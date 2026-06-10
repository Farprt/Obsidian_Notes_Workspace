---
title: "Convex Optimization"
type: area-note
area: mathematics
subarea: convex-optimization
status: draft
tags:
  - Math
---
Material
[一看就懂！新手如何快速学会【凸优化】，6个小时带你解决机器学习数学最优化问题！NLP自然语言处理从入门到进阶必知必会！！！梯度下降|机器学习|人工智能数学_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV18s4y117BM/?spm_id_from=333.1391.0.0)

# 1. Mathematical optimization

> [!abstract] [[Optimization problem(优化问题)]]
[[Optimization problem(优化问题)]]
# 2. Optimization - Categories
1. **convex vs Non-convex**
convex: 有全局最优解
Non-convex: 无全局最优解（局部最优解）Deep network

算法: Better Local Optimal
Relax: convex problem
假如是小的问题L Brute Force solution		

2. Continuous vc Discrete
3. Constrained vs Non-constrained
4. Smooth vs Non-smooth

# 3. Convex Set
> [!abstract] [[Convex Set（凸集）]]
[[Convex Set（凸集）]]

例子：所有的$R^n$
所有的正数集合$R_{+}^n$
范数$||x||\leq_{1}$
Affine set: 线性方程组式的所有解$Ax=b$
$$证：
\begin{align}
\left\{ \begin{array}
 & Ax=b \\
Ay=b
\end{array} \right. \implies A(\alpha x+(1-\alpha)y)=b
\end{align}
$$
Halfspace: 不等式的所有解$Ax\leq b$

# 4. Convex Funtion

> [!abstract] [[Convex Function(凸函数)]]
[[Convex Function(凸函数)]]

例：
- 线性函数：$f(x)=b^Tx+c$
	证：
$$
\begin{align}
 & \forall x_{1},x_{2}\in domf \\
 & f(x_{1})=b^Tx_{1}+c \\
 & f(x_{2})=b^Tx_{2}+c \\
 & 证：b^T(\theta x_{1}+(1-\theta x_{2}))\leq\theta(b^Tx_{1}+c)+(1-\theta)(b^Tx_{2}+c)
\end{align}
$$
- 二次方函数(quadratic function): $f(x)=\frac{1}{2}x^TAx+b^Tx+c$，对于任意的$A\geq 0$
$$
\begin{align}
 & \frac{ \partial f(x) }{ \partial x }=Ax+b \\
 & 根据矩阵微分规则:\frac{ \partial (x^TAx) }{ \partial x }=(A+A^T)x=2Ax，当A为对称矩阵(A=A^T) \\
 & 二阶偏导数（Hessian矩阵）\frac{ \partial^2 f(x) }{ \partial^2 x }=A\geq 0
\end{align}
$$

> [!abstract] [[Semidefinite Matrix(半正定矩阵)]]
[[Semidefinite Matrix(半正定矩阵)]]

> [!abstract] [[Positive Definite Matrix(正定矩阵)]]
[[Positive Definite Matrix(正定矩阵)]]

> [!abstract] [[Quadratic Form(二次型)]]
[[Quadratic Form(二次型)]]


## 4.1. 凸函数判断方式
### 4.1.1. First Order Convexity Condition一阶导（用的不多）
假设$f:R^n\to R$（定义域在函数f的情况下映射到值域R)是可导的(differentiable)，则$f$为凸函数，当且仅当：$f(y)\geq f(x)+\nabla (x)^T(y-x)$对于任意$x,y\in domf$
![[first-order-convexity-condition.png]]

### 4.1.2. Second Order Convexity Condition二阶导
假设$f:R^n\to R$是二次可导的(twice differentiable)，则$f$为凸函数，当且仅当：
$\nabla^2f(x)>0$
对于任意$x,y\in domf$

## 4.2. 例：
运筹学(operation research) stochastic programming
- LP problem
- inventory optimization
- scheduling problem

### 4.2.1 Transportation Problem
![[transportation-problem-example.png]]
1. Decision Variable
2. Objective: Minimize cost
3. Constraint
4. 判断目标函数的类型(Linear Programming)
5. 寻找Solver

$$
\begin{align}
\left\{ \begin{array}
  \text{minimize:} 5B_{1}+3B_{2}+6B_{3}+7S_{1}+2S_{2}+3S_{3}\\
  \text{s.t(subject to):} \left\{ \begin{array}
  & B_{1}+S_{1}=300 \\
 B_{2}+S_{2}=300 \\
\dots
\end{array} \right.
\end{array} \right. 
\end{align}
$$
矩阵形式：
$$
\begin{align}
\left\{ \begin{array}
  \text{minimize:} a^Tx\\
  \text{s.t:} \left\{ \begin{array} \\
 & Ax=b \\
 & Bx\leq C
\end{array} \right.
\end{array} \right.  \\
a=\begin{bmatrix}
5 \\
3 \\
6 \\
7 \\
2 \\
3
\end{bmatrix} & x=\begin{bmatrix}
B_{1} \\
B_{2} \\
B_{3} \\
S_{1} \\
S_{2} \\
S_{3}
\end{bmatrix} & b=\begin{bmatrix}
300 \\
200 \\
250
\end{bmatrix}\dots
\end{align}
$$

### 4.2.2 portfolio optimization
1. Decisino Varable: $\omega_{1},\dots,\omega_{m}$(权重)
$\omega_{i}$：在股票$i$上投资多少(%)
假设：每支股票的收益服从正态分布$S_{i}$
$$
\begin{align}
&S_{1}\sim N(r_{1},\sigma_{1}^2) \\
&S_{2}\sim N(r_{1},\sigma_{1}^2) \\
&\dots \\
&S_{m}\sim N(r_{m},\sigma_{m}^2) \\
\end{align}
$$
$$
(\omega_{1}S_{1}+\dots+\omega_{m}S_{m})\sim N\left( \sum_{i}^m\omega_{i}r_{i}, \sum_{j}\sum_{i\neq j}\omega_{i}\omega_{j}\sigma_{ij} \right)
$$
$\sum_{j}\sum_{i\neq j}\omega_{i}\omega_{j}\sigma_{ij}$: covarance
2. Objective: 最大化收益+最小化风险
3. Constraints
$$
\begin{align}
 & \text{object: minimize }-\sum^m\omega_{i}r_{i}+\lambda \sum_{j}\sum_{i\neq j}\omega_{i}\omega_{j}\sigma_{ij}  \\
 & \sum^m\omega_{i}r_{i} : \text{收益} \lambda\sum_{j}\sum_{i\neq j}\omega_{i}\omega_{j}\sigma_{ij} : \text{风险} \\
 & \text{vectorization=> minimize } -R^T\omega+\lambda \omega^T\Sigma\omega \\
 & R=\begin{bmatrix}
r_{1} \\
r_{2} \\
\dots \\
r_{m}
\end{bmatrix}, \Sigma=\begin{bmatrix}
0 & \sigma_{1}\sigma_{2} & \dots & \sigma_{1}\sigma_{m} \\
\dots & \dots & \dots & \dots \\
\sigma_{m}\sigma_{1} & \dots & \dots & 0
\end{bmatrix} \\
 & \text{s.t :}\sum_{i}^m\omega_{i}=1
\end{align}
$$
4. 判断类型
convex quadratic programming
5. 使用Solve
### 4.2.3 Set Cover Problem
假设我们有个全集$U$(Universal Set)，以及$m$个子集合$S_{1},\dots,S_{m}$，目标是要找最少的集合，使得集合的union等于$U$

例：$U=\{1,2,3,4,5\}$，$S:\left\{ S_{1}=\left\{ 1,2,3 \right\},S_{2}=\left\{ 2,4 \right\},S_{3}=\left\{ 1,3 \right\},S_{4}=\left\{ 4 \right\},S_{5}=\left\{ 3,4 \right\},S_{6}=\left\{ 4,5 \right\} \right\}$，最少的集合为:$\left\{ 1,2,3 \right\},\left\{ 4,5 \right\}$，集合个数为2

1. Decision Varable: $x_{i}=\left\{ 0,1 \right\}$:集合$S_{i}$是否被选择
2. Object: $\text{minimize }\sum_{i=1}^mx_{i}$
3. constraints: $\sum_{i:e\in S_{i}}x_{i\geq_{1}}, e\in U$
$$
\begin{align}
 & \text{minimize} \sum_{i=1}^ix_{i} \\
 & \text{s.t. } \sum_{i:e\in S}x_{i}\geq1, \forall e\in U \\
 & x_{i}\in \left\{ 0,1 \right\} 
\end{align}
$$
4. 识别函数/判断类型(non convex)
- integer linear programming
5. Solver
- ILP solver
- Relaxation
原来的方法(non convex)$\implies$新的方法(convex)(approximation)
- brute Froce

# 5. Duality