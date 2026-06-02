<!--
Generated for NSubstitute v5.3.0.
Do not edit by hand — rerun the update script (scripts/update_skill.py) to refresh.
-->

# NSubstitute v5.3.0 — Examples

Short, focused test snippets showing the canonical NSubstitute usage patterns on v5.3.0. Each block is a test method body; pick your favourite test framework (xUnit `[Fact]`, NUnit `[Test]`, or MSTest `[TestMethod]`).

Assume these test types throughout:

```csharp
public interface ICalculator
{
    int Add(int a, int b);
    int Next();
}

public interface IOrderRepository
{
    void Save(Order order);
    void Cancel(int orderId);
    Task<Order?> GetAsync(int id);
    Task SaveAsync(Order order);
}

public record Order(int Id, decimal Total);
```

## 1. Creating a substitute

`Substitute.For<T>()` creates a proxy. For multiple interfaces (or one class plus interfaces) use the multi-arg overload; pass constructor arguments via `params object[]` when substituting a class.

```csharp
[Fact]
public void Create_substitutes()
{
    // Single interface
    var calc = Substitute.For<ICalculator>();

    // Multi-interface
    var multi = Substitute.For<ICalculator, IDisposable>();

    // Class with ctor args (only virtual/abstract members are interceptable)
    var stream = Substitute.For<System.IO.MemoryStream>(capacity: 1024);

    Assert.NotNull(calc);
    Assert.NotNull(multi);
    Assert.NotNull(stream);
}
```

Notes:
- For class substitutes, only `virtual` / `abstract` members are recorded or stubbable — non-virtual members run their real implementation.
- Multi-target substitute can be cast to either interface: `((IDisposable)multi).Dispose();`.

## 2. Stubbing return values

Calls on a substitute are the configuration — no `.Setup(...)` wrapper. `Returns` supports both literals and a `CallInfo`-driven function.

```csharp
[Fact]
public void Stub_return_values()
{
    var calc = Substitute.For<ICalculator>();

    // Literal
    calc.Add(1, 2).Returns(3);

    // Computed from the actual arguments via CallInfo
    calc.Add(Arg.Any<int>(), Arg.Any<int>())
        .Returns(call => call.Arg<int>(0) + call.Arg<int>(1));

    Assert.Equal(3, calc.Add(1, 2));
    Assert.Equal(11, calc.Add(4, 7));
}
```

Notes:
- If you use a matcher (`Arg.Any<T>()`, `Arg.Is<T>(...)`) for any parameter in an invocation, **every** parameter must be a matcher — mixing literals and matchers throws at runtime.
- `CallInfo.Arg<T>(int)` returns the argument at that index cast to `T`.

## 3. Multiple sequential returns

Pass extra values to return on subsequent calls (calls beyond the list keep returning the last value).

```csharp
[Fact]
public void Stub_sequential_returns()
{
    var calc = Substitute.For<ICalculator>();
    calc.Next().Returns(1, 2, 3);

    Assert.Equal(1, calc.Next());
    Assert.Equal(2, calc.Next());
    Assert.Equal(3, calc.Next());
    Assert.Equal(3, calc.Next()); // sticks at last
}
```

Notes:
- The same pattern works for function-based returns: `Returns(_ => 1, _ => 2, _ => 3)`.

## 4. Throwing from a stub

Two idioms — the callback-style `Returns(_ => throw ...)`, and the dedicated `Throws` / `ThrowsAsync` extensions in `NSubstitute.ExceptionExtensions`.

```csharp
using NSubstitute.ExceptionExtensions;

[Fact]
public void Stub_throws()
{
    var calc = Substitute.For<ICalculator>();
    var repo = Substitute.For<IOrderRepository>();

    // Callback style
    calc.Add(0, 0).Returns(_ => throw new InvalidOperationException("nope"));

    // Throws<TException>
    calc.Next().Throws<InvalidOperationException>();

    // Throws with a specific exception instance
    repo.When(r => r.Cancel(99)).Do(_ => throw new ArgumentException("bad id"));

    // ThrowsAsync for Task-returning members
    repo.GetAsync(42).ThrowsAsync(new TimeoutException());

    Assert.Throws<InvalidOperationException>(() => calc.Add(0, 0));
    Assert.Throws<InvalidOperationException>(() => calc.Next());
    Assert.Throws<ArgumentException>(() => repo.Cancel(99));
    Assert.ThrowsAsync<TimeoutException>(() => repo.GetAsync(42));
}
```

Notes:
- `Throws<T>(value)` (on `ExceptionExtensions`) configures the *previous* call to throw. New in v5.3: for `When(...).Do` you can also call `.Throw(...)` / `.Throws(...)` on the `WhenCalled<T>` builder (see §10).

## 5. Argument matchers

Use matchers to broaden a stub or assertion. `Arg.Do<T>` captures whatever was passed for later inspection.

```csharp
[Fact]
public void Argument_matchers()
{
    var calc = Substitute.For<ICalculator>();
    var repo = Substitute.For<IOrderRepository>();

    calc.Add(Arg.Any<int>(), Arg.Any<int>()).Returns(42);
    calc.Add(Arg.Is<int>(x => x > 100), Arg.Is(5)).Returns(999);

    Assert.Equal(42, calc.Add(1, 2));
    Assert.Equal(999, calc.Add(150, 5));

    // Capture an argument as it's passed
    Order? captured = null;
    repo.When(r => r.Save(Arg.Do<Order>(o => captured = o))).Do(_ => { });

    repo.Save(new Order(7, 12.50m));
    Assert.Equal(7, captured!.Id);
}
```

Notes:
- `Arg.Is<T>(literal)` is the matcher form of an equality check — use it when other args in the same call already use matchers.
- Predicates that throw count as non-matching, not as test failures.

## 6. Asserting received calls

`Received()`, `Received(n)`, `DidNotReceive()`, and `ReceivedWithAnyArgs()` are all extension methods on the substitute. They read the recorded call log.

```csharp
[Fact]
public void Assert_received_calls()
{
    var repo = Substitute.For<IOrderRepository>();
    var order = new Order(1, 9.99m);

    repo.Save(order);
    repo.Save(new Order(2, 1m));

    repo.Received().Save(order);                       // at least once with this arg
    repo.Received(2).Save(Arg.Any<Order>());           // exact count
    repo.DidNotReceive().Cancel(99);                   // never
    repo.ReceivedWithAnyArgs().Save(default!);         // method-only, args ignored
}
```

Notes:
- `Received()` reads accumulated state — create a fresh substitute per test (or `ClearReceivedCalls()` / `ClearSubstitute(ClearOptions.ReceivedCalls)`).
- For a precise non-default count: `repo.Received(Quantity.Within(2, 5)).Save(Arg.Any<Order>())` (in `NSubstitute.ReceivedExtensions`).

## 7. Async stubbing and assertion

`Returns(value)` on a `Task<T>`-returning member wraps the value in `Task.FromResult` automatically. Same for `ValueTask<T>`.

```csharp
[Fact]
public async Task Async_stubs_and_assertions()
{
    var repo = Substitute.For<IOrderRepository>();
    var order = new Order(42, 100m);

    repo.GetAsync(42).Returns(order);

    var result = await repo.GetAsync(42);
    Assert.Equal(42, result!.Id);

    await repo.SaveAsync(order);
    await repo.Received().SaveAsync(order);
}
```

Notes:
- Async `Throws`: use `ThrowsAsync<T>()` or `ThrowsAsync(ex)` from `NSubstitute.ExceptionExtensions`.
- The substitute treats `null` and the default value of `T` as "not configured" for argument-matching purposes — see §5 about `Arg.Do`.

## 8. Partial substitutes

`Substitute.ForPartsOf<T>()` calls real methods by default, but lets you override individual virtual members. Pair with `When..DoNotCallBase` to suppress real behaviour for a specific call.

```csharp
public class Greeter
{
    public virtual string Hello(string name) => $"Hello, {name}!";
    public virtual int Compute() => 100;
}

[Fact]
public void Partial_substitute()
{
    var greeter = Substitute.ForPartsOf<Greeter>();

    // Real behaviour by default
    Assert.Equal("Hello, Sam!", greeter.Hello("Sam"));

    // Override one virtual method without running the base
    greeter.Configure().Compute().Returns(7);
    Assert.Equal(7, greeter.Compute());

    // Or: prevent the base from running for any-args of Hello
    greeter.WhenForAnyArgs(g => g.Hello(default!)).DoNotCallBase();
    greeter.Hello("anything"); // base not invoked
}
```

Notes:
- `Configure()` is the explicit "I'm configuring, not calling" hint — useful here because just calling `greeter.Compute()` would actually invoke the real method first.
- Only `virtual`/`abstract` members can be intercepted on class substitutes.

## 9. Raising events

`Raise.Event` raises a delegate-shaped event; `Raise.EventWith` is the shortcut for `EventHandler<TEventArgs>`.

```csharp
public interface IButton
{
    event EventHandler? Clicked;
    event EventHandler<KeyEventArgs>? KeyPressed;
}

public class KeyEventArgs(char key) : EventArgs { public char Key { get; } = key; }

[Fact]
public void Raise_events()
{
    var button = Substitute.For<IButton>();
    var clicks = 0;
    char? lastKey = null;

    button.Clicked += (_, _) => clicks++;
    button.KeyPressed += (_, e) => lastKey = e.Key;

    button.Clicked += Raise.Event<EventHandler>(button, EventArgs.Empty);
    button.KeyPressed += Raise.EventWith(new KeyEventArgs('Q'));

    Assert.Equal(1, clicks);
    Assert.Equal('Q', lastKey);
}
```

Notes:
- `Raise.Event<THandler>(args...)` reflects over `THandler` and supplies defaults for missing args. Provide them explicitly when in doubt.

## 10. New in v5.3: `When(...).Throws(...)` and `Substitute.ForTypeForwardingTo<TInterface, TClass>`

v5.3 adds a dedicated `Throws` / `Throws<T>` on the `WhenCalled<T>` builder (avoiding the awkward `Do(_ => throw ...)` for void-returning methods, see #803), and `Substitute.ForTypeForwardingTo` for spying on a concrete class through one of its interfaces — even when the class is `sealed` or its members are non-virtual (#700).

```csharp
using NSubstitute.ExceptionExtensions;

public sealed class RealOrderRepository : IOrderRepository
{
    public void Save(Order order) { /* real impl */ }
    public void Cancel(int orderId) { /* real impl */ }
    public Task<Order?> GetAsync(int id) => Task.FromResult<Order?>(new Order(id, 0m));
    public Task SaveAsync(Order order) => Task.CompletedTask;
}

[Fact]
public void When_Throws_and_ForTypeForwardingTo()
{
    // New WhenCalled<T>.Throws — much cleaner than When(...).Do(_ => throw ...)
    var repo = Substitute.For<IOrderRepository>();
    repo.When(r => r.Cancel(13)).Throw(new InvalidOperationException("unlucky"));

    Assert.Throws<InvalidOperationException>(() => repo.Cancel(13));

    // Substitute.ForTypeForwardingTo: spy on a sealed class through its interface.
    // Calls hit the real implementation by default, but are recorded and can be overridden.
    var spy = Substitute.ForTypeForwardingTo<IOrderRepository, RealOrderRepository>();

    spy.Save(new Order(1, 5m));                  // forwarded to real RealOrderRepository.Save
    spy.Received().Save(Arg.Any<Order>());       // …and recorded for assertion

    spy.Configure().GetAsync(99).Returns(Task.FromResult<Order?>(null)); // selectively stub one method
    Assert.Null(spy.GetAsync(99).Result);
}
```

Notes:
- `ForTypeForwardingTo` works with sealed types and non-virtual members. Caveat from the docs: because the substituted method is non-virtual, *internal* calls within the real class still invoke the real implementation directly and won't appear in the received-calls log.
- `When(x => ...).Throws(ex)` / `Throws<TException>()` is the recommended way to throw from a `When..Do` chain — the previous `Do(_ => throw ex)` works but produced confusing `CouldNotSetReturnDueToNoLastCallException` errors in some scenarios.
