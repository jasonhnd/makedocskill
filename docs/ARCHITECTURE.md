# Architecture Design / アーキテクチャ設計 / 架构设计

> Based on EIP (Explain In Picture) project documentation

[EN](#english) · [日本語](#japanese) · [中文](#chinese)

---

## English {#english}

> Based on EIP (Explain In Picture) project documentation migration. makedocskill is the skill-based successor of EIP — distilling EIP's Web App capabilities into a single Claude Code Skill.

### 1. Positioning and Boundaries

#### 1.1 What is makedocskill

makedocskill is a **Claude Code Skill**, not a Web application, not a CLI tool, not a SaaS service.

| Dimension | EIP (Predecessor) | makedocskill |
|-----------|-------------------|--------------|
| Form | Web App (Next.js) | Claude Code Skill (SKILL.md) |
| Runtime | Browser + Server | Claude Code session (local terminal) |
| User Interaction | Web UI | Natural language conversation |
| Output | Online rendering | Self-contained HTML file (local disk) |
| Dependencies | Node.js, React, Database | Zero dependencies (Claude Code only) |
| Deployment | Server deployment | `cp SKILL.md ~/.claude/skills/` |

#### 1.2 Core Capabilities

Transforms complex information (product architecture, business processes, strategic concepts, research results) into:

- **Single-page scrolling document** (one-pager): Online viewing, print-friendly
- **16:9 slide deck**: Projection display, team presentations, PDF output

#### 1.3 Out of Scope

- No interactive web applications
- No plain Markdown documents
- No PPTX format (there is a dedicated pptx skill)
- No crawler logic (CI extraction via Claude Code's built-in browse/fetch tools)

### 2. Three-Layer Decoupled Architecture

The core architecture of makedocskill is **Brain-Router-Canvas three-layer separation**. This methodology inherited from EIP Engine 1.0 ensures complete decoupling of logic analysis, template selection, and visual rendering.

```
┌─────────────────────────────────────────────────────┐
│                    User Input                        │
│  (Material documents / URL / Verbal / Uploaded files)│
└───────────────────────┬─────────────────────────────┘
                        │
                        ▼
┌─────────────────────────────────────────────────────┐
│               Brain Layer (Logic Analysis)           │
│                                                     │
│  ┌─────────────┐  ┌──────────────┐  ┌────────────┐  │
│  │ Material     │  │ Core Tension │  │ Evidence   │  │
│  │ Understanding│  │ Extraction   │  │ Evaluation │  │
│  │ Step 3       │  │ Step 4       │  │ Step 4     │  │
│  └─────────────┘  └──────────────┘  └────────────┘  │
│                                                     │
│  ┌─────────────┐  ┌──────────────┐                  │
│  │ Causal Chain │  │ Multi-angle  │                  │
│  │ Construction │  │ Review       │                  │
│  │ Step 4       │  │ Step 4       │                  │
│  └─────────────┘  └──────────────┘                  │
└───────────────────────┬─────────────────────────────┘
                        │
                        ▼
┌─────────────────────────────────────────────────────┐
│              Router Layer (Template Routing)          │
│                                                     │
│  ┌──────────────────────────────────────────────┐   │
│  │  Content type ID → Strategy match → Template  │   │
│  │  auto-recommendation                          │   │
│  │  Step 5                                       │   │
│  │                                               │   │
│  │  28 content strategies ──map──→ 18 templates   │   │
│  │  (User can override recommendation)           │   │
│  └──────────────────────────────────────────────┘   │
└───────────────────────┬─────────────────────────────┘
                        │
                        ▼
┌─────────────────────────────────────────────────────┐
│              Canvas Layer (Visual Rendering)          │
│                                                     │
│  ┌────────────┐  ┌───────────┐  ┌────────────────┐  │
│  │ Template   │  │ CI Spec   │  │ Depth          │  │
│  │ Skeleton   │  │ Step 1    │  │ Visualization  │  │
│  │ Step 7     │  │           │  │ Step 7         │  │
│  └────────────┘  └───────────┘  └────────────────┘  │
│                                                     │
│  ┌────────────┐  ┌───────────┐                      │
│  │ Review     │  │ HTML      │                      │
│  │ Validation │  │ Generation│                      │
│  │ Step 6     │  │ Step 7    │                      │
│  └────────────┘  └───────────┘                      │
└─────────────────────────────────────────────────────┘
                        │
                        ▼
                Self-contained HTML file
```

#### 2.1 Brain Layer

**Responsibility**: Understand materials, extract core tensions, build causal chains, evaluate evidence strength.

The Brain layer is the analysis engine. It does not care what template will be used for presentation, only:

- **What is the core claim?** The central argument of the material
- **How strong is the evidence?** Primary data vs secondary inference vs unverified
- **Is the causal chain complete?** Full derivation from cause to effect
- **What blind spots exist?** Missing dimensions, counter-arguments
- **How well does it match the audience?** Whether depth matches audience knowledge level

Brain layer depth is controlled by **S/M/L/XL four levels** (see SIZE_DEPTH_MATRIX.md).

**Corresponding pipeline steps**: Step 3 (Material organization), Step 4 (Sparring/Expert questioning).

#### 2.2 Router Layer

**Responsibility**: Automatically match the optimal visual template based on content type.

The Router layer bridges Brain and Canvas. It receives Brain's analysis results, identifies the content type (one of 28 strategies), then queries the mapping table to recommend the best template (primary + 2 alternatives).

**Routing logic**:

```
Content type identification (Brain analysis results)
    ↓
Strategy matching (28 content strategy table)
    ↓
Template recommendation (Primary + Alt 1 + Alt 2)
    ↓
User confirmation (can override recommendation)
    ↓
Composition table generation (8 fields / Section)
```

**Corresponding pipeline step**: Step 5 (Composition table).

#### 2.3 Canvas Layer

**Responsibility**: Generate final HTML according to template skeleton rules + CI specification.

The Canvas layer is the rendering engine. It strictly follows:

1. **Template skeleton rules**: Each of the 18 templates has Tailwind class-level layout definitions
2. **CI design specification**: Brand colors, fonts, border-radius, shadows from Step 1
3. **Depth visualization rules**: 6 types including causal chain, confidence, comparison delta
4. **Universal design rules**: Grid alignment, glassmorphism, responsive, micro-interactions

**Corresponding pipeline steps**: Step 6 (Review), Step 7 (HTML generation).

### 3. 8-Step Pipeline Overview

The three-layer architecture is executed through an 8-step pipeline. Each step produces an intermediate file, and each step requires user confirmation before proceeding.

```
Step 0  Project name   → output/[name]/
Step 1  CI acquisition → 01_design.md          ← Canvas input
Step 2  Pre-interview  → 02_interview.md        ← Global parameters
Step 3  Materials      → 03_source.md           ← Brain input
Step 4  Sparring       → 04_sparring.md         ← Brain deep analysis
Step 5  Composition    → 05_composition_[lang].md ← Router output
Step 6  Review         → 06_review.md           ← Canvas quality gate
Step 7  HTML generation→ [title]_[lang].html    ← Canvas output
```

See [PIPELINE.md](./PIPELINE.md) for details.

### 4. 18 Template System

makedocskill has 18 built-in visual templates, each with Tailwind class-level skeleton definitions:

| # | Template | One-line Purpose |
|---|----------|-----------------|
| 1 | Dashboard | Bento-box KPI dashboard |
| 2 | Versus | Left-right comparison analysis |
| 3 | Timeline | Timeline narrative |
| 4 | Article | Long-form reading |
| 5 | Steps | Numbered step tutorial |
| 6 | Report | Structured report |
| 7 | Matrix | Multi-dimensional evaluation matrix |
| 8 | Profile | Entity profile / product introduction |
| 9 | Flowchart | Decision flowchart |
| 10 | Scorecard | Rating scorecard |
| 11 | Pitch | Narrative landing page |
| 12 | Infographic | Vertical infographic |
| 13 | Comparison Table | Feature comparison table |
| 14 | FAQ | Collapsible Q&A |
| 15 | Slide | 16:9 slide deck |
| 16 | Iceberg | Surface vs deep |
| 17 | Funnel | Conversion funnel |
| 18 | Bridge | Transformation path |

See [TEMPLATES.md](./TEMPLATES.md) for details.

### 5. 28 Content Strategies

The Router layer supports 28 content strategies covering a wide range from breaking news to real estate:

`breaking-news` / `opinion` / `product` / `ecommerce` / `tutorial` / `tech-doc` / `research` / `finance` / `legal-policy` / `video` / `social-thread` / `general` / `press-release` / `case-study` / `whitepaper` / `data-analysis` / `review` / `interview` / `event` / `job-posting` / `recipe` / `travel` / `health` / `real-estate` / `startup` / `podcast` / `announcement` / `sports`

Each strategy defines analysis focus, expert questioning patterns, and Brain Schema Override. See [CONTENT_STRATEGIES.md](./CONTENT_STRATEGIES.md) for details.

### 6. 4-Level Depth Control

| Level | Analysis Depth | Section Count | Depth Visualization |
|-------|---------------|---------------|-------------------|
| **S** | Core conclusions + action items | 3-5 | Basic |
| **M** | Standard analysis + evidence evaluation | 5-8 | Standard (confidence badges, comparison highlights) |
| **L** | Deep analysis + explanatory framework | 8-12 | Full (causal chains, trend charts, multi-source comparison) |
| **XL** | Complete report + multi-angle review | 12+ | Full + interactive |

See [SIZE_DEPTH_MATRIX.md](./SIZE_DEPTH_MATRIX.md) for details.

### 7. Runtime Environment

#### 7.1 Skill Execution Model

makedocskill runs as a Claude Code Skill:

1. User triggers in a Claude Code session (natural language or `/make-doc-skill`)
2. Claude Code loads SKILL.md as context instructions
3. The Skill guides users through the 8-step pipeline via conversation
4. Intermediate artifacts from each step are written to local disk `output/[name]/`
5. The final HTML file is written to the same directory

#### 7.2 File System Layout

```
output/[project_name]/
├── README.md                    ← Project summary
├── 00_assets/                   ← Uploaded material files
├── 01_design.md                 ← CI design specification
├── 02_interview.md              ← Pre-interview 8 questions answers
├── 03_source.md                 ← Structured material organization
├── 04_sparring.md               ← Sparring record
├── 05_composition_[lang].md     ← Composition table
├── 06_review.md                 ← Review report
├── [title]_[lang].html          ← Final output
└── _history/                    ← Iteration history versions
    ├── v1/
    └── v2/
```

#### 7.3 External Dependencies

makedocskill itself has zero dependencies. The generated HTML files reference:

| Resource | Source | Purpose |
|----------|--------|---------|
| Tailwind CSS | CDN | Style framework |
| Google Fonts | CDN | Fonts |
| Lucide Icons | inline SVG | Icons |
| Images | Base64 embedded | No external image dependencies |

HTML files can be opened directly in any modern browser without a local server.

### 8. Relationship with EIP

makedocskill is the **skill-based successor** of EIP (Explain In Picture):

| Inherited | Changed |
|-----------|---------|
| Brain-Router-Canvas three-layer architecture | From Web App code to Prompt instructions |
| 18 visual templates | Skeleton rules from component code to Tailwind class descriptions |
| 28 content strategies | Mapping table directly embedded in SKILL.md |
| 8-step pipeline | From UI flow to conversation flow |
| CI extraction system | From built-in crawler to Claude Code tool calls |
| Depth visualization rules | Fully inherited |
| Universal design rules | Fully inherited |
| 3-layer 15-item review checklist | Fully inherited |

Core methodology unchanged, medium changed from Web App to Skill.

---

## 日本語 {#japanese}

> EIP (Explain In Picture) プロジェクトドキュメントからの移行。makedocskill は EIP の Skill 化後継者であり、EIP の Web App 能力を一つの Claude Code Skill に凝縮したものです。

### 1. 位置づけと境界

#### 1.1 makedocskill とは

makedocskill は **Claude Code Skill** であり、Web アプリケーションでもなく、CLI ツールでもなく、SaaS サービスでもありません。

| 次元 | EIP（前身） | makedocskill |
|------|-----------|-------------|
| 形態 | Web App（Next.js） | Claude Code Skill（SKILL.md） |
| 実行環境 | ブラウザ + サーバー | Claude Code セッション（ローカルターミナル） |
| ユーザー操作 | Web UI | 自然言語対話 |
| 出力 | オンラインレンダリング | 自己完結型 HTML ファイル（ローカルディスク） |
| 依存関係 | Node.js, React, データベース | ゼロ依存（Claude Code のみ） |
| デプロイ | サーバーデプロイ | `cp SKILL.md ~/.claude/skills/` |

#### 1.2 コア機能

複雑な情報（プロダクトアーキテクチャ、ビジネスプロセス、戦略構想、研究成果）を以下に変換します：

- **シングルページスクロール文書**（one-pager）：オンライン閲覧、印刷対応
- **16:9 スライドデッキ**：プロジェクション表示、チーム報告、PDF 出力

#### 1.3 対象外

- インタラクティブ Web アプリケーションは作らない
- 純粋な Markdown ドキュメントは作らない
- PPTX 形式は作らない（専用の pptx skill あり）
- クローラーロジックは含まない（CI 抽出は Claude Code 内蔵の browse/fetch ツールで実行）

### 2. 三層分離アーキテクチャ

makedocskill のコアアーキテクチャは **Brain-Router-Canvas 三層分離** です。EIP Engine 1.0 から継承されたこの方法論により、論理分析、テンプレート選択、ビジュアルレンダリングの三つの関心事が完全に分離されます。

```
┌─────────────────────────────────────────────────────┐
│                    ユーザー入力                        │
│  （素材文書 / URL / 口述 / アップロードファイル）          │
└───────────────────────┬─────────────────────────────┘
                        │
                        ▼
┌─────────────────────────────────────────────────────┐
│                 Brain 層（論理分析）                    │
│                                                     │
│  ┌─────────────┐  ┌──────────────┐  ┌────────────┐  │
│  │ 素材理解     │  │ 核心テンション│  │ 証拠評価    │  │
│  │ Step 3       │  │ 抽出 Step 4  │  │ Step 4     │  │
│  └─────────────┘  └──────────────┘  └────────────┘  │
│                                                     │
│  ┌─────────────┐  ┌──────────────┐                  │
│  │ 因果チェーン │  │ 多角度検討    │                  │
│  │ 構築 Step 4  │  │ Step 4       │                  │
│  └─────────────┘  └──────────────┘                  │
└───────────────────────┬─────────────────────────────┘
                        │
                        ▼
┌─────────────────────────────────────────────────────┐
│                Router 層（テンプレートルーティング）       │
│                                                     │
│  ┌──────────────────────────────────────────────┐   │
│  │  コンテンツタイプ識別 → 戦略マッチング →          │   │
│  │  テンプレート自動推薦                            │   │
│  │  Step 5                                       │   │
│  │                                               │   │
│  │  28種コンテンツ戦略 ──マッピング──→ 18種テンプレート │   │
│  │  （ユーザーは推薦結果を上書き可能）                 │   │
│  └──────────────────────────────────────────────┘   │
└───────────────────────┬─────────────────────────────┘
                        │
                        ▼
┌─────────────────────────────────────────────────────┐
│                Canvas 層（ビジュアルレンダリング）        │
│                                                     │
│  ┌────────────┐  ┌───────────┐  ┌────────────────┐  │
│  │ テンプレート │  │ CI 仕様   │  │ 深度可視化     │  │
│  │ 骨格 Step 7 │  │ Step 1    │  │ Step 7        │  │
│  └────────────┘  └───────────┘  └────────────────┘  │
│                                                     │
│  ┌────────────┐  ┌───────────┐                      │
│  │ 審査検証    │  │ HTML 生成  │                      │
│  │ Step 6      │  │ Step 7     │                      │
│  └────────────┘  └───────────┘                      │
└─────────────────────────────────────────────────────┘
                        │
                        ▼
                   自己完結型 HTML ファイル
```

#### 2.1 Brain 層

**責務**：素材理解、核心テンション抽出、因果チェーン構築、証拠強度評価。

Brain 層は分析エンジンです。最終的にどのテンプレートで表示するかは関係なく、以下のみに注目します：

- **核心主張は何か？** 素材の中心的論点
- **証拠の強度は？** 一次データ vs 二次推測 vs 未検証
- **因果チェーンは完全か？** 原因から結果までの完全な導出
- **どのような盲点があるか？** 欠落した次元、反論
- **オーディエンスとの適合度は？** 深度とオーディエンスの知識レベルが適合しているか

Brain 層の深度は **S/M/L/XL の4段階** で制御されます（SIZE_DEPTH_MATRIX.md 参照）。

**対応パイプラインステップ**：Step 3（素材整理）、Step 4（壁打ち/エキスパート質問）。

#### 2.2 Router 層

**責務**：コンテンツタイプに基づき最適なビジュアルテンプレートを自動マッチング。

Router 層は Brain と Canvas の橋渡し役です。Brain 層の分析結果を受け取り、コンテンツタイプ（28種の戦略のいずれか）を識別し、マッピングテーブルを参照して最適なテンプレート（第一推薦 + 代替2つ）を推薦します。

**ルーティングロジック**：

```
コンテンツタイプ識別（Brain 分析結果）
    ↓
戦略マッチング（28種コンテンツ戦略テーブル）
    ↓
テンプレート推薦（第一推薦 + 代替1 + 代替2）
    ↓
ユーザー確認（推薦を上書き可能）
    ↓
構成表生成（8フィールド / Section）
```

**対応パイプラインステップ**：Step 5（構成表）。

#### 2.3 Canvas 層

**責務**：テンプレート骨格ルール + CI 仕様に従い最終 HTML を生成。

Canvas 層はレンダリングエンジンです。以下を厳格に遵守します：

1. **テンプレート骨格ルール**：18種のテンプレートそれぞれに Tailwind class レベルのレイアウト定義
2. **CI デザイン仕様**：Step 1 からのブランドカラー、フォント、角丸、シャドウ
3. **深度可視化ルール**：因果チェーン、信頼度、比較増分など6種の可視化
4. **汎用デザインルール**：Grid 整列、グラスモーフィズム、レスポンシブ、マイクロインタラクション

**対応パイプラインステップ**：Step 6（審査）、Step 7（HTML 生成）。

### 3. 8ステップパイプライン概要

三層アーキテクチャは8ステップパイプラインを通じて実行されます。各ステップは中間ファイルを生成し、次のステップに進む前にユーザー確認が必要です。

```
Step 0  プロジェクト名  → output/[name]/
Step 1  CI 取得        → 01_design.md          ← Canvas 入力
Step 2  事前8問        → 02_interview.md        ← グローバルパラメータ
Step 3  素材整理       → 03_source.md           ← Brain 入力
Step 4  壁打ち         → 04_sparring.md         ← Brain 深度分析
Step 5  構成表         → 05_composition_[lang].md ← Router 出力
Step 6  審査           → 06_review.md           ← Canvas 品質ゲート
Step 7  HTML 生成      → [title]_[lang].html    ← Canvas 出力
```

詳細は [PIPELINE.md](./PIPELINE.md) を参照してください。

### 4. 18種テンプレートシステム

makedocskill には18種のビジュアルテンプレートが内蔵されており、それぞれ Tailwind class レベルの骨格定義があります：

| # | テンプレート名 | 一言用途 |
|---|-------------|---------|
| 1 | Dashboard | Bento-box KPI ダッシュボード |
| 2 | Versus | 左右対比分析 |
| 3 | Timeline | タイムライン物語 |
| 4 | Article | 長文読み物 |
| 5 | Steps | 番号付きステップチュートリアル |
| 6 | Report | 構造化レポート |
| 7 | Matrix | 多次元評価マトリクス |
| 8 | Profile | エンティティプロファイル/製品紹介 |
| 9 | Flowchart | 意思決定フローチャート |
| 10 | Scorecard | スコアカード |
| 11 | Pitch | ナラティブランディングページ |
| 12 | Infographic | 縦型インフォグラフィック |
| 13 | Comparison Table | 機能比較表 |
| 14 | FAQ | 折りたたみ式 Q&A |
| 15 | Slide | 16:9 スライドデッキ |
| 16 | Iceberg | 表面 vs 深層 |
| 17 | Funnel | コンバージョンファネル |
| 18 | Bridge | 変革パス |

詳細は [TEMPLATES.md](./TEMPLATES.md) を参照してください。

### 5. 28種コンテンツ戦略

Router 層は速報ニュースから不動産まで幅広いシーンをカバーする28種のコンテンツ戦略をサポートしています：

`breaking-news` / `opinion` / `product` / `ecommerce` / `tutorial` / `tech-doc` / `research` / `finance` / `legal-policy` / `video` / `social-thread` / `general` / `press-release` / `case-study` / `whitepaper` / `data-analysis` / `review` / `interview` / `event` / `job-posting` / `recipe` / `travel` / `health` / `real-estate` / `startup` / `podcast` / `announcement` / `sports`

各戦略は分析の焦点、エキスパート質問パターン、Brain Schema Override を定義しています。詳細は [CONTENT_STRATEGIES.md](./CONTENT_STRATEGIES.md) を参照してください。

### 6. 4段階深度制御

| レベル | 分析深度 | Section 数 | 深度可視化 |
|--------|---------|-----------|-----------|
| **S** | 核心結論 + アクション項目 | 3-5 | 基礎 |
| **M** | 標準分析 + 証拠評価 | 5-8 | 標準（信頼度バッジ、比較ハイライト） |
| **L** | 深度分析 + 説明フレームワーク | 8-12 | 完全（因果チェーン、トレンドチャート、多ソース比較） |
| **XL** | 完全レポート + 多角度レビュー | 12+ | 完全 + インタラクティブ |

詳細は [SIZE_DEPTH_MATRIX.md](./SIZE_DEPTH_MATRIX.md) を参照してください。

### 7. 実行環境

#### 7.1 Skill 実行モデル

makedocskill は Claude Code Skill として動作します：

1. ユーザーが Claude Code セッション内でトリガー（自然言語または `/make-doc-skill`）
2. Claude Code が SKILL.md をコンテキスト指示として読み込み
3. Skill が対話を通じてユーザーを8ステップパイプラインに導く
4. 各ステップの中間生成物はローカルディスク `output/[name]/` に書き込み
5. 最終 HTML ファイルは同じディレクトリに書き込み

#### 7.2 ファイルシステムレイアウト

```
output/[project_name]/
├── README.md                    ← プロジェクト概要
├── 00_assets/                   ← アップロード素材ファイル
├── 01_design.md                 ← CI デザイン仕様
├── 02_interview.md              ← 事前8問回答
├── 03_source.md                 ← 素材構造化整理
├── 04_sparring.md               ← 壁打ち記録
├── 05_composition_[lang].md     ← 構成表
├── 06_review.md                 ← 審査レポート
├── [title]_[lang].html          ← 最終出力
└── _history/                    ← イテレーション履歴バージョン
    ├── v1/
    └── v2/
```

#### 7.3 外部依存

makedocskill 自体はゼロ依存です。生成された HTML ファイルは以下を参照します：

| リソース | ソース | 用途 |
|---------|--------|------|
| Tailwind CSS | CDN | スタイルフレームワーク |
| Google Fonts | CDN | フォント |
| Lucide Icons | inline SVG | アイコン |
| 画像 | Base64 埋め込み | 外部画像依存なし |

HTML ファイルはローカルサーバーなしで任意のモダンブラウザで直接開けます。

### 8. EIP との関係

makedocskill は EIP (Explain In Picture) の **Skill 化後継者** です：

| 継承 | 変化 |
|------|------|
| Brain-Router-Canvas 三層アーキテクチャ | Web App コードから Prompt 指示へ |
| 18種ビジュアルテンプレート | 骨格ルールがコンポーネントコードから Tailwind class 記述へ |
| 28種コンテンツ戦略 | マッピングテーブルを SKILL.md に直接埋め込み |
| 8ステップパイプライン | UI フローから対話フローへ |
| CI 抽出システム | 内蔵クローラーから Claude Code ツール呼び出しへ |
| 深度可視化ルール | 完全継承 |
| 汎用デザインルール | 完全継承 |
| 3層15項目審査チェックリスト | 完全継承 |

コア方法論は不変、媒体が Web App から Skill に変わりました。

---

## 中文 {#chinese}

> 基于 EIP (Explain In Picture) 项目文档迁移。makedocskill 是 EIP 的 skill 化继承者——将 EIP 的 Web App 能力提炼为一个 Claude Code skill。

### 1. 定位与边界

#### 1.1 makedocskill 是什么

makedocskill 是一个 **Claude Code Skill**，不是 Web 应用、不是 CLI 工具、不是 SaaS 服务。

| 维度 | EIP (前身) | makedocskill |
|------|-----------|-------------|
| 形态 | Web App（Next.js） | Claude Code Skill（SKILL.md） |
| 执行环境 | 浏览器 + 服务端 | Claude Code 会话（本地终端） |
| 用户交互 | Web UI | 自然语言对话 |
| 输出 | 在线渲染 | 自包含 HTML 文件（本地磁盘） |
| 依赖 | Node.js, React, 数据库 | 零依赖（仅 Claude Code） |
| 部署 | 服务器部署 | `cp SKILL.md ~/.claude/skills/` |

#### 1.2 核心能力

将复杂信息（产品架构、业务流程、战略构想、研究结果）转化为：

- **单页滚动文档**（one-pager）：在线阅览、打印友好
- **16:9 幻灯片**（slide deck）：投影展示、团队汇报、PDF 输出

#### 1.3 不做的事

- 不做交互式 Web 应用
- 不做纯 Markdown 文档
- 不做 PPTX 格式（有专门的 pptx skill）
- 不含爬虫逻辑（CI 提取通过 Claude Code 内置的 browse/fetch 工具）

### 2. 三层解耦架构

makedocskill 的核心架构是 **Brain-Router-Canvas 三层分离**。这是从 EIP Engine 1.0 继承的方法论，确保逻辑分析、模板选择、视觉渲染三个关注点完全解耦。

```
┌─────────────────────────────────────────────────────┐
│                    用户输入                           │
│  （素材文档 / URL / 口述 / 上传文件）                   │
└───────────────────────┬─────────────────────────────┘
                        │
                        ▼
┌─────────────────────────────────────────────────────┐
│                 Brain 层（逻辑分析）                    │
│                                                     │
│  ┌─────────────┐  ┌──────────────┐  ┌────────────┐  │
│  │ 素材理解     │  │ 核心张力抽出  │  │ 证据评价    │  │
│  │ Step 3       │  │ Step 4       │  │ Step 4     │  │
│  └─────────────┘  └──────────────┘  └────────────┘  │
│                                                     │
│  ┌─────────────┐  ┌──────────────┐                  │
│  │ 因果链构建   │  │ 多视角审视    │                  │
│  │ Step 4       │  │ Step 4       │                  │
│  └─────────────┘  └──────────────┘                  │
└───────────────────────┬─────────────────────────────┘
                        │
                        ▼
┌─────────────────────────────────────────────────────┐
│                Router 层（模板路由）                    │
│                                                     │
│  ┌──────────────────────────────────────────────┐   │
│  │  内容类型识别 → 策略匹配 → 模板自动推荐         │   │
│  │  Step 5                                       │   │
│  │                                               │   │
│  │  28 种内容策略 ──映射──→ 18 种视觉模板          │   │
│  │  （用户可覆盖推荐结果）                          │   │
│  └──────────────────────────────────────────────┘   │
└───────────────────────┬─────────────────────────────┘
                        │
                        ▼
┌─────────────────────────────────────────────────────┐
│                Canvas 层（视觉渲染）                    │
│                                                     │
│  ┌────────────┐  ┌───────────┐  ┌────────────────┐  │
│  │ 模板骨格    │  │ CI 规范    │  │ 深度可视化     │  │
│  │ Step 7      │  │ Step 1     │  │ Step 7        │  │
│  └────────────┘  └───────────┘  └────────────────┘  │
│                                                     │
│  ┌────────────┐  ┌───────────┐                      │
│  │ 审查验证    │  │ HTML 生成  │                      │
│  │ Step 6      │  │ Step 7     │                      │
│  └────────────┘  └───────────┘                      │
└─────────────────────────────────────────────────────┘
                        │
                        ▼
                   自包含 HTML 文件
```

#### 2.1 Brain 层

**职责**：理解素材、提炼核心张力、构建因果链、评价证据强度。

Brain 层是分析引擎。它不关心最终用什么模板呈现，只关心：

- **核心主张是什么？** 素材的中心论点
- **证据强度如何？** 一次数据 vs 二次推测 vs 未验证
- **因果链是否完整？** 从原因到结果的完整推导
- **存在哪些盲点？** 缺失维度、反面论据
- **受众匹配度如何？** 深度与受众知识水平是否适配

Brain 层的深度由 **S/M/L/XL 四级控制**（详见 SIZE_DEPTH_MATRIX.md）。

**对应管线步骤**：Step 3（素材整理）、Step 4（壁打ち/专家追问）。

#### 2.2 Router 层

**职责**：根据内容类型自动匹配最优视觉模板。

Router 层是 Brain 和 Canvas 之间的桥梁。它接收 Brain 层的分析结果，识别内容类型（28 种策略之一），然后查询映射表推荐最佳模板（首选 + 2 个备选）。

**路由逻辑**：

```
内容类型识别（Brain 分析结果）
    ↓
策略匹配（28 种内容策略表）
    ↓
模板推荐（首选 + 备选 1 + 备选 2）
    ↓
用户确认（可覆盖推荐）
    ↓
构成表生成（8 字段 / Section）
```

**对应管线步骤**：Step 5（构成表）。

#### 2.3 Canvas 层

**职责**：按模板骨格规则 + CI 规范生成最终 HTML。

Canvas 层是渲染引擎。它严格遵循：

1. **模板骨格规则**：18 种模板各有 Tailwind class 级别的布局定义
2. **CI 设计规范**：来自 Step 1 的品牌色、字体、圆角、阴影
3. **深度可视化规则**：因果链、置信度、对比增量等 6 种可视化
4. **通用设计规则**：Grid 整列、玻璃拟态、响应式、微交互

**对应管线步骤**：Step 6（审查）、Step 7（HTML 生成）。

### 3. 8 步管线概览

三层架构通过 8 步管线落地执行。每一步产出一个中间文件，每一步需要用户确认后才进入下一步。

```
Step 0  项目名        → output/[name]/
Step 1  CI 获取       → 01_design.md          ← Canvas 输入
Step 2  前置 8 问     → 02_interview.md        ← 全局参数
Step 3  素材整理      → 03_source.md           ← Brain 输入
Step 4  壁打ち        → 04_sparring.md         ← Brain 深度分析
Step 5  构成表        → 05_composition_[lang].md ← Router 输出
Step 6  审查          → 06_review.md           ← Canvas 质量门
Step 7  HTML 生成     → [title]_[lang].html    ← Canvas 输出
```

详细说明请参考 [PIPELINE.md](./PIPELINE.md)。

### 4. 18 种模板系统

makedocskill 内置 18 种视觉模板，每种都有 Tailwind class 级别的骨格定义：

| # | 模板名 | 一句话用途 |
|---|--------|-----------|
| 1 | Dashboard | Bento-box KPI 仪表盘 |
| 2 | Versus | 左右对比分析 |
| 3 | Timeline | 时间轴叙事 |
| 4 | Article | 长文阅读 |
| 5 | Steps | 编号步骤教程 |
| 6 | Report | 结构化报告 |
| 7 | Matrix | 多维评价矩阵 |
| 8 | Profile | 实体画像/产品介绍 |
| 9 | Flowchart | 决策流程图 |
| 10 | Scorecard | 评分卡 |
| 11 | Pitch | 叙事型着陆页 |
| 12 | Infographic | 纵向信息图 |
| 13 | Comparison Table | 特性比较表 |
| 14 | FAQ | 折叠式 Q&A |
| 15 | Slide | 16:9 幻灯片 |
| 16 | Iceberg | 表面 vs 深层 |
| 17 | Funnel | 漏斗转化 |
| 18 | Bridge | 转化路径 |

详细说明请参考 [TEMPLATES.md](./TEMPLATES.md)。

### 5. 28 种内容策略

Router 层支持 28 种内容策略，覆盖从突发新闻到房地产的广泛场景：

`breaking-news` / `opinion` / `product` / `ecommerce` / `tutorial` / `tech-doc` / `research` / `finance` / `legal-policy` / `video` / `social-thread` / `general` / `press-release` / `case-study` / `whitepaper` / `data-analysis` / `review` / `interview` / `event` / `job-posting` / `recipe` / `travel` / `health` / `real-estate` / `startup` / `podcast` / `announcement` / `sports`

每种策略定义了分析侧重、专家追问模式和 Brain Schema Override。详细说明请参考 [CONTENT_STRATEGIES.md](./CONTENT_STRATEGIES.md)。

### 6. 4 级深度控制

| 级别 | 分析深度 | Section 数 | 深度可视化 |
|------|---------|-----------|-----------|
| **S** | 核心结论 + 行动项 | 3-5 | 基础 |
| **M** | 标准分析 + 证据评价 | 5-8 | 标准（置信度标记、对比高亮） |
| **L** | 深度分析 + 解释框架 | 8-12 | 完全（因果链、趋势图、多源对比） |
| **XL** | 完全报告 + 多视角审视 | 12+ | 完全 + 交互式 |

详细说明请参考 [SIZE_DEPTH_MATRIX.md](./SIZE_DEPTH_MATRIX.md)。

### 7. 执行环境

#### 7.1 Skill 执行模型

makedocskill 作为 Claude Code Skill 运行：

1. 用户在 Claude Code 会话中触发（自然语言或 `/make-doc-skill`）
2. Claude Code 加载 SKILL.md 作为上下文指令
3. Skill 通过对话引导用户完成 8 步管线
4. 每一步的中间产物写入本地磁盘 `output/[name]/`
5. 最终 HTML 文件写入同一目录

#### 7.2 文件系统布局

```
output/[project_name]/
├── README.md                    ← 项目概要
├── 00_assets/                   ← 上传的素材文件
├── 01_design.md                 ← CI 设计规范
├── 02_interview.md              ← 前置 8 问回答
├── 03_source.md                 ← 素材结构化整理
├── 04_sparring.md               ← 壁打ち记录
├── 05_composition_[lang].md     ← 构成表
├── 06_review.md                 ← 审查报告
├── [title]_[lang].html          ← 最终输出
└── _history/                    ← 迭代历史版本
    ├── v1/
    └── v2/
```

#### 7.3 外部依赖

makedocskill 本身零依赖。生成的 HTML 文件引用：

| 资源 | 来源 | 用途 |
|------|------|------|
| Tailwind CSS | CDN | 样式框架 |
| Google Fonts | CDN | 字体 |
| Lucide Icons | inline SVG | 图标 |
| 图片 | Base64 内嵌 | 无外部图片依赖 |

HTML 文件在任何现代浏览器中可直接打开，无需本地服务器。

### 8. 与 EIP 的关系

makedocskill 是 EIP (Explain In Picture) 的 **skill 化继承者**：

| 继承 | 变化 |
|------|------|
| Brain-Router-Canvas 三层架构 | 从 Web App 代码变为 Prompt 指令 |
| 18 种视觉模板 | 骨格规则从组件代码变为 Tailwind class 描述 |
| 28 种内容策略 | 映射表直接嵌入 SKILL.md |
| 8 步管线 | 从 UI 流程变为对话流程 |
| CI 提取系统 | 从内置爬虫变为 Claude Code 工具调用 |
| 深度可视化规则 | 完整继承 |
| 通用设计规则 | 完整继承 |
| 审查 3 层 15 项清单 | 完整继承 |

核心方法论不变，载体从 Web App 变为 Skill。
