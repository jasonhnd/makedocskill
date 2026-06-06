# Size-Depth Matrix / サイズ-深度マトリクス / 尺寸-深度矩阵

> Depth control for company documents — board materials, IR / CFO proposals, bilingual JP/ZH documents, and 16:9 decks.

[EN](#english) · [日本語](#japanese) · [中文](#chinese)

---

## English {#english}

> The S/M/L/XL four-level depth control is a core parameter of make-doc-skill. It sets **how hard Brain analyzes and how rigorous QA is** for a company document. This file mirrors the Depth Control table in `SKILL.md`.

### What depth controls — and what it never controls

**Depth controls**: Brain analysis depth, sparring rounds, section count, number of diagrams, QA rigor, and (for 16:9) deck slide count.

**Depth never controls** the anchoring rules. **Numerical fidelity and language lock ALWAYS apply at every size — S, M, L, and XL alike.** Figures, currency symbols, units, and fiscal periods stay exact at every level; the chosen output language governs the whole render chain at every level; `[DATA_GAP]` marks missing data and unverified legal/tax statements are marked draft regardless of size. Choosing S never licenses rounding, fabrication, or language drift.

**Core principle**: Depth is not "how much content" but "how deep the judgment." S is not a trimmed L — it is the same deliverable answered with a sharper, more focused conclusion. A 1-page memo and a full board pack both obey numerical fidelity and language lock; they differ only in Brain depth and QA rigor.

### Four-Level Depth Control Table

| Dimension | S | M | L | XL |
|-----------|---|---|---|-----|
| **Use case** | 1-page exec summary / memo | Standard proposal / explanation | Full board material / IR document | Comprehensive board pack + appendix |
| **Section count** | 3–5 | 5–8 | 8–12 | 12+ |
| **Brain depth** | Core conclusion + actions | + evidence evaluation | + explanatory framework + alternatives | + multi-perspective review + extreme test |
| **Sparring rounds** | 0–1 | 1–2 | 2–3 | 3+ |
| **Diagrams** | 0–1 | 1–2 | 2–4 | 4+ |
| **QA rigor** | Output + fonts + path | + TOC + pagination | + bilingual parity + diagram QA | full Quality Gates + visual contact sheet |
| **Deck slides (if 16:9)** | 3–6 | 6–10 | 10–15 | 15+ |
| **Numerical fidelity** | Always | Always | Always | Always |
| **Language lock** | Always | Always | Always | Always |

### Brain Graded Depth Details

#### S — Core conclusion + actions

**Use case**: 1-page exec summary or memo for a busy board member / CFO who needs the decision, not the dossier.

**Brain execution**: Identify 1 core recommendation, extract its supporting points, generate the required actions. State the conclusion first (pyramid). No alternatives framework, no deep causal digging.

**Sparring (Step 4)**: 0–1 round. Focus: "Is the core recommendation defensible? Any obvious omission a board member would catch?"

**Composition (Step 5)**: 3–5 sections, low-medium information density, 0–1 diagram.

**QA rigor**: Output exists in the delivery folder + readable language-appropriate fonts + correct handoff path. Numerical fidelity and language lock still verified.

#### M — + evidence evaluation

**Use case**: Standard proposal or business explanation (e.g. a CFO proposal). Evidence-supported, balancing depth and readability.

**Brain execution**: Core recommendation + 2–3 supporting arguments, each backed by source evidence and data. Evaluate evidence strength (primary data vs assertion). Surface the strongest counter-argument.

**Sparring (Step 4)**: 1–2 rounds. Round 1: hypothesis challenge. Round 2: blind-spot completion (downside, risk, dilution, regulatory, tax, timeline).

**Composition (Step 5)**: 5–8 sections, medium density, 1–2 diagrams.

**QA rigor**: S checks + TOC present and aligned + correct pagination (chapters start on new pages where required).

#### L — + explanatory framework + alternatives

**Use case**: Full board material or IR document for a board / decision committee that must withstand auditor and investor scrutiny.

**Brain execution**: Complete explanatory framework, pro/con arguments per major conclusion, multi-stakeholder perspective, full evidence evaluation, alternatives considered and rejected with reasons, information-gap identification (`[DATA_GAP]`).

**Sparring (Step 4)**: 2–3 rounds. Round 1: deep hypothesis challenge. Round 2: systematic blind-spot review. Round 3: perspective reconstruction (risk-first / comparison-first / timeline-first framing).

**Composition (Step 5)**: 8–12 sections, medium-high density, 2–4 diagrams.

**QA rigor**: M checks + bilingual parity (JP/ZH sections, tables, and diagram numbering align) + diagram QA (fixed SVG/PNG, arrows land on node edges, no broken Word shapes).

#### XL — + multi-perspective review + extreme test

**Use case**: Comprehensive board pack with appendix; archival reference; multi-perspective review where no dimension is omitted.

**Brain execution**: All L content plus multi-perspective review, systematic rebuttal framework, sensitivity analysis, and an **extreme test**: "what if the core assumption is wrong?"

**Sparring (Step 4)**: 3+ rounds (until no new findings). L rounds plus Round 4: extreme test. Optional further round: cross-domain perspective.

**Composition (Step 5)**: 12+ sections, high density, 4+ diagrams; appendix with supporting tables and references.

**QA rigor**: full Quality Gates (see `SKILL.md`) + visual contact sheet of rendered PDF pages (title page, diagram pages, dense tables, appendix).

### Section Structure by Level

**S**: Section title (message-type, conveys the conclusion) → core information (1–2 paragraphs) → optional 1 KPI / figure → action recommendation.

**M**: Section title → core information (2–3 paragraphs) → evidence / data support → evidence-strength note → optional comparison table or trend.

**L**: Section title → core information (3–4 paragraphs) → full argumentation (pro + con) → diagram → information-quality note → section summary.

**XL**: Section title → core information (4+ paragraphs) → full argumentation framework (multi-source cross-validation, counter + response, sensitivity) → diagram → information-quality + source detail → uncertainty assessment → section summary + cross-references to appendix.

### Output Scale Reference

| Dimension | S | M | L | XL |
|-----------|---|---|---|---|
| Section count | 3–5 | 5–8 | 8–12 | 12+ |
| DOCX pages (approx.) | 1–2 | 3–6 | 8–15 | 15+ with appendix |
| Deck slides (if 16:9) | 3–6 | 6–10 | 10–15 | 15+ |
| Diagrams | 0–1 | 1–2 | 2–4 | 4+ |
| Tables | 0–1 | 1–3 | 3–6 | 6+ |
| Sparring rounds | 0–1 | 1–2 | 2–3 | 3+ |

### Selection Guide

**When to choose S?** A memo or 1-page summary; the audience needs the decision in minutes; an internal informal note. Example: a one-page summary of a mid-term management plan for a busy director.

**When to choose M?** A standard proposal or business explanation needing evidence but not a full board dossier; the common default. Example: a CFO proposal (M–L depending on stakes).

**When to choose L?** A full board material or IR document that must withstand auditor / investor scrutiny with complete pro/con argumentation. Example: the board material for a mid-term management plan submitted by Acme Holdings, Inc. (ticker 0000).

**When to choose XL?** A comprehensive board pack with appendix; archival reference; multiple stakeholders need different angles and an extreme-case stress test.

**If the user does not specify a size, infer it from the deliverable**: a memo = S, a CFO proposal = M–L, a full board material with appendix = L–XL.

### Related Documents

- The 8-step Full-Mode pipeline and where depth is set (Step 2) / applied (Step 4): [PIPELINE.md](./PIPELINE.md)
- Brain / Router / Canvas role design and graded depth in prompts: [PROMPT_ENGINEERING.md](./PROMPT_ENGINEERING.md)
- DOCX / deck / diagram / token hard constraints: [DESIGN_RULES.md](./DESIGN_RULES.md)

---

## 日本語 {#japanese}

> S/M/L/XL の4段階深度制御は make-doc-skill のコアパラメータです。企業文書に対して **Brain がどこまで深く分析し、QA をどこまで厳格に行うか** を決めます。本ファイルは `SKILL.md` の深度制御表をミラーします。

### 深度が制御するもの — そして決して制御しないもの

**深度が制御するもの**：Brain の分析深度、壁打ちのラウンド数、Section 数、図表の数、QA の厳格さ、（16:9 の場合）デッキのスライド枚数。

**深度が決して制御しないもの**：アンカリングルール。**数値忠実性と言語ロックは S・M・L・XL のどのサイズでも常に適用されます。** 数値・通貨記号・単位・会計期間はどの段階でも正確なまま、選択した出力言語がどの段階でもレンダリングチェーン全体を支配し、欠損データは `[DATA_GAP]` で明示、未検証の法務/税務記述はサイズに関わらずドラフト扱いとします。S を選んでも、丸め・捏造・言語のブレが許容されることは決してありません。

**コア原則**：深度は「コンテンツの量」ではなく「判断の深さ」です。S は L の削減版ではなく、同じ成果物をより鋭くフォーカスした結論で答えるものです。1ページのメモも完全な取締役会資料も、ともに数値忠実性と言語ロックに従います。違うのは Brain の深度と QA の厳格さだけです。

### 4段階深度制御表

| 次元 | S | M | L | XL |
|------|---|---|---|-----|
| **適用シーン** | 1ページのエグゼクティブサマリー / メモ | 標準的な提案 / 説明 | 完全な取締役会資料 / IR 文書 | 包括的な取締役会パック + 付録 |
| **Section 数** | 3–5 | 5–8 | 8–12 | 12+ |
| **Brain 深度** | 核心結論 + アクション | + エビデンス評価 | + 説明フレームワーク + 代替案 | + 多視点レビュー + 極端テスト |
| **壁打ちラウンド** | 0–1 | 1–2 | 2–3 | 3+ |
| **図表** | 0–1 | 1–2 | 2–4 | 4+ |
| **QA 厳格度** | 出力 + フォント + パス | + 目次 + ページネーション | + 二言語整合 + 図表 QA | 完全 Quality Gates + ビジュアルコンタクトシート |
| **デッキ枚数（16:9 の場合）** | 3–6 | 6–10 | 10–15 | 15+ |
| **数値忠実性** | 常に | 常に | 常に | 常に |
| **言語ロック** | 常に | 常に | 常に | 常に |

### Brain 分級深度詳解

#### S — 核心結論 + アクション

**適用シーン**：意思決定だけを必要とする多忙な取締役 / CFO 向けの1ページのサマリーまたはメモ。

**Brain 実行内容**：1つの核心提言を識別し、その支持ポイントを抽出、必要なアクションを生成。結論を先に述べる（ピラミッド）。代替案フレームワークや因果の深掘りは行わない。

**壁打ち（Step 4）**：0–1 ラウンド。焦点：「核心提言は擁護可能か？取締役が突くような明白な漏れはないか？」

**構成表（Step 5）**：3–5 Section、低-中の情報密度、図表 0–1。

**QA 厳格度**：納品フォルダに出力が存在 + 言語に適した可読フォント + 正しい受け渡しパス。数値忠実性と言語ロックは引き続き検証。

#### M — + エビデンス評価

**適用シーン**：エビデンスに裏付けられた標準的な提案または事業説明（例：CFO 提案）。深さと可読性のバランス。

**Brain 実行内容**：核心提言 + 2–3 の支持論点、各々をソースのエビデンスとデータで裏付け。エビデンス強度（一次データか断定か）を評価。最も強い反論を提示。

**壁打ち（Step 4）**：1–2 ラウンド。第1：仮説挑戦。第2：盲点補完（下振れ、リスク、希薄化、規制、税務、タイムライン）。

**構成表（Step 5）**：5–8 Section、中程度の密度、図表 1–2。

**QA 厳格度**：S のチェック + 目次が存在し整列 + 正しいページネーション（必要箇所で章が改ページ）。

#### L — + 説明フレームワーク + 代替案

**適用シーン**：監査人や投資家の精査に耐える必要がある取締役会 / 意思決定委員会向けの完全な取締役会資料または IR 文書。

**Brain 実行内容**：完全な説明フレームワーク、主要結論ごとの正反論証、多ステークホルダー視点、完全なエビデンス評価、却下した代替案とその理由、情報ギャップの識別（`[DATA_GAP]`）。

**壁打ち（Step 4）**：2–3 ラウンド。第1：深度仮説挑戦。第2：体系的盲点レビュー。第3：視点再構成（リスク先行 / 比較先行 / タイムライン先行のフレーミング）。

**構成表（Step 5）**：8–12 Section、中-高密度、図表 2–4。

**QA 厳格度**：M のチェック + 二言語整合（JP/ZH の Section・表・図番号が一致）+ 図表 QA（固定 SVG/PNG、矢印がノード端に接続、Word シェイプの破綻なし）。

#### XL — + 多視点レビュー + 極端テスト

**適用シーン**：付録付きの包括的な取締役会パック、アーカイブ用リファレンス、どの次元も省略しない多視点レビュー。

**Brain 実行内容**：L のすべて + 多視点レビュー、体系的反駁フレームワーク、感度分析、そして **極端テスト**：「核心の前提が誤っていたら？」

**壁打ち（Step 4）**：3+ ラウンド（新発見がなくなるまで）。L のラウンド + 第4：極端テスト。オプション：分野横断視点。

**構成表（Step 5）**：12+ Section、高密度、図表 4+、補足表・参考資料を含む付録。

**QA 厳格度**：完全 Quality Gates（`SKILL.md` 参照）+ レンダリング済み PDF ページのビジュアルコンタクトシート（表紙、図表ページ、密なテーブル、付録）。

### Section 構造の差異

**S**：Section タイトル（メッセージ型、結論を伝える）→ コア情報（1–2 段落）→ オプション：1 KPI / 数値 → アクション提案。

**M**：Section タイトル → コア情報（2–3 段落）→ エビデンス / データ裏付け → エビデンス強度注記 → オプション：比較表またはトレンド。

**L**：Section タイトル → コア情報（3–4 段落）→ 完全論証（正面 + 反面）→ 図表 → 情報品質注記 → Section サマリー。

**XL**：Section タイトル → コア情報（4+ 段落）→ 完全論証フレームワーク（多ソースのクロスバリデーション、反論 + 応答、感度）→ 図表 → 情報品質 + ソース明細 → 不確実性評価 → Section サマリー + 付録へのクロスリファレンス。

### 出力規模参考

| 次元 | S | M | L | XL |
|------|---|---|---|---|
| Section 数 | 3–5 | 5–8 | 8–12 | 12+ |
| DOCX ページ数（概算） | 1–2 | 3–6 | 8–15 | 15+（付録込み） |
| デッキ枚数（16:9 の場合） | 3–6 | 6–10 | 10–15 | 15+ |
| 図表数 | 0–1 | 1–2 | 2–4 | 4+ |
| テーブル数 | 0–1 | 1–3 | 3–6 | 6+ |
| 壁打ちラウンド | 0–1 | 1–2 | 2–3 | 3+ |

### 選択ガイド

**S を選ぶべき時**：メモまたは1ページのサマリー、対象は数分で意思決定が必要、社内非公式メモ。例：多忙な取締役向けの中期経営計画の1ページ要約。

**M を選ぶべき時**：エビデンスは必要だが完全な取締役会一式は不要な標準提案または事業説明、最も一般的なデフォルト。例：CFO 提案（重要度により M–L）。

**L を選ぶべき時**：完全な正反論証で監査人 / 投資家の精査に耐える必要がある完全な取締役会資料または IR 文書。例：Acme Holdings, Inc.（ティッカー 0000）が提出する中期経営計画の取締役会資料。

**XL を選ぶべき時**：付録付きの包括的な取締役会パック、アーカイブ用リファレンス、複数のステークホルダーが異なる角度と極端ケースのストレステストを必要とする場合。

**ユーザーがサイズを指定しない場合は、成果物から推定する**：メモ = S、CFO 提案 = M–L、付録付きの完全な取締役会資料 = L–XL。

### 関連ドキュメント

- 8ステップの Full-Mode パイプラインと、深度の設定（Step 2）/ 適用（Step 4）箇所：[PIPELINE.md](./PIPELINE.md)
- Brain / Router / Canvas の役割設計とプロンプト内の分級深度：[PROMPT_ENGINEERING.md](./PROMPT_ENGINEERING.md)
- DOCX / デッキ / 図表 / トークンのハード制約：[DESIGN_RULES.md](./DESIGN_RULES.md)

---

## 中文 {#chinese}

> S/M/L/XL 四级深度控制是 make-doc-skill 的核心参数。它决定对一份公司文档 **Brain 分析有多深、QA 有多严格**。本文件镜像 `SKILL.md` 中的深度控制表。

### 深度控制什么 —— 以及永远不控制什么

**深度控制**：Brain 分析深度、壁打ち（对抗式追问）轮数、Section 数、图表数量、QA 严格度，以及（16:9 时）演示文稿幻灯片张数。

**深度永远不控制**锚定规则。**数值忠实与语言锁定在 S、M、L、XL 每一个尺寸都始终适用。** 数字、货币符号、单位与财政期间在任何级别都保持精确；所选输出语言在任何级别都统辖整条渲染链；缺失数据一律以 `[DATA_GAP]` 标注，未经核实的法务/税务表述无论尺寸大小都标为草案。选择 S 绝不意味着可以四舍五入、捏造或语言漂移。

**核心原则**：深度不是「内容多少」，而是「判断多深」。S 不是 L 的删减版，而是用更锐利、更聚焦的结论回答同一份成果物。一页备忘录与完整董事会材料同样遵守数值忠实与语言锁定，二者之别仅在 Brain 深度与 QA 严格度。

### 四级深度控制表

| 维度 | S | M | L | XL |
|------|---|---|---|-----|
| **适用场景** | 一页高管摘要 / 备忘录 | 标准提案 / 说明 | 完整董事会材料 / IR 文档 | 综合董事会包 + 附录 |
| **Section 数** | 3–5 | 5–8 | 8–12 | 12+ |
| **Brain 深度** | 核心结论 + 行动项 | + 证据评价 | + 解释框架 + 备选方案 | + 多视角审视 + 极端测试 |
| **壁打ち轮数** | 0–1 | 1–2 | 2–3 | 3+ |
| **图表** | 0–1 | 1–2 | 2–4 | 4+ |
| **QA 严格度** | 输出 + 字体 + 路径 | + 目录 + 分页 | + 双语对齐 + 图表 QA | 完整 Quality Gates + 视觉联系表 |
| **演示文稿张数（16:9 时）** | 3–6 | 6–10 | 10–15 | 15+ |
| **数值忠实** | 始终 | 始终 | 始终 | 始终 |
| **语言锁定** | 始终 | 始终 | 始终 | 始终 |

### Brain 分级深度详解

#### S —— 核心结论 + 行动项

**适用场景**：面向只需要决策、不需要完整卷宗的繁忙董事 / CFO 的一页摘要或备忘录。

**Brain 执行内容**：识别 1 个核心建议，提炼其支撑要点，生成所需行动项。结论先行（金字塔）。不做备选方案框架，不做因果深挖。

**壁打ち（Step 4）**：0–1 轮。聚焦：「核心建议是否站得住脚？是否存在董事一眼能看出的明显遗漏？」

**构成表（Step 5）**：3–5 个 Section，低-中信息密度，图表 0–1。

**QA 严格度**：交付文件夹中存在输出 + 语言适配的可读字体 + 正确的交接路径。仍然校验数值忠实与语言锁定。

#### M —— + 证据评价

**适用场景**：有证据支撑的标准提案或业务说明（例如 CFO 提案）。平衡深度与可读性。

**Brain 执行内容**：核心建议 + 2–3 个支撑论点，各以来源证据与数据支撑。评价证据强度（一手数据还是断言）。提出最强反面论据。

**壁打ち（Step 4）**：1–2 轮。第 1 轮：假设挑战。第 2 轮：盲点补全（下行、风险、稀释、监管、税务、时间线）。

**构成表（Step 5）**：5–8 个 Section，中等信息密度，图表 1–2。

**QA 严格度**：S 的检查 + 目录存在且对齐 + 正确分页（需要处章节另起一页）。

#### L —— + 解释框架 + 备选方案

**适用场景**：必须经受审计师与投资者审视的董事会 / 决策委员会的完整董事会材料或 IR 文档。

**Brain 执行内容**：完整解释框架、每个主要结论的正反论证、多利益相关方视角、完整证据评价、已考虑并否决的备选方案及理由、信息缺口识别（`[DATA_GAP]`）。

**壁打ち（Step 4）**：2–3 轮。第 1 轮：深度假设挑战。第 2 轮：系统性盲点审视。第 3 轮：视角重构（风险优先 / 对比优先 / 时间线优先的呈现）。

**构成表（Step 5）**：8–12 个 Section，中-高信息密度，图表 2–4。

**QA 严格度**：M 的检查 + 双语对齐（JP/ZH 的 Section、表格、图号一致）+ 图表 QA（固定 SVG/PNG，箭头精确落在节点边缘，无 Word 形状断裂）。

#### XL —— + 多视角审视 + 极端测试

**适用场景**：带附录的综合董事会包；存档参考；不遗漏任何维度的多视角审视。

**Brain 执行内容**：L 的全部 + 多视角审视、系统性反驳框架、敏感性分析，以及 **极端测试**：「如果核心假设是错的会怎样？」

**壁打ち（Step 4）**：3+ 轮（直到无新发现）。L 的各轮 + 第 4 轮：极端测试。可选追加：跨领域视角。

**构成表（Step 5）**：12+ 个 Section，高信息密度，图表 4+，含支撑表格与参考资料的附录。

**QA 严格度**：完整 Quality Gates（见 `SKILL.md`）+ 已渲染 PDF 页面的视觉联系表（封面、图表页、密集表格、附录）。

### Section 结构差异

**S**：Section 标题（消息型，传达结论）→ 核心信息（1–2 段）→ 可选：1 个 KPI / 数字 → 行动建议。

**M**：Section 标题 → 核心信息（2–3 段）→ 证据 / 数据支撑 → 证据强度标注 → 可选：对比表或趋势。

**L**：Section 标题 → 核心信息（3–4 段）→ 完整论证（正面 + 反面）→ 图表 → 信息质量标注 → 本 Section 小结。

**XL**：Section 标题 → 核心信息（4+ 段）→ 完整论证框架（多来源交叉验证、反面论据 + 回应、敏感性）→ 图表 → 信息质量 + 来源明细 → 不确定性评估 → 本 Section 小结 + 与附录的交叉引用。

### 输出规模参考

| 维度 | S | M | L | XL |
|------|---|---|---|---|
| Section 数 | 3–5 | 5–8 | 8–12 | 12+ |
| DOCX 页数（约） | 1–2 | 3–6 | 8–15 | 15+（含附录） |
| 演示文稿张数（16:9 时） | 3–6 | 6–10 | 10–15 | 15+ |
| 图表数 | 0–1 | 1–2 | 2–4 | 4+ |
| 表格数 | 0–1 | 1–3 | 3–6 | 6+ |
| 壁打ち轮数 | 0–1 | 1–2 | 2–3 | 3+ |

### 选择指南

**什么时候选 S？** 备忘录或一页摘要；受众需要在几分钟内拿到决策；内部非正式便条。例：为繁忙董事准备的中期经营计划一页要点。

**什么时候选 M？** 需要证据但不需要完整董事会卷宗的标准提案或业务说明；最常见的默认选择。例：CFO 提案（依重要程度 M–L）。

**什么时候选 L？** 需以完整正反论证经受审计师 / 投资者审视的完整董事会材料或 IR 文档。例：Acme Holdings, Inc.（股票代码 0000）提交的中期经营计划董事会材料。

**什么时候选 XL？** 带附录的综合董事会包；存档参考；多个利益相关方需要不同角度与极端情形压力测试。

**若用户未指定尺寸，则从成果物推断**：备忘录 = S，CFO 提案 = M–L，带附录的完整董事会材料 = L–XL。

### 与其他文档的关系

- 8 步 Full-Mode 管线，以及深度的设定（Step 2）/ 应用（Step 4）位置：[PIPELINE.md](./PIPELINE.md)
- Brain / Router / Canvas 角色设计与提示词中的分级深度：[PROMPT_ENGINEERING.md](./PROMPT_ENGINEERING.md)
- DOCX / 演示文稿 / 图表 / token 硬约束：[DESIGN_RULES.md](./DESIGN_RULES.md)
