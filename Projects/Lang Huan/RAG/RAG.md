---
title: "RAG"
type: project
area: Computer Science
subarea: AI Architecture
topics:
  - rag
  - retrieval
  - obsidian
status: evergreen
visibility: public
publish_status: cleaned
aliases:
  - Obsidian RAG
  - Local RAG
  - 本地检索增强生成
---

# RAG

这个子项目记录 `琅嬛` 的本地 RAG 工具链：把 Obsidian Markdown 笔记转成可检索的语义与关键词索引，让 agent 在整理笔记前先定位上下文。

## Core Pipeline

```text
Obsidian Markdown
  -> file selection and privacy filtering
  -> frontmatter / wikilink / embed parsing
  -> heading-aware chunking
  -> dense embedding index
  -> BM25 sparse index
  -> hybrid retrieval + RRF
  -> cross-encoder rerank
  -> source-file verification before writing notes
```

## What It Solves

普通全文搜索适合找准确词，但不擅长找语义相近的内容；纯向量检索适合找语义相近的内容，但容易漏掉精确术语、文件名和代码符号。`琅嬛` 的 RAG 基线把两者结合起来：

- 用 Dense retrieval 找语义相关片段；
- 用 BM25 找关键词、缩写、代码名和精确术语；
- 用 RRF 融合两个排序；
- 用 Cross-Encoder reranker 做最终精排。

## Public Boundary

公开版只描述系统设计，不包含：

- 私有 vault 路径；
- API key、`.env`、日志内容或运行缓存；
- 私人阅读材料、raw export、draft extraction；
- PDF、图片原件或长版权文本。

## Maps

- [[RAG Implementation Map]]
- [[RAG Open Questions]]
- [[RAG MOC]]

## Related Concepts

- [[Retrieval-Augmented Generation（检索增强生成）]]
- [[Heading-Aware Chunking（标题感知分块）]]
- [[Obsidian Wikilink Parsing（Obsidian 双链解析）]]
- [[Incremental Indexing（增量索引）]]
- [[Hybrid Search（混合检索）]]
- [[Rerank（重排序）]]
