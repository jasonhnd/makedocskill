# Pipeline Design / パイプライン設計 / 管线设计

> Full Mode 8-step audited pipeline for company documents (Word / PDF / bilingual JP-ZH / 16:9 deck)

[EN](#english) · [日本語](#japanese) · [中文](#chinese)

---

## English {#english}

> The 8-step pipeline is make-doc-skill's execution skeleton, translating the Brain → Router → Canvas three-layer architecture into an auditable conversation flow for **formal company documents**: board materials, IR / CFO proposals, internal approval documents, bilingual Japanese/Chinese deliverables, and 16:9 HTML/PDF decks. HTML visual one-pagers are an optional secondary output mode, not the default path.

### Two Modes

| Mode | Trigger | Flow |
|------|---------|------|
| **Quick Mode** | User drops an existing source (Word/PDF/text) and wants a fast polished output, no project setup | Detect input → extract → infer real deliverable → apply company tokens (or sensible default) → Brain light pass → render DOCX/HTML → export PDF → report path |
| **Full Mode** | Board/IR material, bilingual delivery, or "build the document properly" | 8-step audited pipeline with intermediate files and per-step user checkpoints |

### Quick Mode — One-Shot Polish

Accepts an existing Word/PDF, pasted notes, or a Markdown outline. The fast path still enforces the non-negotiable anchoring rules:

1. **Input detection** — identify whether the source is a DOCX, PDF, outline, or pasted text, and infer the real deliverable (board / IR / CFO / explanation / deck).
2. **Content extraction** — read the source as material only; never overwrite the original file.
3. **Token application** — apply the company token set if known, otherwise a sensible default (example palette `#c0392b` red / gray, A4, 12pt body).
4. **Brain light pass** — tighten headings, fix line breaks and terminology, normalize tables. No fabricated figures.
5. **Numerical-fidelity + language-lock checks** — figures, units, currency, and fiscal periods stay exact; the chosen output language governs the whole render.
6. **Render + export** — generate DOCX/HTML, export PDF, report the output path (default `~/Downloads`).

Post-generation: offer "upgrade to Full Mode" — it keeps the normalized source and adds company tokens, sparring, review, and PDF QA.

### Full Mode — 8-Step Pipeline

The full pipeline consists of 8 steps. Each step writes a reviewable intermediate file into the project folder and ends with a user checkpoint: **proceed / redo this step / skip with company-token defaults / jump to render**. Skipping applies sensible defaults. This "step-by-step confirmation" design ensures intervention opportunities at every key decision point.

```
Step 1  Company tokens     → 01_company_tokens.md     Brand / language / DOCX / slide tokens (Router input)
Step 2  Document brief     → 02_document_brief.md     Deliverable type, audience, language mode, depth (S/M/L/XL), outputs, delivery folder
Step 3  Source normalized  → 03_source_normalized.md  Existing Word/PDF/text → structured MD/YAML; original quotes preserved; [DATA_GAP] marked
Step 4  Codex sparring     → 04_codex_sparring.md     3-dimension expert questioning, weak-point list, editorial decisions
Step 5  Composition plan   → 05_composition_plan.md   Section-by-section blueprint (8 fields), renderer + template choice
Step 6  Layout review      → 06_layout_review.md      Pre-render structure / quality / brand gate
Step 7  Render log         → 07_render_log.md         DOCX/HTML generated, decisions logged, PDF exported
Step 8  PDF QA             → 08_pdf_qa.md             pdfinfo / pdffonts + visual checks, gate results, final paths
```

### Step 1 — Company Tokens

Build or update the company token set as the Canvas-layer design memory (Router input). Capture brand identity (legal name, ticker, market, logo), brand colors (e.g. an example red palette `#c0392b` / gray — never blue unless the brand calls for it), language fonts (Japanese, Chinese, Latin, mono), DOCX rules (A4, 18mm margin, 12pt body, 1.18 line spacing, chapter page breaks, TOC alignment), and slide tokens (1920×1080 canvas, tokenized font sizes).

Three acquisition paths: A) company website / IR page, B) uploaded brand manual or existing branded document, C) verbal description ("use our corporate colors, not blue").

Output `01_company_tokens.md`. Keep company tokens separate from document content.

### Step 2 — Document Brief

Define the global parameters that govern the whole render chain.

| # | Field | Options | Impact |
|---|-------|---------|--------|
| 1 | Deliverable type | Board material / IR / CFO proposal / internal approval / business explanation / policy / deck | Output family and tone |
| 2 | Audience | Board / CFO / IR / operating team / partner / regulator / public investor | Language style and formality |
| 3 | Output format | Formal DOCX/PDF / 16:9 HTML/PDF deck / combined bilingual / split language files | Renderer and layout rules |
| 4 | Language mode | Japanese / Chinese / bilingual side-by-side / split JP+ZH | Full-chain **language lock** |
| 5 | Depth size | S / M / L / XL | Brain depth, sparring rounds, QA rigor |
| 6 | Source format | Existing Word/PDF / outline / pasted notes / bilingual draft | Step 3 normalization method |
| 7 | Compliance posture | Approved figures / draft assumptions / unverified legal-tax | Whether to mark `[Supplemental]` / draft |
| 8 | Delivery folder | Default `~/Downloads`, or a user-specified path | Handoff convention |

The output language set here **locks** the whole chain. Output `02_document_brief.md`.

### Step 3 — Source Normalized

Convert the existing Word/PDF/pasted text into a structured Markdown/YAML source. Preserve headings, tables, references, and legal/compliance wording. Keep original-language quotations intact; the normalized source preserves source language regardless of the output language. Annotate source credibility, identify logical relationships between materials, and mark missing data `[DATA_GAP]` rather than filling it. Output `03_source_normalized.md`.

### Step 4 — Codex Sparring (Expert Questioning)

Three-dimension expert questioning — this is the Codex Intelligence Layer challenging the draft, not just paraphrasing it:

| Dimension | Goal | Questions to force |
|-----------|------|--------------------|
| **Hypothesis challenge** | Test the core claim | Is the main claim defensible? Is the evidence primary data or assertion? What is the strongest counter-argument a board member or auditor would raise? |
| **Blind-spot completion** | Fill missing dimensions | What is missing — downside, risk, dilution, regulatory, tax, precedent, timeline? What will the audience ask that the draft does not answer? |
| **Perspective reconstruction** | Offer a better framing | Would risk-first / comparison-first / timeline-first framing serve this audience better than the current order? |

Sparring rounds by depth: S = 0–1, M = 1–2, L = 2–3, XL = 3+ (XL adds an extreme test: "what if the core assumption is wrong?").

Prohibited: vague filler, judgment avoidance, phenomenon-listing without causation, fabricated figures/citations/legal-tax conclusions. Mark unverified legal/accounting/tax statements as draft/assumption; mark missing data `[DATA_GAP]`. Output `04_codex_sparring.md`.

### Step 5 — Composition Plan

Router translates Brain's analysis into document structure — a section-by-section blueprint, not prose.

**5.1 Title confirmation**: propose message-type titles that convey the conclusion (e.g. a board topic such as a "mid-term management plan" framed as a decision, not just "Background").

**5.2 Renderer + template choice**: Router maps the deliverable type to an output family (formal DOCX / split bilingual / 16:9 deck / optional HTML) and selects the section schema, renderer, and template.

**5.3 Per-section definition** (8 fields per section): Title (message-type), Core message, Block/component type (heading / paragraph / table / callout / KPI row / diagram), Token / color allocation (accent used sparingly), Source reference, Logical relation, Layout hint, Information density (do not stack high-density sections consecutively).

**Color rule**: all colors from the company token set; the primary color is the only functional accent unless the token set defines additional semantic colors. No non-brand hues, no hardcoded values. Output `05_composition_plan.md`.

### Step 6 — Layout Review

Pre-render structure / quality / brand gate, run before generating the document:

**Layer 1 — Structure check**: Pyramid + MECE compliance, section count vs depth, logic chain, information-density balance.

**Layer 2 — Quality check**: message-type titles, audience perspective, terminology consistency, numerical-fidelity holds, source utilization.

**Layer 3 — Brand & format compliance**: brand tokens only (no unintended blue/green/orange when the brand is red/gray), language fonts correct, DOCX 12pt body, chapter page breaks, TOC alignment, table widths within margins, diagram rules.

Output `06_layout_review.md`.

### Step 7 — Render Log

Generate the real deliverable: render DOCX for formal documents or HTML for 16:9 decks first, then export PDF from that source (never hand-edit the PDF). Insert diagrams as fixed SVG/PNG images for DOCX, inline SVG for decks. Log key rendering decisions in-line so they remain traceable.

Pipeline transparency: report key choices in real time (deliverable inferred, structure rebuilt, renderer chosen, brand tokens applied, section/slide count, diagram count). Output `07_render_log.md` plus the rendered DOCX/HTML and exported PDF.

### Step 8 — PDF QA

Verify the real output surface. A DOCX is not done until the exported PDF is readable; a deck is not done until browser rendering and PDF export both look correct.

Run the Quality Gates: output exists in the requested folder, DOCX opens without repair warnings, fonts are readable and language-appropriate, body is 12pt, TOC alignment correct, chapters start on new pages, tables do not overflow, diagrams are clean, no non-brand colors leak, split JP/ZH files carry the correct language, page count matches TOC, deck PDFs are 16:9 with all pages present, and numerical fidelity holds.

Local verification commands:

```bash
pdfinfo "/path/to/output.pdf"
pdffonts "/path/to/output.pdf"
```

For visual inspection, render PDF pages to images or contact sheets and check title pages, diagram pages, dense tables, and the appendix. Output `08_pdf_qa.md` with gate results and the final delivery paths (default `~/Downloads`).

### Iteration Flow

When the user is unsatisfied: ask which step to redo, archive the current files to `_history/v[N]/`, re-execute from the selected step, and cascade-update all subsequent steps. The project root always holds the latest version, making rollback cheap.

### Pipeline Transparency Principles

1. **Traceable decisions**: every decision is recorded in its step file (`01_company_tokens.md` … `08_pdf_qa.md`).
2. **Auditable intermediates**: the user can pause, review, and modify at any step.
3. **Explainable process**: Brain proactively explains key choices in-line at each decision point.
4. **Low-cost rollback**: the iteration mechanism keeps modification costs controllable.

---

## 日本語 {#japanese}

> 8ステップパイプラインは make-doc-skill の実行骨格であり、Brain → Router → Canvas 三層アーキテクチャを**正式な企業文書**向けの監査可能な対話フローに変換します。対象は取締役会資料、IR / CFO 提案書、社内稟議書、日中バイリンガル成果物、16:9 HTML/PDF デッキです。HTML ビジュアル一枚ものは任意の副次出力モードであり、デフォルトの経路ではありません。

### 2つのモード

| モード | トリガー | フロー |
|--------|----------|--------|
| **Quick Mode** | 既存ソース（Word/PDF/テキスト）を渡し、プロジェクト設定なしで素早く仕上げたい | 入力検出 → 抽出 → 真の成果物を推論 → 企業トークン（または妥当なデフォルト）適用 → Brain ライトパス → DOCX/HTML レンダリング → PDF 書き出し → パス報告 |
| **Full Mode** | 取締役会/IR 資料、バイリンガル納品、または「文書をきちんと作る」 | 中間ファイルとステップ毎ユーザー確認を伴う8ステップ監査パイプライン |

### Quick Mode — ワンショット精修

既存の Word/PDF、貼り付けメモ、Markdown アウトラインを受け付けます。高速経路でも譲れないアンカリングルールを必ず適用します：

1. **入力検出** — ソースが DOCX / PDF / アウトライン / 貼り付けテキストかを識別し、真の成果物（取締役会 / IR / CFO / 説明 / デッキ）を推論。
2. **コンテンツ抽出** — ソースは素材としてのみ読み込み、元ファイルを上書きしない。
3. **トークン適用** — 既知なら企業トークン、未知なら妥当なデフォルト（例：赤系パレット `#c0392b` / グレー、A4、本文12pt）。
4. **Brain ライトパス** — 見出し・改行・用語を整え、表を正規化。数値の捏造は禁止。
5. **数値忠実性 + 言語ロックのチェック** — 数値・単位・通貨・会計期間は厳密に維持。選択した出力言語が全レンダリングを支配。
6. **レンダリング + 書き出し** — DOCX/HTML を生成、PDF を書き出し、出力パスを報告（デフォルト `~/Downloads`）。

生成後：「Full Mode へのアップグレード」を提案 — 正規化ソースを保持し、企業トークン・壁打ち・審査・PDF QA を追加。

### Full Mode — 8ステップパイプライン

パイプラインは8ステップで構成されます。各ステップはレビュー可能な中間ファイルをプロジェクトフォルダに書き出し、ユーザー確認で終了します：**続行 / このステップをやり直す / 企業トークンのデフォルトでスキップ / レンダリングへジャンプ**。スキップは妥当なデフォルトを適用。この「ステップ毎確認」設計により、各重要な意思決定ポイントで介入できます。

```
Step 1  企業トークン    → 01_company_tokens.md     ブランド / 言語 / DOCX / スライドトークン（Router 入力）
Step 2  文書ブリーフ    → 02_document_brief.md     成果物種別、対象、言語モード、深度（S/M/L/XL）、出力、納品フォルダ
Step 3  ソース正規化    → 03_source_normalized.md  既存 Word/PDF/テキスト → 構造化 MD/YAML；原文引用を保持；[DATA_GAP] 記載
Step 4  Codex 壁打ち    → 04_codex_sparring.md     三次元エキスパート質問、弱点リスト、編集判断
Step 5  構成プラン      → 05_composition_plan.md   セクション毎ブループリント（8フィールド）、レンダラ + テンプレート選択
Step 6  レイアウト審査  → 06_layout_review.md      レンダリング前の構造 / 品質 / ブランドゲート
Step 7  レンダリングログ→ 07_render_log.md         DOCX/HTML 生成、判断記録、PDF 書き出し
Step 8  PDF QA          → 08_pdf_qa.md             pdfinfo / pdffonts + 目視チェック、ゲート結果、最終パス
```

### Step 1 — 企業トークン

Canvas 層のデザインメモリ（Router 入力）として企業トークンセットを構築・更新。ブランド identity（法人名、ティッカー、市場、ロゴ）、ブランドカラー（例：赤系パレット `#c0392b` / グレー — ブランドが求めない限り青は使わない）、言語フォント（日本語・中国語・ラテン・等幅）、DOCX ルール（A4、余白18mm、本文12pt、行間1.18、章ごと改ページ、目次整列）、スライドトークン（1920×1080、トークン化フォントサイズ）を取得。

3つの取得経路：A) 企業サイト / IR ページ、B) アップロードされたブランドマニュアルまたは既存ブランド文書、C) 口頭説明（「当社のコーポレートカラーで、青は使わない」）。

`01_company_tokens.md` を出力。企業トークンは文書内容と分離して保持。

### Step 2 — 文書ブリーフ

全レンダリングチェーンを支配するグローバルパラメータを定義。

| # | フィールド | 選択肢 | 影響 |
|---|-----------|--------|------|
| 1 | 成果物種別 | 取締役会資料 / IR / CFO 提案 / 社内稟議 / 事業説明 / 方針 / デッキ | 出力ファミリーとトーン |
| 2 | 対象 | 取締役会 / CFO / IR / 運営チーム / パートナー / 規制当局 / 一般投資家 | 言語スタイルとフォーマリティ |
| 3 | 出力形式 | 正式 DOCX/PDF / 16:9 HTML/PDF デッキ / バイリンガル統合 / 言語別分割 | レンダラとレイアウトルール |
| 4 | 言語モード | 日本語 / 中国語 / バイリンガル併記 / 日中分割 | 全チェーン**言語ロック** |
| 5 | 深度サイズ | S / M / L / XL | Brain 深度、壁打ちラウンド、QA 厳格度 |
| 6 | ソース形式 | 既存 Word/PDF / アウトライン / 貼り付けメモ / バイリンガル草案 | Step 3 正規化方法 |
| 7 | コンプライアンス姿勢 | 承認済み数値 / 草案前提 / 未検証の法務・税務 | `[Supplemental]` / 草案表記の要否 |
| 8 | 納品フォルダ | デフォルト `~/Downloads`、またはユーザー指定パス | ハンドオフ規約 |

ここで設定した出力言語が全チェーンを**ロック**します。`02_document_brief.md` を出力。

### Step 3 — ソース正規化

既存の Word/PDF/貼り付けテキストを構造化 Markdown/YAML ソースに変換。見出し、表、参照、法務/コンプライアンス文言を保持。原文の引用はそのまま維持し、正規化ソースは出力言語にかかわらずソース言語を保持。ソース信頼度を注記し、素材間の論理関係を識別、欠落データは補わず `[DATA_GAP]` を記載。`03_source_normalized.md` を出力。

### Step 4 — Codex 壁打ち（エキスパート質問）

三次元エキスパート質問 — これは Codex Intelligence Layer が草案に挑戦するもので、単なる言い換えではありません：

| 次元 | 目標 | 強制する質問 |
|------|------|------------|
| **仮説挑戦** | コア主張を検証 | 主要主張は弁護可能か？証拠は一次データか主張か？取締役や監査人が挙げる最強の反論は何か？ |
| **盲点補完** | 欠落次元を補完 | 何が欠けているか — ダウンサイド、リスク、希薄化、規制、税務、先例、タイムライン？対象が問うが草案が答えていない点は？ |
| **視点再構成** | より良いフレーミングを提示 | リスク先行 / 比較先行 / 時系列先行のフレーミングが現在の順序より対象に適さないか？ |

深度別の壁打ちラウンド：S = 0–1、M = 1–2、L = 2–3、XL = 3+（XL は極限テストを追加：「コア仮説が誤っていたら？」）。

禁止：空虚な表現、判断回避、因果なしの現象列挙、数値/引用/法務・税務結論の捏造。未検証の法務/会計/税務記述は草案/前提と明記、欠落データは `[DATA_GAP]` を記載。`04_codex_sparring.md` を出力。

### Step 5 — 構成プラン

Router が Brain の分析を文書構造に翻訳 — 散文ではなくセクション毎ブループリント。

**5.1 タイトル確認**：結論を伝えるメッセージ型タイトルを提案（例：「中期経営計画」のような取締役会トピックを単なる「背景」ではなく意思決定として提示）。

**5.2 レンダラ + テンプレート選択**：Router が成果物種別を出力ファミリー（正式 DOCX / 日中分割 / 16:9 デッキ / 任意 HTML）にマッピングし、セクションスキーマ、レンダラ、テンプレートを選択。

**5.3 セクション毎定義**（セクション当たり8フィールド）：タイトル（メッセージ型）、コアメッセージ、ブロック/コンポーネント種別（見出し / 段落 / 表 / コールアウト / KPI 行 / 図表）、トークン / 色彩配分（アクセントは控えめに）、ソース参照、論理関係、レイアウトヒント、情報密度（高密度セクションを連続させない）。

**色彩ルール**：すべての色彩は企業トークンセットから。トークンセットが追加の意味色を定義しない限り、プライマリ色が唯一の機能アクセント。非ブランド色相禁止、ハードコード値禁止。`05_composition_plan.md` を出力。

### Step 6 — レイアウト審査

レンダリング前の構造 / 品質 / ブランドゲートを、文書生成前に実行：

**Layer 1 — 構造チェック**：ピラミッド + MECE 準拠、深度に対するセクション数、論理チェーン、情報密度バランス。

**Layer 2 — 品質チェック**：メッセージ型タイトル、対象視点、用語一貫性、数値忠実性の維持、ソース活用。

**Layer 3 — ブランド & 形式準拠**：ブランドトークンのみ（赤/グレーのブランドで意図しない青/緑/橙が出ない）、言語フォント正確、DOCX 本文12pt、章ごと改ページ、目次整列、表幅が余白内、図表ルール。

`06_layout_review.md` を出力。

### Step 7 — レンダリングログ

実際の成果物を生成：正式文書は DOCX、16:9 デッキは HTML を先にレンダリングし、そのソースから PDF を書き出す（PDF を手編集しない）。図表は DOCX では固定 SVG/PNG 画像、デッキではインライン SVG として挿入。主要なレンダリング判断をインラインで記録し追跡可能に保つ。

パイプライン透明性：主要な選択をリアルタイム報告（推論した成果物、再構築した構造、選択したレンダラ、適用したブランドトークン、セクション/スライド数、図表数）。`07_render_log.md` とレンダリング済み DOCX/HTML、書き出した PDF を出力。

### Step 8 — PDF QA

実際の出力面を検証。DOCX は書き出した PDF が読めるまで未完了。デッキはブラウザ表示と PDF 書き出しの両方が正しく見えるまで未完了。

Quality Gates を実行：出力が指定フォルダに存在、DOCX が修復警告なしで開く、フォントが読みやすく言語適切、本文12pt、目次整列、章が新ページで開始、表が溢れない、図表がクリーン、非ブランド色が漏れない、日中分割ファイルが正しい言語、ページ数が目次と一致、デッキ PDF が16:9で全ページ揃う、数値忠実性が維持。

ローカル検証コマンド：

```bash
pdfinfo "/path/to/output.pdf"
pdffonts "/path/to/output.pdf"
```

目視検査では PDF ページを画像またはコンタクトシートにレンダリングし、タイトルページ、図表ページ、密な表、付録を確認。ゲート結果と最終納品パス（デフォルト `~/Downloads`）を含む `08_pdf_qa.md` を出力。

### イテレーションフロー

ユーザーが不満な場合：どのステップからやり直すか確認、現在のファイルを `_history/v[N]/` にアーカイブ、選択ステップから再実行し後続すべてのステップをカスケード更新。プロジェクトルートは常に最新バージョンを保持し、ロールバックを低コストに保つ。

### パイプライン透明性原則

1. **追跡可能な決定**：各決定はステップファイル（`01_company_tokens.md` … `08_pdf_qa.md`）に記録。
2. **監査可能な中間生成物**：ユーザーは任意のステップで一時停止、審査、修正可能。
3. **説明可能なプロセス**：Brain が各意思決定ポイントで主要な選択をインラインで能動的に説明。
4. **低コストロールバック**：イテレーションメカニズムで修正コストを制御可能。

---

## 中文 {#chinese}

> 8 步管线是 make-doc-skill 的执行骨架，将 Brain → Router → Canvas 三层架构落地为面向**正式企业文档**的可审计对话流程：董事会材料、IR / CFO 提案、内部审批文件、中日双语成果物，以及 16:9 HTML/PDF 演示稿。HTML 视觉单页是可选的次要输出模式，而非默认路径。

### 两种模式

| 模式 | 触发条件 | 流程 |
|------|---------|------|
| **Quick Mode** | 用户丢入既有源文件（Word/PDF/文本），想快速精修、无需建项目 | 检测输入 → 提取 → 推断真实成果物 → 套用公司令牌（或合理默认）→ Brain 轻量遍历 → 渲染 DOCX/HTML → 导出 PDF → 报告路径 |
| **Full Mode** | 董事会/IR 材料、双语交付，或"把文档好好做出来" | 带中间文件与逐步用户确认的 8 步审计管线 |

### Quick Mode — 一键精修

接受既有 Word/PDF、粘贴笔记或 Markdown 大纲。快速路径仍强制执行不可让步的锚定规则：

1. **输入检测** — 识别源是 DOCX / PDF / 大纲 / 粘贴文本，并推断真实成果物（董事会 / IR / CFO / 说明 / 演示稿）。
2. **内容提取** — 仅将源作为素材读取，绝不覆盖原文件。
3. **令牌套用** — 已知则套用公司令牌，未知则用合理默认（示例：红色调色板 `#c0392b` / 灰，A4，正文 12pt）。
4. **Brain 轻量遍历** — 收紧标题、修正换行与术语、规范表格。禁止捏造数字。
5. **数值保真 + 语言锁定检查** — 数字、单位、币种、财务期间保持精确；所选输出语言支配整条渲染链。
6. **渲染 + 导出** — 生成 DOCX/HTML，导出 PDF，报告输出路径（默认 `~/Downloads`）。

生成后：提示"升级到 Full Mode" — 保留规范化源，追加公司令牌、壁打ち、审查与 PDF QA。

### Full Mode — 8 步管线

管线由 8 个步骤组成。每一步将一个可审阅的中间文件写入项目文件夹，并以用户确认结束：**继续 / 重做本步 / 用公司令牌默认跳过 / 跳到渲染**。跳过时套用合理默认。这种「步步确认」设计确保用户在每个关键决策点都有介入机会。

```
Step 1  公司令牌      → 01_company_tokens.md     品牌 / 语言 / DOCX / 幻灯片令牌（Router 输入）
Step 2  文档简报      → 02_document_brief.md     成果物类型、受众、语言模式、深度（S/M/L/XL）、输出、交付文件夹
Step 3  源规范化      → 03_source_normalized.md  既有 Word/PDF/文本 → 结构化 MD/YAML；保留原文引用；标注 [DATA_GAP]
Step 4  Codex 壁打ち  → 04_codex_sparring.md     三维度专家追问、弱点清单、编辑决策
Step 5  构成方案      → 05_composition_plan.md   逐节蓝图（8 字段）、渲染器 + 模板选择
Step 6  版式审查      → 06_layout_review.md      渲染前的结构 / 品质 / 品牌门检
Step 7  渲染日志      → 07_render_log.md         DOCX/HTML 已生成、决策记录、PDF 已导出
Step 8  PDF QA        → 08_pdf_qa.md             pdfinfo / pdffonts + 目视检查、门检结果、最终路径
```

### Step 1 — 公司令牌

构建或更新公司令牌集，作为 Canvas 层的设计记忆（Router 输入）。采集品牌标识（法定名称、股票代码、市场、Logo）、品牌色（例如红色调色板 `#c0392b` / 灰 — 除非品牌要求否则不用蓝色）、语言字体（日文、中文、拉丁、等宽）、DOCX 规则（A4、页边距 18mm、正文 12pt、行距 1.18、章节分页、目录对齐），以及幻灯片令牌（1920×1080 画布、令牌化字号）。

三种获取途径：A) 公司网站 / IR 页面，B) 上传的品牌手册或既有品牌文档，C) 口头说明（"用我们的企业色，不要蓝色"）。

输出 `01_company_tokens.md`。公司令牌与文档内容分离保存。

### Step 2 — 文档简报

定义支配整条渲染链的全局参数。

| # | 字段 | 选项 | 影响 |
|---|------|------|------|
| 1 | 成果物类型 | 董事会材料 / IR / CFO 提案 / 内部审批 / 业务说明 / 方针 / 演示稿 | 输出族系与基调 |
| 2 | 受众 | 董事会 / CFO / IR / 运营团队 / 伙伴 / 监管 / 公众投资人 | 用语风格与正式度 |
| 3 | 输出形式 | 正式 DOCX/PDF / 16:9 HTML/PDF 演示稿 / 双语合并 / 分语言文件 | 渲染器与版式规则 |
| 4 | 语言模式 | 日文 / 中文 / 双语并排 / 中日分拆 | 全链路**语言锁定** |
| 5 | 深度尺寸 | S / M / L / XL | Brain 深度、壁打ち轮数、QA 严格度 |
| 6 | 源格式 | 既有 Word/PDF / 大纲 / 粘贴笔记 / 双语草稿 | Step 3 规范化方式 |
| 7 | 合规姿态 | 已批准数字 / 草案假设 / 未核实法务税务 | 是否标注 `[Supplemental]` / 草案 |
| 8 | 交付文件夹 | 默认 `~/Downloads`，或用户指定路径 | 交接约定 |

此处设定的输出语言**锁定**整条链路。输出 `02_document_brief.md`。

### Step 3 — 源规范化

将既有 Word/PDF/粘贴文本转换为结构化 Markdown/YAML 源。保留标题、表格、引用以及法务/合规措辞。原文引用原样保留；规范化源无论输出语言如何都保留源语言。标注来源可信度，识别素材间逻辑关系，缺失数据不填补而标注 `[DATA_GAP]`。输出 `03_source_normalized.md`。

### Step 4 — Codex 壁打ち（专家追问）

三维度专家追问 — 这是 Codex Intelligence Layer 在挑战草案，而非简单改写：

| 维度 | 目标 | 强制追问 |
|------|------|---------|
| **假设挑战** | 检验核心主张 | 主要主张可辩护吗？证据是一手数据还是断言？董事或审计会提出的最强反驳是什么？ |
| **盲点补全** | 填补缺失维度 | 缺了什么 — 下行、风险、稀释、监管、税务、先例、时间线？受众会问而草案未答的是什么？ |
| **视角重构** | 给出更佳框架 | 风险优先 / 对比优先 / 时间线优先的框架是否比当前顺序更适合该受众？ |

按深度的壁打ち轮数：S = 0–1，M = 1–2，L = 2–3，XL = 3+（XL 增加极端测试："若核心假设是错的？"）。

禁止：空泛表述、回避判断、无因果的现象罗列、捏造数字/引用/法务税务结论。未核实的法务/会计/税务陈述须标为草案/假设，缺失数据标注 `[DATA_GAP]`。输出 `04_codex_sparring.md`。

### Step 5 — 构成方案

Router 将 Brain 的分析翻译为文档结构 — 逐节蓝图而非散文。

**5.1 标题确认**：提出传递结论的消息型标题（例如把"中期经营计划"这类董事会议题表述为一项决策，而非仅"背景"）。

**5.2 渲染器 + 模板选择**：Router 将成果物类型映射到输出族系（正式 DOCX / 中日分拆 / 16:9 演示稿 / 可选 HTML），并选定节结构、渲染器与模板。

**5.3 逐节定义**（每节 8 字段）：标题（消息型）、核心信息、块/组件类型（标题 / 段落 / 表格 / 标注 / KPI 行 / 图表）、令牌 / 色彩分配（点缀色克制使用）、素材参照、逻辑关系、版式提示、信息密度（不连续堆叠高密度节）。

**色彩规律**：全部色彩来自公司令牌集；除非令牌集定义额外语义色，否则主色是唯一功能点缀色。禁止非品牌色相、禁止硬编码色值。输出 `05_composition_plan.md`。

### Step 6 — 版式审查

在生成文档前运行渲染前的结构 / 品质 / 品牌门检：

**Layer 1 — 结构检查**：金字塔 + MECE 准据、深度对应的节数、逻辑链、信息密度平衡。

**Layer 2 — 品质检查**：消息型标题、受众视角、术语一致性、数值保真维持、素材活用。

**Layer 3 — 品牌与格式合规**：仅用品牌令牌（红/灰品牌不出现意外的蓝/绿/橙）、语言字体正确、DOCX 正文 12pt、章节分页、目录对齐、表格宽度在页边距内、图表规则。

输出 `06_layout_review.md`。

### Step 7 — 渲染日志

生成真实成果物：正式文档先渲染 DOCX，16:9 演示稿先渲染 HTML，再从该源导出 PDF（不手改 PDF）。图表在 DOCX 中作为固定 SVG/PNG 图片插入，在演示稿中作为内联 SVG。将关键渲染决策内联记录以保持可追溯。

管线透明度：实时报告关键选择（推断的成果物、重构的结构、所选渲染器、套用的品牌令牌、节/页数、图表数）。输出 `07_render_log.md` 以及渲染好的 DOCX/HTML 和导出的 PDF。

### Step 8 — PDF QA

验证真实输出面。DOCX 在导出的 PDF 可读之前不算完成；演示稿在浏览器渲染与 PDF 导出都正确之前不算完成。

运行 Quality Gates：输出存在于指定文件夹、DOCX 无修复警告地打开、字体可读且语言适配、正文 12pt、目录对齐、章节另起新页、表格不溢出、图表干净、非品牌色不外泄、中日分拆文件语言正确、页数与目录一致、演示稿 PDF 为 16:9 且页面齐全、数值保真维持。

本地验证命令：

```bash
pdfinfo "/path/to/output.pdf"
pdffonts "/path/to/output.pdf"
```

目视检查时将 PDF 页渲染为图片或联系表，核对标题页、图表页、密集表格与附录。输出 `08_pdf_qa.md`，含门检结果与最终交付路径（默认 `~/Downloads`）。

### 迭代流程

用户不满意时：询问从哪个步骤开始重做，将当前文件移入 `_history/v[N]/`，从选定步骤开始重新执行，选定步骤之后的全部步骤自动级联更新。项目根目录始终保持最新版本，使回滚低成本。

### 管线透明度原则

1. **决策可追溯**：每个决策都记录在其步骤文件中（`01_company_tokens.md` … `08_pdf_qa.md`）。
2. **中间产物可审**：用户可以在任何步骤暂停、审查、修改。
3. **过程可解释**：Brain 在每个决策点主动内联解释关键选择。
4. **回滚低成本**：迭代机制让修改成本可控。
