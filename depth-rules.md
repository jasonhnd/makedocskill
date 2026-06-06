# Depth Visualization & Few-Shot Reference

> **[HTML output mode — optional]** make-doc-skill's primary path is company document generation (Word/PDF/bilingual board materials; see `SKILL.md`). The HTML depth-visualization Canvas instructions and HTML few-shots below apply only when the deliverable is an HTML visual document or 16:9 HTML deck. For company documents, depth is controlled per `docs/SIZE_DEPTH_MATRIX.md`.

> Contains 4-tier depth visualization Canvas instructions and HTML reference examples.

When material contains the following data structures, **the corresponding visualization method must be used**. Degradation to text lists is prohibited.

---

## 6.1 S Size (core rules only)

At S size, only the following core rules apply:

- **Causal Chain**: Vertical flow + arrows. Mechanism explanation mandatory at each node. Parallel cards prohibited. CI color opacity for hierarchy (root cause=darkest, result=lightest).
- **Confidence**: Horizontal progress bar + percentage + reason explanation. Color scale: >=80% dark / 50-79% medium / 30-49% light / <30% lightest.
- **Comparison Increment**: GAP column mandatory. Direction arrows (improvement / deterioration / stable). Color-coded difference (positive/negative using different opacities of CI color).

## 6.2 M Size (+ Information Quality Badges + Trend Visualization + Round 2 Challenge)

All S rules plus:

- **Information Quality Badges**: Place evidence level badges next to each major conclusion. Primary data (dark badge) / Secondary speculation (medium badge) / Unverified (light badge). `[DATA_GAP]` displayed as warning callout.

```html
<!-- Information Quality Badge Example -->
<span class="inline-flex items-center gap-1 px-2 py-0.5 rounded-full text-xs font-bold" style="background:color-mix(in srgb,var(--c-accent) 15%,transparent);color:var(--c-accent)">
  <svg xmlns="http://www.w3.org/2000/svg" width="10" height="10" viewBox="0 0 24 24" fill="currentColor"><circle cx="12" cy="12" r="10"/></svg>
  Primary Data
</span>
<span class="inline-flex items-center gap-1 px-2 py-0.5 rounded-full text-xs font-bold" style="background:color-mix(in srgb,var(--c-accent) 8%,transparent);color:var(--c-muted)">
  <svg xmlns="http://www.w3.org/2000/svg" width="10" height="10" viewBox="0 0 24 24" fill="currentColor"><circle cx="12" cy="12" r="10"/></svg>
  Speculation
</span>
```

- **Trend Visualization**: CSS mini bar + direction arrows. **Derivative (rate of change) calculation mandatory**. One-sentence explanation included.

```html
<!-- Trend Visualization Example -->
<div class="flex items-center gap-3">
  <div class="w-24 h-4 rounded-full overflow-hidden" style="background:var(--c-surface)">
    <div class="h-full rounded-full" style="width:68%;background:var(--c-accent)"></div>
  </div>
  <span class="text-lg font-bold" style="color:var(--c-accent)">68%</span>
  <span class="text-sm" style="color:var(--c-accent)">+12pp YoY</span>
  <span class="text-sm" style="color:var(--c-muted)">Accelerating trend (prior year +8pp -> this year +12pp)</span>
</div>
```

- **Round 2 Challenge Block**: Visualizes sparring challenges. Dedicated callout showing "counterargument -> rebuttal."

```html
<!-- Round 2 Challenge Example -->
<div class="rounded-xl p-5 my-6" style="background:color-mix(in srgb,var(--c-accent-dark) 5%,transparent);border:1px dashed color-mix(in srgb,var(--c-accent-dark) 20%,transparent)">
  <div class="flex items-center gap-2 mb-3">
    <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="var(--c-accent-dark)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M8 2v4"/><path d="M16 2v4"/><path d="M21 13V6a2 2 0 0 0-2-2H5a2 2 0 0 0-2 2v14a2 2 0 0 0 2 2h8"/></svg>
    <span class="font-bold text-sm" style="color:var(--c-accent-dark)">CHALLENGE</span>
  </div>
  <p class="text-base mb-2" style="color:var(--c-sub)"><strong>Counterargument:</strong> [Counterargument content]</p>
  <p class="text-base" style="color:var(--c-body)"><strong>Rebuttal:</strong> [Rebuttal content]</p>
</div>
```

## 6.3 L Size (+ Search Supplementation + Uncertainty Section + Confidence Gradient)

All M rules plus:

- **Search Supplementation**: Background information not in the materials is added with `[Supplemental]` marking. Sources explicitly stated.

```html
<!-- Supplemental Information Example -->
<div class="rounded-xl p-4 my-4" style="background:color-mix(in srgb,var(--c-muted) 5%,transparent);border:1px solid color-mix(in srgb,var(--c-muted) 15%,transparent)">
  <div class="flex items-center gap-1.5 mb-2">
    <svg xmlns="http://www.w3.org/2000/svg" width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="var(--c-muted)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="11" cy="11" r="8"/><path d="m21 21-4.3-4.3"/></svg>
    <span class="text-xs font-bold" style="color:var(--c-muted)">[Supplemental] Background Information</span>
  </div>
  <p class="text-base" style="color:var(--c-sub)">[Supplemental background information text]</p>
</div>
```

- **Uncertainty Section**: Independent "uncertainty area." Dashed border + reduced opacity. Information gap list.

```html
<!-- Uncertainty Section Example -->
<div class="rounded-xl p-6 my-8" style="border:2px dashed color-mix(in srgb,var(--c-muted) 30%,transparent);background:color-mix(in srgb,var(--c-muted) 3%,transparent)">
  <h3 class="text-lg font-bold mb-4 flex items-center gap-2" style="color:var(--c-muted)">
    <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M9.09 9a3 3 0 0 1 5.83 1c0 2-3 3-3 3"/><path d="M12 17h.01"/></svg>
    Uncertainty Area
  </h3>
  <ul class="space-y-2" style="color:var(--c-sub)">
    <li class="flex items-start gap-2 text-base">
      <span class="text-sm font-bold px-2 py-0.5 rounded" style="background:color-mix(in srgb,var(--c-muted) 10%,transparent);color:var(--c-muted)">GAP</span>
      [Description of unknown point / information gap]
    </li>
  </ul>
</div>
```

- **Confidence Gradient**: Background color intensity changes according to conclusion confidence. High confidence=dark color, low confidence=light color.

## 6.4 XL Size (+ Collapsible Details + Evidence Citation Markers)

All L rules plus:

- **Collapsible Details**: Additional information collapsed with `<details>`. Does not obstruct main flow.

```html
<!-- Collapsible Details Example -->
<details class="rounded-xl border overflow-hidden my-4" style="border-color:var(--c-border)">
  <summary class="p-4 cursor-pointer font-bold text-base flex items-center justify-between" style="background:var(--c-surface);color:var(--c-text)">
    View Detailed Data
    <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="m6 9 6 6 6-6"/></svg>
  </summary>
  <div class="p-4 text-base" style="color:var(--c-body)">
    [Detailed data / supplementary information]
  </div>
</details>
```

- **Evidence Citation Markers**: Superscript numbers at the end of each claim indicating the source. Source list in footer.

```html
<!-- Evidence Citation Marker Example -->
<span>[Claim text]</span>
<sup class="text-xs font-bold cursor-help" style="color:var(--c-accent)" title="Source: [Material Name]">[1]</sup>

<!-- Footer Source List -->
<div class="mt-16 border-t pt-8" style="border-color:var(--c-border)">
  <h3 class="text-sm font-bold uppercase tracking-wider mb-4" style="color:var(--c-muted)">Sources</h3>
  <ol class="space-y-1 text-sm" style="color:var(--c-muted)">
    <li>[1] [Source information]</li>
    <li>[2] [Source information]</li>
  </ol>
</div>
```

---

## Few-Shot Reference HTML

### 9.1 Executive Summary

```html
<div style="background:var(--c-surface);border:1px solid var(--c-border)" class="rounded-2xl p-8 mb-10">
  <h2 class="text-xl font-bold mb-4" style="color:var(--c-text)">Executive Summary</h2>
  <p class="text-lg leading-relaxed mb-4" style="color:var(--c-body)">
    <span class="font-bold" style="color:var(--c-accent)">Conclusion:</span> The three structural challenges of cross-border B2B settlement (legal risk, misdirected payments, manual reconciliation) can be resolved through a new digital settlement scheme. Acme holds a strong position at the intersection of payments, settlement, and platform services.
  </p>
  <div class="border-l-4 p-5 rounded-r-xl mb-4" style="border-color:var(--c-accent);background:color-mix(in srgb,var(--c-accent) 5%,transparent)">
    <span class="font-bold" style="color:var(--c-accent)">Key Finding:</span> Among the Top 3 options, "Option A" (85 points) scored highest. The optimal strategy is "enter with the basic service, earn with the premium tier" — acquire customers short-term with Option B (81 points) and expand mid-term into Option A (85 points).
  </div>
  <p class="text-lg leading-relaxed" style="color:var(--c-body)">
    <span class="font-bold" style="color:var(--c-accent)">Recommended Action:</span> Within 3 months, initiate three workstreams: regulatory pre-consultation, partner selection, and a limited pilot.
  </p>
</div>
```

### 9.2 Data Cards

```html
<div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4 mb-10">
  <div class="rounded-xl p-6 border text-center" style="background:var(--c-surface);border-color:var(--c-border)">
    <p class="text-sm mb-1" style="color:var(--c-muted)">Annual Transaction Target</p>
    <p class="text-3xl font-bold" style="color:var(--c-accent)">$2.4B</p>
    <p class="text-xs mt-2" style="color:var(--c-accent)">+34% YoY</p>
  </div>
  <div class="rounded-xl p-6 border text-center" style="background:var(--c-surface);border-color:var(--c-border)">
    <p class="text-sm mb-1" style="color:var(--c-muted)">Customers</p>
    <p class="text-3xl font-bold" style="color:var(--c-accent)">1,200</p>
    <p class="text-xs mt-2" style="color:var(--c-accent)">Phase 3 Target</p>
  </div>
  <div class="rounded-xl p-6 border text-center" style="background:var(--c-surface);border-color:var(--c-border)">
    <p class="text-sm mb-1" style="color:var(--c-muted)">Premium-tier Balance</p>
    <p class="text-3xl font-bold" style="color:var(--c-accent)">$500M</p>
    <p class="text-xs mt-2" style="color:var(--c-muted)">Mid-term Target</p>
  </div>
  <div class="rounded-xl p-6 border text-center" style="background:var(--c-surface);border-color:var(--c-border)">
    <p class="text-sm mb-1" style="color:var(--c-muted)">Annual Revenue</p>
    <p class="text-3xl font-bold" style="color:var(--c-accent)">10B JPY</p>
    <p class="text-xs mt-2" style="color:var(--c-accent)">Phase 3 Target</p>
  </div>
</div>
```

### 9.3 Comparison Table

```html
<div class="overflow-x-auto rounded-xl border my-8" style="border-color:var(--c-border)">
  <table class="w-full text-sm">
    <thead>
      <tr style="background:var(--c-surface)">
        <th class="text-left p-4 font-bold" style="color:var(--c-text)">Comparison Item</th>
        <th class="text-center p-4 font-bold border-x-2" style="color:var(--c-accent);border-color:color-mix(in srgb,var(--c-accent) 20%,transparent)">
          <span class="inline-block px-2 py-0.5 rounded-full text-xs text-white mb-1" style="background:var(--c-accent)">Recommended</span><br>
          Acme Instant Settlement
        </th>
        <th class="text-center p-4 font-bold" style="color:var(--c-muted)">Traditional SWIFT Transfer</th>
        <th class="text-center p-4 font-bold" style="color:var(--c-muted)">Bank L/C</th>
      </tr>
    </thead>
    <tbody>
      <tr style="border-bottom:1px solid var(--c-border)">
        <td class="p-4 font-medium" style="color:var(--c-body)">Transfer Speed</td>
        <td class="p-4 text-center border-x-2" style="border-color:color-mix(in srgb,var(--c-accent) 20%,transparent)">
          <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="var(--c-accent)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="mx-auto"><path d="M20 6 9 17l-5-5"/></svg>
          <span class="text-xs block mt-1" style="color:var(--c-accent)">Instant</span>
        </td>
        <td class="p-4 text-center">
          <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="var(--c-muted)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="mx-auto"><path d="M5 12h14"/></svg>
          <span class="text-xs block mt-1" style="color:var(--c-muted)">2-5 Business Days</span>
        </td>
        <td class="p-4 text-center">
          <svg xmlns="http://www.w3.org/2000/svg" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="var(--c-muted)" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="mx-auto"><path d="M18 6 6 18"/><path d="m6 6 12 12"/></svg>
          <span class="text-xs block mt-1" style="color:var(--c-muted)">5-10 Business Days</span>
        </td>
      </tr>
    </tbody>
  </table>
</div>
```
