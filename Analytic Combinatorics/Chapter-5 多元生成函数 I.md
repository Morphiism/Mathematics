许多科学问题都需要对组合对象的**参数**的概率特性获取精确的定量信息。例如，在设计、分析以及优化算法时，需要确定给定数据的随机特征，并通过均值或者是分布反映出来。类似的情况在概率论、统计学、计算机科学、信息论以及统计物理中均有出现。

确切的问题则是一个涉及两个参数的精细计数问题：即大小和一个额外特征，这就是本章所讨论的主题，并且它可以通过生成函数框架的一个自然扩展来解决。我们将看到，最初为统计组合对象的数量而开发的符号计数方法能够很好地应用于可构造类的参数的分析，无论它是无编号的还是有编号的。

**多元生成函数**（MGF）——普通的或指数的——可以被用于追踪组合对象的一组参数。从一个 MGF 出发，通常我们可以求出显式的概率分布，当显式分布不存在时，至少我们还能够求出其期望以及方差。对于**可继承的**参数而言，到目前为止的所有组合类都适用这种方式。从技术上来说，将组合构造与 MGF 联系起来的转换范式没有重大困难：它们是前几章针对单变量所发展的符号计数范式的一种自然的改进和完善。

# Section 1: 二元生成函数与概率分布

我们在前几章看到，一个数列 $(f_{n})$ 可以由一个单变量生成函数（普通或指数的）进行编码：

$$
\begin{gather}
(f_{n}) \longrightarrow f(z)=\begin{cases}
\displaystyle \sum_{n} f_{n}z^{n}  &  (\text{Ordinary GF}) \\
\displaystyle \sum_{n} f_{n} \dfrac{z^{n}}{n!}  &  (\text{Exponential GF})
\end{cases}
\end{gather}
$$

这种编码非常有用，因为组合类的构造能够直接转换为生成函数的运算，进而得到精确的组合计数公式。

类似地，考虑一个二维数组 $(f_{n,k})$，通常表示类 $\mathcal{F}$ 中的对象 $\varphi$ 的数量，其满足 $|\varphi|=n$ 且有参数 $\chi(\varphi)=k$. 我们可以用**二元生成函数**（BGF）来编码该数组，其中主变量 $z$ 编码 $n$，而次变量 $u$ 编码 $k$.

**定义 5.1.1** 二元生成函数（bivariate generating function）

一个二维数组 $(f_{n,k})$ 的（普通或指数的）**二元生成函数**是一个双变量形式幂级数

$$
\begin{gather}
f(z,u)=\begin{cases}
\displaystyle \sum_{n,k} f_{n,k} z^{n} u^{k}  & (\text{Ordinary BGF}) \\
\displaystyle \sum_{n,k} f_{n,k} \dfrac{z^{n}}{n!} u^{k}  & (\text{Exponential BGF})
\end{cases}
\end{gather}
$$

我们很快将看到，可构造类的参数计数可以通过 BGF 来进行。下面，我们介绍 BGF 的一些常用记号，我们定义**水平生成函数**

$$
\begin{gather}
f_{n}(u)=\sum_{k} f_{n,k} u^{k}
\end{gather}
$$

和**竖直生成函数**

$$
\begin{gather}
f^{\langle k \rangle }(z)=\begin{cases}
\displaystyle \sum_{n} f_{n,k} z^{n}  & (\text{Ordinary BGF}) \\
\displaystyle \sum_{n} f_{n,k} \dfrac{z^{n}}{n!}  & (\text{Exponential BGF})
\end{cases}
\end{gather}
$$

如果我们把 $(f_{n,k})$ 放在一个二维矩阵中，其中 $f_{n,k}$ 位于第 $n$ 行第 $k$ 列，那么上面的术语就变得清晰了，如图所示：

![](5-1.png)

显然，我们有下式成立：

$$
\begin{gather}
f(z,u)=\sum_{k} u^{k} f^{\langle k \rangle }(z)=\begin{cases}
\displaystyle \sum_{n} f_{n}(u) z^{n}  & (\text{Ordinary BGF}) \\
\displaystyle \sum_{n} f_{n}(u) \dfrac{z^{n}}{n!} & (\text{Exponential BGF})
\end{cases}
\end{gather}
$$

此外，当设置 $u=1$ 时，BGF 就退化为了原始的单变量生成函数，这表明了 BGF 与我们在前几章中发展的理论是相容的。

**例 5.1.2**

二项式系数 $\binom{ n }{ k }$ 统计了某个字符出现 $k$ 次且长度为 $n$ 的二进制字符串的数量。为求出它的 BGF，我们可以从最基本的 Newton 二项式定理出发得到水平生成函数：

$$
\begin{gather}
W_{n}(u)=\sum_{k} \binom{ n }{ k } u^{k}=(1+u)^{n}
\end{gather}
$$

进而得到普通 BGF

$$
\begin{gather}
W(z,u)=\sum_{n} (1+u)^{n}z^{n} =\dfrac{1}{1-z(1+u)}
\end{gather}
$$

当 $u=1$ 时，$W(z,1)=(1-2z)^{-1}$，这与第一章给出的公式一致。

此外，我们也可以从竖直生成函数出发：

$$
\begin{gather}
W^{\langle k \rangle }(z)=\sum_{n} \binom{ n }{ k } z^{n}=\dfrac{z^{k}}{(1-z)^{k+1}}
\end{gather}
$$

同样得到

$$
\begin{gather}
W(z,u)=\sum_{k} u^{k} \dfrac{z^{k}}{(1-z)^{k+1}}=\dfrac{1}{1-z} \dfrac{1}{1-u \frac{z}{1-z}}=\dfrac{1}{1-z(1+u)}
\end{gather}
$$

**例 5.1.3**

Stirling 循环数 $\left[ \begin{matrix}n \\ k\end{matrix} \right]$ 统计了长度为 $n$ 且有 $k$ 个循环的置换的数量。它的竖直 EGF 为

$$
\begin{gather}
P^{\langle k \rangle }(z)=\sum_{n} \left[ \begin{matrix}n \\ k\end{matrix} \right] \dfrac{z^{n}}{n!} = \dfrac{1}{k!} \left( \ln \dfrac{1}{1-z} \right)^{k}
\end{gather}
$$

从而其指数 BGF 如下：

$$
\begin{gather}
P(z,u)=\sum_{k} u^{k} P^{\langle k \rangle }(z)=\exp(-u \ln(1-z))=(1-z)^{-u}
\end{gather}
$$

由此，我们可以提取出它的水平生成函数

$$
\begin{gather}
P_{n}(u)=(-1)^{n} \binom{ -u }{ n } =u(u+1)\cdots (u+n-1)
\end{gather}
$$

这一多项式被称为指标为 $n$ 的“Stirling 循环多项式”，它完整地描述了所有长度为 $n$ 的置换中循环数量的分布。此外，通过提取系数，我们可以得到 Stirling 循环数的一个递推关系

$$
\begin{gather}
P_{n}(u)=P_{n-1}(u)(u+n-1) \implies \left[ \begin{matrix}n \\ k\end{matrix} \right]=(n-1)\left[ \begin{matrix}n-1 \\ k\end{matrix} \right]+\left[ \begin{matrix}n-1 \\ k-1\end{matrix} \right]
\end{gather}
$$

这一关系也有一个组合解释：元素 $n$ 或者是一个不动点，或者位于一个长度 $\geq 2$ 的循环中，在第二种情况下共有 $n-1$ 个位置来放置 $n$.

接下来，我们将展示如何通过 BGF 推导矩、方差甚至更加精细的分布性质。我们将主要考虑按照大小以及带有一个额外参数的计数问题。为了简化记号，我们引入**基本因子**序列 $(\omega_{n})$，定义为

$$
\begin{gather}
\omega_{n}=\begin{cases}
1 &  (\text{Ordinary GF}) \\
n! &  (\text{Exponential GF})
\end{cases}
\end{gather}
$$

从而 OGF 与 EGF 可以统一地表示为

$$
\begin{gather}
f(z)=\sum_{n} f_{n} \dfrac{z^{n}}{\omega_{n}}, \quad f_{n}=\omega_{n} [z^{n}] f(z)
\end{gather}
$$

**定义 5.1.4** 二元生成函数（bivariate generating function）

设 $\mathcal{A}$ 是一个组合类，一个（标量）**参数**是一个函数 $\chi\colon \mathcal{A}\to \mathbb{N}$. 二维数组

$$
\begin{gather}
A_{n,k}=\lvert \{ \alpha \in \mathcal{A} \mid |\alpha|=n, \chi(\alpha)=k \} \rvert 
\end{gather}
$$

称为有序对 $(\mathcal{A},\chi)$ 的**计数序列**，它的**二元生成函数**定义为

$$
\begin{gather}
A(z,u)=\sum_{n,k} A_{n,k} \dfrac{z^{n}}{\omega_{n}} u^{k}
\end{gather}
$$

称变量 $z$ 指示了大小而 $u$ 指示了参数 $\chi$.

给定一个组合类 $\mathcal{A}$，集合 $\mathcal{A}_{n}$ 上的均匀分布为每个 $\alpha \in \mathcal{A}_{n}$ 赋予了 $1 / A_{n}$ 的概率，我们将使用 $\mathbb{P}_{\mathcal{A}_{n}}$ 或 $\mathbb{P}_{n}$ 或 $\mathbb{P}$ 来表示其对应的概率测度。

对于 $\mathcal{A}$ 上的参数 $\chi$，它在每个 $\mathcal{A}_{n}$ 上都定义了一个离散随机变量：

$$
\begin{gather}
\mathbb{P}_{\mathcal{A}_{n}}(\chi=k)=\dfrac{A_{n,k}}{A_{n}}=\dfrac{A_{n,k}}{\sum_{k} A_{n,k}}
\end{gather}
$$

给定一个离散随机变量 $X$，我们定义其**概率生成函数**（PGF）为

$$
\begin{gather}
p(u)=\sum_{k} \mathbb{P}(X=k)u^{k}
\end{gather}
$$

于是根据上面的讨论，我们立即得到：

**定理 5.1.5**

设 $A(z,u)$ 是组合类 $\mathcal{A}$ 与定义在其上的参数 $\chi$ 的 BGF，则离散随机变量 $\chi|_{\mathcal{A}_{n}}$ 的概率生成函数由下式给出：

$$
\begin{gather}
\sum_{k} \mathbb{P}_{\mathcal{A}_{n}}(\chi=k)u^{k} = \dfrac{[z^{n}]A(z,u)}{[z^{n}]A(z,1)}
\end{gather}
$$

即 PGF 是水平生成函数的归一化版本。

随机变量的矩蕴含着大量关于其分布的信息。对于一个离散随机变量 $X$ 和函数 $f$，$f(X)$ 的期望根据定义就是

$$
\begin{gather}
\mathbb{E}(f(X))=\sum_{k} f(k) \mathbb{P}(X=k)
\end{gather}
$$

$X$ 的 $r$ 阶矩就定义为

$$
\begin{gather}
\mathbb{E}(X^{r})=\sum_{k} k^{r} \mathbb{P}(X=k)
\end{gather}
$$

从而 $X$ 的期望、方差以及标准差分别就是

$$
\begin{gather}
\mathbb{E}(X) ,\quad \mathrm{Var}(X)=\mathbb{E}(X^{2})-\mathbb{E}(X)^{2}, \quad \sigma(X)=\sqrt{ \mathrm{Var}(X) }
\end{gather}
$$

$X$ 的期望通常与做大量观测时数据的算术平均值接近，这一性质被称为“弱大数定律”。而标准差则衡量了数据与期望相比的偏离程度，它以平方平均的方式来衡量这一点。

在组合学中，**阶乘矩**

$$
\begin{gather}
\mathbb{E}(X(X-1)\cdots (X-r+1))
\end{gather}
$$

也有重要作用，它与 BGF 的联系由以下定理给出：

**定理 5.1.6**

组合类 $\mathcal{A}$ 上的参数 $\chi$ 的 $r$ 阶阶乘矩可以由对 BGF 求导得到：

$$
\begin{gather}
\mathbb{E}_{\mathcal{A}_{n}}(\chi(\chi-1)\cdots(\chi-r+1))=\dfrac{[z^{n}] \partial_{u}^{r}A(z,u)|_{u=1}}{[z^{n}]A(z,1)}
\end{gather}
$$

特别地，前两个矩有等式

$$
\begin{gather}
\mathbb{E}_{\mathcal{A}_{n}}(\chi)=\dfrac{[z^{n}]\partial_{u}A(z,u)|_{u=1}}{[z^{n}]A(z,1)} \\
\mathbb{E}_{\mathcal{A}_{n}}(\chi^{2})=\mathbb{E}_{\mathcal{A}_{n}}(\chi(\chi-1))+\mathbb{E}_{\mathcal{A}_{n}}(\chi)
\end{gather}
$$

进而可以得到方差和标准差

$$
\begin{gather}
\mathrm{Var}(\chi)=\sigma(\chi)^{2}=\mathbb{E}(\chi^{2})-\mathbb{E}(\chi)^{2}
\end{gather}
$$

换言之，量

$$
\begin{gather}
\Omega_{n}^{(k)}=\omega_{n} [z^{n}] \partial_{u}^{k} A(z,u)|_{u=1}
\end{gather}
$$

在经过归一化后就给出了阶乘矩：

$$
\begin{gather}
\mathbb{E}(\chi(\chi-1)\cdots(\chi-k+1))=\dfrac{1}{A_{n}}\Omega_{n}^{(k)}
\end{gather}
$$

特别地，$\Omega_{n}^{(1)}$ 给出了 $\mathcal{A}_{n}$ 中参数 $\chi$ 的累计值：

$$
\begin{gather}
\Omega_{n}^{(1)}=\omega_{n}[z^{n}] \partial_{u}A(z,u)|_{u=1}=\sum_{\alpha \in \mathcal{A}_{n}} \chi(\alpha)=A_{n}\mathbb{E}_{\mathcal{A}_{n}}(\chi)
\end{gather}
$$

根据这个原因，序列 $(\Omega_{n}^{(1)})$ 的生成函数 $\Omega^{(1)}(z)$ 通常被称为**累计生成函数**（CGF），它有组合形式

$$
\begin{gather}
\Omega^{(1)}(z)=\sum_{n} \mathbb{E}_{\mathcal{A}_{n}}(\chi) A_{n} \dfrac{z^{n}}{\omega_{n}} =\sum_{\alpha \in \mathcal{A}} \chi(\alpha) \dfrac{z^{|\alpha|}}{\omega_{|\alpha|}}
\end{gather}
$$

下面我们就来利用定理 5.1.6 来求一些分布的矩。首先我们来看二项分布，它可以被定义为长度为 $n$ 的二进制字符串中某个特定字符的出现次数的分布，于是根据前面求出的 BGF

$$
\begin{gather}
W(z,u)=\dfrac{1}{1-z-zu}
\end{gather}
$$

我们有

$$
\begin{gather}
\Omega^{(r)}(z)=\partial_{u}^{r} W(z,u) |_{u=1}=\dfrac{r!z^{r}}{(1-2z)^{r+1}}
\end{gather}
$$

提取系数并归一化，可得 $1,2,\dots,r$ 阶阶乘矩为

$$
\begin{gather}
\dfrac{n}{2}, \dfrac{n(n-1)}{4}, \dfrac{n(n-1)(n-2)}{8},\dots, \dfrac{r!}{2^{r}}\binom{ n }{ r } 
\end{gather}
$$

从而其期望与方差为 $\dfrac{n}{2}$ 和 $\dfrac{n}{4}$，进而有标准差 $\dfrac{1}{2}\sqrt{ n }$，比期望的阶更低，这表明二项分布的数据在极限情况下集中在均值附近，我们之后将会提到这一点。

现在我们转到 Stirling 循环数，对 BGF

$$
\begin{gather}
P(z,u)=(1-z)^{-u}
\end{gather}
$$

中的变量 $u$ 求导，并设 $u=1$ 就得到了期望：

$$
\begin{gather}
\mathbb{E}_{n}(\chi)=[z^{n}] \dfrac{1}{1-z} \ln \dfrac{1}{1-z}=1+\dfrac{1}{2}+\dots+\dfrac{1}{n}
\end{gather}
$$

这就是调和数 $H_{n}$，因此长度为 $n$ 的随机置换平均含有约 $\ln n+\gamma$ 个循环。更高阶的矩可以通过 Stirling 循环多项式来得到，我们有 Stirling 循环数的 PGF

$$
\begin{gather}
\dfrac{1}{n!}u(u+1)\cdots(u+n-1)=\exp\left( vH_{n}-\dfrac{v^{2}}{2}H_{n}^{(2)}+\dfrac{v^{3}}{3}H_{n}^{(3)}-\cdots \right)
\end{gather}
$$

其中 $u=1+v$，$H_{n}^{(r)}=\sum_{j=1}^{n}j^{-r}$ 是广义调和数。于是，Stirling 循环数分布的任意阶矩都是广义调和数的多项式，特别地，我们有

$$
\begin{gather}
\sigma_{n}^{2}=\sum_{k=1}^{n} \dfrac{1}{k} - \sum_{k=1}^{n} \dfrac{1}{k^{2}}=\ln n+\gamma- \dfrac{\pi^{2}}{6}+O(n^{-1})
\end{gather}
$$

进而有渐近公式

$$
\begin{gather}
\sigma_{n}\sim \sqrt{ \ln n }
\end{gather}
$$

同样比期望 $\ln n$ 低一个阶，因此当 $n$ 足够大时，与均值产生较大偏离的点出现的概率可以忽略不计。

定性地说，概率分布可以被分为两类：一类是**分散的**，即标准差的阶至少与期望的阶相同（比如 $[0..n]$ 上的均匀分布），另一类则是**集中的**，即标准差的阶比期望的阶小（比如二项分布与 Stirling 循环数分布）。上述直观结论可以由 Markov 不等式和 Chebyshev 不等式支撑，它们利用了前两个矩所提供的信息。

**定理 5.1.7** Markov-Chebyshev 不等式

设 $X$ 是一个非负随机变量，$\mathbb{E}(X)>0$，$Y$ 是一个实值随机变量，$\sigma(Y)>0$，则对任意 $t>0$ 有

$$
\begin{align}
\mathbb{P}(X\geq t\mathbb{E}(X))  & \leq \dfrac{1}{t}  & (\text{Markov}) \\
\mathbb{P}(|Y-\mathbb{E}(Y)|\geq t\sigma(Y)) & \leq \dfrac{1}{t^{2}}  & (\text{Chebyshev})
\end{align}
$$

**证明**

我们有

$$
\begin{gather}
\mathbb{E}(X)=\int X\mathrm{d} \mathbb{P}\geq \int_{X\geq t\mathbb{E}(X)} X\mathrm{d} \mathbb{P}=t\mathbb{E}(X) \mathbb{P}(X\geq t\mathbb{E}(X))
\end{gather}
$$

两边消去 $\mathbb{E}(X)$ 即证 Markov 不等式。在不等式中令 $X=(Y-\mathbb{E}(Y))^{2}$ 即得 Chebyshev 不等式。

这个结果告诉我们，远大于均值的概率必须衰减（Markov），而这种衰减的上界由分布的标准差来进行度量（Chebyshev）。

下一个定理形式化了“分布集中”的概念，它适用于一族由正整数进行索引的概率分布。

**定理 5.1.8**

设 $(X_{n})$ 是一族随机变量，其期望 $\mu_{n}=\mathbb{E}(X_{n})$ 和标准差 $\sigma_{n}=\sigma(X_{n})>0$ 满足

$$
\begin{gather}
\lim_{ n \to \infty } \dfrac{\sigma_{n}}{\mu_{n}}=0
\end{gather}
$$

那么 $(X_{n})$ 的分布是**集中的**，即对任意 $\varepsilon>0$ 有

$$
\begin{gather}
\lim_{ n \to \infty } \mathbb{P}\left( 1-\varepsilon\leq \dfrac{X_{n}}{\mu_{n}}\leq 1+\varepsilon \right)=1
\end{gather}
$$

**证明**

这一定理是 Chebyshev 不等式的直接应用，我们有

$$
\begin{gather}
\mathbb{P}(|X_{n}-\mu_{n}|>\varepsilon|\mu_{n}|)\leq \dfrac{\mathrm{Var}(X_{n})}{\varepsilon^{2}\mu_{n}^{2}}=\dfrac{1}{\varepsilon^{2}}\left( \dfrac{\sigma_{n}}{\mu_{n}} \right)^{2} \to 0
\end{gather}
$$

从而有

$$
\begin{gather}
\lim_{ n \to \infty } \mathbb{P}\left( \left\lvert  \dfrac{X_{n}}{\mu_{n}}-1  \right\rvert \leq\varepsilon \right)=1-\lim_{ n \to \infty } \mathbb{P}\left( \left\lvert  \dfrac{X_{n}}{\mu_{n}}-1  \right\rvert >\varepsilon \right)=1
\end{gather}
$$

定理 5.1.8 中的集中性质表明，随着 $n$ 的增大，$X_{n}$ 的值在平均意义上越来越接近均值 $\mu_{n}$. 在概率论中我们称这样的极限性质为 $X_{n} / \mu_{n}$ **依概率收敛**于 $1$，记作

$$
\begin{gather}
\dfrac{X_{n}}{\mu_{n}} \overset{P}{\longrightarrow} 1
\end{gather}
$$

这一性质是概率论中**弱大数定律**的一个特例。更为精细的分布估计是最后一章我们要讨论的重点。

# Section 2: 无编号类与普通 MGF

在本节和下一节中，我们将讨论如何从组合构造中直接确定组合类的 BGF：它由符号计数方法的一个自然推广给出，并以多元生成函数（MGF）进行形式化表述。这种生成函数可以将有限个（甚至在极限意义下，可数个）组合参数纳入考虑范围。BGF 则作为 MGF 的一种特殊情况出现。

**定义 5.2.1** 组合参数（combinatorial parameter）

设 $\mathcal{A}$ 是一个组合类，一个**组合参数**是函数 $\chi=(\chi_{1},\dots,\chi_{d})\colon \mathcal{A}\to \mathbb{N}^{d}$，关于大小与参数 $\chi$ 的 $\mathcal{A}$ 的**计数序列**定义为

$$
\begin{gather}
A_{n,k_{1},\dots,k_{d}}=\lvert \{ \alpha \in \mathcal{A} \mid |\alpha|=n, \chi_{1}(\alpha)=k_{1},\dots,\chi_{d}(\alpha)=k_{d} \} \rvert 
\end{gather}
$$

为了简化记号，我们引入以下的多重索引约定：设 $\mathbf{x}=(x_{1},\dots,x_{d})$ 是一个形式变量构成的 $d$ 维向量，$\mathbf{k}=(k_{1},\dots,k_{d})$ 是 $d$ 维的整数向量，那么我们定义

$$
\begin{gather}
\mathbf{x}^{\mathbf{k}}=x_{1}^{k_{1}}\cdots x_{d}^{k_{d}}
\end{gather}
$$

利用这种记号，我们给出以下定义：

**定义 5.2.2** 多元生成函数（multivariate generating function）

设 $A_{n,\mathbf{k}}$ 是一个序列，由 $n\in \mathbb{N}$ 和 $\mathbf{k}\in \mathbb{N}^{d}$ 进行索引，则它的**多元生成函数**（MGF）定义为形式幂级数

$$
\begin{gather}
A(z,\mathbf{u})=\begin{cases}
\displaystyle \sum_{n,\mathbf{k}} A_{n,\mathbf{k}}\mathbf{u}^{\mathbf{k}}z^{n}  & (\text{Ordinary MGF}) \\
\displaystyle \sum_{n,\mathbf{k}} A_{n,\mathbf{k}}\mathbf{u}^{\mathbf{k}} \dfrac{z^{n}}{n!}  & (\text{Exponential MGF})
\end{cases}
\end{gather}
$$

给定组合类 $\mathcal{A}$ 和参数 $\chi$，二元组 $(\mathcal{A},\chi)$ 的 MGF 定义为其计数序列的 MGF. 等价地，其有组合形式

$$
\begin{gather}
A(z,\mathbf{u})=\begin{cases}
\displaystyle \sum_{\alpha \in \mathcal{A}} \mathbf{u}^{\chi(\alpha)}z^{|\alpha|}  & (\text{Unlabelled class}) \\
\displaystyle \sum_{\alpha \in \mathcal{A}} \mathbf{u}^{\chi(\alpha)} \dfrac{z^{|\alpha|}}{|\alpha|!}  & (\text{Labelled class})
\end{cases}
\end{gather}
$$

我们也称变量 $\mathbf{u}$ 标记了参数 $\chi$ 而 $z$ 标记了大小。

显然，根据定义，如果 $\mathbf{1}=(1,\dots,1)$，那么 $A(z,\mathbf{1})$ 就与 $\mathcal{A}$ 的一元生成函数相同。因此，我们可以将 MGF 看成是前几章中的生成函数理论的一个扩展。特别地，如果除了某个 $u_{j}$ 外其余的 $u$ 均等于 $1$，那么我们就可以得到一个 BGF，从而就可以应用第一节中的方法来求出组合类的概率性质，如均值、矩等等。

对于能够从子结构继承的参数（定义见下文）来说，它们可以通过符号计数方法的一种直接扩展来进行计数。适当地使用多重索引约定，在前几章给出的转换规则甚至可以逐字逐句地移动到 MGF 上，这就自动地给出了大量多元计数问题的答案。

**定义 5.2.3** 继承的（inherited）

设 $(\mathcal{A},\chi),(\mathcal{B},\xi),(\mathcal{C},\zeta)$ 是组合类，赋予了具有相同维度 $d$ 的参数，则在下面的情况下，参数 $\chi$ 称为是**继承的**：

- 当 $\mathcal{A}=\mathcal{B}+\mathcal{C}$ 时，有

$$
\begin{gather}
\chi(\omega)=\begin{cases}
\xi(\omega), & \omega \in \mathcal{B} \\
\zeta(\omega), & \omega \in \mathcal{C}
\end{cases}
\end{gather}
$$

- 当 $\mathcal{A}=\mathcal{B}\times \mathcal{C}$ 时，有

$$
\chi(\beta,\gamma)=\xi(\beta)+\zeta(\gamma)
$$

- 当 $\mathcal{A}=\mathscr{C}(\mathcal{B})$，其中 $\mathscr{C}$ 是 $\mathrm{Seq},\mathrm{MSet},\mathrm{PSet},\mathrm{Cyc}$ 其中之一时，有

$$
\chi(\beta_{1},\dots,\beta_{r})=\xi(\beta_{1})+\dots+\xi(\beta_{r})
$$

当 $\mathcal{A}$ 上的参数 $\chi$ 继承自 $\mathcal{B},\mathcal{C}$ 上的参数 $\xi,\zeta$ 时，我们可以写

$$
\begin{gather}
(\mathcal{A},\chi)=(\mathcal{B},\xi)+(\mathcal{C},\zeta), \quad (\mathcal{A},\chi)=(\mathcal{B},\xi)\times(\mathcal{C},\zeta), \quad (\mathcal{A},\chi)=\mathscr{C}(\mathcal{B},\xi)
\end{gather}
$$

这一继承性的定义与我们对复合结构的大小的定义是一致的：无交并的大小由情况定义，而元组的大小由加法得到。

反过来说，大小 $\lvert \cdot \rvert$ 也可以视为一种特殊的继承参数，将其与其它的参数并列放置，我们给出**增广组合参数** $\overline{\chi}=(\chi_{0},\chi_{1},\dots,\chi_{d})$，其中 $\chi_{0}(\alpha)=|\alpha|$ 是 $\alpha$ 的大小，以及它对应的极为简单且对称的 MGF：

$$
\begin{gather}
A(\mathbf{z})=\sum_{\mathbf{k}} A_{\mathbf{k}}\mathbf{z}^{\mathbf{k}}=\sum_{\alpha \in \mathcal{A}} \mathbf{z}^{\overline{\chi}(\alpha)}
\end{gather}
$$

其中 $\mathbf{z}=(z_{0},\dots,z_{d})$，$z_{0}$ 标记大小，$z_{1},\dots,z_{d}$ 标记参数 $\chi$，且 $\mathbf{k}=(k_{0},\dots,k_{d})$ 是 $d+1$ 维的整数向量，特别地，$k_{0}=n$.

**定理 5.2.4** 无编号类的继承参数

设 $\mathcal{A}$ 是一个由 $\mathcal{B},\mathcal{C}$ 构造的组合类，其上的参数 $\chi$ 继承自 $\mathcal{B}$ 和 $\mathcal{C}$ 上的参数 $\xi,\zeta$，则无交并、直积、序列、多重集、幂集、循环构造是可容许的，且其对应的 MGF 如下：

$$
\begin{align}
\mathcal{A}=\mathcal{B}+\mathcal{C} &\implies A(\mathbf{z})=B(\mathbf{z})+C(\mathbf{z}) \\
\mathcal{A}=\mathcal{B}\times \mathcal{C} &\implies A(\mathbf{z})=B(\mathbf{z})C(\mathbf{z}) \\
\mathcal{A}=\mathrm{Seq}(\mathcal{B}) &\implies A(\mathbf{z})=\dfrac{1}{1-B(\mathbf{z})} \\
\mathcal{A}=\mathrm{MSet}(\mathcal{B}) &\implies A(\mathbf{z})=\exp\left( \sum_{\ell=1}^{\infty} \dfrac{1}{\ell} B(\mathbf{z}^{\ell}) \right) \\
\mathcal{A}=\mathrm{PSet}(\mathcal{B}) &\implies A(\mathbf{z})=\exp\left( \sum_{\ell=1}^{\infty} \dfrac{(-1)^{\ell-1}}{\ell} B(\mathbf{z}^{\ell}) \right) \\
\mathcal{A}=\mathrm{Cyc}(\mathcal{B}) &\implies A(\mathbf{z})=\sum_{\ell=1}^{\infty} \dfrac{\varphi(\ell)}{\ell} \ln \dfrac{1}{1-B(\mathbf{z}^{\ell})}
\end{align}
$$

其中对于序列、多重集、幂集、循环构造有 $\mathcal{B}_{0}=\varnothing$，且 $\varphi(n)$ 是 Euler $\varphi$ 函数。

**证明**

根据继承参数的定义，对于无交并有

$$
\begin{gather}
A(\mathbf{z})=\sum_{\alpha \in \mathcal{A}}\mathbf{z}^{\overline{\chi}(\alpha)} =\sum_{\beta \in \mathcal{B}} \mathbf{z}^{\overline{\xi}(\beta)}+\sum_{\gamma \in \mathcal{C}} \mathbf{z}^{\overline{\zeta}(\gamma)}=B(\mathbf{z})+C(\mathbf{z})
\end{gather}
$$

同样，对于直积我们有

$$
\begin{gather}
A(\mathbf{z})=\sum_{\alpha \in \mathcal{A}}\mathbf{z}^{\overline{\chi}(\alpha)}=\sum_{\beta \in \mathcal{B},\gamma \in \mathcal{C}} \mathbf{z}^{\overline{\xi}(\beta)} \mathbf{z}^{\overline{\zeta}(\gamma)}=B(\mathbf{z})C(\mathbf{z})
\end{gather}
$$

接下来的四种构造的可容许性证明与定理 1.2.8 的证明是一致的，只需将变量从 $z$ 改为 $\mathbf{z}$ 即可。

多重索引约定对于研究 MGF 的统一理论是非常有效的，但在实际应用中，我们通常只会遇到很少的参数，比如一个或两个，此时将 $\mathbf{z}$ 展开为 $(z,u)$ 或者 $(z,u,v)$ 来使用最为方便。下面我们给出几个基础的例子。

在第一章，我们证明了整数组合构成的类 $\mathcal{C}$ 具有规范

$$
\begin{gather}
\mathcal{C}=\mathrm{Seq}(\mathcal{I}), \quad \mathcal{I}=\mathrm{Seq}_{\geq 1}(\mathcal{Z})
\end{gather}
$$

其对应的 OGF 为

$$
\begin{gather}
C(z)=\dfrac{1}{1-I(z)}, \quad I(z)=\dfrac{z}{1-z}
\end{gather}
$$

于是 $C_{n}=2^{n-1}(n\geq 1)$. 现在假设我们要统计关于加数数量 $\chi$ 的组合的数量，利用定理 5.2.4，我们可以这样来构造：在 $\mathcal{I}$ 上定义参数 $\xi=1$，并使 $\chi$ 继承自 $\xi$，于是我们有

$$
\begin{gather}
I(z,u)=zu+z^{2}u+z^{3}u+\cdots=\dfrac{zu}{1-z}
\end{gather}
$$

从而

$$
\begin{gather}
C(z,u)=\dfrac{1}{1-I(z,u)}=\dfrac{1-z}{1-z(1+u)}
\end{gather}
$$

根据二项式系数的 BGF $\dfrac{1}{1-z(1+u)}$，我们就有

$$
\begin{gather}
C_{n}^{(k)}=[z^{n}u^{k}] C(z,u)=\binom{ n }{ k } -\binom{ n-1 }{ k } =\binom{ n-1 }{ k-1 } 
\end{gather}
$$

这与第一章中我们得到的公式一致。

上述过程中“定义参数”的一步看上去既不直观，也不利于快速地推导所需的 MGF，因此，下面我们给出另一种更为直观的方法。

我们称一个**标签** $\mu$ 是一个大小为 0 的元素，以直积的形式附着在一个规范中的子构造上。标签不改变元素的大小，因此组合类的一元生成函数不受影响。另一方面，一个元素包含的标签数量 $\chi$ 根据定义就是一个继承参数，因此定理 5.2.4 可以被应用于推导含标签的 MGF.

例如，在整数组合的例子中，如果我们要追踪一个组合中加数的数量，我们可以将一个标签 $\mu$ 附着在每个加数上，形成构造

$$
\begin{gather}
\mathcal{C}=\mathrm{Seq}(\mu\ \mathrm{Seq}_{\geq 1}(\mathcal{Z})) \implies C(z,u)=\dfrac{1}{1-u \frac{z}{1-z}}=\dfrac{1-z}{1-z(1+u)}
\end{gather}
$$

此外，我们还可以使用多个标签。例如，假设我们要追踪整数组合中加数 1 和 2 的数量，那么我们可以给出如下构造：

$$
\begin{gather}
\mathcal{C}=\mathrm{Seq}(\mu_{1}\mathcal{Z}+\mu_{2}\mathcal{Z}^{2}+\mathrm{Seq}_{\geq 3}(\mathcal{Z}))
\end{gather}
$$

从而

$$
\begin{gather}
C(z,u_{1},u_{2})=\dfrac{1}{1-(u_{1}z+u_{2}z^{2}+z^{3}(1-z)^{-1})}
\end{gather}
$$

其中变量 $u_{1},u_{2}$ 分别指示了加数 1 和 2 的数量。

类似地，要追踪加数的数量以及加数 1 的数量，我们有构造

$$
\begin{gather}
\mathcal{C}=\mathrm{Seq}(\mu \mu_{1}\mathcal{Z}+\mu\ \mathrm{Seq}_{\geq 2}(\mathcal{Z}))
\end{gather}
$$

以及 MGF

$$
\begin{gather}
C(z,u_{1},u)=\dfrac{1}{1-(uu_{1}z+uz^{2}(1-z)^{-1})}
\end{gather}
$$

其中 $u$ 指示了加数的数量，$u_{1}$ 则指示了加数 1 的数量。令 $u_{1}=1$，则我们就回到了前面的 MGF $C(z,u)$.

和之前一样，我们可以得到加数数量的累计生成函数

$$
\begin{gather}
\partial_{u} C(z,u) |_{u=1}=\dfrac{z(1-z)}{(1-2z)^{2}}
\end{gather}
$$

于是，对于 $n$ 的一个随机组合，其加数的数量具有期望

$$
\begin{gather}
\dfrac{1}{2^{n-1}} [z^{n}] \dfrac{z(1-z)}{(1-2z)^{2}}=\dfrac{n+1}{2}
\end{gather}
$$

进一步求导给出了标准差 $\dfrac{1}{2}\sqrt{ n-1 }$，比期望的阶数更低，因此这一概率分布在 $n\to \infty$ 时集中在期望周围。

类似地，我们也可以给出加数 $r$ 的数量的构造：

$$
\begin{gather}
\mathcal{C}=\mathrm{Seq}(\mu \mathcal{Z}^{r}+\mathrm{Seq}_{\neq r}(\mathcal{Z})) \implies C(z,u)=\left( 1-\left( \dfrac{z}{1-z}+(u-1)z^{r} \right) \right)^{-1}
\end{gather}
$$

其累计生成函数

$$
\begin{gather}
\partial_{u} C(z,u)|_{u=1}=\dfrac{z^{r}(1-z)^{2}}{(1-2z)^{2}}
\end{gather}
$$

部分分式分解给出

$$
\begin{gather}
\dfrac{z^{r}(1-z)^{2}}{(1-2z)^{2}}=\dfrac{2^{-r-2}}{(1-2z)^{2}}+\dfrac{2^{-r-1}-r 2^{-r-2}}{1-2z}+q(z)
\end{gather}
$$

其中 $q(z)$ 是一个多项式。取 $z^{n}$ 项的系数并除以 $2^{n-1}$ 就得到了加数 $r$ 数量的期望，再次求导就得到了标准差，我们可得以下结论：

**定理 5.2.5**

在 $n$ 的一个随机组合中加数的总数具有期望 $\dfrac{1}{2}(n+1)$ 以及标准差 $\dfrac{1}{2}\sqrt{ n-1 }$，加数 $r$ 的数量具有期望

$$
\begin{gather}
\dfrac{n}{2^{r+1}}+O(1)
\end{gather}
$$

以及标准差 $O(\sqrt{ n })$.

根据标准差的阶，我们可知该分布同样也是集中的：这就是说，对于一个足够大的 $n$，它的一个随机组合几乎必然含有 $\dfrac{n}{4}$ 个 $1$，$\dfrac{n}{8}$ 个 $2$，等等，构成如下的一种形式：

$$
\begin{gather}
1^{n/4}2^{n/8}3^{n/16}4^{n/32}\dots
\end{gather}
$$

关于随机结构的渐近行为，我们将在后续的章节进行系统的研究。

现在我们来对组合构造中部分的数量进行统一的研究。考虑组合构造 $\mathcal{A}=\mathscr{C}(u \mathcal{B})$，其中 $\mathscr{C}$ 是 $\mathrm{Seq},\mathrm{MSet},\mathrm{PSet},\mathrm{Cyc}$ 之一，$u$ 指示了部分的数量，则可容许性定理立即给出了 BGF $A(z,u)$，进而可得累计生成函数

$$
\begin{gather}
\Omega(z)=\partial_{u} A(z,u)|_{u=1}
\end{gather}
$$

对于四种构造的 $\Omega(z)$ 总结如下：

**定理 5.2.6**

构造 $\mathcal{A}=\mathscr{C}(u\mathcal{B})$ 的累计生成函数 $\Omega(z)$ 由以下公式给出：

$$
\begin{align}
\text{Seq:} \quad & \Omega(z)=A(z)^{2}B(z) \\
\text{MSet:} \quad & \Omega(z)=A(z)\sum_{k=1}^{\infty} B(z^{k}) \\
\text{PSet:} \quad & \Omega(z)=A(z)\sum_{k=1}^{\infty} (-1)^{k-1}B(z^{k}) \\
\text{Cyc:} \quad  & \Omega(z)=\sum_{k=1}^{\infty} \varphi(k) \dfrac{B(z^{k})}{1-B(z^{k})}
\end{align}
$$

其中 $\varphi(k)$ 是 Euler $\varphi$ 函数。

部分数量的期望则由以下公式给出：

$$
\begin{gather}
\mathbb{E}_{\mathcal{A}_{n}}(\chi)=\dfrac{[z^{n}]\Omega(z)}{[z^{n}]A(z)}
\end{gather}
$$

我们以整数拆分的例子结束这一节。令 $\mathcal{P}=\mathrm{MSet}(u\mathcal{I})$ 为整数拆分构成的类，其中 $u$ 指示了部分的数量，则其 BGF 和累计生成函数分别为

$$
\begin{gather}
P(z,u)=\prod_{n=1}^{\infty}  \dfrac{1}{1-uz^{n}}=\exp\left( \sum_{k=1}^{\infty} \dfrac{u^{k}}{k} \dfrac{z^{k}}{1-z^{k}} \right)
\end{gather}
$$

和

$$
\begin{gather}
\Omega(z)=P(z) \sum_{k=1}^{\infty} \dfrac{z^{k}}{1-z^{k}}=P(z) \sum_{n=1}^{\infty} d(n)z^{n}
\end{gather}
$$

其中 $d(n)$ 是 $n$ 的正因数的数量。于是 $n$ 的一个随机拆分中部分的数量具有期望

$$
\begin{gather}
\mathbb{E}_{n}(\chi)=\dfrac{1}{P_{n}} \sum_{j=1}^{n} d(j)P_{n-j}
\end{gather}
$$

对比组合与拆分可见，不同的组合构造可以具有相当不同的概率行为。

# Section 3: 编号类与指数 MGF

在上一节中发展的继承参数理论几乎可以逐字逐句地应用到编号类上。唯一的区别在于，其对应的 MGF 中指示大小的变量带有一个阶乘系数，这是为了将重编号考虑在内。和之前一样，一旦我们采用多重指标约定，那么在第三章中发展的符号计数方法可以直接应用到参数的统计中。

具体来说，对于编号类 $\mathcal{A}$ 与其上的参数 $\chi=(\chi_{1},\dots,\chi_{d})$，我们将其扩展为 $\overline{\chi}=(\chi_{0},\dots,\chi_{d})$，其中 $\chi_{0}(\alpha)=|\alpha|$ 是元素的大小，于是 $(\mathcal{A},\chi)$ 的指数 MGF 就可以表示为

$$
\begin{gather}
A(\mathbf{z})=\sum_{\mathbf{k}} A_{\mathbf{k}} \dfrac{\mathbf{z}^{\mathbf{k}}}{k_{0}!}=\sum_{\alpha \in \mathcal{A}} \dfrac{\mathbf{z}^{\overline{\chi}(\alpha)}}{|\alpha|!}
\end{gather}
$$

下面我们定义编号类中的继承参数。

**定义 5.3.1** 相容的（compatible）

编号类 $\mathcal{A}$ 上的一个参数 $\chi$ 是**相容的**，如果对任意 $\alpha \in \mathcal{A}$ 以及 $\alpha$ 的任意保序重编号 $\beta$ 有 $\chi(\alpha)=\chi(\beta)$.

我们定义编号类上的继承参数为相容且满足定义 5.2.3 的组合参数，于是我们即可得到以下定理，它是定理 5.2.4 的一个对应。

**定理 5.3.2** 编号类的继承参数

设 $\mathcal{A}$ 是一个由 $\mathcal{B},\mathcal{C}$ 构成的编号类，其上的参数 $\chi$ 继承自 $\mathcal{B},\mathcal{C}$ 上的参数 $\xi,\zeta$，则无交并、编号积、序列、集合、循环构造是可容许的，且其指数 MGF 如下：

$$
\begin{align}
\mathcal{A}=\mathcal{B}+\mathcal{C} &\implies A(\mathbf{z})=B(\mathbf{z})+C(\mathbf{z}) \\
\mathcal{A}=\mathcal{B}\otimes \mathcal{C} &\implies A(\mathbf{z})=B(\mathbf{z})C(\mathbf{z}) \\
\mathcal{A}=\mathrm{Seq}(\mathcal{B}) &\implies A(\mathbf{z})=\dfrac{1}{1-B(\mathbf{z})} \\
\mathcal{A}=\mathrm{Cyc}(\mathcal{B}) &\implies A(\mathbf{z})=\ln \dfrac{1}{1-B(\mathbf{z})} \\
\mathcal{A}=\mathrm{Set}(\mathcal{B}) &\implies A(\mathcal{z})=\exp B(\mathbf{z})
\end{align}
$$

**证明**

无交并的证明与定理 5.2.4 相同。对于编号积，我们有

$$
\begin{gather}
A(\mathbf{z})=\sum_{\alpha \in \mathcal{A}} \dfrac{\mathbf{z}^{\overline{\chi}(\alpha)}}{|\alpha|!}=\sum_{\beta \in \mathcal{B},\gamma \in \mathcal{C}} \binom{ |\beta|+|\gamma| }{ |\beta|,|\gamma| }  \dfrac{\mathbf{z}^{\overline{\xi}(\beta)+\overline{\zeta}(\gamma)}}{(|\beta|+|\gamma|)!}=B(\mathbf{z})C(\mathbf{z})
\end{gather}
$$

由此我们可以得出序列、循环、集合构造的 MGF.

与无编号类一样，通过 BGF，我们可以得到参数分布的各阶矩，我们首先通过一个例子来说明。

设 $\mathcal{P}$ 表示所有置换构成的类，$\chi$ 表示部分的数量（即循环的个数），则我们有构造

$$
\begin{gather}
\mathcal{P}=\mathrm{Set}(u\mathrm{Cyc}(\mathcal{Z})) \implies P(z,u)=\exp\left( u \ln \dfrac{1}{1-z} \right)=(1-z)^{-u}
\end{gather}
$$

这与我们在第一节中得到的公式一致。我们已经知道循环个数的均值为调和数 $H_{n}$，并且分布是集中的，因为标准差的阶比均值的阶更低。

同样，对于置换中长度为 $r$ 的循环的个数 $\xi$，其 BGF 为

$$
\begin{gather}
\mathcal{P}=\mathrm{Set}(u\mathrm{Cyc}_{r}(\mathcal{Z})+\mathrm{Cyc}_{\neq r}(\mathcal{Z}))\implies P(z,u)=\dfrac{\exp((u-1)z^{r} / r)}{1-z}
\end{gather}
$$

求导得到其累计生成函数

$$
\begin{gather}
\Omega(z)=\dfrac{z^{r}}{r} \dfrac{1}{1-z}
\end{gather}
$$

因此，在一个大小为 $n(n\geq r)$ 的随机置换中，长度为 $r$ 的循环数量的均值为 $1 / r$.

现在我们给出一般的部分数量分布公式，它是无编号类中定理 5.2.6 的对应。

**定理 5.3.3**

编号类构造 $\mathcal{A}=\mathscr{C}(u\mathcal{B})$ 的累计生成函数 $\Omega(z)$ 由以下公式给出：

$$
\begin{align}
\text{Seq:} \quad & \Omega(z)=A(z)^{2} B(z) \\
\text{Set:} \quad & \Omega(z)=A(z)B(z) \\
\text{Cyc:} \quad & \Omega(z)=\dfrac{B(z)}{1-B(z)}
\end{align}
$$

我们以一个例子结束本节。设 $\mathcal{S}$ 为所有集合划分构成的类，其构造为

$$
\begin{gather}
\mathcal{S}=\mathrm{Set}(u \mathrm{Set}_{\geq 1}(\mathcal{Z}))\implies S(z,u)=\exp(u(e^{z}-1))
\end{gather}
$$

求导即得

$$
\begin{gather}
\Omega(z)=(e^{z}-1) e^{e^{z}-1}=\dfrac{\mathrm{d} }{\mathrm{d} z}S(z)-S(z)
\end{gather}
$$

这给出分块数量的均值

$$
\begin{gather}
\dfrac{\Omega_{n}}{S_{n}}=\dfrac{S_{n+1}}{S_{n}}-1
\end{gather}
$$

同理，我们也可以写出大小为 $r$ 的分块数量的构造

$$
\begin{gather}
\mathcal{S}=\mathrm{Set}(u\mathrm{Set}_{r}(\mathcal{Z})+\mathrm{Set}_{\neq r}(\mathcal{Z})) \implies S(z,u)=\exp\left( e^{z}-1+(u-1) \dfrac{z^{k}}{k!} \right)
\end{gather}
$$

从中可以提取出均值与标准差，就如之前一样。