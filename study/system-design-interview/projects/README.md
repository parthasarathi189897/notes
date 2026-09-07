---
type: sysdesign-projects
parent: "[[../README]]"
milestones_total: 8
design_notes_total: 6
project_name: "Family Website — Mac mini + Cloudflare"
hosting: "Cloudflare Tunnel (no port-forward, home IP hidden)"
repo: "family-site"
created: 2026-08-11
updated: 2026-08-11
tags:
  - study
  - system-design
  - projects
---

# Project Track — Family Website (E2E System Design Lab)

> **One real project, run in parallel with the book.** A family website self-hosted on a
> Mac mini, routed through a WiFi router and a Cloudflare-managed domain.
> Two goals in one shot: (1) ship a real family site, (2) feel the system-design concepts
> in your own hands instead of only drawing them.
>
> Runs alongside [[../study-plan|the 26-week book plan]]. The book teaches billion-user
> theory; this project lets you *touch* the ~5 chapters that map onto a real single-box site.

---

## 🧭 The honest scope

Alex Xu Vol 1 is about **massive-scale** distributed systems. Your project is **one box + ~5 family users**.
That mismatch is fine — we split every chapter into one of two tracks:

- 🔨 **Build milestone** — the chapter maps onto something you can actually run and observe.
- 📝 **Design note** — the chapter is a billion-user problem; you write a short "how I'd scale this"
  note against *your* site instead of building it.

**7 build milestones + 6 design notes.** The three strongest hands-on wins are **Ch 1 (CDN + tiers),
Ch 4 (edge rate limiting), and Ch 8 (short-link service)** — all three run live in your house.

> ⚠️ **Hosting decision (footgun-free):** use **Cloudflare Tunnel** (`cloudflared`), not
> router port-forwarding. No exposed home IP, no ISP inbound-server issues, no dynamic-IP
> pain — and the tunnel itself is a lovely reverse-proxy / zero-trust teaching artifact.

---

## 🗺️ Chapter → milestone map

| Ch | Book topic | Week | Milestone | Track | Spec |
|----|-----------|------|-----------|:-----:|------|
| 1 | Scale 0→millions | W1-2 | **M1** — Origin on Mac mini + Cloudflare CDN/cache in front | 🔨 | [[m1-origin-and-cdn]] |
| 2 | Estimation | W3 | **M2** — Estimate real family traffic (QPS/storage/bandwidth) | 🔨 | [[m2-estimation]] |
| 3 | Interview framework | W4 | **M3** — Write the site's own 4-step design doc | 🔨 | [[m3-design-doc]] |
| 4 | Rate limiter | W5-6 | **M4** — Cloudflare WAF rate-limit rule, observe 429s | 🔨 | [[m4-rate-limiter]] |
| 5 | Consistent hashing | W7-8 | Design note — "how I'd shard at 1B users" | 📝 | [[design-notes#ch-5-consistent-hashing]] |
| 6 | Key-value store | W9-10 | **M5** — Add a cache layer (Redis/SQLite) to one endpoint | 🔨 | [[m5-cache-layer]] |
| 7 | Unique ID generator | W11-12 | Design note — Snowflake vs UUID for your DB PKs | 📝 | [[design-notes#ch-7-unique-id]] |
| 8 | URL shortener | W13-14 | **M6** — Real `go/xxx` short-link service on the site | 🔨 | [[m6-short-links]] |
| 9 | Web crawler | W15-16 | Design note (optional: crawl own site → sitemap) | 📝 | [[design-notes#ch-9-web-crawler]] |
| 10 | Notification system | W17-18 | **M7** — Contact form → email notification (1 channel) | 🔨 | [[m7-notifications]] |
| 11 | News feed | W19-20 | Design note — fan-out for a family "updates" feed | 📝 | [[design-notes#ch-11-news-feed]] |
| 12 | Chat system | W21-22 | **M8** — WebSocket "family wall" live updates (stretch) | 🔨 | [[m8-family-wall]] |
| 13 | Search autocomplete | W23-24 | Design note (optional: trie autocomplete over content) | 📝 | [[design-notes#ch-13-autocomplete]] |
| — | Review + mock | W25-26 | **Capstone wrap** — full ARCHITECTURE.md + walkthrough | 🔨 | [[capstone-wrap]] |

---

## 🧱 Target architecture (end state)

```
Family devices / public
        │  (HTTPS, DNS via Cloudflare)
        ▼
   Cloudflare edge  ── CDN cache (Ch1) · WAF rate limit (Ch4) · TLS
        │  (Cloudflare Tunnel — outbound only, home IP hidden)
        ▼
   cloudflared  →  Reverse proxy (Caddy)   [on Mac mini]
                        │
         ┌──────────────┼───────────────┐
         ▼              ▼                ▼
   Static site     App server        Short-link svc (Ch8)
   (family info)   (contact form,    base62 + cache + 301
                   family wall)
                        │
                   Cache layer (Ch6: Redis/SQLite)
                        │
                   Data store (SQLite/Postgres)
```

Each milestone lights up one more box in this diagram. By W26 the whole thing is real.

---

## 📦 Repo strategy

One repo: **`family-site`** (it's one product, not nine). Suggested layout:

```
family-site/
├── README.md            # Problem → architecture → tradeoffs → how to run
├── ARCHITECTURE.md      # The diagram above + decisions (grows each milestone)
├── Caddyfile            # Reverse proxy config
├── cloudflared/         # Tunnel config
├── static/              # Family info site
├── app/                 # Contact form, family wall, short-links
├── infra/               # Setup scripts, systemd/launchd plists
└── docs/                # Design notes, screenshots
```

> Commit after every milestone. Tag `m1`, `m2`, … so the history *is* the learning log.

---

## ✅ Global rules

1. **Book first, build second.** Read/watch the chapter, then do the milestone. Theory gives you the "why".
2. **A milestone is done when you can demo it** — a URL, a 429, a cache hit in logs. Not "code kinda runs".
3. **Every milestone updates `ARCHITECTURE.md`** with one paragraph: what changed and why.
4. **Design notes are ≤1 page.** Answer: "what would I add, and what pain forces it?" — don't build them.
5. **Low time budget is fine.** Milestones are sized for 30-60 min. Slip, don't skip. Streak > sprint.
6. **Screenshot the wins** (Cloudflare cache ratio, a 429, the live short link). Those are your interview artifacts.

---

## 🔗 Live links (fill as you go)

| What | URL | Status |
|------|-----|--------|
| Family site (public) | — | ⬜ |
| `family-site` repo | — | ⬜ |
| Cloudflare Tunnel | — | ⬜ |

---

*Back to [[../README]] · [[../progress-tracker]] · [[../study-plan]]*
