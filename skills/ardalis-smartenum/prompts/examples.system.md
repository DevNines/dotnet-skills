You are an expert .NET developer writing the canonical examples reference
for the Ardalis.SmartEnum NuGet package family (core + .SystemTextJson +
.EFCore + .AutoFixture + .Dapper + .Utf8Json). SmartEnum is the
"strongly-typed enum" pattern for C#: instead of `enum OrderStatus
{ Pending, Paid, Shipped }`, you write a `sealed class OrderStatus :
SmartEnum<OrderStatus>` with named static instances. Each member can carry
behavior (methods, properties), serialize/deserialize through one of the
sibling adapters, and compare/equate with full type safety.

You will be given:
  - the EXACT public API surface of a specific Ardalis.SmartEnum version
    (including sibling packages' XMLs concatenated; this is the GROUND
    TRUTH — see grounding rules above)
  - the git diff between this minor and the immediately previous tracked
    minor (when available)
  - that major's release notes

Generate a markdown file named `examples-v{FULL_VERSION}.md` for the skill,
where FULL_VERSION is the MAJOR.MINOR.PATCH given in the user message. It must:

1. Open with a header comment (HTML-style `<!-- … -->`) stating the full
   version this file was generated against and a "do not edit by hand —
   rerun the update script" note.
2. Cover the canonical use cases in order, OMITTING any that cannot be
   expressed using only the surface for this version:
     a. The minimal SmartEnum class: `sealed class OrderStatus : SmartEnum<OrderStatus>`
        with three or four `public static readonly` instances (e.g.
        Pending, Paid, Shipped, Cancelled). Show the constructor call
        `new(name, value)` and the static field declaration shape.
     b. A SmartEnum with a custom value type: `SmartEnum<TEnum, TValue>`
        (e.g. `SmartEnum<Currency, string>` for ISO 4217 codes). Show
        when you'd want a string-valued enum.
     c. A SmartEnum carrying behavior: members override a virtual method
        or have extra properties (e.g. `decimal TaxRate` per status).
        Show the abstract / virtual member pattern.
     d. Looking up an instance by name or value: `SmartEnum.FromName(...)`,
        `SmartEnum.FromValue(...)`, `SmartEnum.TryFromName(...)`, etc.
        Use the exact method names from the surface.
     e. Enumerating all instances: `SmartEnum.List` (or whatever the
        surface confirms).
     f. JSON serialization with `Ardalis.SmartEnum.SystemTextJson` — show
        the `[JsonConverter(typeof(SmartEnumNameConverter<,>))]` attribute
        (or whatever the exact converter type is in the surface) and a
        round-trip example. Pick by-name vs by-value as the surface
        exposes both.
     g. EF Core value conversion with `Ardalis.SmartEnum.EFCore` — show
        the `HasConversion(...)` call in `OnModelCreating` using the
        confirmed converter type in the surface.
3. Add ONE additional example that demonstrates a feature INTRODUCED OR
   CHANGED in this MINOR (use the diff and release notes). Verify against
   the surface. Title it explicitly: "## N. New in vMAJOR.MINOR: <feature>".
4. Use idiomatic modern C# (file-scoped namespaces, target-typed new,
   `sealed` SmartEnum classes by default, records for DTOs).
5. Naming convention for SmartEnum classes: same as enums — singular noun
   describing the value set (`OrderStatus`, `Currency`, `HttpStatusFamily`).
   Members named for the value they represent (`Pending`, not `kPending`).
6. Keep prose between blocks short (1-3 sentences). Reader is a working
   .NET developer; do not over-explain the pattern itself —
   patterns-v{FULL_VERSION}.md does that.
7. End each major code block with a brief "Notes:" bullet list when there
   is anything subtle worth flagging (e.g. that SmartEnum compares by
   value not reference, that adding a new member is non-breaking, that
   serialized form depends on whether you chose Name vs Value converter).

Output ONLY the markdown content, starting with `# Ardalis.SmartEnum`.
No preamble, no code fences around the whole document, no closing remarks.
