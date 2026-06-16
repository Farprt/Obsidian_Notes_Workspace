---
title: "GraphRAG（图谱增强检索）"
type: concept
area: Computer Science
subarea: AI Architecture
topics:
  - rag
  - knowledge-graph
  - obsidian
status: evergreen
visibility: public
publish_status: cleaned
aliases:
  - GraphRAG
  - 图谱增强检索
---

# GraphRAG（图谱增强检索）

## Definition

GraphRAG 是把图结构纳入 RAG 的方法。它不仅检索文本相似片段，也利用实体、概念、文档链接或知识图谱关系扩展上下文。

## In Obsidian

Obsidian 的双链、backlinks 和 MOC 天然形成图结构。检索到一个笔记片段后，可以沿 outlinks 找到相邻概念、项目证据和来源笔记。

## Design Question

图扩展不能无限展开。需要控制 hop 数、边类型和排序权重，否则会把大量弱相关内容塞进上下文。

## Related

- [[Obsidian Wikilink Parsing（Obsidian 双链解析）]]
- [[HippoRAG（RAG 作为记忆）]]
- [[RAG Evaluation（RAG 评估）]]
