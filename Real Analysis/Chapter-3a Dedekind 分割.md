我们首先明确一下我们要达到的目标：以有理数为起点，证明实数的存在性，即：

**定理**

存在一个 Archimedes 序域，我们称为实数，它满足确界性质，并且包含有理数作为它的子域。

本章中，我们将使用 Dedekind 的方法证明上述定理。

# 分割

Dedekind 分割法基于所谓**分割**的概念，一种特殊的有理数的子集，定义如下：

**定义 1** 分割（cut）

有理数的子集 $\alpha$ 是一个**分割**如果：

1. $\alpha\neq \varnothing$ 且 $\alpha\neq \mathbb{Q}$
2. 如果 $r\in\alpha$，那么对任意 $q<r$ 有 $q\in\alpha$
3. 如果 $r \in\alpha$，那么存在 $s \in\alpha$ 使得 $r<s$

> 先验地看，一个分割就相当于区间 $(-\infty,x)\cap \mathbb{Q}$.

实数则被定义为所有分割所构成的集合：

$$
\mathbb{R}=\{ \alpha \in\mathscr{P}(\mathbb{Q}) \mid \alpha \text{是一个分割} \}
$$

# 序关系

根据我们的直观想法，$\mathbb{R}$ 上的序应该定义如下：

**定义 2** $\mathbb{R}$ 上的序

设 $\alpha,\beta \in \mathbb{R}$，则定义 $\mathbb{R}$ 上的序为

$$
\alpha < \beta \iff \alpha \subsetneq \beta
$$

读者可以自行验证 $<$ 满足传递性和三分律，这表明 $\mathbb{R}$ 是一个有序集。

下面我们验证 $\mathbb{R}$ 具有确界性质。

**定理 3** $\mathbb{R}$ 的上确界性质

设 $E \subset \mathbb{R},E\neq \varnothing$，$E$ 在 $\mathbb{R}$ 中有上界，则 $E$ 在 $\mathbb{R}$ 中有唯一上确界。

**证明**

唯一性我们已经证过了，现在来证存在性。

令 $\gamma=\bigcup E$，由于 $E$ 非空，于是有 $\alpha \subset\gamma$，即 $\gamma\neq \varnothing$. $E$ 有上界 $\beta$，故 $\gamma \subset\beta$，则 $\gamma\neq \mathbb{Q}$. 

设 $r\in\gamma$，则有 $\alpha \in E$ 使得 $r\in\alpha$，任取 $q<r$，则 $q\in\alpha$，从而 $q\in\gamma$.

对于上述的 $r$，存在 $s \in\alpha$ 使得 $r<s$，又 $s \in\gamma$，这就证明了 $\gamma$ 是一个分割。

显然 $\gamma$ 是 $E$ 的一个上界，设 $\delta<\gamma$，则存在 $r \in\gamma$ 使得 $r \not\in\delta$. 根据 $\gamma$ 的定义，存在 $\alpha \in E$ 使得 $r \in\alpha$，于是 $\delta<\alpha$，因此 $\delta$ 不是 $E$ 的上界。这就完成了证明。

# 加法

**定义 4** $\mathbb{R}$ 上的加法

设 $\alpha,\beta \in \mathbb{R}$，定义 $\mathbb{R}$ 上的**加法**为

$$
\alpha+\beta=\{ a+b \mid a \in\alpha,b \in\beta \}
$$

可以验证 $\alpha+\beta$ 是一个分割，并且加法满足交换律与结合律。

$\mathbb{R}$ 上的加法单位元为 $\overline{0}=\{ r \mid r<0 \}$，对于加法逆元，我们需要找到一个元素 $-\alpha$ 使得 $\alpha+(-\alpha)=\overline{0}$. 直观地来看，$-\alpha$ 应当包含所有小于 $-\sup \alpha$ 的有理数，但问题是如何不使用上确界来描述它（我们知道 $\mathbb{Q}$ 没有确界性质，而且现在还没有把 $\mathbb{Q}$ 嵌入 $\mathbb{R}$ 中）。

这里我们给出一种构造方法：

$$
-\alpha=\{ r \mid \exists t \not\in\alpha(t < -r) \}
$$

这可以由下图来说明：

![](https://picx.zhimg.com/v2-85f7f8aaca202641f9ef12b13831d3d5_1440w.jpg)

可以验证 $-\alpha$ 是一个分割，且 $\alpha+(-\alpha)=\overline{0}$.

结合序关系，我们可以验证 $<$ 的加法保序性。

# 乘法

相比加法，实数的乘法更为复杂，这是因为两个负数相乘后是正的。为了避免符号的影响，我们首先定义正数的乘法：

**定义 5** $\mathbb{R}$ 上的乘法

设 $\alpha,\beta \in \mathbb{R},\alpha,\beta\geq \overline{0}$，定义 $\mathbb{R}$ 上的**乘法**为

$$
\alpha \cdot\beta=\{ ab \mid a \in\alpha,b \in\beta,a,b\geq 0 \}\cup \{ q \mid q<0 \}
$$

再设 $\alpha,\beta \in \mathbb{R}$，定义 $\mathbb{R}$ 上的**乘法**为

$$
\alpha \cdot\beta=\begin{cases}
\alpha \cdot\beta &, \alpha\geq \overline{0},\beta\geq \overline{0} \\
-(\alpha \cdot(-\beta)) &, \alpha\geq \overline{0},\beta<\overline{0} \\
-((-\alpha)\cdot\beta) &, \alpha<\overline{0},\beta\geq \overline{0} \\
(-\alpha)\cdot(-\beta) &, \alpha<\overline{0},\beta<\overline{0}
\end{cases}
$$

分别讨论不同符号下的乘法，我们可以验证实数的乘法满足交换律、结合律以及分配律。

实数上的乘法单位元是 $\overline{1}=\{ r \mid r<1 \}$，对于 $\alpha> \overline{0}$，其乘法逆元可以取

$$
\alpha^{-1}=\left\{ \dfrac{1}{a} \mid a \in\alpha,a>0 \right\} \cup \{ q \mid q\leq 0 \}
$$

对于 $\alpha<\overline{0}$，可以取 $\alpha^{-1}=-(-\alpha)^{-1}$.

最后，我们可以验证 $<$ 的乘法保序性。

这就给出了以下定理：

**定理 6**

四元组 $(\mathbb{R},+,\cdot,<)$ 是一个序域。

# 有理数的同构嵌入

考虑如下的有理分割

$$
\overline{q}= \{ r \mid r<q \}
$$

构成的集合 $\overline{\mathbb{Q}}$，可以验证其满足：

1. $\overline{p}+\overline{q}=\overline{p+q}$
2. $\overline{p}\cdot  \overline{q}=\overline{pq}$
3. $p<q \implies  \overline{p}<\overline{q}$

因此 $\overline{\mathbb{Q}}$ 构成了 $\mathbb{R}$ 的一个封闭子集，令 $f(q)=\overline{q}$，则 $f$ 将 $\mathbb{Q}$ 同构嵌入 $\mathbb{R}$.

最后我们再来验证 $\mathbb{R}$ 的 Archimedes 性，实际上它是确界性质的一个推论。

**定理 7** $\mathbb{R}$ 的 Archimedes 性

任取 $\alpha \in \mathbb{R}$，存在 $n \in \mathbb{N}$ 使得 $\alpha<n$.

**证明**

假设 $\mathbb{N}$ 在 $\mathbb{R}$ 中有上界，根据确界性质，存在 $\gamma=\sup \mathbb{N}$，于是对任意 $n \in \mathbb{N}$，有 $n\leq \gamma$. 由于 $\gamma$ 是最小上界，故 $\gamma-1$ 不是上界，即存在 $m \in \mathbb{N}$ 使得 $\gamma-1<m$，从而 $\gamma<m+1$，矛盾。

如此，我们就从有理数中构造出了实数。我们可以比较一下两种方法，它们的侧重各不相同：Cauchy 序列法更强调实数的代数运算（加法和乘法），这使得它能够直接继承有理数的代数性质，但是对于实数的序的处理比较繁琐；而 Dedekind 分割法更强调实数的序关系，这使得我们在定义了实数上的序之后直接证明实数具有确界性质，然而分割的不对称性使得我们在处理负数时不像 Cauchy 序列法那样简洁。

但总的来说，Cauchy 序列法是优于 Dedekind 分割法的，因为前者可以推广到更一般的**度量空间**上，作为完备化度量空间的一种方法，在那里，通常不会有像有理数那样的序关系。

尽管有不同的构造实数的方法，但我们可以证明：所有满足确界性质的 Archimedes 序域都是同构的。因此，一些教材中会使用公理法定义实数，即声称存在一个实数集满足以上性质。之后我们将证明这一点。