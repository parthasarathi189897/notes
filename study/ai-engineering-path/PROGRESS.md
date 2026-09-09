---
type: study-progress-tracker
status: active
role: "Live tracker + coaching contract. This file is the single source of truth."
paths: [ai-engineering, system-design-interview]
rebased: 2026-09-07
ai_end_date: 2027-08-22
sd_end_date: 2027-05-16
hours_per_week: 5
hours_ai: 3.5
hours_sd: 1.5
updated: 2026-09-07
tags: [study, tracker, progress]
---

# 📊 PROGRESS — Live Tracker

> **This file supersedes `02-progress-tracker.md` and the date tables in `01-course-path-timeline.md`.**
> Those two contradicted the `weeks/` files in three different ways. `weeks/week-NN.md` is authoritative for
> *content*; this file is authoritative for *dates and status*. Open this every Sunday.

---

## ▶️ RESUME BLOCK — read this first

```
YOU ARE HERE:   AI W8  ·  Sep 7-13, 2026  ·  Phase 1
                SD W1  ·  Sep 7-13, 2026  ·  Ch 1

LAST DONE:      AI W7 (C2 Prompt Engineering) — finished Aug 13, 2026
                SD — nothing started

THE GAP:        3 study weeks lost (Aug 14 – Sep 6). No repo work has ever happened.

THIS WEEK, AI:  Create `aieng-p01-json-extractor`. Public. pyproject.toml + one passing test.
                That is the whole goal. Not the CLI. Not the schema. The repo and one test.

THIS WEEK, SD:  Get a page serving from the Mac mini over HTTP. Local only. No Cloudflare yet.

FIRST ACTION:   uv init aieng-p01-json-extractor && cd $_ && git init
                ↑ 10 minutes. Do this before you read anything else.
```

> **Why the first action is that small.** You said: *"Work got busy after mid-Aug and I never restarted
> the repo work."* W8 was the first week that asked for a repo instead of a video. You stopped exactly
> there. The fix is not more discipline — it is making the restart cost 10 minutes instead of an evening.

---

## 📍 Status

| | AI Engineering | System Design |
|---|---|---|
| Slots complete | **7 / 48** | **0 / 26** |
| Projects shipped | **0 / 9** | **0 / 8 milestones** |
| Courses complete | 2 / 16 (C1, C2) | 0 / 13 chapters |
| Repos created | **0** | **0** |
| Hours logged | ~5.1h | 0h |
| Current streak | **0 weeks** | — |
| Longest streak | 2 weeks (W3-W4) | — |
| Last activity | **2026-08-13** | — |
| Rebased end date | **2027-08-22** | **2027-05-16** |

> ⚠️ **7 slots complete, 0 artifacts.** Every completed week so far was a watch-and-take-notes week.
> The plan has never been tested against the thing that actually broke it. Treat W8 as week 1.

---
## 🗓️ AI Engineering — week ledger

> `Original target` = the date before this rebase, preserved. Never overwritten.
> `Shipped` = blank until an artifact exists. Blank is a valid, correct value.
> Every `Done when` is **APPROVED (2026-09-07)** and mirrored into the matching `weeks/week-NN.md` file
> as a checkbox. A written note is not a shipped artifact.

| Slot | Topic | Done when | Original target | Rebased target | Shipped |
|---|---|---|---|---|---|
| W1 | C1 GenAI w/ LLMs (1/4) | Concept note on transformers committed | Jun 1-7, 2026 | *(unchanged)* | ✅ 2026-06 |
| W2 | C1 (2/4) | Concept note on pretraining committed | Jun 8-14 | *(unchanged)* | ✅ 2026-06 |
| W3 | C1 (2/4 finish + 3/4) | Concept notes on RLHF committed | Jun 15-21 | *(unchanged)* | ✅ 2026-06 |
| W4 | C1 (4/4) + synthesis | Phase 0 synthesis note committed | Jun 22-28 | *(unchanged)* | ✅ 2026-06 |
| W5 | Python ramp | uv env + Pydantic model + first LLM call | Jun 29 - Jul 5 | *(unchanged)* | ✅ 2026-07 |
| W6 | C2 Prompt Engineering (1/2) | Prompt-engineering guidelines note committed | Aug 3-9 | *(unchanged)* | ✅ 2026-08-08 |
| W7 | C2 Prompt Engineering (2/2) | Inferring/transforming + iterative notes committed | Aug 10-16 | *(unchanged)* | ✅ 2026-08-13 |
| **W8** | C3 Building Systems (1/2) · P1 scaffold | Repo `aieng-p01-json-extractor` public; pyproject.toml + 1 passing test committed | Aug 27 - Sep 2 | **Sep 7-13, 2026** | |
| **W9** | C3 Building Systems (2/2) · P1 main build | CLI returns schema-valid JSON on 5 inputs; token + $ cost printed per call | Sep 3-9 | **Sep 14-20, 2026** | |
| **B1** | BUFFER — pre-travel catch-up | Nothing owed. Optional: finish anything W8-W9 left open | Sep 17-24 | **Sep 21-24, 2026** | |
| 🧳 | **HOLIDAY — Sep travel** | — | — | **Sep 25 - Oct 4, 2026** | — |
| **W10** | (build week) · P1 SHIP | All 6 P1 acceptance criteria ticked; repo public; README <300 words | Sep 10-16 | **Oct 5-11, 2026** | |
| **W11** | C4 Vector DBs (1/2) | Script embeds 10 strings + prints similarity matrix; note on cosine vs dot | Oct 5-11 | **Oct 12-18, 2026** | |
| **W12** | C4 Vector DBs (2/2) | ANN index over 100+ vectors; recall vs brute-force measured and written down | Oct 12-18 | **Oct 19-25, 2026** | |
| **B2** | BUFFER — embeddings catch-up | Nothing owed. Optional: pull nomic-embed-text, compare vs mxbai | Oct 19-25 | **Oct 26 - Nov 1, 2026** | |
| 🎄 | **HOLIDAY — 🪔 Diwali** | — | — | **Nov 2-8, 2026** | — |
| **W13** | C5 Building Apps VDB (1/2) · P2 scaffold | Repo `aieng-p02-semantic-search` public; ingests 20+ local files to a vector store | Oct 26 - Nov 1 | **Nov 9-15, 2026** | |
| **W14** | C5 Building Apps VDB (2/2) · P2 main build | Top-5 query returns file + snippet + score + section metadata; latency logged | Nov 2-8 | **Nov 16-22, 2026** | |
| **W15** | (build week) · P2 SHIP | All 8 P2 criteria ticked incl. 5-question recall@5 eval running in one command | Nov 9-15 | **Nov 23-29, 2026** | |
| **W16** | C6 RAG (1/9) | One-paragraph note: the 6 stages of a RAG pipeline, from memory | Nov 16-22 | **Nov 30 - Dec 6, 2026** | |
| **W17** | C6 RAG (2/9) | Ingestion note: which loaders for md/PDF, and what breaks on each | Nov 23-29 | **Dec 7-13, 2026** | |
| **W18** | C6 RAG (3/9) Chunking | 3 chunking strategies run over the same doc; chunk-count + boundary quality compared | Nov 30 - Dec 6 | **Dec 14-20, 2026** | |
| 🎄 | **HOLIDAY — 🎄 Year-end break** | — | — | **Dec 21-27, 2026** | — |
| 🎄 | **HOLIDAY — 🎄 Year-end break** | — | — | **Dec 28 - Jan 3, 2027** | — |
| 🎄 | **HOLIDAY — 🎄 Year-end break** | — | — | **Jan 4-10, 2027** | — |
| **W19** | C6 RAG (4/9) | Note comparing 2 embedding models on the P2 corpus with recall numbers | Dec 7-13 | **Jan 11-17, 2027** | |
| **W20** | C6 RAG (5/9) · P3 scaffold | Repo `aieng-p03-rag-v1` public; tracing tool chosen and capturing 1 request | Dec 14-20 | **Jan 18-24, 2027** | |
| **W21** | C6 RAG (6/9) · P3 ingestion | 50+ docs ingested end-to-end; chunk count + index size logged | Dec 21-27 | **Jan 25-31, 2027** | |
| **W22** | C6 RAG (7/9) · P3 retrieval | Query returns top-k chunks with scores; retrieval logged to JSON per query | Dec 28 - Jan 3, 2027 | **Feb 1-7, 2027** | |
| **W23** | C6 RAG (8/9) · P3 generation | Query returns a generated answer grounded in retrieved chunks | Jan 4-10 | **Feb 8-14, 2027** | |
| **W24** | C6 RAG (9/9) · P3 citations + logs | Every answer carries citations resolving to real chunks; full log entry per query | Jan 11-17 | **Feb 15-21, 2027** | |
| **W25** | (build week) · P3 SHIP (RAG v1) | All 7 P3 criteria ticked; architecture diagram in README; repo public | Jan 18-24 | **Feb 22-28, 2027** | |
| **W26** | C7 Advanced Retrieval (1/2) | Note: query expansion vs reranking — when each helps, with a worked example | Jan 25-31 | **Mar 1-7, 2027** | |
| **W27** | C7 Advanced Retrieval (2/2) · RAG v1 + 2 improvements | 2 retrieval improvements running in the v1 repo; before/after numbers recorded | Feb 1-7 | **Mar 8-14, 2027** | |
| **B3** | BUFFER — Phase 4 catch-up | Nothing owed. Optional: expand golden-set draft, re-run v1 evals | Feb 8-14 | **Mar 15-21, 2027** | |
| **W28** | C8 Build & Eval Adv RAG (1/2) · Golden set draft | 30+ golden questions with expected sources committed as JSONL | Feb 15-21 | **Mar 22-28, 2027** | |
| **W29** | C8 Build & Eval Adv RAG (2/2) · P4 build | Groundedness + correctness scored on the golden set; baseline recorded | Feb 22-28 | **Mar 29 - Apr 4, 2027** | |
| **W30** | (build week) · P4 SHIP (RAG v2) | All 8 P4 criteria ticked incl. 5 categorised failure modes; repo public | Mar 1-7 | **Apr 5-11, 2027** | |
| **W31** | C9 Improving Accuracy (1/2) | Note: 3 accuracy levers ranked by cost-to-try on your own RAG | Mar 8-14 | **Apr 12-18, 2027** | |
| **W32** | C9 Improving Accuracy (2/2) | Iteration log: 3 prompt variants scored against the golden set | Mar 15-21 | **Apr 19-25, 2027** | |
| **W33** | C10 Eval & Debug GenAI · P5 scaffold | Repo `aieng-p05-eval-harness` public; runs 1 question end-to-end and writes a score | Mar 22-28 | **Apr 26 - May 2, 2027** | |
| **W34** | (build week) · P5 SHIP (eval harness) | All 7 P5 criteria ticked; 30+ questions in <10 min from one command | Mar 29 - Apr 4 | **May 3-9, 2027** | |
| **W35** | C11 Finetuning LLMs (1/2) | Note: 4 concrete signals that prompting/RAG has run out of road | Apr 5-11 | **May 10-16, 2027** | |
| **W36** | C11 Finetuning LLMs (2/2) | Note: what a fine-tuning dataset actually looks like, with 3 example rows | Apr 12-18 | **May 17-23, 2027** | |
| **W37** | C12 Post-training · Memo outline | P6 memo outline covering all 8 required sections, one line each | Apr 19-25 | **May 24-30, 2027** | |
| **W38** | (write week) · P6 SHIP (decision memo) | All 5 P6 criteria ticked; go/no-go recommendation stated; repo public | Apr 26 - May 2 | **May 31 - Jun 6, 2027** | |
| **W39** | C13 Agentic AI (1/2) | Note: reflection vs planning vs tool-use, with a failure example of each | May 3-9 | **Jun 7-13, 2027** | |
| **W40** | C13 Agentic AI (2/2) · P7 scaffold | Repo `aieng-p07-research-agent` public; agent loop runs 1 query with logged steps | May 10-16 | **Jun 14-20, 2027** | |
| **B4** | BUFFER — reset before capstone | Nothing owed. Optional: sketch capstone architecture on paper | May 17-23 | **Jun 21-27, 2027** | |
| **W41** | C14 Evaluating Agents (1/2) · P7 plan loop | Planner emits a step list; each step logged with its output | May 24-30 | **Jun 28 - Jul 4, 2027** | |
| **W42** | C14 Evaluating Agents (2/2) · P7 tool integration | 1-2 tools callable by the agent; tool calls + results logged | May 31 - Jun 6 | **Jul 5-11, 2027** | |
| **W43** | (build week) · P7 SHIP (research agent) | All 7 P7 criteria ticked incl. trajectory eval scoring each run; repo public | Jun 7-13 | **Jul 12-18, 2027** | |
| **W44** | C15 LLMOps (1/2) | Note: what an LLM deploy pipeline needs that a normal one doesn't | Jun 14-20 | **Jul 19-25, 2027** | |
| **W45** | C15 LLMOps (2/2) · Capstone scaffold | Repo `aieng-p09-capstone` public; backend serves 1 RAG query from P3 code | Jun 21-27 | **Jul 26 - Aug 1, 2027** | |
| **W46** | C16 Auto Testing LLMOps · P8 scaffold + capstone wiring | Repo `aieng-p08-ci-eval-pipeline` public; GH Action runs unit tests on push | Jun 28 - Jul 4 | **Aug 2-8, 2027** | |
| **W47** | (build week) · P8 SHIP + capstone eval dashboard | All 7 P8 criteria ticked incl. intentional regression failing the build | Jul 5-11 | **Aug 9-15, 2027** | |
| **W48** | (capstone) · P9 CAPSTONE SHIP | All 10 P9 criteria ticked: deployed, eval-gated, demo video, blog post | Jul 12-18 | **Aug 16-22, 2027** | |

---

## 🗓️ System Design — week ledger

> Same rules. All 30 `Done when` values are **APPROVED (2026-09-07)** and mirrored into `system-design-interview/weeks/`.

| Slot | Topic | Done when | Original target | Rebased target | Shipped |
|---|---|---|---|---|---|
| **W1** | Ch1 Scale 0→millions — read 1st half | Mac mini serving a page locally over HTTP | Aug 31 - Sep 6 | **Sep 7-13, 2026** | |
| **W2** | Ch1 finish + diagram · **M1 SHIP** | `curl -I` shows `cf-cache-status: HIT`; diagram drawn from memory | Sep 7-13 | **Sep 14-20, 2026** | |
| — | *pre-travel, 0h* | — | — | **Sep 21-24, 2026** | — |
| 🧳 | **HOLIDAY — Sep travel** | — | — | **Sep 25 - Oct 4, 2026** | — |
| **W3** | Ch2 Estimation · **M2** | QPS / storage / bandwidth estimated for the family site, written down | Sep 14-20 | **Oct 5-11, 2026** | |
| **W4** | Ch3 Framework · **M3** | 4-step design doc for your own site committed | Sep 21-27 | **Oct 12-18, 2026** | |
| **W5** | Ch4 Rate limiter — algorithms | Note comparing token bucket vs leaky bucket vs sliding window | Sep 28 - Oct 4 | **Oct 19-25, 2026** | |
| **W6** | Ch4 finish + diagram · **M4 SHIP** | A real 429 observed and screenshotted from your own site | Oct 5-11 | **Oct 26 - Nov 1, 2026** | |
| 🪔 | **HOLIDAY — 🪔 Diwali** | — | — | **Nov 2-8, 2026** | — |
| **W7** | Ch5 Consistent hashing — hash ring | Hash ring drawn by hand; note on why mod-N rehashing hurts | Oct 12-18 | **Nov 9-15, 2026** | |
| **W8** | Ch5 finish + diagram | Design note: how I'd shard this at 1B users | Oct 19-25 | **Nov 16-22, 2026** | |
| **W9** | Ch6 Key-value store — CAP | Note: where your site sits on CAP and why | Oct 26 - Nov 1 | **Nov 23-29, 2026** | |
| **W10** | Ch6 finish + diagram · **M5 SHIP** | One endpoint served from cache; hit/miss latency both measured | Nov 2-8 | **Nov 30 - Dec 6, 2026** | |
| **B1** | BUFFER — catch up / re-draw | Nothing owed | Nov 9-15 | **Dec 7-13, 2026** | |
| **W11** | Ch7 Unique ID — UUID vs Snowflake | Snowflake bit layout drawn from memory | Nov 16-22 | **Dec 14-20, 2026** | |
| 🎄 | **HOLIDAY — 🎄 Year-end break** | — | — | **Dec 21-27, 2026** | — |
| 🎄 | **HOLIDAY — 🎄 Year-end break** | — | — | **Dec 28 - Jan 3, 2027** | — |
| 🎄 | **HOLIDAY — 🎄 Year-end break** | — | — | **Jan 4-10, 2027** | — |
| **W12** | Ch7 finish + diagram | Design note: Snowflake vs UUID for your own DB keys | Nov 23-29 | **Jan 11-17, 2027** | |
| **B2** | BUFFER — review Ch1-7 diagrams | Nothing owed. Test: can you draw all 7? | Nov 30 - Dec 6 | **Jan 18-24, 2027** | |
| **W13** | Ch8 URL shortener — hash, base62 | Note on base62 encoding + collision handling | Dec 7-13 | **Jan 25-31, 2027** | |
| **W14** | Ch8 finish + diagram · **M6 SHIP** | `go/xxx` resolves with a 301 on your live site; click count works | Dec 14-20 | **Feb 1-7, 2027** | |
| **W15** | Ch9 Web crawler — BFS, frontier | Note on frontier design + politeness | Dec 21-27 | **Feb 8-14, 2027** | |
| **W16** | Ch9 finish + diagram | Design note: crawler architecture | Dec 28 - Jan 3 | **Feb 15-21, 2027** | |
| **W17** | Ch10 Notification system | Note on the fan-out + retry path | Jan 4-10 | **Feb 22-28, 2027** | |
| **W18** | Ch10 finish + diagram · **M7 SHIP** | Contact form sends a real email; failure path handled | Jan 11-17 | **Mar 1-7, 2027** | |
| **W19** | Ch11 News feed — fan-out | Note: fan-out on write vs on read, with the tradeoff | Jan 18-24 | **Mar 8-14, 2027** | |
| **W20** | Ch11 finish + diagram | Design note: fan-out for a family updates feed | Jan 25-31 | **Mar 15-21, 2027** | |
| **W21** | Ch12 Chat — WebSocket, 1:1 | Note on connection state + delivery guarantees | Feb 1-7 | **Mar 22-28, 2027** | |
| **W22** | Ch12 finish + diagram · **M8 SHIP** (stretch) | Live WebSocket update visible on two devices | Feb 8-14 | **Mar 29 - Apr 4, 2027** | |
| **W23** | Ch13 Autocomplete — trie, top-k | Trie sketched by hand with a worked top-k example | Feb 15-21 | **Apr 5-11, 2027** | |
| **W24** | Ch13 finish + diagram | Design note: autocomplete over your own content | Feb 22-28 | **Apr 12-18, 2027** | |
| **W25** | Re-draw 3 weakest diagrams | 3 diagrams redrawn from memory, 5 min each, timed | Mar 1-7 | **Apr 19-25, 2027** | |
| **W26** | Mock + capstone wrap | 15-min design explained out loud and recorded; ARCHITECTURE.md committed | Mar 8-14 | **Apr 26 - May 2, 2027** | |
| **B3** | BUFFER — catch-up / rest | Nothing owed | Mar 15-21 | **May 3-9, 2027** | |
| **B4** | BUFFER — final wrap | Nothing owed. Optional 2nd mock | Mar 22-28 | **May 10-16, 2027** | |

---

## 🛟 Buffer ledger

> Buffers are **rest and catch-up capacity**. Per your instruction they were **not** spent absorbing the
> slip — the end date moved instead. They slide with the schedule; holidays do not.

| ID | Path | Original | Rebased | Purpose | Spent? |
|---|---|---|---|---|---|
| B1 | AI | Sep 17-24, 2026 | **Sep 21-24, 2026** | Pre-travel catch-up | ⬜ |
| B2 | AI | Oct 19-25, 2026 | **Oct 26 - Nov 1, 2026** | Embeddings catch-up | ⬜ |
| B3 | AI | Feb 8-14, 2027 | **Mar 15-21, 2027** | Phase 4 catch-up | ⬜ |
| B4 | AI | May 17-23, 2027 | **Jun 21-27, 2027** | Reset before capstone | ⬜ |
| B1 | SD | Nov 30 - Dec 6, 2026 | **Nov 9-15, 2026** | Catch up / re-draw | ⬜ |
| B2 | SD | Dec 21-27, 2026 | **Nov 30 - Dec 6, 2026** | Review Ch 1-7 diagrams | ⬜ |
| B3 | SD | Apr 19-25, 2027 | **May 3-9, 2027** | Catch-up / rest | ⬜ |
| B4 | SD | Apr 26 - May 2, 2027 | **May 10-16, 2027** | Final wrap | ⬜ |

**Remaining capacity: 4 AI + 4 SD buffer weeks.** Both plans previously advertised more (AI "6", SD "11")
by counting travel and festivals as buffers. They are not. Corrected here.

### 🔒 Holiday anchors — never move, never spent on catch-up

| Block | Dates | Applies to |
|---|---|---|
| 🧳 Aug travel | **Aug 17-26, 2026** | Both — *already elapsed* |
| 🧳 Sep travel | **Sep 25 - Oct 4, 2026** | Both |
| 🪔 Diwali | **Nov 2-8, 2026** | Both — **newly added to the AI path** |
| 🎄 Year-end break | **Dec 21, 2026 - Jan 10, 2027** | Both — **newly added to the AI path** |

> The AI path previously scheduled *"P2 main build"* on Diwali and *"P3 SHIP"* on Jan 4-10, both of which
> you had already declared holidays in the system-design plan. Reconciled.

---

## 🪫 Reduced mode

> Trigger it deliberately when a week is going to be 1h instead of 4. **Reduced mode protects the streak.
> It is a legitimate week, not a failure.** Mark the slot `🪫` in the ledger, not `⚠️`.

| Normal week | Reduced week (≤1h) |
|---|---|
| Course lessons + labs | Watch lessons only. Skip labs. |
| Project deliverable | **One commit.** Any size. A README line counts. |
| 1-2 concept notes | One sentence in the session log. |
| Sunday retro | Tick the ledger row. 60 seconds. |

**The reduced-mode floor, for a build week:** `git commit` something to the current project repo.
Not "make progress." A commit. If the repo does not exist yet, `uv init` + `git init` + push is the week.

**Rule:** two consecutive reduced weeks is fine. Three fires TW-2 below.

---

## 🚨 Tripwires

> Built against your stated failure mode: *"Work got busy after mid-Aug and I never restarted the repo work."*
> The pattern was **silent** — no slip-log entry was ever written for the 3 weeks you lost. These exist to
> make the next one loud and early.

| # | Trip condition | Action — not optional |
|---|---|---|
| **TW-1** | **No commit to the current project repo in 10 days** | Drop to reduced mode. Next session is 20 min and its only goal is one commit. |
| **TW-2** | **3 consecutive reduced weeks** | Stop advancing the ledger. Spend the next slot on a buffer instead. Write the slip-log row *before* resuming. |
| **TW-3** | **A build/ship week ends with the repo not created** | Do not move to the next slot. The ship week repeats. Creating the repo is the whole job. |
| **TW-4** | **2 weeks with no session-log entry at all** | This is the Aug-2026 signature. Open PROGRESS.md, write the slip-log row, then do the 10-minute first action from the resume block. |
| **TW-5** | **Work crunch declared** (you know when) | Pre-emptively mark the next 2 slots reduced. Do it *in advance* — deciding early is what stops the silent drift. |
| **TW-6** | **A slot is ticked complete with a blank `Shipped` cell on a build week** | Untick it. A written note is not a shipped artifact. |

> **The meta-tripwire:** if you are reading this file and the "Last activity" date in Status is more than
> 14 days old, do not re-plan. Do not re-read the timeline. Do the first action in the resume block.

---

## 🌫️ Shaky concepts

> Anything you would fumble in an interview. Add rows freely — this table getting longer is a good sign.
> Confidence: **L** = can't explain it · **M** = can explain, can't apply · **H** = can build with it.

| Concept | Path | Conf | Last touched | Where it's revisited | Note |
|---|---|---|---|---|---|
| RLHF | AI | **L** | Jun 2026 | W37 (C12 post-training) | [[concepts/Reinforcement learning - Human feedback]] |
| Attention / transformers | AI | M | Jun 2026 | not revisited — accept as M | [[concepts/attention-intuition]] |
| Transformer architecture | AI | M | Jun 2026 | not revisited | [[concepts/Transformer Architecture]] |
| In-context learning | AI | M | Jun 2026 | W16-W24 (RAG) | [[concepts/In-Context Learning]] |
| Fine-tuning | AI | M | Jun 2026 | W35-W38 | [[concepts/Fine Tuning]] |
| Model evaluation | AI | M | Jun 2026 | W28-W34 | [[concepts/Model Evaluation]] |
| **Python / async / httpx** | AI | **?** | Jul 2026 | **W8 — about to be tested** | Phase 0 ramp done, never used in anger |
| Pydantic | AI | ? | Jul 2026 | **W8-W10** | [[concepts/pydantic]] |
| — everything | SD | **L** | never | W1 onward | Path not started |

> **Flag:** the two rows marked `?` are the ones W8 depends on. If W8 stalls, it is probably here, and the
> fix is a 30-minute Pydantic refresher, not more course video.

---

## 📋 PROPOSED — scope cuts for weeks over 5 hours

> ✅ The 75 `Done when` criteria were approved on 2026-09-07 and are now live in the ledgers above and in
> every week file. **The scope cuts below are still unapproved.**

> **Cutting scope only. No acceptance criterion is touched.** You approve these; I don't apply them.
> At 3.5h/week the AI path has **~144h** of capacity left and **~220h** of work. These close ~60h of that.

| # | Week(s) | Est. | Proposed cut | Criteria affected |
|---|---|---|---|---|
| **C-1** | W16-W24 | 9 wks | **Compress C6 RAG from 9 weeks to 5** (2 lessons/wk). Frees 4 weeks, redistributed to P3 build. | None |
| **C-2** | W30 P4 ship (10-12h) | −4h | Generate the 30 golden questions **semi-automatically** from the corpus, then hand-edit — instead of writing all 30 by hand. | None — still 30+ with expected sources |
| **C-3** | W34 P5 ship (8-10h) | −3h | Eval harness stores history as **append-only JSONL**, not a DB + chart. Summary report is markdown, not HTML. | None — "stores historical results" still met |
| **C-4** | W43 P7 ship (7-9h) | −3h | Agent gets **one** tool, not two. Trajectory eval scores 10 runs, not a framework. | None — spec already says "pick 1-2" |
| **C-5** | W47 P8 ship (7-9h) | −3h | Split: P8 ships W47, **capstone eval dashboard moves to W48**. | None |
| **C-6** | W44-W46 | −6h | **Skim C15 + C16 without labs** (watch only). Frees ~6h into the capstone. | None — no project depends on their labs |
| **C-7** | W45-W48 capstone (40-60h vs 14h) | — | ⚠️ **Unresolved.** Even with C-6 the capstone is ~35h short. Options: (a) extend 4 more weeks → end **Sep 19, 2027**; (b) cut the frontend to 3 screens, no streaming; (c) accept a slip when you get there. **Needs your call.** |
| **C-8** | SD M8 (WebSocket wall) | −8h | **Demote to a design note.** Spec already marks it "stretch". | Milestone count 8 → 7 |
| **C-9** | SD M1 (6-10h vs 1h) | — | Split M1 across W1-W2 as already scheduled, but **W1 = local HTTP only**, W2 = Cloudflare. | None |

> **C-7 is the one that matters.** The capstone is the resume artifact. Everything else can slip; that can't.

---

## 📝 Session log

> One row per session. 15 minutes counts. **This is the tripwire's data source — if this table stops
> growing, TW-4 fires.** Backfilled entries from `weeks/` are marked ↩.

| Date | Path | Slot | Min | What happened |
|---|---|---|---|---|
| 2026-08-04 ↩ | AI | W6 | 30 | Started C2, watched intro videos |
| 2026-08-08 ↩ | AI | W6 | 20 | A few more videos. W6 goals ticked. |
| 2026-08-11 ↩ | AI | W7 | 30 | Inferring + transforming prompts |
| 2026-08-13 ↩ | AI | W7 | 30 | Remaining videos: temperature, small chatbot. W7 goals ticked. |
| *2026-08-14 → 2026-09-06* | — | — | **0** | ⚠️ **3 weeks lost.** "Work got busy after mid-Aug and I never restarted the repo work." |
| | | | | |

---

## 🚨 Slip log

| Period | Reason | What changed |
|---|---|---|
| W2 (Jun 8-14, 2026) | Busy week, couldn't protect Sat AM. 0.83h of 3.5h. | W3 absorbed the remainder. |
| **Jul 6 – Aug 2, 2026** (~4 wks) | Professional commitments + health. | Slipped whole schedule ~4 wks. Resumed W6 Aug 3. Added 2 travel buffers. |
| **Aug 14 – Sep 6, 2026** (3 wks) | *"Work got busy after mid-Aug and I never restarted the repo work."* | **This rebase.** End date Jul 18 → **Aug 22, 2027**. Buffers preserved. Diwali + year-end added as holidays. Tripwires added. |

---

## 🛠️ Sunday ritual (5 minutes)

1. Fill the session-log rows for the week. Honestly. Zero is a valid entry.
2. Ledger row: tick `Shipped` **only if the artifact exists**. Otherwise leave blank.
3. Check the tripwire table. Any firing? Do the action now, not next week.
4. Update `Status` — especially **Last activity**.
5. Update the shaky-concepts table if something got clearer or murkier.
6. Read the resume block. Set next week's first action to something ≤10 minutes.

---

*Superseded: [[02-progress-tracker]] · [[01-course-path-timeline]] · Specs: [[projects/README]] · Brief: [[COACH-BRIEF]]*
