# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

---

## [0.0.6] — 2026-06-06

### Changed
- **Pivot to company-document-primary** — make-doc-skill v4 is now the **Company Document Generator**. Primary deliverables are formal Word/PDF board materials, IR / CFO proposals, internal approval documents, bilingual JP/ZH documents, and 1920x1080 HTML/PDF decks. Value proposition reframed from "theme application" to a **Brain -> Router -> Canvas intelligence pipeline**: infer the real deliverable, rebuild structure, lock numbers and language, then render and verify real DOCX/PDF/HTML.
- **HTML demoted to optional output mode** — the 18-template / 28-strategy / 16-component / glassmorphism HTML machinery is preserved as the secondary "HTML output mode" for one-pagers, diagram docs, and visual explainers, not the headline.
- **Brain redefined** as editor + domain analyst (Codex Intelligence Layer); **Router** as document architect mapping deliverable type to output family + section schema + renderer; **Canvas** as renderer/typesetter that makes no editorial decisions.
- README (EN/JA/ZH) and `docs/README.md` index rewritten to lead with company documents; install instructions, badges, and EIP lineage preserved.
- Version badge updated to 0.0.6.

### Added
- **New 8-step company-document Full-Mode pipeline** — `01_company_tokens` → `02_document_brief` → `03_source_normalized` → `04_codex_sparring` → `05_composition_plan` → `06_layout_review` → `07_render_log` → `08_pdf_qa`, each writing a reviewable intermediate file with a user checkpoint.
- **Output families** — formal DOCX/PDF (primary), split JP/ZH documents, 1920x1080 HTML/PDF decks, and the optional HTML visual document.
- **Company token model** — per-company brand/language/docx/slide tokens (JSON/YAML) consumed by Router; no hardcoded colors/fonts/sizes in templates.
- **Anchoring & prohibition rules for listed-company material** — numerical fidelity, material anchoring with `[DATA_GAP]`, source attribution with `[Supplemental]`, language lock, pyramid + MECE; sparring runs at M depth and above, anchoring at all depths including Quick Mode.
- **Quality gates** — DOCX/PDF render checks, 12pt body, chapter page breaks, TOC alignment, table overflow, diagram integrity, brand-color discipline, bilingual language residue, and numerical-fidelity verification (`pdfinfo` / `pdffonts`).

### Removed
- **All sensitive example data and personal paths** — removed real company names, tickers, brand hex colors, real board-proposal titles, personal file paths, and emails. Examples now use clearly-generic placeholders only: company "Acme Holdings, Inc.", ticker "0000", example red palette `#c0392b`, a generic "mid-term management plan" board topic, and default output folder `~/Downloads`.

## [0.0.5] — 2026-04-13

### Added
- **Quick Mode** — one-shot generation from YouTube URL, web URL, PDF, or plain text (no Q&A needed)
- **YouTube subtitle extraction** via `yt-dlp` with auto-sub fallback to title+description
- **Auto content strategy classification** — 28-strategy auto-detection from input content
- **Auto-defaults** — language auto-detect, depth auto-size by content length, default CI palette
- **Post-generation upgrade path** — Quick Mode output can be upgraded to Full Mode
- **Mandatory print CSS rule** — `print-color-adjust:exact` enforced for all formats (single-page and slides)
- **Full file URL output** — always show `file:///absolute/path` after generation

### Changed
- Pipeline docs (PIPELINE.md) updated with Quick Mode section in EN/JA/ZH
- SKILL.md description updated to include Quick Mode triggers
- Version badge updated to 0.0.5

## [0.0.4] — 2026-04-13

### Added
- **Larger worked example** — expanded the bundled sample deck to exercise longer documents (purpose page, table of contents, executive summary, and appendices)

### Changed
- **Deeper sparring** — expanded from 2 rounds / 6 findings to 4 rounds / 17 findings
- **Larger composition** — composition table expanded to more sections (prior version archived to `_history/v1/`)
- Review checklist updated with v1→v2 feedback-resolution tracking

## [0.0.3] — 2026-04-12

### Added
- **18 visual templates** with Tailwind class-level skeleton rules: Dashboard, Versus, Timeline, Article, Steps, Report, Matrix, Profile, Flowchart, Scorecard, Pitch, Infographic, Comparison Table, FAQ, Slide, Iceberg, Funnel, Bridge
- **28 content strategies** with automatic template mapping, expert questioning chains (ja/zh/en), tone/avoid rules, and Brain Schema Overrides
- **S/M/L/XL depth control** — 4-level size system controlling analysis depth, section count, and visualization tier
- **6 depth visualization rules** — causal chains, confidence bars, contrast increments, information quality badges, trend direction, uncertainty sections — with 4-tier graduated Canvas instructions (S/M/L/XL)
- **Expert questioning mode** — domain-specific interrogation patterns for finance, tech, news, and general analysis
- **Brain → Router → Canvas architecture** — three-layer decoupled methodology from EIP Engine 1.0
- **Pipeline transparency** — insight reporting at each step
- **Content anchoring rules** — pyramid principle, MECE validation, content anchoring (no fabrication), language locking
- **Few-shot HTML references** — Executive Summary, Data Cards, Comparison Table as quality benchmarks
- **Universal design rules** — Grid alignment, glass morphism cards, font minimum sizes, micro-interactions, 12-item prohibition list
- **Full docs/ documentation system** (9 files, trilingual EN/JA/ZH)
- **Trilingual README** — English (main), Japanese (`i18n/ja/`), Chinese (`i18n/zh/`)

### Changed
- SKILL.md rewritten entirely in English
- README restructured — centered header, badges, narrative "Why" section, conversation-style usage examples
- License changed from MIT to **Apache License 2.0**
- Framework count expanded from 6 to 18 templates
- Pre-interview expanded from 7 to **8 questions** (added depth size)
- Review expanded from 2-layer 9-item to **3-layer 15-item** (added CI compliance audit)

## [0.0.2] — 2026-04-11

### Added
- **16:9 slide deck format** — 1280x720px fixed size, page numbers, CI accent bar, print-friendly
- **CI compliance audit** (Layer 3) — 6 mandatory checks before HTML generation
- **Color discipline rule** — strictly enforce CI palette, prohibit hues outside brand colors
- **Title confirmation flow** — provide 3-4 professional title candidates, avoid casual naming
- **Font and whitespace defaults** — body text minimum 16px, card padding max 24px

### Changed
- Pre-interview expanded from 6 to **7 questions** (added output format)
- Framework color references changed from hardcoded to CI-relative

## [0.0.1] — 2026-04-11

### Added
- Initial release of make-doc-skill
- **8-step pipeline**: project name → CI extraction → pre-interview → material organization → sparring → composition → review → HTML generation
- **CI auto-extraction** from websites, uploaded files, or verbal description
- **6 document frameworks**: system architecture, process/methodology, comparative analysis, concept explainer, project overview, decision summary
- **16 built-in HTML components**: Meta Pills, Hero Section, Summary Card, Flow Diagram, Section Header, Info Card, Highlight Box, Numbered Steps, Vertical Cycle, Badge Row, Divider, Two-Column Comparison, Small Command Grid, Data Chart (3 variants), Print Button, Return Flow Pill
- **Sparring mechanism** — 3-dimension pre-generation review
- **2-layer review** — structure check (4 items) + quality check (5 items)
- **Iteration mechanism** — version history management, restart from any step
- **Multilingual support** — ja/zh/en
- **Self-contained HTML output** — Tailwind CDN + Google Fonts + Lucide inline SVG
- **Print optimization** and auto-generated OG tags + SVG favicon
