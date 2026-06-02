# Swashbuckle.AspNetCore.SwaggerGen — release notes by major

_Generated from `https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases`. Use when answering migration questions or when a user asks what changed between versions._

## v10.x

### v10.2.1  (v10.2.1)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v10.2.1>

## What's Changed

* Update Microsoft.OpenApi to 2.7.5 to pick up fix for GHSA-v5pm-xwqc-g5wc by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3974

**Full Changelog**: https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v10.2.0...v10.2.1

### v10.2.0  (v10.2.0)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v10.2.0>

## What's Changed

* Add `MapSwaggerUI` and `MapReDoc` to support endpoint routing by @Strepto in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3822
* Bump version to 10.2.0 by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3872
* Bump swagger-ui-dist from 5.32.1 to 5.32.2 by @dependabot in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3883
* Support `HEAD` requests by @snebjorn in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3887
* Use `IAsyncSwaggerProvider` in CLI `tofile` command by @bt-Knodel in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3910
* Pin runner images by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3944
* Disable npm install scripts by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3946
* Bump redoc from 2.5.2 to 2.5.3 by @dependabot in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3967

## New Contributors

* @Strepto made their first contribution in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3822
* @snebjorn made their first contribution in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3887
* @bt-Knodel made their first contribution in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3910

**Full Changelog**: https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v10.1.7...v10.2.0

### v10.1.7  (v10.1.7)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v10.1.7>

## What's Changed

* Support custom data type for DataTypeAttribute by @tayfunyuksel in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3868

## New Contributors

* @tayfunyuksel made their first contribution in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3868

**Full Changelog**: https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v10.1.6...v10.1.7

### v10.1.6  (v10.1.6)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v10.1.6>

## What's Changed

* Fix handling of duplicate enum values for dictionaries by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3839
* Log exception when app fails to start in CLI by @ODukhno in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3853
* Fix missing OpenAPI 3.1 $ref properties by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3859
* Add description for OpenAPI schema references by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3860

## New Contributors

* @ODukhno made their first contribution in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3853

**Full Changelog**: https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v10.1.5...v10.1.6

### v10.1.5  (v10.1.5)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v10.1.5>

## What's Changed

* Bump swagger-ui-dist from 5.31.1 to 5.32.0 in /src/Swashbuckle.AspNetCore.SwaggerUI by @dependabot in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3814
* Migrate to actions/attest by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3815
* Disable secrets-outside-env audit by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3823
* Update zizmor to 1.23.1 by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3825
* Fix null examples by @jgarciadelanoceda in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3803
* Bump dependencies by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3835

**Full Changelog**: https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v10.1.4...v10.1.5

### v10.1.4  (v10.1.4)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v10.1.4>

## What's Changed

* Bump swagger-ui-dist from 5.31.0 to 5.31.1 in /src/Swashbuckle.AspNetCore.SwaggerUI by @dependabot in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3792
* Return null on example, as it was with OpenApiNull before by @jgarciadelanoceda in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3793

**Full Changelog**: https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v10.1.3...v10.1.4

### v10.1.3  (v10.1.3)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v10.1.3>

## What's Changed

* Fix null examples being represented as the string `"null"` by @jgarciadelanoceda in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3788

**Full Changelog**: https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v10.1.2...v10.1.3

### v10.1.2  (v10.1.2)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v10.1.2>

## What's Changed

* Fix browser caching behaviour by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3772
* Fix document URL serialization by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3773

**Full Changelog**: https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v10.1.1...v10.1.2

### v10.1.1  (v10.1.1)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v10.1.1>

## What's Changed

* Add cache headers to document URLs endpoint by @Copilot and @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3766

## New Contributors

* @Copilot made their first contribution in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3766

**Full Changelog**: 

https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v10.1.0...v10.1.1

### v10.1.0  (v10.1.0)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v10.1.0>

## What's Changed

### New Features

* Add public method `SchemaRepository.ReplaceSchemaId` by @bkoelman in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3708

### Bug Fixes

* Exclude inherited properties only when base added to `AllOf` by @John-Paul-R in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3692

### Miscellaneous

* Add clarifying example in migration guide to v10 by @markuspalme in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3672
* Add markdown linter by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3673
* Update dependencies by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3685
* Validate OpenAPI documents create valid C# clients by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3686
* End-to-end client validation tests by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3687
* Add NSwag client test by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3689
* Fix GitHub step summaries by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3691
* Clarify compatibility by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3694
* Update zizmor by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3695
* Suppress zizmor false-positive by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3696
* Refactor tests by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3705
* Use NuGet Trusted Publishing by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3574
* Annotate `TryLookupByType` with nullability hints by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3719
* Bump swagger-ui-dist to 5.31.0 by @dependabot in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3720

## New Contributors

* @markuspalme made their first contribution in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3672
* @John-Paul-R made their first contribution in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3692

**Full Changelog**: https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v10.0.1...v10.1.0

### v10.0.1  (v10.0.1)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v10.0.1>

## What's Changed

* Prepare for OpenAPI.NET 3.0 by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3647
* Fix exception sorting operation tags by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3652
* Improve version table by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3653
* Update migration guide by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3654

**Full Changelog**: https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v10.0.0...v10.0.1

### v10.0.0  (v10.0.0)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v10.0.0>

# Swashbuckle.AspNetCore v10.0.0

> [!IMPORTANT]  
> This release contains major breaking changes.
>
> Read our [v10 migration guide](https://github.com/domaindrivendev/Swashbuckle.AspNetCore/blob/HEAD/docs/migrating-to-v10.md) for further information.

With this release, Swashbuckle.AspNetCore adds support for generating OpenAPI 3.1 documents and for ASP.NET Core 10.

Swashbuckle.AspNetCore v10 depends on [OpenAPI.NET v2.3](https://github.com/microsoft/OpenAPI.NET/releases/tag/v2.3.0) which introduces many breaking changes to the public API surface. More information can be found in their [OpenAPI.NET v2 Upgrade Guide](https://github.com/microsoft/OpenAPI.NET/blob/main/docs/upgrade-guide-2.md).

To reduce the number of breaking behavioural changes in Swashbuckle.AspNetCore v10, generation of OpenAPI 3.1 documents is **opt-in**.
To generate OpenAPI 3.1 documents, change the OpenAPI version as shown in the code snippet below:

```csharp
app.UseSwagger(options =>
{
    options.OpenApiVersion = OpenApiSpecVersion.OpenApi3_1;
});
```

> [!TIP]
> It is strongly recommended that you upgrade to [Swashbuckle.AspNetCore v9.0.6](https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v9.0.6) **before** upgrading to v10.

> [!IMPORTANT]  
> Use of Swashbuckle.AspNetCore with the ASP.NET Core [`WithOpenApi()` method](https://learn.microsoft.com/dotnet/core/compatibility/aspnet-core/10/withopenapi-deprecated) is no longer supported.

## What's Changed

* Update README badges by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3597
* Extend NuGet package validation by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3602
* Support .NET 10 by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3283

**Full Changelog**: https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v9.0.6...v10.0.0


## v9.x

### v9.0.6  (v9.0.6)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v9.0.6>

## What's Changed

* Bump redoc from 2.5.0 to 2.5.1 by @dependabot in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3587
* Bump swagger-ui from 5.29.1 to 5.29.2 by @dependabot in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3595

**Full Changelog**: https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v9.0.5...v9.0.6

### v9.0.5  (v9.0.5)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v9.0.5>

## What's Changed

* .NET 10 preparation by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3565
* Update NuGet packages by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3573
* Fix anchors by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3577
* Bump swagger-ui-dist from 5.27.1 to 5.29.1

**Full Changelog**: https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v9.0.4...v9.0.5

### v9.0.4  (v9.0.4)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v9.0.4>

## What's Changed

* Fix incorrect `ETag` values by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3490
* Fix `Accept-Encoding` parsing by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3492
* Check `Accept-Encoding` quality by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3493
* Update xunit packages by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3500
* Add release notes configuration by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3502
* Simplify release workflow by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3503
* Bump xunit dependencies by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3508
* Update NuGet dependencies by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3513
* Remove `WebHost` usage from tests by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3517
* Fix typos by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3520
* Sign-off commits by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3526
* Add zizmor by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3528
* Fix permissions by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3529
* Bump zizmor by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3535
* Add default `$type` discriminator for `[JsonPolymorphic]` by @lilinus in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3496
* Update NuGet dependencies by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3545

## New Contributors

* @lilinus made their first contribution in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3496

**Full Changelog**: https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v9.0.3...v9.0.4

### v9.0.3  (v9.0.3)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v9.0.3>

## What's Changed

* Fix incorrect `Content-Length` for swagger-ui and Redoc static assets by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3488

**Full Changelog**: https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v9.0.2...v9.0.3

### v9.0.2  (v9.0.2)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v9.0.2>

## What's Changed

* Generate SBOM by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3468
* Compress swagger-ui and Redoc files in embedded resources with GZip by @stratosblue in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3399
* Refactor GZip compression by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3480

## New Contributors

* @stratosblue made their first contribution in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3399

**Full Changelog**: https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v9.0.1...v9.0.2

### v9.0.1  (v9.0.1)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v9.0.1>

## What's Changed

* Fix missing Swashbuckle.AspNetCore metapackage dependencies by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3460

**Full Changelog**: https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v9.0.0...v9.0.1

### v9.0.0  (v9.0.0)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v9.0.0>

📣 This release contains the following **breaking changes**:

- Drops support for `netstandard2.0` and thus .NET Framework - now only `net8.0` and `net9.0` are supported.
- Removes all public members annotated as `[Obsolete]` in previous releases.
- Removes the deprecated `--serializeasv2` option from Swashbuckle.AspNetCore.Cli, which was superseded by `--openapiversion` from version 8.0.0.

## What's Changed

* Add tests for `[Range]` and respect `ParseLimitsInInvariantCulture` property by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3448
* Fix `[Range]` behaviour by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3449
* Refactor sample websites by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3450
* Drop netstandard support by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3422

**Full Changelog**: https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v8.1.4...v9.0.0


## v8.x

### v8.1.4  (v8.1.4)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v8.1.4>

## What's Changed

* Avoid `ArgumentNullException` being thrown generating examples by @skironDotNet in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3444

**Full Changelog**: https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v8.1.3...v8.1.4

### v8.1.3  (v8.1.3)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v8.1.3>

## What's Changed

* Re-enable MyGet publishing by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3421
* Improve test reliability by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3423
* Fix conflicting Git/EditorConfig settings by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3430
* Add integration test logging by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3431
* Disable Static Web Assets by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3432
* Typo fixes by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3433
* Fix HumanizeHrefTags not working when see tag spans over multiple lines by @Focus1337 in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3435
* Revert #3377 by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3436

## New Contributors

* @Focus1337 made their first contribution in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3435

**Full Changelog**: https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v8.1.2...v8.1.3

### v8.1.2  (v8.1.2)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v8.1.2>

## What's Changed

* Update to fix Lists/Arrays of nullables not getting marked as nullable by @Scarecrow7250 in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3364
* Add build timeout by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3370
* Bump redoc to 2.5.0 by @dependabot in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3374
* Add test analytics by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3376
* Fix schema for nullable enums by @ItsVeryWindy in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3377
* [Docs] Split readme md by @peter-csala in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3405
* [Docs] Improve the formatting of documentation files by @peter-csala in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3409
* Spruce-up the READMEs by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3410
* Migrate to slnx by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3411
* Documentation refresh by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3412
* Bump swagger-ui to 5.22.0 by @dependabot in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3417

## New Contributors

* @Scarecrow7250 made their first contribution in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3364
* @ItsVeryWindy made their first contribution in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3377
* @peter-csala made their first contribution in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3405

**Full Changelog**: https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v8.1.1...v8.1.2

### v8.1.1  (v8.1.1)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v8.1.1>

## What's Changed

* Bump swagger-ui to 5.20.8 by @dependabot in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3359

**Full Changelog**: https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v8.1.0...v8.1.1

### v8.1.0  (v8.1.0)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v8.1.0>

## What's Changed

* Adopt File-scoped namespaces by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3331
* Apply analyzer suggestions by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3334
* Add cache headers for ReDoc and SwaggerUI by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3341

**Full Changelog**: https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v8.0.0...v8.1.0

### v8.0.0  (v8.0.0)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v8.0.0>

> [!IMPORTANT]  
> Swashbuckle.AspNetCore drops support for .NET 6.

Swashbuckle.AspNetCore v8.0.0 makes the following notable changes:

- Drops support for `net6.0`.
- The `netstandard2.0` TFM now depends on [ASP.NET Core 2.3](https://github.com/dotnet/announcements/issues/331) instead of ASP.NET Core 2.1.
- Updates Microsoft.OpenApi to [v1.6.23](https://github.com/microsoft/OpenAPI.NET/releases/tag/1.6.23). This update requires the use of swagger-ui [v5.19.0](https://github.com/swagger-api/swagger-ui/releases/tag/v5.19.0) or later ([v5.20.1](https://github.com/swagger-api/swagger-ui/releases/tag/v5.20.1) is included in the Swashbuckle.AspNetCore.SwaggerUI NuGet package). You may need to clear your browser's cache to pick up the latest JavaScript files for swagger-ui.
- To prepare for future support for OpenAPI 3.1 documents, deprecates the `SerializeAsV2` property by marking it as `[Obsolete]`. Users should update their code as illustrated below, depending on their use case:
    ```diff
    - options.SerializeAsV2 = true;
    + options.OpenApiVersion = Microsoft.OpenApi.OpenApiSpecVersion.OpenApi2_0;

    // or if explicitly disabling (the same as the default behaviour)
    - options.SerializeAsV2 = false;
    + options.OpenApiVersion = Microsoft.OpenApi.OpenApiSpecVersion.OpenApi3_0;
    ```
- To prepare for future support for OpenAPI 3.1 documents, the [Swashbuckle.AspNetCore.Cli](https://www.nuget.org/packages/Swashbuckle.AspNetCore.Cli) tool has deprecated the `--serializeasv2` option and logs a warning to the console. Users should update their usage as illustrated below, depending on their use case:
    ```diff
    - swagger tofile --output [output] [startupassembly] [swaggerdoc] --serializeasv2
    + swagger tofile --output [output] [startupassembly] [swaggerdoc] --openapiversion "2.0"
    ```

## What's Changed

* More reliable coverage by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3294
* Apply IDE refactoring suggestions by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3254
* .NET 10 preparation by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3285
* Move snapshots by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3314
* Snapshot OpenApiDocument as JSON by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3315
* Enable implicit usings by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3316
* Drop .NET 6 by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3183
* Deprecate `SerializeAsV2` by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3286
* Improve release automation by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3317
* Bump NuGet packages by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3319

**Full Changelog**: https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v7.3.2...v8.0.0


## v7.x

### v7.3.2  (v7.3.2)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v7.3.2>

## What's Changed

* Fix humanize for multiline `code` and `<para>` tags by @EvgeniyZ in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3295
* Fix `DescribeAllParametersInCamelCase` usage for parameters by @maksim-sovkov in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3309

## New Contributors

* @maksim-sovkov made their first contribution in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3309

**Full Changelog**: https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v7.3.1...v7.3.2

### v7.3.1  (v7.3.1)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v7.3.1>

## What's Changed

* Fix for ApiDescriptionProvider throws NRE by @EvgeniyZ in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3280
* Bump swagger-ui-dist from 5.19.0 to 5.20.0 by @dependabot in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3279

**Full Changelog**: https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v7.3.0...v7.3.1

### v7.3.0  (v7.3.0)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v7.3.0>

## What's Changed

* Add `CreateFromJson` options overload by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3218
* Stop testing with .NET 6 by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3219
* Replace IdentityServer4 with Duende.IdentityServer (#3008) by @pseudometalhead in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3184
* Fix JWT version for .NET 9 by @Saibamen in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3227
* Adjust readme for issue #1014 by @EvgeniyZ in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3233
* Humanize multiline para tag by @EvgeniyZ in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3234
* Humanize multi line code tag by @EvgeniyZ in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3239
* Fix `JsonSerializerDataContractResolver` so that it handles jagged arrays correctly by @ozziepeeps in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3245
* Use `DeepObject` parameter style for dictionary by @EvgeniyZ in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3241
* Remove `MvcOptions` from `SchemaGenerator` by @EvgeniyZ in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3242
* Optional EOL for XML comments (#2947) by @RainDance74 in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3255
* Add support for listing available OpenAPI documents by @rassilon in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3263
* Bump swagger-ui-dist from 5.18.3 to 5.19.0 by @dependabot in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3266

## New Contributors

* @pseudometalhead made their first contribution in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3184
* @RainDance74 made their first contribution in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3255
* @rassilon made their first contribution in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3263

**Full Changelog**: https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v7.2.0...v7.3.0

### v7.2.0  (v7.2.0)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v7.2.0>

## What's Changed

* Path grouping strategy by @Saibamen in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3152
* Add package README by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3178
* Allow no match to be found to avoid throwing an exception by @moni-dips in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3188

## New Contributors

* @moni-dips made their first contribution in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3188

**Full Changelog**: https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v7.1.0...v7.2.0

### v7.1.0  (v7.1.0)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v7.1.0>

## What's Changed

* Update some nugets by @Saibamen in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3143
* Recreate package lock files by @Saibamen in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3146
* More asserts for `SwaggerGeneratorTests` by @Saibamen in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3147
* Add more HTTP codes to `ResponseDescriptionMap` by @Saibamen in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3148
* Test more WebAPI examples by @Saibamen in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3149
* Fix issue with `[FromForm]` and enums for Controllers by @jgarciadelanoceda in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3164
* Support `[Description]` and `[ReadOnly]` by @jgarciadelanoceda in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3162
* Second level inheritance for `UseOneOfForPolymorphism` by @k0ka in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3155
* Avoid exception checking nullability by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3119
* Fix `NotSupportedException` in AoT test project by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3171
* Create `snupkg` files by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3168
* Support of `[JsonPolymorphic]` and `[JsonDerivedType]` attributes by @k0ka in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3170

## New Contributors

* @k0ka made their first contribution in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3155

**Full Changelog**: https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v7.0.0...v7.1.0

### v7.0.0  (v7.0.0)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v7.0.0>

## What's Changed

* Refactor filter descriptor type checks in SwaggerGen by @iskandersierra in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3125
* Apply SwaggerIgnore on Newtonsoft by @jgarciadelanoceda in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3134
* Support .NET 9 by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3007
* Drop support for .NET (Core) versions prior to 8 (except 6) by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3007
* Fix FromForm without WithOpenApi schemas by @jgarciadelanoceda in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3133

## New Contributors
* @iskandersierra made their first contribution in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3125

**Full Changelog**: https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v6.9.0...v7.0.0


## v6.x

### v6.9.0  (v6.9.0)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v6.9.0>

## What's Changed

* Generate Properties whenever there are objects without schema(Not onl… by @jgarciadelanoceda in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3095
* fix: Pass props to multi targeting by @xC0dex in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3107
* Types with TryParse must be set with type string by @jgarciadelanoceda in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3108
* Add native AoT support for ReDoc by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3088

## New Contributors

* @xC0dex made their first contribution in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3107

**Full Changelog**: https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v6.8.1...v6.9.0

### v6.8.1  (v6.8.1)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v6.8.1>

## What's Changed

* Fix issue when applying filters for WithOpenApi extension by @jgarciadelanoceda in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3085

**Full Changelog**: https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v6.8.0...v6.8.1

### v6.8.0  (v6.8.0)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v6.8.0>

## What's Changed

* Added dependency injection/easy registration for async filters by @tofi92 in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3030
* Improve IncludeXmlComments performance (2) by @mus65 in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3044
* Apply ParameterFilters and RequestBodyFilters for WithOpenApi endpoints by @jgarciadelanoceda in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3059
* Swagger plugins support by @jvmlet in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3056
* Add benchmarks project by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3050
* Fix NuGet badge by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3064
* SwaggerGen - Improved handling of dictionaries with enum key by @flarestudiopl in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3068
* Fix typo by @tom-star119 in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3073
* Do not fill the RequestBody description with the first parameter of a… by @jgarciadelanoceda in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3076

## New Contributors

* @tofi92 made their first contribution in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3030
* @mus65 made their first contribution in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3044
* @jvmlet made their first contribution in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3056
* @flarestudiopl made their first contribution in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3068
* @tom-star119 made their first contribution in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3073

**Full Changelog**: https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v6.7.3...v6.8.0

### v6.7.3  (v6.7.3)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v6.7.3>

## What's Changed

* Fix nested types nullable context check by @VladimirTyrin in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3043
* Use NullabilityInfoContext to determine if member is nullable by @patrikwlund in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3046

## New Contributors
* @VladimirTyrin made their first contribution in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3043

**Full Changelog**: https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v6.7.2...v6.7.3

### v6.7.2  (v6.7.2)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v6.7.2>

## What's Changed

* Use NullabilityInfoContext to determine dictionary value nullability by @patrikwlund in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3041

**Full Changelog**: https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v6.7.1...v6.7.2

### v6.7.1  (v6.7.1)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v6.7.1>

## What's Changed
* docs: Update README.md by @WeihanLi in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3002
* Support `[DataMember]` `IsRequired` in `NewtonsoftDataContractResolver` by @ouvreboite in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2644
* Add API analysers by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3003
* Update README by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3004
* docs: fix example code formatting by @WeihanLi in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3010
* Fixes nullability problems with dictionaries by @ozziepeeps in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3023
* Fix handling of nullable structs by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3015
* Fix missing form parameter XML documentation by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/3020

## New Contributors
* @ouvreboite made their first contribution in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2644

**Full Changelog**: https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v6.7.0...v6.7.1

### v6.7.0  (v6.7.0)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v6.7.0>

## What's Changed

* Allow Swagger UI CSS and JS paths to be configurable by @mag1art in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2908
* Add `IncludeXmlCommentsForAssembly()` convience overload by @leotsarev in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2909
* Add snapshot tests using Verify by @keahpeters in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2929
* Add posibility to ignore properties in `[FromForm]` with `[SwaggerIgnore]` by @jgarciadelanoceda in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2928
* Adding check for existing directory and creating if doesn't exist by @matt-lethargic in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2927
* Default null value on nullable types caused errors by @jgarciadelanoceda in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2941
* Add additional Verify tests by @keahpeters in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2950
* Only apply a SchemaFilter to create the description on SwaggerUI by @jgarciadelanoceda in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2943
* Add support for async filters by @mauve in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2938
* Fix package validation by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2926
* Adding support for .NET 8 Model State attributes by @jgarciadelanoceda in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2958
* Only set Exclusive Range when they are by @jgarciadelanoceda in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2960
* `[AsParameters]` throwing error on cast when showing the description with `EnableAnnotations()` by @jgarciadelanoceda in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2962
* Fix `RequestBodyFilterAnnotation` and `MultipleFromForm` for Minimal APIs  by @jgarciadelanoceda in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2963
* Swagger UI refactoring by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2942
* Add help wanted badge by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2911
* Move inline css and js to external files for SwaggerUI and ReDoc by @junior-santana in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2965
* Missing properties section when generating `IFomFile`/`IFormFileCollection` by @jgarciadelanoceda in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2972
* Missing Encoding and RequiredProperties when `IFormFile` with OpenAPI by @jgarciadelanoceda in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2979
* Use `ApiParameter.Type` by @jgarciadelanoceda in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2980
* Document arrays of generic parameters with XML comments and support overload methods by @jgarciadelanoceda in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2982
* Take into account [JsonRequired] for System.Text.Json by @jgarciadelanoceda in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2988
* Configure non-nullable types as required by @AntiGuideAkquinet in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2803
* Use `HttpMethods.IsGet()` by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2971

## New Contributors

* @mag1art made their first contribution in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2908
* @jgarciadelanoceda made their first contribution in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2928
* @matt-lethargic made their first contribution in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2927
* @mauve made their first contribution in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2938
* @junior-santana made their first contribution in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2965
* @AntiGuideAkquinet made their first contribution in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2803

**Full Changelog**: https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v6.6.2...v6.7.0

### v6.6.2  (v6.6.2)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v6.6.2>

## What's Changed

* Fix to make required and nullable properties nullable in schema by @keahpeters in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2879
* Update Swagger UI section in README by @cremor in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2883
* Add support for the `[Length]`attribute. by @satma0745 in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2882
* Existing output file should be deleted/overwritten by @patrikwlund in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2886
* Fix libraries being handled as test projects by @patrikwlund in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2898
* Avoid competing swagger generation during test build by @patrikwlund in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2897
* Replace `<br />`, `<br/>`, and `<br>` in XML comments with `Environment.Newline` by @mburumaxwell in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2899
* Fix schema generation for c#9 positional record with param tag without example property creating unexpected empty example by @stb-co in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2901
* Fix serialization of `AdditionalItems` by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2890
* Disable parallel build by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2894
* Do not run `IHostedService` implementations by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2880
* Fix interceptor JSON casing by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2907
* Fix generation when `[DefaultValue]`'s type differs by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2895

## New Contributors

* @satma0745 made their first contribution in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2882
* @patrikwlund made their first contribution in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2886
* @stb-co made their first contribution in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2901

**Full Changelog**: https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v6.6.1...v6.6.2

### v6.6.1  (v6.6.1)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v6.6.1>

## What's Changed

* Modernise build and migrate to GitHub Actions for CI by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2775
* Update Redoc spelling in docs by @Quppa in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2568
* C# 9 Record - Read example/summary from positional record by @pixellos in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2546
* Grammatical correction of some comments by @mokarchi in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2768
* Update README.md for nested types custom schemaId support by @antmeehan in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2746
* Add support for `WithSummary` and `WithDescription` metadata by @hwoodiwiss in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2414
* Update README.md - Fix `Add Security Definitions and Requirements for Bearer auth` URL by @Saibamen in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2705
* Replace <see href="link">text</see> with Markdown link format by @mburumaxwell in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2392
* Add support for required keyword by @keahpeters in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2810
* Resolves #2717 by @MerickOWA in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2718
* Observe the route template constraints in the Swagger middleware by @0xced in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2418
* Added Swashbuckle.AspNetCore.Annotations.SwaggerIgnoreAttribute by @jcracknell in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2610
* Fix schema generation with allOf inheritance by @bkoelman in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2815
* avoid triple enumeration of formParameters by @SimonCropp in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2823
* reduce some linq allocation by @SimonCropp in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2819
* remove some duplicate dictionary lookups by @SimonCropp in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2822
* remove redundant any check in InferRequestContentTypes by @SimonCropp in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2824
* Correctly respect interfaces in `GetInheritanceChain` by @angelaki in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2826
* Generate Enum-Dictionary-Keys (analogous to Newtonsoft) by @angelaki in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2825
* Fix build badge by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2782
* Fix preview package versions by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2783
* Handle Stream and PipeReader content types correctly by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2784
* Add NuGet package READMEs by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2808
* Bump redoc to 2.1.3 by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2807
* Sort system usings first by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2790
* Throw if unsupported HTTP method used by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2797
* Fix configuration properties not being copied by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2796
* Add security policy by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2785
* Bump Microsoft.OpenApi by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2795
* Update to Swagger UI v5 by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2806
* Add customized document serialization support by @remcolam in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2677
* Added documentation for ISwaggerDocumentSerializer by @remcolam in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2837
* Fix flaky tests by locking on the statup type by @remcolam in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2838
* #2765 Allow Filter instance reuse by @remcolam in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2839
* Throw an error when a user uses FromForm attribute with IFormFile in … by @nikunjbhargava in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2840
* Filter illegal header fields by @keahpeters in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2842
* Fix handling of FileResult's with content types by @IGx89 in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2841
* Adding additional responses when 5XX errors are thrown. by @say25 in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2852
* Fix that XML comment examples do not show up if the type is string and the example contains quotation marks by @dldl-cmd in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2727
* Exclude unused Swagger-UI files by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2851
* Fix RequestBodyFilters not being deep copied by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2850
* Avoid GitHub step summary file write conflicts by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2848
* Extend built-in supported types by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2804
* Update compatibility table by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2856
* Add GitHub issue and PR templates by @martincostello in https://github.com/domaindrivendev/

_…truncated…_

### v6.6.0  (v6.6.0)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v6.6.0>

## What's Changed

* Modernise build and migrate to GitHub Actions for CI by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2775
* Update Redoc spelling in docs by @Quppa in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2568
* C# 9 Record - Read example/summary from positional record by @pixellos in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2546
* Grammatical correction of some comments by @mokarchi in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2768
* Update README.md for nested types custom schemaId support by @antmeehan in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2746
* Add support for `WithSummary` and `WithDescription` metadata by @hwoodiwiss in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2414
* Update README.md - Fix `Add Security Definitions and Requirements for Bearer auth` URL by @Saibamen in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2705
* Replace <see href="link">text</see> with Markdown link format by @mburumaxwell in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2392
* Add support for required keyword by @keahpeters in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2810
* Resolves #2717 by @MerickOWA in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2718
* Observe the route template constraints in the Swagger middleware by @0xced in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2418
* Added Swashbuckle.AspNetCore.Annotations.SwaggerIgnoreAttribute by @jcracknell in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2610
* Fix schema generation with allOf inheritance by @bkoelman in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2815
* avoid triple enumeration of formParameters by @SimonCropp in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2823
* reduce some linq allocation by @SimonCropp in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2819
* remove some duplicate dictionary lookups by @SimonCropp in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2822
* remove redundant any check in InferRequestContentTypes by @SimonCropp in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2824
* Correctly respect interfaces in `GetInheritanceChain` by @angelaki in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2826
* Generate Enum-Dictionary-Keys (analogous to Newtonsoft) by @angelaki in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2825
* Fix build badge by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2782
* Fix preview package versions by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2783
* Handle Stream and PipeReader content types correctly by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2784
* Add NuGet package READMEs by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2808
* Bump redoc to 2.1.3 by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2807
* Sort system usings first by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2790
* Throw if unsupported HTTP method used by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2797
* Fix configuration properties not being copied by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2796
* Add security policy by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2785
* Bump Microsoft.OpenApi by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2795
* Update to Swagger UI v5 by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2806
* Add customized document serialization support by @remcolam in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2677
* Added documentation for ISwaggerDocumentSerializer by @remcolam in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2837
* Fix flaky tests by locking on the statup type by @remcolam in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2838
* #2765 Allow Filter instance reuse by @remcolam in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2839
* Throw an error when a user uses FromForm attribute with IFormFile in … by @nikunjbhargava in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2840
* Filter illegal header fields by @keahpeters in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2842
* Fix handling of FileResult's with content types by @IGx89 in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2841
* Adding additional responses when 5XX errors are thrown. by @say25 in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2852
* Fix that XML comment examples do not show up if the type is string and the example contains quotation marks by @dldl-cmd in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2727
* Exclude unused Swagger-UI files by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2851
* Fix RequestBodyFilters not being deep copied by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2850
* Avoid GitHub step summary file write conflicts by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2848
* Extend built-in supported types by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2804
* Update compatibility table by @martincostello in https://github.com/domaindrivendev/Swashbuckle.AspNetCore/pull/2856
* Add GitHub issue and PR templates by @martincostello in https://github.com/domaindrivendev/

_…truncated…_

### v6.5.0  (v6.5.0)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v6.5.0>

[Changes since v6.4.0](https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v6.4.0...v6.5.0)

### v6.4.0  (v6.4.0)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v6.4.0>

[Changes since v6.3.0](https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v6.3.0...v6.4.0)

### v6.3.1  (v6.3.1)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v6.3.1>

[Changes since `v6.3.0`](https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v6.3.0...v6.3.1)

### v6.3.0  (v6.3.0)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v6.3.0>

[Changes since `v6.2.3`](https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v6.2.3...v6.3.0)

### v6.2.3  (v6.2.3)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v6.2.3>

[Changes since `v6.1.3`](https://github.com/domaindrivendev/Swashbuckle.AspNetCore/compare/v6.1.3...v6.2.3)

### v6.1.3  (v6.1.3)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v6.1.3>

_No release notes._

### v6.1.0  (v6.1.0)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v6.1.0>

_No release notes._

### v6.0.0  (v6.0.0)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v6.0.0>

This release includes a number of small enhancements and bug fixes. See the following for a full list of issues addressed:
https://github.com/domaindrivendev/Swashbuckle.AspNetCore/milestone/16?closed=1

__Of note, these include:__
- include discriminator metadata in base schema if _either_ UseOneOfForPolymorphism OR UseAllOfForInheritance are enabled
- remove fragile logic around X-Forwarded-* headers in favor of MS's Forwarded Headers Middleware (*see breaking changes)
- beta (opt-in) support for non-nullable reference types
- enhancements to SwaggerSchemaAttribute incl. use on Enum types & ability to set Nullable flag explicitly
- wrap generator exceptions to surface contextual info for troubleshooting
- support JSON object/array syntax in XML <example> tags
- improved handling for enum default values to reflect serializer behavior more accurately
- upgrade swagger-ui to 3.40.0

__Breaking Changes__
- the _obsolete_ settings `DescribeAllEnumsAsStrings` and `DescribeStringEnumsInCamelCase` are now fully removed
- X-Forwarded-* headers are no longer honored within SB code - use [MS's Forwarded Headers Middleware](https://github.com/domaindrivendev/Swashbuckle.AspNetCore#working-with-reverse-proxies-and-load-balancers) instead


## v5.x

### v5.6.0  (v5.6.0)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v5.6.0>

This release includes a number of small enhancements and bug fixes. See the following for a full list of issues addressed:
https://github.com/domaindrivendev/Swashbuckle.AspNetCore/milestone/15?closed=1

Of note, these include:
- Improve polymorphism & inheritance behavior, incl. more flexible config & discriminator metadata
- Better support for reverse proxy environments, incl. assigning `servers` metadata based on the presence of common reverse proxy headers
- Support for emitting Swagger / OpenAPI in yaml format
- Improve Schema generation for `ProblemDetails`
- Handle Min/MaxLength attribute for arrays
- Upgrade swagger-ui to v3.32.5
- Upgrade redoc to v2.0.0-rc.40

### v5.5.0  (v5.5.0)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v5.5.0>

These release is primarily to improve compatability of the CLI tool with different versions of the `dotnet` SDK, but also contains a few other minor fixes and enhancements, including an upgrade of the embedded [swagger-ui](https://github.com/swagger-api/swagger-ui) to version `3.26.0`. 

__Addressed issues:__

https://github.com/domaindrivendev/Swashbuckle.AspNetCore/milestone/14?closed=1

### v5.4.1  (v5.4.1)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v5.4.1>

Hotfix for #1645

### v5.4.0  (v5.4.0)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v5.4.0>

__Issues Addressed:__

https://github.com/domaindrivendev/Swashbuckle.AspNetCore/milestone/13?closed=1

### v5.3.0  (v5.3.0)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v5.3.0>

__Issues Addressed__
https://github.com/domaindrivendev/Swashbuckle.AspNetCore/milestone/12?closed=1

### v5.2.0  (v5.2.0)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v5.2.0>

__Issues Addressed__
https://github.com/domaindrivendev/Swashbuckle.AspNetCore/milestone/10

### V5.1.0  (v5.1.0)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v5.1.0>

__Issues Addressed__

See https://github.com/domaindrivendev/Swashbuckle.AspNetCore/milestone/9?closed=1

### v5.0.0  (v5.0.0)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v5.0.0>

__Release Summary__

This release contains a number of significant changes, including a transition to Swagger/OpenAPI v3 and support for ASP.NET Core 3.0, and will require modifications to your application setup if you're upgrading from previous major versions.

While it's awesome to finally support the latest __Swagger/OpenAPI version (v3)__, this does introduce significant structural changes to the Swagger object model, which you're likely interacting with to configure and/or extend Swashbuckle. Specific details are provided below but at a high level, the built-in `SwaggerDocument` and contained types have now been replaced with an `OpenApiDocument` object model that's imported from the [Micorosft/OpenAPI.NET](https://github.com/Microsoft/OpenAPI.NET) library.

To coincide with the release of __ASP.NET Core 3.x__, this version of Swashbuckle will be fully compatible with that version of the framework, including out-of-the-box support for the new *System.Text.Json (STJ)* serializer. 

Furthermore, this release also includes a [wide range of bug fixes and enhancements]( https://github.com/domaindrivendev/Swashbuckle.AspNetCore/milestone/7?closed=1) including an upgrade of the embedded __swagger-ui to 3.24.3__, an upgrade of the __ReDoc UI to 2.0.0-rc.14__, improved handling of `IFormFile` and `FileResult` parameters and responses, and support for polymorphic models.

__Breaking Changes__

* _New Swagger/OpenAPI Object Model:_

Best case, you can simply replace references to the old Swagger objects (`Info`, `Operation`, `Schema` etc.) with corresponding types from the new object model (e.g. `OpenApiInfo`, `OpenApiOperation`, `OpenApiSchema`) available in the `Microsoft.OpenApi.Models` namespace. However, the old model was based on version 2.0 of the Swagger/OpenApi spec. whereas the new version is based on 3.0. Therefore, depending on the extent to which you're manipulating the generated Swagger, you may need to re-work some of your code. Check out the [official Swagger docs](https://swagger.io/blog/news/whats-new-in-openapi-3-0/) to get a better sense of what's changed between v2 and v3 of the spec.

It's also worth noting ... if you have consumers of the generated Swagger JSON that _still_ depend on v2 of the spec, you can configure the Swagger middleware to continue outputting in that format:

```
app.UseSwagger(c => c.SerializeAsV2 = true);
```

* _Honors System.Text.Json Serializer instead of Newtonsoft by default:_

While previous versions of Swashbuckle honored Newtonsoft settings/attributes by default when generating Swagger, this version honors STJ options/attributes by default. If you're still using the Newtonsoft serializer, then you'll need to install a separate Swashbuckle package and explicitly opt-in as described [here](https://github.com/domaindrivendev/Swashbuckle.AspNetCore#systemtextjson-stj-vs-newtonsoft)

* _Changes to Filter Interfaces_ 

As a result of the object model change, the `Apply` method for _all_ filter types accepts a type from the new model instead of the old. For example, `IOperationFilter.Apply` now accepts an `OpenApiOperation`, `IParameterFilter.Apply` an `OpenApiParameter` and so on. 

Also, the `SchemaRegistry` property on filter context objects has been replaced with a `SchemaGenerator/SchemaRepository` pair of properties. This change is the result of an underlying separating of concerns into "schema generation" and "referenced schema storage". Now, if you need to leverage the schema generator within a filter, it should be invoked as follows:

```csharp
var schema = context.SchemaGenerator.GenerateSchema(typeof(CustomType), context.SchemaRepository);
```

__Issues Addressed__

See https://github.com/domaindrivendev/Swashbuckle.AspNetCore/milestone/7?closed=1

### Last planned pre-release  (v5.0.0-rc5)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v5.0.0-rc5>

__Release Summary__

This release contains a number of significant changes, including a transition to Swagger/OpenAPI v3 and support for ASP.NET Core 3.0, and will require modifications to your application setup if you're upgrading from previous major versions.

While it's awesome to finally support the latest __Swagger/OpenAPI version (v3)__, this does introduce structural changes to the Swagger object model, which you're likely interacting with to configure and/or extend Swashbuckle. Specific details are provided below but at a high level, the built-in `SwaggerDocument` and contained types have now been replaced with an `OpenApiDocument` object model that's imported from the [Micorosft/OpenAPI.NET](https://github.com/Microsoft/OpenAPI.NET) library.

To coincide with the release of __ASP.NET Core 3.x__, this version of Swashbuckle will be fully compatible with that version of the framework, including out-of-the-box support for the new *System.Text.Json (STJ)* serializer. 

Furthermore, this release also includes a [wide range of bug fixes and enhancements]( https://github.com/domaindrivendev/Swashbuckle.AspNetCore/milestone/7?closed=1) including an upgrade of the embedded __swagger-ui to 3.24.0__, an upgrade of the __ReDoc UI to 2.0.0-rc.14__, improved handling of `IFormFile` and `FileResult` parameters and responses, and support for polymorphic models.

__Breaking Changes__

* _New Swagger/OpenAPI Object Model:_

Best case, you can simply replace references to the old Swagger objects (`Info`, `Operation`, `Schema` etc.) with corresponding types from the new object model (e.g. `OpenApiInfo`, `OpenApiOperation`, `OpenApiSchema`) available in the `Microsoft.OpenApi.Models` namespace. However, the old model was based on version 2.0 of the Swagger/OpenApi spec. whereas the new version is based on 3.0. Therefore, depending on the extent to which you're manipulating the generated Swagger, you may need to re-work some of your code. Check out the [official Swagger docs](https://swagger.io/blog/news/whats-new-in-openapi-3-0/) to get a better sense of what's changed between v2 and v3 of the spec.

It's also worth noting ... if you have consumers of the generated Swagger JSON that _still_ depend on v2 of the spec, you can configure the Swagger middleware to continue outputting in that format:

```
app.UseSwagger(c => c.SerializeAsV2 = true);
```

* _Honors System.Text.Json Serializer instead of Newtonsoft by default:_

While previous versions of Swashbuckle honored Newtonsoft settings/attributes by default when generating Swagger, this version honors STJ options/attributes by default. If you're still using the Newtonsoft serializer, then you'll need to install a separate Swashbuckle package and explicitly opt-in as described [here](https://github.com/domaindrivendev/Swashbuckle.AspNetCore#systemtextjson-stj-vs-newtonsoft)

* _Changes to Filter Interfaces_ 

As a result of the object model change, the `Apply` method for _all_ filter types accepts a type from the new model instead of the old. For example, `IOperationFilter.Apply` now accepts an `OpenApiOperation`, `IParameterFilter.Apply` an `OpenApiParameter` and so on. 

Also, the `SchemaRegistry` property on filter context objects has been replaced with a `SchemaGenerator/SchemaRepository` pair of properties. This change is the result of an underlying separating of concerns into "schema generation" and "referenced schema storage". Now, if you need to leverage the schema generator within a filter, it should be invoked as follows:

```csharp
var schema = context.SchemaGenerator.GenerateSchema(typeof(CustomType), context.SchemaRepository);
```

__Issues Addressed__

See https://github.com/domaindrivendev/Swashbuckle.AspNetCore/milestone/7?closed=1

### Last planned pre-release before 5.0.0  (v5.0.0-rc4)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v5.0.0-rc4>

__Release Summary__

This release contains a number of significant changes, including a transition to Swagger/OpenAPI v3 and support for ASP.NET Core 3.0, and will require modifications to your application setup if you're upgrading from previous major versions.

While it's awesome to finally support the latest __Swagger/OpenAPI version (v3)__, this does introduce structural changes to the Swagger object model, which you're likely interacting with to configure and/or extend Swashbuckle. Specific details are provided below but at a high level, the built-in `SwaggerDocument` and contained types have now been replaced with an `OpenApiDocument` object model that's imported from the [Micorosft/OpenAPI.NET](https://github.com/Microsoft/OpenAPI.NET) library.

To coincide with the __ASP.NET Core 3.0__ release in Sep 2019, this version of Swashbuckle will be fully compatible with that version of the framework. At this point, the schema generator is still optimized for Newtonsoft serializer behaviors but additional support for the new `System.Text.Json` API is planned for a future minor version.

Furthermore, this release also includes a [wide range of bug fixes and enhancements]( https://github.com/domaindrivendev/Swashbuckle.AspNetCore/milestone/7?closed=1) including an upgrade of the embedded __swagger-ui to 3.23.8__, an upgrade of the __ReDoc UI to 2.0.0-rc.14__, improved handling of __IFormFile and FileResult__ parameters and responses, and support for __polymorphic models__.

__Breaking Changes__

* _New Swagger/OpenAPI Object Model:_

Best case, you can simply replace references to the old Swagger objects (`Info`, `Operation`, `Schema` etc.) with corresponding types from the new object model (e.g. `OpenApiInfo`, `OpenApiOperation`, `OpenApiSchema`) available in the `Microsoft.OpenApi.Models` namespace. However, the old model was based on version 2.0 of the Swagger/OpenApi spec. whereas the new version is based on 3.0. Therefore, depending on the extent to which you're manipulating the generated Swagger, you may need to re-work some of your code. Check out the [official Swagger docs](https://swagger.io/blog/news/whats-new-in-openapi-3-0/) to get a better sense of what's changed between v2 and v3 of the spec.

It's also worth noting ... if you have consumers of the generated Swagger JSON that _still_ depend on v2 of the spec, you can configure the Swagger middleware to continue outputting in that format:

```
app.UseSwagger(c => c.SerializeAsV2 = true);
```

* _Changes to Filter Interfaces_ 

As a result of the object model change, the `Apply` method for _all_ filter types accepts a type from the new model instead of the old. For example, `IOperationFilter.Apply` now accepts an `OpenApiOperation`, `IParameterFilter` an `OpenApiParameter` and so on. 

Also, the `SchemaRegistry` property on filter context objects has been replaced with a `SchemaGenerator/SchemaRepository` pair of properties. This change is the result of an underlying separating of concerns into "schema generation" and "referenced schema storage". Now, if you need to leverage the schema generator within a filter, it should be invoked as follows:

```csharp
var schema = context.SchemaGenerator.GenerateSchema(typeof(CustomType), context.SchemaRepository);
```

Finally, the `SystemType` and `JsonContract` properties on `SchemaFiltercontext` have been replaced with a new property of name and type `ApiModel`. Like `JsonContract`, this abstracts serializer behavior for a given type, but without coupling to the `Newtonsoft` library directly, making it easier to support other serializers (e.g. `System.Text.Json`) going forward. If you need access to the underlying type, use `ApiModel.Type` instead of `SystemType`. 

__Issues Addressed__

See https://github.com/domaindrivendev/Swashbuckle.AspNetCore/milestone/7?closed=1

### v5.0.0-rc3  (v5.0.0-rc3)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v5.0.0-rc3>

__Release Summary__

This release contains a number of significant changes, including a transition to Swagger/OpenAPI v3 and support for ASP.NET Core 3.0, and will require modifications to your application setup if you're upgrading from previous major versions.

While it's awesome to finally support the latest __Swagger/OpenAPI version (v3)__, this does introduce structural changes to the Swagger object model, which you're likely interacting with to configure and/or extend Swashbuckle. Specific details are provided below but at a high level, the built-in `SwaggerDocument` and contained types have now been replaced with an `OpenApiDocument` object model that's imported from the [Micorosft/OpenAPI.NET](https://github.com/Microsoft/OpenAPI.NET) library.

To coincide with the __ASP.NET Core 3.0__ release in Sep 2019, this version of Swashbuckle will be fully compatible with that version of the framework. At this point, the schema generator is still optimized for Newtonsoft serializer behaviors but additional support for the new `System.Text.Json` API is planned for a future minor version.

Furthermore, this release also includes a [wide range of bug fixes and enhancements]( https://github.com/domaindrivendev/Swashbuckle.AspNetCore/milestone/7?closed=1) including an upgrade of the embedded __swagger-ui to 3.23.8__, an upgrade of the __ReDoc UI to 2.0.0-rc.14__, improved handling of __IFormFile and FileResult__ parameters and responses, and support for __polymorphic models__.

__Breaking Changes__

* _New Swagger/OpenAPI Object Model:_

Best case, you can simply replace references to the old Swagger objects (`Info`, `Operation`, `Schema` etc.) with corresponding types from the new object model (e.g. `OpenApiInfo`, `OpenApiOperation`, `OpenApiSchema`) available in the `Microsoft.OpenApi.Models` namespace. However, the old model was based on version 2.0 of the Swagger/OpenApi spec. whereas the new version is based on 3.0. Therefore, depending on the extent to which you're manipulating the generated Swagger, you may need to re-work some of your code. Check out the [official Swagger docs](https://swagger.io/blog/news/whats-new-in-openapi-3-0/) to get a better sense of what's changed between v2 and v3 of the spec.

It's also worth noting ... if you have consumers of the generated Swagger JSON that _still_ depend on v2 of the spec, you can configure the Swagger middleware to continue outputting in that format:

```
app.UseSwagger(c => c.SerializeAsV2 = true);
```

* _Changes to Filter Interfaces_ 

As a result of the object model change, the `Apply` method for _all_ filter types accepts a type from the new model instead of the old. For example, `IOperationFilter.Apply` now accepts an `OpenApiOperation`, `IParameterFilter` an `OpenApiParameter` and so on. 

Also, the `SchemaRegistry` property on filter context objects has been replaced with a `SchemaGenerator/SchemaRepository` pair of properties. This change is the result of an underlying separating of concerns into "schema generation" and "referenced schema storage". Now, if you need to leverage the schema generator within a filter, it should be invoked as follows:

```csharp
var schema = context.SchemaGenerator.GenerateSchema(typeof(CustomType), context.SchemaRepository);
```

Finally, the `SystemType` and `JsonContract` properties on `SchemaFiltercontext` have been replaced with a new property of name and type `ApiModel`. Like `JsonContract`, this abstracts serializer behavior for a given type, but without coupling to the `Newtonsoft` library directly, making it easier to support other serializers (e.g. `System.Text.Json`) going forward. If you need access to the underlying type, use `ApiModel.Type` instead of `SystemType`. 

__Issues Addressed__

See https://github.com/domaindrivendev/Swashbuckle.AspNetCore/milestone/7?closed=1


## v4.x

### v4.0.0  (v4.0.0)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v4.0.0>

__Release Summary__

This release makese an explicit jump to ASP.NET Core 2.0 and the `netstandard2.0` library contract. As a result, Swashbuckle can simplify it's implementation by leveraging some of the newer ASP.NET Core features. However, it also means applications need to upgrade their ASP.NET Core stack to 2.0 __or above__ before they can use this version or subsequent versions of Swashbuckle.

It also includes a significant refactor to the way in which Swashbuckle middleware and services are configured, adhering more closely to the [ASP.NET Core Options Pattern](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/configuration/options?view=aspnetcore-2.1). This allows for the Swashbuckle components to be configured via `appSettings.json` if desired.

The other notable change with this release is out-of-the-box support for parameters of type `IFormFile`. That is, the generator will automatically detect these and generate the correct Swagger to describe parameters that are passed in `formData`. If you have a workaround in place (e.g. using Operation Filters), you should remove it as part of the upgrade.

__Breaking Changes__

* _Requires ASP.NET Core 2.0 and netstandard2.0 or above_:
Applications need to upgrade their ASP.NET Core stack to 2.0 __or above__ before they can use this version or subsequent versions of Swashbuckle.

* _Strongly typed options for SwaggerUI and ReDoc middleware_:
May need to update middleware configuration (e.g. in `Startup.cs`) to compile

* _Explicit OperationIds now required_:
As per the Swagger spec, `operationId`s MUST be unique and SHOULD follow common programming conventions. In previous versions, Swashbuckle attempted to generate these values but this has proved increasingly problematic. As a result, this behavior has been removed and the action name or (optionally) the route name is used instead. So, API developers are now responsible to ensure the uniqueness of these values. See [the readme topic](https://github.com/domaindrivendev/Swashbuckle.AspNetCore#assign-explicit-operationids) for more details.

__Issues Addressed__

See https://github.com/domaindrivendev/Swashbuckle.AspNetCore/milestone/6?closed=1


## v3.x

### v3.0.0  (v3.0.0)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v3.0.0>

__Release Summary__
Includes two significant changes in addition to a handful of bug fixes and minor enhancements. The generator will now honor the `BindRequired` and `Required` attributes on __ALL__ parameters (top-level or property-based) and model properties, flagging the corresponding elements as `required` in the generated Swagger. Also, the Swagger-specific annotations (`SwaggerOperation`, `SwaggerResponse` etc.) have been enhanced, but also extracted from the core functionality into a separate package that consumers need to explicitly install and enable.

__Breaking Changes__
* _Updates to annotations_: To continue using the swagger-specific annotations, you'll need to explicitly install and enable the new `Swashbuckle.AspNetCore.Annotations` package as described [here](https://github.com/domaindrivendev/Swashbuckle.AspNetCore#swashbuckleaspnetcoreannotations). Furthermore, the attributes have moved from the `SwaggerGen` namespace to the `Annotations` namespace, and the ordering of some constructor parameters has changed. So, you'll need to update and test your use of these attributes. 
* _Handling of `Required` / `BindRequired` attributes_: Previously, parameters and properties had to be decorated with these attributes _AND_ be nullable to be flagged as `required` in the generated Swagger. This has changed and now those attributes will be honored on __ALL__ parameters and model properties.

__Issues Addressed__
See https://github.com/domaindrivendev/Swashbuckle.AspNetCore/milestone/5?closed=1


## v2.x

### v2.4.0  (v2.4.0)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v2.4.0>

* Set parameter required based on model binding & data validation behavior
* Support Xml comments from generic type methods
* Upgrade swagger-ui to v3.12.2
* Fixes #499, #542, #599, #631, #655, #662,

### Upgrade to swagger-ui v3.12.0 plus big fixes  (v2.3.0)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v2.3.0>

* Upgrade swagger-ui to v3.12.0
* Add options to use references for enum definitions
*  Fixes #520, #600, #633, #637, #639, #646

### v2.1.0  (v2.1.0)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v2.1.0>

- disables UI validator badge by default
- fixes/addresses #604

### v2.0.0  (v2.0.0)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v2.0.0>

- upgrades embedded version of swagger-ui from 2.2.10 to 3.10.0 . This involves breaking changes to the SwaggerUI config interface - see [readme](https://github.com/domaindrivendev/Swashbuckle.AspNetCore/tree/v2.0.0#apply-swagger-ui-parameters) for details on the new interface
- renames the CLI package from `dotnet-swagger` to `Swashbuckle.AspNetCore.Cli`
- fixes/addresses #179, #210, #228, #231, #349


## v1.x

### v1.2.0  (v1.2.0)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v1.2.0>

* new package for embedded Redoc as an alternative to swagger-ui
* new package for dotnet-swagger CLI tool
* support for custom versions of swagger-ui index.html
* support swagger-ui at root url
* fixes/addresses: #157, #310, #404, #541, #557, #574

### Minor bug fixes and enhancements  (v1.1.0)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v1.1.0>

Fixes #288, #318, #336, #389, #402, #425, #523

### v1.0.0-rc3  (v1.0.0-rc3)
<https://github.com/domaindrivendev/Swashbuckle.AspNetCore/releases/tag/v1.0.0-rc3>

(Hopefully) the last RC before a stable release which will follow shortly assuming no major issues.

**Addresses**:
#171, #249, #255, #266, #267, #274, #305

**Breaking Changes**:
1. the helper for enabling the UI middleware has been renamed from _SwaggerUi_ to _SwaggerUI_ to align better with .NET naming conventions.
