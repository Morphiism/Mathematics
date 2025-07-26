我们已经完成了单变量微积分全部内容的介绍，现在，我们想要将分析推广至其它的空间中，首先要推广的是“收敛”的概念。我们不仅需要对实数序列取极限，还需要对复数序列、向量序列、函数序列甚至序列的序列取极限，一种方法是对每一种对象分别定义收敛的概念，但这种方法很快就会让人感到枯燥乏味。一种更好的方法是，我们定义一种抽象的空间，使得实数、复数、向量以及函数都是这种空间的一种特例，然后我们在这种抽象空间上一次性地定义收敛的概念。

实际上，有两种满足条件的空间：**度量空间**以及**拓扑空间**，我们将着重介绍前者，因为实数分析的绝大多数概念可以直接推广到度量空间上，而拓扑空间我们只会做简要介绍。

# Section 1: 度量空间

简单来说，一个度量空间就是一个附带了**距离**的集合，其中，“距离”与我们日常生活中的距离不同，在数学中，“距离”是一个未定义项，就像现代数学中的几乎所有基础概念（例如“向量”“点”“直线”）一样，它的意义是隐含在限定它的公理中的，如下所示：

**定义 14.1.1** 度量空间（metric space）

**度量空间** $(X,d)$ 包含一个集合 $X$，其中的元素称为**点**，以及函数 $d\colon X^{2}\to \mathbb{R}$，称为 $X$ 上的**度量**，满足对任意 $x,y,z \in X$ 有：

- 正定性：如果 $x\neq y$，则 $d(x,y)>0$；$d(x,x)=0$
- 对称性：$d(x,y)=d(y,x)$
- 三角不等式：$d(x,y)\leq d(x,z)+d(z,y)$

如果度量 $d$ 是上下文自明的，那么可以将 $(X,d)$ 简写为 $X$.

显然，实数集 $\mathbb{R}$ 配上其**标准度量** $d(x,y)=|x-y|$ 是一个度量空间。如果没有特殊说明，那么我们总是使用标准度量作为 $\mathbb{R}$ 上的度量。

下面，我们考虑实数集 $\mathbb{R}$ 的自然推广：实数的 $n$ 元组构成的集合 $\mathbb{R}^{n}$，在其上可以定义许多不同的度量。

**定义 14.1.2** $l^{p}$ 度量，$l^{\infty}$ 度量

设 $n$ 是一个正整数，实数 $p\geq 1$，定义 $\mathbb{R}^{n}$ 上的 $l^{p}$ **度量**为

$$
d_{l^{p}}(x,y)=\left( \sum_{i=1}^{n} |x_{i}-y_{i}|^{p} \right)^{1/p}
$$

此外，定义 $\mathbb{R}^{n}$ 上的 $l^{\infty}$ **度量**为

$$
d_{l^{\infty}}(x,y)=\sup_{1\leq i\leq n} |x_{i}-y_{i}|
$$

通常，我们称 $l^{1}$ 度量为 Manhattan 距离，称 $l^{2}$ 度量为 Euclid 距离，并称 $(\mathbb{R}^{n},d_{l^{2}})$ 为 $n$ **维 Euclid 空间**。在没有特殊说明的情况下，我们总是使用 $l^{2}$ 度量作为 $\mathbb{R}^{n}$ 上的度量。

更进一步，在 $\mathbb{R}^{n}$ 上我们可以定义向量的加法和数乘（就像你在线性代数课程中看到的那样），从而 $\mathbb{R}^{n}$ 是 $\mathbb{R}$ 上的向量空间，如果再配上 Euclid 内积 $\langle u,v \rangle=\sum_{i=1}^{n}u_{i}v_{i}$，那么 $\mathbb{R}^{n}$ 就是 $\mathbb{R}$ 上的内积空间。从而我们的上一个系列：有限维向量空间就可以发挥它的作用，我们很快就会看到这一点。

在任意集合 $X$ 上，我们都可以定义一种平凡的度量：离散度量，如下所示：

**定义 14.1.3** 离散度量（discrete metric）

设 $X$ 是任意集合，定义函数 $d_{\mathrm{disc}}\colon X^{2}\to \mathbb{R}$ 如下：当 $x=y$ 时，定义 $d_{\mathrm{disc}}(x,y)=0$；当 $x\neq y$ 时，定义 $d_{\mathrm{disc}}(x,y)=1$，称为 $X$ 上的**离散度量**。

我们可以验证，$(X,d_{\mathrm{disc}})$ 是一个度量空间，从而任意集合上都有度量。下面，我们来证明 $l^{p},l^{\infty}$ 距离的确是 $\mathbb{R}^{n}$ 上的度量。

**定理 14.1.4**

设 $n$ 是一个正整数，实数 $p\geq 1$，则 $(\mathbb{R}^{n},d_{l^{p}})$ 与 $(\mathbb{R}^{n},d_{l^{\infty}})$ 是度量空间。

**证明**

首先，根据定义我们知道 $d_{l^{p}},d_{l^{\infty}}$ 满足正定性和对称性，因此我们只需证明三角不等式。

当 $p=1$ 时，$d_{l^{1}}(x,y)=\sum_{i=1}^{n}|x_{i}-y_{i}|$，由绝对值的三角不等式即证。

当 $p>1$ 时，由 Minkowski 不等式知，对任意 $a,b \in \mathbb{R}^{n}$ 有

$$
\left( \sum_{i=1}^{n}|a_{i}+b_{i}|^{p} \right)^{1/p}\leq \left( \sum_{i=1}^{n}|a_{i}|^{p} \right)^{1/p}+\left( \sum_{i=1}^{n}|b_{i}|^{p} \right)^{1/p}
$$

将 $a=x-z,b=z-y$ 代入即证（Minkowski 不等式的证明见附录）。

对于 $l^{\infty}$ 度量，由绝对值的三角不等式有

$$
|x_{i}-y_{i}|\leq |x_{i}-z_{i}|+|z_{i}-y_{i}|
$$

对右边取上确界有 $|x_{i}-y_{i}|\leq d_{l^{\infty}}(x,z)+d_{l^{\infty}}(z,y)$，再对左边取上确界即证。

下面，我们给出子空间的定义。

**定义 14.1.5** 子空间（subspace）

设 $(X,d)$ 是一个度量空间，$Y\subset X$，则称度量空间 $(Y,d|_{Y^{2}})$ 为由 $Y$ 导出的 $(X,d)$ 的**子空间**。

例如，在 Euclid 度量下，$\mathbb{R}^{2}$ 的子集 $\{ (x,0) \mid x \in \mathbb{R} \}$ 就可以导出 $\mathbb{R}^{2}$ 的子空间，事实上这个子空间与实数集 $\mathbb{R}$ 是同构的。

现在有了度量空间，我们就可以在上面定义序列收敛的概念。

**定义 14.1.6** 收敛（convergence）

设 $(X,d)$ 是一个度量空间，$(x^{(n)})_{n=0}^{\infty}$ 是 $X$ 中的点列，$x \in X$，称 $(x^{(n)})_{n=0}^{\infty}$ 按度量 $d$ **收敛于** $x$，如果 $\lim_{ n \to \infty }d(x^{(n)},x)=0$，记作 $\lim_{ n \to \infty;d }x^{(n)}=x$.

显然上述定义与实数序列的收敛定义是一致的：设 $(x_{n})$ 是实数序列，则 $\lim_{ n \to \infty }x_{n}=x$ 当且仅当 $\lim_{ n \to \infty }d(x_{n},x)=0$.

下面我们证明按 14.1.6 定义的极限是唯一的，从而符号 $\lim_{ n \to \infty;d }x^{(n)}$ 是良定的。

**定理 14.1.7**

设 $(X,d)$ 是一个度量空间，$(x^{(n)})$ 是 $X$ 中的点列，$x,x'\in X$，如果 $(x^{(n)})$ 按度量 $d$ 收敛于 $x$ 和 $x'$，那么 $x=x'$.

**证明**

根据定义，对任意 $\varepsilon>0$，存在 $N$ 使得对任意 $n>N$ 有 $d(x^{(n)},x)<\varepsilon$ 以及 $d(x^{(n)},x')<\varepsilon$，于是

$$
d(x,x')\leq d(x,x^{(n)})+d(x^{(n)},x')<2\varepsilon
$$

从而 $d(x,x')=0$，即 $x=x'$.

现在，我们考虑 $\mathbb{R}^{n}$ 上点列的收敛性，下面是一个常用的定理：

**定理 14.1.8**

设 $(x^{(k)})$ 是 $\mathbb{R}^{n}$ 中的点列，记 $x^{(k)}=(x^{(k)}_{1},\dots,x^{(k)}_{n})$，设 $x\in \mathbb{R}^{n}$，则以下命题等价：

1. $(x^{(k)})$ 按 $l^{1}$ 度量收敛于 $x$
2. $(x^{(k)})$ 按 $l^{2}$ 度量收敛于 $x$
3. $(x^{(k)})$ 按 $l^{\infty}$ 度量收敛于 $x$
4. 对于每个 $1\leq j\leq n$，实数序列 $(x_{j}^{(k)})$ 收敛于 $x_{j}$

**证明**

命题 1 和 2 的等价性来源于不等式 $d_{l^{2}}(x,y)\leq d_{l^{1}}(x,y)\leq \sqrt{ n }d_{l^{2}}(x,y)$，对于左边的不等式，两边平方即证，对于右边的不等式，根据内积空间的 Cauchy-Schwartz 不等式有

$$
\lvert \langle u,v \rangle  \rvert \leq \lVert u \rVert \lVert v \rVert ,u,v \in \mathbb{R}^{n}
$$

将 $u_{i}=|x_{i}-y_{i}|,v_{i}=1$ 以及 $\langle u,v \rangle=\sum_{i=1}^{n}u_{i}v_{i}$ 代入即证。

命题 2 和 3 的等价性来源于不等式 $\dfrac{1}{\sqrt{ n }}d_{l^{2}}(x,y)\leq d_{l^{\infty}}(x,y)\leq d_{l^{2}}(x,y)$，对于右边的不等式，我们有

$$
d_{l^{2}}(x,y)=\left( \sum_{i=1}^{n}|x_{i}-y_{i}|^{2} \right)^{1/2}\geq \left(\sup_{1\leq i\leq n}|x_{i}-y_{i}|^{2}\right)^{1/2}=d_{l^{\infty}}(x,y)
$$

对于左边的不等式，我们有

$$
d_{l^{2}}(x,y)^{2}=\sum_{i=1}^{n}|x_{i}-y_{i}|^{2}\leq \sum_{i=1}^{n}\sup_{1\leq i\leq n}|x_{i}-y_{i}|^{2}=n d_{l^{\infty}}(x,y)^{2}
$$

下证 $1 \iff 4$，先设 1 成立，则有 $\lim_{ k \to \infty }d_{l^{1}}(x^{(k)},x)=0$，设 $1\leq j\leq n$，则 $|x^{(k)}_{j}-x_{j}|\leq d_{l^{1}}(x^{(k)},x)$，故 $\lim_{ k \to \infty }|x_{j}^{(k)}-x_{j}|=0$，即 $(x_{j}^{(k)})$ 收敛于 $x_{j}$.

再设 4 成立，则对任意 $1\leq j\leq n$ 有 $\lim_{ k \to \infty }|x_{j}^{(k)}-x_{j}|=0$，故

$$
\lim_{ k \to \infty } d_{l^{1}}(x^{(k)},x)=\lim_{ k \to \infty } \sum_{j=1}^{n}|x_{j}^{(k)}-x_{j}|=0
$$

这就完成了证明。

最后，我们再给出一个常用定理：

**定理 14.1.9**

设 $(x^{(n)}),(y^{(n)})$ 是度量空间 $(X,d)$ 中的两个点列，如果 $(x^{(n)})$ 和 $(y^{(n)})$ 分别按度量 $d$ 收敛于 $x \in X$ 和 $y \in X$，那么 $\lim_{ n \to \infty }d(x^{(n)},y^{(n)})=d(x,y)$.

**证明**

根据定义，任取 $\varepsilon>0$，存在 $N$ 使得对任意 $n>N$ 有 $d(x^{(n)},x)<\varepsilon$ 且 $d(y^{(n)},y)<\varepsilon$，从而当 $d(x^{(n)},y^{(n)})\geq d(x,y)$ 时有

$$
|d(x^{(n)},y^{(n)})-d(x,y)|\leq d(x^{(n)},x)+d(y,y^{(n)})<2\varepsilon
$$

当 $d(x^{(n)},y^{(n)})< d(x,y)$ 时有

$$
|d(x^{(n)},y^{(n)})-d(x,y)|\leq d(x,x^{(n)})+d(y^{(n)},y)<2\varepsilon
$$

于是 $\lim_{ n \to \infty }|d(x^{(n)},y^{(n)})-d(x,y)|=0$，即证。

上述定理表明，度量函数是一个连续函数（定义在之后给出）。

# Section 2: 点集拓扑

在定义了按度量收敛的概念后，我们再来考虑一些其它的概念，包括开集、闭集、附着点等等，对这些概念的研究构成了一个新的数学分支：**点集拓扑**，这里我们简要地介绍一些主要成果。

首先，我们来定义**开球**，它是实数上的开区间在高维空间的对应。

**定义 14.2.1** 开球（open ball）

设 $(X,d)$ 是一个度量空间，$x_{0}\in X$，实数 $r>0$，定义以 $x_{0}$ 为中心，$r$ 为半径的**开球**为

$$
B_{(X,d)}(x_{0},r)=\{ x \in X \mid d(x,x_{0})<r \}
$$

显然，$\mathbb{R}$ 上的开球就是 $(x_{0}-r,x_{0}+r)$，而 $\mathbb{R}^{2}$ 上的开球 $B((0,0),1)$ 是以原点为中心，$1$ 为半径的开圆盘。

利用开球和一个集合 $E\subset X$，我们可以将 $X$ 中的点分成三类：$E$ 的内点、外点以及边界点。

**定义 14.2.2** 内部（interior），外部（exterior），边界（boundary）

设 $(X,d)$ 是一个度量空间，$E\subset X,x_{0}\in X$，称 $x_{0}$ 是 $E$ 的**内点**，如果存在 $r>0$ 使得 $B(x_{0},r)\subset E$；称 $x_{0}$ 是 $E$ 的**外点**，如果存在 $r>0$ 使得 $B(x_{0},r)\cap E=\varnothing$；称 $x_{0}$ 是 $E$ 的**边界点**，如果 $x_{0}$ 不是 $E$ 的内点或外点。

$E$ 的所有内点构成的集合称为 $E$ 的**内部**，记为 $\mathrm{Int}(E)$，$E$ 的所有外点构成的集合称为 $E$ 的**外部**，记为 $\mathrm{Ext}(E)$，$E$ 的所有边界点构成的集合称为 $E$ 的**边界**，记为 $\partial E$.

例如，考虑实数的子集 $E=[1,2)$，那么 $E$ 的内部是 $(1,2)$，外部是 $(-\infty,1)\cup(2,+\infty)$，边界是 $\{ 1,2 \}$. 注意，内点一定是 $E$ 的元素，边界点可以是 $E$ 的元素，也可以不是，而外点一定不是 $E$ 的元素。

**定义 14.2.3** 附着点（adherent point），闭包（closure）

设 $(X,d)$ 是一个度量空间，$E\subset X,x_{0}\in X$，如果对任意 $r>0$ 都有 $B(x_{0},r)\cap E\neq \varnothing$，则称 $x_{0}$ 是 $E$ 的一个**附着点**。$E$ 的所有附着点构成的集合称为 $E$ 的**闭包**，记为 $\overline{E}$.

下面我们把附着点、内部、外部和边界联系起来。

**定理 14.2.4**

设 $(X,d)$ 是一个度量空间，$E\subset X,x_{0}\in X$，那么以下命题等价：

1. $x_{0}$ 是 $E$ 的附着点
2. $x_{0}$ 是 $E$ 的内点或边界点
3. 存在 $E$ 中的点列 $(x^{(n)})$ 使其按度量 $d$ 收敛于 $x_{0}$.

**证明**

首先证明 $1 \iff 2$. 先设 1 成立，假设 $x_{0}$ 不是 $E$ 的内点或边界点，那么 $x_{0}$ 是 $E$ 的外点，从而存在 $r>0$ 使得 $B(x_{0},r)\cap E=\varnothing$，这与 $x_{0}$ 是 $E$ 的附着点矛盾。

再设 2 成立，如果 $x_{0} \in \mathrm{Int}(E)$，那么 $x_{0} \in E$，则 $x_{0}$ 显然是 $E$ 的附着点。如果 $x_{0} \in \partial E$，那么对任意 $r>0$，总有 $B(x_{0},r)\cap E\neq \varnothing$（否则 $x_{0}$ 将是 $E$ 的外点），从而 $x_{0}$ 是 $E$ 的附着点。

下面证明 $1 \iff 3$. 设 1 成立，则集族

$$
\left\{  x \in E \mid d(x,x_{0})< \dfrac{1}{n}  \right\},n \in \mathbb{N}\setminus \{ 0 \}
$$

均非空，利用选择公理取出点列 $(x^{(n)})_{n=1}^{\infty}$，则 $\lim_{ n \to \infty }d(x^{(n)},x_{0})=0$，即点列按度量 $d$ 收敛于 $x_{0}$.

最后，设 3 成立，则对任意 $r>0$，存在 $N$ 使得对任意 $n>N$ 有 $d(x^{(n)},x_{0})<r$，即 $B(x_{0},r)\cap E\neq \varnothing$，故 $x_{0}\in \overline{E}$，这就完成了证明。

上述定理表明：$\overline{E}=\mathrm{Int}(E)\cup \partial E$，从而我们可以通过边界点是否属于 $E$ 来判断 $E$ 的开闭。

**定义 14.2.5** 开集（open set），闭集（closed set）

设 $(X,d)$ 是一个度量空间，$E\subset X$，称 $E$ 是**开的**，如果 $E\cap \partial E=\varnothing$；称 $E$ 是**闭的**，如果 $\partial E\subset E$.

注意，在点集拓扑中，“开的”的反义词不是“闭的”，因为存在既开又闭的集合（如果集合的边界是空集），也存在不开也不闭的集合（如果 $E$ 只包含一部分边界点，而不包含其它边界点，那么 $E$ 就是不开不闭的）。

下面我们给出开集和闭集的一些基本性质。

**定理 14.2.6**

设 $(X,d)$ 是一个度量空间，则：

1. $E\subset X$ 是开集当且仅当 $E=\mathrm{Int}(E)$
2. $E\subset X$ 是闭集当且仅当 $E=\overline{E}$
3. 对任意 $x_{0}\in X$ 和 $r>0$，开球 $B(x_{0},r)$ 是开集（这解释了它名字的来源），而 $C(x_{0},r)=\{ x \in X \mid d(x,x_{0})\leq r \}$ 是闭集（称为以 $x_{0}$ 为中心，$r$ 为半径的**闭球**）。
4. 对任意 $x_{0}\in X$，单点集 $\{ x_{0} \}$ 是闭的。
5. $E\subset X$ 是开集当且仅当 $X\setminus E$ 是闭集。
6. $X$ 中有限个开集的交是开集，有限个闭集的并是闭集。
7. $X$ 中任意个开集的并是开集，任意个闭集的交是闭集。
8. 设 $E\subset X$，那么 $\mathrm{Int}(E)$ 是包含在 $E$ 中的最大开集，并且 $\overline{E}$ 是包含 $E$ 的最小闭集。

**证明**

(1). 设 $E$ 是开集，则 $E\cap \partial E=\varnothing$，而 $\mathrm{Int}(E)\subset E\subset \mathrm{Int}(E)\cup \partial E$，故 $E=\mathrm{Int}(E)$. 反之，由于 $\mathrm{Int}(E)\cap \partial E=\varnothing$，故 $E\cap \partial E=\varnothing$，即 $E$ 是开的。

(2). 设 $E$ 是闭集，则 $\partial E\subset E$，从而 $\overline{E}=E\cup \partial E=E$. 反之，由于 $E=E\cup \partial E$，故 $\partial E\subset E$，即 $E$ 是闭集。

(3). 设 $x \in B(x_{0},r)$，令 $r'=r-d(x,x_{0})$，则 $B(x,r')\subset B(x_{0},r)$，从而 $x$ 是 $B(x_{0},r)$ 的内点，由性质 1 知 $B(x_{0},r)$ 是开集。

任取 $C(x_{0},r)$ 中的收敛点列 $(x^{(n)})$，其极限为 $x$，则有 $\lim_{ n \to \infty }d(x^{(n)},x_{0})=d(x,x_{0})$，由于 $d(x^{(n)},x_{0})\leq r$，故 $d(x,x_{0})\leq r$，从而 $x \in C(x_{0},r)$，这表明 $C(x_{0},r)$ 是闭集。

(4). $x_{0}$ 是 $\{ x_{0} \}$ 的唯一附着点，故 $\overline{\{ x_{0} \}}=\{ x_{0} \}$，即 $\{ x_{0} \}$ 是闭集。

(5). 先设 $E$ 是开集，则 $X\setminus E=\partial E\cup \mathrm{Ext}(E)=\partial E \cup(X\setminus E)$，这表明 $\partial E\subset X\setminus E$，而 $E$ 的边界点也是 $X\setminus E$ 的边界点，故 $X\setminus E$ 是闭集。

再设 $E$ 是闭集，则 $X\setminus E=\mathrm{Ext}(E)$，设 $x \in X\setminus E$，则存在 $r>0$ 使得 $B(x,r)\cap E=\varnothing$，由于 $E=\mathrm{Int}(E)\cup \partial E$，故 $B(x,r)\subset \mathrm{Ext}(E)$，这表明 $X\setminus E$ 是开集。

(6). 设 $E_{1},\dots,E_{n}$ 是开集，设 $x \in E_{1}\cap\dots \cap E_{n}$，则对任意 $1\leq j\leq n$，存在 $r_{j}>0$ 使得 $B(x,r_{j})\subset E_{j}$，令 $r=\min_{1\leq j\leq n}r_{j}>0$，则有 $B(x,r)\subset E_{j}$，从而 $B(x,r)\subset E_{1}\cap\dots \cap E_{n}$，即 $E_{1}\cap\dots \cap E_{n}$ 是开集。利用 5 以及集合的 De Morgan 律就可以证明有限个闭集的并是闭集。

(7). 设 $\{ E_{i} \}_{i \in I}$ 是一族开集，任取 $E_{j}$ 和 $x \in E_{j}$，则存在 $r>0$ 使得 $B(x,r)\subset E_{j}\subset \bigcup_{i \in I}E_{i}$，因此 $\bigcup_{i \in I}E_{i}$ 是开集。利用 5 和 De Morgan 律即可证明任意个闭集的交是闭集。

(8). 显然 $\mathrm{Int}(E)\subset E$ 是开集，设 $F\subset E$ 是开集，设 $x \in F$，则存在 $r>0$ 使得 $B(x,r)\subset F\subset E$，这表明 $x \in \mathrm{Int}(E)$，因此 $\mathrm{Int}(E)$ 是包含于 $E$ 中的最大开集。

显然 $\overline{E}$ 是闭集，设 $E\subset G$ 是闭集，设 $x \in \overline{E}$，则有 $E$ 中收敛于 $x$ 的点列 $(x^{(n)})$，则 $x^{(n)}\in G$，由于 $G$ 是闭集，故 $x \in G$，因此 $\overline{E}\subset G$，这表明 $\overline{E}$ 是包含 $E$ 的最小闭集。

在定义开集、闭集等概念时，显然这些概念都依赖于所选用的度量 $d$. 例如，在实数集 $\mathbb{R}$ 上，如果我们选用标准度量，那么单点集 $\{ 0 \}$ 不是开集，然而，如果我们选取离散度量 $d_{\mathrm{disc}}$，那么单点集 $\{ 0 \}$ 就是一个开集（准确来说，是既开又闭的）。

然而，不仅度量 $d$ 会对开和闭的概念有影响，其环绕空间 $X$ 也会对这些概念有影响。例如，我们考虑一段区间 $[0,1)$，如果把它看作 $\mathbb{R}$ 的子集，那么 $[0,1)$ 不是闭集，但如果把它看作 $(-1,1)$ 的子集，那么 $[0,1)$ 就是闭的（因为 $1 \not\in(-1,1)$，也就不是 $[0,1)$ 的附着点）。

为了表示这种区别，我们给出以下定义：

**定义 14.2.7** 相对拓扑（relative topology）

设 $(X,d)$ 是一个度量空间，$E\subset Y\subset X$，如果 $E$ 在子空间 $(Y,d|_{Y^{2}})$ 中是开的，则称 $E$ **相对于** $Y$ **是开的**；如果 $E$ 在子空间 $(Y,d|_{Y^{2}})$ 中是闭的，则称 $E$ **相对于** $Y$ **是闭的**。

下面的定理表明了开集与相对开集、闭集与相对闭集的关系。

**定理 14.2.8**

设 $(X,d)$ 是一个度量空间，$E\subset Y\subset X$，则：

1. $E$ 相对于 $Y$ 是开的，当且仅当存在开集 $V\subset X$ 使得 $E=V\cap Y$
2. $E$ 相对于 $Y$ 是闭的，当且仅当存在闭集 $K\subset X$ 使得 $E=K\cap Y$

**证明**

我们先来证明 1. 设 $E$ 相对于 $Y$ 是开的，故对任意 $x \in E$，存在 $r_{x}>0$ 使得 $B_{(Y,d|_{Y^{2}})}(x,r_{x})\subset E$，下面，考虑集合

$$
V=\bigcup_{x \in E}B_{(X,d)}(x,r_{x})
$$

则由定理 14.2.6 知 $V\subset X$ 是开集，现在我们来证 $E=V\cap Y$. 设 $x \in E$，则 $x$ 同时属于 $Y$ 和 $B_{(X,d)}(x,r_{x})$，从而 $E\subset V\cap Y$，再设 $x \in V\cap Y$，则 $x \in B_{(X,d)}(x,r_{x})$，又由于 $x \in Y$，故 $x \in B_{(Y,d|_{Y^{2}})}(x,r_{x})$，从而有 $x \in E$，即证。

现在设存在开集 $V$ 使得 $E=V\cap Y$，我们要证 $E$ 相对于 $Y$ 是开集。设 $x \in E$，则存在 $r>0$ 使得 $B_{(X,d)}(x,r)\subset V$，又 $E=V\cap Y$，故 $B_{(X,d)}(x,r)\cap Y\subset E$，但 $B_{(Y,d|_{Y^{2}})}(x,r)=B_{(X,d)}(x,r)\cap Y$，因此 $E$ 在 $(Y,d|_{Y^{2}})$ 中是开的，这就完成了证明。

现在来证明 2. 设 $E$ 相对于 $Y$ 是闭的，则 $Y\setminus E$ 相对于 $Y$ 是开的，从而存在开集 $V$ 使得 $Y\setminus E=V\cap Y$，现在令 $K=X\setminus V$，则 $K$ 是闭集，我们要证 $E=K\cap Y$. 设 $x \in E\subset Y$，则 $x \not\in V\cap Y$，从而

$$
x \in Y\setminus(V\cap Y)=(Y\setminus V)\cup \varnothing=Y\setminus V\subset X\setminus V=K
$$

故 $x \in K\cap Y$. 反之，设 $x \in K\cap Y=(X\setminus V)\cap Y$，则 $x \in Y$ 且 $x \not\in V$，则 $x \in Y\setminus V=Y\setminus (V\cap Y)=E$，即证。

再设存在闭集 $K$ 使得 $E=K\cap Y$，则 $V=X\setminus K$ 是开集，从而 $V\cap Y$ 相对于 $Y$ 是开集，从而 $Y\setminus(V\cap Y)=Y\setminus V$ 相对于 $Y$ 是闭集。现在我们证明 $E=Y\setminus V$.

设 $x \in E$，则 $x \in Y$ 且 $x \not\in V$，从而 $x \in Y\setminus V$. 再设 $x \in Y\setminus V$，则 $x \in Y\subset X$ 且 $x \not\in V$，从而 $x \in X\setminus V=K$，即 $x \in E$，这就完成了证明。

# Section 3: 完备度量空间

现在，我们可以将实数序列极限的绝大多数理论推广至一般度量空间中，先从子序列开始。

**定义 14.3.1** 子序列（subsequence）

设 $(x^{(n)})_{n=0}^{\infty},(y^{(n)})_{n=0}^{\infty}$ 是度量空间 $(X,d)$ 中的点列，函数 $f\colon \mathbb{N}\to \mathbb{N}$ 是严格递增的，称 $(y^{(n)})_{n=0}^{\infty}$ 是 $(x^{(n)})_{n=0}^{\infty}$ 的一个**子序列**，如果对任意 $n \in \mathbb{N}$ 有 $y^{(n)}=x^{(f(n))}$.

**定义 14.3.2** 序列的附着点（adherent point）

设 $(x^{(n)})_{n=0}^{\infty}$ 是度量空间 $(X,d)$ 中的点列，$x \in X$，称 $x$ 是序列 $(x^{(n)})_{n=0}^{\infty}$ 的一个**附着点**，如果对任意 $\varepsilon>0$ 和 $N \in \mathbb{N}$，存在 $n>N$ 使得 $d(x^{(n)},x)<\varepsilon$.

定理 5.1.2 和 5.1.3 也可以直接推广至一般度量空间上。

**定理 14.3.3**

设 $(x^{(n)})_{n=0}^{\infty}$ 是度量空间 $(X,d)$ 中的点列，$x_{0}\in X$，则以下命题等价：

1. $(x^{(n)})_{n=0}^{\infty}$ 按度量 $d$ 收敛于 $x_{0}$
2. $(x^{(n)})_{n=0}^{\infty}$ 的所有子序列都按度量 $d$ 收敛于 $x_{0}$

**定理 14.3.4**

设 $(x^{(n)})_{n=0}^{\infty}$ 是度量空间 $(X,d)$ 中的点列，$x_{0}\in X$，则以下命题等价：

1. $x_{0}$ 是 $(x^{(n)})_{n=0}^{\infty}$ 的附着点
2. 存在 $(x^{(n)})_{n=0}^{\infty}$ 的一个子序列按度量 $d$ 收敛于 $x_{0}$

上述定理的证明与实数序列的证明几乎是相同的，因此这里不再重复了。

下面我们考虑一般度量空间上的 Cauchy 序列。

**定义 14.3.5** Cauchy 序列

设 $(x^{(n)})_{n=0}^{\infty}$ 是度量空间 $(X,d)$ 中的点列，称该序列是一个 **Cauchy 序列**，如果对任意 $\varepsilon>0$，存在 $N \in \mathbb{N}$ 使得对任意 $n,m>N$ 有 $d(x^{(n)},x^{(m)})<\varepsilon$.

同样地，实数 Cauchy 序列的大多数性质都可以继承到 14.3.5 定义的 Cauchy 序列中。

**定理 14.3.6**

如果度量空间 $(X,d)$ 中的点列 $(x^{(n)})$ 是收敛序列，则它也是一个 Cauchy 序列。

上述定理的证明与定理 4.1.6 的证明相同。

**定理 14.3.7**

设度量空间 $(X,d)$ 中的点列 $(x^{(n)})$ 是 Cauchy 序列，如果存在 $(x^{(n)})$ 的一个子序列按度量 $d$ 收敛于 $x_{0}\in X$，则 $\lim_{ n \to \infty;d }x^{(n)}=x_{0}$.

**证明**

设 $(x^{(n)})_{n=0}^{\infty}$ 的子序列 $(x^{(f(n))})_{n=0}^{\infty}$ 收敛于 $x_{0}$，则对任意 $\varepsilon>0$，存在 $N \in \mathbb{N}$ 使得对任意 $k,m,n>N$ 有 $d(x^{(f(k))},x_{0})<\varepsilon$ 且 $d(x^{(n)},x^{(m)})<\varepsilon$，固定 $k=N+1$，由于 $f$ 是严格递增的，故 $f(N+1)>N$，从而

$$
d(x^{(n)},x_{0})\leq d(x^{(n)},x^{(f(N+1))})+d(x^{(f(N+1))},x_{0})<2\varepsilon
$$

这就完成了证明。

在一般的度量空间 $(X,d)$ 中，Cauchy 序列不一定是收敛序列，比如在标准度量下，$(\mathbb{Q},d)$ 中的 Cauchy 序列不一定在 $\mathbb{Q}$ 中有极限。然而，$(\mathbb{R},d)$ 中的 Cauchy 序列就一定在 $\mathbb{R}$ 中收敛，这种性质我们称为**完备性**。

**定义 14.3.8** 完备的（complete）

称度量空间 $(X,d)$ 是**完备的**，如果 $(X,d)$ 中的任意 Cauchy 序列都在 $(X,d)$ 中收敛。

按以上定义，$(\mathbb{R},d)$ 就是完备的，而 $(\mathbb{Q},d)$ 就不是完备的。就像我们从 $\mathbb{Q}$ 中构造出了实数一样，我们也可以将一个度量空间完备化，这一过程和我们构造实数的过程几乎是相同的。事实上，我们有以下结果（证明在附录中）：

**定理 14.3.9** 度量空间的完备化（completion）

设 $(X,d)$ 是度量空间，则存在一个完备度量空间 $(\overline{X},\overline{d})$，其包含 $(X,d)$ 作为它的子空间，并且 $X$ 在 $(\overline{X},\overline{d})$ 中的闭包就是 $\overline{X}$.

上述定理的证明过程中需要用到等价序列的概念，这里我们给出定义。

**定义 14.3.10** 等价的（equivalent）

设 $(x^{(n)})_{n=0}^{\infty},(y^{(n)})_{n=0}^{\infty}$ 是度量空间 $(X,d)$ 中的点列，称 $(x^{(n)})_{n=0}^{\infty}$ **等价于** $(y^{(n)})_{n=0}^{\infty}$，如果 $\lim_{ n \to \infty }d(x^{(n)},y^{(n)})=0$.

根据三角不等式，序列的等价满足自反性、对称性和传递性，因而是一个等价关系。

完备度量空间有一些非常好的性质，比如说，完备度量空间的点集总是一个闭集。

**定理 14.3.11**

1. 设 $(X,d)$ 是度量空间，$Y\subset X$，如果 $(Y,d|_{Y^{2}})$ 是完备的，那么 $Y$ 是闭集。
2. 设 $(X,d)$ 是完备度量空间，$Y\subset X$ 是闭集，那么子空间 $(Y,d|_{Y^{2}})$ 是完备的。

**证明**

(1). 任取 $Y$ 中的 Cauchy 序列 $(y^{(n)})$，由于 $(Y,d|_{Y^{2}})$ 是完备的，故其按度量 $d|_{Y^{2}}$ 收敛于 $y \in Y$，从而 $Y$ 是闭集。

(2). 任取 $Y$ 中的 Cauchy 序列 $(y^{(n)})$，由于 $(X,d)$ 是完备的，故 $(y^{(n)})$ 按度量 $d|_{Y^{2}}$ 收敛于 $y$，由于 $Y$ 是闭集，故 $y \in Y$，从而 $(Y,d|_{Y^{2}})$ 是完备的。

# Section 4: 紧致性

现在我们来考察分析中最重要的概念之一：紧致性。回顾一下 Heine-Borel 定理（定理 9.1.11），它指出实数的子集 $X$ 是一个有界闭集当且仅当 $X$ 中的序列有一个收敛的子序列，其极限 $L\in X$，或者 $X$ 的开覆盖可以分离出一个有限覆盖。这个性质非常有用，我们给它一个定义：

**定义 14.4.1** 紧致的（compact）

称度量空间 $(X,d)$ 是**紧致的**，如果 $(X,d)$ 中每个序列都有一个收敛于 $X$ 中元素的子序列。如果 $Y\subset X$ 且 $(Y,d|_{Y^{2}})$ 是紧致的，则称 $Y$ 是紧致的。

度量空间的紧致性，与开和闭不同，是一种内在属性。也就是说，度量空间 $(X,d)$ 的紧致性只与其度量 $d$ 有关，而与其环绕空间无关。

下面我们考虑将 Heine-Borel 定理推广至一般的度量空间。

**定义 14.4.2** 有界的（bounded）

设 $(X,d)$ 是度量空间，$Y\subset X$，称 $Y$ 是**有界的**，如果存在 $x \in X$ 和 $r>0$ 使得 $Y\subset B(x,r)$.

**定理 14.4.3**

设 $(X,d)$ 是一个紧致度量空间，那么 $(X,d)$ 是完备且有界的。

**证明**

设 $(x^{(n)})$ 是 $(X,d)$ 中的 Cauchy 序列，根据紧致性，它有一个收敛的子序列，从而根据定理 14.3.7，序列 $(x^{(n)})$ 收敛，这表明 $(X,d)$ 是完备的。

假设 $X$ 不是有界的，取 $x_{0}\in X$，则集族

$$
\{ x \in X \mid d(x,x_{0})>n \}, n \in \mathbb{N}
$$

均非空，应用选择公理取出序列 $(x^{(n)})$，则它的任意子序列都不收敛，这与紧致性矛盾。

结合定理 14.3.11，我们就证明了 Heine-Borel 定理的一半：

**定理 14.4.4**

设 $(X,d)$ 是度量空间，$Y\subset X$ 是紧致的，那么 $Y$ 是闭且有界的。

Heine-Borel 定理的另一半只在 $\mathbb{R}^{n}$ 上成立。

**定理 14.4.5** Heine-Borel 定理

设 $\mathbb{R}^{n}$ 上的度量是 $l^{1}$ 度量、$l^{2}$ 度量或者 $l^{\infty}$ 度量，$E\subset \mathbb{R}^{n}$，那么 $E$ 是紧致的，当且仅当 $E$ 是闭且有界的。

**证明**

我们只需证如果 $E$ 是闭且有界的，那么 $E$ 是紧致的。根据定理 14.1.8，按这三个度量收敛是等价的，因此我们就写成 $(\mathbb{R}^{n},d)$.

给定 $E$ 中的序列 $(x^{(k)})$，则有 $x^{(k)}=(x_{1}^{(k)},\dots,x_{n}^{(k)})$，由于序列 $(x^{(k)})$ 是有界的，故对每个 $1\leq j\leq n$，实数序列 $(x_{j}^{(k)})$ 都是有界的，从而存在收敛的子序列。我们将按以下方法取出 $(x^{(k)})$ 的子序列：

首先，存在 $(x_{1}^{(k)})$ 的子序列 $(x_{1}^{(k_{i})})$ 收敛于 $x_{1}$，由于 $(x_{2}^{(k_{i})})$ 也是有界的，故存在它的子序列 $(x_{2}^{(k_{i_{j}})})$ 收敛于 $x_{2}$，然后再取 $(x_{3}^{(k_{i_{j}})})$ 的子序列收敛于 $x_{3}$，以此类推，最终我们可以得到 $(x^{(k)})$ 的一个子序列，其收敛于 $(x_{1},\dots,x_{n})\in E$，这就完成了证明。

实数上的 Heine-Borel 定理还涉及了紧致集的开覆盖，我们同样可以将其推广至一般的度量空间。

**定义 14.4.6** 开覆盖（open cover）

设 $(X,d)$ 是一个度量空间，$Y\subset X$，$\mathcal{O}=\{ V_{i} \}_{i \in I}$ 是 $X$ 上的一族开集，称 $\mathcal{O}$ 是 $Y$ 的一个**开覆盖**，如果 $Y\subset \bigcup \mathcal{O}$.

**定理 14.4.7** 有限覆盖定理

设 $(X,d)$ 是一个度量空间，$Y\subset X$，并且 $\{ V_{i} \}_{i \in I}$ 是 $Y$ 的一个开覆盖，则 $Y$ 是紧致的，当且仅当存在有限集 $J\subset I$ 使得 $Y\subset \bigcup_{j \in J}V_{j}$.

**证明**

设 $Y$ 是紧致的，假设其不存在有限覆盖。设 $y \in Y$，那么存在 $i \in I$ 使得 $y \in V_{i}$，则存在 $r>0$ 使得 $B(y,r)\subset V_{i}$，定义

$$
r(y)=\sup\{ r \mid \exists i \in I (B(y,r)\subset V_{i}) \}
$$

那么对任意 $y \in Y$ 有 $r(y)>0$，现在令

$$
r_{0}=\inf\{ r(y) \mid y \in Y \}
$$

则 $r_{0}\geq 0$，我们分两种情况来讨论：$r_{0}=0$ 和 $r_{0}>0$.

如果 $r_{0}=0$，那么对任意正整数 $n$，都有 $y \in Y$ 使得 $r(y)< \dfrac{1}{n}$，从中取出一个记为 $y^{(n)}$，从而序列 $(y^{(n)})_{n=1}^{\infty}$ 满足 $\lim_{ n \to \infty }r(y^{(n)})=0$. 根据紧致性，存在 $(y^{(n)})$ 的子序列 $(y^{(n_{k})})$ 收敛于 $y_{0}\in Y$，则存在 $i \in I$ 使得 $y_{0}\in V_{i}$，从而有 $\varepsilon>0$ 使得 $B(y_{0},\varepsilon)\subset V_{i}$.

由于 $(y^{(n_{k})})$ 收敛于 $y_{0}$，故存在 $K$ 使得对任意 $k>K$ 有 $d(y^{(n_{k})},y_{0})< \dfrac{\varepsilon}{2}$，于是有 $B\left( y^{(n_{k})}, \dfrac{\varepsilon}{2} \right)\subset B(y_{0},\varepsilon)\subset V_{i}$，从而有 $r(y^{(n_{k})})\geq \dfrac{\varepsilon}{2}$，但这与 $\lim_{ n \to \infty }r(y^{(n)})=0$ 矛盾。

如果 $r_{0}>0$，那么对任意 $y \in Y$，都有 $r(y)> \dfrac{r_{0}}{2}$，从而都存在 $i \in I$ 使得 $B\left( y, \dfrac{r_{0}}{2} \right)\subset V_{i}$. 下面按以下方法构造序列：

取 $y^{(0)}\in Y$，则存在 $i_{0} \in I$ 使得 $B\left( y^{(0)}, \dfrac{r_{0}}{2} \right)\subset V_{i_{0}}$，$V_{i_{0}}$ 不可能覆盖 $Y$，故存在 $y^{(1)}\in Y\setminus V_{i_{0}}$，则有 $B\left( y^{(1)}, \dfrac{r_{0}}{2} \right)\subset V_{i_{1}}$，$V_{i_{0}}\cup V_{i_{1}}$ 也不能覆盖 $Y$，故存在 $y^{(2)}\in Y\setminus(V_{i_{0}}\cup V_{i_{1}})$，使得 $B\left( y^{(2)}, \dfrac{r_{0}}{2} \right)\subset V_{i_{2}}$，以此类推。由于 $Y$ 不能被有限覆盖，故上述过程可以一直持续下去，从而得到一个序列 $(y^{(n)})_{n=0}^{\infty}$，满足对任意 $n,m$ 有 $d(y^{(n)},y^{(m)})\geq r_{0}$，故该序列的任意子序列都不是 Cauchy 序列，从而不收敛，但这与 $Y$ 的紧致性矛盾。

反之，设 $Y$ 具有有限覆盖性质，假设 $Y$ 不是紧致的。那么存在 $Y$ 中的一个序列 $(y^{(n)})_{n=0}^{\infty}$，它没有附着点，从而对任意 $y \in Y$，都存在 $\varepsilon_{y}>0$ 使得 $B(y,\varepsilon_{y})\cap \{ y^{(n)} \mid n \in \mathbb{N} \}$ 是有限集。现在构造 $Y$ 的开覆盖

$$
\mathcal{O}=\{ B(y,\varepsilon_{y}) \mid y \in Y \}
$$

则存在 $Y$ 的一个有限覆盖 $\{ B(y_{1},\varepsilon_{y_{1}}),\dots,B(y_{n},\varepsilon_{y_{n}}) \}$，但每个 $B(y_{j},\varepsilon_{y_{j}})$ 中的 $(y^{(n)})$ 点都是有限的，从而 $\{ y^{(n)} \mid n \in \mathbb{N} \}$ 是有限集，矛盾。

上述利用开集描述的紧致性概念通常被看作是比使用序列描述的更为基本，这是因为与度量空间中以序列为基本概念不同。在拓扑空间中，开集是更为基本和本质的概念，我们之后会做一些简要介绍。

利用有限覆盖定理，我们可以证明紧致套定理，它是实数上区间套定理的推广。

**定理 14.4.8** 紧致套定理（nested compact theorem）

设 $(X,d)$ 是度量空间，$(K_{n})_{n=0}^{\infty}$ 是 $X$ 的非空紧致子集构成的序列，满足

$$
K_{0}\supset K_{1}\supset K_{2}\supset \cdots
$$

那么 $\bigcap_{n=0}^{\infty}K_{n}\neq \varnothing$.

**证明**

假设 $\bigcap_{n=0}^{\infty}K_{n}= \varnothing$，考虑紧致度量空间 $(K_{0},d|_{K_{0}^{2}})$ 上的开集 $K_{0}\setminus K_{n}$，则 $\{ K_{0}\setminus K_{n} \}_{n \in \mathbb{N}}$ 是 $K_{0}$ 的一个开覆盖，从而存在有限覆盖

$$
K_{0}=\bigcup_{j=1}^{k} (K_{0}\setminus K_{n_{j}})=K_{0}\setminus \left( \bigcap_{j=1}^{k} K_{n_{j}} \right)
$$

但 $\bigcap_{j=1}^{k} K_{n_{j}}\neq \varnothing$，故 $K_{0}\neq K_{0}\setminus \left( \bigcap_{j=1}^{k} K_{n_{j}} \right)$，矛盾。

最后，我们再给出紧致集的一些性质。

**定理 14.4.9**

设 $(X,d)$ 是度量空间，则有：

1. 如果 $Y\subset X$ 是紧致的，$Z\subset Y$，那么 $Z$ 是紧致的当且仅当 $Z$ 是闭的。
2. $X$ 中有限个紧致集的并也是紧致集。
3. $X$ 的有限子集是紧致的。

**证明**

(1). 设 $Z$ 是紧致的，那么根据定理 14.4.4，$Z$ 是闭的。再设 $Z$ 是闭集，任取 $Z$ 中的序列 $(z^{(n)})$，由于 $Y$ 是紧致的，故 $(z^{(n)})$ 有一个收敛的子序列，由于 $Z$ 是闭集，故其极限包含在 $Z$ 中，从而 $Z$ 是紧致的。

(2). 设 $Y_{1},\dots,Y_{n}\subset X$ 是紧致的，对于 $1\leq j\leq n$，设 $\mathcal{O}_{j}$ 是 $Y_{j}$ 的一个开覆盖，那么可以分离出 $Y_{j}$ 的一个有限覆盖 $\mathcal{O}_{j}'$，从而有

$$
\bigcup_{j=1}^{n}Y_{j} \subset \bigcup_{j=1}^{n}\mathcal{O}_{j}'
$$

并且后者是有限集，这表明 $\bigcup_{j=1}^{n}Y_{j}$ 是紧致集。

(3). 空集显然是紧致的。设 $x_{0}\in X$，那么单点集 $\{ x_{0} \}$ 是紧致的（它有有限覆盖 $\{ B(x_{0},r) \}$ ），由于 $X$ 的有限子集是有限个单点集的并，因而是紧致的。

**定理 14.4.10**

设 $(X,d)$ 是一个紧致度量空间，$\{ K_{i} \}_{i \in I}$ 是 $X$ 中的一族闭子集，满足有限交性质：其中有限个集合的交集非空，那么 $\bigcap_{i \in I}K_{i}\neq \varnothing$.

**证明**

根据定理 14.4.9，每个 $K_{i}$ 都是紧致的。假设 $\bigcap_{i \in I}K_{i}= \varnothing$，取一个集合 $K_{i_{0}}$，定义 $V_{i}=X\setminus K_{i}$，那么 $\{ V_{i} \}_{i \in I}$ 构成了 $K_{i_{0}}$ 的一个开覆盖，从而有

$$
K_{i_{0}}\subset \bigcup_{j=1}^{k} (X\setminus K_{i_{j}})=X \setminus \left( \bigcap_{j=1}^{k} K_{i_{j}} \right)
$$

但这表明 $K_{i_{0}}\cap K_{i_{1}}\cap\dots \cap K_{i_{k}}=\varnothing$，与有限交性质矛盾。

上述定理给出了紧致套定理的另一种证明方法。