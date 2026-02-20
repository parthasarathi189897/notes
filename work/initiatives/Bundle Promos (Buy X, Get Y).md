---
type: initiative
status: active
phase: Execution
health: "🟡 Yellow"
priority: P1
created: 2026-02-20
updated: 2026-02-20
tags:
  - initiative
  - bundle-promos
  - carousels
  - gmv
confluence: https://confluence.walmart.com/pages/viewpage.action?pageId=3349514339
figma:
slack:
jira:
---

# Bundle Promos (Buy X, Get Y)

> [!abstract] Summary
> Enable bundle promotion support (Buy X, Get Y) within homepage carousels to drive incremental GMV through promotional bundling. Currently carousels cannot surface bundle promos, missing $50M incremental annualized GMV opportunity. Q1 carryover initiative under Digital Merchandising Omni Enablement.

> [!multi-column]
>
> > [!info|no-icon] Phase
> > `= this.phase`
>
> > [!info|no-icon] Health
> > `= this.health`
>
> > [!info|no-icon] Priority
> > `= this.priority`
>
> > [!info|no-icon] Updated
> > `= this.updated`

---

## 👥 People

| Role | Name | Team |
|:-----|:-----|:-----|
| 🎯 Lead | Parthasarathi Das | Homepage & Category |
| 📦 Product | Bhavya | Homepage & Category |
| ⚙️ Engineering | Nag, John, Abanoub, Cassie | Homepage & Category |
| ⚙️ Engineering Manager | Karthik Shivkumar | Homepage & Category |

---

## 🗺️ Milestones

| # | Deliverable | Target | Status |
|:--|:------------|:-------|:-------|
| 1 | Bundle promo data contract & carousel integration design | TBD | 🔵 Carryover |
| 2 | Bundle promo support in carousel components | FY 27 Q1 | 🔵 In Progress |
| 3 | A/B test & full rollout | TBD | ⬜ |

> [!example]- Status Legend
> ⬜ Not Started · 🔵 In Progress · ✅ Done · ⏸️ Paused · 🔴 Blocked · 🔄 Carryover · 👀 In Review

---

## 📌 Decisions

| Date | Decision | Context |
|:-----|:---------|:--------|
| 2026-02-17 | All item tiles and PDP promos include bundle link from IPM | Promotions response provides bundle item links |
| 2026-02-17 | Side/bottom sheet UX for bundle item display | Users click bundle link → sheet shows purchasable items for discount |
| 2026-02-17 | API flow: FE → OL Gateway → CLS → CLE → P13n | Architecture for bundle promo data retrieval |

---

## ⚠️ Risks & Blockers

| Risk | Impact | Mitigation |
|:-----|:-------|:-----------|
| Bundle promo data availability/format issues | High | Early alignment with Promotions/Pricing team on data contract |
| Q1 carryover scope creep | Medium | Lock scope to Buy X Get Y only; defer complex bundle types |

---

## 📈 Progress Log

> Latest first — `[[YYYY-MM-DD]]` for full context.

### 2026-02-17
- Technical architecture defined: item tiles and PDP promos include bundle link from IPM
- User flow documented: side/bottom sheet for bundle item display
- API flow established: FE → OL Gateway → CLS → CLE → P13n
- Design reference: Figma PDP FY 26 specs

### 2026-02-13
- Initiative page created from FY 27 roadmap. Q1 carryover under Digital Merchandising Omni Enablement.

---

## 🔗 References

> [!note]- Design, discovery, and deep-dives live externally. Link them here.

| | Link |
|:--|:-----|
| 📄 Confluence | [Initiative – Bundle Promos](https://confluence.walmart.com/pages/viewpage.action?pageId=3349514339) |
| 📐 Figma | PDP FY 26 Design |
| 📋 Jira | TBD |
| 💬 Slack | TBD |
| 🔀 Key PRs | |
| 📊 Metrics | |

---

> [!quote] `Discovery → Design → Execution → Testing → Rollout → Monitoring`
