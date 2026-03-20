# Commands

Quick-trigger actions that execute immediately without user input. Each command is a single `.md` file with step-by-step execution instructions.

## Available Commands

| Command | Purpose |
|---------|---------|
| `commit-push` | Commit all changes and push to remote |
| `claude-md-init-all` | Create/update all CLAUDE.md files across a repo |
| `refresh-portfolio` | Refresh portfolio pages with latest content |
| `linkedin-post` | Quick-trigger for the LinkedIn post skill |
| `flip-a-coin` | Flip a coin |
| `open-portfolio` | Open PM Workspace portfolio in browser |
| `open-ironman` | Open Ironman 70.3 Training Tracker |

## Command Structure

Each command is a single `.md` file. No frontmatter required — just clear, imperative execution steps.

```
commands/
├── CLAUDE.md              ← You are here
├── commit-push.md
├── claude-md-init-all.md
├── flip-a-coin.md
├── linkedin-post.md
├── open-ironman.md
├── open-portfolio.md
└── refresh-portfolio.md
```

## Conventions

- Commands execute without asking clarifying questions
- Write step-by-step instructions in imperative voice
- Include error handling (e.g., what to do if `git push` fails)
- Commands that wrap a skill should reference the skill's `SKILL.md` for full rules
- Naming: kebab-case `.md` files
