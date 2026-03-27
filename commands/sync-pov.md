Sync the Proof of Value page from this repo to the portfolio repo.

## Steps

1. Read the source of truth: `pm-workspace/velyo/proof-of-value.md`
2. Read the current portfolio HTML: `/Users/abhay.tyagi/Desktop/portfolio/pages/proof-of-value.html`
3. Update the portfolio HTML to reflect any changes from the source file:
   - Update item counts on each category card (count evidence log entries per category)
   - If a "Watching" category now has evidence entries, consider flagging it for promotion to "Active"
   - Update the detail pages in `/Users/abhay.tyagi/Desktop/portfolio/pages/pov/` with new evidence entries if applicable
4. Commit the changes in the portfolio repo with message: "Sync proof-of-value from pm-workspace"
5. Confirm to the user what was updated

## Important
- The source of truth is ALWAYS `pm-workspace/velyo/proof-of-value.md` in this repo
- The portfolio repo is at `/Users/abhay.tyagi/Desktop/portfolio/`
- Do NOT modify the source file — only read it and push changes to the portfolio repo
- Update item counts by counting rows in the Evidence Log table that match each category
