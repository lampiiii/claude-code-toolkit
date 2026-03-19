# Skills

Shared PM workflow automations. Each skill is a self-contained module invoked as a slash command in Claude Code.

## Available Skills

| Skill | Slash Command | Purpose |
|-------|--------------|---------|
| `doc-refiner` | `/doc-refiner` | Refine, restructure, and polish unstructured markdown documents |
| `epic-creator` | `/epic-creator` | Create structured product epics (Subject, Description, Acceptance Criteria) |
| `story-creator` | `/story-creator` | Create structured user stories (Short Description, Description, Acceptance Criteria) |
| `meeting-prep` | `/meeting-prep` | Generate meeting subject line and structured, prioritized agenda |
| `linkedin-post` | `/linkedin-post` | Write high-engagement LinkedIn posts in Abhay's authentic voice and proven format |
| `team-message` | `/team-message` | Convert rough thoughts into clear, professional team messages for Teams/Slack/email |

## Skill Structure

Each skill directory contains:
- `SKILL.md` -- Defines the skill's purpose, trigger phrases, input/output format, and execution rules
- `.skill` file (optional) -- Packaged skill archive
- `References/` or `references/` (optional) -- Reference PDFs or examples used by the skill

## Core Design Principles

All skills follow these shared principles:
1. **Zero questions, full execution** -- Never ask clarifying questions. Read input, produce complete output immediately.
2. **Assume and draft** -- Make reasonable assumptions based on the CSM domain. User refines afterward.
3. **Speed over perfection** -- First draft momentum matters more than getting it perfect.
4. **Domain: CSM** -- Skills are optimized for Customer Success Management product development context.

## Rules
- Do not modify SKILL.md files without explicit request
- Reference PDFs in `References/` directories are read-only source material
- When creating a new skill, follow the same structure: create a subfolder with a `SKILL.md` at minimum
