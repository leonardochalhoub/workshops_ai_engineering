# BRAINSTORM — AI Engineering Workshops (Layer Zero → Shipped App)

> **Phase 0 · AgentSpec SDD** · Generated 2026-06-02 · Author: Leonardo Chalhoub
> Next phase: `/define .claude/sdd/features/BRAINSTORM_AI_WORKSHOPS.md`

---

## 1. The one-sentence pitch

A **4-Saturday workshop series** where 2 students with some coding basics live the *mental shift* of building **with** AI — starting from Leonardo's shipped portfolio (Caixa Forte, Foco Contábil, Amazing School, CareConnect, Mirante, CV) as proof, choosing one real app idea with help from the **Mirante Council of agents**, and shipping it to a live URL by Week 4 — all on free tooling.

---

## 2. Who this is for

| | |
|---|---|
| **Instructor** | Leonardo Chalhoub — AI Data Engineering Tech Lead @ NTT DATA (Bradesco). Ex-undergraduate professor of **Financial Mathematics & Budget Management**. Path: family credit business → systems technician in Paraguay → finance & management → professor → Contracts Manager @ Itaipu Binacional → Big Data (CPFL, GSK, AB-InBev, Unilever) → Tech Lead. MSc Finance (UFRGS), completing BSc Software Engineering (Estácio). Trilingual. Author of *Papéis* (novel). |
| **Students** | 2 motivated learners with **some coding basics** (have seen code, can follow + edit + run commands with guidance). Currently studying **Layer Zero** of Leonardo's AI Data Engineering course — the *mental change* about using AI. |
| **Mode** | **Online**, screen-share (Meet/Zoom). 3–5h per session. |

---

## 3. The North Star

> **"From finance professor to AI builder — and now it's your turn."**

The series proves a thesis the students are already studying in *Layer Zero*: the bottleneck is no longer *can you code* — it's *can you think, decide, and direct*. By Week 4 each student has helped ship a real, deployed app. The portfolio is the evidence; the Council is the mentor; the chosen app is the proof.

---

## 4. The 4-week arc (Saturdays, June 2026)

| Week | Date | Theme | Outcome |
|---|---|---|---|
| **W1** | **Sat 06 Jun 2026** | **SHOW & DECIDE** — Layer Zero made real | Portfolio shown · 20 ideas explored · Council weighs in · **1 app idea chosen** + Business Model Canvas drafted |
| **W2** | **Sat 13 Jun 2026** | **DEFINE & DESIGN** — from idea to spec | Requirements (`/define`) · screens sketched · stack decided · repo + Supabase + Vercel skeleton live |
| **W3** | **Sat 20 Jun 2026** | **BUILD** — the core feature works | Core user flow implemented with AI pair-building · data persists · deployed preview |
| **W4** | **Sat 27 Jun 2026** | **SHIP & PITCH** — live + presented | App on a public URL · students pitch it · Council final verdict · retro + next steps |

> Stack is **decided live in Workshop 1** based on the chosen idea and student comfort. Default candidate: the proven **Next.js + Supabase + Groq + Vercel** zero-cost stack (same as the shipped apps). Lighter fallback: plain HTML+JS or Streamlit for a non-framework path.

---

## 5. Gantt (text profile)

```
                          JUN 2026
ID  TASK                       W1(06) W2(13) W3(20) W4(27)   Owner
─────────────────────────────────────────────────────────────────
A   Layer-Zero mindset demo    ████                          Leo
B   Portfolio showcase         ████                          Leo
C   Idea exploration (20)      ████                          All
D   Council opinions           ████░                         Agents
E   Pick the idea + BMC        ░███                          All
F   /define requirements             ████                    All
G   UX sketch + screens              ████                    Students
H   Stack + repo + deploy skel       ███░                    Leo+Stu
I   /design architecture             ░██                     Leo
J   Build core feature                     ████              Students
K   Data model + persistence              ████░             Leo+Stu
L   AI features (Groq/LLM)                 ░███              Students
M   Polish + accessibility                      ███          Students
N   Ship to public URL                          ████         All
O   Pitch + Council verdict                     ░███         All
P   Retro + roadmap                             ░░██         All
─────────────────────────────────────────────────────────────────
Legend: ████ primary work   ░ spillover/buffer
Milestones:  ◆W1 Idea chosen   ◆W2 Skeleton live   ◆W3 Core works   ◆W4 Shipped
```

A polished visual Gantt is rendered inside the presentation deck (slide "The 4-week map").

---

## 6. The portfolio to SHOW (Workshop 1 evidence)

Each is **live, shipped, zero-to-low cost** — the point is "a finance person built these *with* AI."

| Project | One-liner | Stack | Proof point |
|---|---|---|---|
| **Caixa Forte** | Personal finance for Brazilians — clarity without spreadsheets, friction, or subscription | Next.js 16 · React 19 · Supabase · Groq (Llama 3.3 + Whisper) | v0.5.0 · 90 tests · Council 9.0/10 · R$0 forever |
| **Foco Contábil** | Multi-tenant platform for Brazilian accounting offices — cadastro to caixa | Next.js 16 · Supabase RLS · Asaas (Pix+Boleto) | NFS-e, DRE & balanço with legal basis (Lei 6.404) · WCAG 2.2 AA |
| **Amazing School** | Teacher-first English platform — "the AI is the stage crew" | Next.js 16 · Supabase · Groq (llama-3.3-70b + Whisper) | v1.0.0 · 15-probe Whisper pronunciation scoring · MIT · $0 |
| **CareConnect** | Management platform for Home Care agencies — 3 profiles in one codebase | Next.js 16 · React 19 · Tailwind v4 · Supabase | Shift schedule, payroll, family portal, Asaas billing |
| **Mirante dos Dados** | Open lakehouse for Brazilian public microdata | Spark · Delta Lake · DABs · Unity Catalog · React · LaTeX | 2.53bi-row table · 7 working papers · **US$70 lifetime** · home of the Council |
| **Professional Presentations** | Courses engineered like software | Single-file HTML decks · bilingual · 3 themes | DQX Masterclass: 10 modules + hands-on, ~128 slides |
| **CV / Career** | The narrative: finance → AI builder | LaTeX · Tectonic · ATS-optimized | 50+ active certs · published in Brazilian Review of Finance |

---

## 7. The Mirante Council (the "agents that give opinions")

Four agents from `mirante-dos-dados-br/.claude/agents/` evaluate every candidate idea, each through a distinct lens. In Workshop 1 they give **pre-opinions**; live, Leonardo can invoke them on the chosen idea.

| Agent | Persona | Lens | The question it asks |
|---|---|---|---|
| 💰 **Conselheiro de Finanças** | PhD Finance, sold a data-science boutique to a French consultancy | Viability, numbers, causal rigor | *"Does this survive a stress-test on real data? Is the unit economics real?"* |
| 🎯 **Conselheiro de Administração** | Professor titular, lens of Sinek (WHY-HOW-WHAT), Harari, Carrey | Purpose & money | *"What's the WHY? Can this make money? Is it real change or cargo cult?"* |
| 🛠️ **Conselheiro de Eng. de Software** | Post-doc, DOS-1995 → cloud-2026, Tech Lead at a global consultancy | Buildability | *"What stack? Is it testable, reproducible, shippable by Week 4?"* |
| 🎨 **Conselheira de Design** | PhD InfoViz/HCI, lens of Tufte, Norman, Bostock | Usability & beauty | *"Is it usable, accessible, legible? Would a human enjoy it?"* |

---

## 8. The 20 app ideas (pre-seeded — open to more)

Scoring is the Council's **quick pre-take**: 💰 Finance · 🎯 Admin/WHY · 🛠️ Build · 🎨 Design (each ●●●●● out of 5). "Free?" = buildable on free tiers. All are buildable by 2 students in 3 weeks if scoped to one core flow.

### 🏦 Finance · Accounting · Fintech

| # | Idea | Pitch | 💰 | 🎯 | 🛠️ | 🎨 | Free? |
|---|---|---|---|---|---|---|---|
| 1 | **MEI Descomplicado** | Assistant for Brazilian micro-entrepreneurs: DAS reminders, revenue-limit tracker, 1-tap invoice | ●●●●● | ●●●●● | ●●●● | ●●●● | ✅ |
| 2 | **Racha Pix** | Group-expense splitter, Pix-native, OCR the receipt → who owes what | ●●●● | ●●●● | ●●●● | ●●●●● | ✅ |
| 3 | **Simulador de Financiamento** | Price vs SAC loan simulator with plain-PT AI advice *(leverages Leo's Financial Math teaching)* | ●●●●● | ●●●● | ●●●●● | ●●●● | ✅ |
| 4 | **Orçamento de Festa** | Event/wedding budget planner with vendor & payment tracking | ●●● | ●●●● | ●●●● | ●●●● | ✅ |
| 5 | **Investidor Iniciante** | Beginner portfolio tracker that *explains* every move in plain Portuguese | ●●●● | ●●●● | ●●●● | ●●●● | ✅ |

### 📚 Education · Productivity

| # | Idea | Pitch | 💰 | 🎯 | 🛠️ | 🎨 | Free? |
|---|---|---|---|---|---|---|---|
| 6 | **Flashcards IA** | Drop a PDF/notes → AI generates spaced-repetition cards (Whisper for audio notes) | ●●●● | ●●●●● | ●●●● | ●●●● | ✅ |
| 7 | **Redação ENEM Coach** | AI essay grader on the 5 ENEM competencies — massive BR market | ●●●● | ●●●●● | ●●●● | ●●●● | ✅ |
| 8 | **Plano de Aula** | Lesson-plan generator for teachers *(ties to Amazing School)* | ●●● | ●●●● | ●●●●● | ●●●● | ✅ |
| 9 | **Clube da Matemática** | Gamified math practice with AI hints *(Leo already has the brand)* | ●●● | ●●●● | ●●●● | ●●●●● | ✅ |
| 10 | **TCC Assistant** | Structures an undergrad thesis: outline, citations, ABNT formatting | ●●● | ●●●● | ●●●● | ●●● | ✅ |

### 🇧🇷 Local · Brazilian real-world pain

| # | Idea | Pitch | 💰 | 🎯 | 🛠️ | 🎨 | Free? |
|---|---|---|---|---|---|---|---|
| 11 | **Pequeno Comércio** | WhatsApp-order manager for small shops: catalog + Pix + order list | ●●●●● | ●●●●● | ●●●● | ●●●● | ✅ |
| 12 | **Cuidador Solo** | Micro-CareConnect for *independent* caregivers: schedule + shift notes | ●●●● | ●●●● | ●●●● | ●●●● | ✅ |
| 13 | **Síndico Fácil** | Condo management: shared expenses, notices, simple voting | ●●●● | ●●●● | ●●●● | ●●●● | ✅ |
| 14 | **Preço da Feira** | Crowdsourced neighborhood grocery-price comparison | ●●● | ●●●● | ●●● | ●●●● | ✅ |
| 15 | **Brechó do Bairro** | Local donation & second-hand marketplace with photo listing | ●●● | ●●●● | ●●●● | ●●●● | ✅ |

### ✨ Wide-open · Surprising

| # | Idea | Pitch | 💰 | 🎯 | 🛠️ | 🎨 | Free? |
|---|---|---|---|---|---|---|---|
| 16 | **Memória Viva** | Interview your grandparent → Whisper + LLM turns voice into a written memoir *(ties to Leo the author)* | ●●● | ●●●●● | ●●●● | ●●●●● | ✅ |
| 17 | **Diário com IA** | Voice journaling → mood insights over time (Whisper + Llama) | ●●● | ●●●● | ●●●● | ●●●● | ✅ |
| 18 | **Tem na Geladeira?** | Photo your fridge → AI suggests recipes from what you have | ●●● | ●●●● | ●●●● | ●●●●● | ✅ |
| 19 | **Histórias para Dormir** | Personalized kids' bedtime stories with the child's name (PT-BR) | ●●● | ●●●● | ●●●● | ●●●●● | ✅ |
| 20 | **Olhos** | Describe-my-surroundings camera app for low-vision users (vision model) | ●● | ●●●●● | ●●● | ●●●● | ✅ |

> **Wildcards welcome.** Workshop 1 ends with an open call: a student's *own* pain point beats any of these. The 20 exist to prime the pump, not to cap it.

**Instructor's three to spotlight** (high WHY × buildable × emotionally resonant): **#1 MEI Descomplicado** (clear money + huge market), **#11 Pequeno Comércio** (real pain Leo's family business lived), **#16 Memória Viva** (the surprise that makes the room go quiet).

---

## 9. Business Model Canvas (worked example + blank)

Filled live in Workshop 1 once the idea is chosen. A **worked example** (MEI Descomplicado) and a **blank printable** are provided as `materials/business-model-canvas.html`. The 9 blocks:

1. **Customer Segments** · 2. **Value Propositions** · 3. **Channels** · 4. **Customer Relationships** · 5. **Revenue Streams** · 6. **Key Resources** · 7. **Key Activities** · 8. **Key Partnerships** · 9. **Cost Structure**

The Conselheiro de Administração drives blocks 1–5 (the WHY and the money); the Conselheiro de Eng. de Software grounds blocks 6–9 (what it actually takes to build & run on free tiers).

---

## 10. Workshop 1 — minute-by-minute facilitator script (3.5h core, 5h with breaks)

| Time | Block | What happens | Material |
|---|---|---|---|
| 0:00–0:15 | **Welcome & North Star** | "From finance professor to AI builder." Set the thesis from Layer Zero: thinking > typing. | Deck §Intro |
| 0:15–0:35 | **Layer Zero, made real** | The mental shift: AI as stage crew, you as director. Live: one prompt → working thing. | Deck §Mindset + live demo |
| 0:35–1:20 | **The portfolio tour** | Walk the 6 shipped apps. For each: the pain, the WHY, the stack, the cost. "All built by one finance guy + AI." | Deck §Showcase (open the live URLs) |
| 1:20–1:35 | ☕ **Break** | | |
| 1:35–1:55 | **Meet the Council** | Introduce the 4 agents. Show how an agent gives a real opinion. | Deck §Council + live agent run |
| 1:55–2:40 | **The idea storm** | Walk the 20 ideas as a menu. Students react, react, react. Then open the floor: *your* pain point. | Deck §20 Ideas |
| 2:40–2:55 | ☕ **Break** | | |
| 2:55–3:25 | **Council weighs in & we decide** | Run top 2–3 candidates past the Council lenses. Score together. **Pick one.** | Deck §Decide + scoring |
| 3:25–4:05 | **Draft the Business Model Canvas** | Fill the 9 blocks live for the chosen idea. | `materials/business-model-canvas.html` |
| 4:05–4:30 | **The plan & homework** | Show the 4-week Gantt. Assign W2 pre-work (accounts to create). Close. | Deck §Roadmap + student handout |

> Online tip: keep the deck on screen-share, the live apps in tabs, and a terminal ready to invoke a Council agent so the opinion feels alive, not scripted.

---

## 11. Approaches explored (and the call)

### Approach A — "Show, then decide, then BMC" ⭐ Recommended
**Why:** Matches the request exactly. Evidence first (portfolio) lowers the students' "I can't build" barrier, *then* ideation lands because they believe it's possible, *then* the BMC turns excitement into a plan. The Council adds credibility and a repeatable decision tool.
**Pros:** High motivation curve; ends W1 with a concrete artifact (chosen idea + BMC); de-risks W2–W4.
**Cons:** Lots to fit in one session — mitigated by the strict minute-by-minute script and breaks.

### Approach B — "Build something tiny in W1"
**Why not:** Tempting, but building before deciding wastes the "wow" of the portfolio and risks choosing an idea just because it was easy to start. Save the build energy for W2–W4 when the idea is real. *(Deferred, not discarded — a 10-min "hello AI" micro-demo is folded into the Layer-Zero block instead.)*

### Approach C — "Pure open brainstorm, no pre-seeded ideas"
**Why not:** With only 3–5h and 2 students, a blank page stalls. The 20 ideas + open call gets the best of both: momentum *and* authentic discovery. *(This is why we pre-seed 20 but explicitly invite wildcards.)*

---

## 12. YAGNI — what we deliberately cut from Workshop 1

| Cut | Why |
|---|---|
| Choosing the tech stack in detail | Decided live; depends on the chosen idea. Don't pre-bikeshed. |
| Writing any code in W1 | W1 is decide-day. Code starts W2. |
| All 4 Council agents on all 20 ideas | Only top 2–3 finalists get the full Council treatment — the rest get one-line pre-takes. |
| Full BMC financial modeling | A *drafted* canvas is enough for W1; numbers firm up across W2–W4. |
| Recording/LMS/grading infrastructure | 2 students, screen-share. Keep it human. |

---

## 13. Deliverables — this session vs. later phases

**Produced now (Phase 0):**

| Artifact | Path | Purpose |
|---|---|---|
| This plan | `.claude/sdd/features/BRAINSTORM_AI_WORKSHOPS.md` | The master course design (feeds `/define`) |

**Planned for Phase 3 (`/build`)** — *not yet created; specced in `/define` → `/design` first:*

| Artifact | Path (target) | Purpose |
|---|---|---|
| **Presentation** | `presentation/index.html` | Beautiful bilingual carousel deck (lava bg, dark/light toggle) to *lead* Workshop 1 |
| **Business Model Canvas** | `materials/business-model-canvas.html` | Printable; worked example + blank to fill live |
| **Facilitator cheat-sheet** | `materials/facilitator-cheatsheet.html` | Printable one-pager: what to say, when |
| **Student handout** | `materials/student-handout.html` | Pre-read + setup checklist to send before 06 Jun |

---

## 14. Draft requirements (for `/define`)

- **R1** The series runs 4 consecutive Saturdays from 2026-06-06, online, 3–5h each.
- **R2** Workshop 1 must end with (a) one chosen app idea and (b) a drafted Business Model Canvas.
- **R3** All workshop materials are **bilingual (PT-BR / EN)** with an instant toggle.
- **R4** The presentation must replicate the `professional-presentations` aesthetic: scroll-snap carousel, dark/light theme toggle, Databricks-Lava accent, reveal animations, self-contained single HTML file.
- **R5** The chosen app must be buildable on **free tiers** and **shipped to a public URL by Workshop 4**.
- **R6** The Mirante Council (4 agents) provides idea evaluation in Workshop 1.
- **R7** Students have *some coding basics*; pacing assumes guided edit/run, not from-scratch authoring.

---

## 15. Open questions to resolve in `/define`

1. Which exact idea wins (locked at end of W1)?
2. Final stack (Next.js+Supabase+Groq vs. lighter path)?
3. Do both students build the *same* app together, or one each?
4. Public URL target: Vercel project name?
5. Any LGPD/data concern if the app handles real user data in W4?

---

*Quality gate: ✅ 7 discovery questions asked · ✅ sample/grounding via real portfolio + Council · ✅ 3 approaches explored · ✅ YAGNI applied · ✅ user confirmed direction (bilingual, 20 ideas, decide-stack-live, online) · ✅ draft requirements included.*
