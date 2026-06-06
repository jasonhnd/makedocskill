# 28 Content Strategy Reference / 28種コンテンツ戦略参考 / 28 种内容策略参考

> **[Partly shared / HTML output mode]** make-doc-skill's primary path is company document generation (see `../SKILL.md`). The expert-questioning chains here are reused by Brain/sparring across all output types; the template-mapping and HTML-specific guidance applies only to the optional HTML output mode.

> Based on EIP (Explain In Picture) project documentation

[EN](#english) · [日本語](#japanese) · [中文](#chinese)

---

## English {#english}

> Based on EIP (Explain In Picture) project documentation migration. makedocskill's Router layer uses content strategies to automatically match materials to templates.

### Overview

Content strategy is the core concept of the Router layer. Each strategy defines:

1. **Analysis focus**: What the Brain layer should focus on
2. **Expert questioning pattern**: Domain expert perspectives injected during sparring
3. **Brain Schema Override**: Special rules overriding the default analysis framework
4. **Recommended templates**: Primary + 2 alternatives

### Strategy Overview Table

| # | Strategy ID | Name | Analysis Focus |
|---|-------------|------|---------------|
| 1 | `breaking-news` | Breaking News | Fact-checking, information sources, timeline, impact scope |
| 2 | `opinion` | Opinion Commentary | Argument structure, stance, counter-arguments, persuasiveness |
| 3 | `product` | Product Introduction | Core value proposition, differentiation, user value, tech specs |
| 4 | `ecommerce` | E-commerce | Price comparison, value-for-money, user reviews, purchase decision |
| 5 | `tutorial` | Tutorial | Step completeness, prerequisites, common errors, learning curve |
| 6 | `tech-doc` | Technical Document | System architecture, API interfaces, dependencies, scalability |
| 7 | `research` | Research Report | Methodology, data quality, statistical significance, reproducibility |
| 8 | `finance` | Financial Analysis | Revenue structure, cash flow, valuation, risk factors |
| 9 | `legal-policy` | Legal Policy | Clause interpretation, compliance requirements, risk assessment, impact analysis |
| 10 | `video` | Video Content | Timeline, key segments, core arguments, emotional arc |
| 11 | `social-thread` | Social Media Thread | Narrative structure, audience reaction, viral elements, controversy points |
| 12 | `general` | General | Core claims, evidence chain, logical structure, audience fit |
| 13 | `press-release` | Press Release | 5W1H, citation sources, data support, media angle |
| 14 | `case-study` | Case Study | Background-problem-solution-result, ROI, replicability |
| 15 | `whitepaper` | White Paper | Problem definition, technical solution, competitor comparison, implementation path |
| 16 | `data-analysis` | Data Analysis | Data source quality, statistical methods, outliers, trends, correlations |
| 17 | `review` | Review | Scoring dimensions, pros/cons, use cases, competitor comparison |
| 18 | `interview` | Interview | Core viewpoint extraction, context, stance, controversy points |
| 19 | `event` | Event | Timeline, participants, agenda, key outcomes |
| 20 | `job-posting` | Job Posting | Job requirements, skill matching, company culture, salary competitiveness |
| 21 | `recipe` | Recipe | Ingredient ratios, step sequence, key techniques, alternatives |
| 22 | `travel` | Travel | Route planning, budget, time allocation, experience highlights |
| 23 | `health` | Health | Symptom-cause-solution, evidence level, risk alerts, professional advice |
| 24 | `real-estate` | Real Estate | Price trends, location analysis, ROI, risk factors |
| 25 | `startup` | Startup | Problem-solution-market-team-finance, competitive moat |
| 26 | `podcast` | Podcast | Guest viewpoints, discussion thread, controversy points, key quotes |
| 27 | `announcement` | Announcement | Core information, impact scope, timeline, next actions |
| 28 | `sports` | Sports | Data statistics, matchup analysis, performance trends, key moments |

### Expert Questioning Patterns Explained

During sparring (Step 4), switch expert questioning mode based on content strategy. This is not a generic "you are an analyst" but injects domain-specific expert questioning chains.

#### general (General)

**Expert identity**: General analyst, skilled in logical structure and critical thinking.

**Three-question probe**:

1. **What is the core tension?** The most fundamental contradiction or unresolved issue in the material. Not a surface "challenge" but a deep structural tension.
2. **Is the multi-layer causation complete?** From root cause to surface, is every causal layer supported by evidence? Are there reasoning jumps?
3. **Does it pass the So What test?** If the reader says "So what?" after reading, the core claim isn't sharp enough. What is the strongest counter-argument?

**Brain Schema Override**:
- Must identify core tension (not simple summary)
- Every claim must have at least one counter-argument
- MECE check: Are all Section contents mutually exclusive and collectively exhaustive

#### finance (Financial Analysis)

**Expert identity**: Investment banking analyst / buy-side researcher, skilled in financial modeling and valuation.

**Three-question probe**:

1. **Is revenue growth organic or M&A-driven? How large is the FCF vs NI divergence?** Revenue growth quality matters more than speed. Long-term divergence between free cash flow and net income is a danger signal.
2. **What is the historical credibility of management guidance?** Is there a systematic pattern of over-optimism or over-conservatism? Guidance vs actual comparison over the past 4-8 quarters.
3. **What growth assumptions does the current valuation imply? If the core assumption fails, where is the downside?** How much optimism is already priced in? Reverse-engineer the implied growth rate.

**Brain Schema Override**:
- All financial figures must cite source and date
- Growth rates must distinguish organic vs inorganic
- Valuation must provide cross-validation from at least two methods
- Forecasts must note uncertainty intervals
- Cash flow takes priority over profit metrics

#### tech-doc (Technical Document)

**Expert identity**: Senior system architect, skilled in distributed system design and technical review.

**Three-question probe**:

1. **What is the core abstraction? What is the failure mode at 10x scale?** What is the core design decision? When traffic/data/users grow 10x, which component breaks first?
2. **What is the lock-in risk? What is the complete TCO picture?** How high is the migration cost of the technology choice? Beyond direct costs, are operations, training, and hiring hidden costs included?
3. **What is the blast radius of failure? What is the recovery time?** How wide is the impact of a single point of failure? Are there isolation mechanisms? Are RTO/RPO clear?

**Brain Schema Override**:
- System components must note dependencies
- Performance metrics must have benchmark data
- Architecture decisions must document trade-offs
- Must identify single points of failure
- Security considerations cannot be omitted

#### breaking-news (Breaking News)

**Expert identity**: Investigative journalist / intelligence analyst, skilled in fact-checking and information verification.

**Three-question probe**:

1. **What is the primary evidence? What is speculation?** Which information comes from first-hand sources (official statements, eyewitnesses, raw data)? Which is media retelling, anonymous sources, or analyst speculation?
2. **How large is the information gap? Probability of reversal within 72 hours?** What is currently unknown? Based on known information, what is the probability the story is overturned in the short term? What is the historical reversal rate for similar events?
3. **Who benefits? What is the information manipulation motive of stakeholders?** Who benefits from this narrative? Is the timing of information release suspicious? Is there a possibility of information warfare?

**Brain Schema Override**:
- Each piece of information must note source type (primary/secondary/unverified)
- Timeline must be accurate to the hour
- Must note information gap areas
- Definitive language must not be used for unverified information
- Must identify stakeholders and their motives

#### opinion (Opinion Commentary)

**Expert identity**: Academic debate coach / public intellectual, skilled in argument analysis and rhetorical criticism.

**Three-question probe**:

1. **Is the argument structure valid? Are there logical fallacies?** Is the derivation from premise to conclusion rigorous? Are there straw man, slippery slope, appeal to authority, or other common fallacies?
2. **What is the strongest counter-argument? Did the author anticipate and respond to it?** If the smartest opponent wrote a rebuttal, what would be the core attack point?
3. **What are the fundamental assumptions of the stance? What happens if the assumptions are wrong?** What unproven assumptions has the author tacitly accepted?

#### product (Product Introduction)

**Expert identity**: Product manager / industry analyst, skilled in value proposition analysis and competitive research.

**Three-question probe**:

1. **What is the core user pain point? Is this product solving a painkiller problem or a vitamin problem?**
2. **How deep is the differentiation moat? How long would it take competitors to copy?**
3. **What are the usage frequency and stickiness? What are the main reasons for user churn?**

#### research (Research Report)

**Expert identity**: Academic reviewer / research methodology expert.

**Three-question probe**:

1. **Is the methodology sound? What about sample size and selection bias?**
2. **Are results reproducible? What are the p-values and confidence intervals of key findings?**
3. **Are research limitations fully disclosed? Do conclusions exceed what the data supports?**

#### startup (Startup)

**Expert identity**: Venture capitalist / serial entrepreneur.

**Three-question probe**:

1. **How big is the market? Creating a new market or capturing an existing one? Is the TAM/SAM/SOM logic consistent?**
2. **Why now? Why hasn't anyone succeeded before? What is the biggest risk in the next 6 months?**
3. **What unfair advantage does the team have? If the founder leaves, can the company survive?**

#### case-study (Case Study)

**Expert identity**: Management consultant, skilled in case analysis and best practice extraction.

**Three-question probe**:

1. **How unique are the background conditions? Is this success replicable in other environments?**
2. **Is the success attribution correct? Are there omitted variables or survivorship bias?**
3. **Are quantitative effects (ROI, KPI changes) supported by causal inference, or merely correlation?**

#### data-analysis (Data Analysis)

**Expert identity**: Data scientist / statistician.

**Three-question probe**:

1. **What is the data source quality and bias? Is there selection bias, measurement error, or missing data?**
2. **Is correlation being misread as causation? Have confounding factors been controlled?**
3. **Is outlier handling reasonable? Are trend prediction assumptions transparent?**

#### review (Review)

**Expert identity**: Professional reviewer / consumer rights advisor.

**Three-question probe**:

1. **Are review dimensions comprehensive and weights reasonable? Are important use cases missing?**
2. **Are review conditions close to real usage? How large is the gap between lab tests and daily use?**
3. **Is there a conflict of interest? Is there a commercial relationship between the reviewer and the reviewed?**

#### ecommerce (E-commerce)

**Expert identity**: E-commerce operations expert / consumer researcher.

**Three-question probe**:

1. **What patterns do real user reviews show? What dimensions do negative reviews concentrate on?**
2. **What is the complete value-for-money calculation? Are hidden costs (accessories, maintenance, upgrades) included?**
3. **What do return rates and after-sales data tell us?**

#### legal-policy (Legal Policy)

**Expert identity**: Legal counsel / compliance expert.

**Three-question probe**:

1. **Which clauses have a gap between actual enforcement and literal meaning? Where are the gray areas?**
2. **What is the impact on different stakeholders? Who benefits, who loses?**
3. **What are the actual consequences of violations? Enforcement priorities and historical cases?**

#### tutorial (Tutorial)

**Expert identity**: Technical educator / curriculum designer.

**Three-question probe**:

1. **Are prerequisite knowledge assumptions reasonable? Does the target audience actually possess these prerequisites?**
2. **Are there cognitive leaps between steps? Where is a beginner most likely to get stuck?**
3. **Can they independently apply what they learned? Or did they merely follow along once?**

#### whitepaper (White Paper)

**Expert identity**: Industry expert / technical review committee member.

**Three-question probe**:

1. **Is the problem definition precise? Is it solving a real and important problem?**
2. **Are the technical solution trade-offs transparent? Is the comparison with alternatives fair?**
3. **Is the implementation path realistic? Are obstacles from concept to implementation being underestimated?**

#### interview (Interview)

**Expert identity**: Senior journalist / talk show host.

**Three-question probe**:

1. **What are the interviewee's core viewpoints? Are they consistent with their public stance?**
2. **Which questions were evaded? What do silences or vague answers suggest?**
3. **Do key quotes from the interview have context? Could they mislead if taken out of context?**

#### event (Event)

**Expert identity**: Event planner / industry observer.

**Three-question probe**:

1. **What is the core objective of the event? Did participants' gains meet expectations?**
2. **What was the actual discussion quality of key agenda items? Were there substantive outcomes?**
3. **What is the impact on the industry/community? What are the follow-up actions after the event ends?**

#### health (Health)

**Expert identity**: Clinician / public health expert.

**Three-question probe**:

1. **What is the evidence level of the advice? RCT / observational study / expert opinion?**
2. **How significant is individual variation? Does the general advice apply to specific populations?**
3. **Are risks and side effects fully disclosed? Is the cost-benefit analysis transparent?**

#### press-release (Press Release)

**Expert identity**: PR auditor / media analyst.

**Three-question probe**:

1. **What is the core news value? Is the 5W1H complete?**
2. **Can data and citations withstand verification? Is there selective disclosure?**
3. **From a media perspective, what are the potential follow-up directions for this story?**

#### social-thread (Social Media Thread)

**Expert identity**: Content strategist / social media analyst.

**Three-question probe**:

1. **Does the thread's core argument hold up? Is it adequately supported?**
2. **Does the narrative approach have manipulative tendencies? What is the ratio of emotional language to facts?**
3. **What does the mainstream comment section reaction tell us? Are there high-quality rebuttals?**

#### video (Video Content)

**Expert identity**: Video content analyst / documentary editor.

**Three-question probe**:

1. **What is the video's core narrative arc? Where are the key turning points?**
2. **Does the editing and presentation have a guiding tendency? What might have been cut?**
3. **How do visual and audio elements affect information reception?**

#### job-posting (Job Posting)

**Expert identity**: HR consultant / career planner.

**Three-question probe**:

1. **Does the actual need match the description? Which are real requirements, which are wish lists?**
2. **How competitive is the salary range in the market? What is the actual value of hidden benefits?**
3. **What is the growth path for this position? Where is it in the organizational structure?**

#### real-estate (Real Estate)

**Expert identity**: Real estate analyst / investment advisor.

**Three-question probe**:

1. **What drives the price trend? Fundamentals or speculation?**
2. **What is the long-term development potential of the location? Infrastructure and population flow trends?**
3. **Does the ROI calculation include all costs? Holding costs, opportunity costs?**

#### travel (Travel)

**Expert identity**: Travel planner / destination expert.

**Three-question probe**:

1. **Is the itinerary time allocation reasonable? Is there buffer for unexpected events?**
2. **Are hidden expenses included in the budget? What are actual local price levels?**
3. **Are experience highlights over-marketed? What are real traveler reviews?**

#### recipe (Recipe)

**Expert identity**: Professional chef / food editor.

**Three-question probe**:

1. **Have ingredient ratios been tested multiple times? Which step is most likely to fail for beginners?**
2. **How significant are the differences with alternatives (ingredient substitutions, tool substitutions)?**
3. **What are the principles for taste adjustment? How to fine-tune based on personal preferences?**

#### podcast (Podcast)

**Expert identity**: Podcast producer / content curator.

**Three-question probe**:

1. **What are the guest's core viewpoints? Are they consistent with mainstream consensus in the field?**
2. **What is the most valuable insight from the discussion? Are there actionable recommendations?**
3. **Are the host's questions effective? Do they challenge the guest's assumptions?**

#### announcement (Announcement)

**Expert identity**: Corporate communications expert / stakeholder analyst.

**Three-question probe**:

1. **What is the core message of the announcement? What does it mean for different stakeholders?**
2. **Is the timing choice strategically motivated? Connection to industry/market events?**
3. **Are next steps clear? Is the execution timeline realistic?**

#### sports (Sports)

**Expert identity**: Sports data analyst / event commentator.

**Three-question probe**:

1. **What trends do key data metrics show? Is the sample size sufficient to support conclusions?**
2. **Is performance attribution correct? How are tactical, physical, and psychological factors weighted?**
3. **Does the matchup analysis consider off-field factors (injuries, schedule, home/away)?**

### Brain Schema Override Universal Rules

The following rules apply to all strategies:

1. **Anchoring principle**: Only analyze materials provided by the user. Do not fabricate information not present
2. **DATA_GAP marking**: When data is insufficient, mark `[DATA_GAP]` — do not fabricate data
3. **No empty talk**: Prohibit vague expressions like "this field is rapidly developing" or "worth watching"
4. **No mere listing**: Prohibit simply listing phenomena without causal explanation
5. **MECE check**: Section content must be mutually exclusive and collectively exhaustive
6. **Language lock**: The output language specified in Step 2 must be strictly followed

---

## 日本語 {#japanese}

> EIP (Explain In Picture) プロジェクトドキュメントからの移行。makedocskill の Router 層はコンテンツ戦略を使用して素材からテンプレートへの自動マッチングを実現します。

### 概要

コンテンツ戦略は Router 層のコア概念です。各戦略は以下を定義します：

1. **分析の焦点**：Brain 層が注目すべきポイント
2. **エキスパート質問パターン**：壁打ち時に注入されるドメインエキスパートの視点
3. **Brain Schema Override**：デフォルト分析フレームワークを上書きする特殊ルール
4. **推奨テンプレート**：第一推薦 + 代替2つ

### 戦略一覧表

| # | 戦略 ID | 名称 | 分析の焦点 |
|---|---------|------|-----------|
| 1 | `breaking-news` | 速報ニュース | 事実確認、情報ソース、タイムライン、影響範囲 |
| 2 | `opinion` | 意見論評 | 論証構造、立場、反論、説得力 |
| 3 | `product` | 製品紹介 | コア価値提案、差別化、ユーザー価値、技術スペック |
| 4 | `ecommerce` | EC | 価格比較、コストパフォーマンス、ユーザーレビュー、購入意思決定 |
| 5 | `tutorial` | チュートリアル | ステップ完全性、前提条件、よくあるエラー、学習曲線 |
| 6 | `tech-doc` | 技術ドキュメント | システムアーキテクチャ、API インターフェース、依存関係、拡張性 |
| 7 | `research` | 研究レポート | 方法論、データ品質、統計的有意性、再現性 |
| 8 | `finance` | 財務分析 | 収益構造、キャッシュフロー、バリュエーション、リスク要因 |
| 9 | `legal-policy` | 法律政策 | 条項解釈、コンプライアンス要件、リスク評価、影響分析 |
| 10 | `video` | 動画コンテンツ | タイムライン、キーセグメント、コア論点、感情的アーク |
| 11 | `social-thread` | SNS 長文スレッド | ナラティブ構造、オーディエンス反応、バイラル要素、論争点 |
| 12 | `general` | 汎用 | コア主張、証拠チェーン、論理構造、オーディエンス適合 |
| 13 | `press-release` | プレスリリース | 5W1H、引用ソース、データ裏付け、メディアアングル |
| 14 | `case-study` | ケーススタディ | 背景-問題-解決策-結果、ROI、再現可能性 |
| 15 | `whitepaper` | ホワイトペーパー | 問題定義、技術ソリューション、競合比較、実装パス |
| 16 | `data-analysis` | データ分析 | データソース品質、統計手法、外れ値、トレンド、相関性 |
| 17 | `review` | レビュー | スコアリング次元、長所短所、ユースケース、競合比較 |
| 18 | `interview` | インタビュー | コア観点抽出、コンテキスト、立場、論争点 |
| 19 | `event` | イベント | タイムライン、参加者、アジェンダ、主要成果 |
| 20 | `job-posting` | 求人 | 職務要件、スキルマッチング、企業文化、給与競争力 |
| 21 | `recipe` | レシピ | 食材配合、手順順序、テクニックのポイント、代替案 |
| 22 | `travel` | 旅行 | ルート計画、予算、時間配分、体験ハイライト |
| 23 | `health` | 健康 | 症状-原因-解決策、エビデンスレベル、リスク注意、専門的アドバイス |
| 24 | `real-estate` | 不動産 | 価格トレンド、ロケーション分析、投資リターン、リスク要因 |
| 25 | `startup` | スタートアップ | 問題-解決策-市場-チーム-財務、競争障壁 |
| 26 | `podcast` | ポッドキャスト | ゲスト観点、ディスカッション主線、論争点、キー引用 |
| 27 | `announcement` | アナウンス | コア情報、影響範囲、タイムポイント、次のアクション |
| 28 | `sports` | スポーツ | データ統計、対戦分析、パフォーマンストレンド、キーモーメント |

### エキスパート質問パターン詳解

壁打ち（Step 4）時に、コンテンツ戦略に基づきエキスパート質問モードを切り替えます。これは汎用的な「あなたはアナリストです」ではなく、該当ドメインのエキスパートによる具体的な質問チェーンを注入します。

#### general（汎用）

**エキスパートのアイデンティティ**：汎用アナリスト、論理構造とクリティカルシンキングに秀でる。

**三言質問**：

1. **核心テンションは何か？** 素材中に存在する最も根本的な矛盾または未解決の問題。表面的な「課題」ではなく、深層の構造的テンション。
2. **多層の因果関係は完全か？** 根本原因から表象まで、各因果層にエビデンスの裏付けがあるか？論理の飛躍はないか？
3. **So What テストに合格するか？** 読者が読了後に「So what?」と言うなら、コア主張が十分に鋭くない。最も強力な反論は何か？

**Brain Schema Override**：
- 核心テンションの識別が必須（単純なサマリーではない）
- 各主張には少なくとも一つの反論が必要
- MECE チェック：全 Section の内容が相互排他的かつ網羅的か

#### finance（財務分析）

**エキスパートのアイデンティティ**：投資銀行アナリスト / バイサイドリサーチャー、財務モデリングとバリュエーションに秀でる。

**三言質問**：

1. **収益成長はオーガニックか M&A 駆動か？FCF と NI の乖離はどの程度か？** 収益成長の質は速度より重要。フリーキャッシュフローと純利益の長期的乖離は危険信号。
2. **マネジメントガイダンスの歴史的信頼性は？** 過度に楽観的または保守的なシステム的パターンがあるか？過去4-8四半期のガイダンス vs 実績の比較。
3. **現在のバリュエーションはどのような成長前提を織り込んでいるか？コア前提が崩れた場合のダウンサイドは？** 市場価格にどれだけの楽観が織り込まれているか？インプライド成長率を逆算。

**Brain Schema Override**：
- すべての財務数値にソースと日付を記載
- 成長率はオーガニック vs インオーガニックを区別
- バリュエーションは少なくとも2つの手法のクロスバリデーションを提供
- 予測には不確実性区間を記載
- キャッシュフローが利益指標に優先

#### tech-doc（技術ドキュメント）

**エキスパートのアイデンティティ**：シニアシステムアーキテクト、分散システム設計と技術レビューに秀でる。

**三言質問**：

1. **コア抽象は何か？10倍スケールでの障害モードは？** システムのコア設計判断は何か？トラフィック/データ/ユーザーが10倍に成長した時、最初に壊れるコンポーネントは？
2. **ロックインリスクは？TCO の完全な全体像は？** 技術選定の移行コストはどの程度か？直接コスト以外に、運用、トレーニング、採用の隠れたコストは含まれているか？
3. **障害の爆発半径は？リカバリー時間は？** 単一障害点の影響範囲はどの程度か？隔離メカニズムはあるか？RTO/RPO は明確か？

**Brain Schema Override**：
- システムコンポーネントに依存関係を記載
- パフォーマンス指標にはベンチマークデータが必要
- アーキテクチャ決定にはトレードオフを記録
- 単一障害点の識別が必須
- セキュリティの考慮は省略不可

#### breaking-news（速報ニュース）

**エキスパートのアイデンティティ**：調査記者 / インテリジェンスアナリスト、事実確認と情報検証に秀でる。

**三言質問**：

1. **一次証拠は何か？推測はどれか？** 一次ソース（公式声明、目撃者、生データ）からの情報はどれか？メディアの転述、匿名ソース、アナリストの推測はどれか？
2. **情報のギャップはどの程度か？72時間以内の反転の可能性は？** 現在不明な点は何か？既知の情報に基づき、短期的にストーリーが覆される確率は？類似イベントの歴史的反転率は？
3. **誰が利益を得るか？ステークホルダーの情報操作の動機は？** このナラティブから誰が利益を得るか？情報公開のタイミングは疑わしいか？情報戦の可能性はあるか？

**Brain Schema Override**：
- 各情報にソースタイプを記載（一次/二次/未検証）
- タイムラインは時間単位で正確に
- 情報の空白領域を記載
- 未検証情報に確定的言語を使用しない
- ステークホルダーとその動機を識別

#### opinion（意見論評）

**エキスパートのアイデンティティ**：学術ディベートコーチ / 公共知識人、論証分析と修辞批評に秀でる。

**三言質問**：

1. **論証構造は有効か？論理的誤謬はあるか？** 前提から結論への導出は厳密か？ストローマン、スリッパリースロープ、権威への訴えなどの一般的な誤謬はないか？
2. **最も強力な反論は何か？著者はそれを予見し対応したか？** 最も賢い反対者が反論文を書いたら、核心的な攻撃点はどこか？
3. **立場の基礎にある前提は何か？前提が間違っていたらどうなるか？** 著者が暗黙に受け入れている証明されていない前提は何か？

#### product（製品紹介）

**エキスパートのアイデンティティ**：プロダクトマネージャー / 業界アナリスト、価値提案分析と競合リサーチに秀でる。

**三言質問**：

1. **コアのユーザーペインポイントは何か？この製品は鎮痛剤型の問題を解決しているか、それともビタミン型か？**
2. **差別化の堀はどの程度深いか？競合が複製するにはどのくらいかかるか？**
3. **使用頻度と粘着性はどうか？ユーザー離脱の主な理由は何か？**

#### research（研究レポート）

**エキスパートのアイデンティティ**：学術査読者 / 研究方法論エキスパート。

**三言質問**：

1. **方法論は妥当か？サンプルサイズと選択バイアスはどうか？**
2. **結果は再現可能か？主要発見の p 値と信頼区間は？**
3. **研究の限界は十分に開示されているか？結論はデータがサポートする範囲を超えていないか？**

#### startup（スタートアップ）

**エキスパートのアイデンティティ**：ベンチャーキャピタリスト / シリアルアントレプレナー。

**三言質問**：

1. **市場はどの程度大きいか？新市場を創出しているか、既存市場を奪取しているか？TAM/SAM/SOM のロジックは一貫しているか？**
2. **なぜ今か？過去に誰も成功しなかったのはなぜか？今後6ヶ月の最大のリスクは？**
3. **チームにはどんなアンフェアアドバンテージがあるか？創業者が離脱しても会社は生き残れるか？**

#### case-study（ケーススタディ）

**エキスパートのアイデンティティ**：経営コンサルタント、ケース分析とベストプラクティス抽出に秀でる。

**三言質問**：

1. **背景条件はどの程度特殊か？この成功は他の環境で再現可能か？**
2. **成功の帰属は正しいか？省略された変数や生存者バイアスはないか？**
3. **定量的効果（ROI、KPI 変化）は因果推論に裏付けられているか、それとも単なる相関か？**

#### data-analysis（データ分析）

**エキスパートのアイデンティティ**：データサイエンティスト / 統計学者。

**三言質問**：

1. **データソースの品質とバイアスは？選択バイアス、測定誤差、欠損データはあるか？**
2. **相関が因果と誤読されていないか？交絡因子は制御されているか？**
3. **外れ値の処理は適切か？トレンド予測の前提は透明か？**

#### review（レビュー）

**エキスパートのアイデンティティ**：プロのレビュアー / 消費者権利アドバイザー。

**三言質問**：

1. **レビュー次元は包括的で、重みは適切か？重要なユースケースが欠けていないか？**
2. **レビュー条件は実際の使用に近いか？ラボテストと日常使用のギャップはどの程度か？**
3. **利益相反はあるか？レビュアーとレビュー対象の間に商業関係はないか？**

#### ecommerce（EC）

**エキスパートのアイデンティティ**：EC 運営エキスパート / 消費者リサーチャー。

**三言質問**：

1. **実際のユーザーレビューはどのようなパターンを示すか？ネガティブレビューはどの次元に集中しているか？**
2. **コストパフォーマンスの完全な計算は？隠れたコスト（付属品、メンテナンス、アップグレード）は含まれているか？**
3. **返品率とアフターサービスデータは何を示しているか？**

#### legal-policy（法律政策）

**エキスパートのアイデンティティ**：法務顧問 / コンプライアンスエキスパート。

**三言質問**：

1. **実際の執行と字面の意味にギャップがある条項はどれか？グレーゾーンはどこか？**
2. **異なるステークホルダーへの影響はそれぞれ何か？誰が利益を得、誰が損害を受けるか？**
3. **違反の実際の結果は何か？執行の優先順位と歴史的判例は？**

#### tutorial（チュートリアル）

**エキスパートのアイデンティティ**：技術教育者 / カリキュラムデザイナー。

**三言質問**：

1. **前提知識の想定は妥当か？ターゲットオーディエンスは実際にこれらの前提知識を持っているか？**
2. **ステップ間に認知的ジャンプはあるか？初心者が最もつまずきやすいステップはどこか？**
3. **学習後に独立して応用できるか？それとも単に一度なぞっただけか？**

#### whitepaper（ホワイトペーパー）

**エキスパートのアイデンティティ**：業界エキスパート / 技術レビュー委員。

**三言質問**：

1. **問題定義は正確か？実在する重要な問題を解決しているか？**
2. **技術ソリューションのトレードオフは透明か？代替案との比較は公正か？**
3. **実装パスは現実的か？コンセプトからランディングまでの障壁が過小評価されていないか？**

#### interview（インタビュー）

**エキスパートのアイデンティティ**：シニアジャーナリスト / トーク番組ホスト。

**三言質問**：

1. **インタビュー対象者のコア観点は何か？公開の立場と一致しているか？**
2. **どの質問が回避されたか？沈黙や曖昧な回答は何を暗示するか？**
3. **インタビュー中のキー引用にはコンテキストがあるか？文脈から外すと誤解を招かないか？**

#### event（イベント）

**エキスパートのアイデンティティ**：イベントプランナー / 業界オブザーバー。

**三言質問**：

1. **イベントのコア目標は何か？参加者の収穫は期待に達したか？**
2. **主要アジェンダの実際のディスカッション品質は？実質的な成果はあったか？**
3. **業界/コミュニティへの影響は？イベント終了後のフォローアップアクションは？**

#### health（健康）

**エキスパートのアイデンティティ**：臨床医 / 公衆衛生エキスパート。

**三言質問**：

1. **アドバイスのエビデンスレベルは？RCT / 観察研究 / 専門家意見？**
2. **個体差の影響はどの程度大きいか？一般的なアドバイスは特定の集団に適用できるか？**
3. **リスクと副作用は十分に開示されているか？メリットとデメリットの比較は透明か？**

#### press-release（プレスリリース）

**エキスパートのアイデンティティ**：PR 監査 / メディアアナリスト。

**三言質問**：

1. **コアのニュース価値は何か？5W1H は完全か？**
2. **データと引用は検証に耐えるか？選択的開示はないか？**
3. **メディアの観点から、このストーリーにはどのような潜在的フォローアップの方向性があるか？**

#### social-thread（SNS 長文スレッド）

**エキスパートのアイデンティティ**：コンテンツストラテジスト / SNS アナリスト。

**三言質問**：

1. **スレッドのコア論点は成り立つか？十分な論拠で裏付けられているか？**
2. **ナラティブ手法に操作的傾向はないか？感情的言語と事実の比率は？**
3. **コメント欄の主流の反応は何を示しているか？高品質な反論はあるか？**

#### video（動画コンテンツ）

**エキスパートのアイデンティティ**：動画コンテンツアナリスト / ドキュメンタリーエディター。

**三言質問**：

1. **動画のコアナラティブアークは何か？キーとなる転換点はどこか？**
2. **編集と提示方法に誘導的傾向はあるか？カットされた部分には何があり得るか？**
3. **ビジュアルとオーディオ要素は情報の受容にどう影響するか？**

#### job-posting（求人）

**エキスパートのアイデンティティ**：HR コンサルタント / キャリアプランナー。

**三言質問**：

1. **職務の実際のニーズは記載と一致しているか？実際の要件とウィッシュリストはどれか？**
2. **給与レンジの市場競争力はどうか？隠れた福利厚生の実際の価値は？**
3. **このポジションの成長パスは？組織構造における位置は？**

#### real-estate（不動産）

**エキスパートのアイデンティティ**：不動産アナリスト / 投資アドバイザー。

**三言質問**：

1. **価格トレンドの駆動要因は何か？ファンダメンタルズか投機か？**
2. **ロケーションの長期的発展ポテンシャルは？インフラと人口流動トレンドは？**
3. **投資リターン率の計算にすべてのコストが含まれているか？保有コスト、機会コストは？**

#### travel（旅行）

**エキスパートのアイデンティティ**：旅行プランナー / デスティネーションエキスパート。

**三言質問**：

1. **旅程の時間配分は合理的か？予期せぬ事態へのバッファーはあるか？**
2. **予算に隠れた支出は含まれているか？現地の物価の実際のレベルは？**
3. **体験のハイライトは過度にマーケティングされていないか？実際の旅行者のフィードバックは？**

#### recipe（レシピ）

**エキスパートのアイデンティティ**：プロの料理人 / フードエディター。

**三言質問**：

1. **食材の配合比は複数回テストされたか？初心者が最も失敗しやすいステップは？**
2. **代替案（食材の置き換え、道具の置き換え）での効果の差はどの程度か？**
3. **味の調整の原則は何か？個人の好みに基づいてどう微調整するか？**

#### podcast（ポッドキャスト）

**エキスパートのアイデンティティ**：ポッドキャストプロデューサー / コンテンツキュレーター。

**三言質問**：

1. **ゲストのコア観点は何か？該当分野の主流コンセンサスと一致しているか？**
2. **ディスカッションで最も価値のあるインサイトは何か？実行可能なアドバイスはあるか？**
3. **ホストの質問は効果的か？ゲストの前提に挑戦しているか？**

#### announcement（アナウンス）

**エキスパートのアイデンティティ**：企業コミュニケーションエキスパート / ステークホルダーアナリスト。

**三言質問**：

1. **アナウンスのコアメッセージは何か？異なるステークホルダーにとっての意味は？**
2. **タイミングの選択に戦略的意図はあるか？業界/市場イベントとの関連は？**
3. **次のアクションは明確か？実行タイムラインは現実的か？**

#### sports（スポーツ）

**エキスパートのアイデンティティ**：スポーツデータアナリスト / イベントコメンテーター。

**三言質問**：

1. **主要データ指標はどのようなトレンドを示しているか？サンプルサイズは結論を裏付けるのに十分か？**
2. **パフォーマンスの帰属は正しいか？戦術、フィジカル、メンタル要因の重みはどう配分されるか？**
3. **対戦分析で場外要因（怪我、スケジュール、ホーム/アウェイ）は考慮されているか？**

### Brain Schema Override 汎用ルール

以下のルールはすべての戦略に適用されます：

1. **アンカリング原則**：ユーザーが提供した素材のみを分析。出現していない情報を捏造しない
2. **DATA_GAP マーキング**：データ不足時は `[DATA_GAP]` と記載し、データを捏造しない
3. **空言禁止**：「この分野は急速に発展している」「注目に値する」などの空虚な表現を禁止
4. **列挙のみ禁止**：現象を列挙するだけで因果説明をしないことを禁止
5. **MECE チェック**：Section の内容は相互排他的かつ網羅的でなければならない
6. **言語ロック**：Step 2 で指定された出力言語を厳格に遵守

---

## 中文 {#chinese}

> 基于 EIP (Explain In Picture) 项目文档迁移。makedocskill 的 Router 层通过内容策略实现从素材到模板的自动匹配。

### 概述

内容策略是 Router 层的核心概念。每种策略定义了：

1. **分析侧重**：Brain 层应该关注什么
2. **专家追问模式**：壁打ち时注入的领域专家视角
3. **Brain Schema Override**：覆盖默认分析框架的特殊规则
4. **推荐模板**：首选 + 2 个备选

### 策略总览表

| # | 策略 ID | 名称 | 分析侧重 |
|---|---------|------|---------|
| 1 | `breaking-news` | 突发新闻 | 事实核查、信息来源、时间线、影响范围 |
| 2 | `opinion` | 观点评论 | 论证结构、立场、反面论据、说服力 |
| 3 | `product` | 产品介绍 | 核心价值主张、差异化、用户价值、技术规格 |
| 4 | `ecommerce` | 电商 | 价格对比、性价比、用户评价、购买决策 |
| 5 | `tutorial` | 教程 | 步骤完整性、前置条件、常见错误、学习曲线 |
| 6 | `tech-doc` | 技术文档 | 系统架构、API 接口、依赖关系、扩展性 |
| 7 | `research` | 研究报告 | 方法论、数据质量、统计显著性、可重复性 |
| 8 | `finance` | 财务分析 | 收入结构、现金流、估值、风险因子 |
| 9 | `legal-policy` | 法律政策 | 条款解读、合规要求、风险评估、影响分析 |
| 10 | `video` | 视频内容 | 时间线、关键片段、核心论点、情感弧线 |
| 11 | `social-thread` | 社交媒体长帖 | 叙事结构、观众反应、传播要素、争议点 |
| 12 | `general` | 通用 | 核心主张、证据链、逻辑结构、受众适配 |
| 13 | `press-release` | 新闻稿 | 5W1H、引用来源、数据支撑、媒体角度 |
| 14 | `case-study` | 案例研究 | 背景-问题-方案-结果、ROI、可复制性 |
| 15 | `whitepaper` | 白皮书 | 问题定义、技术方案、竞品对比、实施路径 |
| 16 | `data-analysis` | 数据分析 | 数据源质量、统计方法、异常值、趋势、相关性 |
| 17 | `review` | 评测 | 评分维度、优劣势、适用场景、竞品对比 |
| 18 | `interview` | 访谈 | 核心观点提取、上下文、立场、争议点 |
| 19 | `event` | 活动 | 时间线、参与者、议程、关键成果 |
| 20 | `job-posting` | 招聘 | 岗位要求、技能匹配、公司文化、薪酬竞争力 |
| 21 | `recipe` | 食谱 | 食材配比、步骤顺序、技巧要点、替代方案 |
| 22 | `travel` | 旅行 | 路线规划、预算、时间分配、体验亮点 |
| 23 | `health` | 健康 | 症状-原因-方案、证据等级、风险提示、专业建议 |
| 24 | `real-estate` | 房地产 | 价格趋势、区位分析、投资回报、风险因素 |
| 25 | `startup` | 创业 | 问题-方案-市场-团队-财务、竞争壁垒 |
| 26 | `podcast` | 播客 | 嘉宾观点、讨论主线、争议点、关键引用 |
| 27 | `announcement` | 公告 | 核心信息、影响范围、时间节点、下一步行动 |
| 28 | `sports` | 体育 | 数据统计、对阵分析、表现趋势、关键时刻 |

### 专家追问模式详解

壁打ち（Step 4）时，根据内容策略切换专家追问模式。这不是通用的「你是一个分析师」，而是注入该领域专家的具体追问链。

#### general（通用）

**专家身份**：通用分析师，擅长逻辑结构和批判性思维。

**三言追问**：

1. **核心张力是什么？** 素材中存在的最根本矛盾或未解决的问题。不是表面的「挑战」，而是深层的结构性张力。
2. **多层因果完整吗？** 从根因到表象，是否每一层因果关系都有证据支撑？是否存在跳跃推理？
3. **So What 测试通过吗？** 如果读者读完后说「So what?」，说明核心主张不够锋利。最强的反论是什么？

**Brain Schema Override**：
- 必须识别核心张力（非简单总结）
- 每个主张必须有至少一个反面论据
- MECE 检验：所有 Section 的内容是否互斥且穷尽

#### finance（财务分析）

**专家身份**：投行分析师 / 买方研究员，擅长财务建模和估值。

**三言追问**：

1. **Revenue growth 是 organic 还是 M&A 驱动？FCF 与 NI 的背离有多大？** 收入增长的质量比速度更重要。自由现金流与净利润的长期背离是危险信号。
2. **Management guidance 的历史可信度如何？** 管理层预期是否有系统性偏乐观或偏保守的模式？过去 4-8 个季度的 guidance vs actual 对比。
3. **当前估值隐含了什么增长假设？如果核心假设失败，downside 在哪里？** 市场定价已经包含了多少乐观预期？反向推导隐含增长率。

**Brain Schema Override**：
- 所有财务数字必须标注来源和时间
- 增长率必须区分 organic vs inorganic
- 估值必须提供至少两种方法的交叉验证
- 预测必须标注不确定性区间
- 现金流优先于利润指标

#### tech-doc（技术文档）

**专家身份**：高级系统架构师，擅长分布式系统设计和技术评审。

**三言追问**：

1. **核心抽象是什么？10x 规模下的故障模式是什么？** 系统的核心设计决策是什么？当流量/数据/用户增长 10 倍时，哪个组件会先崩溃？
2. **Lock-in 风险如何？TCO 的完整图景是什么？** 技术选型的迁移成本有多高？除了直接成本，运维、培训、招聘的隐性成本是否计入？
3. **故障的爆炸半径是什么？恢复时间是多少？** 单点故障会影响多大范围？是否有隔离机制？RTO/RPO 是否明确？

**Brain Schema Override**：
- 系统组件必须标注依赖关系
- 性能指标必须有基准测试数据
- 架构决策必须记录 trade-off
- 必须识别单点故障
- 安全性考虑不能遗漏

#### breaking-news（突发新闻）

**专家身份**：调查记者 / 情报分析师，擅长事实核查和信息验证。

**三言追问**：

1. **一次证据是什么？哪些是推测？** 哪些信息来自第一手来源（官方声明、目击者、原始数据）？哪些是媒体转述、匿名来源或分析师推测？
2. **信息空白有多大？72 小时内反转的可能性？** 目前不知道什么？基于已知信息，故事在短期内被颠覆的概率有多大？历史上类似事件的反转率是多少？
3. **Who benefits? 利益相关方的信息操纵动机是什么？** 谁从这个叙事中获益？信息发布的时机是否可疑？是否存在信息战的可能？

**Brain Schema Override**：
- 每条信息必须标注来源类型（一次/二次/未验证）
- 时间线必须精确到小时
- 必须标注信息空白区域
- 不得使用确定性语言描述未验证信息
- 必须识别利益相关方及其动机

#### opinion（观点评论）

**专家身份**：学术辩论教练 / 公共知识分子，擅长论证分析和修辞批评。

**三言追问**：

1. **论证结构是否有效？是否存在逻辑谬误？** 前提到结论的推导是否严密？是否存在稻草人、滑坡、诉诸权威等常见谬误？
2. **最强的反面论据是什么？作者是否预见并回应了？** 如果由最聪明的反对者来写反驳文，核心攻击点在哪里？
3. **立场的基础假设是什么？如果假设错误会怎样？** 作者默认接受了哪些未经证明的假设？

#### product（产品介绍）

**专家身份**：产品经理 / 行业分析师，擅长价值主张分析和竞品研究。

**三言追问**：

1. **核心用户痛点是什么？这个产品解决的是止痛药问题还是维生素问题？**
2. **差异化壁垒有多深？竞争对手复制需要多长时间？**
3. **使用频率和粘性如何？用户流失的主要原因是什么？**

#### research（研究报告）

**专家身份**：学术审稿人 / 研究方法论专家。

**三言追问**：

1. **方法论是否合理？样本量和选择偏差如何？**
2. **结果是否可重复？关键发现的 p-value 和置信区间？**
3. **研究限制是否充分披露？结论是否超出了数据支持的范围？**

#### startup（创业）

**专家身份**：风险投资人 / 连续创业者。

**三言追问**：

1. **市场有多大？是创造新市场还是抢夺已有市场？TAM/SAM/SOM 的逻辑是否自洽？**
2. **为什么是现在？过去为什么没人做成？未来 6 个月最大的风险是什么？**
3. **团队有什么不公平优势？如果创始人离开，公司还能活吗？**

#### case-study（案例研究）

**专家身份**：管理咨询顾问，擅长案例分析和最佳实践提炼。

**三言追问**：

1. **背景条件有多特殊？这个成功在其他环境下是否可复制？**
2. **成功归因是否正确？是否存在遗漏变量或幸存者偏差？**
3. **定量效果（ROI、KPI 变化）是否有因果推断支撑，还是仅仅是相关性？**

#### data-analysis（数据分析）

**专家身份**：数据科学家 / 统计学家。

**三言追问**：

1. **数据源的质量和偏差如何？是否存在选择偏差、测量误差或缺失数据？**
2. **相关性是否被误读为因果性？是否做了混淆因素控制？**
3. **异常值的处理是否合理？趋势预测的假设是否透明？**

#### review（评测）

**专家身份**：专业评测人 / 消费者权益顾问。

**三言追问**：

1. **评测维度是否全面且权重合理？是否遗漏了重要使用场景？**
2. **评测条件是否贴近真实使用？实验室测试与日常使用的差距有多大？**
3. **是否存在利益冲突？评测者与被评对象之间是否有商业关系？**

#### ecommerce（电商）

**专家身份**：电商运营专家 / 消费者研究员。

**三言追问**：

1. **真实用户反馈呈现什么模式？差评集中在哪些维度？**
2. **性价比的完整计算是什么？隐性成本（配件、维护、迭代）是否计入？**
3. **退货率和售后数据说明什么？**

#### legal-policy（法律政策）

**专家身份**：法律顾问 / 合规专家。

**三言追问**：

1. **哪些条款的实际执行与字面含义存在差距？模糊地带在哪里？**
2. **对不同利益相关方的影响分别是什么？谁受益、谁受损？**
3. **违规的实际后果是什么？执法的优先级和历史案例？**

#### tutorial（教程）

**专家身份**：技术教育者 / 课程设计师。

**三言追问**：

1. **前置知识假设是否合理？目标受众是否真的具备这些前置知识？**
2. **步骤之间是否存在认知跳跃？新手最可能在哪一步卡住？**
3. **学完之后能独立应用吗？还是仅仅跟着做了一遍？**

#### whitepaper（白皮书）

**专家身份**：行业专家 / 技术评审委员。

**三言追问**：

1. **问题定义是否精准？是否在解决一个真实且重要的问题？**
2. **技术方案的 trade-off 是否透明？与替代方案的比较是否公正？**
3. **实施路径是否现实？从概念到落地的障碍是否被低估？**

#### interview（访谈）

**专家身份**：资深记者 / 访谈节目主持人。

**三言追问**：

1. **被采访者的核心观点是什么？与公开立场是否一致？**
2. **哪些问题被回避了？沉默或模糊回答暗示什么？**
3. **访谈中的关键引用是否有上下文？脱离语境是否会误导？**

#### event（活动）

**专家身份**：活动策划人 / 行业观察者。

**三言追问**：

1. **活动的核心目标是什么？参与者的收获是否达到预期？**
2. **关键议程的实际讨论质量如何？是否有实质性成果？**
3. **对行业/社区的影响是什么？活动结束后的跟进行动是什么？**

#### health（健康）

**专家身份**：临床医生 / 公共健康专家。

**三言追问**：

1. **建议的证据等级是什么？RCT / 观察性研究 / 专家意见？**
2. **个体差异的影响有多大？通用建议是否适用于特定人群？**
3. **风险和副作用是否充分披露？利弊权衡是否透明？**

#### press-release（新闻稿）

**专家身份**：公关审计 / 媒体分析师。

**三言追问**：

1. **核心新闻价值是什么？5W1H 是否完整？**
2. **数据和引用是否经得起核实？是否有选择性披露？**
3. **从媒体角度，这个故事有哪些潜在的追问方向？**

#### social-thread（社交媒体长帖）

**专家身份**：内容策略师 / 社交媒体分析师。

**三言追问**：

1. **帖子的核心论点是否站得住脚？是否有充分论据支撑？**
2. **叙事方式是否有操纵倾向？情绪化语言与事实的比例？**
3. **评论区的主流反应说明什么？是否有高质量的反驳？**

#### video（视频内容）

**专家身份**：视频内容分析师 / 纪录片编辑。

**三言追问**：

1. **视频的核心叙事弧线是什么？关键转折点在哪里？**
2. **剪辑和呈现方式是否有引导倾向？被剪掉的部分可能是什么？**
3. **视觉和音频元素如何影响信息的接收？**

#### job-posting（招聘）

**专家身份**：HR 顾问 / 职业规划师。

**三言追问**：

1. **岗位的实际需求与描述是否一致？哪些是真需求，哪些是愿望清单？**
2. **薪酬范围在市场上的竞争力如何？隐性福利的实际价值？**
3. **这个岗位的成长路径是什么？组织架构中的位置？**

#### real-estate（房地产）

**专家身份**：房地产分析师 / 投资顾问。

**三言追问**：

1. **价格趋势的驱动因素是什么？是基本面还是投机？**
2. **区位的长期发展潜力如何？基础设施和人口流动趋势？**
3. **投资回报率的计算是否包含所有成本？持有成本、机会成本？**

#### travel（旅行）

**专家身份**：旅行策划师 / 目的地专家。

**三言追问**：

1. **行程的时间分配是否合理？是否为意外留了缓冲？**
2. **预算的隐性支出是否计入？当地物价的实际水平？**
3. **体验亮点是否过度营销？真实游客反馈如何？**

#### recipe（食谱）

**专家身份**：专业厨师 / 美食编辑。

**三言追问**：

1. **食材配比是否经过多次测试？新手最容易失败的步骤？**
2. **替代方案（食材替换、工具替换）的效果差异有多大？**
3. **口味调整的原则是什么？如何根据个人偏好微调？**

#### podcast（播客）

**专家身份**：播客制作人 / 内容策展人。

**三言追问**：

1. **嘉宾的核心观点是什么？与该领域的主流共识是否一致？**
2. **讨论中最有价值的洞见是什么？是否有可操作的建议？**
3. **主持人的提问是否有效？是否挑战了嘉宾的假设？**

#### announcement（公告）

**专家身份**：企业通信专家 / 利益相关方分析师。

**三言追问**：

1. **公告的核心信息是什么？对不同利益相关方的含义分别是什么？**
2. **时间节点的选择是否有战略意图？与行业/市场事件的关联？**
3. **下一步行动是否明确？执行时间表是否现实？**

#### sports（体育）

**专家身份**：体育数据分析师 / 赛事评论员。

**三言追问**：

1. **关键数据指标说明了什么趋势？样本量是否足够支撑结论？**
2. **表现的归因是否正确？战术、体能、心理因素的权重如何分配？**
3. **对阵分析中是否考虑了场外因素（伤病、赛程、主客场）？**

### Brain Schema Override 通用规则

以下规则适用于所有策略：

1. **锚定原则**：仅分析用户提供的素材。未出现的信息不得捏造
2. **DATA_GAP 标记**：数据不足时必须标注 `[DATA_GAP]`，不得编造数据
3. **禁止空话**：禁止「这个领域正在快速发展」「值得关注」等空泛表述
4. **禁止罗列**：禁止仅罗列现象不做因果解释
5. **MECE 检验**：Section 内容必须互斥且穷尽
6. **语言锁定**：Step 2 指定的输出语言必须严格遵守
