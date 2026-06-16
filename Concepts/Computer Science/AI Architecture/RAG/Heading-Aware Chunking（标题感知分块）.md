---
title: "Heading-Aware Chunking（标题感知分块）"
type: concept
area: Computer Science
subarea: AI Architecture
topics:
  - rag
  - chunking
  - markdown
status: evergreen
visibility: public
publish_status: cleaned
aliases:
  - Heading-Aware Chunking
  - Markdown Header Chunking
  - 标题感知分块
---

# Heading-Aware Chunking（标题感知分块）

## Definition

Heading-aware chunking 是按 Markdown 标题结构切分文本的策略。它优先保留章节边界，而不是按固定字数硬切。

## Why It Matters

知识笔记通常已经用标题表达逻辑结构。按标题切分可以避免把实验设计、结论、代码解释和开放问题混在同一个 chunk 里。

## Common Shape

```text
# h1
  ## h2
    ### h3
      chunk text with heading path
```

如果某个标题块仍然过长，再做二次递归切分。

## Related

- [[Contextual Retrieval（上下文增强检索）]]
- [[Retrieval-Augmented Generation（检索增强生成）]]
