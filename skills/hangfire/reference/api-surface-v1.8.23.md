# Hangfire.Core v1.8.23 — API surface

_Generated from the XML doc comments shipped inside these NuGet packages:_

- `Hangfire.Core` v1.8.23 (`netstandard2.0+source`)
- `Hangfire.SqlServer` v1.8.23 (`netstandard2.0+source`)
- `Hangfire.AspNetCore` v1.8.23 (`netstandard2.0+source`)
- `Hangfire.NetCore` v1.8.23 (`netstandard2.0+source`)

_Do not edit by hand — rerun `scripts/update_skill.py`._

Use **only** the members listed here when writing code against Hangfire.Core v1.8.23. If a member you want isn't here, it doesn't exist in this version and you must pick another approach.

## package `Hangfire.Core` v1.8.23

### namespace `Hangfire`

#### `AppBuilderExtensions`

**Methods:**

- `UseHangfireDashboard([NotNull] this IAppBuilder)`
- `UseHangfireDashboard([NotNull] this IAppBuilder, [NotNull] string)`
- `UseHangfireDashboard([NotNull] this IAppBuilder, [NotNull] string, [NotNull] DashboardOptions)`
- `UseHangfireDashboard([NotNull] this IAppBuilder, [NotNull] string, [NotNull] DashboardOptions, [NotNull] JobStorage)`
- `UseHangfireDashboard([NotNull] this IAppBuilder, [NotNull] string, [NotNull] DashboardOptions, [NotNull] JobStorage, [CanBeNull] IOwinDashboardAntiforgery)`
- `UseHangfireServer([NotNull] this IAppBuilder)`
- `UseHangfireServer([NotNull] this IAppBuilder, [NotNull] BackgroundJobServerOptions)`
- `UseHangfireServer([NotNull] this IAppBuilder, [NotNull] BackgroundJobServerOptions, [NotNull] JobStorage)`
- `UseHangfireServer([NotNull] this IAppBuilder, [NotNull] BackgroundJobServerOptions, [NotNull] params IBackgroundProcess[])`
- `UseHangfireServer([NotNull] this IAppBuilder, [NotNull] IBackgroundProcessingServer)`
- `UseHangfireServer([NotNull] this IAppBuilder, [NotNull] JobStorage, [NotNull] BackgroundJobServerOptions, [NotNull] params IBackgroundProcess[])`
- `UseHangfireServer([NotNull] this IAppBuilder, [NotNull] params IBackgroundProcess[])`


#### `AttemptsExceededAction`

Specifies a candidate state for a background job that will be chosen
by the `AutomaticRetryAttribute` filter after exceeding
the number of retry attempts.

**Fields:**

- `Delete`
  - Background job will be moved to the `DeletedState`.
- `Fail`
  - Background job will be moved to the `FailedState`.


#### `AutomaticRetryAttribute`

Represents a job filter that performs automatic retries for
background jobs whose processing was failed due to an exception, with
a limited number of attempts.

**Methods:**

- `#ctor`
  - Initializes a new instance of the `AutomaticRetryAttribute`
class with `DefaultRetryAttempts` number.
- `OnStateApplied(ApplyStateContext, IWriteOnlyTransaction)`
- `OnStateApplied(Hangfire.States.ApplyStateContext, Hangfire.Storage.IWriteOnlyTransaction)`
- `OnStateElection(ElectStateContext)`
- `OnStateElection(Hangfire.States.ElectStateContext)`
- `OnStateUnapplied(ApplyStateContext, IWriteOnlyTransaction)`
- `OnStateUnapplied(Hangfire.States.ApplyStateContext, Hangfire.Storage.IWriteOnlyTransaction)`
- `ScheduleAgainLater(Hangfire.States.ElectStateContext, int, Hangfire.States.FailedState)`
  - Schedules the job to run again later. See `DelayInSecondsByAttemptFunc`.
  - `context`: The state context.
  - `retryAttempt`: The count of retry attempts made so far.
  - `failedState`: Object which contains details about the current failed state.
- `TransitionToDeleted(Hangfire.States.ElectStateContext, Hangfire.States.FailedState)`
  - Transition the candidate state to the deleted state.
  - `context`: The state context.
  - `failedState`: Object which contains details about the current failed state.

**Properties:**

- `Attempts`
  - Gets or sets the maximum number of automatic retry attempts.
- `DelayInSecondsByAttemptFunc`
  - Gets or sets a function using to get a delay by an attempt number.
- `DelaysInSeconds`
  - Gets or sets the delays between attempts.
- `ExceptOn`
  - Gets or sets the array of exception types on which the automatic retry mechanism
should not be applied.
- `LogEvents`
  - Gets or sets whether to produce log messages on retry attempts.
- `OnAttemptsExceeded`
  - Gets or sets a candidate state for a background job that
will be chosen when number of retry attempts exceeded.
- `OnlyOn`
  - Gets a sets an array of exception types that will be used to determine whether
automatic retry logic should be attempted to run. By default it will be run on
any exception, but this property allow to reduce it only to some specific
exception types and their subtypes.

**Fields:**

- `DefaultRetryAttempts`
  - Represents the default number of retry attempts. This field is read-only.
  - remarks: The value of this field is `10`.


#### `BackgroundJob`

Provides static methods for creating fire-and-forget, delayed
jobs and continuations as well as re-queue and delete existing
background jobs.

**Methods:**

- `#ctor(string, Hangfire.Common.Job, DateTime)`
- `#ctor(string, Hangfire.Common.Job, DateTime, Generic.IReadOnlyDictionary<string,string>)`
- `ContinueJobWith([NotNull] string, [NotNull, InstantHandle] Expression<Action>)`
- `ContinueJobWith([NotNull] string, [NotNull, InstantHandle] Expression<Action>, JobContinuationOptions)`
- `ContinueJobWith([NotNull] string, [NotNull, InstantHandle] Expression<Func<Task>>, JobContinuationOptions)`
- `ContinueJobWith([NotNull] string, [NotNull] string, [NotNull, InstantHandle] Expression<Action>, JobContinuationOptions)`
- `ContinueJobWith([NotNull] string, [NotNull] string, [NotNull, InstantHandle] Expression<Func<Task>>, JobContinuationOptions)`
- `ContinueJobWith(string, Expressions.Expression<Action>)`
  - Creates a new background job that will wait for a successful completion
of another background job to be enqueued.
  - `parentId`: Identifier of a background job to wait completion for.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - returns: Unique identifier of a created job.
- `ContinueJobWith(string, Expressions.Expression<Action>, Hangfire.JobContinuationOptions)`
  - Creates a new background job that will wait for another background job to be enqueued.
  - `parentId`: Identifier of a background job to wait completion for.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - `options`: Continuation options.
  - returns: Unique identifier of a created job.
- `ContinueJobWith(string, Expressions.Expression<Func<Tasks.Task>>, Hangfire.JobContinuationOptions)`
  - Creates a new background job that will wait for another background job to be enqueued.
  - `parentId`: Identifier of a background job to wait completion for.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - `options`: Continuation options. By default,
`OnlyOnSucceededState` is used.
  - returns: Unique identifier of a created job.
- `ContinueJobWith(string, string, Expressions.Expression<Action>, Hangfire.JobContinuationOptions)`
  - Creates a new background job that will wait for another background job to be enqueued to the
specified queue.
  - `parentId`: Identifier of a background job to wait completion for.
  - `queue`: Default queue for the continuation.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - `options`: Continuation options.
  - returns: Unique identifier of a created job.
- `ContinueJobWith(string, string, Expressions.Expression<Func<Tasks.Task>>, Hangfire.JobContinuationOptions)`
  - Creates a new background job that will wait for another background job to be enqueued to the
specified queue.
  - `parentId`: Identifier of a background job to wait completion for.
  - `queue`: Default queue for the continuation.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - `options`: Continuation options. By default,
`OnlyOnSucceededState` is used.
  - returns: Unique identifier of a created job.
- `ContinueJobWith<T>([NotNull] string, [NotNull, InstantHandle] Expression<Action<T>>)`
- `ContinueJobWith<T>([NotNull] string, [NotNull, InstantHandle] Expression<Action<T>>, JobContinuationOptions)`
- `ContinueJobWith<T>([NotNull] string, [NotNull, InstantHandle] Expression<Func<T, Task>>, JobContinuationOptions)`
- `ContinueJobWith<T>([NotNull] string, [NotNull] string, [NotNull, InstantHandle] Expression<Action<T>>, JobContinuationOptions)`
- `ContinueJobWith<T>([NotNull] string, [NotNull] string, [NotNull, InstantHandle] Expression<Func<T, Task>>, JobContinuationOptions)`
- `ContinueJobWith<T>(string, Expressions.Expression<Action<T1>>)`
  - Creates a new background job that will wait for a successful completion
of another background job to be enqueued.
  - `parentId`: Identifier of a background job to wait completion for.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - returns: Unique identifier of a created job.
- `ContinueJobWith<T>(string, Expressions.Expression<Action<T1>>, Hangfire.JobContinuationOptions)`
  - Creates a new background job that will wait for another background job to be enqueued.
  - `parentId`: Identifier of a background job to wait completion for.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - `options`: Continuation options.
  - returns: Unique identifier of a created job.
- `ContinueJobWith<T>(string, Expressions.Expression<Func<T1,Tasks.Task>>, Hangfire.JobContinuationOptions)`
  - Creates a new background job that will wait for another background job to be enqueued.
  - `parentId`: Identifier of a background job to wait completion for.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - `options`: Continuation options. By default,
`OnlyOnSucceededState` is used.
  - returns: Unique identifier of a created job.
- `ContinueJobWith<T>(string, string, Expressions.Expression<Action<T1>>, Hangfire.JobContinuationOptions)`
  - Creates a new background job that will wait for another background job to be enqueued to the
specified queue.
  - `parentId`: Identifier of a background job to wait completion for.
  - `queue`: Default queue for the continuation.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - `options`: Continuation options.
  - returns: Unique identifier of a created job.
- `ContinueJobWith<T>(string, string, Expressions.Expression<Func<T1,Tasks.Task>>, Hangfire.JobContinuationOptions)`
  - Creates a new background job that will wait for another background job to be enqueued to the
specified queue.
  - `parentId`: Identifier of a background job to wait completion for.
  - `queue`: Default queue for the continuation.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - `options`: Continuation options. By default,
`OnlyOnSucceededState` is used.
  - returns: Unique identifier of a created job.
- `ContinueWith([NotNull] string, [NotNull, InstantHandle] Expression<Action>)`
- `ContinueWith([NotNull] string, [NotNull, InstantHandle] Expression<Action>, JobContinuationOptions)`
- `ContinueWith([NotNull] string, [NotNull, InstantHandle] Expression<Func<Task>>, JobContinuationOptions)`
- `ContinueWith(string, Expressions.Expression<Action>)`
  - Creates a new background job that will wait for a successful completion
of another background job to be enqueued.
  - `parentId`: Identifier of a background job to wait completion for.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - returns: Unique identifier of a created job.
- `ContinueWith(string, Expressions.Expression<Action>, Hangfire.JobContinuationOptions)`
  - Creates a new background job that will wait for another background job to be enqueued.
  - `parentId`: Identifier of a background job to wait completion for.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - `options`: Continuation options.
  - returns: Unique identifier of a created job.
- `ContinueWith(string, Expressions.Expression<Func<Tasks.Task>>, Hangfire.JobContinuationOptions)`
  - Creates a new background job that will wait for another background job to be enqueued.
  - `parentId`: Identifier of a background job to wait completion for.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - `options`: Continuation options. By default,
`OnlyOnSucceededState` is used.
  - returns: Unique identifier of a created job.
- `ContinueWith<T>([NotNull] string, [NotNull, InstantHandle] Expression<Action<T>>)`
- `ContinueWith<T>([NotNull] string, [NotNull, InstantHandle] Expression<Action<T>>, JobContinuationOptions)`
- `ContinueWith<T>([NotNull] string, [NotNull, InstantHandle] Expression<Func<T, Task>>, JobContinuationOptions)`
- `ContinueWith<T>(string, Expressions.Expression<Action<T1>>)`
  - Creates a new background job that will wait for a successful completion
of another background job to be enqueued.
  - `parentId`: Identifier of a background job to wait completion for.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - returns: Unique identifier of a created job.
- `ContinueWith<T>(string, Expressions.Expression<Action<T1>>, Hangfire.JobContinuationOptions)`
  - Creates a new background job that will wait for another background job to be enqueued.
  - `parentId`: Identifier of a background job to wait completion for.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - `options`: Continuation options.
  - returns: Unique identifier of a created job.
- `ContinueWith<T>(string, Expressions.Expression<Func<T1,Tasks.Task>>, Hangfire.JobContinuationOptions)`
  - Creates a new background job that will wait for another background job to be enqueued.
  - `parentId`: Identifier of a background job to wait completion for.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - `options`: Continuation options. By default,
`OnlyOnSucceededState` is used.
  - returns: Unique identifier of a created job.
- `Delete([NotNull] string)`
- `Delete([NotNull] string, [CanBeNull] string)`
- `Delete(string)`
  - Changes state of a job with the specified jobId
to the `DeletedState`.
`Delete`
  - `jobId`: An identifier, that will be used to find a job.
  - returns: True on a successful state transition, false otherwise.
- `Delete(string, string)`
  - Changes state of a job with the specified jobId
to the `DeletedState`. State change is only performed
if current job state is equal to the fromState value.
`Delete`
  - `jobId`: Identifier of job, whose state is being changed.
  - `fromState`: Current state assertion, or null if unneeded.
  - returns: True, if state change succeeded, otherwise false.
- `Enqueue(Expressions.Expression<Action>)`
  - Creates a new fire-and-forget job based on a given method call expression.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - returns: Unique identifier of a background job.
- `Enqueue(Expressions.Expression<Func<Tasks.Task>>)`
  - Creates a new fire-and-forget job based on a given method call expression.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - returns: Unique identifier of a background job.
- `Enqueue([NotNull, InstantHandle] Expression<Action>)`
- `Enqueue([NotNull, InstantHandle] Expression<Func<Task>>)`
- `Enqueue([NotNull] string, [NotNull, InstantHandle] Expression<Action>)`
- `Enqueue([NotNull] string, [NotNull, InstantHandle] Expression<Func<Task>>)`
- `Enqueue(string, Expressions.Expression<Action>)`
  - Creates a new fire-and-forget job based on a given method call expression and places it
to the specified queue.
  - `queue`: Default queue for the background job.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - returns: Unique identifier of a background job.
- `Enqueue(string, Expressions.Expression<Func<Tasks.Task>>)`
  - Creates a new fire-and-forget job based on a given method call expression and places it
to the specified queue.
  - `queue`: Default queue for the background job.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - returns: Unique identifier of a background job.
- `Enqueue<T>(Expressions.Expression<Action<T1>>)`
  - Creates a new fire-and-forget job based on a given method call expression.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - returns: Unique identifier of a background job.
- `Enqueue<T>(Expressions.Expression<Func<T1,Tasks.Task>>)`
  - Creates a new fire-and-forget job based on a given method call expression.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - returns: Unique identifier of a background job.
- `Enqueue<T>([NotNull, InstantHandle] Expression<Action<T>>)`
- `Enqueue<T>([NotNull, InstantHandle] Expression<Func<T, Task>>)`
- `Enqueue<T>([NotNull] string, [NotNull, InstantHandle] Expression<Action<T>>)`
- `Enqueue<T>([NotNull] string, [NotNull, InstantHandle] Expression<Func<T, Task>>)`
- `Enqueue<T>(string, Expressions.Expression<Action<T1>>)`
  - Creates a new fire-and-forget job based on a given method call expression and places it
to the specified queue.
  - `queue`: Default queue for the background job.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - returns: Unique identifier of a background job.
- `Enqueue<T>(string, Expressions.Expression<Func<T1,Tasks.Task>>)`
  - Creates a new fire-and-forget job based on a given method call expression and places it
to the specified queue.
  - `queue`: Default queue for the background job.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - returns: Unique identifier of a background job.
- `Requeue([NotNull] string)`
- `Requeue([NotNull] string, [CanBeNull] string)`
- `Requeue(string)`
  - Changes state of a job with the specified jobId
to the `EnqueuedState`.
  - `jobId`: Identifier of job, whose state is being changed.
  - returns: True, if state change succeeded, otherwise false.
- `Requeue(string, string)`
  - Changes state of a job with the specified jobId
to the `EnqueuedState`. If fromState value
is not null, state change will be performed only if the current state name
of a job equal to the given value.
  - `jobId`: Identifier of job, whose state is being changed.
  - `fromState`: Current state assertion, or null if unneeded.
  - returns: True, if state change succeeded, otherwise false.
- `Reschedule([NotNull] string, DateTimeOffset)`
- `Reschedule([NotNull] string, DateTimeOffset, [CanBeNull] string)`
- `Reschedule([NotNull] string, TimeSpan)`
- `Reschedule([NotNull] string, TimeSpan, [CanBeNull] string)`
- `Reschedule(string, DateTimeOffset)`
  - Changes state of a job with the specified jobId
to the `ScheduledState`.
  - `jobId`: Identifier of job, whose state is being changed.
  - `enqueueAt`: The moment of time at which the job will be rescheduled.
  - returns: True, if state change succeeded, otherwise false.
- `Reschedule(string, DateTimeOffset, string)`
  - Changes state of a job with the specified jobId
to the `ScheduledState`. If fromState value
is not null, state change will be performed only if the current state name
of a job equal to the given value.
  - `jobId`: Identifier of job, whose state is being changed.
  - `enqueueAt`: The moment of time at which the job will be rescheduled.
  - `fromState`: Current state assertion, or null if unneeded.
  - returns: True, if state change succeeded, otherwise false.
- `Reschedule(string, TimeSpan)`
  - Changes state of a job with the specified jobId
to the `ScheduledState`.
  - `jobId`: Identifier of job, whose state is being changed.
  - `delay`: Delay, after which the job will be scheduled.
  - returns: True, if state change succeeded, otherwise false.
- `Reschedule(string, TimeSpan, string)`
  - Changes state of a job with the specified jobId
to the `ScheduledState`. If fromState value
is not null, state change will be performed only if the current state name
of a job equal to the given value.
  - `jobId`: Identifier of job, whose state is being changed.
  - `delay`: Delay, after which the job will be scheduled.
  - `fromState`: Current state assertion, or null if unneeded.
  - returns: True, if state change succeeded, otherwise false.
- `Schedule(Expressions.Expression<Action>, DateTimeOffset)`
  - Creates a new background job based on a specified method call expression
and schedules it to be enqueued at the given moment of time.
  - `methodCall`: Method call expression that will be marshalled to the Server.
  - `enqueueAt`: The moment of time at which the job will be enqueued.
  - returns: Unique identifier of a created job.
- `Schedule(Expressions.Expression<Action>, TimeSpan)`
  - Creates a new background job based on a specified method
call expression and schedules it to be enqueued after a given delay.
  - `methodCall`: Instance method call expression that will be marshalled to the Server.
  - `delay`: Delay, after which the job will be enqueued.
  - returns: Unique identifier of the created job.
- `Schedule(Expressions.Expression<Func<Tasks.Task>>, DateTimeOffset)`
  - Creates a new background job based on a specified method call expression
and schedules it to be enqueued at the given moment of time.
  - `methodCall`: Method call expression that will be marshalled to the Server.
  - `enqueueAt`: The moment of time at which the job will be enqueued.
  - returns: Unique identifier of a created job.
- `Schedule(Expressions.Expression<Func<Tasks.Task>>, TimeSpan)`
  - Creates a new background job based on a specified method
call expression and schedules it to be enqueued after a given delay.
  - `methodCall`: Instance method call expression that will be marshalled to the Server.
  - `delay`: Delay, after which the job will be enqueued.
  - returns: Unique identifier of the created job.
- `Schedule([NotNull, InstantHandle] Expression<Action>, DateTimeOffset)`
- `Schedule([NotNull, InstantHandle] Expression<Action>, TimeSpan)`
- `Schedule([NotNull, InstantHandle] Expression<Func<Task>>, DateTimeOffset)`
- `Schedule([NotNull, InstantHandle] Expression<Func<Task>>, TimeSpan)`
- `Schedule([NotNull] string, [NotNull, InstantHandle] Expression<Action>, DateTimeOffset)`
- `Schedule([NotNull] string, [NotNull, InstantHandle] Expression<Action>, TimeSpan)`
- `Schedule([NotNull] string, [NotNull, InstantHandle] Expression<Func<Task>>, DateTimeOffset)`
- `Schedule([NotNull] string, [NotNull, InstantHandle] Expression<Func<Task>>, TimeSpan)`
- `Schedule(string, Expressions.Expression<Action>, DateTimeOffset)`
  - Creates a new background job based on a specified method call expression and schedules it
to be enqueued to the specified queue at the given moment of time.
  - `queue`: Default queue for the background job.
  - `methodCall`: Method call expression that will be marshalled to the Server.
  - `enqueueAt`: The moment of time at which the job will be enqueued.
  - returns: Unique identifier of a created job.
- `Schedule(string, Expressions.Expression<Action>, TimeSpan)`
  - Creates a new background job based on a specified method call expression and schedules it
to be enqueued to the specified queue after a given delay.
  - `queue`: Default queue for the background job.
  - `methodCall`: Instance method call expression that will be marshalled to the Server.
  - `delay`: Delay, after which the job will be enqueued.
  - returns: Unique identifier of the created job.
- `Schedule(string, Expressions.Expression<Func<Tasks.Task>>, DateTimeOffset)`
  - Creates a new background job based on a specified method call expression and schedules it
to be enqueued to the specified queue at the given moment of time.
  - `queue`: Default queue for the background job.
  - `methodCall`: Method call expression that will be marshalled to the Server.
  - `enqueueAt`: The moment of time at which the job will be enqueued.
  - returns: Unique identifier of a created job.
- `Schedule(string, Expressions.Expression<Func<Tasks.Task>>, TimeSpan)`
  - Creates a new background job based on a specified method call expression and schedules it
to be enqueued to the specified queue after a given delay.
  - `queue`: Default queue for the background job.
  - `methodCall`: Instance method call expression that will be marshalled to the Server.
  - `delay`: Delay, after which the job will be enqueued.
  - returns: Unique identifier of the created job.
- `Schedule<T>(Expressions.Expression<Action<T1>>, DateTimeOffset)`
  - Creates a new background job based on a specified method call expression
and schedules it to be enqueued at the given moment of time.
  - `methodCall`: Method call expression that will be marshalled to the Server.
  - `enqueueAt`: The moment of time at which the job will be enqueued.
  - `<T>`: The type whose method will be invoked during the job processing.
  - returns: Unique identifier of a created job.
- `Schedule<T>(Expressions.Expression<Action<T1>>, TimeSpan)`
  - Creates a new background job based on a specified instance method
call expression and schedules it to be enqueued after a given delay.
  - `methodCall`: Instance method call expression that will be marshalled to the Server.
  - `delay`: Delay, after which the job will be enqueued.
  - `<T>`: Type whose method will be invoked during job processing.
  - returns: Unique identifier of the created job.
- `Schedule<T>(Expressions.Expression<Func<T1,Tasks.Task>>, DateTimeOffset)`
  - Creates a new background job based on a specified method call expression
and schedules it to be enqueued at the given moment of time.
  - `methodCall`: Method call expression that will be marshalled to the Server.
  - `enqueueAt`: The moment of time at which the job will be enqueued.
  - `<T>`: The type whose method will be invoked during the job processing.
  - returns: Unique identifier of a created job.
- `Schedule<T>(Expressions.Expression<Func<T1,Tasks.Task>>, TimeSpan)`
  - Creates a new background job based on a specified instance method
call expression and schedules it to be enqueued after a given delay.
  - `methodCall`: Instance method call expression that will be marshalled to the Server.
  - `delay`: Delay, after which the job will be enqueued.
  - `<T>`: Type whose method will be invoked during job processing.
  - returns: Unique identifier of the created job.
- `Schedule<T>([NotNull, InstantHandle] Expression<Action<T>>, DateTimeOffset)`
- `Schedule<T>([NotNull, InstantHandle] Expression<Action<T>>, TimeSpan)`
- `Schedule<T>([NotNull, InstantHandle] Expression<Func<T, Task>>, DateTimeOffset)`
- `Schedule<T>([NotNull, InstantHandle] Expression<Func<T, Task>>, TimeSpan)`
- `Schedule<T>([NotNull] string, [NotNull, InstantHandle] Expression<Action<T>>, DateTimeOffset)`
- `Schedule<T>([NotNull] string, [NotNull, InstantHandle] Expression<Action<T>>, TimeSpan)`
- `Schedule<T>([NotNull] string, [NotNull, InstantHandle] Expression<Func<T, Task>>, DateTimeOffset)`
- `Schedule<T>([NotNull] string, [NotNull, InstantHandle] Expression<Func<T, Task>>, TimeSpan)`
- `Schedule<T>(string, Expressions.Expression<Action<T1>>, DateTimeOffset)`
  - Creates a new background job based on a specified method call expression and schedules it
to be enqueued to the specified queue at the given moment of time.
  - `queue`: Default queue for the background job.
  - `methodCall`: Method call expression that will be marshalled to the Server.
  - `enqueueAt`: The moment of time at which the job will be enqueued.
  - `<T>`: The type whose method will be invoked during the job processing.
  - returns: Unique identifier of a created job.
- `Schedule<T>(string, Expressions.Expression<Action<T1>>, TimeSpan)`
  - Creates a new background job based on a specified instance method call expression and schedules
it to be enqueued to the specified queue after a given delay.
  - `queue`: Default queue for the background job.
  - `methodCall`: Instance method call expression that will be marshalled to the Server.
  - `delay`: Delay, after which the job will be enqueued.
  - `<T>`: Type whose method will be invoked during job processing.
  - returns: Unique identifier of the created job.
- `Schedule<T>(string, Expressions.Expression<Func<T1,Tasks.Task>>, DateTimeOffset)`
  - Creates a new background job based on a specified method call expression and schedules it
to be enqueued to the specified queue at the given moment of time.
  - `queue`: Default queue for the background job.
  - `methodCall`: Method call expression that will be marshalled to the Server.
  - `enqueueAt`: The moment of time at which the job will be enqueued.
  - `<T>`: The type whose method will be invoked during the job processing.
  - returns: Unique identifier of a created job.
- `Schedule<T>(string, Expressions.Expression<Func<T1,Tasks.Task>>, TimeSpan)`
  - Creates a new background job based on a specified instance method call expression and schedules
it to be enqueued to the specified queue after a given delay.
  - `queue`: Default queue for the background job.
  - `methodCall`: Instance method call expression that will be marshalled to the Server.
  - `delay`: Delay, after which the job will be enqueued.
  - `<T>`: Type whose method will be invoked during job processing.
  - returns: Unique identifier of the created job.

**Properties:**

- `CreatedAt`
- `Id`
- `Job`
- `ParametersSnapshot`


#### `BackgroundJobClient`

Provides methods for creating background jobs and changing their states.
Represents a default implementation of the `IBackgroundJobClient`
interface.

**Methods:**

- `#ctor`
  - Initializes a new instance of the `BackgroundJobClient`
class with the storage from a global configuration.
  - remarks: Please see the `GlobalConfiguration` class for the
details regarding the global configuration.
- `#ctor(Hangfire.JobStorage)`
  - Initializes a new instance of the `BackgroundJobClient`
class with the specified storage.
  - `storage`: Job storage to use for background jobs.
- `#ctor(Hangfire.JobStorage, Hangfire.Client.IBackgroundJobFactory, Hangfire.States.IBackgroundJobStateChanger)`
  - Initializes a new instance of the `BackgroundJobClient` class
with the specified storage, background job factory and state changer.
  - `storage`: Job storage to use for background jobs.
  - `factory`: Factory to create background jobs.
  - `stateChanger`: State changer to change states of background jobs.
- `#ctor(Hangfire.JobStorage, Hangfire.Common.IJobFilterProvider)`
  - Initializes a new instance of the `BackgroundJobClient` class
with the specified storage and filter provider.
  - `storage`: Job storage to use for background jobs.
  - `filterProvider`: Filter provider responsible to locate job filters.
- `#ctor([NotNull] JobStorage)`
- `#ctor([NotNull] JobStorage, [NotNull] IBackgroundJobFactory, [NotNull] IBackgroundJobStateChanger)`
- `#ctor([NotNull] JobStorage, [NotNull] IJobFilterProvider)`
- `ChangeState(string, Hangfire.States.IState, string)`
- `ChangeState(string, IState, string)`
- `Create(Hangfire.Common.Job, Hangfire.States.IState)`
- `Create(Hangfire.Common.Job, Hangfire.States.IState, Generic.IDictionary<string,object>)`
- `Create(Job, IState)`
- `Create(Job, IState, IDictionary<string, object>)`

**Properties:**

- `RetryAttempts`
- `Storage`


#### `BackgroundJobClientException`

The exception that is thrown when an instance of the class that
implements the `IBackgroundJobClient` interface is unable
to perform an operation due to an error.

**Methods:**

- `#ctor(Serialization.SerializationInfo, Serialization.StreamingContext)`
  - Initializes a new instance of the `BackgroundJobClientException` class
with serialized data.
  - `info`: The `SerializationInfo` that holds the serialized object data about the exception being thrown.
  - `context`: The `StreamingContext` that contains contextual information about the source or destination.
- `#ctor(string, Exception)`
  - Initializes a new instance of the `BackgroundJobClientException`
class with a specified error message and a reference to the inner exception
that is the cause of this exception.
  - `message`: The error message that explains the reason for the exception.
  - `inner`: The exception that is the cause of this exception, not null.


#### `BackgroundJobClientExtensions`

Provides extension methods for the `IBackgroundJobClient`
interface to simplify the creation of fire-and-forget jobs, delayed
jobs, continuations and other background jobs in well-known states.
Also allows to re-queue and delete existing background jobs.

**Methods:**

- `ChangeState(Hangfire.IBackgroundJobClient, string, Hangfire.States.IState)`
  - Changes state of a job with the given jobId to
the specified one.
  - `client`: An instance of `IBackgroundJobClient` implementation.
  - `jobId`: A job, whose state is being changed.
  - `state`: New state for a job.
  - returns: True, if state change succeeded, otherwise false.
- `ChangeState([NotNull] this IBackgroundJobClient, [NotNull] string, [NotNull] IState)`
- `ContinueJobWith(Hangfire.IBackgroundJobClient, string, Expressions.Expression<Action>)`
  - Creates a new background job that will wait for a successful completion
of another background job to be triggered in the `EnqueuedState`.
  - `client`: A job client instance.
  - `parentId`: Identifier of a background job to wait completion for.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - returns: Unique identifier of a created job.
- `ContinueJobWith(Hangfire.IBackgroundJobClient, string, Expressions.Expression<Action>, Hangfire.JobContinuationOptions)`
  - Creates a new background job that will wait for another background job to be triggered
in the `EnqueuedState`.
  - `client`: A job client instance.
  - `parentId`: Identifier of a background job to wait completion for.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - `options`: Continuation options.
  - returns: Unique identifier of a created job.
- `ContinueJobWith(Hangfire.IBackgroundJobClient, string, Expressions.Expression<Action>, Hangfire.States.IState)`
  - Creates a new background job that will wait for a successful completion
of another background job to be triggered.
  - `client`: A job client instance.
  - `parentId`: Identifier of a background job to wait completion for.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - `nextState`: Next state for a job, when continuation is triggered.
If null, then `EnqueuedState` is used.
  - returns: Unique identifier of a created job.
- `ContinueJobWith(Hangfire.IBackgroundJobClient, string, Expressions.Expression<Action>, Hangfire.States.IState, Hangfire.JobContinuationOptions)`
  - Creates a new background job that will wait for another background job to be triggered.
  - `client`: A job client instance.
  - `parentId`: Identifier of a background job to wait completion for.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - `nextState`: Next state for a job, when continuation is triggered.
  - `options`: Continuation options.
  - returns: Unique identifier of a created job.
- `ContinueJobWith(Hangfire.IBackgroundJobClient, string, Expressions.Expression<Func<Tasks.Task>>, Hangfire.States.IState, Hangfire.JobContinuationOptions)`
  - Creates a new background job that will wait for another background job to be triggered.
  - `client`: A job client instance.
  - `parentId`: Identifier of a background job to wait completion for.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - `nextState`: Next state for a job, when continuation is triggered.
If null, then `EnqueuedState` is used.
  - `options`: Continuation options. By default,
`OnlyOnSucceededState` is used.
  - returns: Unique identifier of a created job.
- `ContinueJobWith(Hangfire.IBackgroundJobClient, string, string, Expressions.Expression<Action>, Hangfire.States.IState, Hangfire.JobContinuationOptions)`
  - Creates a new background job that will wait for another background job to be enqueued
to the specified queue.
  - `client`: A job client instance.
  - `parentId`: Identifier of a background job to wait completion for.
  - `queue`: Default queue for the continuation.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - `nextState`: Next state for a job, when continuation is triggered.
  - `options`: Continuation options.
  - returns: Unique identifier of a created job.
- `ContinueJobWith(Hangfire.IBackgroundJobClient, string, string, Expressions.Expression<Func<Tasks.Task>>, Hangfire.States.IState, Hangfire.JobContinuationOptions)`
  - Creates a new background job that will wait for another background job to be enqueued
to the specified queue.
  - `client`: A job client instance.
  - `parentId`: Identifier of a background job to wait completion for.
  - `queue`: Default queue for the continuation.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - `nextState`: Next state for a job, when continuation is triggered.
If null, then `EnqueuedState` is used.
  - `options`: Continuation options. By default,
`OnlyOnSucceededState` is used.
  - returns: Unique identifier of a created job.
- `ContinueJobWith([NotNull] this IBackgroundJobClient, [NotNull] string, [InstantHandle] Expression<Action>, [NotNull] IState, JobContinuationOptions)`
- `ContinueJobWith([NotNull] this IBackgroundJobClient, [NotNull] string, [InstantHandle] Expression<Func<Task>>, [CanBeNull] IState, JobContinuationOptions)`
- `ContinueJobWith([NotNull] this IBackgroundJobClient, [NotNull] string, [NotNull, InstantHandle] Expression<Action>)`
- `ContinueJobWith([NotNull] this IBackgroundJobClient, [NotNull] string, [NotNull, InstantHandle] Expression<Action>, JobContinuationOptions)`
- `ContinueJobWith([NotNull] this IBackgroundJobClient, [NotNull] string, [NotNull, InstantHandle] Expression<Action>, [NotNull] IState)`
- `ContinueJobWith([NotNull] this IBackgroundJobClient, [NotNull] string, [NotNull] string, [InstantHandle] Expression<Func<Task>>, [CanBeNull] IState, JobContinuationOptions)`
- `ContinueJobWith([NotNull] this IBackgroundJobClient, [NotNull] string, [NotNull] string, [NotNull, InstantHandle] Expression<Action>, [CanBeNull] IState, JobContinuationOptions)`
- `ContinueJobWith<T>(Hangfire.IBackgroundJobClient, string, Expressions.Expression<Action<T1>>)`
  - Creates a new background job that will wait for a successful completion
of another background job to be triggered in the `EnqueuedState`.
  - `client`: A job client instance.
  - `parentId`: Identifier of a background job to wait completion for.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - returns: Unique identifier of a created job.
- `ContinueJobWith<T>(Hangfire.IBackgroundJobClient, string, Expressions.Expression<Action<T1>>, Hangfire.JobContinuationOptions)`
  - Creates a new background job that will wait for another background job to be triggered
in the `EnqueuedState`.
  - `client`: A job client instance.
  - `parentId`: Identifier of a background job to wait completion for.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - `options`: Continuation options.
  - returns: Unique identifier of a created job.
- `ContinueJobWith<T>(Hangfire.IBackgroundJobClient, string, Expressions.Expression<Action<T1>>, Hangfire.States.IState)`
  - Creates a new background job that will wait for a successful completion
of another background job to be triggered.
  - `client`: A job client instance.
  - `parentId`: Identifier of a background job to wait completion for.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - `nextState`: Next state for a job, when continuation is triggered.
If null, then `EnqueuedState` is used.
  - returns: Unique identifier of a created job.
- `ContinueJobWith<T>(Hangfire.IBackgroundJobClient, string, Expressions.Expression<Action<T1>>, Hangfire.States.IState, Hangfire.JobContinuationOptions)`
  - Creates a new background job that will wait for another background job to be triggered.
  - `client`: A job client instance.
  - `parentId`: Identifier of a background job to wait completion for.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - `nextState`: Next state for a job, when continuation is triggered.
  - `options`: Continuation options.
  - returns: Unique identifier of a created job.
- `ContinueJobWith<T>(Hangfire.IBackgroundJobClient, string, Expressions.Expression<Func<T1,Tasks.Task>>, Hangfire.States.IState, Hangfire.JobContinuationOptions)`
  - Creates a new background job that will wait for another background job to be triggered.
  - `client`: A job client instance.
  - `parentId`: Identifier of a background job to wait completion for.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - `nextState`: Next state for a job, when continuation is triggered.
If null, then `EnqueuedState` is used.
  - `options`: Continuation options. By default,
`OnlyOnSucceededState` is used.
  - returns: Unique identifier of a created job.
- `ContinueJobWith<T>(Hangfire.IBackgroundJobClient, string, string, Expressions.Expression<Action<T1>>, Hangfire.States.IState, Hangfire.JobContinuationOptions)`
  - Creates a new background job that will wait for another background job to be enqueued
to the specified queue.
  - `client`: A job client instance.
  - `parentId`: Identifier of a background job to wait completion for.
  - `queue`: Default queue for the continuation.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - `nextState`: Next state for a job, when continuation is triggered.
  - `options`: Continuation options.
  - returns: Unique identifier of a created job.
- `ContinueJobWith<T>(Hangfire.IBackgroundJobClient, string, string, Expressions.Expression<Func<T1,Tasks.Task>>, Hangfire.States.IState, Hangfire.JobContinuationOptions)`
  - Creates a new background job that will wait for another background job to be enqueued
to the specified queue.
  - `client`: A job client instance.
  - `parentId`: Identifier of a background job to wait completion for.
  - `queue`: Default queue for the continuation.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - `nextState`: Next state for a job, when continuation is triggered.
If null, then `EnqueuedState` is used.
  - `options`: Continuation options. By default,
`OnlyOnSucceededState` is used.
  - returns: Unique identifier of a created job.
- `ContinueJobWith<T>([NotNull] this IBackgroundJobClient, [NotNull] string, [NotNull, InstantHandle] Expression<Action<T>>)`
- `ContinueJobWith<T>([NotNull] this IBackgroundJobClient, [NotNull] string, [NotNull, InstantHandle] Expression<Action<T>>, JobContinuationOptions)`
- `ContinueJobWith<T>([NotNull] this IBackgroundJobClient, [NotNull] string, [NotNull, InstantHandle] Expression<Action<T>>, [NotNull] IState)`
- `ContinueJobWith<T>([NotNull] this IBackgroundJobClient, [NotNull] string, [NotNull, InstantHandle] Expression<Action<T>>, [NotNull] IState, JobContinuationOptions)`
- `ContinueJobWith<T>([NotNull] this IBackgroundJobClient, [NotNull] string, [NotNull, InstantHandle] Expression<Func<T, Task>>, [CanBeNull] IState, JobContinuationOptions)`
- `ContinueJobWith<T>([NotNull] this IBackgroundJobClient, [NotNull] string, [NotNull] string, [NotNull, InstantHandle] Expression<Action<T>>, [CanBeNull] IState, JobContinuationOptions)`
- `ContinueJobWith<T>([NotNull] this IBackgroundJobClient, [NotNull] string, [NotNull] string, [NotNull, InstantHandle] Expression<Func<T, Task>>, [CanBeNull] IState, JobContinuationOptions)`
- `ContinueWith(Hangfire.IBackgroundJobClient, string, Expressions.Expression<Action>)`
  - Creates a new background job that will wait for a successful completion
of another background job to be triggered in the `EnqueuedState`.
  - `client`: A job client instance.
  - `parentId`: Identifier of a background job to wait completion for.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - returns: Unique identifier of a created job.
- `ContinueWith(Hangfire.IBackgroundJobClient, string, Expressions.Expression<Action>, Hangfire.JobContinuationOptions)`
  - Creates a new background job that will wait for another background job to be triggered
in the `EnqueuedState`.
  - `client`: A job client instance.
  - `parentId`: Identifier of a background job to wait completion for.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - `options`: Continuation options.
  - returns: Unique identifier of a created job.
- `ContinueWith(Hangfire.IBackgroundJobClient, string, Expressions.Expression<Action>, Hangfire.States.IState)`
  - Creates a new background job that will wait for a successful completion
of another background job to be triggered.
  - `client`: A job client instance.
  - `parentId`: Identifier of a background job to wait completion for.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - `nextState`: Next state for a job, when continuation is triggered.
If null, then `EnqueuedState` is used.
  - returns: Unique identifier of a created job.
- `ContinueWith(Hangfire.IBackgroundJobClient, string, Expressions.Expression<Action>, Hangfire.States.IState, Hangfire.JobContinuationOptions)`
  - Creates a new background job that will wait for another background job to be triggered.
  - `client`: A job client instance.
  - `parentId`: Identifier of a background job to wait completion for.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - `nextState`: Next state for a job, when continuation is triggered.
  - `options`: Continuation options.
  - returns: Unique identifier of a created job.
- `ContinueWith(Hangfire.IBackgroundJobClient, string, Expressions.Expression<Func<Tasks.Task>>, Hangfire.States.IState, Hangfire.JobContinuationOptions)`
  - Creates a new background job that will wait for another background job to be triggered.
  - `client`: A job client instance.
  - `parentId`: Identifier of a background job to wait completion for.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - `nextState`: Next state for a job, when continuation is triggered.
If null, then `EnqueuedState` is used.
  - `options`: Continuation options. By default,
`OnlyOnSucceededState` is used.
  - returns: Unique identifier of a created job.
- `ContinueWith([NotNull] this IBackgroundJobClient, [NotNull] string, [InstantHandle] Expression<Action>, [NotNull] IState, JobContinuationOptions)`
- `ContinueWith([NotNull] this IBackgroundJobClient, [NotNull] string, [InstantHandle] Expression<Func<Task>>, [CanBeNull] IState, JobContinuationOptions)`
- `ContinueWith([NotNull] this IBackgroundJobClient, [NotNull] string, [NotNull, InstantHandle] Expression<Action>)`
- `ContinueWith([NotNull] this IBackgroundJobClient, [NotNull] string, [NotNull, InstantHandle] Expression<Action>, JobContinuationOptions)`
- `ContinueWith([NotNull] this IBackgroundJobClient, [NotNull] string, [NotNull, InstantHandle] Expression<Action>, [NotNull] IState)`
- `ContinueWith<T>(Hangfire.IBackgroundJobClient, string, Expressions.Expression<Action<T1>>)`
  - Creates a new background job that will wait for a successful completion
of another background job to be triggered in the `EnqueuedState`.
  - `client`: A job client instance.
  - `parentId`: Identifier of a background job to wait completion for.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - returns: Unique identifier of a created job.
- `ContinueWith<T>(Hangfire.IBackgroundJobClient, string, Expressions.Expression<Action<T1>>, Hangfire.JobContinuationOptions)`
  - Creates a new background job that will wait for another background job to be triggered
in the `EnqueuedState`.
  - `client`: A job client instance.
  - `parentId`: Identifier of a background job to wait completion for.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - `options`: Continuation options.
  - returns: Unique identifier of a created job.
- `ContinueWith<T>(Hangfire.IBackgroundJobClient, string, Expressions.Expression<Action<T1>>, Hangfire.States.IState)`
  - Creates a new background job that will wait for a successful completion
of another background job to be triggered.
  - `client`: A job client instance.
  - `parentId`: Identifier of a background job to wait completion for.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - `nextState`: Next state for a job, when continuation is triggered.
If null, then `EnqueuedState` is used.
  - returns: Unique identifier of a created job.
- `ContinueWith<T>(Hangfire.IBackgroundJobClient, string, Expressions.Expression<Action<T1>>, Hangfire.States.IState, Hangfire.JobContinuationOptions)`
  - Creates a new background job that will wait for another background job to be triggered.
  - `client`: A job client instance.
  - `parentId`: Identifier of a background job to wait completion for.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - `nextState`: Next state for a job, when continuation is triggered.
  - `options`: Continuation options.
  - returns: Unique identifier of a created job.
- `ContinueWith<T>(Hangfire.IBackgroundJobClient, string, Expressions.Expression<Func<T1,Tasks.Task>>, Hangfire.States.IState, Hangfire.JobContinuationOptions)`
  - Creates a new background job that will wait for another background job to be triggered.
  - `client`: A job client instance.
  - `parentId`: Identifier of a background job to wait completion for.
  - `methodCall`: Method call expression that will be marshalled to a server.
  - `nextState`: Next state for a job, when continuation is triggered.
If null, then `EnqueuedState` is used.
  - `options`: Continuation options. By default,
`OnlyOnSucceededState` is used.
  - returns: Unique identifier of a created job.
- `ContinueWith<T>([NotNull] this IBackgroundJobClient, [NotNull] string, [NotNull, InstantHandle] Expression<Action<T>>)`
- `ContinueWith<T>([NotNull] this IBackgroundJobClient, [NotNull] string, [NotNull, InstantHandle] Expression<Action<T>>, JobContinuationOptions)`
- `ContinueWith<T>([NotNull] this IBackgroundJobClient, [NotNull] string, [NotNull, InstantHandle] Expression<Action<T>>, [NotNull] IState)`
- `ContinueWith<T>([NotNull] this IBackgroundJobClient, [NotNull] string, [NotNull, InstantHandle] Expression<Action<T>>, [NotNull] IState, JobContinuationOptions)`
- `ContinueWith<T>([NotNull] this IBackgroundJobClient, [NotNull] string, [NotNull, InstantHandle] Expression<Func<T, Task>>, [CanBeNull] IState, JobContinuationOptions)`
- `Create(Hangfire.IBackgroundJobClient, Expressions.Expression<Action>, Hangfire.States.IState)`
  - Creates a new background job based on a specified lambda expression in a given state.
  - `client`: A job client instance.
  - `methodCall`: Static method call expression that will be marshalled to the Server.
  - `state`: Initial state of a job.
  - returns: Unique identifier of the created job.
- `Create(Hangfire.IBackgroundJobClient, Expressions.Expression<Func<Tasks.Task>>, Hangfire.States.IState)`
  - Creates a new background job based on a specified lambda expression in a given state.
  - `client`: A job client instance.
  - `methodCall`: Static method call expression that will be marshalled to the Server.
  - `state`: Initial state of a job.
  - returns: Unique identifier of the created job.
- `Create(Hangfire.IBackgroundJobClient, string, Expressions.Expression<Action>, Hangfire.States.IState)`
  - Creates a new background job based on a specified lambda expression in a given state with
the specified default queue.
  - `client`: A job client instance.
  - `queue`: Default queue for a job.
  - `methodCall`: Static method call expression that will be marshalled to the Server.
  - `state`: Initial state of a job.
  - returns: Unique identifier of the created job.
- `Create(Hangfire.IBackgroundJobClient, string, Expressions.Expression<Func<Tasks.Task>>, Hangfire.States.IState)`
  - Creates a new background job based on a specified lambda expression in a given state with
the specified default queue.
  - `client`: A job client instance.
  - `queue`: Default queue for a job.
  - `methodCall`: Static method call expression that will be marshalled to the Server.
  - `state`: Initial state of a job.
  - returns: Unique identifier of the created job.
- `Create([NotNull] this IBackgroundJobClient, [NotNull, InstantHandle] Expression<Action>, [NotNull] IState)`
- `Create([NotNull] this IBackgroundJobClient, [NotNull, InstantHandle] Expression<Func<Task>>, [NotNull] IState)`
- `Create([NotNull] this IBackgroundJobClient, [NotNull] string, [NotNull, InstantHandle] Expression<Action>, [NotNull] IState)`
- `Create([NotNull] this IBackgroundJobClient, [NotNull] string, [NotNull, InstantHandle] Expression<Func<Task>>, [NotNull] IState)`
- `Create<T>(Hangfire.IBackgroundJobClient, Expressions.Expression<Action<T1>>, Hangfire.States.IState)`
  - Creates a new background job based on a specified instance method in a given state.
  - `client`: A job client instance.
  - `methodCall`: Instance method call expression that will be marshalled to the Server.
  - `state`: Initial state of a job.
  - `<T>`: Type whose method will be invoked during job processing.
  - returns: Unique identifier of the created job.
- `Create<T>(Hangfire.IBackgroundJobClient, Expressions.Expression<Func<T1,Tasks.Task>>, Hangfire.States.IState)`
  - Creates a new background job based on a specified instance method in a given state.
  - `client`: A job client instance.
  - `methodCall`: Instance method call expression that will be marshalled to the Server.
  - `state`: Initial state of a job.
  - `<T>`: Type whose method will be invoked during job processing.
  - returns: Unique identifier of the created job.
- `Create<T>(Hangfire.IBackgroundJobClient, string, Expressions.Expression<Action<T1>>, Hangfire.States.IState)`
  - Creates a new background job based on a specified instance method in a given state with
the specified default queue.
  - `client`: A job client instance.
  - `queue`: Default queue for a job.
  - `methodCall`: Instance method call expression that will be marshalled to the Server.
  - `state`: Initial state of a job.
  - `<T>`: Type whose method will be invoked during job processing.
  - returns: Unique identifier of the created job.
- `Create<T>(Hangfire.IBackgroundJobClient, string, Expressions.Expression<Func<T1,Tasks.Task>>, Hangfire.States.IState)`
  - Creates a new background job based on a specified instance method in a given state with
the specified default queue.
  - `client`: A job client instance.
  - `queue`: Default queue for a job.
  - `methodCall`: Instance method call expression that will be marshalled to the Server.
  - `state`: Initial state of a job.
  - `<T>`: Type whose method will be invoked during job processing.
  - returns: Unique identifier of the created job.
- `Create<T>([NotNull] this IBackgroundJobClient, [NotNull, InstantHandle] Expression<Action<T>>, [NotNull] IState)`
- `Create<T>([NotNull] this IBackgroundJobClient, [NotNull, InstantHandle] Expression<Func<T, Task>>, [NotNull] IState)`
- `Create<T>([NotNull] this IBackgroundJobClient, [NotNull] string, [NotNull, InstantHandle] Expression<Action<T>>, [NotNull] IState)`
- `Create<T>([NotNull] this IBackgroundJobClient, [NotNull] string, [NotNull, InstantHandle] Expression<Func<T, Task>>, [NotNull] IState)`
- `Delete(Hangfire.IBackgroundJobClient, string)`
  - Changes state of a job with the specified jobId
to the `DeletedState`.
  - `client`: An instance of `IBackgroundJobClient` implementation.
  - `jobId`: Identifier of job, whose state is being changed.
  - returns: True, if state change succeeded, otherwise false.
  - remarks: The job is not actually being deleted, this method changes only
its state.

This operation does not provide guarantee that the job will not be
performed. If you are deleting a job that is performing right now, it
will be performed anyway, despite of this call.

The method returns result of a state transition. It can be false
if a job was expired, its method does not exist or there was an
exception during the state change process.
- `Delete(Hangfire.IBackgroundJobClient, string, string)`
  - Changes state of a job with the specified jobId
to the `DeletedState`. If fromState value
is not null, state change will be performed only if the current state name
of a job equal to the given value.
  - `client`: An instance of `IBackgroundJobClient` implementation.
  - `jobId`: Identifier of job, whose state is being changed.
  - `fromState`: Current state assertion, or null if unneeded.
  - returns: True, if state change succeeded, otherwise false.
  - remarks: The job is not actually being deleted, this method changes only
its state.

This operation does not provide guarantee that the job will not be
performed. If you are deleting a job that is performing right now, it
will be performed anyway, despite of this call.

The method returns result of a state transition. It can be false
if a job was expired, its method does not exist or there was an
exception during the state change process.
- `Delete([NotNull] this IBackgroundJobClient, [NotNull] string)`
- `Delete([NotNull] this IBackgroundJobClient, [NotNull] string, [CanBeNull] string)`
- `Enqueue(Hangfire.IBackgroundJobClient, Expressions.Expression<Action>)`
  - Creates a background job based on a specified lambda expression
and places it into its actual queue.
Please, see the `QueueAttribute` to learn how to
place the job on a non-default queue.
  - `client`: A job client instance.
  - `methodCall`: Static method call expression that will be marshalled to the Server.
  - returns: Unique identifier of the created job.
- `Enqueue(Hangfire.IBackgroundJobClient, Expressions.Expression<Func<Tasks.Task>>)`
  - Creates a background job based on a specified lambda expression
and places it into its actual queue.
Please, see the `QueueAttribute` to learn how to
place the job on a non-default queue.
  - `client`: A job client instance.
  - `methodCall`: Static method call expression that will be marshalled to the Server.
  - returns: Unique identifier of the created job.
- `Enqueue(Hangfire.IBackgroundJobClient, string, Expressions.Expression<Action>)`
  - Creates a background job based on a specified lambda expression and places it into
the specified queue.
Please, see the `QueueAttribute` to learn how to
place the job on a non-default queue.
  - `client`: A job client instance.
  - `queue`: Default queue for the background job.
  - `methodCall`: Static method call expression that will be marshalled to the Server.
  - returns: Unique identifier of the created job.
- `Enqueue(Hangfire.IBackgroundJobClient, string, Expressions.Expression<Func<Tasks.Task>>)`
  - Creates a background job based on a specified lambda expression and places it into
the specified queue.
Please, see the `QueueAttribute` to learn how to
place the job on a non-default queue.
  - `client`: A job client instance.
  - `queue`: Default queue for the background job.
  - `methodCall`: Static method call expression that will be marshalled to the Server.
  - returns: Unique identifier of the created job.
- `Enqueue([NotNull] this IBackgroundJobClient, [NotNull, InstantHandle] Expression<Action>)`
- `Enqueue([NotNull] this IBackgroundJobClient, [NotNull, InstantHandle] Expression<Func<Task>>)`
- `Enqueue([NotNull] this IBackgroundJobClient, [NotNull] string, [NotNull, InstantHandle] Expression<Action>)`
- `Enqueue([NotNull] this IBackgroundJobClient, [NotNull] string, [NotNull, InstantHandle] Expression<Func<Task>>)`
- `Enqueue<T>(Hangfire.IBackgroundJobClient, Expressions.Expression<Action<T1>>)`
  - Creates a background job based on a specified lambda expression
and places it into its actual queue.
Please, see the `QueueAttribute` to learn how to
place the job on a non-default queue.
  - `client`: A job client instance.
  - `methodCall`: Instance method call expression that will be marshalled to the Server.
  - `<T>`: Type whose method will be invoked during job processing.
  - returns: Unique identifier of the created job.
- `Enqueue<T>(Hangfire.IBackgroundJobClient, Expressions.Expression<Func<T1,Tasks.Task>>)`
  - Creates a background job based on a specified lambda expression
and places it into its actual queue.
Please, see the `QueueAttribute` to learn how to
place the job on a non-default queue.
  - `client`: A job client instance.
  - `methodCall`: Instance method call expression that will be marshalled to the Server.
  - `<T>`: Type whose method will be invoked during job processing.
  - returns: Unique identifier of the created job.
- `Enqueue<T>(Hangfire.IBackgroundJobClient, string, Expressions.Expression<Action<T1>>)`
  - Creates a background job based on a specified lambda expression and places it into
the specified queue.
Please, see the `QueueAttribute` to learn how to
place the job on a non-default queue.
  - `client`: A job client instance.
  - `queue`: Default queue for the background job.
  - `methodCall`: Instance method call expression that will be marshalled to the Server.
  - `<T>`: Type whose method will be invoked during job processing.
  - returns: Unique identifier of the created job.
- `Enqueue<T>(Hangfire.IBackgroundJobClient, string, Expressions.Expression<Func<T1,Tasks.Task>>)`
  - Creates a background job based on a specified lambda expression and places it into
the specified queue.
Please, see the `QueueAttribute` to learn how to
place the job on a non-default queue.
  - `client`: A job client instance.
  - `queue`: Default queue for the background job.
  - `methodCall`: Instance method call expression that will be marshalled to the Server.
  - `<T>`: Type whose method will be invoked during job processing.
  - returns: Unique identifier of the created job.
- `Enqueue<T>([NotNull] this IBackgroundJobClient, [NotNull, InstantHandle] Expression<Action<T>>)`
- `Enqueue<T>([NotNull] this IBackgroundJobClient, [NotNull, InstantHandle] Expression<Func<T, Task>>)`
- `Enqueue<T>([NotNull] this IBackgroundJobClient, [NotNull] string, [NotNull, InstantHandle] Expression<Action<T>>)`
- `Enqueue<T>([NotNull] this IBackgroundJobClient, [NotNull] string, [NotNull, InstantHandle] Expression<Func<T, Task>>)`
- `Requeue(Hangfire.IBackgroundJobClient, string)`
  - Changes state of a job with the specified jobId
to the `EnqueuedState`.
  - `client`: An instance of `IBackgroundJobClient` implementation.
  - `jobId`: Identifier of job, whose state is being changed.
  - returns: True, if state change succeeded, otherwise false.
- `Requeue(Hangfire.IBackgroundJobClient, string, string)`
  - Changes state of a job with the specified jobId
to the `EnqueuedState`. If fromState value
is not null, state change will be performed only if the current state name
of a job equal to the given value.
  - `client`: An instance of `IBackgroundJobClient` implementation.
  - `jobId`: Identifier of job, whose state is being changed.
  - `fromState`: Current state assertion, or null if unneeded.
  - returns: True, if state change succeeded, otherwise false.
- `Requeue([NotNull] this IBackgroundJobClient, [NotNull] string)`
- `Requeue([NotNull] this IBackgroundJobClient, [NotNull] string, [CanBeNull] string)`
- `Reschedule(Hangfire.IBackgroundJobClient, string, DateTimeOffset)`
  - Changes state of a job with the specified jobId
to the `ScheduledState`.
  - `client`: An instance of `IBackgroundJobClient` implementation.
  - `jobId`: Identifier of job, whose state is being changed.
  - `enqueueAt`: Moment of time at which the job will be rescheduled.
  - returns: True, if state change succeeded, otherwise false.
- `Reschedule(Hangfire.IBackgroundJobClient, string, DateTimeOffset, string)`
  - Changes state of a job with the specified jobId
to the `ScheduledState`. If fromState value
is not null, state change will be performed only if the current state name
of a job equal to the given value.
  - `client`: An instance of `IBackgroundJobClient` implementation.
  - `jobId`: Identifier of job, whose state is being changed.
  - `enqueueAt`: Moment of time at which the job will be rescheduled.
  - `fromState`: Current state assertion, or null if unneeded.
  - returns: True, if state change succeeded, otherwise false.
- `Reschedule(Hangfire.IBackgroundJobClient, string, TimeSpan)`
  - Changes state of a job with the specified jobId
to the `ScheduledState`.
  - `client`: An instance of `IBackgroundJobClient` implementation.
  - `jobId`: Identifier of job, whose state is being changed.
  - `delay`: Delay, after which the job will be rescheduled.
  - returns: True, if state change succeeded, otherwise false.
- `Reschedule(Hangfire.IBackgroundJobClient, string, TimeSpan, string)`
  - Changes state of a job with the specified jobId
to the `ScheduledState`. If fromState value
is not null, state change will be performed only if the current state name
of a job equal to the given value.
  - `client`: An instance of `IBackgroundJobClient` implementation.
  - `jobId`: Identifier of job, whose state is being changed.
  - `delay`: Delay, after which the job will be rescheduled.
  - `fromState`: Current state assertion, or null if unneeded.
  - returns: True, if state change succeeded, otherwise false.
- `Reschedule([NotNull] this IBackgroundJobClient, [NotNull] string, DateTimeOffset)`
- `Reschedule([NotNull] this IBackgroundJobClient, [NotNull] string, DateTimeOffset, [CanBeNull] string)`
- `Reschedule([NotNull] this IBackgroundJobClient, [NotNull] string, TimeSpan)`
- `Reschedule([NotNull] this IBackgroundJobClient, [NotNull] string, TimeSpan, [CanBeNull] string)`
- `Schedule(Hangfire.IBackgroundJobClient, Expressions.Expression<Action>, DateTimeOffset)`
  - Creates a new background job based on a specified lambda expression
and schedules it to be enqueued at the specified moment of time.
  - `client`: A job client instance.
  - `methodCall`: Method call expression that will be marshalled to the Server.
  - `enqueueAt`: Moment of time at which the job will be enqueued.
  - returns: Unique identifier or a created job.
- `Schedule(Hangfire.IBackgroundJobClient, Expressions.Expression<Action>, TimeSpan)`
  - Creates a new background job based on a specified lambda expression
and schedules it to be enqueued after a given delay.
  - `client`: A job client instance.
  - `methodCall`: Instance method call expression that will be marshalled to the Server.
  - `delay`: Delay, after which the job will be enqueued.
  - returns: Unique identifier of the created job.
- `Schedule(Hangfire.IBackgroundJobClient, Expressions.Expression<Func<Tasks.Task>>, DateTimeOffset)`
  - Creates a new background job based on a specified lambda expression
and schedules it to be enqueued at the specified moment of time.
  - `client`: A job client instance.
  - `methodCall`: Method call expression that will be marshalled to the Server.
  - `enqueueAt`: Moment of time at which the job will be enqueued.
  - returns: Unique identifier or a created job.
- `Schedule(Hangfire.IBackgroundJobClient, Expressions.Expression<Func<Tasks.Task>>, TimeSpan)`
  - Creates a new background job based on a specified lambda expression
and schedules it to be enqueued after a given delay.
  - `client`: A job client instance.
  - `methodCall`: Instance method call expression that will be marshalled to the Server.
  - `delay`: Delay, after which the job will be enqueued.
  - returns: Unique identifier of the created job.
- `Schedule(Hangfire.IBackgroundJobClient, string, Expressions.Expression<Action>, DateTimeOffset)`
  - Creates a new background job based on a specified lambda expression and schedules it
to be enqueued to the specified queue at the specified moment of time.
  - `client`: A job client instance.
  - `queue`: Default queue for the background job.
  - `methodCall`: Method call expression that will be marshalled to the Server.
  - `enqueueAt`: Moment of time at which the job will be enqueued.
  - returns: Unique identifier or a created job.
- `Schedule(Hangfire.IBackgroundJobClient, string, Expressions.Expression<Action>, TimeSpan)`
  - Creates a new background job based on a specified lambda expression and schedules it
to be enqueued to the specified queue after a given delay.
  - `client`: A job client instance.
  - `queue`: Default queue for the background job.
  - `methodCall`: Instance method call expression that will be marshalled to the Server.
  - `delay`: Delay, after which the job will be enqueued.
  - returns: Unique identifier of the created job.
- `Schedule(Hangfire.IBackgroundJobClient, string, Expressions.Expression<Func<Tasks.Task>>, DateTimeOffset)`
  - Creates a new background job based on a specified lambda expression and schedules it
to be enqueued to the specified queue at the specified moment of time.
  - `client`: A job client instance.
  - `queue`: Default queue for the background job.
  - `methodCall`: Method call expression that will be marshalled to the Server.
  - `enqueueAt`: Moment of time at which the job will be enqueued.
  - returns: Unique identifier or a created job.
- `Schedule(Hangfire.IBackgroundJobClient, string, Expressions.Expression<Func<Tasks.Task>>, TimeSpan)`
  - Creates a new background job based on a specified lambda expression and schedules it
to be enqueued to the specified queue after a given delay.
  - `client`: A job client instance.
  - `queue`: Default queue for the background job.
  - `methodCall`: Instance method call expression that will be marshalled to the Server.
  - `delay`: Delay, after which the job will be enqueued.
  - returns: Unique identifier of the created job.
- `Schedule([NotNull] this IBackgroundJobClient, [NotNull, InstantHandle] Expression<Action>, DateTimeOffset)`
- `Schedule([NotNull] this IBackgroundJobClient, [NotNull, InstantHandle] Expression<Action>, TimeSpan)`
- `Schedule([NotNull] this IBackgroundJobClient, [NotNull, InstantHandle] Expression<Func<Task>>, DateTimeOffset)`
- `Schedule([NotNull] this IBackgroundJobClient, [NotNull, InstantHandle] Expression<Func<Task>>, TimeSpan)`
- `Schedule([NotNull] this IBackgroundJobClient, [NotNull] string, [NotNull, InstantHandle] Expression<Action>, DateTimeOffset)`
- `Schedule([NotNull] this IBackgroundJobClient, [NotNull] string, [NotNull, InstantHandle] Expression<Action>, TimeSpan)`
- `Schedule([NotNull] this IBackgroundJobClient, [NotNull] string, [NotNull, InstantHandle] Expression<Func<Task>>, DateTimeOffset)`
- `Schedule([NotNull] this IBackgroundJobClient, [NotNull] string, [NotNull, InstantHandle] Expression<Func<Task>>, TimeSpan)`
- `Schedule<T>(Hangfire.IBackgroundJobClient, Expressions.Expression<Action<T1>>, DateTimeOffset)`
  - Creates a new background job based on a specified lambda expression and schedules
it to be enqueued at the specified moment.
  - `client`: A job client instance.
  - `methodCall`: Method call expression that will be marshalled to the Server.
  - `enqueueAt`: Moment at which the job will be enqueued.
  - `<T>`: Type whose method will be invoked during job processing.
  - returns: Unique identifier of a created job.
- `Schedule<T>(Hangfire.IBackgroundJobClient, Expressions.Expression<Action<T1>>, TimeSpan)`
  - Creates a new background job based on a specified instance method
call expression and schedules it to be enqueued after a given delay.
  - `client`: A job client instance.
  - `methodCall`: Instance method call expression that will be marshalled to the Server.
  - `delay`: Delay, after which the job will be enqueued.
  - `<T>`: Type whose method will be invoked during job processing.
  - returns: Unique identifier of the created job.
- `Schedule<T>(Hangfire.IBackgroundJobClient, Expressions.Expression<Func<T1,Tasks.Task>>, DateTimeOffset)`
  - Creates a new background job based on a specified lambda expression and schedules
it to be enqueued at the specified moment.
  - `client`: A job client instance.
  - `methodCall`: Method call expression that will be marshalled to the Server.
  - `enqueueAt`: Moment at which the job will be enqueued.
  - `<T>`: Type whose method will be invoked during job processing.
  - returns: Unique identifier of a created job.
- `Schedule<T>(Hangfire.IBackgroundJobClient, Expressions.Expression<Func<T1,Tasks.Task>>, TimeSpan)`
  - Creates a new background job based on a specified instance method
call expression and schedules it to be enqueued after a given delay.
  - `client`: A job client instance.
  - `methodCall`: Instance method call expression that will be marshalled to the Server.
  - `delay`: Delay, after which the job will be enqueued.
  - `<T>`: Type whose method will be invoked during job processing.
  - returns: Unique identifier of the created job.
- `Schedule<T>(Hangfire.IBackgroundJobClient, string, Expressions.Expression<Action<T1>>, DateTimeOffset)`
  - Creates a new background job based on a specified lambda expression and schedules
it to be enqueued to the specified queue at the specified moment.
  - `client`: A job client instance.
  - `queue`: Default queue for the background job.
  - `methodCall`: Method call expression that will be marshalled to the Server.
  - `enqueueAt`: Moment at which the job will be enqueued.
  - `<T>`: Type whose method will be invoked during job processing.
  - returns: Unique identifier of a created job.
- `Schedule<T>(Hangfire.IBackgroundJobClient, string, Expressions.Expression<Action<T1>>, TimeSpan)`
  - Creates a new background job based on a specified instance method call expression and
schedules it to be enqueued to the specified queue after a given delay.
  - `client`: A job client instance.
  - `queue`: Default queue for the background job.
  - `methodCall`: Instance method call expression that will be marshalled to the Server.
  - `delay`: Delay, after which the job will be enqueued.
  - `<T>`: Type whose method will be invoked during job processing.
  - returns: Unique identifier of the created job.
- `Schedule<T>(Hangfire.IBackgroundJobClient, string, Expressions.Expression<Func<T1,Tasks.Task>>, DateTimeOffset)`
  - Creates a new background job based on a specified lambda expression and schedules
it to be enqueued to the specified queue at the specified moment.
  - `client`: A job client instance.
  - `queue`: Default queue for the background job.
  - `methodCall`: Method call expression that will be marshalled to the Server.
  - `enqueueAt`: Moment at which the job will be enqueued.
  - `<T>`: Type whose method will be invoked during job processing.
  - returns: Unique identifier of a created job.
- `Schedule<T>(Hangfire.IBackgroundJobClient, string, Expressions.Expression<Func<T1,Tasks.Task>>, TimeSpan)`
  - Creates a new background job based on a specified instance method call expression and
schedules it to be enqueued to the specified queue after a given delay.
  - `client`: A job client instance.
  - `queue`: Default queue for the background job.
  - `methodCall`: Instance method call expression that will be marshalled to the Server.
  - `delay`: Delay, after which the job will be enqueued.
  - `<T>`: Type whose method will be invoked during job processing.
  - returns: Unique identifier of the created job.
- `Schedule<T>([NotNull] this IBackgroundJobClient, [NotNull, InstantHandle] Expression<Action<T>>, DateTimeOffset)`
- `Schedule<T>([NotNull] this IBackgroundJobClient, [NotNull, InstantHandle] Expression<Action<T>>, TimeSpan)`
- `Schedule<T>([NotNull] this IBackgroundJobClient, [NotNull, InstantHandle] Expression<Func<T, Task>>, DateTimeOffset)`
- `Schedule<T>([NotNull] this IBackgroundJobClient, [NotNull, InstantHandle] Expression<Func<T, Task>>, TimeSpan)`
- `Schedule<T>([NotNull] this IBackgroundJobClient, [NotNull] string, [NotNull, InstantHandle] Expression<Action<T>>, DateTimeOffset)`
- `Schedule<T>([NotNull] this IBackgroundJobClient, [NotNull] string, [NotNull, InstantHandle] Expression<Action<T>>, TimeSpan)`
- `Schedule<T>([NotNull] this IBackgroundJobClient, [NotNull] string, [NotNull, InstantHandle] Expression<Func<T, Task>>, DateTimeOffset)`
- `Schedule<T>([NotNull] this IBackgroundJobClient, [NotNull] string, [NotNull, InstantHandle] Expression<Func<T, Task>>, TimeSpan)`


#### `BackgroundJobServer`

**Methods:**

- `#ctor`
  - Initializes a new instance of the `BackgroundJobServer` class
with default options and `Current` storage.
- `#ctor(Hangfire.BackgroundJobServerOptions)`
  - Initializes a new instance of the `BackgroundJobServer` class
with the given options and `Current` storage.
  - `options`: Server options
- `#ctor(Hangfire.BackgroundJobServerOptions, Hangfire.JobStorage)`
  - Initializes a new instance of the `BackgroundJobServer` class
with the specified options and the given storage.
  - `options`: Server options
  - `storage`: The storage
- `#ctor(Hangfire.JobStorage)`
  - Initializes a new instance of the `BackgroundJobServer` class
with default options and the given storage.
  - `storage`: The storage
- `#ctor([NotNull] BackgroundJobServerOptions)`
- `#ctor([NotNull] BackgroundJobServerOptions, [NotNull] JobStorage)`
- `#ctor([NotNull] BackgroundJobServerOptions, [NotNull] JobStorage, [NotNull] IEnumerable<IBackgroundProcess>)`
- `#ctor([NotNull] BackgroundJobServerOptions, [NotNull] JobStorage, [NotNull] IEnumerable<IBackgroundProcess>, [CanBeNull] IJobFilterProvider, [CanBeNull] JobActivator, [CanBeNull] IBackgroundJobFactory, [CanBeNull] IBackgroundJobPerformer, [CanBeNull] IBackgroundJobStateChanger)`
- `#ctor([NotNull] JobStorage)`
- `Dispose`
- `SendStop`
- `Start`
- `Stop`
- `Stop(bool)`
- `WaitForShutdown(TimeSpan)`
- `WaitForShutdownAsync(CancellationToken)`


#### `BackgroundJobServerOptions`

**Methods:**

- `#ctor`

**Properties:**

- `Activator`
- `CancellationCheckInterval`
- `FilterProvider`
- `HeartbeatInterval`
- `IsLightweightServer`
  - Gets or sets whether storage instance will include only `Worker` and required
`ServerWatchdog` and `ServerJobCancellationWatcher` processes. No
storage-related processes or recurring/delayed job schedulers will be included.
- `MaxDegreeOfParallelismForSchedulers`
  - Experimental option for schedulers, but not for workers. Gets or sets the
maximum degree of parallelism for `RecurringJobScheduler`
and `DelayedJobScheduler` processes, allowing them to enable
parallel scheduling of recurring and delayed jobs when the specified value
is greater than `1`. Parallel work items are executed on the task scheduler
specified in the `TaskScheduler` property.
- `Queues`
- `SchedulePollingInterval`
- `ServerCheckInterval`
- `ServerName`
- `ServerTimeout`
- `ServerWatchdogOptions`
- `ShutdownTimeout`
- `StopTimeout`
- `TaskScheduler`
- `TimeZoneResolver`
- `WorkerCount`
- `WorkerThreadConfigurationAction`


#### `BootstrapperConfigurationExtensions`

**Methods:**

- `UseServer(IBootstrapperConfiguration)`
- `UseServer(IBootstrapperConfiguration, BackgroundJobServerOptions)`
- `UseServer(IBootstrapperConfiguration, JobStorage)`
- `UseServer(IBootstrapperConfiguration, JobStorage, BackgroundJobServerOptions)`
- `UseServer(IBootstrapperConfiguration, int)`
- `UseServer(IBootstrapperConfiguration, int, string[])`
- `UseServer(IBootstrapperConfiguration, string[])`


#### `CaptureCultureAttribute`

**Methods:**

- `#ctor`
- `#ctor([CanBeNull] string, [CanBeNull] string, bool)`
- `#ctor([CanBeNull] string, bool)`
- `OnCreated(CreatedContext)`
- `OnCreating(CreatingContext)`
- `OnPerformed(PerformedContext)`
- `OnPerforming(PerformingContext)`

**Properties:**

- `CachedCulture`
  - Gets or sets whether to use the `GetCultureInfo` method when getting
a culture by its name, or create a `CultureInfo` instance using its
constructor instead. Cached method does not respect user-overridden values associated
with the current culture specified on the OS level.
- `CaptureDefault`
- `DefaultCultureName`
- `DefaultUICultureName`


#### `CompatibilityLevel`

**Fields:**

- `Version_110`
- `Version_170`
- `Version_180`


#### `CompatibilityLevelExtensions`

**Methods:**

- `SetDataCompatibilityLevel([NotNull] this IGlobalConfiguration, CompatibilityLevel)`


#### `ContinuationsSupportAttribute`

**Methods:**

- `#ctor`
- `#ctor(HashSet<string>)`
- `#ctor([NotNull] HashSet<string>, [NotNull] IBackgroundJobStateChanger)`
- `#ctor(bool)`
- `#ctor(bool, HashSet<string>)`
- `#ctor(bool, [NotNull] HashSet<string>, [NotNull] IBackgroundJobStateChanger)`
- `OnStateApplied(ApplyStateContext, IWriteOnlyTransaction)`
- `OnStateElection(ElectStateContext)`


#### `Cron`

Helper class that provides common values for the cron expressions.

**Methods:**

- `Daily`
  - Returns cron expression that fires every day at 00:00 UTC.
- `Daily(int)`
  - Returns cron expression that fires every day at the first minute of
the specified hour in UTC.
  - `hour`: The hour in which the schedule will be activated (0-23).
- `Daily(int, int)`
  - Returns cron expression that fires every day at the specified hour and minute
in UTC.
  - `hour`: The hour in which the schedule will be activated (0-23).
  - `minute`: The minute in which the schedule will be activated (0-59).
- `DayInterval(int)`
  - Returns cron expression that fires every interval days.
  - `interval`: The number of days to wait between every activation.
  - remarks: Please note that only those intervals into which the number 30 is evenly divisible make sense
in Cron expressions, such as 2, 5, 6, 10, 15, etc. Intervals such as 7, 13, 25 will not work
correctly. However, even in this case the actual intervals may be longer in months with
31 or 28 days.
- `GetDescription(string)`
- `HourInterval(int)`
  - Returns cron expression that fires every interval hours.
  - `interval`: The number of hours to wait between every activation.
  - remarks: Please note that only those intervals into which the number 24 is evenly divisible make sense
in Cron expressions, such as 2, 4, 6, 8, 12, etc. Intervals such as 7, 13, 25 will not work
correctly.
- `Hourly`
  - Returns cron expression that fires every hour at the first minute.
- `Hourly(int)`
  - Returns cron expression that fires every hour at the specified minute.
  - `minute`: The minute in which the schedule will be activated (0-59).
- `MinuteInterval(int)`
  - Returns cron expression that fires every interval minutes.
  - `interval`: The number of minutes to wait between every activation.
  - remarks: Please note that only those intervals into which the number 60 is evenly divisible make sense
in Cron expressions, such as 2, 5, 10, 15, 30, etc. Intervals such as 7, 13, 25 will not work
correctly.
- `Minutely`
  - Returns cron expression that fires every minute.
- `MonthInterval(int)`
  - Returns cron expression that fires every interval months.
  - `interval`: The number of months to wait between every activation.
  - remarks: Please note that only those intervals into which the number 12 is evenly divisible make sense
in Cron expressions, such as 2, 3, 4, 6. Intervals such as 7, 13, 25 will not work correctly.
- `Monthly`
  - Returns cron expression that fires every month at 00:00 UTC of the first
day of month.
- `Monthly(int)`
  - Returns cron expression that fires every month at 00:00 UTC of the specified
day of month.
  - `day`: The day of month in which the schedule will be activated (1-31).
- `Monthly(int, int)`
  - Returns cron expression that fires every month at the first minute of the
specified day of month and hour in UTC.
  - `day`: The day of month in which the schedule will be activated (1-31).
  - `hour`: The hour in which the schedule will be activated (0-23).
- `Monthly(int, int, int)`
  - Returns cron expression that fires every month at the specified day of month,
hour and minute in UTC.
  - `day`: The day of month in which the schedule will be activated (1-31).
  - `hour`: The hour in which the schedule will be activated (0-23).
  - `minute`: The minute in which the schedule will be activated (0-59).
- `Never`
  - Returns cron expression that never fires. Specifically 31st of February.
- `Weekly`
  - Returns cron expression that fires every week at Monday, 00:00 UTC.
- `Weekly(DayOfWeek)`
  - Returns cron expression that fires every week at 00:00 UTC of the specified
day of the week.
  - `dayOfWeek`: The day of week in which the schedule will be activated.
- `Weekly(DayOfWeek, int)`
  - Returns cron expression that fires every week at the first minute
of the specified day of week and hour in UTC.
  - `dayOfWeek`: The day of week in which the schedule will be activated.
  - `hour`: The hour in which the schedule will be activated (0-23).
- `Weekly(DayOfWeek, int, int)`
  - Returns cron expression that fires every week at the specified day
of week, hour and minute in UTC.
  - `dayOfWeek`: The day of week in which the schedule will be activated.
  - `hour`: The hour in which the schedule will be activated (0-23).
  - `minute`: The minute in which the schedule will be activated (0-59).
- `Yearly`
  - Returns cron expression that fires every year on Jan, 1st at 00:00 UTC.
- `Yearly(int)`
  - Returns cron expression that fires every year in the first day at 00:00 UTC
of the specified month.
  - `month`: The month in which the schedule will be activated (1-12).
- `Yearly(int, int)`
  - Returns cron expression that fires every year at 00:00 UTC of the specified
month and day of month.
  - `month`: The month in which the schedule will be activated (1-12).
  - `day`: The day of month in which the schedule will be activated (1-31).
- `Yearly(int, int, int)`
  - Returns cron expression that fires every year at the first minute of the
specified month, day and hour in UTC.
  - `month`: The month in which the schedule will be activated (1-12).
  - `day`: The day of month in which the schedule will be activated (1-31).
  - `hour`: The hour in which the schedule will be activated (0-23).
- `Yearly(int, int, int, int)`
  - Returns cron expression that fires every year at the specified month, day,
hour and minute in UTC.
  - `month`: The month in which the schedule will be activated (1-12).
  - `day`: The day of month in which the schedule will be activated (1-31).
  - `hour`: The hour in which the schedule will be activated (0-23).
  - `minute`: The minute in which the schedule will be activated (0-59).


#### `DashboardOptions`

**Methods:**

- `#ctor`

**Properties:**

- `AppPath`
  - The path for the Back To Site link. Set to in order to hide the Back To Site link.
- `AsyncAuthorization`
- `Authorization`
- `AuthorizationFilters`
- `DarkModeEnabled`
  - Gets or sets whether dark mode support is enabled by including
or excluding the corresponding CSS files.
- `DashboardTitle`
  - The Title displayed on the dashboard, optionally modify to describe this dashboards purpose.
- `DefaultRecordsPerPage`
  - Gets or sets the default number of records per page.
- `DisplayNameFunc`
  - Display name provider for jobs
- `DisplayStorageConnectionString`
- `FaviconPath`
  - Optional favicon path
- `IgnoreAntiforgeryToken`
- `IsReadOnlyFunc`
- `PrefixPath`
  - The path for the first url prefix link, eg. set "/admin", then url is "{domain}/{PrefixPath}/{hangfire}"
- `ServerPossiblyAbortedThreshold`
  - Gets or sets the time threshold after which a warning icon will be shown near a job or a
server, depending on its last reported heartbeat.
  - remarks: It should be larger than a configured `HeartbeatInterval`
value, to give servers a chance to report it, but is expected to be lower than a configured
`ServerTimeout` value, since this is a heuristic anyway.
- `StatsPollingInterval`
  - The interval the /stats endpoint should be polled with.
- `TimeZoneResolver`


#### `DefaultTimeZoneResolver`

**Methods:**

- `GetTimeZoneById(string)`


#### `DisableConcurrentExecutionAttribute`

**Methods:**

- `#ctor(int)`
- `#ctor(string, int)`
- `OnPerformed(PerformedContext)`
- `OnPerforming(PerformingContext)`

**Properties:**

- `Resource`
- `TimeoutSec`


#### `ExceptionInfo`

**Methods:**

- `#ctor([NotNull] Exception)`
- `#ctor([NotNull] string, [CanBeNull] string, [CanBeNull] ExceptionInfo)`
- `ToString`

**Properties:**

- `InnerException`
- `Message`
- `Type`


#### `FromExceptionAttribute`

**Methods:**

- `#ctor`


#### `FromParameterAttribute`

**Methods:**

- `#ctor(string)`

**Properties:**

- `ParameterName`


#### `FromResultAttribute`

**Methods:**

- `#ctor`


#### `GlobalConfiguration`

**Properties:**

- `Configuration`


#### `GlobalConfigurationExtensions`

**Methods:**

- `Use<T>([NotNull] this IGlobalConfiguration, T, [NotNull] Action<T>)`
- `UseActivator<T>([NotNull] this IGlobalConfiguration, [NotNull] TActivator)`
- `UseColouredConsoleLogProvider([NotNull] this IGlobalConfiguration)`
- `UseColouredConsoleLogProvider([NotNull] this IGlobalConfiguration, LogLevel)`
- `UseDashboardJavaScript([NotNull] this IGlobalConfiguration, [NotNull] Assembly, [NotNull] string)`
- `UseDashboardMetric([NotNull] this IGlobalConfiguration, [NotNull] DashboardMetric)`
- `UseDashboardMetrics([NotNull] this IGlobalConfiguration, [NotNull] params DashboardMetric[])`
- `UseDashboardStylesheet([NotNull] this IGlobalConfiguration, [NotNull] Assembly, [NotNull] string)`
- `UseDashboardStylesheetDarkMode([NotNull] this IGlobalConfiguration, [NotNull] Assembly, [NotNull] string)`
- `UseDefaultActivator([NotNull] this IGlobalConfiguration)`
- `UseDefaultCulture([NotNull] this IGlobalConfiguration, [CanBeNull] CultureInfo)`
- `UseDefaultCulture([NotNull] this IGlobalConfiguration, [CanBeNull] CultureInfo, [CanBeNull] CultureInfo)`
- `UseDefaultCulture([NotNull] this IGlobalConfiguration, [CanBeNull] CultureInfo, [CanBeNull] CultureInfo, bool)`
- `UseDefaultCulture([NotNull] this IGlobalConfiguration, [CanBeNull] CultureInfo, bool)`
- `UseDefaultTypeResolver([NotNull] this IGlobalConfiguration)`
- `UseDefaultTypeSerializer([NotNull] this IGlobalConfiguration)`
- `UseElmahLogProvider([NotNull] this IGlobalConfiguration)`
- `UseElmahLogProvider([NotNull] this IGlobalConfiguration, LogLevel)`
- `UseEntLibLogProvider([NotNull] this IGlobalConfiguration)`
- `UseFilter<T>([NotNull] this IGlobalConfiguration, [NotNull] TFilter)`
- `UseFilterProvider<T>([NotNull] this IGlobalConfiguration, [NotNull] TFilterProvider)`
- `UseIgnoredAssemblyVersionTypeResolver([NotNull] this IGlobalConfiguration)`
- `UseJobDetailsRenderer([NotNull] this IGlobalConfiguration, int, [NotNull] Func<JobDetailsRendererDto, NonEscapedString>)`
- `UseLog4NetLogProvider([NotNull] this IGlobalConfiguration)`
- `UseLogProvider<T>([NotNull] this IGlobalConfiguration, [NotNull] TLogProvider)`
- `UseLoupeLogProvider([NotNull] this IGlobalConfiguration)`
- `UseMaxArgumentSizeToRender([NotNull] this IGlobalConfiguration, int)`
- `UseMaxLinesInExceptionDetails([NotNull] this IGlobalConfiguration, [CanBeNull] int?)`
- `UseNLogLogProvider([NotNull] this IGlobalConfiguration)`
- `UseNoOpLogProvider(Hangfire.IGlobalConfiguration)`
  - Explicitly disables all the logging in Hangfire. Not recommended to use in a production
application, because logging provides significant benefits in case of exceptions or other
problems. But it can be useful for testing-related scenarios.
- `UseNoOpLogProvider([NotNull] this IGlobalConfiguration)`
- `UseRecommendedSerializerSettings([NotNull] this IGlobalConfiguration)`
- `UseRecommendedSerializerSettings([NotNull] this IGlobalConfiguration, [CanBeNull] Action<JsonSerializerSettings>)`
- `UseResultsInContinuations(IGlobalConfiguration)`
- `UseSerializerSettings(Hangfire.IGlobalConfiguration, Newtonsoft.Json.JsonSerializerSettings)`
  - These settings are used to serialize user data like arguments or parameters.
You can use `Serialize<T>` with `User` option
to serialize with specified settings
- `UseSerializerSettings([NotNull] this IGlobalConfiguration, [CanBeNull] JsonSerializerSettings)`
- `UseSerilogLogProvider([NotNull] this IGlobalConfiguration)`
- `UseSimpleAssemblyNameTypeSerializer([NotNull] this IGlobalConfiguration)`
- `UseStorage<T>([NotNull] this IGlobalConfiguration, [NotNull] TStorage)`
- `UseTypeResolver([NotNull] this IGlobalConfiguration, [CanBeNull] Func<string, Type>)`
- `UseTypeSerializer([NotNull] this IGlobalConfiguration, [CanBeNull] Func<Type, string>)`
- `WithJobExpirationTimeout<T>([NotNull] this IGlobalConfiguration<TStorage>, TimeSpan)`


#### `GlobalJobFilters`

Represents the global filter collection.

**Properties:**

- `Filters`
  - Gets the global filter collection.


#### `GlobalStateHandlers`

**Properties:**

- `Handlers`


#### `IBackgroundJobClient`

Provides methods for creating background jobs and changing their states.

**Methods:**

- `ChangeState(string, Hangfire.States.IState, string)`
  - Attempts to change a state of a background job with a given
identifier to a specified one.
  - `jobId`: Identifier of background job, whose state should be changed.
  - `state`: New state for a background job.
  - `expectedState`: Expected state assertion, or if unneeded.
  - returns: , if a given state was applied
successfully otherwise .
  - remarks: If expectedState value is not null, state
change will be performed only if the current state name of a job
equal to the given value.



The interface allows implementations to change a state of a
background job to other than specified. The given state instance also
may be modified. For example, `ElectStateContext` class
contains public setter for the `CandidateState`
property allowing to choose completely different state by state
election filters. If a state was changed,
value will be returned.
- `Create(Hangfire.Common.Job, Hangfire.States.IState)`
  - Creates a new background job in a specified state.
  - `job`: Job that should be processed in background.
  - `state`: Initial state for a background job.
  - returns: Unique identifier of a created background job -or-
, if it was not created.
  - remarks: The interface allows implementations to return
value for this method when background job creation has been canceled
by an implementation under the normal circumstances (not due to an
exception). For example, the `CreatingContext` class
contains the `Canceled` property that
may be used by a client filter to cancel a background job creation.



The interface allows implementations to create a background
job in a state other than specified. The given state instance also
may be modified. For example, `ElectStateContext` class
contains public setter for the `CandidateState`
property allowing to choose completely different state by state
election filters.


#### `IBackgroundJobClientV2`

Provides extended methods for creating background jobs and changing
their states.

**Methods:**

- `Create(Hangfire.Common.Job, Hangfire.States.IState, Generic.IDictionary<string,object>)`
  - Creates a background job within the specified state and given job parameters.
  - `job`: Job that should be processed in background.
  - `state`: Initial state for a background job.
  - `parameters`: Job parameters to create.
  - returns: Unique identifier of a created background job -or-
, if it was not created.

**Properties:**

- `Storage`
  - Gets a storage associated with the current background job client.


#### `IBootstrapperConfiguration`


#### `IGlobalConfiguration`


#### `IGlobalConfiguration<T>`


#### `IJobCancellationToken`

**Methods:**

- `ThrowIfCancellationRequested`
  - Throws a `OperationCanceledException` if
this token has had cancellation requested.
  - remarks: This method provides functionality equivalent to:
`if (token.ShutdownToken.IsCancellationRequested)
throw new OperationCanceledException(token);`


#### `IRecurringJobManager`


#### `IRecurringJobManagerV2`


#### `ITimeZoneResolver`


#### `IdempotentCompletionAttribute`

**Methods:**

- `#ctor`
- `OnStateElection(ElectStateContext)`


#### `JobActivator`

**Methods:**

- `ActivateJob(Type)`
- `BeginScope`
- `BeginScope(JobActivatorContext)`
- `BeginScope(PerformContext)`

**Properties:**

- `Current`
  - Gets or sets the current `JobActivator` instance
that will be used to activate jobs during performance.


#### `JobActivatorContext`

**Methods:**

- `#ctor([NotNull] IStorageConnection, [NotNull] BackgroundJob, [NotNull] IJobCancellationToken)`
- `GetJobParameter<T>([NotNull] string)`
- `GetJobParameter<T>([NotNull] string, bool)`
- `SetJobParameter([NotNull] string, object)`

**Properties:**

- `BackgroundJob`
- `CancellationToken`
- `Connection`


#### `JobActivatorScope`

**Methods:**

- `Dispose`
- `DisposeScope`
- `Resolve(Type)`

**Properties:**

- `InnerScope`

**Fields:**

- `Current`


#### `JobCancellationToken`

**Methods:**

- `#ctor(bool)`
- `ThrowIfCancellationRequested`

**Properties:**

- `ShutdownToken`

**Fields:**

- `Null`


#### `JobContinuationOptions`

**Fields:**

- `OnAnyFinishedState`
- `OnlyOnDeletedState`
- `OnlyOnSucceededState`


#### `JobDisplayNameAttribute`

Specifies a display name for a job method.

**Methods:**

- `#ctor(string)`
- `Format(DashboardContext, Job)`

**Properties:**

- `DisplayName`
  - Gets display name for the job.
- `ResourceType`
  - Gets or sets resource type to localize `DisplayName` string.


#### `JobParameterInjectionFilter`

**Methods:**

- `OnPerformed(PerformedContext)`
- `OnPerforming(PerformingContext)`


#### `JobStorage`

**Methods:**

- `GetComponents`
- `GetConnection`
- `GetMonitoringApi`
- `GetReadOnlyConnection`
- `GetServerRequiredProcesses`
- `GetStateHandlers`
- `GetStorageWideProcesses`
- `HasFeature([NotNull] string)`
- `WriteOptionsToLog(ILog)`

**Properties:**

- `Current`
- `JobExpirationTimeout`

**Fields:**

- `LinearizableReads`


#### `LatencyTimeoutAttribute`

Represents a job filter that automatically deletes a background job,
when a certain amount of time elapsed since its creation. Deletion
is taking place when a `Worker` attempts
to move a job to the `ProcessingState` state.

**Methods:**

- `#ctor(int)`
  - Initializes a new instance of the `LatencyTimeoutAttribute`
class with the given timeout value.
  - `timeoutInSeconds`: Non-negative timeout value in seconds
that will be used to determine whether to delete a job.
- `OnStateElection(ElectStateContext)`
- `OnStateElection(Hangfire.States.ElectStateContext)`

**Properties:**

- `LogLevel`
  - Gets or sets a level for log message that will be produced, when a
background job was deleted due to exceeded timeout.
- `TimeoutInSeconds`


#### `MisfireHandlingMode`

Specifies how to handle missed schedule when processing server was
inactive.

**Fields:**

- `Ignorable`
  - Specifies that no background jobs should be created on missed schedule,
regardless the number of missed occurrences.
- `Relaxed`
  - Default mode. Specifies that only a single background job will
be created, no matter how many occurrences were missed. The "Time"
parameter for the background job will point to the time background
job was scheduled.
- `Strict`
  - Specifies that new background job will be created for every missed
occurrence, with "Time" parameter set to the corresponding schedule
time.


#### `NamespaceDoc`

The `Hangfire` namespace contains high-level types for configuring,
creating and processing background jobs, such as `GlobalConfiguration`,
`BackgroundJob` and `BackgroundJobServer`.


#### `OwinBootstrapper`

**Methods:**

- `UseHangfire([NotNull] this IAppBuilder, [NotNull] Action<IBootstrapperConfiguration>)`


#### `QueueAttribute`

Represents attribute, that is used to determine queue name
for background jobs. It can be applied to the methods and classes.
If the attribute is not applied neither to the method, nor the class,
then default queue will be used.

**Methods:**

- `#ctor(string)`
  - Initializes a new instance of the `QueueAttribute` class
using the specified queue name.
  - `queue`: Queue name.
- `OnStateElection(ElectStateContext)`

**Properties:**

- `Queue`
  - Gets the queue name that will be used for background jobs.


#### `RecurringJob`

**Methods:**

- `AddOrUpdate([NotNull, InstantHandle] Expression<Action>, [NotNull] Func<string>, [CanBeNull] TimeZoneInfo, [NotNull] string)`
- `AddOrUpdate([NotNull, InstantHandle] Expression<Action>, [NotNull] Func<string>, [NotNull] RecurringJobOptions)`
- `AddOrUpdate([NotNull, InstantHandle] Expression<Action>, [NotNull] string, [CanBeNull] TimeZoneInfo, [NotNull] string)`
- `AddOrUpdate([NotNull, InstantHandle] Expression<Action>, [NotNull] string, [NotNull] RecurringJobOptions)`
- `AddOrUpdate([NotNull, InstantHandle] Expression<Func<Task>>, [NotNull] Func<string>, [CanBeNull] TimeZoneInfo, [NotNull] string)`
- `AddOrUpdate([NotNull, InstantHandle] Expression<Func<Task>>, [NotNull] Func<string>, [NotNull] RecurringJobOptions)`
- `AddOrUpdate([NotNull, InstantHandle] Expression<Func<Task>>, [NotNull] string, [CanBeNull] TimeZoneInfo, [NotNull] string)`
- `AddOrUpdate([NotNull, InstantHandle] Expression<Func<Task>>, [NotNull] string, [NotNull] RecurringJobOptions)`
- `AddOrUpdate([NotNull] string, [NotNull, InstantHandle] Expression<Action>, [NotNull] Func<string>)`
- `AddOrUpdate([NotNull] string, [NotNull, InstantHandle] Expression<Action>, [NotNull] Func<string>, [CanBeNull] TimeZoneInfo, [NotNull] string)`
- `AddOrUpdate([NotNull] string, [NotNull, InstantHandle] Expression<Action>, [NotNull] Func<string>, [NotNull] RecurringJobOptions)`
- `AddOrUpdate([NotNull] string, [NotNull, InstantHandle] Expression<Action>, [NotNull] string)`
- `AddOrUpdate([NotNull] string, [NotNull, InstantHandle] Expression<Action>, [NotNull] string, [CanBeNull] TimeZoneInfo, [NotNull] string)`
- `AddOrUpdate([NotNull] string, [NotNull, InstantHandle] Expression<Action>, [NotNull] string, [NotNull] RecurringJobOptions)`
- `AddOrUpdate([NotNull] string, [NotNull, InstantHandle] Expression<Func<Task>>, [NotNull] Func<string>)`
- `AddOrUpdate([NotNull] string, [NotNull, InstantHandle] Expression<Func<Task>>, [NotNull] Func<string>, [CanBeNull] TimeZoneInfo, [NotNull] string)`
- `AddOrUpdate([NotNull] string, [NotNull, InstantHandle] Expression<Func<Task>>, [NotNull] Func<string>, [NotNull] RecurringJobOptions)`
- `AddOrUpdate([NotNull] string, [NotNull, InstantHandle] Expression<Func<Task>>, [NotNull] string)`
- `AddOrUpdate([NotNull] string, [NotNull, InstantHandle] Expression<Func<Task>>, [NotNull] string, [CanBeNull] TimeZoneInfo, [NotNull] string)`
- `AddOrUpdate([NotNull] string, [NotNull, InstantHandle] Expression<Func<Task>>, [NotNull] string, [NotNull] RecurringJobOptions)`
- `AddOrUpdate([NotNull] string, [NotNull] string, [NotNull, InstantHandle] Expression<Action>, [NotNull] Func<string>)`
- `AddOrUpdate([NotNull] string, [NotNull] string, [NotNull, InstantHandle] Expression<Action>, [NotNull] Func<string>, [NotNull] RecurringJobOptions)`
- `AddOrUpdate([NotNull] string, [NotNull] string, [NotNull, InstantHandle] Expression<Action>, [NotNull] string)`
- `AddOrUpdate([NotNull] string, [NotNull] string, [NotNull, InstantHandle] Expression<Action>, [NotNull] string, [NotNull] RecurringJobOptions)`
- `AddOrUpdate([NotNull] string, [NotNull] string, [NotNull, InstantHandle] Expression<Func<Task>>, [NotNull] Func<string>)`
- `AddOrUpdate([NotNull] string, [NotNull] string, [NotNull, InstantHandle] Expression<Func<Task>>, [NotNull] Func<string>, [NotNull] RecurringJobOptions)`
- `AddOrUpdate([NotNull] string, [NotNull] string, [NotNull, InstantHandle] Expression<Func<Task>>, [NotNull] string)`
- `AddOrUpdate([NotNull] string, [NotNull] string, [NotNull, InstantHandle] Expression<Func<Task>>, [NotNull] string, [NotNull] RecurringJobOptions)`
- `AddOrUpdate<T>([NotNull, InstantHandle] Expression<Action<T>>, [NotNull] Func<string>, [CanBeNull] TimeZoneInfo, [NotNull] string)`
- `AddOrUpdate<T>([NotNull, InstantHandle] Expression<Action<T>>, [NotNull] Func<string>, [NotNull] RecurringJobOptions)`
- `AddOrUpdate<T>([NotNull, InstantHandle] Expression<Action<T>>, [NotNull] string, [CanBeNull] TimeZoneInfo, [NotNull] string)`
- `AddOrUpdate<T>([NotNull, InstantHandle] Expression<Action<T>>, [NotNull] string, [NotNull] RecurringJobOptions)`
- `AddOrUpdate<T>([NotNull, InstantHandle] Expression<Func<T, Task>>, [NotNull] Func<string>, [CanBeNull] TimeZoneInfo, [NotNull] string)`
- `AddOrUpdate<T>([NotNull, InstantHandle] Expression<Func<T, Task>>, [NotNull] Func<string>, [NotNull] RecurringJobOptions)`
- `AddOrUpdate<T>([NotNull, InstantHandle] Expression<Func<T, Task>>, [NotNull] string, [CanBeNull] TimeZoneInfo, [NotNull] string)`
- `AddOrUpdate<T>([NotNull, InstantHandle] Expression<Func<T, Task>>, [NotNull] string, [NotNull] RecurringJobOptions)`
- `AddOrUpdate<T>([NotNull] string, [NotNull, InstantHandle] Expression<Action<T>>, [NotNull] Func<string>)`
- `AddOrUpdate<T>([NotNull] string, [NotNull, InstantHandle] Expression<Action<T>>, [NotNull] Func<string>, [CanBeNull] TimeZoneInfo, [NotNull] string)`
- `AddOrUpdate<T>([NotNull] string, [NotNull, InstantHandle] Expression<Action<T>>, [NotNull] Func<string>, [NotNull] RecurringJobOptions)`
- `AddOrUpdate<T>([NotNull] string, [NotNull, InstantHandle] Expression<Action<T>>, [NotNull] string)`
- `AddOrUpdate<T>([NotNull] string, [NotNull, InstantHandle] Expression<Action<T>>, [NotNull] string, [CanBeNull] TimeZoneInfo, [NotNull] string)`
- `AddOrUpdate<T>([NotNull] string, [NotNull, InstantHandle] Expression<Action<T>>, [NotNull] string, [NotNull] RecurringJobOptions)`
- `AddOrUpdate<T>([NotNull] string, [NotNull, InstantHandle] Expression<Func<T, Task>>, [NotNull] Func<string>)`
- `AddOrUpdate<T>([NotNull] string, [NotNull, InstantHandle] Expression<Func<T, Task>>, [NotNull] Func<string>, [CanBeNull] TimeZoneInfo, [NotNull] string)`
- `AddOrUpdate<T>([NotNull] string, [NotNull, InstantHandle] Expression<Func<T, Task>>, [NotNull] Func<string>, [NotNull] RecurringJobOptions)`
- `AddOrUpdate<T>([NotNull] string, [NotNull, InstantHandle] Expression<Func<T, Task>>, [NotNull] string)`
- `AddOrUpdate<T>([NotNull] string, [NotNull, InstantHandle] Expression<Func<T, Task>>, [NotNull] string, [CanBeNull] TimeZoneInfo, [NotNull] string)`
- `AddOrUpdate<T>([NotNull] string, [NotNull, InstantHandle] Expression<Func<T, Task>>, [NotNull] string, [NotNull] RecurringJobOptions)`
- `AddOrUpdate<T>([NotNull] string, [NotNull] string, [NotNull, InstantHandle] Expression<Action<T>>, [NotNull] Func<string>)`
- `AddOrUpdate<T>([NotNull] string, [NotNull] string, [NotNull, InstantHandle] Expression<Action<T>>, [NotNull] Func<string>, [NotNull] RecurringJobOptions)`
- `AddOrUpdate<T>([NotNull] string, [NotNull] string, [NotNull, InstantHandle] Expression<Action<T>>, [NotNull] string)`
- `AddOrUpdate<T>([NotNull] string, [NotNull] string, [NotNull, InstantHandle] Expression<Action<T>>, [NotNull] string, [NotNull] RecurringJobOptions)`
- `AddOrUpdate<T>([NotNull] string, [NotNull] string, [NotNull, InstantHandle] Expression<Func<T, Task>>, [NotNull] Func<string>)`
- `AddOrUpdate<T>([NotNull] string, [NotNull] string, [NotNull, InstantHandle] Expression<Func<T, Task>>, [NotNull] Func<string>, [NotNull] RecurringJobOptions)`
- `AddOrUpdate<T>([NotNull] string, [NotNull] string, [NotNull, InstantHandle] Expression<Func<T, Task>>, [NotNull] string)`
- `AddOrUpdate<T>([NotNull] string, [NotNull] string, [NotNull, InstantHandle] Expression<Func<T, Task>>, [NotNull] string, [NotNull] RecurringJobOptions)`
- `RemoveIfExists([NotNull] string)`
- `Trigger([NotNull] string)`
- `TriggerJob([NotNull] string)`


#### `RecurringJobManager`

Represents a recurring job manager that allows to create, update
or delete recurring jobs.

**Methods:**

- `#ctor`
- `#ctor([NotNull] JobStorage)`
- `#ctor([NotNull] JobStorage, [NotNull] IBackgroundJobFactory)`
- `#ctor([NotNull] JobStorage, [NotNull] IBackgroundJobFactory, [NotNull] ITimeZoneResolver)`
- `#ctor([NotNull] JobStorage, [NotNull] IJobFilterProvider)`
- `#ctor([NotNull] JobStorage, [NotNull] IJobFilterProvider, [NotNull] ITimeZoneResolver)`
- `#ctor([NotNull] JobStorage, [NotNull] IJobFilterProvider, [NotNull] ITimeZoneResolver, [NotNull] Func<DateTime>)`
- `AddOrUpdate(string, Job, string, RecurringJobOptions)`
- `RemoveIfExists(string)`
- `Trigger(string)`
- `TriggerExecution(string)`
- `TriggerJob(string)`

**Fields:**

- `Storage`


#### `RecurringJobManagerExtensions`

**Methods:**

- `AddOrUpdate([NotNull] this IRecurringJobManager, [NotNull] string, [NotNull] Expression<Action>, [NotNull] Func<string>)`
- `AddOrUpdate([NotNull] this IRecurringJobManager, [NotNull] string, [NotNull] Expression<Action>, [NotNull] Func<string>, TimeZoneInfo, string)`
- `AddOrUpdate([NotNull] this IRecurringJobManager, [NotNull] string, [NotNull] Expression<Action>, [NotNull] Func<string>, [NotNull] RecurringJobOptions)`
- `AddOrUpdate([NotNull] this IRecurringJobManager, [NotNull] string, [NotNull] Expression<Action>, [NotNull] string)`
- `AddOrUpdate([NotNull] this IRecurringJobManager, [NotNull] string, [NotNull] Expression<Action>, [NotNull] string, TimeZoneInfo, string)`
- `AddOrUpdate([NotNull] this IRecurringJobManager, [NotNull] string, [NotNull] Expression<Action>, [NotNull] string, [NotNull] RecurringJobOptions)`
- `AddOrUpdate([NotNull] this IRecurringJobManager, [NotNull] string, [NotNull] Expression<Func<Task>>, [NotNull] Func<string>)`
- `AddOrUpdate([NotNull] this IRecurringJobManager, [NotNull] string, [NotNull] Expression<Func<Task>>, [NotNull] Func<string>, TimeZoneInfo, string)`
- `AddOrUpdate([NotNull] this IRecurringJobManager, [NotNull] string, [NotNull] Expression<Func<Task>>, [NotNull] Func<string>, [NotNull] RecurringJobOptions)`
- `AddOrUpdate([NotNull] this IRecurringJobManager, [NotNull] string, [NotNull] Expression<Func<Task>>, [NotNull] string)`
- `AddOrUpdate([NotNull] this IRecurringJobManager, [NotNull] string, [NotNull] Expression<Func<Task>>, [NotNull] string, TimeZoneInfo, string)`
- `AddOrUpdate([NotNull] this IRecurringJobManager, [NotNull] string, [NotNull] Expression<Func<Task>>, [NotNull] string, [NotNull] RecurringJobOptions)`
- `AddOrUpdate([NotNull] this IRecurringJobManager, [NotNull] string, [NotNull] Job, [NotNull] string)`
- `AddOrUpdate([NotNull] this IRecurringJobManager, [NotNull] string, [NotNull] Job, [NotNull] string, [NotNull] TimeZoneInfo)`
- `AddOrUpdate([NotNull] this IRecurringJobManager, [NotNull] string, [NotNull] Job, [NotNull] string, [NotNull] TimeZoneInfo, [NotNull] string)`
- `AddOrUpdate([NotNull] this IRecurringJobManager, [NotNull] string, [NotNull] string, [NotNull] Expression<Action>, [NotNull] Func<string>)`
- `AddOrUpdate([NotNull] this IRecurringJobManager, [NotNull] string, [NotNull] string, [NotNull] Expression<Action>, [NotNull] Func<string>, [NotNull] RecurringJobOptions)`
- `AddOrUpdate([NotNull] this IRecurringJobManager, [NotNull] string, [NotNull] string, [NotNull] Expression<Action>, [NotNull] string)`
- `AddOrUpdate([NotNull] this IRecurringJobManager, [NotNull] string, [NotNull] string, [NotNull] Expression<Action>, [NotNull] string, [NotNull] RecurringJobOptions)`
- `AddOrUpdate([NotNull] this IRecurringJobManager, [NotNull] string, [NotNull] string, [NotNull] Expression<Func<Task>>, [NotNull] Func<string>)`
- `AddOrUpdate([NotNull] this IRecurringJobManager, [NotNull] string, [NotNull] string, [NotNull] Expression<Func<Task>>, [NotNull] Func<string>, [NotNull] RecurringJobOptions)`
- `AddOrUpdate([NotNull] this IRecurringJobManager, [NotNull] string, [NotNull] string, [NotNull] Expression<Func<Task>>, [NotNull] string)`
- `AddOrUpdate([NotNull] this IRecurringJobManager, [NotNull] string, [NotNull] string, [NotNull] Expression<Func<Task>>, [NotNull] string, [NotNull] RecurringJobOptions)`
- `AddOrUpdate<T>([NotNull] this IRecurringJobManager, [NotNull] string, [NotNull] Expression<Action<T>>, [NotNull] Func<string>)`
- `AddOrUpdate<T>([NotNull] this IRecurringJobManager, [NotNull] string, [NotNull] Expression<Action<T>>, [NotNull] Func<string>, TimeZoneInfo, string)`
- `AddOrUpdate<T>([NotNull] this IRecurringJobManager, [NotNull] string, [NotNull] Expression<Action<T>>, [NotNull] Func<string>, [NotNull] RecurringJobOptions)`
- `AddOrUpdate<T>([NotNull] this IRecurringJobManager, [NotNull] string, [NotNull] Expression<Action<T>>, [NotNull] string)`
- `AddOrUpdate<T>([NotNull] this IRecurringJobManager, [NotNull] string, [NotNull] Expression<Action<T>>, [NotNull] string, TimeZoneInfo, string)`
- `AddOrUpdate<T>([NotNull] this IRecurringJobManager, [NotNull] string, [NotNull] Expression<Action<T>>, [NotNull] string, [NotNull] RecurringJobOptions)`
- `AddOrUpdate<T>([NotNull] this IRecurringJobManager, [NotNull] string, [NotNull] Expression<Func<T, Task>>, [NotNull] Func<string>)`
- `AddOrUpdate<T>([NotNull] this IRecurringJobManager, [NotNull] string, [NotNull] Expression<Func<T, Task>>, [NotNull] Func<string>, TimeZoneInfo, string)`
- `AddOrUpdate<T>([NotNull] this IRecurringJobManager, [NotNull] string, [NotNull] Expression<Func<T, Task>>, [NotNull] Func<string>, [NotNull] RecurringJobOptions)`
- `AddOrUpdate<T>([NotNull] this IRecurringJobManager, [NotNull] string, [NotNull] Expression<Func<T, Task>>, [NotNull] string)`
- `AddOrUpdate<T>([NotNull] this IRecurringJobManager, [NotNull] string, [NotNull] Expression<Func<T, Task>>, [NotNull] string, TimeZoneInfo, string)`
- `AddOrUpdate<T>([NotNull] this IRecurringJobManager, [NotNull] string, [NotNull] Expression<Func<T, Task>>, [NotNull] string, [NotNull] RecurringJobOptions)`
- `AddOrUpdate<T>([NotNull] this IRecurringJobManager, [NotNull] string, [NotNull] string, [NotNull] Expression<Action<T>>, [NotNull] Func<string>)`
- `AddOrUpdate<T>([NotNull] this IRecurringJobManager, [NotNull] string, [NotNull] string, [NotNull] Expression<Action<T>>, [NotNull] Func<string>, [NotNull] RecurringJobOptions)`
- `AddOrUpdate<T>([NotNull] this IRecurringJobManager, [NotNull] string, [NotNull] string, [NotNull] Expression<Action<T>>, [NotNull] string)`
- `AddOrUpdate<T>([NotNull] this IRecurringJobManager, [NotNull] string, [NotNull] string, [NotNull] Expression<Action<T>>, [NotNull] string, [NotNull] RecurringJobOptions)`
- `AddOrUpdate<T>([NotNull] this IRecurringJobManager, [NotNull] string, [NotNull] string, [NotNull] Expression<Func<T, Task>>, [NotNull] Func<string>)`
- `AddOrUpdate<T>([NotNull] this IRecurringJobManager, [NotNull] string, [NotNull] string, [NotNull] Expression<Func<T, Task>>, [NotNull] Func<string>, [NotNull] RecurringJobOptions)`
- `AddOrUpdate<T>([NotNull] this IRecurringJobManager, [NotNull] string, [NotNull] string, [NotNull] Expression<Func<T, Task>>, [NotNull] string)`
- `AddOrUpdate<T>([NotNull] this IRecurringJobManager, [NotNull] string, [NotNull] string, [NotNull] Expression<Func<T, Task>>, [NotNull] string, [NotNull] RecurringJobOptions)`


#### `RecurringJobOptions`

**Methods:**

- `#ctor`

**Properties:**

- `MisfireHandling`
- `QueueName`
- `TimeZone`


#### `StatisticsHistoryAttribute`

**Methods:**

- `#ctor`
- `OnStateElection(ElectStateContext)`


### namespace `Hangfire.Annotations`

#### `BaseTypeRequiredAttribute`

When applied to a target attribute, specifies a requirement for any type marked
with the target attribute to implement or inherit specific type or types.


#### `CanBeNullAttribute`

Indicates that the value of the marked element could be `null` sometimes,
so the check for `null` is necessary before its usage


#### `CannotApplyEqualityOperatorAttribute`

Indicates that the value of the marked type (or its derivatives)
cannot be compared using '==' or '!=' operators and `Equals()`
should be used instead. However, using '==' or '!=' for comparison
with `null` is always permitted.


#### `ContractAnnotationAttribute`

Describes dependency between method input and output


#### `ImplicitUseKindFlags`

**Fields:**

- `Access`
  - Only entity marked with attribute considered used
- `Assign`
  - Indicates implicit assignment to a member
- `InstantiatedNoFixedConstructorSignature`
  - Indicates implicit instantiation of a type
- `InstantiatedWithFixedConstructorSignature`
  - Indicates implicit instantiation of a type with fixed constructor signature.
That means any unused constructor parameters won't be reported as such.


#### `ImplicitUseTargetFlags`

Specify what is considered used implicitly
when marked with `MeansImplicitUseAttribute`
or `UsedImplicitlyAttribute`

**Fields:**

- `Members`
  - Members of entity marked with attribute are considered used
- `WithMembers`
  - Entity marked with attribute and all its members considered used


#### `InstantHandleAttribute`

Tells code analysis engine if the parameter is completely handled
when the invoked method is on stack. If the parameter is a delegate,
indicates that delegate is executed while the method is executed.
If the parameter is an enumerable, indicates that it is enumerated
while the method is executed


#### `InvokerParameterNameAttribute`

Indicates that the function argument should be string literal and match one
of the parameters of the caller function. For example, ReSharper annotates
the parameter of `ArgumentNullException`


#### `LocalizationRequiredAttribute`

Indicates that marked element should be localized or not


#### `MeansImplicitUseAttribute`

Should be used on attributes and causes ReSharper
to not mark symbols marked with such attributes as unused
(as well as by other usage inspections)


#### `NamespaceDoc`

The `Annotations` namespace contains attributes that enable
additional code inspections in design time with JetBrains ReSharper.


#### `NotNullAttribute`

Indicates that the value of the marked element could never be `null`


#### `NotifyPropertyChangedInvocatorAttribute`

Indicates that the method is contained in a type that implements
`INotifyPropertyChanged` interface
and this method is used to notify that some property value changed


#### `PublicAPIAttribute`

This attribute is intended to mark publicly available API
which should not be removed and so is treated as used


#### `PureAttribute`

Indicates that a method does not make any observable state changes.
The same as `System.Diagnostics.Contracts.PureAttribute`


#### `StringFormatMethodAttribute`

Indicates that the marked method builds string by format pattern and (optional) arguments.
Parameter, which contains format string, should be given in constructor. The format string
should be in `Format`-like form

**Methods:**

- `#ctor(string)`
  - `formatParameterName`: Specifies which parameter of an annotated method should be treated as format-string


#### `UsedImplicitlyAttribute`

Indicates that the marked symbol is used implicitly
(e.g. via reflection, in external library), so this symbol
will not be marked as unused (as well as by other usage inspections)


### namespace `Hangfire.Client`

#### `BackgroundJobFactory`

**Methods:**

- `#ctor`
- `#ctor([NotNull] IJobFilterProvider)`
- `Create(CreateContext)`

**Properties:**

- `RetryAttempts`

**Fields:**

- `StateMachine`


#### `ClientExceptionContext`

Provides the context for the `OnClientException`
method of the `IClientExceptionFilter` interface.

**Methods:**

- `#ctor(CreateContext, Exception)`

**Properties:**

- `Exception`
  - Gets an exception that occurred during the creation of the job.
- `ExceptionHandled`
  - Gets or sets a value that indicates that this `ClientExceptionContext`
object handles an exception occurred during the creation of the job.


#### `CreateContext`

Provides information about the context in which the job is created.

**Methods:**

- `#ctor([NotNull] CreateContext)`
- `#ctor([NotNull] JobStorage, [NotNull] IStorageConnection, [NotNull] Job, [CanBeNull] IState)`
- `#ctor([NotNull] JobStorage, [NotNull] IStorageConnection, [NotNull] Job, [CanBeNull] IState, [CanBeNull] IDictionary<string, object>)`

**Properties:**

- `Connection`
- `Factory`
- `InitialState`
  - Gets the initial state of the creating job. Note, that
the final state of the created job could be changed after
the registered instances of the `IElectStateFilter`
class are doing their job.
- `Items`
  - Gets an instance of the key-value storage. You can use it
to pass additional information between different client filters
or just between different methods.
- `Job`
- `Parameters`
- `Storage`


#### `CreateJobFailedException`

The exception that is thrown when a `BackgroundJobClient` class instance
could not create a job due to another exception was thrown.

**Methods:**

- `#ctor(Serialization.SerializationInfo, Serialization.StreamingContext)`
  - Initializes a new instance of the `CreateJobFailedException` class
with serialized data.
  - `info`: The `SerializationInfo` that holds the serialized object data about the exception being thrown.
  - `context`: The `StreamingContext` that contains contextual information about the source or destination.
- `#ctor(string, Exception)`
  - Initializes a new instance of the `CreateJobFailedException`
class with a specified error message and a reference to the
inner exception that is the cause of this exception.
  - `message`: The error message that explains the reason for the exception.
  - `inner`: The exception that is the cause of this exception, not null.


#### `CreatedContext`

Provides the context for the `OnCreated`
method of the `IClientFilter` interface.

**Methods:**

- `#ctor([NotNull] CreateContext, [CanBeNull] BackgroundJob, bool, [CanBeNull] Exception)`
- `SetJobParameter([NotNull] string, object)`

**Properties:**

- `BackgroundJob`
- `Canceled`
  - Gets a value that indicates that this `CreatedContext`
object was canceled.
- `Exception`
  - Gets an exception that occurred during the creation of the job.
- `ExceptionHandled`
  - Gets or sets a value that indicates that this `CreatedContext`
object handles an exception occurred during the creation of the job.

**Fields:**

- `JobId`
- `Parameters`


#### `CreatingContext`

Provides the context for the `OnCreating`
method of the `IClientFilter` interface.

**Methods:**

- `#ctor(CreateContext)`
- `GetJobParameter<T>(string)`
  - Gets the job parameter of the specified name
if it exists. The parameter is deserialized from a JSON
string value to the given type T.
  - `name`: The name of the parameter.
  - `<T>`: The type of the parameter.
  - returns: The value of the given parameter if it exists or null otherwise.
- `SetJobParameter(string, object)`
  - Sets the job parameter of the specified name
to the corresponding value. The value of the
parameter is serialized to a JSON string.
  - `name`: The name of the parameter.
  - `value`: The value of the parameter.

**Properties:**

- `Canceled`
  - Gets or sets a value that indicates that this `CreatingContext`
object was canceled.


#### `IBackgroundJobFactory`

This interface acts as extensibility point for the process
of job creation. See the default implementation in the
`BackgroundJobFactory` class.

**Methods:**

- `Create(Hangfire.Client.CreateContext)`
  - Runs the process of job creation with the specified context.

**Properties:**

- `StateMachine`
  - Gets a state machine that's responsible for initial state change.


#### `IClientExceptionFilter`

Defines methods that are required for the client exception filter.

**Methods:**

- `OnClientException(Hangfire.Client.ClientExceptionContext)`
  - Called when an exception occurred during the creation of the job.
  - `filterContext`: The filter context.


#### `IClientFilter`

Defines methods that are required for a client filter.

**Methods:**

- `OnCreated(Hangfire.Client.CreatedContext)`
  - Called after the creation of the job.
  - `context`: The filter context.
- `OnCreating(Hangfire.Client.CreatingContext)`
  - Called before the creation of the job.
  - `context`: The filter context.


#### `NamespaceDoc`

The `Client` namespace contains types that allow you to
customize the background job creation pipeline using the `IClientFilter`,
or define your own creation process by implementing the `IBackgroundJobFactory`
interface.


### namespace `Hangfire.Common`

#### `CachedExpressionCompiler`

The caching expression tree compiler was copied from MVC core to MVC Futures so that Futures code could benefit
from it and so that it could be exposed as a public API. This is the only public entry point into the system.
See the comments in the ExpressionUtil namespace for more information.

The unit tests for the ExpressionUtil.* types are in the System.Web.Mvc.Test project.

**Methods:**

- `Evaluate(Expressions.Expression)`
  - Evaluates an expression (not a LambdaExpression), e.g. 2 + 2.
  - `arg`
  - returns: Expression result.


#### `CancellationEvent`

**Methods:**

- `#ctor(CancellationToken)`
- `Dispose`

**Fields:**

- `WaitHandle`


#### `CancellationTokenExtentions`

**Methods:**

- `GetCancellationEvent(CancellationToken)`
  - Returns a class that contains a `EventWaitHandle` that is set, when
the given cancellationToken is canceled. This method is based
on cancellation token registration and avoids using the `WaitHandle`
property as it may lead to high CPU issues.
- `Wait(CancellationToken, TimeSpan)`
  - Performs a wait until the specified timeout is elapsed or the
given cancellation token is canceled. The wait is performed on a dedicated event
wait handle to avoid using the `WaitHandle` property
that may lead to high CPU issues.
- `WaitOrThrow(CancellationToken, TimeSpan)`
  - Performs a wait until the specified timeout is elapsed or the
given cancellation token is canceled and throw `OperationCanceledException`
exception if wait succeeded. The wait is performed on a dedicated event
wait handle to avoid using the `WaitHandle` property
that may lead to high CPU issues.


#### `Enumerator`

**Methods:**

- `MoveNext`

**Fields:**

- `Current`


#### `FilterCollection<T>`

**Methods:**

- `Enumerator(List<JobFilter>)`
- `GetEnumerator`


#### `IJobFilter`

Defines members that specify the order of filters and
whether multiple filters are allowed.

**Properties:**

- `AllowMultiple`
  - When implemented in a class, gets or sets a value
that indicates whether multiple filters are allowed.
- `Order`
  - When implemented in a class, gets the filter order.


#### `IJobFilterProvider`

Provides an interface for finding filters.

**Methods:**

- `GetFilters(Hangfire.Common.Job)`
  - Returns an enumerator that contains all the `IJobFilterProvider`.
  - returns: The enumerator that contains all the `IJobFilterProvider`.


#### `Job`

Represents an action that can be marshalled to another process to
be performed.

**Methods:**

- `#ctor(MethodInfo)`
  - Initializes a new instance of the `Job` class with the
metadata of a method with no arguments.
  - `method`: Method that should be invoked.
- `#ctor(MethodInfo, object[])`
  - Initializes a new instance of the `Job` class with the
metadata of a method and the given list of arguments.
  - `method`: Method that should be invoked.
  - `args`: Arguments that will be passed to a method invocation.
- `#ctor(Type, MethodInfo)`
  - Initializes a new instance of the `Job` class with the
type, metadata of a method with no arguments.
  - `type`: Type that contains the given method.
  - `method`: Method that should be invoked.
- `#ctor(Type, MethodInfo, Generic.IReadOnlyList<object>)`
  - Initializes a new instance of the `Job` class with the type, metadata of a method,
and the given list of arguments, specified in a read-only list.
  - `type`: Type that contains the given method.
  - `method`: Method that should be invoked.
  - `args`: Arguments that should be passed during the method call.
- `#ctor(Type, MethodInfo, Generic.IReadOnlyList<object>, string)`
  - Initializes a new instance of the `Job` class with the type, metadata of a method,
the given list of arguments, and the default target queue for a job.
  - `type`: Type that contains the given method.
  - `method`: Method that should be invoked.
  - `args`: Arguments that should be passed during the method call.
  - `queue`: Default target queue for the job.
- `#ctor(Type, MethodInfo, object[])`
  - Initializes a new instance of the `Job` class with the
type, metadata of a method, and the given list of arguments.
  - `type`: Type that contains the given method.
  - `method`: Method that should be invoked.
  - `args`: Arguments that should be passed during the method call.
- `#ctor([NotNull] MethodInfo)`
- `#ctor([NotNull] MethodInfo, [NotNull] params object[])`
- `#ctor([NotNull] Type, [NotNull] MethodInfo)`
- `#ctor([NotNull] Type, [NotNull] MethodInfo, [NotNull] IReadOnlyList<object>)`
- `#ctor([NotNull] Type, [NotNull] MethodInfo, [NotNull] IReadOnlyList<object>, [CanBeNull] string)`
- `#ctor([NotNull] Type, [NotNull] MethodInfo, [NotNull] params object[])`
- `FromExpression(Expressions.Expression<Action>)`
  - Gets a new instance of the `Job` class based on the
given expression tree of a method call.
  - `methodCall`: Expression tree of a method call.
  - remarks: The `Type` property of a returning job will
point to the type of a given instance object when it is specified,
or to the declaring type otherwise. All the arguments are evaluated
using the expression compiler that uses caching where possible to
decrease the performance penalty.

Instance object (e.g. `() => instance.Method()`) is
only used to obtain the type for a job. It is not
serialized and not passed across the process boundaries.
- `FromExpression(Expressions.Expression<Func<Tasks.Task>>)`
  - Gets a new instance of the `Job` class based on the
given expression tree of a method call.
  - `methodCall`: Expression tree of a method call.
  - remarks: The `Type` property of a returning job will
point to the type of a given instance object when it is specified,
or to the declaring type otherwise. All the arguments are evaluated
using the expression compiler that uses caching where possible to
decrease the performance penalty.

Instance object (e.g. `() => instance.Method()`) is
only used to obtain the type for a job. It is not
serialized and not passed across the process boundaries.
- `FromExpression([NotNull, InstantHandle] Expression<Action>)`
- `FromExpression([NotNull, InstantHandle] Expression<Action>, [CanBeNull] string)`
- `FromExpression([NotNull, InstantHandle] Expression<Func<Task>>)`
- `FromExpression([NotNull, InstantHandle] Expression<Func<Task>>, [CanBeNull] string)`
- `FromExpression<T>(Expressions.Expression<Action<T1>>)`
  - Gets a new instance of the `Job` class based on the
given expression tree of an instance method call with explicit
type specification.
  - `methodCall`: Expression tree of a method call on TType.
  - `<TType>`: Explicit type that should be used on method call.
  - remarks: All the arguments are evaluated using the expression compiler
that uses caching where possible to decrease the performance
penalty.
- `FromExpression<T>(Expressions.Expression<Func<T1,Tasks.Task>>)`
  - Gets a new instance of the `Job` class based on the
given expression tree of an instance method call with explicit
type specification.
  - `methodCall`: Expression tree of a method call on TType.
  - `<TType>`: Explicit type that should be used on method call.
  - remarks: All the arguments are evaluated using the expression compiler
that uses caching where possible to decrease the performance
penalty.
- `FromExpression<T>([NotNull, InstantHandle] Expression<Action<TType>>)`
- `FromExpression<T>([NotNull, InstantHandle] Expression<Action<TType>>, [CanBeNull] string)`
- `FromExpression<T>([NotNull, InstantHandle] Expression<Func<TType, Task>>)`
- `FromExpression<T>([NotNull, InstantHandle] Expression<Func<TType, Task>>, [CanBeNull] string)`
- `Perform(Hangfire.JobActivator, Hangfire.IJobCancellationToken)`
- `ToString`
- `ToString(bool)`

**Properties:**

- `Args`
  - Gets a read-only collection of arguments that Should be passed to a
method invocation during the performance.
- `Arguments`
- `Method`
  - Gets the metadata of a method that should be invoked during the
performance.
- `Queue`
  - Gets a default target queue for a job to which it will be enqueued unless
overriden by a job filter.
- `Type`
  - Gets the metadata of a type that contains a method that should be
invoked during the performance.


#### `JobFilter`

Represents a metadata class that contains a reference to the
implementation of one or more of the filter interfaces, the filter's
order, and the filter's scope.

**Methods:**

- `#ctor(object, Hangfire.Common.JobFilterScope, Nullable<int>)`
  - Initializes a new instance of the Filter class.
  - `instance`: Filter instance.
  - `scope`: Filter scope.
  - `order`: The run order.
- `#ctor(object, JobFilterScope, int?)`

**Properties:**

- `Instance`
  - Gets the instance of the filter.
- `Order`
  - Gets the order in which the filter is applied.
- `Scope`
  - Gets the scope ordering of the filter.

**Fields:**

- `DefaultOrder`
  - Represents a constant that is used to specify the default ordering of filters.


#### `JobFilterAttribute`

Represents the base class for job filter attributes.

**Properties:**

- `Order`

**Fields:**

- `AllowMultiple`
- `TypeId`


#### `JobFilterAttributeFilterProvider`

Defines a filter provider for filter attributes.

**Methods:**

- `#ctor`
  - Initializes a new instance of the `JobFilterAttributeFilterProvider`
class with the attribute instance caching enabled.
- `#ctor(bool)`
  - Initializes a new instance of the `JobFilterAttributeFilterProvider`
class and optionally caches attribute instances.
  - `cacheAttributeInstances`
- `GetFilters(Job)`


#### `JobFilterCollection`

Represents a class that contains the job filters.

**Methods:**

- `Add(object)`
  - Adds the specified filter to the global filter collection.
  - `filter`: The filter instance.
- `Add(object, int)`
  - Adds the specified filter to the global filter collection
using the specified filter run order.
  - `filter`: The filter instance.
  - `order`: The run order.
- `Clear`
  - Removes all filters from the global filter collection.
- `Contains(object)`
  - Determines whether a filter is in the global filter collection.
  - `filter`: The filter instance.
  - returns: True if the global filter collection contains the filter, otherwise false.
- `GetEnumerator`
- `Remove(Type)`
  - Remove all filters of the specified type with strict type matching.
  - `type`: Type of filters to remove.
- `Remove(object)`
  - Removes all filters that match the specified filter.
  - `filter`: The filter instance.
- `Remove<T>`
  - Remove all filters of the specified type with strict type matching.
  - `<T>`: Type of filters to remove.

**Properties:**

- `Count`
  - Gets the number of filters in the global job filter collection.


#### `JobFilterInfo`

Encapsulates information about the available job filters.

**Methods:**

- `#ctor(Generic.IEnumerable<Hangfire.Common.JobFilter>)`
  - Initializes a new instance of the `JobFilterInfo` class using the specified filters collection.
  - `filters`: The filters collection.

**Properties:**

- `ApplyStateFilters`
  - Gets all the state changed filters in the application.
  - returns: The state changed filters.
- `ClientExceptionFiltersReversed`
  - Gets all the client exception filters in the application.
  - returns: The client exception filters.
- `ClientFilters`
  - Gets all the client filters in the application.
  - returns: The client filters.
- `ElectStateFilters`
  - Gets all the stat changing filters in the application.
  - returns: The state changing filters.
- `ServerExceptionFiltersReversed`
  - Gets all the server exception filters in the application.
  - returns: The server exception filters.
- `ServerFilters`
  - Gets all the server filters in the application.
  - returns: The server filters.


#### `JobFilterProviderCollection`

Represents the collection of filter providers for the application.

**Methods:**

- `#ctor`
  - Initializes a new instance of the `JobFilterProviderCollection`
class.
- `#ctor(IJobFilterProvider[])`
- `GetFilters(Hangfire.Common.Job)`
  - Returns the collection of filter providers.
  - `job`: Job, can be null.
  - returns: The collection of filter providers.
- `GetFilters(Job)`


#### `JobFilterProviders`

Provides a registration point for filters.

**Properties:**

- `Providers`
  - Provides a registration point for filters.


#### `JobFilterScope`

Defines values that specify the order in which Hangfire filters
run within the same filter type and filter order.

**Fields:**

- `Global`
  - Specifies an order before the `Type`.
- `Method`
  - Specifies an order after the `Type`.
- `Type`
  - Specifies an order after the `Global` and
before the `Method`.


#### `JobHelper`

**Methods:**

- `DeserializeDateTime(string)`
- `DeserializeNullableDateTime(string)`
- `FromJson(string, [NotNull] Type)`
- `FromJson<T>(string)`
- `FromMillisecondTimestamp(long)`
- `FromTimestamp(long)`
- `SerializeDateTime(DateTime)`
- `SetSerializerSettings(JsonSerializerSettings)`
- `ToJson(object)`
- `ToMillisecondTimestamp(DateTime)`
- `ToTimestamp(DateTime)`


#### `JobLoadException`

The exception that is thrown when a job could not
be loaded from the storage due to missing or incorrect
information about its type or method.

**Methods:**

- `#ctor(Serialization.SerializationInfo, Serialization.StreamingContext)`
  - Initializes a new instance of the `JobLoadException` class
with serialized data.
  - `info`: The `SerializationInfo` that holds the serialized object data about the exception being thrown.
  - `context`: The `StreamingContext` that contains contextual information about the source or destination.
- `#ctor(string, Exception)`
  - Initializes a new instance of the `JobLoadException`
class with a given message and information about inner exception.


#### `NamespaceDoc`

The `Common` namespace provides base types for background
job filters, such as `JobFilterAttribute`, and some helper classes.


#### `ReversedEnumerator`

**Methods:**

- `MoveNext`

**Fields:**

- `Current`


#### `ReversedFilterCollection<T>`

**Methods:**

- `GetEnumerator`
- `ReversedEnumerator(List<JobFilter>)`


#### `SerializationHelper`

Provides methods to serialize/deserialize data with Hangfire default settings.
Isolates internal serialization process from user interference including `JsonConvert.DefaultSettings` modification.

**Methods:**

- `Deserialize([CanBeNull] string, [NotNull] Type)`
- `Deserialize([CanBeNull] string, [NotNull] Type, SerializationOption)`
- `Deserialize(string, Type)`
  - Deserializes data with `Internal` option.
Use this method to deserialize internal data. Using isolated settings that can't be changed from user code.
- `Deserialize(string, Type, Hangfire.Common.SerializationOption)`
  - Deserializes data with specified option.
Use `Internal` to deserialize internal data.
Use `TypedInternal` if deserializable internal data has type names information.
Use `User` to deserialize user data like arguments and parameters,
configurable via `SetUserSerializerSettings`.
- `Deserialize<T>([CanBeNull] string)`
- `Deserialize<T>([CanBeNull] string, SerializationOption)`
- `Deserialize<T>(string)`
  - Deserializes data with `Internal` option.
Use this method to deserialize internal data. Using isolated settings that can't be changed from user code.
- `Deserialize<T>(string, Hangfire.Common.SerializationOption)`
  - Deserializes data with specified option.
Use `Internal` to deserialize internal data.
Use `TypedInternal` if deserializable internal data has type names information.
Use `User` to deserialize user data like arguments and parameters,
configurable via `SetUserSerializerSettings`.
- `Serialize([CanBeNull] object, [CanBeNull] Type, SerializationOption)`
- `Serialize(object, Type, Hangfire.Common.SerializationOption)`
  - Serializes data with specified option.
Use `Internal` option to serialize internal data.
Use `TypedInternal` option if you need to store type information.
Use `User` option to serialize user data like arguments and parameters,
configurable via `SetUserSerializerSettings`.
- `Serialize<T>(T1)`
  - Serializes data with `Internal` option.
Use this method to serialize internal data. Using isolated settings that can't be changed from user code.
- `Serialize<T>(T1, Hangfire.Common.SerializationOption)`
  - Serializes data with specified option.
Use `Internal` option to serialize internal data.
Use `TypedInternal` option if you need to store type information.
Use `User` option to serialize user data like arguments and parameters,
configurable via `SetUserSerializerSettings`.
- `Serialize<T>([CanBeNull] T)`
- `Serialize<T>([CanBeNull] T, SerializationOption)`


#### `SerializationOption`

**Fields:**

- `Internal`
  - For internal data using isolated settings that can't be changed from user code.
- `TypedInternal`
  - For internal data using isolated settings with types information (`Objects` setting)
that can't be changed from user code.
- `User`
  - For user data like arguments and parameters, configurable via `SetUserSerializerSettings`.


#### `TypeHelper`

**Methods:**

- `DefaultTypeResolver(string)`
- `DefaultTypeSerializer(Type)`
- `IgnoredAssemblyVersionTypeResolver(string)`
- `SimpleAssemblyTypeSerializer(Type)`

**Properties:**

- `CurrentTypeResolver`
- `CurrentTypeSerializer`


#### `TypeHelperSerializationBinder`

**Methods:**

- `BindToName(Type, string, string)`
- `BindToType(string, string)`


### namespace `Hangfire.Dashboard`

#### `DashboardContext`

Provides the context for the Dashboard UI. This class serves as a base class for specific web application frameworks,
such as ASP.NET Core or OWIN, and is accessible from different Dashboard UI request dispatchers (please see
`IDashboardDispatcher`), like pages or other endpoints.

**Methods:**

- `#ctor(Hangfire.JobStorage, Hangfire.DashboardOptions)`
  - Initializes a new instance of the `DashboardContext` class.
  - `storage`: The job storage used by the Dashboard UI.
  - `options`: The options for configuring the Dashboard UI.
- `GetBackgroundJobClient`
  - Gets the background job client for the current `JobStorage` instance.
  - returns: An instance of `IBackgroundJobClient`.
- `GetRecurringJobManager`
  - Gets the recurring job manager for the current `JobStorage` instance.
  - returns: An instance of `IRecurringJobManager`.

**Properties:**

- `AntiforgeryHeader`
  - Gets or sets the anti-forgery header value.
- `AntiforgeryToken`
  - Gets or sets the anti-forgery token value.
- `IsReadOnly`
  - Gets a value indicating whether the Dashboard UI is in read-only mode to possibly
hide elements that modify the `JobStorage` instance's data.
- `Options`
  - Gets the `DashboardOptions` for configuring the Dashboard UI.
- `Request`
  - Gets the `DashboardRequest` metadata.
Used by request dispatchers (please see `IDashboardDispatcher`) to provide request information.
- `Response`
  - Gets the `DashboardResponse` metadata.
Used by request dispatchers (please see `IDashboardDispatcher`) to send response information.
- `Storage`
  - Gets the `JobStorage` instance used by the Dashboard UI.
- `UriMatch`
  - Gets or sets the URI match information passed from the configured `pathTemplate`
when defining a route in the `DashboardRoutes` class.


#### `DashboardMetric`

**Methods:**

- `#ctor(string, Func<RazorPage, Metric>)`
- `#ctor(string, string, Func<RazorPage, Metric>)`

**Properties:**

- `Func`
- `Name`
- `Title`
- `Url`


#### `DashboardMetrics`

**Methods:**

- `AddMetric([NotNull] DashboardMetric)`
- `GetMetrics`

**Fields:**

- `AwaitingCount`
- `DeletedCount`
- `EnqueuedAndQueueCount`
- `EnqueuedCountOrNull`
- `FailedCount`
- `FailedCountOrNull`
- `ProcessingCount`
- `RecurringJobCount`
- `RetriesCount`
- `ScheduledCount`
- `ServerCount`
- `SucceededCount`


#### `DashboardOwinExtensions`

**Methods:**

- `MapHangfireDashboard(IAppBuilder)`
- `MapHangfireDashboard(IAppBuilder, string)`
- `MapHangfireDashboard(IAppBuilder, string, string)`
- `MapHangfireDashboard(IAppBuilder, string, string, IEnumerable<IAuthorizationFilter>)`
- `MapHangfireDashboard([NotNull] this IAppBuilder, string, string, IEnumerable<IAuthorizationFilter>, JobStorage)`


#### `DashboardRequest`

Provides the request details for the Dashboard UI. This class serves as an abstraction for HTTP requests
and is used within `IDashboardDispatcher` implementations to access request information.

**Methods:**

- `GetFormValuesAsync(string)`
  - Gets the values of a specific form parameter asynchronously, reading the request body if it's a form.
  - `key`: The key of the form parameter.
  - returns: A task that represents the asynchronous operation. The task result contains the list of values for the form parameter.
- `GetQuery(string)`
  - Gets the value of a specific query string parameter.
  - `key`: The key of the query string parameter.
  - returns: The value of the query string parameter.

**Properties:**

- `LocalIpAddress`
  - Gets the local IP address from which the request originated.
- `Method`
  - Gets the HTTP method of the request like `"GET"` or `"POST"`, that can
be checked for equality by using the `OrdinalIgnoreCase` comparer.
- `Path`
  - Gets the request path for the current request that doesn't include the `PrefixPath`,
like `"/jobs/enqueued"`.
- `PathBase`
  - Gets the base path for the request configured in the request middleware, usually useful
to reconstruct full URIs like for link generation.
- `RemoteIpAddress`
  - Gets the remote IP address from which the request originated.


#### `DashboardResponse`

Provides the response details for the Dashboard UI. This class serves as an abstraction for HTTP responses
and is used within `IDashboardDispatcher` implementations to send response information.

**Methods:**

- `SetExpire(DateTimeOffset?)`
- `SetExpire(Nullable<DateTimeOffset>)`
  - Sets the expiration time for the response.
  - `value`: The expiration time, or `null` to remove the expiration header.
- `WriteAsync(string)`
  - Writes the specified text to the response body asynchronously.
  - `text`: The text to write to the response body.
  - returns: A task that represents the asynchronous operation.

**Properties:**

- `Body`
  - Gets the response body stream, most of the time it's better to use the
`WriteAsync` method instead for text data.
- `ContentType`
  - Gets or sets the content type of the response like `"application/json"`.
- `StatusCode`
  - Gets or sets the HTTP status code of the response like `200`.


#### `DashboardRoutes`

Provides the routing mechanisms for the Dashboard UI. This class is used to register custom
request dispatchers, allowing developers to write extensions for the Dashboard UI, such as
custom pages, API endpoints or adding custom JavaScript or CSS files.

**Methods:**

- `AddJavaScript(Assembly, string)`
  - Adds a JavaScript resource embedded into the given assembly to be included in the dashboard.
  - `assembly`: The assembly containing the JavaScript embedded resource.
  - `resource`: The name of the JavaScript embedded resource.
  - remarks: The specified resource should be an embedded resource file within the referenced assembly.
You can discover embedded resource names by calling the `assembly.GetManifestResourceNames()` method.
- `AddJavaScript([NotNull] Assembly, [NotNull] string)`
- `AddStylesheet(Assembly, string)`
  - Adds a stylesheet resource embedded into the given assembly to be included in the dashboard.
  - `assembly`: The assembly containing the embedded stylesheet resource.
  - `resource`: The name of the stylesheet embedded resource.
  - remarks: The specified resource should be an embedded resource file within the referenced assembly.
You can discover embedded resource names by calling the `assembly.GetManifestResourceNames()` method.
- `AddStylesheet([NotNull] Assembly, [NotNull] string)`
- `AddStylesheetDarkMode(Assembly, string)`
  - Adds a resource embedded into the given assembly that will only be included in the dashboard
when the `DarkModeEnabled` is set to `true`.
  - `assembly`: The assembly containing the dark-mode stylesheet embedded resource.
  - `resource`: The name of the dark-mode stylesheet embedded resource.
  - remarks: The specified resource should be an embedded resource file within the referenced assembly.
You can discover embedded resource names by calling the `assembly.GetManifestResourceNames()` method.
- `AddStylesheetDarkMode([NotNull] Assembly, [NotNull] string)`

**Properties:**

- `Routes`
  - Gets the collection of routes for the Dashboard UI. Use this property to register
custom request dispatchers.


#### `HtmlHelper`

**Methods:**

- `#ctor([NotNull] RazorPage)`
- `BlockMetric([NotNull] DashboardMetric)`
- `Breadcrumbs(string, [NotNull] IDictionary<string, string>)`
- `FormatProperties(IDictionary<string, string>)`
- `HtmlEncode(string)`
- `InlineMetric([NotNull] DashboardMetric)`
- `JobId(string, bool)`
- `JobIdLink(string)`
- `JobName(Job)`
- `JobName(Job, bool)`
- `JobNameLink(string, Job)`
- `JobNameLink(string, Job, bool)`
- `JobsSidebar`
- `LocalTime(DateTime)`
- `MomentTitle(DateTime, string)`
- `Paginator([NotNull] Pager)`
- `PerPageSelector([NotNull] Pager)`
- `QueueLabel(string)`
- `Raw(string)`
- `RelativeTime(DateTime)`
- `RenderPartial(RazorPage)`
- `ServerId(string)`
- `SidebarMenu([NotNull] IEnumerable<Func<RazorPage, MenuItem>>)`
- `StackTrace(string)`
- `StateLabel(string)`
- `StateLabel(string, string, bool)`
- `ToHumanDuration(TimeSpan?, bool)`

**Fields:**

- `Page`


#### `IAuthorizationFilter`


#### `IDashboardAsyncAuthorizationFilter`


#### `IDashboardAuthorizationFilter`


#### `IDashboardDispatcher`

Defines the method for dispatching requests within the Dashboard UI.
Implementations of this interface handle incoming requests to the dashboard and produce appropriate responses.

**Methods:**

- `Dispatch(Hangfire.Dashboard.DashboardContext)`
  - Processes the request within the provided `DashboardContext`.
  - `context`: The context for the current dashboard request, containing information about the request and response.
  - returns: A task that represents the asynchronous dispatch operation.


#### `IRequestDispatcher`


#### `JobDetailsRendererDto`

**Methods:**

- `#ctor([NotNull] RazorPage, [NotNull] string, [NotNull] JobDetailsDto)`

**Properties:**

- `JobDetails`
- `JobId`
- `Page`


#### `JobHistoryRenderer`

**Methods:**

- `AddBackgroundStateColor(string, string)`
- `AddForegroundStateColor(string, string)`
- `AddStateCssSuffix(string, string)`
- `DefaultRenderer(HtmlHelper, IDictionary<string, string>)`
- `Exists(string)`
- `GetBackgroundStateColor(string)`
- `GetForegroundStateColor(string)`
- `GetStateCssSuffix(string)`
- `NullRenderer(HtmlHelper, IDictionary<string, string>)`
- `Register(string, Func<HtmlHelper, IDictionary<string, string>, NonEscapedString>)`
- `RenderHistory(HtmlHelper, string, IDictionary<string, string>)`
- `SucceededRenderer(HtmlHelper, IDictionary<string, string>)`


#### `JobsSidebarMenu`

**Fields:**

- `Items`


#### `LocalRequestsOnlyAuthorizationFilter`

**Methods:**

- `Authorize(DashboardContext)`
- `Authorize(IDictionary<string, object>)`


#### `MenuItem`

**Methods:**

- `#ctor(string, string)`
- `GetAllMetrics`

**Properties:**

- `Active`
- `Metric`
- `Metrics`
- `Text`
- `Url`


#### `Metric`

**Methods:**

- `#ctor(long)`
- `#ctor(string)`

**Properties:**

- `Highlighted`
- `IntValue`
- `Style`
- `Title`
- `Value`


#### `MetricStyle`

**Fields:**

- `Danger`
- `Default`
- `Info`
- `Success`
- `Warning`


#### `MiddlewareExtensions`

**Methods:**

- `UseHangfireDashboard([NotNull] DashboardOptions, [NotNull] JobStorage, [NotNull] RouteCollection, [CanBeNull] IOwinDashboardAntiforgery)`
- `UseHangfireDashboard([NotNull] this BuildFunc, [NotNull] DashboardOptions, [NotNull] JobStorage, [NotNull] RouteCollection, [CanBeNull] IOwinDashboardAntiforgery)`


#### `NamespaceDoc`

The `Dashboard` namespace contains types that allow you to
restrict an access to the Dashboard UI by implementing the `IDashboardAuthorizationFilter`
interface, as well as customize it by adding new pages, menu items, metrics, routes.


#### `NavigationMenu`

**Fields:**

- `Items`


#### `NonEscapedString`

**Methods:**

- `#ctor(string)`
- `ToString`


#### `OwinDashboardContext`

**Methods:**

- `#ctor([NotNull] JobStorage, [NotNull] DashboardOptions, [NotNull] IDictionary<string, object>)`

**Properties:**

- `Environment`


#### `OwinDashboardContextExtensions`

**Methods:**

- `GetOwinEnvironment([NotNull] this DashboardContext)`


#### `Pager`

**Methods:**

- `#ctor(int, int, int, long)`
- `#ctor(int, int, long)`
- `PageUrl(int)`
- `RecordsPerPageUrl(int)`

**Properties:**

- `BasePageUrl`
- `CurrentPage`
- `FromRecord`
- `RecordsPerPage`
- `TotalPageCount`
- `TotalRecordCount`


#### `RazorPage`

**Methods:**

- `Assign(Hangfire.Dashboard.RazorPage)`
- `Assign(RazorPage)`
- `Execute`
- `Query(string)`
- `ToString`
- `Write(object)`
- `WriteLiteral(string)`

**Properties:**

- `ApplicationUtcNow`
- `Context`
- `GenerationTime`
- `Html`
- `Layout`
- `Statistics`
- `StorageUtcNow`
- `TimeDifference`
- `Url`

**Fields:**

- `AppPath`
- `DashboardOptions`
- `IsReadOnly`
- `RequestPath`
- `Storage`


#### `RequestDispatcherContext`

**Methods:**

- `#ctor(string, int, [NotNull] JobStorage, [NotNull] IDictionary<string, object>, [NotNull] Match)`
- `FromDashboardContext([NotNull] DashboardContext)`

**Properties:**

- `AppPath`
- `JobStorage`
- `OwinEnvironment`
- `StatsPollingInterval`
- `UriMatch`


#### `RequestDispatcherWrapper`

**Methods:**

- `#ctor([NotNull] IRequestDispatcher)`
- `Dispatch(DashboardContext)`


#### `RouteCollection`

**Methods:**

- `Add([NotNull] string, [NotNull] IDashboardDispatcher)`
- `Add([NotNull] string, [NotNull] IRequestDispatcher)`
- `FindDispatcher(string)`


#### `RouteCollectionExtensions`

**Methods:**

- `AddBatchCommand([NotNull] this RouteCollection, [NotNull] string, [NotNull] Action<DashboardContext, string>)`
- `AddBatchCommand([NotNull] this RouteCollection, [NotNull] string, [NotNull] Action<RequestDispatcherContext, string>)`
- `AddClientBatchCommand(RouteCollection, string, [NotNull] Action<IBackgroundJobClient, string>)`
- `AddCommand([NotNull] this RouteCollection, [NotNull] string, [NotNull] Func<DashboardContext, bool>)`
- `AddCommand([NotNull] this RouteCollection, [NotNull] string, [NotNull] Func<RequestDispatcherContext, bool>)`
- `AddRazorPage([NotNull] this RouteCollection, [NotNull] string, [NotNull] Func<Match, RazorPage>)`
- `AddRecurringBatchCommand(RouteCollection, string, [NotNull] Action<IRecurringJobManager, string>)`
- `AddRecurringBatchCommand(RouteCollection, string, [NotNull] Action<RecurringJobManager, string>)`


#### `UrlHelper`

**Methods:**

- `#ctor([NotNull] DashboardContext)`
- `#ctor([NotNull] IDictionary<string, object>)`
- `Home`
- `JobDetails(string)`
- `LinkToQueues`
- `Queue(string)`
- `To(string)`


### namespace `Hangfire.Dashboard.Owin`

#### `IOwinDashboardAntiforgery`


### namespace `Hangfire.Dashboard.Pages`

#### `LayoutPage`

**Methods:**

- `Execute`


#### `NamespaceDoc`

The `Pages` namespace contains the `LayoutPage`
class, layout for all the Dashboard UI pages.


### namespace `Hangfire.Dashboard.Resources`

#### `Strings`

A strongly-typed resource class, for looking up localized strings, etc.

**Properties:**

- `AwaitingJobsPage_ContinuationsWarning_Text`
  - Looks up a localized string similar to Don't worry, continuations are working as expected. But your current job storage does not support some queries required to show this page. Please try to update your storage or wait until the full command set is implemented..
- `AwaitingJobsPage_ContinuationsWarning_Title`
  - Looks up a localized string similar to Continuations are working, but this page can't be displayed.
- `AwaitingJobsPage_NoJobs`
  - Looks up a localized string similar to No jobs found in awaiting state..
- `AwaitingJobsPage_Table_Options`
  - Looks up a localized string similar to Options.
- `AwaitingJobsPage_Table_Parent`
  - Looks up a localized string similar to Parent.
- `AwaitingJobsPage_Table_Since`
  - Looks up a localized string similar to Since.
- `AwaitingJobsPage_Title`
  - Looks up a localized string similar to Awaiting Jobs.
- `Common_CannotFindTargetMethod`
  - Looks up a localized string similar to Can not find the target method..
- `Common_Condition`
  - Looks up a localized string similar to Condition.
- `Common_Continuations`
  - Looks up a localized string similar to Continuations.
- `Common_Created`
  - Looks up a localized string similar to Created.
- `Common_Delete`
  - Looks up a localized string similar to Delete.
- `Common_DeleteConfirm`
  - Looks up a localized string similar to Do you really want to DELETE ALL selected jobs?.
- `Common_DeleteSelected`
  - Looks up a localized string similar to Delete selected.
- `Common_Deleting`
  - Looks up a localized string similar to Deleting....
- `Common_Disabled`
  - Looks up a localized string similar to Disabled.
- `Common_EnqueueButton_Text`
  - Looks up a localized string similar to Enqueue jobs.
- `Common_Enqueued`
  - Looks up a localized string similar to Enqueued.
- `Common_Enqueueing`
  - Looks up a localized string similar to Enqueueing....
- `Common_Error`
  - Looks up a localized string similar to Error.
- `Common_Fetched`
  - Looks up a localized string similar to Fetched.
- `Common_Id`
  - Looks up a localized string similar to Id.
- `Common_Job`
  - Looks up a localized string similar to Job.
- `Common_JobExpired`
  - Looks up a localized string similar to Job expired..
- `Common_JobStateChanged_Text`
  - Looks up a localized string similar to Job's state has been changed while fetching data..
- `Common_LessDetails`
  - Looks up a localized string similar to Fewer details....
- `Common_MoreDetails`
  - Looks up a localized string similar to More details....
- `Common_NoState`
  - Looks up a localized string similar to No state.
- `Common_NotAvailable`
  - Looks up a localized string similar to N/A.
- `Common_PeriodDay`
  - Looks up a localized string similar to Day.
- `Common_PeriodWeek`
  - Looks up a localized string similar to Week.
- `Common_Reason`
  - Looks up a localized string similar to Reason.
- `Common_RequeueJobs`
  - Looks up a localized string similar to Requeue jobs.
- `Common_Retry`
  - Looks up a localized string similar to Retry.
- `Common_Server`
  - Looks up a localized string similar to Server.
- `Common_State`
  - Looks up a localized string similar to State.
- `Common_Unknown`
  - Looks up a localized string similar to Unknown.
- `Culture`
  - Overrides the current thread's CurrentUICulture property for all
resource lookups using this strongly typed resource class.
- `DeletedJobsPage_NoJobs`
  - Looks up a localized string similar to No deleted jobs found..
- `DeletedJobsPage_Table_Deleted`
  - Looks up a localized string similar to Deleted.
- `DeletedJobsPage_Table_Exception`
  - Looks up a localized string similar to Exception.
- `DeletedJobsPage_Title`
  - Looks up a localized string similar to Deleted Jobs.
- `EnqueuedJobsPage_NoJobs`
  - Looks up a localized string similar to The queue is empty..
- `EnqueuedJobsPage_Title`
  - Looks up a localized string similar to Enqueued Jobs.
- `FailedJobsPage_FailedJobsNotExpire_Warning_Html`
  - Looks up a localized string similar to <strong>Failed jobs do not become expired</strong> to allow you to re-queue them without any
time pressure. You should re-queue or delete them manually, or apply <code>AutomaticRetry(OnAttemptsExceeded = AttemptsExceededAction.Delete)</code>
attribute to delete them automatically..
- `FailedJobsPage_NoJobs`
  - Looks up a localized string similar to You have no failed jobs at the moment..
- `FailedJobsPage_Table_Failed`
  - Looks up a localized string similar to Failed.
- `FailedJobsPage_Title`
  - Looks up a localized string similar to Failed Jobs.
- `FetchedJobsPage_NoJobs`
  - Looks up a localized string similar to The queue is empty..
- `FetchedJobsPage_Title`
  - Looks up a localized string similar to Fetched Jobs.
- `HomePage_GraphHover_Failed`
  - Looks up a localized string similar to Failed.
- `HomePage_GraphHover_Succeeded`
  - Looks up a localized string similar to Succeeded.
- `HomePage_HistoryGraph`
  - Looks up a localized string similar to History Graph.
- `HomePage_RealtimeGraph`
  - Looks up a localized string similar to Realtime Graph.
- `HomePage_Title`
  - Looks up a localized string similar to Overview.
- `JobDetailsPage_Created`
  - Looks up a localized string similar to Created.
- `JobDetailsPage_DeleteConfirm`
  - Looks up a localized string similar to Do you really want to delete this job?.
- `JobDetailsPage_JobAbortedNotActive_Warning_Html`
  - Looks up a localized string similar to <strong>The job was aborted</strong> – it is processed by server
<code>{0}</code> which is not in the
<a href="{1}">active servers</a> list for now.
It will be retried automatically after invisibility timeout, but you can
also re-queue or delete it manually..
- `JobDetailsPage_JobAbortedWithHeartbeat_Warning_Html`
  - Looks up a localized string similar to <strong>Looks like the job was aborted</strong> – it is processed by server
<code>{0}</code>, which reported its heartbeat more than 1 minute ago.
It will be retried automatically after invisibility timeout, but you can
also re-queue or delete it manually..
- `JobDetailsPage_JobExpired`
  - Looks up a localized string similar to Background job '{0}' has expired or could not be found on the server..
- `JobDetailsPage_JobFinished_Warning_Html`
  - Looks up a localized string similar to <strong>The job is finished</strong>.
It will be removed automatically <em><abbr data-moment="{0}">{1}</abbr></em>..
- `JobDetailsPage_JobId`
  - Looks up a localized string similar to Id.
- `JobDetailsPage_Parameters`
  - Looks up a localized string similar to Parameters.
- `JobDetailsPage_Requeue`
  - Looks up a localized string similar to Requeue.
- `JobDetailsPage_State`
  - Looks up a localized string similar to State.
- `JobsSidebarMenu_Awaiting`
  - Looks up a localized string similar to Awaiting.
- `JobsSidebarMenu_Deleted`
  - Looks up a localized string similar to Deleted.
- `JobsSidebarMenu_Enqueued`
  - Looks up a localized string similar to Enqueued.
- `JobsSidebarMenu_Failed`
  - Looks up a localized string similar to Failed.
- `JobsSidebarMenu_Processing`
  - Looks up a localized string similar to Processing.
- `JobsSidebarMenu_Scheduled`
  - Looks up a localized string similar to Scheduled.
- `JobsSidebarMenu_Succeeded`
  - Looks up a localized string similar to Succeeded.
- `LayoutPage_Back`
  - Looks up a localized string similar to Back to site.
- `LayoutPage_Footer_Generatedms`
  - Looks up a localized string similar to Generated: {0}ms.
- `LayoutPage_Footer_StorageTime`
  - Looks up a localized string similar to Storage Time:.
- `LayoutPage_Footer_Time`
  - Looks up a localized string similar to Application Time:.
- `LayoutPage_Footer_TimeIsOutOfSync`
  - Looks up a localized string similar to Application time is out of sync with storage time.
- `Metrics_ActiveConnections`
  - Looks up a localized string similar to Active Connections.
- `Metrics_AwaitingCount`
  - Looks up a localized string similar to Awaiting.
- `Metrics_DeletedJobs`
  - Looks up a localized string similar to Deleted Jobs.
- `Metrics_EnqueuedCountOrNull`
  - Looks up a localized string similar to Enqueued.
- `Metrics_EnqueuedQueuesCount`
  - Looks up a localized string similar to Enqueued / Queues.
- `Metrics_FailedCountOrNull`
  - Looks up a localized string similar to {0} failed job(s) found. Retry or delete them manually..
- `Metrics_FailedJobs`
  - Looks up a localized string similar to Failed Jobs.
- `Metrics_ProcessingJobs`
  - Looks up a localized string similar to Processing Jobs.
- `Metrics_RecurringJobs`
  - Looks up a localized string similar to Recurring Jobs.
- `Metrics_Retries`
  - Looks up a localized string similar to Retries.
- `Metrics_SQLServer_ActiveTransactions`
  - Looks up a localized string similar to Active Transactions.
- `Metrics_SQLServer_DataFilesSize`
  - Looks up a localized string similar to Data File(s) Used (MB).
- `Metrics_SQLServer_LogFilesSize`
  - Looks up a localized string similar to Log File(s) Used (MB).
- `Metrics_SQLServer_SchemaVersion`
  - Looks up a localized string similar to Schema Version.
- `Metrics_ScheduledJobs`
  - Looks up a localized string similar to Scheduled Jobs.
- `Metrics_Servers`
  - Looks up a localized string similar to Servers.
- `Metrics_SucceededJobs`
  - Looks up a localized string similar to Succeeded Jobs.
- `Metrics_TotalConnections`
  - Looks up a localized string similar to Total Connections.
- `NavigationMenu_Jobs`
  - Looks up a localized string similar to Jobs.
- `NavigationMenu_RecurringJobs`
  - Looks up a localized string similar to Recurring Jobs.
- `NavigationMenu_Retries`
  - Looks up a localized string similar to Retries.
- `NavigationMenu_Servers`
  - Looks up a localized string similar to Servers.
- `Paginator_Next`
  - Looks up a localized string similar to Next.
- `Paginator_Prev`
  - Looks up a localized string similar to Prev.
- `Paginator_TotalItems`
  - Looks up a localized string similar to Total items.
- `PerPageSelector_ItemsPerPage`
  - Looks up a localized string similar to Items per page.
- `ProcessingJobsPage_Aborted`
  - Looks up a localized string similar to Looks like the job was aborted.
- `ProcessingJobsPage_NoJobs`
  - Looks up a localized string similar to No jobs are being processed right now..
- `ProcessingJobsPage_Table_Started`
  - Looks up a localized string similar to Started.
- `ProcessingJobsPage_Title`
  - Looks up a localized string similar to Processing Jobs.
- `QueuesPage_NoJobs`
  - Looks up a localized string similar to No jobs queued..
- `QueuesPage_NoQueues`
  - Looks up a localized string similar to No queued jobs found. Try to enqueue a job..
- `QueuesPage_Table_Length`
  - Looks up a localized string similar to Length.
- `QueuesPage_Table_NextsJobs`
  - Looks up a localized string similar to Next jobs.
- `QueuesPage_Table_Queue`
  - Looks up a localized string similar to Queue.
- `QueuesPage_Title`
  - Looks up a localized string similar to Queues.
- `RecurringJobsPage_Canceled`
  - Looks up a localized string similar to Canceled.
- `RecurringJobsPage_NoJobs`
  - Looks up a localized string similar to No recurring jobs found..
- `RecurringJobsPage_RecurringJobDisabled_Tooltip`
  - Looks up a localized string similar to Cron expression is invalid or don't have any occurrences over the next 100 years.
- `RecurringJobsPage_Table_Cron`
  - Looks up a localized string similar to Cron.
- `RecurringJobsPage_Table_LastExecution`
  - Looks up a localized string similar to Last execution.
- `RecurringJobsPage_Table_NextExecution`
  - Looks up a localized string similar to Next execution.
- `RecurringJobsPage_Table_TimeZone`
  - Looks up a localized string similar to Time zone.
- `RecurringJobsPage_Title`
  - Looks up a localized string similar to Recurring Jobs.
- `RecurringJobsPage_TriggerNow`
  - Looks up a localized string similar to Trigger now.
- `RecurringJobsPage_Triggering`
  - Looks up a localized string similar to Triggering....
- `ResourceManager`
  - Returns the cached ResourceManager instance used by this class.
- `RetriesPage_NoJobs`
  - Looks up a localized string similar to All is OK – you have no retries..
- `RetriesPage_Title`
  - Looks up a localized string similar to Retries.
- `RetriesPage_Warning_Html`
  - Looks up a localized string similar to <h4>Retries are working, but this page can't be displayed</h4>
<p>
Don't worry, retries are working as expected. Your current job storage does not support
some queries required to show this page. Please try to update your storage or wait until
the full command set is implemented.
</p>
<p>
Please go to the <a href="{0}">Scheduled jobs</a> page to see all the
scheduled jobs including retries.
</p>.
- `ScheduledJobsPage_EnqueueNow`
  - Looks up a localized string similar to Enqueue now.
- `ScheduledJobsPage_NoJobs`
  - Looks up a localized string similar to There are no scheduled jobs..
- `ScheduledJobsPage_Table_Enqueue`
  - Looks up a localized string similar to Enqueue.
- `ScheduledJobsPage_Table_Scheduled`
  - Looks up a localized string similar to Scheduled.
- `ScheduledJobsPage_Title`
  - Looks up a localized string similar to Scheduled Jobs.
- `ServersPage_Active`
  - Looks up a localized string similar to Active.
- `ServersPage_NoServers`
  - Looks up a localized string similar to There are no active servers. Background tasks will not be processed..
- `ServersPage_Note_Text`
  - Looks up a localized string similar to Some of the servers don't have heartbeat reported within the last minute and may be aborted. If they don't report heartbeat in the near future, they will be removed automatically after timeout is exceeded, no manual action is required.
Incomplete background jobs running on those servers will be re-queued automatically, but you can speed up the process by checking the <a href="{0}">Processing Jobs</a> page..
- `ServersPage_Note_Title`
  - Looks up a localized string similar to Aborted servers will be removed automatically.
- `ServersPage_Possibly_Aborted`
  - Looks up a localized string similar to Possibly aborted.
- `ServersPage_Table_Heartbeat`
  - Looks up a localized string similar to Heartbeat.
- `ServersPage_Table_Name`
  - Looks up a localized string similar to Name.
- `ServersPage_Table_Queues`
  - Looks up a localized string similar to Queues.
- `ServersPage_Table_Started`
  - Looks up a localized string similar to Started.
- `ServersPage_Table_Workers`
  - Looks up a localized string similar to Workers.
- `ServersPage_Title`
  - Looks up a localized string similar to Servers.
- `SucceededJobsPage_NoJobs`
  - Looks up a localized string similar to No succeeded jobs found..
- `SucceededJobsPage_Table_Duration`
  - Looks up a localized string similar to Duration.
- `SucceededJobsPage_Table_Latency`
  - Looks up a localized string similar to Latency.
- `SucceededJobsPage_Table_Succeeded`
  - Looks up a localized string similar to Succeeded.
- `SucceededJobsPage_Table_TotalDuration`
  - Looks up a localized string similar to Total Duration.
- `SucceededJobsPage_Title`
  - Looks up a localized string similar to Succeeded Jobs.


### namespace `Hangfire.Logging`

#### `ColouredConsoleLogProvider`

**Methods:**

- `#ctor`
- `#ctor(LogLevel)`
- `GetLogger(string)`
- `MessageFormatterDelegate(string, LogLevel, object, Exception)`

**Properties:**

- `Colors`
- `MessageFormatter`


#### `ElmahLogProvider`

**Methods:**

- `#ctor`
- `#ctor(LogLevel)`
- `GetLogger(string)`
- `IsLoggerAvailable`

**Properties:**

- `ProviderIsAvailableOverride`


#### `EntLibLogProvider`

**Methods:**

- `#ctor`
- `GetLogger(string)`
- `IsLoggerAvailable`

**Properties:**

- `ProviderIsAvailableOverride`


#### `ILog`

Simple interface that represent a logger.

**Methods:**

- `Log(Hangfire.Logging.LogLevel, Func<string>, Exception)`
  - Log a message the specified log level.
  - `logLevel`: The log level.
  - `messageFunc`: The message function.
  - `exception`: An optional exception.
  - returns: true if the message was logged. Otherwise false.
  - remarks: Note to implementers: the message func should not be called if the loglevel is not enabled
so as not to incur performance penalties.

To check IsEnabled call Log with only LogLevel and check the return value, no event will be written


#### `ILogProvider`

Represents a way to get a `ILog`


#### `Log4NetLogProvider`

**Methods:**

- `#ctor`
- `GetLogger(string)`
- `IsLoggerAvailable`

**Properties:**

- `ProviderIsAvailableOverride`


#### `LogExtensions`

**Methods:**

- `Debug(ILog, Func<string>)`
- `Debug(ILog, string)`
- `DebugException(ILog, string, Exception)`
- `DebugFormat(ILog, string, object[])`
- `Error(ILog, Func<string>)`
- `Error(ILog, string)`
- `ErrorException(ILog, string, Exception)`
- `ErrorFormat(ILog, string, object[])`
- `Fatal(ILog, Func<string>)`
- `Fatal(ILog, string)`
- `FatalException(ILog, string, Exception)`
- `FatalFormat(ILog, string, object[])`
- `Info(ILog, Func<string>)`
- `Info(ILog, string)`
- `InfoException(ILog, string, Exception)`
- `InfoFormat(ILog, string, object[])`
- `IsDebugEnabled(ILog)`
- `IsErrorEnabled(ILog)`
- `IsFatalEnabled(ILog)`
- `IsInfoEnabled(ILog)`
- `IsTraceEnabled(ILog)`
- `IsWarnEnabled(ILog)`
- `Trace(ILog, Func<string>)`
- `Trace(ILog, string)`
- `TraceException(ILog, string, Exception)`
- `TraceFormat(ILog, string, object[])`
- `Warn(ILog, Func<string>)`
- `Warn(ILog, string)`
- `WarnException(ILog, string, Exception)`
- `WarnFormat(ILog, string, object[])`


#### `LogLevel`

The log level.

**Fields:**

- `Debug`
- `Error`
- `Info`
- `Trace`
- `Warn`


#### `LogProvider`

Provides a mechanism to create instances of `ILog` objects.

**Methods:**

- `For<T>`
  - Gets a logger for the specified type.
  - `<T>`: The type whose name will be used for the logger.
  - returns: An instance of `ILog`
- `GetCurrentClassLogger`
  - Gets a logger for the current class.
  - returns: An instance of `ILog`
- `GetLogger(Type)`
  - Gets a logger for the specified type.
  - `type`: The type whose name will be used for the logger.
  - returns: An instance of `ILog`
- `GetLogger(string)`
  - Gets a logger with the specified name.
  - `name`: The name.
  - returns: An instance of `ILog`
- `SetCurrentLogProvider(Hangfire.Logging.ILogProvider)`
  - Sets the current log provider.
  - `logProvider`: The log provider.
- `SetCurrentLogProvider(ILogProvider)`


#### `LoupeLogProvider`

**Methods:**

- `#ctor`
- `GetLogger(string)`
- `IsLoggerAvailable`

**Properties:**

- `ProviderIsAvailableOverride`


#### `NLogLogProvider`

**Methods:**

- `#ctor`
- `GetLogger(string)`
- `IsLoggerAvailable`

**Properties:**

- `ProviderIsAvailableOverride`


#### `NamespaceDoc`

The `Logging` namespace contains types that allow you to
integrate Hangfire's logging with your projects as well as use it
to log custom messages.


#### `NamespaceGroupDoc`

The Hangfire.Logging namespaces contain types that allow you to
integrate Hangfire's logging with your projects as well as use it
to log custom messages.


#### `SerilogLogProvider`

**Methods:**

- `#ctor`
- `GetLogger(string)`
- `IsLoggerAvailable`

**Properties:**

- `ProviderIsAvailableOverride`


### namespace `Hangfire.Logging.LogProviders`

#### `LoupeLogProvider`

**Properties:**

- `ProviderIsAvailableOverride`
  - Gets or sets a value indicating whether [provider is available override]. Used in tests.


#### `NamespaceDoc`

The `LogProviders` namespace contains types for
supporting most popular logging frameworks to simplify the logging integration
with your projects.


### namespace `Hangfire.Logging.LogProviders.ColouredConsoleLogProvider`

#### `MessageFormatterDelegate`

A delegate returning a formatted log message


### namespace `Hangfire.Logging.LogProviders.LoupeLogProvider`

#### `WriteDelegate`

The form of the Loupe Log.Write method we're using


### namespace `Hangfire.Processing`

#### `BackgroundTaskScheduler`

Represents a custom implementation of the `TaskScheduler` that uses
its own threads to execute `Task`-based work items and their continuations.
The primary purpose of this scheduler is background processing, for other use cases
consider using the `Default` scheduler instead.

**Methods:**

- `#ctor`
  - Initializes a new instance of the `BackgroundTaskScheduler` with
the number of threads based on the `ProcessorCount` property.
All the created threads will be started to dispatch `Task`
instances scheduled to run on this scheduler.
- `#ctor(Func<ThreadStart,Generic.IEnumerable<Thread>>, Action<Exception>)`
  - Initializes a new instance of the `BackgroundTaskScheduler`
class with the specified threadFactory and an optional exception
handler. All the created threads will be started to dispatch `Task`
instances scheduled to run on this scheduler.
  - `threadFactory`: Callback that creates one or more dedicated threads.
  - `exceptionHandler`: Optional callback that is invoked when unhandled exception occurs
in one of the threads. After this event this instance is considered stopped.
- `#ctor([NotNull] Func<ThreadStart, IEnumerable<Thread>>, [CanBeNull] Action<Exception>)`
- `#ctor(int)`
  - Initializes a new instance of the `BackgroundTaskScheduler` with
the given number of dedicated threads that will be creating using the default thread
factory. All the created threads will be started to dispatch `Task`
instances scheduled to run on this scheduler.
  - `threadCount`: The number of dedicated threads will be created.
- `Dispose`
  - Signals all the threads to be stopped and releases all the unmanaged resources.
This method should be called only when you are uninterested on the corresponding tasks,
i.e. during AppDomain unloads, process shutdowns, etc.
- `GetScheduledTasks`
- `QueueTask(Tasks.Task)`
- `TryExecuteTaskInline(Tasks.Task, bool)`

**Properties:**

- `MaximumConcurrencyLevel`


#### `IBackgroundDispatcher`


#### `IBackgroundExecution`


### namespace `Hangfire.Server`

#### `BackgroundJobPerformer`

**Methods:**

- `#ctor`
- `#ctor([NotNull] IJobFilterProvider)`
- `#ctor([NotNull] IJobFilterProvider, [NotNull] JobActivator)`
- `#ctor([NotNull] IJobFilterProvider, [NotNull] JobActivator, [CanBeNull] TaskScheduler)`
- `Perform(PerformContext)`


#### `BackgroundProcessContext`

**Methods:**

- `#ctor([NotNull] string, [NotNull] JobStorage, [NotNull] IDictionary<string, object>, CancellationToken)`
- `#ctor([NotNull] string, [NotNull] JobStorage, [NotNull] IDictionary<string, object>, Guid, CancellationToken, CancellationToken, CancellationToken)`
- `Wait(TimeSpan)`

**Properties:**

- `ExecutionId`
- `Properties`
- `ServerId`
- `ShutdownToken`
- `StoppedToken`
- `StoppingToken`
- `Storage`

**Fields:**

- `CancellationToken`
- `IsShutdownRequested`
- `IsStopped`
- `IsStopping`


#### `BackgroundProcessExtensions`

**Methods:**

- `UseBackgroundPool([NotNull] this IBackgroundProcess)`
- `UseBackgroundPool([NotNull] this IBackgroundProcess, [NotNull] Func<string, ThreadStart, IEnumerable<Thread>>)`
- `UseBackgroundPool([NotNull] this IBackgroundProcess, int)`
- `UseBackgroundPool([NotNull] this IBackgroundProcess, int, [CanBeNull] Action<Thread>)`
- `UseBackgroundPool([NotNull] this IBackgroundProcessAsync)`
- `UseBackgroundPool([NotNull] this IBackgroundProcessAsync, int)`
- `UseBackgroundPool([NotNull] this IBackgroundProcessAsync, int, [NotNull] Func<string, ThreadStart, IEnumerable<Thread>>)`
- `UseBackgroundPool([NotNull] this IBackgroundProcessAsync, int, int)`
- `UseThreadPool([NotNull] this IBackgroundProcessAsync)`
- `UseThreadPool([NotNull] this IBackgroundProcessAsync, int)`


#### `BackgroundProcessingServer`

Responsible for running the given collection background processes.

**Methods:**

- `#ctor(Hangfire.Server.BackgroundServerProcess, Hangfire.Server.BackgroundProcessingServerOptions)`
  - Initializes a new instance of the `BackgroundProcessingServer`
class and immediately starts all the given background processes.
- `#ctor([NotNull] IEnumerable<IBackgroundProcess>)`
- `#ctor([NotNull] IEnumerable<IBackgroundProcess>, [NotNull] IDictionary<string, object>)`
- `#ctor([NotNull] JobStorage, [NotNull] IEnumerable<IBackgroundProcess>)`
- `#ctor([NotNull] JobStorage, [NotNull] IEnumerable<IBackgroundProcess>, [NotNull] IDictionary<string, object>)`
- `#ctor([NotNull] JobStorage, [NotNull] IEnumerable<IBackgroundProcess>, [NotNull] IDictionary<string, object>, [NotNull] BackgroundProcessingServerOptions)`
- `#ctor([NotNull] JobStorage, [NotNull] IEnumerable<IBackgroundProcessDispatcherBuilder>, [NotNull] IDictionary<string, object>, [NotNull] BackgroundProcessingServerOptions)`
- `Dispose`
- `SendStop`
- `WaitForShutdown(TimeSpan)`
- `WaitForShutdownAsync(CancellationToken)`

**Fields:**

- `DefaultShutdownTimeout`


#### `BackgroundProcessingServerOptions`

**Methods:**

- `#ctor`

**Properties:**

- `CancellationCheckInterval`
- `ExcludeStorageProcesses`
- `HeartbeatInterval`
- `LastChanceTimeout`
- `RestartDelay`
- `RetryDelay`
- `ServerCheckInterval`
- `ServerName`
- `ServerTimeout`
- `ShutdownTimeout`
- `StopTimeout`


#### `BackgroundServerContext`

**Methods:**

- `#ctor([NotNull] string, [NotNull] JobStorage, [NotNull] IDictionary<string, object>, CancellationToken, CancellationToken, CancellationToken)`

**Properties:**

- `Properties`
- `ServerId`
- `ShutdownToken`
- `StoppedToken`
- `StoppingToken`
- `Storage`


#### `DelayedJobScheduler`

Represents a background process responsible for enqueueing delayed
jobs.

**Methods:**

- `#ctor`
  - Initializes a new instance of the `DelayedJobScheduler`
class with the `DefaultPollingDelay` value as a
delay between runs.
- `#ctor(TimeSpan)`
  - Initializes a new instance of the `DelayedJobScheduler`
class with a specified polling interval.
  - `pollingDelay`: Delay between scheduler runs.
- `#ctor(TimeSpan, Hangfire.States.IBackgroundJobStateChanger)`
  - Initializes a new instance of the `DelayedJobScheduler`
class with a specified polling interval and given state changer.
  - `pollingDelay`: Delay between scheduler runs.
  - `stateChanger`: State changer to use for background jobs.
- `#ctor(TimeSpan, [NotNull] IBackgroundJobStateChanger)`
- `Execute(BackgroundProcessContext)`
- `Execute(Hangfire.Server.BackgroundProcessContext)`
- `ToString`

**Properties:**

- `MaxDegreeOfParallelism`
  - Gets or sets the maximum degree of parallelism for a scheduler instance.
When greater than `1` and batching enabling, delayed jobs will
be scheduled in parallel under separate connections, increasing the
throughput.
- `TaskScheduler`
  - Gets or sets a task scheduler that will be used when parallel scheduling
is enabled via the `MaxDegreeOfParallelism` option.

**Fields:**

- `DefaultPollingDelay`
  - Represents a default polling interval for delayed job scheduler.
This field is read-only.
  - remarks: The value of this field is `TimeSpan.FromSeconds(15)`.


#### `IBackgroundJobPerformer`


#### `IBackgroundProcess`

Provides methods for defining processes that will be executed in a
background thread by `BackgroundProcessingServer`.

**Methods:**

- `Execute(Hangfire.Server.BackgroundProcessContext)`
  - `context`: Context for a background process.


#### `IBackgroundProcessAsync`


#### `IBackgroundProcessDispatcherBuilder`


#### `IBackgroundProcessingServer`


#### `IServerComponent`


#### `IServerExceptionFilter`

Defines methods that are required for the server exception filter.

**Methods:**

- `OnServerException(Hangfire.Server.ServerExceptionContext)`
  - Called when an exception occurred during the performance of the job.
  - `filterContext`: The filter context.


#### `IServerFilter`

Defines methods that are required for a server filter.

**Methods:**

- `OnPerformed(Hangfire.Server.PerformedContext)`
  - Called after the performance of the job.
  - `context`: The filter context.
- `OnPerforming(Hangfire.Server.PerformingContext)`
  - Called before the performance of the job.
  - `context`: The filter context.


#### `IServerProcess`


#### `JobAbortedException`

**Methods:**

- `#ctor`
- `#ctor(Serialization.SerializationInfo, Serialization.StreamingContext)`
  - Initializes a new instance of the `JobAbortedException` class
with serialized data.
  - `info`: The `SerializationInfo` that holds the serialized object data about the exception being thrown.
  - `context`: The `StreamingContext` that contains contextual information about the source or destination.


#### `JobPerformanceException`

**Methods:**

- `#ctor(Serialization.SerializationInfo, Serialization.StreamingContext)`
  - Initializes a new instance of the `JobPerformanceException` class
with serialized data.
  - `info`: The `SerializationInfo` that holds the serialized object data about the exception being thrown.
  - `context`: The `StreamingContext` that contains contextual information about the source or destination.
- `#ctor(string, Exception)`
- `#ctor(string, Exception, string)`

**Properties:**

- `JobId`
  - The Background Job Id of the Job instance this exception has been raised for


#### `NamespaceDoc`

The `Server` namespace contains types that are responsible
for background processing. You may use them to customize your processing pipeline
by implementing the `IServerFilter` interface or define your own
continuously-running background processes by implementing the `IBackgroundProcess`
as well as create completely custom instances of `BackgroundProcessingServer`.


#### `PerformContext`

Provides information about the context in which the job
is performed.

**Methods:**

- `#ctor([CanBeNull] JobStorage, [NotNull] IStorageConnection, [NotNull] BackgroundJob, [NotNull] IJobCancellationToken)`
- `#ctor([NotNull] IStorageConnection, [NotNull] BackgroundJob, [NotNull] IJobCancellationToken)`
- `#ctor([NotNull] PerformContext)`
- `GetJobParameter<T>([NotNull] string)`
- `GetJobParameter<T>([NotNull] string, bool)`
- `SetJobParameter([NotNull] string, object)`

**Properties:**

- `BackgroundJob`
- `CancellationToken`
- `Connection`
- `Items`
  - Gets an instance of the key-value storage. You can use it
to pass additional information between different client filters
or just between different methods.
- `Performer`
- `ServerId`
- `Storage`

**Fields:**

- `CreatedAt`
- `Job`
- `JobId`


#### `PerformedContext`

Provides the context for the `OnPerformed`
method of the `IServerFilter` interface.

**Methods:**

- `#ctor([NotNull] PerformContext, [CanBeNull]object, bool, [CanBeNull] Exception)`

**Properties:**

- `Canceled`
  - Gets a value that indicates that this `PerformedContext`
object was canceled.
- `Exception`
  - Gets an exception that occurred during the performance of the job.
- `ExceptionHandled`
  - Gets or sets a value that indicates that this `PerformedContext`
object handles an exception occurred during the performance of the job.
- `Result`
  - Gets a value that was returned by the job.


#### `PerformingContext`

Provides the context for the `OnPerforming`
method of the `IServerFilter` interface.

**Methods:**

- `#ctor(PerformContext)`

**Properties:**

- `Canceled`
  - Gets or sets a value that indicates that this `PerformingContext`
object was canceled.


#### `RecurringJobScheduler`

Represents a background process responsible for enqueueing recurring
jobs.

**Methods:**

- `#ctor`
  - Initializes a new instance of the `RecurringJobScheduler`
class with default background job factory.
- `#ctor(Hangfire.Client.IBackgroundJobFactory)`
  - Initializes a new instance of the `RecurringJobScheduler`
class with custom background job factory and a state machine.
  - `factory`: Factory that will be used to create background jobs.
- `#ctor(Hangfire.Client.IBackgroundJobFactory, TimeSpan)`
  - Initializes a new instance of the `RecurringJobScheduler` class
with custom background job factory, state machine and clocks.
  - `factory`: Factory that will be used to create background jobs.
  - `pollingDelay`: Delay before another polling attempt, when no jobs scheduled yet.
- `#ctor(Hangfire.Client.IBackgroundJobFactory, TimeSpan, Hangfire.ITimeZoneResolver)`
  - Initializes a new instance of the `RecurringJobScheduler` class
with custom background job factory, state machine and clocks.
  - `factory`: Factory that will be used to create background jobs.
  - `pollingDelay`: Delay before another polling attempt, when no jobs scheduled yet.
  - `timeZoneResolver`: Function that returns a time zone object by its identifier.
- `#ctor([NotNull] IBackgroundJobFactory)`
- `#ctor([NotNull] IBackgroundJobFactory, TimeSpan)`
- `#ctor([NotNull] IBackgroundJobFactory, TimeSpan, [NotNull] ITimeZoneResolver)`
- `#ctor([NotNull] IBackgroundJobFactory, TimeSpan, [NotNull] ITimeZoneResolver, [NotNull] Func<DateTime>)`
- `Execute(BackgroundProcessContext)`
- `Execute(Hangfire.Server.BackgroundProcessContext)`
- `ToString`

**Properties:**

- `MaxDegreeOfParallelism`
  - Gets or sets the maximum degree of parallelism for a scheduler instance.
When greater than `1` and batching enabling, recurring jobs will
be scheduled in parallel under separate connections, increasing the
throughput.
- `TaskScheduler`
  - Gets or sets a task scheduler that will be used when parallel scheduling
is enabled via the `MaxDegreeOfParallelism` option.


#### `ServerContext`

**Methods:**

- `#ctor`

**Properties:**

- `Queues`
- `WorkerCount`


#### `ServerExceptionContext`

Provides the context for the `OnServerException`
method of the `IServerExceptionFilter` interface.

**Methods:**

- `#ctor(PerformContext, Exception)`

**Properties:**

- `Exception`
  - Gets an exception that occurred during the performance of the job.
- `ExceptionHandled`
  - Gets or sets a value that indicates that this `ServerExceptionContext`
object handles an exception occurred during the performance of the job.


#### `ServerOwinExtensions`

**Methods:**

- `RunHangfireServer(IAppBuilder, BackgroundJobServer)`


#### `ServerWatchdogOptions`

**Methods:**

- `#ctor`

**Properties:**

- `CheckInterval`
- `ServerTimeout`


#### `Worker`

Represents a background process responsible for processing
fire-and-forget jobs.

**Methods:**

- `#ctor`
- `#ctor([NotNull] IEnumerable<string>, [NotNull] IBackgroundJobPerformer, [NotNull] IBackgroundJobStateChanger)`
- `#ctor([NotNull] params string[])`
- `Execute(BackgroundProcessContext)`
- `Execute(Hangfire.Server.BackgroundProcessContext)`

**Fields:**

- `TransactionalAcknowledgePrefix`


### namespace `Hangfire.States`

#### `ApplyStateContext`

**Methods:**

- `#ctor([NotNull] IWriteOnlyTransaction, [NotNull] ElectStateContext)`
- `#ctor([NotNull] JobStorage, [NotNull] IStorageConnection, [NotNull] IWriteOnlyTransaction, [NotNull] BackgroundJob, [NotNull] IState, [CanBeNull] string)`
- `GetJobParameter<T>([NotNull] string)`
- `GetJobParameter<T>([NotNull] string, bool)`

**Properties:**

- `BackgroundJob`
- `Connection`
- `CustomData`
- `JobExpirationTimeout`
- `NewState`
- `OldStateName`
- `StateMachine`
- `Storage`
- `Transaction`


#### `AwaitingState`

Defines the intermediate state of a background job when it is waiting
for a parent background job to be finished before it is moved to the
`EnqueuedState` by the `ContinuationsSupportAttribute`
filter.

**Methods:**

- `#ctor([NotNull] string)`
- `#ctor([NotNull] string, [NotNull] IState)`
- `#ctor([NotNull] string, [NotNull] IState, JobContinuationOptions)`
- `#ctor([NotNull] string, [NotNull] IState, JobContinuationOptions, TimeSpan)`
- `#ctor(string)`
  - Initializes a new instance of the `AwaitingState` class with
the specified parent background job id and with an instance of the
`EnqueuedState` class as a next state.
  - `parentId`: The identifier of a background job to wait for.
- `#ctor(string, Hangfire.States.IState)`
  - Initializes a new instance of the `AwaitingState` class with
the specified parent job id and next state.
  - `parentId`: The identifier of a background job to wait for.
  - `nextState`: The next state for the continuation.
- `#ctor(string, Hangfire.States.IState, Hangfire.JobContinuationOptions)`
  - Initializes a new instance of the `AwaitingState` class with
the given options along with other parameters.
  - `parentId`: The identifier of a background job to wait for.
  - `nextState`: The next state for the continuation.
  - `options`: Options to configure a continuation.
- `#ctor(string, Hangfire.States.IState, Hangfire.JobContinuationOptions, TimeSpan)`
  - Initializes a new instance of the `AwaitingState` class with
the specified expiration time along with other parameters.
  - `parentId`: The identifier of a background job to wait for.
  - `nextState`: The next state for the continuation.
  - `options`: Options to configure the continuation.
  - `expiration`: The expiration time for the continuation.
- `SerializeData`
  - remarks: Returning dictionary contains the following keys. You can obtain
the state data by using the `GetStateData`
method.

Key
Type
Deserialize Method
Notes

- `ParentId`
`String`
Not required
Please see the `ParentId` property.

- `NextState`
`IState`
`Deserialize<T>` with
`TypedInternal`
Please see the `NextState` property.

- `Options`
`JobContinuationOptions`
`Parse` with `JobContinuationOptions`
Please see the `Options` property.

**Properties:**

- `Expiration`
  - Gets the expiration time of a background job continuation.
- `IgnoreJobLoadException`
  - remarks: Always returns for the `AwaitingState`.
Please see the description of this property in the
`IgnoreJobLoadException`
article.
- `IsFinal`
  - remarks: Always returns for the `AwaitingState`.
Please refer to the `IsFinal` documentation
for the details.
- `Name`
  - remarks: Always equals to `StateName` for the `AwaitingState`.
Please see the remarks section of the `Name`
article for the details.
- `NextState`
  - Gets the next state, to which a background job will be moved.
- `Options`
  - Gets the continuation options associated with the current state.
- `ParentId`
  - Gets the identifier of a parent background job.
- `Reason`

**Fields:**

- `StateName`
  - Represents the name of the Awaiting state. This field is read-only.
  - remarks: The value of this field is `"Awaiting"`.


#### `BackgroundJobStateChanger`

**Methods:**

- `#ctor`
- `#ctor([NotNull] IJobFilterProvider)`
- `#ctor([NotNull] StateMachine)`
- `ChangeState(StateChangeContext)`


#### `DeletedState`

Defines the final state of a background job when nobody
is interested whether it was performed or not.

**Methods:**

- `#ctor`
  - Initializes a new instance of the `DeletedState` class.
- `#ctor([CanBeNull] ExceptionInfo)`
- `SerializeData`
  - remarks: Returning dictionary contains the following keys. You can obtain
the state data by using the `GetStateData`
method.

Key
Type
Deserialize Method
Notes

- `DeletedAt`
`DateTime`
`DeserializeDateTime`
Please see the `DeletedAt` property.

- `Exception`
`ExceptionInfo`
`Deserialize<T>` with `Internal` option.
Can be absent or null. Please see the `Exception` property.

**Properties:**

- `DeletedAt`
  - Gets a date/time when the current state instance was created.
- `ExceptionInfo`
- `IgnoreJobLoadException`
  - remarks: Always returns for the `DeletedState`.
Please see the description of this property in the
`IgnoreJobLoadException`
article.
- `IsFinal`
  - remarks: Always returns for the `DeletedState`.
Please refer to the `IsFinal` documentation
for the details.
- `Name`
  - remarks: Always equals to `StateName` for the `DeletedState`.
Please see the remarks section of the `Name`
article for the details.
- `Reason`

**Fields:**

- `DefaultException`
- `StateName`
  - Represents the name of the Deleted state. This field is read-only.
  - remarks: The value of this field is `"Deleted"`.


#### `ElectStateContext`

**Methods:**

- `#ctor([NotNull] ApplyStateContext)`
- `#ctor([NotNull] ApplyStateContext, [CanBeNull] StateMachine)`
- `GetJobParameter<T>([NotNull] string)`
- `GetJobParameter<T>([NotNull] string, bool)`
- `SetJobParameter<T>([NotNull] string, T)`

**Properties:**

- `BackgroundJob`
- `CandidateState`
- `Connection`
- `CurrentState`
- `CustomData`
- `StateMachine`
- `Storage`
- `Transaction`

**Fields:**

- `TraversedStates`


#### `EnqueuedState`

Defines the intermediate state of a background job when it is placed
on a message queue to be processed by the `Worker`
background process as soon as possible.

**Methods:**

- `#ctor`
  - Initializes a new instance of the `EnqueuedState` class
with the `DefaultQueue` queue name.
- `#ctor([CanBeNull] string)`
- `#ctor(string)`
  - Initializes a new instance of the `EnqueuedState` class
with the specified queue name.
  - `queue`: The queue name to which a background job identifier will be added.
- `SerializeData`
  - remarks: Returning dictionary contains the following keys. You can obtain
the state data by using the `GetStateData`
method.

Key
Type
Deserialize Method
Notes

- `EnqueuedAt`
`DateTime`
`DeserializeDateTime`
Please see the `EnqueuedAt` property.

- `Queue`
`String`
Not required
Please see the `Queue` property.

**Properties:**

- `EnqueuedAt`
  - Gets a date/time when the current state instance was created.
- `IgnoreJobLoadException`
  - remarks: Always returns for the `EnqueuedState`.
Please see the description of this property in the
`IgnoreJobLoadException`
article.
- `IsFinal`
  - remarks: Always returns for the `EnqueuedState`.
Please refer to the `IsFinal` documentation
for the details.
- `Name`
  - remarks: Always equals to `StateName` for the `EnqueuedState`.
Please see the remarks section of the `Name`
article for the details.
- `Queue`
  - Gets or sets a queue name to which a background job identifier
will be added.
  - remarks: Queue name must consist only of lowercase letters, digits and
underscores, other characters aren't permitted. Some examples:

- `"critical"` (good)

- `"worker_1"` (good)

- `"documents queue"` (bad, whitespace)

- `"MyQueue"` (bad, capital letters)
- `Reason`

**Fields:**

- `DefaultQueue`
  - Represents the default queue name. This field is constant.
  - remarks: The value of this field is `"default"`.
- `StateName`
  - Represents the name of the Enqueued state. This field is read-only.
  - remarks: The value of this field is `"Enqueued"`.


#### `Enumerator`

**Methods:**

- `#ctor(List<IStateHandler>, IEnumerable<IStateHandler>, string)`
- `MoveNext`

**Fields:**

- `Current`


#### `FailedState`

Defines the intermediate state of a background job when its processing
was interrupted by an exception and it is a developer's responsibility
to decide what to do with it next.

**Methods:**

- `#ctor(Exception)`
  - Initializes a new instance of the `FailedState` class
with the given exception.
  - `exception`: Exception that occurred during the background
job processing.
- `#ctor(Exception, string)`
  - Initializes a new instance of the `FailedState` class
with the given exception and specified server id.
  - `exception`: Exception that occurred during the background job processing.
  - `serverId`: Server Id on which the exception occurred.
- `#ctor([NotNull] Exception)`
- `#ctor([NotNull] Exception, [CanBeNull] string)`
- `SerializeData`
  - remarks: Returning dictionary contains the following keys. You can obtain
the state data by using the `GetStateData`
method.

Key
Type
Deserialize Method
Notes

- `FailedAt`
`DateTime`
`DeserializeDateTime`
Please see the `FailedAt` property.

- `ExceptionType`
`String`
Not required
The full name of the current exception type.

- `ExceptionMessage`
`String`
Not required
Message that describes the current exception.

- `ExceptionDetails`
`String`
Not required
String representation of the current exception.

**Properties:**

- `Exception`
  - Gets the exception that occurred during the background job processing.
- `FailedAt`
  - Gets a date/time when the current state instance was created.
- `IgnoreJobLoadException`
  - remarks: Always returns for the `FailedState`.
Please see the description of this property in the
`IgnoreJobLoadException`
article.
- `IncludeFileInfo`
- `IsFinal`
  - remarks: Always returns for the `FailedState`.
Please refer to the `IsFinal` documentation
for the details.
- `MaxLinesInStackTrace`
- `Name`
  - remarks: Always equals to `StateName` for the `FailedState`.
Please see the remarks section of the `Name`
article for the details.
- `Reason`
- `ServerId`
  - Gets the server identifier on which the exception occurred.

**Fields:**

- `StateName`
  - Represents the name of the Failed state. This field is read-only.
  - remarks: The value of this field is `"Failed"`.


#### `IApplyStateFilter`

Provides methods that are required for a state changed filter.

**Methods:**

- `OnStateApplied(Hangfire.States.ApplyStateContext, Hangfire.Storage.IWriteOnlyTransaction)`
  - Called after the specified state was applied
to the job within the given transaction.
- `OnStateUnapplied(Hangfire.States.ApplyStateContext, Hangfire.Storage.IWriteOnlyTransaction)`
  - Called when the state with specified state was
unapplied from the job within the given transaction.


#### `IBackgroundJobStateChanger`

**Methods:**

- `ChangeState(Hangfire.States.StateChangeContext)`
  - Attempts to change the state of a job, respecting any applicable job filters and state handlers.
  - returns: `Null` if a constraint has failed, otherwise the final applied state
  - remarks: Also ensures that the job data can be loaded for this job


#### `IElectStateFilter`

Defines methods that are required for a state changing filter.

**Methods:**

- `OnStateElection(Hangfire.States.ElectStateContext)`
  - Called when the current state of the job is being changed to the
specified candidate state.
This state change could be intercepted and the final state could
be changed through setting the different state in the context
in an implementation of this method.


#### `IState`

Provides the essential members for describing a background job state.

**Methods:**

- `SerializeData`
  - Gets a serialized representation of the current state.
  - returns: A dictionary with serialized properties of the current state.
  - remarks: Returning dictionary contains the serialized properties of a state. You can obtain
the state data by using the `GetStateData`
method. Please refer to documentation for this method in implementors to learn
which key/value pairs are available.

**Properties:**

- `IgnoreJobLoadException`
  - Gets whether transition to this state should ignore job de-serialization
exceptions.
  - remarks: During a state transition, an instance of the `Job` class
is deserialized to get state changing filters, and to allow `IStateHandler` to perform additional work related to the state.



However we cannot always deserialize a job, for example, when job method was
removed from the code base or its assembly reference is missing. Since background
processing is impossible anyway, the `IBackgroundJobStateChanger`
moves such a background job to the `FailedState` in this case to
highlight a problem to the developers (because deserialization exception may
occur due to bad refactorings or other programming mistakes).



However, in some exceptional cases we can ignore deserialization exceptions,
and allow a state transition for some states that does not require a `Job`
instance. `FailedState` itself and `DeletedState` are
examples of such a behavior.

In general, implementers should return when implementing
this property.
- `IsFinal`
  - Gets if the current state is a final one.
  - remarks: Final states define a termination stage of a background job
processing pipeline. Background jobs in a final state is considered
as finished with no further processing required.



The `IBackgroundJobStateChanger` marks
finished background jobs to be expired within an interval that
is defined in the `JobExpirationTimeout`
property that is available from a state changing filter that
implements the `IApplyStateFilter` interface.

When implementing this property, always hard-code this property to
or . Hangfire does
not work with states that can be both intermediate and
final yet. Don't define a public setter for this property.
- `Name`
  - Gets the unique name of the state.
  - remarks: The state name is used to differentiate one state from another
during the state change process. So all the implemented states
should have a unique state name. Please use one-word names
that start with a capital letter, in a past tense in English for
your state names, for example:

- `Succeeded`

- `Enqueued`

- `Deleted`

- `Failed`

The returning value should be hard-coded, no modifications of
this property should be allowed to a user. Implementors should
not add a public setter on this property.
- `Reason`
  - Gets the human-readable reason of a state transition.
  - remarks: The reason is usually displayed in the Dashboard UI to simplify
the understanding of a background job lifecycle by providing a
human-readable text that explains why a background job is moved
to the corresponding state. Here are some examples:

- Can not change the state to 'Enqueued': target
method was not found

- Exceeded the maximum number of retry attempts
The reason value is usually not hard-coded in a state implementation,
allowing users to change it when creating an instance of a state
through the public setter.


#### `IStateHandler`

Provides a mechanism for performing custom actions when applying or
unapplying the state of a background job by `StateMachine`.

**Methods:**

- `Apply(Hangfire.States.ApplyStateContext, Hangfire.Storage.IWriteOnlyTransaction)`
  - Performs additional actions when applying a state whose name is
equal to the `StateName` property.
  - `context`: The context of a state applying process.
  - `transaction`: The current transaction of a state applying process.
- `Unapply(Hangfire.States.ApplyStateContext, Hangfire.Storage.IWriteOnlyTransaction)`
  - Performs additional actions when unapplying a state whose name
is equal to the `StateName` property.
  - `context`: The context of a state applying process.
  - `transaction`: The current transaction of a state applying process.

**Properties:**

- `StateName`
  - Gets the name of a state, for which custom actions will be
performed.


#### `IStateMachine`

Provides a mechanism for running state election and state applying processes.

**Methods:**

- `ApplyState(Hangfire.States.ApplyStateContext)`
  - Performs the state applying process, where a current background job
will be moved to the elected state.
  - `context`: The context of a state applying process.


#### `NamespaceDoc`

The `States` namespace contains types that describe
background job states and the transitions between them. You can implement
custom `IElectStateFilter` or `IApplyStateFilter`
to customize the state changing pipeline, or define your own state by
implementing the `IState` interface.


#### `ProcessingState`

Defines the intermediate state of a background job when a
`Worker` has started to process it.

**Methods:**

- `SerializeData`
  - remarks: Returning dictionary contains the following keys. You can obtain
the state data by using the `GetStateData`
method.

Key
Type
Deserialize Method
Notes

- `StartedAt`
`DateTime`
`DeserializeDateTime`
Please see the `StartedAt` property.

- `ServerId`
`String`
Not required
Please see the `ServerId` property.

- `WorkerId`
`String`
Not required
Please see the `WorkerId` property.

**Properties:**

- `IgnoreJobLoadException`
  - remarks: Always returns for the `ProcessingState`.
Please see the description of this property in the
`IgnoreJobLoadException`
article.
- `IsFinal`
  - remarks: Always returns for the `ProcessingState`.
Please refer to the `IsFinal` documentation
for the details.
- `Name`
  - remarks: Always equals to `StateName` for the `ProcessingState`.
Please see the remarks section of the `Name`
article for the details.
- `Reason`
- `ServerId`
  - Gets the instance id of an instance of the `BackgroundProcessingServer`
class, whose `Worker` background process started to process an
enqueued background job.
- `StartedAt`
  - Gets a date/time when the current state instance was created.
- `WorkerId`
  - Gets the identifier of a `Worker` that started to
process an enqueued background job.

**Fields:**

- `StateName`
  - Represents the name of the Processing state. This field is read-only.
  - remarks: The value of this field is `"Processing"`.


#### `ScheduledState`

Defines the intermediate state of a background job when it is placed
on a schedule to be moved to the `EnqueuedState` in the future
by `DelayedJobScheduler` background process.

**Methods:**

- `#ctor(DateTime)`
  - Initializes a new instance of the `ScheduledState`
class with the specified date/time in UTC format when a job should
be moved to the `EnqueuedState`.
  - `enqueueAt`: The date/time when a job will be moved to the
`EnqueuedState`.
- `#ctor(TimeSpan)`
  - Initializes a new instance of the `ScheduledState` class
with the specified time interval after which a job should be moved to
the `EnqueuedState`.
  - `enqueueIn`: The time interval after which a job will be
moved to the `EnqueuedState`.
- `SerializeData`
  - remarks: Returning dictionary contains the following keys. You can obtain
the state data by using the `GetStateData`
method.

Key
Type
Deserialize Method
Notes

- `EnqueueAt`
`DateTime`
`DeserializeDateTime`
Please see the `EnqueueAt` property.

- `ScheduledAt`
`DateTime`
`DeserializeDateTime`
Please see the `ScheduledAt` property.

**Properties:**

- `EnqueueAt`
  - Gets a date/time when a background job should be enqueued.
- `IgnoreJobLoadException`
  - remarks: Always returns for the `ScheduledState`.
Please see the description of this property in the
`IgnoreJobLoadException`
article.
- `IsFinal`
  - remarks: Always returns for the `ScheduledState`.
Please refer to the `IsFinal` documentation
for the details.
- `Name`
  - remarks: Always equals to `StateName` for the `ScheduledState`.
Please see the remarks section of the `Name`
article for the details.
- `Reason`
- `ScheduledAt`
  - Gets a date/time when the current state instance was created.

**Fields:**

- `StateName`
  - Represents the name of the Scheduled state. This field is read-only.
  - remarks: The value of this field is `"Scheduled"`.


#### `StateChangeContext`

**Methods:**

- `#ctor([NotNull] JobStorage, [NotNull] IStorageConnection, [CanBeNull] JobStorageTransaction, [NotNull] string, [NotNull] IState, [CanBeNull] IEnumerable<string>, CancellationToken)`
- `#ctor([NotNull] JobStorage, [NotNull] IStorageConnection, [NotNull] string, [NotNull] IState)`
- `#ctor([NotNull] JobStorage, [NotNull] IStorageConnection, [NotNull] string, [NotNull] IState, [CanBeNull] IEnumerable<string>, CancellationToken)`
- `#ctor([NotNull] JobStorage, [NotNull] IStorageConnection, [NotNull] string, [NotNull] IState, [CanBeNull] params string[])`

**Properties:**

- `BackgroundJobId`
- `CancellationToken`
- `CompleteJob`
- `Connection`
- `CustomData`
- `DisableFilters`
- `ExpectedStates`
- `NewState`
- `ProcessedJob`
- `ServerId`
- `Storage`
- `Transaction`


#### `StateContext`

**Properties:**

- `BackgroundJob`

**Fields:**

- `CreatedAt`
- `Job`
- `JobId`


#### `StateHandlerCollection`

**Methods:**

- `AddHandler(IStateHandler)`
- `AddRange(IEnumerable<IStateHandler>)`
- `GetHandlers(string)`


#### `StateMachine`

**Methods:**

- `#ctor([NotNull] IJobFilterProvider)`
- `ApplyState(ApplyStateContext)`

**Fields:**

- `InnerStateMachine`


#### `SucceededState`

Defines the final state of a background job when a `Worker`
performed an enqueued job without any exception thrown during the performance.

**Methods:**

- `#ctor(object, long, long)`
- `SerializeData`
  - remarks: Returning dictionary contains the following keys. You can obtain
the state data by using the `GetStateData`
method.

Key
Type
Deserialize Method
Notes

- `SucceededAt`
`DateTime`
`DeserializeDateTime`
Please see the `SucceededAt` property.

- `PerformanceDuration`
`Int64`
`Parse` with
`InvariantCulture`
Please see the `PerformanceDuration` property.

- `Latency`
`Int64`
`Parse` with
`InvariantCulture`
Please see the `Latency` property.

- `Result`
`Object`
`Serialize<T>` with `User` argument
Please see the `Result` property.


This key may be missing from the dictionary, when the return
value was . Always check for its existence
before using it.

**Properties:**

- `IgnoreJobLoadException`
  - remarks: Always returns for the `SucceededState`.
Please see the description of this property in the
`IgnoreJobLoadException`
article.
- `IsFinal`
  - remarks: Always returns for the `SucceededState`.
Please refer to the `IsFinal` documentation
for the details.
- `Latency`
  - Gets the total number of milliseconds passed from a job
creation time till the start of the performance.
- `Name`
  - remarks: Always equals to `StateName` for the `SucceededState`.
Please see the remarks section of the `Name`
article for the details.
- `PerformanceDuration`
  - Gets the total milliseconds elapsed from a processing start.
- `Reason`
- `Result`
  - Gets the value returned by a job method.
- `SucceededAt`
  - Gets a date/time when the current state instance was created.

**Fields:**

- `StateName`
  - Represents the name of the Succeeded state. This field is read-only.
  - remarks: The value of this field is `"Succeeded"`.


### namespace `Hangfire.Storage`

#### `BackgroundServerGoneException`

**Methods:**

- `#ctor`
- `#ctor(Serialization.SerializationInfo, Serialization.StreamingContext)`
  - Initializes a new instance of the `BackgroundServerGoneException` class
with serialized data.
  - `info`: The `SerializationInfo` that holds the serialized object data about the exception being thrown.
  - `context`: The `StreamingContext` that contains contextual information about the source or destination.


#### `Connection`

**Fields:**

- `BatchedGetFirstByLowest`
- `GetSetContains`
- `GetUtcDateTime`
- `LimitedGetSetCount`


#### `DistributedLockTimeoutException`

**Methods:**

- `#ctor(Serialization.SerializationInfo, Serialization.StreamingContext)`
  - Initializes a new instance of the `DistributedLockTimeoutException` class
with serialized data.
  - `info`: The `SerializationInfo` that holds the serialized object data about the exception being thrown.
  - `context`: The `StreamingContext` that contains contextual information about the source or destination.
- `#ctor(string)`

**Properties:**

- `Resource`


#### `IFetchedJob`


#### `IMonitoringApi`


#### `IStorageConnection`


#### `IWriteOnlyTransaction`


#### `InvocationData`

**Methods:**

- `#ctor(string, string, string, string)`
- `#ctor(string, string, string, string, string)`
- `Deserialize`
- `DeserializeJob`
- `DeserializePayload(string)`
- `Serialize(Job)`
- `SerializeJob(Job)`
- `SerializePayload(bool)`
- `SetTypeResolver([CanBeNull] Func<string, Type>)`
- `SetTypeSerializer([CanBeNull] Func<Type, string>)`

**Properties:**

- `Arguments`
- `Method`
- `ParameterTypes`
- `Queue`
- `Type`


#### `JobData`

**Methods:**

- `EnsureLoaded`

**Properties:**

- `CreatedAt`
- `InvocationData`
- `Job`
- `LoadException`
- `ParametersSnapshot`
- `State`


#### `JobStorageConnection`

**Methods:**

- `AcquireDistributedLock(string, TimeSpan)`
- `AnnounceServer(string, ServerContext)`
- `CreateExpiredJob(Job, IDictionary<string, string>, DateTime, TimeSpan)`
- `CreateWriteTransaction`
- `Dispose`
- `FetchNextJob(string[], CancellationToken)`
- `GetAllEntriesFromHash(string)`
- `GetAllItemsFromList([NotNull] string)`
- `GetAllItemsFromSet(string)`
- `GetCounter([NotNull] string)`
- `GetFirstByLowestScoreFromSet(string, double, double)`
- `GetFirstByLowestScoreFromSet(string, double, double, int)`
- `GetHashCount([NotNull] string)`
- `GetHashTtl([NotNull] string)`
- `GetJobData(string)`
- `GetJobParameter(string, string)`
- `GetListCount([NotNull] string)`
- `GetListTtl([NotNull] string)`
- `GetRangeFromList([NotNull] string, int, int)`
- `GetRangeFromSet([NotNull] string, int, int)`
- `GetSetContains([NotNull] string, [NotNull] string)`
- `GetSetCount([NotNull] IEnumerable<string>, int)`
- `GetSetCount([NotNull] string)`
- `GetSetTtl([NotNull] string)`
- `GetStateData(string)`
- `GetUtcDateTime`
- `GetValueFromHash([NotNull] string, [NotNull] string)`
- `Heartbeat(string)`
- `RemoveServer(string)`
- `RemoveTimedOutServers(TimeSpan)`
- `SetJobParameter(string, string, string)`
- `SetRangeInHash(string, IEnumerable<KeyValuePair<string, string>>)`


#### `JobStorageFeatures`

**Methods:**

- `GetNotSupportedException([NotNull] string)`

**Properties:**

- `Connection`
- `Monitoring`
- `Transaction`

**Fields:**

- `ExtendedApi`
- `JobQueueProperty`
- `ProcessesInsteadOfComponents`


#### `JobStorageMonitor`

**Methods:**

- `AwaitingCount`
- `AwaitingJobs(int, int)`
- `DeletedByDatesCount`
- `DeletedJobs(int, int)`
- `DeletedListCount`
- `EnqueuedCount(string)`
- `EnqueuedJobs(string, int, int)`
- `FailedByDatesCount`
- `FailedCount`
- `FailedJobs(int, int)`
- `FetchedCount(string)`
- `FetchedJobs(string, int, int)`
- `GetStatistics`
- `HourlyDeletedJobs`
- `HourlyFailedJobs`
- `HourlySucceededJobs`
- `JobDetails(string)`
- `ProcessingCount`
- `ProcessingJobs(int, int)`
- `Queues`
- `ScheduledCount`
- `ScheduledJobs(int, int)`
- `Servers`
- `SucceededByDatesCount`
- `SucceededJobs(int, int)`
- `SucceededListCount`


#### `JobStorageTransaction`

**Methods:**

- `AcquireDistributedLock([NotNull] string, TimeSpan)`
- `AddJobState(string, IState)`
- `AddRangeToSet([NotNull] string, [NotNull] IList<string>)`
- `AddToQueue(string, string)`
- `AddToSet(string, string)`
- `AddToSet(string, string, double)`
- `Commit`
- `CreateJob([NotNull] Job, [NotNull] IDictionary<string, string>, DateTime, TimeSpan)`
- `DecrementCounter(string)`
- `DecrementCounter(string, TimeSpan)`
- `Dispose`
- `ExpireHash([NotNull] string, TimeSpan)`
- `ExpireJob(string, TimeSpan)`
- `ExpireList([NotNull] string, TimeSpan)`
- `ExpireSet([NotNull] string, TimeSpan)`
- `IncrementCounter(string)`
- `IncrementCounter(string, TimeSpan)`
- `InsertToList(string, string)`
- `PersistHash([NotNull] string)`
- `PersistJob(string)`
- `PersistList([NotNull] string)`
- `PersistSet([NotNull] string)`
- `RemoveFromList(string, string)`
- `RemoveFromQueue([NotNull] IFetchedJob)`
- `RemoveFromSet(string, string)`
- `RemoveHash(string)`
- `RemoveSet([NotNull] string)`
- `SetJobParameter([NotNull] string, [NotNull] string, [CanBeNull] string)`
- `SetJobState(string, IState)`
- `SetRangeInHash(string, IEnumerable<KeyValuePair<string, string>>)`
- `TrimList(string, int, int)`


#### `Monitoring`

**Fields:**

- `AwaitingJobs`
- `DeletedStateGraphs`


#### `NamespaceDoc`

The Hangfire.Storage namespaces contain abstract types like `JobStorage`,
`IStorageConnection` and `IWriteOnlyTransaction` for
querying and modifying the underlying background job storage.
These types are also used to implement support for other persistent storages.


#### `NamespaceGroupDoc`

The Hangfire.Storage namespaces contain abstract types like `JobStorage`,
`IStorageConnection` and `IWriteOnlyTransaction` for
querying and modifying the underlying background job storage.
These types are also used to implement support for other persistent storages.


#### `RecurringJobDto`

**Properties:**

- `CreatedAt`
- `Cron`
- `Error`
- `Id`
- `Job`
- `LastExecution`
- `LastJobId`
- `LastJobState`
- `LoadException`
- `NextExecution`
- `Queue`
- `Removed`
- `RetryAttempt`
- `TimeZoneId`


#### `StateData`

**Properties:**

- `Data`
- `Name`
- `Reason`


#### `StorageConnectionExtensions`

**Methods:**

- `AcquireDistributedJobLock([NotNull] this IStorageConnection, [NotNull] string, TimeSpan)`
- `AcquireDistributedJobLock([NotNull] this JobStorageTransaction, [NotNull] string, TimeSpan)`
- `GetRecurringJobCount([NotNull] this JobStorageConnection)`
- `GetRecurringJobIds([NotNull] this JobStorageConnection, int, int)`
- `GetRecurringJobs([NotNull] this IStorageConnection)`
- `GetRecurringJobs([NotNull] this IStorageConnection, IEnumerable<string>)`
- `GetRecurringJobs([NotNull] this JobStorageConnection, int, int)`


#### `Transaction`

**Methods:**

- `RemoveFromQueue(Type)`

**Fields:**

- `AcquireDistributedLock`
- `CreateJob`
- `SetJobParameter`


### namespace `Hangfire.Storage.Monitoring`

#### `AwaitingJobDto`

**Methods:**

- `#ctor`

**Properties:**

- `AwaitingAt`
- `InAwaitingState`
- `InvocationData`
- `Job`
- `LoadException`
- `ParentStateName`
- `StateData`


#### `DeletedJobDto`

**Methods:**

- `#ctor`

**Properties:**

- `DeletedAt`
- `InDeletedState`
- `InvocationData`
- `Job`
- `LoadException`
- `StateData`


#### `EnqueuedJobDto`

**Methods:**

- `#ctor`

**Properties:**

- `EnqueuedAt`
- `InEnqueuedState`
- `InvocationData`
- `Job`
- `LoadException`
- `State`
- `StateData`


#### `FailedJobDto`

**Methods:**

- `#ctor`

**Properties:**

- `ExceptionDetails`
- `ExceptionMessage`
- `ExceptionType`
- `FailedAt`
- `InFailedState`
- `InvocationData`
- `Job`
- `LoadException`
- `Reason`
- `StateData`


#### `FetchedJobDto`

**Properties:**

- `FetchedAt`
- `InvocationData`
- `Job`
- `LoadException`
- `State`


#### `JobDetailsDto`

**Properties:**

- `CreatedAt`
- `ExpireAt`
- `History`
- `InvocationData`
- `Job`
- `LoadException`
- `Properties`


#### `JobList<T>`

**Methods:**

- `#ctor(IEnumerable<KeyValuePair<string, TDto>>)`


#### `NamespaceDoc`

The `Monitoring` provides data transfer objects
for the `IMonitoringApi` interface.


#### `ProcessingJobDto`

**Methods:**

- `#ctor`

**Properties:**

- `InProcessingState`
- `InvocationData`
- `Job`
- `LoadException`
- `ServerId`
- `StartedAt`
- `StateData`


#### `QueueWithTopEnqueuedJobsDto`

**Properties:**

- `Fetched`
- `FirstJobs`
- `Length`
- `Name`


#### `ScheduledJobDto`

**Methods:**

- `#ctor`

**Properties:**

- `EnqueueAt`
- `InScheduledState`
- `InvocationData`
- `Job`
- `LoadException`
- `ScheduledAt`
- `StateData`


#### `ServerDto`

**Properties:**

- `Heartbeat`
- `Name`
- `Queues`
- `StartedAt`
- `WorkersCount`


#### `StateHistoryDto`

**Properties:**

- `CreatedAt`
- `Data`
- `Reason`
- `StateName`


#### `StatisticsDto`

**Properties:**

- `Awaiting`
- `Deleted`
- `Enqueued`
- `Failed`
- `Processing`
- `Queues`
- `Recurring`
- `Retries`
- `Scheduled`
- `Servers`
- `Succeeded`


#### `SucceededJobDto`

**Methods:**

- `#ctor`

**Properties:**

- `InSucceededState`
- `InvocationData`
- `Job`
- `LoadException`
- `Result`
- `StateData`
- `SucceededAt`
- `TotalDuration`


### namespace `MoreLinq`

#### `MoreEnumerable`

**Methods:**

- `Pairwise<T1, T2>(Generic.IEnumerable<T1>, Func<T1,T1,T2>)`
  - Returns a sequence resulting from applying a function to each
element in the source sequence and its
predecessor, with the exception of the first element which is
only returned as the predecessor of the second element.
  - `source`: The source sequence.
  - `resultSelector`: A transform function to apply to
each pair of sequence.
  - `<TSource>`: The type of the elements of source.
  - `<TResult>`: The type of the element of the returned sequence.
  - returns: Returns the resulting sequence.
  - remarks: This operator uses deferred execution and streams its results.


### namespace `System.Diagnostics.CodeAnalysis`

#### `BaseTypeRequiredAttribute`

**Methods:**

- `#ctor([NotNull] Type)`

**Properties:**

- `BaseType`


#### `CanBeNullAttribute`


#### `CannotApplyEqualityOperatorAttribute`


#### `ContractAnnotationAttribute`

**Methods:**

- `#ctor([NotNull] string)`
- `#ctor([NotNull] string, bool)`

**Properties:**

- `Contract`
- `ForceFullStates`


#### `HtmlAttributeValueAttribute`

**Methods:**

- `#ctor([NotNull] string)`

**Properties:**

- `Name`


#### `HtmlElementAttributesAttribute`

**Methods:**

- `#ctor`
- `#ctor([NotNull] string)`

**Properties:**

- `Name`


#### `ImplicitUseKindFlags`

**Fields:**

- `Access`
- `Assign`
- `Default`
- `InstantiatedNoFixedConstructorSignature`
- `InstantiatedWithFixedConstructorSignature`


#### `ImplicitUseTargetFlags`

**Fields:**

- `Default`
- `Itself`
- `Members`


#### `InstantHandleAttribute`


#### `InvokerParameterNameAttribute`


#### `LocalizationRequiredAttribute`

**Methods:**

- `#ctor`
- `#ctor(bool)`

**Properties:**

- `Required`


#### `MeansImplicitUseAttribute`

**Methods:**

- `#ctor`
- `#ctor(ImplicitUseKindFlags)`
- `#ctor(ImplicitUseKindFlags, ImplicitUseTargetFlags)`
- `#ctor(ImplicitUseTargetFlags)`

**Properties:**

- `TargetFlags`
- `UseKindFlags`


#### `NotNullAttribute`


#### `NotifyPropertyChangedInvocatorAttribute`

**Methods:**

- `#ctor`
- `#ctor(string)`

**Properties:**

- `ParameterName`


#### `PublicAPIAttribute`

**Methods:**

- `#ctor`
- `#ctor([NotNull] string)`

**Properties:**

- `Comment`


#### `PureAttribute`


#### `StringFormatMethodAttribute`

**Methods:**

- `#ctor(string)`

**Properties:**

- `FormatParameterName`


#### `UsedImplicitlyAttribute`

**Methods:**

- `#ctor`
- `#ctor(ImplicitUseKindFlags)`
- `#ctor(ImplicitUseKindFlags, ImplicitUseTargetFlags)`
- `#ctor(ImplicitUseTargetFlags)`

**Properties:**

- `TargetFlags`
- `UseKindFlags`



## package `Hangfire.SqlServer` v1.8.23

### namespace `Hangfire`

#### `SqlServerStorageExtensions`

**Methods:**

- `UseSqlServerStorage([NotNull] this IGlobalConfiguration, [NotNull] Func<DbConnection>)`
- `UseSqlServerStorage([NotNull] this IGlobalConfiguration, [NotNull] Func<DbConnection>, [NotNull] SqlServerStorageOptions)`
- `UseSqlServerStorage([NotNull] this IGlobalConfiguration, [NotNull] string)`
- `UseSqlServerStorage([NotNull] this IGlobalConfiguration, [NotNull] string, [NotNull] SqlServerStorageOptions)`


### namespace `Hangfire.SqlServer`

#### `EnqueuedAndFetchedCountDto`

**Properties:**

- `EnqueuedCount`
- `FetchedCount`


#### `IPersistentJobQueue`


#### `IPersistentJobQueueMonitoringApi`


#### `IPersistentJobQueueProvider`


#### `PersistentJobQueueProviderCollection`

**Methods:**

- `#ctor(IPersistentJobQueueProvider)`
- `Add(IPersistentJobQueueProvider, IEnumerable<string>)`
- `GetEnumerator`
- `GetProvider(string)`


#### `SqlServerBootstrapperConfigurationExtensions`

**Methods:**

- `UseSqlServerStorage(IBootstrapperConfiguration, string)`
- `UseSqlServerStorage(IBootstrapperConfiguration, string, SqlServerStorageOptions)`


#### `SqlServerDistributedLock`

**Methods:**

- `#ctor([NotNull] SqlServerStorage, [NotNull] string, TimeSpan)`
- `Dispose`


#### `SqlServerDistributedLockException`

**Methods:**

- `#ctor(Serialization.SerializationInfo, Serialization.StreamingContext)`
  - Initializes a new instance of the `SqlServerDistributedLockException` class
with serialized data.
  - `info`: The `SerializationInfo` that holds the serialized object data about the exception being thrown.
  - `context`: The `StreamingContext` that contains contextual information about the source or destination.
- `#ctor(string)`


#### `SqlServerObjectsInstaller`

**Methods:**

- `GetInstallScript(string, bool)`
- `Install(DbConnection)`
- `Install(DbConnection, string)`
- `Install(DbConnection, string, bool)`

**Fields:**

- `LatestSchemaVersion`
- `RequiredSchemaVersion`


#### `SqlServerStorage`

**Methods:**

- `#ctor(Common.DbConnection)`
  - Initializes a new instance of the `SqlServerStorage` class with
explicit instance of the `DbConnection` class that will be used
to query the data.
- `#ctor(Common.DbConnection, Hangfire.SqlServer.SqlServerStorageOptions)`
  - Initializes a new instance of the `SqlServerStorage` class with
explicit instance of the `DbConnection` class that will be used
to query the data, with the given options.
- `#ctor(Func<Common.DbConnection>)`
  - Initializes a new instance of the `SqlServerStorage` class with
a connection factory `Func<T>` class that will be invoked
to create new database connections for querying the data.
- `#ctor(Func<Common.DbConnection>, Hangfire.SqlServer.SqlServerStorageOptions)`
  - Initializes a new instance of the `SqlServerStorage` class with
a connection factory `Func<T>` class that will be invoked
to create new database connections for querying the data.
- `#ctor([NotNull] DbConnection)`
- `#ctor([NotNull] DbConnection, [NotNull] SqlServerStorageOptions)`
- `#ctor([NotNull] Func<DbConnection>)`
- `#ctor([NotNull] Func<DbConnection>, [NotNull] SqlServerStorageOptions)`
- `#ctor(string)`
- `#ctor(string, Hangfire.SqlServer.SqlServerStorageOptions)`
  - Initializes SqlServerStorage from the provided SqlServerStorageOptions and either the provided connection
string or the connection string with provided name pulled from the application config file.
  - `nameOrConnectionString`: Either a SQL Server connection string or the name of
a SQL Server connection string located in the connectionStrings node in the application config
  - `options`
- `#ctor(string, SqlServerStorageOptions)`
- `GetComponents`
- `GetConnection`
- `GetMonitoringApi`
- `GetServerRequiredProcesses`
- `GetStorageWideProcesses`
- `HasFeature(string)`
- `ToString`
- `WriteOptionsToLog(ILog)`

**Properties:**

- `QueueProviders`

**Fields:**

- `ActiveConnections`
- `ActiveTransactions`
- `DataFilesSize`
- `LinearizableReads`
- `LogFilesSize`
- `PerformanceCounterDatabaseMetric`
- `SchemaVersion`
- `TotalConnections`


#### `SqlServerStorageOptions`

**Methods:**

- `#ctor`

**Properties:**

- `CommandBatchMaxTimeout`
- `CommandTimeout`
- `CountersAggregateInterval`
- `DashboardJobListLimit`
- `DefaultQueueProvider`
  - Gets or sets a default queue provider that will be used when no special provider was
registered for a particular queue.
- `DeleteExpiredBatchSize`
  - Gets or sets the number of records deleted in a single batch in expiration manager. Default
value is 1000, but it can be configured to a higher one when processing throughput is high
enough, so expiration manager becomes the bottleneck.
- `DisableGlobalLocks`
- `DisableTransactionScope`
- `EnableHeavyMigrations`
- `ImpersonationFunc`
- `InactiveStateExpirationTimeout`
- `InvisibilityTimeout`
- `JobExpirationCheckInterval`
- `PrepareSchemaIfNecessary`
- `QueuePollInterval`
- `SchemaName`
- `SlidingInvisibilityTimeout`
- `SqlClientFactory`
  - Gets or sets the `DbProviderFactory` for creating `SqlConnection` instances.
Defaults to either `System.Data.SqlClient.SqlClientFactory.Instance` or
`Microsoft.Data.SqlClient.SqlClientFactory` depending on which package reference exists
on the consuming project.
- `TransactionIsolationLevel`
- `TransactionTimeout`
- `TryAutoDetectSchemaDependentOptions`
  - Gets or sets whether to try automatically query for the current schema on application start
and enable `UseIgnoreDupKeyOption`, `DeleteExpiredBatchSize` and
`DisableGlobalLocks` options depending on the current schema version. When storage
is inaccessible on startup, default values will be used for those options.
- `UseFineGrainedLocks`
- `UseIgnoreDupKeyOption`
  - Gets or sets whether IGNORE_DUP_KEY was applied to [Hash] and [Set] tables and so MERGE
statements can be replaced by much more efficient INSERT/UPDATE pair. This option allows
to avoid deadlocks related to SERIALIZABLE-level range locks without introducing transient
errors due to concurrency.
- `UsePageLocksOnDequeue`
- `UseRecommendedIsolationLevel`
- `UseTransactionalAcknowledge`
  - Gets or sets whether to enable experimental feature of transactional acknowledge of completed
background jobs. In this case there will be less requests sent to SQL Server and better handling
of data loss when asynchronous replication is used. But additional blocking on the JobQueue table
is expected, since transaction commit requires an explicit Commit request to be sent.


### namespace `Hangfire.SqlServer.SqlServerMonitoringApi`

#### `SafeDictionary<T1, T2>`

Overloaded dictionary that doesn't throw if given an invalid key
Fixes issues such as https://github.com/HangfireIO/Hangfire/issues/871



## package `Hangfire.AspNetCore` v1.8.23

### namespace `Hangfire`

#### `HangfireApplicationBuilderExtensions`

**Methods:**

- `RegisterHangfireServer([NotNull] this IServiceProvider, [NotNull] IBackgroundProcessingServer)`
- `UseHangfireDashboard([NotNull] this IApplicationBuilder, [NotNull] string, [CanBeNull] DashboardOptions, [CanBeNull] JobStorage)`
- `UseHangfireServer([NotNull] this IApplicationBuilder, [CanBeNull] BackgroundJobServerOptions, [CanBeNull] IEnumerable<IBackgroundProcess>, [CanBeNull] JobStorage)`
- `UseHangfireServer([NotNull] this IApplicationBuilder, [NotNull] Func<IBackgroundProcessingServer>)`


#### `HangfireEndpointRouteBuilderExtensions`

**Methods:**

- `MapHangfireDashboard([NotNull] this IEndpointRouteBuilder, [CanBeNull] DashboardOptions, [CanBeNull] JobStorage)`
- `MapHangfireDashboard([NotNull] this IEndpointRouteBuilder, [NotNull] string, [CanBeNull] DashboardOptions, [CanBeNull] JobStorage)`
- `MapHangfireDashboardWithAuthorizationPolicy([NotNull] this IEndpointRouteBuilder, [NotNull] string, [NotNull] string, [CanBeNull] DashboardOptions, [CanBeNull] JobStorage)`
- `MapHangfireDashboardWithNoAuthorizationFilters([NotNull] this IEndpointRouteBuilder, [NotNull] string, [CanBeNull] DashboardOptions, [CanBeNull] JobStorage)`


### namespace `Hangfire.Dashboard`

#### `AspNetCoreDashboardContext`

**Methods:**

- `#ctor([NotNull] JobStorage, [NotNull] DashboardOptions, [NotNull] HttpContext)`
- `GetBackgroundJobClient`
- `GetRecurringJobManager`

**Properties:**

- `HttpContext`


#### `AspNetCoreDashboardContextExtensions`

**Methods:**

- `GetHttpContext([NotNull] this DashboardContext)`


#### `AspNetCoreDashboardMiddleware`

**Methods:**

- `#ctor([NotNull] RequestDelegate, [NotNull] JobStorage, [NotNull] DashboardOptions, [NotNull] RouteCollection)`
- `#ctor([NotNull] RequestDelegate, [NotNull] JobStorage, [NotNull] DashboardOptions, [NotNull] RouteCollection, bool)`
- `Invoke(HttpContext)`



## package `Hangfire.NetCore` v1.8.23

### namespace `Hangfire`

#### `BackgroundJobServerHostedService`

**Methods:**

- `#ctor([NotNull] JobStorage, [NotNull] BackgroundJobServerOptions, [NotNull] IEnumerable<IBackgroundProcess>)`
- `#ctor([NotNull] JobStorage, [NotNull] BackgroundJobServerOptions, [NotNull] IEnumerable<IBackgroundProcess>, [CanBeNull] IBackgroundJobFactory, [CanBeNull] IBackgroundJobPerformer, [CanBeNull] IBackgroundJobStateChanger stateChanger #if NETSTANDARD2_1 ||, [CanBeNull] IHostApplicationLifetime hostApplicationLifetime)`
- `#ctor([NotNull] JobStorage, [NotNull] BackgroundJobServerOptions, [NotNull] IEnumerable<IBackgroundProcess>, [CanBeNull] IBackgroundJobFactory, [CanBeNull] IBackgroundJobPerformer, [CanBeNull] IBackgroundJobStateChanger)`
- `#ctor([NotNull] JobStorage, [NotNull] BackgroundJobServerOptions, [NotNull] IEnumerable<IBackgroundProcess>, [CanBeNull] IHostApplicationLifetime)`
- `Dispose`
- `StartAsync(CancellationToken)`
- `StopAsync(CancellationToken)`


#### `BackgroundProcessingServerHostedService`

**Methods:**

- `#ctor([NotNull] IBackgroundProcessingServer)`
- `#ctor([NotNull] IBackgroundProcessingServer, [CanBeNull] IHostApplicationLifetime)`
- `Dispose`
- `StartAsync(CancellationToken)`
- `StopAsync(CancellationToken)`


#### `HangfireServiceCollectionExtensions`

**Methods:**

- `AddHangfire([NotNull] this IServiceCollection, [NotNull] Action<IGlobalConfiguration>)`
- `AddHangfire([NotNull] this IServiceCollection, [NotNull] Action<IServiceProvider, IGlobalConfiguration>)`
- `AddHangfireServer([NotNull] this IServiceCollection)`
- `AddHangfireServer([NotNull] this IServiceCollection, [NotNull] Action<BackgroundJobServerOptions>)`
- `AddHangfireServer([NotNull] this IServiceCollection, [NotNull] Action<IServiceProvider, BackgroundJobServerOptions>)`
- `AddHangfireServer([NotNull] this IServiceCollection, [NotNull] Action<IServiceProvider, BackgroundJobServerOptions>, [NotNull] JobStorage)`
- `AddHangfireServer([NotNull] this IServiceCollection, [NotNull] Action<IServiceProvider, BackgroundJobServerOptions>, [NotNull] JobStorage, [NotNull] IEnumerable<IBackgroundProcess>)`
- `AddHangfireServer([NotNull] this IServiceCollection, [NotNull] Func<IServiceProvider, IBackgroundProcessingServer>)`
- `AddHangfireServer([NotNull] this IServiceCollection, [NotNull] JobStorage)`
- `AddHangfireServer([NotNull] this IServiceCollection, [NotNull] JobStorage, [NotNull] IEnumerable<IBackgroundProcess>)`
- `GetInternalServices(IServiceProvider, IBackgroundJobFactory, IBackgroundJobStateChanger, IBackgroundJobPerformer)`
- `ThrowIfNotConfigured(IServiceProvider)`


#### `IBackgroundJobClientFactory`


#### `IBackgroundJobClientFactoryV2`


#### `IRecurringJobManagerFactory`


#### `IRecurringJobManagerFactoryV2`


### namespace `Hangfire.AspNetCore`

#### `AspNetCoreJobActivator`

**Methods:**

- `#ctor([NotNull] IServiceScopeFactory)`
- `BeginScope`
- `BeginScope(JobActivatorContext)`


#### `AspNetCoreLogProvider`

**Methods:**

- `#ctor([NotNull] ILoggerFactory)`
- `GetLogger(string)`
