---
title: "Cross-Encoder Reranker（交叉编码器重排序）"
type: concept
area: Computer Science
subarea: AI Architecture
topics:
  - rag
  - reranker
  - transformer
status: evergreen
visibility: public
publish_status: cleaned
aliases:
  - Cross-Encoder
  - Cross Encoder Reranker
  - 交叉编码器重排序
---

# Cross-Encoder Reranker（交叉编码器重排序）

## Definition

Cross-Encoder Reranker 把 query 和候选文本拼在一起输入同一个模型，让模型直接判断二者相关性。

## Compared With Bi-Encoder

Bi-Encoder 先分别编码 query 和文档，再比较向量相似度，速度快，适合大规模召回。Cross-Encoder 同时读取 query 和候选片段，速度慢，但相关性判断通常更精细，适合 rerank 阶段。

## In RAG

典型用法是：先召回几十到上百个候选，再用 Cross-Encoder 重排并保留 top-k。

## Related

- [[Rerank（重排序）]]
- [[Hybrid Search（混合检索）]]
