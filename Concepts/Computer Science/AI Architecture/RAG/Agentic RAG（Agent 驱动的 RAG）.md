---
title: "Agentic RAG（Agent 驱动的 RAG）"
type: concept
area: Computer Science
subarea: AI Architecture
topics:
  - rag
  - agent
  - retrieval-loop
status: evergreen
visibility: public
publish_status: cleaned
aliases:
  - Agentic RAG
  - Agent 驱动的 RAG
---

# Agentic RAG（Agent 驱动的 RAG）

## Definition

Agentic RAG 指让 agent 主动决定是否检索、如何改写查询、是否需要多轮检索，以及何时停止检索的 RAG 形态。

## Key Risk

Agent 不会自动修复错误检索；如果第一轮检索质量很差，多轮 agent 循环可能只是把错误上下文放大。因此 Agentic RAG 需要明确退出条件、质量判断和预算限制。

## In Personal Knowledge Systems

个人知识库场景中，Agentic RAG 更适合用来“定位和核对上下文”，不适合让 agent 在没有源文件验证的情况下自动改写正式笔记。

## Related

- [[RAG 检索策略（When to Retrieve）]]
- [[RAG Evaluation（RAG 评估）]]
- [[RAG Security（RAG 安全性）]]
