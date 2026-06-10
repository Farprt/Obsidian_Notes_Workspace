---
title: "Optimization problem(优化问题)"
type: area-note
area: mathematics
subarea: convex-optimization
status: draft
---
> $$
\begin{align}
 & min_{x\in D} f(x) \\
 & \text{subject to } g_{i}(x)\leq_{0}, i=1,\dots, m \\
 & h_{j}(x)=0,j=1,\dots,r \\
 & \text{ This is a convex optimization problem provided the functions} \\
 & f \text{ and } g_{i},\dots, m \text{ are convex, and} h_{j}, j=1,\dots,p \text{ are affine:} \\
 & h_{j}(x)=a_{j}^T x+b_{j}, j=1,\dots,p
\end{align}
$$

> A mathematical optimization problem, or just optimization problem, has the form
>$$
\begin{align}
 & \text{minimize} & f_{0}(x) \\
 & \text{subject to} & f_{i}(x)\leq b_{i}, & i=1,\dots,m. \\
 &  & g_{j}(x)=0, & j=1,\dots,p.
\end{align}
>$$
>x: 定义域
>feasible region: 满足条件的x的范围
>feasible solution: 可行解
>optimal solution