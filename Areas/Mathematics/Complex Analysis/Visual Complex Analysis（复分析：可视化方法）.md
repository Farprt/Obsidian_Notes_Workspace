---
title: "Visual Complex Analysis（复分析：可视化方法）"
type: area-note
area: mathematics
subarea: complex-analysis
status: draft
---
# 1. Geometry and Complex Arithmetic
## 1.1 Introduction
几何解释:即平面上的点（或向量）：应该把$a+ib$这个神秘的东西看成$xy$平面上以 $(a,b)$为坐标的点, 或等价地看成连接原点到此点的向量. 见图 1-1. 这样来看待的平面记作$\mathbb{C}$, 并称为复平面(complex plane).
![[complex-plane.png]]
对两个复数的加法和乘法现在也可以赋予确定的几何意义, 即解释为平面上相应的点（或向量）的几何运算. 
图 1-2a 演示了加法的法则:
**两个复数之和 A + B 由通常向量加法的平行四边形法则给出**[式(1.1)]
$$A+B=(a+i \tilde{a})+(b+i \tilde{b})=(a+b)+i(\tilde{a}+\tilde{b})$$
[式(1.5)]
图 1-2b 画出了不那么明显的乘法法则：
**AB 之长是 A 之长与 B 之长的乘积, AB 的辐角是 A 与 B 的辐角之和**.[式(1.2)]
$$
AB=(a+i \tilde{a})(b+i \tilde{b})=(ab-\tilde{a}\tilde{b})+i(a \tilde{a}+b \tilde{b})
$$
[式(1.6)]
![[complex-sum-and-product-geometry.png]]

一些术语和记号

| Name                            | Meaning                                     |     Notation     |
| ------------------------------- | ------------------------------------------- | :--------------: |
| modulus of $z$                  | length $r$ of $z$                           |     $\|z\|$      |
| argument of $z$（z的辐角）           | angle $\theta$ of $z$                       |     $arg(z)$     |
| real part of $z$                | $x$ coordinate of $z$                       | $\mathrm{Re}(z)$ |
| imaginary part of $z$           | $y$ coordinate of $z$                       | $\mathrm{Im}{z}$ |
| imaginary number                | real multiple of $i$                        |                  |
| real axis                       | set of a real numbers                       |                  |
| imaginary axis                  | set of imaginary numbers                    |                  |
| complex conjugate of $z$（z的复共轭） | reflection of $z$ in the real axis（z对实轴的反射） |    $\bar{z}$     |
![[complex-number-terminology-summary.png]]

用笛卡儿坐标（实部 x 和虚部 y）把复数写成 $z=x+iy$, 只是标记方法之一.当我们处理复数的加法时, 这是很自然的标记, 因为[式(1.5)]说明$A+B$的实部和虚部正是 A 和 B 的实部和虚部分别相加而得.

但是在乘法情况下, 笛卡儿标记法就不再是自然的了, 因为它给出拖沓而且没有启发性的法则[式(1.6)]. 简单得多的几何法则[式(1.2)]使我们看得很清楚, 我们应该用极坐标来标志一个典型的点$z:r=|z|,\theta=arg(z)$. 我们现在可以把$z$写作$z=\angle \theta$而不是$z=x+iy$, 这里符号$\angle$用于提醒我们 $\theta$是 z 的角度.几何乘法法则[式(1.2)]现在就有了简单的形式
$$
(R\angle \phi)(r \angle \theta)=Rr \angle(\phi+\theta)
$$
[式(1.7)]
和笛卡儿标记 x + iy 一样, 一个给定的极坐标标记 r∠θ 就确定了唯一的点, 但是（与笛卡儿标记不同）, 一个给定的点并没有唯一的极坐标标记. 因为任意两个相差 2π 的整数倍的角度表示同样的方向

> [!Example] 练习
> $\mathrm{Re}(z)=\frac{1}{2}(z+\bar{z})$
> $\mathrm{Im}(z)=\frac{1}{2i}(z-\bar{z})$
> $|z|=\sqrt{ x_{2}+y_{2} }$
> $\tan(arg z)=\frac{\mathrm{Im}(z)}{\mathrm{Re}(z)}$
> $\bar{z}z=|z|^2$
> $r\angle\theta=r(\cos \theta+i\sin \theta)$
> $\frac{1}{z}=\frac{1}{r\angle \theta}=\frac{1}{r}\angle-\theta$
> $\frac{R\angle\phi}{r\angle\theta}=\frac{R}{r}\angle(\phi-\theta)$
> $\frac{1}{x+iy}=\frac{x}{x_{2}+y_{2}}-i\frac{y}{x_{2}+y_{2}}$
> $\bar{r\angle\theta}=r\angle(-\theta)$
> $\bar{z_{1}+z_{2}}=\bar{z_{1}}+\bar{z_{2}}$
> $\bar{z_{1}z_{2}}=\bar{z_{1}}\bar{z_{2}}$
> $|z_{1}+z_{2}+\dots+z_{n}|\leq|z_{1}|+|z_{2}|+\dots+|z_{n}|$[式(1.8)]

**从几何上看, 乘以复数 $A=R\angle\phi$ 就是把平面旋转一个角$\phi$, 且放大一个因子 R.**(1.9)
### 1.1.1 符号算数和几何算数的等价性
我们一直在交换地使用符号法则[式(1.5)],[式(1.6)]与几何法则[式(1.1)],[式(1.2)], 现在我们要证明二者等价, 因此这种交换使用是合理的.

我们先证明乘法的符号法则可以由几何法则导出. 为此我们先用一种特别有用的重要方法来重述几何法则[式(1.7)]. 令$z$为$\mathbb{C}$中一般的点并且考虑当用一个固定复数$A=R\angle\phi$去乘它时, 它会变成什么. 

按[式(1.7)],$z$的长度将放大$R$倍, 而$z$的角度将增加一个$\phi$. 现在想象对平面的每一点都同时这样做：
**从几何上看, 乘以复数$A=R\angle\phi$就是把平面旋转一个角$\phi$, 且放大一个因子$R$.**[式(1.9)]

图 1-5 画出了这种变换的效果, 浅色的图形变成了深色的图形.
![[complex-multiplication-distributive-geometry.png]]
用 A 去乘就是把这个平行四边形变成以 O, AB, AC 和 A(B + C) 为顶点的另一个平行四边形. [式(1.6)]由此即可推出.

反过来, 我们现在证明几何法则也可由符号法则导出. 先考虑变换$z\mapsto iz$. 按符号法则, 这意味着$x+iy\mapsto(-y+ix)$, 图 1-6a 表明$iz$就是把$z$逆时针转一个直角. 现在用这个事实来解释$A$为一般复数时, 变换$z\mapsto Az$是什么, , 以$A=4+3i=5\angle\phi$为例,$\phi=\arctan\left( \frac{3}{4} \right)$. 图 1-6b 就是如此. 符号规则表明, 括号可以乘开, 所以我们的变换可以重写为
$$
z\mapsto Az=(4+3i)z=4z+3\left( z旋转 \frac{\pi}{2} \right)
$$
图 1-6c 画出了这些步骤.所以用 5∠φ 去乘就表示把平面旋转一个角度 φ 再按因子 5 放大
![[complex-multiplication-rotation-scaling.png]]

## 1.2 Euler's Formula（欧拉公式）
现在该把 $r\angle \theta$ 换成一个好得多的记号了, 这个记号基于一个奇迹般的公式
$$
e^{i\theta}=\cos \theta+i\sin \theta
$$
(1.10)

正如图 1-7a 所示, 这个公式表明 $e^{i\theta}$ 是单位圆上辐角为 θ 的一点. 我们可以不再把复数写为 $z=r\angle\theta$, 而写为 $z=re^{i\theta}$; 具体说来, 要想达到 z, 必须先取指向 z 的单位向量 eiθ, 然后再把这向量拉长到 z. 这种表示法的好处就在于, 复数乘法的几何法则 (1.7) 现在成了几乎自明的事：
$$
(R e^{i\theta})(r e^{i\theta})=Rre^{i(\theta+\phi)}
$$

![[euler-formula-unit-circle.png]]

欧拉公式的一个简单而重要的结论是：正弦和余弦可以用指数函数构造出来.准确地说, 检查一下图 1-10, 可得
$$
e^{i\theta}+e^{-i\theta}=2\cos \theta, e^{i\theta}-e^{-i\theta}=2i\sin \theta
$$
或者与此等价有
$$
\cos \theta=\frac{e^{i\theta}+e^{-i\theta}}{2},\sin \theta=\frac{e^{i\theta}-e^{-i\theta}}{2i}
$$
![[trigonometric-functions-from-complex-exponentials.png]]

### 1.2.1 一些应用
#### 1.2.1.1 向量
$$
z=x+iy \Longleftrightarrow \vec{z}=\begin{pmatrix}
x \\
y
\end{pmatrix}
$$
虽然点乘和叉乘对任意空间向量都有意义, 但我们下面假设所有向量都在同一平面―――复平面内.

给定两个向量$\vec{a}$和$\vec{b}$, 图 1-20a 帮我们回忆起, 点乘就是一个向量的长乘以另一向量在此向量上的投影：
$$
\vec{a}\vec{b}=|a||b|\cos \theta=\vec{b}\vec{a}
$$
其中 θ 是$\vec{a}$与$\vec{b}$之间的夹角.
![[dot-product-and-cross-product-geometry.png]]

图 1-20b 使我们回忆起叉乘的定义：$\vec{a}\times \vec{b}$垂直于$\vec{a}$和$\vec{b}$所决定的平面, 其长
为$\vec{a},\vec{b}$所张的平行四边形的面积$\mathcal{A}$.

$\vec{a}\times \vec{b}$的定义中包含了一个人为的规定, 叉乘本质上是三维的. 这就提出了一个问题：如果$\vec{a},\vec{b}$被看成了复数, $\vec{a}\times \vec{b}$就**不可能**是复数, 因为它并不位于$\vec{a},\vec{b}$所在的（复）平面$\mathbb{C}$内. 
为了本书所需, 我们将重新定义向量的叉乘是由$\vec{a}$到$\vec{b}$所张的（而不只是$\vec{a}$和$\vec{b}$所张的）平行四边形的（有符号的）面积：
$$
\vec{a}\times \vec{b}=|{a}||{b}|\sin \theta=-(\vec{b}\times \vec{a})
$$
图 1-21 表明, 若有两个复数$a=|{a}|e^{i\theta}$和 $b=|{b}|e^{i{\beta}}$, 则由$a$到$b$的角是$\theta=\beta-\alpha$. 为了看出它们的点乘与叉乘怎样与复数乘法相关, 先考虑用 a 乘$\mathbb{C}$的任一点的净效果. 这就是旋转一个角 −α 再放大 |a| 倍, 如果再看斜边为 b 的有阴影的直角三角形在此变换下的象, 则我们可以立刻看到
$$
\bar{a}b=\vec{a}\vec{b}+i(\vec{a}\times \vec{b})
$$
(1.20)

![[complex-product-dot-cross-components.png]]
当我们把点乘和叉乘说成是 “向量运算” 时, 这意味着它们是几何地加以定义的, 而与坐标轴的任意特定的选取无关. 然而, 一旦选定了笛卡儿坐标系, (1.20) 就很容易用笛卡儿坐标来表示这些运算. 写出$a=x+iy$,$b=x'+iy'$, 则
$$
\bar{a}b=(x-iy)(x'+iy')=(xx'+yy')+i(xy'-x'y)
$$
所以
$$
\begin{pmatrix}
x \\
y
\end{pmatrix}\begin{pmatrix}
x' \\
y'
\end{pmatrix}=xx'+yy',\begin{pmatrix}
x \\
y
\end{pmatrix}\times\begin{pmatrix}
x' \\
y'
\end{pmatrix}=xy'-x'y
$$

# 2. Complex Functions as Transformations
## 2.1 Introduction
一个复函数就是一个规则, 按此规则对每一个复数$z$均指定一个复数$w$为其象$w=f(z)$.为了研究这种函数, 使它可视化是很重要的.

把$z$及其象$w$都看作复平面上的点（也就是一个向量）, 这样 $f$就成了一个**平面的变换**.

有一种约定是把象点$w$画在一个新的$\mathbb{C}$平面上, 称为**象平面**或**$w$平面**. 图2-1 显示了这个约定, 图中画出了变换$z\mapsto w=f(z)=(1+i\sqrt{ 3 })z$（请与第 1 章的图 1-5 比较)
![[complex-function-plane-mapping.png]]

z 的实部和虚部通常记作 x 和 y, 象点 w 的实部和虚部则记作 u 和 v, 所以w = f(z) = u(z) + iv(z), u(z) 和 v(z) 是 z 的实值函数.例如, 在上例中记 z = x + iy, 则有
$$
u(x+iy)=x-\sqrt{ 3 }y, v(x+iy)=\sqrt{ 3 }
$$

