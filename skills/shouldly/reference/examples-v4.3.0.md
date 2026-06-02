# Shouldly

<!--
  examples-v4.3.0.md
  Generated against Shouldly v4.3.0.
  Do not edit by hand — rerun the update script to regenerate.
-->

Short, focused examples for Shouldly v4.3.0. Each example is a test method body; the assertion is the point.

## 1. Value equality

`ShouldBe` reads the source expression at the call site, so the failure message names the actual variable rather than just printing its value.

```csharp
namespace MyApp.Tests;

public sealed class ValueEqualityExamples
{
    [Fact]
    public void Primitives_and_strings()
    {
        var sum = 2 + 3;
        sum.ShouldBe(5);

        var greeting = "hello";
        greeting.ShouldBe("hello");
    }

    [Fact]
    public void Negation()
    {
        var status = "pending";
        status.ShouldNotBe("approved");
    }
}
```

Notes:
- `ShouldBe<T>` uses `EqualityComparer<T>.Default`; pass an `IEqualityComparer<T>` overload for custom equality.

## 2. Reference equality and nullability

```csharp
public sealed class ReferenceExamples
{
    [Fact]
    public void Null_checks()
    {
        string? maybe = null;
        maybe.ShouldBeNull();

        var name = "Bart";
        name.ShouldNotBeNull();
    }

    [Fact]
    public void Reference_identity()
    {
        var list = new List<int> { 1, 2 };
        var alias = list;
        var copy = new List<int> { 1, 2 };

        alias.ShouldBeSameAs(list);
        copy.ShouldNotBeSameAs(list);
    }
}
```

Notes:
- `ShouldNotBeNull` is annotated with `[NotNull]`, so the compiler treats the value as non-null afterwards — you can dot into it without a null-forgiving operator.

## 3. Numerical comparisons (with tolerance)

```csharp
public sealed class NumericExamples
{
    [Fact]
    public void Ordering()
    {
        var age = 42;
        age.ShouldBeGreaterThan(18);
        age.ShouldBeLessThanOrEqualTo(120);
        age.ShouldBeInRange(0, 150);
    }

    [Fact]
    public void Floating_point_needs_tolerance()
    {
        var computed = 0.1 + 0.2;
        computed.ShouldBe(0.3, tolerance: 1e-9);
    }

    [Fact]
    public void Sign()
    {
        var delta = -3;
        delta.ShouldBeNegative();
        (delta * delta).ShouldBePositive();
    }
}
```

Notes:
- Never call `ShouldBe(double)` without `tolerance` on floating point — IEEE-754 rounding will bite you. v4.3.0 specifically fixed handling of `tolerance: 0`.

## 4. Collections

```csharp
public sealed class CollectionExamples
{
    [Fact]
    public void Containment_and_shape()
    {
        var names = new[] { "Homer", "Marge", "Bart" };

        names.ShouldContain("Bart");
        names.ShouldNotContain("Milhouse");
        names.ShouldNotBeEmpty();
        names.ShouldContain(n => n.StartsWith('M'), expectedCount: 1);
    }

    [Fact]
    public void Single_item_and_ordering()
    {
        var only = new[] { 99 };
        only.ShouldHaveSingleItem();

        var sorted = new[] { 1, 2, 3, 4 };
        sorted.ShouldBeInOrder();
        sorted.ShouldBeInOrder(SortDirection.Ascending);
    }

    [Fact]
    public void Predicate_for_every_element()
    {
        var ages = new[] { 21, 33, 47 };
        ages.ShouldAllBe(a => a >= 18);
    }

    [Fact]
    public void Subset_and_uniqueness()
    {
        var picked = new[] { 2, 4 };
        var allowed = new[] { 1, 2, 3, 4, 5 };
        picked.ShouldBeSubsetOf(allowed);

        new[] { "a", "b", "c" }.ShouldBeUnique();
    }
}
```

Notes:
- `ShouldContain` with a predicate also has an `expectedCount` overload — handy when "exists" isn't strong enough.
- For element-wise floating-point comparison use `IEnumerable<double>.ShouldBe(other, tolerance)`.

## 5. Strings

```csharp
public sealed class StringExamples
{
    [Fact]
    public void Substrings_and_anchors()
    {
        var msg = "Connection refused at 127.0.0.1";

        msg.ShouldStartWith("Connection");
        msg.ShouldEndWith("127.0.0.1");
        msg.ShouldContain("refused");
    }

    [Fact]
    public void Case_insensitive_comparison()
    {
        var header = "Content-Type";
        header.ShouldBe("content-type", StringCompareShould.IgnoreCase);
        header.ShouldContain("TYPE", Case.Insensitive);
    }

    [Fact]
    public void Regex_and_whitespace()
    {
        "Cheese".ShouldMatch("C.e{2}s[e]");
        "   ".ShouldBeNullOrWhiteSpace();
    }
}
```

Notes:
- The string `ShouldContain`, `ShouldStartWith`, `ShouldEndWith` overloads take a `Case` enum (e.g. `Case.Insensitive`); for `ShouldBe` the case-control parameter is `StringCompareShould.IgnoreCase`.

## 6. Type assertions

```csharp
public sealed class TypeExamples
{
    [Fact]
    public void Exact_type()
    {
        object payload = new InvalidOperationException("boom");
        var typed = payload.ShouldBeOfType<InvalidOperationException>();
        typed.Message.ShouldBe("boom");
    }

    [Fact]
    public void Assignable_to_base_or_interface()
    {
        object stream = new MemoryStream();
        stream.ShouldBeAssignableTo<IDisposable>();
    }
}
```

Notes:
- `ShouldBeOfType<T>` returns the cast value, so you can chain follow-up assertions on the typed instance.
- v4.3.0 added support for `Nullable<T>` in `ShouldBeAssignableTo` — `((object?)42).ShouldBeAssignableTo<int?>()` works.

## 7. Exception assertions

```csharp
public sealed class ExceptionExamples
{
    private static int Divide(int a, int b) =>
        b == 0 ? throw new DivideByZeroException("nope") : a / b;

    [Fact]
    public void Sync_throw()
    {
        var ex = Should.Throw<DivideByZeroException>(() => Divide(1, 0));
        ex.Message.ShouldBe("nope");
    }

    [Fact]
    public void Sync_does_not_throw()
    {
        Should.NotThrow(() => Divide(10, 2));
    }

    [Fact]
    public async Task Async_throw()
    {
        var ex = await Should.ThrowAsync<InvalidOperationException>(async () =>
        {
            await Task.Yield();
            throw new InvalidOperationException("async boom");
        });
        ex.Message.ShouldBe("async boom");
    }

    [Fact]
    public async Task Async_does_not_throw()
    {
        await Should.NotThrowAsync(async () => await Task.Delay(1));
    }
}
```

Notes:
- `Should.Throw<T>(...)` is the canonical entry point; it returns the thrown exception so you can assert on its properties.
- For tasks, prefer `Should.ThrowAsync<T>` / `Should.NotThrowAsync` and `await` the result — don't fire-and-forget.

## 8. Custom messages

The trailing `customMessage` is shown after the standard failure block, so use it to explain *why* the assertion matters in this test.

```csharp
public sealed class CustomMessageExamples
{
    [Fact]
    public void Adds_context_on_failure()
    {
        var balance = 100m;
        balance.ShouldBeGreaterThan(0m, "account must never go negative after a deposit");

        var roles = new[] { "user" };
        roles.ShouldContain("admin", "admin role is required to invoke this endpoint");

        var token = "abc.def.ghi";
        token.ShouldMatch(@"^[\w-]+\.[\w-]+\.[\w-]+$", "must be a well-formed JWT");
    }
}
```

Notes:
- The custom message is only rendered on failure — passing tests stay quiet.

## 9. Composing multiple assertions

`ShouldSatisfyAllConditions` runs every assertion and reports *all* failures at once instead of stopping at the first.

```csharp
public sealed class CompositeExamples
{
    private sealed record Order(int Id, decimal Total, string Status);

    [Fact]
    public void All_invariants_at_once()
    {
        var order = new Order(7, 42.50m, "Paid");

        order.ShouldSatisfyAllConditions(
            () => order.Id.ShouldBeGreaterThan(0),
            () => order.Total.ShouldBePositive(),
            () => order.Status.ShouldBe("Paid"));
    }
}
```

Notes:
- The typed overload `ShouldSatisfyAllConditions<T>(T, params Action<T>[])` lets you write `o => o.Id.ShouldBe(7)` lambdas without re-naming the subject.

## 10. New in v4.3: `IReadOnlyDictionary<K,V>` and `ImmutableArray<T>` support

v4.3.0 extended the dictionary assertions to work directly on `IReadOnlyDictionary<TKey, TValue>` (previously they only accepted `IDictionary<TKey, TValue>`), and added support for `ImmutableArray<T>` in `ShouldBeEquivalentTo`.

```csharp
using System.Collections.Immutable;

public sealed class NewInV43Examples
{
    [Fact]
    public void Read_only_dictionary_assertions()
    {
        IReadOnlyDictionary<string, int> scores = new Dictionary<string, int>
        {
            ["alice"] = 90,
            ["bob"]   = 75,
        };

        scores.ShouldContainKey("alice");
        scores.ShouldContainKeyAndValue("bob", 75);
        scores.ShouldNotContainKey("eve");
        scores.ShouldNotContainValueForKey("alice", 0);
    }

    [Fact]
    public void Immutable_array_equivalence()
    {
        var actual   = ImmutableArray.Create(1, 2, 3);
        var expected = ImmutableArray.Create(1, 2, 3);

        actual.ShouldBeEquivalentTo(expected);
    }
}
```

Notes:
- Before 4.3.0, exposing a dictionary as `IReadOnlyDictionary<K,V>` (the modern recommendation) forced you to cast back to `IDictionary` to use Shouldly. That dance is gone.
- `ShouldBeEquivalentTo` does a structural comparison — use it when reference equality and `Equals` aren't enough, e.g. comparing two freshly-constructed records or collections.
