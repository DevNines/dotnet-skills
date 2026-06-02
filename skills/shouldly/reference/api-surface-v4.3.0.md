# Shouldly v4.3.0 — API surface

_Generated from the XML doc comments shipped inside these NuGet packages:_

- `Shouldly` v4.3.0 (`github-source`)

_Do not edit by hand — rerun `scripts/update_skill.py`._

Use **only** the members listed here when writing code against Shouldly v4.3.0. If a member you want isn't here, it doesn't exist in this version and you must pick another approach.

## package `Shouldly` v4.3.0

### namespace `Shouldly`

#### `ActualFilteredWithPredicateShouldlyMessage`

**Methods:**

- `#ctor(Expression, object?, object?, string?, [CallerMemberName] string)`


#### `ActualShouldlyMessage`

**Methods:**

- `#ctor(object?, string?, [CallerMemberName] string)`


#### `AsyncShouldlyNotThrowShouldlyMessage`

**Methods:**

- `#ctor(Type, string?, StackTrace, string, [CallerMemberName] string)`


#### `AsyncShouldlyThrowShouldlyMessage`

**Methods:**

- `#ctor(Type, Type, string?, StackTrace)`
- `#ctor(Type, string?, StackTrace, [CallerMemberName] string)`


#### `Case`

**Fields:**

- `Sensitive`


#### `CompleteInShouldlyMessage`

**Methods:**

- `#ctor(string, TimeSpan, string?, [CallerMemberName] string)`


#### `DynamicShould`

**Methods:**

- `HaveProperty(dynamic, string, string?)`
- `Throw<T>([InstantHandle] Action, string?)`


#### `ExpectedActualIgnoreOrderShouldlyMessage`

**Methods:**

- `#ctor(object?, object?, string?, [CallerMemberName] string)`


#### `ExpectedActualKeyShouldlyMessage`

**Methods:**

- `#ctor(object?, object?, object, string?, [CallerMemberName] string)`


#### `ExpectedActualShouldlyMessage`

**Methods:**

- `#ctor(object?, object?, string?, [CallerMemberName] string)`


#### `ExpectedActualToleranceShouldlyMessage`

**Methods:**

- `#ctor(object?, object?, object, string?, [CallerMemberName] string)`


#### `ExpectedActualWithCaseSensitivityShouldlyMessage`

**Methods:**

- `#ctor(object?, object?, Case?, string?, [CallerMemberName] string)`


#### `ExpectedEquivalenceShouldlyMessage`

**Methods:**

- `#ctor(object?, object?, IEnumerable<string>, string?, [CallerMemberName] string)`


#### `ExpectedOrderShouldlyMessage`

**Methods:**

- `#ctor(object?, SortDirection, int, object?, string?, [CallerMemberName] string)`


#### `ExpectedShouldlyMessage`

**Methods:**

- `#ctor(object?, string?, [CallerMemberName] string)`


#### `IShouldlyAssertionContext`


#### `ObjectGraphTestExtensions`

**Methods:**

- `ShouldBeEquivalentTo([NotNullIfNotNull(nameof(expected))] this object?, [NotNullIfNotNull(nameof(actual))] object?, string?)`


#### `Should`

**Methods:**

- `CompleteIn(Action, TimeSpan, string?)`
- `CompleteIn(Func<Task>, TimeSpan, string?)`
- `CompleteIn(Task, TimeSpan, string?)`
- `CompleteIn<T>(Func<T>, TimeSpan, string?)`
- `CompleteIn<T>(Func<Task<T>>, TimeSpan, string?)`
- `CompleteIn<T>(Task<T>, TimeSpan, string?)`
- `NotThrow(Task, TimeSpan, string?)`
- `NotThrow(Task, string?)`
- `NotThrow([InstantHandle] Action, string?)`
- `NotThrow([InstantHandle] Func<Task>, TimeSpan, string?)`
- `NotThrow([InstantHandle] Func<Task>, string?)`
- `NotThrow<T>(Task<T>, TimeSpan, string?)`
- `NotThrow<T>(Task<T>, string?)`
- `NotThrow<T>([InstantHandle] Func<T>, string?)`
- `NotThrow<T>([InstantHandle] Func<Task<T>>, TimeSpan, string?)`
- `NotThrow<T>([InstantHandle] Func<Task<T>>, string?)`
- `NotThrowAsync(Func<Task>, string?)`
- `NotThrowAsync(Task, string?)`
- `Throw(Task, TimeSpan, Type, string?)`
- `Throw(Task, Type, string?)`
- `Throw([InstantHandle] Action, Type, string?)`
- `Throw([InstantHandle] Func<Task>, TimeSpan, Type)`
- `Throw([InstantHandle] Func<Task>, TimeSpan, string?, Type)`
- `Throw([InstantHandle] Func<Task>, Type, string?)`
- `Throw([InstantHandle] Func<object?>, Type)`
- `Throw([InstantHandle] Func<object?>, string?, Type)`
- `Throw<T>(Task, TimeSpan, string?)`
- `Throw<T>(Task, string?)`
- `Throw<T>([InstantHandle] Action, string?)`
- `Throw<T>([InstantHandle] Func<Task>, TimeSpan, string?)`
- `Throw<T>([InstantHandle] Func<Task>, string?)`
- `Throw<T>([InstantHandle] Func<object?>, string?)`
- `ThrowAsync(Func<Task>, Type, string?)`
- `ThrowAsync(Task, Type, string?)`
- `ThrowAsync<T>(Func<Task>, string?)`
- `ThrowAsync<T>(Task, string?)`


#### `ShouldAssertException`

**Methods:**

- `#ctor(string?)`
- `#ctor(string?, Exception?)`

**Fields:**

- `StackTrace`


#### `ShouldBeBooleanExtensions`

**Methods:**

- `ShouldBeFalse([DoesNotReturnIf(true)] this bool, string?)`
- `ShouldBeTrue([DoesNotReturnIf(false)] this bool, string?)`


#### `ShouldBeDecoratedWithExtensions`

**Methods:**

- `ShouldBeDecoratedWith<T>(Type, string?)`


#### `ShouldBeDictionaryTestExtensions`

**Methods:**

- `ShouldContainKey<T1, T2>(IDictionary<TKey, TValue>, TKey, string?)`
- `ShouldContainKey<T1, T2>(IReadOnlyDictionary<TKey, TValue>, TKey, string?)`
- `ShouldContainKeyAndValue<T1, T2>(IDictionary<TKey, TValue>, TKey, TValue, string?)`
- `ShouldContainKeyAndValue<T1, T2>(IReadOnlyDictionary<TKey, TValue>, TKey, TValue, string?)`
- `ShouldNotContainKey<T1, T2>(IDictionary<TKey, TValue>, TKey, string?)`
- `ShouldNotContainKey<T1, T2>(IReadOnlyDictionary<TKey, TValue>, TKey, string?)`
- `ShouldNotContainValueForKey<T1, T2>(IDictionary<TKey, TValue>, TKey, TValue, string?)`
- `ShouldNotContainValueForKey<T1, T2>(IReadOnlyDictionary<TKey, TValue>, TKey, TValue, string?)`


#### `ShouldBeEnumerableTestExtensions`

**Methods:**

- `ShouldAllBe<T>(IEnumerable<T>, [InstantHandle] Expression<Func<T, bool>>, string?)`
- `ShouldBe(IEnumerable<string>, IEnumerable<string>, Case, string?)`
- `ShouldBeEmpty<T>([NotNull] this IEnumerable<T>?, string?)`
- `ShouldBeInOrder<T>(IEnumerable<T>, SortDirection, IComparer<T>?, string?)`
- `ShouldBeInOrder<T>(IEnumerable<T>, SortDirection, string?)`
- `ShouldBeInOrder<T>(IEnumerable<T>, string?)`
- `ShouldBeOfTypes<T>(IEnumerable<T>, Type[])`
- `ShouldBeOfTypes<T>(IEnumerable<T>, Type[], string?)`
- `ShouldBeSubsetOf<T>(IEnumerable<T>, IEnumerable<T>, IEqualityComparer<T>, string?)`
- `ShouldBeSubsetOf<T>(IEnumerable<T>, IEnumerable<T>, string?)`
- `ShouldBeUnique<T>(IEnumerable<T>, IEqualityComparer<T>)`
- `ShouldBeUnique<T>(IEnumerable<T>, IEqualityComparer<T>, string?)`
- `ShouldBeUnique<T>(IEnumerable<T>, string?)`
- `ShouldContain(IEnumerable<double>, double, double, string?)`
- `ShouldContain(IEnumerable<float>, float, double, string?)`
- `ShouldContain<T>(IEnumerable<T>, T, IEqualityComparer<T>, string?)`
- `ShouldContain<T>(IEnumerable<T>, T, string?)`
- `ShouldContain<T>(IEnumerable<T>, [InstantHandle] Expression<Func<T, bool>>, int, string?)`
- `ShouldContain<T>(IEnumerable<T>, [InstantHandle] Expression<Func<T, bool>>, string?)`
- `ShouldHaveSingleItem<T>([NotNull] this IEnumerable<T>?, string?)`
- `ShouldNotBeEmpty<T>([NotNull] this IEnumerable<T>?, string?)`
- `ShouldNotContain<T>(IEnumerable<T>, T, IEqualityComparer<T>, string?)`
- `ShouldNotContain<T>(IEnumerable<T>, T, string?)`
- `ShouldNotContain<T>(IEnumerable<T>, [InstantHandle] Expression<Func<T, bool>>, string?)`


#### `ShouldBeNullExtensions`

**Methods:**

- `ShouldBeNull<T>(T?, string?)`
- `ShouldNotBeNull<T>([NotNull] this T?, string?)`


#### `ShouldBeStringTestExtensions`

**Methods:**

- `ShouldBe([NotNullIfNotNull(nameof(expected))] this string?, [NotNullIfNotNull(nameof(actual))] string?, StringCompareShould)`
- `ShouldBe([NotNullIfNotNull(nameof(expected))] this string?, [NotNullIfNotNull(nameof(actual))] string?, string?)`
- `ShouldBe([NotNullIfNotNull(nameof(expected))] this string?, [NotNullIfNotNull(nameof(actual))] string?, string?, StringCompareShould)`
- `ShouldBeNullOrEmpty(string?, string?)`
- `ShouldBeNullOrWhiteSpace(string?, string?)`
- `ShouldContain(string, string, Case, string?)`
- `ShouldContainWithoutWhitespace(string, object?, string?)`
- `ShouldEndWith([NotNull] this string?, string, Case, string?)`
- `ShouldMatch(string, [RegexPattern] string, string?)`
- `ShouldNotBeNullOrEmpty([NotNull] this string?, string?)`
- `ShouldNotBeNullOrWhiteSpace([NotNull] this string?, string?)`
- `ShouldNotContain(string, string, Case, string?)`
- `ShouldNotEndWith(string?, string, Case)`
- `ShouldNotEndWith(string?, string, string?, Case)`
- `ShouldNotMatch(string, [RegexPattern] string, string?)`
- `ShouldNotStartWith(string?, string, Case, string?)`
- `ShouldStartWith([NotNull] this string?, string, Case, string?)`


#### `ShouldBeTestExtensions`

**Methods:**

- `ShouldBe(DateTime, DateTime, TimeSpan, string?)`
- `ShouldBe(DateTimeOffset, DateTimeOffset, TimeSpan, string?)`
- `ShouldBe(IEnumerable<decimal>, IEnumerable<decimal>, decimal, string?)`
- `ShouldBe(IEnumerable<double>, IEnumerable<double>, double, string?)`
- `ShouldBe(IEnumerable<float>, IEnumerable<float>, double, string?)`
- `ShouldBe(TimeSpan, TimeSpan, TimeSpan, string?)`
- `ShouldBe(decimal, decimal, decimal, string?)`
- `ShouldBe(double, double, double, string?)`
- `ShouldBe(float, float, double, string?)`
- `ShouldBe<T>([NotNullIfNotNull(nameof(expected))] this IEnumerable<T>?, [NotNullIfNotNull(nameof(actual))] IEnumerable<T>?, IEqualityComparer<T>, bool, string?)`
- `ShouldBe<T>([NotNullIfNotNull(nameof(expected))] this IEnumerable<T>?, [NotNullIfNotNull(nameof(actual))] IEnumerable<T>?, bool)`
- `ShouldBe<T>([NotNullIfNotNull(nameof(expected))] this IEnumerable<T>?, [NotNullIfNotNull(nameof(actual))] IEnumerable<T>?, bool, string?)`
- `ShouldBe<T>([NotNullIfNotNull(nameof(expected))] this T?, [NotNullIfNotNull(nameof(actual))] T?, IEqualityComparer<T>, string?)`
- `ShouldBe<T>([NotNullIfNotNull(nameof(expected))] this T?, [NotNullIfNotNull(nameof(actual))] T?, string?)`
- `ShouldBeAssignableTo(object?, Type, string?)`
- `ShouldBeAssignableTo<T>(object?, string?)`
- `ShouldBeGreaterThan<T>(T?, T?, IComparer<T>, string?)`
- `ShouldBeGreaterThan<T>(T?, T?, string?)`
- `ShouldBeGreaterThanOrEqualTo<T>(T?, T?, IComparer<T>, string?)`
- `ShouldBeGreaterThanOrEqualTo<T>(T?, T?, string?)`
- `ShouldBeInRange<T>([DisallowNull] this T, T?, T?, string?)`
- `ShouldBeLessThan<T>(T?, T?, IComparer<T>, string?)`
- `ShouldBeLessThan<T>(T?, T?, string?)`
- `ShouldBeLessThanOrEqualTo<T>(T?, T?, IComparer<T>, string?)`
- `ShouldBeLessThanOrEqualTo<T>(T?, T?, string?)`
- `ShouldBeNegative(decimal, string?)`
- `ShouldBeNegative(double, string?)`
- `ShouldBeNegative(float, string?)`
- `ShouldBeNegative(int, string?)`
- `ShouldBeNegative(long, string?)`
- `ShouldBeNegative(short, string?)`
- `ShouldBeOfType([NotNull] this object?, Type, string?)`
- `ShouldBeOfType<T>([NotNull] this object?, string?)`
- `ShouldBeOneOf<T>(T?, T[])`
- `ShouldBeOneOf<T>(T?, T[], IEqualityComparer<T>, string?)`
- `ShouldBeOneOf<T>(T?, T[], string?)`
- `ShouldBePositive(decimal, string?)`
- `ShouldBePositive(double, string?)`
- `ShouldBePositive(float, string?)`
- `ShouldBePositive(int, string?)`
- `ShouldBePositive(long, string?)`
- `ShouldBePositive(short, string?)`
- `ShouldBeSameAs([NotNullIfNotNull(nameof(expected))] this object?, [NotNullIfNotNull(nameof(actual))] object?, string?)`
- `ShouldNotBe(DateTime, DateTime, TimeSpan, string?)`
- `ShouldNotBe(DateTimeOffset, DateTimeOffset, TimeSpan, string?)`
- `ShouldNotBe(TimeSpan, TimeSpan, TimeSpan, string?)`
- `ShouldNotBe<T>(T?, T?, IEqualityComparer<T>, string?)`
- `ShouldNotBe<T>(T?, T?, string?)`
- `ShouldNotBeAssignableTo(object?, Type, string?)`
- `ShouldNotBeAssignableTo<T>(object?, string?)`
- `ShouldNotBeInRange<T>([DisallowNull] this T, T?, T?, string?)`
- `ShouldNotBeOfType(object?, Type, string?)`
- `ShouldNotBeOfType<T>(object?, string?)`
- `ShouldNotBeOneOf<T>(T?, T[])`
- `ShouldNotBeOneOf<T>(T?, T[], IEqualityComparer<T>, string?)`
- `ShouldNotBeOneOf<T>(T?, T[], string?)`
- `ShouldNotBeSameAs(object?, object?, string?)`


#### `ShouldCompleteInException`

**Methods:**

- `#ctor(string?, ShouldlyTimeoutException?)`


#### `ShouldContainWithCountShouldlyMessage`

**Methods:**

- `#ctor(object?, object?, int, string?, [CallerMemberName] string)`


#### `ShouldMatchApprovedException`

**Methods:**

- `#ctor(string?, string?, string?)`


#### `ShouldMatchApprovedTestExtensions`

**Methods:**

- `ShouldMatchApproved(string, Action<ShouldMatchConfigurationBuilder>?, string?)`


#### `ShouldNotThrowTaskAsyncExtensions`

**Methods:**

- `ShouldNotThrowAsync(Func<Task>, string?)`
- `ShouldNotThrowAsync(Task, string?)`


#### `ShouldSatisfyAllConditionsTestExtensions`

**Methods:**

- `ShouldSatisfyAllConditions(object?, [InstantHandle] params Action[])`
- `ShouldSatisfyAllConditions(object?, string?, [InstantHandle] params Action[])`
- `ShouldSatisfyAllConditions<T>(T, [InstantHandle] params Action<T>[])`
- `ShouldSatisfyAllConditions<T>(T, string?, [InstantHandle] params Action<T>[])`


#### `ShouldThrowAsyncExtensions`

**Methods:**

- `ShouldThrowAsync(Func<Task>, Type, string?)`
- `ShouldThrowAsync(Task, Type, string?)`
- `ShouldThrowAsync<T>(Func<Task>, string?)`
- `ShouldThrowAsync<T>(Task, string?)`


#### `ShouldThrowExtensions`

**Methods:**

- `ShouldNotThrow(Action, string?)`
- `ShouldNotThrow<T>(Func<T>, string?)`
- `ShouldThrow(Action, Type, string?)`
- `ShouldThrow(Func<object?>, Type, string?)`
- `ShouldThrow<T>(Action, string?)`
- `ShouldThrow<T>(Func<object?>, string?)`


#### `ShouldThrowTaskExtensions`

**Methods:**

- `ShouldNotThrow(Func<Task>, TimeSpan, string?)`
- `ShouldNotThrow(Func<Task>, string?)`
- `ShouldNotThrow(Task, TimeSpan, string?)`
- `ShouldNotThrow(Task, string?)`
- `ShouldNotThrow<T>(Func<Task<T>>, TimeSpan, string?)`
- `ShouldNotThrow<T>(Func<Task<T>>, string?)`
- `ShouldNotThrow<T>(Task<T>, TimeSpan, string?)`
- `ShouldNotThrow<T>(Task<T>, string?)`
- `ShouldThrow(Func<Task>, TimeSpan, Type)`
- `ShouldThrow(Func<Task>, TimeSpan, string?, Type)`
- `ShouldThrow(Func<Task>, Type)`
- `ShouldThrow(Func<Task>, string?, Type)`
- `ShouldThrow(Task, TimeSpan, Type)`
- `ShouldThrow(Task, TimeSpan, string?, Type)`
- `ShouldThrow(Task, Type)`
- `ShouldThrow(Task, string?, Type)`
- `ShouldThrow<T>(Func<Task>, TimeSpan, string?)`
- `ShouldThrow<T>(Func<Task>, string?)`
- `ShouldThrow<T>(Task, TimeSpan, string?)`
- `ShouldThrow<T>(Task, string?)`


#### `ShouldlyAssertionContext`

**Methods:**

- `#ctor(string, object?, object?, StackTrace?)`

**Properties:**

- `Actual`
- `CaseSensitivity`
- `CodePart`
- `CustomMessage`
- `Expected`
- `FileName`
- `Filter`
- `HasRelevantActual`
- `HasRelevantKey`
- `IgnoreOrder`
- `Key`
- `LineNumber`
- `MatchCount`
- `OutOfOrderIndex`
- `OutOfOrderObject`
- `Path`
- `ShouldMethod`
- `SortDirection`
- `Timeout`
- `Tolerance`

**Fields:**

- `CodePartMatchesActual`
- `IsNegatedAssertion`


#### `ShouldlyConfiguration`

**Methods:**

- `DisableSourceInErrors`
- `IsSourceDisabledInErrors`

**Properties:**

- `CompareAsObjectTypes`
- `ShouldMatchApprovedDefaults`

**Fields:**

- `DefaultFloatingPointTolerance`
- `DefaultTaskTimeout`


#### `ShouldlyCoreExtensions`

**Methods:**

- `AssertAwesomely<T>(T, Func<T, bool>, object?, object?, Case, string?, [CallerMemberName] string)`
- `AssertAwesomely<T>(T, Func<T, bool>, object?, object?, object, string?, [CallerMemberName] string)`
- `AssertAwesomely<T>(T, Func<T, bool>, object?, object?, string?, [CallerMemberName] string)`
- `AssertAwesomelyIgnoringOrder<T>(T, Func<T, bool>, object?, object?, string?, [CallerMemberName] string)`
- `AssertAwesomelyWithCaseSensitivity<T>(T, Func<T, bool>, object?, object?, Case, string?, [CallerMemberName] string)`


#### `ShouldlyMessage`

**Methods:**

- `ToString`


#### `ShouldlyMethodsAttribute`


#### `ShouldlyThrowMessage`

**Methods:**

- `#ctor(object?, object?, string?, [CallerMemberName] string)`
- `#ctor(object?, string, string?, [CallerMemberName] string)`
- `#ctor(object?, string?, [CallerMemberName] string)`


#### `ShouldlyTimeoutException`

**Methods:**

- `#ctor`
- `#ctor(string?, ShouldlyTimeoutException?)`

**Fields:**

- `StackTrace`


#### `SortDirection`

**Fields:**

- `Ascending`


#### `StringCompareShould`

**Fields:**

- `IgnoreCase`


#### `TaskShouldlyThrowMessage`

**Methods:**

- `#ctor(object?, Exception, string?, [CallerMemberName] string)`
- `#ctor(object?, object?, string?, [CallerMemberName] string)`
- `#ctor(object?, string?, [CallerMemberName] string)`


### namespace `Shouldly.Configuration`

#### `FindMethodUsingAttribute<T>`

**Methods:**

- `GetTestMethodInfo(StackTrace, int)`


#### `FirstNonShouldlyMethodFinder`

**Methods:**

- `GetTestMethodInfo(StackTrace, int)`

**Properties:**

- `Offset`


#### `ITestMethodFinder`


#### `ShouldMatchConfiguration`

**Methods:**

- `#ctor`
- `#ctor(ShouldMatchConfiguration)`

**Properties:**

- `ApprovalFileSubFolder`
- `FileExtension`
- `FilenameDiscriminator`
- `FilenameGenerator`
- `PreventDiff`
- `Scrubber`
- `StringCompareOptions`
- `TestMethodFinder`


#### `ShouldMatchConfigurationBuilder`

**Methods:**

- `#ctor(ShouldMatchConfiguration)`
- `Build`
- `Configure(Action<ShouldMatchConfiguration>)`
- `DoNotIgnoreLineEndings`
- `LocateTestMethodUsingAttribute<T>`
- `NoDiff`
- `SubFolder(string)`
- `UseCallerLocation`
- `WithDiscriminator(string)`
- `WithFileExtension(string)`
- `WithFilenameGenerator(FilenameGenerator)`
- `WithScrubber(Func<string, string>)`
- `WithStringCompareOptions(StringCompareShould)`


#### `TestMethodInfo`

**Methods:**

- `#ctor(StackFrame)`

**Properties:**

- `DeclaringTypeName`
- `MethodName`
- `SourceFileDirectory`


### namespace `Shouldly.ShouldlyExtensionMethods`

#### `ShouldHaveEnumExtensions`

**Methods:**

- `ShouldHaveFlag(Enum, Enum, string?)`
- `ShouldNotHaveFlag(Enum, Enum, string?)`
