概率论，作为研究随机现象与不确定性的一门学科，其核心当然就是对“概率”的研究。与古典概率论不同，现代概率论，或者说公理化概率论是以测度为基础的。测度论为描述随机现象提供了严格的集合论框架，其中一个事件被编码为一个集合 $A$，而概率 $\mathbb{P}(A)$ 就描述了一个事件发生的可能性，也就是一个定义在子集上的特殊实值函数：一个测度。

在概率论的前几章内，概率学完全可以视为一种特殊的测度论，这就是说，实分析中的结果可以得到直接的应用。然而，让概率论真正成为一门学科（而非测度论的一个分支）的，正是它独有的方法和结论：大数定律、中心极限定理、独立性等等，这也是概率学在现实生活中被广泛应用的部分。

本章，我们首先回顾一下测度论中的结论，然后我们将给出概率的标准定义。

# Section 1: 分布函数

我们从**分布函数**的讨论开始概率论的研究，这是引入概率测度的一种传统方法。给定有界递增函数 $f\colon \mathbb{R}\to \mathbb{R}$，如果 $f$ 不是常值函数，我们可以考虑其“归一化”的函数

$$
F(x)= \dfrac{f(x+)-f(-\infty)}{f(+\infty)-f(-\infty)}
$$

那么 $F$ 是递增且右连续的，并且 $F(-\infty)=0,F(+\infty)=1$. 根据实分析中的结论，$F$ 是一个归一化的有界变差函数（$NBV$），从而存在唯一的有限测度 $\mu_{F}$ 使得 $F(x)=\mu_{F}((-\infty,x])$，我们之后将看到，$\mu_{F}$ 正是一个概率测度。

**定义 1.1.1** 分布函数（distribution function）

函数 $F\colon \mathbb{R}\to \mathbb{R}$ 是一个**分布函数**，如果 $F$ 是递增且右连续的，并且满足 $F(-\infty)=0,F(+\infty)=1$.

有一类特殊的分布函数需要我们注意，这就是**点质量函数**

$$
\delta_{t}(x)=\begin{cases}
1 &, x\geq t \\
0 &, x<t
\end{cases}
$$

它对应的测度是点质量测度：$\delta_{t}(A)=1$ 如果 $t \in A$，反之则等于 $0$. 利用它，我们可以给出分布函数的一个分解。

实分析中的结论指出，每个有限测度 $\mu$ 都可以唯一地分解为离散部分和连续部分：

$$
\mu=\mu_{d}+\mu_{c}
$$

对于分布函数 $F$ 对应的测度 $\mu_{F}$ 来说，它的离散部分就是 $F$ 的跳跃间断点 $D_{F}=\{ x \mid F(x)>F(x-) \}$ 所对应的点质量测度之和：

$$
(\mu_{F})_{d}=\sum_{t \in D_{F}} (F(t)-F(t-))\delta_{t}
$$

对应于函数，我们就得到了 $F$ 的“离散部分”：

$$
F_{d}(x)=\sum_{t \in D_{F}} (F(t)-F(t-))\delta_{t}(x)
$$

从 $F$ 中减去 $F_{d}$，我们自然会期望得到的函数是连续的，现在我们就来证明这一点。

**定理 1.1.2**

设 $F$ 是一个分布函数，令

$$
F_{c}(x)=F(x)-F_{d}(x)=F(x)-\sum_{t \in D_{F}}(F(t)-F(t-))\delta_{t}(x)
$$

则 $F_{c}\geq 0$，递增，且处处连续。

**证明**

设 $x<y$，我们有

$$
F_{d}(y)-F_{d}(x)=\sum_{x<t\leq y,t \in D_{F}}(F(t)-F(t-))\leq F(y)-F(x)
$$

因此 $F_{c}$ 递增，令 $x\to -\infty$ 得 $F_{c}\geq 0$. 由于 $\sum_{t \in D_{F}}(F(t)-F(t-))\leq 1$，故级数 $\sum_{t \in D_{F}}(F(t)-F(t-))\delta_{t}$ 一致收敛于 $F_{d}$，从而 $F_{d}$ 右连续，因此 $F_{c}$ 也是右连续的。最后，我们有

$$
F(x)-F(x-)=F_{d}(x)-F_{d}(x-)=\begin{cases}
F(x)-F(x-) &, x \in D_{F} \\
0 &, x \not\in D_{F}
\end{cases}
$$

从而我们有 $F_{c}(x)-F_{c}(x-)=0$，即 $F_{c}$ 在 $\mathbb{R}$ 上连续。

由于测度的分解式 $\mu=\mu_{d}+\mu_{c}$ 是唯一的，因此函数分解 $F=F_{d}+F_{c}$ 是唯一的。事实上，我们还可以得到一个稍微强一点的结论。

**定义 1.1.3** 离散的（discrete）

设 $F$ 是一个分布函数，称 $F$ 是**离散的**，如果存在至多可数集 $\{ x_{j} \}\subset \mathbb{R}$ 和 $c_{j}>0$ 使得 $\sum_{j}c_{j}=1$ 且 $F=\sum_{j}c_{j}\delta_{x_{j}}$.

假设 $F_{d}\neq 0,F_{c}\neq 0$，则 $\alpha=F_{d}(+\infty)$ 满足 $0<\alpha<1$，我们令

$$
F_{1}= \dfrac{1}{\alpha} F_{d},F_{2}= \dfrac{1}{1-\alpha}F_{c}
$$

则 $F_{1}$ 是离散的，$F_{2}$ 是连续的，并且 $F=\alpha F_{1}+(1-\alpha)F_{2}$，我们称 $F$ 是 $F_{1}$ 和 $F_{2}$ 的一个**凸组合**。如果 $F_{c}=0$，那么我们设 $\alpha=1$ 且 $F=F_{1}$，反之，如果 $F_{d}=0$，那么我们设 $\alpha=0$ 且 $F=F_{2}$，因此我们有：

**定理 1.1.4**

每个分布函数都可以唯一地写成一个离散分布函数和一个连续分布函数的凸组合。

下面，我们考虑分布函数 $F$ 的另一种分解：奇异部分和绝对连续部分。如果 $F$ 是绝对连续的，根据实分析中的结论，存在 $f \in L^{1}(m)$ 使得

$$
F(x)=\int_{-\infty}^{x} f(t)\mathrm{d} t
$$

且 $f=F'$ a.e.，并且根据 $F$ 的性质我们有 $f\geq 0$ a.e. 且 $\int_{-\infty}^{\infty}f(t)\mathrm{d}t=1$. 反之，如果 $f \in L^{1}(m)$ 满足这两个条件，那么定义为 $F(x)=\int_{-\infty}^{x}f(t)\mathrm{d}t$ 的函数 $F$ 就是一个绝对连续的分布函数。

另一边，我们知道 $\mu_{F}\perp m$ 当且仅当 $F'=0$ a.e.，因此我们有如下定义：

**定义 1.1.5** 奇异的（singular）

设 $F$ 是一个分布函数，称 $F$ 是**奇异的**，如果 $F\neq 0$ 且 $F'=0$ a.e.

下面的定理是 Lebesgue 分解 $\mathrm{d}\mu_{F}=\mathrm{d}\mu_{s}+F'\mathrm{d}m$ 的简单推论。

**定理 1.1.6**

设 $F$ 是一个分布函数，则有：

1. $F'\geq 0$ a.e.
2. $F' \in L^{1}(m)$ 且对任意 $x<y$ 有 $\int_{x}^{y}F'(t)\mathrm{d}t\leq F(y)-F(x)$
3. 设 $F_{ac}=\int_{-\infty}^{x}F'(t)\mathrm{d}t,F_{s}=F-F_{ac}$，则 $F_{ac}'=F'$ a.e.，$F_{s}'=0$ a.e.，从而 $F_{s}$ 是奇异的当且仅当 $F_{s}\neq 0$

上面的 $F_{ac}$ 和 $F_{s}$ 自然被称为 $F$ 的**绝对连续部分**和**奇异部分**，结合定理 1.1.4，我们就有：

**定理 1.1.7**

每个分布函数都可以唯一地写成一个离散分布函数、一个绝对连续分布函数和一个奇异连续分布函数的凸组合。

最后，我们再介绍一个术语。

**定义 1.1.8** 密度（density）

设 $F$ 是一个分布函数，称非负函数 $f\colon \mathbb{R}\to \mathbb{R}$ 是 $F$ 的一个**密度**，如果 $f=F'$ a.e.

换句话说，$f$ 是 $F$ 的密度当且仅当 $F(x)=\int_{-\infty}^{x}f(t)\mathrm{d}t$.

# Section 2: 概率空间

在概率论中，我们使用的术语有时候会与测度论中不同：例如，在概率论中我们通常将代数称为**域**，$\sigma$-代数称为 $\sigma$**-域**或者 **Borel 域**。其它还有一些术语的变化我们会在合适的时候介绍。

**定义 1.2.1** 概率空间（probability space）

**概率空间** $(\Omega,\mathcal{F},\mathbb{P})$ 包含集合 $\Omega$，称为**样本空间**，其元素称为**样本点**，和 Borel 域 $\mathcal{F}$，称为**事件域**，以及**概率测度** $\mathbb{P}\colon \mathcal{F}\to[0,1]$ 满足：

1. 设 $(E_{n})_{n=0}^{\infty}$ 是 $\mathcal{F}$ 中不相交的集合，则 $\mathbb{P}\left( \bigcup_{n=0}^{\infty}E_{n} \right)=\sum_{n=0}^{\infty}\mathbb{P}(E_{n})$
2. $\mathbb{P}(\Omega)=1$

根据定义我们知道，$\mathbb{P}$ 就是 $\mathcal{F}$ 上的一个有限测度，因此所有关于有限测度的结论对概率测度都适用。

设 $E \in \mathcal{F}$ 且 $\mathbb{P}(E)>0$，取 $\mathcal{F}_{E}=\{ E\cap F \mid F \in \mathcal{F} \}$，并且对 $E\cap F \in \mathcal{F}_{E}$ 定义 $\mathbb{P}_{E}(E\cap F)= \dfrac{\mathbb{P}(E\cap F)}{\mathbb{P}(E)}$，则我们可以验证 $(E,\mathcal{F}_{E},\mathbb{P}_{E})$ 是一个概率空间，称为 $(\Omega,\mathcal{F},\mathbb{P})$ 在 $E$ 上的**迹**。另外，$\mathbb{P}_{E}$ 通常称为在 $E$ 下的**条件概率**，记作 $\mathbb{P}(F \mid E)=\mathbb{P}_{E}(E\cap F)$.

在所有概率空间中，实数上的概率测度是最重要的一类，因为它们将概率与分布函数联系在一起。事实上，我们有以下定理：

**定理 1.2.2**

每个 $(\mathbb{R},\mathcal{B}_{\mathbb{R}})$ 上的概率测度 $\mu$ 都唯一确定了一个分布函数 $F$ 使得 $F(x)=\mu((-\infty,x])$，反之，每个分布函数 $F$ 都唯一确定了 $(\mathbb{R},\mathcal{B}_{\mathbb{R}})$ 上的概率测度 $\mu$ 使得 $\mu((a,b])=F(b)-F(a)$.

上面的定理是 Lebesgue-Stieltjes 测度理论的一个标准结果。根据这个定理，我们就把 $F$ 称为 $\mu$ 的分布函数，$\mu$ 称为 $F$ 的概率测度。

有时候，我们需要考虑实数的子集上的概率测度。不失一般性地，我们可以假设 $\Omega=[0,1]$，此时我们可以定义分布函数 $F$ 使得当 $x<0$ 时有 $F(x)=0$，并且 $x>1$ 时有 $F(x)=1$，于是利用 1.2.2 我们可以得到一个概率测度 $\mu$，满足 $\mu((-\infty,0))=\mu((1,+\infty))=0$，于是 $(\Omega,\mathcal{B}_{[0,1]},\mu)$ 就是一个概率空间，并且它是 $(\mathbb{R},\mathcal{B}_{\mathbb{R}},\mu)$ 在 $[0,1]$ 上的迹。

这其中最常用的一个分布函数就是 $[0,1]$ 上的均匀分布

$$
F(x)=\begin{cases}
0 &, x<0 \\
x &, 0\leq x\leq 1 \\
1 &, x>1
\end{cases}
$$

它所对应的概率测度就是 $[0,1]$ 上通常的 Borel 测度，其完备化就是 $[0,1]$ 上的 Lebesgue 测度。

对于概率为零的集合 $N \in \mathcal{F},\mathbb{P}(N)=0$，在概率论中我们也有一个相关的术语。如果一个性质在 $\Omega \setminus N$ 上成立，其中 $\mathbb{P}(N)=0$，那么我们就称该性质**几乎必然成立**，简记为 a.s.（almost surely），它与测度论中的几乎处处（a.e.）是一致的。

另一类常用的概率空间是所谓的**离散概率空间**。设 $\Omega$ 是一个至多可数集，不妨设为 $\Omega=\{ \omega_{n} \mid n \in \mathbb{N} \}$，事件域取为 $\mathcal{F}=\mathscr{P}(\Omega)$，实数 $(p_{n})_{n=0}^{\infty}$ 满足 $p_{n}\geq 0$ 且 $\sum_{n=0}^{\infty}p_{n}=1$，定义 $\mathbb{P}\colon \mathscr{P}(\Omega)\to[0,1]$ 为

$$
\mathbb{P}(E)=\sum_{\omega_{j} \in E} p_{j}
$$

也就是说，我们为每个单元集 $\{ \omega_{j} \}$ 赋予一个概率 $\mathbb{P}(\{ \omega_{j} \})=p_{j}$，我们很容易可以看出 $(\Omega,\mathscr{P}(\Omega),\mathbb{P})$ 是一个概率空间。事实上，任何 $(\Omega,\mathscr{P}(\Omega))$ 上的概率测度都具有上述形式（根据 $\mathbb{P}$ 的可数可加性）。在现实生活中，我们遇到的大多数情景都可以建模为一个离散概率空间。

# Section 3: 随机变量与期望

前面我们讨论了实数上的概率测度与其分布函数，然而，在一般的概率空间上并没有这样的对应关系。为了使用实分析中的工具，我们就需要从一般的概率空间转换到实数上，这就是我们引入**随机变量**的动机。

**定义 1.3.1** 随机变量（random variable）

设 $(\Omega,\mathcal{F},\mathbb{P})$ 是概率空间，$E \in \mathcal{F}$，一个 $E$ 上的广义实值**随机变量**是一个 $\mathcal{F}_{E}$-可测的函数 $X\colon E\to \mathbb{R}^{*}$；一个 $E$ 上的复值随机变量是一个函数 $X\colon E\to \mathbb{C}$ 使得 $\mathrm{Re}\ X$ 和 $\mathrm{Im}\ X$ 都是 $E$ 上的实值随机变量。

大多数时候，我们使用的都是 $\Omega$ 上 a.e. 有限的广义实值随机变量，或者就是单纯的实值随机变量，之后我们提到随机变量时，如果没有特殊指定，那么我们就是指这一类随机变量。

随机变量的一大用处就是将一个概率空间转换为实数上的概率空间，我们有以下定理：

**定理 1.3.2**

每个 $(\Omega,\mathcal{F},\mathbb{P})$ 上的随机变量 $X$ 都诱导了一个概率空间 $(\mathbb{R},\mathcal{B}_{\mathbb{R}},\mu)$，满足对任意 $B \in \mathcal{B}_{\mathbb{R}}$ 有

$$
\mu(B)=\mathbb{P}(X^{-1}[B])=\mathbb{P}(X \in B)
$$

**证明**

显然有 $\mu(B)\geq 0$，设 $(B_{j})_{j=1}^{\infty}$ 是不相交的 Borel 集，则有

$$
\mu\left( \bigcup_{j=1}^{\infty} B_{j} \right)=\mathbb{P}\left( \bigcup_{j=1}^{\infty} X^{-1}[B_{j}] \right)=\sum_{j=1}^{\infty} \mathbb{P}(X^{-1}[B_{j}])=\sum_{j=1}^{\infty} \mu(B_{j})
$$

因此 $\mu$ 是可数可加的。最后，我们有 $\mu(\mathbb{R})=\mathbb{P}(\Omega)=1$，从而 $\mu$ 是一个概率测度，这就完成了证明。

我们把 $X$ 诱导的概率测度 $\mu=\mathbb{P}\circ X^{-1}$ 称为 $X$ 的**概率分布测度**，与 $\mu$ 对应的分布函数 $F$ 称为 $X$ 的**概率分布函数**，其满足

$$
F(x)=\mu((-\infty,x])=\mathbb{P}(X\leq x)
$$

尽管 $X$ 唯一确定了一个概率分布，反之却不成立。两个具有相同概率分布的随机变量被称为是**同分布的**。

由于随机变量本质上就是一个可测函数，因此关于可测函数的结论对随机变量都适用，下面我们列举一些结论。

**定理 1.3.3**

设 $(\Omega,\mathcal{F},\mathbb{P})$ 是概率空间，$X$ 是一个随机变量，如果 $f\colon \mathbb{R}\to \mathbb{R}$ 是 Borel 可测的，那么 $f(X)=f\circ X$ 也是一个随机变量。

有时候，我们需要使用多个随机变量，从而组成了所谓的**随机向量**，也就是随机变量的直和：$(X_{1},\dots,X_{n})=X_{1}\oplus\dots \oplus X_{n}$. 根据测度理论，如果 $X_{1},\dots,X_{n}$ 都是随机变量，那么 $(X_{1},\dots,X_{n})$ 也是一个随机变量，并且它诱导了 $\mathbb{R}^{n}$ 上的一个概率测度。此外，我们还有：

**定理 1.3.4**

设 $(\Omega,\mathcal{F},\mathbb{P})$ 是概率空间，$X_{1},\dots,X_{n}$ 是随机变量，如果 $f\colon \mathbb{R}^{n}\to \mathbb{R}$ 是 Borel 可测的，那么 $f(X_{1},\dots,X_{n})$ 也是一个随机变量。

上述定理只是定理 1.3.3 的简单应用，只需明确映射复合的顺序

$$
\Omega \overset{X_{j}}{\longrightarrow} \mathbb{R} \overset{\oplus }{\longrightarrow} \mathbb{R}^{n} \overset{f}{\longrightarrow} \mathbb{R}
$$

然后利用可测的定义即可。

由此，我们知道了如果 $X,Y$ 是随机变量，那么 $\max(X,Y)$，$\min(X,Y)$，$X+Y$，$XY$ 和 $X / Y$ 都是随机变量，并且我们还有以下结果：

**定理 1.3.5**

设 $(\Omega,\mathcal{F},\mathbb{P})$ 是概率空间，$(X_{j})_{j=1}^{\infty}$ 都是广义实值随机变量，那么

$$
\sup_{j\geq 1} X_{j} , \inf_{j\geq 1} X_{j}, \limsup_{ j \to \infty } X_{j}, \liminf_{ j \to \infty } X_{j}
$$

都是广义实值随机变量。此外，$\lim_{ j \to \infty }X_{j}$ 在其收敛或者发散至 $\pm \infty$ 的点构成的集合上是一个广义实值随机变量。

这是实分析中的一个标准结果，我们只是用概率论的语言重新叙述一遍而已。

另一个常用结果是可测函数可以由简单函数逼近，我们给出以下定义：

**定义 1.3.6** 离散的（discrete）

设 $(\Omega,\mathcal{F},\mathbb{P})$ 是概率空间，一个随机变量 $X$ 是**离散的**，如果存在至多可数集 $B\subset \mathbb{R}$ 使得 $\mathbb{P}(X \in B)=1$.

换句话说，随机变量 $X$ 是离散的当且仅当 $X$ 的值域是至多可数的，因此 $X$ 是离散的当且仅当其分布函数是离散的。

称 $(\Lambda_{j})_{j=1}^{\infty}$ 是 $\Omega$ 的一个**可数分割**，如果 $\Lambda_{j}\in \mathcal{F}$ 不相交且 $\Omega=\bigcup_{j=1}^{\infty}\Lambda_{j}$，设 $c_{j}\in \mathbb{R}$，则定义为

$$
\phi=\sum_{j=1}^{\infty} c_{j} 1_{\Lambda_{j}}
$$

的随机变量 $\phi$ 是离散的，其中**指示函数** $1_{\Lambda_{j}}$ 与特征函数 $\chi_{\Lambda_{j}}$ 是相同的。我们称 $\phi$ 是对应于**加权划分** $\{ (\Lambda_{j},c_{j}) \}$ 的随机变量，反之，每个离散随机变量都对应了一个加权划分，只需取 $\Lambda_{j}=X^{-1}[\{ c_{j} \}]$ 即可。如果一个加权划分是有限的，则称其对应的随机变量是**简单的**。

下面我们给出**数学期望**的定义，从测度论的角度来看，随机变量 $X$ 的期望不过就是 $X$ 关于概率测度 $\mathbb{P}$ 的积分，即：

**定义 1.3.7** 期望（expectation）

设 $(\Omega,\mathcal{F},\mathbb{P})$ 是概率空间，$X$ 是一个（广义实值或复值）随机变量，定义其**期望**为

$$
\mathbb{E}(X)=\int X \mathrm{d} \mathbb{P}
$$

根据积分的定义，对于非负离散随机变量，我们有

$$
\mathbb{E}(\phi)=\sum_{j=1}^{\infty} c_{j} \mathbb{P}(\Lambda_{j})
$$

对于非负随机变量，我们可以用简单随机变量从下方逼近它，然后取上确界即可。下面，对于任意的广义实值随机变量 $X$，我们可以把它写成两个非负随机变量的差：$X=X^{+}-X^{-}$，如果 $\mathbb{E}(X^{+})$ 和 $\mathbb{E}(X^{-})$ 至少有一个是有限的，那么就有 $\mathbb{E}(X)=\mathbb{E}(X^{+})-\mathbb{E}(X^{-})$，如果不然，则称 $\mathbb{E}(X)$ 不存在。最后，一个复值随机变量的期望就是对其实部和虚部分别取期望。

当概率空间是 $(\mathbb{R},\mathcal{B}_{\mathbb{R}},\mu)$ 时，其上的随机变量 $f$ 的期望就退化为了通常的 Lebesgue-Stieltjes 积分：

$$
\mathbb{E}(f)= \int f \mathrm{d} \mu
$$

下面的定理将关于 $\mathbb{P}$ 的抽象积分转换为了 $\mathbb{R}$ 上的 Lebesgue-Stieltjes 积分：

**定理 1.3.8**

设 $(\Omega,\mathcal{F},\mathbb{P})$ 上的随机变量 $X$ 诱导了概率空间 $(\mathbb{R},\mathcal{B}_{\mathbb{R}},\mu)$，Borel 可测函数 $f\colon \mathbb{R}\to \mathbb{R}$ 满足 $f\geq 0$ 或者 $f \in L^{1}(\mu)$，则有

$$
\int_{\Omega} f(X) \mathrm{d} \mathbb{P}=\int_{\mathbb{R}} f \mathrm{d} \mu
$$

**证明**

设 $B \in \mathcal{B}_{\mathbb{R}}$，$f=1_{B}$，则上述等式就退化为

$$
\mathbb{P}(X \in B)=\mu(B)
$$

这正是 $\mu$ 的定义。从而根据实分析中的常规论证可知上述等式对 $f\geq 0$ 或者 $f \in L^{1}(\mu)$ 成立。

上述定理也可以推广至任意有限个随机变量，我们以二维为例：

**定理 1.3.9**

设 $(\Omega,\mathcal{F},\mathbb{P})$ 上的随机变量 $(X,Y)$ 诱导了概率空间 $(\mathbb{R}^{2},\mathcal{B}_{\mathbb{R}^{2}},\mu)$，Borel 可测函数 $f\colon \mathbb{R}\to \mathbb{R}$ 满足 $f\geq 0$ 或者 $f \in L^{1}(\mu)$，则有

$$
\int_{\Omega} f(X,Y) \mathrm{d} \mathbb{P}=\int_{\mathbb{R}^{2}} f \mathrm{d} \mu
$$

下面，我们给出一些概率论中常用的不等式。

**定理 1.3.10**

设 $(\Omega,\mathcal{F},\mathbb{P})$ 是概率空间，$X$ 是一个随机变量，则有

$$
\sum_{n=1}^{\infty} \mathbb{P}(|X|\geq n)\leq \mathbb{E}(|X|)\leq 1+ \sum_{n=1}^{\infty} \mathbb{P}(|X|\geq n)
$$

**证明**

设 $\Lambda_{n}=\{ n\leq|X|<n+1 \}$，则

$$
\sum_{n=1}^{\infty} n\mathbb{P}(\Lambda_{n}) \leq\sum_{n=0}^{\infty} \int_{\Lambda_{n}}|X|\mathrm{d} \mathbb{P}\leq \sum_{n=0}^{\infty}(n+1)\mathbb{P}(\Lambda_{n}) =1+\sum_{n=1}^{\infty} n\mathbb{P}(\Lambda_{n})
$$

下面我们只需证明 $\displaystyle \sum_{n=1}^{\infty}n\mathbb{P}(\Lambda_{n})=\sum_{n=1}^{\infty}\mathbb{P}(|X|\geq n)$ 即可。对于 $N\geq 1$，我们有

$$
\begin{align}
\sum_{n=1}^{N} n\mathbb{P}(\Lambda_{n}) &= \sum_{n=1}^{N} n(\mathbb{P}(|X|\geq n)-\mathbb{P}(|X|\geq n+1)) \\
&= \sum_{n=1}^{N} \mathbb{P}(|X|\geq n) - N \mathbb{P}(|X|\geq N+1)
\end{align}
$$

因此

$$
\sum_{n=1}^{N} n\mathbb{P}(\Lambda_{n})\leq \sum_{n=1}^{N} \mathbb{P}(|X|\geq n)\leq \sum_{n=1}^{N} n\mathbb{P}(\Lambda_{n})+\int_{\{ |X|\geq N+1 \}}|X|\mathrm{d} \mathbb{P}
$$

如果 $\mathbb{E}(|X|)<+\infty$，则令 $N\to \infty$ 可得最后一项积分收敛于 $0$，从而等式成立。另一边，如果 $\mathbb{E}(|X|)=+\infty$，那么两个求和都发散至 $+\infty$，同样有等式成立，这就完成了证明。

上述定理表明，$\mathbb{E}(|X|)<+\infty$ 当且仅当 $\sum_{n=1}^{\infty}\mathbb{P}(|X|\geq n)$ 收敛，此外，如果 $X$ 的值域包含于正整数内，那么有

$$
\mathbb{E}(X)=\sum_{n=1}^{\infty} n \mathbb{P}(X=n)=\sum_{n=1}^{\infty} \mathbb{P}(X\geq n)
$$

另一个简单但是常用的不等式如下：

**定理 1.3.11** Chebyshev 不等式

设 $(\Omega,\mathcal{F},\mathbb{P})$ 是概率空间，函数 $\varphi\colon \mathbb{R}\to(0,+\infty)$ 满足 $\varphi$ 在 $(0,+\infty)$ 上递增，并且 $\varphi(u)=\varphi(-u)$，$X$ 是一个随机变量使得 $\mathbb{E}(\varphi(X))<+\infty$，则对任意 $u>0$ 有

$$
\mathbb{P}(|X|\geq u)\leq \dfrac{\mathbb{E}(\varphi(X))}{\varphi(u)}
$$

**证明**

根据条件我们知道 $\varphi$ 是 Borel 可测的，因此我们有

$$
\mathbb{E}(\varphi(X))=\int_{\Omega}\varphi(X)\mathrm{d} \mathbb{P}\geq \int_{\{ |X|\geq u \}} \varphi(X)\mathrm{d} \mathbb{P}\geq \varphi(u)\mathbb{P}(|X|\geq u)
$$

即证。

最后，我们再给出一个重要定义。

**定义 1.3.12** 矩（moment）

设 $(\Omega,\mathcal{F},\mathbb{P})$ 是概率空间，$X$ 是一个随机变量，$a \in \mathbb{R},r\geq 0$，称 $\mathbb{E}(|X-a|^{r})$ 为关于 $a$ 的 $r$ 阶**绝对矩**；如果 $r\geq 0$ 是整数，称 $\mathbb{E}((X-a)^{r})$ 为关于 $a$ 的 $r$ 阶**矩**。

当 $r=1,a=0$ 时，$\mathbb{E}((X-a)^{r})$ 就退化为期望 $\mathbb{E}(X)$，也称为 $X$ 的**均值**，关于均值的矩称为**中心矩**。二阶的中心矩 $\mathbb{E}((X-\mathbb{E}(X))^{2})$ 称为 $X$ 的**方差**，记作 $\mathrm{var}(X)$，其平方根称为**标准差**，记作 $\sigma(X)$，并且我们有

$$
\mathrm{var}(X)=\sigma^{2}(X)=\mathbb{E}((X-\mathbb{E}(x))^{2})=\mathbb{E}(X^{2})-\mathbb{E}(X)^{2}
$$

因此有 $\sigma^{2}(X)\leq \mathbb{E}(X^{2})$，这个不等式之后将会用到。设实数 $p>0$，所有满足 $\mathbb{E}(|X|^{p})<+\infty$ 的复值随机变量构成的集合记作 $L^{p}(\Omega,\mathbb{P})$.

下面我们给出著名的 Holder 和 Minkowski 不等式。

**定理 1.3.13** Holder 不等式

设 $(\Omega,\mathcal{F},\mathbb{P})$ 是概率空间，$X,Y$ 是随机变量，实数 $p>1$，$\dfrac{1}{p}+\dfrac{1}{q}=1$，则有

$$
\mathbb{E}(|XY|)\leq \mathbb{E}(|X|^{p})^{1 / p}\mathbb{E}(|Y|^{q})^{1/q}
$$

**定理 1.3.14** Minkowski 不等式

设 $(\Omega,\mathcal{F},\mathbb{P})$ 是概率空间，$X,Y$ 是随机变量，实数 $p>1$，则有

$$
\mathbb{E}(|X+Y|^{p})^{1 / p}\leq \mathbb{E}(|X|^{p})^{1/p}+\mathbb{E}(|Y|^{p})^{1/p}
$$

在 Holder 不等式中令 $p=q=2$，我们就得到了 Cauchy-Schwarz 不等式。此外，在 Holder 不等式中令 $Y=1$，则有

$$
\mathbb{E}(|X|)\leq \mathbb{E}(|X|^{p})^{1/p}
$$

设 $0<r<p$，将 $|X|$ 替换为 $|X|^{r}$，再令 $s=pr>r$，则有

$$
\mathbb{E}(|X|^{r})^{1/r}\leq \mathbb{E}(|X|^{s})^{1/s},0<r<s
$$

这一不等式称为 Liapounov 不等式，它是下一个不等式的特殊情形：

**定理 1.3.15** Jensen 不等式

设 $(\Omega,\mathcal{F},\mathbb{P})$ 是概率空间，$\varphi\colon \mathbb{R}\to \mathbb{R}$ 是一个凸函数，$X$ 是一个随机变量使得 $X$ 和 $\varphi(X)$ 都是可积的，则有

$$
\varphi(\mathbb{E}(X))\leq \mathbb{E}(\varphi(X))
$$

所谓凸函数就是指对任意实数 $a<b$ 和 $0\leq\lambda\leq 1$ 有

$$
\varphi((1-\lambda)a+\lambda b)\leq(1-\lambda)\varphi(a)+\lambda\varphi(b)
$$

Jensen 不等式就可以看作是上述不等式的连续版本，它的一个更广义的版本的证明我们放在附录中。