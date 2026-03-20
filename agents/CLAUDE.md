# Agents

Stateful, multi-turn specialist analysts invoked via the `/task` command. Each agent has persistent memory that accumulates knowledge across conversations.

## Available Agents

| Agent | Slash Command | Purpose |
|-------|--------------|---------|
| `competitive-strategic-lens` | `/task competitive-strategic-lens` | Competitive intelligence analysis for CSM product decisions |
| `prd-edge-case-analyzer` | `/task prd-edge-case-analyzer` | Review PRDs for edge cases, risks, and gaps before engineering handoff |

## Agent Structure

Each agent is a single `.md` file with YAML frontmatter:

```yaml
---
name: agent-name
description: "Trigger conditions and usage examples"
model: opus
color: blue
memory: user
---
```

**Required frontmatter fields:**
- `name` — kebab-case identifier
- `description` — when to trigger, with concrete examples
- `model` — Claude model to use (`opus`, `sonnet`, `haiku`)
- `color` — visual indicator in Claude Code UI
- `memory` — memory scope (`user` for persistent cross-conversation memory)

## Conventions

- Agents produce structured, multi-section analyses with clear visual hierarchy
- Each agent stores persistent memory in `~/.claude/agent-memory/<agent-name>/`
- Memory files use `MEMORY.md` (~200 line max) plus separate topic files
- Agents should be brutally honest — no sugarcoating — with actionable recommendations
- Always provide concrete examples and cite specific evidence over vague statements
