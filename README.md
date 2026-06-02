# .NET Skills for Claude Code

Version-aware [Claude Code](https://docs.claude.com/en/docs/claude-code) skills for the .NET ecosystem, shipped as a single installable plugin.

Each skill detects the **exact version** of a library your project pins (from `.csproj` / `Directory.Packages.props`) and loads reference material generated against that version — so the code Claude writes matches the API surface you actually have, never a member that doesn't exist in your version.

## Install

In Claude Code:

```
/plugin marketplace add DevNines/dotnet-skills
/plugin install devnines-dotnet-skills@devnines-skills
```

The first command registers this repo as a plugin marketplace; the second installs the plugin. All skills below are then auto-discovered — each one triggers on its own description when your task calls for it. Manage or remove it any time from the `/plugin` menu.

## Skills

| Skill | Library |
|---|---|
| `ardalis-guardclauses` | [Ardalis.GuardClauses](https://github.com/ardalis/GuardClauses) — precondition / argument-validation helpers |
| `ardalis-result` | [Ardalis.Result](https://github.com/ardalis/Result) — Result pattern (core + AspNetCore + FluentValidation) |
| `ardalis-smartenum` | [Ardalis.SmartEnum](https://github.com/ardalis/SmartEnum) — strongly-typed enums (core + SystemTextJson + EFCore + Dapper + AutoFixture + Utf8Json) |
| `ardalis-spec` | [Ardalis.Specification](https://github.com/ardalis/Specification) — Specification pattern (core + EFCore + EF6) |
| `fastendpoints` | [FastEndpoints](https://github.com/FastEndpoints/FastEndpoints) — REPR-pattern endpoints (core + Swagger + Security + Validation + Generator + Messaging.* + Attributes) |
| `nsubstitute` | [NSubstitute](https://github.com/nsubstitute/NSubstitute) — mocking for tests |
| `shouldly` | [Shouldly](https://github.com/shouldly/shouldly) — fluent test assertions |
| `stripe` | [Stripe.net](https://github.com/stripe/stripe-dotnet) — official Stripe .NET SDK (two-tier surface: service index + curated core-resource detail) |

## How "version-aware" works

Every skill ships a `SKILL.md` plus one trio of reference files **per tracked version** (`api-surface`, `examples`, `patterns`) and a `migration-notes` file. When you ask for help, the skill:

1. Detects the full `MAJOR.MINOR.PATCH` your project pins for that package.
2. Loads the closest-matching reference trio (exact full match → same-minor highest patch → same-major lower-or-equal minor).
3. Writes/reviews/migrates code grounded in that exact surface — it won't recommend a member that doesn't exist in your version.

The reference files are regenerated automatically as new library versions ship, so tracking accumulates forever: a project pinned to an older patch still gets correct docs.

## License

[MIT](./LICENSE) © DevNines
