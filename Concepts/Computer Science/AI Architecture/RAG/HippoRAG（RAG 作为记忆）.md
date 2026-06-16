---
title: "HippoRAG（RAG 作为记忆）"
type: concept
area: Computer Science
subarea: AI Architecture
topics:
  - rag
  - memory
  - graph-retrieval
status: evergreen
visibility: public
publish_status: cleaned
aliases:
  - HippoRAG
  - RAG 作为记忆
---

# HippoRAG（RAG 作为记忆）

## Definition

HippoRAG 可以理解为把 RAG 进一步看作长期记忆系统：不仅做相似文本检索，还尝试通过图结构、关联路径和记忆组织方式支持多跳回忆。

## Intuition

人查笔记时常常不是只搜一个关键词，而是沿着概念、来源、项目和问题链路逐步回忆。HippoRAG 类方法强调这种“沿关系找上下文”的能力。

## Related

- [[GraphRAG（图谱增强检索）]]
- [[Obsidian Wikilink Parsing（Obsidian 双链解析）]]
