我们已经看到了很多连续函数的例子，本章中，我们将研究连续函数所拥有的其它性质，特别是定义在有界闭区间上的连续函数。这也是 Heine-Borel 定理发挥重要作用的地方。

# Section 1: 闭区间上的连续函数

首先我们给出有界函数的定义。

**定义 10.1.1** 有界的（bounded），上界（upper bound），下界（lower bound）

设 $X\subset \mathbb{R}$，函数 $f\colon X\to \mathbb{R}$，如果存在实数 $M>0$ 使得对任意 $x \in X$ 有 $|f(x)|\leq M$，则称 $f$ 是**有界的**。实数 $U$ 是 $f$ 的一个**上界**，如果对任意 $x \in X$ 有 $f(x)\leq U$；实数 $L$ 是 $f$ 的一个**下界**，如果对任意 $x \in X$ 有 $f(x)\geq L$.

显然，函数 $f$ 是有界的当且仅当 $f$ 有上界和下界，当且仅当 $f$ 的值域 $f[X]$ 是一个有界集合。

并非所有连续函数都是有界的，例如定义在 $(0,1)$ 上的函数 $x\mapsto \dfrac{1}{x}$ 是无界的。然而，我们可以证明，定义在闭区间上的连续函数一定是有界函数。

**定理 10.1.2**

设实数 $a<b$，函数 $f\colon [a,b]\to \mathbb{R}$ 是连续函数，则 $f$ 是有界函数。

**证明**

设 $x_{0}\in[a,b]$，根据连续性有 $\lim_{ x \to x_{0};x \in[a,b] }f(x)=f(x_{0})$，取 $\varepsilon=1$，则存在 $\delta_{x_{0}}>0$ 使得对任意 $d(x,x_{0})<\delta_{x_{0}}$ 的 $x \in[a,b]$ 有 $d(f(x),f(x_{0}))<\varepsilon$，于是对任意 $x \in(x_{0}-\delta_{x_{0}},x_{0}+\delta_{x_{0}})$ 有 $|f(x)|\leq|f(x_{0})|+1$. 现在构造开覆盖

$$
\mathcal{O} = \{ O_{x}=(x-\delta_{x},x+\delta_{x}) \mid x \in[a,b] \}
$$

则 $[a,b]\subset \bigcup \mathcal{O}$，根据 Heine-Borel 定理，存在有限覆盖 $\{ O_{x_{1}},\dots,O_{x_{n}} \}$，令 $M=\max_{1\leq i\leq n} |f(x_{i})|+1$，则对任意 $x \in[a,b]$ 有 $|f(x)|\leq M$，这就完成了证明。

事实上，定理 10.1.2 可以做进一步加强：我们不仅可以证明 $f$ 是有界的，还能证明 $f$ 在 $[a,b]$ 上有最大值和最小值。

**定义 10.1.3** 最大值（maximum），最小值（minimum）

设 $X\subset \mathbb{R}$，函数 $f\colon X\to \mathbb{R}$，$x_{0}\in X$，称 $f$ 在 $x_{0}$ 处达到**最大值**，如果对任意 $x \in X$ 有 $f(x)\leq f(x_{0})$；称 $f$ 在 $x_{0}$ 处达到**最小值**，如果对任意 $x \in X$ 有 $f(x)\geq f(x_{0})$.

上述定义中的最大值、最小值通常被称为全局最大值、最小值，这是为了与后续的局部最大值、最小值区分，这两个概念将在微分学中引入。

**定理 10.1.4** 最值定理（extreme value theorem）

设实数 $a<b$，函数 $f\colon [a,b]\to \mathbb{R}$ 是连续函数，那么存在 $x_{\mathrm{max}}\in X$ 使得 $f$ 在 $x_{\mathrm{max}}$ 处达到最大值，并且存在 $x_{\mathrm{min}}\in X$ 使得 $f$ 在 $x_{\mathrm{min}}$ 处达到最小值。

**证明**

我们只证明存在最大值，最小值的情况同理。根据定理 10.1.2，$f$ 是有界的，即 $f$ 的值域 $f[a,b]$ 有界，从而存在实数 $m=\sup f[a,b]$，我们只需证明存在一点 $x_{\mathrm{max}}\in[a,b]$ 使得 $f(x_{\mathrm{max}})=m$ 即可。

根据上确界的性质，集族

$$
\left\{  x \in [a,b] \mid m-\dfrac{1}{n}< f(x)\leq m  \right\},n \in \mathbb{N}\setminus \{ 0 \}
$$

中每个集合都非空，应用选择公理从中选出序列 $(x_{n})_{n=1}^{\infty}$，根据 Heine-Borel 定理，存在一个子序列 $(x_{n_{j}})_{j=1}^{\infty}$ 收敛于 $x_{\mathrm{max}}\in[a,b]$，又有

$$
m\geq f(x_{n_{j}})> m-\dfrac{1}{n_{j}}\geq m-\dfrac{1}{j}
$$

因此 $f(x_{\mathrm{max}})=\lim_{ j \to \infty }f(x_{n_{j}})=m$，这就完成了证明。

现在我们知道了，有界闭区间上的连续函数至少一次达到了它的最大值和最小值，然而对于开区间或者无界区间则不是这样。这就更显示出了 Heine-Borel 定理的特殊性。

下面，我们再来考虑介于最大值和最小值之间的值，事实证明，闭区间上的连续函数可以达到最大值与最小值之间的每一个值。

**定理 10.1.5** 介值定理（intermediate value theorem）

设实数 $a<b$，函数 $f\colon [a,b]\to \mathbb{R}$ 是连续函数，设实数 $y$ 满足 $f(a)\leq y\leq f(b)$ 或者 $f(b)\leq y\leq f(a)$，则存在 $c \in[a,b]$ 使得 $f(c)=y$.

**证明**

不妨假设 $f(a)\leq y\leq f(b)$ 成立，另一种情况同理。如果 $y=f(a)$ 或者 $y=f(b)$，那么取 $c=a$ 或 $c=b$ 即可。因此设 $f(a)<y<f(b)$.

令 $E=\{ x \in[a,b] \mid f(x)<y \}$，则 $E$ 有界且非空，于是有 $c=\sup E$. 由于 $y<f(b)$，故 $c\leq b$，又 $a \in E$，故 $a\leq c$，从而 $c \in[a,b]$，因此只需证明 $f(c)=y$.

设整数 $n\geq 1$，于是存在 $x_{n}\in E$ 使得 $c-\dfrac{1}{n}<x_{n}\leq c$，则有 $\lim_{ n \to \infty }x_{n}=c$，根据 $f$ 的连续性以及 $f(x_{n})<c$ 就有 $f(c)=\lim_{ n \to \infty }f(x_{n})\leq y$.

由于 $c\neq b$，故 $c<b$，从而存在 $N$ 使得对任意 $n>N$ 有 $c+\dfrac{1}{n}<b$，由于 $c=\sup E$，故 $f\left( c+\dfrac{1}{n} \right)\geq y$，两边对 $n$ 取极限，则有 $f(c)\geq y$，因此 $f(c)=y$，这就完成了证明。

将介值定理与最值定理结合，就有了以下推论：

**定理 10.1.6**

设实数 $a<b$，函数 $f\colon [a,b]\to \mathbb{R}$ 是连续函数，$M$ 是 $f$ 的最大值，$m$ 是 $f$ 的最小值，则 $f$ 的值域 $f[a,b]=[m,M]$.

上述定理的证明只需注意到 $f$ 在 $E\subset[a,b]$ 上也是连续函数，把 $E$ 取为 $[x_{\mathrm{min}},x_{\mathrm{max}}]$ 或者 $[x_{\mathrm{max}},x_{\mathrm{min}}]$ 即可。

介值定理给出了一种求连续函数零点的方法：二分法。任取一段区间 $[a,b]$，如果 $f(a)f(b)<0$，那么在 $[a,b]$ 中一定有零点，将 $[a,b]$ 分成两半 $[a,c],[c,b]$，如果 $f(a)f(c)<0$，那么在 $[a,c]$ 中有零点，这就将范围缩小了一半，这种方法可以快速地逼近零点。

# Section 2: 单调函数

现在我们考虑一类与连续函数类似但不同的函数：单调函数。

**定义 10.2.1** 单调函数（monotone function）

设 $X\subset \mathbb{R}$，函数 $f\colon X\to \mathbb{R}$，称 $f$ 是**单调递增的**，如果对任意 $x,y \in X$ 有 $x<y\implies f(x)\leq f(y)$；称 $f$ 是**单调递减的**，如果对任意 $x,y \in X$ 有 $x<y \implies f(x)\geq f(y)$.

把不等号都换成严格不等号就得到了严格单调递增、递减的定义。

单调函数自动地满足最值定理，它的最值总是在区间 $[a,b]$ 的端点处达到。但是单调函数不满足介值定理，因为单调函数可能存在非常多的间断点（其中大多数都是跳跃间断点）。

如果一个函数既是连续的，也是严格单调的，那么它就有一些非常好的性质，特别地，它是一个双射。

**定理 10.2.2**

设实数 $a<b$，函数 $f\colon [a,b]\to \mathbb{R}$ 连续且严格单调递增，那么 $f$ 是从 $[a,b]$ 到 $[f(a),f(b)]$ 的双射，并且其反函数 $f^{-1}\colon [f(a),f(b)]\to[a,b]$ 也连续且严格单调递增。

**证明**

由于 $f$ 严格单调递增，因此 $f$ 是单射，并且 $f$ 的最小值是 $f(a)$，最大值是 $f(b)$，根据定理 10.1.6 知 $f\colon [a,b]\to[f(a),f(b)]$ 是满射，因此 $f$ 是双射。

设 $f(x)<f(y)$，假设 $x>y$，则 $f(x)>f(y)$，矛盾，因此 $x<y$，从而 $f^{-1}$ 严格单调递增。下面我们用连续的 $\varepsilon-\delta$ 定义证明 $f^{-1}$ 的连续性。

设 $x_{0} \in[a,b]$，$f$ 在 $x_{0}$ 处连续，则对任意 $\varepsilon>0$，存在 $\delta>0$ 使得对任意 $d(x,x_{0})<\delta$ 的 $x \in[a,b]$ 有 $d(f(x),f(x_{0}))<\varepsilon$，特别地，我们有 $f[(x_{0}-\delta,x_{0}+\delta)]\subset(f(x_{0})-\varepsilon,f(x_{0})+\varepsilon)$，由于 $f$ 严格递增，故可以取 $\varepsilon_{1}>0$ 使得 $(f(x_{0})-\varepsilon_{1},f(x_{0})+\varepsilon_{1})\subset f[(x_{0}-\delta,x_{0}+\delta)]$，并且对任意 $0<\delta_{1}<\delta$ 都有 $\varepsilon_{1}$ 使得对任意 $d(f(x),f(x_{0}))<\varepsilon_{1}$ 的 $f(x)$ 有 $d(x,x_{0})<\delta_{1}$，于是 $f^{-1}$ 在 $f(x_{0})$ 处连续，这就完成了证明。

对于严格单调递减函数也有类似的定理，其证明是类似的。这个定理在后续的反函数微分法中会用到。

# Section 3: 一致连续

我们之前看到，闭区间上的连续函数是有界的，但开区间上的连续函数不一定有界。以函数 $f(x)=\dfrac{1}{x}$ 为例，我们来分析这种现象。我们假设函数 $f$ 定义在 $(0,1)$ 上，取 $x_{0}\in(0,1)$，由于 $f$ 在 $x_{0}$ 处连续，故对任意 $\varepsilon>0$，存在 $\delta>0$ 使得当 $d(x,x_{0})<\delta$ 时有 $d(f(x),f(x_{0}))<\varepsilon$.

我们知道，导致 $f$ 无界的原因就是它在接近 $0$ 时的表现，所以我们就让 $x_{0}$ 接近 $0$，可以发现：对于同样的 $\varepsilon$，$x_{0}$ 越接近 $0$，它所对应的 $\delta$ 就越小。我们可以预料到 $x_{0}$ 趋于 $0$ 时的情况：当 $x_{0}$ 无限接近 $0$ 时，$\delta$ 无限趋于 $0$，换言之，当 $x_{0}$ 趋于 $0$ 时，$f$ 变得“越来越不连续”。事实上，$f$ 在 $0$ 处的确有一个无穷间断点。

然而，有些其它函数的性质与 $x\mapsto \dfrac{1}{x}$ 不同，例如函数 $x\mapsto 2x$，对于不同的 $x_{0}$，只要 $\varepsilon$ 相同，那么它对应的 $\delta$ 就是相同的。这种一致性启发我们给出下面的定义：

**定义 10.3.1** 一致连续（uniformly continuous）

设 $X\subset \mathbb{R}$，函数 $f\colon X\to \mathbb{R}$，称 $f$ **一致连续**，如果对任意 $\varepsilon>0$，存在 $\delta>0$ 使得对任意满足 $d(x',x'')<\delta$ 的 $x',x''\in X$ 有 $d(f(x'),f(x''))<\varepsilon$.

我们之前看到附着点以及连续的概念都有“序列化”的表述，对于一致连续，同样也有序列表述，它涉及序列的等价性。回忆一下，两个序列 $(a_{n}),(b_{n})$ 等价当且仅当 $\lim_{ n \to \infty }(a_{n}-b_{n})=0$.

**定理 10.3.2**

设 $X\subset \mathbb{R}$，函数 $f\colon X\to \mathbb{R}$，则以下命题等价：

1. $f$ 一致连续
2. 如果 $X$ 上元素的序列 $(x_{n}'),(x_{n}'')$ 等价，则序列 $(f(x_{n}')),(f(x_{n}''))$ 等价

**证明**

先设 $f$ 一致连续，则对任意 $\varepsilon>0$，存在 $\delta>0$ 使得对任意满足 $d(x',x'')<\delta$ 的 $x',x''\in X$ 有 $d(f(x'),f(x''))<\varepsilon$，由于 $(x_{n}')$ 等价于 $(x_{n}'')$，故存在 $N$ 使得对任意 $n>N$ 有 $d(x_{n}',x_{n}'')<\delta$，从而 $d(f(x_{n}'),f(x_{n}''))<\varepsilon$，于是序列 $(f(x_{n}'))$ 等价于 $(f(x_{n}''))$.

下设 $f$ 不一致连续，则存在 $\varepsilon_{0}>0$ 对任意 $\delta>0$ 都有 $x',x''\in X$ 使得 $d(x',x'')<\delta$ 且 $d(f(x'),f(x''))\geq\varepsilon_{0}$，设整数 $n\geq 1$，取 $\delta_{n}=\dfrac{1}{n}$，将 $\delta_{n}$ 对应的 $x',x''$ 取为 $x_{n}',x_{n}''$，则序列 $(x_{n}')$ 等价于 $(x_{n}'')$，但是 $f(x_{n}')$ 与 $f(x_{n}'')$ 不等价。这就完成了证明。

上述定理表明：一致连续函数将等价序列映射为等价序列，而连续函数将收敛序列映射为收敛序列。为了找到它们之间的联系，我们需要注意到序列 $(x_{n})$ 收敛于 $x$ 当且仅当序列 $(x_{n})$ 等价于常值序列 $(x)$，因此，一致连续是比连续更强的条件，并且一致连续可以推出连续。

一致连续的另一个性质如下：

**定理 10.3.3**

设 $X\subset \mathbb{R}$，函数 $f\colon X\to \mathbb{R}$ 一致连续，并且 $(x_{n})$ 是 $X$ 上的 Cauchy 序列，则序列 $(f(x_{n}))$ 也是 Cauchy 序列。

**证明**

根据定义，对任意 $\varepsilon>0$，存在 $\delta>0$ 使得对任意 $d(x',x'')<\delta$ 的 $x',x''\in X$ 有 $d(f(x'),f(x''))<\varepsilon$，由于 $(x_{n})$ 是 Cauchy 序列，故存在 $N$ 使得对任意 $n,m>N$ 有 $d(x_{n},x_{m})<\delta$，从而 $d(f(x_{n}),f(x_{m}))<\varepsilon$，即证。

根据上述定理，我们有推论：

**定理 10.3.4**

设 $X\subset \mathbb{R}$，函数 $f\colon X\to \mathbb{R}$ 一致连续，$x_{0}$ 是 $X$ 的极限点，那么极限 $\lim_{ x \to x_{0};x \in X }f(x)$ 存在。

**证明**

取 $X\setminus \{ x_{0} \}$ 中收敛于 $x_{0}$ 的序列 $(x_{n})$，则 $(x_{n})$ 是 Cauchy 序列，从而 $(f(x_{n}))$ 也是 Cauchy 序列，于是收敛。下面我们要证所有序列 $(f(x_{n}))$ 收敛于同一个极限。任取另一个收敛于 $x_{0}$ 的序列 $(y_{n})$，则 $(x_{n})$ 等价于 $(y_{n})$，根据一致连续的性质，序列 $f(x_{n})$ 等价于 $f(y_{n})$，这就完成了证明。

下面我们可以证明一致连续函数将有界集映射到有界集。

**定理 10.3.5**

设 $X\subset \mathbb{R}$，函数 $f\colon X\to \mathbb{R}$ 一致连续，$E\subset X$ 是有界集合，那么 $f[E]$ 也是有界集合。

**证明**

假设 $f[E]$ 不是有界集，那么集族

$$
\{ x \in E \mid |f(x)| > n \},n \in \mathbb{N}
$$

中每个集合都非空，利用选择公理取出序列 $(x_{n})_{n=0}^{\infty}$，则序列 $(f(x_{n}))$ 是无界的。

由于 $E$ 是有界的，故序列 $(x_{n})$ 有界，从而存在一个收敛的子序列 $(x_{n_{j}})_{j=0}^{\infty}$，其极限为 $a$，它是 $X$ 的极限点，从而极限 $\lim_{ x \to a; x \in X }f(x)$ 存在，并且就等于 $\lim_{ j \to \infty }f(x_{n_{j}})$，但这与序列 $(f(x_{n_{j}}))$ 无界矛盾。

下面，我们来看闭区间上的连续函数，就像我们多次看到的一样，事实上闭区间上的连续函数就是一致连续函数。

**定理 10.3.6**

设实数 $a<b$，函数 $f\colon [a,b]\to \mathbb{R}$ 连续，则 $f$ 一致连续。

**证明**

假设 $f$ 不一致连续，那么存在两个等价的序列 $(x_{n}),(y_{n})$ 使得 $(f(x_{n}))$ 不等价于 $(f(y_{n}))$，于是存在 $\varepsilon_{0}>0$，对任意 $N$ 都有 $n>N$ 使得 $d(f(x_{n}),f(y_{n}))\geq\varepsilon_{0}$，构造集合

$$
E=\{ n \in \mathbb{N} \mid d(f(x_{n}),f(y_{n}))\geq \varepsilon_{0} \}
$$

于是 $E$ 是无限集，又 $E\subset \mathbb{N}$，故 $E$ 是可数集，从而有严格递增的双射 $h\colon \mathbb{N}\to E$ 使得对任意 $n \in \mathbb{N}$ 有 $d(f(x_{h(n)}),f(y_{h(n)}))\geq\varepsilon_{0}$.

由于 $(x_{h(n)})$ 是 $[a,b]$ 上的序列，根据 Heine-Borel 定理，存在一个收敛的子序列 $(x_{h(n)_{k}})_{k=0}^{\infty}$，设其极限为 $L$，由于 $(x_{n})$ 等价于 $(y_{n})$，故而 $(x_{h(n)_{k}})$ 等价于 $(y_{h(n)_{k}})$，从而 $\lim_{ k \to \infty }y_{h(n)_{k}}=L$.

由于 $f$ 连续，因此 $f$ 将收敛序列映射到收敛序列，从而

$$
\lim_{ k \to \infty } f(x_{h(n)_{k}})=\lim_{ k \to \infty } f(y_{h(n)_{k}})=f(L)
$$

这表明 $(f(x_{h(n)_{k}}))$ 与 $(f(y_{h(n)_{k}}))$ 等价，但这与 $d(f(x_{h(n)}),f(y_{h(n)}))\geq\varepsilon_{0}$ 矛盾，这表明 $f$ 一致连续。

最后，尽管一致连续性在加法、乘法等运算中无法保持，它仍然在复合运算中得以保持，如以下定理所示：

**定理 10.3.7**

设 $X,Y,Z\subset \mathbb{R}$，函数 $f\colon X\to Y,g\colon Y\to Z$ 都一致连续，则函数 $g\circ f\colon X\to Z$ 一致连续。

**证明**

对任意 $\varepsilon>0$，存在 $\delta>0$ 使得对任意 $d(y',y'')<\delta$ 的 $y',y''\in Y$ 有 $d(g(y'),g(y''))<\varepsilon$.

对于这个 $\delta$，存在 $\eta>0$ 使得对任意 $d(x',x'')<\eta$ 的 $x',x''\in X$ 有 $d(f(x'),f(x''))<\delta$，从而 $d(g\circ f(x'),g\circ f(x''))<\varepsilon$，这就完成了证明。