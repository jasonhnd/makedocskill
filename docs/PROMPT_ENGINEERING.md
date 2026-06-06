# Prompt Engineering Specification / プロンプトエンジニアリング仕様 / 提示词工程规范

> Brain → Router → Canvas role design + prompt meta-principles for the company document generator

[EN](#english) · [日本語](#japanese) · [中文](#chinese)

---

## English {#english}

> makedocskill's core methodology is the Brain → Router → Canvas pipeline, achieving high-quality company documents (formal Word/PDF board materials, IR / CFO proposals, bilingual JP/ZH documents, and 16:9 HTML/PDF decks) through carefully designed prompt structures.

### Overview

makedocskill is not a traditional "give AI a paragraph and let it generate" workflow. Through the three-stage pipeline, Brain graded depth, Canvas role definition, and other prompt engineering techniques, it transforms document generation from "one-shot generation" to "structured reasoning + step-by-step verification" — so a board pack is convincing because the material was read correctly and rebuilt, not because a color theme was applied.

### 1. The Three-Stage Pipeline

#### Design Philosophy

The core insight: **Depth comes not from more steps, but from better prompt quality.**

The traditional approach lets AI complete all work at once (understand materials → organize structure → render output), producing shallow, template-like documents that round numbers, miss board questions, and bury the conclusion.

The pipeline decomposes this into three independent stages, each with a clear role:

```
Brain (Thinker) → Router (Decision Maker) → Canvas (Executor)
```

#### Three-Stage Responsibilities

| Pipeline | Role | Input | Output | Core Prompt Pattern |
|----------|------|-------|--------|-------------------|
| Brain | Editor / domain analyst | Source material + company context | Structured, corrected content + section plan | Expert questioning chain |
| Router | Document architect | Brain analysis | Composition plan + renderer choice (formal DOCX / split bilingual / 16:9 deck / HTML) | Deliverable-type mapping table |
| Canvas | Renderer / typesetter | Composition plan + company tokens | Final DOCX/PDF or 16:9 deck | Layout rules + few-shot |

#### Why Three Stages Instead of One?

1. **Separation of concerns**: Brain only analyzes, Canvas only renders. Each stage's prompt is more focused.
2. **Auditable quality**: Each stage produces a reviewable intermediate file. Issues are traceable to a specific stage.
3. **Iterable**: Users can redo just one stage without affecting others.
4. **Prompt quality**: Shorter, more focused prompts per stage yield higher quality AI output.

### 2. Brain Graded Depth

#### Brain's Role Definition

Brain is a combination of "the CFO's board-document editor + critical analyst." It doesn't passively reformat the source; it actively identifies the real deliverable, challenges weak claims, discovers blind spots (downside, dilution, regulatory, tax, precedent), and rebuilds the explanatory structure.

#### Step 1-2: Environmental Perception

Step 1 provides company tokens (brand colors, fonts, DOCX/slide tokens). Step 2 provides deliverable type, audience (board / CFO / IR / regulator), language mode, and depth level (S/M/L/XL) — all setting the analysis framework for Brain.

#### Step 3: Material Digestion

Prompt pattern: "You are a research assistant for a TSE-listed company's finance team. Structurally organize the following source, annotating source type (primary data / secondary inference / unverified) and key figures." Key: no analysis, only organization; forced source annotation; classify by topic, not original order; **preserve every figure, unit, currency, and fiscal period exactly** and quote original-language passages verbatim.

#### Step 4: Deep Analysis (Brain Core)

**S Level**: One-round questioning. Core conclusion (one sentence), obvious omissions, 3-5 supporting points, 1-3 action recommendations.

**M Level**: Two rounds. Round 1 — Hypothesis challenge: Is the main claim defensible? Is the evidence primary data or assertion? What is the strongest counter-argument a board member or auditor would raise? Round 2 — Blind-spot completion: What is missing — downside, risk, dilution, regulatory, tax, precedent, timeline? What will the board ask that the draft does not answer?

**L Level**: Three rounds. Rounds 1-2 plus Round 3 — Perspective reconstruction: Would risk-first / comparison-first / timeline-first framing serve this audience better? Propose an alternative section order. Anchoring rules: only analyze provided material, `[DATA_GAP]` for missing info, no vague filler, every claim needs evidence, **never round or invent a figure**.

**XL Level**: L level plus Round 4 — Extreme testing (what if the core assumption is completely wrong?), Round 5 (optional) — Cross-domain / precedent perspectives.

### 3. Canvas Role Definition

Canvas is "a senior document typesetter + information designer who follows specifications." It makes no editorial decisions, only renders the deliverable: a formal DOCX/PDF or a 1920x1080 HTML/PDF deck.

Canvas prompt structure: role definition → strict constraints (company tokens, DOCX layout rules, deck layout rules, diagram rules, token & brand-color discipline, prohibition rules — see `DESIGN_RULES.md`) → composition table → company tokens → layout-review results.

#### Canvas vs Brain Boundary

| Dimension | Brain Decides | Canvas Executes |
|-----------|--------------|----------------|
| Content | What to say (and that figures stay exact) | How to lay out (DOCX pages / slides) |
| Structure | Section order and logic | Page breaks, grids, tables, diagram placement |
| Depth | How deep to analyze | How dense the page / slide is |
| Color | N/A (doesn't care) | Strictly follows company brand tokens |
| Language | Content language (and language lock) | Document `lang` attribute + JP/ZH fonts |

### 4. Few-shot Strategy

Direct descriptive rules ("use restrained table borders") are far less effective than a concrete worked example (few-shot): a formal DOCX board section, or a single 16:9 slide.

SKILL.md anchors quality with worked examples such as: an Executive Summary section (12pt body, chapter page break, conclusion-first, accent-color heading rule), a KPI / data table (company accent header fill, 10.5–11.5pt table text, exact figures with units), and a comparison table (clean borders, recommended-option emphasis, no fabricated rows). For decks, anchor with a single slide (6px accent header bar, title band, content area, fixed footer).

Principles: few-shots take priority over rule descriptions; company tokens over hardcoded colors/sizes; combine examples for complex sections; extend rather than copy; the figures in any example are illustrative — real renders use the source figures verbatim.

### 5. Content Anchoring Rules

**Pyramid principle**: All sections follow conclusion → supporting arguments → specific data. Readers can stop at any level and still get the core information.

**MECE check**: Sections must be Mutually Exclusive and Collectively Exhaustive.

**Material anchoring**: Only state what the source supports. Information not in the source cannot appear. Mark `[DATA_GAP]` for insufficient data; mark background knowledge `[Supplemental]`.

**Numerical fidelity (non-negotiable for listed-company material)**: Use every figure exactly as in the source. Never round ¥2.4B to "about ¥2B," never invent a number; currency symbols, units, and fiscal periods stay exact. Unverified legal / accounting / tax statements are marked draft/assumption.

**Language lock**: Once the output language is set (Step 2), the entire chain strictly follows it. `03_source_normalized.md` preserves the source language (quotations are not translated); all subsequent files use the output language; the DOCX `lang` attribute and JP/ZH fonts match. For split bilingual output, each language file is rendered and proofread independently with no foreign-language residue (proper nouns excepted).

### 6. Prohibition Rules

**Brain pipeline**: No vague filler, no judgment avoidance, no phenomenon-listing without causation, no fabricated figures / citations / legal-tax conclusions, no surface-level paraphrasing of a weak source, no definitive language for unverified information.

**Canvas pipeline**: No blue/green/orange functional colors when the brand is red/gray, no hardcoded hex outside the token set, no Word freeform flow arrows for complex diagrams (use fixed SVG/PNG), no fabricated copyright/watermarks, no overflowing tables or slides, no `transform: scale()` to "fix" print, no diagram where every node is the accent color.

**Router pipeline**: No ignoring the deliverable-type mapping, no uniform information density across all sections (do not stack high-density sections consecutively), no descriptive titles (must be message-type conveying the conclusion).

### 7. Prompt Design Meta-Principles

1. **Role > Instruction**: Don't say "please improve this" — say "you are the CFO's board-document editor at a TSE-listed company." Role definition naturally brings behavior patterns.
2. **Constraint > Freedom**: Explicit prohibitions are more effective than vague encouragement. "No fabricated figures" beats "please be accurate."
3. **Structure > Prose**: Giving AI a composition table to fill produces higher quality than free-writing the document. The 8-field section blueprint embodies this.
4. **Few-shot > Description**: One worked DOCX section or slide is more precise than ten rules. The examples in SKILL.md are the most direct quality anchors.
5. **Segmented > One-shot**: The 8-step pipeline exists because each step's prompt is shorter and more focused, and AI performs better on narrow, auditable tasks.

### 8. Related Documents

| Document | Relationship to Prompt Engineering |
|----------|----------------------------------|
| [PIPELINE.md](./PIPELINE.md) | The 8-step audited Full-Mode pipeline is the prompt-segmentation execution framework |
| [DESIGN_RULES.md](./DESIGN_RULES.md) | DOCX / deck / diagram / token / brand-color hard constraints are the Canvas prompt constraint set |
| [SIZE_DEPTH_MATRIX.md](./SIZE_DEPTH_MATRIX.md) | S/M/L/XL depth control determines Brain prompt depth and QA rigor |
| [SKILL.md](../SKILL.md) | Sparring, anchoring, and prohibition rules are the Brain prompt core content |

---

## 日本語 {#japanese}

> makedocskill のコア方法論は Brain → Router → Canvas パイプラインであり、精巧に設計されたプロンプト構造を通じて高品質な企業ドキュメント（正式な Word/PDF 取締役会資料、IR / CFO 提案、日中バイリンガル文書、16:9 HTML/PDF デッキ）の生成を実現します。

### 概要

makedocskill は従来の「AI に一段落を与えて生成させる」ワークフローではありません。三段式パイプライン、Brain 分級深度、Canvas ロール定義などのプロンプトエンジニアリング技術を通じて、ドキュメント生成を「一発生成」から「構造化推論 + 段階的検証」のプロセスに変換します — 取締役会資料が説得力を持つのは、カラーテーマを適用したからではなく、素材を正しく読み再構築したからです。

### 1. 三段式パイプライン

#### 設計思想

コアインサイト：**深さはより多くのステップからではなく、より良いプロンプト品質から生まれる。**

従来の方法は AI に全作業を一度に完了させる（素材理解 → 構造組織 → 出力レンダリング）ため、結果は浅くテンプレート的になり、数値を丸め、取締役会の質問を見落とし、結論を埋もれさせます。

パイプラインはこのプロセスを3つの独立段に分解し、各段に明確なロールを持たせます：

```
Brain（思考者）→ Router（意思決定者）→ Canvas（実行者）
```

#### 三段の責務

| パイプライン | ロール | 入力 | 出力 | コアプロンプトパターン |
|------------|------|------|------|-------------------|
| Brain | 編集者 / ドメインアナリスト | 素材 + 企業コンテキスト | 構造化・修正済みコンテンツ + セクション計画 | エキスパート質問チェーン |
| Router | ドキュメントアーキテクト | Brain 分析 | 構成プラン + レンダラー選択（正式 DOCX / 分割バイリンガル / 16:9 デッキ / HTML） | 成果物タイプマッピングテーブル |
| Canvas | レンダラー / 組版者 | 構成プラン + 企業トークン | 最終 DOCX/PDF または 16:9 デッキ | レイアウトルール + few-shot |

#### なぜ1段ではなく3段か？

1. **関心の分離**：Brain は分析のみ、Canvas はレンダリングのみ。各段のプロンプトがより焦点を絞れる。
2. **監査可能な品質**：各段が審査可能な中間ファイルを生成。問題を特定段に追跡可能。
3. **イテレーション可能**：ユーザーは一段だけやり直し、他段に影響なし。
4. **プロンプト品質**：各段のより短く焦点を絞ったプロンプトにより、AI の出力品質が向上。

### 2. Brain 分級深度

#### Brain のロール定義

Brain は「CFO の取締役会資料編集者 + 批判的アナリスト」の組み合わせ。受動的に素材を再整形するのではなく、能動的に真の成果物を識別、弱い主張に挑戦、盲点（下振れ、希薄化、規制、税務、前例）を発見、説明構造を再構築します。

#### Step 1-2：環境認識

Step 1 で企業トークン（ブランドカラー、フォント、DOCX/スライドトークン）。Step 2 で成果物タイプ、オーディエンス（取締役会 / CFO / IR / 規制当局）、言語モード、深度レベル（S/M/L/XL）を取得 — Brain の分析フレームワークを設定。

#### Step 3：素材消化

プロンプトパターン：「あなたは上場企業の財務チームのリサーチアシスタントです。以下の素材を構造化整理し、各情報のソースタイプ（一次データ/二次推測/未検証）とキー数値を注記してください。」キー：分析せず整理のみ、ソース注記を強制、テーマ別に分類、**すべての数値・単位・通貨・会計期間を厳密に保持**し、原言語の文章は逐語的に引用。

#### Step 4：深度分析（Brain コア）

**S 級**：1ラウンド質問。コア結論（一文）、明白な漏れ、3-5 支持ポイント、1-3 アクション提案。

**M 級**：2ラウンド。第1ラウンド — 仮説挑戦：主要主張は防衛可能か？エビデンスは一次データか主張か？取締役や監査人が挙げる最強の反論は？第2ラウンド — 盲点補完：欠落は何か — 下振れ、リスク、希薄化、規制、税務、前例、タイムライン？ドラフトが答えていない取締役会の質問は？

**L 級**：3ラウンド。1-2 ラウンド + 第3ラウンド — 視点再構成：リスク先行 / 比較先行 / 時系列先行の枠組みがこのオーディエンスに有効か？代替セクション順序を提案。アンカリングルール：提供素材のみ分析、`[DATA_GAP]` で不足情報を記載、空虚な表現禁止、全主張にエビデンス必要、**数値の丸めや捏造を禁止**。

**XL 級**：L 級 + 第4ラウンド — 極端テスト（コア仮説が完全に間違っていたら？）、第5ラウンド（オプション）— 分野横断 / 前例視点。

### 3. Canvas ロール定義

Canvas は「仕様に従う上級ドキュメント組版者 + 情報デザイナー」。編集判断は行わず、成果物のレンダリングのみを行う：正式な DOCX/PDF または 1920x1080 HTML/PDF デッキ。

Canvas プロンプト構造：ロール定義 → 厳格な制約（企業トークン、DOCX レイアウトルール、デッキレイアウトルール、ダイアグラムルール、トークン & ブランドカラー規律、禁止ルール — `DESIGN_RULES.md` 参照）→ 構成表 → 企業トークン → レイアウト審査結果。

#### Canvas と Brain の境界

| 次元 | Brain が決定 | Canvas が実行 |
|------|------------|-------------|
| コンテンツ | 何を言うか（数値は厳密に維持） | どう配置するか（DOCX ページ / スライド） |
| 構造 | Section 順序と論理 | ページ区切り、グリッド、表、ダイアグラム配置 |
| 深度 | 分析の深さ | ページ / スライドの密度 |
| 色彩 | 無関係 | 企業ブランドトークンを厳格に遵守 |
| 言語 | コンテンツ言語（言語ロック） | ドキュメント `lang` 属性 + 日中フォント |

### 4. Few-shot 戦略

記述的ルール（「控えめな表罫線を使用」）は具体的なワークド例（few-shot）よりはるかに効果が低い：正式な DOCX 取締役会セクション、または1枚の 16:9 スライド。

SKILL.md は次のようなワークド例で品質をアンカー：Executive Summary セクション（12pt 本文、章ページ区切り、結論先行、アクセントカラー見出し罫線）、KPI / データ表（企業アクセントヘッダー塗り、10.5–11.5pt 表テキスト、単位付き厳密数値）、比較表（クリーンな罫線、推奨案の強調、捏造行なし）。デッキでは1枚のスライド（6px アクセントヘッダーバー、タイトルバンド、コンテンツエリア、固定フッター）でアンカー。

原則：few-shot はルール記述に優先、企業トークンはハードコード色/サイズに優先、複雑なセクションでは例を組み合わせ、コピーでなく拡張、例中の数値は説明用であり実レンダリングは素材の数値を逐語使用。

### 5. コンテンツアンカリングルール

**ピラミッド原則**：全 Section は結論 → 支持論拠 → 具体データの順。読者は任意のレベルで止めてもコア情報を得られる。

**MECE チェック**：Section は相互排他的かつ網羅的でなければならない。

**素材アンカリング**：素材が支持する内容のみ記載。素材にない情報は記載不可。データ不足は `[DATA_GAP]`、背景知識は `[Supplemental]` を記載。

**数値忠実性（上場企業資料では譲歩不可）**：すべての数値を素材どおり厳密に使用。¥24億を「約¥20億」と丸めない、数値を捏造しない；通貨記号・単位・会計期間は厳密に維持。未検証の法務 / 会計 / 税務記述はドラフト/仮定として明示。

**言語ロック**：出力言語が確定（Step 2）した後、全チェーンが厳格に遵守。`03_source_normalized.md` は素材原言語を保持（引用は翻訳しない）、以降のファイルは出力言語、DOCX `lang` 属性と日中フォントは対応。分割バイリンガル出力では各言語ファイルを独立にレンダリング・校正し、外国語残留なし（固有名詞を除く）。

### 6. 禁止出力ルール

**Brain パイプライン**：空虚な表現禁止、判断回避禁止、因果なしの現象列挙禁止、数値 / 引用 / 法務税務結論の捏造禁止、弱い素材の表面的言い換え禁止、未検証情報への確定的言語禁止。

**Canvas パイプライン**：ブランドが赤/グレーのとき青/緑/オレンジの機能色禁止、トークン外のハードコード hex 禁止、複雑なダイアグラムへの Word フリーフォーム矢印禁止（固定 SVG/PNG を使用）、偽著作権/ウォーターマーク禁止、表やスライドのオーバーフロー禁止、印刷を「直す」ための `transform: scale()` 禁止、全ノードがアクセントカラーのダイアグラム禁止。

**Router パイプライン**：成果物タイプマッピングの無視禁止、全 Section 同一情報密度禁止（高密度セクションの連続配置禁止）、記述型タイトル禁止（結論を伝えるメッセージ型必須）。

### 7. プロンプト設計メタ原則

1. **ロール > 指示**：「これを改善してください」ではなく「あなたは上場企業の CFO の取締役会資料編集者です」。ロール定義が自然に行動パターンを導く。
2. **制約 > 自由**：明示的禁止は曖昧な奨励より効果的。「数値捏造禁止」は「正確にしてください」より有用。
3. **構造 > 散文**：AI に構成表を埋めさせる方が、ドキュメントの自由記述より高品質。8フィールドのセクションブループリントがこの原則を体現。
4. **Few-shot > 記述**：1つのワークド DOCX セクションまたはスライドは10のルールより正確。SKILL.md の例が最も直接的な品質アンカー。
5. **分割 > 一括**：8ステップパイプラインが存在する理由：各ステップのプロンプトが短く焦点を絞れ、AI は狭く監査可能なタスクでより良いパフォーマンスを発揮。

### 8. 関連ドキュメント

| ドキュメント | プロンプトエンジニアリングとの関係 |
|------------|-------------------------------|
| [PIPELINE.md](./PIPELINE.md) | 8ステップの監査付き Full モードパイプラインはプロンプト分割の実行フレームワーク |
| [DESIGN_RULES.md](./DESIGN_RULES.md) | DOCX / デッキ / ダイアグラム / トークン / ブランドカラーのハード制約は Canvas プロンプトの制約セット |
| [SIZE_DEPTH_MATRIX.md](./SIZE_DEPTH_MATRIX.md) | S/M/L/XL 深度制御は Brain プロンプトの深度と QA 厳格度を決定 |
| [SKILL.md](../SKILL.md) | スパーリング、アンカリング、禁止ルールは Brain プロンプトのコアコンテンツ |

---

## 中文 {#chinese}

> makedocskill 的核心方法论是 Brain → Router → Canvas 管道，通过精心设计的提示词结构实现高质量的企业文档生成（正式 Word/PDF 董事会材料、IR / CFO 提案、中日双语文档、16:9 HTML/PDF 演示）。

### 概述

makedocskill 不是传统的「给 AI 一段话让它生成」的工作流。它通过三段式管道、Brain 分级深度、Canvas 角色定义等提示词工程技术，将文档生成从「一次性生成」转变为「结构化推理 + 分步验证」的过程 — 董事会材料之所以有说服力，是因为正确读懂并重建了素材，而不是套用了配色主题。

### 1. 三段式管道

#### 设计理念

核心洞察：**深度不是来自更多的步骤，而是来自更好的 prompt 质量。**

传统方法是让 AI 一次完成全部工作（理解素材 → 组织结构 → 渲染输出），结果往往浅层且模板化，会把数字四舍五入、漏掉董事会的质疑、把结论埋没。

管道将这个过程分解为三段独立管道，每段有明确的角色和职责：

```
Brain（思考者）→ Router（决策者）→ Canvas（执行者）
```

#### 三段职责

| 管道 | 角色 | 输入 | 输出 | 核心 prompt 模式 |
|------|------|------|------|----------------|
| Brain | 编辑 / 领域分析师 | 素材 + 公司语境 | 结构化、修正后的内容 + 章节计划 | 专家追问链 |
| Router | 文档架构师 | Brain 分析 | 构成方案 + 渲染器选择（正式 DOCX / 分语言双语 / 16:9 演示 / HTML） | 交付物类型映射表 |
| Canvas | 渲染器 / 排版师 | 构成方案 + 公司令牌 | 最终 DOCX/PDF 或 16:9 演示 | 布局规则 + 少样本 |

#### 为什么要三段而不是一段？

1. **关注点分离**：Brain 只管分析，Canvas 只管渲染。各段的 prompt 更聚焦。
2. **质量可审**：每段产出一个可审查的中间文件。问题可以追溯到具体的管道段。
3. **可迭代**：用户可以只重做某一段而不影响其他段。
4. **prompt 质量**：每段的 prompt 更短、更聚焦，AI 的输出质量更高。

### 2. Brain 分级深度

#### Brain 的角色定义

Brain 是「CFO 的董事会文档编辑 + 批判性分析师」的组合。它不是被动地重新排版素材，而是主动地识别真正的交付物、质疑薄弱论点、发现盲点（下行风险、稀释、监管、税务、先例）、重建解释结构。

#### Step 1-2：环境感知

Step 1 提供公司令牌（品牌色、字体、DOCX/幻灯片令牌）。Step 2 提供交付物类型、受众（董事会 / CFO / IR / 监管方）、语言模式、深度级别（S/M/L/XL）— 为 Brain 设定分析框架。

#### Step 3：素材消化

prompt 模式：「你是一家上市公司财务团队的研究助理。请结构化整理以下素材，标注每条信息的来源类型（一次数据/二次推测/未验证）和关键数字。」关键：不做分析只做整理，强制标注信息来源，按主题分类，**严格保留所有数字、单位、币种和会计期间**，原始语言的段落逐字引用。

#### Step 4：深度分析（Brain 核心）

**S 级**：一轮追问。核心结论（一句话）、明显遗漏、3-5 个支撑要点、1-3 个行动建议。

**M 级**：两轮追问。第 1 轮 — 假设挑战：主要主张是否站得住脚？证据是一次数据还是断言？董事或审计师会提出的最强反驳是什么？第 2 轮 — 盲点补完：缺少什么 — 下行风险、风险、稀释、监管、税务、先例、时间线？草稿没有回答的董事会问题是什么？

**L 级**：三轮追问。1-2 轮 + 第 3 轮 — 视角重构：风险优先 / 对比优先 / 时间线优先的框架是否更适合这一受众？提出替代章节顺序。锚定规则：仅分析提供的素材、`[DATA_GAP]` 标注不足信息、禁止空泛表述、所有主张需证据支撑、**禁止四舍五入或捏造数字**。

**XL 级**：L 级 + 第 4 轮 — 极端测试（如果核心假设完全错误会怎样？）、第 5 轮（可选）— 跨领域 / 先例视角。

### 3. Canvas 角色定义

Canvas 是「遵循规范的高级文档排版师 + 信息设计师」。它不做编辑决策，只渲染交付物：正式 DOCX/PDF 或 1920x1080 HTML/PDF 演示。

Canvas prompt 结构：角色定义 → 严格约束（公司令牌、DOCX 布局规则、演示布局规则、图示规则、令牌 & 品牌色纪律、禁止规则 — 见 `DESIGN_RULES.md`）→ 构成表 → 公司令牌 → 布局审查结果。

#### Canvas 与 Brain 的明确边界

| 维度 | Brain 决定 | Canvas 执行 |
|------|-----------|------------|
| 内容 | 说什么（数字保持精确） | 怎么排版（DOCX 页面 / 幻灯片） |
| 结构 | Section 顺序和逻辑 | 分页、网格、表格、图示摆放 |
| 深度 | 分析多深 | 页面 / 幻灯片的密度 |
| 色彩 | 无（不关心） | 严格遵循公司品牌令牌 |
| 语言 | 内容语言（语言锁定） | 文档 `lang` 属性 + 中日字体 |

### 4. 少样本策略

直接给 AI 描述性规则（「使用克制的表格边框」）效果远不如给一个具体的范例（少样本）：一个正式的 DOCX 董事会章节，或一张 16:9 幻灯片。

SKILL.md 用以下范例锚定质量：Executive Summary 章节（12pt 正文、章节分页、结论优先、强调色标题分隔线）、KPI / 数据表（公司强调色表头填充、10.5–11.5pt 表格文本、带单位的精确数字）、对比表（干净边框、推荐方案高亮、无捏造行）。演示则用单张幻灯片（6px 强调色页眉条、标题带、内容区、固定页脚）锚定。

原则：少样本优先于规则描述；公司令牌优先于硬编码色/字号；复杂章节可组合范例；扩展而非复制；范例中的数字仅作示意，实际渲染逐字使用素材数字。

### 5. 内容锚定规则

**金字塔原则**：所有 Section 遵循结论 → 支撑论据 → 具体数据。读者在任意层级停止阅读都能获得核心信息。

**MECE 检验**：Section 之间的内容必须互斥且穷尽。

**素材锚定**：仅陈述素材支持的内容。素材中没有的信息不得出现。数据不足标注 `[DATA_GAP]`，背景知识标注 `[Supplemental]`。

**数值忠实（上市公司材料不可妥协）**：所有数字按素材原样精确使用。不把 24 亿日元四舍五入为「约 20 亿日元」，不捏造数字；币种符号、单位、会计期间保持精确。未验证的法律 / 会计 / 税务陈述标注为草稿/假设。

**语言锁定**：输出语言确定（Step 2）后，全链路严格遵守。`03_source_normalized.md` 保留素材原始语言（引用不翻译），其后文件用输出语言，DOCX `lang` 属性与中日字体对应。分语言双语输出时，每个语言文件独立渲染与校对，无外语残留（专有名词除外）。

### 6. 禁止输出规则

**Brain 管道**：禁止空泛表述、回避判断、纯罗列现象无因果、捏造数字 / 引用 / 法律税务结论、对薄弱素材的表面化复述、对未验证信息使用确定性表述。

**Canvas 管道**：当品牌为红/灰时禁止蓝/绿/橙功能色、禁止令牌外硬编码 hex、禁止用 Word 自由流程箭头画复杂图示（改用固定 SVG/PNG）、禁止虚假版权/水印、禁止表格或幻灯片溢出、禁止用 `transform: scale()`「修正」打印、禁止全部节点都是强调色的图示。

**Router 管道**：禁止忽视交付物类型映射、禁止所有 Section 同一信息密度（禁止连续堆叠高密度章节）、禁止描述型标题（必须是传递结论的消息型）。

### 7. Prompt 设计的元原则

1. **角色 > 指令**：不要说「请改进这个」，而是说「你是上市公司 CFO 的董事会文档编辑」。角色定义自然带出行为模式。
2. **约束 > 自由**：明确禁止比笼统鼓励更有效。「禁止捏造数字」比「请准确」更有用。
3. **结构 > 散文**：给 AI 一个构成表填写比让 AI 自由发挥文档质量更高。8 字段章节蓝图就是这个原则的体现。
4. **少样本 > 描述**：一个范例 DOCX 章节或幻灯片比十条规则更精确。SKILL.md 中的范例就是最直接的质量锚点。
5. **分段 > 一次**：8 步管线的存在理由：每一步的 prompt 更短更聚焦，AI 在狭窄、可审计的任务上表现更好。

### 8. 与其他文档的关系

| 文档 | 与 Prompt Engineering 的关系 |
|------|---------------------------|
| [PIPELINE.md](./PIPELINE.md) | 8 步带审计的 Full 模式管线是 prompt 分段的执行框架 |
| [DESIGN_RULES.md](./DESIGN_RULES.md) | DOCX / 演示 / 图示 / 令牌 / 品牌色硬性约束是 Canvas prompt 的约束集 |
| [SIZE_DEPTH_MATRIX.md](./SIZE_DEPTH_MATRIX.md) | S/M/L/XL 深度控制决定 Brain prompt 的深度与 QA 严格度 |
| [SKILL.md](../SKILL.md) | 陪练、锚定、禁止规则是 Brain prompt 的核心内容 |
