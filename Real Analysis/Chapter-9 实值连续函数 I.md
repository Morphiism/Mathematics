在前几章中，我们着重研究了序列：从 $\mathbb{N}$ 到 $\mathbb{R}$ 的函数。从本章开始，我们将研究定义在一个连续统（实数的不可数子集）上的函数，我们将对它们做大量运算，包括取极限、求导、积分等操作，以及研究与之密切相关的**连续函数**的概念。

# Section 1: 实数的子集

实数的子集显然有无穷多个，但实数的一些特殊子集才是我们经常遇到的，其中**区间**就是这样的一类集合。在第 5 章我们已经定义了区间，下面我们补充一些概念。

**定义 9.1.1** 区间（interval）

设 $a,b \in \mathbb{R}^{*}$，则集合 $(a,b),(a,b],[a,b),[a,b]$ 称为**区间**，$a,b$ 分别称为区间的**左端点**和**右端点**。如果 $a<b$，则称区间是**非退化的**，反之则称区间是**退化的**。

分析的绝大部分理论都建立在非退化的区间上。

和序列类似，实数集也有附着点的概念，下面我们给出定义，注意它和序列的附着点的区别。

**定义 9.1.2** 附着点（adherent point），闭包（closure）

设 $X\subset \mathbb{R},x \in \mathbb{R}$，称 $x$ 是 $X$ 的**附着点**，如果对任意 $\varepsilon>0$，存在 $y \in X$ 使得 $d(x,y)<\varepsilon$. 如果 $\sup X=+\infty$，则称 $+\infty$ 是 $X$ 的附着点，如果 $\inf X=-\infty$，则称 $-\infty$ 是 $X$ 的附着点。

$X$ 的**闭包**定义为 $X$ 的所有有限附着点构成的集合，记作 $\overline{X}$.

显然，如果 $x \in X$，那么 $x$ 一定是 $X$ 的附着点，从而 $X\subset  \overline{X}$. 下面我们再给出闭包的一些性质。

**定理 9.1.3**

设 $X,Y \subset \mathbb{R}$，则 $\overline{X\cup Y}=\overline{X}\cup \overline{Y},\overline{X\cap Y}\subset  \overline{X}\cap \overline{Y}$，并且如果 $X\subset Y$，则 $\overline{X}\subset  \overline{Y}$.

**证明**

设 $x \in \overline{X\cup Y}$，则对任意 $\varepsilon>0$ 存在 $y \in X\cup Y$ 使得 $d(x,y)<\varepsilon$，假设 $x \not\in \overline{X}\cup \overline{Y}$，即 $x$ 不是 $X$ 或 $Y$ 的附着点，则存在 $\varepsilon_{0}>0$ 使得对任意 $y \in X$ 以及 $y \in Y$ 都有 $d(x,y)\geq\varepsilon_{0}$，矛盾。故 $\overline{X\cup Y}\subset  \overline{X}\cup \overline{Y}$. 

反之，如果 $x \in \overline{X}\cup \overline{Y}$，当 $x \in \overline{X}$ 时，存在 $y \in X\subset X\cup Y$ 使得 $d(x,y)<\varepsilon$，于是 $x \in \overline{X\cup Y}$，当 $x \in \overline{Y}$ 时同理。因此 $\overline{X\cup Y}=\overline{X}\cup \overline{Y}$.

设 $x \in \overline{X\cap Y}$，则有 $y \in X\cap Y$ 使得 $d(x,y)<\varepsilon$，由于 $X\cap Y\subset X,X\cap Y\subset Y$，故 $x \in \overline{X}\cap \overline{Y}$，因此 $\overline{X\cap Y}\subset  \overline{X}\cap \overline{Y}$.

最后，设 $X\subset Y,x \in \overline{X}$，则有 $y \in X\subset Y$ 使得 $d(x,y)<\varepsilon$，故 $x \in \overline{Y}$. 这就完成了证明。

现在我们来计算一些闭包，下面的定理给出了一种从已有的闭包计算出其它集合闭包的方法。

**定理 9.1.4**

设 $X,Y\subset \mathbb{R}$，且 $X\subset Y\subset  \overline{X}$，则 $\overline{Y}=\overline{X}$.

**证明**

首先由 9.1.3 可知 $\overline{X}\subset \overline{Y}\subset  \overline{\overline{X}}$，下面只需证 $\overline{\overline{X}}=\overline{X}$，即 $\overline{X}$ 的附着点仍然是 $X$ 的附着点。

设 $x \in \overline{\overline{X}}$，则存在 $y \in \overline{X}$ 使得 $d(x,y)<\varepsilon$，又由于 $y \in \overline{X}$，故存在 $z \in X$ 使得 $d(y,z)<\varepsilon$，从而 $d(x,z)\leq d(x,y)+d(y,z)=2\varepsilon$，由 $\varepsilon$ 的任意性可知 $x \in \overline{X}$，这就完成了证明。

利用上述定理，我们来计算一些特殊子集的闭包。

**定理 9.1.5**

设实数 $a<b$，则区间 $(a,b),(a,b],[a,b),[a,b]$ 的闭包是 $[a,b]$，区间 $(-\infty,b),(-\infty,b]$ 的闭包是 $(-\infty,b]$，区间 $(a,+\infty),[a,+\infty)$ 的闭包是 $[a,+\infty)$，最后，$\overline{\mathbb{N}}=\mathbb{N},\overline{\mathbb{Z}}=\mathbb{Z},\overline{\mathbb{Q}}=\mathbb{R},\overline{\mathbb{R}}=\mathbb{R}$.

**证明**

对于 $(a,b)$ 等区间，我们只需证明 $(a,b)$ 的闭包是 $[a,b]$，其余的根据 9.1.5 即得。根据实数的稠密性，显然 $[a,b]$ 中的每个点都附着于 $(a,b)$，下证只有这些点附着于 $(a,b)$. 不妨设 $x>b$，则取 $\varepsilon=x-b$，则不存在 $y \in(a,b)$ 使得 $d(x,y)<\varepsilon$，故 $x$ 不是 $(a,b)$ 的附着点。$x<a$ 时同理。

使用同样的方法，我们可以证明 $(a,+\infty)$ 的闭包是 $[a,+\infty)$，$(-\infty,b)$ 的闭包是 $(-\infty,b]$，以及 $\overline{\mathbb{R}}=\mathbb{R}$.

假设 $\mathbb{Z}$ 有除 $\mathbb{Z}$ 以外的附着点，设为 $x$，则存在唯一的整数 $m$ 使得 $m<x<m+1$，令 $\varepsilon=\min(x-m,m-x+1)$，则不存在 $y \in \mathbb{Z}$ 使得 $d(x,y)<\varepsilon$，这与 $x$ 的定义矛盾。故 $\overline{\mathbb{Z}}=\mathbb{Z}$，同理可证 $\overline{\mathbb{N}}=\mathbb{N}$. 最后，由于 $\mathbb{Q}$ 在 $\mathbb{R}$ 中是稠密的，故在任意区间 $(x-\varepsilon,x+\varepsilon)$ 中都存在有理数，故 $\overline{\mathbb{Q}}=\mathbb{R}$.

序列的附着点有这样一条性质：每个附着点都是某个子序列的极限。在集合的附着点中也有这样的性质。

**定理 9.1.6**

设 $X\subset \mathbb{R},x \in \mathbb{R}$，则 $x$ 是 $X$ 的附着点当且仅当存在 $X$ 中元素的序列 $(a_{n})$ 使得 $\lim_{ n \to \infty }a_{n}=x$.

**证明**

设 $x$ 是 $X$ 的附着点，对非空集族

$$
\left\{  y \in X \mid d(x,y)< \dfrac{1}{n}  \right\},n\in \mathbb{N}\setminus \{ 0 \}
$$

应用选择公理，就得到了序列 $(a_{n})_{n=1}^{\infty}$，满足 $\lim_{ n \to \infty }a_{n}=x$.

反之，设 $\lim_{ n \to \infty }a_{n}=x$，则对任意 $\varepsilon>0$ 存在 $N$ 使得对任意 $n>N$ 有 $d(x,a_{n})<\varepsilon$，从而存在 $a_{n}\in X$ 使得 $d(x,a_{n})<\varepsilon$，因此 $x$ 是 $X$ 的附着点。

上述定理对于无限附着点也成立，只需把性质换成 $y>n$ 或 $y<-n$ 即可。

接下来，我们给出另一个定义。

**定义 9.1.7** 闭集（closed set）

设 $X\subset \mathbb{R}$，称 $X$ 是**闭的**，如果 $\overline{X}=X$.

根据 9.1.4，显然 $\overline{X}$ 是闭的。利用 9.1.6，我们也可以说：$X$ 是闭的当且仅当 $X$ 中元素的收敛序列其极限仍然在 $X$ 中，这其实就是我们从有理数构造出实数的方法：实数是作为有理数序列的极限来定义的。

在后续的理论中，我们需要用到一个与附着点不同但紧密联系的概念：极限点，特别是在极限与微分学中，它要求 $d(x,y)>0$，即 $x\neq y$.

**定义 9.1.8** 极限点（limit point），孤立点（isolated point）

设 $X\subset \mathbb{R},x \in \mathbb{R}$，称 $x$ 是 $X$ 的**极限点**，如果 $x$ 是 $X\setminus \{ x \}$ 的附着点。$X$ 中不是 $X$ 的极限点的元素称为 $X$ 的**孤立点**。

用序列极限的语言来说，$x$ 是 $X$ 的极限点当且仅当存在 $X$ 中不同于 $x$ 的元素的序列 $(a_{n})$ 使得 $\lim_{ n \to \infty }a_{n}=x$. 注意，如果 $x \not\in X$ 并且 $x$ 是 $X$ 的附着点，那么 $x$ 一定是 $X$ 的极限点。

**定理 9.1.9**

设 $a<b$，则区间 $(a,b),(a,b],[a,b),[a,b]$ 以及 $(a,+\infty),[a,+\infty),(-\infty,b),(-\infty,b]$ 的所有元素都是它自身的极限点。

**证明**

以 $[a,b]$ 为例，设 $x \in [a,b]$，当 $x\neq b$ 时，考虑序列 $\left( x+\dfrac{1}{n} \right)_{n=N}^{\infty}$，该序列收敛于 $x$，并且当 $N$ 足够大时，序列中的项全部都落在 $[a,b]$ 中。当 $x=b$ 时，只需把序列换成 $\left( x-\dfrac{1}{n} \right)_{n=N}^{\infty}$. 其它区间同理可证。

最后，我们定义有界集合的概念。

**定义 9.1.10** 有界的（bounded）

设 $X\subset \mathbb{R}$，称 $X$ 是**有界的**，如果存在实数 $M>0$ 使得 $X\subset[-M,M]$.

实数集上关于闭且有界的集合有一个重要且基本的性质如下：

**定理 9.1.11** Heine-Borel 定理

设 $X\subset \mathbb{R}$，则以下命题等价：

1. $X$ 是闭且有界的
2. 任意 $X$ 中元素的序列都存在它的一个子序列收敛于 $L\in X$
3. $X$ 的任意开覆盖都包含一个有限覆盖

**证明**

首先我们证明 1 和 2 的等价性。设 $X$ 是闭且有界的，取 $X$ 中元素的序列 $(a_{n})$，则 $(a_{n})$ 是有界序列，由 Bolzano-Weierstrass 定理，$(a_{n})$ 有一个收敛的子序列，又因为 $X$ 是闭集，故其极限 $L \in X$.

现在设 2 成立。任取 $X$ 中的收敛序列，并把子序列取为它本身，则该序列的极限（也是 $X$ 的附着点）$L \in X$，故 $X$ 是闭集。假设 $X$ 是无界的，那么可以对非空集族

$$
\{ x \in X \mid |x|>n \},n \in \mathbb{N}
$$

应用选择公理，取出序列 $(a_{n})_{n=0}^{\infty}$，它的任意子序列都不收敛，这与 2 矛盾。因此 $X$ 是闭且有界的。

下面证明 1 和 3 等价。设 $X$ 的开覆盖 $\mathcal{O}$ 包含一个有限覆盖 $\{ O_{1},\dots,O_{n} \}$，我们可以把 $\mathcal{O}$ 中的开区间都取为有界开区间，从而 $X\subset \bigcup_{i=1}^{n}O_{i}$ 也是有界的。现假设 $X$ 不是闭集，也就是说存在 $X$ 中元素的收敛序列 $(a_{n})$ 其极限 $L\not\in X$，我们构造如下的开覆盖：

$$
\left\{  O_{x}=(x-\varepsilon,x+\varepsilon) \mid x \in X,\varepsilon=\dfrac{1}{2}d(x,L)  \right\}
$$

从中可以取出有限覆盖 $\{ O_{x_{1}},\dots,O_{x_{n}} \}$，令 $\varepsilon_{0}=\dfrac{1}{2}\min_{1\leq i\leq n} d(x_{i},L)$，则存在 $n$ 使得 $d(a_{n},L)<\varepsilon_{0}$，但该 $a_{n}$ 不属于 $\bigcup_{i=1}^{n}O_{x_{i}}$，矛盾。因此 $X$ 是闭且有界的。

最后，设 $X$ 是闭且有界的，假设 $X$ 没有有限覆盖，我们取一个有界闭区间 $I_{0}$ 使得 $X\subset I_{0}$，将 $I_{0}$ 平分为两个闭区间 $A_{1},B_{1}$，则 $A_{1}\cap X$ 与 $B_{1}\cap X$ 中必有一个不能被有限覆盖，不妨设为 $A_{1}\cap X$，则令 $I_{1}=A_{1}$. 下面，将 $I_{1}$ 平分，利用同样的方法得到闭区间 $I_{2}$，以此类推，就有

$$
I_{0}\cap X\supset I_{1}\cap X\supset I_{2}\cap X\supset \cdots
$$

满足 $I_{n}\cap X$ 不能被有限覆盖。利用选择公理从每个集合中取出一个元素组成序列 $(a_{n})_{n=0}^{\infty}$，由于 $X$ 是闭且有界的，故存在一个子序列使其收敛于 $X$ 中的元素 $x$. 由于 $I_{n}$ 与 $X$ 都是闭的，故 $I_{n}\cap X$ 也是闭的（根据 9.1.3），又因为 $(a_{n})_{n=n_{0}}^{\infty}$ 可以看成 $I_{n_{0}}\cap X$ 上的序列，故 $x \in I_{n_{0}}\cap X$，从而 $x \in \bigcap_{n=0}^{\infty}(I_{n}\cap X)$.

由于 $x \in X$，故存在 $O_{k}\in \mathcal{O}$ 使得 $x \in O_{k}$，因为 $I_{n}$ 的长度趋于 $0$，故对于足够大的 $n$，我们有 $I_{n}\subset(x-\varepsilon,x+\varepsilon)\subset O_{k}$，这与 $I_{n}\cap X$ 不能被有限覆盖矛盾。

上述定理实际上说明了：实数集上闭且有界的集合是紧致集，这个定理更一般的形式将在后面给出。

# Section 2: 函数极限

前面我们定义了一个序列收敛的概念，现在，我们来定义函数在某一点处收敛于某个值是什么意思。

**定义 9.2.1** 函数极限（functional limit）

设 $X\subset \mathbb{R}$，函数 $f\colon X\to \mathbb{R}$，$E\subset X$，$x_{0}\in \mathbb{R}$ 是 $E$ 的一个极限点，且 $L\in \mathbb{R}$，称 $f$ 在 $x_{0}$ 处**沿着** $E$ **收敛于** $L$，如果对任意 $\varepsilon>0$，存在 $\delta>0$ 使得对任意满足 $0<d(x,x_{0})<\delta$ 的 $x \in E$ 有 $d(f(x),L)<\varepsilon$，记作

$$
\lim_{ x \to x_{0}; x \in E } f(x)=L
$$

如果 $f$ 在 $x_{0}$ 处不收敛于任何数，则称 $f$ 在 $x_{0}$ 处**发散**。

上述定义被称为“函数极限的 $\varepsilon-\delta$ 定义”，对于上面的定义，注意以下几点：

1. $f(x_{0})$ 的值（无论是否存在）与 $\lim_{ x \to x_{0};x \in E }f(x)$ 是无关的，换言之，极限只与 $x_{0}$ 以外的函数值有关。
2. 极限值只与 $x_{0}$ 周围局部区域的函数值有关：取一个足够小的 $\delta$ 即可。
3. $x_{0}$ 是极限点是必要的，这是为了保证 $\{ x \in E \mid 0<d(x,x_{0})<\delta \}$ 不是空集。

当 $E=X$ 时，我们通常省略 $x \in E$，而直接写成 $\lim_{ x \to x_{0} }f(x)=L$.

我们可以利用已有的序列极限来改写上述定义。

**定理 9.2.2** Heine 定理

设 $X\subset \mathbb{R}$，函数 $f\colon X\to \mathbb{R}$，$E\subset X$，$x_{0}\in \mathbb{R}$ 是 $E$ 的一个极限点，且 $L\in \mathbb{R}$，则以下命题是等价的：

1. $\lim_{ x \to x_{0};x \in E }f(x)=L$
2. 对任意 $E$ 中不同于 $x_{0}$ 的元素构成并且收敛于 $x_{0}$ 的序列 $(a_{n})$，序列 $(f(a_{n}))$ 收敛于 $L$

**证明**

先设 $1$ 成立。则对任意 $\varepsilon>0$，存在 $\delta>0$ 使得对任意 $0<d(x,x_{0})<\delta$ 有 $d(f(x),L)<\varepsilon$. 由于 $\lim_{ n \to \infty }a_{n}=x_{0}$，故存在 $N$ 使得对任意 $n>N$ 有 $0<d(a_{n},x_{0})<\delta$，从而有 $d(f(a_{n}),L)<\varepsilon$，因此 $\lim_{ n \to \infty }f(a_{n})=L$.

现设 $1$ 不成立，我们需要找到收敛于 $x_{0}$ 的序列 $(a_{n})$ 使得 $(f(a_{n}))$ 不收敛于 $L$. 我们有

$$
\exists \varepsilon_{0}>0 \forall \delta>0 \exists x \in E(0<d(x,x_{0})<\delta \text{且} d(f(x),L)\geq\varepsilon_{0})
$$

取 $\delta_{1}=1$，将满足条件的 $x$ 的其中一个取为 $a_{1}$，再取 $\delta_{2}=\dfrac{1}{2}$，按同样的方法取出 $a_{2}$，以此类推，得到序列 $(a_{n})_{n=1}^{\infty}$ 满足

$$
0<d(a_{n},x_{0})<\dfrac{1}{n} \text{且} d(f(a_{n}),L)\geq \varepsilon_{0}
$$

从而 $\lim_{ n \to \infty }a_{n}=x_{0}$ 但 $\lim_{ n \to \infty }f(a_{n})\neq L$，这就完成了证明。

利用 Heine 定理，我们可以将函数极限的问题转化为序列极限，从而序列极限的性质也可以继承到函数极限上，如下定理所示。

**定理 9.2.3**

设 $E\subset X\subset \mathbb{R}$，函数 $f\colon X\to \mathbb{R}$，$x_{0}\in \mathbb{R}$ 是 $E$ 的一个极限点，如果 $f$ 在 $x_{0}$ 处沿着 $E$ 有极限，则极限值是唯一的。

**证明**

假设 $f$ 在 $x_{0}$ 处沿着 $E$ 收敛于 $L$ 与 $L'$，则有 $E\setminus \{ x_{0} \}$ 中元素构成且收敛于 $x_{0}$ 的序列 $(a_{n})$ 使得序列 $(f(a_{n}))$ 收敛于 $L$ 与 $L'$，由序列极限的唯一性，我们有 $L=L'$，这就完成了证明。

同样，根据定理 4.1.9，我们可以得到以下定理：

**定理 9.2.4**

设 $E\subset X\subset \mathbb{R}$，$x_{0}\in \mathbb{R}$ 是 $E$ 的极限点，函数 $f\colon X\to \mathbb{R},g\colon X\to \mathbb{R}$，且 $f$ 和 $g$ 在 $x_{0}$ 处沿着 $E$ 收敛于 $L$ 和 $M$，则有：

1. $\lim_{ x \to x_{0};x \in E }(f(x)+g(x))=L+M$
2. $\lim_{ x \to x_{0}; x \in E } f(x)g(x)=LM$
3. 如果对任意 $x \in E\setminus \{ x_{0} \}$ 有 $g(x)\neq 0$ 且 $M\neq 0$，则 $\lim_{ x \to x_{0}; x \in E }g(x)^{-1}=M^{-1}$

**证明**

取 $E\setminus \{ x_{0} \}$ 中的序列 $(a_{n})$ 满足 $\lim_{ n \to \infty }a_{n}=x_{0}$，则 $\lim_{ n \to \infty }f(a_{n})=L$，$\lim_{ n \to \infty }g(a_{n})=M$，由序列极限的代数性质即得上述定理。

下面我们考虑函数极限的比较准则，同样，它也是 Heine 定理与序列极限的比较准则的一个推论。

**定理 9.2.5** 比较准则

设 $E\subset X\subset \mathbb{R}$，$x_{0}\in \mathbb{R}$ 是 $E$ 的极限点，函数 $f\colon X\to \mathbb{R},g\colon X\to \mathbb{R}$，且 $f$ 和 $g$ 在 $x_{0}$ 处沿着 $E$ 收敛于 $L$ 和 $M$，如果对任意 $x \in E\setminus \{ x_{0} \}$ 有 $f(x)\leq g(x)$，则 $L\leq M$.

**证明**

取 $E\setminus \{ x_{0} \}$ 中的序列 $(a_{n})$ 满足 $\lim_{ n \to \infty }a_{n}=x_{0}$，则 $\lim_{ n \to \infty }f(a_{n})=L$，$\lim_{ n \to \infty }g(a_{n})=M$，由于 $f(a_{n})\leq g(a_{n})$，故 $L\leq M$.

下面的定理，尽管有它在序列极限中的对应，反而是直接从定义 9.2.1 中推出的。

**定理 9.2.6** 挤压定理（squeeze theorem）

设 $E\subset X\subset \mathbb{R}$，$x_{0}\in \mathbb{R}$ 是 $E$ 的极限点，$f,g,h$ 都是 $X$ 到 $\mathbb{R}$ 的函数，$\lim_{ x \to x_{0};x \in E }f(x)=\lim_{ x \to x_{0};x \in E }h(x)=L$，且对任意 $x \in E\setminus \{ x_{0} \}$ 有 $f(x)\leq g(x)\leq h(x)$，则 $\lim_{ x \to x_{0};x \in E }g(x)=L$.

**证明**

根据定义与已知条件，我们知道对任意 $\varepsilon>0$，存在 $\delta>0$ 使得对任意 $0<d(x,x_{0})<\delta$ 的 $x \in E$ 有

$$
L-\varepsilon<f(x)\leq g(x)\leq h(x)<L+\varepsilon
$$

即 $d(g(x),L)<\varepsilon$，这就完成了证明。

到目前为止，我们讨论了 $f$ 在有限极限点处的极限，现在我们简要地讨论一下在无穷处的极限，以及极限为无穷的情况。

**定义 9.2.7** 在无穷处的极限

设 $E\subset X\subset \mathbb{R}$，函数 $f\colon X\to \mathbb{R}$，$+\infty$ 是 $E$ 的极限点，$L\in \mathbb{R}$，称 $x\to +\infty$ 时 $f$ **沿着** $E$ **收敛于** $L$，如果对任意 $\varepsilon>0$，存在 $M>0$ 使得对任意满足 $x>M$ 的 $x \in E$ 有 $d(f(x),L)<\varepsilon$，记作

$$
\lim_{ x \to +\infty;x \in E } f(x)=L
$$

如果 $x\to +\infty$ 时 $f$ 不收敛于任何值，则称 $x\to +\infty$ 时 $f$ **发散**。

$x\to -\infty$ 的情况同理。

上述定义与序列极限的定义是一致的：把 $a_{n}$ 写成 $f(n)$，其中 $f\colon \mathbb{R}\to \mathbb{R}$，则

$$
\lim_{ n \to \infty } f(n)=\lim_{ n \to +\infty; n \in \mathbb{N} } f(n)
$$

下面我们定义极限值为无穷的情况，例如，显然函数 $x\mapsto \dfrac{1}{x^{2}}$ 在 $x\to 0$ 时发散至 $+\infty$.

**定义 9.2.8** 无穷极限

设 $E\subset X\subset \mathbb{R}$，函数 $f\colon X\to \mathbb{R}$，$x_{0}\in \mathbb{R}$ 是 $E$ 的极限点，称 $f$ 在 $x_{0}$ 处**沿着** $E$ **发散至** $+\infty$，如果对任意 $K>0$，存在 $\delta>0$ 使得对任意满足 $0<d(x,x_{0})<\delta$ 的 $x \in E$ 有 $f(x)>K$，记作

$$
\lim_{ x \to x_{0};x \in E } f(x)=+\infty
$$

发散至 $-\infty$ 的情况同理。

9.2.8 给出了有限极限点、无穷极限的情况，如果是无穷极限点、无穷极限，只需把 9.2.7 与 9.2.8 结合起来。尽管上面这四种情况（还有一个有限极限点、有限极限）看上去形式不同，但我们后面会看到，如果我们考虑 $\mathbb{R}^{*}$ 的拓扑结构，那么这些定义可以被很好地统一起来（a.k.a. 邻域形式）。

我们可以拿这些无穷极限做很多事情，例如，大部分极限定律仍然成立，然而比起有限情况，我们不常用到无穷的情况，因此关于无穷极限的性质我们留给读者进行推导。

# Section 3: 连续函数

现在我们给出函数论中最基本的概念之一：连续性。

**定义 9.3.1** 连续（continuous）

设 $X\subset \mathbb{R}$，函数 $f\colon X\to \mathbb{R}$，$x_{0}\in X$，称 $f$ 在 $x_{0}$ 处**连续**，如果

$$
\lim_{ x \to x_{0};x \in X } f(x)=f(x_{0})
$$

如果对任意 $x \in X$ 都有 $f$ 在 $x$ 处连续，则称 $f$ 在 $X$ 上连续。

将上述定义与 Heine 定理结合起来，我们就得到了以下的关于连续性的等价表述：

**定理 9.3.2**

设 $X\subset \mathbb{R}$，函数 $f\colon X\to \mathbb{R}$，$x_{0}\in X$，则以下命题等价：

1. $f$ 在 $x_{0}$ 处连续
2. 对任意 $X$ 中元素构成且收敛于 $x_{0}$ 的序列 $(a_{n})$，序列 $(f(a_{n}))$ 收敛于 $f(x_{0})$

上述定理可以简单地理解为：如果 $f$ 连续，则

$$
\lim_{ n \to \infty } f(a_{n})=f(\lim_{ n \to \infty } a_{n})
$$

或者 $f$ 把收敛序列 $(a_{n})$ 映射到收敛序列 $(f(a_{n}))$，极限 $x_{0}$ 到极限 $f(x_{0})$.

同理，将定义 9.3.1 与定律 9.2.4 结合，我们就有连续的代数性质：

**定理 9.3.3**

设 $X\subset \mathbb{R}$，函数 $f\colon X\to \mathbb{R},g\colon X\to \mathbb{R}$，$x_{0}\in X$，$f,g$ 都在 $x_{0}$ 处连续，则：

1. $f+g$ 在 $x_{0}$ 处连续
2. $f\cdot g$ 在 $x_{0}$ 处连续
3. 如果对任意 $x \in X$ 有 $g(x)\neq 0$，则 $g^{-1}$ 在 $x_{0}$ 处连续

利用上述定理，以及常数函数 $x\mapsto c$ 和恒等函数 $x\mapsto x$ 是连续的事实（可以利用 9.3.2 证明），我们就可以证明多项式

$$
p(x)=a_{0}+a_{1}x+\dots+a_{n}x^{n},a_{n}\neq 0
$$

以及有理函数

$$
q(x)= \dfrac{a_{0}+a_{1}x+\dots+a_{n}x^{n}}{b_{0}+b_{1}x+\dots+b_{m}x^{m}},a_{n},b_{m}\neq 0
$$

在其定义域上都是连续的。

下面我们给出连续性的其它例子。

**命题 9.3.4**

设实数 $a>0$，则定义在 $\mathbb{R}$ 上的指数函数 $x\mapsto a^{x}$ 在 $\mathbb{R}$ 上连续。

**证明**

当 $a=1$ 时是常值函数，显然连续。现设 $a>1$，$a<1$ 的情况是类似的。设 $x_{0}\in \mathbb{R}$，当 $x_{0}<x<x_{0}+\delta$ 时有

$$
|a^{x}-a^{x_{0}}|=a^{x_{0}}(a^{x-x_{0}}-1)<a^{x_{0}}(a^{\delta}-1)
$$

令 $0<\delta<1$，则存在 $n \in \mathbb{N}$ 使得 $\delta<\dfrac{1}{n}$，从而 $a^{\delta}-1<a^{1/n}-1$，由于 $\lim_{ n \to \infty }a^{1/n}=1$，故对任意 $\varepsilon>0$，存在 $N$ 使得 $a^{1/N}-1<\varepsilon$，于是可以取 $0<\delta<\dfrac{1}{N}$，则有

$$
|a^{x}-a^{x_{0}}|<a^{x_{0}}(a^{1/N}-1)<a^{x_{0}}\varepsilon
$$

这就完成了证明的一半。另一边，设 $x_{0}-\delta<x<x_{0}$，则

$$
|a^{x}-a^{x_{0}}|=a^{x_{0}}(1-a^{x-x_{0}})<a^{x_{0}}(1-a^{-\delta})
$$

根据 $\lim_{ n \to \infty }a^{-1/n}=1$ 同样得到 $|a^{x}-a^{x_{0}}|<a^{x_{0}}\varepsilon$，这就完成了证明。

**命题 9.3.5**

设 $p \in \mathbb{R}$，则定义在 $(0,+\infty)$ 上的函数 $x\mapsto x^{p}$ 在定义域上连续。

**证明**

当 $p=0$ 时是常值函数，显然连续。现设 $p\neq 0$. 设 $x_{0}>0$，我们要证 $\lim_{ x \to x_{0} }x^{p}=x_{0}^{p}$，这等价于

$$
\lim_{ x \to x_{0} } \left( \dfrac{x}{x_{0}} \right)^{p}=\lim_{ t \to 1 } t^{p}=1
$$

事实上，根据极限的代数性质以及 $\lim_{ t \to 1 }t=1$，我们有 $\lim_{ t \to 1 }t^{n}=1$ 对任意整数 $n$ 成立。根据整数的分布性质，对于 $p$，存在唯一的整数 $n$ 使得 $n\leq p<n+1$，于是

$$
t^{n}\leq t^{p}<t^{n+1},t>1; t^{n+1}<t^{p}\leq t^{n},0<t<1
$$

根据挤压定理，就有 $\lim_{ t \to 1 }t^{p}=1$，这就完成了证明。

最后，我们来考虑复合函数 $g\circ f\colon x\mapsto g(f(x))$ 的连续性，下面的定理指出，连续性对于复合运算也是封闭的。

**定理 9.3.6**

设 $X\subset \mathbb{R},Y\subset \mathbb{R}$，函数 $f\colon X\to Y,g\colon Y\to \mathbb{R}$，$x_{0}\in X$，且 $f$ 在 $x_{0}$ 处连续，$g$ 在 $f(x_{0})$ 处连续，则 $g\circ f$ 在 $x_{0}$ 处连续。

**证明**

我们使用 $\varepsilon-\delta$ 定义证明。根据条件我们知道，对任意 $\varepsilon>0$，存在 $\delta>0$ 使得对任意满足 $d(y,f(x_{0}))<\delta$ 的 $y \in Y$ 有 $d(g(y),g\circ f(x_{0}))<\varepsilon$.

对于这个 $\delta$，存在 $\eta>0$ 使得对任意满足 $d(x,x_{0})<\eta$ 的 $x \in X$ 有 $d(f(x),f(x_{0}))<\delta$，从而有 $d(g\circ f(x),g\circ f(x_{0}))<\varepsilon$，这就完成了证明。

利用上述定理，我们可以证明更加复杂的函数也是连续的，如 $2^{x^{2}+3x+2},\dfrac{|x^{3}-x+1|^{\sqrt{ 2 }}}{x^{2}+1}$ 等，其中绝对值函数 $x\mapsto |x|$ 的连续性可以分段考虑。然而，还有一些函数不太容易证明其连续性，比如函数 $x\mapsto x^{x}$，不过，当我们定义了**对数**后，这个函数就比较容易处理了。关于对数、三角函数、反三角函数等超越函数，我们需要**幂级数**才能对它们进行严格的处理，这就是以后的事了。

最后，让我们来简要考察一下不连续点（通常称为**间断点**或**奇点**）的情况，我们需要以下的定义：

**定义 9.3.7** 左极限（left limit），右极限（right limit）

设 $X\subset \mathbb{R}$，函数 $f\colon X\to \mathbb{R}$，$x_{0}\in \mathbb{R}$，如果 $x_{0}$ 是 $X\cap(x_{0},+\infty)$ 的极限点，并且极限

$$
\lim_{ x \to x_{0}; x \in X\cap(x_{0},+\infty) } f(x)
$$

存在，则称其为 $f$ 在 $x_{0}$ 处的**右极限**，记作 $f(x_{0}+)$ 或 $\lim_{ x \to x_{0}+ } f(x)$.

同理可以定义 $f$ 在 $x_{0}$ 处的**左极限**，记作 $f(x_{0}-)$ 或 $\lim_{ x \to x_{0}- }f(x)$.

显然，如果 $f$ 在 $x_{0}$ 处沿着 $X$ 有极限，那么 $f$ 在 $x_{0}$ 处有左右极限，并且它们都等于 $\lim_{ x \to x_{0} }f(x)$. 下面的定理指出，反之也成立。

**定理 9.3.8**

设 $X\subset \mathbb{R}$，函数 $f\colon X\to \mathbb{R}$，$x_{0}\in X$，如果 $x_{0}$ 同时是 $X\cap(x_{0},+\infty)$ 和 $X\cap(-\infty,x_{0})$ 的极限点，并且 $f(x_{0}+),f(x_{0}-)$ 都存在且等于 $f(x_{0})$，那么 $f$ 在 $x_{0}$ 处连续。

**证明**

根据定义，对任意 $\varepsilon>0$，存在 $\delta^{+}>0$ 使得对任意 $x_{0}<x<x_{0}+\delta^{+}$ 的 $x \in X$ 有 $d(f(x),f(x_{0}))<\varepsilon$. 同理，存在 $\delta^{-}>0$ 使得对任意 $x_{0}-\delta^{-}<x<x_{0}$ 的 $x \in X$ 有 $d(f(x),f(x_{0}))<\varepsilon$.

令 $\delta=\min(\delta^{+},\delta^{-})$，则对任意 $d(x,x_{0})<\delta$ 的 $x \in X$ 有 $d(f(x),f(x_{0}))<\varepsilon$，这就完成了证明。

定理 9.3.8 给出了连续的一个充要条件，我们可以依据 9.3.8 来为间断点分类。

如果 $f(x_{0}+),f(x_{0}-)$ 都存在但不相等，这就是一个**跳跃间断点**，典型的例子如符号函数

$$
\mathrm{sgn}(x)=\begin{cases}
1 &, x>0 \\
0 &, x=0 \\
-1 &, x<0
\end{cases}
$$

在 $x=0$ 处的表现。

如果 $f(x_{0}+),f(x_{0}-)$ 都存在且相等，但是不等于 $f(x_{0})$（或者 $f$ 在 $x_{0}$ 无定义），这就是一个**可去间断点**，例如定义在 $\mathbb{R}\setminus\{ 0 \}$ 上的函数 $\dfrac{x^{2}}{x}$，它在 $x=0$ 处有一个可去间断点。可去间断点可以通过重定义的方式进行修补，假设 $f$ 在 $x_{0}$ 处有一个可去间断点，那么我们可以定义

$$
F(x)=\begin{cases}
f(x) &, x\neq x_{0} \\
f(x_{0}+) &, x=x_{0}
\end{cases}
$$

这样定义的 $F$ 在 $x_{0}$ 处就是连续的，这种技巧在之后会用到。

除了跳跃间断点和可去间断点，还有其它类型的间断点，它们都有一个特征：有一侧或者两侧的极限不存在。例如函数 $x\mapsto \dfrac{1}{x}$ 在 $x\to 0+$ 时发散至 $+\infty$，这种间断点通常被称为**无穷间断点**或者**渐近间断点**。另一种常见间断点是**震荡间断点**，它的一大特征是单侧极限不收敛，也不发散至 $\pm \infty$，比如 Dirichlet 函数

$$
D(x)=\begin{cases}
1 &, x \in \mathbb{Q} \\
0 &, x \not\in \mathbb{Q}
\end{cases}
$$

它的函数值在 $0$ 和 $1$ 之间不断震荡，因此它在任何一点的左右极限都不存在，尽管该函数是有界的。

对奇点的研究是复分析中的重要内容，但我们目前不会花太多精力在这上面。