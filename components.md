# Component HTML Templates Reference

> **[HTML output mode — optional]** make-doc-skill's primary path is company document generation (Word/PDF/bilingual board materials; see `SKILL.md`). This file is the HTML component machinery — load it only when the requested deliverable is an HTML visual document or 16:9 HTML deck.

> Referenced by SKILL.md (HTML output mode). Contains complete HTML code for all 16 visual components.

All components use CSS variables (`--c-accent`, etc.) and `color-mix()` for color control. Auto-adapts to CI color palette.

---

## 01_design.md Template (Step 1 Output)

```markdown
# Design System — [Organization Name]

## Source
[URL] (crawled on [date])

## Brand Colors
- Primary: [HEX] ([RGB] — [usage description])
- Secondary: [HEX] ([RGB] — [usage description])
- Background: [HEX]
- Surface: [HEX] ([RGB] — [usage description])
- Text: [HEX] ([RGB] — [usage description])
- Heading: [HEX] ([RGB] — [usage description])
- Muted Text: [HEX] (estimated — for muted text)
- Dimmest Text: [HEX] (estimated — for footers and auxiliary info)

## Typography
- Heading: [font family] (Google Fonts)
- Body: [font stack]
- Heading Weight: [value]

## Logo
- File: [URL or base64]
- Placement Suggestion: [usage method]

## Border Radius
- Preference: [sharp / rounded / mixed]
- Common Values: [value list]

## Shadows
- Style: [none / subtle / medium / pronounced]
- Common Values:
  - [shadow value 1]
  - [shadow value 2]

## Spacing Rhythm
- Common Padding: [value list]
- Common Gap: [value list]

## Component Style
- Buttons: [style description]
- Cards: [style description]

## Light/Dark Mode
- [support status]
- This document uses [light/dark] mode

## Overall Tone
[One sentence summarizing the overall visual tone]

## Signature Info
[Organization official name]
```

---

## 5.1 Meta Pills (Metadata Badges)

```html
<div class="flex flex-wrap gap-2 mb-6">
  <span class="inline-flex items-center gap-1.5 px-3 py-1 rounded-full text-sm font-medium" style="background:color-mix(in srgb,var(--c-accent) 10%,transparent);color:var(--c-accent)">
    <svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M16 21v-2a4 4 0 0 0-4-4H6a4 4 0 0 0-4 4v2"/><circle cx="9" cy="7" r="4"/></svg>
    For Teams
  </span>
  <span class="inline-flex items-center gap-1.5 px-3 py-1 rounded-full text-sm font-medium" style="background:color-mix(in srgb,var(--c-accent) 10%,transparent);color:var(--c-accent)">
    <svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect width="18" height="18" x="3" y="4" rx="2" ry="2"/><line x1="16" x2="16" y1="2" y2="6"/><line x1="8" x2="8" y1="2" y2="6"/><line x1="3" x2="21" y1="10" y2="10"/></svg>
    April 2026
  </span>
</div>
```

## 5.2 Hero Section

```html
<div class="mb-10">
  <h1 class="text-4xl md:text-5xl font-black leading-tight" style="color:var(--c-text)">[Document Title]</h1>
  <p class="text-lg mt-4 leading-relaxed" style="color:var(--c-sub)">[Subtitle / Overview Text]</p>
</div>
```

## 5.3 Summary Card

```html
<div class="rounded-2xl p-8 mb-10" style="background:var(--c-surface);border:1px solid var(--c-border)">
  <h2 class="text-xl font-bold mb-4" style="color:var(--c-text)">Executive Summary</h2>
  <p class="text-lg leading-relaxed mb-4" style="color:var(--c-body)">
    <span class="font-bold" style="color:var(--c-accent)">Conclusion:</span> [Core conclusion text]
  </p>
  <div class="border-l-4 p-5 rounded-r-xl mb-4" style="border-color:var(--c-accent);background:color-mix(in srgb,var(--c-accent) 5%,transparent)">
    <span class="font-bold" style="color:var(--c-accent)">Key Finding:</span> [Data-backed finding text]
  </div>
  <p class="text-lg leading-relaxed" style="color:var(--c-body)">
    <span class="font-bold" style="color:var(--c-accent)">Recommended Action:</span> [Specific next step text]
  </p>
</div>
```

## 5.4 Flow Diagram

```html
<div class="flex flex-col md:flex-row items-center justify-center gap-0 my-8">
  <!-- Node 1 -->
  <div class="flex flex-col items-center w-48">
    <div class="w-16 h-16 rounded-xl flex items-center justify-center mb-2" style="background:color-mix(in srgb,var(--c-accent) 10%,transparent);border:1px solid color-mix(in srgb,var(--c-accent) 20%,transparent)">
      <svg xmlns="http://www.w3.org/2000/svg" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="var(--c-accent)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><!-- lucide icon --></svg>
    </div>
    <span class="font-bold text-lg" style="color:var(--c-text)">[Node Name]</span>
    <span class="text-sm" style="color:var(--c-muted)">[Description]</span>
  </div>
  <!-- Arrow -->
  <svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="var(--c-dim)" stroke-width="2"><path d="M5 12h14"/><path d="m12 5 7 7-7 7"/></svg>
  <!-- Node 2 (repeat) -->
</div>
```

## 5.5 Section Header

```html
<div class="flex items-center gap-3 mb-6 mt-12">
  <div class="w-10 h-10 rounded-lg flex items-center justify-center flex-shrink-0" style="background:color-mix(in srgb,var(--c-accent) 10%,transparent)">
    <svg xmlns="http://www.w3.org/2000/svg" width="22" height="22" viewBox="0 0 24 24" fill="none" stroke="var(--c-accent)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><!-- lucide icon --></svg>
  </div>
  <h2 class="text-2xl font-bold" style="color:var(--c-text)">[Message-Type Title]</h2>
</div>
```

## 5.6 Info Card

```html
<div class="rounded-xl p-6 h-fit" style="background:var(--c-surface);border:1px solid var(--c-border)">
  <div class="flex items-center gap-2 mb-3">
    <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="var(--c-accent)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><!-- lucide icon --></svg>
    <h3 class="text-lg font-bold" style="color:var(--c-text)">[Card Title]</h3>
  </div>
  <p class="text-lg leading-relaxed" style="color:var(--c-body)">[Card Content]</p>
</div>
```

## 5.7 Highlight Box

```html
<div class="border-l-4 p-5 rounded-r-xl my-6" style="border-color:var(--c-accent);background:color-mix(in srgb,var(--c-accent) 5%,transparent)">
  <div class="flex items-center gap-2 mb-2">
    <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="var(--c-accent)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M15 14c.2-1 .7-1.7 1.5-2.5 1-.9 1.5-2.2 1.5-3.5A6 6 0 0 0 6 8c0 1 .2 2.2 1.5 3.5.7.7 1.3 1.5 1.5 2.5"/><path d="M9 18h6"/><path d="M10 22h4"/></svg>
    <span class="font-bold" style="color:var(--c-accent)">[Highlight Label]</span>
  </div>
  <p class="text-lg leading-relaxed" style="color:var(--c-body)">[Highlight Content]</p>
</div>
```

## 5.8 Numbered Steps

```html
<div class="space-y-4 my-6">
  <div class="flex items-start gap-4">
    <div class="w-8 h-8 rounded-full flex items-center justify-center font-bold text-white flex-shrink-0" style="background:var(--c-accent)">1</div>
    <div>
      <p class="font-bold text-lg" style="color:var(--c-text)">[Step Title]</p>
      <p class="text-lg leading-relaxed" style="color:var(--c-body)">[Step Content]</p>
    </div>
  </div>
  <div class="flex items-start gap-4">
    <div class="w-8 h-8 rounded-full flex items-center justify-center font-bold text-white flex-shrink-0" style="background:var(--c-accent)">2</div>
    <div>
      <p class="font-bold text-lg" style="color:var(--c-text)">[Step Title]</p>
      <p class="text-lg leading-relaxed" style="color:var(--c-body)">[Step Content]</p>
    </div>
  </div>
</div>
```

## 5.9 Vertical Cycle (Vertical Cycle/Pipeline)

```html
<div class="space-y-0 my-8">
  <!-- Stage 1 -->
  <div class="relative p-6 rounded-t-xl" style="background:color-mix(in srgb,var(--c-accent) 6%,transparent);border:1px solid color-mix(in srgb,var(--c-accent) 15%,transparent)">
    <div class="flex items-center gap-3 mb-2">
      <span class="px-3 py-1 rounded-full text-sm font-bold text-white" style="background:var(--c-accent)">Phase 1</span>
      <span class="text-lg font-bold" style="color:var(--c-text)">[Phase Name]</span>
    </div>
    <p class="text-lg" style="color:var(--c-body)">[Content]</p>
  </div>
  <!-- Connector -->
  <div class="mx-auto w-0.5 h-4" style="background:color-mix(in srgb,var(--c-accent) 30%,transparent)"></div>
  <!-- Stage 2 -->
  <div class="relative p-6" style="background:color-mix(in srgb,var(--c-accent) 10%,transparent);border:1px solid color-mix(in srgb,var(--c-accent) 20%,transparent)">
    <div class="flex items-center gap-3 mb-2">
      <span class="px-3 py-1 rounded-full text-sm font-bold text-white" style="background:var(--c-accent)">Phase 2</span>
      <span class="text-lg font-bold" style="color:var(--c-text)">[Phase Name]</span>
    </div>
    <p class="text-lg" style="color:var(--c-body)">[Content]</p>
  </div>
  <!-- Connector -->
  <div class="mx-auto w-0.5 h-4" style="background:color-mix(in srgb,var(--c-accent) 30%,transparent)"></div>
  <!-- Stage 3 -->
  <div class="relative p-6 rounded-b-xl" style="background:color-mix(in srgb,var(--c-accent) 14%,transparent);border:1px solid color-mix(in srgb,var(--c-accent) 25%,transparent)">
    <div class="flex items-center gap-3 mb-2">
      <span class="px-3 py-1 rounded-full text-sm font-bold text-white" style="background:var(--c-accent)">Phase 3</span>
      <span class="text-lg font-bold" style="color:var(--c-text)">[Phase Name]</span>
    </div>
    <p class="text-lg" style="color:var(--c-body)">[Content]</p>
  </div>
</div>
```

## 5.10 Badge Row

```html
<div class="flex flex-wrap gap-2 my-4">
  <span class="inline-block px-3 py-1 rounded-full text-sm font-bold break-keep" style="background:color-mix(in srgb,var(--c-accent) 10%,transparent);color:var(--c-accent)">[Badge 1]</span>
  <span class="inline-block px-3 py-1 rounded-full text-sm font-bold break-keep" style="background:var(--c-accent);color:white">[Badge 2 (emphasized)]</span>
  <span class="inline-block px-3 py-1 rounded-full text-sm font-bold break-keep" style="background:color-mix(in srgb,var(--c-accent-dark) 10%,transparent);color:var(--c-accent-dark)">[Badge 3]</span>
</div>
```

## 5.11 Divider

```html
<div class="flex items-center gap-4 my-10">
  <div class="flex-1 h-px" style="background:var(--c-border)"></div>
  <span class="text-sm font-medium" style="color:var(--c-muted)">[Divider Label (optional)]</span>
  <div class="flex-1 h-px" style="background:var(--c-border)"></div>
</div>
```

## 5.12 Two-Column Comparison

```html
<div class="grid grid-cols-1 md:grid-cols-2 gap-6 my-8">
  <div class="rounded-xl p-6" style="background:color-mix(in srgb,var(--c-accent) 4%,transparent);border:1px solid color-mix(in srgb,var(--c-accent) 15%,transparent)">
    <div class="inline-block px-3 py-1 rounded-full text-sm font-bold mb-4" style="background:color-mix(in srgb,var(--c-accent) 12%,transparent);color:var(--c-accent)">[Left Label]</div>
    <ul class="space-y-2 text-lg" style="color:var(--c-body);list-style:none;padding:0">
      <li class="flex items-start gap-2">
        <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="var(--c-accent)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="mt-1 flex-shrink-0"><path d="M20 6 9 17l-5-5"/></svg>
        [Advantage Item]
      </li>
    </ul>
  </div>
  <div class="rounded-xl p-6" style="background:color-mix(in srgb,var(--c-accent-dark) 4%,transparent);border:1px solid color-mix(in srgb,var(--c-accent-dark) 15%,transparent)">
    <div class="inline-block px-3 py-1 rounded-full text-sm font-bold mb-4" style="background:color-mix(in srgb,var(--c-accent-dark) 12%,transparent);color:var(--c-accent-dark)">[Right Label]</div>
    <ul class="space-y-2 text-lg" style="color:var(--c-body);list-style:none;padding:0">
      <li class="flex items-start gap-2">
        <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="var(--c-muted)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="mt-1 flex-shrink-0"><path d="M18 6 6 18"/><path d="m6 6 12 12"/></svg>
        [Disadvantage Item]
      </li>
    </ul>
  </div>
</div>
```

## 5.13 Small Command Grid

```html
<div class="grid grid-cols-2 md:grid-cols-3 gap-3 my-6">
  <div class="rounded-lg p-4 text-center" style="background:var(--c-surface);border:1px solid var(--c-border)">
    <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="var(--c-accent)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="mx-auto mb-2"><!-- lucide icon --></svg>
    <p class="text-sm font-bold" style="color:var(--c-text)">[Item Name]</p>
    <p class="text-xs" style="color:var(--c-muted)">[Description]</p>
  </div>
</div>
```

## 5.14 Data Chart (3 Types)

### Bar Chart (Horizontal Bar)

```html
<div class="space-y-3 my-6">
  <div class="flex items-center gap-3">
    <span class="w-24 text-right text-sm font-medium" style="color:var(--c-sub)">[Label]</span>
    <div class="flex-1 h-6 rounded-full overflow-hidden" style="background:var(--c-surface)">
      <div class="h-full rounded-full" style="width:75%;background:var(--c-accent)"></div>
    </div>
    <span class="w-12 text-right text-sm font-bold" style="color:var(--c-accent)">75%</span>
  </div>
  <div class="flex items-center gap-3">
    <span class="w-24 text-right text-sm font-medium" style="color:var(--c-sub)">[Label]</span>
    <div class="flex-1 h-6 rounded-full overflow-hidden" style="background:var(--c-surface)">
      <div class="h-full rounded-full" style="width:45%;background:color-mix(in srgb,var(--c-accent) 60%,transparent)"></div>
    </div>
    <span class="w-12 text-right text-sm font-bold" style="color:var(--c-accent)">45%</span>
  </div>
</div>
```

### Column Chart (Vertical Bar)

```html
<div class="flex items-end justify-center gap-4 h-48 my-8">
  <div class="flex flex-col items-center gap-1">
    <span class="text-xs font-bold" style="color:var(--c-accent)">$2.4B</span>
    <div class="w-12 rounded-t-lg" style="height:80%;background:var(--c-accent)"></div>
    <span class="text-xs" style="color:var(--c-muted)">2024</span>
  </div>
  <div class="flex flex-col items-center gap-1">
    <span class="text-xs font-bold" style="color:var(--c-accent)">$3.1B</span>
    <div class="w-12 rounded-t-lg" style="height:100%;background:var(--c-accent)"></div>
    <span class="text-xs" style="color:var(--c-muted)">2025</span>
  </div>
</div>
```

### KPI Number Card

```html
<div class="grid grid-cols-2 sm:grid-cols-4 gap-4 my-6">
  <div class="rounded-xl p-6 text-center" style="background:var(--c-surface);border:1px solid var(--c-border)">
    <p class="text-3xl font-bold" style="color:var(--c-accent)">$2.4B</p>
    <p class="text-sm mt-1" style="color:var(--c-muted)">[Metric Name]</p>
    <p class="text-xs mt-2" style="color:var(--c-accent)">+34% YoY</p>
  </div>
</div>
```

## 5.15 Print Button

```html
<div class="no-print" style="position:fixed;top:12px;right:20px;z-index:50">
  <button onclick="window.print()" class="flex items-center gap-1.5 px-3 py-1.5 rounded-lg text-sm cursor-pointer" style="color:var(--c-muted);background:white;border:1px solid var(--c-border)">
    <svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"/><polyline points="7 10 12 15 17 10"/><line x1="12" x2="12" y1="15" y2="3"/></svg>
    PDF
  </button>
</div>
```

## 5.16 Return Flow Pill

```html
<div class="flex items-center gap-2 px-4 py-2 rounded-full text-sm" style="background:color-mix(in srgb,var(--c-accent) 8%,transparent);color:var(--c-accent);border:1px solid color-mix(in srgb,var(--c-accent) 15%,transparent)">
  <svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="m12 19-7-7 7-7"/><path d="M19 12H5"/></svg>
  [Return Link Text]
</div>
```
