# Section 1: 编号树与图

本节的主要内容是树结构，以及与之相关的重要构造。这里我们研究的是**编号树**，表明其节点上具有整数编号。与无编号类中的树相同，编号树也可以分成两类：平面树，即那些可以被嵌入平面上的树结构；无序树，即那些子节点的顺序无关的树结构。我们可以通过要求子节点的个数属于 $\Omega$（$0\in\Omega$）来进一步限制树的结构。

## 树

我们首先来看平面树 $\mathcal{A}$，它的构造是

$$
\begin{gather}
\mathcal{A}=\mathcal{Z} \otimes \mathrm{Seq}_{\Omega}(\mathcal{A})
\end{gather}
$$

根据可容许性定理，我们有 EGF

$$
\begin{gather}
A(z)=z\phi(\mathcal{A}(z)), \quad \phi(u)=\sum_{\omega \in\Omega} u^{\omega}
\end{gather}
$$

根据 Lagrange 反演定理，对于无限制的平面树 $\Omega=\mathbb{N}$，其计数序列为

$$
\begin{gather}
A_{n}=(n-1)![u^{n-1}] (1-u)^{-n}=(n-1)! \binom{ 2n-2 }{ n-1 } = \dfrac{(2n-2)!}{(n-1)!}
\end{gather}
$$

可见，具有 $n$ 个节点的一般平面编号树的数量恰好等于 $n!$ 乘以具有 $n$ 个节点的无编号平面树的数量，这可以容易地由下图得到：

![](4-1.png)

换句话说，一个平面编号树可以被定义为它的无编号“形状”以及一个按某种顺序（例如先序）进行遍历的序列。

接下来我们来看无序树，没有限制的树类 $\mathcal{T}$ 的生成函数由一个隐式函数方程给出：

$$
\begin{gather}
\mathcal{T}=\mathcal{Z} \otimes \mathrm{Set}(\mathcal{T}) \implies T(z)=ze^{ T(z) }
\end{gather}
$$

再一次利用 Lagrange 反演定理，我们得到

$$
\begin{gather}
T_{n}=(n-1)! [u^{n-1}] e^{ nu }= n^{n-1}
\end{gather}
$$

这一计数序列 $T_{n}=n^{n-1}$ 首先由数学家 Cayley 给出，因此 $\mathcal{T}$ 中的树经常被称为“Cayley 树”。函数 $T(z)$ 也常被称为“Cayley 树函数”，它与由方程 $We^{ W }=z$ 定义的 Lambert W 函数 $W(z)$ 密切相关。

一个类似的过程可以被用于具有限制的非平面树上，我们有构造

$$
\begin{gather}
\mathcal{T}^{\Omega}=\mathcal{Z}\otimes \mathrm{Set}_{\Omega}(\mathcal{T}^{\Omega}) \implies T^{\Omega}(z)=z\overline{\phi}(T^{\Omega}(z))
\end{gather}
$$

其中 $\overline{\phi}$ 是指数特征函数

$$
\begin{gather}
\overline{\phi}(u)=\sum_{\omega \in\Omega} \dfrac{u^{\omega}}{\omega!}
\end{gather}
$$

Lagrange 反演是处理这类问题的通用方法，从而我们可得

**定理 4.1.1**

节点的出度属于 $\Omega \subset \mathbb{N}(0\in\Omega)$ 的有根无序树的数量由下式给出：

$$
\begin{gather}
T_{n}^{\Omega}=(n-1)![u^{n-1}] (\overline{\phi}(u))^{n}, \quad \overline{\phi}(u)=\sum_{\omega \in\Omega} \dfrac{u^{\omega}}{\omega!}
\end{gather}
$$

特别地，当 $\Omega=\mathbb{N}$ 时，有 $T_{n}=n^{n-1}$，且其 EGF 为 Cayley 树函数，其满足函数方程 $T(z)=ze^{ T(z) }$.

根据 Lagrange 反演的 Burmann 形式，我们可得 Cayley 树的无序 $k$-森林的数量为

$$
\begin{gather}
\mathcal{F}^{(k)}=\mathrm{Set}_{k}(\mathcal{T}) \implies F_{n}^{(k)}=\dfrac{(n-1)!}{(k-1)!}[u^{n-k}]e^{ nu }=\binom{ n-1 }{ k-1 } n^{n-k}
\end{gather}
$$

## 有限集上的函数

设 $f$ 是有限集 $X$ 上的函数（通常设 $X=[n]$），我们可以将其与一个顶点集为 $[n]$ 的有向图联系起来：如果 $f(i)=j$，那么就有一条边从 $i$ 指向 $j$，如图所示：

![](4-2.png)

这样的图称为**函数图**，它有性质：每个顶点的出度必定等于 1.

给定 $f\colon[n]\to[n]$ 以及任意 $x_{0}$，由于集合是有限的，故序列

$$
\begin{gather}
x_{0},f(x_{0}),ff(x_{0}),fff(x_{0}),\dots
\end{gather}
$$

必然会进入一个循环。这就给出了函数图的一种构造方式：一个函数图是连通图的集合；一个连通的函数图是若干个有根无序树的循环。因此，取 $\mathcal{T}$ 为 Cayley 树类，$\mathcal{K}$ 为连通函数图的类，我们有规范

$$
\begin{gather}
\begin{cases}
\mathcal{F}=\mathrm{Set}(\mathcal{K}) \\
\mathcal{K}=\mathrm{Cyc}(\mathcal{T}) \\
\mathcal{T}=\mathcal{Z}\otimes \mathrm{Set}(\mathcal{T})
\end{cases}\implies \begin{cases}
F(z)=e^{ K(z) } \\
K(z)=\ln \dfrac{1}{1-T(z)} \\
T(z)=ze^{ T(z) }
\end{cases}
\end{gather}
$$

从上我们可得

$$
\begin{gather}
F(z)=\dfrac{1}{1-T(z)} \implies F_{n}=n^{n}
\end{gather}
$$

就如同我们所期望的那样（考虑该问题的源头）。更进一步地，我们可得连通的函数图 $\mathcal{K}$ 具有数量（通过展开 $\ln(1-T)^{-1}$ 并使用 Lagrange 反演）

$$
\begin{gather}
K_{n}=n^{n-1} Q(n), \quad Q(n)=1+\dfrac{n-1}{n}+\dfrac{(n-1)(n-2)}{n^{2}}+\cdots
\end{gather}
$$

其中 $Q(n)$ 被称为“Ramanujan Q 函数”，因为它在 Ramanujan 给 Hardy 的信件中首次出现。在后续的章节中，我们还会给出它的一个渐近公式。

如同符号计数中的大多数场景一样，基本的构造为其它大量相关的计数问题提供了统一的解决方案。首先，通过修改规范，我们可得没有不动点（$f(x)\neq x$）以及没有 $1,2$-循环（$ff(x)\neq x$）的函数图分别具有 EGF

$$
\begin{gather}
\dfrac{e^{ -T(z) }}{1-T(z)}, \quad \dfrac{e^{ -T(z)-T(z)^{2}/2 }}{1-T(z)}
\end{gather}
$$

其中第一项的系数 $(n-1)^{n}$ 与直接计数的结果一致。

接下来，我们可得**幂等函数**（$ff(x)=f(x)$）的函数图具有构造

$$
\begin{gather}
\mathcal{I}\cong \mathrm{Set}(\mathcal{Z}\otimes \mathrm{Set}(\mathcal{Z})) \implies I(z)=\exp(ze^{ z })
\end{gather}
$$

利用 $e^{ z }$ 的 Taylor 级数，我们有

$$
\begin{gather}
I_{n}=\sum_{k=0}^{n} \binom{ n }{ k } k^{n-k}
\end{gather}
$$

这是因为幂等函数的图只有长度为 1 的循环，在这些循环的节点上接有其前驱的集合。

## 编号图

随机图构成了随机离散结构理论的一个重要章节。我们在此探讨关于“复杂度”较低的图的计数结果，即那些几乎为树的图。此外，我们将图限定为**简单图**，即那些没有重边也没有自环的图。

在所有的连通图中，最简单的显然就是那些没有环的图。这些图是树，但与 Cayley 树不同，其没有一个特殊的节点被指定为它的根。设 $\mathcal{U}$ 表示所有无根树构成的类，由于一个有根树由一个无根树和一个被指定的根节点构成，因此我们有

$$
\begin{gather}
T_{n}=nU_{n} \implies U_{n}=n^{n-2}
\end{gather}
$$

对于其 EGF，我们有

$$
\begin{gather}
U(z)=\int_{0}^{z} T(w) \dfrac{\mathrm{d} w}{w}=T(z)-\dfrac{1}{2}T(z)^{2}
\end{gather}
$$

接下来，由于 $U(z)$ 是连通无环图的 EGF，因此

$$
\begin{gather}
A(z)=e^{ U(z) }=e^{ T(z)-T(z)^{2} / 2 }
\end{gather}
$$

就是所有无环图的 EGF，因为所有图都可以写成其连通部分的集合，即无根树的无序森林：

$$
\begin{gather}
\mathcal{A}=\mathrm{Set}(\mathcal{U}) \implies A(z)=e^{ U(z) }
\end{gather}
$$

下面我们讨论更复杂一些的图，我们有一个指标来精确地为其复杂度分层：

**定义 4.1.2** 过剩量（excess）

一个图的**过剩量**定义为它的边数与顶点数之差。

对于一个连通图，它的过剩量必然大于等于 $-1$，并且在等于 $-1$ 时就是无根树。令 $\mathcal{W}_{k}$ 表示所有过剩量为 $k$ 的连通图构成的类，由上面的讨论知 $\mathcal{W}_{-1}=\mathcal{U}$.

下面我们来看 $\mathcal{W}_{0}$，这些是边数等于顶点数的连通图，也是仅有一个环的连通图，因此 $\mathcal{W}_{0}$ 中的元素通常被称为“单环分量”。这些图看起来非常像函数图中的一个连通分量，只不过它的边是无向的。

精确地说，一个 $\mathcal{W}_{0}$ 中的图包含一个无向的（将在反射置换下不变的循环等同）、长度大于等于 $3$ 的循环，其每个节点上连接了一棵 Cayley 树。我们用下面的符号来表示这种新的无向循环：

$$
\begin{gather}
\mathcal{W}_{0}=\mathrm{UCyc}_{\geq 3}(\mathcal{T})
\end{gather}
$$

显然我们有以下的同构等式：

$$
\begin{gather}
\mathcal{W}_{0}+\mathcal{W}_{0} \cong \mathrm{Cyc}_{\geq 3}(\mathcal{T}) \implies W_{0}(z)=\dfrac{1}{2}\ln \dfrac{1}{1-T(z)} -\dfrac{1}{2}T(z)-\dfrac{1}{4}T(z)^{2}
\end{gather}
$$

因为一个循环只有两种定向：顺时针和逆时针。于是仅含有树和单环连通分量的图具有 EGF

$$
\begin{gather}
e^{ W_{-1}(z)+W_{0}(z) }=\dfrac{e^{ T / 2-3T^{2} / 4 }}{\sqrt{ 1-T }}
\end{gather}
$$

对于 $k\geq 1$ 的类 $\mathcal{W}_{k}$，其精确的计数公式过于复杂，因此我们只能依赖渐近分析。这其中，E. M. Wright 做出了重要贡献，他的结论可以总结为下面的定理：

**定理 4.1.3**

设 $k\geq 1$，具有过剩量 $k$ 的连通图构成的类 $\mathcal{W}_{k}$ 的 EGF 具有形式

$$
\begin{gather}
W_{k}(z)=\dfrac{P_{k}(T)}{(1-T)^{3k}}
\end{gather}
$$

其中 $T$ 是 Cayley 树函数，$P_{k}$ 是一个次数为 $3k+2$ 的多项式。

上述定理的证明依赖于之后将要讨论的指示构造与多元生成函数，这里我们仅作简要的介绍。

**证明**（Wright）

定义二元生成函数 $w_{k}(z,y)=y^{k}W_{k}(zy)$，其中 $z$ 指示了顶点数而 $y$ 指示了边数。在一个过剩量为 $k+1$ 的连通图中选取一条边，然后把它去除，剩下的部分或者是一个过剩量为 $k$ 的连通图，其中有两个点被指示（且没有边连接它们）；或者是两个分别具有过剩量 $h$ 和 $k-h$ 的连通分量，其分别有一个点被指示，如图所示：

![](4-3.png)

这可以转化为 EGF 的微分方程（一些项被乘以 $\dfrac{1}{2}$ 以消除指示的有序性）

$$
\begin{gather}
2 \partial_{y} w_{k+1}=(z^{2}\partial_{z}^{2} w_{k}-2y\partial_{y} w_{k}) + \sum_{h=-1}^{k+1} (z\partial_{z}w_{h})(z\partial_{z} w_{k-h})
\end{gather}
$$

由此，根据归纳法，我们可以证明每个 $W_{k}=w_{k}(z,1)$ 都是 $T$ 的一个有理函数，其中 $T$ 是 Cayley 树函数。

前几项 $W_{k}$ 的精确形式如下：

$$
\begin{gather}
W_{1}=\dfrac{1}{24} \dfrac{T^{4}(6-T)}{(1-T)^{3}},\quad W_{2}=\dfrac{1}{48} \dfrac{T^{4}(2+28T-23T+9T^{3}-T^{4})}{(1-T)^{6}}
\end{gather}
$$

# Section 2: 其它构造

和无编号类的情形一样，指示构造和替换构造在编号类中同样可以被定义，并且隐式构造扩大了符号计数方法的适用范围。最后是编号类与无编号类不同的一点，整数编号的有序性使得在编号类中考虑编号的序限制是可行的。

## 指示与替换

**定义 4.2.1** 指示（pointing）

一个编号类 $\mathcal{B}$ 的**指示**构造定义为

$$
\begin{gather}
\Theta \mathcal{B}=\sum_{n\geq 0} \mathcal{B}_{n}\times [n]
\end{gather}
$$

编号类的指示构造与它的无编号对应是完全一致的，即选择一个原子使其与其它原子区分开来。不过，在编号类中这种选择更加简单：只需选择一个属于 $[n]$ 的编号以指向该编号所对应的原子即可。

**定义 4.2.2** 替换（substitution）

编号类 $\mathcal{B}$ 与 $\mathcal{C}$ 的**替换**构造定义为

$$
\begin{gather}
\mathcal{B}\circ \mathcal{C}=\sum_{k\geq 0} \mathcal{B}_{k}\times \mathrm{Set}_{k}(\mathcal{C})
\end{gather}
$$

一种对替换操作的解释如下：首先选择一个 $\beta \in \mathcal{B}$，设 $k=|\beta|$ 为其大小，这是我们要做替换的“基底”。然后取出 $\mathcal{C}$ 的一个 $k$-集合，该集合中的元素自然地按照其“头节点”的编号升序排列（我们定义头节点为具有最小编号的节点），然后用排在第 $r$ 位的元素替换 $\beta$ 中编号为 $r$ 的节点。

根据可容许性定理，我们得到：

**定理 4.2.3**

指示构造与替换构造是可容许的，并且其生成函数为：

$$
\begin{gather}
\mathcal{A}=\Theta \mathcal{B} \implies A(z)=z\partial_{z} B(z) \\
\mathcal{A}=\mathcal{B}\circ \mathcal{C} \implies A(z)=B(C(z))
\end{gather}
$$

其中 $\mathcal{C}_{0}=\varnothing$.

**证明**

对于指示构造，我们有

$$
\begin{gather}
A_{n}=nB_{n} \implies A(z)=z\partial_{z} B(z)
\end{gather}
$$

对于替换构造，我们有

$$
\begin{gather}
A(z)=\sum_{k=0}^{\infty} B_{k} \dfrac{C(z)^{k}}{k!}=B(C(z))
\end{gather}
$$

$C_{0}=0$ 保证了级数在形式拓扑中的收敛性。

编号类的基本构造（序列、集合、循环）均可以写成替换的形式：

$$
\begin{gather}
\mathrm{Seq}(\mathcal{A})\cong \mathcal{P}\circ \mathcal{A},\quad \mathrm{Set}(\mathcal{A})\cong \mathcal{U}\circ \mathcal{A},\quad \mathrm{Cyc}(\mathcal{A})\cong \mathcal{C}\circ \mathcal{A}
\end{gather}
$$

其中 $\mathcal{P}$ 是置换类，$\mathcal{U}$ 是空图类，$\mathcal{C}$ 是循环类。从这一角度看，置换、空图和循环就成为了基于替换的组合分析中的原型类。

## 隐式构造

设 $\mathcal{X}$ 是一个编号类，由下面的规范隐含地确定：

$$
\begin{gather}
\mathcal{A}=\mathcal{B}+\mathcal{X}, \quad \mathcal{A}=\mathcal{B}\otimes \mathcal{X}
\end{gather}
$$

求解相应的函数方程即得

$$
\begin{gather}
X(z)=A(z)-B(z),\quad X(z)=\dfrac{A(z)}{B(z)}
\end{gather}
$$

对于序列、集合与循环构造，利用基本的代数运算同样可得：

**定理 4.2.4**

由隐式构造确定的编号类 $\mathcal{X}$

$$
\begin{gather}
\mathcal{A}=\mathrm{Seq}(\mathcal{X}),\quad \mathcal{A}=\mathrm{Set}(\mathcal{X}),\quad \mathcal{A}=\mathrm{Cyc}(\mathcal{X})
\end{gather}
$$

的 EGF 分别为

$$
\begin{gather}
X(z)=1-\dfrac{1}{A(z)},\quad X(z)=\ln A(z),\quad X(z)=1-e^{ -A(z) }
\end{gather}
$$

下面我们给出图论中的两个例子。

第一个例子涉及编号图 $\mathcal{G}$，以及连通编号图 $\mathcal{K}$，它们由下面的等式联系：

$$
\begin{gather}
\mathcal{G}=\mathrm{Set}(\mathcal{K}) \implies G(z)=e^{ K(z) }
\end{gather}
$$

这只是“图是其连通分量的集合”这一事实的反映。公式 $G(z)=e^{ K(z) }$ 在图论中被称为“指数公式”。

考虑由所有无向编号图构成的类 $\mathcal{G}$，其中图的大小定义为它的顶点数，那么一个大小为 $n$ 的图就由它的边集决定：有 $\binom{ n }{ 2 }$ 条可能的边可以被设为连接或不连接，因此 $G_{n}=2^{\binom{ n }{ 2 }}$. 令 $\mathcal{K}$ 由所有无向连通图构成，则指数公式隐含地确定了 $\mathcal{K}$ 的 EGF：

$$
\begin{gather}
K(z)=\ln G(z)=\ln \left( 1+\sum_{n\geq 1} 2^{\binom{ n }{ 2 } } \dfrac{z^{n}}{n!} \right)
\end{gather}
$$

将对数利用 $\ln(1+u)=u-u^{2} / 2+u^{3} / 3-\cdots$ 展开，则我们可以提取出 $K_{n}$ 的一个显式公式：

$$
\begin{gather}
K_{n}=2^{\binom{ n }{ 2 } }- \dfrac{1}{2}\sum \binom{ n }{ n_{1} } 2^{\binom{ n_{1} }{ 2 } +\binom{ n_{2} }{ 2 } }+ \dfrac{1}{3} \sum \binom{ n }{ n_{1},n_{2},n_{3} } 2^{\binom{ n_{1} }{ 2 } +\binom{ n_{2} }{ 2 } +\binom{ n_{3} }{ 2 } }-\cdots
\end{gather}
$$

其中求和式中的指标满足 $n_{1}+\dots+n_{k}=n,0<n_{j}<n$.

另一个例子是**二分图**。一个平面二分图可以定义为二元组 $(G,\omega)$，其中 $\omega=(\omega_{L},\omega_{R})$ 是图 $G$ 的顶点的一个二分，并且 $G$ 只有从 $\omega_{L}$ 到 $\omega_{R}$ 的边。通过直接计数，我们可得平面二分图的 EGF 为

$$
\begin{gather}
\Gamma(z)=\sum_{n=0}^{\infty} \gamma_{n} \dfrac{z^{n}}{n!}, \quad \gamma_{n}=\sum_{k=0}^{n} \binom{ n }{ k } 2^{k(n-k)}
\end{gather}
$$

于是根据指数公式，连通的平面二分图的 EGF 为 $\ln\Gamma(z)$.

一个二分图是一个编号图，其顶点集可以被分成两个不相交的集合，使得每条边连接的节点分别属于不同的集合。对于一个连通二分图来说，它是平面连通二分图的无定向版本，因此连通二分图的 EGF 为 $\dfrac{1}{2}\ln\Gamma(z)$，其中 $\dfrac{1}{2}$ 的因子去除了平面图中 $L-R$ 的定向，从而所有二分图的 EGF 为

$$
\begin{gather}
\exp\left( \dfrac{1}{2}\ln\Gamma(z) \right)=\sqrt{ \Gamma(z) }
\end{gather}
$$

## 序限制

一种非常适合处理具有序限制的组合问题的构造是以下的修正编号积：

$$
\begin{gather}
\mathcal{A}=(\mathcal{B}^{\min}\otimes \mathcal{C})
\end{gather}
$$

其中 $\mathcal{B}^{\min}$ 表示 $\mathcal{B}$ 中的元素含有最小编号。同样我们也可以定义

$$
\begin{gather}
\mathcal{A}=(\mathcal{B}^{\max}\otimes \mathcal{C})
\end{gather}
$$

以表示 $\mathcal{B}$ 中的元素含有最大编号。为了使该定义一致，我们需要保证 $\mathcal{B}_{0}=\varnothing$.

**定理 4.2.5** 有序编号积

上述的有序编号积是可容许的，其 EGF 为

$$
\begin{gather}
\mathcal{A}=(\mathcal{B}^{\mathfrak{m}}\otimes \mathcal{C}) \implies A(z)=\int_{0}^{z} (\partial_{t} B(t)) \cdot C(t) \mathrm{d} t
\end{gather}
$$

其中 $\mathfrak{m}$ 表示 $\min$ 或 $\max$.

**证明**

根据有序编号积的定义，我们有

$$
\begin{gather}
A_{n}=\sum_{k=1}^{n} \binom{ n-1 }{ k-1 } B_{k}C_{n-k}=\dfrac{1}{n} \sum_{k=0}^{n} \binom{ n }{ k } (kB_{k})C_{n-k}
\end{gather}
$$

这是因为只有 $n-1$ 个编号需要被分配：$\mathcal{B}$ 分量得到 $k-1$ 个，$\mathcal{C}$ 分量得到 $n-k$ 个。取两边的 EGF 即得

$$
\begin{gather}
z\partial_{z}A(z)=(z\partial_{z}B(z))C(z) \implies A(z)=\int_{0}^{z} (\partial_{t}B(t))C(t) \mathrm{d} t
\end{gather}
$$

一个有用的特例是最小根节点操作：

$$
\begin{gather}
\mathcal{A}=(\mathcal{Z}^{\min}\otimes \mathcal{C})
\end{gather}
$$

它可以做如下解释：首先取 $\gamma \in \mathcal{C}$，再准备一个原子（编号为 0）将其添加到 $\gamma$ 上，最后将 $\gamma$ 中的所有编号向右平移一位。显然 $A_{n+1}=C_{n}$，这给出

$$
\begin{gather}
A(z)=\int_{0}^{z} C(t)\mathrm{d} t
\end{gather}
$$

这与定理 4.2.5 给出的结果一致。

给定一个置换 $\sigma=\sigma_{1}\dots\sigma_{n}$，称 $\sigma_{k}$ 是 $\sigma$ 的一个**记录**，如果对任意 $j<k$ 有 $\sigma_{j}<\sigma_{k}$. 换言之，一个记录就是从左（第一个位置）到右（当前位置）的最大值。下面我们来计算具有 $k$ 个记录的 $n$-置换的数量。

首先我们来看一类特殊的置换，即那些在第一个位置取到最大值的置换，这种置换的构造由下式给出：

$$
\begin{gather}
\mathcal{Q}=(\mathcal{Z}^{\max}\otimes \mathcal{P})
\end{gather}
$$

其中 $\mathcal{P}$ 是置换类。由此我们得到 $\mathcal{Q}$ 的 EGF

$$
\begin{gather}
Q(z)=\int_{0}^{z} \dfrac{1}{1-t}\mathrm{d} t=\ln \dfrac{1}{1-z} \implies Q_{n}=(n-1)!
\end{gather}
$$

这些是只有一个记录的置换的数量，从而有 $k$ 个记录的置换可以表示为

$$
\begin{gather}
\mathcal{P}^{(k)}=\mathrm{Set}_{k}(\mathcal{Q}) \implies P^{(k)}(z)=\dfrac{1}{k!}\left( \ln \dfrac{1}{1-z} \right)^{k}
\end{gather}
$$

于是 $P_{n}^{(k)}$ 由 Stirling 循环数 $\left[ \begin{matrix}n \\ k\end{matrix} \right]$ 给出。这一循环与记录的对应是置换计数中的一个基本转换：在置换的循环分解中将每个循环的最大值写在循环的第一个位置（记为循环的“头元素”），然后按照头元素的值为循环升序排列，最后去掉括号并把剩下的部分看成是另一个置换的线性表示，这样得到的置换必然有 $k$ 个记录，其中 $k$ 是原置换中循环的数量。下面是一个例子：

$$
\begin{gather}
(1\mathbf{7}26)(3\mathbf{4})(5\mathbf{9}8) = (\mathbf{4}3)(\mathbf{7}261)(\mathbf{9}85) \longrightarrow 437261985
\end{gather}
$$

我们可以容易地看出上面的过程是可逆的：在记录与下一个记录之间加上括号即可。由此，我们在置换的循环与置换的极值之间建立了联系。

利用加法、乘法以及有序编号积，我们可以建立一种与序列、集合、循环在表达能力上完全相同的符号计数语言。具体来说，考虑下面的等式

$$
\begin{gather}
\mathcal{F}=\mathrm{Seq}(\mathcal{G}) \implies f(z)=\dfrac{1}{1-g(z)}, \quad f=1+gf \\
\mathcal{F}=\mathrm{Set}(\mathcal{G}) \implies f(z)=e^{ g(z) }, \quad f=1+\int g' f \\
\mathcal{F}=\mathrm{Cyc}(\mathcal{G}) \implies f(z)=\ln \dfrac{1}{1-g(z)}, \quad f=\int g' \dfrac{1}{1-g}
\end{gather}
$$

最后一列等式可以通过初等的微积分进行验证。不仅如此，它还有一个直接的组合解释，对于序列，我们有递归方程

$$
\begin{gather}
\mathcal{F}=\mathrm{Seq}(\mathcal{G}) \implies \mathcal{F}\cong \mathcal{E}+(\mathcal{G}\otimes \mathcal{F})
\end{gather}
$$

对于集合，我们有

$$
\begin{gather}
\mathcal{F}=\mathrm{Set}(\mathcal{G}) \implies \mathcal{F}\cong \mathcal{E}+(\mathcal{G}^{\max}\otimes \mathcal{F})
\end{gather}
$$

它可以理解为在一个集合中，我们总是可以取出具有最大编号的一个元素，而剩下的元素仍然构成一个集合。换句话说，当我们递归地进行这种构造时，集合中的元素可以根据最大标签的值（即“头节点”）进行规范的排序。

而对于循环，具有最大编号的那个节点可以被选择为该循环的头元素，剩下的元素就构成了 $\mathcal{G}$ 的一个序列：

$$
\begin{gather}
\mathcal{F}=\mathrm{Cyc}(\mathcal{G}) \implies \mathcal{F}\cong (\mathcal{G}^{\max}\otimes  \mathrm{Seq}(\mathcal{G}))
\end{gather}
$$

因此，仅使用无交并、编号积与有序编号积，我们就可以建立一种等价的符号计数方法。Greene 利用这种语法建立了一种完整的框架，在这种框架中，更多的最大/最小元素限制可以被纳入考虑范围。例如，设 $\min$，$\min_{2}$，$\max$ 分别表示最小、第二最小和最大的编号，则有

$$
\begin{gather}
\mathcal{A}=(\mathcal{B}^{\min}\otimes \mathcal{C}^{\max}) \implies \partial_{z}^{2} A(z)=(\partial_{z}B(z))(\partial_{z}C(z)) \\
\mathcal{A}=(\mathcal{B}^{\min,\max}\otimes \mathcal{C}) \implies \partial_{z}^{2}A(z)=(\partial_{z}^{2}B(z)) C(z) \\
\mathcal{A}=(\mathcal{B}^{\min}\otimes \mathcal{C}^{\min_{2}}\otimes \mathcal{D}^{\max}) \implies \partial_{z}^{3}A(z)=(\partial_{z}B(z))(\partial_{z}C(z))(\partial_{z}D(z))
\end{gather}
$$

等等。这些等式还可以进一步转化为重积分表达式。

最后，我们通过三个例子来显示有序编号积在计数问题中的作用。

对于每个置换，我们可以将其对应到一种特殊的二叉树上，称为**递增二叉树**。这是一种平面编号二叉树，满足从根节点向下的每一条节点链上的编号都是递增的。其构造方法如下：给定一个置换 $\sigma=\sigma_{1}\dots\sigma_{n}$，我们可以将其分解为

$$
\begin{gather}
\sigma=(\sigma_{L},\min(\sigma),\sigma_{R})
\end{gather}
$$

其中 $\min(\sigma)$ 是 $\sigma$ 中具有最小编号的元素，下面我们可以递归地定义二叉树 $\beta(\sigma)$ 为

$$
\begin{gather}
\beta(\sigma)=(\beta(\sigma_{L}),\min(\sigma),\beta(\sigma_{R})), \quad \beta(\varepsilon)=\varepsilon
\end{gather}
$$

其中 $\varepsilon$ 是空置换。反之，给定一个递增二叉树，它的中序遍历序列就给出了其对应的置换，如图所示：

![](4-4.png)

因此，递增二叉树构成的类 $\mathcal{I}$ 有如下构造：

$$
\begin{gather}
\mathcal{I}=\mathcal{E}+(\mathcal{Z}^{\min}\otimes \mathcal{I}\otimes \mathcal{I}) \implies I(z)=1+\int_{0}^{z} I(t)^{2} \mathrm{d} t
\end{gather}
$$

求导得到 $I'(z)=I(z)^{2}$，在初始条件 $I(0)=1$ 下解得 $I(z)=(1-z)^{-1}$，即 $I_{n}=n!$，这与“置换与递增二叉树一一对应”的事实一致。

递增二叉树在解决具有局部序关系的置换计数问题中非常有用，我们以**交错排列**的问题来说明这一点。称一个置换 $\sigma=\sigma_{1}\dots\sigma_{n}$ 是**交错的**，如果它满足

$$
\begin{gather}
\sigma_{1}>\sigma_{2}<\sigma_{3}>\sigma_{4}<\cdots
\end{gather}
$$

我们首先来看奇数大小的交错排列 $\mathcal{J}$，它对应的递增二叉树没有单向分支节点，如图所示：

![](4-5.png)

因此 $\mathcal{J}$ 具有构造

$$
\begin{gather}
\mathcal{J}=\mathcal{Z}+(\mathcal{Z}^{\min}\otimes \mathcal{J}\otimes \mathcal{J}) \implies J(z)=z+\int_{0}^{z}J(t)^{2}\mathrm{d} t
\end{gather}
$$

求导得 $J'(z)=1+J(z)^{2}$，利用分离变量法在初始条件 $J(0)=0$ 下解得 $J(z)=\tan z$，其系数 $J_{2n+1}$ 被称为“正切数”或奇数下标的 Euler 数 $E_{2n+1}$.

对于偶数大小的交错排列 $\mathcal{K}$，它在去除一个根节点后留下的是一个奇数和一个偶数大小的交错排列，因此它有构造

$$
\begin{gather}
\mathcal{K}=\mathcal{E}+(\mathcal{Z}^{\min}\otimes \mathcal{J}\otimes \mathcal{K}) \implies K(z)=1+\int_{0}^{z} K(t)\tan t \mathrm{d} t
\end{gather}
$$

即 $K'(z)=\tan(z)K(z)$，解得 $K(z)=\sec z$，其系数就称为“正割数”或偶数下标的 Euler 数 $E_{2n}$. 综上，Euler 数的 EGF 就是

$$
\begin{gather}
E(z)=\tan z+\sec z=\sum_{n=0}^{\infty} E_{n} \dfrac{z^{n}}{n!}
\end{gather}
$$

该数列在置换的计数问题中非常常见。

一个**递增 Cayley 树**是一个 Cayley 树（非平面有根编号树），其从根节点向下的节点链上的编号是递增的。显然，递增 Cayley 树的最小编号必然在根节点处，并且其子节点是无序的，令 $\mathcal{L}$ 为递增 Cayley 树构成的类，则有递归等式

$$
\begin{gather}
\mathcal{L}=(\mathcal{Z}^{\min}\otimes \mathrm{Set}(\mathcal{L})) \implies L(z)=\int_{0}^{z} e^{ L(t) } \mathrm{d} t
\end{gather}
$$

即 $L'(z)=e^{ L(z) }$，在初始条件 $L(0)=0$ 下解得 $L(z)=\ln \dfrac{1}{1-z}$，从而大小为 $n$ 的递增 Cayley 树的数量为 $(n-1)!$，这也是大小为 $n-1$ 的置换的数量。

这一简单的结果值得为之寻找一个组合解释。事实上，一个递增 Cayley 树完全由节点的双亲-孩子关系决定，因此我们可以将一棵树 $\tau$ 与一个函数 $\phi=\phi_{\tau}$ 联系起来，其中 $\phi(i)$ 定义为 $i$ 的双亲节点 $j$. 由于根节点没有双亲，故 $\phi(1)$ 是无定义的，形式上我们令 $\phi(1)=\perp$；又由于 $\tau$ 是递增的，故 $\phi(i)<i$ 对任意 $i\geq 2$ 成立，满足最后两条性质的映射称为一个**回归映射**，它与递增 Cayley 树的双射关系可以从图中看出：

![](4-6.png)

显然，$[n]$ 上的回归映射 $\phi$ 对于 $\phi(2)$ 有 1 种选择，对于 $\phi(3)$ 有两种选择，以此类推，从而公式

$$
\begin{gather}
L_{n}=1\cdot 2 \cdots (n-1)=(n-1)!
\end{gather}
$$

得到了一个自然的解释。

此外，回归映射与置换之间也有直接的联系，实现这一连接的构造是**逆序表**：给定置换 $\sigma=\sigma_{1}\dots\sigma_{n}$，它的逆序表是函数 $\psi\colon[n]\to[0..n-1]$ 使得

$$
\begin{gather}
\psi(k)=\lvert \{ j \mid j<k,\sigma_{j}>\sigma_{k} \} \rvert 
\end{gather}
$$

这其中函数 $\psi$ 是回归映射的一个平凡变体。

更进一步，递增 Cayley 树与递增二叉树同样有直接的联系。由于 Cayley 树的非平面的，故子节点可以按照其编号进行升序排列，于是旋转对应（见第二章）就给出了一个递增二叉树。总结一下上述讨论，我们有四种相互同构的组合构造

$$
\begin{gather}
\text{递增 Cayley 树} \cong \text{回归映射} \cong \text{置换} \cong \text{递增二叉树}
\end{gather}
$$

它们为其它更多的置换计数问题开辟了道路。