在前面的章节中我们主要研究了区域上的解析函数。本章，我们来研究除了某些孤立点外在区域上解析的函数，这些函数失去解析性的点被称为**奇点**。通过分析函数在奇点附近的行为，我们可以得到若干有用的结论。特别地，它们能够帮助我们计算一些无法通过简单微积分手段完成的实积分。

# Section 1: 奇点的分类

我们从奇点中性质最好的一类——可去奇点开始。

**定义 4.1.1** 孤立奇点（isolated singularity），可去奇点（removable singularity）

称函数 $f$ 在 $a$ 处有一个**孤立奇点**，如果有 $R>0$ 使得 $f$ 在 $B(a,R)\setminus\{ a \}$ 上解析，但不在 $B(a,R)$ 上解析。点 $a$ 称为是一个**可去奇点**，如果存在解析函数 $g\colon B(a,R)\to \mathbb{C}$ 使得在 $B(a,R)\setminus\{ a \}$ 上有 $g(z)=f(z)$.

例如，函数 $\dfrac{\sin z}{z},\dfrac{1}{z},\exp \dfrac{1}{z}$ 均在 $z=0$ 处有一个孤立奇点，但仅有 $\dfrac{\sin z}{z}$ 的奇点是可去的。事实上，当 $z\to 0$ 时，$\left\lvert  \dfrac{1}{z}  \right\rvert$ 和 $\left\lvert  \exp \dfrac{1}{z}  \right\rvert$ 的极限均不是有限的，因此，这些函数的任意扩张在 $z=0$ 处都不连续。

于是，我们可以给出函数在一点处有可去奇点的条件：至少 $\lim_{ z \to a }f(z)$ 必须存在且有限。不过，事实上存在一个更弱的条件：

**定理 4.1.2**

设 $f$ 在 $a$ 处有一个孤立奇点，则 $a$ 是可去的当且仅当

$$
\begin{gather}
\lim_{ z \to a } (z-a)f(z)=0
\end{gather}
$$

**证明**

必要性是显然的：如果 $a$ 是可去的，令 $g$ 为 $f$ 的解析扩张，则有

$$
\begin{gather}
\lim_{ z \to a } (z-a)f(z)=\lim_{ z \to a } (z-a)g(z)=0\cdot g(a)=0
\end{gather}
$$

下证充分性。设 $f$ 在 $B(a,R)\setminus\{ a \}$ 上解析，令 $g(z)=(z-a)f(z),z\neq a$ 且 $g(a)=0$. 由于 $\lim_{ z \to a }(z-a)f(z)=0$，故 $g$ 是连续函数。如果我们可以证明 $g$ 是解析函数，那么由于 $g(a)=0$，存在解析函数 $h\colon B(a,R)\to \mathbb{C}$ 使得 $g(z)=(z-a)h(z)$，从而 $f(z)=h(z)$ 对 $z\neq a$ 成立，即证 $a$ 是可去奇点。

为证 $g$ 的解析性，我们使用 Morera 定理。设 $T$ 是 $B(a,R)$ 中的一条三角路径，令 $\Delta$ 为 $T$ 和其内部构成的闭三角形。如果 $a \not\in\Delta$，那么在 $B(a,R)\setminus\{ a \}$ 中有 $T\sim 0$，从而由 Cauchy 定理得 $\int_{T}g=0$.

![](4-1.png)

如果 $a$ 是 $T$ 的一个顶点，设 $T=[a,b,c,a]$，令 $x \in[a,b],y \in[a,c]$，并记 $T_{1}=[a,x,y,a]$，以及 $P=[x,b,c,y,x]$，由于在 $B(a,R)\setminus\{ a \}$ 中有 $P \sim 0$，故

$$
\begin{gather}
\int_{T} g=\int_{T_{1}}g+\int_{P} g=\int_{T_{1}} g
\end{gather}
$$

由于 $g$ 连续且 $g(a)=0$，故对任意 $\varepsilon>0$，我们可以选取 $x,y$ 使得 $|g(z)|<\varepsilon /\ell$ 对任意 $z \in \{ T_{1} \}$ 成立，其中 $\ell$ 是 $T$ 的长度. 于是我们有 $\left\lvert  \int_{T}g  \right\rvert=\left\lvert  \int_{T_{1}} g  \right\rvert<\varepsilon$，即得 $\int_{T}g=0$.

![](4-2.png)

如果 $a \in \mathrm{Int}\,\Delta$ 且 $T=[x,y,z,x]$，我们考虑三角形 $T_{1}=[x,a,z,x]$，$T_{2}=[x,y,a,x]$，$T_{3}=[y,z,a,y]$，则根据上文有 $\int_{T_{j}}g=0$，从而

$$
\begin{gather}
\int_{T}g=\sum_{j=1}^{3} \int_{T_{j}} g=0
\end{gather}
$$

最后剩下的只有 $a$ 位于 $T$ 的边上的情况。这实际上是 $a$ 位于内部的情况的一种退化版本：我们只需连接 $a$ 与 $a$ 所在边的对角顶点，将 $T$ 分成两个以 $a$ 为顶点的三角形即可。这就完成了证明。

上述定理显示了复函数与实函数的又一明显的区别：在实数中，我们有像 $f(x)=|x|$ 这样在 $x=0$ 处连续但不可微的函数，因为它在 $x=0$ 处有类似“尖角”的行为。然而，这种情形在复数中不可能发生。为使复函数在一点处拥有确实的奇点（即不可去的奇点），函数就必须在该点附近拥有相当程度的奇异行为。那也就是说，或者 $|f(z)|$ 在 $z\to a$ 时趋于无穷，并且速度至少与 $(z-a)^{-1}$ 相当，或者 $|f(z)|$ 在 $z\to a$ 时的极限完全不存在（注意，极限为无穷也被视为存在）。

**定义 4.1.3** 极点（pole），本性奇点（essential singularity）

如果 $f$ 在 $a$ 处有一个孤立奇点，则 $a$ 是一个**极点**如果 $\lim_{ z \to a }|f(z)|=\infty$. 如果 $a$ 既不是可去奇点也不是极点，则称它是一个**本性奇点**。

容易证明，对于 $m\geq 1$，函数 $(z-a)^{-m}$ 在 $a$ 处有一个极点。此外，函数 $\exp \dfrac{1}{z}$ 在 $z\to 0$ 时模长的极限不存在，因此它在 $0$ 处有一个本性奇点。

假设 $f$ 在 $a$ 处有一个极点，则根据定理 4.1.2 可知 $f(z)^{-1}$ 在 $a$ 处有一个可去奇点。因此，定义为 $h(z)=f(z)^{-1},z\neq a$ 且 $h(a)=0$ 的函数 $h$ 在 $B(a,R)$ 上解析。于是存在解析函数 $h_{1}$ 使得 $h(z)=(z-a)^{m}h_{1}(z)$，其中 $h_{1}(a)\neq 0,m\geq 1$. 这表明 $h_{1}(z)^{-1}=(z-a)^{m}f(z)$ 在 $a$ 处有一个可去奇点。这样就证明了以下定理：

**定理 4.1.4**

设 $G$ 是一个区域，$a \in G$，如果 $f$ 在 $G\setminus\{ a \}$ 上解析，且在 $a$ 处有一个极点，那么存在整数 $m\geq 1$ 和解析函数 $g\colon G\to \mathbb{C}$ 使得

$$
\begin{gather}
f(z)=\dfrac{g(z)}{(z-a)^{m}}
\end{gather}
$$

**定义 4.1.5**

如果 $f$ 在 $a$ 处有一个极点，$m$ 是使得 $f(z)(z-a)^{m}$ 在 $a$ 处有可去奇点的最小整数，则称 $f$ 在 $a$ 处有一个 $m$ **阶极点**。

注意到，如果 $f$ 在 $a$ 处有 $m$ 阶极点，并且有 $f(z)=g(z)(z-a)^{-m}$ 成立，那么 $g(a)\neq 0$. 此外，由于 $g$ 在 $B(a,R)$ 上解析，因此它有幂级数展开

$$
\begin{gather}
g(z)=A_{m}+A_{m-1}(z-a)+\dots+A_{1}(z-a)^{m-1}+(z-a)^{m} \sum_{k=0}^{\infty} a_{k}(z-a)^{k}
\end{gather}
$$

于是

$$
\begin{gather}
f(z)=\dfrac{A_{m}}{(z-a)^{m}}+\dots+\dfrac{A_{1}}{z-a}+g_{1}(z)
\end{gather}
$$

其中 $g_{1}$ 在 $B(a,R)$ 上解析，且 $A_{m}\neq 0$.

**定义 4.1.6** 奇异部分（singular part）

如果 $f$ 在 $a$ 处有一个 $m$ 阶极点，则我们称 $\dfrac{A_{m}}{(z-a)^{m}}+\dots+\dfrac{A_{1}}{z-a}$ 为 $f$ 在 $a$ 处的**奇异部分**。

作为一个简单例子，我们考虑有理函数 $r(z)=p(z) /q(z)$，其中 $p,q$ 是没有共同因子的多项式。换句话说，$p$ 和 $q$ 没有相同的零点。于是，$r$ 的极点就是 $q(z)$ 的零点，且极点的阶数等于其对应的零点的重数。假设 $q(a)=0$，并令 $S(z)$ 为 $r(z)$ 在 $a$ 处的奇异部分，则 $r(z)-S(z)=r_{1}(z)$ 是一个与 $r(z)$ 有相同极点的有理函数（除了 $z=a$）。此外，不难看出 $r_{1}(z)$ 在其他任意极点处的奇异部分与 $r(z)$ 在该处的奇异部分相同。使用归纳法我们可得：如果 $a_{1},\dots,a_{n}$ 是 $r(z)$ 的极点，并且 $S_{j}(z)$ 是 $r$ 在 $a_{j}$ 处的奇异部分，则

$$
\begin{gather}
r(z)=\sum_{j=1}^{n} S_{j}(z)+P(z)
\end{gather}
$$

其中 $P(z)$ 是一个没有极点的有理函数，也就是说，一个多项式。因此，以上的过程不过只是有理函数的部分分式分解而已。

类似上式的部分分式展开仅对有理函数有效吗？如果我们限定 $P(z)$ 为多项式，那么它当然是的。但如果我们允许 $P(z)$ 为任意区域 $G$ 上的解析函数，则上式对除了有限个极点外在 $G$ 上解析的函数 $r(z)$ 成立。进一步，如果 $f$ 有无穷多个极点，比如 $f(z)=(\cos z)^{-1}$，那么我们可以将上式中的有限和改成无限和，而仍保持等式吗？答案是肯定的，这一结论称为 **Mittag-Leffler 定理**。

对于本性奇点，它也有一个类似的奇异部分。然而，与极点不同，本性奇点处的奇异部分是向左无限延申的（如若不然，那么它就是一个极点而非本性奇点）。因此，我们将会遇到形如 $\sum_{n=-\infty}^{\infty}z_{n}$ 的双边级数，这类级数的收敛性定义在下面给出：

**定义 4.1.7** 绝对收敛（absolute convergence），一致收敛（uniform convergence）

设 $\{ z_{n} \mid n=0,\pm 1,\pm 2,\dots \}$ 是一列复数，则级数 $\sum_{n=-\infty}^{\infty}z_{n}$ **绝对收敛**如果级数 $\sum_{n=0}^{\infty}z_{n}$ 和 $\sum_{n=1}^{\infty}z_{-n}$ 绝对收敛，此时定义

$$
\begin{gather}
\sum_{n=-\infty}^{\infty}z_{n}=\sum_{n=0}^{\infty}z_{n}+\sum_{n=1}^{\infty}z_{-n}
\end{gather}
$$

设 $\{ u_{n}(s) \mid n=0,\pm 1,\pm 2,\dots \}$ 是 $S$ 上的一列复值函数，且对任意 $s \in S$ 有 $\sum_{n=-\infty}^{\infty}u_{n}(s)$ 绝对收敛，则级数 $\sum_{n=-\infty}^{\infty}u_{n}$ 在 $S$ 上**一致收敛**如果级数 $\sum_{n=0}^{\infty}u_{n}$ 和 $\sum_{n=1}^{\infty}u_{-n}$ 在 $S$ 上一致收敛。

如果 $0\leq R_{1}<R_{2}\leq \infty$ 且 $a \in \mathbb{C}$，我们定义 $\mathrm{ann}(a,R_{1},R_{2})$ 为开圆环 $\{ z \mid R_{1}<|z-a|<R_{2} \}$. 注意 $\mathrm{ann}(a,0,R)$ 是一个中心穿孔的圆盘。

**定理 4.1.8**

设 $f$ 在 $\mathrm{ann}(a,R_{1},R_{2})$ 上解析，则有

$$
\begin{gather}
f(z)=\sum_{n=-\infty}^{\infty} a_{n}(z-a)^{n}
\end{gather}
$$

其中当 $R_{1}<r_{1}<r_{2}<R_{2}$ 时级数在 $\overline{\mathrm{ann}(a,r_{1},r_{2})}$ 上绝对且一致收敛。其系数由

$$
\begin{gather}
a_{n}=\dfrac{1}{2\pi i} \int_{\gamma} \dfrac{f(z)}{(z-a)^{n+1}} \mathrm{d} z
\end{gather}
$$

给出，其中 $\gamma$ 是圆 $|z-a|=r,R_{1}<r<R_{2}$. 此外，这一级数是唯一的，称为 $f$ 在 $a$ 处的 **Laurent 级数**。

**证明**

我们首先证明唯一性。假设 $f(z)=\sum_{n=-\infty}^{\infty}a_{n}(z-a)^{n}$ 绝对且一致收敛，则我们可以将积分与求和交换位置，得到

$$
\begin{align}
\int_{\gamma} \dfrac{f(z)}{(z-a)^{k+1}}\mathrm{d} z = \sum_{n=-\infty}^{\infty} \int_{\gamma} \dfrac{a_{n}}{(z-a)^{k-n+1}} \mathrm{d} z
\end{align}
$$

由于 $\gamma(t)=a+re^{it},0\leq t\leq 2\pi$，故右侧的积分中仅有 $\int_{\gamma}(z-a)^{-1}\mathrm{d}z$ 一项不为零，从而有

$$
\begin{gather}
\int_{\gamma} \dfrac{f(z)}{(z-a)^{k+1}}\mathrm{d} z=2\pi i a_{k}
\end{gather}
$$

即证唯一性。下面我们来证明存在性。

设 $R_{1}<r_{1}<r_{2}<R_{2}$，令 $\gamma_{1},\gamma_{2}$ 分别为圆 $|z-a|=r_{1},|z-a|=r_{2}$，则在 $\mathrm{ann}(a,R_{1},R_{2})$ 中有 $\gamma_{1}\sim\gamma_{2}$. 这表明，对于 $\mathrm{ann}(a,R_{1},R_{2})$ 上的解析函数 $g$ 有 $\int_{\gamma_{1}}g=\int_{\gamma_{2}}g$. 特别地，系数 $a_{n}$ 的积分表达式与 $r$ 无关，从而 $a_{n}$ 是一个常数。令 $f_{2}\colon B(a,R_{2})\to \mathbb{C}$ 为

$$
\begin{gather}
f_{2}(z)=\dfrac{1}{2\pi i} \int_{|w-a|=r_{2}} \dfrac{f(w)}{w-z} \mathrm{d} w
\end{gather}
$$

其中 $|z-a|<r_{2},R_{1}<r_{2}<R_{2}$，则引理 3.2.1 表明 $f_{2}$ 在 $B(a,R_{2})$ 上解析。类似地，设 $G=\{ z \mid |z-a|>R_{1} \}$，令 $f_{1}\colon G\to \mathbb{C}$ 为

$$
\begin{gather}
f_{1}(z)=- \dfrac{1}{2\pi i} \int_{|w-a|=r_{1}} \dfrac{f(w)}{w-z}\mathrm{d} w
\end{gather}
$$

其中 $|z-a|>r_{1},R_{1}<r_{1}<R_{2}$，则同样有 $f_{1}$ 在 $G$ 上解析。

当 $R_{1}<|z-a|<R_{2}$ 时，选取 $r_{1},r_{2}$ 使得 $R_{1}<r_{1}<|z-a|<r_{2}<R_{2}$，并取 $\gamma_{1}(t)=a+r_{1}e^{it},\gamma_{2}(t)=a+r_{2}e^{it}$，以及一条直线段 $\lambda$ 连接 $\gamma_{1}$ 和 $\gamma_{2}$ 并避开点 $z$，如图所示。

![](4-3.png)

由于 $\gamma_{1}\sim\gamma_{2}$，故闭曲线 $\gamma=\gamma_{2}-\lambda-\gamma_{1}+\lambda$ 满足 $\gamma \sim 0$. 又因为 $n(\gamma_{2},z)=1$，$n(\gamma_{1},z)=0$，故由 Cauchy 积分公式得

$$
\begin{align}
f(z) &= \dfrac{1}{2\pi i} \int_{\gamma_{2}} \dfrac{f(w)}{w-z} \mathrm{d} w- \dfrac{1}{2\pi i} \int_{\gamma_{1}} \dfrac{f(w)}{w-z} \mathrm{d} w \\
&= f_{2}(z)+f_{1}(z)
\end{align}
$$

下面我们要对 $f_{2},f_{1}$ 做幂级数展开，将它们相加就得到 $f(z)$ 的 Laurent 级数。由于 $f_{2}$ 在 $B(a,R_{2})$ 上解析，应用引理 3.2.1 即得

$$
\begin{gather}
\dfrac{1}{n!} f_{2}^{(n)}(z)=\dfrac{1}{2\pi i} \int_{\gamma_{2}} \dfrac{f(w)}{(w-z)^{n+1}} \mathrm{d} w=a_{n}
\end{gather}
$$

现在定义 $g(z)=f_{1}(a+1 /z)$，则 $z=0$ 是一个孤立奇点。我们断言 $z=0$ 是可去的。事实上，当 $r>R_{1}$ 时我们定义 $\rho(z)=d(z,C)$，其中 $C$ 是圆 $|w-a|=r$，并令 $M=\max_{w \in C}|f(w)|$，则对于 $|z-a|>r$ 有

$$
\begin{gather}
|f_{1}(z)|\leq \dfrac{Mr}{\rho(z)} \to 0 \quad (z\to \infty)
\end{gather}
$$

故

$$
\begin{gather}
\lim_{ z \to 0 } g(z)=\lim_{ z \to 0 } f_{1}\left( a+\dfrac{1}{z} \right)=0
\end{gather}
$$

因此，如果我们定义 $g(0)=0$，那么 $g$ 在 $B(0,1 /R_{1})$ 上解析。设

$$
\begin{gather}
g(z)=\sum_{n=1}^{\infty} B_{n}z^{n}, \quad B_{n}=\dfrac{1}{2\pi i} \int_{|w|=r} \dfrac{g(w)}{w^{n+1}} \mathrm{d} w \quad (R_{1}<1 /r<R_{2})
\end{gather}
$$

则 $f_{1}(z)=g\left( \dfrac{1}{z-a} \right)$ 的幂级数展开式中 $(z-a)^{-n}$ 项的系数为 $B_{n}$. 做变量替换 $w=\dfrac{1}{z-a}$，当 $w$ 沿着圆 $|w|=r$ 逆时针绕行一圈时，$z$ 沿着圆 $|z-a|=1 /r$ 顺时针绕行一圈，因此我们有

$$
\begin{align}
B_{n}&=- \dfrac{1}{2\pi i} \int_{|z-a|=1 /r} f_{1}(z)(z-a)^{n+1} \left( -\dfrac{1}{(z-a)^{2}} \right)\mathrm{d} z \\
&= \dfrac{1}{2\pi i} \int_{|z-a|=1 /r} \dfrac{f_{1}(z)}{(z-a)^{-n+1}} \mathrm{d} z
\end{align}
$$

由于 $f_{1}(z)=f(z)-f_{2}(z)$，且 $f_{2}(z)$ 在 $B(a,R_{2})$ 上解析，因而 Cauchy 定理给出 $B_{n}=a_{-n}$. 再根据 $f_{2}(z),f_{1}(z)$ 的幂级数收敛性质，可知级数 $\sum_{n=-\infty}^{\infty}a_{n}(z-a)^{n}$ 在小圆环上绝对且一致收敛。这就完成了证明。

现在我们可以直接根据 Laurent 级数的系数来对孤立奇点进行分类。

**定理 4.1.9**

设 $f$ 在 $a$ 处有一个孤立奇点，$f(z)=\sum_{n=-\infty}^{\infty}a_{n}(z-a)^{n}$ 为其在穿孔圆盘 $\mathrm{ann}(a,0,R)$ 上的 Laurent 级数，则：

1. $a$ 是一个可去奇点当且仅当对 $n\leq -1$ 有 $a_{n}=0$
2. $a$ 是一个 $m$ 阶极点当且仅当 $a_{-m}\neq 0$ 且对 $n\leq -(m+1)$ 有 $a_{n}=0$
3. $a$ 是一个本性奇点当且仅当 $a_{n}\neq 0$ 对无穷多个负整数 $n$ 成立

**证明**

(1). 如果对 $n\leq-1$ 有 $a_{n}=0$，则定义为 $g(z)=\sum_{n=0}^{\infty}a_{n}(z-a)^{n}$ 在 $B(a,R)$ 上解析，并且在穿孔圆盘上与 $f(z)$ 相同，即证 $a$ 是可去的。反方向的蕴含同理。

(2). 如果对 $n\leq -(m+1)$ 有 $a_{n}=0$，那么 $(z-a)^{m}f(z)$ 的 Laurent 级数没有奇异项，由命题 1 知 $(z-a)^{m}f(z)$ 在 $a$ 点有可去奇点，故 $f$ 在 $a$ 处有一个 $m$ 阶极点。将以上论证反过来写即得反方向的蕴含。

(3). 由于 $f$ 在 $a$ 处有本性奇点当且仅当 $a$ 不是可去奇点也不是极点，于是由命题 1 和 2 即可证明 3.

本节的最后，我们再给出一个定理，它鲜明地显示了在一个本性奇点附近，函数的行为有多么的奇异：当 $z\to a$ 时，函数值 $f(z)$ 不仅仅在 $\mathbb{C}$ 上游走，而且它能够与 $\mathbb{C}$ 上的每个数都任意地接近。这实际上是 **Picard 大定理**的一个推论，它说的是，当 $z$ 趋于一个本性奇点时，函数值 $f(z)$ 可以取到 $\mathbb{C}$ 上的任意一点（并且取到无穷多次），至多只有一个例外。

**定理 4.1.10** Casorati-Weierstrass 定理

如果 $f$ 在 $a$ 处有一个本性奇点，则对任意 $\delta>0$，$\overline{f[\mathrm{ann}(a,0,\delta)]}=\mathbb{C}$.

**证明**

设 $f$ 在 $\mathrm{ann}(a,0,R)$ 上解析，我们要证如果给定 $c$ 和 $\varepsilon>0$，则对任意 $\delta>0$，存在 $z$ 使得 $|z-a|<\delta$ 且 $|f(z)-c|<\varepsilon$. 我们使用反证法。假设存在 $c$ 和 $\varepsilon$ 使得 $|f(z)-c|\geq \varepsilon$ 对任意 $z \in G=\mathrm{ann}(a,0,\delta)$ 成立，故

$$
\begin{gather}
\lim_{ z \to a } \dfrac{|f(z)-c|}{|z-a|}=\infty
\end{gather}
$$

这表明 $(z-a)^{-1}(f(z)-c)$ 在 $a$ 处有一个极点，设其阶数为 $m$. 故

$$
\begin{gather}
\lim_{ z \to a } |z-a|^{m+1} |f(z)-c|=0
\end{gather}
$$

从而由 $|f(z)|\leq|f(z)-c|+|c|$ 得 $\lim_{ z \to a }|z-a|^{m+1}|f(z)|=0$，因此 $(z-a)^{m}f(z)$ 在 $a$ 处有可去奇点，但这与 $a$ 是本性奇点的假设矛盾。这就完成了证明。

# Section 2: 留数

我们定义留数的动机来源于这样一个问题：如果 $f$ 在 $a$ 处有一个孤立奇点，那么对于一条同调于零且不经过 $a$ 的闭曲线 $\gamma$，积分 $\int_{\gamma}f$ 的值是什么？如果 $a$ 是可去奇点，那么显然积分等于零。而如果 $a$ 是极点或者本性奇点，那么积分的值有时不为零，并且对于特定的闭曲线 $\gamma$，其值由 Laurent 级数中的系数 $a_{-1}$ 给出。

**定义 4.2.1** 留数（residue）

如果 $f$ 在 $a$ 处有一个孤立奇点，令

$$
\begin{gather}
f(z)=\sum_{n=-\infty}^{\infty} a_{n}(z-a)^{n}
\end{gather}
$$

为其在 $a$ 处的 Laurent 级数。我们定义 $f$ 在 $a$ 处的**留数**为

$$
\begin{gather}
\mathrm{Res}(f,a)=a_{-1}=\dfrac{1}{2\pi i} \int_{|z-a|=r} f(z)\mathrm{d} z
\end{gather}
$$

以下的定理将积分曲线从圆推广到了更大的曲线类。

**定理 4.2.2** 留数定理（Residue Theorem）

设 $f$ 在除孤立奇点 $a_{1},\dots,a_{n}$ 外的区域 $G$ 上解析，如果 $G$ 上的可求长闭曲线 $\gamma$ 不经过任何一个 $a_{k}$，且 $\gamma \approx 0$，则

$$
\begin{gather}
\dfrac{1}{2\pi i} \int_{\gamma} f(z)\mathrm{d} z=\sum_{k=1}^{n} n(\gamma,a_{k}) \mathrm{Res}(f,a_{k})
\end{gather}
$$

**证明**

令 $m_{k}=n(\gamma,a_{k})$，并取 $r_{1},\dots,r_{n}> 0$ 使得闭圆盘 $\overline{B(a_{k},r_{k})}$ 两两不交，均不与 $\{ \gamma \}$ 相交，并且每个闭圆盘都包含在 $G$ 中。令

$$
\begin{gather}
\gamma_{k}(t)=a_{k}+r_{k} \exp(-2\pi im_{k} t), \quad 0\leq t\leq 1
\end{gather}
$$

则我们有

$$
\begin{gather}
n(\gamma,a_{j})+\sum_{k=1}^{n} n(\gamma_{k},a_{j})=0
\end{gather}
$$

又由于 $\gamma \approx 0$ 且 $\overline{B(a_{k},r_{k})}\subset G$，故对于 $G\setminus\{ a_{1},\dots,a_{n} \}$ 以外的点 $a$，我们也有

$$
\begin{gather}
n(\gamma,a)+\sum_{k=1}^{n} n(\gamma_{k},a)=0
\end{gather}
$$

由于 $f$ 在 $G\setminus\{ a_{1},\dots,a_{n} \}$ 上解析，Cauchy 定理给出

$$
\begin{gather}
\int_{\gamma} f+\sum_{k=1}^{n} \int_{\gamma_{k}} f=0
\end{gather}
$$

设 $f(z)=\sum_{n=-\infty}^{\infty}b_{n}(z-a_{k})^{n}$ 是 $f$ 在 $a_{k}$ 处的 Laurent 级数，则它在 $\overline{B(a_{k},r_{k})}\setminus\{ a_{k} \}$ 上一致收敛，于是我们有

$$
\begin{gather}
\int_{\gamma_{k}} f=\sum_{n=-\infty}^{\infty} b_{n} \int_{\gamma_{k}} (z-a)^{n}\mathrm{d} z=-2\pi i m_{k} b_{-1}=-2\pi i n(\gamma,a_{k}) \mathrm{Res}(f,a_{k})
\end{gather}
$$

这就完成了证明。

注意，在留数定理中我们要求 $f$ 的孤立奇点数量是有限个，但当 $f$ 有无穷多个孤立奇点时，上述定理仍然能够成立。这是因为 $f$ 的孤立奇点只能够在 $\partial G$ 上聚集，从而只有有限个点 $a_{k}$ 满足 $n(\gamma,a_{k})\neq 0$.

如果所求留数的奇点是一个极点，那么我们也有一种简单的方法来计算它。假设 $f$ 在 $a$ 处有一个 $m$ 阶极点，则 $g(z)=(z-a)^{m}f(z)$ 在 $a$ 处有可去奇点，并且 $g(a)\neq 0$. 设 $g(z)=\sum_{n=0}^{\infty}b_{n}(z-a)^{n}$ 是 $g$ 在 $a$ 处的幂级数展开，则在 $a$ 处的穿孔圆盘上，有 $f$ 的 Laurent 级数

$$
\begin{gather}
f(z)=\dfrac{b_{0}}{(z-a)^{m}}+\dots+\dfrac{b_{m-1}}{z-a}+\sum_{k=0}^{\infty} b_{m+k} (z-a)^{k}
\end{gather}
$$

于是我们有 $\mathrm{Res}(f,a)=b_{m-1}$. 这就是以下定理的主要内容。

**定理 4.2.3**

设 $f$ 在 $a$ 处有一个 $m$ 阶极点，令 $g(z)=(z-a)^{m}f(z)$，则

$$
\begin{gather}
\mathrm{Res}(f,a)=\dfrac{1}{(m-1)!} g^{(m-1)}(a)
\end{gather}
$$

特别地，如果 $a$ 是一个单极点（一阶极点），那么就有

$$
\begin{gather}
\mathrm{Res}(f,a)=g(a)=\lim_{ z \to a } (z-a)f(z)
\end{gather}
$$

留数定理的一个重要应用在于，通过精心选取的积分路径，我们能够计算出一些无法通过微积分手段求出的实积分。本节的剩余部分将展示如何使用留数定理来计算特定的定积分。

**例 4.2.4**

计算定积分

$$
\begin{gather}
\int_{-\infty}^{\infty} \dfrac{x^{2}}{1+x^{4}} \mathrm{d} x
\end{gather}
$$

设 $f(z)=\dfrac{z^{2}}{1+z^{4}}$，则它的极点正是 $-1$ 的四个四次单位根，即

$$
\begin{gather}
a_{n}=\exp\left( i\left( \dfrac{\pi}{4}+(n-1) \dfrac{\pi}{2} \right) \right), \quad n=1,2,3,4
\end{gather}
$$

显然它们都是单极点，从而有

$$
\begin{align}
\mathrm{Res}(f,a_{1})&=\lim_{ z \to a_{1} } (z-a_{1})f(z)=\dfrac{a_{1}^{2}}{(a_{1}-a_{2})(a_{1}-a_{3})(a_{1}-a_{4})} \\
&= \dfrac{1-i}{4\sqrt{ 2 }}= \dfrac{1}{4}\exp\left( -i \dfrac{\pi}{4} \right)
\end{align}
$$

同理

$$
\begin{gather}
\mathrm{Res}(f,a_{2})=\dfrac{-1-i}{4\sqrt{ 2 }}= \dfrac{1}{4}\exp\left( -i \dfrac{3\pi}{4} \right)
\end{gather}
$$

![](4-4.png)

现在令 $R>1$，并取如图所示的积分路径 $\gamma$，根据留数定理我们有

$$
\begin{gather}
\dfrac{1}{2\pi i} \int_{\gamma} f= \dfrac{-i}{2\sqrt{ 2 }}
\end{gather}
$$

然而，根据线积分的定义，我们便有

$$
\begin{gather}
\int_{\gamma}f=\int_{-R}^{R} \dfrac{x^{2}}{1+x^{4}}\mathrm{d} x+\int_{0}^{\pi} \dfrac{iR^{3}e^{3it}}{1+R^{4}e^{4it}} \mathrm{d} t=\dfrac{\pi}{\sqrt{ 2 }}
\end{gather}
$$

由于

$$
\begin{gather}
\left\lvert  iR^{3} \int_{0}^{\pi} \dfrac{e^{3it}}{1+R^{4}e^{4it}} \mathrm{d} t  \right\rvert \leq \dfrac{\pi R^{3}}{R^{4}-1} \to 0 \quad (R\to \infty)
\end{gather}
$$

从而我们就有

$$
\begin{gather}
\int_{-\infty}^{\infty} \dfrac{x^{2}}{1+x^{4}}\mathrm{d} x= \lim_{ R \to \infty } \int_{-R}^{R} \dfrac{x^{2}}{1+x^{4}}\mathrm{d} x= \dfrac{\pi}{\sqrt{ 2 }}
\end{gather}
$$

**例 4.2.5**

计算定积分

$$
\begin{gather}
\int_{0}^{\infty} \dfrac{\sin x}{x}\mathrm{d} x
\end{gather}
$$

考虑函数 $f(z)=\dfrac{e^{iz}}{z}$，其在 $z=0$ 处有一个单极点。设 $0<r<R$，令 $\gamma$ 为如下图所示的积分路径。

![](4-5.png)

由于 $\gamma \sim 0$，故由 Cauchy 定理得

$$
\begin{gather}
0=\int_{\gamma}f=\int_{r}^{R} \dfrac{e^{ix}}{x}\mathrm{d} x+\int_{\gamma_{R}} \dfrac{e^{iz}}{z}\mathrm{d} z+\int_{-R}^{-r} \dfrac{e^{ix}}{x}\mathrm{d} x+\int_{\gamma_{r}} \dfrac{e^{iz}}{z}\mathrm{d} z
\end{gather}
$$

其中 $\gamma_{R}$ 和 $\gamma_{r}$ 分别是半径为 $R$ 和 $r$ 的半圆。我们有

$$
\begin{align}
\int_{r}^{R} \dfrac{\sin x}{x}\mathrm{d} x &= \dfrac{1}{2i} \int_{r}^{R} \dfrac{e^{ix}-e^{-ix}}{x}\mathrm{d} x \\
&= \dfrac{1}{2i} \int_{r}^{R} \dfrac{e^{ix}}{x}\mathrm{d} x+\dfrac{1}{2i} \int_{-R}^{-r} \dfrac{e^{ix}}{x} \mathrm{d} x
\end{align}
$$

此外，我们还有

$$
\begin{align}
\left\lvert  \int_{\gamma_{R}} \dfrac{e^{iz}}{z}\mathrm{d} z \right\rvert &= \left\lvert  i \int_{0}^{\pi} \exp(i R e^{i\theta}) \mathrm{d} \theta  \right\rvert  \\
&\leq \int_{0}^{\pi} |\exp(i R e^{i\theta})| \mathrm{d} \theta \\
&= \int_{0}^{\pi} \exp(-R \sin\theta) \mathrm{d} \theta
\end{align}
$$

通过分析 $\exp(-R\sin\theta)$ 的单调性，可知当 $\delta>0$ 充分小时，函数 $\exp(-R\sin\theta)$ 在 $\delta\leq\theta\leq \pi-\delta$ 上的最大值为 $\exp(-R\sin\delta)$，从而有

$$
\begin{align}
\left\lvert  \int_{\gamma_{R}} \dfrac{e^{iz}}{z}\mathrm{d} z  \right\rvert &\leq 2\delta+ \int_{\delta}^{\pi-\delta} \exp(-R\sin\theta) \mathrm{d} \theta \\
&< 2\delta+\pi \exp(-R\sin\delta)
\end{align}
$$

由于 $\lim_{ R \to \infty }\exp(-R\sin\delta)=0$，故给定 $\varepsilon>0$，取 $\delta<\varepsilon /3$，存在 $R_{0}$ 使得当 $R>R_{0}$ 时有 $\exp(-R\sin\delta)<\varepsilon /3\pi$，即得

$$
\begin{gather}
\lim_{ R \to \infty } \int_{\gamma_{R}} \dfrac{e^{iz}}{z}\mathrm{d} z=0
\end{gather}
$$

另一边，考虑函数 $\dfrac{e^{iz}-1}{z}$，它在 $z=0$ 处有一个可去奇点，因此当 $|z|\leq 1$ 时存在 $M>0$ 使得 $\left\lvert  \dfrac{e^{iz}-1}{z}  \right\rvert\leq M$，因此

$$
\begin{gather}
\left\lvert  \int_{\gamma_{r}} \dfrac{e^{iz}-1}{z}\mathrm{d} z  \right\rvert \leq \pi rM \to 0 \quad (r\to 0+)
\end{gather}
$$

于是我们有

$$
\begin{gather}
\lim_{ r \to 0+ } \int_{\gamma_{r}} \dfrac{e^{iz}}{z}\mathrm{d} z= \lim_{ r \to 0+ } \int_{\gamma_{r}} \dfrac{1}{z}\mathrm{d} z=-i\pi
\end{gather}
$$

即证

$$
\begin{gather}
\int_{0}^{\infty} \dfrac{\sin x}{x}\mathrm{d} x= \dfrac{\pi}{2}
\end{gather}
$$

在这个例子中我们没有使用留数定理，而是以 Cauchy 定理为核心。然而，在这一例子中我们用来计算积分的技术与使用留数定理时应用的技术是相同的。

**例 4.2.6**

当 $a>1$ 时计算

$$
\begin{gather}
\int_{0}^{\pi} \dfrac{\mathrm{d} \theta}{a+\cos\theta}
\end{gather}
$$

如果 $z=e^{i\theta}$，那么 $\overline{z}=\dfrac{1}{z}$，因此

$$
\begin{align}
a+\cos\theta=a+\dfrac{1}{2}(z+\overline{z})=a+\dfrac{1}{2}\left( z+\dfrac{1}{z} \right)=\dfrac{z^{2}+2az+1}{2z}
\end{align}
$$

从而

$$
\begin{align}
\int_{0}^{\pi} \dfrac{\mathrm{d} \theta}{a+\cos\theta}&= \dfrac{1}{2} \int_{0}^{2\pi} \dfrac{\mathrm{d} \theta}{a+\cos\theta} \\
&= -i \int_{\gamma} \dfrac{\mathrm{d} z}{z^{2}+2az+1}
\end{align}
$$

其中 $\gamma$ 是圆 $|z|=1$. 又由于 $z^{2}+2az+1=(z-\alpha)(z-\beta)$，其中 $\alpha=-a+\sqrt{ a^{2}-1 }$，$\beta=-a-\sqrt{ a^{2}-1 }$，故 $|\alpha|<1$，$|\beta|>1$，根据留数定理，有

$$
\begin{align}
\int_{\gamma} \dfrac{\mathrm{d} z}{z^{2}+2az+1}=\dfrac{2\pi i}{\alpha-\beta}=\dfrac{\pi i}{\sqrt{ a^{2}-1 }}
\end{align}
$$

即证

$$
\begin{gather}
\int_{0}^{\pi} \dfrac{\mathrm{d} \theta}{a+\cos\theta}=\dfrac{\pi}{\sqrt{ a^{2}-1 }}
\end{gather}
$$

**例 4.2.7**

计算定积分

$$
\begin{gather}
\int_{0}^{\infty} \dfrac{\log x}{1+x^{2}} \mathrm{d} x
\end{gather}
$$

为了使用留数定理，我们需要用到复对数，因此就需要选取对数的一个分支。在本例中，我们在区域

$$
\begin{gather}
G=\left\{  z \in \mathbb{C} \mid z\neq 0, -\dfrac{\pi}{2}<\mathrm{arg}\,z< \dfrac{3\pi}{2}  \right\}
\end{gather}
$$

上定义对数的分支 $\log(|z|e^{i\theta})=\log|z|+i\theta$，其中 $-\dfrac{\pi}{2}<\theta<\dfrac{3\pi}{2}$. 现在令 $0<r<1<R$，并取例 4.2.5 中的积分路径 $\gamma$，则我们有

$$
\begin{align}
\int_{\gamma} \dfrac{\log z}{1+z^{2}}\mathrm{d} z &=\int_{r}^{R} \dfrac{\log x}{1+x^{2}}\mathrm{d} x+iR \int_{0}^{\pi} \dfrac{\log R+i\theta}{1+R^{2}e^{2i\theta}} e^{i\theta} \mathrm{d} \theta \\
&+\int_{-R}^{-r} \dfrac{\log|x|+i\pi}{1+x^{2}}\mathrm{d} x+ir \int_{\pi}^{0} \dfrac{\log r+i\theta}{1+r^{2}e^{2i\theta}}e^{i\theta} \mathrm{d} \theta
\end{align}
$$

函数 $\dfrac{\log z}{1+z^{2}}$ 在 $\gamma$ 内部的极点只有 $z=i$，并且显然它是一个单极点，因此留数定理给出

$$
\begin{gather}
\int_{\gamma} \dfrac{\log z}{1+z^{2}}\mathrm{d} z=2\pi i \dfrac{\log |i|+i(\pi /2)}{2i}=\dfrac{\pi^{2}i}{2}
\end{gather}
$$

此外，我们有

$$
\begin{gather}
\int_{r}^{R} \dfrac{\log x}{1+x^{2}}\mathrm{d} x+\int_{-R}^{-r} \dfrac{\log|x|+i\pi}{1+x^{2}}\mathrm{d} x=2 \int_{r}^{R} \dfrac{\log x}{1+x^{2}}\mathrm{d} x+i\pi \int_{r}^{R} \dfrac{\mathrm{d} x}{1+x^{2}}
\end{gather}
$$

令 $r\to 0+$ 且 $R\to \infty$，并利用等式

$$
\begin{gather}
\int_{0}^{\infty} \dfrac{\mathrm{d} x}{1+x^{2}}=\lim_{ x \to \infty } \arctan x =\dfrac{\pi}{2}
\end{gather}
$$

我们就有

$$
\begin{align}
\int_{0}^{\infty} \dfrac{\log x}{1+x^{2}}\mathrm{d} x &= \dfrac{1}{2} \lim_{ r \to 0+ } ir \int_{0}^{\pi} \dfrac{\log r+i\theta}{1+r^{2}e^{2i\theta}}e^{i\theta} \mathrm{d} \theta \\
&- \dfrac{1}{2} \lim_{ R \to \infty } iR \int_{0}^{\pi} \dfrac{\log R+i\theta}{1+R^{2}e^{2i\theta}} e^{i\theta} \mathrm{d} \theta
\end{align}
$$

我们来证明右侧的两个极限均为零。设 $\rho>0$，则

$$
\begin{align}
\left\lvert  \rho \int_{0}^{\pi} \dfrac{\log \rho +i\theta}{1+\rho^{2} e^{2i\theta}} e^{i\theta} \mathrm{d} \theta  \right\rvert &\leq \dfrac{\rho \lvert \log \rho \rvert }{|1-\rho^{2}|}\int_{0}^{\pi} \mathrm{d} \theta+ \dfrac{\rho}{|1-\rho^{2}|} \int_{0}^{\pi} \theta \mathrm{d} \theta \\
&= \dfrac{\pi \rho \lvert \log \rho \rvert }{|1-\rho^{2}|}+\dfrac{\pi^{2} \rho}{2|1-\rho^{2}|}
\end{align}
$$

当 $\rho\to 0+$ 或 $\rho\to \infty$ 时，上述表达式的极限均为零，即证

$$
\begin{gather}
\int_{0}^{\infty} \dfrac{\log x}{1+x^{2}} \mathrm{d} x=0
\end{gather}
$$

**例 4.2.8**

当 $0<c<1$ 时计算

$$
\begin{gather}
\int_{0}^{\infty} \dfrac{x^{-c}}{1+x} \mathrm{d} x
\end{gather}
$$

与上例相同，我们需要选取 $z^{-c}$ 的一个分支。本例中我们选取的积分路径通常称为锁孔围道（keyhole contour），如下图所示。这样选取的原因是为了避开对数的分支割线（branch cut），通常为正实轴 $[0,\infty)$.

![](4-6.png)

令 $G=\{ z \in \mathbb{C} \mid z\neq 0, 0<\mathrm{arg}\,z<2\pi \}$，在 $G$ 上定义对数的一个分支 $\log z$，并取 $z^{-c}=\exp(-c\log z)$. 令 $\gamma$ 为图示的锁孔围道，其中 $0<r<1<R$，$L_{1}$ 为线段 $[r+i\delta,R+i\delta]$，$L_{2}$ 为线段 $[R-i\delta,r-i\delta]$，$\delta>0$.

函数 $\dfrac{z^{-c}}{1+z}$ 在 $\gamma$ 内部有一个单极点 $z=-1$，因此留数定理给出

$$
\begin{gather}
\int_{\gamma} \dfrac{z^{-c}}{1+z}=2\pi i e^{-i\pi c}
\end{gather}
$$

根据线积分的定义，我们有

$$
\begin{gather}
\int_{L_{1}} \dfrac{z^{-c}}{1+z}\mathrm{d} z=\int_{r}^{R} \dfrac{(t+i\delta)^{-c}}{1+t+i\delta} \mathrm{d} t
\end{gather}
$$

定义 $g\colon[r,R]\times\left[ 0, \dfrac{\pi}{2} \right]\to \mathbb{R}$ 为

$$
\begin{gather}
g(t,\delta)=\left\lvert  \dfrac{(t+i\delta)^{-c}}{1+t+i\delta}- \dfrac{t^{-c}}{1+t}  \right\rvert  \quad (\delta>0)
\end{gather}
$$

且 $g(t,0)=0$. 则 $g$ 是连续函数，从而一致连续。给定 $\varepsilon>0$，存在 $\delta_{0}$ 使得当 $(t-t')^{2}+(\delta-\delta')^{2}<\delta_{0}^{2}$ 时有 $|g(t,\delta)-g(t',\delta')|<\varepsilon /R$，特别地，当 $r\leq t\leq R$ 且 $\delta<\delta_{0}$ 时有 $g(t,\delta)<\varepsilon /R$，从而

$$
\begin{gather}
\int_{r}^{R} g(t,\delta)\mathrm{d} t<\varepsilon
\end{gather}
$$

这表明

$$
\begin{gather}
\int_{r}^{R} \dfrac{t^{-c}}{1+t}\mathrm{d} t= \lim_{ \delta \to 0+ } \int_{L_{1}} \dfrac{z^{-c}}{1+z}\mathrm{d} z
\end{gather}
$$

类似地，利用 $\log \overline{z}=\overline{\log z}+2\pi i$，我们可得

$$
\begin{gather}
-e^{-2\pi ic} \int_{r}^{R} \dfrac{t^{-c}}{1+t}\mathrm{d} t=\lim_{ \delta \to 0+ } \int_{L_{2}} \dfrac{z^{-c}}{1+z}\mathrm{d} z
\end{gather}
$$

从而

$$
\begin{align}
2\pi i e^{-i\pi c}-(1-e^{-2\pi ic}) \int_{r}^{R} \dfrac{t^{-c}}{1+t}\mathrm{d} t=\lim_{ \delta \to 0+ } \left( \int_{\gamma_{r}} \dfrac{z^{-c}}{1+z}\mathrm{d} z+\int_{\gamma_{R}} \dfrac{z^{-c}}{1+z}\mathrm{d} z \right)
\end{align}
$$

而当 $\rho>0$ 且 $\rho\neq 1$ 时，令 $\gamma_{\rho}$ 为圆 $|z|=\rho$ 上从 $\sqrt{ \rho^{2}-\delta^{2} }+i\delta$ 到 $\sqrt{ \rho^{2}-\delta^{2} }-i\delta$ 的一段弧，则有

$$
\begin{gather}
\left\lvert  \int_{\gamma_{\rho}} \dfrac{z^{-c}}{1+z}\mathrm{d} z  \right\rvert \leq \dfrac{\rho^{-c}}{|1-\rho|} 2\pi \rho
\end{gather}
$$

因此

$$
\begin{align}
\left\lvert  2\pi i e^{-i\pi c}-(1-e^{-2\pi ic}) \int_{r}^{R} \dfrac{t^{-c}}{1+t}\mathrm{d} t \right\rvert \leq \dfrac{r^{-c}2\pi r}{|1-r|}+\dfrac{R^{-c}2\pi R}{|1-R|}
\end{align}
$$

当 $r\to 0+$ 且 $R\to \infty$ 时，上式右侧的两个表达式的极限为零，因此

$$
\begin{align}
\int_{0}^{\infty} \dfrac{t^{-c}}{1+t}\mathrm{d} t &= \dfrac{2\pi i e^{-i\pi c}}{1-e^{-2\pi ic}} \\
&= \dfrac{2\pi i}{e^{i\pi c}-e^{-i\pi c}} \\
&= \dfrac{\pi}{\sin \pi c}
\end{align}
$$

# Section 3: 辐角原理

假设 $f$ 是解析函数，在 $z=a$ 处有一个 $m$ 阶零点，于是存在解析函数 $g$ 使得 $f(z)=(z-a)^{m}g(z)$，其中 $g(a)\neq 0$. 因此

$$
\begin{gather}
\dfrac{f'(z)}{f(z)}=\dfrac{m}{z-a}+\dfrac{g'(z)}{g(z)}
\end{gather}
$$

并且 $\dfrac{g'}{g}$ 在 $a$ 的邻域内解析。现在设 $f$ 在 $z=a$ 处有一个 $m$ 阶极点，这就是说，$f(z)=(z-a)^{-m}g(z)$，其中 $g$ 解析且 $g(a)\neq 0$. 这给出

$$
\begin{gather}
\dfrac{f'(z)}{f(z)}=\dfrac{-m}{z-a}+\dfrac{g'(z)}{g(z)}
\end{gather}
$$

同样有 $\dfrac{g'}{g}$ 在 $a$ 的邻域内解析。

通过重复应用以上两个分解式，我们就可以给出本节的主定理“辐角原理”。不过首先，我们给出一些术语。

**定义 4.3.1** 亚纯（meromorphic）

设 $G\subset \mathbb{C}$ 是开集，如果函数 $f$ 在除极点外的 $G$ 上解析，则称 $f$ 是 $G$ 上的一个**亚纯函数**。

“亚纯”是与“全纯”（holomorphic）相对的定义。事实上，我们可以证明，一个亚纯函数一定可以写成两个全纯函数的商。因此，亚纯函数是区域上的有理函数的推广。

设 $f$ 是 $G$ 上的亚纯函数，$z$ 是一个极点，我们定义 $f\colon G\to \mathbb{C}_{\infty}$ 为 $f(z)=\infty$，则我们可以证明 $f$ 是 $G$ 到 $\mathbb{C}_{\infty}$ 的一个连续函数。换句话说，亚纯函数的不连续点是可去的，尽管它的不可微点（奇点）是不可去的。

**定理 4.3.2** 辐角原理（Argument Principle）

设 $f$ 是 $G$ 上的亚纯函数，其极点为 $p_{1},\dots,p_{m}$，零点为 $z_{1},\dots,z_{n}$，均按阶数重复。如果 $G$ 上的可求长闭曲线 $\gamma$ 满足 $\gamma \approx 0$ 且不经过任何一个 $p_{j}$ 和 $z_{k}$，则

$$
\begin{gather}
\dfrac{1}{2\pi i} \int_{\gamma} \dfrac{f'(z)}{f(z)}\mathrm{d} z=\sum_{k=1}^{n} n(\gamma,z_{k})-\sum_{j=1}^{m} n(\gamma,p_{j})
\end{gather}
$$

**证明**

我们有

$$
\begin{gather}
\dfrac{f'(z)}{f(z)}=\sum_{k=1}^{n} \dfrac{1}{z-z_{k}}-\sum_{j=1}^{m} \dfrac{1}{z-p_{j}}+\dfrac{g'(z)}{g(z)}
\end{gather}
$$

其中 $g$ 解析且在 $G$ 上不为零，这表明 $\dfrac{g'}{g}$ 在 $G$ 上解析，从而根据卷绕数的定义并应用 Cauchy 定理就完成了证明。

为什么这被称为“辐角原理”？答案在于复对数。事实上，如果我们可以定义 $\log f(z)$，那么它将是 $\dfrac{f'}{f}$ 的一个原函数，因此定理表明，当 $z$ 沿着 $\gamma$ 积分时，$\log f(z)$ 将变化 $2\pi i K$，其中 $K$ 是定理中等式右边的整数。由于 $\mathrm{Im}(\log f(z))=\mathrm{arg}\,f(z)$，因此辐角原理就是在说：沿着函数 $f$ 的零点或极点转过一圈，$f$ 的辐角将变化 $2\pi$ 的整数倍，其符号和倍数取决于零点和极点的阶数。

当然，以上讨论是不严谨的，因为我们无法在整个 $\mathbb{C}$ 上定义对数。然而，通过将 $\gamma$ 分割为若干小段，并在每个局部区域上定义一个对数分支，我们可以将上述讨论置于一个严格的基础之上。这一过程的技术细节我们在这里不做展开。

回顾一下辐角原理证明中的等式

$$
\begin{gather}
\dfrac{f'(z)}{f(z)}=\sum_{k=1}^{n} \dfrac{1}{z-z_{k}}-\sum_{j=1}^{m} \dfrac{1}{z-p_{j}}+\dfrac{h'(z)}{h(z)}
\end{gather}
$$

其中 $h$ 在 $G$ 上解析且不为零。设 $g$ 是一个解析函数，那么我们在上式两边乘以 $g$ 并沿着 $\gamma$ 积分，根据 Cauchy 积分公式与 Cauchy 定理，我们便立即得到以下辐角原理的推广：

**定理 4.3.3**

设 $f$ 是 $G$ 上的亚纯函数，其极点为 $p_{1},\dots,p_{m}$，零点为 $z_{1},\dots,z_{n}$，均按阶数重复。如果 $g$ 在 $G$ 上解析，$\gamma$ 是 $G$ 上的可求长闭曲线满足 $\gamma \approx 0$ 且不经过任何一个 $p_{j}$ 和 $z_{k}$，则

$$
\begin{gather}
\dfrac{1}{2\pi i} \int_{\gamma} g \dfrac{f'}{f}=\sum_{k=1}^{n} g(z_{k})n(\gamma,z_{k})-\sum_{j=1}^{m} g(p_{j})n(\gamma,p_{j})
\end{gather}
$$

我们已经知道一个解析的双射有一个解析反函数（定理 3.4.5）。现在，定理 4.3.3 给了我们一种计算该反函数的方法。假设 $R>0$，单射 $f$ 在 $\overline{B(a,R)}$ 上解析，令 $\Omega=f[B(a,R)]$，则当 $|z-a|<R$ 且 $\xi=f(z)\in\Omega$ 时，$f(w)-\xi$ 在 $B(a,R)$ 中有且仅有一个零点。如果我们取 $g(w)=w$，那么定理 4.3.3 给出

$$
\begin{gather}
z=\dfrac{1}{2\pi i} \int_{\gamma} \dfrac{wf'(w)}{f(w)-\xi} \mathrm{d} w
\end{gather}
$$

其中 $\gamma$ 是圆 $|z-a|=R$. 但 $z=f^{-1}(\xi)$，因此我们便证明了：

**定理 4.3.4**

设 $f$ 在包含 $\overline{B(a,R)}$ 的开集上解析，且 $f$ 在 $B(a,R)$ 上是单射。如果 $\Omega=f[B(a,R)]$ 且 $\gamma$ 是圆 $|z-a|=R$，则对 $w \in\Omega$ 有

$$
\begin{gather}
f^{-1}(w)=\dfrac{1}{2\pi i} \int_{\gamma} \dfrac{zf'(z)}{f(z)-w} \mathrm{d} z
\end{gather}
$$

我们以 Rouche 定理结束本节。

**定理 4.3.5** Rouche 定理

设 $f,g$ 在 $\overline{B(a,R)}$ 的一个邻域上亚纯，且在圆 $\gamma\colon|z-a|=R$ 上没有零点或极点。如果 $Z_{f},Z_{g},P_{f},P_{g}$ 分别是 $f,g$ 在 $\gamma$ 内部的零点和极点数量（计入重数），并且在 $\gamma$ 上有

$$
\begin{gather}
|f(z)+g(z)|<|f(z)|+|g(z)|
\end{gather}
$$

则

$$
\begin{gather}
Z_{f}-P_{f}=Z_{g}-P_{g}
\end{gather}
$$

**证明**

根据假设，在 $\gamma$ 上我们有

$$
\begin{gather}
\left\lvert  \dfrac{f(z)}{g(z)}+1  \right\rvert < \left\lvert  \dfrac{f(z)}{g(z)}  \right\rvert +1
\end{gather}
$$

如果 $\lambda=f(z) /g(z)$ 是一个正实数，那么上式就给出 $\lambda+1<\lambda+1$，一个矛盾。因此，亚纯函数 $f /g$ 将 $\gamma$ 映射到 $\Omega=\mathbb{C}\setminus [0,\infty)$，在 $\Omega$ 上定义一个对数分支 $\log z$，则 $\log(f /g)$ 是 $(f /g)'(f /g)^{-1}$ 在 $\gamma$ 邻域上的一个原函数，因此

$$
\begin{align}
0 &= \dfrac{1}{2\pi i} \int_{\gamma} (f /g)'(f /g)^{-1} \\
&= \dfrac{1}{2\pi i} \int_{\gamma} \left( \dfrac{f'}{f}-\dfrac{g'}{g} \right) \\
&= (Z_{f}-P_{f})-(Z_{g}-P_{g})
\end{align}
$$

这就完成了证明。

Rouche 定理可以用来给出代数基本定理的另一个证明。设多项式 $p(z)=z^{n}+a_{1}z^{n-1}+\dots+a_{n}$，则

$$
\begin{gather}
\dfrac{p(z)}{z^{n}}=1+\dfrac{a_{1}}{z}+\dots+\dfrac{a_{n}}{z^{n}} \to 1 \quad (z\to \infty)
\end{gather}
$$

因此对于充分大的 $R>0$，在圆 $|z|=R$ 上有

$$
\begin{gather}
\left\lvert  \dfrac{p(z)}{z^{n}}-1  \right\rvert <1
\end{gather}
$$

即 $|p(z)-z^{n}|<|z^{n}|$，从而 Rouche 定理表明 $p(z)$ 在圆 $|z|=R$ 内必然有 $n$ 个零点（因为 $z^{n}$ 在 $z=0$ 处有一个重数为 $n$ 的零点）。

另外，我们指出，Rouche 定理中使用圆作为积分曲线只是为了表述方便。实际上，任何同调于零的曲线 $\gamma$ 都适用，只是最终的等式需要根据卷绕数进行调整。