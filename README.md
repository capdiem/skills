# Agent Skills

A collection of Agent Skills for coding agents (pi, Claude Code, Cursor, Codex, and [70+ more](https://github.com/vercel-labs/skills)).

## Skills

| Skill | Description |
|-------|-------------|
| [code-discipline](skills/code-discipline/) | Merged coding discipline from ponytail + karpathy-guidelines. Fixes four common LLM coding pitfalls. |
| [skill-creator](skills/skill-creator/) | Guide for creating effective, well-structured skills. Migrated from Qoder CLI. |

## Install

```bash
npx skills add github.com/yourname/agent-skills -g
```

Or install from local path:

```bash
npx skills add ./skills -g
```

### Options

| Flag | Description |
|------|-------------|
| `-g` | Install globally (`~/.agents/skills/`) |
| `-a <agent>` | Target specific agent (e.g., `pi`, `claude-code`) |
| `-s <name>` | Install specific skill by name |
| `--list` | List available skills without installing |
| `-y` | Skip confirmation prompts |

### Examples

```bash
# Install all skills globally
npx skills add . -g

# Install a single skill
npx skills add . -g --skill code-discipline

# Install to specific agents
npx skills add . -g -a pi -a claude-code

# Non-interactive
npx skills add . -g -y
```

## Usage

After installation, trigger a skill by:

- **Auto**: the agent loads it when the description matches the task.
- **Manual**: `/<skill-name>` command (e.g., `/code-discipline`).

## Structure

```
skills/
  <skill-name>/
    SKILL.md       # Agent instructions (required)
    README.md      # Human documentation (optional)
```

Compatible with the [Agent Skills specification](https://agentskills.io).

## License

MIT
