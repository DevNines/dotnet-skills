You are an expert .NET architect writing the `patterns-v{FULL_VERSION}.md`
reference for the Ardalis.Specification skill, where FULL_VERSION is the
MAJOR.MINOR.PATCH given in the user message. This file is loaded for every
question to the skill WHEN the user's project resolves to this version.
Rules and code in this file must therefore be valid for THIS version — not
"stable across all majors", not "the latest version", but THIS specific
version as defined by the API SURFACE.

Generate a markdown file that covers:

1. What the Specification pattern is for, in 2-3 paragraphs. State the
   problem it solves and where it does NOT belong (single-row primary-key
   lookups, mutations, cross-aggregate transactions).
2. Naming conventions: file-per-spec, class name shape
   (`<Entity><Filter>Spec`), `Spec` suffix not `Specification`, ctor
   parameters become spec parameters.
3. A "where does each piece of code belong" table covering: filtering /
   ordering / includes / paging / projection (inside the spec); authorization
   (NOT in the spec); validation of constructor inputs; caching tags;
   AsNoTracking / split queries; DbContext-specific config (NOT in the spec).
4. The canonical constructor shape with explanation of: `sealed`, positional
   required args, no nullable optional-filter params, Query.… chain order
   (filter → sort → page → include → project). All identifiers used MUST be
   in the surface.
5. Repository wiring: use `IRepositoryBase<T>` / `IReadRepositoryBase<T>`
   directly; do not wrap in your own `IGenericRepository`. Show the
   open-generic DI registration. Verify the interface names against the surface.
6. Testing specs against in-memory data.
     — If the surface has a concrete `InMemorySpecificationEvaluator`, use it.
     — Otherwise, recommend evaluating the spec's predicates against an
       `IEnumerable<T>` manually, and show a short example.
     — Do not invent an evaluator type that the surface doesn't list.
7. A "things to avoid" section that names specific anti-patterns:
   IQueryable-returning methods on the spec; subclassing Specification to
   add soft-delete / tenant filters (use EF query filters instead); injecting
   IServiceProvider / DbContext into a spec; dynamic spec generation at
   runtime.

Use idiomatic modern C#. Keep the file under ~250 lines.

Output ONLY the markdown content, starting with `# Ardalis.Specification v{FULL_VERSION} — patterns`.
No preamble, no code fences around the whole document, no closing remarks.
