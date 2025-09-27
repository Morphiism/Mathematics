**（线性）泛函分析**是无穷维向量空间理论的别名，它与有限维向量空间理论（线性代数）最大的区别就是它对于拓扑的考虑。在有限维空间上，只有一种合理的拓扑（也就是标准度量生成的拓扑），并且线性映射是自动连续的（19.1.1），但在无限维空间如函数空间上，事情就没有这么简单了。本章我们将对泛函分析的基础内容给出一些简单的介绍。

# Section 1: 赋范空间

本章中，我们总是设 $\mathbb{F}=\mathbb{R}$ 或 $\mathbb{C}$.

**定义 27.1.1** 范数（norm），半范数（seminorm）

设 $\mathcal{X}$ 是 $\mathbb{F}$ 上的向量空间，其上的**半范数**是函数 $\lVert \cdot \rVert\colon \mathcal{X}\to[0,+\infty)$ 使得对任意 $x,y \in \mathcal{X},\lambda \in \mathbb{F}$ 有：

- 齐次性：$\lVert \lambda x \rVert=|\lambda| \lVert x \rVert$
- 三角不等式：$\lVert x+y \rVert\leq \lVert x \rVert+\lVert y \rVert$

如果半范数 $\lVert \cdot \rVert$ 还满足：

- 正定性：$\lVert x \rVert=0$ 当且仅当 $x=0$

那么 $\lVert \cdot \rVert$ 就称为一个**范数**，并称 $(\mathcal{X},\lVert \cdot \rVert)$ 是一个**赋范空间**。

如果 $\mathcal{X}$ 是一个赋范空间，那么定义为 $d(x,y)=\lVert x-y \rVert$ 的函数 $d$ 就是一个度量，其生成的拓扑称为**范数拓扑**，如果没有特殊指定，对于一个赋范空间我们总是取它的范数拓扑作为其上的拓扑。

**定义 27.1.2** 等价（equivalent）

设 $\mathcal{X}$ 是赋范空间，其上的两个范数 $\lVert \cdot \rVert_{1},\lVert \cdot \rVert_{2}$ 是**等价的**，如果存在 $C_{1},C_{2}>0$ 使得对任意 $x \in \mathcal{X}$ 有

$$
\begin{gather}
C_{1}\lVert x \rVert _{1}\leq \lVert x \rVert _{2}\leq C_{2}\lVert x \rVert _{1}
\end{gather}
$$

显然，如果两个范数等价，那么它们定义的拓扑就是相同的。我们说“有限维空间上只有一种合理的拓扑”，指的就是有限维空间上的所有范数都是等价的。

**定义 27.1.3** Banach 空间

设 $\mathcal{X}$ 是一个赋范空间，如果 $\mathcal{X}$ 关于范数度量是完备的，那么 $\mathcal{X}$ 就称为一个 **Banach 空间**。

每个赋范空间都同胚于一个 Banach 空间的稠密子集，因为每个度量空间都可以完备化，并且完备空间的基础集合是原空间基础集合的闭包。之后我们将给出另一种构造方法。

接下来，我们给出一个判断完备性的方法。

**定理 27.1.4**

一个赋范空间 $\mathcal{X}$ 是完备的当且仅当 $\mathcal{X}$ 中的绝对收敛级数是收敛的。

**证明**

如果 $\mathcal{X}$ 是完备的，$\sum_{n=1}^{\infty}\lVert x_{n} \rVert<+\infty$，设 $S_{N}=\sum_{n=1}^{N}x_{n}$，则对任意 $\varepsilon>0$，存在 $N$ 使得对任意 $n>m>N$ 有

$$
\begin{gather}
\lVert S_{n}-S_{m} \rVert \leq \sum_{n=m+1}^{n} \lVert x_{n} \rVert<\varepsilon
\end{gather}
$$

因此 $(S_{N})$ 是一个 Cauchy 序列，从而是收敛的。

反之，设每个绝对收敛级数是收敛的，令 $(x_{n})$ 是一个 Cauchy 序列，取 $n_{1}<n_{2}<\cdots$ 使得对任意 $n,m\geq n_{j}$ 有 $\lVert x_{n}-x_{m} \rVert<2^{-j}$，令 $y_{1}=x_{n_{1}}$，$y_{j}=x_{n_{j}}-x_{n_{j-1}}$，则有 $\sum_{j=1}^{k}y_{j}=x_{n_{k}}$，并且

$$
\begin{gather}
\sum_{j=1}^{\infty}\lVert y_{j} \rVert\leq \lVert y_{1} \rVert + \sum_{j=1}^{\infty} 2^{-j}<+\infty
\end{gather}
$$

因此 $\sum_{j=1}^{\infty}y_{j}=\lim_{ k \to \infty }x_{n_{k}}$ 收敛，由于 $(x_{n})$ 是 Cauchy 的，故 $(x_{n})$ 也收敛，即 $\mathcal{X}$ 是完备的。

我们已经见过许多 Banach 空间了，例如，设 $X$ 是拓扑空间，那么 $B(X)$ 和 $C_{b}(X)$ 在一致范数下是 Banach 空间，并且如果 $(X,\mathcal{M},\mu)$ 是测度空间，那么在 $L^{1}$ 范数下 $L^{1}(\mu)$ 就是一个 Banach 空间（定理 21.4.8）。

给定两个赋范空间 $\mathcal{X},\mathcal{Y}$，我们可以在 $\mathcal{X}\times \mathcal{Y}$ 上定义**乘积范数**

$$
\begin{gather}
\lVert (x,y) \rVert =\max(\lVert x \rVert ,\lVert y \rVert )
\end{gather}
$$

有时候，我们会使用 $\lVert x \rVert+\lVert y \rVert$ 或者 $(\lVert x \rVert^{2}+\lVert y \rVert^{2})^{1/2}$ 作为乘积范数，我们可以这样做的原因是这些范数都是等价的。

另一个相关的构造就是商空间。设 $\mathcal{X}$ 是一个向量空间，$\mathcal{M}$ 是它的一个子空间，定义 $x \sim y$ 如果 $x-y \in \mathcal{M}$，那么 $\sim$ 就是 $\mathcal{X}$ 上的一个等价关系，所有等价类 $x+\mathcal{M}$ 构成的空间 $\mathcal{X} / \mathcal{M}$ 就称为**商空间**。如果 $\mathcal{X}$ 是赋范空间，$\mathcal{M}$ 是闭集，那么我们可以在 $\mathcal{X} / \mathcal{M}$ 上定义范数：

$$
\begin{gather}
\lVert x+\mathcal{M} \rVert = \inf_{y \in \mathcal{M}} \lVert x+y \rVert 
\end{gather}
$$

称为**商范数**。

下面我们来看线性映射，在无限维空间中，线性映射不一定是连续的。不过，受定理 19.1.1 所启发，我们给出以下定义：

**定义 27.1.5** 有界（bounded）

设 $\mathcal{X},\mathcal{Y}$ 是赋范空间，线性映射 $T\colon \mathcal{X}\to \mathcal{Y}$ 是**有界的**，如果存在 $C\geq 0$ 使得对任意 $x \in \mathcal{X}$ 有

$$
\begin{gather}
\lVert Tx \rVert \leq C\lVert x \rVert 
\end{gather}
$$

注意，线性映射的有界性与一般函数的有界性不同，后者要求的是对任意 $x$ 有 $\lVert Tx \rVert\leq C$，任何线性映射都不满足这一要求。我们的定义表明，$T$ 在 $\mathcal{X}$ 中的有界集上有界。

**定理 27.1.6**

设 $\mathcal{X},\mathcal{Y}$ 是赋范空间，$T\colon \mathcal{X}\to \mathcal{Y}$ 是线性映射，则以下命题等价：

1. $T$ 是连续的。
2. $T$ 在 $0$ 处连续。
3. $T$ 是有界的。

**证明**

1 蕴含 2 是显然的。设 $T$ 在 $0$ 处连续，则存在 $\delta>0$ 使得对任意 $\lVert x \rVert\leq\delta$ 有 $\lVert Tx \rVert\leq 1$，于是当 $\lVert x \rVert\leq a$ 时有 $\lVert Tx \rVert\leq a\delta^{-1}$，从而 $\lVert Tx \rVert\leq\delta^{-1}\lVert x \rVert$，即 $T$ 是有界的。如果 $T$ 是有界的，那么对任意 $x \in \mathcal{X}$，有

$$
\begin{gather}
\lVert Ty-Tx \rVert =\lVert T(y-x) \rVert \leq C\lVert y-x \rVert 
\end{gather}
$$

从而 $T$ 是连续的，这就完成了证明。

我们将所有 $\mathcal{X}$ 到 $\mathcal{Y}$ 的有界线性映射构成的集合记作 $L(\mathcal{X},\mathcal{Y})$，我们可以验证它是一个向量空间，并且在其上可以定义范数：

$$
\begin{align}
\lVert T \rVert &= \sup \{ \lVert Tx \rVert \mid \lVert x \rVert =1 \} \\
&= \sup \left\{  \dfrac{\lVert Tx \rVert }{\lVert x \rVert } \middle| x\neq 0  \right\} \\
&= \inf \{ C \mid \lVert Tx \rVert \leq C\lVert x \rVert  \}
\end{align}
$$

称为**算子范数**，如果没有特殊指定，那么我们总是取该范数作为 $L(\mathcal{X},\mathcal{Y})$ 上的范数。

**定理 27.1.7**

设 $\mathcal{X},\mathcal{Y}$ 是赋范空间，如果 $\mathcal{Y}$ 是完备的，那么 $L(\mathcal{X},\mathcal{Y})$ 也是完备的。

**证明**

设 $(T_{n})$ 是 $L(\mathcal{X},\mathcal{Y})$ 中的 Cauchy 序列，则对任意 $x \in \mathcal{X}$，有

$$
\begin{gather}
\lVert T_{n}x-T_{m}x \rVert \leq \lVert T_{n}-T_{m} \rVert \lVert x \rVert 
\end{gather}
$$

因此 $(T_{n}x)$ 是 $\mathcal{Y}$ 中的 Cauchy 序列，于是收敛。定义 $T\colon \mathcal{X}\to \mathcal{Y}$ 为 $Tx=\lim_{ n \to \infty }T_{n}x$，$T$ 的线性性是显然的，对于有界性，由于 $(T_{n})$ 是 Cauchy 序列，于是对任意 $\varepsilon>0$，存在 $N$ 使得对任意 $n,m>N$ 有

$$
\begin{gather}
\lVert T_{n}x-T_{m}x \rVert \leq \lVert T_{n}-T_{m} \rVert \lVert x \rVert  \leq \varepsilon \lVert x \rVert 
\end{gather}
$$

令 $n\to \infty$，由范数的连续性得 $\lVert Tx-T_{m}x \rVert\leq\varepsilon \lVert x \rVert$，即 $\lVert Tx \rVert\leq(\lVert T_{m} \rVert+\varepsilon)\lVert x \rVert$，由于 $(T_{m})$ 是 Cauchy 序列，故有界，因此 $T \in L(\mathcal{X},\mathcal{Y})$，并且

$$
\begin{gather}
\lVert T-T_{m} \rVert=\sup_{x\neq 0} \dfrac{\lVert Tx-T_{m}x \rVert}{\lVert x \rVert}\leq\varepsilon
\end{gather}
$$

从而 $T_{m}\to T$，这就完成了证明。

另一个常用的性质如下：如果 $T \in L(\mathcal{X},\mathcal{Y}),S \in L(\mathcal{Y},\mathcal{Z})$，那么对任意 $x \in \mathcal{X}$ 有

$$
\begin{gather}
\lVert STx \rVert \leq \lVert S \rVert \lVert Tx \rVert \leq \lVert S \rVert \lVert T \rVert \lVert x \rVert 
\end{gather}
$$

即 $\lVert ST \rVert\leq \lVert S \rVert \lVert T \rVert$，从而 $ST \in L(\mathcal{X},\mathcal{Z})$. 特别地，$L(\mathcal{X},\mathcal{X})$ 是一个代数，并且当 $\mathcal{X}$ 完备时，它是一个 **Banach 代数**。另一个 Banach 代数的例子是 $C_{b}(X)$，其中 $X$ 是一个拓扑空间。

**定义 27.1.8** 可逆（invertible），等距映射（isometry）

设 $\mathcal{X},\mathcal{Y}$ 是赋范空间，$T \in L(\mathcal{X},\mathcal{Y})$，如果 $T$ 是双射并且 $T^{-1}$ 是有界的（即存在 $C>0$ 使得对任意 $x \in \mathcal{X}$ 有 $\lVert Tx \rVert\geq C\lVert x \rVert$），则称 $T$ 是**可逆的**，或称 $T$ 是一个**同构**。

称 $T \in L(\mathcal{X},\mathcal{Y})$ 是一个**等距映射**，如果对任意 $x \in \mathcal{X}$ 有 $\lVert Tx \rVert=\lVert x \rVert$.

一个等距映射必定是单射，但不一定是满射。如果 $T \in L(\mathcal{X},\mathcal{Y})$ 是等距映射，那么 $T$ 是从 $\mathcal{X}$ 到 $T[\mathcal{X}]$ 的同构，当 $T[\mathcal{X}]=\mathcal{Y}$ 时，$T$ 就称为一个**等距同构**。

# Section 2: 线性泛函

**定义 27.2.1** 线性泛函（linear functional），对偶空间（dual space）

设 $\mathcal{X}$ 是向量空间，线性映射 $f\colon \mathcal{X}\to \mathbb{F}$ 称为一个**线性泛函**。如果 $\mathcal{X}$ 是赋范空间，那么 $L(\mathcal{X},\mathbb{F})$ 称为 $\mathcal{X}$ 的**对偶空间**，记作 $\mathcal{X}^{*}$.

根据定理 27.1.7，$\mathcal{X}^{*}$ 在算子范数下是一个 Banach 空间。

如果 $\mathcal{X}$ 是 $\mathbb{C}$ 上的向量空间，那么它也是 $\mathbb{R}$ 上的向量空间，因此我们可以同时考虑 $\mathcal{X}$ 上的实线性泛函与复线性泛函，这两者的关系如下所示：

**定理 27.2.2**

设 $\mathcal{X}$ 是 $\mathbb{C}$ 上的向量空间，如果 $f$ 是一个复线性泛函，$u=\mathrm{Re}\ f$，那么 $u$ 是一个实线性泛函，并且 $f(x)=u(x)-iu(ix)$. 反之，如果 $u$ 是一个实线性泛函，那么定义为 $f(x)=u(x)-iu(ix)$ 的函数 $f$ 是一个复线性泛函。此外，如果 $\mathcal{X}$ 是赋范空间，那么 $\lVert f \rVert=\lVert u \rVert$.

**证明**

设 $f$ 是复线性泛函，那么 $u$ 显然是实线性的，并且 $\mathrm{Im}\ f=-\mathrm{Re}(if)$，因此 $f(x)=u(x)-iu(ix)$. 反之，如果 $f(x)=u(x)-iu(ix)$，那么 $f$ 是实线性的，并且 $f(ix)=u(ix)-iu(-x)=iu(x)+u(ix)=if(x)$，因此 $f$ 也是复线性的。

最后，对任意 $x \in \mathcal{X}$，我们有 $|u(x)|=|\mathrm{Re}\ f(x)|\leq|f(x)|$，于是 $\lVert u \rVert\leq \lVert f \rVert$. 反之，设 $f(x)\neq 0$ 且 $\alpha=\overline{\mathrm{sgn}\ f(x)}$，则有

$$
\begin{gather}
|f(x)|=\alpha f(x)=f(\alpha x)=u(\alpha x)\leq \lVert u \rVert \lVert \alpha x \rVert =\lVert u \rVert \lVert x \rVert 
\end{gather}
$$

因此 $\lVert f \rVert\leq \lVert u \rVert$，这就完成了证明。

到目前为止，我们还不清楚对任意赋范空间 $\mathcal{X}$，是否总是存在不为零的线性泛函。实际上，这样的线性泛函存在的事实是泛函分析中的一个基本定理，下面我们就来叙述并证明它。

**定义 27.2.3** 次线性泛函（sublinear functional）

设 $\mathcal{X}$ 是实向量空间，一个**次线性泛函**是函数 $p\colon \mathcal{X}\to \mathbb{R}$ 使得对任意 $x,y \in \mathcal{X}$ 和 $\lambda\geq 0$ 有：

- 次可加性：$p(x+y)\leq p(x)+p(y)$
- 齐次性：$p(\lambda x)=\lambda p(x)$

例如，每个半范数都是次线性泛函，反之则不然。通常，我们将 $x \in \mathcal{X}$ 张成的一维子空间记作 $\mathbb{F}x$.

**定理 27.2.4** Hahn-Banach 定理

设 $\mathcal{X}$ 是实向量空间，$p$ 是一个次线性泛函，$\mathcal{M}$ 是 $\mathcal{X}$ 的子空间，$f$ 是 $\mathcal{M}$ 上的线性泛函满足对任意 $x \in \mathcal{M}$ 有 $f(x)\leq p(x)$，那么存在 $\mathcal{X}$ 上的线性泛函 $F$ 使得对任意 $x \in \mathcal{X}$ 有 $F(x)\leq p(x)$ 且 $F|_{\mathcal{M}}=f$.

**证明**

取 $x \in \mathcal{X}\setminus \mathcal{M}$，我们首先证明 $f$ 可以扩张为 $\mathcal{M}+\mathbb{R}x$ 上的线性泛函 $g$ 使得 $g(x)\leq p(x)$. 设 $y_{1},y_{2} \in \mathcal{M}$，则有

$$
\begin{gather}
f(y_{1})+f(y_{2})=f(y_{1}+y_{2})\leq p(y_{1}+y_{2})\leq p(y_{1}-x)+p(x+y_{2})
\end{gather}
$$

即 $f(y_{1})-p(y_{1}-x)\leq p(x+y_{2})-f(y_{2})$，从而

$$
\begin{gather}
\sup_{y \in \mathcal{M}} (f(y)-p(y-x))\leq \inf_{y \in \mathcal{M}} (p(x+y)-f(y))
\end{gather}
$$

任取 $\alpha$ 介于两者之间，定义 $g\colon \mathcal{M}+\mathbb{R}x\to \mathbb{R}$ 为 $g(y+\lambda x)=f(y)+\lambda\alpha$，则 $g$ 显然是线性的，并且 $g|_{\mathcal{M}}=f$，于是对于 $y \in \mathcal{M}$ 有 $g(y)\leq p(y)$. 此外，对任意 $y \in \mathcal{M}$ 和 $\lambda\geq 0$，有

$$
\begin{align}
g(y+\lambda x)&=\lambda(f(y / \lambda)+\alpha) \\
&\leq \lambda(f(y / \lambda)+p(x+y / \lambda)-f(y / \lambda)) \\
&=p(y+\lambda x)
\end{align}
$$

对于 $\lambda=-\mu<0$，有

$$
\begin{align}
g(y+\lambda x) &= \mu(f(y / \mu)-\alpha) \\
&\leq \mu(f(y / \mu)-f(y / \mu)+p(y / \mu-x)) \\
&= p(y-\mu x)=p(y+\lambda x)
\end{align}
$$

因此在 $\mathcal{M}+\mathbb{R}x$ 上有 $g\leq p$.

设 $\mathcal{F}$ 由 $f$ 的线性扩张 $F$ 使得 $F\leq p$ 组成，在其上按定义域的包含关系定义偏序。由于 $f$ 自身是 $f$ 的扩张，因此 $\mathcal{F}$ 是非空的。设 $\{ F_{l} \}$ 是 $\mathcal{F}$ 中的一个链，其定义域为 $\{ \mathcal{D}_{l} \}$，令 $\mathcal{D}=\bigcup_{l} \mathcal{D}_{l}$，定义 $F\colon \mathcal{D}\to \mathbb{R}$ 如下：对任意 $x \in \mathcal{D}$，存在 $l$ 使得 $x \in \mathcal{D}_{l}$，定义 $F(x)=F_{l}(x)$.

由于每个 $F_{l} \in \mathcal{F}$，故 $F|_{\mathcal{M}}=f,F\leq p$，并且对于 $x,y \in \mathcal{D}$，根据全序性，存在 $l$ 使得 $x,y \in \mathcal{D}_{l}$，由 $F_{l}$ 的线性性知 $F$ 是线性的，从而 $F$ 是 $\{ F_{l} \}$ 的上界。根据 Zorn 引理，存在 $\mathcal{F}$ 的极大元 $F^{*}$，其定义域为 $\mathcal{D}^{*}$，假设 $\mathcal{D}^{*}\neq \mathcal{X}$，取 $x \in \mathcal{X}\setminus\mathcal{D}^{*}$，则根据前面的论述，它可以扩张到 $\mathcal{D}^{*}+\mathbb{R}x$ 上，这与 $F^{*}$ 的极大性矛盾，于是 $F^{*}$ 就是要求的扩张。

如果 $p$ 是一个半范数，那么 $f\leq p$ 就等价于 $|f|\leq p$，因为 $|f(x)|=\pm f(x)=f(\pm x)$，并且 $p(-x)=p(x)$，在这种情况下我们可以将 Hahn-Banach 定理推广到复线性泛函：

**定理 27.2.5** 复 Hahn-Banach 定理

设 $\mathcal{X}$ 是复向量空间，$p$ 是一个半范数，$\mathcal{M}$ 是 $\mathcal{X}$ 的子空间，$f$ 是 $\mathcal{M}$ 上的复线性泛函使得对任意 $x \in \mathcal{M}$ 有 $|f(x)|\leq p(x)$，那么存在 $\mathcal{X}$ 上的复线性泛函 $F$ 使得对任意 $x \in \mathcal{X}$ 有 $|F(x)|\leq p(x)$ 且 $F|_{\mathcal{M}}=f$.

**证明**

取 $u=\mathrm{Re}\ f$，根据 Hahn-Banach 定理，存在 $u$ 的线性扩张 $U$ 使得 $|U|\leq p$，令 $F(x)=U(x)-iU(ix)$，则 $F$ 是 $\mathcal{X}$ 上的复线性泛函，并且 $F|_{\mathcal{M}}=f$. 此外，对任意 $x \in \mathcal{X}$，令 $\alpha=\overline{\mathrm{sgn}\ F(x)}$，则有

$$
\begin{gather}
|F(x)|=\alpha F(x)=F(\alpha x)=U(\alpha x)\leq p(\alpha x)=p(x)
\end{gather}
$$

这就完成了证明。

下面我们给出 Hahn-Banach 定理的一些应用，我们主要关注复向量空间上的结论，但同样的论证过程也可以应用到实向量空间上。

**定理 27.2.6**

设 $\mathcal{X}$ 是赋范空间，则有：

1. 设 $\mathcal{M}$ 是 $\mathcal{X}$ 的闭子空间，$x \in \mathcal{X}\setminus\mathcal{M}$，则存在 $f \in \mathcal{X}^{*}$ 使得 $f(x)\neq 0$ 且 $f|_{\mathcal{M}}=0$. 事实上，如果 $\delta=\inf_{y \in \mathcal{M}}\lVert x-y \rVert$，则可以取 $f \in \mathcal{X}^{*}$ 使得 $\lVert f \rVert=1$ 且 $f(x)=\delta$.
2. 如果 $x \in \mathcal{X},x\neq 0$，则存在 $f \in \mathcal{X}^{*}$ 使得 $\lVert f \rVert=1$ 且 $f(x)=\lVert x \rVert$.
3. $\mathcal{X}$ 上的有界线性泛函是分离点的。
4. 如果 $x \in \mathcal{X}$，定义 $\hat{x}\colon \mathcal{X}^{*}\to \mathbb{C}$ 为 $\hat{x}(f)=f(x)$，则函数 $x\mapsto \hat{x}$ 是从 $\mathcal{X}$ 到 $\mathcal{X}^{**}$ 的等距映射。

**证明**

在 $\mathcal{M}+\mathbb{C}x$ 上定义 $f$ 为 $f(y+\lambda x)=\lambda\delta$，其中 $y \in \mathcal{M},\lambda \in \mathbb{C}$，于是 $f(x)=\delta\neq 0,f|_{\mathcal{M}}=0$，并且当 $\lambda\neq 0$ 时有

$$
\begin{gather}
|f(y+\lambda x)|=|\lambda|\delta\leq |\lambda|\lVert \lambda^{-1}y+x \rVert=\lVert y+\lambda x \rVert 
\end{gather}
$$

于是 $\lVert f \rVert=1$，取 $p(x)=\lVert x \rVert$ 然后应用 Hahn-Banach 定理即证 1.

将 1 应用到 $\mathcal{M}=\{ 0 \}$ 上即证 2. 如果 $x\neq y$，根据 2 可得存在 $f \in \mathcal{X}^{*}$ 使得 $f(x-y)=\lVert x-y \rVert\neq 0$，即 $f(x)\neq f(y)$，这就证明了 3.

对于 4，显然 $\hat{x}$ 和 $x\mapsto \hat{x}$ 都是线性的，并且 $|\hat{x}(f)|=|f(x)|\leq \lVert f \rVert\lVert x \rVert$，于是 $\lVert \hat{x} \rVert\leq \lVert x \rVert$. 另一边，2 表明存在 $f$ 使得 $\lVert f \rVert=1$ 且 $\hat{x}(f)=\lVert x \rVert$，于是 $\lVert \hat{x} \rVert\geq \lVert x \rVert$，从而 $x\mapsto \hat{x}$ 是一个等距映射。

令 $\hat{\mathcal{X}}=\{ \hat{x} \mid x \in \mathcal{X} \}$，则它是 $\mathcal{X}^{**}$ 的一个子集。由于 $\mathcal{X}^{**}$ 是完备的，故 $\hat{\mathcal{X}}$ 的闭包 $\overline{\hat{\mathcal{X}}}$ 是一个 Banach 空间，并且函数 $x\mapsto \hat{x}$ 将 $\mathcal{X}$ 作为一个稠密子集嵌入 $\overline{\hat{\mathcal{X}}}$. $\overline{\hat{\mathcal{X}}}$ 就称为 $\mathcal{X}$ 的**完备化**，因为如果 $\mathcal{X}$ 自身是 Banach 空间，那么有 $\overline{\hat{\mathcal{X}}}=\hat{\mathcal{X}}$.

如果 $\mathcal{X}$ 是有限维的，那么显然有 $\hat{\mathcal{X}}=\mathcal{X}^{**}$，因为这两者的维数是相同的。在无限维空间上，则不一定有 $\hat{\mathcal{X}}=\mathcal{X}^{**}$，如果这个等式成立，那么就称 $\mathcal{X}$ 是**自反的**。通常我们把 $x$ 和 $\hat{x}$ 等同起来，此时 $\mathcal{X}$ 就是 $\mathcal{X}^{**}$ 的一个子集，那么自反性就表明 $\mathcal{X}^{**}=\mathcal{X}$.

我们回到 Hahn-Banach 定理，本质上来说，该定理允许我们将线性泛函在局部（子空间上）的行为推广到全局，下面我们给出另一个类似的扩张定理。

**定理 27.2.7** Krein 扩张定理（Krein extension theorem）

设 $\mathcal{X}$ 是实向量空间，$\mathcal{P}\subset \mathcal{X}$ 满足：

1. 如果 $x,y \in \mathcal{P}$，那么 $x+y \in \mathcal{P}$
2. 如果 $x \in \mathcal{P},\lambda\geq 0$，那么 $\lambda x \in \mathcal{P}$
3. 如果 $x \in \mathcal{P},-x \in \mathcal{P}$，那么 $x=0$

在 $\mathcal{X}$ 上定义 $x\leq y$ 当且仅当 $y-x \in \mathcal{P}$，则 $\leq$ 是一个偏序。设 $\mathcal{M}$ 是 $\mathcal{X}$ 的子空间使得对任意 $x \in \mathcal{X}$，存在 $y \in \mathcal{M}$ 使得 $x\leq y$，那么如果 $f$ 是 $\mathcal{M}$ 上的线性泛函满足对任意 $x \in \mathcal{M}\cap \mathcal{P}$ 有 $f(x)\geq 0$，则存在 $\mathcal{X}$ 上的线性泛函 $F$ 使得对任意 $x \in \mathcal{P}$ 有 $F(x)\geq 0$ 并且 $F|_{\mathcal{M}}=f$.

**证明**

根据 $\mathcal{P}$ 的定义，显然 $\leq$ 是一个偏序。任取 $x \in \mathcal{X}$，定义

$$
\begin{gather}
p(x)=\inf \{ f(y) \mid y \in \mathcal{M}, x\leq y \}
\end{gather}
$$

设 $x \in \mathcal{X}$，则存在 $z \in \mathcal{M}$ 使得 $-x\leq z$，即 $x+z \in \mathcal{P}$，再取 $y \in \mathcal{M}$ 满足 $x\leq y$，则 $y-x \in \mathcal{P}$，从而 $y+z \in \mathcal{M}\cap\mathcal{P}$，于是 $f(y+z)\geq 0$，即 $f(y)\geq-f(z)$，对 $y$ 取下确界则有 $p(x)\geq-f(z)>-\infty$.

设 $\lambda\geq 0$，则 $p(\lambda x)=\inf\{ f(\lambda y) \mid y \in \mathcal{M},\lambda x\leq \lambda y \}=\lambda p(x)$. 另一边，设 $x,y \in \mathcal{X}$，则存在 $z_{1},z_{2}\in \mathcal{M}$ 使得 $f(z_{1})<p(x)+\varepsilon,f(z_{2})<p(y)+\varepsilon$，由于 $x+y\leq z_{1}+z_{2}$，故 $p(x+y)\leq f(z_{1}+z_{2})<p(x)+p(y)+2\varepsilon$，即 $p(x+y)\leq p(x)+p(y)$，从而 $p$ 是一个次线性泛函。

设 $x \in \mathcal{M}$，取 $y \in \mathcal{M}$ 使得 $x\leq y$，则 $y-x \in \mathcal{M}\cap \mathcal{P}$，故 $f(y-x)=f(y)-f(x)\geq 0$，从而 $f(x)\leq p(x)$，根据 Hahn-Banach 定理，存在 $\mathcal{X}$ 上的线性泛函 $F$ 使得 $F(x)\leq p(x)$ 且 $F|_{\mathcal{M}}=f$. 再设 $x \in \mathcal{P}$，由于 $0-(-x)=x \in \mathcal{P}$，故 $-x\leq 0$，从而 $p(-x)\leq f(0)=0$，于是 $-F(x)=F(-x)\leq p(-x)\leq 0$，即 $F(x)\geq 0$，这就完成了证明。

注意，Hahn-Banach 定理和 Krein 扩张定理都是“纯代数”的定理，也就是说它们不受 $\mathcal{X}$ 上的拓扑影响，而只和向量空间的结构相关。正是这一特征使得它们的应用非常广泛。

# Section 3: 泛函分析基本定理

在本节中，我们将给出拓扑学中的一个重要定理：Baire 纲定理，它可以用来证明泛函分析中的三个主要定理：开映射定理、闭图像定理以及一致有界原理，它们与 Hahn-Banach 定理合称为泛函分析的基本定理。

**定理 27.3.1** Baire 纲定理（Baire category theorem）

设 $X$ 是一个完备度量空间，则有：

1. 如果 $(U_{n})_{n=1}^{\infty}$ 是 $X$ 中的一列稠密开子集，那么 $\bigcap_{n=1}^{\infty}U_{n}$ 在 $X$ 中稠密。
2. $X$ 不是可数个无处稠密集的并集。

**证明**

我们要证如果 $W\subset X$ 是一个非空开集，那么 $W\cap \bigcap_{n=1}^{\infty}U_{n}\neq \varnothing$. 由于 $U_{1}$ 是开集，故存在 $x_{0} \in X$ 和 $0<r_{0}<1$ 使得 $B(x_{0},r_{0})\subset U_{1}\cap W$，下面递归地取 $x_{n}\in X$ 和 $0<r_{n}<2^{-n}$ 使得 $\overline{B(x_{n},r_{n})}\subset U_{n}\cap B(x_{n-1},r_{n-1})$，于是对任意 $N$ 和 $n,m>N$，有 $x_{n},x_{m}\in B(x_{N},r_{N})$，又因为 $r_{n}\to 0$，故序列 $(x_{n})$ 是 Cauchy 的，根据 $X$ 的完备性知 $x=\lim_{ n \to \infty }x_{n}$ 存在。

由于对任意 $n>N$ 有 $x_{n}\in B(x_{N},r_{N})$，故

$$
x \in \overline{B(x_{N},r_{N})}\subset U_{N}\cap B(x_{N-1},r_{N-1})\subset \dots \subset U_{N}\cap B(x_{0},r_{0})\subset U_{N}\cap W
$$

对任意 $N$ 都成立，因此 $\bigcap_{n=1}^{\infty}U_{n}$ 是稠密的。

设 $(E_{n})_{n=1}^{\infty}$ 是 $X$ 中的一列无处稠密的子集，则 $((\overline{E_{n}})^{c})$ 就是一列稠密开子集，从而 $\bigcap_{n=1}^{\infty}(\overline{E_{n}})^{c}\neq \varnothing$，因此 $\bigcup_{n=1}^{\infty}E_{n}\subset \bigcup_{n=1}^{\infty}\overline{E_{n}}\neq X$.

该定理的名字来源于 Baire 对集合的分类上：如果 $X$ 是一个拓扑空间，$E\subset X$ 称为**第一纲的**，如果它是可数个无处稠密集的并，否则就称为**第二纲的**。因此 Baire 纲定理表明，每个完备度量空间都是第二纲的。我们也称第一纲的集合为**贫集**，一个贫集的补集称为**剩余集**。

Baire 纲定理通常可用于证明具有某种性质的对象的存在性，我们只需找到一个合适的完备度量空间，然后证明不具有这种性质的对象构成的集合是第一纲的即可。

下面我们使用 Baire 纲定理来研究 Banach 空间中线性映射的行为。

**定义 27.3.2** 开映射（open mapping）

设 $X,Y$ 是拓扑空间，称映射 $f\colon X\to Y$ 是**开的**，如果对任意开集 $U\subset X$，$f[U]$ 在 $Y$ 中是开的。

特别地，对于赋范空间中的线性映射 $T$，由于 $T$ 与平移和拉伸可交换，因此 $T$ 是开的当且仅当 $T[B(0,1)]$ 包含了一个开球 $B(0,r)$.

**定理 27.3.3** 开映射定理（open mapping theorem）

设 $\mathcal{X},\mathcal{Y}$ 是 Banach 空间，如果 $T \in L(\mathcal{X},\mathcal{Y})$ 是满射，那么 $T$ 是开的。

**证明**

令 $B_{r}=B(0,r)\subset \mathcal{X}$，我们需要证明 $T[B_{1}]$ 在 $\mathcal{Y}$ 中是开的。由于 $\mathcal{X}=\bigcup_{n=1}^{\infty}B_{n}$ 且 $T$ 是满射，故 $\mathcal{Y}=\bigcup_{n=1}^{\infty}T[B_{n}]$. 由于 $\mathcal{Y}$ 是完备的，并且 $y\mapsto ny$ 是将 $T[B_{1}]$ 映射到 $T[B_{n}]$ 的同胚，因此由 Baire 纲定理知 $T[B_{1}]$ 不是无处稠密的，也就是说存在 $y_{0}\in \mathcal{Y}$ 和 $r>0$ 使得 $B(y_{0},4r)\subset  \overline{T[B_{1}]}$. 取 $y_{1}=Tx_{1} \in T[B_{1}]$ 使得 $\lVert y_{1}-y_{0} \rVert<2r$，则 $B(y_{1},2r)\subset B(y_{0},4r)$，因此当 $\lVert y \rVert<2r$ 时有 $y+y_{1} \in B(y_{1},2r)$，因此

$$
\begin{gather}
y=(y+y_{1})-Tx_{1} \in \overline{T[-x_{1}+B_{1}]}\subset  \overline{T[B_{2}]}
\end{gather}
$$

两边同除以 $2$，则有对任意 $\lVert y \rVert<r$ 有 $y \in \overline{T[B_{1}]}$.

对任意 $n\geq 1$，我们有对任意 $\lVert y \rVert<r 2^{-n}$ 有 $y \in \overline{T[B_{2^{-n}}]}$. 设 $\lVert y \rVert<r / 2$，递归地取 $x_{n} \in B_{2^{-n}}$ 使得 $\left\lVert  y-\sum_{j=1}^{n}Tx_{j}  \right\rVert<r 2^{-n-1}$，则 $\sum_{j=1}^{\infty}x_{n}$ 绝对收敛，由 $\mathcal{X}$ 的完备性知存在 $x=\sum_{j=1}^{\infty}x_{n}$，从而 $\lVert x \rVert<\sum_{j=1}^{\infty}2^{-j}=1$，并且 $y=\sum_{j=1}^{\infty}Tx_{j}=Tx$. 也就是说，$T[B_{1}]$ 包含了所有 $\lVert y \rVert<r / 2$，从而 $T[B_{1}]$ 是开集，这就完成了证明。

当 $T$ 是双射时，$T^{-1}$ 的连续性就等价于 $T$ 的开性，因此我们有推论：

**定理 27.3.4**

设 $\mathcal{X},\mathcal{Y}$ 是 Banach 空间，如果 $T \in L(\mathcal{X},\mathcal{Y})$ 是双射，那么 $T$ 是可逆的，即 $T^{-1}\in L(\mathcal{Y},\mathcal{X})$.

有了开性，自然也有闭性，我们给出以下定义：

**定义 27.3.5** 闭映射（closed mapping）

设 $\mathcal{X},\mathcal{Y}$ 是赋范空间，线性映射 $T\colon \mathcal{X}\to \mathcal{Y}$ 是**闭的**，如果

$$
\begin{gather}
T=\{ (x,y) \in \mathcal{X}\times \mathcal{Y} \mid y=Tx \}
\end{gather}
$$

作为 $\mathcal{X}\times \mathcal{Y}$ 的子集是闭的。

为了区分作为映射的 $T$ 和作为 $\mathcal{X}\times \mathcal{Y}$ 子集的 $T$（$T$ 的集合论定义），我们通常将后者记作 $\Gamma(T)$，称为 $T$ 的**图像**。从集合论角度来看，$T$ 和它的图像是相同的，我们做这一区分只是为了论述更清晰。

显然，如果 $T$ 是连续的，那么 $T$ 一定是闭映射。当 $\mathcal{X},\mathcal{Y}$ 是 Banach 空间时，反方向的命题也是正确的，如下所示：

**定理 27.3.6** 闭图像定理（closed graph theorem）

设 $\mathcal{X},\mathcal{Y}$ 是 Banach 空间，线性映射 $T\colon \mathcal{X}\to \mathcal{Y}$ 是闭的，那么 $T$ 是有界的。

**证明**

定义投影映射为 $\pi_{1}(x,Tx)=x,\pi_{2}(x,Tx)=Tx$，显然 $\pi_{1} \in L(\Gamma(T),\mathcal{X})$，$\pi_{2}\in L(\Gamma(T),\mathcal{Y})$. 由于 $\mathcal{X},\mathcal{Y}$ 是完备的，因此 $\mathcal{X}\times \mathcal{Y}$ 也是完备的，又由于 $\Gamma(T)$ 是闭的，因此 $\Gamma(T)$ 是完备的。映射 $\pi_{1}$ 是 $\Gamma(T)$ 到 $\mathcal{X}$ 的双射，根据定理 27.3.4 得 $\pi_{1}^{-1}\in L(\mathcal{X},\Gamma(T))$，从而 $T=\pi_{2}\circ \pi_{1}^{-1} \in L(\mathcal{X},\mathcal{Y})$，即证。

$T$ 的连续性表明如果 $x_{n}\to x$ 那么 $Tx_{n}\to Tx$，而 $T$ 的闭性则表明如果 $x_{n}\to x$ 且 $Tx_{n}\to y$，则有 $y=Tx$. 因此闭图像定理的重要性在于，当我们证明 $Tx_{n}\to Tx$ 时，我们可以假设 $Tx_{n}$ 收敛于某个 $y$，然后我们只需证明 $y=Tx$ 即可。这通常可以为我们避免很多麻烦。

本节的最后一个结果是一致有界原理，它允许我们从一些点处的有界性推出一致有界性。

**定理 27.3.7** 一致有界原理（uniform boundedness principle）

设 $\mathcal{X},\mathcal{Y}$ 是赋范空间，$\mathcal{A}\subset L(\mathcal{X},\mathcal{Y})$，则有：

1. 如果在一个第二纲集上有 $\sup_{T \in \mathcal{A}}\lVert Tx \rVert<+\infty$，那么 $\sup_{T \in \mathcal{A}}\lVert T \rVert<+\infty$.
2. 如果 $\mathcal{X}$ 是 Banach 空间，并且对任意 $x \in \mathcal{X}$ 有 $\sup_{T \in \mathcal{A}}\lVert Tx \rVert<+\infty$，那么 $\sup_{T \in \mathcal{A}}\lVert T \rVert<+\infty$.

**证明**

令

$$
\begin{gather}
E_{n}=\{ x \in \mathcal{X} \mid \sup_{T \in \mathcal{A}} \lVert Tx \rVert \leq n \}=\bigcap_{T \in \mathcal{A}} \{ x \in \mathcal{X} \mid \lVert Tx \rVert \leq n \}
\end{gather}
$$

则 $E_{n}$ 是闭集，并且存在 $n$ 使得 $E_{n}$ 包含闭球 $\overline{B(x_{0},r)}$，于是对任意 $\lVert x \rVert\leq r$ 有 $x+x_{0} \in E_{n}$，从而

$$
\begin{gather}
\lVert Tx \rVert =\lVert T(x+x_{0})-Tx_{0} \rVert  \leq \lVert T(x+x_{0}) \rVert +\lVert Tx_{0} \rVert \leq 2n
\end{gather}
$$

因此对任意 $\lVert x \rVert\leq r$ 有 $\sup_{T \in \mathcal{A}}\lVert Tx \rVert\leq 2n$，从而 $\sup_{T \in \mathcal{A}}\lVert T \rVert\leq 2n / r$，这就证明了 1. 根据 Baire 纲定理即证 2.

# Section 4: 拓扑向量空间

除了范数拓扑以外，我们经常还会用到其它的拓扑，只需保证其与向量空间的运算（加法和数乘）相容即可。精确地说，就是：

**定义 27.4.1** 拓扑向量空间（topological vector space）

**拓扑向量空间** $(\mathcal{X},\mathcal{T})$ 包含 $\mathbb{F}$ 上的向量空间 $\mathcal{X}$，以及 $\mathcal{X}$ 上的拓扑 $\mathcal{T}$，使得函数 $(x,y)\mapsto x+y$ 和 $(\lambda,x)\mapsto\lambda x$ 是连续的。

**定义 27.4.2** 局部凸的（locally convex）

一个拓扑向量空间称为**局部凸的**，如果其拓扑有一个由凸集（集合 $A$ 是凸集如果对任意 $x,y \in A,0<t<1$ 有 $tx+(1-t)y \in A$）构成的基。

在实际应用中，大多数拓扑向量空间都是局部凸且 Hausdorff 的。此外，最常见的局部凸空间通常是由半范数生成的：

**定理 27.4.3**

设 $\{ p_{\alpha} \}_{\alpha \in A}$ 是向量空间 $\mathcal{X}$ 上的一族半范数，$x \in \mathcal{X},\alpha \in A,\varepsilon>0$，令

$$
\begin{gather}
U_{x\alpha \varepsilon}=\{ y \in \mathcal{X} \mid p_{\alpha}(y-x)<\varepsilon\}
\end{gather}
$$

并且令 $\mathcal{T}$ 为所有集合 $U_{x\alpha \varepsilon}$ 生成的拓扑，则有：

1. 对任意 $x \in \mathcal{X}$，集合 $U_{x\alpha\varepsilon},\alpha \in A,\varepsilon>0$ 的有限交构成了 $x$ 的一个邻域基。
2. 设 $\langle x_{i} \rangle_{i \in I}$ 是 $\mathcal{X}$ 中的网，那么 $x_{i}\to x$ 当且仅当对任意 $\alpha \in A$ 有 $p_{\alpha}(x_{i}-x)\to 0$.
3. $(\mathcal{X},\mathcal{T})$ 是一个局部凸的拓扑向量空间。

**证明**

(1). 如果 $x \in \bigcap_{j=1}^{k}U_{x_{j}\alpha_{j}\varepsilon_{j}}$，令 $\delta_{j}=\varepsilon_{j}-p_{\alpha_{j}}(x_{j}-x)$，根据三角不等式，我们有 $x \in \bigcap_{j=1}^{k}U_{x\alpha_{j}\delta_{j}}\subset \bigcap_{j=1}^{k}U_{x_{j}\alpha_{j}\varepsilon_{j}}$，于是根据定理 25.1.6 就证明了 1.

(2). 对任意 $x,\alpha,\varepsilon$，显然 $p_{\alpha}(x_{i}-x)\to 0$ 当且仅当 $\langle x_{i} \rangle$ 最终在 $U_{x\alpha\varepsilon}$ 中，又根据 1 知 $U_{x\alpha\varepsilon}$ 构成了 $x$ 的邻域基，这就证明了 2.

(3). 设 $x_{i}\to x,y_{i}\to y$，则根据三角不等式有

$$
\begin{gather}
p_{\alpha}((x_{i}+y_{i})-(x+y))\leq p_{\alpha}(x_{i}-x)+p_{\alpha}(y_{i}-y)\to 0
\end{gather}
$$

因此 $x_{i}+y_{i}\to x+y$，从而根据定理 25.3.4 知向量加法是连续的。再设 $\lambda_{i}\to\lambda$，则 $\langle \lambda_{i} \rangle$ 最终满足 $|\lambda_{i}|\leq|\lambda|+1=C$，于是当 $i$ 足够大时有

$$
\begin{align}
p_{\alpha}(\lambda_{i}x_{i}-\lambda x)&\leq p_{\alpha}(\lambda_{i}(x_{i}-x))+p_{\alpha}((\lambda_{i}-\lambda)x) \\
&\leq Cp_{\alpha}(x_{i}-x)+|\lambda_{i}-\lambda|p_{\alpha}(x)\to 0
\end{align}
$$

因此 $\lambda_{i}x_{i}\to\lambda x$，从而数乘也是连续的。最后，设 $y,z \in U_{x\alpha\varepsilon}$，则

$$
\begin{gather}
p_{\alpha}(x-(ty+(1-t)z))\leq tp_{\alpha}(x-y)+(1-t)p_{\alpha}(x-z)<\varepsilon
\end{gather}
$$

因此 $ty+(1-t)z \in U_{x\alpha\varepsilon}$，从而 $U_{x\alpha\varepsilon}$ 是凸集，由 1 就知 $(\mathcal{X},\mathcal{T})$ 是一个局部凸的拓扑向量空间。

在上述定理中，半范数 $p_{\alpha}$ 就起到了范数的作用，于是我们可以证明定理 27.1.6 的一个对应版本：

**定理 27.4.4**

设 $\mathcal{X},\mathcal{Y}$ 是拓扑向量空间，其上的拓扑分别由半范数 $\{ p_{\alpha} \}_{\alpha \in A}$ 和 $\{ q_{\beta} \}_{\beta \in B}$ 生成，如果 $T\colon \mathcal{X}\to \mathcal{Y}$ 是一个线性映射，那么 $T$ 是连续的当且仅当对任意 $\beta \in B$，存在 $\alpha_{1},\dots,\alpha_{k}\in A$ 和 $C>0$ 使得 $q_{\beta}(Tx)\leq C\sum_{j=1}^{k}p_{\alpha_{j}}(x)$.

**证明**

如果后一个结论成立，设 $\langle x_{i} \rangle$ 是收敛至 $x$ 的网，根据定理 27.4.3 得 $p_{\alpha}(x_{i}-x)\to 0$，则对任意 $\beta$ 有 $q_{\beta}(Tx_{i}-Tx)\to 0$，从而 $Tx_{i}\to Tx$，即 $T$ 是连续的。

反之，如果 $T$ 是连续的，那么对任意 $\beta$，存在 $0 \in \mathcal{X}$ 的邻域 $U$ 使得对任意 $x \in U$ 有 $q_{\beta}(Tx)<1$. 根据定理 27.4.3，我们可以设 $U=\bigcap_{j=1}^{k}U_{0 \alpha_{j}\varepsilon_{j}}$，令 $\varepsilon=\min_{j}\varepsilon_{j}$，则当 $p_{\alpha_{j}}(x)<\varepsilon$ 时有 $q_{\beta}(Tx)<1$ 对任意 $j$ 成立。

任取 $x \in \mathcal{X}$，如果存在 $j$ 使得 $p_{\alpha_{j}}(x)>0$，令 $y= \dfrac{\varepsilon x}{\sum_{j=1}^{k}p_{\alpha_{j}}(x)}$，则 $p_{\alpha_{j}}(y)<\varepsilon$，从而

$$
\begin{gather}
q_{\beta}(Tx)=\sum_{j=1}^{k} \varepsilon^{-1} p_{\alpha_{j}}(x)q_{\beta}(Ty)\leq \varepsilon^{-1} \sum_{j=1}^{k} p_{\alpha_{j}}(x)
\end{gather}
$$

如果对任意 $j$ 有 $p_{\alpha_{j}}(x)=0$，则对任意 $r>0$ 有 $p_{\alpha_{j}}(rx)=0$，从而 $q_{\beta}(T(rx))=rq_{\beta}(Tx)<1$，因此 $q_{\beta}(Tx)=0$，同样满足上述不等式，这就证明了 $T$ 在 $0$ 处连续。由于线性映射 $T$ 与平移和伸缩可交换，因此 $T$ 在 $\mathcal{X}$ 上连续，这就完成了证明。

对于由半范数生成的拓扑向量空间 $\mathcal{X}$，根据定理 27.4.4，其上的一个线性泛函 $f$ 是连续的当且仅当 $|f(x)|\leq C\sum_{j=1}^{k}p_{\alpha_{j}}(x)$，由于有限个半范数的和也是半范数，因此 Hahn-Banach 定理保证了存在足够多的 $\mathcal{X}$ 上的连续线性泛函，它们组成了 $\mathcal{X}$ 的对偶空间 $\mathcal{X}^{*}$. 在 $\mathcal{X}^{*}$ 上，我们可以构造多种不同的拓扑，它们各有各的用处和特性，下面我们给出最常用的几个。

我们从线性映射生成的弱拓扑开始，它和半范数生成的拓扑有如下关系：

**定理 27.4.5**

设 $\mathcal{X}$ 是向量空间，$\mathcal{Y}$ 是赋范空间，$T_{\alpha}\colon \mathcal{X}\to \mathcal{Y}$ 是一族线性映射，那么 $\{ T_{\alpha} \}$ 生成的弱拓扑 $\mathcal{T}$ 等于半范数族 $\{ x\mapsto \lVert T_{\alpha}x \rVert \}$ 生成的拓扑 $\mathcal{T}'$.

**证明**

首先证明 $\mathcal{T}'\subset \mathcal{T}$. 由于半范数 $p_{\alpha}(x)=\lVert T_{\alpha}x \rVert$ 是 $T_{\alpha}$ 与范数函数 $\lVert \cdot \rVert$ 的复合，$\lVert \cdot \rVert$ 在 $\mathcal{Y}$ 中连续，并且 $\mathcal{T}$ 使得 $T_{\alpha}$ 连续，故 $\mathcal{T}$ 使得 $p_{\alpha}$ 连续，但 $\mathcal{T}'$ 是使得所有 $p_{\alpha}$ 连续的最粗的拓扑，因此 $\mathcal{T}'\subset \mathcal{T}$.

再证 $\mathcal{T}\subset \mathcal{T}'$. 固定 $\alpha$，我们要证 $T_{\alpha}$ 在 $\mathcal{T}'$ 拓扑下连续，这样由弱拓扑的定义即证。

设 $x_{0}\in \mathcal{X},\varepsilon>0$，取 $U=\{ y \in \mathcal{X} \mid p_{\alpha}(x-x_{0})<\varepsilon \} \in \mathcal{T}'$，则当 $x \in U$ 时有

$$
\begin{gather}
\lVert T_{\alpha}x-T_{\alpha}x_{0} \rVert =\lVert T_{\alpha}(x-x_{0}) \rVert =p_{\alpha}(x-x_{0})<\varepsilon
\end{gather}
$$

因此 $T_{\alpha}$ 在 $x_{0}$ 处连续，从而 $T_{\alpha}$ 在 $\mathcal{X}$ 上连续，这就完成了证明。

对于赋范空间 $\mathcal{X}$，其上的**弱拓扑**就是有界线性泛函 $\mathcal{X}^{*}$ 生成的拓扑，于是关于这个拓扑的收敛性自然就称为**弱收敛**。也就是说，对于 $\mathcal{X}$ 上的网 $\langle x_{\alpha} \rangle$，$x_{\alpha}$ 弱收敛于 $x$ 当且仅当对任意 $f \in \mathcal{X}^{*}$ 有 $f(x_{\alpha})\to f(x)$.

接下来，对于 $\mathcal{X}^{*}$，它上面的弱拓扑正是 $\mathcal{X}^{**}$ 生成的拓扑，其中我们更感兴趣的是由 $\mathcal{X}$（作为 $\mathcal{X}^{**}$ 的一个子空间）生成的拓扑，通常称为**弱**$^{*}$**拓扑**。它也是 $\mathcal{X}^{*}$ 上的逐点收敛拓扑：$f_{\alpha}\to f$ 当且仅当对任意 $x \in \mathcal{X}$ 有 $f_{\alpha}(x)\to f(x)$.

有弱拓扑，自然也有强拓扑。设 $\mathcal{X},\mathcal{Y}$ 是 Banach 空间，在 $L(\mathcal{X},\mathcal{Y})$ 上可以定义**强算子拓扑**：由求值映射 $T\mapsto Tx,x \in \mathcal{X}$ 生成的拓扑，以及**弱算子拓扑**：由线性泛函 $T\mapsto f(Tx),x \in \mathcal{X},f \in \mathcal{Y}^{*}$ 生成的拓扑。换句话说，$T_{\alpha}$ 强收敛于 $T$ 当且仅当对任意 $x \in \mathcal{X}$ 有 $T_{\alpha}x\to Tx$，而 $T_{\alpha}$ 弱收敛于 $T$ 当且仅当对任意 $x \in \mathcal{X}$ 有 $T_{\alpha}x$ 弱收敛于 $Tx$.

下面我们给出一个关于强收敛性的非常有用的定理。

**定理 27.4.6**

设 $\mathcal{X},\mathcal{Y}$ 是 Banach 空间，$(T_{n})_{n=1}^{\infty}\subset L(\mathcal{X},\mathcal{Y})$，$\sup_{n}\lVert T_{n} \rVert<+\infty$，并且 $T \in L(\mathcal{X},\mathcal{Y})$，如果在稠密集 $D\subset \mathcal{X}$ 上有 $\lVert T_{n}x-Tx \rVert\to 0$，那么 $T_{\alpha}$ 强收敛于 $T$.

**证明**

令 $C=\sup \{ \lVert T \rVert,\lVert T_{1} \rVert,\lVert T_{2} \rVert ,\dots \}$，任取 $x \in \mathcal{X},\varepsilon>0$，则存在 $x' \in D$ 使得 $\lVert x-x' \rVert<\varepsilon / 3C$，再令 $n$ 足够大，使得 $\lVert T_{n}x'-Tx' \rVert<\varepsilon / 3$，则有

$$
\begin{align}
\lVert T_{n}x-Tx \rVert &\leq \lVert T_{n}x-T_{n}x' \rVert +\lVert T_{n}x'-Tx' \rVert +\lVert Tx-Tx' \rVert  \\
&\leq  2C \lVert x-x' \rVert + \varepsilon / 3<\varepsilon
\end{align}
$$

于是 $T_{\alpha}$ 强收敛于 $T$.

另一个定理关于 $\mathcal{X}^{*}$ 的紧致性，它是弱$^{*}$拓扑重要性的体现。

**定理 27.4.7** Alaoglu 定理

设 $\mathcal{X}$ 是赋范空间，则单位闭球 $B^{*}=\{ f \in \mathcal{X}^{*} \mid \lVert f \rVert\leq 1 \}$ 在弱$^{*}$拓扑中是紧致的。

**证明**

对任意 $x \in \mathcal{X}$，令 $D_{x}=\{ z \in \mathbb{C} \mid |z|\leq \lVert x \rVert \},D=\prod_{x}D_{x}$，则根据 Tychonoff 定理，$D$ 是紧致的。对任意 $\phi \in D$，满足对任意 $x$ 有 $|\phi(x)|\leq \lVert x \rVert$，因此 $B^{*}$ 包含了那些线性的 $D$ 中的元素。

又 $B^{*}$ 上的相对拓扑（继承自 $D$ 上的乘积拓扑）与弱$^{*}$拓扑相同，因此我们只需证明 $B^{*}$ 是闭集。设 $\langle f_{\alpha} \rangle$ 是 $\mathcal{X}^{*}$ 中收敛于 $f \in D$ 的网，对任意 $x,y \in \mathcal{X}$ 和 $a,b \in \mathbb{C}$ 有

$$
\begin{gather}
f(ax+by)=\lim_{ \alpha } f_{\alpha}(ax+by)=\lim_{ \alpha } (af_{\alpha}(x)+b f_{\alpha}(y))=af(x)+b f(y)
\end{gather}
$$

因此 $f \in \mathcal{X}^{*}$，这就完成了证明。

在拓扑向量空间 $\mathcal{X}$ 中，我们同样可以定义 **Cauchy 网**的概念：网 $\langle x_{i} \rangle_{i \in I}$ 是 **Cauchy 的**，如果 $\langle x_{i}-x_{j} \rangle_{(i,j)\in I\times I}$ 收敛于 $0$. 自然地，$\mathcal{X}$ 称为**完备的**，如果每个 Cauchy 网都收敛。

当 $\mathcal{X}$ 上的拓扑是第一可数的时候，完备性是最引人关注的一个特征，因为此时它等价于每个 Cauchy **序列**都收敛。由可数个半范数生成的完备 Hausdorff 拓扑向量空间称为 **Frechet 空间**。

拓扑向量空间通常会在微分方程的研究中自然地出现，其中大多数情况下都涉及对导数算子 $D= \dfrac{\mathrm{d}}{\mathrm{d}x}$ 的研究。在大多数函数空间 $\mathcal{X}$ 上，不存在范数使得 $D$ 成为一个有界线性映射：例如，令 $f_{\lambda}=e^{\lambda x}$，则 $Df_{\lambda}=\lambda f_{\lambda}$，因此 $\lVert D \rVert\geq|\lambda|$ 对任意 $\lambda$ 都成立，无论 $\mathcal{X}$ 上的范数是如何定义的。

面对这样的情况，我们就可以利用半范数将 $D$ 看成一个局部凸的拓扑向量空间上的连续映射。例如，在 $C^{\infty}([0,1])$ 上可以取半范数 $p_{k}(f)=\sup_{0\leq x\leq 1}|f^{(k)}(x)|$，此时 $C^{\infty}([0,1])$ 就成为了一个 Frechet 空间，并且根据定理 27.4.4，$D$ 是一个连续映射，因为 $p_{k}(Df)=p_{k+1}(f)$.

# Section 5: Hilbert 空间

最重要的 Banach 空间，并且能够在其上做最精细的分析的空间，就是所谓的 **Hilbert 空间**。它是有限维中内积空间的直接推广，并且内积空间的大多数良好性质都得以继承到无限维。下面我们给出定义：

**定义 27.5.1** Hilbert 空间

一个定义了内积的复向量空间称为**准 Hilbert 空间**。准 Hilbert 空间 $\mathcal{H}$ 如果关于范数 $\lVert x \rVert=\sqrt{ \langle x,x \rangle }$ 是完备的，则称 $\mathcal{H}$ 是一个 **Hilbert 空间**。

一些有限维空间中的结论可以直接推广到一般的准 Hilbert 空间中，其证明完全不需要做任何改动（参考专栏有限维向量空间），下面列举出一些常用结论：

**定理 27.5.2** Cauchy-Schwarz 不等式

设 $\mathcal{H}$ 是准 Hilbert 空间，则对任意 $x,y \in \mathcal{H}$ 有 $|\langle x,y \rangle|\leq \lVert x \rVert\lVert y \rVert$，等号成立当且仅当 $x,y$ 线性相关。

**定理 27.5.3** 平行四边形恒等式

设 $\mathcal{H}$ 是准 Hilbert 空间，则对任意 $x,y \in \mathcal{H}$ 有

$$
\begin{gather}
\lVert x+y \rVert ^{2}+\lVert x-y \rVert ^{2}=2(\lVert x \rVert ^{2}+\lVert y \rVert ^{2})
\end{gather}
$$

**定理 27.5.4** 勾股定理

设 $\mathcal{H}$ 是准 Hilbert 空间，如果对任意 $1\leq j\neq k\leq n$ 有 $\langle x_{j},x_{k} \rangle=0$，那么

$$
\begin{gather}
\left\lVert  \sum_{j=1}^{n} x_{j}   \right\rVert ^{2}=\sum_{j=1}^{n} \lVert x_{j} \rVert ^{2}
\end{gather}
$$

**定理 27.5.5** 极化恒等式

设 $\mathcal{H}$ 是准 Hilbert 空间，则对任意 $x,y \in \mathcal{H}$ 有

$$
\langle x,y \rangle = \dfrac{1}{4}(\lVert x+y \rVert ^{2}+\lVert x-y \rVert ^{2}+i\lVert x+iy \rVert ^{2}+i\lVert x-iy \rVert ^{2})
$$

Hilbert 空间的一个重要的蓝本是 $L^{2}(\mu)$：所有满足 $\int|f|^{2}\mathrm{d}\mu<+\infty$ 的可测函数构成的空间。根据均值不等式 $ab\leq \dfrac{1}{2}(a^{2}+b^{2})$，当 $f,g \in L^{2}(\mu)$ 时，我们有 $|f \overline{g}|\leq \dfrac{1}{2}(|f|^{2}+|g|^{2})$，因此 $f \overline{g}\in L^{1}(\mu)$，从而

$$
\begin{gather}
\langle f,g \rangle =\int f \overline{g} \mathrm{d} \mu
\end{gather}
$$

定义了 $L^{2}(\mu)$ 上的一个内积，我们将在下一章证明它的完备性。

当 $\mu$ 取为 $(A,\mathscr{P}(A))$ 上的计数测度时，通常把 $L^{2}(A,\mu)$ 记作 $l^{2}(A)$，也就是说，$l^{2}(A)$ 由满足 $\sum_{\alpha \in A}|f(\alpha)|^{2}<+\infty$ 的函数 $f\colon A\to \mathbb{C}$ 构成。

**定理 27.5.6**

设 $\mathcal{H}$ 是 Hilbert 空间，$x_{n}\to x,y_{n}\to y$，则 $\langle x_{n},y_{n} \rangle\to \langle x,y \rangle$.

**证明**

根据 Cauchy-Schwarz 不等式有

$$
\begin{align}
|\langle x_{n},y_{n} \rangle -\langle x,y \rangle | &= |\langle x_{n}-x,y_{n} \rangle +\langle x,y_{n}-y \rangle | \\
&\leq \lVert x_{n}-x \rVert \lVert y_{n} \rVert +\lVert x \rVert \lVert y_{n}-y \rVert \to 0
\end{align}
$$

因为 $\lVert y_{n} \rVert\to \lVert y \rVert$，从而 $\lVert y_{n} \rVert$ 有界。

**定理 27.5.7**

如果 $\mathcal{M}$ 是 Hilbert 空间 $\mathcal{H}$ 的一个闭子空间，则 $\mathcal{H}=\mathcal{M}\oplus \mathcal{M}^{\perp}$，即每个 $x \in \mathcal{H}$ 都可以唯一地分解为 $x=y+z,y \in \mathcal{M},z \in \mathcal{M}^{\perp}$，并且 $y$ 和 $z$ 分别是 $\mathcal{M}$ 和 $\mathcal{M}^{\perp}$ 中与 $x$ 之间距离最小的点。

**证明**

给定 $x \in \mathcal{H}$，令 $\delta=\inf \{ \lVert x-y \rVert \mid y \in \mathcal{M} \}$，取 $\mathcal{M}$ 中的序列 $(y_{n})$ 使得 $\lVert x-y_{n} \rVert\to \delta$，根据平行四边形恒等式有

$$
\begin{gather}
2(\lVert y_{n}-x \rVert ^{2}+\lVert y_{m}-x \rVert ^{2})=\lVert y_{n}-y_{m} \rVert ^{2}+\lVert y_{n}+y_{m}-2x \rVert ^{2}
\end{gather}
$$

再根据 $\dfrac{1}{2}(y_{n}+y_{m})\in \mathcal{M}$ 有

$$
\begin{align}
\lVert y_{n}-y_{m} \rVert ^{2}&= 2(\lVert y_{n}-x \rVert ^{2}+\lVert y_{m}-x \rVert ^{2})- 4 \left\lVert  \dfrac{1}{2}(y_{n}+y_{m})-x  \right\rVert ^{2} \\
&\leq 2(\lVert y_{n}-x \rVert ^{2}+\lVert y_{m}-x \rVert ^{2})- 4\delta^{2}
\end{align}
$$

由于 $\lVert y_{n}-x \rVert\to\delta$，故 $\lVert y_{n}-y_{m} \rVert\to 0$，因此 $(y_{n})$ 是 Cauchy 序列，进而收敛。令 $y=\lim_{ n \to \infty }y_{n},z=x-y$，因为 $\mathcal{M}$ 是闭的，故 $y \in \mathcal{M}$，并且 $\lVert x-y \rVert=\delta$.

下面我们要证 $z \in \mathcal{M}^{\perp}$. 任取 $u \in \mathcal{M}$，通过乘以一个适当的标量，我们可以令 $\langle z,u \rangle \in \mathbb{R}$，从而

$$
\begin{gather}
f(t)=\lVert z+tu \rVert ^{2}=\lVert z \rVert ^{2}+2t \langle z,u \rangle + t^{2}\lVert u \rVert ^{2} \in \mathbb{R}
\end{gather}
$$

由于 $z+tu=x-(y-tu)$ 而 $y-tu \in \mathcal{M}$，故 $f(t)$ 在 $t=0$ 处取到极小值，从而 $2\langle z,u \rangle=f'(0)=0$，进而有 $z \in \mathcal{M}^{\perp}$. 此外，如果另有 $z' \in \mathcal{M}^{\perp}$，则根据勾股定理有

$$
\begin{gather}
\lVert x-z' \rVert ^{2}=\lVert x-z \rVert ^{2}+\lVert z-z' \rVert ^{2}\geq \lVert x-z \rVert ^{2}
\end{gather}
$$

因此 $z$ 是 $\mathcal{M}^{\perp}$ 中距离 $x$ 最近的点（从而是唯一的）。对 $y$ 也是同理。

最后，如果另有 $x=y'+z'$，那么 $y-y'=z'-z \in \mathcal{M}\cap \mathcal{M}^{\perp}=\{ 0 \}$，即 $y=y',z=z'$，从而 $\mathcal{H}=\mathcal{M}\oplus \mathcal{M}'$.

上述定理中的 $y$ 和 $z$ 就自然地称为 $x$ 在 $\mathcal{M},\mathcal{M}^{\perp}$ 上的**正交投影**。

任取 $y \in \mathcal{H}$，Cauchy-Schwarz 不等式表明 $f_{y}(x)=\langle x,y \rangle$ 定义了 $\mathcal{H}$ 上的一个有界线性泛函，其中 $\lVert f_{y} \rVert=\lVert y \rVert$，因此映射 $y\mapsto f_{y}$ 是 $\mathcal{H}$ 到其对偶空间 $\mathcal{H}^{*}$ 的一个等距映射。下面的定理指出该映射是满的：

**定理 27.5.8** Riesz 表示定理（Riesz representation theorem）

设 $\mathcal{H}$ 是 Hilbert 空间，如果 $f \in \mathcal{H}^{*}$，那么存在唯一的 $y \in \mathcal{H}$ 使得对任意 $x \in \mathcal{H}$ 有 $f(x)=\langle x,y \rangle$.

**证明**

首先证明唯一性：如果 $\langle x,y \rangle=\langle x,y' \rangle$，那么取 $x=y-y'$ 可得 $\lVert y-y' \rVert^{2}=0$，即 $y=y'$. 下面证明存在性。

如果 $f=0$，则可以取 $y=0$，反之，令 $\mathcal{M}=\ker f=\{ x \mid f(x)=0 \}$，则 $\mathcal{M}\neq \mathcal{H}$，并且 $\mathcal{M}$ 是 $\mathcal{H}$ 的一个闭子空间，从而由定理 27.5.7 知 $\mathcal{M}^{\perp}\neq \{ 0 \}$.

取 $z \in \mathcal{M}^{\perp}$ 使得 $\lVert z \rVert=1$，令 $u=f(x)z-f(z)x$，则 $f(u)=0$，即 $u \in \mathcal{M}$，因此

$$
\begin{gather}
0=\langle u,z \rangle =f(x)\langle z,z \rangle -f(z)\langle x,z \rangle =f(x)-\langle x,\overline{f(z)} z \rangle 
\end{gather}
$$

于是取 $y=\overline{f(z)}z$ 即证。

Riesz 表示定理表明，Hilbert 空间是自反的：$\mathcal{H}$ 和 $\mathcal{H}^{*}$ 以及 $\mathcal{H}^{**}$ 具有自然的同构。此外，它还保证了**伴随映射** $T^{*}$ 的存在性 $\langle Tx,y \rangle=\langle x,T^{*}y \rangle$，这是建立谱理论的基础。

下面我们来考虑正交向量与正交基相关的定理。对于可数个线性无关的向量 $(x_{n})_{n=1}^{\infty}$，我们有一套标准算法称为 **Gram-Schmidt 过程**，用来将 $(x_{n})$ 转化为规范正交的向量 $(u_{n})_{n=1}^{\infty}$，并且有 $\mathrm{span}(x_{n})_{n=1}^{N}=\mathrm{span}(u_{n})_{n=1}^{N}$ 对任意 $N\geq 1$ 都成立。

**定理 27.5.9** Bessel 不等式

设 $\mathcal{H}$ 是 Hilbert 空间，如果 $\{ u_{\alpha} \}_{\alpha \in A}$ 是规范正交的，那么对任意 $x \in \mathcal{H}$ 有

$$
\begin{gather}
\sum_{\alpha \in A} |\langle x,u_{\alpha} \rangle |^{2}\leq \lVert x \rVert ^{2}
\end{gather}
$$

特别地，$\{ \alpha \mid \langle x,u_{\alpha} \rangle\neq 0 \}$ 是至多可数的。

**证明**

我们只需证明对任意有限集 $F\subset A$ 有 $\sum_{\alpha \in F}|\langle x,u_{\alpha} \rangle|^{2}\leq \lVert x \rVert^{2}$，但我们有

$$
\begin{align}
0 &\leq \left\lVert  x- \sum_{\alpha \in F} \langle x,u_{\alpha} \rangle u_{\alpha}  \right\rVert^{2}  \\
&= \lVert x \rVert ^{2}-2 \mathrm{Re} \left\langle  x, \sum_{\alpha \in F} \langle x,u_{\alpha} \rangle u_{\alpha}  \right\rangle +\left\lVert   \sum_{\alpha \in F} \langle x,u_{\alpha} \rangle u_{\alpha}  \right\rVert ^{2} \\
&= \lVert x \rVert ^{2} -2 \sum_{\alpha \in F} |\langle x,u_{\alpha} \rangle |^{2} +\sum_{\alpha \in F} |\langle x,u_{\alpha} \rangle |^{2} \\
&= \lVert x \rVert ^{2} -\sum_{\alpha \in F} |\langle x,u_{\alpha} \rangle |^{2}
\end{align}
$$

这就完成了证明。

**定理 27.5.10**

设 $\mathcal{H}$ 是 Hilbert 空间，$\{ u_{\alpha} \}_{\alpha \in A}$ 是规范正交的，则以下命题等价：

1. 完备性：如果对任意 $\alpha$ 都有 $\langle x,u_{\alpha} \rangle=0$，那么 $x=0$.
2. Parseval 恒等式：$\lVert x \rVert^{2}=\sum_{\alpha \in A}|\langle x,u_{\alpha} \rangle|^{2}$
3. 对任意 $x \in \mathcal{H}$ 有 $x=\sum_{\alpha \in A}\langle x,u_{\alpha} \rangle u_{\alpha}$，其中右边的求和中只有至多可数项不为零，并且在任意重排下都收敛。

**证明**

$1\to 3$：设 $\alpha_{1},\alpha_{2},\dots$ 是使得 $\langle x,u_{\alpha_{j}} \rangle\neq 0$ 的下标，根据 Bessel 不等式，级数 $\sum_{j=1}^{\infty}|\langle x,u_{\alpha_{j}} \rangle|^{2}$ 收敛，因此对于 $n>m$ 有

$$
\begin{gather}
\left\lVert  \sum_{j=m}^{n} \langle x,u_{\alpha_{j}} \rangle u_{\alpha_{j}}  \right\rVert ^{2}=\sum_{j=m}^{n} |\langle x,u_{\alpha_{j}} \rangle |^{2} \to 0 \quad (m,n\to \infty)
\end{gather}
$$

因此由 $\mathcal{H}$ 的完备性知 $\sum_{j=1}^{\infty}\langle x,u_{\alpha_{j}} \rangle u_{\alpha_{j}}$ 收敛。令 $y=\sum_{j=1}^{\infty}\langle x,u_{\alpha_{j}} \rangle u_{\alpha_{j}}$，则 $\langle y,u_{\alpha} \rangle=0$，从而由 1 得 $y=0$.

$3\to 2$：根据 Bessel 不等式的证明，我们有

$$
\begin{gather}
\lVert x \rVert ^{2} -\sum_{j=1}^{n}  |\langle x,u_{\alpha_{j}} \rangle |^{2}=\left\lVert  x- \sum_{j=1}^{n}  \langle x,u_{\alpha_{j}} \rangle u_{\alpha_{j}}  \right\rVert^{2} \to 0 \quad (n\to \infty)
\end{gather}
$$

即证。$2\to 1$ 是显然的，这就完成了证明。

满足定理 27.5.10 的三条性质的规范正交向量组称为**规范正交基**。例如，在 $l^{2}(A)$ 上我们可以定义 $e_{\alpha}(\beta)=\delta_{\alpha\beta}$，则 $\langle f,e_{\alpha} \rangle=f(\alpha)$，于是由完备性知 $\{ e_{\alpha} \}_{\alpha \in A}$ 是一个规范正交基，通常它也被称为 $l^{2}(A)$ 中的标准基。

**定理 27.5.11**

每个 Hilbert 空间都有规范正交基。

**证明**

我们将使用 Zorn 引理来进行证明。设 $\mathcal{B}$ 由规范正交的向量集构成，按包含关系形成偏序。对于其上的链 $\{ B_{l} \mid l \in L \}$，取 $B=\bigcup_{l \in L}B_{l}$，则对任意 $u_{\alpha} \in B$ 有 $\lVert u_{\alpha} \rVert=1$，且对于 $u_{\alpha},u_{\beta}\in B,\alpha\neq\beta$，存在 $B_{l}$ 使得 $u_{\alpha},u_{\beta}\in B_{l}$，于是 $\langle u_{\alpha},u_{\beta} \rangle=0$，因此 $B$ 是规范正交的，并且是 $\{ B_{l} \}$ 的一个上界。

根据 Zorn 引理，存在 $\mathcal{B}$ 的极大元 $B^{*}$，假设 $B^{*}$ 不是规范正交基，那么存在 $x \in \mathcal{H}\setminus  \overline{\mathrm{span}(B^{*})}$，根据 27.5.7，$x$ 可以分解为 $x=y+z$，其中 $z \in \overline{\mathrm{span}(B^{*})}^{\perp},z\neq 0$，令 $u=z / \lVert z \rVert$，则 $B^{*}\cup \{ u \}$ 也是规范正交的，这与 $B^{*}$ 的极大性矛盾。这就完成了证明。

**定理 27.5.12**

Hilbert 空间 $\mathcal{H}$ 是可分的当且仅当它有一个至多可数的规范正交基，此时每个规范正交基都是至多可数的。

**证明**

如果 $\{ x_{n} \}$ 是 $\mathcal{H}$ 的一个可数稠密子集，将包含在 $\mathrm{span}(x_{1},\dots,x_{n-1})$ 中的那些 $x_{n}$ 去除，我们可以得到一至多可数的线性无关集 $\{ y_{n} \}$，其张成空间在 $\mathcal{H}$ 中是稠密的。将 Gram-Schmidt 过程应用到 $\{ y_{n} \}$ 上得到规范正交集 $\{ u_{n} \}$，其张成空间也是稠密的，从而是一个规范正交基。

反之，如果 $\{ u_{n} \}$ 是一个可数的规范正交基，有限个 $u_{n}$ 的线性组合（系数包含于 $\mathbb{C}$ 的可数稠密子集中）构成了 $\mathcal{H}$ 的一个可数稠密子集。此外，如果 $\{ v_{\alpha} \}_{\alpha \in A}$ 是另一个规范正交基，则 $A_{n}=\{ \alpha \mid \langle u_{n},v_{\alpha} \rangle\neq 0 \}$ 是可数的，根据 $\{ u_{n} \}$ 的完备性知 $A=\bigcup_{n=1}^{\infty}A_{n}$ 是可数的，即证。

最后，我们来描绘 Hilbert 空间的形象。

**定义 27.5.13** 酉映射（unitary map）

设 $\mathcal{H}_{1},\mathcal{H}_{2}$ 是 Hilbert 空间，一个**酉映射** $U\colon \mathcal{H}_{1}\to \mathcal{H}_{2}$ 是一个可逆线性映射，并且满足对任意 $x,y \in \mathcal{H}_{1}$ 有

$$
\begin{gather}
\langle Ux,Uy \rangle _{2}=\langle x,y \rangle _{1}
\end{gather}
$$

换句话说，一个酉映射是一个保持内积的同构。从酉同构的角度来看，每个 Hilbert 空间都等价于某个 $l^{2}$ 空间：

**定理 27.5.14**

设 $\mathcal{H}$ 是 Hilbert 空间，$\{ u_{\alpha} \}_{\alpha \in A}$ 是一个规范正交基，对任意 $x \in \mathcal{H}$，定义 $\hat{x}(\alpha)=\langle x,u_{\alpha} \rangle$，则映射 $x\mapsto \hat{x}$ 是一个从 $\mathcal{H}$ 到 $l^{2}(A)$ 的酉映射。

**证明**

映射 $\Phi\colon x\mapsto \hat{x}$ 显然是线性的，并且根据 Parseval 恒等式 $\lVert x \rVert^{2}=\sum_{\alpha \in A}|\hat{x}(\alpha)|^{2}$ 知 $\Phi$ 是等距映射。如果 $f \in l^{2}(A)$，则 $\sum_{\alpha \in A}|f(\alpha)|^{2}<+\infty$，于是勾股定理表明级数 $\sum_{\alpha \in A}f(\alpha)u_{\alpha}$ 的部分和序列是 Cauchy 的，从而 $x=\sum_{\alpha \in A}f(\alpha)u_{\alpha}$ 在 $\mathcal{H}$ 中存在，并且 $\hat{x}=f$，即 $\Phi$ 是满射。

因为等距映射是单射，因此 $\Phi$ 是双射，再由极化恒等式知 $\Phi$ 保持内积不变，即证 $\Phi$ 是酉映射。

当 $A$ 是至多可数集时，这里的 $\hat{x}(\alpha)$ 通常称为 $x$ 的第 $\alpha$ 个坐标。