本章，我们来推广隐函数定理（19.6.1），使之能够对 $f\colon E\to \mathbb{R}^{m}$ 成立，通常称为一个**隐函数组**。根据一维隐函数定理的证明过程，我们可以看出，关键在于构造出函数 $F$，证明 $J_{F}(y)$ 可逆，然后应用反函数定理。因此，某种意义上，隐函数定理是反函数定理的一个直接推论。

现在我们对原定理的证明做一定的推广，据此，我们就可以找到那个合适的定理条件。设函数 $F\colon E\to \mathbb{R}^{n}$ 定义为

$$
F(x_{1},\dots,x_{n})=(f_{1},\dots,f_{m},x_{m+1},\dots,x_{n})
$$

其中我们用 $f_{i}$ 代替 $f_{i}(x_{1},\dots,x_{n})$，现在我们写出 $J_{F}(y)$：

$$
J_{F}(y)=\begin{pmatrix}
\dfrac{ \partial f_{1} }{ \partial x_{1} } (y) & \cdots & \dfrac{ \partial f_{1} }{ \partial x_{m} } (y) & \dfrac{ \partial f_{1} }{ \partial x_{m+1} } (y) & \cdots & \dfrac{ \partial f_{1} }{ \partial x_{n} } (y) \\
\vdots &  & \vdots & \vdots &  & \vdots \\
\dfrac{ \partial f_{m} }{ \partial x_{1} } (y) & \cdots & \dfrac{ \partial f_{m} }{ \partial x_{m} } (y) & \dfrac{ \partial f_{m} }{ \partial x_{m+1} } (y) & \cdots & \dfrac{ \partial f_{m} }{ \partial x_{n} } (y) \\
0 & \cdots & 0 & 1 & \cdots & 0 \\
\vdots &  & \vdots & \vdots &  & \vdots \\
0 & \cdots & 0 & 0 & \cdots & 1
\end{pmatrix}
$$

要使 $J_{F}(y)$ 可逆，我们可以考虑它的行列式，根据行展开，我们发现只要左上角 $m\times m$ 的子矩阵的行列式 $\left\lvert  \dfrac{\partial(f_{1},\dots,f_{m})}{\partial(x_{1},\dots,x_{m})}(y) \right\rvert\neq 0$ 即可，这明确了定理的条件，下面我们来看定理的结论。

一维的隐函数定理有如下等式成立：

$$
f(x_{1},\dots,x_{n-1},g)=0, (x_{1},\dots,x_{n-1})\in U
$$

对其做推广，则有

$$
f(g_{1},\dots,g_{m},x_{m+1},\dots,x_{n})=0, (x_{m+1},\dots,x_{n})\in U
$$

将其展开，即

$$
\begin{matrix}
f_{1}(g_{1},\dots,g_{m},x_{m+1},\dots,x_{n})=0 \\
\vdots \\
f_{m}(g_{1},\dots,g_{m},x_{m+1},\dots,x_{n})=0
\end{matrix}
$$

取 $m+1\leq j\leq n$，求偏导则有

$$
\begin{matrix}
\dfrac{ \partial f_{1} }{ \partial x_{j} } (y) + \dfrac{ \partial f_{1} }{ \partial x_{1} } (y) \dfrac{ \partial g_{1} }{ \partial x_{j} } + \dots+\dfrac{ \partial f_{m} }{ \partial x_{m} } (y)\dfrac{ \partial g_{m} }{ \partial x_{j} } =0 \\
\vdots \\
\dfrac{ \partial f_{m} }{ \partial x_{j} } (y) + \dfrac{ \partial f_{m} }{ \partial x_{1} } (y) \dfrac{ \partial g_{1} }{ \partial x_{j} } + \dots+\dfrac{ \partial f_{m} }{ \partial x_{m} } (y)\dfrac{ \partial g_{m} }{ \partial x_{j} } =0
\end{matrix}
$$

对于 $1\leq i\leq m$，根据 Cramer 法则有

$$
\begin{align}
&\dfrac{ \partial g_{i} }{ \partial x_{j} } (y_{m+1},\dots,y_{n}) \\
&= - \left\lvert  \dfrac{\partial(f_{1},\dots,f_{m})}{\partial(x_{1},\dots,x_{m})} (y) \right\rvert ^{-1} \left\lvert  \dfrac{\partial(f_{1},\dots,f_{m})}{\partial(x_{1},\dots,x_{i-1},x_{j},x_{i+1},\dots,x_{m})}(y)  \right\rvert 
\end{align}
$$

这就是推广的隐函数定理，下面我们完整地叙述并证明它。

**定理 1** 隐函数定理（implicit function theorem）

设 $E\subset \mathbb{R}^{n}$ 是开集，$m<n$，函数 $f\colon E\to \mathbb{R}^{m}$ 是 $C^{1}$ 函数，$y=(y_{1},\dots,y_{n})\in E$ 满足 $f(y)=0,\left\lvert  \dfrac{ \partial (f_{1},\dots,f_{m}) }{ \partial (x_{1},\dots,x_{m}) } (y) \right\rvert\neq 0$，那么存在包含 $(y_{m+1},\dots,y_{n})$ 的开集 $U\subset \mathbb{R}^{n-m}$，和包含 $y$ 的开集 $V\subset E$，以及函数 $g\colon U\to \mathbb{R}^{m}$ 使得 $g(y_{m+1},\dots,y_{n})=(y_{1},\dots,y_{m})$，并且

$$
\begin{align}
& \{ x \in V \mid f(x)=0 \} \\
&= \{ (g(x_{m+1},\dots,x_{n}),x_{m+1},\dots,x_{n}) \mid (x_{m+1},\dots,x_{n}) \in U \}
\end{align}
$$

此外，$g$ 在 $(y_{m+1},\dots,y_{n})$ 处可微，并且对任意整数 $1\leq i\leq m$ 和 $m+1\leq j\leq n$ 有

$$
\begin{align}
&\dfrac{ \partial g_{i} }{ \partial x_{j} } (y_{m+1},\dots,y_{n}) \\
&= - \left\lvert  \dfrac{\partial(f_{1},\dots,f_{m})}{\partial(x_{1},\dots,x_{m})} (y) \right\rvert ^{-1} \left\lvert  \dfrac{\partial(f_{1},\dots,f_{m})}{\partial(x_{1},\dots,x_{i-1},x_{j},x_{i+1},\dots,x_{m})}  (y)\right\rvert 
\end{align}
$$

**证明**

定义 $F\colon E\to \mathbb{R}^{n}$ 为

$$
F(x_{1},\dots,x_{n})=(f_{1},\dots,f_{m},x_{m+1},\dots,x_{n})
$$

则 $F(y)=(0,\dots,0,y_{m+1},\dots,y_{n})$，并且 $J_{F}(y)$ 可逆，从而有包含 $y$ 的开集 $V\subset E$ 和包含 $F(y)$ 的开集 $W\subset \mathbb{R}^{n}$ 使得 $F$ 是从 $V$ 到 $W$ 的双射，并且 $F^{-1}$ 在 $F(y)$ 处可微。

设 $F^{-1}(x)=(h_{1}(x),\dots,h_{n}(x))$，则对于 $m+1\leq j\leq n$ 有 $h_{j}(x)=x_{j}$，并且

$$
f(h_{1}(x),\dots,h_{m}(x),x_{m+1},\dots,x_{n})=(x_{1},\dots,x_{m})
$$

令 $U=\{ (x_{m+1},\dots,x_{n}) \mid (0,\dots,0,x_{m+1},\dots,x_{n}) \in W \}$，则 $U$ 是包含 $(y_{m+1},\dots,y_{n})$ 的开集，定义 $g\colon U\to \mathbb{R}^{m}$ 为

$$
g_{i}(x_{m+1},\dots,x_{n})=h_{i}(0,\dots,0,x_{m+1},\dots,x_{n})
$$

下面我们证明

$$
\begin{align}
& \{ x \in V \mid f(x)=0 \} \\
&= \{ (g(x_{m+1},\dots,x_{n}),x_{m+1},\dots,x_{n}) \mid (x_{m+1},\dots,x_{n}) \in U \}
\end{align}
$$

设 $x \in V,f(x)=0$，则 $F(x)=(0,\dots,0,x_{m+1},\dots,x_{n})\in W$，故 $(x_{m+1},\dots,x_{n})\in U$，并且 $F^{-1}(0,\dots,0,x_{m+1},\dots,x_{n})=x$，从而对任意 $1\leq i\leq m$ 有

$$
g_{i}(x_{m+1},\dots,x_{n})=h_{i}(0,\dots,0,x_{m+1},\dots,x_{n})=x_{i}
$$

反之，设 $(x_{m+1},\dots,x_{n})\in U$，则 $(x_{1},\dots,x_{m})=g(x_{m+1},\dots,x_{n})$，从而

$$
\begin{align}
F(x) &=(f(h_{1}(x),\dots,h_{m}(x),x_{m+1},\dots,x_{n}),x_{m+1},\dots,x_{n}) \\
&= (0,\dots,0,x_{m+1},\dots x_{n})
\end{align}
$$

即 $f(x)=0$，并且 $x=F^{-1}(0,\dots,0,x_{m+1},\dots x_{n})\in V$.

$F^{-1}$ 在 $F(y)=(0,\dots,0,y_{m+1},\dots,y_{n})$ 处可微，从而 $h_{i}$ 在 $F(y)$ 处可微，即 $g_{i}$ 在 $(y_{m+1},\dots,y_{n})$ 处可微。此外，$f$ 在 $(g_{1},\dots,g_{m},y_{m+1},\dots,y_{n})$ 处可微，从而对

$$
f(g_{1},\dots,g_{m},x_{m+1},\dots,x_{n})=0
$$

应用链式法则，解方程组即得

$$
\begin{align}
&\dfrac{ \partial g_{i} }{ \partial x_{j} } (y_{m+1},\dots,y_{n}) \\
&= - \left\lvert  \dfrac{\partial(f_{1},\dots,f_{m})}{\partial(x_{1},\dots,x_{m})}(y)  \right\rvert ^{-1} \left\lvert  \dfrac{\partial(f_{1},\dots,f_{m})}{\partial(x_{1},\dots,x_{i-1},x_{j},x_{i+1},\dots,x_{m})} (y) \right\rvert 
\end{align}
$$

事实上，我们可以对条件 $\left\lvert  \dfrac{\partial(f_{1},\dots,f_{m})}{\partial(x_{1},\dots,x_{m})}(y) \right\rvert\neq 0$ 做进一步的放宽。本质上，我们需要的是对于一个特殊的函数 $F$，其 Jacobian 矩阵的行列式不为零，那么我们事实上只需要 $\nabla f_{1}(y),\dots,\nabla f_{m}(y)$ 线性无关即可。根据线性代数的理论，一个矩阵的行秩等于列秩，因此，在矩阵

$$
\begin{pmatrix}
\nabla f_{1}(y) \\
\vdots \\
\nabla f_{m}(y)
\end{pmatrix}=\begin{pmatrix}
\dfrac{ \partial f_{1} }{ \partial x_{1} } (y) & \cdots & \dfrac{ \partial f_{1} }{ \partial x_{m} } (y) & \dfrac{ \partial f_{1} }{ \partial x_{m+1} } (y) & \cdots & \dfrac{ \partial f_{1} }{ \partial x_{n} } (y) \\
\vdots &  & \vdots & \vdots &  & \vdots \\
\dfrac{ \partial f_{m} }{ \partial x_{1} } (y) & \cdots & \dfrac{ \partial f_{m} }{ \partial x_{m} } (y) & \dfrac{ \partial f_{m} }{ \partial x_{m+1} } (y) & \cdots & \dfrac{ \partial f_{m} }{ \partial x_{n} } (y)
\end{pmatrix}
$$

中，必定存在 $m$ 个线性无关的列，将这 $m$ 个变量作为受约束的变量，剩下的证明就是顺理成章的了。从而我们有以下推论：

**定理 2** Lagrange 乘数法

设 $E\subset \mathbb{R}^{n}$ 是开集，$m<n$，函数 $f\colon E\to \mathbb{R},g\colon E\to \mathbb{R}^{m}$ 是 $C^{1}$ 函数，如果 $x^{*}\in E$ 是 $f$ 在约束 $g(x)=0$ 下的极值点，并且 $\nabla g_{1}(x^{*}),\dots,\nabla g_{m}(x^{*})$ 线性无关，那么存在 $\lambda \in \mathbb{R}^{m}$ 使得

$$
\nabla f(x^{*})=\sum_{i=1}^{m} \lambda_{i} \nabla g_{i}(x^{*})
$$

**证明**

不妨设 $\left\lvert  \dfrac{ \partial(g_{1},\dots,g_{m}) }{ \partial(x_{1},\dots,x_{m}) }(x^{*})  \right\rvert\neq 0$，则存在开集 $U\subset \mathbb{R}^{n-m}$ 和函数 $\phi\colon U\to \mathbb{R}^{m}$ 使得

$$
g(\phi_{1},\dots,\phi_{m},x_{m+1},\dots,x_{n})=0,(x_{m+1},\dots,x_{n})\in U
$$

定义函数 $F\colon U\to \mathbb{R}$ 为

$$
F(x_{m+1},\dots,x_{n})=f(\phi_{1},\dots,\phi_{m},x_{m+1},\dots,x_{n})
$$

从而 $(x_{m+1}^{*},\dots,x_{n}^{*})$ 是 $F$ 的无约束极值点，于是对任意 $m+1\leq j\leq n$ 有

$$
\dfrac{ \partial F }{ \partial x_{j} } (x_{m+1}^{*},\dots,x_{n}^{*}) = \dfrac{ \partial f }{ \partial x_{j} } + \dfrac{ \partial f }{ \partial x_{1} } \dfrac{ \partial \phi_{1} }{ \partial x_{j} } +\dots+\dfrac{ \partial f }{ \partial x_{m} } \dfrac{ \partial \phi_{m} }{ \partial x_{j} } =0
$$

即

$$
\begin{align}
\dfrac{ \partial f }{ \partial x_{j} } &= \left\lvert  \dfrac{ \partial (g_{1},\dots,g_{m}) }{ \partial (x_{1},\dots,x_{m}) }   \right\rvert ^{-1} \sum_{i=1}^{m} \dfrac{ \partial f }{ \partial x_{i} } \left\lvert  \dfrac{ \partial (g_{1},\dots,g_{m}) }{ \partial (x_{1},\dots,x_{i-1},x_{j},x_{i+1},\dots,x_{m}) }   \right\rvert  \\
&= \left\lvert  \dfrac{ \partial (g_{1},\dots,g_{m}) }{ \partial (x_{1},\dots,x_{m}) }   \right\rvert ^{-1} \sum_{i=1}^{m} \dfrac{ \partial f }{ \partial x_{i} } \sum_{k=1}^{m} C_{ki} \dfrac{ \partial g_{k} }{ \partial x_{j} } 
\end{align}
$$

其中 $C_{ki}$ 是代数余子式，将系数合并，则我们有

$$
\dfrac{ \partial f }{ \partial x_{j} } (x^{*})=\sum_{k=1}^{m} \lambda_{k}\dfrac{ \partial g_{k} }{ \partial x_{j} } (x^{*}),m+1\leq j\leq n
$$

对于 $1\leq j\leq m$，考虑 $\displaystyle \dfrac{ \partial f }{ \partial x_{j} } -\sum_{k=1}^{m} \lambda_{k} \dfrac{ \partial g_{k} }{ \partial x_{j} }$，由于

$$
\begin{align}
\lambda_{k} &= \left\lvert  \dfrac{ \partial (g_{1},\dots,g_{m}) }{ \partial (x_{1},\dots,x_{m}) }   \right\rvert ^{-1} \sum_{i=1}^{m} C_{ki} \dfrac{ \partial f }{ \partial x_{i} }  \\
&= \left\lvert  \dfrac{ \partial (g_{1},\dots,g_{m}) }{ \partial (x_{1},\dots,x_{m}) }   \right\rvert ^{-1} \left\lvert  \dfrac{ \partial(g_{1},\dots,g_{k-1},f,g_{k+1},\dots,g_{m}) }{ \partial (x_{1},\dots,x_{m}) }   \right\rvert 
\end{align}
$$

这是方程组

$$
\lambda_{1}\dfrac{ \partial g_{1} }{ \partial x_{j} } +\dots+\lambda_{m}\dfrac{ \partial g_{m} }{ \partial x_{j} } =\dfrac{ \partial f }{ \partial x_{j} } ,1\leq j\leq m
$$

的解，故 $\displaystyle \dfrac{ \partial f }{ \partial x_{j} } -\sum_{k=1}^{m} \lambda_{k} \dfrac{ \partial g_{k} }{ \partial x_{j} }=0$，这就完成了证明。

上述定理有一个更简单也更本质的证明方法，它来源于微分几何，涉及流形在某点处切空间的分析，它表明：切空间中的向量都正交于约束函数的梯度 $\nabla g_{i}(x^{*})$，而极值点处 $f$ 的梯度 $\nabla f(x^{*})$ 与切向量正交。也就是说，设

$$
S=\mathrm{span}(\nabla g_{1}(x^{*}),\dots,\nabla g_{m}(x^{*}))
$$

那么对任意切空间中的向量 $t$，有 $t \in S^{\perp}$，而 $t\cdot \nabla f(x^{*})=0$，从而

$$
\nabla f(x^{*})\in(S^{\perp})^{\perp}=S=\mathrm{span}(\nabla g_{1}(x^{*}),\dots,\nabla g_{m}(x^{*}))
$$

这个证明非常简单，但是其中的细节需要我们对微分流形以及切空间有一定的认识后才能填补。

Lagrange 乘数法还有一种广义的扩展，称为 **KKT 条件**，它所处理的是 $f$ 在约束 $g_{1}(x)=0,\dots,g_{m}(x)=0,h_{1}(x)\leq 0,\dots,h_{p}(x)\leq 0$ 下的极值问题，是非线性规划理论的核心内容。KKT 条件在凸优化、机器学习、经济学和工程中均有广泛应用。