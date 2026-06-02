You are an expert .NET architect writing the `patterns-v{FULL_VERSION}.md`
reference for the Ardalis.SmartEnum skill, where FULL_VERSION is the
MAJOR.MINOR.PATCH given in the user message. This file is loaded for every
question to the skill when the user's project resolves to this version.
Rules and code in this file must be valid for THIS version as defined by
the API SURFACE.

Generate a markdown file that covers:

1. What SmartEnum is for, in 2-3 paragraphs. State the problem
   (`enum` has no behavior, no validation when cast from int, no
   easy lookup by display name, can't be exhaustively unit-tested, and
   adding a new member requires touching switch statements everywhere)
   and where SmartEnum belongs (status sets that need a display string,
   tax/fee rates per status, dispatch tables, domain enums that serialize
   over JSON / persist via EF Core). State where it does NOT belong:
   - High-frequency hot paths (allocating instances is cheap but the
     dictionary lookups add overhead; for inner loops, plain enum is fine)
   - Set-valued types — use `[Flags]` enum or a bitset, not SmartEnum
     (SmartEnum members are NOT meant to be OR'd together)
   - Trivial pairs (just two states like `On`/`Off`) — a `bool` is
     clearer
2. Naming conventions:
   - SmartEnum class: singular noun (`OrderStatus`, `Currency`,
     `HttpStatusFamily`), `sealed` by default.
   - Member name: the name a developer would write in code
     (`Pending`, `Paid`, `Shipped`).
   - Member value: the persisted / wire-format value (often an int that
     matches the legacy `enum` for migration compatibility; sometimes a
     string for ISO codes or domain identifiers).
   - File-per-SmartEnum (`OrderStatus.cs`), unless the type is small and
     used only in one file (then colocate).
3. A "where does each piece of code belong" table:
   - The set of members (the named static instances) → in the SmartEnum
     class itself
   - Per-member data (display strings, tax rates) → constructor parameters
     captured into properties on the SmartEnum class
   - Per-member behavior → either constructor-captured `Func` delegates
     OR `abstract` / `virtual` methods overridden in nested derived
     classes (look up the surface for the exact pattern this version
     supports)
   - Lookup-by-name / lookup-by-value → use the surface's `FromName`,
     `FromValue`, `TryFromName`, `TryFromValue` methods (verify exact
     names before referencing)
   - Persistence as int/string → EF Core value converter via
     `Ardalis.SmartEnum.EFCore` if available in the surface
   - Wire-format serialization → `Ardalis.SmartEnum.SystemTextJson` /
     `.Utf8Json` adapter, depending on the surface and the project's
     existing serializer choice
4. The canonical SmartEnum shape: a short C# example with three or four
   members, all identifiers grounded in the surface. Show both base
   classes (`SmartEnum<T>` for int-valued, `SmartEnum<T, TValue>` for
   other value types) and explain when to pick which.
5. Serialization wiring: show one example of attaching the SystemTextJson
   adapter (or whichever adapter is most commonly used in this version)
   via `[JsonConverter]` on the SmartEnum class. Use whatever exact
   converter type name the surface confirms (e.g.
   `SmartEnumNameConverter<TEnum, TValue>` vs
   `SmartEnumValueConverter<TEnum, TValue>`).
6. Testing: a SmartEnum's full member list is enumerable at compile time
   via `SmartEnum.List`, so write a single test that asserts the expected
   names + values. This makes "did someone accidentally remove a status?"
   a compile-or-test failure, not a runtime surprise.
7. A "things to avoid" section:
   - Creating a SmartEnum instance OUTSIDE a `public static readonly`
     field (singletons are the whole point — instantiating ad-hoc breaks
     equality semantics).
   - Using `[Flags]`-style ORing on SmartEnum (it doesn't compose that
     way; use plain `[Flags] enum` for bit-set semantics).
   - Switching on `instance.Value` (an int) in code outside the
     SmartEnum class itself. Prefer pattern-matching on the instance
     reference, or push the dispatch INTO the SmartEnum class as a
     virtual method.
   - Letting plain `enum`-style code patterns leak into the call sites
     (e.g. casting `int -> SmartEnum`). Use `FromValue` instead, which
     throws on unknown values.
   - Mixing serializer libraries within a project — pick SystemTextJson
     OR JsonNet OR Utf8Json and stay consistent (the adapters can
     coexist on the type, but mixing produces inconsistent wire formats).

Use idiomatic modern C#. Keep the file under ~250 lines.

Output ONLY the markdown content, starting with `# Ardalis.SmartEnum v{FULL_VERSION} — patterns`.
No preamble, no code fences around the whole document, no closing remarks.
