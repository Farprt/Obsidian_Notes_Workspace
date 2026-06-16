---
title: "Obsidian Wikilink Parsing（Obsidian 双链解析）"
type: concept
area: Computer Science
subarea: AI Architecture
topics:
  - obsidian
  - wikilink
  - rag
status: evergreen
visibility: public
publish_status: cleaned
aliases:
  - Obsidian Wikilink Parsing
  - 双链解析
  - Wikilink Parsing
---

# Obsidian Wikilink Parsing（Obsidian 双链解析）

## Definition

Obsidian 双链解析是把 `［［Note］］`、`［［Note|Alias］］`、`［［Note#Heading］］`、`!［［image.png］］` 等语法拆成可检索文本和结构化链接 metadata 的过程。

## Key Distinction

- `［［Note|Alias］］` 中的 `Alias` 更适合进入向量化文本，因为它是显示给读者的语义。
- `Note` 更适合进入 outlinks metadata，因为它是图谱中的真实目标。

## Why It Matters

如果把双链当普通括号文本，RAG 会丢掉 Obsidian 最重要的结构信息。正确解析双链后，检索结果可以推荐下一步打开的相关笔记。

## Related

- [[GraphRAG（图谱增强检索）]]
- [[Retrieval-Augmented Generation（检索增强生成）]]
