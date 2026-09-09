# Coach Brief — Self-directed AI Engineering + System Design study plan

**Person:** Principal engineer, 15 yrs frontend, moving into AI engineering. Kid + busy office.
**Capacity:** 5-6 h/week total → **3.5h AI engineering, 1.5h system design.**
**Prepared:** 2026-09-07, immediately after a rebase. Both paths run in parallel on one shared calendar.
**Tracker:** `study/ai-engineering-path/PROGRESS.md` is the single source of truth for dates and status.

## 1. Status

| | AI Engineering | System Design |
|---|---|---|
| Slots complete | **7 / 48** | **0 / 26** |
| Artifacts shipped | **0 / 9 projects** | **0 / 8 milestones** |
| Repos created | **0** | **0** |
| Last activity | **2026-08-13** | never started |
| Rebased end | **2027-08-22** (was Jul 18) | **2027-05-16** (was May 2) |

- **Confirmed complete:** AI W1-W5 (Phase 0: course C1 + Python ramp), AI W6-W7 (course C2 prompt engineering). All confirmed by the learner directly, not inferred.
- **Partial:** none.
- **Not started:** AI W8-W48, all 9 AI projects, the entire system-design path.
- ⚠️ **All 7 completed weeks were watch-and-take-notes weeks. Zero code has been written.** The plan has never been tested against building anything.

## 2. What derailed him — verbatim

> "Work got busy after mid-Aug and I never restarted the repo work"

Prior derail, from the existing slip log: a ~4-week pause Jul 6 – Aug 2, 2026 for "professional commitments + health issues."

**Pattern worth naming:** W8 was the first week in the entire plan that required creating a repo rather than watching videos. He stopped exactly there, and no slip-log entry was ever written for the 3 weeks lost. The failure was silent.

## 3. Rebased ledger — AI Engineering (abridged; milestones only)

| Slot | Milestone | Original target | Rebased target |
|---|---|---|---|
| W8 | P1 scaffold — repo + 1 test | Aug 27 - Sep 2, 2026 | **Sep 7-13, 2026** ← current |
| W10 | **P1 ship** — JSON extractor CLI | Sep 10-16, 2026 | **Oct 5-11, 2026** |
| W15 | **P2 ship** — semantic search + recall@5 eval | Nov 9-15, 2026 | **Nov 23-29, 2026** |
| W25 | **P3 ship** — RAG v1, citations + logging | Jan 18-24, 2027 | **Feb 22-28, 2027** |
| W30 | **P4 ship** — RAG v2, 30+ golden set | Mar 1-7, 2027 | **Apr 5-11, 2027** |
| W34 | **P5 ship** — eval harness | Mar 29 - Apr 4, 2027 | **May 3-9, 2027** |
| W38 | **P6 ship** — fine-tuning decision memo | Apr 26 - May 2, 2027 | **May 31 - Jun 6, 2027** |
| W43 | **P7 ship** — research agent + trajectory eval | Jun 7-13, 2027 | **Jul 12-18, 2027** |
| W47 | **P8 ship** — CI eval pipeline | Jul 5-11, 2027 | **Aug 9-15, 2027** |
| W48 | **P9 CAPSTONE** — deployed, eval-gated | Jul 12-18, 2027 | **Aug 16-22, 2027** |

## 4. Rebased ledger — System Design (milestones only)

| Slot | Milestone | Rebased target |
|---|---|---|
| W2 | **M1** — family site live behind Cloudflare CDN | **Sep 14-20, 2026** |
| W6 | **M4** — edge rate limiting, real 429s | **Oct 26 - Nov 1, 2026** |
| W10 | **M5** — cache layer on one endpoint | **Nov 30 - Dec 6, 2026** |
| W14 | **M6** — `go/xxx` short-link service | **Feb 1-7, 2027** |
| W18 | **M7** — contact form → email notify | **Mar 1-7, 2027** |
| W22 | **M8** — WebSocket family wall *(proposed cut)* | **Mar 29 - Apr 4, 2027** |
| W26 | Mock interview + capstone wrap | **Apr 26 - May 2, 2027** |

## 5. Holidays and buffers

**🔒 Holidays — fixed anchors. Never move, never spent on catch-up. Both paths.**

| Block | Dates |
|---|---|
| 🧳 Aug travel | Aug 17-26, 2026 *(elapsed)* |
| 🧳 Sep travel | **Sep 25 - Oct 4, 2026** |
| 🪔 Diwali | **Nov 2-8, 2026** |
| 🎄 Year-end break | **Dec 21, 2026 - Jan 10, 2027** |

**🛟 Buffers — catch-up capacity. Preserved, not spent. Slide with the schedule.**

| ID | AI path | SD path |
|---|---|---|
| B1 | Sep 21-24, 2026 | Nov 9-15, 2026 |
| B2 | Oct 26 - Nov 1, 2026 | Nov 30 - Dec 6, 2026 |
| B3 | Mar 15-21, 2027 | May 3-9, 2027 |
| B4 | Jun 21-27, 2027 | May 10-16, 2027 |

> Both plans previously overstated capacity by counting travel as buffer (AI claimed 6, SD claimed 11). **Real capacity is 4 + 4.**

## 6. Findings from the audit

**Artifact gaps**
- **Zero of 75 week notes had a checkable "done when."** Every AI week W8-W48 carried identical boilerplate: *"complete this week's lessons / small code experiment / 1-2 concept notes."* Unfalsifiable. ✅ **75 criteria written and approved 2026-09-07**, now live in every week file as a checkbox.
- 26 of 48 AI weeks were pure reading with no artifact at all.

**Hour overruns**
- Budget was 3.5h/week = 161h. Realistic demand against the written acceptance criteria: **~220h. ~40% over.**
- **13 weeks over 5h; 9 of them at 2-4×.** Worst: W30 P4 ship (10-12h), W34 P5 ship (8-10h), W47 P8 ship (7-9h).
- **The capstone is budgeted 14h and needs 40-60h.** Its criteria include a React frontend with streaming, a citation viewer, a live eval dashboard, public deploy, monitoring, CI gate, demo video and blog post.
- **System design is worse in ratio:** advertised "30 min/week" (13h total), but a project track added in Aug 2026 — Cloudflare Tunnel, Caddy, WAF rate limiting, Redis cache, base62 short-link service, WebSocket wall — needs **40-60h**. M1 alone is 6-10h against 1h allocated.

**Eval placement — back-loaded**
- Evals appear once at W15 (a 5-question recall@5 exercise), then **vanish for 13 weeks**, then arrive all at once W28-W34.
- The real eval harness (P5) lands at **slot 34 of 48 — 70% through, May 2027.**
- **P3, the largest project (10 weeks), has no eval criterion at all.** Its quality bar is "manual review: 7/10 answers factually grounded." That's a vibe check.
- His own ground rule #3 says *"Evals are core engineering… start eval thinking from P2."* The plan doesn't honour it.

**Sequencing problems**
1. **P5 ships after its own consumer.** P4 (W30) requires a groundedness metric and baseline scores; P5 — the harness that produces them — ships W34, four weeks later.
2. **RAG is built before any means of measuring it.** P3 ships W25; the first eval course is W28; the harness is W34. RAG v1 is declared done 9 weeks before it can be evaluated, so no true v1 baseline is ever obtainable.
3. Tracing tool chosen W20; the tracing course is W33.
4. **Three documents described three different plans.** `weeks/` files, `02-progress-tracker.md` and `projects/README.md` disagreed by up to 2 weeks on every ship date. Resolved: week files win; the other two now carry deprecation banners.
5. **Cross-path contradictions:** the AI plan scheduled "P2 main build" on Diwali and "P3 ship" during Dec 28 - Jan 10 — both already declared holidays in his own system-design plan. Reconciled.

## 7. Open questions awaiting his approval

| # | Item | Status |
|---|---|---|
| 1 | ~~75 "done when" criteria across both paths~~ | ✅ **Approved 2026-09-07 — applied** |
| 2 | **C-7: the capstone gap.** ~35h short even after cuts. Options: extend 4 weeks → end **Sep 19, 2027**; or cut frontend to 3 screens, no streaming; or accept a slip on arrival | ⏳ **Needs a decision — this is the resume artifact** |
| 3 | C-1: compress course C6 from 9 weeks to 5, redistribute 4 weeks to P3 build | ⏳ Not approved |
| 4 | C-2/3/4/5/6: scope cuts on P4, P5, P7, P8 and courses C15/C16 (~19h) | ⏳ Not approved |
| 5 | C-8: demote SD milestone M8 (WebSocket wall, already "stretch") to a design note | ⏳ Not approved |
| 6 | Whether the 90/10 AI:SD split he stated matches the 3.5h/1.5h hours he gave (that's ~70/30) | ⏳ Unresolved |

## 8. What a coach should push on

- **The restart cost, not the discipline.** He stops at repo-creation boundaries, twice now. This week's goal is deliberately `uv init` + one passing test — 10 minutes — not a working CLI.
- **Zero artifacts after 7 completed weeks.** Notes are not evidence. The `Shipped` column stays blank until a repo exists.
- **He has never written a slip-log entry in real time.** Both derails were reconstructed after the fact. Six tripwires now exist; the binding one is *no commit in 10 days*.
- **Don't let him re-plan.** He has re-planned twice (Jul 25, Aug 11) and both re-plans produced more documents and zero code. If he arrives wanting to restructure the schedule again, that is the avoidance behaviour.
