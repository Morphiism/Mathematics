现在我们将上一章的各种收敛概念应用到**大数定律**上，一个概率论中非常著名的定理，同时也是统计学的理论基础。大数定律与随机变量 $X_{n}$ 的部分和

$$
\begin{gather}
S_{n}=\sum_{j=1}^{n} X_{j}
\end{gather}
$$

有关。我们将给出多个不同版本的大数定律，尽管它们在一定程度上是相互重叠的。

# Section 1: 简单极限定理

在最经典的表述中，所谓的“弱大数定律”和“强大数定律”指的是在一定的条件下，依概率或者 a.s. 有

$$
\begin{gather}
\dfrac{S_{n}-\mathbb{E}(S_{n})}{n}\to 0
\end{gather}
$$

它有一个直接的推广：在一定条件下，依概率或 a.s. 有

$$
\begin{gather}
\dfrac{S_{n}-a_{n}}{b_{n}}\to 0
\end{gather}
$$

成立，其中 $(a_{n})$ 是一个实数序列而 $(b_{n})$ 是一个发散到 $\infty$ 的正数序列。

最简单的一种情况如下：设 $(Z_{n})$ 是一列随机变量，满足 $\mathbb{E}(Z_{n}^{2})\to 0$（i.e. $L^{2}$ 收敛），则 $Z_{n}\to 0$ 依概率，且有子序列 $Z_{n_{k}}\to 0$ a.s. 令 $Z_{n}=S_{n} / n$，则第一个结论就变成了

$$
\begin{gather}
\mathbb{E}(S_{n}^{2})=o(n^{2}) \implies \dfrac{S_{n}}{n}\to 0 \quad \text{依概率}
\end{gather}
$$

为研究何时能够达到这一条件，我们来进一步展开 $\mathbb{E}(S_{n}^{2})$：

$$
\begin{align}
\mathbb{E}\left( \left( \sum_{j=1}^{n} X_{j} \right)^{2} \right)=\sum_{j=1}^{n} \mathbb{E}(X_{j}^{2})+2\sum_{1\leq j<k\leq n} \mathbb{E}(X_{j}X_{k})
\end{align}
$$

观察到上述展开式中一共有 $n^{2}$ 项，因此即使每一项都一致有界（有共同的上界），我们也只能得到 $\mathbb{E}(S_{n}^{2})=O(n^{2})$，从而无法应用上面的定理。因此，接下来我们的目标就是引入一些合适的假设，使得交叉项 $\mathbb{E}(X_{j}X_{k})$ 足够小。下面是其中最简单的一个。

**定义 3.1.1** 不相关的（uncorrelated），正交的（orthogonal）

设 $(\Omega,\mathcal{F},\mathbb{P})$ 是概率空间，$X,Y$ 是具有有限二阶矩的随机变量，则称 $X,Y$ 是**不相关的**，如果 $\mathbb{E}(XY)=\mathbb{E}(X)\mathbb{E}(Y)$；称 $X,Y$ 是**正交的**，如果 $\mathbb{E}(XY)=0$.

一族随机变量 $\{ X_{t} \}_{t \in T}$ 称为是不相关的（或正交的），如果其中任意两个随机变量是不相关的（或正交的）。

通过简单的计算，我们可以注意到 $\mathbb{E}(XY)=\mathbb{E}(X)\mathbb{E}(Y)$ 等价于

$$
\begin{gather}
\mathbb{E}[(X-\mathbb{E}(X))(Y-\mathbb{E}(Y))]=0
\end{gather}
$$

左边的表达式通常称为 $X,Y$ 的**协方差**（covariance），该等式退化为 $\mathbb{E}(XY)=0$ 当且仅当 $\mathbb{E}(X)=\mathbb{E}(Y)=0$. 定义中的有限二阶矩看起来是不必要的，但是它保证了 $\mathbb{E}(XY)$ 以及 $\mathbb{E}(X),\mathbb{E}(Y)$ 的有限性（Holder 不等式），从而保证了良定性。最后我们指出一个显而易见的事实：如果 $X,Y$ 是独立的，那么 $X,Y$ 就是不相关的。

如果 $(X_{n})$ 是一列不相关的随机变量，那么 $(X_{n}-\mathbb{E}(X_{n}))$ 就是正交的，于是我们有

$$
\begin{gather}
\sigma^{2}(S_{n})=\mathbb{E}[(S_{n}-\mathbb{E}(S_{n}))^{2}]=\sum_{j=1}^{n} \sigma^{2}(X_{j})
\end{gather}
$$

这被称为“方差的可加性”。相反，对 $n=2$，可加性也可以推出 $X_{1},X_{2}$ 的不相关性。于是，在不相关的条件下，上述等式右边只剩下 $n$ 项，如果每一项都是一致有界的，那么我们可以得到 $\sigma^{2}(S_{n})=O(n)=o(n^{2})$，即证下面的定理：

**定理 3.1.2** Chebyshev 大数定律

设 $(\Omega,\mathcal{F},\mathbb{P})$ 是概率空间，$(X_{n})$ 是一列不相关的随机变量，其二阶矩是一致有界的，那么依 $L^{2}$ 范数（从而依概率）有

$$
\begin{gather}
\dfrac{S_{n}-\mathbb{E}(S_{n})}{n}\to 0
\end{gather}
$$

下一个结论由 Rajchman 给出，它指出，在同样的假设下，我们可以将收敛性加强为 a.s. 收敛。

**定理 3.1.3**

设 $(\Omega,\mathcal{F},\mathbb{P})$ 是概率空间，$(X_{n})$ 是一列不相关的随机变量，其二阶矩是一致有界的，那么有

$$
\begin{gather}
\dfrac{S_{n}-\mathbb{E}(S_{n})}{n} \to 0 \quad \text{a.s.}
\end{gather}
$$

**证明**

不失一般性地，我们设 $\mathbb{E}(X_{n})=0$，从而 $(X_{n})$ 是正交的。根据方差的可加性，我们有

$$
\begin{gather}
\mathbb{E}(S_{n}^{2})\leq Mn
\end{gather}
$$

其中 $M$ 是各 $\mathbb{E}(X_{j})$ 的一致上界。根据 Chebyshev 不等式，我们有

$$
\begin{gather}
\mathbb{P}(|S_{n}|> n\varepsilon)\leq \dfrac{Mn}{n^{2}\varepsilon^{2}}=\dfrac{M}{n\varepsilon^{2}}
\end{gather}
$$

如果对 $n$ 求和，那么右边的级数发散，因此我们考虑子序列 $(S_{n^{2}})$ 得

$$
\begin{gather}
\sum_{n=1}^{\infty} \mathbb{P}(|S_{n^{2}}|>n^{2}\varepsilon)\leq \sum_{n=1}^{\infty} \dfrac{M}{n^{2}\varepsilon^{2}}<\infty
\end{gather}
$$

于是根据 Borel-Cantelli 引理有

$$
\begin{gather}
\mathbb{P}(|S_{n^{2}}|>n^{2}\varepsilon\ \text{i.o.})=0
\end{gather}
$$

因此，对于几乎所有 $\omega \in\Omega$，都存在 $N$ 使得当 $n>N$ 时有 $\dfrac{|S_{n^{2}}(\omega)|}{n^{2}}\leq \varepsilon$，即

$$
\begin{gather}
\dfrac{S_{n^{2}}}{n^{2}}\to 0 \quad \text{a.s.}
\end{gather}
$$

为证明 $\dfrac{S_{n}}{n}\to 0$ a.s.，我们需要证明任意 $S_{k}$ 与其距离最近的 $S_{n^{2}}$ 的差别足够小，从而 $S_{n^{2}}$ 的收敛性可以推出 $S_{k}$ 的收敛性。我们定义

$$
\begin{gather}
D_{n}=\max_{n^{2}\leq k<(n+1)^{2}} |S_{k}-S_{n^{2}}|
\end{gather}
$$

于是根据 Cauchy-Schwarz 不等式有

$$
\begin{align}
\mathbb{E}(D_{n}^{2})&\leq \mathbb{E}\left( \left( \sum_{j=n^{2}+1}^{(n+1)^{2}-1} |X_{j}| \right)^{2} \right)\leq 2n \mathbb{E}\left( \sum_{j=n^{2}+1}^{(n+1)^{2}-1} X_{j}^{2}  \right) \\
&=2n \sum_{j=n^{2}+1}^{(n+1)^{2}-1} \mathbb{E}(X_{j}^{2})\leq 4n^{2}M
\end{align}
$$

从而根据 Chebyshev 不等式得

$$
\begin{gather}
\mathbb{P}(D_{n}>n^{2}\varepsilon)\leq \dfrac{4M}{n^{2}\varepsilon^{2}}
\end{gather}
$$

同理得到

$$
\begin{gather}
\dfrac{D_{n}}{n^{2}}\to 0 \quad \text{a.s.}
\end{gather}
$$

当 $n^{2}\leq k<(n+1)^{2}$ 时，根据不等式

$$
\begin{gather}
\dfrac{|S_{k}|}{k}\leq \dfrac{|S_{n^{2}}|+D_{n}}{n^{2}}
\end{gather}
$$

就完成了证明。

作为上述定理的一个应用，我们来给出概率论中的一个经典结果，它与所谓的**正规数**有关。称一个实数 $\omega \in[0,1]$ 是（以 10 为底）正规的，如果在它的 10 进制表示法

$$
\begin{gather}
\omega=0.x_{1}x_{2}\dots x_{n}\dots
\end{gather}
$$

中，每个数字出现的概率是均等的。这就是说，如果令 $N_{k}^{(n)}(\omega)$ 表示 $\omega$ 的前 $n$ 位小数中 $k$ 的数量，那么对任意 $0\leq k\leq 9$ 有

$$
\begin{gather}
\varphi_{k}(\omega)=\lim_{ n \to \infty } \dfrac{N_{k}^{(n)}(\omega)}{n}=\dfrac{1}{10}
\end{gather}
$$

有一些有理数不是正规的，因为它们最终会进入循环。然而，直观上来看，如果我们在 $[0,1]$ 上随机选取一个实数，那么几乎可以肯定它是一个正规数，这就是下面的定理的核心思想：

**定理 3.1.4** Borel 正规数定理

除了一个 Lebesgue 测度为零的 Borel 集外，每个 $[0,1]$ 中的实数都是正规的。

**证明**

考虑概率空间 $([0,1],\mathcal{B},m)$，其中 $m$ 是 Lebesgue 测度。对于一些实数来说，它有两种 10 进制表示：一种是末尾全是 0 的，另一种是末尾全是 9 的，我们将使用前一种表示方法。任取 $\omega \in[0,1]$，设

$$
\begin{gather}
\omega=0.\xi_{1}(\omega)\xi_{2}(\omega)\dots \xi_{n}(\omega)\dots
\end{gather}
$$

则 $(\xi_{n})$ 是一列独立的随机变量：事件 $\bigcap_{j=1}^{n}\{ \xi_{j}=c_{j} \}$ 是 $[0,1]$ 中的一段长度为 $1 / 10^{n}$ 的左闭右开区间，再根据

$$
\begin{gather}
m(\xi_{n}=k)= \dfrac{1}{10}, \quad k=0,1,\dots,9
\end{gather}
$$

即证。定义 $X_{n}$ 为集合 $\{ \omega \mid \xi_{n}(\omega)=k \}$ 的指示函数，则 $\mathbb{E}(X_{n})=1 / 10$，$\mathbb{E}(X_{n}^{2})=1 / 10$，并且当 $i\neq j$ 时有

$$
\begin{gather}
\mathbb{E}(X_{i}X_{j})=m(\xi_{i}=k,\xi_{j}=k)=m(\xi_{i}=k)m(\xi_{j}=k)=\mathbb{E}(X_{i})\mathbb{E}(X_{j})
\end{gather}
$$

于是根据定理 3.1.3 得

$$
\begin{gather}
\dfrac{S_{n}}{n}\to \dfrac{1}{10} \quad \text{a.s.}
\end{gather}
$$

又由于

$$
\begin{gather}
\dfrac{1}{n}\sum_{j=1}^{n} X_{j}(\omega)= \dfrac{N_{k}^{(n)}(\omega)}{n}
\end{gather}
$$

表示 $\omega$ 的前 $n$ 位小数中 $k$ 出现的频率，故 $m(\varphi_{k}=1 / 10)=1$ 对任意 $k$ 成立，从而有

$$
\begin{gather}
m\left( \bigcap_{k=0}^{9} \left\{  \varphi_{k}= \dfrac{1}{10}  \right\} \right)=1
\end{gather}
$$

即证正规数的集合具有 Lebesgue 测度 1.

尽管证明一个特定的数是正规数，比如 $e,\pi,\sqrt{ 2 }$ 等，是一件非常难的事，并且超出了目前数学工具的范围，但上述定理的证明非常简洁，这显示了概率论的强大表示能力。

# Section 2: 弱大数定律

3.1 中的定理都依赖于有限二阶矩的假设，但只得到了关于一阶矩的信息，对于我们来说，这个条件过强了。为了去除对于二阶矩的假设，我们引入以下定义：

**定义 3.2.1** 等价的（equivalent）

设 $(\Omega,\mathcal{F},\mathbb{P})$ 是概率空间，称随机变量序列 $(X_{n})$ 和 $(Y_{n})$ 是**等价的**，如果

$$
\begin{gather}
\sum_{n=1}^{\infty} \mathbb{P}(X_{n}\neq Y_{n})<\infty
\end{gather}
$$

**定理 3.2.2**

设 $(\Omega,\mathcal{F},\mathbb{P})$ 是概率空间，随机变量序列 $(X_{n})$ 和 $(Y_{n})$ 是等价的，那么级数 $\sum_{n=1}^{\infty}(X_{n}-Y_{n})$ a.s. 收敛。此外，如果实数序列 $(a_{n})$ 递增且发散至 $\infty$，那么

$$
\begin{gather}
\dfrac{1}{a_{n}}\sum_{j=1}^{n} (X_{n}-Y_{n})\to 0 \quad \text{a.s.}
\end{gather}
$$

**证明**

根据 Borel-Cantelli 引理，我们有

$$
\begin{gather}
\mathbb{P}(X_{n}\neq Y_{n}\ \text{i.o.})=0
\end{gather}
$$

这表明，对于几乎所有 $\omega \in\Omega$，都存在 $N$ 使得对任意 $n>N$ 有 $X_{n}(\omega)=Y_{n}(\omega)$，即 $X_{n}(\omega)$ 和 $Y_{n}(\omega)$ 只有有限个项不同。由此我们可以立即证明定理中的两个结论。

根据该定理，我们可知：如果 $(X_{n}),(Y_{n})$ 是等价的，那么 $\displaystyle \dfrac{1}{a_{n}}\sum_{j=1}^{n}X_{j}$ 和 $\displaystyle \dfrac{1}{a_{n}}\sum_{j=1}^{n}Y_{j}$ 具有相同的收敛性和极限，这一事实被用于证明下面的结论：

**定理 3.2.3** Khintchine 大数定律

设 $(\Omega,\mathcal{F},\mathbb{P})$ 是概率空间，随机变量 $(X_{n})$ 两两独立且同分布，并且具有有限期望 $m$，则有

$$
\begin{gather}
\dfrac{S_{n}}{n} \to m \quad \text{依概率}
\end{gather}
$$

**证明**

设 $X_{n}$ 共同的分布函数为 $F$，则有

$$
\begin{gather}
m=\mathbb{E}(X_{n})=\int x\mathrm{d} F(x), \mathbb{E}(|X_{n}|)=\int|x|\mathrm{d} F(x)<\infty
\end{gather}
$$

根据定理 1.3.10，$\mathbb{E}(|X_{1}|)<\infty$ 等价于

$$
\begin{gather}
\sum_{n=1}^{\infty} \mathbb{P}(|X_{1}|>n)<\infty
\end{gather}
$$

由于 $X_{n}$ 同分布，从而有

$$
\begin{gather}
\sum_{n=1}^{\infty} \mathbb{P}(|X_{n}|>n)<\infty
\end{gather}
$$

现在定义

$$
\begin{gather}
Y_{n}(\omega)=\begin{cases}
X_{n}(\omega) & ,|X_{n}(\omega)|\leq n \\
0 & ,|X_{n}(\omega)|>n
\end{cases}
\end{gather}
$$

则 $\mathbb{P}(|X_{n}|>n)=\mathbb{P}(X_{n}\neq Y_{n})$，从而 $X_{n}$ 和 $Y_{n}$ 是等价的。令

$$
\begin{gather}
T_{n}=\sum_{j=1}^{n} Y_{j}
\end{gather}
$$

则依概率 $S_{n} / n\to m$ 当且仅当 $T_{n} / n \to m$. 由于 $X_{n}$ 是两两独立的，故 $Y_{n}$ 也是两两独立的，从而是不相关的。又由于 $Y_{n}$ 都是有界的，故 $\mathbb{E}(Y_{n}^{2})<\infty$. 现在我们来计算 $\sigma^{2}(T_{n})$：

$$
\begin{gather}
\sigma^{2}(T_{n})=\sum_{j=1}^{n} \sigma^{2}(Y_{n})\leq \sum_{j=1}^{n} \mathbb{E}(Y_{n}^{2})=\sum_{j=1}^{n} \int_{|x|\leq j} x^{2}\mathrm{d} F(x)
\end{gather}
$$

如果采用最粗糙的估计，我们将得到

$$
\begin{gather}
\sum_{j=1}^{n} \int_{|x|\leq j}x^{2}\mathrm{d} F(x)\leq \sum_{j=1}^{n} j \int_{|x|\leq j} |x|\mathrm{d} F(x)\leq \dfrac{n(n+1)}{2}\int|x|\mathrm{d} F(x)=O(n^{2})
\end{gather}
$$

但我们需要的是 $\sigma^{2}(T_{n})=o(n^{2})$，从而我们可以应用定理 3.1.2. 为此，我们引入整数序列 $(a_{n})$ 满足：$0<a_{n}<n$，$a_{n}\to \infty$，且 $a_{n}=o(n)$，于是我们有

$$
\begin{align}
\sum_{j=1}^{n} \int_{|x|\leq j}x^{2}\mathrm{d} F(x)&=\sum_{j\leq a_{n}} \int_{|x|\leq j}x^{2}\mathrm{d} F(x)+\sum_{a_{n}<j\leq n}\int_{|x|\leq j}x^{2}\mathrm{d} F(x) \\
&\leq \sum_{j\leq a_{n}}a_{n} \int_{|x|\leq a_{n}}|x|\mathrm{d} F(x)+\sum_{a_{n}<j\leq n} a_{n}\int_{|x|\leq a_{n}}|x|\mathrm{d} F(x) \\
&+\sum_{a_{n}<j\leq n} n \int_{a_{n}<|x|\leq n}|x|\mathrm{d} F(x) \\
&\leq na_{n} \int|x|\mathrm{d} F(x)+ n^{2} \int_{|x|>a_{n}}|x|\mathrm{d} F(x)
\end{align}
$$

右边第一项的阶是 $O(na_{n})=o(n^{2})$，第二项的阶是 $n^{2}o(1)=o(n^{2})$，因为 $\{ x \mid |x|>a_{n} \}$ 递减至空集，故第二项积分收敛于 $0$. 从而我们有 $\sigma^{2}(T_{n})=o(n^{2})$，即得

$$
\begin{gather}
\dfrac{T_{n}-\mathbb{E}(T_{n})}{n}=\dfrac{1}{n}\sum_{j=1}^{n} (Y_{j}-\mathbb{E}(Y_{j}))\to 0 \quad \text{依概率}
\end{gather}
$$

根据单调收敛定理，我们有 $\mathbb{E}(Y_{j})\to \mathbb{E}(X_{j})=m$，故有

$$
\begin{gather}
\dfrac{1}{n}\sum_{j=1}^{n} Y_{j} \to m \quad \text{依概率}
\end{gather}
$$

根据定理 3.2.2 即证 $\dfrac{S_{n}}{n}\to m$ 依概率。

对于独立，但不同分布的随机变量，Kolmogorov 证明了如下所示的最一般形式的大数定律：

**定理 3.2.4** 弱大数定律（weak law of large numbers）

设 $(\Omega,\mathcal{F},\mathbb{P})$ 是概率空间，随机变量 $(X_{n})$ 是独立的，对应的分布函数为 $(F_{n})$，$(b_{n})$ 是一个递增且发散至 $\infty$ 的正数序列，假设满足以下条件：

1. $\displaystyle \lim_{ n \to \infty }\sum_{j=1}^{n}\int_{|x|>b_{n}}\mathrm{d}F_{j}(x)=0$；
2. $\displaystyle \lim_{ n \to \infty } \dfrac{1}{b_{n}^{2}}\sum_{j=1}^{n}\int_{|x|\leq b_{n}}x^{2}\mathrm{d}F_{j}(x)=0$；

那么如果令

$$
\begin{gather}
a_{n}=\sum_{j=1}^{n} \int_{|x|\leq b_{n}} x \mathrm{d} F_{j}(x)
\end{gather}
$$

则有

$$
\begin{gather}
\dfrac{S_{n}-a_{n}}{b_{n}}\to 0 \quad \text{依概率}
\end{gather}
$$

**证明**

对任意 $n\geq 1$ 和 $1\leq j\leq n$，定义

$$
\begin{gather}
Y_{nj}=\begin{cases}
X_{j} & ,|X_{j}|\leq b_{n} \\
0 & ,|X_{j}|>b_{n}
\end{cases}
\end{gather}
$$

并定义

$$
\begin{gather}
T_{n}=\sum_{j=1}^{n} Y_{nj}
\end{gather}
$$

那么条件 1 可以表示为

$$
\begin{gather}
\lim_{ n \to \infty } \sum_{j=1}^{n} \mathbb{P}(Y_{nj}\neq X_{j})=0
\end{gather}
$$

于是有

$$
\begin{gather}
\mathbb{P}(T_{n}\neq S_{n})\leq \mathbb{P}\left( \bigcup_{j=1}^{n} \{ Y_{nj}\neq X_{j} \} \right)\leq \sum_{j=1}^{n} \mathbb{P}(Y_{nj}\neq X_{j})\to 0
\end{gather}
$$

接下来，条件 2 可以表示为

$$
\begin{gather}
\lim_{ n \to \infty } \sum_{j=1}^{n} \mathbb{E}\left( \left( \dfrac{Y_{nj}}{b_{n}} \right)^{2} \right)=0
\end{gather}
$$

根据 $Y_{nj}$ 的独立性，我们就有

$$
\begin{gather}
\sigma^{2}\left( \dfrac{T_{n}}{b_{n}} \right)=\sum_{j=1}^{n} \sigma^{2}\left( \dfrac{Y_{nj}}{b_{n}} \right)\leq \sum_{j=1}^{n} \mathbb{E}\left( \left( \dfrac{Y_{nj}}{b_{n}} \right)^{2} \right)\to 0
\end{gather}
$$

于是

$$
\begin{gather}
\dfrac{T_{n}-\mathbb{E}(T_{n})}{b_{n}}\to 0 \quad \text{依概率}
\end{gather}
$$

又因为 $\mathbb{P}(S_{n}\neq T_{n})\to 0$，故 $S_{n}-T_{n} \to 0$ 依概率，从而有

$$
\begin{gather}
\dfrac{S_{n}-\mathbb{E}(T_{n})}{b_{n}}\to 0 \quad \text{依概率}
\end{gather}
$$

再根据

$$
\begin{gather}
\mathbb{E}(T_{n})=\sum_{j=1}^{n} \mathbb{E}(Y_{nj})=\sum_{j=1}^{n} \int_{|x|\leq b_{n}}x\mathrm{d} F_{j}(x)=a_{n}
\end{gather}
$$

就完成了证明。

上述定理的核心思想与第一节中的 Chebyshev 大数定律是一致的：如果随机变量的方差（二阶矩）足够小，那么部分和的均值 $S_{n} / n$ 依概率收敛于平均期望，只是在这一定理中，我们并不要求方差的一致有界性。

# Section 3: 随机变量的级数

在介绍强大数定律之前，我们需要先研究一下随机变量，特别是独立随机变量的级数，它有一些比较特殊的收敛性质，这与强大数定律有直接的联系。本节中，我们首先给出两个重要不等式，然后我们将给出著名的 Kolmogorov “三级数定理”。

**定理 3.3.1**

设 $(\Omega,\mathcal{F},\mathbb{P})$ 是概率空间，$(X_{n})$ 是独立的随机变量，满足对任意 $n$ 有

$$
\begin{gather}
\mathbb{E}(X_{n})=0, \mathbb{E}(X_{n}^{2})=\sigma^{2}(X_{n})<\infty
\end{gather}
$$

则对任意 $\varepsilon>0$ 有

$$
\begin{gather}
\mathbb{P}(\max_{1\leq j\leq n} |S_{j}|>\varepsilon)\leq \dfrac{\sigma^{2}(S_{n})}{\varepsilon^{2}}
\end{gather}
$$

**证明**

对任意 $\varepsilon>0$，定义

$$
\begin{gather}
\Lambda=\{ \omega \mid \max_{1\leq j\leq n}|S_{j}(\omega)|>\varepsilon \} \\
v(\omega)=\min \{ 1\leq j\leq n \mid |S_{j}(\omega)|>\varepsilon \}
\end{gather}
$$

显然 $v$ 是 $\Lambda$ 上的一个随机变量。再令

$$
\begin{gather}
\Lambda_{k}=\{ \omega \mid v(\omega)=k \}=\{ \omega \mid \max_{1\leq j\leq k-1}|S_{j}(\omega)|\leq\varepsilon, |S_{k}(\omega)|>\varepsilon \}
\end{gather}
$$

则各 $\Lambda_{k}$ 是不相交的，并且有 $\Lambda=\bigcup_{k=1}^{n}\Lambda_{k}$，从而

$$
\begin{align}
\int_{\Lambda} S_{n}^{2}\mathrm{d} \mathbb{P}&=\sum_{k=1}^{n} \int_{\Lambda_{k}}S_{n}^{2}\mathrm{d} \mathbb{P}=\sum_{k=1}^{n} \int_{\Lambda_{k}}(S_{k}+S_{n}-S_{k})^{2}\mathrm{d} \mathbb{P} \\
&=\sum_{k=1}^{n} \int_{\Lambda_{k}}(S_{k}^{2}+2S_{k}(S_{n}-S_{k})+(S_{n}-S_{k})^{2})\mathrm{d} \mathbb{P}
\end{align}
$$

设 $\varphi_{k}$ 是 $\Lambda_{k}$ 的指示函数，由于 $X_{n}$ 是独立的，故 $\varphi_{k}S_{k}$ 和 $S_{n}-S_{k}$ 是独立的，从而有

$$
\begin{align}
\int_{\Lambda_{k}}S_{k}(S_{n}-S_{k})\mathrm{d} \mathbb{P}&=\int\varphi_{k}S_{k}(S_{n}-S_{k})\mathrm{d} \mathbb{P} \\
&=\int\varphi_{k}S_{k}\mathrm{d} \mathbb{P} \int(S_{n}-S_{k})\mathrm{d} \mathbb{P} \\
&=\int\varphi_{k}S_{k}\mathrm{d} \mathbb{P} \sum_{j=k+1}^{n} \mathbb{E}(X_{j})=0
\end{align}
$$

代入上式得

$$
\begin{align}
\sigma^{2}(S_{n})&=\int S_{n}^{2}\mathrm{d} \mathbb{P}\geq \int_{\Lambda}S_{n}^{2}\mathrm{d} \mathbb{P}\geq \sum_{k=1}^{n} \int_{\Lambda_{k}}S_{k}^{2}\mathrm{d} \mathbb{P} \\
&\geq \varepsilon^{2} \sum_{k=1}^{n} \mathbb{P}(\Lambda_{k})=\varepsilon^{2}\mathbb{P}(\Lambda)
\end{align}
$$

这就完成了证明。

注意，在上述定理中，如果我们将 $\max_{1\leq j\leq n}|S_{j}|$ 换成 $|S_{n}|$，那么我们就可以得到 Chebyshev 不等式的一个特殊情况。

**定理 3.3.2**

设 $(\Omega,\mathcal{F},\mathbb{P})$ 是概率空间，$(X_{n})$ 是独立的随机变量，并且具有有限期望，则如果存在 $A>0$ 使得对任意 $n$ 有

$$
\begin{gather}
|X_{n}-\mathbb{E}(X_{n})|\leq A<\infty
\end{gather}
$$

那么对任意 $\varepsilon>0$ 有

$$
\begin{gather}
\mathbb{P}(\max_{1\leq j\leq n}|S_{j}|\leq\varepsilon)\leq \dfrac{(2A+4\varepsilon)^{2}}{\sigma^{2}(S_{n})}
\end{gather}
$$

**证明**

定义 $M_{0}=\Omega$，并且对 $1\leq k\leq n$ 定义

$$
\begin{gather}
M_{k}=\{ \omega \mid \max_{1\leq j\leq k} |S_{j}(\omega)|\leq\varepsilon \}, \Delta_{k}=M_{k-1}\setminus M_{k}
\end{gather}
$$

我们可以假设 $\mathbb{P}(M_{n})>0$，否则结论就是平凡的。另外，定义 $S_{0}'=0$，对 $k\geq 1$ 定义 $X_{k}'=X_{k}-\mathbb{E}(X_{k}),S_{k}'=\sum_{j=1}^{k}X_{j}'$. 下面再令

$$
\begin{gather}
a_{k}= \dfrac{1}{\mathbb{P}(M_{k})}\int_{M_{k}} S_{k}' \mathrm{d} \mathbb{P}
\end{gather}
$$

于是有

$$
\begin{gather}
\int_{M_{k}}(S_{k}'-a_{k})\mathrm{d} \mathbb{P}=0
\end{gather}
$$

以及

$$
\begin{align}
\int_{M_{k+1}} (S_{k+1}'-a_{k+1})^{2}\mathrm{d} \mathbb{P}&=\int_{M_{k}}(S_{k}'-a_{k}+a_{k}-a_{k+1}+X_{k+1}')^{2}\mathrm{d} \mathbb{P} \\
&- \int_{\Delta_{k+1}} (S_{k}'-a_{k}+a_{k}-a_{k+1}+X_{k+1}')^{2}\mathrm{d} \mathbb{P}
\end{align}
$$

我们将右边的两个积分分别记作 $I_{1}$ 和 $I_{2}$. 由于

$$
\begin{align}
|S_{k}'-a_{k}|&= \left\lvert  S_{k}-\mathbb{E}(S_{k})- \dfrac{1}{\mathbb{P}(M_{k})} \int_{M_{k}}(S_{k}-\mathbb{E}(S_{k}))\mathrm{d} \mathbb{P}  \right\rvert  \\
&=\left\lvert  S_{k}- \dfrac{1}{\mathbb{P}(M_{k})}\int_{M_{k}} S_{k}\mathrm{d} \mathbb{P}  \right\rvert \leq |S_{k}|+\varepsilon \\
|a_{k}-a_{k+1}|&=\left\lvert  \dfrac{1}{\mathbb{P}(M_{k})}\int_{M_{k}}S_{k}\mathrm{d} \mathbb{P}-\dfrac{1}{\mathbb{P}(M_{k+1})}\int_{M_{k+1}}(S_{k}+X_{k+1}')\mathrm{d} \mathbb{P}  \right\rvert  \\
&\leq 2\varepsilon+A
\end{align}
$$

因此有

$$
\begin{gather}
I_{2}\leq \int_{\Delta_{k+1}}(|S_{k}|+\varepsilon+2\varepsilon+A+A)^{2}\mathrm{d} \mathbb{P}\leq (4\varepsilon+2A)^{2} \mathbb{P}(\Delta_{k+1})
\end{gather}
$$

另一方面，我们有

$$
\begin{align}
I_{1}&= \int_{M_{k}} ((S_{k}'-a_{k})^{2}+(a_{k}-a_{k+1})^{2}+(X_{k+1}')^{2}+2(S'_{k}-a_{k})(a_{k}-a_{k+1}) \\
&+ 2(S_{k}'-a_{k})X_{k+1}'+2(a_{k}-a_{k+1})X_{k+1}')\mathrm{d} \mathbb{P}
\end{align}
$$

根据 $a_{k}$ 的定义以及独立性，上式的最后三项积分均为 $0$，从而

$$
\begin{align}
I_{1}&\geq \int_{M_{k}}(S_{k}'-a_{k})^{2}\mathrm{d} \mathbb{P}+\int_{M_{k}}(X_{k+1}')^{2}\mathrm{d} \mathbb{P} \\
&=\int_{M_{k}}(S_{k}'-a_{k})^{2}\mathrm{d} \mathbb{P}+\mathbb{P}(M_{k})\sigma^{2}(X_{k+1})
\end{align}
$$

回到前面的等式，根据 $M_{k}\supset M_{n}$，我们有

$$
\begin{align}
& \int_{M_{k+1}}(S_{k+1}'-a_{k+1})^{2}\mathrm{d} \mathbb{P}-\int_{M_{k}}(S_{k}'-a_{k})^{2}\mathrm{d} \mathbb{P} \\
&\geq \mathbb{P}(M_{n})\sigma^{2}(X_{k+1})-(4\varepsilon+2A)^{2}\mathbb{P}(\Delta_{k+1})
\end{align}
$$

对 $0\leq k\leq n-1$ 求和，则有

$$
\begin{align}
4\varepsilon^{2}\mathbb{P}(M_{n})&\geq \int_{M_{n}}(|S_{n}|+\varepsilon)^{2} \mathrm{d} \mathbb{P}\geq \int_{M_{n}} (S_{n}'-a_{n})^{2}\mathrm{d} \mathbb{P} \\
&\geq \mathbb{P}(M_{n})\sum_{j=1}^{n} \sigma^{2}(X_{j})-(4\varepsilon+2A)^{2} \mathbb{P}(\Omega\setminus M_{n})
\end{align}
$$

移项即得

$$
\begin{gather}
(4\varepsilon+2A)^{2}\geq \mathbb{P}(M_{n}) \sum_{j=1}^{n} \sigma^{2}(X_{j})=\mathbb{P}(M_{n})\sigma^{2}(S_{n})
\end{gather}
$$

这就完成了证明。

现在我们可以给出 Kolmogorov 的三级数定理，它给出了独立随机变量级数 a.s. 收敛的一个充要条件。

**定理 3.3.3** Kolmogorov 三级数定理

设 $(\Omega,\mathcal{F},\mathbb{P})$ 是概率空间，$(X_{n})$ 是独立的随机变量，并且对给定的常数 $A>0$ 定义

$$
\begin{gather}
Y_{n}(\omega)=\begin{cases}
X_{n}(\omega) & ,|X_{n}(\omega)|\leq A \\
0 & ,|X_{n}(\omega)|>A
\end{cases}
\end{gather}
$$

则级数 $\sum_{n=1}^{\infty}X_{n}$ 收敛 a.s. 当且仅当以下三个级数都收敛：

1. $\sum_{n=1}^{\infty}\mathbb{P}(|X_{n}|>A)=\sum_{n=1}^{\infty}\mathbb{P}(X_{n}\neq Y_{n})$
2. $\sum_{n=1}^{\infty}\mathbb{E}(Y_{n})$
3. $\sum_{n=1}^{\infty}\sigma^{2}(Y_{n})$

**证明**

首先设这三个级数收敛。对独立随机变量 $Y_{n}-\mathbb{E}(Y_{n})$ 应用定理 3.3.1，则对任意 $m\geq 1$ 有

$$
\begin{gather}
\mathbb{P}\left( \max_{n\leq k\leq n'} \left\lvert  \sum_{j=n}^{k} (Y_{j}-\mathbb{E}(Y_{j}))  \right\rvert \leq \dfrac{1}{m} \right) \geq 1- m^{2} \sum_{j=n}^{n'} \sigma^{2}(Y_{j})
\end{gather}
$$

将左边的概率记作 $\mathbb{P}(m,n,n')$，则根据 3 的收敛性，对任意 $m$ 有

$$
\begin{gather}
\lim_{ n \to \infty } \lim_{ n' \to \infty } \mathbb{P}(m,n,n')=1
\end{gather}
$$

因此级数 $\sum_{n=1}^{\infty}(Y_{n}-\mathbb{E}(Y_{n}))$ 的尾部收敛于 $0$ a.s.，从而级数收敛 a.s. 又由于 2 收敛，故 $\sum_{n=1}^{\infty}Y_{n}$ 收敛 a.s. 最后，由 1 知 $(X_{n})$ 与 $(Y_{n})$ 等价，因此 $\sum_{n=1}^{\infty}X_{n}$ 也收敛 a.s.

反之，设 $\sum_{n=1}^{\infty}X_{n}$ 收敛 a.s.，则对任意 $A>0$ 有

$$
\begin{gather}
\mathbb{P}(|X_{n}|>A\ \text{i.o.})=0
\end{gather}
$$

由 Borel-Cantelli 引理，1 必然收敛。于是根据等价性，$\sum_{n=1}^{\infty}Y_{n}$ 收敛 a.s. 又由于 $|Y_{n}-\mathbb{E}(Y_{n})|\leq 2A$，根据定理 5.3.2 得

$$
\begin{gather}
\mathbb{P}\left( \max_{n\leq k\leq n'} \left\lvert  \sum_{j=n}^{k} Y_{j}  \right\rvert \leq 1 \right)\leq \dfrac{(4A+4)^{2}}{\sum_{j=n}^{n'} \sigma^{2}(Y_{j})}
\end{gather}
$$

如果级数 3 不收敛，那么 $\sum_{n=1}^{\infty}Y_{n}$ 的尾部几乎必然不会被 $1$ 所约束，从而级数不收敛，这一矛盾表明 3 收敛。

最后，考虑级数 $\sum_{n=1}^{\infty}(Y_{n}-\mathbb{E}(Y_{n}))$，由于 $\mathbb{P}(|Y_{n}-\mathbb{E}(Y_{n})|>2A)=0$，$\mathbb{E}(Y_{n}-\mathbb{E}(Y_{n}))=0$，根据已经证明的充分性部分，我们可得 $\sum_{n=1}^{\infty}(Y_{n}-\mathbb{E}(Y_{n}))$ 收敛 a.s.，由 $\sum_{n=1}^{\infty}Y_{n}$ 的收敛性即证 2 收敛。这就完成了证明。

下面的定理由 Levy 证明，它给出了独立随机变量级数 a.s. 收敛的另一个充分必要条件。

**定理 3.3.4**

设 $(\Omega,\mathcal{F},\mathbb{P})$ 是概率空间，$(X_{n})$ 是独立的随机变量，则级数 $\sum_{n=1}^{\infty}X_{n}$ 依概率收敛等价于它 a.s. 收敛。

**证明**

我们只需证明依概率收敛蕴含 a.s. 收敛。给定 $0<\varepsilon<1$，则存在 $N$ 使得对任意 $n>m>N$ 有

$$
\begin{gather}
\mathbb{P}(|S_{m,n}|>\varepsilon)<\varepsilon
\end{gather}
$$

其中

$$
\begin{gather}
S_{m,n}=\sum_{j=m+1}^{n} X_{j}
\end{gather}
$$

对于 $m<k\leq n$，根据三角不等式有

$$
\begin{gather}
\bigcup_{k=m+1}^{n} \{ \max_{m<j\leq k-1}|S_{m,j}|\leq 2\varepsilon, |S_{m,k}|>2\varepsilon, |S_{k,n}|\leq\varepsilon \} \subset \{ |S_{m,n}|>\varepsilon \}
\end{gather}
$$

左边的各集合是不相交的。利用独立性，我们有

$$
\begin{gather}
\sum_{k=m+1}^{n} \mathbb{P}(\max_{m<j\leq k-1}|S_{m,j}|\leq 2\varepsilon,|S_{m,k}|>2\varepsilon)\mathbb{P}(|S_{k,n}|\leq\varepsilon)\leq \mathbb{P}(|S_{m,n}|>\varepsilon)
\end{gather}
$$

从而

$$
\begin{gather}
\mathbb{P}(\max_{m<j\leq n}|S_{m,j}|>2\varepsilon) \min_{m<k\leq n} \mathbb{P}(|S_{k,n}|\leq\varepsilon)\leq \mathbb{P}(|S_{m,n}|>\varepsilon)
\end{gather}
$$

于是当 $n>m>N$ 时，有

$$
\begin{gather}
\mathbb{P}(\max_{m<j\leq n}|S_{m,j}|>2\varepsilon)\leq \dfrac{\varepsilon}{1-\varepsilon}
\end{gather}
$$

令 $n\to \infty$，然后 $m\to \infty$，最后 $\varepsilon\to 0$，则左边的三重累次极限为 $0$，下面我们要证这可以推出 $\sum_{n=1}^{\infty}X_{n}$ 收敛 a.s.

设 $C$ 包含所有使得 $S_{n}(\omega)$ 收敛的 $\omega \in\Omega$. 如果 $\omega \in C$，那么对任意 $m\geq 1$，存在 $N$ 使得对任意 $n'>n>N$，有 $|S_{n'}(\omega)-S_{n}(\omega)|\leq \dfrac{1}{m}$ 成立，从而有

$$
\begin{gather}
\max_{n<j<k\leq n'} |S_{k}(\omega)-S_{j}(\omega)|\leq \dfrac{1}{m}
\end{gather}
$$

对所有 $n'>n$ 成立。于是

$$
\begin{gather}
\omega \in \bigcap_{m=1}^{\infty} \bigcup_{n=1}^{\infty} \bigcap_{n'=n+1}^{\infty} \left\{  \omega \middle| \max_{n<j<k\leq n'} |S_{k}(\omega)-S_{j}(\omega)|\leq \dfrac{1}{m}  \right\} 
\end{gather}
$$

反向的包含也成立：这只是 $\mathbb{R}$ 的完备性（Cauchy 序列收敛）。因此，我们有

$$
\begin{gather}
\mathbb{P}(C)=\lim_{ m \to \infty } \lim_{ n \to \infty } \lim_{ n' \to \infty } \mathbb{P}\left(\max_{n<j<k\leq n'} |S_{j,k}|\leq \dfrac{1}{m}\right)
\end{gather}
$$

根据前文的结论，即证 $\mathbb{P}(C)=1$.

我们可以看出，本节中的大多数不等式都涉及求和式最大值的概率控制，这是概率论中的一种常用技术。

最后，我们指出：如果 $X_{n}$ 是独立的，那么甚至当 $S_{n}$ 依分布收敛时也有 $S_{n}$ a.s. 收敛，这一结论我们将在后面的章节中证明。

# Section 4: 强大数定律

为建立上一节与强大数定律的联系，我们给出以下引理：

**定理 3.4.1** Kronecker 引理

设 $(x_{k})$ 是一个实数序列，$(a_{k})$ 是一个递增至 $\infty$ 的正数序列，则

$$
\begin{gather}
\sum_{n=1}^{\infty} \dfrac{x_{n}}{a_{n}} \text{ 收敛} \implies \dfrac{1}{a_{n}}\sum_{j=1}^{n} x_{j} \to 0
\end{gather}
$$

**证明**

定义

$$
\begin{gather}
b_{n}=\sum_{j=1}^{n} \dfrac{x_{x}}{a_{n}} \to b
\end{gather}
$$

如果令 $a_{0}=b_{0}=0$，那么根据分部求和法有

$$
\begin{gather}
x_{n}=a_{n}(b_{n}-b_{n-1}) \\
\dfrac{1}{a_{n}}\sum_{j=1}^{n} x_{j}=b_{n}- \dfrac{1}{a_{n}}\sum_{j=0}^{n-1} b_{j}(a_{j+1}-a_{j})
\end{gather}
$$

由于 $a_{j+1}-a_{j}\geq 0$，

$$
\begin{gather}
\dfrac{1}{a_{n}}\sum_{j=0}^{n-1} (a_{j+1}-a_{j})=1
\end{gather}
$$

且 $b_{n}\to b$，故有

$$
\begin{gather}
\dfrac{1}{a_{n}}\sum_{j=1}^{n} x_{j} \to b-b=0
\end{gather}
$$

这就完成了证明。

**定理 3.4.2**

设 $(\Omega,\mathcal{F},\mathbb{P})$ 是概率空间，$(X_{n})$ 是独立的随机变量，且 $\mathbb{E}(X_{n})=0$，$(a_{n})$ 是一个递增至 $\infty$ 的正数序列，连续函数 $\varphi\colon \mathbb{R}\to(0,\infty)$ 是偶函数，且在 $(0,\infty)$ 上 $\dfrac{\varphi(x)}{|x|}$ 递增，$\dfrac{\varphi(x)}{x^{2}}$ 递减，并且

$$
\begin{gather}
\sum_{n=1}^{\infty} \dfrac{\mathbb{E}(\varphi(X_{n}))}{\varphi(a_{n})}<\infty
\end{gather}
$$

那么

$$
\begin{gather}
\sum_{n=1}^{\infty} \dfrac{X_{n}}{a_{n}} \text{ 收敛 a.s.}
\end{gather}
$$

**证明**

记 $X_{n}$ 的分布函数为 $F_{n}$，定义

$$
\begin{gather}
Y_{n}(\omega)=\begin{cases}
X_{n}(\omega) & ,|X_{n}(\omega)|\leq a_{n} \\
0 & ,|X_{n}(\omega)|>a_{n}
\end{cases}
\end{gather}
$$

则

$$
\begin{align}
\sum_{n=1}^{\infty} \mathbb{E}\left( \dfrac{Y_{n}^{2}}{a_{n}^{2}} \right)&=\sum_{n=1}^{\infty} \int_{|x|\leq a_{n}} \dfrac{x^{2}}{a_{n}^{2}}\mathrm{d} F_{n}(x)\leq \sum_{n=1}^{\infty} \int_{|x|\leq a_{n}} \dfrac{\varphi(x)}{\varphi(a_{n})}\mathrm{d} F_{n}(x) \\
&\leq \sum_{n=1}^{\infty} \dfrac{\mathbb{E}(\varphi(X_{n}))}{\varphi(a_{n})}<\infty
\end{align}
$$

从而

$$
\begin{gather}
\sum_{n=1}^{\infty} \sigma^{2}\left( \dfrac{Y_{n}}{a_{n}} \right)\leq \sum_{n=1}^{\infty} \mathbb{E}\left( \dfrac{Y_{n}^{2}}{a_{n}^{2}} \right)<\infty
\end{gather}
$$

因此，对于随机变量 $\dfrac{Y_{n}-\mathbb{E}(Y_{n})}{a_{n}}$，三级数定理中的级数 3 收敛，而级数 1 和 2 在 $A=2$ 时收敛，从而

$$
\begin{gather}
\sum_{n=1}^{\infty} \dfrac{Y_{n}-\mathbb{E}(Y_{n})}{a_{n}} \text{ 收敛 a.s.}
\end{gather}
$$

接下来，由于 $\mathbb{E}(X_{n})=0$，我们有

$$
\begin{align}
\sum_{n=1}^{\infty} \dfrac{|\mathbb{E}(Y_{n})|}{a_{n}}&=\sum_{n=1}^{\infty} \dfrac{1}{a_{n}} \left\lvert  \int_{|x|\leq a_{n}} x\mathrm{d} F_{n}(x)  \right\rvert =\sum_{n=1}^{\infty} \dfrac{1}{a_{n}} \left\lvert  \int_{|x|>a_{n}} x\mathrm{d} F_{n}(x)  \right\rvert  \\
&\leq \sum_{n=1}^{\infty} \int_{|x|>a_{n}} \dfrac{|x|}{a_{n}}\mathrm{d} F_{n}(x)\leq \sum_{n=1}^{\infty} \int_{|x|>a_{n}} \dfrac{\varphi(x)}{\varphi(a_{n})}\mathrm{d} F_{n}(x) \\
&\leq \sum_{n=1}^{\infty} \dfrac{\mathbb{E}(\varphi(X_{n}))}{\varphi(a_{n})}<\infty
\end{align}
$$

这表明 $\sum_{n=1}^{\infty} Y_{n} / a_{n}$ 收敛 a.s. 最后，由于 $\varphi$ 递增，故

$$
\begin{align}
\sum_{n=1}^{\infty} \mathbb{P}(X_{n}\neq Y_{n})&=\sum_{n=1}^{\infty} \int_{|x|>a_{n}}\mathrm{d} F_{n}(x)\leq \sum_{n=1}^{\infty} \int_{|x|>a_{n}} \dfrac{\varphi(x)}{\varphi(a_{n})}\mathrm{d} F_{n}(x) \\
&\leq \sum_{n=1}^{\infty} \dfrac{\mathbb{E}(\varphi(X_{n}))}{\varphi(a_{n})}<\infty
\end{align}
$$

即证 $X_{n}$ 等价于 $Y_{n}$，从而 $\sum_{n=1}^{\infty}X_{n} / a_{n}$ 收敛 a.s.

应用 Kronecker 引理，在同样的假设下，我们有

$$
\begin{gather}
\dfrac{1}{a_{n}}\sum_{j=1}^{n} X_{j}= \dfrac{S_{n}}{a_{n}}\to 0 \quad \text{a.s.}
\end{gather}
$$

现在我们就可以给出 Kolmogorov 大数定律的强形式了。

**定理 3.4.3** 强大数定律（strong law of large numbers）

设 $(\Omega,\mathcal{F},\mathbb{P})$ 是概率空间，$(X_{n})$ 是独立同分布（i.i.d.）的随机变量，则有

$$
\begin{gather}
\mathbb{E}(|X_{1}|)<\infty \implies \dfrac{S_{n}}{n}\to \mathbb{E}(X_{1}) \quad \text{a.s.} \\
\mathbb{E}(|X_{1}|)=\infty \implies \limsup_{ n \to \infty } \dfrac{|S_{n}|}{n}=\infty \quad \text{a.s.}
\end{gather}
$$

**证明**

首先设 $\mathbb{E}(|X_{1}|)<\infty$，定义

$$
\begin{gather}
Y_{n}(\omega)=\begin{cases}
X_{n}(\omega) & ,|X_{n}(\omega)|\leq n \\
0 & ,|X_{n}(\omega)|>n
\end{cases}
\end{gather}
$$

则

$$
\begin{gather}
\sum_{n=1}^{\infty} \mathbb{P}(X_{n}\neq Y_{n})=\sum_{n=1}^{\infty} \mathbb{P}(|X_{n}|>n)=\sum_{n=1}^{\infty} \mathbb{P}(|X_{1}|>n)<\infty
\end{gather}
$$

故 $X_{n}$ 等价于 $Y_{n}$. 我们要对随机变量 $Y_{n}-\mathbb{E}(Y_{n})$ 应用定理 3.4.2，取 $\varphi(x)=x^{2}$，由于

$$
\begin{align}
\sum_{n=1}^{\infty} \dfrac{\sigma^{2}(Y_{n})}{n^{2}}&\leq \sum_{n=1}^{\infty} \dfrac{\mathbb{E}(Y_{n}^{2})}{n^{2}}=\sum_{n=1}^{\infty} \dfrac{1}{n^{2}}\int_{|x|\leq n} x^{2}\mathrm{d} F(x) \\
&=\sum_{n=1}^{\infty} \dfrac{1}{n^{2}} \sum_{j=1}^{n} \int_{j-1<|x|\leq j} x^{2}\mathrm{d} F(x) \\
&=\sum_{j=1}^{\infty} \sum_{n=j}^{\infty} \dfrac{1}{n^{2}} \int_{j-1<|x|\leq j}x^{2}\mathrm{d} F(x) \\
&\leq \sum_{j=1}^{\infty} \dfrac{C}{j} \cdot j \int_{j-1<|x|\leq j} |x|\mathrm{d} F(x) \\
&=C\mathbb{E}(|X_{1}|)<\infty
\end{align}
$$

故根据定理 3.4.2 得

$$
\begin{gather}
\dfrac{1}{n}\sum_{j=1}^{n} (Y_{j}-\mathbb{E}(Y_{j}))\to 0 \quad \text{a.s.}
\end{gather}
$$

由单调有界定理，有 $\mathbb{E}(Y_{n})\to \mathbb{E}(X_{1})$，因此

$$
\begin{gather}
\dfrac{1}{n}\sum_{j=1}^{n} \mathbb{E}(Y_{j})\to \mathbb{E}(X_{1}) \quad \text{a.s.}
\end{gather}
$$

从而

$$
\begin{gather}
\dfrac{1}{n} \sum_{j=1}^{n} Y_{j} \to \mathbb{E}(X_{1}) \quad \text{a.s.}
\end{gather}
$$

根据 $X_{n}$ 和 $Y_{n}$ 的等价性即证。

现在设 $\mathbb{E}(|X_{1}|)=\infty$，则对任意 $A>0$，有 $\mathbb{E}(|X_{1}| / A)=\infty$，因此根据定理 1.3.10 得

$$
\begin{gather}
\sum_{n=1}^{\infty} \mathbb{P}(|X_{1}|>An)=\sum_{n=1}^{\infty} \mathbb{P}(|X_{n}|>An)=\infty
\end{gather}
$$

根据 Borel-Cantelli 引理，我们有

$$
\begin{gather}
\mathbb{P}(|X_{n}|>An \ \text{i.o.})=1
\end{gather}
$$

又因为 $|S_{n}-S_{n-1}|=|X_{n}|>An$ 蕴含 $|S_{n}|>An / 2$ 或者 $|S_{n-1}|>An / 2$，这表明

$$
\begin{gather}
\mathbb{P}\left( |S_{n}|> \dfrac{An}{2} \ \text{i.o.} \right)=1
\end{gather}
$$

因此对任意 $A>0$，存在零概率集 $Z(A)$ 使得当 $\omega \in\Omega \setminus Z(A)$ 时有

$$
\begin{gather}
\limsup_{ n \to \infty } \dfrac{|S_{n}(\omega)|}{n}\geq \dfrac{A}{2}
\end{gather}
$$

令 $Z=\bigcup_{m=1}^{\infty}Z(m)$，则仍然有 $\mathbb{P}(Z)=0$，并且在 $\Omega \setminus Z$ 上有上式对任意 $A>0$ 成立，这就完成了证明。

当 $\mathbb{E}(|X_{1}|)=\infty$ 时，Feller 给出了强大数定律的一个推广：

**定理 3.4.4**

设 $(\Omega,\mathcal{F},\mathbb{P})$ 是概率空间，$(X_{n})$ 是独立同分布的随机变量，$\mathbb{E}(|X_{1}|)=\infty$，$(a_{n})$ 是一个正数序列，满足 $\dfrac{a_{n}}{n}$ 递增，则有

$$
\begin{gather}
\sum_{n=1}^{\infty} \mathbb{P}(|X_{n}|\geq a_{n})<\infty \implies \limsup_{ n \to \infty } \dfrac{|S_{n}|}{a_{n}}=0 \quad \text{a.s.} \\
\sum_{n=1}^{\infty} \mathbb{P}(|X_{n}|\geq a_{n})=\infty \implies \limsup_{ n \to \infty } \dfrac{|S_{n}|}{a_{n}}=\infty \quad \text{a.s.}
\end{gather}
$$

**证明**

我们有

$$
\begin{gather}
\mathbb{P}(|X_{n}|\geq a_{n})=\int_{|x|\geq a_{n}}\mathrm{d} F(x)=\sum_{k=n}^{\infty} \int_{a_{k}\leq|x|<a_{k+1}} \mathrm{d} F(x)
\end{gather}
$$

假设

$$
\begin{gather}
\sum_{n=1}^{\infty} \sum_{k=n}^{\infty} \int_{a_{k}\leq|x|<a_{k+1}}\mathrm{d} F(x)=\sum_{k=1}^{\infty} k \int_{a_{k}\leq|x|<a_{k+1}}\mathrm{d} F(x)<\infty
\end{gather}
$$

定义

$$
\begin{gather}
\mu_{n}=\int_{|x|<a_{n}}x\mathrm{d} F(x) \\
Y_{n}=\begin{cases}
X_{n}-\mu_{n} & ,|X_{n}|< a_{n} \\
-\mu_{n} & ,|X_{n}|\geq a_{n}
\end{cases}
\end{gather}
$$

则 $\mathbb{E}(Y_{n})=0$，并且

$$
\begin{gather}
\sum_{n=1}^{\infty} \mathbb{P}(Y_{n}\neq X_{n}-\mu_{n})=\sum_{n=1}^{\infty} \mathbb{P}(|X_{n}|\geq a_{n})<\infty
\end{gather}
$$

接下来令 $a_{0}=0$，则有

$$
\begin{align}
\sum_{n=1}^{\infty} \mathbb{E}\left( \dfrac{Y_{n}^{2}}{a_{n}^{2}} \right)&\leq \sum_{n=1}^{\infty} \dfrac{1}{a_{n}^{2}} \int_{|x|<a_{n}} x^{2}\mathrm{d} F(x) \\
&= \sum_{n=1}^{\infty} \dfrac{1}{a_{n}^{2}} \sum_{k=1}^{n} \int_{a_{k-1}\leq|x|<a_{k}}x^{2}\mathrm{d} F(x) \\
&\leq \sum_{k=1}^{\infty} a_{k}^{2} \int_{a_{k-1}\leq|x|<a_{k}}\mathrm{d} F(x) \sum_{n=k}^{\infty} \dfrac{1}{a_{n}^{2}}
\end{align}
$$

由于 $\dfrac{a_{n}}{n}\geq \dfrac{a_{k}}{k}$，故

$$
\begin{align}
\sum_{n=k}^{\infty} \dfrac{1}{a_{n}^{2}}\leq \dfrac{k^{2}}{a_{k}^{2}} \sum_{n=k}^{\infty} \dfrac{1}{n^{2}}\leq \dfrac{2k}{a_{k}^{2}}
\end{align}
$$

因此

$$
\begin{gather}
\sum_{n=1}^{\infty} \mathbb{E}\left( \dfrac{Y_{n}^{2}}{a_{n}^{2}} \right)\leq \sum_{k=1}^{\infty} 2k \int_{a_{k-1}\leq|x|<a_{k}}\mathrm{d} F(x)<\infty
\end{gather}
$$

从而根据定理 3.4.2 得

$$
\begin{gather}
\dfrac{1}{a_{n}}\sum_{j=1}^{n} Y_{j} \to 0 \quad \text{a.s.}
\end{gather}
$$

我们现在来估计以下量

$$
\begin{gather}
\dfrac{1}{a_{n}}\sum_{k=1}^{n} \mu_{k}=\dfrac{1}{a_{n}}\sum_{k=1}^{n} \int_{|x|<a_{k}}x\mathrm{d} F(x)
\end{gather}
$$

对任意 $N<n$，上式的绝对值有上界

$$
\begin{gather}
\dfrac{n}{a_{n}}\left( a_{N}+\int_{a_{N}<|x|<a_{n}} |x|\mathrm{d} F(x) \right)
\end{gather}
$$

由于 $\mathbb{E}(|X_{1}|)=\infty$，根据定理 1.3.10，如果 $\dfrac{a_{n}}{n}$ 有界，那么级数 $\sum_{n=1}^{\infty}\mathbb{P}(|X_{n}|\geq a_{n})$ 不可能收敛，这与假设矛盾，因此 $\dfrac{a_{n}}{n}\to \infty$，从而对固定的 $N$，有 $\dfrac{n}{a_{n}}a_{N}\to 0$. 另一项则有上界

$$
\begin{gather}
\dfrac{n}{a_{n}}\sum_{j=N+1}^{n} a_{j} \int_{a_{j-1}\leq |x|<a_{j}} \mathrm{d} F(x)\leq \sum_{j=N+1}^{n} j \int_{a_{j-1}\leq|x|<a_{j}}\mathrm{d} F(x)
\end{gather}
$$

因此对任意 $N$ 有

$$
\begin{gather}
\dfrac{1}{a_{n}} \left\lvert \sum_{k=1}^{\infty} \mu_{k}  \right\rvert \leq \sum_{j=N+1}^{\infty} j \int_{a_{j-1}\leq|x|<a_{j}} \mathrm{d} F(x) \to 0 \quad (N\to \infty)
\end{gather}
$$

即证 $\limsup_{ n \to \infty } |S_{n}| / a_{n}=0$ a.s.

再设 $\sum_{n=1}^{\infty}\mathbb{P}(|X_{n}|\geq a_{n})=\infty$，由于 $\mathbb{E}(|X_{1}|)=\infty$，故 $\mathbb{E}\left( \dfrac{n}{Aa_{n}}|X_{1}| \right)=\infty$，从而有

$$
\begin{gather}
\sum_{n=1}^{\infty} \mathbb{P}(|X_{1}|\geq Aa_{n})=\sum_{n=1}^{\infty} \mathbb{P}(|X_{n}|\geq Aa_{n})=\infty
\end{gather}
$$

下面仿照定理 3.4.3 的证明即得 $\limsup_{ n \to \infty }|S_{n}| / a_{n}=\infty$.

由此我们可以得到推论：

**定理 3.4.5**

设 $(\Omega,\mathcal{F},\mathbb{P})$ 是概率空间，$(X_{n})$ 是独立同分布的随机变量，$\mathbb{E}(|X_{1}|)=\infty$，$(a_{n})$ 是一个正数序列，满足 $\dfrac{a_{n}}{n}$ 递增，则有

$$
\begin{gather}
\mathbb{P}(|S_{n}|\geq a_{n} \ \text{i.o.})=\mathbb{P}(|X_{n}|\geq a_{n} \ \text{i.o.})
\end{gather}
$$

这一推论成立是因为上式中的第二项只能取 $0$ 或 $1$，根据级数的收敛性而定。它表明，在某种程度上，$S_{n}$ 与 $X_{n}$ 的增长速度是相似的。

# Section 5: 应用

大数定律在概率论以及统计学的各种分支都有应用，下面我们给出三个例子。

第一个例子关于统计学中所谓的“经验分布”。令 $(X_{n})$ 是一列 i.i.d. 随机变量，其共同的分布函数是 $F$，这在统计学中被称为“理论分布”，并且被视为是未知的。对于 $\omega \in\Omega$，量 $X_{n}(\omega)$ 被称为一个“样本”或者“观测值”，而统计学的目标就是通过观测值来得到关于 $F$ 的信息。

对任意 $n$ 和 $\omega \in\Omega$，将 $n$ 个实数 $\{ X_{j}(\omega) \mid 1\leq j\leq n \}$ 按递增顺序排列：

$$
\begin{gather}
Y_{n 1}(\omega)\leq Y_{n 2}(\omega)\leq \dots\leq Y_{nn}(\omega)
\end{gather}
$$

现在定义一个分布函数 $F_{n}(\cdot,\omega)$ 如下：

$$
\begin{gather}
F_{n}(x,\omega)=\begin{cases}
0 & ,x< Y_{n 1}(\omega) \\
\dfrac{k}{n} & ,Y_{nk}(\omega)\leq x< Y_{n,k+1}(\omega),1\leq k\leq n-1 \\
1 & , x\geq Y_{nn}(\omega)
\end{cases}
\end{gather}
$$

这被称为基于 $F$ 的 $n$ 个样本的**经验分布函数**，它给出了不超过 $x$ 的观测值的经验频率。

显然，对任意 $x$，$F_{n}(x,\cdot)$ 是一个随机变量。下面我们引入指示随机变量 $\xi_{j}(x)$ 如下：

$$
\begin{gather}
\xi_{j}(x,\omega)=\begin{cases}
1 & , X_{j}(\omega)\leq x \\
0 & , X_{j}(\omega)>x
\end{cases}
\end{gather}
$$

于是有

$$
\begin{gather}
F_{n}(x,\omega)=\dfrac{1}{n}\sum_{j=1}^{n} \xi_{j}(x,\omega)
\end{gather}
$$

由于 $(X_{n})$ 是 i.i.d. 的，故 $(\xi_{j}(x))$ 也是 i.i.d. 的，其分布就是参数为 $p=F(x)$ 的 Bernoullian 分布 $B(1,p)$，从而 $\mathbb{E}(\xi_{j}(x))=F(x)$，于是强大数定律就表明

$$
\begin{gather}
F_{n}(x,\omega) \to F(x) \quad \text{a.s. }\omega
\end{gather}
$$

对 $F_{n}(x,\omega)$ 作为随机变量的研究就到这里，接下来，我们来考虑 $\mathbb{R}$ 上的函数 $F_{n}(\cdot,\omega)$ 与 $F$ 的关系。

根据上面的极限式，我们可知对任意 $x$，存在一个零概率集 $N(x)$ 使得对任意 $\omega \in\Omega\setminus N(x)$ 有 $F_{n}(x,\omega)\to F(x)$. 因此对任意可数稠密集（如有理数集）$Q\subset \mathbb{R}$，同样存在零概率集

$$
\begin{gather}
N=\bigcup_{x \in Q} N(x)
\end{gather}
$$

使得对任意 $\omega \in\Omega\setminus N$ 有 $F_{n}(x,\omega)\to F(x)$，这表明 $F_{n}(\cdot,\omega)$ 淡收敛于 $F$ 对 a.s. $\omega$ 成立。该结果可以进一步加强，如以下定理所示：

**定理 3.5.1**

当 $n\to \infty$ 时有

$$
\begin{gather}
\sup_{-\infty<x<\infty} |F_{n}(x,\omega)-F(x)| \to 0 \quad \text{a.s. } \omega
\end{gather}
$$

**证明**

令可数集 $J$ 由 $F$ 的跳跃间断点构成，对 $x \in J$，定义

$$
\begin{gather}
\eta_{j}(x,\omega)=\begin{cases}
1 & , X_{j}(\omega)=x \\
0 & , X_{j}(\omega)\neq x
\end{cases}
\end{gather}
$$

于是有

$$
\begin{gather}
F_{n}(x,\omega)-F_{n}(x-,\omega)= \dfrac{1}{n}\sum_{j=1}^{n} \eta_{j}(x,\omega)
\end{gather}
$$

并且由前文知存在零概率集 $N(x)$ 使得当 $\omega \in\Omega\setminus N(x)$ 时有

$$
\begin{gather}
F_{n}(x,\omega)-F_{n}(x-,\omega)\to F(x)-F(x-)
\end{gather}
$$

现在令 $N_{1}=\bigcup_{x \in Q\cup J}N(x)$，则 $\mathbb{P}(N_{1})=0$，并且当 $\omega \in\Omega\setminus N_{1}$ 时，上式对 $x \in J$ 成立，并且也有

$$
\begin{gather}
F_{n}(x,\omega)\to F(x)
\end{gather}
$$

对 $x \in Q$ 成立。于是定理的结论就由以下引理给出：

**引理 3.5.2**

设 $F_{n},F$ 是分布函数，$Q$ 和 $J$ 定义如上，那么如果

$$
\begin{gather}
\forall x \in Q, F_{n}(x)\to F(x) \\
\forall x \in J, F_{n}(x)-F_{n}(x-)\to F(x)-F(x-)
\end{gather}
$$

则 $F_{n}$ 一致收敛于 $F$.

**证明**

我们使用反证法，假设 $F_{n}$ 不一致收敛，则存在 $\varepsilon>0$ 和子序列 $(F_{n_{k}})$，以及实数序列 $(x_{k})$ 使得对任意 $k$ 有

$$
\begin{gather}
|F_{n_{k}}(x_{k})-F(x_{k})|\geq\varepsilon
\end{gather}
$$

当 $x_{k}\to \pm \infty$ 时上式显然不成立，因此我们可以假设存在子序列（任记为 $x_{k}$）收敛于 $\xi \in \mathbb{R}$. 下面设 $k$ 足够大，$r_{1},r_{2}\in Q$，$r_{1}<\xi<r_{2}$，则有以下四种情况：

(i). $x_{k}$ 递增至 $\xi$，$F_{n_{k}}(x_{k})>F(x_{k})$：

$$
\begin{align}
\varepsilon&\leq F_{n_{k}}(x_{k})-F(x_{k})\leq F_{n_{k}}(\xi-)-F(r_{1}) \\
&\leq F_{n_{k}}(\xi-)-F_{n_{k}}(\xi)+F_{n_{k}}(r_{2})-F(r_{2})+F(r_{2})-F(r_{1})
\end{align}
$$

(ii). $x_{k}$ 递增至 $\xi$，$F_{n_{k}}(x_{k})<F(x_{k})$：

$$
\begin{align}
\varepsilon&\leq F(x_{k})-F_{n_{k}}(x_{k})\leq F(\xi-)-F_{n_{k}}(r_{1}) \\
&\leq F(\xi-)-F(r_{1})+F(r_{1})-F_{n_{k}}(r_{1})
\end{align}
$$

(iii). $x_{k}$ 递减至 $\xi$，$F_{n_{k}}(x_{k})>F(x_{k})$：

$$
\begin{align}
\varepsilon&\leq F_{n_{k}}(x_{k})-F(x_{k})\leq F_{n_{k}}(r_{2})-F(\xi) \\
&\leq F_{n_{k}}(r_{2})-F_{n_{k}}(r_{1})+F_{n_{k}}(r_{1})-F(r_{1})+F(r_{1})-F(\xi)
\end{align}
$$

(iv). $x_{k}$ 递减至 $\xi$，$F_{n_{k}}(x_{k})<F(x_{k})$：

$$
\begin{align}
\varepsilon&\leq F(x_{k})-F_{n_{k}}(x_{k})\leq F(r_{2})-F_{n_{k}}(\xi) \\
&\leq F(r_{2})-F(r_{1})+F(r_{1})-F_{n_{k}}(r_{1})+F_{n_{k}}(r_{1})-F_{n_{k}}(\xi)
\end{align}
$$

在四种情况中，首先令 $k\to \infty$，再令 $r_{1}\to \xi,r_{2}\to \xi$，则每种情况下不等式的最后一项均趋于 $0$，这一矛盾就表明 $F_{n}$ 一致收敛于 $F$.

下一个例子来源于更新论。令 $(X_{n})$ 是 i.i.d. 的随机变量，进一步，我们假设 $X_{n}$ 是非负的，并且不是 a.s. 为零的，于是它们的共同期望严格大于 $0$. 在更新论中，随机变量 $X_{n}$ 被看作是某个物体的“寿命”，或者某种过程的“重现周期”，并且我们要解决的问题有如下形式：给定一个时间点，在它之前发生了多少次更新？最近的一次更新距今有多少时间？下一次更新还有多久？

我们先来考虑第一个问题。给定时刻 $t\geq 0$，令 $N(t,\omega)$ 表示 $t$ 时刻之前发生的更新的次数，则我们有

$$
\begin{gather}
\{ \omega \mid N(t,\omega)=n \}=\{ \omega \mid S_{n}(\omega)\leq t<S_{n+1}(\omega) \}
\end{gather}
$$

对 $n\geq 0$ 成立，其中 $S_{0}=0$. 对 $n\leq m-1$ 求和，则有

$$
\begin{gather}
\{ \omega \mid N(t,\omega)<m \}=\{ \omega \mid S_{m}(\omega)>t \}
\end{gather}
$$

这表明对任意 $t>0$，$N(t,\cdot)$ 是一个离散随机变量，其值域是自然数集。这样一族随机变量 $\{ N(t) \}_{t \in [0,\infty)}$ 就称为一个**更新过程**。

下面我们先来证明

$$
\begin{gather}
\lim_{ t \to \infty } N(t)=\infty \quad \text{a.s.}
\end{gather}
$$

即，当时间趋于无穷时，更新次数也趋于无穷。由于 $N(t,\omega)$ 关于 $t$ 是递增的，因此上面的极限对任意 $\omega$ 都存在。假设存在 $M>0$ 使得

$$
\begin{gather}
\mathbb{P}(\sup_{0\leq t<\infty} N(t)<M)> 0
\end{gather}
$$

那么我们就有

$$
\begin{gather}
\mathbb{P}(S_{M}=\infty)> 0
\end{gather}
$$

而这是不可能的，因为 $(X_{n})$ 是几乎处处有限的。

接着我们令

$$
\begin{gather}
0<m=\mathbb{E}(X_{1})\leq \infty
\end{gather}
$$

并首先假设 $m<\infty$，于是根据强大数定律，$S_{n} / n \to m$ a.s.，即存在零概率集 $Z_{1}$ 使得对任意 $\omega \in\Omega\setminus Z_{1}$ 有

$$
\begin{gather}
\lim_{ n \to \infty }  \dfrac{S_{n}(\omega)}{n} = m
\end{gather}
$$

此外，我们之前证明了存在零概率集 $Z_{2}$ 使得对任意 $\omega \in\Omega\setminus Z_{2}$ 有

$$
\begin{gather}
\lim_{ t \to \infty } N(t,\omega)=\infty
\end{gather}
$$

于是对任意 $\omega \in\Omega\setminus (Z_{1}\cup Z_{2})$ 就有

$$
\begin{gather}
\lim_{ t \to \infty } \dfrac{S_{N(t,\omega)}(\omega)}{N(t,\omega)}=m
\end{gather}
$$

根据 $N(t,\omega)$ 的定义，$S_{N(t,\omega)}(\omega)$ 的值应当接近于 $t$，这一结果可以加强为以下的定理：

**定理 3.5.3**

对于 $0<m\leq \infty$，有

$$
\begin{gather}
\lim_{ t \to \infty } \dfrac{N(t)}{t}= \dfrac{1}{m} \quad \text{a.s.} \\
\lim_{ t \to \infty } \dfrac{\mathbb{E}(N(t))}{t}=\dfrac{1}{m}
\end{gather}
$$

其中 $1 / \infty=0$.

**证明**

根据 $N(t)$ 的定义知对任意 $\omega$ 有

$$
\begin{gather}
S_{N(t,\omega)}(\omega)\leq t<S_{N(t,\omega)+1}(\omega)
\end{gather}
$$

于是当 $t$ 足够大使得 $N(t,\omega)>0$ 时，有

$$
\begin{gather}
\dfrac{S_{N(t,\omega)}(\omega)}{N(t,\omega)}\leq \dfrac{t}{N(t,\omega)}\leq \dfrac{S_{N(t,\omega)+1}(\omega)}{N(t,\omega)+1} \dfrac{N(t,\omega)+1}{N(t,\omega)}
\end{gather}
$$

令 $t \to \infty$，则当 $m<\infty$ 时有 $\dfrac{t}{N(t,\omega)}\to m$ a.s.

$m=\infty$ 的情况可由以下结论推出：如果 $\mathbb{E}(X_{1})=\infty$，那么 $S_{n} / n\to \infty$ a.s. 对 $A>0$ 我们定义

$$
\begin{gather}
Y_{n}(\omega)=\begin{cases}
X_{n}(\omega) & ,X_{n}(\omega)\leq A \\
A & ,X_{n}(\omega)>A
\end{cases}
\end{gather}
$$

则 $\mathbb{E}(Y_{1})<\infty$，且当 $A\to \infty$ 时有 $\mathbb{E}(Y_{1})\to \mathbb{E}(X_{1})=\infty$. 根据强大数定律我们有

$$
\begin{gather}
\dfrac{1}{n}\sum_{j=1}^{n} Y_{j} \to \mathbb{E}(Y_{1}) \quad \text{a.s.}
\end{gather}
$$

另一方面，我们有 $X_{n}\geq Y_{n}$，因此 $S_{n} / n\geq \sum_{j=1}^{n}Y_{j} / n$，从而有

$$
\begin{gather}
\liminf_{ n \to \infty } \dfrac{S_{n}}{n}\geq \lim_{ n \to \infty } \dfrac{1}{n}\sum_{j=1}^{n} Y_{j}=\mathbb{E}(Y_{1})\quad \text{a.s.}
\end{gather}
$$

令 $A\to \infty$，即证 $S_{n} / n\to \infty$ a.s.

接下来，我们考虑第二个结论。由于 $X_{n}$ 不是 a.s. 为零的，故存在 $\delta>0$ 使得 $\mathbb{P}(|X_{n}|\geq\delta)=p>0$，定义

$$
\begin{gather}
X_{n}'(\omega)=\begin{cases}
\delta & ,X_{n}(\omega)\geq\delta \\
0 & ,X_{n}(\omega)<\delta
\end{cases}
\end{gather}
$$

并且令 $S_{n}',N'(t)$ 是与随机变量 $(X_{n}')$ 相对应的量，显然我们有 $S_{n}'\leq S_{n}$，$N'(t)\geq N(t)$. 由于 $X_{n}' / \delta$ 服从参数为 $p$ 的 Bernoullian 分布，因此简单的计算表明

$$
\begin{gather}
\mathbb{E}(N'(t)^{2})=O\left( \dfrac{t^{2}}{\delta^{2}} \right)
\end{gather}
$$

因此对于固定的 $t$ 有

$$
\begin{gather}
\mathbb{E}\left( \left( \dfrac{N(t)}{t} \right)^{2} \right)\leq \mathbb{E}\left( \left( \dfrac{N'(t)}{t} \right)^{2} \right)=O(1)
\end{gather}
$$

根据第一个结论知 $N(t) / t$ 依分布收敛于 $\delta_{1 / m}$，则应用定理 2.5.2，其中 $p=2$，$r=1$ 就完成了证明。

现在我们回过头来看看随机变量 $S_{N(t,\cdot)}(\cdot)$，它是随机变量的和，并且这个和的项数也是一个随机变量。上面的极限式表明，当 $t\to \infty$ 时，$\mathbb{E}(S_{N(t)})$ 应当接近于 $m\mathbb{E}(N(t))=\mathbb{E}(X_{1})\mathbb{E}(N(t))$. 这是对期望的可加性的一个惊人的推广：它甚至对项数“随机”的求和也适用。这一结果是以下定理的特殊形式：

**定理 3.5.4** Wald 等式

设 $(\Omega,\mathcal{F},\mathbb{P})$ 是概率空间，$(X_{n})$ 是 i.i.d. 的随机变量，且具有有限期望，对 $k\geq 1$，设 $\mathcal{F}_{k}$ 为随机变量 $\{ X_{j} \mid 1\leq j\leq k \}$ 生成的 $\sigma$-域，则如果 $N$ 是一个正整数值的随机变量，满足对任意 $k\geq 1$ 有

$$
\begin{gather}
\{ \omega \mid N(\omega)\leq k \} \in \mathcal{F}_{k}
\end{gather}
$$

并且 $\mathbb{E}(N)<\infty$，那么有

$$
\begin{gather}
\mathbb{E}(S_{N})=\mathbb{E}(X_{1})\mathbb{E}(N)
\end{gather}
$$

**证明**

取 $S_{0}=0$，则我们有

$$
\begin{align}
\mathbb{E}(S_{N})=\int S_{N}\mathrm{d} \mathbb{P}&=\sum_{k=1}^{\infty} \int_{N=k} S_{N} \mathrm{d} \mathbb{P}=\sum_{k=1}^{\infty} \sum_{j=1}^{k} \int_{N=k}X_{j}\mathrm{d} \mathbb{P} \\
&=\sum_{j=1}^{\infty} \sum_{k=j}^{\infty} \int_{N=k}X_{j}\mathrm{d} \mathbb{P}=\sum_{j=1}^{\infty} \int_{N\geq j}X_{j}\mathrm{d} \mathbb{P} \\
&=\sum_{j=1}^{\infty} \left( \mathbb{E}(X_{1})-\int_{N\leq j-1}X_{j}\mathrm{d} \mathbb{P} \right)
\end{align}
$$

由于 $\{ N\leq j-1 \}$ 与 $X_{n}$ 是独立的，故积分项为 $\mathbb{E}(X_{1})\mathbb{P}(N\leq j-1)$，从而有

$$
\begin{gather}
\mathbb{E}(S_{N})=\sum_{j=1}^{\infty} \mathbb{E}(X_{1})\mathbb{P}(N\geq j)=\mathbb{E}(X_{1})\mathbb{E}(N)
\end{gather}
$$

现在我们只需验证上面的交换求和顺序是有效的。将 $X_{1}$ 换成 $|X_{1}|$，通过相同的论证，我们得到该二重求和的值为 $\mathbb{E}(|X_{1}|)\mathbb{E}(N)<\infty$，因此 Fubini 定理保证了我们可以交换求和的顺序，这就完成了证明。

本节的最后一个例子是概率论在经典分析中的应用，这其中最有代表性，也是最著名的一个范例，当属 Bernstein 对于 Weierstrass 逼近定理的证明。

**定理 3.5.5**

设 $f \in C([0,1],\mathbb{R})$，定义 **Bernstein 多项式**如下：

$$
\begin{gather}
p_{n}(x)=\sum_{k=0}^{n} f\left( \dfrac{k}{n} \right) \binom{ n }{ k } x^{k}(1-x)^{n-k}
\end{gather}
$$

则 $p_{n}$ 在 $[0,1]$ 上一致收敛于 $f$.

**证明**

考虑 i.i.d. 的随机变量 $X_{n}$，其服从参数为 $x$ 的 Bernoullian 分布，并令 $S_{n}=\sum_{k=1}^{n}X_{k}$，则根据二项分布公式得

$$
\begin{gather}
\mathbb{P}(S_{n}=k)=\binom{ n }{ k } x^{k}(1-x)^{n-k}
\end{gather}
$$

于是

$$
\begin{gather}
p_{n}(x)=\mathbb{E}\left( f\left( \dfrac{S_{n}}{n} \right) \right)
\end{gather}
$$

根据强大数定律，$S_{n} / n\to x$ a.s.，从而依概率收敛。由于 $f$ 是连续的，故由定理 2.4.10 的证明知，$f(S_{n} / n)\to f(x)$ 依概率，从而有

$$
\begin{gather}
p_{n}(x)=\mathbb{E}\left( f\left( \dfrac{S_{n}}{n} \right) \right)\to \mathbb{E}(f(x))=f(x)
\end{gather}
$$

这就证明了逐点收敛性，下面我们来证明一致性。对任意 $\delta>0$，我们有

$$
\begin{align}
|p_{n}(x)-f(x)|&\leq \mathbb{E}\left( \left\lvert  f\left( \dfrac{S_{n}}{n} \right)-f(x)  \right\rvert  \right) \\
&\leq \int_{|S_{n} / n-x|\leq \delta} \left\lvert  f\left( \dfrac{S_{n}}{n} \right)-f(x)  \right\rvert \mathrm{d} \mathbb{P} \\
&+\int_{|S_{n} / n-x|> \delta} \left\lvert  f\left( \dfrac{S_{n}}{n} \right)-f(x)  \right\rvert \mathrm{d} \mathbb{P}
\end{align}
$$

由于 $f$ 一致连续，故给定 $\varepsilon>0$，存在 $\delta>0$ 使得当 $|x-y|\leq\delta$ 时有 $|f(x)-f(y)|<\varepsilon / 2$，因此上式的第一项积分具有上界 $\varepsilon / 2$，而第二项具有上界

$$
\begin{align}
2\lVert f \rVert _{\infty} \mathbb{P}\left( \left\lvert  \dfrac{S_{n}}{n}-x  \right\rvert >\delta \right)&\leq 2\lVert f \rVert _{\infty} \dfrac{\sigma^{2}(S_{n} / n)}{\delta^{2}}=\dfrac{2\lVert f \rVert _{\infty}x(1-x)}{\delta^{2}n} \\
&\leq \dfrac{\lVert f \rVert _{\infty}}{2\delta^{2}n}
\end{align}
$$

于是当 $n\geq \lVert f \rVert_{\infty} / \delta^{2}\varepsilon$ 时，就有 $|p_{n}(x)-f(x)|\leq\varepsilon$，这就完成了证明。