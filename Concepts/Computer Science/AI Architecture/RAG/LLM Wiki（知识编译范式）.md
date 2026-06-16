---
title: "LLM Wiki（知识编译范式）"
type: concept
area: Computer Science
subarea: AI Architecture
topics:
  - knowledge-system
  - rag
  - wiki
status: evergreen
visibility: public
publish_status: cleaned
aliases:
  - LLM Wiki
  - 知识编译范式
---

# LLM Wiki（知识编译范式）

## Definition

LLM Wiki 是一种把知识提前整理成 wiki / concept graph 的范式。它不把所有计算都推迟到提问时，而是把部分结构化整理前置到日常维护过程中。

## Contrast With Runtime RAG

传统 RAG 常在提问时临时检索、拼接、生成。LLM Wiki 更强调平时就维护概念页、关系图和索引入口，让检索时拿到的不是碎片堆，而是已经被整理过的知识结构。

## In Obsidian

Obsidian 的 MOC、概念节点和双链很适合这种范式。RAG 可以定位材料，但长期理解仍应沉淀到人能阅读的 wiki 结构中。

## Related

- [[Retrieval-Augmented Generation（检索增强生成）]]
- [[GraphRAG（图谱增强检索）]]
