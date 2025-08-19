上一章我们证明了 Radon-Nikodym 定理，它提供了一个符号测度或者复测度 $\nu$ 关于一个正测度 $\mu$ 的“导数”的概念。在本章中，我们将着重研究当 $\mu$ 是 $\mathbb{R}^{n}$ 上的 Lebesgue 测度 $m$ 时的情况，当 $n=1$ 时，本章的讨论就可以结合一元微分学的内容，给出关于 Lebesgue 积分的微积分基本定理。

# Section 1: Lebesgue 微分定理

与一般的测度不同，在 $\mathbb{R}^{n}$ 上我们可以定义 $\nu$ 关于 $m$ 的“逐点导数”，即极限

$$
F(x)=\lim_{ r \to 0 } \dfrac{\nu(B(x,r))}{m(B(x,r))}
$$

如果 $\nu\ll m$，那么根据 Radon-Nikodym 定理知存在 $f$ 使得 $\mathrm{d}\nu=f\mathrm{d}m$，于是有

$$
F(x)=\lim_{ r \to 0 } \dfrac{1}{m(B(x,r))} \int_{B(x,r)} f(y)\mathrm{d} y
$$

也就是说，$F$ 是 $B(x,r)$ 上 $f$ 的平均值，那么我们自然会期望 $F=f$ a.e.，作为微积分基本定理的一个体现：积分的导数是函数自身。事实证明，如果对任意 $x,r$ 都有 $\nu(B(x,r))$ 是有限的，那么上述断言就是成立的。

下面我们来着手证明本节的主定理，即 Lebesgue 微分定理，首先我们给出一个引理：

**引理 24.1.1**

设 $\mathcal{C}$ 是 $\mathbb{R}^{n}$ 上的开球组成的集合，$U=\bigcup \mathcal{C}$，如果 $c<m(U)$，那么存在不相交的开球 $B_{1},\dots,B_{k}\in \mathcal{C}$ 使得 $\sum_{j=1}^{k}m(B_{j})>3^{-n}c$.

**证明**

如果 $c<m(U)$，根据定理 22.3.1 知存在紧致集 $K\subset U$ 使得 $m(K)>c$，设开球 $A_{1},\dots,A_{m}$ 覆盖 $K$，令 $B_{1}$ 是 $A_{j}$ 中半径最大的，$B_{2}$ 是与 $B_{1}$ 不相交的 $A_{j}$ 中半径最大的，$B_{3}$ 是与 $B_{1},B_{2}$ 不相交的 $A_{j}$ 中半径最大的，以此类推，得到了开球 $B_{1},\dots,B_{k}$.

设 $A_{i}$ 不是任意一个 $B_{j}$，那么存在 $B_{j}$ 使得 $A_{i}\cap B_{j}\neq \varnothing$，令 $j$ 为满足这一条件的最小整数，那么 $A_{i}$ 的半径必定小于等于 $B_{j}$ 的半径，从而令 $B_{j}^{*}$ 为与 $B_{j}$ 有相同中心，半径为 $B_{j}$ 的三倍的开球，则 $A_{i}\subset B_{j}^{*}$. 因此，$B_{1}^{*},\dots,B_{k}^{*}$ 覆盖了所有 $A_{i}$，进而覆盖了 $K$，从而有

$$
c<m(K)< \sum_{j=1}^{k} m(B_{j}^{*})= 3^{n} \sum_{j=1}^{k} m(B_{j})
$$

即证。

**定义 24.1.2** 局部可积的（locally integrable）

一个可测函数 $f\colon \mathbb{R}^{n}\to \mathbb{C}$ 是**局部可积的**，如果对任意有界可测集 $K$ 都有 $\int_{K}|f|\mathrm{d}m<+\infty$. 所有 $\mathbb{R}^{n}$ 上局部可积函数构成的集合记作 $L^{1}_{\mathrm{loc}}(\mathbb{R}^{n})$.

对于 $f \in L_{\mathrm{loc}}^{1}(\mathbb{R}^{n})$，我们可以定义平均函数

$$
A_{r}f(x)= \dfrac{1}{m(B(x,r))} \int_{B(x,r)} f(y)\mathrm{d} y
$$

并且我们有：

**引理 24.1.3**

如果 $f \in L_{\mathrm{loc}}^{1}(\mathbb{R}^{n})$，那么 $A_{r}f(x)$ 作为 $\mathbb{R}^{n}\times(0,+\infty)$ 上的函数是连续的。

**证明**

根据 22.4 中的结论，我们有 $m(B(x,r))=c r^{n}$，其中 $c=m(B(0,1))$，并且对于 $S(x,r)=\{ y \in \mathbb{R}^{n} \mid \lVert y-x \rVert=r \}$ 有 $m(S(x,r))=0$. 此外，当 $x\to x_{0}$，$r\to r_{0}$ 时，$\chi_{B(x,r)}$ 在 $\mathbb{R}^{n}\setminus S(x_{0},r_{0})$ 上逐点收敛于 $\chi_{B(x_{0},r_{0})}$，从而 $\chi_{B(x,r)}$ 几乎处处收敛于 $\chi_{B(x_{0},r_{0})}$.

此外，我们有 $|\chi_{B(x,r)}|\leq \chi_{B(x_{0},r_{0}+1)}$，其中 $r<r_{0}+1 / 2$，$\lVert x-x_{0} \rVert<1 / 2$，根据控制收敛定理，关于 $x$ 和 $r$ 的函数 $\int_{B(x,r)}f(y)\mathrm{d}y$ 是连续的，从而函数 $A_{r}f(x)=c^{-1}r^{-n}\int_{B(x,r)}f(y)\mathrm{d}y$ 也是连续的。

根据该引理，我们可以定义：

**定义 24.1.4** Hardy-Littlewood 极大函数（Hardy-Littlewood maximal function）

设 $f \in L_{\mathrm{loc}}^{1}(\mathbb{R}^{n})$，定义 $f$ 的 **Hardy-Littlewood 极大函数**为

$$
Hf(x)=\sup_{r>0} A_{r}|f|(x)=\sup_{r>0} \dfrac{1}{m(B(x,r))}\int_{B(x,r)}|f(y)|\mathrm{d} y
$$

由于 $A_{r}|f|(x)$ 是连续的，故 $Hf^{-1}[(a,+\infty)]=\bigcup_{r>0}(A_{r}|f|)^{-1}[(a,+\infty)]$ 是开集，从而 $Hf$ 是可测函数。

**定理 24.1.5** 极大定理（maximal theorem）

存在实数 $C>0$ 使得对任意 $f \in L^{1}(\mathbb{R}^{n},m)$ 和 $\alpha>0$ 有

$$
m(\{ x \in \mathbb{R}^{n} \mid Hf(x)>\alpha \})\leq \dfrac{C}{\alpha} \int |f(y)|\mathrm{d} y
$$

**证明**

设 $E_{\alpha}=\{ x \mid Hf(x)>\alpha \}$，则对任意 $x \in E_{\alpha}$ 有 $r_{x}>0$ 使得 $A_{r_{x}}|f|(x)>\alpha$. 所有开球 $B(x,r_{x})$ 覆盖了 $E_{\alpha}$，因此根据引理 24.1.1，对任意 $c<m(E_{\alpha})$，存在 $x_{1},\dots,x_{k}$ 使得各 $B_{j}=B(x_{j},r_{x_{j}})$ 不相交且 $\sum_{j=1}^{k}m(B_{j})>3^{-n}c$，从而有

$$
c< 3^{n} \sum_{j=1}^{k} m(B_{j})\leq \dfrac{3^{n}}{\alpha} \sum_{j=1}^{k} \int_{B_{j}} |f(y)|\mathrm{d} y\leq \dfrac{3^{n}}{\alpha} \int |f(y)|\mathrm{d} y
$$

由于上式对任意 $c<m(E_{\alpha})$ 都成立，因此也对 $m(E_{\alpha})$ 成立，这就完成了证明。

有了这样一个工具，我们现在就可以来给出本节的基本微分定理。在证明过程中我们需要用到**上极限**的概念：

$$
\limsup_{ r \to R } \phi(r)=\lim_{ \delta \to 0 } \sup_{0<\lVert r-R \rVert <\delta} \phi(r)=\inf_{\delta>0} \sup_{0<\lVert r-R \rVert <\delta}\phi(r)
$$

并且我们可以验证

$$
\lim_{ r \to R } \phi(r)=c \iff \limsup_{ r \to R } |\phi(r)-c|=0
$$

**引理 24.1.6**

如果 $f \in L_{\mathrm{loc}}^{1}(\mathbb{R}^{n})$，那么对 a.e. $x$ 有 $\lim_{ r \to 0 }A_{r}f(x)=f(x)$.

**证明**

我们只需证明对任意 $N \in \mathbb{N}$ 和 $\lVert x \rVert\leq N$ 有 $\lim_{ r \to 0 }A_{r}f(x)=f(x)$ a.e.，但当 $\lVert x \rVert\leq N$ 和 $r\leq 1$ 时 $A_{r}f(x)$ 的值只和 $f(y),\lVert y \rVert\leq N+1$ 有关，因此通过把 $f$ 换成 $f \chi_{B(0,N+1)}$，我们可以假设 $f \in L^{1}(\mathbb{R}^{n})$.

任取 $\varepsilon>0$，根据定理 22.3.2 可知存在连续函数 $g$ 使得 $\int|g-f|\mathrm{d}m<\varepsilon$，连续性表明对任意 $x \in \mathbb{R}^{n}$ 和 $\delta>0$，存在 $r>0$ 使得对任意 $\lVert y-x \rVert<r$ 的 $y$ 有 $|g(y)-g(x)|<\delta$，从而

$$
|A_{r}g(x)-g(x)|= \dfrac{1}{m(B(x,r))} \left\lvert  \int_{B(x,r)} (g(y)-g(x))\mathrm{d} y  \right\rvert <\delta
$$

因此对任意 $x$ 有 $\lim_{ r \to 0 }A_{r}g(x)=g(x)$，于是

$$
\begin{align}
&\limsup_{ r \to 0 } |A_{r}f(x)-f(x)| \\
&= \limsup_{ r \to 0 } |A_{r}(f-g)(x)+(A_{r}g-g)(x)+(g-f)(x)| \\
&\leq H(f-g)(x)+ |f-g|(x)
\end{align}
$$

令

$$
E_{\alpha}=\{ x \mid \limsup_{ r \to 0 } |A_{r}f(x)-f(x)|>\alpha \}, F_{\alpha}=\{ x \mid |f-g|(x)>\alpha \}
$$

则有

$$
E_{\alpha}\subset F_{\alpha / 2} \cup \{ x \mid H(f-g)(x)>\alpha / 2 \}
$$

根据极大定理我们有

$$
m(\{ x \mid H(f-g)(x)>\alpha / 2 \})\leq \dfrac{2C}{\alpha} \int |f-g|\mathrm{d} m< \dfrac{2C}{\alpha}\varepsilon
$$

此外，我们也有

$$
\dfrac{\alpha}{2} m(F_{\alpha / 2})\leq \int_{F_{\alpha / 2}} |f-g|\mathrm{d} m< \varepsilon
$$

从而 $m(E_{\alpha})<\left(  \dfrac{2+2C}{\alpha} \right)\varepsilon$，根据 $\varepsilon$ 的任意性得 $m(E_{\alpha})=0$. 又由于当 $x \not\in \bigcup_{n=1}^{\infty}E_{1 / n}$ 时有 $\limsup_{ r \to 0 }|A_{r}f(x)-f(x)|=0$，这就完成了证明。

下面，我们要将上述结论进行优化，首先我们注意到上述定理可以写成

$$
\lim_{ r \to 0 } \dfrac{1}{m(B(x,r))}\int_{B(x,r)}(f(y)-f(x))\mathrm{d} y=0 \quad \text{a.e.}\ x
$$

事实上，我们可以将上述积分中的式子换成它的绝对值，我们有如下定义：

**定义 24.1.7** Lebesgue 集

设 $f \in L_{\mathrm{loc}}^{1}(\mathbb{R}^{n})$，定义其 **Lebesgue 集**为

$$
L_{f}=\left\{  x \in \mathbb{R}^{n} \middle| \lim_{ r \to 0 } \dfrac{1}{B(x,r)}\int_{B(x,r)} |f(y)-f(x)|\mathrm{d} y=0  \right\}
$$

**引理 24.1.8**

如果 $f \in L_{\mathrm{loc}}^{1}(\mathbb{R}^{n})$，那么 $m((L_{f})^{c})=0$.

**证明**

对任意 $c \in \mathbb{C}$，将引理 24.1.6 应用到函数 $g_{c}(x)=|f(x)-c|$ 上，则除了一个零测集 $E_{c}$ 外，我们都有

$$
\lim_{ r \to 0 } \dfrac{1}{m(B(x,r))}\int_{B(x,r)} |f(y)-c|\mathrm{d} y= |f(x)-c|
$$

令 $D=\{ p+iq \mid p,q \in \mathbb{Q} \}$，则 $D$ 是 $\mathbb{C}$ 的可数稠密子集，设 $E=\bigcup_{c \in D}E_{c}$，则 $m(E)=0$，并且对任意 $x \not\in E$ 和 $\varepsilon>0$，存在 $c \in D$ 使得 $|f(x)-c|<\varepsilon$，于是 $|f(y)-f(x)|\leq |f(y)-c|+\varepsilon$，从而

$$
\limsup_{ r \to 0 } \dfrac{1}{m(B(x,r))}\int_{B(x,r)} |f(y)-f(x)| \mathrm{d} y\leq |f(x)-c|+\varepsilon<2\varepsilon
$$

根据 $\varepsilon$ 的任意性就完成了证明。

最后，我们可以考虑在比开球更加广泛的集合上求均值，但这些集合必须在某种程度上与开球是“相似”的，更精确地说，就是：

**定义 24.1.9** 均匀收缩（shrink nicely）

设 $E_{r}\subset \mathbb{R}^{n}$ 是 Borel 集，称集族 $\{ E_{r} \}_{r>0}$ **均匀收缩至** $x \in \mathbb{R}^{n}$，如果：

1. 对任意 $r>0$ 有 $E_{r}\subset B(x,r)$
2. 存在 $\alpha>0$，对任意 $r>0$ 有 $m(E_{r})>\alpha m(B(x,r))$

现在，我们就可以给出本节的主定理。

**定理 24.1.10** Lebesgue 微分定理（Lebesgue differentiation theorem）

设 $f \in L_{\mathrm{loc}}^{1}(\mathbb{R}^{n})$，则对任意 $x \in L_{f}$（特别地，对 a.e. $x$）有

$$
\lim_{ r \to 0 } \dfrac{1}{m(E_{r})}\int_{E_{r}}|f(y)-f(x)|\mathrm{d} y=0
$$

其中 $\{ E_{r} \}_{r>0}$ 均匀收缩至 $x$.

**证明**

根据定义，存在 $\alpha>0$ 使得

$$
\begin{align}
\dfrac{1}{m(E_{r})}\int_{E_{r}}|f(y)-f(x)|\mathrm{d} y &\leq \dfrac{1}{m(E_{r})}\int_{B(x,r)}|f(y)-f(x)|\mathrm{d} y \\
&\leq \dfrac{1}{\alpha m(B(x,r))}\int_{B(x,r)}|f(y)-f(x)|\mathrm{d} y
\end{align}
$$

根据引理 24.1.8 即证。

下面，我们要将上一章的 Lebesgue-Radon-Nikodym 定理与 Lebesgue 微分定理结合起来。首先我们给出一个概念。

**定义 24.1.11** 正则的（regular）

$\mathbb{R}^{n}$ 上的 Borel 测度 $\nu$ 是**正则的**，如果：

1. 对任意紧致集 $K$ 都有 $\nu(K)<+\infty$
2. 对任意 Borel 集 $E$ 有 $\nu(E)=\inf\{ \nu(U) \mid U\supset E,U\text{是开集} \}$

一个 Borel 符号测度或复测度 $\nu$ 是正则的，如果 $|\nu|$ 是正则的。

显然，Lebesgue 测度 $m$ 是正则的，并且我们可以验证正则测度一定是 $\sigma$-有限的。

**引理 24.1.12**

如果 $\lambda,\mu$ 是 $\mathbb{R}^{n}$ 上互异的 Borel 测度，并且 $\lambda+\mu$ 是正则的，那么 $\lambda$ 和 $\mu$ 也是正则的。

**证明**

设 $K\subset \mathbb{R}^{n}$ 是紧致的，则 $(\lambda+\mu)(K)<+\infty$，由于 $\lambda\leq \lambda+\mu$，$\mu\leq\lambda+\mu$，故 $\lambda(K)<+\infty,\mu(K)<+\infty$. 现设 $E\subset \mathbb{R}^{n}$ 是 Borel 集，则对任意 $\varepsilon>0$ 都有开集 $U\supset E$ 使得 $(\lambda+\mu)(U)<(\lambda+\mu)(E)+\varepsilon$. 

设 $\mathbb{R}^{n}=P\cup Q,P\cap Q=\varnothing$，并且 $\lambda(Q)=0,\mu(P)=0$，取 $E\subset P$ 是 Borel 集，则有开集 $U\supset E$ 使得 $\lambda(U)\leq(\lambda+\mu)(U)<\lambda(E)+\varepsilon$，从而 $\lambda$ 是正则的，同理 $\mu$ 也是正则的，即证。

**引理 24.1.13**

设 $f\colon \mathbb{R}^{n}\to[0,+\infty]$ 是可测的，那么测度 $f\mathrm{d}m$ 是正则的当且仅当 $f \in L_{\mathrm{loc}}^{1}$.

**证明**

条件 $f \in L_{\mathrm{loc}}^{1}$ 等价于对任意紧致集 $K$ 都有 $\int_{K}|f|\mathrm{d}m<+\infty$，即正则性的条件 1，而条件 2 可以从 1 中推导出来：设 $E$ 是一个有界的 Borel 集，根据 $m$ 的正则性知对任意 $\delta>0$ 有开集 $U\supset E$ 使得 $m(U)<m(E)+\delta$，从而 $m(U\setminus E)<\delta$.

于是，由定理 23.2.4 知对任意 $\varepsilon>0$，存在开集 $U\supset E$ 使得

$$
\int_{U\setminus E}f\mathrm{d} m=\int_{U}f\mathrm{d} m-\int_{E}f\mathrm{d} m<\varepsilon
$$

这就完成了 $E$ 是有界集合情况下的证明。当 $E$ 是无界 Borel 集时，由 $m$ 的 $\sigma$-有限性，我们可以找到有界集 $E_{j}$ 使得 $E=\bigcup_{j=1}^{\infty}E_{j}$，对每个 $E_{j}$，我们可以找到开集 $U_{j}\supset E_{j}$ 使得 $m(U_{j})<m(E_{j})+\varepsilon 2^{-j}$，取 $U=\bigcup_{j=1}^{\infty}U_{j}$，则有 $m(U)<m(E)+\varepsilon$，这就完成了证明。

**定理 24.1.14**

设 $\nu$ 是 $\mathbb{R}^{n}$ 上正则的 Borel 符号测度或复测度，$\mathrm{d}\nu=\mathrm{d}\lambda+f\mathrm{d}m$ 是其 Lebesgue-Radon-Nikodym 分解，那么对 $m$-a.e. $x$ 有

$$
\lim_{ r \to 0 } \dfrac{\nu(E_{r})}{m(E_{r})}=f(x)
$$

其中 $\{ E_{r} \}_{r>0}$ 均匀收缩至 $x$.

**证明**

我们很容易验证 $\mathrm{d}|\nu|=\mathrm{d}|\lambda|+|f|\mathrm{d}m$，于是根据引理 24.1.12，$\lambda$ 和 $f\mathrm{d}m$ 是正则的，于是 $f \in L_{\mathrm{loc}}^{1}(\mathbb{R}^{n})$，根据 Lebesgue 微分定理，我们只需证明对 a.e. $x$ 有 $\lim_{ r \to 0 } \dfrac{\lambda(E_{r})}{m(E_{r})}=0$. 此外，我们还可以假设 $E_{r}=B(x,r)$ 且 $\lambda$ 是正测度，因为

$$
\left\lvert  \dfrac{\lambda(E_{r})}{m(E_{r})}  \right\rvert \leq \dfrac{|\lambda|(E_{r})}{m(E_{r})}\leq \dfrac{|\lambda|(B(x,r))}{\alpha m(B(x,r))}
$$

由于 $\lambda \perp m$，故存在 Borel 集 $A$ 使得 $\lambda(A)=m(A^{c})=0$，令

$$
F_{k}=\left\{ x \in A \middle| \limsup_{ r \to 0 } \dfrac{\lambda(B(x,r))}{m(B(x,r))}> \dfrac{1}{k} \right\} 
$$

我们要证对任意 $k$ 有 $m(F_{k})=0$，于是就有 $\lim_{ r \to 0 } \dfrac{\lambda(E_{r})}{m(E_{r})}=0$ a.e. $x$.

根据 $\lambda$ 的正则性，对任意 $\varepsilon>0$，存在开集 $U\supset A$ 使得 $\lambda(U)<\varepsilon$，并且对每个 $x \in F_{k}$ 都有开球 $B_{x}\subset U$ 使得 $\lambda(B_{x})> \dfrac{1}{k}m(B_{x})$. 根据引理 24.1.1，设 $V=\bigcup_{x \in F_{k}}B_{x}$，如果 $c<m(V)$，则存在 $x_{1},\dots,x_{J}$ 使得 $B_{x_{1}},\dots,B_{x_{J}}$ 是不相交的，并且

$$
c<3^{n} \sum_{j=1}^{J} m(B_{x_{j}})<3^{n}k \sum_{j=1}^{J} \lambda(B_{x_{j}})\leq 3^{n}k \lambda(V)\leq 3^{n}k\lambda(U)<3^{n}k\varepsilon
$$

于是 $m(V)<3^{n}k\varepsilon$，由于 $F_{k}\subset V$，由 $\varepsilon$ 的任意性知 $m(F_{k})=0$，这就完成了证明。

# Section 2: 有界变差函数

现在，我们将上一节的理论应用到 $\mathbb{R}$ 上的 Borel 测度上，因为我们在定理 20.4.2 中建立了递增函数 $F$ 与 Borel 测度 $\mu_{F}$ 之间的一一对应，故我们得到的关于测度的结论可以被转化为关于函数 $F$ 的微分学性质。我们的第一个结论就与递增函数的 a.e. 可微性有关。

**定理 24.2.1**

设 $F\colon \mathbb{R}\to \mathbb{R}$ 是递增函数，$G(x)=F(x+)$，则：

1. $F$ 的间断点构成的集合是至多可数的。
2. $F$ 和 $G$ 是 a.e. 可微的，并且 $F'=G'$ a.e.

**证明**

由于 $F$ 是递增的，故区间 $(F(x-),F(x+))$ 是不相交的，取有理数 $q \in(F(x-),F(x+))$，则我们就有 $\{ x \mid F(x-)<F(x+) \}$ 到 $\mathbb{Q}$ 的单射，因此 $F$ 的间断点构成的集合是至多可数的。

下面我们首先观察到 $G$ 是递增且右连续的，并且在 $F$ 的连续点处有 $G=F$. 此外，根据定理 20.4.2 有

$$
G(x+h)-G(x)=\begin{cases}
\mu_{G}((x,x+h]) &, h\geq 0 \\
-\mu_{G}((x+h,x]) &, h<0
\end{cases}
$$

并且集族 $\{ (x,x+r] \},\{ (x-r,x] \},r=|h|$ 均匀收缩至 $x$，因此将定理 24.1.14 应用到正则测度 $\mu_{G}$ 上，即得 $G'$ 对 a.e. $x$ 都存在。下面我们要证函数 $H=G-F$ 对 a.e. $x$ 都有 $H'=0$.

设 $(x_{j})_{j=1}^{\infty}$ 表示满足 $H\neq 0$ 的点，于是 $H(x_{j})>0$，并且我们有

$$
\sum_{|x_{j}|<N} H(x_{j})\leq \sum_{|x_{j}|<N} (F(x_{j}+)-F(x_{j}-))\leq F(N)-F(-N)<+\infty
$$

对任意 $N$ 都成立。定义 $x_{j}$ 处的**点质量测度**为

$$
\delta_{j}(A)=\begin{cases}
0 &, x_{j}\not\in A \\
1 &, x_{j} \in A
\end{cases}
$$

令 $\mu=\sum_{j=1}^{\infty}H(x_{j})\delta_{j}$，于是 $\mu$ 在紧致集上有限，从而根据定理 20.4.2 和 20.4.5 得 $\mu$ 是正则的。此外，$\mu \perp m$，因为 $m(\{ x_{j} \})=\mu(\{ x_{j} \}^{c})=0$，并且有

$$
\left\lvert  \dfrac{H(x+h)-H(x)}{h}  \right\rvert \leq \dfrac{H(x+h)+H(x)}{|h|}\leq 4 \dfrac{\mu((x-2|h|,x+2|h|))}{4|h|}
$$

根据定理 24.1.14，对 a.e. $x$，当 $h\to 0$ 时上式也趋于零，即 $H'=0$ a.e.，这就完成了证明。

上述定理表明，每个递增函数都与一个递增且右连续的函数关联，从而也和一个 $\mathbb{R}$ 上的正测度关联。类似地，与 $\mathbb{R}$ 上的复测度关联的，就是所谓的**有界变差函数**。

**定义 24.2.2** 总变差函数（total variation function）

设 $F\colon \mathbb{R}\to \mathbb{C}$，定义 $F$ 的**总变差函数** $T_{F}\colon \mathbb{R}\to [0,+\infty]$ 为

$$
T_{F}(x)=\sup \left\{  \sum_{j=1}^{n} |F(x_{j})-F(x_{j-1})| \middle| n\geq 1,-\infty<x_{0}<\dots<x_{n}=x  \right\}
$$

根据三角不等式，我们可以发现，如果我们增加划分点 $x_{j}$ 的数量，那么求和 $\sum_{j=1}^{n}|F(x_{j})-F(x_{j-1})|$ 的值将会增大，因此，如果 $a<b$，且 $a$ 总是划分点之一，那么 $T_{F}(b)$ 的定义不会有任何改变，从而我们有

$$
\begin{align}
& T_{F}(b)-T_{F}(a) \\
&= \sup \left\{  \sum_{j=1}^{n} |F(x_{j})-F(x_{j-1})| \middle| n\geq 1, a=x_{0}<\dots<x_{n}=b  \right\}
\end{align}
$$

因此，$T_{F}$ 是一个递增函数。下面我们给出有界变差的定义。

**定义 24.2.3** 有界变差函数（function of bounded variation）

设 $F\colon \mathbb{R}\to \mathbb{C}$，称 $F$ 在 $\mathbb{R}$ 上具有**有界变差**，如果 $T_{F}(+\infty)$ 是有限的. 所有 $\mathbb{R}$ 上的有界变差函数构成的集合记作 $BV$.

设实数 $a<b$，定义

$$
\sup \left\{  \sum_{j=1}^{n} |F(x_{j})-F(x_{j-1})| \middle| n\geq 1, a=x_{0}<\dots<x_{n}=b  \right\}
$$

为 $F$ 在 $[a,b]$ 上的**总变差**。称 $F$ 在 $[a,b]$ 上具有有界变差，如果 $F$ 在 $[a,b]$ 上的总变差是有限的。$[a,b]$ 上的有界变差函数构成的集合记作 $BV([a,b])$.

对于 $F \in BV$，将 $F$ 限制在 $[a,b]$ 上就有 $F \in BV([a,b])$，因为 $F$ 在 $[a,b]$ 上的总变差就是 $T_{F}(b)-T_{F}(a)$. 另一方面，如果 $F \in BV([a,b])$，那么如果我们令

$$
F^{*}(x)=\begin{cases}
F(a) &, x<a \\
F(x) &, a\leq x\leq b \\
F(b) &, x>b
\end{cases}
$$

那么 $F^{*}\in BV$. 因此，所有关于 $BV$ 的结论都可以应用到 $BV([a,b])$ 上。

下面我们给出有界变差函数的一些基本性质。

**定理 24.2.4**

1. 如果 $F\colon \mathbb{R}\to \mathbb{R}$ 是有界且递增，那么 $F \in BV$
2. 如果 $F,G \in BV$ 且 $a,b \in \mathbb{C}$，则 $aF+bG \in BV$
3. 如果 $F$ 在 $\mathbb{R}$ 上可微并且 $F'$ 是有界的，那么 $F \in BV([a,b])$

**证明**

(1). 设 $-\infty<x_{0}<\dots<x_{n}<+\infty$，则

$$
\sum_{j=1}^{n} |F(x_{j})-F(x_{j-1})|=\sum_{j=1}^{n} (F(x_{j})-F(x_{j-1}))=F(x_{n})-F(x_{0})
$$

于是 $T_{F}(x)=F(x)-F(-\infty)$，根据 $F$ 的有界性得 $T_{F}(+\infty)<+\infty$.

(2). 设 $F \in BV$，则有 $T_{aF}(x)=|a|T_{F}(x)$，故 $aF \in BV$. 再设 $G \in BV$，则有

$$
|(F+G)(x_{j})-(F+G)(x_{j-1})|\leq |F(x_{j})-F(x_{j-1})|+ |G(x_{j})-G(x_{j-1})|
$$

于是 $T_{F+G}(x)\leq T_{F}(x)+T_{G}(x)$，从而 $F+G \in BV$.

(3). 设对任意 $x \in \mathbb{R}$ 有 $|F'(x)|\leq M$，于是对 $a=x_{0}<\dots<x_{n}=b$ 有

$$
\sum_{j=1}^{n} |F(x_{j})-F(x_{j-1})|=\sum_{j=1}^{n} |F'(\xi_{j})|(x_{j}-x_{j-1})\leq M(b-a)
$$

因此 $F \in BV([a,b])$，即证。

在符号测度的 Jordan 分解定理中，我们也使用了“变差”这个术语，这两者之间有什么关系呢？下面我们来说明这一点。

**引理 24.2.5**

如果 $F\colon \mathbb{R}\to \mathbb{R}$ 具有有界变差，则函数 $T_{F}+F$ 和 $T_{F}-F$ 都是递增的。

**证明**

设 $x<y,\varepsilon>0$，取 $x_{0}<\dots<x_{n}=x$ 使得

$$
\sum_{j=1}^{n} |F(x_{j})-F(x_{j-1})|> T_{F}(x)-\varepsilon
$$

于是 $\sum_{j=1}^{n}|F(x_{j})-F(x_{j-1})|+|F(y)-F(x)|$ 就是 $T_{F}(y)$ 的一个近似，从而

$$
\begin{align}
T_{F}(y)\pm F(y) &\geq \sum_{j=1}^{n} |F(x_{j})-F(x_{j-1})|+|F(y)-F(x)| \\
&\pm (F(y)-F(x)) \pm F(x) \\
&\geq T_{F}(x)-\varepsilon \pm F(x)
\end{align}
$$

根据 $\varepsilon$ 的任意性即得 $T_{F}\pm F$ 是递增函数。

**定理 24.2.6**

1. $F \in BV$ 当且仅当 $\mathrm{Re}\ F \in BV$ 且 $\mathrm{Im}\ F \in BV$
2. 如果 $F\colon \mathbb{R}\to \mathbb{R}$，那么 $F \in BV$ 当且仅当 $F$ 是两个有界递增函数的差，特别地，这两个函数可以取为 $\dfrac{1}{2}(T_{F}+F)$ 和 $\dfrac{1}{2}(T_{F}-F)$
3. 如果 $F \in BV$，那么对任意 $x$，$F(x+),F(x-)$ 和 $F(\pm \infty)$ 都存在。
4. 如果 $F \in BV$，那么 $F$ 的间断点构成的集合是至多可数的。
5. 如果 $F \in BV$，$G(x)=F(x+)$，那么 $F'=G'$ a.e.

**证明**

1 是显然的。如果 $F\colon \mathbb{R}\to \mathbb{R},F \in BV$，那么显然 $F$ 是有界的，并且根据引理 24.2.5，$F$ 是两个有界递增函数的差。反之，根据定理 24.2.4，有界递增函数具有有界变差，从而 $F \in BV$.

对于 3，将 $F$ 写成两个递增函数的差，对于递增函数 $f$，我们有

$$
f(x+)=\inf_{y>x} f(y), f(x-)=\sup_{y<x} f(y)
$$

从而 $F(x+),F(x-)$ 都存在，同理 $F(\pm \infty)$ 也存在。类似地，将 $F$ 写成两个递增函数的差，然后应用定理 24.2.1 即证 4 和 5.

等式 $F= \dfrac{1}{2}(T_{F}+F)- \dfrac{1}{2}(T_{F}-F)$ 称为 $F$ 的 **Jordan 分解**，相应地，$\dfrac{1}{2}(T_{F}+F)$ 和 $\dfrac{1}{2}(T_{F}-F)$ 分别称为 $F$ 的**正变差**和**负变差**。

通过 Jordan 分解，我们可以看到有界变差函数与复测度之间的关联，为了精确表述这一关系，我们定义（N 表示 normalized，即归一化）

$$
NBV=\{ F \in BV \mid F\text{右连续}, F(-\infty)=0 \}
$$

我们可以验证，如果 $F \in BV$，那么定义为 $G(x)=F(x+)-F(-\infty)$ 的函数 $G \in NBV$，并且 $F'=G'$ a.e.

**引理 24.2.7**

如果 $F \in BV$，那么 $T_{F}(-\infty)=0$，并且如果 $F$ 是右连续的，那么 $T_{F}$ 也是右连续的。

**证明**

设 $\varepsilon>0$，取 $x_{0}<\dots<x_{n}=x$ 使得

$$
\sum_{j=1}^{n} |F(x_{j})-F(x_{j-1})|> T_{F}(x)-\varepsilon
$$

于是 $T_{F}(x)-T_{F}(x_{0})>T_{F}(x)-\varepsilon$，这表明对任意 $y<x_{0}$ 有 $T_{F}(y)<\varepsilon$，即 $T_{F}(-\infty)=0$.

现设 $F$ 是右连续的，设 $x \in \mathbb{R},\varepsilon>0$，令 $\alpha=T_{F}(x+)-T_{F}(x)$，并取 $\delta>0$ 使得对任意 $0<h<\delta$ 有

$$
|F(x+h)-F(x)|<\varepsilon, T_{F}(x+h)-T_{F}(x+)<\varepsilon
$$

固定 $h$，取 $x=x_{0}<\dots<x_{n}=x+h$ 使得

$$
\sum_{j=1}^{n} |F(x_{j})-F(x_{j-1})|\geq \dfrac{3}{4}(T_{F}(x+h)-T_{F}(x))\geq \dfrac{3}{4}\alpha
$$

从而

$$
\sum_{j=2}^{n} |F(x_{j})-F(x_{j-1})|\geq \dfrac{3}{4}\alpha-|F(x_{1})-F(x)|\geq \dfrac{3}{4}\alpha-\varepsilon
$$

类似地，取 $x=t_{0}<\dots<t_{m}=x_{1}$ 使得 $\sum_{j=1}^{m}|F(t_{j})-F(t_{j-1})|\geq \dfrac{3}{4}\alpha$，于是就有

$$
\begin{align}
\alpha+\varepsilon &> T_{F}(x+h)-T_{F}(x) \\
&\geq \sum_{j=2}^{n} |F(x_{j})-F(x_{j-1})|+ \sum_{j=1}^{m} |F(t_{j})-F(t_{j-1})| \\
&\geq \dfrac{3}{2}\alpha -\varepsilon
\end{align}
$$

即 $\alpha<4\varepsilon$，从而 $\alpha=0$，即 $T_{F}$ 右连续。

**定理 24.2.8**

如果 $\mu$ 是 $\mathbb{R}$ 上的 Borel 复测度，$F(x)=\mu((-\infty,x])$，那么 $F \in NBV$. 反之，如果 $F \in NBV$，那么存在唯一的 Borel 复测度 $\mu_{F}$ 使得对任意 $x$ 有 $F(x)=\mu_{F}((-\infty,x])$，并且 $|\mu_{F}|=\mu_{T_{F}}$.

**证明**

如果 $\mu$ 是一个复测度，则有 $\mu=\mu_{1}^{+}-\mu_{1}^{-}+i(\mu_{2}^{+}-\mu_{2}^{-})$，并且每个 $\mu_{j}^{\pm}$ 都是有限正测度，令 $F_{j}^{\pm}(x)=\mu_{j}^{\pm}((-\infty,x])$，那么 $F_{j}^{\pm}$ 是递增且右连续的，并且 $F_{j}^{\pm}(-\infty)=0$，$F_{j}^{\pm}(+\infty)=\mu_{j}^{\pm}(\mathbb{R})<+\infty$，因此函数 $F=F_{1}^{+}-F_{1}^{-}+i(F_{2}^{+}-F_{2}^{-}) \in NBV$.

反之，每个 $F \in NBV$ 都可以写成 $F=F_{1}^{+}-F_{1}^{-}+i(F_{2}^{+}-F_{2}^{-})$，每个 $F_{j}^{\pm}$ 都是递增且右连续的，并且 $F_{j}^{\pm}(-\infty)=0,F_{j}^{\pm}(+\infty)<+\infty$，从而每个 $F_{j}^{\pm}$ 都诱导了唯一的有限测度 $\mu_{j}^{\pm}$，于是 $\mu_{F}=\mu_{1}^{+}-\mu_{1}^{-}+i(\mu_{2}^{+}-\mu_{2}^{-})$ 是唯一的，并且 $F(x)=\mu_{F}((-\infty,x])$.

设 $G(x)=|\mu_{F}|((-\infty,x])$，我们要证 $G=T_{F}$，从而根据唯一性得 $|\mu_{F}|=\mu_{T_{F}}$.

设 $x_{0}<\dots<x_{n}=x$，则

$$
\sum_{j=1}^{n} |F(x_{j})-F(x_{j-1})|=\sum_{j=1}^{n} |\mu_{F}((x_{j-1},x_{j}])|\leq |\mu_{F}|((x_{0},x]) \leq G(x)
$$

故 $T_{F}\leq G$.

设 $E=(a,b]$，则有 $|\mu_{F}(E)|=|F(b)-F(a)|\leq T_{F}(b)-T_{F}(a)=\mu_{T_{F}}(E)$，于是当 $E$ 是半开区间的有限无交并时也成立，从而对任意 Borel 集 $E$ 都有 $|\mu_{F}(E)|\leq \mu_{T_{F}}(E)$（利用单调类引理）。

任取 $n\geq 1,E=\bigcup_{j=1}^{n}E_{j}$，$E_{1},\dots,E_{n}$ 不相交，我们有 $\sum_{j=1}^{n}|\mu_{F}(E_{j})|\leq \sum_{j=1}^{n}\mu_{T_{F}}(E_{j})=\mu_{T_{F}}(E)$，因此根据定理 23.3.6 得 $|\mu_{F}|\leq \mu_{T_{F}}$，从而 $G\leq T_{F}$，这就完成了证明。

现在，我们看到了 $NBV$ 中的函数与 $\mathbb{R}$ 上的 Borel 复测度具有一一对应，那么，我们自然要问：什么函数对应于 $\mu \perp m$ 或者 $\mu\ll m$ 的复测度 $\mu$ 呢？其中一个答案如下：

**定理 24.2.9**

如果 $F \in NBV$，那么 $F' \in L^{1}(m)$，此外，$\mu_{F}\perp m$ 当且仅当 $F'=0$ a.e.，并且 $\mu_{F}\ll m$ 当且仅当 $F(x)=\int_{-\infty}^{x}F'(t)\mathrm{d}t$.

**证明**

设 $E_{r}=(x,x+r]$ 或者 $E_{r}=(x-r,x]$，则 $E_{r}$ 均匀收缩至 $x$，并且有

$$
\lim_{ r \to 0 } \dfrac{\mu_{F}(E_{r})}{m(E_{r})}=F'(x)
$$

再应用定理 24.1.14 就完成了证明。

对于条件 $\mu_{F}\ll m$，我们可以直接使用函数 $F$ 来表述。

**定义 24.2.10** 绝对连续（absolutely continuous）

函数 $F\colon \mathbb{R}\to \mathbb{C}$ 是**绝对连续的**，如果对任意 $\varepsilon>0$，存在 $\delta>0$ 使得对任意不相交的区间 $(a_{1},b_{1}),\dots,(a_{n},b_{n})$ 有

$$
\sum_{j=1}^{n} (b_{j}-a_{j})<\delta \implies \sum_{j=1}^{n} |F(b_{j})-F(a_{j})|<\varepsilon
$$

称 $F$ 在 $[a,b]$ 上绝对连续，如果上述条件中的 $(a_{j},b_{j})\subset[a,b]$.

显然，绝对连续蕴含了一致连续（取 $n=1$ 即可），因此它是一种更强的连续性。此外，如果 $F$ 是可微的并且 $F'$ 是有界的，那么 $F$ 是绝对连续的，因为根据中值定理有 $|F(b_{j})-F(a_{j})|\leq M(b_{j}-a_{j})$.

**定理 24.2.11**

设 $F \in NBV$，那么 $F$ 绝对连续当且仅当 $\mu_{F}\ll m$.

**证明**

当 $\mu_{F}\ll m$ 时，将定理 23.2.3 应用到 $E=\bigcup_{j=1}^{n}(a_{j},b_{j}]$ 上即可。反之，设 Borel 集 $E$ 满足 $m(E)=0$，令 $\varepsilon$ 和 $\delta$ 如定义 24.2.10 中所示，则存在开集 $U_{1}\supset U_{2}\supset\dots \supset E$ 使得 $m(U_{1})<\delta$ 并且 $\lim_{ j \to \infty }\mu_{F}(U_{j})=\mu_{F}(E)$，由于每个开集 $U_{j}$ 都是可数个开区间 $(a_{jk},b_{jk})$ 的无交并，且

$$
\sum_{k=1}^{n} |\mu_{F}((a_{jk},b_{jk}))|\leq \sum_{k=1}^{n} |F(b_{jk})-F(a_{jk})|<\varepsilon
$$

令 $n\to \infty$，则有 $|\mu_{F}(U_{j})|\leq\varepsilon$，从而 $|\mu_{F}(E)|\leq\varepsilon$，从而 $\mu_{F}(E)=0$，即 $\mu_{F}\ll m$.

结合 24.2.9 和 24.2.11，我们就有推论：

**定理 24.2.12**

如果 $f \in L^{1}(m)$，那么定义为 $F(x)=\int_{-\infty}^{x}f(t)\mathrm{d}t$ 的函数 $F \in NBV$ 且绝对连续，并且 $f=F'$ a.e. 反之，如果 $F \in NBV$ 且绝对连续，那么 $F' \in L^{1}(m)$ 且 $F(x)=\int_{-\infty}^{x}F'(t)\mathrm{d}t$.

如果我们考虑有界闭区间上的函数，那么上面的结果还可以做进一步的改进。

**引理 24.2.13**

如果 $F$ 在 $[a,b]$ 上绝对连续，那么 $F \in BV([a,b])$.

**证明**

设 $\varepsilon=1$，令 $\delta>0$ 为定义 24.2.10 中所示，设 $N= \left\lfloor  \dfrac{b-a}{\delta}  \right\rfloor+1$，取 $a=x_{0}<\dots<x_{n}=b$，并将区间 $(x_{j-1},x_{j})$ 分成至多 $N$ 组，使得每组区间长度之和小于 $\delta$，于是每一组中的求和 $\sum_{j}|F(x_{j})-F(x_{j-1})|$ 小于 $1$，从而 $F$ 在 $[a,b]$ 上的总变差小于 $N$，这就完成了证明。

综合以上所有的讨论，我们给出本节的主定理，即微积分基本定理。

**定理 24.2.14** 微积分基本定理（fundamental theorem of calculus）

设实数 $a<b$，函数 $F\colon [a,b]\to \mathbb{C}$，则以下命题等价：

1. $F$ 在 $[a,b]$ 上绝对连续。
2. 存在 $f \in L^{1}([a,b],m)$ 使得 $F(x)-F(a)=\int_{a}^{x}f(t)\mathrm{d}t$
3. $F$ 在 $[a,b]$ 上 a.e. 可微，$F' \in L^{1}([a,b],m)$，并且 $F(x)-F(a)=\int_{a}^{x}F'(t)\mathrm{d}t$

**证明**

为证明 $1\implies 3$，通过减去一个常数 $F(a)$，我们可以假设 $F(a)=0$，于是，我们定义当 $x<a$ 时 $F(x)=0$，当 $x>b$ 时 $F(x)=F(b)$，则根据引理 24.2.13 得 $F \in NBV$，从而 3 成立。

$3\implies 2$ 是显然的。假设 2 成立，当 $t\not\in [a,b]$ 时我们定义 $f(t)=0$，于是 $f \in L^{1}(m)$，从而根据定理 24.2.12 得 1 成立，这就完成了证明。

对于 $\mathbb{R}^{n}$ 上的 Borel 复测度，以下的分解通常是有用的。一个 $\mathbb{R}^{n}$ 上的 Borel 复测度 $\mu$ 是**离散的**，如果存在至多可数的集合 $\{ x_{j} \}$ 和复数 $c_{j}$ 使得 $\sum_{j=1}^{\infty}|c_{j}|<+\infty$，并且 $\mu=\sum_{j=1}^{\infty}c_{j}\delta_{j}$，其中 $\delta_{j}$ 是 $x_{j}$ 处的点质量测度。另一方面，$\mu$ 是**连续的**，如果对任意 $x$ 有 $\mu(\{ x \})=0$.

每个复测度都可以唯一地分解为 $\mu=\mu_{d}+\mu_{c}$，其中 $\mu_{d}$ 是离散的，$\mu_{c}$ 是连续的：令 $E=\{ x \mid \mu(\{ x \})\neq 0 \}$，则对任意可数集 $F\subset E$ 有 $\sum_{x \in F}\mu(\{ x \})$ 绝对收敛，因此对任意 $k$，集合 $\{ x \mid |\mu(\{ x \})|>k^{-1} \}$ 是有限的，从而 $E$ 自身是至多可数的。于是，$\mu_{d}(A)=\mu(A\cap E)$ 是离散的，$\mu_{c}(A)=\mu(A\setminus E)$ 是连续的。

显然，如果 $\mu$ 是离散的，那么 $\mu \perp m$，而如果 $\mu\ll m$，那么 $\mu$ 是连续的，因此根据定理 24.1.14，每个正则的复测度都可以分解为

$$
\mu=\mu_{d}+\mu_{ac}+\mu_{sc}
$$

其中 $\mu_{d}$ 是离散的，$\mu_{ac}\ll m$，而 $\mu_{sc}$ 是连续的，但 $\mu_{sc}\perp m$，因此它被称为“奇异连续”部分。这一分解在研究函数的间断行为时非常有用，下面我们给出一例。

设 $F \in NBV$，通常我们会把函数 $g$ 关于复测度 $\mu_{F}$ 的积分记作 $\int g\mathrm{d}F$ 或者 $\int g(x)\mathrm{d}F(x)$，称为 **Lebesgue-Stieltjes 积分**，它是 Riemann-Stieltjes 积分的扩展。

**定理 24.2.15** 分部积分法（integration by parts）

设 $F,G \in NBV$，则对任意实数 $a<b$ 有

$$
\int_{[a,b]}F(x)\mathrm{d} G(x)+\int_{[a,b]}G(x-)\mathrm{d} F(x)=F(b)G(b)-F(a-)G(a-)
$$

此外，如果不存在 $x \in[a,b]$ 使得 $F$ 和 $G$ 在 $x$ 处同时间断，则有

$$
\int_{[a,b]}F\mathrm{d} G+\int_{[a,b]} G\mathrm{d} F=F(b)G(b)-F(a-)G(a-)
$$

**证明**

由于 $F,G$ 可以写成 $NBV$ 中递增函数的线性组合，因此我们可以假设 $F,G$ 都是递增的。设 $\Omega=\{ (x,y) \mid a\leq x\leq y\leq b \}$，我们将使用 Fubini 定理以两种方法来计算 $\mu_{F}\times \mu_{G}(\Omega)$. 首先我们有

$$
\begin{align}
\mu_{F}\times \mu_{G}(\Omega) &= \int_{[a,b]}\int_{[a,y]}\mathrm{d} F(x)\mathrm{d} G(y)=\int_{[a,b]} (F(y)-F(a-))\mathrm{d} G(y) \\
&= \int_{[a,b]}F\mathrm{d} G-F(a-)(G(b)-G(a-))
\end{align}
$$

另一边，我们有

$$
\begin{align}
\mu_{F}\times \mu_{G}(\Omega) &= \int_{[a,b]}\int_{[x,b]}\mathrm{d} G(y)\mathrm{d} F(x)=\int_{[a,b]}(G(b)-G(x-))\mathrm{d} F(x) \\
&= G(b)(F(b)-F(a-))-\int_{[a,b]} G(x-)\mathrm{d} F(x)
\end{align}
$$

两式相减就得到了第一个结论。

现在假设 $F$ 和 $G$ 不同时间断，我们考虑积分

$$
\int_{[a,b]} (G(x)-G(x-))\mathrm{d} F(x)
$$

令 $D_{G}=\{ x \mid G(x)-G(x-)>0 \}$，将测度 $\mu_{F}$ 分解为离散部分 $\mu_{d}$ 和连续部分 $\mu_{c}$，由于 $D_{G}$ 是至多可数的，故 $\mu_{c}(D_{G})=0$，于是

$$
\int_{[a,b]} (G(x)-G(x-))\mathrm{d} \mu_{c}=\int_{D_{G}}(G(x)-G(x-))\mathrm{d} \mu_{c}=0
$$

对于 $\mu_{d}$，我们有 $\mu_{d}=\sum_{x \in D_{F}}c_{x}\delta_{x}$，其中 $D_{F}$ 是 $F$ 的间断点，于是由 $D_{G}\cap D_{F}=\varnothing$ 得

$$
\int_{[a,b]}(G(x)-G(x-))\mathrm{d} \mu_{d}=\sum_{x \in D_{F}} c_{x} (G(x)-G(x-))=0
$$

因此 $\int_{[a,b]}G\mathrm{d}F=\int_{[a,b]}G(x-)\mathrm{d}F(x)$，这就完成了证明。

另一个常用的定理是换元法，如下所示：

**定理 24.2.16** 积分换元法（substitution formula）

设 $G$ 是 $[a,b]$ 上的连续递增函数，$G(a)=c,G(b)=d$，那么如果可测函数 $f$ 满足 $f\geq 0$ 或者 $f \in L^{1}([c,d],m)$，则有

$$
\int_{c}^{d} f(y)\mathrm{d} y=\int_{a}^{b} f(G(x))\mathrm{d} G(x)
$$

**证明**

设 $(s,t]\subset [c,d]$，设 $G^{-1}(s)=u,G^{-1}(t)=v$，则

$$
\mu_{G}(G^{-1}[(s,t]])=\mu_{G}((u,v])=G(v)-G(u)=t-s=m((s,t])
$$

因此 $m(E)=\mu_{G}(G^{-1}[E])$ 对于 $E$ 是半开区间成立，从而当 $E\subset[c,d]$ 是 Borel 集时也成立，因此等式

$$
\int_{c}^{d} f(y)\mathrm{d} y=\int_{a}^{b} f(G(x))\mathrm{d} G(x)
$$

在 $f=\chi_{E}$ 时成立，于是等式对于 $f\geq 0$ 和 $f \in L^{1}([c,d],m)$ 成立，这就完成了证明。

当然，根据微积分基本定理，当 $F$ 绝对连续时，可以将一个 Lebesgue-Stieltjes 积分写成普通的 Lebesgue 积分：

$$
\int g \mathrm{d} F=\int g F' \mathrm{d} m
$$

下面，我们再给出一个应用。我们定义 $\mathbb{C}$ 上曲线 $\{ t+i f(t) \mid t \in[a,b] \}$ 的**长度** $L$ 为折线长度 $|t_{j}-t_{j-1}+i(f(t_{j})-f(t_{j-1}))|$ 之和的上确界，其中 $a=t_{0}<\dots<t_{n}=b$，$n\geq 1$.

**定理 24.2.17**

设 $f\colon [a,b]\to \mathbb{R}$，令 $F(t)=t+if(t)$，则 $\{ F(t) \mid t \in[a,b] \}$ 的长度 $L$ 是 $F$ 在 $[a,b]$ 上的总变差，并且如果 $f$ 是绝对连续的，那么有

$$
L=\int_{a}^{b} \sqrt{ 1+f'(t)^{2} } \mathrm{d} t
$$

**证明**

根据定义即得 $L$ 是 $F$ 在 $[a,b]$ 上的总变差。如果 $f$ 绝对连续，那么 $F$ 也绝对连续，当 $t<a$ 时令 $F(t)=F(a)$，当 $t>b$ 时令 $F(t)=F(b)$，考虑总变差函数 $T_{F}(t)$：由于 $\mu_{F}\ll m$，故 $|\mu_{F}|\ll m$，即 $\mu_{T_{F}}\ll m$，于是 $T_{F}$ 绝对连续，因此对 a.e. $t$ 都有

$$
T_{F}'(t)=\lim_{ h \to 0 } \dfrac{T_{F}(t+h)-T_{F}(t)}{h}
$$

存在。下面我们要证 $T_{F}'(t)=|F'(t)|$ a.e. 设 $h>0$，一方面，我们有

$$
\dfrac{1}{h}\sum_{j=1}^{n} |F(t_{j})-F(t_{j-1})|= \dfrac{1}{h} \sum_{j=1}^{n} \left\lvert  \int_{t_{j-1}}^{t_{j}}F'(\xi)\mathrm{d} \xi  \right\rvert  \leq \dfrac{1}{h} \int_{t}^{t+h} |F'(\xi)|\mathrm{d} \xi
$$

令 $h\to 0$，根据 Lebesgue 微分定理，不等式右边的项收敛于 $|F'(t)|$，因此 $T_{F}'(t)\leq |F'(t)|$ a.e.

另一方面，我们有

$$
\dfrac{|F(t+h)-F(t)|}{h}= \dfrac{|hF'(t)+o(h)|}{h}\geq |F'(t)|-\dfrac{|o(h)|}{h}
$$

令 $h\to 0$，则有 $T_{F}'(t)\geq |F'(t)|$ a.e.，故 $T_{F}'(t)=|F'(t)|$ a.e.

于是，根据微积分基本定理，我们有

$$
L=T_{F}(b)-T_{F}(a)=\int_{a}^{b} |F'(t)|\mathrm{d} t=\int_{a}^{b} \sqrt{ 1+f'(t)^{2} }\mathrm{d} t
$$

这就完成了证明。

最后，我们给出一个关于逐项求导的定理。

**定理 24.2.18**

设 $(F_{j})_{j=1}^{\infty}$ 是一列 $[a,b]$ 上的非负递增函数，并且对任意 $x \in[a,b]$ 有 $F(x)=\sum_{j=1}^{\infty}F_{j}(x)<+\infty$，那么对 a.e. $x$ 有 $F'(x)=\sum_{j=1}^{\infty}F_{j}'(x)$.

**证明**

通过取 $G(x)=F(x+)-F(-\infty)$，我们可以假设 $F_{j}\in NBV$，其中 $F_{j}$ 的定义域要做显然的延拓。考虑测度 $\mu=\sum_{j=1}^{\infty}\mu_{F_{j}}$，由于 $\sum_{j=1}^{\infty}F_{j}(x)$ 有限，故 $\mu$ 是有限测度，从而 $F(x)=\mu((-\infty,x])$ 在 $NBV$ 中，因此 $F$ 是 a.e. 可微的。

将测度分成奇异部分 $\mu_{s},(\mu_{F_{j}})_{s}$ 和绝对连续部分 $F'\mathrm{d}m,F_{j}'\mathrm{d}m$，根据 Lebesgue 分解的唯一性有 $\mu_{s}=\sum_{j=1}^{\infty}(\mu_{F_{j}})_{s}$，$F'\mathrm{d}m=\sum_{j=1}^{\infty}F_{j}'\mathrm{d}m$，于是对任意 Borel 集 $E$ 有

$$
\int_{E} F'\mathrm{d} m= \sum_{j=1}^{\infty} \int_{E}F_{j}'\mathrm{d} m=\int_{E} \sum_{j=1}^{\infty} F_{j}'\mathrm{d} m
$$

从而 $F'=\sum_{j=1}^{\infty}F_{j}'$ a.e.，即证。