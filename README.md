# Human Code

> A Codex skill for small, readable, scope-controlled code changes.

Human Code helps coding agents make the smallest correct change that a human
maintainer can understand quickly.

It favors direct control flow, existing domain language, local reasoning, and
concrete evidence over speculative abstractions, configuration, and defensive
machinery.

## What it guards against

- Scope creep and unrelated cleanup
- Premature abstractions and one-use wrappers
- Generic “future-proofing”
- Unclear names, hidden behavior, and invented terminology
- Defensive code without a concrete failure mode
- Continued polishing after the requested work is complete

## Use with

- `stop-that-shit` for task boundaries and stopping conditions
- `human-code` for implementation clarity and maintainability

## Installation

Copy this repository into your Codex skills directory:

```text
~/.codex/skills/human-code/
