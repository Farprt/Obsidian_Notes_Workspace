---
title: "Reciprocal Rank Fusion（倒数排名融合）"
type: concept
area: Computer Science
subarea: AI Architecture
topics:
  - rag
  - rank-fusion
status: evergreen
visibility: public
publish_status: cleaned
aliases:
  - RRF
  - Reciprocal Rank Fusion
  - 倒数排名融合
---

# Reciprocal Rank Fusion（倒数排名融合）

## Definition

RRF 是一种把多个检索器的排序结果合并的方法。它不直接比较不同检索器的原始分数，而是根据每个结果在各自排序中的名次累加得分。

## Formula

常见形式为：

$$
score(d) = \sum_i \frac{1}{k + rank_i(d)}
$$

其中 $rank_i(d)$ 是文档 $d$ 在第 $i$ 个检索器中的排名，$k$ 是平滑常数。

## Why It Works

不同检索器的分数尺度往往不可比，排名比原始分数更稳定。RRF 因此适合合并 Dense retrieval 和 BM25 这类异构检索器。

## Related

- [[Hybrid Search（混合检索）]]
- [[BM25（Best Matching 25）]]
