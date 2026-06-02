# NSubstitute v5.3.0 — patterns

## What NSubstitute is for

NSubstitute is a test double library for .NET. The problem it solves: traditional
mocking libraries like Moq force you to wrap every setup and verification in a
lambda — `mock.Setup(x => x.Bar(It.IsAny<int>())).Returns(42)` or
`mock.Verify(x => x.Bar(42), Times.Once)`. The lambda-quoting trick is necessary
for those libraries to inspect the expression tree, but it obscures the
distinction between "this is what I'm asserting" and "this is what I'm calling",
and it makes the test read nothing like the production code it stands in for.

NSubstitute's answer is to make invocations on a substitute the configuration
itself. `sub.Bar(42).Returns("ok")` is a real method call on `sub` whose return
value is then redirected via the `Returns` extension method. There's no
expression tree, no lambda, no `Setup`/`Verify` ceremony. The test reads like
the code under test.

The trade-off: substitutes only intercept `virtual`, `abstract`, and interface
members. Sealed classes and non-virtual methods cannot be substituted (the real
implementation runs and `Received()` will not see the call). NSubstitute does
NOT belong in:

- **Cross-process / integration tests** — use the real implementation, an
  in-memory test double, or a containerized dependency. Substitutes verify
  *interaction*, not end-to-end behaviour.
- **Production code** — NSubstitute is test-only; never reference it from a
  non-test project.
- **Static method mocking** — NSubstitute cannot substitute static methods.
  Refactor to an interface or wrap the static behind an instance type.

## Lifecycle: substitutes are stateful

Every call made on a substitute is **recorded**. That recording is what
makes `sub.Received().Bar(42)` work — but it also means a substitute reused
across tests accumulates calls and configured returns from earlier tests.

The rule:

- **Fresh substitute per test** is the default. Create it in the xUnit test
  class constructor, the NUnit `[SetUp]` method, or directly in the test body.
- If you must share a substitute across tests in a fixture, call
  `sub.ClearReceivedCalls()` between tests, or use
  `sub.ClearSubstitute(ClearOptions.All)` (from `NSubstitute.ClearExtensions`)
  to also wipe configured returns.

## Naming conventions

- **Test method names** describe behaviour:
  `Returns_user_when_id_is_known`, `Forwards_save_to_repository`.
- **Variable names for substitutes** describe the role, not the test-double
  category. Prefer `logger`, `repo`, `clock` over `mockLogger`, `fakeRepo`,
  `stubClock`. The whole point of NSubstitute's syntax is that the test reads
  like real code; Hungarian prefixes work against that.

## Where each piece of code belongs

| Code                                                       | Section                                            |
|------------------------------------------------------------|----------------------------------------------------|
| `Substitute.For<T>()`                                      | Arrange (top of test, or constructor / `[SetUp]`)  |
| `sub.X(arg).Returns(value)`                                | Arrange (top)                                      |
| Invoking the system-under-test                             | Act (middle)                                       |
| `sub.Received().X(arg)` / `sub.DidNotReceive().X(arg)`     | Assert (bottom)                                    |
| Shared substitutes across a fixture                        | Test class constructor (xUnit) / `[SetUp]` (NUnit) — pair with `ClearReceivedCalls()` if state could leak |

## Canonical AAA shape

```csharp
public class GreeterTests
{
    private readonly IClock _clock = Substitute.For<IClock>();

    [Fact]
    public void Uses_clock_to_build_morning_greeting()
    {
        // Arrange
        _clock.Now().Returns(new DateTime(2025, 1, 1, 9, 0, 0));
        var greeter = new Greeter(_clock);

        // Act
        var message = greeter.Greet("Ada");

        // Assert
        Assert.Equal("Good morning, Ada", message);
        _clock.Received(1).Now();
    }
}
```

## The argument-matchers rule

**Once you use any `Arg.X<T>()` matcher in an invocation, every argument in
that invocation must also be a matcher.** Mixing concrete values with matchers
produces ambiguous-arguments errors at runtime.

```csharp
// WRONG — mixes a literal with a matcher
repo.Save(42, Arg.Any<string>()).Returns(true);

// RIGHT — wrap the literal in Arg.Is so both arguments are matchers
repo.Save(Arg.Is(42), Arg.Any<string>()).Returns(true);
```

The same rule applies to `Received()` assertions.

## Which entry point to use

| Goal                                            | Call                                                                |
|-------------------------------------------------|---------------------------------------------------------------------|
| Stub return value                               | `sub.X(args).Returns(value)`                                        |
| Stub computed return                            | `sub.X(args).Returns(call => f(call.Arg<T>()))`                     |
| Stub sequential returns                         | `sub.X(args).Returns(v1, v2, v3)`                                   |
| Throw                                           | `sub.X(args).Throws(new Ex())` or `sub.X(args).Throws<Ex>()` (from `NSubstitute.ExceptionExtensions`) |
| Throw from async                                | `sub.DoAsync(args).ThrowsAsync(new Ex())`                           |
| Assert called                                   | `sub.Received().X(args)`                                            |
| Assert called N times                           | `sub.Received(N).X(args)` or `sub.Received(Quantity.Within(1, 3)).X(args)` |
| Assert NOT called                               | `sub.DidNotReceive().X(args)`                                       |
| Assert called with any args                     | `sub.ReceivedWithAnyArgs().X(default)`                              |
| Assert NOT called with any args                 | `sub.DidNotReceiveWithAnyArgs().X(default)`                         |
| Partial substitute (call real virtuals)         | `Substitute.ForPartsOf<T>()`                                        |
| Multi-interface substitute                      | `Substitute.For<IA, IB>()`                                          |
| Async return                                    | `sub.GetAsync(id).Returns(value)` — NSubstitute wraps in `Task.FromResult` |
| Capture argument for later assertion            | `Arg.Do<T>(x => captured = x)`                                      |
| Side-effect on call (no return change)          | `sub.When(s => s.X(args)).Do(call => { ... })`                      |
| Verify call order across substitutes            | `Received.InOrder(() => { a.X(); b.Y(); })`                         |
| Reset received calls only                       | `sub.ClearReceivedCalls()`                                          |
| Reset received + configured returns + actions   | `sub.ClearSubstitute(ClearOptions.All)`                             |

### Async example

```csharp
var repo = Substitute.For<IUserRepository>();
repo.GetAsync(7).Returns(new User(7, "Ada"));

var user = await repo.GetAsync(7);

await repo.Received(1).GetAsync(7);
```

### Capture-and-assert example

```csharp
var captured = default(Order);
processor.Submit(Arg.Do<Order>(o => captured = o));

service.PlaceOrder(...);

Assert.Equal(99.50m, captured.Total); // explicit equality — better diagnostics
```

## Things to avoid

- **Substituting a concrete class with non-virtual methods.** NSubstitute can
  only intercept `virtual` / `abstract` members. Non-virtual calls invoke the
  real implementation, are not recorded, and `Received()` will not see them.
- **`Substitute.For<ConcreteWithCtorArgs>()` without ctor args.** Pass them via
  the `object[] constructorArguments` parameter:
  `Substitute.For<MyClass>(dep1, dep2)`.
- **Sharing a substitute across tests without `ClearReceivedCalls()`.**
  `Received(1)` then passes for the wrong reason because the call lingered
  from a previous test.
- **`Returns(...)` on a non-virtual method.** Silently does nothing useful —
  the real method runs. Add `NSubstitute.Analyzers.CSharp` to your test
  project to catch this at compile time.
- **`Substitute.For<T>()` on a sealed class.** Castle DynamicProxy can't
  subclass it; the analyzer flags it, or you get a runtime failure.
- **Forgetting to await async assertions.**
  `sub.Received().DoAsync(...)` returns a `Task`; if you don't `await` it,
  the assertion may never run and the test passes vacuously.
  Write `await sub.Received().DoAsync(...);`.
- **`Arg.Is<T>(x => x.Prop == expected)` instead of capture-and-assert.**
  Predicate matchers don't print the actual value on failure; capture with
  `Arg.Do<T>` and use explicit equality assertions for readable diagnostics.
- **`Substitute.ForPartsOf<T>()` followed by stubbing every virtual method.**
  That defeats the purpose of a partial substitute — use plain
  `Substitute.For<T>()` instead.
- **Mixing literals and `Arg.X` matchers in one call.** See the matchers rule
  above — wrap literals in `Arg.Is(...)`.
