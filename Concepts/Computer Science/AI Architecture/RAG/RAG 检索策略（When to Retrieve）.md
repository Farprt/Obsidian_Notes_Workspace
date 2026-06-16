---
title: "RAG 检索策略（When to Retrieve）"
type: concept
area: Computer Science
subarea: AI Architecture
topics:
  - rag
  - retrieval-policy
  - agent
status: evergreen
visibility: public
publish_status: cleaned
aliases:
  - When to Retrieve
  - 检索策略
---

# RAG 检索策略（When to Retrieve）

## Definition

RAG 检索策略回答一个问题：什么时候应该检索，什么时候不应该检索。

## Retrieve When

- 问题跨多个笔记或项目；
- 需要找到原始来源、实现证据或概念节点；
- 当前上下文不足以判断；
- 需要检查同一术语在不同文件中的用法。

## Do Not Retrieve When

- 用户只问当前打开文件中的局部问题；
- 答案是稳定的通用知识，且不会影响正式笔记；
- 检索可能引入大量无关上下文。

## Related

- [[Agentic RAG（Agent 驱动的 RAG）]]
- [[RAG Evaluation（RAG 评估）]]
