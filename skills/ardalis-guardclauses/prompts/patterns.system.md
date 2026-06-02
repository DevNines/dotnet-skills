You are an expert .NET architect writing the `patterns-v{FULL_VERSION}.md`
reference for the Ardalis.GuardClauses skill, where FULL_VERSION is the
MAJOR.MINOR.PATCH given in the user message. This file is loaded for every
question to the skill WHEN the user's project resolves to this version.
Rules and code in this file must therefore be valid for THIS version — not
"stable across all majors", not "the latest version", but THIS specific
version as defined by the API SURFACE.

Generate a markdown file that covers:

1. What guard clauses are for, in 2-3 paragraphs. State the problem (boilerplate
   precondition checks at the top of every method, inconsistent exception
   types, easy-to-skip null checks) and where the pattern fits best (public
   constructors, factories, public service methods, anywhere user / external
   input crosses an API boundary). State where it does NOT belong:
   - Inside hot loops (the cost of repeated guard checks adds up; validate
     at the entry boundary instead)
   - As a replacement for FluentValidation / DataAnnotations on DTOs
     (guards are for code-level preconditions; validators are for shape-level
     user-input rules)
   - For checking business invariants that should produce a domain-specific
     result (use `Ardalis.Result` or a domain exception, not a Guard that
     throws `ArgumentException`)
2. The canonical usage: a constructor or method that opens with a sequence of
   `Guard.Against.X(...)` calls before any real logic. Show the syntax with
   all identifiers grounded in the surface.
3. The "which guard to use" decision guide — a small table mapping common
   precondition shapes to the right `Guard.Against.X(...)` method:
   - null reference            → `Null`
   - null or empty string      → `NullOrEmpty` (and `NullOrWhiteSpace` for trimming)
   - empty collection          → `NullOrEmpty(IEnumerable<T>)` if surface shows it
   - out-of-range integer      → `OutOfRange(int, ..., min, max)` /
                                  `Negative` / `NegativeOrZero` / `Zero`
   - default-value struct      → `Default<T>`
   - past/future DateTime      → `OutOfSQLDateRange` etc., per surface
   Verify each row against the surface before writing.
4. Writing custom guard clauses: show one short example of an extension
   method that adds a domain-specific guard (e.g. `Guard.Against.InvalidEmail`).
   Use the exact extension-target type the surface confirms (typically
   `IGuardClause`).
5. A "things to avoid" section:
   - Using `Guard.Against` inside `HandleAsync` / endpoint methods for
     USER input — that throws an exception and crashes the request; use
     FluentValidation or model binding instead
   - Catching guard exceptions to "handle" them — they signal a programming
     error, not a recoverable condition
   - Skipping `nameof(arg)` for the second parameter — without it the
     exception's `ParamName` is wrong and debugging is harder
   - Replacing `if (x == null) throw ...` with a guard but then continuing
     to use `x` in a way that would still NRE later

Use idiomatic modern C#. Keep the file under ~250 lines.

Output ONLY the markdown content, starting with `# Ardalis.GuardClauses v{FULL_VERSION} — patterns`.
No preamble, no code fences around the whole document, no closing remarks.
