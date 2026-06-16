---
title: "Retrieval-Augmented Generation（检索增强生成）"
type: concept
area: Computer Science
subarea: AI Architecture
topics:
  - rag
  - retrieval
  - llm
status: evergreen
visibility: public
publish_status: cleaned
aliases:
  - RAG
  - Retrieval-Augmented Generation
  - 检索增强生成
---

# Retrieval-Augmented Generation（检索增强生成）

## Definition

RAG 是一种把外部知识检索接入生成模型的架构。模型在回答前先检索相关文档、片段或结构化知识，再基于检索结果生成回答。

## Intuition

RAG 的核心不是“让模型记住更多东西”，而是把需要临时调用的知识放在可更新的外部知识库里。这样知识可以独立维护，模型只负责理解问题、使用上下文和组织回答。

## In 琅嬛

在 `琅嬛` 中，RAG 被设计成 agent 的上下文定位器：它帮助 agent 找到可能相关的 Obsidian 笔记，但正式写入前仍要打开源文件核对。

## Related

- [[Hybrid Search（混合检索）]]
- [[Contextual Retrieval（上下文增强检索）]]
- [[RAG Evaluation（RAG 评估）]]
- [[RAG Security（RAG 安全性）]]
