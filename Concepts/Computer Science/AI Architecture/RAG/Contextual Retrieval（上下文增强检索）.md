---
title: "Contextual Retrieval（上下文增强检索）"
type: concept
area: Computer Science
subarea: AI Architecture
topics:
  - rag
  - chunking
  - retrieval
status: evergreen
visibility: public
publish_status: cleaned
aliases:
  - Contextual Retrieval
  - 上下文增强检索
---

# Contextual Retrieval（上下文增强检索）

## Definition

Contextual Retrieval 指在索引 chunk 前，给 chunk 补充来源、标题路径或文档级上下文，使它脱离原文后仍然能表达自身语境。

## Problem

普通 chunking 会把一段文字从文档结构中切出来。片段本身可能有意义，但失去了“来自哪篇文章、哪个章节、哪个实验”的信息，检索和生成都会变得不稳定。

## In Obsidian

Obsidian 笔记天然有标题层级和 frontmatter。把标题路径注入 chunk，可以低成本获得上下文增强，不一定需要额外 LLM 生成 chunk 摘要。

## Related

- [[Heading-Aware Chunking（标题感知分块）]]
- [[Retrieval-Augmented Generation（检索增强生成）]]
