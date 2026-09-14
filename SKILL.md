---
name: human-code
description: Use when implementing, modifying, refactoring, or reviewing code for a scoped task, especially when the change may add abstractions, configuration, defensive paths, or unrelated work.
---

# Human Code

Write code for human maintainers. Make the smallest correct change a maintainer can understand quickly—not the most sophisticated solution.

## Scope and Correctness

- Change only what the current task requires. Do not perform unrelated cleanup, refactoring, renaming, formatting, or investigation.
- Smallest correct does **not** mean fewest lines or files. Include relevant callers, tests, validation, compatibility, migration, security, or accessibility work when concrete current evidence shows omitting it would break correctness.
- A stated acceptance criterion or explicit, in-scope review request is a current requirement. Implement the named cases directly; do not build a framework for unnamed cases.
- Treat a caller guarantee as established only when it is enforced at the relevant boundary or demonstrated by an existing invariant. Types, names, and assumptions alone are not enough. Do not treat external input, public APIs, persisted data, or cross-process data as impossible by default.
- Before adding a helper, class, configuration option, fallback, retry, public extension point, or extra state, identify the current requirement or concrete invariant it serves. If none exists, do not add it.
- Investigation needed to establish the affected boundary, existing invariant, or caller contract is in scope; stop once that evidence is sufficient to implement and test the requested behavior.
- If an unrelated issue is worth reporting, mention it separately; do not change it.

## Write Directly

- Prefer explicit control flow, local reasoning, descriptive names, and existing domain terms over cleverness, generic machinery, and invented terminology.
- Prefer a direct `if` to policy objects, wrappers, factories, or strategies for one implementation.
- Small duplication is better than a premature abstraction. A one-use helper, forwarding wrapper, or class without a domain concept needs a clear readability or invariant boundary; otherwise inline it.
- Preserve existing required subsystem contracts and architecture. Reuse local conventions only when they keep the changed behavior understandable; do not copy a legacy pattern merely for consistency.
- Do not bypass or replace an existing abstraction until its relevant contract is understood and concrete evidence shows it is unnecessary for this change.
- Avoid unnecessary indirection, parameter plumbing, redundant state, boolean-flag growth, callbacks, and inheritance.

## Comments and Explanations

Comments explain a non-obvious constraint, invariant, or why a simpler-looking approach is wrong. Do not translate code into English, narrate history, or introduce new terminology.

When explaining complex code: state what it does, the core condition or invariant, and what fails without it before describing implementation details. Start in plain language.

## Finish

After implementing, inspect the diff once: remove accidental helpers, branches, parameters, state, and comments only when readability clearly improves. Verify the relevant behavior, then stop when the requested behavior is complete and no requirement remains. Do not continue polishing, generalizing, or investigating.
