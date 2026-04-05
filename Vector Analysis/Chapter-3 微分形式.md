在微积分中，我们学过 $\mathbb{R}^{3}$ 上的向量代数。在这其中，我们引入了标量场与向量场的概念，以及它们的运算，也就是梯度、散度与旋度：

$$
\begin{gather}
\mathrm{grad}\ F=\nabla F, \quad \mathrm{div}\ F=\nabla\cdot F, \quad \mathrm{curl}\ F=\nabla \times F
\end{gather}
$$

并且其主要定理以 Green, Gauss, 以及 Stokes 进行命名。

类似地，在本章中，我们将应用上一章节给出的张量代数，在空间与流形上定义所谓的“张量场”。具体来说，是一个交错张量场，称为一个“微分形式”。此外，我们还将定义微分形式上的一种运算，称为“微分算子” $\mathrm{d}$，它是运算 $\mathrm{grad},\mathrm{div},\mathrm{curl}$ 的扩展。最后，在下一章节，我们将结合上面的一切来证明广义 Stokes 公式，它是一个关于微分形式的积分的一般定理，包含了 Green 公式、Gauss 公式与 Stokes 公式作为特例。

# Section 1: 切向量与微分形式

**定义 3.1.1** 切向量（tangent vector），切空间（tangent space）

设 $x \in \mathbb{R}^{n}$，我们定义 $x$ 处 $\mathbb{R}^{n}$ 的**切向量**为有序对 $(x;v)$，其中 $v \in \mathbb{R}^{n}$. $x$ 处 $\mathbb{R}^{n}$ 的所有切向量构成了一个向量空间，如果我们定义

$$
\begin{gather}
(x;v)+(x;w)=(x;v+w) \\
c(x;v)=(x;cv)
\end{gather}
$$

它称为 $x$ 处 $\mathbb{R}^{n}$ 的**切空间**，记作 $\mathcal{T}_{x}(\mathbb{R}^{n})$.

在上述定义中，尽管 $x$ 和 $v$ 都属于 $\mathbb{R}^{n}$，但它们所扮演的角色是不同的。我们通常将 $x$ 视为度量空间 $\mathbb{R}^{n}$ 中的元素，并用一个点来表示它；而 $v$ 则被视为向量空间 $\mathbb{R}^{n}$ 中的元素，并用一个箭头来表示它。一个切向量 $(x;v)$ 则通常用起点在 $x$ 处的箭头表示，所有这样的箭头构成的集合就是切空间 $\mathcal{T}_{x}(\mathbb{R}^{n})$，显然，它就等于集合 $\{ x \}\times \mathbb{R}^{n}$.

**定义 3.1.2** 速度向量（velocity vector）

设 $(a,b)$ 是 $\mathbb{R}$ 上的开区间，$\gamma\colon(a,b)\to \mathbb{R}^{n}$ 是一个 $C^{r}$ 函数。我们定义 $\gamma$ 在参数 $t$ 处的**速度向量**为 $(\gamma(t); \gamma'(t))$.

这一向量可以表示为一个起点为 $p=\gamma(t)$ 的箭头，如图所示：

![](3-1.png)

“速度”一词则来源于物理学。如果

$$
\begin{gather}
\gamma(t)=x(t)e_{1}+y(t)e_{2}+z(t)e_{3}
\end{gather}
$$

是 $\mathbb{R}^{3}$ 中的一条参数曲线（也称为“轨迹”），那么 $\gamma$ 的速度向量就定义为

$$
\begin{gather}
\gamma'(t)=\dfrac{\mathrm{d} x}{\mathrm{d} t} e_{1}+\dfrac{\mathrm{d} y}{\mathrm{d} t}e_{2}+\dfrac{\mathrm{d} z}{\mathrm{d} t} e_{3}
\end{gather}
$$

更一般地，我们给出以下定义：

**定义 3.1.3**

设 $A$ 是 $\mathbb{R}^{k}$ 或 $\mathbb{H}^{k}$ 中的开集，$\alpha\colon A\to \mathbb{R}^{n}$ 是 $C^{r}$ 函数，令 $x \in A, p=\alpha(x)$，我们定义线性映射

$$
\begin{gather}
\alpha_{*}\colon \mathcal{T}_{x}(\mathbb{R}^{k}) \to \mathcal{T}_{p}(\mathbb{R}^{n})
\end{gather}
$$

为

$$
\begin{gather}
\alpha_{*}(x;v)=(p; \alpha'(x)v)
\end{gather}
$$

它被称为由可微函数 $\alpha$ **诱导的**映射。

给定 $(x;v)$，链式法则表明，向量 $\alpha_{*}(x;v)$ 事实上是参数曲线 $\gamma(t)=\alpha(x+tv)$ 在参数 $t=0$ 处的速度向量，如图所示：

![](3-2.png)

**引理 3.1.4**

设 $A$ 是 $\mathbb{R}^{k}$ 或 $\mathbb{H}^{k}$ 中的开集，$\alpha\colon A\to \mathbb{R}^{m}$ 是 $C^{r}$ 函数，设 $B$ 是 $\mathbb{R}^{m}$ 或 $\mathbb{H}^{m}$ 中包含 $\alpha[A]$ 的开集，$\beta\colon B\to \mathbb{R}^{n}$ 是 $C^{r}$ 函数，则

$$
\begin{gather}
(\beta \circ\alpha)_{*}=\beta_{*}\circ\alpha_{*}
\end{gather}
$$

**证明**

上述公式只是链式法则。令 $y=\alpha(x),z=\beta(y)$，则有

$$
\begin{align}
(\beta \circ\alpha)_{*}(x;v) &= ((\beta \circ\alpha)(x); (\beta \circ\alpha)'(x)v) \\
&=(\beta(y); \beta'(y) \alpha'(x)v) \\
&=\beta_{*}(\alpha(x); \alpha'(x)v) \\
&=\beta_{*}(\alpha_{*}(x;v))
\end{align}
$$

即证。

这些映射以及它们诱导的映射之间的关系由以下的交换图给出：

![](3-3.png)

**定义 3.1.5** 切向量场（tangent vector field）

设 $A$ 是 $\mathbb{R}^{k}$ 中的开集，$A$ 上的一个**切向量场**定义为一个连续函数 $F\colon A\to \mathbb{R}^{n}\times \mathbb{R}^{n}$ 使得 $F(x)\in \mathcal{T}_{x}(\mathbb{R}^{n})$ 对任意 $x \in A$ 成立。则 $F$ 具有形式 $F(x)=(x;f(x))$，其中 $f\colon A\to \mathbb{R}^{n}$. 如果 $F$ 是 $C^{r}$ 函数，那么我们就称其为一个 $C^{r}$ 切向量场。

现在我们定义流形上的切向量场，它是我们研究的重点。

**定义 3.1.6**

设 $M$ 是 $\mathbb{R}^{n}$ 中 $C^{r}$ 连续的 $k$-流形，如果 $p \in M$，取 $p$ 处的坐标卡 $\alpha\colon U\to V$，其中 $U$ 在 $\mathbb{R}^{k}$ 或 $\mathbb{H}^{k}$ 中开。令 $x \in U$ 满足 $\alpha(x)=p$，所有具有形式 $\alpha_{*}(x;v)$，其中 $v \in \mathbb{R}^{k}$ 的向量构成的集合称为 $p$ 处 $M$ 的切空间，记作 $\mathcal{T}_{p}(M)$. 换句话说，我们有

$$
\begin{gather}
\mathcal{T}_{p}(M)=\alpha_{*}[\mathcal{T}_{x}(\mathbb{R}^{k})]
\end{gather}
$$

不难证明 $\mathcal{T}_{p}(M)$ 是 $\mathcal{T}_{p}(\mathbb{R}^{n})$ 的一个子空间，并且与 $\alpha$ 的选取无关。事实上，由于 $\mathbb{R}^{k}$ 由标准基 $e_{1},\dots,e_{k}$ 张成，$\mathcal{T}_{p}(M)$ 由向量

$$
\begin{gather}
(p; \alpha'(x)e_{j})=\left( p; \dfrac{ \partial \alpha }{ \partial x_{j} } (x) \right)
\end{gather}
$$

张成，并且 $J_{\alpha}$ 的秩为 $k$，因此上述向量是线性无关的，从而构成了 $\mathcal{T}_{p}(M)$ 的一个基。一些典型例子如下图所示：

![](3-4.png)

我们将所有 $\mathcal{T}_{p}(M)\ (p \in M)$ 的并集记作 $\mathcal{T}(M)$，称为 $M$ 的**切丛**（tangent bundle）。$M$ 上的一个**切向量场**是一个连续函数 $F\colon M\to \mathcal{T}(M)$ 使得 $F(p)\in \mathcal{T}_{p}(M)$ 对任意 $p \in M$ 成立。

现在我们给出本节最重要的一个定义。

**定义 3.1.7** 张量场（tensor field），微分形式（differential form）

设 $A$ 是 $\mathbb{R}^{n}$ 中的开集，$A$ 上的一个 $k$-**张量场**定义为一个函数 $\omega$，其将每个 $x \in A$ 映射为向量空间 $\mathcal{T}_{x}(\mathbb{R}^{n})$ 上的一个 $k$-张量，即

$$
\begin{gather}
\omega(x)\in T^{k}(\mathcal{T}_{x}(\mathbb{R}^{n}))
\end{gather}
$$

对任意 $x \in A$ 成立。因此 $\omega(x)$ 将 $\mathcal{T}_{x}(\mathbb{R}^{n})$ 中的 $k$-元组映射为实数，我们用

$$
\begin{gather}
\omega(x)((x;v_{1}),\dots,(x;v_{k}))
\end{gather}
$$

来表示 $\omega(x)$ 在给定 $k$-元组上的值。我们要求 $\omega$ 作为以 $(x,v_{1},\dots,v_{k})$ 为自变量的函数是连续的；如果 $\omega$ 是 $C^{r}$ 连续的，我们就称 $\omega$ 是一个 $C^{r}$ 张量场。如果对任意 $x \in A$，$\omega(x)$ 是一个交错 $k$-张量，那么 $\omega$ 就称为 $A$ 上的一个 $k$ **阶微分形式**，简称 $k$-**形式**。

更一般地说，如果 $M$ 是 $\mathbb{R}^{n}$ 上的流形，那么我们定义 $M$ 上的 $k$-张量场是一个函数 $\omega$，其将 $p \in M$ 映射为 $\mathcal{T}_{p}(M)$ 上的 $k$-张量。如果对任意 $p \in M$，$\omega(p)$ 是交错的，那么我们就称 $\omega$ 是 $M$ 上的 $k$-形式。

**定义 3.1.8** 基本形式（elementary form）

设 $e_{1},\dots,e_{n}$ 是 $\mathbb{R}^{n}$ 上的标准基，我们称 $(x;e_{1}),\dots,(x;e_{n})$ 为 $\mathcal{T}_{x}(\mathbb{R}^{n})$ 上的标准基。我们在 $\mathbb{R}^{n}$ 上定义 $1$-形式 $\widetilde{\phi}_{i}$ 如下：

$$
\begin{gather}
\widetilde{\phi}_{i}(x)(x;e_{j})=\begin{cases}
1 & , i=j \\
0 & , i\neq j
\end{cases}
\end{gather}
$$

形式 $\widetilde{\phi}_{1},\dots,\widetilde{\phi}_{n}$ 称为 $\mathbb{R}^{n}$ 上的**基本** $1$-**形式**。进一步，给定 $[n]$ 上的升序 $k$-元组 $I=(i_{1},\dots,i_{k})$，我们定义 $\mathbb{R}^{n}$ 上的 $k$-形式 $\widetilde{\psi}_{I}$ 如下：

$$
\begin{gather}
\widetilde{\psi}_{I}=\widetilde{\phi}_{i_{1}}\land\dots \land \widetilde{\phi}_{i_{k}}
\end{gather}
$$

形式 $\widetilde{\psi}_{I}$ 称为 $\mathbb{R}^{n}$ 上的**基本** $k$-**形式**。

注意到对任意 $x$，$1$-张量 $\widetilde{\phi}_{i_{1}}(x),\dots,\widetilde{\phi}_{i_{k}}(x)$ 构成了 $T^{1}(\mathcal{T}_{x}(\mathbb{R}^{n}))$ 上的一个基，它是 $\mathcal{T}_{x}(\mathbb{R}^{n})$ 上标准基的对偶，并且 $k$-张量 $\widetilde{\psi}_{I}(x)$ 就是与其对应的基本交错张量。

此外，对于基本形式，我们还有计算公式

$$
\begin{gather}
\widetilde{\phi}_{i}(x)(x;v)=v_{i} \\
\widetilde{\psi}_{I}(x)((x;v_{1}),\dots,(x;v_{k}))=\det X_{I}
\end{gather}
$$

其中 $X$ 为矩阵 $[v_{1},\dots,v_{k}]$. 这表明，$\widetilde{\phi}_{i}$ 和 $\widetilde{\psi}_{I}$ 均是 $C^{\infty}$ 连续的。

如果 $\omega$ 是开集 $A$ 上的 $k$-形式，给定 $x \in A$，$k$-张量 $\omega(x)$ 可以唯一地写成如下形式：

$$
\begin{gather}
\omega(x)=\sum_{[I]} b_{I}(x)\widetilde{\psi}_{I}(x)
\end{gather}
$$

其中 $b_{I}(x)$ 是一个标量函数。这些函数称为 $\omega$ 对应于基本形式的分量。

**引理 3.1.9**

设 $\omega$ 是开集 $A\subset \mathbb{R}^{n}$ 上的 $k$-形式，则 $\omega$ 是 $C^{r}$ 连续的当且仅当其分量 $b_{I}$ 是 $C^{r}$ 连续的。

**证明**

给定 $\omega$，我们将其写成基本形式的线性组合：

$$
\begin{gather}
\omega=\sum_{[I]} b_{I} \widetilde{\psi}_{I}
\end{gather}
$$

函数 $\widetilde{\psi}_{I}$ 是 $C^{\infty}$ 连续的，因此，如果 $b_{I}$ 是 $C^{r}$ 连续的，那么 $\omega$ 也是。反之，如果 $\omega$ 是 $C^{r}$ 连续的，那么给定升序 $k$-元组 $J$，函数

$$
\begin{gather}
b_{J}(x)=\omega(x)((x;e_{j_{1}}),\dots,(x;e_{j_{k}}))
\end{gather}
$$

作为以 $x$ 为自变量的函数是 $C^{r}$ 连续的，即证。

**引理 3.1.10**

设 $\omega$ 和 $\eta$ 是开集 $A\subset \mathbb{R}^{n}$ 上的 $k$-形式，$\theta$ 是 $A$ 上的 $\ell$-形式，如果 $\omega,\eta,\theta$ 都是 $C^{r}$ 连续的，那么 $a\omega+b \eta$ 和 $\omega \land\theta$ 也是 $C^{r}$ 连续的。

**证明**

显然 $a\omega+b \eta$ 是 $C^{r}$ 连续的，因为它是 $C^{r}$ 函数的线性组合。为证明 $\omega \land\theta$ 是 $C^{r}$ 连续的，我们写

$$
\begin{gather}
\omega=\sum_{[I]} b_{I} \widetilde{\psi}_{I}, \quad \theta=\sum_{[J]} c_{J} \widetilde{\psi}_{J}
\end{gather}
$$

从而有

$$
\begin{gather}
\omega \land\theta=\sum_{[I]} \sum_{[J]} b_{I}c_{J} \widetilde{\psi}_{I}\land \widetilde{\psi}_{J}
\end{gather}
$$

应用楔积的性质，我们将张量 $(\omega \land\theta)(x)$ 写成基本交错张量的线性组合：首先我们去除有指标相同的项，然后将剩余的项重写成升序指标的形式，并在前面写入符号（$\pm 1$），最后合并相同项。因此，$\omega \land\theta$ 的每个分量都是若干个 $\pm b_{I}c_{J}$ 的和，故 $\omega \land\theta$ 是 $C^{r}$ 连续的。

上面我们定义了张量场，但有时候，我们也希望能够将标量场和张量场同时考虑。因此，我们扩张微分形式的定义使其能够容纳标量场，即 $0$-形式。

**定义 3.1.11** 标量场（scalar field）

设 $A$ 是 $\mathbb{R}^{n}$ 中的开集，如果 $f\colon A\to \mathbb{R}$ 是一个 $C^{r}$ 函数，那么我们称 $f$ 是 $A$ 上的一个**标量场**，也称为 $A$ 上的一个 $0$-**形式**。

我们定义两个 $0$-形式 $f,g$ 的楔积为 $f\land g=fg$，即两个实值函数的乘积。更一般地，我们定义一个 $0$-形式 $f$ 和一个 $k$-形式 $\omega$ 的楔积为

$$
\begin{gather}
(\omega \land f)(x)=(f\land\omega)(x)=f(x)\omega(x)
\end{gather}
$$

即张量 $\omega(x)$ 与标量 $f(x)$ 的数乘。

注意到，当我们把楔积扩张到 $0$-形式后，其性质仍然成立：结合性、齐次性和分配性是显然的，并且反对称性成立因为标量场是 $0$ 阶形式：

$$
\begin{gather}
f\land\omega=(-1)^{0} \omega \land f
\end{gather}
$$

# Section 2: 微分算子

现在我们在微分形式上定义一个运算 $\mathrm{d}$，它可以视为对梯度、散度和旋度的一种扩展。一般来说，对一个 $k$-形式应用 $\mathrm{d}$，可以得到一个 $k+1$ 形式。我们从定义 $0$-形式的微分开始。

开集 $A$ 上的一个 $0$-形式是一个函数 $f\colon A\to \mathbb{R}$，它的微分 $\mathrm{d}f$ 是一个 $1$-形式，也就是从 $\mathcal{T}_{x}(\mathbb{R}^{n})$ 到 $\mathbb{R}$ 的一个线性泛函。事实上，我们在多元微分学中见过这样的一种函数，它就是“$f$ 在 $x$ 处的导数”，我们将其作为微分的定义。

**定义 3.2.1** 微分（differential）

设 $A$ 是 $\mathbb{R}^{n}$ 中的开集，$f\colon A\to \mathbb{R}$ 是一个 $C^{r}$ 函数，我们在 $A$ 上定义一个 $1$-形式 $\mathrm{d}f$ 如下：

$$
\begin{gather}
\mathrm{d} f(x)(x;v)=f'(x)v=J_{f}(x)v
\end{gather}
$$

称为 $f$ 的**微分**。它是一个以 $x$ 和 $v$ 作为自变量的 $C^{r-1}$ 函数。

**定理 3.2.2**

$0$-形式上的运算 $\mathrm{d}$ 是线性的。

**证明**

设 $f,g\colon A\to \mathbb{R}$ 是 $C^{r}$ 函数，令 $h=af+bg$，根据导数的线性性，我们有

$$
\begin{gather}
h'(x)=af'(x)+bg'(x)
\end{gather}
$$

从而

$$
\begin{gather}
\mathrm{d} h(x)(x;v)=a\mathrm{d} f(x)(x;v)+b\mathrm{d} g(x)(x;v)
\end{gather}
$$

对任意 $v$ 成立，这就完成了证明。

使用运算 $\mathrm{d}$，我们可以得到基本 $1$-形式 $\widetilde{\phi}_{i}$ 的另一种表达：

**定理 3.2.3**

设 $\widetilde{\phi}_{1},\dots,\widetilde{\phi}_{n}$ 是 $\mathbb{R}^{n}$ 上的基本 $1$-形式，令 $\pi_{i}\colon \mathbb{R}^{n}\to \mathbb{R}$ 为向第 $i$ 个坐标的投影函数，定义为

$$
\begin{gather}
\pi_{i}(x)=x_{i}
\end{gather}
$$

则 $\mathrm{d}\pi_{i}=\widetilde{\phi}_{i}$.

**证明**

由于 $\pi_{i}$ 是 $C^{\infty}$ 连续的，故 $\mathrm{d}\pi_{i}$ 是一个 $C^{\infty}$ 的 $1$-形式。我们有

$$
\begin{gather}
\mathrm{d} \pi_{i}(x)(x;v)=\pi_{i}'(x)v=[0,\dots,0,1,0,\dots,0] \begin{bmatrix}
v_{1} \\
\vdots \\
v_{n}
\end{bmatrix}=v_{i}
\end{gather}
$$

因此 $\mathrm{d}\pi_{i}=\widetilde{\phi}_{i}$.

在微分几何学中，我们通常把投影函数 $\pi_{i}$ 写成 $x_{i}$，于是，在这种记号下，$\widetilde{\phi}_{i}$ 就等于 $\mathrm{d}x_{i}$. 于是，下面我们约定：

**约定**

如果 $x \in \mathbb{R}^{n}$，我们用 $x_{i}$ 来表示向第 $i$ 个坐标的投影函数，则 $\mathrm{d}x_{i}$ 就等于 $\mathbb{R}^{n}$ 上的基本 $1$-形式 $\widetilde{\phi}_{i}$. 如果 $I=(i_{1},\dots,i_{k})$ 是 $[n]$ 上的升序 $k$-元组，我们引入记号

$$
\begin{gather}
\mathrm{d} x_{I}=\mathrm{d} x_{i_{1}}\land\dots \land \mathrm{d} x_{i_{k}}
\end{gather}
$$

来表示 $\mathbb{R}^{n}$ 上的基本 $k$-形式 $\widetilde{\psi}_{I}$. 于是，一个一般的 $k$-形式 $\omega$ 可以表示为

$$
\begin{gather}
\omega=\sum_{[I]} b_{I} \mathrm{d} x_{I}
\end{gather}
$$

形式 $\mathrm{d}x_{i}$ 和 $\mathrm{d}x_{I}$ 的计算公式由下式给出：

$$
\begin{gather}
\mathrm{d} x_{i}(x)(x;v)=v_{i} \\
\mathrm{d} x_{I}(x)((x;v_{1}),\dots,(x;v_{k}))=\det X_{I}
\end{gather}
$$

其中 $X_{I}$ 是矩阵 $[v_{1},\dots,v_{k}]$.

设 $J$ 是任意 $[n]$ 上的 $k$-元组，我们将这一记号扩展为

$$
\begin{gather}
\mathrm{d} x_{J}=\mathrm{d} x_{j_{1}}\land\dots \land \mathrm{d} x_{j_{k}}
\end{gather}
$$

此时 $\mathrm{d}x_{J}$ 不再是一个形式的微分，而是若干个基本 $1$-形式的楔积。

下面的定理解释了我们采用上述记号的原因。

**定理 3.2.4**

设 $A$ 是 $\mathbb{R}^{n}$ 中的开集，$f\colon A\to \mathbb{R}$ 是 $C^{r}$ 函数，则有

$$
\begin{gather}
\mathrm{d} f=\dfrac{ \partial f }{ \partial x_{1} } \mathrm{d} x_{1}+\dots+\dfrac{ \partial f }{ \partial x_{n} } \mathrm{d} x_{n}
\end{gather}
$$

特别地，$\mathrm{d}f=0$ 当且仅当 $f$ 是常值函数。

**证明**

任取 $(x;v)$，我们计算：

$$
\begin{gather}
\mathrm{d} f(x)(x;v)=f'(x)v=\sum_{i=1}^{n} \dfrac{ \partial f }{ \partial x_{i} } (x) v_{i}
\end{gather}
$$

由于 $v_{i}=\mathrm{d}x_{i}(x)(x;v)$，这就完成了证明。

在上述定理中取 $n=1$，则我们就得到了微积分中微分的定义式：

$$
\begin{gather}
\mathrm{d} f=\dfrac{\mathrm{d} f}{\mathrm{d} x} \mathrm{d} x
\end{gather}
$$

在微分形式的框架下，一切都合情合理。

对于 $C^{r}$ 函数 $f$，其微分 $\mathrm{d}f$ 是 $C^{r-1}$ 连续的这一事实非常不方便。这意味着我们需要在证明中时刻记录可微性的变化。为了避免这些困难，我们做如下约定：

**约定**

如果没有明确说明，我们将只考虑 $C^{\infty}$ 连续（光滑）的流形、映射、向量场以及形式。

接下来，我们来定义 $k$-形式上的微分算子 $\mathrm{d}$. 我们记开集 $A$ 上所有光滑 $k$-形式构成的集合为 $\Omega^{k}(A)$，它在 $k$-形式的加法与数乘下构成了一个向量空间。

**定理 3.2.5**

设 $A$ 是 $\mathbb{R}^{n}$ 中的开集，则存在唯一的线性映射

$$
\begin{gather}
\mathrm{d} \colon\Omega^{k}(A)\to\Omega^{k+1}(A)
\end{gather}
$$

使得：

1. 如果 $f$ 是一个 $0$-形式，那么 $\mathrm{d}f$ 是 $1$-形式 $$
\mathrm{d} f(x)(x;v)=f'(x)v
$$
2. 如果 $\omega,\eta$ 分别是 $k$ 阶和 $\ell$ 阶形式，则 $$
\mathrm{d} (\omega \land \eta)=\mathrm{d} \omega \land \eta+(-1)^{k} \omega \land \mathrm{d} \eta
$$
3. 对任意形式 $\omega$ 有 $\mathrm{d}(\mathrm{d}\omega)=0$

我们称 $\mathrm{d}$ 为**微分算子**（differential operator），并称 $\mathrm{d}\omega$ 为形式 $\omega$ 的**微分**。

**证明**

(1). 我们首先假设性质 1, 2, 3 成立来验证唯一性。我们先来证明，对任意形式 $\omega_{1},\dots,\omega_{k}$，有

$$
\begin{gather}
\mathrm{d} (\mathrm{d} \omega_{1}\land\dots \land \mathrm{d} \omega_{k})=0
\end{gather}
$$

当 $k=1$ 时，上式就是性质 3. 假设上式对 $k-1$ 成立，我们记 $\eta=\mathrm{d}\omega_{2}\land\dots \land \mathrm{d}\omega_{k}$，并计算

$$
\begin{gather}
\mathrm{d} (\mathrm{d} \omega_{1}\land \eta)=\mathrm{d} (\mathrm{d} \omega_{1})\land \eta\pm \mathrm{d} \omega_{1}\land \mathrm{d} \eta
\end{gather}
$$

第一项根据性质 3 等于零，第二项根据归纳假设也等于零，即证。

现在我们证明，对任意 $k$-形式 $\omega$，其微分 $\mathrm{d}\omega$ 仅由 $\mathrm{d}$ 在 $0$-形式上的值决定。由于 $\mathrm{d}$ 是线性的，故我们只需对 $\omega=f\mathrm{d}x_{I}$ 验证即可。我们计算

$$
\begin{align}
\mathrm{d} \omega &= \mathrm{d} (f\land \mathrm{d} x_{I}) \\
&= \mathrm{d} f\land \mathrm{d} x_{I}+f\land \mathrm{d} (\mathrm{d} x_{I}) \\
&= \mathrm{d} f\land \mathrm{d} x_{I}
\end{align}
$$

这表明，$\mathrm{d}\omega$ 仅与 $0$-形式 $f$ 的微分有关，这由性质 1 所确定，从而是唯一的。

(2). 现在我们来定义 $\mathrm{d}$. 步骤 (1) 中的计算已经告诉了我们定义的方法。对于 $0$-形式的微分，我们按性质 1 进行定义。给定开集 $A$ 以及其上的 $k$-形式 $\omega$，我们将 $\omega$ 写成

$$
\begin{gather}
\omega=\sum_{[I]} f_{I} \mathrm{d} x_{I}
\end{gather}
$$

然后定义

$$
\begin{gather}
\mathrm{d} \omega=\sum_{[I]} \mathrm{d} f_{I} \land \mathrm{d} x_{I}
\end{gather}
$$

我们来验证 $\mathrm{d}\omega \in\Omega^{k+1}(A)$. 我们首先写出

$$
\begin{gather}
\mathrm{d} \omega=\sum_{[I]} \left( \sum_{j=1}^{n} \dfrac{ \partial f_{I} }{ \partial x_{j} } \mathrm{d} x_{j} \right) \land \mathrm{d} x_{I}
\end{gather}
$$

然后我们按如下方法把 $\mathrm{d}\omega$ 写成 $k+1$ 阶基本形式的线性组合：首先去除所有 $j$ 与 $I$ 中的指标相同的项，然后对 $\mathrm{d}x_{i}$ 进行排列使其成为升序，最后合并相同项。因此，$\mathrm{d}\omega$ 的每个分量都是若干 $\dfrac{ \partial f_{I} }{ \partial x_{j} }$ 的线性组合，因此它是光滑的。（注意，如果 $\omega$ 是 $C^{r}$ 连续的，那么 $\mathrm{d}\omega$ 是 $C^{r-1}$ 连续的）

我们验证 $\mathrm{d}$ 在 $k$-形式上是线性的。设

$$
\begin{gather}
\omega=\sum_{[I]} f_{I}\mathrm{d} x_{I}, \quad \eta=\sum_{[I]} g_{I}\mathrm{d} x_{I}
\end{gather}
$$

则有

$$
\begin{align}
\mathrm{d} (a\omega+b \eta) &= \mathrm{d}  \sum_{[I]} (af_{I}+bg_{I}) \mathrm{d} x_{I} \\
&= \sum_{[I]} \mathrm{d} (af_{I}+bg_{I}) \land \mathrm{d} x_{I} \\
&= \sum_{[I]} (a\mathrm{d} f_{I}+b\mathrm{d} g_{I}) \land \mathrm{d} x_{I} \\
&= a\mathrm{d} \omega+b\mathrm{d} \eta
\end{align}
$$

(3). 现在我们证明，如果 $J$ 是 $[n]$ 上的任意 $k$-元组，那么对于 $0$-形式 $f$ 有

$$
\begin{gather}
\mathrm{d} (f\land \mathrm{d} x_{J})=\mathrm{d} f\land \mathrm{d} x_{J}
\end{gather}
$$

显然，当 $J$ 中有两个指标相同时上式成立，因为此时 $\mathrm{d}x_{J}=0$. 因此，我们假设 $J$ 中的指标各不相同。设 $I$ 是这些指标的升序排列形式，$\pi$ 是实现这一排列的置换，那么楔积的反对称性表明 $\mathrm{d}x_{I}=\mathrm{sgn}(\pi)\mathrm{d}x_{J}$，从而根据 $\mathrm{d}(f\land \mathrm{d}x_{I})=\mathrm{d}f\land \mathrm{d}x_{I}$ 以及楔积的齐次性和 $\mathrm{d}$ 的线性性有

$$
\begin{gather}
\mathrm{sgn}(\pi)\mathrm{d} (f\land \mathrm{d} x_{J})=\mathrm{sgn}(\pi) \mathrm{d} f\land \mathrm{d} x_{J}
\end{gather}
$$

消去 $\mathrm{sgn}(\pi)$ 即证。

(4). 我们验证性质 2 在 $k=\ell=0$ 情况下的特例。我们计算

$$
\begin{align}
\mathrm{d} (f\land g) &= \sum_{j=1}^{n} \dfrac{ \partial }{ \partial x_{j} } (fg) \mathrm{d} x_{j} \\
&= \sum_{j=1}^{n} \dfrac{ \partial f }{ \partial x_{j} }  g\mathrm{d} x_{j}+\sum_{j=1}^{n} f \dfrac{ \partial g }{ \partial x_{j} }  \mathrm{d} x_{j} \\
&= \mathrm{d} f\land g+f\land \mathrm{d} g
\end{align}
$$

(5). 我们验证一般情况下的性质 2. 根据 $\mathrm{d}$ 的线性性，我们只需考虑

$$
\begin{gather}
\omega=f\mathrm{d} x_{I}, \quad \eta=g\mathrm{d} x_{J}
\end{gather}
$$

的情况。我们计算

$$
\begin{align}
\mathrm{d} (\omega \land \eta) &= \mathrm{d} (fg \mathrm{d} x_{I}\land \mathrm{d} x_{J}) \\
&= \mathrm{d} (fg)\land \mathrm{d} x_{I} \land \mathrm{d} x_{J} \\
&= (\mathrm{d} f\land g+f\land \mathrm{d} g)\land \mathrm{d} x_{I}\land \mathrm{d} x_{J} \\
&= \mathrm{d} f\land \mathrm{d} x_{I}\land g\land \mathrm{d} x_{J}+(-1)^{k} f\land \mathrm{d} x_{I}\land \mathrm{d} g\land \mathrm{d} x_{J} \\
&=\mathrm{d} \omega \land \eta+(-1)^{k} \omega \land \mathrm{d} \eta
\end{align}
$$

注意第二项的符号 $(-1)^{k}$ 来源于交换 $k$-形式 $\mathrm{d}x_{I}$ 与 $1$-形式 $\mathrm{d}g$.

当 $k=0$ 或 $\ell=0$ 时，我们仍然可以按上面的推导进行证明，只需在式中去除 $\mathrm{d}x_{I}$ 或 $\mathrm{d}x_{J}$ 这一项即可。

(6). 我们证明对 $0$-形式 $f$ 有 $\mathrm{d}(\mathrm{d}f)=0$. 我们计算

$$
\begin{align}
\mathrm{d} (\mathrm{d} f) &= \mathrm{d} \sum_{j=1}^{n} \dfrac{ \partial f }{ \partial x_{j} } \mathrm{d} x_{j} \\
&= \sum_{j=1}^{n} \mathrm{d} \left( \dfrac{ \partial f }{ \partial x_{j} }  \right)\land \mathrm{d} x_{j} \\
&= \sum_{j=1}^{n} \sum_{i=1}^{n} \dfrac{ \partial  }{ \partial x_{i} } \dfrac{ \partial f }{ \partial x_{j} } \mathrm{d} x_{i} \land \mathrm{d} x_{j} \\
&= \sum_{1\leq i<j\leq n} \left( \dfrac{ \partial ^{2} f }{ \partial x_{i} \partial x_{j} } - \dfrac{ \partial ^{2} f }{ \partial x_{j} \partial x_{i} } \right) \mathrm{d} x_{i}\land \mathrm{d} x_{j}
\end{align}
$$

根据偏导顺序的可交换性（Clairaut 定理），可得 $\mathrm{d}(\mathrm{d}f)=0$.

(7). 最后我们证明，如果 $\omega$ 是 $k$-形式，那么 $\mathrm{d}(\mathrm{d}\omega)=0$. 我们只需考虑 $\omega=f\mathrm{d}x_{I}$ 的情况，则有

$$
\begin{align}
\mathrm{d} (\mathrm{d} \omega) &= \mathrm{d} (\mathrm{d} f\land \mathrm{d} x_{I}) \\
&=\mathrm{d} (\mathrm{d} f)\land \mathrm{d} x_{I}-\mathrm{d} f\land \mathrm{d} (\mathrm{d} x_{I})
\end{align}
$$

由于 $\mathrm{d}(\mathrm{d}f)=0$，并且

$$
\begin{gather}
\mathrm{d} (\mathrm{d} x_{I})=\mathrm{d} (1)\land \mathrm{d} x_{I}=0
\end{gather}
$$

因此 $\mathrm{d}(\mathrm{d}\omega)=0$，这就完成了证明。

**定义 3.2.6** 闭形式（closed form），恰当形式（exact form）

设 $A$ 是 $\mathbb{R}^{n}$ 上的开集，$A$ 上的 $0$-形式 $f$ 称为**恰当的**，如果 $f$ 在 $A$ 上是常值函数；$A$ 上的 $k$-形式 $\omega$ 称为**恰当的**，如果存在 $k-1$ 形式 $\theta$ 使得 $\omega=\mathrm{d}\theta$. $A$ 上的 $k$-形式 $\omega$ 称为**闭的**，如果 $\mathrm{d}\omega=0$.

恰当性是一个我们曾见过的概念。我们称一个向量场

$$
\begin{gather}
F=Pe_{1}+Qe_{2}+R e_{3}
\end{gather}
$$

是**保守场**，如果它是某个标量场 $f$（称为**势函数**）的梯度：

$$
\begin{gather}
P=\dfrac{ \partial f }{ \partial x } ,\quad Q=\dfrac{ \partial f }{ \partial y } , \quad R=\dfrac{ \partial f }{ \partial z } 
\end{gather}
$$

这就等价于说 $1$-形式 $P\mathrm{d}x+Q\mathrm{d}y+R\mathrm{d}z$ 是 $0$-形式 $f$ 的微分，也就是说，它是恰当形式。

由于 $\mathrm{d}(\mathrm{d}\omega)=0$，因此所有的恰当形式都是闭的。然而，并非每个闭形式都是恰当形式。事实上，“在什么情况下闭形式是恰当形式”是一个非平凡的问题，我们将在后续的章节进行讨论。

# Section 3: 梯度、散度与旋度

现在，是时候证明我们对张量场、微分形式与算子所做的工作的确是对 $\mathbb{R}^{3}$ 中我们熟悉的向量分析的推广。我们将给出向量场与微分形式之间的一种转换语言，它允许我们将使用微分形式的语言的定理翻译为使用向量场的语言的定理，这是后续我们从广义 Stokes 公式中得到 Green 公式、Gauss 公式和 Stokes 公式的关键。

给定开集 $A$，我们已经知道 $A$ 上的 $k$-形式构成的集合 $\Omega^{k}(A)$ 是一个向量空间。另一边，我们可以容易地证明，$A$ 上的光滑向量场构成的集合也是向量空间。我们将在这两个向量空间之间建立同构关系，从而证明梯度、散度和旋度与微分算子 $\mathrm{d}$ 本质上是同一种运算。

**定义 3.3.1** 梯度（gradient），散度（divergence）

设 $A$ 是 $\mathbb{R}^{n}$ 中的开集，$f\colon A\to \mathbb{R}$ 是一个标量场，我们定义 $f$ 的**梯度**为向量场

$$
\begin{gather}
(\mathrm{grad}\ f)(x)=\left( x; \dfrac{ \partial f }{ \partial x_{1} }(x) e_{1}+\dots+\dfrac{ \partial f }{ \partial x_{n} }(x) e_{n} \right)
\end{gather}
$$

再设 $G(x)=(x;g(x))$ 是 $A$ 上的向量场，其中 $g\colon A\to \mathbb{R}$ 由方程

$$
\begin{gather}
g(x)=g_{1}(x)e_{1}+\dots+g_{n}(x)e_{n}
\end{gather}
$$

给出，则我们定义 $G$ 的**散度**为标量场

$$
\begin{gather}
(\mathrm{div}\ G)(x)=\dfrac{ \partial g_{1} }{ \partial x_{1} } (x)+\dots+\dfrac{ \partial g_{n} }{ \partial x_{n} } (x)
\end{gather}
$$

**定理 3.3.2**

设 $A$ 是 $\mathbb{R}^{n}$ 中的开集，则存在线性同构 $\alpha_{i}$ 和 $\beta_{j}$ 使得下图交换：

![](3-5.png)

换句话说，我们有

$$
\begin{gather}
\mathrm{d} \circ\alpha_{0}=\alpha_{1}\circ \mathrm{grad}, \quad \mathrm{d} \circ\beta_{n-1}=\beta_{n}\circ \mathrm{div}
\end{gather}
$$

**证明**

设 $f$ 和 $h$ 是 $A$ 上的标量场，并设

$$
\begin{gather}
F(x)=\left( x;\sum_{i=1}^{n} f_{i}(x)e_{i} \right), \quad G(x)=\left( x;\sum_{i=1}^{n} g_{i}(x)e_{i} \right)
\end{gather}
$$

是 $A$ 上的向量场。我们定义

$$
\begin{align}
\alpha_{0}f &= f \\
\alpha_{1}F &= \sum_{i=1}^{n} f_{i} \mathrm{d} x_{i} \\
\beta_{n-1}G &= \sum_{i=1}^{n} (-1)^{i-1} g_{i} \mathrm{d} x_{1}\land\dots \land \mathrm{d} x_{i-1}\land \mathrm{d} x_{i+1}\land\dots \land \mathrm{d} x_{n} \\
\beta_{n}h &= h \mathrm{d} x_{1}\land\dots \land \mathrm{d} x_{n}
\end{align}
$$

显然 $\alpha_{0},\alpha_{1},\beta_{n}$ 都是线性同构，并且 $\beta_{n-1}$ 是线性的，我们验证 $\beta_{n-1}$ 是一个双射。我们记 $\mathrm{d}x_{[n]\setminus \{ i \}}=\mathrm{d}x_{1}\land\dots \land \mathrm{d}x_{i-1}\land \mathrm{d}x_{i+1}\land\dots \land \mathrm{d}x_{n}$.

假设 $\beta_{n-1}G=\beta_{n-1}H$，由于 $\mathrm{d}x_{[n]\setminus \{ i \}}$ 是 $\Omega^{n-1}(A)$ 的基，因此有

$$
\begin{gather}
(-1)^{i-1}g_{i}=(-1)^{i-1}h_{i}
\end{gather}
$$

对任意 $i$ 成立，因此 $\beta_{n-1}$ 是单的。再取 $\omega \in\Omega^{n-1}(A)$，它可以表示成

$$
\begin{gather}
\omega=\sum_{i=1}^{n} b_{i} \mathrm{d} x_{[n]\setminus \{ i \}}
\end{gather}
$$

此时取 $g_{i}=(-1)^{i-1}b_{i}$ 即得 $\beta_{n-1}G=\omega$，从而 $\beta_{n-1}$ 是一个同构。

接下来我们验证等式。我们计算

$$
\begin{align}
\alpha_{1}^{-1}\circ\mathrm{d} \circ\alpha_{0}(f) &= \alpha_{1}^{-1}\circ \mathrm{d} f \\
&= \alpha_{1}^{-1}\left( \sum_{i=1}^{n} \dfrac{ \partial f }{ \partial x_{i} } \mathrm{d} x_{i} \right) \\
&= \left( x; \sum_{i=1}^{n} \dfrac{ \partial f }{ \partial x_{i} } (x) e_{i} \right) \\
&= \mathrm{grad}\ f
\end{align}
$$

以及

$$
\begin{align}
\beta_{n}^{-1}\circ \mathrm{d} \circ\beta_{n-1}(G) &= \beta_{n}^{-1}\circ \mathrm{d} \left( \sum_{i=1}^{n} (-1)^{i-1} g_{i} \mathrm{d} x_{[n]\setminus \{ i \}} \right) \\
&= \beta_{n}^{-1}\left( \sum_{i=1}^{n} (-1)^{i-1} \mathrm{d} g_{i} \land \mathrm{d} x_{[n]\setminus \{ i \}} \right) \\
&= \beta_{n}^{-1}\left( \sum_{i=1}^{n} (-1)^{i-1} \sum_{j=1}^{n} \dfrac{ \partial g_{i} }{ \partial x_{j} } \mathrm{d} x_{j} \land \mathrm{d} x_{[n]\setminus \{ i \}} \right) \\
&= \beta_{n}^{-1}\left( \sum_{i=1}^{n} (-1)^{i-1} \dfrac{ \partial g_{i} }{ \partial x_{i} } \mathrm{d} x_{i} \land \mathrm{d} x_{[n]\setminus \{ i \}} \right) \\
&= \beta_{n}^{-1}\left( \sum_{i=1}^{n} \dfrac{ \partial g_{i} }{ \partial x_{i} } \mathrm{d} x_{1}\land\dots \land \mathrm{d} x_{n} \right) \\
&= \sum_{i=1}^{n} \dfrac{ \partial g_{i} }{ \partial x_{i} } =\mathrm{div}\ G
\end{align}
$$

这就完成了证明。

上述定理完全描述了 $\mathbb{R}^{n}$ 上向量场的运算。不过，在 $\mathbb{R}^{3}$ 中，我们还可以更进一步，这需要用到 $\mathbb{R}^{3}$ 中特有的运算：旋度。

**定义 3.3.3** 旋度（curl）

设 $A$ 是 $\mathbb{R}^{3}$ 中的开集，令

$$
\begin{gather}
F(x)=(x;f_{1}(x)e_{1}+f_{2}(x)e_{2}+f_{3}(x)e_{3})
\end{gather}
$$

是 $A$ 上的向量场，我们定义 $F$ 的**旋度**为向量场

$$
\begin{align}
&(\mathrm{curl}\ F)(x) \\
&=\left( x; \left( \dfrac{ \partial f_{3} }{ \partial x_{2} } -\dfrac{ \partial f_{2} }{ \partial x_{3} }  \right)e_{1}+\left( \dfrac{ \partial f_{1} }{ \partial x_{3} } -\dfrac{ \partial f_{3} }{ \partial x_{1} }  \right)e_{2}+\left( \dfrac{ \partial f_{2} }{ \partial x_{1} } -\dfrac{ \partial f_{1} }{ \partial x_{2} }  \right) e_{3}\right)
\end{align}
$$

上述公式在形式上可以简单记为

$$
\begin{gather}
\det \begin{bmatrix}
e_{1} & e_{2} & e_{3} \\
\dfrac{ \partial  }{ \partial x_{1} }  & \dfrac{ \partial  }{ \partial x_{2} }  & \dfrac{ \partial  }{ \partial x_{3} }  \\
f_{1} & f_{2} & f_{3}
\end{bmatrix}
\end{gather}
$$

在 $\mathbb{R}^{3}$ 上，我们有定理 3.3.2 的加强版：

**定理 3.3.4**

设 $A$ 是 $\mathbb{R}^{3}$ 中的开集，则存在线性同构 $\alpha_{i}$ 和 $\beta_{j}$ 使得下图交换：

![](3-6.png)

换句话说，我们有

$$
\begin{gather}
\mathrm{d} \circ\alpha_{0}=\alpha_{1}\circ \mathrm{grad}, \quad \mathrm{d} \circ\alpha_{1}=\beta_{2}\circ \mathrm{curl}, \quad \mathrm{d} \circ\beta_{2}=\beta_{3}\circ \mathrm{div}
\end{gather}
$$

**证明**

令 $\alpha_{i},\beta_{j}$ 如定理 3.3.2 中所示，则我们只需验证第二个等式。设 $F$ 是 $A$ 上的向量场，我们计算

$$
\begin{align}
\mathrm{d} \circ\alpha_{1}(F) &= \mathrm{d} \left( \sum_{i=1}^{3} f_{i}\mathrm{d} x_{i} \right) \\
&= \sum_{i=1}^{3} \mathrm{d} f_{i}\land \mathrm{d} x_{i} \\
&= \sum_{i=1}^{3} \sum_{j=1}^{3} \dfrac{ \partial f_{i} }{ \partial x_{j} } \mathrm{d} x_{j}\land \mathrm{d} x_{i} \\
&= \sum_{1\leq j<i\leq 3} \left( \dfrac{ \partial f_{i} }{ \partial x_{j} } -\dfrac{ \partial f_{j} }{ \partial x_{i} }  \right) \mathrm{d} x_{j}\land \mathrm{d} x_{i} \\
\end{align}
$$

对其应用 $\beta_{2}^{-1}$ 即得

$$
\begin{gather}
\left( x; \left( \dfrac{ \partial f_{3} }{ \partial x_{2} } -\dfrac{ \partial f_{2} }{ \partial x_{3} }  \right)e_{1} - \left( \dfrac{ \partial f_{3} }{ \partial x_{1} } -\dfrac{ \partial f_{1} }{ \partial x_{3} }  \right)e_{2}+\left( \dfrac{ \partial f_{2} }{ \partial x_{1} } -\dfrac{ \partial f_{1} }{ \partial x_{2} }  \right)e_{3} \right)
\end{gather}
$$

这正是 $\mathrm{curl}$ 的定义。

# Section 4: 可微映射的对偶

如果 $\alpha\colon A\to \mathbb{R}^{n}$ 是一个光滑映射，其中 $A$ 是 $\mathbb{R}^{k}$ 中的开集，那么 $\alpha$ 诱导了一个从 $x$ 处的切空间到 $\alpha(x)$ 处的切空间的线性映射 $\alpha_{*}$；另一方面，我们知道任意一个线性映射 $T\colon V\to W$ 都诱导了一个交错张量上的对偶映射 $T^{*}\colon \mathcal{A}^{\ell}(W)\to \mathcal{A}^{\ell}(V)$. 将上面两个事实结合，我们将展示光滑映射 $\alpha$ 如何导出一个微分形式上的对偶映射，我们记作 $\alpha^{*}$，它能够保持我们施加在形式上的所有结构：向量空间、楔积以及微分算子。

**定义 3.4.1**

设 $A$ 是 $\mathbb{R}^{k}$ 中的开集，$\alpha\colon A\to \mathbb{R}^{n}$ 是 $C^{\infty}$ 函数，令 $B$ 是 $\mathbb{R}^{n}$ 中包含 $\alpha[A]$ 的开集，我们定义**微分形式上的对偶映射**

$$
\begin{gather}
\alpha^{*}\colon\Omega^{\ell}(B)\to\Omega^{\ell}(A)
\end{gather}
$$

如下：给定 $0$-形式 $f\colon B\to \mathbb{R}$，定义 $(\alpha^{*}f)(x)=f(\alpha(x))$；给定 $\ell$-形式 $\omega$，定义

$$
\begin{gather}
(\alpha^{*}\omega)(x)((x;v_{1}),\dots,(x;v_{\ell}))=\omega(\alpha(x))(\alpha_{*}(x;v_{1}),\dots,\alpha_{*}(x;v_{\ell}))
\end{gather}
$$

由于 $f,\omega,\alpha,\alpha'$ 都是光滑的，因此 $\alpha^{*}f$ 和 $\alpha^{*}\omega$ 也是光滑的。注意，如果 $f,\omega,\alpha$ 是 $C^{r}$ 连续的，那么 $\alpha^{*}f$ 是 $C^{r}$ 函数，但 $\alpha^{*}\omega$ 将会是 $C^{r-1}$ 连续的（因为 $\alpha_{*}(x;v)=(\alpha(x);\alpha'(x)v)$）。因此，这里我们同样只考虑 $C^{\infty}$ 函数。

映射 $\alpha^{*}$ 与线性映射 $\alpha_{*}$ 的对偶关系如下所示：给定光滑函数 $\alpha\colon A\to \mathbb{R}^{n}$，设 $y=\alpha(x)$，则它诱导了线性映射

$$
\begin{gather}
T=\alpha_{*}\colon \mathcal{T}_{x}(\mathbb{R}^{k})\to \mathcal{T}_{y}(\mathbb{R}^{n})
\end{gather}
$$

这一映射又诱导了交错张量上的对偶映射

$$
\begin{gather}
T^{*}\colon \mathcal{A}^{\ell}(\mathcal{T}_{y}(\mathbb{R}^{n}))\to \mathcal{A}^{\ell}(\mathcal{T}_{x}(\mathbb{R}^{k}))
\end{gather}
$$

如果 $\omega$ 是 $B$ 上的 $\ell$-形式，那么 $\omega(y) \in \mathcal{A}^{\ell}(\mathcal{T}_{y}(\mathbb{R}^{n}))$，从而 $T^{*}(\omega(y))$ 就是 $\mathcal{T}_{x}(\mathbb{R}^{k})$ 上的一个交错张量，它就等于

$$
\begin{gather}
T^{*}(\omega(y))=(\alpha^{*}\omega)(x)
\end{gather}
$$

这是因为

$$
\begin{align}
T^{*}(\omega(y))((x;v_{1}),\dots,(x;v_{\ell})) &= \omega(\alpha(x))(\alpha_{*}(x;v_{1}),\dots,\alpha_{*}(x;v_{\ell})) \\
&= (\alpha^{*}\omega)(x)((x;v_{1}),\dots,(x;v_{\ell}))
\end{align}
$$

这一事实允许我们利用对偶映射 $T^{*}$ 的性质来得到关于 $\alpha^{*}$ 的性质：

**定理 3.4.2**

设 $A$ 是 $\mathbb{R}^{k}$ 中的开集，$\alpha\colon A\to \mathbb{R}^{m}$ 是 $C^{\infty}$ 函数，$B$ 是 $\mathbb{R}^{m}$ 中包含 $\alpha[A]$ 的开集，$\beta\colon B\to \mathbb{R}^{n}$ 是 $C^{\infty}$ 函数。设 $\omega,\eta,\theta$ 是定义在 $\mathbb{R}^{n}$ 中包含 $\beta[B]$ 的开集 $C$ 上的形式，且 $\omega$ 和 $\eta$ 的阶数相同。则映射 $\alpha^{*}$ 和 $\beta^{*}$ 满足以下性质：

1. $\beta^{*}(a\omega+b \eta)=a(\beta^{*}\omega)+b(\beta^{*}\eta)$
2. $\beta^{*}(\omega \land\theta)=\beta^{*}\omega \land\beta^{*}\theta$
3. $(\beta \circ\alpha)^{*}\omega=\alpha^{*}(\beta^{*}\omega)$

**证明**

对于 $k$-形式（$k>0$），上述定理只是定理 2.1.8 和 2.3.1 的重述。其中一部分或所有形式的阶数为 $0$ 的情况是平凡的。

这一定理表明，$\alpha^{*}$ 保持向量空间结构与楔积，下面我们来证明它保持微分算子。为此，我们给出 $\alpha^{*}\omega$ 的一个计算公式。事实上，设 $A$ 在 $\mathbb{R}^{k}$ 中开，且 $\alpha\colon A\to \mathbb{R}^{n}$ 是光滑函数，我们只需要给出 $1$-形式和 $k$-形式的计算公式即可。

由于 $\alpha^{*}$ 是线性的，且保持楔积，又由于 $\alpha^{*}f=f\circ\alpha$，故我们只需计算基本 $1$-形式和基本 $k$-形式即可。下面是所求的公式：

**定理 3.4.3**

设 $A$ 是 $\mathbb{R}^{k}$ 中的开集，$\alpha\colon A\to \mathbb{R}^{n}$ 是 $C^{\infty}$ 函数。令 $x$ 表示 $\mathbb{R}^{k}$ 中的一般点，$y$ 表示 $\mathbb{R}^{n}$ 中的一般点，则 $\mathrm{d}x_{i}$ 和 $\mathrm{d}y_{i}$ 分别表示 $\mathbb{R}^{k}$ 和 $\mathbb{R}^{n}$ 上的基本 $1$-形式。我们有如下公式成立：

1. $\alpha^{*}(\mathrm{d}y_{i})=\mathrm{d}\alpha_{i}$
2. 如果 $I=(i_{1},\dots,i_{k})$ 是 $[n]$ 上的升序 $k$-元组，那么 $$
\alpha^{*}(\mathrm{d} y_{I})=\det \dfrac{ \partial \alpha_{I} }{ \partial x }  \mathrm{d} x_{1}\land \dots \land \mathrm{d} x_{k}
$$其中 $$
\dfrac{ \partial \alpha_{I} }{ \partial x } =\dfrac{ \partial (\alpha_{i_{1}},\dots,\alpha_{i_{k}}) }{ \partial (x_{1},\dots,x_{k}) } 
$$

**证明**

(1). 令 $y=\alpha(x)$，我们计算

$$
\begin{align}
\alpha^{*}(\mathrm{d} y_{i})(x)(x;v) &= \mathrm{d} y_{i}(y)(\alpha_{*}(x;v)) \\
&= \pi_{i} (\alpha'(x)v) \\
&= \sum_{j=1}^{k} \dfrac{ \partial \alpha_{i} }{ \partial x_{j} } (x) v_{j} \\
&= \sum_{j=1}^{k} \dfrac{ \partial \alpha_{i} }{ \partial x_{j} }(x) \mathrm{d} x_{j}(x)(x;v)
\end{align}
$$

这表明

$$
\begin{gather}
\alpha^{*}(\mathrm{d} y_{i})=\sum_{j=1}^{k} \dfrac{ \partial \alpha_{i} }{ \partial x_{j} } \mathrm{d} x_{j}=\mathrm{d} \alpha_{i}
\end{gather}
$$

(2). 形式 $\alpha^{*}(\mathrm{d}y_{I})$ 是定义在 $\mathbb{R}^{k}$ 中的开集上的一个 $k$-形式，因此它可以写成

$$
\begin{gather}
\alpha^{*}(\mathrm{d} y_{I})=h \mathrm{d} x_{1}\land\dots \land \mathrm{d} x_{k}
\end{gather}
$$

其中 $h$ 是一个标量场。如果我们将右边应用到 $(x;e_{1}),\dots,(x;e_{k})$ 上，我们就得到了 $h(x)$，从而我们有

$$
\begin{align}
h(x) &= \alpha^{*}(\mathrm{d} y_{I})(x)((x;e_{1}),\dots,(x;e_{k})) \\
&= \mathrm{d} y_{I} (y) (\alpha_{*}(x;e_{1}),\dots,\alpha_{*}(x;e_{k})) \\
&= \mathrm{d} y_{I}(y)\left( \left( y;\dfrac{ \partial \alpha }{ \partial x_{1} }  \right),\dots,\left( y;\dfrac{ \partial \alpha }{ \partial x_{k} }  \right) \right) \\
&= \det [J_{\alpha}(x)]_{I} \\
&= \det \dfrac{ \partial \alpha_{I} }{ \partial x } 
\end{align}
$$

这就完成了证明。

对于一般情况，我们可以仿照上面 (2) 的证明，首先将 $\ell$-形式 $\alpha^{*}(\mathrm{d}y_{I})$ 表示为基本形式的线性组合，然后应用到基向量上。最终，我们可得公式

$$
\begin{gather}
\alpha^{*}(\mathrm{d} y_{I})=\sum_{[J]} \det \dfrac{ \partial \alpha_{I} }{ \partial x_{J} } \mathrm{d} x_{J}
\end{gather}
$$

其中

$$
\begin{gather}
\dfrac{ \partial \alpha_{I} }{ \partial x_{J} } =\dfrac{ \partial (\alpha_{i_{1}},\dots,\alpha_{i_{\ell}}) }{ \partial (x_{j_{1}},\dots,x_{j_{\ell}}) } 
\end{gather}
$$

**定理 3.4.4**

设 $A$ 是 $\mathbb{R}^{k}$ 中的开集，$\alpha\colon A\to \mathbb{R}^{n}$ 是 $C^{\infty}$ 函数，如果 $\omega$ 是定义在 $\mathbb{R}^{n}$ 中包含 $\alpha[A]$ 的开集上的 $\ell$-形式，那么

$$
\begin{gather}
\alpha^{*}(\mathrm{d} \omega)=\mathrm{d} (\alpha^{*}\omega)
\end{gather}
$$

**证明**

设 $x$ 表示 $\mathbb{R}^{k}$ 中的一般点，$y$ 表示 $\mathbb{R}^{n}$ 中的一般点。

(1). 我们首先对 $0$-形式 $f$ 进行验证。我们首先计算等式左边：

$$
\begin{align}
\alpha^{*}(\mathrm{d} f)&= \alpha^{*}\left( \sum_{i=1}^{n} \dfrac{ \partial f }{ \partial y_{i} } \mathrm{d} y_{i} \right) \\
&= \sum_{i=1}^{n} \left( \dfrac{ \partial f }{ \partial y_{i} } \circ\alpha \right) \mathrm{d} \alpha_{i}
\end{align}
$$

再计算右边：

$$
\begin{align}
\mathrm{d} (\alpha^{*}f) &= \mathrm{d} (f\circ\alpha) \\
&= \sum_{j=1}^{k} \dfrac{ \partial  }{ \partial x_{j} } (f\circ\alpha) \mathrm{d} x_{j}
\end{align}
$$

接下来我们使用链式法则。令 $y=\alpha(x)$，则有

$$
\begin{align}
\dfrac{ \partial  }{ \partial x_{j} } (f\circ\alpha)(x)&= J_{f\circ\alpha}(x)e_{j} \\
&= J_{f}(y) J_{\alpha}(x)e_{j} \\
&= \sum_{i=1}^{n} \dfrac{ \partial f }{ \partial y_{i} } (y) \dfrac{ \partial \alpha_{i} }{ \partial x_{j} } (x)
\end{align}
$$

从而

$$
\begin{gather}
\dfrac{ \partial  }{ \partial x_{j} } (f\circ\alpha)=\sum_{i=1}^{n} \left( \dfrac{ \partial f }{ \partial y_{i} } \circ\alpha \right) \dfrac{ \partial \alpha_{i} }{ \partial x_{j} } 
\end{gather}
$$

于是就有

$$
\begin{align}
\mathrm{d} (\alpha^{*}f) &= \sum_{j=1}^{k} \sum_{i=1}^{n} \left( \dfrac{ \partial f }{ \partial y_{i} } \circ\alpha \right) \dfrac{ \partial \alpha_{i} }{ \partial x_{j} } \mathrm{d} x_{j} \\
&= \sum_{i=1}^{n} \left( \dfrac{ \partial f }{ \partial y_{i} } \circ\alpha \right) \mathrm{d} \alpha_{i} \\
&= \alpha^{*}(\mathrm{d} f)
\end{align}
$$

(2). 我们验证剩下的部分。由于 $\alpha^{*}$ 和 $\mathrm{d}$ 都是线性的，故我们只需验证 $\omega=f\mathrm{d}y_{I}$ 的情况。我们首先计算

$$
\begin{align}
\alpha^{*}(\mathrm{d} \omega) &= \alpha^{*}(\mathrm{d} f\land \mathrm{d} y_{I}) \\
&= \alpha^{*}(\mathrm{d} f)\land\alpha^{*}(\mathrm{d} y_{I})
\end{align}
$$

另一方面，我们有

$$
\begin{align}
\mathrm{d} (\alpha^{*}\omega) &= \mathrm{d} (\alpha^{*}(f\land \mathrm{d} y_{I})) \\
&= \mathrm{d} (\alpha^{*}f\land\alpha^{*}(\mathrm{d} y_{I})) \\
&= \mathrm{d} (\alpha^{*}f) \land \alpha^{*}(\mathrm{d} y_{I}) + \alpha^{*}f\land \mathrm{d} (\alpha^{*}(\mathrm{d} y_{I}))
\end{align}
$$

由于

$$
\begin{gather}
\mathrm{d} (\alpha^{*}(\mathrm{d} y_{I}))=\mathrm{d} (\mathrm{d} \alpha_{i_{1}}\land\dots \land \mathrm{d} \alpha_{i_{\ell}})=0
\end{gather}
$$

从而由 (1) 中的结果即证。

我们现在有了微分形式的代数以及微分算子 $\mathrm{d}$ 可供使用。本节和上一节中所总结的这个代数和算子 $\mathrm{d}$ 的基本性质，就是我们在后续所需要的全部内容。