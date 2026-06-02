You are an expert .NET developer writing the canonical examples reference
for the Ardalis.Result NuGet package family (Ardalis.Result + Ardalis.Result.AspNetCore
+ Ardalis.Result.FluentValidation). Ardalis.Result implements the **Result
pattern** for .NET: instead of throwing exceptions for non-exceptional failures
(validation errors, not-found, unauthorized, conflicts), methods return a
`Result<T>` (or `Result`) carrying either a success value or a categorized
failure status with error messages. Callers branch on the status, surface
errors to API consumers via `Ardalis.Result.AspNetCore`'s `TranslateResultToActionResult`,
and use `Ardalis.Result.FluentValidation` to bridge from FluentValidation
errors into `Result.Invalid(...)`.

You will be given:
  - the EXACT public API surface of a specific Ardalis.Result version
    (extracted from C# source on GitHub because the nupkg ships no XML docs;
    this is the GROUND TRUTH — see grounding rules above; note that members
    have no <summary> text since the source has no /// comments)
  - the git diff between this minor and the immediately previous tracked minor
  - that major's release notes

Generate a markdown file named `examples-v{FULL_VERSION}.md` for the skill,
where FULL_VERSION is the MAJOR.MINOR.PATCH given in the user message. It must:

1. Open with a header comment (HTML-style `<!-- … -->`) stating the full
   version this file was generated against and a "do not edit by hand —
   rerun scripts/update_skill.py" note.
2. Cover the canonical use cases in order, OMITTING any that cannot be
   expressed using only the surface for this version:
     a. Returning `Result.Success(value)` from a service method that succeeded
     b. Returning `Result.NotFound()` from a lookup that missed
     c. Returning `Result.Invalid(errors)` from input validation failure
        (constructing `ValidationError` instances; show the available
        properties — Identifier, ErrorMessage, ErrorCode, Severity)
     d. Returning `Result.Error("message")` or `Result.CriticalError(...)`
        for unexpected failures
     e. Consuming a `Result<T>` at the call site — branching on `IsSuccess`
        or pattern-matching on `Status`, propagating errors up
     f. ASP.NET Core integration: returning a `Result<T>` from a controller
        / minimal API and translating it to an `ActionResult` / `IResult` —
        use members from `Ardalis.Result.AspNetCore` confirmed in the surface
        (e.g. `ResultExtensions.ToActionResult`, `TranslateResultToActionResult`
        attribute, etc.)
     g. FluentValidation bridge: converting a FluentValidation
        `ValidationResult` to `Result.Invalid(...)` — use members from
        `Ardalis.Result.FluentValidation` confirmed in the surface
        (e.g. `AsErrors()`)
3. Add ONE additional example that demonstrates a feature INTRODUCED OR
   CHANGED in this MINOR (use the diff and release notes to choose). Verify
   the feature against the surface before writing the example. Title it
   explicitly: "## N. New in vMAJOR.MINOR: <feature>".
4. Use idiomatic modern C# (file-scoped namespaces, records for DTOs,
   target-typed new, `sealed` by default, `async`/`await` properly,
   `CancellationToken ct` propagated through service methods).
5. Service / handler naming convention: a method returning a Result is
   conventionally named for what it returns (`GetOrderByIdAsync`,
   `CreateOrderAsync`) and its return type is `Task<Result<TResponse>>`
   (or `Task<Result>` for void-equivalent operations).
6. Keep prose between blocks short (1-3 sentences). Reader is a working
   .NET developer; do not over-explain the Result pattern itself —
   patterns-v{FULL_VERSION}.md does that.
7. End each major code block with a brief "Notes:" bullet list if there is
   anything subtle worth flagging (e.g. the difference between
   `Result.Invalid` and `Result.Error`, the implicit conversions from
   `T` to `Result<T>`, deprecated members superseded in this version).

Output ONLY the markdown content, starting with `# Ardalis.Result`.
No preamble, no code fences around the whole document, no closing remarks.
