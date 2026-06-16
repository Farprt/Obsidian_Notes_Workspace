---
title: "RAG Implementation Map"
type: project-map
area: Computer Science
subarea: AI Architecture
topics:
  - rag
  - implementation
  - obsidian
status: evergreen
visibility: public
publish_status: cleaned
---

# RAG Implementation Map

## Module View

```text
config
  -> defines included/excluded note paths
reader
  -> parses Markdown, frontmatter, wikilinks, embeds
chunker
  -> keeps heading context and splits long sections
indexer
  -> computes file hashes and updates vector / sparse indexes
sync command
  -> gives agents a stable post-edit index update entry
query command
  -> dense + sparse retrieval, fusion, rerank, feedback logging
```

## File Selection

索引层只应该读取经过整理的 Markdown 理解层，例如 `Sources`、`Concepts`、`Projects`、`Maps`、`Areas`、`Home`。临时材料、系统规则、图片、PDF、缓存和敏感配置应排除。

这个边界的核心理由是：RAG 只应检索可以被引用和核对的知识材料，而不是把临时草稿、原始摘录或系统配置混进回答上下文。

## Obsidian Parsing

Obsidian 的双链不是普通文本。解析器需要同时保留两类信息：

- **向量化文本**：`［［Note|Alias］］` 应优先保留 `Alias`，因为它是读者实际看到的语义。
- **结构化 metadata**：真实目标 `Note` 应进入 outlinks，方便后续推荐打开相关 notes。

这使得 RAG 不只是“搜片段”，还可以把检索结果接回 Obsidian 图谱。

## Heading-Aware Chunking

Markdown 标题本身就是结构。分块时保留 `# / ## / ### / ####` 标题链，可以让检索结果说明“这段话属于哪个章节”。

这对论文笔记、项目实现笔记和长书笔记都很重要，因为同一个关键词在不同标题下可能代表完全不同的语义。

## Hybrid Retrieval

当前基线采用四阶段检索：

1. Dense vector retrieval：召回语义相近内容。
2. BM25 retrieval：召回精确关键词、缩写、代码符号。
3. RRF fusion：把两套排序合并。
4. Cross-Encoder rerank：对候选片段做最终相关性判断。

## Incremental Indexing

增量索引通过文件哈希判断哪些 Markdown 发生变化。只有变化文件需要重建 chunks；删除文件时，也要删除索引中对应的旧 chunks，避免 orphan chunks（孤儿片段）污染检索。

## Feedback Loop

反馈不应该只停留在主观感觉上。每次查询可以记录：

- query；
- filters；
- result count；
- top score / rerank score；
- agent 是否实际使用结果；
- positive / negative feedback。

长期看，这些数据可以用来做困难样本集、评估集和检索策略调优。

## Design Decisions

- 使用本地 embedding 模型优先保护隐私。
- 用 ChromaDB 这类本地向量库降低部署复杂度。
- 用 BM25 弥补纯向量检索对精确词的弱点。
- 不让 RAG 替代人工维护的 `Home`、`Areas`、`Maps` 和 MOC。
