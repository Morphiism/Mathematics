在向量分析中，特别是在物理学的应用中，知道一个 $\mathbb{R}^{3}$ 中的向量场 $F$ 是否是某个标量场 $f$ 的梯度通常是重要的。如果答案是肯定的，那么我们就称 $F$ 是一个保守场，并称 $f$（有时为 $-f$）为其势函数。将其翻译为形式的语言，这就是说一个 $1$-形式 $\omega$ 是否是某个 $0$-形式 $f$ 的微分，也就是说，$\omega$ 是否是恰当的。

在其他应用中，我们有时也需要知道一个向量场 $G$ 是否是某个向量场 $F$ 的旋度。将其翻译为形式的语言，这就是说一个 $2$-形式 $\omega$ 是否是某个 $1$-形式的微分，也就是说，$\omega$ 是否是恰当的。

在本章中，我们来研究一般的问题：在什么情况下 $k$-形式 $\omega$ 是恰当的？我们知道，如果 $\omega$ 是定义在开集 $A$ 上的 $k$-形式，那么它是恰当的一个必要条件是它是闭的。然而，$\omega$ 的闭性在一般情况下无法充分地推出 $\omega$ 的恰当性，因此我们需要一些额外条件。在本章中，我们探讨为了确保 $\omega$ 是恰当的，需要在 $A$ 或者 $A$ 和 $\omega$ 上附加哪些条件。

# Section 1: Poincare 引理

令 $A$ 是 $\mathbb{R}^{n}$ 上的开集，在本节中，我们将证明如果 $A$ 满足一个称为**星状凸性**的条件，那么定义在 $A$ 上的闭形式 $\omega$ 就自动是恰当的。换句话说，闭形式的恰当性仅取决于底空间 $A$ 的拓扑性质，而与 $\omega$ 无关。这一结论就是著名的 Poincare 引理。

我们首先以一个基础结论开始：

**定理 5.1.1** Leibnitz 定律

设 $Q$ 是 $\mathbb{R}^{n}$ 中的长方形，$f\colon Q\times[a,b]\to \mathbb{R}$ 是一个连续函数，记作 $f=f(x,t)$，其中 $x \in Q,t \in[a,b]$. 则函数

$$
\begin{gather}
F(x)=\int_{a}^{b} f(x,t)\mathrm{d} t
\end{gather}
$$

在 $Q$ 上连续。此外，如果 $\dfrac{ \partial f }{ \partial x_{j} }$ 在 $Q\times[a,b]$ 上连续，则

$$
\begin{gather}
\dfrac{ \partial F }{ \partial x_{j} } (x)=\int_{a}^{b} \dfrac{ \partial f }{ \partial x_{j} } (x,t)\mathrm{d} t
\end{gather}
$$

**证明**

(1). 我们证明 $F$ 是连续的。由于 $Q\times[a,b]$ 是紧致集，因此 $f$ 在 $Q\times[a,b]$ 上一致连续，从而对任意 $\varepsilon>0$，存在 $\delta>0$ 使得

$$
\begin{gather}
\lVert (x_{1},t_{1})-(x_{0},t_{0}) \rVert <\delta \implies |f(x_{1},t_{1})-f(x_{0},t_{0})| <\varepsilon
\end{gather}
$$

于是，当 $\lVert x_{1}-x_{0} \rVert<\delta$ 时有

$$
\begin{gather}
F(x_{1})-F(x_{0})\leq \int_{a}^{b} |f(x_{1},t)-f(x_{0},t)|\mathrm{d} t\leq \varepsilon(b-a)
\end{gather}
$$

因此 $F$ 是连续的。

(2). 在计算定理中出现的积分和导数时，只有变量 $x_{j}$ 和 $t$ 是变化的，其他变量均保持不变，因此我们只需证明 $n=1$ 且 $Q=[c,d]$ 的情况。

给定 $x \in[c,d]$，我们定义

$$
\begin{gather}
G(x)=\int_{a}^{b} \dfrac{ \partial f }{ \partial x } (x,t)\mathrm{d} t
\end{gather}
$$

由于 $\dfrac{ \partial f }{ \partial x }$ 是连续的，故根据步骤 (1)，$G$ 是连续的。我们想证明 $F'(x)$ 存在并且等于 $G(x)$，为此，我们使用 Fubini 定理，得到：

$$
\begin{align}
\int_{c}^{x_{0}} G(x)\mathrm{d} x &= \int_{c}^{x_{0}} \int_{a}^{b} \dfrac{ \partial f }{ \partial x } (x,t) \mathrm{d} t \mathrm{d} x \\
&= \int_{a}^{b} \int_{c}^{x_{0}} \dfrac{ \partial f }{ \partial x } (x,t) \mathrm{d} x \mathrm{d} t \\
&= \int_{a}^{b} (f(x_{0},t)-f(c,t)) \mathrm{d} t \\
&= F(x_{0})-F(c)
\end{align}
$$

于是对任意 $x \in[c,d]$，我们有

$$
\begin{gather}
\int_{c}^{x} G=F(x)-F(c)
\end{gather}
$$

应用微积分基本定理，即证 $G=F'$.

**定义 5.1.2** 微分同伦（differentiable homotopy）

设 $A,B$ 分别是 $\mathbb{R}^{n}$ 和 $\mathbb{R}^{m}$ 中的开集，$g,h\colon A\to B$ 是 $C^{\infty}$ 函数。我们称 $g$ 和 $h$ 是**微分同伦的**，如果存在 $C^{\infty}$ 函数 $H\colon A\times I\to B$ 使得

$$
\begin{gather}
H(x,0)=g(x),\quad H(x,1)=h(x)
\end{gather}
$$

对 $x \in A$ 成立。函数 $H$ 就称为 $g$ 和 $h$ 之间的**微分同伦**。

对任意 $t$，函数 $x\mapsto H(x,t)$ 是一个从 $A$ 到 $B$ 的 $C^{\infty}$ 函数。如果我们把 $t$ 看作“时间”，那么 $H$ 给了我们一种将函数 $g$ “变形”成 $h$ 的方法。

现在我们得到了一个判定两个闭形式何时相差一个恰当形式的判据。

**定理 5.1.3**

设 $A,B$ 分别是 $\mathbb{R}^{n}$ 和 $\mathbb{R}^{m}$ 中的开集，$g,h\colon A\to B$ 是微分同伦的 $C^{\infty}$ 函数。则存在一个线性映射

$$
\begin{gather}
\mathcal{P}\colon \Omega^{k+1}(B)\to\Omega^{k}(A)
\end{gather}
$$

使得对任意阶数为 $k>0$ 的形式 $\eta$ 有

$$
\begin{gather}
\mathrm{d} \mathcal{P}\eta+\mathcal{P}\mathrm{d} \eta=h^{*}\eta-g^{*}\eta
\end{gather}
$$

而对 $0$-形式 $f$ 有

$$
\begin{gather}
\mathcal{P}\mathrm{d} f=h^{*}f-g^{*}f
\end{gather}
$$

这一定理表明，如果 $\eta$ 是一个正数阶闭形式，那么 $h^{*}\eta$ 与 $g^{*}\eta$ 仅相差一个恰当形式（因为 $\mathrm{d}\eta=0$）。另一方面，如果 $f$ 是一个闭 $0$-形式，那么 $h^{*}f-g^{*}f=0$.

注意 $\mathcal{P}$ 与微分算子 $\mathrm{d}$ 的不同：$\mathrm{d}$ 将形式的阶数提升 $1$，而 $\mathcal{P}$ 将形式的阶数降低 $1$，因此，$\mathcal{P}f$ 是无定义的。

**证明**

(1). 我们首先考虑一个特殊情况。给定 $\mathbb{R}^{n}$ 中的开集 $A$，令 $U$ 是 $\mathbb{R}^{n+1}$ 中 $A\times I$ 的一个邻域，并令 $\alpha,\beta\colon A\to U$ 为

$$
\begin{gather}
\alpha(x)=(x,0),\quad \beta(x)=(x,1)
\end{gather}
$$

则 $\alpha,\beta$ 是微分同伦的。我们定义，对任意 $U$ 上的 $k+1$ 形式，一个 $A$ 上的 $k$-形式 $P\eta$，使得

$$
\begin{gather}
\mathrm{d} P\eta+P\mathrm{d} \eta=\beta^{*}\eta-\alpha^{*}\eta \\
P\mathrm{d} f=\beta^{*}f-\alpha^{*}f
\end{gather}
$$

首先，我们用 $x$ 表示 $\mathbb{R}^{n}$ 中的一般点，用 $t$ 表示 $\mathbb{R}$ 中的一般点，则 $\mathrm{d}x_{1},\dots,\mathrm{d}x_{n},\mathrm{d}t$ 是 $\mathbb{R}^{n+1}$ 上的基本 $1$-形式。如果 $g$ 是 $A\times I$ 上的任意连续标量函数，我们定义 $A$ 上的标量函数 $\mathcal{I}g$ 为

$$
\begin{gather}
\mathcal{I}g(x)=\int_{0}^{1} g(x,t) \mathrm{d} t
\end{gather}
$$

然后我们定义 $P$ 如下：如果 $k\geq 0$，则 $\mathbb{R}^{n+1}$ 上的 $k+1$ 形式 $\eta$ 可以写成

$$
\begin{gather}
\eta=\sum_{[I]} f_{I} \mathrm{d} x_{I}+\sum_{[J]} g_{J} \mathrm{d} x_{J} \land \mathrm{d} t
\end{gather}
$$

其中 $I$ 表示一个升序 $k+1$ 元组，$J$ 表示一个升序 $k$-元组。我们定义

$$
\begin{align}
P\eta &=\sum_{[I]} P(f_{I} \mathrm{d} x_{I}) + \sum_{[J]} P(g_{J} \mathrm{d} x_{J}\land \mathrm{d} t) \\
&= \sum_{[J]} (-1)^{k} (\mathcal{I}g_{J}) \mathrm{d} x_{J}
\end{align}
$$

则 $P\eta$ 是定义在 $A$ 上的 $k$-形式。根据 $\eta$ 分解的唯一性以及积分算子 $\mathcal{I}$ 的线性性，我们立即得到 $P$ 的线性性。

为证明 $P\eta$ 是 $C^{\infty}$ 连续的，我们只需证明 $\mathcal{I}g_{J}$ 是 $C^{\infty}$ 连续的。后者由 Leibnitz 定律给出，因为 $g_{J}$ 是 $C^{\infty}$ 连续的。

注意，当 $k=0$ 时，$\eta$ 是 $1$-形式

$$
\begin{gather}
\eta=\sum_{i=1}^{n} f_{i} \mathrm{d} x_{i}+g\mathrm{d} t
\end{gather}
$$

则 $J$ 是一个 $0$-元组 $\varnothing$，并且我们有

$$
\begin{gather}
P\eta=P(g\mathrm{d} t)=\mathcal{I}g
\end{gather}
$$

尽管算子 $P$ 看起来似乎是人造的，但实际上它是一个相当自然的算子。正如 $\mathrm{d}$ 在某种意义上是一个“微分算子”一样，算子 $P$ 在某种意义上也是一个“积分算子”，即“沿着最后一个坐标方向对 $\eta$ 进行积分”。

(2). 我们证明等式

$$
\begin{gather}
P(f_{I}\mathrm{d} x_{I})=0,\quad P(g \mathrm{d} x_{J}\land \mathrm{d} t)=(-1)^{k} (\mathcal{I}g) \mathrm{d} x_{J}
\end{gather}
$$

在 $I$ 是任意 $k+1$ 元组，$J$ 是任意 $k$-元组时同样成立。这一证明是一个常规任务。如果有相同的指标，那么等式是平凡的。反之，我们可以对指标进行重排，使其成为升序元组，由于每次置换两个指标时等式两边均改变一次符号，因此等式在任意指标上是否成立取决于它在升序指标上是否成立，而后者根据定义是满足的，即证。

(3). 我们对 $k=0$ 来验证 $P$ 所声明的性质。我们计算

$$
\begin{align}
P\mathrm{d} f &= P\left( \sum_{i=1}^{n} \dfrac{ \partial f }{ \partial x_{i} } \mathrm{d} x_{i}+\dfrac{ \partial f }{ \partial t } \mathrm{d} t \right) \\
&= \mathcal{I}\left( \dfrac{ \partial f }{ \partial t }  \right) \\
&= f(x,1)-f(x,0) \\
&= \beta^{*}f-\alpha^{*}f
\end{align}
$$

(4). 我们对 $k>0$ 验证 $P$ 所声明的性质。我们指出，由于 $\alpha(x)=(x,0)$，因此

$$
\begin{gather}
\alpha^{*}(\mathrm{d} x_{i})=\mathrm{d} \alpha_{i}=\mathrm{d} x_{i} \\
\alpha^{*}(\mathrm{d} t)=\mathrm{d} \alpha_{n+1}=0
\end{gather}
$$

同理，上式对 $\beta$ 也成立。

现在，由于等式中涉及的运算都是线性的，因此我们只需对 $f\mathrm{d}x_{I}$ 和 $g\mathrm{d}x_{J}\land \mathrm{d}t$ 验证即可。我们首先考虑 $\eta=f\mathrm{d}x_{I}$，我们计算

$$
\begin{align}
\mathrm{d} P\eta+P\mathrm{d} \eta &= P(\mathrm{d} f\land \mathrm{d} x_{I}) \\
&= P\left( \sum_{i=1}^{n} \dfrac{ \partial f }{ \partial x_{i} } \mathrm{d} x_{i} \land \mathrm{d} x_{I}+\dfrac{ \partial f }{ \partial t } \mathrm{d} t \land \mathrm{d} x_{I} \right) \\
&= (-1)^{k+1} P\left( \dfrac{ \partial f }{ \partial t } \mathrm{d} x_{I}\land \mathrm{d} t \right) \\
&= \mathcal{I}\left( \dfrac{ \partial f }{ \partial t }   \right) \mathrm{d} x_{I} \\
&= (f\circ\beta-f\circ\alpha)\mathrm{d} x_{I}
\end{align}
$$

另一方面，我们有

$$
\begin{align}
\beta^{*}\eta-\alpha^{*}\eta &= (f\circ\beta) \beta^{*}(\mathrm{d} x_{I})-(f\circ\alpha) \alpha^{*}(\mathrm{d} x_{I}) \\
&= (f\circ\beta-f\circ\alpha) \mathrm{d} x_{I}
\end{align}
$$

下面我们考虑 $\eta=g\mathrm{d}x_{J}\land \mathrm{d}t$，我们计算

$$
\begin{align}
\mathrm{d} P\eta &= \mathrm{d} ((-1)^{k} (\mathcal{Ig})\mathrm{d} x_{J}) \\
&= (-1)^{k} \sum_{i=1}^{n} \dfrac{ \partial  }{ \partial x_{i} } (\mathcal{I}g) \mathrm{d} x_{i}\land \mathrm{d} x_{J}
\end{align}
$$

以及

$$
\begin{align}
P\mathrm{d} \eta &= P\left( \sum_{i=1}^{n} \dfrac{ \partial g }{ \partial x_{i} } \mathrm{d} x_{i}\land \mathrm{d} x_{J}\land \mathrm{d} t+\dfrac{ \partial g }{ \partial t } \mathrm{d} t \land \mathrm{d} x_{J}\land \mathrm{d} t \right) \\
&= (-1)^{k+1} \sum_{i=1}^{n} \mathcal{I}\left( \dfrac{ \partial g }{ \partial x_{i} }  \right) \mathrm{d} x_{i}\land \mathrm{d} x_{J}
\end{align}
$$

应用 Leibnitz 定律，我们得到

$$
\begin{gather}
\mathrm{d} P\eta+P\mathrm{d} \eta=0
\end{gather}
$$

另一方面，我们有

$$
\begin{align}
\beta^{*}(g\mathrm{d} x_{J}\land \mathrm{d} t)-\alpha^{*}(g\mathrm{d} x_{J}\land \mathrm{d} t)=0
\end{align}
$$

因为 $\beta^{*}(\mathrm{d}t)=\alpha^{*}(\mathrm{d}t)=0$，这就完成了这一特例的证明。

(5). 最后我们来证明一般情况。给定 $C^{\infty}$ 函数 $g,h\colon A\to B$ 以及微分同伦 $H\colon A\times I\to B$，令 $\alpha,\beta\colon A\to A\times I$ 和 $P$ 如前所示。我们定义 $\mathcal{P}\colon\Omega^{k+1}(B)\to\Omega^{k}(A)$ 如下：

$$
\begin{gather}
\mathcal{P}\eta=P(H^{*}\eta)
\end{gather}
$$

由于 $H^{*}\eta$ 是一个 $A\times I$ 上的 $k+1$ 形式，因此 $\mathcal{P}\eta$ 是 $A$ 上的 $k$-形式。

由于 $H$ 是 $g,h$ 之间的微分同伦，因此我们有

$$
\begin{gather}
H\circ\alpha=g, \quad H\circ\beta=h
\end{gather}
$$

从而当 $k>0$ 时我们有

$$
\begin{align}
\mathrm{d} \mathcal{P\eta}+\mathcal{P}\mathrm{d} \eta&= \mathrm{d} P(H^{*}\eta)+P (H^{*} \mathrm{d}\eta)  \\
&= \mathrm{d} P(H^{*}\eta)+P\mathrm{d} (H^{*}\eta) \\
&= \beta^{*}(H^{*}\eta)-\alpha^{*}(H^{*}\eta) \\
&= h^{*}\eta-g^{*}\eta
\end{align}
$$

当 $k=0$ 时同理。这就完成了证明。

现在我们来证明 Poincare 引理，首先，我们给出一个定义：

**定义 5.1.4** 星状凸（star-convex）

设 $A$ 是 $\mathbb{R}^{n}$ 中的开集，我们称 $A$ 关于点 $p \in A$ 是**星状凸的**，如果对任意 $x \in A$，连接 $x$ 和 $p$ 的直线段包含于 $A$ 中。

![](5-1.png)

如图所示，集合 $A$ 关于 $p$ 是星状凸的，而其关于 $q$ 点则不是；集合 $B$ 关于其上的每一点都是星状凸的，从而它是一个凸集；集合 $C$ 关于其上任意一点都不是星状凸的。

**定理 5.1.5** Poincare 引理

设 $A$ 是 $\mathbb{R}^{n}$ 上星状凸的开集，如果 $\omega$ 是 $A$ 上的闭形式，那么 $\omega$ 在 $A$ 上是恰当形式。

**证明**

我们将应用定理 5.1.3. 设 $A$ 关于 $p$ 点是星状凸的，令 $h\colon A\to A$ 为恒等映射，并令 $g\colon A\to A$ 为常值映射 $g(x)=p$. 则 $g$ 和 $h$ 是微分同伦的：函数

$$
\begin{gather}
H(x,t)=th(x)+(1-t)g(x)=tx+(1-t)p
\end{gather}
$$

就是一个微分同伦，我们称其为 $g$ 和 $h$ 之间的**直线同伦**。其中 $A$ 的星状凸性保证了 $H(x,t)$ 的良定性。

令 $\mathcal{P}$ 如定理 5.1.3 中所示，如果 $f$ 是一个闭 $0$-形式，则我们有

$$
\begin{gather}
h^{*}f-g^{*}f=f\circ h-f\circ g=0
\end{gather}
$$

于是对任意 $x \in A$ 有

$$
\begin{gather}
f(x)=f(h(x))=f(g(x))=f(p)
\end{gather}
$$

因此 $f$ 是常值函数。

如果 $\omega$ 是一个闭 $k$-形式，则

$$
\begin{gather}
\mathrm{d} \mathcal{P}\omega=h^{*}\omega-g^{*}\omega
\end{gather}
$$

由于 $h$ 是恒等映射，故 $h^{*}\omega=\omega$；又因为 $g$ 是常值函数，故 $g^{*}\omega=0$，因此 $\omega=\mathrm{d}\mathcal{P\omega}$ 是 $A$ 上的恰当形式。

**定理 5.1.6**

设 $A$ 是 $\mathbb{R}^{n}$ 上星状凸的开集，$\omega$ 是 $A$ 上的闭 $k$-形式。如果 $k>1$，且 $\eta$ 和 $\eta_{0}$ 是 $A$ 上两个 $k-1$ 形式使得 $\mathrm{d}\eta=\mathrm{d}\eta_{0}=\omega$，则

$$
\begin{gather}
\eta=\eta_{0}+\mathrm{d} \theta
\end{gather}
$$

对 $A$ 上的某个 $k-2$ 形式 $\theta$ 成立。如果 $k=1$，且 $f$ 和 $f_{0}$ 是 $A$ 上两个 $0$-形式使得 $\mathrm{d}f=\mathrm{d}f_{0}=\omega$，则 $f=f_{0}+c$ 对某个常数 $c$ 成立。

**证明**

如果 $k>1$，由于 $\mathrm{d}(\eta-\eta_{0})=0$，故形式 $\eta-\eta_{0}$ 在 $A$ 上是闭形式，从而是恰当形式。$k=1$ 的情况同理。

显然，$\mathbb{R}^{n}$ 自身是星状凸集，因此我们有推论：$\mathbb{R}^{n}$ 上的闭形式就是恰当形式。在数学中，我们有一个专门的术语来表示这种情况：

**定义 5.1.7** 同调平凡的（homologically trivial）

设 $A$ 是 $\mathbb{R}^{n}$ 上的开集，如果 $A$ 上的每个闭 $k$-形式都是 $A$ 上的恰当形式，那么我们就称 $A$ 在 $k$ 维上是**同调平凡的**。

因此，Poincare 引理的一个等价表述为：$\mathbb{R}^{n}$ 上的星状凸开集在所有维度上是同调平凡的。这一定义的名字来源将在下一节给出。

在本节的最后，我们将 Poincare 引理翻译为向量场的语言。根据形式与向量场的对应关系（定理 3.3.4），我们有如下结论：

**定理 5.1.8**

设 $A$ 是 $\mathbb{R}^{3}$ 上的星状凸开集，$F,G$ 是 $A$ 上的 $C^{\infty}$ 向量场，则有：

1. 如果 $\mathrm{curl}\ F=0$，则存在标量场 $f$ 使得 $F=\mathrm{grad}\ f$
2. 如果 $\mathrm{div}\ G=0$，则存在向量场 $H$ 使得 $G=\mathrm{curl}\ H$

这些是向量分析中势场理论的标准结果。

# Section 2: deRham 上同调群

我们已经证明 $\mathbb{R}^{n}$ 上的开集 $A$ 在所有维度上是同调平凡的，当且仅当 $A$ 是星状凸的。现在，我们考虑一些 $A$ 不是同调平凡的情况。最简单的这种情况出现在 $A$ 是穿孔 Euclidean 空间 $\mathbb{R}^{n}\setminus\{ 0 \}$ 的时候：在本节的最后，我们将构造一个 $A$ 上并非恰当形式的闭 $n-1$ 形式。现在我们对其做进一步的分析，给出一个闭形式何时为恰当形式的判据。

代数拓扑的思想启发我们，要处理上述问题，一种简单的方法是考虑 $A$ 上的特定代数结构（在本例中为向量空间）$H^{k}(A)$，称为 $A$ 上的 **deRham 上同调群**，使得 $A$ 上形式的性质都可以归结为 $H^{k}(A)$ 的代数性质。通过这种方法，我们就将一个拓扑问题转化为了一个（通常来说较易解决的）代数问题。

首先，我们来回顾一下线性代数中商空间的定义。

**定义 5.2.1** 商空间（quotient space）

设 $V$ 是一个向量空间，$W$ 是它的一个子空间。我们用 $V / W$ 来表示所有 $V$ 的具有以下形式的子集构成的集合：

$$
\begin{gather}
v+W=\{ v+w \mid w \in W \}
\end{gather}
$$

每个这样的子集称为 $V$ 的一个**陪集**（coset）。根据线性代数与等价关系的理论，$V / W$ 构成了 $V$ 的一个分割，即不同的陪集之间不相交，且所有陪集的并等于 $V$.

我们在 $V / W$ 上定义加法和数乘

$$
\begin{gather}
(v_{1}+W)+(v_{2}+W)=(v_{1}+v_{2})+W \\
c(v+W)=(cv)+W
\end{gather}
$$

可以使 $V / W$ 成为一个向量空间，称为 $V$ 关于 $W$ 的**商空间**。

**定义 5.2.2**

设 $V$ 和 $V'$ 是向量空间，$W$ 和 $W'$ 分别是 $V$ 和 $V'$ 的子空间。如果 $T\colon V\to V'$ 是一个线性映射，使得 $T[W]\subset W'$，则我们定义线性映射

$$
\begin{gather}
\widetilde{T}\colon V / W \to V' / W'
\end{gather}
$$

为 $\widetilde{T}(v+W)=T(v)+W'$，称为由 $T$ **诱导的**线性映射。

我们来证明它是良定的。假设 $v_{1}+W=v_{2}+W$，则 $v_{1}-v_{2}\in W$，从而 $T(v_{1}-v_{2})=T(v_{1})-T(v_{2})\in W'$，因此 $\widetilde{T}(v_{1}+W)=\widetilde{T}(v_{2}+W)$. 线性性的验证是平凡的。

接下来，我们来定义 deRham 上同调群。

**定义 5.2.3** deRham 上同调群（deRham cohomology group）

设 $A$ 是 $\mathbb{R}^{n}$ 上的开集，则 $A$ 上 $k$-形式的集合 $\Omega^{k}(A)$ 构成一个向量空间。$A$ 上的闭 $k$-形式集合 $C^{k}(A)$ 和恰当 $k$-形式集合 $E^{k}(A)$ 是它的子空间。由于每个恰当形式都是闭形式，故 $E^{k}(A)\subset C^{k}(A)$. 我们定义 $A$ 的 $k$ 维 **deRham 上同调群**为商空间

$$
\begin{gather}
H^{k}(A)=C^{k}(A) / E^{k}(A)
\end{gather}
$$

如果 $\omega$ 是 $A$ 上的闭 $k$-形式，我们将它的陪集 $\omega+E^{k}(A)$ 记作 $[\omega]$.

根据定义我们立即得到：$A$ 在 $k$ 维上是同调平凡的，当且仅当它的 $k$ 维 deRham 上同调群 $H^{k}(A)$ 为平凡空间 $\{ 0 \}$，这正是“同调平凡”一词的由来。

现设 $A,B$ 分别是 $\mathbb{R}^{n},\mathbb{R}^{m}$ 上的开集，$g\colon A\to B$ 是 $C^{\infty}$ 函数，则 $g$ 诱导了形式上的线性映射 $g^{*}\colon\Omega^{k}(B)\to\Omega^{k}(A)$. 由于 $g^{*}$ 与微分算子 $\mathrm{d}$ 交换，因此 $g^{*}$ 将闭形式映射到闭形式，将恰当形式映射到恰当形式，从而 $g^{*}$ 诱导了商空间上的线性映射

$$
\begin{gather}
g^{*}\colon H^{k}(B)\to H^{k}(A)
\end{gather}
$$

为了方便，这里我们仍然用 $g^{*}$ 而非 $\widetilde{g}^{*}$ 来表示这个映射。

于是，开集 $A$ 上闭形式与恰当形式的研究现在就简化为了 deRham 上同调群 $H^{k}(A)$ 的计算。对于后者，我们在本节介绍两种方法来进行计算，其一涉及**同伦等价**的概念，其二则是一个称为 Mayer-Vietoris 定理的一般定理的特例。两者均是代数拓扑中的标准工具。

**定理 5.2.4** 同伦等价定理（homotopy equivalence theorem）

设 $A,B$ 分别是 $\mathbb{R}^{n},\mathbb{R}^{m}$ 上的开集，$g\colon A\to B$ 和 $h\colon B\to A$ 是 $C^{\infty}$ 函数。如果 $g\circ h$ 微分同伦于 $B$ 上的恒等映射 $i_{B}$，并且 $h\circ g$ 微分同伦于 $A$ 上的恒等映射 $i_{A}$，则 $g^{*}$ 和 $h^{*}$ 是 $H^{k}(A)$ 和 $H^{k}(B)$ 之间的线性同构。

我们称定理中的 $g$ 和 $h$ 是（微分）**同伦等价的**。

**证明**

如果 $\eta$ 是 $A$ 上的闭 $k$-形式，那么根据定理 5.1.3 知

$$
\begin{gather}
(h\circ g)^{*}\eta-i_{A}^{*} \eta
\end{gather}
$$

是恰当形式。于是其诱导映射满足

$$
\begin{gather}
g^{*}(h^{*}([\eta]))=[\eta]
\end{gather}
$$

因此 $g^{*}\circ h^{*}$ 是 $H^{k}(A)$ 上的恒等映射。同理可得 $h^{*}\circ g^{*}$ 是 $H^{k}(B)$ 上的恒等映射，这就完成了证明。

为了证明另一个主要定理，我们需要一个技术性引理。

**引理 5.2.5**

设 $U,V$ 是 $\mathbb{R}^{n}$ 中的开集，令 $X=U\cup V$，并且 $A=U\cap V\neq \varnothing$. 则存在一个 $C^{\infty}$ 函数 $\phi\colon X\to[0,1]$ 使得在 $U\setminus A$ 的一个邻域上有 $\phi=0$，在 $V\setminus A$ 的一个邻域上有 $\phi=1$.

![](5-2.png)

**证明**

设 $\{ \phi_{i} \}$ 为 $X$ 上受开覆盖 $\{ U,V \}$ 控制的单位分解，令 $S_{i}=\mathrm{supp}(\phi_{i})$. 我们将 $\{ \phi_{i} \}$ 的指标集分成两个不相交的集合 $J,K$，其中 $i\in J$ 的 $\phi_{i}$ 满足 $S_{i}\subset U$；而 $i \in K$ 的 $\phi_{i}$ 满足 $S_{i}\subset V$. 然后我们令

$$
\begin{gather}
\phi(x)=\sum_{i \in K} \phi_{i}(x)
\end{gather}
$$

则 $\phi$ 是 $C^{\infty}$ 函数：因为每个 $x \in X$ 都有一个邻域使其仅和有限个 $S_{i}$ 相交，在其上 $\phi$ 等于有限个 $C^{\infty}$ 函数的和。

设 $x \in U\setminus A$，我们证明在 $x$ 的某个邻域上有 $\phi=0$. 首先，选择一个邻域 $W$ 使得它只和有限个 $S_{i}$ 相交。在这有限个 $S_{i}$ 中，取出那些 $i\in K$ 的集合，令 $D$ 为它们的并集。则 $D$ 是一个闭集，并且不包含点 $x$. 于是，集合 $W\setminus D$ 就是 $x$ 的一个开邻域，并且对于 $i \in K$，函数 $\phi_{i}$ 在 $W\setminus D$ 上消失，故在 $W\setminus D$ 上 $\phi=0$.

又由于

$$
\begin{gather}
1-\phi(x)=\sum_{i\in J} \phi_{i}(x)
\end{gather}
$$

根据对称性可知 $1-\phi(x)$ 在 $V\setminus A$ 的一个邻域上等于零，这就完成了证明。

**定理 5.2.6** Mayer-Vietoris 定理（特例）

设 $U,V$ 是 $\mathbb{R}^{n}$ 上的开集，且在任意维度上同调平凡。令 $X=U\cup V$，假设 $A=U\cap V\neq \varnothing$. 则 $H^{0}(X)$ 是平凡空间，并且对于 $k\geq 0$，$H^{k+1}(X)$ 线性同构于 $H^{k}(A)$.

**证明**

我们首先引入一些记号。如果 $B,C$ 是 $\mathbb{R}^{n}$ 中的开集，$B\subset C$，并且 $\eta$ 是 $C$ 上的 $k$-形式，那么我们用 $\eta|_{B}$ 来表示 $\eta$ 在 $B$ 上的限制，即 $\eta|_{B}=j^{*}\eta$，其中 $j\colon B\to C$ 是嵌入映射。由于 $j^{*}$ 与微分算子 $\mathrm{d}$ 交换，因此闭形式的限制仍是闭形式，恰当形式的限制仍是恰当形式。此外，如果 $A\subset B\subset C$ 都是开集，那么 $(\eta|_{B})|_{A}=\eta|_{A}$.

(1). 首先我们证明 $H^{0}(X)$ 是平凡的。令 $f$ 是 $X$ 上的闭 $0$-形式，则 $f|_{U}$ 和 $f|_{V}$ 分别是 $U$ 和 $V$ 上的闭形式。由于 $U,V$ 是同调平凡的，因此存在常数 $c_{1},c_{2}$ 使得 $f|_{U}=c_{1},f|_{V}=c_{2}$. 又由于 $U\cap V\neq \varnothing$，故 $c_{1}=c_{2}$，因此 $f$ 是常值函数，因而是恰当形式。

(2). 令 $\phi\colon X\to[0,1]$ 为一个 $C^{\infty}$ 函数使得 $\phi$ 在 $U\setminus A$ 的邻域 $U'$ 上消失，并且 $1-\phi$ 在 $V\setminus A$ 的邻域 $V'$ 上消失。对于 $k\geq 0$，我们定义线性映射

$$
\begin{gather}
\delta\colon \Omega^{k}(A)\to \Omega^{k+1}(X)
\end{gather}
$$

为

$$
\begin{gather}
\delta(\omega)=\begin{cases}
\mathrm{d} \phi \land\omega , & x \in A \\
0 , & x \in U'\cup V'
\end{cases}
\end{gather}
$$

由于在 $U'\cup V'$ 上 $\mathrm{d}\phi=0$，故 $\delta$ 是良定的。又由于 $A\cup U'\cup V'=X$，因此 $\delta$ 在 $X$ 上是 $C^{\infty}$ 连续的。我们计算

$$
\begin{align}
\mathrm{d} \delta(\omega)&= \begin{cases}
-\mathrm{d} \phi \land \mathrm{d} \omega,  & x \in A \\
0,  & x \in U'\cup V'
\end{cases} \\
&= -\delta(\mathrm{d} \omega)
\end{align}
$$

因此在相差一个符号下，$\delta$ 和 $\mathrm{d}$ 是交换的。故 $\delta$ 将闭形式映射为闭形式，将恰当形式映射为恰当形式，从而诱导了一个线性映射

$$
\begin{gather}
\widetilde{\delta}\colon H^{k}(A)\to H^{k+1}(X)
\end{gather}
$$

我们来证明 $\widetilde{\delta}$ 是一个线性同构。

(3). 首先我们证明 $\widetilde{\delta}$ 是单射。这就是说，如果 $\omega$ 是 $A$ 上的闭 $k$-形式使得 $\delta(\omega)$ 是恰当的，那么 $\omega$ 自身是恰当形式。

因此我们假设 $\delta(\omega)=\mathrm{d}\theta$ 对 $X$ 上的 $k$-形式 $\theta$ 成立。我们定义 $k$-形式 $\omega_{1}$ 和 $\omega_{2}$ 如下：

$$
\begin{gather}
\omega_{1}=\begin{cases}
\phi\omega, & x \in A \\
0, & x \in U'
\end{cases} \qquad \omega_{2}=\begin{cases}
(1-\phi)\omega, & x \in A \\
0,  & x \in V'
\end{cases}
\end{gather}
$$

则 $\omega_{1},\omega_{2}$ 是良定且光滑的。

![](5-3.png)

我们计算

$$
\begin{gather}
\mathrm{d} \omega_{1}=\begin{cases}
\mathrm{d} \phi \land\omega, & x \in A \\
0, & x \in U'
\end{cases}
\end{gather}
$$

因此 $\mathrm{d}\omega_{1}=\delta(\omega)|_{U}=\mathrm{d}\theta|_{U}$，从而 $\omega_{1}-\theta|_{U}$ 是 $U$ 上的闭 $k$-形式。类似的计算给出 $\omega_{2}+\theta|_{V}$ 是 $V$ 上的闭 $k$-形式。

由于 $U,V$ 是同调平凡的，因此存在 $U,V$ 上的 $k-1$ 形式 $\eta_{1}$ 和 $\eta_{2}$ 使得

$$
\begin{gather}
\omega_{1}-\theta|_{U}=\mathrm{d} \eta_{1}, \quad \omega_{2}+\theta|_{V}=\mathrm{d} \eta_{2}
\end{gather}
$$

将上式限制在 $A$ 上并求和，即得

$$
\begin{align}
\omega=\omega_{1}|_{A}-\theta|_{A}+\omega_{2}|_{A}+\theta|_{A}=\mathrm{d} (\eta_{1}|_{A}+\eta_{2}|_{A})
\end{align}
$$

从而 $\omega$ 是恰当的。$k=0$ 时的计算是类似的。

(4). 我们证明 $\widetilde{\delta}$ 是满射。这就是说，如果 $\eta$ 是 $X$ 上的闭 $k+1$ 形式，那么存在 $A$ 上的闭 $k$-形式 $\omega$ 使得 $\eta-\delta(\omega)$ 是恰当的。

给定 $\eta$，由于 $\eta|_{U}$ 和 $\eta|_{V}$ 是闭形式（从而恰当），故存在 $U,V$ 上的 $k$-形式 $\theta_{1},\theta_{2}$ 使得

$$
\begin{gather}
\eta|_{U}=\mathrm{d} \theta_{1}, \quad \eta|_{V}=\mathrm{d} \theta_{2}
\end{gather}
$$

令 $\omega$ 为 $A$ 上的 $k$-形式满足

$$
\begin{gather}
\omega=\theta_{1}|_{A}-\theta_{2}|_{A}
\end{gather}
$$

则 $\mathrm{d}\omega=\eta|_{A}-\eta|_{A}=0$，从而 $\omega$ 是闭的。我们定义 $X$ 上的 $k$-形式 $\theta$ 如下：

$$
\begin{gather}
\theta=\begin{cases}
(1-\phi)\theta_{1}+\phi\theta_{2}, & x \in A \\
\theta_{1},  & x \in U' \\
\theta_{2},  & x \in V'
\end{cases}
\end{gather}
$$

则 $\theta$ 是良定且光滑的。

![](5-4.png)

我们来证明 $\eta-\delta(\omega)=\mathrm{d}\theta$. 为此，我们在 $A,U',V'$ 上分别计算 $\mathrm{d}\theta$：

$$
\begin{align}
\mathrm{d} \theta|_{A} &= -\mathrm{d} \phi \land\theta_{1}|_{A}+(1-\phi) \mathrm{d} \theta_{1}|_{A}+\mathrm{d} \phi \land\theta_{2}|_{A}+\phi \mathrm{d} \theta_{2}|_{A} \\
&= (1-\phi)\eta|_{A}+\phi \eta|_{A}+\mathrm{d} \phi \land(\theta_{2}|_{A}-\theta_{1}|_{A}) \\
&= \eta|_{A} +\mathrm{d} \phi \land(-\omega) \\
&= \eta|_{A}-\delta(\omega)|_{A}
\end{align}
$$

限制在 $U',V'$ 上，我们有

$$
\begin{align}
\mathrm{d} \theta|_{U'}=\mathrm{d} \theta_{1}|_{U'}=\eta|_{U'}=\eta|_{U'}-\delta(\omega)|_{U'} \\
\mathrm{d} \theta|_{V'}=\mathrm{d} \theta_{2}|_{V'}=\eta|_{V'}=\eta|_{V'}-\delta(\omega)|_{V'}
\end{align}
$$

因为在 $U'\cup V'$ 上 $\delta(\omega)=0$. 从而我们有 $\mathrm{d}\theta=\eta-\delta(\omega)$，这就完成了证明。

现在，我们就用这两个定理来实际计算一个 deRham 上同调群。

**定理 5.2.7**

设 $n\geq 1$，则

$$
\begin{gather}
\mathrm{dim}\ H^{k}(\mathbb{R}^{n}\setminus \{ 0 \})=\begin{cases}
0 , & k\neq n-1 \\
1 , & k=n-1
\end{cases}
\end{gather}
$$

**证明**

(1). 我们对 $n=1$ 的情况进行证明。令 $A=\mathbb{R}\setminus\{ 0 \}$，它可以写成 $A=A_{0}\cup A_{1}$，其中 $A_{0}$ 是负实数构成的集合，$A_{1}$ 是正实数构成的集合。如果 $\omega$ 是 $A$ 上的正数阶闭形式，则 $\omega|_{A_{0}}$ 和 $\omega|_{A_{1}}$ 是闭形式。由于 $A_{0},A_{1}$ 都是星状凸开集，故存在 $k-1$ 形式 $\eta_{0},\eta_{1}$ 使得 $\omega|_{A_{i}}=\mathrm{d}\eta_{i}$. 定义

$$
\begin{gather}
\eta=\begin{cases}
\eta_{0}, & x \in A_{0} \\
\eta_{1}, & x \in A_{1}
\end{cases}
\end{gather}
$$

则 $\eta$ 是良定且光滑的，并且 $\omega=\mathrm{d}\eta$.

现在我们令 $f_{0}$ 是 $A$ 上的 $0$-形式，定义为

$$
\begin{gather}
f_{0}(x)=\begin{cases}
0, & x \in A_{0} \\
1, & x \in A_{1}
\end{cases}
\end{gather}
$$

则 $f_{0}$ 是闭形式，但不是恰当的。我们证明陪集 $[f_{0}]$ 构成了 $H^{0}(A)$ 上的一个基。给定 $A$ 上的闭 $0$-形式 $f$，由于 $f|_{A_{0}}$ 和 $f|_{A_{1}}$ 是恰当的，故存在常数 $c_{0},c_{1}$ 使得 $f|_{A_{0}}=c_{0},f|_{A_{1}}=c_{1}$，从而

$$
\begin{gather}
f(x)=(c_{1}-c_{0})f_{0}(x)+c_{0}
\end{gather}
$$

于是 $[f]=(c_{1}-c_{0})[f_{0}]$，即证。

(2). 如果 $B$ 是 $\mathbb{R}^{n}$ 中的开集，则 $B\times \mathbb{R}$ 在 $\mathbb{R}^{n+1}$ 中开。我们来证明

$$
\begin{gather}
\mathrm{dim}\ H^{k}(B)=\mathrm{dim}\ H^{k}(B\times \mathbb{R})
\end{gather}
$$

对任意 $k$ 成立。

我们使用同伦等价定理。定义 $g\colon B\to B\times \mathbb{R}$ 为 $g(x)=(x,0)$，并定义 $h\colon B\times \mathbb{R}\to B$ 为 $h(x,s)=x$，则 $h\circ g$ 等于 $B$ 上的恒等映射；另一方面，$g\circ h$ 微分同伦于 $B\times \mathbb{R}$ 上的恒等映射：考虑直线同伦

$$
\begin{gather}
H((x,s),t)=t(x,s)+(1-t)(x,0)=(x,ts)
\end{gather}
$$

因此 $H^{k}(B)$ 线性同构于 $H^{k}(B\times \mathbb{R})$.

(3). 设 $n\geq 1$，我们假设定理对 $n$ 成立，并证明 $n+1$ 的情况。

设 $U,V$ 是 $\mathbb{R}^{n+1}$ 上的开集，定义为

$$
\begin{gather}
U=\mathbb{R}^{n+1} \setminus \{ (0,\dots,0,t) \mid t\geq 0 \} \\
V=\mathbb{R}^{n+1} \setminus \{ (0,\dots,0,t) \mid t\leq 0 \}
\end{gather}
$$

换句话说，$U$ 包含除了 $0\times \mathbb{H}^{1}$ 上的所有 $\mathbb{R}^{n+1}$ 点，$V$ 包含除了 $0\times \mathbb{L}^{1}$ 上的所有 $\mathbb{R}^{n+1}$ 点。令 $A=U\cap V$，则 $A$ 包含了除 $0\times \mathbb{R}$ 上的所有点，即

$$
\begin{gather}
A=(\mathbb{R}^{n}\setminus \{ 0 \}) \times \mathbb{R}
\end{gather}
$$

![](5-5.png)

我们令 $X=U\cup V$，则 $X=\mathbb{R}^{n+1}\setminus\{ 0 \}$. 可以验证，集合 $U$ 关于点 $p=(0,\dots,0,-1)$ 是星状凸的，$V$ 关于点 $q=(0,\dots,0,1)$ 是星状凸的。根据 Mayer-Vietoris 定理，我们可知 $H^{0}(X)$ 是平凡的，且

$$
\begin{gather}
\mathrm{dim}\ H^{k+1}(X)=\mathrm{dim}\ H^{k}(A)
\end{gather}
$$

现在，步骤 (2) 告诉我们 $H^{k}(A)$ 同构于 $H^{k}(\mathbb{R}^{n}\setminus\{ 0 \})$，并且归纳假设告诉我们后者的维度是 $0$ 如果 $k\neq n-1$；维度是 $1$ 如果 $k=n-1$，即

$$
\begin{gather}
\mathrm{dim}\ H^{k+1}(\mathbb{R}^{n+1}\setminus \{ 0 \})=\begin{cases}
0, & k+1\neq n \\
1, & k+1=n
\end{cases}
\end{gather}
$$

这就完成了证明。

让我们用形式的语言重写这个定理。

**定理 5.2.8**

设 $n\geq 1$，令 $A=\mathbb{R}^{n}\setminus \{ 0 \}$，则：

1. 如果 $k\neq n-1$，则 $A$ 上的任意闭 $k$-形式都是恰当的。
2. 在 $A$ 上存在一个闭 $n-1$ 形式 $\eta_{0}$，它不是恰当的。如果 $\eta$ 是任意 $A$ 上的闭 $n-1$ 形式，则存在唯一的标量 $c$ 使得 $\eta-c\eta_{0}$ 是恰当的。

这一定理保证了 $A$ 上非恰当的闭 $n-1$ 形式的存在性，然而它并没有给出具体的构造。下面我们就来给出这样一个形式。

定义 $n-1$ 形式

$$
\begin{gather}
\eta_{0}=\sum_{i=1}^{n} (-1)^{i-1} f_{i} \mathrm{d} x_{1}\land\dots \land \mathrm{d} x_{i-1}\land \mathrm{d} x_{i+1}\land\dots \land \mathrm{d} x_{n}
\end{gather}
$$

其中 $f_{i}=\dfrac{x_{i}}{\lVert x \rVert^{n}}$. 通过直接计算，我们可得

$$
\begin{align}
\mathrm{d} \eta_{0} &= \sum_{i=1}^{n} \dfrac{ \partial f_{i} }{ \partial x_{i} }  \mathrm{d} x_{1}\land\dots \land \mathrm{d} x_{n} \\
&=\sum_{i=1}^{n} \dfrac{\lVert x \rVert ^{2}-nx_{i}^{2}}{\lVert x \rVert ^{n+2}} \mathrm{d} x_{1}\land\dots \land \mathrm{d} x_{n} \\
&= 0
\end{align}
$$

因此 $\eta_{0}$ 是闭的。然而，我们考虑积分

$$
\begin{gather}
\int_{S^{n-1}} \eta_{0}=\int_{S^{n-1}} \langle F,N \rangle \mathrm{d} V
\end{gather}
$$

在 $x \in S^{n-1}$ 处，球面 $S^{n-1}$ 上的外法向量与 $x$ 的方向相同，从而

$$
\begin{gather}
\langle F,N \rangle =\dfrac{1}{\lVert x \rVert ^{n}} \langle (x_{1},\dots,x_{n}),(x_{1},\dots,x_{n}) \rangle =1
\end{gather}
$$

因此

$$
\begin{gather}
\int_{S^{n-1}} \eta_{0}=V(S^{n-1}) \neq 0
\end{gather}
$$

这就表明 $\eta_{0}$ 不可能是恰当的：假设不然，则 $\eta_{0}=\mathrm{d}\theta$，由于 $S^{n-1}$ 是无边界流形，因此根据 Stokes 定理有

$$
\begin{gather}
\int_{S^{n-1}} \eta_{0}=\int_{S^{n-1}} \mathrm{d} \theta=0
\end{gather}
$$

这就完成了证明。

利用这个结果，我们给出 $\mathbb{R}^{n}\setminus \{ 0 \}$ 上的闭 $n-1$ 形式成为恰当形式的一个充要条件：

**定理 5.2.9**

设 $n>1$，$A=\mathbb{R}^{n}\setminus \{ 0 \}$，如果 $\eta$ 是 $A$ 上的闭 $n-1$ 形式，则 $\eta$ 是恰当形式当且仅当

$$
\begin{gather}
\int_{S^{n-1}} \eta=0
\end{gather}
$$

**证明**

如果 $\eta$ 是恰当形式，那么根据 Stokes 定理，上述积分等于零。反之，令 $\eta_{0}$ 为前面定义的 $n-1$ 形式，定理 5.2.8 表明存在唯一的标量 $c$ 使得 $\eta-c\eta_{0}$ 是恰当的，则

$$
\begin{gather}
\int_{S^{n-1}} (\eta-c\eta_{0})=0
\end{gather}
$$

由于 $\eta_{0}$ 在 $S^{n-1}$ 上的积分不为零，因此 $c=0$，从而 $\eta$ 是恰当的。这就完成了证明。