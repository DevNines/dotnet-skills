# Shouldly — release notes by major

_Generated from `https://github.com/shouldly/shouldly/releases`. Use when answering migration questions or when a user asks what changed between versions._

## v4.x

### 4.3.0  (4.3.0)
<https://github.com/shouldly/shouldly/releases/tag/4.3.0>

Notable PRs in this milestone: https://github.com/shouldly/shouldly/pulls?q=is%3Apr+is%3Aclosed+milestone%3A4.3.0

## What's Changed
* remove some obsoletes by @SimonCropp in https://github.com/shouldly/shouldly/pull/931
* Add support for ImmutableArray for ShouldBeEquivalentTo by @larsiver in https://github.com/shouldly/shouldly/pull/930
* update sdk to 8.0.301 by @SimonCropp in https://github.com/shouldly/shouldly/pull/942
* sdk 8.0.302 by @SimonCropp in https://github.com/shouldly/shouldly/pull/943
* remove sourcelink by @SimonCropp in https://github.com/shouldly/shouldly/pull/944
* move tests projects to net8 by @SimonCropp in https://github.com/shouldly/shouldly/pull/947
* update MarkdownSnippets by @SimonCropp in https://github.com/shouldly/shouldly/pull/949
* update PublicApiGenerator by @SimonCropp in https://github.com/shouldly/shouldly/pull/950
* update Microsoft.NET.Test.Sdk by @SimonCropp in https://github.com/shouldly/shouldly/pull/951
* update Microsoft.CodeAnalysis.CSharp by @SimonCropp in https://github.com/shouldly/shouldly/pull/952
* Improve some of the flaky tests by @slang25 in https://github.com/shouldly/shouldly/pull/954
* avoid task waiting in ShouldCompleteInTests by @SimonCropp in https://github.com/shouldly/shouldly/pull/945
* update xunit by @SimonCropp in https://github.com/shouldly/shouldly/pull/946
* Extend timeout for CI by @slang25 in https://github.com/shouldly/shouldly/pull/961
* Assortment of Minor Improvements by @slang25 in https://github.com/shouldly/shouldly/pull/962
* Switch from AppVeyor to GitHub Actions by @slang25 in https://github.com/shouldly/shouldly/pull/965
* update xunit 2.9 by @SimonCropp in https://github.com/shouldly/shouldly/pull/966
* sdk 8.0.303 by @SimonCropp in https://github.com/shouldly/shouldly/pull/968
* Fix name allBe.md by @bas-mulder in https://github.com/shouldly/shouldly/pull/972
* Support IReadOnlyDictionary<K, V> by @martincostello in https://github.com/shouldly/shouldly/pull/984
* Drop .NET 5 and add .NET 8 by @martincostello in https://github.com/shouldly/shouldly/pull/997
* Removing previous maintainers in README to avoid confusion/spam by @slang25 in https://github.com/shouldly/shouldly/pull/1032
* fix descriminate -> discriminate by @CaringDev in https://github.com/shouldly/shouldly/pull/1038
* move to stable net9 sdk 9.0.102 by @SimonCropp in https://github.com/shouldly/shouldly/pull/1039
* remove redundant verbatum strings by @SimonCropp in https://github.com/shouldly/shouldly/pull/1042
* fix docs snippets by @SimonCropp in https://github.com/shouldly/shouldly/pull/1040
* remove appveyor.yml from sln by @SimonCropp in https://github.com/shouldly/shouldly/pull/1041
* Add NRT annotation to ShouldBeAssignableTo by @Shane32 in https://github.com/shouldly/shouldly/pull/933
* fix PackageLicenseExpression in nuget by @SimonCropp in https://github.com/shouldly/shouldly/pull/1043
* fix link and add license name license.txt by @SimonCropp in https://github.com/shouldly/shouldly/pull/1044
* Add xunit v3 marker interfaces by @slang25 in https://github.com/shouldly/shouldly/pull/1045
* Fix handling of zero tolerances by @martincostello in https://github.com/shouldly/shouldly/pull/1049
* Housekeeping changes by @slang25 in https://github.com/shouldly/shouldly/pull/1052
* Add a git-blame-ignore-revs file by @slang25 in https://github.com/shouldly/shouldly/pull/1053
* Support Nullable<T> in ShouldBeAssignableTo by @slang25 in https://github.com/shouldly/shouldly/pull/1054
* Relax missing actual argument expression by @slang25 in https://github.com/shouldly/shouldly/pull/1056
* Many dependabot updates

## New Contributors
* @larsiver made their first contribution in https://github.com/shouldly/shouldly/pull/930
* @bas-mulder made their first contribution in https://github.com/shouldly/shouldly/pull/972
* @CaringDev made their first contribution in https://github.com/shouldly/shouldly/pull/1038
* @Shane32 made their first contribution in https://github.com/shouldly/shouldly/pull/933

**Full Changelog**: https://github.com/shouldly/shouldly/compare/4.2.1...4.3.0

### 4.2.1  (4.2.1)
<https://github.com/shouldly/shouldly/releases/tag/4.2.1>

## What's Changed
* Avoid Microsoft.CSharp dependency on net5.0 by @ViktorHofer in https://github.com/shouldly/shouldly/pull/897
* Bump DiffEngine from 11.2.0 to 11.3.0 by @dependabot in https://github.com/shouldly/shouldly/pull/895
* docs: remove HashSnippetAnchors by @SimonCropp in https://github.com/shouldly/shouldly/pull/879
* Improved deterministic build support by @slang25 in https://github.com/shouldly/shouldly/pull/898

## New Contributors
* @ViktorHofer made their first contribution in https://github.com/shouldly/shouldly/pull/897

**Full Changelog**: https://github.com/shouldly/shouldly/compare/4.2.0...4.2.1

### 4.2.0  (4.2.0)
<https://github.com/shouldly/shouldly/releases/tag/4.2.0>

## What's Changed
* Install .NET SDK in GitHub Actions by @martincostello in https://github.com/shouldly/shouldly/pull/863
* Switch from shouldly.io to shouldly.org by @jnm2 in https://github.com/shouldly/shouldly/pull/864
* update refs by @SimonCropp in https://github.com/shouldly/shouldly/pull/868
* sdk 7.0.101 by @SimonCropp in https://github.com/shouldly/shouldly/pull/873
* update to DiffEngine 11 and EmptyFiles 4.1 by @SimonCropp in https://github.com/shouldly/shouldly/pull/872
* move tests to net7 by @SimonCropp in https://github.com/shouldly/shouldly/pull/874
* System.Half support by @sungam3r in https://github.com/shouldly/shouldly/pull/870
* Include Enumerable Have documentation in summary by @chris-codeflow in https://github.com/shouldly/shouldly/pull/869
* remove redundant T from EqualityComparerAdapter by @SimonCropp in https://github.com/shouldly/shouldly/pull/875
* CheckEolTargetFramework>false by @SimonCropp in https://github.com/shouldly/shouldly/pull/891
* suppress NU1505 by @SimonCropp in https://github.com/shouldly/shouldly/pull/893
* Bump MarkdownSnippets.MsBuild from 24.5.0 to 24.5.1 by @dependabot in https://github.com/shouldly/shouldly/pull/888
* Bump EmptyFiles from 4.1.0 to 4.4.0 by @dependabot in https://github.com/shouldly/shouldly/pull/889
* Bump Microsoft.CodeAnalysis.CSharp from 4.4.0 to 4.5.0 by @dependabot in https://github.com/shouldly/shouldly/pull/885
* change time in flakey test by @SimonCropp in https://github.com/shouldly/shouldly/pull/894
* Bump DiffEngine from 11.0.0 to 11.2.0 by @dependabot in https://github.com/shouldly/shouldly/pull/890
* Bump Microsoft.NET.Test.Sdk from 17.4.1 to 17.5.0 by @dependabot in https://github.com/shouldly/shouldly/pull/887
* Bump PublicApiGenerator from 10.3.0 to 11.0.0 by @dependabot in https://github.com/shouldly/shouldly/pull/886
* Add support for deterministic builds by @slang25 in https://github.com/shouldly/shouldly/pull/883


**Full Changelog**: https://github.com/shouldly/shouldly/compare/4.1.0...4.2.0

### 4.1.0  (4.1.0)
<https://github.com/shouldly/shouldly/releases/tag/4.1.0>

See [Milestone  4.1.0](https://github.com/shouldly/shouldly/issues?q=is%3Aclosed+milestone%3A4.1.0)

Published to https://www.nuget.org/packages/Shouldly/4.1.0

### v4.0.2  (v4.0.2)
<https://github.com/shouldly/shouldly/releases/tag/v4.0.2>

See https://github.com/shouldly/shouldly/issues?q=is%3Aclosed+milestone%3A4.0.2

### v4.0.1  (v4.0.1)
<https://github.com/shouldly/shouldly/releases/tag/v4.0.1>

* Fix [Approval methods fail with TypeInitializationException under .NET 5 ](https://github.com/shouldly/shouldly/issues/717)

### v4.0.0  (v4.0.0)
<https://github.com/shouldly/shouldly/releases/tag/v4.0.0>

This is the first stable release in over 2 years. It is essentially an effort to reboot the project to being better supported and to have a regular release cadence. 

See the [v4 milestone](https://github.com/shouldly/shouldly/issues?q=is%3Aclosed+milestone%3A4.0.0) for the list of changes. Although note that some changes have been done without associated issues or PR.

Where possible `ObsoleteAttribute`s have been applied with directions on using the new API.

There is a work-in-progress [v3 to v4 upgrade guide](https://docs.shouldly.io/documentation/3to4). Please feel free to help out by adding any additional notes to it.

### v4.0.0-beta0004  (v4.0.0-beta0004)
<https://github.com/shouldly/shouldly/releases/tag/v4.0.0-beta0004>

_No release notes._

### v4.0.0-beta2  (4.0.0-beta0002)
<https://github.com/shouldly/shouldly/releases/tag/4.0.0-beta0002>

- [#564](https://github.com/shouldly/shouldly/pull/564) - #550 Add diffing support for Windows VS Code contributed by Eubert Go ([ber2go](https://github.com/ber2go))
 - [#560](https://github.com/shouldly/shouldly/pull/560) - Refactor ShouldThrowAsync for cancellation handing and add test contributed by Adam Hathcock ([adamhathcock](https://github.com/adamhathcock))
 - [#555](https://github.com/shouldly/shouldly/pull/555) - Fix in the Should.ThrowAsync error messages and exception handling contributed by Gabriel Milani ([gmilani](https://github.com/gmilani))
 - [#550](https://github.com/shouldly/shouldly/issues/550) - Add diffing support for VS Code
 - [#411](https://github.com/shouldly/shouldly/pull/411) - Object Graph Comparison - ShouldBeEquivalentTo(...) contributed by RJ Hollberg ([TaffarelJr](https://github.com/TaffarelJr))

This release also includes the initial release of the new `ShouldBeEquivalentTo` method used for object graph comparison. This feature is still early in the making so I imagine there'll be a few bugs, for this reason this package will stay as a beta whilst we iterate on it.

Please raise any issues you find on our GitHub repository.

### v4.0.0-beta1  (v4.0.0-beta1)
<https://github.com/shouldly/shouldly/releases/tag/v4.0.0-beta1>

- [#547](https://github.com/shouldly/shouldly/pull/547) - Make ShouldMatchApproved cross-platform contributed by Joseph Woodward ([JosephWoodward](https://github.com/JosephWoodward))
 - [#516](https://github.com/shouldly/shouldly/pull/516) - Add new Do Not Launch Strategy contributed by Brian Dukes ([bdukes](https://github.com/bdukes))


## v3.x

### v3.0.2  (v3.0.2)
<https://github.com/shouldly/shouldly/releases/tag/v3.0.2>

- [#539](https://github.com/shouldly/shouldly/pull/539) - Prevent optimizations from interfering with stack walking logic [investigated by Joseph Woodward](https://github.com/shouldly/shouldly/issues/524), fix by Stuart Lang ([slang25](https://github.com/slang25))
- [#538](https://github.com/shouldly/shouldly/pull/538) - Fixed null string comparison contributed by Joseph Musser ([jnm2](https://github.com/jnm2))
- [#536](https://github.com/shouldly/shouldly/pull/536) - Sourcelink contributed by Stuart Lang ([slang25](https://github.com/slang25))
- [#530](https://github.com/shouldly/shouldly/pull/530) - Add Should.Throw() overloads for Func contributed by Martin Costello ([martincostello](https://github.com/martincostello))
- [#527](https://github.com/shouldly/shouldly/pull/527) - Add RepositoryUrl MSBuild property contributed by Martin Costello ([martincostello](https://github.com/martincostello))
- [#501](https://github.com/shouldly/shouldly/pull/501) - Removed irrelevant stack frames from exception stack traces contributed by Joseph Musser ([jnm2](https://github.com/jnm2))

Commits: 86e42dd76e...c4aa6f50f8

### v3.0.1  (v3.0.1)
<https://github.com/shouldly/shouldly/releases/tag/v3.0.1>

- [#510](https://github.com/shouldly/shouldly/pull/510) - Add WinMerge to known diff tools contributed by Brian Dukes ([bdukes](https://github.com/bdukes))
 - [#500](https://github.com/shouldly/shouldly/pull/500) - Syntax highlight contributed by Jonathan ([vanillajonathan](https://github.com/vanillajonathan))
 - [#494](https://github.com/shouldly/shouldly/pull/494) - Now will work on vs 2017 Build 15.6 contributed by osama arif lone ([loneosama](https://github.com/loneosama))
 - [#492](https://github.com/shouldly/shouldly/pull/492) - Fixed Test.csproj Now will work on linux contributed by osama arif lone ([loneosama](https://github.com/loneosama))
 - [#489](https://github.com/shouldly/shouldly/pull/489) - Fixed NullReferenceException when creating error message from Expression contributed by Hajbok Robert ([HajbokRobert](https://github.com/HajbokRobert))
 - [#479](https://github.com/shouldly/shouldly/pull/479) - .NET Standard tests and .NET 2.0 target contributed by Joseph Woodward ([JosephWoodward](https://github.com/JosephWoodward))

### v3.0.0  (v3.0.0)
<https://github.com/shouldly/shouldly/releases/tag/v3.0.0>

- [#488](https://github.com/shouldly/shouldly/pull/448) - Tidy up test class by Joseph Woodward ([JosephWoodward](https://github.com/JosephWoodward))
 - [#474](https://github.com/shouldly/shouldly/pull/474) - Fix broken ShouldHaveFlag tests contributed by Joseph Woodward ([JosephWoodward](https://github.com/JosephWoodward))
 - [#468](https://github.com/shouldly/shouldly/pull/468) - Fix typos in SourceCodeTextGetter.cs contributed by David ([TAGC](https://github.com/TAGC))
 - [#462](https://github.com/shouldly/shouldly/pull/462) - Correct VSTS/TFS environment variable. contributed by Gian Lorenzetto ([GianLorenzetto](https://github.com/GianLorenzetto))
 - [#452](https://github.com/shouldly/shouldly/pull/452) - Update cake build script for new tooling contributed by Stuart Lang ([slang25](https://github.com/slang25))
 - [#451](https://github.com/shouldly/shouldly/pull/451) - Fix build scripts contributed by Joseph Woodward ([JosephWoodward](https://github.com/JosephWoodward))
- [#450](https://github.com/shouldly/shouldly/pull/450) - More build improvements contributed by Stuart Lang ([slang25](https://github.com/slang25))
- [#446](https://github.com/shouldly/shouldly/pull/446) - Drop support for .NET 3.5 contributed by Stuart Lang ([slang25](https://github.com/slang25))
- [#447](https://github.com/shouldly/shouldly/pull/447) - Consolidate conditional code contributed by Stuart Lang ([slang25](https://github.com/slang25))
- [#445](https://github.com/shouldly/shouldly/pull/445) - Added OS conditional to allow building on non Windows platforms by Joseph Woodward ([JosephWoodward](https://github.com/JosephWoodward))
- [#439](https://github.com/shouldly/shouldly/pull/439) - Make diff tools configuration lazy contributed by Stuart Lang ([slang25](https://github.com/slang25))
- [#426](https://github.com/shouldly/shouldly/pull/426) - Added more ReSharper contract annotations contributed by Sebastian Krysmanski ([skrysmanski](https://github.com/skrysmanski))
- [#416](https://github.com/shouldly/shouldly/pull/416) - Fix for #415 (ShouldlyMethods attribute were missing on ShouldBeEnumE… contributed by Niklas Källander ([niklaskallander](https://github.com/niklaskallander))
- [#236](https://github.com/shouldly/shouldly/issues/236) - New logo
- [#432](https://github.com/shouldly/shouldly/pull/432) - Tooling migration by Joseph Woodward ([JosephWoodward](https://github.com/JosephWoodward))

### v3.0.0-beta.1  (v3.0.0-beta.1)
<https://github.com/shouldly/shouldly/releases/tag/v3.0.0-beta.1>

- [#450](https://github.com/shouldly/shouldly/pull/450) - More build improvements contributed by Stuart Lang ([slang25](https://github.com/slang25))
- [#488](https://github.com/shouldly/shouldly/pull/448) - Tidy up test class by Joseph Woodward ([JosephWoodward](https://github.com/JosephWoodward))
- [#447](https://github.com/shouldly/shouldly/pull/447) - Consolidate conditional code contributed by Stuart Lang ([slang25](https://github.com/slang25))
- [#446](https://github.com/shouldly/shouldly/pull/446) - Drop support for .NET 3.5 contributed by Stuart Lang ([slang25](https://github.com/slang25))
- [#445](https://github.com/shouldly/shouldly/pull/445) - Added OS conditional to allow building on non Windows platforms by Joseph Woodward ([JosephWoodward](https://github.com/JosephWoodward))
- [#432](https://github.com/shouldly/shouldly/pull/432) - Tooling migration by Joseph Woodward ([JosephWoodward](https://github.com/JosephWoodward))


## v2.x

### v2.8.3  (v2.8.3)
<https://github.com/shouldly/shouldly/releases/tag/v2.8.3>

- [#428](https://github.com/shouldly/shouldly/pull/428) - Null fix for ShouldBeAssignableTo contributed by Joseph Woodward ([JosephWoodward](https://github.com/JosephWoodward))
- [#423](https://github.com/shouldly/shouldly/pull/423) - Fix for Try catch around environment variable calls contributed by Ståle Strømme ([SteelFlow](https://github.com/SteelFlow))
- [#419](https://github.com/shouldly/shouldly/pull/419) - Added build servers contributed by Rob Moore ([robdmoore](https://github.com/robdmoore))
- [#418](https://github.com/shouldly/shouldly/pull/418) - Adding currently running Visual Studio and Tortoise Git diff tools contributed by Rob Moore ([robdmoore](https://github.com/robdmoore))
- [#414](https://github.com/shouldly/shouldly/pull/414) - Updated Should.Throw fix for TimeoutException contributed by João Barbosa ([bmpj13](https://github.com/bmpj13))
- [#410](https://github.com/shouldly/shouldly/pull/410) - Implement 'ShouldBeInOrder' for IEnumerable contributed by RJ Hollberg ([TaffarelJr](https://github.com/TaffarelJr))
- [#409](https://github.com/shouldly/shouldly/pull/409) - Register new diff tools: Devart Code Compare and Perforce P4Merge contributed by RJ Hollberg ([TaffarelJr](https://github.com/TaffarelJr))
- [#408](https://github.com/shouldly/shouldly/pull/408) - Include customMessage in ShouldNotBeAssignableTo(...) contributed by RJ Hollberg ([TaffarelJr](https://github.com/TaffarelJr))
- [#406](https://github.com/shouldly/shouldly/pull/406) - Split out contributing guidelines into their own file. contributed by Tom Wright ([tdwright](https://github.com/tdwright))
- [#404](https://github.com/shouldly/shouldly/pull/404) - Ability to check exception type and exception message. contributed by Derek Comartin ([dcomartin](https://github.com/dcomartin))
- [#402](https://github.com/shouldly/shouldly/pull/402) - Fixed some issues with the Shouldly convention tests contributed by Jake Ginnivan ([JakeGinnivan](https://github.com/JakeGinnivan))
- [#401](https://github.com/shouldly/shouldly/pull/401) - Compare Custom classes that don't implement IComparable (#364) contributed by ([ankurMalhotra](https://github.com/ankurMalhotra))
- [#398](https://github.com/shouldly/shouldly/pull/398) - Updated approved text to fix build contributed by Joseph Woodward ([JosephWoodward](https://github.com/JosephWoodward))

### v2.8.2  (v2.8.2)
<https://github.com/shouldly/shouldly/releases/tag/v2.8.2>

- [#396](https://github.com/shouldly/shouldly/pull/396) - Add net451 support, fixes [#394](https://github.com/shouldly/shouldly/issues/394) contributed by ([slang25](https://github.com/slang25))
- [#395](https://github.com/shouldly/shouldly/pull/395) - update README contributed by Brent Sullivan ([brntsllvn](https://github.com/brntsllvn))
- [#393](https://github.com/shouldly/shouldly/pull/393) - Adding VisitTypeBinary override for ExpressionStringBuilder - Resolves [#389](https://github.com/shouldly/shouldly/issues/389) contributed by Steve Sikorski ([ssiko](https://github.com/ssiko))

Commits: 84c90506a1...24ac8738f9

### v2.8.1  (v2.8.1)
<https://github.com/shouldly/shouldly/releases/tag/v2.8.1>

- [#390](https://github.com/shouldly/shouldly/pull/390) - Upgraded to .NET Core RTM contributed by Joseph Woodward ([JosephWoodward](https://github.com/JosephWoodward))

### v2.8.0  (v2.8.0)
<https://github.com/shouldly/shouldly/releases/tag/v2.8.0>

- [#386](https://github.com/shouldly/shouldly/pull/386) - Switch to dotnet cli RC2 Preview 1 Tooling contributed by Jake Ginnivan ([JakeGinnivan](https://github.com/JakeGinnivan))
- [#383](https://github.com/shouldly/shouldly/pull/383) - Trim quotes when initializing DiffTools contributed by Alexander Nyquist ([alexandernyquist](https://github.com/alexandernyquist))
- [#382](https://github.com/shouldly/shouldly/pull/382) - Fixed codePart format issue contributed by Joseph Woodward ([JosephWoodward](https://github.com/JosephWoodward)) fixes [#377](https://github.com/shouldly/shouldly/issues/377) - Type initialization for KnownDiffTools fails
- [#380](https://github.com/shouldly/shouldly/pull/380) - Renaming the AssemblyInfo.cs because GitVersion now adds in the missi… contributed by Jake Ginnivan ([JakeGinnivan](https://github.com/JakeGinnivan))
- [#378](https://github.com/shouldly/shouldly/issues/378) - Should.Throw causes a FormatException
- [#374](https://github.com/shouldly/shouldly/pull/374) - Addition of Should.Throw and Should.ThrowAsync methods contributed by ([StuartFerguson](https://github.com/StuartFerguson))
- [#372](https://github.com/shouldly/shouldly/pull/372) [#371](https://github.com/shouldly/shouldly/issues/371) - changes for shouldly should show more details when asserting DateTime #371 contributed by Sebastian Wojciechowski ([SebastianWojciechowski](https://github.com/SebastianWojciechowski))

Commits: 2ed69761d3...c5cc758437

### v2.7.0  (v2.7.0)
<https://github.com/shouldly/shouldly/releases/tag/v2.7.0>

v2.7.0 is a pretty big release which manages to not have any breaking changes afaik (please raise an issue if this is not the case). Here are the highlights:
- PCL/CoreCLR support
- Way better error messages when source is not available, as time goes on we will bring better error messages to different PCL targets. At the moment PCL/CoreCLR cannot get at the source code of your tests so the error messages are not quite as good.
- Switched over to XUnit and removed our testbase class. This means those of you using the Visual Studio test explorer, Shouldlys test suite will now be usable for you.
- `ShouldMatchApproved` - Based on the awesome ApprovalTests.net, shouldly now has a simple and configurable version for strings. Have a look at the docs at http://shouldly.readthedocs.org/en/latest/assertions/shouldMatchApproved.html - Feedback on API and functionality welcome, especially during beta period
- We have a documentation project now which powers http://shouldly.readthedocs.org - We need help porting the docs to readthedocs! Jump in and pickup an assertion on #308
- Option to ignore line endings when comparing strings
- Plugged gaps in missing overloads and other small API inconsistencies
  -  `ShouldHaveSingleItem` method
  - `AddEnumHaveFlag` method

### Changelog:
- [#368](https://github.com/shouldly/shouldly/pull/368) - Added ShouldHaveSingleItem for Enumerables. contributed by Steve Sikorski ([ssiko](https://github.com/ssiko))
- [#365](https://github.com/shouldly/shouldly/issues/365) - ShouldHaveSingleItem() +Enhancement
- [#362](https://github.com/shouldly/shouldly/pull/362) - remove apostrophe contributed by Chris Sutton ([chrissutton](https://github.com/chrissutton))
- [#361](https://github.com/shouldly/shouldly/pull/361) - Merged pull request #355 from bangsholt:AddEnumHaveFlag contributed by Joseph Woodward ([JosephWoodward](https://github.com/JosephWoodward))
- [#360](https://github.com/shouldly/shouldly/pull/360) - Added example classes to help with documentation contributed by Chaitanya Gurrapu ([chaitanyagurrapu](https://github.com/chaitanyagurrapu))
- [#355](https://github.com/shouldly/shouldly/pull/355) - Add enum have flag contributed by ([bangsholt](https://github.com/bangsholt))
- [#272](https://github.com/shouldly/shouldly/issues/272) - Implement ShouldHaveFlag() and ShouldNotHaveFlag() for enums decorated with [Flags] attribute +Enhancement
- [#348](https://github.com/shouldly/shouldly/pull/348) - Wrote docs for new shouldMatchApproved and fixed up a few more issues… contributed by Jake Ginnivan ([JakeGinnivan](https://github.com/JakeGinnivan))
- [#347](https://github.com/shouldly/shouldly/pull/347) - Switched ShouldNotBe docs over to use examples, moved approved files … contributed by Jake Ginnivan ([JakeGinnivan](https://github.com/JakeGinnivan))
- [#346](https://github.com/shouldly/shouldly/pull/346) - Add support for the dotnet TFM contributed by Oren Novotny ([onovotny](https://github.com/onovotny))
- [#345](https://github.com/shouldly/shouldly/pull/345) - Created documentation samples project which outputs files to be inclu… contributed by Jake Ginnivan ([JakeGinnivan](https://github.com/JakeGinnivan))
- [#344](https://github.com/shouldly/shouldly/issues/344) - ShouldBeSameAs and reference equality
- [#343](https://github.com/shouldly/shouldly/pull/343) - Some constants missing in test projects contributed by Jake Ginnivan ([JakeGinnivan](https://github.com/JakeGinnivan))
- [#342](https://github.com/shouldly/shouldly/pull/342) - Initial pass at ShouldMatchApproved contributed by Jake Ginnivan ([JakeGinnivan](https://github.com/JakeGinnivan))
- [#341](https://github.com/shouldly/shouldly/pull/341) - Add support for coreclr/portable libraries contributed by Jake Ginnivan ([JakeGinnivan](https://github.com/JakeGinnivan))
- [#339](https://github.com/shouldly/shouldly/pull/339) - Dnx contributed by Jake Ginnivan ([JakeGinnivan](https://github.com/JakeGinnivan))
- [#338](https://github.com/shouldly/shouldly/pull/338) - Minor consistency tweaks to StringHelper.cs contributed by Joseph Woodward ([JosephWoodward](https://github.com/JosephWoodward))
- [#337](https://github.com/shouldly/shouldly/pull/337) [#301](https://github.com/shouldly/shouldly/issues/301) - Includes numeric suffixes in error messages contributed by Amadeusz Wieczorek ([AmadeusW](https://github.com/AmadeusW))
- [#336](https://github.com/shouldly/shouldly/pull/336) - String options clean up contributed by ([sholland1](https://github.com/sholland1))
- [#335](https://github.com/shouldly/shouldly/pull/335) - Xunit conversion contributed by Jake Ginnivan ([JakeGinnivan](https://github.com/JakeGinnivan))
- [#333](https://github.com/shouldly/shouldly/pull/333) - Should be with options contributed by ([sholland1](https://github.com/sholland1)) and Jake Ginnivan ([JakeGinnivan](https://github.com/JakeGinnivan))
- [#332](https://github.com/shouldly/shouldly/pull/332) - Fixed #330 contributed by Jake Ginnivan ([JakeGinnivan](https://github.com/JakeGinnivan))
- [#331](https://github.com/shouldly/shouldly/issues/331) - Support CoreCLR
- [#330](https://github.com/shouldly/shouldly/issues/330) - ShouldContainWithoutWhitespace uses Is.Equal not contains
- [#329](https://github.com/shouldly/shouldly/pull/329) - Finished off ShouldNotMatch contributed by Joseph Woodward ([JosephWoodward](https://github.com/JosephWoodward))
- [#328](https://github.com/shouldly/shouldly/pull/328) - Fix for #327 Mono NullReferenceException contributed by Nate Barbettini ([nbarbettini](https://github.com/nbarbettini))
- [#327](https://github.com/shouldly/shouldly/issues/327) - ShouldThrow fails under Mono
- [#325](https://github.com/shouldly/shouldly/pull/325) - Set thread culture within tests contributed by Joseph Woodward ([JosephWoodward](https://github.com/JosephWoodward))
- [#324](https://github.com/shouldly/shouldly/issues/324) - Tests fail with Hungarian regional settings
- [#321](https://github.com/shouldly/shouldly/pull/321) [#273

_…truncated…_

### v2.7.0-beta.3  (v2.7.0-beta.3)
<https://github.com/shouldly/shouldly/releases/tag/v2.7.0-beta.3>

A small release adding `LocateTestMethodUsingAttribute` to the `ShouldMatchApproved` configuration.

### v2.7.0-beta.2  (v2.7.0-beta.2)
<https://github.com/shouldly/shouldly/releases/tag/v2.7.0-beta.2>

*_Breaking change from beta.1: *_ The new ShouldMatchApproved now includes the class name. To restore beta.1 functionality you can override the naming with this `ShouldlyConfiguration.ShouldMatchApprovedDefaults.WithFilenameGenerator((testMethodInfo, descriminator, type, extension) => $"{testMethodInfo.MethodName}{descriminator}.{type}.{extension}");`
- [#357](https://github.com/shouldly/shouldly/pull/357) - Empty dependency groups to save clr dependencies being installed via … contributed by Jake Ginnivan ([JakeGinnivan](https://github.com/JakeGinnivan))
- [#356](https://github.com/shouldly/shouldly/pull/356) - Fixed approval defaults to include class name in filename. contributed by Jake Ginnivan ([JakeGinnivan](https://github.com/JakeGinnivan))
- [#354](https://github.com/shouldly/shouldly/pull/354) - Updates NuGet tags and fixes a typo contributed by Amadeusz Wieczorek ([AmadeusW](https://github.com/AmadeusW))
- [#353](https://github.com/shouldly/shouldly/pull/353) - Updates NuGet tags for more search scenarios contributed by Amadeusz Wieczorek ([AmadeusW](https://github.com/AmadeusW))
- [#352](https://github.com/shouldly/shouldly/pull/352) - for issue #326, added ShouldContainMatchingCount contributed by Matthew D. Groves ([mgroves](https://github.com/mgroves))
- [#351](https://github.com/shouldly/shouldly/pull/351) - Added ShouldBeNullNotNull docs contributed by Joseph Woodward ([JosephWoodward](https://github.com/JosephWoodward))
- [#350](https://github.com/shouldly/shouldly/pull/350) - Added ShouldBeTrue and ShouldBeFalse docs contributed by Joseph Woodward ([JosephWoodward](https://github.com/JosephWoodward))
- [#349](https://github.com/shouldly/shouldly/pull/349) - Fixed 'DynamicShould' with dnx contributed by Chaitanya Gurrapu ([chaitanyagurrapu](https://github.com/chaitanyagurrapu))

Commits: f155864d5e...ba204c7ebf

### 2.7.0-beta.1  (2.7.0-beta.1)
<https://github.com/shouldly/shouldly/releases/tag/2.7.0-beta.1>

2.7.0 will be a pretty big release! The highlights are:
- PCL/CoreCLR support
- Way better error messages when source is not available, as time goes on we will bring better error messages to different PCL targets. At the moment PCL/CoreCLR cannot get at the source code of your tests so the error messages are not quite as good.
- Switched over to XUnit and removed our testbase class. This means those of you using the Visual Studio test explorer, Shouldlys test suite will now be usable for you.
- `ShouldMatchApproved` - Based on the awesome ApprovalTests.net, shouldly now has a simple and configurable version for strings. Have a look at the docs at http://shouldly.readthedocs.org/en/latest/assertions/shouldMatchApproved.html - Feedback on API and functionality welcome, especially during beta period
- We have a documentation project now which powers http://shouldly.readthedocs.org - We need help porting the docs to readthedocs! Jump in and pickup an assertion on #308
- Option to ignore line endings when comparing strings
- Plugged gaps in missing overloads and other small API inconsistencies

Please test and give feedback, _a lot_ has changed internally in shouldly for this release to happen and there are bound to be edge cases our tests do not cover (although they are getting pretty good now).

### Changelog:
- [#348](https://github.com/shouldly/shouldly/pull/348) - Wrote docs for new shouldMatchApproved and fixed up a few more issues… contributed by Jake Ginnivan ([JakeGinnivan](https://github.com/JakeGinnivan))
- [#347](https://github.com/shouldly/shouldly/pull/347) - Switched ShouldNotBe docs over to use examples, moved approved files … contributed by Jake Ginnivan ([JakeGinnivan](https://github.com/JakeGinnivan))
- [#346](https://github.com/shouldly/shouldly/pull/346) - Add support for the dotnet TFM contributed by Oren Novotny ([onovotny](https://github.com/onovotny))
- [#345](https://github.com/shouldly/shouldly/pull/345) - Created documentation samples project which outputs files to be inclu… contributed by Jake Ginnivan ([JakeGinnivan](https://github.com/JakeGinnivan))
- [#344](https://github.com/shouldly/shouldly/issues/344) - ShouldBeSameAs and reference equality
- [#343](https://github.com/shouldly/shouldly/pull/343) - Some constants missing in test projects contributed by Jake Ginnivan ([JakeGinnivan](https://github.com/JakeGinnivan))
- [#342](https://github.com/shouldly/shouldly/pull/342) - Initial pass at ShouldMatchApproved contributed by Jake Ginnivan ([JakeGinnivan](https://github.com/JakeGinnivan))
- [#341](https://github.com/shouldly/shouldly/pull/341) - Add support for coreclr/portable libraries contributed by Jake Ginnivan ([JakeGinnivan](https://github.com/JakeGinnivan))
- [#339](https://github.com/shouldly/shouldly/pull/339) - Dnx contributed by Jake Ginnivan ([JakeGinnivan](https://github.com/JakeGinnivan))
- [#338](https://github.com/shouldly/shouldly/pull/338) - Minor consistency tweaks to StringHelper.cs contributed by Joseph Woodward ([JosephWoodward](https://github.com/JosephWoodward))
- [#337](https://github.com/shouldly/shouldly/pull/337) [#301](https://github.com/shouldly/shouldly/issues/301) - Includes numeric suffixes in error messages contributed by Amadeusz Wieczorek ([AmadeusW](https://github.com/AmadeusW))
- [#336](https://github.com/shouldly/shouldly/pull/336) - String options clean up contributed by ([sholland1](https://github.com/sholland1))
- [#335](https://github.com/shouldly/shouldly/pull/335) - Xunit conversion contributed by Jake Ginnivan ([JakeGinnivan](https://github.com/JakeGinnivan))
- [#333](https://github.com/shouldly/shouldly/pull/333) - Should be with options contributed by ([sholland1](https://github.com/sholland1)) and Jake Ginnivan ([JakeGinnivan](https://github.com/JakeGinnivan))
- [#332](https://github.com/shouldly/shouldly/pull/332) - Fixed #330 contributed by Jake Ginnivan ([JakeGinnivan](https://github.com/JakeGinnivan))
- [#331](https://github.com/shouldly/shouldly/issues/331) - Support CoreCLR
- [#330](https://github.com/shouldly/shouldly/issues/330) - ShouldContainWithoutWhitespace uses Is.Equal not contains
- [#329](https://github.com/shouldly/shouldly/pull/329) - Finished off ShouldNotMatch contributed by Joseph Woodward ([JosephWoodward](https://github.com/JosephWoodward))
- [#328](https://github.com/shouldly/shouldly/pull/328) - Fix for #327 Mono NullReferenceException contributed by Nate Barbettini ([nbarbettini](https://github.com/nbarbettini))
- [#327](https://github.com/shouldly/shouldly/issues/327) - ShouldThrow fails under Mono
- [#325](https://github.com/shouldly/shouldly/pull/325) - Set thread culture within tests contributed by Joseph Woodward ([JosephWoodward](https://github.com/JosephWoodward))
- [#324](https://github.com/shouldly/shouldly/issues/324) - Tests fail with Hungarian regional settings
- [#321](https://github.com/shouldly/shouldly/pull/321) [#273](https://github.com/shouldly/shouldly/issues/273) - Implement ShouldBePositive() and ShouldBeNegative() for numeric types with sign contributed by Gert Nelissen ([gertnelissen](https://github.com/gertnelissen))
- [#319](https://github.com/shouldly/shouldly/pull/319) [#312](https://github.com/shouldly/shouldly/issues/312) - Made ShouldNotMatch with a test contributed by Brad ([bradarv90](https://github.com/bradarv90))
- [#318](https://github.com/shouldly/shouldly/pull/318) - Created ShouldNotMatch contributed by Brad ([bradarv90](https://github.com/bradarv90))
- [#317](https://github.com/shouldly/shouldly/pull/317) [#304](https://github.com/shouldly/shouldly/issues/304) - ShouldNotBe error message PR contributed by Christos Matskas ([cmatskas](https://github.com/cmatskas))
- [#316](https://github.com/shouldly/shouldly/pull/316) - Reworks docs to use Spinx and Rst contributed by Phil Scott ([enkafan](https://github.com/enkafan))
- [#315](https://github.com/shouldly/shouldly/pull/315) - Added ShouldNotBe DateTime (Offset) contributed by Joseph Woodward ([Joseph

_…truncated…_

### 2.6.0  (2.6.0)
<https://github.com/shouldly/shouldly/releases/tag/2.6.0>

- [#267](https://github.com/shouldly/shouldly/issues/267) - ShouldContain() fails when the item is in the list?
- [#266](https://github.com/shouldly/shouldly/pull/266) [#265](https://github.com/shouldly/shouldly/issues/265) - Updates NuGet tags for more search scenarios contributed by Amadeusz Wieczorek ([AmadeusW](https://github.com/AmadeusW))
- [#261](https://github.com/shouldly/shouldly/pull/261) - Should not throw message generator contributed by Jake Ginnivan ([JakeGinnivan](https://github.com/JakeGinnivan))
- [#260](https://github.com/shouldly/shouldly/issues/260) - Remove ShouldThrow/ShouldNotThrow?
- [#259](https://github.com/shouldly/shouldly/pull/259) - Should not throw message generator contributed by Yannis Güdel ([yannisgu](https://github.com/yannisgu))
- [#258](https://github.com/shouldly/shouldly/pull/258) - Added ShouldBeTrue|False and Null|NotNull extensions. contributed by Joseph Woodward ([JoeMighty](https://github.com/JoeMighty))
- [#257](https://github.com/shouldly/shouldly/pull/257) - Implementing ShouldBe with Case choice for IEnumerable<string> contributed by Julien Fiaffé ([JulienFiaffe](https://github.com/JulienFiaffe))
- [#256](https://github.com/shouldly/shouldly/issues/256) - Unexpected exception ShouldAssertException while testing string extension method...
- [#251](https://github.com/shouldly/shouldly/pull/251) - Adds Should(Not)BeNullOrWhiteSpace for strings contributed by Jake Ginnivan ([JakeGinnivan](https://github.com/JakeGinnivan))
- [#249](https://github.com/shouldly/shouldly/pull/249) - Added ShouldThrow and ShouldNotThrow extensions contributed by Joseph Woodward ([JoeMighty](https://github.com/JoeMighty))
- [#248](https://github.com/shouldly/shouldly/issues/248) - ShouldBe(True|False|Null) +Enhancement
- [#244](https://github.com/shouldly/shouldly/issues/244) - Add ShouldBe Case insensitive Enumerable<string> comparision +Enhancement
- [#243](https://github.com/shouldly/shouldly/pull/243) [#242](https://github.com/shouldly/shouldly/issues/242) - #242 Bugs/exception with null dictionary keys contributed by Andy McDowall ([andymcdowall](https://github.com/andymcdowall))
- [#241](https://github.com/shouldly/shouldly/pull/241) - Adds Should(Not)BeNullOrWhiteSpace for strings contributed by Bar Arnon ([i3arnon](https://github.com/i3arnon))
- [#240](https://github.com/shouldly/shouldly/pull/240) - NotThrowAsync implemented contributed by Yogiraj Aradhye ([YogirajA](https://github.com/YogirajA))
- [#235](https://github.com/shouldly/shouldly/pull/235) - Update Readme contributed by ([DavidSSL](https://github.com/DavidSSL))
- [#233](https://github.com/shouldly/shouldly/pull/233) - Highlight differences contributed by Chaitanya Gurrapu ([chaitanyagurrapu](https://github.com/chaitanyagurrapu))
- [#232](https://github.com/shouldly/shouldly/pull/232) - Should throw async fix contributed by Jake Ginnivan ([JakeGinnivan](https://github.com/JakeGinnivan))
- [#231](https://github.com/shouldly/shouldly/pull/231) [#172](https://github.com/shouldly/shouldly/issues/172) - Issue bug fix contributed by Yogiraj Aradhye ([YogirajA](https://github.com/YogirajA))
- [#230](https://github.com/shouldly/shouldly/pull/230) [#221](https://github.com/shouldly/shouldly/issues/221) - Issues/221  should contain without whitespace message generator contributed by Uri Goldstein ([urig](https://github.com/urig))
- [#229](https://github.com/shouldly/shouldly/pull/229) - ShouldContain and ShouldNotContain case sensitivity and tests contributed by Joseph Woodward ([JoeMighty](https://github.com/JoeMighty))
- [#228](https://github.com/shouldly/shouldly/pull/228) [#153](https://github.com/shouldly/shouldly/issues/153) [#238](https://github.com/shouldly/shouldly/pull/238)  - Added InstantHandle attribute to ShouldContain, ShouldAllBe and ShouldNotContain contributed by Joseph Woodward ([JoeMighty](https://github.com/JoeMighty))
- [#226](https://github.com/shouldly/shouldly/pull/226) [#184](https://github.com/shouldly/shouldly/issues/184) - Added InstantHandle attribute to ShouldThrow methods contributed by Joseph Woodward ([JoeMighty](https://github.com/JoeMighty))
- [#220](https://github.com/shouldly/shouldly/issues/220) - Should.NotThrow message generator +Enhancement
- [#213](https://github.com/shouldly/shouldly/issues/213) - Add extension methods on System.Action for ShouldThrow etc +Enhancement
- [#211](https://github.com/shouldly/shouldly/issues/211) - ShouldContain case sensitivity option +Enhancement
- [#205](https://github.com/shouldly/shouldly/pull/205) [#41](https://github.com/shouldly/shouldly/issues/41) [#239](https://github.com/shouldly/shouldly/pull/239) - Detailed string diff
- [#105](https://github.com/shouldly/shouldly/issues/105) - "Length cannot be less than zero" at Shouldly.ShouldlyMessage.ToString()

### 2.5.0  (2.5.0)
<https://github.com/shouldly/shouldly/releases/tag/2.5.0>

This release brings two major enhancements to Shouldly.

1) The ability to specify additional context in your Should calls. There are many times when the code and the error message just cannot provide enough context, no matter how good shouldly is. The additional info will simply be added under shouldly's already awesome messages.  
2) The message generator work has been pretty much completed, this is custom error messages for each of the types of shouldly methods. It basically means 2.5.0 will have _even better error messages_

This release has had a heap of community contributions with **12** different people submitting pull requests and a few of those being first time Open Source contributors. Thanks all who have contributed!
- [#190](https://github.com/shouldly/shouldly/issues/190) [#169](https://github.com/shouldly/shouldly/issues/169) [#195](https://github.com/shouldly/shouldly/pull/195) - Allow custom/additional message to ShouldlyMessage contributed by ([JoeMighty](https://github.com/JoeMighty)), Martin Leech ([mleech](https://github.com/mleech)), Aaron Powell ([aaronpowell](https://github.com/aaronpowell)) and Robert ([robertlyson](https://github.com/robertlyson))
- [#218](https://github.com/shouldly/shouldly/pull/218) - Added JetBrains.Annotations contributed by ([JoeMighty](https://github.com/JoeMighty))
- [#216](https://github.com/shouldly/shouldly/issues/216) - Should.Throw(Task) Overloads
- [#214](https://github.com/shouldly/shouldly/pull/214) - Custom message for ShouldCompleteIn and message generator for it
- [#206](https://github.com/shouldly/shouldly/issues/206) [#209](https://github.com/shouldly/shouldly/pull/209) - Add optional case sensitivity to Should[Not]StartWith and Should[Not]EndWith contributed by Chaitanya Gurrapu ([chaitanyagurrapu](https://github.com/chaitanyagurrapu))
- [#204](https://github.com/shouldly/shouldly/pull/204) - Added custom messages to ShouldBeDictionaryTestExtensions contributed by ([JoeMighty](https://github.com/JoeMighty))
- [#200](https://github.com/shouldly/shouldly/pull/200) - Message generator for ShouldBeSubsetOf contributed by Gabriel Weyer ([gabrielweyer](https://github.com/gabrielweyer))
- [#197](https://github.com/shouldly/shouldly/pull/197) - Fixed documentation link contributed by Gabriel Weyer ([gabrielweyer](https://github.com/gabrielweyer))
- [#191](https://github.com/shouldly/shouldly/pull/191) - Changed parameter of ShouldlyAssertionContext to IShouldlyAssertionConte... contributed by ([JoeMighty](https://github.com/JoeMighty))
- [#187](https://github.com/shouldly/shouldly/pull/187) [#185](https://github.com/shouldly/shouldly/issues/185) - Better expression printing contributed by Null ([ByteBlast](https://github.com/ByteBlast))
- [#182](https://github.com/shouldly/shouldly/pull/182) - Added ShouldContainMessageGenerator contributed by Dimitar Miloseski ([dimitar](https://github.com/dimitar))
- [#181](https://github.com/shouldly/shouldly/pull/181) - fix ShouldAllBe message generator contributed by Matt Kocaj ([cottsak](https://github.com/cottsak))
- [#179](https://github.com/shouldly/shouldly/issues/179) [#188](https://github.com/shouldly/shouldly/pull/188) - Client-friendly exception names contributed by Jimmy Bogard ([jbogard](https://github.com/jbogard))
- [#176](https://github.com/shouldly/shouldly/pull/176) - Cleaned up readme to point at docs.shouldly-lib.net
- [#174](https://github.com/shouldly/shouldly/issues/174) [#186](https://github.com/shouldly/shouldly/pull/186) [#178](https://github.com/shouldly/shouldly/pull/178) - Improve ShouldContain error message contributed by Uri Goldstein ([urig](https://github.com/urig))
- [#168](https://github.com/shouldly/shouldly/issues/168) - Update http://shouldly.github.io
- [#158](https://github.com/shouldly/shouldly/issues/158) - Message generator for ShouldBeSubsetOf
- [#150](https://github.com/shouldly/shouldly/issues/150) - ShouldAllBe message generator
- [#52](https://github.com/shouldly/shouldly/issues/52) - Refactor ShouldlyMessage to use Message Generators
- [#192](https://github.com/shouldly/shouldly/pull/192) - Adding Nunit test adapter so you don't need any VS plugins to run tests contributed by Aaron Powell ([aaronpowell](https://github.com/aaronpowell))

### 2.4.0  (2.4.0)
<https://github.com/shouldly/shouldly/releases/tag/2.4.0>

- [#165](https://github.com/shouldly/shouldly/pull/165) - Show count when .ShouldBeEmpty() fails for IEnumerable contributed by Matt Kocaj ([cottsak](https://github.com/cottsak))
- [#164](https://github.com/shouldly/shouldly/issues/164) [#167](https://github.com/shouldly/shouldly/pull/167) - Ignore case = true breaks comparison for yield break/yield return methods
- [#160](https://github.com/shouldly/shouldly/issues/160) - Multiple Assertions - see https://github.com/shouldly/shouldly#shouldSatisfyAllConditions
- [#105](https://github.com/shouldly/shouldly/issues/105) [#173](https://github.com/shouldly/shouldly/pull/173) - "Length cannot be less than zero" at Shouldly.ShouldlyMessage.ToString()

### 2.3.1  (2.3.1)
<https://github.com/shouldly/shouldly/releases/tag/2.3.1>

- #161 Implementing 'Multiple Assertion' scenario - contributed by @chaitanyagurrapu 
- #157 - Better message when ignoring order on ShouldBe

### 2.3.0  (2.3.0)
<https://github.com/shouldly/shouldly/releases/tag/2.3.0>

- [#155](https://github.com/shouldly/shouldly/pull/155) - Fix hardcoded datetimes in tests contributed by Ilya Murzinov ([ilya-murzinov](https://github.com/ilya-murzinov))
- [#151](https://github.com/shouldly/shouldly/pull/151) [#149](https://github.com/shouldly/shouldly/issues/149) - ShouldBe tolerance for dates contributed by Ben Scott ([bendetat](https://github.com/bendetat))
- [#148](https://github.com/shouldly/shouldly/pull/148) - Improving the messages for the Dictionary failure scenarios. contributed by Chaitanya Gurrapu ([chaitanyagurrapu](https://github.com/chaitanyagurrapu))
- [#145](https://github.com/shouldly/shouldly/pull/145) [#138](https://github.com/shouldly/shouldly/issues/138) - Implementing the 'DynamicShould.HaveProperty' functionality. contributed by Chaitanya Gurrapu ([chaitanyagurrapu](https://github.com/chaitanyagurrapu))
- [#144](https://github.com/shouldly/shouldly/pull/144) - Add ShouldBeUnique for collections contributed by Ilya Murzinov ([ilya-murzinov](https://github.com/ilya-murzinov))
- [#143](https://github.com/shouldly/shouldly/issues/143) - Dictionary "ShouldNotContainKeyAndValue" shows slightly incorrect message
- [#50](https://github.com/shouldly/shouldly/issues/50) - ShouldAll for IEnumerables

### v2.2.1  (2.2.1)
<https://github.com/shouldly/shouldly/releases/tag/2.2.1>

- Equality now checks reference equality before other strategies (#146)

### v2.2.0  (v2.2.0)
<https://github.com/shouldly/shouldly/releases/tag/v2.2.0>

- [#135](https://github.com/shouldly/shouldly/issues/135) - Should be on a list of strings fails +fix
- [#126](https://github.com/shouldly/shouldly/pull/126) - Tasks now timeout after 10 seconds
- [#136](https://github.com/shouldly/shouldly/pull/136) - Should be on a list of strings fails
- [#132](https://github.com/shouldly/shouldly/pull/132) - ShouldBe for IEnumerable with IgnoreOrder = true fails if objects are not IComparable contributed by Asger Hallas ([asgerhallas](https://github.com/asgerhallas))
- [#131](https://github.com/shouldly/shouldly/issues/131) - Case enum on string asserts could be renamed
- [#109](https://github.com/shouldly/shouldly/issues/109) - Task.ShouldCompleteIn (equivalent to NUnit Timeout Attribute) contributed by Gert Jansen van Rensburg ([gertjvr](https://github.com/gertjvr))

### v2.1.0  (v2.1.0)
<https://github.com/shouldly/shouldly/releases/tag/v2.1.0>

See [ReleaseNotes.md](https://github.com/shouldly/shouldly/blob/master/ReleaseNotes.md) for changes

### v2.0.1  (v2.0.1)
<https://github.com/shouldly/shouldly/releases/tag/v2.0.1>

See [ReleaseNotes.md](https://github.com/shouldly/shouldly/blob/master/ReleaseNotes.md) for changes

### v2.0.0  (v2.0.0)
<https://github.com/shouldly/shouldly/releases/tag/v2.0.0>

See [ReleaseNotes.md](https://github.com/shouldly/shouldly/blob/master/ReleaseNotes.md) for changes
