---
title: "Convex Function(凸函数)"
type: concept
area: mathematics
subarea: convex-function(凸函数).md
status: draft
tags:
  - Math
---
> 函数的定义域$domf$为凸集，对于定义域里任意$x,y$，函数满足
> $f(\theta x+(1-\theta)y)\leq\theta f(x)+(1-\theta)f(y), \theta \in[0,1]$
> ![[convex-function-tangent-lower-bound.png]]
> 函数上任意两点，它的连线上的任意一点在函数上面

>  $$
 \begin{align}
 &f:\mathbb{R}^n\to \mathbb{R} \text{ such that } dom(f)\subseteq \mathbb{R}^n \text{ convex, and} \\
 & f(tx+(1-t)y\leq tf(x)+(1-t)f(y) \text{ for all } 0\leq t\leq_{1} \text{ and all } x,y\in dom(f))
\end{align}
$$