# Template Skeletons Reference

> **[HTML output mode — optional]** make-doc-skill's primary path is company document generation (Word/PDF/bilingual board materials; see `SKILL.md`). This file is the HTML/Tailwind template machinery — load it only when the requested deliverable is an HTML visual document or 16:9 HTML deck.

> Referenced by SKILL.md (HTML output mode). Contains complete Tailwind class-level skeleton rules for all 18 visual templates.

Each template has skeleton rules at the Tailwind class level. Strictly followed during HTML generation.

---

## 3.1 Dashboard — Bento-box KPI

**Use case**: Data-dense overviews, metric dashboards, project summaries.

**Skeleton Rules**:
```
<main> — max-w-6xl mx-auto px-5 py-10
  Hero — text-4xl md:text-5xl font-black mb-2
  Subtitle — text-lg text-[--c-muted] mb-10
  KPI Row — grid grid-cols-2 md:grid-cols-4 gap-4 mb-10
    KPI Card — rounded-xl p-6 border text-center
      Value — text-3xl font-bold text-[--c-accent]
      Label — text-sm text-[--c-muted]
      Delta — text-xs mt-2 (↑ green / ↓ red / → gray)
  Bento Grid — grid grid-cols-1 md:grid-cols-3 lg:grid-cols-4 gap-4 md:gap-6
    Card Small — col-span-1 rounded-xl p-6 bg-[--c-surface] border h-fit
    Card Medium — col-span-2 (same as above)
    Card Large — col-span-3 (same as above)
    Chart Area — col-span-2 md:col-span-3 (CSS bar chart / mini sparkline)
  Section Divider — my-12 border-t border-[--c-border]
  Footer — text-center text-sm text-[--c-dim] py-8
```

## 3.2 Versus — Comparative Analysis

**Use case**: A vs B, binary choices, policy comparison.

**Skeleton Rules**:
```
<main> — max-w-5xl mx-auto px-5 py-10
  Hero — text-center mb-12
    Title — text-4xl md:text-5xl font-black
    vs Badge — inline-block px-4 py-1 rounded-full bg-[--c-accent]/10 text-[--c-accent] font-bold text-lg my-4
  Split — grid grid-cols-1 md:grid-cols-2 gap-8
    Left Panel — rounded-2xl p-8 bg-[--c-accent]/5 border-2 border-[--c-accent]/20
      Label — text-2xl font-bold text-[--c-accent] mb-4
      Items — space-y-3
        Item — flex items-start gap-3
          Icon — lucide-check text-[--c-accent] (pros) / lucide-x text-[--c-muted] (cons)
          Text — text-lg
    Right Panel — rounded-2xl p-8 bg-[--c-accent-dark]/5 border-2 border-[--c-accent-dark]/20
      (same structure, using secondary color)
  Unified Table — col-span-2 mt-8 overflow-x-auto
    Table — w-full text-sm rounded-xl border
      Header — bg-[--c-surface]
      Rows — even:bg-[--c-surface]/50
  Verdict — mt-12 rounded-2xl p-8 bg-[--c-accent]/5 border-l-4 border-[--c-accent]
    Verdict Title — text-xl font-bold text-[--c-accent]
    Verdict Body — text-lg
```

## 3.3 Timeline — Chronological Axis

**Use case**: Development history, phase breakdown, roadmaps.

**Skeleton Rules**:
```
<main> — max-w-4xl mx-auto px-5 py-10
  Hero — text-center mb-16
  Timeline Container — relative pl-8 md:pl-0
    Center Line — absolute left-4 md:left-1/2 w-1 h-full bg-gradient-to-b from-[--c-accent] to-[--c-accent-dark]
    Event (odd) — relative mb-12 md:ml-[50%] md:pl-12
      Dot — absolute left-[-24px] md:left-[-24px] w-10 h-10 rounded-full bg-[--c-accent] text-white flex items-center justify-center text-sm font-bold
      Date Badge — inline-block px-3 py-1 rounded-full bg-[--c-accent]/10 text-[--c-accent] text-sm font-bold mb-2
      Card — rounded-xl p-6 bg-[--c-surface] border shadow-sm
        Title — text-xl font-bold
        Body — text-lg leading-relaxed
    Event (even) — relative mb-12 md:mr-[50%] md:pr-12 md:text-right
      (Mirror layout)
  Summary — mt-16 rounded-2xl p-8 bg-[--c-accent]/5 text-center
```

## 3.4 Article — Long-Form Reading

**Use case**: News analysis, opinion pieces, deep-dive explainers.

**Skeleton Rules**:
```
<main> — max-w-3xl mx-auto px-5 py-10
  Hero — mb-12
    Meta — text-sm text-[--c-muted] mb-4 (date / category)
    Title — text-4xl md:text-6xl font-black leading-tight
    Lead — text-xl text-[--c-sub] mt-6 leading-relaxed
  Article Body — space-y-6
    Paragraph — text-lg leading-relaxed text-[--c-body]
    Blockquote — border-l-4 border-[--c-accent] pl-6 text-xl italic text-[--c-sub]
    Figure — my-8 flex md:flex-row gap-8
      Image — rounded-xl (or CSS chart)
      Caption — text-sm text-[--c-muted]
    Subheading — text-2xl font-bold mt-12 mb-4
    Callout — rounded-xl p-6 bg-[--c-accent]/5 border border-[--c-accent]/20
  Footnotes — mt-16 border-t pt-8
    Note — text-sm text-[--c-muted]
```

## 3.5 Steps — Numbered Steps

**Use case**: Tutorials, procedure guides, implementation guides.

**Skeleton Rules**:
```
<main> — max-w-3xl mx-auto px-5 py-10
  Hero — text-center mb-12
  Prerequisites — rounded-xl p-6 bg-[--c-surface] border mb-12
    Title — text-lg font-bold mb-3
    List — grid grid-cols-1 md:grid-cols-2 gap-2
  Steps — space-y-0
    Step — relative pl-16
      Circle — absolute left-0 w-10 h-10 rounded-full bg-[--c-accent] text-white flex items-center justify-center font-bold text-lg
      Connector — absolute left-5 top-10 border-l-2 border-dashed border-[--c-accent]/30 h-8
      Content — pb-8
        Title — text-xl font-bold mb-2
        Body — text-lg leading-relaxed
        Code — bg-gray-900 text-green-400 rounded-lg p-4 text-sm font-mono overflow-x-auto
        Tip — mt-4 rounded-lg p-4 bg-[--c-accent]/5 border-l-4 border-[--c-accent]
  Result — mt-8 rounded-2xl p-8 bg-[--c-accent]/5 border-2 border-[--c-accent]/20
    Title — text-xl font-bold text-[--c-accent]
```

## 3.6 Report — Structured Report

**Use case**: Research reports, financial analysis, market research.

**Skeleton Rules**:
```
<main> — max-w-4xl mx-auto px-5 py-10
  Cover — mb-16
    Title — text-4xl md:text-5xl font-black
    Subtitle — text-xl text-[--c-sub] mt-4
    Meta Bar — flex gap-6 mt-6 text-sm text-[--c-muted]
  Executive Summary — bg-[--c-accent]/5 border-l-4 border-[--c-accent] rounded-r-lg p-6 mb-12
    Label — text-sm font-bold text-[--c-accent] uppercase tracking-wider mb-2
    Content — text-lg leading-relaxed
  TOC — mb-12 rounded-xl p-6 bg-[--c-surface] border
    Items — space-y-2 text-lg
  Numbered Section — mb-16
    Section Number — text-sm font-bold text-[--c-accent] uppercase tracking-wider
    Section Title — text-2xl font-bold mt-1 mb-6
    Body — space-y-4 text-lg leading-relaxed
    Sidebar Callout — float-right w-48 ml-6 mb-4 p-4 rounded-xl bg-[--c-surface] border
      Value — text-3xl font-black text-[--c-accent] sticky top-4
      Label — text-sm text-[--c-muted]
    Data Table — w-full text-sm rounded-xl border overflow-x-auto
  Recommendations — mt-16 rounded-2xl p-8 bg-[--c-accent]/5
    Title — text-2xl font-bold mb-6
    Items — space-y-4
      Item — flex items-start gap-4
        Number — w-8 h-8 rounded-full bg-[--c-accent] text-white flex items-center justify-center font-bold flex-shrink-0
        Text — text-lg
```

## 3.7 Matrix — Evaluation Matrix

**Use case**: Multi-dimensional evaluation, vendor comparison, decision matrix.

**Skeleton Rules**:
```
<main> — max-w-5xl mx-auto px-5 py-10
  Hero — text-center mb-12
  Matrix Table — overflow-x-auto rounded-xl border
    Table — w-full
      Header Row — bg-[--c-surface]
        Dimension Headers — text-sm font-bold text-[--c-text] p-4
        Weight Badge — text-xs text-[--c-muted]
      Score Rows —
        Option Name — font-bold text-lg p-4
        Score Cells — p-4 text-center
          Score Badge — inline-block px-3 py-1 rounded-full text-sm font-bold
            High (8-10) — bg-[--c-accent]/20 text-[--c-accent]
            Mid (5-7) — bg-[--c-accent]/10 text-[--c-accent]/70
            Low (1-4) — bg-[--c-muted]/10 text-[--c-muted]
  Weighted Ranking — mt-12 space-y-4
    Rank Card — flex items-center gap-4 p-4 rounded-xl border
      Rank Badge — w-10 h-10 rounded-full bg-[--c-accent] text-white font-bold
      Name — text-xl font-bold flex-1
      Total Score — text-2xl font-black text-[--c-accent]
  Recommendation — mt-8 rounded-2xl p-8 bg-[--c-accent]/5 border-2 border-[--c-accent]/20
```

## 3.8 Profile — Entity Portrait

**Use case**: Product introductions, company overviews, people profiles.

**Skeleton Rules**:
```
<main> — max-w-4xl mx-auto px-5 py-10
  Hero Banner — rounded-2xl overflow-hidden mb-8
    Background — h-48 bg-gradient-to-r from-[--c-accent] to-[--c-accent-dark]
    Name Overlay — -mt-12 ml-8
      Avatar — w-24 h-24 rounded-xl bg-white shadow-lg flex items-center justify-center
      Name — text-4xl font-black mt-4
      Tagline — text-lg text-[--c-sub]
  Metrics Bar — grid grid-cols-3 md:grid-cols-6 gap-4 mb-10
    Metric — text-center p-4 rounded-xl bg-[--c-surface] border
      Value — text-2xl md:text-3xl font-bold text-[--c-accent]
      Label — text-sm text-[--c-muted]
  Content Grid — grid grid-cols-1 md:grid-cols-2 gap-6
    Card — rounded-xl p-6 bg-[--c-surface] border h-fit
      Card Title — text-lg font-bold mb-3 flex items-center gap-2
        Icon — lucide icon text-[--c-accent]
      Card Body — text-lg leading-relaxed
  Full Width Section — mt-8 rounded-xl p-6 bg-[--c-surface] border
```

## 3.9 Flowchart — Decision Flow

**Use case**: Decision processes, system flows, diagnostic charts.

**Skeleton Rules**:
```
<main> — max-w-4xl mx-auto px-5 py-10
  Hero — text-center mb-12
  Flow Container — space-y-0
    Start Node — mx-auto w-fit px-8 py-4 rounded-full bg-[--c-accent] text-white font-bold text-lg
    Arrow — mx-auto w-0.5 h-8 bg-[--c-accent]/30
    Decision Node — mx-auto max-w-md p-6 rounded-xl border-2 border-[--c-accent] bg-[--c-accent]/5
      Question — text-lg font-bold text-center
    Branch — grid grid-cols-2 md:grid-cols-3 gap-4 mt-4
      Branch Label — text-center text-sm font-bold text-[--c-accent] mb-2
      Branch Card — rounded-xl p-4 bg-[--c-surface] border h-fit
    Process Node — mx-auto max-w-lg p-6 rounded-xl bg-[--c-surface] border
      Title — text-lg font-bold
      Body — text-base
    End Node — mx-auto w-fit px-8 py-4 rounded-full bg-[--c-accent-dark] text-white font-bold text-lg
  Legend — mt-12 flex gap-6 justify-center text-sm text-[--c-muted]
```

## 3.10 Scorecard — Score Card

**Use case**: Product reviews, evaluation reports, performance cards.

**Skeleton Rules**:
```
<main> — max-w-4xl mx-auto px-5 py-10
  Hero — text-center mb-12
  Overall Score — mx-auto w-48 h-48 rounded-full border-8 border-[--c-accent] flex items-center justify-center mb-8
    Score — text-6xl font-black text-[--c-accent]
    Max — text-xl text-[--c-muted]
  Score Label — text-center text-2xl font-bold mb-12
  Dimension Scores — space-y-6 mb-12
    Dimension — flex items-center gap-4
      Label — w-32 text-right text-sm font-bold
      Bar Container — flex-1 h-6 rounded-full bg-[--c-surface] overflow-hidden
        Bar Fill — h-full rounded-full bg-[--c-accent] (width: [score]%)
      Score — w-12 text-right font-bold text-[--c-accent]
  Pros Cons — grid grid-cols-1 md:grid-cols-2 gap-8
    Pros — rounded-xl p-6 bg-green-50 border-l-4 border-green-500
      Title — text-lg font-bold text-green-700 mb-3
      Items — space-y-2
    Cons — rounded-xl p-6 bg-red-50 border-l-4 border-red-500
      Title — text-lg font-bold text-red-700 mb-3
      Items — space-y-2
  Verdict — mt-12 text-center text-xl
```

## 3.11 Pitch — Narrative Landing Page

**Use case**: Strategic proposals, investor-facing, elevator pitches.

**Skeleton Rules**:
```
<main> — max-w-5xl mx-auto
  Screen 1 (Hero) — min-h-screen flex items-center justify-center px-5
    Tagline — text-5xl md:text-7xl font-black text-center leading-tight
    Subtitle — text-xl text-[--c-sub] text-center mt-6 max-w-2xl
  Screen 2 (Problem) — py-20 px-5
    Section Label — text-sm font-bold text-[--c-accent] uppercase tracking-wider mb-4
    Title — text-3xl md:text-4xl font-black mb-8
    Cards — grid grid-cols-1 md:grid-cols-2 gap-12
  Screen 3 (Solution) — py-20 px-5 bg-[--c-surface]
    (same structure)
  Screen 4 (Evidence) — py-20 px-5
    Data Grid — grid grid-cols-2 md:grid-cols-4 gap-6
      Stat — text-center
        Number — text-4xl font-black text-[--c-accent]
        Label — text-sm text-[--c-muted]
  Screen 5 (CTA) — py-20 px-5 text-center
    Title — text-3xl font-black mb-6
    CTA Button — inline-block px-8 py-4 bg-[--c-accent] text-white rounded-full text-lg font-bold shadow-lg hover:-translate-y-1 transition-all
```

## 3.12 Infographic — Vertical Information Graphic

**Use case**: Data storytelling, statistical highlights, annual reports.

**Skeleton Rules**:
```
<main> — max-w-3xl mx-auto px-5 py-10
  Hero — text-center mb-16
    Big Number — text-6xl md:text-8xl font-black text-[--c-accent]
    Context — text-xl text-[--c-sub] mt-2
    Title — text-3xl font-black mt-4
  Info Block — flex items-start gap-6 mb-12
    Icon — w-16 h-16 rounded-xl bg-[--c-accent]/10 flex items-center justify-center flex-shrink-0
      Lucide Icon — text-[--c-accent] w-8 h-8
    Content —
      Title — text-xl font-bold mb-2
      Body — text-lg leading-relaxed
      Stat — text-3xl font-black text-[--c-accent] mt-2
  Gradient Section — py-12 px-8 rounded-2xl bg-gradient-to-br from-[--c-accent]/5 to-[--c-accent-dark]/5 mb-12
    (section with gradually changing background color)
  Trend Arrow — flex items-center gap-3
    Arrow — text-2xl (up-right / right / down-right)
    Derivative — text-sm text-[--c-muted] (rate of change)
    Description — text-lg
  Divider — my-8 flex items-center gap-4
    Line — flex-1 h-px bg-[--c-border]
    Label — text-sm text-[--c-muted]
```

## 3.13 Comparison Table — Feature Comparison Table

**Use case**: Product comparison, plan comparison, vendor selection.

**Skeleton Rules**:
```
<main> — max-w-5xl mx-auto px-5 py-10
  Hero — text-center mb-12
  Table Container — overflow-x-auto rounded-xl border border-[--c-border]
    Table — w-full text-sm
      Header — bg-[--c-surface]
        Feature Column — text-left p-4 font-bold
        Option Columns — text-center p-4
          Recommended — border-2 border-[--c-accent] rounded-t-xl
            Badge — bg-[--c-accent] text-white text-xs px-2 py-0.5 rounded-full
      Body —
        Rows — border-b border-[--c-border]
          Category Header — bg-[--c-surface]/50 font-bold text-[--c-text] p-4 colspan
          Feature Row —
            Feature Name — p-4 text-left
            Check — p-4 text-center
              Yes — lucide-check text-[--c-accent]
              No — lucide-x text-[--c-muted]
              Partial — lucide-minus text-[--c-muted]/50
        Zebra — even:bg-[--c-surface]/30
      Footer — bg-[--c-surface]
        Price Row — font-bold text-lg p-4
        CTA Row — p-4
  Notes — mt-8 text-sm text-[--c-muted] space-y-1
```

## 3.14 FAQ — Accordion Q&A

**Use case**: FAQ, knowledge bases, Q&A compilations.

**Skeleton Rules**:
```
<main> — max-w-3xl mx-auto px-5 py-10
  Hero — text-center mb-12
  Category Tabs — flex gap-2 mb-8 overflow-x-auto
    Tab — px-4 py-2 rounded-full text-sm font-bold
      Active — bg-[--c-accent] text-white
      Inactive — bg-[--c-surface] text-[--c-muted] border
  FAQ Group — mb-8
    Group Title — text-xl font-bold mb-4
    Items — space-y-3
      Item — <details> rounded-xl border overflow-hidden
        <summary> — p-5 bg-[--c-surface] cursor-pointer font-bold text-lg flex items-center justify-between
          Question Text —
          Chevron — lucide-chevron-down transition-transform
        Answer — p-5 border-l-2 border-[--c-accent]/30
          Body — text-lg leading-relaxed
          Related — mt-4 text-sm text-[--c-muted]
  Contact — mt-16 rounded-2xl p-8 bg-[--c-accent]/5 text-center
```

## 3.15 Slide — 16:9 Slides

**Use case**: Team presentations, PDF output, presentations.

**Skeleton Rules**:
```
<body> — background: #E2E8F0; padding: 24px 0
  Print Button — position:fixed top:12px right:20px z-50 (no-print)
  Slide — width:1280px height:720px position:relative overflow:hidden margin:0 auto 24px border:1px solid var(--c-border)
    Slide Inner — padding:32px 48px 40px height:100% display:flex flex-direction:column
    Bottom Bar — position:absolute bottom:0 left:0 right:0 height:4px background:var(--c-accent)
    Page Number — position:absolute bottom:14px right:40px text:13px color:var(--c-dim)
    Footer Text — position:absolute bottom:14px left:40px text:13px color:var(--c-dim)

  Cover Slide — dark background (var(--c-accent-dark))
    Title — text:54px font-weight:900 color:white text-center
    Subtitle — text:20px color:rgba(255,255,255,0.5) text-center
    Meta Pills — flex gap:12px (audience / purpose / date)

  Content Slide — light background (var(--c-bg))
    Section Header — flex items-center gap:12px mb:16px
      Icon Box — w:40px h:40px rounded:5px bg:var(--c-accent)/10 flex center
      H2 — text:26px font-weight:700
    Content Area — flex:1 (grid / flex layout)

  @page — size:landscape margin:0
  @media print —
    * — -webkit-print-color-adjust:exact!important print-color-adjust:exact!important
    body — margin:0!important padding:0!important background:white!important
    .no-print — display:none!important
    .slide — width:100vw!important height:100vh!important margin:0!important border:none!important page-break-after:always!important page-break-inside:avoid!important overflow:hidden!important
    .slide:last-child — page-break-after:auto!important
    .slide-dark — background:[CI secondary]!important (force dark bg in print)
```

## 3.16 Iceberg — Surface vs Deep Structure

**Use case**: Root cause analysis, surface understanding vs deep structure.

**Skeleton Rules**:
```
<main> — max-w-4xl mx-auto px-5 py-10
  Hero — text-center mb-12
  Surface Zone — 30% height
    Container — rounded-t-2xl p-8 bg-[--c-accent]/5 border-t-2 border-x-2 border-[--c-accent]/20
      Label — text-sm font-bold text-[--c-accent] uppercase tracking-wider mb-4
      Title — text-2xl font-bold mb-4
      Items — grid grid-cols-1 md:grid-cols-2 gap-4
        Item — rounded-xl p-4 bg-white/80 border
  Water Line — relative my-0
    Line — h-2 bg-gradient-to-r from-[--c-accent]/20 via-[--c-accent]/40 to-[--c-accent]/20
    Label — absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2 bg-white px-4 text-sm font-bold text-[--c-accent]
  Deep Zone — 70% height, progressively darker
    Level 1 — p-8 bg-[--c-accent]/8 border-x-2 border-[--c-accent]/20
      Depth Badge — text-sm font-bold text-[--c-accent] mb-2
      Content — text-lg
    Level 2 — p-8 bg-[--c-accent]/12 border-x-2 border-[--c-accent]/20
    Level 3 — p-8 bg-[--c-accent]/16 border-x-2 border-b-2 border-[--c-accent]/20 rounded-b-2xl
      (deepest layer = darkest color)
  Root Cause — mt-8 rounded-2xl p-8 bg-[--c-accent-dark] text-white
    Title — text-xl font-bold
    Body — text-lg opacity-90
```

## 3.17 Funnel — Funnel

**Use case**: Conversion analysis, sales funnels, process attrition.

**Skeleton Rules**:
```
<main> — max-w-4xl mx-auto px-5 py-10
  Hero — text-center mb-12
  Funnel Container — space-y-0 mx-auto
    Level 1 — max-w-4xl mx-auto p-6 rounded-t-2xl bg-[--c-accent]/5 border-t-2 border-x-2 border-[--c-accent]/10
      flex items-center justify-between
      Stage Name — text-xl font-bold
      Metrics — text-right
        Count — text-2xl font-black text-[--c-accent]
        Conversion — text-sm text-[--c-muted]
    Level 2 — max-w-3xl mx-auto p-6 bg-[--c-accent]/10 border-x-2 border-[--c-accent]/15
      (same structure, narrower width)
    Level 3 — max-w-2xl mx-auto p-6 bg-[--c-accent]/15 border-x-2 border-[--c-accent]/20
    Level 4 — max-w-xl mx-auto p-6 bg-[--c-accent]/20 border-x-2 border-b-2 border-[--c-accent]/25 rounded-b-2xl
  Drop-off Indicators — absolute right side
    Arrow — text-red-500 text-sm (drop-off rate)
  Bottom Result — mt-8 mx-auto max-w-lg rounded-2xl p-8 bg-[--c-accent] text-white text-center
    Final Number — text-4xl font-black
    Label — text-lg opacity-80
```

## 3.18 Bridge — Transformation Path

**Use case**: Change proposals, As-Is / To-Be, gap analysis.

**Skeleton Rules**:
```
<main> — max-w-6xl mx-auto px-5 py-10
  Hero — text-center mb-12
  Three Zones — grid grid-cols-1 md:grid-cols-[1fr_2fr_1fr] gap-6 items-start
    Left (As-Is) — rounded-2xl p-6 bg-red-50 border-2 border-red-200
      Label — text-sm font-bold text-red-500 uppercase tracking-wider mb-2
      Title — text-xl font-bold mb-4
      Pain Points — space-y-3
        Point — flex items-start gap-3
          Icon — lucide-alert-triangle text-red-400
          Text — text-lg
    Center (Bridge) — space-y-4
      Label — text-center text-sm font-bold text-[--c-accent] uppercase tracking-wider mb-2
      Bridge Steps — space-y-0
        Step — relative p-4 rounded-xl bg-[--c-accent]/5 border border-[--c-accent]/20
          Step Number — w-8 h-8 rounded-full bg-[--c-accent] text-white font-bold text-sm flex items-center justify-center
          Title — text-lg font-bold
          Body — text-base
        Connector — mx-auto w-0.5 h-6 bg-[--c-accent]/30
      Key Transition — p-4 rounded-xl bg-[--c-accent]/15 border-2 border-[--c-accent]/30 (accent)
    Right (To-Be) — rounded-2xl p-6 bg-green-50 border-2 border-green-200
      Label — text-sm font-bold text-green-500 uppercase tracking-wider mb-2
      Title — text-xl font-bold mb-4
      Outcomes — space-y-3
        Outcome — flex items-start gap-3
          Icon — lucide-check-circle text-green-500
          Text — text-lg
  Summary — mt-12 rounded-2xl p-8 bg-[--c-surface] border text-center
```
