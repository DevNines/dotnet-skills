# Shouldly v4.3.0 — patterns

## What Shouldly is for

Shouldly is a test-only assertion library. The problem it solves is feedback
quality at failure time. With xUnit, NUnit, or MSTest, an assertion like
`Assert.AreEqual(true, result.IsValid)` fails with a message such as
"Expected: True. Actual: False." That tells you what the values were, but
not which expression produced them — you have to read the line number back
to source to figure out what was being checked. Worse, when several similar
asserts live in one test, the failure messages are indistinguishable.

Shouldly fixes this by reading the source expression off the call site. When
`result.IsValid.ShouldBeTrue()` fails, the message is
`result.IsValid should be True but was False`. The assertion verb is the
method name, the subject is the expression you wrote, and the failure
text reads like the test. No re-reading line numbers, no decoding which
of three booleans tripped.

Shouldly does NOT belong in:

- **Production assertion code.** Use `Ardalis.GuardClauses` or plain
  `ArgumentNullException`/`ArgumentException` for argument validation.
  Shouldly throws `ShouldAssertException`, which is a test concept.
- **Property-based testing.** Use FsCheck or CsCheck to generate inputs.
  Shouldly does example-based asserts only.
- **Approval testing of large documents.** Use Verify for snapshot/approval
  flows. Shouldly does have a small `ShouldMatchApproved` for short strings,
  but Verify is the better tool for serialized objects, files, and diffs.

## Naming conventions

- **Test method names** describe behavior in plain English:
  `Should_throw_when_input_is_null`, `Returns_404_for_unknown_id`,
  `Computes_total_including_tax`.
- **Test class names** are `<TypeUnderTest>Tests` or
  `<TypeUnderTest>_<Behavior>Tests`. One class per public type or per
  behavior cluster keeps fixtures scoped.
- Shouldly is **framework-agnostic** — it works with xUnit `[Fact]`,
  NUnit `[Test]`, or MSTest `[TestMethod]`. Pick one test framework per
  project and stay consistent.

## Where each piece of code belongs

| Code                                                      | Where it goes                                               |
| --------------------------------------------------------- | ----------------------------------------------------------- |
| Arrange — build inputs, construct SUT                     | Top of the test method                                      |
| Act — call the method under test                          | Middle of the test method (often one line)                  |
| Assert — `ShouldXxx` calls                                | Bottom of the test method                                   |
| Setup shared across many tests                            | Test-class constructor or framework fixture                 |
| `ShouldlyConfiguration` overrides (e.g. `DefaultFloatingPointTolerance`, `DefaultTaskTimeout`, `DisableSourceInErrors`) | Assembly init / module initializer — rare; comment the reason |

## Canonical test shape

```csharp
using Shouldly;
using Xunit;

public sealed class InvoiceCalculatorTests
{
    [Fact]
    public void Computes_total_including_tax()
    {
        // Arrange
        var calculator = new InvoiceCalculator(taxRate: 0.10m);
        var lineItems = new[] { 100m, 50m };

        // Act
        var total = calculator.Total(lineItems);

        // Assert
        total.ShouldBe(165m);
    }
}
```

When the failure says `total should be 165 but was 150`, you do not need
to look at the source to know which value broke.

## Which `Should*` to use

| Assertion shape                          | Method                                                                |
| ---------------------------------------- | --------------------------------------------------------------------- |
| Value equality (any type)                | `ShouldBe(expected)`                                                  |
| Inequality                               | `ShouldNotBe(other)`                                                  |
| Reference equality                       | `ShouldBeSameAs(other)` / `ShouldNotBeSameAs(other)`                  |
| Nullability                              | `ShouldBeNull()` / `ShouldNotBeNull()`                                |
| Boolean                                  | `ShouldBeTrue()` / `ShouldBeFalse()`                                  |
| Numeric comparison                       | `ShouldBeGreaterThan`, `ShouldBeLessThan`, `ShouldBeGreaterThanOrEqualTo`, `ShouldBeLessThanOrEqualTo`, `ShouldBeInRange` |
| Floating-point with tolerance            | `ShouldBe(expected, tolerance)` (overloads for `double`, `float`, `decimal`) |
| Positive / negative                      | `ShouldBePositive()` / `ShouldBeNegative()`                           |
| One-of set                               | `ShouldBeOneOf(values)` / `ShouldNotBeOneOf(values)`                  |
| String content                           | `ShouldStartWith`, `ShouldEndWith`, `ShouldContain`, `ShouldMatch` (regex) |
| String content, case-insensitive         | `ShouldContain(value, Case.Sensitive)` — pass `Case` enum; or `ShouldBe(other, StringCompareShould.IgnoreCase)` |
| String null/empty/whitespace             | `ShouldBeNullOrEmpty`, `ShouldBeNullOrWhiteSpace`, `ShouldNotBeNullOrEmpty`, `ShouldNotBeNullOrWhiteSpace` |
| Collection contains                      | `ShouldContain(item)` / `ShouldContain(predicate)` / `ShouldNotContain` |
| Collection emptiness                     | `ShouldBeEmpty()` / `ShouldNotBeEmpty()`                              |
| Collection single item                   | `ShouldHaveSingleItem()`                                              |
| Collection order                         | `ShouldBeInOrder()` / `ShouldBeInOrder(SortDirection.Ascending)`      |
| Collection uniqueness                    | `ShouldBeUnique()`                                                    |
| Collection subset                        | `ShouldBeSubsetOf(other)`                                             |
| Collection every-item predicate          | `ShouldAllBe(x => predicate(x))`                                      |
| Collection equality (any order)          | `ShouldBe(other, ignoreOrder: true)`                                  |
| Dictionary keys/values                   | `ShouldContainKey`, `ShouldContainKeyAndValue`, `ShouldNotContainKey` |
| Type identity                            | `ShouldBeOfType<T>()` / `ShouldBeAssignableTo<T>()`                   |
| Attribute presence                       | `typeof(Foo).ShouldBeDecoratedWith<MyAttr>()`                         |
| Enum flags                               | `ShouldHaveFlag(flag)` / `ShouldNotHaveFlag(flag)`                    |
| Exception (sync)                         | `Should.Throw<TException>(() => sut.Do())`                            |
| Exception (async)                        | `await Should.ThrowAsync<TException>(async () => await sut.DoAsync())` |
| Object graph equivalence                 | `actual.ShouldBeEquivalentTo(expected)`                               |
| Multiple asserts grouped                 | `sut.ShouldSatisfyAllConditions(s => s.A.ShouldBe(1), s => s.B.ShouldBe(2))` |
| Completes within budget                  | `Should.CompleteIn(() => work(), TimeSpan.FromSeconds(2))`            |

## Custom messages

Add the optional final `customMessage` argument when the asserted expression
alone won't tell you what failed — typically when the value is derived
deep in a computation or when the same shape is asserted in a loop with
distinguishing context.

```csharp
foreach (var user in users)
{
    user.IsActive.ShouldBeTrue($"user {user.Id} should be active after migration");
}
```

For a simple `result.Count.ShouldBe(3)` you don't need one — the expression
is already self-describing.

## Things to avoid

- **Don't mix `Assert.X(...)` and `value.ShouldXxx(...)` in the same test
  class.** Readers can't predict the failure-message shape; pick one
  style per project.
- **Don't assert inside a bare `foreach` over a collection.** When item
  three fails, items four and five never run, and you only see the first
  failure. Use `collection.ShouldAllBe(x => predicate(x))` so Shouldly
  evaluates every element and reports the offending value.
- **Don't write `Should.Throw<Exception>(...)`** with the base `Exception`
  type. That hides regressions where the SUT starts throwing a different
  exception class. Assert the most specific type you expect.
- **Don't write `value.ShouldBe(other)` when `other` is computed from
  `value`.** Self-equal assertions always pass — usually a copy-paste bug
  in the Arrange section.
- **Don't forget `await` on `ShouldThrowAsync` / `Should.ThrowAsync`.**
  Without `await`, the returned `Task` is discarded and the test passes
  vacuously even when the SUT throws nothing.
- **Don't catch-and-assert exceptions manually.** `try { ... } catch (FooException) { }`
  passes when no exception is thrown. Use `Should.Throw<FooException>(() => ...)`.
