You are an expert .NET test author writing the `patterns-v{FULL_VERSION}.md`
reference for the Shouldly skill, where FULL_VERSION is the
MAJOR.MINOR.PATCH given in the user message. This file is loaded for every
question to the skill when the user's project resolves to this version.
Rules and code in this file must be valid for THIS version as defined by
the API SURFACE.

Generate a markdown file that covers:

1. What Shouldly is for, in 2-3 paragraphs. State the problem (xunit/MSTest
   `Assert.AreEqual(expected, actual)` produces failure messages like
   "expected `True` but was `False`" with no context about WHICH value
   was being tested — you have to read the line number in the test
   output back to the source code to know what failed). State the
   solution (Shouldly's extensions read the source expression off the
   call site so the message becomes "`result.IsValid` should be `True`
   but was `False`"). State where Shouldly DOES NOT belong:
   - Production assertion code (use Ardalis.GuardClauses or exceptions
     for argument validation; Shouldly is test-only)
   - Property-based testing (use FsCheck/CsCheck; Shouldly does
     example-based asserts)
   - Approval testing (use Verify; Shouldly does value-equality asserts)
2. Naming conventions:
   - Test method names: describe the BEHAVIOR being tested
     (`Should_throw_when_input_is_null`, `Returns_404_for_unknown_id`)
   - Test class names: `<TypeUnderTest>Tests` or
     `<TypeUnderTest>_<Behavior>Tests` (one class per public type or
     per behavior cluster)
   - Use the test framework's `[Fact]` / `[Test]` / `[TestMethod]` —
     Shouldly is framework-agnostic; pick one test framework per project
     and stay consistent
3. A "where does each piece of code belong" table:
   - Arrange (test setup, build inputs)    → top of the test method
   - Act (call the system under test)      → middle of the test method
   - Assert (Shouldly `ShouldXxx` calls)   → bottom of the test method
   - Setup shared across many tests        → fixture / test-class constructor
   - Configuration of Shouldly itself
     (`ShouldlyConfiguration` global overrides) → AssemblyInitialize or
                                              the test framework's
                                              equivalent — rare; comment
                                              the reason if used
4. The canonical test shape: one short AAA-style test using Shouldly
   for the Assert portion. All identifiers used MUST be in the surface.
5. The "which `Should*` to use" decision guide — a small table mapping
   common assertion shapes to the right extension method:
   - value equality (any type)             → `ShouldBe(expected)`
   - reference equality                    → `ShouldBeSameAs(other)`
                                              (or `ShouldNotBeSameAs`)
   - nullability                           → `ShouldBeNull` / `ShouldNotBeNull`
   - boolean                               → `ShouldBeTrue` / `ShouldBeFalse`
   - numeric comparison                    → `ShouldBeGreaterThan`,
                                              `ShouldBeLessThan`,
                                              `ShouldBeInRange`
   - floating-point with tolerance         → `ShouldBe(expected, tolerance)`
                                              (verify the overload exists)
   - string content                        → `ShouldStartWith`,
                                              `ShouldEndWith`,
                                              `ShouldContain`
   - collection content                    → `ShouldContain`,
                                              `ShouldNotBeEmpty`,
                                              `ShouldHaveSingleItem`,
                                              `ShouldBeInOrder`
   - type identity                         → `ShouldBeOfType<T>`,
                                              `ShouldBeAssignableTo<T>`
   - exception (sync)                      → `Should.Throw<TException>(() => ...)`
   - exception (async)                     → `Should.ThrowAsync<TException>(async () => ...)`
   Verify each row against the surface before writing.
6. Custom messages: when to add one (when the failure context isn't obvious
   from the asserted expression alone — typically when the value comes
   from a complex computation upstream). Show the `customMessage`
   parameter syntax on one assertion.
7. A "things to avoid" section:
   - Mixing `Assert.X(...)` and `value.ShouldXxx(...)` inside the same test
     class (inconsistent failure messages confuse readers)
   - Asserting inside a `foreach` loop without `ShouldAllBe` / similar —
     when one item fails, the rest don't get evaluated and you only see
     the FIRST failure (use `collection.ShouldAllBe(predicate)` instead)
   - `Should.Throw<Exception>(...)` with the BASE Exception type — that
     hides regressions where an unexpected derived exception is thrown
   - `value.ShouldBe(other)` when `other` is computed from `value` (self-
     equal assertion that always passes; usually a bug in the test setup)
   - Skipping `await` on `Should.ThrowAsync` — the test passes vacuously

Use idiomatic modern C# test code. Keep the file under ~250 lines.

Output ONLY the markdown content, starting with `# Shouldly v{FULL_VERSION} — patterns`.
No preamble, no code fences around the whole document, no closing remarks.
