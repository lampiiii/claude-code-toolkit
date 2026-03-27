# Claude Code Toolkit

A collection of custom **skills**, **agents**, and **commands** for [Claude Code](https://docs.anthropic.com/en/docs/claude-code) — turning it into a full-fledged PM operating system for product managers, especially those working in Customer Success Management (CSM).

## The Problem

Product managers repeat the same workflows daily — writing epics, drafting stories, prepping meetings, sending team updates, analyzing competitors, reviewing PRDs. Each one follows a predictable structure, but doing it from scratch every time burns time and mental energy.

## What This Toolkit Does

This toolkit packages those repeatable PM workflows into reusable Claude Code components:

- **Skills** — slash-command automations that take rough input and produce polished, structured output in one shot. No clarifying questions, no back-and-forth. You type `/epic-creator`, paste your context, and get a complete epic with acceptance criteria.
- **Agents** — multi-turn specialists with persistent memory. They accumulate domain knowledge across conversations and deliver deep strategic analysis (competitive intelligence, PRD risk review).
- **Commands** — quick-trigger utilities for common actions like committing code, initializing project docs, or opening dashboards.

Everything follows a **zero-questions, full-execution** philosophy: read the input, make reasonable assumptions, produce complete output. The user refines afterward — not before.

## Skills

Single-shot workflow automations invoked as slash commands.

| Skill | Command | What It Does |
|-------|---------|--------------|
| **epic-creator** | `/epic-creator` | Creates structured product epics with Subject, Description, and detailed Acceptance Criteria (10 subsections including personas, functional details, telemetry, and customer outcomes) |
| **story-creator** | `/story-creator` | Creates user stories with Short Description, Description, and Acceptance Criteria (General AC + User Interaction narrative) |
| **doc-refiner** | `/doc-refiner` | Refines and restructures messy markdown — adds TL;DR, logical headings, deduplication, grammar fixes while preserving the author's voice |
| **meeting-prep** | `/meeting-prep` | Generates a concise meeting subject line and a prioritized agenda table from free-form input |
| **linkedin-post** | `/linkedin-post` | Drafts LinkedIn posts in a specific authentic voice with a proven 5-part structure (hook, problem, solution, impact, closing) |
| **team-message** | `/team-message` | Converts rough, unstructured thoughts into clear, professional messages ready to paste into Teams or Slack |
| **sync-features** | `/sync-features` | Syncs CSM feature docs from workspace to company GitHub repo for engineering team |

## Agents

Stateful specialists with persistent memory, invoked via `/task`.

| Agent | What It Does |
|-------|--------------|
| **competitive-strategic-lens** | Full competitive intelligence analysis — feature comparison across 15+ competitors (Gainsight, Totango, Salesforce, etc.), differentiation scoring, moat assessment, AI disruption threat analysis, and a strategic build/don't-build verdict |
| **prd-edge-case-analyzer** | Reviews PRDs across 10 dimensions (user edge cases, data/input boundaries, state/flow issues, security risks, performance, business logic, error handling, operational risks, and more) with CSM-specific scenario coverage |
| **persona-drip** | Generates daily B2B persona immersion scenarios — vivid, realistic slices of a CSM's workday with play-by-play, invisible friction points, and PM takeaways. Rotates across 6 categories and 4 segments. |

Agents remember insights across conversations. The competitive lens accumulates market intelligence; the PRD analyzer learns recurring risk patterns in your product area.

## Commands

Immediate-execution utilities.

| Command | What It Does |
|---------|--------------|
| **commit-push** | Stages, commits, and pushes all changes — auto-generates commit message, excludes secrets |
| **claude-md-init-all** | Creates or updates `CLAUDE.md` context files across an entire repository |
| **refresh-portfolio** | Refreshes portfolio HTML pages with latest content from source files |
| **linkedin-post** | Quick-trigger wrapper for the LinkedIn post skill |
| **open-velyo** | Opens the Velyo PM Workspace in browser (starts server if needed) |
| **open-ironman** | Opens the Ironman 70.3 Training Tracker app |
| **sync-pov** | Syncs the proof of value page to the portfolio repo |
| **update-activity-log** | Updates the Claude Code activity log with session entries |
| **flip-a-coin** | Flips a coin. Sometimes you just need one. |

## Project Structure

```
claude-code-toolkit/
├── CLAUDE.md                          # Root context — conventions, naming rules
├── README.md
├── skills/                            # Slash-command automations
│   ├── CLAUDE.md                      # Skills system documentation
│   ├── doc-refiner/
│   │   └── SKILL.md
│   ├── epic-creator/
│   │   ├── SKILL.md
│   │   └── references/                # Domain reference PDFs
│   ├── story-creator/
│   │   ├── SKILL.md
│   │   └── references/
│   ├── meeting-prep/
│   │   └── SKILL.md
│   ├── linkedin-post/
│   │   └── SKILL.md
│   ├── team-message/
│   │   └── SKILL.md
│   └── sync-features/
│       └── SKILL.md
├── agents/                            # Multi-turn specialists with memory
│   ├── CLAUDE.md                      # Agents system documentation
│   ├── competitive-strategic-lens.md
│   ├── prd-edge-case-analyzer.md
│   └── persona-drip.md
└── commands/                          # Quick-trigger actions
    ├── CLAUDE.md                      # Commands system documentation
    ├── commit-push.md
    ├── claude-md-init-all.md
    ├── refresh-portfolio.md
    ├── linkedin-post.md
    ├── open-velyo.md
    ├── open-ironman.md
    ├── sync-pov.md
    ├── update-activity-log.md
    └── flip-a-coin.md
```

## Getting Started

### Prerequisites

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) installed and configured

### Installation

1. **Clone the repo**
   ```bash
   git clone https://github.com/lampiiii/claude-code-toolkit.git
   ```

2. **Copy components to your Claude Code config**
   ```bash
   # Skills — copy to your project or global config
   cp -r skills/* ~/.claude/skills/

   # Agents
   cp agents/*.md ~/.claude/agents/

   # Commands
   cp commands/*.md ~/.claude/commands/
   ```

3. **Start using them**
   ```
   /epic-creator Build a health score dashboard that shows CSM portfolio risk at a glance
   /meeting-prep Discuss API delay with eng, QA timeline, release readiness
   /team-message Hey need to tell Raj about the renewal forecast bug and ask about the timeline
   ```

## Design Principles

| Principle | What It Means |
|-----------|---------------|
| **Zero questions** | Skills never ask clarifying questions. They assume, draft, and let you refine. |
| **Full execution** | Every invocation produces complete, usable output — not outlines or placeholders. |
| **Domain-native** | Optimized for CSM product development — personas, workflows, and terminology are baked in. |
| **Persistent intelligence** | Agents accumulate knowledge across conversations via persistent memory. |
| **Convention over configuration** | Consistent structure (kebab-case naming, YAML frontmatter, `SKILL.md` per skill) makes extending the toolkit predictable. |

## Creating Your Own

### New Skill
```bash
mkdir skills/your-skill-name
```
Create `skills/your-skill-name/SKILL.md` with YAML frontmatter (`name`, `description`) and execution rules. Add a `references/` folder if the skill needs domain context.

### New Agent
Create `agents/your-agent-name.md` with YAML frontmatter (`name`, `description`, `model`, `color`, `memory`) and the agent's full system prompt.

### New Command
Create `commands/your-command-name.md` with step-by-step execution instructions.

## License

MIT
