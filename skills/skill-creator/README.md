# Skill Creator

Migrated from Qoder CLI's built-in skill. This skill guides the agent through creating effective, well-structured skills for agentic coding tools.

## Origin

Originally part of [Qoder CLI](https://github.com/qoder/cli)'s built-in skill set. Extracted and maintained separately here for cross-platform use (pi, Qoder CLI, Claude Code, etc.).

## What It Does

Walks through the full skill creation lifecycle:

1. Understand the skill with concrete examples
2. Plan reusable resources (scripts, references, assets)
3. Create the skill directory and SKILL.md
4. Edit and validate
5. Install and test

## Key Principles

- **Concise is key** — context window is a public good. Challenge every paragraph's token cost.
- **Progressive disclosure** — metadata always in context, body loads on trigger, resources load on demand.
- **Set appropriate degrees of freedom** — match specificity to task fragility (high/medium/low).

## License

MIT
