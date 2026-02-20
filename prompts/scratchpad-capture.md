---
description: Quick-captures an idea, ad-hoc task, or team contribution
trigger: "new idea" or "jot this down" or "new scratchpad [topic]"
tools: vault (read/write)
template: templates/scratchpad.md
output: work/scratchpad/<slug>.md
vault_path: /Users/p0d00wj/notes
---

# Scratchpad Capture

## Steps

1. **Ask the user** (2-3 questions max):
   - "What's the topic?" (becomes file name)
   - "Quick context — what triggered this?"
   - "Any immediate next steps?"

2. **Determine category** from context:
   - `idea` | `team-contribution` | `investigation` | `tooling` | `other`

3. **Check for related notes** in `work/initiatives/` and `work/scratchpad/`. Suggest links if found.

4. **Read template** from `templates/scratchpad.md`. Fill in:
   - File name as kebab-case slug (e.g., `api-caching-idea.md`)
   - `category:` and `initiative:` in frontmatter
   - What Is This, Context, Tasks sections from user input
   - Related wikilinks in footer

5. **Save** to `work/scratchpad/<slug>.md`

## Confirm
```
Scratchpad created: work/scratchpad/<slug>.md
  Category: <category> | Related: [links]
```
