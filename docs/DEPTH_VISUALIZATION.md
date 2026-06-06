# Depth Visualization Rules / 深度可視化ルール / 深度可视化规则

> **[HTML output mode — optional]** make-doc-skill's primary path is company document generation (see `../SKILL.md`). These HTML depth-visualization rules apply only to the optional HTML output mode. For company documents, depth is controlled per `SIZE_DEPTH_MATRIX.md`.

> Based on EIP (Explain In Picture) project documentation

[EN](#english) · [日本語](#japanese) · [中文](#chinese)

---

## English {#english}

> Based on EIP (Explain In Picture) project documentation migration. Depth visualization rules ensure data and analytical conclusions are presented in the most appropriate visual form, rather than degrading to plain text lists.

### Overview

When materials contain any of the following 6 data structures, **the corresponding visualization method must be used**. Degradation to text lists is prohibited.

Depth visualization intensity is controlled by S/M/L/XL four levels (see [SIZE_DEPTH_MATRIX.md](./SIZE_DEPTH_MATRIX.md)).

### 1. Causal Chain Visualization

**Trigger**: Material contains causal derivation relationships like "A leads to B, B leads to C".

#### Visualization Rules

- **Layout**: Vertical flow + arrow connections
- **Nodes**: Each node contains cause/effect + mechanism explanation
- **Prohibited**: Side-by-side card arrangement (side-by-side implies equal level, violating causal order)
- **Colors**: CI primary color opacity differentiates hierarchy
  - Root cause (deepest) = darkest (CI primary 20% opacity)
  - Intermediate steps = medium (CI primary 12% opacity)
  - Final result (most surface) = lightest (CI primary 4% opacity)

#### Canvas Instructions

**S Level**: Simplified causal chain: show only start→end direct relationship. Two nodes + one arrow. Node style: `rounded-xl p-6 border-l-4`, border-color uses CI primary. Arrow: `border-l-2 border-dashed ml-5 h-8`, CI primary.

**M Level**: Standard causal chain: show complete chain (3-5 nodes). Vertical arrangement, each node contains title (`font-bold`, CI primary) + mechanism explanation (`text-sm`, body color). Connector: `border-l-2 border-dashed`, inter-node spacing `h-8`. Colors: root node `bg-[CI primary]/20`, intermediate `bg-[CI primary]/12`, result `bg-[CI primary]/4`.

**L Level**: Complete causal chain: show full chain + branch paths + feedback loops. Main chain vertical (3-7 nodes). Branch points use `grid grid-cols-2`. Feedback loops shown with dashed arc arrows. Each node includes title, mechanism, evidence strength badge. Key turning point nodes get `ring-2 ring-[CI primary]` emphasis.

**XL Level**: Interactive causal chain: L level plus `details/summary` fold/expand for each node's detailed argument, cross-point annotations for multiple causal chains, counterfactual analysis area (`border-dashed`, low opacity), uncertainty annotation at each chain connection.

### 2. Confidence Visualization

**Trigger**: Claims/conclusions in material need credibility annotation.

#### Visualization Rules

- **Layout**: Horizontal progress bar + percentage + reason explanation
- **Color scale** (based on CI primary opacity):
  - >= 80%: Dark (CI primary 100%)
  - 50-79%: Medium (CI primary 60%)
  - 30-49%: Light (CI primary 30%)
  - < 30%: Lightest (CI primary 10%)
- **Required**: Each confidence score must have a one-line reason beside it

#### Canvas Instructions

**S Level**: Simplified: only mark high/medium/low badges next to core conclusions. Badge style: `px-2 py-0.5 rounded-full text-xs font-medium`. High = `bg-[CI primary] text-white`. Medium = `bg-[CI primary]/30 text-[CI primary]`. Low = `bg-gray-100 text-gray-600`.

**M Level**: Standard: horizontal progress bar + percentage + reason. Container: `flex items-center gap-4`. Label: `w-32 text-sm font-medium`. Progress bar: `flex-1 h-2 rounded-full bg-gray-100`. Fill: `h-full rounded-full`, width = percentage. Colors by threshold. Percentage text: `w-12 text-right text-sm font-bold`. Reason: `text-xs text-[body color] mt-1`.

**L Level**: Complete: M level plus grouped display (by topic/Section), evidence source list per conclusion, overall confidence summary chart (bottom), gap analysis between high and low confidence.

**XL Level**: Interactive: L level plus `details/summary` for full argument per confidence, confidence change tracking (if time series data), sensitivity analysis.

### 3. Comparison Delta Visualization

**Trigger**: Material contains comparison of two or more data sets (A vs B, before vs after, plan vs actual).

#### Visualization Rules

- **GAP column**: Comparison tables must have a GAP/difference column
- **Direction arrows**: ↑ improvement / ↓ deterioration / → stable
- **Color-coded differences**: Positive uses CI primary, negative uses CI primary low opacity
- **Prohibited**: Simply listing two data sets without marking differences

#### Canvas Instructions

**S Level**: Simplified: simple two-column + GAP column table. GAP column contains direction arrow and value. Positive: `text-[CI primary] font-bold` + ↑. Negative: `text-[CI secondary]` + ↓. Stable: `text-gray-400` + →.

**M Level**: Standard: formatted table + visual GAP. Each row GAP cell contains direction arrow, percentage change, small horizontal bar chart (width = change ratio). Positive row: `bg-[CI primary]/4`. Negative row: `bg-[CI secondary]/4`.

**L Level**: Complete: M level plus multi-group comparison (not just A vs B, but A vs B vs C), weighted summary row, key difference item highlights (Top 3 largest differences), difference explanation column.

**XL Level**: Interactive: L level plus column header sorting (CSS class toggle only), threshold annotations (warning color for values outside normal range), trend comparison (if time series available).

### 4. Information Quality Annotation

**Trigger**: All M level and above documents.

#### Visualization Rules

Each major conclusion has an evidence level badge beside it:

| Badge | Meaning | Visual |
|-------|---------|--------|
| Primary data | Raw data, official statements, experimental results | Solid circle + CI primary |
| Secondary inference | Analytical derivation, media retelling, expert opinion | Half-solid circle + CI primary 60% |
| Unverified | Hearsay, anonymous sources, single source | Hollow circle + CI primary 20% |

- `[DATA_GAP]` marking uses warning callout: `bg-amber-50 border-l-4 border-amber-400 p-4`

#### Canvas Instructions

**S Level**: Simplified: no individual conclusion annotation, only overall data source summary at document end.

**M Level**: Standard: badges next to core conclusions. Badge style: `inline-flex items-center gap-1 px-2 py-0.5 rounded-full text-xs`. Primary: `bg-[CI primary]/15 text-[CI primary]`, solid circle SVG. Secondary: `bg-[CI primary]/8 text-[CI primary]/70`, half-solid circle SVG. Unverified: `bg-gray-100 text-gray-500`, hollow circle SVG. DATA_GAP callout: `bg-amber-50 border-l-4 border-amber-400 p-4 rounded-r-lg`.

**L Level**: Complete: M level plus evidence source summary at each Section bottom, overall document information quality score, complete list of data gap areas.

**XL Level**: Interactive: L level plus `details/summary` for detailed source info, cross-validation annotations, source credibility rating.

### 5. Trend Direction Visualization

**Trigger**: Material contains time series data or trend descriptions.

#### Visualization Rules

- **Layout**: CSS mini bar + direction arrow
- **Direction arrows**: ↗ accelerating / → stable / ↘ decelerating
- **Derivative calculation**: **Rate of change (derivative) calculation is mandatory**, cannot show only absolute values
- **One-line explanation**: Each trend indicator must have a one-line summary

#### Canvas Instructions

**S Level**: Simplified: only direction arrow + one-line description. Accelerating ↗: `text-[CI primary]`. Stable →: `text-gray-400`. Decelerating ↘: `text-[CI secondary]`.

**M Level**: Standard: CSS mini bar + direction arrow + rate of change + one-line explanation. Mini bar: `w-24 h-3 rounded-full bg-gray-100`. Growth fill: `bg-[CI primary]`. Decline fill: `bg-[CI secondary]`. Derivative annotation: `text-xs text-[muted color]`.

**L Level**: Complete: M level plus multi-metric parallel display on timeline, trend turning point annotations (inflection + cause), prediction interval (dashed, with uncertainty range).

**XL Level**: Interactive: L level plus CSS hover for detailed data points, multi-trend correlation analysis, "if trend continues..." projection.

### 6. Uncertainty Visualization

**Trigger**: Analysis contains significant information uncertainty or knowledge gaps.

#### Visualization Rules

- **Independent Section**: Uncertainty content forms a separate section, not mixed into confirmed conclusions
- **Visual distinction**: Dashed border + low opacity background
- **Content**: Information gap list + potential impact + suggested data to supplement

#### Canvas Instructions

**S Level**: Simplified: add a "notes" paragraph at document end. Style: `border border-dashed border-gray-300 rounded-lg p-4 bg-gray-50/50`.

**M Level**: Standard: independent "Uncertainty Zone" Section. Container: `border-2 border-dashed rounded-2xl p-6`. Border-color: CI primary 30% opacity. Background: CI primary 3% opacity. Title: `text-lg font-bold` + warning icon (Lucide alert-triangle). Two-column content: left — information gap list, right — potential impact. Bottom: recommended data supplementation action items.

**L Level**: Complete: M level plus uncertainty grading (high/medium/low impact ranking), scenario analysis (best/baseline/worst three scenarios), "if..." projection for each uncertainty factor.

**XL Level**: Interactive: L level plus `details/summary` for detailed analysis per uncertainty factor, sensitivity matrix (uncertainty factors x impact dimensions), risk mitigation recommendations.

### Depth Level Summary

| Visualization Type | S | M | L | XL |
|-------------------|---|---|---|---|
| Causal chain | Start→End | Complete chain | +Branches+Feedback | +Interactive+Counterfactual |
| Confidence | High/Med/Low badge | Progress bar+Reason | +Grouped+Summary | +Argument+Sensitivity |
| Comparison delta | Simple GAP table | +Visual bars | +Multi-group+Highlight | +Sorting+Threshold |
| Information quality | None (overall only) | Core conclusion badges | +Source summary | +Cross-validation |
| Trend direction | Arrow+One line | Mini bar+Rate of change | +Turning point+Forecast | +Correlation+Projection |
| Uncertainty | End notes | Independent Section | +Scenario analysis | +Sensitivity matrix |

---

## 日本語 {#japanese}

> EIP (Explain In Picture) プロジェクトドキュメントからの移行。深度可視化ルールにより、データと分析結論が最も適切なビジュアル形式で表示され、プレーンテキストリストへの退化を防ぎます。

### 概要

素材に以下の6種のデータ構造が含まれる場合、**対応する可視化方式を使用しなければなりません**。テキストリストへの退化は禁止されています。

深度可視化の強度は S/M/L/XL の4段階で制御されます（[SIZE_DEPTH_MATRIX.md](./SIZE_DEPTH_MATRIX.md) 参照）。

### 1. 因果チェーン可視化

**トリガー条件**：素材に「A が B を引き起こし、B が C を引き起こす」という因果推導関係が存在する。

#### 可視化ルール

- **レイアウト**：縦方向フロー + 矢印接続
- **ノード**：各ノードに原因/結果 + メカニズム説明を含む
- **禁止**：並列カード配置（並列は同レベル関係を暗示し、因果順序に違反）
- **色彩**：CI メインカラーの透明度で階層を区別
  - 根本原因（最深層）= 最も濃い（CI メインカラー 20% 透明度）
  - 中間段階 = 中程度（CI メインカラー 12% 透明度）
  - 最終結果（最表層）= 最も淡い（CI メインカラー 4% 透明度）

#### Canvas 指示

**S 級**：簡略版：起点→終点の直接関係のみ表示。2ノード + 1矢印。ノードスタイル：`rounded-xl p-6 border-l-4`、border-color は CI メインカラー。矢印：`border-l-2 border-dashed ml-5 h-8`。

**M 級**：標準版：完全な因果チェーン（3-5ノード）を表示。縦配置、各ノードにタイトル（`font-bold`、CI メインカラー）+ メカニズム説明（`text-sm`、body 色）。コネクター：`border-l-2 border-dashed`、ノード間隔 `h-8`。色彩：根本ノード `bg-[CI メインカラー]/20`、中間 `bg-[CI メインカラー]/12`、結果 `bg-[CI メインカラー]/4`。

**L 級**：完全版：完全なチェーン + 分岐パス + フィードバックループ。メインチェーン縦配置（3-7ノード）。分岐点は `grid grid-cols-2`。フィードバックループは破線弧矢印。各ノードにエビデンス強度バッジ付き。重要転換点ノードに `ring-2 ring-[CI メインカラー]`。

**XL 級**：インタラクティブ版：L 級に加え、`details/summary` 折りたたみ展開、複数因果チェーンの交差点注記、反事実分析エリア（`border-dashed`、低透明度）、各接続の不確実性注記。

### 2. 信頼度可視化

**トリガー条件**：素材中の主張/結論に信頼度の注記が必要。

#### 可視化ルール

- **レイアウト**：水平プログレスバー + パーセント + 理由説明
- **色階**（CI メインカラー透明度ベース）：
  - >= 80%：濃色（CI メインカラー 100%）
  - 50-79%：中色（CI メインカラー 60%）
  - 30-49%：淡色（CI メインカラー 30%）
  - < 30%：最淡（CI メインカラー 10%）
- **必須**：各信頼度スコアの横に一言の理由

#### Canvas 指示

**S 級**：簡略版：コア結論の横に高/中/低バッジのみ。高 = `bg-[CI メインカラー] text-white`。中 = `bg-[CI メインカラー]/30 text-[CI メインカラー]`。低 = `bg-gray-100 text-gray-600`。

**M 級**：標準版：水平プログレスバー + パーセント + 理由。コンテナ：`flex items-center gap-4`。閾値別の色彩。

**L 級**：完全版：M 級に加え、グループ表示、証拠ソースリスト、全体信頼度サマリーチャート、高低信頼度間のギャップ分析。

**XL 級**：インタラクティブ版：L 級に加え、`details/summary` で完全論証、信頼度変化追跡、感度分析。

### 3. 比較増分可視化

**トリガー条件**：素材に2組以上のデータの比較が存在（A vs B、前 vs 後、計画 vs 実績）。

#### 可視化ルール

- **GAP 列**：比較表には GAP/差異列が必須
- **方向矢印**：↑ 改善 / ↓ 悪化 / → 安定
- **色分け差異**：正方向は CI メインカラー、負方向は CI メインカラー低透明度
- **禁止**：2組のデータを差異を記さず列挙するだけ

#### Canvas 指示

**S 級**：簡略版：シンプルな2列 + GAP 列テーブル。正方向：`text-[CI メインカラー] font-bold` + ↑。負方向：`text-[CI 補助カラー]` + ↓。安定：`text-gray-400` + →。

**M 級**：標準版：フォーマット済みテーブル + ビジュアル GAP。各行 GAP セルに方向矢印、パーセント変化、小型水平棒グラフ。

**L 級**：完全版：M 級に加え、多グループ比較、加重サマリー行、キー差異項目ハイライト、差異説明列。

**XL 級**：インタラクティブ版：L 級に加え、列ヘッダーソート（CSS class toggle のみ）、閾値注記、トレンド比較。

### 4. 情報品質注記

**トリガー条件**：すべての M 級以上のドキュメント。

#### 可視化ルール

各主要結論の横にエビデンスレベルバッジ：

| バッジ | 意味 | ビジュアル |
|-------|------|----------|
| 一次データ | 生データ、公式声明、実験結果 | 実心円 + CI メインカラー |
| 二次推測 | 分析導出、メディア転述、専門家意見 | 半実心円 + CI メインカラー 60% |
| 未検証 | 伝聞、匿名ソース、単一ソース | 空心円 + CI メインカラー 20% |

- `[DATA_GAP]` マーキング：警告 callout `bg-amber-50 border-l-4 border-amber-400 p-4`

#### Canvas 指示

**S 級**：簡略版：個別結論の注記なし、文書末尾の全体データソース概要のみ。

**M 級**：標準版：コア結論の横にバッジ。一次データ：`bg-[CI メインカラー]/15 text-[CI メインカラー]`。二次推測：`bg-[CI メインカラー]/8 text-[CI メインカラー]/70`。未検証：`bg-gray-100 text-gray-500`。

**L 級**：完全版：M 級に加え、各 Section 下部の証拠ソースサマリー、全体文書の情報品質スコア、データ空白エリアの完全リスト。

**XL 級**：インタラクティブ版：L 級に加え、`details/summary` で詳細ソース情報、クロスバリデーション注記、ソース信頼度評価。

### 5. トレンド方向可視化

**トリガー条件**：素材に時系列データまたはトレンド記述が含まれる。

#### 可視化ルール

- **レイアウト**：CSS mini bar + 方向矢印
- **方向矢印**：↗ 加速 / → 安定 / ↘ 減速
- **導関数計算**：**変化率（導関数）計算は必須**、絶対値のみの表示は不可
- **一言解説**：各トレンド指標に一言のサマリーが必須

#### Canvas 指示

**S 級**：簡略版：方向矢印 + 一言記述のみ。加速 ↗：`text-[CI メインカラー]`。安定 →：`text-gray-400`。減速 ↘：`text-[CI 補助カラー]`。

**M 級**：標準版：CSS mini bar + 方向矢印 + 変化率 + 一言解説。

**L 級**：完全版：M 級に加え、タイムライン上の複数指標並列表示、トレンド転換点注記、予測区間（破線、不確実性範囲付き）。

**XL 級**：インタラクティブ版：L 級に加え、CSS ホバーで詳細データポイント、複数トレンドの相関分析、「トレンドが続けば...」の推計。

### 6. 不確実性可視化

**トリガー条件**：分析に顕著な情報の不確実性または知識の空白が存在する。

#### 可視化ルール

- **独立 Section**：不確実性コンテンツは独立セクション、確定的結論に混在させない
- **ビジュアル区別**：破線ボーダー + 低透明度背景
- **内容**：情報ギャップリスト + 潜在的影響 + 補充すべきデータの推奨

#### Canvas 指示

**S 級**：簡略版：文書末尾に「注意事項」段落を追加。スタイル：`border border-dashed border-gray-300 rounded-lg p-4 bg-gray-50/50`。

**M 級**：標準版：独立「不確実性ゾーン」Section。コンテナ：`border-2 border-dashed rounded-2xl p-6`。二列コンテンツ：左 — 情報ギャップリスト、右 — 潜在的影響。

**L 級**：完全版：M 級に加え、不確実性グレーディング、シナリオ分析（最良/基準/最悪）、各不確実性因子の「もし...」推計。

**XL 級**：インタラクティブ版：L 級に加え、`details/summary` で詳細分析、感度マトリクス、リスク緩和推奨。

### 深度レベルサマリー

| 可視化タイプ | S | M | L | XL |
|------------|---|---|---|---|
| 因果チェーン | 起点→終点 | 完全チェーン | +分岐+フィードバック | +インタラクティブ+反事実 |
| 信頼度 | 高/中/低バッジ | プログレスバー+理由 | +グループ+サマリー | +論証+感度 |
| 比較増分 | シンプルGAP表 | +ビジュアルバー | +多グループ+ハイライト | +ソート+閾値 |
| 情報品質 | なし（全体のみ） | コア結論バッジ | +ソースサマリー | +クロスバリデーション |
| トレンド方向 | 矢印+一言 | mini bar+変化率 | +転換点+予測 | +相関+推計 |
| 不確実性 | 末尾注意事項 | 独立Section | +シナリオ分析 | +感度マトリクス |

---

## 中文 {#chinese}

> 基于 EIP (Explain In Picture) 项目文档迁移。深度可视化规则确保数据和分析结论以最合适的视觉形式呈现，而非退化为纯文字列表。

### 概述

当素材中包含以下 6 种数据结构时，**必须使用对应的可视化方式**。退化为文字列表是被禁止的。

深度可视化的强度受 S/M/L/XL 四级控制（详见 [SIZE_DEPTH_MATRIX.md](./SIZE_DEPTH_MATRIX.md)）。

### 1. 因果链可视化

**触发条件**：素材中存在「A 导致 B，B 导致 C」的因果推导关系。

#### 可视化规则

- **布局**：纵向流程 + 箭头连接
- **节点**：每个节点包含原因/结果 + 机制说明
- **禁止**：并列卡片排列（并列暗示同级关系，违背因果顺序）
- **色彩**：CI 主色透明度区分层级
  - 根因（最深层）= 最浓（CI 主色 20% 透明度）
  - 中间环节 = 中等（CI 主色 12% 透明度）
  - 最终结果（最表层）= 最淡（CI 主色 4% 透明度）

#### Canvas 指令

**S 级**：因果链简化版：仅展示起点→终点的直接关系。两个节点 + 一个箭头。节点样式：`rounded-xl p-6 border-l-4`，border-color 使用 CI 主色。箭头：`border-l-2 border-dashed ml-5 h-8`，CI 主色。

**M 级**：因果链标准版：展示完整因果链（3-5 个节点）。纵向排列，每个节点包含标题（`font-bold`，CI 主色）+ 机制说明（`text-sm`，body 色）。连接器：`border-l-2 border-dashed`，节点间距 `h-8`。色彩：根因节点 `bg-[CI主色]/20`，中间 `bg-[CI主色]/12`，结果 `bg-[CI主色]/4`。

**L 级**：因果链完整版：展示完整因果链 + 分支路径 + 反馈循环。主链纵向排列（3-7 个节点）。分支点使用 `grid grid-cols-2` 展开。反馈循环用虚线圆弧箭头表示。每个节点包含证据强度标记。关键转折点节点加 `ring-2 ring-[CI主色]` 强调。

**XL 级**：因果链交互版：在 L 级基础上增加 `details/summary` 折叠展开每个节点的详细论证、多条因果链的交叉点标注、「如果...那么...」反事实分析区域（`border-dashed`，低透明度）、不确定性标注在链的每个连接处。

### 2. 置信度可视化

**触发条件**：素材中的主张/结论需要标注可信度。

#### 可视化规则

- **布局**：水平进度条 + 百分比 + 理由说明
- **色阶**（基于 CI 主色透明度）：
  - >= 80%：浓色（CI 主色 100%）
  - 50-79%：中色（CI 主色 60%）
  - 30-49%：淡色（CI 主色 30%）
  - < 30%：最淡（CI 主色 10%）
- **必须**：每个置信度评分旁附带一句话理由

#### Canvas 指令

**S 级**：置信度简化版：仅在核心结论旁标注高/中/低徽章。高 = `bg-[CI主色] text-white`。中 = `bg-[CI主色]/30 text-[CI主色]`。低 = `bg-gray-100 text-gray-600`。

**M 级**：置信度标准版：水平进度条 + 百分比 + 理由。容器：`flex items-center gap-4`。色彩按阈值分级。

**L 级**：置信度完整版：在 M 级基础上增加分组显示、证据来源列表、整体置信度汇总图、高置信度与低置信度之间的 gap 分析。

**XL 级**：置信度交互版：在 L 级基础上增加 `details/summary` 展开每个置信度的完整论证、置信度变化追踪、敏感性分析。

### 3. 对比增量可视化

**触发条件**：素材中存在两组或多组数据的对比（A vs B，前 vs 后，计划 vs 实际）。

#### 可视化规则

- **GAP 列**：对比表必须有 GAP/差异列
- **方向箭头**：↑ 改善 / ↓ 恶化 / → 稳定
- **色标差异**：正向用 CI 主色，负向用 CI 主色低透明度
- **禁止**：仅列出两组数据不标注差异

#### Canvas 指令

**S 级**：对比增量简化版：简单的两列 + GAP 列表格。正向：`text-[CI主色] font-bold` + ↑。负向：`text-[CI辅助色]` + ↓。稳定：`text-gray-400` + →。

**M 级**：对比增量标准版：格式化表格 + 视觉化 GAP。每行 GAP 单元格包含方向箭头、百分比变化、小型水平条形图。

**L 级**：对比增量完整版：在 M 级基础上增加多组对比、加权汇总行、关键差异项高亮、差异解释列。

**XL 级**：对比增量交互版：在 L 级基础上增加按维度排序（CSS class toggle）、阈值标注、趋势对比。

### 4. 信息质量标注

**触发条件**：所有 M 级及以上的文档。

#### 可视化规则

每个主要结论的旁边标注证据等级徽章：

| 标记 | 含义 | 视觉 |
|------|------|------|
| 一次数据 | 原始数据、官方声明、实验结果 | 实心圆 + CI 主色 |
| 二次推测 | 分析推导、媒体转述、专家观点 | 半实心圆 + CI 主色 60% |
| 未验证 | 传闻、匿名来源、单一来源 | 空心圆 + CI 主色 20% |

- `[DATA_GAP]` 标记使用警告 callout：`bg-amber-50 border-l-4 border-amber-400 p-4`

#### Canvas 指令

**S 级**：信息质量简化版：不标注个别结论，仅在文档末尾注明整体数据来源概要。

**M 级**：信息质量标准版：核心结论旁标注徽章。一次数据：`bg-[CI主色]/15 text-[CI主色]`。二次推测：`bg-[CI主色]/8 text-[CI主色]/70`。未验证：`bg-gray-100 text-gray-500`。

**L 级**：信息质量完整版：在 M 级基础上增加每个 Section 底部的证据来源汇总、整体文档的信息质量评分、数据空白区域的完整列表。

**XL 级**：信息质量交互版：在 L 级基础上增加 `details/summary` 展开每个来源的详细信息、交叉验证标注、来源可信度评级。

### 5. 趋势方向可视化

**触发条件**：素材中包含时间序列数据或趋势描述。

#### 可视化规则

- **布局**：CSS mini bar + 方向箭头
- **方向箭头**：↗ 加速 / → 稳定 / ↘ 减速
- **导数计算**：**变化率（导数）计算是必须的**，不能仅展示绝对值
- **一句话解说**：每个趋势指标必须有一句话总结

#### Canvas 指令

**S 级**：趋势简化版：仅用方向箭头 + 一句话描述。加速 ↗：`text-[CI主色]`。稳定 →：`text-gray-400`。减速 ↘：`text-[CI辅助色]`。

**M 级**：趋势标准版：CSS mini bar + 方向箭头 + 变化率 + 一句话解说。

**L 级**：趋势完整版：在 M 级基础上增加时间轴上的多指标并排展示、趋势转折点标注、预测区间（虚线，带不确定性范围）。

**XL 级**：趋势交互版：在 L 级基础上增加 CSS 悬停展示详细数据点、多趋势的相关性分析、「如果趋势持续...」的推演。

### 6. 不确定性可视化

**触发条件**：分析中存在显著的信息不确定性或知识空白。

#### 可视化规则

- **独立 Section**：不确定性内容单独成区，不混入确定性结论中
- **视觉区分**：破线边框 + 低透明度背景
- **内容**：信息缺口列表 + 潜在影响 + 建议补充的数据

#### Canvas 指令

**S 级**：不确定性简化版：文档末尾加一段「注意事项」。样式：`border border-dashed border-gray-300 rounded-lg p-4 bg-gray-50/50`。

**M 级**：不确定性标准版：独立「不确定性区域」Section。容器：`border-2 border-dashed rounded-2xl p-6`。两栏内容：左栏 — 信息缺口列表，右栏 — 潜在影响。

**L 级**：不确定性完整版：在 M 级基础上增加不确定性分级、场景分析（最佳/基线/最差）、每个不确定性因素的「如果...」推演。

**XL 级**：不确定性交互版：在 L 级基础上增加 `details/summary` 展开每个不确定性因素的详细分析、敏感性矩阵、风险缓解建议。

### 深度级别汇总

| 可视化类型 | S | M | L | XL |
|-----------|---|---|---|---|
| 因果链 | 起点→终点 | 完整链 | +分支+反馈 | +交互+反事实 |
| 置信度 | 高/中/低徽章 | 进度条+理由 | +分组+汇总 | +论证+敏感性 |
| 对比增量 | 简单GAP表 | +视觉化条形 | +多组+高亮 | +排序+阈值 |
| 信息质量 | 无（仅整体） | 核心结论徽章 | +来源汇总 | +交叉验证 |
| 趋势方向 | 箭头+一句话 | mini bar+变化率 | +转折点+预测 | +相关性+推演 |
| 不确定性 | 末尾注意事项 | 独立Section | +场景分析 | +敏感性矩阵 |
