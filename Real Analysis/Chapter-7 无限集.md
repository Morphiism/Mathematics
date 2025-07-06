本章我们回过头来研究一下集合论，特别地，我们要对无限集做深入的研究。在这之后，我们将引入在无限集上求和的概念。

# Section 1: 有限基数

在正式进入超穷世界之前，我们先来考虑有限集的性质。根据定义，一个集合是有限的如果存在双射 $f\colon n \to X$，因此，要研究有限集，我们首先要研究自然数（作为集合）的性质。

首先我们给出区分有限与无限的一个判断方法。

**定理 7.1.1** 鸽巢原理（pigeonhole principle）

不存在自然数 $n \in \mathbb{N}$ 到其真子集的双射。

**证明**

我们使用归纳法。当 $n=0$ 时，$\varnothing$ 没有真子集，从而也没有双射。

假设不存在 $n$ 到 $n$ 的真子集的双射。现假设 $n+1=n \cup \{ n \}$ 与其真子集 $X$ 之间存在双射 $f\colon n+1\to X$，我们分两种情况考虑：$n \in X$ 与 $n \not\in X$.

如果 $n \not\in X$，则 $f$ 是 $n$ 到 $X\setminus \{ f(n) \}$ 的双射，与归纳假设矛盾。

如果 $n \in X$，设 $n=f(k)$，定义函数 $g\colon n\to X\setminus \{ n \}$ 如下：

$$
g(i)=\begin{cases}
f(i) &, i\neq k \\
f(n) &, i=k
\end{cases}
$$

从而 $g$ 是 $n$ 到 $X\setminus \{ n \}$ 的双射，与归纳假设矛盾。这就完成了证明。

从上述定理我们得到推论：

**定理 7.1.2**

不存在有限集到其真子集的双射。

现在我们就可以证明自然数 $\mathbb{N}$ 是一个无限集，因为存在 $\mathbb{N}$ 到其真子集 $\mathbb{N}\setminus \{ 0 \}$ 的双射 $f(n)=n+1$. 进而我们知道，所有可数集都是无限集。

下面我们给出有限集的一些基本性质，它们都可以使用归纳法来证明。

**定理 7.1.3**

设 $X,Y$ 是有限集，则 $X$ 的子集，$X\cup Y$，$\mathscr{P}(X)$，$F[X]$ 都是有限集，其中 $F$ 是以 $X$ 为定义域的函数。

对于有限集来说，集合的**基数**或**势** $|X|$ 除了表明它与自然数 $n$ 之间存在双射外，也等于集合内元素的个数，这是**计数组合学**的基础。对于我们来说，其中最重要的性质如下：

**定理 7.1.4**

设 $X,Y$ 是有限集，则：

1. $|X|\leq|Y|$ 当且仅当存在单射 $f\colon X\to Y$
2. $|X|\geq|Y|>0$ 当且仅当存在满射 $g\colon X\to Y$

**证明**

当 $X=\varnothing$ 时，$f\colon X\to Y$ 是空映射 $\varnothing$，它是一个单射（不存在使其不满足定义的元素）。

设 $X\neq \varnothing$，我们可以写 $X=\{ a_{0},\dots,a_{n} \},Y=\{ b_{0},\dots,b_{m} \}$，当 $|X|\leq |Y|$，即 $n\leq m$ 时，可以构造单射 $f(a_{i})=b_{i}$. 反之，设 $f\colon X\to Y$ 是单射，由于 $f[X]\subset Y$，则 $|X|=|f[X]|\leq|Y|$.

对于 2，我们可以用单射 $f\colon Y\to X$ 构造满射 $g\colon X\to Y$. $Y$ 非空，故存在 $y_{0}\in Y$，我们构造函数 $g\colon X\to Y$ 如下：

$$
g(x)=\begin{cases}
y &, x \in f[Y],f(y)=x \\
y_{0} &, x \not\in f[Y]
\end{cases}
$$

$f$ 的单性保证了上述定义是良定的，并且 $g$ 是一个满射，这就完成了证明。

现在我们总结一下有限基数的性质：

1. 自反性：$|X|\leq|X|$
2. 反对称性：$|X|\leq|Y|,|Y|\leq|X|\implies|X|=|Y|$
3. 传递性：$|X|\leq|Y|,|Y|\leq|Z|\implies|X|\leq|Z|$
4. 完全性：$|X|\leq|Y|$ 与 $|Y|\leq|X|$ 至少有一个成立

下面，我们要将上述性质推广到无限集。

# Section 2: 实无限

**定义 7.2.1** 等势（equipotent）

称集合 $X,Y$ **等势**，如果存在双射 $f\colon X\to Y$，记作 $X\approx Y$ 或者 $|X|=|Y|$.

显然，等势满足自反性、对称性以及传递性，这来源于双射的相应性质。

在无限集上，没有像自然数那样的序关系，然而，定理 7.1.4 给了我们启发，让我们能够脱离数的概念，纯粹使用函数来表达基数的大小关系。

**定义 7.2.2** 基数的序

设 $X,Y$ 是集合，定义 $X\preceq Y$ 或 $|X|\leq|Y|$，如果存在单射 $f\colon X\to Y$.

我们可以证明，如果 $X\preceq Y,X\neq \varnothing$，那么存在满射 $g\colon Y\to X$，其构造方式与 7.1.4 证明中的方法是一样的。

目前我们只见过两种集合：与某个自然数 $n$ 等势的集合，称为有限集，以及与自然数集 $\mathbb{N}$ 等势的集合，称为可数集，它们合称为**至多可数集**。是否有其它类型的无限集？下面的定理给出了答案。

**定理 7.2.3** Cantor 定理

对任意集合 $X$ 有 $X\prec \mathscr{P}(X)$.

**证明**

显然存在 $X\to\mathscr{P}(X)$ 的单射 $f(x)=\{ x \}$，我们要证不存在 $X$ 到 $\mathscr{P}(X)$ 的满射（从而不存在双射）。反设存在满射 $f\colon X\to\mathscr{P}(X)$，构造 $X$ 的子集

$$
Y=\{ x \in X \mid x \not\in f(x) \}
$$

则存在 $x_{0}\in X$ 使得 $f(x_{0})=Y$，现在考虑 $x_{0}$ 是否属于 $f(x_{0})$.

如果 $x_{0}\in f(x_{0})$，则 $x_{0} \not\in f(x_{0})$；如果 $x_{0}\not\in f(x_{0})$，则 $x_{0} \in f(x_{0})$，矛盾。

注意上述证明中的集合 $Y$ 类似于 Russell 悖论中的集合 $S=\{ x \mid x \not\in x \}$，它们都利用了“自指”的悖论性质。

Cantor 定理指出：存在各种不同类型的实无限，事实上，有无穷多种：

$$
\mathbb{N}\prec \mathscr{P}(\mathbb{N})\prec \mathscr{P}(\mathscr{P}(\mathbb{N}))\prec \mathscr{P}(\mathscr{P}(\mathscr{P}(\mathbb{N})))\prec \cdots
$$

接下来，我们给出一个方便的判断两个集合是否等势的方法，实际上就是有限基数的反对称性在无限集上的推广：$X\preceq Y,Y\preceq X\implies X\approx Y$. 首先我们证明一个引理：

**引理 7.2.4**

设集合 $A,B,C$ 满足 $A \supset B \supset C,A\approx C$，则 $A\approx B\approx C$.

**证明**

设 $f\colon A\to C$ 是双射，我们递归地构造以下集合：

$$
\begin{cases}
A_{0}=A\setminus B \\
A_{n+1}=f[A_{n}]
\end{cases}
$$

构造函数 $g\colon A\to B$ 如下：

$$
g(x)=\begin{cases}
f(x) &, x \in \bigcup_{n \in \mathbb{N}} A_{n} \\
x &, x \in A \setminus \bigcup_{n \in \mathbb{N}} A_{n}
\end{cases}
$$

下证 $g$ 是双射。由于 $f$ 是单射，故我们只需验证当 $x_{1} \in A_{k}$ 且 $x_{2}\in A\setminus \bigcup_{n \in \mathbb{N}} A_{n}$ 时有 $g(x_{1})\neq g(x_{2})$. 事实上，我们有 $g(x_{1})=f(x_{1}) \in A_{k+1}$，而 $g(x_{2})=x_{2} \in A\setminus \bigcup_{n \in \mathbb{N}} A_{n}$，从而 $g$ 是单射。

设 $y \in B$，则 $y \in A_{k}(k\geq 1)$ 或 $y \in A\setminus \bigcup_{n \in \mathbb{N}} A_{n}$，无论哪种情况，都存在 $x \in A$ 使得 $g(x)=y$，因为 $f$ 以及 $x\mapsto x$ 都是满射。因此，$g$ 是一个双射，根据等势的传递性得 $A\approx B\approx C$.

> 上述定理的证明可以按下面的例子理解：假设有一旅店，其中有可数个房间，编号为 $0,1,2,\dots$，并且该店已经客满。现在，如果又来了 $10$ 个客人，那么店主就可以要求住在编号为 $0,1,\dots,9$ 房间的客人移动到 $10,11,\dots,19$，在这些房间的客人也相应的移动到后面的房间，这就是 $A=\mathbb{N}$ 到 $C=\mathbb{N}\setminus\{ 0,1,\dots,9 \}$ 的双射 $f(n)=n+10$.
> 
> 现在，假设只有 $5$ 个而非 $10$ 个客人来到旅店，但店主的调动策略 $f$ 不变，那么可以这样调动：住在编号 $0,1,\dots,4$ 房间的客人移动到 $10,11,\dots,14$，这些房间的客人也相应的向后移动，而对于住在 $5,6,\dots,9,15,16,\dots,19,\dots$ 房间的客人则保持不变，这就是 $A=\mathbb{N}$ 到 $B=\mathbb{N}\setminus\{ 0,1,\dots,4 \}$ 的双射 $g$.

**定理 7.2.5** Cantor-Bernstein 定理

设集合 $X,Y$ 满足 $X\preceq Y,Y\preceq X$，则 $X\approx Y$.

**证明**

取单射 $f\colon X\to Y$ 和 $g\colon Y\to X$，则我们有

$$
\begin{gather}
X\approx f[X],Y\approx g[Y],f[X]\approx g[f[X]] \\
X \supset g[Y] \supset g[f[X]]
\end{gather}
$$

根据引理 7.2.4，即得 $X\approx Y$.

我们之前证明了如果 $X\succeq Y\neq \varnothing$，那么存在满射 $g\colon X\to Y$，那么反过来呢？换句话说，能否用 $g$ 来构造单射 $f\colon Y\to X$？下面我们来证明这一点。

**定理 7.2.6**

若存在满射 $g\colon X\to Y,Y\neq \varnothing$，则 $Y\preceq X$.

**证明**

对任意 $y \in Y$，都存在 $x \in X$ 使得 $g(x)=y$，换句话说，原像集 $g^{-1}[\{ y \}]$ 是非空的。取 $x \in g^{-1}[\{ y \}]$，构造函数 $f\colon Y\to X$ 为 $f(y)=x$，下面我们证明 $f$ 是单射。

设 $y_{1}\neq y_{2}$，则 $g^{-1}[\{ y_{1} \}]\cap g^{-1}[\{ y_{2} \}]=\varnothing$，从而 $f(y_{1})\neq f(y_{2})$，即证。

事实上，上述定理的证明中隐含地用到了**选择公理**，上面的函数 $f$ 就是集合 $\{ g^{-1}[\{ y \}] \mid y \in Y \}$ 的选择函数。而且，基数的序的完全性（ $X\preceq Y$ 与 $Y\preceq X$ 至少有一个成立）是选择公理的等价形式之一。关于选择公理，我们将在后面做详细讨论。

下面我们来证明一些等势定理。

**定理 7.2.7**

对任意集合 $X$，有 $\mathscr{P}(X)\approx 2^{X}=\{ 0,1 \}^{X}$.

**证明**

我们可以直接构造双射。任取 $A \in\mathscr{P}(X)$，定义函数 $\chi_{A}\colon X\to 2$ 为

$$
\chi_{A}(x)=\begin{cases}
1 &, x \in A \\
0 &, x \not\in A
\end{cases}
$$

则函数 $F\colon \mathscr{P}(X)\to 2^{X},F(A)=\chi_{A}$ 是双射（ $\chi_{A}$ 称为 $A$ 的**特征函数**）。

上述定理解释了为什么 $\mathscr{P}(X)$ 称为 $X$ 的“幂集”。

**定理 7.2.8**

设 $X\subset \mathbb{N}$，则 $X$ 是至多可数的。

**证明**

若 $X$ 是有限集，则 $X$ 是至多可数的。设 $X$ 是无限集，我们要证 $X\approx \mathbb{N}$.

递归地定义 $\mathbb{N}\to X$ 的函数 $f$ 如下：

$$
\begin{cases}
f(0)=\min X \\
f(n+1)=\min X \setminus \{ f(i) \mid i\leq n \}
\end{cases}
$$

根据归纳法我们知道 $f$ 是严格递增的，从而 $f$ 是单射。现假设 $f$ 不是满射，则 $X\setminus f[\mathbb{N}]\neq \varnothing$，设 $k = \min X\setminus f[\mathbb{N}]$，则 $k\leq f(k)$，于是

$$
k= \min X\setminus \{ f(i) \mid i<k \}=f(k) \in f[\mathbb{N}]
$$

与假设矛盾，从而 $f$ 是一个双射。

于是我们得到推论：

**定理 7.2.9**

可数集的子集是至多可数的。

上述定理表明，可数集是“最小”的无限集。

**命题 7.2.10**

$\mathbb{N}^{2}\approx \mathbb{N}$

**证明**

第一，$\mathbb{N}\to \mathbb{N}^{2}$ 的映射 $f(n)=(n,0)$ 是单射。

第二，$\mathbb{N}^{2}\to \mathbb{N}$ 的映射 $f(m,n)=2^{m}3^{n}$ 是单射，即证。

利用归纳法，我们可以证明对任意 $n \in \mathbb{N}$，有 $\mathbb{N}^{n}\approx \mathbb{N}$，即有限个可数集的直积是可数的。

**命题 7.2.11**

$\mathbb{N}\approx \mathbb{Z}\approx \mathbb{Q}$

**证明**

第一，$\mathbb{N}\to \mathbb{Q}$ 的嵌入映射是单射。

第二，$\mathbb{Q}\to \mathbb{N}$ 的函数 $f\left( (-1)^{k}\dfrac{m}{n} \right)=2^{m}3^{n}5^{k}$ 是单射，其中 $k=0$ 或 $1$，$\dfrac{m}{n}\geq 0$ 是最简分数。再根据 $\mathbb{N}\subset \mathbb{Z}\subset \mathbb{Q}$ 可得 $\mathbb{N}\approx \mathbb{Z}\approx \mathbb{Q}$.

**命题 7.2.12**

$\mathbb{N}\prec 2^{\mathbb{N}}\approx \mathbb{R}$

**证明**

首先证明 $2^{\mathbb{N}}\preceq \mathbb{R}$. 设 $\chi\in 2^{\mathbb{N}}$，构造函数 $f$ 为

$$
f(\chi)=\sum_{i=0}^{\infty} \dfrac{\chi(i)}{10^{i+1}}=\overline{0.\chi(0)\chi(1)\dots \chi(n)\dots}_{10}
$$

$f(\chi)$ 是一个 Cauchy 序列，所以一定收敛，并且 $f$ 是一个单射。

下面证明 $\mathbb{R}\preceq 2^{\mathbb{N}}$. 我们先证 $(0,1)\approx \mathbb{R}$，取函数 $h(x)=\dfrac{1}{x}+\dfrac{1}{x-1}$ 即得 $(0,1)\to \mathbb{R}$ 的双射。$(0,1)$ 中的实数可以表示为二进制小数

$$
x=\overline{0.x_{0}x_{1}\dots x_{n}\dots}_{2}=\sum_{i=0}^{\infty} \dfrac{x_{i}}{2^{i+1}}
$$

其中 $x_{i}=0$ 或 $1$，如果存在 $m$ 使得 $x_{m}=1$ 且 $x_{m+k}=0$ 对一切 $k>0$ 成立，则把它改成 $x_{m}=0,x_{m+k}=1$.

令 $\chi(n)=x_{n}$，定义 $f(x)=\chi$，则有 $(0,1)\to 2^{\mathbb{N}}$ 的单射，这就完成了证明。

上述命题表明，实数集是一个不可数集，它是我们遇到的第一个不可数集。

**命题 7.2.13**

$\mathbb{R}^{2}\approx \mathbb{R}$

**证明**

首先我们有 $\mathbb{R}\to \mathbb{R}^{2}$ 的单射 $f(x)=(x,0)$，其次，我们只需构造 $(0,1)^{2}\to(0,1)$ 的单射。

给定 $(x,y) \in(0,1)^{2}$，我们写出其十进制小数表达式：

$$
x=\overline{0.x_{0}x_{1}\dots x_{n}\dots}_{10},y=\overline{0.y_{0}y_{1}\dots y_{n}\dots}_{10}
$$

同样，如果存在 $m \in \mathbb{N}$ 使得 $x_{m}=n\neq 0$ 且 $x_{m+k}=0$ 对一切 $k>0$ 成立，则把它改成 $x_{m}=n-1,x_{m+k}=9$. 构造 $(0,1)^{2}\to(0,1)$ 的函数如下：

$$
f(x,y)=\overline{0.x_{0}y_{0}x_{1}y_{1}\dots x_{n}y_{n}\dots}_{10}
$$

则 $f$ 是单射，这就完成了证明。

利用归纳法，我们可以证明 $\mathbb{R}^{n}\approx \mathbb{R}$. 上述命题表明，平面上的点和直线上的点“一样多”。

**命题 7.2.14**

对任意 $a,b \in \mathbb{R},a<b$，有 $(a,b)\approx [a,b]\approx \mathbb{R}$.

**证明**

我们可以构造 $(0,1)\to(a,b)$ 的双射 $h(x)=a+(b-a)x$，从而 $(a,b)\approx (0,1)\approx \mathbb{R}$，又 $(a,b)\subset [a,b]\subset \mathbb{R}$，即证。

现在我们要问，在 $\mathbb{N}$ 与 $\mathbb{R}\approx\mathscr{P}(\mathbb{N})$ 之间还有没有其它类型的无限，即，是否存在 $X$ 使得 $\mathbb{N}\prec X\prec \mathbb{R}$？这就是著名的**连续统假设**（continuum hypothesis，简称 CH）：$\mathbb{R}$ 的不可数子集与 $\mathbb{R}$ 等势。Godel 与 Cohen 证明了，在 ZFC 内，CH 不能被证明也不能被证伪，这也就是说，无论我们承认还是否定 CH，都能得到一个独立且自洽的公理系统。这类似于非欧几何，无论我们承认过一点能作多少条平行线，所得到的几何学系统都是自洽的。

最后，我们给出一些关于可数集的性质。

**定理 7.2.15**

1. 若 $X \preceq \mathbb{N}$ 且 $X$ 是无限集，则 $X$ 是可数集。
2. 若非空至多可数集 $A_{0},\dots,A_{n}$ 中至少有一个可数，则 $\displaystyle \prod_{i=0}^{n}A_{i}$ 是可数集。
3. 若至多可数集 $A_{0},\dots,A_{n}$ 中至少有一个可数，则 $\displaystyle \bigcup_{i=0}^{n}A_{i}$ 是可数集。
4. 若每个 $A_{n}$ 至多可数且 $\displaystyle \bigcup_{i=0}^{\infty}A_{i}$ 是无限集，则 $\displaystyle \bigcup_{i=0}^{\infty}A_{i}$ 是可数集。

**证明**

(1). 取单射 $f\colon X\to \mathbb{N}$，则 $f$ 是 $X$ 到 $f[X]\subset \mathbb{N}$ 的双射，由于 $\mathbb{N}$ 的无限子集是可数集，从而 $X\approx f[X]$ 是可数集。

(2). 先证明两个集合时的情况，使用归纳法可以推广至任意有限个。设 $A$ 是可数集，$B$ 是至多可数的，从而我们有 $A=\{ a_{0},a_{1},\dots \}$，$B=\{ b_{0},b_{1},\dots \}$ 或者 $B=\{ b_{0},b_{1},\dots,b_{n} \}$，则构造 $A\times B\to \mathbb{N}$ 的单射为

$$
f(a_{i},b_{j})=2^{i}3^{j}
$$

由于 $A\times B$ 是无限集，故 $A\times B$ 是可数集。

(3). 同样先证两个集合时的情况。设 $A$ 是可数集，$B$ 是至多可数的，则有 $A=\{ a_{0},a_{1},\dots \}$，$B=\{ b_{0},b_{1},\dots \}$ 或者 $B=\{ b_{0},b_{1},\dots,b_{n} \}$.

如果 $A\cap B=\varnothing$，则 $A\cup B$ 的元素可以构成无限序列

$$
a_{0},b_{0},a_{1},b_{1},\dots,a_{n},b_{n},a_{n+1},\dots
$$

于是 $A\cup B$ 是可数的。

如果 $A\cap B\neq \varnothing$，则取 $C=B\setminus A\subset B$，则 $C$ 是至多可数的，且 $A\cap C=\varnothing$，$A\cup C=A\cup B$，从而由上一种情况可知 $A\cup B$ 是可数的。

(4). 每个 $A_{k}$ 都有 $A_{k}=\{ x_{k 0},x_{k 1},\dots \}$ 或者 $A_{k}=\{ x_{k 0},\dots,x_{k n_{k}} \}$.

如果对于 $i\neq j$ 有 $A_{i}\cap A_{j}=\varnothing$，则构造 $\displaystyle \bigcup_{i=0}^{\infty}A_{i}\to \mathbb{N}$ 的单射

$$
f(x_{ij})=2^{i}3^{j}
$$

根据 (1) 可得 $\displaystyle \bigcup_{i=0}^{\infty}A_{i}$ 是可数集。

如果存在 $i\neq j$ 使得 $A_{i}\cap A_{j}\neq \varnothing$，则递归地构造集合 $B_{n}$ 为

$$
\begin{cases}
B_{0}=A_{0} \\
B_{n+1}=A_{n+1}\setminus \bigcup_{i=0}^{n}A_{i}
\end{cases}
$$

则对于 $i\neq j$ 有 $B_{i}\cap B_{j}=\varnothing$，且 $\displaystyle \bigcup_{i=0}^{\infty}B_{i}=\displaystyle \bigcup_{i=0}^{\infty}A_{i}$，于是根据上一种情况可知 $\displaystyle \bigcup_{i=0}^{\infty}A_{i}$ 是可数集。

# Section 3: 无限和

作为有限和的自然推广，我们定义在可数集上求和的概念。

**定义 7.3.1** 可数和（countable sum）

设 $X$ 是一个可数集，$f\colon X\to \mathbb{R}$，如果存在双射 $g\colon \mathbb{N}\to X$ 使得级数 $\sum_{i=0}^{\infty}f(g(i))$ 绝对收敛，则称级数 $\sum_{x \in X}f(x)$ 绝对收敛，并且定义

$$
\sum_{x \in X} f(x)=\sum_{i=0}^{\infty} f(g(i))
$$

由于绝对收敛级数可以重排，故上述定义是良定的。

利用通常的绝对收敛级数的性质，我们可以证明可数和的相关性质，例如线性性、三角不等式、比较准则等。下面，我们把定理 6.1.4 推广到无穷。

**定理 7.3.2**

设 $X,Y$ 是可数集，则：

1. $\displaystyle \sum_{i \in \mathbb{N}}a_{i}$ 绝对收敛当且仅当 $\displaystyle \sum_{i=0}^{\infty}a_{i}$ 绝对收敛，且这两个级数相等。
2. 换元法：设 $g\colon Y\to X$ 是双射，则 $\displaystyle \sum_{x \in X}f(x)$ 绝对收敛当且仅当 $\displaystyle \sum_{y \in Y}f(g(y))$ 绝对收敛，且这两个级数相等。
3. 设 $X\cap Y=\varnothing$，则 $\displaystyle \sum_{z \in X\cup Y}f(z)$ 绝对收敛当且仅当 $\displaystyle \sum_{x \in X}f(x)$ 和 $\displaystyle \sum_{y \in Y}f(y)$ 绝对收敛，且 $\displaystyle \sum_{z \in X\cup Y}f(z)= \sum_{x \in X}f(x)+ \sum_{y \in Y}f(y)$.

**证明**

1 直接根据定义得到。对于 2，设 $\sum_{x \in X}f(x)$ 绝对收敛，则存在双射 $h\colon \mathbb{N}\to X$ 使得 $\sum_{i=0}^{\infty}f(h(i))$ 绝对收敛，由于 $g$ 是双射，从而 $g^{-1}\circ h\colon \mathbb{N}\to Y$ 也是双射，于是 $\sum_{i=0}^{\infty}f(g(g^{-1}\circ h(i)))=\sum_{i=0}^{\infty}f(h(i))$ 绝对收敛，反之同理。

对于 3，由于 $X,Y$ 是可数集，则 $X\cup Y$ 也是可数集，从而 $X\cup Y$ 的元素可以排成一个无限序列：$x_{0},y_{0},x_{1},y_{1},\dots$，令其为 $\mathbb{N}\to X\cup Y$ 的双射。

设 $\sum_{z \in X\cup Y}f(z)$ 绝对收敛，即 $\sum_{i=0}^{\infty}(|f(x_{i})|+|f(y_{i})|)$ 收敛，令其和为 $M$，于是级数 $\sum_{i=0}^{\infty}|f(x_{i})|$ 和 $\sum_{i=0}^{\infty}|f(y_{i})|$ 的部分和序列有上界 $M$，从而绝对收敛。反之，设 $\sum_{i=0}^{\infty}|f(x_{i})|=L,\sum_{i=0}^{\infty}|f(y_{i})|=K$，则 $\sum_{i=0}^{\infty}(|f(x_{i})|+|f(y_{i})|)$ 的部分和序列有上界 $L+K$，从而绝对收敛。

最后，由线性性我们有

$$
\sum_{i=0}^{\infty} (f(x_{i})+f(y_{i}))=\sum_{i=0}^{\infty} f(x_{i})+\sum_{i=0}^{\infty} f(y_{i})
$$

这就完成了证明。

下面我们考虑无穷级数的 Fubini 定理，它指出：当级数绝对收敛时，可以交换求和的顺序。

**定理 7.3.3** 无穷级数的 Fubini 定理

设 $f\colon \mathbb{N}^{2}\to \mathbb{R}$ 是一个函数，级数 $\sum_{(i,j)\in \mathbb{N}^{2}}f(i,j)$ 绝对收敛，则

$$
\sum_{i=0}^{\infty} \left( \sum_{j=0}^{\infty} f(i,j) \right) =\sum_{(i,j)\in \mathbb{N}^{2}}f(i,j)=\sum_{(j,i)\in \mathbb{N}^{2}}f(i,j)
$$

**证明**

第二个等号使用换元法即可。对第一个等号，我们首先证明其对非负级数成立，之后我们会把这个结果扩展到绝对收敛级数。

设 $f(i,j)\geq 0$，$\sum_{(i,j)\in \mathbb{N}^{2}}f(i,j)=L$，我们要证 $\sum_{i=0}^{\infty} \left( \sum_{j=0}^{\infty} f(i,j) \right)$ 收敛于 $L$. 

显然，对任意有限集 $X\subset \mathbb{N}^{2}$，有 $\sum_{(i,j)\in X}f(i,j)\leq L$，特别地，对任意 $i \in \mathbb{N}$ 和 $m \in \mathbb{N}$，有 $\sum_{j=0}^{m}f(i,j)\leq L$，根据单调收敛定理，对于每个 $i$，级数 $\sum_{j=0}^{\infty}f(i,j)$ 都是收敛的。类似地，对任意 $n,m \in \mathbb{N}$ 有

$$
\sum_{i=0}^{n}\left( \sum_{j=0}^{m} f(i,j) \right)  =\sum_{j=0}^{m}\left( \sum_{i=0}^{n} f(i,j) \right) = \sum_{(i,j)\in X} f(i,j)\leq L
$$

其中 $X=\{ (i,j)\mid i\leq n,j\leq m \}$ 是有限集。于是对每个 $n \in \mathbb{N}$，有

$$
\sum_{j=0}^{\infty}\left( \sum_{i=0}^{n} f(i,j) \right)=\sum_{i=0}^{n} \left( \sum_{j=0}^{\infty} f(i,j) \right) \leq L
$$

成立，从而 $\sum_{i=0}^{\infty} \left( \sum_{j=0}^{\infty} f(i,j) \right)$ 收敛，且极限 $\leq L$. 下面我们只需证明对任意 $\varepsilon>0$，有 $\sum_{i=0}^{\infty} \left( \sum_{j=0}^{\infty} f(i,j) \right)>L-\varepsilon$ 即可。

由于 $\sum_{(i,j)\in \mathbb{N}^{2}}f(i,j)=L$，存在有限集 $X\subset \mathbb{N}^{2}$ 使 $\sum_{(i,j)\in X}f(i,j)>L-\varepsilon$，又因为 $X$ 是有限集，故存在 $n,m \in \mathbb{N}$ 使得 $X\subset \{ (i,j)\mid i\leq n,j\leq m \}$，从而

$$
\sum_{i=0}^{\infty} \left( \sum_{j=0}^{\infty} f(i,j) \right)\geq \sum_{i=0}^{n} \left( \sum_{j=0}^{m} f(i,j) \right) \geq \sum_{(i,j)\in X}f(i,j)> L-\varepsilon
$$

这就完成了证明。

对于绝对收敛级数，我们注意到 $f(i,j)$ 可以写成

$$
f(i,j)=f_{+}(i,j)-f_{-}(i,j)=\max(f(i,j),0)-(-\min(f(i,j),0))
$$

而 $f$ 的正数部分 $f_{+}$ 和负数部分 $f_{-}$ 都是非负且绝对收敛的，将已经证明的结论应用到 $f_{+}$ 和 $f_{-}$ 上，再利用求和的线性性就得到了关于一般的 $f$ 的结论。

接下来，我们考虑如何在不可数集上求和，为此，我们需要将绝对收敛的概念推广至一般的集合，而非仅限于可数集。因此，我们需要下面的定理：

**定理 7.3.4**

设 $X$ 是可数集，$f\colon X\to \mathbb{R}$ 是一个函数，则级数 $\sum_{x \in X}f(x)$ 绝对收敛当且仅当

$$
\sup \left\{  \sum_{x \in A} |f(x)| \middle| A\subset X,A\text{是有限集}  \right\}<+\infty
$$

**证明**

设 $\sum_{x \in X}f(x)$ 绝对收敛，设 $\sum_{x \in X}|f(x)|=L$，则取双射 $g\colon \mathbb{N}\to X$，我们有 $\sum_{i=0}^{n}|f(g(i))|\leq L<+\infty$. 任取 $A\subset X$，由于 $A$ 是有限集，从而 $g[A]$ 也是有限集，于是存在 $n \in \mathbb{N}$ 使得

$$
\sum_{x \in A}|f(x)|\leq \sum_{i=0}^{n} |f(g(i))|<+\infty
$$

从而其上确界也 $<+\infty$.

反之，任取双射 $g\colon \mathbb{N}\to X$，考虑级数 $\sum_{i=0}^{\infty}|f(g(i))|$，其部分和序列的每一项都对应了集合 $\left\{  \sum_{x \in A} |f(x)| \middle| A\subset X,A\text{是有限集}  \right\}$ 中的一个元素，从而其部分和序列有上界，从而 $\sum_{i=0}^{\infty}|f(g(i))|$ 绝对收敛，这就完成了证明。

根据上述定理，我们可以将绝对收敛的概念推广至不可数集。

**定义 7.3.5** 绝对收敛（absolute convergence）

设 $X$ 是一个集合，$f\colon X\to \mathbb{R}$ 是一个函数，称级数 $\sum_{x \in X}f(x)$ **绝对收敛**，如果

$$
\sup \left\{  \sum_{x \in A} |f(x)| \middle| A\subset X,A\text{是有限集}  \right\}<+\infty
$$

然而，我们现在还不知道当 $X$ 是不可数集时应该如何计算 $\sum_{x \in X}f(x)$，下面的引理给出了答案：

**引理 7.3.6**

设 $X$ 是一个集合，$f\colon X\to \mathbb{R}$ 是一个函数，级数 $\sum_{x \in X}f(x)$ 绝对收敛，则集合 $\{ x \in X \mid f(x)\neq 0 \}$ 是至多可数的。

**证明**

根据条件我们可得

$$
M=\sup \left\{  \sum_{x \in A} |f(x)| \middle| A\subset X,A\text{是有限集}  \right\}<+\infty
$$

设 $n\geq 1$，定义集合 $X_{n}=\left\{  x \in X \mid |f(x)|> \dfrac{1}{n}  \right\}$，我们来证明每个 $X_{n}$ 都是有限的。假设 $X_{n}$ 是无限集，那么可以取有限集 $A\subset X_{n}$，其中 $|A|=\lfloor nM \rfloor+1$，于是我们有

$$
\sum_{x \in A}|f(x)|> \dfrac{\lfloor nM \rfloor +1}{n}>M
$$

这与 $M$ 的定义矛盾，故每个 $X_{n}$ 都是有限集。我们有

$$
\{ x \in X \mid f(x)\neq 0 \}=\bigcup_{i=1}^{\infty}X_{i}
$$

可数个有限集的并是至多可数的，这就完成了证明。

于是我们可以定义无限和如下：

**定义 7.3.7** 无限和（infinite sum）

设 $X$ 是一个集合，$f\colon X\to \mathbb{R}$，如果级数 $\sum_{x \in X}f(x)$ 绝对收敛，则定义**无限和**为

$$
\sum_{x \in X} f(x)=\sum_{x \in X,f(x)\neq 0} f(x)
$$

引理 7.3.6 将一个不可数的求和转化为了可数集上的求和，进一步，可数集上的求和又可以转化为我们熟知的无穷级数，而无穷级数又可以转化为有限级数的极限，从而我们就将一个无限和转化为了极限问题。大部分分析的过程，从还原的角度来看，其本质都是一个极限问题，这就是极限在分析学中如此重要的原因。

由于无限和实际上是一个可数和，因此定理 7.3.2 对无限和仍然成立。

最后，我们来研究一下条件收敛级数的重排问题。首先我们证明一个引理：

**引理 7.3.8**

设 $\sum_{i=0}^{\infty}a_{i}$ 条件收敛，定义 $a_{n}^{+}=\max(a_{n},0),a_{n}^{-}=-\min(a_{n},0)$，则级数 $\sum_{i=0}^{\infty}a_{i}^{+}$ 和 $\sum_{i=0}^{\infty}a_{i}^{-}$ 都发散。

**证明**

我们使用反证法。假设两个级数都收敛，则 $|a_{n}|=a_{n}^{+}+a_{n}^{-}$，从而有

$$
\sum_{i=0}^{\infty} |a_{i}|=\sum_{i=0}^{\infty} a_{i}^{+}+\sum_{i=0}^{\infty} a_{i}^{-}
$$

收敛，这与 $\sum_{i=0}^{\infty}a_{i}$ 条件收敛矛盾。假设其中一个级数收敛，不妨设为 $\sum_{i=0}^{\infty}a_{i}^{+}$，由于 $a_{n}=a_{n}^{+}-a_{n}^{-}$，从而有

$$
\sum_{i=0}^{\infty} a_{i}^{-}=\sum_{i=0}^{\infty} a_{i}^{+}-\sum_{i=0}^{\infty} a_{i}
$$

收敛，同样得到矛盾。因此两个级数都发散。

现在我们给出 Riemann 重排定理的证明，它表明，对一个条件收敛级数进行重排，可以使其收敛于任意值。

**定理 7.3.9** Riemann 重排定理

设 $\sum_{i=0}^{\infty}a_{i}$ 条件收敛，$L \in \mathbb{R}$，则存在双射 $f\colon \mathbb{N}\to \mathbb{N}$ 使得 $\sum_{i=0}^{\infty}a_{f(i)}$ 收敛于 $L$.

**证明**

定义 $A_{+}=\{ n \in \mathbb{N} \mid a_{n}\geq 0 \},A_{-}=\{ n \in \mathbb{N} \mid a_{n}<0 \}$，根据引理 7.3.8，$A_{+},A_{-}$ 都是可数集，我们仿照定理 7.2.8 构造严格递增的双射 $f_{+}\colon \mathbb{N}\to A_{+},f_{-}\colon \mathbb{N}\to A_{-}$，从而级数 $\sum_{i=0}^{\infty}a_{f_{+}(i)}$ 和 $\sum_{i=0}^{\infty}a_{f_{-}(i)}$ 都发散。我们将以适当的顺序从两个级数中取出项使其收敛于 $L$.

按下面的方式定义自然数序列 $(n_{i})_{i=0}^{\infty}$：假设对所有 $i<j$ 已经定义了 $n_{i}$，则根据以下情况定义 $n_{j}$：

1. 如果 $\displaystyle \sum_{0\leq i<j}a_{n_{i}}<L$，则令 $n_{j}=\min A_{+}\setminus \{ n_{i} \mid i<j \}$
2. 如果 $\displaystyle \sum_{0\leq i<j}a_{n_{i}}\geq L$，则令 $n_{j}=\min A_{-}\setminus \{ n_{i} \mid i<j \}$

令 $f(j)=n_{j}$，下面我们证明 $f$ 是双射且 $\sum_{i=0}^{\infty}a_{f(i)}=L$.

显然 $f$ 是单射，因为对 $i\neq j$ 有 $n_{i}\neq n_{j}$. 下面我们证明情况 1 和 2 出现了无限次。不妨假设情况 2 出现了有限次，于是存在 $K$ 使得对一切 $j>K$ 有 $\sum_{0\leq i<j}a_{n_{i}}<L$，这表明级数 $\sum_{i=0}^{\infty}a_{i}^{+}$ 收敛，矛盾。

因此情况 1 和 2 都出现了无限次，从而 $f$ 是满射（如不然，则有一种情况只出现了有限次，从而产生矛盾）。并且当 $j\to \infty$ 时，我们有 $n_{j}\to \infty$，从而 $\lim_{ j \to \infty }a_{n_{j}}=0$. 因此对任意 $\varepsilon>0$，存在 $J$ 使得对任意 $j>J$ 有 $|a_{n_{j}}|<\varepsilon$.

设 $S_{k}=\sum_{i=0}^{k}a_{n_{i}}$，则必然存在 $K>J$ 使得 $S_{K}< L$ 且 $S_{K+1}\geq L$，任取 $k>K$，如果 $S_{k-1}< L$，则 $a_{n_{k}}\geq 0$，从而 $S_{k}\leq L+a_{n_{k}}<L+\varepsilon$，如果 $S_{k-1}\geq L$，则 $a_{n_{k}}<0$，从而 $S_{k}>L-|a_{n_{k}}|>L-\varepsilon$，综上，我们有 $|S_{k}-L|<\varepsilon$，于是有 $\sum_{i=0}^{\infty}a_{n_{i}}=L$.

> 这个定理背后的直观是：由于级数的正数部分和负数部分都发散，于是当部分和 $S_{k}<L$ 时，我们可以添加足够多的正项使 $S_{k}\geq L$，此时可以再添加足够多的负项使 $S_{k}<L$，如此往复。因为 $\lim_{ j \to \infty }a_{n_{j}}=0$，所以这种上下振动的幅度是不断减小的，从而就使得级数收敛于 $L$.
> 
> 利用类似的技术，我们也可以证明存在双射使级数发散至 $\pm \infty$，或者不收敛于任何数以及无限实数。以 $+\infty$ 为例，我们可以一直添加正项，直到 $S_{k}>1$，此时添加一个负项，然后再添加正项直到 $S_{k}>2$，添加一个负项，以此类推。对于第三种情况，我们可以取两个数，比如 $1$ 和 $-1$，添加正项直到 $S_{k}>1$，然后添加负项直到 $S_{k}<-1$，如此循环往复。