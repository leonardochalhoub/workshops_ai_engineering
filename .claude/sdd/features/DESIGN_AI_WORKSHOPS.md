# DESIGN: AI Engineering Workshops — Workshop 1 Facilitation Material

> Technical design for a bilingual, GitHub-Pages-hosted facilitation kit: a carousel deck + printable Business Model Canvas + facilitator cheat-sheet + student handout, plus a live Council demo flow.

## Metadata

| Attribute | Value |
|-----------|-------|
| **Feature** | AI_WORKSHOPS |
| **Date** | 2026-06-02 |
| **Author** | design-agent |
| **DEFINE** | [DEFINE_AI_WORKSHOPS.md](./DEFINE_AI_WORKSHOPS.md) |
| **Status** | Ready for Build |
| **Live URL (target)** | https://leonardochalhoub.github.io/workshops_ai_engineering/ |

---

## Architecture Overview

```text
┌──────────────────────────────────────────────────────────────────────┐
│              workshops_ai_engineering  (GitHub Pages, main /)          │
├──────────────────────────────────────────────────────────────────────┤
│                                                                        │
│   index.html ──────────────► SERIES LANDING (hub)                     │
│   (root, self-contained)      • bilingual title + cards (links)       │
│        │                      • dark/light + EN/PT toggle              │
│        └──► workshop-01/  (all W1 deliverables; workshop-02..04 later) │
│             ├──► presentation/index.html ... THE DECK (27 slides)     │
│             │        SlideEngine · data-en/pt · 2 themes · lava blob  │
│             ├──► materials/business-model-canvas.html . BMC (wkd+blank)│
│             ├──► materials/facilitator-cheatsheet.html . SCRIPT(print)│
│             └──► materials/student-handout.html ....... PRE-READ(print)│
│                                                                        │
│   .nojekyll  (serve files verbatim)     assets/ (optional shared SVG) │
│                                                                        │
│   EXTERNAL (not in page):                                             │
│     • Google Fonts CDN (Inter, JetBrains Mono) — graceful fallback    │
│     • LIVE COUNCIL: Leo's terminal → Claude Code → .claude/agents/    │
│       conselheiro-* (copied from mirante) — screen-shared, deck cues  │
└──────────────────────────────────────────────────────────────────────┘

Navigation:  ← → / scroll / swipe / dots   |   Toggles persist in localStorage
Render path: every text node carries data-en + data-pt → JS innerHTML swap
```

Each HTML artifact is **fully self-contained** (inline CSS + JS). No shared stylesheet → zero base-path fragility on GitHub Pages, and each file stays portable (matches the `professional-presentations` single-file philosophy).

---

## Components

| Component | Purpose | Technology |
|-----------|---------|------------|
| **Landing hub** (`index.html`) | Entry point on Pages; bilingual title + 4 navigation cards; sets the visual tone | Vanilla HTML/CSS/JS, inline |
| **The Deck** (`presentation/index.html`) | The 27-slide Workshop 1 presentation Leo leads from | `SlideEngine` (IntersectionObserver + scroll-snap), inline CSS design-system, lava blob |
| **Bilingual+Theme engine** | Instant EN/PT swap + dark/light, persisted | `data-en`/`data-pt` innerHTML swap; `localStorage` keys `ws-lang`, `ws-theme` |
| **Business Model Canvas** (`materials/business-model-canvas.html`) | Teach + capture the model; worked (Pequeno Comércio) + blank | CSS Grid 9-block canvas, `@media print` landscape |
| **Facilitator cheat-sheet** (`materials/facilitator-cheatsheet.html`) | Minute-by-minute script, say-cues, Council prompts, URLs | Print-first HTML, `@media print` portrait |
| **Student handout** (`materials/student-handout.html`) | Pre-read + account/setup checklist sent before 06 Jun | Print-first HTML, portrait |
| **Live Council kit** (`.claude/agents/conselheiro-*.md`) | Make the on-screen agent demo runnable from this repo | 4 agent files copied from `mirante-dos-dados-br` |
| **Pages deploy** (`.nojekyll`, git push, Pages API) | Publish to the public URL | `gh` CLI + GitHub Pages |

---

## Key Decisions

### Decision 1: Reuse the DQX deck engine (vanilla single-file), not a framework

| Attribute | Value |
|-----------|-------|
| **Status** | Accepted |
| **Date** | 2026-06-02 |

**Context:** DEFINE requires the `professional-presentations` look (scroll-snap carousel, reveal, Lava accent) and a self-contained, no-build artifact.

**Choice:** Port the proven `SlideEngine` + CSS design-system from `professional-presentations/course/index.html` into a fresh, workshop-themed deck.

**Rationale:** It already satisfies AT-001…AT-003, AT-008, AT-009; rebuilding would risk parity and waste time. Vanilla = opens anywhere, students can read the source.

**Alternatives Rejected:**
1. Reveal.js / framework deck — extra deps, build step, less portable, harder to make pixel-match.
2. Google Slides / PDF — no bilingual toggle, no live theme, not on-brand.

**Consequences:** (+) Instant parity, offline-capable. (−) ~340 lines of CSS duplicated per file (accepted; matches reference).

---

### Decision 2: Bilingual via `data-en`/`data-pt` innerHTML swap

| Attribute | Value |
|-----------|-------|
| **Status** | Accepted · **Date** 2026-06-02 |

**Context:** R3 — every visible string must toggle PT-BR/EN instantly, anywhere.

**Choice:** Each text node carries both `data-en` and `data-pt`; `applyLang(lang)` swaps `innerHTML`. No-flash inline script restores saved lang/theme before paint.

**Rationale:** Single source file, no i18n library, no flicker; identical to the reference so behavior is known-good.

**Alternatives Rejected:**
1. Two separate HTML files (en/pt) — duplicate maintenance, no instant toggle.
2. i18n JS library — overkill for a static deck, adds a dependency.

**Consequences:** (+) One file, instant switch. (−) Authoring discipline: **every** string needs both attrs (enforced by AT-002 / success metric "0 leftover-language nodes").

---

### Decision 3: GitHub Pages from `main` root, relative links, `.nojekyll`

| Attribute | Value |
|-----------|-------|
| **Status** | Accepted · **Date** 2026-06-02 |

**Context:** R: publish to `leonardochalhoub.github.io/workshops_ai_engineering/`. Pages serves under a `/<repo>/` base path.

**Choice:** Deploy from `main` branch root. All inter-page links **relative** (`presentation/index.html`, `../index.html`). Add `.nojekyll` so files (incl. any `_`-prefixed) serve verbatim. Enable Pages via `gh api`.

**Rationale:** Root deploy keeps paths simple; relative links survive the base path; `.nojekyll` avoids Jekyll surprises. No CI needed — static push.

**Alternatives Rejected:**
1. `/docs` folder source — would force materials under `docs/`, awkward layout.
2. `gh-pages` branch via Action — unnecessary build complexity for static files.

**Consequences:** (+) Dead-simple, push-to-publish. (−) Must never use absolute `/...` paths (lint check in testing).

---

### Decision 4: Each artifact fully self-contained (no shared CSS file)

| Attribute | Value |
|-----------|-------|
| **Status** | Accepted · **Date** 2026-06-02 |

**Context:** Hosting under a base path + desire for portability.

**Choice:** Inline all CSS/JS into each of the 5 HTML files. `assets/` holds only optional shared images/SVG.

**Rationale:** Eliminates base-path CSS resolution bugs entirely; any file can be emailed/opened standalone; matches reference deck.

**Alternatives Rejected:** Shared `assets/workshop.css` — one more relative-path failure mode under Pages; marginal DRY benefit.

**Consequences:** (+) Bulletproof paths, portable. (−) Style edits touch multiple files (acceptable; the print materials share a *smaller* CSS block, the deck owns the big one).

---

### Decision 5: Live Council runs in Leo's terminal; the deck only *cues* it

| Attribute | Value |
|-----------|-------|
| **Status** | Accepted · **Date** 2026-06-02 |

**Context:** R: students watch a real agent give an opinion; but no secrets/backends in a static page.

**Choice:** Copy the 4 `conselheiro-*` agents from `mirante-dos-dados-br/.claude/agents/` into `workshops_ai_engineering/.claude/agents/` so Leo can invoke them via Claude Code from this repo. The deck has a **demo-cue slide** with the exact prompt to paste.

**Rationale:** Real, credible opinions; reproducible; zero attack surface in the page; agents are reusable across all 4 workshops.

**Alternatives Rejected:**
1. Embed an LLM call in the page — needs an API key in client = security risk (explicitly out of scope).
2. Pre-recorded video of an agent — less authentic; loses the "ask anything" magic.

**Consequences:** (+) Authentic, safe, reusable. (−) Depends on Leo's local Claude Code session being ready (noted in cheat-sheet setup).

---

## File Manifest

| # | File | Action | Purpose | Agent | Dependencies |
|---|------|--------|---------|-------|--------------|
| 1 | `workshop-01/presentation/index.html` | Create | The 27-slide bilingual deck (engine + content) | (general/visual-explainer) | None |
| 2 | `workshop-01/materials/business-model-canvas.html` | Create | 9-block BMC: worked (Pequeno Comércio) + blank, print CSS | (general) | None |
| 3 | `workshop-01/materials/facilitator-cheatsheet.html` | Create | Minute-by-minute script + say-cues + Council prompts + URLs | (general) | 1 |
| 4 | `workshop-01/materials/student-handout.html` | Create | Pre-read + setup checklist (send before 06 Jun) | (general) | None |
| 5 | `index.html` | Create | Root **series** landing hub → links into `workshop-01/` (relative) | (general) | 1, 2, 3, 4 |
| 6 | `.nojekyll` | Create | Tell Pages to serve files verbatim | (general) | None |
| 7 | `.claude/agents/conselheiro-financas.md` | Copy | Enable live Council demo from this repo | (general) | None |
| 8 | `.claude/agents/conselheiro-administrador.md` | Copy | " | (general) | None |
| 9 | `.claude/agents/conselheiro-eng-software.md` | Copy | " | (general) | None |
| 10 | `.claude/agents/conselheira-design.md` | Copy | " | (general) | None |
| 11 | `README.md` | Modify | Repo intro → what this is, live URL, how to run W1 | (general) | 5 |
| 12 | `assets/` (logos/SVG) | Create (as needed) | Any shared imagery the deck references | (general) | None |

**Total Files:** ~12 (4 agent copies are mechanical)

---

## Agent Assignment Rationale

> No dedicated front-end agent exists in the AgentSpec roster; this is hand-authored HTML/CSS/JS. The `agentspec:visual-explainer` skill (`generate-slides`) is the closest stylistic reference.

| Agent | Files | Why |
|-------|-------|-----|
| (general / build-agent) | 1–12 | Vanilla HTML/CSS/JS authoring + git/`gh` deploy — no specialist needed |
| `visual-explainer` skill (reference only) | 1 | Mine its slide-deck CSS conventions for parity; not invoked as an agent |

---

## Deck Slide Inventory (the heart of the build)

27 slides → satisfies "≥18 slides across 9 blocks". Component = the reference CSS class to use.

| # | Block | Slide | Component (class) | Key content |
|---|-------|-------|-------------------|-------------|
| 1 | Intro | **Title** | `slide--title` | "Construindo com IA / Building with AI" · pills: 4 Sábados, 2 alunos, Layer Zero, R$0 · byline Leonardo |
| 2 | Intro | How to use this deck | `cardgrid--quad` | Navigate · Language · Theme · Practice |
| 3 | Mindset | **Module: Layer Zero** | `slide--module` | "00 · A virada mental / The mental shift" |
| 4 | Mindset | The thesis | `slide--split` | Left: old world (typing). Right: new world (thinking/directing). AI = stage crew, you = director |
| 5 | Mindset | Leonardo's arc | `steps` | credit business → Paraguay → finance professor → Itaipu → Big Data → Tech Lead. "If a finance guy can…" |
| 6 | Showcase | **Module: The proof** | `slide--module` | "01 · O que já está no ar / What's already shipped" |
| 7 | Showcase | Six things, one builder | `cardgrid` | 6 app cards (logo/emoji + one-liner) — the overview |
| 8 | Showcase | Caixa Forte | `slide--split` + `slide__kpis` | Pain → WHY → stack → KPIs (90 tests, Council 9.0, R$0) · live URL |
| 9 | Showcase | Foco Contábil | `slide--split` | Multi-tenant accounting; Pix+Boleto; Lei 6.404; WCAG 2.2 AA |
| 10 | Showcase | Amazing School | `slide--split` | Teacher-first English; Whisper 15-probe pronunciation; MIT, $0 |
| 11 | Showcase | Mirante dos Dados | `slide__kpis` | 2.53bi rows · US$70 lifetime · 7 papers · home of the Council |
| 12 | Showcase | CareConnect · CV · Presentations | `cardgrid` | The rest of the portfolio + "even this deck is the method" |
| 13 | Council | **Module: The Council** | `slide--module` | "02 · Quem opina / Who weighs in" |
| 14 | Council | The four councillors | `cardgrid--quad` | Finanças 💰 · Administração 🎯 · Eng 🛠️ · Design 🎨 + their question |
| 15 | Council | **Live demo** | `slide--lab` (`lab-badge`) | The exact prompt to paste; what students will watch happen |
| 16 | Ideas | **Module: 20 ideas (and yours)** | `slide--module` | "03 · O banco de ideias / The idea bank" |
| 17 | Ideas | Finance · Accounting | `dtable` + score pills | Ideas 1–5 with 💰🎯🛠️🎨 |
| 18 | Ideas | Education · Productivity | `dtable` | Ideas 6–10 |
| 19 | Ideas | Local · Brazilian pain | `dtable` | Ideas 11–15 |
| 20 | Ideas | Wide-open · Surprising | `dtable` + `callout` | Ideas 16–20 + "Wildcards welcome / sua dor vale mais" |
| 21 | Decide | How we decide | `slide--split` + `callout` | The 4-lens scoring rubric; run finalists past the Council |
| 22 | Decide | Three to spotlight | `cardgrid` | Pequeno Comércio · Memória Viva · Simulador de Financiamento |
| 23 | BMC | Business Model Canvas | custom 9-block mini-grid | The 9 blocks explained → "we fill it now" (points to printable) |
| 24 | Roadmap | The 4-week map | custom **Gantt grid** | Visual bars across W1–W4 with milestones |
| 25 | Roadmap | What we ship each week | `steps` | W1 idea+BMC · W2 spec+skeleton · W3 core · W4 ship+pitch |
| 26 | Close | Homework before W2 | `cardgrid` | GitHub account · install checklist · pick your pain point |
| 27 | Close | Now it's your turn | `slide--bleed` | CTA + the live URL + "Generated with Claude" byline |

---

## Code Patterns

### Pattern 1: No-flash head + engine bootstrap (port from reference)

```html
<html lang="pt-BR" data-theme="dark" data-lang="pt">
<script>
  /* restore saved theme/lang before paint */
  (function(){try{var t=localStorage.getItem('ws-theme'),l=localStorage.getItem('ws-lang');
    if(t)document.documentElement.setAttribute('data-theme',t);
    if(l){document.documentElement.setAttribute('data-lang',l);
          document.documentElement.setAttribute('lang',l==='pt'?'pt-BR':'en');}
  }catch(e){}})();
</script>
```

`SlideEngine` (IntersectionObserver @ threshold .5, progress bar, dots, counter, keyboard ← →/Home/End, touch swipe), `applyLang()`, `applyTheme()` — ported verbatim from `professional-presentations/course/index.html` lines ~2271–2326, with `dqx-` keys renamed to `ws-`. **Default lang = `pt`** (Brazilian students), default theme = `dark`.

### Pattern 2: A bilingual slide (authoring rule)

```html
<section class="slide">
  <p class="slide__label reveal" data-en="The proof" data-pt="A prova">A prova</p>
  <h2 class="slide__heading reveal"
      data-en="Six things, one builder"
      data-pt="Seis coisas, um construtor">Seis coisas, um construtor</h2>
  <!-- EVERY visible string MUST carry both data-en and data-pt -->
</section>
```

### Pattern 3: Lava blob background (COULD — reduced-motion safe)

```css
.lava{position:fixed;inset:0;z-index:-2;overflow:hidden;pointer-events:none}
.lava i{position:absolute;border-radius:50%;filter:blur(60px);opacity:.20;
  background:radial-gradient(circle,var(--accent-soft),transparent 70%)}
.lava i:nth-child(1){width:46vw;height:46vw;top:-8vw;left:-6vw;animation:drift 26s ease-in-out infinite}
.lava i:nth-child(2){width:38vw;height:38vw;bottom:-10vw;right:-6vw;animation:drift 34s ease-in-out infinite reverse}
@keyframes drift{50%{transform:translate(6vw,4vw) scale(1.12)}}
@media (prefers-reduced-motion:reduce){.lava i{animation:none}}
```
```html
<div class="lava" aria-hidden="true"><i></i><i></i></div>
```

### Pattern 4: Visual Gantt grid (slide 24)

```css
.gantt{display:grid;grid-template-columns:160px repeat(4,1fr);gap:6px;margin-top:24px}
.gantt__hd{font-family:var(--font-mono);font-size:12px;color:var(--text-muted);text-align:center}
.gantt__row{display:contents}
.gantt__task{font-size:14px;color:var(--text-dim);align-self:center}
.gantt__bar{height:22px;border-radius:6px;background:var(--surface);position:relative}
.gantt__bar.fill{background:linear-gradient(90deg,var(--accent),var(--accent-soft))}
/* span helpers: .c1..c4 set grid-column to place the bar under the right week(s) */
```

### Pattern 5: Business Model Canvas grid (print landscape)

```css
.bmc{display:grid;gap:8px;
  grid-template-columns:repeat(5,1fr);
  grid-template-areas:
    "kp ka vp cr cs"
    "kp kr vp ch cs"
    "co co co rs rs";min-height:78vh}
.bmc__cell{border:1.5px solid var(--border);border-radius:10px;padding:12px}
.bmc__cell--kp{grid-area:kp} /* …ka,vp,cr,cs,kr,ch,co,rs */
.bmc__h{font-family:var(--font-mono);font-size:11px;text-transform:uppercase;
  letter-spacing:1px;color:var(--accent);font-weight:700}
@media print{@page{size:A4 landscape;margin:8mm} .noprint{display:none}
  body{background:#fff;color:#000}}
.pagebreak{break-before:page}
```
Two `.bmc` instances: first **filled** (Pequeno Comércio, both languages via `data-*` — print shows current lang), second **blank** after `.pagebreak`.

### Pattern 6: GitHub Pages deploy (one-time + updates)

```bash
# at repo root
printf '' > .nojekyll
git add -A && git commit -m "feat: Workshop 1 facilitation kit (deck, BMC, cheat-sheet, handout)"
git push origin main
# enable Pages from main / root (one-time)
gh api -X POST repos/leonardochalhoub/workshops_ai_engineering/pages \
  -f 'source[branch]=main' -f 'source[path]=/'  || \
gh api -X PUT  repos/leonardochalhoub/workshops_ai_engineering/pages \
  -f 'source[branch]=main' -f 'source[path]=/'
# verify
gh api repos/leonardochalhoub/workshops_ai_engineering/pages --jq '.html_url,.status'
```

### Pattern 7: Copy Council agents into this repo

```bash
mkdir -p .claude/agents
cp /home/leochalhoub/mirante-dos-dados-br/.claude/agents/conselheir{o,a}-*.md .claude/agents/
```
Live-demo prompt (goes on slide 15 + cheat-sheet):
```text
Use the conselheiro-administrador agent to give a candid opinion on this app idea:
"<chosen idea>" — is there a real WHY? Can it make money? One paragraph, be direct.
```

---

## Data Flow

```text
1. Student/Leo opens https://leonardochalhoub.github.io/workshops_ai_engineering/
   │  (landing hub, default PT-BR + dark)
   ▼
2. Clicks "Apresentação" → presentation/index.html (relative link)
   │
   ▼
3. SlideEngine renders; IntersectionObserver adds .visible → reveal animations
   │  ← → / scroll / dots navigate; progress bar + counter update
   ▼
4. Toggle EN/PT → applyLang swaps innerHTML on all [data-en]; persists ws-lang
   Toggle Dark/Light → applyTheme sets data-theme; persists ws-theme
   ▼
5. Slide 15 cue → Leo runs Council prompt in screen-shared terminal → agent opinion streams
   ▼
6. Slide 23 cue → open materials/business-model-canvas.html → fill live / print
   ▼
7. Close (slide 27) → assign homework from student-handout.html
```

---

## Integration Points

| External System | Integration Type | Authentication |
|-----------------|-----------------|----------------|
| Google Fonts CDN | `<link>` (Inter, JetBrains Mono) | None; system-font fallback if offline |
| GitHub Pages | Static hosting from `main` root | `gh` CLI (already authed as `leonardochalhoub`) |
| Claude Code + Council agents | Local terminal (screen-shared), not in page | Leo's local session |
| Live app URLs (Caixa Forte, etc.) | Outbound `<a target="_blank">` | None |

---

## Testing Strategy

| Test Type | Scope | Files | Tools | Goal |
|-----------|-------|-------|-------|------|
| Manual / AT | AT-001…AT-009 from DEFINE | all | Browser (Chrome/Firefox) | All pass |
| Bilingual lint | 0 nodes missing `data-pt` where `data-en` exists (and vice-versa) | 1–5 | `grep`/quick script | 0 mismatches |
| Path lint | No absolute `/…` asset/link paths (Pages base-path safety) | 1–5 | `grep -n 'href="/\|src="/'` | 0 hits |
| Print check | BMC 1 page landscape; cheat-sheet & handout portrait, no clipping | 2,3,4 | Browser print preview → PDF | clean |
| Link check | Landing → all 4 artifacts resolve on live URL | 5 | open live URL | 0 broken |
| A11y spot | Body contrast AA in both themes; focus-visible; reduced-motion | 1–5 | manual + DevTools | pass |

### Bilingual lint snippet (Build runs this)
```bash
for f in presentation/index.html materials/*.html index.html; do
  en=$(grep -o 'data-en=' "$f" | wc -l); pt=$(grep -o 'data-pt=' "$f" | wc -l)
  echo "$f  EN=$en PT=$pt $([ "$en" = "$pt" ] && echo OK || echo MISMATCH)"
done
```

---

## Error Handling

| Error Type | Handling Strategy | Retry? |
|------------|-------------------|--------|
| Google Fonts unreachable | CSS font stack falls back to `system-ui`/monospace | No |
| `localStorage` blocked/private mode | `try/catch` around get/set; deck still works, just no persistence | No |
| `prefers-reduced-motion` | Disable reveal + lava animations; content fully visible | n/a |
| Absolute path used by mistake | Caught by path-lint before deploy | Fix |
| Pages base-path 404 on asset | All paths relative (D3/D4); lint guards | Fix |
| Council agent not found in repo | Pattern 7 copies them; cheat-sheet lists the `cp` as setup | n/a |

---

## Configuration

| Config Key | Type | Default | Description |
|------------|------|---------|-------------|
| `data-lang` (html attr) | string | `pt` | Initial language (Brazilian students) |
| `data-theme` (html attr) | string | `dark` | Initial theme |
| `localStorage ws-lang` | string | — | Persisted language choice |
| `localStorage ws-theme` | string | — | Persisted theme choice |
| Themes available | enum | `dark`, `light` | NTT theme dropped (not needed here) |
| Slide count | int | 27 | Deck length |

---

## Security Considerations

- **No secrets in any page** — static HTML only; the Council demo runs in Leo's terminal, never in the browser (D5). No API keys client-side.
- **External links** use `rel="noopener noreferrer"` on `target="_blank"`.
- **No user input / no backend** — nothing to inject; the BMC is filled by hand or print.
- **Public repo content** — deck shows only already-public portfolio facts and live URLs; no client/employer-confidential data.

---

## Observability

| Aspect | Implementation |
|--------|----------------|
| Logging | None (static site) |
| Metrics | Optional: GitHub Pages traffic (repo Insights) — no in-page analytics (privacy, zero-cost) |
| Tracing | n/a |

---

## Revision History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | 2026-06-02 | design-agent | Initial design from DEFINE_AI_WORKSHOPS.md — 5 ADRs, 27-slide inventory, 7 code patterns, Pages deploy, live-Council kit |

---

## Next Step

**Ready for:** `/build .claude/sdd/features/DESIGN_AI_WORKSHOPS.md`
