我们已经看到有一大类函数都是 Riemann 可积的，然而，仍然有一些函数不是 Riemann 可积的，就比如著名的 Dirichlet 函数

$$
D(x)=\begin{cases}
1 &, x \in \mathbb{Q} \\
0 &, x \not\in \mathbb{Q}
\end{cases}
$$

它在 $[0,1]$ 上就是不可积的。这是因为 $\mathbb{Q}$ 在 $\mathbb{R}$ 中是稠密的，从而在任意小的区间 $[a,b]$ 内总是存在无穷多的有理数和无理数，从而有 $U(f,\mathbf{P})=1$ 而 $L(f,\mathbf{P})=0$，上下积分不相等。

有一些方法可以对 Riemann 积分进行改进，一种方法就是之前提到的 Lebesgue 积分，另一种方法就是我们即将介绍的 Riemann-Stieltjes 积分。

# Section 1: Riemann-Stieltjes 积分

设 $\alpha$ 是一个单调递增的函数，函数 $f\colon I\to \mathbb{R}$ 定义在有界区间 $I$ 上，那么存在 Riemann 积分的一个推广，这种积分和 Riemann 积分的定义是一样的，除了一点：我们不取区间 $J$ 的长度，而是取区间的 $\alpha$-长度，定义如下：

**定义 13.1.1** $\alpha$-长度

设 $I\subset X\subset \mathbb{R}$ 是有界区间，函数 $\alpha\colon X\to \mathbb{R}$，定义 $I$ 的 $\alpha$**-长度** $|I|_{\alpha}$ 如下：如果 $I$ 是空集或单点集，定义 $|I|_{\alpha}=0$；如果 $I$ 是非退化的区间，端点为 $a<b$，那么定义 $|I|_{\alpha}=\alpha(b)-\alpha(a)$.

我们可以注意到：当 $\alpha$ 是恒等函数 $\alpha(x)=x$ 时，区间的 $\alpha$-长度就是普通的区间长度 $|I|$，因此，$\alpha$-长度是区间长度的一种推广。

与区间的长度一样，$\alpha$-长度也具有有限可加性。

**定理 13.1.2**

设 $I\subset X\subset \mathbb{R}$ 是有界区间，函数 $\alpha\colon X\to \mathbb{R}$，并且 $\mathbf{P}$ 是 $I$ 的一个划分，那么有

$$
|I|_{\alpha}=\sum_{J \in \mathbf{P}} |J|_{\alpha}
$$

**证明**

逐字逐句重复定理 12.1.5 的证明，然后把长度 $|I|$ 换成 $\alpha$-长度 $|I|_{\alpha}$ 即可。

现在我们来定义分段常值函数的 Riemann-Steltjes 积分。

**定义 13.1.3** 分段常值 Riemann-Steltjes 积分

设 $I\subset X\subset \mathbb{R}$ 是有界区间，函数 $\alpha\colon X\to \mathbb{R}$，并且 $\mathbf{P}$ 是 $I$ 的一个划分，函数 $f\colon I\to \mathbb{R}$ 是关于 $\mathbf{P}$ 的分段常值函数，那么我们定义

$$
\int_{\mathbf{P}}f\mathrm{d} \alpha=\sum_{J \in \mathbf{P}} c_{J} |J|_{\alpha}
$$

其中 $c_{J}$ 是 $f$ 在 $J$ 上的常数值。

就像定理 12.2.4 一样，在 Riemann-Steltjes 积分中也有其对应的定理（作为 $\alpha$-长度有限可加性的一个推论），从而我们可以定义

$$
\int_{I} f\mathrm{d} \alpha=\int_{\mathbf{P}}f\mathrm{d} \alpha
$$

其中 $f$ 关于 $\mathbf{P}$ 是分段常值函数。

当 $\alpha(x)=x$ 时，上述定义就退化为一般的 Riemann 积分，因此有时候我们会把 Riemann 积分写成 $\int_{I}f\mathrm{d}x$.

到目前为止，函数 $\alpha$ 都是任意的，现在我们要求 $\alpha$ 是单调递增函数，那么我们可以证明，如果把定理 12.2.6 中的 Riemann 积分都替换为 Riemann-Steltjes 积分，其对应的定理仍然成立。

**定理 13.1.4**

设 $I\subset X\subset \mathbb{R}$ 是有界区间，函数 $\alpha\colon X\to \mathbb{R}$ 单调递增，函数 $f\colon I\to \mathbb{R},g\colon I\to \mathbb{R}$ 是分段常值函数，则有：

1. 线性性：$\int_{I}(af+bg)\mathrm{d}\alpha=a \int_{I}f\mathrm{d}\alpha+b \int_{I}g\mathrm{d}\alpha$
2. 比较准则：如果对任意 $x \in I$ 有 $f(x)\leq g(x)$，那么 $\int_{I}f\mathrm{d}\alpha\leq \int_{I}g\mathrm{d}\alpha$
3. 设 $I\subset J$，函数 $F\colon J\to \mathbb{R}$ 定义为 $$
F(x)=\begin{cases}
f(x) &, x \in I \\
0 &, x \not\in I
\end{cases}
$$ 则 $F$ 是分段常值函数，并且 $\int_{J}F\mathrm{d}\alpha=\int_{I}f\mathrm{d}\alpha$
4. 设 $\{ J,K \}$ 是 $I$ 的划分，那么 $f|_{J}$ 和 $f|_{K}$ 都是分段常值函数，并且 $\int_{I}f\mathrm{d}\alpha=\int_{J}f|_{J}\mathrm{d}\alpha+\int_{K}f|_{K}\mathrm{d}\alpha$

**证明**

由于 $\alpha$ 是单调递增的，故对任意有界区间 $J$ 有 $|J|_{\alpha}\geq 0$，由此，再逐字逐句重复定理 12.2.6 的证明，并将 $|J|$ 换成 $|J|_{\alpha}$ 即可。

于是我们就可以直接按照 Riemann 积分的定义来给出 Riemann-Stieltjes 积分的定义。

**定义 13.1.5** Riemann-Stieltjes 积分

设 $I\subset X\subset \mathbb{R}$ 是有界区间，函数 $\alpha\colon X\to \mathbb{R}$，函数 $f\colon I\to \mathbb{R}$ 是有界函数，那么定义**上 Riemann-Stieltjes 积分**为

$$
\overline{\int_{I}}f\mathrm{d} \alpha=\inf \left\{  \int_{I}g\mathrm{d} \alpha \middle| g \text{是从上方控制} f \text{的分段常值函数}  \right\}
$$

定义**下 Riemann-Stieltjes 积分**为

$$
\underline{\int_{I}}f\mathrm{d} \alpha=\sup \left\{  \int_{I}g\mathrm{d} \alpha \middle| g \text{是从下方控制} f \text{的分段常值函数}  \right\}
$$

如果 $\overline{\int_{I}}f\mathrm{d}\alpha=\underline{\int_{I}}f\mathrm{d}\alpha$，则称 $f$ 在 $I$ 上关于 $\alpha$ 是 **Riemann-Stieltjes 可积**的，并且定义

$$
\int_{I}f\mathrm{d} \alpha=\overline{\int_{I}}f\mathrm{d} \alpha=\underline{\int_{I}}f\mathrm{d} \alpha
$$

根据定理 13.1.4，剩下的绝大部分 Riemann 积分的理论都可以轻松地推广到 Riemann-Stieltjes 积分中去，只需保证 $\alpha$ 是单调递增的，并且将长度替换为 $\alpha$-长度即可。但是，有一些定理不再成立，特别是当 $\alpha$ 在一些关键的位置间断的时候，比如定理 12.4.1 的 3，定理 12.4.6，以及定理 12.4.8，不过，定理 12.4.4 仍然成立。

**定理 13.1.6**

设 $I\subset X\subset \mathbb{R}$ 是有界区间，函数 $\alpha\colon X\to \mathbb{R}$ 单调递增，函数 $f\colon I\to \mathbb{R}$ 一致连续，那么 $f$ 关于 $\alpha$ 是 Riemann-Stieltjes 可积的。

**证明**

由于一致连续函数将有界集映射到有界集，故 $f$ 是有界函数。如果 $I$ 是空集或者单点集，那么定理自动成立，现在设 $I$ 是非退化的区间，其端点是 $a<b$.

对任意 $\varepsilon>0$，存在 $\delta>0$ 使得对任意 $d(x',x'')<\delta$ 的 $x',x''\in I$ 有 $d(f(x'),f(x''))<\varepsilon$. 取正整数 $N$ 使得 $\dfrac{b-a}{N}<\delta$，将 $I$ 按长度均分为 $N$ 份 $J_{1},\dots,J_{N}$，则在每个 $J_{k}$ 上有 $d(x',x'')<\delta$，从而有

$$
\overline{\int_{I}}f\mathrm{d} \alpha-\underline{\int_{I}}f\mathrm{d} \alpha\leq \sum_{k=1}^{N} (\sup_{x \in J_{k}}f(x)-\inf_{x \in J_{k}}f(x))|J_{k}|_{\alpha}\leq \varepsilon (\alpha(b)-\alpha(a))
$$

因此 $f$ 关于 $\alpha$ 是 Riemann-Stieltjes 可积的。

# Section 2: 微积分基本定理

现在我们已经有了足够的工具来将微分学与积分学联系起来，这就是微积分基本定理的主要内容。事实上，有两个基本定理，一个涉及积分的导数，另一个涉及导数的积分。

**定理 13.2.1** 微积分基本定理 I

设实数 $a<b$，函数 $f\colon [a,b]\to \mathbb{R}$ 是 Riemann 可积的，并且设函数 $F\colon [a,b]\to \mathbb{R}$ 定义为

$$
F(x)=\int_{a}^{x} f
$$

那么 $F$ 是连续函数，并且如果 $f$ 在 $x_{0}\in[a,b]$ 处连续，那么 $F$ 在 $x_{0}$ 处可微，且 $F'(x_{0})=f(x_{0})$.

**证明**

由于 $f$ 是 Riemann 可积的，故它是有界的，故存在实数 $M>0$ 使得 $|f(x)|\leq M$. 现设 $a\leq x<y\leq b$，则

$$
|F(y)-F(x)|=\left| \int_{x}^{y}f \right| \leq \int_{x}^{y} |f|\leq M|y-x|
$$

当 $y\leq x$ 时也有同样的结果。设 $x \in[a,b]$，取 $[a,b]$ 中收敛于 $x$ 的序列 $(x_{n})$，则对任意 $n$ 有 $-M|x_{n}-x|\leq F(x_{n})-F(x)\leq M|x_{n}-x|$，对 $n\to \infty$ 取极限，则有 $\lim_{ n \to \infty }F(x_{n})=F(x)$，因此 $F$ 在 $x$ 处连续，由于 $x$ 是任意的，故 $F$ 在 $[a,b]$ 上连续。

现设 $x_{0}\in[a,b]$，$f$ 在 $x_{0}$ 处连续，故对任意 $\varepsilon>0$，存在 $\delta>0$ 使得对任意 $d(x,x_{0})<\delta$ 的 $x \in[a,b]$ 有 $d(f(x),f(x_{0}))<\varepsilon$，现在我们要证对任意 $x \in (x_{0}-\delta,x_{0}+\delta)\cap[a,b]$ 有

$$
|F(x)-F(x_{0})-f(x_{0})(x-x_{0})|\leq \varepsilon|x-x_{0}|
$$

如果 $x=x_{0}$，那么结论显然成立。设 $x>x_{0}$，则我们有

$$
(f(x_{0})-\varepsilon)(x-x_{0})< F(x)-F(x_{0})=\int_{x_{0}}^{x}f < (f(x_{0})+\varepsilon)(x-x_{0})
$$

即证。对于 $x<x_{0}$ 的情况，其证明是类似的。

上述定理表明，如果 $f\colon [a,b]\to \mathbb{R}$ 是连续的，那么在 $[a,b]$ 上就有

$$
\left( \int_{a}^{x} f \right)'=f
$$

即积分的导数是函数自身。下面我们证明相反的命题，即导数的积分是函数自身。

**定义 13.2.2** 原函数（antiderivative）

设 $I$ 是一个有界区间，函数 $f\colon I\to \mathbb{R}$，如果函数 $F\colon I\to \mathbb{R}$ 在 $I$ 上可微，并且对任意 $x \in I$ 有 $F'(x)=f(x)$，那么称 $F$ 是 $f$ 的一个**原函数**。

定理 11.2.10 表明，函数 $f$ 的两个原函数之间存在关系 $F(x)=G(x)+C$，已知一个函数 $f$，求其原函数的过程称为**不定积分**。

**定理 13.2.3** 微积分基本定理 II，Newton-Leibniz 公式

设实数 $a<b$，函数 $f\colon [a,b]\to \mathbb{R}$ 是 Riemann 可积的，如果 $F\colon [a,b]\to \mathbb{R}$ 是 $f$ 的一个原函数，那么

$$
\int_{a}^{b}f=F(b)-F(a)
$$

**证明**

证明的思路是要证对 $I$ 的每个划分 $\mathbf{P}$，都有

$$
L(f,\mathbf{P})\leq F(b)-F(a)\leq U(f,\mathbf{P})
$$

对两边分别取下确界或上确界就有

$$
\underline{\int_{I}}f\leq F(b)-F(a)\leq \overline{\int_{I}}f
$$

由于 $f$ 是 Riemann 可积的，故上下积分相等，就得到了想要的结论。

设 $\mathbf{P}$ 是 $I$ 的一个划分，任取 $J \in \mathbf{P}$，根据 $F$-长度的有限可加性有

$$
F(b)-F(a)=|I|_{F}=\sum_{J \in \mathbf{P}\setminus \{ \varnothing \}} |J|_{F}
$$

根据 Riemann 和的定义，我们就只需证明

$$
(\inf_{x \in J}f(x))|J|\leq |J|_{F}\leq(\sup_{x \in J}f(x))|J|
$$

当 $J$ 是单点集时，结论显然成立，现设 $J$ 是非退化的区间，端点为 $c<d$，则 $|J|_{F}=F(d)-F(c)$，根据 Lagrange 中值定理，我们有

$$
F(d)-F(c)=F'(\xi)(d-c)=f(\xi)|J|,c<\xi<d
$$

又 $\inf_{x \in J}f(x)\leq f(\xi)\leq \sup_{x \in J}f(x)$，这就完成了证明。

微积分基本定理 I 保证了连续函数总有原函数，一旦得到了 $f$ 的原函数（通常是通过求 $f$ 的不定积分得到），我们就可以通过 Newton-Leibniz 公式求出 $f$ 的定积分。然而，对于不连续的函数，情况就变得复杂了，这正是实分析的后续理论要解决的问题。

现在我们给出微积分基本定理的一些推论，首先是著名的分部积分法。

**定理 13.2.4** 分部积分法（integration by parts）

设实数 $a<b$，函数 $f\colon [a,b]\to \mathbb{R},g\colon [a,b]\to \mathbb{R}$ 在 $[a,b]$ 上可微，并且 $f'$ 和 $g'$ 在 $[a,b]$ 上 Riemann 可积，那么有

$$
\int_{a}^{b} fg'=f(b)g(b)-f(a)g(a)-\int_{a}^{b}f'g
$$

**证明**

由于 $f,g$ 在 $[a,b]$ 上可微，故连续，从而 $f,g$ 在 $[a,b]$ 上 Riemann 可积，因此 $fg'$ 和 $f'g$ 在 $[a,b]$ 上可积，从而 $fg'+f'g=(fg)'$ 可积，根据 Newton-Leibniz 公式即得

$$
\int_{a}^{b}fg'+\int_{a}^{b}f'g=f(b)g(b)-f(a)g(a)
$$

下面我们证明在某些情况下，我们可以将一个 Riemann-Stieltjes 积分写成一个 Riemann 积分。我们首先对分段常值函数做证明。

**引理 13.2.5**

设实数 $a<b$，函数 $\alpha\colon [a,b]\to \mathbb{R}$ 在 $[a,b]$ 上单调递增且可微，并且 $\alpha'$ 是 Riemann 可积的，函数 $f\colon [a,b]\to \mathbb{R}$ 是分段常值函数，那么 $f\alpha'$ 在 $[a,b]$ 上 Riemann 可积，并且

$$
\int_{a}^{b} f\mathrm{d} \alpha=\int_{a}^{b} f\alpha'
$$

**证明**

$f$ 是分段常值函数，故 Riemann 可积，从而 $f\alpha'$ 是 Riemann 可积的。设 $f$ 关于 $I$ 的划分 $\mathbf{P}$ 是分段常值函数，那么有

$$
\int_{a}^{b}f\mathrm{d} \alpha=\sum_{J \in \mathbf{P}\setminus \{ \varnothing \}}c_{J}|J|_{\alpha}
$$

并且

$$
\int_{a}^{b}f\alpha'=\sum_{J \in \mathbf{P}\setminus \{ \varnothing \}}\int_{J}f\alpha'=\sum_{J \in \mathbf{P}\setminus \{ \varnothing \}}c_{J} \int_{J}\alpha'
$$

由 Newton-Leibniz 公式知 $\int_{J}\alpha'=|J|_{\alpha}$，即证。

现在我们将其推广至 Riemann-Stieltjes 可积函数。

**定理 13.2.6**

设实数 $a<b$，函数 $\alpha\colon [a,b]\to \mathbb{R}$ 在 $[a,b]$ 上单调递增且可微，并且 $\alpha'$ 是 Riemann 可积的，函数 $f\colon [a,b]\to \mathbb{R}$ 关于 $\alpha$ Riemann-Stieltjes 可积，那么 $f\alpha'$ 是 Riemann 可积的，并且

$$
\int_{a}^{b} f\mathrm{d} \alpha=\int_{a}^{b} f\alpha'
$$

**证明**

由于 $f$ 和 $\alpha$ 是有界的，故 $f\alpha'$ 是有界的，由于 $\alpha$ 单调递增，故 $\alpha'(x)\geq 0$.

任取 $\varepsilon>0$，则有从上方控制 $f$ 的分段常值函数 $\overline{f}$ 和从下方控制 $f$ 的分段常值函数 $\underline{f}$ 使得

$$
\int_{a}^{b}f\mathrm{d} \alpha-\varepsilon< \int_{a}^{b}\underline{f}\mathrm{d} \alpha\leq \int_{a}^{b}\overline{f}\mathrm{d} \alpha< \int_{a}^{b}f\mathrm{d} \alpha+\varepsilon
$$

根据引理，我们有 $\int_{a}^{b}\overline{f}\mathrm{d}\alpha=\int_{a}^{b}\overline{f}\alpha'$ 以及 $\int_{a}^{b}\underline{f}\mathrm{d}\alpha=\int_{a}^{b}\underline{f}\alpha'$.

由于 $\alpha'$ 非负且 $\overline{f}$ 从上方控制 $f$，故 $\overline{f}\alpha'$ 从上方控制 $f\alpha'$，于是

$$
\overline{\int_{a}^{b}}f\alpha'\leq \int_{a}^{b} \overline{f}\alpha'< \int_{a}^{b}f\mathrm{d} \alpha+\varepsilon
$$

同理 $\underline{\int_{a}^{b}}f\alpha'>\int_{a}^{b}f\mathrm{d}\alpha-\varepsilon$，从而

$$
\int_{a}^{b}f\mathrm{d} \alpha\leq \underline{\int_{a}^{b}}f\alpha'\leq \overline{\int_{a}^{b}}f\alpha'\leq \int_{a}^{b}f\mathrm{d} \alpha
$$

这就完成了证明。

通俗地说，上述定理表明，当 $\alpha$ 可微时，$f\mathrm{d}\alpha$ 与 $f \dfrac{\mathrm{d}\alpha}{\mathrm{d}x}\mathrm{d}x$ 是等价的，这也是人们常说的“一阶微分的形式不变性”的来源。而 Riemann-Stieltjes 积分的优点是，即使 $\alpha$ 不可微，积分 $\int_{I}f\mathrm{d}\alpha$ 仍然可以有意义。

下面我们要证明积分的换元法，首先还是对分段常值函数进行证明。

**引理 13.2.7**

设实数 $a<b$，函数 $\phi\colon [a,b]\to[\phi(a),\phi(b)]$ 单调递增且连续，函数 $f\colon [\phi(a),\phi(b)]\to \mathbb{R}$ 是分段常值函数，那么 $f\circ \phi$ 是 $[a,b]$ 上的分段常值函数，并且

$$
\int_{a}^{b}f\circ \phi \mathrm{d} \phi=\int_{\phi(a)}^{\phi(b)}f
$$

**证明**

设 $f$ 关于 $[\phi(a),\phi(b)]$ 的划分 $\mathbf{P}$ 是分段常值函数，则

$$
\int_{\phi(a)}^{\phi(b)}f=\sum_{J \in \mathbf{P}\setminus \{ \varnothing \}}c_{J}|J|
$$

设 $J \in \mathbf{P}\setminus\{ \varnothing \}$，考虑原像集 $\phi^{-1}[J]$，设 $x,y \in \phi^{-1}[J],x<z<y$，则 $\phi(x)\leq \phi(z)\leq \phi(y)$，由于 $\phi(x),\phi(y)\in J$，而 $J$ 是一个区间，故 $\phi(z)\in J$，即 $z \in \phi^{-1}[J]$，从而 $\phi^{-1}[J]$ 是连通的，因而是一个区间。此外，$c_{J}$ 是函数 $f\circ \phi$ 在 $\phi^{-1}[J]$ 上的常数值。

令 $\mathbf{P}'=\{ \phi^{-1}[J] \mid J \in \mathbf{P}\setminus \{ \varnothing \} \}$，设 $J\neq K$，则 $J\cap K=\varnothing$，由于 $\phi^{-1}[J\cup K]=\phi^{-1}[J]\cup \phi^{-1}[K]$，并且 $\phi^{-1}[J\cap K]=\phi^{-1}[J]\cap \phi^{-1}[K]$，故 $\mathbf{P}'$ 是 $[a,b]$ 的一个划分，并且 $f\circ \phi$ 关于 $\mathbf{P}'$ 是分段常值函数，从而

$$
\int_{a}^{b}f\circ \phi \mathrm{d} \phi=\sum_{J \in \mathbf{P}\setminus \{ \varnothing \}}c_{J}|\phi^{-1}[J]|_{\phi}=\sum_{J \in \mathbf{P}\setminus \{ \varnothing \}}c_{J}|J|=\int_{\phi(a)}^{\phi(b)}f
$$

**定理 13.2.8** 积分换元法（substitution formula）

设实数 $a<b$，函数 $\phi\colon [a,b]\to[\phi(a),\phi(b)]$ 单调递增且连续，函数 $f\colon [\phi(a),\phi(b)]\to \mathbb{R}$ 是 Riemann 可积的，那么 $f\circ \phi$ 在 $[a,b]$ 上关于 $\phi$ Riemann-Stieltjes 可积，并且

$$
\int_{a}^{b}f\circ \phi \mathrm{d} \phi=\int_{\phi(a)}^{\phi(b)}f
$$

**证明**

由于 $f$ 有界，故 $f\circ \phi$ 也是有界的。任取 $\varepsilon>0$，那么存在从上方控制 $f$ 的分段常值函数 $\overline{f}$ 和从下方控制 $f$ 的分段常值函数 $\underline{f}$ 使得

$$
\int_{\phi(a)}^{\phi(b)}f-\varepsilon<\int_{\phi(a)}^{\phi(b)}\underline{f}\leq \int_{\phi(a)}^{\phi(b)}\overline{f}<\int_{\phi(a)}^{\phi(b)}f+\varepsilon
$$

根据引理，我们有 $\int_{\phi(a)}^{\phi(b)}\overline{f}=\int_{a}^{b}\overline{f}\circ \phi \mathrm{d}\phi$ 以及 $\int_{\phi(a)}^{\phi(b)}\underline{f}=\int_{a}^{b}\underline{f}\circ \phi \mathrm{d}\phi$.

由于 $\overline{f}$ 从上方控制 $f$，故 $\overline{f}\circ \phi$ 从上方控制 $f\circ \phi$，从而

$$
\overline{\int_{a}^{b}}f\circ \phi \mathrm{d} \phi\leq \int_{a}^{b}\overline{f}\circ \phi \mathrm{d} \phi<\int_{\phi(a)}^{\phi(b)}f+\varepsilon
$$

同理 $\underline{\int_{a}^{b}}f\circ \phi \mathrm{d} \phi>\int_{\phi(a)}^{\phi(b)}f-\varepsilon$，从而有

$$
\int_{\phi(a)}^{\phi(b)}f\leq \underline{\int_{a}^{b}}f\circ \phi \mathrm{d} \phi\leq \overline{\int_{a}^{b}}f\circ \phi \mathrm{d} \phi\leq \int_{\phi(a)}^{\phi(b)}f
$$

这就完成了证明。

把上述公式与定理 13.2.6 结合起来，就有了常用的变量替换公式。

**定理 13.2.9** 积分换元法（substitution formula）

设实数 $a<b$，函数 $\phi\colon [a,b]\to[\phi(a),\phi(b)]$ 单调递增且可微，并且 $\phi'$ 在 $[a,b]$ 上 Riemann 可积，函数 $f\colon [\phi(a),\phi(b)]\to \mathbb{R}$ 是 Riemann 可积的，那么 $(f\circ \phi)\phi'$ 在 $[a,b]$ 上 Riemann 可积，并且

$$
\int_{a}^{b}(f\circ \phi)\phi' = \int_{\phi(a)}^{\phi(b)}f
$$

最后，我们考虑一下当 $\phi$ 是单调递减函数时的换元公式，由于 $\phi$ 可以写成 $(-1)(-\phi)$，而 $-\phi$ 是单调递增的，因此我们只需考虑 $\phi(x)=-x$ 时的情况。

**引理 13.2.10**

设实数 $a<b$，函数 $f\colon [a,b]\to \mathbb{R}$ 是 Riemann 可积的，那么定义为 $g(x)=f(-x)$ 的函数 $g\colon [-b,-a]\to \mathbb{R}$ 是 Riemann 可积的，并且

$$
\int_{-b}^{-a}g=\int_{a}^{b}f
$$

**证明**

任取 $\varepsilon>0$，则有分段常值函数 $\overline{f},\underline{f}$ 分别从上方和下方控制 $f$，并且

$$
\int_{a}^{b}f-\varepsilon<\int_{a}^{b}\underline{f}\leq \int_{a}^{b}\overline{f}<\int_{a}^{b}f+\varepsilon
$$

定义 $\overline{g}(x)=\overline{f}(-x)$，则 $\overline{g}$ 从上方控制 $g$，设 $\overline{f}$ 关于 $\mathbf{P}$ 是分段常值的，考虑 $[-b,-a]$ 的划分 $\mathbf{P}'=\{ -J \mid J \in \mathbf{P} \}$，其中 $-J=\{ -x \mid x \in J \}$，则 $\overline{g}$ 关于 $\mathbf{P}'$ 是分段常值的，从而

$$
\int_{-b}^{-a}\overline{g}=\sum_{J \in \mathbf{P}}c_{J}|-J|=\sum_{J \in \mathbf{P}}c_{J}|J|=\int_{a}^{b}\overline{f}
$$

于是有

$$
\overline{\int_{-b}^{-a}}g\leq \int_{-b}^{-a}\overline{g}<\int_{a}^{b}f+\varepsilon
$$

另一边的不等式是类似的，从而

$$
\int_{a}^{b}f\leq \underline{\int_{-b}^{-a}}g\leq\overline{\int_{-b}^{-a}}g\leq\int_{a}^{b}f
$$

即证。

由此，我们可以给出 $\phi$ 单调递减时的定理 13.2.9：

**定理 13.2.11** 积分换元法（substitution formula）

设实数 $a<b$，函数 $\phi\colon [a,b]\to[\phi(b),\phi(a)]$ 单调递减且可微，并且 $\phi'$ 在 $[a,b]$ 上 Riemann 可积，函数 $f\colon [\phi(b),\phi(a)]\to \mathbb{R}$ 是 Riemann 可积的，那么 $(f\circ \phi)\phi'$ 在 $[a,b]$ 上 Riemann 可积，并且

$$
\int_{a}^{b}(f\circ \phi)\phi' = -\int_{\phi(b)}^{\phi(a)}f
$$

**证明**

定义函数 $\psi=-\phi$，则 $\psi\colon [a,b]\to[-\phi(a),-\phi(b)]$ 单调递增，并且根据引理，定义为 $g(x)=f(-x)$ 的函数 $g$ 在 $[-\phi(a),-\phi(b)]$ 上可积，于是有

$$
-\int_{a}^{b}(f\circ \phi)\phi'=\int_{a}^{b}(g\circ \psi)\psi'=\int_{-\phi(a)}^{-\phi(b)}g=\int_{\phi(b)}^{\phi(a)}f
$$

这就完成了证明。