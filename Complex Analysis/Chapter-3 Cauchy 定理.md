本章我们介绍复分析中的核心定理之一——Cauchy 定理，它的不同版本以及推论。它展示了解析函数的积分与实函数的积分具有本质上的不同。

# Section 1: 卷绕数

之前我们证明了 $\int_{\gamma}(z-a)^{-1}\mathrm{d}z=2\pi in$，其中 $\gamma(t)=a+e^{2\pi in t}$，$0\leq t\leq 1$. 下面的定理表明，这一性质不止对于圆形环路成立。

**定理 3.1.1**

如果 $\gamma\colon[0,1]\to \mathbb{C}$ 是一条可求长闭曲线，$a \not\in \{ \gamma \}$，那么

$$
\begin{gather}
\dfrac{1}{2\pi i} \int_{\gamma} \dfrac{\mathrm{d} z}{z-a}
\end{gather}
$$

是一个整数。

**证明**

通过将可求长曲线用折线近似，我们可以假设 $\gamma$ 是分段光滑的，于是我们只需证明 $\gamma$ 是光滑曲线的情况。在这一条件下我们定义

$$
\begin{gather}
g(t)=\int_{0}^{t} \dfrac{\gamma'(s)}{\gamma(s)-a} \mathrm{d} s
\end{gather}
$$

于是 $g(0)=0,g(1)=\int_{\gamma}(z-a)^{-1}\mathrm{d}z$，并且有

$$
\begin{gather}
g'(t)=\dfrac{\gamma'(t)}{\gamma(t)-a}
\end{gather}
$$

但这给出

$$
\begin{align}
\dfrac{\mathrm{d} }{\mathrm{d} t} e^{-g(t)}(\gamma(t)-a) &= e^{-g} \gamma'-g'e^{-g}(\gamma-a) \\
&=e^{-g}(\gamma'-\gamma'(\gamma-a)^{-1}(\gamma-a)) \\
&= 0
\end{align}
$$

这表明 $e^{-g(t)}(\gamma(t)-a)$ 是常值函数，即

$$
\begin{gather}
\gamma(0)-a=e^{-g(1)}(\gamma(1)-a)=e^{-g(1)}(\gamma(0)-a)
\end{gather}
$$

从而 $g(1)=\int_{\gamma}(z-a)^{-1}\mathrm{d}z=2\pi in$，其中 $n \in \mathbb{Z}$.

**定义 3.1.2** 卷绕数（winding number）

如果 $\gamma$ 是 $\mathbb{C}$ 上的一条可求长闭曲线，$a \not\in \{ \gamma \}$，则定义

$$
\begin{gather}
n(\gamma,a)=\dfrac{1}{2\pi i} \int_{\gamma} \dfrac{\mathrm{d} z}{z-a}
\end{gather}
$$

为 $\gamma$ 关于点 $a$ 的**卷绕数**。它也称为 $\gamma$ 关于点 $a$ 的**指标**（index）。

回顾一下，如果 $\gamma\colon[0,1]\to \mathbb{C}$ 是一条曲线，那么 $-\gamma$ 就是定义为 $(-\gamma)(t)=\gamma(1-t)$ 的反向曲线（事实上，这是原定义的一个重参数化，其不改变函数在曲线上积分的值）。此外，如果 $\gamma,\sigma$ 都是定义在 $[0,1]$ 上的曲线，$\gamma(1)=\sigma(0)$，那么我们定义 $\gamma+\sigma$ 为曲线

$$
\begin{gather}
(\gamma+\sigma)(t)=\begin{cases}
\gamma(2t), & 0\leq t\leq \dfrac{1}{2} \\
\sigma(2t-1), & \dfrac{1}{2}\leq t\leq 1
\end{cases}
\end{gather}
$$

它是将 $\gamma$ 的终点和 $\sigma$ 的起点相连构成的曲线。

**定理 3.1.3**

如果 $\gamma$ 和 $\sigma$ 是具有相同起点的可求长闭曲线，那么：

1. 对任意 $a \not\in \{ \gamma \}$ 有 $n(\gamma,a)=-n(-\gamma,a)$
2. 对任意 $a \not\in \{ \gamma \}\cup \{ \sigma \}$ 有 $n(\gamma+\sigma,a)=n(\gamma,a)+n(\sigma,a)$

**证明**

根据定理 2.1.12，$\int_{\gamma}f=-\int_{-\gamma}f$，即证命题 1. 对于命题 2，根据积分换元公式我们有

$$
\begin{align}
n(\gamma+\sigma,a) &= \dfrac{1}{2\pi i} \int_{0}^{1/2} \dfrac{\mathrm{d} \gamma(2t)}{\gamma(2t)-a}+\dfrac{1}{2\pi i} \int_{1 /2}^{1} \dfrac{\mathrm{d} \sigma(2t-1)}{\sigma(2t-1)-a} \\
&=\dfrac{1}{2\pi i} \int_{0}^{1} \dfrac{\mathrm{d} \gamma(s)}{\gamma(s)-a}+\dfrac{1}{2\pi i} \int_{0}^{1} \dfrac{\mathrm{d} \sigma(s')}{\sigma(s')-a} \\
&= n(\gamma,a)+n(\sigma,a)
\end{align}
$$

这就完成了证明。

为什么 $n(\gamma,a)$ 被称为 $\gamma$ 关于 $a$ 的卷绕数？一种解释来源于本节开头的例子：当 $\gamma(t)=a+e^{2\pi in t},0\leq t\leq 1$ 时有 $n(\gamma,a)=n$. 注意到随着 $t$ 从 $0$ 变化到 $1$，曲线 $\gamma$ 绕着 $a$ 点逆时针旋转了 $n$ 圈。相应地，如果 $\gamma$ 绕 $a$ 点顺时针旋转了 $n$ 圈（$\gamma(t)=a+e^{-2\pi in t}$），那么 $n(\gamma,a)=-n$. 换句话说，卷绕数检测了曲线绕某点旋转的圈数与方向。

更直观的解释涉及到复对数。尽管以下的讨论是不严谨的，但我们将在后续的章节中证明，通过一些更高阶的手段，我们可以将其修正，并为**辐角原理**（Argument Principle）提供洞见。

在实数微积分中，我们有 $\int(x-a)^{-1}\mathrm{d}x=\log(x-a)$. 因此我们似乎可以写下

$$
\begin{gather}
\int_{\gamma} \dfrac{\mathrm{d} z}{z-a}=\log(\gamma(1)-a)-\log(\gamma(0)-a)=0
\end{gather}
$$

因为 $\gamma(0)=\gamma(1)$. 然而这是错误的等式！复对数与实对数拥有本质上的区别，前者在复数域上拥有多值性，因此除非我们在对数的某个解析分支上工作，否则 $\log(\gamma(t)-a)$ 就不是良定的。特别地，如果 $\gamma$ 绕 $a$ 点旋转了一圈，那么我们无法定义 $\log(\gamma(t)-a)$，因为 $\mathbb{C}\setminus\{ a \}$ 上不存在对数的解析分支。

不过，仍有一种解读方法能够正确地给出答案。如果我们将复对数写成 $\log z=\log|z|+i\mathrm{arg}\,z$，那么我们有

$$
\begin{align}
&\int_{\gamma} \dfrac{\mathrm{d} z}{z-a}=\log(\gamma(1)-a)-\log(\gamma(0)-a) \\
&= \log|\gamma(1)-a|-\log|\gamma(0)-a|+i(\mathrm{arg}(\gamma(1)-a)-\mathrm{arg}(\gamma(0)-a))
\end{align}
$$

它的实部显然为零，并且，尽管 $\mathrm{arg}\,z$ 的值具有模糊性，我们至少能够同意上式的虚部是 $2\pi$ 的整数倍，并且这一整数检测了 $\gamma$ 绕 $a$ 的圈数。

设 $\gamma$ 是一条可求长闭曲线，我们考虑开集 $G=\mathbb{C}\setminus\{ \gamma \}$. 由于 $\{ \gamma \}$ 是紧致的，故存在 $R>0$ 使得 $\{ z \mid |z|>R \}\subset G$，这表明 $G$ 有且仅有一个无界的连通分量。

**定理 3.1.4**

设 $\gamma$ 是 $\mathbb{C}$ 中的一条可求长闭曲线，则 $n(\gamma,a)$ 作为 $a \not\in \{ \gamma \}$ 的函数在 $G=\mathbb{C}\setminus\{ \gamma \}$ 的每个连通分量上是常值函数。此外，在 $G$ 的无界连通分量上有 $n(\gamma,a)=0$.

**证明**

定义 $f\colon G\to \mathbb{C}$ 为 $f(a)=n(\gamma,a)$. 我们来证明 $f$ 是连续函数，从而对 $G$ 的每个连通分量 $D$，$f[D]\subset \mathbb{Z}$ 是连通集，从而 $f$ 在 $D$ 上为常值函数。

根据定理 1.2.9，由于 $G$ 是开集，故它的连通分量也是开集。固定 $a \in G$ 并取 $r=d(a,\{ \gamma \})$，如果 $|a-b|<\delta<r /2$，那么我们有

$$
\begin{align}
|f(a)-f(b)| &= \dfrac{1}{2\pi} \left\lvert  \int_{\gamma} \left( \dfrac{1}{z-a}-\dfrac{1}{z-b} \right)\mathrm{d} z  \right\rvert  \\
&\leq \dfrac{1}{2\pi} \int_{\gamma} \dfrac{|a-b||\mathrm{d} z|}{|z-a||z-b|} \\
&\leq \dfrac{\delta}{2\pi} \int_{\gamma} \dfrac{|\mathrm{d} z|}{|z-a||z-b|}
\end{align}
$$

由于 $|a-b|<r /2$，因此对于 $z \in \{ \gamma \}$ 有 $|z-a|\geq r>r /2$ 且 $|z-b|>r /2$，从而 $|f(a)-f(b)|\leq \dfrac{2\delta}{\pi r^{2}}V(\gamma)$. 因此，给定 $\varepsilon>0$，取 $\delta<r /2$ 且 $\delta<(\pi r^{2}\varepsilon) /2V(\gamma)$，即证 $f$ 是连续的。

现在设 $U$ 是 $G$ 的无界连通分量。根据 $\{ \gamma \}$ 的紧致性，存在 $R>0$ 使得 $\{ z \mid |z|>R \}\subset U$. 如果 $\varepsilon>0$，取 $|a|>R$ 且 $|z-a|>V(\gamma) /2\pi\varepsilon$ 对任意 $z \in \{ \gamma \}$ 成立，则 $|n(\gamma,a)|<\varepsilon$. 又由于 $n(\gamma,a)$ 在 $U$ 上是常值函数，即证 $n(\gamma,a)=0$.

# Section 2: Cauchy 积分公式

我们已经证明了 Cauchy 定理的一个特例：如果 $G$ 是一个开圆盘，那么对 $G$ 上的任意解析函数 $f$ 和任意可求长闭曲线 $\gamma$ 有 $\int_{\gamma}f=0$. 还有哪些区域 $G$ 也满足这个性质？我们可以找到一个不满足这一性质的区域 $\mathbb{C}\setminus\{ 0 \}$：取 $f=z^{-1},\gamma(t)=e^{it},0\leq t\leq 2\pi$，则 $\int_{\gamma}f=2\pi i$. 这是因为区域 $\mathbb{C}\setminus\{ 0 \}$ 的中心有一个“洞”。在下一节我们将证明，对于没有“洞”的区域 $G$，其上的解析函数和可求长闭曲线必定满足 $\int_{\gamma}f=0$.

在本节中，我们从另一个角度看待这个问题。固定区域 $G$，我们要问：闭曲线 $\gamma$ 满足什么条件，才能使 $\int_{\gamma}f=0$？这一问题的答案由 $\gamma$ 相对于 $G$ 的外部点的卷绕数决定。

**引理 3.2.1**

设 $\gamma$ 是一条可求长曲线，$\varphi$ 在 $\{ \gamma \}$ 上连续。对 $m\geq 1$ 和 $z \not\in \{ \gamma \}$，定义

$$
\begin{gather}
F_{m}(z)=\int_{\gamma} \dfrac{\varphi(w)}{(w-z)^{m}} \mathrm{d} w
\end{gather}
$$

则每个 $F_{m}$ 均在 $\mathbb{C}\setminus\{ \gamma \}$ 上解析，且 $F_{m}'(z)=mF_{m+1}(z)$.

**证明**

我们首先证明 $F_{m}$ 是连续的。其证明过程与定理 3.1.4 有相同的结构：由于 $\{ \gamma \}$ 是紧致集，故 $\varphi$ 是有界函数，此外，我们还有分解式

$$
\begin{align}
\dfrac{1}{(w-z)^{m}}-\dfrac{1}{(w-a)^{m}} &= \left( \dfrac{1}{w-z}-\dfrac{1}{w-a} \right) \sum_{k=1}^{m} \dfrac{1}{(w-z)^{m-k}(w-a)^{k-1}} \\
&=(z-a) \sum_{k=1}^{m} \dfrac{1}{(w-z)^{m-k+1}(w-a)^{k}}
\end{align}
$$

当 $|z-a|<\delta<r /2$ 时有 $|w-a|\geq r>r /2$ 且 $|w-z|>r /2$，从而

$$
\begin{align}
|F_{m}(z)-F_{m}(a)| &\leq \int_{\gamma} |\varphi(w)| |z-a| \sum_{k=1}^{m} \dfrac{1}{|w-z|^{m-k+1}|w-a|^{k}} |\mathrm{d} w| \\
&\leq \dfrac{mM\delta}{(r /2)^{m+1}} V(\gamma)
\end{align}
$$

取 $\delta<\min(r / 2,(r /2)^{m+1}\varepsilon / mMV(\gamma))$ 即证 $F_{m}$ 连续。

现在固定 $a \in G=\mathbb{C}\setminus\{ \gamma \}$，$z \in G,z\neq a$，则我们有

$$
\begin{align}
\dfrac{F_{m}(z)-F_{m}(a)}{z-a}=\sum_{k=1}^{m} \int_{\gamma} \dfrac{\varphi(w)(w-a)^{-k}}{(w-z)^{m-k+1}} \mathrm{d} w
\end{align}
$$

由于 $\varphi(w)(w-a)^{-k}$ 在 $\{ \gamma \}$ 上连续，故根据证明的第一部分，上式右侧的每个积分都定义了一个以 $z$ 为自变量的连续函数，于是令 $z\to a$，我们有

$$
\begin{align}
F_{m}'(a)=\sum_{k=1}^{m} \int_{\gamma} \dfrac{\varphi(w)}{(w-a)^{m+1}}\mathrm{d} w=mF_{m+1}(a)
\end{align}
$$

这就完成了证明。

**定理 3.2.2** Cauchy 积分公式 I

设 $G\subset \mathbb{C}$ 是开集，$f\colon G\to \mathbb{C}$ 是解析函数。如果 $\gamma$ 是 $G$ 中的一条可求长闭曲线，使得对任意 $w \in \mathbb{C}\setminus G$ 有 $n(\gamma,w)=0$，那么对 $a \in G\setminus\{ \gamma \}$ 有

$$
\begin{gather}
f(a)n(\gamma,a)=\dfrac{1}{2\pi i} \int_{\gamma} \dfrac{f(z)}{z-a} \mathrm{d} z
\end{gather}
$$

**证明**

定义 $\varphi\colon G\times G\to \mathbb{C}$ 为

$$
\begin{gather}
\varphi(z,w)=\begin{cases}
\dfrac{f(z)-f(w)}{z-w}, & z\neq w \\
f'(z), & z=w
\end{cases}
\end{gather}
$$

由于 $f$ 是解析函数，故 $\varphi$ 连续，并且对于 $w \in G$，函数 $z\mapsto\varphi(z,w)$ 是解析的。令 $H=\{ w \in \mathbb{C} \mid n(\gamma,w)=0 \}$，由于 $n(\gamma,w)$ 作为 $w$ 的函数是连续的，故 $H$ 是开集，并且 $G\cup H=\mathbb{C}$.

定义 $g\colon \mathbb{C}\to \mathbb{C}$ 为

$$
\begin{gather}
g(z)=\begin{cases}
\displaystyle \int_{\gamma} \varphi(z,w)\mathrm{d} w, & z \in G \\
\displaystyle \int_{\gamma} \dfrac{f(w)}{w-z}\mathrm{d} w, & z \in H
\end{cases}
\end{gather}
$$

当 $z \in G\cap H$ 时，我们有

$$
\begin{align}
\int_{\gamma} \varphi(z,w)\mathrm{d} w &= \int_{\gamma} \dfrac{f(w)-f(z)}{w-z} \mathrm{d} w \\
&= \int_{\gamma} \dfrac{f(w)}{w-z}\mathrm{d} w-2\pi in(\gamma,z) f(z) \\
&= \int_{\gamma} \dfrac{f(w)}{w-z}\mathrm{d} w
\end{align}
$$

因此 $g$ 是良定的。根据引理 3.2.1，$g$ 在 $\mathbb{C}$ 上解析，从而是一个整函数。定理 3.1.4 表明 $H$ 包含了 $\infty$ 的一个邻域，又由于 $f$ 在 $\{ \gamma \}$ 上有界，$\lim_{ z \to \infty }(w-z)^{-1}=0$ 对 $w \in \{ \gamma \}$ 一致成立，从而

$$
\begin{gather}
\lim_{ z \to \infty } g(z)=\lim_{ z \to \infty } \int_{\gamma} \dfrac{f(w)}{w-z}\mathrm{d} w=0
\end{gather}
$$

这表明 $g$ 在 $\{ z \mid |z|>R \}$ 上有界。再由 $g$ 在 $\overline{B(0,R)}$ 上有界，可知 $g$ 是一个有界整函数，从而根据 Liouville 定理，$g$ 是一个常值函数。由 $g$ 的极限值，可得 $g=0$ 恒成立。于是，对于 $a \in G\setminus\{ \gamma \}$，有

$$
\begin{align}
\int_{\gamma} \dfrac{f(z)-f(a)}{z-a}\mathrm{d} z=\int_{\gamma} \dfrac{f(z)}{z-a}\mathrm{d} z-n(\gamma,a)f(a)=0
\end{align}
$$

这就完成了证明。

直观上，条件 $n(\gamma,w)=0,w \in \mathbb{C}\setminus G$ 可以解释为 $\gamma$ 所围成的有界区域均完全包含于 $G$ 中。以上定理可以被推广为一个更通用的版本，其涉及多条曲线。

**定理 3.2.3** Cauchy 积分公式 II

设 $G\subset \mathbb{C}$ 是开集，$f\colon G\to \mathbb{C}$ 是解析函数。如果 $\gamma_{1},\dots,\gamma_{m}$ 是 $G$ 中的可求长闭曲线，使得对任意 $w \in \mathbb{C}\setminus G$ 有 $n(\gamma_{1},w)+\dots+n(\gamma_{m},w)=0$，则对于 $a \in G\setminus \bigcup_{k=1}^{m}\{ \gamma_{k} \}$ 有

$$
\begin{gather}
f(a)\sum_{k=1}^{m} n(\gamma_{k},a)=\dfrac{1}{2\pi i} \sum_{k=1}^{m} \int_{\gamma_{k}} \dfrac{f(z)}{z-a} \mathrm{d} z
\end{gather}
$$

**证明**

将定理 3.2.2 证明中的 $H$ 换成 $\{ w \in \mathbb{C} \mid n(\gamma_{1},w)+\dots+n(\gamma_{m},w)=0 \}$，函数 $g$ 换成在 $\gamma_{k}$ 上的积分之和，剩下的证明按 3.2.2 的结构进行即可。

在上述定理中做替换 $f(z)\mapsto f(z)(z-a)$，则我们立即得到推论：

**定理 3.2.4** Cauchy 定理 I

设 $G\subset \mathbb{C}$ 是开集，$f\colon G\to \mathbb{C}$ 是解析函数，$\gamma_{1},\dots,\gamma_{m}$ 是 $G$ 中的可求长闭曲线，使得对任意 $w \in \mathbb{C}\setminus G$ 有 $n(\gamma_{1},w)+\dots+n(\gamma_{m},w)=0$，则

$$
\begin{gather}
\sum_{k=1}^{m} \int_{\gamma_{k}} f(z)\mathrm{d} z=0
\end{gather}
$$

**定理 3.2.5**

设 $G\subset \mathbb{C}$ 是开集，$f\colon G\to \mathbb{C}$ 是解析函数。如果 $\gamma_{1},\dots,\gamma_{m}$ 是 $G$ 中的可求长闭曲线，使得对任意 $w \in \mathbb{C}\setminus G$ 有 $n(\gamma_{1},w)+\dots+n(\gamma_{m},w)=0$，则对于 $a \in G\setminus \bigcup_{k=1}^{m}\{ \gamma_{k} \}$ 和 $k\geq 1$ 有

$$
\begin{gather}
\dfrac{1}{k!} f^{(k)}(a) \sum_{k=1}^{m} n(\gamma_{k},a)=\dfrac{1}{2\pi i} \sum_{k=1}^{m} \int_{\gamma_{k}} \dfrac{f(z)}{(z-a)^{k+1}}\mathrm{d} z
\end{gather}
$$

**证明**

利用引理 3.2.1，在定理 3.2.3 公式两边对 $a$ 求导 $k$ 次即证。

**定理 3.2.6**

设 $G\subset \mathbb{C}$ 是开集，$f\colon G\to \mathbb{C}$ 是解析函数。如果 $\gamma$ 是 $G$ 中的可求长闭曲线，使得对任意 $w \in \mathbb{C}\setminus G$ 有 $n(\gamma,w)=0$，则对于 $a \in G\setminus \{ \gamma \}$ 和 $k\geq 1$ 有

$$
\begin{gather}
\dfrac{1}{k!} f^{(k)}(a)n(\gamma,a)=\dfrac{1}{2\pi i} \int_{\gamma} \dfrac{f(z)}{(z-a)^{k+1}} \mathrm{d} z
\end{gather}
$$

Cauchy 定理和积分公式是复分析的基本结论。由于这一定理对于整个理论而言是如此基础，所以在数学中，人们通常会探究该定理有效性的边界范围。对于闭曲线 $\gamma$，是否还有其他函数 $f$ 使得 $\int_{\gamma}f=0$？答案是否定的，正如以下 Cauchy 定理的逆命题所示。

我们称一条闭路径 $T$ 是**三角路径**（triangular path），如果它是一条具有三条边的折线。

**定理 3.2.7** Morera 定理

设 $G$ 是一个区域，$f\colon G\to \mathbb{C}$ 是一个连续函数，使得对任意 $G$ 中的三角路径 $T$ 有 $\int_{T}f=0$，那么 $f$ 是解析的。

**证明**

首先注意到，如果我们可以证明 $f$ 在 $G$ 中的任意圆盘上解析，那么 $f$ 就在 $G$ 上解析。因此，我们可以不失一般性地假设 $G$ 是圆盘 $B(a,R)$.

我们来证明 $f$ 在 $G$ 上有原函数，从而 $f=F'$ 是解析的。对 $z \in G$，我们定义 $F(z)=\int_{[a,z]}f$，注意 $[a,z]$ 是复平面上的一条线段。固定 $z_{0}\in G$，则对任意 $z \in G$，条件 $\int_{T}f=0$ 给出 $F(z)=\int_{[a,z_{0}]}f+\int_{[z_{0},z]}f$. 因此

$$
\begin{align}
\dfrac{F(z)-F(z_{0})}{z-z_{0}}-f(z_{0}) &= \dfrac{1}{z-z_{0}} \int_{[z_{0},z]} (f(w)-f(z_{0}))\mathrm{d} w
\end{align}
$$

从而

$$
\begin{gather}
\left\lvert  \dfrac{F(z)-F(z_{0})}{z-z_{0}}-f(z_{0})  \right\rvert \leq \max_{w \in[z_{0},z]} |f(w)-f(z_{0})|
\end{gather}
$$

令 $z\to z_{0}$，由于 $f$ 连续，故

$$
\begin{gather}
\lim_{ z \to z_{0} } \dfrac{F(z)-F(z_{0})}{z-z_{0}}=f(z_{0})
\end{gather}
$$

这就完成了证明。

# Section 3: 同伦与单连通性

上一节我们从卷绕数的角度给出了 Cauchy 定理成立的条件，它可以视为 Cauchy 定理的“同调”版本（我们将在本节的最后给出原因）。在本节中，我们将从同伦的角度给出闭曲线 $\gamma$ 的一个条件，使得 $\int_{\gamma}f=0$. 尽管这一条件不如同调版本那么具有普遍性，但它有更强的几何直观性，并且能够用来定义**单连通域**：在其上的任意解析函数和任意可求长闭曲线均满足 Cauchy 定理。因此，单连通域可以视为开圆盘的一种推广。

**定义 3.3.1** 同伦（homotopy），同伦的（homotopic）

设 $G$ 是一个区域，两条可求长闭曲线 $\gamma_{0},\gamma_{1}\colon[0,1]\to G$ 称为是**同伦的**，如果存在连续函数 $\Gamma\colon[0,1]^{2}\to G$ 使得

$$
\begin{gather}
\Gamma(s,0)=\gamma_{0}(s), \quad \Gamma(s,1)=\gamma_{1}(s), \quad \Gamma(0,t)=\Gamma(1,t)
\end{gather}
$$

对 $0\leq s,t\leq 1$ 成立。函数 $\Gamma$ 称为从 $\gamma_{0}$ 到 $\gamma_{1}$ 的**同伦**。

直观上来说，同伦可以视为一种对曲线的连续形变。如果我们定义 $\gamma_{t}\colon[0,1]\to G$ 为 $\gamma_{t}(s)=\Gamma(s,t)$，则 $\gamma_{t}$ 构成了一族连续闭曲线，从 $\gamma_{0}$ 开始，结束于 $\gamma_{1}$. 下面我们给出一个例子。

令 $G=B(a,R)$，$\gamma\colon[0,1]\to G$ 是一条可求长闭曲线，我们考虑直线同伦：对 $0\leq s,t\leq 1$，取 $\Gamma(s,t)=ta+(1-t)\gamma(s)$，则 $\Gamma(s,0)$ 是曲线 $\gamma$，而 $\Gamma(s,1)$ 则是常值曲线 $a$. 随着 $t$ 从 $0$ 到 $1$ 变化，曲线 $\gamma$ 逐渐收缩至点 $a$，这一过程是连续的，因为 $G$ 中没有“洞”。如若不然，当 $\gamma_{t}$ 经过洞时将会出现一个不连续点，从而无法达到 $a$.

在区域 $G$ 中，如果闭曲线 $\gamma_{0}$ 同伦于 $\gamma_{1}$，我们记作 $\gamma_{0}\sim_{G} \gamma_{1}$，当 $G$ 明确时，我们可以简写为 $\gamma_{0}\sim\gamma_{1}$. 容易证明 $\sim$ 是一个等价关系。

**定义 3.3.2** 凸的（convex），星状的（star-shaped）

集合 $G$ 是**凸的**，如果对任意 $a,b \in G$，连接点 $a,b$ 的线段 $[a,b]\subset G$. 集合 $G$ 是**星状的**或**星状凸的**（star-convex），如果存在 $a \in G$ 使得对任意 $z \in G$ 有 $[a,z]\subset G$. 此时也称 $G$ 是 $a$-星状的。

显然凸集一定是星状的，反之则不然。此外，星状集一定是连通集：如果 $G$ 是 $a$-星状集，那么对任意 $z,w \in G$，折线 $[z,a,w]$ 包含于 $G$ 中。

**定理 3.3.3**

设 $G$ 是一个 $a$-星状开集，如果 $\gamma_{0}$ 是恒等于 $a$ 的常值曲线，则 $G$ 上的每条可求长闭曲线都同伦于 $\gamma_{0}$.

**证明**

设 $\gamma_{1}$ 是 $G$ 上的一条可求长闭曲线，取 $\Gamma(s,t)=t\gamma_{1}(s)+(1-t)\gamma_{0}(s)$，由于 $G$ 是 $a$-星状的，故对任意 $s,t$，$\Gamma(s,t)$ 都是良定的。容易证明 $\Gamma$ 是一个同伦，这就完成了证明。

曲线同伦于常值曲线是一种我们经常会遇到的情况，我们给它一个定义：

**定义 3.3.4** 零伦/同伦于零（homotopic to zero）

如果 $G$ 中的可求长闭曲线 $\gamma$ 同伦于一个常值曲线，我们就称 $\gamma$ **同伦于零**，记作 $\gamma \sim 0$.

**定理 3.3.5** Cauchy 定理 II

设 $G\subset \mathbb{C}$ 是开集，$f\colon G\to \mathbb{C}$ 是一个解析函数，如果 $\gamma$ 是 $G$ 中的可求长闭曲线使得 $\gamma \sim 0$，则

$$
\begin{gather}
\int_{\gamma}f=0
\end{gather}
$$

以上就是同伦版本的 Cauchy 定理。我们可以通过同调版本来证明它，只需证明当 $\gamma \sim 0$ 蕴含 $n(\gamma,w)=0$ 对 $w \in \mathbb{C}\setminus G$ 成立即可。一种合理的证明思路如下：

令 $\gamma_{1}=\gamma$ 且 $\gamma_{0}$ 是常值曲线，使得 $\gamma_{1}\sim\gamma_{0}$. 设 $\Gamma$ 为 $\gamma_{0}$ 到 $\gamma_{1}$ 的同伦，并定义 $h(t)=n(\gamma_{t},w)$，其中 $\gamma_{t}(s)=\Gamma(s,t),w \in \mathbb{C}\setminus G$. 我们可以证明 $h$ 是连续的，从而由 $h(0)=0$ 且 $h(t) \in \mathbb{Z}$ 得 $h=0$.

上述论证的唯一困难在于，对于 $0<t<1$，曲线 $\gamma_{t}$ 不一定是可求长的。因此，为了使上述论证成立，我们必须引入额外的限制。好在，我们还有另一种证明方法，事实上，我们将证明以下的更有普遍性的版本：

**定理 3.3.6** Cauchy 定理 III

设 $G\subset \mathbb{C}$ 是开集，$f\colon G\to \mathbb{C}$ 是一个解析函数，如果 $\gamma_{0},\gamma_{1}$ 是 $G$ 中的可求长闭曲线，$\gamma_{0}\sim\gamma_{1}$，那么

$$
\begin{gather}
\int_{\gamma_{0}} f=\int_{\gamma_{1}} f
\end{gather}
$$

**证明**

令 $\Gamma\colon I^{2}\to G$ 为同伦。由于 $\Gamma$ 在紧致集 $I^{2}$ 上连续，从而一致连续，并且 $\Gamma[I^{2}]$ 是 $G$ 中的紧致集，因此

$$
\begin{gather}
r=d(\Gamma[I^{2}],\mathbb{C}\setminus G)>0
\end{gather}
$$

并且存在整数 $n$ 使得当 $(t-t')^{2}+(s-s')^{2}<4 /n^{2}$ 时有

$$
\begin{gather}
\lvert \Gamma(s,t)-\Gamma(s',t') \rvert <r
\end{gather}
$$

令

$$
\begin{gather}
Z_{jk}=\Gamma\left( \dfrac{j}{n}, \dfrac{k}{n} \right), \quad 0\leq j,k\leq n
\end{gather}
$$

并取

$$
\begin{gather}
J_{jk}=\left[ \dfrac{j}{n},\dfrac{j+1}{n} \right] \times\left[ \dfrac{k}{n}, \dfrac{k+1}{n} \right], \quad 0\leq j,k\leq n-1
\end{gather}
$$

由于 $J_{jk}$ 的直径为 $\dfrac{\sqrt{ 2 }}{n}$，故 $\Gamma[J_{jk}]\subset B(Z_{jk},r)$，因此如果我们定义 $P_{jk}$ 为闭折线 $[Z_{jk},Z_{j+1,k},Z_{j+1,k+1},Z_{j,k+1},Z_{jk}]$，则由于圆盘是凸集，我们有 $P_{jk}\subset B(Z_{jk},r)$. 根据 Cauchy 定理在圆盘上的特例，我们即得

$$
\begin{gather}
\int_{P_{jk}} f=0
\end{gather}
$$

现在我们来证明 $\int_{\gamma_{0}}f=\int_{Q_{0}}f=\int_{Q_{1}}f=\dots=\int_{Q_{n}}f=\int_{\gamma_{1}}f$，其中 $Q_{k}=[Z_{0k},Z_{1k},\dots,Z_{nk}]$. 首先，要证 $\int_{\gamma_{0}}f=\int_{Q_{0}}f$，我们令

$$
\begin{gather}
\sigma_{j}(t)=\gamma_{0}(t) ,\quad \dfrac{j}{n}\leq t\leq \dfrac{j+1}{n}
\end{gather}
$$

则 $\sigma_{j}+[Z_{j+1,0},Z_{j 0}]$ 是一条 $B(Z_{j 0},r)$ 内的可求长闭曲线，因此

$$
\begin{gather}
\int_{\sigma_{j}} f=-\int_{[Z_{j+1,0},Z_{j 0}]} f=\int_{[Z_{j 0},Z_{j+1,0}]}
\end{gather}
$$

两边对 $0\leq j\leq n$ 求和即得 $\int_{\gamma_{0}}f=\int_{Q_{0}}f$. 同理我们也有 $\int_{\gamma_{1}}f=\int_{Q_{n}}f$.

为证 $\int_{Q_{k}}f=\int_{Q_{k+1}}f$，我们使用折线 $P_{jk}$. 这给出

$$
\begin{gather}
\sum_{j=0}^{n-1} \int_{P_{jk}} f=0
\end{gather}
$$

![](3-1.png)

然而，如图所示，积分 $\int_{P_{jk}}f$ 包含了线段 $[Z_{j+1,k},Z_{j+1,k+1}]$ 上的积分，其值等于 $[Z_{j+1,k+1},Z_{j+1,k}]$ 上积分的相反数，而后者为积分 $\int_{P_{j+1,k}}f$ 的一部分。此外，由于 $\Gamma(s,t)$ 是闭曲线，我们有

$$
\begin{gather}
Z_{0k}=\Gamma\left( 0, \dfrac{k}{n} \right)=\Gamma\left( 1, \dfrac{k}{n} \right)=Z_{nk}
\end{gather}
$$

因此 $[Z_{0,k+1},Z_{0k}]=-[Z_{nk},Z_{n,k+1}]$，从而

$$
\begin{gather}
\sum_{j=0}^{n-1} \int_{P_{jk}}f=\int_{Q_{k}} f-\int_{Q_{k+1}} f=0
\end{gather}
$$

这就完成了证明。

在以上定理中令 $\gamma_{1}$ 为常值曲线，我们便立即得到了定理 3.3.5 作为推论。

**定理 3.3.7**

如果 $\gamma$ 是开集 $G$ 中的可求长闭曲线，$\gamma \sim 0$，那么对任意 $w \in \mathbb{C}\setminus G$ 有 $n(\gamma,w)=0$.

Cauchy 定理的另一个推论如下，它表明：对于端点固定的两条可求长曲线，如果一个可以通过连续形变变成另一个，那么解析函数的积分与路径无关。这里的“连续形变”是可求长曲线之间的同伦，定义如下：

**定义 3.3.8** 固定端点同伦（fixed-end-point(FEP) homotopic）

如果 $\gamma_{0},\gamma_{1}\colon[0,1]\to G$ 是 $G$ 上的可求长曲线使得 $\gamma_{0}(0)=\gamma_{1}(0)=a$，$\gamma_{0}(1)=\gamma_{1}(1)=b$，则 $\gamma_{0},\gamma_{1}$ 是**固定端点同伦的**，如果存在连续函数 $\Gamma\colon I^{2}\to G$ 满足

$$
\begin{align}
\Gamma(s,0)=\gamma_{0}(s),\quad \Gamma(s,1)=\gamma_{1}(s),\quad \Gamma(0,t)=a,\quad \Gamma(1,t)=b
\end{align}
$$

对 $0\leq s,t\leq 1$ 成立。

同样，容易证明 FEP 同伦是固定端点曲线上的等价关系。

如果 $\gamma_{0},\gamma_{1}$ 是从 $a$ 到 $b$ 的可求长曲线，那么 $\gamma_{0}-\gamma_{1}$ 是一条闭曲线，其中 $\gamma_{0}-\gamma_{1}=\gamma_{0}+(-\gamma_{1})$ 是以 $a$ 为起点，沿着 $\gamma_{0}$ 到 $b$，然后再沿着 $-\gamma_{1}$ 回到 $a$ 的环路。设 $\Gamma$ 是 $\gamma_{0}$ 到 $\gamma_{1}$ 的 FEP 同伦，并定义

$$
\begin{gather}
\gamma(s)=\begin{cases}
\gamma_{0}(3s), & 0\leq s\leq \dfrac{1}{3} \\
b, & \dfrac{1}{3}\leq s\leq \dfrac{2}{3} \\
\gamma_{1}(3-3s), & \dfrac{2}{3}\leq s\leq 1
\end{cases}
\end{gather}
$$

我们要证 $\gamma \sim 0$. 事实上，令

$$
\begin{gather}
\Lambda(s,t)=\begin{cases}
\Gamma(3s(1-t),t), & 0\leq s\leq \dfrac{1}{3} \\
\Gamma(1-t,3s-1+2t-3st), & \dfrac{1}{3}\leq s\leq \dfrac{2}{3} \\
\gamma_{1}((3-3s)(1-t)), & \dfrac{2}{3}\leq s\leq 1
\end{cases}
\end{gather}
$$

即可。虽然这个公式看起来有些神秘，但通过观察图片就能很容易地理解：对于给定的 $t$，$\Lambda$ 就是 $\Gamma$ 在正方形 $[0,1-t]\times[t,1]$ 边界上的限制。

![](3-2.png)

因此，对于 $G$ 上的解析函数 $f$，Cauchy 定理 II 给出

$$
\begin{gather}
0=\int_{\gamma}f=\int_{\gamma_{0}} f-\int_{\gamma_{1}} f
\end{gather}
$$

这就完成了以下定理的证明。

**定理 3.3.9** 路径无关性定理（Independence of Path Theorem）

设 $G\subset \mathbb{C}$ 是开集，$f\colon G\to \mathbb{C}$ 是解析函数，如果 $G$ 中从 $a$ 到 $b$ 的可求长曲线 $\gamma_{0},\gamma_{1}$ 是固定端点同伦的，那么

$$
\begin{gather}
\int_{\gamma_{0}} f=\int_{\gamma_{1}} f
\end{gather}
$$

另一方面，那些在其上的解析函数沿着任意闭曲线的积分均为零的区域也可以用同伦的语言来描述：

**定义 3.3.10** 单连通的（simply connected）

开集 $G$ 是**单连通的**，如果 $G$ 是连通的，并且 $G$ 中的任意闭曲线都同伦于零。

这给出了 Cauchy 定理的又一个版本。

**定理 3.3.11** Cauchy 定理 IV

如果 $G$ 是一个单连通域，那么对任意解析函数 $f\colon G\to \mathbb{C}$ 和 $G$ 中的可求长闭曲线 $\gamma$，有

$$
\begin{gather}
\int_{\gamma}f=0
\end{gather}
$$

根据定理 3.3.3，任何星状开集都是单连通域。此外，之前我们已经证明，如果解析函数 $f$ 在区域 $G$ 上有原函数，那么 $f$ 沿着任意可求长闭曲线的积分均为零。鉴于此，下面的结果应该不会让人感到太意外。

**定理 3.3.12**

如果 $G$ 是单连通域，$f\colon G\to \mathbb{C}$ 是解析函数，那么 $f$ 在 $G$ 上有原函数。

**证明**

固定 $a \in G$，设 $\gamma_{1},\gamma_{2}$ 是 $G$ 中任意两条从 $a$ 到 $z \in G$ 的可求长曲线。则根据 Cauchy 定理 IV 知

$$
\begin{gather}
0=\int_{\gamma_{1}-\gamma_{2}} f=\int_{\gamma_{1}}f-\int_{\gamma_{2}} f
\end{gather}
$$

于是我们可以定义 $F(z)=\int_{\gamma}f$，其中 $\gamma$ 是任意从 $a$ 到 $z$ 的可求长曲线。我们断言 $F$ 是 $f$ 的原函数。

设 $z_{0}\in G$ 和 $r>0$ 使得 $B(z_{0},r)\subset G$，则令 $\gamma$ 为从 $a$ 到 $z_{0}$ 的一条曲线。对于 $z \in B(z_{0},r)$，令 $\gamma_{z}=\gamma+[z_{0},z]$，则我们有

$$
\begin{gather}
\dfrac{F(z)-F(z_{0})}{z-z_{0}} = \dfrac{1}{z-z_{0}} \int_{[z_{0},z]} f
\end{gather}
$$

接下来仿照 Morera 定理的证明过程，即证 $F'=f$.

单连通性的一个相对较出乎意料的推论是，$\log f(z)$ 的一个分支可以定义在一个单连通域上，其中 $f$ 是解析函数且永不为零。

**定理 3.3.13**

设 $G$ 是单连通域，$f\colon G\to \mathbb{C}$ 是一个解析函数，满足 $f(z)\neq 0$ 对任意 $z \in G$ 成立。则存在解析函数 $g\colon G\to \mathbb{C}$ 使得 $f(z)=\exp g(z)$. 如果 $z_{0}\in G$ 且 $e^{w_{0}}=f(z_{0})$，我们可以选取 $g$ 使得 $g(z_{0})=w_{0}$.

**证明**

由于 $f$ 永不消失，故 $\dfrac{f'}{f}$ 在 $G$ 上解析，因此，根据定理 3.3.12，它在 $G$ 上有原函数 $g_{1}$. 令 $h(z)=\exp g_{1}(z)$，则 $h$ 是解析函数且永不消失，因而 $\dfrac{f}{h}$ 解析，并且其导数是

$$
\begin{gather}
\dfrac{hf'-fh'}{h^{2}}
\end{gather}
$$

由于 $h'=g_{1}'h$，故 $hf'-fh'=0$，因此 $\dfrac{f}{h}=c$ 为常数，从而

$$
\begin{gather}
f(z)=c\exp g_{1}(z)=\exp(g_{1}(z)+c')
\end{gather}
$$

其中 $c'$ 是常数。取 $g(z)=g_{1}(z)+c'+2\pi ik$ 并选取 $c'$ 和整数 $k$ 使得 $g(z_{0})=w_{0}$，这就完成了证明。

让我们强调一下，单连通性的假设属于拓扑学范畴，这一假设被用于得出一些分析学的基本结论。这最后三个定理不仅都是单连通性的推论，而且它们与单连通性是等价的。这一结论我们将在后续的章节进行证明。

我们以一个定义结束本节。

**定义 3.3.14** 零调/同调于零（homologous to zero）

设 $\gamma$ 是开集 $G$ 上的可求长闭曲线，我们称 $\gamma$ **同调于零**，记作 $\gamma \approx 0$，如果 $n(\gamma,w)=0$ 对任意 $w \in \mathbb{C}\setminus G$ 成立。

利用这一定义，我们便可将 Cauchy 定理 I 表述为：如果 $\gamma$ 同调于零，那么 $\int_{\gamma}f=0$. 这也是为什么 Cauchy 定理 I 被称为“同调版本”。相应地，Cauchy 定理 II 就称为“同伦版本”。此外，定理 3.3.7 表明，$\gamma \sim 0$ 蕴含 $\gamma \approx 0$，但反之则不然。因此，同调版本的 Cauchy 定理具有更强的普遍性。

# Section 4: 零点计数与开映射定理

本节我们将给出一些 Cauchy 定理的应用。我们将展示如何计算曲线所围成区域内部零点的个数，并且，利用解析函数零点的信息，我们可以证明一个非常值解析函数是**开映射**，即函数将开集映射到开集。

上一章中我们已经证明，如果解析函数 $f$ 满足 $f(a)=0$，那么我们可以将其写成 $f(z)=(z-a)^{m}g(z)$，其中 $g(a)\neq 0$. 假设 $f$ 在区域 $G$ 上解析，其零点是 $a_{1},\dots,a_{m}$（其中一些 $a_{k}$ 会因为零点的重数而重复）。于是我们可以将 $f$ 表示为 $f(z)=(z-a_{1})\cdots(z-a_{m})g(z)$，其中 $g$ 在 $G$ 上解析且永不为零。应用导数的乘积法则得到

$$
\begin{gather}
\dfrac{f'(z)}{f(z)}=\dfrac{1}{z-a_{1}}+\dots+\dfrac{1}{z-a_{m}} +\dfrac{g'(z)}{g(z)}
\end{gather}
$$

对 $z\neq a_{1},\dots,a_{m}$ 成立。

**定理 3.4.1**

设 $G$ 是一个区域，解析函数 $f\colon G\to \mathbb{C}$ 具有零点 $a_{1},\dots,a_{m}$（根据重数而重复）。如果 $\gamma$ 是 $G$ 中不经过任何一个 $a_{k}$ 的可求长闭曲线，$\gamma \approx 0$，则

$$
\begin{gather}
\dfrac{1}{2\pi i} \int_{\gamma} \dfrac{f'(z)}{f(z)}\mathrm{d} z= \sum_{k=1}^{m} n(\gamma,a_{k})
\end{gather}
$$

**证明**

如果 $g$ 在 $G$ 上永不为零，那么 $\dfrac{g'}{g}$ 解析，从而由 Cauchy 定理得 $\int_{\gamma}g' /g=0$. 于是根据卷绕数的定义即证。

将上述定理中的 $f$ 替换为 $f-\alpha$，其中 $\alpha \in \mathbb{C}$，我们即得

**定理 3.4.2**

设 $G$ 是一个区域，$f\colon G\to \mathbb{C}$ 是解析函数，$a_{1},\dots,a_{m}$ 是方程 $f(z)=\alpha$ 的根（根据重数而重复）。如果 $\gamma$ 是 $G$ 中不经过任何一个 $a_{k}$ 的可求长闭曲线，$\gamma \approx 0$，则

$$
\dfrac{1}{2\pi i} \int_{\gamma} \dfrac{f'(z)}{f(z)-\alpha} \mathrm{d} z=\sum_{k=1}^{m} n(\gamma,a_{k})
$$

注意，方程 $f(z)=\alpha$ 可能有无穷多个根。然而，定理 2.3.8 表明，这些根的极限点必定位于 $G$ 的边界上，否则 $f=\alpha$ 为常值函数。因此，由于 $\gamma$ 位于 $G$ 的内部且 $\gamma \approx 0$，因此最多只会有有限个 $a_{k}$ 满足 $n(\gamma,a_{k})\neq 0$.

下面我们给出一个例子。设 $\gamma\colon[0,1]\to G$ 是一条可求长闭曲线，$\gamma \approx 0$，假设 $f\colon G\to \mathbb{C}$ 是解析函数，则 $\sigma=f\circ\gamma$ 也是一条可求长闭曲线。令 $\alpha$ 是一个复数，$\alpha \not\in \{ \sigma \}=f[\{ \gamma \}]$，我们来计算 $n(\sigma,\alpha)$：

$$
\begin{align}
n(\sigma,\alpha) &= \dfrac{1}{2\pi i} \int_{\sigma} \dfrac{\mathrm{d} w}{w-\alpha} \\
&= \dfrac{1}{2\pi i} \int_{\gamma} \dfrac{f'(z)}{f(z)-\alpha} \mathrm{d} z \\
&= \sum_{k=1}^{m} n(\gamma,a_{k})
\end{align}
$$

其中 $a_{k}$ 是 $f(z)=\alpha$ 的根。

现在，如果 $\beta \in \mathbb{C}\setminus\{ \sigma \}$ 位于与 $\alpha$ 相同的 $\mathbb{C}\setminus\{ \sigma \}$ 的连通分量中，则 $n(\sigma,\alpha)=n(\sigma,\beta)$，也即

$$
\begin{gather}
\sum_{k} n(\gamma,z_{k}(\alpha))=\sum_{j} n(\gamma,z_{j}(\beta))
\end{gather}
$$

其中 $z_{k}(\alpha)$ 和 $z_{j}(\beta)$ 分别是 $f(z)=\alpha$ 和 $f(z)=\beta$ 的根。如果我们能够选取 $\gamma$ 使得 $n(\gamma,z_{k}(\alpha))=1$ 对每个 $k$ 成立，那么我们可知至少有一个 $j$ 使得 $n(\gamma,z_{j}(\beta))=1$，即 $\gamma$ 的内部至少有一个点使得 $f(z)=\beta$. 由于 $\beta$ 是任意的，故 $f[G]$ 包含了 $\alpha$ 所在的 $\mathbb{C}\setminus f[\{ \gamma \}]$ 的连通分量。此外，我们还能够得到关于方程 $f(z)=\beta$ 根的数量的信息。这一过程能够用来证明以下的结论，这一结果不仅本身具有重要意义，还将得出**开映射定理**作为推论。

**定理 3.4.3**

设 $f$ 在 $B(a,R)$ 上解析，$\alpha=f(a)$，如果 $f(z)-\alpha$ 在 $a$ 处有一个重数为 $m$ 的零点，则存在 $\varepsilon>0$ 和 $\delta>0$ 使得当 $|\zeta-\alpha|<\delta$ 时，方程 $f(z)=\zeta$ 在 $B(a,\varepsilon)$ 内有 $m$ 个单根。

方程 $f(z)=\zeta$ 的一个**单根**（simple root）是 $f(z)-\zeta$ 的一个重数为 $1$ 的零点。注意到上述定理的一个推论是 $B(\alpha,\delta)\subset f[B(a,\varepsilon)]$，并且 $f(z)-\alpha$ 在 $a$ 处具有有限重数的零点保证了 $f$ 不是常值函数。

**证明**

由于解析函数的零点是孤立的，故我们可以选取 $\varepsilon<R /2$ 使得 $f(z)=\alpha$ 在 $0<|z-a|<2\varepsilon$ 时没有根，并且 $f'(z)\neq 0$ 对这些 $z$ 成立。令 $\gamma(t)=a+\varepsilon e^{2\pi it}$，$0\leq t\leq 1$，并取 $\sigma=f\circ\gamma$. 由于 $\alpha \not\in \{ \sigma \}$，故有 $\delta>0$ 使得 $B(\alpha,\delta)\cap \{ \sigma \}=\varnothing$，因此，$B(\alpha,\delta)$ 包含于 $\alpha$ 所在的 $\mathbb{C}\setminus\{ \sigma \}$ 的连通分量中，即，当 $|\alpha-\zeta|<\delta$ 时有

$$
\begin{gather}
n(\sigma,\alpha)=n(\sigma,\zeta)=\sum_{k} n(\gamma,z_{k}(\zeta))=m
\end{gather}
$$

但由于 $n(\gamma,z_{k}(\zeta))\leq 1$，故 $B(a,\varepsilon)$ 内必然包含 $f(z)=\zeta$ 的 $m$ 个根。又由于 $f'(z)\neq 0$ 对 $0<|z-a|<\varepsilon$ 成立，故这 $m$ 个根均为单根。

**定理 3.4.4** 开映射定理（Open Mapping Theorem）

设 $G$ 是一个区域，$f\colon G\to \mathbb{C}$ 是一个非常值解析函数，则对任意开集 $U\subset G$，$f[U]$ 是开集。

**证明**

如果 $U\subset G$ 是开集，要证 $f[U]$ 是开集，我们只需证明对任意 $a \in U$，存在 $\delta>0$ 使得 $B(\alpha,\delta)\subset f[U]$，其中 $\alpha=f(a)$. 而定理 3.4.3 表明我们可以找到 $\varepsilon>0$ 和 $\delta>0$ 使得 $B(\alpha,\delta)\subset f[B(a,\varepsilon)]\subset f[U]$，这就完成了证明。

具有以上性质的函数 $f$ 称为**开映射**（open map）。如果 $f$ 是一个双射，那么我们可以定义它的反函数 $f^{-1}$ 为 $f\circ f^{-1}(z)=f^{-1}\circ f(z)=z$，于是我们可以证明，$f^{-1}$ 连续当且仅当 $f$ 是开映射，因为 $(f^{-1})^{-1}[U]=f[U]$.

**定理 3.4.5**

设 $G$ 是区域，$f\colon G\to\Omega$ 解析并且是双射，则 $f^{-1}\colon\Omega\to G$ 是解析的，并且 $(f^{-1})'(w)=f'(z)^{-1}$，其中 $w=f(z)$.

**证明**

根据开映射定理，$f^{-1}$ 连续并且 $\Omega$ 是开集。由于 $f^{-1}(f(z))=z$，根据定理 1.3.7 即证 $f^{-1}$ 解析且 $(f^{-1})'(f(z))=f'(z)^{-1}$.

# Section 5: 全纯函数

在第一章我们就提到，全纯函数，即那些在开集上复可微的函数，与解析函数是同一类函数。现在，我们终于可以来证明这一断言，从而在这之前的所有关于解析函数的定理均可将条件弱化为全纯性。

**定理 3.5.1** Goursat 定理

设 $G\subset \mathbb{C}$ 是开集，$f\colon G\to \mathbb{C}$ 是一个全纯函数，则 $f$ 在 $G$ 上解析。

**证明**

我们只需证明 $f'$ 在 $G$ 中的任意圆盘上连续，因此我们可以不失一般性地假设 $G$ 是一个圆盘。下面我们将利用 Morera 定理来证明 $f$ 解析，即，我们将证明 $\int_{T}f=0$ 对任意三角路径 $T$ 成立。

设 $T=[a,b,c,a]$，我们记 $\Delta$ 为 $T$ 和它的内部构成的三角形闭集，注意到 $T=\partial\Delta$. 现在，我们根据 $\Delta$ 三边的中点将其划分为四个小三角形 $\Delta_{j}$，$1\leq j\leq 4$，并且，给予边界 $T_{j}=\partial\Delta_{j}$ 适当的方向（如图所示），我们可以使

$$
\begin{gather}
\int_{T} f=\sum_{j=1}^{4} \int_{T_{j}} f
\end{gather}
$$

![](3-3.png)

在这四条路径中，存在路径 $T^{(1)}$，满足 $\left\lvert  \int_{T^{(1)}} f  \right\rvert\geq \left\lvert  \int_{T_{j}} f  \right\rvert$ 对 $1\leq j\leq 4$ 成立。此外，每个 $T_{j}$ 的长度 $\ell(T_{j})=\dfrac{1}{2}\ell(T)$，直径 $\mathrm{diam}\,\Delta_{j}=\dfrac{1}{2}\mathrm{diam}\,\Delta$，并且

$$
\begin{gather}
\left\lvert  \int_{T} f  \right\rvert \leq 4 \left\lvert  \int_{T^{(1)}} f  \right\rvert 
\end{gather}
$$

现在我们对 $T^{(1)}$ 做相同的操作，得到类似的三角形 $T^{(2)}$，根据归纳法，我们可得一系列三角路径 $T^{(n)}$ 使得，如果 $\Delta^{(n)}$ 是 $T^{(n)}$ 的内部构成的闭集，那么

$$
\begin{gather}
\Delta^{(1)} \supset \Delta^{(2)} \supset \cdots \\
\left\lvert  \int_{T^{(n)}} f  \right\rvert \leq 4 \left\lvert  \int_{T^{(n+1)}} f  \right\rvert  \\
\ell(T^{(n+1)})=\dfrac{1}{2}\ell(T^{(n)}) \\
\mathrm{diam}\,\Delta^{(n+1)}=\dfrac{1}{2} \mathrm{diam}\,\Delta^{(n)}
\end{gather}
$$

这些等式表明

$$
\begin{gather}
\left\lvert  \int_{T} f  \right\rvert \leq 4^{n} \left\lvert  \int_{T^{(n)}} f  \right\rvert  \\
\ell(T^{(n)}) = \dfrac{1}{2^{n}} \ell, \quad \ell=\ell(T) \\
\mathrm{diam}\,\Delta^{(n)}=\dfrac{1}{2^{n}} d, \quad d=\mathrm{diam}\,\Delta
\end{gather}
$$

由于每个 $\Delta^{(n)}$ 是闭集，于是根据 Cantor 定理，集合 $\bigcap_{n=1}^{\infty}\Delta^{(n)}$ 是单点集，记作 $\{ z_{0} \}$.

令 $\varepsilon>0$，由于 $f$ 在 $z_{0}$ 处可微，故存在 $\delta>0$ 使得 $B(z_{0},\delta)\subset G$ 且对于 $0<|z-z_{0}|<\delta$ 有

$$
\begin{gather}
\left\lvert  \dfrac{f(z)-f(z_{0})}{z-z_{0}}-f'(z_{0})  \right\rvert <\varepsilon
\end{gather}
$$

等价地，我们有

$$
\begin{gather}
\lvert f(z)-f(z_{0})-f'(z_{0})(z-z_{0}) \rvert <\varepsilon|z-z_{0}|
\end{gather}
$$

对 $|z-z_{0}|<\delta$ 成立。选取 $n$ 使得 $\mathrm{diam}\,\Delta^{(n)}<\delta$，由于 $z_{0}\in\Delta^{(n)}$，这表明 $\Delta^{(n)}\subset B(z_{0},\delta)$，从而 Cauchy 定理给出 $0=\int_{T^{(n)}}\mathrm{d}z=\int_{T^{(n)}}z\mathrm{d}z$. 因此

$$
\begin{align}
\left\lvert  \int_{T^{(n)}} f  \right\rvert &= \left\lvert  \int_{T^{(n)}} (f(z)-f(z_{0})-f'(z_{0})(z-z_{0})) \mathrm{d} z  \right\rvert  \\
&\leq \varepsilon \int_{T^{(n)}} |z-z_{0}||\mathrm{d} z| \\
&\leq \varepsilon (\mathrm{diam}\, \Delta^{(n)}) \ell(T^{(n)}) \\
&= \dfrac{\varepsilon d\ell}{4^{n}}
\end{align}
$$

从而我们有

$$
\begin{align}
\left\lvert  \int_{T} f  \right\rvert \leq 4^{n} \left\lvert  \int_{T^{(n)}} f  \right\rvert =\varepsilon d\ell
\end{align}
$$

即证 $\int_{T}f=0$，这就完成了证明。

鉴于以上定理，在后续的章节中我们将“全纯函数”与“解析函数”作为同义词使用。