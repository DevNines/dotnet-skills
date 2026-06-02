# Hangfire.Core — release notes by major

_Generated from `https://github.com/HangfireIO/Hangfire/releases`. Use when answering migration questions or when a user asks what changed between versions._

## v1.x

### 1.8.23  (v1.8.23)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.8.23>

### Release Notes

#### Hangfire.Core

* **Changed** – Use stable sorting algorithm for background job filters again (by @jirikanda).
* **Fixed** – Custom `AutomaticRetryAttribute` is ignored under certain conditions regression from 1.8.14 (by @jirikanda).
* **Fixed** – Add missing keys for Swedish translation (by @karl-sjogren).
* **Project** – Use `TypeNameAssemblyFormatHandling` in tests with .NET 6 (by @viktor-vintertass).

#### Hangfire.AspNetCore

* **Fixed** – `InvalidOperationException`: The request reached the end of the pipeline without executing the endpoint.

### 1.8.22  (v1.8.22)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.8.22>

### Release Notes

#### Hangfire.Core

* **Added** – `IGlobalConfiguration.UseNoOpLogProvider` method to disable logging.
* **Changed** – Un-deprecate interval methods in the `Cron` class, add remarks in docs instead.
* **Changed** – Bump internalized version of Cronos to 0.11.1.
* **Changed** – Bump internalized version of Microsoft.Owin to 4.2.3.
* **Fixed** – Serialization of arrays of nested types `SimpleAssemblyTypeSerializer`.
* **Fixed** – Remove wrong escaping characters in Portuguese translations on the "Servers" page.
* **Fixed** – Properly remove registered `IBackgroundProcessingServer` instances on OWIN app shutdown.
* **Fixed** – `AspNetShutdownDetector` for early ASP.NET shutdown detection is not working (regression from 1.7.30).
* **Project** – Replace the `netcoreapp3.1` target with the `net8.0` one in tests.

#### Hangfire.SqlServer

* **Fixed** – `InvalidCastException` when creating a background job with Schema 5 (regression from 1.8.15).
* **Project** – Replace the `netcoreapp3.1` target with the `net8.0` one in tests.

#### Hangfire.AspNetCore

* **Added** – `MapHangfireDashboardWithNoAuthorizationFilters` method, which does not include local-only filters.
* **Changed** – Set 404 status code when `MapHangfireDashboard` is used and no dispatcher is found.
* **Fixed** – `InvalidOperationException` upon receiving a request for 'hangfire/bootstrap.min.css.map'.

### 1.8.21  (v1.8.21)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.8.21>

### Release Notes

#### Hangfire.Core

* **Added** – `FailedState.IncludeFileInfo` to optionally show/hide line numbers in exceptions in Failed state.
* **Changed** – Include line numbers for exceptions by default when available.
* **Fixed** – Portuguese (Brazil) translations in Strings.pt-BR.resx (by @pedro-cons).
* **Fixed** – Static `BackgroundJob` class always acquires the most current `JobStorage.Current` instance.
* **Fixed** – Static `RecurringJob` class always acquires the most current `JobStorage.Current` instance.

#### Hangfire.SqlServer

* **Added** – `SqlServerStorageOptions.DisableTransactionScope` option for .NET Framework targets.
* **Project** – Port Monitoring API tests from the Hangfire.InMemory storage for better coverage.
* **Project** – Run tests for different targets in parallel with different databases.

### 1.8.20  (v1.8.20)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.8.20>

### Release Notes

#### Hangfire.Core

* **Fixed** – Glyphicons from Bootstrap are not displaying after upgrading to version 1.8.19.

### 1.8.19  (v1.8.19)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.8.19>

### Release Notes

#### Hangfire.Core

* **Changed** – Update Bootstrap to the custom version of 3.4.2 to avoid false alerts on unused features.
* **Fixed** – Typos in Portuguese translation (by @VianaArthur).
* **Fixed** – Unnecessary recurring job update transaction when nothing is changed after an error.

#### Hangfire.SqlServer

* **Fixed** – Sliding invisibility timeout isn't prolonged in lightweight servers, causing jobs to be restarted.

### 1.8.18  (v1.8.18)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.8.18>

### Release Notes

#### Hangfire.Core

* **Added** – `DashboardOptions.ServerPossiblyAbortedThreshold` to configure a custom threshold for "possibly aborted" warnings.
* **Fixed** – Expired jobs are still shown on the "Retries" page in some cases.
* **Fixed** – Issues with `CultureInfo`-related differences after upgrading to 1.8.15–1.8.17.
* **Fixed** – Don't leak `AsyncLocal` values from synchronous background job methods.
* **Fixed** – Don't throw an exception when passing the `Job.Args` property to the `Job` class' constructor.
* **Project** – Make the lock file usable for both .NET 8.0 and .NET 9.0 builds.
* **Project** – Make code generation for `cshtml` files working on newer platforms.

#### Hangfire.AspNetCore

* **Fixed** – Swallow possible `ObjectDisposedException` in the `StopAsync` method.
* **Fixed** – Avoid `NullReferenceException` when `LocalIpAddress` or `RemoteIpAddress` is null.

### 1.8.17  (v1.8.17)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.8.17>

### Release Notes

#### Hangfire.SqlServer

* **Fixed** – `InvalidCastException` while fetching a job with older schemas regression from 1.8.16.

### 1.8.16  (v1.8.16)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.8.16>

### Release Notes

#### Hangfire.Core

* **Changed** – Include fewer stack frames in exceptions come from `IServerFilter` implementations.
* **Changed** – Don't include file information in the `ExceptionDetails` property of a FailedState instance.
* **Changed** – Switch back to `CancellationEvent` usage instead of `CancellationToken.WaitHandle`.
* **Fixed** – Don't commit external transaction in the `BackgroundJobStateChanger` implementation.
* **Fixed** – Use safe default serializer settings for Newtonsoft.Json 12.X and below.
* **Project** – Fix builds for the `net451` platform when using .NET 9.0.
* **Project** – Significantly reduce execution time of unit tests in the `RecurringJobSchedulerFacts` class.
* **Project** – Bump `Microsoft.CodeAnalysis.NetAnalyzers` package to version 9.0.0.

#### Hangfire.SqlServer

* **Changed** – Use vanilla ADO.NET when fetching a job in the `SqlServerJobQueue` implementation.
* **Changed** – Decrease the `LockTimeout` time when calling the `sp_getapplock` procedure to 1 second for less blocking.
* **Fixed** – SqlException: Must declare the scalar variable "key" in delayed and recurring job schedulers.
* **Project** – Disable parallel tests execution when building under .NET 9.0.
* **Project** – Run tests over the latest Microsoft.Data.SqlClient package and the `net6.0` platform.
* **Project** – Reduce execution time of integration tests.
* **Project** – Disable `PoolBlockingPeriod` setting on AppVeyor to handle transient test failures.

### 1.8.15  (v1.8.15)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.8.15>

### Release Notes

#### Hangfire.Core

* **Added** – New `AutomaticRetryAttribute.ExceptOn` property to skip retries for specific exceptions.
* **Changed** – Refactor filters pipeline to use less LINQ magic and fewer allocations.
* **Changed** – Use `GetCultureInfo` instead of creating an instance in the `CaptureCultureAttribute` filter.
* **Changed** – Cache some immutable data to avoid extra allocations.
* **Fixed** – Improve loopback address detection (by @meziantou).
* **Fixed** – Reformulate misleading error messages regarding retry timings (by @RGFuaWVs).
* **Fixed** – Problem with missing localizations in the previous version.
* **Fixed** – Don't hide exception details on Failed Jobs page when the exception message is empty.
* **Fixed** – Problems with the first restore when using the `build.bat` command.
* **Fixed** – Better display of canceled recurring jobs in dashboard.
* **Fixed** – Less overall allocations with using static delegates and struct-based iterators.
* **Fixed** – Improve precision of some diagnostic messages in the wait protection logic.
* **Fixed** – Make all private and internal classes sealed to improve code consistency.
* **Fixed** – Less overall pressure on garbage collector.

#### Hangfire.SqlServer

* **Changed** – Use query template caching based on schema name to avoid excessive `string` allocations.
* **Changed** – Use static callbacks almost anywhere to avoid unnecessary delegate allocations.
* **Changed** – Use `QuerySingle`* or `ReadSingle`* where possible to avoid allocating lists.
* **Changed** – Unify `DbCommand` and `DbParameter` creation logic to improve code consistency.

### 1.8.13 & 1.8.14  (v1.8.14)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.8.14>

### Release Notes

#### Hangfire.Core

* **Changed** – Partial cache for serialization and deserialization in `InvocationData` to produce less strings.
* **Changed** – Add caching for default type serializer and resolver.
* **Changed** – Don't let `JobFilter`-related logic to show up in profilers.
* **Changed** – Modify `IProfiler` to be less allocatey for diagnostic purposes that almost never run.
* **Changed** – Prefer using `CancellationToken.WaitHandle` again, since early .NET Core days are gone.
* **Changed** – Fewer allocations when working with `IStateHandler` collections in a state machine.
* **Fixed** – Redirect the "System.Private.Xml.Linq" assembly to the "System.Xml.Linq" one for better interoperability.
* **Fixed** – Don't throw `KeyNotFoundException` when recurring job is malformed.
* **Fixed** – Proper relative path calculation in `UrlHelper.To` for OWIN-based Dashboard UI (by @LordJZ).
* **Fixed** – Typo in the Turkish localization file (by @ismkdc).
* **Project** – Switch to a modern PowerShell 7+ to speed up SignPath installation on AppVeyor.

#### Hangfire.SqlServer

* **Changed** – Limit polling queries when queues are empty with a semaphore for all configurations.
* **Changed** – Use per-queue signaling for same-process workers, instead of having a global signal.
* **Fixed** – Don't silently truncate queue names, throw an exception instead.
* **Project** – Decrease delays in SQL Server-related tests to complete them faster.

### 1.8.12  (v1.8.12)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.8.12>

### Release Notes

#### Hangfire.Core

* **Added** – `MaxDegreeOfParallelismForSchedulers` experimental server option if supported by storage.
* **Added** – Experimental support for parallel execution of the delayed job scheduler.
* **Added** – Experimental support for parallel execution of the recurring job scheduler.
* **Fixed** – Recurring job is scheduled to the past after recovering from error with `AddOrUpdate`.
* **Fixed** – `AddOrUpdate` triggers execution of a recurring job, even if its next execution is in the future.
* **Fixed** – Two very minor errors in the Swedish localization file (by @Uglack).

#### Hangfire.SqlServer

* **Fixed** – Populate `InvocationData` and `LoadException` properties in `JobDetails` method results.

### 1.8.11  (v1.8.11)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.8.11>

### Release Notes

#### Hangfire.Core

* **Changed** – Add icons and fix metadata for NuGet packages.
* **Changed** – Bump ILRepack to version 2.0.27 to avoid problems with internalizing.
* **Fixed** – "Type exists in both Cronos and Hangfire.Core" exception.

### 1.8.10  (v1.8.10)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.8.10>

### Release Notes

#### Hangfire.Core

* **Changed** – Added Norwegian translations for new keys (by @khellang).
* **Changed** – Update Brazilian Portuguese translation (by @HugoAlames).
* **Changed** – Bump Cronos dependency to version 0.8.3.

#### Hangfire.AspNetCore

* **Fixed** – Don't check `HasStarted` in `Response.WriteAsync` to avoid breaking dispatchers.

#### Hangfire.SqlServer

* **Changed** – Bump Dapper for the `netstandard2.0` platform to version 2.1.28.
* **Changed** – Bump Dapper for `net451` and `netstandard1.3` platforms to version 1.60.6.

#### Hangfire.Core, Hangfire.NetCore, Hangfire.AspNetCore, Hangfire.SqlServer, Hangfire.SqlServer.Msmq

* **Project** – Enable NuGet package and DLL signing with a company certificate.
* **Project** – Require NuGet package signature validation on restore for dependencies.
* **Project** – Add `HangfireIO` as a package owner.

### 1.8.9  (v1.8.9)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.8.9>

### Release Notes

Please note that version 1.8.8 was unlisted on NuGet because of broken package references.

#### Hangfire.Core

* **Changed** – Use `Environment.MachineName` as a server name if other environment vars aren't available.
* **Changed** – Bump the Cronos package version from 0.7.1 to 0.8.1.
* **Changed** – Improve portuguese translations (by @filipe-silva).
* **Fixed** – Possible `NullReferenceException` on the Deleted Jobs page (regression from 1.8.7).
* **Project** – Enable full source link support with embedded symbols and repository-based sources.
* **Project** – Enable repeatable package restore using a lock file.
* **Project** – Run unit tests against the `net6.0` platform.
* **Project** – Modernise the build system and clean up the build scripts.

#### Hangfire.SqlServer

* **Project** – Enable full source link support with embedded symbols and repository-based sources.
* **Project** – Enable repeatable package restore using a lock file.
* **Project** – Run unit tests against the `net6.0` platform.

#### Hangfire.NetCore

* **Project** – Enable full source link support with embedded symbols and repository-based sources.
* **Project** – Enable repeatable package restore using a lock file.

#### Hangfire.AspNetCore

* **Fixed** – Don't attempt to write response headers when response has already started (by @maliming).
* **Project** – Enable full source link support with embedded symbols and repository-based sources.
* **Project** – Enable repeatable package restore using a lock file.

### 1.8.7  (v1.8.7)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.8.7>

### Release Notes

#### Hangfire.Core

* **Added** – Allow using macro expressions like `@hourly` for recurring jobs (by @MuhamedAbdalla).
* **Added** – Show storage time in page footer when supported by storage implementation.
* **Added** – Show duration and latency columns separately on the Succeeded Jobs page when supported.
* **Added** – Show the exception column on the Deleted Jobs page when available and supported by storage.
* **Changed** – Reduce package size by stripping unnecessary locales in Moment.js.
* **Changed** – Bump Microsoft.Owin package to version 4.2.2.
* **Changed** – Log a warning message when a server listens to unsupported queue names (by @MuhamedAbdalla).
* **Changed** – Use storage time, if available, to show delay warnings in the Dashboard UI.
* **Fixed** – Proper rendering of generic arguments on the Job Details page (by @olivermue).
* **Fixed** – Language inconsistency in the Dashboard UI related to date/time description.
* **Fixed** – Big stack traces take too long time to be formatted.
* **Fixed** – Don't throw `NullReferenceException` from the Scheduled Jobs page when there's a job with missing data.
* **Fixed** – Don't throw `NullReferenceException` from the Processing Jobs page when there's a job with missing data.
* **Fixed** – CSS for Enqueued and Deleted state cards in dark theme.
* **Fixed** – Log errors instead of throwing an exception when a particular table can't be cleaned.
* **Fixed** – Avoid logging fatal exceptions when stopping a faulting background process.
* **Fixed** – Don't display checkboxes in the Dashboard UI when job details can not be fetched.
* **Fixed** – Scrollbars in WebKit-based browsers are now dark in dark mode.
* **Project** – Disable tests for `netcoreapp1.0` and `netcoreapp2.1` targets since they aren't supported in AppVeyor.
* **Project** – Add a `net6.0` target for unit tests instead of the removed ones.
* **Project** – Modernise projects and build environments to use the newest features.

#### Hangfire.SqlServer

* **Changed** – Avoid throwing an exception when a connection string has duplicate property names.
* **Project** – Disable tests for `netcoreapp1.0` and `netcoreapp2.1` targets since they aren't supported in AppVeyor.
* **Project** – Add a `net6.0` target for unit tests instead of the removed ones.
* **Project** – Modernise projects and build environments to use the newest features.

### 1.8.6  (v1.8.6)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.8.6>

### Release Notes

#### Hangfire.Core

* **Changed** – Update jQuery library in Dashboard UI to version 3.7.1.
* **Changed** – Mark all types in Hangfire.Annotations with `EditorBrowsableAttribute(Never)`.
* **Changed** – Change state card colors for the Awaiting state to match the Scheduled state.
* **Fixed** – Exception when deserializing an instance of the `AutomaticRetryAttribute` class from JSON.
* **Fixed** – Add serialization-related constructors for all the exception classes.
* **Fixed** – Use invariant culture or ordinal comparisons for internal strings.
* **Fixed** – Use invariant culture when formatting key names for metrics.
* **Fixed** – Use `CurrentCulture` instead of `CurrentUICulture` when displaying time.
* **Project** – Enable running static analysis by Coverity Scan weekly.
* **Project** – Enable mandatory static analysis by the Microsoft.CodeAnalysis.NetAnalyzers package.
* **Project** – Change MSBuild path when building using newer .NET SDKs for Razor views.
        
#### Hangfire.SqlServer

* **Fixed** – Exception in Dashboard UI when schema version is not present in a database.
* **Fixed** – `DbCommand` resource leak when releasing a lock detected by static analysis.
* **Fixed** – Don't add SQL Server-related metrics multiple times in Dashboard UI.

#### Hangfire.NetCore

* **Fixed** – Include assembly information to the Hangfire.NetCore assembly.

### 1.8.5  (v1.8.5)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.8.5>

### Release Notes

#### Hangfire.Core

* **Added** – Possibility to inform a `FaviconPath` on `DashboardOptions` (by @cezar-pimentel).
* **Fixed** – Inability to restore a disabled recurring job, regression in version 1.8.3.
* **Fixed** – Make it possible to serialize the `AutomaticRetryAttribute` filter to JSON.

#### Hangfire.SqlServer

* **Fixed** – "Query processor could not produce a query plan" when removing expired counters in `Schema 5`.

### 1.8.4  (v1.8.4)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.8.4>

### Release Notes

#### Hangfire.Core

* **Added** – Pass server id from a worker to the `PerformContext.ServerId` property available in filters.
* **Fixed** – Send heartbeats until full background processing server shutdown.
      
#### Hangfire.NetCore

* **Changed** – Send the stop signal earlier in the shutdown pipeline when hosting in .NET Core 3.1 or higher.
* **Changed** – Set processing server to null in hosted service to avoid `ObjectDisposedException`.
* **Fixed** – Other `IHostedService` implementations can block Hangfire server from being stopped.

### 1.8.3  (v1.8.3)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.8.3>

### Release Notes

**Hangfire.Core**

* **Changed** – Allow to configure `MaxLinesInStackTrace` for a particular `FailedState` instance.
* **Fixed** – Remove job id from schedule when it's not in the Scheduled state for some reason.
* **Fixed** – Missing invocations of recurring jobs when the new "Ignorable" option is used.
* **Fixed** – Make `DisableConcurrentExecutionAttribute` and `LatencyTimeoutAttribute` serializable.

### 1.8.2  (v1.8.2)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.8.2>

### Release Notes

**Hangfire.Core**

* **Changed** – Disable transactional job creation feature appeared in 1.8.0.
* **Fixed** – "Can not start continuation XXX" error when storage supports transactional job creation.

**Hangfire.SqlServer**

* **Fixed** – `InvalidOperationException` with new dashboard metrics when a database has multiple data/log files.

### 1.8.1  (v1.8.1)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.8.1>

### Release Notes

**Hangfire.Core**

* **Added** – `MisfireHandlingMode.Ignorable` to avoid scheduling recurring jobs on missed schedules.
* **Added** – Support disabling dark mode via the `DashboardOptions.DarkModeEnabled` property.
* **Changed** – Remove the 1-hour limitation for the `WithJobExpirationTimeout` configuration method.
* **Fixed** – Add missing `UseDefaultCulture` configuration method overloads.
* **Fixed** – Add missing `UseDashboardStylesheet` and `UseJobDetailsRenderer` configuration methods.
* **Fixed** – Give even more space for identifiers on the Recurring Jobs page.
* **Fixed** – `state-card-state-active` color is not very dark (by @coolhome).
* **Fixed** – Slightly change chart proportions to fit 4K in Dashboard UI.

**Hangfire.SqlServer**

* **Fixed** – Blocked workers regression since 1.7.28 when using multiple servers inside a process.
* **Fixed** – Target schema version is less than the current schema version error.
* **Fixed** – Implement database metrics without the need for additional permissions.
* **Fixed** – Use the `forceseek` table hint whenever possible to avoid performance drops.
      
**Hangfire.NetCore**

* **Fixed** – Add `net461` target for Hangfire.NetCore package to avoid missing method exceptions.

### 1.8.0  (v1.8.0)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.8.0>

### Release Notes

Please see more human-friendly release notes in our blog https://www.hangfire.io/blog/2023/04/28/hangfire-1.8.0.html. Please see https://docs.hangfire.io/en/latest/upgrade-guides/upgrading-to-hangfire-1.8.html to learn how to upgrade.

**Hangfire.Core**

* **Breaking** – Dropped the `NET45` platform target in favor of the `NET451` target to support Visual Studio 2022.
* **Added** – Introduce the `Job.Queue` property, so jobs now can have their own queue specified.
* **Added** – Method overloads to create background jobs directly with a custom default queue.
* **Added** – Method overloads to create recurring jobs directly with a custom default queue.
* **Added** – `IBackgroundJobClient.Create` method overloads with the new `queue` parameter.
* **Added** – Allow to filter exception types in `AutomaticRetryAttribute` by using the new `OnlyOn` property.
* **Added** – `DeletedState` now has the persisted `Exception` property populated after a failure.
* **Added** – `JobContinuationOptions.OnlyOnDeletedState` to create continuations after a failure.
* **Added** – `Exception` job parameter is passed to continuation when `UseResultsInContinuations` method is used.
* **Added** – `FromExceptionAttribute` to deal with an antecedent exception in a background job continuation.
* **Added** – Make it possible to specify multiple `JobContinuationOptions` values for a continuation.
* **Added** – `BackgroundJobServerOptions.IsLightweightServer` option to run a server with no storage processes.
* **Added** – Ability to use custom formattable resource identifiers for the `DisableConcurrentExecution` filter.
* **Added** – Pass `ServerId` to `FailedState` instances to simplify the debugging on different servers.
* **Added** – Allow to pass job parameters when creating a job (by @brian-knoll-micronetonline).
* **Added** – `MisfireHandlingMode.Strict` to create a job for each missed recurring job occurrence.
* **Added** – Support for default culture and UI culture via the `UseDefaultCulture` configuration method.
* **Added** – Introduce the `captureDefault` parameter in the `CaptureCulture` filter.
* **Added** – `IGlobalConfiguration.UseFilterProvider` extension method to unify the configuration.
* **Added** – Built-in `Remove` method for `JobFilterCollection` to remove global filters based on their type.
* **Added** – `CompatibilityLevel.Version_180` flag to avoid storing culture parameters when they are the same as the default ones.
* **Changed** – Create job atomically when `Transaction.CreateJob` feature is supported by the storage.
* **Changed** – Query time from storage in recurring and delayed schedulers when supported by storage.
* **Changed** – Move job to the `DeletedState` instead of `SucceededState` when its invocation was canceled by a filter.
* **Changed** – Speedup delayed jobs when a custom default queue is specified by avoiding extra state transition.
* **Changed** – Use UI culture from `CurrentCulture` parameter when `CurrentUICulture` one is missing.
* **Changed** – Increase the default value for the `BackgroundJobServerOptions.StopTimeout` to 500 ms.
* **Deprecated** – `AddOrUpdate` overloads with optional params defined in the `RecurringJobManagerExtensions` class.
* **Deprecated** – `AddOrUpdate` overloads with optional parameters defined in the `RecurringJob` class.
* **Deprecated** – `AddOrUpdate` method overloads with no `recurringJobId` parameter.
* **Deprecated** – `RecurringJobOptions.QueueName` property, new methods should be used instead.
* **Breaking** – Dropped `NET45` platform target in favor of `NET451` target to support Visual Studio 2022.

*Dashboard UI*
* **Added** – Dark mode support for Dashboard UI depending on the system settings (by @danillewin).
* **Added** – Dashboard UI now has a full-width layout to display more data (by @danillewin).
* **Added** – Allow to add custom JavaScript and CSS files to the Dashboard UI via the `DashboardRoutes` class.
* **Added** – `DefaultRecordsPerPage` property on the `DashboardOptions` class (by @PaulARoy).
* **Added** – `IGlobalConfiguration.UseJobDetailsRenderer` method for custom renderers for the Job Details page.
* **Added** – Display deleted jobs in the Realtime and History graphs when supported by storage.
* **Added** – `IGlobalConfiguration.UseDashboardMetrics` extension method to pass multiple metrics at once.
* **Added** – State renderer for the `DeletedState` to display its new exception property.
* **Added** – Support for new `MonitoringApi` methods for the Awaiting Jobs page.
* **Changed** – Make it possible to display methods of non-loaded jobs in the Dashboard UI when supported by storage.
* **Changed** – Improved display of realtime chart with more accents on failed and deleted jobs.
* **Changed** – Don't display the queue name in the state transition list when it's the `default` one.
* **Changed** – Display scheduled job count when the enqueued count is zero on the main metric.

*Extensibility*
* **Added** – `Factory`, `StateMachine`, and `Performer` properties to context classes to avoid injecting services.
* **Added** – Allow to pass custom data to `ApplyStateContext` and `ElectStateContext` instances.
* **Added** – Preserve custom data dictionary between the entire filter chain.
* **Added** – Allow to pass a transaction to background job state changer when new methods are implemented.
* **Changed** – Ignore some members when serializing a `JobFilterAttribute` instance to decrease the payload size.

*Storage*
* **Added** – Virtual `JobStorage.GetReadOnlyConnection` method intended to return `JobStorageConnection` for replicas.
* **Added** – Virtual `JobStorage.HasFeature` method for querying optional features.
* **Added** – The `JobStorageFeatures` class to avoid using magic strings in storage features.
* **Added** – Optional `GetSetCount`, `GetSetContains`, and `GetUtcDateTime` methods for the `JobStorageConnection` class.
* **Added

_…truncated…_

### 1.8.0-rc4  (v1.8.0-rc4)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.8.0-rc4>

### Release Notes

**Hangfire.Core**

* **Added** – `DefaultRecordsPerPage` property on the `DashboardOptions` class (by @PaulARoy).

**Hangfire.NetCore**

* **Changed** – Send the "stop" signal earlier when host supports .NET Standard 2.1.
* **Changed** – Don't throw `ObjectDisposedException` when hosted service disposed twice.

**Hangfire.SqlServer**

* **Added** – `Schema 9` migration that creates index for the `State.CreatedAt` column.
* **Added** – Clean up of old state entries of a non-finished job when `InactiveStateExpirationTimeout` is set.
* **Added** – `DefaultQueueProvider` option to specify a custom default queue provider.
* **Changed** – Enable common metrics for SQL Server storage to be shown by default.

### 1.8.0-rc3  (v1.8.0-rc3)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.8.0-rc3>

### Release Notes

Please see release notes in our blog – https://www.hangfire.io/blog/2023/03/30/hangfire-1.8.0-rc3.html.

#### Hangfire.Core

* **Added** – Introduce the `captureDefault` parameter in the `CaptureCulture` filter.
* **Added** – Built-in awaiting metric through the `StatisticsDto.Awaiting` for monitoring stats.
* **Added** – `JobStorageFeatures` class to avoid using magic strings in storage features.
* **Added** – Create job atomically when corresponding storage feature supported.
* **Added** – Support for new MonitoringApi methods for the Awaiting Jobs page.
* **Changed** – Rely on `captureDefault` when dealing with default cultures instead of compatibility level.
* **Changed** – Rename in a non-breaking way `SetContains` to `GetSetContains` for consistency.
* **Changed** – Rely on storage indexing with `Monitoring.AwaitingJobs` feature.
* **Changed** – Rename the `BatchedGetFirstByLowest` feature.
* **Changed** – Throw more descriptive `NotSupportedException` from new storage methods
* **Changed** – Make new methods in `JobStorageMonitor` virtual, not abstract.
* **Changed** – Change GetSetCount with multiple keys in a non-breaking way.
* **Fixed** – Throw an exception early when `Job.Queue` feature not supported.
* **Fixed** – Don't show assembly details in deleted state renderer.
* **Rollback** – Use the `AttemptsExceededAction.Delete` option by default in the global automatic retry filter.

#### Hangfire.SqlServer

* **Changed** – Enable the `Monitoring.AwaitingJobs` feature for SQL storage.
* **Changed** – Implement the `Transaction.AcquireDistributedLock` feature.
* **Changed** – Implement the `GetSetCount.Limited feature`.
* **Changed** – Implement the `GetSetContains feature`.
* **Fixed** – Detect schema-related options after migration, not before, to get the actual schema version.

### 1.8.0-rc2  (v1.8.0-rc2)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.8.0-rc2>

### Release Notes

#### Hangfire.Core

* **Added** – Support for default culture and UI culture via the `UseDefaultCulture` configuration method.
* **Added** – `CompatibilityLevel.Version_180` flag to avoid storing culture parameters when they are the same as default.
* **Added** – `BackgroundJobServerOptions.IsLightweightServer` option to run server with no storage processes.
* **Changed** – Use UI culture from `CurrentCulture` parameter when `CurrentUICulture` one is missing.

#### Hangfire.SqlServer

* **Breaking** – Prioritise Microsoft.Data.SqlClient package over System.Data.SqlClient one.
* **Changed** – Bump internal version of Dapper to 2.0.123.
* **Changed** – Remove System.Data.SqlClient package from the NuGet dependency graph (by @0xced).

#### Hangfire.NetCore

* **Added** – `net451` and `netstandard1.3` targets for the package.
* **Changed** – Use `netstandard2.1` target instead of `netcoreapp3.0` for the package.

#### Hangfire.AspNetCore

* **Breaking** – Make the package to be dependent on Hangfire.NetCore to use the same types.

### 1.8.0-rc1  (v1.8.0-rc1)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.8.0-rc1>

### Release Notes

#### Hangfire.Core

* **Added** – Introduce the `Job.Queue` property, so jobs now can have their own queue specified.
* **Added** – Method overloads to create background jobs directly with a custom default queue.
* **Added** – Method overloads to create recurring jobs directly with a custom default queue.
* **Added** – `IBackgroundJobClient.Create` method overloads with the new `queue` parameter.
* **Added** – `JobContinuationOptions.OnlyOnDeletedState` to create continuations after a failure.
* **Added** – Make it possible to specify multiple `JobContinuationOptions` values for a continuation.
* **Added** – Ability to use custom formattable resource identifiers for the `DisableConcurrentExecution` filter.
* **Added** – Pass `ServerId` to `FailedState` instances to simplify the debugging on different servers.
* **Added** – Allow to pass job parameters when creating a job (by @brian-knoll-micronetonline).
* **Added** – `MisfireHandlingMode.Strict` to create job for each missed recurring job occurrence.
* **Added** – `DeletedState` now have the persisted `Exception` property populated after a failure.
* **Added** – `Exception` job parameter is passed to continuation when `UseResultsInContinuations` method is used.
* **Added** – `FromExceptionAttribute` to deal with an antecedent exception in a background job continuation.
* **Added** – Allow to filter exception types in `AutomaticRetryAttribute` by using the new `OnlyOn` property.
* **Added** – Built-in `Remove` method for `JobFilterCollection` to remove global filters based on their type.
* **Added** – `IGlobalConfiguration.UseFilterProvider` extension method to unify the configuration.
* **Changed** – Use the `AttemptsExceededAction.Delete` option by default in the global automatic retry filter.
* **Changed** – Query time from storage in recurring and delayed schedulers when supported by storage.
* **Changed** – Increase the default value for the `BackgroundJobServerOptions.StopTimeout` to 500 ms.
* **Changed** – Speedup delayed jobs when custom default queue is specified by avoiding extra state transition.
* **Changed** – Move job to the `DeletedState` instead of `SucceededState` when its invocation was canceled by a filter.
* **Deprecated** – `AddOrUpdate` overloads with optional params defined in the `RecurringJobManagerExtensions` class.
* **Deprecated** – `AddOrUpdate` overloads with optional parameters defined in the `RecurringJob` class.
* **Deprecated** – `AddOrUpdate` method overloads with no `recurringJobId` parameter.
* **Deprecated** – `RecurringJobOptions.QueueName` property, new methods should be used instead.
* **Breaking** – Dropped `NET45` platform target in favor of `NET451` target to support Visual Studio 2022.

*Dashboard UI*

* **Added** – Dark mode support for Dashboard UI configurable with the `UseDarkModeSupportForDashboard` method (by @danillewin).
* **Added** – Dashboard UI now have full-width layout to display more data (by @danillewin).
* **Added** – Allow to add custom JavaScript and CSS files to the Dashboard UI via the `DashboardRoutes` class.
* **Added** – `IGlobalConfiguration.UseJobDetailsRenderer` method for custom renderers for Job Details page.
* **Added** – Display deleted jobs in the Realtime and History graphs when supported by storage.
* **Added** – `IGlobalConfiguration.UseDashboardMetrics` extension method to pass multiple metrics at once.
* **Added** – State renderer for the `DeletedState` to display its new exception property.
* **Changed** – Make it possible to display methods of non-loaded jobs in Dashboard UI when supported by storage.
* **Changed** – Improved display of real-time chart with more accents on failed and deleted jobs.
* **Changed** – Don't display queue name in state transition list when it's the `default` one.
* **Changed** – Display scheduled job count when enqueued count is zero on the main metric.

*Extensibility*

* **Added** – `Factory`, `StateMachine` and `Performer` properties to context classes to avoid injecting services.
* **Added** – Allow to pass custom data to `ApplyStateContext` and `ElectStateContext` instances.
* **Added** – Preserve custom data dictionary between the entire filter chain.
* **Added** – Allow to pass transaction to background job state changer when new methods implemented.
* **Changed** – Ignore some members when serializing a `JobFilterAttribute` instance to decrease payload size.

*Storage*

* **Added** – Virtual `JobStorage.GetReadOnlyConnection` method intended to return `JobStorageConnection` for replicas.
* **Added** – Virtual `JobStorage.HasFeature` method for querying optional features.
* **Added** – Optional `GetSetCount` and `GetUtcDateTime` methods for the `JobStorageConnection` class.
* **Added** – Optional `AcquireDistributedLock` and `RemoveFromQueue` methods for the `JobStorageTransaction` class.
* **Added** – Support for transactional acknowledge using new storage method for better handling some data loss scenarios.
* **Added** – `CreateJob` method to the `JobStorageTransaction` abstract class.
* **Added** – `SetJobParameter` method to the `JobStorageTransaction` abstract class.
* **Added** – Experimental `JobStorageConnection.SetContains` method.
* **Added** – Optional `ParametersSnapshot` property for `BackgroundJob` and `JobData` classes to minimize roundtrips in future.
* **Added** – Fetch "Retries" metric with other statistics when supported by storage.
* **Added** – `JobStorageMonitor` class with more available methods for the new features.
* **Changed** – Allow to query job parameters without additional roundtrip when supported by a storage.
* **Changed** – Expose state data dictionaries in list DTOs when supported by storage.

*Internals*

* **Added** – `IBackgroundProcess.UseBackgroundPool` now allows to pass thread configuration logic.
* **Added** – `BackgroundJobServerOptions.WorkerThreadConfigurationAction` option for custom th

_…truncated…_

### 1.8.0-beta4  (v1.8.0-beta4)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.8.0-beta4>

### Release Notes

#### Hangfire.Core

* **Added** – Dark mode support for Dashboard UI configurable with the `UseDarkModeSupportForDashboard` method.
* **Added** – Allow to add custom JavaScript and CSS files to the Dashboard UI via the `DashboardRoutes` class.
* **Added** – Ability to use custom formattable resource identifiers for the `DisableConcurrentExecutionAttribute`.
* **Changed** – Increase the default value for the `BackgroundJobServerOptions.StopTimeout` to 500 ms.
      
#### Hangfire.SqlServer

* **Added** – `TryAutoDetectSchemaDependentOptions` option to automatically enable options based on schema.
* **Changed** – `GetJobData` now populates `JobData.ParametersSnapshot` property to avoid additional round-trips.
* **Changed** – Polling delay when `QueuePollInterval` is set to zero now defaults to 200 ms.
* **Deprecated** – `UsePageLocksOnDequeue` option is now obsolete and doesn't affect anything.

### 1.8.0-beta3  (v1.8.0-beta3)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.8.0-beta3>

### Release Notes

**Hangfire.Core**

* **Added** – Introduce the `Job.Queue` property, so jobs now can have their own queue specified.
* **Added** – Method overloads to create recurring jobs directly with a custom default queue.
* **Added** – Method overloads to create background jobs directly with a custom default queue.
* **Added** – `IBackgroundJobClient.Create` method overloads with the new `queue` parameter.
* **Added** – Experimental `JobStorageConnection.SetContains` method.
* **Added** – Pass `ServerId` to `FailedState` instances to simplify the debugging on different servers.
* **Changed** – Dashboard UI now have full-width layout to display more data (by @danillewin).
* **Changed** – Query time from storage in recurring and delayed schedulers when supported by storage.
* **Changed** – Speedup delayed jobs when custom default queue is specified by avoiding extra state transition.
* **Changed** – Display scheduled job count when enqueued count is zero on the main metric.
* **Changed** – Don't display queue name in state transition list when it's the `default` one.
* **Changed** – Re-implement `TaskExtensions.WaitOneAsync` only with the `RegisterWaitForSingleObject` method.
* **Changed** – Expose state data dictionaries in list DTOs when supported by storage.
* **Changed** – Make it possible to display methods of non-loaded jobs in Dashboard UI when supported by storage.
* **Fixed** – Check job details for the `null` value before passing it to renderers (regression).
* **Deprecated** – `AddOrUpdate` overloads with optional params defined in the `RecurringJobManagerExtensions` class.
* **Deprecated** – `AddOrUpdate` overloads with optional parameters defined in the `RecurringJob` class.
* **Deprecated** – `AddOrUpdate` method overloads with no `recurringJobId` parameter.
* **Deprecated** – `RecurringJobOptions.QueueName` property, new methods should be used instead.

**Hangfire.SqlServer**

* **Added** – Implement the `Connection.GetUtcDateTime` feature to make work new changes in schedulers.
* **Changed** – Display scheduled and processing jobs in the ascending order in Dashboard UI.

### 1.8.0-beta2  (v1.8.0-beta2)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.8.0-beta2>

### Release Notes

**Hangfire.Core**

* **Added** – `MisfireHandlingMode.Strict` to create job for each missed recurring job occurrence.
* **Added** – Allow to pass parameters when creating a job (by @brian-knoll-micronetonline).
* **Added** – Make it possible to use specify multiple `JobContinuationOptions` for a continuation.
* **Added** – `CreateJob` method to the `JobStorageTransaction` abstract class.
* **Added** – `SetJobParameter` method to the `JobStorageTransaction` abstract class.
* **Changed** – Allow to query job parameters without roundtrip when supported by a storage.
* **Changed** – Turn `JobContinuationOptions` enum into flags while still possible.
* **Changed** – Avoid storage roundtrip to query job data in worker, take data from previous state change.
* **Fixed** – Don't overwrite existing argument values with null job parameters when using `FromParameter` attribute.
* **Fixed** – Job continuation mistakenly started when using the new `OnlyOnDeletedState` option.

**Hangfire.SqlServer**

* **Changed** – Set default value for the `QueuePollInterval` option to `TimeSpan.Zero`.
* **Changed** – Use command batching by default with 5-minute maximum timeout.
* **Changed** – Enable `UseRecommendedIsolationLevel` option by default.

### 1.8.0-beta1  (v1.8.0-beta1)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.8.0-beta1>

### Release Notes

**Hangfire.Core**

* **Added** – Display deleted jobs in the Realtime and History graphs when supported by storage.
* **Added** – `DeletedState` now have the persisted `Exception` property.
* **Added** – `JobContinuationOptions.OnlyOnDeletedState` to create continuations after a failure.
* **Added** – `Exception` job parameter is passed to continuation when `UseResultsInContinuations` method is used.
* **Added** – `FromExceptionAttribute` to deal with an antecedent exception in a background job continuation.
* **Added** – Allow to filter exception types in `AutomaticRetryAttribute` by using the new `OnlyOn` property.
* **Added** – `IBackgroundProcess.UseBackgroundPool` now allows to pass thread configuration logic.
* **Added** – `IGlobalConfiguration.UseJobDetailsRenderer` method for custom renderers.
* **Added** – `BackgroundJobServerOptions.WorkerThreadConfigurationAction` option
* **Added** – Allow to pass custom data to `ApplyStateContext` and `ElectStateContext` instances.
* **Added** – Preserve custom data dictionary between the entire filter chain.
* **Added** – Fetch "Retries" metric with other statistics when supported by storage
* **Added** – `IGlobalConfiguration.UseDashboardMetrics` extension method to pass multiple metrics at once.
* **Added** – State renderer for the `DeletedState` to display its new exception property.
* **Added** – Virtual `JobStorage.GetReadOnlyConnection` method intended to return `JobStorageConnection` for replicas.
* **Added** – Virtual `JobStorage.HasFeature` method for querying optional features.
* **Added** – Optional `GetSetCount` and `GetUtcDateTime` methods for the `JobStorageConnection` class.
* **Added** – Optional `AcquireDistributedLock` and `RemoveFromQueue` methods for the `JobStorageTransaction` class.
* **Added** – Support for transactional acknowledge using new storage method for better handling some data loss scenarios.
* **Added** – `Factory`, `StateMachine` and `Performer` properties to context classes to avoid injecting services.
* **Added** – Allow to pass transaction to background job state changer when new methods implemented.
* **Added** – Optional `ParametersSnapshot` property for `BackgroundJob` and `JobData` classes to minimize roundtrips in future.
* **Changed** – Use the `AttemptsExceededAction.Delete` option by default in the global automatic retry filter.
* **Changed** – Move job to the `DeletedState` instead of `SucceededState` when its invocation was canceled by a filter.
* **Changed** – `FromParameterAttribute`-based logic now always overwrites arguments, even with non-null values.
* **Changed** – Improved display of real-time chart with more accents on failed and deleted jobs.
* **Changed** – Ignore some members when serializing a `JobFilterAttribute` instance to decrease size
* **Changed** – `ServerHeartbeatProcess` now uses `ThreadPriority.AboveNormal` to prioritize heartbeats.

**Hangfire.SqlServer**

* **Added** – Recommended Schema 8 migration with fixed `JobQueue.Id` column to use `bigint` type.
* **Added** – `SqlServerStorageOptions.PreferMicrosoftDataSqlClient` option to use the corresponding package.
* **Added** – `SqlServerStorage.SchemaVersion` metric for Dashboard UI.
* **Added** – Implement optional experimental transactional acknowledge for SQL Server (`UseTransactionalAcknowledge` option).
* **Changed** – Sliding invisibility timeout-based fetching method is now used by default with 5 minute timeout.
* **Fixed** – Ensure connection is released when exception is thrown when during lock release.

**Hangfire.NetCore** and **Hangfire.AspNetCore**

* **Added** – `IApplicationBuilder.UseHangfireServer` that accepts custom factory for `IBackgroundProcessingServer`.

### 1.7.37  (v1.7.37)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.37>

### Release Notes

* **Fixed** – Recurring job is scheduled to the past after recovering from error with `AddOrUpdate` (backported).
* **Fixed** – `AddOrUpdate` triggers execution of a recurring job, even if its next execution is in the future (backported).
* **Fixed** – Send heartbeats until full background processing server shutdown (backported).

### 1.7.36  (v1.7.36)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.36>

### Release Notes

**Hangfire.Core**

* **Fixed** – Remove job id from schedule when it's not in the Scheduled state for some reason.

**Hangfire.NetCore** and **Hangfire.AspNetCore**

* **Changed** – Set processing server to `null` in hosted service to avoid `ObjectDisposedException`.

### 1.7.35  (v1.7.35)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.35>

### Release Notes

**Hangfire.SqlServer**

* **Fixed** – Blocked workers regression since 1.7.28 when using multiple servers inside a process.

### 1.7.34  (v1.7.34)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.34>

### Release Notes

#### Hangfire.Core

* **Added** – Add reschedule functionality to `BackgroundJob` and `IBackgroundJobClient` (by @chrischu).
* **Fixed** – `ArgumentNullException` with tricky generic type with inheritance case for jobs.
* **Fixed** – Display "Aborted servers will be removed…" note only once aborted threshold passed.

### 1.7.33  (v1.7.33)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.33>

### Release Notes

#### Hangfire.SqlServer

* **Changed** – Use SQL Server as a time authority for server heartbeats.
* **Changed** – Increase `MinPollingDelayMs` for SQL Server to 100 milliseconds.
* **Changed** – Don't wait on SQL Server's side when using long polling for fetching.

#### Hangfire.AspNetCore

* **Fixed** – Implement support `IAsyncDisposable` for `IServiceScope` instances for newer .NET platforms.

### 1.7.32  (v1.7.32)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.32>

### Release Notes

#### Hangfire.Core
      
* **Added** – First version of Swedish translation of the Dashboard UI (by @karl-sjogren).
* **Changed** – More detailed message for exception when `JobStorage.Current` is not initialized.
* **Changed** – Make `TypeHelperSerializationBinder` class public to use it from custom serializer settings.
* **Fixed** – Small typos in French resources for the Dashboard UI (by @agriffard).
* **Fixed** – Document the exception for the `IJobCancellationToken` interface method (by @judah4).

#### Hangfire.NetCore and Hangfire.AspNetCore

* **Changed** – Wait for application to be ready before starting the server when using `AddHangfireServer`.
* **Fixed** – Do not return `null` as result of `StopAsync` in hosted service implementation (by @tomaszek92).

### 1.7.31  (v1.7.31)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.31>

### Release Notes

#### Hangfire.Core

* **Added** – `RecurringJob.TriggerJob` method that returns identifier of a triggered background job.
* **Added** – `RecurringJobManager.TriggerJob` as a replacement for the `TriggerExecution` method.
* **Changed** – Update Moment.js library used by Dashboard UI to version 2.29.4 (by @mmitchell-w).
* **Fixed** – Typos in pt-BR translation (by @gumbarros and @marcelcamargo).
* **Fixed** – Added missing parameter annotations for methods of the `RecurringJob` class.
* **Deprecated** – `RecurringJob.Trigger` method is now obsolete, `TriggerJob` is the replacement.
* **Deprecated** – `RecurringJobManager.TriggerExecution` method is now obsolete, `TriggerJob` should be used instead.

### New Contributors
* @gumbarros made their first contribution in https://github.com/HangfireIO/Hangfire/pull/2057
* @marcelcamargo made their first contribution in https://github.com/HangfireIO/Hangfire/pull/2072
* @mmitchell-w made their first contribution in https://github.com/HangfireIO/Hangfire/pull/2083

**Full Changelog**: https://github.com/HangfireIO/Hangfire/compare/v1.7.30...v1.7.31

### 1.7.30  (v1.7.30)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.30>

### Release Notes

* **Fixed** – Don't consider `SecurityException` as a non-catchable one.
* **Fixed** – Replace timer with a dedicated thread in `AspNetShutdownDetector` to avoid depending on thread pool.
* **Fixed** – Better ASP.NET shutdown detection with yet another check based on internal state.
* **Fixed** – Decrease `AspNetShutdownDetector`'s check intervals to detect shutdowns earlier.
* **Fixed** – Don't wait for server stop on AppDomain unloads when hosting in IIS to avoid delaying them.

### 1.7.29  (v1.7.29)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.29>

### Release Notes

#### Hangfire.Core

* **Added** – `RecurringJobManager.TriggerExecution` method that returns identifier of a created job.
* **Added** – `GetRecurringJobIds` extension method for `JobStorageConnection` that returns only identifiers.
* **Added** – `DashboardMetric.Url` property to make it possible for metrics on the Overview page to be clickable (by @twinmind).
* **Changed** – Bump Moment.js version to 2.29.3 in Dashboard UI (by @Westat-Transportation).
* **Fixed** – Deserialization issues with `DateOnly` and `TimeOnly` in .NET 6.0 or other new types in CoreLib.
* **Fixed** – Don't even try to catch unsafe exceptions like `OutOfMemoryException` or `StackOverflowException`.
* **Fixed** – Add non-breaking space between Server Id and Status glyph on the Servers page.
* **Fixed** – Problems with internal wait implementation shouldn't cause high CPU issues now, added protection and logging.
* **Fixed** – Wait can't be performed now on a signaled `ManualResetEvent` instance in `BackgroundExecution`.

#### Hangfire.SqlServer

* **Fixed** – Command batching is now fully working for the Microsoft.Data.SqlClient package (by @0xced).

### 1.7.28  (v1.7.28)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.28>

### Release Notes

**Hangfire.Core**

* **Fixed** – Reduce the number of attempts in `BackgroundJobStateChanger` to avoid infinite loops.
* **Fixed** – Typos in German translation (by @saxx).
* **Fixed** – Translations in Turkish translation (by @can-zengin).

**Hangfire.SqlServer**

* **Fixed** – Possibly fixed CPU consumption problems and high amounts of fetching queries after deploys to IIS.
* **Fixed** – No more than a single long-polling query is allowed per storage instance when using sub-second polling.
* **Fixed** – Don't depend on thread pool when sending heartbeats for active jobs to avoid problems when it's starved.

### 1.7.27  (v1.7.27)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.27>

### Release Notes

#### Hangfire.Core

* **Added** – Turkish language support for the Dashboard UI (by @csarigul).
* **Fixed** – Trigger button in the Dashboard UI doesn't respect a custom time zone resolver.
* **Fixed** – Dispatchers stopped when unable to add the ExecutionId data for an exception instance.
* **Fixed** – Safari's zoom feature breaks the Dashboard UI (by @oguzhantopcu).
* **Fixed** – Some typos in XML documentation comments (by @GitHubPang).

### 1.7.26  (v1.7.26)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.26>

### Security Patch

This security patch fixes a regression appeared in the previous version 1.7.25 that makes Dashboard UI available for remote requests in the default configuration, e.g. when no authentication filter specified. Please note that when custom authentication filter is defined as recommended in the documentation, everything works as expected, but upgrade is recommended in any case. Please read the [GHSA-7rq6-7gv8-c37h](https://github.com/HangfireIO/Hangfire/security/advisories/GHSA-7rq6-7gv8-c37h) security advisory for details.

<dl>
<dt>CVE ID</dt><dd>CVE-2021-41238</dd>
<dt>Affected Packages</dt><dd>Hangfire.Core = 1.7.25 (only)</dd>
<dt>Affected Platforms</dt><dd>All, including .NET Core, .NET Framework, Mono of any version</dd>
</dl>

**Hangfire.Core**

* **Security** – Fix "Dashboard UI accessible from outside by default since 1.7.25" regression.

### 1.7.25  (v1.7.25)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.25>

### Release Notes

**Hangfire.Core**

* **Changed** – Upgrade Bootstrap from 3.3.7 to version 3.4.1 in Dashboard UI.
* **Changed** – Upgrade Chart.js from 2.7.3 to version 2.9.4 in Dashboard UI.
* **Changed** – Upgrade jQuery from 2.2.4 to version 3.6.0 in Dashboard UI.
* **Fixed** – Check background job existence before adding a continuation id to job parameters.
* **Fixed** – Incorrect validation for the `HeartbeatInterval` option (by @GitHubPang).
* **Fixed** – Use better stacking for succeeded/failed charts in the Dashboard UI.
* **Fixed** – Move explicit styles to CSS to fix possible CSP errors in Dashboard UI.
* **Fixed** – Reset default sync auth filter when async one is specified in Dashboard UI.

**Hangfire.SqlServer**

* **Fixed** – Avoid any blocked rows when removing inactive servers from the `Server` table.

**Hangfire.NetCore** and **Hangfire.AspNetCore**

* **Added** – More overloads for the `AddHangfireServer` extension method in .NET Core.
* **Deprecated** – `UseHangfireServer` method for targets where `AddHangfireServer` one is available.

### 1.7.24  (v1.7.24)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.24>

**Hangfire.Core**

* **Added** – Support for async auth methods via the `DashboardOptions.AsyncAuthorization` property (#1803 by @rosenbjerg).
* **Fixed** – Error alert in Dashboard UI is now correctly shown when sidebar is present (#1869 by @danillewin).
* **Fixed** – Reference an empty favicon in Dashboard UI to prevent backend 404s (#1885 by @dan2468).
* **Fixed** – Back-to-site link text in Dashboard UI is now hidden on small screens (#1887 by @danillewin).
* **Fixed** – Avoid memory leak in the `AppBuilderExtensions` class (#1878 by @LordJZ).
* **Fixed** – Make the `TypeHelper` class public instead of internal to use it outside.

**Hangfire.SqlServer**

* **Changed** – Don't use the `readcommittedlock` table hint when not required.
* **Project** – Stop using `TransactionScope` class in tests, re-create database instead.
* **Project** – Make it possible to run SQL Server tests on Mono on Linux.

**Hangfire.AspNetCore**

* **Added** – Support for async auth methods via the `DashboardOptions.AsyncAuthorization` property (#1803 by @rosenbjerg).
* **Added** – Authorization policy support via the new `MapHangfireDashboardWithAuthorizationPolicy` method (#1663 by @dasiths).

### 1.7.23  (v1.7.23)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.23>

### Release Notes

**Hangfire.Core**

* **Added** – `JobId` property to `JobPerformanceException` for error logging purposes (by @Plasma).
* **Fixed** – `JsonSerializationException` when using `IdempotentCompletionAttribute`.
* **Fixed** – Unreported yet corner case related to daylight time transition by upgrading Cronos to 0.7.1 (by @aidmsu).
* **Fixed** – Dashboard issue: recurring job table doesn't handle very long cron strings.
* **Fixed** – Add missing argument-is-null check for the `DeserializePayload` method.
* **Project** – Replace deprecated `PerformContext` ctor usage to avoid alerts in SonarQube (by @kumaheiyama).
* **Project** – Avoid possible `NullReferenceException` in tests to fix alerts in Fortify analyser.
* **Project** – Release connections properly in tests to fix alerts in Fortify analyser.

**Hangfire.SqlServer**

* **Fixed** – `NotImplementedException` in `Transaction.EnlistPromotableSinglePhase` when running on Mono.

### 1.7.22  (v1.7.22)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.22>

### Release Notes

**Hangfire.Core**

* **Fixed** – Fonts-related regression in Dashboard UI after upgrading Bootstrap in 1.7.21.

### 1.7.21  (v1.7.21)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.21>

### Release Notes

**Hangfire.Core**

* **Changed** – Upgrade jQuery from 2.1.4 to 2.2.4 in Dashboard UI.
* **Changed** – Upgrade Bootstrap from 3.3.5 to 3.3.7 in Dashboard UI.
* **Changed** – Upgrade Moment.js to 2.29.1 in Dashboard UI.
* **Project** – Update RazorGenerator.MsBuild package from 2.4.7 to version 2.5.0.
* **Project** – Update 7-Zip.CommandLine package from 9.20.0 to version 18.1.0.

**Hangfire.SqlServer**

* **Fixed** – Ensure connection is disposed immediately when exception is thrown during lock release.
* **Fixed** – "A network-related or instance-specific error" when using `DisableConcurrentExecution` for long-running jobs.

### 1.7.20  (v1.7.20)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.20>

### Release Notes

Please see https://www.hangfire.io/blog/2021/03/19/hangfire-1.7.20.html for details, manual changes required to fix potential problems when using Hangfire.SqlServer as a job storage for those who already migrated to Schema 6 and 7. This problem will be also fixed in a new migration in Hangfire 1.8.0.

**Hangfire.Core**

* **Added** – Norwegian translations (PR #1794 by @khellang).
* **Fixed** – Correction on brazilian portuguese translations (PR #1828 by @Prestini).
* **Fixed** – Changing time zone of recurring job without changing cron expression causes immediate execution.

**Hangfire.SqlServer**

* **Fixed** – `Schema 6` migration now fixes problem that prevents 2,147,483,648th job from being enqueued.

**Hangfire.NetCore** and **Hangfire.AspNetCore**

* **Added** – An overload for `AddHangfireServer` utilizing `IServiceProvider` (PR #1800 by @penenkel).
* **Added** – `IBackgroundJobClientFactory` and `IRecurringJobManagerFactory` interfaces to fix the following bug.
* **Fixed** – Dashboard UI is unable to 'requeue' job on other then default `JobStorage`.

### 1.7.19  (v1.7.19)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.19>

### Release Notes

**Hangfire.Core**

* **Added** – German (Deutsch) Dashboard UI localization (PR #1772 by @d-oit).
* **Added** – `IGlobalConfiguration.UseMaxArgumentSizeToRender` method to avoid "VALUE TOO BIG" messages.
* **Changed** – Remove "readonly" keyword from the `JobMethodCallRenderer.MaxArgumentToRenderSize` field to support .NET 5.0.
* **Fixed** – Race condition in `AspNetShutdownDetector` leads to `NullReferenceException` (PR #1786 by @jr01).
* **Fixed** – Avoid ArgumentException: Item has already been added when preserving an original exception.
* **Project** – Add repository link to nuspec files (PR #1749 by @jeremyhayes).

**Hangfire.SqlServer**

* **Fixed** – Return `null` instead of throwing FormatException when job id can't be parsed.
* **Project** – Run the entire Hangfire.SqlServer test suite against the new Microsoft.Data.SqlClient package.

### 1.7.18  (v1.7.18)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.18>

### Release Notes

**Hangfire.SqlServer**

* **Added** – `SqlServerStorageOptions.DeleteExpiredBatchSize` option to remove more expired records in a single pass.
* **Fixed** – Don't throw from `SqlServerStorage.ToString` method when using custom factory or existing connection.

### 1.7.17  (v1.7.17)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.17>

### Release Notes

**Hangfire.SqlServer**

* **Fixed** – SqlException "Incorrect syntax near 'throw'" after upgrading to 1.7.15 when using SQL Server 2008 or 2008R2.

### 1.7.16  (v1.7.16)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.16>

### Release Notes

**Hangfire.SqlServer**

* **Fixed** – Blocking problems when using multiple storages with the same queue names in the same process (appeared in 1.7.9).

### 1.7.15  (v1.7.15)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.15>

### Release Notes

**Hangfire.Core**

* **Added** – `IGlobalConfiguration.UseMaxLinesInExceptionDetails` option to cap the size of stack traces.
* **Changed** – Only the first 100 lines of a stack trace will be preserved now by default in Failed state.
* **Fixed** – Don't let exceptions with huge stack traces take up too much storage space.

**Hangfire.SqlServer**

* **Fixed** – Avoid deadlocks when using the `SetJobParameter` method without introducing issues for older schemas.
* **Fixed** – Remove duplicate sorting in the `SqlServerMonitoringApi.GetJobs` method which is used by a lot of queries.

### 1.7.14  (v1.7.14)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.14>

### Release Notes

**Hangfire.SqlServer**

* **Changed** – Use better queries for jobs with 3 and 4 parameters, this is a common case.
* **Fixed** – Duplicate entries in the `JobParameters` table after upgrading to version 1.7.13.
* **Fixed** – Extensive retries on a method that has a retry attribute after upgrading to 1.7.13.
* **Fixed** – "ArgumentException: An item with the same key has already been added. Key: RetryCount" in `SqlServerMonitoringApi`.

### 1.7.13  (v1.7.13)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.13>

### Release Notes

**Hangfire.Core**

* **Added** – Catalan translation for Dashboard UI (based on Spanish translation, by @agausachs).
* **Added** – Support for configuring recommended serializer settings via callback (by @Yaevh).
* **Fixed** – Use correct wording for job parameters in Job Details page, add it to resources.
* **Fixed** – Don't push negative points to the realtime graph in dashboard.
* **Fixed** – Don't depend on history collection type returned from Storage API.
* **Project** – Execute tests one by one to ensure exit code isn't being lost (by @willchis).

**Hangfire.SqlServer**

* **Added** – `UseIgnoreDupKeyOption` for SQL Server storage configuration (changes to [Set] and [Hash] tables required).
* **Fixed** – Don't truncate too long keys silently, throw exceptions instead.
* **Fixed** – Add missing null checks for methods in the `SqlServerWriteOnlyTransaction` class.
* **Fixed** – Change `holdlock` hint to `xlock` in `merge` statements in transaction to prevent deadlocks.
* **Fixed** – Don't rethrow "Lock request time out period exceeded" exceptions from expiration manager.
* **Fixed** – Increase [Server].[Id] column's length to 200 for new installations.

### 1.7.12  (v1.7.12)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.12>

### Release Notes

* **Added** – Display actual job payload and exception message on job details page when could find the method.
* **Added** – French translation for Dashboard UI (by @PaulARoy).
* **Added** – Expose IStorageConnection.GetRecurringJobs(IEnumerable ids) to public.
* **Changed** – Bump thread priority in heartbeat process for constrained environments.
* **Changed** – Display job properties in a dedicated row in job details page.
* **Fixed** – Avoid storage round-trip when displaying continuations on job details page.

### 1.7.11  (v1.7.11)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.11>

### Release Notes

**Hangfire.Core**

* **Added** – Display recurring job exceptions directly in the Dashboard UI.
* **Added** – Add built-in support for reliable shutdown detection of ASP.NET apps.
* **Changed** – Internal feature to perform state changes without calling any filters.
* **Changed** – Decrease the number of retry attempts for recurring jobs to 5.
* **Changed** – Unify exception handling in recurring job scheduler.
* **Fixed** – Let workers to ignore any state change filters when all previous attempts to call them failed.
* **Fixed** – Don't let `RecurringJobScheduler` to stall the pipeline when extension filters throw an exception.
* **Fixed** – Don't let `DelayedJobScheduler` to stall the pipeline when state filters throw an exception.
* **Fixed** – `JobLoadException` when new methods deployed, caused by overlapped recycles in ASP.NET applications.
* **Fixed** – Configuration changes aren't taken into account, caused by overlapped recycles in ASP.NET.
* **Fixed** – Zombie servers shown on the "Servers" page that aren't stopped automatically unless app pool is recycled.
* **Fixed** – Pass the whole exception to the `Error` field of a recurring job.
* **Fixed** – Re-schedule recurring jobs with unsupported versions, instead of stopping the pipeline.
* **Fixed** – Don't stumble over non-existing recurring jobs in a scheduler.
* **Fixed** – Add another check before removing non-existing jobs from delayed jobs to avoid race conditions.
* **Fixed** – Avoid throwing `NullReferenceException` instead of `InvalidOperationException` when deserializing a job.
* **Fixed** – Don't transform queue names to upper case in the Dashboard UI.

### 1.7.9  (v1.7.9)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.9>

### Release Notes

**Hangfire.Core**

* **Fixed** – Additional Chinese translation for Dashboard UI (by @brookqin).
* **Fixed** – Added `null` checks for expired failed jobs in Dashboard UI (by @ppkale1995-cimpress).
* **Fixed** – Add word break to definition lists for state cards in Dashboard UI.
* **Fixed** – Render long recurring job identifiers correctly in Dashboard UI.

**Hangfire.SqlServer**

* **Changed** – Implement long polling fetch for sub-second polling delays without `sp_getapplock`.
* **Fixed** – Don't leak `DbConnection` instance when an exception occurs during its opening.
* **Fixed** – Can not obtain connection from the pool exception after database was offline.
* **Fixed** – High number of waits in SQL Server when Hangfire Servers are idle.

**Documentation**

* **Changed** – Update "Making ASP.NET Applications Always Running" for .NET Core (by @unionthugface).
* **Fixed** – Fix typo in the README.md file (by @tawfikkh).

### 1.7.8  (v1.7.8)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.8>

### Release Notes

**Hangfire.Core**

* **Added** – `IGlobalConfiguration.UseResultsInContinuations` method to globally enable results for continuations.
* **Added** – Ability to push antecedent job's result to continuations via job parameters with `ContinuationsSupport`.
* **Added** – `JobParameterInjectionFilter` server filter to inject job parameters as arguments.
* **Added** – Allow to specify a custom thread factory in `UseBackgroundPool` methods.
* **Changed** – Add retry attempts for recurring jobs instead of immediately disabling them.
* **Fixed** – `CultureInfo.InvariantCulture` is now restored properly in background jobs.
* **Fixed** – Recurring jobs aren't triggered early after changing their cron expressions.
* **Fixed** – Don't trigger recurring job when it can't be scheduled due to errors.
* **Fixed** – Argument with a `null` value is skipped when displaying job arguments in Dashboard UI.
* **Fixed** – Add a workaround for resolving `System.Diagnostics.Debug` type in .NET Core 3.0.
* **Deprecated** – Deprecate the `JobActivatorScope.InnerScope` property as it wasn't implemented.

**Hangfire.SqlServer**

* **Added** – Support for Microsoft.Data.SqlClient package when using a custom connection factory (Part II).
* **Fixed** – Remove `System.Data.SqlClient` dependency from `SqlCommandBatch` and `ExpirationManager`.

**Hangfire.AspNetCore**

* **Added** – `IAppBuilder.MapHangfireDashboard` method for ASP.NET Core 3.0 endpoint routing (by @kendaleiv).
* **Changed** – Add explicit `netcoreapp3.0` target with "Microsoft.AspNetCore.App" framework reference (by @stebueh).

**Hangfire.NetCore**

* **Changed** – Add explicit `netcoreapp3.0` target with reference to "3.0.0" packages.

**Documentation**

* **Added** – Making ASP.NET Core application always running on IIS (by @bamotav).
* **Fixed** – Small typo on the "Getting Started in ASP.NET Core applications" page (by @msynk).
* **Fixed** – Small spelling correction in "Throttling &amp; Rate Limiters" (by @Bert-R).
* **Fixed** – Small typo in the "Sending Email" tutorial (by @nabeelvalley).
* **Fixed** – Correct spelling of 'prerequisites' in README.md (by @lgirvin).

### 1.7.7  (v1.7.7)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.7>

### Release Notes

**Hangfire.Core**

* **Changed** – Produce a trace log message with details when updating a recurring job.
* **Changed** – Return early from `CoreBackgroundJobFactory.Create` when storage returns `null`.
* **Project** – Minor changes for the `Readme.md` file (PR #1526 by @231293).
* **Project** – Add `netcoreapp3.0` target framework for Hangfire.Core.Tests.
* **Project** – Add support for MSBuild 15.0 (VS 2019) when building `*.cshtml` files.

**Dashboard UI**

* **Added** – Allow modification of the Dashboard UI title (PR #1231 by @tbertenshaw).
* **Added** – Support for HTML tags on the Dashboard UI title (PR #1545 by @augustoproiete).
* **Added** – Buttons for 1,000 and 5,000 items per page in dashboard (#1518).
* **Added** – Links to previous/next pages to the top of the dashboard page (#1534).
* **Changed** – Expose the `RazorPage.Context` property as a public member.
* **Fixed** – Supplementary Chinese translation (PR #1523 by @mccj).
* **Fixed** – Don't update real-time chart when too much time passed since the last update (#1497).

**Hangfire.SqlServer**

* ~~**Added** – Add support for Microsoft.Data.SqlClient package when using custom connection factory (#1514).~~ (postponed to 1.7.8)
* **Added** – Add `UseFineGrainedLocks` option to avoid deadlocks in some theoretical cases.
* **Added** – Add missing overload for `UseSqlServerStorage` with connection factory parameter only.
* **Added** – Expose the SqlServerObjectsInstaller.GetInstallScript method (PR #1527 by @altso).
* **Fixed** – Make command batching working on .NET Core when using System.Data.SqlClient 4.7.0 and higher.
* **Fixed** – Permit dash characters (`-`) in schema names (PR #1531 by @kendaleiv).
* **Fixed** – Escape square bracket characters in schema names.
* **Project** – Add support for `netcoreapp3.0` target in Hangfire.SqlServer.Tests.
* **Project** – Take schema name from constant in Hangfire.SqlServer.Tests (PR #1532 by @kendaleiv).
* **Project** – Make Hangfire.SqlServer.Tests work on Linux in Travis CI environment.

**Hangfire.AspNetCore**

* **Fixed** – Add missing `AddHangfireServer` method for .NET Framework 4.6.1 and higher (PR #1488 by @danstur).

### 1.7.6  (v1.7.6)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.6>

### Release Notes

**Hangfire.Core**

* **Changed** – Add support for dash characters (`-`) in queue names (PR #1469 by @augustoproiete).
* **Fixed** – Show actual error in Dashboard UI when recurring job can't be scheduled.
* **Fixed** – Ensure backward compatibility when JSON payloads are serialized with field names only.
* **Fixed** – Non-awaited continuations can bring down the whole app when `TaskScheduler` is set to `null`.
* **Fixed** – Timeout value is not respected in some cases in the `WaitOneAsync` method.

### 1.7.5  (v1.7.5)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.5>

### Release Notes

**Hangfire.Core**

* **Fixed** – Show error message when there's an error loading the statistics in Dashboard UI (PR #1242 by @prochnowc).
* **Fixed** – Properly handle recurring jobs with null or empty 'Job' field.
* **Fixed** – Disable recurring job when we can't schedule it due to an error.
* **Fixed** – Use `LazyThreadSafetyMode.PublicationOnly` to avoid caching "JobStorage.Current is null" exceptions.

**Hangfire.AspNetCore** &amp; **Hangfire.NetCore**

* **Fixed** – Add missing overload for the `AddHangfireServer` method with "options" action.

### 1.7.4  (v1.7.4)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.4>

### Release Notes

**Hangfire.Core**

* **Added** – `BackgroundJobClient.RetryAttempts` property to make job creation resilient to transient exceptions.
* **Added** – Dashboard localization support in `pt-BR` (by @candidodmv).
* **Changed** – Protect background dispatchers from moving from stopped state to non-stopped one.
* **Changed** – Unify `WaitOne` and `WaitOneAsync` methods with timeout and cancellation token for `WaitHandle` class.
* **Fixed** – Don't hide an original fatal exception occurred in dispatchers in some cases.
* **Fixed** – Dashboard UI to display "await" keyword on all task-like methods.
* **Fixed** – Display links properly in an informational message on the Servers page in Dashboard UI.
* **Fixed** – Wait for the heartbeat process before shutting down a server.

**Hangfire.SqlServer**

* **Fixed** – Potential deadlocks cause by suboptimal queries when using `SlidingInvisibilityTimeout` fetching.
* **Fixed** – Prevent zero delays between fetch retry attempts when lock acquisition failed without blocking.
* **Fixed** – Specify float precision explicitly for the `Score` column in the `AddToSet` method.

### 1.7.3  (v1.7.3)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.3>

### Release Notes

This version contains **security fixes** to prevent possible XSS attacks as described in #1441. They don't relate to user data submitted to Hangfire directly via method arguments, but it's recommended to upgrade anyway. If you are using Hangfire 1.6, please upgrade to version [1.6.26](https://github.com/HangfireIO/Hangfire/releases/tag/v1.6.26) instead.

<dl>
<dt>Affected Packages</dt><dd>Hangfire.Core &le; 1.6.25, 1.7.0, 1.7.1, 1.7.2</dd>
<dt>Affected Platforms</dt><dd>All, including .NET Core, .NET Framework, Mono of any version</dd>
</dl>

**Steps to reproduce**

```csharp
public static void Xss()
{
    BackgroundJob.Enqueue(() => Xss2());
}

public static void Xss2()
{
    throw new Exception("<script>alert(1);</script>");
}
```

**Hangfire.Core**

* **SECURITY** – Use `HtmlEncode` in all remaining places in Dashboard UI to prevent XSS attacks.
* **Added** – Added Dutch language, and updated missing translation on "Servers" page (by @r-win).
* **Added** – `Cron.Never` method for adding manual recurring jobs that never fire (by @michaltalaga).
* **Fixed** – Add missing `AddOrUpdate` extension methods for the `IRecurringJobManager` interface.
* **Deprecated** – Unused `HtmlHelper.FormatProperties` method is now obsolete.

**Hangfire.SqlServer**

* **Fixed** – Wrong error message in migration script, when @CurrentSchemaVersion has a NULL value (by @penenkel).

### Reporting security issues 

In order to give the community time to respond and upgrade we strongly urge you report all security issues privately. Please email us at [support@hangfire.io](support@hangfire.io) with details and we will respond ASAP. Security issues always take precedence over bug fixes and feature work. We can and do mark releases as "urgent" if they contain serious security fixes.

### 1.7.2  (v1.7.2)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.2>

### Release Notes

> Please see https://docs.hangfire.io/en/latest/upgrade-guides/upgrading-to-hangfire-1.7.html to learn how to upgrade from 1.6.X.

**Hangfire.Core**

* **Added** – `DashboardOptions.TimeZoneResolver` property to handle custom time zone resolvers in Dashboard UI.
* **Fixed** – `RecurringJob.AddOrUpdate` method is now able to update a broken recurring job.
* **Fixed** – Recurring job scheduler now properly handles recurring jobs whose job method or time zone is wrong.
* **Fixed** – Don't throw an exception on Recurring Jobs page when time zone can't be resolved.

**Hangfire.AspNetCore & Hangfire.NetCore**

* **Added** – Automatically resolve `ITimeZoneResolver` service for the `DashboardOptions.TimeZoneResolver` property.
* **Fixed** – Allow to resolve `IJobFilterProvider` service from the `AddHangfire` method.

**Hangfire.SqlServer**

* **Fixed** – Occasional "DataException: Error parsing column" error when using blocking fetch.

### 1.7.1  (v1.7.1)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.1>

### Release Notes

> Please see https://docs.hangfire.io/en/latest/upgrade-guides/upgrading-to-hangfire-1.7.html to learn how to upgrade to 1.7.X.

This is a patch release that adds some nice features for Dashboard UI, knows how to deal with recurring jobs with invalid Cron expressions, and contains some minor improvements for SQL Server storage. Also, `Hangfire.NetCore` package was added to support new .NET Core Worker Service applications without referencing any ASP.NET Core packages.

**Hangfire.Core**

* **Added** – `DashboardOptions.IgnoreAntiforgeryToken` property to disable token validation in Dashboard UI.
* **Added** – Display hints regarding server status on Servers page in Dashboard UI.
* **Added** – Highlight recurring jobs with no next execution in Dashboard UI.
* **Added** – Show actual error in Dashboard UI when recurring job has an invalid Cron expression.
* **Fixed** – `InvalidOperationException` when `AllowSynchronousIO` option isn't set in ASP.NET Core 3.0.
* **Fixed** – Set `NextExecution` value to `null` when existing recurring job has an invalid Cron expression.
* **Fixed** – Make dashboard charts to be more culture-specific to use correct time format.
* **Fixed** – Obsolete `UseSerializationSettings` comment now contains correct method name (by @PaitoAnderson).
* **Project** – `resx` files now re-generated automatically when building a project.

**Hangfire.NetCore**

* **Added** – Worker Service host support for .NET Core without unnecessary dependencies to ASP.NET Core.

**Hangfire.SqlServer**

* **Changed** – Use blocking fetch implementation only for sub-second polling intervals.
* **Fixed** – Don't fail with an exception when can't connect to MS SQL instance during start-up.
* **Fixed** – Don't access the `JobQueue` table when using blocking query and don't have results.

### 1.7.0  (v1.7.0)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.0>

### Release Notes

Please see the [Upgrading to Hangfire 1.7](https://docs.hangfire.io/en/latest/upgrade-guides/upgrading-to-hangfire-1.7.html) article to learn more about the upgrade steps.

**Hangfire.Core**

* **Added** – Full .NET Core 2.0 support by explicitly targeting .NET Standard 2.0.
* **Added** – `IGlobalConfiguration.SetDataCompatibilityLevel` to enable rolling upgrades from version 1.6.
* **Added** – `IGlobalConfiguration.UseRecommendedSerializerSettings` method for new installations.
* **Added** – Assemblies now loaded automatically when resolving a type when using default type resolver.
* **Added** – Custom `TaskScheduler` can now be specified in `BackgroundJobServerOptions` for workers.
* **Added** – `IdempotentCompletionAttribute` filter to enforce strict order for continuations.
* **Added** – `IBackgroundJobClient.ContinueJobWith` methods to replace `ContinueWith` ones in future for clarity.
* **Added** – `JobStorage.LinearizableReads` virtual property to avoid unnecessary waits in state changer.
* **Added** – Allow async methods to run their continuations on worker thread by disabling `TaskScheduler`.
* **Added** – Multi-stage shutdown to wait for graceful completion before starting to abort jobs.
* **Added** – Asynchronous checks for job cancellation, `IJobCancellationToken` can be replaced with `CancellationToken` (by @pieceofsummer).
* **Added** – Possibility to create millions of recurring jobs without stressing the scheduler.
* **Added** – Second-based recurring jobs are fully supported now with 6-part cron expressions.
* **Added** – Support for custom `TimeZoneInfo` resolvers in recurring jobs for interoperability purposes.
* **Added** – Package now explicitly targets .NET Standard 2.0, and .NET Framework 4.6 target added as well.
* **Added** – Type roundtrip support between .NET Core and .NET Framework for most common types.
* **Added** – Allow to specify queue names based on job arguments with `QueueAttribute` via patterns.
* **Added** – `PerformContext.Storage` property to allow server filters to spawn connections.
* **Added** – `GetFirstByLowestScoreFromSet` connection method overload that returns multiple items (by @cdschneider).
* **Added** – Entry point for custom job naming strategies available for dashboard (by @pieceofsummer).
* **Added** – `JobDisplayNameAttribute` class for displaying jobs in dashboard, available on .NET Core (by @pieceofsummer).
* **Added** – Support for async jobs returning ValueTask&lt;T&gt; (by @pieceofsummer).
* **Added** – Support for asynchronous background processes, opens the road toward async storage.
* **Added** – Circuit breaker pattern for background processes to reduce the logging pressure.
* **Added** – Processing server is now able to detect it was expired, and restart itself with the new id.
* **Added** – Ability to use custom delays for automatic retries of a background job.
* **Added** – `ThreadAbortException` and `ThreadInterruptedException` handling to keep the background process running.
* **Added** – Support for complex Cron expressions, including the `L`, `W`, `#` characters.
* **Added** – `JobActivator.BeginScope` method overload with the full `PerformContext` (by @jeroenvervaeke).
* **Added** – Support for read-only view for dashboard (by @mikechamberlain).
* **Added** – Storage property to control the job expiration time (by @rsilvanet).
* **Added** – Decrease the size of serialized type payloads and remove version information.
* **Changed** – Make `TaskScheduler.Default` the default scheduler for async jobs to avoid breaking changes.
* **Changed** – Split serializer setting to Internal and User scopes to isolate them (Version_170 Switch).
* **Changed** – Don't allow to affect internal serialization even by `JsonConvert.DefaultSettings` (Version_170 Switch).
* **Changed** – Share the same type binder between Hangfire itself and Newtonsoft.Json (Version_170 Switch).
* **Changed** – Use more compact representation of dates when using `SerializeDateTime` (Version_170 Switch).
* **Changed** – Stop using special case for `DateTime` argument serialization (Version_170 Switch).
* **Changed** – Don't serialize unused `AwaitingState.Expiration` field (Version_170 Switch).
* **Changed** – Specify parameter type when serializing arguments to allow using `TypeNameHandling.Auto` option.
* **Changed** – Use case sensitive search when resolving a type as by default in .NET.
* **Changed** – Make `SucceededState` constructor public to allow state serialization.
* **Changed** – Add `IBackgroundJobFactory.StateMachine` property (breaking change for low level API).
* **Changed** – Replace Rickshaw with Chart.js to have beautiful charts with less headache.
* **Changed** – `DelayedJobScheduler` is able to use the new storage method to query multiple jobs at once.
* **Changed** – `RecurringJobScheduler` now uses index-based checks to fetch only those jobs that should be scheduled.
* **Fixed** – Worker now logs an error, when all the state change attempts failed due to an exception.
* **Fixed** – Don't serialize arguments multiple times when showing job details in dashboard.
* **Fixed** – `DateTimeOffset` conversion error when it was serialized with `TypeConverter`.
* **Fixed** – Remove duplicate of argument deserialization code for obsolete `Job` class methods.
* **Fixed** – Decorate all the exceptions with the `SerializableAttribute`.
* **Fixed** – `ArgumentNullException` when job class contains method with non-resolvable generic arguments.
* **Fixed** – "Failed to initialize CoreCLR" error, by removing reference to `Microsoft.NETCore.Portable.Compatibility`.
* **Fixed** – Possible race conditions in `RecurringJobScheduler` that may lead to job duplicates.
* **Fixed** – Configuration inconsistency introduced in 1.6.18 leading to issues with custom `JobActivator`.
* **Fixed** – Triggering the recurring task doesn't update its last execution time.
* **Fixed** – Recurring

_…truncated…_

### 1.7.0-rc2  (v1.7.0-rc2)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.0-rc2>

### Release Notes

This is the second release candidate of the upcoming version 1.7.0 that fixes some issues and avoids some breaking changes. Please see the [Upgrading to Hangfire 1.7](https://docs.hangfire.io/en/latest/upgrade-guides/upgrading-to-hangfire-1.7.html) article to learn more about the upgrade steps.

**Hangfire.Core**

* **Changed** – Allow `IdempotentCompletion` filter to move a job to non-final and non-processing states.
* **Changed** – Make `TaskScheduler.Default` the default scheduler for async jobs to avoid breaking changes.
* **Changed** – Increase delays between continuation state fetch attempts to reduce storage load.
* **Changed** – Avoid breaking changes in `BackgroundJobServer` and `RecurringJobScheduler` classes.
* **Changed** – Add `IBackgroundJobFactory.StateMachine` property (breaking change for low level API).
* **Fixed** – Deadlock in async methods when `ConfigureAwait(false)` is used (regression in RC 1).

**Hangfire.AspNetCore**

* **Changed** – Allow to use registered custom low-level classes like `IBackgroundJobFactory` again.
* **Fixed** – `NullReferenceException` when application is stopped due to an exception during the start.

**Hangfire.SqlServer**

* **Fixed** – Don't use clustered index on table variable in `CountersAggregator`, works only in MSSQL 2014.
* **Fixed** – Don't use the `CONCAT` function in migration script, works only in MSSQL 2012.

### 1.7.0-rc1  (v1.7.0-rc1)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.0-rc1>

### Release Notes

This is the first release candidate of version 1.7 that adds a lot of new features and improvements and allows rolling upgrades from version 1.6.X and below. Detailed migration guide will be posted in the documentation next week, but the point of this release is to disable by default all the changes that are incompatible with 1.6 installations.

**Known issues**

* Due to the bug in the `CoreBackgroundJobPerformer` class, there's a race condition that leads to deadlocks when running asynchronous job methods, when `ConfigureAwait(false)` method is called inside. This will be fixed in 1.7.0-rc2, and as a workaround, set the `BackgroundJobServerOptions.TaskScheduler` property to `TaskScheduler.Default` for your processing servers.
* SQL Server 2014 is required for the `Hangfire.SqlServer` package to properly run the migration and execute `CountersAggregator` process. The required version will be lowered back to SQL Server 2008 R2 in 1.7.0-rc2.

**Upgrading from beta versions**

If you are upgrading from 1.7.0 betas, upgrade all the servers first to the newest `rc1` version and only then use add the following configuration lines to turn on the new features that were disabled by default in this release candidate. Please note that `CompatibilityLevel.Version_170` contains some changes that your existing 1.7.0-beta servers may not understand.

```csharp
GlobalConfiguration.Configuration
    .SetDataCompatibilityLevel(CompatibilityLevel.Version_170) // Compact data representation
    .UseSimpleAssemblyNameTypeSerializer() // Compact type serialization format
```

If you are using SQL Server as a job storage, set the following settings if you were using 1.7.0 betas just after updating the package. These settings are the same that were enabled by default for beta versions, so your existing servers are compatible with them.

```csharp
    .UseSqlServerStorage("connection_string", new SqlServerStorageOptions
    {
        CommandBatchMaxTimeout = TimeSpan.FromMinutes(5)
        SlidingInvisibilityTimeout = TimeSpan.FromMinutes(5),
        QueuePollInterval = TimeSpan.Zero, // Set only when using SlidingInvisibilityTimeout
        DisableGlobalLocks = true, // Set only if `Schema 6` migration is applied
        UsePageLocksOnDequeue = true // Set only if `Schema 6` migration is applied
    })
```

**Hangfire.Core**

* **Added** – `IGlobalConfiguration.SetDataCompatibilityLevel` to enable rolling upgrades from version 1.6.
* **Added** – `IGlobalConfiguration.UseRecommendedSerializerSettings` method for new installations.
* **Added** – Assemblies now loaded automatically when resolving a type when using default type resolver.
* **Added** – Custom `TaskScheduler` can now be specified in `BackgroundJobServerOptions` for workers.
* **Added** – `IdempotentCompletionAttribute` filter to enforce strict order for continuations.
* **Added** – `IBackgroundJobClient.ContinueJobWith` methods to replace `ContinueWith` ones in future for clarity.
* **Added** – `JobStorage.LinearizableReads` virtual property to avoid unnecessary waits in state changer.
* **Changed** – Split serializer setting to Internal and User scopes to isolate them (Version_170 Switch).
* **Changed** – Don't allow to affect internal serialization even by `JsonConvert.DefaultSettings` (Version_170 Switch).
* **Changed** – Share the same type binder between Hangfire itself and Newtonsoft.Json (Version_170 Switch).
* **Changed** – Use more compact representation of dates when using `SerializeDateTime` (Version_170 Switch).
* **Changed** – Stop using special case for `DateTime` argument serialization (Version_170 Switch).
* **Changed** – Don't serialize unused `AwaitingState.Expiration` field (Version_170 Switch).
* **Changed** – Use custom `SynchronizationContext` for async methods to run their continuations on worker thread.
* **Changed** – Specify parameter type when serializing arguments to allow using `TypeNameHandling.Auto` option.
* **Changed** – Use case sensitive search when resolving a type as by default in .NET.
* **Changed** – Make `SucceededState` constructor public to allow state serialization.
* **Fixed** – Worker now logs an error, when all the state change attempts failed due to an exception.
* **Fixed** – Ensure `RecurringJobScheduler` doesn't go into infinite loop when there's server of an older version.
* **Fixed** – Implement `BackgroundTaskScheduler.MaximumConcurrencyLevel` property.
* **Fixed** – Dashboard renderer for `AwaitingState` displays `Option` property as string again.
* **Fixed** – Don't serialize arguments multiple times when showing job details in dashboard.
* **Fixed** – `DateTimeOffset` conversion error when it was serialized with `TypeConverter`.
* **Fixed** – Remove duplicate of argument deserialization code for obsolete `Job` class methods.
* **Fixed** – Decorate all the exceptions with the `SerializableAttribute`.
* **Project** – Add `DataCompatibilityRangeFact` and `DataCompatibilityRangeTheory` classes for compatibility checks.
* **Project** – Reduce test execution time by removing unnecessary waits.
* **Ported** – Merged updates from version 1.6.23.

**Hangfire.AspNetCore**

* **Changed** – Remove internal service registrations that are inconsistent with server options.
* **Ported** – Merged updates from version 1.6.23.

**Hangfire.SqlServer**

* **Added** – `SqlServerStorageOptions.EnableHeavyMigrations` switch to automatically install even heavy migrations.
* **Added** – `Schema 7` migration to fix the `IX_HangFire_Set_Score` index to include the `Key` column.
* **Added** – `SqlServerStorageOptions.DisableGlobalLocks` property to avoid custom locking scheme.
* **Added** – `SqlServerStorageOptions.UsePageLocksOnDequeue` property to use less CPU consuming fetch.
* **Changed** – `Schema 6` migration is disabled by default for existing installations, because it may take too long.
* **Changed** – Don't throw an excep

_…truncated…_

### 1.7.0-beta4  (v1.7.0-beta4)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.0-beta4>

### Release Notes

**Hangfire.Core**

* **Changed** – `StopTimeout` introduced in 1.7.0-beta3 now defaults to zero seconds (2ca6fc48edfbf370c5aa444496d5721c81fe2396).
* **Fixed** – `NotSupportedException` thrown by `RecurringJobScheduler` (regression, 001ee0869d811ee34ec5f0af6d29ad2c47b26dc1).
* **Fixed** – `NotSupportedException` thrown by `DelayedJobScheduler` (regression, 3c2ec58805bd8f3e210047f667260f98df4fdcae).
* **Fixed** – `RecurringJobManager.AddOrUpdate` method doesn't preserve `LastJobId` (regression, 4748d7e9c1e3e0ac82ea21e18b8e2c99d034232e).
* **Fixed** – Cache results of the `IsBatchingAvailable` method per connection type (6dc93e83c514c03a6d4459af9ddd3c3c0c8c3e84).

### 1.7.0-beta3  (v1.7.0-beta3)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.0-beta3>

### Release Notes

**Hangfire.Core**

* **Added** – Multi-stage shutdown to wait for graceful completion before starting to abort jobs.
* **Added** – Asynchronous checks for job cancellation, `IJobCancellationToken` can be replaced with `CancellationToken` (PR&nbsp;#976 by @pieceofsummer).
* **Added** – Possibility to create millions of recurring jobs without stressing the scheduler.
* **Added** – Second-based recurring jobs are fully supported now with 6-part cron expressions (#167, #1262).
* **Added** – Support for custom `TimeZoneInfo` resolvers in recurring jobs for interoperability purposes.
* **Added** – Package now explicitly targets .NET Standard 2.0, and .NET Framework 4.6 target added as well (PR&nbsp;#1309).
* **Added** – Type round-trip support between .NET Core and .NET Framework for most common types.
* **Added** – Allow to specify queue names based on job arguments with `QueueAttribute` via patterns.
* **Added** – `PerformContext.Storage` property to allow server filters to spawn connections.
* **Added** – `GetFirstByLowestScoreFromSet` connection method overload that returns multiple items (PR&nbsp;#1251 by @cdschneider).
* **Changed** – New type serialization is disabled by default for compatibility reasons.
* **Changed** – Cronos package upgraded to 0.7.0 and internalized even on .NET Standard platforms.
* **Changed** – Replace Rickshaw with Chart.js to have beautiful charts with less headache (PR&nbsp;#1315).
* **Changed** – `DelayedJobScheduler` is able to use the new storage method to query multiple jobs at once (PR&nbsp;#1330, #38).
* **Changed** – `RecurringJobScheduler` now uses index-based checks to fetch only those jobs that should be scheduled (PR&nbsp;#1334).
* **Fixed** – `ArgumentNullException` when job class contains method with non-resolvable generic arguments.
* **Fixed** – Re-add missing fonts as embedded resources due to a regression appeared in 1.7.0-beta2.
* **Fixed** – "Failed to initialize CoreCLR" error, by removing reference to `Microsoft.NETCore.Portable.Compatibility` (#982, #1074).
* **Fixed** – Intermittent `JsonSerializationException` in .NET Core 2.0 (#1214).
* **Fixed** – Possible race conditions in `RecurringJobScheduler` that may lead to job duplicates.
* **Fixed** – Configuration inconsistency introduced in 1.6.18 leading to issues with custom `JobActivator`.
* **Fixed** – Backward compatibility issue with type serialization when `TypeNameHandling.All` is used.
* **Fixed** – Triggering the recurring task doesn't update its last execution time (#233).
* **Fixed** – Recurring job which don't have next execution (intentionally or not) don't cause exception.
* **Fixed** – Dashboard recurring jobs sorting is random (now it's based on next execution time, #391, #791).
* **Fixed** – Performance problems with huge amount of recurring jobs (#449).
* **Fixed** – `NextExecution` field of a recurring job has delay in value getting set. (#843)
* **Fixed** – Dashboard graphs have improper sizing (#1011).
* **Ported** – Merged updates from version [1.6.21](https://github.com/HangfireIO/Hangfire/releases/tag/v1.6.21) and [1.6.22](https://github.com/HangfireIO/Hangfire/releases/tag/v1.6.22).

**Hangfire.AspNetCore**

* **Added** – Full .NET Core 2.0 support by explicitly targeting .NET Standard 2.0.
* **Added** – An overloaded AddHangfire method with `IServiceProvider` parameter (#954 by @ericgreenmix and #1114 by @denis-ivanov).
* **Added** – `BackgroundJobServerHostedService` class based on `IHostedService` interface (#962).
* **Added** – `IServiceCollection.AddHangfireServer` method to register the server during configuration.

**Hangfire.SqlServer**

* **Changed** – Short paths for the CreateExpiredJob method to avoid some round-trips.
* **Changed** – Allow to use zero-based poll interval when sliding invisibility timeout.
* **Changed** – Set `SqlParameter` types explicitly to not to duplicate query plans.
* **Changed** – Batch support for `AddToQueue` method when default provider is used (PR&nbsp;#1331).
* **Changed** – Check `FetchedAt` has expected value to prevent prolonging others' work.
* **Changed** – Use more recent Dapper 1.50.7 on all platforms except .NET Framework 4.5.
* **Changed** – Dapper package is internalized now even on .NET Core to avoid possible conflicts.
* **Ported** – Merged updates from versions [1.6.21](https://github.com/HangfireIO/Hangfire/releases/tag/v1.6.21) and [1.6.22](https://github.com/HangfireIO/Hangfire/releases/tag/v1.6.22).

### 1.7.0-beta2  (v1.7.0-beta2)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.0-beta2>

### Release Notes

The goal of this release is to incorporate important changes from recent versions [1.6.18](https://github.com/HangfireIO/Hangfire/releases/tag/v1.6.18), [1.6.19](https://github.com/HangfireIO/Hangfire/releases/tag/v1.6.19) and [1.6.20](https://github.com/HangfireIO/Hangfire/releases/tag/v1.6.20), as well as provide great improvements for Hangfire.SqlServer unlocked by schema changes introduced in 1.7.0:

* **Blocking fetch**. It is possible now to avoid polling when using SQL Server. Short-lived (2 seconds) application locks are used to implement this behavior, and workers don't compete now with each other and don't perform unnecessary concurrent logical reads when queue is empty. The only requirement is to use sliding-expiration-based fetch as shown below.
* **Less CPU-consuming fetch** when using sliding expiration-based fetch. When using table as a queue, the major CPU consumption is done for scanning ghost rows, since SQL Server deletes records asynchronously. Now page locks are acquired to force SQL Server to remove them in-place, instead of postponing this action. It's essential to minimize the lifetime of these locks, so improvement works only for sliding-expiration fetch method.
* **Improved parallelism** for hashes, sets and lists. Instead of acquiring global, coarse-grained application locks, we now using regular SQL Server's locks. To avoid deadlocks, we are reordering writes in transactions to match clustered key sorting.

To use all the new features, consider adding the following lines to your configuration logic:

```csharp
GlobalConfiguration.Configuration
    .UseSqlServerStorage(@"connection_string", new SqlServerStorageOptions
    {
        SlidingInvisibilityTimeout = TimeSpan.FromMinutes(5), // To enable Sliding invisibility fetching
        CommandBatchMaxTimeout = TimeSpan.FromMinutes(5), // To enable command pipelining
        QueuePollInterval = TimeSpan.FromTicks(1) // To reduce processing delays to minimum
    })
```

**Hangfire.Core**

* **Fixed** – `MissingMethodException` when using Newtonsoft.Json 11 in .NET Core 2.X with continuations (by @pieceofsummer).
* **Ported** – Merged updates from versions 1.6.18 – 1.6.20.

**Hangfire.SqlServer**

* **Added** – Blocking fetch support for sliding expiration-based fetch to avoid excessive polling.
* **Changed** – Optimize sliding-expiration-based fetching to use even less CPU time.
* **Changed** – Use write reordering and fine-grained locking scheme to improve parallelism.
* **Ported** – Merged updates from versions 1.6.18 – 1.6.20.

### 1.7.0-beta1  (v1.7.0-beta1)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.0-beta1>

### Release Notes

This is a preview of the next release that contains important changes in a lot of subsystems. A completely new background processing engine introduced with support for both synchronous and asynchronous processes while using the same model. While processing is still not asynchronous, because storage methods aren't, it's a great step forward.

After dealing with a lot of daylight saving time transition issues, we've decided to build a completely new library to work with cron expression. So the [Cronos project](https://github.com/HangfireIO/Cronos) was born contains first-class support for time zones and knows about all the subtleties.

And last but not least, it contains major upgrades to the Hangfire.SqlServer package with the new optimized schema with much fewer indexes, and identity columns upgraded to the `bigint` type for those, who processed 2,147,483,647 background jobs.

**Hangfire.Core**

* **Added** – Entry point for custom job naming strategies available for dashboard (PR #660 by @pieceofsummer).
* **Added** – `JobDisplayNameAttribute` class for displaying jobs in dashboard, available on .NET Core (PR #993 by @pieceofsummer).
* **Added** – Support async jobs returning `ValueTask<T>` and other `await`-compatible types (PR #974 by @pieceofsummer).
* **Added** – Support for asynchronous background processes, opens the road toward async storage (PR #1082, #150).
* **Added** – Circuit breaker pattern for background processes to reduce the logging pressure (PR #1082).
* **Added** – Processing server is now able to detect it was expired, and restart itself with the new id (PR #1082).
* **Added** – Ability to use custom delays for automatic retries of a background job (PR #931).
* **Added** – `ThreadAbortException` and `ThreadInterruptedException` handling to keep the background process running (PR #1082).
* **Added** – Support for complex Cron expressions, including the `L`, `W`, `#` characters (PR #853, #494).
* **Added** – `JobActivator.BeginScope` method overload with the full PerformContext (PR #995 by @jeroenvervaeke, #828).
* **Added** – Support for read-only view for dashboard (PR #934 by @mikechamberlain, #423, #758).
* **Added** – Storage property to control the job expiration time (PR #913 by @rsilvanet).
* **Changed** – Decrease the size of serialized payloads and remove version information (PR #891).
* **Fixed** – Server disappears from the list, but still performing the background processing (#796, #1123).
* **Fixed** – Logging is too aggressive on transient errors (#542).
* **Fixed** – Daylight saving time transitions now handled perfectly in recurring jobs thanks to Cronos (#567).
* **Fixed** – Confusing Cron scheduling, when both day-of-week and day-of-month fields set (#979).

**Hangfire.SqlServer**

* **Added** – Callback method to allow to open the database with impersonation (PR #907 by @BjoernHund).
* **Changed** – Identity columns either converted to the `bigint` type, or entirely removed (PR #898).
* **Changed** – Clustered indexes were organized according to the access patterns of their tables (PR #898).
* **Changed** – Most of secondary indexes were either removed or made filtered (PR #898).
* **Fixed** – Background processing stops when identity columns exceed the `Int32.MaxValue` (#749).
* **Fixed** – Slowdown of scheduled jobs due to the missing index on the `Set` table (#844).

### 1.6.30  (v1.6.30)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.6.30>

### Release Notes

**Hangfire.Core**

Backported from 1.7.19:
* **Fixed** – Race condition in `AspNetShutdownDetector` leads to `NullReferenceException` (by @jr01).

**Hangfire.SqlServer**

Backported from 1.7.21:
* **Fixed** – Ensure connection is released when exception is thrown when during lock release.
* **Fixed** – "A network-related or instance-specific error" when using `DisableConcurrentExecution` for long-running jobs.

### 1.6.29  (v1.6.29)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.6.29>

### Release Notes

**Hangfire.Core**

* **Added** – Add built-in support for reliable shutdown detection of ASP.NET apps.
* **Changed** – Internal feature to perform state changes without calling any filters.
* **Fixed** – Let workers to ignore any state change filters when all previous attempts to call them failed.
* **Fixed** – Don't let `DelayedJobScheduler` to stall the pipeline when state filters throw an exception.
* **Fixed** – `JobLoadException` when new methods deployed, caused by overlapped recycles in ASP.NET applications.
* **Fixed** – Configuration changes aren't taken into account, caused by overlapped recycles in ASP.NET.
* **Fixed** – Zombie servers shown on the "Servers" page that aren't stopped automatically unless app pool is recycled.
* **Fixed** – Add another check before removing non-existing jobs from delayed jobs to avoid race conditions.

### 1.6.28  (v1.6.28)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.6.28>

### Release Notes

**Hangfire.Core** (backported from 1.7)

* **Fixed** – `CultureInfo.InvariantCulture` is now restored properly in background jobs.
* **Fixed** – Use `LazyThreadSafetyMode.PublicationOnly` to avoid caching "JobStorage.Current is null" exceptions.

**Hangfire.SqlServer** (backported from 1.7)

* **Fixed** – Don't leak a `DbConnection` instance when an exception occurs while trying to open it.

### 1.6.27  (v1.6.27)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.6.27>

### Release Notes

This maintenance release contains some fixes for the Hangfire.SqlServer package, backported from recent 1.7.X versions.

**Hangfire.SqlServer**

* **Fixed** – Cannot resolve the collation conflict in `CountersAggregator` (#852).
* **Fixed** – Set `SqlParameter` types explicitly to not to duplicate query plans and and avoid conversion issues.

### 1.6.26  (v1.6.26)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.6.26>

### Release Notes

This version contains **security fixes** to prevent possible XSS attacks as described in #1441. They don't relate to user data submitted to Hangfire directly via method arguments, but it's recommended to upgrade anyway. If you are using Hangfire 1.7, please upgrade to version [1.7.3](https://github.com/HangfireIO/Hangfire/releases/tag/v1.7.3) instead.

<dl>
<dt>Affected Packages</dt><dd>Hangfire.Core &le; 1.6.25, 1.7.0, 1.7.1, 1.7.2</dd>
<dt>Affected Platforms</dt><dd>All, including .NET Core, .NET Framework, Mono of any version</dd>
</dl>

**Steps to reproduce**

```csharp
public static void Xss()
{
    BackgroundJob.Enqueue(() => Xss2());
}

public static void Xss2()
{
    throw new Exception("<script>alert(1);</script>");
}
```

**Hangfire.Core**

* **SECURITY** – Use `HtmlEncode` in all remaining places in Dashboard UI to prevent XSS attacks.

### 1.6.25  (v1.6.25)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.6.25>

### Release Notes

**Hangfire.Core**

* **Fixed** – Buggy `CancellationToken` consumers now can't cause memory leaks related to token registrations.

### 1.6.24  (v1.6.24)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.6.24>

### Release Notes

**Hangfire.Core**

* **Fixed** – `PreserveCulture` filter logs a message instead of throwing an error when it can't find the culture.
* **Fixed** – Uninitialized continuation shouldn't cause exception when completing an antecedent job.

**Hangfire.SqlServer**

* **Fixed** – Validate `JobExpirationCheckInterval` option to avoid exceptions in runtime (PR #1377 by @carlowahlstedt).
* **Fixed** – Don't throw an exception, when current schema version is higher than expected.

### 1.6.23  (v1.6.23)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.6.23>

### Release Notes

**Hangfire.Core**

* **Added** – Slow log to see warning messages when filters or queries take more than 1 minute.
* **Fixed** – Catching `DistributedLockTimeoutException` based on resource name in schedulers (PR #1370 by @bogdandanielb).
* **Fixed** – Serilog context property name does not follow Serilog convention (PR #1360 by @pobiega).
* **Fixed** – Add more guards against `NullReferenceException` on Recurring Jobs page.
* **Fixed** – Don't handle recurring jobs created by newer version of Hangfire.

**Hangfire.AspNetCore**

* **Fixed** – Could not load type `Microsoft.***.FormattedLogValues` in ASP.NET Core 3.0.

**Hangfire.SqlServer**

* **Fixed** – Make `GetRangeFromSet` to be forward compatible with the 1.7.0 schema.
* **Fixed** – Changed some SQL queries to not to cause index scans when using 1.7.0 schema.

### 1.6.22  (v1.6.22)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.6.22>

### Release Notes

**Hangfire.Core**

* **Added** – Ability to use custom type resolvers to modify the type de-serialization logic.
* **Fixed** – `JobLoadException` when processing jobs in .NET Framework, which were created in .NET Core.
* **Fixed** – `JobLoadException` when jobs reside in a signed assembly and a new version is deployed.
* **Fixed** – Don't produce extra logging message when there's an exception in a worker (#1304).
* **Fixed** – Ensure form values are properly returned when there are different versions of Microsoft.Owin (#1329 by @DC-jc, #1324).
* **Fixed** – Dashboard fails with 404 "Not Found" error if there's a trailing slash for some reason (#1086).

**Hangfire.SqlServer**

* **Added** – Connection factory overload for the `SqlServerStorage` class (#1325 by @chinwobble).
* **Fixed** – Inability to use package with Azure's managed service identity (by using a connection factory, #1323).

### 1.6.21  (v1.6.21)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.6.21>

### Release Notes

This is a maintenance release with minor changes. 

**Hangfire.Core**

* **Fixed** – High CPU usage and long response time when accessing Failed jobs page with Linux stack traces.
* **Fixed** – `RecurringJobScheduler` may block server shutdown and cause distributed lock to be abandoned.

**Hangfire.SqlServer**

* **Fixed** – Change locking scheme in the `Connection.SetRangeInHash` method to avoid deadlocks.

**Hangfire.AspNetCore**

* **Fixed** – Null-based implementation of the `IAntiforgery` interface doesn't lead to an exception.

### 1.6.20  (v1.6.20)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.6.20>

### Release Notes

This release **contains fixes for security issues** related to dashboard, so it is highly recommended to upgrade. [Cross-Site Request Forgery](https://www.owasp.org/index.php/Cross-Site_Request_Forgery_(CSRF)_Prevention_Cheat_Sheet) protection was added by using existing libraries, but methods are different across application frameworks:

* For ASP.NET Core, no additional configuration is required, since [`Microsoft.AspNetCore.Antiforgery`](https://www.nuget.org/packages/Microsoft.AspNetCore.Antiforgery/) package is used to generate and validate tokens. Dependency injection is used to obtain the implementation and apply it when available.
* For other frameworks, additional configuration is required based on an abstract `IOwinDashboardAntiforgery` interface, because the available implementation is tightly coupled with the `System.Web.Helpers` assembly. Please check [this gist](https://gist.github.com/odinserj/4d3e3c5fbcc6c3dc83488a5738591ad1) to learn how to enable antiforgery token validation on ASP.NET and ASP.NET MVC platforms.

Other important updates include a new retry implementation for state changes in the `Worker` class to avoid any reads and writes whenever it is possible for a job's distributed lock to be abandoned, because it may lead to consistency issues.  Transitions directly to the Failed state without applying the job filters were also disabled, because such a behavior is not a determined one.

Also, looks like waiting on `CancellationToken.WaitHandle` rarely leads to high CPU usage. I was unable to reveal the exact reason for this, but any other implementation, including using `Task.Delay` or own tandem of `CancellationToken.Register` with `ManualResetEvent` works fine without such issues.

**Hangfire.Core**

* **SECURITY** – Add "robots" meta tag to ensure browser don't index dashboard pages.
* **SECURITY** – Add support for antiforgery validation to prevent CSRF attacks (requires configuration).

* **Fixed** – Perform state change retries using a fresh connection when job's distributed lock may be abandoned
* **Fixed** – Disallow transitions to the Failed state on retries that bypass all the filters
* **Fixed** – Remove possible rare CPU spikes due to the use of `CancellationToken.WaitHandle`
* **Fixed** – Avoid resolving types and methods for logging in static constructors that may lead to process shutdown
* **Fixed** – Prevent Recurring jobs dashboard from throwing `NullReferenceException` (#1203 by @mattkwiecien)
* **Fixed** – Replace wall clocks with monotonic ones when calculating local timeouts
* **Fixed** – Change logger initialization to be deterministic and predictable by using instance fields
* **Fixed** – Make `_currentLogProvider` field access to use volatile reads/writes
* **Fixed** – Typo in `NotSupportedException`'s message (#1210 by @benrick)
* **Fixed** – Typo on the Failed jobs page (#1207 by @gareth-evans)

**Hangfire.SqlServer**

* **Fixed** – Remove the synthetic limitation to support Azure SQL Management instance (#1222, #1230 by @TimSQL)

**Hangfire.AspNetCore**

* **SECURITY** – Use ASP.NET Core's built-in antiforgery validation to prevent CSRF attacks

### 1.6.19  (v1.6.19)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.6.19>

### Release Notes

**Hangfire.Core**

* **Fixed** – `NullReferenceException` in `JobMethodCallRenderer` regression appeared in 1.6.18.

**Hangfire.SqlServer**

* **Fixed** – "String or binary data would be truncated" exception when state reason is too long.
* **Fixed** – Command handling in batch mode now stops after the first error due to "XACT_ABORT ON".
* **Fixed** – Make `SqlCommandBatch` disposable to dispose all the commands.

### 1.6.18  (v1.6.18)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.6.18>

### Release Notes

This release contains a lot of fixes, but the most important ones are related to .NET Core and ASP.NET Core frameworks. Filters based on attributes are now working fine there, and `DisplayName` decoration will finally bring the human-ready name for your jobs. Other fixes are mostly related to dashboard.

**Hangfire.Core**

* **Added** – Add on option to remove the storage connection string from the footer (PR #1079 by @sandorfr).
* **Added** – Add Dashboard UI Resource zh-TW (PR #1105 by @crablin).
* **Fixed** – OutOfMemoryException in dashboard when arguments are too big (#1051, PR #1153).
* **Fixed** – DisplayNameAttribute doesn't work when using dashboard in .NET Core (PR #1154).
* **Fixed** – Update rickshaw css to match the js version (PR #1018 by @pieceofsummer).
* **Fixed** – Bad exception when Job.FromExpression fails to resolve method for explicit interface implementations (#1050, PR #1056 by @f00).
* **Fixed** – Missing intValue-values in "/stats" endpoint (PR #1152 by @pieceofsummer).
* **Fixed** – Logging doesn't work with log4net integration in .NET Core (#1095, PR #1134 by @evollu).
* **Fixed** – Fix nuspec pointing to version of Newtonsoft.Json that does not exist (#947, #973, PR #1083 by @mvestergaard)
* **Fixed** – Server start time has a bad tooltip position (PR #1029 by @pieceofsummer).
* **Fixed** – Prevent connection string from blowing mobile page layout (PR #1030 by @pieceofsummer).
* **Fixed** – Number of recurring jobs per page is now correct (PR #1006 by @pieceofsummer).
* **Project** – Get rid of all the compile-time warnings (PR #1058 by @liakamp).
* **Project** – More details for build instructions for the project (PR #1055 by @kristofferjalen).
* **Project** – Unable to build project with space in folder path (#809, PR #1057 by @stefanviberg).

**Hangfire.AspNetCore**

* **Added** – More Hangfire-related services are now registered in an IoC container (PR #800 by @pieceofsummer).
* **Fixed** – Queue parameter is ignored in .NET Core when creating a job (#799, PR #800 by @pieceofsummer).
* **Fixed** – Fix issue with configuration block not called on .NET Core (PR #800 by @pieceofsummer).

**Hangfire.SqlServer**

* **Fixed** – Rare deadlocks in SQL Server caused by the SetRangeInHash command (#1124, PR #1139).

### 1.6.17  (v1.6.17)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.6.17>

### Release Notes

**Hangfire.SqlServer**

* **Added** – `SqlServerStorageOptions.CommandBatchMaxTimeout` parameter to enable batching in transactions.
* **Fixed** – Timeout exceptions when there are a lot of large concurrent transactions by using the new batching method.
* **Fixed** – Distributed locks are safe now even in very unreliable networks and after network blips.
* **Performance** – Greatly decreased the number of connections required to process background jobs.
* **Performance** – Significantly decrease the number of roundtrips required to commit a transaction.

### 1.6.16  (v1.6.16)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.6.16>

### Release Notes

This is yet another maintenance release that fixes a bunch of non-critical bugs in `Hangfire.Core` and `Hangfire.SqlServer` packages.

**Hangfire.Core**

* **Fixed** – Unexpected `DateTime` and `DateTime?` serialization issues in background job arguments (#971 by @plaisted, #970, #972).
* **Fixed** – `DistributedLockTimeoutException` in some background processes now logged with "DEBUG" level instead of "ERROR" (#789).
* **Fixed** – `ElmahLogProvider` to show errors when using SQL log (#867 by @francnuec).
* **Fixed** – Last execution field isn't shown on recurring jobs page, when background job has already expired (#930).
* **Fixed** – `Hangfire.SqlServer` assembly doesn't include version in the `netstandard` target (#951).

**Hangfire.SqlServer**

* **Fixed** – Lower the number of requests, when trying to acquire a distributed lock.
* **Fixed** – Problems with continuations and batch continuations, when using existing `SqlConnection` instance.
* **Fixed** – Distributed locks were silently released, when passing explicit closed connection to a storage.
* **Fixed** – `KeyNotFoundException` errors on various dashboard pages don't appear anymore (#948 by @benjymous, #945, #946).
* **Fixed** – "Cannot release the application lock because it is not currently held" exceptions, when connection was closed.
* **Fixed** – Allow to use zero timeout for SQL Server-based distributed locks (#967).

### 1.6.15  (v1.6.15)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.6.15>

### Release Notes

This release contains important fixes for the Hangfire.SqlServer package, which is actively using the [`sp_getapplock`](https://docs.microsoft.com/en-us/sql/relational-databases/system-stored-procedures/sp-getapplock-transact-sql) stored procedure to synchronize work between different servers. I've realized that locks shouldn't be awaited on SQL Server's side, because this may lead to SQL Server's connection pool starvation, because each blocked request will block a single worker thread. 

When you are using a lot of workers, and there's a contention on few lock resources (like when using the `DisableConcurrentExecutionAttribute`, batches or many continuations on a single job), all worker threads can be blocked in SQL Server, causing its unresponsiveness and lead to huge amount of timeout exceptions.

**Hangfire.SqlServer**

* **Fixed** – Timeout exceptions that's caused by SQL Server's thread pool starvation, caused by `sp_getapplock`&nbsp;(fbe756ee71ccb6bd20ee9f9167981d4574c773d4).
* **Fixed** – Antecedent background job is constantly failing, when its continuation hasn't been fully created&nbsp;(8bece534517cd5cdfea35f49eb1b046e14d1f16e).

### 1.6.14  (v1.6.14)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.6.14>

### Release Notes

This versions adds possibility to use non-transactional message fetching algorithm when using Hangfire.SqlServer package. This is especially helpful, if you have a lot of long-running background jobs, since they may prevent you from taking transaction log backups, leading to the *Transaction log is full due to 'ACTIVE_TRANSACTION'* error.

The new implementation is based on the old invisibility timeout, but workers are now periodically renewing that timeout, so you can forget about setting too high timeout just to allow your long-running background jobs to run smoothly. Non-transactional fetch is not enabled by default in this version (and will not be in 1.7.0 to preserve backward compatibility), to configure it please use the `SlidingInvisibilityTimeout` option as written below.

Lower values will stress your database (for example, if it is set to 5 minutes, each worker will run a keep-alive query each minute when processing a job), higher values will add a corresponding delay, when processing is terminated ungracefully.

```csharp
GlobalConfiguration.Configuration.UseSqlServerStorage(
    "connection_string", 
    new SqlServerStorageOptions { SlidingInvisibilityTimeout = TimeSpan.FromMinutes(5) });
```

**Hangfire.SqlServer**

* **Added** – `SqlServerStorageOptions.SlidingInvisibilityTimeout` to fetch jobs without using transaction.
* **Fixed** – Transaction log is full due to 'ACTIVE_TRANSACTION' by allowing to use new non-transactional fetch (when using `SlidingInvisibilityTimeout` option).
* **Fixed** – `SqlServerJobQueueMonitoringApi` can't cause READ UNCOMMITTED isolation level to leak on SQL Server 2012 or earlier. 
* **Fixed** – Add missing `SqlServerStorage(DbConnection, SqlServerStorageOptions)` constructor.

### 1.6.13  (v1.6.13)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.6.13>

### Release Notes

This release contains a bunch of fixes for core and integration packages. The most important updates are fix for SQL connection leaks when we failed to acquire a distributed lock, and wrong queue selection, when continuation is created after antecedent job is finished. So upgrade is recommended.

**Hangfire.Core**

* **Fixed** – Continuation is fired on a wrong queue, when parent job is finished before the creation.
* **Fixed** – Impossible to intercept failed state transition before `AutomaticRetryAttribute`.
* **Fixed** – Fixed translation in Chinese localization on home page (by @JustinChia).
* **Fixed** – Don't throw `NullReferenceException`, when state has changed during query on Processing page.
* **Fixed** – `CreateBatchFailedException`, when batch creation takes longer than 1 hour.

**Hangfire.AspNetCore**

* **Fixed** – Types are resolved using the `GetServiceOrCreateInstance` method (by @Tsabo).

**Hangfire.SqlServer**

* **Fixed** – `SqlServerDistributedLock` leaks connections, when lock acquisition is failed.
* **Fixed** – Don't hide errors occurred while running SQL migrations.
* **Fixed** – `KeyNotFoundException` when accessing Deleted Jobs page in Dashboard.

### 1.6.12  (v1.6.12)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.6.12>

### Release Notes

This release brings better exception handling policy for state changing pipeline. Previously, non-transient exception in a state filter could cause a worker to perform retries for affected background job infinitely. And a large number of such background jobs could stall the processing.

The new logic makes 10 attempts to perform a state change using state filters. When all the attempts failed, it moves background job to the Failed state without calling any state filters.

**Hangfire.Core**

* **Fixed** – Buggy state filters may cause background job to be infinitely retried.
* **Fixed** – Transient exception during Processing-Succeeded state transition may cause unexpected retry.

### 1.6.11  (v1.6.11)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.6.11>

This release fixes a problem with CSS and JS files in dashboard appeared in 1.6.10, as well as corrects the authorization behavior, when the `User` property is `null`.

**Hangfire.Core**

* **Fixed** – `NullReferenceException` in dashboard when OWIN's or ASP.NET Core's `User` is `null`.
* **Fixed** – Bug related to missing CSS and JS resources in dashboard appeared in [1.6.10](https://github.com/HangfireIO/Hangfire/releases/tag/v1.6.10).

### 1.6.10  (v1.6.10)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.6.10>

This is a maintenance release that contains fixes for job continuations and some dashboard issues related to Content Security Policy and recurring jobs page. It's highly recommended to upgrade to prevent problems with continuations. They are rare, but lead to significant headache.

**Hangfire.Core**

* **Fixed** – Duplicate job continuations aren't added anymore, when outer transaction has failed.
* **Fixed** – Existing duplicate continuations don't lead to `ArgumentException`: the same key already added.
* **Fixed** – Replace inline script, because it may violate the Content Security Policy (by @Beczka).
* **Fixed** – Don't skip records in RecurringJobsPage (by @reaction1989).

### 1.6.9  (v1.6.9)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.6.9>

### Release Notes

This is a small correcting release that make it possible to have a workaround for `TimeoutException` exceptions when using **SQL Server** with huge arguments or batches. The `SqlServerOptions.CommandTimeout` option was added to allow to override the default timeout of 30 seconds.

**Fixed** – `TimeoutException` on large arguments or large batches via `SqlServerOptions.CommandTimeout`.

### 1.6.8  (v1.6.8)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.6.8>

### Release Notes

This release contains a bunch of minor fixes, mostly for Dashboard UI.

**Hangfire.Core**
- **Fixed** – `Cron.MonthInterval` now returns correct CRON expression.
- **Fixed** – Throw `NotSupportedException` early, when arguments contain delegate or expression.
- **Fixed** – Connection and distributed lock kept longer than necessary in `RecurringJobScheduler`.
- **Fixed** – Use local date/times everywhere in Dashboard UI (#702, #761).
- **Fixed** – Call chart update only when it exists in Dashboard UI to prevent JavaScript errors (#745).
- **Fixed** – Scheduled column title is now displaying correctly in Dashboard UI (#765).
- **Fixed** – Typo "Nexts jobs" should be "Next jobs" in Dashboard UI (#754 by @danielabbatt).

**Hangfire.SqlServer**
- **Fixed** – Use `long` where possible instead of `int` for background job identifiers, full support will be in 1.7.0 (#749).

### 1.6.7  (v1.6.7)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.6.7>

### Release Notes

This is a correcting release that brings fixes to fully support generic methods, whose generic arguments are defined in their parameters, including `List<T>` and `T[]`. A lot of issues with Dashboard UI that cause exceptions and other errors, like uncontrolled growth of event listeners on resize, were also fixed. Please see the full delails below.

**Hangfire.Core**
- **Fixed** – `ArgumentException` when using complex arguments in generic methods like `IList<T>` (#719 by @aidmsu).
- **Fixed** – Generic arrays like `T[]` aren't supported in background job arguments (#740 by @aidmsu).
- **Fixed** – Wrong choice of the overload when multiple methods match the given arguments (#713 by @aidmsu).
- **Fixed** – Null values for arguments when there are errors during the JSON deserialization (#731).
- **Fixed** – Window resize cause errors and uncontrolled growth of event and poll listeners (#711 by @Yarmonov).
- **Fixed** – `HtmlHelper.ToHumanDuration` incorrectly formats fractional seconds (#708 by @pieceofsummer).
- **Fixed** – Dashboard UI shows wrong description for CRON that contain trailing spaces (#727, #729 by @aidmsu).
- **Fixed** – Exception in Dashboard UI when CRON expression is null by an accident (#692, #730 by @aidmsu).
- **Fixed** – Error in Dashboard UI when rendering an array that contains a null element (#734, #741 by @djfoz).
- **Fixed** – Inconsistent constructors' accessibility for different context classes (#703, #710 by @pieceofsummer).
- **Fixed** – Decrease the max default workers count to "20" in tests (#701 by @patrykpiotrmarek).
- **Fixed** – Inconsistent EOL characters in some files of a project (#721 by @aidmsu).
- **Fixed** – Make Queue name accessible from `RecurringJobDto` (#737 by @swordfish6975).

**Hangfire.SqlServer**
- **Fixed** – Validation added to avoid "An invalid application lock time-out" exceptions (#686 by @t0mburton).

**Hangfire.AspNetCore**
- **Fixed** – Parameterless `AspNetCoreJobActivator.BeginScope` method now returns a correct instance (#706, #709 by @pieceofsummer).

### 1.6.6  (v1.6.6)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.6.6>

### Release Notes

This is a correcting release that fixes a regression, when using generic methods of a scoped variable in expression when creating a background job, as well as some minor optimizations for SQL Server. It also adds CLS compliance for basic packages, since public API is already compliant.

**Hangfire.Core**
- **Fixed** – `Hangfire.Core`, `Hangfire.SqlServer` and `Hangfire.SqlServer.Msmq` marked as CLS-compliant.
- **Fixed** – Generic methods cause `ArgumentNullException` when scoped variable is used in expression.

**Hangfire.SqlServer**
- **Fixed** – `SqlServerJobQueue` class doesn't use obsolete `InvisibilityTimeout` parameter anymore.

### 1.6.5  (v1.6.5)
<https://github.com/HangfireIO/Hangfire/releases/tag/v1.6.5>

### Release Notes

This correcting release contains a **lot of stability improvements** for Hangfire.SqlServer, especially for SQL Azure Database environments. Processing is now more predictable even in Basic pricing tier, there is a special harness application that's running 24/7 to ensure everything is fine. Some problems related to I18N, authorisation and continuations were also fixed.

**Hangfire.Core**
- **Added** – Chinese language to Dashboard UI (#653 by @andy-zhouyou).
- **Changed** – Default upper limit of worker number is 20.
- **Changed** – Default value for DashboardJobListLimit is now 10000.
- **Fixed** – Deserialization exception in continuations, when `TypeNameHandling.All` option is used (#666, #674 by @MaksimSimkin).
- **Fixed** – I18N is not working, because there are no localized resources in NuGet packages (#668).
- **Fixed** – Infinite redirect loops, when authenticated, but not authorized user accesses Dashboard UI (#638).
- **Fixed** – "The type ... exists in both..." issue when building Hangfire, related to `Newtonsoft.Json`.
- **Fixed** – Use the given type's method, when scope variable is passed to a job expression (#656).
- **Fixed** – Very rare resource leaks detected by Coverity Scan.

**Hangfire.SqlServer**
- **Fixed** – Different timeout issues after making performance optimisations (#489, #515, #628, #643).
- **Fixed** – SQL timeouts while getting a connection, when using default settings and &ge; 8 CPU cores.
- **Fixed** – `ExpirationManager` is bloated by `SqlError` instances, when there are a lot of messages from server.
- **Fixed** – Counters query returned inconsistent results during `CountersAggregator` executions.
- **Performance** – Added missing `NOLOCK` hint for monitoring queries when using SqlServer-based queues.
- **Performance** – `ExpirationManager` is forced to use index seek operations for cascade deletions.
- **Performance** – `CountersAggregator` now uses clustered index scan to issue less logical reads.
- **Performance** – Paging queries in dashboard now use CTEs to utilize less logical reads.
