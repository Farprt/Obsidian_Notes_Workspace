---
title: "RAG Evaluation（RAG 评估）"
type: concept
area: Computer Science
subarea: AI Architecture
topics:
  - rag
  - evaluation
  - feedback
status: evergreen
visibility: public
publish_status: cleaned
aliases:
  - RAG Evaluation
  - RAG 评估
---

# RAG Evaluation（RAG 评估）

## Definition

RAG Evaluation 是评估检索结果、上下文质量和最终回答质量的一组方法。它关注的不只是生成答案是否流畅，而是检索证据是否足够、是否相关、是否支持回答。

## Useful Signals

- top-k 结果是否包含正确来源；
- agent 是否实际打开并使用了结果；
- rerank score 是否持续偏低；
- 用户或 agent 是否标记 positive / negative feedback；
- 修改检索策略后，同一批查询结果是否变好。

## Practical Baseline

先建立一个小型查询集，人工判断哪些结果有用。这个数据集不需要很大，但必须稳定，否则 RAG 优化只能靠主观感觉。

## Related

- [[Hybrid Search（混合检索）]]
- [[Rerank（重排序）]]
- [[Agentic RAG（Agent 驱动的 RAG）]]
