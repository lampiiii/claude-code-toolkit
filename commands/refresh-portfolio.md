Refresh all portfolio pages with the latest content from the repository. Scan source files for changes and update portfolio HTML pages accordingly.

Execute these steps exactly. Do not ask any clarifying questions.

## Source Files to Scan

These are the source-of-truth files. Read each one to get the latest content:

### Profile & Resume Data
- `pm-workspace/portfolio/resources/Abhay.pdf` — Resume (extract latest job titles, dates, achievements, education, certifications)
- `pm-workspace/portfolio/resources/Profile.pdf` — Profile summary
- `pm-workspace/portfolio/resources/profile-photo.jpg` — Profile photo (check it exists, verify path references)

### Product & Feature Data
- `pm-workspace/products/customer-success-management/releases/features/2026/active/` — Scan all active feature directories for current features, their status, and descriptions
- `pm-workspace/products/customer-success-management/strategy/` — Vision, mission, strategic direction

### Claude Code Setup Data
- `~/.claude/skills/` — List all custom skills (name, description from each SKILL.md)
- `/Users/abhay.tyagi/Desktop/AI/.claude/agents/` — List all custom agents (name, description from each .md file)
- `~/.claude/settings.json` — MCP servers, plugin configurations, AND all lifecycle hooks (count hooks, note their event types and purposes)
- `~/.claude/projects/-Users-abhay-tyagi-Desktop-AI/memory/` — Memory files (MEMORY.md + individual files)
- All `CLAUDE.md` files in the repo — count them, note their scope

### Proof of Value Data
- `pm-workspace/manager-guidance/framework-and-mindset/proof-of-value.md` — Living evidence log organized by 10 Strategic Playbook skill areas. Check which sections have content (Active) vs are empty (Watching).

### Workspace Structure
- Scan `pm-workspace/` directory tree for any new or removed directories

## Pages to Update

### 1. Profile Page (`pm-workspace/portfolio/profile.html`)
Update these sections if source data changed:
- **Header**: Name, title, company, contact links
- **About**: Bio text, metrics (ACV growth, agents built, Plus tier upgrades, enterprise accounts)
- **Experience**: Job titles, companies, dates, achievement bullets — must match resume
- **Products**: Active features list — must match what's in `releases/features/2026/active/`
- **Skills & Certifications**: Skill groups, certification list — must match resume
- **Education**: Degrees, institutions, years — must match resume
- **Achievements**: Achievement cards — must match resume

### 2. Claude Code Showcase (`pm-workspace/portfolio/claude-code.html`)
Update these sections if source data changed:
- **Stats strip**: Count of skills, agents, CLAUDE.md files, lifecycle hooks, MCP integrations, memory files
- **Custom Skills**: List each skill with name, description, tags
- **Custom Agents**: List each agent with name, description, tags
- **MCP Integrations**: List active MCP servers and plugins
- **Lifecycle Hooks**: List each hook with name, event type, description, tags — must match hooks in `settings.json`
- **CLAUDE.md Context System**: Grid of all CLAUDE.md files with paths and descriptions
- **Persistent Memory**: List memory entries and what they track
- **Workspace Structure**: File tree reflecting current directory layout

### 3. Proof of Value Hub (`pm-workspace/portfolio/proof-of-value.html`)
Update these sections based on `proof-of-value.md`:
- **Progress bar**: Count how many of the 10 skill areas have content (not "No entries yet") — update the "X / 10 active" label and the progress bar fill width percentage
- **Skill cards**: For each of the 10 categories, check if `proof-of-value.md` has real content under that section:
  - If content exists → card should be `card--active` with accent bar, "Active" status, and item count
  - If no content → card should be `card--watching` with "Watching" status and lock icon
- **Item counts**: Count the number of proof entries (table rows, bullet points, paragraphs) in each active section

### 4. Homepage (`pm-workspace/portfolio/pm-workspace-home.html`)
- **Hero text**: Verify title, subtitle, and role label are current
- **Nav links**: Verify all links work and point to correct routes

## Rules
- Only modify content that actually changed — do not rewrite unchanged sections
- Preserve all HTML structure, CSS, and design — only update text content and data
- If a new feature was added to `releases/features/2026/active/`, add a new product card
- If a feature was moved to shipped or removed, remove its product card
- If new skills or agents were added, add them to the Claude Code page
- If CLAUDE.md files were added or removed, update the count and grid
- After making changes, list what was updated in a summary table

## Output
Report a table with:
| Page | Section | Change | Details |
|------|---------|--------|---------|

If nothing changed, report "All portfolio pages are up to date."