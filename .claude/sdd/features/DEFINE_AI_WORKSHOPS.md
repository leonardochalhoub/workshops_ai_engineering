# DEFINE: AI Engineering Workshops — Workshop 1 Facilitation Material

> A bilingual, self-contained presentation + facilitation kit that lets Leonardo lead Workshop 1 (06 Jun 2026), showcase his shipped portfolio, run the Mirante Council over 20 app ideas, and close with one chosen idea + a drafted Business Model Canvas.

## Metadata

| Attribute | Value |
|-----------|-------|
| **Feature** | AI_WORKSHOPS |
| **Date** | 2026-06-02 |
| **Author** | Leonardo Chalhoub |
| **Status** | Ready for Design |
| **Clarity Score** | 15/15 |

---

## Problem Statement

Leonardo wants to transfer the *Layer Zero* mindset ("thinking & directing beats typing") to 2 students with some coding basics — but he has no teaching material that (a) **proves** the thesis with his real shipped portfolio, (b) **drives a decision** to one app idea using the Mirante Council, and (c) does it **bilingually and beautifully** in a single 3–5h online session. Without a polished, self-contained kit, the first workshop risks being an unstructured demo that ends with enthusiasm but no concrete artifact.

> **Scope anchor:** This feature is the **Workshop 1 facilitation material**, not the app the students will build in Weeks 2–4. The app is a *workshop outcome* chosen live and is explicitly out of scope here.

---

## Target Users

| User | Role | Pain Point |
|------|------|------------|
| **Leonardo** | Instructor / facilitator | Needs a deck he can *lead* from (not read), with live-demo cues, Council prompts, and a minute-by-minute script — bilingual so he can switch register on the fly. |
| **Student A & B** | Learners, *some coding basics*, studying Layer Zero | Believe "I can't really build". Need evidence it's possible, a menu of ideas so they aren't staring at a blank page, and a tangible plan they leave with. |
| **The Mirante Council** | 4 advisor agents (Finance, Admin, Eng, Design) | Must appear *credibly* in the material so their opinions feel like real mentorship, not decoration. |

---

## Goals

| Priority | Goal |
|----------|------|
| **MUST** | A self-contained `presentation/index.html` deck that visually matches the `professional-presentations` aesthetic (scroll-snap carousel, dark/light toggle, Databricks-Lava accent, reveal animations). |
| **MUST** | Every text node bilingual **PT-BR / EN** with an instant top-bar toggle (the `data-en`/`data-pt` innerHTML-swap mechanism). |
| **MUST** | Deck content covers: North Star → Layer-Zero mindset → portfolio showcase (6 apps + CV) → Council intro → 20 ideas → decide → BMC → 4-week Gantt/roadmap → homework. |
| **MUST** | A printable **Business Model Canvas** (`materials/business-model-canvas.html`): one worked example (**#11 Pequeno Comércio**) + one blank, both A-page printable. |
| **MUST** | A printable **facilitator cheat-sheet** (`materials/facilitator-cheatsheet.html`): the minute-by-minute script, what-to-say cues, Council prompts. |
| **MUST** | **Publish to GitHub Pages** — a repo-root landing `index.html` links to the deck + materials; deployed at a public `github.io` URL the students can open. |
| **MUST** | A **live Council demo** flow: a deck cue + exact terminal prompts so Leo can ask a Council agent on screen and students watch the opinion stream in real time. |
| **SHOULD** | A **student handout** (`materials/student-handout.html`): pre-read + account/setup checklist to send before 06 Jun. |
| **SHOULD** | The 4-week Gantt rendered as a clean visual inside the deck (not just text). |
| **COULD** | Subtle animated "lava" background blob (CSS-only, `prefers-reduced-motion` safe) for extra polish. |
| **COULD** | Print-to-PDF stylesheet so cheat-sheet/BMC export cleanly. |

---

## Success Criteria

Measurable outcomes:

- [ ] Deck is **1 self-contained HTML file**, opens offline with **0 external JS deps** (Google Fonts link allowed), renders in Chrome/Edge/Firefox.
- [ ] **100%** of visible deck copy has both `data-en` and `data-pt`; toggling changes every string with **0** leftover-language nodes.
- [ ] Theme toggle switches **dark ⇄ light** with persisted choice (localStorage), **0** unreadable contrast states (WCAG AA on body text).
- [ ] Deck contains **≥ 18 slides** spanning all 9 content blocks listed in Goals.
- [ ] All **20 app ideas** present with their 4-lens Council pre-scores; **6 portfolio apps + CV** each shown with one-liner + stack + proof point.
- [ ] BMC renders all **9 blocks**; the worked example (**Pequeno Comércio**) is fully filled; the blank prints on **1 page** without clipping.
- [ ] Cheat-sheet fits the full Workshop 1 timeline (0:00–4:30) on a printable sheet; total facilitator run time sums to **3.5h core / 5h with breaks**.
- [ ] Facilitator can run the entire Workshop 1 from these files with **no other tooling** except a browser, the live app URLs, and a terminal for Council demos.
- [ ] Material is **live on GitHub Pages**: the public URL loads the landing page; deck + all materials reachable from it; **0** broken links/assets when served from the `github.io` base path.
- [ ] Deck includes a **live-Council demo slide** with the exact prompt(s) to run, so the on-screen agent demo is repeatable.

---

## Acceptance Tests

| ID | Scenario | Given | When | Then |
|----|----------|-------|------|------|
| AT-001 | Carousel navigation | Deck open on slide 1 | Press → / scroll / click a dot | Advances one slide with reveal animation; progress bar + counter update |
| AT-002 | Language toggle | Deck on any slide in EN | Click **PT-BR** | Every visible string swaps to Portuguese instantly; choice persists on reload |
| AT-003 | Theme toggle | Deck in dark theme | Click **Light** | Palette switches to light, lava accent preserved, body text stays AA-legible; persists |
| AT-004 | Portfolio showcase | On the showcase slides | Facilitator reads them | All 6 apps + CV appear with one-liner, stack, proof point; live URLs clickable |
| AT-005 | 20 ideas + Council | On the ideas slides | Reviewed | 20 ideas grouped in 4 flavors, each with 💰🎯🛠️🎨 pre-scores; "wildcards welcome" present |
| AT-006 | BMC worked example | Open `business-model-canvas.html` | Print preview | 9 blocks filled for MEI Descomplicado; fits 1 page; blank variant also 1 page |
| AT-007 | Cheat-sheet completeness | Open `facilitator-cheatsheet.html` | Print preview | Full 0:00–4:30 script present with say-cues; prints legibly |
| AT-008 | Offline / self-contained | No network (fonts cached) | Open deck | Renders and is fully navigable; no broken layout |
| AT-009 | Reduced motion | OS `prefers-reduced-motion: reduce` | Open deck | Reveal + lava animations disabled; content fully visible |

---

## Out of Scope

- **The app the students build (Weeks 2–4).** Idea, stack, and code are decided live in Workshop 1 — not authored here.
- **Workshop 2–4 materials.** Only Workshop 1's kit is built now (later workshops get their own SDD pass).
- **Recording, LMS, grading, attendance.** 2 students, screen-share — kept human.
- **Live/interactive BMC editing in-browser.** BMC is printable static (worked example + blank); filled by hand or in a doc during the session.
- **Translating the underlying app READMEs.** Only the deck/material copy is bilingual.
- **A custom domain / CDN.** Plain `github.io` Pages URL is enough; no DNS work.
- **Embedding a live agent runtime in the page.** The Council demo runs in Leo's terminal (screen-shared); the page only *cues* it — no API keys or backend in the deck.
- **A real animated WebGL lava sim.** "Lava" = the Databricks-Lava palette + an optional lightweight CSS blob, nothing GPU-heavy.

---

## Constraints

| Type | Constraint | Impact |
|------|------------|--------|
| Technical | Single self-contained HTML per artifact; vanilla HTML+CSS+JS (no build step, no framework) | Mirrors `professional-presentations`; portable, opens anywhere, easy for students to inspect |
| Hosting | **GitHub Pages** from this repo — static only; links must be **relative** so they resolve under the `/<repo>/` base path; fonts via CDN allowed | Drives the repo-root landing `index.html`; a `.nojekyll` file avoids Jekyll processing |
| Technical | Bilingual via `data-en`/`data-pt` innerHTML swap; theme/lang persisted in localStorage | Reuse the proven engine from the DQX deck rather than inventing one |
| Style | Must visually echo `professional-presentations` (Lava accent, dark/light, scroll-snap, reveal) | Design phase reuses the existing CSS design-system vocabulary |
| Timeline | Usable for the **06 Jun 2026** session; pre-read sendable a few days before | Build must finish with buffer; handout is the earliest-needed piece |
| Resource | Free tooling only; no paid assets; icons/emoji or inline SVG | No licensing risk; consistent with the zero-cost portfolio story |
| Mode | Online screen-share | Deck optimized for 16:9 shared screen; legibility at projection scale |

---

## Technical Context

| Aspect | Value | Notes |
|--------|-------|-------|
| **Deployment Location** | `presentation/` (deck) + `materials/` (BMC, cheat-sheet, handout) + `assets/` (any shared SVG/img) under `workshops_ai_engineering/` | Already scaffolded in Phase 0 |
| **KB Domains** | None (this is a static front-end artifact, not a data/cloud feature) | Design pulls patterns from the existing `professional-presentations/course/index.html` instead of a KB |
| **IaC Impact** | None | No infrastructure; files open in a browser |

**Reference implementation to mirror:** `/home/leochalhoub/professional-presentations/course/index.html` — its `SlideEngine`, theme/lang appliers, slide-type CSS (`.slide--title`, `.cardgrid`, `.agenda`, `.vpipe`, `.callout`, `.dtable`, `.slide__kpis`, `.slide--module`) are the building blocks.

---

## Assumptions

| ID | Assumption | If Wrong, Impact | Validated? |
|----|------------|------------------|------------|
| A-001 | Reusing the DQX deck's CSS/JS engine is acceptable (style consistency is desired) | Would need a fresh design system — large rework | [x] (user asked for this exact look) |
| A-002 | Deck is **published to GitHub Pages** (resolved) — links must be relative | Broken assets under base path if absolute paths used | [x] (resolved: GitHub Pages) |
| A-003 | Worked-BMC exemplar = **#11 Pequeno Comércio** (resolved; MEI dropped) | Swap the example idea — cheap text edit | [x] (resolved) |
| A-004 | Portfolio facts in BRAINSTORM §6 are current as of Jun 2026 | Minor copy edits to stats | [x] (read from live READMEs) |
| A-005 | Two students, online, ~3.5–5h available on 06 Jun | Re-time the cheat-sheet | [ ] |
| A-006 | **Live** Council run happens on screen (resolved: yes) — Leo asks, agent answers, students watch | Need exact prompts + setup notes in cheat-sheet & a deck cue slide | [x] (resolved: live demo) |
| A-007 | Repo has a GitHub remote (`leonardochalhoub/workshops_ai_engineering`, `gh` authed). Target URL: **https://leonardochalhoub.github.io/workshops_ai_engineering/** | Only need to enable Pages (source: `main` root) in repo settings | [x] (remote verified) |

---

## Clarity Score Breakdown

| Element | Score (0-3) | Notes |
|---------|-------------|-------|
| Problem | 3 | Specific: no lead-material for a bilingual, proof-driven, decision-closing Workshop 1 |
| Users | 3 | Leo + 2 named student personas + the Council, each with pain points |
| Goals | 3 | MUST/SHOULD/COULD across deck, BMC, cheat-sheet, handout |
| Success | 3 | Numeric + testable (slide counts, 100% bilingual, 1-page print, AA contrast, live URL) |
| Scope | 3 | Out-of-scope explicit; hosting (GitHub Pages), worked example, and live-Council all resolved |
| **Total** | **15/15** | Above the 12 threshold — ready for Design |

---

## Open Questions

All Phase-1 open questions are **resolved**:

1. ~~Local-only vs hosted?~~ → **Publish to GitHub Pages.** (A-002)
2. ~~MEI as worked BMC example?~~ → **No — use #11 Pequeno Comércio.** (A-003)
3. ~~Live Council run?~~ → **Yes — Leo asks on screen, agent answers, students watch.** (A-006)

Remaining to confirm during Design/Build (non-blocking):
- **(A-007)** Confirm the GitHub remote + Pages source (root vs `/docs`, branch). *(Default: deploy from `main` root with `.nojekyll`.)*

---

## Revision History

| Version | Date | Author | Changes |
|---------|------|--------|---------|
| 1.0 | 2026-06-02 | define-agent | Initial version from BRAINSTORM_AI_WORKSHOPS.md |
| 1.1 | 2026-06-02 | define-agent | Resolved open Qs: publish to GitHub Pages; worked BMC example → #11 Pequeno Comércio (MEI dropped); live Council demo on screen. Clarity 14→15. |

---

## Next Step

**Ready for:** `/design .claude/sdd/features/DEFINE_AI_WORKSHOPS.md`
