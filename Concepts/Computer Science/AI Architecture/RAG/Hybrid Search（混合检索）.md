---
title: "Hybrid Search（混合检索）"
type: concept
area: Computer Science
subarea: AI Architecture
topics:
  - rag
  - retrieval
  - search
status: evergreen
visibility: public
publish_status: cleaned
aliases:
  - 混合检索
  - Dense Sparse Hybrid Search
---

# Hybrid Search（混合检索）

## Definition

Hybrid Search 指同时使用语义向量检索和关键词检索，再把结果融合起来的一类检索策略。

## Why It Matters

纯向量检索容易漏掉代码名、缩写、文件名和精确术语；纯关键词检索又难以找到语义相近但措辞不同的内容。混合检索把两者合并，通常比单一检索更稳。

## In 琅嬛

`琅嬛` 的 RAG 基线使用 Dense retrieval + [[BM25（Best Matching 25）]]，再通过 [[Reciprocal Rank Fusion（倒数排名融合）]] 合并排序，最后交给 [[Rerank（重排序）]] 精排。

## Related

- [[BM25（Best Matching 25）]]
- [[Reciprocal Rank Fusion（倒数排名融合）]]
- [[Rerank（重排序）]]
