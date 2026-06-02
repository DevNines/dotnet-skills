# Ardalis.Result — release notes by major

_Generated from `https://github.com/ardalis/Result/releases`. Use when answering migration questions or when a user asks what changed between versions._

## v10.x

### v10.1.0  (v10.1.0)
<https://github.com/ardalis/Result/releases/tag/v10.1.0>

## What's Changed
* Add Bind in addition to Map to support Railway Oriented Programming by @christophercalm in https://github.com/ardalis/Result/pull/215
* Add Map Extension Method to Support Mapping from Result<T> to Result by @jmrtnz94 in https://github.com/ardalis/Result/pull/213
* Add identifier & error message constructor to ValidationError by @gordysc in https://github.com/ardalis/Result/pull/209
* Bump google-protobuf from 3.24.3 to 3.25.5 in /docs by @dependabot in https://github.com/ardalis/Result/pull/207
* Release 10.1.0 by @KyleMcMaster in https://github.com/ardalis/Result/pull/216

## New Contributors
* @christophercalm made their first contribution in https://github.com/ardalis/Result/pull/215
* @jmrtnz94 made their first contribution in https://github.com/ardalis/Result/pull/213
* @gordysc made their first contribution in https://github.com/ardalis/Result/pull/209

**Full Changelog**: https://github.com/ardalis/Result/compare/v10.0.0...v10.1.0

### v10.0.0  (v10.0.0)
<https://github.com/ardalis/Result/releases/tag/v10.0.0>

## What's Changed
* Add error messages to forbidden and unauthorized by @Ahammdan in https://github.com/ardalis/Result/pull/190
* Fix unhandled ResultStatus.NoContent in MinimalApiResultExtensions.ToMinimalApiResult by @inghamc in https://github.com/ardalis/Result/pull/192
* Bump rexml from 3.2.8 to 3.3.6 in /docs by @dependabot in https://github.com/ardalis/Result/pull/202
* Fix missing new on Result.Error by @tpitlik-dev in https://github.com/ardalis/Result/pull/194
* Add support for HttpStatusCode: Created to the ResultStatus mapping by @wtygibbs in https://github.com/ardalis/Result/pull/198
* Add Result.Created void methods so that return Result type is implicitly handled. by @jdrames in https://github.com/ardalis/Result/pull/200
* Implement Expression method by @KhanbalaRashidov in https://github.com/ardalis/Result/pull/201
* Add support for ToMinimalApiResult in net6

## New Contributors
* @Ahammdan made their first contribution in https://github.com/ardalis/Result/pull/190
* @inghamc made their first contribution in https://github.com/ardalis/Result/pull/192
* @tpitlik-dev made their first contribution in https://github.com/ardalis/Result/pull/194
* @wtygibbs made their first contribution in https://github.com/ardalis/Result/pull/198
* @jdrames made their first contribution in https://github.com/ardalis/Result/pull/200
* @KhanbalaRashidov made their first contribution in https://github.com/ardalis/Result/pull/201

**Full Changelog**: https://github.com/ardalis/Result/compare/v9.1.0...v10.0.0


## v9.x

### v9.1.0  (v9.1.0)
<https://github.com/ardalis/Result/releases/tag/v9.1.0>

## What's Changed
* fixes ardalis/Result#187; add created option in ToMinimalApiResult by @Dalmazox in https://github.com/ardalis/Result/pull/188
* ✨ 176 result status helpers by @danielmackay in https://github.com/ardalis/Result/pull/184
* Bump rexml from 3.2.6 to 3.2.8 in /docs by @dependabot in https://github.com/ardalis/Result/pull/183
* Fix Null Ref when returning Result.Error(string) non-generically. by @ardalis in https://github.com/ardalis/Result/pull/189

## New Contributors
* @Dalmazox made their first contribution in https://github.com/ardalis/Result/pull/188
* @danielmackay made their first contribution in https://github.com/ardalis/Result/pull/184
* @dependabot made their first contribution in https://github.com/ardalis/Result/pull/183

**Full Changelog**: https://github.com/ardalis/Result/compare/v9.0.1...v9.1.0

### v9.0.1  (v9.0.1)
<https://github.com/ardalis/Result/releases/tag/v9.0.1>

## What's Changed
* Fix 181 by @ardalis in https://github.com/ardalis/Result/pull/182


**Full Changelog**: https://github.com/ardalis/Result/compare/v9.0.0...v9.0.1

### v9.0.0  (v9.0.0)
<https://github.com/ardalis/Result/releases/tag/v9.0.0>

## What's Changed
* Expose ValidationErrors as IEnumerable to Prevent Side Effects by @KyleMcMaster in https://github.com/ardalis/Result/pull/169
* Add Created.Result by @hectorrhg in https://github.com/ardalis/Result/pull/177
* Add Result.NoContent support (HTTP 204) by @dadyarri in https://github.com/ardalis/Result/pull/178
* Fix 179 by @ardalis in https://github.com/ardalis/Result/pull/180
* Update Error usage to utilize ErrorList record with ErrorMessages and CorrelationId by @KyleMcMaster in https://github.com/ardalis/Result/pull/173

## New Contributors
* @hectorrhg made their first contribution in https://github.com/ardalis/Result/pull/177
* @dadyarri made their first contribution in https://github.com/ardalis/Result/pull/178

**Full Changelog**: https://github.com/ardalis/Result/compare/v8.0.0...v9.0.0


## v8.x

### v8.0.0  (v8.0.0)
<https://github.com/ardalis/Result/releases/tag/v8.0.0>

## What's Changed
* closes #161 Auto-Evaluation of the Status property when Errors or ValidationErrors are added to the result. by @Ewerton in https://github.com/ardalis/Result/pull/162

## New Contributors
* @Ewerton made their first contribution in https://github.com/ardalis/Result/pull/162

**Full Changelog**: https://github.com/ardalis/Result/compare/v7.3.0...v8.0.0


## v7.x

### v7.3.0  (v7.3.0)
<https://github.com/ardalis/Result/releases/tag/v7.3.0>

## What's Changed
* Add .NET 8 to NetCoreFrameworks  by @KyleMcMaster in https://github.com/ardalis/Result/pull/158
* Update dotnetcore.yml by @ardalis in https://github.com/ardalis/Result/pull/159
* Update README.md by @ardalis in https://github.com/ardalis/Result/pull/160
* Update README.md by @ardalis in https://github.com/ardalis/Result/pull/164
* Update jekyll-gh-pages.yml by @ardalis in https://github.com/ardalis/Result/pull/167
* occured -> occurred by @Persistent13 in https://github.com/ardalis/Result/pull/168
* Fix Serialization always results in a Success object. by @MischaWeerwag in https://github.com/ardalis/Result/pull/166

## New Contributors
* @Persistent13 made their first contribution in https://github.com/ardalis/Result/pull/168
* @MischaWeerwag made their first contribution in https://github.com/ardalis/Result/pull/166

**Full Changelog**: https://github.com/ardalis/Result/compare/v7.2.0...v7.3.0

### v7.2.0  (v7.2.0)
<https://github.com/ardalis/Result/releases/tag/v7.2.0>

## What's Changed
* Add support for single validation error with Result.Invalid by @IliyanAng in https://github.com/ardalis/Result/pull/144
* Added CriticalError to ResultStatuses (#140) by @EnochMtzR in https://github.com/ardalis/Result/pull/141
* Drop aspnetcore 2.2 dependencies by @radekwojpl2 in https://github.com/ardalis/Result/pull/142
* Radekwojpl2/critical error result by @radekwojpl2 in https://github.com/ardalis/Result/pull/143
* Adds missing Result.Void CriticalError method by @DorianGreen in https://github.com/ardalis/Result/pull/147
* Add Unavailable result status by @DorianGreen in https://github.com/ardalis/Result/pull/146
* Update CONTRIBUTING.md by @sadukie in https://github.com/ardalis/Result/pull/150
* Fix Issue with Serializing Type When Using System.Text.Json by @KyleMcMaster in https://github.com/ardalis/Result/pull/151
* Add params overload for Invalid factory method by @danihengeveld in https://github.com/ardalis/Result/pull/152
* Basic structure and some placeholder pages as a Jekyll JustTheDocs site by @pedroduarte0 in https://github.com/ardalis/Result/pull/153
* Fix TargetFrameworks by @DorianGreen in https://github.com/ardalis/Result/pull/155
* Version update to 7.2.0 by @KyleMcMaster in https://github.com/ardalis/Result/pull/154

## New Contributors
* @IliyanAng made their first contribution in https://github.com/ardalis/Result/pull/144
* @EnochMtzR made their first contribution in https://github.com/ardalis/Result/pull/141
* @radekwojpl2 made their first contribution in https://github.com/ardalis/Result/pull/142
* @DorianGreen made their first contribution in https://github.com/ardalis/Result/pull/147
* @danihengeveld made their first contribution in https://github.com/ardalis/Result/pull/152
* @pedroduarte0 made their first contribution in https://github.com/ardalis/Result/pull/153

**Full Changelog**: https://github.com/ardalis/Result/compare/v7.1.0...v7.2.0

### v7.1.0  (v7.1.0)
<https://github.com/ardalis/Result/releases/tag/v7.1.0>

## What's Changed
* #116 added name to method declaration by @almostengr in https://github.com/ardalis/Result/pull/118
* Added CorrelationId property to Result (#120) by @scottjferguson in https://github.com/ardalis/Result/pull/122
* Working through code coverage from forks by @sadukie in https://github.com/ardalis/Result/pull/125
* Added Directory Build and Packages.props by @thomas-mullaly in https://github.com/ardalis/Result/pull/128
* Moved nuget version back into csproj to fix package publishing issues by @thomas-mullaly in https://github.com/ardalis/Result/pull/129
* Updated github actions to remove deprecation warnings by @thomas-mullaly in https://github.com/ardalis/Result/pull/130
* Publish the release version of the nuget packages by @thomas-mullaly in https://github.com/ardalis/Result/pull/131
* Add Result.Conflict by @IlyaBelitser in https://github.com/ardalis/Result/pull/132
* add conflict info to landing page by @buti1021 in https://github.com/ardalis/Result/pull/136
* Bump Version to 7.1.0 by @KyleMcMaster in https://github.com/ardalis/Result/pull/139

## New Contributors
* @almostengr made their first contribution in https://github.com/ardalis/Result/pull/118
* @scottjferguson made their first contribution in https://github.com/ardalis/Result/pull/122
* @sadukie made their first contribution in https://github.com/ardalis/Result/pull/125
* @thomas-mullaly made their first contribution in https://github.com/ardalis/Result/pull/128
* @IlyaBelitser made their first contribution in https://github.com/ardalis/Result/pull/132
* @buti1021 made their first contribution in https://github.com/ardalis/Result/pull/136

**Full Changelog**: https://github.com/ardalis/Result/compare/v7.0.0...v7.1.0

### v7.0  (v7.0.0)
<https://github.com/ardalis/Result/releases/tag/v7.0.0>

## What's Changed
* Features/api description by @Artem-Romanenia in https://github.com/ardalis/Result/pull/92
* Update TargetFramework to .NET 7 by @KyleMcMaster in https://github.com/ardalis/Result/pull/112


**Full Changelog**: https://github.com/ardalis/Result/compare/v4.2.0...v7.0.0


## v4.x

### v4.1.0  (v4.1.0)
<https://github.com/ardalis/Result/releases/tag/v4.1.0>

## What's Changed

* Add the ability to return an error body with the Result.NotFound() extension by @berv63 in https://github.com/ardalis/Result/pull/96
* Proposal: Add map extension to convert result values by @KyleMcMaster in https://github.com/ardalis/Result/pull/97
* Add xml comment to Map extension by @KyleMcMaster in https://github.com/ardalis/Result/pull/98

## New Contributors

* @berv63 made their first contribution in https://github.com/ardalis/Result/pull/96
* @KyleMcMaster made their first contribution in https://github.com/ardalis/Result/pull/97

**Full Changelog**: https://github.com/ardalis/Result/compare/v4.0.0...v4.1.0
