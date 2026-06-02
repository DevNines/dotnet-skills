# FastEndpoints — release notes by major

_Generated from `https://github.com/FastEndpoints/FastEndpoints/releases`. Use when answering migration questions or when a user asks what changed between versions._

## v8.x

### v8.1 Release  (v8.1)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v8.1>

---

## ⚠️ Sponsorship Level Critically Low ⚠️

Due to low financial backing by the community, FastEndpoints will soon be going into "Bugfix Only" mode until the situation improves. Please [join the discussion here](https://github.com/FastEndpoints/FastEndpoints/issues/1042) and help out if you can.

---

[//]: # (<details><summary>title text</summary></details>)

## New 🎉

<details><summary>Dual mode testing support for 'AppFixture'</summary>

You can now use the same app fixture (without any conditional code in your tests) to run WAF based tests during regular development, and run smoke tests against a native aot build during a CI/CD pipeline run by simply doing `dotnet test MyTestProject.csproj -p:NativeAotTestMode=true` in the pipeline. This way you are able to have a faster feedback loop during development and also verify that everything works the same once the app is built with native aot by running the same set of tests against the aot build without any special handling in your code. See the documentation [here](https://fast-endpoints.com/docs/native-aot#testing-native-aot-builds).

</details>

<details><summary>Fluent generics support for serializer context generator</summary>

The STJ serializer context generator now supports endpoints defined with [fluent generics](https://fast-endpoints.com/docs/get-started#fluent-generics).

</details>

<details><summary>Referenced project + Nuget package support for the serializer context generator</summary>

The generated serializer context will now have `JsonSerializable` attributes for request and response DTOs from referenced source projects as well as Nuget packages. Previously the generator was only capable of generating attributes for DTOs from the current project directory.

</details>

<details><summary>Ability to configure a pre-determined list of "known subscribers" for remote event queues</summary>

Remote event subscribers can now supply an explicit `subscriberID` instead of relying on the auto generated client identity, and event hubs can be configured with a known list of subscriber IDs to begin queuing events for them from app startup onward. Known subscriber pre-seeding does not affect round-robin mode, which still delivers only to currently connected subscribers.

</details>

## Fixes 🪲

<details><summary>Stack overflow issue with .NET 8 and 9</summary>

A stack overflow exception was being thrown in .NET 8/9 due to cyclical calls in TypeInfoResolver, which .NET 10 has solved. We've added a workaround to prevent this from happening.

</details>

<details><summary>Serializer context generator was skipping collection DTO types</summary>

The serializer context generator tool was not creating `JsonSerializable` attributes for request and response DTO types if they were collection types such as `List<Request>`, `IEnumerable<Response>`, etc.

</details>

<details><summary>Job queue storage provider query translation issue</summary>

The job queue search predicate has been improved to allow EF Core (and potentially other ORMs) to translate the expression correctly when the storage provider is configured in non-distributed mode. Previously, an unmapped `DequeueAfter` property was included in the expression causing EF Core translation errors.

</details>

<details><summary>Regression in OData library</summary>

Due to recent changes in FastEndpoints v8, the OData library stopped producing results. This has now been fixed, and comprehensive tests added to prevent a reoccurrence.

</details>

## Improvements 🚀

<details><summary>Prune stale remote event hub subscribers after 24 hours</summary>

Remote event hubs now stop creating event records for disconnected subscribers that have not been seen for 24 hours. This keeps temporarily disconnected subscribers eligible to receive queued events when they reconnect, while preventing dead subscribers from accumulating new records indefinitely.

</details>

<details><summary>Remote event queue persistence retry handling</summary>

The publisher event hub and remote event subscriber now retry only the actual event storage operations and perform their semaphore wake-up signaling separately. This avoids re-persisting already stored event records if the post-store notification step fails.

</details>

<details><summary>Optimize serializer context generator</summary>

The serializer context generator has been improved to use less resources and do the generation in a more efficient and faster manner.

</details>

<details><summary>Custom value parser registration internals</summary>

v8 matches custom value parsers by the underlying type (due to native aot intricacies) and if a user would register the parser with the nullable type, it would not match. This has been solved by always registering the underlying type even if the user supplies a nullable type.

</details>

<details><summary>Job queue executor refilling and shutdown behavior</summary>

Job queue executors now refill newly freed concurrency slots immediately instead of waiting for the whole fetched batch to finish. During shutdown, the executor also drains already running jobs before exiting, and distributed storage providers only claim as many jobs as there are currently available execution slots.

</details>

<details><summary>Remote event queue executor refilling with stable event record IDs</summary>

Remote event storage records now carry a library generated `TrackingID`, which allows event subscribers to refill newly freed execution slots immediately without re-scheduling the same in-flight durable record. This improves concurrency utilization for persistent remote event queues, especially when a slow handler would otherwise hold up the next batch.

</details>

## Minor Breaking Changes ⚠️

<details><summary>Remote event storage records now require a TrackingID</summary>

The `IEventStorageRecord` contract now includes a `Guid Tr

_…truncated…_

### v8.0.1 Release  (v8.0.1)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v8.0.1>

---

## ⚠️ Sponsorship Level Critically Low ⚠️

Due to low financial backing by the community, FastEndpoints will soon be going into "Bugfix Only" mode until the situation improves. Please [join the discussion here](https://github.com/FastEndpoints/FastEndpoints/issues/1042) and help out if you can.

---

[//]: # (<details><summary>title text</summary></details>)

## New 🎉

<details><summary>Support for Native AOT compilation</summary>

FastEndpoints is now Native AOT compatible. Please see the [documentation here](https://fast-endpoints.com/docs/native-aot) on how to configure it.

If you'd like to jump in head first, a fresh AOT primed starter project can be scaffolded like so:

```sh
dotnet new install FastEndpoints.TemplatePack
dotnet new feaot -n MyProject
```

If you've not worked with AOT compilation in .NET before, it's highly recommended to read the docs linked above.

</details>

<details><summary>Auto generate STJ JsonSerializationContexts</summary>

You no longer need to ever see a `JsonSerializerContext` thanks to the new serializer context generator in FastEndpoints. (Unless you want to that is 😉). See the documentation [here](https://fast-endpoints.com/docs/model-binding#auto-generate-stj-serializer-contexts) on how to enable it for non-AOT projects.

</details>

<details><summary>Distributed job processing support</summary>

The job queueing functionality now has support for distributed workers that connect to the same underlying database. See the documentation [here](https://fast-endpoints.com/docs/job-queues#distributed-job-processing).

</details>

<details><summary>Qualify endpoints in global configurator according to endpoint level metadata</summary>

You can now register any object as metadata at the endpoint level like so:

```csharp
sealed class SomeObject
{
    public int Id { get; set; }
    public bool Yes { get; set; }
}

sealed class MetaDataRegistrationEndpoint : EndpointWithoutRequest
{
    public override void Configure()
    {
        Get("/test-cases/endpoint-metadata-reg-test");
        Metadata(
            new SomeObject { Id = 1, Yes = true },
            new SomeObject { Id = 2, Yes = false });
    }
}
```

and configure endpoints conditionally at startup according to the endpoint level metadata that was added by the endpoint configure method:

```csharp
app.UseFastEndpoints(
       c => c.Endpoints.Configurator =
                ep =>
                {
                    if (ep.EndpointMetadata?.OfType<SomeObject>().Any(s => s.Yes) is true)
                        ep.AllowAnonymous();
                })
```

</details>

<details><summary>Response sending method 'NotModifiedAsync'</summary>

A new response sending method has been added for sending a 304 status code response.

```csharp
public override async Task HandleAsync(CancellationToken c)
{
    await Send.NotModifiedAsync();
}
```

</details>

## Fixes 🪲

<details><summary>Index out of range exception in routeless test helpers</summary>

The routeless integration test helpers such as `.GETAsync<>()` would throw an exception when testing an endpoint configured with the root URL `/`, which has now been fixed.

</details>

<details><summary>Query/Route param culture mismatch with routeless test helpers and backend</summary>

The routeless test helpers such as `.GETAsync<>()` would construct route/query params (of certain primitives such as `DateTime`) using the culture of the machine where the tests are being run, while the application is set up to use a different culture, the tests would fail. This has been solved by constructing route/query params for primitive/`IFormattable` types using ISO compliant invariant culture format when constructing the requests.

</details>

<details><summary>Routeless testing helpers contention issue</summary>

The test helpers were using a regular dictionary to cache test URLs internally which could sometimes cause trouble under high load. This has been solved by switching to a concurrent dictionary.

</details>

<details><summary>Source generators having trouble with special characters in project names</summary>

The source generators were generating incorrect namespaces if the project name has dashes such as `My-Project.csproj` which would result in generating namespaces with dashes, which is invalid for C#.

</details>

<details><summary>Test collection ordering regression</summary>

Due to an internal behavior change in XUnit v3, test collection ordering was being overriden by XUnit. This has been rectified by taking matters in to our own hands and bypassing XUnit's collection runner.

</details>

## Improvements 🚀

<details><summary>Job Queues storage processing</summary>

Several optimizations have been done to the job queues storage logic to reduce the number of queries in certain scenarios. Please see the breaking changes section below as one of the methods of `IJobStorageProvider` needs a minor change.

</details>

<details><summary>Easy access to error response content with testing helpers</summary>

You can now easily inspect why a request failed when you expected it to succeed. There's now a new string property `ErrorContent` on the `TestResult` record that routeless testing helpers return.

```csharp
[Fact]
public async Task Get_Request_Responds_With_200_Ok()
{
    var (rsp, res, errorContent) = await app.Client.GETAsync<MyEndpoint, MyRequest, string>(new() { ... });

    if (rsp.IsSuccessStatusCode)
        Assert.True(...);
    else
        Assert.Fail(errorContent); //errorContent contains the error response body as a string
}
```

</details>

<details><summary>Request DTO serialization behavior of testing helpers</summary>

Testing helpers such as `.POSTAsync<>()` will only serialize the request DTO in to the request body if there's at least one property on the DTO that will be bound from the JSON b

_…truncated…_


## v7.x

### v7.2 Release  (v7.2)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v7.2>

---

## ⚠️ Sponsorship Level Critically Low ⚠️

Due to low financial backing by the community, FastEndpoints will soon be going into "Bugfix Only" mode until the situation improves. Please [join the discussion here](https://github.com/FastEndpoints/FastEndpoints/issues/1042) and help out if you can.

---

[//]: # (<details><summary>title text</summary></details>)

## New 🎉

<details><summary>Standalone package for Event/Command Bus functionality</summary>

The in-process Event Bus and Command Bus features have been liberated from the clutches of the FastEndpoints main library. A new, independent `FastEndpoints.Messaging` package has been created. This package can be used in any .NET 8+ application, even with Blazor WASM. Simply install the nuget package and register it with the IOC container like so:

```csharp
builder.Services.AddMessaging();
var host = builder.Build();
host.Services.UseMessaging();
```

There's no setup (nor code changes) needed for projects using FastEndpoints main library. The above is only for when you want to use the messaging functionality in projects that don't have FastEndpoints.

</details>

<details><summary>Standalone package for Job Queues functionality</summary>

The job queuing functionality has also been extracted out to a separate package `FastEndpoints.JobQueues` which can be used independently of the main FE library. No code changes are needed for existing FE projects.

</details>

<details><summary>Aspire Testing support for routeless test helpers</summary>

You can now use the routeless test helpers such as `.GETAsync<MyEndpoint>()` with Aspire `DistributedApplication` testing like so:

```csharp
[Fact]
public async Task Endpoint_Returns_Ok_Response()
{
    // Arrange
    var ct = TestContext.Current.CancellationToken;
    var appHost = await DistributedApplicationTestingBuilder.CreateAsync<Projects.AspireApp_AppHost>(ct);
    await using var app = await appHost.BuildAsync(ct).WaitAsync(_defaultTimeout, ct);
    await app.StartAsync(ct).WaitAsync(_defaultTimeout, ct);
    await app.ResourceNotifications.WaitForResourceHealthyAsync("apiservice", ct).WaitAsync(_defaultTimeout, ct);

    // Act
    var httpClient = app.CreateHttpClient("apiservice");
    var (response, _) = await httpClient.GETAsync<HelloEndpoint, EmptyResponse>();

    // Assert
    Assert.Equal(HttpStatusCode.OK, response.StatusCode);
}
```

</details>

<details><summary>'FastEndpoints.HealthChecks' package</summary>

An opt-in library that eliminates boilerplate health check wiring for apps running behind orchestrators such as Kubernetes/.NET Aspire. You can now use the following convenient extension method and it's overloads:

```csharp
// Defaults: 
// - /health/live (liveness)
// - /health/ready (readiness)
builder.Services.AddServiceHealthChecks();

// Custom paths
builder.Services.AddServiceHealthChecks(
    configureOptions: opts =>
    {
        opts.LivePath = "/alive";
        opts.ReadyPath = "/ready";
    });

// Add custom health checks
builder.Services.AddServiceHealthChecks(
    configureChecks: hc =>
    {
        hc.AddNpgSql(connectionString, name: "postgres");
        hc.AddRedis("localhost:6379", name: "redis");
    });
```

Liveness returns 200 if process is alive (no dependency checks). Readiness runs all registered health checks and returns aggregate status with optional JSON response.

</details>

<details><summary>Test/verify command executions in endpoints without mocks/fakes</summary>

In a similar fashion to the previously released [Test Event Receivers](https://gist.github.com/dj-nitehawk/ae85c63fefb1e8163fdd37ca6dcb7bfd) feature, you can now use [Test Command Receivers](https://gist.github.com/dj-nitehawk/abf3fd08bae544ee3bcafb5c5f487c4a) to verify that a certain command execution was initiated by an endpoint or service without having to register fake command handlers.

Typically, you'd unit test the command/handlers in isolation to verify the business logic in those handlers and use the "Test Event/Command Receivers" to validate that certain entrypoints in your application actually do trigger/issue particular commands and events.

</details>

## Improvements 🚀

<details><summary>Strong-Name-Signed Assemblies</summary>

All FastEndpoints assemblies are now strong-name-signed. This only matters if your project is utilizing assembly signing. Signed projects will no longer show warnings about FastEndpoints not being signed.

</details>

<details><summary>Increased frequency of stream flushing in SSE</summary>

SSE streams are now flushed after each write as opposed to after every batch. This eliminates random pauses on the client-side due to stream buffering.

</details>

<details><summary>Job storage performance optimization</summary>

Optimized the `JobQueue` startup initialization by reusing the results of the existing scheduled-jobs query to determine whether the queue is in use, allowing the system to skip the additional query for future scheduled jobs when current jobs are already present, thereby reducing database load and improving startup performance without changing observable behavior.

</details>

## Fixes 🪲

<details><summary>Group summary overriding endpoint level summary data</summary>

There was an oversight that resulted in endpoint level summary data being overwritten by group level summary data in situations such as the following:

```csharp
sealed class MyGroup : Group
{
    public MyGroup()
    {
        Configure("group", ep => ep.Summary(s => s.Description = "group level text"));
    }
}

sealed class MyEndpoint : EndpointWithoutRequest
{
    public override void Configure()
    {
        Get("/something");
        Group<MyGroup>();
        Summary(s => s.Description = "endpoint level text"); //this would get loss due to the bug
    }
}
```

</details>

<details><summary>Routeless test helpers

_…truncated…_

### v7.1.1 Release  (v7.1.1)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v7.1.1>

# .NET 10 Support

> We've had .NET 10 preview support for a while and this is just a patch release to update the SDK references to .NET 10 final.

[//]: # (---)

[//]: # ()

[//]: # (## ❇️ Help Keep FastEndpoints Free & Open-Source ❇️)

[//]: # ()

[//]: # (Due to the current [unfortunate state of FOSS]&#40;https://www.youtube.com/watch?v=H96Va36xbvo&#41;, please consider [becoming a sponsor]&#40;https://opencollective.com/fast-endpoints&#41; and help us beat the odds to keep the project alive and free for everyone.)

[//]: # ()

[//]: # (---)

[//]: # ()

[//]: # ([//]: # &#40;<details><summary>title text</summary></details>&#41;)

[//]: # ()

[//]: # (## New 🎉)

[//]: # ()

[//]: # (## Improvements 🚀)

[//]: # ()

[//]: # (## Fixes 🪲)

[//]: # ()

[//]: # (## Breaking Changes ⚠️)

### v7.1 Release  (v7.1)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v7.1>

---

## ❇️ Help Keep FastEndpoints Free & Open-Source ❇️

Due to the current [unfortunate state of FOSS](https://www.youtube.com/watch?v=H96Va36xbvo), please consider [becoming a sponsor](https://opencollective.com/fast-endpoints) and help us beat the odds to keep the project alive and free for everyone.

---

[//]: # (<details><summary>title text</summary></details>)

## New 🎉

<details><summary>Better conditional sending of responses</summary>

All **Send.\*Async()** methods now return a T**ask\<Void\>** result. If a response needs to be sent conditionally, you can simply change the return type of the handler from **Task** to **Task\<Void\>**  and return the awaited result as shown below in order to stop further execution of endpoint handler logic:

```csharp
public override async Task<Void> HandleAsync(CancellationToken c)
{
    if (id == 0)
        return await Send.NotFoundAsync();

    if (id == 1)
        return await Send.NoContentAsync();

    return await Send.OkAsync();
}
```

If there's no async work being done in the handler, the **Task\<Void\>** can simply be returned as well:

```csharp
public override Task<Void> HandleAsync(CancellationToken c)
{
    return Send.OkAsync();
}
```

</details>

<details><summary>Specify max request body size per endpoint</summary>

Instead of globally increasing the max request body size in Kestrel, you can now set a max body size per endpoint where necessary like so:

```csharp
public override void Configure()
{
    Post("/file-upload");
    AllowFileUploads();
    MaxRequestBodySize(50 * 1024 * 1024);
}
```

</details>

<details><summary>Customize error response builder func when using 'ProblemDetails'</summary>

You can now specify a custom response builder function when doing `.UseProblemDetails()` as shown below in case you have a special requirement to use a certain shape
for one or more of your endpoints while the rest of the endpoints use the standard response.

```csharp
app.UseFastEndpoints(
       c => c.Errors.UseProblemDetails(
           p =>
           {
               p.ResponseBuilder = (failures, ctx, statusCode) =>
                                   {
                                       if (ctx.Request.Path.StartsWithSegments("/group-name"))
                                       {
                                           // return any shape you want to be serialized
                                           return new
                                           {
                                               Errors = failures
                                           };
                                       }

                                       // anything else will use the standard problem details.
                                       return new ProblemDetails(failures, ctx.Request.Path, ctx.TraceIdentifier, statusCode);
                                   };
           }))
```

</details>

<details><summary>Use 'ProblemDetails.Detail' property for describing single error instances</summary>

The `FastEndpoints.ProblemDetails.Detail` property has been unused until now. It will now by default be populated according to the following `DetailTransformer` logic, which you can customize if needed. The transformer can also be set to `null` in case you'd like to go back to the previous behavior.

```csharp
app.UseFastEndpoints(
       c => c.Errors.UseProblemDetails(
           p =>
           {
               p.DetailTransformer = pd => pd.Errors.Count() == 1
                                               ? pd.Errors.First().Reason
                                               : null;
           }))
```

The default behavior is to populate the `Detail` property with the reason if there's only 1 error and not populate it at all in case there's more than 1 error.

</details>

<details><summary>Specify a request binder per group</summary>

It is now possible to register a particular open generic request binder such as the following:

```csharp
class MyBinder<TRequest> : RequestBinder<TRequest> where TRequest : notnull 
{ 
    public override async ValueTask<TRequest> BindAsync(BinderContext ctx, CancellationToken ct) 
    { 
        var req = await base.BindAsync(ctx, ct); // run the default binding logic
 
        if (req is MyRequest r) 
            r.SomeValue = Guid.NewGuid().ToString(); // do whatever you like
 
        return req; 
    } 
} 
```

only for a certain group configuration, so that only endpoints of that group will have the above custom binder associated with them.

```csharp
sealed class MyGroup : Group 
{ 
    public MyGroup() 
    { 
        Configure("/my-group", ep => ep.RequestBinder(typeof(MyBinder<>))); 
    } 
} 
```

</details>

<details><summary>Position endpoint version anywhere in the route</summary>

With the built-in versioning, you could only have the endpoint version number either pre-fixed or post-fixed. You can now make the version appear anywhere in the route by using a route template. The template segment will be replaced by the actual version number instead of being prepended or appended.

```csharp
sealed class MyEndpoint : EndpointWithoutRequest
{
    public override void Configure()
    {
        Get("/sales/{_version_}/my-endpoint");
        Version(1);
    }

    ...
}
```

This version placement strategy must be enabled at startup like so:

```csharp
app.UseFastEndpoints(
       c =>
       {
           c.Versioning.RouteTemplate = "{_version_}";
       })
```

If this setting is enabled, it will take precedence over the default behavior of appending/prepending the version number to the route.

</details>

<details><summary>Support for Feature Management libraries</summary>

Endpoints can now be setup to execute a `FeatureFlag` for every Http request that comes in, which allows an endpoint to be conditiona

_…truncated…_

### v7.0.1 Release  (v7.0.1)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v7.0.1>

---

## ❇️ Help Keep FastEndpoints Free & Open-Source ❇️

Due to the current [unfortunate state of FOSS](https://www.youtube.com/watch?v=H96Va36xbvo), please consider [becoming a sponsor](https://opencollective.com/fast-endpoints) and help us beat the odds to keep the project alive and free for everyone.

---

## New 🎉

<details><summary>Relocate response sending methods ⚠️</summary>

Response sending methods such as `SendOkAsync()` have been ripped out of the endpoint base class for a better intellisense experience and extensibility.

Going forward, the response sending methods are accessed via the `Send` property of the endpoint as follows:

```cs
public override async Task HandleAsync(CancellationToken c)
{
    await Send.OkAsync("hello world!");
}
```

In order to add your own custom response sending methods, simply target the `IResponseSender` interface and write extension methods like so:

```cs
static class SendExtensions
{
    public static Task HelloResponse(this IResponseSender sender)
        => sender.HttpContext.Response.SendOkAsync("hello!");
}
```

This is obviously is a wide-reaching breaking change which can be easily remedied with a quick regex based find & replace. Please see the breaking changes section below for step-by-step instructions on how to migrate. Takes less than a minute.

</details>

<details><summary>Send multiple Server-Sent-Event models in a single stream</summary>

It is now possible to send different types of data in a single SSE stream with the use of a wrapper type called **StreamItem** like so:

```cs
public override async Task HandleAsync(CancellationToken ct)
{
    await Send.EventStreamAsync(GetMultiDataStream(ct), ct);

    async IAsyncEnumerable<StreamItem> GetMultiDataStream([EnumeratorCancellation] CancellationToken ct)
    {
        long id = 0;

        while (!ct.IsCancellationRequested)
        {
            await Task.Delay(1000, ct);

            id++;

            if (DateTime.Now.Second % 2 == 1)
                yield return new StreamItem(id.ToString(), "odd-second", Guid.NewGuid()); //guide data
            else
                yield return new StreamItem(id.ToString(), "even-second", "hello!"); //string data
        }
    }
}
```

By default, the `StreamItem` will be serialized as a JSON object, but you can change this by inheriting from it and overriding the `GetDataString` method to return a different format such as XML or plain text.

</details>

<details><summary>Customize param names for strongly typed route params</summary>

It is now possible to customize the route param names when using the [strongly typed route params](https://fast-endpoints.com/docs/misc-conveniences#strongly-typed-route-parameters) feature by simply decorating the target DTO property with a `[BindFrom("customName"))]` attribute. If a `BindFrom` attribute annotation is not present on the property, the actual name of the property itself will end up being the route param name.

</details>

<details><summary>Support for malformed JSON array string binding</summary>

When submitting requests via SwaggerUI where a complex object collection is to be bound to a collection property of a DTO, SwaggerUI sends in a malformed string of JSON objects without properly enclosing them in the JSON array notation `[...]` such as the following:

```json
{"something":"one"},{"something":"two"}
```

whereas it should be a proper JSON array such as this:

```json
[{"something":"one"},{"something":"two"}]
```

Since we have no control over how SwaggerUI behaves, support has been added to the default request binder to support parsing and binding the malformed comma separateed JSON objects that SwaggerUI sends at the expense of a minor performance hit.

</details>

<details><summary>Auto infer query parameters for routeless integration tests</summary>

If you annotate request DTO properties with `[RouteParam]` attribute, the helper extensions such as `.GETAsync()` will now automatically populate
the request query string with values from the supplied DTO instance when sending integration test requests.

```cs
sealed class MyRequest
{
    [RouteParam]
    public string FirstName { get; set; }

    public string LastName { get; set; }
}

[Fact]
public async Task Query_Param_Test()
{
    var request = new MyRequest
    {
        FirstName = "John", //will turn into a query parameter
        LastName = "Gallow" //will be in json body content
    };
    var result = await App.Client.GETAsync<MyEndpoint, MyRequest, string>(request);
}
```

</details>

<!-- ## Improvements 🚀 -->

## Fixes 🪲

<details><summary>Header example value not picked up from swagger example request</summary>

If a request DTO specifies a custom header name that is different from the property name such as the following:

```cs
sealed class GetItemRequest
{
    [FromHeader("x-correlation-id")]
    public Guid CorrelationId { get; init; }
}
```

and a summary example request is provided such as the following:

```cs
Summary(s => s.ExampleRequest = new GetItemRequest()
{
    CorrelationId = "54321"
});
```

the example value from the summary example property was not being picked up due to an oversight.

</details>

<details><summary>Xml comments not picked up by swagger for request schema</summary>

There was a regression in the code path that was picking up `Summary` xml comments from DTO properties in certain scenarios, which has now been fixed.

</details>

<details><summary>Incorrect swagger example generation when '[FromBody] or [FromForm]' was used</summary>

If a request DTO was defined like this:

```cs
sealed class MyRequest
{
    [FromBody]
    public Something Body { get; set; }
}
```

and an example request is provided via the Summary like this:

```cs
Summary(x=>x.ExampleRequest = new MyRequest()
{
    Body = new Something()
    {
  

_…truncated…_


## v6.x

### v6.2 Release  (v6.2)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v6.2>

---

## ❇️ Help Keep FastEndpoints Free & Open-Source ❇️

Due to the current [unfortunate state of FOSS](https://www.youtube.com/watch?v=H96Va36xbvo), please consider [becoming a sponsor](https://opencollective.com/fast-endpoints) and help us beat the odds to keep the project alive and free for everyone.

---

<!-- <details><summary>title text</summary></details> -->

## New 🎉

<details><summary>Support 'Scope' based access restriction</summary>

Your can now restrict access based on [Scopes](https://oauth.net/2/scope) in tokens (e.g., from OAuth2/OpenID Connect IDPs). Simply specify required scopes using the newly added **Scopes()** method:

```cs
public override void Configure()
{
    Get("/item");
    Scopes("item:read", "item:write");
}
```

This allows access if the user's **"scope"** claim includes ANY of the listed values. To require ALL scopes, use **ScopesAll()** instead.

By default, scopes are read from the **"scope"** claim, which can be changed like so:

```cs
app.UseFastEndpoints(c => c.Security.ScopeClaimType = "scp")
```

If scope values aren't space-separated, customize parsing like so:

```cs
app.UseFastEndpoints(c => c.Security.ScopeParser = input =>
{
    //extract scope values and return a collection of strings
})
```

</details>

<details><summary>Automatic 'Accepts Metadata' for Non-Json requests</summary>

In the past, if an endpoint defines a request DTO type, an accepts-metadata of `application/json` would be automatically added to the endpoint, which would require the user to [clear that default metadata](https://fast-endpoints.com/docs/swagger-support#clearing-only-accepts-metadata) if all the properties of the DTO is bound from non-json binding sources such as route/query/header etc.

Now, if the user annotates all the properties of a DTO with the respective non-json binding sources such as the following:

```cs
sealed class GetAccountStatementRequest
{
    [RouteParam]
    public int UserId { get; set; }
    
    [QueryParam]
    public DateTime DateFrom { get; set; }

    [QueryParam]
    public DateTime DateTo { get; set; }
}
```

It is no longer necessary for the user to manually clear the default accepts-metadata as the presence of non-json binding source attributes on each of the DTO properties allows us to correctly detect that there's not going to be any JSON body present in the incoming request.

</details>

<details><summary>Support for 'DataAnnotations' Validation Attributes</summary>

You can now annotate request DTO properties with `DataAnnotations` attributes such as `[Required], [StringLength(...)]` etc., instead of writing a `FluentValidations` validator for quick-n-dirty input validation. Do note however, only one of the strategies can be used for a single endpoint. I.e. if a request DTO has annotations as well as a fluent validator, only the fluent validator will be run and the annotations will be ignored. Mixing strategies is not allowed in order to prevent confusion for the reader. To enable `DataAnnotations` support, do the following:

```cs
app.UseFastEndpoints(c => c.Validation.EnableDataAnnotationsSupport = true)
```

</details>

<!-- ## Improvements 🚀 -->

## Fixes 🪲

<details><summary>Swagger generation bug caused by lists of request DTOs</summary>

A new feature introduced in `v6.1` caused swagger generation to fail if the request DTO type of the endpoint is a `List<T>`, which has been corrected.

</details>

<details><summary>Infinite recursion issue with swagger generation due to self referencing validators</summary>

If a request uses a self referencing validator for nested properties, a stack overflow was happening due to infinite recursion.

</details>

<details><summary>Issue with generic post-processor registration</summary>

Generic post-processors were not being correctly registered due to an oversight, which has been corrected with this release.

</details>

## Minor Breaking Changes ⚠️

<details><summary>Behavior change with multiple binding sources and the 'required' keyword</summary>

If a request DTO has required properties like so:

```cs
{
    public required string UserId { get; set; } //to be bound from route param
    public required string Name { get; set; } //to be bound from json body
}
```

The previous advice was to simply decorate the `UserId` property with a `[JsonIgnore]` attribute so that the serializer will ignore the `required` keyword and won't complain due to missing data for that property in the incoming JSON body.

Even though the `[JsonIgnore]` attribute seemed logical for this purpose at the time, we've come to realize it has the potential to cause problems elsewhere.

So, if you are using the `required` keyword on DTO properties that are to be bound from a non-json binding source such as route/query params, form fields, headers, claims, etc. and would like to keep on using the `required` keyword (even though it doesn't really make much sense in the context of request DTOs in most cases), you should remove the `[JsonIgnore]` property and annotate the binding related attribute that actually specifies what binding source should be used for that property, such as `[RouteParam]`, `[QueryParam]`, `[FormField]`, `[FromClaim]`, `[FromHeader]`, etc.

The request DTO now needs to look like the following:

```cs
sealed class MyRequest
{
    [RouteParam]
    public required string UserId { get; set; }

    public required string Name { get; set; }
}
```

</details>

### v6.1 Release  (v6.1)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v6.1>

---

## ❇️ Help Keep FastEndpoints Free & Open-Source ❇️

Due to the current [unfortunate state of FOSS](https://www.youtube.com/watch?v=H96Va36xbvo), please consider [becoming a sponsor](https://opencollective.com/fast-endpoints) and help us beat the odds to keep the project alive and free for everyone.

---

<!-- <details><summary>title text</summary></details> -->

## New 🎉

<details><summary>Convenience method for retrieving the auto generated endpoint name</summary>

You can now obtain the generated endpoint name like below for the purpose of custom link generation using the `LinkGenerator` class.

```cs
var endpointName = IEndpoint.GetName<SomeEndpoint>();
```

</details>

<details><summary>Auto population of headers in routeless tests</summary>

Given a request dto such as the following where a property is decorated with the `[FromHeader]` attribute:

```cs
sealed class Request
{
    [FromHeader]
    public string Title { get; set; }
    public string FirstName { get; set; }
    public string LastName { get; set; }
}
```

Previously, you had to manually add the header to the request in order for the endpoint to succeed without sending back an error response.
Now you can simply supply the value for the header when making the request as follows, and the header will be automatically added to the request with the value from the property.

```cs
var (rsp, res) = await App.Client.POSTAsync<MyEndpoint, Request, string>(
                     new()
                     {
                         Title = "Mrs.",
                         FirstName = "Doubt",
                         LastName = "Fire"
                     });
```

This automatic behavior can be disabled as follows if you'd like to keep the previous behavior:

```cs
POSTAsync<...>(..., populateHeaders: false);
```

</details>

<details><summary>Comma separated value binding support for collection properties</summary>

It was only possible to model bind collection properties if the values were submitted either as json arrays or duplicate keys.
You can now submit csv data for automatically binding to collection properties such as the following:

```cs
public class FindRequest
{
    [QueryParam]
    public string[] Status { get; set; }
}
```

A url with query parameters such as this would work out-of-the-box now:

```ini
/find?status=queued,completed
```

</details>


<details><summary>'SendAcceptedAtAsync()' method for endpoints</summary>

The following method is now available for sending a `202 - Accepted` similarly to the `201 - Created` response.

```cs
await SendAcceptedAtAsync<ProgressEndpoint>(new { Id = "123" });
```

</details>

<details><summary>Error Code & Error Severity support for the 'ThrowError()' method</summary>

A new overload has been added for the `ThrowError()` method where you can supply an error code and an optional severity value as follows:

```cs
ThrowError("Account is locked out!", errorCode: "AccountLocked", severity: Severity.Error, statusCode: 423);
```

</details>


<details><summary>Setting for changing 'default value' binding behavior</summary>

Given a request dto such as the following, which has a nullable value type property:

```cs
public class MyRequest
{
    [QueryParam]
    public int? Age { get; set; }
}
```

and a request is made with an empty parameter value such as:

```yaml
/person?age=
```

the default behavior is to populate the property with the `default value` for that `value type` when model binding, and if the parameter name is also omitted, the property would end up being `null`.

You can now change this behavior so that in case an empty parameter is submitted, the property would end up being `null`, instead of the default value:

```cs
app.UseFastEndpoints(c => c.Binding.UseDefaultValuesForNullableProps = false)
```

Note: the setting applies to all non-STJ binding paths such as route/query/claims/headers/form fields etc.

</details>


<details><summary>Preliminery support for OData</summary>

A new pre-release package `FastEndpoints.OData` has been created to provide support for OData. Since the OData library's Minimal APIs support is still in flux, FE's OData package is referncing a nightly build from `MyGet` and the public API may change drastically. [See here](https://github.com/FastEndpoints/FastEndpoints/issues/344#issuecomment-2868729911) if you'd like to give it a try.

</details>

## Improvements 🚀

<details><summary>'Configuration Groups' support for refresh token service</summary>

Configuration groups were not previously compatible with the built-in refresh token functionality. You can now group refresh token service endpoints using a group as follows:

```cs
public class AuthGroup : Group
{
    public AuthGroup()
    {
        Configure("users/auth", ep => ep.Options(x => x.Produces(401)));
    }
}

public class UserTokenService : RefreshTokenService<TokenRequest, TokenResponse>
{
    public MyTokenService(IConfiguration config)
    {
        Setup(
            o =>
            {
                o.Endpoint("refresh-token", ep => 
                  { 
                    ep.Summary(s => s.Summary = "this is the refresh token endpoint");
                    ep.Group<AuthGroup>(); // this was not possible before
                  });
            });
    }
}
```

</details>

<details><summary>Pick up Swagger request param example values from summary example</summary>

In the past, the only way to provide an example value for a swagger request parameter was with an xml document comment like so:

```cs
sealed class MyRequest
{
    /// <example>john doe</example>
    public string Name { get; set; }
}
```

The example values will now be picked up from the summary example request properties which you can supply like so:

```cs
Summary(
    s => s.ExampleRequest = new()
    {
        Nam

_…truncated…_

### v6.0 Release  (v6.0)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v6.0>

---

## ❇️ Help Keep FastEndpoints Free & Open-Source ❇️

Due to the current [unfortunate state of FOSS](https://www.youtube.com/watch?v=H96Va36xbvo), please consider [becoming a sponsor](https://opencollective.com/fast-endpoints) and help us beat the odds to keep the project alive and free for everyone.

---

<!-- <details><summary>title text</summary></details> -->

## Breaking Changes ⚠️

> Support for .NET 6 & 7 has been dropped as those SDKs are no longer supported by Microsoft. In order to use this release of FastEndpoints, you need to be on at least .NET 8.0.4

## New 🎉

<details><summary>Support for .NET 10 preview</summary>

You can start targeting `net10.0` SDK in your FE projects now. Currently preview versions of the dependencies are used.

</details>

<details><summary>Generic Pre/Post Processor global registration</summary>

Open generic pre/post processors can now be registered globally using the endpoint configurator func like so:

```cs
app.UseFastEndpoints(c => c.Endpoints.Configurator = ep => ep.PreProcessors(Order.Before, typeof(MyPreProcessor<>)))
```

```cs
sealed class MyPreProcessor<TRequest> : IPreProcessor<TRequest>
{
    public Task PreProcessAsync(IPreProcessorContext<TRequest> ctx, CancellationToken c)
    {
        ...
    }
}
```

</details>

<details><summary>Middleware pipeline for Command Bus</summary>

By popular demand from people moving away from MediatR, a middleware pipeline similar to MediatRs [pipeline behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) has been added to FE's built-in command bus. You just need to write your pipeline/middleware pieces by implementing the interface `ICommandMiddleware<TCommand,TResult>` and register those pieces to form a middleware pipeline as described in the [documentation](https://fast-endpoints.com/docs/command-bus#command-middleware-pipeline).

</details>

<details><summary>Support 'CONNECT' and 'TRACE' verbs</summary>

The `FastEndpoints.Http` enum and the endpoint base classes now have support for the HTTP `CONNECT` & `TRACE` verbs.

</details>

<details><summary>Verify event publishes when integration testing</summary>

When integration testing using the `AppFixture`, it is now possible to setup a `Test Event Receiver` as a collector of all the events that gets published from your code. These received events can be used as verification that your code did actually publish the desired event. A full example of this new capability can be seen [here](https://gist.github.com/dj-nitehawk/ae85c63fefb1e8163fdd37ca6dcb7bfd).

</details>

<details><summary>Dynamic updating of JWT signing keys at runtime</summary>

Updating the signing keys used by JWT middleware at runtime is now made simple without having to restart the application.
[See here](https://gist.github.com/dj-nitehawk/65b78b08075fae3070e9d30e2a59f4c1) for a full example of how it is done.

</details>

## Improvements 🚀

<details><summary>Automatic addition of 'ProducesResponseTypeMetadata'</summary>

The library [automatically adds response type metadata](https://fast-endpoints.com/docs/swagger-support#describe-endpoints) for certain response types.
Sometimes, the automatically added responses need to be cleared by the user when it's not appropriate.
From now on, the automatic additions will only happen if the user hasn't already added it.

**Before:**

```cs
Description(x => x.ClearDefaultProduces(200) //had to clear the auto added 200
                  .Produces(201))
```

**Now:**

```cs
Description(x => x.Produces(201)) //nothing to clear as nothing was added due to 201 being present
```

</details>

<details><summary>Use source generated regex</summary>

Source generated regex is now used whereever possible. Source generated regex was not used before due to having to support older SDK versions.

</details>

<details><summary>Allow overriding the 'Verbs()' method of `Endpoint<>` class</summary>

The `Verbs()` method was sealed until now because it was doing some essential setup which was required for adding the default request/response swagger descriptions.
This logic has been moved out of the `Verbs()` method making it overrideable if needed.

</details>

<details><summary>Prevent configuration methods being called after startup</summary>

A meaningful exception will now be thrown if the user tries to call endpoint configuration methods such as `Verbs()/Routes()/etc.` outside of the endpoint `Configure()` method.

</details>

## Fixes 🪲

<details><summary>Contention issue in reflection source generator</summary>

The reflection source generator was using some static state which was causing issues in certain usage scenarios, which has now been fixed.

</details>

<details><summary>Type discriminator missing from polymorphic responses</summary>

The type discriminator was not being serialized by STJ when the response type was a base type, due to an oversight in the default response serialized func.

</details>

<details><summary>Source generated reflection for obsolete members</summary>

When source generation happens for obsolete members of classes, the generated file triggered a compiler warning, which has now been correctly handled.

</details>


## v5.x

### v5.35 Release  (v5.35)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.35>

---

## ❇️ Help Keep FastEndpoints Free & Open-Source ❇️

Due to the current [unfortunate state of FOSS](https://www.youtube.com/watch?v=H96Va36xbvo), please consider [becoming a sponsor](https://opencollective.com/fast-endpoints) and help us beat the odds to keep the project alive and free for everyone.

---

<!-- <details><summary>title text</summary></details> -->

## New 🎉

<details><summary>Bypass endpoint caching for integration tests</summary>

You can now easily test endpoints that have caching enabled, by using a client configured to automatically bypass caching like so:

```cs
var antiCacheClient = App.CreateClient(new() { BypassCaching = true });
```

</details>

<details><summary>Mark properties as "bind required"</summary>

You can now make the request binder automatically add a validation failure when binding from route params, query params, and form fields by decorating the dto properties if the binding source doesn't provide a value:

```cs
sealed class MyRequest
{
    [QueryParam(IsRequired = true)]
    public bool Correct { get; set; }

    [RouteParam(IsRequired = true)]
    public int Count { get; set; }

    [FormField(IsRequired = true)]
    public Guid Id { get; set; }
}
```

</details>

<details><summary>Generic command support for job queues</summary>

Closed generic commands can now be registered like so:

```cs
app.Services.RegisterGenericCommand<QueueCommand<OrderCreatedEvent>, QueueCommandHandler<OrderCreatedEvent>>();
```

and then be queued as jobs like so:

```cs
await new QueueEventCommand<OrderCreatedEvent>()
{ 
  ...
}.QueueJobAsync();
```

Note: Open generic commands are not supported for job queueing.

</details>

<details><summary>Inter-Process-Communication via Unix-Domain-Sockets</summary>

The [FastEndpoints.Messaging.Remote](https://fast-endpoints.com/docs/remote-procedure-calls) library can now do inter-process-communication via unix sockets when everything is running on the same machine by doing the following:

```cs
//server setup
bld.WebHost.ConfigureKestrel(k => k.ListenInterProcess("ORDERS_MICRO_SERVICE"));

//client setup
app.MapRemote("ORDERS_MICRO_SERVICE", c => c.Register<CreateOrderCommand>());
```

When a service is lifted out to a remote machine, all that needs to be done is to update the connection settings like so:

```cs
//server
bld.WebHost.ConfigureKestrel(k => k.ListenAnyIP(80, o => o.Protocols = HttpProtocols.Http2);

//client
app.MapRemote("http://orders.my-app.com", c => c.Register<CreateOrderCommand>());
```

</details>

<details><summary>Optionally save command type on job storage record</summary>

A new optional/addon interface `IHasCommandType` has been introduced if you need to persist the full type name of the command that is associated with the job storage record. Simply implement the new interface on your job storage record and the system will automatically populate the property value before being persisted.

</details>

## Improvements 🚀

<details><summary>RPC Event Subscriber parallel execution</summary>

Event subscribers used to execute the event handlers in sequence when a batch of event storage records were fetched from the storage provider.
The handlers will now be executed in parallel just like how parallel execution happens in job queues.

</details>

<details><summary>RPC Event Hub startup sequence</summary>

The rpc event hub was using a thread sleep pattern during startup to restore subscriber IDs via the storage provider, resulting in a sequential initialization.
It has been refactored to use an IHostedService together with retry logic for a proper async and parallel initialization, resulting in decreased startup time.

</details>

<details><summary>RPC Event Hub event distribution</summary>

Previously if a hub was not registered before events were broadcasted, or if event serialization fails due to user error, those exceptions would have been swallowed in some cases.
The internals of the hub has been refactored to surface those exceptions when appropriate.

</details>

<details><summary>Workaround for NSwag quirk with byte array responses</summary>

NSwag has a quirk that it will render an incorrect schema if the user does something like the following:

```cs
b => b.Produces<byte[]>(200, "image/png");
```

In order to get the correct schema generated, we've had to do the following:

```cs
b => b.Produces<IFormFile>(200, "image/png");
```

You now have the ability to do either of the above, and it will generate the correct schema.

</details>

## Fixes 🪲

<details><summary>Job result is null when job execution failure occurs</summary>

The result property of job records that was passed into the `OnHandlerExecutionFailureAsync()` method of the storage provider was `null` due to an oversight, which has been corrected.

</details>

<details><summary>Parallel 'VersionSet' creation issue</summary>

If `VersionSet`s are created by multiple SUTs at the same time when doing integration testing, a non-concurrent dictionary modification exception was being thrown.
The internal dictionary used to keep track of the version sets has been changed to a concurrent dictionary which solves the issue.

</details>

## Breaking Changes (Minor) ⚠️

<details><summary>'IEventHubStorageProvider' contract change</summary>

In order to improve database write performance, the `IEventHubStorageProvider.StoreEventAsync(TStorageRecord r, CancellationToken ct)` method signature has been changed to the following:

```cs
ValueTask StoreEventsAsync(IEnumerable<TStorageRecord> r, CancellationToken ct);
```

Previously, records were persisted one at a time. Now, the records are supplied in batches allowing you to take advantage of batched inserts and/or transactions improving database write performance and consistency.

NOTE: You should make sure either none or all of the supplied 

_…truncated…_

### v5.34 Release  (v5.34)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.34>

---

## ❇️ Help Keep FastEndpoints Free & Open-Source ❇️

Due to the current [unfortunate state of FOSS](https://www.youtube.com/watch?v=H96Va36xbvo), please consider [becoming a sponsor](https://opencollective.com/fast-endpoints) and help us beat the odds to keep the project alive and free for everyone.

---

<!-- <details><summary>title text</summary></details> -->

## New 🎉

<details><summary>Queued job progress tracking</summary>

It is now possible to queue a job and track its progress and/or retrieve intermediate results while the command handler executes via the job tracker as [documented here](https://fast-endpoints.com/docs/job-queues#tracking-job-execution-progress).

</details>

<details><summary>Global 'JwtCreationOptions' support for refresh token service</summary>

If you configure jwt creation options at a global level like so:

```cs
bld.Services.Configure<JwtCreationOptions>( o =>  o.SigningKey = "..." ); 
```

The `RefreshTokenService` will now take the default values from the global config if you don't specify anything when configuring the token service like below:

```cs
sealed class MyTokenService : RefreshTokenService<TokenRequest, TokenResponse>
{
    public MyTokenService
    {
        Setup(o =>
        {         
            //no need to specify token signing key/style/etc. here unless you want to.
            o.Endpoint("/api/refresh-token");
            o.AccessTokenValidity = TimeSpan.FromMinutes(5);
            o.RefreshTokenValidity = TimeSpan.FromHours(4);
        });
    }
}
```

</details>

<details><summary>Global response modifier setting</summary>

A new global action has been added which gets triggered right before a response is written to the response stream allowing you to carry out some common logic that should be applied to all endpoints.

```cs
app.UseFastEndpoints(
       c => c.Endpoints.GlobalResponseModifier
                = (ctx, content) =>
                  {
                      ctx.Response.Headers.Append("x-common-header", "some value");
                  })
```

</details>

<details><summary>Access 'IServiceProvider' when configuring Swagger Documents</summary>

You can now access the built service provider instance via the `DocumentOptions.Services` property when configuring swagger documents like so:

```cs
var bld = WebApplication.CreateBuilder(args);
bld.Services.Configure<MySettings>(bld.Configuration.GetSection(nameof(MySettings)));
bld.Services
   .SwaggerDocument(
       o =>
       {
           // IServiceProvider is available via DocumentOptions.Services property
           var conf = o.Services.GetRequiredService<IOptions<MySettings>>();
           o.DocumentSettings = doc =>
                                {
                                    doc.DocumentName = conf.Value.DocName;
                                };
       })
   .AddFastEndpoints();
```

</details>

## Improvements 🚀

<details><summary>Value parser support for Reflection Source Generator</summary>

Value parser functions (used by non-stj model binding) will now be source generated instead of being compiled at runtime when you opt-in to use the reflection source generator.

</details>

<details><summary>Optimize value parser internals</summary>

String value parsing logic used in most non-stj model binding paths has been simplified and optimized to reduce allocations and unnecessary boxing.

</details>

<details><summary>Graceful shutdown of Job Queue processing</summary>

If app shutdown is requested during a retry loop (due to transient failures) in job queue processing, the operation will now be tried at least once before exiting the retry loops and allowing the app to shut down.

</details>

<details><summary>Miscellaneous improvements</summary>

- Remove all traces of `FluentAssertions` from FE test projects & documentation examples
- Prioritize the typed `Summary(x => {})` overload over the untyped overload in .NET 9

</details>

## Fixes 🪲

<details><summary>Issue with unit testing endpoints with pre-processors with injected dependencies</summary>

Unit tests were failing to instantiate pre-processors that had injected dependencies due to a small oversight in the `ServiceResolver` code with regards to how singletons were instantiated, which has been fixed.

</details>

<details><summary>Potential infinite recursion in Swagger Processor due to circular references</summary>

In certain edge cases where the schema has circular references, there was a potential inifinite recursion issue which could lead to memory leaks when generating the swagger docs.

</details>

<!-- ## Breaking Changes ⚠️ -->

### v5.33 Release  (v5.33)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.33>

---

## ❇️ Help Keep FastEndpoints Free & Open-Source ❇️

Due to the current [unfortunate state of FOSS](https://www.youtube.com/watch?v=H96Va36xbvo), please consider [becoming a sponsor](https://opencollective.com/fast-endpoints) and help us beat the odds to keep the project alive and free for everyone.

---

<!-- <details><summary>title text</summary></details> -->

## New 🎉

<details><summary>Migrate to xUnit v3 ⚠️</summary>

If you're using the `FastEndpoints.Testing` package in your test projects, take the following steps to migrate your projects:

1. Update all "FastEndpoints" package references in your projects to "5.33.0".
2. In your test project's `.csproj` file:
    1. Remove the package reference to the `xunit` v2 package.
    2. Add a package reference to the new `xunit.v3` library with version `1.0.0`
    3. Change the version of `xunit.runner.visualstudio` to `3.0.0`
3. Build the solution.
4. If there are compilation errors related to the return type of overridden methods in your derived `AppFixture<TProgram>` classes, such as `SetupAsync` and `TearDownAsync`. Change their return type from `Task` to `ValueTask` to resolve these errors.
5. If there are any compilation errors related to `XUnit.Abstractions` namespace not being found, simply delete those "using statements" as that namespace has been removed in xUnit v3.

After doing the above, it should pretty much be smooth sailing, unless your project is affected by the removal of previously deprecated classes as mentioned in the "Breaking Changes" section below.

</details>

<details><summary>Eliminate the need for [BindFrom(...)] attribute</summary>

Until now, when binding from sources other than JSON body, you had to annotate request DTO properties with the `[BindFrom("my_field")]` attribute when the incoming field name is different to the DTO property name. A new setting has now been introduced which allows you to use the same property naming policy as the serializer for matching incoming request parameters without having to use any attributes.

```cs
app.UseFastEndpoints(c => c.Binding.UsePropertyNamingPolicy = true)
```

This only applies to properties where you haven't specified the field names manually using an attribute such as `[BindFrom(...)]`, `[FromClaim(...)]`. `[FromHeader(...)]` etc.

</details>


<details><summary>Control binding sources per DTO property</summary>

The default binding order is designed to minimize attribute clutter on DTO models. In most cases, disabling binding sources is unnecessary. However, for rare scenarios where a binding source must be explicitly blocked, you can now do the following:

```cs
[DontBind(Source.QueryParam | Source.RouteParam)] 
public string UserID { get; set; } 
```

The opposite approach can be taken as well, by just specifying a single binding source for a property like so:

```cs
[FormField]
public string UserID { get; set; }

[QueryParam]
public string UserName { get; set; }

[RouteParam]
public string InvoiceID { get; set; }
```

</details>

<details><summary>Deeply nested complex model binding from query parameters</summary>

Binding deeply nested complex DTOs from incoming query parameters is now supported. Please refer to the documentation [here](https://fast-endpoints.com/docs/model-binding#complex-query-binding).

</details>

<details><summary>Swagger descriptions for deeply nested DTO properties</summary>

Until now, if you wanted to provide text descriptions for deeply nested request DTO properties, the only option was to provide them via XML document summary tags. You can now provide descriptions for deeply nested properties like so:

```cs
Summary(
    s =>
    {
        s.RequestParam(r => r.Nested.Name, "nested name description");
        s.RequestParam(r => r.Nested.Items[0].Id, "nested item id description");
    });
```

Descriptions for lists and arrays can be provided by using an index `0` to get at the actual property. **Note:** only lists and arrays can be used for this.

</details>

<!-- ## Improvements 🚀 -->

## Fixes 🪲

<details><summary>Incorrect latest version detection with 'Release Versioning' strategy</summary>

The new release versioning strategy was not correctly detecting the latest version of an endpoint if there was multiple endpoints for the same route such as a GET & DELETE endpoint on the same route.

</details>

<details><summary>Issue with nullability context not being thread safe in Swagger processor</summary>

In rare occasions where swagger documents were being generated concurrently, an exception was being thrown due to `NullabilityInfoContext` not being thread safe. This has been fixed by implementing a caching mechanism per property type.

</details>

<details><summary>Complex DTO handling in routeless testing extensions</summary>

If the request DTO is a complex structure, testing with routeless test extensions like the following did not work correctly:

```cs
[Fact]
public async Task FormDataTest()
{
    var book = new Book
    {
        BarCodes = [1, 2, 3],
        CoAuthors = [new Author { Name = "a1" }, new Author { Name = "a2" }],
        MainAuthor = new() { Name = "main" }
    };

    var (rsp, res) = await App.GuestClient.PUTAsync<MyEndpoint, Book, Book>(book, sendAsFormData: true);

    rsp.IsSuccessStatusCode.Should().BeTrue();
    res.Should().BeEquivalentTo(book);    
}
```

</details>

<details><summary>Incorrect detection of generic arguments of generic commands</summary>

There was a minor oversight in correctly detecting the number of generic arguments of generic commands if there was more than one.
This has been fixed to correctly detect all generic arguments of generic commands.

</details>

<details><summary>Complex form data binding issue</summary>

When binding deeply nested form data with the `[FromForm]` attribute, if a certain deeply nested objects didn't have a

_…truncated…_

### v5.32 Release  (v5.32)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.32>

---

## ❇️ Help Keep FastEndpoints Free & Open-Source ❇️

Due to the current [unfortunate state of FOSS](https://www.youtube.com/watch?v=H96Va36xbvo), please consider [becoming a sponsor](https://opencollective.com/fast-endpoints) and help us beat the odds to keep the project alive and free for everyone.

---

<!-- <details><summary>title text</summary></details> -->

## New 🎉

<details><summary>.NET 9.0 Support</summary>

Migration to .NET 9.0 SDK is now complete. You can now target `net9.0` sdk without any issues.

</details>

<details><summary>Support for enforcing antiforgery token checks for non-form requests</summary>

The antiforgery middleware can now be configured to check antiforgery tokens for any content-type by configuring it like so:

```csharp
app.UseAntiforgeryFE(additionalContentTypes: ["application/json"])
```

</details>

<details><summary>User configurable Endpoint Name (Operation Id) generation</summary>

The endpoint name generation logic can now be overriden at a global level like so:

```csharp
app.UseFastEndpoints(
       c => c.Endpoints.NameGenerator =
                ctx =>
                {
                    return ctx.EndpointType.Name.TrimEnd("Endpoint");
                })
```

</details>

<details><summary>Global configuration of 'JwtCreationOptions'</summary>

You can now configure `JwtCreationOptions` once globally like so:

```csharp
bld.Services.Configure<JwtCreationOptions>(
       o =>
       {
           o.SigningKey = "...";
           o.Audience = "...";
           o.Issuer = "...";
       })
```

and only specify just the relevant settings that are needed to be set during token creation like so.

```csharp
var token = JwtBearer.CreateToken(
    o =>
    {
        o.ExpireAt = DateTime.UtcNow.AddHours(1);
        o.User.Claims.Add(("UserId", "001"));
    });
```

If you need to override any of the globally specified settings, that can be done during token creation as well, as what's supplied to the `CreateToken(o=> ...)` method is a deeply cloned instance independant of the global instance.

</details>

<details><summary>New endpoint versioning strategy based on 'Release Versions'</summary>

A new route based versioning strategy called [Release Versioning](https://fast-endpoints.com/docs/api-versioning#release-version-strategy) has been introduced in addition to the existing two built-in versioning strategies.

</details>

## Improvements 🚀

<details><summary>Swagger OneOf support for polymorphic responses</summary>

When enabling `OneOf` for polymorphism like the following:

```csharp
.SwaggerDocument(c => c.UseOneOfForPolymorphism = true)
```

The correct response swagger spec is not generated by NSwag by default. As requested by #807, the correct spec will now be generated.

</details>

<details><summary>Default response metadata for endpoints without a response type</summary>

Previously, if the endpoint doesn't define a particular response DTO type, a default produces 200 response metadata was being added which resulted in swagger spec like the following:

```json
"responses": { 
  "200": { 
    "description": "Success", 
    "content": { 
      "text/plain": { 
        "schema": {} 
      }, 
      "application/json": { 
        "schema": {} 
      } 
    } 
  }
```

Even though it's not incorrect, it can cause issues in some cases such as TS client generation. From now on if the endpoint doesn't specify a response DTO type, a 204 - No Content produces metadata would be added by default which results in more correct swagger spec such as the following:

```json
"responses": { 
  "204": { 
    "description": "No Content" 
  }
}
```

</details>

<details><summary>Detection of mapper type in unit tests</summary>

The logic for automatically detecting the endpoint mapper type during unit tests has been improved to prevent any "Endpoint mapper not set!" exceptions in some cases.

</details>

## Fixes 🪲

<details><summary>Struct support for request DTOs</summary>

Adding the new reflection source generator broke support for struct types to be used for request DTOs, which has been corrected in this release.

</details>

<details><summary>Struct support for Reflection Source Generator</summary>

The reflection generator was not generating the correct source for unboxing value types.

</details>

<details><summary>Reflection generation for abstract types</summary>

The reflection generator was trying to generate code for deeply nested abstract types, which has now been fixed.

</details>

<details><summary>Incorrect constructor detection in Reflection Generator</summary>

The reflection generator was wrongly detecting constructors from base types instead of just stopping at the top most level.

</details>

<details><summary>Included validators causing an exception</summary>

There was a regression in the validation schema processor which resulted in included fluent validators causing an exception at the time of generating the swagger spec.

</details>

<details><summary>Unescaped back slashes breaking model binding</summary>

Incorrectly unescaped parameter values from the client was causing model binding failures which has been now corrected.

</details>

<details><summary>Rogue 200 response in Swagger spec</summary>

Due to a known bug in the .NET 9.0 SDK, a rogue 200 response metadata was being added to endpoints if the endpoints response DTO type is an `IResult` type and it's not a 200 status code. A workaround has been put in place to prevent that from happening.

</details>

<!-- ## Minor Breaking Changes ⚠️ -->

### v5.31 Release  (v5.31)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.31>

---

## ❇️ Help Keep FastEndpoints Free & Open-Source ❇️

Due to the current [unfortunate state of FOSS](https://www.youtube.com/watch?v=H96Va36xbvo), please consider [becoming a sponsor](https://opencollective.com/fast-endpoints) and help us beat the odds to keep the project alive and free for everyone.

---

[//]: # (<details><summary>title text</summary></details>)

## New 🎉

<details><summary>.NET 9.0 SDK Support</summary>

Migration to .NET 9 has been completed. We're currently referencing the GA build of the SDK. Once RTM comes out, the references will be updated in the following FastEndpoints release. The GA build seems to be quite stable and suitable for production use.

</details>

<details><summary>Source generator for avoiding reflection cost</summary>

The newly added [Reflection Source Generator](https://fast-endpoints.com/docs/configuration-settings#source-generated-reflection) can be used in order to avoid the cost of runtime expression compilation & reflection based methods.

</details>

<details><summary>Multipart Form Data binding support for deeply nested complex DTOs</summary>

Binding deeply nested complex DTOs from incoming form-data (including files) is now supported. Please refer to the documentation [here](https://fast-endpoints.com/docs/model-binding#binding-nested-complex-form-data).

</details>

<details><summary>Ability to disable FluentValidation+Swagger integration per rule</summary>

The built-in FV+Swagger integration can be disabled per property rule with the newly added `.SwaggerIgnore()` extension method as shown below.

```csharp
sealed class MyValidator : Validator<MyRequest>
{
    public MyValidator()
    {
        RuleFor(x => x.Id)
            .NotEmpty()
            .SwaggerIgnore();
    }
}
```

</details>

<details><summary>Automatic transformation of 'ProblemDetails.Title' & 'ProblemDetails.Type' values according to 'StatusCode'</summary>

The `ProblemDetails` Title and Type values will now be automatically determined/transformed according to the `Status` code of the instance. The [default behavior](https://github.com/FastEndpoints/FastEndpoints/blob/0ff9555cd6a99ca19bcfe4ad7c458d5e2d2e04ff/Src/Library/Config/ErrorOptions.cs#L112-L120) can be changed by setting your own `TypeTransformer` and `TitleTransformer` functions like so:

```csharp
app.UseFastEndpoints(
       cfg => cfg.Errors.UseProblemDetails(
           pCfg =>
           {
               pCfg.TypeTransformer
                   = pd =>
                     {
                         switch (pd.Status)
                         {
                             case 404:
                                 return "https://www.rfc-editor.org/rfc/rfc7231#section-6.5.4";
                             case 429:
                                 return "https://www.rfc-editor.org/rfc/rfc6585#section-4";
                             default:
                                 return "https://www.rfc-editor.org/rfc/rfc7231#section-6.5.1";
                         }
                     };
           }))
```

</details>

<details><summary>Enhance Swagger UI search bar behavior</summary>

The Swagger UI search bar is only capable of searching/filtering operations by tag values. The search bar has been enhanced via a custom injected JS plugin to be able to search the following sources:

- Operation paths
- Summary text
- Description text
- Operation parameters
- Request schema
- Response schema

</details>

<details><summary>Extension method to display Swagger operation IDs in Swagger UI</summary>

Calling the following extension method will cause the operation ids to show up in the swagger ui.

```csharp
app.UseSwaggerGen(uiConfig: u => u.ShowOperationIDs());
```

</details>

<details><summary>Allow multiple gRPC event subscribers from the same machine</summary>

Previously it was only possible for a single gRPC subscriber to exist on a single machine for any given event type. Now it's possible to run the subscriber with a custom identifier per instance which will allow more than one subscriber to exist on a particular machine for an event type.

```csharp
app.MapRemote(
    "http://localhost:6000",
    c =>
    {
        //set some unique value per each instance.
        //process id here is just an example.
        //the value just needs to be different across the multiple app/subscriber instances.
        c.Subscribe<MyEvent, MyEventHandler>(clientIdentifier: Environment.ProcessId.ToString());
    });
```

</details>

## Improvements 🚀

<details><summary>Route template syntax highlighting for VS and Rider</summary>

Route template items such as the following will now be correctly syntax highlighted in Rider and Visual Studio:

```csharp
Get("api/invoice/{id}/print")
```

</details>

<details><summary>Allow route param values with curly braces</summary>

The default request binder did not bind incoming route parameter values with curly braces such as:

```http
http://localhost:5000/invoice/{123-456}
```

</details>

<details><summary>Better handling of 'JsonIgnore' attribute condition</summary>

The `[JsonIgnore]` attribute on request/response DTO properties will now be taken into consideration only if it's declared in either of the following two ways:

```csharp
[JsonIgnore] //without specifying a condition (defaults to JsonIgnoreCondition.Always)

[JsonIgnore(Condition = JsonIgnoreCondition.Always)]
```

This change only applies to Swagger generation and Non-STJ model binding behavior.

</details>

## Fixes 🪲

<details><summary>Global 'TypeInfoResolver' not working</summary>

As reported by #783, there was an oversight in the way the built-in modifiers were checking the existence of custom attributes which lead to DTO properties being marked as "should not serialize".

</details>

<details><summary>Incorrect property name resolution of fluen

_…truncated…_

### v5.30 Release  (v5.30)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.30>

---

## ✨ Looking For Sponsors ✨

FastEndpoints needs sponsorship to [sustain the project](https://github.com/FastEndpoints/FastEndpoints/issues/449). Please help out if you can.

---

[//]: # (<details><summary>title text</summary></details>)

## New 🎉

<details><summary>Fluent endpoint base class picker</summary>

A fluent endpoint base class picker similar to `Ardalis.ApiEndpoints` has been added, with which you can pick and choose the DTO and Mapper types you'd like to use in a fluent manner.

```csharp
sealed class MyEndpoint : Ep.Req<MyRequest>.Res<MyResponse>.Map<MyMapper>
{
    ...
}

sealed class MyEndpoint : Ep.Req<MyRequest>.NoRes.Map<MyMapper>
{
    ...
}

sealed class MyEndpoint : Ep.NoReq.Res<MyResponse>
{
    ...
}
```

</details>

<details><summary>Job Queuing support for Commands that return a result</summary>

A command that returns a result `ICommand<TResult>` can now be queued up as a job. The result of a job can be retrieved via the **JobTracker** using its **Tracking Id**.

```csharp
// queue the command as a job and retrieve the tracking id 
var trackingId = new MyCommand { ... }.QueueJobAsync();

// retrieve the result of the command using the tracking id
var result = await JobTracker<MyCommand>.GetJobResultAsync<MyResult>(trackingId);
```

[Click here](https://fast-endpoints.com/docs/job-queues#jobs-with-results) to read the documentation for this feature.

</details>

<details><summary>Transform FluentValidation error property names with 'JsonPropertyNamingPolicy'</summary>

A new configuration setting has been introduced so that deeply nested request DTO property names can be transformed to the correct case using the `JsonPropertyNamingPolicy` of the application.

```csharp
app.UseFastEndpoints(c => c.Validation.UsePropertyNamingPolicy = true)
```

The setting is turned on by default and can be turned off by setting the above boolean to `false`.

</details>

<details><summary>Skip anti-forgery checks for certain requests</summary>

The anti-forgery middleware will now accept a filter/predicate which can be used to skip processing certain requests if a given condition is matched. If the function returns true for a certain request, that request will be skipped by the anti-forgery middleware.

```csharp
.UseAntiforgeryFE(httpCtx => !httpCtx.Request.Headers.Origin.IsNullOrEmpty())
```

</details>

## Improvements 🚀

<details><summary>Make Pre/Post Processor Context's 'Request' property nullable</summary>

Since there are certain edge cases where the `Request` property can be `null` such as when STJ receives invalid JSON input from the client and fails to successfully deserialize the content, the pre/post processors would be executed (even in those cases) where the pre/post processor context's `Request` property would be null. This change would allow the compiler to remind you to check for null if the `Request` property is accessed from pre/post processors.

</details>

<details><summary>Preliminary support for .NET 9.0</summary>

Almost everything works with .NET 9 except for source generation. Full .NET 9 support will be available at the first FE release after .NET 9 final comes out.

</details>

## Fixes 🪲

<details><summary>Nullable 'IFormFile' handling issue with 'HttpClient' extensions</summary>

The `HttpClient` extensions for integration testing was not correctly handling nullable `IFormFile` properties in request DTOs when automatically converting them to form fields.

</details>

<details><summary>Swagger processor issue with virtual path routes</summary>

The swagger processor was not correctly handling routes if it starts with a `~/` (virtual path that refers to the root directory of the web application).

</details>

<details><summary>Remove unreferenced schema from generated swagger document</summary>

When a request DTO has a property that's annotated with a `[FromBody]` attribute, the parent schema was left in the swagger document components section as an unreferenced schema. These orphaned schema will no longer be present in the generated swagger spec.

</details>

<details><summary>Swagger request example issue with properties annotated with [FromBody]</summary>

Xml docs based example values were not correctly picked up for properties annotated with a `[FromBody]` attribute, which resulted in a default sample request example being set in Swagger UI.

</details>

[//]: # (## Minor Breaking Changes ⚠️)

### v5.29 Release  (v5.29)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.29>

---

## ✨ Looking For Sponsors ✨

FastEndpoints needs sponsorship to [sustain the project](https://github.com/FastEndpoints/FastEndpoints/issues/449). Please help out if you can.

---

[//]: # (<details><summary>title text</summary></details>)

## New 🎉

<details><summary>Multi-level test-collection ordering</summary>

Tests can now be ordered by prioritizing test-collections, test-classes in those collections as well as tests within the classes for fully controlling the order of test execution when test-collections are involved. [See here](https://fast-endpoints.com/docs/integration-unit-testing#ordering-tests-in-collections) for a usage example.

</details>

<details><summary>Customize character encoding of JSON responses</summary>

A new config setting has been added for customizing the charset of JSON responses. `utf-8` is used by default. can be set to `null` for disabling the automatic appending of the charset to the `Content-Type` header of responses.

```csharp
app.UseFastEndpoints(c => c.Serializer.CharacterEncoding = "utf-8")
```

</details>

<details><summary>Setting for allowing [JsonIgnore] attribute on 'required' DTO properties</summary>

STJ typically [does not allow](https://github.com/dotnet/runtime/issues/82879) `required` properties to be annotated with `[JsonIgnore]` attribute. The following doesn't work out of the box:

```csharp
public class MyRequest
{
    [JsonIgnore]
    public required string Id { get; init; }
}
```

The following setting is now enabled by default allowing you to annotate `required` properties with `[JsonIgnore]`:

```csharp
app.UseFastEndpoints(c => c.Serializer.EnableJsonIgnoreAttributeOnRequiredProperties = true)
```

It's necessary to decorate `required` properties with `[JsonIgnore]` in situations where the same property is bound from multiple sources.

</details>

<details><summary>Read form-field values together with form-file sections</summary>

A new method has been added to conveniently read regular form-field values when they come in with multi-part form data requests while [buffering is turned off](https://fast-endpoints.com/docs/file-handling#handling-large-file-uploads).

```csharp
await foreach (var sec in FormMultipartSectionsAsync(ct))
{
    //reading the value of a form field
    if (sec.IsFormSection && sec.FormSection.Name == "formFieldName")
    {
        var formFieldValue = await sec.FormSection.GetValueAsync(ct);
    }

    //obtaining the stream of a file
    if (sec.IsFileSection && sec.FileSection.Name == "fileFieldName")
    {
        var fileStream = sec.FileSection.FileStream;
    }
}
```

</details>

<details><summary>'IDisposable' & 'IAsyncDisposable' support for endpoint classes</summary>

You can now implement either 'IDisposable' or 'IAsyncDisposable' interfaces on your Endpoint classes and the correct dispose method will be called once the endpoint completes sending the response.

</details>

<details><summary>Ability to override Swagger Auto-Tagging per endpoint</summary>

Previously you could only choose a single strategy for tagging/grouping endpoints with Swagger. You could either use the path segment based auto-tagging or you could turn it off and manually tag each endpoint yourself. Now you can have auto-tagging enabled and override the auto-tag value per endpoint when necessary like so:

```csharp
Description(x => x.AutoTagOverride("Overridden Tag Name"))
```

</details>

## Improvements 🚀

<details><summary>Remove dependency on 'Xunit.Priority' package</summary>

The 'Xunit.Priority' package is no longer necessary as we've implemented our own test-case-orderer. If you've been using test ordering with the `[Priority(n)]` attribute, all you need to do is get rid of any `using` statements that refer to `XUnit.Priority`.

</details>

## Fixes 🪲

<details><summary>Issue with FluentValidation+Swagger integration</summary>

When a child validator has no parameterless constructor, the FV+Swagger integration was not able to construct an instance of the child validator causing it to be ignored when generating the Swagger spec. Child validators will now be instantiated via FE's service resolver in the validation schema processor to mitigate this issue.

</details>

[//]: # (## Minor Breaking Changes ⚠️)

### v5.28 Release  (v5.28)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.28>

---

## ✨ Looking For Sponsors ✨

FastEndpoints needs sponsorship to [sustain the project](https://github.com/FastEndpoints/FastEndpoints/issues/449). Please help out if you can.

---

[//]: # (<details><summary>title text</summary></details>)

## New 🎉

<details><summary>Jwt token revocation middleware</summary>

Jwt token revocation can be easily implemented with the newly provided abstract class like so:

```csharp
public class JwtBlacklistChecker(RequestDelegate next) : JwtRevocationMiddleware(next)
{
    protected override Task<bool> JwtTokenIsValidAsync(string jwtToken, CancellationToken ct)
    { 
        //return true if the supplied token is still valid
    }
}
```

Simply register it before any auth related middleware like so:

```csharp
app.UseJwtRevocation<JwtBlacklistChecker>()
   .UseAuthentication()
   .UseAuthorization()
```

</details>

<details><summary>Ability to override JWT Token creation options per request for Refresh Tokens</summary>

A couple of new [optional hooks](https://github.com/FastEndpoints/FastEndpoints/blob/5afe7db3628e08fc4515af17701410b4a35f182b/Src/Security/RefreshTokens/RefreshTokenService.cs#L55-L91) have been added that can be tapped in to if you'd like to modify Jwt token creation parameters per request, and also modify the token response per request before it's sent to the client. Per request token creation parameter modification may be useful when allowing the client to decide the validity of tokens.

</details>

<details><summary>Ability to subscribe to gRPC Events from Blazor Wasm projects</summary>

Until now, only gRPC Command initiations were possible from within Blazor Wasm projects. Support has been added to the `FastEndpoints.Messaging.Remote.Core` project which is capable of running in the browser to be able to act as a subscriber for Event broadcasts from a gRPC server. [See here](https://github.com/FastEndpoints/Blazor-Wasm-Remote-Messaging-Demo) for a sample project showcasing both.

</details>

## Improvements 🚀

<details><summary>Get rid of Swagger middleware ordering requirements</summary>

Swagger middleware ordering is no longer important. You can now place the `.SwaggerDocument()` and `.UseSwaggerGen()` calls wherever you prefer.

</details>

<details><summary>Swagger OneOf support for polymorphic request/response DTOs</summary>

Correctly annotated polymorphic base types can now be used as request/response DTOs. The possible list of derived types will be shown in Swagger UI under a `OneOf` field. To enable, decorate the base type with the correct set of attributes like so:

```csharp
public class Apple : Fruit
{
    public string Foo { get; set; }
}

public class Orange : Fruit
{
    public string Bar { get; set; }
}

[JsonPolymorphic(TypeDiscriminatorPropertyName = "_t")]
[JsonDerivedType(typeof(Apple), "a")]
[JsonDerivedType(typeof(Orange), "o")]
public class Fruit
{
    public string Baz { get; set; }
}
```

And set the following setting to `true` when defining the Swagger document:

```csharp
builder.Services.SwaggerDocument(c => c.UseOneOfForPolymorphism = true)
```

</details>

## Fixes 🪲

<details><summary>Swagger generator issue with [FromBody] properties</summary>

The referenced schema was generated as a `OneOf` instead of a direct `$ref` when a request DTO property was being annotated with the `[FromBody]` attribute.

</details>

<details><summary>Swagger route parameter detection issue</summary>

The Nswag operation processor did not correctly recognize route parameters in the following form:

```csharp
api/a:{id1}:{id2}
```

Which has now been corrected thanks to PR #735

</details>

<details><summary>Kiota client generation issue with 'clean output' setting</summary>

If the setting for cleaning the output folder was enabled, Kiota client generation was throwing an error that it can't find the input swagger json file, because Kiota deletes everything in the output folder when that setting is enabled. From now on, if the setting is enabled, the swagger json file will be created in the system temp folder instead of the output folder.

</details>

<details><summary>Graceful shutdown issue of gRPC streaming</summary>

Server & Client Streaming was not listening for application shutdown which made app shutdown to wait until the streaming was finished. It has been fixed to be able to gracefully terminate the streams if the application is shutting down.

</details>

[//]: # (## Minor Breaking Changes ⚠️)

### v5.27 Release  (v5.27)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.27>

---

## ✨ Looking For Sponsors ✨

FastEndpoints needs sponsorship to [sustain the project](https://github.com/FastEndpoints/FastEndpoints/issues/449). Please help out if you can.

---

[//]: # (<details><summary>title text</summary></details>)

## New 🎉

<details><summary>Support for cancellation of queued jobs</summary>

Queuing a command as a job now returns a **Tracking Id** with which you can request cancellation of a queued job from anywhere/anytime like so:

```csharp
var trackingId = await new LongRunningCommand().QueueJobAsync();

await JobTracker<LongRunningCommand>.CancelJobAsync(trackingId);
```

Use either use the **JobTracker&lt;TCommand&gt;** generic class or inject a **IJobTracker&lt;TCommand&gt;** instance from the DI Container to access the **CancelJobAsync()** method.

**NOTE:** This feature warrants a minor breaking change. See how to upgrade below.

</details>

<details><summary>Check if app is being run in Swagger Json export mode and/or Api Client Generation mode</summary>

You can now use the following new extension methods for conditionally configuring your middleware pipeline depending on the mode the app is running in:

#### WebApplicationBuilder Extensions

```csharp
bld.IsNotGenerationMode(); //returns true if running normally
bld.IsApiClientGenerationMode(); //returns true if running in client gen mode
bld.IsSwaggerJsonExportMode(); //returns true if running in swagger export mode
```

#### WebApplication Extensions

```csharp
app.IsNotGenerationMode(); //returns true if running normally
app.IsApiClientGenerationMode(); //returns true if running in client gen mode
app.IsSwaggerJsonExportMode(); //returns true if running in swagger export mode
```

</details>

<details><summary>[AllowFileUploads] attribute for endpoint class decoration</summary>

When using attribute based configuration of endpoints you can now enable file upload support for endpoints like so:

```csharp
[HttpPost("form"), AllowFileUploads]
sealed class MyEndpoint : Endpoint<MyRequest>
{
    
}
```

</details>

<details><summary>Blazor Wasm support for Remote messaging client</summary>

A new package has been added `FastEndpoints.Messaging.Remote.Core` which contains only the core functionality along with a client that's capable of running in the web browser with Blazor Wasm.

</details>

<details><summary>Bypass endpoint throttle limits with integration tests</summary>

Integration tests can now bypass the throttle limits enforced by endpoints if they need to like so:

```csharp
[Fact]
public async Task Throttle_Limit_Bypassing_Works()
{
    var client = App.CreateClient(new()
    {
        ThrottleBypassHeaderName = "X-Forwarded-For" //must match with what the endpoint is looking for
    });

    for (var i = 0; i < 100; i++)
    {
        var (rsp, _) = await client.GETAsync<ThrottledEndpoint, Response>();
        rsp.IsSuccessStatusCode.Should().BeTrue();
    }
}
```

Each request made through that client would then automatically contain a `X-Forwarded-For` header with a unique value per request allowing the test code to bypass the throttle limits set by the endpoint.

</details>

## Improvements 🚀

<details><summary>Change default redirection behavior of cookie authentication middleware</summary>

The default behavior of the ASP.NET cookie auth middleware is to automatically return a redirect response when current user is either not authenticated or unauthorized. This default behavior is not appropriate for REST APIs because there's typically no login UI page as part of the backend server to redirect to, which results in a `404 - Not Found` error which confuses people that's not familiar with the cookie auth middleware. The default behavior has now been overridden to correctly return a `401 - Unauthorized` & `403 - Forbidden` as necessary without any effort from the developer.

</details>

<details><summary>Change 'RoleClaimType' of cookie auth to non-soap value</summary>

Until now, the `CookieAuth.SignInAsync()` method was using the long soap version of 'Role Claim Type' value `http://schemas.microsoft.com/ws/2008/06/identity/claims/role` which is not in line with what FE uses for JWT tokens. Now both JWT & Cookie auth uses the same value from the global config which is set like below or it's default value `role`:

```csharp
app.UseFastEndpoints(c=>c.Security.RoleClaimType = "role");
```

</details>

<details><summary>Workaround for CookieAuth middleware 'IsPersistent' misbehavior</summary>

By default, in ASP.NET Cookie middleware, if you specify an `Expiry` or `Max-Age` at the global/middleware level, setting `IsPersitent = false` will have no effect when signing in the user, as the middleware sets `Expiry/Max-Age` on the generated cookie anyway, making it a persistent cookie. A workaround has been implemented to fix this behavior.

</details>

## Fixes 🪲

<details><summary>[HideFromDocs] attribute missing issue with the source generator</summary>

If the consuming project didn't have a `global using FastEndpoints;` statement, the generated classes would complain about not being able to located the said attribute, which has now been rectified.

</details>

<details><summary>Service registration source generator issue with third party source generators</summary>

The service registration source generator was encountering a compatibility issue with partial classes generated by other source generators such as Mapster, which has no been fixed.

</details>

<details><summary>Swagger UI issue with path param names that are substrings</summary>

If a route contains multiple path parameters where one is a substring of another, the generated swagger spec would cause Swagger UI to not match the path param correctly. An example of this would be a route such as the following:

```
/api/parents/{ParentId}/children/{Id}
```

Path segment matching has been chan

_…truncated…_

### v5.26 Release  (v5.26)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.26>

---

## ✨ Looking For Sponsors ✨

FastEndpoints needs sponsorship to [sustain the project](https://github.com/FastEndpoints/FastEndpoints/issues/449). Please help out if you can.

---

[//]: # (<details><summary>title text</summary></details>)

## New 🎉

<details><summary>Idempotency support based on 'OutputCaching' middleware</summary>

FastEndpoints now ships with built-in endpoint [idempotency support](https://fast-endpoints.com/docs/idempotency) built around the OutputCaching middleware.

</details>

<details><summary>Specify additional Http Verbs/Methods for endpoints globally</summary>

In addition to the Verbs you specify at the endpoint level, you can now specify Verbs to be added to endpoints with the global configurator as well as endpoint groups like so:

```csharp
//global configurator
app.UseFastEndpoints(
   c => c.Endpoints.Configurator =
            ep =>
            {
                ep.AdditionalVerbs(Http.OPTIONS, Http.HEAD);
            })
    
//endpoint group
sealed class SomeGroup : Group
{
    public SomeGroup()
    {
        Configure(
            "prefix",
            ep =>
            {
                ep.AdditionalVerbs(Http.OPTIONS, Http.HEAD);
            });
    }
}
```

</details>

<details><summary>Collection-Fixture support for Testing</summary>

This release brings easy access to xUnit collection-fixtures for integration testing. Please see the [documentation](https://fast-endpoints.com/docs/integration-unit-testing#test-collections-collection-fixtures) for details.

</details>

<details><summary>Export multiple swagger json files in one go</summary>

A new overload has been added to the `ExportSwaggerJsonAndExitAsync()` method for exporting multiple Swagger Json files using the `FastEndpoints.ClientGen.Kiota` library.

```csharp
await app.ExportSwaggerJsonAndExitAsync(
    ct: default,
    c =>
    {
        c.DocumentName = "v1";
        c.DestinationPath = "/export/path";
        c.DestinationFileName = "v1.json";
    },
    c =>
    {
        c.DocumentName = "v2";
        c.DestinationPath = "/export/path";
        c.DestinationFileName = "v2.json";
    });
```

</details>

## Improvements 🚀

<details><summary>Throw meaningful exception when incorrect JWT singing algorithm is used</summary>

When creating Asymmetric JWTs, if the user forgets to change the default `SigningAlgorithm` from `HmacSha256` to something suitable for `Asymmetric` signing, a helpful exception message will be thrown instructing the user to correct the mistake. More info: #685

</details>

<details><summary>Establish SSE connection before any data is available</summary>

The SSE request would previously stay in a pending state if there was no initial data available to be sent to the client. Now the client would receive the response headers and await future data in a "connection established" state, even if no data has been received from the server.

</details>

<details><summary>Workaround for NSwag bug with nullable enum parameters</summary>

Swagger UI fails to correctly render a dropdown for nullable Enum DTO properties due to a bug in NSwag where the schema is always referenced via a `OneOf`, instead of directly referencing it with a `$ref`. A workaround has been implemented to mitigate the issue. #699

</details>

## Fixes 🪲

<details><summary>ACL source generator wasn't filtering out internal public static fields</summary>

Generated ACL incorrectly contained the `Descriptions` property in the permission dictionary items due to not being filtered out correctly, which has now been fixed.

</details>

<details><summary>Swagger generation failure due to multiple route constraints</summary>

Swagger generation was throwing an exception if an endpoint with multiple route constraints on a single parameter such as the following was encountered:

```csharp
/{member:int:min(1):max(5)}/
```

</details>

## Minor Breaking Changes ⚠️

<details><summary>Move static properties of 'ProblemDetails' class to global config</summary>

Static configuration properties that used to be on the `ProblemDetails` class will have to be set from the global configuration going forward like so:

```csharp
app.UseFastEndpoints(
   c => c.Errors.UseProblemDetails(
       x =>
       {
           x.AllowDuplicateErrors = true;  //allows duplicate errors for the same error name
           x.IndicateErrorCode = true;     //serializes the fluentvalidation error code
           x.IndicateErrorSeverity = true; //serializes the fluentvalidation error severity
           x.TypeValue = "https://www.rfc-editor.org/rfc/rfc7231#section-6.5.1";
           x.TitleValue = "One or more validation errors occurred.";
           x.TitleTransformer = pd => pd.Status switch
           {
               400 => "Validation Error",
               404 => "Not Found",
               _ => "One or more errors occurred!"
           };
       }));
```

</details>

### v5.25 Release  (v5.25)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.25>

---

## ✨ Looking For Sponsors ✨

FastEndpoints needs sponsorship to [sustain the project](https://github.com/FastEndpoints/FastEndpoints/issues/449). Please help out if you can.

---

[//]: # (<details><summary>title text</summary></details>)

## New 🎉

<details><summary>New generic attribute [Group&lt;T&gt;] for attribute based endpoint group configuration</summary>

When using attribute based endpoint configuration, you can now use the generic 'Group<TEndpointGroup>' attribute to specify the group which the endpoint belongs to like so:

```csharp
//group definition class
sealed class Administration : Group
{
    public Administration()
    {
        Configure(
            "admin",
            ep =>
            {
                ep.Description(
                    x => x.Produces(401)
                          .WithTags("administration"));
            });
    }
}

//using generic attribute to associate the endpoint with the above group
[HttpPost("login"), Group<Administration>]
sealed class MyEndpoint : EndpointWithoutRequest
{
    ...
}
```

</details>

<details><summary>Specify a label, summary & description for Swagger request examples</summary>

When specifying multiple swagger request examples, you can now specify the additional info like this:

```csharp
Summary(
    x =>
    {
        x.RequestExamples.Add(
            new(
                new MyRequest { ... },
                "label",
                "summary",
                "description"));
    });
```

</details>

<details><summary>Automatic type inference for route params from route constraints for Swagger</summary>

Given route templates such as the following that has type constraints for route params, it was previously only possible to correctly infer the type of the parameter (for Swagger spec generation) if the parameters are being bound to a request DTO and that DTO has a matching property. The following will now work out of the box and the generated Swagger spec will have the respective parameter type/format.

```csharp
sealed class MyEndpoint : EndpointWithoutRequest
{
    public override void Configure()
    {
        Get("test/{id:int}/{token:guid}/{date:datetime}");
        AllowAnonymous();
    }

    public override async Task HandleAsync(CancellationToken c)
    {
        var id = Route<int>("id");
        var token = Route<Guid>("token");
        var date = Route<DateTime>("date");

        await SendAsync(new { id, token, date });
    }
}
```

You can register your own route constraint types or even override the default ones like below by updating the Swagger route constraint map:

```csharp
FastEndpoints.Swagger.GlobalConfig.RouteConstraintMap["nonzero"] = typeof(long);
FastEndpoints.Swagger.GlobalConfig.RouteConstraintMap["guid"] = typeof(Guid);
FastEndpoints.Swagger.GlobalConfig.RouteConstraintMap["date"] = typeof(DateTime);
```

</details>

<details><summary>Form related exception transformer function setting</summary>

When accessing Form data there are various cases where an exception would be thrown internally by ASP.NET such as in the case of the incoming request body size exceeding the default limit or whatever you specify like so:

```csharp
bld.WebHost.ConfigureKestrel(
    o =>
    {
        o.Limits.MaxRequestBodySize = 30000000;
    });
```

If the incoming request body size is more than `MaxRequestBodySize`, Kestrel would automatically short-circuit the request with a `413 - Content Too Long` response, which may not be what you want. You can instead specify a `FormExceptionTrasnformer` func to transform the exception in to a regular 400 error/problem details JSON response like so:

```csharp
app.UseFastEndpoints(
       c =>
       {
           c.Errors.UseProblemDetails(); //this is optional
           c.Binding.FormExceptionTransformer =
               ex => new ValidationFailure("GeneralErrors", ex.Message);
       })
```

Which would result in a JSON response like so:

```json
{
    "type": "https://www.rfc-editor.org/rfc/rfc7231#section-6.5.1",
    "title": "One or more validation errors occurred.",
    "status": 400,
    "instance": "/upload-file",
    "traceId": "0HN39MGSS8QDA:00000001",
    "errors": [
        {
            "name": "generalErrors",
            "reason": "Request body too large. The max request body size is 30000000 bytes."
        }
    ]
}
```

</details>

<details><summary>Ability to disable WAF/SUT caching in AppFixtures</summary>

`AppFixture`'s default behavior of internally caching the SUT/WAF instance per derived `AppFixture` type can now be disabled simply by decorating the derived fixture class with an attribute like so:

```csharp

[DisableWafCache]
public class MyAppFixture : AppFixture<Program> { ... }

```

</details>

[//]: # (## Improvements 🚀)

## Fixes 🪲

<details><summary>Contention issue resulting in random 415 responses</summary>

There was a possible contention issue that could arise in an extremely niche edge case where the WAFs could be instantiated in quick succession which results in tests failing due to 415 responses being returned randomly. This has been fixed by moving the necessary work to be performed at app startup instead of at the first request for a particular endpoint. More info: #661

</details>

<details><summary>Eliminate potential contention issues with 'AppFixture'</summary>

`AppFixture` abstract class has been improved to use an Async friendly Lazy initialization technique to prevent any chances of more than a single WAF being created per each derived `AppFixture` type in high concurrent situations. Previously we were relying solely on `ConcurrentDictionary`'s thread safety features which did not always give the desired effect. Coupling that with Lazy initialization seems to solve any and all possible contention issues.

</details>

<details><summary>Correct ex

_…truncated…_

### v5.24 Release  (v5.24)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.24>

---

## ✨ Looking For Sponsors ✨

FastEndpoints needs sponsorship to [sustain the project](https://github.com/FastEndpoints/FastEndpoints/issues/449). Please help out if you can.

---

[//]: # (<details><summary>title text</summary></details>)

## New 🎉

<details><summary>Customize error response Content-Type globally</summary>
The default `content-type` header value for all error responses is `application/problem+json`. The default can now be customized as follows:

```cs
app.UseFastEndpoints(c => c.Errors.ContentType = "application/json")
```

</details>

<details><summary>'DontAutoSend()' support for 'Results&lt;T1,T2,...&gt;' returning endpoint handler methods</summary>

When putting a [post-processor in charge](https://fast-endpoints.com/docs/pre-post-processors#abstracting-response-sending-logic-into-a-post-processor) of sending the 
response, it was not previously supported when the handler method returns a `Results<T1,T2,...>`. You can now use the `DontAutoSend()` config option with such endpoint 
handlers.

</details>

<details><summary>'ProblemDetails' per instance title transformer</summary>

You can now supply a delegate that will transform the `Title` field of `ProblemDetails` responses based on some info present on the final problem details instance. 
For example, you can transform the final title value depending on the status code of the response like so:

```cs
ProblemDetails.TitleTransformer = p => p.Status switch
{
    400 => "Validation Error",
    404 => "Not Found",
    _ => "One or more errors occurred!"
};
```

</details>

<details><summary>Setting for allowing empty request DTOs</summary>

By default, an exception will be thrown if you set the `TRequest` of an endpoint to a class type that does not have any bindable properties. This behavior can now be 
turned off if your use case requires empty request DTOs.

```cs
app.UseFastEndpoints(c => c.Endpoints.AllowEmptyRequestDtos = true)
```

```cs
sealed record HelloRequest;

sealed class MyEndpoint : Endpoint<HelloRequest>
{
    public override void Configure()
    {
        Post("test");
        Description(x => x.ClearDefaultAccepts()); //this will be needed for POST requests
        AllowAnonymous();
    }
}
```

</details>

<details><summary>Ability to specify output file name with 'ExportSwaggerJsonAndExitAsync()'</summary>

It is now possible to customize the name of the exported `swagger.json` file when exporting a swagger document to disk with the `ExportSwaggerJsonAndExitAsync()` method.

</details>

## Improvements 🚀

<details><summary>Support async setup activity that contributes to WAF creation in 'AppFixture'</summary>

Previously it was not possible to do any setup activity that directly contributes to the creation of the WAF instance. Now it can be achieved like so:

```cs
using Testcontainers.MongoDb;

public class Sut : AppFixture<Program>
{
    const string Database = "TestingDB";
    const string RootUsername = "root";
    const string RootPassword = "password";

    MongoDbContainer _container = null!;

    protected override async Task PreSetupAsync()
    {
        // anything that needs to happen before the WAF is initialized can be done here.
        
        _container = new MongoDbBuilder()
                     .WithImage("mongo")
                     .WithUsername(RootUsername)
                     .WithPassword(RootPassword)
                     .WithCommand("mongod")
                     .Build();
        await _container.StartAsync();
    }

    protected override void ConfigureApp(IWebHostBuilder b)
    {
        b.ConfigureAppConfiguration(
            c =>
            {
                c.AddInMemoryCollection(
                    new Dictionary<string, string?>
                    {
                        { "Mongo:Host", _container.Hostname },
                        { "Mongo:Port", _container.GetMappedPublicPort(27017).ToString() },
                        { "Mongo:DbName", Database },
                        { "Mongo:UserName", RootUsername },
                        { "Mongo:Password", RootPassword }
                    });
            });
    }

    protected override async Task TearDownAsync()
        => await _container.DisposeAsync();
}
```

</details>

<details><summary>Automatically rewind request stream with 'IPlainTextRequest' when 'EnableBuffering()' is used.</summary>

It was not possible to manually re-read the request body stream due to `IPlainTextRequest` automatically consuming the stream even with the use of `EnableBuffering()`.
The stream will now be automatically re-wound if `EnableBuffering()` is detected in order to allow re-reading the stream by the user.

</details>

<details><summary>Filter out illegal header names from being created as request parameters in Swagger docs</summary>

According to the OpenApi Spec, there are certain header names that are not allowed as part of the regular parameter specification in the Swagger Spec. These 
Headers (`Accept`, `Content-Type` and `Authorization`) are described using other OpenApi fields. The FE Swagger generation did not previously respect/filter them out 
when processing properties marked with `[FromHeader]`.

</details>

<details><summary>'[FromBody]'attribute support for strongly-typed integration testing</summary>

There was no support for correctly integration testing an endpoint where its request DTO had a property decorated with `[FromBody]` attribute. This scenario is now 
correctly implemented and handled by the strongly-typed extension methods for the `HttpClient`.

</details>

<details><summary>Hydrate typed integration testing route url with values from request DTO</summary>

Until now, when a strongly-typed integration test calls the endpoint, it was using a faux url with the correct number of route segments so that the correct endpoint 
gets called. 

_…truncated…_

### v5.23 Release  (v5.23)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.23>

---

## ✨ Looking For Sponsors ✨

FastEndpoints needs sponsorship to [sustain the project](https://github.com/FastEndpoints/FastEndpoints/issues/449). Please help out if you can.

---

[//]: # (<details><summary>title text</summary></details>)

## New 🎉

<details><summary>Keyed service injection support</summary>

[Keyed services](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-8.0#keyed-services) introduced in .NET 8 can be injected like so:
```csharp
//property injection
[KeyedService("KeyName")]
public IHelloWorldService HelloService { get; set; }

//constructor injection
public MyEndpoint([FromKeyedServices("KeyName")]IHelloWorldService helloScv)
{
    ...
}

//manual resolving
Resolve<IHelloWorldService>("KeyName");
```

</details>

<details><summary>Model binding support for Typed Http Headers</summary>

Typed Http Headers can be bound by simply annotating with a `[FromHeader(...)]` attribute like so:

```csharp
sealed class MyRequest : PlainTextRequest
{
    [FromHeader("Content-Disposition")]
    public ContentDispositionHeaderValue Disposition { get; set; }
}
```

NOTE: Only supported on .Net 8+ and typed header classes from `Microsoft.Net.Http.Headers` namespace.

</details>

<details><summary>Ability to strip symbols from Swagger group/tag names</summary>

Given a route like:

```
/api/admin-dashboard/ticket/{id}
```

And swagger config like this:

```csharp
bld.Services.SwaggerDocument(
    o =>
    {
        o.AutoTagPathSegmentIndex = 2;
        o.TagCase = TagCase.TitleCase;
        o.TagStripSymbols = true; //this option is new
    });
```

The resulting group/tag name will be:

```
AdminDashboard
```

</details>

## Improvements 🚀

<details><summary>Better separation of concerns for integration test-classes</summary>

Previously, the recommendation was to create as many derived `TestFixture<TProgram>` classes as needed and use them as the means to share data/state among multiple test-methods of the same test-class.

A new `StateFixture` abstract class has been introduced. So that your test suit can have just a couple of "App Fixtures"(`AppFixture<TProgram>`) - each representing a uniquely configured SUT(live app/WAF instance), while each test-class can have their own lightweight "StateFixture" for the sole purpose of sharing state/data amongst multiple test-methods of that test-class.

This leads to better test run performance as each unique SUT is only created once no matter how many test classes use the same derived `AppFixture<TProgram>` class. Please re-read the [integration testing doc page](https://fast-endpoints.com/docs/integration-unit-testing#fastendpoints-testing-package) for further clarification.

</details>

<details><summary>Relax DTO type constraint on 'Validator&lt;TRequest&gt;' class</summary>

The type constraint on the `Validator<TRequest>` class has been relaxed to `notnull` so that struct type DTOs can be validated.

</details>

<details><summary>Allow TestFixture's TearDownAsync method to make Http calls</summary>

Previously the `TestFixture<TProgram>` class would dispose the default http client before executing the teardown method. This prevents cleanup code to be able to make http calls. Now the http client is only disposed after `TearDownAsync` has completed.

</details>

<details><summary>Ability to customize job queue storage provider re-check frequency</summary>

You can now customize the job queue storage provider re-check time delay in case you need re-scheduled jobs to execute quicker.

```csharp
app.UseJobQueues( 
    o => 
    { 
        o.StorageProbeDelay = TimeSpan.FromSeconds(5); 
    });
```

</details>

## Fixes 🪲

<details><summary>Swagger UI displaying random text for email fields</summary>

When a FluentValidator rule is attached to a property that's an email address, Swagger UI was displaying a random string of characters instead of showing an email address. This has been rectified.

</details>

<details><summary>Swagger generation issue with form content and empty request DTO</summary>

Endpoints configured like below, where the request dto type is `EmptyRequest` and the endpoint allows form content; was causing the swagger processor to throw an error, which has been rectified.

```csharp
sealed class MyEndpoint : EndpointWithoutRequest<MyResponse>
{
    public override void Configure()
    {
        ...
        AllowFileUploads(); 
    }
}
```

</details>

<details><summary>Swagger issue with reference type DTO props being marked as nullable</summary>

Given a DTO such as this:

```csharp
sealed class MyRequest
{
    public string PropOne { get; set; }
    public string? PropTwo { get; set; }
}
```

The following swagger spec was generated before:

```json
"parameters": [
    {
        "name": "propOne",
        "in": "query",
        "required": true,
        "schema": {
            "type": "string",
            "nullable": true //this is wrong as property is not marked nullable
        }
    },
    {
        "name": "propTwo",
        "in": "query",
        "schema": {
            "type": "string",
            "nullable": true
        }
    }
]
```

Non-nullable reference types are now correctly generated as non-nullable.

</details>

<details><summary>Swagger security processor was unable to handle Minimal Api Endpoints with Auth requirements</summary>

A NRE was being thrown when the swagger security operation processor was encountering minimal api endpoints with auth requirements.

</details>

[//]: # (## Breaking Changes ⚠️)

### v5.22 Release  (v5.22)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.22>

---

## ✨ Looking For Sponsors ✨

FastEndpoints needs sponsorship to [sustain the project](https://github.com/FastEndpoints/FastEndpoints/issues/449). Please help out if you can.

---

[//]: # (<details><summary>title text</summary></details>)

## New 🎉

<details><summary>Attribute driven response headers</summary>

Please see the [documentation](https://fast-endpoints.com/docs/misc-conveniences#attribute-driven-response-headers) for more information.

</details>

<details><summary>Allow a Post-Processor to act as the sole mechanism for sending responses</summary>

As shown in [this example](https://gist.github.com/dj-nitehawk/6e23842dcb7640b165fd80ba57967540), a post-processor can now be made the sole orchestrator of sending the
appropriate response such as in the case with the "Results Pattern".

</details>

<details><summary>Support for generic commands and command handlers</summary>

Please see the [documentation](https://fast-endpoints.com/docs/command-bus#generic-commands-handlers) for more information.

</details>

## Improvements 🚀

<details><summary>Auto resolving of Mappers in unit tests</summary>

Previously it was necessary for the user to instantiate and set the mapper on endpoints when unit testing endpoints classes. It is no longer necessary to do so
unless you want to. Existing code doesn't need to change as the `Mapper` property is still publicly settable.

</details>

<details><summary>Respect default values of constructor arguments when model binding</summary>

The default request binder will now use the default values from the constructor arguments of the DTO when instantiating the DTO before model binding starts. For
example, the `SomeOtherParam` property will have a value of `10` if no other binding sources provides a value for it.

```csharp
record MyRequest(string SomeParam,
                 int SomeOtherParam = 10);
```

</details>

<details><summary>Warn user about illegal request DTO types</summary>

FastEndpoints only supports model binding with DTOs that have publicly accessible properties. The following is not supported:

```csharp
sealed class MyEndpoint : Endpoint<Guid>
```

A more detailed `NotSupportedException` is now being thrown to make it easy to track down the offending endpoint.

</details>

<details><summary>Property naming policy was not applied to route parameters when generating Swagger spec</summary>

If you had a request DTO like this:

```csharp
sealed class MyRequest
{
    public long SomeId { get; set; }
}
```

And a route like this:

```csharp
public override void Configure()
{
    Get("/something/{someID}");
}
```

Where the case of the parameter is different, and also had a property naming policy applied like this:

```csharp
app.UseFastEndpoints(c => c.Serializer.Options.PropertyNamingPolicy = JsonNamingPolicy.KebabCaseLower)
```

Previously the Swagger spec generated would have a mismatched operation path parameter `{someID}` and a Swagger request parameter `some-id`.

Now the Swagger path parameter is correctly rendered to match with the exact value/case as the request parameter.

</details>

<details><summary>Change default output location for Kiota Api Client generation</summary>

When using `.MapApiClientEndpoint()`, previously the default value was a sub folder called `ClientGen` under the current folder. The default has been changed to a sub folder called `KiotaClientGen` in the current user's `TEMP` folder away from any project/source files, which is a much safer default location.

</details>

## Fixes 🪲

<details><summary>Type discovery source generator creating duplicates for partial classes</summary>

The type discovery source generator will now correctly detect partial classes of targets and only create a single entry. #574

</details>

<details><summary>Correct handling of Swagger request param examples</summary>

Examples for request parameters were previously rendered as strings instead of the respective primitives or json objects.

Given the DTO model (with examples as xml tags):

```csharp
sealed class MyRequest
{
    /// <example>
    /// 10
    /// </example>
    public int SomeNumber { get; set; }

    /// <example>
    /// ["blah1","blah2"]
    /// </example>
    public string[] SomeList { get; set; }

    /// <example>
    /// { id : 1000, name : "john" }
    /// </example>
    public Nested SomeClass { get; set; }

    public sealed class Nested
    {
        public int Id { get; set; }
        public Guid GuidId { get; set; }
        public string Name { get; set; }
    }
}
```

Will now be correctly rendered as follows:

```json
"parameters": [
    {
        "name": "someNumber",
        "example": 10
    },
    {
        "name": "someList",        
        "example": [
            "blah1",
            "blah2"
        ]
    },
    {
        "name": "someClass",        
        "example": {
            "id": 1000,
            "name": "john"
        }
    }
]
```

</details>

<details><summary>MinLength validator rule was not detected after a NotEmpty rule in Swagger generation</summary>

```csharp
RuleFor(r => r.Name)
    .NotEmpty()
    .MinimumLength(10); // this was not being picked up before
```

</details>

## Breaking Changes ⚠️

<details><summary>Minor behavior change of 'HttpClient' extensions when integration testing</summary>

Previous behavior of the HttpClient extension methods such as `GETAsync()`,`PUTAsync()` was to swallow any deserialization exceptions and return a default value for the `TestResult.Result` property. While this works fine for 99% of scenarios, it's not apparent for the developer why exactly it's null such as in the case of #588

From now on, if an exception occurs with deserialization on successful requests, it will not be swallowed. The test will fail with an exception.

</details>

<details><

_…truncated…_

### v5.21.2 Patch Release  (v5.21.2)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.21.2>

---

## ✨ Looking For Sponsors ✨

FastEndpoints needs sponsorship to [sustain the project](https://github.com/FastEndpoints/FastEndpoints/issues/449). Please help out if you can.

---

[//]: # (<details><summary>title text</summary></details>)

[//]: # (## New 🎉)

[//]: # (## Improvements 🚀)

## Fixes 🪲

- Unit test not calling `Configure()` method #569
- Source generators causing namespace conflict in multi-project generation

[//]: # (## Breaking Changes ⚠️)

### v5.21 Release  (v5.21)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.21>

---

## ✨ Looking For Sponsors ✨

FastEndpoints needs sponsorship to [sustain the project](https://github.com/FastEndpoints/FastEndpoints/issues/449). Please help out if you can.

---

[//]: # (<details><summary>title text</summary></details>)

## New 🎉

<details><summary>Api Client generation using Kiota</summary>

Kiota is now the recommended way to generate API Clients. Please see the [documentation](https://fast-endpoints.com/docs/swagger-support#api-client-generation) on how
to use it. The previous methods for client generation using NSwag are still valid but may be deprecated at a future point in time.

</details>

<details><summary>Attribute based Pre/Post Processor configuration</summary>

When doing simple attribute based endpoint configuration instead of using the `Configure()` method, you can now add pre/post processors to the endpoint like so:

```csharp
[HttpPost("/test"),
 PreProcessor<PreProc>,
 PostProcessor<PostProc>]
sealed class Endpoint : Endpoint<Request, Response>
{
    public override Task HandleAsync(Request r, CancellationToken c)
    {
        ...
    }
}
```

</details>

<details><summary>Ability to specify descriptions with ACL generation</summary>

You can now specify a description/xml doc summary for individual permission items when [source generating](https://fast-endpoints.com/docs/security#source-generated-access-control-lists) them. See [the documentation](https://fast-endpoints.com/docs/security#xml-doc-summaries-for-permissions) on how to use it.

</details>

<details><summary>[HideFromDocs] attribute for removing properties from Swagger schema</summary>

```csharp
sealed class MyRequest
{
    [HideFromDocs]
    public int Internal { get; set; } //this will not appear in swagger schema

    public string Name { get; set; }
}
```

</details>

## Improvements 🚀

<details><summary>Treat validation rules with conditions attached as optional properties in Swagger spec.</summary>

If a validation rule is conditional, like in the example below, that particular DTO property will be considered optional and will not be marked as required in the Swagger Schema.

```csharp
RuleFor(x => x.Id) //this property will be a required property in the swagger spec
    .NotEmpty();   //because there's no 'When(...)' condition attached to it.

RuleFor(x => x.Age) //this will be an optional property in swagger spec because
    .NotEmpty()     //'NotEmpty()' is conditional.
    .When(SomeCondition);
```

For this to work, the rules have to be written separately as above. I.e. the `.When(...)` condition must proceed immediately after the `.NotEmpty()` or `.NotNull()` rule.

</details>

<details><summary>Support for 'UrlSegmentApiVersionReader' of 'Asp.Versioning.Http'</summary>

Only the `HeaderApiVersionReader` was previously supported. Support for doing versioning based on URL segments using the `Asp.Versioning.Http` package is now working
correctly.

</details>

<details><summary>Automatically forward endpoint attribute annotations</summary>

When using attribute annotations to configure endpoints, any custom attributes were not automatically added to endpoint metadata previously. You would've had to do the following and use the `Configure()` method for configuration instead if you had some custom attributes you needed to use:

```csharp
Description(b => b.WithMetadata(new CustomAttribute()));
```

Now, all custom attributes are automatically added/forwarded to endpoint metadata when you configure endpoints using attribute annotations.

```csharp
[HttpGet("/"), CustomAttribute]
public class Endpoint : Endpoint<Request, Response>
```

**Note:** you still have to choose one of the strategies for endpoint configuration (attributes or configure method). Mixing both is not allowed.
</details>

<details><summary>Optimize source generators</summary>

All source generators were refactored to reduce GC pressure by reducing heap allocations. Allocations are now mostly done when there's actually a need to regenerate the
source code.

</details>

<details><summary>Micro optimization with 'Concurrent Dictionary' usage</summary>

Concurrent dictionary `GetOrAdd()` overload with lambda parameter seems to perform a bit better in .NET 8. All locations that were using the other overload was changed to use the overload with the lambda.

</details>

## Fixes 🪲

<details><summary>'JsonNamingPolicy.SnakeCaseLower' was causing incorrect Swagger Schema properties</summary>

Snake case policy did not exist before .NET 8, so it's usage was not accounted for in the Swagger operation processor, which has now been corrected.

</details>

[//]: # (## Breaking Changes ⚠️)

### v5.20 Release  (v5.20)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.20>

---

## ✨ Looking For Sponsors ✨

FastEndpoints needs sponsorship to [sustain the project](https://github.com/FastEndpoints/FastEndpoints/issues/449). Please help out if you can.

---

[//]: # (<details><summary>title text</summary></details>)

## New 🎉

<details><summary>Support for .Net 8.0</summary>

The project is now developed and built using .NET 8.0 while supporting .NET 6 & 7 as well. You can upgrade your existing projects simply by targeting .NET 8

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">
    <PropertyGroup>
        <TargetFramework>net8.0</TargetFramework>
     </PropertyGroup>
</Project>
```

The .NET 8 [Request Delegate Generator](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/aot/request-delegate-generator/rdg?view=aspnetcore-8.0) is not yet compatible with FastEndpoints as FE has it's own endpoint mapping and model binding system which will require a complete rewrite as a Source Generator to properly support Native AOT. We're currently investigating ways to achieve that but cannot give a timeframe on completion as it's a massive undertaking. You can see our [internal discussion](https://discord.com/channels/933662816458645504/1174563570013442098) about this matter on discord.

</details>

<details><summary>Simpler way to register Pre/Post Processors with DI support</summary>

Processors can now be configured just by specifying the type of the processor without the need for instantiating them yourself.

```cs
public class MyEndpoint : EndpointWithoutRequest
{
    public override void Configure()
    {
        ...
        PreProcessor<PreProcessorOne>();
        PreProcessor<PreProcessorTwo>();
    }
}
```

While the old **PreProcessors(...)** method continues to work, the new method automatically resolves any constructor injected dependencies without you having to manually register the processors in DI.
</details>

<details><summary>Exception handling capability for Post-Processors</summary>

Post-Processors can now handle uncaught exceptions as an alternative to an exception handling middleware.
Please see the [documentation page](https://fast-endpoints.com/docs/pre-post-processors#handling-unhandled-exceptions-with-post-processors) for details.

</details>

<details><summary>Shared state support for global Pre/Post Processors</summary>

Global Pre/Post Processors now have [shared state](https://fast-endpoints.com/docs/pre-post-processors#sharing-state) support with the following two newly added abstract types:

- GlobalPreProcessor\<TState\>
- GlobalPostProcessor\<TState\>

</details>

<details><summary>Ability to hide the error reason in the JSON response when using the default exception handler middleware</Summary>

The actual error reason can now be hidden from the client by configuring the [exception handler middleware](https://fast-endpoints.com/docs/exception-handler#unhandled-exception-handler) like so:

```cs
app.UseDefaultExceptionHandler(useGenericReason: true);
```

</details>

[//]: # (## Improvements 🚀)

## Fixes 🪲

<details><summary>Auto binding collections of form files fails after first request</summary>

An object disposed error was being thrown in subsequent requests for file collection submissions due to a flaw in the model binding logic, which has now been corrected.

</details>

<details><summary>Incorrect validation error field names when nested request DTO property has [FromBody] attribute</summary>

JSON error responses didn't correctly render the deeply nested property chain/paths when the following conditions were met:

- Request DTO has a property annotated with `[FromBody]` attribute
- The bound property is a complex object graph
- Some validation errors occur for deeply nested items

This has been fixed to correctly render the property chain of the actual item that caused the validation failure.

More info [here](https://discord.com/channels/933662816458645504/1168177198415482972).

</details>

<details><summary>Test assertions couldn't be done on ProblemDetails DTO</summary>

The `ProblemDetails` DTO properties had private setter properties preventing STJ from being able to deserialize the JSON which has now been corrected.

</details>

## Minor Breaking Changes ⚠️

<details><summary>Pre/Post Processor interface changes</summary>

Due to the Processor related new features introduced in this release, the `*ProcessAsync(...)` method signatures had to be changed. The previous arguments are still available but they have been grouped/pushed into a processor context object. The new method signatures look like the following. Migrating your existing pre/post processors shouldn't take more than a few minutes.

**PreProcessor Signature:**

```cs
sealed class MyProcessor : IPreProcessor<MyRequest>
{
    public Task PreProcessAsync(IPreProcessorContext<MyRequest> ctx, CancellationToken c)
    {
        ...
    }
}
```

**PostProcessor Signature:**

```cs
sealed class MyProcessor : IPostProcessor<MyRequest, MyResponse>
{
    public Task PostProcessAsync(IPostProcessorContext<MyRequest, MyResponse> ctx, CancellationToken c)
    {
        ...
    }
}
```

</details>

<details><summary>AddJWTBearerAuth() default claim type mapping behavior change</summary>

The `JwtSecurityTokenHandler.DefaultInboundClaimTypeMap` static dictionary is presently used by ASP.NET for mapping claim types for inbound claim type mapping. In most cases people use `JwtSecurityTokenHandler.DefaultInboundClaimTypeMap.Clear()` to not have long claim types such as `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/nameidentifier` as the claim type for the `sub` claim for example.

The default behavior has now been changed to make the claim types not use the SOAP type identifiers like above. If for some reason you'd like to revert to the old behavior, it can be achieved like so:

```csharp
.AddJWTBearerAuth("jwt_signing_key", o =

_…truncated…_

### v5.19.2 Patch Release  (v5.19.2)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.19.2>

## Fixes 🪲

<details><summary>Tests couldn't assert on 'ProblemDetails' DTO due to having private property setters</summary>

Trying to assert on properties of `ProblemDetails` when testing, STJ could not deserialize the error JSON response due to the DTO having incorrect access modifiers for public properties, which has been corrected with this patch release.

</details>

### v5.19.1 Patch Release  (v5.19.1)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.19.1>

## Fixes 🪲

<details><summary>Auto binding collections of form files fails after first request</summary>

An object disposed error was being thrown in subsequent requests for file collection submissions due to a flaw in the model binding logic, which has now been corrected.

</details>

### v5.19 Release  (v5.19)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.19>

---

## ✨ Looking For Sponsors ✨

FastEndpoints needs sponsorship to [sustain the project](https://github.com/FastEndpoints/FastEndpoints/issues/449). Please help out if you can.

---

[//]: # (<details><summary>title text</summary></details>)

## New 🎉

<details><summary>Model binding collections of 'IFormFile' from incoming form data</summary>

The following types of properties can now be automatically model bound from `file` form data fields.

```csharp
class Request
{
    public IEnumerable<IFormFile> Cars { get; set; }
    public List<IFormFile> Boats { get; set; }    
    public IFormFileCollection Jets { get; set; }
}
```

When submitting collections of form files, the incoming field names can be one of the following 3 formats:

|     | Format One | Format Two | Format Three |
|-----|------------|------------|--------------|
| # 1 | Cars       | Boats[1]   | Jets[]       |
| # 2 | Cars       | Boats[2]   | Jets[]       |

</details>

<details><summary>Multiple request examples for Swagger</summary>

Multiple examples for the request DTO can be specified by either setting the `ExampleRequest` property of the Summary class multiple times or adding to
the `RequestExamples` collection like so:

```csharp
Summary(s =>
{
    s.ExampleRequest = new MyRequest {...};  
    s.ExampleRequest = new MyRequest {...};
    s.RequestExamples.Add(new MyRequest {...});
});
```

</details>

<details><summary>Anti-forgery token validation middleware</summary>

Please see the [documentation page](https://fast-endpoints.com/docs/security#csrf-protection-for-form-submissions-antiforgery-tokens) for details of this feature.

Thank you Wàn Yǎhǔ for the [contribution](https://github.com/FastEndpoints/FastEndpoints/pull/509).

</details>

<details><summary>Support for simple validation with 'DataAnnotations'</summary>

```csharp
//enable the feature at startup.

app.UseFastEndpoints(c.Validation.EnableDataAnnotationsSupport = true;)

//decorate properties with DataAnnotations attributes

sealed class Request
{
    [Required, StringLength(10, MinimumLength = 2)]
    public string Name { get; set; }
}

//can be used together with `FluentValidations` rules

sealed class MyValidator : Validator<Request>
{
    public MyValidator()
    {
        RuleFor(x => x.Id).InclusiveBetween(10, 100);
    }
}
```

Note: there's no swagger integration for data annotations.

Thank you Wàn Yǎhǔ for the [contribution](https://github.com/FastEndpoints/FastEndpoints/pull/500).

</details>

## Improvements 🚀

<details><summary>Prevent swallowing of STJ exceptions in edge cases</summary>

If STJ throws internally after it has started writing to the response stream, those exceptions will no longer be swallowed.
This can happen in rare cases such as when the DTO being serialized has an infinite recursion depth issue.

</details>

<details><summary>Deep nested collection property name serialization support with 'AddError(expression, ...)' method</summary>

When doing a manual add error call like this:

```csharp
AddError(r => r.ObjectArray[i].Test, "Some error message");
```

Previous output was:

![](https://github.com/FastEndpoints/FastEndpoints/assets/10120072/99b866ff-30bb-4ec7-bf19-7957ecc1b882)

New output:

![](https://github.com/FastEndpoints/FastEndpoints/assets/10120072/b4d14887-bb99-4654-9e75-6fa31741f27e)

Thank you Mattis Bratland for the [contribution](https://github.com/FastEndpoints/FastEndpoints/pull/506)

</details>

<details><summary>Misc. improvements</summary>

- Upgrade dependencies to latest
- Minor internal code refactors/optimizations

</details>

## Fixes 🪲

<details><summary>Response DTO property description not being detected</summary>

When the response DTO property description was provided by a lambda expression and the respective DTO property is also decorated with `[JsonPropertyName]` attribute,
the Swagger operation processor was not correctly setting the property description in generated Swagger spec. See #511 for more details.

</details>

[//]: # (## Minor Breaking Change ⚠️)

### v5.18 Release  (v5.18)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.18>

---

## ✨ Looking For Sponsors ✨

FastEndpoints needs sponsorship to [sustain the project](https://github.com/FastEndpoints/FastEndpoints/issues/449). Please help out if you can.

---

<!-- <details><summary>title text</summary></details> -->

## New 🎉

<details><summary>Source generated DI registrations</summary>

Please see the [documentation](https://fast-endpoints.com/docs/dependency-injection#source-generated-service-registrations) for details of this feature.

</details>

<details><summary>Source generated access control lists</summary>

Please see the [documentation](https://fast-endpoints.com/docs/security#source-generated-access-control-lists) for details of this feature.

</details>

<details><summary>Ability to show deprecated endpoint versions in Swagger</summary>

By default, deprecated endpoint versions are not included in swagger docs. Now you have the choice of including/displaying them in the doc so they'll be displayed greyed out like this:

![image](https://user-images.githubusercontent.com/7043768/267551669-25eb2c56-fb55-4dfb-b3a2-847e1c55b2c7.png)

Please see [this usage example](https://gist.github.com/dj-nitehawk/c32e7f887389460c661b955d233b650d) on how to enable it.

</details>

<details><summary>Round-Robin Event delivery with gRPC</summary>

It is now possible to deliver an event to only just one of the connected remote subscribers in a round-robin fashion. Comes in handy when you need to distribute the workload among a pool of subscribers/workers and ensure that a single event is only processed by a single remote subscriber. See the [documentation](https://fast-endpoints.com/docs/remote-procedure-calls#round-robin-mode) for more info.

</details>

## Improvements 🚀

<details><summary>Ability to get rid of null-forgiving operator '!' from test code</summary>

The `TestResult<TResponse>.Result` property is no longer a nullable property. This change enables us to get rid of the null-forgiving operator `!` from our integration test code.
Existing test code wouldn't have to change. You just don't need to use the `!` to hide the compiler warnings anymore. If/when the value of the property is actually `null`, the tests will 
just fail with a NRE, which is fine in the context of test code.

</details>

<details><summary>Optimize source generator performance</summary>

The type discovery generator is now highly efficient and only generates the source when any of the target types changes or new ones are added.

</details>

<details><summary>Optimize startup routine</summary>

Authorization policy building is moved to the `MapFastEndpoints` stage avoiding the need to iterate the discovered endpoint collection twice. This also avoids any potential race conditions due to different middleware pipeline config/ordering edge cases.

</details>

## Fixes 🪲

<details><summary>Startup issue due to 'IAuthorizationService' injection</summary>

v5.16 had introduced a bug of not being able to inject `IAuthorizationService` into endpoint classes, which has now been fixed.

</details>

<details><summary>Startup type discovery issue with exclusion list</summary>

Since you can override the exclusion list by doing:

```cs
.AddFastEndpoints(o.Assemblies = new[] { typeof(SomeClass).Assembly });
```

This was not working if the assembly name didn't have a dot (.) in the namespace.  

</details>

<details><summary>Empty swagger parameter example generation</summary>

The swagger operation processor was creating an example field with an empty string when there's no example provided by the user like the following:

```json
"parameters": [
    {
    ...
    "example": ""
    }
```

</details>

<details><summary>Swagger parameter example generation with default values</summary>

The swagger operation processor was creating an example field with the default value when there's no example or `DefaultValue` provided by the user like the following:

```json
"parameters": [
    {
    ...
    "example": 0
    }
```

</details>

<details><summary>Allow customizing serialization/deserialization of Event/Command objects in Job/Event Queue storage</summary>

See [code example](https://gist.github.com/dj-nitehawk/02420788fb0a72c4be4752be8bd4c40b?permalink_comment_id=4710007#gistcomment-4710007) and related issue: #480

</details>

## Minor Breaking Change ⚠️

<details><summary>'AddFastEndpoints()' no longer calls 'AddAuthorization()'</summary>

Due to the startup optimization mentioned above, you will now be greeted with the following exception if your app is using authorization middleware:

```yaml
Unhandled exception. System.InvalidOperationException: Unable to find the required services. Please add all the required services by calling 'IServiceCollection.AddAuthorization' in the application startup code.
```

It's because `AddFastEndpoints()` used to do the `AddAuthorization()` call internally which it no longer does. Simply add this call yourself to the middleware pipeline.

</details>

### v5.17.1 Release  (v5.17.1)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.17.1>

---

### ✨ Looking For Sponsors ✨

FastEndpoints needs sponsorship to [sustain the project](https://github.com/FastEndpoints/FastEndpoints/issues/449). Please help out if you can.

---

<!-- <details><summary>title text</summary></details> -->

<!-- ### 🔖 New -->

### 🪲 Fixes

<details><summary>Auth policy not found bug</summary>

The auth policy builder was not being run when an endpoint only specifies a `Policies(...)` config call.

</details>

### 🚀 Improvements

<details><summary>Internal optimizations in 'FastEndpoints.Testing' package</summary>

- Prevent duplicate WAFs from being created for a single `TestFixture` type.

</details>

<!-- ### ⚠️ Minor Breaking Changes -->

### v5.17 Release  (v5.17)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.17>

---

### ✨ Looking For Sponsors ✨

FastEndpoints needs sponsorship to [sustain the project](https://github.com/FastEndpoints/FastEndpoints/issues/449). Please help out if you can.

---

<!-- <details><summary>title text</summary></details> -->

### 🔖 New

<details><summary>'FastEndpoints.Testing' package for convenient Integration testing</summary>

Please see the [documentation](https://fast-endpoints.com/docs/integration-unit-testing#integration-testing) for details.

</details>

<!-- ### 🚀 Improvements -->

### 🪲 Fixes

<details><summary>Example generation for swagger nullable request params</summary>

Swagger schema example was being auto generated for request parameters even if the field (DTO property) is nullable. See bug report [here](https://github.com/FastEndpoints/FastEndpoints/issues/477). Which is not the desired behavior. 

Now the examples are only auto generated if developer hasn't decorated the property with a XML example or `[DefaultValue(...)]` attribute for nullable properties.

Non-nullable properties will always get the example/default values filled in the following order: `[DefaultValue(...)]` attribute > XML Comment > Auto generated example

</details>


### ⚠️ Minor Breaking Changes

<details><summary>Type discovery source generator behavior change</summary>

The source generator no longer automatically discovers types from referenced assemblies/projects.
You now have to add the `FastEndpoints.Generator` package to each project you'd like to use type discovery with and register the discovered types per assembly like so:
```cs
builder.Services.AddFastEndpoints(o =>
{
    o.SourceGeneratorDiscoveredTypes.AddRange(MyApplication.DiscoveredTypes.All);
    o.SourceGeneratorDiscoveredTypes.AddRange(SomeClassLib.DiscoveredTypes.All);
})
```

</details>

### v5.16 Release  (v5.16)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.16>

---

### ✨ Looking For Sponsors ✨

FastEndpoints needs sponsorship to [sustain the project](https://github.com/FastEndpoints/FastEndpoints/issues/449). Please help out if you can.

---

<!-- <details><summary>title text</summary></details> -->

## 🔖 New

<details><summary>Integration testing with fake/test handlers for messaging features</summary>

Both `In-Proc` and `RPC` based messaging functionality can now be easily integration tested by registering fake/test handlers during testing. See below links for examples of each:

- [Command Bus](https://fast-endpoints.com/docs/command-bus) ([example](https://github.com/FastEndpoints/FastEndpoints/blob/fcb18db8e938fc850ea517d298ecaadd869d0f7c/Tests/IntegrationTests/FastEndpoints/CommandBusTests/CommandBusTests.cs#L73-L84))
- [Job Queues](https://fast-endpoints.com/docs/job-queues#queueing-a-job) ([example](https://github.com/FastEndpoints/Job-Queue-Demo/tree/main/Test))
- [Event Bus](https://fast-endpoints.com/docs/event-bus) ([example](https://github.com/FastEndpoints/FastEndpoints/blob/fcb18db8e938fc850ea517d298ecaadd869d0f7c/Tests/IntegrationTests/FastEndpoints/EventBusTests/EventBusTests.cs#L22-L35))
- [Event-Queue/Broker](https://fast-endpoints.com/docs/remote-procedure-calls#remote-pub-sub-event-queues) ([example](https://github.com/FastEndpoints/Event-Broker-Demo/tree/main/Test))

</details>

<details><summary>[DontRegister] attribute for skipping auto registration</summary>

Any auto discovered types (endpoints/commands/events/etc.) can be annotated with the attribute `[DontRegister]` if you'd like it to be skipped while assembly scanning for auto registration.

</details>

<details><summary>Auto instantiation of 'JsonSerializerContext' with global 'SerializerOptions'</summary>

```cs
public override void Configure()
{
    ...
    SerializerContext<UpdateAddressCtx>();
}
```

By specifying just the type of the serializer context, instead of supplying an instance as with the existing method, the context will be created using the `SerializerOptions` that you've configured at startup using the `UseFastEndpoints(...)` call.

</details>

<details><summary>Auto generation of examples for swagger request parameters</summary>

Take the following example request DTO:
```cs
sealed class MyRequest
{
    [QueryParam]
    public Nested ComplexObject { get; set; }
}

sealed class Nested
{
    [DefaultValue(100)]
    public int Id { get; set; }

    [DefaultValue("John Doe")]
    public string Name { get; set; }

    [DefaultValue(new[] { 1, 2, 3 })]
    public int[] Numbers { get; set; }
}
```

The following swagger spec `example` will now be auto generated by default:

```json
{
  "paths": {
    "/my-endpoint": {
      "get": {
        "parameters": [
          {
            "example": {
              "id": 100,
              "name": "John Doe",
              "numbers": [ 1,2,3 ]
            }
          }
        ]
      }
    }
  }
}
```

This behavior can be turned off like so:
```cs
builder.Services.SwaggerDocument(o =>
{
    o.DocumentSettings = s =>
    {
        s.GenerateExamples = false;
    };
});
```

</details>

<details><summary>NSwag serializer (Newtonsoft) customization</summary>

Since NSwag still uses Newtonsoft internally, it is sometimes necessary to register custom converters for the NewtonSoft serializer, which can now be achieved like so:

```cs
.SwaggerDocument(o =>
{
    o.NewtonsoftSettings = s =>
    {
        s.Converters.Add(new MyCustomConverter());
    };
});
```
Any other Newtonsoft settings that needs to be tuned can also be accessed via the `s` parameter.

</details>

<details><summary>Starter Project Templates</summary>

[See here](https://fast-endpoints.com/docs/scaffolding#project-scaffolding) for details about new project scaffolding with the `Template Pack`.

</details>

## 🚀 Improvements

<details><summary>Minor performance optimizations</summary>

- Job queue message pump improvements
- Startup code optimizations

</details>

<details><summary>Concurrent WAF testing</summary>

- Better thread safety of `EndpointData` when running concurrent integration tests
- Avoid potential contention issues for `Event Handlers` when integration testing

</details>

<details><summary>Unit testing improvements</summary>

- Warn user if internal `ServiceResolver` is null due to incorrect unit test setup

</details>

<details><summary>Nested type discovery for source generator</summary>

Nested endpoints were previously ignored by the type discovery [source generator](https://fast-endpoints.com/docs/configuration-settings#source-generator-based-startup). Thanks to [Tomasz Chacuk](https://github.com/FastEndpoints/FastEndpoints/pull/472) we now have a more streamlined source generator that discovers nested types as well.

</details>

## 🪲 Fixes

<details><summary>Event handler constructors being called twice</summary>

Due to an oversight in `IEnumerable` iteration, the event handler constructor was being called twice per execution. Thank you [Wahid Bitar](https://github.com/WahidBitar) for reporting it.

</details>

<details><summary>Json serializer context was not correctly copying 'JsonSerializerOptions'</summary>

`SerializerContext<TContext>()` was not properly making a copy of the global `JsonSerializerOptions` when the serializer context was being instantiated; leading to the same global options instance being bound to multiple serializer contexts, which is not supported by the SDK as of .NET 7.0.

</details>

<details><summary>Startup exception edge case</summary>

If `app.MapControllers()` call was placed before the `app.UseFastEndpoints()` call, the app would randomly throw a cryptic exception at startup. Now when this misconfiguration is detected, a clear exception would be thrown instructing the user to change the middleware order.

</details>

<!-- ## ⚠️ Minor Breaking Changes -->

### v5.15 Release  (v5.15)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.15>

---

### ✨ Looking For Sponsors ✨

FastEndpoints needs sponsorship to [sustain the project](https://github.com/FastEndpoints/FastEndpoints/issues/449). Please help out if you can.

---

<!-- <details><summary>1️⃣ some title</summary></details> -->

## 📢 New

<details><summary>Job Queues for background processing of commands</summary>

Please see the documentation [here](https://fast-endpoints.com/docs/job-queues) for details.

</details>

<details><summary>TypedResults (union type) support for endpoints</summary>

Please see the documentation [here](https://fast-endpoints.com/docs/get-started#union-type-returning-handler) for details.

</details>

<details><summary>Support for IResult via SendResultAsync() method</summary>

You can now use any `IResult` returned from `Results` static class of minimal apis.

```cs
[HttpGet("bad-result"), AllowAnonymous]
sealed class MyEndpoint : EndpointWithoutRequest
{
    public override async Task HandleAsync(CancellationToken c)
    {
        await SendResultAsync(Results.BadRequest());
    }
}
``` 

</details>

## 🚀 Improvements

<details><summary>Allow customization of in-memory event queue size</summary>

If you're are using the [default in-memory event storage providers](https://fast-endpoints.com/docs/remote-procedure-calls#event-bus-vs-event-queue), the size limit of their internal queues can now be specified like so:

```cs
InMemoryEventQueue.MaxLimit = 1000;
```
This limit is applied per queue. Each event type in the system has it's own independent queue. If there's 10 events in the system,
there will be 10X the number of events held in memory if they aren't being dequeued in a timely manner.

</details>

<details><summary>Remote messaging performance improvements</summary>

- Refactor logging to use code generated high performance logging.
- Reduce allocations for `void` commands by utilizing a static `EmptyObject` instance.

</details>

<details><summary>Event Queues internal optimizations</summary>

- Use `SemaphoreSlim`s instead of `Task.Delay(...)` for message pump

</details>

<details><summary>Misc. performance improvements</summary>

- Reduce boxing/unboxing in a few hot paths.

</details>

<!-- ### 🪲 Fixes -->

## ⚠️ Minor Breaking Changes

<details><summary>Event Queue storage provider API changes</summary>

There has been several implementation changes to the custom storage providers to provide a more user-friendly experience. Please see the updated [doc page](https://fast-endpoints.com/docs/remote-procedure-calls#reliable-event-queues-with-persistence) for the current usage.

</details>

### v5.14 Release  (v5.14)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.14>

﻿
---

### ⭐ Looking For Sponsors
FastEndpoints needs sponsorship to [sustain the project](https://github.com/FastEndpoints/FastEndpoints/issues/449). Please help out if you can.

---

### 📢 New

<details><summary>1️⃣ gRPC based Event Broker functionality</summary>

Please see the documentation [here](https://fast-endpoints.com/docs/remote-procedure-calls#event-broker-mode) for details.

</details>

<details><summary>2️⃣ Ability to subscribe to exceptions in Event Queues</summary>

Please see the documentation [here](https://fast-endpoints.com/docs/remote-procedure-calls#event-queue-error-notifications) for details.

</details>

<details><summary>3️⃣ Support for TimeProvider in FastEndpoints.Security package</summary>

You can now register your own [TimeProvider](https://learn.microsoft.com/en-us/dotnet/api/system.timeprovider) implementation in the IOC container and the `FastEndpoints.Security` package will use that implementation to obtain the current time for token creation. If no `TimeProvider` is registered, the `TimeProvider.System` default implementation is used. There's no need to wait for .NET 8.0 release since the `TimeProvider` abstract class is already in a `netstandard2.0` BCL package on nuget. #458

</details>

<details><summary>4️⃣ Support for Asp.Versioning.Http package</summary>

Please see the documentation [here](https://fast-endpoints.com/docs/api-versioning#asp-versioning-http-package-support-experimental) for details.

</details>

<details><summary>5️⃣ Visual Studio Code Extension</summary>

Thanks to [Davor Rilko](https://github.com/drilko) we now have a [VSCode Extension](https://marketplace.visualstudio.com/items?itemName=drilko.fastendpoints) for quickly scaffolding/expanding code snippets similarly to the [VS Extension](https://marketplace.visualstudio.com/items?itemName=dj-nitehawk.FastEndpoints) which has also been updated to bring the functionality up to par.

</details>

### 🚀 Improvements

<details><summary>1️⃣ Optimize Event Queue internals</summary></details>
<details><summary>2️⃣ Upgrade dependencies to latest</summary></details>

<!-- ### 🪲 Fixes -->

<!-- ### ⚠️ Minor Breaking Changes -->

<!-- <details><summary>1️⃣ some title</summary></details> -->

### v5.13 Release  (v5.13)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.13>

﻿
---

### ⭐ Looking For Sponsors
FastEndpoints needs sponsorship to [sustain the project](https://github.com/FastEndpoints/FastEndpoints/issues/449). Please help out if you can.

---

### 📢 New

<details><summary>1️⃣ Support for RPC Commands that do not return any result</summary>

Remote procedure calls via `ICommand` & `ICommandHandler<TCommand>` is now possible which the initial RPC feature did not support. Command/Handler registration is done the same way:

```cs
//SERVER
app.MapHandlers(h =>
{
    h.Register<SayHelloCommand, SayHelloHandler>();
});

//CLIENT
app.MapRemote("http://localhost:6000", c =>
{
    c.Register<SayHelloCommand>();
});

//COMMAND EXECUTION
await new SayHelloCommand { From = "mars" }.RemoteExecuteAsync();
```

</details>

<details><summary>2️⃣ Reliable remote Pub/Sub event queues</summary>

Please refer to the [documentation](https://fast-endpoints.com/docs/remote-procedure-calls#remote-pub-sub-event-queues) for details of this feature.

</details>

<!-- ### 🚀 Improvements -->

### 🪲 Fixes

<details><summary>1️⃣ Scope creation in a Validator was throwing an exception in unit tests</summary>

Validator code such as the following was preventing the validator from being unit tested via the `Factory.CreateValidator<T>()` method, which has now been fixed.

```cs
public class IdValidator : Validator<RequestDto>
{
    public IdValidator()
    {
        using var scope = CreateScope();
        var idChecker = scope.Resolve<IdValidationService>();

        RuleFor(x => x.Id).Must((id)
            => idChecker.IsValidId(id));
    }
}
```

</details>

### ⚠️ Minor Breaking Changes

<details><summary>1️⃣ RPC remote connection configuration method renamed</summary>

Due to the introduction of remote Pub/Sub messaging (see new features above), it no longer made sense to call the method `MapRemoteHandlers` as it now supports both remote handlers and event hubs.

```cs
app.MapRemoteHandlers(...) -> app.MapRemote(...)
```
</details>

### v5.12 Release  (v5.12)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.12>

﻿
---

### ⭐ Looking For Sponsors
FastEndpoints needs sponsorship to [sustain the project](https://github.com/FastEndpoints/FastEndpoints/issues/449). Please help out if you can.

---

<!-- ### ⚠️ Breaking Changes -->

### 📢 New

<details>
<summary>1️⃣ GRPC based Remote-Procedure-Calls</summary>

Please refer to the [documentation](https://fast-endpoints.com/docs/command-bus#dependency-injection) for details of this feature.
</details>

<details>
<summary>2️⃣ Unit test Endpoints that use Resolve&lt;T&gt;() methods</summary> 

It's now possible to unit test endpoints (including dependencies) that use the `Resolve<T>()` methods to resolve services from DI. This is especially helpful when resolving `Scoped` services in `Mapper` classes. Just register the services that need to be "Resolved" like so:

```cs
var ep = Factory.Create<Endpoint>(ctx =>
{
    ctx.AddTestServices(s => s.AddTransient<MyService>());
});
```
An example mapper that uses the `Resolve<T>()` method would be such as this:

```cs
public class Mapper : Mapper<Request, Response, Entity>
{
    public override Entity ToEntity(Request r)
    {
        var mySvc = Resolve<MyService>();
    }
}
```
</details>

<details>
<summary>3️⃣ Unit test Mapper & Validator classes that use Resolve&lt;T&gt;()</summary>

Mappers & Validators that use the `Resolve<T>()` methods to obtain services from the DI container can now be unit tested by supplying the necessary dependencies.

```cs
var validator = Factory.CreateValidator<AgeValidator>(s =>
{
    s.AddTransient<AgeService>();
});
```

Use `Factory.CreateMapper<TMapper>()` the same way in order to get a testable instance of a mapper.
</details>

<details>
<summary>4️⃣ Overloads for adding Claims, Roles & Permissions when creating JWT tokens</summary>

New extension method overloads have been added to make it easier to add `Roles` and `Permissions` with `params` and with tuples for `Claims` when creating JWT tokens.

```cs
var jwtToken = JWTBearer.CreateToken(
    priviledges: u =>
    {
        u.Roles.Add(
            "Manager",
            "Employee");
        u.Permissions.Add(
            "ManageUsers",
            "ManageInventory");
        u.Claims.Add(
            ("UserName", req.Username),
            ("Email", req.Email));
    });
```
</details>

### 🚀 Improvements

<details>
<summary>1️⃣ Alert which service was not registered when unit testing</summary>

The unit testing `Factory.Create<T>(...)` method will now inform which service you forgot to register if either the endpoint or one of the dependencies requires a service. In which case, you'd be registering that service like below:

```cs
var ep = Factory.Create<Endpoint>(ctx =>
{
    ctx.AddTestServices(s => s.AddScoped<ScopedSvc>());
});
```

</details>

<!-- ### 🪲 Fixes -->

### v5.11 Release  (v5.11.0)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.11.0>

﻿
---
### ⭐ Looking For Sponsors
FastEndpoints needs sponsorship to [sustain the project](https://github.com/FastEndpoints/FastEndpoints/issues/449). Please help out if you can.

---
### 📢 New
- ability to call `PublishAsync()` on a `IEvent` type without a concrete event model type [#info](https://discord.com/channels/933662816458645504/1104729873743872170)
- `.UseSwaggerGen(uiConfig: c => c.DeActivateTryItOut())` extension method to de-activate the try it out button by default.
- support for property injection with unit testing using `Factory.Create()` method #448
- extension method `httpContext.AddTestServices(...)` for cleaner test services registration with `Factory.Create()` method #448

---
### 🚀 Improvements
- prevent `UseFastEndpoints()` call overwriting the DI registered `JsonOptions` [#info](https://discord.com/channels/933662816458645504/1103132906681012295)
- ability to optionally specify a status code when using the `Throw*(404)` endpoint error short-circuit methods #450

---
### 🪲 Fixes
- swagger schema properties marked as required by a validator were not removed from the schema in some cases [#info](https://discord.com/channels/933662816458645504/1101429081830064162)

### v5.10 Release  (v5.10)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.10>

### EXPERIMENTAL
- support for `Asp.Versioning.Http` package via `FastEndpoints.AspVersioning` [#info](https://github.com/FastEndpoints/FastEndpoints/issues/352#issuecomment-1522188041)

### IMPROVEMENTS
- trim down `AddSwaggerDoc()` calls with `SwaggerDocument(Action<DocumentOptions>)`. see deprecations below & [example](https://github.com/FastEndpoints/FastEndpoints/blob/925d96ccea6e01cdee408142be1855f3baf616be/Web/Program.cs#L20-L32).
- improve `IFormFile` support in OAS2 [#info](https://discord.com/channels/933662816458645504/1101429081830064162)
- nswag operation processor internal optimizations

### DEPRECATIONS
> the following methods have been deprecated but will still work until the next major version jump. you may however want to refactor your code as shown in the [latest documentation](https://fast-endpoints.com/docs/swagger-support#enable-swagger), which will only take a few minutes.
- `FastEndpoints.Swagger.Extensions.AddSwaggerDoc()` in favor of `SwaggerDocument(Action<DocumentOptions>)`
- `FastEndpoints.Swagger.Extensions.EndpointFilter()` in favor of `DocumentOptions.EndpointFilter` property
- `FastEndpoints.Swagger.Extensions.TagDescriptions()` in favor of `DocumentOptions.TagDescriptions` property
- `FastEndpoints.Swagger.Extensions.EnableFastEndpoints()` in favor of `EnableFastEndpoints(Action<DocumentOptions>)`

### v5.9 Release  (v5.9)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.9>

### BREAKING CHANGES
- integration testing extensions (GETAsync(), POSTAsync(), etc.) no longer throws `InvalidOperationException`
> if your integration tests are doing try/catch blocks for doing assertions on the unhappy/error path, those tests would now fail. you'll have to get rid of the try/catch blocks and assert on the `HttpResponseMessage`'s properties instead. 
here's an [example](https://github.com/FastEndpoints/FastEndpoints/blob/4831acea19f8b574bf7e4ebfe390ec4138a2a7e1/Tests/IntegrationTests/FastEndpoints.IntegrationTests/WebTests/AdminTests.cs#L65-L94).

### NEW
- `ValidationContext<T>` class for manipulating the validation failures list of the current endpoint [#info](https://fast-endpoints.com/docs/validation#throwing-adding-errors-from-anywhere)
- `RFC8707` compatible problem detail (error response) builder [#info](https://fast-endpoints.com/docs/configuration-settings#rfc8707-compatible-problem-details)
- `JsonExceptionTransformer` func to enable customization of error messages when STJ throws due to invalid json input [#info](https://discord.com/channels/933662816458645504/1095670893113528370/1095923891605622884)
- `ClearDefaultProduces(200,401,401)` extension method to clear chosen produces metadata added by default [#info](https://fast-endpoints.com/docs/swagger-support#clear-only-accepts-metadata)
- `MarkNonNullablePropsAsRequired()` swagger doc extension for TS client generation with OA3 swagger definitions #388
- json array request body binding for inherited `IEnumerable<T>` request DTOs #436

### IMPROVEMENTS
- automatically add `400 - Bad Request`, `401 - Unauthorized` and `403 - Forbidden` produces metadata to endpoints by default [#info](https://fast-endpoints.com/docs/swagger-support#describe-endpoints) 
- add overload to `AddError()`, `ThrowError()`, `ThrowIfAnyErrors()` methods to accept a `ValidationFailure` [#info](https://discord.com/channels/933662816458645504/1090551226598432828/1090934715952926740)
- modify type discovery source generator for incremental generation #426 
- upgrade dependencies to latest

### FIXES
- default response serializer func overriding the `content-type` of 400 responses [#info](https://discord.com/channels/933662816458645504/1090697556549447821)
- swagger descriptions for properties decorated with `[FromHeader("...")]` not being picked up [#info](https://discord.com/channels/933662816458645504/1093846313201827940)
- swagger descriptions for inherited classes/schema not being picked up

### v5.8.1 Release  (v5.8.1)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.8.1>

### IMPROVEMENTS
- optional boolean argument `urlEncoded` for `AllowFormData()` method to accept `application/x-www-form-urlencoded` instead of `multipart/form-data` [#info](https://fast-endpoints.com/docs/model-binding#from-form-fields)
- ability to submit a request DTO as multipart form data when integration testing endpoints that accept form data. [#409](https://github.com/FastEndpoints/FastEndpoints/issues/409#issuecomment-1473758591)
- ability to execute a non-concrete `ICommand` types #411
- refactor & simplify httpclient extensions for testing 

### FIXES
- `EndpointWithMapping<TRequest, TResponse, TEntity>` map methods becoming protected in v5.8 [#info](https://discord.com/channels/933662816458645504/1082207914376319026)
- double response issue if pre-processor sent response and validator also has failures. [#info](https://discord.com/channels/933662816458645504/1080609437879914506)
- endpoint factory being inferred from request body issue [#info](https://discord.com/channels/933662816458645504/1084841217898061915)
- incorrect swagger spec generation issue [#info](https://discord.com/channels/933662816458645504/1085966972560347237)
- minor oversight in accept metadata checking/caching per endpoint on first request [#info](https://discord.com/channels/933662816458645504/1085526696406548604/1087362733021872200)

### v5.8 Release  (v5.8)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.8>

### NEW
- support for `record` types and `required` keyword by removing `new()` constraint on request DTOs
- allow command handlers to manipulate endpoint validation state [#info](https://fast-endpoints.com/docs/command-bus#manipulating-endpoint-error-state)
- ability to share state between pre/post processors and endpoint handler [#info](https://fast-endpoints.com/docs/pre-post-processors#sharing-state)
- add `Policy()` method to endpoint class for building authorization requirements per endpoint [#info](https://fast-endpoints.com/docs/security#policy-method)
- ability to automatically add produces 400 metadata for endpoints with validators [#info](https://discord.com/channels/933662816458645504/1077784720051556473)
- ability to remove optional `[FromHeaders],[FromClaim],[HasPermission]` annotated properties from swagger request schema #387
- support for `IParsable<T>` interface from .net 7.0 #385
- support for ignoring `GET` request DTO properties annotated with `[JsonIgnore]` attribute for disabling binding [#info](https://discord.com/channels/933662816458645504/1078782887756824606/1079980820581859378)

### IMPROVEMENTS
- better swagger support for OAS2.0 #390
- testing extensions now return a `TestResult<TResponse>` record instead of a value tuple
- optimize the endpoint request handler internals

### FIXES
- duplicate validator detection issue #394
- contention issue with parallel test runs #395
- `RSA` instance being disposed when using `Assymetric` JWT signing style
- handling of STJ exceptions when the error is not directly related to any field of the json payload #391

### v5.7.2 Release  (v5.7.2)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.7.2>

### IMPROVEMENTS
- add overload for `TagDescriptions()` method for adding swagger tag descriptions with tuples [#info](https://fast-endpoints.com/docs/swagger-support#swagger-operation-tags)
- swagger support for route params with mixed patterns #380
- misc. improvements to `FastEndpoints.Security` package internals
- upgrade all dependencies to latest

### v5.7.1 Release  (v5.7.1)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.7.1>

### FIXES
- .net 7 `IEndpointFilter` classes not executing correctly [#info](https://discord.com/channels/933662816458645504/1072142204862205972)
- object disposed exeception when signing with assymetric key #372
- STJ trying to bind json object as `IEnumerable` when dto prop is `IDictionary` [#info](https://discord.com/channels/933662816458645504/1069941646646595594)

### v5.7 Release  (v5.7)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.7>

### NEW
- easy cookie auth support via `FastEndpoints.Security` package [#info](https://fast-endpoints.com/docs/security#cookie-based-authentication)
- add `SendInterceptedAsync()` method to endpoint class for compatibility with `FluentResults` package #365

### IMPROVEMENTS
- auto send 415 response if endpoint specifies content-types but request doesn't have any content-type headers [#info](https://discord.com/channels/933662816458645504/955771546654359553/1070336144941797477)
- better handling of inherited `ICommandHandler` [#info](https://discord.com/channels/933662816458645504/1067599463310446592)

### FIXES
- jwt refresh token renewal privileges were not correctly set if awaiting a task in the method #368

### v5.6 Release  (v5.6)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.6>

### CHANGES
- `AddAuthenticationJWTBearer()` has been renamed to `AddJWTBearerAuth()` and signature changed [#info](https://fast-endpoints.com/docs/security#jwt-bearer-authentication)

### NEW
- customize dto property binding failure message #356
- ability to specify jwt bearer events with `AddJWTBearerAuth()` #359

### IMPROVEMENTS
- send 400 error response with json body instead of 500 exception when STJ throws #360
- not fail modelbinding if queryparam is empty and dto property is nullable [#info](https://discord.com/channels/933662816458645504/1053657195771858944)

### v5.5 Release  (v5.5)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.5>

### NEW
- jwt refresh token support [#info](https://fast-endpoints.com/docs/security#jwt-refresh-tokens)
- export swagger json file with dotnet run/ms build #348
- specify binding sources for the default request binder [#info](https://discord.com/channels/933662816458645504/1045775010226253876)

### IMPROVEMENTS
- tighten up event handling to support long-running processes
- upgrade fluentvalidations pkg to latest
- add safeguard against security policiy builder execution order change
- adjust default jwt verification clock skew to 60 seconds

### v5.4.1 Release  (v5.4.1)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.4.1>

### CHANGELOG
- upgrade nswag to latest (.net 7 support)
- fix swagger response dto property description not appearing if case not matched.

### v5.4 Release  (v5.4)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.4>

### NEW
- shortcut `app.UseSwaggerGen()` as an alternative to `app.UseOpenApi() + app.UseSwaggerUi3()`
- choose swagger tag naming strategy with `AddSwaggerDoc()` method #330
- provide descriptions for response dto properties using the endpoint summary [#info](https://github.com/vpetrusevici/Library/blob/3467e90e17c8acfb80a3c94d78d28e4ba7177949/Web/%5BFeatures%5D/TestCases/QueryObjectBindingTest/Endpoint.cs#L17-L18)

### FIXES
- roles requirement issue with attribute based config [#info](https://discord.com/channels/933662816458645504/1038735848167968798)
- bug in command handlers and scoped service resolving #324

### IMPROVEMENTS
- reduce startup time
- validate swagger startup config order
- optimize value parser functionality
- service resolver refactors

### v5.3.2 Release  (v5.3.2)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.3.2>

### FIXES
- swagger operation processor culture-info issue in docker #314

### IMPROVEMENTS
- swagger request & response example serialization
- add extension method to easily obtain `EndpointDefinition` in a nswag op-processor #311
- remove internal only code from default nswag op-processor #311
- unit testability for endpoints with createdat/linkgenerator [#info](https://github.com/FastEndpoints/FastEndpoints/blob/849d0d064b052da2da63066da4c3a4d11058610a/Tests/UnitTests/FastEndpoints.UnitTests/WebTests/UnitTests.cs#L129-L136)

### v5.3.1 Release  (v5.3.1)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.3.1>

### HOTFIX
- `IEventHandler` based event handler classes requiring a parameterless constructor #308

### IMPROVEMENTS
- remove readonly request dto properties from swagger doc #306
- capitalize first letter of swagger auto tags based on path segment
- default request binder will ignore dto props without public getter/setter

### v5.3 Release  (v5.3)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.3>

### NEW
- command bus pattern messaging [#info](https://fast-endpoints.com/docs/command-bus)
- ability to publish events from anywhere [#info](https://fast-endpoints.com/docs/event-bus#publish-from-anywhere)
- constructor injection support for event handlers [#info](https://fast-endpoints.com/docs/dependency-injection#event-handler-dependencies)
- type safety for the shortcut http verb methods such as `Get()`, `Post()`, etc. [#info](https://fast-endpoints.com/docs/misc-conveniences#strongly-typed-route-parameters)
- dependency resolving support for endpoint `Configure()` method
- custom value parser registration at startup for any given type [#info](https://fast-endpoints.com/docs/model-binding#custom-value-parsers)
- specify whether to execute global pre/post processors before or after endpoint level processors [#info](https://fast-endpoints.com/docs/pre-post-processors#global-processors)
- `[DontInject]` attribute for preventing property injection of endpoint properties
- add `Verbs(...)` overload that can take any string #299

### IMPROVEMENTS
- make `IEventHandler<TEvent>` public and remove requirement of `FastEventHandler<TEvent>`[#info](https://fast-endpoints.com/docs/event-bus#_2-define-an-event-handler)
- move attribute classes to a separate package `FastEndpoints.Attributes` [#info](https://discord.com/channels/933662816458645504/955771546654359553/1032020804671647854)
- remove read-only properties from swagger request body #283
- non-conforming DI container support #289
- remove previously deprecated scoped validator support

### FIXES
- swagger response examples not honoring serializer settings #280
- swagger request property xml examples not picked up for route params #287 
- property injection not working on sub-classes #292

### v5.2.1 Release  (v5.2.1)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.2.1>

### HOTFIX
- authorize attribute related NRE #281

### NEW
- `x.TagDescriptions()` method for swagger to supply tag descriptions #278

### v5.2 Release  (v5.2)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.2>

### CHANGES
- signature of global error response builder func has changed to include the `HttpContext` [#docs](https://fast-endpoints.com/docs/configuration-settings#customizing-error-responses)
- security related methods such as `ep.Roles(...)` in global config will now compound what's being done in the endpoint config [#docs](https://fast-endpoints.com/docs/configuration-settings#global-endpoint-options)

### NEW
- support .net 7.0 via multi targeting
- endpoint configuration with groups and sub/nested groups [#docs](https://fast-endpoints.com/docs/configuration-settings#endpoint-configuration-groups)
- complex object binding from json object strings for query/forms/claims/headers [#docs](https://fast-endpoints.com/docs/model-binding#json-objects)
- ability to filter out non-fastendpoints from swagger docs [#docs](https://fast-endpoints.com/docs/swagger-support#exluding-non-fastendpoints)
- filtering (endpoint inclusion) for swagger documents [#docs](https://fast-endpoints.com/docs/swagger-support#filtering-endpoints)
- specify endpoint summary and description with xml comments [#info](https://fast-endpoints.com/docs/swagger-support#enabling-xml-documentation)
- specify dto property level examples with xml comments #276
- specify response examples with `EndpointSummary` #205
- `[Throttle(...)]` attribute for configuring endpoints #227
- min endpoint version support for `AddSwaggerDoc()` #244
- non-conforming DI container support #243
- endpoint unit testing support for attribute based config [#docs](https://discord.com/channels/933662816458645504/1021479855130427442)
- asymmetric jwt signing support in `FastEndpoints.Security` pkg #249
- add `EndpointVersion()` method to `EndpointDefinition` for use with global config #209
- `TokenValidationParameters` config action argument for `AddAuthenticationJWTBearer()` method #268
- `HttpContext.MarkResponseStart()` and `HttpContext.ResponseStarted()` extension methods #230
- complex object binding from query parameters #238 #245 #254 #266

### FIXES
- pre/post processor collection modification bug #224
- response dto initialization not working with array types #225
- unable to instantiate validators for unit tests [#info](https://discord.com/channels/933662816458645504/1017889876521267263)
- nested schema resolving in nswag operation processor [#info](https://discord.com/channels/933662816458645504/1018565805555863572)
- concurrent test execution bug #224
- workaround for grpc wildcard route match conflict [#info](https://discord.com/channels/933662816458645504/1020806973689696388)
- plain text request fails if request contains json content type [#info](https://discord.com/channels/933662816458645504/1021819753016328253)
- NRE when publishing an event and no handlers are registered #259

### IMPROVEMENTS
- remove `notnull` constraint from `TResponse` generic argument of endpoint class
- `Logger` endpoint property now uses `ILoggerFactory` to create loggers
- apply validation rules from included/foreach validators #270
- better unit testability of endpoints with mappers [#info](https://discord.com/channels/933662816458645504/1029375558871679046)
- json object array string binding of requests from swagger ui
- optimize default request binder by reducing allocations
- better swagger schema resolving

### v5.1 Release  (v5.1)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.1>

### NEW
- global model binder support [#info](https://fast-endpoints.com/docs/model-binding#global-request-binder)
- global request binding modifier function [#info](https://fast-endpoints.com/docs/model-binding#binding-modifier-function)
- constructor injection support for mappers [#info](https://fast-endpoints.com/docs/dependency-injection#entity-mapper-dependencies)
- unit testing support for event handlers (successful execution & exceptions only) [#info](https://github.com/FastEndpoints/Library/blob/main/Tests/UnitTests/FastEndpoints.UnitTests/EventBusTests.cs)
- `DELETEAsync()` extension method for testing #216
- `AddSwaggerDoc(removeEmptySchemas:true)` parameter for removing empty schemas from swagger document [#info](https://fast-endpoints.com/docs/swagger-support#removing-empty-schema)
- startup type discovery filter #203

### FIXES
- global endpoint configurator ineffective for route prefix override and security related calls #207 [#info](https://discord.com/channels/933662816458645504/1012563507339857930)
- global configurator overriding endpoint level summary object #210 #212
- empty schema in swagger doc if under namespace [#info](https://discord.com/channels/933662816458645504/1014025472792870992)
- incorrect client generation with nswag [#info](https://discord.com/channels/933662816458645504/1014300348275499058)
- incorrect swagger doc/client generation when `[FromBody]` attribute was used [#info](https://discord.com/channels/933662816458645504/1017005911220428871)
- post processors were not executed if validation error was thrown by user code

### IMPROVEMENTS
- reworked event notification system (no api change)
- service provider scoping
- optimize default request binder
- route contraint handling and property type detection in swagger processor

### CHANGES
- deprecate ability to register validators as scoped in favor of `CreateScope()` method [#info](https://fast-endpoints.com/docs/dependency-injection#validator-dependencies)

### v5.0 Release  (v5.0)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v5.0>

### BREAKING CHANGES
this major version jump introduces some minor breaking changes to the startup configuration.
#### **1. restructured configuration**
the `Config` object structure has been re-organized and made more convenient to use.
```cs
app.UseFastEndpoints(c =>
{
    c.Serializer.Options.PropertyNamingPolicy = null;
    c.Endpoints.RoutePrefix = "api";
    c.Endpoints.ShortNames = false;
    c.Endpoints.Filter = ...
    c.Endpoints.Configurator = ...
    c.Versioning.Prefix = "V";
});
```
read the docs [here](https://fast-endpoints.com/docs/configuration-settings#customizing-functionality).

#### **2. reworked global endpoint configuration**
the `GlobalEndpointOptions` was removed in favor or `Endpoints.Configurator`. 
this will be the new place to configure globally applicable endpoint settings.
most of the same endpoint configuration methods are available for use on the `ep` (EndpointDefinition) argument as shown below:
```cs
app.UseFastEndpoints(c =>
{
    c.Endpoints.Configurator = ep =>
    {
        ep.AllowAnonymous();
        ep.Options(b => b.RequireHost("admin.domain.com"));
        ep.Description(b => b.Produces<ErrorResponse>(400));
    });
});
```
read the docs [here](https://fast-endpoints.com/docs/configuration-settings#global-endpoint-options)

### NEW
- code snippets added to visual studio extension [#info](https://fast-endpoints.com/docs/scaffolding#vs-code-snippets)
- `FastEndpoints.ClientGen` package for c# and typescript client generation with `NSwag` [#info](https://fast-endpoints.com/docs/swagger-support#api-client-generation)
- override default model binding logic by inheriting from `RequestBinder<TRequest>` class [#info](https://fast-endpoints.com/docs/model-binding#inherit-the-default-binder)
- global pre/post processor support [#info](https://fast-endpoints.com/docs/pre-post-processors#global-processors)
- `DontCatchExceptions()` method to enable custom exception handler middleware #186
- `IncludeAbstractValidators` startup flag for including validators inheriting `AbstractValidator<TRequest>` in auto registration [#info](https://fast-endpoints.com/docs/validation#abstract-validator-classes)
- `Validator<TValidafor>()` method for being explicit in the endpoint configuration [#info](https://fast-endpoints.com/docs/validation#abstract-validator-classes)
- `RequestMapper<TRequest,TEntity>` and `ResponseMapper<TResponse,TEntity>` classes [#info](https://fast-endpoints.com/docs/domain-entity-mapping#mapping-logic-in-a-separate-class)
- `EndpointWithMapper<TRequest, TMapper>` and `EndpointWithoutRequest<TResponse, TMapper>` classes #188
- `ProducesProblemFE()` extension method for `RouteHandlerBuilder` [#info](https://discord.com/channels/933662816458645504/1004762111546769498)
- ability to customize permissions claim type #187
- multiple route support for http attributes #129

### IMPROVEMENTS
- remove the `new()` contraint on response dtos so a parameterless ctor is not needed on response classes #184
- built-in unhandled exception handler now sends a response of type `InternalErrorResponse`
- `ValidationFailureException` class now has the failure details #186
- support for non-ascii chars in `Content-Disposition` header [#info](https://discord.com/channels/933662816458645504/1009356074983379004)
- warn user at start up if duplicate validators are found and user is not being explicit about which one to use #190
- increase logging in validation schema processor #117
- add jetbrains external annotations #191
- update dependencies to latest

### FIXES
- swagger schema becoming invalid overnight #173
- swagger example couldn't handle `IEnumerable` records #195
- oversight in duplicate route detection code
- minor issue in versioning system related to default version and swagger


## v4.x

### v4.4 Release  (v4.4)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v4.4>

### NEW
- doc site refresh: http://fast-endpoints.com
- custom request model binder support via `IRequetBinder<TRequest>` interface #172
- `[FromBody]` attribute for binding request json body to a dto sub property [#info](https://discord.com/channels/933662816458645504/998996342187753543/998996347925561505)
- swagger integration for `[FromBody]` attribute
- support for binding duplicate query param values to `IEnumerable` properties #165
- support for binding duplicate headers to `IEnumerable` properties
- `UpdateEntity()` method for mapper to update an entity from the request dto #167
- support for `[DefaultValue(...)]` attribute with swagger [#info](https://discord.com/channels/933662816458645504/1003942423174598656/1003942426584551514)

### FIXES
- swagger issue when `ApiController` exists in same project #163
- enum binding from route cause NRE when value is invalid or case not matched [#info](https://discord.com/channels/933662816458645504/1003272032789741621/1003272038200381560)

### v4.3.1 Release  (v4.3.1)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v4.3.1>

### FIXES
- custom `TryParse()` method precedence over JsonSerializer issue #155
- `EndpointDiscoveryOptions` not considered in `AddFastEndpoints()` #157
- `IEnumerable` property binding not allowing pre-processors to work #161
- assembly scanning blocked if user's namespaces are in exlusion list #162
- plain text request binding with `IPlainText` issue introduced in v4.3
- concurrency issue with xunit parallel test runs

### v4.3 Release  (v4.3.0)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v4.3.0>

### NEW
- endpoint discovery options argument for `AddFastEndpoints()`
- source generator support for startup type discovery #117
- http `HEAD` support #144

### IMPROVEMENTS
- support empty requests with `application/json` content type #147
- throw exception if swagger pipeline is misconfigured #122
- validator inheritance for swagger-fluentvalidation integration #126 #135 #141
- cancellation token support for hooks #134
- upgrade dependancies to latest

### FIXES
- binding duplicate claim types such as `role` #131
- not finding generic parameters of `Summary<TEndpoint,TRequest>` at startup
- model binding issue with generic request dtos #143

### CHANGES
- specifying custom assemblies at startup should now be done like: `AddFastEndpoints(o=> o.Assemblies = ...)`
- `AbstractValidator<T>` classes will no longer be auto discovered due to #140
- moved `ValidationFailureException` to `FastEndpoints` namespace. you'll have to add a `Using FastEndoints;` import statement if this class is referenced from your code.

### v4.2 Release  (v4.2.0)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v4.2.0>

### NEW
 - specify swagger example request object with the `ExampleRequest` property in endpoint summary
 - model bind json arrays from request body by doing `MyEndpoint : Endpoint<List<MyModel>>`
 - model bind `json array strings` to `IEnumerable` properties of request dtos from form fiels/query params/headers/claims #110
 - global config `ErrorResponseStatusCode` for overriding status code for validation error responses
 - fluentvalidation integration with swagger #112 #116
 - `dotnet new` template for scaffolding vertical slice feature file sets #119

 ### IMPROVEMENTS
 - structured logging for default exception handler #105
 - correctly infer and set route parameter type in swagger from dto property type #99
 - swagger `OperationProcessor` now uses `NJsonSchema.SchemaGeneratorSettings` #108
 - remove empty request schema from swagger doc #115
 - misc. swagger improvements
 - upgrade to latest fluentvalidation version
 - new optional parameters for AddError() method #120

 ### FIXES
 - swagger bug #86 solved by #109
 - fix `Query<T<()` method StringValues issue #113

### v4.1 Release  (v4.1.0)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v4.1.0>

### NEW
- complete decoupling of endpoint summaries via `Summary<TEndpoint>` abstract class
- `Response<T>()` method as an alternative to `.Produces()` method
- large file upload/reading support via `FormFileSectionsAsync()` without buffering to memory/disk #79
- `OnValidationFailed()` hook method
- ability to specify a global header name and response message for rate limiting/throttling #84
- access to `IConfiguration` from within endpoint `Configure()` method

### IMPROVEMENTS
- ability to change order of generic arguments when inheriting `Endpoint` abstract classes #95

### v4.0 Release  (v4.0.0)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v4.0.0>

### BREAKING CHANGES
- fluentvalidation code is no longer integrated. remove the package reference to `FastEndpoints.Validation` from your csproj file and add a `global using FluentValidation`. no other changes are necessary. [#70]

- the `Describe()` method has been removed. use `Description()` isntead. refer to the [doc page](https://fast-endpoints.com/wiki/Swagger-Support.html#describe-endpoints) for details. to migrate your existing code, just rename `Describe(...)` to `Description(..., clearDefaults: true)`

- `SerializerContext<T>()` has been removed. use the `SerializerContext(myContext.Default)` and provide the serializer context yourself. [#68]

- removed a previously deprecated `Summary()` overload. use one of the other `Summary()` methods if you were using the deprecated method.

### NEW
- `Configure()` method is now optional. endpoint classes can be annotated with `[HttpGet("xyz")]`,`[AllowAnonymous]`,`[Authorize(Roles="abc")]` instead if that's preferred. advanced usage however does require `Configure()` method.

- `SendEventStreamAsync()` method for doing server-sent-events streams
- `DontAutoTag()` method for ignoring auto swagger tagging based on path segment
- `[QueryParam]` attribute for marking request dto properties which are to be bound from query parameters.
- `Query<T>("xyz")` endpoint method for reading query params without a request dto [#73]

### FIXES
- serializer ctx not being set correctly [#65]
- swagger not removing json properties correctly [#69]

### IMPROVEMENTS
- nswag now uses the same serializer settings as fastendpoints by default, which is overrideable.
- optional (IsRequired=false) `[FromClaim]` and `[HasPermission]` dto properties now get transformed into query params in swagger.


## v3.x

### v3.11 Release  (v3.11.0)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v3.11.0>

### NEW
- override or disable global route prefix in endpoints via `RoutePrefixOverride()` method
- `ResponseStarted` property on endpoint class to facilitate manual response sending in non-kestrel environments
- `Description()` method with optional parameter to clear default Accepts/Produces metadata.

### CHANGES (minor breaking)
- deprecate `Describe()` method in favor of `Description()` method
- `AddSwaggerDoc` serializer settings now accepts `System.Test.Json.JsonSerializerOptions` instead of newtonsoft
- #62 set default swagger serializer casing to camel case

### IMPROVEMENTS
- all send methods will now use `HttpContext.RequestAborted` cancellation token if a token was not supplied
- lazy initialize validation failure list in base endpoint class
- stop relying on request content-length header in model binding
- swagger now honors system.text.json attributes such as `[JsonIgnore]` and [JsonPropertyName]
- swagger `[BindFrom]` attribute handling improvements
- upgrade to latest fluentvalidation code
- upgrade other dependancies to latest

### FIXES
- incorrect handling of jwt issuer/audience
- swagger replacing default response descriptions when user doesn't supply a value

### v3.10 Release  (v3.10.0)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v3.10.0>

### NEW
- add SendRedirectAsync() method
- add SendOkAsync() method from PR #51
- overload for JWTBearer.CreateToken() to supply issuer and audience
- absolute url generation support for SendCreatedAt() method

### CHANGES (minor breaking)
- #59 `SendErrorsAsync()` method now takes an optional status code
- #59 `ErrorResponseBuilder()` func is now supplied a http status code

### FIXES
- #58 test url cache issue
- response body duplication issue with http servers other than kestrel
- content-length header missing issue with cross-fetch client

### v3.9.1 Release  (v3.9.1)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v3.9.1>

### NEW
- `[HasPermission("xyz")]` attribute to model bind if user has the given permission
- endpoint discovery from additional assemblies
- relax type constraints on request/response dtos. anything with a parameterless ctor is now supported.
- enable `Route<T>()` method for all endpoint types

### CHANGES
- make `ValidationFailureException` public to aid in unit testing endpoints

### IMPROVEMENTS
- increase startup speed by late initializing request dto cache
- reduce gc pressure by converting some reference types to structs
- optimize property setter expression tree
- optimize property getter expression tree
- optimize ReqTypeCache class

### FIXES
- startup failure when endpoints are inherited with ctor args
- swagger required fromheader/fromclaim/haspermission props are removed from request body
- swagger adding request param for non-writable dto properties
- swagger handling of nullable reference types in dtos
- swagger misc. improvements in operation handler

### v3.8.1 Release  (v3.8.1)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v3.8.1>

### NEW
- ability to return the dto object by implementing `Task<TResponse> ExecuteAsync()` override

### CHANGES (non-breaking)
- `HandleAsync()` method is no longer marked as abstract. you must now implement either `HandleAsync()` or `ExecuteAsync()`

### IMPROVEMENTS
- remove startup parallelization due to occasional stability issues with di registration

### v3.8 Release  (v3.8.0)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v3.8.0>

### NEW
- ability to unit test endpoints with `Factory.Create<TEndpoint>()`
- constructor injection support for validators with `ScopedValidator()` method

### IMPROVEMENTS
- reduce startup time of large projects via parallelization

### v3.7 Release  (v3.7.0)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v3.7.0>

### NEW
- constructor injection support for endpoint DI

### CHANGES
- `EndpointRegistrationFilter` input parameter changed to `EndpointDefinition`
- `GlobalEndpointOptions` first argument changed to `EndpointDefinition`

### v3.6 Release  (v3.6.0)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v3.6.0>

### NEW
- code generator support for request/response dtos
- ability to specify global endpoint options with `GlobalEndpointOptions` setting
- `[BindFrom]` attribute for customizing form/route/query/claim/header names
- ability to model bind any type that has a `TryParse()` static method from form/route/query/claim/header

### CHANGES
- `Route<T>()` method now throws validation error by default if unsuccessful

### SWAGGER FIXES
- empty tag creation when route is root
- duplicate param issue when casing mismatched in GET requests
- empty request body when dto only contains route/query bound properties
- correct handling of route bound request body
- missing endpoint op from swagger doc when bare route is the same

### v3.5.1 Release  (v3.5.1)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v3.5.1>

### NEW
- request param descriptions via `Summary(x=>x.RequestParams(...))` method

### IMPROVEMENTS
- swagger support for generic & deeply nested generic dtos
- swagger property descriptions from xml comments
- swagger nullable params
- swagger route constraints
- hit counter optimizations
- reduce closures

### v3.5 Release  (v3.5.0)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v3.5.0>

### NEW
 - endpoint rate limiting with Throttle() method
 - header binding support for non-string type dto properties
 - claim binding support for non-string type dto properties
 - nullable property binding from query/route params
 - route param reading for EndpointWithoutRequest endpoints

 ### IMPROVEMENTS
 - relax constraints on event msg type
 - model binding value parser internals
 - route value binding internals
 - query param binding internals
 - GETAsync() http client method internals
 - optimize security policy claim/permission matching
 - micro-optimizations to reduce boxing of value types
 - multiple swagger request content type support
 - multiple swagger response content type support
 - increase test coverage

 ### FIXES
 - duplication of swagger request params when route/path params are present

### v3.4 Release  (v3.4.0)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v3.4.0>

### NEW
 - generation of short endpoint names/swagger operation ids with ShortEndpointNames setting
 - multi verb/route endpoint support for SendCreatedAtAsync() method
 - short summary support for endpoint summaries in addition to long descriptions

 ### IMPROVEMENTS
 - add more overloads of the Summary() method

 ### CHANGES (possibly breaking)
 - auto generated swagger operation ids now use endpoint class names instead of being route based
 - deprecate one of the Summary() method overloads

### v3.3 Release  (v3.3.0)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v3.3.0>

### NEW
 - specify authentication schemes per endpoint with AuthSchemes() method
 - specify multiple swagger auth schemes per document with AddAuth()
 - generation of short schema names in swagger with shortSchemaNames param
 - override the defaults for swagger set with ConfigureDefaults()

 ### CHANGES (minor breaking)
 - input type of EndpointRegistrationFilter has been changed to EndpointDefinition

 ### IMPROVEMENTS
 - populate AuthorizeAttribute endpoint metadata with roles/schemes for better swagger support
 - swagger operations will now only include relevant auth schemes if defined via AuthSchemes()
 - update fluentvalidations to latest version

### v3.2.2 Release  (v3.2.2)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v3.2.2>

### IMPROVEMENTS
- range processing internals
- header and claim binding internals
- increase test coverage

### v3.2.1 Release  (v3.2.1)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v3.2.1>

### IMPROVEMENTS
 - upgrade nswag to latest
 - support for startup.cs in lambda functions

### v3.2 Release  (v3.2.0)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v3.2.0>

### NEW
 - send file/byte/stream methods now support range requests
 - Summary() method for providing swagger descriptions
 - ability to deprecate an endpoint with Version(x, deprecateAt:y)

 ### CHANGES
 - EndpointWithoutRequest.HandleAsync() method no longer has the redundant request argument
 - swagger schema names & operation ids are now generated without underscores #38

 ### FIXES
 - fix model binding enum values #37
 - Options(x=>x.WithName(...)) is now correctly honored

### v3.1.4 Release  (v3.1.4)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v3.1.4>

### HOTFIXES
- fix #33 index-oor issue when route prefix not used

### IMPROVEMENTS
- throw error if duplicate route handlers are detected #34

### v3.1.3 Release  (v3.1.3)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v3.1.3>

### IMPROVEMENTS
- middleware pipeline misconfiguration situations #32
- enforce check for insecure endpoint configurations

### v3.1.2 Release  (v3.1.2)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v3.1.2>

### IMPROVEMENTS
- use custom middleware for executing endpoints
- misc. code refactors

### v3.1.1 Release  (v3.1.1)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v3.1.1>

### HOTFIXES
- nswag failure if project contains minimal endpoints
- endpoint version metadata being marked incorrectly

### v3.1 Release  (v3.1.0)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v3.1.0>

### IMPROVEMENTS
- optimize nswag serializer settings
- optimize default error response
- optimize default response serializer
- optimize model binding

### v3.0 Release  (v3.0.0)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v3.0.0>

### BREAKING
- switched to nswag from swashbuckle

### NEW
- endpoint versioning
- startup configuration
- global route prefixing
- exclude/filter endpoints from registration
- endpoint tagging (for filtering purposes)
- customize error responses
- customize request deserialization
- customize response serialization

### CHANGES
- allow any content-type for plain text requests
- change error response content type to "application/problem+json"

### IMPROVEMENTS
- ConfigureDefaults() for swagger ui settings
- versioning support for swagger
- tagIndex parameter for swagger
- reduce allocations in endpoint registration

### FIX
- issue #21 with swagger gen


## v2.x

### v2.20 Release  (v2.20.0)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v2.20.0>

## changelog
- add support for NSwag
- rename `FastEndpoints.Swagger` pkg to `FastEndpoints.Swashbuckle`
- remove request body for GET requests in swashbuckle
- misc. minor code changes

### v2.19.2 Release  (v2.19.2)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v2.19.2>

## changelog
- optimization of endpoint metadata retrieval
- move endpoint metadata to metadata collection
- eliminate static vars in metadata discovery

### v2.19.1 Release  (v2.19.1)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v2.19.1>

## changelog
- add SendCreatedAtAsync() method
- ability to auto send `Response` if not already sent from handler
- improve swagger integration
- misc. code refactors

### v2.18.1 Release  (v2.18.1)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v2.18.1>

## changelog
- add Describe() method for specifying openapi metadata
- optimize endpoint class property accessors
- optimize Response property of endpoint class with late init
- optimize model binding logic

### v2.17 Release  (v2.17.0)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v2.17.0>

## changelog
- support for sending responses from pre-processors
- support for fast binding of request content body
- optimize model binding
- misc. minor refactors

### v2.16 Release  (v2.16.0)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v2.16.0>

## changelog
- add EndpointWithMapping overload
- remove EndpointWithMapper overload
- optimize endpoint discovery logic
- improve di property injection logic
- improve service resolver interface
- misc. code refactors

### v2.15 Release  (v2.15.0)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v2.15.0>

## changelog
- add support for seperating mapping logic from endpoint
- refactor service resolver
- misc. code refactors

### v2.14 Release  (v2.14.0)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v2.14.0>

## changelog
- add async hook methods for endpoints
- change hook method accessors to public from protected
- add endpoint generic overload to help mapping to/from domain entities
- misc. performance optimizations
- misc. code refactors

### v2.13.1 Release  (v2.13.1)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v2.13.1>

## changelog
- add [FromHeader] attribute for binding from headers
- add swagger support for header binding
- make claimType parameter optional for [FromClaim] attribute
- optimize model binding logic

### v2.12 Release  (v2.12.0)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v2.12.0>

## changelog
- solve WAF testing contention (issue #10) - thanks @bobbyangers
- optimize endpoint discovery/registration
- optimize startup duration time measurement
- misc. minor refactors

### v2.11 Release  (v2.11.0)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v2.11.0>

## changelog
- improve endpoint discovery and registration
- upgrade project dependancies

### v2.10 Release  (v2.10.0)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v2.10.0>

## changelog
- add default global exception handler
- upgrade project dependancies
- minor code cleanups

### v2.9.1 Release  (v2.9.1)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v2.9.1>

## changelog
- upgrade dependancies to .net 6.0

### v2.9 Release  (v2.9.0)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v2.9.0>

## changelog
- add support for publishing events from anywhere      
- add startup time measurement
- improve model binding of empty json requests
- improve swagger integration
- upgrade dependancies

### v2.8.1 Release  (v2.8.1)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v2.8.1>

## changelog
- eliminate reflection use for handler execution
- eliminate reflection use for model binding
- eliminate reflection use for service bound props (DI)
- improve referenece type route binding

### v2.7.1 Release  (v2.7.1)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v2.7.1>

## changelog
- streamline model binding
- streamline validation error response
- improve swagger integration

### v2.6 Release  (v2.6.0)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v2.6.0>

## changelog
- improve swagger integration
- improve permission handling
- improve third-pary auth provider support

### v2.5 Release  (v2.5.0)
<https://github.com/FastEndpoints/FastEndpoints/releases/tag/v2.5.0>

## changelog
- change behavior of Claims() and Permissions() method to allow ANY
- add ClaimsAll() and PermissionsAll() methods to require ALL
- add more system types to route binding support
