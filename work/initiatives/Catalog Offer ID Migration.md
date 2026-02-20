---
type: initiative
status: active
phase: Discovery
health: "🟡 Yellow"
priority: P1
created: 2026-02-20
updated: 2026-02-20
tags:
  - initiative
  - catalog
  - omni-5
  - iro-migration
confluence: https://confluence.walmart.com/pages/viewpage.action?pageId=3357967477
figma:
slack:
jira:
---

# Catalog Offer ID Migration

> [!abstract] Summary
> Transition from legacy IRO (Item Relationship Orchestration) attributes to the new Omni 5 catalog system. Multiple offer-level attributes are being deprecated, impacting PDP, PLP, Cart, Checkout, and Search. Target: April 15 launch with zero customer-facing regression. 10 high-impact attributes identified requiring migration.

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
| 🎯 Lead | TBD | CXO / Catalog Platform |
| 📦 Product | TBD - Dedicated PM | CXO |
| ⚙️ Engineering | IRO Team | Catalog Platform |
| 📦 Product (Regulated) | Sourabh | Flowers/Alcohol/Tobacco |
| 📦 Product (Automotive) | Tires PM | Automotive |
| 📦 Product (Warranties) | Gaurav Gupta | Services |
| 🏢 Business | Merchant Team | Merchandising |

---

## 🗺️ Milestones

| # | Deliverable | Target | Status |
|:--|:------------|:-------|:-------|
| 1 | Complete attribute inventory and impact analysis | TBD | 🔵 In Progress |
| 2 | Stakeholder alignment on each attribute decision | TBD | ⬜ |
| 3 | Merchant team approval for supplierItemNumber approach | TBD | ⬜ |
| 4 | IRO confirmation on attribute paths and timelines | TBD | ⬜ |
| 5 | Backend service updates (tem-service, search, cart) | Before Apr 15 | ⬜ |
| 6 | Frontend code cleanup and migration | Before Apr 15 | ⬜ |
| 7 | Testing across all consumer touchpoints | Before Apr 15 | ⬜ |
| 8 | Production deployment and monitoring | Apr 15 | ⬜ |

> [!example]- Status Legend
> ⬜ Not Started · 🔵 In Progress · ✅ Done · ⏸️ Paused · 🔴 Blocked

---

## 📌 Decisions

| Date | Decision | Context |
|:-----|:---------|:--------|
| TBD | Confirm alternative for supplierItemNumber or communicate removal to merchants | PDP functionality impact |
| TBD | Decide on tobacco productType granularity approach | Age verification logic |
| TBD | Define path for member_max_order_quantity in Omni 5 | Walmart+ limits |
| TBD | Warranty alternative solution approach | Free warranty display |

---

## ⚠️ Risks & Blockers

| Risk | Impact | Mitigation |
|:-----|:-------|:-----------|
| No alternative for supplierItemNumber breaks merchant workflows | High | Early merchant team engagement; explore workarounds |
| April 15 deadline too aggressive given discovery needs | Medium | Prioritize critical path attributes; phase non-critical features |
| Multiple PM dependencies cause alignment delays | Medium | Weekly sync; create decision framework; escalate blockers early |
| Regulated item attributes (alcohol/tobacco) break compliance | Critical | Prioritize age verification attributes; comprehensive testing |
| Code cleanup across multiple services introduces regressions | High | Staged rollout; feature flags; integration testing; rollback plan |
| Perishable attribute removal impacts fraud detection | High | Engage Fraud Gateway team early; validate alternative signals |

---

## 📈 Progress Log

> Latest first — `[[YYYY-MM-DD]]` for full context.

### 2026-02-17
- Initiative created based on Sam's Omni 5 migration context
- Identified 10 high-impact attributes requiring migration
- Documented stakeholder map across Product, Engineering, and Merchant teams
- Noted MADR 003 access issues (timeout) — need to resolve

---

## 🔗 References

> [!note]- Design, discovery, and deep-dives live externally. Link them here.

| | Link |
|:--|:-----|
| 📄 Confluence | [Initiative – Catalog Offer ID Migration](https://confluence.walmart.com/pages/viewpage.action?pageId=3357967477) |
| 📄 Reference | Sam's Migration to Omni 5 (IRO attributes removed) |
| 📄 MADR 003 | Sams Migration to Omni 5 (access issues — to be resolved) |
| 📋 Jira | TBD |
| 💬 Slack | TBD |
| 🔀 Key PRs | |
| 📊 Metrics | |

---

> [!quote] `Discovery → Design → Execution → Testing → Rollout → Monitoring`
