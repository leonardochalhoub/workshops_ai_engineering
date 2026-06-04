<div align="center">

# AI Workshops · Workshops de IA

### Building with AI — from Layer Zero to a shipped app

A **4-Thursday workshop series** (Jun 2026): a finance professor, two students, and AI as the stage crew — going from *"I have an idea"* to *"it's live on the internet,"* at near-zero cost.

[**▸ Open the live site**](https://leonardochalhoub.github.io/workshops_ai_engineering/) · bilingual **PT-BR / EN** · dark · light

</div>

---

## What's here

| Workshop | Date | Theme | Status |
|---|---|---|---|
| **01** | Thu 04 Jun 2026 | **Show & decide** — portfolio, the Council, 20 ideas → choose one + draft the BMC | ✅ Built |
| 02 | Thu 11 Jun 2026 | Define & design — spec, screens, repo + Supabase + Vercel skeleton | ⏳ Planned |
| 03 | Thu 18 Jun 2026 | Build the core — the flow works end to end, deployed preview | ⏳ Planned |
| 04 | Thu 25 Jun 2026 | Ship & pitch — public URL, students pitch, Council's final verdict | ⏳ Planned |

## Workshop 1 materials

- **[Presentation](workshop-01/presentation/index.html)** — 27-slide bilingual deck (scroll-snap carousel, dark/light toggle, lava accent).
- **[Business Model Canvas](workshop-01/materials/business-model-canvas.html)** — worked example (*Pequeno Comércio*) + a blank, printable (A4 landscape).
- **[Facilitator cheat-sheet](workshop-01/materials/facilitator-cheatsheet.html)** — minute-by-minute run of show, say-cues, live Council prompts.
- **[Student handout](workshop-01/materials/student-handout.html)** — pre-read + setup checklist + a blank canvas. Send before W1.

## The Council

Four AI advisors copied from [Mirante dos Dados](https://github.com/leonardochalhoub/mirante-dos-dados-br) into `.claude/agents/` — they give candid, on-screen opinions on the app ideas during Workshop 1:

| Agent | Lens |
|---|---|
| `conselheiro-administrador` | 🎯 The WHY + money (Sinek / Harari / Carrey) |
| `conselheiro-financas` | 💰 Viability + numbers (PhD Finance) |
| `conselheiro-eng-software` | 🛠️ Buildable by Week 4 (post-doc Software Eng.) |
| `conselheira-design` | 🎨 Usable + beautiful (PhD InfoViz/HCI) |

Run a live take from the repo:

```bash
# in Claude Code, from this repo
Use the conselheiro-administrador agent to give a candid opinion on this app idea:
"<idea>" — real WHY? Can it make money? One paragraph, be direct.
```

## How it's built

Vanilla, self-contained **HTML + CSS + JS** — no framework, no build step. Each page carries `data-en` / `data-pt` on every string for instant bilingual toggle; theme + language persist in `localStorage`. Hosted on **GitHub Pages** (`main` root, `.nojekyll`). The deck engine and aesthetic are ported from [`professional-presentations`](https://professional-presentations.vercel.app).

The series was planned through the AgentSpec SDD workflow — see [`.claude/sdd/features/`](.claude/sdd/features/) for the Brainstorm → Define → Design documents.

---

<div align="center">

Series by **Leonardo Chalhoub** · built with Claude · 2026

</div>
