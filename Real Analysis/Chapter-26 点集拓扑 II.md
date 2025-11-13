现在我们继续研究拓扑空间，本章我们将给出几个拓扑学中的基本定理，包括 Tychonoff 定理、Arzela-Ascoli 定理、Stone-Weierstrass 定理、Urysohn 度量化定理等。

# Section 1: 紧致性定理

正如我们之前所说，在函数空间中，紧致性是一个相当少见的性质。几乎所有的紧致性都来源于两个基本定理，即 Tychonoff 定理和 Arzela-Ascoli 定理。

首先我们来看 Tychonoff 定理，它与乘积集合的紧致性有关。回顾一下，一个 $x \in X=\prod_{\alpha \in A}X_{\alpha}$ 是一个从 $A$ 到 $\bigcup_{\alpha \in A}X_{\alpha}$ 的映射，它将 $\alpha \in A$ 映射到 $x_{\alpha} \in X_{\alpha}$，我们将其记作 $\pi_{\alpha}(x)$. 类似地，如果 $B\subset A$，那么 $\pi_{B}(x)$ 就是 $x$ 在 $B$ 上的限制（投影），并且我们把 $\pi_{\{ \alpha \}}(x)$ 与 $\pi_{\alpha}(x)$ 看作是一样的。如果 $p \in \prod_{\alpha \in B}X_{\alpha},q \in \prod_{\alpha \in C}X_{\alpha}$，我们称 $q$ 是 $p$ 的**扩张**，如果 $B\subset C$ 且对任意 $\alpha \in B$ 有 $p_{\alpha}=q_{\alpha}$.

**定理 26.1.1** Tychonoff 定理

设 $\{ X_{\alpha} \}_{\alpha \in A}$ 是一族紧致拓扑空间，则 $X=\prod_{\alpha \in A}X_{\alpha}$ 在乘积拓扑下是紧致的。

**证明**

我们只需证明 $X$ 中的任意网 $\langle x_{i} \rangle_{i \in I}$ 都有聚点。我们通过研究 $B\subset A$ 上的投影 $\langle \pi_{B}(x_{i}) \rangle$ 来证明这一点，设

$$
\begin{gather}
\mathcal{P}=\bigcup_{B\subset A} \left\{  p \in \prod_{\alpha \in B} X_{\alpha} \middle| p \text{是} \langle \pi_{B}(x_{i}) \rangle \text{的聚点}  \right\}
\end{gather}
$$

$\mathcal{P}$ 是非空的，因为 $X_{\alpha}$ 是紧致的，所以当 $B=\{ \alpha \}$ 时 $\langle \pi_{\alpha}(x_{i}) \rangle$ 有聚点。在 $\mathcal{P}$ 上定义关系 $\leq$ 如下：$p\leq q$ 如果 $q$ 是 $p$ 的扩张，则 $\leq$ 是 $\mathcal{P}$ 上的一个偏序。下面我们使用 Zorn 引理来说明 $\mathcal{P}$ 极大元的存在性。

设 $\{ p_{l} \mid l \in L \}$ 是 $\mathcal{P}$ 上的一个链，其中 $p_{l}\in \prod_{\alpha \in B_{l}}X_{\alpha}$，令 $B^{*}=\bigcup_{l \in L}B_{l}$，并且设 $p^{*}$ 是所有 $p_{l}$ 在 $\prod_{\alpha \in B^{*}}X_{\alpha}$ 上的唯一扩张，我们断言 $p^{*}\in \mathcal{P}$. 根据乘积拓扑的定义，$p^{*}$ 的任意邻域都包含集合 $\prod_{\alpha \in B^{*}}U_{\alpha}$，其中 $U_{\alpha}$ 是开集，并且除了有限个 $\alpha$ 外都有 $U_{\alpha}=X_{\alpha}$，这有限个 $\alpha_{j}$ 分别属于某个 $B_{j}$，根据全序性，它们都属于某个 $B_{l}$. 又因为 $\prod_{\alpha \in B_{l}}U_{\alpha}$ 是 $p_{l}$ 的一个邻域，因此 $\langle \pi_{B_{l}}(x_{i}) \rangle$ 在 $\prod_{\alpha \in B_{l}}U_{\alpha}$ 中经常出现，从而 $\langle \pi_{B^{*}}(x_{i}) \rangle$ 在 $\prod_{\alpha \in B^{*}}U_{\alpha}$ 中经常出现，即 $p^{*}$ 是 $\langle \pi_{B^{*}}(x_{i}) \rangle$ 的聚点，从而 $p^{*}$ 是 $\{ p_{l} \mid l \in L \}$ 的一个上界。

根据 Zorn 引理，$\mathcal{P}$ 有极大元 $\overline{p}\in \prod_{\alpha \in \overline{B}}X_{\alpha}$，我们断言 $\overline{B}=A$. 如果不然，取 $\gamma \in A\setminus \overline{B}$，由于 $\overline{p}$ 是一个聚点，故存在子网 $\langle \pi_{\overline{B}}(x_{i(j)}) \rangle_{j \in J}$ 收敛于 $\overline{p}$，又由于 $X_{\gamma}$ 是紧致的，故存在子网 $\langle \pi_{\gamma}(x_{i(j(k))}) \rangle_{k \in K}$ 收敛于 $p_{\gamma}\in X_{\gamma}$，设 $q$ 是 $\overline{p}$ 和 $p_{\gamma}$ 在 $\prod_{\alpha \in \overline{B}\cup \{ \gamma \}}X_{\alpha}$ 上的唯一扩张，则 $\langle \pi_{\overline{B}\cup \{ \gamma \}}(x_{i(j(k))}) \rangle$ 收敛于 $q$，这与 $\overline{p}$ 的极大性矛盾，因此 $\overline{p}$ 是 $\langle x_{i} \rangle$ 的聚点，这就完成了证明。

下面我们转到 Arzela-Ascoli 定理，它与连续函数空间中的紧致性有关，首先我们需要一些概念。

**定义 26.1.2** 完全有界的（totally bounded）

称度量空间 $(X,d)$ 是**完全有界的**，如果对任意 $\varepsilon>0$，存在有限个点 $x_{1},\dots,x_{n}$ 使得 $X=\bigcup_{j=1}^{n}B(x_{j},\varepsilon)$.

显然，完全有界性蕴含了有界性，并且完全有界集合的子集也是完全有界的。此外，完全有界性还是度量空间上的另一个紧致性判定方法。

**定理 26.1.3**

设 $(X,d)$ 是度量空间，则 $X$ 是紧致的当且仅当 $X$ 是完备且完全有界的。

**证明**

设 $X$ 是完备且完全有界的，$(x_{n})$ 是 $X$ 中的序列，根据完全有界性，存在有限个半径为 $2^{-1}$ 的开球覆盖 $X$，其中必然有一个包含了无限个 $x_{n}$，记作 $B_{1}$，这些点的指标集记作 $N_{1}$. 由于 $X\cap B_{1}$ 是完全有界的，故存在有限个半径为 $2^{-2}$ 的开球覆盖 $X\cap B_{1}$，其中必然有一个包含了无限个 $x_{n},n \in N_{1}$，记作 $B_{2}$，指标集记作 $N_{2}\subset N_{1}$. 以此类推，我们就得到了一列半径为 $2^{-j}$ 的开球 $B_{j}$ 和一列指标集 $N_{j}$ 使得对任意 $n \in N_{j}$ 有 $x_{n}\in B_{j}$，取 $n_{j}\in N_{j}$ 使得 $n_{1}<n_{2}<\cdots$，则当 $j<k$ 时有 $d(x_{n_{j}},x_{n_{k}})\leq 2^{1-j}$，因此 $(x_{n_{j}})$ 是一个 Cauchy 序列，由 $X$ 的完备性知其有极限。

如果 $X$ 不完备，那么存在 Cauchy 序列 $(x_{n})$ 没有极限，那么它没有收敛的子序列（否则整个序列将会收敛于同一个极限），因此 $X$ 不是紧致的。如果 $X$ 不是完全有界的，那么存在 $\varepsilon>0$ 使得 $X$ 不能被有限个开球覆盖，按以下方法取出没有收敛子序列的序列：首先取 $x_{1}\in X$，然后递归地取 $x_{n} \in X\setminus \bigcup_{j=1}^{n-1}B(x_{j},\varepsilon)$，则对任意 $m<n$ 有 $d(x_{m},x_{n})\geq\varepsilon$，因此 $(x_{n})$ 没有收敛的子序列，这就完成了证明。

根据 Heine-Borel 定理，我们就知道 $\mathbb{R}^{n}$ 上的有界集合是完全有界的。

**定义 26.1.4** 等度连续（equicontinuous）

设 $X$ 是拓扑空间，$Y$ 是度量空间，称函数族 $\mathcal{F}\subset C(X,Y)$ 在 $x \in X$ 处**等度连续**，如果对任意 $\varepsilon>0$，存在 $x$ 的邻域 $U$ 使得对任意 $f \in \mathcal{F}$ 和 $y \in U$ 有 $d_{Y}(f(y),f(x))<\varepsilon$；称 $\mathcal{F}$ 是**等度连续的**，如果 $\mathcal{F}$ 在任意点 $x \in X$ 处等度连续。

**定义 26.1.5** 逐点有界（pointwise bounded）

设 $X$ 是拓扑空间，$Y$ 是度量空间，称函数族 $\mathcal{F}\subset Y^{X}$ 是**逐点有界的**，如果对任意 $x \in X$，集合 $\{ f(x) \mid f \in \mathcal{F} \}$ 是有界的。类似地，称 $\mathcal{F}$ 是**逐点完全有界的**，如果对任意 $x \in X$，集合 $\{ f(x) \mid f \in \mathcal{F} \}$ 是完全有界的。

我们通常取 $Y=\mathbb{C}$，此时逐点有界和逐点完全有界就是等价的。

Arzela-Ascoli 定理有多个不同的变体，下面我们给出其中最有用的两个。

**定理 26.1.6** Arzela-Ascoli 定理 I

设 $X$ 是紧致 Hausdorff 空间，$Y$ 是完备度量空间，$\mathcal{F}\subset C(X,Y)$ 是等度连续且逐点完全有界的，则 $\mathcal{F}$ 在一致度量下是完全有界的，并且 $\overline{\mathcal{F}}$ 是紧致的。

**证明**

任取 $\varepsilon>0$，对任意 $x \in X$，存在邻域 $U_{x}$ 使得对任意 $y \in U_{x}$ 和 $f \in \mathcal{F}$ 有 $d_{Y}(f(y),f(x))< \varepsilon$. 由于 $X$ 是紧致的，故存在 $x_{1},\dots,x_{n}$ 使得 $\{ U_{x_{j}} \}_{j=1}^{n}$ 覆盖 $X$，再根据逐点完全有界性，$\{ f(x_{j}) \mid f \in \mathcal{F},1\leq j\leq n \}$ 是完全有界的，从而存在 $z_{1},\dots,z_{m}\in Y$ 使得 $\{ B(z_{k},\varepsilon) \}_{k=1}^{m}$ 覆盖 $\{ f(x_{j}) \}$. 令 $A=\{ x_{1},\dots,x_{n} \}$，$B=\{ z_{1},\dots,z_{m} \}$，则集合 $B^{A}$ 是有限的，并且定义

$$
\begin{gather}
\mathcal{F}_{\phi}=\{ f \in \mathcal{F} \mid d_{Y}(f(x_{j}),\phi(x_{j}))<\varepsilon,1\leq j\leq n \}, \phi \in B^{A}
\end{gather}
$$

则 $\mathcal{F}=\bigcup_{\phi \in B^{A}}\mathcal{F}_{\phi}$，并且当 $f,g \in \mathcal{F}_{\phi}$ 时，对任意 $j$，我们有

$$
\begin{gather}
d_{Y}(f(x_{j}),g(x_{j}))\leq d_{Y}(f(x_{j}),\phi(x_{j}))+d_{Y}(\phi(x_{j}),g(x_{j}))\leq 2\varepsilon
\end{gather}
$$

并且对任意 $x \in X$，存在 $j$ 使得 $x \in U_{x_{j}}$，因此有

$$
\begin{gather}
d_{Y}(f(x),g(x))\leq d_{Y}(f(x),f(x_{j}))+d_{Y}(f(x_{j}),g(x_{j}))+d_{Y}(g(x_{j}),g(x))\leq 4\varepsilon
\end{gather}
$$

从而 $\mathcal{F}$ 是完全有界的，于是 $\overline{\mathcal{F}}$ 是完全有界的（如果 $\mathcal{F}\subset \bigcup_{j=1}^{n}B(s_{j},\varepsilon)$，那么 $\overline{\mathcal{F}}\subset \bigcup_{j=1}^{n}B(s_{j},2\varepsilon)$），根据 $Y$ 的完备性知 $C(X,Y)$ 在一致度量下是完备的，故 $\overline{\mathcal{F}}$ 是紧致的。

根据 $\mathbb{R}^{n}$ 空间的性质，当 $Y=\mathbb{C}$ 或者更一般地，$Y=\mathbb{R}^{n}$ 时，上述定理的条件逐点完全有界可以弱化为逐点有界。

**定理 26.1.7** Arzela-Ascoli 定理 II

设 $X$ 是 $\sigma$-紧致的 LCH 空间，如果 $(f_{n})$ 是 $C(X)$ 中的一个等度连续且逐点有界的函数序列，那么存在 $f \in C(X)$ 和 $(f_{n})$ 的一个子序列，其在紧致集上一致收敛于 $f$.

**证明**

根据定理 25.5.13，存在预紧致的开集 $\{ U_{n} \}_{n=1}^{\infty}$ 使得 $\overline{U}_{n}\subset U_{n+1}$ 且 $X=\bigcup_{n=1}^{\infty}U_{n}$，根据 26.1.6，存在 $(f_{n})$ 的子序列在 $\overline{U}_{1}$ 上一致 Cauchy，记作 $(f_{j}^{(1)})_{j=1}^{\infty}$，下面递归地取 $(f_{j}^{(k-1)})$ 的子序列 $(f_{j}^{(k)})$ 使其在 $\overline{U}_{k}$ 上一致 Cauchy.

令 $g_{k}=f_{k}^{(k)}$，则 $(g_{k})$ 是 $(f_{n})$ 的子序列，并且除了前 $k-1$ 项外，$(g_{k})$ 是 $(f_{j}^{(k)})$ 的子序列，因此在每个 $\overline{U}_{k}$ 上一致 Cauchy，由 $\mathbb{C}$ 的完备性，我们可以令 $f=\lim_{ k \to \infty }g_{k}$，则 $f \in C(X)$，并且由定理 25.5.14 得 $(g_{k})$ 在紧致集上一致收敛于 $f$.

当然，上述定理可以被推广至 $f_{n}\in C(X,Y)$，其中 $Y$ 是完备度量空间，并且逐点有界性也要加强为逐点完全有界性。

# Section 2: Stone-Weierstrass 定理

本节中，我们将把 Weierstrass 逼近定理，即每个 $[a,b]$ 上的连续函数都是 $[a,b]$ 上的多项式的一致极限，推广到紧致 Hausdorff 空间上。本节中，$\mathbb{F}$ 表示 $\mathbb{R}$ 或者 $\mathbb{C}$.

**定义 26.2.1** 分离点（separate points）

称集合 $\mathcal{A}\subset C(X,\mathbb{F})$ 是**分离点的**，如果对任意 $x,y \in X,x\neq y$，存在 $f \in \mathcal{A}$ 使得 $f(x)\neq f(y)$.

**定义 26.2.2** 代数（algebra），格（lattice）

称 $\mathcal{A}\subset C(X,\mathbb{F})$ 是一个**代数**，如果 $\mathcal{A}$ 是 $\mathbb{F}$ 上的向量空间，并且当 $f,g \in \mathcal{A}$ 时有 $fg \in \mathcal{A}$. 称 $\mathcal{A}\subset C(X,\mathbb{R})$ 是一个**格**，如果当 $f,g \in \mathcal{A}$ 时有 $\max(f,g)\in \mathcal{A}$ 且 $\min(f,g)\in \mathcal{A}$.

换句话说，$\mathcal{A}$ 是一个代数如果它对代数运算（加法和乘法）封闭，$\mathcal{A}$ 是一个格如果它对格运算（最大和最小值）封闭。例如，$[a,b]$ 上的多项式构成的集合就是一个代数。

如果 $\mathcal{A}$ 是一个代数或一个格，那么在一致度量下 $\overline{\mathcal{A}}$ 也是代数或者格，因为代数运算和格运算都是连续的。

现在我们叙述实数上的 Stone-Weierstrass 定理。

**定理 26.2.3** Stone-Weierstrass 定理

设 $X$ 是紧致 Hausdorff 空间，如果 $\mathcal{A}\subset C(X,\mathbb{R})$ 是一个分离点的闭代数，那么 $\mathcal{A}=C(X,\mathbb{R})$ 或者 $\mathcal{A}=\{ f \in C(X,\mathbb{R}) \mid f(x_{0})=0 \},x_{0}\in X$，前者成立当且仅当 $\mathcal{A}$ 包含常值函数。

下面我们给出几个引理。

**引理 26.2.4**

在 $\mathbb{R}^{2}$ 上定义乘法：$(x_{1},y_{1})(x_{2},y_{2})=(x_{1}x_{2},y_{1}y_{2})$，则 $\mathbb{R}^{2}$ 是一个代数，并且 $\mathbb{R}^{2}$ 的子代数只有 $\{ (0,0) \}$，$\mathrm{span}((1,0))$，$\mathrm{span}((0,1))$，$\mathrm{span}((1,1))$，以及 $\mathbb{R}^{2}$.

**证明**

上面列出的这些集合显然都是 $\mathbb{R}^{2}$ 的子代数。设 $\mathcal{A}$ 是 $\mathbb{R}^{2}$ 的非零子代数，则存在 $(0,0)\neq (a,b) \in \mathcal{A}$，于是 $(a^{2},b^{2})\in \mathcal{A}$. 如果 $a\neq 0,b\neq 0,a\neq b$，那么 $(a,b),(a^{2},b^{2})$ 线性无关，于是 $\mathcal{A}=\mathbb{R}^{2}$. 类似地，如果 $a=b\neq 0$，那么 $\mathcal{A}=\mathrm{span}((1,1))$，如果 $a\neq 0,b=0$，那么 $\mathcal{A}=\mathrm{span}((1,0))$，反之同理。

**引理 26.2.5**

对任意 $\varepsilon>0$，存在 $\mathbb{R}$ 上的多项式 $P$ 使得 $P(0)=0$ 且对任意 $x \in[-1,1]$ 有 $||x|-P(x)|<\varepsilon$.

**证明**

由于 $|x|$ 是 $[-1,1]$ 上的连续函数，由 Weierstrass 逼近定理知存在多项式 $Q$ 使得对 $x \in[-1,1]$ 有 $||x|-Q(x)|<\varepsilon / 2$，特别地，$|Q(0)|<\varepsilon / 2$，令 $P(x)=Q(x)-Q(0)$，则 $P(0)=0$，且 $||x|-P(x)|<\varepsilon$.

**引理 26.2.6**

如果 $\mathcal{A}$ 是 $C(X,\mathbb{R})$ 的一个闭子代数，那么对任意 $f \in \mathcal{A}$ 都有 $|f| \in \mathcal{A}$，并且 $\mathcal{A}$ 是一个格。

**证明**

设 $f \in \mathcal{A},f\neq 0$，令 $h= \dfrac{f}{\lVert f \rVert_{\infty}}$，则 $h\colon X\to[-1,1]$，因此设 $\varepsilon>0$ 且多项式 $P$ 如引理 26.2.5 所示，则有 $\lVert |h|-P\circ h \rVert_{\infty}<\varepsilon$. 由于 $P(0)=0$，故 $P$ 不含有常数项，因此 $P\circ h \in \mathcal{A}$，由于 $\mathcal{A}$ 是闭的，因此 $|h| \in \mathcal{A}$，于是 $|f|=\lVert f \rVert_{\infty}|h| \in \mathcal{A}$. 第二个结论由以下等式直接推出：

$$
\begin{gather}
\max(f,g)= \dfrac{f+g+|f-g|}{2}, \min(f,g)= \dfrac{f+g-|f-g|}{2}
\end{gather}
$$

**引理 26.2.7**

设 $X$ 是紧致 Hausdorff 空间，$\mathcal{A}\subset C(X,\mathbb{R})$ 是一个闭格，$f \in C(X,\mathbb{R})$，如果对任意 $x,y \in X$，存在 $g_{xy}\in \mathcal{A}$ 使得 $g_{xy}(x)=f(x)$ 且 $g_{xy}(y)=f(y)$，那么 $f \in \mathcal{A}$.

**证明**

任取 $\varepsilon>0$，对任意 $x,y \in X$ 令 $U_{xy}=\{ z \mid f(z)<g_{xy}(z)+\varepsilon \}$，$V_{xy}=\{ z \mid f(z)>g_{xy}(z)-\varepsilon \}$，则 $U_{xy},V_{xy}$ 是开集并且包含 $x,y$. 固定 $y$，则 $\{ U_{xy} \mid x \in X \}$ 是 $X$ 的开覆盖，于是有有限子覆盖 $\{ U_{x_{j}y} \}_{j=1}^{n}$，设 $g_{y}=\max_{j} g_{x_{j}y}$，则在 $X$ 上有 $f<g_{y}+\varepsilon$，并且在 $V_{y}=\bigcap_{j=1}^{n}V_{x_{j}y}$ 上有 $f>g_{y}-\varepsilon$. 由于 $\{ V_{y} \}$ 也是 $X$ 的开覆盖，于是有有限覆盖 $\{ V_{y_{j}} \}_{j=1}^{m}$，令 $g=\min_{j}g_{y_{j}}$，则在 $X$ 上有 $|f-g|<\varepsilon$. 由于 $\mathcal{A}$ 是一个格，故 $g \in \mathcal{A}$，又由于 $\mathcal{A}$ 是闭的，因此 $f \in \mathcal{A}$.

现在我们就可以给出 Stone-Weierstrass 定理的证明了。

**证明**（26.2.3）

设 $x,y \in X,x\neq y$，令 $\mathcal{A}_{xy}=\{ (f(x),f(y)) \mid f \in \mathcal{A} \}$，则 $\mathcal{A}_{xy}$ 是引理 26.2.4 中 $\mathbb{R}^{2}$ 的一个子代数。如果对任意 $x,y$ 有 $\mathcal{A}_{xy}=\mathbb{R}^{2}$，那么根据引理 26.2.6 和 26.2.7 得 $\mathcal{A}=C(X,\mathbb{R})$.

如果存在 $x,y$ 使得 $\mathcal{A}_{xy}\neq \mathbb{R}^{2}$，因为 $\mathcal{A}$ 是分离点的，故 $\mathcal{A}_{xy}$ 不可能等于 $\{ (0,0) \}$ 或 $\mathrm{span}((1,1))$，因此 $\mathcal{A}_{xy}$ 必然是 $\mathrm{span}((1,0))$ 或 $\mathrm{span}((0,1))$，此时存在 $x_{0}$ 使得对任意 $f$ 有 $f(x_{0})=0$，并且该 $x_{0}$ 是唯一的，因此，如果 $x\neq x_{0},y\neq x_{0}$，那么 $\mathcal{A}_{xy}=\mathbb{R}^{2}$，从而 $\mathcal{A}=\{ f \in C(X,\mathbb{R}) \mid f(x_{0})=0 \}$. 最后，如果 $\mathcal{A}$ 包含常值函数，那么不存在 $x_{0}$ 使得对任意 $f$ 有 $f(x_{0})=0$，因此 $\mathcal{A}=C(X,\mathbb{R})$，这就完成了证明。

在上面的定理中，我们假设了 $\mathcal{A}$ 是一个闭代数，然而，通常情况下我们需要处理的是一个不是闭的代数 $\mathcal{B}$（例如多项式集合），此时我们需要将 Stone-Weierstrass 定理应用到其闭包 $\overline{\mathcal{B}}$ 上，该定理就变为：

**定理 26.2.8**

设 $X$ 是紧致 Hausdorff 空间，$\mathcal{B}\subset C(X,\mathbb{R})$ 是一个分离点的子代数，如果存在 $x_{0}\in X$ 使得对任意 $f \in \mathcal{B}$ 有 $f(x_{0})=0$，那么 $\overline{\mathcal{B}}=\{ f \in C(X,\mathbb{R}) \mid f(x_{0})=0 \}$，如果不然，那么就有 $\overline{\mathcal{B}}=C(X,\mathbb{R})$.

为了得到 $\mathbb{R}^{n}$ 上的 Weierstrass 逼近定理，我们把 $X$ 取为 $\mathbb{R}^{n}$ 上的一个紧致集，$\mathcal{B}=P(X,\mathbb{R})$ 为 $\mathbb{R}^{n}$ 上的多项式（限制在 $X$ 上），根据 26.2.8 就有 $\overline{P(X,\mathbb{R})}=C(X,\mathbb{R})$.

下面我们考虑复值函数的 Stone-Weierstrass 定理，一个显然的证明方法就是分别考虑 $f$ 的实部和虚部。然而，根据 $\mathrm{Re}\ f= \dfrac{f+\overline{f}}{2}$，即使 $f \in \mathcal{A}$，$\overline{f}$ 也不一定在 $\mathcal{A}$ 中。因此，我们需要对 $\mathcal{A}$ 做更强的约束，如下所示：

**定理 26.2.9** 复 Stone-Weierstrass 定理

设 $X$ 是紧致 Hausdorff 空间，$\mathcal{A}\subset C(X)$ 是分离点的闭代数，并且对复共轭封闭，那么 $\mathcal{A}=C(X)$ 或者 $\mathcal{A}=\{ f \in C(X) \mid f(x_{0})=0 \},x_{0} \in X$，前者成立当且仅当 $\mathcal{A}$ 包含常值函数。

**证明**

记由 $\mathcal{A}$ 中函数的实部和虚部构成的集合 $\mathcal{A}_{\mathbb{R}}$ 是 $C(X,\mathbb{R})$ 的一个子代数，应用定理 26.2.3，再根据 $\mathcal{A}=\{ f+ig \mid f,g \in \mathcal{A}_{\mathbb{R}} \}$ 就完成了证明。

在 LCH 空间上，同样有一个相应的 Stone-Weierstrass 定理，我们叙述并证明实值函数的情况，复值函数的情况是其自然推论。

**定理 26.2.10**

设 $X$ 是非紧致的 LCH 空间，$\mathcal{A}\subset C_{0}(X,\mathbb{R})$ 是一个分离点的闭代数，那么 $\mathcal{A}=C_{0}(X,\mathbb{R})$ 或者 $\mathcal{A}=\{ f \in C_{0}(X,\mathbb{R}) \mid f(x_{0})=0 \},x_{0}\in X$.

**证明**

如果存在 $x_{0}$ 使得对任意 $f \in \mathcal{A}$ 有 $f(x_{0})=0$，令 $Y=(X\setminus \{ x_{0} \})\cup \{ \infty \}$ 是 $X\setminus \{ x_{0} \}$ 的单点紧化，每个 $f \in \mathcal{A}$ 在 $X\setminus \{ x_{0} \}$ 上的限制都可以连续地扩张为 $\hat{f} \in C(Y,\mathbb{R})$，其中 $\hat{f}(\infty)=0$，所有这些 $\hat{f}$ 构成的闭代数记作 $\hat{\mathcal{A}}$.

由于 $\mathcal{A}$ 是分离点的，所以对任意 $x \in Y,x\neq \infty$，存在 $\hat{f}\in \hat{\mathcal{A}}$ 使得 $\hat{f}(x)\neq 0$，因此 $\hat{\mathcal{A}}$ 是分离点的。应用 Stone-Weierstrass 定理，则有 $\hat{\mathcal{A}}=\{ \hat{f} \in C(Y,\mathbb{R}) \mid \hat{f}(\infty)=0 \}$，因此 $\mathcal{A}=\{ f \in C_{0}(X,\mathbb{R}) \mid f(x_{0})=0 \}$.

如果不存在这样的 $x_{0}$，则令 $Y=X\cup \{ \infty \}$ 为 $X$ 的单点紧化，同理可得 $\hat{\mathcal{A}}=\{ \hat{f} \in C(Y,\mathbb{R}) \mid \hat{f}(\infty)=0 \}$，因此 $\mathcal{A}=C_{0}(X,\mathbb{R})$.

# Section 3: 立方体中的嵌入

本节我们给出一种将拓扑空间嵌入 $[0,1]^{A}$ 中的方法，并给出一些应用。本节中我们用 $I$ 来表示 $[0,1]$，如果 $A\neq \varnothing$，则称 $I^{A}$ 是一个**立方体**。根据 Tychonoff 定理，$I^{A}$ 是紧致的。

**定义 26.3.1** 分离点和闭集（separate points and closed sets）

设 $X$ 是拓扑空间，称 $\mathcal{F}\subset C(X,I)$ **分离点和闭集**，如果对任意闭集 $E\subset X$ 和 $x \in E^{c}$，存在 $f \in \mathcal{F}$ 使得 $f(x)\not\in \overline{f[E]}$.

如果 $\mathcal{F}$ 分离点和闭集，那么存在另一个函数族 $\mathcal{G}$ 满足一个更强的性质：对任意闭集 $E$ 和 $x \in E^{c}$ 有 $g \in \mathcal{G}$ 使得 $g(x)=1,g|_{E}=0$，我们只需取 $g=\phi \circ f$，其中 $\phi \in C(I,I)$ 满足 $\phi(f(x))=1,\phi|_{\overline{f[E]}}=0$ 即可。这就表明一个 $T_{1}$ 空间 $X$ 有分离点和闭集的函数族 $\mathcal{F}$ 当且仅当 $X$ 是完全正则的。

每个非空的 $\mathcal{F}\subset C(X,I)$ 都诱导了函数 $e\colon X\to I^{\mathcal{F}}$ 满足 $\pi_{f}\circ e=f$，其中 $\pi_{f}\colon I^{\mathcal{F}}\to I$ 是投影映射。我们称 $e$ 是与 $\mathcal{F}$ 相关的映射。

**定理 26.3.2**

设 $X$ 是拓扑空间，$\mathcal{F}\subset C(X,I)$，$e\colon X\to I^{\mathcal{F}}$ 是与 $\mathcal{F}$ 相关的映射，则：

1. $e$ 是连续的。
2. 如果 $\mathcal{F}$ 分离点，那么 $e$ 是单射。
3. 如果 $X$ 是 $T_{1}$ 空间并且 $\mathcal{F}$ 分离点和闭集，那么 $e$ 是一个嵌入。

**证明**

每个 $\pi_{f}\circ e=f$ 是连续的，根据定理 25.2.6，$e$ 是连续的。如果 $\mathcal{F}$ 分离点，假设存在 $x\neq y$ 使得 $e(x)=e(y)$，则对任意 $f \in \mathcal{F}$ 有 $f(x)=f(y)$，矛盾，因此 $e$ 是单射。

如果 $X$ 是 $T_{1}$ 空间且 $\mathcal{F}$ 分离点和闭集，根据 25.1.12 知 $\{ x \}$ 是闭集，因此 $\mathcal{F}$ 也是分离点的，从而 $e$ 是连续的单射。为证明 $e^{-1}$ 的连续性，设 $U\subset X$ 是开集，$x \in U$，取 $f \in \mathcal{F}$ 使得 $f(x)\not\in \overline{f[U^{c}]}$，令

$$
\begin{gather}
V=\pi_{f}^{-1}\left[\overline{f[U^{c}]}\right]^{c}=\{ p \in I^{\mathcal{F}} \mid \pi_{f}(p) \not\in \overline{f[U^{c}]} \}
\end{gather}
$$

则 $V\subset I^{\mathcal{F}}$ 是开集，并且 $e(x) \in V\cap e[X]\subset e[U]$，因此对任意 $x \in U$，$e[U]$ 是 $e(x)$ 的一个邻域，于是 $e[U]$ 是一个开集，即 $e^{-1}$ 是连续的。

由上述定理，我们可以得到推论：

**定理 26.3.3**

任意紧致 Hausdorff 空间都同胚于一个立方体的闭子集。

**证明**

根据 25.4.6，紧致 Hausdorff 空间是正规的，从而是完全正则的，取 $\mathcal{F}=C(X,I)$ 即可。

**定理 26.3.4**

拓扑空间 $X$ 是完全正则的当且仅当 $X$ 同胚于一个紧致 Hausdorff 空间的子集。

**证明**

完全正则性推出后者是显然的。下面我们要证一个完全正则空间的子集在相对拓扑下是完全正则的。

设 $Y$ 是完全正则空间，$A\subset Y$，设 $E$ 在 $A$ 中是闭集，$x \in A\setminus E$，则存在闭集 $F\subset Y$ 使得 $E=A\cap F$，于是 $x \in A\setminus F$，从而存在 $f \in C(Y,I)$ 使得 $f(x)=1$ 且 $f|_{F}=0$，于是 $f|_{E}=0$ 且 $f \in C(A,I)$，这表明 $A$ 是完全正则的。由于 $X$ 同胚于一个完全正则空间，故 $X$ 也是完全正则的。

定理 26.3.2 中的映射 $e$ 给出了一种使拓扑空间紧致化的方法，首先我们给出紧化的定义：

**定义 26.3.5** 紧化（compactification）

拓扑空间 $X$ 的一个**紧化**是二元组 $(Y,\phi)$，其中 $Y$ 是一个紧致 Hausdorff 空间，$\phi$ 是 $X$ 到 $Y$ 的一个稠密子集的同胚。

通常，我们会把 $X$ 和 $\phi[X]$ 等同起来，并称 $Y$ 是 $X$ 的一个紧化。例如，单点紧化 $X^{*}$ 就是 LCH 空间 $X$ 的一个紧化，其中 $\phi=i$ 是包含映射。

设 $X$ 是一个完全正则空间，根据定理 26.3.2，如果 $\mathcal{F}\subset C(X,I)$ 分离点和闭集，与之相关的嵌入为 $e\colon X\to I^{\mathcal{F}}$，并且 $Y$ 是 $e[X]$ 的闭包，那么 $(Y,e)$ 就是 $X$ 的一个紧化。如果我们将 $X$ 等同于 $e[X]$，那么 $f \in \mathcal{F}$ 就等同于 $\pi_{f}|_{e[X]}$，由于 $e[X]$ 在 $Y$ 中稠密，通过取极限，我们可以连续地将 $\pi_{f}|_{e[X]}$ 扩张到 $Y$ 上，从而 $f \in \mathcal{F}$ 可以连续地扩张到 $Y$ 上。

此外，如果 $f,g \in C_{b}(X)$ 可以连续地扩张到 $Y$ 上，那么 $f+g,fg$ 也可以连续地扩张到 $Y$ 上，并且如果 $(f_{n})$ 是一列一致收敛的有界连续函数，它们可以连续扩张，那么 $f=\lim_{ n \to \infty }f_{n}$ 也可以连续扩张。总结一下上述讨论，我们就有：

**定理 26.3.6**

设 $X$ 是完全正则空间，$\mathcal{F}\subset C(X,I)$ 分离点和闭集，令 $(Y,e)$ 是与 $\mathcal{F}$ 相关的 $X$ 的紧化，$\mathcal{A}\subset C_{b}(X)$ 是包含 $\mathcal{F}$ 的最小的闭子代数，那么每个 $f \in \mathcal{A}$ 都可以连续地扩张到 $Y$ 上。

设 $X$ 是一个完全正则空间，与 $\mathcal{F}=C(X,I)$ 相关的 $X$ 的紧化称为 **Stone-Cech 紧化**，记作 $(\beta X,e)$. 根据 26.3.6，每个 $f \in C_{b}(X)$ 都可以连续扩张到 $\beta X$ 上（如果我们把 $X$ 等同于 $e[X]$）。事实上，我们有一个更强的结论成立：

**定理 26.3.7**

设 $X$ 是完全正则空间，$Y$ 是紧致 Hausdorff 空间，$\phi \in C(X,Y)$，则 $\phi$ 有在 $\beta X$ 上的唯一连续扩张（即存在唯一的 $\tilde{\phi} \in C(\beta X,Y)$ 使得 $\tilde{\phi}\circ e=\phi$）。如果 $(Y,\phi)$ 是 $X$ 的一个紧化，那么 $\tilde{\phi}$ 是一个满射，如果又有每个 $f \in C_{b}(X)$ 都可以连续扩张至 $Y$ 上（即存在 $g \in C(Y)$ 使得 $f=g\circ \phi$），那么 $\tilde{\phi}$ 是一个同胚。

**证明**

令 $\mathcal{F}=C(X,I),\mathcal{G}=C(Y,I)$，$(\beta Y,i)$ 是 $Y$ 的 Stone-Cech 紧化。给定 $\phi \in C(X,Y)$，定义 $\Phi\colon I^{\mathcal{F}}\to I^{\mathcal{G}}$ 为 $\pi_{g}(\Phi(p))=\pi_{g\circ \phi}(p)$，于是 $\Phi$ 是连续的，并且对任意 $x \in X$ 有

$$
\begin{gather}
\pi_{g}(\Phi(e(x)))=\pi_{g\circ \phi}(e(x))=g(\phi(x))=\pi_{g}(i(\phi(x)))
\end{gather}
$$

因此 $\Phi \circ e=i\circ \phi$，于是 $(\Phi \circ e)[X]=(i\circ \phi)[X]\subset\beta Y$，从而 $\Phi[\beta X]\subset  \overline{\beta Y}=\beta Y$，因此我们有下图交换：

![](Real%20Analysis/images/5.png)

令 $\tilde{\phi}=i^{-1}\circ(\Phi|_{\beta X})$，则 $\tilde{\phi}\circ e=i^{-1}\circ \Phi \circ e=\phi$，由于 $e[X]$ 在 $\beta X$ 中稠密，因此根据 $\tilde{\phi}$ 的连续性，它是唯一的。如果 $(Y,\phi)$ 是 $X$ 的紧化，那么 $\phi[X]$ 在 $Y$ 中是稠密的，从而 $\tilde{\phi}[\beta X]$ 在 $Y$ 中也是稠密的，再根据 $\tilde{\phi}[\beta X]$ 的紧致性得 $\tilde{\phi}[\beta X]=Y$. 最后，如果对每个 $f \in C_{b}(X)$ 都存在 $g \in C(Y)$ 使得 $f=g\circ \phi$，则 $\Phi$ 是单射，从而 $\tilde{\phi}$ 是双射，根据定理 25.4.9，$\tilde{\phi}$ 是一个同胚。

这一定理表明，$\beta X$ 是完全正则空间 $X$ 的“最大的”紧化。另一边，LCH 空间的单点紧化 $X^{*}$ 是 $X$ 的“最小的”紧化，它和对应于 $\mathcal{F}=C_{c}(X,I)$ 的紧化同胚。

最后，我们再给出一个应用，它回答了这样一个问题：在什么时候，一个拓扑是由一个度量所诱导的？一个必要条件为 $X$ 是正规的（25.1.13），另一方面，我们有：

**定理 26.3.8** Urysohn 度量化定理（Urysohn metrization theorem）

任意第二可数的正则空间是可度量化的。

我们给出几个引理。

**引理 26.3.9**

第二可数的正则空间是正规的。

**证明**

设 $\mathcal{B}$ 是 $X$ 的一个可数基，$A,B\subset X$ 是不相交的闭集。对任意 $a \in A$，根据正则性，存在不相交的开集 $E_{a},F_{a}$ 使得 $a \in E_{a},B\subset F_{a}$，则有 $U_{a} \in \mathcal{B}$ 使得 $a \in U_{a}\subset E_{a}$，并且 $\overline{U}_{a}\cap B=\varnothing$. 令 $\mathcal{B}_{A}=\{ U \in \mathcal{B} \mid \overline{U}\cap B=\varnothing \}$，类似地，令 $\mathcal{B}_{B}=\{ V \in \mathcal{B} \mid \overline{V}\cap A=\varnothing \}$，则 $\mathcal{B}_{A}$ 覆盖了 $A$，$\mathcal{B}_{B}$ 覆盖了 $B$.

由于 $\mathcal{B}$ 是可数的，则可取 $\mathcal{B}_{A}=\{ U_{n} \}_{n=1}^{\infty},\mathcal{B}_{B}=\{ V_{n} \}_{n=1}^{\infty}$，令

$$
\begin{gather}
U=\bigcup_{n=1}^{\infty} \left( U_{n} \setminus \bigcup_{j=1}^{n} \overline{V}_{j} \right) \\
V=\bigcup_{n=1}^{\infty} \left( V_{n} \setminus \bigcup_{j=1}^{n} \overline{U}_{j} \right)
\end{gather}
$$

则 $U,V$ 是开集。设 $a \in A$，则 $a$ 属于某个 $U_{n}$，并且不属于任何一个 $\overline{V}_{j}$，从而 $A\subset U$，同理，$B\subset V$. 假设存在 $x \in U\cap V$，则存在 $m,n$ 使得 $x \in U_{n}\setminus \bigcup_{j=1}^{n}\overline{V}_{j}$ 且 $x \in V_{m}\setminus \bigcup_{j=1}^{m}\overline{U}_{j}$，不妨设 $m\leq n$，则由前式得 $x \not\in \overline{V}_{m}$，而由后式得 $x \in V_{m}$，矛盾，因此 $U\cap V=\varnothing$. 这就完成了证明。

**引理 26.3.10**

如果 $X$ 是第二可数且正规的，那么存在可数集 $\mathcal{F}\subset C(X,I)$ 分离点和闭集。

**证明**

设 $\mathcal{B}$ 是 $X$ 的一个可数基，考虑可数集合

$$
\begin{gather}
\mathcal{A}=\{ (U,V) \in \mathcal{B}^{2} \mid \overline{U}\subset V \}
\end{gather}
$$

根据 Urysohn 引理，对每个 $(U,V)\in \mathcal{A}$，存在 $f \in C(X,I)$ 使得 $f|_{\overline{U}}=1$ 且 $f|_{V^{c}}=0$，所有这些 $f$ 构成的集合记作 $\mathcal{F}$，下面我们证明 $\mathcal{F}$ 分离点和闭集。

设 $A\subset X$ 是闭集，$x \not\in A$，那么存在不相交的开集 $E,F$ 使得 $x \in E$ 且 $A\subset F$，根据基的性质，存在 $V \in \mathcal{B}$ 使得 $x \in V\subset E$，再次利用正规性，存在开集 $W$ 使得 $x \in W\subset \overline{W}\subset V$，于是有 $U \in \mathcal{B}$ 使得

$$
\begin{gather}
x \in U\subset \overline{U}\subset \overline{W}\subset V\subset F^{c}
\end{gather}
$$

从而存在 $f \in \mathcal{F}$ 使得 $f|_{\overline{U}}=1,f|_{V^{c}}=0$，而 $A\subset V^{c}$，故 $f|_{A}=0$，这就完成了证明。

**引理 26.3.11**

设 $(X,d)$ 是度量空间，则定义为 $\rho= \dfrac{d}{d+1}$ 的函数 $\rho\colon X^{2}\to[0,1)$ 是 $X$ 上的一个度量，并且 $\rho$ 和 $d$ 在 $X$ 上生成了相同的拓扑。

**证明**

$\rho$ 的正定性和对称性是显然的，设 $x,y,z \in X$，$a=d(x,z)$，$b=d(z,y)$，$c=d(x,y)$，则有 $c\leq a+b$，于是

$$
\begin{align}
\rho(x,z)+\rho(z,y)-\rho(x,y) &= \dfrac{a}{a+1}+ \dfrac{b}{b+1}- \dfrac{c}{c+1} \\
&= \dfrac{a+b-c+2ab+abc}{(a+1)(b+1)(c+1)} \\
&\geq 0
\end{align}
$$

因此 $\rho$ 是一个度量。

设 $x,y \in X,r>0$，则 $d(x,y)<r$ 当且仅当 $\rho(x,y)< \dfrac{r}{r+1}$，因此每个 $d$-开球都是一个 $\rho$-开球，反之亦然，由于开球是度量生成的拓扑的一个基，故 $d$ 和 $\rho$ 在 $X$ 上生成了相同的拓扑。

**引理 26.3.12**

设 $\{ (X_{n},\rho_{n}) \}_{n=1}^{\infty}$ 是一族度量空间，其中度量 $\rho_{n}\colon X_{n}^{2}\to[0,1)$ 如引理 26.3.11 所示，令 $X=\prod_{n=1}^{\infty}X_{n}$，则 $X$ 上的函数

$$
\begin{gather}
\rho(x,y)=\sum_{n=1}^{\infty} 2^{-n} \rho_{n}(x_{n},y_{n})
\end{gather}
$$

是一个度量，并且其生成的拓扑为乘积拓扑。

**证明**

由于 $2^{-n} \rho_{n}(x_{n},y_{n})\leq 2^{-n}$，故级数 $\sum_{n=1}^{\infty}2^{-n}\rho_{n}(x_{n},y_{n})$ 绝对收敛，从而我们可以证明 $\rho$ 是一个度量。

设 $\prod_{n=1}^{\infty}U_{n}$ 是乘积拓扑中的一个开集，即除了有限个项 $U_{n_{1}},\dots,U_{n_{k}}$ 外都有 $U_{n}=X_{n}$. 对于 $X_{n_{j}}$ 中的开集 $U_{n_{j}}$，存在开球 $B_{n_{j}}(x_{n_{j}},r_{n_{j}})\subset U_{n_{j}}$，对于其它 $X_{n}$，任取 $x_{n}\in X_{n}$. 令 $x=(x_{1},x_{2},\dots)$，$r=\min_{j} 2^{-n_{j}} r_{n_{j}}$，考虑开球

$$
\begin{gather}
B(x,r)=\{ y \in X \mid \rho(x,y)<r \}
\end{gather}
$$

设 $y \in B(x,r)$，则对于 $n_{j}$ 有 $2^{-n_{j}}\rho_{n_{j}}(x_{n_{j}},y_{n_{j}})<r\leq 2^{-n_{j}}r_{n_{j}}$，即 $y_{n_{j}}\in B_{n_{j}}(x_{n_{j}},r_{n_{j}})$，因此 $B(x,r)\subset \prod_{n=1}^{\infty}U_{n}$，即 $\prod_{n=1}^{\infty}U_{n}$ 在度量拓扑中是开集。

设 $B(x,r)$ 是度量拓扑中的开球，定义函数 $f_{n}\colon X\to[0,1)$ 为

$$
\begin{gather}
f_{n}(y)=\rho_{n}(x_{n},y_{n})
\end{gather}
$$

由于 $f_{n}=\rho_{n}(x_{n},\cdot)\circ \pi_{n}$，在乘积拓扑下 $\pi_{n}$ 是连续的，度量函数 $\rho_{n}$ 也是连续的，故 $f_{n}$ 是连续的。定义

$$
\begin{gather}
F(y)=\sum_{n=1}^{\infty} 2^{-n}f_{n}(y)=\sum_{n=1}^{\infty} 2^{-n} \rho_{n}(x_{n},y_{n})
\end{gather}
$$

则级数一致且绝对收敛，从而 $F$ 是连续的，于是 $B(x,r)=F^{-1}[(-\infty,r)]$ 在乘积拓扑中是开集。因此 $\rho$ 生成的拓扑是乘积拓扑。

结合上面的引理，我们就到达了本节的目标：

**证明**（26.3.8）

引理 26.3.9 表明 $X$ 是正规的，再根据引理 26.3.10，则存在可数集 $\mathcal{F}\subset C(X,I)$ 分离点和闭集，从而由引理 26.3.12，$I^{\mathcal{F}}$ 是可度量化的。利用定理 26.3.2 将 $X$ 嵌入 $I^{\mathcal{F}}$，将 $I^{\mathcal{F}}$ 上的度量限制在 $e[X]^{2}$ 上即证。