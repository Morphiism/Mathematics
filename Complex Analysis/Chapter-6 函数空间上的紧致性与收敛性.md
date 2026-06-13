在本章中，我们将在区域 $G$ 上的解析函数构成的空间上引入一个度量，并讨论这一度量空间上的紧致性与收敛性。作为它的应用，我们将给出两个重要定理：Riemann 映射定理与 Weierstrass 分解定理的证明。同时，利用一些更普遍的结果，我们也可以研究亚纯函数构成的空间。

# Section 1: 连续函数空间 $C(G,\Omega)$

设开集 $G\subset \mathbb{C}$，我们考虑函数 $f\colon G\to\Omega$ 构成的空间，其中 $\Omega$（连带着其上的度量）将总是设为一个完备度量空间，例如 $\mathbb{R},\mathbb{C}$ 和 $\mathbb{C}_{\infty}$.

**定义 6.1.1**

设 $G\subset \mathbb{C}$ 是开集，$\Omega$ 是一个完备度量空间，则我们记从 $G$ 到 $\Omega$ 的所有连续函数构成的集合为 $C(G,\Omega)$.

集合 $C(G,\Omega)$ 总是非空的，因为它包含所有的常值函数。然而 $C(G,\Omega)$ 中只有常值函数是可能的：如果 $G$ 连通并且 $\Omega=\mathbb{Z}$，那么 $f[G]$ 连通，从而 $f$ 一定是常值函数。不过，如果我们主要考察的是 $\Omega=\mathbb{C}$ 或 $\mathbb{C}_{\infty}$ 的情况，此时 $C(G,\Omega)$ 显然是不平凡的：$C(G,\mathbb{C})$ 包含了 $G$ 上的解析函数，而 $C(G,\mathbb{C}_{\infty})$ 包含了 $G$ 上的亚纯函数。

为了在 $C(G,\Omega)$ 上定义一个度量，我们需要下面的定理。用术语来说，它表明 $\mathbb{C}$ 上的开集是“$\sigma$-紧致”的。

**定理 6.1.2**

如果 $G\subset \mathbb{C}$ 是开集，那么存在 $G$ 的紧致子集族 $\{ K_{n} \}$ 使得 $G=\bigcup_{n=1}^{\infty}K_{n}$. 此外，紧致集 $K_{n}$ 可以被选取使得：

1. $K_{n}\subset \mathrm{Int}(K_{n+1})$
2. 对于紧致集 $K\subset G$，存在 $n$ 使得 $K\subset K_{n}$
3. $\mathbb{C}_{\infty}\setminus K_{n}$ 的每个连通分量都包含 $\mathbb{C}_{\infty}\setminus G$ 的一个连通分量

**证明**

对任意 $n\geq 1$，令

$$
\begin{gather}
K_{n}=\{ z \mid |z|\leq n \} \cap \left\{  z \middle| d(z,\mathbb{C}\setminus G)\geq \dfrac{1}{n}  \right\}
\end{gather}
$$

由于 $K_{n}$ 有界并且是两个闭集的交，故 $K_{n}$ 紧致。此外，集合

$$
\begin{gather}
\{ z \mid |z|<n+1 \}\cap \left\{  z \middle| \mathrm{d} (z,\mathbb{C}\setminus G)> \dfrac{1}{n+1}  \right\}
\end{gather}
$$

是开集，包含 $K_{n}$，并且是 $K_{n+1}$ 的子集，因此 $K_{n}\subset \mathrm{Int}(K_{n+1})$. 此外，由 $G=\bigcup_{n=1}^{\infty}K_{n}$ 可得 $G=\bigcup_{n=1}^{\infty}\mathrm{Int}(K_{n})$，因此如果紧致集 $K\subset G$，那么 $\{ \mathrm{Int}(K_{n}) \}$ 就是它的一个开覆盖，利用性质 1 即得性质 2.

对于性质 3，注意到 $\mathbb{C}_{\infty}\setminus K_{n}\supset \mathbb{C}_{\infty}\setminus G$ 的无界分量必然包含 $\infty$，因此它也包含 $\mathbb{C}_{\infty}\setminus G$ 的无界分量。此外，无界分量包含集合 $\{ z \mid |z|>n \}$，因此如果 $D$ 是 $\mathbb{C}_{\infty}\setminus K_{n}$ 的一个有界分量，那么它包含一点 $z$ 使得 $d(z,\mathbb{C}\setminus G)<1 /n$，于是有 $w \in \mathbb{C}\setminus G$ 使得 $|z-w|<1 /n$，从而 $z \in B(w,1 /n)\subset \mathbb{C}_{\infty}\setminus K_{n}$. 由于圆盘是连通集，$z \in D$，故 $B(w,1 /n)\subset D$. 因此，如果 $D_{1}$ 是包含 $w$ 的 $\mathbb{C}_{\infty}\setminus G$ 的连通分量，那么 $D_{1}\subset D$.

如果 $G=\bigcup_{n=1}^{\infty}K_{n}$，其中 $K_{n}$ 紧致并且 $K_{n}\subset \mathrm{Int}(K_{n+1})$，我们定义

$$
\begin{gather}
\rho_{n}(f,g)=\sup_{z \in K_{n}} d(f(z),g(z))
\end{gather}
$$

其中 $f,g \in C(G,\Omega)$. 再定义

$$
\begin{gather}
\rho(f,g)=\sum_{n=1}^{\infty} \dfrac{1}{2^{n}} \dfrac{\rho_{n}(f,g)}{1+\rho_{n}(f,g)}
\end{gather}
$$

由于 $\dfrac{t}{1+t}\leq 1$，故以上级数由 $\sum_{n=1}^{\infty}2^{-n}$ 控制，从而绝对收敛。我们可以证明 $\rho$ 是 $C(G,\Omega)$ 上的一个度量（称为**紧收敛度量**），为此，我们需要拓扑学中的一个引理：

**引理 6.1.3**

如果 $(X,d)$ 是一个度量空间，那么

$$
\begin{gather}
\mu(x,y)=\dfrac{d(x,y)}{1+d(x,y)}
\end{gather}
$$

是一个度量，并且其生成的拓扑与 $d$ 生成的拓扑相同。

**定理 6.1.4**

$\rho$ 是 $C(G,\Omega)$ 上的一个度量。

**证明**

显然 $\rho(f,g)\geq 0$，$\rho(f,g)=\rho(g,f)$，并且 $\rho(f,f)=0$. 如果 $\rho(f,g)=0$，由于级数的每一项都非负，故对任意 $n$ 有

$$
\begin{gather}
\rho_{n}(f,g)=0
\end{gather}
$$

由于 $G=\bigcup_{n=1}^{\infty}K_{n}$，这表明 $f=g$. 最后我们只需证明三角不等式。由于 $d$ 是一个度量，故 $\rho_{n}$ 满足三角不等式，于是引理 6.1.3 表明 $\mu_{n}=\dfrac{\rho_{n}}{1+\rho_{n}}$ 也满足三角不等式，从而我们有

$$
\begin{align}
\rho(f,g) &= \sum_{n=1}^{\infty} \dfrac{1}{2^{n}} \mu_{n}(f,g) \\
&\leq \sum_{n=1}^{\infty} \dfrac{1}{2^{n}}(\mu_{n}(f,h)+\mu_{n}(h,g)) \\
&= \rho(f,h)+\rho(h,g)
\end{align}
$$

这就完成了证明。

下一个引理关乎 $C(G,\Omega)\times C(G,\Omega)$ 的子集，并且它为理解 $\rho$ 的行为提供了深入的见解。

**引理 6.1.5**

给定 $\varepsilon>0$，则存在 $\delta>0$ 和紧致集 $K\subset G$ 使得对 $f,g \in C(G,\Omega)$ 有

$$
\begin{gather}
\sup_{z \in K} d(f(z),g(z))<\delta \implies \rho(f,g)<\varepsilon
\end{gather}
$$

反之，如果给定 $\delta>0$ 和紧致集 $K$，则存在 $\varepsilon>0$ 使得对 $f,g \in C(G,\Omega)$ 有

$$
\begin{gather}
\rho(f,g)<\varepsilon \implies \sup_{z \in K} d(f(z),g(z))<\delta
\end{gather}
$$

**证明**

如果给定 $\varepsilon>0$，取 $p>0$ 使得 $\sum_{n=p+1}^{\infty}2^{-n}<\varepsilon /2$，令 $K=K_{p}$. 取 $\delta>0$ 使得当 $0\leq t<\delta$ 时有 $\dfrac{t}{1+t}< \dfrac{\varepsilon}{2}$. 设 $f,g \in C(G,\Omega)$ 满足

$$
\begin{gather}
\sup_{z \in K} d(f(z),g(z))<\delta
\end{gather}
$$

则由于 $K_{n}\subset K_{p}$ 对 $n\leq p$ 成立，故有 $\rho_{n}(f,g)<\delta$，从而

$$
\begin{gather}
\dfrac{\rho_{n}(f,g)}{1+\rho_{n}(f,g)}<\dfrac{\varepsilon}{2}
\end{gather}
$$

对 $n\leq p$ 成立。因此

$$
\begin{gather}
\rho(f,g)\leq \sum_{n=1}^{p} \dfrac{1}{2^{n}} \dfrac{\varepsilon}{2}+\sum_{n=p+1}^{\infty} \dfrac{1}{2^{n}}<\varepsilon
\end{gather}
$$

现在假设有 $\delta>0$ 和 $K$ 给定，由于 $G=\bigcup_{n=1}^{\infty}K_{n}=\bigcup_{n=1}^{\infty}\mathrm{Int}(K_{n})$，因此存在 $p>0$ 使得 $K\subset K_{p}$，于是

$$
\begin{gather}
\rho_{p}(f,g)\geq \sup_{z \in K} d(f(z),g(z))
\end{gather}
$$

取 $\varepsilon>0$ 使得当 $0\leq s<2^{p}\varepsilon$ 时有 $\dfrac{s}{1-s}<\delta$，于是 $\dfrac{t}{1+t}<2^{p}\varepsilon$ 蕴含 $t<\delta$. 如果 $\rho(f,g)<\varepsilon$，则 $\dfrac{\rho_{p}(f,g)}{1+\rho_{p}(f,g)}<2^{p}\varepsilon$，从而 $\rho_{p}(f,g)<\delta$，这就是所要证的。

**定理 6.1.6**

1. 集合 $\mathcal{O}\subset C(G,\Omega)$ 是开集当且仅当对任意 $f \in \mathcal{O}$，存在 $\delta>0$ 和紧致集 $K\subset G$ 使得 $\{ g \in C(G,\Omega) \mid \sup_{z \in K} d(f(z),g(z))<\delta \} \subset \mathcal{O}$
2. 此外，$C(G,\Omega)$ 中的序列 $(f_{n})$ 按 $\rho$ 收敛于 $f$ 当且仅当 $(f_{n})$ 在 $G$ 的所有紧致子集上一致收敛于 $f$.

**证明**

如果 $\mathcal{O}$ 是开集，$f \in \mathcal{O}$，那么存在 $\varepsilon>0$ 使得 $\{ g \mid \rho(f,g)<\varepsilon \}\subset \mathcal{O}$，于是由引理 6.1.5 知存在 $\delta>0$ 和紧致集 $K$ 满足 $\sup_{z \in K}d(f(z),g(z))<\delta$ 蕴含 $\rho(f,g)<\varepsilon$. 反之，如果有 $\{ g \mid \sup_{z \in K}d(f(z),g(z))<\delta \}\subset \mathcal{O}$，那么存在 $\varepsilon>0$ 使得 $\rho(f,g)<\varepsilon$ 蕴含 $\sup_{z \in K}d(f(z),g(z))<\delta$，即证 $\mathcal{O}$ 是开集。

再设 $(f_{n})$ 按 $\rho$ 收敛于 $f$，根据引理 6.1.5，任取 $\delta>0$ 和紧致集 $K$，存在 $\varepsilon>0$ 使得

$$
\begin{gather}
\rho(f_{n},f)<\varepsilon \implies \sup_{z \in K} d(f_{n}(z),f(z))<\delta
\end{gather}
$$

对于这个 $\varepsilon$，存在 $N$ 使得对任意 $n>N$ 有 $\rho(f_{n},f)<\varepsilon$，于是对 $n>N$ 有 $\sup_{z \in K}d(f_{n}(z),f(z))<\delta$，即 $(f_{n})$ 在 $K$ 上一致收敛于 $f$.

反之，对任意 $\varepsilon>0$，存在 $\delta>0$ 和紧致集 $K$ 使得

$$
\begin{gather}
\sup_{z \in K} d(f_{n}(z),f(z))<\delta \implies \rho(f_{n},f)<\varepsilon
\end{gather}
$$

由于 $(f_{n})$ 在 $K$ 上一致收敛于 $f$，故存在 $N$ 使得当 $n>N$ 时有 $\sup_{z \in K}d(f_{n}(z),f(z))<\delta$，因此对 $n>N$ 有 $\rho(f_{n},f)<\varepsilon$，即证 $(f_{n})$ 按 $\rho$ 收敛于 $f$.

作为推论，我们有如下结果：

**定理 6.1.7**

$\rho$ 生成的拓扑与紧致集族 $\{ K_{n} \}$ 的选取无关。

**证明**

由定理 6.1.6 的第一部分即证 $C(G,\Omega)$ 上开集的刻画与 $K_{n}$ 的选取无关。

于是，在之后的章节中，我们将 $\rho$ 作为 $C(G,\Omega)$ 上的标准度量，其中紧致集 $K_{n}$ 满足定理 6.1.2 中的性质。

到现在为止，我们还未用到 $\Omega$ 是一个完备度量空间的假设。下面的定理给出了像空间完备性的一个直接推论。

**定理 6.1.8**

$C(G,\Omega)$ 是一个完备度量空间。

**证明**

设 $(f_{n})$ 是 $C(G,\Omega)$ 中的一个 Cauchy 序列，则对任意紧致集 $K\subset G$，将 $f_{n}$ 限制在 $K$ 上就得到了 $C(K,\Omega)$ 上的一个 Cauchy 序列。即，对任意 $\delta>0$，存在 $N$ 使得对 $n,m\geq N$ 有

$$
\begin{gather}
\sup_{z \in K} d(f_{n}(z),f_{m}(z))<\delta
\end{gather}
$$

特别地，$f_{n}(z)$ 是 $\Omega$ 中的 Cauchy 序列，从而有 $f(z)=\lim_{ n \to \infty }f_{n}(z)$，这给出了函数 $f\colon G\to\Omega$. 我们来证明 $f$ 连续并且 $\rho(f_{n},f)\to 0$.

取 $K$ 紧致和 $\delta>0$，则对任意 $z \in K$ 有 $m\geq N$ 使得 $d(f(z),f_{m}(z))<\delta$，从而有

$$
\begin{gather}
d(f(z),f_{n}(z))\leq d(f(z),f_{m}(z))+d(f_{m}(z),f_{n}(z))<2\delta
\end{gather}
$$

对任意 $n\geq N$ 成立。由于 $N$ 与 $z$ 无关，因此

$$
\begin{gather}
\lim_{ n \to \infty } \sup_{z \in K} d(f(z),f_{n}(z))=0
\end{gather}
$$

这表明 $f_{n}$ 在 $K$ 上一致收敛于 $f$. 因此 $f$ 连续，并且由定理 6.1.6 得 $f_{n}$ 按 $\rho$ 收敛于 $f$.

本节的剩余部分我们给出 **Arzela-Ascoli 定理**，它在分析学的各个领域都有广泛的应用。

**定义 6.1.9** 正规族（normal family）

称 $\mathcal{F}\subset C(G,\Omega)$ 是一个**正规族**，如果 $\mathcal{F}$ 中的任意序列都有一个收敛于 $f \in C(G,\Omega)$ 的子序列。

以上的定义看起来非常像序列紧致的定义，不过，它并不要求子序列的极限 $f \in \mathcal{F}$. 它与序列紧致的关联如下：

**定理 6.1.10**

集合 $\mathcal{F}\subset C(G,\Omega)$ 是正规族当且仅当 $\overline{\mathcal{F}}$ 是紧致集。

**证明**

如果 $\overline{\mathcal{F}}$ 紧致，那么 $\mathcal{F}$ 中的任意序列都有收敛于 $f \in \overline{\mathcal{F}}\subset C(G,\Omega)$ 的子序列，即 $\mathcal{F}$ 正规。反之，设 $\mathcal{F}$ 是正规族，$(f_{n})$ 是 $\overline{\mathcal{F}}$ 中的序列，则对任意 $n$，存在 $g_{n}\in \mathcal{F}$ 使得 $\rho(f_{n},g_{n})< n^{-1}$，并且 $(g_{n})$ 有一个收敛于 $f \in \overline{\mathcal{F}}$ 的子序列 $(g_{n_{k}})$. 于是，我们有

$$
\begin{gather}
\rho(f_{n_{k}},f)\leq \rho(f_{n_{k}},g_{n_{k}})+\rho(g_{n_{k}},f)< \dfrac{1}{n_{k}}+\rho(g_{n_{k}},f)
\end{gather}
$$

当 $k\to \infty$ 时，$n_{k}^{-1}\to 0$，因此有 $\rho(f_{n_{k}},f)\to 0$，即证 $\overline{\mathcal{F}}$ 紧致。

**定理 6.1.11**

集合 $\mathcal{F}\subset C(G,\Omega)$ 是正规族当且仅当对任意 $\delta>0$ 和紧致集 $K$，存在函数 $f_{1},\dots,f_{n}\in \mathcal{F}$ 使得对任意 $f \in \mathcal{F}$，存在 $k$ 使得

$$
\begin{gather}
\sup_{z \in K} d(f(z),f_{k}(z))<\delta
\end{gather}
$$

**证明**

设 $\mathcal{F}$ 是正规族且 $K$ 和 $\delta>0$ 给定，则由引理 6.1.5 知存在 $\varepsilon>0$ 使得

$$
\begin{gather}
\rho(f,g)<\varepsilon \implies \sup_{z \in K} d(f(z),g(z))<\delta
\end{gather}
$$

但由于 $\overline{\mathcal{F}}$ 紧致，故 $\mathcal{F}$ 完全有界，从而有 $f_{1},\dots,f_{n}\in \mathcal{F}$ 使得

$$
\begin{gather}
\mathcal{F} \subset \bigcup_{k=1}^{n} \{ f \mid \rho(f,f_{k})<\varepsilon \} \subset \bigcup_{k=1}^{n} \{ f \mid \sup_{z \in K} d(f(z),f_{k}(z))<\delta \}
\end{gather}
$$

这就是所要证的。

反之，如果 $\mathcal{F}$ 满足定理中的条件，那么 $\overline{\mathcal{F}}$ 也满足。由于 $C(G,\Omega)$ 是完备度量空间，故 $\overline{\mathcal{F}}$ 也是完备的。再次应用引理 6.1.5，我们可以证明 $\overline{\mathcal{F}}$ 是完全有界的，从而 $\overline{\mathcal{F}}$ 紧致。这就完成了证明。

设 $(X_{n},d_{n})$ 是度量空间，令 $X=\prod_{n=1}^{\infty}X_{n}$ 为其直积，这就是说，$X$ 中的元素是序列 $(x_{n})_{n=1}^{\infty}$，其中 $x_{n}\in X_{n}$. 在 $X$ 上我们定义

$$
\begin{gather}
d(\xi,\eta)=d((x_{n}),(y_{n}))=\sum_{n=1}^{\infty} \dfrac{1}{2^{n}} \dfrac{d_{n}(x_{n},y_{n})}{1+d_{n}(x_{n},y_{n})}
\end{gather}
$$

则我们有如下结论：

**定理 6.1.12**

$d$ 是 $X=\prod_{n=1}^{\infty}X_{n}$ 上的一个度量。设 $\xi^{k}=(x_{n}^{k})_{n=1}^{\infty}$ 是 $X$ 中的一个序列，则 $\xi^{k}\to \xi=(x_{n})$ 当且仅当对每个 $n$ 有 $x_{n}^{k}\to x_{n}$. 此外，如果每个 $X_{n}$ 都是紧致的，那么 $X$ 也是紧致的。

**证明**

仿照定理 6.1.4 的证明，我们可得 $d$ 是一个度量。假设 $d(\xi^{k},\xi)\to 0$，由于

$$
\begin{gather}
\dfrac{d_{n}(x_{n}^{k},x_{n})}{1+d_{n}(x_{n}^{k},x_{n})}\leq 2^{n} d(\xi^{k},\xi)
\end{gather}
$$

则对任意 $n$ 有 $\dfrac{d_{n}(x_{n}^{k},x_{n})}{1+d_{n}(x_{n}^{k},x_{n})}\to 0$，从而有 $d_{n}(x_{n}^{k},x_{n})\to 0$. 反之，给定 $\varepsilon>0$，我们可以找到 $p>0$ 使得 $\sum_{n=p+1}^{\infty}2^{-n}<\varepsilon /2$，对于级数的前 $p$ 项，由于 $x_{n}^{k}\to x_{n}$ 对 $n\leq p$ 成立，故存在 $K$ 使得当 $k>K$ 时，对任意 $n\leq p$ 有 $\dfrac{d_{n}(x_{n}^{k},x_{n})}{1+d_{n}(x_{n}^{k},x_{n})}<\dfrac{\varepsilon}{2}$，从而

$$
\begin{gather}
d(\xi^{k},\xi) \leq \sum_{n=1}^{p} \dfrac{1}{2^{n}} \dfrac{d_{n}(x_{n}^{k},x_{n})}{1+d_{n}(x_{n}^{k},x_{n})}+\sum_{n=p+1}^{\infty} \dfrac{1}{2^{n}}<\varepsilon
\end{gather}
$$

即证 $d(\xi^{k},\xi)\to 0$.

现在假设每个 $X_{n}$ 都紧致，我们来证明 $X$ 是紧致的。我们可以使用拓扑学中的 Tychonoff 定理来证明它，不过，在可数情形下，我们有一种初等的证明方法，通常称为 **Cantor 对角线论证**。令 $\xi^{k}=(x_{n}^{k})_{n=1}^{\infty}$，我们将其排列为一张二维数表

$$
\begin{gather}
\xi^{1}=(x_{1}^{1},x_{2}^{1},x_{3}^{1},\dots) \\
\xi^{2}=(x_{1}^{2},x_{2}^{2},x_{3}^{2},\dots) \\
\xi^{3}=(x_{1}^{3},x_{2}^{3},x_{3}^{3},\dots) \\
\vdots
\end{gather}
$$

考虑它的第一列 $(x_{1}^{k})_{k=1}^{\infty}\subset X_{1}$，由于 $X_{1}$ 紧致，因此存在 $I_{1}\subset \mathbb{Z}_{>0}$ 使得子序列 $(x_{1}^{k})_{k \in I_{1}}$ 收敛于 $x_{1} \in X_{1}$. 接下来，考虑上指标属于 $I_{1}$ 的第二列元素 $(x_{2}^{k})_{k \in I_{1}}\subset X_{2}$，由于 $X_{2}$ 也是紧致的，故有 $I_{2}\subset I_{1}$ 使得子序列 $(x_{2}^{k})_{k \in I_{2}}$ 收敛于 $x_{2}\in X_{2}$. 继续这一过程，我们就得到一列正整数的子集

$$
\begin{gather}
\mathbb{Z}_{>0} \supset I_{1}\supset I_{2}\supset \cdots
\end{gather}
$$

以及一列 $x_{n} \in X_{n}$ 满足

$$
\begin{gather}
\lim_{ k \to \infty; k \in I_{n} } x_{n}^{k} = x_{n}
\end{gather}
$$

现在我们考虑“对角线”，也就是 $I_{j}$ 中的第 $j$ 个元素 $k_{j}$，并考虑 $(\xi^{k_{j}})_{j=1}^{\infty}$，我们断言 $\xi^{k_{j}}\to \xi=(x_{n})$. 为此，我们只需证明

$$
\begin{gather}
\lim_{ j \to \infty } x_{n}^{k_{j}}=x_{n}
\end{gather}
$$

但 $I_{j}\subset I_{n}$ 对 $j\geq n$ 成立，因此 $(x_{n}^{k_{j}})_{j\geq n}$ 是 $(x_{n}^{k})_{k \in I_{n}}$ 的一个子序列，这就完成了证明。

最后，我们再给出一个定义，它在 Arzela-Ascoli 定理中扮演了极为重要的角色。

**定义 6.1.13** 等度连续（equicontinuous）

称集合 $\mathcal{F}\subset C(G,\Omega)$ 在 $z_{0}\in G$ 处**等度连续**，如果对任意 $\varepsilon>0$，存在 $\delta>0$ 使得对任意 $f \in \mathcal{F}$ 和 $z \in G$ 有

$$
\begin{gather}
|z-z_{0}|<\delta \implies d(f(z),f(z_{0}))<\varepsilon
\end{gather}
$$

称 $\mathcal{F}$ 在 $E\subset G$ 上等度连续，如果对任意 $\varepsilon>0$，存在 $\delta>0$ 使得对任意 $f \in \mathcal{F}$ 和 $z,z' \in E$ 有

$$
\begin{gather}
|z-z'|<\delta \implies d(f(z),f(z'))<\varepsilon
\end{gather}
$$

等度连续可以视为一种关于函数一致的连续性。如果 $\mathcal{F}$ 中只有一个元素 $f$，那么 $\mathcal{F}$ 在 $z_{0}$ 处等度连续就等价于 $f$ 在 $z_{0}$ 处连续，并且 $\mathcal{F}$ 在 $E$ 上等度连续等价于 $f$ 在 $E$ 上一致连续。而当 $\mathcal{F}$ 包含多个元素时，这种连续性对于函数是一致的：相同的 $\delta$ 对每个 $f \in \mathcal{F}$ 都成立。

根据以上的关于连续性与一致连续性的类比，下面的定理也就不足为奇了。

**定理 6.1.14**

设 $\mathcal{F}\subset C(G,\Omega)$ 在 $G$ 中的每一点处等度连续，则 $\mathcal{F}$ 在 $G$ 的所有紧致子集上等度连续。

**证明**

设 $K\subset G$ 紧致并令 $\varepsilon>0$，则对任意 $w \in K$，存在 $\delta_{w}>0$ 使得对任意 $f \in \mathcal{F}$ 有

$$
\begin{gather}
|w-w'|<\delta_{w} \implies d(f(w),f(w'))< \dfrac{\varepsilon}{2}
\end{gather}
$$

由于 $\{ B(w,\delta_{w}) \mid w \in K \}$ 构成了 $K$ 的开覆盖，故由 Lebesgue 覆盖引理知存在 $\delta>0$ 使得对任意 $z \in K$，$B(z,\delta)$ 包含于某个 $B(w,\delta_{w})$ 中。因此，如果 $z,z'$ 满足 $|z-z'|<\delta$，那么存在 $w$ 使得 $z' \in B(z,\delta)\subset B(w,\delta_{w})$，于是我们有 $|z-w|<\delta_{w},|z'-w|<\delta_{w}$，从而

$$
\begin{gather}
d(f(z),f(z'))\leq d(f(z),f(w))+d(f(w),f(z'))<\varepsilon
\end{gather}
$$

即证 $\mathcal{F}$ 在 $K$ 上等度连续。

**定理 6.1.15** Arzela-Ascoli 定理

集合 $\mathcal{F}\subset C(G,\Omega)$ 是正规族当且仅当以下命题成立：

1. 对任意 $z \in G$，$\{ f(z) \mid f \in \mathcal{F} \}$ 在 $\Omega$ 中有紧致闭包
2. $\mathcal{F}$ 在 $G$ 上每一点处等度连续

**证明**

首先设 $\mathcal{F}$ 正规。由于赋值映射 $f\mapsto f(z)$ 是 $C(G,\Omega)$ 到 $\Omega$ 的连续函数，并且 $\overline{\mathcal{F}}$ 紧致，故 $\overline{\{ f(z) \mid f \in \mathcal{F} \}}$ 是紧致的。为证性质 2，固定 $z_{0}\in G$ 和 $\varepsilon>0$，取 $R>0$ 使得 $K=\overline{B(z_{0},R)}\subset G$，则 $K$ 是紧致集，从而由定理 6.1.11 知存在 $f_{1},\dots,f_{n}\in \mathcal{F}$ 使得对任意 $f \in \mathcal{F}$，存在 $k$ 使得

$$
\begin{gather}
\sup_{z \in K} d(f(z),f_{k}(z))< \dfrac{\varepsilon}{3}
\end{gather}
$$

由于每个 $f_{k}$ 均连续，故存在 $0<\delta<R$ 满足

$$
\begin{gather}
|z-z_{0}|<\delta \implies d(f_{k}(z),f_{k}(z_{0}))< \dfrac{\varepsilon}{3}
\end{gather}
$$

于是，对任意 $f \in \mathcal{F}$ 和 $|z-z_{0}|<\delta$ 有

$$
\begin{align}
d(f(z),f(z_{0})) &\leq d(f(z),f_{k}(z))+d(f_{k}(z),f_{k}(z_{0}))+d(f_{k}(z_{0}),f(z_{0})) \\
&< \varepsilon
\end{align}
$$

即证 $\mathcal{F}$ 在 $z_{0}$ 处等度连续。

现在假设 $\mathcal{F}$ 满足性质 1 和 2，我们要证 $\mathcal{F}$ 正规。考虑 $G$ 中实部和虚部均为有理数的点构成的集合，则它可以排列成一个序列 $(z_{n})$，并且其在 $G$ 中稠密。对 $n\geq 1$ 令

$$
\begin{gather}
X_{n}=\overline{\{ f(z_{n}) \mid f \in \mathcal{F} \}} \subset\Omega
\end{gather}
$$

则 $X_{n}$ 紧致，从而 $X=\prod_{n=1}^{\infty}X_{n}$ 是一个紧致度量空间。对 $f \in \mathcal{F}$，定义 $\widetilde{f} \in X$ 为

$$
\begin{gather}
\widetilde{f} = (f(z_{1}),f(z_{2}),\dots)
\end{gather}
$$

设 $(f_{k})$ 是 $\mathcal{F}$ 中的序列，则 $(\widetilde{f}_{k})$ 是 $X$ 中的序列，从而有 $\xi=(\xi_{n}) \in X$ 和子序列（仍然记作 $\widetilde{f}_{k}$）收敛于 $\xi$. 于是我们有

$$
\begin{gather}
\lim_{ k \to \infty } f_{k}(z_{n})=\xi_{n}
\end{gather}
$$

我们将证明 $f_{k}$ 收敛于 $f \in C(G,\Omega)$，上式的重要性在于，它对 $G$ 的一个稠密子集上 $f_{k}$ 的值施加了控制。利用等度连续的性质，我们可以将这种控制扩张到整个 $G$ 上。

由于 $C(G,\Omega)$ 完备，故我们只需证明 $(f_{k})$ 是一个 Cauchy 序列。因此令 $K$ 紧致且 $\varepsilon>0$，我们只需证明存在 $J$ 使得对 $k,j\geq J$ 有

$$
\begin{gather}
\sup_{z \in K} d(f_{k}(z),f_{j}(z))<\varepsilon
\end{gather}
$$

由于 $K$ 紧致，故 $R=d(K,\partial G)>0$. 令 $K_{1}=\{ z \mid d(z,K)\leq R /2 \}$，则 $K_{1}$ 紧致并且 $K\subset \mathrm{Int}(K_{1})\subset K_{1}\subset G$. 由于 $\mathcal{F}$ 在 $G$ 上每一点等度连续，故由定理 6.1.14 知 $\mathcal{F}$ 在 $K_{1}$ 上等度连续。因此存在 $0<\delta<R /2$ 使得对任意 $f \in \mathcal{F}$ 和 $z,z' \in K_{1}$ 有

$$
\begin{gather}
|z-z'|<\delta \implies d(f(z),f(z'))< \dfrac{\varepsilon}{3}
\end{gather}
$$

现在令 $D=\{ z_{n} \mid z_{n} \in K_{1} \}$，如果 $z \in K$，那么存在 $z_{n}$ 使得 $|z-z_{n}|<\delta$，由于 $\delta<R /2$，故 $z_{n}\in K_{1}$. 因此 $\{ B(w,\delta) \mid w \in D \}$ 是 $K$ 的一个开覆盖，取 $w_{1},\dots,w_{n}\in D$ 使得

$$
\begin{gather}
K\subset \bigcup_{i=1}^{n} B(w_{i},\delta)
\end{gather}
$$

由于 $\lim_{ k \to \infty }f_{k}(w_{i})$ 存在，于是有 $J$ 使得当 $k,j\geq J$ 时有

$$
\begin{gather}
d(f_{k}(w_{i}),f_{j}(w_{i}))< \dfrac{\varepsilon}{3}
\end{gather}
$$

从而，设 $z \in K$ 满足 $|z-w_{i}|<\delta$，则对 $k,j\geq J$ 有

$$
\begin{align}
d(f_{k}(z),f_{j}(z)) &\leq d(f_{k}(z),f_{k}(w_{i}))+d(f_{k}(w_{i}),f_{j}(w_{i}))+d(f_{j}(w_{i}),f_{j}(z)) \\
&< \varepsilon
\end{align}
$$

这就完成了证明。

# Section 2: 全纯函数空间 $H(G)$

设 $G\subset \mathbb{C}$ 是一个开集，我们令 $H(G)$ 表示 $G$ 上的全纯（解析）函数构成的集合，则我们可以将 $H(G)$ 视为 $C(G,\mathbb{C})$ 的一个子集。一个首要的问题是，在紧收敛拓扑 $\rho$ 下，$H(G)$ 在 $C(G,\mathbb{C})$ 中闭吗？下面的定理回答了这一问题，并且它还表明，微分算子 $f\mapsto f'$ 在 $H(G)$ 上连续。

**定理 6.2.1**

如果 $(f_{n})$ 是 $H(G)$ 中的序列，$f \in C(G,\mathbb{C})$ 满足 $f_{n}\to f$，那么 $f$ 解析，并且对任意 $k\geq 1$ 有 $f_{n}^{(k)}\to f^{(k)}$.

**证明**

我们使用 Morera 定理来证明 $f$ 解析。令 $T$ 为圆盘 $D\subset G$ 中的一条三角路径，由于 $T$ 紧致，故 $f_{n}\to f$ 在 $T$ 上一致，因此

$$
\begin{gather}
\int_{T}f=\lim_{ n \to \infty }\int_{T}f_{n}=0
\end{gather}
$$

于是 $f$ 在任意圆盘 $D\subset G$ 上解析，即 $f$ 在 $G$ 上解析。

为证 $f_{n}^{(k)}\to f^{(k)}$，令 $D=\overline{B(a,r)}\subset G$，则存在 $R>r$ 使得 $\overline{B(a,R)}\subset G$. 如果 $\gamma$ 是圆 $|z-a|=R$，则由 Cauchy 积分公式得

$$
\begin{gather}
f_{n}^{(k)}(z)-f^{(k)}(z)= \dfrac{k!}{2\pi i} \int_{\gamma} \dfrac{f_{n}(w)-f(w)}{(w-z)^{k+1}} \mathrm{d} w
\end{gather}
$$

从而

$$
\begin{gather}
\lvert f_{n}^{(k)}(z)-f^{(k)}(z) \rvert \leq \dfrac{k!M_{n}R}{(R-r)^{k+1}}
\end{gather}
$$

对 $|z-a|\leq r$ 成立，其中 $M_{n}=\sup \{ |f_{n}(w)-f(w)| \mid |w-a|=R \}$. 又由于 $f_{n}\to f$，故 $M_{n}\to 0$，因此 $f_{n}^{(k)}\to f^{(k)}$ 在 $\overline{B(a,r)}$ 上一致。设 $K$ 是任意紧致集，取 $0<r<d(K,\partial G)$，则存在 $a_{1},\dots,a_{n}\in K$ 使得 $\{ B(a_{j},r) \}$ 覆盖 $K$. 由于 $f_{n}^{(k)}\to f^{(k)}$ 在 $B(a_{j},r)$ 上一致，因此它在 $K$ 上也一致，这就完成了证明。

由于 $C(G,\mathbb{C})$ 是完备的，因此我们立即得到以下结论。

**定理 6.2.2**

$H(G)$ 是一个完备度量空间。

**定理 6.2.3**

如果 $(f_{n})$ 是 $H(G)$ 中的序列，并且 $\sum_{n=1}^{\infty}f_{n}$ 在紧致集上一致收敛于 $f$，那么

$$
\begin{gather}
f^{(k)}=\sum_{n=1}^{\infty} f_{n}^{(k)}
\end{gather}
$$

需注意到，以上定理在实函数中没有对应物。在实函数中，很容易构造出一列可微函数，其极限不可微。然而，在复分析中，一旦全纯函数序列的极限存在，那么其极限就是自动全纯的。

为进一步显示解析函数的特殊性，我们给出以下结果。作为推论，它表明如果 $f_{n}\to f$ 且每个 $f_{n}$ 都无零点，那么或者 $f=0$ 为常数，或者 $f$ 也无零点。

**定理 6.2.4** Hurwitz 定理

设 $G$ 是区域，序列 $(f_{n}) \subset H(G)$ 收敛于 $f$. 如果 $f$ 不恒为零，$\overline{B(a,R)}\subset G$，并且在圆 $|z-a|=R$ 上 $f(z)\neq 0$，那么存在 $N$ 使得当 $n\geq N$ 时，$f$ 与 $f_{n}$ 在 $B(a,R)$ 中有相同的零点数。

**证明**

由于 $f(z)\neq 0$ 在 $|z-a|=R$ 上成立，故

$$
\begin{gather}
\delta=\inf \{ |f(z)| \mid |z-a|=R \} >0
\end{gather}
$$

但 $f_{n}\to f$ 在 $|z-a|=R$ 上一致，因此存在 $N$ 使得当 $n\geq N$ 时有

$$
\begin{gather}
|f_{n}(z)-f(z)|< \dfrac{\delta}{2}< |f(z)|
\end{gather}
$$

因此由 Rouche 定理知 $f$ 与 $f_{n}$ 在 $B(a,R)$ 内的零点数相同。

**定理 6.2.5**

如果 $(f_{n})\subset H(G)$ 收敛于 $f \in H(G)$ 并且 $f_{n}$ 在 $G$ 上不消失，那么或者 $f=0$ 为常数，或者 $f$ 在 $G$ 上也不消失。

接下来我们考虑 $H(G)$ 上的正规族。

**定义 6.2.6** 局部有界（locally bounded）

称 $\mathcal{F}\subset H(G)$ 是**局部有界的**，如果对任意 $a \in G$，存在 $M$ 和 $r>0$ 使得对任意 $f \in \mathcal{F}$ 和 $|z-a|<r$ 有

$$
\begin{gather}
|f(z)|\leq M
\end{gather}
$$

换句话说，$\mathcal{F}$ 是局部有界的，如果对任意 $a \in G$，存在以 $a$ 为中心的圆盘使得 $\mathcal{F}$ 在其上一致有界。利用这一性质，我们可以立即将其推广到紧致集上。

**引理 6.2.7**

集合 $\mathcal{F}\subset H(G)$ 局部有界当且仅当对任意紧致集 $K\subset G$，存在 $M$ 使得对任意 $f \in \mathcal{F}$ 和 $z \in K$ 有

$$
\begin{gather}
|f(z)|\leq M
\end{gather}
$$

**证明**

设 $\mathcal{F}$ 局部有界，则对任意 $a \in G$，都有 $B(a,r_{a})$ 使得 $\mathcal{F}$ 在其上一致有界。由于 $\{ B(a,r_{a}) \}$ 覆盖了 $K$，因此存在 $a_{1},\dots,a_{n} \in K$ 使得 $\mathcal{F}$ 在 $B(a_{j},r_{a_{j}})$ 上一致有界，取上界的最大值 $M$，则对任意 $f \in \mathcal{F}$ 和 $z \in K$ 就有 $|f(z)|\leq M$.

反之，对任意 $a \in G$，存在 $\overline{B(a,r)}\subset G$. 由于 $\overline{B(a,r)}$ 是有界闭集，故紧致，从而 $\mathcal{F}$ 在其上一致有界，即证 $\mathcal{F}$ 在 $B(a,r)$ 上一致有界。这就完成了证明。

**定理 6.2.8** Montel 定理

集合 $\mathcal{F}\subset H(G)$ 是正规族当且仅当 $\mathcal{F}$ 局部有界。

**证明**

假设 $\mathcal{F}$ 正规但不局部有界，于是根据引理 6.2.7，存在紧致集 $K\subset G$ 使得 $\sup \{ |f(z)| \mid f \in \mathcal{F},z \in K \}=\infty$. 这就是说，存在 $(f_{n})\subset \mathcal{F}$ 使得 $\sup \{ |f_{n}(z)| \mid z \in K \}\geq n$. 由于 $\mathcal{F}$ 正规，故存在子序列 $(f_{n_{k}})$ 收敛于 $f \in H(G)$. 但这表明 $\sup_{z \in K}|f_{n}(z)-f(z)| \to 0$，于是如果 $|f(z)|\leq M$ 对 $z \in K$ 成立，那么

$$
\begin{gather}
n_{k}\leq \sup_{z \in K} |f_{n}(z)-f(z)| +M \to M
\end{gather}
$$

这与 $n_{k}\to \infty$ 矛盾。

现在设 $\mathcal{F}$ 局部有界，我们将使用 Arzela-Ascoli 定理来证明 $\mathcal{F}$ 正规。显然 $\{ f(z) \mid f \in \mathcal{F} \}$ 是有界的，从而我们只需验证等度连续性。取 $a \in G$ 和 $\varepsilon>0$，则存在 $r>0$ 和 $M$ 使得 $\overline{B(a,r)}\subset G$ 且在其上有 $|f(z)|\leq M$ 对任意 $f \in \mathcal{F}$ 成立。令 $|z-a|<r /2$，$\gamma$ 为圆 $|z-a|=r$，则有

$$
\begin{align}
|f(z)-f(a)| &= \dfrac{1}{2\pi} \left\lvert  \int_{\gamma} \dfrac{f(w)(z-a)}{(w-a)(w-z)} \mathrm{d} w  \right\rvert  \\
&\leq \dfrac{4M}{r} |z-a|
\end{align}
$$

取 $\delta<\min \left\{  \dfrac{r}{2}, \dfrac{r}{4M}\varepsilon  \right\}$，则 $|z-a|<\delta$ 蕴含 $|f(z)-f(a)|<\varepsilon$ 对任意 $f \in \mathcal{F}$ 成立，这就完成了证明。

**定理 6.2.9**

集合 $\mathcal{F}\subset H(G)$ 紧致当且仅当 $\mathcal{F}$ 闭且局部有界。

# Section 3: 亚纯函数空间 $M(G)$

设 $G$ 是一个区域，$f$ 是 $G$ 上的亚纯函数。如果我们定义当 $z$ 是 $f$ 的极点时 $f(z)=\infty$，那么 $f\colon G\to \mathbb{C}_{\infty}$ 就是一个连续函数。我们将 $G$ 上所有亚纯函数构成的集合记作 $M(G)$，并将其视为 $C(G,\mathbb{C}_{\infty})$ 的一个子集。本节我们就来研究 $M(G)$ 的性质。

回顾一下，$\mathbb{C}_{\infty}$ 上的度量 $d$ 定义如下：对于 $z_{1},z_{2}\in \mathbb{C}$，有

$$
\begin{gather}
d(z_{1},z_{2})=\dfrac{2|z_{1}-z_{2}|}{\sqrt{ (1+|z_{1}|^{2})(1+|z_{2}|^{2}) }}
\end{gather}
$$

并且对 $z \in \mathbb{C}$ 有

$$
\begin{gather}
d(z,\infty)=\dfrac{2}{\sqrt{ 1+|z_{}|^{2} }}
\end{gather}
$$

注意到，对于复数 $z_{1},z_{2}\neq 0$，我们有

$$
\begin{gather}
d(z_{1},z_{2})=d\left( \dfrac{1}{z_{1}},\dfrac{1}{z_{2}} \right)
\end{gather}
$$

并且对 $z\neq 0$ 有

$$
\begin{gather}
d(z,0)=d\left( \dfrac{1}{z},\infty \right)
\end{gather}
$$

此外，如果 $z_{n},z \in \mathbb{C}$ 满足 $d(z_{n},z)\to 0$，那么就有 $|z_{n}-z| \to 0$.

关于 $\mathbb{C}$ 与 $\mathbb{C}_{\infty}$ 上度量的关系如下定理所示。为了避免歧义，我们用 $B(a,r)$ 来表示 $\mathbb{C}$ 中的开球，用 $B_{\infty}(a,r)$ 来表示 $\mathbb{C}_{\infty}$ 中的开球。

**定理 6.3.1**

1. 如果 $a \in \mathbb{C},r>0$，那么存在 $\rho>0$ 使得 $B_{\infty}(a,\rho)\subset B(a,r)$. 反之，如果给定 $\rho>0$，那么存在 $r>0$ 使得 $B(a,r)\subset B_{\infty}(a,\rho)$.
2. 如果 $\rho>0$，那么存在紧致集 $K\subset \mathbb{C}$ 使得 $\mathbb{C}_{\infty}\setminus K\subset B_{\infty}(\infty,\rho)$. 反之，如果给定紧致集 $K$，那么存在 $\rho>0$ 使得 $B_{\infty}(\infty,\rho)\subset \mathbb{C}_{\infty}\setminus K$.

**证明**

(1). 给定 $B(a,r)$，由于

$$
\begin{gather}
|z-a|=\dfrac{1}{2} d(z,a) \sqrt{ (1+|a|^{2})(1+|z|^{2}) }
\end{gather}
$$

且当 $|z-a|<1$ 时有 $\sqrt{ 1+|z|^{2} }< \sqrt{ 1+(|a|+1)^{2} }$，令

$$
\begin{gather}
C=\dfrac{1}{2}\sqrt{ 1+|a|^{2} } \sqrt{ 1+(|a|+1)^{2} }
\end{gather}
$$

则取 $\rho=\min \left\{  \dfrac{1}{C},\dfrac{r}{C}  \right\}$，从而当 $d(z,a)<\rho$ 时有 $|z-a|<r$.

反之，由于

$$
\begin{gather}
d(z,a)=\dfrac{2|z-a|}{\sqrt{ 1+|a|^{2} }\sqrt{ 1+|z|^{2} }}\leq \dfrac{2|z-a|}{\sqrt{ 1+|a|^{2} }}
\end{gather}
$$

取 $r=\dfrac{\sqrt{ 1+|a|^{2} }}{2}\rho$，于是当 $|z-a|<r$ 时就有 $d(z,a)<\rho$.

(2). 给定 $B_{\infty}(\infty,\rho)$，由于 $d(\infty,z)$ 的最大值为 $2$，故当 $\rho\geq 2$ 时有 $\mathbb{C}_{\infty}\subset B_{\infty}(\infty,\rho)$，此时取 $K=\varnothing$ 即可。当 $0<\rho<2$ 时，我们有

$$
\begin{gather}
d(\infty,z)=\dfrac{2}{\sqrt{ 1+|z|^{2} }}<\rho \iff |z|^{2}> \dfrac{4}{\rho^{2}}-1
\end{gather}
$$

取 $R>\sqrt{ \dfrac{4}{\rho^{2}}-1 }$，$K=\overline{B(0,R)}$，则 $K$ 闭且有界，从而紧致。此外，对 $z \not\in K$，我们有 $|z|>R$，即 $d(\infty,z)<\rho$，这表明 $\mathbb{C}_{\infty}\setminus K\subset B_{\infty}(\infty,\rho)$.

反之，给定紧致集 $K$，其有界，因此存在 $M$ 使得 $K\subset  \overline{B(0,M)}$，于是取 $\rho=\dfrac{2}{\sqrt{ 1+M^{2} }}$，则当 $d(z,\infty)<\rho$ 时有 $|z|>M$，即 $B_{\infty}(\infty,\rho)\subset \mathbb{C}_{\infty}\setminus K$.

以上的定理表明了两个基本事实：其一是 $\mathbb{C}$ 上的标准拓扑与 $\mathbb{C}$ 作为 $\mathbb{C}_{\infty}$ 的子空间所诱导的拓扑是等价的；其二是 $\mathbb{C}_{\infty}$，作为 $\mathbb{C}$ 的单点紧化，其无穷远点的邻域正是由 $\mathbb{C}$ 中紧致集的补集构成的。

下面我们来研究 $M(G)$ 上的收敛性。第一个观察是，$M(G)$ 是不完备的：如果 $f_{n}(z)=n$，那么 $f_{n}$ 是 $M(G)$ 中的 Cauchy 序列，然而其极限 $f(z)=\infty$ 不是亚纯函数。不过，下面的定理表明，这就是最坏的情况了。

**定理 6.3.2**

设 $(f_{n})\subset M(G)$，$f \in C(G,\mathbb{C}_{\infty})$ 满足 $f_{n}\to f$，则或者 $f \in M(G)$，或者 $f=\infty$ 为常数。如果每个 $f_{n}$ 都是解析函数，那么或者 $f$ 解析，或者 $f=\infty$ 为常数。

**证明**

设 $a \in G$ 满足 $f(a)\neq \infty$，取 $M=|f(a)|$. 于是，根据定理 6.3.1，我们可以找到 $\rho>0$ 使得 $B_{\infty}(f(a),\rho)\subset B(f(a),M)$. 由于 $f_{n}\to f$，故存在 $N$ 使得当 $n\geq N$ 时有 $d(f_{n}(z),f(z))<\rho /2$. 又 $\{ f,f_{1},f_{2},\dots \}$ 在 $C(G,\mathbb{C}_{\infty})$ 中紧致，从而等度连续。即，存在 $r>0$ 使得对任意 $n$ 有 $|z-a|<r$ 蕴含 $d(f_{n}(z),f_{n}(a))<\rho /2$，从而 $d(f_{n}(z),f(a))<\rho$ 对 $|z-a|<r$ 和 $n\geq N$ 成立。但根据 $\rho$ 的选取，我们有

$$
\begin{gather}
|f_{n}(z)|\leq |f_{n}(z)-f(a)|+|f(a)|\leq 2M
\end{gather}
$$

对 $z \in \overline{B(a,r)}$ 和 $n\geq N$ 成立，从而

$$
\begin{gather}
d(f_{n}(z),f(z))\geq \dfrac{2}{1+4M^{2}}|f_{n}(z)-f(z)|
\end{gather}
$$

由于 $d(f_{n}(z),f(z))\to 0$ 对 $z \in \overline{B(a,r)}$ 一致，故 $f_{n}$ 在 $\overline{B(a,r)}$ 上一致收敛于 $f$. 又由于 $n$ 充分大时 $f_{n}$ 在 $B(a,r)$ 上有界，从而没有极点，因此在 $a$ 的邻域上解析，这就表明 $f$ 在 $a$ 的邻域上解析。

现在设 $a \in G$ 满足 $f(a)=\infty$. 对于 $g \in C(G,\mathbb{C}_{\infty})$，我们定义 $\dfrac{1}{g}(z)=\dfrac{1}{g(z)}$ 如果 $g(z)\neq 0$，定义 $\dfrac{1}{g}(z)=\infty$ 如果 $g(z)=0$，则 $\dfrac{1}{g}\in C(G,\mathbb{C}_{\infty})$. 根据度量 $d$ 的性质，由 $f_{n}\to f$ 我们可得 $\dfrac{1}{f_{n}}\to \dfrac{1}{f}$，由于 $\dfrac{1}{f_{n}}$ 是亚纯函数，因此根据上一段证明，存在 $N$ 和 $r>0$ 使得对 $n\geq N$ 有 $\dfrac{1}{f},\dfrac{1}{f_{n}}$ 在 $B(a,r)$ 上解析，且 $\dfrac{1}{f_{n}}\to \dfrac{1}{f}$ 在 $B(a,r)$ 上一致。于是由 Hurwitz 定理可知或者 $\dfrac{1}{f}=0$ 恒成立或者 $\dfrac{1}{f}$ 在 $B(a,r)$ 上有孤立零点。因此，如果 $f$ 不恒为 $\infty$，那么 $f$ 在 $B(a,r)$ 上亚纯。综合以上两段证明，我们可知如果 $f$ 不恒为 $\infty$，那么 $f$ 就在 $G$ 上亚纯。

如果每个 $f_{n}$ 都解析，那么 $\dfrac{1}{f_{n}}$ 在 $B(a,r)$ 中无零点，从而 Hurwitz 定理表明 $\dfrac{1}{f}=0$ 为常数或者 $\dfrac{1}{f}$ 无零点。但由于 $f(a)=\infty$，故 $\dfrac{1}{f(a)}=0$，因此必然有 $\dfrac{1}{f}=0$，即 $f=\infty$ 在 $B(a,r)$ 上恒成立。结合上一段证明，我们可得 $f=\infty$ 或者 $f$ 在 $G$ 上解析。

**定理 6.3.3**

$M(G)\cup \{ \infty \}$ 是一个完备度量空间。

**定理 6.3.4**

$H(G)\cup \{ \infty \}$ 是 $C(G,\mathbb{C}_{\infty})$ 中的闭集。

接下来我们讨论亚纯函数的正规性。为此，我们必须引入以下表达式：

$$
\begin{gather}
\mu(f)(z)=\dfrac{2|f'(z)|}{1+|f(z)|^{2}}
\end{gather}
$$

这是因为如果 $f\colon G\to \mathbb{C}_{\infty}$ 是亚纯函数，那么 $z$ 和 $z'$ 接近时 $d(f(z),f(z'))$ 可以由 $\mu(f)(z)|z-z'|$ 来近似。于是，如果 $\mu(f)$ 是有界的，那么 $f$ 就是一个 Lipschitz 函数。如果一族函数的 $\mu(f)$ 一致有界，那么这一族函数将是一致 Lipschitz 的，这是证明正规性的一个关键步骤。

然而，如果 $a$ 是 $f$ 的极点，那么 $\mu(f)(a)$ 无定义，因为 $f'(a)$ 在此处无定义。为修复这个问题，我们考虑 $a$ 处的 Laurent 展开

$$
\begin{gather}
f(z)=\dfrac{A_{m}}{(z-a)^{m}}+\dots+\dfrac{A_{1}}{z-a}+g(z)
\end{gather}
$$

其中 $g$ 解析。对于 $z\neq a$ 我们有

$$
\begin{gather}
f'(z)=g'(z) - \left( \dfrac{mA_{m}}{(z-a)^{m+1}}+\dots+\dfrac{A_{1}}{(z-a)^{2}} \right)
\end{gather}
$$

于是

$$
\begin{align}
\dfrac{2|f'(z)|}{1+|f(z)|^{2}} &= \dfrac{2 \left\lvert  \dfrac{mA_{m}}{(z-a)^{m+1}}+\dots+\dfrac{A_{1}}{(z-a)^{2}}-g'(z)  \right\rvert }{1+\left\lvert  \dfrac{A_{m}}{(z-a)^{m}}+\dots+\dfrac{A_{1}}{z-a}+g(z)  \right\rvert ^{2}} \\
&= \dfrac{2|z-a|^{2m}\lvert mA_{m}+\dots+A_{1}(z-a)^{m-1}-g'(z)(z-a)^{m+1} \rvert }{|z-a|^{m+1}+\lvert A_{m}+\dots+A_{1}(z-a)^{m-1}+g(z)(z-a)^{m} \rvert ^{2}}
\end{align}
$$

因此当 $m\geq 2$ 时有

$$
\begin{gather}
\lim_{ z \to a } \dfrac{2|f'(z)|}{1+|f(z)|^{2}}=0
\end{gather}
$$

而 $m=1$ 时有

$$
\begin{gather}
\lim_{ z \to a } \dfrac{2|f'(z)|}{1+|f(z)|^{2}}=\dfrac{2}{|A_{1}|}
\end{gather}
$$

从而我们可以定义：

**定义 6.3.5**

设 $f$ 是区域 $G$ 上的亚纯函数，定义 $\mu(f)\colon G\to \mathbb{R}$ 为

$$
\begin{gather}
\mu(f)(z)=\dfrac{2|f'(z)|}{1+|f(z)|^{2}}
\end{gather}
$$

如果 $z$ 不是 $f$ 的极点。并定义

$$
\begin{gather}
\mu(f)(a)=\lim_{ z \to a } \dfrac{2|f'(z)|}{1+|f(z)|^{2}}
\end{gather}
$$

如果 $a$ 是 $f$ 的极点。

根据定义我们立即得到 $\mu(f) \in C(G,\mathbb{C})$.

**定理 6.3.6**

$\mathcal{F}\subset M(G)$ 是 $C(G,\mathbb{C}_{\infty})$ 中的正规族当且仅当 $\mu(\mathcal{F})=\{ \mu(f) \mid f \in \mathcal{F} \}$ 是局部有界的。

**证明**

假设 $\mathcal{F}$ 正规但 $\mu(\mathcal{F})$ 不局部有界，则存在紧致集 $K$，$(f_{n})\subset \mathcal{F}$ 以及 $(z_{n})\subset K$ 使得

$$
\begin{gather}
\lim_{ n \to \infty } \mu(f_{n})(z_{n})=\infty
\end{gather}
$$

由于 $K$ 紧致，故 $(z_{n})$ 有收敛于 $z_{0}\in K$ 的子序列，仍记作 $(z_{n})$. 又由于 $\mathcal{F}$ 正规，故 $(f_{n})$ 有收敛于 $f \in C(G,\mathbb{C}_{\infty})$ 的子序列，仍记为 $(f_{n})$. 则根据定理 6.3.2，$f=\infty$ 或者 $f \in M(G)$.

(1). 如果 $f(z_{0})\neq \infty$，则 $f$ 在 $z_{0}$ 的邻域上解析，且有 $r>0$ 使得 $f$ 在 $\overline{B(z_{0},r)}\subset G$ 上有界，并且 $f_{n}$ 在 $\overline{B(z_{0},r)}$ 上一致收敛于 $f$. 于是，根据定理 6.2.1，序列 $(f_{n}')$ 在 $\overline{B(z_{0},r /2)}$ 上一致收敛于 $f'$，从而 $\mu(f_{n})$ 在 $\overline{B(z_{0},r /2)}$ 上一致收敛于 $\mu(f)$，因此 $\mu(f)$ 在 $\overline{B(z_{0},r /2)}$ 上连续，从而有界，但这与 $\mu(f_{n})(z_{n})\to \infty$ 矛盾。

(2). 如果 $f(z_{0})=\infty$，考虑 $g_{n}=\dfrac{1}{f_{n}}$，则 $g_{n}$ 在 $z_{0}$ 的邻域上解析，并且有 $r>0$ 使得 $g_{n}\to 0$ 在 $\overline{B(z_{0},r)}$ 上一致，从而 $g_{n}'\to 0$ 在 $\overline{B(z_{0},r /2)}$ 上一致。此外，当 $f_{n}(z)\neq 0,\infty$ 时，有 $g_{n}'=- \dfrac{f_{n}'}{f_{n}^{2}}$，于是

$$
\begin{gather}
\mu(g_{n})(z)=\dfrac{2|g_{n}'(z)|}{1+|g_{n}(z)|^{2}}=\dfrac{2|f_{n}'(z)|}{1+|f_{n}(z)|^{2}}=\mu(f_{n})(z)
\end{gather}
$$

又由于 $\mu(g_{n}),\mu(f_{n})$ 是连续函数，故以上等式在 $\overline{B(z_{0},r /2)}$ 上成立，从而有 $\mu(f_{n})\to 0$，这与 $\mu(f_{n})(z_{n})\to \infty$ 矛盾。

这就证明了：如果 $\mathcal{F}$ 正规，那么 $\mu(\mathcal{F})$ 局部有界。

下面，我们假设 $\mu(\mathcal{F})$ 局部有界，并使用 Arzela-Ascoli 定理来证明 $\mathcal{F}$ 的正规性。由于 $\mathbb{C}_{\infty}$ 是紧致的，故我们只需证明 $\mathcal{F}$ 在 $G$ 的每一点上等度连续。令 $K$ 为 $G$ 中的闭圆盘，并令 $M$ 满足 $\mu(f)(z)\leq M$ 对 $z \in K$ 和 $f \in \mathcal{F}$ 成立。设 $z,z'$ 是 $K$ 中的任意点。

固定 $f \in \mathcal{F}$，假设 $z,z'$ 都不是 $f$ 的极点，取 $\alpha>0$，则我们可以找到点 $z=w_{0},w_{1},\dots,w_{n}=z'$ 满足以下条件：

1. 如果 $w \in[w_{k-1},w_{k}]$，那么 $w$ 不是 $f$ 的极点
2. $\displaystyle \sum_{k=1}^{n}|w_{k}-w_{k-1}|\leq 2|z-z'|$
3. $\dfrac{1+|f(w_{k})|^{2}}{\sqrt{ 1+|f(w_{k})|^{2} }\sqrt{ 1+|f(w_{k-1})|^{2} }}-1<\alpha$
4. $\left\lvert  \dfrac{f(w_{k})-f(w_{k-1})}{w_{k}-w_{k-1}}-f'(w_{k-1})  \right\rvert<\alpha$

为证明这种取点的存在性，我们在 $K$ 中选择一条折线 $P$，其满足性质 1 和 2，然后用满足类似 3 和 4 性质的开圆盘覆盖 $P$，选取有限个开覆盖，并取 $P$ 上的点 $w_{0},\dots,w_{n}$ 使得每个 $[w_{k-1},w_{k}]$ 都包含在一个圆盘内，则按这种方法选出的点满足上述四个条件。设 $\beta_{k}$ 为性质 3 中表达式的分母，则我们有

$$
\begin{align}
d(f(z),f(z')) &\leq \sum_{k=1}^{n} d(f(w_{k-1}),f(w_{k})) \\
&= \sum_{k=1}^{n} \dfrac{2}{\beta_{k}} |f(w_{k})-f(w_{k-1})| \\
&\leq \sum_{k=1}^{n} \dfrac{2}{\beta_{k}} \left\lvert  \dfrac{f(w_{k})-f(w_{k-1})}{w_{k}-w_{k-1}}-f'(w_{k-1})  \right\rvert \lvert w_{k}-w_{k-1} \rvert  \\
&+\sum_{k=1}^{n} \dfrac{2}{\beta_{k}}\lvert f'(w_{k-1}) \rvert \lvert w_{k}-w_{k-1} \rvert 
\end{align}
$$

利用 $2|f'(w)|\leq M(1+|f(w)|^{2})$ 以及 $w_{0},\dots,w_{n}$ 的性质，可得

$$
\begin{align}
d(f(z),f(z')) &\leq 2\alpha \sum_{k=1}^{n} \dfrac{1}{\beta_{k}} |w_{k}-w_{k-1}|+M \sum_{k=1}^{n} \dfrac{1+|f(w_{k})|^{2}}{\beta_{k}}|w_{k}-w_{k-1}| \\
&\leq 4\alpha |z-z'|+2M(1+\alpha)|z-z'|
\end{align}
$$

由于 $\alpha>0$ 是任意的，故

$$
\begin{gather}
d(f(z),f(z'))\leq 2M |z-z'|
\end{gather}
$$

当 $z,z'$ 不是 $f$ 的极点时成立。

现设 $z'$ 是 $f$ 的极点而 $z$ 不是。如果 $w \in K$ 不是 $f$ 的极点，那么根据上文有

$$
\begin{align}
d(f(z),f(z')) &\leq d(f(z),f(w))+d(f(w),\infty) \\
&\leq 2M|z-w|+d(f(w),\infty)
\end{align}
$$

由于极点是孤立的，因此我们可以选取 $w$ 使得 $w\to z'$ 且 $w$ 不是极点，此时有 $f(w)\to f(z')=\infty$ 而 $|z-w| \to |z-z'|$，这给出

$$
\begin{gather}
d(f(z),f(z'))\leq 2M|z-z'|
\end{gather}
$$

当 $z,z'$ 均是 $f$ 的极点时，则显然有上式成立。因此，如果 $K=\overline{B(a,r)}$ 且 $\varepsilon>0$ 给定，取 $\delta=\min \{ r,\varepsilon /2M \}$，则我们有 $|z-a|<\delta$ 蕴含 $d(f(z),f(a))<\varepsilon$. 由于 $\delta$ 的选取与 $f$ 无关，因此以上不等式对 $f \in \mathcal{F}$ 一致，即证 $\mathcal{F}$ 在 $a$ 点等度连续。这就完成了证明。

# Section 4: Riemann 映射定理

我们希望在 $\mathbb{C}$ 上的区域之间建立一个等价关系。在这之后我们将证明 $\mathbb{C}$ 上的所有真单连通域均等价于单位开圆盘 $D=\{ z \mid |z|<1 \}$，因此彼此之间都等价。

**定义 6.4.1** 共形等价（conformally equivalent）

一个区域 $G_{1}$ **共形等价于** $G_{2}$，如果存在解析函数 $f\colon G_{1}\to \mathbb{C}$ 使得 $f$ 是单射且 $f[G_{1}]=G_{2}$.

显然，共形等价是一个等价关系。根据 Liouville 定理，我们立即可知 $\mathbb{C}$ 不等价于任何有界区域。此外，如果 $G_{1}$ 是单连通的，我们也容易证明 $G_{2}=f[G_{1}]$ 也是单连通的。此外，如果 $f$ 是平方根函数的主分支，则 $f$ 是单射，并且 $f$ 将 $\mathbb{C}\setminus\{ z \mid z\leq 0 \}$ 满射到右半平面。

**定理 6.4.2** Riemann 映射定理（Riemann Mapping Theorem）

设 $G\neq \mathbb{C}$ 是一个单连通域，令 $a \in G$，则存在唯一的解析函数 $f\colon G\to \mathbb{C}$ 满足以下性质：

1. $f(a)=0$ 且 $f'(a)>0$
2. $f$ 是单射
3. $f[G]=D=\{ z \mid |z|<1 \}$

以上定理的唯一性部分相当简单：如果 $g$ 也满足以上性质，那么 $f\circ g^{-1}\colon D\to D$ 是一个解析双射，并且 $f\circ g^{-1}(0)=f(a)=0$，从而由定理 5.2.3 知存在 $|c|=1$ 满足 $f\circ g^{-1}(z)=cz$. 但 $f(z)=cg(z)$ 表明 $0<f'(a)=cg'(a)$，根据 $g'(a)>0$ 有 $c=1$，即得 $f=g$.

为了给出存在性证明的动机，我们考虑满足性质 1, 2 以及 $|f(z)|<1$ 的解析函数 $f$ 构成的集合 $\mathcal{F}$. 我们的想法是选取一个 $f$ 使得性质 3 成立。假设 $\{ K_{n} \}$ 是 $G$ 中的一列紧致集，$G=\bigcup_{n=1}^{\infty}K_{n}$，并且 $a \in K_{n}$ 对任意 $n$ 成立，则 $\{ f[K_{n}] \}$ 就是 $D$ 中的一列紧致集。当 $n$ 增大时，$f[K_{n}]$ 变得越来越大，如果我们取使得 $f'(a)$ 最大的 $f$，这就是说 $f$ 在 $a$ 处的增长速度最快，从而有更大的可能覆盖整个圆盘，即 $\bigcup_{n=1}^{\infty}f[K_{n}]=D$.

在给出证明之前，我们指出在本证明中用到的关于单连通性的性质只有无零点的解析函数有解析平方根。因此我们只需证明以下引理：

**引理 6.4.3**

设 $G\neq \mathbb{C}$ 满足其上的任意无零点解析函数都有解析平方根，令 $a \in G$，则存在解析函数 $f\colon G\to \mathbb{C}$ 使得：

1. $f(a)=0$ 且 $f'(a)>0$
2. $f$ 是单射
3. $f[G]=D$

**证明**

定义

$$
\begin{gather}
\mathcal{F}=\{ f \in H(G) \mid f\text{单},f(a)=0,f'(a)>0,f[G]\subset D \}
\end{gather}
$$

由于 $f[G]\subset D$，因此 $\mathcal{F}$ 局部有界，从而由 Montel 定理知如果 $\mathcal{F}\neq \varnothing$，那么 $\mathcal{F}$ 是正规族。因此我们首先要证明 $\mathcal{F}$ 非空。在这之后我们将证明 $\overline{\mathcal{F}}=\mathcal{F}\cup \{ 0 \}$，知道这两个结论我们就可证明这个引理。

事实上，假设以上两个结论成立，考虑 $H(G)$ 到 $\mathbb{C}$ 的映射 $f\mapsto f'(a)$，它是一个连续函数，因此存在 $f \in \overline{\mathcal{F}}$ 使得 $f'(a)\geq g'(a)$ 对任意 $g \in \mathcal{F}$ 成立。由于 $\mathcal{F}\neq \varnothing$，故 $f \in \mathcal{F}$. 下面我们要证 $f[G]=D$. 假设有 $w \in D$ 使得 $w \not\in f[G]$，则函数

$$
\begin{gather}
\dfrac{f(z)-w}{1-\overline{w} f(z)}
\end{gather}
$$

在 $G$ 上解析，并且无零点。根据假设，存在解析函数 $h$ 满足

$$
\begin{gather}
h(z)^{2}=\dfrac{f(z)-w}{1-\overline{w}f(z)}
\end{gather}
$$

由于 Mobius 变换 $T(\zeta)=\dfrac{\zeta-w}{1-\overline{w}\zeta}$ 将 $D$ 满射到 $D$，故 $h[G]\subset D$. 定义 $g\colon G\to \mathbb{C}$ 为

$$
\begin{align}
g(z)=\dfrac{|h'(a)|}{h'(a)} \dfrac{h(z)-h(a)}{1-\overline{h(a)} h(z)}
\end{align}
$$

则 $g[G]\subset D$，$g(a)=0$，并且 $g$ 是单射。此外

$$
\begin{align}
g'(a) &= \dfrac{|h'(a)|}{h'(a)} \dfrac{h'(a)(1-|h(a)|^{2})}{(1-|h(a)|^{2})^{2}}= \dfrac{|h'(a)|}{1-|h(a)|^{2}}
\end{align}
$$

然而 $|h'(a)|^{2}=|w|$，并且对 $h(z)^{2}$ 求导得到

$$
\begin{gather}
2h(a)h'(a)=f'(a)(1-|w|^{2})
\end{gather}
$$

因此

$$
\begin{align}
g'(a) &= \dfrac{f'(a)(1-|w|^{2})}{2 \sqrt{ |w| }} \dfrac{1}{1-|w|} \\
&= f'(a) \dfrac{1+|w|}{2\sqrt{ |w| }} > f'(a)
\end{align}
$$

这与 $f$ 的选取矛盾，因此 $f[G]=D$.

现在我们来证 $\mathcal{F}\neq \varnothing$ 且 $\overline{\mathcal{F}}=\mathcal{F}\cup \{ 0 \}$. 由于 $G\neq \mathbb{C}$，令 $b \in \mathbb{C}\setminus G$ 并定义解析函数 $g$ 使得 $g(z)^{2}=z-b$. 如果 $z_{1},z_{2}\in G$ 满足 $g(z_{1})=\pm g(z_{2})$，那么 $z_{1}=z_{2}$. 特别地，$g$ 是单射。根据开映射定理，存在 $r>0$ 使得

$$
\begin{gather}
B(g(a),r) \subset g[G]
\end{gather}
$$

因此如果有 $z \in G$ 使得 $g(z) \in B(-g(a),r)$，那么 $r>|g(z)+g(a)|$，于是有 $w \in G$ 满足 $g(w)=-g(z)$，这表明 $w=z$，即 $g(z)=0$. 但 $z-b=g(z)^{2}=0$ 表明 $b \in G$，矛盾。因此

$$
\begin{gather}
g[G] \cap B(-g(a),r)=\varnothing
\end{gather}
$$

设 $U=B(-g(a),r)$，则存在 Mobius 变换 $T$ 使得 $T[\mathbb{C}_{\infty}\setminus \overline{U}]=D$，令 $g_{1}=T\circ g$，则 $g_{1}$ 解析并且 $g_{1}[G]\subset D$. 如果 $\alpha=g_{1}(a)$，令 $g_{2}=\varphi_{\alpha}\circ g_{1}$，则 $g_{2}$ 解析，$g_{2}[G]\subset D$，并且 $g_{2}(a)=0$. 再取 $|c|=1$ 使得 $g_{3}=cg_{2}$ 在 $z=a$ 处有正导数，从而 $g_{3}\in \mathcal{F}$. 即证 $\mathcal{F}\neq \varnothing$.

现设 $(f_{n})\subset \mathcal{F}$，并且在 $H(G)$ 中 $f_{n}\to f$，则显然 $f(a)=0$，$f'(a)\geq 0$. 令 $z_{1}\in G$，取 $\zeta=f(z_{1})$，$\zeta_{n}=f_{n}(z_{1})$. 再令 $z_{2}\neq z_{1}$，取以 $z_{2}$ 为中心的闭圆盘 $K$ 满足 $z_{1} \not\in K$，则 $f_{n}(z)-\zeta_{n}$ 在 $K$ 上无零点。由于在 $K$ 上一致有 $f_{n}(z)-\zeta_{n}\to f(z)-\zeta$，根据 Hurwitz 定理，$f(z)-\zeta$ 在 $K$ 上无零点，或者 $f=\zeta$ 为常数。

如果 $f=\zeta$，由于 $f(a)=0$，那么 $f=0$ 恒成立。否则，当 $z_{1}\neq z_{2}$ 时我们就有 $f(z_{1})\neq f(z_{2})$，即 $f$ 是单射。假设 $f'(a)=0$，那么由幂级数展开得 $f(z)-f(a)=(z-a)^{k}m(z)$，其中 $k\geq 2$，$m$ 解析。于是定理 3.4.3 表明，存在 $\varepsilon,\delta$ 使得当 $|\omega-f(a)|<\delta$ 时 $f(z)=\omega$ 在 $B(a,\varepsilon)$ 内有 $k$ 个单根，但这与 $f$ 是单射矛盾。因此 $f'(a)>0$ 从而 $f \in \mathcal{F}$. 这就证明了 $\overline{\mathcal{F}}=\mathcal{F}\cup \{ 0 \}$. 以上就完成了证明。

**定理 6.4.4**

$\mathbb{C}$ 上的单连通域在共形等价下只有两个等价类：其一只包含 $\mathbb{C}$ 本身，剩下的包含所有的真单连通域。

# Section 5: Weierstrass 分解定理

考虑这样一个问题：给定在 $G$ 中没有极限点的序列 $(a_{k})$，以及一列正整数 $(m_{k})$，是否存在 $G$ 上的解析函数 $f$ 使得 $f$ 仅在 $z=a_{k}$ 处有一个重数为 $m_{k}$ 的零点？这一问题的答案由本节的主定理：Weierstrass 分解定理给出。

如果序列 $(a_{k})$ 中只有有限项，那么显然 $f(z)=(z-a_{1})^{m_{1}}\cdots (z-a_{n})^{m_{n}}$ 就是所求的函数。我们要问的是，如果 $(a_{k})$ 有无限项会怎么样？为此，我们必须首先讨论序列的无穷乘积。

**定义 6.5.1** 无穷乘积（infinite product）

设 $(z_{n})$ 是一列复数，如果部分积序列

$$
\begin{gather}
p_{n}=\prod_{k=1}^{n} z_{k} 
\end{gather}
$$

有极限且等于 $z$，那么就称**无穷乘积** $\prod_{n=1}^{\infty}z_{n}$ 收敛于 $z$，记作

$$
\begin{gather}
z=\prod_{n=1}^{\infty} z_{n}
\end{gather}
$$

显然，如果 $(z_{n})$ 中有一项为零，那么无穷乘积必然收敛于零。此外，假设每个 $z_{n}\neq 0$，并且 $z=\prod_{n=1}^{\infty}z_{n}$ 存在且不为零，那么每个 $p_{n}\neq 0$，且 $\dfrac{p_{n}}{p_{n-1}}=z_{n}$，由 $p_{n}\to z$ 可得 $z_{n}\to 1$. 这就是说，除了 $z=0$ 的情况，无穷乘积存在的一个必要条件就是序列中的项趋于 $1$. 另一方面，如果 $z=0$，那么 $z_{n}\to 1$ 不一定成立：设 $z_{n}=a,|a|<1$，那么 $\prod_{n=1}^{\infty}z_{n}=0$，但 $z_{n}\to a \neq 1$.

由于对数函数将乘法变成加法，因此我们可以通过级数 $\sum \log z_{n}$ 来得到无穷乘积 $\prod z_{n}$ 的信息。然而，在我们考虑以上级数之前，我们必须确保 $z_{n}$ 都落在一个单连通域内，从而 $\log z_{n}$ 是有定义的。如果无穷乘积的值不为零，那么 $z_{n}\to 1$，从而我们可以不失一般性地假设 $\mathrm{Re}\,z_{n}>0$. 现假设 $\sum_{n=1}^{\infty} \log z_{n}$ 收敛，令 $s_{n}=\sum_{k=1}^{n}\log z_{k}$，则 $s_{n}\to s$ 且 $e^{s_{n}}\to e^{s}$，而 $e^{s_{n}}=\prod_{k=1}^{n}z_{k}$，因此 $\prod_{n=1}^{\infty}z_{n}=e^{s}\neq 0$.

**定理 6.5.2**

设 $\mathrm{Re}\,z_{n}>0$，则 $z=\prod_{n=1}^{\infty}z_{n}\neq 0$ 当且仅当级数 $\sum\log z_{n}$ 收敛。

**证明**

令 $p_{n}=\prod_{k=1}^{n}z_{k}$，$z=r e^{i\theta}$，$-\pi<\theta\leq \pi$，并且 $\log p_{n}=\log |p_{n}|+i\theta_{n}$，其中 $\theta-\pi<\theta_{n}\leq\theta+\pi$. 设 $s_{n}=\sum_{k=1}^{n}\log z_{k}$，则 $e^{s_{n}}=p_{n}$，从而 $s_{n}=\log p_{n}+2\pi i k_{n}$. 假设 $p_{n}\to z$，则 $\log p_{n}-\log p_{n-1}\to 0$，即 $s_{n}-s_{n-1}=\log z_{n}\to 0$，这表明 $k_{n}-k_{n-1}\to 0$，但 $k_{n} \in \mathbb{Z}$，因此存在 $N$ 使得当 $m,n\geq N$ 时有 $k_{m}=k_{n}=k$. 于是 $s_{n}\to \log z+2\pi ik$，即证 $\sum \log z_{n}$ 收敛。由定理之前的讨论可知反向的蕴含成立，这就完成了证明。

有时候，$\sum \log z_{n}$ 的收敛性证明与 $\prod z_{n}$ 的困难程度相当，我们需要找到一个更好的充要条件。考虑 $\log(1+z)$ 在 $z=0$ 处的幂级数展开

$$
\begin{gather}
\log(1+z)=\sum_{n=1}^{\infty} (-1)^{n-1} \dfrac{z^{n}}{n}
\end{gather}
$$

其收敛半径是 $1$，并且当 $|z|<1$ 时有

$$
\begin{align}
\left\lvert  1- \dfrac{\log(1+z)}{z}  \right\rvert &= \left\lvert  \dfrac{1}{2}z-\dfrac{1}{3}z^{2}+\cdots  \right\rvert  \\
&\leq \dfrac{1}{2}(|z|+|z|^{2}+\cdots) \\
&= \dfrac{1}{2} \dfrac{|z|}{1-|z|}
\end{align}
$$

于是当 $|z|< \dfrac{1}{2}$ 时，有

$$
\begin{gather}
\left\lvert  1-\dfrac{\log(1+z)}{z}  \right\rvert \leq \dfrac{1}{2}
\end{gather}
$$

即

$$
\begin{gather}
\dfrac{1}{2}|z|\leq \lvert \log(1+z) \rvert \leq \dfrac{3}{2}|z|
\end{gather}
$$

根据这个不等式，我们可以证明以下定理：

**定理 6.5.3**

设 $\mathrm{Re}\,z_{n}>-1$，则 $\sum \log(1+z_{n})$ 绝对收敛当且仅当 $\sum z_{n}$ 绝对收敛。

**证明**

如果 $\sum |z_{n}|$ 收敛那么 $|z_{n}| \to 0$，于是当 $n$ 充分大时有 $|z_{n}|<1 /2$，从而 $\sum \lvert \log(1+z_{n}) \rvert$ 由一个收敛级数控制，从而收敛。如果 $\sum \lvert \log(1+z_{n}) \rvert$ 收敛，那么 $\log(1+z_{n})\to 0$，同样有 $z_{n}\to 0$，从而 $\sum|z_{n}|$ 由收敛级数控制，这就完成了证明。

我们希望定义无穷乘积的绝对收敛，使得绝对收敛蕴含原乘积收敛。因此，$\prod |z_{n}|$ 是不可行的，因为 $z_{n}=-1$ 不满足以上的条件。在定理 6.5.2 的基础上，我们给出以下定义：

**定义 6.5.4** 绝对收敛（absolute convergence）

设 $\mathrm{Re}\,z_{n}>0$，称无穷乘积 $\prod_{n=1}^{\infty}z_{n}$ **绝对收敛**，如果级数 $\sum \log z_{n}$ 绝对收敛。

由于级数的绝对收敛蕴含收敛，因此以上定义能够满足我们的要求。此外，绝对收敛的乘积还满足其他类似的性质，例如绝对收敛乘积中的各项可以交换次序。等价地，我们还可以不使用对数来定义绝对收敛性：称 $\prod_{n=1}^{\infty}(1+z_{n})$ 绝对收敛，如果 $\prod_{n=1}^{\infty}(1+|z_{n}|)$ 收敛。第二种定义更符合级数与乘积之间的类比，我们将这两种定义之间的等价性留给读者进行思考。

**定理 6.5.5**

如果 $\mathrm{Re}\,z_{n}>0$，则 $\prod z_{n}$ 绝对收敛当且仅当 $\sum (z_{n}-1)$ 绝对收敛。

现在我们将这些结果应用到函数的乘积上。

**引理 6.5.6**

设 $f,f_{n}\colon X\to \mathbb{C}$ 满足 $f_{n}\to f$ 在 $X$ 上一致，则如果存在 $a$ 使得对任意 $x \in X$ 有 $\mathrm{Re}\,f(x)\leq a$，则 $\exp f_{n}\to \exp f$ 在 $X$ 上一致。

**证明**

给定 $\varepsilon>0$，取 $\delta>0$ 使得 $\lvert e^{z}-1 \rvert<\varepsilon e^{-a}$ 对 $|z|<\delta$ 成立，再取 $N$ 使得当 $n\geq N$ 时有 $\lvert f_{n}(x)-f(x) \rvert<\delta$ 对 $x \in X$ 成立，从而

$$
\begin{align}
\lvert \exp(f_{n}(x)-f(x))-1 \rvert =\left\lvert  \dfrac{\exp f_{n}(x)}{\exp f(x)}-1  \right\rvert <\varepsilon e^{-a}
\end{align}
$$

即

$$
\begin{align}
\lvert \exp f_{n}(x)-\exp f(x) \rvert <\varepsilon \exp(\mathrm{Re}\,f(x)-a)\leq \varepsilon
\end{align}
$$

这就完成了证明。

**引理 6.5.7**

设 $X$ 是一个紧致度量空间，$(g_{n})\subset C(X,\mathbb{C})$ 满足 $\sum g_{n}$ 在 $X$ 上绝对且一致收敛，则乘积

$$
\begin{gather}
f(x)=\prod_{n=1}^{\infty} (1+g_{n}(x))
\end{gather}
$$

在 $X$ 上绝对且一致收敛。此外，存在 $N$ 使得 $f(x)=0$ 当且仅当存在 $n\leq N$ 使得 $g_{n}(x)=-1$.

**证明**

由于 $\sum g_{n}$ 一致收敛，故存在 $N$ 使得对任意 $n>N$ 和 $x \in X$ 有 $\lvert g_{n}(x) \rvert<1 /2$，这表明 $\mathrm{Re}(1+g_{n}(x))>0$，并且成立

$$
\begin{gather}
\lvert \log(1+g_{n}(x)) \rvert \leq \dfrac{3}{2}\lvert g_{n}(x) \rvert 
\end{gather}
$$

于是级数

$$
\begin{gather}
h(x)=\sum_{n=N+1}^{\infty} \log(1+g_{n}(x))
\end{gather}
$$

一致收敛。由于 $h$ 连续，并且 $X$ 紧致，因此 $h$ 有界，从而存在 $a$ 使得对 $x \in X$ 有 $\mathrm{Re}\,h(x)<a$，于是引理 6.5.6 表明乘积

$$
\begin{gather}
\exp h(x)=\prod_{n=N+1}^{\infty} (1+g_{n}(x))
\end{gather}
$$

一致收敛。最后，我们有

$$
\begin{gather}
f(x)=(1+g_{1}(x))\cdots (1+g_{N}(x)) \exp h(x)
\end{gather}
$$

由于 $\exp h(x)\neq 0$，因此 $f(x)=0$ 当且仅当存在 $n\leq N$ 使得 $g_{n}(x)=-1$.

现在我们转向解析函数的情形。

**定理 6.5.8**

设 $G$ 是一个区域，$(f_{n})\subset H(G)$ 满足没有一个 $f_{n}$ 恒等于零。如果 $\sum(f_{n}(z)-1)$ 在 $G$ 的紧致子集上绝对且一致收敛，则 $\prod_{n=1}^{\infty}f_{n}(z)$ 在 $H(G)$ 中收敛于解析函数 $f(z)$. 如果 $a$ 是 $f$ 的一个零点，那么 $a$ 是有限个 $f_{n}$ 的零点，并且 $f$ 在 $a$ 处的零点重数等于 $f_{n}$ 在 $a$ 处的零点重数之和。

**证明**

由于 $\sum (f_{n}(z)-1)$ 在 $G$ 的紧致子集上绝对且一致收敛，于是由引理 6.5.7 得 $f(z)=\prod_{n=1}^{\infty}f_{n}(z)$ 在 $G$ 的紧致子集上绝对且一致收敛。这就是说，$\prod_{n=1}^{\infty}f_{n}(z)$ 在 $H(G)$ 中收敛于 $f(z)$.

假设 $f(a)=0$，取 $r>0$ 使得 $\overline{B(a,r)}\subset G$，由于 $\sum(f_{n}(z)-1)$ 在 $\overline{B(a,r)}$ 上一致收敛，因此引理 6.5.7 表明存在 $N$ 使得

$$
\begin{gather}
f(z)=f_{1}(z)\cdots f_{N}(z) g(z)
\end{gather}
$$

其中 $g(z)\neq 0$ 在 $\overline{B(a,r)}$ 上成立，这就完成了证明。

下面我们就来回答本节开始时的问题。如果 $(a_{n})$ 是 $G$ 中的序列，在 $G$ 中没有极限点，考虑函数 $z-a_{n}$. 根据定理 6.5.8，如果我们能找到 $G$ 上的解析函数 $g_{n}(z)$，其在 $G$ 上没有零点，并且 $\sum((z-a_{n})g_{n}(z)-1)$ 在 $G$ 的紧致子集上绝对且一致收敛，那么 $f(z)=\prod (z-a_{n})g_{n}(z)$ 解析并且仅在 $a_{n}$ 处有零点。要保证 $g_{n}(z)\neq 0$，一种最简单的方法是令 $g_{n}=\exp h_{n}$，其中 $h_{n}$ 解析。事实上，如果 $G$ 是单连通的，那么 $g_{n}$ 必然具有这样的形式。

**定义 6.5.9** 基本因子（elementary factor）

一个**基本因子** $E_{p}\colon \mathbb{C}\to \mathbb{C}$ 是如下的函数：

$$
\begin{align}
E_{0}(z) &= 1-z \\
E_{p}(z) &= (1-z) \exp\left( z+ \dfrac{z^{2}}{2}+\dots+\dfrac{z^{p}}{p} \right), \quad p\geq 1
\end{align}
$$

显然，$E_{p}(z /a)$ 在 $z=a$ 处有一个单零点，并且没有其他零点。如果 $b \in \mathbb{C}\setminus G$，那么 $E_{p}\left( \dfrac{a-b}{z-b} \right)$ 在 $z=a$ 处有一个单零点，并且在 $G$ 上解析。这些函数将被用于构造具有特定零点的解析函数。

**引理 6.5.10**

如果 $|z|\leq 1$，那么 $\lvert 1-E_{p}(z) \rvert\leq |z|^{p+1}$.

**证明**

$p=0$ 是平凡的。设 $p\geq 1$，令

$$
\begin{gather}
E_{p}(z)=1+\sum_{k=1}^{\infty} a_{k}z^{k}
\end{gather}
$$

为 $E_{p}$ 在 $z=0$ 处的幂级数展开。对幂级数以及 $E_{p}$ 的原始表达式求导即得

$$
\begin{align}
E_{p}'(z) &= \sum_{k=1}^{\infty} ka_{k} z^{k-1} \\
&= -z^{p} \exp\left( z+\dfrac{z^{2}}{2}+\dots+\dfrac{z^{p}}{p} \right)
\end{align}
$$

比较两者的幂级数系数即得 $a_{1}=\dots=a_{p}=0$，此外，由于 $\exp(z+\dots+z^{p} /p)$ 的系数均为正数，故 $a_{k}\leq 0$ 对 $k\geq p+1$ 成立。这给出

$$
\begin{align}
E_{p}(1)=1+\sum_{k=p+1}^{\infty} a_{k}=1-\sum_{k=p+1}^{\infty} |a_{k}|=0
\end{align}
$$

从而对 $|z|\leq 1$ 有

$$
\begin{align}
\lvert 1-E_{p}(z) \rvert &= \left\lvert  \sum_{k=p+1}^{\infty} a_{k}z^{k}  \right\rvert  \\
&\leq |z|^{p+1} \sum_{k=p+1}^{\infty} |a_{k}| \\
&= |z|^{p+1}
\end{align}
$$

这就完成了证明。

**定理 6.5.11**

设 $(a_{n})$ 是一列复数，满足 $a_{n}\neq 0$ 且 $\lim_{ n \to \infty }|a_{n}|=\infty$. 如果 $(p_{n})$ 是整数序列，使得

$$
\begin{gather}
\sum_{n=1}^{\infty} \left( \dfrac{r}{|a_{n}|} \right)^{p_{n}+1}<\infty
\end{gather}
$$

对任意 $r>0$ 成立，那么

$$
\begin{gather}
f(z)=\prod_{n=1}^{\infty} E_{p_{n}}\left( \dfrac{z}{a_{n}} \right)
\end{gather}
$$

在 $H(\mathbb{C})$ 中收敛。函数 $f$ 是一个整函数，仅在 $a_{n}$ 处有零点，并且如果 $z_{0}$ 在序列 $(a_{n})$ 中出现了 $m$ 次，那么 $f$ 在 $z_{0}$ 处有一个重数为 $m$ 的零点。此外，当 $p_{n}=n-1$ 时以上定理成立。

**证明**

设 $(p_{n})$ 为满足条件的整数序列，则由引理 6.5.10 得

$$
\begin{gather}
\left\lvert  1-E_{p_{n}}\left( \dfrac{z}{a_{n}} \right)  \right\rvert \leq \left\lvert  \dfrac{z}{a_{n}}  \right\rvert ^{p_{n}+1}\leq \left( \dfrac{r}{|a_{n}|} \right)^{p_{n}+1}
\end{gather}
$$

对 $|z|\leq r$ 和 $r\leq|a_{n}|$ 成立。固定 $r>0$，存在 $N$ 使得当 $n\geq N$ 时有 $|a_{n}|\geq r$，因此级数 $\sum|1-E_{p_{n}}(z /a_{n})|$ 在 $\overline{B(0,r)}$ 上由一个收敛级数控制，从而 $\sum(E_{p_{n}}(z /a_{n})-1)$ 在 $H(\mathbb{C})$ 上绝对收敛，即证 $\prod E_{p_{n}}(z /a_{n})$ 绝对收敛。

设 $p_{n}=n-1$，对给定的 $r>0$，存在 $N$ 使得当 $n\geq N$ 时有 $|a_{n}|\geq 2r$，即 $\dfrac{r}{|a_{n}|}\leq \dfrac{1}{2}$，这表明级数 $\sum (r /|a_{n}|)^{p_{n}+1}$ 的尾部由 $\sum 2^{-n}$ 控制，因而收敛。这就完成了证明。

容易看出，整数 $p_{n}$ 的选取有很大的自由度。例如，$p_{n}$ 可以选取 $\geq n-1$ 的任意值。不过，我们总是希望 $p_{n}$ 的值越小越好，进而得到更为“初等”的因子 $E_{p_{n}}$. 从定理的条件中我们可以看出，$p_{n}$ 的选取取决于序列 $|a_{n}|$ 趋于 $\infty$ 的速度。我们将在后续的章节中进行深入的研究。

**定理 6.5.12** Weierstrass 分解定理（Weierstrass Factorization Theorem）

设 $f$ 是一个整函数，$(a_{n})$ 是 $f$ 的非零零点组成的序列（根据重数重复），并设 $f$ 在 $z=0$ 处有一个 $m\geq 0$ 阶零点（$m=0$ 表明 $f(0)\neq 0$），则存在整函数 $g$ 以及一列整数 $(p_{n})$ 使得

$$
\begin{gather}
f(z)=z^{m} e^{g(z)} \prod_{n=1}^{\infty} E_{p_{n}}\left( \dfrac{z}{a_{n}} \right)
\end{gather}
$$

**证明**

根据定理 6.5.11，存在序列 $(p_{n})$ 使得

$$
\begin{gather}
h(z)=z^{m} \prod_{n=1}^{\infty} E_{p_{n}}\left( \dfrac{z}{a_{n}} \right)
\end{gather}
$$

与 $f$ 有相同的零点与重数，因此 $f /h$ 在 $z=0,a_{1},a_{2},\dots$ 处有可去奇点。通过补充定义，则 $f /h$ 是一个整函数，从而由 $\mathbb{C}$ 的单连通性知存在整函数 $g$ 使得

$$
\begin{gather}
\dfrac{f(z)}{h(z)}=e^{g(z)}
\end{gather}
$$

这就完成了证明。

现在我们可以来回答本节开始时的问题了。

**定理 6.5.13**

设 $G$ 是一个区域，$(a_{j})\subset G$ 是一列各不相同的数，且在 $G$ 中没有极限点，并设 $(m_{j})$ 是一列整数。则存在 $G$ 上的解析函数 $f$ 使得其仅在 $a_{j}$ 处有零点，并且 $a_{j}$ 的重数为 $m_{j}$.

**证明**

我们首先证明一个特例，其中存在 $R>0$ 满足

$$
\begin{gather}
\{ z \mid |z|>R \}\subset G, \quad |a_{j}|\leq R
\end{gather}
$$

并且此时存在 $f \in H(G)$ 使得 $a_{j}$ 是 $f$ 的仅有零点，其重数为 $m_{j}$，并满足

$$
\begin{gather}
\lim_{ z \to \infty } f(z)=1
\end{gather}
$$

事实上，如果这样的 $f$ 总是存在，令 $G_{1}$ 为任意开集，$(\alpha_{j})$ 是 $G_{1}$ 中的不同点，在 $G_{1}$ 中没有极限点，并令 $(m_{j})$ 是一列整数。如果 $\overline{B(a,r)}\subset G_{1}$ 满足 $\alpha_{j} \not\in B(a,r)$，考虑 Mobius 变换 $T(z)=(z-a)^{-1}$，取 $G=T[G_{1}]$，则 $G$ 满足以上条件，且 $a_{j}=(\alpha_{j}-a)^{-1}$. 取 $f$ 为 $H(G)$ 中的相应函数，则 $g(z)=f(Tz)$ 在 $G_{1}\setminus\{ a \}$ 上解析，并且在 $a$ 处有可去奇点，此外，$g$ 的零点和重数都与 $f$ 相同。

因此我们可以假设 $G$ 满足上述条件，定义序列 $(z_{n})$ 包含所有 $a_{j}$，每个 $a_{j}$ 重复 $m_{j}$ 次。根据 $G$ 的假设，$G\neq \mathbb{C}$，除非 $(a_{j})$ 是有限的。然而，如果 $(a_{j})$ 有限，那么定理是平凡的，因此我们可以假设 $(a_{j})$ 是无限序列，从而 $\mathbb{C}\setminus G$ 非空并且紧致。于是，对任意 $n\geq 1$ 存在 $w_{n}\in \mathbb{C}\setminus G$ 使得

$$
\begin{gather}
|z_{n}-w_{n}|=d(z_{n},\mathbb{C}\setminus G)
\end{gather}
$$

并且

$$
\begin{gather}
\lim_{ n \to \infty } |z_{n}-w_{n}|=0
\end{gather}
$$

考虑函数

$$
\begin{gather}
E_{n}\left( \dfrac{z_{n}-w_{n}}{z-w_{n}} \right)
\end{gather}
$$

其在 $z=z_{n}$ 有一个单零点。我们需要证明这些函数的乘积在 $H(G)$ 中收敛。为此，设 $K\subset G$ 紧致，并且 $d(K,\mathbb{C}\setminus G)>0$，对 $z \in K$ 有

$$
\begin{align}
\left\lvert  \dfrac{z_{n}-w_{n}}{z-w_{n}}  \right\rvert \leq \dfrac{|z_{n}-w_{n}|}{d(w_{n},K)}\leq \dfrac{|z_{n}-w_{n}|}{d(K,\mathbb{C}\setminus G)} \to 0
\end{align}
$$

于是对任意 $0<\delta<1$，存在 $N$ 使得对任意 $n\geq N$ 和 $z \in K$ 有

$$
\begin{gather}
\left\lvert  \dfrac{z_{n}-w_{n}}{z-w_{n}}  \right\rvert <\delta
\end{gather}
$$

于是由引理 6.5.10 得

$$
\begin{gather}
\left\lvert  E_{n}\left( \dfrac{z_{n}-w_{n}}{z-w_{n}} \right)-1  \right\rvert \leq \delta^{n+1}
\end{gather}
$$

因此级数

$$
\begin{gather}
\sum_{n=1}^{\infty} \left( E_{n}\left( \dfrac{z_{n}-w_{n}}{z-w_{n}} \right)-1 \right)
\end{gather}
$$

在 $K$ 上绝对且一致收敛，从而乘积

$$
\begin{gather}
f(z)=\prod_{n=1}^{\infty} E_{n}\left( \dfrac{z_{n}-w_{n}}{z-w_{n}} \right)
\end{gather}
$$

在 $H(G)$ 中收敛。这表明 $f$ 在 $G$ 上解析，并且 $f$ 仅在 $a_{j}$ 处有零点，其重数为 $m_{j}$.

最后我们只需证明 $\lim_{ z \to \infty }f(z)=1$. 令 $\varepsilon>0$，$R_{1}>R$，如果 $|z|\geq R_{1}$，由于 $|z_{n}|\leq R$ 且 $w_{n}\in \mathbb{C}\setminus G$，故

$$
\begin{gather}
\left\lvert  \dfrac{z_{n}-w_{n}}{z-w_{n}}  \right\rvert \leq \dfrac{2R}{R_{1}-R}
\end{gather}
$$

因此，如果我们选取 $R_{1}$ 使得 $\dfrac{2R}{R_{1}-R}<\delta$，其中 $0<\delta<1$，那么对 $|z|\geq R_{1}$ 成立

$$
\begin{gather}
\left\lvert  E_{n}\left( \dfrac{z_{n}-w_{n}}{z-w_{n}} \right)-1  \right\rvert \leq \delta^{n+1}
\end{gather}
$$

特别地，$\mathrm{Re}\,E_{n}\left( \dfrac{z_{n}-w_{n}}{z-w_{n}} \right)>0$，因此

$$
\begin{gather}
|f(z)-1|=\left\lvert  \exp\left( \sum_{n=1}^{\infty} \log E_{n}\left( \dfrac{z_{n}-w_{n}}{z-w_{n}} \right) \right)-1  \right\rvert 
\end{gather}
$$

是一个良定的等式。此外，我们还有

$$
\begin{align}
\left\lvert  \sum_{n=1}^{\infty} \log E_{n}\left( \dfrac{z_{n}-w_{n}}{z-w_{n}} \right)  \right\rvert &\leq \sum_{n=1}^{\infty} \left\lvert  \log E_{n}\left( \dfrac{z_{n}-w_{n}}{z-w_{n}} \right)  \right\rvert  \\
&\leq \dfrac{3}{2} \sum_{n=1}^{\infty} \left\lvert  E_{n}\left( \dfrac{z_{n}-w_{n}}{z-w_{n}} \right)-1  \right\rvert  \\
&\leq \dfrac{3}{2} \dfrac{\delta^{2}}{1-\delta}
\end{align}
$$

如果我们限制 $\delta$ 使得当 $|w|< \dfrac{3}{2} \dfrac{\delta^{2}}{1-\delta}$ 时有 $|e^{w}-1|<\varepsilon$，那么就有 $|f(z)-1|<\varepsilon$ 对 $|z|\geq R_{1}$ 成立，即 $\lim_{ z \to \infty }f(z)=1$. 这就完成了证明。

根据以上定理，我们可以得到以下推论。它表明，每个亚纯函数都是两个全纯函数的商，这在一些教材中也作为亚纯函数的定义。

**定理 6.5.14**

设 $f$ 是开集 $G$ 上的亚纯函数，则有 $G$ 上的解析函数 $g,h$ 使得 $f=g /h$.

**证明**

设 $(a_{j})$ 是 $f$ 的极点组成的序列，其阶数为 $(m_{j})$. 根据定理 6.5.13，存在解析函数 $h$ 使得其仅在 $z=a_{j}$ 处有一个重数为 $m_{j}$ 的零点，从而 $hf$ 在 $a_{j}$ 处有可去奇点，这表明 $g=hf$ 在 $G$ 上解析，这就完成了证明。

最后，我们再给出一个定理，它是乘积的导数法则在无穷乘积下的推广。

**定理 6.5.15**

设 $G$ 是开集，$(f_{n})\subset H(G)$ 满足 $f(z)=\prod f_{n}(z)$ 在 $H(G)$ 中收敛，则：

1. $\displaystyle \sum_{k=1}^{\infty}\left( f_{k}'(z) \prod_{n\neq k} f_{n}(z) \right)$ 在 $H(G)$ 中收敛于 $f'(z)$
2. 设 $f$ 不恒为零，$K\subset G$ 紧致并且 $f$ 在 $K$ 上不消失，则在 $K$ 上一致有 $\displaystyle \dfrac{f'(z)}{f(z)}=\sum_{n=1}^{\infty} \dfrac{f_{n}'(z)}{f_{n}(z)}$

**证明**

(1). 我们将乘积分成 $P_{N}(z)=\prod_{n=1}^{N}f_{n}(z)$ 和尾部 $R_{N}(z)=\prod_{n=N+1}^{\infty}f_{n}(z)$，则 $f(z)=P_{N}(z)R_{N}(z)$，并且在 $H(G)$ 中有 $P_{N}\to f$.

考虑部分和 $S_{N}(z)=\sum_{k=1}^{N}\left( f_{k}'(z)\prod_{n\neq k} f_{n}(z) \right)$，同样将其分成部分积与尾部：

$$
\begin{align}
S_{N}(z) &= \sum_{k=1}^{N} \left( R_{N}(z) f_{k}'(z) \prod_{1\leq n\leq N,n\neq k} f_{n}(z) \right) \\
&= R_{N}(z)P_{N}'(z)
\end{align}
$$

由于 $P_{N}\to f$，故 $P_{N}'\to f'$ 在 $H(G)$ 中成立。此外，如果 $f$ 恒等于零，那么或者存在 $f_{k}$ 恒等于零，或者 $R_{N}\to 0$，无论哪种情况，均有 $P_{N}'R_{N}\to 0=f'$ 在 $H(G)$ 中成立。如果 $f$ 不恒等于零，那么根据定理 6.5.8，$f$ 的零点是孤立的，并且对每个零点，只有有限个 $f_{n}$ 在该处为零。因此，当 $N$ 充分大时，$f /P_{N}$ 只有可去奇点且极限非零，从而在 $H(G)$ 中有 $R_{N}=f /P_{N}\to 1$，即得 $P_{N}'R_{N}\to f'$.

(2). 由于 $f(z)\neq 0$ 对 $z \in K$ 成立，因此每个 $f_{k}$ 在 $K$ 上均不消失，从而

$$
\begin{align}
f'(z)=\sum_{k=1}^{\infty} \left( f_{k}'(z) \prod_{n\neq k} f_{n}(z) \right)=\sum_{k=1}^{\infty} f_{k}'(z) \dfrac{f(z)}{f_{k}(z)}
\end{align}
$$

即

$$
\begin{gather}
\dfrac{f'(z)}{f(z)}=\sum_{k=1}^{\infty} \dfrac{f_{k}'(z)}{f_{k}(z)}
\end{gather}
$$

下面我们要证以上的收敛是一致的。令 $T_{N}$ 为上式右侧的部分和，则有 $S_{N}(z)=f(z)T_{N}(z)$，由于在 $H(G)$ 中 $S_{N}\to f'$，因此在 $K$ 上该收敛是一致的。此外，由于 $K$ 紧致，故 $m=\min_{z \in K} |f(z)|>0$，从而

$$
\begin{gather}
\left\lvert  T_{N}(z)-\dfrac{f'(z)}{f(z)}  \right\rvert \leq \dfrac{1}{m} |S_{N}(z)-f'(z)| \to 0
\end{gather}
$$

对 $z \in K$ 一致，这就完成了证明。

# Section 6: Gamma 函数

利用前几节建立的理论，我们可以来研究数学中的一个经典函数：$\Gamma$ 函数。设 $G$ 是开集，$f_{n}$ 在 $G$ 上解析，并且在 $H(G)$ 中收敛于 $f$，其中 $f$ 不恒等于零。则我们可以证明 $\dfrac{1}{f_{n}}$ 在 $M(G)$ 中收敛于 $\dfrac{1}{f}$，从而 $\dfrac{1}{f_{n}}$ 在 $f_{n}$ 不消失的紧致集 $K$ 上一致收敛于 $\dfrac{1}{f}$. 于是，根据定理 6.5.11，乘积

$$
\begin{gather}
\prod_{n=1}^{\infty} \left( 1+\dfrac{z}{n} \right) e^{-z /n}
\end{gather}
$$

在 $H(\mathbb{C})$ 上收敛于一个整函数，其在 $z=-1,-2,\dots$ 处有单零点，从而上面的讨论表明

$$
\begin{gather}
\prod_{n=1}^{\infty} \left( 1+\dfrac{z}{n} \right)^{-1} e^{z /n}
\end{gather}
$$

在 $\mathbb{C}\setminus\{ -1,-2,\dots \}$ 的紧致子集上一致收敛于一个亚纯函数，其在 $z=-1,-2,\dots$ 处有单极点。

**定义 6.6.1** $\Gamma$ 函数

$\Gamma$ 函数是一个 $\mathbb{C}$ 上的亚纯函数，在 $z=0,-1,-2,\dots$ 处有单极点，定义为

$$
\begin{gather}
\Gamma(z)=\dfrac{e^{-\gamma z}}{z} \prod_{n=1}^{\infty} \left( 1+\dfrac{z}{n} \right)^{-1} e^{z /n}
\end{gather}
$$

其中 $\gamma$ 是一个常数使得 $\Gamma(1)=1$，称为 **Euler–Mascheroni 常数**。

一个首要的问题是确认 $\gamma$ 的存在性。在乘积式中代入 $z=1$ 得到

$$
\begin{gather}
c=\prod_{n=1}^{\infty} \left( 1+\dfrac{1}{n} \right)^{-1} e^{1/n}
\end{gather}
$$

右侧的乘积收敛，并且显然是一个正数。令 $\gamma=\log c$，则我们就有 $\Gamma(1)=1$，并且

$$
\begin{gather}
e^{\gamma}=\prod_{n=1}^{\infty} \left( 1+\dfrac{1}{n} \right)^{-1} e^{1/n}
\end{gather}
$$

两边取对数得到

$$
\begin{align}
\gamma &= \sum_{n=1}^{\infty} \log \left( \left( 1+\dfrac{1}{n} \right)^{-1}e^{1/n} \right) \\
&=\sum_{n=1}^{\infty} \left( \dfrac{1}{n}-\log(n+1)+\log n \right) \\
&= \lim_{ n \to \infty } \sum_{k=1}^{n} \left( \dfrac{1}{k}-\log(k+1)+\log k \right) \\
&= \lim_{ n \to \infty } \left( \sum_{k=1}^{n} \dfrac{1}{k}-\log(n+1) \right)
\end{align}
$$

由于 $\lim_{ n \to \infty } \log\left( \dfrac{n+1}{n} \right)=0$，因此我们有

$$
\begin{gather}
\gamma=\lim_{ n \to \infty } \left( \sum_{k=1}^{n} \dfrac{1}{k}-\log n \right)
\end{gather}
$$

上式可以用来计算 $\gamma$ 的近似值，同时也可以作为它的另一个定义。此外，它还可以给出 $\Gamma$ 函数的另一种乘积表达式。根据定义，我们有

$$
\begin{align}
\Gamma(z) &= \dfrac{e^{-\gamma z}}{z} \lim_{ n \to \infty } \prod_{k=1}^{n} \dfrac{k}{z+k} e^{z /k} \\
&= \lim_{ n \to \infty } \dfrac{e^{-\gamma z} n!}{z(z+1)\cdots (z+n)} \exp\left( z \sum_{k=1}^{n} \dfrac{1}{k} \right)
\end{align}
$$

而

$$
\begin{gather}
e^{-\gamma z} \exp\left( z \sum_{k=1}^{n} \dfrac{1}{k} \right)= n^{z} \exp\left( z\left( -\gamma+\sum_{k=1}^{n} \dfrac{1}{k}-\log n \right) \right)
\end{gather}
$$

这给出：

**定理 6.6.2** Gauss 公式

对 $z\neq 0,-1,-2,\dots$ 有

$$
\begin{gather}
\Gamma(z)=\lim_{ n \to \infty } \dfrac{n! n^{z}}{z(z+1)\cdots (z+n)}
\end{gather}
$$

这一公式允许我们推导 $\Gamma$ 函数的函数方程，也就是作为阶乘的扩展的那个。

**定理 6.6.3**

对 $z\neq 0,-1,-2,\dots$ 有

$$
\begin{gather}
\Gamma(z+1)=z \Gamma(z)
\end{gather}
$$

**证明**

我们有

$$
\begin{align}
\Gamma(z+1) &= \lim_{ n \to \infty } \dfrac{n! n^{z+1}}{(z+1)(z+2)\cdots (z+n+1)} \\
&= z \lim_{ n \to \infty } \dfrac{n!n^{z}}{z(z+1)\cdots (z+n)} \dfrac{n}{z+n+1} \\
&= z \Gamma(z)
\end{align}
$$

最后一步由 $\lim_{ n \to \infty } \dfrac{n}{z+n+1}=1$ 给出。

设 $n$ 是一个非负整数，通过重复应用以上方程，我们得到

$$
\begin{gather}
\Gamma(z+n)=z(z+1)\cdots (z+n-1) \Gamma(z)
\end{gather}
$$

令 $z=1$，我们即得 $\Gamma(n+1)=n!$，因此我们可以将 $\Gamma$ 视为阶乘函数在复数上的推广，并写 $z! =\Gamma(z+1)$.

前面我们指出，$\Gamma(z)$ 在 $z=0,-1,-2,\dots$ 有单极点，于是我们可以在这些点处计算它的留数：

$$
\begin{align}
\mathrm{Res}(\Gamma,-n)=\lim_{ z \to -n } (z+n)\Gamma(z)
\end{align}
$$

然而

$$
\begin{gather}
(z+n)\Gamma(z)=\dfrac{\Gamma(z+n+1)}{z(z+1)\cdots (z+n-1)}
\end{gather}
$$

因此令 $z\to -n$ 即得

$$
\begin{gather}
\mathrm{Res}(\Gamma,-n)=\dfrac{(-1)^{n}}{n!}, \quad n\geq 0
\end{gather}
$$

根据定理 6.5.15，我们有

$$
\begin{gather}
\dfrac{\Gamma'(z)}{\Gamma(z)}=-\gamma-\dfrac{1}{z}+\sum_{n=1}^{\infty} \dfrac{z}{n(n+z)}
\end{gather}
$$

对 $z\neq 0,-1,-2,\dots$ 成立，并且其收敛在 $\mathbb{C}\setminus\{ 0,-1,-2,\dots \}$ 的紧致子集上一致。于是我们可以计算其导数

$$
\begin{gather}
\left( \dfrac{\Gamma'(z)}{\Gamma(z)} \right)'=\dfrac{1}{z^{2}}+\sum_{n=1}^{\infty} \dfrac{1}{(n+z)^{2}}
\end{gather}
$$

上式允许我们以一种公理化的方式刻画 $\Gamma$ 函数。为此，注意到，当 $x>0$ 时，我们有 $\Gamma(x)>0$，并且 $\log \Gamma(x)$ 的二阶导数总是大于零，这表明 $\Gamma(x)$ 在 $(0,\infty)$ 上是对数凸的。事实表明，这一性质，加上阶乘的函数方程，以及 $\Gamma(1)=1$ 完全确定了 $\Gamma$ 函数的行为。

**定理 6.6.4** Bohr-Mollerup 定理

设 $f\colon(0,\infty)\to \mathbb{R}$ 满足 $f(x)>0$，并且有以下性质成立：

1. $\log f(x)$ 是凸函数
2. 对任意 $x>0$ 有 $f(x+1)=xf(x)$
3. $f(1)=1$

那么对 $x>0$ 有 $f(x)=\Gamma(x)$.

**证明**

首先注意到，利用性质 2 和 3，我们有

$$
\begin{gather}
f(x+n)=x(x+1)\cdots (x+n-1)f(x)
\end{gather}
$$

从而只要我们在 $0<x\leq 1$ 上得到 $f(x)=\Gamma(x)$，那么 $f=\Gamma$ 就在 $(0,\infty)$ 上成立。现设 $0<x\leq 1$，$n\geq 2$，则由 $\log f(x)$ 的凸性得

$$
\begin{gather}
\dfrac{\log f(n-1)-\log f(n)}{(n-1)-n}\leq \dfrac{\log f(x+n)-\log f(n)}{(x+n)-n}\leq \dfrac{\log f(n+1)-\log f(n)}{(n+1)-n}
\end{gather}
$$

由于对整数 $m\geq 1$ 有 $f(m)=(m-1)!$，因此我们有

$$
\begin{gather}
x \log(n-1)\leq \log f(x+n)-\log(n-1)!\leq x \log n
\end{gather}
$$

在不等式两边加上 $\log(n-1)!$ 并取指数得到

$$
\begin{gather}
(n-1)^{x} (n-1)!\leq f(x+n)\leq n^{x}(n-1)!
\end{gather}
$$

即

$$
\begin{align}
\dfrac{(n-1)^{x}(n-1)!}{x(x+1)\cdots (x+n-1)}\leq f(x) &\leq \dfrac{n^{x}(n-1)!}{x(x+1)\cdots (x+n-1)} \\
&= \dfrac{n^{x} n!}{x(x+1)\cdots (x+n)} \dfrac{x+n}{n}
\end{align}
$$

由于上式对 $n\geq 2$ 成立，并且 $f(x)$ 与 $n$ 无关，我们可以将左边表达式中的 $n$ 替换为 $n+1$，从而有

$$
\begin{gather}
\dfrac{n^{x}n!}{x(x+1)\cdots (x+n)}\leq f(x)\leq \dfrac{n^{x}n!}{x(x+1)\cdots (x+n)} \dfrac{x+n}{n}
\end{gather}
$$

由于 $\lim_{ n \to \infty } \dfrac{x+n}{n}=1$，根据 Gauss 公式即证 $f(x)=\Gamma(x)$ 对 $0<x\leq 1$ 成立，这就完成了证明。

尽管我们对 $\Gamma$ 函数乘积定义有良好的解析性质，但比起 $\Gamma$ 函数的另一个广为人知的积分定义，它在计算上仍有许多不便。下面，我们就来证明这两个定义是等价的。

**定理 6.6.5**

如果 $\mathrm{Re}\,z>0$，那么

$$
\begin{gather}
\Gamma(z)=\int_{0}^{\infty} t^{z-1} e^{-t} \mathrm{d} t
\end{gather}
$$

我们首先证明，右侧的广义积分是一致收敛的。

**引理 6.6.6**

设 $S=\{ z \mid a\leq \mathrm{Re}\,z\leq A \}$，其中 $0<a<A<\infty$，则：

1. 对任意 $\varepsilon>0$，存在 $\delta>0$ 使得 $$
\left\lvert  \int_{\alpha}^{\beta} t^{z-1}e^{-t} \mathrm{d} t  \right\rvert <\varepsilon
$$对 $0<\alpha<\beta<\delta$ 和 $z \in S$ 成立。
2. 对任意 $\varepsilon>0$，存在 $\kappa>0$ 使得 $$
\left\lvert  \int_{\alpha}^{\beta}t^{z-1}e^{-t}\mathrm{d} t  \right\rvert <\varepsilon
$$对 $\beta>\alpha>\kappa$ 和 $z \in S$ 成立。

**证明**

(1). 当 $0<t\leq 1$ 时，我们有

$$
\begin{gather}
|t^{z-1}e^{-t}|\leq t^{\mathrm{Re}\,z-1}\leq t^{a-1}
\end{gather}
$$

因此如果 $0<\alpha<\beta<1$，则

$$
\begin{align}
\left\lvert  \int_{\alpha}^{\beta} t^{z-1}e^{-t}\mathrm{d} t  \right\rvert \leq \int_{\alpha}^{\beta} t^{a-1}\mathrm{d} t=\dfrac{1}{a}(\beta^{a}-\alpha^{a})
\end{align}
$$

对于给定的 $\varepsilon>0$，取 $\delta<1$ 使得当 $\beta-\alpha<\delta$ 时有 $\dfrac{\beta^{a}-\alpha^{a}}{a}<\varepsilon$ 即证。

(2). 当 $t\geq 1$ 时，我们有 $|t^{z-1}|\leq t^{A-1}$. 由于 $t^{A-1}e^{-t/2}$ 在 $[1,\infty)$ 上连续，并且其在 $t\to \infty$ 的极限为零，因此存在 $c$ 使得 $t^{A-1}e^{-t/2}\leq c$ 对 $t\geq 1$ 成立，从而

$$
\begin{gather}
|t^{z-1}e^{-t}|\leq c e^{-t/2}
\end{gather}
$$

如果 $\beta>\alpha>1$，那么

$$
\begin{align}
\left\lvert  \int_{\alpha}^{\beta} t^{z-1}e^{-t} \mathrm{d} t  \right\rvert \leq c \int_{\alpha}^{\beta} e^{-t/2}\mathrm{d} t=2c(e^{-\alpha/2}-e^{-\beta/2})
\end{align}
$$

同样，对给定的 $\varepsilon>0$，取 $\kappa>1$ 使得当 $\beta>\alpha>\kappa$ 时有 $2c(e^{-\alpha/2}-e^{-\beta/2})<\varepsilon$ 即证。

**引理 6.6.7**

设 $G=\{ z \mid \mathrm{Re}\,z>0 \}$，并令

$$
\begin{gather}
f_{n}(z)=\int_{1 /n}^{n} t^{z-1}e^{-t} \mathrm{d} t
\end{gather}
$$

则 $f_{n}$ 在 $G$ 上解析，并且序列 $(f_{n})$ 在 $H(G)$ 中收敛。

**证明**

定义 $\varphi(t,z)=t^{z-1}e^{-t}$，设 $K\subset G$ 为闭圆盘，则 $\varphi$ 在 $[1 /n,n]\times K$ 上关于 $t$ 一致连续，并且关于 $z$ 解析。则 $\dfrac{ \partial \varphi }{ \partial z }$ 在 $[1 /n,n]\times K$ 上一致连续，于是存在 $\delta$ 使得

$$
\begin{gather}
\lvert (t,z)-(t',z') \rvert <\delta \implies \left\lvert  \dfrac{ \partial \varphi }{ \partial z } (t,z)- \dfrac{ \partial \varphi }{ \partial z }  (t',z')  \right\rvert <\varepsilon
\end{gather}
$$

取 $|h|<\delta$，则我们有

$$
\begin{align}
&\left\lvert \dfrac{\varphi(t,z+h)-\varphi(t,z)}{h} -\dfrac{ \partial \varphi }{ \partial z } (t,z) \right\rvert  \\
&= \left\lvert \dfrac{1}{h} \int_{[z,z+h]} \dfrac{ \partial \varphi }{ \partial z } (t,\zeta) \mathrm{d} \zeta-\dfrac{ \partial \varphi }{ \partial z } (t,z) \right\rvert  \\
&= \left\lvert  \int_{0}^{1} \left( \dfrac{ \partial \varphi }{ \partial z } (t,z+sh) -\dfrac{ \partial \varphi }{ \partial z } (t,z) \right)  \mathrm{d} s  \right\rvert  \\
&\leq \varepsilon
\end{align}
$$

对 $1 /n\leq t\leq n$ 一致。从而

$$
\begin{align}
f_{n}'(z) &=\lim_{ h \to 0 } \dfrac{1}{h} \int_{1 /n}^{n} (\varphi(t,z+h)-\varphi(t,z)) \mathrm{d} t \\
&=\int_{1 /n}^{n} \lim_{ h \to 0 } \dfrac{\varphi(t,z+h)-\varphi(t,z)}{h} \mathrm{d} t \\
&=\int_{1 /n}^{n} \dfrac{ \partial \varphi }{ \partial z }(t,z) \mathrm{d} t
\end{align}
$$

即证 $f_{n}$ 在 $K$ 上全纯，从而在 $G$ 上解析。最后，取 $m>n$，则在紧致集 $K$ 上有

$$
\begin{gather}
f_{m}(z)-f_{n}(z)=\int_{1 /m}^{1 /n} t^{z-1}e^{-t}\mathrm{d} t+\int_{n}^{m} t^{z-1}e^{-t}\mathrm{d} t
\end{gather}
$$

由于 $K\subset \{ z \mid a\leq \mathrm{Re}\,z\leq A \}$，根据引理 6.6.6 知 $(f_{n})$ 是 $H(G)$ 中的 Cauchy 序列，从而收敛，这就完成了证明。

注意，以上定理的第一部分（$f_{n}$ 的解析性）可以被推广至 $\{ \gamma \}\times G$ 上关于 $z$ 解析的连续函数 $\varphi(w,z)$，其中 $\gamma$ 是一条可求长曲线，结论是函数

$$
\begin{gather}
g(z)=\int_{\gamma} \varphi(w,z)\mathrm{d} w
\end{gather}
$$

解析，并且

$$
\begin{gather}
g'(z)=\int_{\gamma} \dfrac{ \partial \varphi }{ \partial z }(w,z) \mathrm{d} w
\end{gather}
$$

这实际上就是 Leibniz 法则在解析函数上的推广。

由于 $f_{n}$ 在 $H(G)$ 中收敛，我们将极限记作

$$
\begin{gather}
f(z)=\int_{0}^{\infty} t^{z-1} e^{-t} \mathrm{d} t
\end{gather}
$$

现在我们只需证明 $f(x)=\Gamma(x)$ 对 $x\geq 1$ 成立，因为 $[1,\infty)$ 在右半平面内部有极限点。根据分部积分法，我们可得

$$
\begin{gather}
\int_{0}^{n} \left( 1-\dfrac{t}{n} \right)^{n} t^{x-1} \mathrm{d} t = \dfrac{n! n^{x}}{x(x+1)\cdots (x+n)}
\end{gather}
$$

当 $n\to \infty$ 时，右边趋于 $\Gamma(x)$，于是我们只需证明左边的积分收敛于 $f(x)$.

**引理 6.6.8**

1. $\left( 1+\dfrac{z}{n} \right)^{n}$ 在 $H(\mathbb{C})$ 中收敛于 $e^{z}$
2. 如果 $t\geq 0$，那么 $\left( 1-\dfrac{t}{n} \right)^{n}\leq e^{-t}$ 对 $n\geq t$ 成立

**证明**

设 $K$ 紧致，则对充分大的 $n$ 有 $|z|<n$，从而

$$
\begin{align}
\left\lvert  n \log\left( 1+\dfrac{z}{n} \right)-z  \right\rvert &\leq |z| \sum_{k=2}^{\infty} \dfrac{1}{k} \left\lvert  \dfrac{z}{n}  \right\rvert ^{k-1} \\
&\leq |z| \sum_{k=1}^{\infty} \left\lvert  \dfrac{z}{n}  \right\rvert ^{k} \\
&= \dfrac{|z|^{2}}{n-|z|} \\
&\leq \dfrac{R^{2}}{n-R}
\end{align}
$$

其中 $|z|\leq R$ 对 $z \in K$ 成立，于是 $n \log\left( 1+\dfrac{z}{n} \right)$ 在 $K$ 上一致收敛于 $z$，从而由引理 6.5.6 得 $\left( 1+\dfrac{z}{n} \right)^{n}$ 在 $H(\mathbb{C})$ 上收敛于 $e^{z}$.

任取 $t\geq 0$，当 $n\geq t$ 时，我们有

$$
\begin{gather}
n \log\left( 1-\dfrac{t}{n} \right)+t=-t \sum_{k=1}^{\infty} \dfrac{1}{k} \left( \dfrac{t}{n} \right)^{k-1}\leq 0
\end{gather}
$$

即 $n\log\left( 1-\dfrac{t}{n} \right)\leq -t$，两边取指数即证。

**证明**（6.6.5）

取 $x>1$，$\varepsilon>0$，则存在 $\kappa>0$ 使得当 $r>\kappa$ 时有

$$
\begin{gather}
\int_{\kappa}^{r} t^{x-1}e^{-t} \mathrm{d} t< \dfrac{\varepsilon}{4}
\end{gather}
$$

令 $n>\kappa$ 为整数，则

$$
\begin{align}
f_{n}(x)-\int_{0}^{n} \left( 1-\dfrac{t}{n} \right)^{n} t^{x-1} \mathrm{d} t &= - \int_{0}^{1 /n} \left( 1-\dfrac{t}{n} \right)^{n} t^{x-1}\mathrm{d} t \\
&+\int_{1 /n}^{n} \left( e^{-t}-\left( 1-\dfrac{t}{n} \right)^{n} \right) t^{x-1} \mathrm{d} t
\end{align}
$$

根据引理 6.6.6 和 6.6.8，我们有

$$
\begin{align}
\int_{0}^{1 /n} \left( 1-\dfrac{t}{n} \right)^{n}t^{x-1}\mathrm{d} t\leq \int_{0}^{1 /n} e^{-t} t^{x-1}\mathrm{d} t< \dfrac{\varepsilon}{4}
\end{align}
$$

对充分大的 $n$ 成立。并且，对充分大的 $n$，有

$$
\begin{gather}
\left\lvert  e^{-t}-\left( 1-\dfrac{t}{n} \right)^{n}  \right\rvert < \dfrac{\varepsilon}{4M}
\end{gather}
$$

对 $0\leq t\leq \kappa$ 成立，其中 $M=\int_{0}^{\kappa}t^{x-1}\mathrm{d}t$，则

$$
\begin{gather}
\left\lvert  \int_{1 /n}^{\kappa} \left( e^{-t}-\left( 1-\dfrac{t}{n} \right)^{n} \right) t^{x-1} \mathrm{d} t  \right\rvert \leq \dfrac{\varepsilon}{4}
\end{gather}
$$

最后，我们有

$$
\begin{align}
\left\lvert  \int_{\kappa}^{n} \left( e^{-t}-\left( 1-\dfrac{t}{n} \right)^{n} \right) t^{x-1} \mathrm{d} t  \right\rvert \leq 2 \int_{\kappa}^{n} e^{-t}t^{x-1}\mathrm{d} t\leq \dfrac{\varepsilon}{2}
\end{align}
$$

从而对充分大的 $n$ 有

$$
\begin{align}
\left\lvert  f_{n}(x)-\int_{0}^{n} \left( 1-\dfrac{t}{n} \right)^{n} t^{x-1}\mathrm{d} t  \right\rvert <\varepsilon
\end{align}
$$

关于 $x$ 一致，这就完成了证明。