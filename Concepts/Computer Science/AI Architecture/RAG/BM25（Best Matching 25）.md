---
title: "BM25（Best Matching 25）"
type: concept
area: Computer Science
subarea: AI Architecture
topics:
  - information-retrieval
  - sparse-retrieval
status: evergreen
visibility: public
publish_status: cleaned
aliases:
  - BM25
  - Best Matching 25
  - 稀疏检索
---

# BM25（Best Matching 25）

## Definition

BM25 是经典稀疏检索算法，根据词频、逆文档频率和文档长度归一化来估计查询与文档的相关性。

## Intuition

如果一个词在当前文档里经常出现、但在整个语料里不常见，它通常更能说明文档和查询相关。BM25 适合处理精确术语、缩写、代码名和文件名。

## In RAG

BM25 常作为向量检索的补充。它不理解语义相似性，但在精确匹配上非常可靠。

## Related

- [[Hybrid Search（混合检索）]]
- [[Reciprocal Rank Fusion（倒数排名融合）]]
