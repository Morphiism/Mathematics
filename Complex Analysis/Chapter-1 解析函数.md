复分析的出发点仅仅只是这样一个想法：如果我们将原本定义在实数上的函数扩展为复数上的函数会怎么样？换句话说，我们要研究的是从复数域到其自身的函数

$$
\begin{gather}
f\colon \mathbb{C}\to \mathbb{C}
\end{gather}
$$

或者更一般地，从复数域中的开集到复数域的函数。起初，有人可能会说，这种扩展并没有带来任何新的东西，因为每个复数 $z$ 都可以等同于平面上的一个点 $(x,y)\in \mathbb{R}^{2}$. 然而，当我们对 $f$ 做一个自然的假设，即 $f$ 在复数意义下可导时，一切都发生了巨大的变化。那个假设被称为**全纯性**（holomorphicity），它表明极限

$$
\begin{gather}
\lim_{ h \to 0 } \dfrac{f(z+h)-f(z)}{h} \quad (h\in \mathbb{C})
\end{gather}
$$

存在。这一定义几乎是实函数可导性的直接推广，只不过我们允许 $h$ 取任意复数，这一点造成了全纯性与实可导性的本质不同：在实数上，$h$ 只能从两个方向趋于零，而在复数中则有无穷多个方向。正因如此，复数域上的全纯函数具有一些极其优良的性质：

1. 围道积分：如果 $f$ 在 $\Omega$ 上全纯，那么对于 $\Omega$ 中满足特定条件的闭曲线 $\gamma$ 有 $$
\int_{\gamma} f(z)\mathrm{d} z=0
$$
2. 正则性：函数 $f$ 是全纯的，当且仅当它是**解析的**（analytic），即 $f$ 可以在局部展开为幂级数。换句话说，$f$ 是无穷阶可微的。正因如此，在复分析中我们将“全纯”与“解析”作为同义词使用。
3. 解析延拓：$\Omega$ 上的全纯函数 $f,g$ 如果在 $\Omega$ 的某个开子集上相等，那么 $f=g$ 在整个 $\Omega$ 上成立。换句话说，全纯函数根据其局部的信息可以确定整个函数。

这些性质构成了全纯函数的所谓“刚性”。对于一个实函数，我们可以轻易地改变其在局部的值，而不影响全局的性质。而由于复可导条件的“刚性”，解析函数局部值的变化将对全局性质产生决定性的变化。在复分析中，我们将多次体会到这一点。

# Section 1: 复数

我们假定读者已经熟悉复数系统及它的一些基本特性。给定 $z=(x,y)\in \mathbb{C}$，我们将其写成 $x+yi$，其中 $i^{2}=-1$. 我们称 $x,y$ 分别为 $z$ 的实部和虚部，记作 $x=\mathrm{Re}\, z,y=\mathrm{Im}\, z$. 并且我们定义 $z$ 的模长（modulus）为 $|z|=\sqrt{ x^{2}+y^{2} }$，以及 $z$ 的共轭为 $\overline{z}=x-yi$.

对于复平面 $\mathbb{C}$ 上的点 $z=x+iy$，这种表示方法称为直角坐标表示。除此以外，我们还有极坐标表示：$z=r(\cos\theta+i\sin\theta)$，其中 $r=|z|$，$\theta$ 满足等式 $r\cos\theta=x,r\sin\theta=y$，称为 $z$ 的辐角（argument），记作

$$
\begin{gather}
\theta=\mathrm{arg}\, z
\end{gather}
$$

由于三角函数的周期性，一个复数有无穷多个辐角，因此 $\mathrm{arg}$ 不是通常意义上的函数。利用极坐标表示，我们可以给出复数乘法的一个几何解释：设 $z_{1}=r_{1}(\cos\theta_{1}+i\sin\theta_{1}),z_{2}=r_{2}(\cos\theta_{2}+i\sin\theta_{2})$，则根据三角恒等式有

$$
\begin{gather}
z_{1}z_{2}=r_{1}r_{2}(\cos(\theta_{1}+\theta_{2})+i\sin(\theta_{1}+\theta_{2}))
\end{gather}
$$

换句话说，两个复数相乘，其模长相乘，辐角相加（仅相差 $2\pi$ 的整数倍）。从另一方面来说，乘以一个复数 $z_{1}$ 就相当于对 $z_{2}$ 做一个均匀缩放（缩放为 $|z_{1}|$ 倍）和一个旋转（旋转 $\mathrm{arg}\,z_{1}$ 弧度）。特别地，我们有

$$
\begin{gather}
z^{n}=r^{n}(\cos n\theta+i\sin n\theta)
\end{gather}
$$

于是，对于复数 $z$，它的 $n$ 次根 $z^{1/n}$ 共有 $n$ 个，分别为

$$
\begin{gather}
r^{1/n} \left( \cos \dfrac{\theta+2\pi k}{n}+i \sin \dfrac{\theta+2\pi k}{n} \right), 0\leq k\leq n-1
\end{gather}
$$

由于 $z^{1/n}$ 的多值性，因此 $n$ 次根与辐角一样，均不是通常意义下的函数。

设 $L$ 是 $\mathbb{C}$ 中的一条直线，根据基础解析几何，一条直线由其上的一个点和一个方向完全确定。我们令 $a$ 为 $L$ 上的点，$b\neq 0$ 为 $L$ 的方向向量，则

$$
\begin{gather}
L=\{ z=a+tb \mid t \in \mathbb{R} \}
\end{gather}
$$

对于 $z \in L$，上式也可以表示为 $\dfrac{z-a}{b}=t \in \mathbb{R}$，即

$$
\begin{gather}
L=\left\{  z \middle| \mathrm{Im}\,\dfrac{z-a}{b}=0  \right\}
\end{gather}
$$

这条直线将平面分成了两个部分，分别是 $\left\{  z \middle| \mathrm{Im}\, \dfrac{z-a}{b} >0 \right\}$ 和 $\left\{  z \middle| \mathrm{Im}\, \dfrac{z-a}{b} <0 \right\}$. 我们来逐一辨析这些集合。

首先注意到，由于 $b$ 是一个方向向量，因此我们可以将其归一化为 $|b|=1$，从而我们可以设 $b=\cos\beta+i\sin\beta$. 考虑集合 $H_{0}=\{ z \mid \mathrm{Im}(z / b)>0 \}$，如果 $z=r(\cos\theta+i\sin\theta)$，则

$$
\begin{gather}
\dfrac{z}{b}=r(\cos(\theta-\beta)+i\sin(\theta-\beta))
\end{gather}
$$

从而 $\mathrm{Im}(z / b)>0$ 当且仅当 $\sin(\theta-\beta)>0$，即 $\beta<\theta<\pi+\beta$. 换句话说，$H_{0}$ 是这样的区域：沿着 $b$ 的方向直线行走，左手边的半平面正是 $H_{0}$.

![](1-1.png)

将 $H_{0}$ 沿 $a$ 的方向平移，我们就得到了

$$
\begin{gather}
\left\{  z \middle| \mathrm{Im}\, \dfrac{z-a}{b} >0 \right\}=H_{a}=a+H_{0}=\{ a+w \mid w \in H_{0} \}
\end{gather}
$$

类似地，集合 $K_{a}=\left\{  z \middle| \mathrm{Im}\, \dfrac{z-a}{b} <0 \right\}$ 就是这样的区域：按 $b$ 的方向沿着 $L$ 行走，右手边的半平面正是 $K_{a}$.

在复分析中，我们时常需要研究函数在无穷远点处的行为。在这种情况下，我们可以引入扩展复数平面 $\mathbb{C}_{\infty}=\mathbb{C}\cup \{ \infty \}$，其中 $\infty$ 表示一个不在 $\mathbb{C}$ 上的“无穷远点”。我们还想要在 $\mathbb{C}_{\infty}$ 上讨论函数的连续性，为此，我们需要一个 $\mathbb{C}_{\infty}$ 上的度量。

为了说明动机，我们可以将 $\mathbb{C}_{\infty}$ 想象成 $\mathbb{R}^{3}$ 上的球面

$$
\begin{gather}
S=\{ (x_{1},x_{2},x_{3}) \mid x_{1}^{2}+x_{2}^{2}+x_{3}^{2}=1 \}
\end{gather}
$$

令 $N=(0,0,1)$ 为 $S$ 的北极点，并且我们将 $\mathbb{C}$ 等同于 $S$ 的赤道所在的平面 $\{ (x_{1},x_{2},0) \mid x_{1},x_{2} \in \mathbb{R} \}$. 对于 $z \in \mathbb{C}$，连接 $z$ 与 $N$ 的直线与球面有交点 $Z\neq N$，并且当 $|z|>1$ 时，$Z$ 属于北半球；当 $|z|<1$ 时，$Z$ 属于南半球；当 $|z|=1$ 时有 $Z=z$. 而当 $|z| \to \infty$ 时，$Z$ 似乎正“趋近于”北极点 $N$，因此，我们将无穷远点 $\infty$ 与 $N$ 等同。这样，我们就构造了 $S$ 与 $\mathbb{C}_{\infty}$ 之间的一个双射。

![](1-2.png)

我们来求解 $Z$ 的坐标。设 $z=x+iy$，则连接 $z$ 与 $N$ 的直线为

$$
\begin{gather}
\{ ((1-t)x,(1-t)y,t) \mid t \in \mathbb{R} \}
\end{gather}
$$

它与 $S$ 的交点满足

$$
\begin{gather}
(1-t)^{2}x^{2}+(1-t)^{2}y^{2}+t^{2}=(1-t)^{2}|z|^{2}+t^{2}=1
\end{gather}
$$

由于 $t\neq 1(Z\neq N)$，故有 $t= \dfrac{|z|^{2}-1}{|z|^{2}+1}$，因此

$$
\begin{gather}
x_{1}=\dfrac{2x}{|z|^{2}+1}=\dfrac{z+\overline{z}}{|z|^{2}+1}, x_{2}=\dfrac{2y}{|z|^{2}+1}=\dfrac{-i(z-\overline{z})}{|z|^{2}+1}, x_{3}= \dfrac{|z|^{2}-1}{|z|^{2}+1}
\end{gather}
$$

如果我们已知 $Z\neq N$，我们也可以利用上式得到

$$
\begin{gather}
z=\dfrac{x_{1}+ix_{2}}{1-x_{3}}
\end{gather}
$$

现在我们利用 $\mathbb{R}^{3}$ 上的度量来定义 $\mathbb{C}_{\infty}$ 上的度量：对于 $z,z' \in \mathbb{C}_{\infty}$，我们定义 $d_{\mathbb{C}_{\infty}}(z,z')=d_{\mathbb{R}^{3}}(Z,Z')$. 换句话说，我们有

$$
\begin{gather}
d_{\mathbb{C}_{\infty}}(z,z')=\sqrt{ (x_{1}-x_{1}')^{2}+(x_{2}-x_{2}')^{2}+(x_{3}-x_{3}')^{2} }
\end{gather}
$$

利用等式 $x_{1}^{2}+x_{2}^{2}+x_{3}^{2}=1$ 以及 $x_{1},x_{2},x_{3}$ 的表达式，我们可得

$$
\begin{gather}
d_{\mathbb{C}_{\infty}}(z,z')=\dfrac{2|z-z'|}{\sqrt{ (1+|z|^{2})(1+|z'|^{2}) }} \quad (z,z' \in \mathbb{C})
\end{gather}
$$

而当 $z'=\infty$ 时我们有

$$
\begin{gather}
d_{\mathbb{C}_{\infty}}(z,\infty)= \dfrac{2}{\sqrt{ 1+|z|^{2} }}
\end{gather}
$$

以上的 $\mathbb{C}_{\infty}$ 与 $S$ 之间的一一对应通常称为**球极投影**（stereographic projection）。

# Section 2: 复数的拓扑

在标准度量 $d(z,w)=|z-w|$ 下，复数 $\mathbb{C}$ 构成了一个度量空间，其同构于实平面 $\mathbb{R}^{2}$. 于是，所有对 $\mathbb{R}^{2}$ 成立的拓扑性质对 $\mathbb{C}$ 也成立。因此，接下来我们将只补充之后会用到的拓扑性质。

首先，一个连通性的等价定义：

**定理 1.2.1**

度量空间 $X$ 是连通的当且仅当 $X$ 中既开又闭的子集仅有 $\varnothing$ 和 $X$.

**证明**

设 $X$ 是连通的，假设有既开又闭的子集 $U\neq \varnothing$ 且 $U\neq X$，那么 $V=X\setminus U\neq \varnothing$ 是开集，并且 $X=U\cup V$，这与连通性的定义矛盾。

反之，设 $X$ 中既开又闭的子集仅有 $\varnothing$ 和 $X$，假设 $X$ 不连通，则有不相交的非空开集 $U,V$ 使得 $X=U\cup V$，则 $V=X\setminus U$ 是闭集，从而 $V$ 是不同于 $\varnothing,X$ 的既开又闭子集，这与条件矛盾。

**定义 1.2.2** 折线（polygonal line）

如果 $z,w \in \mathbb{C}$，我们将连接 $z,w$ 的直线段记作

$$
\begin{gather}
[z,w]=\{ tw+(1-t)z \mid 0\leq t\leq 1 \}
\end{gather}
$$

一条连接 $a,b \in \mathbb{C}$ 的**折线**定义为集合 $P=\bigcup_{k=1}^{n}[z_{k},w_{k}]$，其中 $z_{1}=a$，$w_{n}=b$，并且对任意 $1\leq k\leq n-1$ 有 $w_{k}=z_{k+1}$. 上述折线通常也写成 $P=[a,z_{1},\dots,z_{n},b]$.

**定理 1.2.3**

开集 $G\subset \mathbb{C}$ 是连通的当且仅当对任意 $a,b \in G$，存在连接 $a,b$ 的折线 $P\subset G$.

**证明**

假设 $G$ 中的任意两点都有折线 $P=\bigcup_{k=0}^{n-1}[z_{k},w_{k}]$ 连接。显然，定义为

$$
\begin{gather}
\gamma(t)=(nt-k) w_{k}+(k+1-nt) z_{k}, t \in \left[ \dfrac{k}{n}, \dfrac{k+1}{n} \right], 0\leq k\leq n-1
\end{gather}
$$

的函数 $\gamma\colon[0,1]\to P$ 是连续的，从而 $G$ 道路连通，因而是连通的。

现在假设 $G$ 是连通的且 $a \in G$，我们要证存在 $a$ 到 $b$ 的折线 $P\subset G$. 令

$$
\begin{gather}
A=\{ b \in G \mid \text{存在折线} P\subset G \text{连接} a,b \}
\end{gather}
$$

我们将证明 $A$ 是既开又闭的，从而根据 $a \in A$ 以及连通性知 $A=G$.

为证明 $A$ 是开集，设 $b \in A$，并令 $P=[a,z_{1},\dots,z_{n},b]\subset G$. 由于 $G$ 是开集，故存在开球 $B(b,\varepsilon)\subset G$，从而对于 $z \in B(b,\varepsilon)$ 有 $[b,z]\subset G$，因此连接 $a,z$ 的折线 $P\cup [b,z]\subset G$. 这表明 $B(b,\varepsilon)\subset A$，从而 $A$ 是开的。

为证明 $A$ 是闭集，考虑 $A^{c}=G\setminus A$. 设 $z \in A^{c}$，开球 $B(z,\varepsilon)\subset G$，如果 $A\cap B(z,\varepsilon)\neq \varnothing$，那么根据上文，我们可以构造从 $a$ 到 $z$ 的折线，这与 $z$ 的定义矛盾。因此，$A\cap B(z,\varepsilon)=\varnothing$，即 $B(z,\varepsilon)\subset A^{c}$，从而 $A^{c}$ 是开集，即证 $A$ 是闭集。这就完成了证明。

将以上证明稍作修改，我们立即得到推论：

**定理 1.2.4**

如果 $G\subset \mathbb{C}$ 是连通开集，$a,b \in G$，则存在连接 $a,b$ 的折线 $P=\bigcup_{k=1}^{n}[z_{k},w_{k}]\subset G$ 使得每个 $[z_{k},w_{k}]$ 均平行于实轴或虚轴。

**证明**

在定理 1.2.3 的证明中，除了集合 $A$ 的定义外，我们只需修改一处内容：从 $b$ 到 $z \in B(b,\varepsilon)$ 的直线段 $[b,z]$ 不一定平行于坐标轴。然而，容易看出，如果 $b=x+iy,z=u+iv$，则折线 $[b,u+iy]\cup[u+iy,z]\subset B(b,\varepsilon)$ 是满足要求的。

下面我们来证明，度量空间中的集合 $S$ 可以典范地写成一系列“分量”的无交并。

**定义 1.2.5** 连通分量（connected component）

度量空间 $X$ 的子集 $D$ 称为 $X$ 的一个**连通分量**，如果 $D$ 是 $X$ 的一个极大连通子集。即，$D$ 是连通的并且不存在连通集 $E$ 使得 $E\supsetneq D$.

**引理 1.2.6**

给定度量空间 $X$ 和 $x_{0}\in X$，令 $\{ D_{j} \}$ 为一族连通集使得 $x_{0}\in D_{j}$ 对任意 $j$ 成立，则 $D=\bigcup_{j} D_{j}$ 是连通的。

**证明**

设 $A\subset D$ 是一个既开又闭子集，且 $A\neq \varnothing$，则对任意 $j$，集合 $A\cap D_{j}$ 在 $D_{j}$ 中是既开又闭的，从而 $A\cap D_{j}=\varnothing$ 或者 $A\cap D_{j}=D_{j}$. 由于 $A$ 非空，因此至少存在一个 $D_{k}$ 使得 $A\cap D_{k}\neq \varnothing$，即 $A\cap D_{k}=D_{k}$. 于是 $x_{0}\in A$，这表明对所有 $j$ 均有 $A\cap D_{j}\neq \varnothing$，从而 $D_{j}\subset A$. 因此 $A=D$，从而 $D$ 是连通的。

**定理 1.2.7**

设 $X$ 是一个度量空间，则：

1. 每个 $x_{0}\in X$ 都包含于 $X$ 的某个连通分量中
2. $X$ 的不同连通分量是不相交的

**证明**

令 $\mathcal{D}$ 表示包含 $x_{0}\in X$ 的连通集构成的集族，由于 $\{ x_{0} \}\in \mathcal{D}$，故 $\mathcal{D}\neq \varnothing$. 应用引理 1.2.6，集合 $C=\bigcup \mathcal{D}$ 是连通的并且 $x_{0}\in C$. 下面我们证明 $C$ 是一个连通分量。事实上，如果 $D$ 是连通集且 $C\subset D$，则 $x_{0}\in D$，从而 $D\in \mathcal{D}$，因此 $D\subset C$，这表明 $C=D$，因而 $C$ 是极大连通集，即连通分量。

下面假设有连通分量 $C_{1},C_{2}$ 使得 $C_{1}\cap C_{2}\neq \varnothing$，则再次应用引理 1.2.6 可知 $C_{1}\cup C_{2}$ 也是连通的，利用极大性，我们有 $C_{1}=C_{1}\cup C_{2}=C_{2}$，这就完成了证明。

**定理 1.2.8**

设 $X$ 是一个度量空间，则：

1. 如果 $A\subset X$ 是连通集，$A\subset B\subset \overline{A}$，则 $B$ 也是连通集
2. 如果 $C$ 是 $X$ 的一个连通分量，则 $C$ 是闭集

**证明**

注意到 2 是 1 的一个直接推论：如果 $C$ 是连通分量，则 $\overline{C}$ 是连通的，从而根据极大性有 $C=\overline{C}$，即 $C$ 是闭集。下面我们证明性质 1.

假设 $B$ 不连通，即存在开集 $U,V$ 使得 $B\cap U\neq \varnothing,B\cap V\neq \varnothing$，$B=(B\cap U)\cup(B\cap V)$ 且 $B\cap U\cap V=\varnothing$. 由于 $A\subset B$，则显然有 $A\subset U\cup V$ 且 $A\cap U\cap V=\varnothing$，下证 $A\cap U\neq \varnothing$ 且 $A\cap V\neq \varnothing$.

取 $x \in B\cap U$，则 $x \in \overline{A}$，由于 $U$ 是 $x$ 的一个邻域，故根据闭包的定义，$U\cap A\neq \varnothing$. 同理 $V\cap A\neq \varnothing$，因此 $A$ 不是连通集，这与条件矛盾。

**定理 1.2.9**

设 $G\subset \mathbb{C}$ 是开集，则 $G$ 的连通分量是开集，并且连通分量的个数至多可数。

**证明**

设 $C$ 是 $G$ 的一个连通分量，$x_{0} \in C$，则存在开球 $B(x_{0},\varepsilon)\subset G$. 应用引理 1.2.6，$B(x_{0},\varepsilon)\cup C$ 是连通集，从而 $B(x_{0},\varepsilon)\cup C=C$，即 $B(x_{0},\varepsilon)\subset C$，这就证明了 $C$ 是开的。

要证连通分量的个数至多可数，设 $S=\{ a+bi \mid a,b \in \mathbb{Q} \}$，由于 $S$ 是 $\mathbb{C}$ 的可数稠密子集，故对每个连通分量 $C$，我们可以取 $s \in S\cap C$，又由于不同的连通分量不相交，我们可得从连通分量构成的集族到 $S$ 的一个单射，这就完成了证明。

接下来的几个定理关乎集合间的距离。

**定义 1.2.10**

设 $X$ 是度量空间，定义 $A\subset X$ 的**直径**（diameter）为

$$
\begin{gather}
\mathrm{diam}\, A=\sup \{ d(x,y) \mid x,y \in A \}
\end{gather}
$$

给定 $x \in X$，定义 $x$ 到 $A$ 的距离为

$$
\begin{gather}
d(x,A)=\inf \{ d(x,y) \mid y \in A \}
\end{gather}
$$

再设 $B\subset X$，定义 $A$ 与 $B$ 之间的距离为

$$
\begin{gather}
d(A,B)=\inf \{ d(x,y) \mid x \in A,y \in B \}
\end{gather}
$$

**引理 1.2.11**

设 $X$ 是度量空间，$A\subset X$，则 $\mathrm{diam}\,A=\mathrm{diam}\, \overline{A}$.

**证明**

根据定义，显然有 $\mathrm{diam}\,A\leq \mathrm{diam}\, \overline{A}$，下证反向的不等式。任取 $\varepsilon>0$ 和 $x,y \in \overline{A}$，开球 $B(x,\varepsilon / 2)$ 和 $B(y,\varepsilon / 2)$ 与 $A$ 相交，分别取交集中的点 $x', y' \in A$，则有

$$
\begin{gather}
|d(x,y)-d(x',y')|<\varepsilon
\end{gather}
$$

即 $d(x,y)<d(x',y')+\varepsilon\leq \mathrm{diam}\,A+\varepsilon$，对左边取上确界得 $\mathrm{diam}\, \overline{A}\leq\mathrm{diam}\, A+\varepsilon$，根据 $\varepsilon$ 的任意性即证。

**定理 1.2.12** Cantor 定理

度量空间 $X$ 是完备的，当且仅当对任意一列非空闭集 $\{ F_{n} \}$，如果 $F_{1}\supset F_{2}\supset\cdots$ 且 $\mathrm{diam}\, F_{n}\to 0$，那么集合 $\bigcap_{n=1}^{\infty}F_{n}$ 是单点集。

**证明**

首先假设 $X$ 是完备的，且有一列非空闭集 $\{ F_{n} \}$ 满足 $F_{1}\supset F_{2}\supset\cdots$ 且 $\lim \mathrm{diam}\, F_{n}=0$. 对任意 $n$，取 $x_{n}\in F_{n}$，构成序列 $(x_{n})$，则当 $n,m\geq N$ 时，有 $x_{n},x_{m}\in F_{N}$，从而 $d(x_{n},x_{m})\leq \mathrm{diam}\,F_{N}$. 根据假设，我们可以选取足够大的 $N$ 使得 $\mathrm{diam}\,F_{N}<\varepsilon$，从而 $(x_{n})$ 是 Cauchy 序列。由于 $X$ 是完备的，存在 $x_{0}=\lim x_{n}$，并且对任意 $N$ 均有 $x_{0}\in F_{N}$，这表明 $x_{0}\in \bigcap_{n=1}^{\infty}F_{n}$. 此外，如果又有 $y \in \bigcap_{n=1}^{\infty}F_{n}$，则 $x_{0},y\in F_{n}$ 对任意 $n$ 成立，从而 $d(x_{0},y)\leq \mathrm{diam}\,F_{n}\to 0$，即得 $x_{0}=y$.

反之，令 $(x_{n})$ 为 $X$ 中的 Cauchy 序列，取 $F_{n}=\overline{\{ x_{n},x_{n+1},\dots \}}$，则 $F_{1}\supset F_{2}\supset\cdots$，并且对任意 $\varepsilon>0$，存在 $N$ 使得 $d(x_{n},x_{m})<\varepsilon$ 对任意 $n,m\geq N$ 成立，于是根据引理 1.2.11 得 $\mathrm{diam}\, F_{n}\leq\varepsilon$ 对 $n\geq N$ 成立，因此 $\mathrm{diam}\,F_{n}\to 0$，从而 $\bigcap_{n=1}^{\infty}F_{n}$ 为单点集 $\{ x_{0} \}$. 于是对任意 $n$ 有 $d(x_{0},x_{n})\leq \mathrm{diam}\,F_{n}\to 0$，即证 $\lim x_{n}=x_{0}$.

**定义 1.2.13** Lipschitz 连续

设 $(X,d_{X}),(Y,d_{Y})$ 是度量空间，$M>0$，函数 $f\colon X\to Y$ 称为是 $M$-**Lipschitz 连续**的，如果对任意 $x,y \in X$ 有

$$
\begin{gather}
d_{Y}(f(x),f(y))\leq Md_{X}(x,y)
\end{gather}
$$

显然，Lipschitz 函数是一致连续的。以下的定理给出了一大类 Lipschitz 函数。

**定理 1.2.14**

设 $X$ 是度量空间，$A\subset X$，则：

1. $d(x,A)=d(x,\overline{A})$
2. $d(x,A)=0$ 当且仅当 $x \in \overline{A}$
3. $|d(x,A)-d(y,A)|\leq d(x,y)$ 对任意 $x,y \in X$ 成立

**证明**

(1). 显然我们有 $d(x,\overline{A})\leq d(x,A)$. 另一方面，对任意 $\varepsilon>0$，存在 $y \in \overline{A}$ 使得 $d(x,\overline{A})\geq d(x,y)-\varepsilon /2$，并且存在 $a \in A$ 使得 $d(y,a)<\varepsilon /2$，于是根据三角不等式有

$$
\begin{gather}
|d(x,y)-d(x,a)|\leq d(y,a)<\varepsilon /2
\end{gather}
$$

即 $d(x,\overline{A})\geq d(x,a)-\varepsilon\geq d(x,A)-\varepsilon$，根据 $\varepsilon$ 的任意性即证。

(2). 如果 $x \in \overline{A}$，则 $d(x,A)=d(x,\overline{A})=0$. 另一方面，对任意 $x \in X$，存在 $A$ 中的序列 $(a_{n})$ 使得 $d(x,A)=\lim d(x,a_{n})$，如果 $d(x,A)=0$ 即 $d(x,a_{n})\to 0$，这就是说 $x=\lim a_{n}$，即证 $x \in \overline{A}$.

(3). 根据三角不等式，对 $a \in A$ 有 $d(x,A)\leq d(x,a)\leq d(x,y)+d(y,a)$，在右边对 $a \in A$ 取下确界得 $d(x,A)\leq d(y,A)+d(x,y)$，同理可得 $d(y,A)\leq d(x,A)+d(x,y)$，这就完成了证明。

**定理 1.2.15**

设 $X$ 是度量空间，$x \in X$，$K\subset X$ 是紧致集，则存在 $y \in K$ 使得 $d(x,y)=d(x,K)$.

**证明**

定义 $f\colon X\to \mathbb{R}$ 为 $f(y)=d(x,y)$，则 $f$ 是连续函数，并且 $f[K]$ 是紧致集，这表明 $f|_{K}$ 可以取到最小值 $d(x,K)$，即证。

**定理 1.2.16**

设 $X$ 是度量空间，$A,B$ 是 $X$ 中不相交的集合，$A$ 是紧致集且 $B$ 是闭集，则 $d(A,B)>0$.

**证明**

定义 $f\colon X\to \mathbb{R}$ 为 $f(x)=d(x,B)$，由于 $B=\overline{B}$，故 $f(a)>0$ 对任意 $a \in A$ 成立。又由于 $A$ 是紧致的，存在 $a \in A$ 使得 $f|_{A}$ 取到最小值 $d(A,B)=f(a)>0$，即证。

**定理 1.2.17** Lebesgue 覆盖引理（Lebesgue Covering Lemma）

设 $X$ 是紧致度量空间，$\mathcal{G}$ 是 $X$ 的一个开覆盖，则存在 $\varepsilon>0$ 使得如果 $x \in X$，那么有 $G \in \mathcal{G}$ 满足 $B(x,\varepsilon)\subset G$.

**证明**

我们用反证法。假设不存在这样的 $\varepsilon$，则对任意 $n$，存在 $x_{n}\in X$ 使得 $B(x_{n},1 /n)$ 不包含于任何 $G \in \mathcal{G}$. 由于 $X$ 紧致，故存在 $x_{0} \in X$ 和子序列 $(x_{n_{k}})$ 收敛于它。令 $G_{0}\in \mathcal{G}$ 使得 $x_{0}\in G_{0}$ 并取 $\varepsilon>0$ 使得 $B(x_{0},\varepsilon)\subset G_{0}$. 根据收敛性，存在 $N$ 使得当 $n_{k}\geq N$ 时有 $d(x_{0},x_{n_{k}})<\varepsilon /2$，于是，对任意 $n_{k}\geq \max \{ N,2 /\varepsilon \}$ 和 $y \in B(x_{n_{k}},1 /n_{k})$，有

$$
\begin{gather}
d(x_{0},y)\leq d(x_{0},x_{n_{k}})+d(x_{n_{k}},y)< \varepsilon
\end{gather}
$$

因此 $B(x_{n_{k}},1 /n_{k})\subset B(x_{0},\varepsilon)\subset G_{0}$，这与假设矛盾。

# Section 3: 解析函数

现在我们来定义复函数可导的条件，并指出它与实可导函数根本性的不同之处。

**定义 1.3.1** 可微（differentiable），全纯（holomorphic）

设 $G\subset \mathbb{C}$ 是开集，$f\colon G\to \mathbb{C}$，称 $f$ 在 $z \in G$ 处**可微**，如果极限

$$
\begin{gather}
\lim_{ h \to 0 } \dfrac{f(z+h)-f(z)}{h}
\end{gather}
$$

存在。该极限的值记作 $f'(z)$，称为 $f$ 在 $z$ 处的**导数**。如果 $f$ 在 $G$ 上的每一点都可微，则称 $f$ 在 $G$ 上是**全纯的**。

注意到复可微性与实可微性的定义在形式上是相同的，因此对实可微性成立的定理对复可微性也成立，例如导数的线性性、链式法则等。

**定义 1.3.2** 解析（analytic）

设 $G\subset \mathbb{C}$ 是开集，$f\colon G\to \mathbb{C}$ 称为是**解析的**，如果 $f$ 在 $G$ 上连续可微。

显然，如果 $f,g$ 是解析函数，那么 $f+g,fg$ 都是解析函数，并且 $f / g$ 在 $g\neq 0$ 处解析。

注意，为了定义导数，我们需要 $f$ 定义在开集上。如果我们说 $f$ 在非开集 $A$ 上解析，我们的意思是 $f$ 在一个包含 $A$ 的开集上解析。

在引言中我们提到，如果函数 $f$ 在开集 $G$ 上全纯，那么 $f$ 在 $G$ 上无穷次可微。这表明复可微性是一个极其强的条件：我们可以从它的定义来进行分析。

假设 $f\colon G\to \mathbb{C}$ 在 $z$ 处可微，则在 $z$ 的一个极小邻域内，我们有

$$
\begin{gather}
f(z+h) \approx f(z)+f'(z)h
\end{gather}
$$

几何上来看，$f$ 对 $z$ 的邻域的作用就相当于一个平移复合一个拉伸+旋转（回顾一下，乘以一个复数 $f'(z)$ 相当于对平面做均匀缩放和旋转）。从这一角度来看，复可微性比平面上实二元函数的可微性（Frechet 可微）更强，后者只需

$$
\begin{gather}
f(x+h) \approx f(x)+Lh
\end{gather}
$$

其中 $L=f'(x)$ 是一个线性映射。而复可微性不仅要求 $L$ 是线性映射，其还对线性映射的结构做出了限制，那就是所谓的 **Cauchy-Riemann 方程**，下面我们就来推导它。

设 $f\colon G\to \mathbb{C}$ 是一个解析函数，它可以写成

$$
\begin{gather}
f(x+iy)=u(x,y)+iv(x,y)
\end{gather}
$$

其中 $u,v$ 是连续可微的实函数。我们用两种不同的方法来计算极限

$$
\begin{gather}
\lim_{ h \to 0 } \dfrac{f(z+h)-f(z)}{h}
\end{gather}
$$

首先从 $h \in \mathbb{R}$ 开始，则我们有

$$
\begin{align}
f'(z) &= \lim_{ h \to 0 } \dfrac{f(x+h+iy)-f(x+iy)}{h} \\
&= \lim_{ h \to 0 } \dfrac{u(x+h,y)-u(x,y)}{h}+i \dfrac{v(x+h,y)-v(x,y)}{h} \\
&= \dfrac{ \partial u }{ \partial x } (x,y)+i \dfrac{ \partial v }{ \partial x } (x,y)
\end{align}
$$

现在我们令 $h$ 从纯虚数处趋于 $0$，即

$$
\begin{align}
f'(z) &= \lim_{ h \to 0 } \dfrac{f(x+iy+ih)-f(x+iy)}{ih} \\
&= \lim_{ h \to 0 } \dfrac{v(x,y+h)-v(x,y)}{h}-i \dfrac{u(x,y+h)-u(x,y)}{h} \\
&= \dfrac{ \partial v }{ \partial y } (x,y)-i \dfrac{ \partial u }{ \partial y } (x,y)
\end{align}
$$

将上述两式的实部与虚部等同，我们即得

$$
\begin{gather}
\dfrac{ \partial u }{ \partial x } =\dfrac{ \partial v }{ \partial y } , \quad \dfrac{ \partial v }{ \partial x } =-\dfrac{ \partial u }{ \partial y } 
\end{gather}
$$

从几何上，我们还可以使用另一种证明方法。根据前面关于复可微性的讨论，我们知道函数 $g(x,y)=(u(x,y),v(x,y))$ 的 Jacobian 矩阵

$$
\begin{gather}
\begin{pmatrix}
\dfrac{ \partial u }{ \partial x } & \dfrac{ \partial u }{ \partial y }  \\
\dfrac{ \partial v }{ \partial x } & \dfrac{ \partial v }{ \partial y } 
\end{pmatrix}
\end{gather}
$$

是一个均匀伸缩与一个旋转的乘积，也就是说它具有形式

$$
\begin{gather}
r \begin{pmatrix}
\cos\theta & -\sin\theta \\
\sin\theta & \cos\theta
\end{pmatrix}
\end{gather}
$$

将其与 $J_{g}$ 等同，我们立刻得到 Cauchy-Riemann 方程

$$
\begin{gather}
\dfrac{ \partial u }{ \partial x } =\dfrac{ \partial v }{ \partial y } , \quad \dfrac{ \partial v }{ \partial x } =-\dfrac{ \partial u }{ \partial y } 
\end{gather}
$$

现在假设 $u,v$ 具有二阶连续偏导数，对上式两边求偏导，我们可得

$$
\begin{gather}
\dfrac{ \partial ^{2} u }{ \partial x^{2} } +\dfrac{ \partial ^{2} u }{ \partial y^{2} } =\dfrac{ \partial ^{2} v }{ \partial x^{2} } +\dfrac{ \partial ^{2} v }{ \partial y^{2} }=0
\end{gather}
$$

满足上式的函数 $u,v$ 被称为**调和函数**（harmonic function），我们将在后面的章节研究它们。

另一方面，如果定义在开集 $G\subset \mathbb{R}^{2}$ 上的 $u,v$ 具有连续偏导数，并且满足 Cauchy-Riemann 方程，那么可以证明 $f(x+iy)=u(x,y)+iv(x,y)$ 在 $G$ 上是解析的。为此，我们设 $z=x+iy \in G$，则有 $B(z,r)\subset G$. 令 $h=s+it \in B(0,r)$，则有

$$
\begin{align}
&u(x+s,y+t)-u(x,y) \\
& =[u(x+s,y+t)-u(x,y+t)]+[u(x,y+t)-u(x,y)]
\end{align}
$$

应用中值定理，则对任意 $s+it$，存在 $|s'|<|s|,|t'|<|t|$ 使得

$$
\begin{gather}
u(x+s,y+t)-u(x,y+t)=\dfrac{ \partial u }{ \partial x } (x+s',y+t) s \\
u(x,y+t)-u(x,y)=\dfrac{ \partial u }{ \partial y } (x,y+t')t
\end{gather}
$$

令

$$
\begin{gather}
\varphi(s,t)=[u(x+s,y+t)-u(x,y)]-\left[ \dfrac{ \partial u }{ \partial x } (x,y)s+\dfrac{ \partial u }{ \partial y } (x,y)t \right]
\end{gather}
$$

则

$$
\begin{align}
\dfrac{\varphi(s,t)}{s+it}&=\dfrac{s}{s+it}\left( \dfrac{ \partial u }{ \partial x } (x+s',y+t)-\dfrac{ \partial u }{ \partial x } (x,y) \right) \\
&+\dfrac{t}{s+it}\left( \dfrac{ \partial u }{ \partial y } (x,y+t')-\dfrac{ \partial u }{ \partial y } (x,y) \right)
\end{align}
$$

由于 $|s|\leq|s+it|,|t|\leq|s+it|$，并且 $u$ 具有连续偏导数，因此我们有

$$
\begin{gather}
\lim_{ s+it \to 0 } \dfrac{\varphi(s,t)}{s+it}=0
\end{gather}
$$

同理，对于

$$
\begin{gather}
\psi(s,t)=[v(x+s,y+t)-v(x,y)]-\left[ \dfrac{ \partial v }{ \partial x } (x,y)s+\dfrac{ \partial v }{ \partial y } (x,y)t \right]
\end{gather}
$$

我们有

$$
\begin{gather}
\lim_{ s+it \to 0 } \dfrac{\psi(s,t)}{s+it}=0
\end{gather}
$$

现在，利用 $u,v$ 满足 Cauchy-Riemann 方程的条件，我们得到

$$
\begin{gather}
\dfrac{f(z+s+it)-f(z)}{s+it}=\dfrac{ \partial u }{ \partial x } (x,y)+i \dfrac{ \partial v }{ \partial x } (x,y)+\dfrac{\varphi(s,t)+\psi(s,t)}{s+it}
\end{gather}
$$

两边取 $s+it \to 0$ 时的极限，则 $f$ 全纯，并且有 $f'(z)=\dfrac{ \partial u }{ \partial x }+i \dfrac{ \partial v }{ \partial x }$. 由于 $u,v$ 是连续可微的，故 $f'$ 是连续的，从而 $f$ 是解析函数。我们将上述结果总结为以下定理：

**定理 1.3.3**

设 $u,v$ 是定义在开集 $G\subset \mathbb{C}$ 上的实函数，且具有连续偏导数，则定义为 $f(x+iy)=u(x,y)+iv(x,y)$ 的函数 $f\colon G\to \mathbb{C}$ 在 $G$ 上解析当且仅当 $u,v$ 满足 Cauchy-Riemann 方程

$$
\begin{gather}
\dfrac{ \partial u }{ \partial x } =\dfrac{ \partial v }{ \partial y } , \quad \dfrac{ \partial v }{ \partial x } =-\dfrac{ \partial u }{ \partial y } 
\end{gather}
$$

这里我们将 $\mathbb{C}$ 上的开集 $G$ 与 $\mathbb{R}^{2}$ 上的开集 $G$ 等同，因为它们之间有显然的同构。

关乎调和函数的另一个问题是，对于调和函数 $u\colon G\to \mathbb{R}$，是否存在另一个调和函数 $v\colon G\to \mathbb{R}$ 使得 $f=u+iv$ 是解析函数？如果这样的函数 $v$ 存在，则称其为 $u$ 的一个**调和共轭**（harmonic conjugate）。对于一般的开集 $G$，上面所说的函数 $v$ 并不一定存在。然而，对于一些特定的集合 $G$，其上的任意调和函数都有共轭，下面我们给出一例。

**定理 1.3.4**

令 $G$ 为 $\mathbb{C}$ 或者其上的任意开圆盘，如果 $u\colon G\to \mathbb{R}$ 是调和函数，那么 $u$ 有一个调和共轭。

**证明**

对于任意开圆盘 $B(z_{0},R)$，我们可以平移坐标系使得原点落在 $z_{0}$ 处，此时圆盘可以表示为 $G=B(0,R)$. 令 $u\colon G\to \mathbb{R}$ 为调和函数，我们要找到一个调和函数 $v$ 使得 $u,v$ 满足 Cauchy-Riemann 方程。因此我们定义

$$
\begin{gather}
v(x,y)=\int_{0}^{y} \dfrac{ \partial u }{ \partial x } (x,t) \mathrm{d} t+\varphi(x)
\end{gather}
$$

其中 $\varphi$ 是一个待定函数使得 $\dfrac{ \partial v }{ \partial x }=-\dfrac{ \partial u }{ \partial y }$. 由于 $u$ 是 $C^{2}$ 连续的，故根据 Leibnitz 法则得

$$
\begin{align}
\dfrac{ \partial v }{ \partial x } (x,y) &= \int_{0}^{y} \dfrac{ \partial ^{2} u }{ \partial x^{2} } (x,t)\mathrm{d} t+\varphi'(x) \\
&= - \int_{0}^{y} \dfrac{ \partial ^{2}u }{ \partial y^{2} } (x,t)\mathrm{d} t+\varphi'(x) \\
&= -\dfrac{ \partial u }{ \partial y } (x,y)+\dfrac{ \partial u }{ \partial y } (x,0)+\varphi'(x)
\end{align}
$$

因此我们有 $\varphi'(x)=-\dfrac{ \partial u }{ \partial y }(x,0)$，这给出

$$
\begin{gather}
v(x,y)=\int_{0}^{y} \dfrac{ \partial u }{ \partial x } (x,t)\mathrm{d} t-\int_{0}^{x} \dfrac{ \partial u }{ \partial y } (s,0)\mathrm{d} s
\end{gather}
$$

这里 $G$ 的定义保证了上述积分均有定义。容易验证这样定义的 $u,v$ 满足 Cauchy-Riemann 方程，这就完成了证明。

对于更进一步的结论，我们将在后续的章节进行研究。

现在我们来实际构造一些解析函数。显然常值函数 $1$ 与恒等函数 $z$ 都是解析的，从而根据导数的线性性和乘积与商法则，可知任意多项式与有理函数（两个多项式的商）在分母不为零处都是解析的。

更进一步来说，幂级数的理论告诉我们，收敛半径为 $R$ 的幂级数 $\sum_{n=0}^{\infty}c_{n}(z-z_{0})^{n}$ 在开圆盘 $B(z_{0},R)$ 内部无穷次可微，因而其在 $B(z_{0},R)$ 上解析。在这其中，有三个幂级数特别重要，它们定义为

$$
\begin{gather}
e^{z}=\exp z=\sum_{n=0}^{\infty} \dfrac{z^{n}}{n!} \\
\cos z=\sum_{n=0}^{\infty} (-1)^{n} \dfrac{z^{2n}}{(2n)!} \\
\sin z=\sum_{n=0}^{\infty} (-1)^{n} \dfrac{z^{2n+1}}{(2n+1)!}
\end{gather}
$$

分别被称作**指数函数**，**余弦函数**和**正弦函数**。根据比值判别法，它们均在整个平面 $\mathbb{C}$ 上解析。此外，通过对级数进行换序求和（由于级数绝对收敛故可行），我们可得 **Euler 公式**

$$
\begin{gather}
e^{iz}=\cos z+i\sin z
\end{gather}
$$

从而我们可以将复数的极坐标形式写成 $z=re^{i\theta}$，其中 $r=|z|,\theta=\mathrm{arg}\,z$. 从上式中我们还可知，指数函数 $e^{z}$ 在复数上具有周期 $2k\pi i$，这一性质在实数上是完全不可见的。

接下来我们来定义**对数函数** $\log z$. 我们可以像指数、三角函数一样，使用其在实数上的幂级数进行定义，但这只能给我们在一个圆盘上的定义。此外，由于 $e^{z}$ 在 $\mathbb{C}$ 上不是单射，因此我们也不能将 $\log z$ 定义为 $e^{z}$ 的反函数。不过，我们可以做一些类似的事。

我们定义对数的动机是想要找到一个函数 $f$，使得 $\exp f(z)=z$ 对任意 $z\neq 0$ 成立。因此，我们可以来考虑方程 $e^{z}=w$，其中 $w\neq 0$ 的解集。对方程两边取模长，得到 $\exp(\mathrm{Re}\,z)=|w|$，于是有 $\mathrm{Re}\,z=\log|w|$，从而 $\exp(i\mathrm{Im}\,z)=\exp(i\mathrm{arg}\,w)$，即 $\mathrm{Im}\,z=\mathrm{arg}\,w+2k\pi$，因此

$$
\begin{gather}
\{ \log|w|+i(\mathrm{arg}\,w+2k\pi) \mid k \in \mathbb{Z} \}
\end{gather}
$$

是方程 $e^{z}=w$ 的解集（注意此处的 $\log|w|$ 是实对数）。

**定义 1.3.5** 对数的分支（branch of the logarithm）

设 $G\subset \mathbb{C}$ 是连通开集，如果 $f\colon G\to \mathbb{C}$ 是一个连续函数，使得 $\exp f(z)=z$ 对任意 $z \in G$ 成立，则称 $f$ 是**对数的一个分支**，记作 $\log z$.

假设 $f$ 是对数的一个分支，令 $g(z)=f(z)+2k\pi i$，其中 $k \in \mathbb{Z}$，则 $\exp g(z)=\exp f(z)=z$，因此 $g$ 也是对数的一个分支。反过来说，如果 $f,g$ 均为对数的分支，那么对任意 $z \in G$，有 $g(z)=f(z)+2k\pi i$ 成立，其中 $k$ 与 $z$ 有关。我们可以证明对任意 $z \in G$，其对应的 $k$ 是相同的：事实上，令 $h(z)=\dfrac{1}{2\pi i}(f(z)-g(z))$，则 $h$ 是连续函数，又由于 $G$ 是连通集，故 $h[G]\subset \mathbb{Z}$ 也是连通集，从而 $h(z)=k$ 为常值函数。这给出

**定理 1.3.6**

设 $G\subset \mathbb{C}$ 是连通开集，$f\colon G\to \mathbb{C}$ 是对数的一个分支，则对数的所有分支都具有形式 $f(z)+2k\pi i$，其中 $k \in \mathbb{Z}$.

现在我们来构造单个分支中的对数函数。令

$$
\begin{gather}
G=\mathbb{C} \setminus \{ z \mid z\leq 0 \}
\end{gather}
$$

换句话说，将复平面沿着负实轴“割开”。显然 $G$ 是连通开集，并且每个 $z \in G$ 都可以唯一地表示为 $z=|z|e^{i\theta}$，其中 $-\pi<\theta<\pi$. 对于这个范围内的 $\theta$，映射 $\theta\mapsto(\cos\theta,\sin\theta)$ 是单射，因此当 $r_{n}e^{i\theta_{n}}\to re^{i\theta}$ 时我们可证 $r_{n}\to r$ 且 $\theta_{n}\to\theta$. 这表明函数 $f(re^{i\theta})=\log r+i\theta$ 是连续的，且是对数的一个分支，称为**主分支**（principal branch）。

$f$ 是解析函数吗？为回答这个问题，我们首先证明一个广义的结论。

**定理 1.3.7**

设 $G,\Omega \subset \mathbb{C}$ 是开集，假设 $f\colon G\to \mathbb{C}$ 和 $g\colon\Omega\to \mathbb{C}$ 是连续函数，满足 $f[G]\subset\Omega$ 且 $g(f(z))=z$ 对任意 $z \in G$ 成立，则如果 $g$ 全纯并且 $g'\neq 0$，那么 $f$ 全纯，并且

$$
\begin{gather}
f'(z)=\dfrac{1}{g'(f(z))}
\end{gather}
$$

从而如果 $g$ 解析，那么 $f$ 解析。

**证明**

取 $a \in G$ 与 $h\neq 0$ 使得 $a+h \in G$，于是 $a=g(f(a)),a+h=g(f(a+h))$ 表明 $f(a)\neq f(a+h)$. 我们有

$$
\begin{align}
1 &= \dfrac{g(f(a+h))-g(f(a))}{h} \\
&= \dfrac{g(f(a+h))-g(f(a))}{f(a+h)-f(a)} \cdot \dfrac{f(a+h)-f(a)}{h}
\end{align}
$$

对左边取 $h\to 0$ 的极限，其极限值显然为 $1$，因此等式右边的极限存在。又因为 $\lim_{ h \to 0 }(f(a+h)-f(a))=0$，故

$$
\begin{gather}
\lim_{ h \to 0 } \dfrac{g(f(a+h))-g(f(a))}{f(a+h)-f(a)}=g'(f(a))
\end{gather}
$$

从而我们有

$$
\begin{gather}
\lim_{ h \to 0 } \dfrac{f(a+h)-f(a)}{h}=\dfrac{1}{g'(f(a))}
\end{gather}
$$

即 $f'(a)=g'(f(a))^{-1}$. 如果 $g$ 是解析的，那么 $g'$ 连续，从而 $f'$ 是连续的，即证 $f$ 解析。

由此，我们得到推论

**定理 1.3.8**

对数的一个分支是解析的，其导数为 $1 / z$.

如果没有额外说明，当我们写 $\log z$ 时，我们均默认它是对数的主分支。给定对数的一个分支 $\log z$ 及其定义域 $G$，$b \in \mathbb{C}$，我们定义幂函数 $z^{b}$ 的一个分支为 $g(z)=\exp(b \log z)$. 同样，当我们写 $z^{b}$ 时，我们默认取对数的主分支。显然，$z^{b}$ 是解析的，因为 $\log z$ 是。

从上面的讨论我们可以看出，连通性在解析函数理论中具有重要意义。实际上，我们可以将连通开集视为实数中区间的对应。例如，下面的定理在 $G$ 不连通时是不成立的。

**定理 1.3.9**

设 $G\subset \mathbb{C}$ 是连通开集，$f\colon G\to \mathbb{C}$ 是全纯函数，满足 $f'(z)=0$ 对任意 $z \in G$ 成立，则 $f$ 是常值函数。

**证明**

固定 $z_{0}\in G$，令 $w_{0}=f(z_{0})$. 取 $A=\{ z \in G \mid f(z)=w_{0} \}$，我们要证 $A$ 在 $G$ 中是既开又闭的，从而 $A=G$.

令 $z \in G$ 并令序列 $(z_{n})\subset A$ 收敛于 $z$，则 $f(z_{n})=w_{0}$ 且 $f(z_{n})\to f(z)$，从而 $f(z)=w_{0}$，$z \in A$，因此 $A$ 是闭的。现在设 $a \in A$，则有开球 $B(a,\varepsilon)\subset G$，如果 $z \in B(a,\varepsilon)$，定义 $g(t)=f(tz+(1-t)a)$，则根据链式法则有

$$
\begin{gather}
g'(t)=f'(tz+(1-t)a)(z-a)=0
\end{gather}
$$

对 $0\leq t\leq 1$ 成立，从而 $g$ 是常值函数，$f(z)=g(1)=g(0)=f(a)=w_{0}$，因此 $B(a,\varepsilon)\subset A$，这表明 $A$ 是开集。这就完成了证明。

鉴于连通开集的重要性，我们通常将其称为一个**区域**（region）。

# Section 4: 解析函数作为平面的变换

本节我们继续深化复函数的几何视角，也即，将复函数视为平面上的变换，而非一个二维输入、二维输出的函数。以函数 $f(z)=z^{2}$ 为例，当 $z=x+iy$ 时有 $f(z)=\mu+i\nu$，其中 $\mu=x^{2}-y^{2},\nu=2xy$. 因此，双曲线 $x^{2}-y^{2}=c$ 和 $2xy=d$ 经 $f$ 变换后成为了直线 $\mu=c$ 和 $\nu=d$.

现在我们考虑直线 $x=c$ 和 $y=d$ 经 $f$ 变换后得到的图形。对于 $x=c$，我们有 $\mu=c^{2}-y^{2},\nu=2cy$，消去 $y$ 后得到抛物线 $\nu^{2}=-4c^{2}(\mu-c^{2})$，类似地，直线 $y=d$ 被 $f$ 映射到抛物线 $\nu^{2}=4d^{2}(\mu+d^{2})$. 这两个抛物线交于 $(c^{2}-d^{2},\pm 2|cd|)$.

一个中心在原点的圆会变成什么？如果 $z=re^{i\theta}$，那么 $f(z)=r^{2}e^{2i\theta}$，因此，半径为 $r$ 的圆被映射为一个半径为 $r^{2}$ 的圆，并且当 $z$ 沿着圆走过一圈时，$z^{2}$ 沿着圆走过两圈。

最后，我们考虑扇形 $S(\alpha,\beta)=\{ z \mid \alpha<\mathrm{arg}\,z<\beta \}$. 容易看出它在映射 $f$ 下的像是扇形 $S(2\alpha,2\beta)$，并且 $f|_{S(\alpha,\beta)}$ 是单射当且仅当 $\beta-\alpha<\pi$.

以上的讨论阐明了映射 $f(z)=z^{2}$ 的一些性质。其中，我们指出该映射的一个相当有趣的性质：双曲线 $x^{2}-y^{2}=c$ 和 $2xy=d$ 在交点处形成了一个直角，就如同它们的像一样；另一边，直线 $x=c,y=d$ 以直角相交，与它们的像相同，如图所示：

![](1-3.png)
![](1-4.png)

从直观上看，这一“保角”性质是 $z^{2}$ 解析性的直接体现：在局部邻域内，应用 $f$ 就相当于应用一个缩放与旋转，其当然不会改变线条之间的相对角度。下面我们就来将这一思想严格化。

**定义 1.4.1** 路径（path），光滑路径（smooth path），分段光滑（piecewise smooth）

区域 $G\subset \mathbb{C}$ 中的一条**路径**是一个连续函数 $\gamma\colon[a,b]\to G$. 如果 $\gamma$ 可微并且 $\gamma'$ 在 $[a,b]$ 上连续，那么就称 $\gamma$ 是一条**光滑路径**。称 $\gamma$ 是**分段光滑的**，如果存在 $[a,b]$ 的划分 $a=t_{0}<t_{1}<\dots<t_{n}=b$ 使得 $\gamma$ 在每个 $[t_{j-1},t_{j}]$ 上光滑。

> 在数学的惯例中，“光滑”通常指代的是 $C^{\infty}$ 连续。然而，这里的“光滑”指代的是 $C^{1}$ 连续，这是由于历史惯例所致。此外，$C^{1}$ 连续性对后续的理论已经足够，引入更强的连续性不会得到更强的结果。因此，在不致歧义的情况下，我们将“光滑”与 $C^{1}$ 连续等同。

假设 $\gamma\colon[a,b]\to G$ 是一条光滑路径，且存在 $t_{0}\in(a,b)$ 使得 $\gamma'(t_{0})\neq 0$，则 $\gamma$ 在 $z_{0}=\gamma(t_{0})$ 处有切线，其经过 $z_{0}$ 且与 $\gamma'(t_{0})$ 的方向相同。如果 $\gamma_{1},\gamma_{2}$ 是光滑路径，满足 $\gamma_{1}(t_{1})=\gamma_{2}(t_{2})=z_{0}$ 且 $\gamma_{1}'(t_{1})\neq 0,\gamma_{2}'(t_{2})\neq 0$，则我们可以定义路径 $\gamma_{1},\gamma_{2}$ 在 $z_{0}$ 处的**夹角**为

$$
\begin{gather}
\mathrm{arg}\,\gamma_{2}'(t_{2})-\mathrm{arg}\,\gamma_{1}'(t_{1})
\end{gather}
$$

再设 $f\colon G\to \mathbb{C}$ 是解析函数，则 $\sigma=f\circ\gamma$ 也是光滑路径，并且 $\sigma'(t)=f'(\gamma(t))\gamma'(t)$. 令 $z_{0}=\gamma(t_{0})$，并假设 $\gamma'(t_{0})\neq 0,f'(z_{0})\neq 0$，则 $\sigma'(t_{0})\neq 0$ 且 $\mathrm{arg}\,\sigma'(t_{0})=\mathrm{arg}\,f'(z_{0})+\mathrm{arg}\,\gamma'(t_{0})$，即

$$
\begin{gather}
\mathrm{arg}\,\sigma'(t_{0})-\mathrm{arg}\,\gamma'(t_{0})=\mathrm{arg}\,f'(z_{0})
\end{gather}
$$

现在令 $\gamma_{1},\gamma_{2}$ 如前文所示，$\sigma_{1}=f\circ\gamma_{1},\sigma_{2}=f\circ\gamma_{2}$，并假设 $\gamma_{1},\gamma_{2}$ 在 $z_{0}$ 处不相切，即 $\gamma_{1}'(t_{1})\neq\gamma_{2}'(t_{2})$，则我们有

$$
\begin{gather}
\mathrm{arg}\,\sigma_{1}'(t_{1})-\mathrm{arg}\,\sigma_{2}'(t_{2})=\mathrm{arg}\,\gamma_{1}'(t_{1})-\mathrm{arg}\,\gamma_{2}'(t_{2})
\end{gather}
$$

这表明，解析函数 $f$ 将两条交于 $z_{0}$ 的光滑路径映射到两条交于 $f(z_{0})$ 的光滑路径，并且当 $f'(z_{0})\neq 0$ 时，$f$ 保持了两条路径夹角的大小与方向不变。这种性质称为**保角性质**。则以上讨论可以总结为如下定理：

**定理 1.4.2**

区域 $G\subset \mathbb{C}$ 上的解析函数 $f$ 在 $f'(z)\neq 0$ 的点 $z$ 上具有保角性质。

如果一个函数 $f\colon G\to \mathbb{C}$ 具有保角性质，并且极限

$$
\begin{gather}
\lim_{ z \to a } \dfrac{|f(z)-f(a)|}{|z-a|}
\end{gather}
$$

存在，则称函数 $f$ 是一个**共形映射**（conformal map）。于是，上述定理就可以表述为：如果 $f\colon G\to \mathbb{C}$ 是解析函数并且 $f'(z)\neq 0$ 对任意 $z$ 成立，那么 $f$ 是一个共形映射。这一结论的逆命题也成立，我们将在后续的章节中进行证明。

设 $f(z)=e^{z}$，则根据定理，它在 $\mathbb{C}$ 上是共形的。我们来仔细研究它的映射性质。如果 $z=c+iy$，其中 $c$ 是常数，则 $f(z)=e^{c}e^{iy}=re^{iy}$. 这就是说，$f$ 将竖直的直线 $x=c$ 映射到中心在原点，半径为 $e^{c}$ 的圆；如果 $z=x+id$，则 $f(z)=e^{x}e^{id}$，即 $f$ 将水平的直线 $y=d$ 映射到从原点射出的射线 $\{ re^{id} \mid r> 0 \}$.

![](1-5.png)

对数函数 $\log z$ 则与之相反：其将圆映射为竖直的线段（取主分支），将射线映射为水平的直线。

接下来我们考虑一类非常重要的变换：**Mobius 变换**。

**定义 1.4.3** 分式线性变换（linear fractional transformation），Mobius 变换

一个具有形式 $S(z)=\dfrac{az+b}{cz+d}$ 的映射称为一个**分式线性变换**。如果进一步有 $ad-bc\neq 0$，则称 $S$ 是一个 **Mobius 变换**。

当 $S$ 是 Mobius 变换时，我们可以验证 $S^{-1}(z)=\dfrac{dz-b}{-cz+a}$ 是 $S$ 的逆变换，即 $S\circ S^{-1}(z)=S^{-1}\circ S(z)=z$. 显然，两个分式线性变换的复合仍然是分式线性变换，因此所有 Mobius 变换在函数复合下构成了一个群。除非明确指定，否则我们将仅考虑是 Mobius 变换的分式线性变换。

令 $S(z)=\dfrac{az+b}{cz+d}$，我们考虑 $S$ 在 $\mathbb{C}_{\infty}$ 上的行为，其中我们定义 $S(\infty)=a /c$ 且 $S(-d /c)=\infty$. 注意我们不会遇到 $a=c=0$ 或者 $c=d=0$ 的情况，因为这与 $ad-bc\neq 0$ 的条件矛盾。由于 $S$ 有一个逆变换，因此它是 $\mathbb{C}_{\infty}$ 到 $\mathbb{C}_{\infty}$ 的一个双射。

关于 Mobius 变换的一个基本性质是它可以分解为一系列简单映射的复合，包括**平移**（translation）$S(z)=z+a$，**缩放**（dilation）$S(z)=az$，**旋转**（rotation）$S(z)=e^{i\theta}z$，以及**反演**（inversion）$S(z)=1 /z$. 注意这里的缩放系数 $a \in \mathbb{C}$，因此其带有旋转的分量。

**定理 1.4.4**

如果 $S$ 是一个 Mobius 变换，那么 $S$ 是平移、缩放和反演的复合。

**证明**

首先假设 $c=0$，则 $S(z)=(a /d)z+(b / d)$，因此设 $S_{1}(z)=(a /d)z$，$S_{2}(z)=z+(b /d)$，我们有 $S=S_{2}\circ S_{1}$.

现设 $c\neq 0$，则

$$
\begin{align}
\dfrac{az+b}{cz+d} = \dfrac{(a /c)z+(b /c)}{z+(d /c)} = \dfrac{a}{c}+ \dfrac{(bc-ad) / c^{2}}{z+(d /c)}
\end{align}
$$

因此，令 $S_{1}=z+(d /c)$，$S_{2}=1 /z$，$S_{3}=\dfrac{bc-ad}{c^{2}}z$，$S_{4}=z+(a /c)$，则 $S=S_{4}\circ S_{3}\circ S_{2}\circ S_{1}$，这就完成了证明。

$S$ 的不动点有哪些？也就是说，点 $z$ 使得 $S(z)=z$. 将 $S$ 的表达式代入，我们得到方程

$$
\begin{gather}
cz^{2}+(d-a)z-b=0
\end{gather}
$$

因此，除了恒等映射 $S(z)=z$，Mobius 变换最多有两个不动点。

现在设 $S\colon \mathbb{C}_{\infty}\to \mathbb{C}_{\infty}$ 是一个 Mobius 变换，并令 $a,b,c$ 是 $\mathbb{C}_{\infty}$ 中不同的三点使得 $\alpha=S(a),\beta=S(b),\gamma=S(c)$. 假设 $T$ 是另一个 Mobius 变换使得 $\alpha=T(a),\beta=T(b),\gamma=T(c)$，则 $T^{-1}\circ S$ 拥有不动点 $a,b,c$，这表明 $S=T$. 上述讨论表明，一旦确定了三个点上的取值，$\mathbb{C}_{\infty}$ 上的 Mobius 变换是唯一的。

现在令 $z_{2},z_{3},z_{4}\in \mathbb{C}_{\infty}$ 为不同点，我们定义 $S\colon \mathbb{C}_{\infty}\to \mathbb{C}_{\infty}$ 如下：

$$
\begin{gather}
S(z)=\begin{cases}
\left( \dfrac{z-z_{3}}{z-z_{4}} \right) / \left( \dfrac{z_{2}-z_{3}}{z_{2}-z_{4}} \right), & z_{2},z_{3},z_{4}\in \mathbb{C} \\
\dfrac{z-z_{3}}{z-z_{4}}, & z_{2}=\infty \\
\dfrac{z_{2}-z_{4}}{z-z_{4}}, & z_{3}=\infty \\
\dfrac{z-z_{3}}{z_{2}-z_{3}}, & z_{4}=\infty
\end{cases}
\end{gather}
$$

则 $S$ 将 $z_{2}$ 映射到 $1$，将 $z_{3}$ 映射到 $0$，将 $z_{4}$ 映射到 $\infty$. 根据前面的讨论，$S$ 是满足这一性质的唯一映射。

**定义 1.4.5** 交比（cross ratio）

设 $z_{1}\in \mathbb{C}_{\infty}$，定义 $z_{1},z_{2},z_{3},z_{4}$ 的**交比** $(z_{1},z_{2},z_{3},z_{4})$ 为 $z_{1}$ 在将 $z_{2}$ 映射到 $1$，将 $z_{3}$ 映射到 $0$，将 $z_{4}$ 映射到 $\infty$ 的唯一 Mobius 变换下的像。

**定理 1.4.6**

如果 $z_{2},z_{3},z_{4}$ 是不同点，$T$ 是任意 Mobius 变换，则对任意 $z_{1}$ 有

$$
\begin{gather}
(z_{1},z_{2},z_{3},z_{4})=(Tz_{1},Tz_{2},Tz_{3},Tz_{4})
\end{gather}
$$

**证明**

令 $S$ 为 $Sz=(z,z_{2},z_{3},z_{4})$，则 $M=S\circ T^{-1}$ 是一个 Mobius 变换，满足 $M(Tz_{2})=1,M(Tz_{3})=0,M(Tz_{4})=\infty$，则

$$
\begin{gather}
Mz=S\circ T^{-1}z=(z,Tz_{2},Tz_{3},Tz_{4})
\end{gather}
$$

令 $z_{1}=T^{-1}z$ 即证。

下面我们证明，$\mathbb{C}_{\infty}$ 上的三个点完全确定了一个 Mobius 变换。

**定理 1.4.7**

设 $z_{2},z_{3},z_{4}\in \mathbb{C}_{\infty}$ 是不同点，$w_{2},w_{3},w_{4}\in \mathbb{C}_{\infty}$ 也是不同点，则存在唯一的一个 Mobius 变换 $S\colon \mathbb{C}_{\infty}\to \mathbb{C}_{\infty}$ 使得 $Sz_{2}=w_{2},Sz_{3}=w_{3},Sz_{4}=w_{4}$.

**证明**

根据前文可知，如果存在这样一个 Mobius 变换，那么它一定是唯一的。现在我们来证明存在性。设 $Tz=(z,z_{2},z_{3},z_{4})$，$Mw=(w,w_{2},w_{3},w_{4})$，令 $S=M^{-1}\circ T$，我们来验证 $S$ 满足所要求的性质。

设 $z=z_{2}$，则 $Tz=1$，从而 $Sz=M^{-1}(1)=w_{2}$. 同理我们可以计算出 $Tz_{3}=0,Tz_{4}=\infty$，从而 $Sz_{3}=w_{3},Sz_{4}=w_{4}$，这就完成了证明。

一个众所周知的事实是，在平面 $\mathbb{C}$ 上，三个不共线的点唯一确定一个圆。而在 $\mathbb{C}_{\infty}$ 上，我们可以去除共线的条件：在球极投影下，一条直线被映射为球面上一个经过无穷远点 $\infty$ 的圆。在之后的定理中，我们所说的“圆”指的是 $\mathbb{C}_{\infty}$ 上的圆。

**定理 1.4.8**

设 $z_{1},z_{2},z_{3},z_{4}$ 是 $\mathbb{C}_{\infty}$ 上的不同点，则 $(z_{1},z_{2},z_{3},z_{4})\in \mathbb{R}$ 当且仅当四点位于同一圆上。

**证明**

令 $Sz=(z,z_{2},z_{3},z_{4})$，则 $S^{-1}[\mathbb{R}]$ 就是使得 $(z,z_{2},z_{3},z_{4})\in \mathbb{R}$ 的 $z$ 构成的集合。因此，我们只需证明 $\mathbb{R}_{\infty}=\mathbb{R}\cup \{ \infty \}$ 在 Mobius 变换下的像是圆即可。于是可知 $S^{-1}[\mathbb{R}_{\infty}]$ 是经过 $z_{2},z_{3},z_{4}$ 的圆，从而 $(z_{1},z_{2},z_{3},z_{4})\in \mathbb{R}$ 当且仅当 $z_{1}\in S^{-1}[\mathbb{R}]$ 当且仅当 $z_{1},z_{2},z_{3},z_{4}$ 共圆。

设 $Sz=\dfrac{az+b}{cz+d}$，如果 $x \in \mathbb{R}$ 且 $w=S^{-1}x$，则 $x=Sw$ 表明 $Sw=\overline{Sw}$，即

$$
\begin{gather}
\dfrac{aw+b}{cw+d}=\dfrac{\overline{a}\overline{w}+\overline{b}}{\overline{c}\overline{w}+\overline{d}}
\end{gather}
$$

从而有

$$
\begin{gather}
(a \overline{c}-\overline{a}c)|w|^{2}+(a \overline{d}-\overline{b}c)w+(b \overline{c}-\overline{a}d)\overline{w}+(b \overline{d}-\overline{b}d)=0
\end{gather}
$$

当 $a \overline{c}\in \mathbb{R}$ 时，有 $a \overline{c}-\overline{a}c=0$，令 $\alpha=2(a \overline{d}-\overline{b}c),\beta=i(b \overline{d}-\overline{b}d)$，则上式变成

$$
\begin{gather}
0=\mathrm{Im}(\alpha w)-\beta=\mathrm{Im}(\alpha w-\beta)
\end{gather}
$$

其中第二个等式成立因为 $\beta \in \mathbb{R}$. 上式表明，$w$ 位于 $\mathbb{C}$ 的一条直线上。

当 $a \overline{c}$ 不是实数时，我们有

$$
\begin{gather}
|w|^{2}+\overline{\gamma}w+\gamma \overline{w}-\delta=0
\end{gather}
$$

其中 $\gamma \in \mathbb{C},\delta \in \mathbb{R}$，于是我们可得

$$
\begin{gather}
|w+\gamma|=\sqrt{ |\gamma|^{2}+\delta }=\left\lvert  \dfrac{ad-bc}{\overline{a}c-a \overline{c}}  \right\rvert >0
\end{gather}
$$

这是 $\mathbb{C}$ 上圆的方程，这就完成了证明。

**定理 1.4.9**

Mobius 变换将圆映射到圆。

**证明**

设 $\Gamma$ 是 $\mathbb{C}_{\infty}$ 中的圆，$S$ 为任意 Mobius 变换。令 $z_{2},z_{3},z_{4}$ 为 $\Gamma$ 上不同的三点，$w_{j}=Sz_{j}$，则 $w_{2},w_{3},w_{4}$ 确定了一个圆 $\Gamma'$，我们断言 $S[\Gamma]=\Gamma'$. 事实上，对任意 $z \in \mathbb{C}_{\infty}$，我们有

$$
\begin{gather}
(z,z_{2},z_{3},z_{4})=(Sz,w_{2},w_{3},w_{4})
\end{gather}
$$

如果 $z \in\Gamma$，那么根据定理 1.4.8，上式左右两边是实数，从而再次应用 1.4.8，可知 $Sz \in\Gamma'$. 反之，如果 $w \in\Gamma'$，则

$$
\begin{gather}
(w,w_{2},w_{3},w_{4})=(S^{-1}w,z_{2},z_{3},z_{4})
\end{gather}
$$

是实数，于是存在 $z=S^{-1}w \in\Gamma$ 使得 $Sz=w$，这就完成了证明。

从该定理的证明过程中我们可知，如果 $\Gamma,\Gamma'$ 是 $\mathbb{C}_{\infty}$ 中的两个圆，$z_{2},z_{3},z_{4}\in\Gamma$，$w_{2},w_{3},w_{4}\in\Gamma'$，那么将 $z_{j}$ 映射为 $w_{j}$ 的 Mobius 变换 $T$ 将 $\Gamma$ 映射到 $\Gamma'$. 此外，根据定理 1.4.7，这样的映射 $T$ 是唯一的。我们将以上结论总结为以下定理：

**定理 1.4.10**

给定 $\mathbb{C}_{\infty}$ 中的圆 $\Gamma$ 和 $\Gamma'$，存在 Mobius 变换 $T$ 使得 $T[\Gamma]=\Gamma'$. 进一步，我们可以构造 $T$ 使得 $\Gamma$ 上的任意三点被映射为 $\Gamma'$ 上的任意三点。如果我们的确指定了 $Tz_{j}$（其中各 $z_{j}$ 是不同点），那么 $T$ 是唯一的。

现在我们知道了 Mobius 变换在圆上的作用，下一个问题是：圆的内部和外部被映射成了什么？为此，我们需要引入一些新的概念。

**定义 1.4.11** 对称（symmetric）

设 $\Gamma$ 是经过点 $z_{2},z_{3},z_{4}$ 的圆，我们称 $z,z^{*}\in \mathbb{C}_{\infty}$ 关于 $\Gamma$ **对称**，如果

$$
\begin{gather}
(z^{*},z_{2},z_{3},z_{4})=\overline{(z,z_{2},z_{3},z_{4})}
\end{gather}
$$

根据定理 1.4.8，圆上的点关于自身是对称的。

现在我们来建立关于对称性的几何图像。如果 $\Gamma$ 是 $\mathbb{C}$ 上的一条直线，那么我们能够期望 $z$ 和 $z^{*}$ 位于 $\Gamma$ 的两侧、到直线的距离相同、并且 $[z,z^{*}]$ 垂直于 $\Gamma$. 事实也确实如此。

取 $z_{4}=\infty$，则 $\Gamma$ 在 $\mathbb{C}_{\infty}$ 上是经过无穷远点的圆，从而在球极投影下成为一条直线。对称性的定义给出

$$
\begin{gather}
\dfrac{z^{*}-z_{3}}{z_{2}-z_{3}}=\dfrac{\overline{z}-\overline{z}_{3}}{\overline{z}_{2}-\overline{z}_{3}}
\end{gather}
$$

于是有 $|z^{*}-z_{3}|=|z-z_{3}|$，由于 $z_{3}$ 可以任意选取，因此 $z$ 和 $z^{*}$ 到 $\Gamma$ 上每一点的距离相同。另一方面，我们有

$$
\begin{align}
\mathrm{Im}\, \dfrac{z^{*}-z_{3}}{z_{2}-z_{3}}=\mathrm{Im}\, \dfrac{\overline{z}-\overline{z}_{3}}{\overline{z}_{2}-\overline{z}_{3}}=-\mathrm{Im}\, \dfrac{z-z_{3}}{z_{2}-z_{3}}
\end{align}
$$

因此，除非 $z \in\Gamma$，否则 $z$ 和 $z^{*}$ 分属 $\Gamma$ 的两侧，即证 $[z,z^{*}]$ 垂直于 $\Gamma$.

现在我们设 $\Gamma$ 是 $\mathbb{C}$ 上的圆 $\{ z \mid |z-a|=R \}$，令 $z_{2},z_{3},z_{4}$ 为 $\Gamma$ 上的点，应用定理 1.4.6 可得

$$
\begin{align}
(z^{*},z_{2},z_{3},z_{4}) &= \overline{(z,z_{2},z_{3},z_{4})} \\
&= \overline{(z-a,z_{2}-a,z_{3}-a,z_{4}-a)} \\
&= \left( \overline{z}-\overline{a}, \dfrac{R^{2}}{z_{2}-a}, \dfrac{R^{2}}{z_{3}-a}, \dfrac{R^{2}}{z_{4}-a} \right) \\
&= \left( \dfrac{R^{2}}{\overline{z}-\overline{a}},z_{2}-a,z_{3}-a,z_{4}-a \right) \\
&= \left( \dfrac{R^{2}}{\overline{z}-\overline{a}}+a,z_{2},z_{3},z_{4} \right)
\end{align}
$$

于是 $z^{*}=a+R^{2} /(\overline{z}-\overline{a})$，即 $(z^{*}-a)(\overline{z}-\overline{a})=R^{2}$，这给出

$$
\begin{gather}
\dfrac{z^{*}-a}{z-a}=\dfrac{R^{2}}{|z-a|^{2}}> 0
\end{gather}
$$

因此 $z^{*}$ 位于连接 $a$ 和 $z$ 的射线 $\{ a+t(z-a) \mid t>0 \}$ 上，并且满足 $|z^{*}-a||z-a|=R^{2}$. 根据以上条件，我们可以按下图来得到 $z^{*}$：

![](1-6.png)

如图，假设 $z$ 在 $\Gamma$ 内部，令 $L$ 为连接 $a$ 与 $z$ 的射线，在 $z$ 处构造垂直于 $L$ 的直线 $P$，在 $P$ 与 $\Gamma$ 的交点处构造 $\Gamma$ 的切线，其与 $L$ 的交点就是 $z^{*}$. 从这一角度看，点 $a$ 与无穷远点 $\infty$ 关于 $\Gamma$ 是对称的。

**定理 1.4.12** 对称原理（Symmetry Principle）

设 $T$ 是一个将圆 $\Gamma_{1}$ 映射到圆 $\Gamma_{2}$ 的 Mobius 变换，则 $T$ 将任意一对关于 $\Gamma_{1}$ 对称的点映射到一对关于 $\Gamma_{2}$ 对称的点。

**证明**

设 $z_{2},z_{3},z_{4}\in\Gamma_{1}$，如果 $z$ 和 $z^{*}$ 关于 $\Gamma_{1}$ 对称，则有

$$
\begin{align}
(Tz^{*},Tz_{2},Tz_{3},Tz_{4}) &= (z^{*},z_{2},z_{3},z_{4}) \\
&= \overline{(z,z_{2},z_{3},z_{4})} \\
&= \overline{(Tz,Tz_{2},Tz_{3},Tz_{4})}
\end{align}
$$

这就是说，$Tz^{*}$ 与 $Tz$ 关于 $\Gamma_{2}$ 对称，这就完成了证明。

一个圆将 $\mathbb{C}_{\infty}$ 分成了两个部分，然而，我们遇到一个问题：在球面 $\mathbb{C}_{\infty}$ 上，不存在一种典范的“内部”和“外部”的区分。因此，我们还需要为圆加上定向。

**定义 1.4.13** 定向（orientation）

如果 $\Gamma$ 是一个圆，则 $\Gamma$ 的一个**定向**定义为三元组 $(z_{1},z_{2},z_{3})$ 使得 $z_{j}\in\Gamma$ 且三点各不相同。

直观上看，三个点给出了 $\Gamma$ 的一个“方向”，那就是沿着 $z_{1}\to z_{2}\to z_{3}$ 的路径的方向。在平面上，一个圆有两种定向：逆时针与顺时针，而一条直线只需两点就能确定方向，因为第三个点总是取为 $\infty$.

设 $\Gamma=\mathbb{R}_{\infty}$，令 $z_{1},z_{2},z_{3}\in \mathbb{R}$，并取 $Tz=(z,z_{1},z_{2},z_{3})=\dfrac{az+b}{cz+d}$，由于 $T[\mathbb{R}_{\infty}]=\mathbb{R}_{\infty}$，因此我们可以将 $a,b,c,d$ 取为实数，于是

$$
\begin{align}
Tz &= \dfrac{az+b}{cz+d} \\
&= \dfrac{az+b}{|cz+d|^{2}} (c\overline{z}+d) \\
&= \dfrac{1}{|cz+d|^{2}}(ac|z|^{2}+bd+adz+bc\overline{z})
\end{align}
$$

从而

$$
\begin{align}
\mathrm{Im}\,(z,z_{1},z_{2},z_{3})=\dfrac{ad-bc}{|cz+d|^{2}} \mathrm{Im}\,z
\end{align}
$$

因此，集合 $\{ z \mid \mathrm{Im}\,(z,z_{1},z_{2},z_{3})>0 \}$ 是上半平面或下半平面，取决于 $ad-bc>0$ 或 $ad-bc<0$.

现在令 $\Gamma$ 是任意圆，$z_{1},z_{2},z_{3}\in\Gamma$，则对任意 Mobius 变换 $S$ 有

$$
\begin{align}
\{ z \mid \mathrm{Im}\,(z,z_{1},z_{2},z_{3})>0 \} &= \{ z \mid \mathrm{Im}\,(Sz,Sz_{1},Sz_{2},Sz_{3})>0 \} \\
&= S^{-1}[\{ z \mid \mathrm{Im}\,(z,Sz_{1},Sz_{2},Sz_{3})>0 \}]
\end{align}
$$

特别地，取 $S$ 使得 $S$ 将 $\Gamma$ 映射到 $\mathbb{R}_{\infty}$，则 $\{ z \mid \mathrm{Im}\,(z,z_{1},z_{2},z_{3})>0 \}$ 就是上半平面或下半平面在 $S^{-1}$ 下的像。

设 $(z_{1},z_{2},z_{3})$ 是 $\Gamma$ 的一个定向，则我们定义在这个定向下，$\Gamma$ 的**右侧**为集合 $\{ z \mid \mathrm{Im}\,(z,z_{1},z_{2},z_{3})>0 \}$，**左侧**为 $\{ z \mid \mathrm{Im}\,(z,z_{1},z_{2},z_{3})<0 \}$.

例如，考虑 $\mathbb{R}_{\infty}$ 的定向 $(1,0,\infty)$，则我们有 $(z,1,0,\infty)=z$，因此 $\mathbb{R}_{\infty}$ 的右侧是上半平面。这与我们的直觉相符：沿着 $1\to 0\to \infty$ 在实轴上行走，我们的右侧正是上半平面。

**定理 1.4.14** 定向原理（Orientation Principle）

设 $T$ 是一个将圆 $\Gamma_{1}$ 映射到圆 $\Gamma_{2}$ 的 Mobius 变换，取 $(z_{1},z_{2},z_{3})$ 为 $\Gamma_{1}$ 的定向，$(Tz_{1},Tz_{2},Tz_{3})$ 为 $\Gamma_{2}$ 的定向，则 $T$ 将 $\Gamma_{1}$ 的右侧映射到 $\Gamma_{2}$ 的右侧，将 $\Gamma_{1}$ 的左侧映射到 $\Gamma_{2}$ 的左侧。

**证明**

我们有

$$
\begin{align}
\{ z \mid \mathrm{Im}\,(z,z_{1},z_{2},z_{3})>0 \} = \{ z \mid \mathrm{Im}\,(Tz,Tz_{1},Tz_{2},Tz_{3})>0 \}
\end{align}
$$

这表明 $z$ 属于 $\Gamma_{1}$ 的右侧当且仅当 $Tz$ 属于 $\Gamma_{2}$ 的右侧，对于左侧也是同理，这就完成了证明。

最后我们来简要介绍一下 Mobius 变换在解析函数理论中的应用。在解析函数论中，一个至关重要的问题是，给定两个连通开集 $G,\Omega$，是否存在解析函数 $f\colon G\to \mathbb{C}$ 使得 $f[G]=\Omega$？Mobius 变换提供了这一问题的部分解法，我们以一个例子来说明这一点。

考虑以下问题：构造解析函数 $f\colon G\to \mathbb{C}$，其中 $G=\{ z \mid \mathrm{Re}\,z>0 \}$，使得 $f[G]=D=\{ z \mid |z|<1 \}$. 我们可以找到一个将虚轴映射到单位圆的 Mobius 变换，从而根据定向原理，其将 $G$ 映射到 $D$.

给予虚轴定向 $(-i,0,i)$，则 $G$ 就在虚轴的右侧，并且

$$
\begin{align}
(z,-i,0,i) &= \dfrac{2z}{z-i} \\
&= \dfrac{2z(\overline{z}+i)}{|z-i|^{2}} \\
&= \dfrac{2}{|z-i|^{2}}(|z|^{2}+iz)
\end{align}
$$

因此，$\{ z \mid \mathrm{Im}\,(z,-i,0,i)>0 \}=\{ z \mid \mathrm{Im}(iz)>0 \}=\{ z \mid \mathrm{Re}\,z>0 \}$. 接下来，给予单位圆定向 $(-i,-1,i)$，则 $D$ 在单位圆的右侧，并且

$$
\begin{gather}
(z,-i,-1,i)=\dfrac{2i}{i-1}\cdot \dfrac{z+1}{z-i}
\end{gather}
$$

令 $Sz=(z,-i,0,i),Rz=(z,-i,-1,i)$，则 $T=R^{-1}\circ S$ 将 $G$ 映射到 $D$，且有

$$
\begin{gather}
Tz=\dfrac{z-1}{z+1}
\end{gather}
$$

如果 $G_{1},G_{2}$ 是连通开集，要找到解析函数 $f$ 使得 $f[G_{1}]=G_{2}$，我们可以先将 $G_{1}$ 和 $G_{2}$ 映射到单位开圆盘 $D$ 上。如果这可以做到，那么 $f$ 就等于一个函数与另一个函数的逆的复合。