在讨论完 Lebesgue 积分后，我们就要考虑这种新的积分如何与导数进行交互，即所谓的微积分基本定理。为了研究这个问题，我们首先就要了解在同一个 $\sigma$-代数下，测度 $\nu$ 关于 $\mu$ 的导数是什么，在这之后，我们将把 $\mu$ 取为 Lebesgue 测度 $m$ 并得到一个更精细的结果。事实证明，在这一部分的研究中，将测度的概念扩宽使得它能够取到负数甚至复数是有用的，在这种框架下，微分理论的研究可以更自然地进行。

# Section 1: 符号测度

**定义 23.1.1** 符号测度（signed measure）

设 $(X,\mathcal{M})$ 是一个可测空间，函数 $\nu\colon \mathcal{M}\to[-\infty,+\infty]$ 是一个**符号测度**，如果：

1. $\nu(\varnothing)=0$
2. $\nu$ 至多取到 $\{ -\infty,+\infty \}$ 中的一个。
3. 设 $(E_{n})_{n=0}^{\infty}$ 是 $\mathcal{M}$ 不相交的集合，那么 $\nu\left( \bigcup_{n=0}^{\infty}E_{n} \right)=\sum_{n=0}^{\infty}\nu(E_{n})$，并且当 $\nu\left( \bigcup_{n=0}^{\infty}E_{n} \right)$ 有限时，级数绝对收敛。

显然每个测度都是符号测度，通常我们会把测度称为**正测度**。

我们可以立刻想到两个符号测度的例子。第一，设 $\mu_{1},\mu_{2}$ 是两个正测度，并且至少一个是有限的，那么 $\nu=\mu_{1}-\mu_{2}$ 就是一个符号测度。第二，设 $\mu$ 是一个正测度，$f\colon X\to[-\infty,+\infty]$ 是一个可测函数，并且 $\int f^{+}\mathrm{d}\mu$，$\int f^{-}\mathrm{d}\mu$ 至少有一个是有限的（这种情况下我们称 $f$ 是一个**广义** $\mu$**-可积**函数），那么 $\nu(E)=\int_{E}f\mathrm{d}\mu$ 就是一个符号测度。之后我们将证明，所有符号测度都是这两种情况之一。

**定理 23.1.2**

设 $\nu$ 是 $(X,\mathcal{M})$ 上的符号测度，如果 $E_{0}\subset E_{1}\subset\cdots$，那么 $\nu\left( \bigcup_{n=0}^{\infty}E_{n} \right)=\lim_{ n \to \infty }\nu(E_{n})$，如果 $E_{0}\supset E_{1}\supset\cdots$ 并且 $\nu(E_{0})$ 是有限的，那么 $\nu\left( \bigcap_{n=0}^{\infty}E_{n} \right)=\lim_{ n \to \infty }\nu(E_{n})$.

上述定理的证明与定理 20.2.4 是一致的，都需要用到测度的可数可加性。

**定义 23.1.3** 正的（positive），负的（negative），零的（null）

设 $\nu$ 是 $(X,\mathcal{M})$ 上的符号测度，称 $E\in \mathcal{M}$ 是**正的**（或**负的**，**零的**），如果对任意 $F\subset E,F\in \mathcal{M}$ 有 $\nu(F)\geq 0$（或 $\nu(F)\leq 0,\nu(F)=0$）。

**引理 23.1.4**

正集的可测子集是正的，可数个正集的并也是正的。

**证明**

设 $E$ 是正集，$F\in \mathcal{M},F\subset E$，如果 $G\subset F,G\in \mathcal{M}$，那么 $G\subset E$，故 $\nu(G)\geq 0$，因此 $F$ 是正集。

设 $(P_{j})_{j=1}^{\infty}$ 是正集，令 $Q_{n}=P_{n}\setminus\bigcup_{j=1}^{n}P_{j}$，则 $Q_{n}\subset P_{n}$，故 $Q_{n}$ 是正集，从而对任意 $E\subset \bigcup_{j=1}^{\infty}P_{j},E\in \mathcal{M}$ 有 $\nu(E)=\sum_{j=1}^{\infty}\nu(E\cap Q_{j})\geq 0$，即证。

**定理 23.1.5** Hahn 分解定理（Hahn decomposition theorem）

设 $\nu$ 是 $(X,\mathcal{M})$ 上的符号测度，那么存在正集 $P$ 和负集 $N$ 使得 $P\cup N=X$，$P\cap N=\varnothing$. 如果 $P',N'$ 是另一对满足上述条件的集合，那么 $P\Delta P'=N\Delta N'$ 是零集。

**证明**

不失一般性地，我们设 $\nu$ 不能取到 $+\infty$（否则可以将 $\nu$ 替换为 $-\nu$）。设 $m=\sup\{ \nu(P) \mid P \text{是正集} \}$，则存在正集 $(P_{j})_{j=1}^{\infty}$ 使得 $\lim_{ j \to \infty }\nu(P_{j})=m$，令 $P=\bigcup_{j=1}^{\infty}P_{j}$，则 $P$ 是正集，并且 $\nu(P)=m$，特别地，$m<+\infty$. 下面我们要证 $N=X\setminus P$ 是负集，我们将使用反证法。

假设 $N$ 不是负集，首先我们注意到 $N$ 不可能包含非零的正集：如果 $E\subset N$ 是正集且 $\nu(E)>0$，那么 $E\cup P$ 是正集，并且有 $\nu(E\cup P)=\nu(E)+\nu(P)>m$，矛盾。

其次，如果 $A\subset N$ 并且 $\nu(A)>0$，那么存在 $B\subset A$ 且 $\nu(B)>\nu(A)$：由于 $A$ 不是正集，故存在 $C\subset A$ 使得 $\nu(C)<0$，令 $B=A\setminus C$，则 $\nu(B)=\nu(A)-\nu(C)>\nu(A)$.

现在我们按以下方法构造 $(A_{j})$ 和 $(n_{j})$：设 $n_{1}$ 是最小的一个正整数使得存在 $B\subset N$ 满足 $\nu(B)> \dfrac{1}{n_{1}}$，将其中一个 $B$ 取为 $A_{1}$. 递归地取 $n_{j}$ 为最小的一个正整数使得存在 $B\subset A_{j-1}$ 满足 $\nu(B)> \nu(A_{j-1})+ \dfrac{1}{n_{j}}$，将其中一个 $B$ 取为 $A_{j}$.

令 $A=\bigcap_{j=1}^{\infty}A_{j}$，则 $+\infty>\nu(A)=\lim_{ j \to \infty }\nu(A_{j})>\sum_{j=1}^{\infty}n_{j}^{-1}$，于是 $\lim_{ j \to \infty }n_{j}=+\infty$. 然而，由于 $A\subset N$ 且 $\nu(A)>0$，故存在 $B\subset A$ 满足 $\nu(B)>\nu(A)+ \dfrac{1}{n}$，当 $j$ 足够大时有 $n<n_{j}$，此时也有 $B\subset A_{j-1}$，这与 $n_{j}$ 的最小性矛盾。

因此 $N$ 是一个负集，并且如果 $P',N'$ 是另一对这样的集合，那么我们有 $P\setminus P'\subset P$，$P\setminus P'\subset X\setminus P'=N'$，从而 $P\setminus P'$ 既是正集也是负集，从而是一个零集，对 $P'\setminus P$ 同理，故 $P\Delta P'$ 是零集，这就完成了证明。

上述定理中的 $X=P\cup N$ 称为 $\nu$ 的 **Hahn 分解**，利用它可以将一个符号测度分解为两个正测度的差。在此之前我们还需要一个概念：

**定义 23.1.6** 互异（mutually singular）

设 $\mu,\nu$ 是 $(X,\mathcal{M})$ 上的符号测度，称 $\mu,\nu$ 是**互异的**，如果存在 $E,F \in \mathcal{M}$ 使得 $E\cup F=X,E\cap F=\varnothing$，且 $E$ 是 $\mu$-零集，$F$ 是 $\nu$-零集，记作 $\mu \perp \nu$.

**定理 23.1.7** Jordan 分解定理（Jordan decomposition theorem）

如果 $\nu$ 是 $(X,\mathcal{M})$ 上的符号测度，那么存在唯一的正测度 $\nu^{+},\nu^{-}$ 使得 $\nu=\nu^{+}-\nu^{-}$ 且 $\nu^{+}\perp \nu^{-}$.

**证明**

设 $X=P\cup N$ 是 $\nu$ 的一个 Hahn 分解，令 $\nu^{+}(E)=\nu(E\cap P)$，$\nu^{-}(E)=-\nu(E\cap N)$，则显然有 $\nu=\nu^{+}-\nu^{-},\nu^{+}\perp \nu^{-}$.

如果又有 $\nu=\mu^{+}-\mu^{-},\mu^{+}\perp \mu^{-}$，令 $E,F \in \mathcal{M}$ 满足 23.1.6 中的条件，其中 $\mu^{+}(F)=\mu^{-}(E)=0$，则 $X=E\cup F$ 是 $\nu$ 的一个 Hahn 分解，于是 $P\Delta E$ 是 $\nu$-零集，从而对任意 $A \in \mathcal{M}$ 有

$$
\mu^{+}(A)=\mu^{+}(A\cap E)=\nu(A\cap E)=\nu(A\cap P)=\nu^{+}(A)
$$

同理也有 $\nu^{-}=\mu^{-}$，这就完成了证明。

等式 $\nu=\nu^{+}-\nu^{-}$ 就称为 $\nu$ 的 **Jordan 分解**，其中的正测度 $\nu^{+},\nu^{-}$ 分别称为 $\nu$ 的**正变差**与**负变差**。此外，我们还可以定义**总变差**为

$$
\lvert \nu \rvert =\nu^{+}+\nu^{-}
$$

它也是一个正测度。

**定理 23.1.8**

设 $\nu$ 是 $(X,\mathcal{M})$ 上的符号测度，那么 $E$ 是 $\nu$-零集当且仅当 $|\nu|(E)=0$. 如果 $\mu$ 是另一个符号测度，那么 $\nu \perp \mu$ 当且仅当 $|\nu|\perp \mu$ 当且仅当 $\nu^{+}\perp \mu$ 且 $\nu^{-}\perp \mu$.

**证明**

如果 $|\nu|(E)=\nu^{+}(E)+\nu^{-}(E)=0$，则 $\nu^{+}(E)=\nu^{-}(E)=0$，于是对任意 $F\subset E$ 有 $\nu^{+}(F)=\nu^{-}(F)=0$，即 $\nu(F)=0$，故 $E$ 是零集。反之，设 $E$ 是零集，则 $\nu(E\cap P)=\nu^{+}(E)=0,-\nu(E\cap N)=\nu^{-}(E)=0$，从而 $|\nu|(E)=0$.

设 $\nu \perp \mu$，则存在 $E,F$ 使得 $X=E\cup F,E\cap F=\varnothing$，且 $E$ 是 $\nu$-零集，$F$ 是 $\mu$-零集，于是 $|\nu|(E)=0$，因此 $E$ 也是 $|\nu|$-零集，即 $|\nu|\perp \mu$. 反之，设 $|\nu|\perp \mu$，则同样有 $|\nu|(E)=0$，因此 $E$ 是 $\nu$-零集，即 $\nu \perp \mu$.

设 $|\nu|\perp \mu$，则 $|\nu|(E)=0$，即 $\nu^{+}(E)=\nu^{-}(E)=0$，从而 $\nu^{+}\perp \mu$，$\nu^{-}\perp \mu$. 反之，设 $X=E_{1}\cup F_{1}=E_{2}\cup F_{2}$ 是相应的集合，设 $E=E_{1}\cap E_{2}$，$F=F_{1}\cup F_{2}$，则 $|\nu|(E)=0$，并且 $|\mu|(F)\leq|\mu|(F_{1})+|\mu|(F_{2})=0$，则 $|\nu|\perp|\mu|$，即 $|\nu|\perp \mu$，这就完成了证明。

我们可以看到，如果 $\nu$ 没有取到 $+\infty$，那么 $\nu^{+}(X)=\nu(P)<+\infty$，即 $\nu^{+}$ 是一个有限测度，对 $\nu^{-}$ 也是同理。因此，每个符号测度都可以分解为 $\nu=\nu^{+}-\nu^{-}$，其中至少一个测度是有限的，这就是我们开头给出的第一个例子。

对于第二个例子，我们有 $\nu(E)=\int_{E}f\mathrm{d}\mu$，其中 $f=\chi_{P}-\chi_{N},\mu=|\nu|$. 一个函数关于符号测度 $\nu$ 的积分也可以自然地定义：

$$
\int f\mathrm{d} \nu=\int f\mathrm{d} \nu^{+}-\int f\mathrm{d} \nu^{-} \quad (f \in L^{1}(\nu)=L^{1}(\nu^{+})\cap L^{1}(\nu^{-}))
$$

最后，我们再给出一个概念：称符号测度 $\nu$ 是**有限的**或 $\sigma$**-有限的**，如果 $|\nu|$ 是有限的或 $\sigma$-有限的。

# Section 2: Lebesgue-Radon-Nikodym 定理

本节的主定理是 Lebesgue-Radon-Nikodym 定理，它描述了一个测度关于另一个测度的“导数”是什么，为证明这个定理，我们需要一些概念。

**定义 23.2.1** 绝对连续（absolutely continuous）

设 $(X,\mathcal{M})$ 是可测空间，$\nu$ 是一个符号测度，$\mu$ 是一个正测度，称 $\nu$ 关于 $\mu$ 是**绝对连续的**，如果对任意满足 $\mu(E)=0$ 的 $E \in \mathcal{M}$ 有 $\nu(E)=0$，记作 $\nu\ll \mu$.

**定理 23.2.2**

设 $(X,\mathcal{M})$ 是可测空间，$\nu$ 是一个符号测度，$\mu$ 是一个正测度，则 $\nu\ll \mu$ 当且仅当 $|\nu|\ll \mu$ 当且仅当 $\nu^{+}\ll \mu$ 且 $\nu^{-}\ll \mu$.

**证明**

设 $\nu\ll \mu$，则对任意 $\mu(E)=0$ 的 $E$ 有 $\nu(E)=0$，设 $X=P\cup N$ 是一个 Hahn 分解，由于 $E\cap P \in \mathcal{M}$，$E\cap N \in \mathcal{M}$，于是 $\nu^{+}(E)=\nu^{-}(E)=0$，从而 $|\nu|\ll \mu$.

设 $|\nu|\ll \mu$，则 $|\nu|(E)=0$ 当且仅当 $\nu^{+}(E)=\nu^{-}(E)=0$，从而 $\nu^{+}\ll \mu$ 且 $\nu^{-}\ll \mu$. 最后，如果 $\nu^{+}\ll \mu$ 且 $\nu^{-}\ll \mu$，由于 $\nu=\nu^{+}-\nu^{-}$，故 $\nu\ll \mu$.

在某种程度上，绝对连续性是互异性的对立面：如果 $\nu \perp \mu$ 且 $\nu\ll \mu$，那么有 $X=E\cup F,E\cap F=\varnothing$ 满足 $\mu(E)=|\nu|(F)=0$，于是 $|\nu|(E)=0$，从而 $|\nu|=0$，进而有 $\nu=0$.

这一概念之所以被称为绝对连续，是因为它本质上也是一种连续性：

**定理 23.2.3**

设 $(X,\mathcal{M})$ 是可测空间，$\nu$ 是一个有限符号测度，$\mu$ 是一个正测度，那么 $\nu\ll \mu$ 当且仅当对任意 $\varepsilon>0$，存在 $\delta>0$ 使得对任意满足 $\mu(E)<\delta$ 的 $E \in \mathcal{M}$ 有 $|\nu(E)|<\varepsilon$.

**证明**

由于 $\nu\ll \mu$ 当且仅当 $|\nu|\ll \mu$，故我们可以假设 $\nu$ 是正测度。显然 $\varepsilon-\delta$ 条件可以推出 $\nu\ll \mu$，现在设 $\varepsilon-\delta$ 不成立。这表明存在 $\varepsilon>0$ 使得对任意 $n$ 都存在 $E_{n}$ 使得 $\mu(E_{n})<2^{-n}$ 且 $\nu(E_{n})\geq\varepsilon$，令 $F_{k}=\bigcup_{j=k}^{\infty}E_{j}$，$F=\bigcap_{k=1}^{\infty}F_{k}$，则 $\mu(F_{k})\leq \sum_{j=k}^{\infty}2^{-j}=2^{1-k}$，于是 $\mu(F)=0$，然而对任意 $k$ 有 $\nu(F_{k})\geq\varepsilon$，又 $\nu$ 是有限的，故 $\nu(F)=\lim_{ k \to \infty }\nu(F_{k})\geq\varepsilon$，因此 $\nu$ 关于 $\mu$ 不是绝对连续的，这就完成了证明。

如果 $f$ 是一个广义 $\mu$-可积的函数，那么 $\nu(E)=\int_{E}f\mathrm{d}\mu$ 就是一个符号测度，并且显然有 $\nu\ll \mu$. 此外，$\nu$ 是有限的当且仅当 $f \in L^{1}(X,\mu)$，对 $f$ 的实部和虚部分别应用上述定理即得推论：

**定理 23.2.4**

设 $f \in L^{1}(X,\mu)$，那么对任意 $\varepsilon>0$，存在 $\delta>0$ 使得对任意满足 $\mu(E)<\delta$ 的 $E \in \mathcal{M}$ 有 $\left\lvert  \int_{E}f\mathrm{d}\mu  \right\rvert<\varepsilon$.

对于测度 $\nu(E)=\int_{E}f\mathrm{d}\mu$，我们可以发现，它本质上就是函数 $f$ 的**不定积分**，我们可以用

$$
\mathrm{d} \nu=f \mathrm{d} \mu
$$

来表示它，相对地，$f$ 在某种程度上就可以看作 $\nu$ 关于 $\mu$ 的**导数**。有时候，我们也会把符号测度 $\nu$ 说成符号测度 $f\mathrm{d}\mu$.

下面我们将给出本节的主定理，它完整地表示出了一个符号测度关于一个正测度的结构。首先我们需要两个引理：

**引理 23.2.5**

设 $\mu,\nu$ 是 $(X,\mathcal{M})$ 上的有限测度，那么或者 $\mu \perp \nu$，或者存在 $\varepsilon>0$ 和 $E \in \mathcal{M}$ 使得 $\mu(E)>0$ 且 $E$ 关于 $\nu-\varepsilon \mu$ 是正集。

**证明**

设 $X=P_{n}\cup N_{n}$ 是 $\nu- \dfrac{1}{n}\mu$ 的一个 Hahn 分解，令 $P=\bigcup_{j=1}^{\infty}P_{j}$，$N=\bigcap_{j=1}^{\infty}N_{j}=P^{c}$，则对任意 $n$，$N$ 关于 $\nu- \dfrac{1}{n}\mu$ 是负集，即 $0\leq \nu(N)\leq \dfrac{1}{n}\mu(N)$，从而 $\nu(N)=0$. 如果 $\mu(P)=0$，那么 $\mu \perp \nu$，如果 $\mu(P)>0$，那么存在 $n$ 使得 $\mu(P_{n})>0$，于是 $\nu(P_{n})\geq \dfrac{1}{n}\mu(P_{n})$，即证。

**引理 23.2.6**

设 $(\nu_{j})_{j=1}^{\infty},\mu$ 都是 $(X,\mathcal{M})$ 上的正测度，如果对任意 $j$ 都有 $\nu_{j}\perp \mu$，那么 $\sum_{j=1}^{\infty}\nu_{j}\perp \mu$，并且如果对任意 $j$ 都有 $\nu_{j}\ll \mu$，那么 $\sum_{j=1}^{\infty}\nu_{j}\ll \mu$.

**证明**

设 $\nu_{j}\perp \mu$，并且有 $X=E_{j}\cup F_{j}$，$\nu_{j}(E_{j})=\mu(F_{j})=0$，令 $E=\bigcap_{j=1}^{\infty}E_{j}$，$F=\bigcup_{j=1}^{\infty}F_{j}$，则 $\sum_{j=1}^{\infty}\nu_{j}(E)=0$，并且 $\mu(F)\leq \sum_{j=1}^{\infty}\mu(F_{j})=0$，从而 $\sum_{j=1}^{\infty}\nu_{j}\perp \mu$.

现在设 $\nu_{j}\ll \mu$，则对任意 $\mu(E)=0$ 的 $E$ 有 $\nu_{j}(E)=0$，从而 $\sum_{j=1}^{\infty}\nu_{j}(E)=0$，即 $\sum_{j=1}^{\infty}\nu_{j}\ll \mu$，即证。

**定理 23.2.7** Lebesgue-Radon-Nikodym 定理

设 $(X,\mathcal{M})$ 是可测空间，$\nu$ 是 $\sigma$-有限的符号测度，$\mu$ 是 $\sigma$-有限的正测度，那么唯一存在 $\sigma$-有限的符号测度 $\lambda,\rho$ 使得

$$
\lambda \perp \mu, \rho\ll \mu, \nu=\lambda+\rho
$$

此外，还存在广义 $\mu$-可积的函数 $f\colon X\to \mathbb{R}$ 使得 $\mathrm{d}\rho=f\mathrm{d}\mu$，如果函数 $g$ 也满足上述性质，则 $f=g$ $\mu$-a.e.

**证明**

首先我们设 $\mu,\nu$ 都是有限的正测度。令

$$
\mathcal{F}=\left\{  f\colon X\to[0,+\infty] \middle| \int_{E}f\mathrm{d} \mu\leq \nu(E), \forall E \in \mathcal{M}  \right\}
$$

我们有 $0 \in \mathcal{F}$，并且如果 $f,g \in \mathcal{F}$，那么 $h=\max(f,g)\in \mathcal{F}$：设 $A=\{ x \mid f(x)>g(x) \}$，则对任意 $E \in \mathcal{M}$ 有

$$
\int_{E} h\mathrm{d} \mu=\int_{E\cap A}f\mathrm{d} \mu+\int_{E\setminus A}g\mathrm{d} \mu\leq \nu(E\cap A)+\nu(E\setminus A)=\nu(E)
$$

设 $a=\sup\left\{  \int f \mathrm{d}\mu \mid f \in \mathcal{F}  \right\}$，则 $a\leq \nu(X)<+\infty$，并且我们可以取 $\mathcal{F}$ 中的序列 $(f_{n})_{n=1}^{\infty}$ 使得 $\lim_{ n \to \infty } \int f \mathrm{d}\mu=a$. 令 $g_{n}=\max(f_{1},\dots,f_{n})$，$f=\sup_{n\geq 1}f_{n}$，则 $g_{n}$ 递增且逐点收敛于 $f$，并且 $\int g_{n}\mathrm{d}\mu\geq \int f_{n}\mathrm{d}\mu$，因此 $\lim_{ n \to \infty }\int g_{n}\mathrm{d}\mu=a$，根据单调收敛定理，$f \in \mathcal{F}$ 且 $\int f\mathrm{d}\mu=a$. 特别地，$\int f\mathrm{d}\mu<+\infty$，因此 $f$ 是 a.e. 有限的，从而可以重定义 $f$ 为实值函数。

下面我们要证正测度 $\mathrm{d}\lambda=\mathrm{d}\nu-f\mathrm{d}\mu$ 与 $\mu$ 互异。假设不然，根据引理 23.2.5 知存在 $E \in \mathcal{M}$ 和 $\varepsilon>0$ 使得 $\mu(E)>0$ 且 $E$ 关于 $\lambda-\varepsilon \mu$ 是正集，从而 $\varepsilon \chi_{E}\mathrm{d}\mu\leq \mathrm{d}\lambda=\mathrm{d}\nu-f\mathrm{d}\mu$，即 $(f+\varepsilon \chi_{E})\mathrm{d}\mu\leq \mathrm{d}\nu$，即 $f+\varepsilon \chi_{E}\in \mathcal{F}$，然而 $\int_{E}(f+\varepsilon \chi_{E})\mathrm{d}\mu=a+\varepsilon \mu(E)>a$，矛盾。

下面证明唯一性。设又有 $\mathrm{d}\nu=\mathrm{d}\lambda'+f'\mathrm{d}\mu$，于是 $\mathrm{d}\lambda-\mathrm{d}\lambda'=(f-f')\mathrm{d}\mu$，但 $\lambda-\lambda'\perp \mu$，$(f-f')\mathrm{d}\mu\ll \mathrm{d}\mu$，因此 $\lambda=\lambda'$ 且 $f=f'$ $\mu$-a.e. 这就完成了有限测度情况的证明。

现设 $\nu,\mu$ 是 $\sigma$-有限的正测度，则 $X$ 是可数个 $\mu$-有限集合或者 $\nu$-有限集合的并，对这些集合取交集，我们可以得到 $(A_{j})_{j=1}^{\infty}$ 使得 $\mu(A_{j}),\nu(A_{j})$ 都是有限的，并且 $X=\bigcup_{j=1}^{\infty}A_{j}$. 令 $\mu_{j}(E)=\mu(E\cap A_{j}),\nu_{j}=\nu(E\cap A_{j})$，则对任意 $j$，都有 $\lambda_{j},f_{j}$ 使得 $\mathrm{d}\nu_{j}=\mathrm{d}\lambda_{j}+f_{j}\mathrm{d}\mu_{j}$，且 $\lambda_{j}\perp \mu_{j}$. 由于 $\mu_{j}(A_{j}^{c})=\nu_{j}(A_{j}^{c})=0$，因此 $\lambda_{j}(A_{j}^{c})=\nu_{j}(A_{j}^{c})-\int_{A_{j}^{c}}f_{j}\mathrm{d}\mu_{j}=0$，并且我们可以假设在 $A_{j}^{c}$ 上 $f_{j}=0$.

令 $\lambda=\sum_{j=1}^{\infty}\lambda_{j},f=\sum_{j=1}^{\infty}f_{j}$，则 $\mathrm{d}\nu=\mathrm{d}\lambda+f\mathrm{d}\mu$，并且由引理 23.2.6 得 $\lambda \perp \mu$，并且 $\lambda$ 和 $f\mathrm{d}\mu$ 都是 $\sigma$-有限的。唯一性的证明与有限部分的证明一致，这就完成了 $\sigma$-有限的正测度部分的证明。

最后，如果 $\nu$ 是 $\sigma$-有限的符号测度，对 $\nu^{+},\nu^{-}$ 分别应用 $\sigma$-有限的正测度部分的结论，然后相减就完成了证明。

等式 $\nu=\lambda+\rho$ 称为 $\nu$ 关于 $\mu$ 的 **Lebesgue 分解**。当 $\nu\ll \mu$ 时，存在函数 $f$ 使得 $\mathrm{d}\nu=f\mathrm{d}\mu$，并且 $f$ 在 $\mu$-a.e. 相等的意义下是唯一的，我们把这一等价类称为 $\nu$ 关于 $\mu$ 的 **Radon-Nikodym 导数**，记作

$$
\mathrm{d} \nu= \dfrac{\mathrm{d} \nu}{\mathrm{d} \mu}\mathrm{d} \mu
$$

符号 $\dfrac{\mathrm{d}\nu}{\mathrm{d}\mu}$ 来源于一元微分学。事实上，Radon-Nikodym 导数的确满足许多正常导数满足的性质，例如可加性：$\dfrac{\mathrm{d}(\nu_{1}+\nu_{2})}{\mathrm{d}\mu}=\dfrac{\mathrm{d}\nu_{1}}{\mathrm{d}\mu}+\dfrac{\mathrm{d}\nu_{2}}{\mathrm{d}\mu}$，以及链式法则：

**定理 23.2.8**

设 $(X,\mathcal{M})$ 是可测空间，$\nu$ 是 $\sigma$-有限的符号测度，$\mu,\lambda$ 是 $\sigma$-有限的正测度，并且 $\nu\ll \mu,\mu\ll\lambda$，则有：

1. 如果 $g \in L^{1}(\nu)$，那么 $g \dfrac{\mathrm{d}\nu}{\mathrm{d}\mu}\in L^{1}(\mu)$，并且 $$
\int g\mathrm{d} \nu=\int g \dfrac{\mathrm{d} \nu}{\mathrm{d} \mu} \mathrm{d} \mu
$$
2. $\nu\ll\lambda$，并且 $$
\dfrac{\mathrm{d} \nu}{\mathrm{d} \lambda}=\dfrac{\mathrm{d} \nu}{\mathrm{d} \mu} \dfrac{\mathrm{d} \mu}{\mathrm{d} \lambda} \quad \lambda\text{-a.e.}
$$

**证明**

通过考虑 $\nu^{+}$ 和 $\nu^{-}$，我们可以假设 $\nu$ 是正测度。当 $g=\chi_{E}$ 时，上述等式就退化为 $\displaystyle \nu(E)=\int_{E} \dfrac{\mathrm{d}\nu}{\mathrm{d}\mu}\mathrm{d}\mu$，这就是导数的定义，因此等式对特征函数成立。根据积分的线性性，等式对简单函数成立，然后利用单调收敛定理得等式对非负函数成立，最后再使用线性性知等式对 $g \in L^{1}(\nu)$ 成立。

$\nu\ll\lambda$ 是显然的，任取 $E \in \mathcal{M}$，令 $g=\chi_{E} \dfrac{\mathrm{d}\nu}{\mathrm{d}\mu}$ 并应用结论 1 得

$$
\nu(E)=\int_{E} \dfrac{\mathrm{d} \nu}{\mathrm{d} \mu}\mathrm{d} \mu=\int_{E} \dfrac{\mathrm{d} \nu}{\mathrm{d} \mu} \dfrac{\mathrm{d} \mu}{\mathrm{d} \lambda}\mathrm{d} \lambda
$$

从而我们有 $\mathrm{d}\nu=\dfrac{\mathrm{d}\nu}{\mathrm{d}\mu} \dfrac{\mathrm{d}\mu}{\mathrm{d}\lambda}\mathrm{d}\lambda$，根据定理 23.2.7 的唯一性部分即证。

根据上述定理，我们有一个显然的推论：

**定理 23.2.9**

设 $(X,\mathcal{M})$ 是可测空间，$\mu,\lambda$ 是 $\sigma$-有限的正测度，并且 $\mu\ll\lambda,\lambda\ll \mu$，则 $\dfrac{\mathrm{d}\mu}{\mathrm{d}\lambda} \dfrac{\mathrm{d}\lambda}{\mathrm{d}\mu}=1$ a.e.（关于 $\mu$ 或 $\lambda$ 都成立）。

事实上，定理 23.2.7 可以做进一步的扩展，使其适用于任意的符号测度。

**定理 23.2.10** Radon-Nikodym 定理

设 $(X,\mathcal{M})$ 是可测空间，$\nu$ 是一个符号测度，$\mu$ 是 $\sigma$-有限的正测度，并且 $\nu\ll \mu$，那么存在广义 $\mu$-可积的函数 $f\colon X\to[-\infty,+\infty]$ 使得 $\mathrm{d}\nu=f\mathrm{d}\mu$.

**证明**

我们只需考虑 $\nu$ 是正测度且 $\mu$ 是有限测度的情况。令

$$
a=\sup \{ \mu(F) \mid F \in \mathcal{M} \text{关于} \nu \text{是} \sigma \text{-有限的} \}
$$

于是存在 $(F_{j})_{j=1}^{\infty}$ 使得 $\lim_{ j \to \infty }\mu(F_{j})=a$，令 $E=\bigcup_{j=1}^{\infty}F_{j}$，则 $E \in \mathcal{M}$ 关于 $\nu$ 也是 $\sigma$-有限的，并且 $\mu(E)\geq \mu(F_{j})$，从而 $\mu(E)=a$.

在 $E$ 上应用 Lebesgue-Radon-Nikodym 定理，则存在 $g\colon E\to \mathbb{R}$ 使得

$$
\mathrm{d} \nu|_{E}=g \mathrm{d} \mu|_{E}
$$

现设 $F\cap E=\varnothing$，如果 $\mu(F)=0$，由 $\nu\ll \mu$ 得 $\nu(F)=0$. 如果 $\mu(F)>0$，假设 $\nu(F)<+\infty$，那么 $E\cup F$ 关于 $\nu$ 是 $\sigma$-有限的，并且 $\mu(E\cup F)=a+\mu(F)>a$，矛盾，故 $\nu(F)=+\infty$. 因此，我们可以定义

$$
f(x)=\begin{cases}
g(x) &, x \in E \\
+\infty &, x \not\in E
\end{cases}
$$

则有 $\mathrm{d}\nu=f\mathrm{d}\mu$，这就完成了证明。

上述定理，结合 Lebesgue-Radon-Nikodym 定理的唯一性部分，我们就得到了完整的 Radon-Nikodym 定理，它是抽象测度上的微积分基本定理，即对密度 $\dfrac{\mathrm{d}\nu}{\mathrm{d}\mu}$ 积分得到测度 $\nu$，对 $\nu$ 求导得到密度 $\dfrac{\mathrm{d}\nu}{\mathrm{d}\mu}$. 然而，为了使其更加实用化，我们还需要做进一步的工作，这就是下一章的内容了。

Radon-Nikodym 定理在概率论中也有很多应用，下面给出一例：

**定理 23.2.11**

设 $(X,\mathcal{M,\mu})$ 是测度空间，$\mathcal{N}\subset \mathcal{M}$ 是 $\sigma$-代数，$\nu=\mu|_{\mathcal{N}}$ 是 $\sigma$-有限的，那么如果 $f \in L^{1}(\mu)$，则存在 $g \in L^{1}(\nu)$ 使得 $\int_{E}f\mathrm{d}\mu=\int_{E}g\mathrm{d}\nu$ 对任意 $E \in \mathcal{N}$ 成立。如果 $h$ 是另一个满足上述条件的函数，那么 $g=h$ $\nu$-a.e.

**证明**

定义 $\mathcal{N}$ 上的符号测度 $\lambda(E)=\int_{E}f\mathrm{d}\mu$，则 $\lambda\ll \nu$，并且 $\lambda$ 是有限的，根据 Radon-Nikodym 定理，存在 $g \in L^{1}(\nu)$ 使得 $\mathrm{d}\lambda=g\mathrm{d}\nu$，即

$$
\lambda(E)=\int_{E}f\mathrm{d} \mu=\int_{E}g\mathrm{d} \nu
$$

根据导数的唯一性，我们有 $g=h$ $\nu$-a.e.，即证。

上面的函数 $g$ 通常被称为 $f$ 在 $\mathcal{N}$ 上的**条件期望**。

最后，我们以一个简单的结论结束本节。

**引理 23.2.12**

如果 $\mu_{1},\dots,\mu_{n}$ 是 $(X,\mathcal{M})$ 上的测度，那么定义为 $\mu=\sum_{j=1}^{n}\mu_{j}$ 的测度 $\mu$ 满足对任意 $j$ 有 $\mu_{j}\ll \mu$.

# Section 3: 复测度

**定义 23.3.1** 复测度（complex measure）

设 $(X,\mathcal{M})$ 是可测空间，函数 $\nu\colon \mathcal{M}\to \mathbb{C}$ 是一个**复测度**，如果：

1. $\nu(\varnothing)=0$
2. 设 $(E_{n})_{n=0}^{\infty}$ 是 $\mathcal{M}$ 中不相交的集合，则 $\nu\left( \bigcup_{n=0}^{\infty}E_{n} \right)=\sum_{n=0}^{\infty}\nu(E_{n})$，其中级数绝对收敛。

从定义中我们可以看出，复测度的值总是具有有限的绝对值，因此一个正测度（或者符号测度）是复测度当且仅当它是有限的。例如，如果 $\mu$ 是一个正测度，$f \in L^{1}(X,\mu)$，那么 $f\mathrm{d}\mu$ 就是一个复测度。

设 $\nu$ 是一个复测度，我们通常将它的实部和虚部记作 $\nu_{r}$ 和 $\nu_{i}$，于是 $\nu_{r},\nu_{i}$ 都是有限的符号测度。关于 $\nu$ 的积分也是容易定义的：

$$
\int f\mathrm{d} \nu=\int f \mathrm{d} \nu_{r}+i \int f \mathrm{d} \nu_{i} \quad (f \in L^{1}(\nu)=L^{1}(\nu_{r})\cap L^{1}(\nu_{i}))
$$

如果 $\mu,\nu$ 是复测度，那么 $\mu \perp \nu$ 当且仅当 $\mu_{r}\perp \nu_{r}$ 且 $\mu_{i}\perp \nu_{i}$. 并且如果 $\lambda$ 是一个正测度，那么 $\nu\ll\lambda$ 当且仅当 $\nu_{r}\ll\lambda$ 且 $\nu_{i}\ll\lambda$. 此外，将定理 23.2.7 应用到 $\nu$ 的实部和虚部，我们就有以下定理：

**定理 23.3.2** Lebesgue-Radon-Nikodym 定理

设 $(X,\mathcal{M})$ 是可测空间，$\nu$ 是一个复测度，$\mu$ 是 $\sigma$-有限的正测度，那么存在复测度 $\lambda$ 和 $f \in L^{1}(\mu)$ 使得

$$
\lambda \perp \mu, \mathrm{d} \nu=\mathrm{d} \lambda+f\mathrm{d} \mu
$$

并且如果又有 $\lambda',f'$ 满足上述条件，那么 $\lambda=\lambda'$ 且 $f=f'$ $\mu$-a.e.

同样，当 $\nu\ll \mu$ 时，我们把 $f$ 的等价类记作 $\dfrac{\mathrm{d}\nu}{\mathrm{d}\mu}$.

一个复测度 $\nu$ 的**总变差** $|\nu|$ 可以按如下方式定义：如果有正测度 $\mu$ 和函数 $f$ 使得 $\mathrm{d}\nu=f\mathrm{d}\mu$，那么 $\mathrm{d}|\nu|=|f|\mathrm{d}\mu$. 这个定义是良定的，因为我们可以证明每个复测度都可以写成 $\mathrm{d}\nu=f\mathrm{d}\mu$ 的形式：我们可以取 $\mu=|\nu_{r}|+|\nu_{i}|$，然后使用 Radon-Nikodym 定理即可得到 $f \in L^{1}(\mu)$. 此外，如果有 $\mathrm{d}\nu=f_{1}\mathrm{d}\mu_{1}=f_{2}\mathrm{d}\mu_{2}$，其中 $\mu_{1},\mu_{2}$ 是有限测度，令 $\rho=\mu_{1}+\mu_{2}$，则有

$$
\mathrm{d} \nu=f_{1} \dfrac{\mathrm{d} \mu_{1}}{\mathrm{d} \rho}\mathrm{d} \rho=f_{2} \dfrac{\mathrm{d} \mu_{2}}{\mathrm{d} \rho}\mathrm{d} \rho
$$

于是 $f_{1} \dfrac{\mathrm{d}\mu_{1}}{\mathrm{d}\rho}=f_{2} \dfrac{\mathrm{d}\mu_{2}}{\mathrm{d}\rho}$ $\rho$-a.e.，由于 $\dfrac{\mathrm{d}\mu_{j}}{\mathrm{d}\rho}$ 是非负的，从而有

$$
|f_{1}| \dfrac{\mathrm{d} \mu_{1}}{\mathrm{d} \rho}=\left\lvert  f_{1} \dfrac{\mathrm{d} \mu_{1}}{\mathrm{d} \rho}  \right\rvert =\left\lvert  f_{2} \dfrac{\mathrm{d} \mu_{2}}{\mathrm{d} \rho}  \right\rvert =|f_{2}| \dfrac{\mathrm{d} \mu_{2}}{\mathrm{d} \rho} \quad \rho\text{-a.e.}
$$

因此我们有

$$
|f_{1}| \mathrm{d} \mu_{1}= |f_{1}| \dfrac{\mathrm{d} \mu_{1}}{\mathrm{d} \rho} \mathrm{d} \rho=|f_{2}| \dfrac{\mathrm{d} \mu_{2}}{\mathrm{d} \rho}\mathrm{d} \rho=|f_{2}|\mathrm{d} \mu_{2}
$$

从而 $\lvert \nu \rvert$ 的定义与 $f,\mu$ 的选取是无关的，这一定义与符号测度的总变差是一致的，因为对于符号测度 $\nu$，我们有 $\mathrm{d}\nu=(\chi_{P}-\chi_{N})\mathrm{d}|\nu|$，其中 $X=P\cup N$ 是 $\nu$ 的 Hahn 分解，并且 $|\chi_{P}-\chi_{N}|=1$.

**定理 23.3.3**

设 $(X,\mathcal{M})$ 是可测空间，$\mu,\nu$ 是复测度，$\lambda$ 是正测度，那么 $\mu \perp \nu$ 当且仅当 $|\mu|\perp|\nu|$，并且 $\nu\ll\lambda$ 当且仅当 $|\nu|\ll\lambda$.

**证明**

如果 $\mu \perp \nu$，那么存在正测度 $\mu_{0},\nu_{0}$ 和 $f \in L^{1}(\mu_{0}),g \in L^{1}(\nu_{0})$ 使得 $\mathrm{d}\mu=f\mathrm{d}\mu_{0}$ 且 $\mathrm{d}\nu=g\mathrm{d}\nu_{0}$，此外，还存在 $X=E\cup F,E\cap F=\varnothing$ 使得 $E$ 是 $\mu$-零集，$F$ 是 $\nu$-零集，因此在 $E$ 上有 $f=0$ $\mu_{0}$-a.e.，从而 $|\mu|(E)=0$，同理 $|\nu|(F)=0$，即证 $|\mu|\perp|\nu|$. 反之同理。

再设 $\nu\ll\lambda$，则有正测度 $\mu$ 和 $f \in L^{1}(\mu)$ 使得 $\mathrm{d}\nu=f\mathrm{d}\mu$，设 $\lambda(E)=0$，则对任意 $F\subset E,F \in \mathcal{M}$ 有 $\int_{F}f\mathrm{d}\mu=0$，于是在 $E$ 上有 $f=0$ $\mu$-a.e.，从而 $|\nu|(E)=0$，即 $|\nu|\ll\lambda$. 反之同理。

**定理 23.3.4**

设 $\nu$ 是 $(X,\mathcal{M})$ 上的复测度，则有：

1. 对任意 $E \in \mathcal{M}$ 有 $|\nu(E)|\leq|\nu|(E)$
2. $\nu\ll|\nu|$，并且有 $\left\lvert  \dfrac{\mathrm{d}\nu}{\mathrm{d}|\nu|}  \right\rvert=1$ $|\nu|$-a.e.
3. $L^{1}(\nu)=L^{1}(|\nu|)$，并且如果 $f \in L^{1}(\nu)$，那么 $\left\lvert  \int f\mathrm{d}\nu  \right\rvert\leq \int|f|\mathrm{d}|\nu|$

**证明**

设 $\mu$ 是有限正测度，$f \in L^{1}(\mu)$ 使得 $\mathrm{d}\nu=f\mathrm{d}\mu$，则

$$
|\nu(E)|=\left\lvert  \int_{E} f \mathrm{d} \mu  \right\rvert \leq \int_{E} |f| \mathrm{d} \mu= |\nu|(E)
$$

这也表明 $\nu\ll|\nu|$，设 $g= \dfrac{\mathrm{d}\nu}{\mathrm{d}|\nu|}$，则有

$$
\mathrm{d} \nu=f\mathrm{d} \mu=g\mathrm{d} |\nu|=g |f|\mathrm{d} \mu
$$

从而 $f=g|f|$ $\mu$-a.e.，从而也有 $|\nu|$-a.e.，两边取绝对值，由于 $|f|>0$ $|\nu|$-a.e.，故 $|g|=1$ $|\nu|$-a.e.

设 $h \in L^{1}(\nu)$，则 $\int h \mathrm{d}\nu=\int hf\mathrm{d}\mu$ 存在且有限，于是

$$
\int |hf|\mathrm{d} \mu=\int|h| \mathrm{d} |\nu|<+\infty
$$

从而 $h \in L^{1}(|\nu|)$. 反之，设 $L^{1}(|\nu|)$，则有

$$
\left\lvert  \int hf\mathrm{d} \mu  \right\rvert \leq \int|hf|\mathrm{d} \mu<+\infty
$$

即 $\int h\mathrm{d}\nu$ 存在且有限，故 $h \in L^{1}(\nu)$. 此外，我们还有

$$
\left\lvert  \int h\mathrm{d} \nu  \right\rvert =\left\lvert  \int h \dfrac{\mathrm{d} \nu}{\mathrm{d} |\nu|}\mathrm{d} |\nu|  \right\rvert \leq \int|h|\mathrm{d} |\nu|
$$

这就完成了证明。

下面的性质通常称为测度的三角不等式。

**定理 23.3.5** 三角不等式（triangle inequality）

如果 $\nu_{1},\nu_{2}$ 是 $(X,\mathcal{M})$ 上的复测度，那么 $\lvert \nu_{1}+\nu_{2} \rvert\leq|\nu_{1}|+|\nu_{2}|$.

**证明**

根据引理 23.2.12，存在正测度 $\mu$ 使得 $\nu_{j}\ll \mu$，于是有 $\nu_{j}=f_{j}\mathrm{d}\mu$，从而

$$
\mathrm{d} |\nu_{1}+\nu_{2}|=|f_{1}+f_{2}|\mathrm{d} \mu\leq |f_{1}|\mathrm{d} \mu+|f_{2}|\mathrm{d} \mu=\mathrm{d} |\nu_{1}|+\mathrm{d} |\nu_{2}|
$$

即证。

最后，我们再给出一个定理，它表现了复测度的四个不同表示。

**定理 23.3.6**

设 $\nu$ 是 $(X,\mathcal{M})$ 上的复测度，对任意 $E \in \mathcal{M}$，定义

$$
\begin{gather}
\mu_{1}(E)=\sup \left\{  \sum_{j=1}^{n} |\nu(E_{j})| \middle| n\geq 1, E_{1},\dots,E_{n} \text{不相交}, E=\bigcup_{j=1}^{n} E_{j} \right\} \\
\mu_{2}(E)=\sup \left\{  \sum_{j=1}^{\infty} |\nu(E_{j})| \middle| E_{1},E_{2}\dots \text{不相交}, E=\bigcup_{j=1}^{\infty} E_{j} \right\} \\
\mu_{3}(E)=\sup \left\{  \left\lvert  \int_{E} f  \mathrm{d} \nu \right\rvert \middle| |f|\leq 1  \right\}
\end{gather}
$$

则 $\mu_{1}=\mu_{2}=\mu_{3}=|\nu|$.

**证明**

设 $E=\bigcup_{j=1}^{n}E_{j}$，将 $E_{n}$ 分割为 $E_{n}=\bigcup_{j=n}^{\infty}E_{j}'$，对于 $1\leq j< n$，定义 $E_{j}'=E_{j}$，则有 $E=\bigcup_{j=1}^{\infty}E_{j}'$，$E'_{1},E'_{2},\dots$ 不相交，并且由三角不等式得 $\sum_{j=1}^{n}|\nu(E_{j})|\leq \sum_{j=1}^{\infty}|\nu(E_{j}')|$，从而 $\mu_{1}\leq \mu_{2}$.

设 $E=\bigcup_{j=1}^{\infty}E_{j}$，令 $f=\sum_{j=1}^{\infty}c_{j}\chi_{E_{j}}$，其中 $c_{j}=\exp(-i \mathrm{arg}\ \nu(E_{j}))$，于是 $c_{j}\nu(E_{j})=|\nu(E_{j})|$，从而 $\int_{E}f\mathrm{d}\nu=\sum_{j=1}^{\infty}|\nu(E_{j})|$，因此我们有 $\mu_{2}\leq \mu_{3}$.

设 $|f|\leq 1$，则 $\left\lvert  \int_{E}f\mathrm{d}\nu  \right\rvert \leq \int_{E}|f|\mathrm{d}|\nu| \leq|\nu|(E)$，故 $\mu_{3}\leq|\nu|$. 再令 $f=\overline{\dfrac{\mathrm{d}\nu}{\mathrm{d}|\nu|}}$，则 $\int_{E}f\mathrm{d}\nu=\int_{E}\mathrm{d}|\nu|=|\nu|(E)$，于是 $|\nu|\leq \mu_{3}$，从而 $\mu_{3}=|\nu|$.

最后，我们要证 $\mu_{3}\leq \mu_{1}$. 设 $|f|\leq 1$，则存在简单函数 $\phi=\sum_{j=1}^{n}c_{j}\chi_{E_{j}}$ 使得 $|c_{j}|\leq 1$ 且 $\left\lvert  \int_{E}(f-\phi)\mathrm{d}\nu  \right\rvert<\varepsilon$，从而

$$
\left\lvert  \int_{E}f\mathrm{d} \nu  \right\rvert \leq \left\lvert  \int_{E}\phi \mathrm{d} \nu  \right\rvert +\varepsilon\leq \sum_{j=1}^{n} |\nu(E_{j})|+\varepsilon
$$

根据 $\varepsilon$ 的任意性就有 $\mu_{3}\leq \mu_{1}$，这就完成了证明。

复测度论，或者说复概率论，是量子力学的数学基础，这里我们只是简单地介绍了一些内容。