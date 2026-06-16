---
title: "Rerank（重排序）"
type: concept
area: Computer Science
subarea: AI Architecture
topics:
  - rag
  - reranker
status: evergreen
visibility: public
publish_status: cleaned
aliases:
  - Reranking
  - 重排序
  - Reranker
---

# Rerank（重排序）

## Definition

Rerank 是在初始召回之后，对候选结果重新排序的阶段。它通常使用更昂贵但更准确的模型判断 query 和候选片段之间的相关性。

## Intuition

第一阶段检索要“召回尽量多的可能相关内容”，第二阶段重排序再判断“哪些候选最值得放进上下文”。这能在召回率和精度之间取得平衡。

## In 琅嬛

`琅嬛` 的 RAG 基线先通过 Dense + BM25 + RRF 得到候选，再用 [[Cross-Encoder Reranker（交叉编码器重排序）]] 精排。

## Related

- [[Cross-Encoder Reranker（交叉编码器重排序）]]
- [[Hybrid Search（混合检索）]]
