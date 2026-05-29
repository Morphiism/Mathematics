我们在上一章中看到了 $k$-形式如何将 $\mathbb{R}^{3}$ 中标量场和向量场的概念推广至 $\mathbb{R}^{n}$，以及微分算子 $\mathrm{d}$ 如何推广了向量场的运算 $\mathrm{grad},\mathrm{div}$ 和 $\mathrm{curl}$. 现在我们来定义 $k$-流形上微分流形的积分，它正是微积分中“第二类”曲线积分与曲面积分在 $\mathbb{R}^{n}$ 中的推广。

在本章中，我们仍然对标量场、向量场、流形和微分形式采用 $C^{\infty}$ 光滑的假设。

# Section 1: 参数化流形上形式的积分

在第一章，我们定义了流形上标量场关于体积的积分。类似地，我们按同样的过程来定义 $k$-流形上 $k$-形式的积分。我们首先考虑一个特例：

**定义 4.1.1**

设 $A$ 是 $\mathbb{R}^{k}$ 中的开集，$\eta$ 是 $A$ 上的 $k$-形式，则 $\eta$ 可以唯一地写成以下形式：

$$
\begin{gather}
\eta=f \mathrm{d} x_{1}\land\dots \land \mathrm{d} x_{k}
\end{gather}
$$

我们定义 $\eta$ 在 $A$ 上的**积分**为

$$
\begin{gather}
\int_{A} \eta=\int_{A} f
\end{gather}
$$

如果右边的积分存在。

上面的定义看似依赖于坐标系的选取：为了定义 $\int_{A}\eta$，我们用基本 $1$-形式 $\mathrm{d}x_{i}$ 来表示 $\eta$，而这些形式依赖于标准基 $e_{1},\dots,e_{k} \in \mathbb{R}^{k}$. 然而，我们可以用一种坐标无关的方法来表述这个定义。

**定义 4.1.2** 标架（frame），右手的（right-handed），定向（orientation）

设 $V$ 是一个 $n$ 维向量空间，$V$ 中的一个线性无关向量构成的 $n$-元组 $(v_{1},\dots,v_{n})$ 称为 $V$ 中的一个 $n$-**标架**。在 $\mathbb{R}^{n}$ 中，一个标架 $(x_{1},\dots,x_{n})$ 称为是**右手的**，如果

$$
\begin{gather}
\det [x_{1},\dots,x_{n}] > 0
\end{gather}
$$

否则，我们就称它是**左手的**。$\mathbb{R}^{n}$ 上所有右手标架构成的集合称为 $\mathbb{R}^{n}$ 的一个**定向**，它与左手标架构成的集合互称为**反定向**。更一般地，取线性同构 $T\colon \mathbb{R}^{n}\to V$，所有形如 $(Tx_{1},\dots,Tx_{n})$ 的标架构成了 $V$ 的一个定向，其中 $(x_{1},\dots,x_{n})$ 是右手的，它与左手标架形成的定向互称为反定向。

定义 4.1.1 的一种重述如下：如果 $(u_{1},\dots,u_{k})$ 是 $\mathbb{R}^{k}$ 中任意右手的规范正交标架，那么我们定义

$$
\begin{gather}
\int_{A} \eta=\int_{A} \eta(x)((x;u_{1}),\dots,(x;u_{k}))
\end{gather}
$$

这一定义是良定的，因为

$$
\begin{align}
\eta(x)((x;u_{1}),\dots,(x;u_{k})) &= f(x)\mathrm{d} x_{1}\land\dots \land \mathrm{d} x_{k} (x)((x;u_{1}),\dots,(x;u_{k})) \\
&= f(x) \det [u_{1},\dots,u_{k}] \\
&= f(x)
\end{align}
$$

从而 $\int_{A}\eta$ 的值与选取的坐标系无关，尽管它仍然与坐标系的定向有关。

现在我们定义参数化流形上 $k$-形式的积分。

**定义 4.1.3**

设 $A$ 是 $\mathbb{R}^{k}$ 中的开集，$\alpha\colon A\to \mathbb{R}^{n}$ 是 $C^{\infty}$ 函数，集合 $Y=\alpha[A]$ 以及函数 $\alpha$ 共同构成了参数化流形 $Y_{\alpha}$. 如果 $\omega$ 是定义在 $\mathbb{R}^{n}$ 中包含 $Y$ 的开集上的 $k$-形式，我们定义 $\omega$ 在 $Y_{\alpha}$ 上的**积分**为

$$
\begin{gather}
\int_{Y_{\alpha}} \omega=\int_{A} \alpha^{*}\omega
\end{gather}
$$

如果右边的积分存在。由于 $\alpha^{*}$ 和 $\int_{A}$ 都是线性的，故该积分也是线性的。

下面我们证明，这一积分在重参数化下，至多相差一个符号。

**定理 4.1.4**

设 $g\colon A\to B$ 是 $\mathbb{R}^{k}$ 中开集上的微分同胚，假设 $\det g'$ 在 $A$ 上不改变符号。令 $\beta\colon B\to \mathbb{R}^{n}$ 是 $C^{\infty}$ 函数，$Y=\beta[B]$，再令 $\alpha=\beta \circ g$，则 $Y=\alpha[A]$. 如果 $\omega$ 是定义在 $\mathbb{R}^{n}$ 中包含 $Y$ 的开集上的 $k$-形式，那么 $\omega$ 在 $Y_{\alpha}$ 上可积当且仅当 $\omega$ 在 $Y_{\beta}$ 上可积，此时有

$$
\begin{gather}
\int_{Y_{\alpha}}\omega= \mathrm{sgn}(\det g') \int_{Y_{\beta}}\omega
\end{gather}
$$

其中 $\mathrm{sgn}$ 是符号函数。

**证明**

令 $x$ 表示 $A$ 中的一般点，$y$ 表示 $B$ 中的一般点，我们想要证明

$$
\begin{gather}
\int_{A} \alpha^{*}\omega=\epsilon \int_{B} \beta^{*}\omega
\end{gather}
$$

其中 $\epsilon=\mathrm{sgn}(\det g')$. 如果我们设 $\eta=\beta^{*}\omega$，那么上述等式等价于

$$
\begin{gather}
\int_{A} g^{*}\eta=\epsilon \int_{B} \eta
\end{gather}
$$

我们将 $\eta$ 表示为 $\eta=f \mathrm{d}y_{1}\land\dots \land \mathrm{d}y_{k}$，则

$$
\begin{align}
g^{*}\eta &= (f\circ g) g^{*}(\mathrm{d} y_{1}\land\dots \land \mathrm{d} y_{k}) \\
&= (f\circ g) (\det g') \mathrm{d} x_{1}\land\dots \land \mathrm{d} x_{k}
\end{align}
$$

根据积分的变量替换公式，我们有

$$
\begin{gather}
\int_{A} (f\circ g) |\det g'|=\int_{B} f
\end{gather}
$$

因此

$$
\begin{gather}
\int_{A} (f\circ g) \det g'=\epsilon \int_{B} f
\end{gather}
$$

这就完成了证明。

我们指出：如果 $A$ 是一个连通集，那么“$\det g'$ 在 $A$ 上不改变符号”的假设是自动满足的，因为 $\det g'$ 在 $A$ 上是连续函数，因而具有介值性。如果 $\det g'$ 在 $A$ 上改变符号，那么存在一点 $x_{0}$ 使得 $\det g'(x_{0})=0$，这与 $g$ 的微分同胚性质矛盾。

在实际应用中，上面的积分定义是容易计算的。我们有如下公式：

**定理 4.1.5**

设 $A$ 是 $\mathbb{R}^{k}$ 中的开集，$\alpha\colon A\to \mathbb{R}^{n}$ 是 $C^{\infty}$ 函数，$Y=\alpha[A]$. 令 $x$ 表示 $A$ 中的一般点，$z$ 表示 $\mathbb{R}^{n}$ 中的一般点。如果

$$
\begin{gather}
\omega=f \mathrm{d} z_{I}
\end{gather}
$$

是定义在 $\mathbb{R}^{n}$ 中包含 $Y$ 的开集上的 $k$-形式，那么

$$
\begin{gather}
\int_{Y_{\alpha}} \omega= \int_{A} (f\circ\alpha) \det \dfrac{ \partial \alpha_{I} }{ \partial x } 
\end{gather}
$$

**证明**

应用定理 3.4.3，我们得到

$$
\begin{gather}
\alpha^{*}\omega=(f\circ\alpha) \det \dfrac{ \partial \alpha_{I} }{ \partial x } \mathrm{d} x_{1}\land\dots \land \mathrm{d} x_{k}
\end{gather}
$$

根据定义即证。

现在我们可以解释一元积分学中常见的 $\mathrm{d}x$ 符号了。如果 $\eta=f\mathrm{d}x$ 是定义在开区间 $(a,b)$ 上的 $1$-形式，那么根据定义有

$$
\begin{gather}
\int_{(a,b)} \eta=\int_{(a,b)} f
\end{gather}
$$

换句话说，我们有

$$
\begin{gather}
\int_{(a,b)} f\mathrm{d} x=\int_{a}^{b} f
\end{gather}
$$

其中，上式的左边是一个形式的积分，而右边是一个函数的积分，它们根据定义是相等的。于是，一旦学习了微分形式，在单变量微积分中出现的符号 $\mathrm{d}x$ 就具有了意义。

类似地，我们也可以解释定义微积分中定义曲线积分时用的符号。给定定义在开集 $A\subset \mathbb{R}^{3}$ 上的 $1$-形式 $P\mathrm{d}x+Q\mathrm{d}y+R\mathrm{d}z$，以及参数曲线 $\gamma\colon(a,b)\to A$，根据上面的定理我们有

$$
\begin{align}
&\int_{C_{\gamma}} P\mathrm{d} x+Q\mathrm{d} y+R\mathrm{d} z \\
&=\int_{(a,b)} \left( P(\gamma(t)) \dfrac{\mathrm{d} \gamma_{1}}{\mathrm{d} t}+Q(\gamma(t)) \dfrac{\mathrm{d} \gamma_{2}}{\mathrm{d} t}+R(\gamma(t)) \dfrac{\mathrm{d} \gamma_{3}}{\mathrm{d} t} \right) \mathrm{d} t
\end{align}
$$

这正是微积分中计算线积分 $\int_{C}P\mathrm{d}x+Q\mathrm{d}y+R\mathrm{d}z$ 所用的公式。

然而，要理解处理二重积分时出现的 $\mathrm{d}x\mathrm{d}y$ 符号是一件比较困难的事。如果 $f$ 是一个定义在 $A\subset \mathbb{R}^{2}$ 上的可积函数，那么我们通常将 $f$ 在 $A$ 上的积分记作

$$
\begin{gather}
\int_{A} f=\iint_{A} f(x,y) \mathrm{d} x\mathrm{d} y
\end{gather}
$$

此处的符号 $\mathrm{d}x\mathrm{d}y$ 不像单变量积分中的 $\mathrm{d}x$ 有其单独的含义。它的一种解释是，$\mathrm{d}x\mathrm{d}y$ 的顺序标识了累次积分的顺序。事实上，根据 Fubini 定理，如果 $A$ 是长方形 $[a,b]\times[c,d]$，那么我们有等式

$$
\begin{gather}
\int_{c}^{d}\left( \int_{a}^{b} f(x,y)\mathrm{d} x \right) \mathrm{d} y=\int_{A} f
\end{gather}
$$

另一种解释是，$\mathrm{d}x\mathrm{d}y$ 表示了 $2$-形式 $\mathrm{d}x\land \mathrm{d}y$，因为我们定义在微分形式之间的乘积运算只有楔积，于是根据定义我们有等式

$$
\begin{gather}
\int_{A} f\mathrm{d} x\land \mathrm{d} y=\int_{A} f
\end{gather}
$$

然而，当我们交换 $x$ 和 $y$ 的角色时，问题就出现了：如果按我们的“积分顺序”解释，我们有正确的等式

$$
\begin{gather}
\int_{a}^{b} \left( \int_{c}^{d} f(x,y)\mathrm{d} y \right) \mathrm{d} x=\int_{A} f
\end{gather}
$$

但按“微分形式假设”，我们却得到

$$
\begin{gather}
\int_{A} f \mathrm{d} y\land \mathrm{d} x \overset{!}{=} -\int_{A} f
\end{gather}
$$

因此，对于符号 $\mathrm{d}x\mathrm{d}y$，我们需要根据其上下文来判断它究竟属于哪一种解释。一般来说，对于标量函数的二重积分，我们用 $\mathrm{d}x\mathrm{d}y$ 来标识积分的顺序；而在曲面积分中，我们通常用 $\mathrm{d}x\mathrm{d}y$ 来表示 $2$-形式 $\mathrm{d}x\land \mathrm{d}y$，例如 $\iint_{S} P\mathrm{d}y\mathrm{d}z+Q\mathrm{d}x\mathrm{d}z+R\mathrm{d}x\mathrm{d}y$ 就表示 $2$-形式的积分

$$
\begin{gather}
\int_{S_{\alpha}} P\mathrm{d} y\land \mathrm{d} z+Q\mathrm{d} x\land \mathrm{d} z+R\mathrm{d} x\land \mathrm{d} y
\end{gather}
$$

# Section 2: 流形的定向

我们将以与定义标量函数在流形上的积分大致相同的方式，来定义流形 $M$ 上微分形式的积分。首先，我们考虑当形式 $\omega$ 的支撑集落在单个坐标卡 $\alpha\colon U\to V$ 中的情况，我们定义

$$
\begin{gather}
\int_{M} \omega=\int_{\mathrm{Int}(U)} \alpha^{*}\omega
\end{gather}
$$

然而，这一积分仅在相差一个符号下是重参数化不变的。因此，为了保证定义的良定性，我们需要 $M$ 上的一个额外条件，称为**可定向性**。本节我们来讨论这一性质。

**定义 4.2.1** 保定向的（orientation-preserving），反定向的（orientation-reversing）

设 $g\colon A\to B$ 是 $\mathbb{R}^{k}$ 上开集之间的微分同胚，我们说 $g$ 在 $A$ 上是**保定向的**，如果在 $A$ 上有 $\det g'>0$；否则就称 $g$ 在 $A$ 上是**反定向的**。

**定义 4.2.2** 正向重叠（overlap positively），可定向的（orientable）

设 $M$ 是 $\mathbb{R}^{n}$ 上的 $k$-流形，给定坐标卡 $\alpha_{i}\colon U_{i}\to V_{i}\ (i=0,1)$，我们称它们**重叠**，如果 $V_{0}\cap V_{1}\neq \varnothing$. 我们称它们**正向重叠**，如果其转移函数 $\alpha_{1}^{-1}\circ\alpha_{0}$ 是保定向的。如果 $M$ 可以被一族相互之间正向重叠（如果有重叠）的坐标卡覆盖，则称 $M$ 是**可定向的**，否则就称 $M$ 是**不可定向的**。

**定义 4.2.3** 定向流形（oriented manifold）

设 $M$ 是 $\mathbb{R}^{n}$ 上的可定向 $k$-流形，给定覆盖 $M$ 的一族相互之间正向重叠的坐标卡，我们将这个集合与 $M$ 上所有与这些坐标卡正向重叠的其他坐标卡合并起来，这一扩展集合中的坐标卡之间也是正向重叠的，我们称其为 $M$ 的一个**定向**。一个流形 $M$ 与其上的一个定向共同构成了一个**定向流形**。

上面的定义对 $0$-流形不适用，因为那只是一些离散点的集合。我们将在之后讨论这种情况下的“定向”意味着什么。

如果 $V$ 是一个 $k$ 维向量空间，那么 $V$ 也是一个 $k$-流形。于是，我们关于 $V$ 的定向有两种不同的定义：4.1.2 与 4.2.3. 这两种定义之间的联系是容易建立的：给定 $V$ 的一个 4.1.2 意义下的定向，我们构造 4.2.3 意义下的一个定向如下：对任意属于给定的定向的标架 $(v_{1},\dots,v_{k})$，定义为 $\alpha(e_{i})=v_{i}$ 的线性同构 $\alpha\colon \mathbb{R}^{k}\to V$ 是 $V$ 上的一个坐标卡，两个这样的坐标卡是正向重叠的，于是所有这些坐标卡构成了 $V$ 上 4.2.3 意义下的定向。

在特定的维度下，定向的概念有一个简单的几何解释。这种情况发生在 $1,n-1$ 以及 $n$ 维。在 $k=1$ 的情况下，我们可以使用切向量场来描述一个定向，如下所示：

**定义 4.2.4** 单位切向量场（unit tangent field）

设 $M$ 是 $\mathbb{R}^{n}$ 上的定向 $1$-流形，我们定义 $M$ 上的切向量场 $T$ 如下：给定 $p \in M$，选取 $p$ 处属于给定定向的坐标卡 $\alpha\colon U\to V$，定义

$$
\begin{gather}
T(p)=\left( p; \dfrac{\alpha'(t_{0})}{\lVert \alpha'(t_{0}) \rVert } \right)
\end{gather}
$$

其中 $t_{0} \in U$ 满足 $\alpha(t_{0})=p$. 则 $T$ 称为对应于 $M$ 的定向的**单位切向量场**。

我们来证明 $T$ 是良定的。令 $\beta$ 是另一个属于给定定向的坐标卡，令 $p=\beta(t_{1})$ 且 $\alpha=\beta \circ g$，则 $g$ 是从 $t_{0}$ 的邻域到 $t_{1}$ 的邻域的一个微分同胚，并且

$$
\begin{align}
\alpha'(t_{0})=(\beta \circ g)'(t_{0})=\beta'(t_{1}) g'(t_{0})
\end{align}
$$

由于 $M$ 是 $1$-流形，故 $g'(t_{0})$ 是一个实数，又由于 $g$ 是保定向的，故 $g'(t_{0})>0$，从而

$$
\begin{gather}
\dfrac{\alpha'(t_{0})}{\lVert \alpha'(t_{0}) \rVert }=\dfrac{\beta'(t_{1})}{\lVert \beta'(t_{1}) \rVert }
\end{gather}
$$

此外，$T$ 是一个 $C^{\infty}$ 向量场，因为 $t_{0}=\alpha^{-1}(p)$ 关于 $p$ 是光滑的，且 $\alpha'$ 关于 $t$ 也是光滑的。

下面我们看一个例子。

给定一个定向 $1$-流形 $M$，以及其对应的单位切向量场 $T$，我们通常在曲线 $M$ 上画上方向来表示切向量场 $T$ 的方向，如图所示：

![](4-1.png)

因此，一个定向 $1$-流形通常被称为一个“有向曲线”。

然而，当 $M$ 的边界不为空时出现了一个问题。

![](4-2.png)

如图，$\partial M$ 包含两点 $p,q$，如果 $\alpha\colon U\to V$ 是 $p$ 处的坐标卡，则 $U$ 在 $\mathbb{H}^{1}$ 中开，这表明 $p$ 处的单位切向量 $T(p)$ 必须从 $p$ 指向 $M$ 的内部；同理，$T(q)$ 也从 $q$ 指向 $M$ 的内部。然而，对于图中的流形，不可能定义一个连续的切向量场 $T$ 使得 $T(p)$ 和 $T(q)$ 都指向 $M$ 的内部，因此 $M$ 似乎是不可定向的。显然，这是一种反常现象。

为了解决这一问题，我们采用如下约定：

**约定**

对于 $1$-流形 $M$，我们允许 $M$ 上坐标卡的定义域是 $\mathbb{R}^{1},\mathbb{H}^{1}$ 或**下半平面** $\mathbb{L}^{1}=\{ x \in \mathbb{R}^{1} \mid x\leq 0 \}$ 中的开集。

在上述假设下，我们就可以用相互之间正向重叠的坐标卡来覆盖上面的流形，如图所示：

![](4-3.png)

事实上，在这一约定下，每个 $1$-流形都是可定向的。上面的例子提供了一种证明的思路。

下面，我们考虑 $\mathbb{R}^{n}$ 中的 $n-1$ 流形。在这种情况下，我们可以用 $M$ 上的单位法向量场来表示 $M$ 的定向。

**定义 4.2.5** 单位法向量场（unit normal field）

设 $M$ 是 $\mathbb{R}^{n}$ 中的可定向 $n-1$ 流形，如果 $p \in M$，令 $(p;n) \in \mathcal{T}_{p}(\mathbb{R}^{n})$ 为一个正交于 $n-1$ 维向量空间 $\mathcal{T}_{p}(M)$ 的单位向量，则 $n$ 在相差一个符号下是唯一确定的。给定 $M$ 的一个定向，取 $p$ 处属于该定向的坐标卡 $\alpha\colon U\to V$，令 $\alpha(x)=p$，则矩阵 $J_{\alpha}(x)$ 的列给出了 $\mathcal{T}_{p}(M)$ 的一个基

$$
\begin{gather}
\left( p;\dfrac{ \partial \alpha }{ \partial x_{1} }  \right), \dots, \left( p;\dfrac{ \partial \alpha }{ \partial x_{n-1} }  \right)
\end{gather}
$$

我们按如下方法确定 $n$ 的符号：我们要求标架

$$
\begin{gather}
\left( n,\dfrac{ \partial \alpha }{ \partial x_{1} } ,\dots,\dfrac{ \partial \alpha }{ \partial x_{n-1} }  \right)
\end{gather}
$$

是右手的，即 $\det [n, J_{\alpha}(x)]>0$. 向量场 $N(p)=(p;n(p))$ 称为对应于 $M$ 的定向的**单位法向量场**。

现在我们可以给出一个不可定向流形的例子。如下图所示的 $2$-流形上不存在连续的单位法向量场。该流形被称为 **Mobius 带**，它是将一条纸带扭转一圈后首尾连接得到的。

![](4-4.png)

最后，我们来考虑 $\mathbb{R}^{n}$ 上的 $n$-流形。在这种情况下，不仅 $M$ 是可定向的，而且事实上它还有一种“自然的”定向。

**定义 4.2.6** 自然定向（natural orientation）

设 $M$ 是 $\mathbb{R}^{n}$ 上的 $n$-流形，如果 $\alpha\colon U\to V$ 是 $M$ 上的坐标卡，那么 $J_{\alpha}$ 是一个 $n\times n$ 矩阵。我们定义 $M$ 的**自然定向**包含所有满足 $\det \alpha'>0$ 的坐标卡 $\alpha$. 显然，这些坐标卡相互之间均是正向重叠的。

我们需要证明自然定向的确能够覆盖 $M$. 给定 $p \in M$，令 $\alpha\colon U\to V$ 是 $p$ 处的坐标卡。由于 $U$ 在 $\mathbb{R}^{n}$ 或 $\mathbb{H}^{n}$ 中开，通过取 $U$ 的子集，我们可以假设 $U$ 或者是一个 $\varepsilon$-开球，或者是一个 $\varepsilon$-开球与 $\mathbb{H}^{n}$ 的交集。在任意情况下，$U$ 都是连通的，因此 $\det\alpha'$ 在 $U$ 上不改变符号。如果在 $U$ 上 $\det\alpha'>0$，那么 $\alpha$ 就是我们所求的 $p$ 处的坐标卡；反之，则 $\alpha \circ r$ 是我们所求的坐标卡，其中 $r\colon \mathbb{R}^{n}\to \mathbb{R}^{n}$ 是反射变换

$$
\begin{gather}
r(x_{1},\dots,x_{n})=(-x_{1},x_{2},\dots,x_{n})
\end{gather}
$$

对于 $\mathbb{R}^{k}$ 上的反射变换 $r$，它是它自身的逆元。此外，当 $k>1$ 时，它将 $\mathbb{H}^{k}$ 映射到 $\mathbb{H}^{k}$，而对于 $k=1$，它将 $\mathbb{H}^{1}$ 映射到 $\mathbb{L}^{1}$.

**定义 4.2.7** 反定向（reverse/opposite orientation）

设 $M$ 是 $\mathbb{R}^{n}$ 上的一个定向 $k$-流形，如果 $\alpha_{i}\colon U_{i}\to V_{i}$ 是 $M$ 上属于给定定向的坐标卡，定义坐标卡 $\beta_{i}$ 为

$$
\begin{gather}
\beta_{i}=\alpha_{i}\circ r\colon r[U_{i}] \to V_{i}
\end{gather}
$$

则 $\beta_{i}$ 与 $\alpha_{i}$ 负向重叠，从而不属于给定定向。不过，各 $\beta_{i}$ 之间正向重叠，因此它们构成了 $M$ 的另一个定向，称为给定定向的**反定向**。

这表明，每个可定向的 $k$-流形都至少有两个定向：给定定向以及它的反定向。而对于连通的流形，我们有进一步的结论：

**定理 4.2.8**

如果 $M$ 是 $\mathbb{R}^{n}$ 中连通的可定向 $k$-流形，那么 $M$ 只有两个定向。

**证明**

取 $M$ 的一个定向 $\{ \alpha_{i} \}$，令 $\{ \beta_{j} \}$ 是 $M$ 的任意一个定向。给定 $x \in M$，取 $x$ 处的坐标卡 $\alpha_{i},\beta_{j}$，并定义 $\lambda(x)=1$ 如果 $\alpha_{i}$ 和 $\beta_{j}$ 正向重叠，$\lambda(x)=-1$ 如果 $\alpha_{i}$ 和 $\beta_{j}$ 反向重叠。

(1). 首先我们证明 $\lambda$ 是良定的，并且与 $\alpha_{i},\beta_{j}$ 的选取无关。我们记 $\alpha_{0}=\alpha_{i}$，$\beta_{0}=\beta_{j}$，假设 $\alpha_{1},\beta_{1}$ 是不同于 $\alpha_{0},\beta_{0}$ 的坐标卡，根据定向的定义，$\alpha_{0}$ 与 $\alpha_{1}$、$\beta_{0}$ 与 $\beta_{1}$ 是正向重叠的，因此，$\alpha_{1},\beta_{1}$ 正向重叠当且仅当 $\alpha_{0},\beta_{0}$ 正向重叠，即证。

(2). 我们证明 $\lambda$ 是连续的。事实上，对任意 $x \in M$ 我们有

$$
\begin{gather}
\lambda(x)= \mathrm{sgn}(\det J_{\beta_{j}^{-1}\circ\alpha_{i}}(x))
\end{gather}
$$

由于 $\alpha_{i},\beta_{j}$ 重叠，故存在 $x$ 的一个 $\varepsilon$-开球邻域包含于 $\alpha_{i},\beta_{j}$ 的值域中，在该邻域中，根据步骤 (1)，我们可以选取 $\alpha_{i},\beta_{j}$ 作为其上点的坐标卡，因此在该邻域上有 $\lambda=\mathrm{sgn}\circ \det J_{\beta_{j}^{-1}\circ\alpha_{i}}$ 为常值函数，从而 $\lambda$ 在 $x$ 处连续。

(3). 我们证明 $\lambda$ 实际上是一个常值函数。我们用反证法。假设不然，则 $\lambda^{-1}(1)$ 和 $\lambda^{-1}(-1)$ 是 $M$ 上的开集（根据步骤 (2)），不相交，并且其并集为 $M$，但这与 $M$ 的连通性矛盾。

(4). 最后，我们来证明 $M$ 只有两个定向：当 $\lambda=1$ 时 $\{ \beta_{j} \}$ 与 $\{ \alpha_{i} \}$ 是同一定向，当 $\lambda=-1$ 时 $\{ \beta_{j} \}$ 是 $\{ \alpha_{i} \}$ 的反定向。

如果 $\lambda=1$，那么 $\{ \beta_{j} \}$ 与 $\{ \alpha_{i} \}$ 中的坐标卡相互之间均正向重叠，又因为 $\{ \alpha_{i} \}$ 和 $\{ \beta_{j} \}$ 自身也是定向，故 $\{ \alpha_{i} \}\cup \{ \beta_{j} \}$ 中的坐标卡相互之间正向重叠，从而它构成了 $M$ 的一个定向，它与定向 $\{ \alpha_{i} \}$ 是同一定向。

如果 $\lambda=-1$，那么各 $\beta_{j}$ 与 $\alpha_{i}$ 是反向重叠的，从而 $\beta_{j}$ 与 $\alpha_{i}\circ r$ 正向重叠，于是 $\{ \beta_{j} \}\cup \{ \alpha_{i}\circ r \}$ 中的坐标卡相互正向重叠，这构成了 $M$ 的一个定向，它与定向 $\{ \alpha_{i} \}$ 的反定向是同一定向。这就完成了证明。

对于非连通的流形，它的定向多于两个。例如，下图所示的 $1$-流形含有四个定向。

![](4-5.png)

我们指出：如果 $M$ 是一个定向 $1$-流形，其对应的单位切向量场是 $T$，那么将 $M$ 的定向反转的结果就是将 $T$ 替换为 $-T$. 这是因为如果 $\alpha\colon U\to V$ 是属于 $M$ 的定向的坐标卡，那么 $\alpha \circ r$ 属于 $M$ 的反定向。又由于 $(\alpha \circ r)(t)=\alpha(-t)$，因此 $\dfrac{\mathrm{d}(\alpha \circ r)}{\mathrm{d}t}=-\dfrac{\mathrm{d}\alpha}{\mathrm{d}t}$.

类似地，如果 $M$ 是一个定向 $n-1$ 流形，其单位法向量场是 $N$，那么反转 $M$ 的定向的结果就是将 $N$ 替换为 $-N$. 因为如果 $\alpha\colon U\to V$ 是属于 $M$ 的定向的坐标卡，那么 $\alpha \circ r$ 属于其反定向。我们有

$$
\begin{gather}
\dfrac{\mathrm{d} (\alpha \circ r)}{\mathrm{d} x_{1}}=-\dfrac{\mathrm{d} \alpha}{\mathrm{d} x_{1}}, \quad \dfrac{\mathrm{d} (\alpha \circ r)}{\mathrm{d} x_{i}}=\dfrac{\mathrm{d} \alpha}{\mathrm{d} x_{i}}\ (i>1)
\end{gather}
$$

此外，两个标架

$$
\begin{gather}
\left( n,\dfrac{ \partial \alpha }{ \partial x_{1} } ,\dots,\dfrac{ \partial \alpha }{ \partial x_{n-1} }  \right),\quad \left( -n,-\dfrac{ \partial \alpha }{ \partial x_{1} } , \dfrac{ \partial \alpha }{ \partial x_{2} }  ,\dots,\dfrac{ \partial \alpha }{ \partial x_{n-1} }  \right)
\end{gather}
$$

的定向是相同的，因此，如果 $n$ 属于坐标卡 $\alpha$，那么 $-n$ 属于坐标卡 $\alpha \circ r$.

在 Stokes 定理中，我们将建立 $M$ 上的微分形式积分与 $\partial M$ 上微分形式积分之间的联系，因此我们还需要研究 $\partial M$ 上的定向如何随 $M$ 的定向变化。事实上，相应于 $M$ 的定向，$\partial M$ 上存在一个“自然”的诱导定向。

**定理 4.2.9**

设 $k>1$，如果 $M$ 是一个有非空边界的可定向 $k$-流形，那么 $\partial M$ 是可定向的。

**证明**

设 $p \in \partial M$，令 $\alpha\colon U\to V$ 是 $p$ 处的坐标卡，则存在 $\partial M$ 上的坐标卡 $\alpha_{0}$ 可以通过对 $\alpha$ 进行限制得到（见第一章）。具体来说，令 $b\colon \mathbb{R}^{k-1}\to \mathbb{R}^{k}$ 定义为

$$
\begin{gather}
b(x_{1},\dots,x_{k-1})=(x_{1},\dots,x_{k-1},0)
\end{gather}
$$

则 $\alpha_{0}=\alpha \circ b$.

我们证明如果 $\alpha,\beta$ 是 $p$ 处正向重叠的坐标卡，那么它们的限制 $\alpha_{0},\beta_{0}$ 也是正向重叠的。令 $g\colon W_{0}\to W_{1}$ 为转移函数 $g=\beta^{-1}\circ\alpha$，其中 $W_{0},W_{1}$ 在 $\mathbb{H}^{k}$ 中开，则 $\det g'>0$.

现在我们设 $x \in \partial \mathbb{H}^{k}$，则 $J_{g}$ 的最后一行为

$$
\begin{gather}
J_{g_{k}}=\left[ 0,\dots,0,\dfrac{ \partial g_{k} }{ \partial x_{k} }  \right]
\end{gather}
$$

其中 $\dfrac{ \partial g_{k} }{ \partial x_{k} }\geq 0$. 这是因为在 $x$ 处，如果我们给变量 $x_{1},\dots,x_{n-1}$ 一个增量，函数 $g_{k}$ 没有变化，而当我们给 $x_{k}$ 一个正增量，函数 $g_{k}$ 的值将会增大，如图所示：

![](4-6.png)

因此 $\dfrac{ \partial g_{k} }{ \partial x_{j} }=0$ 对 $j<k$ 成立，而 $\dfrac{ \partial g_{k} }{ \partial x_{k} }\geq 0$. 由于 $\det J_{g}>0$，因此 $\dfrac{ \partial g_{k} }{ \partial x_{k} }>0$，将 $\det J_{g}$ 按最后一行做代数余子式展开，我们就有

$$
\begin{gather}
\det \dfrac{ \partial (g_{1},\dots,g_{k-1}) }{ \partial (x_{1},\dots,x_{k-1}) } > 0
\end{gather}
$$

但该矩阵正是转移函数 $\beta_{0}^{-1}\circ\alpha_{0}$ 的 Jacobian 矩阵，换句话说，$\alpha_{0}$ 和 $\beta_{0}$ 正向重叠。这就完成了证明。

上述定理表明，通过取 $M$ 的定向中坐标卡的限制，我们可以得到 $\partial M$ 的一个定向。然而，这一定向通常不是我们想要的（例如在 $\mathbb{R}^{3}$ 中，我们通常要求一个闭曲面的单位法向量场指向外部），因此，我们给出以下定义：

**定义 4.2.10** 诱导定向（induced orientation）

设 $M$ 是一个具有非空边界的可定向 $k$-流形，给定 $M$ 的一个定向，其对应的 $\partial M$ 上的**诱导定向**定义如下：如果 $k$ 是偶数，那么该定向是通过将属于 $M$ 的定向的坐标卡进行限制得到的；如果 $k$ 是奇数，那么该定向是按上述方法得到的定向的反定向。

如果 $M$ 是 $\mathbb{R}^{3}$ 中的 $3$-流形，具有自然定向，那么我们对 $\partial M$ 上的诱导定向能说些什么呢？按我们在微积分和物理学中学到的，$\partial M$ 上的单位法向量场应当指向 $M$ 的外部，事实也确实如此。这里我们首先建立一些直觉，一个严格的证明将在之后给出。

令 $\alpha\colon U\to V$ 是 $p \in \partial M$ 处属于自然定向的坐标卡，则函数

$$
\begin{gather}
(\alpha \circ b)(x)=(x_{1},x_{2},0)
\end{gather}
$$

是 $p$ 处的限制坐标卡。由于 $k=3$ 为奇数，故 $\partial M$ 上的诱导定向是限制坐标卡构成的定向的反定向，从而 $\partial M$ 上的单位法向量场 $N(p)=(p;n)$ 满足条件：标架 $\left( -n,\dfrac{ \partial \alpha }{ \partial x_{1} },\dfrac{ \partial \alpha }{ \partial x_{2} } \right)$ 是右手的。

另一方面，由于 $\det\alpha'>0$，因此标架 $\left( \dfrac{ \partial \alpha }{ \partial x_{3} },\dfrac{ \partial \alpha }{ \partial x_{1} },\dfrac{ \partial \alpha }{ \partial x_{2} } \right)$ 是右手的，因此 $-n$ 与 $\dfrac{ \partial \alpha }{ \partial x_{3} }$ 指向 $p$ 处切平面的同一侧。由于 $\dfrac{ \partial \alpha }{ \partial x_{3} }$ 指向 $M$ 的内部，因而 $n$ 指向 $M$ 的外部，如图所示。

![](4-7.png)

再设 $M$ 是 $\mathbb{R}^{3}$ 上的 $2$-流形，如果 $M$ 是定向的，我们给予 $\partial M$ 诱导定向。令 $N$ 为对应于 $M$ 的定向的单位法向量场，并令 $T$ 为对应于 $\partial M$ 的诱导定向的单位切向量场。那么，$N$ 和 $T$ 之间的关系是什么？

我们断言：给定 $N$ 和 $T$，对任意 $p \in \partial M$，我们令 $W(p)$ 为一个单位向量，正交于 $N(p)$ 和 $T(p)$，并且其方向使得标架 $(N(p),T(p),W(p))$ 是右手的，则 $W(p)$ 与 $M$ 相切，并且从 $\partial M$ 指向 $M$ 的内部。

这一断言事实上是微积分中 Stokes 定理“右手法则”的精确表述：如果你站在 $\partial M$ 上，头部朝着 $N$ 所指向的方向，并沿着 $T$ 的方向绕着 $\partial M$ 行走，流形 $M$ 在你的左侧，那么 $T$ 所指的方向就是曲线 $\partial M$ 的方向，如图所示：

![](4-8.png)

为证明这个断言，令 $\alpha\colon U\to V$ 是 $p \in \partial M$ 处属于 $M$ 的定向的坐标卡，则坐标卡 $\alpha \circ b$ 属于 $\partial M$ 的诱导定向。向量 $\dfrac{ \partial \alpha }{ \partial x_{1} }$ 是参数曲线 $\alpha \circ b$ 的速度向量，因此根据定义它和单位切向量 $T$ 具有同一方向。

另一方面，向量 $\dfrac{ \partial \alpha }{ \partial x_{2} }$ 是这样一条参数曲线的速度向量：它以 $p \in \partial M$ 为起点，当 $t$ 增大时，曲线从 $p$ 点进入 $M$ 的内部。因此，根据定义，$\dfrac{ \partial \alpha }{ \partial x_{2} }$ 从 $p$ 指向 $M$ 的内部。虽然 $\dfrac{ \partial \alpha }{ \partial x_{2} }$ 不一定与 $\dfrac{ \partial \alpha }{ \partial x_{1} }$ 正交，但我们可以选取标量 $\lambda$ 使得 $w=\dfrac{ \partial \alpha }{ \partial x_{2} }+\lambda \dfrac{ \partial \alpha }{ \partial x_{1} }$ 正交于 $\dfrac{ \partial \alpha }{ \partial x_{1} }$，从而正交于 $T$. 则 $w$ 同样从 $p$ 指向 $M$ 的内部，我们令 $W(p)=\left( p; \dfrac{w}{\lVert w \rVert} \right)$.

最后，向量 $N(p)=(p;n)$ 根据定义，是使得标架 $\left( n,\dfrac{ \partial \alpha }{ \partial x_{1} },\dfrac{ \partial \alpha }{ \partial x_{2} } \right)$ 为右手系的单位法向量。由于

$$
\begin{gather}
\det \left[ n, \dfrac{ \partial \alpha }{ \partial x_{1} } , \dfrac{ \partial \alpha }{ \partial x_{2} }  \right]=\det \left[ n, \dfrac{ \partial \alpha }{ \partial x_{1} } , w \right]
\end{gather}
$$

这就表明标架 $(N,T,W)$ 是右手的，即证。

# Section 3: 定向流形上形式的积分

现在我们可以定义定向 $k$-流形上 $k$-形式的积分了，这一过程与第一章中定义流形上标量函数的积分非常相似，因此这里我们将省略一部分技术细节。

我们首先考虑 $\omega$ 的支撑集可被单个坐标卡覆盖的情况。

**定义 4.3.1**

设 $M$ 是 $\mathbb{R}^{n}$ 中的一个紧致定向 $k$-流形，$\omega$ 是一个定义在 $\mathbb{R}^{n}$ 中包含 $M$ 的开集上的 $k$-形式，令 $C=M\cap \mathrm{supp}(\omega)$，则 $C$ 是紧致的。假设存在属于 $M$ 的定向的坐标卡 $\alpha\colon U\to V$ 使得 $C\subset V$，通过取 $U$ 的开子集，我们可以假设 $U$ 是有界的。我们定义 $\omega$ 在 $M$ 上的**积分**为

$$
\begin{gather}
\int_{M} \omega=\int_{\mathrm{Int}(U)} \alpha^{*}\omega
\end{gather}
$$

其中 $\mathrm{Int}(U)=U$ 如果 $U$ 在 $\mathbb{R}^{k}$ 中开；$\mathrm{Int}(U)=U\cap \mathbb{H}_{+}^{k}$ 如果 $U$ 在 $\mathbb{H}^{k}$ 中开而不在 $\mathbb{R}^{k}$ 中开。

首先我们指出上述定义中积分的存在性。由于 $\alpha$ 可以扩张为定义在 $\mathbb{R}^{k}$ 中的开集 $U'$ 上的 $C^{\infty}$ 函数，故 $\alpha^{*}\omega$ 可以扩张为一个定义在 $U'$ 上的 $C^{\infty}$ 形式。这一形式可以表示为 $h\mathrm{d}x_{1}\land\dots \land \mathrm{d}x_{k}$，从而根据定义有

$$
\begin{gather}
\int_{\mathrm{Int}(U)}\alpha^{*}\omega=\int_{\mathrm{Int}(U)} h
\end{gather}
$$

函数 $h$ 是连续的，并且在紧致集 $\alpha^{-1}[C]$ 外消失，因此 $h$ 在 $U$ 上有界，从而可积。

其次，我们指出积分 $\int_{M}\omega$ 是良定的，与坐标卡的选取无关（只要它们是属于同一定向的）。这一结论的证明与引理 1.6.2 类似，这里我们使用额外的条件，即两个坐标卡是正向重叠的，从而定理 4.1.4 中的符号取 $+1$.

再次，我们指出，上述积分是线性的。具体来说，如果 $\omega$ 和 $\eta$ 的支撑集的交集可以被单个坐标卡 $\alpha\colon U\to V$ 覆盖，则

$$
\begin{gather}
\int_{M} (a\omega+b \eta)=a\int_{M}\omega+b\int_{M} \eta
\end{gather}
$$

这是因为 $\alpha^{*}$ 和 $\int_{\mathrm{Int}(U)}$ 都是线性的。

最后，如果我们用 $-M$ 来表示具有反定向的流形 $M$，则

$$
\begin{gather}
\int_{-M} \omega=-\int_{M} \omega
\end{gather}
$$

这一结果由定理 4.1.4 给出，因为 $\alpha$ 与 $\alpha \circ r$ 负向重叠，从而定理中的符号取 $-1$.

下面，为了定义一般的积分 $\int_{M}\omega$，我们使用单位分解。

**定义 4.3.2**

设 $M$ 是 $\mathbb{R}^{n}$ 中的一个紧致定向 $k$-流形，$\omega$ 是一个定义在 $\mathbb{R}^{n}$ 中包含 $M$ 的开集上的 $k$-形式。用属于 $M$ 的定向的坐标卡覆盖 $M$，并取 $M$ 上的单位分解 $\phi_{1},\dots,\phi_{\ell}$ 使其受这些坐标卡的控制。我们定义 $\omega$ 在 $M$ 上的**积分**为

$$
\begin{gather}
\int_{M} \omega=\sum_{i=1}^{\ell} \int_{M} \phi_{i} \omega
\end{gather}
$$

上述定义与定义 4.3.1 是相容的，这一结论来源于积分的线性性以及等式

$$
\begin{gather}
\omega(x)=\sum_{i=1}^{\ell} \phi_{i}(x)\omega(x)
\end{gather}
$$

与 $\int_{M}f\mathrm{d}V$ 类似，我们也可以证明上述定义与单位分解的选取无关。同理也有：

**定理 4.3.3**

设 $M$ 是 $\mathbb{R}^{n}$ 中的一个紧致定向 $k$-流形，$\omega,\eta$ 是定义在 $\mathbb{R}^{n}$ 中包含 $M$ 的开集上的 $k$-形式，则有

$$
\begin{gather}
\int_{M}(a\omega+b \eta)=a\int_{M}\omega+b\int_{M}\eta \\
\int_{-M} \omega=-\int_{M} \omega
\end{gather}
$$

$k$-形式是一个相当抽象的概念，而其在流形上的积分则更为抽象。我们可以给它一些直观的几何解释吗？下面，我们将讨论它与流形上标量函数的积分之间的联系，其中后者更接近于我们的几何直观。

首先，我们讨论 $\mathbb{R}^{n}$ 中的交错张量与体积函数 $V$ 之间的关系。

**定理 4.3.4**

设 $W$ 是 $\mathbb{R}^{n}$ 的一个 $k$ 维子空间，令 $(w_{1},\dots,w_{k})$ 是 $W$ 的一个规范正交 $k$-标架，$f$ 是 $W$ 上的一个交错 $k$-张量。如果 $(x_{1},\dots,x_{k})$ 是 $W$ 中的任意 $k$-元组，则

$$
\begin{gather}
f(x_{1},\dots,x_{k})=\epsilon V(x_{1},\dots,x_{k}) f(w_{1},\dots,w_{k})
\end{gather}
$$

其中 $\epsilon=\pm 1$. 当 $x_{1},\dots,x_{k}$ 线性无关时，$\epsilon=+1$ 如果标架 $(x_{1},\dots,x_{k})$ 与 $(w_{1},\dots,w_{k})$ 的定向相同；反之则 $\epsilon=-1$.

如果 $x_{1},\dots,x_{k}$ 线性相关，那么 $V(x_{1},\dots,x_{k})=0$，因此 $\epsilon$ 的值是无关紧要的。

**证明**

(1). 我们证明当 $W=\mathbb{R}^{k}$ 时定理成立。此时，交错张量 $f$ 就是行列式函数的标量倍，即

$$
\begin{gather}
f(x_{1},\dots,x_{k})=c \det[x_{1},\dots,x_{k}]
\end{gather}
$$

如果 $x_{1},\dots,x_{k}$ 线性相关，则 $f=0$，因而定理成立。反之，我们有

$$
\begin{gather}
f(x_{1},\dots,x_{k})=c \epsilon_{1} V(x_{1},\dots,x_{k})
\end{gather}
$$

其中 $\epsilon_{1}=+1$ 如果 $(x_{1},\dots,x_{k})$ 是右手的，反之则有 $\epsilon_{1}=-1$. 同理，我们有

$$
\begin{gather}
f(w_{1},\dots,w_{k})=c\epsilon_{2} V(w_{1},\dots,w_{k})=c\epsilon_{2}
\end{gather}
$$

其中 $\epsilon_{2}=+1$ 如果 $(w_{1},\dots,w_{k})$ 是右手的，因此

$$
\begin{gather}
f(x_{1},\dots,x_{k})=\dfrac{\epsilon_{1}}{\epsilon_{2}} V(x_{1},\dots,x_{k})f(w_{1},\dots,w_{k})
\end{gather}
$$

其中 $\epsilon=\dfrac{\epsilon_{1}}{\epsilon_{2}}=+1$ 如果两个标架定向相同，反之则有 $\epsilon=-1$.

(2). 我们对一般的 $W$ 进行证明。给定 $W$，取一个正交变换 $h\colon \mathbb{R}^{n}\to \mathbb{R}^{n}$，其将 $W$ 映射到 $\mathbb{R}^{k}\times 0$. 令 $k\colon \mathbb{R}^{k}\times 0\to W$ 为 $h$ 的逆映射，由于 $f$ 是 $W$ 上的交错张量，故 $k^{*}f$ 是 $\mathbb{R}^{k}\times 0$ 上的交错张量。由于 $(h(x_{1}),\dots,h(x_{k}))$ 是 $\mathbb{R}^{k}\times 0$ 上的 $k$-元组，$(h(w_{1}),\dots,h(w_{k}))$ 是 $\mathbb{R}^{k}\times 0$ 上的规范正交标架，于是根据步骤 (1) 得

$$
\begin{gather}
(k^{*}f)(h(x_{1}),\dots,h(x_{k}))=\epsilon V(h(x_{1}),\dots,h(x_{k})) (k^{*}f)(h(w_{1}),\dots,h(w_{k}))
\end{gather}
$$

由于 $V$ 在正交变换下不变，并且 $k^{*}f=f\circ k$，因此我们有

$$
\begin{gather}
f(x_{1},\dots,x_{k})=\epsilon V(x_{1},\dots,x_{k}) f(w_{1},\dots,w_{k})
\end{gather}
$$

现在假设 $x_{1},\dots,x_{k}$ 是线性无关的，则 $h(x_{1}),\dots,h(x_{k})$ 线性无关。根据步骤 (1)，$\epsilon=+1$ 当且仅当 $(h(x_{1}),\dots,h(x_{k}))$ 与 $(h(w_{1}),\dots,h(w_{k}))$ 的定向相同，而这当且仅当 $(x_{1},\dots,x_{k})$ 与 $(w_{1},\dots,w_{k})$ 的定向相同。这就完成了证明。

特别地，根据上述定理，如果 $(u_{1},\dots,u_{k})$ 和 $(w_{1},\dots,w_{k})$ 是 $W$ 中两个规范正交标架，那么

$$
\begin{gather}
f(u_{1},\dots,u_{k})=\pm f(w_{1},\dots,w_{k})
\end{gather}
$$

其中的符号取决于两个标架是否属于 $W$ 的同一定向。

**定义 4.3.5** 自然定向（natural orientation）

设 $M$ 是 $\mathbb{R}^{n}$ 中的 $k$-流形，$p \in M$，如果 $M$ 是定向的，那么 $p$ 处 $M$ 的切空间 $\mathcal{T}_{p}(M)$ 有一个自然的诱导定向，定义如下：取一个 $p$ 处属于 $M$ 的定向的坐标卡 $\alpha\colon U\to V$，令 $\alpha(x)=p$，则所有 $\mathcal{T}_{p}(M)$ 中具有以下形式的 $k$-标架构成的集合

$$
\begin{gather}
(\alpha_{*}(x;u_{1}),\dots,\alpha_{*}(x;u_{k}))
\end{gather}
$$

其中 $(u_{1},\dots,u_{k})$ 是 $\mathbb{R}^{k}$ 中的右手系，称为由 $M$ 的定向诱导的 $\mathcal{T}_{p}(M)$ 的**自然定向**。容易证明它是良定的，与坐标卡的选取无关。

**定理 4.3.6**

设 $M$ 是 $\mathbb{R}^{n}$ 中的一个紧致定向 $k$-流形，$\omega$ 是一个定义在 $\mathbb{R}^{n}$ 中包含 $M$ 的开集上的 $k$-形式。令 $\lambda$ 为 $M$ 上的标量场

$$
\begin{gather}
\lambda(p)=\omega(p)((p;u_{1}),\dots,(p;u_{k}))
\end{gather}
$$

其中 $((p;u_{1}),\dots,(p;u_{k}))$ 是属于 $\mathcal{T}_{p}(M)$ 的自然定向的任意规范正交标架。则 $\lambda$ 是连续的，并且

$$
\begin{gather}
\int_{M} \omega=\int_{M} \lambda \mathrm{d} V
\end{gather}
$$

**证明**

根据线性性，我们只需证明当 $\omega$ 的支撑集被单个坐标卡 $\alpha\colon U\to V$ 覆盖的情况。我们有

$$
\begin{gather}
\alpha^{*}\omega=h \mathrm{d} x_{1}\land\dots \land \mathrm{d} x_{k}
\end{gather}
$$

令 $\alpha(x)=p$，我们计算 $h(x)$ 如下：

$$
\begin{align}
h(x) &= (\alpha^{*}\omega)(x)((x;e_{1}),\dots,(x;e_{k})) \\
&= \omega(\alpha(x))(\alpha_{*}(x;e_{1}),\dots,\alpha_{*}(x;e_{k})) \\
&= \omega(p)\left( \left( p;\dfrac{ \partial \alpha }{ \partial x_{1} }  \right),\dots,\left( p;\dfrac{ \partial \alpha }{ \partial x_{k} }  \right) \right) \\
&= V(J_{\alpha}) \lambda(p)
\end{align}
$$

其中最后一步由定理 4.3.4 给出，其中的符号是 $+1$，因为标架

$$
\left( \left( p;\dfrac{ \partial \alpha }{ \partial x_{1} }  \right),\dots,\left( p;\dfrac{ \partial \alpha }{ \partial x_{k} }  \right) \right)
$$

根据定义是属于 $\mathcal{T}_{p}(M)$ 的自然定向的。由于 $J_{\alpha}$ 的秩为 $k$，故 $V(J_{\alpha})\neq 0$，又因为 $x=\alpha^{-1}(p)$ 是连续函数，因此

$$
\begin{gather}
\lambda(p)=\dfrac{h(x)}{V(J_{\alpha})}
\end{gather}
$$

是连续的，于是

$$
\begin{gather}
\int_{M} \lambda \mathrm{d} V=\int_{\mathrm{Int}(U)} (\lambda \circ\alpha) V(J_{\alpha})=\int_{\mathrm{Int}(U)} h
\end{gather}
$$

另一方面，根据定义我们也有

$$
\begin{gather}
\int_{M}\omega =\int_{\mathrm{Int}(U)} \alpha^{*}\omega=\int_{\mathrm{Int}(U)} h
\end{gather}
$$

这就完成了证明。

这一定理表明，给定定义在 $\mathbb{R}^{n}$ 中包含 $M$ 的开集上的 $k$-形式 $\omega$，存在一个标量函数（实际上是 $C^{\infty}$ 连续的）$\lambda$ 使得

$$
\begin{gather}
\int_{M}\omega=\int_{M} \lambda \mathrm{d} V
\end{gather}
$$

换句话说，所有形式的积分都等价于一个标量函数对体积的积分。作为它的一个推论，我们可以给出形式积分的一个计算公式：

**定理 4.3.7**

设 $M$ 是 $\mathbb{R}^{n}$ 中的一个紧致定向 $k$-流形，$\omega$ 是一个定义在 $\mathbb{R}^{n}$ 中包含 $M$ 的开集上的 $k$-形式。假设 $\alpha_{i}\colon A_{i}\to M_{i}\ (i=1,\dots,N)$ 是属于 $M$ 的定向的坐标卡，使得 $A_{i}$ 是 $\mathbb{R}^{k}$ 中的开集，且 $M$ 是开集 $M_{1},\dots,M_{N}$ 以及一个 $M$ 上的零测集 $K$ 的无交并，则

$$
\begin{gather}
\int_{M} \omega=\sum_{i=1}^{N} \int_{A_{i}} \alpha_{i}^{*} \omega
\end{gather}
$$

换句话说，为计算积分 $\int_{M}\omega$，我们可以将 $M$ 分解为若干个小块，在每一部分上分别参数化并积分，最后把所有积分值加起来。

# Section 4: 广义 Stokes 定理

现在，我们终于来到了集我们所有努力之大成的那个定理。我们以一个引理开始，在某种意义上，它是该定理的一个非常特殊的例子。

我们记 $I^{k}$ 为 $\mathbb{R}^{k}$ 中的单位 $k$-立方体 $I^{k}=[0,1]^{k}$，则 $\mathrm{Int}(I^{k})$ 就是单位开立方体 $(0,1)^{k}$.

**引理 4.4.1**

设 $k>1$，$\eta$ 是定义在 $\mathbb{R}^{k}$ 中包含 $I^{k}$ 的开集 $U$ 上的 $k-1$ 形式。假设 $\eta$ 在除了 $\mathrm{Int}(I^{k-1})\times 0$ 以外的 $\partial I^{k}$ 上消失，则

$$
\begin{gather}
\int_{\mathrm{Int}(I^{k})} \mathrm{d} \eta=(-1)^{k} \int_{\mathrm{Int}(I^{k-1})} b^{*}\eta
\end{gather}
$$

其中 $b\colon I^{k-1}\to I^{k}$ 定义为

$$
\begin{gather}
b(u_{1},\dots,u_{k-1})=(u_{1},\dots,u_{k-1},0)
\end{gather}
$$

**证明**

我们用 $x$ 表示 $\mathbb{R}^{k}$ 中的一般点，用 $u$ 表示 $\mathbb{R}^{k-1}$ 中的一般点。给定 $1\leq j\leq k$，我们记 $I_{j}$ 为 $k-1$ 元组

$$
\begin{gather}
I_{j}=(1,\dots,j-1,j+1,\dots,k)
\end{gather}
$$

则与之相关的基本 $k-1$ 形式为

$$
\begin{gather}
\mathrm{d} x_{I_{j}}=\mathrm{d} x_{1}\land\dots \land \mathrm{d} x_{j-1}\land \mathrm{d} x_{j+1} \land\dots \land \mathrm{d} x_{k}
\end{gather}
$$

由于定理中的等式两边关于 $\eta$ 是线性的，因此我们只需考虑

$$
\begin{gather}
\eta=f \mathrm{d} x_{I_{j}}
\end{gather}
$$

的情况。

(1). 我们计算左边的积分。我们有

$$
\begin{align}
\mathrm{d} \eta &= \mathrm{d} f\land \mathrm{d} x_{I_{j}} \\
&= \left( \sum_{i=1}^{k} \dfrac{ \partial f }{ \partial x_{i} } \mathrm{d} x_{i} \right) \land \mathrm{d} x_{I_{j}} \\
&= (-1)^{j-1} \dfrac{ \partial f }{ \partial x_{j} } \mathrm{d} x_{1}\land\dots \land \mathrm{d} x_{k}
\end{align}
$$

于是我们计算

$$
\begin{align}
\int_{\mathrm{Int}(I^{k})} \mathrm{d} \eta &= (-1)^{j-1} \int_{\mathrm{Int}(I^{k})} \dfrac{ \partial f }{ \partial x_{j} }  \\
&= (-1)^{j-1} \int_{I^{k}} \dfrac{ \partial f }{ \partial x_{j} }  \\
&= (-1)^{j-1} \int_{v \in I^{k-1}} \int_{x_{j} \in I} \dfrac{ \partial f }{ \partial x_{j} } (x_{1},\dots,x_{k})
\end{align}
$$

其中 $v=(x_{1},\dots,x_{j-1},x_{j+1},\dots,x_{k})$，应用微积分基本定理，我们可得内层积分为

$$
\begin{align}
\int_{x_{j}\in I} \dfrac{ \partial f }{ \partial x_{j} } (x_{1},\dots,x_{k})=f(x_{1},\dots,1,\dots,x_{k})-f(x_{1},\dots,0,\dots,x_{k})
\end{align}
$$

由于 $\eta$ 在除了 $\mathrm{Int}(I^{k-1})\times 0$ 以外的 $\partial I^{k}$ 上消失，因此当 $j<k$ 时，上式等于零，而当 $j=k$ 时，上式就等于

$$
\begin{gather}
-f(x_{1},\dots,x_{k-1},0)
\end{gather}
$$

因此我们得出

$$
\begin{gather}
\int_{\mathrm{Int}(I^{k})} \mathrm{d} \eta=\begin{cases}
0 ,&  j<k \\
\displaystyle (-1)^{k} \int_{I^{k-1}} (f\circ b) , & j=k
\end{cases}
\end{gather}
$$

(2). 下面我们计算右边的积分。映射 $b\colon \mathbb{R}^{k-1}\to \mathbb{R}^{k}$ 具有导数

$$
\begin{gather}
J_{b}=\begin{bmatrix}
I_{k-1}  \\
0
\end{bmatrix}
\end{gather}
$$

因此，根据定理 3.4.3 有

$$
\begin{align}
b^{*}(\mathrm{d} x_{I_{j}}) &= \det [J_{b}]_{I_{j}} \mathrm{d} u_{1}\land\dots \land \mathrm{d} u_{k-1} \\
&=\begin{cases}
0 , & j<k \\
\mathrm{d} u_{1}\land\dots \land \mathrm{d} u_{k-1} , & j=k
\end{cases}
\end{align}
$$

从而

$$
\begin{gather}
\int_{\mathrm{Int}(I^{k-1})} b^{*}\eta=\begin{cases}
0 , & j<k \\
\displaystyle \int_{\mathrm{Int}(I^{k-1})} (f\circ b) , & j=k
\end{cases}
\end{gather}
$$

由于 $\partial I^{k-1}$ 具有测度零，因此在 $\mathrm{Int}(I^{k-1})$ 上的积分等于在 $I^{k-1}$ 上的积分，这就完成了证明。

**定理 4.4.2** Stokes 定理

设 $k>1$，$M$ 是 $\mathbb{R}^{n}$ 中的一个紧致定向 $k$-流形，如果 $\partial M\neq \varnothing$，则给予 $\partial M$ 诱导定向。令 $\omega$ 是一个定义在 $\mathbb{R}^{n}$ 中包含 $M$ 的开集上的 $k-1$ 形式则

$$
\begin{gather}
\int_{M} \mathrm{d} \omega=\int_{\partial M} \omega
\end{gather}
$$

如果 $\partial M\neq \varnothing$；并且 $\int_{M}\mathrm{d}\omega=0$ 如果 $\partial M=\varnothing$.

**证明**

(1). 我们首先用精心挑选的坐标卡来覆盖 $M$. 作为第一个例子，我们设 $p \in \mathrm{Int}(M)$，通过与平移变换与拉伸变换复合，我们可以选取坐标卡 $\alpha\colon U\to V$ 使得 $U$ 在 $\mathbb{R}^{k}$ 中开，包含单位立方体 $I^{k}$，并且 $\alpha^{-1}(p)$ 属于 $\mathrm{Int}(I^{k})$. 令 $W=\mathrm{Int}(I^{k})$，$Y=\alpha[W]$，则 $\alpha|_{W}\colon W\to Y$ 仍然是一个 $p$ 处的坐标卡，其中 $W$ 在 $\mathbb{R}^{k}$ 中开。我们选取这个坐标卡作为 $p$ 处的坐标卡。

作为第二个例子，我们设 $p \in \partial M$. 选取坐标卡 $\alpha\colon U\to V$ 使得 $U$ 在 $\mathbb{H}^{k}$ 中开，包含 $I^{k}$，并且 $\alpha^{-1}(p)$ 属于 $\mathrm{Int}(I^{k-1})\times 0$. 令

$$
\begin{gather}
W=\mathrm{Int}(I^{k}) \cup (\mathrm{Int}(I^{k-1})\times 0)
\end{gather}
$$

且 $Y=\alpha[W]$，则 $\alpha|_{W}\colon W\to Y$ 仍然是 $p$ 处的坐标卡，其中 $W$ 在 $\mathbb{H}^{k}$ 中开而不在 $\mathbb{R}^{k}$ 中开。我们选取这个坐标卡作为 $p$ 处的坐标卡。

![](4-9.png)

(2). 由于微分算子 $\mathrm{d}$ 和积分是线性的，故我们只需考虑

$$
\begin{gather}
C=M\cap \mathrm{supp}(\omega)
\end{gather}
$$

可以被单个坐标卡 $\alpha\colon W\to Y$ 覆盖的情况。由于 $\mathrm{supp}(\mathrm{d}\omega)\subset \mathrm{supp}(\omega)$，因此 $M\cap \mathrm{supp}(\mathrm{d}\omega)\subset C$，从而它可被相同的坐标卡覆盖。

令 $\eta=\alpha^{*}\omega$，它可以扩张为一个定义在 $\mathbb{R}^{k}$ 中包含 $I^{k}$ 的开集上的 $C^{\infty}$ 形式。此外，它在除了 $\mathrm{Int}(I^{k-1})\times 0$ 以外的 $\partial I^{k}$ 上消失，于是我们可以应用引理 4.4.1 的结论。

(3). 我们首先对步骤 (1) 中第一种情况下构造的 $\alpha\colon W\to Y$ 进行证明，此时 $W=\mathrm{Int}(I^{k})$ 且 $Y$ 与 $\partial M$ 不相交。由于 $\alpha^{*}\mathrm{d}\omega=\mathrm{d}(\alpha^{*}\omega)=\mathrm{d}\eta$，我们有

$$
\begin{gather}
\int_{M} \mathrm{d} \omega=\int_{\mathrm{Int}(I^{k})} \alpha^{*}\mathrm{d} \omega=\int_{\mathrm{Int}(I^{k})} \mathrm{d} \eta=(-1)^{k} \int_{\mathrm{Int}(I^{k-1})} b^{*}\eta
\end{gather}
$$

在这种情况下，由于 $\alpha^{-1}[C]\subset W$，因此 $\eta$ 在 $I^{k-1}\times 0$ 上消失，从而 $b^{*}\eta=0$，这给出 $\int_{M}\mathrm{d}\omega=0$.

如果 $\partial M=\varnothing$，这就是我们要证的；如果 $\partial M\neq \varnothing$，由于 $C\subset Y$ 与 $\partial M$ 不相交，因而有

$$
\begin{gather}
\int_{M} \mathrm{d} \omega=\int_{\partial M} \omega=0
\end{gather}
$$

(4). 下面我们对步骤 (1) 中的第二种情况进行证明。此时 $W$ 在 $\mathbb{H}^{k}$ 中开而不在 $\mathbb{R}^{k}$ 中开，$Y\cap \partial M\neq \varnothing$，并且 $\mathrm{Int}(W)=\mathrm{Int}(I^{k})$. 我们计算

$$
\begin{gather}
\int_{M} \mathrm{d} \omega=\int_{\mathrm{Int}(I^{k})} \mathrm{d} \eta=(-1)^{k} \int_{\mathrm{Int}(I^{k-1})} b^{*}\eta
\end{gather}
$$

接下来我们计算积分 $\int_{\partial M} \omega$. 集合 $\partial M\cap \mathrm{supp}(\omega)$ 可以由坐标卡 $\alpha$ 的限制

$$
\begin{gather}
\alpha_{0}=\alpha \circ b\colon \mathrm{Int}(I^{k-1}) \to Y\cap \partial M
\end{gather}
$$

覆盖。根据诱导定向的定义，如果 $k$ 是偶数，那么 $\alpha_{0}$ 属于诱导定向，如果 $k$ 是奇数，那么 $\alpha_{0}$ 属于诱导定向的反定向。因此，如果我们使用 $\alpha_{0}$ 来计算 $\int_{\partial M}\omega$，那么当 $k$ 为奇数时我们必须反转符号，从而

$$
\begin{gather}
\int_{\partial M} \omega=(-1)^{k} \int_{\mathrm{Int}(I^{k-1})} \alpha_{0}^{*} \omega
\end{gather}
$$

又由于 $\alpha_{0}^{*}\omega=b^{*}(\alpha^{*}\omega)=b^{*}\eta$，这就完成了证明。

在上述定理中令 $n=k=2$，则我们立即得到：

**定理 4.4.3** Green 定理

设 $M$ 是 $\mathbb{R}^{2}$ 中的紧致定向 $2$-流形，取自然定向，并给予 $\partial M$ 诱导定向。令 $P\mathrm{d}x+Q\mathrm{d}y$ 为定义在 $\mathbb{R}^{2}$ 中包含 $M$ 的开集上的 $1$-形式，则有

$$
\begin{gather}
\int_{\partial M} P\mathrm{d} x+Q\mathrm{d} y=\int_{M} \left( \dfrac{ \partial Q }{ \partial x } -\dfrac{ \partial P }{ \partial y }  \right) \mathrm{d} x\land \mathrm{d} y
\end{gather}
$$

**证明**

设 $\omega=P\mathrm{d}x+Q\mathrm{d}y$，则我们有

$$
\begin{align}
\mathrm{d} \omega &= \mathrm{d} P\land \mathrm{d} x+\mathrm{d} Q\land \mathrm{d} y \\
&= \left( \dfrac{ \partial P }{ \partial x } \mathrm{d} x+\dfrac{ \partial P }{ \partial y } \mathrm{d} y \right)\land \mathrm{d} x+\left( \dfrac{ \partial Q }{ \partial x } \mathrm{d} x+\dfrac{ \partial Q }{ \partial y } \mathrm{d} y \right) \land \mathrm{d} y \\
&= \left( \dfrac{ \partial Q }{ \partial x } -\dfrac{ \partial P }{ \partial y }  \right)\mathrm{d} x\land \mathrm{d} y
\end{align}
$$

根据 Stokes 定理即证。

我们已经对 $k>1$ 的 $k$-流形证明了 Stokes 定理。对于 $k=1$ 的情况，我们能说什么呢？如果 $\partial M=\varnothing$，那么我们可以类似地证明 $\int_{M}\mathrm{d}\omega=0$；但如果 $\partial M\neq \varnothing$，那么我们就面临几个问题：一个 $0$-流形的“定向”是指什么？而且我们如何在一个定向 $0$-流形上对 $0$-形式“积分”呢？

为了弄清楚在这种情况下 Stokes 定理应采取何种形式，我们先考虑一个特殊情况。

**定义 4.4.4** 弧（arc）

设 $M$ 是 $\mathbb{R}^{n}$ 上的 $1$-流形，如果存在 $C^{\infty}$ 微分同胚 $\alpha\colon[a,b]\to M$，则称 $M$ 是 $\mathbb{R}^{n}$ 上的一段光滑**弧**。如果 $M$ 是定向的，并且 $\alpha|_{(a,b)}$ 是属于给定定向的坐标卡，那么我们就称 $p=\alpha(a)$ 为 $M$ 的**起点**，$q=\alpha(b)$ 为 $M$ 的**终点**。

![](4-10.png)

**定理 4.4.5**

设 $M$ 是 $\mathbb{R}^{n}$ 上的 $1$-流形，$f$ 是定义在 $\mathbb{R}^{n}$ 中包含 $M$ 的开集上的 $0$-形式。如果 $M$ 是以 $p$ 为起点，$q$ 为终点的弧，那么

$$
\begin{gather}
\int_{M} \mathrm{d} f=f(q)-f(p)
\end{gather}
$$

**证明**

令 $\alpha\colon[a,b]\to M$ 如定义 4.4.4 中所示。则 $\alpha|_{(a,b)}\colon (a,b)\to M\setminus\{ p,q \}$ 是一个覆盖 $M$ 的坐标卡（除了一个零测集），根据定理 4.3.7，我们有

$$
\begin{align}
\int_{M} \mathrm{d} f &= \int_{(a,b)} \alpha^{*} \mathrm{d} f \\
&= \int_{(a,b)} \mathrm{d} (f\circ\alpha) \\
&= \int_{(a,b)} (f\circ\alpha)' \mathrm{d} t \\
&= (f\circ\alpha)(b)-(f\circ\alpha)(a)
\end{align}
$$

这就完成了证明。

这一结果为我们表述 $1$-流形上的 Stokes 定理提供了指导。

**定义 4.4.6**

$\mathbb{R}^{n}$ 上的紧致 $0$-流形 $N$ 是一个 $\mathbb{R}^{n}$ 上的有限点集 $\{ x_{1},\dots,x_{m} \}$. 我们定义 $N$ 上的一个**定向**是一个函数 $\epsilon\colon N\to \{ -1,1 \}$. 如果 $f$ 是一个定义在 $\mathbb{R}^{n}$ 中包含 $N$ 的开集上的 $0$-形式，我们定义 $f$ 在 $N$ 上的**积分**为

$$
\begin{gather}
\int_{N} f=\sum_{i=1}^{m} \epsilon(x_{i})f(x_{i})
\end{gather}
$$

**定义 4.4.7**

设 $M$ 是 $\mathbb{R}^{n}$ 上具有非空边界的定向 $1$-流形，我们定义 $\partial M$ 上的**诱导定向**如下：对 $p \in \partial M$，如果存在 $p$ 处属于 $M$ 的定向的坐标卡 $\alpha\colon U\to V$ 使得 $U$ 在 $\mathbb{H}^{1}$ 中开，则定义 $\epsilon(p)=-1$；反之，如果 $U$ 在 $\mathbb{L}^{1}$ 中开，则定义 $\epsilon(p)=+1$.

![](4-11.png)

有了上面的定义，$1$-流形上的 Stokes 定理就与 $k$-流形上的 Stokes 定理具有相同的形式，如下所示：

**定理 4.4.8** Stokes 定理

设 $M$ 是 $\mathbb{R}^{n}$ 上的紧致定向 $1$-流形，如果 $\partial M\neq \varnothing$，则给予 $\partial M$ 诱导定向。令 $f$ 是定义在 $\mathbb{R}^{n}$ 中包含 $M$ 的开集上的 $0$-形式，则

$$
\begin{gather}
\int_{M}\mathrm{d} f=\int_{\partial M}f
\end{gather}
$$

如果 $\partial M\neq \varnothing$；并且 $\int_{M}\mathrm{d}f=0$ 如果 $\partial M=\varnothing$.

**证明**

我们仿照 4.4.2 中的证明，使用坐标卡 $\alpha\colon W\to Y$ 来覆盖 $M$，其中 $W$ 是 $(0,1),[0,1),(-1,0]$ 之一。由于等式两边关于 $f$ 是线性的，因此我们只需考虑 $C=M\cap \mathrm{supp}(f)$ 被单个坐标卡覆盖的情况。

首先设 $W=(0,1)$，则此时 $Y$ 与 $\partial M$ 不相交。我们计算

$$
\begin{align}
\int_{M} \mathrm{d} f=\int_{(0,1)} \alpha^{*} \mathrm{d} f=(f\circ\alpha)(1)-(f\circ\alpha)(0)
\end{align}
$$

由于 $\alpha^{-1}[C]\subset W$，因此 $\int_{M}\mathrm{d}f=0$. 如果 $\partial M=\varnothing$，这就是要证的；如果 $\partial M\neq \varnothing$，由于 $C\subset Y$ 与 $\partial M$ 不相交，因此 $\int_{\partial M}f=0$，即证。

其次，设 $W=[0,1)$，则此时的 $\alpha\colon W\to Y$ 是 $p=\alpha(0)$ 处的坐标卡，使得 $p \in \partial M$ 满足 $\epsilon(p)=-1$，于是我们有

$$
\begin{gather}
\int_{M} \mathrm{d} f=-f(p)=\epsilon(p)f(p)=\int_{\partial M} f
\end{gather}
$$

最后，对于 $W=(-1,0]$，此时的 $\alpha\colon W\to Y$ 是 $q=\alpha(1)$ 处的坐标卡，使得 $q \in \partial M$ 满足 $\epsilon(q)=+1$，因此

$$
\begin{gather}
\int_{M} \mathrm{d} f=f(q)=\epsilon(q)f(q)=\int_{\partial M} f
\end{gather}
$$

这就完成了证明。

# Section 5: 向量分析

我们知道，在特定的情况下，$\mathbb{R}^{n}$ 中的 $k$-形式可以被解释为标量场或者向量场，具体来说，是当 $k=0,1,n-1$ 或 $n$ 时。在本节中，我们将展示，在这些情况下，流形上形式的积分也同样可以解释为标量场或向量场的积分。在这些情况下，Stokes 定理同样适用，并且它们构成了向量分析的几大基本定理。

我们逐一考虑各种情况。

首先，我们使用向量场来解释 $1$-形式的积分。如果 $F$ 是定义在 $\mathbb{R}^{n}$ 中的开集上的向量场，根据定理 3.3.2，它通过映射 $\alpha_{1}$ 对应于一个 $1$-形式 $\omega$. 事实证明，$\omega$ 在定向 $1$-流形上的积分等于 $F$ 的切向分量关于 $1$-体积的积分。那就是以下引理的主要内容：

**引理 4.5.1**

设 $M$ 是 $\mathbb{R}^{n}$ 上的紧致定向 $1$-流形，$T$ 为对应于 $M$ 的定向的单位切向量场。令

$$
\begin{gather}
F(x)=(x;f(x))=\left( x; \sum_{i=1}^{n} f_{i}(x)e_{i} \right)
\end{gather}
$$

为一个定义在 $\mathbb{R}^{n}$ 中包含 $M$ 的开集上的向量场，它对应于 $1$-形式

$$
\begin{gather}
\omega=\sum_{i=1}^{n} f_{i} \mathrm{d} x_{i}
\end{gather}
$$

则我们有

$$
\begin{gather}
\int_{M} \omega=\int_{M} \langle F,T \rangle \mathrm{d} s
\end{gather}
$$

这里我们使用经典符号 $\mathrm{d}s$ 而不是 $\mathrm{d}V$ 来表示关于 $1$-体积（长度）的积分。在物理学中，我们通常省略切向量场 $T$，而直接写成

$$
\begin{gather}
\int_{M} \mathbf{F} \cdot \mathrm{d} \mathbf{s} \quad \text{或} \quad \int_{M} \mathbf{F} \cdot \mathrm{d} \mathbf{l}
\end{gather}
$$

注意，当我们取 $M$ 的反定向时，左边的积分改变了符号。对于右边的积分，由于切向量 $T$ 被替换为了 $-T$，因此它也改变了符号。

**证明**

根据定理 4.3.6，我们有

$$
\begin{gather}
\int_{M} \omega=\int_{M} \lambda \mathrm{d} s
\end{gather}
$$

其中 $\lambda(p)$ 是张量 $\omega(p)$ 在 $\mathcal{T}_{p}(M)$ 中属于自然定向的规范正交基上的值。在这种情况下，切空间是一维的，并且 $T(p)$ 就是这样的一个基。令 $T(p)=(p;t)$，则我们有

$$
\begin{align}
\lambda(p) = \sum_{i=1}^{n} f_{i}(p) t_{i}(p) = \langle F(p),T(p) \rangle 
\end{align}
$$

这就完成了证明。

**定理 4.5.2** 梯度定理（gradient theorem）

设 $M$ 是 $\mathbb{R}^{n}$ 上的紧致定向 $1$-流形，$T$ 为对应于 $M$ 的定向的单位切向量场。设 $f$ 是一个定义在 $\mathbb{R}^{n}$ 中包含 $M$ 的开集上的 $C^{\infty}$ 函数。如果 $\partial M=\varnothing$，则

$$
\begin{gather}
\int_{M} \langle \mathrm{grad}\ f, T \rangle \mathrm{d} s=0
\end{gather}
$$

如果 $\partial M=\{ x_{1},\dots,x_{m} \}$，令 $\epsilon(x_{i})=-1$ 如果 $T(x_{i})$ 指向 $M$ 的内部；反之则 $\epsilon(x_{i})=+1$，那么我们有

$$
\begin{gather}
\int_{M} \langle \mathrm{grad}\ f, T \rangle \mathrm{d} s=\sum_{i=1}^{m} \epsilon(x_{i}) f(x_{i})
\end{gather}
$$

**证明**

向量场 $\mathrm{grad}\ f$ 对应于 $1$-形式 $\mathrm{d}f$，因此根据引理 4.5.1 得

$$
\begin{gather}
\int_{M} \mathrm{d} f=\int_{M} \langle \mathrm{grad}\ f, T \rangle \mathrm{d} s
\end{gather}
$$

应用一维 Stokes 定理即证。

下面我们用向量场来解释 $n-1$ 形式在定向 $n-1$ 流形上的积分。不过首先，我们需要验证一个我们曾断言但未证明的结论：$n-1$ 流形 $M$ 的定向唯一确定了其上的单位法向量场。回顾第二节中的以下定义：

**定义**

设 $M$ 是 $\mathbb{R}^{n}$ 中的可定向 $n-1$ 流形，如果 $p \in M$，令 $(p;n) \in \mathcal{T}_{p}(\mathbb{R}^{n})$ 为一个正交于 $n-1$ 维向量空间 $\mathcal{T}_{p}(M)$ 的单位向量，则 $n$ 在相差一个符号下是唯一确定的。给定 $M$ 的一个定向，取 $p$ 处属于该定向的坐标卡 $\alpha\colon U\to V$，令 $\alpha(x)=p$，则矩阵 $J_{\alpha}(x)$ 的列给出了 $\mathcal{T}_{p}(M)$ 的一个基

$$
\begin{gather}
\left( p;\dfrac{ \partial \alpha }{ \partial x_{1} }  \right), \dots, \left( p;\dfrac{ \partial \alpha }{ \partial x_{n-1} }  \right)
\end{gather}
$$

我们按如下方法确定 $n$ 的符号：我们要求标架

$$
\begin{gather}
\left( n,\dfrac{ \partial \alpha }{ \partial x_{1} } ,\dots,\dfrac{ \partial \alpha }{ \partial x_{n-1} }  \right)
\end{gather}
$$

是右手的，即 $\det [n, J_{\alpha}(x)]>0$. 向量场 $N(p)=(p;n(p))$ 称为对应于 $M$ 的定向的**单位法向量场**。

我们证明 $N(p)$ 是良定的，并且它还是 $C^{\infty}$ 连续的。为证明它是良定的，我们设 $\beta$ 是 $p$ 处的另一个坐标卡，它属于 $M$ 的定向。令 $g=\beta^{-1}\circ\alpha$ 为转移函数，并令 $g(x)=y$，则有

$$
\begin{gather}
J_{\alpha}(x)=J_{\beta}(y) J_{g}(x)
\end{gather}
$$

于是，对任意 $v \in \mathbb{R}^{n}$，我们有等式

$$
\begin{gather}
[v, J_{\alpha}(x)]=[v, J_{\beta}(y)] \begin{bmatrix}
1 & 0 \\
0 & J_{g}(x)
\end{bmatrix}
\end{gather}
$$

因为 $J_{\alpha},J_{\beta}$ 都是 $n\times(n-1)$ 矩阵，$J_{g}$ 是 $(n-1)\times(n-1)$ 矩阵。从而我们有

$$
\begin{gather}
\det [v,J_{\alpha}(x)]=\det [v,J_{\beta}(y)] \det J_{g}
\end{gather}
$$

由于 $\det J_{g}>0$，故 $\det[v,J_{\alpha}(x)]=0$ 当且仅当 $\det[v,J_{\beta}(y)]=0$.

为证明 $N$ 是 $C^{\infty}$ 连续的，我们可以给出它的一个公式。作为动机，我们首先考虑 $n=3$ 的情况：

给定 $a,b \in \mathbb{R}^{3}$，我们在微积分中学到，它们的叉积 $c=a\times b$ 正交于 $a,b$，并且标架 $(c,a,b)$ 是右手的，还有 $\lVert c \rVert=V(a,b)$.

根据上述性质，我们可知如果 $M$ 是 $\mathbb{R}^{3}$ 中的定向 $2$-流形，$\alpha\colon U\to V$ 是属于给定定向的坐标卡，并且如果我们设

$$
\begin{gather}
c=\dfrac{ \partial \alpha }{ \partial x_{1} } \times \dfrac{ \partial \alpha }{ \partial x_{2} } 
\end{gather}
$$

那么向量 $n=\dfrac{c}{\lVert c \rVert}$ 就是所求的单位法向量，如图所示：

![](4-12.png)

上面这些性质的最简单解释是由叉积的行列式公式给出的：

$$
\begin{gather}
c=a\times b=\det \begin{bmatrix}
e_{1} & a_{1} & b_{1} \\
e_{2} & a_{2} & b_{2} \\
e_{3} & a_{3} & b_{3}
\end{bmatrix}
\end{gather}
$$

我们将行列式按第一列展开，对于任意向量 $v \in \mathbb{R}^{3}$，由于 $\langle v,e_{j} \rangle=v_{j}$，故 $v$ 与 $c$ 的内积就相当于将 $v$ 的分量 $v_{j}$ 代替标准基 $e_{j}$，下面我们反向应用代数余子式展开，即得

$$
\begin{gather}
\langle v,c \rangle =\det \begin{bmatrix}
v_{1} & a_{1} & b_{1} \\
v_{2} & a_{2} & b_{2} \\
v_{3} & a_{3} & b_{3}
\end{bmatrix}
\end{gather}
$$

因此，当 $v=a$ 或 $v=b$ 时显然有 $\langle v,c \rangle=0$. 此外，当 $v=c$ 时，我们有 $\det[c,a,b]=\langle c,c \rangle>0$，因此标架 $(c,a,b)$ 是右手的。最后，第三个性质由定理 1.1.7 给出。

将叉积的行列式公式推广到 $n$ 维，我们就得到了单位法向量场 $N$ 的一个公式。

**引理 4.5.3**

给定线性无关的向量 $x_{1},\dots,x_{n-1}\in \mathbb{R}^{n}$，令 $X$ 为 $n\times(n-1)$ 矩阵 $[x_{1},\dots,x_{n-1}]$，并令 $c\in \mathbb{R}^{n}$ 为 $c=\sum_{i=1}^{n}c_{i}e_{i}$，其中

$$
\begin{gather}
c_{i}=(-1)^{i-1} \det X(1,\dots,i-1,i+1,\dots,n)
\end{gather}
$$

则向量 $c$ 有如下性质：

1. $c\neq 0$ 且与所有 $x_{i}$ 正交
2. 标架 $(c,x_{1},\dots,x_{n-1})$ 是右手的
3. $\lVert c \rVert=V(X)$

**证明**

就像 $\mathbb{R}^{3}$ 中的叉积一样，我们可以在形式上将 $c$ 写成

$$
\begin{gather}
c=\det [e,x_{1},\dots,x_{n-1}], \quad e=(e_{1},\dots,e_{n})
\end{gather}
$$

利用第一列的代数余子式展开，我们可得

$$
\begin{gather}
\langle v,c \rangle =\det [v,x_{1},\dots,x_{n-1}]
\end{gather}
$$

这一等式包含了证明该定理所需的所有内容。这里我们只证 $c\neq 0$，其他性质的证明与 $\mathbb{R}^{3}$ 中的例子没有本质的区别。

由于 $x_{1},\dots,x_{n-1}$ 是线性无关的，故矩阵 $X$ 的秩为 $n-1$，从而其中的 $n-1$ 行是线性无关的，因此这 $n-1$ 行对应的 $c_{i}\neq 0$，因而 $c\neq 0$.

**定理 4.5.4**

如果 $M$ 是 $\mathbb{R}^{n}$ 上的一个光滑定向 $n-1$ 流形，那么对应于 $M$ 的定向的单位法向量场 $N(p)$ 是关于 $p$ 的一个 $C^{\infty}$ 函数。

**证明**

设 $\alpha\colon U\to V$ 是 $p$ 处的坐标卡，我们令

$$
\begin{gather}
c(x)=\det \left[ e, \dfrac{ \partial \alpha }{ \partial x_{1} }(x) ,\dots,\dfrac{ \partial \alpha }{ \partial x_{n-1} }(x)  \right]
\end{gather}
$$

其中 $x \in U$，则对任意 $p \in V$，我们有

$$
\begin{gather}
N(p)=\left( p; \dfrac{c(x)}{\lVert c(x) \rVert } \right)
\end{gather}
$$

其中 $x=\alpha^{-1}(p)$. 这个函数关于 $p$ 是 $C^{\infty}$ 连续的。

现在我们用向量场来描述 $n-1$ 流形上 $n-1$ 形式的积分。如果 $G$ 是 $\mathbb{R}^{n}$ 中的向量场，那么它通过映射 $\beta_{n-1}$ 对应于某个 $n-1$ 形式 $\omega$. 事实证明，$\omega$ 在 $n-1$ 流形上的积分等于 $G$ 的法向分量关于体积的积分。那就是以下引理的主要内容：

**引理 4.5.5**

设 $M$ 是 $\mathbb{R}^{n}$ 上的紧致定向 $n-1$ 流形，$N$ 是对应于 $M$ 的定向的单位法向量场。令 $G$ 是定义在 $\mathbb{R}^{n}$ 中包含 $M$ 的开集上的向量场。如果我们用 $y$ 来表示 $\mathbb{R}^{n}$ 中的一般点，则 $G$ 具有形式

$$
\begin{gather}
G(y)=(y;g(y))=\left( y; \sum_{i=1}^{n} g_{i}(y)e_{i} \right)
\end{gather}
$$

它对应于 $n-1$ 形式

$$
\begin{gather}
\omega=\sum_{i=1}^{n} (-1)^{i-1} g_{i} \mathrm{d} y_{1}\land\dots \land \mathrm{d} y_{i-1}\land \mathrm{d} y_{i+1}\land \dots \land \mathrm{d} y_{n}
\end{gather}
$$

则

$$
\begin{gather}
\int_{M} \omega=\int_{M} \langle G,N \rangle \mathrm{d} V
\end{gather}
$$

在物理学中，我们通常省略法向量场 $N$，而直接写成

$$
\begin{gather}
\int_{M} \mathbf{G} \cdot \mathrm{d} \mathbf{S}
\end{gather}
$$

称为 $G$ 在 $M$ 上的**通量**（flux）。由于此时 $n=3$，故我们用 $\mathrm{d}S$ 而不是 $\mathrm{d}V$ 来表示对 $2$-体积（面积）的积分。

注意，如果我们取 $M$ 的反定向，则左边的积分将改变符号。对于右边的积分，由于 $N$ 被替换为 $-N$，故它也将改变符号。

**证明**

根据定理 4.3.6，我们有

$$
\begin{gather}
\int_{M}\omega =\int_{M} \lambda \mathrm{d} V
\end{gather}
$$

我们要证 $\lambda=\langle G,N \rangle$.

令 $(p;u_{1}),\dots,(p;u_{n-1})$ 为 $\mathcal{T}_{p}(M)$ 的一个属于自然定向的规范正交基，设 $U$ 为矩阵 $[u_{1},\dots,u_{n-1}]$，并令 $c$ 为

$$
\begin{gather}
c=\det [e,u_{1},\dots,u_{n-1}]
\end{gather}
$$

根据引理 4.5.3，$c$ 正交于 $u_{i}$，且 $(c,u_{1},\dots,u_{n-1})$ 是右手的，并且

$$
\begin{gather}
\lVert c \rVert =\sqrt{ \det(U^{T}U) }=\sqrt{ \det I_{n-1} }=1
\end{gather}
$$

因此 $N(p)=(p;c)$ 就是 $p$ 处的单位法向量。又由于

$$
\begin{align}
&\mathrm{d} y_{1}\land\dots \land \mathrm{d} y_{i-1}\land \mathrm{d} y_{i+1}\land\dots \land \mathrm{d} y_{n} (p)((p;u_{1}),\dots,(p;u_{n-1})) \\
&= \det U(1,\dots,i-1,i+1,\dots,n)
\end{align}
$$

从而

$$
\begin{align}
\lambda(p) &= \sum_{i=1}^{n} (-1)^{i-1} g_{i}(p) \det U(1,\dots,i-1,i+1,\dots,n) \\
&= \sum_{i=1}^{n} g_{i}(p) c_{i}
\end{align}
$$

即证 $\lambda=\langle G,N \rangle$.

下面我们考虑 $k=n$ 的情况，它可以使用标量场来解释：

**引理 4.5.6**

设 $M$ 是 $\mathbb{R}^{n}$ 上的紧致 $n$-流形，取自然定向。令 $\omega=h\mathrm{d}x_{1}\land\dots \land \mathrm{d}x_{n}$ 为定义在 $\mathbb{R}^{n}$ 中包含 $M$ 的开集上的 $n$-形式，则其对应的标量场为 $h$，并且

$$
\begin{gather}
\int_{M} \omega=\int_{M} h \mathrm{d} V
\end{gather}
$$

**证明**

我们有

$$
\begin{gather}
\int_{M} \omega=\int_{M} \lambda \mathrm{d} V
\end{gather}
$$

由于自然定向包含使得 $\det\alpha'>0$ 的坐标卡 $\alpha$，因此 $\mathcal{T}_{p}(M)$ 上的自然定向包含右手标架。$\mathcal{T}_{p}(M)=\mathcal{T}_{p}(\mathbb{R}^{n})$ 上的标准基就是这样一个标架，并且 $\omega(p)$ 在其上的取值为 $h$，这就完成了证明。

我们指出：积分 $\int_{M}h\mathrm{d}V$ 实际上就等于有界集合 $M$ 上的积分 $\int_{M}h$. 这是因为恒等映射 $\mathrm{id}\colon \mathrm{Int}(M)\to \mathrm{Int}(M)$ 是 $M$ 上的坐标卡，其属于自然定向，并且覆盖了 $M$（除了一个零测集 $\partial M$）。根据定理 1.6.7，我们有

$$
\begin{gather}
\int_{M} h\mathrm{d} V=\int_{\mathrm{Int}(M)} (h\circ \mathrm{id}) V(J_{\mathrm{id}})=\int_{\mathrm{Int}(M)} h=\int_{M} h
\end{gather}
$$

为了联系 $n-1$ 形式的积分和 $n$-形式的积分，我们还需要明确 $\partial M$ 的诱导定向。我们在第二节中考虑了 $n=3$ 的情况，下面我们将其推广至一般情况：

**引理 4.5.7**

设 $M$ 是 $\mathbb{R}^{n}$ 上的 $n$-流形，取自然定向，则对应于 $\partial M$ 的诱导定向的单位法向量 $N$ 指向 $\partial M$ 的外法线方向。

我们说 $p \in \partial M$ 的**内法线方向**是指这样一条曲线 $\alpha(t)$ 的速度向量方向：它以 $p$ 为起点，并且当 $t$ 增大时，$\alpha(t)$ 进入 $M$ 的内部。而 $p$ 的**外法线方向**则是内法线方向的反向。

**证明**

设 $\alpha\colon U\to V$ 是 $p$ 处属于自然定向的坐标卡，则 $\det\alpha'>0$. 令 $b\colon \mathbb{R}^{n-1}\to \mathbb{R}^{n}$ 定义为

$$
\begin{gather}
b(x_{1},\dots,x_{n-1})=(x_{1},\dots,x_{n-1},0)
\end{gather}
$$

则 $\alpha_{0}=\alpha \circ b$ 是 $p$ 处关于 $\partial M$ 的坐标卡。它属于 $\partial M$ 的诱导定向如果 $n$ 是偶数，属于诱导定向的反定向如果 $n$ 是奇数。令 $N(p)=(p;n)$ 为对应于诱导定向的单位法向量场，则

$$
\begin{gather}
(-1)^{n}\det\left[ n, J_{\alpha_{0}}  \right]>0
\end{gather}
$$

这表明

$$
\begin{gather}
\det[J_{\alpha_{0}},n]=\det\left[ \dfrac{ \partial \alpha }{ \partial x_{1} } ,\dots,\dfrac{ \partial \alpha }{ \partial x_{n-1} } ,n \right]<0
\end{gather}
$$

另一方面，我们有

$$
\begin{gather}
\det J_{\alpha}=\det\left[ \dfrac{ \partial \alpha }{ \partial x_{1} } ,\dots,\dfrac{ \partial \alpha }{ \partial x_{n} }  \right]>0
\end{gather}
$$

而 $\dfrac{ \partial \alpha }{ \partial x_{n} }$ 指向 $p$ 处的内法线方向，因此 $n$ 指向 $p$ 的外法线方向。

**定理 4.5.8** Gauss 散度定理（Gauss' divergence theorem）

设 $M$ 是 $\mathbb{R}^{n}$ 中的 $n$-流形，令 $N$ 为 $\partial M$ 上指向外法线方向的单位法向量场。如果 $G$ 是定义在 $\mathbb{R}^{n}$ 中包含 $M$ 的开集上的向量场，则

$$
\begin{gather}
\int_{M} (\mathrm{div}\ G) \mathrm{d} V=\int_{\partial M} \langle G,N \rangle \mathrm{d} V
\end{gather}
$$

其中左侧是关于 $n$-体积的积分，右侧是关于 $n-1$ 体积的积分。

**证明**

给定向量场 $G$，令 $\omega=\beta_{n-1}G$ 为其对应的 $n-1$ 形式。给予 $M$ 自然定向，则法向量场 $N$ 对应于 $\partial M$ 上的诱导定向，因此

$$
\begin{gather}
\int_{\partial M} \omega=\int_{\partial M} \langle G,N \rangle \mathrm{d} V
\end{gather}
$$

另一方面，根据定理 3.3.2，形式 $\mathrm{d}\omega$ 对应于标量场 $\mathrm{div}\ G$，也就是说，$\mathrm{d}\omega=(\mathrm{div}\ G)\mathrm{d}x_{1}\land\dots \land \mathrm{d}x_{n}$，因此我们有

$$
\begin{gather}
\int_{M} \mathrm{d} \omega=\int_{M} (\mathrm{div}\ G) \mathrm{d} V
\end{gather}
$$

根据 Stokes 定理即证。

最后还剩下一种情况，其中我们可以将 Stokes 定理转化成关于向量场的定理。那就是 $\mathbb{R}^{3}$ 中定向 $2$-流形上的旋度定理，它也是 Stokes 定理的原本形式。

**定理 4.5.9** Stokes 定理（经典版本）

设 $M$ 是 $\mathbb{R}^{3}$ 上的紧致定向 $2$-流形，$N$ 是对应于 $M$ 的定向的单位法向量场。令 $F$ 是定义在 $\mathbb{R}^{3}$ 中包含 $M$ 的开集上的向量场。如果 $\partial M=\varnothing$，则

$$
\begin{gather}
\int_{M} \langle \mathrm{curl}\ F,N \rangle \mathrm{d} S=0
\end{gather}
$$

反之，则令 $T$ 为 $\partial M$ 上的单位切向量场，使得 $W(p)=N(p)\times T(p)$ 从 $p \in \partial M$ 处指向 $M$ 的内部，那么有

$$
\begin{gather}
\int_{M} \langle \mathrm{curl}\ F,N \rangle \mathrm{d} S=\int_{\partial M} \langle F,T \rangle \mathrm{d} s
\end{gather}
$$

**证明**

给定向量场 $F$，令 $\omega=\alpha_{1}F$ 为对应的 $1$-形式，则根据定理 3.3.4，向量场 $\mathrm{curl}\ F$ 对应于 $2$-形式 $\mathrm{d}\omega$. 根据引理 4.5.5，我们有

$$
\begin{gather}
\int_{M} \mathrm{d} \omega=\int_{M} \langle \mathrm{curl}\ F,N \rangle \mathrm{d} S
\end{gather}
$$

另一方面，如果 $\partial M\neq \varnothing$，则 $T$ 就是对应于诱导定向的单位切向量场，从而有

$$
\begin{gather}
\int_{\partial M} \omega=\int_{\partial M} \langle F,T \rangle \mathrm{d} s
\end{gather}
$$

根据 Stokes 定理即证。

最后我们给出一个注记：尽管在本章中我们假设定理中出现的流形、微分形式、向量场均为 $C^{\infty}$ 连续的，但实际上它们的光滑性均可以降低至 $C^{1}$ 而无需对证明做出任何改变。这是因为在这些定理的证明过程中我们只使用了一次微分，而 $C^{0}$ 函数在紧致集上是可积的。这些性质保证了 $C^{1}$ 连续性的条件是完全充分的，而假定 $C^{\infty}$ 连续性只是为了行文的方便。