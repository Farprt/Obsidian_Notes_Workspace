---
title: "RAG Security（RAG 安全性）"
type: concept
area: Computer Science
subarea: AI Architecture
topics:
  - rag
  - security
  - privacy
status: evergreen
visibility: public
publish_status: cleaned
aliases:
  - RAG Security
  - RAG 安全性
---

# RAG Security（RAG 安全性）

## Definition

RAG Security 关注检索系统在隐私、权限、提示注入和错误上下文传播上的风险。

## Risks

- 把不该索引的目录纳入检索库；
- 把 raw、draft、密钥、日志、PDF OCR 或私人笔记带入上下文；
- 检索结果中出现恶意指令，agent 未区分“内容”和“指令”；
- public/private 边界不清，导致敏感材料被导出。

## Practical Rule

RAG 检索结果必须被当作“待核对线索”，而不是可直接发布的事实。导出到 public 前，还需要单独做发布边界检查。

## Related

- [[Retrieval-Augmented Generation（检索增强生成）]]
- [[Agentic RAG（Agent 驱动的 RAG）]]
