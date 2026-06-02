# NSubstitute v5.3.0 — API surface

_Generated from the XML doc comments shipped inside these NuGet packages:_

- `NSubstitute` v5.3.0 (`netstandard2.0`)

_Do not edit by hand — rerun `scripts/update_skill.py`._

Use **only** the members listed here when writing code against NSubstitute v5.3.0. If a member you want isn't here, it doesn't exist in this version and you must pick another approach.

## package `NSubstitute` v5.3.0

### namespace `NSubstitute`

#### `Arg`

Argument matchers used for specifying calls to substitutes.

**Methods:**

- `Any<T>`
  - Match any argument value compatible with type T.
- `Do<T>(Action<T1>)`
  - Capture any argument compatible with type T and use it to call the useArgument function
whenever a matching call is made to the substitute.
- `Do<T>(Action<object>)`
  - Capture any argument compatible with type T and use it to call the useArgument function
whenever a matching call is made to the substitute.
- `Invoke`
  - Invoke any `Action` argument whenever a matching call is made to the substitute.
- `Invoke<T1, T2, T3, T4>(T1, T2, T3, T4)`
  - Invoke any `Action<T1, T2, T3, T4>` argument with specified arguments whenever a matching call is made to the substitute.
- `Invoke<T1, T2, T3>(T1, T2, T3)`
  - Invoke any `Action<T1, T2, T3>` argument with specified arguments whenever a matching call is made to the substitute.
- `Invoke<T1, T2>(T1, T2)`
  - Invoke any `Action<T1, T2>` argument with specified arguments whenever a matching call is made to the substitute.
- `Invoke<T>(T1)`
  - Invoke any `Action<T>` argument with specified argument whenever a matching call is made to the substitute.
- `InvokeDelegate<T>(object[])`
  - Invoke any TDelegate argument with specified arguments whenever a matching call is made to the substitute.
  - `arguments`: Arguments to pass to delegate.
- `Is<T>(Expressions.Expression<Predicate<T1>>)`
  - Match argument that satisfies predicate.
If the predicate throws an exception for an argument it will be treated as non-matching.
- `Is<T>(Expressions.Expression<Predicate<object>>)`
  - Match argument that satisfies predicate.
If the predicate throws an exception for an argument it will be treated as non-matching.
- `Is<T>(T1)`
  - Match argument that is equal to value.


#### `Callback`

Perform this chain of callbacks and/or always callback when called.

**Methods:**

- `Always(Action<Core.CallInfo>)`
  - Perform this action always when callback is called.
  - `doThis`
- `AlwaysThrow<T>(Func<Core.CallInfo,T1>)`
  - Throw exception returned by function always when callback is called.
  - `throwThis`: The throw this.
  - `<TException>`: The type of the exception.
- `AlwaysThrow<T>(T1)`
  - Throw this exception always when callback is called.
  - `exception`: The exception.
  - `<TException>`: The type of the exception.
- `First(Action<Core.CallInfo>)`
  - Perform as first in chain of callback when called.
  - `doThis`
- `FirstThrow<T>(Func<Core.CallInfo,T1>)`
  - Throw exception returned by function as first callback in chain of callback when called.
  - `throwThis`
- `FirstThrow<T>(T1)`
  - Throw this exception as first callback in chain of callback when called.
  - `exception`


#### `ClearOptions`

**Fields:**

- `All`
  - Clears all received calls and configured return values and callbacks.
- `CallActions`
  - Clear all call actions configured for this substitute (via When..Do, Arg.Invoke, and Arg.Do)
- `ReceivedCalls`
  - Clear all the received calls
- `ReturnValues`
  - Clear all configured return results (including auto-substituted values).


#### `Raise`

**Methods:**

- `Event`
  - Raise an event for an `EventHandler` or `EventHandler<EventArgs>` event with the substitute
as the sender and with empty `EventArgs`.
- `Event<T>(object[])`
  - Raise an event of type THandler with the provided arguments. If no arguments are provided
NSubstitute will try to provide reasonable defaults.
- `EventWith<T>`
  - Raise an event for an `EventHandler<EventArgsT>` event with the substitute as the sender
and with a default instance of TEventArgs.
- `EventWith<T>(T1)`
  - Raise an event for an `EventHandler<TEventArgs>` event with the substitute as the sender and the provided eventArgs.
- `EventWith<T>(object, T1)`
  - Raise an event for an `EventHandler<TEventArgs>` event with the provided sender and eventArgs.
- `FixParamsArrayAmbiguity(object[], Type)`
  - If delegate takes single parameter of array type, it's impossible to distinguish
whether input array represents all arguments, or the first argument only.
If we find that ambiguity might happen, we wrap user input in an extra array.


#### `Received`

**Methods:**

- `InOrder(Action)`
  - Asserts the calls to the substitutes contained in the given Action were
received by these substitutes in the same order. Calls to property getters are not included
in the assertion.
  - `calls`: Action containing calls to substitutes in the expected order


#### `Substitute`

Create a substitute for one or more types. For example: `Substitute.For<ISomeType>()`

**Methods:**

- `For(Type[], object[])`
  - Substitute for multiple interfaces or a class that implements multiple interfaces. At most one class can be specified.


Be careful when specifying a class, as all non-virtual members will actually be executed. Only virtual members
can be recorded or have return values specified.
  - `typesToProxy`: The types of interfaces or a type of class and multiple interfaces the substitute should implement.
  - `constructorArguments`: Arguments required to construct a class being substituted. Not required for interfaces or classes with default constructors.
  - returns: A substitute implementing the specified types.
- `For<T1, T2, T3>(object[])`
  - Substitute for multiple interfaces or a class that implements multiple interfaces. At most one class can be specified.
If additional interfaces are required use the `For` overload.


Be careful when specifying a class, as all non-virtual members will actually be executed. Only virtual members
can be recorded or have return values specified.
  - `constructorArguments`: Arguments required to construct a class being substituted. Not required for interfaces or classes with default constructors.
  - `<T1>`: The type of interface or class to substitute.
  - `<T2>`: An additional interface or class (maximum of one class) the substitute should implement.
  - `<T3>`: An additional interface or class (maximum of one class) the substitute should implement.
  - returns: A substitute of type T1, that also implements T2 and T3.
- `For<T1, T2>(object[])`
  - Substitute for multiple interfaces or a class that implements an interface. At most one class can be specified.


Be careful when specifying a class, as all non-virtual members will actually be executed. Only virtual members
can be recorded or have return values specified.
  - `constructorArguments`: Arguments required to construct a class being substituted. Not required for interfaces or classes with default constructors.
  - `<T1>`: The type of interface or class to substitute.
  - `<T2>`: An additional interface or class (maximum of one class) the substitute should implement.
  - returns: A substitute of type T1, that also implements T2.
- `For<T>(object[])`
  - Substitute for an interface or class.


Be careful when specifying a class, as all non-virtual members will actually be executed. Only virtual members
can be recorded or have return values specified.
  - `constructorArguments`: Arguments required to construct a class being substituted. Not required for interfaces or classes with default constructors.
  - `<T>`: The type of interface or class to substitute.
  - returns: A substitute for the interface or class.
- `ForPartsOf<T>(object[])`
  - Create a substitute for a class that behaves just like a real instance of the class, but also
records calls made to its virtual members and allows for specific members to be substituted
by using `DoNotCallBase` or by
`Returns<T>` for that member.
  - `constructorArguments`
  - `<T>`: The type to substitute for parts of. Must be a class; not a delegate or interface.
  - returns: An instance of the class that will execute real methods when called, but allows parts to be selectively
overridden via `Returns` and `When..DoNotCallBase`.
- `ForTypeForwardingTo<T1, T2>(object[])`
  - Creates a proxy for a class that implements an interface, forwarding methods and properties to an instance of the class, effectively mimicking a real instance.
Both the interface and the class must be provided as parameters.
The proxy will log calls made to the interface members and delegate them to an instance of the class. Specific members can be substituted
by using `DoNotCallBase` or by
`Returns<T>` for that member.
This extension supports sealed classes and non-virtual members, with some limitations. Since the substituted method is non-virtual, internal calls within the object will invoke the original implementation and will not be logged.
  - `constructorArguments`
  - `<TInterface>`: The interface the substitute will implement.
  - `<TClass>`: The class type implementing the interface. Must be a class; not a delegate or interface.
  - returns: An object implementing the selected interface. Calls will be forwarded to the actuall methods, but allows parts to be selectively
overridden via `Returns` and `When..DoNotCallBase`.


#### `SubstituteExtensions`

**Methods:**

- `ClearReceivedCalls<T>(T1)`
  - Forget all the calls this substitute has received.
  - remarks: Note that this will not clear any results set up for the substitute using Returns().
See `ClearSubstitute<T>` for more options with resetting
a substitute.
- `DidNotReceive<T>(T1)`
  - Checks this substitute has not received the following call.
- `DidNotReceiveWithAnyArgs<T>(T1)`
  - Checks this substitute has not received the following call with any arguments.
- `Received<T>(T1)`
  - Checks this substitute has received the following call.
- `Received<T>(T1, int)`
  - Checks this substitute has received the following call the required number of times.
- `ReceivedCalls<T>(T1)`
  - Returns the calls received by this substitute.
- `ReceivedWithAnyArgs<T>(T1)`
  - Checks this substitute has received the following call with any arguments.
- `ReceivedWithAnyArgs<T>(T1, int)`
  - Checks this substitute has received the following call with any arguments the required number of times.
- `Returns<T>(T1, Func<Core.CallInfo,T1>, Func<Core.CallInfo,T1>[])`
  - Set a return value for this call, calculated by the provided function.
  - `value`
  - `returnThis`: Function to calculate the return value
  - `returnThese`: Optionally use these functions next
- `Returns<T>(T1, T1, T1[])`
  - Set a return value for this call.
  - `value`
  - `returnThis`: Value to return
  - `returnThese`: Optionally return these values next
- `Returns<T>(Tasks.Task<T1>, Func<Core.CallInfo,T1>, Func<Core.CallInfo,T1>[])`
  - Set a return value for this call, calculated by the provided function. The value(s) to be returned will be wrapped in Tasks.
  - `value`
  - `returnThis`: Function to calculate the return value
  - `returnThese`: Optionally use these functions next
- `Returns<T>(Tasks.Task<T1>, T1, T1[])`
  - Set a return value for this call. The value(s) to be returned will be wrapped in Tasks.
  - `value`
  - `returnThis`: Value to return. Will be wrapped in a Task
  - `returnThese`: Optionally use these values next
- `Returns<T>(Tasks.ValueTask<T1>, Func<Core.CallInfo,T1>, Func<Core.CallInfo,T1>[])`
  - Set a return value for this call, calculated by the provided function. The value(s) to be returned will be wrapped in ValueTasks.
  - `value`
  - `returnThis`: Function to calculate the return value
  - `returnThese`: Optionally use these functions next
- `Returns<T>(Tasks.ValueTask<T1>, T1, T1[])`
  - Set a return value for this call. The value(s) to be returned will be wrapped in ValueTasks.
  - `value`
  - `returnThis`: Value to return. Will be wrapped in a ValueTask
  - `returnThese`: Optionally use these values next
- `ReturnsForAnyArgs<T>(T1, Func<Core.CallInfo,T1>, Func<Core.CallInfo,T1>[])`
  - Set a return value for this call made with any arguments, calculated by the provided function.
  - `value`
  - `returnThis`: Function to calculate the return value
  - `returnThese`: Optionally use these functions next
- `ReturnsForAnyArgs<T>(T1, T1, T1[])`
  - Set a return value for this call made with any arguments.
  - `value`
  - `returnThis`: Value to return
  - `returnThese`: Optionally return these values next
- `ReturnsForAnyArgs<T>(Tasks.Task<T1>, Func<Core.CallInfo,T1>, Func<Core.CallInfo,T1>[])`
  - Set a return value for this call made with any arguments, calculated by the provided function. The value(s) to be returned will be wrapped in Tasks.
  - `value`
  - `returnThis`: Function to calculate the return value
  - `returnThese`: Optionally use these functions next
- `ReturnsForAnyArgs<T>(Tasks.Task<T1>, T1, T1[])`
  - Set a return value for this call made with any arguments. The value(s) to be returned will be wrapped in Tasks.
  - `value`
  - `returnThis`: Value to return
  - `returnThese`: Optionally return these values next
- `ReturnsForAnyArgs<T>(Tasks.ValueTask<T1>, Func<Core.CallInfo,T1>, Func<Core.CallInfo,T1>[])`
  - Set a return value for this call made with any arguments, calculated by the provided function. The value(s) to be returned will be wrapped in ValueTasks.
  - `value`
  - `returnThis`: Function to calculate the return value
  - `returnThese`: Optionally use these functions next
- `ReturnsForAnyArgs<T>(Tasks.ValueTask<T1>, T1, T1[])`
  - Set a return value for this call made with any arguments. The value(s) to be returned will be wrapped in ValueTasks.
  - `value`
  - `returnThis`: Value to return
  - `returnThese`: Optionally return these values next
- `When<T1, T2>(T1, Func<T1,Tasks.ValueTask<T2>>)`
  - Perform an action when this member is called.
Must be followed by `Do` to provide the callback.
- `When<T>(T1, Action<T1>)`
  - Perform an action when this member is called.
Must be followed by `Do` to provide the callback.
- `When<T>(T1, Func<T1,Tasks.Task>)`
  - Perform an action when this member is called.
Must be followed by `Do` to provide the callback.
- `WhenForAnyArgs<T1, T2>(T1, Func<T1,Tasks.ValueTask<T2>>)`
  - Perform an action when this member is called with any arguments.
Must be followed by `Do` to provide the callback.
- `WhenForAnyArgs<T>(T1, Action<T1>)`
  - Perform an action when this member is called with any arguments.
Must be followed by `Do` to provide the callback.
- `WhenForAnyArgs<T>(T1, Func<T1,Tasks.Task>)`
  - Perform an action when this member is called with any arguments.
Must be followed by `Do` to provide the callback.


### namespace `NSubstitute.Arg`

#### `AnyType`

This type can be used with any matcher to match a generic type parameter.


#### `Compat`

Alternate version of `Arg` matchers for compatibility with pre-C#7 compilers
which do not support `ref` return types. Do not use unless you are unable to use `Arg`.

For more information see `io/help/compat-args` in the NSubstitute documentation.

**Methods:**

- `Any<T>`
  - Match any argument value compatible with type T.
This is provided for compatibility with older compilers --
if possible use `Any<T>` instead.
- `Do<T>(Action<T1>)`
  - Capture any argument compatible with type T and use it to call the useArgument function
whenever a matching call is made to the substitute.
This is provided for compatibility with older compilers --
if possible use `Do<T>` instead.
- `Do<T>(Action<object>)`
  - Capture any argument compatible with type T and use it to call the useArgument function
whenever a matching call is made to the substitute.
- `Invoke`
  - Invoke any `Action` argument whenever a matching call is made to the substitute.
This is provided for compatibility with older compilers --
if possible use `Invoke` instead.
- `Invoke<T1, T2, T3, T4>(T1, T2, T3, T4)`
  - Invoke any `Action<T1, T2, T3, T4>` argument with specified arguments whenever a matching call is made to the substitute.
This is provided for compatibility with older compilers --
if possible use `Invoke<T1, T2, T3, T4>` instead.
- `Invoke<T1, T2, T3>(T1, T2, T3)`
  - Invoke any `Action<T1, T2, T3>` argument with specified arguments whenever a matching call is made to the substitute.
This is provided for compatibility with older compilers --
if possible use `Invoke<T1, T2, T3>` instead.
- `Invoke<T1, T2>(T1, T2)`
  - Invoke any `Action<T1, T2>` argument with specified arguments whenever a matching call is made to the substitute.
This is provided for compatibility with older compilers --
if possible use `Invoke<T1, T2>` instead.
- `Invoke<T>(T1)`
  - Invoke any `Action<T>` argument with specified argument whenever a matching call is made to the substitute.
This is provided for compatibility with older compilers --
if possible use `Invoke<T>` instead.
- `InvokeDelegate<T>(object[])`
  - Invoke any TDelegate argument with specified arguments whenever a matching call is made to the substitute.
This is provided for compatibility with older compilers --
if possible use `InvokeDelegate<T>` instead.
  - `arguments`: Arguments to pass to delegate.
- `Is<T>(Expressions.Expression<Predicate<T1>>)`
  - Match argument that satisfies predicate.
If the predicate throws an exception for an argument it will be treated as non-matching.
This is provided for compatibility with older compilers --
if possible use `Is<T>` instead.
- `Is<T>(Expressions.Expression<Predicate<object>>)`
  - Match argument that satisfies predicate.
If the predicate throws an exception for an argument it will be treated as non-matching.
This is provided for compatibility with older compilers --
if possible use `Is<T>` instead.
- `Is<T>(T1)`
  - Match argument that is equal to value.
This is provided for compatibility with older compilers --
if possible use `Is<T>` instead.


### namespace `NSubstitute.Callbacks`

#### `ConfiguredCallback`

**Methods:**

- `Then(Action<Core.CallInfo>)`
  - Perform this action once in chain of called callbacks.
- `ThenKeepDoing(Action<Core.CallInfo>)`
  - Keep doing this action after the other callbacks have run.
- `ThenKeepThrowing<T>(Func<Core.CallInfo,T1>)`
  - Keep throwing this exception after the other callbacks have run.
- `ThenKeepThrowing<T>(T1)`
  - Keep throwing this exception after the other callbacks have run.
- `ThenThrow<T>(Func<Core.CallInfo,T1>)`
  - Throw exception returned by function once when called in a chain of callbacks.
  - `throwThis`: Produce the exception to throw for a CallInfo
  - `<TException>`: The type of the exception
- `ThenThrow<T>(T1)`
  - Throw this exception once when called in a chain of callbacks.
  - `exception`: The exception to throw
  - `<TException>`: The type of the exception


#### `EndCallbackChain`

**Methods:**

- `AndAlways(Action<Core.CallInfo>)`
  - Perform the given action for every call.
  - `doThis`: The action to perform for every call


### namespace `NSubstitute.ClearExtensions`

#### `ClearExtensions`

**Methods:**

- `ClearSubstitute<T>(T1, ClearOptions)`
  - Clears received calls, configured return values and/or call actions for this substitute.
  - `substitute`
  - `options`: Specifies what to clear on the substitute. Can be combined with `|` to
clear multiple aspects at once.
  - `<T>`


### namespace `NSubstitute.Compatibility`

#### `CompatArg`

Alternate version of `Arg` matchers for compatibility with pre-C#7 compilers
which do not support `ref` return types. Do not use unless you are unable to use `Arg`.

`CompatArg` provides a non-static version of `Compat`, which can make it easier
to use from an abstract base class. You can get a reference to this instance using the static
`Instance` field.

For more information see `io/help/compat-args` in the NSubstitute documentation.

**Methods:**

- `Any<T>`
  - Match any argument value compatible with type T.
This is provided for compatibility with older compilers --
if possible use `Any<T>` instead.
- `Do<T>(Action<T1>)`
  - Capture any argument compatible with type T and use it to call the useArgument function
whenever a matching call is made to the substitute.
This is provided for compatibility with older compilers --
if possible use `Do<T>` instead.
- `Do<T>(Action<object>)`
  - Capture any argument compatible with type T and use it to call the useArgument function
whenever a matching call is made to the substitute.
- `Invoke`
  - Invoke any `Action` argument whenever a matching call is made to the substitute.
This is provided for compatibility with older compilers --
if possible use `Invoke` instead.
- `Invoke<T1, T2, T3, T4>(T1, T2, T3, T4)`
  - Invoke any `Action<T1, T2, T3, T4>` argument with specified arguments whenever a matching call is made to the substitute.
This is provided for compatibility with older compilers --
if possible use `Invoke<T1, T2, T3, T4>` instead.
- `Invoke<T1, T2, T3>(T1, T2, T3)`
  - Invoke any `Action<T1, T2, T3>` argument with specified arguments whenever a matching call is made to the substitute.
This is provided for compatibility with older compilers --
if possible use `Invoke<T1, T2, T3>` instead.
- `Invoke<T1, T2>(T1, T2)`
  - Invoke any `Action<T1, T2>` argument with specified arguments whenever a matching call is made to the substitute.
This is provided for compatibility with older compilers --
if possible use `Invoke<T1, T2>` instead.
- `Invoke<T>(T1)`
  - Invoke any `Action<T>` argument with specified argument whenever a matching call is made to the substitute.
This is provided for compatibility with older compilers --
if possible use `Invoke<T>` instead.
- `InvokeDelegate<T>(object[])`
  - Invoke any TDelegate argument with specified arguments whenever a matching call is made to the substitute.
This is provided for compatibility with older compilers --
if possible use `InvokeDelegate<T>` instead.
  - `arguments`: Arguments to pass to delegate.
- `Is<T>(Expressions.Expression<Predicate<T1>>)`
  - Match argument that satisfies predicate.
If the predicate throws an exception for an argument it will be treated as non-matching.
This is provided for compatibility with older compilers --
if possible use `Is<T>` instead.
- `Is<T>(Expressions.Expression<Predicate<object>>)`
  - Match argument that satisfies predicate.
If the predicate throws an exception for an argument it will be treated as non-matching.
This is provided for compatibility with older compilers --
if possible use `Is<T>` instead.
- `Is<T>(T1)`
  - Match argument that is equal to value.
This is provided for compatibility with older compilers --
if possible use `Is<T>` instead.

**Fields:**

- `Instance`
  - Get the CompatArg instance.


### namespace `NSubstitute.Core`

#### `CallBaseConfiguration`

**Methods:**

- `Exclude(Core.ICallSpecification)`
- `Include(Core.ICallSpecification)`
- `ShouldCallBase(Core.ICall)`

**Properties:**

- `CallBaseByDefault`


#### `CallHandlerFactory`

Factory method which creates `ICallHandler` from the `ISubstituteState`.


#### `CallInfo`

**Methods:**

- `Arg<T>`
  - Gets the argument of type `T` passed to this call. This will throw if there are no arguments
of this type, or if there is more than one matching argument.
  - `<T>`: The type of the argument to retrieve
  - returns: The argument passed to the call, or throws if there is not exactly one argument of this type
- `ArgAt<T>(int)`
  - Gets the argument passed to this call at the specified zero-based position, converted to type `T`.
This will throw if there are no arguments, if the argument is out of range or if it
cannot be converted to the specified type.
  - `position`: The zero-based position of the argument to retrieve
  - `<T>`: The type of the argument to retrieve
  - returns: The argument passed to the call, or throws if there is not exactly one argument of this type
- `ArgTypes`
  - Gets the types of all the arguments passed to this call.
  - returns: Array of types of all arguments passed to this call
- `Args`
  - Get the arguments passed to this call.
  - returns: Array of all arguments passed to this call

**Properties:**

- `Item`
  - Gets the nth argument to this call.
  - `index`: Index of argument
  - returns: The value of the argument at the given index


#### `ConfiguredCall`

**Methods:**

- `AndDoes(Action<Core.CallInfo>)`
  - Adds a callback to execute for matching calls.
  - `action`: an action to call


#### `Extensions`

**Methods:**

- `AsArray<T>(Generic.IEnumerable<T1>)`
  - Tries to cast sequence to array first before making a new array sequence.
- `IsCompatibleWith(object, Type)`
  - Checks if the instance can be used when a type is expected.
- `Join(Generic.IEnumerable<string>, string)`
  - Join the strings using separator.


#### `ICallBaseConfiguration`

**Methods:**

- `Exclude(Core.ICallSpecification)`
  - Specifies whether base method should be always ignored for the matching call.
If method is both explicitly excluded and included, base method is _not_ called.
- `Include(Core.ICallSpecification)`
  - Specifies whether base method should be called for the matching call.
If method is both explicitly excluded and included, base method is _not_ called.
- `ShouldCallBase(Core.ICall)`
  - Tests whether base method should be called for the call given the existing configuration.

**Properties:**

- `CallBaseByDefault`
  - Gets or sets whether base method should be called by default.


#### `ICallIndependentReturn`

Performance optimization. Allows to not construct `CallInfo` if configured result doesn't depend on it.


#### `ICallRouter`

**Properties:**

- `CallBaseByDefault`
  - Specifies whether base method should be called by default.
  - remarks: This configuration is considered only when base method exists (e.g. you created a substitute for
the AbstractType with method implementation).


#### `IDescribeNonMatches`

**Methods:**

- `DescribeFor(object)`
  - Describes how the argument does not match the condition specified by this class, or `Empty`
if a detailed description can not be provided for the argument.
  - `argument`
  - returns: Description of the non-match, or `Empty` if no description can be provided.


#### `ISubstitutionContext`

**Properties:**

- `ThreadContext`
  - A thread bound state of the NSubstitute context. Usually this API is used to provide the fluent
features of the NSubstitute.


#### `IThreadLocalContext`

**Methods:**

- `RunInQueryContext(Action, Core.IQuery)`
  - Invokes the passed callback in a context of the specified query.
- `SetNextRoute(Core.ICallRouter, Func<Core.ISubstituteState,Routing.IRoute>)`
  - Sets the route to use for the next call dispatch on the current thread for the specified callRouter.
- `UseNextRoute(Core.ICallRouter)`
  - Returns the previously configured next route and resets the stored value.
If route was configured for the different router, returns and persist the route info.
- `UsePendingRaisingEventArgumentsFactory`
  - Returns the previously set arguments factory and resets the stored value.


#### `Maybe<T>`

Particularly poor implementation of Maybe/Option type.
This is just filling an immediate need; use FSharpOption or XSharpx or similar for a
real implementation.


#### `RobustThreadLocal<T>`

Delegates to ThreadLocal<T>, but wraps Value property access in try/catch to swallow ObjectDisposedExceptions.
These can occur if the Value property is accessed from the finalizer thread. Because we can't detect this, we'll
just swallow the exception (the finalizer thread won't be using any of the values from thread local storage anyway).


#### `SubstituteFactory`

**Methods:**

- `Create(Type[], object[])`
  - Create a substitute for the given types.
  - `typesToProxy`
  - `constructorArguments`
- `CreatePartial(Type[], object[])`
  - Create an instance of the given types, with calls configured to call the base implementation
where possible. Parts of the instance can be substituted using
`Returns<T>`.
  - `typesToProxy`
  - `constructorArguments`


#### `WhenCalled<T>`

**Methods:**

- `CallBase`
  - Call the base implementation of future calls. For use with non-partial class substitutes.
- `Do(Action<Core.CallInfo>)`
  - Perform this action when called.
  - `callbackWithArguments`
- `Do(Callback)`
  - Perform this configured callback when called.
  - `callback`
- `DoNotCallBase`
  - Do not call the base implementation on future calls. For use with partial substitutes.
- `Throw(Exception)`
  - Throw the specified exception when called.
- `Throw(Func<Core.CallInfo,Exception>)`
  - Throw an exception generated by the specified function when called.
- `Throw<T>`
  - Throw an exception of the given type when called.
- `Throws(Exception)`
  - Throws the specified exception when called.
- `Throws(Func<Core.CallInfo,Exception>)`
  - Throws an exception generated by the specified function when called.
- `Throws<T>`
  - Throws an exception of the given type when called.


### namespace `NSubstitute.Core.Arguments`

#### `ArgumentMatcher`

**Methods:**

- `Enqueue<T>(Core.Arguments.IArgumentMatcher<T1>)`
  - Enqueues a matcher for the method argument in current position and returns the value which should be
passed back to the method you invoke.


#### `IArgumentMatcher`

Provides a specification for arguments for use with .
Can additionally implement `IDescribeNonMatches` to give descriptions when arguments do not match.

**Methods:**

- `IsSatisfiedBy(object)`
  - Checks whether the argument satisfies the condition of the matcher.
If this throws an exception the argument will be treated as non-matching.


#### `IArgumentMatcher<T>`

Provides a specification for arguments for use with .
Can additionally implement to give descriptions when arguments do not match.

**Methods:**

- `IsSatisfiedBy(T1)`
  - Checks whether the argument satisfies the condition of the matcher.
If this throws an exception the argument will be treated as non-matching.


### namespace `NSubstitute.Core.CallCollection`

#### `IReceivedCallEntry`

Performance optimization. Allows to mark call as deleted without allocating extra wrapper.
To play safely, we track ownership, so object can be re-used only once.


#### `ReceivedCallEntry`

Wrapper to track that particular entry was deleted.
That is needed because concurrent collections don't have a Delete method.
Notice, in most cases the original `Call` instance will be used as a wrapper itself.

**Methods:**

- `#ctor(Core.ICall)`
  - Wrapper to track that particular entry was deleted.
That is needed because concurrent collections don't have a Delete method.
Notice, in most cases the original `Call` instance will be used as a wrapper itself.


### namespace `NSubstitute.Core.DependencyInjection`

#### `IConfigurableNSubContainer`

**Methods:**

- `Decorate<T>(Func<T1,Core.DependencyInjection.INSubResolver,T1>)`
  - Decorates the original implementation with a custom decorator.
The factory method is provided with an original implementation instance.
The lifetime of decorated implementation is used.


#### `INSubContainer`

**Methods:**

- `CreateScope`
  - Create an explicit scope, so all dependencies with the `PerScope` lifetime
are preserved for multiple resolve requests.
- `Customize`
  - Creates a new container based on the current one,
which can be configured to override the existing registrations without affecting the existing container.


#### `NSubContainer`

Tiny and very limited implementation of the DI services.
Container supports the following features required by NSubstitute:
- Registration by type with automatic constructor injection
- Registration of factory methods for the complex objects
- Support of the most required lifetimes:
- `Transient`
- `PerScope`
- `Singleton`
- Immutability (via interfaces) and customization by creating a nested container


#### `NSubLifetime`

**Fields:**

- `PerScope`
  - Value is created only once per scope. Allows to share the same instance across the objects in the same graph.
If no explicit scope is created, an implicit scope is created per single resolve request.
- `Singleton`
  - Value is created only once.
- `Transient`
  - New value is created for each time.


#### `NSubstituteDefaultFactory`

**Properties:**

- `DefaultContainer`
  - The default NSubstitute registrations. Feel free to configure the existing container to customize
and override NSubstitute parts.


### namespace `NSubstitute.ExceptionExtensions`

#### `ExceptionExtensions`

**Methods:**

- `Throws(object, Exception)`
  - Throw an exception for this call.
  - `value`
  - `ex`: Exception to throw
- `Throws(object, Func<Core.CallInfo,Exception>)`
  - Throw an exception for this call, as generated by the specified function.
  - `value`
  - `createException`: Func creating exception object
- `Throws<T>(object)`
  - Throw an exception of the given type for this call.
  - `value`
  - `<TException>`: Type of exception to throw
- `ThrowsAsync(Tasks.Task, Exception)`
  - Throw an exception for this call.
  - `value`
  - `ex`: Exception to throw
- `ThrowsAsync(Tasks.Task, Func<Core.CallInfo,Exception>)`
  - Throw an exception for this call, as generated by the specified function.
  - `value`
  - `createException`: Func creating exception object
- `ThrowsAsync<T>(Tasks.Task)`
  - Throw an exception of the given type for this call.
  - `value`
  - `<TException>`: Type of exception to throw
- `ThrowsAsync<T>(Tasks.Task<T1>, Exception)`
  - Throw an exception for this call.
  - `value`
  - `ex`: Exception to throw
- `ThrowsAsync<T>(Tasks.Task<T1>, Func<Core.CallInfo,Exception>)`
  - Throw an exception for this call, as generated by the specified function.
  - `value`
  - `createException`: Func creating exception object
- `ThrowsAsyncForAnyArgs(Tasks.Task, Exception)`
  - Throw an exception for this call made with any arguments.
  - `value`
  - `ex`: Exception to throw
- `ThrowsAsyncForAnyArgs(Tasks.Task, Func<Core.CallInfo,Exception>)`
  - Throws an exception for this call made with any arguments, as generated by the specified function.
  - `value`
  - `createException`: Func creating exception object
- `ThrowsAsyncForAnyArgs<T>(Tasks.Task)`
  - Throws an exception of the given type for this call made with any arguments.
  - `value`
  - `<TException>`: Type of exception to throw
- `ThrowsAsyncForAnyArgs<T>(Tasks.Task<T1>, Exception)`
  - Throw an exception for this call made with any arguments.
  - `value`
  - `ex`: Exception to throw
- `ThrowsAsyncForAnyArgs<T>(Tasks.Task<T1>, Func<Core.CallInfo,Exception>)`
  - Throws an exception for this call made with any arguments, as generated by the specified function.
  - `value`
  - `createException`: Func creating exception object
- `ThrowsForAnyArgs(object, Exception)`
  - Throw an exception for this call made with any arguments.
  - `value`
  - `ex`: Exception to throw
- `ThrowsForAnyArgs(object, Func<Core.CallInfo,Exception>)`
  - Throws an exception for this call made with any arguments, as generated by the specified function.
  - `value`
  - `createException`: Func creating exception object
- `ThrowsForAnyArgs<T>(object)`
  - Throws an exception of the given type for this call made with any arguments.
  - `value`
  - `<TException>`: Type of exception to throw


### namespace `NSubstitute.Extensions`

#### `ConfigurationExtensions`

**Methods:**

- `Configure<T>(T1)`
  - A hint for the NSubstitute that the subsequent method/property call is about to be configured.
For example: substitute.Configure().GetValue().Returns(1,2,3);


NOTICE, you _don't need_ to invoke this method for the basic configuration scenarios.
Ensure you don't overuse this method and it is applied only if strictly required.
Due to the NSubstitute configuration syntax it is often impossible to recognise during the method call
dispatch whether this is a setup phase or a regular method call.
Usually it doesn't matter, however sometimes method invocation could lead to undesired side effects
(e.g. the previously configured value is returned, base method is invoked). In that case you might want to
provide NSubstitute with a hint that you are configuring a method, so it handles the call in configuration mode.


#### `ReturnsForAllExtensions`

**Methods:**

- `ReturnsForAll<T>(object, Func<Core.CallInfo,T1>)`
  - Configure default return value for all methods that return the specified type, calculated by a function
  - `substitute`
  - `returnThis`
  - `<T>`
- `ReturnsForAll<T>(object, T1)`
  - Configure default return value for all methods that return the specified type
  - `substitute`
  - `returnThis`
  - `<T>`


### namespace `NSubstitute.Proxies.CastleDynamicProxy`

#### `CastleForwardingInterceptor`

**Methods:**

- `SwitchToFullDispatchMode`
  - Switches interceptor to dispatch calls via the full pipeline.


### namespace `NSubstitute.ReceivedExtensions`

#### `Quantity`

Represents a quantity. Primarily used for specifying a required amount of calls to a member.

**Methods:**

- `Describe(string, string)`
  - Describe this quantity using the given noun variants.
For example, `Describe("item", "items")` could return the description:
"more than 1 item, but less than 10 items".
  - `singularNoun`
  - `pluralNoun`
  - returns: A string describing the required quantity of items identified by the provided noun forms.
- `Matches<T>(Generic.IEnumerable<T1>)`
  - Returns whether the given collection contains the required quantity of items.
  - `items`
  - `<T>`
  - returns: true if the collection has the required quantity; otherwise false.
- `RequiresMoreThan<T>(Generic.IEnumerable<T1>)`
  - Returns whether the given collections needs more items to satisfy the required quantity.
  - `items`
  - `<T>`
  - returns: true if the collection needs more items to match this quantity; otherwise false.
- `Within(int, int)`
  - A non-zero quantity between the given minimum and maximum numbers (inclusive).
  - `minInclusive`: Minimum quantity (inclusive). Must be greater than or equal to 0.
  - `maxInclusive`: Maximum quantity (inclusive). Must be greater than minInclusive.


#### `ReceivedExtensions`

**Methods:**

- `Received<T>(T1, ReceivedExtensions.Quantity)`
  - Checks this substitute has received the following call the required number of times.
  - `substitute`
  - `requiredQuantity`
  - `<T>`
- `ReceivedWithAnyArgs<T>(T1, ReceivedExtensions.Quantity)`
  - Checks this substitute has received the following call with any arguments the required number of times.
  - `substitute`
  - `requiredQuantity`
  - `<T>`


### namespace `NSubstitute.ReturnsExtensions`

#### `ReturnsExtensions`

**Methods:**

- `ReturnsNull<T>(Nullable<T1>)`
  - Set null as returned value for this call.
- `ReturnsNull<T>(T1)`
  - Set null as returned value for this call.
- `ReturnsNull<T>(Tasks.Task<Nullable<T1>>)`
  - Set null as returned value for this call.
- `ReturnsNull<T>(Tasks.Task<T1>)`
  - Set null as returned value for this call.
- `ReturnsNull<T>(Tasks.ValueTask<Nullable<T1>>)`
  - Set null as returned value for this call.
- `ReturnsNull<T>(Tasks.ValueTask<T1>)`
  - Set null as returned value for this call.
- `ReturnsNullForAnyArgs<T>(Nullable<T1>)`
  - Set null as returned value for this call made with any arguments.
- `ReturnsNullForAnyArgs<T>(T1)`
  - Set null as returned value for this call made with any arguments.
- `ReturnsNullForAnyArgs<T>(Tasks.Task<Nullable<T1>>)`
  - Set null as returned value for this call made with any arguments.
- `ReturnsNullForAnyArgs<T>(Tasks.Task<T1>)`
  - Set null as returned value for this call made with any arguments.
- `ReturnsNullForAnyArgs<T>(Tasks.ValueTask<Nullable<T1>>)`
  - Set null as returned value for this call made with any arguments.
- `ReturnsNullForAnyArgs<T>(Tasks.ValueTask<T1>)`
  - Set null as returned value for this call made with any arguments.
  - `value`
  - `<T>`


### namespace `NSubstitute.Routing.Handlers`

#### `ClearLastCallRouterHandler`

Clears last call router on SubstitutionContext for routes that do not require it.

**Methods:**

- `#ctor(Core.IThreadLocalContext)`
  - Clears last call router on SubstitutionContext for routes that do not require it.
  - remarks: This is to help prevent static state bleeding over into future calls.


### namespace `System.Diagnostics.CodeAnalysis`

#### `AllowNullAttribute`

Specifies that null is allowed as an input even if the corresponding type disallows it.


#### `DisallowNullAttribute`

Specifies that null is disallowed as an input even if the corresponding type allows it.


#### `DoesNotReturnAttribute`

Applied to a method that will never return under any circumstance.


#### `DoesNotReturnIfAttribute`

Specifies that the method will not return if the associated Boolean parameter is passed the specified value.

**Methods:**

- `#ctor(bool)`
  - Specifies that the method will not return if the associated Boolean parameter is passed the specified value.
  - `parameterValue`: The condition parameter value. Code after the method will be considered unreachable by diagnostics if the argument to
the associated parameter matches this value.
  - remarks: Initializes the attribute with the specified parameter value.

**Properties:**

- `ParameterValue`
  - Gets the condition parameter value.


#### `MaybeNullAttribute`

Specifies that an output may be null even if the corresponding type disallows it.


#### `MaybeNullWhenAttribute`

Specifies that when a method returns `ReturnValue`, the parameter may be null even if the corresponding type disallows it.

**Methods:**

- `#ctor(bool)`
  - Specifies that when a method returns `ReturnValue`, the parameter may be null even if the corresponding type disallows it.
  - `returnValue`: The return value condition. If the method returns this value, the associated parameter may be null.
  - remarks: Initializes the attribute with the specified return value condition.

**Properties:**

- `ReturnValue`
  - Gets the return value condition.


#### `MemberNotNullAttribute`

Specifies that the method or property will ensure that the listed field and property members have not-null values.

**Methods:**

- `#ctor(string)`
  - Initializes the attribute with a field or property member.
  - `member`: The field or property member that is promised to be not-null.
- `#ctor(string[])`
  - Initializes the attribute with the list of field and property members.
  - `members`: The list of field and property members that are promised to be not-null.

**Properties:**

- `Members`
  - Gets field or property member names.


#### `MemberNotNullWhenAttribute`

Specifies that the method or property will ensure that the listed field and property members have not-null values when returning with the specified return value condition.

**Methods:**

- `#ctor(bool, string)`
  - Initializes the attribute with the specified return value condition and a field or property member.
  - `returnValue`: The return value condition. If the method returns this value, the associated parameter will not be null.
  - `member`: The field or property member that is promised to be not-null.
- `#ctor(bool, string[])`
  - Initializes the attribute with the specified return value condition and list of field and property members.
  - `returnValue`: The return value condition. If the method returns this value, the associated parameter will not be null.
  - `members`: The list of field and property members that are promised to be not-null.

**Properties:**

- `Members`
  - Gets field or property member names.
- `ReturnValue`
  - Gets the return value condition.


#### `NotNullAttribute`

Specifies that an output will not be null even if the corresponding type allows it.


#### `NotNullIfNotNullAttribute`

Specifies that the output will be non-null if the named parameter is non-null.

**Methods:**

- `#ctor(string)`
  - Specifies that the output will be non-null if the named parameter is non-null.
  - `parameterName`: The associated parameter name. The output will be non-null if the argument to the parameter specified is non-null.
  - remarks: Initializes the attribute with the associated parameter name.

**Properties:**

- `ParameterName`
  - Gets the associated parameter name.


#### `NotNullWhenAttribute`

Specifies that when a method returns `ReturnValue`, the parameter will not be null even if the corresponding type allows it.

**Methods:**

- `#ctor(bool)`
  - Specifies that when a method returns `ReturnValue`, the parameter will not be null even if the corresponding type allows it.
  - `returnValue`: The return value condition. If the method returns this value, the associated parameter will not be null.
  - remarks: Initializes the attribute with the specified return value condition.

**Properties:**

- `ReturnValue`
  - Gets the return value condition.
