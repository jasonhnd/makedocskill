<div align="center">

# make-doc-skill v4

### 公司文档生成器

---

*生成公司专属的董事会材料、IR / CFO 提案、中日双语文档和 16:9 演示文稿 —— 输出为真实的 Word、PDF 和 HTML。*

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](../../LICENSE)
[![Claude Code](https://img.shields.io/badge/Claude%20Code-Skill-green.svg)](https://code.claude.com/docs/en/skills)
[![agentskill.sh](https://img.shields.io/badge/agentskill.sh-Published-yellow.svg)](https://agentskill.sh/@jasonhnd/makedocskill)
[![Version](https://img.shields.io/badge/version-0.0.6-purple.svg)](../../SKILL.md)

董事会材料 · IR / CFO 提案 · 中日双语 · 正式 Word/PDF · 1920x1080 演示文稿。
Brain -> Router -> Canvas 智能管线。

**这不是主题套用。它推断真正的交付物、重建结构、锁定数字与语言，然后渲染并验证真实的 DOCX/PDF/HTML。**

[查看效果](#使用方法) · [安装](#安装) · [工作原理](#架构) · [输出族](#输出族)

**其他语言：**

[English](../../README.md) · [日本語](../ja/README.md)

</div>

---

## 为什么需要这个 Skill

大多数 AI 工具以同样的方式生成公司文档：把文字灌进一个主题然后宣告完成。你得到的是一堵要点墙，标题上加了品牌色 —— 但数字从未对照原始资料核对、日语是随意口吻而非董事会级别、章节不分页、那份没人真正打开过的导出 PDF 是坏的。

问题不在于生成速度。问题在于，**在文件导出之前，没有发生任何编辑判断**。

上市公司 CFO 办公室的董事会文档编辑不会先打开 Word。他们先读原始资料，判断它究竟是董事会材料、IR 材料还是 CFO 提案，挑战审计师会攻击的薄弱论点，把每个数字锁定到原始资料，修正语言，最后才排版。文档是最后一公里，而非第一公里。

make-doc-skill 以同样的方式工作。它通过 **Brain -> Router -> Canvas** 管线将判断与渲染分离：

- **Brain** 是编辑与领域分析师。它推断真正的交付物、重建结构、运行三维专家壁打ち（假设挑战、盲点补全、视角重构）、统一术语，并修正破碎的层级与语气。这就是 **Codex 智能层** —— 每一份有说服力的董事会材料背后的执行引擎。
- **Router** 是文档架构师。它将交付物类型映射到一个输出族 —— 正式 DOCX、中日双语拆分文件、16:9 演示文稿，或 HTML —— 然后生成逐章节的构图方案，并选择渲染器与模板。
- **Canvas** 是渲染器与排版师。它套用公司品牌 token 与版式规则，渲染 DOCX/HTML，导出 PDF，并执行 QA。它**不做**任何编辑决策。

Token 是设计记忆。Brain 的判断是执行引擎。**深度来自判断的锐利度，而非步骤数量** —— 一份董事会文档之所以有说服力，是因为 Brain 正确读懂了资料并重建了它，而不是因为 Canvas 套了个配色主题。

结果：正式的 Word/PDF 董事会材料和 IR/CFO 演示文稿，读起来像 CFO 办公室出品，数字经得起审计。全部来自一个 Claude Code Skill。

---

## 架构

```
┌──────────────────────────────────────────────────────────────┐
│                      make-doc-skill v4                       │
│                       公司文档生成器                          │
│                                                              │
│   ┌──────────┐     ┌──────────┐     ┌──────────────────┐    │
│   │  Brain    │────>│  Router  │────>│     Canvas       │    │
│   │          │     │          │     │                  │    │
│   │ 编辑 /    │     │ 文档     │     │ 渲染 /           │    │
│   │ 分析师    │     │ 架构师   │     │ 排版师           │    │
│   │ 壁打ち    │     │ 输出族 + │     │ DOCX / HTML      │    │
│   │ 数字与    │     │ 结构方案 │     │ PDF 导出         │    │
│   │ 语言锁定  │     │          │     │ QA / 保真度      │    │
│   └──────────┘     └──────────┘     └──────────────────┘    │
│                                                              │
│   原始资料 + token    构图方案       真实 DOCX/PDF/HTML     │
└──────────────────────────────────────────────────────────────┘
```

**核心原则**：深度来自判断的锐利度，而非步骤数量。

三层在设计上是解耦的。即使 Brain 进行了大量重写，Canvas 也绝不会把分析性散文灌进文档 —— Router 强制将其转化为文档结构（章节、表格、提示框、图示）。Token 是设计记忆；Brain 的判断是执行引擎。

---

## 两种模式 —— Quick Mode / Full Mode

| 模式 | 触发 | 流程 |
|------|------|------|
| **Quick Mode** | 丢入现有 Word/PDF/文本，想要快速精修输出，无需建项目 | 检测输入 -> 提取 -> 推断真正的交付物 -> 套用公司 token（或合理默认）-> Brain 轻量处理 -> 渲染 -> 导出 PDF -> 报告路径 |
| **Full Mode** | 董事会/IR 材料、双语交付，或「把文档好好做出来」 | 8 步审计管线，含中间文件与用户检查点 |

Quick Mode 以壁打ち深度换速度，但**仍运行数字保真与语言锁定检查，且绝不捏造**。Quick 输出后，会提供升级到 Full Mode 的选项（保留已规范化的原始资料，追加 token、壁打ち与审查）。

---

## 输出族

主要交付物是正式文档。HTML 可视化文档是可选的次要模式。

| 输出族 | 使用场景 | 输出 |
|--------|---------|------|
| **正式 DOCX/PDF** *(主要)* | 董事会材料、内部审批文件、政策说明、上市公司材料 | A4、12pt 正文、章节分页、稳定目录、克制的表格、品牌强调色表头、固定 SVG/PNG 图示 |
| **中日双语拆分文档** | 分语言交付 | 一份日语 DOCX/PDF + 一份中文 DOCX/PDF，结构对称，使用各语言专属字体，无跨语言残留 |
| **1920x1080 HTML/PDF 演示文稿** | CFO 提案、IR 演示、运营简报、大屏审阅 | 16:9 固定视口、`html { font-size: 20px }`、品牌强调条、会议室可读性、单 HTML 文件 + PDF 导出 |
| **HTML 可视化文档** *(可选)* | 单页 / 图示文档 / 可视化解说 —— 而非正式公司文档 | 使用 v3 HTML 机制的自包含单页滚动或 16:9 HTML，套用公司 token 而非默认蓝色 |

---

## 深度控制（S / M / L / XL）

深度控制 Brain 分析的强度与 QA 的严格度。它**不**控制数字保真或语言锁定是否生效 —— 这二者始终生效。

| | S | M | L | XL |
|--|---|---|---|-----|
| **使用场景** | 单页执行摘要 / 备忘 | 标准提案 / 说明 | 完整董事会材料 / IR 文档 | 综合董事会材料 + 附录 |
| **章节数** | 3-5 | 5-8 | 8-12 | 12+ |
| **Brain 深度** | 核心结论 + 行动项 | + 证据评估 | + 解释框架 + 替代方案 | + 多视角审查 + 极端测试 |
| **壁打ち轮次** | 0-1 | 1-2 | 2-3 | 3+ |
| **图示数** | 0-1 | 1-2 | 2-4 | 4+ |
| **QA 严格度** | 输出存在 + 字体 + 路径 | + 目录 + 分页 | + 双语对齐 + 图示 QA | 完整质量门 + 视觉联系表 |
| **演示文稿页数（若 16:9）** | 3-6 | 6-10 | 10-15 | 15+ |

若用户未指定尺寸，则从交付物推断：备忘是 S，CFO 提案是 M-L，含附录的完整董事会材料是 L-XL。

---

## 安装

| 平台 | 安装方式 |
|------|---------|
| **Claude Code** | `cp SKILL.md ~/.claude/skills/make-doc-skill/SKILL.md` |
| **Gemini CLI / Antigravity** | `npx skills add jasonhnd/makedocskill` |
| **OpenAI Codex CLI** | `npx skills add jasonhnd/makedocskill` |
| **Claude.ai** | 将 `SKILL.md` 上传到项目知识库 |
| **Cursor / VS Code Copilot** | `npx skills add jasonhnd/makedocskill` |
| **ChatGPT / Gemini Web** | 将 `SKILL.md` 内容粘贴到系统指令中 |

### 快速安装

```bash
# 一行命令
mkdir -p ~/.claude/skills/make-doc-skill && curl -sL https://raw.githubusercontent.com/jasonhnd/makedocskill/main/SKILL.md -o ~/.claude/skills/make-doc-skill/SKILL.md

# 或克隆后复制
git clone https://github.com/jasonhnd/makedocskill.git
cp makedocskill/SKILL.md ~/.claude/skills/make-doc-skill/SKILL.md
```

> 正式 DOCX/PDF 输出需要 DOCX/PDF 渲染的文档工具。仅当在可选 HTML 模式中从 YouTube 源提取时才需要 `yt-dlp`。

### 验证

```
# 在 Claude Code 中运行
/make-doc-skill
```

---

## 使用方法

### 精修品牌 Word 文档

```
你：@board_draft.docx 把这个精修成正式董事会材料，用我们的企业红，日语
Skill：[读取 DOCX，推断交付物 = board_material，规范化原始资料，标记 [DATA_GAP]]
Skill：[构建公司 token：主色 #c0392b，正文 Hiragino Sans，移除误用的蓝色]
Skill：壁打ち发现 3 个审计师会提出的薄弱点：...
Skill：[渲染 A4 DOCX，12pt 正文，章节分页，导出 PDF，运行 PDF QA]
Skill：完成。~/Downloads/board_draft_精修版.docx + .pdf
```

### 中日双语拆分

```
你：@midterm_plan.md 做一份日语董事会版和一份中文版，拆成两个文件
Skill：[锁定输出语言，引文保留原文语言，对齐章节结构]
Skill：[渲染一份日语 DOCX/PDF 和一份中文 DOCX/PDF，目录与表格对称]
Skill：完成。~/Downloads 中的 _日本語版 与 _中文版，已检查语言残留。
```

### CFO 16:9 提案演示

```
你：把这份中期经营计划做成给董事会的 CFO 16:9 演示（Size L）
Skill：[推断 IR/CFO 演示，构建构图方案，12 页，品牌强调条]
Skill：[渲染 1920x1080 HTML，导出 PDF，验证页数与 16:9 尺寸]
Skill：完成。~/Downloads/CFO_Proposal.html + .pdf
```

---

## Codex 智能层

仅有设计 token 是不够的。它们定义颜色、字体、尺寸和间距 —— 但不决定一份文档是否有说服力、是否易读、是否适合上市公司语境。这一层**就是**管线中的 Brain。

它每次都运行：

- **推断真正的交付物**，而非仅看字面文件类型。一个「Word/PDF」请求可能是董事会材料、IR 材料、CFO 提案、业务说明或对外演示。
- **设计前先读现有文档。** 不仅提取文字，还提取薄弱点：破碎的层级、糟糕的断行、拥挤的表格、不稳定的图示、错误的对齐、糟糕的页面节奏、不匹配的语气。
- **将模糊的品牌方向转为具体 token。**「不要用蓝色，用我们的企业色」意味着定义真实的体系（如红/灰），并从标题、表格、链接、图示和图表中移除误用的蓝色。
- **做编辑决策。** 重写标题、拆分过载段落、统一术语、收紧章节顺序。
- **验证真实的输出面。** DOCX 在导出 PDF 可读之前不算完成；演示在浏览器渲染与 PDF 导出都正确之前不算完成。
- **保持用户文件纪律。** 绝不覆盖原始文件。最终文件放入交付文件夹（默认 `~/Downloads`）。

简言之：token 是设计记忆；Codex 式的判断是执行引擎。Skill 应当审视、决策、重建、验证、交付。

---

## 壁打ち、锚定与禁止规则

这正是让 Codex 智能层可靠、而非「LLM 随便改改」的原因。壁打ち在 M 深度及以上运行；锚定与禁止规则在所有深度（含 Quick Mode）运行。

### 三维专家追问（Step 4）

| 维度 | 目标 | 强制 |
|------|------|------|
| **假设挑战** | 检验核心主张 | 主张可辩护吗？是一手数据还是断言？董事会成员或审计师会提出的最强反驳是什么？ |
| **盲点补全** | 补齐缺失维度 | 缺了什么 —— 下行风险、风险、稀释、监管、税务、先例、时间线？ |
| **视角重构** | 提供更好的框架 | 风险优先 / 对比优先 / 时间线优先的框架是否更适合这个受众？ |

### 锚定规则（上市公司材料不可妥协）

- **数字保真** —— 完全照原始资料使用数字。绝不四舍五入，绝不臆造。货币、单位、财年期间保持精确。
- **材料锚定** —— 只陈述原始资料支持的内容。缺失数据标记 `[DATA_GAP]`。
- **来源标注** —— 补充/背景知识标记为 `[Supplemental]`。
- **语言锁定** —— 输出语言一旦确定，整条链遵循它；引文保留原文语言。
- **金字塔 + MECE** —— 先结论，再论据，后数据；章节相互独立、完全穷尽。

### 禁止输出

- 不用为回避结论而填充的模糊话术。
- 不回避判断 —— 若材料支持某项建议，就明确陈述。
- 不臆造数字、引用或法律/税务/会计结论；未经核实的陈述须标记为草案/假设。
- 不只罗列现象而不做因果解释。
- 不对薄弱原始资料做表面改写 —— 要重建它。

---

## 管线 —— Full Mode 8 步

每一步在项目文件夹写入一份可审阅文件，并以检查点结束：**继续 / 重做此步 / 用默认跳过 / 直接渲染**。跳过时套用合理的公司 token 默认值。迭代将旧文件归档到 `_history/v[N]/`；项目根目录始终保存最新版本。

| 步骤 | 动作 | 输出 |
|------|------|------|
| **1** | 公司 token | `01_company_tokens.md`（品牌 / 语言 / docx / 演示 token） |
| **2** | 文档简报 | `02_document_brief.md`（交付物类型、受众、语言模式、深度、输出、交付文件夹） |
| **3** | 原始资料规范化 | `03_source_normalized.md`（Word/PDF/文本 -> 结构化 MD/YAML；保留引文；标记 `[DATA_GAP]`） |
| **4** | Codex 壁打ち | `04_codex_sparring.md`（三维追问、薄弱点清单、编辑决策） |
| **5** | 构图方案 | `05_composition_plan.md`（章节蓝图、渲染器 + 模板选择） |
| **6** | 版式审查 | `06_layout_review.md`（渲染前 结构 / 品质 / 品牌门） |
| **7** | 渲染日志 | `07_render_log.md`（生成 DOCX/HTML、记录决策、导出 PDF） |
| **8** | PDF QA | `08_pdf_qa.md`（pdfinfo / pdffonts + 视觉检查、门结果、最终路径） |

**管线透明度**：每个决策记录在其步骤文件中（可追溯）；用户可在任意步骤暂停、审阅或修改（可审计）；Brain 就地解释关键选择（可解释）；迭代成本低（低成本回滚）。

---

## Token 模型

每家公司在渲染前都获得一份 token 文件。使用 JSON 或 YAML。不要把颜色、字体、尺寸或间距硬编码进模板。

```yaml
company:
  legal_name: "Acme Holdings, Inc."   # 仅为示例 —— 替换为目标公司
  ticker: "0000"
  market: "Tokyo Stock Exchange Growth"
  brand_name: "Acme"

brand:
  primary: "#c0392b"        # 示例品牌配色 —— 替换为公司真实 token
  primary_dark: "#922b21"
  text: "#242424"
  background: "#ffffff"
  border: "#d9d9d9"

language:
  ja_font: "Hiragino Sans"
  zh_font: "PingFang SC"
  latin_font: "Aptos"

docx:
  page_size: "A4"
  body_pt: 12
  line_spacing: 1.18
  chapter_page_break: true

slides:
  canvas_px: [1920, 1080]
  base_font_px: 20
```

规则：

- 除非 token 定义了额外的语义色，否则以公司主色作为唯一的功能强调色。
- 当品牌不需要时，避免使用蓝/绿/橙功能色。
- 通过字重、间距和弱化文字来表达层级，而非失控的字号。

---

## 质量门

Step 6（版式审查）与 Step 8（PDF QA）背后的具体检查，在最终交付前运行：

- 输出存在于请求的文件夹；DOCX 打开无修复警告。
- PDF 从最终 DOCX/HTML 源导出；字体可读且符合语言。
- 正式 Word 文档正文为 12pt（除非另行指定）；需要时章节另起一页。
- 目录对齐正确；表格不溢出页边距；图示未破损，且不是用不稳定的 Word 形状箭头拼的。
- 当公司品牌为红/灰时，不出现意外的蓝/绿/橙。
- 中日拆分文件含正确语言。
- 对 HTML 演示，浏览器截图与 PDF 导出都显示不溢出的 16:9 页面。
- **数字保真成立**：每个数字、单位、货币、财年期间都与原始资料一致；缺口为 `[DATA_GAP]`；未经核实的法律/税务陈述标记为草案。

```bash
pdfinfo "/path/to/output.pdf"
pdffonts "/path/to/output.pdf"
```

---

## 交付约定

除非用户指定其他目的地：

- 最终文件放入 `~/Downloads`（macOS/Linux）或 `%USERPROFILE%\Downloads`（Windows）。
- 输出文件名贴近原始文件名，加上清晰后缀，如 `_精修版`、`_日本語版`、`_中文版` 或 `_CFO Proposal`。
- 除非明确要求，否则不覆盖原始文件。

---

## 可选 HTML 输出模式

当请求的交付物是 HTML 可视化单页或图示文档 —— **而非**正式 Word/PDF 文档 —— 时，Skill 使用保留的 v3 HTML 机制：18 个可视化模板、28 个内容策略、16 个 HTML 组件，以及 HTML 深度可视化规则。它产出自包含的单页滚动或 16:9 HTML 文档，并套用公司 token 而非默认蓝色 CI。

该机制是一个有能力的次要输出。上面的公司文档管线是主路径。

| 参考（HTML 模式） | 内容 |
|------------------|------|
| [TEMPLATES.md](../../docs/TEMPLATES.md) | 18 个 HTML 可视化模板 |
| [CONTENT_STRATEGIES.md](../../docs/CONTENT_STRATEGIES.md) | 28 个内容策略 + 专家追问链 |
| [DEPTH_VISUALIZATION.md](../../docs/DEPTH_VISUALIZATION.md) | HTML 深度可视化规则 |

---

## 文档

| 文档 | 内容 |
|------|------|
| [PIPELINE.md](../../docs/PIPELINE.md) | 公司文档 8 步 Full-Mode 管线（01_company_tokens -> 08_pdf_qa） |
| [PROMPT_ENGINEERING.md](../../docs/PROMPT_ENGINEERING.md) | Brain / Router / Canvas 角色设计 + 提示词元原则 |
| [DESIGN_RULES.md](../../docs/DESIGN_RULES.md) | DOCX / 演示 / 图示 / token / 品牌色硬性约束 |
| [SIZE_DEPTH_MATRIX.md](../../docs/SIZE_DEPTH_MATRIX.md) | 公司文档 S/M/L/XL 深度控制 |
| [ARCHITECTURE.md](../../docs/ARCHITECTURE.md) | Brain -> Router -> Canvas 三层架构 |
| [TEMPLATES.md](../../docs/TEMPLATES.md) | 18 模板（HTML 输出模式） |
| [CONTENT_STRATEGIES.md](../../docs/CONTENT_STRATEGIES.md) | 28 策略（HTML 输出模式） |
| [DEPTH_VISUALIZATION.md](../../docs/DEPTH_VISUALIZATION.md) | 深度可视化规则（HTML 输出模式） |

---

## 传承

本 Skill 源自 [EIP（Explain In Picture）](https://github.com/jasonhnd/eip) 项目 —— 一个 AI 驱动的可视化文档生成 Web 应用（Next.js 16 + React 19 + Tailwind CSS 4），积累了 Engine 1.0 方法论：三阶段管线、可视化模板骨架、内容策略、分类引擎、深度可视化规则和 S/M/L/XL 尺寸控制。

make-doc-skill v4 将这套 Brain -> Router -> Canvas 智能向前推进，并重新瞄准公司文档 —— 正式 Word/PDF 董事会材料、IR/CFO 提案和中日双语交付物 —— 同时把源自 EIP 的 HTML 机制保留为可选输出模式。

---

## 许可证

[Apache License 2.0](../../LICENSE)
