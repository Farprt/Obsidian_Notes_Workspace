---
title: "Reading Processing Rules（读书整理处理法则）"
type: system
status: active
created: 2026-06-09
---

# Reading Processing Rules（读书整理处理法则）

## Core Idea

这个 Vault 的核心用途是读书笔记整理，但不同类型的书不能用同一套方法处理。

总原则是：**书是来源，概念是网络，问题是复习入口。**

- `Sources/Books/...` 保存一本书或一篇材料的阅读痕迹。
- `Concepts/...` 保存可以跨书、跨课程复用的概念节点。
- `Areas/...` 保存课程、专题、系统学习路径。
- `Inbox/Reading/...` 保存手机端导出的原始划线和临时材料。
- `Maps/...` 保存某一领域的导航和关系图。

不要把每本书都整理成同一种“摘要”。技术书、数学书、专业课、人文社科书的目标不同，笔记形态也不同。

## Universal Workflow

### 1. Mobile Capture

手机阅读时只做低摩擦捕获：

- 划线。
- 必要时加极短符号：`!` 重要，`?` 不懂，`x` 不同意，`↔` 有关联，`◎` 核心概念。
- 不强迫自己写完整理解。
- 不在手机上整理结构。

手机端目标不是完成笔记，而是保存注意力轨迹。

### 2. Raw Import

回到电脑后，把微信读书、PDF、网页或其他来源的划线导入：

```text
Inbox/Reading/<Book Title> - raw.md
```

Raw import 只做清洗：

- 保留书名、作者、章节。
- 保留划线和你原本加的短标记。
- 不急着总结。
- 不急着拆概念。

### 3. Processing

我处理导入材料时，先判断阅读类型，再选择不同处理模式。

处理时优先做：

- 按主题分组。
- 标出可能的概念节点。
- 提出问题来唤回你的理解。
- 区分“原文观点”“你的疑问”“可复用概念”。

不优先做：

- 直接替你写完整书评。
- 把每条划线都总结成一句话。
- 把一本书拆成过多孤立卡片。

### 4. Distillation

只有满足下面至少一条，才从 source note 进入 concept note：

- 在多本书、多门课、多篇文章中反复出现。
- 能解释一类现象。
- 能连接已有知识。
- 你明确想复习或继续追问。
- 它是某个学科的核心术语、定理、模型、方法。

### 5. Review

复习入口不是原文，而是：

- 你当时不懂的问题。
- 你反复划线的主题。
- 已经进入 `Concepts/` 的概念节点。
- `status: to-review` 的 source notes。

## Type A: Mathematics Books

### Goal

数学书的目标不是“知道作者说了什么”，而是形成可操作的数学结构：定义、定理、证明、例子、反例、题目。

### Mobile Capture

手机端只适合捕获：

- 定义。
- 定理陈述。
- 直观解释。
- 关键图像。
- 不懂的证明步骤。

不要在手机上硬写证明理解。数学思考需要纸笔或电脑。

### Processing Shape

数学 source note 应该整理成：

```text
## Chapter / Section

### Definitions

### Theorems

### Proof Ideas

### Examples

### Exercises / Problems

### Confusions
```

数学 concept note 应该更短、更硬：

```text
# Concept Name（中文名）

## Definition

## Intuition

## Key Theorems

## Examples

## Common Mistakes

## Links
```

### Graph Rule

数学图谱以概念和定理为节点，不以章节为中心。

好的节点：

- `Complex Plane（复平面）`
- `Cauchy-Riemann Equations（柯西-黎曼方程）`
- `Convex Set（凸集）`

不建议作为长期节点：

- `Chapter 1 Notes`
- `第 3 节读书笔记`

## Type B: Computer Science And Programming Books

### Goal

计算机书的目标是建立可实现、可调试、可迁移的模型。

### Mobile Capture

手机端捕获：

- 算法思想。
- 数据结构不变量。
- 复杂度结论。
- API 或系统设计原则。
- 反常识的工程经验。

### Processing Shape

CS source note 应该整理成：

```text
## Problem / Motivation

## Model

## Algorithm / Mechanism

## Invariants

## Complexity

## Implementation Notes

## Failure Cases
```

CS concept note 应该强调：

- 什么时候用。
- 为什么正确。
- 复杂度是什么。
- 容易错在哪里。
- 有没有代码或伪代码。

### Graph Rule

CS 图谱以“机制”和“问题类型”为中心。

好的节点：

- `Segment Tree（线段树）`
- `Dynamic Programming（动态规划）`
- `Finite-State Machine（有限状态机）`
- `Rate Monotonic Scheduling（速率单调调度）`

不要让每个代码片段都单独成为节点；代码应服务概念。

## Type C: Communications And Engineering Course Books

### Goal

通信和专业课书的目标是把物理现象、数学模型、系统假设和工程结论对应起来。

### Mobile Capture

手机端捕获：

- 模型假设。
- 公式和变量含义。
- 图像。
- 物理直觉。
- 工程限制。
- 结论适用条件。

### Processing Shape

专业课 source note 应该整理成：

```text
## Phenomenon

## System Model

## Assumptions

## Parameters

## Equations

## Physical Intuition

## Engineering Implications

## Figures
```

专业课 concept note 应该区分：

- 这个概念描述什么现象。
- 用什么模型刻画。
- 公式中的变量是什么。
- 假设条件是什么。
- 和其他概念如何连接。

### Graph Rule

通信图谱以“现象 -> 模型 -> 参数 -> 结论”为主线。

好的节点：

- `Rayleigh Fading（瑞利衰落）`
- `Doppler Spectrum（多普勒谱）`
- `Coherence Bandwidth（相干带宽）`
- `Wireless Channel（无线信道）`

图片只作为资产，不作为图谱中心。图片名用英文 kebab-case，解释放在笔记正文中。

## Type D: Economics And Social Science Books

### Goal

经济和社科书通常介于技术书和人文书之间。它们有模型、概念、因果解释，也有价值判断和历史材料。

目标不是背观点，而是识别：作者用什么模型解释什么现象。

### Mobile Capture

手机端捕获：

- 作者的核心判断。
- 因果链条。
- 概念定义。
- 统计或案例证据。
- 你不确定或不同意的地方。

### Processing Shape

社科 source note 应该整理成：

```text
## Main Question

## Author Claims

## Evidence

## Mechanism

## Assumptions

## Tensions / Objections

## My Questions
```

社科 concept note 应该强调：

- 这个概念解释什么。
- 它依赖什么假设。
- 有哪些反例或争议。
- 它和哪些历史、政治、经济现象相连。

### Graph Rule

社科图谱以解释框架为中心，而不是以书名为中心。

好的节点：

- `State Capacity（国家能力）`
- `Bureaucracy（官僚制）`
- `Incentive（激励）`
- `Legitimacy（合法性）`
- `Institution（制度）`

## Type E: Humanities, History, Politics, And General Reading

### Goal

人文社科、历史、政治和杂读不应该被强迫整理成技术摘要。

这类阅读更重要的是保留：

- 你被什么触动。
- 你对某个判断的迟疑。
- 你看到的结构性矛盾。
- 你和已有经验之间的连接。

### Mobile Capture

手机端只划线即可。可以加很短的注意力标记：

```text
! 重要
? 不懂
x 不同意
↔ 联想到别的书
◎ 概念
```

如果写文字，只写词，不写完整段落：

```text
财政 / 改革者困境 / 皇权
合法性 / 精英 / 官僚体系
```

### Processing Shape

人文 source note 不追求完整摘要，建议整理成：

```text
## Reading Trace

### Repeated Motifs

### Strong Claims

### Scenes / Examples

### Tensions

### Questions I Still Care About

### Possible Concept Links
```

其中 `Reading Trace` 可以保留原始划线顺序，因为这类阅读常常需要保留当时的阅读现场。

### Graph Rule

人文阅读不要把每个章节都拆成概念。只有反复出现、有解释力的问题进入 `Concepts/`。

好的节点：

- `Reformer's Dilemma（改革者困境）`
- `Political Legitimacy（政治合法性）`
- `Historical Contingency（历史偶然性）`
- `Elite Circulation（精英循环）`

可以保留中文书名作为 source note 文件名，但概念节点尽量使用中英双语，方便以后跨中文书和英文材料连接。

## Processing Modes

以后处理一本书前，先给它一个 `reading_mode`：

```yaml
reading_mode: mathematics
reading_mode: computer-science
reading_mode: communications
reading_mode: social-science
reading_mode: humanities
reading_mode: casual
```

推荐 source note frontmatter：

```yaml
title: "Book Title"
type: source
source_type: book
reading_mode: humanities
status: raw
area: Humanities
topics:
  - legitimacy
  - bureaucracy
```

状态含义：

- `raw`: 只是导入原始划线。
- `processing`: 正在整理主题和问题。
- `to-review`: 已有问题或概念，等待复习。
- `evergreen`: 已沉淀成稳定 source note 或 concept note。

## When I Process Your Highlights

当你把划线交给我时，我应先做判断，而不是直接总结。

我会先问或判断：

1. 这本书属于哪种 `reading_mode`？
2. 你需要掌握它，还是只想保留触发过你的想法？
3. 哪些划线值得进入概念图谱？
4. 哪些内容只应留在 source note 中？
5. 是否需要我提问题来唤回你的理解？

默认处理方式：

- 数学：定义、定理、证明、例题、问题。
- CS：模型、算法、不变量、复杂度、实现陷阱。
- 通信：现象、模型、公式、参数、假设、工程意义。
- 经济/社科：问题、主张、证据、机制、反驳。
- 人文/历史/政治：主题、张力、场景、问题、概念链接。

## Anti-Rules

不要做这些事：

- 不要把所有书都整理成统一摘要模板。
- 不要把每条划线都变成永久笔记。
- 不要为了图谱好看而制造大量空概念。
- 不要在手机端强迫自己写完整理解。
- 不要让 AI 直接替代你的判断。
- 不要把书名节点当作知识网络中心。

应该做这些事：

- 用最小动作保存阅读现场。
- 回电脑后再整理结构。
- 让 source note 保留材料，让 concept note 负责连接。
- 对技术书追求可操作，对人文书保留问题感。
- 用中英双语概念名连接中文阅读和英文学习。
