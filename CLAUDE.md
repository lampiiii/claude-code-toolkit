# Claude Code Toolkit

Custom skills, agents, and commands that extend Claude Code into a PM operating system — optimized for Customer Success Management (CSM) product development.

## Project Structure

```
skills/       → Slash-command automations (zero-questions, full execution)
agents/       → Stateful, multi-turn specialist analysts with persistent memory
commands/     → Quick-trigger actions that execute immediately
```

Each directory has its own `CLAUDE.md` with detailed conventions.

## Conventions

- **Naming**: kebab-case for all directories and files (e.g., `doc-refiner`, `commit-push.md`)
- **Metadata**: YAML frontmatter on all `.md` skill/agent/command files
- **Reference folders**: always lowercase `references/` (never `References/`)
- **Core principle**: Zero questions, full execution — read input, make reasonable assumptions, produce complete output

## Adding New Components

- **Skill**: Create `skills/<skill-name>/SKILL.md` with frontmatter. Add `references/` if needed.
- **Agent**: Create `agents/<agent-name>.md` with frontmatter (include `model`, `color`, `memory` fields).
- **Command**: Create `commands/<command-name>.md` with execution steps.

## Rules

- Do not modify `SKILL.md` files without explicit request
- Reference PDFs in `references/` directories are read-only source material
- Agents store persistent memory in `~/.claude/agent-memory/<agent-name>/`
