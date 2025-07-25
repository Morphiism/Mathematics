我们已经见过了三种不同类型的集合：有限集、可数集、不可数集，而其中，有限集和可数集是容易处理的，但不可数集的处理则麻烦得多，比如我们定义不可数集上的求和时，必须要通过有限集和可数集来间接地把握不可数集的性质。为什么会有这样的区别？答案是至多可数集可以与自然数的子集建立双射，而自然数，特别是其上的序结构具有以下性质：$\mathbb{N}$ 连同其上的序构成了一个**良序集**，这是**归纳法**得以成立的基础，借由归纳法，我们从有限达到了无限。

现在，我们自然会问，是否有一种方法，可以将自然数的良序结构进行推广？这就是**序数**的由来。为了研究序数，我们首先需要对一般的序关系进行研究，在这之后，我们将应用序数理论对**选择公理**做一些讨论，它是做进一步的分析研究的基础。

# Section 1: 良序结构

## 偏序

**定义 8.1.1** 偏序（partial order）

集合 $X$ 上的关系 $\leq$ 是一个**偏序**如果对任意 $x,y,z \in X$ 有：

- 自反性：$x\leq x$
- 反对称性：$x\leq y,y\leq x\implies x=y$
- 传递性：$x\leq y,y\leq z\implies x\leq z$

并称二元组 $(X,\leq)$ 是一个**偏序集**。如果 $x\leq y$ 且 $x\neq y$，则定义 $x<y$，称 $<$ 是 $X$ 上的**严格偏序**。

$X$ 上的严格偏序满足下列性质：

- 反自反性：$x \not< x$
- 传递性：$x<y,y<z\implies x<z$

有时也称满足上述性质的关系 $<$ 是偏序，这两种定义是等价的。在分析中我们常用 $\leq$ 的偏序，但在集合论中，我们更多地使用 $<$ 类的偏序。

例如，$\mathscr{P}(X)$ 上的包含关系 $\subset$ 是一种 $\leq$ 类的偏序，而自然数上的关系 $\in$ 是一种 $<$ 类的偏序（ $n=\{ 0,1,\dots,n-1 \}$，则 $k<n \iff k\in n$ ）。

下面我们给出几个定义，注意它们之间的区别：

**定义 8.1.2** 极大元（maximal element），极小元（minimal element），最大元（greatest element），最小元（least element），上界（upper bound），下界（lower bound）

设 $X$ 是一个偏序集，$x \in X$，则：

- $x$ 是 $X$ 的**极大元**如果对任意 $y \in X$ 有 $y \not> x$
- $x$ 是 $X$ 的**极小元**如果对任意 $y \in X$ 有 $y \not< x$
- $x$ 是 $X$ 的**最大元**如果对任意 $y \in X$ 有 $y\leq x$
- $x$ 是 $X$ 的**最小元**如果对任意 $y \in X$ 有 $y\geq x$
- $x$ 是 $Y\subset X$ 的**上界**如果对任意 $y \in Y$ 有 $y\leq x$
- $x$ 是 $Y\subset X$ 的**严格上界**如果对任意 $y \in Y$ 有 $y< x$
- $x$ 是 $Y\subset X$ 的**下界**如果对任意 $y \in Y$ 有 $y\geq x$
- $x$ 是 $Y\subset X$ 的**严格下界**如果对任意 $y \in Y$ 有 $y> x$

在偏序集中，最大元一定是极大元，反之则不然，并且最大元最多只有一个（由于反对称性），但极大元可以有多个，对于极小元与最小元也是一样的。

## 全序

我们之前已遇到了多个具体的序关系，如 $\mathbb{Z},\mathbb{Q},\mathbb{R}$ 上的序 $\leq$，它们除了自反性、反对称性和传递性外，还满足完全性：$x\leq y$ 和 $y\leq x$ 至少有一个成立，换言之，任意两个元素都可以比较。这是一种性质更好的序结构，我们给它一个定义：

**定义 8.1.3** 全序（total order），链（chain）

集合 $X$ 上的偏序关系 $\leq$ 是一个**全序**如果对任意 $x,y \in X$ 有：

- 完全性：$x\leq y$ 和 $y\leq x$ 至少有一个成立。

并称 $(X,\leq)$ 是一个**全序集**。设 $Y$ 是偏序集 $X$ 的子集，如果偏序 $\leq$ 在 $Y$ 上的限制是一个全序，则称 $Y$ 是 $X$ 中的**链**（或**全序子集**）。

完全性在严格偏序上的对应是三分律：$x<y,x=y,x>y$ 至少有一个成立。进一步，我们可以证明上面三个关系最多只能有一个成立（用反证法，通过传递性和反自反性我们可以得到矛盾）。

利用三分律可以证明，在全序集中，极大元就是最大元，极小元就是最小元。

下面我们研究全序集之间的关系。

**定义 8.1.4** 保序映射（order-preserving mapping），严格递增函数（strictly increasing function）

设 $A,B$ 是全序集，$f\colon A\to B$，如果对任意 $x,y \in A,x<y$ 有 $f(x)<f(y)$，则称 $f$ 是一个**保序映射**（或**严格递增函数**）。

关于保序映射，有如下的简单性质：

- 设 $A$ 是全序集，$B$ 是偏序集，$f\colon A\to B$ 是保序的，则 $f[A]$ 是 $B$ 中的链（全序子集）。
- 保序映射是一个单射。因此保序满射是一个保序双射（同构）。

**定义 8.1.5** 初始段（initial segment）

设 $A$ 是全序集，$B\subset A$，称 $B$ 是 $A$ 的**初始段**，如果对任意 $x \in A,y \in B$ 有 $x<y\implies x \in B$.

例如，按通常的序，开区间 $(-\infty,0)$ 是 $\mathbb{R}$ 的初始段，负整数集 $\{ n \in \mathbb{Z} \mid n<0 \}$ 是 $\mathbb{Z}$ 的初始段。

**定义 8.1.6** 同构（isomorphism）

两个全序集 $A,B$ 是**同构的**，如果存在保序双射 $f\colon A\to B$，记作 $A\cong B$，并称 $f$ 是一个**同构**，记作 $f\colon A \overset{\sim}{\to} B$.

显然同构关系具有自反性、对称性、传递性，从而是一个等价关系。

## 良序

现在我们就可以引入良序了，它是集合论的中心概念之一。

**定义 8.1.7** 良序（well-order）

集合 $X$ 上的全序关系 $\leq$ 是一个**良序**，如果有：

- 良基性：$X$ 的任意非空子集都有极小元。

并称 $(X,\leq)$ 是一个**良序集**。

显然，自然数的任意子集都是良序集。根据全序的性质，良序集的极小元就是最小元，并且是唯一的。

我们可以用良序集和双射诱导出其它集上的良序，如下定理所示：

**定理 8.1.8**

设 $A$ 是良序集，函数 $f\colon A\to B$ 是双射，则 $B$ 上存在良序关系。

**证明**

定义 $B$ 上的关系 $<_{B}$ 如下：对 $x,y \in B$，定义

$$
x<_{B}y \iff f^{-1}(x)<_{A}f^{-1}(y)
$$

由于 $A$ 上的关系 $<_{A}$ 是良序，从而 $<_{B}$ 也是良序，这就完成了证明。

我们在定义可数和 $\sum_{x \in X}f(x)$ 时，正是利用了上述定理，用 $\mathbb{N}$ 上的良序诱导出了 $X$ 上的良序，于是我们可以将 $X$ 表示为 $\{ x_{0},x_{1},\dots \}$，从而将可数和转化为了无穷级数。相反，不可数集合不能表示为一个无限序列，因为不存在 $\mathbb{N}$ 到 $X$ 的双射，没有良序关系，我们就无法计算（无穷级数是有限级数的极限，而有限级数是用归纳法定义的），所以我们要把不可数和转化为可数和，再进行计算。

良序集的优点之一是它的初始段有简单的表示方法。

**定理 8.1.9**

设 $A$ 是良序集，$X$ 是 $A$ 的真初始段（ $X\neq A$ ），则存在 $x \in A$ 使得

$$
X=A_{x}=\{ y \in A \mid y<x \}
$$

**证明**

设 $Y=A\setminus X\neq \varnothing$，则 $Y$ 有最小元，设为 $x$.

设 $y<x$，则由 $x$ 的最小性知 $y \not\in Y$，则 $y \in X$，于是 $A_{x}\subset X$.

设 $y \in X$，假设 $x\leq y$，则 $y \in Y$，矛盾。故 $y \in A_{x}$，从而 $X\subset A_{x}$.

上述定理只在良序集上成立，对于全序集，我们有如下反例：有理数的初始段 $\{ q \mid q<0 \}\cup\{ q \mid q^{2}<2 \}$ 不存在 $\mathbb{Q}_{x}$ 表示。

接下来，我们介绍良序集最重要的优点：归纳法。作为良序性的直接推论（见定理 1.2.11 的证明），强归纳法可以从自然数推广到任意良序集，甚至是不可数集，只要我们能找到一个良序（利用选择公理，这是可能的）。

**定理 8.1.10** 超限归纳法（transfinite induction）

设 $X$ 是良序集，$A\subset X$，如果 $\forall y<x(y \in A)\implies x \in A$，则 $A=X$.

**证明**

假设 $A\neq X$，令 $B=X\setminus A$，则 $B$ 有最小元 $x_{0}$. 根据 $x_{0}$ 的最小性，可知对任意 $y<x_{0}$ 有 $y \in A$，从而有 $x_{0} \in A$，这与 $x \in B$ 矛盾。

超限归纳法可以用于证明像“对任意 $x \in X$ 有 $\varphi(x)$ 成立”的全称命题，我们使用的归纳法是它在 $X=\mathbb{N}$ 时的特殊情况。它的使用方法也和 $\mathbb{N}$ 上的归纳法一样：首先验证 $X$ 的极小元成立 $\varphi(x_{0})$，然后证明对所有 $y<x$ 都成立 $\varphi(y)$ 时有 $\varphi(x)$ 成立，然后由归纳法可得对任意 $x \in X$ 都有 $\varphi(x)$ 成立。

利用超限归纳法，我们可以证明一个关于良序集的重要结果：任意两个良序集之间可以比较基数。

**定理 8.1.11** 良序集基本定理

设 $A,B$ 是良序集，则 $A\cong B,A_{x}\cong B,A\cong B_{y}$ 有且仅有一个成立。

我们首先证明几个引理。

**引理 8.1.12**

设 $A$ 是良序集，$f\colon A\to A$ 是保序映射，则对任意 $x \in A$ 有 $f(x)\geq x$.

**证明**

设 $x_{0}=\min A$，则显然有 $f(x_{0})\geq x_{0}$. 假设对 $y<x$ 有 $f(y)\geq y$，假设 $f(x)<x$，则由保序性得 $f(f(x))<f(x)$，又 $f(x)<x$，由归纳假设得 $f(f(x))\geq f(x)$，矛盾。

**引理 8.1.13**

良序集与其真初始段不同构。

**证明**

设 $A$ 是良序集，假设 $A\cong A_{x}$，则有 $A\to A_{x}$ 的保序双射 $f$，于是 $f(x) \in A_{x}$，从而 $f(x)<x$，与 $f(x)\geq x$ 矛盾。

**引理 8.1.14**

设 $A,B$ 是良序集，则 $A\cong B,A_{x}\cong B,A\cong B_{y}$ 至多有一种成立。

**证明**

由引理 8.1.13 知 1 和 2，1 和 3 不会同时出现。假设 $A_{x}\cong B$ 且 $A\cong B_{y}$，设 $f\colon A \overset{\sim}{\to} B_{y}$，则

$$
A_{x} \cong (B_{y})_{f(x)} = B_{f(x)} \cong B
$$

与引理 8.1.13 矛盾。

现在我们给出基本定理的证明。

**证明**（8.1.11）

我们只需证明 $A\cong B,A_{x}\cong B,A\cong B_{y}$ 至少有一个成立。构造 $A$ 到 $B$ 的关系

$$
f=\{ (x,y)\in A\times B \mid A_{x} \cong B_{y} \}
$$

我们证明 $f$ 具有单值性。设 $(x,y_{1}) \in f,(x,y_{2}) \in f$，则 $A_{x}\cong B_{y_{1}}\cong B_{y_{2}}$，从而 $y_{1}=y_{2}$（否则就与引理 8.1.13 矛盾）。

利用同样的方法，我们可以证明 $f$ 是单射，即 $(x_{1},y) \in f,(x_{2},y) \in f$ 蕴含 $x_{1}=x_{2}$.

下面我们证明 $f$ 是保序的。设 $x_{1}<x_{2}$，令 $y_{1}=f(x_{1}),y_{2}=f(x_{2})$，假设 $y_{1}>y_{2}$，则

$$
(A_{x_{2}})_{x_{1}} = A_{x_{1}}\cong B_{y_{1}}, A_{x_{2}}\cong B_{y_{2}} = (B_{y_{1}})_{y_{2}}
$$

这与引理 8.1.14 矛盾。设 $D=\mathrm{Dom}(f),R=\mathrm{Ran}(f)$，则 $f\colon D\overset{\sim}{\to}R$.

下面我们证明 $D=A$ 或 $R=B$ 成立。假设 $D\neq A$ 且 $R\neq B$，则 $A\setminus D\neq \varnothing$，设 $x_{0}$ 是其最小元，我们来证明 $D=A_{x_{0}}$.

设 $x \in A_{x_{0}}$，则 $x<x_{0}$，由 $x_{0}$ 的最小性知 $x \in D$. 设 $x \in D$，则 $x\neq x_{0}$，假设 $x>x_{0}$，则根据 $D$ 的定义，存在 $y \in B$ 使得 $f(x)=y$，令 $g\colon A_{x} \overset{\sim}{\to} B_{y}$，则 $A_{x_{0}}\cong B_{g(x_{0})}$，于是 $f(x_{0})=g(x_{0})$，这与 $x_{0}\not\in D$ 矛盾，于是 $x<x_{0}$. 这就证明了 $D=A_{x_{0}}$.

根据对称性，我们有 $R=B_{y_{0}}$，其中 $y_{0}=\min B\setminus R$，于是我们有

$$
A_{x_{0}}=D \cong R = B_{y_{0}}
$$

从而 $f(x_{0})=y_{0}$，这与 $x_{0} \not\in D$ 矛盾。这就完成了证明。

> 这个定理背后的直观是这样的：首先分别取出 $A$ 和 $B$ 的最小元 $x_{0},y_{0}$，此时有 $\{ x_{0} \}\cong \{ y_{0} \}$，下一步，取出 $A\setminus \{ x_{0} \}$ 和 $B\setminus \{ y_{0} \}$ 的最小元 $x_{1},y_{1}$，此时 $\{ x_{0},x_{1} \}\cong \{ y_{0},y_{1} \}$，下一步，再取出两个集合剩余部分的最小元，仍然有 $\{ x_{0},x_{1},x_{2} \}\cong \{ y_{0},y_{1},y_{2} \}$，以此类推。当其中一个集合被抽空时停止，那么有三种情况：或者 $B$ 还有剩余（ $A\cong B_{y}$ ），或者 $A$ 有剩余（ $A_{x}\cong B$ ），或者两者都被抽空（ $A\cong B$ ）。

根据上述定理，我们就有推论：

**定理 8.1.15**

设 $A,B$ 是良序集，则 $A\preceq B$ 与 $B\preceq A$ 至少有一个成立。

# Section 2: 序数与 ZF 公理

到目前为止，除了自然数及其子集，我们还没见过其它的良序结构（除用自然数的良序诱导出来的以外）。特别地，我们还没有见过使得 $\mathbb{N}\cong B_{y}$ 的集合 $B$. 下面我们就要来构造**序数**，它是自然数在超穷世界的推广。

在这之前，让我们把自然数还原到它最初的集合论构造中来，也就是最小归纳集 $\omega$（见第一章）。我们曾用加法来定义 $\omega$ 上的序关系，现在我们也要把它还原：

**定理 8.2.1**

设 $m,n \in \omega$，则 $m \in n \iff m<n$.

**证明**

当 $n=0=\varnothing$ 时，$m \in n \iff m<n$ 是一个空真。假设结论对 $n$ 成立，设 $m \in n'=n\cup \{ n \}$，则 $m \in n$ 或者 $m=n$.

当 $m \in n$ 时，由归纳假设得 $m<n$，从而 $m<n'=n+1$. 当 $m=n$ 时，则 $m=n<n'=n+1$.

再设 $m<n'$，则 $m'\leq n'$，如果 $m'=n'$，则 $m=n$，从而 $m \in n'$. 如果 $m'<n'$，即 $m+1<n+1$，则 $m<n$，由归纳假设得 $m\in n$. 这就完成了证明。

由于 $\omega$ 上的关系 $<$ 是一个良序，因此 $(\omega,\in)$ 也是一个良序集，它将作为我们构造序数的蓝本。

## 序数

**定义 8.2.2** 序数（ordinal）

满足以下性质的集合 $\alpha$ 称为**序数**：

- $\in$-反自反性：$x \not\in x$
- $\in$-传递性：$x \in y \in z\implies x \in z$
- $\in$-三分律：$x \in y,x=y,y \in x$ 有且仅有一个成立
- $\in$-良基性：$\alpha$ 的任意非空子集有 $\in$-极小元
- $\alpha$ 是传递集：$y \in x \in \alpha\implies y \in \alpha$

我们有时把“$\alpha$ 是序数”写作 $\alpha \in \mathbf{On}$. 事实上，所有序数构成的对象不是一个集合，而只能说是一个**类**。我们这里不会涉及集合与类的讨论，并且也不会把类与集合做任何运算。

根据传递性，我们知道序数的元素也是传递集。根据三分律与良基性，我们知道 $\alpha$ 非空子集的极小元就是最小元，并且我们可以知道这个最小元就是 $0=\varnothing$.

**定理 8.2.3**

设序数 $\alpha\neq 0$，则 $0 \in\alpha$.

**证明**

设 $\alpha$ 的 $\in$-最小元为 $\alpha_{0}$，假设 $\alpha_{0}\neq 0$，则存在 $x \in\alpha_{0}$，根据传递性有 $x \in\alpha$，这与 $\alpha_{0}$ 的 $\in$-最小性矛盾。

下面我们继续观察序数的构造，我们知道自然数 $n$ 是由它前面的自然数定义的：$n=\{ 0,1,\dots,n-1 \}$，序数是不是也一样呢？下面的定理给出了答案。

**定理 8.2.4**

设 $\alpha$ 是序数，$x \in\alpha$，则 $x$ 也是序数。

**证明**

$\alpha$ 是传递集，故 $x \subset\alpha$，因此 $x$ 上的关系 $\in$ 继承自 $\alpha$ 上的关系，从而 $x$ 是 $\in$-良序的，并且 $x$ 是传递集，于是 $x \in \mathbf{On}$.

现在我们就知道了：每个序数都由比它小的序数构成，即

$$
\alpha=\{ x \in\alpha \mid x \in \mathbf{On} \}
$$

接下来我们证明：序数的初始段与其端点同一。

**定理 8.2.5**

设 $\alpha$ 是序数，$x \in\alpha$，则 $\alpha_{x}=x$.

**证明**

我们有 $\alpha_{x}=\{ y \in \alpha \mid y \in x \}$，显然有 $\alpha_{x}\subset x$，设 $y \in x$，则 $y \in\alpha$，从而 $y \in\alpha_{x}$，这就完成了证明。

下面我们考察序数之间的关系，我们发现：序数的同构与相等是同一的。

**定理 8.2.6**

设 $\alpha,\beta$ 是序数，则 $\alpha \cong\beta \implies\alpha=\beta$.

**证明**

设 $f\colon \alpha \overset{\sim}{\to}\beta$，先证 $\forall x \in\alpha(f(x)=x)$. 我们使用超限归纳法，当 $x=0$ 时，由 $f$ 的保序性可知 $f(0)$ 是 $\beta$ 中的 $\in$-最小元，故 $f(0)=0$. 假设当 $t \in x$ 时有 $f(t)=t$，下证 $f(x)=x$.

设 $y \in x$，则 $y=f(y) \in f(x)$. 再设 $y \in f(x)$，则 $y \in\beta$，设 $u=f^{-1}(y)$，则 $f(u) \in f(x)$，于是 $u \in x$，从而根据 $f(u)=u$ 得 $f(u)=y \in x$.

既然 $f(x)=x$，故 $\alpha \subset\beta$，根据对称性，我们也有 $\beta \subset\alpha$，从而 $\alpha=\beta$.

由上面的定理立即得到序数之间的 $\in$-三分律：

**定理 8.2.7**

设 $\alpha,\beta$ 是序数，则 $\alpha \in\beta,\alpha=\beta,\beta \in\alpha$ 有且仅有一个成立。

**证明**

根据良序集基本定理，我们有 $\alpha_{x} \cong \beta,\alpha \cong \beta,\alpha \cong\beta_{y}$ 有且仅有一个成立，将初始段与其端点等同，再把同构与相等等同，则有 $\beta=x \in\alpha,\alpha=\beta,\alpha=y \in\beta$ 有且仅有一个成立。

下面的定理是本节的主要结果之一。

**定理 8.2.8**

设集合 $A\subset \mathbf{On}$，则 $A$ 是 $\in$-良序集。

**证明**

首先验证反自反性。设 $\alpha \in A$，假设 $\alpha \in\alpha$，则根据序数的反自反性有 $\alpha \not\in\alpha$，矛盾。然后是传递性，设 $\alpha \in\beta,\beta \in\gamma$，因为 $\gamma$ 是传递集，故 $\alpha \in\gamma$. 三分律是定理 8.2.7. 现在来证 $\in$-良基性。

设 $B\subset A,B\neq \varnothing$，任取 $\alpha \in B$，分两种情况讨论：

如果 $\alpha \cap B=\varnothing$，则 $\forall \beta \in B(\beta \not\in \alpha)$，这表明 $\alpha$ 是 $B$ 的 $\in$-极小元。

如果 $\alpha \cap B\neq \varnothing$，则取 $\alpha_{0}$ 为 $\alpha$ 的子集 $\alpha \cap B$ 的最小元，则 $\alpha_{0}$ 也是 $B$ 的最小元（假设不然，则有 $\gamma \in B,\gamma \in\alpha_{0}$，从而有 $\gamma \in\alpha \cap B$，这与 $\alpha_{0}$ 的最小性矛盾）。

现在我们就可以证明所有序数构成的类 $\mathbf{On}$ 不是集合。假设它是集合，那么 $\mathbf{On}\subset \mathbf{On}$ 是 $\in$-良序集，并且它是传递集（定理 8.2.4），故 $\mathbf{On}\in \mathbf{On}$，这与反自反性矛盾。因此，$\mathbf{On}$ 与所有集合构成的类 $\mathbf{V}$ 一样，被称为是一个**真类**。

下面，我们要在序数之间定义运算，根据自然数的 $\in$ 与 $<$ 的同一性，我们也在序数上定义序关系如下：

$$
\alpha<\beta \iff \alpha \in\beta
$$

显然，我们有 $\alpha\leq\beta \iff \alpha \subset\beta$.

我们仍然用 $\alpha'$ 表示 $\alpha$ 的后继：$\alpha'=\alpha \cup \{ \alpha \}$，下面我们证明，序数的后继也是序数。

**定理 8.2.9**

设 $\alpha$ 是序数，则 $\alpha'$ 也是序数。

**证明**

$\alpha'$ 是良序集，下证 $\alpha'$ 是传递集。设 $y \in x \in\alpha'$，分两种情况讨论：

如果 $x=\alpha$，则 $y \in\alpha$，即 $y \in\alpha'$.

如果 $x \in\alpha$，则由 $\alpha$ 的传递性有 $y \in\alpha$，同样有 $y \in\alpha'$. 这就完成了证明。

现在，我们就可以迈出通往超穷世界的第一步：对 $\omega$ 取后继，就得到了序数 $\omega',\omega'',\omega''',\dots$，按照自然数的习惯，我们把它们写成

$$
\omega+1,\omega+2,\omega+3,\dots
$$

除了取后继，还有什么方法可以构造序数？下面的定理给出了答案。

**定理 8.2.10**

设 $A\subset \mathbf{On}$，则 $\bigcup A$ 也是序数，并且是 $A$ 的最小上界。

**证明**

由于序数的元素也是序数，故 $\bigcup A\subset \mathbf{On}$，从而是良序集，设 $y \in x \in \bigcup A$，则存在序数 $x \in\alpha$，从而 $y \in\alpha \subset \bigcup A$，从而 $\bigcup A$ 是一个序数。

对任意 $\alpha \in A$，有 $\alpha \subset \bigcup A$，即 $\alpha\leq \bigcup A$，因此 $\bigcup A$ 是 $A$ 的上界。设 $\beta<\bigcup A$，即 $\beta \in \bigcup A$，即 $\beta \in\alpha \in A$，即 $\beta<\alpha$，从而 $\beta$ 不是 $A$ 的上界，这就完成了证明。

对序数构成的集合取并集可以构成新的序数，例如，自然数集 $\omega$ 就是所有自然数 $\{ 0,1,2,\dots \}$ 的并集，但它不是某个序数的后继。这两种序数之间的差别启发我们给出下面的定义：

**定义 8.2.11** 后继序数（successor ordinal），极限序数（limit ordinal）

设 $\alpha \in \mathbf{On}$，如果存在序数 $\beta$ 使得 $\beta'=\alpha$，则称 $\alpha$ 是**后继序数**，如果 $\alpha$ 不是 $0$ 也不是后继序数，则称 $\alpha$ 是**极限序数**。

我们来考察一下极限序数的基本性质。

**定理 8.2.12**

序数 $\alpha$ 是极限序数当且仅当 $\alpha\neq 0$ 且 $\beta \in\alpha\implies\beta' \in\alpha$.

**证明**

如果 $\beta \in\alpha\implies\beta' \in\alpha$，假设 $\alpha$ 是后继序数，则存在 $\beta'=\alpha$，于是 $\beta \in\alpha$，从而 $\beta' =\alpha \in\alpha$，与反自反性矛盾。

反之，设 $\alpha$ 是极限序数，设 $\beta \in\alpha$，假设 $\beta'=\alpha$，则 $\alpha$ 是后继序数，矛盾。假设 $\alpha \in\beta'$，则无论是 $\alpha=\beta$ 还是 $\alpha \in\beta$ 都与三分律矛盾。因此 $\beta' \in\alpha$.

上述定理表明，极限序数一定是归纳集，就像 $\omega$ 一样。下面的定理指出了另一个极限序数的特征：它是自身的最小上界。

**定理 8.2.13**

序数 $\alpha$ 是极限序数当且仅当 $\alpha\neq 0$ 且 $\alpha=\bigcup\alpha$.

**证明**

设 $\alpha$ 是极限序数，由于 $\alpha$ 是传递集，故 $\bigcup\alpha \subset\alpha$，现设 $x \in\alpha$，于是 $x \in x' \in\alpha$，从而 $x \in \bigcup\alpha$.

设 $\alpha=\bigcup\alpha$，假设 $\alpha$ 是后继序数，则有 $\alpha=\beta'$，从而

$$
\alpha=\bigcup\alpha=\bigcup\beta'=\beta \in \beta'=\alpha
$$

这与反自反性矛盾。

我们看到，与极限序数不同，后继序数的最小上界是它的最大元：$\bigcup\beta'=\beta$.

## 替换公理模式

接下来，我们就可以使用后继与并集来源源不断地构造序数了。然而，这里出现了一个问题：序数

$$
\omega,\omega+1,\omega+2,\omega+3,\dots
$$

构成的对象是否是一个集合？直观上看它似乎是集合，因为它与自然数似乎可以构成一种“一一对应”，然而，这种一一对应无法使用精确的语言（即双射）来描述，因为我们都不确定它是否是一个集合。为了解决这种情况，我们就需要一条新的公理（模式），来肯定这种与已知集合构成对应关系的集合构造，这就是**替换公理模式**。

**公理 ZF7** 替换公理模式

设 $\varphi$ 是一个性质（带有参数 $p$ ），并且满足单值性条件：

$$
\varphi(x,y,p),\varphi(x,z,p) \implies y=z
$$

那么对任意集合 $X$ 和 $p$，存在集合

$$
Y=\{ y \mid \exists x \in X\ \varphi(x,y,p)\}
$$

读者可以对比一下上面的公理和第一章的公理 ZF7，在第一章中，我们把 $Y$ 描述为函数 $F$ 的值域 $F[X]$，然而这是不准确的，因为我们无法确定 $F$ 的陪域，相反，这个陪域正是公理中所要声明存在的集合。事实上，$F$ 只能是一种**类函数**，而非集合间的映射。

利用替换公理，我们就可以肯定 $\{ \omega+n \mid n \in \omega \}$ 是一个集合，对其取并集，我们就得到了一个极限序数，我们把它记为 $\omega+\omega$ 或者 $\omega\cdot 2$. 在这之后，还会有 $\omega\cdot 3,\omega\cdot 4,\dots,\omega\cdot \omega=\omega^{2}$，再接下去就是 $\omega^{2},\omega^{3},\dots,\omega^{\omega}$，以及 $\omega^{\omega},\omega^{\omega^{\omega}},\dots$

下面的定理是序数理论的中心定理之一，它使得我们能够把序数应用于超穷世界。

**定理 8.2.14** 序型定理

设 $A$ 是良序集，则存在唯一的序数 $\alpha$ 使得 $A\cong \alpha$.

**证明**

唯一性是显然的，因为序数的同构等同于相等。下面证明存在性。

构造集合 $B=\{ x \in A\mid \exists \beta (\beta \cong A_{x}) \}$，则 $x \in A$ 所对应的 $\beta$ 是唯一的，利用替换公理，我们可以肯定

$$
\alpha=\{ \beta \mid \exists x \in A(\beta \cong A_{x}) \}
$$

是一个集合。特别地，$\alpha \subset \mathbf{On}$，从而是良序集，下证 $\alpha$ 是传递集。

设 $\gamma \in\beta \in\alpha$，设 $\beta \cong A_{x}$，取 $f\colon \beta \overset{\sim}{\to}A_{x}$，则

$$
\gamma=\beta_{\gamma} \cong (A_{x})_{f(\gamma)} = A_{f(\gamma)}
$$

从而 $\gamma \in\alpha$，因此 $\alpha$ 是序数。下证 $\alpha \cong A$. 根据良序集基本定理，只需排除 $\alpha \cong A_{x}$ 和 $\alpha_{\beta}\cong A$ 即可。

假设 $\alpha \cong A_{x}$，则 $\alpha \in\alpha$，与反自反性矛盾。假设 $A\cong \alpha_{\beta}=\beta$，因 $\beta \in\alpha$，故存在 $x \in A$ 使得 $\beta \cong A_{x}$，从而 $A\cong A_{x}$，矛盾。这就完成了证明。

根据上述定理，每个良序集都有它对应的序数 $\alpha$，我们把它叫做良序集 $A$ 的**序型**。注意，在同一集合上可以定义不同的良序，它们的序型可能不同，例如，整数上的良序 $0,1,-1,2,-2,\dots$ 具有序型 $\omega$，而良序 $0,1,2,\dots,-1,-2,\dots$ 具有序型 $\omega\cdot 2$.

## 正则公理

到目前为止，ZF 公理系统（不含选择公理）还剩下最后一个公理没有介绍：正则公理。这条公理的提出是为了排除一种异常集合的存在，这种集合能够形成 $\in$-降链：

$$
\cdots \in x_{n} \in \cdots \in x_{2} \in x_{1} \in x_{0}
$$

典型的例子如包含自身的集合 $x \in x$，$\in$-降链的存在意味着集合的原始组成可以不存在，这就使得我们无法从逻辑上否定某些非直观的构造，而这些构造在古典集合论中是需要极力避免的。为了消除这种异常集，我们给出以下公理：

**公理 ZF8** 正则公理

任意非空集合都有 $\in$-极小元。

我们来把上述“极小元”的概念展开，设 $S\neq \varnothing$，且 $x \in S$ 是极小元，则对任意 $y \in S$，都有 $y \not\in x$，这也就是说 $S\cap x=\varnothing$. 因此上面的表述与第一章的表述是一致的。

正则公理的一个直接推论就是对任意集合，都有 $x \not\in x$，从而我们的序数定义得到了大大的简化：集合 $\alpha$ 上的 $\in$-反自反性以及 $\in$-良基性自动得到满足，不仅如此，$\in$-三分律可以推出 $\in$-传递性，下面我们来证明这一点。

**定理 8.2.15**

设集合 $\alpha$ 满足 $\in$-三分律，则 $\in$ 在 $\alpha$ 上具有传递性。

**证明**

设 $x,y,z \in\alpha,x \in y \in z$，我们要证 $x \in z$. 根据三分律，我们只需证明 $z \in x,z=x$ 都会推出矛盾。

假设 $z \in x$，则有 $\in$-降链：$\cdots\in x \in y \in z \in x$，这与正则公理矛盾。假设 $z=x$，同样有 $\in$-降链：$\cdots\in x \in y \in x$，与正则公理矛盾。这就完成了证明。

至此，我们就可以说：**序数**是满足 $\in$-三分律的传递集。

## 超限归纳法

之前，我们已将归纳法从自然数推广到良序集，现在，我们可以更进一步，将归纳法推广到序数类 $\mathbf{On}$ 上，用于证明一类全称命题。不过，由于 $\mathbf{On}$ 是一个真类，故定理的形式也要做一定的修改。

**定理 8.2.16** 超限归纳法

设 $\varphi$ 是一个性质，如果对任意序数 $\alpha$ 都有 $\forall \beta<\alpha\ \varphi(\beta)\implies\varphi(\alpha)$，则对任意 $\alpha$ 都有 $\varphi(\alpha)$ 成立。

**证明**

假设存在序数 $\alpha$ 使得 $\varphi(\alpha)$ 不成立，则构造集合

$$
A=\{ \beta<\alpha \mid \varphi(\beta) \text{不成立} \}
$$

分两种情况讨论：如果 $A=\varnothing$，则 $\forall \beta<\alpha\ \varphi(\beta)$ 是一个空真，从而有 $\varphi(\alpha)$ 成立，与假设矛盾。如果 $A\neq \varnothing$，则根据 $A$ 的 $\in$-良序性，存在 $\in$-最小元 $\alpha_{0}$，于是 $\forall \beta<\alpha_{0}\ \varphi(\beta)$ 成立，从而 $\varphi(\alpha_{0})$ 成立，与 $A$ 的定义矛盾。

既然序数是对自然数的推广，而我们又有了序数上的归纳法，那么下一步自然就是将自然数上的递归原理（定理 1.2.2）推广至 $\mathbf{On}$，这使得我们能够根据序数 $\alpha$ 之前的序数所被赋予的值，为 $\alpha$ 赋予一个值。这实际上就是递归地在 $\mathbf{On}$ 上定义了一个类函数：满足单值性条件的性质 $\psi$，且对任意序数 $\alpha$ 存在集合 $y$ 使得 $\psi(\alpha,y)$ 成立，我们可以简写为 $y=\psi(\alpha)$.

**定理 8.2.17** 超限递归原理

设 $\varphi$ 是一个类函数，则存在唯一的类函数 $\psi$（称为序数函数）满足对任意序数 $\alpha$ 有

$$
\psi(\alpha)=\varphi(\psi|_{\alpha})
$$

其中函数 $\psi|_{\alpha}\colon \alpha\to \psi[\alpha]$ 是 $\psi$ 在序数 $\alpha$ 上的限制。

为节省篇幅，上述定理的证明我们将放到附录中。

与自然数类似，我们可以使用定理 8.2.17 在序数上递归地定义加法和乘法。

**定义 8.2.18** 序数的加法

设 $\alpha$ 是序数，递归地定义 $\mathbf{On}$ 上的**加法**如下：

$$
\begin{cases}
\alpha+0=\alpha \\
\alpha+\beta'=(\alpha+\beta)' &, \beta \text{是后继序数} \\
\alpha+\beta=\bigcup \{ \alpha+\gamma \mid \gamma<\beta \} &, \beta \text{是极限序数}
\end{cases}
$$

**定义 8.2.19** 序数的乘法

设 $\alpha$ 是序数，递归地定义 $\mathbf{On}$ 上的**乘法**如下：

$$
\begin{cases}
\alpha\cdot 0 = 0 \\
\alpha\cdot\beta' = \alpha\cdot\beta +\alpha &, \beta \text{是后继序数} \\
\alpha\cdot\beta = \bigcup \{ \alpha \cdot\gamma\mid \gamma<\beta \} &, \beta \text{是极限序数}
\end{cases}
$$

类似地还可以定义序数的乘方。它们是自然数运算的自然推广，其中结合律对于序数的运算仍然成立，但是交换律不再成立，比如 $\omega+1\neq 1+\omega$，后者等于 $\omega$.

## Hartogs 数

对于良序集，根据序型定理，存在唯一的一个序数与之同构，从而我们可以使用序数 $0,1,2,\dots$ 为集合中的元素编号。对于一般的集合，我们尚不知道是否可以在其上建立良序，然而，对于任意集合 $A$，我们可以确定，存在一个序数 $\alpha$，其元素足够用来给集合 $A$ 的元素编号。这就是集合 $A$ 的 **Hartogs 数**。

**定义 8.2.20** Hartogs 数

集合 $A$ 的 **Hartogs 数**是序数 $\alpha$，其满足：

1. 不存在 $\alpha$ 到 $A$ 的单射。
2. 对任意 $\beta<\alpha$，有 $\beta \preceq A$.

换言之，$A$ 的 Hartogs 数是最小的满足 $\alpha \not\preceq A$ 的序数。不存在 $\alpha$ 到 $A$ 的单射表明：使用 $\alpha$ 的元素给 $A$ 的元素编号，其号码永远不会用完。

下面我们来实际构造出集合 $A$ 的 Hartogs 数，其主要用到下面的引理：

**引理 8.2.21**

设 $A$ 是集合，则 $A^{+}=\{ \beta \mid \beta \preceq A,\beta \in \mathbf{On} \}$ 是序数。

**证明**

首先假设 $A^{+}$ 是集合，则 $A^{+}$ 是 $\in$-良序集，我们只需证明它是传递集。设 $\gamma \in\beta \in A^{+}$，则由于 $\beta$ 是传递集，有 $\gamma \subset\beta \preceq A$，于是 $\gamma \preceq A$，从而 $\gamma \in A^{+}$，因此 $A^{+}$ 是序数。

现在我们要证 $A^{+}$ 是集合而不是真类。构造集合

$$
\{ (B,<) \in \mathscr{P}(A)\times \mathscr{P}(A^{2}) \mid (B,<) \text{是良序集} \}
$$

根据序型定理，每个 $B$ 都有唯一的序数 $\beta$ 使得 $B\cong\beta$，根据替换公理，由这些序数构成的对象 $\mathscr{B}=\{ \beta \mid (\beta,\in) \cong (B,<)\}$ 是集合，下面我们证明这个集合就是 $A^{+}$.

设 $\beta \in \mathscr{B}$，则 $\beta \cong B \subset A$，于是显然有 $\beta \preceq A$，即 $\beta \in A^{+}$. 设 $\beta \in A^{+}$，则存在 $\beta\to A$ 的单射 $f$，利用 $\beta$ 上的良序，我们可以诱导出 $f[\beta]\subset A$ 上的良序 $<$，从而 $(\beta,\in)\cong(f[\beta],<)$，即 $\beta \in \mathscr{B}$，这就完成了证明。

**定理 8.2.22**

任意集合 $A$ 的 Hartogs 数为 $A^{+}=\{ \beta \mid \beta \preceq A,\beta \in \mathbf{On} \}$.

**证明**

根据引理，$A^{+}$ 是一个序数，记为 $\alpha$. 我们来验证 $\alpha$ 满足两条性质。

假设有 $\alpha\to A$ 的单射，则 $\alpha \in A^{+}=\alpha$，这与反自反性矛盾。设 $\beta<\alpha$，则 $\beta \in\alpha=A^{+}$，即 $\beta\preceq A$，这就完成了证明。

现在，我们证明了每个集合都有足够的序数对其元素进行编号。我们考虑一下：是否可以通过 $A^{+}$ 上的良序诱导出 $A$ 上的良序？直观上来说，似乎是可以的，但我们不能确定：编号过程涉及无限次的选取，但现有的公理体系无法保证这一过程是合法的。因此，问题出在**选择**上，这就是下一节我们要讨论的主题：**选择公理**。

# Section 3: 选择公理

在数学研究中，选择公理是一条特殊的公理：它所断言存在的集合极为基础和直观，以至于我们在使用它时通常是不知不觉的。然而，它的一些推论又是如此的反直觉，以至于有相当一部分人怀疑它的真实性。为了认识选择公理的特殊性，我们从有限选取开始讲起。

给定集合 $A_{0}\neq \varnothing$，那么显然存在 $x_{0} \in A_{0}$. 增加一个集合，设 $A_{0},A_{1}\neq \varnothing$，显然也存在 $x_{0}\in A_{0},x_{1} \in A_{1}$，换言之，$(x_{0},x_{1})\in A_{0}\times A_{1}$，并且称 $g=\{ (A_{0},x_{0}),(A_{1},x_{1}) \}$ 是 $\{ A_{0},A_{1} \}$ 上的选择函数。

根据归纳法，我们可以扩展到任意有限次选取：如果 $A_{0},\dots,A_{n-1}\neq \varnothing$，则 $\displaystyle \prod_{i=0}^{n-1}A_{i}=A_{0}\times\dots \times A_{n-1}\neq \varnothing$，其中的元素为有限序列 $(x_{i})_{i=0}^{n-1}$，满足 $x_{i}\in A_{i}$.

然而，到了无限次选取，情况就不同了。

**定义 8.3.1** 无穷直积

集合 $\{ A_{i} \mid i \in I \}$ 的**直积**定义为

$$
\prod_{i \in I} A_{i}=\left\{ f\colon I\to \bigcup_{i \in I} A_{i} \middle| f(i) \in A_{i} \right\} 
$$

当 $I=\omega$ 时，$\prod_{i \in I}A_{i}$ 中的元素（如果有的话）是无限序列 $(x_{i})_{i=0}^{\infty}$，其中 $x_{i} \in A_{i}$. 而在更极端的情况下，$I$ 本身是一个不可数集，当 $A_{i}$ 都非空时，可以肯定 $\prod_{i \in I}A_{i}$ 是非空的吗？在 ZF 公理系统中，这个问题是不可判定的，因此，我们可以将另一条公理添加到我们的系统中，从而构成所谓的 ZFC 公理系统：

**公理 AC** 选择公理

如果对任意 $i \in I$ 有 $A_{i}\neq \varnothing$，则 $\prod_{i \in I}A_{i}\neq \varnothing$.

通常，我们把上述公理写成更为常用的形式：由非空集构成的集合上存在选择函数。比如满足 $g(A_{i})=f(i)$ 的函数 $g$ 就是一个选择函数，因此上述公理与第一章的表述是等价的。

选择公理的争议性质来源于它的**非构造性**：我们不知道这个选择函数是什么样的，我们只知道它存在。实际上，非构造性证明在分析学中非常普遍，例如定理 3.2.4，5.1.3 以及 7.2.6 的证明中，都涉及到了无限次的、任意的选取，这种操作不使用选择公理是无法进行的。

选择公理的等价形式在各个数学领域中都有出现，下面我们就来介绍其中的一些形式。

## 良序原理

我们接续上一节 Hartogs 数的讨论。任取一个非空集合 $A$，要构造 $A$ 上的良序，我们可以用其 Hartogs 数为其元素编号，也就是说，我们递归地构造函数

$$
\begin{gather}
f(0)=x_{0}\in A \\
f(1)=x_{1}\in A \setminus \{ x_{0} \} \\
f(2)=x_{2}\in A \setminus \{ x_{0},x_{1} \} \\
\dots \\
f(\gamma)=x_{\gamma} \in A \setminus f[\gamma] \\
\dots
\end{gather}
$$

到了第 $\gamma_{0}$ 步，$A$ 被抽空：$A\setminus f[\gamma_{0}]=\varnothing$，此时利用序数上的良序 $\in$ 我们就可以诱导出 $A$ 上的良序。但此时 $A^{+}$ 中的号码还未用完，令剩下的号码都对应到一个不在 $A$ 中的元素即可。我们看到这里涉及到了无限次的选取，因此我们需要使用选择公理。

**定理 8.3.2** 良序原理（Well-ordering Principle）

任意集合上都存在良序。

**证明**

如果 $A=\varnothing$，则 $A$ 上只有空关系 $\varnothing$，此时 $A$ 自动成为良序集。下设 $A$ 非空。

取 $\mathscr{P}(A)\setminus \{ \varnothing \}$ 上的选择函数 $g$，令 $\alpha=A^{+},s_{0} \not\in A$，递归地定义 $\alpha$ 上的函数 $f$ 如下：

$$
f(\gamma)=\begin{cases}
g(A \setminus f[\gamma]) &, A \setminus f[\gamma]\neq \varnothing \\
s_{0} &, A \setminus f[\gamma]=\varnothing
\end{cases}
$$

假设存在 $\gamma_{0}$ 是使得 $A \setminus f[\gamma]=\varnothing$ 的最小 $\gamma$，此时 $A=f[\gamma_{0}]$，于是可以用序数 $\gamma_{0}$ 上的良序 $\in$ 诱导出 $A$ 上的良序。现在证明 $\gamma_{0}$ 的存在性，反设其不存在，则对任意 $\gamma<\alpha$，都有 $f(\gamma)=g(A\setminus f[\gamma])$，即 $f(\gamma)\in A \setminus f[\gamma]$，又根据 $f$ 的单性，我们有 $\alpha \preceq A$，这与 Hartogs 数的定义矛盾。

利用良序原理，我们可以将定理 8.1.15 推广至所有集合：

**定理 8.3.3** 势的可比较性

设 $A,B$ 是集合，则 $A\preceq B$ 与 $B\preceq A$ 至少有一个成立。

**证明**

在 $A,B$ 上建立良序，然后应用定理 8.1.15 即可。

良序原理使我们能够将超限归纳法进一步推广至任意集合，它是我们能够在超穷世界中建立秩序的肯定。下面，我们来证明选择公理、良序原理、势可比较性都是等价的。

**定理 8.3.4**

选择公理 $\iff$ 良序原理 $\iff$ 势可比较性

**证明**

我们只需证明两个 $\impliedby$ 命题。首先假设良序原理成立，设 $A$ 的元素是非空集，我们可以在 $\bigcup A$ 上建立良序，然后定义 $A$ 上的选择函数 $g$ 如下：

$$
g(x)=\min x, x \in A
$$

根据良序的性质，可知 $\min x$ 存在且唯一，从而 $g$ 是良定的。

下面假设势可比较，我们要在集合 $A$ 上建立良序。考虑其 Hartogs 数 $A^{+}$，则有 $A\preceq A^{+}$，利用单射 $f\colon A\to A^{+}$ 以及 $A^{+}$ 上的良序 $\in$ 就可以诱导出 $A$ 上的良序，这就完成了证明。

## 极大原理

除了良序原理外，还有一个选择公理的等价形式是 Zorn 引理，它断言了某种偏序集的极大元的存在性。由于偏序是广泛存在的结构，因此 Zorn 引理出现在数学的各个分支中。

**定理 8.3.5** Zorn 引理

若非空偏序集 $A$ 的任一链（全序子集）都有上界，则 $A$ 有极大元。

**证明**

我们先做一些分析。要找到 $A$ 的极大元，我们可以从某个元素 $x_{0}$ 出发，取出递增序列

$$
x_{0}<x_{1}<x_{2}<\cdots<x_{\gamma}<\cdots
$$

每一步都要在前面元素的严格上界中选取，若某一步取到了极大元，则停止。$A^{+}$ 的性质保证了这一过程一定会停止，最后得到的全序子集的上界就是 $A$ 的极大元。由于选择的过程是随意的，因此要用到选择公理。

下面我们来严格地写出证明。取 $\mathscr{P}(A)\setminus \{ \varnothing \}$ 的选择函数 $g$，设非空集 $X \subset A$，记 $X$ 的严格上界构成的集合为 $S(X)$，设 $\alpha=A^{+},s_{0} \not\in A$，递归地定义 $\alpha$ 上的函数 $f$ 如下：

$$
f(\gamma)=\begin{cases}
g(S(f[\gamma])) &, S(f[\gamma])\neq \varnothing \\
s_{0} &, S(f[\gamma])=\varnothing
\end{cases}
$$

令 $\gamma_{0}$ 是使得 $S(f[\gamma])=\varnothing$ 的最小 $\gamma$（ $\gamma_{0}$ 一定存在，否则 $\alpha\preceq A$ ），则 $f[\gamma_{0}]$ 是 $A$ 中的链，其上界就是 $A$ 的极大元。

作为 Zorn 引理的一个应用，我们给出下面的定理：

**定理 8.3.6** Tukey 引理

如果非空集 $A$ 满足有限特征性质：$x \in A$ 当且仅当 $x$ 的所有有限子集属于 $A$，则 $A$ 有 $\subset$-极大元。

**证明**

显然 $\subset$ 是非空集 $A$ 上的偏序，设 $B$ 是 $A$ 上的 $\subset$-链，则对任意 $x \in B$ 有 $x \subset \bigcup B$，为使用 Zorn 引理，我们只需证明 $\bigcup B\in A$，从而 $\bigcup B$ 是 $B$ 的上界。

根据有限特征性质，只需证明 $\bigcup B$ 的有限子集属于 $A$，又 $B$ 是 $\subset$-链，故任意 $\bigcup B$ 的有限子集也是某个 $x \in B$ 的有限子集，再由 $B\subset A$ 以及有限特征性质知 $\bigcup B$ 的有限子集属于 $A$，从而 $\bigcup B\in A$，这就完成了证明。

Zorn 引理的另一重要推论如下所示：

**定理 8.3.7** Hausdorff 极大原理

偏序集的任一链都可以扩张为极大链。

**证明**

如果 $A=\varnothing$，则其上只有空链 $\varnothing$，它是极大链。下设 $A$ 非空。

设 $B$ 是偏序集 $A$ 上的 $<$-链，构造集合

$$
\mathscr{C}=\{ C \mid B\subset C, C \text{是} A \text{上的链} \}
$$

则 $\mathscr{C}$ 非空，并按 $\subset$ 成偏序集，且其 $\subset$-极大元就是 $A$ 上的极大链。

设 $\mathscr{P}$ 是 $\mathscr{C}$ 上的 $\subset$-链，如果 $\mathscr{P}=\varnothing$，则 $\mathscr{C}$ 上的任意元素都是 $\mathscr{P}$ 的上界，如果 $\mathscr{P}\neq \varnothing$，考虑集合 $\bigcup \mathscr{P}$，它是 $A$ 上的 $<$-链，且对任意 $P \in \mathscr{P}$ 有 $P \subset \bigcup \mathscr{P}$，故 $B\subset \bigcup \mathscr{P}$，从而 $\bigcup \mathscr{P} \in \mathscr{C}$，即 $\mathscr{P}$ 在 $\mathscr{C}$ 中有上界，由 Zorn 引理知 $\mathscr{C}$ 的 $\subset$-极大元存在。

Zorn 引理、Tukey 引理、Hausdorff 极大原理都断言了某类偏序集上极大元的存在性，它们是选择公理在偏序结构上的体现。

**定理 8.3.8**

选择公理 $\iff$ Zorn 引理 $\iff$ Tukey 引理 $\iff$ Hausdorff 极大原理

**证明**

我们先来证明 Tukey 引理 $\implies$ 选择公理。设 $A$ 的元素为非空集，且 $A\neq \varnothing$（ $A=\varnothing$ 的情况是平凡的），构造集合

$$
\mathscr{B}=\{ g \mid g \text{是} X \subset A \text{上的选择函数} \}
$$

则 $\mathscr{B}\neq \varnothing$，且 $\mathscr{B}$ 具有有限特征性质，由 Tukey 引理知 $\mathscr{B}$ 有 $\subset$-极大元 $f$，下证 $\mathrm{Dom}(f)=A$. 反设 $A\setminus \mathrm{Dom}(f)\neq \varnothing$，则有非空集 $x \in A\setminus \mathrm{Dom}(f)$，取 $y \in x$，则 $f \cup \{ (x,y) \} \in \mathscr{B}$，这与 $f$ 的极大性矛盾。因此 $f$ 是 $A$ 上的选择函数。这就证明了前三个命题是等价的。

下证 Hausdorff 极大原理 $\implies$ Zorn 引理。设非空偏序集 $A$ 的任一链有上界，利用 Hausdorff 极大原理将 $A$ 上的某个链扩张为极大链 $B$，则 $B$ 在 $A$ 中有上界 $x$，我们要证 $x$ 是 $A$ 的极大元。事实上，假设 $x$ 不是极大元，则存在 $y \in A$ 使得 $x<y$，从而 $B\cup \{ y \}$ 也是 $A$ 上的链，与 $B$ 的极大性矛盾。这就完成了证明。

现在让我们总结一下选择公理的等价形式：

1. 选择公理
2. 良序原理
3. 势的可比较性
4. Zorn 引理
5. Tukey 引理
6. Hausdorff 极大原理

最后，我们以一个选择公理的常用推论结束本章的讨论：

**定理 8.3.9**

任意向量空间都有基。

**证明**

给定向量空间 $V$，构造集合 $\mathcal{S}=\{ S \subset V \mid S \text{线性无关} \}$，则 $\mathcal{S}$ 满足有限特征性质（线性无关集的定义：$S$ 线性无关当且仅当 $S$ 的所有有限子集线性无关），由 Tukey 引理知 $\mathcal{S}$ 有 $\subset$-极大元 $B$（称为 $V$ 的极大线性无关集），下证 $\mathrm{span}(B)=V$.

假设 $\mathrm{span}(B)\neq V$，则存在 $v \in V\setminus \mathrm{span}(B)$，从而 $B\cup \{ v \}$ 也线性无关，这与 $B$ 的极大性矛盾。因此 $B$ 是 $V$ 的基。