---
type: reference
created: 2026-02-20
tags:
  - reference
---

# Markdown Cheatsheet

> The 20% of syntax that covers 80% of daily note-writing.

## Hotkeys (Mac)

| Action | Shortcut |
|--------|----------|
| **Bold** | `Cmd + B` |
| *Italic* | `Cmd + I` |
| New note | `Cmd + N` |
| Quick switcher (find any note) | `Cmd + O` |
| Command palette | `Cmd + P` |
| Search vault | `Cmd + Shift + F` |
| Toggle checkbox | `Cmd + Enter` |
| Insert link | `Cmd + K` |
| Toggle edit/preview | `Cmd + E` |
| Close current note | `Cmd + W` |
| Open settings | `Cmd + ,` |
| Indent line | `Tab` |
| Outdent line | `Shift + Tab` |
| Move line up/down | `Alt + ↑/↓` |

## Text Formatting

```
**bold text**
*italic text*
~~strikethrough~~
==highlighted text==
`inline code`
> blockquote
```

## Headings

```
# Heading 1
## Heading 2
### Heading 3
```

Use `##` for main sections, `###` for sub-sections. That's enough — rarely need deeper.

## Lists

```
- Bullet point
  - Nested (indent with 2 spaces)

1. Numbered item
2. Another item

- [ ] Unchecked task
- [x] Completed task
```

## Links

```
[[Note Name]]              → Link to another note in vault
[[Note Name|Display Text]] → Link with custom text
[[Note Name#Heading]]      → Link to specific heading
[External text](https://url) → Web link
```

**Tip**: Just type `[[` and start typing — Obsidian autocompletes note names.

## Tags

```
#tag-name
#win           → Used in daily notes for performance rollup
#concept       → Used in study notes
```

Tags are searchable and used by Dataview for auto-aggregation.

## Tables

```
| Column 1 | Column 2 | Column 3 |
|----------|----------|----------|
| cell     | cell     | cell     |
```

**Tip**: The Table Editor plugin auto-formats tables. Just type `|` and Tab through cells.

## Code

````
Inline: `code here`

Block:
```javascript
const x = 1;
```
````

## Callouts

```
> [!note] Title
> Content here

> [!warning] Watch out
> Important information
```

Types: `note`, `tip`, `warning`, `important`, `info`, `example`

## Frontmatter

The `---` block at the top of every note. Used for metadata and Dataview queries.

```yaml
---
type: daily-note
date: 2026-02-20
tags:
  - daily
---
```

**Rule**: Don't edit frontmatter manually unless you know what you're changing. The templates and skills handle it.

## Embeds

```
![[Note Name]]             → Embed entire note
![[Note Name#Heading]]     → Embed specific section
![[image.png]]             → Embed image from attachments/
```

## Horizontal Rule

```
---
```

Three dashes on their own line. Used to separate sections (like footer nav in daily notes).
