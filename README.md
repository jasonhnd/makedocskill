<div align="center">

# make-doc-skill v4

### Company Document Generator

---

*Generate company-specific board materials, IR / CFO proposals, bilingual JP/ZH documents, and 16:9 decks — as real Word, PDF, and HTML.*

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](LICENSE)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-Skill-green.svg)](https://code.claude.com/docs/en/skills)
[![agentskill.sh](https://img.shields.io/badge/agentskill.sh-Published-yellow.svg)](https://agentskill.sh/@jasonhnd/makedocskill)
[![Version](https://img.shields.io/badge/version-0.0.6-purple.svg)](CHANGELOG.md)

Board materials · IR / CFO proposals · bilingual JP/ZH · formal Word/PDF · 1920x1080 decks.
Brain -> Router -> Canvas intelligence pipeline.

**This is not theme application. It infers the real deliverable, rebuilds structure, locks numbers and language, then renders and verifies real DOCX/PDF/HTML.**

[See it in action](#usage) · [Install](#installation) · [How it works](#architecture) · [Output families](#output-families)

**Other Languages:**

[日本語](i18n/ja/README.md) · [中文](i18n/zh/README.md)

</div>

---

## Why This Skill Exists

Most AI tools generate a company document the same way: drop text into a theme and call it done. You get a wall of bullet points with a brand color on the headings — but the numbers were never checked against the source, the Japanese is casual instead of board-level, the chapters do not page-break, and the exported PDF nobody actually opened is broken.

The problem is not generation speed. The problem is that **no editorial judgment happens before the file is exported**.

A CFO's board-document editor at a listed company does not open Word first. They read the source, identify whether it is really board material, IR material, or a CFO proposal, challenge the weak claims an auditor would attack, lock every figure to the source, fix the language, and only then lay it out. The document is the last mile, not the first.

make-doc-skill works the same way. It runs a **Brain -> Router -> Canvas** pipeline that separates judgment from rendering:

- **Brain** is the editor and domain analyst. It infers the real deliverable, rebuilds structure, runs three-dimension expert sparring (hypothesis challenge, blind-spot completion, perspective reconstruction), normalizes terminology, and fixes broken hierarchy and tone. This is the **Codex Intelligence Layer** — the execution engine behind every convincing board pack.
- **Router** is the document architect. It maps the deliverable type to an output family — formal DOCX, split bilingual JP/ZH files, a 16:9 deck, or HTML — then produces a section-by-section composition plan and chooses the renderer and template.
- **Canvas** is the renderer and typesetter. It applies company brand tokens and layout rules, renders DOCX/HTML, exports PDF, and runs QA. It makes **no** editorial decisions.

Tokens are the design memory. Brain judgment is the execution engine. **Depth comes from the sharpness of judgment, not the number of steps** — a board document is convincing because Brain read the material correctly and rebuilt it, not because Canvas applied a color theme.

The result: formal Word/PDF board materials and IR/CFO decks that read like a CFO's office produced them, with numbers that survive an audit. All from a single Claude Code skill.

---

## Architecture

```
┌──────────────────────────────────────────────────────────────┐
│                      make-doc-skill v4                       │
│                  Company Document Generator                  │
│                                                              │
│   ┌──────────┐     ┌──────────┐     ┌──────────────────┐    │
│   │  Brain    │────>│  Router  │────>│     Canvas       │    │
│   │          │     │          │     │                  │    │
│   │ Editor /  │     │ Document │     │ Renderer /       │    │
│   │ analyst   │     │ architect│     │ typesetter       │    │
│   │ Sparring  │     │ Output   │     │ DOCX / HTML      │    │
│   │ Number &  │     │ family + │     │ PDF export       │    │
│   │ lang lock │     │ schema   │     │ QA / fidelity    │    │
│   └──────────┘     └──────────┘     └──────────────────┘    │
│                                                              │
│   Source + tokens     Composition       Real DOCX/PDF/HTML  │
└──────────────────────────────────────────────────────────────┘
```

**Core Principle**: Depth comes from the sharpness of judgment, not the number of steps.

The three layers are decoupled by design. Even when Brain rewrites heavily, Canvas never dumps analytical prose into a document — Router forces the translation into document structure (chapters, tables, callouts, diagrams). Tokens are the design memory; Brain judgment is the execution engine.

---

## Two Modes — Quick Mode / Full Mode

| Mode | Trigger | Flow |
|------|---------|------|
| **Quick Mode** | Drop an existing Word/PDF/text and want a fast polished output, no project setup | Detect input -> extract -> infer real deliverable -> apply company tokens (or sensible default) -> Brain light pass -> render -> export PDF -> report path |
| **Full Mode** | Board/IR material, bilingual delivery, or "build the document properly" | 8-step audited pipeline with intermediate files and user checkpoints |

Quick Mode trades sparring depth for speed, but **still runs numerical-fidelity and language-lock checks and never fabricates**. After a Quick output, it offers an upgrade to Full Mode (keeps the normalized source, adds tokens, sparring, and review).

---

## Output Families

The primary deliverables are formal documents. HTML visual documents are an optional secondary mode.

| Family | Use Case | Output |
|--------|----------|--------|
| **Formal DOCX/PDF** *(primary)* | Board packs, internal approval documents, policy explanations, listed-company materials | A4, 12pt body, chapter page breaks, stable TOC, restrained tables, brand-accent headers, fixed SVG/PNG diagrams |
| **Split JP/ZH documents** | Separate-language delivery | One Japanese DOCX/PDF + one Chinese DOCX/PDF, parallel structure, language-specific fonts, no cross-language residue |
| **1920x1080 HTML/PDF deck** | CFO proposals, IR decks, operating briefings, large-screen review | 16:9 fixed viewport, `html { font-size: 20px }`, brand accent bar, conference-room readability, one HTML file + PDF export |
| **HTML visual document** *(optional)* | One-pager / diagram doc / visual explainer — not a formal company document | Self-contained single-page-scroll or 16:9 HTML using the v3 HTML machinery, company tokens applied instead of default blue |

---

## Depth Control (S / M / L / XL)

Depth controls how hard Brain analyzes and how rigorous QA is. It does **not** control whether numerical fidelity or language lock apply — those always apply.

| | S | M | L | XL |
|--|---|---|---|-----|
| **Use Case** | 1-page exec summary / memo | Standard proposal / explanation | Full board material / IR document | Comprehensive board pack + appendix |
| **Sections** | 3-5 | 5-8 | 8-12 | 12+ |
| **Brain depth** | Core conclusion + actions | + evidence evaluation | + explanatory framework + alternatives | + multi-perspective review + extreme test |
| **Sparring rounds** | 0-1 | 1-2 | 2-3 | 3+ |
| **Diagrams** | 0-1 | 1-2 | 2-4 | 4+ |
| **QA rigor** | Output exists + fonts + path | + TOC + pagination | + bilingual parity + diagram QA | full Quality Gates + visual contact sheet |
| **Deck slides (if 16:9)** | 3-6 | 6-10 | 10-15 | 15+ |

If the user does not specify a size, it is inferred from the deliverable: a memo is S, a CFO proposal is M-L, a full board material with appendix is L-XL.

---

## Installation

| Platform | Installation |
|----------|-------------|
| **Claude Code** | `cp SKILL.md ~/.claude/skills/make-doc-skill/SKILL.md` |
| **Gemini CLI / Antigravity** | `npx skills add jasonhnd/makedocskill` |
| **OpenAI Codex CLI** | `npx skills add jasonhnd/makedocskill` |
| **Claude.ai** | Upload `SKILL.md` to Project Knowledge |
| **Cursor / VS Code Copilot** | `npx skills add jasonhnd/makedocskill` |
| **ChatGPT / Gemini Web** | Paste `SKILL.md` content into System Instructions |

### Quick Install

```bash
# One-liner
mkdir -p ~/.claude/skills/make-doc-skill && curl -sL https://raw.githubusercontent.com/jasonhnd/makedocskill/main/SKILL.md -o ~/.claude/skills/make-doc-skill/SKILL.md

# Or clone and copy
git clone https://github.com/jasonhnd/makedocskill.git
cp makedocskill/SKILL.md ~/.claude/skills/make-doc-skill/SKILL.md
```

> Formal DOCX/PDF output requires document tooling for DOCX/PDF rendering. `yt-dlp` is only needed if extracting from a YouTube source in the optional HTML mode.

### Verify

```
# In Claude Code
/make-doc-skill
```

---

## Usage

### Refine a Branded Word Document

```
You: @board_draft.docx Polish this into a formal board material in our corporate red, Japanese
Skill: [Reads DOCX, infers deliverable = board_material, normalizes source, marks [DATA_GAP]]
Skill: [Builds company tokens: primary #c0392b, Hiragino Sans body, removes accidental blue]
Skill: Sparring found 3 weak points an auditor would raise: ...
Skill: [Renders A4 DOCX, 12pt body, chapter page breaks, exports PDF, runs PDF QA]
Skill: Done. ~/Downloads/board_draft_精修版.docx + .pdf
```

### Split Bilingual JP/ZH

```
You: @midterm_plan.md Make a Japanese board version and a Chinese version, split files
Skill: [Locks output languages, keeps quotes in source language, aligns section structure]
Skill: [Renders one Japanese DOCX/PDF and one Chinese DOCX/PDF, parallel TOC and tables]
Skill: Done. _日本語版 and _中文版 in ~/Downloads, language residue checked.
```

### CFO 16:9 Proposal Deck

```
You: Turn this mid-term management plan into a CFO 16:9 deck for the board (Size L)
Skill: [Infers IR/CFO deck, builds composition plan, 12 slides, brand accent bar]
Skill: [Renders 1920x1080 HTML, exports PDF, verifies page count and 16:9 size]
Skill: Done. ~/Downloads/CFO_Proposal.html + .pdf
```

---

## Codex Intelligence Layer

Design tokens alone are not enough. They define colors, fonts, sizes, and spacing — but they do not decide whether a document is convincing, readable, or suitable for a listed-company context. This layer **is the Brain** in the pipeline.

It runs every time:

- **Infer the real deliverable**, not only the literal file type. A "Word/PDF" request may be board material, IR material, a CFO proposal, a business explanation, or a public-facing deck.
- **Read the existing document before designing.** Extract not just text but weak points: broken hierarchy, bad line breaks, crowded tables, unstable diagrams, wrong alignment, poor page rhythm, mismatched tone.
- **Convert vague brand direction into concrete tokens.** "Do not use blue; use our corporate colors" means defining the real system (e.g. red/gray) and removing accidental blue from headings, tables, links, diagrams, and charts.
- **Make editorial decisions.** Rewrite headings, split overloaded paragraphs, normalize terminology, tighten section order.
- **Verify the real output surface.** A DOCX is not done until the exported PDF is readable; a deck is not done until browser rendering and PDF export both look correct.
- **Preserve user file discipline.** Never overwrite source files. Final files go to the handoff folder (default `~/Downloads`).

In short: tokens are the design memory; Codex-style judgment is the execution engine. The skill should inspect, decide, rebuild, verify, and deliver.

---

## Sparring, Anchoring & Prohibition Rules

This is what makes the Codex Intelligence Layer reliable rather than "an LLM rewriting." Sparring runs at M depth and above; anchoring and prohibition rules run at all depths including Quick Mode.

### Three-dimension expert questioning (Step 4)

| Dimension | Goal | Forces |
|-----------|------|--------|
| **Hypothesis challenge** | Test the core claim | Is the main claim defensible? Primary data or assertion? Strongest counter-argument a board member or auditor would raise? |
| **Blind-spot completion** | Fill missing dimensions | What is missing — downside, risk, dilution, regulatory, tax, precedent, timeline? |
| **Perspective reconstruction** | Offer a better framing | Would risk-first / comparison-first / timeline-first framing serve this audience better? |

### Anchoring rules (non-negotiable for listed-company material)

- **Numerical fidelity** — use figures exactly as in the source. Never round, never invent. Currency, units, and fiscal periods stay exact.
- **Material anchoring** — only state what the source supports. Mark missing data `[DATA_GAP]`.
- **Source attribution** — mark supplemental/background knowledge as `[Supplemental]`.
- **Language lock** — once the output language is set, the whole chain obeys it; quotations keep their original language.
- **Pyramid + MECE** — conclusion first, then supporting arguments, then data; sections mutually exclusive and collectively exhaustive.

### Prohibited output

- No vague filler used to avoid stating a conclusion.
- No judgment avoidance — if the material supports a recommendation, state it.
- No fabricated figures, citations, or legal/tax/accounting conclusions; unverified statements must be marked draft/assumption.
- No phenomenon-listing without causal explanation.
- No surface-level paraphrasing of a weak source — rebuild it.

---

## Pipeline — Full Mode 8 Steps

Each step writes a reviewable file into the project folder and ends with a checkpoint: **proceed / redo this step / skip with defaults / jump to render**. Skipping applies sensible company-token defaults. Iteration archives prior files to `_history/v[N]/`; the project root always holds the latest version.

| Step | Action | Output |
|------|--------|--------|
| **1** | Company tokens | `01_company_tokens.md` (brand / language / docx / slide tokens) |
| **2** | Document brief | `02_document_brief.md` (deliverable type, audience, language mode, depth, outputs, delivery folder) |
| **3** | Source normalized | `03_source_normalized.md` (Word/PDF/text -> structured MD/YAML; quotes preserved; `[DATA_GAP]` marked) |
| **4** | Codex sparring | `04_codex_sparring.md` (3-dimension questioning, weak-point list, editorial decisions) |
| **5** | Composition plan | `05_composition_plan.md` (section blueprint, renderer + template choice) |
| **6** | Layout review | `06_layout_review.md` (pre-render structure / quality / brand gate) |
| **7** | Render log | `07_render_log.md` (DOCX/HTML generated, decisions logged, PDF exported) |
| **8** | PDF QA | `08_pdf_qa.md` (pdfinfo / pdffonts + visual checks, gate results, final paths) |

**Pipeline transparency**: every decision is recorded in its step file (traceable); the user can pause, review, or modify at any step (auditable); Brain explains key choices in-line (explainable); iteration is cheap (low-cost rollback).

---

## Token Model

Every company gets a token file before rendering. Use JSON or YAML. Do not hardcode colors, fonts, sizes, or spacing into templates.

```yaml
company:
  legal_name: "Acme Holdings, Inc."   # example only — replace with the target company
  ticker: "0000"
  market: "Tokyo Stock Exchange Growth"
  brand_name: "Acme"

brand:
  primary: "#c0392b"        # example brand palette — replace with the company's real tokens
  primary_dark: "#922b21"
  text: "#242424"
  background: "#ffffff"
  border: "#d9d9d9"

language:
  ja_font: "Hiragino Sans"
  zh_font: "PingFang SC"
  latin_font: "Aptos"

docx:
  page_size: "A4"
  body_pt: 12
  line_spacing: 1.18
  chapter_page_break: true

slides:
  canvas_px: [1920, 1080]
  base_font_px: 20
```

Rules:

- Use company primary color as the only functional accent unless tokens define additional semantic colors.
- Avoid blue/green/orange functional colors when the brand does not call for them.
- Use hierarchy through weight, spacing, and muted text, not uncontrolled font sizes.

---

## Quality Gates

Concrete checks behind Step 6 (layout review) and Step 8 (PDF QA), run before final delivery:

- Output exists in the requested folder; DOCX opens without repair warnings.
- PDF exports from final DOCX/HTML source; fonts are readable and language-appropriate.
- Body text is 12pt for formal Word documents unless overridden; chapters start on new pages when required.
- TOC alignment is correct; tables do not overflow page margins; diagrams are not broken or made from unstable Word shape arrows.
- No unintended blue/green/orange appears when the company brand is red/gray.
- Chinese/Japanese split files contain the correct language.
- For HTML decks, browser screenshot and PDF export both show non-overflowing 16:9 slides.
- **Numerical fidelity holds**: every figure, unit, currency, and fiscal period matches the source; gaps are `[DATA_GAP]`; unverified legal/tax statements are marked draft.

```bash
pdfinfo "/path/to/output.pdf"
pdffonts "/path/to/output.pdf"
```

---

## Handoff Convention

Unless the user specifies another destination:

- Final files go to `~/Downloads` (macOS/Linux) or `%USERPROFILE%\Downloads` (Windows).
- Keep output filenames close to the source filename plus a clear suffix such as `_精修版`, `_日本語版`, `_中文版`, or `_CFO Proposal`.
- Do not overwrite source files unless explicitly requested.

---

## Optional HTML Output Mode

When the requested deliverable is an HTML visual one-pager or diagram doc — **not** a formal Word/PDF document — the skill uses preserved v3 HTML machinery: 18 visual templates, 28 content strategies, 16 HTML components, and HTML depth-visualization rules. It produces a self-contained single-page-scroll or 16:9 HTML document and applies company tokens instead of the default blue CI.

This machinery is a capable secondary output. The company-document pipeline above is the primary path.

| Reference (HTML mode) | Content |
|-----------------------|---------|
| [TEMPLATES.md](docs/TEMPLATES.md) | 18 HTML visual templates |
| [CONTENT_STRATEGIES.md](docs/CONTENT_STRATEGIES.md) | 28 content strategies + expert questioning chains |
| [DEPTH_VISUALIZATION.md](docs/DEPTH_VISUALIZATION.md) | HTML depth-visualization rules |

---

## Documentation

| Document | Content |
|----------|---------|
| [PIPELINE.md](docs/PIPELINE.md) | Company-document 8-step Full-Mode pipeline (01_company_tokens -> 08_pdf_qa) |
| [PROMPT_ENGINEERING.md](docs/PROMPT_ENGINEERING.md) | Brain / Router / Canvas role design + prompt meta-principles |
| [DESIGN_RULES.md](docs/DESIGN_RULES.md) | DOCX / deck / diagram / token / brand-color hard constraints |
| [SIZE_DEPTH_MATRIX.md](docs/SIZE_DEPTH_MATRIX.md) | Company-document S/M/L/XL depth control |
| [ARCHITECTURE.md](docs/ARCHITECTURE.md) | Brain -> Router -> Canvas three-layer architecture |
| [TEMPLATES.md](docs/TEMPLATES.md) | 18 templates (HTML output mode) |
| [CONTENT_STRATEGIES.md](docs/CONTENT_STRATEGIES.md) | 28 strategies (HTML output mode) |
| [DEPTH_VISUALIZATION.md](docs/DEPTH_VISUALIZATION.md) | Depth visualization rules (HTML output mode) |

---

## Heritage

This skill is derived from the [EIP (Explain In Picture)](https://github.com/jasonhnd/eip) project — an AI-driven visual document generation web application (Next.js 16 + React 19 + Tailwind CSS 4) that accumulated the Engine 1.0 methodology: three-stage pipeline, visual template skeletons, content strategies, a classification engine, depth visualization rules, and S/M/L/XL size control.

make-doc-skill v4 carries that Brain -> Router -> Canvas intelligence forward and re-points it at company documents — formal Word/PDF board materials, IR/CFO proposals, and bilingual JP/ZH deliverables — while preserving the EIP-derived HTML machinery as an optional output mode.

---

## License

[Apache License 2.0](LICENSE)
