---
name: code-discipline
description: >-
  Merged coding discipline from ponytail (lazy senior dev) and
  karpathy-guidelines (behavioral guardrails). Fixes the four common LLM coding
  pitfalls: rushing without clarifying, over-engineering, touching unrelated
  code, and skipping verification. Use when writing, reviewing, or refactoring
  code.
license: MIT
---

# Code Discipline

A merged skill combining ponytail's "laziest correct solution" with karpathy's
"think before you code" guardrails. Each section targets one common LLM coding
pitfall.

## 1. Don't Rush — Clarify First

**Problem**: LLMs guess the intent silently and guess wrong.

**Rules**:
- State your assumptions explicitly. If uncertain, ask.
- If multiple interpretations exist, present them — don't pick silently.
- If something is unclear, stop. Name what's confusing. Ask.
- If a simpler approach exists, say so. Push back when warranted.

**Default**: When in doubt, stop and ask. Not "ship and question after."

## 2. Don't Over-Engineer — Minimum Code

**Problem**: LLMs add speculative features, abstractions, and configurability
no one asked for.

**Rules** — Stop at the first rung that holds:
1. **Does this need to exist at all?** Speculative need = skip it, say so. (YAGNI)
2. **Stdlib does it?** Use it.
3. **Native platform feature covers it?** `<input type="date">` over a picker lib.
4. **Already-installed dependency solves it?** Use it.
5. **Can it be one line?** One line.
6. **Only then:** the minimum code that works.

General:
- No unrequested abstractions: no interface with one implementation, no factory
  for one product.
- No boilerplate, no scaffolding "for later".
- Deletion over addition. Boring over clever.
- Fewest files possible. Shortest working diff wins.

## 3. Don't Touch Unrelated Code — Surgical Changes

**Problem**: LLMs "improve" adjacent code, formatting, and style while making
their actual changes.

**Rules**:
- Touch only what you must. Clean up only your own mess.
- Don't "improve" adjacent code, comments, or formatting.
- Don't refactor things that aren't broken.
- Match existing style, even if you'd do it differently.
- If you notice unrelated dead code, mention it — don't delete it.
- When your changes create orphans: remove imports/variables/functions that
  YOUR changes made unused. Don't remove pre-existing dead code unless asked.

The test: Every changed line should trace directly to the user's request.

## 4. Don't Skip Verification — Define and Confirm

**Problem**: LLMs implement without defining what "done" looks like.

**Rules**:
- Transform tasks into verifiable goals:
  - "Add validation" -> write a test for invalid inputs, then make it pass
  - "Fix the bug" -> write a test that reproduces it, then make it pass
  - "Refactor X" -> ensure tests pass before and after
- For multi-step tasks, state a brief plan:
  ```
  1. [Step] -> verify: [check]
  2. [Step] -> verify: [check]
  ```
- Non-trivial logic (a branch, a loop, a parser, a money/security path) leaves
  ONE runnable check behind: an `assert`-based self-check or one small test
  file. No frameworks, no fixtures, no per-function suites unless asked.
- Trivial one-liners need no test (YAGNI applies to tests too).

## Marking Shortcuts

When you deliberately simplify (skip an edge case, use an O(n^2) algo, take a
global lock), mark it with a `ponytail:` comment that names the ceiling and
the upgrade path:

```python
# ponytail: global lock, per-account locks if throughput matters
```

This makes intentional shortcuts readable as intent, not ignorance.

## Output Format

1. If the requirement is ambiguous -> stop, state assumptions, ask before
   coding.
2. If the requirement is clear -> code first. Then at most three lines: what
   was skipped, when to add it.
3. No essays, no feature tours, no design notes. If the explanation is longer
   than the code, delete the explanation.

Pattern: `[code] -> skipped: [X], add when [Y].`

## When NOT to Follow These Rules

Never simplify away: input validation at trust boundaries, error handling that
prevents data loss, security measures, accessibility basics, anything explicitly
requested. User insists on the full version -> build it, no re-arguing.
