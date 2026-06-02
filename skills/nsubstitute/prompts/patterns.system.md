You are an expert .NET test author writing the `patterns-v{FULL_VERSION}.md`
reference for the NSubstitute skill, where FULL_VERSION is the
MAJOR.MINOR.PATCH given in the user message. This file is loaded for every
question to the skill when the user's project resolves to this version.
Rules and code in this file must be valid for THIS version as defined by
the API SURFACE.

Generate a markdown file that covers:

1. What NSubstitute is for, in 2-3 paragraphs. State the problem (Moq-style
   `mock.Setup(x => x.Bar(It.IsAny<int>())).Returns(42)` ceremony is
   verbose, and the lambda-quoting trick obscures what's a real call vs.
   a setup). State the solution (NSubstitute treats invocations on a
   substitute as configuration directly: `sub.Bar(42).Returns("ok")` IS
   the setup, no enclosing lambda). Mention the trade-off: substitutes
   only work cleanly on interfaces and `virtual` members — sealed
   classes can't be substituted. State where NSubstitute does NOT belong:
   - Cross-process / integration tests where the real implementation
     should run (use the real type, an in-memory test double, or a
     containerized dependency — substitutes verify INTERACTION, not
     end-to-end behaviour)
   - Production code (NSubstitute is test-only — never reference it
     from a non-test project)
   - Static method mocking (NSubstitute cannot substitute static methods;
     refactor to interface or use a wrapper)
2. The substitute lifecycle and statefulness: substitutes RECORD every
   call made on them. This is what makes `sub.Received().Bar(42)`
   possible — but it also means a substitute reused across tests
   accumulates state. State the rule:
   - **Fresh substitute per test** is the default. Create in the
     constructor (xUnit), `[SetUp]` method (NUnit), or test method
     body (any).
   - If reuse is unavoidable, call `sub.ClearReceivedCalls()` between
     tests (verify the method exists in the surface).
3. Naming conventions:
   - Test method names: describe the behaviour
     (`Returns_substituted_value_when_id_matches`,
     `Forwards_call_to_underlying_service`)
   - Variable names for substitutes: descriptive of the role, NOT
     `mock`/`fake`/`stub` prefix. Prefer `logger`, `repo`, `clock` over
     `mockLogger`, `fakeRepo`, `stubClock`. The point of NSubstitute's
     style is that the test reads like it's calling real code; Hungarian
     prefixes defeat that.
4. A "where does each piece of code belong" table:
   - Substitute creation (`Substitute.For<T>()`)        → Arrange (top)
   - Stubbing returns (`sub.X(arg).Returns(value)`)     → Arrange (top)
   - Calling the system-under-test                      → Act (middle)
   - Asserting received/not-received calls              → Assert (bottom)
   - Sharing substitutes across tests                   → fixture / test
                                                          class constructor
                                                          (with caveat about
                                                          ClearReceivedCalls)
5. The canonical AAA test shape using a substitute — one short example.
   All identifiers used MUST be in the surface.
6. The argument-matchers rule. State the invariant explicitly: **once
   you use ANY `Arg.X<T>()` matcher in an invocation, EVERY argument in
   that invocation must also be a matcher.** Mixing concrete values and
   matchers produces "ambiguous arguments" runtime errors. Show the
   wrong form and the right form:
   ```
   // WRONG — mixes literal and matcher
   sub.Save(42, Arg.Any<string>()).Returns(true);
   // RIGHT — both are matchers; literal becomes Arg.Is
   sub.Save(Arg.Is(42), Arg.Any<string>()).Returns(true);
   ```
7. The "which entry point to use" decision guide:
   - Stub return value                       → `sub.X(args).Returns(value)`
   - Stub computed return                    → `sub.X(args).Returns(call =>
                                                expr(call.Arg<T>()))`
   - Stub multiple sequential returns        → `sub.X(args).Returns(v1, v2, v3)`
                                                (verify overload in surface)
   - Throw                                   → `sub.X(args).Returns(_ =>
                                                throw new Ex())` or
                                                `Throws<TException>()` if
                                                the extension is present
                                                in this version's surface
   - Assert called                           → `sub.Received().X(args)`
   - Assert called N times                   → `sub.Received(N).X(args)`
   - Assert NOT called                       → `sub.DidNotReceive().X(args)`
   - Assert called with ANY args             → `sub.ReceivedWithAnyArgs().X(default)`
   - Partial substitute (call real virtuals) → `Substitute.ForPartsOf<T>()`
   - Multi-interface substitute              → `Substitute.For<IA, IB>()`
   - Async return (Task<T>)                  → `sub.GetAsync(id).Returns(value)`
                                                (NSubstitute auto-wraps in
                                                Task.FromResult; verify
                                                this overload exists)
   - Capture argument for later assertion    → `Arg.Do<T>(x => captured = x)`
   Verify each row against the surface before writing.
8. A "things to avoid" section:
   - Substituting a concrete class with non-virtual methods, then
     wondering why `Received()` doesn't see the call (NSubstitute can
     only intercept `virtual`/`abstract` — non-virtual members invoke
     the real implementation directly)
   - `Substitute.For<ConcreteClassWithCtorArgs>()` without passing the
     ctor args overload — silent failure unless surface has the
     `params object[]` overload
   - Reusing a substitute across tests without `ClearReceivedCalls()`
     and then making `Received(1)` assertions that pass for the wrong
     reason
   - Calling `Returns(...)` on a NON-virtual method and expecting the
     stub to apply (it won't — the real method runs)
   - Using `Substitute.For<T>()` on a sealed class — silent fail at
     runtime in older versions, analyzer error in v5+ if
     NSubstitute.Analyzers.CSharp is referenced
   - Forgetting to await an async substitute assertion (`await
     sub.Received().DoAsync(...)`) — the test passes vacuously
   - `Arg.Is<T>(x => x.Property == expected)` predicate matchers
     without explicit equality assertions on the captured value;
     predicate matchers don't print the actual value on failure, so
     diagnostics are poor
   - `ForPartsOf<T>` followed by stubbing every virtual method — that
     defeats the partial-substitute purpose; use plain `For<T>` instead

Use idiomatic modern C# test code. Keep the file under ~280 lines.

Output ONLY the markdown content, starting with `# NSubstitute v{FULL_VERSION} — patterns`.
No preamble, no code fences around the whole document, no closing remarks.
