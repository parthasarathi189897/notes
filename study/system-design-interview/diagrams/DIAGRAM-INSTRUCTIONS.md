# Draw.io Diagram Instructions

Instructions for creating system design diagrams. For human or LLM use.

---

## File Setup

1. Create `.drawio` file under `diagrams/`
2. Name: `kebab-case-topic.drawio`
3. Canvas: `pageWidth=1400 pageHeight=900` (adjust height as needed)
4. Link from topic note: `[[filename.drawio]]`

---

## Layout Structure

```
+------------------+-----+--------------------+
|  Section A       | VS  |  Section B         |
|  (container bg)  |     |  (container bg)    |
|                  |     |                    |
|  [Diagram]       |     |  [Diagram]         |
|                  |     |                    |
|  Pros | Cons     |     |  Pros | Cons       |
|  Best for: ...   |     |  Best for: ...     |
+------------------+-----+--------------------+
|  Key Insight / Summary                       |
+----------------------------------------------+
```

### Steps

1. **Title**: Top center, 26px bold, `fontColor=#1A1A1A`
2. **Section containers**: Rounded rectangles as backgrounds
   - Use different light fills per section (see Color Palette)
   - `strokeWidth=2`, `arcSize=8`
3. **Divider** (if comparing): Dashed vertical line with label
   - `strokeWidth=3`, `strokeColor=#90A4AE`, `dashPattern=8 8`
4. **Diagram elements**: Inside each container
5. **Pros/Cons boxes**: Side by side at bottom of each section
6. **"Best for" bar**: Yellow highlight below pros/cons
7. **Summary bar**: Full-width at bottom with key insight

---

## Color Palette (ADA Compliant)

All combinations below pass **WCAG AA 4.5:1** contrast ratio.

### Section Backgrounds

| Purpose          | Fill      | Stroke    |
|------------------|-----------|-----------|
| Section A (cool) | `#F0F4FA` | `#B0BEC5` |
| Section B (warm) | `#FFF8E1` | `#F9A825` |
| Summary bar      | `#E3F2FD` | `#1565C0` |

### Component Colors

| Element        | Fill      | Stroke    | Font      |
|----------------|-----------|-----------|-----------|
| Server/compute | `#1565C0` | `#0D47A1` | `#FFFFFF` |
| Load balancer  | `#E65100` | `#BF360C` | `#FFFFFF` |
| Database       | `#2E7D32` | `#1B5E20` | `#FFFFFF` |
| Cache          | `#6A1B9A` | `#4A148C` | `#FFFFFF` |
| Queue/message  | `#00838F` | `#006064` | `#FFFFFF` |
| User/client    | `#E8EAF6` | `#5C6BC0` | `#1A237E` |

### Pros/Cons

| Type | Box Fill  | Box Stroke | Text Color |
|------|-----------|------------|------------|
| Pros | `#E8F5E9` | `#2E7D32`  | `#1B5E20`  |
| Cons | `#FFEBEE` | `#C62828`  | `#B71C1C`  |

### Highlights

| Purpose   | Fill      | Stroke    | Text      |
|-----------|-----------|-----------|-----------|
| Takeaway  | `#FFF9C4` | `#F9A825` | `#37474F` |
| Warning   | `#FFF3E0` | `#E65100` | `#BF360C` |

### Arrows & Text

| Element      | Color     |
|--------------|-----------|
| Flow arrows  | `#5C6BC0` |
| Action arrows| `#4527A0` |
| Body text    | `#37474F` |
| Titles       | `#1A1A1A` |

---

## Font Sizes

| Element           | Size  | Style |
|-------------------|-------|-------|
| Main title        | 26px  | bold  |
| Section title     | 18px  | bold  |
| Component labels  | 13-14px | bold |
| Pros/cons items   | 13px  | normal|
| Arrows/labels     | 12px  | normal|
| Takeaway text     | 12px  | bold key phrase |
| Summary           | 14px  | bold key phrase |

---

## Element Styles (Copy-Paste)

### Container
```
rounded=1;whiteSpace=wrap;html=1;fillColor=#F0F4FA;strokeColor=#B0BEC5;strokeWidth=2;arcSize=8;
```

### Server
```
rounded=1;whiteSpace=wrap;html=1;fillColor=#1565C0;fontColor=#FFFFFF;fontSize=13;strokeColor=#0D47A1;strokeWidth=2;
```

### Load Balancer
```
rounded=1;whiteSpace=wrap;html=1;fillColor=#E65100;fontColor=#FFFFFF;fontSize=13;strokeColor=#BF360C;strokeWidth=2;
```

### Pros Box
```
rounded=1;whiteSpace=wrap;html=1;fillColor=#E8F5E9;strokeColor=#2E7D32;strokeWidth=1;arcSize=10;
```

### Cons Box
```
rounded=1;whiteSpace=wrap;html=1;fillColor=#FFEBEE;strokeColor=#C62828;strokeWidth=1;arcSize=10;
```

### Arrow
```
endArrow=block;endFill=1;strokeColor=#5C6BC0;strokeWidth=2;
```

### Callout (warning/info)
```
shape=callout;whiteSpace=wrap;html=1;perimeter=calloutPerimeter;size=15;position=0.5;position2=1;base=10;fillColor=#FFF3E0;strokeColor=#E65100;fontColor=#BF360C;fontSize=12;rounded=1;
```

---

## Checklist

- [ ] Title centered at top
- [ ] Section containers with distinct background colors
- [ ] User/client icon showing traffic origin
- [ ] Components labeled with specs (CPU, RAM, etc.)
- [ ] Arrows labeled where meaning isn't obvious
- [ ] Callouts for key concepts (SPOF, fault tolerance)
- [ ] Pros/cons in colored boxes (green/red)
- [ ] "Best for" takeaway per section
- [ ] Summary insight at bottom
- [ ] All text passes WCAG AA contrast (4.5:1 minimum)
- [ ] Font sizes >= 12px
- [ ] File linked from topic note with `[[filename.drawio]]`
