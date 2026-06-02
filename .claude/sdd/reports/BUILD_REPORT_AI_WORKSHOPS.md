# BUILD REPORT: AI Workshops — Workshop 1 Facilitation Kit

| Attribute | Value |
|-----------|-------|
| **Feature** | AI_WORKSHOPS |
| **Date** | 2026-06-02 |
| **Phase** | 3 — Build |
| **DESIGN** | [DESIGN_AI_WORKSHOPS.md](../features/DESIGN_AI_WORKSHOPS.md) |
| **Status** | ✅ Shipped & live |
| **Live URL** | https://leonardochalhoub.github.io/workshops_ai_engineering/ |

---

## What was built

| # | File | Result |
|---|------|--------|
| 1 | `workshop-01/presentation/index.html` | ✅ 27-slide bilingual deck — carousel, dark/light, lava blob, ported `SlideEngine` |
| 2 | `workshop-01/materials/business-model-canvas.html` | ✅ Worked example (Pequeno Comércio) + blank, A4-landscape print CSS |
| 3 | `workshop-01/materials/facilitator-cheatsheet.html` | ✅ Minute-by-minute (0:00–4:30), say-cues, live Council prompts, A4 portrait |
| 4 | `workshop-01/materials/student-handout.html` | ✅ Pre-read + setup checklist + **embedded blank BMC** (added per user request) |
| 5 | `index.html` | ✅ Series landing hub (4 workshop cards + W1 materials) |
| 6 | `.nojekyll` | ✅ Created |
| 7–10 | `.claude/agents/conselheir*.md` | ✅ 4 Council agents copied from Mirante |
| 11 | `README.md` | ✅ Rewritten — series intro, live URL, Council usage |

## Verification (against DEFINE acceptance tests + success criteria)

| Check | Result |
|-------|--------|
| Bilingual lint — `data-en` == `data-pt` count per file | ✅ 31/31, 233/233, 49/49, 53/53, 39/39 |
| Absolute-path lint (Pages base-path safety) | ✅ 0 absolute paths |
| HTML parses clean (all 5 files) | ✅ |
| Deck slide count ≥ 18 | ✅ 27 slides across all 9 content blocks |
| 20 ideas + 4-lens Council scores | ✅ present (slides 17–20) |
| 6 portfolio apps + CV shown | ✅ (slides 7–12) |
| Live-Council demo cue slide | ✅ (slide 15) + cheat-sheet prompts |
| GitHub Pages live — all routes 200 | ✅ landing + deck + BMC + cheat-sheet + handout |
| Default lang PT-BR, theme dark, persisted | ✅ |
| Reduced-motion safe (reveal + lava) | ✅ `@media (prefers-reduced-motion:reduce)` |

## Deviations from DESIGN

- **Student handout now embeds a blank Business Model Canvas** (user request mid-build) — added as section ⑤ on its own print page, in addition to the standalone BMC file.
- **Folder layout** moved to `workshop-01/` (user request) so workshops 02–04 get parallel folders later. DESIGN updated to match.

## Not done (out of scope / future)

- Workshops 02–04 materials (planned; landing shows them as "Soon").
- The app the students build (decided live in W1).
- Print-to-PDF export is via the browser's native print (buttons wired); no separate PDF build.

## Next step

`/ship .claude/sdd/features/DESIGN_AI_WORKSHOPS.md` — archive + capture lessons learned, when Workshop 1 has run.
