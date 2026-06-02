# Ardalis.SmartEnum v8.2.0 — API surface

_Generated from the XML doc comments shipped inside these NuGet packages:_

- `Ardalis.SmartEnum` v8.2.0 (`netstandard2.0`)
- `Ardalis.SmartEnum.SystemTextJson` v8.1.0 (`netstandard2.0`)  ← independent versioning
- `Ardalis.SmartEnum.EFCore` v8.2.0 (`net8.0`)
- `Ardalis.SmartEnum.AutoFixture` v8.1.0 (`netstandard2.0`)  ← independent versioning
- `Ardalis.SmartEnum.Dapper` v8.2.0 (`netstandard2.0`)
- `Ardalis.SmartEnum.Utf8Json` v8.1.0 (`netstandard2.0`)  ← independent versioning

_Do not edit by hand — rerun `scripts/update_skill.py`._

Use **only** the members listed here when writing code against Ardalis.SmartEnum v8.2.0. If a member you want isn't here, it doesn't exist in this version and you must pick another approach.

## package `Ardalis.SmartEnum` v8.2.0

### namespace `Ardalis.SmartEnum`

#### `AllowNegativeInputValuesAttribute`

Marker attribute used to indicate that a `SmartEnum` allows negative values.


#### `AllowUnsafeFlagEnumValuesAttribute`

Marker attribute to indicate that a `SmartEnum` should allow unsafe flag enum values.


#### `ISmartEnum`


#### `SmartEnumComparerAttribute<T>`

Base class for an `Attribute` to specify the `IEqualityComparer<T>` for a SmartEnum.

**Methods:**

- `#ctor(Generic.IEqualityComparer<T1>)`
  - `comparer`

**Properties:**

- `Comparer`


#### `SmartEnumExtensions`

**Methods:**

- `IsSmartEnum(Type)`
  - `type`
- `IsSmartEnum(Type, Type[]@)`
  - `type`
  - `genericArguments`
- `TryGetValues(Type, Generic.IEnumerable<object>@)`
  - `type`
  - `enums`


#### `SmartEnumNameAttribute`

A `ValidationAttribute` that ensures the provided value matches the
`SmartEnum<T>`.Name of a `SmartEnum<T>`/`SmartEnum<T1, T2>`.
Nulls and non-`String` values are considered valid
(add `RequiredAttribute` if you want the field to be required).

**Methods:**

- `#ctor(Type, string, bool, string)`
  - `smartEnumType`: The expected SmartEnum type.
  - `propertyName`: The name of the property that the attribute is being used on.
  - `allowCaseInsensitiveMatch`: Unless this is true, only exact case matching the
`SmartEnum<T>` Name will validate.
  - `errorMessage`: Message template to show when validation fails. {0} is propertyName and
{1} is the comma-separated list of SmartEnum names.
- `IsValid(object)`
  - `value`


#### `SmartEnumNotFoundException`

The exception that is thrown when a item is not found.

**Methods:**

- `#ctor`
  - Initializes a new instance of the `SmartEnumNotFoundException` class.
- `#ctor(string)`
  - Initializes a new instance of the `SmartEnumNotFoundException` class with a specified error message.
  - `message`: The error message that explains the reason for the exception.
- `#ctor(string, Exception)`
  - Initializes a new instance of the `SmartEnumNotFoundException` class with a specified error message and
a reference to the inner exception that is the cause of this exception.
  - `message`: The error message that explains the reason for the exception.
  - `innerException`: The exception that is the cause of the current exception. If the innerException parameter is not a null reference,
the current exception is raised in a `catch` block that handles the inner exception.


#### `SmartEnumStringComparerAttribute`

Attribute to apply to `SmartEnum<T1, T2>` of type `String` to specify how to compare
the enum values

**Methods:**

- `#ctor(stringComparison)`
  - `comparison`


#### `SmartEnum<T>`

A base type to use for creating smart enums with inner value of type `Int32`.

**Methods:**

- `#ctor(string, int)`
  - `name`
  - `value`


#### `SmartEnum<T1, T2>`

A base type to use for creating smart enums.

**Methods:**

- `#ctor(string, T2)`
  - `name`
  - `value`
- `CompareTo(SmartEnum<T1,T2>)`
  - Compares this instance to a specified `SmartEnum<T1, T2>` and returns an indication of their relative values.
  - `other`: An `SmartEnum<T1, T2>` value to compare to this instance.
  - returns: A signed number indicating the relative values of this instance and other.
- `Equals(SmartEnum<T1,T2>)`
  - Returns a value indicating whether this instance is equal to a specified `SmartEnum<T1, T2>` value.
  - `other`: An `SmartEnum<T1, T2>` value to compare to this instance.
  - returns: `true` if other has the same value as this instance; otherwise, `false`.
- `Equals(object)`
  - `obj`
- `FromName(string, bool)`
  - Gets the item associated with the specified name.
  - `name`: The name of the item to get.
  - `ignoreCase`: `true` to ignore case during the comparison; otherwise, `false`.
  - returns: The item associated with the specified name.
If the specified name is not found, throws a `KeyNotFoundException`.
- `FromValue(T2)`
  - Gets an item associated with the specified value.
  - `value`: The value of the item to get.
  - returns: The first item found that is associated with the specified value.
If the specified value is not found, throws a `KeyNotFoundException`.
- `FromValue(T2, T1)`
  - Gets an item associated with the specified value.
  - `value`: The value of the item to get.
  - `defaultValue`: The value to return when item not found.
  - returns: The first item found that is associated with the specified value.
If the specified value is not found, returns defaultValue.
- `GetHashCode`
- `ToString`
- `TryFromName(string, T1@)`
  - Gets the item associated with the specified name.
  - `name`: The name of the item to get.
  - `result`: When this method returns, contains the item associated with the specified name, if the key is found;
otherwise, `null`. This parameter is passed uninitialized.
  - returns: `true` if the `SmartEnum<T1, T2>` contains an item with the specified name; otherwise, `false`.
- `TryFromName(string, bool, T1@)`
  - Gets the item associated with the specified name.
  - `name`: The name of the item to get.
  - `ignoreCase`: `true` to ignore case during the comparison; otherwise, `false`.
  - `result`: When this method returns, contains the item associated with the specified name, if the name is found;
otherwise, `null`. This parameter is passed uninitialized.
  - returns: `true` if the `SmartEnum<T1, T2>` contains an item with the specified name; otherwise, `false`.
- `TryFromValue(T2, T1@)`
  - Gets an item associated with the specified value.
  - `value`: The value of the item to get.
  - `result`: When this method returns, contains the item associated with the specified value, if the value is found;
otherwise, `null`. This parameter is passed uninitialized.
  - returns: `true` if the `SmartEnum<T1, T2>` contains an item with the specified name; otherwise, `false`.
- `When(Generic.IEnumerable<SmartEnum<T1,T2>>)`
  - When this instance is one of the specified `SmartEnum<T1, T2>` parameters.
Execute the action in the subsequent call to Then().
  - `smartEnums`: A collection of `SmartEnum<T1, T2>` values to compare to this instance.
  - returns: A executor object to execute a supplied action.
- `When(SmartEnum<T1,T2>)`
  - When this instance is one of the specified `SmartEnum<T1, T2>` parameters.
Execute the action in the subsequent call to Then().
  - `smartEnumWhen`: A collection of `SmartEnum<T1, T2>` values to compare to this instance.
  - returns: A executor object to execute a supplied action.
- `When(SmartEnum<T1,T2>[])`
  - When this instance is one of the specified `SmartEnum<T1, T2>` parameters.
Execute the action in the subsequent call to Then().
  - `smartEnums`: A collection of `SmartEnum<T1, T2>` values to compare to this instance.
  - returns: A executor object to execute a supplied action.
- `op_Equality(SmartEnum<T1,T2>, SmartEnum<T1,T2>)`
  - `left`
  - `right`
- `op_Explicit((T2)~SmartEnum<T1,T2>)`
  - `value`
- `op_GreaterThan(SmartEnum<T1,T2>, SmartEnum<T1,T2>)`
  - `left`
  - `right`
- `op_GreaterThanOrEqual(SmartEnum<T1,T2>, SmartEnum<T1,T2>)`
  - `left`
  - `right`
- `op_Implicit((SmartEnum<T1,T2>)~T2)`
  - `smartEnum`
- `op_Inequality(SmartEnum<T1,T2>, SmartEnum<T1,T2>)`
  - `left`
  - `right`
- `op_LessThan(SmartEnum<T1,T2>, SmartEnum<T1,T2>)`
  - `left`
  - `right`
- `op_LessThanOrEqual(SmartEnum<T1,T2>, SmartEnum<T1,T2>)`
  - `left`
  - `right`

**Properties:**

- `List`
  - Gets a collection containing all the instances of `SmartEnum<T1, T2>`.
  - remarks: Retrieves all the instances of `SmartEnum<T1, T2>` referenced by public static read-only fields in the current class or its bases.
- `Name`
  - Gets the name.
- `Value`
  - Gets the value.


#### `SmartFlagEngine<T1, T2>`

**Methods:**

- `#ctor`
- `GetFlagEnumValues(T2, Generic.IEnumerable<T1>)`
  - Returns an `IEnumerable<T>` representing a given value
  - `value`: The value to retrieve.
  - `allEnumList`: an `IEnumerable<T>` of `SmartFlagEnum<T>` from which to retrieve values.
- `GetMaxValue`
  - Gets the largest possible value of the underlying type for the SmartFlagEnum.
  - returns: The value of the constant `MaxValue` field defined by the underlying type TValue.


#### `SmartFlagEnumExtensions`

**Methods:**

- `IsSmartFlagEnum(Type)`
  - `type`
- `IsSmartFlagEnum(Type, Type[]@)`
  - `type`
  - `genericArguments`
- `TryGetFlagEnumValuesByName<T1, T2>(Generic.Dictionary<string,T1>, string, Generic.IEnumerable<T1>@)`
  - `dictionary`
  - `names`
  - `outputEnums`
  - `<TEnum>`
  - `<TValue>`


#### `SmartFlagEnum<T>`

A base type to use for creating smart enums with inner value of type `Int32`.

**Methods:**

- `#ctor(string, int)`
  - `name`
  - `value`


#### `SmartFlagEnum<T1, T2>`

A base type to use for creating smart enums.

**Methods:**

- `#ctor(string, T2)`
  - `name`
  - `value`
- `CompareTo(SmartFlagEnum<T1,T2>)`
  - Compares this instance to a specified `SmartFlagEnum<T1, T2>` and returns an indication of their relative values.
  - `other`: An `SmartFlagEnum<T1, T2>` value to compare to this instance.
  - returns: A signed number indicating the relative values of this instance and other.
- `DeserializeValue(T2)`
  - Attempts to retrieve a single `SmartFlagEnum<T>` by value. (Bypasses all Flag behaviour)
  - `value`
- `Equals(SmartFlagEnum<T1,T2>)`
  - Returns a value indicating whether this instance is equal to a specified `SmartFlagEnum<T1, T2>` value.
  - `other`: An `SmartFlagEnum<T1, T2>` value to compare to this instance.
  - returns: `true` if other has the same value as this instance; otherwise, `false`.
- `Equals(object)`
- `FromName(string, bool, bool)`
  - Gets the items associated with the specified names.
  - `names`: The names of the item/s to get.
  - `ignoreCase`: `true` to ignore case during the comparison; otherwise, `false`.
  - `deserialize`
  - returns: The items associated with the specified names.
- `FromValue(T2)`
  - Gets an `IEnumerable<T>` associated with the specified value.
  - `value`: The value of the item/s to get.
  - returns: An `IEnumerable<T>` containing the item/s found.
- `FromValue(T2, Generic.IEnumerable<T1>)`
  - Gets an `IEnumerable<T>` associated with the specified value.
  - `value`: The value of the item/s to get.
  - `defaultValue`: The value to return when no items found.
  - returns: An `IEnumerable<T>` containing the item/s found.
If the specified value is not found, returns defaultValue.
- `FromValueToString(T2)`
  - Returns a `String` representation of a given value as a series of comma delineated enum names.
  - `value`: The value of the item/s to get.
  - returns: A comma delineated series of enum names as a `String`
- `GetHashCode`
  - Returns the GetHashCode of the value
- `ToString`
  - Returns the _name of the `SmartFlagEnum<T1, T2>`.
- `TryFromName(string, Generic.IEnumerable<T1>@)`
  - Gets the items associated with the specified names.
  - `names`: The names of the item/s to get.
  - `result`: When this method returns, contains the item associated with the specified names, if the key is found;
otherwise, `null`. This parameter is passed uninitialized.
  - returns: `true` if the `SmartFlagEnum<T1, T2>` contains an item with the specified names; otherwise, `false`.
- `TryFromName(string, bool, Generic.IEnumerable<T1>@)`
  - Gets the items associated with the specified names.
  - `names`: The names of the item/s to get.
  - `ignoreCase`: `true` to ignore case during the comparison; otherwise, `false`.
  - `result`: When this method returns, contains the items associated with the specified names, if any names are found;
otherwise, `null`. This parameter is passed uninitialized.
  - returns: `true` if the `SmartFlagEnum<T1, T2>` contains an item with the specified names; otherwise, `false`.
- `TryFromValue(T2, Generic.IEnumerable<T1>@)`
  - Gets an `IEnumerable<T>` associated with the specified value.
  - `value`: The value of the item/s to get.
  - `result`: When this method returns, contains the IEnumerable of item/s associated with the specified value, if any value is found;
otherwise, `null`. This parameter is passed uninitialized.
  - returns: `true` if the `SmartFlagEnum<T1, T2>` contains any items with the specified names; otherwise, `false`.
- `TryFromValueToString(T2, string@)`
  - Returns a `String` representation of a given value as a series of comma delineated enum names.
  - `value`: The value of the item/s to get.
  - `result`: When this method returns, contains the string representation associated with the specified value, if any value is found;
otherwise, returns null.
  - returns: A comma delineated series of enum names as a `String`
- `When(Generic.IEnumerable<SmartFlagEnum<T1,T2>>)`
  - When this instance is one of the specified `SmartFlagEnum<T1, T2>` parameters.
Execute the action in the subsequent call to Then().
  - `smartEnums`: A collection of `SmartFlagEnum<T1, T2>` values to compare to this instance.
  - returns: A executor object to execute a supplied action.
- `When(SmartFlagEnum<T1,T2>)`
  - When this instance is one of the specified `SmartFlagEnum<T1, T2>` parameters.
Execute the action in the subsequent call to Then().
  - `smartFlagEnumWhen`: A collection of `SmartFlagEnum<T1, T2>` values to compare to this instance.
  - returns: A executor object to execute a supplied action.
- `When(SmartFlagEnum<T1,T2>[])`
  - When this instance is one of the specified `SmartFlagEnum<T1, T2>` parameters.
Execute the action in the subsequent call to Then().
  - `smartEnums`: A collection of `SmartFlagEnum<T1, T2>` values to compare to this instance.
  - returns: A executor object to execute a supplied action.
- `op_Equality(SmartFlagEnum<T1,T2>, SmartFlagEnum<T1,T2>)`
  - `left`
  - `right`
- `op_Explicit((T2)~SmartFlagEnum<T1,T2>)`
  - `value`
- `op_GreaterThan(SmartFlagEnum<T1,T2>, SmartFlagEnum<T1,T2>)`
  - `left`
  - `right`
- `op_GreaterThanOrEqual(SmartFlagEnum<T1,T2>, SmartFlagEnum<T1,T2>)`
  - `left`
  - `right`
- `op_Implicit((SmartFlagEnum<T1,T2>)~T2)`
  - `smartFlagEnum`
- `op_Inequality(SmartFlagEnum<T1,T2>, SmartFlagEnum<T1,T2>)`
  - `left`
  - `right`
- `op_LessThan(SmartFlagEnum<T1,T2>, SmartFlagEnum<T1,T2>)`
  - `left`
  - `right`
- `op_LessThanOrEqual(SmartFlagEnum<T1,T2>, SmartFlagEnum<T1,T2>)`
  - `left`
  - `right`

**Properties:**

- `List`
  - Gets a collection containing all the instances of `SmartFlagEnum<T1, T2>`.
  - remarks: Retrieves all the instances of `SmartFlagEnum<T1, T2>` referenced by public static read-only fields in the current class or its bases.
- `Name`
  - Gets the names.
- `Value`
  - Gets the value.


### namespace `Ardalis.SmartEnum.Core`

#### `SmartEnumThen<T1, T2>`

**Methods:**

- `Then(Action)`
  - Calls doThis Action when the preceding When call matches.
  - `doThis`: Action method to call.
  - returns: A chainable instance of CaseWhen for more when calls.


#### `SmartEnumWhen<T1, T2>`

**Methods:**

- `Default(Action)`
  - Execute this action if no other calls to When have matched.
  - `action`: The Action to call.
- `When(Generic.IEnumerable<ISmartEnum>)`
  - When this instance is one of the specified `SmartEnum<T1, T2>` parameters.
Execute the action in the subsequent call to Then().
  - `smartEnums`: A collection of `SmartEnum<T1, T2>` values to compare to this instance.
  - returns: A executor object to execute a supplied action.
- `When(ISmartEnum)`
  - When this instance is one of the specified `SmartEnum<T1, T2>` parameters.
Execute the action in the subsequent call to Then().
  - `smartEnumWhen`: A collection of `SmartEnum<T1, T2>` values to compare to this instance.
  - returns: A executor object to execute a supplied action.
- `When(ISmartEnum[])`
  - When this instance is one of the specified `SmartEnum<T1, T2>` parameters.
Execute the action in the subsequent call to Then().
  - `smartEnums`: A collection of `SmartEnum<T1, T2>` values to compare to this instance.
  - returns: A executor object to execute a supplied action.


### namespace `Ardalis.SmartEnum.Exceptions`

#### `InvalidFlagEnumValueParseException`

**Methods:**

- `#ctor`
  - Initializes a new instance of the `InvalidFlagEnumValueParseException` class.
- `#ctor(string)`
  - Initializes a new instance of the `InvalidFlagEnumValueParseException` class with a user specified error message.
  - `message`: The error message that explains the reason for the exception.
- `#ctor(string, Exception)`
  - Initializes a new instance of the `InvalidFlagEnumValueParseException` class with a user specified error message
and a wrapped innerException that is the cause of this exception.
  - `message`: The error message that explains the reason for the exception.
  - `innerException`


#### `NegativeValueArgumentException`

The exception that is thrown when a negative value is provided as an argument value.

**Methods:**

- `#ctor`
  - Initializes a new instance of the `NegativeValueArgumentException` class.
- `#ctor(string)`
  - Initializes a new instance of the `NegativeValueArgumentException` class with a specified error message.
  - `message`: The error message that explains the reason for the exception.
- `#ctor(string, Exception)`
  - Initializes a new instance of the `NegativeValueArgumentException` class with a specified error message and
a reference to the inner exception that is the cause of this exception.
  - `message`: The error message that explains the reason for the exception.
  - `innerException`: The exception that is the cause of the current exception. If the innerException parameter is not a null reference,
the current exception is raised in a `catch` block that handles the inner exception.


#### `SmartFlagEnumContainsNegativeValueException`

**Methods:**

- `#ctor`
  - Initializes a new instance of the `SmartFlagEnumContainsNegativeValueException` class.
- `#ctor(string)`
  - Initializes a new instance of the `SmartFlagEnumContainsNegativeValueException` class with a user specified error message.
  - `message`: The error message that explains the reason for the exception.
- `#ctor(string, Exception)`
  - Initializes a new instance of the `SmartFlagEnumContainsNegativeValueException` class with a user specified error message
and a wrapped innerException that is the cause of this exception.
  - `message`: The error message that explains the reason for the exception.
  - `innerException`


#### `SmartFlagEnumDoesNotContainPowerOfTwoValuesException`

The exception that is thrown when a `SmartFlagEnum<T>` does not contain consecutive power of two values.

**Methods:**

- `#ctor`
  - Initializes a new instance of the `SmartFlagEnumDoesNotContainPowerOfTwoValuesException` class.
- `#ctor(string)`
  - Initializes a new instance of the `SmartFlagEnumDoesNotContainPowerOfTwoValuesException` class with a specified error message.
  - `message`: The error message that explains the reason for the exception.
- `#ctor(string, Exception)`
  - Initializes a new instance of the `SmartFlagEnumDoesNotContainPowerOfTwoValuesException` class with a specified error message and
a reference to the inner exception that is the cause of this exception.
  - `message`: The error message that explains the reason for the exception.
  - `innerException`: The exception that is the cause of the current exception. If the innerException parameter is not a null reference,
the current exception is raised in a `catch` block that handles the inner exception.



## package `Ardalis.SmartEnum.SystemTextJson` v8.1.0

### namespace `Ardalis.SmartEnum.SystemTextJson`

#### `SmartEnumNameConverter<T1, T2>`

**Methods:**

- `Read(Json.Utf8JsonReader@, Type, Json.JsonSerializerOptions)`
  - `reader`
  - `typeToConvert`
  - `options`
- `ReadAsPropertyName(Json.Utf8JsonReader@, Type, Json.JsonSerializerOptions)`
  - `reader`
  - `typeToConvert`
  - `options`
- `Write(Json.Utf8JsonWriter, T1, Json.JsonSerializerOptions)`
  - `writer`
  - `value`
  - `options`
- `WriteAsPropertyName(Json.Utf8JsonWriter, T1, Json.JsonSerializerOptions)`
  - `writer`
  - `value`
  - `options`


#### `SmartEnumValueConverter<T1, T2>`

**Methods:**

- `Read(Json.Utf8JsonReader@, Type, Json.JsonSerializerOptions)`
  - `reader`
  - `typeToConvert`
  - `options`
- `ReadAsPropertyName(Json.Utf8JsonReader@, Type, Json.JsonSerializerOptions)`
  - `reader`
  - `typeToConvert`
  - `options`
- `Write(Json.Utf8JsonWriter, T1, Json.JsonSerializerOptions)`
  - `writer`
  - `value`
  - `options`
- `WriteAsPropertyName(Json.Utf8JsonWriter, T1, Json.JsonSerializerOptions)`
  - `writer`
  - `value`
  - `options`


#### `SmartFlagEnumNameConverter<T1, T2>`

**Methods:**

- `Read(Json.Utf8JsonReader@, Type, Json.JsonSerializerOptions)`
  - `reader`
  - `typeToConvert`
  - `options`
- `Write(Json.Utf8JsonWriter, T1, Json.JsonSerializerOptions)`
  - `writer`
  - `value`
  - `options`

**Properties:**

- `HandleNull`


#### `SmartFlagEnumValueConverter<T1, T2>`

**Methods:**

- `Read(Json.Utf8JsonReader@, Type, Json.JsonSerializerOptions)`
  - `reader`
  - `typeToConvert`
  - `options`
- `Write(Json.Utf8JsonWriter, T1, Json.JsonSerializerOptions)`
  - `writer`
  - `value`
  - `options`

**Properties:**

- `HandleNull`
  - Defaults to true.



## package `Ardalis.SmartEnum.EFCore` v8.2.0

### namespace `Ardalis.SmartEnum.EFCore`

#### `SmartEnumConverter<T1, T2>`

**Methods:**

- `#ctor`
- `GetFromValue(T2)`
  - `value`


### namespace `SmartEnum.EFCore`

#### `SmartEnumConverterExtensions`

**Methods:**

- `ConfigureSmartEnum(Microsoft.EntityFrameworkCore.ModelBuilder)`
  - Adds a converter for all properties derived from `SmartEnum<T1, T2>`
so that entity framework core can work with it.
  - `modelBuilder`
- `ConfigureSmartEnum(Microsoft.EntityFrameworkCore.ModelConfigurationBuilder)`
  - Adds a converter for all properties derived from `SmartEnum<T1, T2>`
so that entity framework core can work with it.



## package `Ardalis.SmartEnum.AutoFixture` v8.1.0

### namespace `Ardalis.SmartEnum.AutoFixture`

#### `SmartEnumCustomization`

**Methods:**

- `Customize(AutoFixture.IFixture)`
  - `fixture`


#### `SmartEnumSpecimenBuilder`

**Methods:**

- `Create(object, AutoFixture.Kernel.ISpecimenContext)`
  - `request`
  - `context`



## package `Ardalis.SmartEnum.Dapper` v8.2.0

### namespace `Ardalis.SmartEnum.Dapper`

#### `DapperRegistration<T1, T2>`

A static class responsible for ensuring that the SmartEnum type handler specified by
TSmartEnumTypeHandler has been added to `SqlMapper`
for the SmartEnum type specified by TEnum, which has a backing data
type of `Int32`.

**Methods:**

- `EnsureTypeHandlerAdded`
  - Ensures that the SmartEnum type handler specified by
TSmartEnumTypeHandler has been added to `SqlMapper`
for the SmartEnum type specified by TEnum.


Note: Calling this method more than once with a given set of generic arguments
has no effect.


#### `DapperRegistration<T1, T2, T3>`

A static class responsible for ensuring that the SmartEnum type handler specified by
TSmartEnumTypeHandler has been added to `SqlMapper`
for the SmartEnum type specified by TEnum.

**Methods:**

- `EnsureTypeHandlerAdded`
  - Ensures that the SmartEnum type handler specified by
TSmartEnumTypeHandler has been added to `SqlMapper`
for the SmartEnum type specified by TEnum.


Note: Calling this method more than once with a given set of generic arguments
has no effect.


#### `DapperSmartEnumByName<T>`

A base type to use for creating smart enums with a backing data type of `Int32`
that automatically register a Dapper type handler for themselves. The handler registered by
this method maps the name of a `SmartEnum` to a database column.

**Methods:**

- `#ctor(string, int)`


#### `DapperSmartEnumByName<T1, T2>`

A base type to use for creating smart enums that automatically register a Dapper type
handler for themselves. The handler registered by this method maps the name of a
`SmartEnum` to a database column.

**Methods:**

- `#ctor(string, T2)`


#### `DapperSmartEnumByValue<T>`

A base type to use for creating smart enums with a backing data type of `Int32`
that automatically register a Dapper type handler for themselves. The handler registered
by this method maps the value of a `SmartEnum` to a database column.

**Methods:**

- `#ctor(string, int)`


#### `DapperSmartEnumByValue<T1, T2>`

A base type to use for creating smart enums that automatically register a Dapper type
handler for themselves. The handler registered by this method maps the value of a
`SmartEnum` to a database column.

**Methods:**

- `#ctor(string, T2)`


#### `DapperSmartEnum<T1, T2>`

A base type to use for creating smart enums with a backing data type of `Int32`
that automatically register a Dapper type handler for themselves.

**Methods:**

- `#ctor(string, int)`


#### `DapperSmartEnum<T1, T2, T3>`

A base type to use for creating smart enums that automatically register a Dapper type
handler for themselves.

**Methods:**

- `#ctor(string, T2)`


#### `DbTypeAttribute`

Indicates that a `SmartEnumTypeHandler<T1, T2>` should assign the
specified `DbType` to a parameter before a command executes.

**Methods:**

- `#ctor(DbType)`
  - Initializes a new instance of the `DbTypeAttribute` class with the
specified `DbType` value.
  - `value`

**Properties:**

- `DbType`
  - Gets the `DbType` to be assigned to a parameter before a
command executes.


#### `DoNotSetDbTypeAttribute`

Indicates that a `SmartEnumTypeHandler<T1, T2>` should not set
the `DbType` property of a parameter before a command executes.


#### `IgnoreCaseAttribute`

Indicates that a `SmartEnumByNameTypeHandler<T1, T2>` should ignore
case when parsing a database value into a `SmartEnum`.


#### `SmartEnumByNameTypeHandler<T>`

A type handler that maps the name of a `SmartEnum` with a backing data type
of `Int32` to a database column.


#### `SmartEnumByNameTypeHandler<T1, T2>`

A type handler that maps the name of a `SmartEnum` to a database column.

**Methods:**

- `#ctor`
  - Initializes a new instance of the `SmartEnumByNameTypeHandler<T1, T2>` class.
- `ConfigureFromCustomAttribute(Attribute)`
- `GetParameterValue(T1)`
- `Parse(object)`

**Properties:**

- `IgnoreCase`
  - Gets or sets whether to ignore case when creating the SmartEnum from name.


#### `SmartEnumByValueTypeHandler<T>`

A type handler that maps the value of a `SmartEnum` with a backing data type
of `Int32` to a database column.


#### `SmartEnumByValueTypeHandler<T1, T2>`

A type handler that maps the value of a `SmartEnum` to a database column.

**Methods:**

- `#ctor`
  - Initializes a new instance of the `SmartEnumByValueTypeHandler<T1, T2>`
class, setting the `DbType` property
according to the type of the TValue type parameter.
- `GetParameterValue(T1)`
- `Parse(object)`


#### `SmartEnumTypeHandler<T1, T2>`

The base class for `SmartEnum` type handlers.

**Methods:**

- `ConfigureFromCustomAttribute(Attribute)`
  - Configures the type handler from the specified attribute.
  - returns: if the type handler was modified, otherwise
.
- `GetParameterValue(T1)`
  - When overriden in a derived class, gets the value to be assigned to a parameter before
a command executes.


Called from the base class's `SetValue`
method.
  - `smartEnum`: The SmartEnum to be used to get the parameter value.


When called from the base `SmartEnumTypeHandler<T1, T2>`
class, this parameter will never be .
- `SetValue(IDbDataParameter, T1)`
- `UnexpectedDatabaseValue(object, Type, Exception)`
  - Gets exception to be thrown when a database value has an unexpected type.

**Properties:**

- `DbType`
  - Gets or sets the `DbType` to be assigned to a parameter before
a command executes. If , a parameter will not have its
`DbType` property set.



## package `Ardalis.SmartEnum.Utf8Json` v8.1.0

### namespace `Ardalis.SmartEnum.Utf8Json`

#### `SmartEnumNameFormatter<T1, T2>`

**Methods:**

- `Deserialize(Utf8Json.JsonReader@, Utf8Json.IJsonFormatterResolver)`
  - `reader`
  - `formatterResolver`
- `Serialize(Utf8Json.JsonWriter@, T1, Utf8Json.IJsonFormatterResolver)`
  - `writer`
  - `value`
  - `formatterResolver`


#### `SmartEnumNameResolver`

**Methods:**

- `GetFormatter<T>`
  - `<T>`

**Fields:**

- `Instance`


#### `SmartEnumValueFormatter<T1, T2>`

**Methods:**

- `Deserialize(Utf8Json.JsonReader@, Utf8Json.IJsonFormatterResolver)`
  - `reader`
  - `formatterResolver`
- `Serialize(Utf8Json.JsonWriter@, T1, Utf8Json.IJsonFormatterResolver)`
  - `writer`
  - `value`
  - `formatterResolver`


#### `SmartEnumValueResolver`

**Methods:**

- `GetFormatter<T>`
  - GetFormatter
  - `<T>`

**Fields:**

- `Instance`


#### `SmartFlagEnumNameFormatter<T1, T2>`

**Methods:**

- `Deserialize(Utf8Json.JsonReader@, Utf8Json.IJsonFormatterResolver)`
  - `reader`
  - `formatterResolver`
- `Serialize(Utf8Json.JsonWriter@, T1, Utf8Json.IJsonFormatterResolver)`
  - `writer`
  - `value`
  - `formatterResolver`


#### `SmartFlagEnumNameResolver`

**Methods:**

- `GetFormatter<T>`
  - `<T>`

**Fields:**

- `Instance`


#### `SmartFlagEnumValueFormatter<T1, T2>`

**Methods:**

- `Deserialize(Utf8Json.JsonReader@, Utf8Json.IJsonFormatterResolver)`
  - `reader`
  - `formatterResolver`
- `Serialize(Utf8Json.JsonWriter@, T1, Utf8Json.IJsonFormatterResolver)`
  - `writer`
  - `value`
  - `formatterResolver`


#### `SmartFlagEnumValueResolver`

**Methods:**

- `#ctor`
- `GetFormatter<T>`
  - `<T>`

**Fields:**

- `Instance`
