在上一章中，我们讨论了多元微分学，现在我们自然要讨论多元积分的相关问题。我们想要知道，对于 $\mathbb{R}^{n}$ 的某个子集 $\Omega$ 和函数 $f\colon \Omega\to \mathbb{R}$，如何求 $f$ 在 $\Omega$ 上的积分，从而得到一个数 $\int_{\Omega}f$，只有回答了这个问题，我们才能进一步去求复值函数以及向量值函数的积分：设 $f=(f_{1},\dots,f_{m})$，那么我们可以定义 $\int_{\Omega}f=\left( \int_{\Omega}f_{1},\dots,\int_{\Omega}f_{m} \right)$.

对于一维的情形，我们建立了 Riemann 积分的概念，这就回答了当 $\Omega=[a,b]$ 时的积分问题。Riemann 积分可以推广至更高维，然而，这需要我们付出更多的努力，但是其收益却不大：Riemann 可积的函数并不多，例如 Riemann 可积函数序列的逐点极限不一定是 Riemann 可积的，$L^{2}$ 极限也不一定是 Riemann 可积的，这对于我们的一些研究（特别是 Fourier 级数的研究）来说是不够的。

因此，我们就需要找到一种真正令人满意的积分概念，即 **Lebesgue 积分**。它可以处理很大一类函数，甚至我们可以说，所有在实际应用中遇到的函数都可以使用 Lebesgue 积分来处理（一些不可积的函数通常是用选择公理构造的，因此不会出现在实际生活中）。

然而，在此之前，我们先考虑一个更基本的问题：如何求 $\Omega$ 的长度、面积或者体积？这个问题之所以重要是因为 Riemann 积分就是用区间的长度来定义的，然而，在高维空间，$\Omega$ 的形状并不像区间那样规范，因此，我们首先就要考虑如何为 $\Omega$ 赋予一个值 $m(\Omega)$，称为它的长度、面积或体积，统称为 $\Omega$ 的**测度**。

在理想情况下，我们可以为每个 $\Omega \in \mathscr{P}(\mathbb{R}^{n})$ 赋予一个非负的实数 $m(\Omega)$，并且 $m$ 应当满足一些显而易见的性质，例如：

- 可数可加性：设 $(E_{n})_{n=0}^{\infty}$ 是两两不交的集合序列，那么应该有
$$
m\left( \bigcup_{n=0}^{\infty}E_{n} \right)=\sum_{n=0}^{\infty} m(E_{n})
$$
- 如果 $E$ 可以通过平移、旋转、反射变换到 $F$，那么 $m(E)=m(F)$
- 单位立方体 $[0,1]^{n}$ 的测度应当等于 $1$

然而，事实上这样的函数 $m$ 根本就不存在。一个例子是 Banach-Tarski 悖论，它显示了 $\mathbb{R}^{3}$ 中的一个球可以通过分割成五个不交的部分，然后分别对其做平移和旋转，最后组合起来可以变成两个球，即 $m(B)=2m(B)$，然而 $m(B)$ 显然是不为 $0$ 的，因此这样的测度 $m$ 的存在性是矛盾的。

这样的悖论表明，我们不可能为 $\mathbb{R}^{n}$ 的每个子集赋予测度，而只能退而求其次，只对那些不会引发矛盾的集合，即**可测集**赋予测度。幸运的是，我们在生活中遇到的集合几乎都是可测的，比如所有的开集和闭集，这对于分析学的研究已经足够好了。

# Section 1: $\sigma$-代数

回看一下我们认为测度应该满足的三个性质，其中后两个性质是与 Euclidean 空间直接关联的，然而，对于满足第一个性质（可数可加性）的函数也出现在数学的其它领域中，例如概率论中，概率函数 $P$ 也满足可数可加性。因此，我们首先来讨论广义的测度函数，从而能够将更多的对象包括进去，为了定义测度，我们还要明确可测集的结构，即 $\sigma$**-代数**。

**定义 20.1.1** 代数（algebra），$\sigma$-代数（$\sigma$-algebra）

集合 $X$ 上的一个**代数**是 $X$ 的子集族 $\mathcal{A}\subset \mathscr{P}(X)$ 满足：

1. $\varnothing \in \mathcal{A}$
2. 如果 $E_{1},\dots,E_{n}$ 满足每个 $E_{j}\in \mathcal{A}$，那么 $E_{1}\cup\dots \cup E_{n} \in \mathcal{A}$
3. 如果 $E\in \mathcal{A}$，那么 $X\setminus E\in \mathcal{A}$

$X$ 上的一个代数 $\mathcal{A}$ 是一个 $\sigma$**-代数**或者 $\sigma$**-域**如果进一步有：

- 如果 $(E_{n})_{n=0}^{\infty}$ 满足每个 $E_{j}\in \mathcal{A}$，那么 $\bigcup_{n=0}^{\infty}E_{n}\in \mathcal{A}$

根据 De Morgan 律，由于 $X\setminus \bigcup_{n=0}^{\infty}E_{n}=\bigcap_{n=0}^{\infty}(X\setminus E_{n})$，故 $\sigma$-代数也包含可数个集合的交集。一些 $\sigma$-代数的例子包括 $\mathscr{P}(X),\{ \varnothing,X \}$ 等。

下面的定义让我们可以构造非平凡的 $\sigma$-代数。

**定义 20.1.2** 生成（generate）

设 $X$ 是一个集合，$\mathcal{E}\subset \mathscr{P}(X)$，则由 $\mathcal{E}$ **生成**的 $\sigma$-代数定义为

$$
\mathcal{M}(\mathcal{E})=\bigcap \{ \mathcal{A} \mid \mathcal{E}\subset \mathcal{A},\mathcal{A} \text{是} \sigma \text{-代数} \}
$$

显然，$\mathcal{M}(\mathcal{E})$ 是一个 $\sigma$-代数，并且我们有以下的有用结论：

**引理 20.1.3**

设 $X$ 是一个集合，$\mathcal{E},\mathcal{F}\subset \mathscr{P}(X)$，如果 $\mathcal{E}\subset \mathcal{M}(\mathcal{F})$，那么 $\mathcal{M}(\mathcal{E})\subset \mathcal{M}(\mathcal{F})$.

**证明**

$\mathcal{M}(\mathcal{F})$ 是一个包含 $\mathcal{E}$ 的 $\sigma$-代数，根据定义就有 $\mathcal{M}(\mathcal{E})\subset \mathcal{M}(\mathcal{F})$.

设 $X$ 是一个度量空间（或者更一般地，是一个拓扑空间），我们称由 $X$ 中的开集生成的 $\sigma$ 代数为 **Borel** $\sigma$**-代数**，记作 $\mathcal{B}_{X}$，其元素称为 **Borel 集**。因此，$\mathcal{B}_{X}$ 包含 $X$ 的所有开集、闭集、开集的可数交、闭集的可数并等等。

对于类似于”开集的可数交“这样的表述，我们有一个标准术语。我们称一个集合是 $G_{\delta}$ 集，如果它是可数个开集的交；称一个集合是 $F_{\sigma}$ 集，如果它是可数个闭集的并；可数个 $G_{\delta}$ 集的并称为 $G_{\delta\sigma}$ 集；可数个 $F_{\sigma}$ 集的交称为 $F_{\sigma\delta}$ 集，以此类推。

$\mathbb{R}$ 上的 Borel $\sigma$-代数 $\mathcal{B}_{\mathbb{R}}$ 将是我们研究的重点，它有以下结论：

**定理 20.1.4**

$\mathcal{B}_{\mathbb{R}}$ 可以由以下集合生成：

1. 开区间：$\mathcal{E}_{1}=\{ (a,b) \mid a<b \}$
2. 闭区间：$\mathcal{E}_{2}=\{ [a,b] \mid a<b \}$
3. 半开区间：$\mathcal{E}_{3}=\{ (a,b] \mid a<b \},\mathcal{E}_{4}=\{ [a,b) \mid a<b \}$
4. 开射线：$\mathcal{E}_{5}=\{ (a,+\infty) \mid a \in \mathbb{R} \},\mathcal{E}_{6}=\{ (-\infty,a) \mid a \in \mathbb{R} \}$
5. 闭射线：$\mathcal{E}_{7}=\{ [a,+\infty) \mid a \in \mathbb{R} \},\mathcal{E}_{8}=\{ (-\infty,a] \mid a \in \mathbb{R} \}$

在证明之前，我们需要一个引理：

**引理 20.1.5**

$\mathbb{R}$ 上的每个开集都是至多可数个不相交的开区间的并。

**证明**

空集是平凡的。设 $V\subset \mathbb{R}$ 是非空开集，$x \in V$，则存在开区间 $I_{x}$ 使得 $x \in I_{x}\subset V$，将所有这样的 $I_{x}$ 构成的集合记作 $\mathcal{J}_{x}$，那么 $J_{x}=\bigcup \mathcal{J}_{x}$ 也是一个开区间。

设 $x,y \in V$，那么或者 $J_{x}=J_{y}$，或者 $J_{x}\cap J_{y}=\varnothing$，因为否则 $J_{x}\cup J_{y}$ 将包含 $J_{x}$，这与 $J_{x}=\bigcup \mathcal{J}_{x}$ 矛盾。因此，$\mathcal{K}=\{ J_{x} \mid x \in V \}$ 中的元素都不相交，并且 $V=\bigcup \mathcal{K}$.

定义 $f\colon \mathcal{K}\to \mathbb{Q}$ 如下：设 $J \in \mathcal{K}$，取有理数 $q \in J$，令 $f(J)=q$，则 $f$ 是 $\mathcal{K}$ 到 $\mathbb{Q}$ 的单射，因此 $\mathcal{K}$ 是至多可数的，即证。

**证明**（20.1.4）

$\mathcal{E}_{j},j\neq 3,4$ 中的集合都是开集或闭集，而 $\mathcal{E}_{3},\mathcal{E}_{4}$ 中的集合是 $G_{\delta}$ 集：例如，$(a,b]=\bigcap_{n=1}^{\infty}(a,b+1 / n)$，因此 $\mathcal{E}_{j}\subset \mathcal{B}_{\mathbb{R}}$，从而 $\mathcal{M}(\mathcal{E}_{j})\subset \mathcal{B}_{\mathbb{R}}$. 由于 $\mathbb{R}$ 上的开集是至多可数个开区间的并，因此 $\mathcal{B}_{\mathbb{R}}\subset \mathcal{M}(\mathcal{E}_{1})$，即 $\mathcal{B}_{\mathbb{R}}=\mathcal{M}(\mathcal{E}_{1})$. 下面我们只需证明 $\mathcal{M}(\mathcal{E}_{1})\subset\mathcal{M}(\mathcal{E}_{j}),j\geq 2$ 即可。

设 $a<b$，则 $(a,b)=\bigcup_{n=1}^{\infty}[a+1 / n,b-1 / n]$，故 $\mathcal{M}(\mathcal{E}_{1})=\mathcal{M}(\mathcal{E}_{2})$. 对于 $\mathcal{E}_{3},\mathcal{E}_{4}$ 同理。对于 $\mathcal{E}_{5}$，$(a,+\infty)$ 的补集为 $(-\infty,a]$，从而

$$
(a,b)= (a,+\infty) \cup \bigcup_{n=1}^{\infty} \left( -\infty,b- \dfrac{1}{n} \right]
$$

故 $\mathcal{M}(\mathcal{E}_{1})=\mathcal{M}(\mathcal{E}_{5})$，其余的同理，这就完成了证明。

关于 $\sigma$-代数，我们还有以下结论：

**定理 20.1.6**

设 $X$ 是一个集合，$\mathcal{E}\subset \mathscr{P}(X)$，则

$$
\mathcal{M}(\mathcal{E})=\bigcup \{ \mathcal{M}(\mathcal{F}) \mid \mathcal{F}\subset \mathcal{E},\mathcal{F}\text{是至多可数的} \}
$$

**证明**

记等式右边的集合为 $\mathcal{A}$，则 $\varnothing \in \mathcal{A}$，设 $E\in \mathcal{A}$，则存在至多可数集 $\mathcal{F}$ 使得 $E\in \mathcal{M}(\mathcal{F})$，从而 $X\setminus E\in \mathcal{M}(\mathcal{F})\subset \mathcal{A}$，最后，设 $(E_{n})_{n=0}^{\infty}$ 满足 $E_{j}\in \mathcal{A}$，则存在至多可数的子集 $(\mathcal{F}_{n})_{n=0}^{\infty}$ 使得 $E_{j}\in \mathcal{M}(\mathcal{F}_{j})$，令 $\mathcal{F}=\bigcup_{n=0}^{\infty} \mathcal{F}_{n}$，则 $\mathcal{F}$ 是 $\mathcal{E}$ 的至多可数子集，并且 $\mathcal{M}(\mathcal{F}_{j})\subset \mathcal{M}(\mathcal{F})$，从而 $\bigcup_{n=0}^{\infty}E_{n}\in \mathcal{M}(\mathcal{F})\subset \mathcal{A}$，故 $\mathcal{A}$ 是一个 $\sigma$-代数。

由于 $\mathcal{F}\subset \mathcal{E}$，故 $\mathcal{M}(\mathcal{F})\subset \mathcal{M}(\mathcal{E})$，从而 $\mathcal{A}\subset \mathcal{M}(\mathcal{E})$，另一方面，设 $E\in \mathcal{E}$，则 $E\in\mathcal{M}(\{ E \})\subset \mathcal{A}$，故 $\mathcal{E}\subset \mathcal{A}$，这就完成了证明。

可见，一个集族 $\mathcal{E}$ 生成的 $\sigma$-代数可以从两个方面来考虑：从外部限制（20.1.2）和从内部构造（20.1.6），在测度中我们也有类似的概念（外测度和内测度）。

下面，我们再引入一个概念。

**定义 20.1.7** 乘积 $\sigma$-代数（product $\sigma$-algebra）

设 $X=\prod_{\alpha \in A}X_{\alpha}$，$\pi_{\alpha}\colon X\to X_{\alpha}$ 是投影函数，如果对任意 $\alpha$，$\mathcal{M}_{\alpha}$ 是 $X_{\alpha}$ 上的 $\sigma$-代数，那么 $X$ 上的**乘积** $\sigma$**-代数**定义为

$$
\bigotimes_{\alpha \in A} \mathcal{M}_{\alpha} =\mathcal{M}(\{ \pi_{\alpha}^{-1}[E_{\alpha}] \mid E_{\alpha}\in \mathcal{M}_{\alpha},\alpha \in A \})
$$

乘积 $\sigma$-代数这样定义的原因将在我们定义可测函数以后解释，现在，我们给出一种更为直观的表示方法。

**定理 20.1.8**

设 $X=\prod_{\alpha \in A}X_{\alpha}$，$\mathcal{M}_{\alpha}$ 是 $X_{\alpha}$ 上的 $\sigma$-代数，如果 $A$ 是至多可数的，那么

$$
\bigotimes_{\alpha \in A} \mathcal{M}_{\alpha}=\mathcal{M}\left( \left\{  \prod_{\alpha \in A} E_{\alpha} \middle| E_{\alpha} \in \mathcal{M}_{\alpha}  \right\} \right)
$$

**证明**

设 $E_{\alpha}\in \mathcal{M}_{\alpha}$，则 $\pi_{\alpha}^{-1}[E_{\alpha}]=\prod_{\beta \in A}E_{\beta}$，其中 $E_{\beta}=X,\beta\neq \alpha$，因此，左边包含于右边。另一边，我们有 $\prod_{\alpha \in A}E_{\alpha}=\bigcap_{\alpha \in A}\pi_{\alpha}^{-1}[E_{\alpha}]$，根据 $A$ 的可数性知右边包含于左边，即证。

下面我们考虑由集族生成的 $\sigma$-代数与乘积代数的关系。

**定理 20.1.9**

设 $X=\prod_{\alpha \in A}X_{\alpha}$，$\mathcal{E}_{\alpha}\subset \mathscr{P}(X_{\alpha})$，则

$$
\bigotimes_{\alpha \in A}\mathcal{M}(\mathcal{E}_{\alpha})=\mathcal{M}(\{ \pi_{\alpha}^{-1}[E_{\alpha}] \mid E_{\alpha} \in \mathcal{E}_{\alpha},\alpha \in A \})
$$

**证明**

由于 $E_{\alpha}\in \mathcal{E}_{\alpha}\subset \mathcal{M}(\mathcal{E}_{\alpha})$，故右边包含于左边。另一边，设 $\mathcal{F}=\{ \pi_{\alpha}^{-1}[E_{\alpha}] \mid E_{\alpha} \in \mathcal{E}_{\alpha},\alpha \in A \}$，则集族

$$
\{ E\subset X_{\alpha} \mid \pi_{\alpha}^{-1}[E] \in \mathcal{M}(\mathcal{F}) \}
$$

是 $X_{\alpha}$ 上包含 $\mathcal{E}_{\alpha}$ 的 $\sigma$-代数，从而其包含 $\mathcal{M}(\mathcal{E}_{\alpha})$，即对任意 $E \in \mathcal{M}(\mathcal{E}_{\alpha})$，有 $\pi_{\alpha}^{-1}[E]\in \mathcal{M}(\mathcal{F})$，从而左边包含于右边，即证。

下面我们来看 Borel $\sigma$-代数的乘积，我们先来补充一些点集拓扑知识。

**定义 20.1.10** 乘积度量（product metric）

设 $(X,d_{X}),(Y,d_{Y})$ 是度量空间，定义 $X\times Y$ 上的**乘积度量**为

$$
d_{X\times Y}((x_{1},y_{1}),(x_{2},y_{2}))=\sup(d_{X}(x_{1},x_{2}),d_{Y}(y_{1},y_{2}))
$$

有时候乘积度量会定义为

$$
d_{X}(x_{1},x_{2})+d_{Y}(y_{1},y_{2}), (d_{X}(x_{1},x_{2})^{2}+d_{Y}(y_{1},y_{2})^{2})^{1/2}
$$

然而，我们可以证明与定理 14.1.8 类似的一个定理，指出这些度量在序列的收敛性上是等价的。

**定义 20.1.11** 稠密（dense），可分（separable）

设 $(X,d)$ 是度量空间，称 $E\subset X$ 是**稠密的**，如果 $\overline{E}=X$；称 $E$ 是**无处稠密的**（nowhere dense），如果 $\mathrm{Int}(\overline{E})=\varnothing$；称 $X$ 是**可分的**，如果 $X$ 有一个稠密的可数子集。

例如，实数集 $\mathbb{R}$ 是可分的，因为 $\mathbb{Q}\subset \mathbb{R}$ 是一个可数的稠密子集。

**定理 20.1.12**

设 $X_{1},\dots,X_{n}$ 是度量空间，$X=\prod_{j=1}^{n} X_{j}$，其上的度量为乘积度量，那么 $\bigotimes_{j=1}^{n}\mathcal{B}_{X_{j}}\subset \mathcal{B}_{X}$. 如果每个 $X_{j}$ 都是可分的，那么 $\bigotimes_{j=1}^{n}\mathcal{B}_{X_{j}}= \mathcal{B}_{X}$.

**证明**

根据定理 20.1.9，$\bigotimes_{j=1}^{n}\mathcal{B}_{X_{j}}$ 由集合 $\pi_{j}^{-1}[U_{j}]$ 生成，其中 $U_{j}$ 在 $X_{j}$ 中是开集，由于投影函数连续，故 $\pi_{j}^{-1}[U_{j}]$ 在 $X$ 中是开集，故 $\bigotimes_{j=1}^{n}\mathcal{B}_{X_{j}}\subset \mathcal{B}_{X}$.

设 $X_{j}$ 是可分的，至多可数集 $C_{j}\subset X_{j}$ 在 $X_{j}$ 中稠密，令

$$
\mathcal{E}_{j}=\{ B_{X_{j}}(x,r) \mid x \in C_{j},r \in \mathbb{Q}_{>0} \}
$$

那么 $\mathcal{E}_{j}$ 是至多可数的，并且 $X_{j}$ 中的每个开集都是 $\mathcal{E}_{j}$ 中元素的可数并，即 $\mathcal{B}_{X_{j}}$ 由 $\mathcal{E}_{j}$ 生成。此外，至多可数集 $\prod_{j=1}^{n}C_{j}$ 在 $X$ 中稠密，并且 $X$ 中半径为 $r \in \mathbb{Q}_{>0}$ 的开球是各 $X_{j}$ 中开球 $B_{X_{j}}(x_{j},r)$ 的乘积，因此 $\mathcal{B}_{X}$ 由 $\left\{  \prod_{j=1}^{n} E_{j} \mid E_{j} \in \mathcal{E}_{j}  \right\}$ 生成，从而 $\bigotimes_{j=1}^{n}\mathcal{B}_{X_{j}}= \mathcal{B}_{X}$，这就完成了证明。

根据上述定理与实数集可分的结论，我们就有 $\mathcal{B}_{\mathbb{R}^{n}}=\bigotimes_{j=1}^{n}\mathcal{B}_{\mathbb{R}}$.

最后，我们再引入一个概念，在后续的研究中将会用到。

**定义 20.1.13** 基本族（elementary family）

集合 $X$ 的子集族 $\mathcal{E}\subset \mathscr{P}(X)$ 是一个**基本族**如果：

1. $\varnothing \in \mathcal{E}$
2. 如果 $E,F\in \mathcal{E}$，那么 $E\cap F \in \mathcal{E}$
3. 如果 $E\in \mathcal{E}$，那么 $E^{c}=X\setminus E$ 是 $\mathcal{E}$ 中有限个元素的无交并。

**定理 20.1.14**

设 $X$ 是集合，如果 $\mathcal{E}\subset \mathscr{P}(X)$ 是一个基本族，那么 $\mathcal{E}$ 中有限个元素的无交并构成的集合 $\mathcal{A}$ 是一个代数。

**证明**

$\mathcal{E}$ 中 $0$ 个元素的并集是 $\varnothing$，故 $\varnothing \in \mathcal{A}$. 下面用归纳法证明 $\mathcal{A}$ 对有限并封闭。设 $A,B \in \mathcal{E}$，且 $B^{c}=\bigcup_{j=1}^{n}C_{j}$，其中 $C_{j}\in \mathcal{E}$ 且不相交，那么有 $A\setminus B=\bigcup_{j=1}^{n}(A\cap C_{j})\in \mathcal{E}$，从而 $A\cup B=(A\setminus B)\cup B\in \mathcal{A}$.

假设 $A_{1},\dots,A_{n-1}\in \mathcal{E}$ 不相交，则 $\bigcup_{j=1}^{n}A_{n}=A_{n}\cup \bigcup_{j=1}^{n-1}(A_{j}\setminus A_{n})\in \mathcal{A}$，因此 $\mathcal{A}$ 对有限并封闭。下证 $\mathcal{A}$ 对补集封闭。设 $A_{1},\dots,A_{n}\in \mathcal{E}$ 不相交，并且 $A_{m}^{c}=\bigcup_{j=1}^{N_{m}}B_{mj}$，则有

$$
\left( \bigcup_{m=1}^{n}A_{m} \right)^{c}=\bigcap_{m=1}^{n}\bigcup_{j=1}^{N_{m}}B_{mj}=\bigcup \left\{  \bigcap_{m=1}^{n}B_{mj_{m}} \middle| 1\leq j_{m}\leq N_{m}  \right\} \in \mathcal{A}
$$

这就完成了证明。

# Section 2: 测度空间

利用 $\sigma$-代数，我们就可以在其上定义**测度**。

**定义 20.2.1** 测度空间（measure space）

**测度空间** $(X,\mathcal{M},\mu)$ 包含集合 $X$，其上的 $\sigma$-代数 $\mathcal{M}$，其中的元素称为**可测集**，以及函数 $\mu\colon \mathcal{M}\to [0,+\infty]$，称为**可测空间** $(X,\mathcal{M})$ 上的**测度**，满足：

1. $\mu(\varnothing)=0$
2. 设 $(E_{n})_{n=0}^{\infty}$ 是 $\mathcal{M}$ 中不相交的集合，那么 $\mu\left( \bigcup_{n=0}^{\infty}E_{n} \right)=\sum_{n=0}^{\infty}\mu(E_{n})$

对于测度的运算，我们通常定义 $+\infty+x=+\infty$，其中 $x \in[0,+\infty]$，以及 $+\infty \cdot x=+\infty$，其中 $x \in(0,+\infty]$. 对于 $+\infty\cdot 0$，需要我们单独考虑（尽管多数时候都等于零）。

**定义 20.2.2** 有限（finite），$\sigma$-有限（$\sigma$-finite），半有限（semifinite）

设 $(X,\mathcal{M},\mu)$ 是一个测度空间，称 $\mu$ 是**有限的**，如果 $\mu(X)<+\infty$；称 $\mu$ 是 $\sigma$**-有限的**，如果 $X=\bigcup_{j=0}^{\infty}E_{j}$，其中 $\mu(E_{j})<+\infty$；更普遍地，如果 $E=\bigcup_{j=0}^{\infty}E_{j}$，其中 $\mu(E_{j})<+\infty$，则称 $E$ 关于 $\mu$ 是 $\sigma$-有限的；称 $\mu$ 是**半有限的**，如果对任意满足 $\mu(E)=+\infty$ 的 $E$，存在 $F\subset E$ 使得 $0<\mu(F)<+\infty$.

不是 $\sigma$-有限的测度有一些病态的表现，幸运的是，我们在生活中遇到的大多数测度都是 $\sigma$-有限的。此外，$\sigma$-有限的测度还有一些较好的性质，比如它总是半有限的。

**定理 20.2.3**

$\sigma$-有限的测度是半有限的。

**证明**

设 $(X,\mathcal{M},\mu)$ 是测度空间，$\mu$ 是 $\sigma$-有限的，则 $X=\bigcup_{j=0}^{\infty}E_{j}$，并且 $\mu(E_{j})<+\infty$，如果 $\mu(X)<+\infty$，则结论成立。下设 $\mu(X)=+\infty$.

不妨设各 $E_{j}$ 是不相交的（否则我们可以定义 $F_{n}=E_{n}\setminus\bigcup_{j=0}^{n-1}E_{j}$ 从而得到不相交的集合），那么 $\{ E_{j} \}$ 构成了 $X$ 的一个分割。设 $\mu(E)=+\infty$，则 $E=\bigcup_{j=0}^{\infty}(E\cap E_{j})$，从而 $\mu(E)=\sum_{j=0}^{\infty}\mu(E\cap E_{j})=+\infty$，因此必然存在一个 $J$，使得 $\mu(E\cap E_{J})> 0$，由于 $\mu(E_{J})=\mu(E\cap E_{J})+\mu(E^{c}\cap E_{J})$，故 $\mu(E\cap E_{J})\leq \mu(E_{J})<+\infty$，这就完成了证明。

下面我们给出一个测度的例子，它将测度与无限和联系在一起。

设 $X$ 是任意集合，$\mathcal{M}=\mathscr{P}(X)$，函数 $f\colon X\to [0,+\infty]$，那么 $f$ 在 $\mathcal{M}$ 上通过如下公式定义了一个测度：

$$
\mu(E)=\sum_{x \in E} f(x)=\sup \left\{  \sum_{x \in F}f(x) \middle| F\subset E,F\text{是有限集}  \right\}
$$

我们可以验证，如果 $f(x)<+\infty$，那么 $\mu$ 就是半有限的，如果还有 $\{ x \in X \mid f(x)>0 \}$ 是可数的，那么 $\mu$ 就是 $\sigma$-有限的。

如果对任意 $x \in X$ 有 $f(x)=1$，那么 $\mu$ 就称为**计数测度**；如果存在一个 $x_{0}$ 使得 $f(x_{0})=1$，在其它点处有 $f(x)=0$，那么 $\mu$ 就称为 $x_{0}$ 处的 **Dirac 测度**。

下面我们给出测度的一些基本性质。

**定理 20.2.4**

设 $(X,\mathcal{M},\mu)$ 是一个测度空间，则：

1. 单调性：如果 $E,F \in \mathcal{M},E\subset F$，那么 $\mu(E)\leq \mu(F)$
2. 次可加性：如果 $(E_{n})_{n=0}^{\infty}$ 中每个 $E_{j}\in \mathcal{M}$，那么 $\mu\left( \bigcup_{n=0}^{\infty}E_{n} \right)\leq \sum_{n=0}^{\infty}\mu(E_{n})$
3. 如果 $(E_{n})_{n=0}^{\infty}$ 中每个 $E_{j}\in \mathcal{M}$，并且 $E_{0}\subset E_{1}\subset\cdots$，那么 $\mu\left( \bigcup_{n=0}^{\infty}E_{n} \right)=\lim_{ n \to \infty }\mu(E_{n})$
4. 如果 $(E_{n})_{n=0}^{\infty}$ 中每个 $E_{j}\in \mathcal{M}$，并且 $E_{0}\supset E_{1}\supset\cdots,\mu(E_{0})<+\infty$，那么 $\mu\left( \bigcap_{n=0}^{\infty}E_{n} \right)=\lim_{ n \to \infty }\mu(E_{n})$

**证明**

(1). 我们有 $\mu(F)=\mu(E)+\mu(F\setminus E)\geq \mu(E)$.

(2). 设 $F_{0}=E_{0}$ 并递归地定义 $F_{n}=E_{n}\setminus\bigcup_{j=0}^{n-1}E_{j}\subset E_{n}$，则 $F_{j}$ 互不相交且 $\bigcup_{n=0}^{\infty}F_{n}=\bigcup_{n=0}^{\infty}E_{n}$，从而

$$
\mu\left( \bigcup_{n=0}^{\infty}E_{n} \right)=\sum_{n=0}^{\infty} \mu(F_{n})\leq \sum_{n=0}^{\infty} \mu(E_{n})
$$

(3). 我们有

$$
\mu\left( \bigcup_{j=0}^{\infty}E_{j} \right)=\mu(E_{0})+\sum_{j=1}^{\infty} \mu(E_{j}\setminus E_{j-1})=\mu(E_{0})+\lim_{ n \to \infty } (\mu(E_{n})-\mu(E_{0}))
$$

即证。

(4). 令 $F_{n}=E_{0}\setminus E_{n}$，则 $F_{0}\subset F_{1}\subset\cdots$，从而

$$
\mu(E_{0})-\mu\left( \bigcap_{j=0}^{\infty}E_{j} \right)=\mu\left( \bigcup_{j=0}^{\infty}F_{j} \right)=\lim_{ n \to \infty } (\mu(E_{0})-\mu(E_{n}))
$$

由于 $\mu(E_{0})<+\infty$，从两端消去就完成了证明。

关于测度，还有一个定理也涉及极限。

**定义 20.2.5** 上极限（limit superior），下极限（limit inferior）

设 $(E_{n})_{n=0}^{\infty}$ 是一列集合，则其**上极限**和**下极限**定义为

$$
\limsup_{ n \to \infty } E_{n}=\bigcap_{k=0}^{\infty}\bigcup_{n=k}^{\infty}E_{n},\liminf_{ n \to \infty } E_{n}=\bigcup_{k=0}^{\infty}\bigcap_{n=k}^{\infty}E_{n}
$$

根据简单的推导，我们知道 $x \in \limsup_{ n \to \infty }E_{n}$ 当且仅当对任意 $k$，都存在 $n\geq k$ 使得 $x \in E_{n}$；$x \in \liminf_{ n \to \infty }E_{n}$ 当且仅当存在 $k$，使得对任意 $n\geq k$ 有 $x \in E_{n}$.

**定理 20.2.6**

设 $(X,\mathcal{M},\mu)$ 是一个测度空间，$(E_{n})_{n=0}^{\infty}$ 是 $\mathcal{M}$ 中的集合，那么有 $\mu(\liminf_{ n \to \infty } E_{n})\leq \liminf_{ n \to \infty } \mu(E_{n})$，如果还有 $\mu\left( \bigcup_{n=0}^{\infty}E_{n} \right)<+\infty$，那么 $\limsup_{ n \to \infty } \mu(E_{n})\leq \mu(\limsup_{ n \to \infty } E_{n})$.

**证明**

由于 $\bigcap_{n=0}^{\infty}E_{n}\subset \bigcap_{n=1}^{\infty}E_{n}\subset\cdots$，故

$$
\mu(\liminf_{ n \to \infty }E_{n})=\lim_{ k \to \infty }\mu\left( \bigcap_{n=k}^{\infty}E_{n} \right)=\sup_{k\geq 0}\mu\left( \bigcap_{n=k}^{\infty}E_{n} \right)
$$

对任意 $n\geq k$，$\bigcap_{j=k}^{\infty}E_{j}\subset E_{n}$，故 $\mu(\bigcap_{j=k}^{\infty}E_{j})\leq \mu(E_{n})$，取下确界即得

$$
\sup_{k\geq 0}\mu\left( \bigcap_{n=k}^{\infty}E_{n} \right)\leq \sup_{k\geq 0} \inf_{n\geq k} \mu(E_{n})=\liminf_{ n \to \infty } \mu(E_{n})
$$

另一边同理。

设 $(X,\mathcal{M},\mu)$ 是一个测度空间，我们来考察使得 $\mu(E)=0$ 的 $E\in \mathcal{M}$，这通常被称为**零测集**，根据次可加性，我们可以知道至多可数个零测集的并也是零测集。设 $P(x)$ 是一个关于 $x \in X$ 的命题，如果 $P(x)$ 对除了一个零测集以外的点都成立，我们就称 $P(x)$ 在 $X$ 上**几乎处处**（almost everywhere，简写为 a.e.）成立，或者称 $P(x)$ 对**几乎所有** $x$ 都成立。

设 $\mu(E)=0,F\subset E$，如果 $F\in \mathcal{M}$，那么单调性保证了 $\mu(F)=0$，然而通常情况下 $F$ 不一定是可测集，于是我们给出以下定义：

**定义 20.2.7** 完备的（complete）

设 $(X,\mathcal{M},\mu)$ 是测度空间，称 $\mu$ 是**完备的**，如果对任意零测集 $E \in \mathcal{M}$，有 $\mathscr{P}(E)\subset \mathcal{M}$.

对于一个不完备的测度 $\mu$，如果我们把零测集的所有子集添加到 $\mathcal{M}$ 中，实际上并不会产生很大影响，$\mu$ 仍然是一个测度，从而我们有以下定理成立：

**定理 20.2.8**

设 $(X,\mathcal{M},\mu)$ 是测度空间，$\mathcal{N}=\{ N \in \mathcal{M} \mid \mu(N)=0 \}$，令

$$
\overline{\mathcal{M}}=\{ E\cup F \mid E \in \mathcal{M},F\subset N \in \mathcal{N} \}
$$

那么 $\overline{\mathcal{M}}$ 是 $X$ 上的 $\sigma$-代数，并且存在唯一的完备测度 $\overline{\mu}$ 作为 $\mu$ 在 $\overline{\mathcal{M}}$ 上的扩张。

**证明**

由于 $\mathcal{M},\mathcal{N}$ 都对可数并封闭，从而 $\overline{\mathcal{M}}$ 也对可数并封闭。设 $E\cup F \in \overline{\mathcal{M}}$，其中 $E\in \mathcal{M},F\subset N \in \mathcal{N}$，我们可以设 $E\cap N=\varnothing$（否则我们可以将 $F$ 和 $N$ 替换为 $F\setminus E$ 和 $N\setminus E$），从而 $E\cup F=(E\cup N)\cap(N^{c}\cup F)$，于是 $(E\cup F)^{c}=(E\cup N)^{c}\cup(N\setminus F)$，而 $E\cup N \in \mathcal{M},N\setminus F\subset N$，故 $\overline{\mathcal{M}}$ 对补集封闭。因此 $\overline{\mathcal{M}}$ 是一个 $\sigma$-代数。

设 $E\cup F\in \overline{\mathcal{M}}$，定义 $\overline{\mu}(E\cup F)=\mu(E)$，这个定义是良定的，因为当 $E_{1}\cup F_{1}=E_{2}\cup F_{2}$ 时，有 $E_{1}\subset E_{2}\cup N_{2}$，从而

$$
\mu(E_{1})\leq \mu(E_{2})+\mu(N_{2})=\mu(E_{2})
$$

根据对称性，也有 $\mu(E_{2})\leq \mu(E_{1})$. 设 $F\subset N \in \mathcal{N}$，则 $F=\varnothing\cup F\in \overline{\mathcal{M}}$，从而 $\overline{\mu}$ 是完备的。假设有另一个完备测度 $\overline{\nu}$，那么对任意 $E\cup F \in \overline{\mathcal{M}}$，我们有

$$
\overline{\mu}(E\cup F)=\mu(E)=\overline{\nu}(E\cup F)
$$

从而 $\overline{\mu}=\overline{\nu}$，这就完成了证明。

上述定理中的 $\overline{\mu}$ 称为 $\mu$ 的**完备化**，$\overline{\mathcal{M}}$ 称为 $\mathcal{M}$ 关于 $\mu$ 的完备化。

# Section 3: 外测度

前面我们一直在讨论抽象的测度，现在，我们将要真正地构造一些有用的测度出来。为了引出所谓“外测度”的概念，我们首先来考虑一个问题：如何求平面上不规则图形 $\Omega$ 的面积？按照分析中一贯的做法，我们可以用若干个长方形（它的面积是已知的）来近似 $\Omega$，准确地说，是分别从外部和内部逼近 $\Omega$：设 $R^{*},R_{*}$ 是由长方形构成的集合，并且 $R_{*}\subset\Omega \subset R^{*}$，这些长方形的面积的极限分别称为“外面积”和“内面积”，如果外面积等于内面积，那么这个值就定义为 $\Omega$ 的面积。注意，设 $R$ 是包含 $\Omega$ 的一个长方形，那么 $\Omega$ 的内面积就等于 $R$ 的面积减去 $R\setminus \Omega$ 的外面积。

现在我们将上述思想进行推广，将外面积的概念抽象化，我们就得到了**外测度**的概念。

**定义 20.3.1** 外测度（outer measure）

设 $X$ 是一个集合，$X$ 上的一个**外测度**是函数 $\mu^{*}\colon \mathscr{P}(X)\to[0,+\infty]$ 满足：

1. $\mu^{*}(\varnothing)=0$
2. 如果 $A\subset B$，那么 $\mu^{*}(A)\leq \mu^{*}(B)$
3. $\mu^{*}\left( \bigcup_{n=0}^{\infty}A_{n} \right)\leq \sum_{n=0}^{\infty}\mu^{*}(A_{n})$

与上面的例子一样，最常用的构造外测度的方法，就是从一些基本的、可求测度的集合（例如平面上的长方形）出发，用这些集合的可数并来“从外部逼近”任意集合，如下所示：

**定理 20.3.2**

设 $X$ 是一个集合，$\mathcal{E}\subset \mathscr{P}(X)$，函数 $\rho\colon \mathcal{E}\to[0,+\infty]$ 满足 $\varnothing \in \mathcal{E},X \in \mathcal{E}$ 且 $\rho(\varnothing)=0$，对任意 $A\subset X$，定义

$$
\mu^{*}(A)=\inf \left\{  \sum_{n=0}^{\infty} \rho(E_{n}) \middle| E_{n} \in \mathcal{E}, A\subset \bigcup_{n=0}^{\infty} E_{n}  \right\}
$$

那么 $\mu^{*}$ 是 $X$ 上的外测度。

**证明**

显然 $\mu^{*}(\varnothing)=0$. 设 $A\subset B$，由于

$$
\left\{  \sum_{n=0}^{\infty} \rho(E_{n}) \middle| E_{n} \in \mathcal{E}, B\subset \bigcup_{n=0}^{\infty} E_{n}  \right\}\subset\left\{  \sum_{n=0}^{\infty} \rho(E_{n}) \middle| E_{n} \in \mathcal{E}, A\subset \bigcup_{n=0}^{\infty} E_{n}  \right\}
$$

故 $\mu^{*}(A)\leq \mu^{*}(B)$. 设 $(A_{n})_{n=0}^{\infty}$ 满足 $A_{j}\subset X$，则对任意 $j$，存在 $(E_{jk})_{k=0}^{\infty}$ 满足 $E_{jk}\in \mathcal{E}$ 且 $A_{j}\subset \bigcup_{k=0}^{\infty}E_{jk}$，根据下确界的性质，任取 $\varepsilon>0$ 使得

$$
\sum_{k=0}^{\infty} \rho(E_{jk})=\mu^{*}(A_{j})+ \dfrac{\varepsilon}{2^{j}}
$$

而 $\bigcup_{j=0}^{\infty}A_{j}\subset \bigcup_{j,k=0}^{\infty}E_{jk}$，故

$$
\mu^{*}\left( \bigcup_{j=0}^{\infty}A_{j} \right)\leq \sum_{j,k=0}^{\infty} \rho(E_{jk})=\sum_{j=0}^{\infty} \mu^{*}(A_{j})+2\varepsilon
$$

由 $\varepsilon$ 的任意性即证。

现在我们有了外测度，要得到真正的测度，我们就需要从 $\mathscr{P}(X)$ 中分离出可测集。我们可以仿照二维平面上的例子，定义一个“内测度”，然后分离出那些外测度等于内测度的集合作为可测集，不过，我们还有一种等价的方法，通常称为 **Caratheodory 条件**，事实证明，这一条件比使用内测度更方便。

**定义 20.3.3** $\mu^{*}$-可测（$\mu^{*}$-measurable）

设 $\mu^{*}$ 是 $X$ 上的外测度，称 $A\subset X$ 是 $\mu^{*}$**-可测的**，如果对任意 $E\subset X$ 有

$$
\mu^{*}(E)=\mu^{*}(E\cap A)+\mu^{*}(E\cap A^{c})
$$

根据外测度的次可加性，我们实际上只需验证

$$
\mu^{*}(E)\geq \mu^{*}(E\cap A)+\mu^{*}(E\cap A^{c}),\mu^{*}(E)<+\infty
$$

即可，因为当 $\mu^{*}(E)=+\infty$ 时上式显然成立。这一定义与“外等于内”的等价性体现在当 $A\subset E$ 时有 $\mu^{*}(A)=\mu^{*}(E)-\mu^{*}(E\setminus A)$，其中等式的右边可以看成 $A$ 的“内测度”，我们可以将其与本节开头的例子比较一下。

**定理 20.3.4** Caratheodory 定理

设 $\mu^{*}$ 是 $X$ 上的外测度，那么 $X$ 上 $\mu^{*}$-可测的集合构成的集族 $\mathcal{M}$ 是一个 $\sigma$-代数，并且 $\mu^{*}$ 在 $\mathcal{M}$ 上的限制是一个完备测度。

**证明**

显然 $\varnothing \in \mathcal{M}$，并且 $\mathcal{M}$ 对补集封闭，因为 $\mu^{*}$-可测的定义对 $A$ 和 $A^{c}$ 是对称的。设 $A,B \in \mathcal{M},E\subset X$，则

$$
\begin{align}
&\mu^{*}(E) = \mu^{*}(E\cap A)+\mu^{*}(E\cap A^{c}) \\
&= \mu^{*}(E\cap A\cap B)+\mu^{*}(E\cap A\cap B^{c})+\mu^{*}(E\cap A^{c}\cap B)+\mu^{*}(E\cap A^{c}\cap B^{c})
\end{align}
$$

而 $A\cup B=(A\cap B)\cup(A^{c}\cap B)\cup(A\cap B^{c})$，故

$$
\mu^{*}(E)\geq \mu^{*}(E\cap(A\cup B))+\mu^{*}(E\cap(A\cup B)^{c})
$$

从而 $A\cup B \in \mathcal{M}$，即 $\mathcal{M}$ 是一个代数。此外，设 $A\cap B=\varnothing$，则

$$
\begin{align}
\mu^{*}(A\cup B)&=\mu^{*}((A\cup B)\cap A)+\mu^{*}((A\cup B)\cap A^{c}) \\
&=\mu^{*}(A)+\mu^{*}(B)
\end{align}
$$

于是 $\mu^{*}$ 是有限可加的。

要证 $\mathcal{M}$ 是 $\sigma$-代数，我们需要证明 $\mathcal{M}$ 对可数无交并封闭。设 $(A_{n})_{n=0}^{\infty}$ 互不相交，$A_{j}\in \mathcal{M}$，令 $B_{n}=\bigcup_{j=0}^{n}A_{j},B=\bigcup_{j=0}^{\infty}A_{j}$，则

$$
\begin{align}
\mu^{*}(E\cap B_{n})&=\mu^{*}(E\cap B_{n}\cap A_{n})+\mu^{*}(E\cap B_{n}\cap A_{n}^{c}) \\
&= \mu^{*}(E\cap A_{n})+\mu^{*}(E\cap B_{n-1}) \\
&= \sum_{j=0}^{n} \mu^{*}(E\cap A_{j})
\end{align}
$$

从而

$$
\mu^{*}(E)=\mu^{*}(E\cap B_{n})+\mu^{*}(E\cap B_{n}^{c})\geq \sum_{j=0}^{n} \mu^{*}(E\cap A_{j})+\mu^{*}(E\cap B^{c})
$$

令 $n\to \infty$，则有

$$
\begin{align}
\mu^{*}(E)&\geq \sum_{j=0}^{\infty} \mu^{*}(E\cap A_{j})+\mu^{*}(E\cap B^{c}) \\
&\geq \mu^{*}(E\cap B)+\mu^{*}(E\cap B^{c})\geq \mu^{*}(E)
\end{align}
$$

从而 $B$ 是 $\mu^{*}$-可测的，故 $\mathcal{M}$ 是 $\sigma$-代数。在上式中取 $E=B$，则有 $\mu^{*}(B)=\sum_{j=0}^{\infty}\mu^{*}(A_{j})$，故 $\mu^{*}$ 是可数可加的，因而是一个测度。最后，设 $\mu^{*}(A)=0$，对任意 $E\subset X$ 有

$$
\mu^{*}(E)\leq \mu^{*}(E\cap A)+\mu^{*}(E\cap A^{c})=\mu^{*}(E\cap A^{c})\leq \mu^{*}(E)
$$

从而 $A \in \mathcal{M}$，因此 $\mu^{*}|_{\mathcal{M}}$ 是完备的，这就完成了证明。

作为 Caratheodory 定理的第一个应用，我们来考虑如何将一个代数上的测度扩展到 $\sigma$-代数上。

**定义 20.3.5** 预测度（premeasure）

设 $X$ 是一个集合，$\mathcal{A}$ 是 $X$ 上的代数，称函数 $\mu_{0}\colon \mathcal{A}\to[0,+\infty]$ 是一个**预测度**如果：

1. $\mu_{0}(\varnothing)=0$
2. 如果 $(A_{n})_{n=0}^{\infty}$ 是 $\mathcal{A}$ 上不相交的集合，并且 $\bigcup_{n=0}^{\infty}A_{n}\in \mathcal{A}$，那么 $\mu_{0}\left( \bigcup_{n=0}^{\infty}A_{n} \right)=\sum_{n=0}^{\infty}\mu_{0}(A_{n})$

$\mu_{0}$ 之所以被称为预测度，是因为它自然地诱导了 $X$ 上的一个外测度：

**引理 20.3.6**

设 $X$ 是一个集合，$\mathcal{A}$ 是 $X$ 上的代数，$\mu_{0}$ 是 $\mathcal{A}$ 上的预测度，定义

$$
\mu^{*}(E)=\inf \left\{  \sum_{n=0}^{\infty} \mu_{0}(A_{n}) \middle| A_{j}\in \mathcal{A},E\subset \bigcup_{n=0}^{\infty}A_{n}  \right\}
$$

则 $\mu^{*}$ 是一个外测度，$\mu^{*}|_{\mathcal{A}}=\mu_{0}$，并且每个 $A\in \mathcal{A}$ 都是 $\mu^{*}$-可测的。

**证明**

根据定理 20.3.2，$\mu^{*}$ 是一个外测度。设 $E \in \mathcal{A}$，如果 $E\subset \bigcup_{n=0}^{\infty}A_{n}$，定义 $B_{n}=E\cap\left( A_{n}\setminus \bigcup_{j=0}^{n-1}A_{j} \right)$，那么 $B_{n}\in \mathcal{A}$ 且互不相交，从而

$$
\mu^{*}(E)\leq\mu_{0}(E)=\sum_{n=0}^{\infty} \mu_{0}(B_{n})\leq \sum_{n=0}^{\infty} \mu_{0}(A_{n})
$$

取下确界得 $\mu^{*}(E)\leq\mu_{0}(E)\leq \mu^{*}(E)$，因此 $\mu^{*}|_{\mathcal{A}}=\mu_{0}$.

现设 $A \in \mathcal{A},E\subset X$，则有 $\mathcal{A}$ 中不相交的集合 $(B_{n})_{n=0}^{\infty}$ 使得 $E\subset \bigcup_{n=0}^{\infty}B_{n}$ 并且 $\sum_{n=0}^{\infty}\mu_{0}(B_{n})\leq \mu^{*}(E)+\varepsilon$，从而

$$
\mu^{*}(E)+\varepsilon\geq \sum_{n=0}^{\infty} (\mu_{0}(B_{n}\cap A)+\mu_{0}(B_{n}\cap A^{c}))\geq \mu^{*}(E\cap A)+\mu^{*}(E\cap A^{c})
$$

根据 $\varepsilon$ 的任意性即证。

**定理 20.3.7** Caratheodory 扩张定理

设 $X$ 是一个集合，$\mathcal{A}$ 是 $X$ 上的代数，$\mu_{0}$ 是 $\mathcal{A}$ 上的预测度，$\mathcal{M}$ 是 $\mathcal{A}$ 生成的 $\sigma$-代数，那么存在一个 $\mathcal{M}$ 上的测度 $\mu$ 使得 $\mu|_{\mathcal{A}}=\mu_{0}$. 如果 $\nu$ 是 $\mathcal{M}$ 上的另一个测度，$\nu|_{\mathcal{A}}=\mu_{0}$，那么对任意 $E \in \mathcal{M}$ 有 $\nu(E)\leq \mu(E)$，取等号当且仅当 $\mu(E)<+\infty$. 如果进一步有 $\mu_{0}$ 是 $\sigma$-有限的，那么 $\mu=\nu$.

**证明**

取 $\mu_{0}$ 诱导的外测度 $\mu^{*}$，则根据 Caratheodory 定理和引理 20.3.6，存在一个测度 $\mu$ 使得 $\mu|_{\mathcal{A}}=\mu_{0}$，并且其定义域包含 $\mathcal{A}$，进而包含 $\mathcal{M}$.

设 $E \in \mathcal{M},E\subset \bigcup_{n=0}^{\infty}A_{n},A_{j}\in \mathcal{A}$，则 $\nu(E)\leq \sum_{n=0}^{\infty} \nu(A_{n})=\sum_{n=0}^{\infty} \mu_{0}(A_{n})$，从而 $\nu(E)\leq \mu(E)$. 再设 $A=\bigcup_{n=0}^{\infty}A_{n}$，则

$$
\nu(A)=\lim_{ n \to \infty } \nu\left( \bigcup_{j=0}^{n}A_{j} \right)=\lim_{ n \to \infty } \mu\left( \bigcup_{j=0}^{n}A_{j} \right)=\mu(A)
$$

当 $\mu(E)<+\infty$ 时，我们可以选取 $A_{j}$ 使得 $\mu(A)<\mu(E)+\varepsilon$，从而

$$
\mu(E)\leq \mu(A)=\nu(A)=\nu(E)+\nu(A\setminus E)\leq \nu(E)+\mu(A\setminus E)<\nu(E)+\varepsilon
$$

从而 $\mu(E)=\nu(E)$. 最后设 $\mu_{0}$ 是 $\sigma$-有限的，即 $X=\bigcup_{n=0}^{\infty}A_{n}$，其中 $\mu_{0}(A_{j})<+\infty$ 且可以设其互不相交，则对任意 $E \in \mathcal{M}$ 有

$$
\mu(E)=\sum_{n=0}^{\infty} \mu(E\cap A_{n})=\sum_{n=0}^{\infty} \nu(E\cap A_{n})=\nu(E)
$$

这就完成了证明。

根据上述定理的证明，我们可以更进一步，把 $\mu_{0}$ 扩展到所有 $\mu^{*}$-可测集构成的 $\sigma$-代数 $\mathcal{M}^{*}$ 上。

最后，我们来证明内外测度相等与 Caratheodory 条件的等价性，首先我们需要以下引理：

**引理 20.3.8**

设 $X$ 是一个集合，$\mathcal{A}$ 是 $X$ 上的代数，$\mu_{0}$ 是 $\mathcal{A}$ 上的预测度，$\mu^{*}$ 是 $\mu_{0}$ 诱导的外测度，那么有：

1. 对任意 $E\subset X$ 和 $\varepsilon>0$，存在 $A \in \mathcal{A}_{\sigma}$ 使得 $E\subset A$ 且 $\mu^{*}(A)\leq \mu^{*}(E)+\varepsilon$
2. 如果 $\mu^{*}(E)<+\infty$，那么 $E$ 是 $\mu^{*}$-可测的当且仅当存在 $B \in \mathcal{A}_{\sigma\delta}$ 使得 $E\subset B$ 且 $\mu^{*}(B\setminus E)=0$
3. 如果 $\mu_{0}$ 是 $\sigma$-有限的，那么 2 中的条件 $\mu^{*}(E)<+\infty$ 是多余的。

**证明**

设 $E\subset X$，则存在 $\mathcal{A}$ 中的集合 $(A_{n})_{n=0}^{\infty}$ 使得 $\sum_{n=0}^{\infty}\mu_{0}(A_{n})\leq \mu^{*}(E)+\varepsilon$，设 $A=\bigcup_{n=0}^{\infty}A_{n}\in \mathcal{A}_{\sigma}$，由于 $\mu^{*}$ 限制在 $\mathcal{A}$ 生成的 $\sigma$-代数 $\mathcal{M}$ 上是一个测度，并且 $\mu^{*}|_{\mathcal{A}}=\mu_{0}$，故 $\mu^{*}(A)\leq \sum_{n=0}^{\infty}\mu^{*}(A_{n})=\sum_{n=0}^{\infty}\mu_{0}(A_{n})$，这就证明了 1.

设 $\mu^{*}(E)<+\infty$，如果 $E$ 是 $\mu^{*}$-可测的，则对任意正整数 $n$，存在 $A_{n}\in \mathcal{A}_{\sigma}$ 使得 $\mu^{*}(A_{n})\leq \mu^{*}(E)+ \dfrac{1}{n}$ 且 $E\subset A_{n}$，取 $B=\bigcap_{n=1}^{\infty}A_{n}\in \mathcal{A}_{\sigma\delta}$，则 $E\subset B$，并且 $\mu^{*}(B)\leq \mu^{*}(A_{n})\leq \mu^{*}(E)+\dfrac{1}{n}$，即 $\mu^{*}(B\setminus E)\leq \dfrac{1}{n}$，从而 $\mu^{*}(B\setminus E)=0$.

反之，由于 $B \in \mathcal{M}$，故 $B$ 是 $\mu^{*}$-可测的，并且零测集 $B\setminus E$ 也是 $\mu^{*}$-可测的，从而 $E=B\setminus(B\setminus E)$ 是 $\mu^{*}$-可测的。

现在设 $\mu_{0}$ 是 $\sigma$-有限的，假设 $E$ 是 $\mu^{*}$-可测的，那么存在不相交的集合 $(X_{n})_{n=0}^{\infty}$ 使得 $X=\bigcup_{n=0}^{\infty}X_{n}$，且 $\mu_{0}(X_{n})<+\infty$. 令 $E_{n}=E\cap X_{n}$，利用 1 得到集合 $A_{nk}\in \mathcal{A}_{\sigma}$ 使得 $\mu^{*}(A_{nk})\leq \mu^{*}(E_{n})+\dfrac{1}{2^{nk}}$，并且 $E_{n}\subset A_{nk}$. 令 $A_{k}=\bigcup_{n=0}^{\infty}A_{nk}\in \mathcal{A}_{\sigma}$，则 $\mu^{*}(A_{k})\leq \mu^{*}(E)+\dfrac{1}{2^{k-1}}$，且 $E_{n}\subset A_{k}$.

设 $B=\bigcap_{k=0}^{\infty}A_{k}\in \mathcal{A}_{\sigma\delta}$，则 $E\subset B$. 令 $B_{n}=B\cap X_{n}$，则

$$
\mu^{*}(B_{n}\setminus E)=\lim_{ k \to \infty } \mu^{*}((A_{k}\cap X_{n})\setminus E)\leq \lim_{ k \to \infty } \mu^{*}(A_{k}\setminus E)=0
$$

故 $\mu^{*}(B\setminus E)\leq \sum_{n=0}^{\infty}\mu^{*}(B_{n}\setminus E)=0$. 反方向的证明不需要用到 $\mu^{*}(E)<+\infty$ 的条件，因此仍然成立，这就完成了证明。

**定理 20.3.9**

设 $X$ 是集合，$\mathcal{A}$ 是 $X$ 上的代数，$\mu_{0}$ 是 $\mathcal{A}$ 上的有限预测度，$\mu^{*}$ 是 $\mu_{0}$ 诱导的外测度，定义**内测度**为 $\mu_{*}(E)=\mu_{0}(X)-\mu^{*}(E^{c})$，那么 $E$ 是 $\mu^{*}$-可测的当且仅当 $\mu^{*}(E)=\mu_{*}(E)$.

**证明**

设 $E$ 是 $\mu^{*}$-可测的，则有

$$
\mu_{0}(X)=\mu^{*}(X)=\mu^{*}(X\cap E)+\mu^{*}(X\cap E^{c})=\mu^{*}(E)+\mu^{*}(E^{c})
$$

即 $\mu^{*}(E)=\mu_{*}(E)$. 反之，设 $\mu^{*}(E)=\mu_{*}(E)$，则对任意 $n\geq 1$，存在 $A_{n}\in \mathcal{A}_{\sigma}$ 使得 $E\subset A_{n}$ 且 $\mu^{*}(A_{n})\leq \mu^{*}(E)+\dfrac{1}{n}$，令 $B=\bigcap_{n=1}^{\infty}A_{n}\in \mathcal{A}_{\sigma\delta}$，则 $E\subset B$，并且 $\mu^{*}(B)\leq \mu^{*}(A_{n})\leq \mu^{*}(E)+\dfrac{1}{n}$，从而 $\mu^{*}(B)= \mu^{*}(E)$. 由于 $B$ 是 $\mu^{*}$-可测的，故

$$
\mu^{*}(E^{c})=\mu^{*}(E^{c}\cap B)+\mu^{*}(E^{c}\cap B^{c})=\mu^{*}(B\setminus E)+\mu^{*}(B^{c})
$$

此外，我们还有

$$
\mu^{*}(B^{c})=\mu^{*}(X)-\mu^{*}(B)=\mu^{*}(X)-\mu_{*}(E)=\mu^{*}(E^{c})
$$

从而 $\mu^{*}(B\setminus E)=0$，根据引理 20.3.8，$E$ 是 $\mu^{*}$-可测的，这就完成了证明。

这样，我们就证明了“内外测度相等”与 Caratheodory 条件的等价性，这也是 Lebesgue 最初定义测度时使用的定义。然而，Lebesgue 的定义比起 Caratheodory 条件要更复杂，并且对于 $\mu_{0}(X)=+\infty$ 的情况要分开讨论。因此，我们一般都使用 Caratheodory 条件作为可测的定义。

# Section 4: Borel 测度与 Lebesgue 测度

现在，我们就可以来构造 $\mathbb{R}$ 上的测度了，我们首先将讨论一类定义在 $\mathcal{B}_{\mathbb{R}}$ 上的测度，称为 **Borel 测度**，然后，我们将对 Borel 测度进行完备化，以得到最终的目标，即 **Lebesgue 测度**。

为了阐明下面的构造的动机，我们首先从结果反推回来，看看我们需要的概念有哪些。设 $\mu$ 是一个有限 Borel 测度，令 $F(x)=\mu((-\infty,x])$（$F$ 称为 $\mu$ 的**分布函数**），则 $F$ 是一个单调递增并且右连续的函数：前者由测度的单调性推出，后者我们可以取从右边收敛于 $x$ 的序列 $(x_{n})$，于是有 $(-\infty,x]=\bigcap_{n=0}^{\infty}(-\infty,x_{n}]$，根据测度的连续性即证。此外，对于 $a<b$，我们有 $\mu((-\infty,a])+\mu((a,b])=\mu(-\infty,b]$，故 $\mu((a,b])=F(b)-F(a)$.

因此，我们要做的，就是从一个单调递增并且右连续的函数 $F$ 出发，构造出满足 $\mu((a,b])=F(b)-F(a)$ 的 Borel 测度 $\mu$. 特别地，当 $F(x)=x$ 时，该测度就与区间的长度保持一致。

由上面的讨论可知，我们的理论的基础结构就是左开右闭的区间，包括 $\varnothing,(a,b],(-\infty,b],(a,+\infty),\mathbb{R}$. 显然，两个半开区间的交集也是半开区间，并且一个半开区间的补集是有限个半开区间的无交并。因此，半开区间构成的集合 $\mathcal{E}$ 是一个基本族（见定义 20.1.13），由定理 20.1.14 知，有限个半开区间的无交并构成的集合 $\mathcal{A}$ 是一个代数，再由定理 20.1.4 知，$\mathcal{A}$ 生成的 $\sigma$-代数就是 $\mathcal{B}_{\mathbb{R}}$.

为了构造 $\mathcal{B}_{\mathbb{R}}$ 上的测度，我们可以先在 $\mathcal{A}$ 上定义预测度，然后利用 Caratheodory 扩张定理得到 $\mathcal{B}_{\mathbb{R}}$ 上的测度。

**引理 20.4.1**

设函数 $F\colon \mathbb{R}\to \mathbb{R}$ 单调递增且右连续，如果 $(a_{j},b_{j}],1\leq j\leq n$ 是不相交的半开区间，定义

$$
\mu_{0}\left( \bigcup_{j=1}^{n} (a_{j},b_{j}] \right)=\sum_{j=1}^{n} (F(b_{j})-F(a_{j}))
$$

并且 $\mu_{0}(\varnothing)=0$，那么 $\mu_{0}$ 是 $\mathcal{A}$ 上的预测度。

**证明**

首先我们证明 $\mu_{0}$ 是良定的。设 $((a_{j},b_{j}])_{j=1}^{n}$ 是不相交的非空半开区间，并且 $\bigcup_{j=1}^{n}(a_{j},b_{j}]=(a,b]$，那么经过重新编号后一定有

$$
a=a_{1}<b_{1}=a_{2}<b_{2}=\dots<b_{n}=b
$$

从而 $\mu_{0}\left( \bigcup_{j=1}^{n}(a_{j},b_{j}] \right)=\sum_{j=1}^{n}(F(b_{j})-F(a_{j}))=F(b)-F(a)$. 类似地，如果 $(I_{k})_{k=1}^{n},(J_{k})_{k=1}^{m}$ 都是不相交的非空半开区间，并且 $\bigcup_{k=1}^{n}I_{k}=\bigcup_{k=1}^{m}J_{k}$，那么有

$$
\mu_{0}\left( \bigcup_{k=1}^{n} I_{k} \right)=\sum_{k=1}^{n} \mu_{0}(I_{k})=\sum_{i,j} \mu_{0}(I_{i}\cap J_{j})=\sum_{k=1}^{m} \mu_{0}(J_{k})=\mu_{0}\left( \bigcup_{k=1}^{m} J_{k} \right)
$$

因此 $\mu_{0}$ 是良定的，并且根据定义，它是有限可加的。下面我们要证当 $\bigcup_{j=0}^{\infty}I_{j}\in \mathcal{A}$ 时有 $\mu_{0}\left( \bigcup_{j=0}^{\infty}I_{j} \right)=\sum_{j=0}^{\infty}\mu_{0}(I_{j})$，其中 $I_{j}$ 是不相交的。

由于 $\bigcup_{j=0}^{\infty}I_{j}$ 是有限个半开区间的无交并，因此它可以分成有限个子序列，每个子序列的并是单个半开区间，分别考虑每个子序列然后使用 $\mu_{0}$ 的有限可加性即证。因此我们可以假设 $\bigcup_{j=1}^{\infty}I_{j}=I=(a,b]$，首先我们有

$$
\mu_{0}(I)\geq \mu_{0}\left( \bigcup_{j=1}^{n} I_{j} \right)=\sum_{j=1}^{n} \mu_{0}(I_{j})
$$

对所有 $n$ 成立，令 $n\to \infty$ 即得 $\mu_{0}(I)\geq \sum_{j=1}^{\infty}\mu_{0}(I_{j})$. 对于反方向的不等式，我们首先设 $a,b$ 都是有限的，取 $\varepsilon>0$，由于 $F$ 右连续，故存在 $\delta>0$ 使得 $F(a+\delta)-F(a)<\varepsilon$，设 $I_{j}=(a_{j},b_{j}]$，那么存在 $\delta_{j}>0$ 使得 $F(b_{j}+\delta_{j})-F(b_{j})<\dfrac{\varepsilon}{2^{j}}$.

由于开区间 $(a_{j},b_{j}+\delta_{j})$ 覆盖了紧致集 $[a+\delta,b]$，因此存在一个有限子覆盖，通过把包含在其它区间内部的开区间去除，并重新编号，我们可以假设：$(a_{1},b_{1}+\delta_{1}),\dots,(a_{n},b_{n}+\delta_{n})$ 覆盖 $[a+\delta,b]$，并且对 $1\leq j\leq n-1$ 有 $b_{j}+\delta_{j}\in(a_{j+1},b_{j+1}+\delta_{j+1})$，此时我们有

$$
\begin{align}
\mu_{0}(I) &< F(b)-F(a+\delta)+\varepsilon \\
&\leq \sum_{j=1}^{n} (F(b_{j}+\delta_{j})-F(a_{j}))+\varepsilon \\
&< \sum_{j=1}^{n} \left( F(b_{j})-F(a_{j})+ \dfrac{\varepsilon}{2^{j}} \right)+\varepsilon \\
&< \sum_{j=1}^{\infty} \mu_{0}(I_{j})+2\varepsilon
\end{align}
$$

根据 $\varepsilon$ 的任意性即证。当 $a=-\infty$ 时，对任意 $M>0$，区间 $(a_{j},b_{j}+\delta_{j})$ 覆盖了紧致集 $[-M,b]$，同理有 $F(b)-F(-M)\leq \sum_{j=1}^{\infty}\mu_{0}(I_{j})+2\varepsilon$. 当 $b=+\infty$ 时，同理也有 $F(M)-F(a)\leq \sum_{j=1}^{\infty}\mu_{0}(I_{j})+2\varepsilon$，令 $M\to +\infty$ 就完成了证明。

现在我们有了代数上的预测度，下面我们就可以将其扩张至 $\mathcal{B}_{\mathbb{R}}$ 上，如下所示：

**定理 20.4.2**

如果函数 $F\colon \mathbb{R}\to \mathbb{R}$ 单调递增且右连续，那么存在唯一的 $\mathbb{R}$ 上的 Borel 测度 $\mu_{F}$ 使得对任意 $a<b$ 有 $\mu_{F}((a,b])=F(b)-F(a)$. 如果 $G$ 是另一个这样的函数，那么 $\mu_{F}=\mu_{G}$ 当且仅当 $F-G$ 是常值函数。相反，如果 $\mu$ 是 $\mathbb{R}$ 上的一个 Borel 测度，并且在所有有界的 Borel 集上有限，定义

$$
F(x)=\begin{cases}
\mu((0,x]) &, x>0 \\
0 &, x=0 \\
-\mu((0,-x]) &, x<0
\end{cases}
$$

那么 $F$ 是单调递增且右连续的，并且 $\mu=\mu_{F}$.

**证明**

根据引理 20.4.1，每个 $F$ 都诱导了 $\mathcal{A}$ 上的一个预测度，并且 $F,G$ 诱导了同一个预测度当且仅当 $F-G$ 是常值函数，根据 Caratheodory 扩张定理以及 $\mu_{0}$ 是 $\sigma$-有限的事实（$\mathbb{R}=\bigcup_{j=-\infty}^{\infty}(j,j+1]$），我们就证明了前两个断言。

反之，根据测度 $\mu$ 的单调性和连续性我们可以证明 $F$ 的单调性和连续性。在 $\mathcal{A}$ 上，我们可以验证 $\mu((a,b])=F(b)-F(a)=\mu_{F}((a,b])$，即 $\mu|_{\mathcal{A}}=\mu_{F}|_{\mathcal{A}}$，根据 Caratheodory 扩张定理就有 $\mu=\mu_{F}$，这就完成了证明。

有几点事项需要注意：第一，上述理论也可以使用左闭右开的区间 $[a,b)$ 和左连续的函数 $F$ 来建立，得到的结论是一样的。第二，根据 Caratheodory 定理，我们实际上可以得到一个完备测度 $\overline{\mu}_{F}$，其定义域包含了 $\mathcal{B}_{\mathbb{R}}$，并且比它更大。事实上，$\overline{\mu}_{F}$ 正是 $\mu_{F}$ 的完备化，下面我们就来证明这一点。

**定理 20.4.3**

设 $(X,\mathcal{M},\mu)$ 是测度空间，$\mu^{*}$ 是 $\mu$ 诱导的外测度，$\mathcal{M}^{*}$ 是所有 $\mu^{*}$-可测集构成的 $\sigma$-代数，定义 $\overline{\mu}=\mu^{*}|_{\mathcal{M}^{*}}$，如果 $\mu$ 是 $\sigma$-有限的，那么 $\overline{\mu}$ 是 $\mu$ 的完备化。

**证明**

我们要证 $\overline{\mathcal{M}}=\mathcal{M}^{*}$，从而根据定理 20.2.8 即证。设 $E\cup F \in \overline{\mathcal{M}}$，其中 $E \in \mathcal{M},F\subset N \in \mathcal{M}$，且 $\mu(N)=0$，令 $B=E\cup N \in \mathcal{M}$，则 $E\cup F\subset B$ 并且 $\mu^{*}(B\setminus(E\cup F))=\mu^{*}(N\setminus F)=0$，根据引理 20.3.8 知 $E\cup F \in \mathcal{M}^{*}$.

反之，设 $E \in \mathcal{M}^{*}$，根据引理 20.3.8，存在 $B \in \mathcal{M}$ 使得 $E\subset B$ 且 $\mu^{*}(B\setminus E)=0$，根据 $\mu^{*}$ 的定义，对任意 $n$ 有 $C_{n}\in \mathcal{M}$ 使得 $\mu(C_{n})\leq \dfrac{1}{n}$ 且 $B\setminus E\subset C_{n}$，令 $C=\bigcap_{n=1}^{\infty}C_{n}$，则 $B\setminus E\subset C$ 且 $\mu(C)=0$.

设 $B'=B\setminus C \in \mathcal{M}$，则 $B'\subset E$，并且 $E\setminus B'\subset B\setminus B'=C$，从而 $E=B'\cup(E\setminus B')\in \overline{\mathcal{M}}$，这就完成了证明。

我们将仍然把这个完备度量记作 $\mu_{F}$，称为关于 $F$ 的 **Lebesgue-Stieltjes 测度**。

下面，我们来研究 Lebesgue-Stieltjes 测度的相关性质。对于这样的一个测度 $\mu$，我们把 $\mu$ 的定义域记作 $\mathcal{M}_{\mu}$，因此，对任意 $E \in \mathcal{M}_{\mu}$ 有

$$
\mu(E)=\inf \left\{  \sum_{j=0}^{\infty} \mu((a_{j},b_{j}]) \middle| E \subset \bigcup_{j=0}^{\infty} (a_{j},b_{j}]  \right\}
$$

我们首先注意到，在上述公式中我们可以将半开区间换成开区间：

**引理 20.4.4**

设 $\mu$ 是一个 Lebesgue-Stieltjes 测度，那么对任意 $E \in \mathcal{M}_{\mu}$ 有

$$
\mu(E)=\inf \left\{  \sum_{j=0}^{\infty} \mu((a_{j},b_{j})) \middle| E\subset \bigcup_{j=0}^{\infty} (a_{j},b_{j})  \right\}
$$

**证明**

我们将等式右边的项记作 $\nu(E)$，设 $E\subset \bigcup_{j=1}^{\infty}(a_{j},b_{j})$，由于每个 $(a_{j},b_{j})$ 都是半开区间的可数并，故存在 $(I_{jk})_{k=1}^{\infty}$ 使得 $(a_{j},b_{j})=\bigcup_{k=1}^{\infty}I_{jk}$，从而

$$
\sum_{j=1}^{\infty} \mu((a_{j},b_{j}))=\sum_{j,k=1}^{\infty} \mu(I_{jk})\geq \mu(E)
$$

即 $\nu(E)\geq \mu(E)$. 反之，任取 $\varepsilon>0$，存在 $((a_{j},b_{j}])_{j=1}^{\infty}$ 使 $E\subset \bigcup_{j=1}^{\infty}(a_{j},b_{j}]$ 并且 $\sum_{j=1}^{\infty}\mu((a_{j},b_{j}])\leq \mu(E)+\varepsilon$. 对任意 $j$，还存在 $\delta_{j}>0$ 使得 $F(b_{j}+\delta_{j})-F(b_{j})<\dfrac{\varepsilon}{2^{j}}$，从而 $E\subset \bigcup_{j=1}^{\infty}(a_{j},b_{j}+\delta_{j})$，而且有

$$
\sum_{j=1}^{\infty} \mu((a_{j},b_{j}+\delta_{j}))<\sum_{j=1}^{\infty} \mu((a_{j},b_{j}])+\varepsilon\leq \mu(E)+2\varepsilon
$$

从而 $\nu(E)\leq \mu(E)$，这就完成了证明。

利用上述引理，我们可以给出一个常用的计算方法。

**定理 20.4.5**

设 $\mu$ 是一个 Lebesgue-Stieltjes 测度，那么对任意 $E \in \mathcal{M}_{\mu}$ 有

$$
\begin{align}
\mu(E) &= \inf \{ \mu(U) \mid U \supset E, U \text{是开集} \} \\
&= \sup \{ \mu(K) \mid K \subset E, K\text{是紧致集} \}
\end{align}
$$

**证明**

设开集 $U\supset E$，则 $\mu(E)\leq \mu(U)$，反之，根据引理 20.4.4，任取 $\varepsilon>0$，存在 $((a_{j},b_{j}))_{j=1}^{\infty}$ 使得 $\sum_{j=1}^{\infty}\mu((a_{j},b_{j}))\leq \mu(E)+\varepsilon$，令 $U=\bigcup_{j=1}^{\infty}(a_{j},b_{j})$，则 $U$ 是开集并且 $\mu(U)\leq \mu(E)+\varepsilon$，这就证明了第一个等式。

对于第二个等式，首先设 $E$ 是有界的，如果 $E$ 是闭集，那么 $E$ 是紧致的，等式显然成立。如果 $E$ 不是闭集，由于集合 $\overline{E}\setminus E$ 是闭集，因此在 $\mathcal{B}_{\mathbb{R}}\subset \mathcal{M}_{\mu}$ 内，故任取 $\varepsilon>0$，存在开集 $U\supset \overline{E}\setminus E$ 使得 $\mu(U)\leq \mu(\overline{E}\setminus E)+\varepsilon$，令 $K=\overline{E}\setminus U$ 是紧致集，且 $K\subset E$，并且

$$
\begin{align}
\mu(K) &\geq \mu(E)-\mu(E\cap U)=\mu(E)-(\mu(U)-\mu(U\setminus E)) \\
&\geq \mu(E)-\mu(U)+\mu(\overline{E}\setminus E)\geq \mu(E)-\varepsilon
\end{align}
$$

如果 $E$ 不是有界的，令 $E_{j}=E\cap(j,j+1]$，根据上面的论述，对每个 $j$ 都有紧致集 $K_{j}\subset E_{j}$ 使得 $\mu(K_{j})\geq \mu(E_{j})-\dfrac{\varepsilon}{2^{|j|}}$. 令 $H_{n}=\bigcup_{j=-n}^{n}K_{j}$，则 $H_{n}$ 是紧致的，且 $H_{n}\subset E$，并且 $\mu(H_{n})\geq \mu\left( \bigcup_{j=-n}^{n}E_{j} \right)-3\varepsilon$，令 $n\to \infty$ 就完成了证明。

下面的定理给出了一种判断可测性的方法。

**定理 20.4.6**

设 $\mu$ 是一个 Lebesgue-Stieltjes 测度，$E\subset \mathbb{R}$，则以下命题等价：

1. $E \in \mathcal{M}_{\mu}$
2. $E=V\setminus N$，其中 $V$ 是一个 $G_{\delta}$ 集，$\mu(N)=0$
3. $E=H\cup N$，其中 $H$ 是一个 $F_{\sigma}$ 集，$\mu(N)=0$

**证明**

显然 2 和 3 蕴含 1，因为 $\mu$ 是完备的。设 $E \in \mathcal{M}_{\mu}$ 且 $\mu(E)<+\infty$，根据定理 20.4.5，对任意 $j$ 我们有开集 $U_{j}$ 和紧致集 $K_{j}$ 使得 $K_{j}\subset E\subset U_{j}$ 并且

$$
\mu(E)- \dfrac{1}{j}\leq\mu(K_{j})\leq \mu(E)\leq \mu(U_{j})\leq \mu(E)+ \dfrac{1}{j}
$$

令 $V=\bigcap_{j=1}^{\infty}U_{j},H=\bigcup_{j=1}^{\infty}K_{j}$，则 $H\subset E\subset V$ 且 $\mu(H)=\mu(E)=\mu(V)$，从而 $\mu(V\setminus E)=\mu(E\setminus H)=0$.

当 $\mu(E)=+\infty$ 时，令 $E_{j}=E\cap(j,j+1]$，对每个 $j$，有 $F_{\sigma}$ 集 $H_{j}$ 使得 $E_{j}=H_{j}\cup N_{j}$，于是 $E=\left( \bigcup_{j=-\infty}^{\infty}H_{j} \right) \cup \left( \bigcup_{j=-\infty}^{\infty}N_{j} \right)$，其中 $\bigcup_{j=-\infty}^{\infty}H_{j}$ 仍然是 $F_{\sigma}$ 集，而 $\mu\left( \bigcup_{j=-\infty}^{\infty}N_{j} \right)=\sum_{j=-\infty}^{\infty}\mu(N_{j})=0$.

同样，对每个 $j$，存在开集 $U_{jk}\supset E_{j}$ 使得 $\mu(U_{jk})\leq \mu(E_{j})+ \dfrac{1}{k 2^{|j|}}$，从而 $\mu(U_{jk}\setminus E)\leq \mu(U_{jk}\setminus E_{j}) \leq \dfrac{1}{k 2^{|j|}}$. 令 $U_{k}=\bigcup_{j=-\infty}^{\infty}U_{jk}$，则 $\mu(U_{k}\setminus E)\leq \dfrac{3}{k}$，取 $V=\bigcap_{k=1}^{\infty}U_{k}$，则 $V$ 是 $G_{\delta}$ 集，并且 $\mu(V\setminus E)=0$，即证。

上述定理表明，一个可测集的结构（在除去某个零测集后）是相对简单的，这也从侧面说明了零测集可以具有非常复杂的拓扑结构。下面的定理是可测集的简单性的另一种体现方式。

**定理 20.4.7**

设 $\mu$ 是一个 Lebesgue-Stieltjes 测度，如果 $E \in \mathcal{M}_{\mu}$ 且 $\mu(E)<+\infty$，那么对任意 $\varepsilon>0$，存在有限个开区间的并集 $A$ 使得 $\mu(E\Delta A)<\varepsilon$. 其中 $E\Delta A=(E\setminus A)\cup(A\setminus E)$ 是对称差。

**证明**

根据定理 20.4.5，存在开集 $U$ 和紧致集 $K$ 使得 $K\subset E\subset U$，并且

$$
\mu(E)-\dfrac{\varepsilon}{3}\leq \mu(K)\leq \mu(E)\leq \mu(U)\leq \mu(E)+\dfrac{\varepsilon}{3}
$$

根据引理 20.1.5，$U$ 是至多可数个开区间的无交并，并且这些开区间覆盖了紧致集 $K$，从而可以选取有限个开区间覆盖 $K$，这些开区间的并集记作 $A$，则有

$$
\mu(E)-\dfrac{\varepsilon}{3}\leq \mu(K)\leq \mu(A)\leq \mu(U)\leq \mu(E)+\dfrac{\varepsilon}{3}
$$

于是

$$
\begin{gather}
\mu(A\setminus E)\leq \mu(U\setminus E)=\mu(U)-\mu(E)\leq \dfrac{\varepsilon}{3} \\
\mu(E\setminus A)\leq \mu(E\setminus K)=\mu(E)-\mu(K)\leq \dfrac{\varepsilon}{3}
\end{gather}
$$

故 $\mu(E\Delta A)=\mu(A\setminus E)+\mu(E\setminus A)\leq \dfrac{2\varepsilon}{3}<\varepsilon$，这就完成了证明。

最后，我们来给出 $\mathbb{R}$ 上最重要的测度，即 **Lebesgue 测度**。它是关于函数 $F(x)=x$ 的 Lebesgue-Stieltjes 测度，其中区间的测度就等于它的长度，我们将其记作 $m$，并把它的定义域，即 **Lebesgue 可测集**，记作 $\mathcal{L}$. 通常我们也把 $m$ 在 $\mathcal{B}_{\mathbb{R}}$ 上的限制称为 Lebesgue 测度。

Lebesgue 测度拥有 Lebesgue-Stieltjes 测度的一切性质，它的特殊性体现在它关于平移的不变性以及关于伸缩的行为上。

**定理 20.4.8**

设 $E \in \mathcal{L}$，$s,r \in \mathbb{R}$，定义

$$
E+s=\{ x+s \mid x \in E \},rE=\{ rx \mid x \in E \}
$$

那么 $E+s \in \mathcal{L},rE \in \mathcal{L}$，并且 $m(E+s)=m(E),m(rE)=|r|m(E)$.

**证明**

由于开区间平移和伸缩后仍然是开区间，又因为开区间生成了 $\mathcal{B}_{\mathbb{R}}$，故 Borel 集在平移和伸缩后仍然是 Borel 集。设 $m_{s}(E)=m(E+s)$，$m^{r}(E)=m(rE)$，那么 $m_{s},m^{r}$ 在有限个半开区间的并集构成的代数 $\mathcal{A}$ 上与 $m$ 和 $|r|m$ 相等，根据 Caratheodory 扩张定理，它们在 $\mathcal{B}_{\mathbb{R}}$ 上也相等。

特别地，设 $E \in \mathcal{B}_{\mathbb{R}}$ 且 $m(E)=0$，则有 $m(E+s)=m(rE)=0$，这表明所有的 Lebesgue 零测集在平移和伸缩下仍然是零测集，由于 $\mathcal{L}$ 中的元素可以写成一个 Borel 集与一个零测集的并，故 $\mathcal{L}$ 中的元素经过平移和伸缩仍然是 $\mathcal{L}$ 中的元素，由完备性知 $m(E+s)=m(E),m(rE)=|r|m(E)$.

一个集合的拓扑性质与测度性质有时可以变得非常不同。例如，每个至多可数的集合都具有 Lebesgue 测度零，考虑其外测度：对于有限集，可以使用开区间 $B(x_{j},\varepsilon / n)$ 来覆盖，令 $\varepsilon\to 0$ 即得 $m^{*}(E)=0$. 对于可数集，我们可以用 $B(x_{j},\varepsilon / 2^{j})$，所有这些开区间的长度之和为 $\varepsilon$，根据 $\varepsilon$ 的任意性可得 $m^{*}(E)=0$. 特别地，$m(\mathbb{Q})=0$，尽管它在 $\mathbb{R}$ 上是稠密的。

除了可数集外，还有一些不可数集也具有 Lebesgue 测度零，最典型的例子就是 Cantor 三分集，它是零测集，然而却是不可数的。