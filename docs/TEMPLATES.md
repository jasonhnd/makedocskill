# 18 Visual Template Reference / 18種ビジュアルテンプレート参考 / 18 种视觉模板参考

> **[HTML output mode — optional]** make-doc-skill's primary path is company document generation (Word/PDF/bilingual board materials; see `../SKILL.md`). These 18 HTML visual templates apply only when the deliverable is an HTML visual document or 16:9 HTML deck.

> Based on EIP (Explain In Picture) project documentation

[EN](#english) · [日本語](#japanese) · [中文](#chinese)

---

## English {#english}

> Based on EIP (Explain In Picture) project documentation migration. Original source: EIP SKELETON_DESIGN_RULES.md.

Each template defines Tailwind class-level skeleton rules. HTML generation (Step 7) must strictly follow these.

### 1. Dashboard — Bento-box KPI Dashboard

**Purpose**: Data-intensive summary. Suitable for KPI aggregation, operational overview, multi-metric monitoring.

**Layout Logic**:
- Container: `grid grid-cols-1 md:grid-cols-3 lg:grid-cols-4 gap-4 md:gap-6`
- KPI cards: `text-3xl font-bold` large numbers + small labels
- Mixed column spans: `col-span-1` / `col-span-2` / `col-span-3` to break uniform grids
- Progress indicators: CSS progress bars (not JS charts)

**Visual Characteristics**:
- Bento-box style, cards of varying sizes
- Numbers first, text secondary
- Color uses opacity to differentiate hierarchy (CI primary 4%/8%/12%/20%)

**Applicable Strategies**: `general`(primary), `product`, `ecommerce`, `travel`, `real-estate`, `sports`, `data-analysis`

### 2. Versus — Comparison Analysis

**Purpose**: A vs B comparison. Suitable for solution comparison, competitive analysis, pros/cons analysis.

**Layout Logic**:
- Container: `grid grid-cols-1 md:grid-cols-2 gap-8`
- Left-right color differentiation: CI primary tint vs secondary tint
- Pros/cons lists: `lucide-check` (pro) / `lucide-x` (con) icons
- Combined comparison table: `col-span-2` full-width bottom summary

**Visual Characteristics**:
- Symmetrical left-right layout with contrasting colors
- Each side has independent titles and metrics
- Bottom summary breaks the binary, providing a comprehensive judgment

**Applicable Strategies**: `opinion`, `review`, `ecommerce`

### 3. Timeline — Timeline

**Purpose**: Development history, phase breakdown, milestone narrative.

**Layout Logic**:
- Center axis: `absolute left-4 md:left-1/2 w-1 bg-gradient-to-b` (CI color gradient)
- Alternating layout: `md:flex-row` / `md:flex-row-reverse` alternating left and right
- Date badges: Circular or rectangular, CI primary background

**Visual Characteristics**:
- Vertical center axis running through the entire document
- Nodes alternate left and right to avoid monotony
- Mobile fallback to left axis + right content

**Applicable Strategies**: `breaking-news`, `event`, `video`, `social-thread`, `interview`, `podcast`

### 4. Article — Long-form Reading

**Purpose**: News coverage, in-depth commentary, narrative content.

**Layout Logic**:
- Hero area: `text-4xl md:text-6xl font-black`
- Body container: `max-w-3xl mx-auto space-y-6`
- Quote blocks: `border-l-4 pl-6 text-xl italic`
- Image-text alternation: `flex md:flex-row gap-8`
- Footnote area

**Visual Characteristics**:
- Narrow column reading experience, magazine-style layout
- Hero area with large title for impactful opening
- Quote blocks and image-text alternation break text walls

**Applicable Strategies**: `breaking-news`(primary), `opinion`, `video`, `social-thread`, `press-release`, `interview`, `podcast`, `announcement`

### 5. Steps — Numbered Steps

**Purpose**: Tutorials, operation manuals, process guides.

**Layout Logic**:
- Step circles: `w-10 h-10 rounded-full bg-[CI primary] text-white` centered number
- Connectors: `border-l-2 border-dashed ml-5 h-8` dashed line connection
- Per-step content: Title + body + optional code block

**Visual Characteristics**:
- Clear step numbering with strong visual guidance
- Dashed connectors emphasize sequential relationships
- Each step can include code blocks, screenshots, and other supporting content

**Applicable Strategies**: `tutorial`(primary), `tech-doc`, `recipe`, `health`, `case-study`

### 6. Report — Structured Report

**Purpose**: Research reports, financial analysis, professional documents.

**Layout Logic**:
- Summary area: `bg-[CI primary]/5 border-l-4 rounded-r-lg p-6`
- Numbered chapters + sidebar number callouts: `sticky top-4 text-3xl font-black`
- Data tables + recommendation area

**Visual Characteristics**:
- Formal document feel with clear numbered chapter structure
- Summary area highlights core findings
- Sidebar number callouts enhance data readability

**Applicable Strategies**: `research`(primary), `finance`, `legal-policy`, `case-study`, `whitepaper`, `general`

### 7. Matrix — Evaluation Matrix

**Purpose**: Multi-dimensional assessment, solution scoring, decision support.

**Layout Logic**:
- Horizontal dimensions x vertical options scoring grid
- Color-scale cells: CI color opacity represents score levels
- Weighted ranking table + recommendation highlight

**Visual Characteristics**:
- Grid-based scoring at a glance
- Color depth directly reflects score levels
- Recommended items have visual emphasis

**Applicable Strategies**: `research`, `whitepaper`, `data-analysis`

### 8. Profile — Entity Profile

**Purpose**: Product introduction, company overview, person/brand profile.

**Layout Logic**:
- Hero banner + name: `text-4xl font-black`
- Core metrics horizontal bar: 3-6 KPIs
- Section card grid: `grid grid-cols-1 md:grid-cols-2 gap-6`

**Visual Characteristics**:
- Large banner opening establishes visual identity
- Core metrics in a horizontal row for quick key data delivery
- Section cards carry detailed information

**Applicable Strategies**: `product`(primary), `job-posting`, `startup`

### 9. Flowchart — Decision Flow

**Purpose**: Decision process visualization, system flowcharts.

**Layout Logic**:
- Node cards + CSS arrow connectors
- Branch area: `grid grid-cols-2 md:grid-cols-3`
- Start node: Circular
- Decision node: Emphasized border
- End node: Circular

**Visual Characteristics**:
- Pure CSS implementation (no JS chart libraries)
- Node shapes distinguish types
- Arrow connections clearly express flow direction

**Applicable Strategies**: `tech-doc`

### 10. Scorecard — Rating Card

**Purpose**: Reviews, ratings, scoring displays.

**Layout Logic**:
- Total score: `text-6xl font-black` + circular progress
- Each dimension: Horizontal progress bars (color scale indicates quality)
- Pros/cons comparison: `grid grid-cols-2` + left color bar

**Visual Characteristics**:
- Large number total score opening
- Dimension scores shown intuitively with progress bars
- Pros/cons lists provide qualitative supplementary judgment

**Applicable Strategies**: `review`(primary), `ecommerce`, `finance`, `sports`, `real-estate`

### 11. Pitch — Narrative Landing Page

**Purpose**: Strategic proposals, product pitch, persuasive narrative.

**Layout Logic**:
- Full-screen taglines: `text-5xl md:text-7xl font-black`
- Argument area: `grid grid-cols-1 md:grid-cols-2 gap-12`
- CTA button: `px-8 py-4 bg-[CI primary] text-white rounded-full`

**Visual Characteristics**:
- Large-format taglines, one core message per screen
- Argument area provides supporting data
- Final CTA drives action

**Applicable Strategies**: `startup`(primary), `opinion`, `press-release`

### 12. Infographic — Vertical Infographic

**Purpose**: Data analysis visualization, statistical data presentation.

**Layout Logic**:
- Large numbers: `text-6xl md:text-8xl font-black text-[CI primary]`
- Icon + text: `flex items-start gap-6`
- Gradient segmented backgrounds
- Trend arrows

**Visual Characteristics**:
- Especially large numbers for strong visual impact
- Vertical scrolling with independent background colors per segment
- Trend arrows and directional indicators strengthen data narrative

**Applicable Strategies**: `data-analysis`(primary), `research`, `case-study`, `whitepaper`, `sports`

### 13. Comparison Table — Feature Comparison Table

**Purpose**: Product comparison, specification comparison, multi-solution evaluation.

**Layout Logic**:
- Container: `overflow-x-auto` + `<table>` tags
- Supported/unsupported: `lucide-check` / `lucide-x` icons
- Recommended column: `border-2 border-[CI primary]` highlight
- Zebra stripe row backgrounds

**Visual Characteristics**:
- Standard table layout with high information density
- Recommended column has visual emphasis
- Mobile horizontal scrolling supported

**Applicable Strategies**: `ecommerce`, `product`, `review`, `job-posting`

### 14. FAQ — Collapsible Q&A

**Purpose**: Frequently asked questions, knowledge base, Q&A compilation.

**Layout Logic**:
- Collapsible component: `<details>` + grouped tabs
- Question row: `bg-[surface] cursor-pointer` + chevron icon
- Answer area: `border-l-2 border-[CI primary]/30`

**Visual Characteristics**:
- Collapse/expand interaction (pure HTML, no JS)
- Grouped tabs organize large amounts of Q&A
- Left color bar marks answer area

**Applicable Strategies**: `tutorial`, `tech-doc`, `legal-policy`, `recipe`, `health`

### 15. Slide — 16:9 Slide Deck

**Purpose**: Team presentations, PDF output, projection display.

**Layout Logic**:
- Fixed dimensions: 1280x720px
- Per page: `page-break-after: always`
- Page numbers: Bottom right
- CI color bar: Bottom 4px
- Cover: CI secondary dark background
- Content area: flex fill

**Visual Characteristics**:
- Strict 16:9 aspect ratio
- Automatic page breaks when printing
- Cover page dark background, content pages light background
- Bottom color bar for unified brand feel

**Applicable Strategies**: `video`, and any scenario requiring slide output

### 16. Iceberg — Surface vs Deep

**Purpose**: Root cause analysis, appearance vs essence, iceberg model.

**Layout Logic**:
- Top 30%: Visible surface (light background)
- Horizontal line separator
- Bottom 70%: Deep structure (progressively deeper tints)
- Visual weight proportional to depth

**Visual Characteristics**:
- Iceberg metaphor, light on top, heavy on bottom
- Colors deepen with depth
- Separator line clearly marks the "waterline"

**Applicable Strategies**: Suitable for any analysis distinguishing appearance from root cause

### 17. Funnel — Conversion Funnel

**Purpose**: Conversion analysis, screening process, progressive narrowing.

**Layout Logic**:
- Decreasing width: `max-w-4xl` → `3xl` → `2xl` → `xl`
- Each layer has conversion/elimination metrics
- Background color deepens as funnel narrows
- Bottom final output highlighted

**Visual Characteristics**:
- Visually wide to narrow
- Each layer annotated with conversion rate
- Deeper color indicates closer to final goal

**Applicable Strategies**: Suitable for any conversion funnel scenario

### 18. Bridge — Transformation Path

**Purpose**: Change proposals, path planning from current state to target.

**Layout Logic**:
- Three-area layout: `grid grid-cols-1 md:grid-cols-[1fr_2fr_1fr]`
  - LEFT: Current state
  - CENTER: Transformation path (3-5 steps)
  - RIGHT: Target
- Key turning points with emphasis styling

**Visual Characteristics**:
- Left-to-right narrative flow
- Center transformation path is the visual focus
- Current state and target form a contrast

**Applicable Strategies**: Suitable for any change/transformation proposal

### Strategy → Template Complete Mapping Table

| Strategy | Primary | Alt 1 | Alt 2 |
|----------|---------|-------|-------|
| breaking-news | Article | Timeline | Dashboard |
| opinion | Article | Versus | Pitch |
| product | Profile | Dashboard | Comparison Table |
| ecommerce | Comparison Table | Scorecard | Dashboard |
| tutorial | Steps | FAQ | Timeline |
| tech-doc | Steps | Flowchart | Report |
| research | Report | Infographic | Matrix |
| finance | Report | Scorecard | Dashboard |
| legal-policy | Report | FAQ | Article |
| video | Article | Timeline | Slide |
| social-thread | Article | Timeline | Dashboard |
| general | Dashboard | Article | Report |
| press-release | Article | Dashboard | Pitch |
| case-study | Report | Steps | Infographic |
| whitepaper | Report | Infographic | Matrix |
| data-analysis | Infographic | Dashboard | Matrix |
| review | Scorecard | Versus | Comparison Table |
| interview | Article | Timeline | Report |
| event | Timeline | Dashboard | Steps |
| job-posting | Profile | Comparison Table | Dashboard |
| recipe | Steps | FAQ | Report |
| travel | Dashboard | Timeline | Infographic |
| health | Steps | FAQ | Report |
| real-estate | Dashboard | Scorecard | Report |
| startup | Pitch | Profile | Report |
| podcast | Article | Timeline | Report |
| announcement | Article | Dashboard | Report |
| sports | Scorecard | Timeline | Infographic |

### Template Selection Principles

1. **Router auto-recommendation**: In Step 5, Router layer automatically recommends the primary template based on Brain analysis results
2. **User can override**: Recommendations are for reference only; users can choose any template
3. **Primary preferred**: Unless there is a clear reason, prefer the primary template
4. **Mixed usage**: Complex documents can mix components from different templates within different Sections
5. **CI first**: Regardless of which template is used, CI specification (colors, fonts, border-radius, shadows) always takes priority

---

## 日本語 {#japanese}

> EIP (Explain In Picture) プロジェクトドキュメントからの移行。元ソース：EIP SKELETON_DESIGN_RULES.md。

各テンプレートは Tailwind class レベルの骨格ルールを定義しています。HTML 生成時（Step 7）は厳格に遵守する必要があります。

### 1. Dashboard — Bento-box KPI ダッシュボード

**用途**：データ密度の高い概要。KPI 集計、運営概観、複数指標モニタリングに適合。

**レイアウトロジック**：
- コンテナ：`grid grid-cols-1 md:grid-cols-3 lg:grid-cols-4 gap-4 md:gap-6`
- KPI カード：`text-3xl font-bold` 大きな数字 + 小さなラベル
- 混合カラムスパン：`col-span-1` / `col-span-2` / `col-span-3` で均一グリッドを崩す
- 進捗インジケーター：CSS プログレスバー（JS チャートではない）

**ビジュアル特徴**：
- Bento-box スタイル、サイズの異なるカードの組み合わせ
- 数字優先、テキスト補助
- CI メインカラーの透明度で階層を区別（4%/8%/12%/20%）

**適用戦略**：`general`（第一推薦）、`product`、`ecommerce`、`travel`、`real-estate`、`sports`、`data-analysis`

### 2. Versus — 対比分析

**用途**：A vs B の比較。方案比較、競合分析、長所短所分析に適合。

**レイアウトロジック**：
- コンテナ：`grid grid-cols-1 md:grid-cols-2 gap-8`
- 左右の色調区分：CI メインカラー tint vs 補助カラー tint
- 長所短所リスト：`lucide-check`（長所）/ `lucide-x`（短所）アイコン
- 統合比較表：`col-span-2` フル幅の下部サマリー

**ビジュアル特徴**：
- 左右対称レイアウト、色彩コントラストが鮮明
- 各側に独立したタイトルと指標
- 下部サマリーが二分法を破り、総合判断を提示

**適用戦略**：`opinion`、`review`、`ecommerce`

### 3. Timeline — タイムライン

**用途**：発展史、フェーズ分解、マイルストーン物語。

**レイアウトロジック**：
- 中心軸線：`absolute left-4 md:left-1/2 w-1 bg-gradient-to-b`（CI カラーグラデーション）
- 交互配置：`md:flex-row` / `md:flex-row-reverse` で左右交互
- 日付バッジ：円形または矩形、CI メインカラー背景

**ビジュアル特徴**：
- 垂直中心軸線が文書全体を貫通
- ノードが左右交互で単調さを回避
- モバイルでは左側軸線 + 右側コンテンツにフォールバック

**適用戦略**：`breaking-news`、`event`、`video`、`social-thread`、`interview`、`podcast`

### 4. Article — 長文読み物

**用途**：ニュース報道、深度コメンタリー、ナラティブコンテンツ。

**レイアウトロジック**：
- Hero エリア：`text-4xl md:text-6xl font-black`
- 本文コンテナ：`max-w-3xl mx-auto space-y-6`
- 引用ブロック：`border-l-4 pl-6 text-xl italic`
- 画像テキスト交互：`flex md:flex-row gap-8`
- 脚注エリア

**ビジュアル特徴**：
- 狭いカラムの読書体験、雑誌風レイアウト
- Hero エリアの大タイトルでインパクトのあるオープニング
- 引用ブロックと画像テキスト交互がテキストの壁を破る

**適用戦略**：`breaking-news`（第一推薦）、`opinion`、`video`、`social-thread`、`press-release`、`interview`、`podcast`、`announcement`

### 5. Steps — 番号付きステップ

**用途**：チュートリアル、操作マニュアル、プロセスガイド。

**レイアウトロジック**：
- ステップ円：`w-10 h-10 rounded-full bg-[CI メインカラー] text-white` 中央に数字
- コネクター：`border-l-2 border-dashed ml-5 h-8` 破線接続
- 各ステップ内容：タイトル + 本文 + オプションのコードブロック

**ビジュアル特徴**：
- 明確なステップ番号、視覚的ガイダンスが強い
- 破線コネクターが順序関係を強調
- 各ステップにコードブロック、スクリーンショットなどの補助コンテンツを含められる

**適用戦略**：`tutorial`（第一推薦）、`tech-doc`、`recipe`、`health`、`case-study`

### 6. Report — 構造化レポート

**用途**：研究レポート、財務分析、専門文書。

**レイアウトロジック**：
- サマリーエリア：`bg-[CI メインカラー]/5 border-l-4 rounded-r-lg p-6`
- 番号付き章 + サイドバー数値コールアウト：`sticky top-4 text-3xl font-black`
- データテーブル + 推奨エリア

**ビジュアル特徴**：
- フォーマルな文書感、番号付き章構造が明確
- サマリーエリアがコア発見を強調
- サイドバーの数値コールアウトがデータの可読性を向上

**適用戦略**：`research`（第一推薦）、`finance`、`legal-policy`、`case-study`、`whitepaper`、`general`

### 7. Matrix — 評価マトリクス

**用途**：多次元評価、方案スコアリング、意思決定支援。

**レイアウトロジック**：
- 横軸次元 x 縦軸オプションのスコアリンググリッド
- 色階セル：CI カラー透明度でスコアレベルを表現
- 加重ランキングテーブル + 推奨ハイライト

**ビジュアル特徴**：
- グリッド型スコアリングが一目瞭然
- 色の濃淡がスコアの高低を直接反映
- 推奨項目にビジュアル強調

**適用戦略**：`research`、`whitepaper`、`data-analysis`

### 8. Profile — エンティティプロファイル

**用途**：製品紹介、企業概要、人物/ブランドプロファイル。

**レイアウトロジック**：
- Hero バナー + 名前：`text-4xl font-black`
- コア指標横バー：3-6 個の KPI
- セクションカードグリッド：`grid grid-cols-1 md:grid-cols-2 gap-6`

**ビジュアル特徴**：
- 大バナーでオープニング、ビジュアルアイデンティティを確立
- コア指標を横並びで、主要データを素早く伝達
- セクションカードが詳細情報を収容

**適用戦略**：`product`（第一推薦）、`job-posting`、`startup`

### 9. Flowchart — 意思決定フロー

**用途**：意思決定プロセスの可視化、システムフローチャート。

**レイアウトロジック**：
- ノードカード + CSS 矢印コネクター
- 分岐エリア：`grid grid-cols-2 md:grid-cols-3`
- 開始ノード：円形
- 決定ノード：強調ボーダー
- 終了ノード：円形

**ビジュアル特徴**：
- 純粋な CSS 実装（JS チャートライブラリなし）
- ノード形状でタイプを区別
- 矢印接続がフロー方向を明確に表現

**適用戦略**：`tech-doc`

### 10. Scorecard — スコアカード

**用途**：評価、レーティング表示。

**レイアウトロジック**：
- 総合スコア：`text-6xl font-black` + 円形プログレス
- 各次元：水平プログレスバー（色階で良し悪しを表示）
- 長所短所比較：`grid grid-cols-2` + 左側カラーバー

**ビジュアル特徴**：
- 大きな数字の総合スコアでオープニング
- 次元スコアをプログレスバーで直感的に表示
- 長所短所リストが定性的判断を補助

**適用戦略**：`review`（第一推薦）、`ecommerce`、`finance`、`sports`、`real-estate`

### 11. Pitch — ナラティブランディングページ

**用途**：戦略提案、プロダクトピッチ、説得的ナラティブ。

**レイアウトロジック**：
- 各画面の大見出し：`text-5xl md:text-7xl font-black`
- 論拠エリア：`grid grid-cols-1 md:grid-cols-2 gap-12`
- CTA ボタン：`px-8 py-4 bg-[CI メインカラー] text-white rounded-full`

**ビジュアル特徴**：
- 大文字スタイルの見出し、画面ごとに一つのコアメッセージ
- 論拠エリアが支持データを提供
- 最終 CTA がアクションを促進

**適用戦略**：`startup`（第一推薦）、`opinion`、`press-release`

### 12. Infographic — 縦型インフォグラフィック

**用途**：データ分析の可視化、統計データ表示。

**レイアウトロジック**：
- 大きな数字：`text-6xl md:text-8xl font-black text-[CI メインカラー]`
- アイコン + テキスト：`flex items-start gap-6`
- グラデーションセグメント背景
- トレンド矢印

**ビジュアル特徴**：
- 特に大きな数字で強い視覚的インパクト
- 縦スクロールで各セグメントに独立した背景色
- トレンド矢印と方向指示がデータナラティブを強化

**適用戦略**：`data-analysis`（第一推薦）、`research`、`case-study`、`whitepaper`、`sports`

### 13. Comparison Table — 機能比較表

**用途**：製品比較、スペック比較、複数方案評価。

**レイアウトロジック**：
- コンテナ：`overflow-x-auto` + `<table>` タグ
- サポート/非サポート：`lucide-check` / `lucide-x` アイコン
- 推奨列：`border-2 border-[CI メインカラー]` ハイライト
- ゼブラストライプ行背景

**ビジュアル特徴**：
- 標準テーブルレイアウト、高い情報密度
- 推奨列にビジュアル強調
- モバイルで水平スクロール対応

**適用戦略**：`ecommerce`、`product`、`review`、`job-posting`

### 14. FAQ — 折りたたみ式 Q&A

**用途**：よくある質問、ナレッジベース、Q&A まとめ。

**レイアウトロジック**：
- 折りたたみコンポーネント：`<details>` + グループタブ
- 質問行：`bg-[surface] cursor-pointer` + chevron アイコン
- 回答エリア：`border-l-2 border-[CI メインカラー]/30`

**ビジュアル特徴**：
- 折りたたみ/展開インタラクション（純粋な HTML、JS なし）
- グループタブで大量の Q&A を整理
- 左側カラーバーが回答エリアをマーク

**適用戦略**：`tutorial`、`tech-doc`、`legal-policy`、`recipe`、`health`

### 15. Slide — 16:9 スライドデッキ

**用途**：チーム発表、PDF 出力、プロジェクション表示。

**レイアウトロジック**：
- 固定サイズ：1280x720px
- 各ページ：`page-break-after: always`
- ページ番号：右下
- CI カラーバー：下部 4px
- 表紙：CI 補助色ダーク背景
- コンテンツエリア：flex 充填

**ビジュアル特徴**：
- 厳格な 16:9 アスペクト比
- 印刷時に自動ページ分割
- 表紙ページはダーク背景、コンテンツページはライト背景
- 下部カラーバーで統一ブランド感

**適用戦略**：`video`、およびスライド出力が必要なすべてのシーン

### 16. Iceberg — 表面 vs 深層

**用途**：根本原因分析、表象と本質、アイスバーグモデル。

**レイアウトロジック**：
- 上部 30%：可視表面（ライト背景）
- 水平線分割
- 下部 70%：深層構造（段階的に濃くなる tint）
- ビジュアルウェイトは深度に比例

**ビジュアル特徴**：
- アイスバーグメタファー、上が軽く下が重い
- 深さに応じて色が濃くなる
- 分割線が「水面」を明確にマーク

**適用戦略**：表象と根本原因を区別する分析に適合

### 17. Funnel — コンバージョンファネル

**用途**：コンバージョン分析、スクリーニングプロセス、段階的絞り込み。

**レイアウトロジック**：
- 幅の漸減：`max-w-4xl` → `3xl` → `2xl` → `xl`
- 各レイヤーにコンバージョン/除外指標
- 背景色がファネルの絞り込みに伴い濃くなる
- 下部の最終出力がハイライト

**ビジュアル特徴**：
- 視覚的に広いものから狭いものへ
- 各レイヤーにコンバージョン率を注記
- 色が濃いほど最終目標に近い

**適用戦略**：コンバージョンファネルシーンに適合

### 18. Bridge — 変革パス

**用途**：変革提案、現状から目標への経路計画。

**レイアウトロジック**：
- 三領域レイアウト：`grid grid-cols-1 md:grid-cols-[1fr_2fr_1fr]`
  - LEFT：現状
  - CENTER：変革パス（3-5 ステップ）
  - RIGHT：目標
- 重要な転換点に強調スタイル

**ビジュアル特徴**：
- 左から右へのナラティブフロー
- 中央の変革パスがビジュアルの焦点
- 現状と目標がコントラストを形成

**適用戦略**：変革/トランスフォーメーション提案に適合

### 戦略→テンプレート完全マッピング表

| 戦略 | 第一推薦 | 代替1 | 代替2 |
|------|---------|-------|-------|
| breaking-news | Article | Timeline | Dashboard |
| opinion | Article | Versus | Pitch |
| product | Profile | Dashboard | Comparison Table |
| ecommerce | Comparison Table | Scorecard | Dashboard |
| tutorial | Steps | FAQ | Timeline |
| tech-doc | Steps | Flowchart | Report |
| research | Report | Infographic | Matrix |
| finance | Report | Scorecard | Dashboard |
| legal-policy | Report | FAQ | Article |
| video | Article | Timeline | Slide |
| social-thread | Article | Timeline | Dashboard |
| general | Dashboard | Article | Report |
| press-release | Article | Dashboard | Pitch |
| case-study | Report | Steps | Infographic |
| whitepaper | Report | Infographic | Matrix |
| data-analysis | Infographic | Dashboard | Matrix |
| review | Scorecard | Versus | Comparison Table |
| interview | Article | Timeline | Report |
| event | Timeline | Dashboard | Steps |
| job-posting | Profile | Comparison Table | Dashboard |
| recipe | Steps | FAQ | Report |
| travel | Dashboard | Timeline | Infographic |
| health | Steps | FAQ | Report |
| real-estate | Dashboard | Scorecard | Report |
| startup | Pitch | Profile | Report |
| podcast | Article | Timeline | Report |
| announcement | Article | Dashboard | Report |
| sports | Scorecard | Timeline | Infographic |

### テンプレート選択原則

1. **Router 自動推薦**：Step 5 で Router 層が Brain 分析結果に基づき第一推薦テンプレートを自動推薦
2. **ユーザーが上書き可能**：推薦結果は参考のみ、ユーザーは任意のテンプレートを選択可能
3. **第一推薦優先**：明確な理由がない限り、第一推薦テンプレートを優先使用
4. **混合使用**：複雑なドキュメントは異なる Section 内で異なるテンプレートのコンポーネントを混合使用可能
5. **CI 優先**：どのテンプレートを使用しても、CI 仕様（色、フォント、角丸、シャドウ）は常に優先

---

## 中文 {#chinese}

> 基于 EIP (Explain In Picture) 项目文档迁移。原始来源：EIP SKELETON_DESIGN_RULES.md。

每种模板定义了 Tailwind class 级别的骨格规则。HTML 生成时（Step 7）必须严格遵循。

### 1. Dashboard — Bento-box KPI 仪表盘

**用途**：数据密集型概要。适用于 KPI 汇总、运营概览、多指标监控。

**布局逻辑**：
- 容器：`grid grid-cols-1 md:grid-cols-3 lg:grid-cols-4 gap-4 md:gap-6`
- KPI 卡片：`text-3xl font-bold` 大数字 + 小标签
- 混合跨列：`col-span-1` / `col-span-2` / `col-span-3` 打破均匀网格
- 进度指示：CSS 进度条（非 JS 图表）

**视觉特征**：
- Bento-box 风格，大小不一的卡片组合
- 数字优先，文字辅助
- 色彩用透明度区分层级（CI 主色 4%/8%/12%/20%）

**适用策略**：`general`(首选), `product`, `ecommerce`, `travel`, `real-estate`, `sports`, `data-analysis`

### 2. Versus — 对比分析

**用途**：A vs B 对比。适用于方案比较、竞品对比、优劣分析。

**布局逻辑**：
- 容器：`grid grid-cols-1 md:grid-cols-2 gap-8`
- 左右色调区分：CI 主色 tint vs 辅助色 tint
- 优劣列表：`lucide-check` (优) / `lucide-x` (劣) 图标
- 统合比较表：`col-span-2` 跨列底部总结

**视觉特征**：
- 左右对称布局，色彩对比鲜明
- 每侧有独立的标题和指标
- 底部汇总区打破二分法，给出综合判断

**适用策略**：`opinion`, `review`, `ecommerce`

### 3. Timeline — 时间轴

**用途**：发展史、阶段分解、里程碑叙事。

**布局逻辑**：
- 中轴线：`absolute left-4 md:left-1/2 w-1 bg-gradient-to-b`（CI 色渐变）
- 交替配置：`md:flex-row` / `md:flex-row-reverse` 左右交替
- 日期徽章：圆形或矩形，CI 主色背景

**视觉特征**：
- 垂直中轴线贯穿全文
- 节点左右交替，避免单调
- 移动端回退为左侧轴线 + 右侧内容

**适用策略**：`breaking-news`, `event`, `video`, `social-thread`, `interview`, `podcast`

### 4. Article — 长文阅读

**用途**：新闻报道、深度评论、叙事型内容。

**布局逻辑**：
- Hero 区：`text-4xl md:text-6xl font-black`
- 正文容器：`max-w-3xl mx-auto space-y-6`
- 引用块：`border-l-4 pl-6 text-xl italic`
- 图文交替：`flex md:flex-row gap-8`
- 脚注区域

**视觉特征**：
- 窄栏阅读体验，类杂志排版
- Hero 区大标题震撼开场
- 引用块和图文交替打破文字墙

**适用策略**：`breaking-news`(首选), `opinion`, `video`, `social-thread`, `press-release`, `interview`, `podcast`, `announcement`

### 5. Steps — 编号步骤

**用途**：教程、操作手册、流程指南。

**布局逻辑**：
- 步骤圆圈：`w-10 h-10 rounded-full bg-[CI主色] text-white` 居中数字
- 连接器：`border-l-2 border-dashed ml-5 h-8` 虚线连接
- 每步内容：标题 + 正文 + 可选代码块

**视觉特征**：
- 清晰的步骤编号，视觉引导强
- 虚线连接器强调顺序关系
- 每步可包含代码块、截图等辅助内容

**适用策略**：`tutorial`(首选), `tech-doc`, `recipe`, `health`, `case-study`

### 6. Report — 结构化报告

**用途**：研究报告、财务分析、专业文档。

**布局逻辑**：
- 摘要区：`bg-[CI主色]/5 border-l-4 rounded-r-lg p-6`
- 编号章节 + 侧边数值呼出：`sticky top-4 text-3xl font-black`
- 数据表格 + 推荐区

**视觉特征**：
- 正式文档感，编号章节结构清晰
- 摘要区突出核心发现
- 侧边栏数字呼出增强数据可读性

**适用策略**：`research`(首选), `finance`, `legal-policy`, `case-study`, `whitepaper`, `general`

### 7. Matrix — 评价矩阵

**用途**：多维度评估、方案评分、决策支持。

**布局逻辑**：
- 横轴维度 x 纵轴选项的评分网格
- 色阶单元格：CI 色透明度表达高低分
- 加权排名表 + 推荐高亮

**视觉特征**：
- 网格化评分一目了然
- 颜色深浅直接反映分数高低
- 推荐项有视觉强调

**适用策略**：`research`, `whitepaper`, `data-analysis`

### 8. Profile — 实体画像

**用途**：产品介绍、企业概况、人物/品牌 Profile。

**布局逻辑**：
- Hero banner + 名称：`text-4xl font-black`
- 核心指标横条：3-6 个 KPI
- 分区卡片网格：`grid grid-cols-1 md:grid-cols-2 gap-6`

**视觉特征**：
- 大 banner 开场，建立视觉身份
- 核心指标横排，快速传递关键数据
- 分区卡片承载详细信息

**适用策略**：`product`(首选), `job-posting`, `startup`

### 9. Flowchart — 决策流程

**用途**：决策过程可视化、系统流程图。

**布局逻辑**：
- 节点卡片 + CSS 箭头连接器
- 分支区域：`grid grid-cols-2 md:grid-cols-3`
- 开始节点：圆形
- 决定节点：强调边框
- 结束节点：圆形

**视觉特征**：
- 纯 CSS 实现（无 JS 图表库）
- 节点形状区分类型
- 箭头连接清晰表达流向

**适用策略**：`tech-doc`

### 10. Scorecard — 评分卡

**用途**：评价、评测、Rating 展示。

**布局逻辑**：
- 总分：`text-6xl font-black` + 圆环进度
- 各维度：水平进度条（色阶表示好坏）
- 优劣对比：`grid grid-cols-2` + 左侧色条

**视觉特征**：
- 大数字总分开场
- 维度分数用进度条直观呈现
- 优劣列表辅助定性判断

**适用策略**：`review`(首选), `ecommerce`, `finance`, `sports`, `real-estate`

### 11. Pitch — 叙事型着陆页

**用途**：战略提案、产品 Pitch、说服性叙事。

**布局逻辑**：
- 每屏大标语：`text-5xl md:text-7xl font-black`
- 论据区：`grid grid-cols-1 md:grid-cols-2 gap-12`
- CTA 按钮：`px-8 py-4 bg-[CI主色] text-white rounded-full`

**视觉特征**：
- 大字报式标语，每屏一个核心信息
- 论据区提供支撑数据
- 最终 CTA 推动行动

**适用策略**：`startup`(首选), `opinion`, `press-release`

### 12. Infographic — 纵向信息图

**用途**：数据分析可视化、统计数据展示。

**布局逻辑**：
- 大数字：`text-6xl md:text-8xl font-black text-[CI主色]`
- 图标+文字：`flex items-start gap-6`
- 渐变分段背景
- 趋势箭头

**视觉特征**：
- 数字特别大，视觉冲击强
- 纵向滚动，每段有独立背景色
- 趋势箭头和方向指示强化数据叙事

**适用策略**：`data-analysis`(首选), `research`, `case-study`, `whitepaper`, `sports`

### 13. Comparison Table — 特性比较表

**用途**：产品对比、规格对比、多方案评估。

**布局逻辑**：
- 容器：`overflow-x-auto` + `<table>` 标签
- 支持/不支持：`lucide-check` / `lucide-x` 图标
- 推荐列：`border-2 border-[CI主色]` 高亮
- 斑马纹行背景

**视觉特征**：
- 标准表格布局，信息密度高
- 推荐列有视觉强调
- 移动端可水平滚动

**适用策略**：`ecommerce`, `product`, `review`, `job-posting`

### 14. FAQ — 折叠式 Q&A

**用途**：常见问题、知识库、Q&A 汇总。

**布局逻辑**：
- 折叠组件：`<details>` + 分组标签页
- 问题行：`bg-[surface] cursor-pointer` + chevron 图标
- 回答区：`border-l-2 border-[CI主色]/30`

**视觉特征**：
- 折叠/展开交互（纯 HTML，无 JS）
- 分组标签页组织大量 Q&A
- 左侧色条标记回答区

**适用策略**：`tutorial`, `tech-doc`, `legal-policy`, `recipe`, `health`

### 15. Slide — 16:9 幻灯片

**用途**：团队展示、PDF 输出、投影演示。

**布局逻辑**：
- 固定尺寸：1280x720px
- 每页：`page-break-after: always`
- 页码：右下角
- CI 色条：底部 4px
- 封面：CI 辅助色深色背景
- 内容区：flex 撑满

**视觉特征**：
- 严格 16:9 比例
- 打印时自动分页
- 封面页深色背景，内容页浅色背景
- 底部色条统一品牌感

**适用策略**：`video`, 以及任何需要幻灯片输出的场景

### 16. Iceberg — 表面 vs 深层

**用途**：根因分析、表象与本质、冰山模型。

**布局逻辑**：
- 上部 30%：可见表面（浅色背景）
- 水平线分割
- 下部 70%：深层结构（逐级加深的 tint）
- 视觉重量与深度成正比

**视觉特征**：
- 冰山隐喻，上轻下重
- 颜色随深度加深
- 分割线明确标记「水面」

**适用策略**：适用于任何需要区分表象与根因的分析

### 17. Funnel — 漏斗

**用途**：转化分析、筛选过程、逐级收窄。

**布局逻辑**：
- 宽度递减：`max-w-4xl` → `3xl` → `2xl` → `xl`
- 每层有转化/淘汰指标
- 背景色随漏斗收窄而加深
- 底部最终输出高亮

**视觉特征**：
- 视觉上从宽到窄
- 每层标注转化率
- 颜色越深表示越接近最终目标

**适用策略**：适用于任何转化漏斗场景

### 18. Bridge — 转化路径

**用途**：变革提案、从现状到目标的路径规划。

**布局逻辑**：
- 三区域布局：`grid grid-cols-1 md:grid-cols-[1fr_2fr_1fr]`
  - LEFT：现状
  - CENTER：转化路径（3-5 步骤）
  - RIGHT：目标
- 关键转折点用强调样式

**视觉特征**：
- 从左到右的叙事流向
- 中间转化路径是视觉焦点
- 现状和目标形成对比

**适用策略**：适用于任何变革/转型提案

### 策略→模板映射完整表

| 策略 | 首选模板 | 备选 1 | 备选 2 |
|------|---------|--------|--------|
| breaking-news | Article | Timeline | Dashboard |
| opinion | Article | Versus | Pitch |
| product | Profile | Dashboard | Comparison Table |
| ecommerce | Comparison Table | Scorecard | Dashboard |
| tutorial | Steps | FAQ | Timeline |
| tech-doc | Steps | Flowchart | Report |
| research | Report | Infographic | Matrix |
| finance | Report | Scorecard | Dashboard |
| legal-policy | Report | FAQ | Article |
| video | Article | Timeline | Slide |
| social-thread | Article | Timeline | Dashboard |
| general | Dashboard | Article | Report |
| press-release | Article | Dashboard | Pitch |
| case-study | Report | Steps | Infographic |
| whitepaper | Report | Infographic | Matrix |
| data-analysis | Infographic | Dashboard | Matrix |
| review | Scorecard | Versus | Comparison Table |
| interview | Article | Timeline | Report |
| event | Timeline | Dashboard | Steps |
| job-posting | Profile | Comparison Table | Dashboard |
| recipe | Steps | FAQ | Report |
| travel | Dashboard | Timeline | Infographic |
| health | Steps | FAQ | Report |
| real-estate | Dashboard | Scorecard | Report |
| startup | Pitch | Profile | Report |
| podcast | Article | Timeline | Report |
| announcement | Article | Dashboard | Report |
| sports | Scorecard | Timeline | Infographic |

### 模板选择原则

1. **Router 自动推荐**：Step 5 中 Router 层根据 Brain 分析结果自动推荐首选模板
2. **用户可覆盖**：推荐结果仅供参考，用户可选择任意模板
3. **首选优先**：除非有明确理由，优先使用首选模板
4. **混合使用**：复杂文档可在不同 Section 内混合使用不同模板的组件
5. **CI 优先**：无论使用哪种模板，CI 规范（颜色、字体、圆角、阴影）始终优先
