# Company Document Design Rules / 企業文書デザインルール / 企业文档设计规则

> Hard constraints for the Canvas layer (Step 7 render). DOCX / 16:9 deck / diagram / token / brand-color discipline for formal company documents.

[EN](#english) · [日本語](#japanese) · [中文](#chinese)

---

## English {#english}

> These rules are hard constraints for the Canvas layer (Step 7 render / Quality Gates in Step 6 and Step 8). Canvas makes no editorial decisions — it applies tokens and these layout rules. The primary deliverables are formal Word/PDF board materials, IR / CFO proposals, bilingual Japanese/Chinese documents, and 16:9 HTML/PDF decks. All color comes from the company tokens. No blue unless the brand calls for it.

### Overview

Whatever the deliverable type, depth (S/M/L/XL), or language mode, the rules below always apply. Tokens are the design memory; these rules are how Canvas spends them. When the company token set conflicts with a default here, the company tokens win.

### 1. Formal DOCX/PDF Layout

Use for board packs, internal approval documents, IR / CFO proposals, policy explanations, and Japanese listed-company materials. Apply these defaults unless the user specifies otherwise.

| Element | Size | Notes |
|---------|------|-------|
| Page | A4 portrait, ~18mm margin | Default for formal board materials |
| Body | 12pt, line spacing 1.15–1.2 | Never shrink body below 12pt unless overridden |
| Major heading | 17–20pt | Chapter / part level |
| Section heading | 14–16pt | |
| Subsection heading | 12.5–13.5pt | |
| Table text | 10.5–11.5pt | Lower end for dense tables |
| Caption / note | 9.5–10pt | |

- Each chapter starts on a new page for formal board materials.
- Table of contents entries are left-aligned; page numbers are visually consistent — centered or right-tabbed per the chosen style.
- Tables use restrained borders plus company-accent header fills; keep tables within page width, reduce text rather than rotating cells.
- Use the company primary color for headings, rules, table headers, and small accent bars; neutral gray for borders and secondary text.
- Use clear hierarchy through weight and spacing, not heavy decoration.
- Avoid Word freeform flow arrows for complex diagrams — render diagrams as fixed SVG/PNG images and place them into the DOCX.
- Check that diagram-heavy pages have no broken wrapping or overlapping objects.

**Fonts (from tokens):** Japanese body Hiragino Sans; Chinese body PingFang SC; Latin / numeric Aptos (or the company-approved Latin font). The DOCX language attribute and fonts follow the locked output language.

### 2. Split Japanese/Chinese Documents

When the user asks to separate languages:

- Generate one Japanese DOCX/PDF and one Chinese DOCX/PDF, each rendered independently.
- Do not leave Chinese fragments in Japanese output, or Japanese fragments in Chinese output, except proper nouns.
- Keep page structure, chart numbering, tables, and section hierarchy parallel across languages.
- Use language-specific fonts and proofread line breaks independently in each file.

### 3. 16:9 Proposal Deck Layout (HTML/PDF)

Use for CFO proposals, IR decks, operating briefings, and large-screen review.

Base assumptions:

- Canvas: 1920x1080 px. Each slide is a fixed viewport section.
- `html { font-size: 20px; }` so 1rem = 20px. Use only tokenized font sizes for slide text.
- Target: conference-room readability at 1–3m plus PDF export.
- Delivery: single HTML file plus PDF, zero build where possible.

Slide layout:

- Header accent bar: 6px using the company primary color.
- Title band near top, content area below, footer fixed at bottom (~48px).
- Content padding scale — default `40px 88px`; compact `28px 72px`; tight `20px 64px`.
- Grids from 2 to 6 columns only; avoid 7+ column grids.
- Cards have a minimum useful width around 250px; border radius stays restrained (typically 6px or less).
- Titles are concise — do not overload title bands.
- Body blocks fill the slide vertically (use `flex: 1`, stretched tables, split columns, callouts, notes). Do not center sparse content as a substitute for real structure, and avoid pure decorative backgrounds.
- Keep the company / product / topic visible in the first viewport.

Print / PDF:

```css
@page {
  size: 508mm 285.75mm;
  margin: 0;
}
```

- Do **not** use `transform: scale()` to fix print layout.
- Print with background graphics enabled.
- Verify PDF page count and page size (16:9) after export; PDF print must match browser rendering.

### 4. Diagram Rules

Use diagrams only when they teach more than a paragraph or table. Allowed types: process flow, funds flow, architecture map, timeline, matrix, org tree, layer stack, waterfall, simple KPI chart.

- One major diagram per slide or page section.
- For DOCX, create diagrams as SVG/PNG and insert as fixed images. For HTML decks, use self-contained inline SVG.
- Avoid Mermaid unless the pipeline reliably converts it into a fixed image.
- Keep node count under 9 where possible; split complex diagrams.
- Use the primary color for at most 1–2 focal nodes — do not make every node the brand color. Use neutral fills and borders for normal nodes.
- Arrow endpoints must land exactly on node edges.
- Use consistent spacing multiples, preferably 4px / 8px.
- Avoid decorative icons, glow, gradients, floating arrows, and non-brand colors.
- For funds flow, prefer a clean left-to-right or top-to-bottom flow with **actor lanes, numbered steps, and a short note table.**

### 5. Token & Brand-Color Discipline

Every company gets a token file (JSON or YAML) before rendering. Do not hardcode colors, fonts, sizes, or spacing into templates unless the token system explicitly allows it.

- **All color comes from the company's tokens.** Introducing a hue outside the company palette is prohibited.
- Use the company primary color as the only functional accent unless the token set explicitly defines additional semantic colors.
- **No blue unless the brand calls for it.** Likewise avoid accidental green / orange functional colors when the brand system is, e.g., red / gray — remove stray blue from headings, tables, links, diagrams, and charts.
- Use the primary color **sparingly** — for headings, rules, table headers, small accent bars, and 1–2 diagram focal nodes only.
- Build hierarchy through **weight, spacing, and muted text**, not uncontrolled font sizes or extra hues.
- Keep color variables in `:root` (deck) or the token file (DOCX); avoid hardcoded hex values in components.

Minimal token shape (example values — replace per company):

```yaml
company:
  legal_name: "Acme Holdings, Inc."   # example only
  ticker: "0000"
brand:
  primary: "#c0392b"        # example red palette — use the company's real tokens
  text: "#242424"
  text_muted: "#666666"
  border: "#d9d9d9"
language:
  ja_font: "Hiragino Sans"
  zh_font: "PingFang SC"
  latin_font: "Aptos"
docx:
  page_size: "A4"
  body_pt: 12
  chapter_page_break: true
  toc_alignment: "left"
slides:
  canvas_px: [1920, 1080]
  base_font_px: 20
  print_page_mm: [508, 285.75]
```

### 6. Quality Gates (Layout)

Run these before final delivery (Step 6 layout review, Step 8 PDF QA):

- DOCX opens without repair warnings; PDF exports from the final DOCX/HTML source.
- Body text is 12pt for formal Word documents unless overridden; headings follow the size bands above.
- TOC alignment is correct (left); chapters start on new pages when required.
- Tables do not overflow page margins; diagrams are not broken, cropped, or built from unstable Word shape arrows.
- No unintended blue / green / orange appears when the brand system is red / gray.
- Japanese / Chinese split files contain the correct language only.
- For HTML decks, browser screenshot and PDF export both show non-overflowing slides; PDF page size is 16:9 and all pages are present.
- Numerical fidelity holds: every figure, unit, currency, and fiscal period matches the source; gaps marked `[DATA_GAP]`; unverified legal/tax statements marked draft.

Useful local checks: `pdfinfo output.pdf`, `pdffonts output.pdf`.

### 7. HTML output mode (optional)

> Secondary, non-default. Only for an HTML visual one-pager / diagram doc / explainer — **not** a formal company document. The v3 HTML machinery (`templates.md`, `strategies.md`, `components.md`, `depth-rules.md`) produces a self-contained single-page-scroll or 16:9 HTML file. Apply company tokens instead of the default blue CI when a company is specified.

In this mode the legacy Canvas conventions apply: Tailwind CDN + `:root` CSS variables (no block-level `<style>` or `<script>`); glassmorphism cards (`bg-white/70 backdrop-blur-md`, raise to `bg-white/90` on dark surfaces); `grid` containers add `items-start`; animate only `transform` / `opacity`; Lucide inline SVG (no emoji); Base64-embed images with `alt`; single-page is mobile-first from `grid-cols-1`. Color still comes only from tokens (same-hue opacity steps 4% / 8% / 12% / 20% / 100%); `[DATA_GAP]` callouts may use amber. None of this overrides the formal DOCX / deck / diagram rules above.

---

## 日本語 {#japanese}

> これらのルールは Canvas 層（Step 7 レンダリング / Step 6・Step 8 の Quality Gates）のハード制約です。Canvas は編集判断を行わず、トークンと以下のレイアウトルールを適用するだけです。主要成果物は正式な Word/PDF 取締役会資料、IR / CFO 提案、日本語・中国語の二言語文書、16:9 HTML/PDF デッキです。すべての色は企業トークンから取得します。ブランドが求めない限り青は使いません。

### 概要

成果物の種類、深度（S/M/L/XL）、言語モードに関わらず、以下のルールは常に有効です。トークンはデザインの記憶であり、これらのルールは Canvas がそれをどう使うかを定めます。企業トークンとここでのデフォルトが衝突する場合、企業トークンが優先されます。

### 1. 正式 DOCX/PDF レイアウト

取締役会資料、社内稟議文書、IR / CFO 提案、方針説明、日本の上場企業向け資料に使用。ユーザーが別途指定しない限り、以下のデフォルトを適用します。

| 要素 | サイズ | 備考 |
|------|--------|------|
| ページ | A4 縦、余白約18mm | 正式な取締役会資料のデフォルト |
| 本文 | 12pt、行間 1.15–1.2 | 上書き指定がない限り本文を12pt未満に縮小しない |
| 大見出し | 17–20pt | 章・部レベル |
| セクション見出し | 14–16pt | |
| サブセクション見出し | 12.5–13.5pt | |
| 表テキスト | 10.5–11.5pt | 高密度の表は下限寄り |
| キャプション / 注記 | 9.5–10pt | |

- 正式な取締役会資料では各章を改ページで開始します。
- 目次の項目は左揃え。ページ番号は視覚的に統一し、選択したスタイルに応じて中央または右タブ揃えにします。
- 表は控えめな罫線と企業アクセントのヘッダー塗りを使用。表はページ幅内に収め、セルを回転させず文字量を減らします。
- 見出し・罫線・表ヘッダー・小さなアクセントバーには企業プライマリーカラー、罫線と副次テキストにはニュートラルグレーを使用します。
- 過度な装飾ではなく、ウェイトと余白で明確な階層を作ります。
- 複雑な図には Word のフリーフォーム矢印を使わず、固定の SVG/PNG 画像としてレンダリングして DOCX に配置します。
- 図の多いページで折り返しの崩れやオブジェクトの重なりがないか確認します。

**フォント（トークンから）:** 日本語本文 Hiragino Sans、中国語本文 PingFang SC、ラテン / 数字 Aptos（または企業承認のラテンフォント）。DOCX の言語属性とフォントはロックされた出力言語に従います。

### 2. 日本語/中国語の分割文書

言語を分けて出力する場合：

- 日本語の DOCX/PDF と中国語の DOCX/PDF を1つずつ、それぞれ独立してレンダリングします。
- 固有名詞を除き、日本語出力に中国語の断片、中国語出力に日本語の断片を残しません。
- ページ構造、図表番号、表、セクション階層を言語間で並行させます。
- 言語別フォントを使用し、各ファイルで改行を個別に校正します。

### 3. 16:9 提案デッキレイアウト（HTML/PDF）

CFO 提案、IR デッキ、業務ブリーフィング、大画面レビューに使用。

基本前提：

- キャンバス：1920x1080 px。各スライドは固定ビューポートのセクション。
- `html { font-size: 20px; }` で 1rem = 20px。スライドテキストにはトークン化されたフォントサイズのみ使用します。
- 目標：1〜3m での会議室可読性と PDF エクスポート。
- 納品：可能な限り単一 HTML ファイルと PDF、ビルドなし。

スライドレイアウト：

- ヘッダーアクセントバー：企業プライマリーカラーで 6px。
- タイトル帯を上部付近、コンテンツ領域をその下、フッターを最下部に固定（約48px）。
- コンテンツパディングのスケール — デフォルト `40px 88px`、コンパクト `28px 72px`、タイト `20px 64px`。
- グリッドは 2〜6 列のみ。7 列以上は避けます。
- カードの実用最小幅は約 250px。角丸は控えめ（通常 6px 以下）。
- タイトルは簡潔に。タイトル帯を詰め込みすぎないこと。
- 本文ブロックはスライドを縦に充填します（`flex: 1`、引き伸ばした表、分割列、callout、注記を使用）。スカスカな内容を中央寄せして構造の代わりにせず、純粋な装飾背景を避けます。
- 最初のビューポートに企業 / 製品 / トピックを表示します。

印刷 / PDF：

```css
@page {
  size: 508mm 285.75mm;
  margin: 0;
}
```

- 印刷レイアウト調整に `transform: scale()` を**使わない**こと。
- 背景グラフィックを有効にして印刷します。
- エクスポート後に PDF のページ数とページサイズ（16:9）を検証します。PDF 印刷はブラウザ表示と一致させます。

### 4. 図表ルール

図は段落や表より多くを伝える場合のみ使用。許可される種類：プロセスフロー、資金フロー、アーキテクチャ図、タイムライン、マトリクス、組織ツリー、レイヤースタック、ウォーターフォール、シンプルな KPI チャート。

- 1スライド / ページセクションにつき主要な図は1つ。
- DOCX では図を SVG/PNG として作成し固定画像として挿入。HTML デッキでは自己完結型のインライン SVG を使用。
- パイプラインが確実に固定画像へ変換できない限り Mermaid は避けます。
- 可能な限りノード数を9未満に保ち、複雑な図は分割します。
- プライマリーカラーは最大1〜2個の焦点ノードにのみ使用。すべてのノードをブランドカラーにしないこと。通常ノードにはニュートラルな塗りと罫線を使用します。
- 矢印の端点はノードの辺に正確に接続します。
- 一貫した間隔の倍数、できれば 4px / 8px を使用します。
- 装飾アイコン、グロー、グラデーション、浮遊矢印、ブランド外の色を避けます。
- 資金フローでは、**アクターレーン、番号付きステップ、短い注記表**を伴う、すっきりした左→右または上→下のフローを優先します。

### 5. トークンとブランドカラーの規律

各企業はレンダリング前にトークンファイル（JSON または YAML）を取得します。トークンシステムが明示的に許可しない限り、色・フォント・サイズ・間隔をテンプレートにハードコードしません。

- **すべての色は企業のトークンから取得します。** 企業パレット外の色相の導入は禁止です。
- トークンセットが追加のセマンティックカラーを明示的に定義しない限り、企業プライマリーカラーを唯一の機能アクセントとして使用します。
- **ブランドが求めない限り青は使いません。** 同様に、ブランドが例えば赤 / グレーの場合、不用意な緑 / オレンジの機能色を避け、見出し・表・リンク・図・チャートから余計な青を取り除きます。
- プライマリーカラーは**控えめに** — 見出し、罫線、表ヘッダー、小さなアクセントバー、図の1〜2個の焦点ノードのみに使用します。
- 階層は**ウェイト、余白、ミュートテキスト**で作り、無秩序なフォントサイズや余分な色相で作らないこと。
- 色変数は `:root`（デッキ）またはトークンファイル（DOCX）に保持し、コンポーネント内のハードコード hex を避けます。

最小トークン形状（例の値 — 企業ごとに置換）：

```yaml
company:
  legal_name: "Acme Holdings, Inc."   # 例のみ
  ticker: "0000"
brand:
  primary: "#c0392b"        # 例の赤パレット — 企業の実トークンを使用
  text: "#242424"
  text_muted: "#666666"
  border: "#d9d9d9"
language:
  ja_font: "Hiragino Sans"
  zh_font: "PingFang SC"
  latin_font: "Aptos"
docx:
  page_size: "A4"
  body_pt: 12
  chapter_page_break: true
  toc_alignment: "left"
slides:
  canvas_px: [1920, 1080]
  base_font_px: 20
  print_page_mm: [508, 285.75]
```

### 6. Quality Gates（レイアウト）

最終納品前に実行します（Step 6 レイアウトレビュー、Step 8 PDF QA）：

- DOCX が修復警告なしで開く。PDF が最終 DOCX/HTML ソースからエクスポートされる。
- 上書き指定がない限り正式 Word 文書の本文は 12pt。見出しは上記のサイズ帯に従う。
- 目次の揃え（左）が正しい。必要な箇所で章が改ページから始まる。
- 表がページ余白を超えない。図が崩れ・切れ・不安定な Word 図形矢印で作られていない。
- ブランドが赤 / グレーのときに意図しない青 / 緑 / オレンジが現れない。
- 日本語 / 中国語の分割ファイルに正しい言語のみが含まれる。
- HTML デッキはブラウザのスクリーンショットと PDF エクスポートの両方でスライドがあふれない。PDF のページサイズが 16:9 で全ページが揃っている。
- 数値の忠実性：すべての数字・単位・通貨・会計期間がソースと一致。欠落は `[DATA_GAP]`、未検証の法務/税務記述は draft と明記。

ローカル確認に便利：`pdfinfo output.pdf`、`pdffonts output.pdf`。

### 7. HTML 出力モード（任意）

> 副次的・非デフォルト。HTML ビジュアル一枚物 / 図解ドキュメント / エクスプレイナー専用で、**正式な企業文書ではありません**。v3 HTML 機構（`templates.md`、`strategies.md`、`components.md`、`depth-rules.md`）は自己完結型のシングルページスクロールまたは 16:9 HTML ファイルを生成します。企業が指定された場合はデフォルトの青 CI ではなく企業トークンを適用します。

このモードではレガシー Canvas 規約が適用されます：Tailwind CDN + `:root` CSS 変数（ブロックレベル `<style>` や `<script>` なし）、グラスモーフィズムカード（`bg-white/70 backdrop-blur-md`、ダーク面では `bg-white/90` に上げる）、`grid` コンテナに `items-start` を追加、`transform` / `opacity` のみアニメーション、Lucide インライン SVG（絵文字なし）、Base64 埋め込み画像に `alt`、シングルページは `grid-cols-1` からのモバイルファースト。色は引き続きトークンのみから（同色相の透明度ステップ 4% / 8% / 12% / 20% / 100%）、`[DATA_GAP]` callout はアンバー可。これらは上記の正式 DOCX / デッキ / 図表ルールを上書きしません。

---

## 中文 {#chinese}

> 这些规则是 Canvas 层（Step 7 渲染 / Step 6 与 Step 8 的 Quality Gates）的硬性约束。Canvas 不做编辑决策，只负责应用 token 和以下版式规则。主要交付物为正式的 Word/PDF 董事会材料、IR / CFO 提案、日中双语文档以及 16:9 HTML/PDF 演示稿。所有颜色均来自公司 token。除非品牌要求，否则不使用蓝色。

### 概述

无论交付物类型、深度（S/M/L/XL）或语言模式如何，以下规则始终生效。Token 是设计记忆，这些规则规定 Canvas 如何使用它们。当公司 token 与此处默认值冲突时，以公司 token 为准。

### 1. 正式 DOCX/PDF 版式

用于董事会材料、内部审批文件、IR / CFO 提案、政策说明及日本上市公司材料。除非用户另行指定，应用以下默认值。

| 元素 | 尺寸 | 说明 |
|------|------|------|
| 页面 | A4 纵向，约18mm 页边距 | 正式董事会材料默认 |
| 正文 | 12pt，行距 1.15–1.2 | 无覆盖指定时不将正文缩至12pt以下 |
| 大标题 | 17–20pt | 章 / 部级别 |
| 章节标题 | 14–16pt | |
| 小节标题 | 12.5–13.5pt | |
| 表格文字 | 10.5–11.5pt | 高密度表格取下限 |
| 图注 / 注释 | 9.5–10pt | |

- 正式董事会材料中每一章另起一页。
- 目录条目左对齐；页码视觉统一，按所选样式居中或右制表位对齐。
- 表格使用克制的边框加公司强调色表头填充；将表格控制在页宽内，减少文字而非旋转单元格。
- 标题、分隔线、表头和小强调条使用公司主色，边框与次要文字使用中性灰。
- 通过字重与间距建立清晰层级，而非繁重装饰。
- 复杂图表不使用 Word 自由流程箭头，应渲染为固定 SVG/PNG 图片并置入 DOCX。
- 检查图表密集的页面是否存在折行错乱或对象重叠。

**字体（来自 token）：** 日文正文 Hiragino Sans；中文正文 PingFang SC；拉丁 / 数字 Aptos（或公司认可的拉丁字体）。DOCX 的语言属性与字体遵循已锁定的输出语言。

### 2. 日文/中文拆分文档

当用户要求分语言输出时：

- 分别生成一份日文 DOCX/PDF 和一份中文 DOCX/PDF，各自独立渲染。
- 除专有名词外，不在日文输出中残留中文片段，也不在中文输出中残留日文片段。
- 在不同语言间保持页面结构、图表编号、表格与章节层级平行。
- 使用各语言专用字体，并在每份文件中单独校对换行。

### 3. 16:9 提案演示稿版式（HTML/PDF）

用于 CFO 提案、IR 演示、运营简报和大屏审阅。

基本假设：

- 画布：1920x1080 px。每张幻灯片为固定视口区块。
- `html { font-size: 20px; }`，因此 1rem = 20px。幻灯片文字仅使用 token 化的字号。
- 目标：1–3m 会议室可读性及 PDF 导出。
- 交付：尽可能为单个 HTML 文件加 PDF，零构建。

幻灯片版式：

- 顶部强调条：使用公司主色，6px。
- 标题带靠上，内容区在下，页脚固定于底部（约48px）。
- 内容内边距档位 — 默认 `40px 88px`；紧凑 `28px 72px`；紧密 `20px 64px`。
- 网格仅 2 至 6 列；避免 7 列以上网格。
- 卡片实用最小宽度约 250px；圆角保持克制（通常 6px 或更小）。
- 标题简洁，不要塞满标题带。
- 正文区块纵向撑满幻灯片（使用 `flex: 1`、拉伸表格、分栏、callout、注释）。不要用居中稀疏内容代替真实结构，避免纯装饰背景。
- 在第一个视口中保持公司 / 产品 / 主题可见。

打印 / PDF：

```css
@page {
  size: 508mm 285.75mm;
  margin: 0;
}
```

- **不要**使用 `transform: scale()` 修正打印版式。
- 启用背景图形打印。
- 导出后核验 PDF 页数与页面尺寸（16:9）；PDF 打印须与浏览器渲染一致。

### 4. 图表规则

仅当图表比段落或表格传达更多信息时才使用。允许的类型：流程图、资金流向、架构图、时间线、矩阵、组织树、分层堆栈、瀑布图、简单 KPI 图。

- 每张幻灯片 / 页面区块只放一个主要图表。
- DOCX 中将图表制作为 SVG/PNG 并作为固定图片插入。HTML 演示稿中使用自包含的内联 SVG。
- 除非管线能可靠地将其转换为固定图片，否则避免使用 Mermaid。
- 尽量将节点数保持在 9 个以下；复杂图表予以拆分。
- 主色最多用于 1–2 个焦点节点，不要让每个节点都是品牌色。普通节点使用中性填充与边框。
- 箭头端点须精确落在节点边缘。
- 使用一致的间距倍数，最好为 4px / 8px。
- 避免装饰图标、辉光、渐变、浮动箭头和非品牌色。
- 资金流向优先采用带**角色泳道、编号步骤和简短注释表**的、清晰的从左到右或从上到下的流向。

### 5. Token 与品牌色规约

每家公司在渲染前获取一个 token 文件（JSON 或 YAML）。除非 token 系统明确允许，否则不将颜色、字体、尺寸或间距硬编码进模板。

- **所有颜色均来自公司 token。** 禁止引入公司色板外的色相。
- 除非 token 集明确定义了额外的语义色，否则将公司主色作为唯一的功能强调色。
- **除非品牌要求，否则不使用蓝色。** 同理，当品牌体系为如红 / 灰时，避免无意的绿 / 橙功能色，并从标题、表格、链接、图表和图形中移除多余的蓝色。
- 主色须**克制使用** — 仅用于标题、分隔线、表头、小强调条以及图表中 1–2 个焦点节点。
- 通过**字重、间距和弱化文字**建立层级，而非无序的字号或额外色相。
- 颜色变量保存在 `:root`（演示稿）或 token 文件（DOCX）中；避免在组件中硬编码 hex。

最小 token 结构（示例值 — 按公司替换）：

```yaml
company:
  legal_name: "Acme Holdings, Inc."   # 仅示例
  ticker: "0000"
brand:
  primary: "#c0392b"        # 示例红色板 — 使用公司真实 token
  text: "#242424"
  text_muted: "#666666"
  border: "#d9d9d9"
language:
  ja_font: "Hiragino Sans"
  zh_font: "PingFang SC"
  latin_font: "Aptos"
docx:
  page_size: "A4"
  body_pt: 12
  chapter_page_break: true
  toc_alignment: "left"
slides:
  canvas_px: [1920, 1080]
  base_font_px: 20
  print_page_mm: [508, 285.75]
```

### 6. Quality Gates（版式）

最终交付前执行（Step 6 版式审查、Step 8 PDF QA）：

- DOCX 打开时无修复警告；PDF 由最终 DOCX/HTML 源导出。
- 除非覆盖指定，正式 Word 文档正文为 12pt；标题遵循上述尺寸档。
- 目录对齐（左）正确；需要处章节另起一页。
- 表格不溢出页边距；图表未破损、裁切，或由不稳定的 Word 形状箭头拼成。
- 当品牌体系为红 / 灰时未出现意外的蓝 / 绿 / 橙。
- 日文 / 中文拆分文件仅包含正确语言。
- HTML 演示稿在浏览器截图与 PDF 导出中幻灯片均不溢出；PDF 页面尺寸为 16:9 且页数齐全。
- 数值保真：每个数字、单位、货币与财年均与来源一致；缺口标注 `[DATA_GAP]`；未核实的法务/税务表述标注 draft。

便捷的本地核验：`pdfinfo output.pdf`、`pdffonts output.pdf`。

### 7. HTML 输出模式（可选）

> 次要、非默认。仅用于 HTML 视觉单页 / 图解文档 / 说明页，而**非正式公司文档**。v3 HTML 机制（`templates.md`、`strategies.md`、`components.md`、`depth-rules.md`）生成自包含的单页滚动或 16:9 HTML 文件。指定公司时，应用公司 token 而非默认蓝色 CI。

此模式下沿用旧版 Canvas 约定：Tailwind CDN + `:root` CSS 变量（无 block 级 `<style>` 或 `<script>`）；玻璃拟态卡片（`bg-white/70 backdrop-blur-md`，深色表面提升至 `bg-white/90`）；`grid` 容器添加 `items-start`；仅动画 `transform` / `opacity`；Lucide 内联 SVG（无 emoji）；图片 Base64 内嵌并带 `alt`；单页为 `grid-cols-1` 起的移动优先。颜色仍仅来自 token（同色相透明度档 4% / 8% / 12% / 20% / 100%），`[DATA_GAP]` callout 可用 amber。这些均不覆盖上述正式 DOCX / 演示稿 / 图表规则。
