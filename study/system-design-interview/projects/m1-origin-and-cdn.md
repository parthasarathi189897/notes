---
type: sysdesign-milestone
milestone: 1
chapter: 1
parent: "[[README]]"
weeks: "W1-2 (Aug 17-30)"
track: build
status: not-started
created: 2026-08-11
tags: [study, system-design, project, milestone]
---

# M1 — Origin on Mac mini + Cloudflare CDN/Cache

> **Ch 1: Scale From Zero To Millions** · Weeks **W1-2 (Aug 17-30)** · 🔨 Build
> This milestone makes the Ch 1 architecture diagram *run in your house*.

---

## 🎯 What I'm shipping

A static family site served by a reverse proxy (Caddy) on the Mac mini, exposed via a
**Cloudflare Tunnel**, with Cloudflare's CDN caching static assets at the edge. This is the
book's "single server → web tier → CDN" story, live.

**Maps to the book's diagram:** user → Cloudflare (CDN/TLS) → tunnel → web tier (Caddy) → static content.

---

## ✅ Acceptance criteria

- [ ] Domain resolves through Cloudflare to your Mac mini via `cloudflared` (no port-forward)
- [ ] Caddy serves a real static family page over HTTPS (Cloudflare TLS)
- [ ] At least one asset (image/CSS) is **cache HIT** at Cloudflare edge (check `cf-cache-status` header)
- [ ] `ARCHITECTURE.md` started with the current diagram
- [ ] Screenshot: Cloudflare cache analytics OR a `curl -I` showing `cf-cache-status: HIT`

---

## 📅 Week-by-week

| Week | Plan | Done? |
|------|------|-------|
| W1 | Read Ch 1 first half. Install Caddy, serve static site locally on Mac mini. | ⬜ |
| W2 | Read Ch 1 rest. Set up Cloudflare Tunnel, point domain, verify a CDN cache HIT. Draw diagram. | ⬜ |

---

## 🛠️ Setup notes (Mac mini)

- Reverse proxy: **Caddy** (auto-HTTPS, tiny config) — or nginx if preferred.
- Tunnel: `cloudflared tunnel` → maps a public hostname to `localhost:PORT`, outbound-only.
- Keep-alive: run `cloudflared` + Caddy as launchd services so the box survives reboots.
- Cache: static assets cache at Cloudflare by default; verify with `cf-cache-status` response header.

> Install tools via Homebrew only if outside the Walmart network. On Walmart network,
> download `cloudflared` / Caddy binaries directly from vendor release pages.

---

## 🧠 Concept ↔ reality

| Book concept | In this project |
|--------------|-----------------|
| Web tier / data tier separation | Caddy (web) now; DB layer arrives in M5 |
| CDN | Cloudflare edge caching your static assets |
| Load balancer | One origin now — note where an LB would sit if you added a 2nd box |
| DB replication | Not yet — design-note it in ARCHITECTURE.md |

---

## 📊 Numbers

- First-byte latency (cold vs cached):
- Cache HIT ratio (Cloudflare analytics):
- Assets served from edge:

---

## 📝 Post-milestone note

**What worked:**
**What surprised me:**
**One thing I can defend in an interview:**

---

*Back to [[README]] · Next: [[m2-estimation]]*
