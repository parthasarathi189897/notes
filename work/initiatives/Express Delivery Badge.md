---
type: initiative
status: active
phase: Execution
health: "🟢 Green"
priority: P1
created: 2026-02-18
updated: 2026-02-19
tags:
  - initiative
  - express-delivery
  - item-service
confluence: https://confluence.walmart.com/pages/viewpage.action?pageId=3360265578
figma:
slack: https://app.slack.com/client/E30MTJF0C/C09S08ATZME
jira:
---

# Express Delivery Badge

> [!abstract] Summary
> Centralize Express Delivery badge logic in item-service for Sam's Club. IRO provides `fulfillmentSummary` → item-service determines badge eligibility → consistent badge display across PLP and all prefetch surfaces (SWAG, etc.).

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
| 🎯 Lead | TBD | Sam's Vivaldi |
| 📦 Product | TBD | Sam's E-commerce |
| ⚙️ Engineering | Sams Vivaldi Team | Item Service / Vivaldi |

---

## 🗺️ Milestones

| # | Deliverable | Target | Status |
|:--|:------------|:-------|:-------|
| 1 | Preso PR — centralized badge logic | Feb 2026 | 🔵 In Review |
| 2 | Integration testing with IRO | TBD | ⬜ |
| 3 | Staging deploy | TBD | ⬜ |
| 4 | Badge consistency validation across PLP | TBD | ⬜ |
| 5 | Production rollout | TBD | ⬜ |

> [!example]- Status Legend
> ⬜ Not Started · 🔵 In Progress · ✅ Done · ⏸️ Paused · 🔴 Blocked · 🔄 Carryover · 👀 In Review

---

## 📌 Decisions

| Date | Decision | Context |
|:-----|:---------|:--------|
| 2026-02-18 | Centralize badge logic in item-service | Single source of truth — consistency across PLP, SWAG; simplifies maintenance |

---

## ⚠️ Risks & Blockers

| Risk | Impact | Mitigation |
|:-----|:-------|:-----------|
| IRO API reliability | Medium | Fallback logic + monitoring |
| Prefetch performance impact | Medium | Load testing before rollout |
| Badge inconsistency across surfaces | High | Centralized logic eliminates this |

---

## 📈 Progress Log

> Latest first — `[[YYYY-MM-DD]]` for full context.

### 2026-02-18
- Initiative kicked off — agreed on IRO → item-service → Frontend flow
- Preso PR submitted: [vivaldi-server#8772](https://gecgithub01.walmart.com/sams-vivaldi/vivaldi-server/pull/8772)
- Documentation and key links consolidated

---

## 🔗 References

> [!note]- Design, discovery, and deep-dives live externally. Link them here.

|                 | Link                                                                                                                                                                                    |
| :-------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 📄 Confluence   | [Initiative Page](https://confluence.walmart.com/pages/viewpage.action?pageId=3360265578)                                                                                               |
| 📄 Impl Docs    | [Item Service Implementation](https://confluence.walmart.com/display/SEG/Express+Delivery+Badge+-+Item+Service+Implementation)                                                          |
| 📄 Badging Spec | [SANEP Dynamic Badging](https://confluence.walmart.com/display/SANEP/Dynamic+Badging)                                                                                                   |
| 🔀 Key PRs      | [vivaldi-server#8772](https://gecgithub01.walmart.com/sams-vivaldi/vivaldi-server/pull/8772)<br>[item-service](https://gecgithub01.walmart.com/ce-orchestration/item-service/pull/7358) |
| 💬 Slack        | [sams-dynamic-express-updates](https://app.slack.com/client/E30MTJF0C/C09S08ATZME)                                                                                                      |
| 📋 Jira         | TBD                                                                                                                                                                                     |

---

> [!quote] `Discovery → Design → Execution → Testing → Rollout → Monitoring`
