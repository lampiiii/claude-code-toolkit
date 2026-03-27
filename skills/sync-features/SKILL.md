---
name: sync-features
description: >
  Sync CSM feature documentation from the PM workspace to the company GitHub repo.
  Use when the user says "sync features", "push features to company repo",
  "update company repo", "sync to company GitHub", or any variation involving
  publishing feature docs to the engineering team's repo.
  IMPORTANT: Never ask clarifying questions. Execute the full sync immediately.
---

# Sync Features

Sync the CSM feature documentation from this workspace to the company GitHub repo at `code.devsnc.com`, so the engineering team always has the latest feature docs.

## What It Does

1. Cleans the target repo (preserves `.git` and `README.md`)
2. Copies all feature content from `pm-workspace/products/customer-success-management/releases/features/`
3. Removes `CLAUDE.md` files (Claude Code guidance, not useful for engineers)
4. Removes `.DS_Store` files
5. Commits with a timestamped message
6. Pushes to `origin main`

## Source and Target

- **Source**: `~/Desktop/AI/pm-workspace/products/customer-success-management/releases/features/*`
- **Target**: `~/Desktop/pm-customer-success-management/`
- **Remote**: `https://code.devsnc.com/abhay-tyagi/pm-customer-success-management.git`

## Execution Steps

When invoked, run these commands in sequence:

```bash
# 1. Clean target (keep .git and README.md)
cd ~/Desktop/pm-customer-success-management && find . -mindepth 1 -not -path './.git/*' -not -path './.git' -not -name 'README.md' -delete 2>/dev/null

# 2. Copy features
cp -R ~/Desktop/AI/pm-workspace/products/customer-success-management/releases/features/* ~/Desktop/pm-customer-success-management/

# 3. Remove CLAUDE.md and .DS_Store files
cd ~/Desktop/pm-customer-success-management && find . -name "CLAUDE.md" -delete && find . -name ".DS_Store" -delete

# 4. Stage, commit, push
cd ~/Desktop/pm-customer-success-management && git add -A && git commit -m "Sync: CSM feature docs — $(date +%Y-%m-%d)" && git push origin main
```

## Output

After successful sync, report:
- Number of files synced
- Commit message used
- Confirmation that push succeeded

## Error Handling

- If the target directory doesn't exist, tell the user to clone the repo first:
  `cd ~/Desktop && git clone https://code.devsnc.com/abhay-tyagi/pm-customer-success-management.git`
- If push fails with auth error, suggest the user run `git push origin main` manually in their terminal
- If nothing changed, report "Already up to date — no changes to sync"
