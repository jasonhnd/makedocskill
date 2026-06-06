# makedocskill Documentation Index / makedocskill ドキュメント索引 / makedocskill 文档索引

> make-doc-skill v4 — Company Document Generator. Brain -> Router -> Canvas intelligence pipeline for board materials, IR / CFO proposals, bilingual JP/ZH documents, and 16:9 decks (real DOCX/PDF/HTML). HTML visual documents are an optional output mode. Methodology derived from the EIP (Explain In Picture) project.

[EN](#english) · [日本語](#japanese) · [中文](#chinese)

---

## English {#english}

> make-doc-skill v4 generates company-specific documents — formal Word/PDF board materials, IR / CFO proposals, bilingual JP/ZH deliverables, and 1920x1080 decks — through a Brain -> Router -> Canvas pipeline that infers the real deliverable, rebuilds structure, locks numbers and language, then renders and verifies real output. The EIP-derived HTML machinery is preserved as an optional HTML output mode. Methodology derived from the EIP (Explain In Picture) project.

### Document Overview

| Document | Content | Reading Suggestion |
|----------|---------|-------------------|
| **Company-document core** | | |
| [PIPELINE.md](./PIPELINE.md) | Company-document 8-step Full-Mode pipeline (01_company_tokens -> 08_pdf_qa) | Read to understand the audited execution flow |
| [PROMPT_ENGINEERING.md](./PROMPT_ENGINEERING.md) | Brain / Router / Canvas role design for documents + prompt meta-principles | Read to understand the methodology |
| [DESIGN_RULES.md](./DESIGN_RULES.md) | DOCX / deck / diagram / token / brand-color hard constraints | Hard constraints for DOCX, decks, and diagrams |
| [SIZE_DEPTH_MATRIX.md](./SIZE_DEPTH_MATRIX.md) | Company-document S/M/L/XL depth control | Reference when choosing S/M/L/XL |
| [ARCHITECTURE.md](./ARCHITECTURE.md) | Brain -> Router -> Canvas three-layer architecture | Read when first learning about makedocskill |
| **HTML output mode (optional)** | | |
| [TEMPLATES.md](./TEMPLATES.md) | 18 HTML visual template reference | Consult when producing an HTML visual document |
| [CONTENT_STRATEGIES.md](./CONTENT_STRATEGIES.md) | 28 content strategy reference (HTML mode) | Consult for HTML analysis angles |
| [DEPTH_VISUALIZATION.md](./DEPTH_VISUALIZATION.md) | HTML depth-visualization rules | Consult for HTML data visualization |

### Reading Paths

#### Quick Overview (10 minutes)

1. [ARCHITECTURE.md](./ARCHITECTURE.md) — Understand the Brain -> Router -> Canvas pipeline and company-document positioning
2. [SIZE_DEPTH_MATRIX.md](./SIZE_DEPTH_MATRIX.md) — Understand the differences between S/M/L/XL

#### Full Understanding (30 minutes)

1. [ARCHITECTURE.md](./ARCHITECTURE.md) — Complete architecture picture
2. [PIPELINE.md](./PIPELINE.md) — Company-document execution flow
3. [PROMPT_ENGINEERING.md](./PROMPT_ENGINEERING.md) — Methodology
4. [DESIGN_RULES.md](./DESIGN_RULES.md) — DOCX / deck / diagram constraints
5. [SIZE_DEPTH_MATRIX.md](./SIZE_DEPTH_MATRIX.md) — Depth control

#### Usage Reference (as needed)

- Check DOCX / deck / diagram rules → [DESIGN_RULES.md](./DESIGN_RULES.md)
- Produce an HTML visual document → [TEMPLATES.md](./TEMPLATES.md)
- Look up HTML strategies → [CONTENT_STRATEGIES.md](./CONTENT_STRATEGIES.md)
- Check HTML visualization rules → [DEPTH_VISUALIZATION.md](./DEPTH_VISUALIZATION.md)

### Core Concepts Quick Reference

#### Three-Layer Pipeline

- **Brain** (editor + domain analyst): infer the real deliverable, rebuild structure, sparring, lock numbers and language → Steps 3-4
- **Router** (document architect): deliverable type → output family (DOCX / split bilingual / 16:9 deck / HTML) → section schema + renderer → Step 5
- **Canvas** (renderer + typesetter): apply tokens + layout rules → render DOCX/HTML → export PDF → QA → Steps 7-8

#### Company-Document 8-Step Pipeline

```
Step 1 Company tokens → Step 2 Document brief → Step 3 Source normalized → Step 4 Codex sparring →
Step 5 Composition plan → Step 6 Layout review → Step 7 Render log → Step 8 PDF QA
(01_company_tokens.md → 08_pdf_qa.md)
```

#### Key Numbers

- **4** output families (formal DOCX/PDF, split JP/ZH, 16:9 HTML/PDF deck, optional HTML visual)
- **4** depth levels (S/M/L/XL)
- **8** company-document pipeline steps
- **2** modes (Quick Mode / Full Mode)
- **3** sparring dimensions (hypothesis challenge, blind-spot completion, perspective reconstruction)
- HTML output mode reference: **18** templates, **28** strategies, **16** components, **6** depth visualizations

### Relationship with EIP

make-doc-skill carries forward the core methodology of EIP (Explain In Picture), re-pointed from a visual-document web app at company documents:

- Brain-Router-Canvas pipeline → carried forward, now mapping to DOCX / split bilingual / deck / HTML output families
- 8-step pipeline → re-pointed to company documents (company tokens, source normalization, sparring, render, PDF QA)
- DOCX / deck / diagram / token rules → company-document design constraints
- Sparring, anchoring, and prohibition rules → carried forward and tightened for listed-company material
- EIP-derived HTML machinery (18 templates / 28 strategies / components / depth visualization) → preserved as the optional HTML output mode

---

## 日本語 {#japanese}

> make-doc-skill v4 は企業固有のドキュメント —— 正式 Word/PDF 取締役会資料、IR / CFO 提案、日中バイリンガル成果物、1920x1080 デック —— を Brain -> Router -> Canvas パイプラインで生成します。本当の成果物を推論し、構造を再構築し、数値と言語をロックし、本物の出力をレンダリングして検証します。EIP 由来の HTML 機構はオプションの HTML 出力モードとして保持されています。方法論は EIP (Explain In Picture) プロジェクトに由来します。

### ドキュメント一覧

| ドキュメント | 内容 | 読み方の提案 |
|------------|------|------------|
| **企業ドキュメントのコア** | | |
| [PIPELINE.md](./PIPELINE.md) | 企業ドキュメント 8 ステップ Full-Mode パイプライン（01_company_tokens -> 08_pdf_qa） | 監査される実行フローを理解する際に読む |
| [PROMPT_ENGINEERING.md](./PROMPT_ENGINEERING.md) | ドキュメント向け Brain / Router / Canvas 役割設計 + プロンプトメタ原則 | 方法論を理解する際に読む |
| [DESIGN_RULES.md](./DESIGN_RULES.md) | DOCX / デック / 図 / トークン / ブランドカラーのハード制約 | DOCX・デック・図のハード制約 |
| [SIZE_DEPTH_MATRIX.md](./SIZE_DEPTH_MATRIX.md) | 企業ドキュメント S/M/L/XL 深度制御 | S/M/L/XL 選択時に参考 |
| [ARCHITECTURE.md](./ARCHITECTURE.md) | Brain -> Router -> Canvas 3 層アーキテクチャ | makedocskill を初めて理解する際に読む |
| **HTML 出力モード（オプション）** | | |
| [TEMPLATES.md](./TEMPLATES.md) | 18 種の HTML ビジュアルテンプレート参考 | HTML ビジュアルドキュメント生成時に参照 |
| [CONTENT_STRATEGIES.md](./CONTENT_STRATEGIES.md) | 28 種のコンテンツ戦略参考（HTML モード） | HTML の分析角度を参照 |
| [DEPTH_VISUALIZATION.md](./DEPTH_VISUALIZATION.md) | HTML 深度可視化ルール | HTML データ可視化を参照 |

### 読み方ガイド

#### クイック概要（10分）

1. [ARCHITECTURE.md](./ARCHITECTURE.md) — Brain -> Router -> Canvas パイプラインと企業ドキュメントの位置づけを理解する
2. [SIZE_DEPTH_MATRIX.md](./SIZE_DEPTH_MATRIX.md) — S/M/L/XL の違いを理解する

#### 完全理解（30分）

1. [ARCHITECTURE.md](./ARCHITECTURE.md) — アーキテクチャ全体像
2. [PIPELINE.md](./PIPELINE.md) — 企業ドキュメントの実行フロー
3. [PROMPT_ENGINEERING.md](./PROMPT_ENGINEERING.md) — 方法論
4. [DESIGN_RULES.md](./DESIGN_RULES.md) — DOCX / デック / 図の制約
5. [SIZE_DEPTH_MATRIX.md](./SIZE_DEPTH_MATRIX.md) — 深度制御

#### 利用参考（必要に応じて）

- DOCX / デック / 図のルール確認 → [DESIGN_RULES.md](./DESIGN_RULES.md)
- HTML ビジュアルドキュメント生成 → [TEMPLATES.md](./TEMPLATES.md)
- HTML 戦略検索 → [CONTENT_STRATEGIES.md](./CONTENT_STRATEGIES.md)
- HTML 可視化ルール確認 → [DEPTH_VISUALIZATION.md](./DEPTH_VISUALIZATION.md)

### コアコンセプト早見表

#### 3 層パイプライン

- **Brain**（編集者 + ドメインアナリスト）：本当の成果物を推論、構造を再構築、スパーリング、数値と言語をロック → Step 3-4
- **Router**（ドキュメントアーキテクト）：成果物タイプ → 出力ファミリー（DOCX / 分割バイリンガル / 16:9 デック / HTML）→ セクションスキーマ + レンダラー → Step 5
- **Canvas**（レンダラー + 組版者）：トークン + レイアウトルール適用 → DOCX/HTML レンダリング → PDF 書き出し → QA → Step 7-8

#### 企業ドキュメント 8 ステップパイプライン

```
Step 1 企業トークン → Step 2 ドキュメントブリーフ → Step 3 ソース正規化 → Step 4 Codex スパーリング →
Step 5 コンポジション計画 → Step 6 レイアウトレビュー → Step 7 レンダリングログ → Step 8 PDF QA
(01_company_tokens.md → 08_pdf_qa.md)
```

#### 主要数字

- **4** 出力ファミリー（正式 DOCX/PDF、日中分割、16:9 HTML/PDF デック、オプション HTML ビジュアル）
- **4** 段階の深度制御（S/M/L/XL）
- **8** ステップの企業ドキュメントパイプライン
- **2** モード（Quick Mode / Full Mode）
- **3** スパーリング次元（仮説への挑戦、死角の補完、視点の再構成）
- HTML 出力モード参考：**18** テンプレート、**28** 戦略、**16** コンポーネント、**6** 深度可視化

### EIP との関係

make-doc-skill は EIP (Explain In Picture) のコア方法論を引き継ぎ、ビジュアルドキュメント Web アプリから企業ドキュメントへ向け直しました：

- Brain-Router-Canvas パイプライン → 引き継ぎ、DOCX / 分割バイリンガル / デック / HTML 出力ファミリーへのマッピングに
- 8 ステップパイプライン → 企業ドキュメントへ向け直し（企業トークン、ソース正規化、スパーリング、レンダリング、PDF QA）
- DOCX / デック / 図 / トークンルール → 企業ドキュメントのデザイン制約
- スパーリング、アンカリング、禁止ルール → 引き継ぎ、上場企業資料向けに強化
- EIP 由来の HTML 機構（18 テンプレート / 28 戦略 / コンポーネント / 深度可視化）→ オプションの HTML 出力モードとして保持

---

## 中文 {#chinese}

> make-doc-skill v4 通过 Brain -> Router -> Canvas 管线生成公司专属文档 —— 正式 Word/PDF 董事会材料、IR / CFO 提案、中日双语交付物和 1920x1080 演示文稿。它推断真正的交付物、重建结构、锁定数字与语言，然后渲染并验证真实输出。源自 EIP 的 HTML 机制保留为可选的 HTML 输出模式。方法论源自 EIP (Explain In Picture) 项目。

### 文档总览

| 文档 | 内容 | 阅读建议 |
|------|------|---------|
| **公司文档核心** | | |
| [PIPELINE.md](./PIPELINE.md) | 公司文档 8 步 Full-Mode 管线（01_company_tokens -> 08_pdf_qa） | 理解受审计的执行流程时阅读 |
| [PROMPT_ENGINEERING.md](./PROMPT_ENGINEERING.md) | 面向文档的 Brain / Router / Canvas 角色设计 + 提示词元原则 | 理解方法论时阅读 |
| [DESIGN_RULES.md](./DESIGN_RULES.md) | DOCX / 演示 / 图示 / token / 品牌色硬性约束 | DOCX、演示与图示的硬性约束 |
| [SIZE_DEPTH_MATRIX.md](./SIZE_DEPTH_MATRIX.md) | 公司文档 S/M/L/XL 深度控制 | 选择 S/M/L/XL 时参考 |
| [ARCHITECTURE.md](./ARCHITECTURE.md) | Brain -> Router -> Canvas 三层架构 | 首次了解 makedocskill 时阅读 |
| **HTML 输出模式（可选）** | | |
| [TEMPLATES.md](./TEMPLATES.md) | 18 种 HTML 可视化模板参考 | 生成 HTML 可视化文档时查阅 |
| [CONTENT_STRATEGIES.md](./CONTENT_STRATEGIES.md) | 28 种内容策略参考（HTML 模式） | 查阅 HTML 分析角度 |
| [DEPTH_VISUALIZATION.md](./DEPTH_VISUALIZATION.md) | HTML 深度可视化规则 | 查阅 HTML 数据可视化 |

### 阅读路径

#### 快速了解（10 分钟）

1. [ARCHITECTURE.md](./ARCHITECTURE.md) — 理解 Brain -> Router -> Canvas 管线与公司文档定位
2. [SIZE_DEPTH_MATRIX.md](./SIZE_DEPTH_MATRIX.md) — 理解 S/M/L/XL 的差异

#### 完整理解（30 分钟）

1. [ARCHITECTURE.md](./ARCHITECTURE.md) — 架构全貌
2. [PIPELINE.md](./PIPELINE.md) — 公司文档执行流程
3. [PROMPT_ENGINEERING.md](./PROMPT_ENGINEERING.md) — 方法论
4. [DESIGN_RULES.md](./DESIGN_RULES.md) — DOCX / 演示 / 图示约束
5. [SIZE_DEPTH_MATRIX.md](./SIZE_DEPTH_MATRIX.md) — 深度控制

#### 使用参考（按需查阅）

- 查 DOCX / 演示 / 图示规则 → [DESIGN_RULES.md](./DESIGN_RULES.md)
- 生成 HTML 可视化文档 → [TEMPLATES.md](./TEMPLATES.md)
- 查 HTML 策略 → [CONTENT_STRATEGIES.md](./CONTENT_STRATEGIES.md)
- 看 HTML 可视化规则 → [DEPTH_VISUALIZATION.md](./DEPTH_VISUALIZATION.md)

### 核心概念速查

#### 三层管线

- **Brain**（编辑 + 领域分析师）：推断真正的交付物、重建结构、壁打ち、锁定数字与语言 → Step 3-4
- **Router**（文档架构师）：交付物类型 → 输出族（DOCX / 双语拆分 / 16:9 演示 / HTML）→ 章节结构 + 渲染器 → Step 5
- **Canvas**（渲染器 + 排版师）：套用 token + 版式规则 → 渲染 DOCX/HTML → 导出 PDF → QA → Step 7-8

#### 公司文档 8 步管线

```
Step 1 公司 token → Step 2 文档简报 → Step 3 原始资料规范化 → Step 4 Codex 壁打ち →
Step 5 构图方案 → Step 6 版式审查 → Step 7 渲染日志 → Step 8 PDF QA
(01_company_tokens.md → 08_pdf_qa.md)
```

#### 关键数字

- **4** 个输出族（正式 DOCX/PDF、中日拆分、16:9 HTML/PDF 演示、可选 HTML 可视化）
- **4** 级深度控制（S/M/L/XL）
- **8** 步公司文档管线
- **2** 种模式（Quick Mode / Full Mode）
- **3** 个壁打ち维度（假设挑战、盲点补全、视角重构）
- HTML 输出模式参考：**18** 模板、**28** 策略、**16** 组件、**6** 深度可视化

### 与 EIP 的关系

make-doc-skill 继承了 EIP (Explain In Picture) 的核心方法论，并从可视化文档 Web 应用重新瞄准公司文档：

- Brain-Router-Canvas 管线 → 继承，现映射到 DOCX / 双语拆分 / 演示 / HTML 输出族
- 8 步管线 → 重新瞄准公司文档（公司 token、原始资料规范化、壁打ち、渲染、PDF QA）
- DOCX / 演示 / 图示 / token 规则 → 公司文档设计约束
- 壁打ち、锚定与禁止规则 → 继承并为上市公司材料强化
- 源自 EIP 的 HTML 机制（18 模板 / 28 策略 / 组件 / 深度可视化）→ 保留为可选的 HTML 输出模式
