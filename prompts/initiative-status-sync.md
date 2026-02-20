---
description: Syncs initiative progress from Obsidian note to its Confluence page
trigger: "sync initiative to confluence" or "push [name] to confluence"
tools: vault (read), mcp-confluence (read/write)
output: Updates Confluence page in-place
vault_path: /Users/p0d00wj/notes
---

# Initiative Status Sync

## Steps

1. **Find the initiative** in `work/initiatives/`. If ambiguous, list and ask.

2. **Get Confluence URL** from frontmatter `confluence:` field. If missing, ask the user and save it back to frontmatter.

3. **Fetch the Confluence page** using MCP:
   ```
   mcp__mcp-confluence__get_confluence_page
     page_url: <confluence_url>
     consent: "yes"
   ```

4. **Compare local vs Confluence** — Identify new/changed:
   - Progress Log entries
   - Decision Log entries
   - Phase / Health
   - Milestones status
   - Risks

5. **Preview changes** and ask: "Push these to Confluence?"

6. **Update Confluence** via MCP. Convert markdown to Confluence storage format:
   - `**bold**` → `<strong>`
   - `[[wikilinks]]` → plain text
   - Tables → HTML `<table>`
   - Lists → `<ul>/<li>`

7. **Update frontmatter**: set `updated:` and `last_synced:` to today.

## Confirm
```
Synced: <name> → Confluence
  URL: <confluence_url>
  Progress: X new | Decisions: X new
```
