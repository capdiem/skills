# Code Discipline

> Prescription for the four common LLM coding pitfalls.

## What

**code-discipline** merges two philosophies:

- **[ponytail](https://github.com/DietrichGebert/ponytail)** — lazy senior dev. YAGNI, stdlib first, shortest path.
- **[karpathy-guidelines](https://github.com/multica-ai/andrej-karpathy-skills)** — Andrej Karpathy's behavioral guardrails for LLM coding. Surface assumptions, surgical changes, verifiable goals.

They complement each other. ponytail is good at "write the minimum," karpathy is good at "think before you write." Combined, they cover the full chain from thought to delivery.

## Why

LLMs have four recurring coding pitfalls. Each upstream skill covers only part of them:

| Pitfall | ponytail | karpathy | code-discipline |
|---------|----------|----------|-----------------|
| 1. Guessing intent, writing wrong thing | Ship first, question after | Stop, surface assumptions, ask | **karpathy wins** |
| 2. Over-engineering, speculative code | 6-rung ladder, strongest | One-liner principle | **ponytail wins** |
| 3. Touching unrelated code | One sentence | Detailed rules | **both** |
| 4. Skipping verification | Leave one assert | Break into verifiable steps | **both** |

A single skill leaves gaps. ponytail doesn't prevent wrong-direction guesses. karpathy has no concrete decision framework. Together they cover all four.

## How

### Install

As a pi package:

```bash
pi install /path/to/code-discipline
```

Or add to `settings.json`:

```json
{
  "packages": ["/path/to/code-discipline"]
}
```

### Trigger

- **Auto**: the skill loads when the agent matches its description (writing, reviewing, or refactoring code).
- **Manual**: `/code-discipline` command.

### Rules (fixed, no levels)

1. **Don't Rush** — ambiguous? Stop, state assumptions, ask before coding.
2. **Don't Over-Engineer** — follow the ladder: YAGNI -> stdlib -> native -> existing dep -> one line -> minimum.
3. **Don't Touch Unrelated** — touch only what you must. No adjacent code/formatting/style changes.
4. **Don't Skip Verification** — break tasks into verifiable steps. Non-trivial logic leaves one assert.

Mark intentional shortcuts with a `ponytail:` comment:

```python
# ponytail: global lock, per-account locks if throughput matters
```

## Relationship with Upstream

- **ponytail**: took the ladder, `ponytail:` comments, output format, boundaries. Removed levels. Changed ambiguity handling from "ship first, question after" to "stop and ask."
- **karpathy-guidelines**: took all four principles. Fills the gaps ponytail leaves in communication and verification.

No auto-sync with upstream — cherry-pick changes manually when they matter.

## License

MIT
