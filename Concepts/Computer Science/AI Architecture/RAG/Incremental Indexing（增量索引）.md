---
title: "Incremental Indexing（增量索引）"
type: concept
area: Computer Science
subarea: AI Architecture
topics:
  - rag
  - indexing
  - database
status: evergreen
visibility: public
publish_status: cleaned
aliases:
  - Incremental Indexing
  - 增量索引
---

# Incremental Indexing（增量索引）

## Definition

增量索引只处理发生变化的文件，而不是每次重建整个检索库。常见做法是保存文件哈希、mtime、chunk 数量和 chunk id。

## Why It Matters

个人知识库会持续变化。如果每次修改一篇笔记都全量重建索引，成本会越来越高。增量索引让 RAG 可以跟随笔记更新而不拖慢工作流。

## Failure Case

如果一个文件的 chunk 数减少，但旧 chunk 没有删除，检索库就会留下 orphan chunks（孤儿片段）。因此更新文件时应先删除该文件旧 chunks，再写入新 chunks。

## Related

- [[Retrieval-Augmented Generation（检索增强生成）]]
- [[RAG Evaluation（RAG 评估）]]
