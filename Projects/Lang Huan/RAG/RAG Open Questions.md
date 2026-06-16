---
title: "RAG Open Questions"
type: project-map
area: Computer Science
subarea: AI Architecture
topics:
  - rag
  - roadmap
  - evaluation
status: active
visibility: public
publish_status: cleaned
---

# RAG Open Questions

## Completed Baseline

- Hybrid Search（混合检索）已作为默认基线。
- Rerank（重排序）已加入检索链路。
- Contextual Retrieval（上下文增强检索）已通过标题路径与来源前缀实现。
- 显式 feedback loop 已具备基本记录能力。

## Next Questions

### 1. Graph-Enhanced Retrieval

Obsidian 本身有 `wikilink` 图结构。下一步可以研究：检索到一个 chunk 后，是否沿 outlinks 做 1-hop / 2-hop 扩展，并把图邻居作为补充上下文。

相关概念：[[GraphRAG（图谱增强检索）]]、[[HippoRAG（RAG 作为记忆）]]。

### 2. Evaluation Pipeline

没有评测集的 RAG 优化很容易变成凭感觉调参。可行做法是先建立一个小型查询集，记录“哪些结果确实有用”，再用它比较不同检索策略。

相关概念：[[RAG Evaluation（RAG 评估）]]。

### 3. Query Rewriting

用户的提问常常是口语化的，而知识库里的术语可能是英文、缩写或学术表达。可以在检索前生成 2-3 个同义查询，再合并检索结果。

### 4. Auto-Reindex

如果 agent 修改笔记后忘记同步索引，RAG 就会落后于知识库。后续可以通过文件变化监控或 post-edit hook 自动触发增量索引。

### 5. Security Audit

RAG 可能把不该公开的上下文带入回答。需要持续检查：哪些目录可索引，哪些 metadata 可记录，哪些内容绝不应送到外部服务。

相关概念：[[RAG Security（RAG 安全性）]]。

## Engineering Rule

先让普通 RAG 的检索质量稳定，再引入更复杂的 agentic loop。Agent 不会自动修复错误检索；它通常只会放大错误检索带来的问题。
