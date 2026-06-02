# NSubstitute — release notes by major

_Generated from `https://github.com/nsubstitute/NSubstitute/releases`. Use when answering migration questions or when a user asks what changed between versions._

## v6.x

### v6.0.0 Release Candidate 1  (v6.0.0-rc.1)
<https://github.com/nsubstitute/NSubstitute/releases/tag/v6.0.0-rc.1>

# NSubstitute v6.0.0 Release Candidate 1

Due to the large number of changes in this release, we wanted to start with a release candidate to ensure we've correctly captured breaking changes.

* [NEW] `ArgMatchers.Matching` predicate matcher as an alternative to `Is(Expression<Predicate<T>>`. (.NET6 and above.)
* [UPDATE] Improved support for custom argument matchers. `Arg.Is` now accepts arg matchers.
* [UPDATE][BREAKING] Update target frameworks: .NET8, .NET Standard 2.0
* [UPDATE][BREAKING] Remove legacy obsolete API
* [UPDATE][BREAKING] Mark as obsolete api CompatArg with pre c# 7.0 support
* [UPDATE][BREAKING] Nullability is enabled for public api for .NET 8+ TFMs
* [UPDATE] Migrate documentation to [docfx platform](https://github.com/dotnet/docfx) and update samples to NUnit 4
* [NEW] Added NuGet Package README file.


## Full change list

* Update target frameworks and other infrastructure changes by @Romfos in https://github.com/nsubstitute/NSubstitute/pull/831
* Remove Google Groups hyperlinks by @304NotModified in https://github.com/nsubstitute/NSubstitute/pull/804
* Improve output for expected argument matchers in https://github.com/nsubstitute/NSubstitute/pull/806
* Mark Substitute.For<T> method as Pure by @Dzliera in https://github.com/nsubstitute/NSubstitute/pull/844
* Move package creating from build.fsproj to github actions by @Romfos in https://github.com/nsubstitute/NSubstitute/pull/838
* Added .NET 9 to test matrix by @Romfos in https://github.com/nsubstitute/NSubstitute/pull/848
* Update dependencies by @Saibamen in https://github.com/nsubstitute/NSubstitute/pull/843
* Migrate documentation to docfx by @Romfos in https://github.com/nsubstitute/NSubstitute/pull/850
* Added test for issue #716 by @rbeurskens in https://github.com/nsubstitute/NSubstitute/pull/846
* feat: add dependabot for this project for minor and patch updates for nuget packages and github actions by @wmundev in https://github.com/nsubstitute/NSubstitute/pull/792
* #853 Fix matching with multiple generic arguments of the same type by @rholek in https://github.com/nsubstitute/NSubstitute/pull/858
* Ability to mock protected methods with and without return value by @Jason31569 in https://github.com/nsubstitute/NSubstitute/pull/845
* Enable nullability for public api by @Romfos in https://github.com/nsubstitute/NSubstitute/pull/856
* Bugfix/async event handlers return instantly by @jmartschinke in https://github.com/nsubstitute/NSubstitute/pull/808
* Fix matching generic calls with AnyType when the generic argument is also a generic argument in return type, out or ref parameter by @JMolenkamp in https://github.com/nsubstitute/NSubstitute/pull/862
* Feature: allow interception of any generic method call when using Arg.AnyType by @JMolenkamp in https://github.com/nsubstitute/NSubstitute/pull/855
* Params arg unit test by @Jason31569 in https://github.com/nsubstitute/NSubstitute/pull/874
* Added exception extensions for ValueTask without return type (rebase) in https://github.com/nsubstitute/NSubstitute/pull/873
* Migrate to slnx by @Romfos in https://github.com/nsubstitute/NSubstitute/pull/882
* Migrate documentation validation from build.fsproj to Roslyn code generator by @Romfos in https://github.com/nsubstitute/NSubstitute/pull/883
* Fix doc links (#884) in https://github.com/nsubstitute/NSubstitute/pull/886
* Add PackageReadmeFile. by @peymanr34 in https://github.com/nsubstitute/NSubstitute/pull/888
* Make public api and tests the same for all TFMs by @Romfos in https://github.com/nsubstitute/NSubstitute/pull/885
* Migrate documentation samples to NUnit4 by @Romfos in https://github.com/nsubstitute/NSubstitute/pull/889
* Run unit tests in Microsoft.Testing.Platform mode by @Romfos in https://github.com/nsubstitute/NSubstitute/pull/896
* Bump actions/checkout from 4 to 5 by @dependabot[bot] in https://github.com/nsubstitute/NSubstitute/pull/902
* Fix typo in return value documentation by @ericmutta in https://github.com/nsubstitute/NSubstitute/pull/903
* Bump actions/setup-dotnet from 4 to 5 by @dependabot[bot] in https://github.com/nsubstitute/NSubstitute/pull/907
* Fix typo in received calls documentation by @ericmutta in https://github.com/nsubstitute/NSubstitute/pull/904
* Simplify github actions to use less jobs by @Romfos in https://github.com/nsubstitute/NSubstitute/pull/911
* Bump actions/upload-artifact from 4 to 5 by @dependabot[bot] in https://github.com/nsubstitute/NSubstitute/pull/916
* Bump NUnit3TestAdapter from 5.0.0 to 5.2.0 by @dependabot[bot] in https://github.com/nsubstitute/NSubstitute/pull/922
* Bump BenchmarkDotNet from 0.15.2 to 0.15.5 by @dependabot[bot] in https://github.com/nsubstitute/NSubstitute/pull/921
* Add .NET 10 to test matrix by @Romfos in https://github.com/nsubstitute/NSubstitute/pull/913
* Bump Microsoft.Extensions.Logging.Abstractions from 9.0.0 to 10.0.0 by @dependabot[bot] in https://github.com/nsubstitute/NSubstitute/pull/926
* Bump actions/checkout from 5 to 6 by @dependabot[bot] in https://github.com/nsubstitute/NSubstitute/pull/928
* Bump Microsoft.CodeAnalysis.CSharp from 4.14.0 to 5.0.0 by @dependabot[bot] in https://github.com/nsubstitute/NSubstitute/pull/929
* Bump BenchmarkDotNet from 0.15.5 to 0.15.6 by @dependabot[bot] in https://github.com/nsubstitute/NSubstitute/pull/924
* Bump BenchmarkDotNet from 0.15.6 to 0.15.8 by @dependabot[bot] in https://github.com/nsubstitute/NSubstitute/pull/930
* Bump NUnit3TestAdapter from 5.2.0 to 6.0.0 by @dependabot[bot] in https://github.com/nsubstitute/NSubstitute/pull/931
* Fix XML docs for WhenCalled.Throws by @kerego in https://github.com/nsubstitute/NSubstitute/pull/934
* Bump NUnit3TestAdapter from 5.2.0 to 6.0.0 by @dependabot[bot] in https://github.com/nsubstitute/NSubstitute/pull/937
* Bump Microsoft.Extensions.Logging.Abstractions from 10.0.0 to 10.0.1 by @dependabot[bot] in https://github.com/nsubstitute/NSubstitute/pull/936
* Bump actions/upload-ar

_…truncated…_


## v5.x

### v5.3.0  (v5.3.0)
<https://github.com/nsubstitute/NSubstitute/releases/tag/v5.3.0>

* [NEW] Introduced `Substitute.ForTypeForwardingTo` to create substitutes that forward interceptable calls to a concrete class. This provides an easy way of implementing a test spy over an existing type. Designed and implemented by @marcoregueira in https://github.com/nsubstitute/NSubstitute/pull/700 from a proposal by @wsaeed. Thanks to all who contributed to discussions of this feature.
* [NEW] Support Raise.EventWith default constructor (#788) by @mihnea-radulescu in https://github.com/nsubstitute/NSubstitute/pull/813
* [NEW] Implement When(...).Throws to avoid confusion with Throw method (#803) by @mihnea-radulescu in https://github.com/nsubstitute/NSubstitute/pull/818
* [FIX] Arg.Any<Arg.AnyType>() does not match arguments passed by reference (#787) by @mihnea-radulescu in https://github.com/nsubstitute/NSubstitute/pull/811
* [FIX] Support matching arguments whose type is generic, when their concrete type is not known (#786) by @mihnea-radulescu in https://github.com/nsubstitute/NSubstitute/pull/814
* [FIX] Release build workflow (https://github.com/nsubstitute/NSubstitute/pull/797)
* [DOC] Add Throws for exceptions to the docs by @304NotModified in https://github.com/nsubstitute/NSubstitute/pull/795
* [DOC] Remove Visual Studio for Mac from readme by @Romfos in https://github.com/nsubstitute/NSubstitute/pull/807
* [TECH] Migrate from NUnit 3 to NUnit 4 by @Romfos in https://github.com/nsubstitute/NSubstitute/pull/783
* [TECH] Update build project to .net 8 by @Romfos in https://github.com/nsubstitute/NSubstitute/pull/776
* [TECH] Code style: use C# 12 collection literals by @Romfos in https://github.com/nsubstitute/NSubstitute/pull/810
* [TECH] Use c# 12 primary constructors by @Romfos in https://github.com/nsubstitute/NSubstitute/pull/812
* [TECH] Added csharp_style_prefer_primary_constructors into editorconfig by @Romfos in https://github.com/nsubstitute/NSubstitute/pull/819

Thanks to first-time contributors @mihnea-radulescu and @marcoregueira! Thanks also @304NotModified and @Romfos for their continued support and contributions to this release.


**Full Changelog**: https://github.com/nsubstitute/NSubstitute/compare/v5.2.0...v5.3.0

### v5.2.0  (v5.2.0)
<https://github.com/nsubstitute/NSubstitute/releases/tag/v5.2.0>

⚠️ **Note: there is no build currently available for this version due to an issue switching over to a new automated release build. We'll have a new release shortly once we sort this.**

<!-- We've released NSubstitute v5.2.0. -->

Summary of main changes:

*    [UPDATE] Upgrade website build to jekyll 3.9.0 and add link to edit website pages (#767, #769; thanks to @brad)
*    [UPDATE] Build improvements:
        - migrate to GitHub Actions and update doc dependencies (#754, #774; thanks to @alexandrnikitin)
        - improve test platform coverage; add .NET 8 to test platforms (#742, #756; thanks to @Romfos)
        - source code format improvements; check format on CI (#758, ##761, #762, #763; thanks again to @Romfos)
*    [NEW] Support for Sourcelink and Deterministic Build. Thanks @304NotModified! (#737)

Many thanks to @alexandrnikitin, @Romfos, @brad, and @304NotModified for their contributions!
Thanks a lot to all code contributors, reviewers, and people who have raised and/or commented on issues.

If you haven't already done so, please make sure you add the NSubstitute.Analyzers package wherever you reference NSubstitute: https://nsubstitute.github.io/help/nsubstitute-analysers/

As always, please raise an [issue on GitHub](https://github.com/nsubstitute/NSubstitute/issues) if you have any problems.

Changelog: https://github.com/nsubstitute/NSubstitute/blob/v5.2.0/CHANGELOG.md
Breaking changes: None.

Project links:

*    NuGet:
        - https://www.nuget.org/packages/NSubstitute
        - https://www.nuget.org/profiles/NSubstitute
*    GitHub: [http://github.com/nsubstitute/NSubstitute](https://github.com/nsubstitute/NSubstitute)
*    Web: http://nsubstitute.github.io/

## Change list

* Documentation: introduce clickable tooltips to copy hx url by @jheinath in https://github.com/nsubstitute/NSubstitute/pull/736
* Move CI to GitHub actions by @alexandrnikitin in https://github.com/nsubstitute/NSubstitute/pull/740
* Support Sourcelink and Deterministic Build by @304NotModified in https://github.com/nsubstitute/NSubstitute/pull/737
* [Github] Run unit tests for all test platforms by @Romfos in https://github.com/nsubstitute/NSubstitute/pull/742
* Move from AppVeyor to GitHub Actions by @alexandrnikitin in https://github.com/nsubstitute/NSubstitute/pull/754
* Added .NET 8 to test platforms by @Romfos in https://github.com/nsubstitute/NSubstitute/pull/756
* Format source code and add format verification on ci by @Romfos in https://github.com/nsubstitute/NSubstitute/pull/758
* Format NSubstitute.csproj layout + remove unusable code for net4.5 by @Romfos in https://github.com/nsubstitute/NSubstitute/pull/761
* Enable ImplicitUsings by @Romfos in https://github.com/nsubstitute/NSubstitute/pull/762
* Use file scoped namepsaces by @Romfos in https://github.com/nsubstitute/NSubstitute/pull/763
* Upgrade jekyll to 3.9.0 by @brad in https://github.com/nsubstitute/NSubstitute/pull/768
* add edit this page link by @brad in https://github.com/nsubstitute/NSubstitute/pull/769
* [CI] Do not build on every push by @alexandrnikitin in https://github.com/nsubstitute/NSubstitute/pull/774
* [Docs] Update Ruby and docs dependencies to the latest versions by @alexandrnikitin in https://github.com/nsubstitute/NSubstitute/pull/773
* Prep for v5.2 release by @dtchepak in https://github.com/nsubstitute/NSubstitute/pull/791

## New Contributors
* @brad made their first contribution in https://github.com/nsubstitute/NSubstitute/pull/768

**Full Changelog**: https://github.com/nsubstitute/NSubstitute/compare/v5.1.0...v5.2.0

### v5.1.0  (v5.1.0)
<https://github.com/nsubstitute/NSubstitute/releases/tag/v5.1.0>

We've released NSubstitute v5.1.0!

**Changes:**

* [DOC] Add clickable headings. Thanks @jheinath! (#729)
* [UPDATE] Update Castle.Core to 5.1.1-* to support C# 9 covariants. Thanks @siblount to tracking this down. (#730)
* [UPDATE] Improved support for testing ILogger. Thanks to @zlangner for this contribution, and also thanks to @Saibamen for reviewing this PR. (#732)
* [NEW] Add Arg.AnyType for matching calls with generic parameters. Thanks @icalvo for implementing and documenting this! (#634, #715, #733).

Thanks a lot to all code contributors, reviewers, and people who have raised and/or commented on issues.

If you haven't already done so, please make sure you add the NSubstitute.Analyzers package wherever you reference NSubstitute: https://nsubstitute.github.io/help/nsubstitute-analysers/

As always, please raise an [issue on GitHub](https://github.com/nsubstitute/NSubstitute/issues) if you have any problems.

**Changelog:** https://github.com/nsubstitute/NSubstitute/blob/v5.1.0/CHANGELOG.md
**Breaking changes:** NSubstitute Analyzers may produce [false positives in some cases for `Arg.AnyType`](https://github.com/nsubstitute/NSubstitute/pull/715#issuecomment-1712043274). Follow https://github.com/nsubstitute/NSubstitute.Analyzers/issues/212 for progress on this. These warnings can be suppressed if required.

Project links:
* NuGet:
    - https://www.nuget.org/packages/NSubstitute
    - https://www.nuget.org/profiles/NSubstitute
* GitHub: http://github.com/nsubstitute/NSubstitute
* Web: http://nsubstitute.github.io/

### v5.0.0  (v5.0.0)
<https://github.com/nsubstitute/NSubstitute/releases/tag/v5.0.0>

Hi all,

We've released NSubstitute v5.0.0. This release updates our target frameworks to the ones [recommended by Microsoft](https://learn.microsoft.com/en-us/dotnet/core/compatibility/core-libraries/6.0/older-framework-versions-dropped): .NET 6+, .NET Framework 4.6.2+, .NET Standard 2.0+. Thanks to @Romfos for this change (#710), and @alexandrnikitin for the review and merge. Thanks also to @TillW for some clarifications to our docs on internal members (#706).

See full release notes here: https://github.com/nsubstitute/NSubstitute/releases/tag/v5.0.0

Thanks a lot to all code contributors, reviewers, and people who have raised and/or commented on issues.

If you haven't already done so, please make sure you add the NSubstitute.Analyzers package wherever you reference NSubstitute: https://nsubstitute.github.io/help/nsubstitute-analysers/

As always, please raise an [issue on GitHub](https://github.com/nsubstitute/NSubstitute/issues) if you have any problems.

**Changelog:** https://github.com/nsubstitute/NSubstitute/blob/v5.0.0/CHANGELOG.md
**Breaking changes:**
* Dropped support for older platforms. Minimum versions now .NET 6+, .NET Framework 4.6.2+, .NET Standard 2.0+

**Project links:**
* NuGet:
    - https://www.nuget.org/packages/NSubstitute
    - https://www.nuget.org/profiles/NSubstitute
* GitHub: http://github.com/nsubstitute/NSubstitute
* Web: http://nsubstitute.github.io/

## What's Changed
* Revised chapter 'Internal members' by @x789 in https://github.com/nsubstitute/NSubstitute/pull/706
* Fix CI by @alexandrnikitin in https://github.com/nsubstitute/NSubstitute/pull/711
* Update target frameworks for .NET 6, .NET Framework 4.6.2, .NET Standard 2.0 by @Romfos in https://github.com/nsubstitute/NSubstitute/pull/710

## New Contributors
* @Romfos made their first contribution in https://github.com/nsubstitute/NSubstitute/pull/710

**Full Changelog**: https://github.com/nsubstitute/NSubstitute/compare/v4.4.0...v5.0.0


## v4.x

### v4.4.0  (v4.4.0)
<https://github.com/nsubstitute/NSubstitute/releases/tag/v4.4.0>

Hi all,

We've released NSubstitute v4.4.0. This adds support for Castle Core v5, thanks to @Havunen (#690, #673), as well as fixing an issue checking for constructor args on null object, courtesy of @phongphanq, and @appel1 (#683, #685). Thanks also to @Mandroide for the code review. @Socolin has also added `.ThrowsAsync()` that will correctly mock exceptions on async methods (#609, #663).

Thanks a lot to all code contributors, reviewers, and people who have raised and/or commented on issues.

If you haven't already done so, please make sure you add the NSubstitute.Analyzers package wherever you reference NSubstitute: https://nsubstitute.github.io/help/nsubstitute-analysers/

As always, please [raise an issue on GitHub](https://github.com/nsubstitute/NSubstitute/issues) if you have any problems.

Changelog: https://github.com/nsubstitute/NSubstitute/blob/v4.4.0/CHANGELOG.md
Breaking changes: There should be no breaking changes with this release.
Project links:

  * NuGet:
      -  https://www.nuget.org/packages/NSubstitute
      -   https://www.nuget.org/profiles/NSubstitute
  * GitHub: [http://github.com/nsubstitute/NSubstitute](https://github.com/nsubstitute/NSubstitute)
  * Web: http://nsubstitute.github.io/

## What's Changed
* Add `.ThrowsAsync()` that will correctly mock exception on async methods by @Socolin in https://github.com/nsubstitute/NSubstitute/pull/663
* Updated NSubstitute to v5 for modern TFMs by @Havunen in https://github.com/nsubstitute/NSubstitute/pull/690
* CastleDynamicProxyFactory_HasItem_true_when_array_is_null by @phongphanq in https://github.com/nsubstitute/NSubstitute/pull/683
* Add support for `ReturnsNull` calls for nullable value types by @Stedoss in https://github.com/nsubstitute/NSubstitute/pull/692

## New Contributors
* @Socolin made their first contribution in https://github.com/nsubstitute/NSubstitute/pull/663
* @phongphanq made their first contribution in https://github.com/nsubstitute/NSubstitute/pull/683
* @Stedoss made their first contribution in https://github.com/nsubstitute/NSubstitute/pull/692

**Full Changelog**: https://github.com/nsubstitute/NSubstitute/compare/v4.3.0...v4.4.0

### v4.3.0  (v4.3.0)
<https://github.com/nsubstitute/NSubstitute/releases/tag/v4.3.0>

Hi everyone,

We've just released NSubstitute v4.3.0. This introduces support for .NET 5 (#636) and .NET 6 (#674). Thanks to @zvirja and @Havunen!

If you haven't already done so, please make sure you add the NSubstitute.Analyzers package wherever you reference NSubstitute: <https://nsubstitute.github.io/help/nsubstitute-analysers/>

As always, please [raise an issue on GitHub](https://github.com/nsubstitute/NSubstitute/issues) or [email the group](http://groups.google.com/group/nsubstitute) if you have any problems.

Changelog: <https://github.com/nsubstitute/NSubstitute/blob/v4.3.0/CHANGELOG.md>

Breaking changes: There should be no breaking changes with this release.

Project links:
* NuGet: 
    + https://www.nuget.org/packages/NSubstitute
    + https://www.nuget.org/profiles/NSubstitute
* GitHub: http://github.com/nsubstitute/NSubstitute
* Web: http://nsubstitute.github.io/

## What's Changed

* Handle protected and internal property setters by @zvirja in https://github.com/nsubstitute/NSubstitute/pull/627
* Fix typo in help. Changed "was" to "way". by @DarqueWarrior in https://github.com/nsubstitute/NSubstitute/pull/628
* Add .NET 5 target and arrange nullability attributes by @zvirja in https://github.com/nsubstitute/NSubstitute/pull/636
* Slightly refactor code to make it look fresh by @zvirja in https://github.com/nsubstitute/NSubstitute/pull/639
* Update Castle.Core min from 4.4.0 to 4.4.1 by @dtchepak in https://github.com/nsubstitute/NSubstitute/pull/640
* doc: Update property received checking to make use of Discards by @rugk in https://github.com/nsubstitute/NSubstitute/pull/651
* Ignore "null handlers" when a substituted event is raised by @x789 in https://github.com/nsubstitute/NSubstitute/pull/667
* Add argument matching tests to demonstrate matching of value and reference types by @suzicurran in https://github.com/nsubstitute/NSubstitute/pull/671
* Added .Net6 target framework by @Havunen in https://github.com/nsubstitute/NSubstitute/pull/674
* Prep for 4.3.0 release by @dtchepak in https://github.com/nsubstitute/NSubstitute/pull/678

## New Contributors

* @DarqueWarrior made their first contribution in https://github.com/nsubstitute/NSubstitute/pull/628
* @rugk made their first contribution in https://github.com/nsubstitute/NSubstitute/pull/651
* @x789 made their first contribution in https://github.com/nsubstitute/NSubstitute/pull/667
* @suzicurran made their first contribution in https://github.com/nsubstitute/NSubstitute/pull/671
* @Havunen made their first contribution in https://github.com/nsubstitute/NSubstitute/pull/674

**Full Changelog**: https://github.com/nsubstitute/NSubstitute/compare/v4.2.2...v4.3.0

### v4.2.2  (v4.2.2)
<https://github.com/nsubstitute/NSubstitute/releases/tag/v4.2.2>

Hi everyone,

We've just released NSubstitute 4.2.2. This patch release fixes a thread-safety issue with auto-value providers (#600, #601). Thanks to Alex Povar (@zvirja) for these changes. 

If you haven't already done so, please make sure you add the NSubstitute.Analyzers package wherever you reference NSubstitute: <https://nsubstitute.github.io/help/nsubstitute-analysers/>

As always, please [raise an issue on GitHub](https://github.com/nsubstitute/NSubstitute/issues) or [email the group](http://groups.google.com/group/nsubstitute) if you have any problems.

Changelog: <https://github.com/nsubstitute/NSubstitute/blob/v4.2.2/CHANGELOG.md>

Breaking changes: There should be no breaking changes with this release.

Project links:
* NuGet: 
    + https://www.nuget.org/packages/NSubstitute
    + https://www.nuget.org/profiles/NSubstitute
* GitHub: http://github.com/nsubstitute/NSubstitute
* Web: http://nsubstitute.github.io/
