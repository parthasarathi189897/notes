---
description: Creates or updates a Zettelkasten concept note from a study session
trigger: "I learned about [topic]" or "new concept [topic]"
tools: vault (read/write)
template: templates/study-concept.md
output: study/concepts/<Concept Name>.md
vault_path: /Users/p0d00wj/notes
---

# Study Session Capture

## Principles
- **Atomic** — One concept per note. If user describes multiple, create separate notes.
- **Linked** — Every note links to at least one other note.
- **Own words** — User's explanation, not copy-pasted definitions.

## Steps

1. **Identify concept** — Check if note exists in `study/concepts/`. Existing → update. New → create.

2. **Ask the user** (conversational, accept whatever detail they give):
   - "Explain it in one sentence?"
   - "How does it work?"
   - "Why does it matter / when would you use it?"
   - "Any examples, trade-offs, or sources?"

3. **Find related concepts** — Search `study/concepts/` and `study/MOCs/` for keyword matches. Suggest links.

4. **Create or update note**:
   - **New**: Read `templates/study-concept.md`. Fill sections from user input. Set `domain:`, `tags:`, `aliases:` in frontmatter. Save to `study/concepts/<Concept Name>.md`.
   - **Existing**: Append/refine sections. Add new related links. Set `updated:` to today.

5. **Update MOC** — Find matching MOC in `study/MOCs/`. Add `[[Concept]]` link. If no MOC fits, ask: "Create a new MOC for [domain]?"

6. **Save** all changed files.

## Confirm
```
Concept captured: study/concepts/<name>.md
  Domain: <domain> | Related: X linked | MOC: <domain>.md
```
