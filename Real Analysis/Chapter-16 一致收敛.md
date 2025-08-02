前面，我们介绍了在度量空间 $(X,d)$ 中的点列 $(x^{(n)})$ 收敛于 $x \in X$ 的含义，即 $\lim_{ n \to \infty }d(x^{(n)},x)=0$. 在本章中，我们将考虑从度量空间 $(X,d_{X})$ 到度量空间 $(Y,d_{Y})$ 的**函数序列** $(f^{(n)})$ 收敛于函数 $f\colon X\to Y$ 的含义。

事实上，这个问题有多个不同的答案，其中最常见的有两种：**逐点收敛**和**一致收敛**，这两个概念是相互关联的，但不完全相同，它们的关系类似于连续和一致连续之间的关系。

当我们明确了函数序列收敛 $\lim_{ n \to \infty }f^{(n)}=f$ 的含义后，我们就可以研究这种极限如何与其它概念相互作用。例如，我们有函数极限 $\lim_{ x \to x_{0};x \in X }f(x)$ 的概念，那么我们可以问：什么时候有以下等式成立？

$$
\lim_{ n \to \infty } \lim_{ x \to x_{0};x \in X } f^{(n)}(x)=\lim_{ x \to x_{0};x \in X } \lim_{ n \to \infty } f^{(n)}(x)
$$

我们将看到，上式是否成立取决于 $f^{(n)}$ 的收敛类型。不仅是极限，我们还可以问什么时候可以交换极限和求导的顺序、交换极限和积分的顺序等。

# Section 1: 逐点收敛与一致收敛

最明显，也是最直观的一种收敛类型就是逐点收敛，即在定义域内的每一点处收敛。

**定义 16.1.1** 逐点收敛（pointwise convergence）

设 $(f^{(n)})_{n=0}^{\infty}$ 是从度量空间 $(X,d_{X})$ 到度量空间 $(Y,d_{Y})$ 的函数序列，函数 $f\colon X\to Y$，如果对任意 $x \in X$ 有

$$
\lim_{ n \to \infty } f^{(n)}(x)=f(x)
$$

则称 $(f^{(n)})_{n=0}^{\infty}$ 在 $X$ 上**逐点收敛于** $f$，并称其**逐点极限**为 $f$，记作 $\lim_{ n \to \infty }f^{(n)}=f$.

注意，上述定义中 $f^{(n)}(x)$ 和 $f(x)$ 都是 $Y$ 中的点，因此我们使用了度量空间中序列极限的定义来定义逐点极限。根据序列极限的性质我们知道，函数序列的逐点极限最多只有一个。

逐点收敛是一个非常直观和自然的概念，然而，它有一些固有的缺陷：它不能保持连续性、可微性与可积性。我们以一个例子说明这一点。

设定义在 $[0,1]$ 上的函数序列为 $f^{(n)}(x)=x^{n}$，根据定义，当 $0\leq x<1$ 时，$f^{(n)}(x)$ 收敛于 $0$，而当 $x=1$ 时，$f^{(n)}(x)$ 收敛于 $1$，从而其逐点极限为

$$
f(x)=\begin{cases}
0 &, 0\leq x<1 \\
1 &, x=1
\end{cases}
$$

显然，每个 $f^{(n)}$ 在 $[0,1]$ 上都连续，但是 $f$ 在 $[0,1]$ 上不连续。

这种现象产生的原因与我们引入一致连续概念时的原因本质上是一样的：对于 $0\leq x<1$，尽管每个 $x^{n}$ 在 $n\to \infty$ 时都收敛于 $0$，但是它们收敛的**速度**是不一样的：$x$ 接近 $0$ 时的收敛速度显然要比 $x$ 接近 $1$ 时的收敛速度快得多。

换言之，$f^{(n)}(x)$ 关于 $x$ 的收敛性不是**一致的**：使得 $d_{Y}(f^{(n)}(x),f(x))<\varepsilon$ 的 $N$ 不仅取决于 $\varepsilon$，还取决于 $x$. 这就启发我们给出另一种定义。

**定义 16.1.2** 一致收敛（uniform convergence）

设 $(f^{(n)})_{n=0}^{\infty}$ 是从度量空间 $(X,d_{X})$ 到度量空间 $(Y,d_{Y})$ 的函数序列，函数 $f\colon X\to Y$，如果对任意 $\varepsilon>0$，存在 $N \in \mathbb{N}$ 使得对任意 $n>N$ 和 $x \in X$ 有 $d_{Y}(f^{(n)}(x),f(x))<\varepsilon$，则称 $(f^{(n)})_{n=0}^{\infty}$ 在 $X$ 上**一致收敛于** $f$，并称其**一致极限**为 $f$，仍然记作 $\lim_{ n \to \infty }f^{(n)}=f$.

如果 $(f^{(n)})$ 一致收敛于 $f$，那么它也一定逐点收敛于 $f$，反之则不然（我们已经看到了一个例子）。

一致收敛有许多好的性质，下面我们给出一个例子。

**定义 16.1.3** 有界函数（bounded function）

设 $(X,d_{X}),(Y,d_{Y})$ 是度量空间，函数 $f\colon X\to Y$，称 $f$ 在 $X$ 上是**有界的**，如果存在 $y_{0}\in Y$ 和 $r>0$ 使得对任意 $x \in X$ 有 $f(x)\in B_{(Y,d_{Y})}(y_{0},r)$.

**定理 16.1.4**

设 $(f^{(n)})_{n=0}^{\infty}$ 是从度量空间 $(X,d_{X})$ 到度量空间 $(Y,d_{Y})$ 的有界函数序列，且一致收敛于有界函数 $f\colon X\to Y$，那么 $(f^{(n)})$ 是**一致有界的**：存在开球 $B_{(Y,d_{Y})}(y_{0},R)$ 使得对任意 $x \in X$ 和 $n \in \mathbb{N}$ 都有 $f^{(n)}(x)\in B_{(Y,d_{Y})}(y_{0},R)$.

**证明**

由于 $f$ 是有界的，故存在开球 $B_{(Y,d_{Y})}(y_{0},r)$ 使得对任意 $x \in X$ 有 $f(x)\in B(y_{0},r)$，又 $(f^{(n)})$ 一致收敛于 $f$，故对任意 $\varepsilon>0$，存在 $N$ 使得对任意 $n>N$ 和 $x \in X$ 有 $d_{Y}(f^{(n)}(x),f(x))<\varepsilon$.

固定 $\varepsilon=1$，则对任意 $n>N$ 和 $x \in X$ 有

$$
d_{Y}(f^{(n)}(x),y_{0})\leq d_{Y}(f^{(n)}(x),f(x))+d_{Y}(f(x),y_{0})<r+1
$$

即 $f^{(n)}(x)\in B(y_{0},r+1)$. 对于每个 $0\leq n\leq N$，由于 $f^{(n)}$ 是有界的，故有 $r_{n}>0$ 使得对任意 $x \in X$ 有 $f^{(n)}(x)\in B(y_{0},r_{n})$，现在令

$$
R=\max(r_{0},\dots,r_{N},r+1)
$$

则对任意 $x \in X$ 和 $n \in \mathbb{N}$ 有 $f^{(n)}(x)\in B(y_{0},R)$，即证。

将上述定理的证明与“收敛序列是有界序列”（定理 3.1.5）的证明对照一下，可以发现它们的结构是相同的：在某个界限 $N$ 之后，序列中的项的有界性是由极限所保证的，而在界限之前的项充当“修正项”添加到 $\max$ 函数中。

这种一致收敛与序列收敛的相似性并非偶然：它们在本质上是相同的，即某种度量下序列的收敛，我们之后会谈到这一点。

# Section 2: 连续性

现在我们给出一致收敛优于逐点收敛的第一个主要性质：一致收敛保持连续性。

**定理 16.2.1**

设 $(f^{(n)})_{n=0}^{\infty}$ 是从度量空间 $(X,d_{X})$ 到度量空间 $(Y,d_{Y})$ 的函数序列，并且一致收敛于 $f\colon X\to Y$，$x_{0}\in X$，如果对任意 $n \in \mathbb{N}$，函数 $f^{(n)}$ 在 $x_{0}$ 处连续，那么 $f$ 也在 $x_{0}$ 处连续。

**证明**

给定 $n$，对任意 $\varepsilon>0$，存在 $\delta>0$ 使得对任意 $d_{X}(x,x_{0})<\delta$ 的 $x \in X$ 有 $d_{Y}(f^{(n)}(x),f^{(n)}(x_{0}))<\varepsilon$.

同样，也存在 $N$ 使得对任意 $n>N$ 和 $x \in X$ 有 $d_{Y}(f^{(n)}(x),f(x))<\varepsilon$.

那么，对任意 $d_{X}(x,x_{0})<\delta$ 的 $x \in X$ 有

$$
\begin{align}
d_{Y}(f(x),f(x_{0})) &\leq d_{Y}(f(x),f^{(N+1)}(x))+d_{Y}(f^{(N+1)}(x),f^{(N+1)}(x_{0})) \\
& +d_{Y}(f^{(N+1)}(x_{0}),f(x_{0})) \\
& < 3\varepsilon
\end{align}
$$

这就完成了证明。

我们可以从证明过程中看出，一致收敛的条件是必要的，否则就不能保证对每个 $x \in B(x_{0},\delta)$ 都有 $d_{Y}(f(x),f^{(N+1)}(x))<\varepsilon$.

将上面的定理稍作修改，我们就可以得到以下结果：

**定理 16.2.2**

设 $(X,d_{X}),(Y,d_{Y})$ 是度量空间，$Y$ 是完备的，$E\subset X$，设 $(f^{(n)})_{n=0}^{\infty}$ 是从 $X$ 到 $Y$ 的函数序列，且在 $X$ 上一致收敛于 $f\colon X\to Y$，设 $x_{0}\in X$ 是 $E$ 的极限点，并且对每个 $n \in \mathbb{N}$，极限 $\lim_{ x \to x_{0};x \in E }f^{(n)}(x)$ 都存在，那么极限 $\lim_{ x \to x_{0};x \in E }f(x)$ 也存在，并且

$$
\lim_{ n \to \infty } \lim_{ x \to x_{0};x \in E } f^{(n)}(x)=\lim_{ x \to x_{0};x \in E } f(x)
$$

**证明**

给定 $n$，设 $\lim_{ x \to x_{0};x \in E }f^{(n)}(x)=L_{n}$，则对任意 $\varepsilon>0$，存在 $\delta_{n}>0$ 使得对任意 $0<d_{X}(x,x_{0})<\delta_{n}$ 的 $x \in E$ 有 $d_{Y}(f^{(n)}(x),L_{n})<\varepsilon$.

同样，也存在 $N$ 使得对任意 $n>N$ 和 $x \in X$ 有 $d_{Y}(f^{(n)}(x),f(x))<\varepsilon$.

现证 $\lim_{ n \to \infty }L_{n}$ 存在。任取 $n,m>N$ 和 $0<d_{X}(x,x_{0})<\min(\delta_{n},\delta_{m})$ 的 $x \in E$，有

$$
\begin{align}
d_{Y}(L_{n},L_{m}) &\leq d_{Y}(L_{n},f^{(n)}(x))+d_{Y}(f^{(n)}(x),f(x)) \\
& + d_{Y}(f(x),f^{(m)}(x))+d_{Y}(f^{(m)}(x),L_{m}) \\
& < 4\varepsilon
\end{align}
$$

从而 $(L_{n})$ 是 Cauchy 序列，由 $Y$ 的完备性知其收敛，设其极限为 $L$.

于是，存在 $N_{1}>N$ 使得对任意 $n>N_{1}$ 有 $d_{Y}(L_{n},L)<\varepsilon$. 从而对任意 $0<d_{X}(x,x_{0})<\delta_{N_{1}+1}$ 的 $x \in E$ 有

$$
\begin{align}
d_{Y}(f(x),L) &\leq d_{Y}(f(x),f^{(N_{1}+1)}(x))+d_{Y}(f^{(N_{1}+1)}(x),L_{N_{1}+1}) \\
& + d_{Y}(L_{N_{1}+1},L) \\
& < 3\varepsilon
\end{align}
$$

这就完成了证明。

简单来说，只要 $f^{(n)}$ 一致收敛，那么我们就可以交换函数极限与一致极限的顺序。利用定理 16.2.2 可以证明定理 16.2.1，但是使用 $\varepsilon-\delta$ 定义证明是最简单的。

下面，我们给出定理 16.2.1 的序列形式。

**定理 16.2.3**

设 $(f^{(n)})_{n=0}^{\infty}$ 是从度量空间 $(X,d_{X})$ 到度量空间 $(Y,d_{Y})$ 的函数序列，并且一致收敛于 $f\colon X\to Y$，$x_{0}\in X$，对任意 $n \in \mathbb{N}$，函数 $f^{(n)}$ 在 $x_{0}$ 处连续，如果 $(x^{(n)})_{n=0}^{\infty}$ 是 $X$ 中收敛于 $x_{0}$ 的序列，那么序列 $(f^{(n)}(x^{(n)}))_{n=0}^{\infty}$ 收敛于 $f(x_{0})$.

**证明**

根据定理 16.2.1，$f$ 在 $x_{0}$ 处连续，故序列 $(f(x^{(n)}))_{n=0}^{\infty}$ 收敛于 $f(x_{0})$.

由一致收敛性，对任意 $\varepsilon>0$，存在 $N_{1}$ 使得对任意 $n>N_{1}$ 和 $x \in X$ 有 $d_{Y}(f^{(n)}(x),f(x))<\varepsilon$，从而 $d_{Y}(f^{(n)}(x^{(n)}),f(x^{(n)}))<\varepsilon$，即 $(f^{(n)}(x^{(n)}))$ 等价于 $(f(x^{(n)}))$，故 $\lim_{ n \to \infty }f^{(n)}(x^{(n)})=f(x_{0})$.

对于有界函数，也有一个类似的性质：一致收敛保持有界性。

**定理 16.2.4**

设 $(f^{(n)})_{n=0}^{\infty}$ 是从度量空间 $(X,d_{X})$ 到度量空间 $(Y,d_{Y})$ 的有界函数序列，且一致收敛于函数 $f\colon X\to Y$，那么 $f$ 也是有界的。

**证明**

给定 $n$ 和 $y_{0}\in Y$，存在 $r_{n}>0$ 使得对任意 $x \in X$ 有 $f^{(n)}(x)\in B(y_{0},r_{n})$.

由一致收敛性，对任意 $\varepsilon>0$，存在 $N$ 使得对任意 $n>N$ 和 $x \in X$ 有 $d_{Y}(f(x),f^{(n)}(x))<\varepsilon$. 固定 $\varepsilon=1$，则有

$$
d_{Y}(f(x),y_{0})\leq d_{Y}(f(x),f^{(N+1)}(x))+d_{Y}(f^{(N+1)}(x),y_{0})<r_{N+1}+1
$$

从而 $f$ 是有界的。

结合定理 16.2.4 与 16.1.4，我们知道：如果有界函数序列一致收敛，那么该序列是一致有界的。

以上的定理看起来都很直观，但我们要注意，这些结果只在一致收敛时才成立。

最后我们给出一个定理。

**定理 16.2.5**

设 $(X,d)$ 是度量空间，$(f^{(n)}),(g^{(n)})$ 是 $X$ 到 $\mathbb{R}$ 的一致有界函数列，并且分别一致收敛于 $f\colon X\to \mathbb{R}$ 和 $g\colon X\to \mathbb{R}$，那么函数列 $(f^{(n)}g^{(n)})$ 一致收敛于 $fg$.

**证明**

根据一致有界性，存在实数 $M>0$ 使得对任意 $n$ 和 $x \in X$ 有 $|f^{(n)}(x)|\leq M$ 且 $|g^{(n)}(x)|\leq M$. 根据定理 16.2.4，函数 $f,g$ 也是有界的，不妨设对任意 $x \in X$ 也有 $|f(x)|\leq M,|g(x)|\leq M$.

再由一致收敛性，对任意 $\varepsilon>0$，存在 $N$ 使得对任意 $n>N$ 和 $x \in X$ 有 $|f^{(n)}(x)-f(x)|<\varepsilon$ 且 $|g^{(n)}(x)-g(x)|<\varepsilon$，从而

$$
\begin{align}
|f^{(n)}g^{(n)}(x)-fg(x)| &\leq |f^{(n)}(x)||g^{(n)}(x)-g(x)|+|g(x)||f^{(n)}(x)-f(x)| \\
& < 2M\varepsilon
\end{align}
$$

即 $(f^{(n)}g^{(n)})$ 一致收敛于 $fg$.

# Section 3: 一致度量

前面我们提到，点列 $(x^{(n)})$ 的收敛与函数列 $(f^{(n)})$ 的收敛本质上是相同的，它们都是某个度量下的序列收敛，现在我们就来解释这一点。

回顾一致收敛的定义，它表明：对任意 $\varepsilon>0$，存在 $N$ 使得对任意 $n>N$ 和 $x \in X$ 有 $d_{Y}(f^{(n)}(x),f(x))<\varepsilon$，即

$$
\sup_{x \in X} d_{Y}(f^{(n)}(x),f(x))\leq\varepsilon
$$

我们将左边记为 $d_{\infty}(f^{(n)},f)$，那么 $d_{\infty}$ 就是一个正定的、对称的、而且满足三角不等式的实值函数：一个度量。而这个度量空间与我们之前遇到的度量空间都不同，它是一个**函数空间**。

**定义 16.3.1** $L^{\infty}$ 度量

设 $(X,d_{X}),(Y,d_{Y})$ 是度量空间，我们定义 $X\to Y$ 的有界函数空间

$$
B(X,Y)=\{ f\mid f\colon X\to Y \text{是有界函数} \}
$$

上的 $L^{\infty}$ **度量**或**一致度量**为

$$
d_{\infty}(f,g)=\sup_{x \in X} d_{Y}(f(x),g(x))
$$

根据上面的分析，$(B(X,Y),d_{\infty})$ 就是一个度量空间，并且函数序列 $(f^{(n)})$ 一致收敛于 $f$ 当且仅当 $(f^{(n)})$ 按度量 $d_{\infty}$ 收敛于 $f$. 这就解释了为什么 $X$ 中的序列极限与 $B(X,Y)$ 上的一致极限如此相似。

现在我们令

$$
C^{0}(X,Y)=\{ f \mid f\colon X\to Y \text{是有界连续函数} \}
$$

那么定理 16.2.1 指出：$C^{0}(X,Y)$ 在 $B(X,Y)$ 中是闭集。事实上，我们还可以更进一步。

**定理 16.3.2**

设 $(X,d_{X}),(Y,d_{Y})$ 是度量空间，$Y$ 是完备的，那么 $C^{0}(X,Y)$ 是 $B(X,Y)$ 的完备子空间。

**证明**

设 $(f^{(n)})$ 是 $C^{0}(X,Y)$ 中的 Cauchy 序列，即对任意 $\varepsilon>0$，存在 $N$ 使得对任意 $n,m>N$ 和 $x \in X$ 有

$$
d_{Y}(f^{(n)}(x),f^{(m)}(x))\leq d_{\infty}(f^{(n)},f^{(m)})<\varepsilon
$$

从而序列 $(f^{(n)}(x))$ 是 $Y$ 中的 Cauchy 序列，由 $Y$ 的完备性知其收敛，记其极限为 $f(x)$.

任取 $x \in X$，则存在 $N_{x}>N$ 使得对任意 $n>N_{x}$ 有 $d_{Y}(f^{(n)}(x),f(x))<\varepsilon$，从而对任意 $m>N$ 和 $x \in X$ 有

$$
d_{Y}(f^{(m)}(x),f(x))\leq d_{Y}(f^{(m)}(x),f^{(N_{x}+1)}(x))+d_{Y}(f^{(N_{x}+1)}(x),f(x))<2\varepsilon
$$

从而 $(f^{(n)})$ 一致收敛于 $f$，根据定理 16.2.1 和 16.2.4 知 $f \in C^{0}(X,Y)$，这就完成了证明。

# Section 4: 函数级数

在讨论了函数序列后，我们来看函数的级数。由于 $(Y,d_{Y})$ 上通常没有加法结构，因此我们将考察 $X\to \mathbb{R}$ 的实值函数。我们首先考虑有限和。

设 $(f^{(n)})_{n=0}^{N}$ 是 $X\to \mathbb{R}$ 的函数序列，那么它的有限和可以定义为

$$
\left( \sum_{i=0}^{n} f^{(i)} \right)(x)=\sum_{i=0}^{n} f^{(i)}(x)
$$

显然，有界函数的有限和是有界的，连续函数的有限和是连续的。下面我们来考虑无穷级数。

**定义 16.4.1** 级数的逐点收敛与一致收敛

设 $(X,d)$ 是度量空间，$(f^{(n)})_{n=0}^{\infty}$ 是 $X$ 到 $\mathbb{R}$ 的函数序列，函数 $f\colon X\to \mathbb{R}$，定义**部分和序列** $(S^{(n)})_{n=0}^{\infty}$ 为

$$
S^{(n)}=\sum_{i=0}^{n} f^{(i)}
$$

如果 $(S^{(n)})_{n=0}^{\infty}$ 逐点收敛于 $f$，则称级数 $\sum_{i=0}^{\infty}f^{(i)}$ 在 $X$ 上**逐点收敛于** $f$，记作 $f=\sum_{i=0}^{\infty}f^{(i)}$；如果 $(S^{(n)})_{n=0}^{\infty}$ 一致收敛于 $f$，则称级数 $\sum_{i=0}^{\infty}f^{(i)}$ 在 $X$ 上**一致收敛于** $f$，仍然记作 $f=\sum_{i=0}^{\infty}f^{(i)}$.

将函数序列的结论应用到部分和 $(S^{(n)})$ 上，我们就知道了：如果 $\sum_{i=0}^{\infty}f^{(i)}$ 一致收敛于 $f$，并且每个 $f^{(n)}$ 都连续（有界），那么 $\sum_{i=0}^{\infty}f^{(i)}$ 也连续（有界）。

此外，对于级数，还有一种非常有用的判别法，称为 **Weierstrass M 判别法**，它可以用一个实数级数来判断函数级数的一致收敛性。

在此之前，我们先引入一个概念。

**定义 16.4.2** $L^{\infty}$ 范数

设 $(X,d)$ 是度量空间，$B(X,\mathbb{R})$ 上的 $L^{\infty}$ **范数**定义为

$$
\lVert f \rVert _{\infty}=\sup_{x \in X} |f(x)|
$$

这使得 $B(X,\mathbb{R})$ 成为了一个赋范空间，并且有 $d_{\infty}(f,g)=\lVert f-g \rVert_{\infty}$.

**定理 16.4.3** Weierstrass M 判别法

设 $(X,d)$ 是度量空间，$(f^{(n)})_{n=0}^{\infty}$ 是 $X$ 到 $\mathbb{R}$ 的有界连续函数序列，并且级数 $\sum_{i=0}^{\infty} \lVert f^{(i)} \rVert _{\infty}$ 收敛，那么级数 $\sum_{i=0}^{\infty}f^{(i)}$ 一致收敛。

**证明**

设 $(S^{(n)})_{n=0}^{\infty}$ 是级数的部分和，由于 $\sum_{i=0}^{\infty}\lVert f^{(i)} \rVert_{\infty}$ 收敛，故对任意 $\varepsilon>0$，存在 $N$ 使得对任意 $n>N,p>0$ 有

$$
d_{\infty}(S^{(n+p)},S^{(n)})=\lVert S^{(n+p)}-S^{(n)} \rVert _{\infty}\leq\lVert f^{(n+1)} \rVert _{\infty}+\dots+\lVert f^{(n+p)} \rVert _{\infty}<\varepsilon
$$

从而 $(S^{(n)})_{n=0}^{\infty}$ 是 $C^{0}(X,\mathbb{R})$ 中的 Cauchy 序列，由完备性知其按度量 $d_{\infty}$ 收敛，即证。

利用 Weierstrass M 判别法，我们可以证明很多级数的一致收敛性，下面我们给出一个例子。

**命题 16.4.4** 几何级数（geometric series）

设实数 $0<r<1$，函数 $f^{(n)}\colon [-r,r]\to \mathbb{R}$ 定义为 $f^{(n)}(x)=x^{n}$，则**几何级数** $\sum_{i=0}^{\infty}x^{i}$ 在 $[-r,r]$ 上一致收敛于函数 $\dfrac{1}{1-x}$.

**证明**

显然，每个 $f^{(n)}$ 都是连续且有界的，并且 $\lVert f^{(n)} \rVert_{\infty}=r^{n}$，而级数 $\sum_{i=0}^{\infty}r^{i}$ 绝对收敛（利用比值判别法），故级数 $\sum_{i=0}^{\infty}f^{(i)}$ 一致收敛。

设 $x \in[-r,r]$，则部分和为 $S^{(n)}(x)=\dfrac{1-x^{n+1}}{1-x}$，当 $n\to \infty$ 时 $S^{(n)}(x)$ 收敛于 $\dfrac{1}{1-x}$，这就完成了证明。

# Section 5: 可积性与可微性

现在我们考虑一致收敛性与 Riemann 积分的关系。下面的定理指出：如果可积序列一致收敛，那么积分和一致极限就可以交换顺序。

**定理 16.5.1**

设实数 $a<b$，$(f^{(n)})_{n=0}^{\infty}$ 是 $[a,b]$ 到 $\mathbb{R}$ 的 Riemann 可积函数序列，并且一致收敛于 $f\colon [a,b]\to \mathbb{R}$，那么 $f$ 在 $[a,b]$ 上 Riemann 可积，并且

$$
\lim_{ n \to \infty } \int_{a}^{b} f^{(n)}=\int_{a}^{b} f
$$

**证明**

对任意 $\varepsilon>0$，存在 $N$ 使得对任意 $n>N$ 和 $x \in[a,b]$ 有 $|f^{(n)}(x)-f(x)|<\varepsilon$，即

$$
f^{(n)}(x)-\varepsilon<f(x)<f^{(n)}(x)+\varepsilon
$$

由于 $f^{(n)}$ Riemann 可积，故

$$
\int_{a}^{b}f^{(n)}-\varepsilon(b-a)<\underline{\int_{a}^{b}}f\leq \overline{\int_{a}^{b}}f<\int_{a}^{b}f^{(n)}+\varepsilon(b-a)
$$

从而 $\underline{\int_{a}^{b}}f= \overline{\int_{a}^{b}}f$，即 $f$ 在 $[a,b]$ 上 Riemann 可积。于是对任意 $n>N$ 有

$$
\left| \int_{a}^{b}f - \int_{a}^{b} f^{(n)} \right| <\varepsilon(b-a)
$$

这就完成了证明。

将上述定理应用到级数上，我们就有如下推论：

**定理 16.5.2** 逐项积分法（termwise integration）

设实数 $a<b$，$(f^{(n)})_{n=0}^{\infty}$ 是 $[a,b]$ 到 $\mathbb{R}$ 的 Riemann 可积函数序列，如果级数 $\sum_{i=0}^{\infty}f^{(i)}$ 一致收敛，那么

$$
\sum_{i=0}^{\infty} \int_{a}^{b}f^{(i)}=\int_{a}^{b} \sum_{i=0}^{\infty} f^{(i)}
$$

下面，我们来考察一致极限与导数的关系，我们把函数序列写成 $(f_{n})$ 以防止与函数的导数相混淆。

假设 $(f_{n})$ 一致收敛于 $f$，并且每个 $f_{n}$ 都可微，那么 $f$ 是否也可微呢？遗憾的是，这是不成立的。我们来看一个例子。

设 $f_{n}\colon [-1,1]\to \mathbb{R}$ 定义为 $f_{n}(x)=\sqrt{ x^{2}+\dfrac{1}{n^{2}} }$，那么每个 $f_{n}$ 都可微，然而，当 $n\to \infty$ 时，$f_{n}$ 一致收敛于绝对值函数 $|x|$，而该函数在 $x=0$ 处不可微。因此，$f_{n}$ 的一致收敛无法给出 $f_{n}'$ 的任何信息，然而，我们可以证明反过来的结论是成立的。

**定理 16.5.3**

设实数 $a<b$，$(f_{n})_{n=0}^{\infty}$ 是 $[a,b]$ 到 $\mathbb{R}$ 的可微函数序列，如果导函数序列 $(f_{n}')_{n=0}^{\infty}$ 一致收敛于函数 $g\colon [a,b]\to \mathbb{R}$，并且存在一点 $x_{0}\in[a,b]$ 使得 $\lim_{ n \to \infty }f_{n}(x_{0})$ 存在，那么 $(f_{n})_{n=0}^{\infty}$ 一致收敛于可微函数 $f\colon [a,b]\to \mathbb{R}$，并且 $f'=g$.

**证明**

由于 $(f_{n}')$ 一致收敛于 $g$，故对任意 $\varepsilon>0$，存在 $N_{1}$ 使得对任意 $n,m>N_{1}$ 有 $d_{\infty}(f_{n}',f_{m}')<\varepsilon$，于是对任意 $x \in[a,b]$ 有 $|f_{n}'(x)-f_{m}'(x)|<\varepsilon$，根据中值定理有

$$
\begin{align}
& |(f_{n}(x)-f_{m}(x))-(f_{n}(x_{0})-f_{m}(x_{0}))|  \\
& = |(f_{n}'(\xi)-f_{m}'(\xi))(x-x_{0})|\leq \varepsilon|x-x_{0}|
\end{align}
$$

于是有

$$
|f_{n}(x)-f_{m}(x)|\leq |f_{n}(x_{0})-f_{m}(x_{0})|+\varepsilon|x-x_{0}|
$$

由于 $\lim_{ n \to \infty }f_{n}(x_{0})$ 存在，故存在 $N_{2}>N_{1}$ 使得对任意 $n,m>N_{2}$ 有 $|f_{n}(x_{0})-f_{m}(x_{0})|<\varepsilon$，又 $x \in[a,b]$，故存在 $M$ 使得 $|x-x_{0}|\leq M$，从而 $|f_{n}(x)-f_{m}(x)|<\varepsilon(1+M)$，显然 $f_{n}$ 是 $[a,b]$ 上的有界连续函数，故 $(f_{n})$ 是 $C^{0}([a,b],\mathbb{R})$ 上的 Cauchy 序列，从而 $(f_{n})$ 一致收敛于 $f$.

任取 $x,y \in[a,b]$，则对任意 $n,m>N_{1}$ 有

$$
|(f_{n}(y)-f_{m}(y))-(f_{n}(x)-f_{m}(x))|\leq\varepsilon|y-x|
$$

令 $m\to \infty$，则有

$$
\begin{align}
& |(f_{n}(y)-f(y))-(f_{n}(x)-f(x))| \\
& = |(f_{n}(y)-f_{n}(x))-(f(y)-f(x))|\leq \varepsilon|y-x|
\end{align}
$$

设 $y\neq x$，令 $F_{n}(y)=\dfrac{f_{n}(y)-f_{n}(x)}{y-x},F(y)=\dfrac{f(y)-f(x)}{y-x}$，则 $(F_{n})$ 一致收敛于 $F$，从而根据定理 16.2.2 有

$$
\lim_{ y \to x } F(y)=\lim_{ n \to \infty } \lim_{ y \to x } F_{n}(y)=\lim_{ n \to \infty } f_{n}'(x)=g(x)
$$

因此 $f$ 在 $x$ 处可微且导数为 $g(x)$，这就完成了证明。

简单来说，上述定理表明，如果 $(f_{n}')$ 一致收敛，并且对于某个 $x_{0}$，序列 $(f_{n}(x_{0}))$ 也收敛，那么 $(f_{n})$ 一致收敛，并且

$$
\dfrac{\mathrm{d} }{\mathrm{d} x}\lim_{ n \to \infty } f_{n}(x)=\lim_{ n \to \infty } \dfrac{\mathrm{d} }{\mathrm{d} x} f_{n}(x)
$$

将上述定理应用到级数上，我们就有推论：

**定理 16.5.4** 逐项求导法（termwise differentiation）

设实数 $a<b$，$(f_{n})_{n=0}^{\infty}$ 是 $[a,b]$ 到 $\mathbb{R}$ 的可微函数序列，如果级数 $\sum_{i=0}^{\infty}f_{i}'$ 一致收敛，并且存在一点 $x_{0}\in[a,b]$ 使得级数 $\sum_{i=0}^{\infty}f_{i}(x_{0})$ 收敛，那么 $\sum_{i=0}^{\infty}f_{i}$ 一致收敛，并且

$$
\dfrac{\mathrm{d} }{\mathrm{d} x}\sum_{i=0}^{\infty} f_{i}(x)=\sum_{i=0}^{\infty} \dfrac{\mathrm{d} }{\mathrm{d} x}f_{i}(x)
$$

通常，上述定理是和 Weierstrass M 判别法结合起来使用：我们可以将条件 $\sum_{i=0}^{\infty}f_{i}'$ 一致收敛换成级数 $\sum_{i=0}^{\infty}\lVert f_{i}' \rVert_{\infty}$ 收敛。

# Section 6: 多项式的一致逼近

尽管连续函数有很多较好的性质，但有时候它的行为可能会变得极为病态：Weierstrass 曾发现一个函数

$$
f(x)=\sum_{n=1}^{\infty} \dfrac{1}{4^{n}}\cos(32^{n}\pi x)
$$

它在 $\mathbb{R}$ 上处处连续（由 Weierstrass M 判别法可知其一致收敛），但是处处不可微。我们将在定义了三角函数以后来证明这一点。

然而，像多项式这样的函数，其行为总是好的：它在 $\mathbb{R}$ 上连续，并且有无穷阶导数。幸运的是，尽管大部分连续函数的性质不那么好，但它们总是可以由多项式**一致逼近**。这个结果被称为 **Weierstrass 逼近定理**。

**定义 16.6.1** 多项式（polynomial）

设实数 $a<b$，则区间 $[a,b]$ 上的**多项式**是形如

$$
p(x)=\sum_{i=0}^{n} c_{i}x^{i},c_{n}\neq 0
$$

的函数 $p\colon [a,b]\to \mathbb{R}$，其中 $c_{j}\in \mathbb{R}$，$n$ 称为 $p$ 的**次数**，记作 $\deg p$.

**定理 16.6.2** Weierstrass 逼近定理

设实数 $a<b$，函数 $f\colon [a,b]\to \mathbb{R}$ 是连续函数，那么对任意 $\varepsilon>0$ 都存在 $[a,b]$ 上的多项式 $p$ 使得 $d_{\infty}(p,f)<\varepsilon$.

这个定理还可以用度量空间的语言来叙述。我们令

$$
P([a,b],\mathbb{R})=\{ p \mid p\colon [a,b]\to \mathbb{R} \text{是多项式} \}
$$

每个多项式都连续，故 $P([a,b],\mathbb{R})$ 是 $C^{0}([a,b],\mathbb{R})$ 的子空间，那么 Weierstrass 逼近定理指出：每个 $f \in C^{0}([a,b],\mathbb{R})$ 都是 $P([a,b],\mathbb{R})$ 的附着点，或者说多项式空间的闭包就是连续函数空间：

$$
\overline{P([a,b],\mathbb{R})}=C^{0}([a,b],\mathbb{R})
$$

根据定理 14.2.4，这表明每个连续函数 $f\colon [a,b]\to \mathbb{R}$ 都是某个多项式序列 $(p_{n})$ 的一致极限，这就是一致逼近的内涵。

Weierstrass 逼近定理的证明比较复杂，因此我们把它放在附录中。下面我们列举一些在定理的证明过程中用到的定义。

**定义 16.6.3** 支撑（support）

称函数 $f\colon \mathbb{R}\to \mathbb{R}$ **支撑在** $X\subset \mathbb{R}$ **上**，如果对任意 $x \in \mathbb{R}\setminus X$ 有 $f(x)=0$. 称函数 $f$ 是**紧支撑的**，如果它支撑在某个区间 $[a,b]$ 上。

当 $f$ 连续且支撑在 $[a,b]$ 上时，我们可以定义

$$
\int_{\mathbb{R}}f=\int_{a}^{b}f
$$

这是因为 $f$ 在除 $[a,b]$ 中的点外都为 $0$. 然而一个函数可以有多个支撑，比如支撑在 $[1,2]$ 上的函数也支撑在 $[0,3]$ 上，因此 $\int_{\mathbb{R}}f$ 的定义可能是不确定的，但事实并非如此。

**定理 16.6.4**

设函数 $f\colon \mathbb{R}\to \mathbb{R}$ 是连续函数，如果 $f$ 支撑在区间 $[a,b]$ 和 $[c,d]$ 上，那么 $\int_{a}^{b}f=\int_{c}^{d}f$.

**证明**

如果 $f=0$，那么结论显然成立。如果存在一点 $x_{0}$ 使得 $f(x_{0})\neq 0$，那么我们有 $c< x_{0}< b$，下面我们分情况讨论 $a$ 和 $c$、$b$ 和 $d$ 的大小关系。

不妨设 $a\leq c,d\leq b$，那么在 $[a,c]\cup[d,b]$ 上 $f(x)=0$，从而

$$
\int_{a}^{b}f=\int_{a}^{c}f+\int_{c}^{d}f+\int_{d}^{b}f=\int_{c}^{d}f
$$

其它情况同理。

**定义 16.6.5** 恒等逼近（approximation to the identity）

设 $\varepsilon>0,0<\delta<1$，称函数 $f\colon \mathbb{R}\to \mathbb{R}$ 是一个 $(\varepsilon,\delta)$**-恒等逼近**，如果

1. $f$ 支撑在 $[-1,1]$ 上，并且对任意 $x \in[-1,1]$ 有 $f(x)\geq 0$.
2. $f$ 是连续的，并且 $\int_{\mathbb{R}}f=1$.
3. 对任意 $\delta<|x|<1$ 有 $f(x)<\varepsilon$.

事实上，所谓的恒等逼近就是用连续函数逼近 Dirac $\delta$ 函数，在物理中，它通常被定义为

$$
\delta(x)=\begin{cases}
0 &, x\neq 0 \\
+\infty &, x=0
\end{cases}
$$

并且有 $\int_{\mathbb{R}}\delta=1$. 但是在数学中，我们通常将它看作是一列函数的极限。而所谓的恒等，就是指 $\delta$ 函数在**卷积**运算下是恒等元素。

**定义 16.6.6** 卷积（convolution）

设 $f\colon \mathbb{R}\to \mathbb{R}$ 和 $g\colon \mathbb{R}\to \mathbb{R}$ 都是连续的紧支撑函数，定义 $f$ 和 $g$ 的**卷积**为

$$
f*g(x)=\int_{\mathbb{R}}f(y)g(x-y)\mathrm{d} y
$$

下面给出卷积的一些基本性质。

**定理 16.6.7**

设 $f,g,h$ 都是 $\mathbb{R}\to \mathbb{R}$ 的连续紧支撑函数，那么有：

1. 卷积 $f*g$ 也是连续的紧支撑函数。
2. 交换性：$f*g=g*f$
3. 线性性：$f*(g+h)=f*g+f*h,c(f*g)=(cf)*g=f*(cg)$

**证明**

(1). 设 $f,g$ 分别支撑在 $[a,b],[c,d]$ 上，那么当 $x>b+d$ 时，对任意 $y \in[a,b]$，都有 $x-y>d$，从而 $f(y)g(x-y)=0$. 当 $x<a+c$ 时，对任意 $y \in[a,b]$，都有 $x-y<c$，从而 $f(y)g(x-y)=0$. 因此，卷积

$$
f*g(x)=\int_{\mathbb{R}}f(y)g(x-y)\mathrm{d} y=\int_{a}^{b} f(y)g(x-y)\mathrm{d} y
$$

支撑在 $[a+c,b+d]$ 上。

由于 $f,g$ 是紧致集上的连续函数，故 $f,g$ 有界且一致连续，从而存在 $M>0$ 使得 $|f(x)|\leq M$，并且对任意 $\varepsilon>0$，存在 $\delta>0$ 使得对任意 $|x'-x''|<\delta$ 的 $x',x''$ 有 $|g(x')-g(x'')|<\varepsilon$.

设 $x_{0}\in \mathbb{R}$，令 $|x-x_{0}|<\delta$，则有

$$
\begin{align}
|f*g(x)-f*g(x_{0})| &= \left| \int_{a}^{b}f(y)(g(x-y)-g(x_{0}-y))\mathrm{d} y \right| \\
& \leq M \int_{a}^{b} |g(x-y)-g(x_{0}-y)|\mathrm{d} y \\
& < M\varepsilon(b-a)
\end{align}
$$

故 $f*g$ 在 $x_{0}$ 处连续。

(2). 我们有

$$
\begin{gather}
f*g(x)=\int_{[a,b]\cap[x-d,x-c]}f(y)g(x-y)\mathrm{d} y \\
g*f(x)=\int_{[c,d]\cap[x-b,x-a]}g(y)f(x-y)\mathrm{d} y
\end{gather}
$$

设 $y \in[a,b]\cap[x-d,x-c]$，令 $z=x-y \in[c,d]\cap[x-b,x-a]$，则根据积分换元公式 13.2.11 有

$$
\begin{align}
g*f(x) &=\int_{[c,d]\cap[x-b,x-a]}g(x-z)f(z) \dfrac{\mathrm{d} z}{\mathrm{d} y} \mathrm{d} y \\
&= -\int_{[a,b]\cap[x-d,x-c]}f(z)g(x-z)(-1)\mathrm{d} z=f*g(x)
\end{align}
$$

卷积的线性性直接由 Riemann 积分的线性性给出。

卷积还有一些其它性质，例如卷积具有结合性、卷积与导数可交换、以及 $f*\delta=\delta*f=f$ 等，它在调和分析、偏微分方程、物理学、以及信号处理理论中有重要作用。