实分析主要由两个主题构成：拓扑（收敛性、连续性等）与测度（积分学）。我们在研究 $\mathbb{R}^{n}$ 上的 Lebesgue 测度时曾经见过这两者之间的相互作用：可测集可以通过开集或紧致集逼近，可积函数可以由连续函数逼近。具有这样性质的测度可以推广到更一般的局部紧致 Hausdorff 空间（LCH 空间）上。此外，我们之后将看到，特定连续函数空间上的线性泛函可以由关于这些测度的积分来表示，这一事实构成了泛函分析与测度论之间的一个重要联系。

# Section 1: $C_{c}(X)$ 上的正线性泛函

设 $X$ 是一个 LCH 空间，回顾一下，$C_{c}(X)$ 是 $X$ 上具有紧支撑的连续函数构成的空间，具有一致范数 $\lVert \cdot \rVert_{\infty}$，有时为了与 $L^{\infty}$ 上的范数区分，通常记作 $\lVert \cdot \rVert_{u}$.

**定义 29.1.1** 正线性泛函（positive linear functional）

设 $X$ 是 LCH 空间，称 $C_{c}(X)$ 上的线性泛函 $I$ 是**正的**，如果对任意满足 $f\geq 0$ 的函数 $f \in C_{c}(X)$ 有 $I(f)\geq 0$.

值得注意的是，正性本身蕴含了一个相当强的连续性条件。

**定理 29.1.2**

设 $X$ 是 LCH 空间，如果 $I$ 是 $C_{c}(X)$ 上的正线性泛函，那么对任意紧致集 $K\subset X$，存在 $C_{K}>0$ 使得 $|I(f)|\leq C_{K}\lVert f \rVert_{u}$ 对任意满足 $\mathrm{supp}(f)\subset K$ 的 $f \in C_{c}(X)$ 成立。

**证明**

通过将 $f$ 分成实部和虚部，我们只需考虑 $f$ 是实值函数的情况。给定紧致集 $K$，根据 Urysohn 引理，存在 $\phi \in C_{c}(X,[0,1])$ 使得 $\phi|_{K}=1$，则当 $\mathrm{supp}(f)\subset K$ 时，有 $|f|\leq \lVert f \rVert_{u} \phi$，即 $\lVert f \rVert_{u}\phi-f\geq 0$ 且 $\lVert f \rVert_{u}\phi+f\geq 0$，根据 $I$ 的正性得 $\lVert f \rVert_{u}I(\phi)-I(f)\geq 0$ 且 $\lVert f \rVert_{u}I(\phi)+I(f)\geq 0$，即得 $|I(f)|\leq I(\phi) \lVert f \rVert_{u}$.

如果 $\mu$ 是 $X$ 上的 Borel 测度，满足 $\mu(K)<\infty$ 对任意紧致集 $K\subset X$ 成立，那么显然有 $C_{c}(X)\subset L^{1}(\mu)$，从而函数 $f\mapsto \int f\mathrm{d}\mu$ 就是 $C_{c}(X)$ 上的正线性泛函。本节的主定理表明，每个正线性泛函都对应了这样的一个测度，并且我们还可以添加一些**正则性条件**，使得 $\mu$ 是唯一的，如下所示：

**定义 29.1.3** 正则的（regular）

设 $X$ 是 LCH 空间，$\mu$ 是 $X$ 上的 Borel 测度，$E\subset X$ 是 Borel 集，称 $\mu$ 在 $E$ 上是**外正则的**，如果

$$
\begin{gather}
\mu(E)=\inf \{ \mu(U) \mid U\supset E, U\text{是开集} \}
\end{gather}
$$

称 $\mu$ 在 $E$ 上是**内正则的**，如果

$$
\begin{gather}
\mu(E)=\sup \{ \mu(K) \mid K\subset E, K\text{是紧致集} \}
\end{gather}
$$

如果 $\mu$ 在所有 Borel 集上是外正则且内正则的，则称 $\mu$ 是**正则的**。

事实上，对于非 $\sigma$-紧致的空间来说，正则的条件过强了，因此我们给出以下定义：

**定义 29.1.4** Radon 测度

设 $X$ 是 LCH 空间，称 $X$ 上的 Borel 测度 $\mu$ 是一个 **Radon 测度**，如果 $\mu$ 在紧致集上有限，在 Borel 集上外正则，在开集上内正则。

Radon 测度是最常见，也是最通用的一种测度，Lebesgue 测度就是其中之一。此外，Radon 测度具有许多良好的性质，我们将在下一节进行深入的研究。

在证明本节的主定理之前，我们再给出一个记号：如果 $U\subset X$ 是开集且 $f \in C_{c}(X)$，我们用 $f\prec U$ 表示 $0\leq f\leq 1$ 且 $\mathrm{supp}(f)\subset U$.

**定理 29.1.5** Riesz 表示定理（Riesz representation theorem）

设 $X$ 是 LCH 空间，$I$ 是 $C_{c}(X)$ 上的正线性泛函，则存在唯一的 Radon 测度 $\mu$ 使得 $I(f)=\int f\mathrm{d}\mu$ 对任意 $f \in C_{c}(X)$ 成立。此外，$\mu$ 满足对任意开集 $U\subset X$ 有

$$
\begin{gather}
\mu(U)=\sup \{ I(f) \mid f \in C_{c}(X), f\prec U \}
\end{gather}
$$

并且对任意紧致集 $K\subset X$ 有

$$
\begin{gather}
\mu(K)=\inf \{ I(f) \mid f \in C_{c}(X), f\geq \chi_{K} \}
\end{gather}
$$

**证明**

首先证明唯一性。设 $\mu$ 是一个 Radon 测度使得 $I(f)=\int f\mathrm{d}\mu$ 对任意 $f \in C_{c}(X)$ 成立，$U\subset X$ 是开集，那么当 $f\prec U$ 时，显然有 $I(f)\leq \mu(U)$. 再设 $K\subset U$ 是紧致集，根据 Urysohn 引理，存在 $f \in C_{c}(X)$ 使得 $f\prec U$ 且 $f|_{K}=1$，于是 $\mu(K)\leq \int f\mathrm{d}\mu=I(f)$，由于 $\mu$ 在 $U$ 上是内正则的，这表明 $\mu(U)=\sup \{ I(f) \mid f \in C_{c}(X), f\prec U \}$，因此 $\mu$ 完全由 $I$ 在开集上的作用决定，于是根据外正则性知 $\mu$ 在 Borel 集上完全由 $I$ 确定。

唯一性的证明过程暗示了我们构造 $\mu$ 的方法，即，我们首先对开集 $U$ 定义

$$
\begin{gather}
\mu(U)=\sup \{ I(f) \mid f \in C_{c}(X), f\prec U \}
\end{gather}
$$

并且对任意 $E\subset X$ 定义

$$
\begin{gather}
\mu^{*}(E)=\inf \{ \mu(U) \mid U\supset E, U\text{是开集} \}
\end{gather}
$$

显然如果 $U\subset V$，那么 $\mu(U)\leq \mu(V)$，从而 $\mu^{*}(U)=\mu(U)$ 如果 $U$ 是开集。下面的证明我们分成四步来进行：

(i). $\mu^{*}$ 是一个外测度。

(ii). 每个开集都是 $\mu^{*}$-可测的。

此时根据 Caratheodory 定理可知所有 Borel 集都是 $\mu^{*}$-可测的，并且 $\mu=\mu^{*}|_{\mathcal{B}_{X}}$ 是一个 Borel 测度。此外，根据定义可知 $\mu$ 是外正则的，并且满足 $\mu(U)=\sup \{ I(f) \mid f \in C_{c}(X), f\prec U \}$. 接下来我们要证

(iii). $\mu(K)=\inf \{ I(f) \mid f \in C_{c}(X), f\geq \chi_{K} \}$

这显然表明 $\mu$ 在紧致集上是有限的，同样我们也可以证明 $\mu$ 在开集上内正则：如果 $U$ 是开集且 $\alpha<\mu(U)$，取 $f \in C_{c}(X)$ 使得 $f\prec U$ 且 $I(f)>\alpha$，令 $K=\mathrm{supp}(f)$. 如果 $g \in C_{c}(X)$ 且 $g\geq \chi_{K}$，则 $g-f\geq 0$，从而 $I(g)\geq I(f)>\alpha$，于是 $\mu(K)>\alpha$，因此 $\mu$ 在 $U$ 上是内正则的。最后，我们证明

(iv). $I(f)=\int f\mathrm{d}\mu$ 对任意 $f \in C_{c}(X)$ 成立。

这样就完成了证明。

(i) 的证明：我们需要证明如果 $(U_{j})$ 是一列开集并且 $U=\bigcup_{j=1}^{\infty}U_{j}$，那么 $\mu(U)\leq \sum_{j=1}^{\infty}\mu(U_{j})$，由此可得对任意 $E\subset X$ 有

$$
\begin{gather}
\mu^{*}(E)=\inf \left\{  \sum_{j=1}^{\infty} \mu(U_{j}) \mid U_{j}\text{是开集}, E\subset \bigcup_{j=1}^{\infty} U_{j}  \right\}
\end{gather}
$$

从而根据定理 20.3.2，右边的表达式定义了一个外测度。设 $U=\bigcup_{j=1}^{\infty}U_{j}$，$f \in C_{c}(X)$，$f\prec U$，令 $K=\mathrm{supp}(f)$. 由于 $K$ 是紧致的，故存在开集 $U_{1},\dots,U_{n}$ 覆盖 $K$，于是根据定理 25.5.16，存在 $g_{1},\dots,g_{n}\in C_{c}(X)$ 满足 $g_{j}\prec U_{j}$ 且在 $K$ 上有 $\sum_{j=1}^{n}g_{j}=1$，从而 $f=\sum_{j=1}^{n}fg_{j}$，且 $fg_{j}\prec U_{j}$，因此

$$
\begin{gather}
I(f)=\sum_{j=1}^{n} I(fg_{j})\leq \sum_{j=1}^{n} \mu(U_{j})\leq \sum_{j=1}^{\infty} \mu(U_{j})
\end{gather}
$$

上述不等式对任意 $f\prec U$ 成立，故 $\mu(U)\leq \sum_{j=1}^{\infty}\mu(U_{j})$.

(ii) 的证明：我们要证如果 $U$ 是开集而 $E\subset X$ 满足 $\mu^{*}(E)<\infty$，那么 $\mu^{*}(E)\geq \mu^{*}(E\cap U)+\mu^{*}(E\setminus U)$. 首先设 $E$ 是开集，则 $E\cap U$ 是开集，从而存在 $f \in C_{c}(X)$ 使得 $f\prec E\cap U$ 且 $I(f)>\mu(E\cap U)-\varepsilon$. 此外，$E\setminus \mathrm{supp}(f)$ 也是开集，于是存在 $g \in C_{c}(X)$ 使得 $g\prec E\setminus\mathrm{supp}(f)$ 且 $I(g)>\mu(E\setminus \mathrm{supp}(f))-\varepsilon$，此时 $f+g\prec E$，从而有

$$
\begin{align}
\mu(E)\geq I(f)+I(g) &> \mu(E\cap U)+\mu(E\setminus \mathrm{supp}(f))-2\varepsilon \\
&\geq \mu(E\cap U)+ \mu(E\setminus U)-2\varepsilon
\end{align}
$$

令 $\varepsilon\to 0$ 即证。对于一般的 $E\subset X$，如果 $\mu^{*}(E)<\infty$，那么根据定义，存在开集 $V\supset E$ 使得 $\mu(V)<\mu^{*}(E)+\varepsilon$，于是

$$
\begin{align}
\mu^{*}(E)+\varepsilon >\mu(V) &\geq \mu(V\cap U)+\mu(V\setminus U) \\
&\geq \mu^{*}(E\cap U)+\mu^{*}(E\setminus U)
\end{align}
$$

令 $\varepsilon\to 0$ 即证。

(iii) 的证明：设 $K$ 是紧致集，$f \in C_{c}(X)$，$f\geq \chi_{K}$，任取 $0<\varepsilon<1$，令 $U_{\varepsilon}=\{ x \mid f(x)>1-\varepsilon \}$，则 $U_{\varepsilon}$ 是开集，并且如果 $g\prec U_{\varepsilon}$，则有 $\dfrac{1}{1-\varepsilon}f-g\geq 0$，从而 $I(g)\leq \dfrac{1}{1-\varepsilon}I(f)$，则 $\mu(K)\leq \mu(U_{\varepsilon})\leq \dfrac{1}{1-\varepsilon}I(f)$，令 $\varepsilon\to 0$ 即得 $\mu(K)\leq I(f)$. 另一方面，对任意开集 $U\supset K$，根据 Urysohn 引理，存在 $f \in C_{c}(X)$ 使得 $f\geq \chi_{K}$ 且 $f\prec U$，于是 $I(f)\leq \mu(U)$，由于 $\mu$ 在 $K$ 上是外正则的，这就证明了 (iii).

(iv) 的证明：我们只需证明 $I(f)=\int f\mathrm{d}\mu$ 对 $f \in C_{c}(X,[0,1])$ 成立即可，因为 $C_{c}(X)$ 可以由 $C_{c}(X,[0,1])$ 线性张成。给定 $N\geq 1$，对于 $1\leq j\leq N$ 定义 $K_{j}=\{ x \mid f(x)\geq j / N \}$，并且令 $K_{0}=\mathrm{supp}(f)$. 此外，定义 $f_{1},\dots,f_{N}\in C_{c}(X)$ 如下：

$$
\begin{gather}
f_{j}(x)=\begin{cases}
0 &, x \not\in K_{j-1} \\
f(x)- \dfrac{j-1}{N} &, x \in K_{j-1}\setminus K_{j} \\
\dfrac{1}{N} &, x \in K_{j}
\end{cases}
\end{gather}
$$

于是 $\dfrac{1}{N}\chi_{K_{j}}\leq f_{j}\leq \dfrac{1}{N}\chi_{K_{j-1}}$，因此

$$
\begin{gather}
\dfrac{1}{N} \mu(K_{j})\leq \int f_{j}\mathrm{d} \mu\leq \dfrac{1}{N} \mu(K_{j-1})
\end{gather}
$$

另一边，如果开集 $U\supset K_{j-1}$，我们有 $Nf_{j}\prec U$，因此 $I(f_{j})\leq \dfrac{1}{N}\mu(U)$，从而根据 (iii) 和外正则性得

$$
\begin{gather}
\dfrac{1}{N}\mu(K_{j})\leq I(f_{j})\leq \dfrac{1}{N} \mu(K_{j-1})
\end{gather}
$$

再根据 $f=\sum_{j=1}^{N}f_{j}$，我们就有

$$
\begin{gather}
\dfrac{1}{N} \sum_{j=1}^{N} \mu(K_{j}) \leq \int f\mathrm{d} \mu\leq \dfrac{1}{N} \sum_{j=0}^{N-1} \mu(K_{j}) \\
\dfrac{1}{N} \sum_{j=1}^{N} \mu(K_{j}) \leq I(f)\leq \dfrac{1}{N} \sum_{j=0}^{N-1} \mu(K_{j})
\end{gather}
$$

从而

$$
\begin{gather}
\left\lvert  I(f)- \int f\mathrm{d} \mu  \right\rvert \leq \dfrac{\mu(K_{0})-\mu(K_{N})}{N}\leq \dfrac{\mu(\mathrm{supp}(f))}{N}
\end{gather}
$$

由于 $\mu(\mathrm{supp}(f))<\infty$ 而 $N$ 是任意的，即证 $I(f)=\int f\mathrm{d}\mu$.

就像 $\mathbb{R}$ 上的 Borel 测度与 Lebesgue-Stieltjes 测度一样，通过上述定理的证明，我们不仅得到了 Borel 测度 $\mu$，还有其在 $\mu^{*}$-可测集构成的 $\sigma$-代数 $\mathcal{M}^{*}$ 上的扩张 $\overline{\mu}$. 根据定理 20.4.3，如果 $\mu$ 是 $\sigma$-有限的，那么 $\overline{\mu}$ 就是 $\mu$ 的完备化。

# Section 2: 正则性与逼近定理

在本节中，我们来深入地了解 Radon 测度的性质。

**定理 29.2.1**

Radon 测度在 $\sigma$-有限集上是内正则的。

**证明**

设 $\mu$ 是 Radon 测度，$E$ 是 $\sigma$-有限的。如果 $\mu(E)<\infty$，那么对任意 $\varepsilon>0$ 存在开集 $U\supset E$ 使得 $\mu(U)<\mu(E)+\varepsilon$ 以及紧致集 $F\subset U$ 使得 $\mu(F)>\mu(U)-\varepsilon$. 由于 $\mu(U\setminus E)<\varepsilon$，根据外正则性我们可以选取开集 $V\supset U\setminus E$ 使得 $\mu(V)<\varepsilon$，令 $K=F\setminus V$，则 $K\subset E$ 是紧致的，并且

$$
\begin{gather}
\mu(K)=\mu(F)-\mu(F\cap V)>\mu(U)-\varepsilon-\mu(V)>\mu(E)-2\varepsilon
\end{gather}
$$

因此 $\mu$ 在 $E$ 上是内正则的。如果 $\mu(E)=\infty$，取一列递增的子集 $(E_{j})$ 使得 $E=\bigcup_{j=1}^{\infty}E_{j}$，$\mu(E_{j})<\infty$，且 $\mu(E_{j})\to \infty$，则对任意 $M>0$，存在 $j$ 使得 $\mu(E_{j})>M$，于是根据上述论证，存在紧致集 $K\subset E_{j}$ 使得 $\mu(K)>M$，从而 $\mu$ 在 $E$ 上内正则，这就完成了证明。

由此我们得到推论：

**定理 29.2.2**

任意 $\sigma$-有限的 Radon 测度都是正则的。如果 LCH 空间 $X$ 是 $\sigma$-紧致的，那么 $X$ 上的任意 Radon 测度都是正则的。

**定理 29.2.3**

设 $\mu$ 是 LCH 空间 $X$ 上 $\sigma$-有限的 Radon 测度，$E\subset X$ 是 Borel 集，则：

1. 对任意 $\varepsilon>0$，存在开集 $U$ 和闭集 $F$ 使得 $F\subset E\subset U$ 且 $\mu(U\setminus F)<\varepsilon$.
2. 存在 $F_{\sigma}$ 集 $A$ 和 $G_{\delta}$ 集 $B$ 使得 $A\subset E\subset B$ 且 $\mu(B\setminus A)=0$.

**证明**

设 $E=\bigcup_{j=1}^{\infty}E_{j}$，其中各 $E_{j}$ 不相交且 $\mu(E_{j})<\infty$. 对每个 $j$，取开集 $U_{j}\supset E_{j}$ 使得 $\mu(U_{j})<\mu(E_{j})+\varepsilon 2^{-j-1}$ 并令 $U=\bigcup_{j=1}^{\infty}U_{j}$，则 $U$ 是开集，$U\supset E$，且 $\mu(U\setminus E)\leq \sum_{j=1}^{\infty}\mu(U_{j}\setminus E_{j})<\varepsilon / 2$. 对 $E^{c}$ 进行同样的操作，可以得到开集 $V\supset E^{c}$ 使得 $\mu(V\setminus E^{c})<\varepsilon / 2$，取 $F=V^{c}$ 为闭集，则有 $F\subset E$，且

$$
\begin{gather}
\mu(U\setminus F)=\mu(U\setminus E)+\mu(E\setminus F)=\mu(U\setminus E)+\mu(V\setminus E^{c})<\varepsilon
\end{gather}
$$

这就证明了 1. 对于 2，给定 $j\geq 1$，取开集 $U_{j}$ 和闭集 $F_{j}$ 使得 $F_{j}\subset E\subset U_{j}$，且 $\mu(U_{j}\setminus F_{j})<1 / j$，令 $B=\bigcap_{j=1}^{\infty}U_{j}$，$A=\bigcup_{j=1}^{\infty}F_{j}$，则 $B\setminus A\subset U_{j}\setminus F_{j}$，因此 $\mu(B\setminus A)<1 / j$ 对任意 $j$ 成立，这就完成了证明。

**定理 29.2.4**

设 $X$ 是一个 LCH 空间，满足其中的每个开集都是 $\sigma$-紧致的（特别地，当 $X$ 第二可数时），则 $X$ 上的每个在紧致集上有限的 Borel 测度都是正则的，从而是 Radon 测度。

**证明**

如果 $\mu$ 是一个在紧致集上有限的 Borel 测度，那么 $C_{c}(X)\subset L^{1}(\mu)$，因此 $I(f)=\int f\mathrm{d}\mu$ 是 $C_{c}(X)$ 上的一个正线性泛函，根据 Riesz 表示定理，存在唯一的 Radon 测度 $\nu$ 与之关联。如果 $U\subset X$ 是开集，设 $U=\bigcup_{j=1}^{\infty}K_{j}$，其中 $K_{j}$ 是紧致集，取 $f_{1}\in C_{c}(X)$ 使得 $f_{1}\prec U$ 且 $f_{1}|_{K_{1}}=1$. 下面递归地取 $f_{n}\in C_{c}(X)$ 使得 $f_{n}\prec U$ 且在 $\bigcup_{j=1}^{n}K_{j}$ 和 $\bigcup_{j=1}^{n-1}\mathrm{supp}(f_{j})$ 上 $f_{n}=1$，于是 $f_{n}$ 递增并收敛于 $\chi_{U}$，从而

$$
\begin{gather}
\mu(U)=\lim_{ n \to \infty } \int f_{n}\mathrm{d} \mu=\lim_{ n \to \infty } \int f_{n}\mathrm{d} \nu=\nu(U)
\end{gather}
$$

接下来，如果 $E\subset X$ 是 Borel 集，根据定理 29.2.3，存在开集 $V$ 和闭集 $F$ 满足 $F\subset E\subset V$ 且 $\nu(V\setminus F)<\varepsilon$，但 $V\setminus F$ 是开集，故 $\mu(V\setminus F)<\varepsilon$，从而 $\mu(V)<\mu(E)+\varepsilon$，即 $\mu$ 是外正则的。此外，有 $\mu(F)>\mu(E)-\varepsilon$，而 $F$ 是 $\sigma$-紧致的（因为 $X$ 是 $\sigma$-紧致的且 $F$ 是闭集），故存在紧致集 $K_{j}\subset F$ 且 $\mu(K_{j})\to \mu(F)$，从而 $\mu$ 是内正则的。因此 $\mu$ 是正则的（并且等于 $\nu$）。

根据该定理，我们可知 $\mathbb{R}^{n}$ 上的在紧致集上有限的 Borel 测度都是正则的，因为其上的开集是立方体的可数并，而每个立方体都是闭且有界的，因而是紧致的。

接下来我们转到连续函数逼近的主题上来。

**定理 29.2.5**

设 $\mu$ 是 LCH 空间 $X$ 上的 Radon 测度，$1\leq p<\infty$，则 $C_{c}(X)$ 在 $L^{p}(\mu)$ 中稠密。

**证明**

由于简单函数在 $L^{p}$ 中稠密，我们只需证明对任意具有有限测度的 Borel 集 $E$，$\chi_{E}$ 可以被 $C_{c}(X)$ 中的元素近似。给定 $\varepsilon>0$，根据定理 29.2.1，存在开集 $U\supset E$ 和紧致集 $K\subset E$ 满足 $\mu(U\setminus K)<\varepsilon$，并且根据 Urysohn 引理，存在 $f \in C_{c}(X)$ 使得 $\chi_{K}\leq f\leq \chi_{U}$，因此 $\lVert \chi_{E}-f \rVert_{p}\leq \mu(U\setminus K)^{1/p}<\varepsilon^{1/p}$，这就完成了证明。

**定理 29.2.6** Lusin 定理

设 $\mu$ 是 LCH 空间 $X$ 上的 Radon 测度，$f\colon X\to \mathbb{C}$ 是一个可测函数，且在一个有限测度集外消失，则对任意 $\varepsilon>0$，存在 $\phi \in C_{c}(X)$ 使得在一个测度 $<\varepsilon$ 的集合外有 $\phi=f$. 如果 $f$ 是有界的，那么可以选取 $\phi$ 使其满足 $\lVert \phi \rVert_{u}\leq \lVert f \rVert_{u}$.

**证明**

令 $E=\{ x \mid f(x)\neq 0 \}$，则 $\mu(E)<\infty$. 首先设 $f$ 是有界的，于是 $f \in L^{1}(\mu)$，从而根据定理 29.2.7，存在 $(g_{n}^{*})\subset C_{c}(X)$ 按 $L^{1}$ 范数收敛于 $f$，于是根据定理 22.1.4，存在它的一个子序列 $(g_{n})$ 收敛于 $f$ a.e. 再根据 Egoroff 定理，存在 $A\subset E$ 使得 $\mu(E\setminus A)<\varepsilon / 3$ 且 $g_{n}$ 在 $A$ 上一致收敛于 $f$，并且还存在紧致集 $B\subset A$ 和开集 $U\supset E$ 使得 $\mu(A\setminus B)<\varepsilon / 3$ 且 $\mu(U\setminus E)<\varepsilon / 3$. 由于 $g_{n}$ 在 $B$ 上一致收敛于 $f$，故 $f|_{B}$ 是连续的，则根据 Tietze 扩张定理，存在 $h \in C_{c}(X)$ 使得在 $B$ 上有 $h=f$ 且 $\mathrm{supp}(h)\subset U$，但此时有 $\{ x \mid f(x)\neq h(x) \}\subset U\setminus B$，其满足 $\mu(U\setminus B)<\varepsilon$.

下面定义 $\beta\colon \mathbb{C}\to \mathbb{C}$ 如下：

$$
\begin{gather}
\beta(z)=\begin{cases}
z &, |z|\leq \lVert f \rVert _{u} \\
\lVert f \rVert _{u} \mathrm{sgn}\ z &, |z|>\lVert f \rVert _{u}
\end{cases}
\end{gather}
$$

并且令 $\phi=\beta \circ h$，则 $\phi \in C_{c}(X)$，因为 $\beta$ 是连续的，$\beta(0)=0$. 此外，$\lVert \phi \rVert_{u}\leq \lVert f \rVert_{u}$，并且当 $h=f$ 时有 $\phi=f$，即证。

现在设 $f$ 是无界的，令 $A_{n}=\{ x \mid 0<|f(x)|\leq n \}$，则 $A_{n}$ 递增且 $E=\bigcup_{j=1}^{\infty}A_{j}$，于是对足够大的 $n$，有 $\mu(E\setminus A_{n})<\varepsilon / 2$ 成立。对有界函数 $f\chi_{A_{n}}$ 重复上述论证，可知存在 $\phi \in C_{c}(X)$ 使得 $\phi=f\chi_{A_{n}}$ 在一个测度 $<\varepsilon / 2$ 的集合外成立，于是 $\phi=f$ 在一个测度 $<\varepsilon$ 的集合外成立。

上述定理是对 22.1.7 的一个扩展，同样表明了可测函数与连续函数几乎是相同的。

本节的最后一个主题研究的是所谓的**半连续函数**：

**定义 29.2.7** 下半连续（lower semicontinuous），上半连续（upper semicontinuous）

设 $X$ 是拓扑空间，称函数 $f\colon X\to(-\infty,\infty]$ 是**下半连续的**，如果对任意 $a \in \mathbb{R}$，$f^{-1}[(a,\infty]]$ 是开集；称函数 $f\colon X\to[-\infty,\infty)$ 是**上半连续的**，如果对任意 $a \in \mathbb{R}$，$f^{-1}[[-\infty,a)]$ 是开集。

显然，如果 $f$ 是连续的，那么 $f$ 就是下半连续且上半连续的，反之亦然。下面我们给出半连续函数的基本性质。

**定理 29.2.8**

设 $X$ 是拓扑空间，则：

1. 如果 $U\subset X$ 是开集，那么 $\chi_{U}$ 是下半连续的。
2. 如果 $f$ 下半连续且 $c\geq 0$，则 $cf$ 下半连续。
3. 如果 $\mathcal{G}$ 是一族下半连续函数，$f(x)=\sup \{ g(x) \mid g \in \mathcal{G} \}$，则 $f$ 下半连续。
4. 如果 $f,g$ 下半连续，那么 $f+g$ 下半连续。
5. 如果 $X$ 是 LCH 空间且 $f\geq 0$ 是下半连续的，那么

$$
\begin{gather}
f(x)=\sup \{ g(x) \mid g \in C_{c}(X) ,0 \leq g\leq f \}
\end{gather}
$$

**证明**

1 和 2 是显然的。3 可以由以下等式推出：

$$
\begin{gather}
f^{-1}[(a,\infty]] = \bigcup_{g \in \mathcal{G}} g^{-1}[(a,\infty]]
\end{gather}
$$

对于 4，如果 $f(x_{0})+g(x_{0})>a$，取 $\varepsilon>0$ 使得 $f(x_{0})>a-g(x_{0})+\varepsilon$，则

$$
\begin{gather}
\{ x \mid (f+g)(x)>a \}\supset \{ x \mid f(x)>a-g(x_{0})+\varepsilon \}\cap \{ x \mid g(x)>g(x_{0})-\varepsilon \}
\end{gather}
$$

而右边是 $x_{0}$ 的一个邻域，从而 $\{ x \mid (f+g)(x)>a \}$ 是开集，即证。最后，如果 $X$ 是 LCH 空间，当 $f(x)=0$ 时是平凡的. 设 $f(x)>0$，且 $0<a<f(x)$，则 $U=\{ y \mid f(y)>a \}$ 是一个包含 $x$ 的开集，因而根据 Urysohn 引理，存在 $g \in C_{c}(X)$ 使得 $g(x)=a$ 且 $0\leq g\leq a\chi_{U}\leq f$，这就证明了 5.

上述定理有上半连续函数的对应版本，这里就不赘述了。下面的定理是一个关于下半连续函数网的单调收敛定理。

**定理 29.2.9**

设 $\mathcal{G}$ 是一族定义在 LCH 空间 $X$ 上的非负下半连续函数，由 $\leq$ 所定向（即，对任意 $g_{1},g_{2}\in \mathcal{G}$，存在 $g \in \mathcal{G}$ 使得 $g_{1}\leq g,g_{2}\leq g$），令 $f=\sup \{ g \mid g \in \mathcal{G} \}$，则如果 $\mu$ 是 $X$ 上的 Radon 测度，那么有 $\int f\mathrm{d}\mu=\sup \left\{  \int g\mathrm{d}\mu \mid g \in \mathcal{G}  \right\}$.

**证明**

根据 29.2.8(3)，$f$ 下半连续，从而是 Borel 可测的，并且显然 $\int f\mathrm{d}\mu\geq \sup \int g\mathrm{d}\mu$. 要证明反向的不等式，考虑递增且收敛于 $f$ 的简单函数序列 $\phi_{n}$，定义如下：

$$
\begin{gather}
\phi_{n}= \dfrac{1}{2^{n}} \sum_{j=1}^{2^{2n}} \chi_{U_{nj}},\quad U_{nj}=\{ x \mid f(x)> j 2^{-n} \}
\end{gather}
$$

根据单调收敛定理，对任意 $a< \int f\mathrm{d}\mu$，存在 $n$ 足够大使得 $2^{-n}\sum_{j=1}^{2^{2n}}\mu(U_{nj})=\int \phi_{n}\mathrm{d}\mu>a$. 由于 $U_{nj}$ 是开集，故存在紧致集 $K_{j}\subset U_{nj}$ 使得 $2^{-n}\sum_{j=1}^{2^{2n}}\mu(K_{j})>a$，令 $\psi=2^{-n}\sum_{j=1}^{2^{2n}}\chi_{K_{j}}$，则对任意 $x \in \bigcup_{j=1}^{2^{2n}}K_{j}$ 有 $f(x)>\phi_{n}(x)\geq \psi(x)$，于是存在 $g_{x}\in \mathcal{G}$ 使得 $g_{x}(x)>\psi(x)$. 又因为 $-\chi_{K_{j}}$ 是下半连续的，故 $g_{x}-\psi$ 下半连续，因此 $V_{x}=\{ y \mid \psi(y)<g_{x}(y) \}$ 是开集，从而 $\left\{  V_{x} \mid x \in \bigcup_{j=1}^{2^{2n}}K_{j}  \right\}$ 是 $\bigcup_{j=1}^{2^{2n}}K_{j}$ 的一个开覆盖，因此有一个子覆盖 $V_{x_{1}},\dots,V_{x_{m}}$. 取 $g \in \mathcal{G}$ 使得 $g_{x_{j}}\leq g$，则 $\psi\leq g$，故 $\int g\mathrm{d}\mu>a$. 由于 $a$ 是任意的，这就完成了证明。

结合 29.2.8(5) 和 29.2.9，我们可得推论：

**定理 29.2.10**

如果 $\mu$ 是 LCH 空间 $X$ 上的 Radon 测度，$f\geq 0$ 是下半连续的，那么

$$
\begin{gather}
\int f\mathrm{d} \mu=\sup \left\{  \int g \mathrm{d} \mu \middle| g \in C_{c}(X),0\leq g\leq f  \right\}
\end{gather}
$$

**定理 29.2.11**

如果 $\mu$ 是 LCH 空间 $X$ 上的 Radon 测度，$f\geq 0$ 是 Borel 可测函数，那么

$$
\begin{gather}
\int f \mathrm{d} \mu=\inf \left\{  \int g\mathrm{d} \mu \middle| g\geq f, g\text{下半连续}  \right\}
\end{gather}
$$

如果 $\{ x \mid f(x)>0 \}$ 是 $\sigma$-有限的，那么

$$
\begin{gather}
\int f\mathrm{d} \mu=\sup \left\{  \int g\mathrm{d} \mu \middle| 0\leq g\leq f, g\text{上半连续}  \right\}
\end{gather}
$$

**证明**

设 $(\phi_{n})$ 是递增并收敛于 $f$ 的简单函数，则 $f=\phi_{1}+\sum_{n=2}^{\infty}(\phi_{n}-\phi_{n-1})$，右边的每一项都是非负的简单函数，因此 $f$ 可以表示为 $f=\sum_{j=1}^{\infty}a_{j}\chi_{E_{j}}$，其中 $a_{j}>0$. 给定 $\varepsilon>0$，对任意 $j$，可以选取开集 $U_{j}\supset E_{j}$ 使得 $\mu(U_{j})\leq \mu(E_{j})+\varepsilon / 2^{j}a_{j}$，则 $g=\sum_{j=1}^{\infty}a_{j}\chi_{U_{j}}$ 是下半连续的，$g\geq f$，且 $\int g\mathrm{d}\mu\leq \int f\mathrm{d}\mu+\varepsilon$，这就证明了第一个等式。

如果 $\{ x \mid f(x)>0 \}$ 是 $\sigma$-有限的，那么各 $E_{j}$ 都是 $\sigma$-有限的。对任意 $a<\int f\mathrm{d}\mu$，存在 $N$ 足够大使得 $\sum_{j=1}^{N}a_{j}\mu(E_{j})>a$，根据定理 29.2.1，存在紧致集 $K_{j}\subset E_{j}$ 使得 $\sum_{j=1}^{N}a_{j}\mu(K_{j})>a$，于是上半连续函数 $g=\sum_{j=1}^{N}a_{j}\chi_{K_{j}}$ 满足 $g\leq f$ 且 $\int g\mathrm{d}\mu>a$，这就完成了证明。

# Section 3: $C_{0}(X)$ 的对偶

回顾一下，对于 LCH 空间 $X$，$C_{0}(X)$ 是 $C_{c}(X)$ 的一致闭包，因此如果 $\mu$ 是 $X$ 上的 Radon 测度，那么 $C_{c}(X)$ 上的正线性泛函 $I(f)=\int f\mathrm{d}\mu$ 可以连续地扩张到 $C_{0}(X)$ 上，当且仅当 $I$ 在一致范数下是连续的（有界的）。根据 Riesz 表示定理，我们有等式

$$
\begin{gather}
\mu(X)=\sup \left\{  \int f \mathrm{d} \mu \middle| f \in C_{c}(X), 0\leq f\leq 1  \right\}
\end{gather}
$$

再根据 $\left\lvert  \int f\mathrm{d}\mu  \right\rvert\leq \int|f|\mathrm{d}\mu$，$I$ 是有界的当且仅当 $\mu(X)<\infty$，此时 $\mu(X)$ 就等于 $I$ 的算子范数。

于是，我们就刻画了 $C_{0}(X)$ 上的正线性泛函：它们由关于有限 Radon 测度的积分给出。本节的目标就是将上述结论进行扩展，使之能够完全地刻画 $C_{0}(X)^{*}$. 我们的第一个关键引理就是 $C_{0}(X,\mathbb{R})$ 上的实线性泛函具有“Jordan 分解”。

**引理 29.3.1**

设 $X$ 是 LCH 空间，$I \in C_{0}(X,\mathbb{R})^{*}$，则存在正线性泛函 $I^{\pm}\in C_{0}(X,\mathbb{R})^{*}$ 使得 $I=I^{+}-I^{-}$.

**证明**

如果 $f \in C_{0}(X,[0,\infty))$，定义

$$
\begin{gather}
I^{+}(f)=\sup \{ I(g) \mid g \in C_{0}(X,\mathbb{R}),0\leq g\leq f \}
\end{gather}
$$

对于 $0\leq g\leq f$，我们有 $|I(g)|\leq \lVert I \rVert\lVert g \rVert_{u}\leq \lVert I \rVert\lVert f \rVert_{u}$，并且 $I(0)=0$，因此有 $0\leq I^{+}(f)\leq \lVert I \rVert\lVert f \rVert_{u}$. 下面我们要证 $I^{+}$ 是线性的。

当 $c\geq 0$ 时，显然有 $I^{+}(cf)=cI^{+}(f)$. 设 $0\leq g_{1}\leq f_{1}$ 且 $0\leq g_{2}\leq f_{2}$，则 $0\leq g_{1}+g_{2}\leq f_{1}+f_{2}$，因此 $I^{+}(f_{1}+f_{2})\geq I(g_{1})+I(g_{2})$，进而有 $I^{+}(f_{1}+f_{2})\geq I^{+}(f_{1})+I^{+}(f_{2})$. 另一边，如果 $0\leq g\leq f_{1}+f_{2}$，令 $g_{1}=\min(g,f_{1})$，$g_{2}=g-g_{1}$，则 $0\leq g_{1}\leq f_{1}$ 且 $0\leq g_{2}\leq f_{2}$，从而 $I(g_{1})+I(g_{2})\leq I^{+}(f_{1})+I^{+}(f_{2})$，即 $I^{+}(f_{1}+f_{2})\leq I^{+}(f_{1})+I^{+}(f_{2})$，即证 $I^{+}(f_{1}+f_{2})=I^{+}(f_{1})+I^{+}(f_{2})$.

现在，如果 $f \in C_{0}(X,\mathbb{R})$，它的正部和负部 $f^{\pm}\in C_{0}(X,[0,\infty))$，定义 $I^{+}(f)=I^{+}(f^{+})-I^{+}(f^{-})$. 如果又有 $f=g-h$，其中 $g,h\geq 0$，那么我们有 $f^{+}+h=g+f^{-}$，于是 $I^{+}(f^{+})+I^{+}(h)=I^{+}(g)+I^{+}(f^{-})$，移项即得 $I^{+}(f)=I^{+}(g)-I^{+}(h)$，因此该定义是良定的。下面仿照定理 21.4.2 的证明即可得到 $I^{+}$ 的线性性。此外，有

$$
\begin{gather}
|I^{+}(f)|\leq \max(I^{+}(f^{+}),I^{+}(f^{-}))\leq \lVert I \rVert \max(\lVert f^{+} \rVert _{u},\lVert f^{-} \rVert _{u})=\lVert I \rVert \lVert f \rVert _{u}
\end{gather}
$$

因此 $\lVert I^{+} \rVert\leq \lVert I \rVert$，即 $I^{+}\in C_{0}(X,\mathbb{R})^{*}$.

最后，令 $I^{-}=I^{+}-I$，则 $I^{-}\in C_{0}(X,\mathbb{R})^{*}$，并且根据定义即得 $I^{\pm}$ 是正线性泛函，这就完成了证明。

对于 $I \in C_{0}(X)^{*}$，我们可以将其分解为 $I=J_{1}+i J_{2}$，其中 $J_{1},J_{2}$ 是 $C_{0}(X,\mathbb{R})$ 上的实线性泛函，因而根据引理 29.3.1 以及 Riesz 表示定理，对任意 $I \in C_{0}(X)^{*}$，存在有限 Radon 测度 $\mu_{j},j=1,2,3,4$ 使得 $I(f)=\int f\mathrm{d}\mu$，其中 $\mu=\mu_{1}-\mu_{2}+i(\mu_{3}-\mu_{4})$，这正是复测度的 Jordan 分解式，由此我们给出以下定义：

**定义 29.3.2** 符号 Radon 测度（signed Radon measure），复 Radon 测度（complex Radon measure）

设 $X$ 是 LCH 空间，$X$ 上的一个**符号 Radon 测度**是一个符号 Borel 测度，其正变差和负变差都是 Radon 测度；$X$ 上的一个**复 Radon 测度**是一个复 Borel 测度，其实部和虚部都是符号 Radon 测度。

$X$ 上所有复 Radon 测度构成的空间记作 $M(X)$. 对任意 $\mu \in M(X)$，定义

$$
\begin{gather}
\lVert \mu \rVert = |\mu|(X)
\end{gather}
$$

其中 $|\mu|$ 是 $\mu$ 的总变差。

**定理 29.3.3**

设 $X$ 是 LCH 空间，如果 $\mu$ 是复 Borel 测度，那么 $\mu$ 是复 Radon 测度当且仅当 $|\mu|$ 是 Radon 测度。此外，$M(X)$ 是一个向量空间，$\mu\mapsto \lVert \mu \rVert$ 是其上的一个范数。

**证明**

根据定理 29.2.1 和 29.2.3，一个有限正 Borel 测度 $\nu$ 是 Radon 测度当且仅当对任意 Borel 集 $E$ 和 $\varepsilon>0$，存在紧致集 $K$ 和开集 $U$ 使得 $K\subset E\subset U$ 且 $\nu(U\setminus K)<\varepsilon$. 因此，设 $\mu=\mu_{1}-\mu_{2}+i(\mu_{3}-\mu_{4})$，如果 $|\mu|(U\setminus K)<\varepsilon$，那么显然有 $\mu_{j}(U\setminus K)<\varepsilon$；反之，可以选取 $U_{j},K_{j}$ 使得 $\mu_{j}(U_{j}\setminus K_{j})<\varepsilon / 4$，令 $U=\bigcap_{j=1}^{4}U_{j},K=\bigcup_{j=1}^{4}K_{j}$，则 $|\mu|(U\setminus K)<\varepsilon$，这就证明了第一个结论。同样的论证过程可以用来证明 $M(X)$ 在加法和数乘下封闭，从而是一个向量空间。最后，根据三角不等式（定理 23.3.5），即证 $\lVert \cdot \rVert$ 是一个范数。

**定理 29.3.4** Riesz 表示定理（Riesz representation theorem）

设 $X$ 是 LCH 空间，对 $\mu \in M(X)$ 和 $f \in C_{0}(X)$ 定义 $I_{\mu}(f)=\int f\mathrm{d}\mu$，则 $\mu\mapsto I_{\mu}$ 是从 $M(X)$ 到 $C_{0}(X)^{*}$ 的等距同构。

**证明**

我们已经证明了每个 $I \in C_{0}(X)^{*}$ 都具有形式 $I(f)=\int f\mathrm{d}\mu$. 另一方面，设 $\mu \in M(X)$，则根据定理 23.3.4 有

$$
\begin{gather}
\left\lvert  \int f\mathrm{d} \mu  \right\rvert \leq \int|f|\mathrm{d} |\mu|\leq \lVert f \rVert _{u}\lVert \mu \rVert 
\end{gather}
$$

因此 $I_{\mu}\in C_{0}(X)^{*}$ 且 $\lVert I_{\mu} \rVert\leq \lVert \mu \rVert$. 此外，如果 $h= \dfrac{\mathrm{d}\mu}{\mathrm{d}|\mu|}$，那么根据定理 23.3.4，$|h|=1$ $|\mu|$-a.e.，因此根据 Lusin 定理，对任意 $\varepsilon>0$，存在 $f \in C_{c}(X)$ 使得 $\lVert f \rVert_{u}=1$ 且在一个 $|\mu|$-测度 $<\varepsilon / 2$ 的集合 $E$ 之外有 $f=\overline{h}$，从而

$$
\begin{align}
\lVert \mu \rVert &= \int |h|^{2} \mathrm{d} |\mu|= \int \overline{h} \mathrm{d} \mu\leq \left\lvert  \int f\mathrm{d} \mu  \right\rvert +\left\lvert  \int(f-\overline{h})\mathrm{d} \mu  \right\rvert  \\
&\leq \left\lvert  \int f\mathrm{d} \mu  \right\rvert +2|\mu|(E)< \lVert I_{\mu} \rVert +\varepsilon
\end{align}
$$

令 $\varepsilon\to 0$ 即得 $\lVert \mu \rVert\leq \lVert I_{\mu} \rVert$，因而 $\lVert \mu \rVert=\lVert I_{\mu} \rVert$，这就完成了证明。

对于紧致 Hausdorff 空间，我们有推论：

**定理 29.3.5**

设 $X$ 是紧致 Hausdorff 空间，则 $C(X)^{*}$ 等距同构于 $M(X)$.

根据 Riesz 表示定理，我们就可以把复 Radon 测度 $\mu$ 与 $C_{0}(X)$ 上的有界线性泛函 $I(f)=\int f\mathrm{d}\mu$ 等同起来。此外，我们还有如下结果：

**定理 29.3.6**

设 $\mu$ 是 LCH 空间 $X$ 上的 Radon 测度，如果 $\phi \in L^{1}(\mu)$ 且 $\phi\geq 0$，那么 $\nu(E)=\int_{E}\phi \mathrm{d}\mu$ 是一个 Radon 测度。

**证明**

由于 $\phi \in L^{1}(\mu)$，故 $\nu(X)<\infty$，因此 $\nu$ 是一个有限 Borel 测度。根据定理 23.2.4，对任意 $\varepsilon>0$，存在 $\delta>0$ 使得对任意满足 $\mu(E)<\delta$ 的 Borel 集 $E$ 有 $\left\lvert  \int_{E}\phi \mathrm{d}\mu  \right\rvert<\varepsilon$，再根据 $\mu$ 的正则性，存在紧致集 $K$ 和开集 $U$ 使得 $K\subset E\subset U$ 且 $\mu(U\setminus K)<\delta$，从而 $\nu(U\setminus K)=\int_{U\setminus K}\phi \mathrm{d}\mu<\varepsilon$，即证。

因此当 $f \in L^{1}(\mu)$ 时，复测度 $\mathrm{d}\nu_{f}=f\mathrm{d}\mu$ 就是一个复 Radon 测度，并且 $\lVert \nu_{f} \rVert=\int|f|\mathrm{d}\mu=\lVert f \rVert_{1}$，从而 $f\mapsto \nu_{f}$ 就是从 $L^{1}(\mu)$ 到 $M(X)$ 的一个等距嵌入，故我们可以把 $L^{1}(\mu)$ 和 $M(X)$ 的子空间等同起来，其恰好包含了那些 $\nu \in M(X)$ 使得 $\nu\ll \mu$（根据 Radon-Nikodym 定理）。这其中最重要的例子就是 $\mu=m$ 是 $\mathbb{R}^{n}$ 上的 Lebesgue 测度的时候，此时我们可以将 $L^{1}(m)$ 与 $M(\mathbb{R}^{n})$ 的子空间等同起来。

$M(X) \cong C_{0}(X)^{*}$ 上的弱$^{*}$拓扑，其中 $\mu_{\alpha}\to \mu$ 当且仅当 $\int f\mathrm{d}\mu_{\alpha}\to \int f\mathrm{d}\mu$ 对任意 $f \in C_{0}(X)$ 成立，在概率论中有非常广泛的应用，因此我们给它一个名字，称为**淡拓扑**（vague topology）。在 $L^{p}$ 空间上，使用弱收敛的证明方法通常对 $p=1$ 不起效果，因为通常 $L^{1}$ 空间不是 $L^{\infty}$ 空间的对偶，不过，把 $L^{1}$ 视为 $M(X)$ 的子空间并采用淡收敛的方法通常是一种好的替代。

最后我们给出 $M(\mathbb{R})$ 上淡收敛的一个判断准则，也就是所谓的“依分布收敛”。

**定理 29.3.7**

设 $\mu,\mu_{1},\mu_{2},\dots \in M(\mathbb{R})$，定义 $F(x)=\mu((-\infty,x])$，$F_{n}(x)=\mu_{n}((-\infty,x])$，则：

1. 如果 $\sup_{n}\lVert \mu_{n} \rVert<\infty$ 且在 $F$ 的连续点上有 $F_{n}(x)\to F(x)$，那么 $\mu_{n}$ 淡收敛于 $\mu$.
2. 如果 $\mu_{n}$ 淡收敛于 $\mu$，那么 $\sup_{n}\lVert \mu_{n} \rVert<\infty$. 如果进一步有 $\mu_{n}$ 是正测度，那么在 $F$ 的连续点上有 $F_{n}(x)\to F(x)$.

**证明**

(1). 根据定理 24.2.6 和 24.2.8，$F$ 的间断点构成的集合是至多可数的，因此有 $F_{n}(x)\to F(x)$ a.e.，此外，$\lVert F_{n} \rVert_{u}\leq \lVert \mu_{n} \rVert$，因此 $(F_{n})$ 是一致有界的。如果 $f \in C_{c}(\mathbb{R})$ 是连续可微的，那么根据分部积分法以及控制收敛定理可得

$$
\begin{gather}
\int f\mathrm{d} \mu_{n} = \int f'(x)F_{n}(x)\mathrm{d} x\to \int f'(x) F(x)\mathrm{d} x=\int f \mathrm{d} \mu
\end{gather}
$$

而根据 Stone-Weierstrass 定理（26.2.10），这样的 $f$ 在 $C_{0}(\mathbb{R})$ 中是稠密的，因此根据定理 27.4.6 知对任意 $f \in C_{0}(\mathbb{R})$ 有 $\int f\mathrm{d}\mu_{n}\to \int f\mathrm{d}\mu$ 成立，即 $\mu_{n}$ 淡收敛于 $\mu$.

(2). 如果 $\mu_{n}$ 淡收敛于 $\mu$，根据一致有界原理可知 $\sup_{n}\lVert \mu_{n} \rVert<\infty$. 设 $\mu_{n}\geq 0$，则 $\mu\geq 0$，并设 $F$ 在 $x=a$ 处连续。考虑 $f \in C_{c}(\mathbb{R})$ 满足 $f$ 在 $[-N,a]$ 上为 $1$，在 $(-\infty,-N-\varepsilon]$ 和 $[a+\varepsilon,\infty)$ 上为 $0$，在其余位置是线性的，则我们有

$$
\begin{align}
F_{n}(a)-F_{n}(-N)&=\mu_{n}((-N,a])\leq \int f\mathrm{d} \mu_{n}\to \int f\mathrm{d} \mu \\
&\leq F(a+\varepsilon)-F(-N-\varepsilon)
\end{align}
$$

令 $N\to \infty$，则 $F_{n}(-N)\to 0,F(-N-\varepsilon)\to 0$，因此

$$
\begin{gather}
\limsup_{ n \to \infty } F_{n}(a)\leq F(a+\varepsilon)
\end{gather}
$$

同理，考虑 $f\in C_{c}(\mathbb{R})$ 满足 $f$ 在 $[-N+\varepsilon,a-\varepsilon]$ 上为 $1$，在 $(-\infty,-N]$ 和 $[a,\infty)$ 上为 $0$，在其余位置线性，则有

$$
\begin{gather}
\liminf_{ n \to \infty } F_{n}(a)\geq F(a-\varepsilon)
\end{gather}
$$

由于 $F$ 在 $a$ 处连续，令 $\varepsilon\to 0$ 即得 $F_{n}(a)\to F(a)$，这就完成了证明。

# Section 4: Radon 测度的乘积

本节我们来研究乘积空间上的 Radon 测度，我们以一个简单的结论开始。

**定理 29.4.1**

设 $X,Y$ 是 LCH 空间，则：

1. $\mathcal{B}_{X}\otimes \mathcal{B}_{Y}\subset \mathcal{B}_{X\times Y}$
2. 如果 $X,Y$ 是第二可数的，那么 $\mathcal{B}_{X}\otimes \mathcal{B}_{Y}=\mathcal{B}_{X\times Y}$.
3. 如果 $X,Y$ 是第二可数的且 $\mu,\nu$ 分别是 $X,Y$ 上的 Radon 测度，那么 $\mu \times \nu$ 是 $X\times Y$ 上的 Radon 测度。

**证明**

根据定理 20.1.9，$\mathcal{B}_{X}\otimes \mathcal{B}_{Y}$ 由 $U\times V$ 生成，其中 $U\subset X$ 和 $V\subset Y$ 是开集，而 $U\times V$ 在 $X\times Y$ 中也是开集，因而有 $\mathcal{B}_{X}\otimes \mathcal{B}_{Y}\subset \mathcal{B}_{X\times Y}$. 如果 $X,Y$ 是第二可数的，那么 $X,Y$ 上的拓扑分别有基 $\mathcal{E},\mathcal{F}$，于是 $\mathcal{B}_{X}$，$\mathcal{B}_{Y}$ 和 $\mathcal{B}_{X\times Y}$ 分别由 $\mathcal{E}$，$\mathcal{F}$，$\{ U\times V\mid U \in \mathcal{E},V \in \mathcal{F} \}$ 生成，进而就有 $\mathcal{B}_{X}\otimes \mathcal{B}_{Y}=\mathcal{B}_{X\times Y}$.

最后，显然 $\mu \times \nu$ 是 $X\times Y$ 上的 Borel 测度，则根据定理 29.2.4，我们只需证明 $\mu \times \nu(K)<\infty$ 对紧致集 $K$ 成立：考虑其投影 $\pi_{X}(K)$ 和 $\pi_{Y}(K)$，它们都是紧致的，并且 $K\subset \pi_{X}(K)\times \pi_{Y}(K)$，从而 $\mu \times \nu(K)\leq \mu(\pi_{X}(K))\nu(\pi_{Y}(K))<\infty$，即证。

当 $X$ 或 $Y$ 不是第二可数的时候，$\mathcal{B}_{X}\otimes \mathcal{B}_{Y}$ 就不一定等于 $\mathcal{B}_{X\times Y}$，在这种情况下 $\mu \times \nu$ 就不是一个 Radon 测度了。不过幸运的是，我们有一种自然的方法来构造 Radon 测度，为此，我们需要给出一些关于连续函数的结论。

如果 $g,h$ 分别是 $X,Y$ 上的函数，我们定义 $X\times Y$ 上的函数 $g\otimes h$ 如下：

$$
\begin{gather}
g\otimes h(x,y)=g(x)h(y)
\end{gather}
$$

**定理 29.4.2**

设 $X,Y$ 是 LCH 空间，$\mathcal{P}$ 是由函数 $g\otimes h$，其中 $g \in C_{c}(X),h \in C_{c}(Y)$ 张成的向量空间，那么 $\mathcal{P}$ 在 $C_{c}(X\times Y)$ 中稠密。更精确地说，给定 $f \in C_{c}(X\times Y)$ 和 $\varepsilon>0$，以及预紧致的开集 $U\subset X,V\subset Y$ 分别包含 $\pi_{X}(\mathrm{supp}(f))$ 和 $\pi_{Y}(\mathrm{supp}(f))$，则存在 $F\in \mathcal{P}$ 使得 $\lVert F-f \rVert_{u}<\varepsilon$ 且 $\mathrm{supp}(F)\subset U\times V$.

**证明**

$\overline{U}\times  \overline{V}$ 是一个紧致 Hausdorff 空间，根据 Stone-Weierstrass 定理，$\{ g\otimes h \mid g \in C(\overline{U}),h \in C(\overline{V}) \}$ 的线性张成在 $C(\overline{U}\times  \overline{V})$ 中是稠密的。特别地，存在张成空间中的元素 $G$ 使得 $\sup_{\overline{U}\times \overline{V}}|G-f|<\varepsilon$. 此外，根据 Urysohn 引理，存在 $\phi \in C_{c}(U,[0,1])$ 和 $\psi \in C_{c}(V,[0,1])$ 使得分别在 $\pi_{X}(\mathrm{supp}(f))$ 和 $\pi_{Y}(\mathrm{supp}(f))$ 上有 $\phi=1$ 和 $\psi=1$，定义

$$
\begin{gather}
F(x,y)=\begin{cases}
\phi(x)\psi(y)G(x,y) &, (x,y) \in \overline{U}\times \overline{V} \\
0 &, (x,y) \not\in \overline{U}\times \overline{V}
\end{cases}
\end{gather}
$$

则 $F\in \mathcal{P}$，$\lVert F-f \rVert_{u}<\varepsilon$，且 $\mathrm{supp}(F)\subset U\times V$.

**定理 29.4.3**

设 $X,Y$ 是 LCH 空间，则每个 $f \in C_{c}(X\times Y)$ 都是 $\mathcal{B}_{X}\otimes \mathcal{B}_{Y}$-可测的。此外，如果 $\mu,\nu$ 分别是 $X,Y$ 上的 Radon 测度，则 $C_{c}(X\times Y)\subset L^{1}(\mu \times \nu)$，并且对任意 $f \in C_{c}(X\times Y)$ 有

$$
\begin{gather}
\int f\mathrm{d} (\mu \times \nu)=\iint f\mathrm{d} \mu \mathrm{d} \nu=\iint f\mathrm{d} \nu \mathrm{d} \mu
\end{gather}
$$

**证明**

如果 $g \in C_{c}(X),h \in C_{c}(Y)$，则 $g\otimes h=(g\circ \pi_{X})(h\circ \pi_{Y})$，由于投影函数是可测的，$g,h$ 是连续的，故 $g\otimes h$ 是可测的。又由于可测函数的和、积与逐点极限都是可测的，故由定理 29.4.2 可得第一个结论。另一方面，每个 $f \in C_{c}(X\times Y)$ 都是有界的，并且支撑在一个具有有限测度的紧致集上，因此 $f \in L^{1}(\mu \times \nu)$. 最后，为使用 Fubini 定理，我们可以将 $\mu$ 和 $\nu$ 限制在 $\pi_{X}(\mathrm{supp}(f))$ 和 $\pi_{Y}(\mathrm{supp}(f))$ 上，得到两个有限测度，进而由 Fubini 定理知等式成立。

现在，构造 Radon 测度的方法就很清晰了：根据定理 29.4.3，定义为 $I(f)=\int f\mathrm{d}(\mu \times \nu)$ 的函数 $I$ 是 $C_{c}(X\times Y)$ 上的正线性泛函，从而根据 Riesz 表示定理，存在唯一的 Radon 测度与之对应。由此我们给出以下定义：

**定义 29.4.4** Radon 乘积（Radon product）

设 $X,Y$ 是 LCH 空间，$\mu,\nu$ 分别是 $X,Y$ 上的 Radon 测度，则 $C_{c}(X\times Y)$ 上的正线性泛函 $I(f)=\int f\mathrm{d}(\mu \times \nu)$ 所对应的 Radon 测度称为 $\mu$ 和 $\nu$ 的 **Radon 乘积测度**，记作 $\mu \otimes \nu$.

一个显然的问题是，在 $\mathcal{B}_{X}\otimes \mathcal{B}_{Y}$ 上是否有 $\mu \otimes \nu=\mu \times \nu$ ？一般来说，答案是否定的。然而，如果我们假设 $\mu,\nu$ 是 $\sigma$-有限的，那么不仅我们可以得到上述等式，我们还能够证明一个 Fubini-Tonelli 类的定理。

**引理 29.4.5**

设 $X,Y$ 是 LCH 空间，则：

1. 如果 $E \in \mathcal{B}_{X\times Y}$，那么 $E_{x}\in \mathcal{B}_{Y}$ 对任意 $x \in X$ 成立且 $E^{y}\in \mathcal{B}_{X}$ 对任意 $y \in Y$ 成立。
2. 如果 $f\colon X\times Y\to \mathbb{C}$ 是 $\mathcal{B}_{X\times Y}$-可测的，那么对任意 $x \in X$ 和 $y \in Y$，$f_{x}$ 是 $\mathcal{B}_{Y}$-可测的且 $f^{y}$ 是 $\mathcal{B}_{X}$-可测的。

**证明**

所有满足 $E_{x}\in \mathcal{B}_{Y}$ 且 $E^{y}\in \mathcal{B}_{X}$ 的 $E\subset X\times Y$ 构成的集族显然是一个 $\sigma$-代数，并且它包含了所有开集：如果 $E$ 是开集，那么 $E_{x}$ 和 $E^{y}$ 都是开集，因为它们分别是 $y'\mapsto(x,y')$ 和 $x'\mapsto(x',y)$ 的原像，从而它包含了 $\mathcal{B}_{X\times Y}$，这就证明了 1. 对于 2，利用 $(f_{x})^{-1}[A]=(f^{-1}[A])_{x}$，$(f^{y})^{-1}[A]=(f^{-1}[A])^{y}$ 以及 1 的结果即证。

**引理 29.4.6**

设 $X,Y$ 是 LCH 空间，如果 $f\in C_{c}(X\times Y)$ 且 $\mu,\nu$ 分别是 $X,Y$ 上的 Radon 测度，那么函数 $x\mapsto \int f_{x}\mathrm{d}\nu$ 和 $y\mapsto \int f^{y}\mathrm{d}\mu$ 是连续的。

**证明**

我们给出 $f_{x}$ 的证明，$f^{y}$ 的证明是类似的。我们只需证明对任意 $x_{0}\in X$ 和 $\varepsilon>0$，存在 $x_{0}$ 的邻域 $U$ 使得对任意 $x \in U$ 有 $\lVert f_{x}-f_{x_{0}} \rVert_{u}<\varepsilon$，从而有

$$
\begin{gather}
\left\lvert  \int(f_{x}-f_{x_{0}}) \mathrm{d} \nu  \right\rvert \leq \varepsilon \nu(\pi_{Y}(\mathrm{supp}(f)))
\end{gather}
$$

对任意 $y \in \pi_{Y}(\mathrm{supp}(f))$，由于 $f$ 在 $(x_{0},y)$ 处连续，故存在 $x_{0}$ 和 $y$ 的邻域 $U_{y}\subset X,V_{y}\subset Y$ 使得当 $(x,z)\in U_{y}\times V_{y}$ 时有 $\lvert f(x,z)-f(x_{0},y) \rvert < \varepsilon / 2$. 所有的 $V_{y}$ 构成了 $\pi_{Y}(\mathrm{supp}(f))$ 的一个开覆盖，由紧致性我们可以取有限子覆盖 $V_{y_{1}},\dots,V_{y_{m}}$，并令 $U=\bigcap_{j=1}^{m}U_{j}$，这就是所求的邻域 $U$，即证。

**引理 29.4.7**

设 $X,Y$ 是 LCH 空间，$\mu,\nu$ 分别是 $X,Y$ 上的 Radon 测度，如果 $U\subset X\times Y$ 是开集，那么函数 $x\mapsto \nu(U_{x})$ 和 $y\mapsto \mu(U^{y})$ 都是 Borel 可测的，并且

$$
\begin{gather}
\mu \otimes \nu(U)=\int \nu(U_{x})\mathrm{d} \mu(x)=\int \mu(U^{y})\mathrm{d} \nu(y)
\end{gather}
$$

**证明**

设 $\mathcal{F}=\{ f \in C_{c}(X\times Y) \mid 0\leq f\leq \chi_{U} \}$，根据定理 29.2.8 我们有 $\chi_{U}=\sup \{ f \mid f \in \mathcal{F} \}$，从而 $\chi_{U_{x}}=\sup f_{x}$，$\chi_{U^{y}}=\sup f^{y}$，于是根据定理 29.2.9 有

$$
\begin{gather}
\mu \otimes \nu(U)=\sup \left\{  \int f \mathrm{d} (\mu \otimes \nu) \middle| f \in \mathcal{F}  \right\} \\
\nu(U_{x})=\sup \left\{  \int f_{x}\mathrm{d} \nu \middle| f \in \mathcal{F}  \right\}, \quad \mu(U^{y})=\sup \left\{  \int f^{y} \mathrm{d} \mu \middle| f \in \mathcal{F}  \right\}
\end{gather}
$$

由引理 29.4.6 和 29.2.8 可知，$x\mapsto \nu(U_{x})$ 和 $\mu(U^{y})$ 都是下半连续的，从而是 Borel 可测的。再次应用 29.2.9，以及 29.4.3 即得

$$
\begin{align}
\mu \otimes \nu(U)&= \sup \left\{  \iint f_{x}\mathrm{d} \nu \mathrm{d} \mu(x) \middle| f \in \mathcal{F}  \right\} \\
&= \int \left( \sup \left\{  \int f_{x}\mathrm{d} \nu \middle| f \in \mathcal{F}  \right\} \right) \mathrm{d} \mu(x) \\
&= \int \nu(U_{x}) \mathrm{d} \mu(x)
\end{align}
$$

同理可证 $\mu \otimes \nu(U)=\int \mu(U^{y})\mathrm{d}\nu(y)$，这就完成了证明。

**定理 29.4.8**

设 $X,Y$ 是 LCH 空间，$\mu,\nu$ 分别是 $X,Y$ 上的 $\sigma$-有限 Radon 测度，如果 $E\in \mathcal{B}_{X\times Y}$，那么函数 $x\mapsto \nu(E_{x})$ 和 $y\mapsto \mu(E^{y})$ 都是 Borel 可测的，并且

$$
\begin{gather}
\mu \otimes \nu(E)=\int \nu(E_{x})\mathrm{d} \mu(x)=\int \mu(E^{y})\mathrm{d} \nu(y)
\end{gather}
$$

此外，$\mu \otimes \nu$ 在 $\mathcal{B}_{X}\otimes \mathcal{B}_{Y}$ 上的限制等于 $\mu \times \nu$.

**证明**

固定开集 $U\subset X,V\subset Y$，其中 $\mu(U)$ 和 $\nu(V)$ 有限，令 $W=U\times V$，定义 $\mathcal{M}$ 由所有使得 $E\cap W$ 满足定理结论的 $E \in \mathcal{B}_{X\times Y}$ 构成，则我们有：

(i). $\mathcal{M}$ 包含所有开集：根据引理 29.4.7.

(ii). 如果 $E,F \in \mathcal{M}$ 且 $F\subset E$，那么 $E\setminus F\in \mathcal{M}$. 这是因为

$$
\begin{gather}
\mu \otimes \nu(E\cap W)=\mu \otimes \nu(F\cap W)+\mu \otimes \nu((E\setminus F)\cap W)
\end{gather}
$$

由于结论对 $E\cap W$ 和 $F\cap W$ 成立，并且这里涉及的集合都具有有限测度（这就是引入 $W$ 的原因），我们可以移项相减以得到关于 $E\setminus F$ 的结论。特别地，如果 $F\in \mathcal{M}$，那么 $F^{c}=X\setminus F \in \mathcal{M}$，即 $\mathcal{M}$ 关于补集封闭。

(iii). $\mathcal{M}$ 关于有限无交并封闭：根据测度的可加性。

(iv). $\mathcal{M}$ 关于可数递增并封闭：根据单调收敛定理，从而 $\mathcal{M}$ 关于可数递减交封闭。

现在令 $\mathcal{E}=\{ A\setminus B \mid A,B\subset X\times Y \text{是开集} \}$，我们有

$$
\begin{gather}
(A_{1}\setminus B_{1})\cap(A_{2}\setminus B_{2})=(A_{1}\cap A_{2})\setminus(B_{1}\cup B_{2}) \\
(A\setminus B)^{c}=((X\times Y)\setminus A)\cup((A\cap B)\setminus \varnothing)
\end{gather}
$$

因此 $\mathcal{E}$ 是一个基本族，从而 $\mathcal{E}$ 的元素的有限无交并构成的集族 $\mathcal{A}$ 是一个代数，根据单调类引理，其生成的单调类等于其生成的 $\sigma$-代数，即 $\mathcal{B}_{X\times Y}$. 而根据 (i)-(iv)，$\mathcal{M}$ 包含了该单调类（因为 $A\setminus B=A\setminus(A\cap B)$），从而 $\mathcal{M}=\mathcal{B}_{X\times Y}$.

接下来，由于 $\mu,\nu$ 是 $\sigma$-有限且外正则的，故可以选取开集 $(U_{n}),(V_{n})$ 使得 $X=\bigcup_{j=1}^{\infty}U_{j}$，$Y=\bigcup_{j=1}^{\infty}V_{j}$，并且 $U_{n},V_{n}$ 递增，且具有有限测度。如果 $E \in \mathcal{B}_{X\times Y}$，根据上面的论证，对任意 $n$，集合 $E\cap(U_{n}\times V_{n})$ 满足定理的结论，从而由单调收敛定理可知 $E$ 也满足定理的结论。

最后，如果 $E \in \mathcal{B}_{X}\otimes \mathcal{B}_{Y}$，根据 Fubini-Tonelli 定理，就有

$$
\begin{gather}
\mu \times \nu(E)=\int \nu(E_{x})\mathrm{d} \mu(x)=\mu \otimes \nu(E)
\end{gather}
$$

这就完成了证明。

**定理 29.4.9** Fubini-Tonelli 定理

设 $X,Y$ 是 LCH 空间，$\mu,\nu$ 分别是 $X,Y$ 上的 $\sigma$-有限 Radon 测度，$f$ 是 $X\times Y$ 上的 Borel 可测函数，则对任意 $x,y$，函数 $f_{x},f^{y}$ 是 Borel 可测的。如果 $f\geq 0$，那么 $x\mapsto \int f_{x}\mathrm{d}\nu$ 和 $y\mapsto \int f^{y}\mathrm{d}\mu$ 是 Borel 可测的；如果 $f \in L^{1}(\mu \otimes \nu)$，那么 $f_{x}\in L^{1}(\nu)$ 对 a.e. $x$ 成立，$f^{y}\in L^{1}(\mu)$ 对 a.e. $y$ 成立，并且 $x\mapsto \int f_{x}\mathrm{d}\nu$ 和 $y\mapsto \int f^{y}\mathrm{d}\mu$ 分别在 $L^{1}(\mu)$ 和 $L^{1}(\nu)$ 中。在两种情况下，都有

$$
\begin{gather}
\int f\mathrm{d} (\mu \otimes \nu)=\iint f\mathrm{d} \mu \mathrm{d} \nu=\iint f\mathrm{d} \nu \mathrm{d} \mu
\end{gather}
$$

**证明**

引理 29.4.5 给出了 $f_{x},f^{y}$ 的 Borel 可测性。剩下的证明与 22.2.8 完全相同，只不过是用定理 29.4.8 替换了引理 22.2.7 而已。

将 Radon 乘积推广到任意有限个 Radon 测度是非常显然的。更加有趣的是，这一理论可以扩展到任意多个（可数或不可数）测度的乘积，只要这里涉及的空间是紧致的，并且其测度归一化为 $1$，i.e.，是**概率空间**。

更准确地说，设 $\{ X_{\alpha} \}_{\alpha \in A}$ 是一族紧致 Hausdorff 空间，对任意 $\alpha$，$\mu_{\alpha}$ 是 $X_{\alpha}$ 上的 Radon 测度，满足 $\mu_{\alpha}(X_{\alpha})=1$. 令 $X=\prod_{\alpha}X_{\alpha}$ 是一个紧致 Hausdorff 空间（根据 Tychonoff 定理），我们可以在 $X$ 上定义一个 Radon 测度 $\mu$ 使得，当除了有限个 $E_{\alpha}\in \mathcal{B}_{X_{\alpha}}$ 外，其余的 $E_{\alpha}$ 都满足 $E_{\alpha}=X_{\alpha}$ 时，有

$$
\begin{gather}
\mu\left( \prod_{\alpha \in A} E_{\alpha} \right)=\prod_{\alpha \in A} \mu_{\alpha}(E_{\alpha})
\end{gather}
$$

这里右边的乘积是良定的：除了有限个 $E_{\alpha}$ 外，其余项都是 $1$. 这也是我们要求测度归一化的原因。

在证明之前我们给出一个记号：设 $\alpha_{1},\dots,\alpha_{n}\in A$，令 $\pi_{(\alpha_{1},\dots,\alpha_{n})}$ 表示从 $X$ 到 $\prod_{j=1}^{n}X_{\alpha_{j}}$ 的自然投影

$$
\begin{gather}
\pi_{(\alpha_{1},\dots,\alpha_{n})}(x)=(x_{\alpha_{1}},\dots,x_{\alpha_{n}})
\end{gather}
$$

则 $\pi_{(\alpha_{1},\dots,\alpha_{n})}^{-1}[E_{\alpha_{1}}\times\dots \times E_{\alpha_{n}}]=\prod_{\alpha \in A}E_{\alpha}$，其中对于 $\alpha\neq\alpha_{1},\dots,\alpha_{n}$ 有 $E_{\alpha}=X_{\alpha}$.

**定理 29.4.10**

假设对任意 $\alpha \in A$，$\mu_{\alpha}$ 是紧致 Hausdorff 空间 $X_{\alpha}$ 上的 Radon 测度，满足 $\mu_{\alpha}(X_{\alpha})=1$，那么在 $X=\prod_{\alpha \in A}X_{\alpha}$ 上存在唯一的 Radon 测度 $\mu$，使得对任意 $\alpha_{1},\dots,\alpha_{n}\in A$ 和 Borel 集 $E\subset \prod_{j=1}^{n}X_{\alpha_{j}}$，有

$$
\begin{gather}
\mu(\pi_{(\alpha_{1},\dots,\alpha_{n})}^{-1}[E])=(\mu_{\alpha_{1}}\otimes \dots \otimes \mu_{\alpha_{n}})(E)
\end{gather}
$$

**证明**

设 $C_{F}(X)$ 包含所有仅依赖于有限个坐标的函数 $f \in C(X)$，即所有具有形式 $f=g\circ \pi_{(\alpha_{1},\dots,\alpha_{n})}$，其中 $g \in C\left( \prod_{j=1}^{n}X_{\alpha_{j}} \right)$ 的函数. 如果 $f\in C_{F}(X)$，定义

$$
\begin{gather}
I(f)=\int g \mathrm{d} (\mu_{\alpha_{1}}\otimes \dots \otimes \mu_{\alpha_{n}})
\end{gather}
$$

增加更多的坐标 $\alpha$ 对上述等式没有影响，因为 $\mu_{\alpha}(X_{\alpha})=1$，因此 $I$ 是 $C_{F}(X)$ 上良定的一个正线性泛函，且 $|I(f)|\leq \lVert f \rVert_{u}$，当 $f$ 是常值函数时取等。

$C_{F}(X)$ 显然是一个分离点的代数，并且关于复共轭封闭，包含常值函数，因此根据 Stone-Weierstrass 定理，它在 $C(X)$ 中稠密，于是 $I$ 可以连续地扩展为 $C(X)$ 上的一个范数为 $1$ 的正线性泛函，从而应用 Riesz 表示定理可得 $X$ 上唯一的 Radon 测度 $\mu$，使得 $I(f)=\int f\mathrm{d}\mu$ 对 $f \in C_{F}(X)$ 成立。

给定 $\alpha_{1},\dots,\alpha_{n}\in A$，令 $\mu_{(\alpha_{1},\dots,\alpha_{n})}=\mu \circ \pi_{(\alpha_{1},\dots,\alpha_{n})}^{-1}$，则 $\mu_{(\alpha_{1},\dots,\alpha_{n})}$ 是 $\prod_{j=1}^{n}X_{\alpha_{j}}$ 上的一个有限 Borel 测度，满足

$$
\begin{gather}
\int g \mathrm{d} \mu_{(\alpha_{1},\dots,\alpha_{n})}=\int g\circ \pi_{(\alpha_{1},\dots,\alpha_{n})} \mathrm{d} \mu
\end{gather}
$$

对特征函数 $g$ 成立，从而根据线性性和单调收敛定理知上述等式对任意有界 Borel 可测函数成立。特别地，对任意 $g \in C\left( \prod_{j=1}^{n}X_{\alpha_{j}} \right)$ 有

$$
\begin{gather}
\int g\mathrm{d} \mu_{(\alpha_{1},\dots,\alpha_{n})}=\int g\mathrm{d} (\mu_{\alpha_{1}}\otimes \dots \otimes \mu_{\alpha_{n}})
\end{gather}
$$

如果我们可以证明 $\mu_{(\alpha_{1},\dots,\alpha_{n})}$ 是 Radon 测度，那么根据 Riesz 表示定理的唯一性部分，可得 $\mu_{(\alpha_{1},\dots,\alpha_{n})}=\mu_{\alpha_{1}}\otimes \dots \otimes \mu_{\alpha_{n}}$，这就是所要证的。

设 $E\subset \prod_{j=1}^{n}X_{\alpha_{j}}$ 是 Borel 集，记 $\pi=\pi_{(\alpha_{1},\dots,\alpha_{n})}$. 由于 $\mu$ 是正则的，对任意 $\varepsilon>0$ 存在紧致集 $K\subset \pi^{-1}[E]$ 使得 $\mu(K)>\mu(\pi^{-1}[E])-\varepsilon$，令 $K'=\pi(K)\subset E$ 是紧致集，则 $\mu_{(\alpha_{1},\dots,\alpha_{n})}(K')=\mu(\pi^{-1}[K'])\geq \mu(K)$，从而 $\mu_{(\alpha_{1},\dots,\alpha_{n})}(K')>\mu_{(\alpha_{1},\dots,\alpha_{n})}(E)-\varepsilon$，即证 $\mu_{(\alpha_{1},\dots,\alpha_{n})}$ 的内正则性。对 $E^{c}$ 应用同样的论证，即证 $\mu_{(\alpha_{1},\dots,\alpha_{n})}$ 的外正则性。因此 $\mu_{(\alpha_{1},\dots,\alpha_{n})}$ 是 Radon 测度，这就完成了证明。

上述定理有另外一个版本，它说的是如果 $\{ (X_{\alpha},\mathcal{M}_{\alpha},\mu_{\alpha}) \}_{\alpha \in A}$ 是一族概率空间（$\mu_{\alpha}(X_{\alpha})=1$），那么我们可以在 $\left( \prod_{\alpha \in A}X_{\alpha},\bigotimes_{\alpha \in A}\mathcal{M}_{\alpha} \right)$ 上构造一个乘积测度 $\prod_{\alpha \in A}\mu_{\alpha}$. 这正是概率论中独立随机变量的存在性定理，利用本质上相同的方法，我们也可以证明概率论中的一个基本结果：Kolmogorov 扩张定理（见专栏概率论第一章）。与之相对的是，我们的版本增加了紧致性的条件，但也给出了一个更强的结果：$\mu$ 的定义域是 $\mathcal{B}_{X}$，当指标集 $A$ 不可数时，它比 $\bigotimes_{\alpha \in A}\mathcal{B}_{X_{\alpha}}$ 要大得多。