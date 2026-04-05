# Section 1: 递归参数

在本节中，我们将考虑由递归方程所定义的组合类以及其上的递归参数。典型的例子就是树结构。

在一棵树中，如果我们要标记叶子节点，或者更广义地，标记度为 $r$ 的节点，我们可以通过分离并放置标签的方式进行构造。例如，对于组合构造 $\mathscr{C}(\mathcal{B})$，假设我们需要标记具有 $r$ 个组分的元素，我们可以按如下方法构造：

$$
\begin{gather}
\mathscr{C}(\mathcal{B})=u \mathscr{C}_{r}(\mathcal{B})+\mathscr{C}_{\neq r}(\mathcal{B})=(u-1)\mathscr{C}_{r}(\mathcal{B})+\mathscr{C}(\mathcal{B})
\end{gather}
$$

下面我们给出两个例子，分别涉及无编号树（Catalan 树）和有编号树（Cayley 树）。

设 $\mathcal{G}$ 为 Catalan 树构成的类，它由 Catalan 数所计数。现在我们为叶子节点打上标签，则其构造为

$$
\begin{gather}
\mathcal{G}=\mathcal{Z}u+\mathcal{Z}\times \mathrm{Seq}_{\geq 1}(\mathcal{G})\implies G(z,u)=zu+\dfrac{zG(z,u)}{1-G(z,u)}
\end{gather}
$$

解得

$$
\begin{gather}
G(z,u)=\dfrac{1}{2}\left(1+(u-1)z+\sqrt{ 1-2(u+1)z+(u-1)^{2}z^{2} }\right)
\end{gather}
$$

另一方面，通过 Lagrange 反演，我们可得 $G(z,u)$ 系数的一个公式：

$$
\begin{align}
G_{n,k} &= [u^{k}][z^{n}] G(z,u)=[u^{k}] \dfrac{1}{n}[y^{n-1}]\left( u+\dfrac{y}{1-y} \right)^{n} \\
&= \dfrac{1}{n} \binom{ n }{ k } [y^{n-1}] \dfrac{y^{n-k}}{(1-y)^{n-k}}=\dfrac{1}{n} \binom{ n }{ k } \binom{ n-2 }{ k-1 } 
\end{align}
$$

数 $G_{n,k}$ 通常被称为 Narayana 数。其累计生成函数

$$
\begin{gather}
\Omega(z)=\partial_{u} G(z,u) |_{u=1}=\dfrac{1}{2}z+\dfrac{1}{2} \dfrac{z}{\sqrt{ 1-4z }}
\end{gather}
$$

于是可得叶子节点的均值 $\mu=n / 2$，并且该分布是集中的，因为我们可以计算出标准差为 $\sigma=O(\sqrt{ n })$.

现在来看二叉树 $\mathcal{B}$，它有构造

$$
\begin{gather}
\mathcal{B}=\mathcal{Z}+(\mathcal{B}\times \mathcal{Z})+(\mathcal{Z}\times \mathcal{B})+(\mathcal{B}\times \mathcal{Z}\times \mathcal{B})
\end{gather}
$$

右边的每一项分别对应于一类节点：叶子、左分支、右分支以及双分支。令 $u_{0},u_{1},u_{2}$ 分别标记度为 $0,1,2$ 的节点，则我们有

$$
\begin{gather}
B=zu_{0}+2zu_{1}B+z^{2}u_{2}B^{2}, \quad B=B(z,u_{0},u_{1},u_{2})
\end{gather}
$$

Lagrange 反演定理给出

$$
\begin{gather}
B_{n,k_{0},k_{1},k_{2}}=\dfrac{2^{k_{1}}}{n} \binom{ n }{ k_{0},k_{1},k_{2} } 
\end{gather}
$$

其中下标 $k_{0},k_{1},k_{2}$ 满足 $k_{0}+k_{1}+k_{2}=n$ 且 $k_{0}=k_{2}+1$. 同样，我们可以计算出相应于每个变量的各阶矩：

$$
\begin{gather}
u_{0}\text{:} \sim \dfrac{n}{4}, \quad u_{1}\text{:} \sim \dfrac{n}{2}, \quad u_{2}\text{:} \sim \dfrac{n}{4}
\end{gather}
$$

并且上述分布均是集中的：其标准差均为 $O(\sqrt{ n })$. 这表明，在一个随机二叉树中，四种节点的渐近比例是一致的。

下面我们来看第二个例子：Cayley 树 $\mathcal{T}$. 我们用 $u$ 来标记叶子节点，得到递归构造

$$
\begin{gather}
T(z,u)=zu+z(e^{T(z,u)}-1)
\end{gather}
$$

通过 Lagrange 反演定理，我们可以提取出用第二类 Stirling 数表示的系数公式。

类似地，对于 Cayley 树的简单变体 $T(z)=z\phi(T(z))$，其中 $\phi$ 是一个幂级数，并且度为 $k$ 的节点被标记的构造，其 BGF 为

$$
\begin{gather}
T(z,u)=z(\phi(T(z,u))+\phi_{k}(u-1)T(z,u)^{k}), \quad \phi_{k}=[u^{k}]\phi(u)
\end{gather}
$$

其累计生成函数

$$
\begin{gather}
\Omega(z)=z \dfrac{\phi_{k}T(z)^{k}}{1-z\phi'(T(z))}=\phi_{k}z^{2} T(z)^{k-1} T'(z)
\end{gather}
$$

从中可以提取出期望与标准差。

现在考虑我们在第四章中讨论的函数图 $\mathcal{F}$，它由一个三个方程所定义：

$$
\begin{gather}
\mathcal{F}=\mathrm{Set}(\mathcal{K}), \quad \mathcal{K}=\mathrm{Cyc}(\mathcal{T}), \quad \mathcal{T}=\mathcal{Z}\otimes \mathrm{Set}(\mathcal{T})
\end{gather}
$$

这转化为 EGF 的方程组：

$$
\begin{gather}
F(z)=e^{K(z)}, \quad K(z)=\ln \dfrac{1}{1-T(z)} ,\quad T(z)=ze^{T(z)}
\end{gather}
$$

我们可以分别将其转化为 BGF，其中变量 $u$ 分别标记了：1. 组分（连通图）的数量，2. 极大树的数量，3. 叶子节点的数量：

$$
\begin{align}
&F_{1}(z,u)=e^{uK(z)} \\
&F_{2}(z,u)=\dfrac{1}{1-uT(z)} \\
&F_{3}(z,u)=\dfrac{1}{1-T(z,u)}, \quad T(z,u)=(u-1)z+ze^{ T(z,u) }
\end{align}
$$

三元生成函数 $F(z,u_{1},u_{2})$，其中 $u_{1}$ 标记了组分的数量，$u_{2}$ 标记了树的个数，的表达式则可以写成

$$
\begin{gather}
F(z,u_{1},u_{2})=\exp\left( u_{1} \ln \dfrac{1}{1-u_{2}T(z)} \right)=\dfrac{1}{(1-u_{2}T(z))^{u_{1}}}
\end{gather}
$$

其系数可以由第一类 Stirling 数给出。

迄今为止，我们仅处理了直接通过递归所定义的参数，下面我们转到其它的递归参数，例如路径长度。设 $\mathcal{A}$ 是一个类，其上定义了两个标量参数 $\chi,\xi$，它们由以下公式所联系：

$$
\begin{gather}
\chi(\alpha)=|\alpha|+\xi(\alpha)
\end{gather}
$$

则利用 BGF 的组合形式可得

$$
\begin{gather}
\sum_{\alpha \in \mathcal{A}} z^{|\alpha|}u^{\chi(\alpha)}=\sum_{\alpha \in \mathcal{A}} z^{|\alpha|}u^{|\alpha|+\xi(\alpha)}=\sum_{\alpha \in \mathcal{A}} (zu)^{|\alpha|}u^{\xi(\alpha)}
\end{gather}
$$

换言之，我们有

$$
\begin{gather}
A_{\chi}(z,u)=A_{\xi}(zu,u)
\end{gather}
$$

即：参数的线性变换对应于 MGF 中标记变量的单项式替换。我们将使用这个原理来分析树结构中的路径长度。

一棵树 $\tau$ 的**路径长度**定义为其所有节点到根节点的距离之和，而两个节点间的距离则定义为连接它们的最短路径所包含的边数。形式上，路径长度 $\lambda$ 可以表示为

$$
\begin{gather}
\lambda(\tau)=\sum_{v\in \tau} d(v,\mathrm{root}(\tau))
\end{gather}
$$

其中 $v$ 取遍 $\tau$ 中的所有节点。通过简单的推导，我们可以写出它的一个递归公式：

$$
\begin{gather}
\lambda(\tau)=\sum_{\sigma \prec \tau} (\lambda(\sigma)+|\sigma|)
\end{gather}
$$

其中 $\sigma$ 取遍 $\tau$ 的所有子树。这是因为每个节点到 $\mathrm{root}(\tau)$ 的路径总是在最后一步从某个子树 $\sigma$ 的根节点到达 $\mathrm{root}(\tau)$，而前 $k-1$ 步则是该节点到 $\mathrm{root}(\sigma)$ 的一条最短路径，这样的路径一共有 $|\sigma|$ 条，对应于 $\sigma$ 的 $|\sigma|$ 个节点。

现在我们来看 Catalan 树中的路径长度，我们引入参数 $\mu(\alpha)=|\alpha|+\lambda(\alpha)$，则根据构造 $\mathcal{G}=\mathcal{Z}\times \mathrm{Seq}(\mathcal{G})$ 有

$$
\begin{gather}
G_{\lambda}(z,u)=\dfrac{z}{1-G_{\mu}(z,u)}, \quad G_{\mu}(z,u)=G_{\lambda}(zu,u)
\end{gather}
$$

因而，函数 $G(z,u)=G_{\lambda}(z,u)$ 满足非线性的函数方程

$$
\begin{gather}
G(z,u)=\dfrac{z}{1-G(zu,u)}
\end{gather}
$$

$\lambda$ 的累计生成函数同样可以通过求导得到：

$$
\begin{gather}
\Omega(z)=\dfrac{z}{(1-G(z))^{2}}(zG'(z)+\Omega(z))
\end{gather}
$$

解得

$$
\begin{gather}
\Omega(z)=z^{2} \dfrac{G'(z)}{(1-G(z))^{2}-z}=\dfrac{z}{2(1-4z)}-\dfrac{z}{2\sqrt{ 1-4z }}
\end{gather}
$$

这给出

$$
\begin{gather}
\Omega_{n}=[z^{n}]\Omega(z)=2^{2n-3}-\dfrac{1}{2} \binom{ 2n-2 }{ n-1 } , \quad n\geq 1
\end{gather}
$$

# Section 2: 完备生成函数

泛泛地说，我们所指的**完备**生成函数，是一种特殊的 MGF，其中使用了大量（在极限意义下可以是可数个）标记变量来标识一个类中的一族同质的特征（如各字符的出现次数、各长度循环的数量等）。作为一个基本例子，我们首先来看字符串类的完备生成函数。

考虑字符表 $\mathcal{A}=\{ a_{1},\dots,a_{r} \}$ 上的字符串类 $\mathcal{W}=\mathrm{Seq}(\mathcal{A})$，定义参数 $\chi=(\chi_{1},\dots,\chi_{r})$，其中 $\chi_{j}(w)$ 表示 $w$ 中字符 $a_{j}$ 的出现次数，那么 $\mathcal{A}$ 相应于 $\chi$ 的构造为

$$
\begin{gather}
\mathcal{A}=u_{1}a_{1}+\dots+u_{r}a_{r} \implies A(z,\mathbf{u})=zu_{1}+\dots+zu_{r}
\end{gather}
$$

显然参数 $\chi$ 是继承的，因此有

$$
\begin{gather}
\mathcal{W}=\mathrm{Seq}(\mathcal{A}) \implies W(z,\mathbf{u})=\dfrac{1}{1-z(u_{1}+\dots+u_{r})}
\end{gather}
$$

进而可知 $\mathcal{W}_{n}$ 中 $a_{1}$ 出现 $n_{1}$ 次，...，$a_{r}$ 出现 $n_{r}$ 次的字符串数量为

$$
\begin{gather}
[z^{n}u_{1}^{n_{1}}\dots u_{r}^{n_{r}}] \dfrac{1}{1-z(u_{1}+\dots+u_{r})}=\binom{ n }{ n_{1},\dots,n_{r} } 
\end{gather}
$$

我们就回到了通常的多项式系数。

作为一个进阶的例子，我们来考虑置换中各长度的循环。设变量 $u_{k}$ 标记了置换中长度为 $k$ 的循环的数量，则置换类 $\mathcal{P}$ 的 MGF 可以表示为

$$
\begin{gather}
P(z,\mathbf{u})=\exp\left( u_{1} \dfrac{z}{1}+u_{2} \dfrac{z^{2}}{2}+u_{3} \dfrac{z^{3}}{3}+\cdots \right)
\end{gather}
$$

通过将除了有限个 $u_{k}$ 外所有的 $u$ 均设为 $1$，我们就能得出关于任何有限个循环长度的所有感兴趣的具体情况，在这个意义下，我们的生成函数 $P(z,\mathbf{u})$ 编码了关于循环长度问题的一个完备集合，因而其得名为“完备”生成函数。

通常我们可以很容易地从完备生成函数中提取系数。例如，对于上面的 $P(z,\mathbf{u})$，我们从等价形式

$$
\begin{gather}
P(z,\mathbf{u})=e^{ u_{1}z / 1 } e^{ u_{2} z^{2} / 2 }e^{ u_{3} z^{3} / 3 } \cdots
\end{gather}
$$

立即得到具有 $k_{1}$ 个 $1$-循环，$k_{2}$ 个 $2$-循环，...，$k_{n}$ 个 $n$-循环的 $n$-置换的数量为

$$
\begin{gather}
n![z^{n}u_{1}^{k_{1}}\dots u_{n}^{k_{n}}]P(z,\mathbf{u})=\dfrac{n!}{k_{1}!k_{2}!\cdots k_{n}! 1^{k_{1}} 2^{k_{2}}\cdots n^{k_{n}}}
\end{gather}
$$

其中 $\sum_{j} jk_{j}=n$. 上述公式是由 Cauchy 首先发现的。类似地，设 $u_{k}$ 标记了集合划分中大小为 $k$ 的分块的数量，则集合划分类 $\mathcal{S}$ 的完备生成函数为

$$
\begin{gather}
S(z,\mathbf{u})=\exp\left( u_{1} \dfrac{z}{1!}+u_{2} \dfrac{z^{2}}{2!}+u_{3} \dfrac{z^{3}}{3!}+\cdots \right)
\end{gather}
$$

从中可以类似地得到具有 $k_{1}$ 个 $1$-分块，$k_{2}$ 个 $2$-分块，...，$k_{n}$ 个 $n$-分块的 $n$-划分的数量为

$$
\begin{gather}
\dfrac{n!}{k_{1}!k_{2}!\cdots k_{n}! 1!^{k_{1}} 2!^{k_{2}}\cdots n!^{k_{n}}}
\end{gather}
$$

同理，对于整数组合以及满射，它们相对于组分数量标识 $u_{k}$ 的完备生成函数分别为

$$
\begin{gather}
C(z,\mathbf{u})=\dfrac{1}{1-\sum_{j=1}^{\infty} u_{j}z^{j}}, \quad R(z,\mathbf{u})=\dfrac{1}{1-\sum_{j=1}^{\infty} u_{j} z^{j} / j!}
\end{gather}
$$

其相应于 $n=\sum_{j} jk_{j}$ 的系数分别为

$$
\begin{gather}
\binom{ k_{1}+\dots+k_{n} }{ k_{1},\dots,k_{n} } , \quad \dfrac{n!}{1!^{k_{1}}2!^{k_{2}}\cdots n!^{k_{n}}} \binom{ k_{1}+\dots+k_{n} }{ k_{1},\dots,k_{n} } 
\end{gather}
$$

## 字符串模型

下面我们来考虑两种模型：字符串模型与树模型的完备生成函数在各个问题中的应用。字符串的计数问题是组合分析中的一个非常丰富的章节，这是因为许多问题都可以被编码为字符串，就像我们在第一章中看到的那样。

作为一个例子，我们考虑字符表 $\mathcal{A}=\{ a_{1},\dots,a_{r} \}$ 上的字符串类 $\mathcal{W}$，其中我们赋予 $\mathcal{A}$ 自然的序关系 $a_{1}<a_{2}<\dots<a_{r}$. 对于一个字符串 $w=w_{1}w_{2}\dots w_{n}$，我们称 $w_{j}$ 是 $w$ 的一个**记录**，如果它大于前面的所有字符：对任意 $i<j$ 有 $w_{j}>w_{i}$. 我们想要对一个字符串中记录的数量进行枚举。

首先我们考虑 $\mathcal{W}$ 的子集，包含所有具有字符 $a_{i_{1}},\dots,a_{i_{k}}$ 作为连续记录的字符串，其构造可以表示为

$$
\begin{gather}
a_{i_{1}} \mathrm{Seq}(a_{1}+\dots+a_{i_{1}}) \cdots a_{i_{k}} \mathrm{Seq}(a_{1}+\dots+a_{i_{k}})
\end{gather}
$$

我们令变量 $z$ 标记长度，$v$ 标记记录的数量，$u_{j}$ 标记字符 $a_{j}$ 的出现次数，则上述子集的 MGF 为

$$
\begin{gather}
zv u_{i_{1}} (1-z(u_{1}+\dots+u_{i_{1}}))^{-1} \cdots zv u_{i_{k}} (1-z(u_{1}+\dots+u_{i_{k}}))^{-1}
\end{gather}
$$

对 $1\leq i_{1}<\dots<i_{k}\leq r$ 以及 $0\leq k\leq r$ 求和就得到

$$
\begin{gather}
W(z,v,\mathbf{u})=\prod_{s=1}^{r} (1+zvu_{s}(1-z(u_{1}+\dots+u_{s}))^{-1})
\end{gather}
$$

这里用到了恒等式

$$
\begin{gather}
\sum_{k=0}^{r} \sum_{1\leq i_{1}<\dots<i_{k}\leq r} y_{i_{1}}\cdots y_{i_{k}} = \prod_{s=1}^{r} (1+y_{s})
\end{gather}
$$

现在我们来计算一个 $n$-字符串中记录个数的均值，为了简便计算，我们假设所有字符出现的概率是均等的，此时我们可以令 $u_{j}=1$，得到

$$
\begin{gather}
W(z,v)=\prod_{j=1}^{r} \left( 1+\dfrac{zv}{1-jz} \right)
\end{gather}
$$

求导得到

$$
\begin{gather}
\Omega(z)=\partial_{v} W(z,v)|_{v=1}=\dfrac{z}{1-rz} \sum_{j=1}^{r} \dfrac{1}{1-(j-1)z}
\end{gather}
$$

从而得到期望

$$
\begin{gather}
\mu_{n}=H_{r}-\sum_{j=1}^{r-1} \dfrac{1}{r-j} \left( \dfrac{j}{r} \right)^{n}
\end{gather}
$$

式中的调和数 $H_{r}$ 也出现在置换的记录枚举中，但此时这里多了一个随 $n$ 增大而指数级减小的修正项。这一不同来自于字符串中每个字符可以重复出现，而置换中则不然。

现在我们来考虑字符的出现概率不均等的情况。设 $\mathcal{A}=\{ a_{1},\dots,a_{r} \}$ 是一个字符表，并设 $\Lambda=\{ \lambda_{1},\dots,\lambda_{r} \}$ 是一列实数称为**权重**，其中 $\lambda_{j}$ 与字符 $a_{j}$ 相关。我们定义一个字符串 $w$ 的权重为其字符权重之积：

$$
\begin{gather}
\pi(w)=\pi(a_{i_{1}}\cdots a_{i_{n}})=\lambda_{i_{1}}\cdots\lambda_{i_{n}}=\prod_{j=1}^{r} \lambda_{j}^{\chi_{j}(w)}
\end{gather}
$$

其中 $\chi_{j}(w)$ 为 $w$ 中字符 $a_{j}$ 的出现次数。最后，一个字符串集合的权重定义为其中字符串权重之和。

一个集合的权重可以直接从它的完备生成函数中得到：考虑子集 $\mathcal{S}\subset \mathcal{W}$ 的生成函数

$$
\begin{gather}
S(z,u_{1},\dots,u_{r})=\sum_{w\in \mathcal{S}} z^{|w|} u_{1}^{\chi_{1}(w)}\cdots u_{r}^{\chi_{r}(w)}
\end{gather}
$$

那么根据定义我们立即得到

$$
\begin{gather}
S(z,\lambda_{1},\dots,\lambda_{r})=\sum_{w\in \mathcal{S}} z^{|w|} \pi(w)=\sum_{n=0}^{\infty} z^{n} \pi(\mathcal{S}_{n})
\end{gather}
$$

换句话说，加权集合的生成函数是通过将权重的值代入相关的完备生成函数中所得到的。

在概率论中，Bernoulli 试验被定义为独立地从一个固定的、具有有限值域的分布（随机变量）中得到的一列结果。如果一个试验有 $r$ 种结果，每种结果出现的概率是 $p_{j}$，那么我们就可以用加权字符表 $\mathcal{A}=\{ a_{1},\dots,a_{r} \}$ 作为我们的模型，其中 $a_{j}$ 的权重为 $p_{j}$. 此时的系数 $[z^{n}]S(z,\lambda_{1},\dots,\lambda_{r})$ 就表示了 $\mathcal{W}_{n}$ 中的随机字符串属于 $\mathcal{S}$ 的概率。

为了演示这一点，我们来看一个例子。假设我们的试验是抛一块不均匀的硬币，其中得到正面（$H$）的概率为 $p$，反面（$T$）的概率是 $q=1-p$，考虑事件“抛 $n$ 次硬币，不出现连续 $\ell$ 次正面”的概率。这里我们的字符表为 $\mathcal{A}=\{ H,T \}$，权重分别为 $p,q$，我们所求的事件的构造如下：

$$
\begin{gather}
\mathcal{S}=\mathrm{Seq}_{<\ell}(H)\mathrm{Seq}(T\mathrm{Seq}_{<\ell}(H))
\end{gather}
$$

设 $u$ 标记正面，$v$ 标记反面，则有 MGF

$$
\begin{gather}
S(z,u,v)=\dfrac{1-z^{\ell}u^{\ell}}{1-zu}\left( 1-zv \dfrac{1-z^{\ell}u^{\ell}}{1-zu} \right)^{-1}
\end{gather}
$$

因此，所求事件的概率就是将 $u=p,v=q$ 代入 MGF 后 $z^{n}$ 的系数：

$$
\begin{gather}
[z^{n}] \dfrac{1-p^{\ell}z^{\ell}}{1-z+qp^{\ell}z^{\ell+1}}
\end{gather}
$$

## 树模型

迄今为止，我们遇到的树模型共分为两类：无编号的平面树（Catalan 树）以及有编号的非平面树（Cayley 树）。它们的共同特征是其生成函数都由函数方程

$$
\begin{gather}
Y(z)=z\phi(Y(z))
\end{gather}
$$

所定义，其中

$$
\begin{gather}
\phi(u)=\sum_{\omega \in\Omega} u^{\omega} \quad \text{或} \quad \phi(u)=\sum_{\omega \in\Omega} \dfrac{u^{\omega}}{\omega!}
\end{gather}
$$

取决于组合类是无编号的还是有编号的，且 $\Omega \subset \mathbb{N}$ 是所允许的节点度数。通常我们统一地将 $\phi$ 表示为

$$
\begin{gather}
\phi(w)=\sum_{j=0}^{\infty} \phi_{j} w^{j}
\end{gather}
$$

称为树的特征函数。下面我们将研究树结构的两种特征：度数与层次，它们在涉及树的算法分析中有许多应用。

首先我们来看度数，它由一系列参数 $\chi_{j}$ 所确定，其中 $\chi_{j}(\tau)$ 表示 $\tau$ 中度数为 $j$ 的节点的数量，我们用 $u_{j}$ 来标记 $\chi_{j}$，则有完备生成函数

$$
\begin{gather}
Y(z,\mathbf{u})=z \Phi(Y(z,\mathbf{u})), \quad \Phi(w)=u_{0}\phi_{0}+u_{1}\phi_{1}w+u_{2}\phi_{2}w^{2}+\cdots
\end{gather}
$$

利用 Lagrange 反演，我们得到以下结果：

**定理 6.2.1**

在以 $\phi$ 作为特征函数的树构成的类中，大小为 $n$ 且具有 $n_{j}$ 个出度为 $j$ 的节点的树的数量为

$$
\begin{gather}
Y_{n,n_{0},n_{1},n_{2},\dots}=\omega_{n} \dfrac{1}{n} \binom{ n }{ n_{0},n_{1},n_{2},\dots } \phi_{0}^{n_{0}} \phi_{1}^{n_{1}} \phi_{2}^{n_{2}}\cdots
\end{gather}
$$

其中 $\omega_{n}$ 是基本因子，且有相容性条件 $\sum_{j} n_{j}=n,\sum_{j}jn_{j}=n-1$.

**证明**

相容性条件是以下事实的反映：节点的数量为 $n$，且边的数量为 $n-1$. 剩余的结论来自 Lagrange 反演定理：

$$
\begin{gather}
Y_{n,n_{0},n_{1},\dots}=\omega_{n} [u_{0}^{n_{0}}u_{1}^{n_{1}}\cdots] \left( \dfrac{1}{n} [w^{n-1}] \Phi(w)^{n} \right)
\end{gather}
$$

交换 $[u_{0}^{n_{0}}u_{1}^{n_{1}}\cdots]$ 与 $[w^{n-1}]$ 的顺序即证。

例如，对于一般 Catalan 树（$\phi_{j}=1$）以及 Cayley 树（$\phi_{j}=1 / j!$），上述公式就可以表示为

$$
\begin{gather}
\dfrac{1}{n} \binom{ n }{ n_{0},n_{1},n_{2},\dots } , \quad \dfrac{(n-1)!}{0!^{n_{0}} 1!^{n_{1}} 2!^{n_{2}}\cdots} \binom{ n }{ n_{0},n_{1},n_{2},\dots } 
\end{gather}
$$

下面我们来看层次，或称为深度。设 $\tau$ 是一棵树，一个节点的层次定义为它到根节点的最短路径的长度，我们用 $u_{j}$ 来标记层次为 $j$ 的节点的数量，则其完备生成函数可以表示为如下的“连续 $\phi$-形式”

$$
\begin{gather}
Y(z,\mathbf{u})=zu_{0} \phi(zu_{1}\phi(zu_{2}\phi(zu_{3}\phi(\cdots))))
\end{gather}
$$

一些典型的例子如 Catalan 树的连分数

$$
\begin{gather}
Y(z,\mathbf{u})=\dfrac{u_{0}z}{1-\dfrac{u_{1}z}{1-\dfrac{u_{2}z}{1-\dfrac{u_{3}z}{\ddots}}}}
\end{gather}
$$

以及 Cayley 树的指数塔

$$
\begin{gather}
Y(z,\mathbf{u})=zu_{0}\exp(zu_{1} \exp(zu_{2}\exp(zu_{3}\exp(\cdots))))
\end{gather}
$$

根据 $u_{0},u_{1},\dots$ 的次数一层层地展开，我们即得下面的结论：

**定理 6.2.2**

在以 $\phi$ 作为特征函数的树构成的类中，大小为 $n$ 且具有 $n_{j}$ 个层次为 $j$ 的节点的树的数量为

$$
\begin{gather}
Y_{n,n_{0},n_{1},n_{2},\dots} =\omega_{n-1} \phi_{n_{1}}^{(n_{0})} \phi_{n_{2}}^{(n_{1})} \phi_{n_{3}}^{(n_{2})} \cdots, \quad \phi_{\nu}^{(\mu)}=[w^{\nu}] \phi(w)^{\mu}
\end{gather}
$$

其中 $\omega_{n}$ 是基本因子，且满足相容性条件 $n_{0}=1, \sum_{j}n_{j}=n$.

**证明**

相容性条件指出：在单个树中只有一个根节点（$n_{0}=1$），且节点的数量为 $n$. 剩下的结果由归纳法给出：设最大深度为 $k$，则有

$$
\begin{align}
Y_{n,n_{0},n_{1},\dots,n_{k}}&=\omega_{n-1} [z^{n-1}] [u_{1}^{n_{1}}\cdots u_{k}^{n_{k}}] \phi(zu_{1}\phi(\cdots)) \\
&=\omega_{n-1} [z^{n-1}] [u_{1}^{n_{1}}\cdots u_{k}^{n_{k}}] \phi_{n_{1}}^{(n_{0})} z^{n_{1}}u_{1}^{n_{1}} \phi(zu_{2}\phi(\cdots))^{n_{1}} \\
&=\omega_{n-1}[z^{n-1}] [u_{1}^{n_{1}}\cdots u_{k}^{n_{k}}] \phi_{n_{1}}^{(n_{0})} \phi_{n_{2}}^{(n_{1})} z^{n_{1}+n_{2}} u_{1}^{n_{1}} u_{2}^{n_{2}} \phi(\cdots)^{n_{2}} \\
&=\cdots \\
&=\omega_{n-1} [z^{n-1}][u_{1}^{n_{1}}\cdots u_{k}^{n_{k}}] \phi_{n_{1}}^{(n_{0})}\cdots \phi_{n_{k}}^{(n_{k-1})} z^{n-1} u_{1}^{n_{1}}\cdots u_{k}^{n_{k}} \\
&= \omega_{n-1} \phi_{n_{1}}^{(n_{0})}\cdots \phi_{n_{k}}^{(n_{k-1})}
\end{align}
$$

对 $k$ 归纳即证。

特别地，对于 Catalan 树以及 Cayley 树有公式

$$
\begin{gather}
\binom{ n_{0}+n_{1}-1 }{ n_{1} } \binom{ n_{1}+n_{2}-1 }{ n_{2} } \cdots, \quad \dfrac{(n-1)!}{n_{0}!n_{1}!n_{2}!\cdots} n_{0}^{n_{1}} n_{1}^{n_{2}} n_{2}^{n_{3}}\cdots
\end{gather}
$$

此外，对于 $n_{0}$ 棵树组成的森林，其相应的系数就是

$$
\begin{gather}
Y_{n,n_{0},n_{1},n_{2},\dots}=\omega_{n-n_{0}} \phi_{n_{1}}^{(n_{0})}\phi_{n_{2}}^{(n_{1})}\phi_{n_{3}}^{(n_{2})}\cdots
\end{gather}
$$

这可以通过对函数

$$
\begin{gather}
F(z,\mathbf{u})=Y(z,\mathbf{u})^{n_{0}}
\end{gather}
$$

提取系数得到。注意当 $n_{0}=1$ 时上式就退化为了单棵树的生成函数。

在生成函数 $Y(z,\mathbf{u})$ 中将 $u_{j}$ 替换为 $q^{j}$，则上述 MGF 枚举了树结构中的路径长度，由变量 $q$ 所标记。特别地，对于 Catalan 树和 Cayley 树，有

$$
\begin{gather}
G(z,q)=\dfrac{z}{1-\dfrac{zq}{1-\dfrac{zq^{2}}{1-\dfrac{zq^{3}}{\ddots}}}}, \quad T(z,q)=z\exp(zq \exp(zq^{2} \exp(\cdots)))
\end{gather}
$$

从中我们可以提取出系数的均值与标准差。

# Section 3: 其它构造

## 指示与替换

设 $(\mathcal{F},\chi)$ 是一个类-参数对，$F(\mathbf{z})$ 是相应的 MGF，其中 $z_{0}$ 标记了大小，并且 $z_{k}$ 标记了 $\chi$ 的第 $k$ 个组分。如果 $z=z_{0}$ 指示了大小，那么就像单变量生成函数中一样，应用 $\theta_{z}=z\partial_{z}$ 就表示了指示一个原子使其与其它原子区分开来。更一般地说，设 $x=z_{j}$，由于

$$
\begin{gather}
x\partial_{x} (s^{a} t^{b} x^{c})=c(s^{a}t^{b}x^{c})
\end{gather}
$$

故算子 $\theta_{x}=x\partial_{x}$ 有一个清晰的组合解释：它表示从 $\mathcal{F}$ 的元素中取出所有由变量 $x$ 所标记的物体并指向其中一个。例如，设 $F(z,u)$ 是树结构类的 BGF，其中 $z$ 指示大小，$u$ 指示叶子节点的数量，则 $\theta_{u}F(z,u)$ 就计数了有一个叶子节点被区分出来的树的个数。

类似地，对生成函数 $F$ 应用替换 $x\mapsto S(\mathbf{z})$，其中 $S(\mathbf{z})$ 是类 $\mathcal{S}$ 的 MGF，所表示的就是用 $\mathcal{S}$ 中的元素替换 $\mathcal{F}$ 元素中由 $x$ 标记的物体。我们用一个例子来说明这一点。

我们考虑整数组合的一种变体，其中相邻的加数需要满足一定的约束 $\mathcal{R}\subset \mathbb{N}^{2}$. 例如，下面的两个约束

$$
\begin{gather}
\mathcal{R}_{1}=\{ (x,y) \mid 1\leq x\leq y \}, \quad \mathcal{R}_{2}=\{ (x,y) \mid 1\leq y\leq 2x \}
\end{gather}
$$

分别对应于加数单调递增，以及下一个加数不超过上一个的两倍的情况。我们可以用一种柱状图来表示这样的组合，其中每个加数都对应于一个列，其高度对应于加数的值。

设 $F(z,u)$ 是这种 $\mathcal{R}$-组合的 BGF，其中 $z$ 指示了总和（即每列的高度之和），$u$ 指示了最后一个加数的值（即最后一列的高度），则 $F$ 满足以下的函数方程：

$$
\begin{gather}
F(z,u)=f(zu)+(\mathcal{L}[F(z,u)])_{u\mapsto zu}
\end{gather}
$$

其中 $f(z)$ 是单列组合构成的类的生成函数，而 $\mathcal{L}$ 是一个作用在 $u$ 的形式幂级数上的线性算子，满足

$$
\begin{gather}
\mathcal{L}[u^{j}]=\sum_{(j,k)\in \mathcal{R}} u^{k}
\end{gather}
$$

事实上，上面的方程递归地描述了这种 $\mathcal{R}$-组合的结构：它或者是一个单列，或者是从一个已有的组合中加入一列所得到的，如图所示：

![](6-1.png)

在高度为 $j$ 的列之后加入高度为 $k$ 的列，其中 $(j,k)\in \mathcal{R}$，正是算子 $\mathcal{L}$ 所要表达的，而最后的替换 $u\mapsto zu$ 则将新加入的 $k$ 个原子纳入考虑。特别地，函数 $F(z,1)$ 枚举了 $\mathcal{F}$-物体的数量，而不考虑最后一列的大小。

当约束条件 $\mathcal{R}$ 相对简单时，我们通常可以得到 $F$ 的一个解析解，其通常由一种递推过程所给出。首先我们来看 $\mathcal{R}=\mathcal{R}_{1}$，假设第一列的高度可以取任意正整数，那么它所计数的实际上是整数分拆的数量。我们有

$$
\begin{gather}
\mathcal{L}[u^{j}]=u^{j}+u^{j+1}+u^{j+2}+\cdots=\dfrac{u^{j}}{1-u}
\end{gather}
$$

则 $F(z,u)$ 满足递归方程

$$
\begin{gather}
F(z,u)=\dfrac{zu}{1-zu}+\dfrac{1}{1-zu}F(z,zu)
\end{gather}
$$

由于任何线性递推方程

$$
\begin{gather}
\phi(u)=\alpha(u)+\beta(u)\phi(\sigma(u))
\end{gather}
$$

都有形式解

$$
\begin{gather}
\phi(u)=\alpha(u)+\beta(u)\alpha(\sigma(u))+\beta(u)\beta(\sigma(u)) \alpha(\sigma^{[2]}(u))+\cdots
\end{gather}
$$

其中 $\sigma^{[k]}(u)$ 表示 $\sigma$ 的 $k$ 次复合，故我们有

$$
\begin{gather}
F(z,u)=\dfrac{zu}{1-zu}+\dfrac{z^{2}u}{(1-zu)(1-z^{2}u)}+\dfrac{z^{3}u}{(1-zu)(1-z^{2}u)(1-z^{3}u)}+\cdots
\end{gather}
$$

其另一个等价形式

$$
\begin{gather}
F(z,u)=\dfrac{zu}{1-z}+\dfrac{z^{2}u^{2}}{(1-z)(1-z^{2})}+\dfrac{z^{3}u^{3}}{(1-z)(1-z^{2})(1-z^{3})}+\cdots
\end{gather}
$$

可以通过将 $F(z,u)$ 展开为 $u$ 的形式幂级数，并在递推式

$$
\begin{gather}
(1-zu)F(z,u)=zu+F(z,zu)
\end{gather}
$$

上应用待定系数法得到。这一形式与第一章中我们得到的整数拆分公式是一致的：显然 $u^{k}$ 的系数是加数最大值为 $k$ 的整数拆分的生成函数。

相同的方法也可以被应用于 $\mathcal{R}_{2}$ 上，其相应的线性算子为

$$
\begin{gather}
\mathcal{L}[u^{j}]=u+\dots+u^{2j}=u \dfrac{1-u^{2j}}{1-u}
\end{gather}
$$

为简单起见，我们假设第一列只能取 $1$，则 $F$ 满足递归方程

$$
\begin{gather}
F(z,u)=zu+\dfrac{zu}{1-zu}(F(z,1)-F(z,z^{2}u^{2}))
\end{gather}
$$

将 $F(z,1)$ 看成一个已知量，并令 $a(u)=zu+zu F(z,1) (1-zu)^{-1}$，则有

$$
\begin{gather}
F(z,u)=a(u)-\dfrac{zu}{1-zu} a(z^{2}u^{2})+\dfrac{zu}{1-zu} \dfrac{z^{2}u^{2}}{1-z^{2}u^{2}} a(z^{6}u^{4})- \cdots
\end{gather}
$$

代入 $u=1$ 即可解得 $F(z,1)$：

$$
\begin{gather}
F(z,1)=\dfrac{\sum_{j\geq 1} (-1)^{j-1} z^{2^{j+1}-j-2} / Q_{j-1}(z)}{\sum_{j\geq 0} (-1)^{j} z^{2^{j+1}-j-2} / Q_{j}(z)}, \\
Q_{j}(z)=(1-z)(1-z^{3})(1-z^{7})\cdots (1-z^{2^{j}-1})
\end{gather}
$$

它枚举了二叉树中层级剖面 $(n_{0},n_{1},n_{2},\dots)$ 的数量（即有 $n_{j}$ 个层级为 $j$ 的节点），或者将 $1$ 表示为 $1,\dfrac{1}{2},\dfrac{1}{4},\dfrac{1}{8},\dots$ 之和的方法数。

在这一例子中，我们所发展的方法通常被称为“切分法”，它在许多计数问题中有广泛的应用。

## 序限制

在编号类的章节中，我们讨论了编号积中的序限制，回顾一下修正编号积

$$
\begin{gather}
\mathcal{A}=(\mathcal{B}^{\min}\otimes \mathcal{C})
\end{gather}
$$

包含了 $\mathcal{B}\otimes \mathcal{C}$ 中所有最小编号位于 $\mathcal{B}$ 中的元素。当我们将一元生成函数扩展为多元函数时，同样的证明可以被逐字逐句地应用，得到对应的 MGF 为

$$
\begin{gather}
A(z,\mathbf{u})=\int_{0}^{z} (\partial_{t}B(t,\mathbf{u}))C(t,\mathbf{u}) \mathrm{d} t
\end{gather}
$$

下面我们给出它的一个应用。

一个置换 $\sigma=\sigma_{1}\dots\sigma_{n}$ 中的每个项 $\sigma_{i}$ 可以按照它与两边的元素大小对比对应于一个递增二叉树中的四类节点：

$$
\begin{align}
\sigma_{i-1}<\sigma_{i}>\sigma_{i+1} \quad &\text{叶子节点}(u_{0}) \\
\sigma_{i-1}<\sigma_{i}<\sigma_{i+1} \quad &\text{右分支节点}(u_{1}) \\
\sigma_{i-1}>\sigma_{i}>\sigma_{i+1} \quad &\text{左分支节点}(u_{1}') \\
\sigma_{i-1}>\sigma_{i}<\sigma_{i+1} \quad &\text{双分支节点}(u_{2})
\end{align}
$$

其中我们定义 $\sigma_{0}=\sigma_{n+1}=-\infty$. 设 $\widehat{\mathcal{I}}$ 表示所有非空递增二叉树构成的类，并令 $u_{0},u_{1},u_{1}',u_{2}$ 分别标记四类节点的数量，则有

$$
\begin{gather}
\widehat{\mathcal{I}}=u_{0}\mathcal{Z}+u_{1}(\mathcal{Z}^{\min}\otimes  \widehat{\mathcal{I}})+u_{1}'(\widehat{\mathcal{I}}\otimes \mathcal{Z}^{\min})+u_{2}(\widehat{\mathcal{I}}\otimes \mathcal{Z}^{\min}\otimes  \widehat{\mathcal{I}})
\end{gather}
$$

这给出了 $\widehat{\mathcal{I}}$ 的指数 MGF 所满足的微分方程

$$
\begin{gather}
\partial_{z} \widehat{I}(z,\mathbf{u})=u_{0}+(u_{1}+u_{1}') \widehat{I}(z,\mathbf{u})+u_{2} \widehat{I}(z,\mathbf{u})^{2}
\end{gather}
$$

由 $\widehat{I}(0,\mathbf{u})=0$ 解得

$$
\begin{gather}
\widehat{I}(z,\mathbf{u})=\dfrac{\delta}{u_{2}} \dfrac{v_{1}+\delta \tan(z\delta)}{\delta-v_{1}\tan(z\delta)}-\dfrac{v_{1}}{u_{2}}, \quad v_{1}=\dfrac{u_{1}+u_{1}'}{2}, \quad \delta=\sqrt{ u_{0}u_{2}-v_{1}^{2} }
\end{gather}
$$

上述结果，当赋予各 $u$ 特定的取值时，给出了一系列与局部序特征相关的置换计数问题的解。例如，如果取 $u_{0}=u_{1}=u_{1}'=u_{2}=1$，即得所有非空置换的 EGF $\dfrac{z}{1-z}$；而如果取 $u_{0}=u_{2}=1,u_{1}=u_{1}'=0$，则可以得到交错排列的 EGF $\tan(z)$；此外，赋值 $u_{0}=u_{1}=u, u_{1}'=u_{2}=1$ 给出了 Eulerian 数的一个简单变体，我们将在后文对其进行讨论。

根据构造

$$
\begin{gather}
\widehat{\mathcal{I}}=\mathcal{Z}+(\mathcal{Z}^{\min}\otimes  \widehat{\mathcal{I}})+(\widehat{\mathcal{I}}\otimes \mathcal{Z}^{\min})+(\widehat{\mathcal{I}}\otimes \mathcal{Z}^{\min}\otimes  \widehat{\mathcal{I}})
\end{gather}
$$

以及我们在第一节中发展的技术，我们可以分析递增二叉树的路径长度。事实上，一个大小为 $n$ 的随机递增二叉树的平均路径长度为

$$
\begin{gather}
2n\ln n+O(n)
\end{gather}
$$

这表明，递增二叉树是相当平衡的，与一般的 Catalan 树相对。这也解释了为什么二叉搜索树（BST）在大多数情况下都有良好的性能，下面解释原因。

给定一个置换 $\tau$，其相应的二叉搜索树递归地定义如下：

$$
\begin{gather}
\mathrm{BST}(\varepsilon)=\varnothing, \quad \mathrm{BST}(\tau)=(\mathrm{BST}(\tau|_{<\tau_{1}}),\tau_{1},\mathrm{BST}(\tau|_{>\tau_{1}}))
\end{gather}
$$

再令 $\mathrm{IBT}(\sigma)$ 表示置换 $\sigma$ 相应的递增二叉树，则我们有等价原理：

$$
\begin{gather}
\mathrm{IBT}(\sigma) \overset{\text{shape}}{=} \mathrm{BST}(\sigma^{-1})
\end{gather}
$$

其中 $A \overset{\text{shape}}{=} B$ 表示树 $A$ 和 $B$ 拥有同样的形状，从而也就具有相同的路径长度。

## 隐式构造

对于由 $\mathcal{A}=\mathscr{C}(\mathcal{X})$ 所定义的隐式结构 $\mathcal{X}$，其对应的 MGF 可以像单变量生成函数一样简单地解出。同样，我们将用两个例子来说明这个过程。

假设我们要通过节点的数量（由 $z$ 标记）和边的数量（由 $u$ 标记）来枚举连通图 $\mathcal{K}$，则 $\mathcal{K}$ 与所有编号图 $\mathcal{G}$ 由指数公式所关联：

$$
\begin{gather}
\mathcal{G}=\mathrm{Set}(\mathcal{K})
\end{gather}
$$

意思是所有编号图都可以唯一地分解为连通部分的集合。上述构造转化为指数 MGF 的等式：

$$
\begin{gather}
G(z,u)=\exp K(z,u) \implies K(z,u)=\ln G(z,u)
\end{gather}
$$

由于具有 $n$ 个节点和 $k$ 条边的编号图的数量为 $\binom{ n(n-1) / 2 }{ k }$，故

$$
\begin{gather}
K(z,u)=\ln\left( 1+\sum_{n=1}^{\infty} (1+u)^{n(n-1) / 2} \dfrac{z^{n}}{n!} \right)
\end{gather}
$$

这一公式是对第四章中单变量公式的一个扩展。此外，函数

$$
\begin{gather}
\widehat{K}(z,u)=K\left( \dfrac{z}{u},u \right)
\end{gather}
$$

枚举了连通图中的节点数量（由 $z$ 标记）和图的过剩量（边超过顶点的数量，由 $u$ 标记）。这表明 Wright 分解可以被重新表述为

$$
\begin{align}
&\ln\left( 1+\sum_{n=1}^{\infty} (1+u)^{n(n-1) / 2} \dfrac{z^{n}}{n!} \right)= \dfrac{1}{u}W_{-1}(z)+W_{0}(z)+uW_{1}(z)+\cdots \\
&= \dfrac{1}{u}\left( T-\dfrac{1}{2}T^{2} \right)+\left( \dfrac{1}{2}\ln \dfrac{1}{1-T}-\dfrac{1}{2}T-\dfrac{1}{4}T^{2} \right)+\cdots
\end{align}
$$

其中 $T=T(z)$ 满足 $T(z)=z\exp T(z)$.

另一个例子关乎任意字符表 $\mathcal{A}=\{ a_{1},\dots,a_{r} \}$ 上的字符串 $\mathcal{W}$. 我们定义一个 **Smirnov 词**为一个没有连续相同字符的字符串，所有 Smirnov 词构成的类记作 $\mathcal{S}$. 我们同样用 $v_{j}$ 来标记 $a_{j}$ 在字符串中的出现次数，省略掉标记长度的变量 $z$，我们有

$$
\begin{gather}
W(v_{1},\dots,v_{r})=\dfrac{1}{1-(v_{1}+\dots+v_{r})}
\end{gather}
$$

从一个 Smirnov 词开始，如果我们把每个字符 $a_{j}$ 都替换为 $a_{j}$ 的一个非空序列 $\mathrm{Seq}_{\geq 1}(a_{j})$，那么我们就可以得到一个不受限制的字符串。反之也是同理：我们可以把一个字符串中的所有连续出现的字符压缩为单个字符，得到一个 Smirnov 词，这给出了 $\mathcal{S}$ 的一个隐式构造：

$$
\begin{gather}
\mathcal{W}=\mathcal{S}[a_{1} \mapsto \mathrm{Seq}_{\geq 1}(a_{1}),\dots,a_{r} \mapsto \mathrm{Seq}_{\geq 1}(a_{r})]
\end{gather}
$$

从而有

$$
\begin{gather}
W(v_{1},\dots,v_{r})=S\left( \dfrac{v_{1}}{1-v_{1}},\dots,\dfrac{v_{r}}{1-v_{r}} \right)
\end{gather}
$$

由于 $v / (1-v)$ 的反函数是 $v / (1+v)$，我们解得

$$
\begin{gather}
S(v_{1},\dots,v_{r})=W\left( \dfrac{v_{1}}{1+v_{1}},\dots,\dfrac{v_{r}}{1+v_{r}} \right)=\left( 1-\sum_{j=1}^{r} \dfrac{v_{j}}{1+v_{j}} \right)^{-1}
\end{gather}
$$

现在，令所有 $v_{j}=z$，这就是说我们“忘记”了字符串的内部结构，只保留它的长度信息，则我们得到了由长度所枚举的 Smirnov 词的 OGF

$$
\begin{gather}
S(z)=\dfrac{1}{1-r \dfrac{z}{1+z}}=\dfrac{1+z}{1-(r-1)z}=1+\sum_{n=1}^{\infty} r(r-1)^{n-1} z^{n}
\end{gather}
$$

这与初等组合学给出的结果是一致的：一个 Smirnov 词由第一个字符（有 $r$ 种选择）和后续的 $n-1$ 个字符确定（每个字符有 $r-1$ 种选择，以避免连续字符的出现）。上述模型也可以用于每个字符出现概率不均等的 Bernoulli 试验中，此时我们需要执行 $v_{j}=p_{j}z$ 的替换。

在上述模型的基础上，我们还可以定义所谓的“广义 Smirnov 词”，其中每个字符最多连续出现 $m$ 次（Smirnov 词就是 $m=1$ 时的特例）。它的精细枚举可以在 $S(v_{1},\dots,v_{r})$ 上执行 $v_{j}\mapsto v_{j}+\dots+v_{j}^{m}$ 的替换得到，再执行 $v_{j}=z$ 的替换，我们可得由长度所枚举的 OGF

$$
\begin{gather}
\dfrac{1}{1-r \dfrac{z \frac{1-z^{m}}{1-z}}{1+z \frac{1-z^{m}}{1-z}} }=\dfrac{1-z^{m+1}}{1-rz+(r-1)z^{m+1}}
\end{gather}
$$

上述技术扩展了我们在第一章中研究的二进制字符串中字符连续出现的问题，此外，它同样也适用于每个字符出现次数有不同的上界和下界的情况，只需在 $S(v_{1},\dots,v_{r})$ 中执行相应的替换即可。

## 容斥原理

在经典组合学中，容斥原理（inclusion-exclusion principle）是一个极为常用的计数方法，它建立了精确计数与过量计数的关系。我们将首先演示它在经典组合学中的形式和应用，然后我们将在符号计数方法中重现这一方法。

设 $\mathcal{E}$ 是一个集合，其上定义了一个实值或复值可加测度 $|\cdot|$，这就是说，当 $A,B\subset \mathcal{E}$ 满足 $AB=A\cap B=\varnothing$ 时，有

$$
\begin{gather}
|A\cup B|=|A|+|B|
\end{gather}
$$

成立。通常，我们将 $|\cdot|$ 取为计数测度（$|A|$ 表示 $A$ 中元素的个数）或者定义在有限集上的概率测度 $\mathbb{P}$，则由基本的集合论原理

$$
\begin{gather}
\sum_{c\in A\cup B} |c|=\sum_{a\in A} |a|+\sum_{b\in B} |b|-\sum_{i\in A\cap B} |i|
\end{gather}
$$

可得容斥原理的最简单形式：

$$
\begin{gather}
|A\cup B|=|A|+|B|-|AB|
\end{gather}
$$

被称为“容斥原理”或者“筛法”的则是如下的广义形式：

$$
\begin{align}
&|A_{1}\cup\dots \cup A_{r}| = |\mathcal{E}\setminus (A_{1}^{c} A_{2}^{c}\dots A_{r}^{c})| \\
&= \sum_{1\leq i\leq r} |A_{i}|-\sum_{1\leq i_{1}<i_{2}\leq r} |A_{i_{1}}A_{i_{2}}| +\dots+ (-1)^{r-1} |A_{1}A_{2}\dots A_{r}|
\end{align}
$$

其中 $A^{c}=\mathcal{E}\setminus A$ 是 $A$ 的补集。另一种形式可以通过执行替换 $B_{j}=A_{j}^{c}$ 得到：

$$
\begin{gather}
|B_{1}\dots B_{r}|=|\mathcal{E}|-\sum_{1\leq i\leq r} |B_{i}^{c}|+\sum_{1\leq i_{1}<i_{2}\leq r} |B_{i_{1}}^{c}B_{i_{2}}^{c}|-\dots+(-1)^{r}|B_{1}^{c}\dots B_{r}^{c}|
\end{gather}
$$

这就是说，同时满足一系列条件的元素的数量（$B_{1}\dots B_{r}$）可以通过枚举不满足一些条件的元素的数量（$B_{j}^{c}$）得到。

下面是应用容斥原理的一个典型例子。回顾一下，我们称一个置换 $\sigma$ 是一个错排，如果 $\sigma$ 没有不动点。令 $\mathcal{E}$ 为 $[n]$ 上所有置换构成的集合，$B_{j}$ 则是满足 $\sigma_{j}\neq j$ 的置换构成的集合，其补集就是 $\sigma_{j}=j$ 的置换构成的集合。代入容斥原理的表达式，则等式左边就是我们要求的错排数 $D_{n}$，而右边的第 $k$ 个求和的值可以通过以下过程得到：首先在 $n$ 个数中选择 $k$ 个作为不动点，剩下的数就形成了一个 $(n-k)$-置换，这给出共 $\binom{ n }{ k }(n-k)!$ 种置换，从而有

$$
\begin{gather}
D_{n}=n!-\binom{ n }{ 1 } (n-1)!+\binom{ n }{ 2 } (n-2)!-\dots+(-1)^{n} \binom{ n }{ n } 0!
\end{gather}
$$

即

$$
\begin{gather}
\dfrac{D_{n}}{n!}=1-\dfrac{1}{1!}+\dfrac{1}{2!}-\dots+\dfrac{(-1)^{n}}{n!}
\end{gather}
$$

现在，我们要在符号计数方法中重新推导出容斥原理，实际上，我们将看到，这一过程是非常直观且简单的。仍以错排为例，考虑置换构成的类 $\mathcal{P}$，我们构造集合 $\mathcal{Q}$ 如下：对任意 $\sigma \in \mathcal{P}$，按任意方式和数量标出 $\sigma$ 中的不动点，$\mathcal{Q}$ 则由所有这样的标记-置换对 $(l,\sigma)$ 构成。例如，$\mathcal{Q}$ 中包含

$$
\begin{gather}
132,\quad \underline{1}32, \quad 123, \quad \underline{1}23, \quad \underline{12}3, \quad 12\underline{3}, \quad \underline{123}
\end{gather}
$$

等等，其中数字下方的横线表示被标出的不动点。显然，$\mathcal{Q}$ 具有构造

$$
\begin{gather}
\mathcal{Q}\cong \mathcal{U}\otimes  \mathcal{P}, \quad \mathcal{U}=\mathrm{Set}(\mathcal{Z})
\end{gather}
$$

因为标记拥有自然的排序。在本例子中，我们有

$$
\begin{gather}
Q(z)=\dfrac{e^{z}}{1-z}
\end{gather}
$$

现在我们已经枚举出了容斥原理中的每一项 $\binom{ n }{ k }(n-k)!$，只不过符号是错的（原式中符号是交替的，而这里全部是加号）。为了修正这个问题，我们引入变量 $v$ 来指示被标出的不动点的数量，则有

$$
\begin{gather}
Q(z,v)=\dfrac{e^{vz}}{1-z}
\end{gather}
$$

此外，我们引入 $\mathcal{P}$ 的 BGF $P(z,u)$ 来枚举 $\mathcal{P}$ 中元素的大小（由 $z$ 指示）以及不动点的数量（由 $u$ 指示）。有一些不动点被标出的置换则可以通过在 $P(z,u)$ 中执行替换 $u=1+v$ 得到，换言之，$P$ 和 $Q$ 通过以下等式所联系：

$$
\begin{gather}
Q(z,v)=P(z,1+v)
\end{gather}
$$

从中我们可以立即解得

$$
\begin{gather}
P(z,u)=Q(z,u-1)=\dfrac{e^{(u-1)z}}{1-z}
\end{gather}
$$

令 $u=0$（表示没有不动点）就得到了正确的公式

$$
\begin{gather}
D(z)=P(z,0)=\dfrac{e^{-z}}{1-z}
\end{gather}
$$

换句话说，我们由过量计数（$Q$）的结果得到了精确计数（$P$）的结果。

上述过程显然可以推广到其它计数问题上：为了枚举含有精确数量的模式的对象，我们可以将其转化为枚举在特定位置含有模式的对象，而后者通常是更容易计算的。要得到原问题的生成函数，我们只需执行替换 $v=u-1$，或者在单变量情况下取 $v=-1$，此时得到的生成函数就枚举了不含有这种模式的对象的数量。

下面我们给出两个例子。在置换 $\sigma=\sigma_{1}\dots\sigma_{n}$ 中，一个**上升**（ascent）是一对相邻的项 $\sigma_{i}\sigma_{i+1}$ 使得 $\sigma_{i}<\sigma_{i+1}$，设 $A_{n,k}$ 表示长度为 $n$ 且有 $k$ 个上升的置换的个数。根据对称性，这也是长度为 $n$ 且有 $k$ 个下降（$\sigma_{i}\sigma_{i+1}$ 使得 $\sigma_{i}>\sigma_{i+1}$）的置换的个数。按照惯例，我们用 $A(z,u)$ 来表示 $A_{n,k}$ 的指数 BGF，其中 $u$ 指示了上升的数量。

按照符号容斥原理的模板，我们首先计算在特定位置含有上升的置换的数量，这些置换构成集合 $\mathcal{B}$. 例如，$\mathcal{B}$ 包含下面的置换

$$
\begin{gather}
2,6,1, \boxed{3 \nearrow 4 \nearrow 8 \nearrow 9 \nearrow 11} , 15,12, \boxed{5 \nearrow 10}, 13,7,14
\end{gather}
$$

其中那些被标出的上升由箭头所表示。我们称一个被标示的极大连续上升序列为一个“集簇”（在例子中以方框的形式呈现），用 $\mathcal{C}$ 来表示，则我们有构造

$$
\begin{gather}
\mathcal{B}=\mathrm{Seq}(\mathcal{Z}+\mathcal{C}), \quad \mathcal{C}=(\mathcal{Z}\nearrow \mathcal{Z})+(\mathcal{Z}\nearrow \mathcal{Z}\nearrow \mathcal{Z})+\cdots=\mathrm{Set}_{\geq 2}(\mathcal{Z})
\end{gather}
$$

这是因为集簇是一个单调递增的序列，或者说一个集合，从而有

$$
\begin{gather}
B(z)=\dfrac{1}{1-(z+(e^{z}-1-z))}=\dfrac{1}{2-e^{z}}
\end{gather}
$$

这恰好是满射构成的类的 EGF.

接下来，我们引入变量 $v$ 来指示被标记的上升，由于一个大小为 $k$ 的集簇含有 $k-1$ 个上升，故

$$
\begin{gather}
B(z,v)=\dfrac{1}{1-\left( z+\dfrac{e^{zv}-1-zv}{v} \right)}=\dfrac{v}{v+1-e^{zv}}
\end{gather}
$$

现在，根据容斥原理，$A(z,u)$ 可以通过执行替换 $v=u-1$ 得到：

$$
\begin{gather}
A(z,u)=B(z,u-1)=\dfrac{u-1}{u-e^{ z(u-1) }}
\end{gather}
$$

其系数 $A_{n,k}$ 被称为 **Eulerian 数**，它的前几项为

$$
\begin{gather}
1+z+(u+1) \dfrac{z^{2}}{2!}+(u^{2}+4u+1) \dfrac{z^{3}}{3!}+(u^{3}+11u^{2}+11u+1) \dfrac{z^{4}}{4!}+\cdots
\end{gather}
$$

同样的方法可以被用于枚举置换中**上升段**的数量。一个置换 $\sigma$ 中的 $\ell$-上升段被定义为序列 $\sigma_{i}\dots\sigma_{i+\ell}$ 使得 $\sigma_{i}<\dots<\sigma_{i+\ell}$（因此，一个上升就是一个 1-上升段）。我们定义一个集簇为一系列被标示的重叠 $\ell$-上升段。例如，当 $\ell=3$ 时，置换

$$
\begin{gather}
2,6,1, \boxed{3 \nearrow 4 \nearrow 8 \nearrow 9 \nearrow 11} , 15,12, 5,10 , 13,7,14
\end{gather}
$$

中由方框标出的一段就是一个集簇。按前面的方法，我们有

$$
\begin{gather}
B(z,v)=\dfrac{1}{1-(z+\widehat{I}(z,v))}, \quad \widehat{I}(z,v)=\sum_{n,k} I_{n,k} v^{k} \dfrac{z^{n}}{n!}
\end{gather}
$$

其中 $B(z,v)$ 枚举了集簇的数量，而 $I_{n,k}$ 则表示用 $k$ 个长度为 $\ell$ 的区间 $[i,i+\ell]$ 覆盖实数区间 $[1,n]$ 的方法数。根据初等组合学，我们能够给出数列 $I_{n,k}$ 的 OGF：第一个区间必然被放置在最左边，剩下的每个区间都可以在前一个区间的基础上向右移动 $1,2,\dots,\ell$ 个单位，从而有

$$
\begin{gather}
I(z,v)=\sum_{n,k} I_{n,k} v^{k} z^{n} = \dfrac{z^{\ell+1}v}{1-v(z+z^{2}+\dots+z^{\ell})}
\end{gather}
$$

为了从 $I(z,v)$ 变换到 $\widehat{I}(z,v)$，我们首先进行部分分式分解

$$
\begin{gather}
I(z,v)=1-z+\sum_{j=1}^{\ell} \dfrac{c_{j}(v)}{1-\omega_{j}(v)z}
\end{gather}
$$

其中 $\omega_{j}(v)$ 是方程 $\omega^{\ell}=v(1+\omega+\dots+\omega^{\ell-1})$ 的第 $j$ 个根。然后执行替换 $z^{n}\mapsto \dfrac{z^{n}}{n!}$，这使得 $\dfrac{c}{1-\omega z}$ 被替换为 $ce^{\omega z}$，从而就有

$$
\begin{gather}
A(z,u)=\dfrac{1}{1-(z+\widehat{I}(z,u-1))}, \quad \widehat{I}(z,v)=1-z+\sum_{j=1}^{\ell} c_{j}(v)e^{ \omega_{j}(v)z }
\end{gather}
$$

另一个例子是字符串中的模式匹配。给定字符串类 $\mathcal{W}=\mathrm{Seq}(\mathcal{A})$，其中 $\mathcal{A}=\{ a_{1},\dots,a_{r} \}$ 是任意字符表，以及一个模式 $\mathfrak{p}=p_{1}\dots p_{k}$，我们要求 $\mathcal{W}$ 的 BGF $W(z,u)$，其中 $u$ 指示了模式 $\mathfrak{p}$ 在字符串中出现的次数。我们在第一章中已经完成了 $W(z,0)$ 的推导，也就是不包含模式 $\mathfrak{p}$ 的字符串的数量。

为了应用容斥原理，我们引入 $\mathcal{X}$，也就是有一些 $\mathfrak{p}$ 被标示的字符串构成的集合。我们定义一个集簇为一个相互重叠的、被标示的模式 $\mathfrak{p}$ 的极大序列。例如，当 $\mathfrak{p}=aaaaa$ 时，下面的字符串可以给出如下的集簇：

![](6-2.png)

因此 $\mathcal{X}$ 就可以表示为字符与集簇的序列：

$$
\begin{gather}
\mathcal{X}=\mathrm{Seq}(\mathcal{A}+\mathcal{C})
\end{gather}
$$

对于集簇 $\mathcal{C}$ 自身，它可以通过对模式 $\mathfrak{p}$ 向右平移得到，只要满足一定的条件，即平移后的模式应当与前面的模式有重叠的部分。考虑第一章中定义的自相关多项式 $c(z)$，并定义 $\widehat{c}(z)=c(z)-1$，我们可以证明，对于一个含有 $s$ 个模式的集簇，其对应的 OGF 正是 $z^{k}\widehat{c}(z)^{s-1}$：上面例子中的这个集簇是 $z^{5}\widehat{c}(z)^{2}$ 中的一项，如图所示：

![](6-3.png)

对所有可能的重叠方式求和，则集簇的 OGF $C(z)=z^{k}(1-\widehat{c}(z))^{-1}$，从而其 BGF 为

$$
\begin{gather}
C(z,v)=\dfrac{v z^{k}}{1-v\widehat{c}(z)}
\end{gather}
$$

这给出 $\mathcal{X}$ 的 BGF，其中 $v$ 指示了被标出的模式的数量，为

$$
\begin{gather}
X(z,v)=\dfrac{1}{1-(rz+vz^{k}(1-v\widehat{c}(z))^{-1})}
\end{gather}
$$

最后，根据常规的容斥原理替换（$v=u-1$），我们立即得到

$$
\begin{gather}
W(z,u)=\dfrac{(u-1)c(z)-u}{(1-rz)((u-1)c(z)-u)+(u-1)z^{k}}
\end{gather}
$$

代入 $u=0$ 即可得到第一章中的函数 $S$.

# Section 4: 极值参数

除了可继承的加性参数（也就是迄今为止我们一直在研究的）以外，另一类非常重要的参数是那些由某种最大规则所定义的参数，典型的例子如一种组合构造中的最大分量（例如一个置换中的最长循环），以及递归构造中的递归深度（例如一棵树中的最大层次）。由于最大值函数的非线性性，我们之前发展的 MGF 理论对此没有较大的帮助。不过，对于这种问题，我们有一个标准技巧，即考虑一族由一个**极值参数** $\chi$ 进行索引的单变量函数 $f^{[k]}(z)$，这种函数可以使用单变量生成函数理论进行处理。

## 最大分量

考虑构造 $\mathcal{B}=\Phi[\mathcal{A}]$，其中 $\Phi$ 是基础构造的任意组合，并且为了简单起见，我们假设 $\Phi$ 是一个非递归的构造。则符号计数方法保证了其生成函数有对应的关系

$$
\begin{gather}
B(z)=\Psi[A(z)]
\end{gather}
$$

其中 $\Psi$ 是 $\Phi$ 通过符号计数方法转化得到的泛函。通过 $\Phi$，类 $\mathcal{A}$ 中的元素呈现为 $\beta \in \mathcal{B}$ 的一个分量，其大小则由 $\mathcal{A}$ 的大小函数确定。我们定义 $\mathcal{B}^{\langle b \rangle}$ 由所有使得 $\mathcal{A}$-分量的大小 $\leq b$ 的 $\beta \in \mathcal{B}$ 构成，它的生成函数与 $\mathcal{B}$ 拥有相同的构造，只需将 $\mathcal{A}$ 的生成函数 $A(z)$ “截断”即可：

$$
\begin{gather}
B^{\langle b \rangle }(z)=\Psi[\mathbf{T}_{b} A(z)]
\end{gather}
$$

其中截断算子 $\mathbf{T}_{b}$ 定义为

$$
\begin{gather}
\mathbf{T}_{b}f(z)=\sum_{n=0}^{b} f_{n} z^{n} \quad \left( f(z)=\sum_{n=0}^{\infty} f_{n}z^{n} \right)
\end{gather}
$$

事实上，一些最大分量问题我们在前面的章节就已经见过了。例如，置换的循环分解

$$
\begin{gather}
\mathcal{P}=\mathrm{Set}(\mathrm{Cyc}(\mathcal{Z})) \implies P(z)=\exp\left( \ln \dfrac{1}{1-z} \right)
\end{gather}
$$

给出了循环长度 $\leq b$ 的置换的 EGF

$$
\begin{gather}
P^{\langle b \rangle }(z)=\exp\left( \dfrac{z}{1}+\dfrac{z^{2}}{2}+\dots+\dfrac{z^{b}}{b} \right)
\end{gather}
$$

其中 $\exp$ 内部的函数正是截断对数。

另一个例子中，字符串的编号类构造

$$
\begin{gather}
\mathcal{W}=\mathrm{Seq}_{m}(\mathrm{Set}(\mathcal{Z})) \implies W(z)=(e^{z})^{m}
\end{gather}
$$

给出了每个字符出现次数 $\leq b$ 的字符串的 EGF

$$
\begin{gather}
W^{\langle b \rangle }(z)=\left( 1+\dfrac{z}{1!}+\dfrac{z^{2}}{2!}+\dots+\dfrac{z^{b}}{b!} \right)^{m}
\end{gather}
$$

其中乘方函数的内部则是截断指数。类似地，分块的大小 $\leq b$ 的集合划分的 EGF 为

$$
\begin{gather}
S^{\langle b \rangle }(z)=\exp\left( \dfrac{z}{1!}+\dfrac{z^{2}}{2!}+\dots+\dfrac{z^{b}}{b!} \right)
\end{gather}
$$

一个稍复杂的例子是二进制字符串中的连续字符段。字符表 $\{ a,b \}$ 上的字符串类 $\mathcal{W}$ 具有无编号构造

$$
\begin{gather}
\mathcal{W}=\mathrm{Seq}(a)\ \mathrm{Seq}(b\ \mathrm{Seq}(a))
\end{gather}
$$

其 OGF 具有形式

$$
\begin{gather}
W(z)=Y(z) \dfrac{1}{1-zY(z)}, \quad Y(z)=\dfrac{1}{1-z}
\end{gather}
$$

于是，字符 $a$ 连续出现的次数 $\leq k-1$ 的 $w\in \mathcal{W}$ 的数量有 OGF

$$
\begin{gather}
W^{\langle k \rangle }(z)=Y^{\langle k \rangle }(z) \dfrac{1}{1-zY^{\langle k \rangle }(z)}, \quad Y^{\langle k \rangle }(z)=1+z+z^{2}+\dots+z^{k-1}
\end{gather}
$$

因此

$$
\begin{gather}
W^{\langle k \rangle }(z)=\dfrac{1-z^{k}}{1-2z+z^{k+1}}
\end{gather}
$$

因此，关于最大分量的生成函数是容易推导的。然而，相较于由继承参数给出的生成函数，它的渐近分析通常更为困难，其原因在于截断算子的复分析特性，我们将在后续的章节进行讨论。

## 最大深度

递归构造的深度是对树结构层次的一种扩展。考虑递归构造

$$
\begin{gather}
\mathcal{B}=\Phi[\mathcal{B}]
\end{gather}
$$

其中 $\Phi$ 是任意构造，我们定义 $\mathcal{B}^{[h]}$ 是 $\mathcal{B}$ 的一个子集，使其包含所有那些由最多 $h$ 次 $\Phi$ 的应用得到的 $\beta \in \mathcal{B}$，因此根据定义有

$$
\begin{gather}
\mathcal{B}^{[h+1]}=\Phi[\mathcal{B}^{[h]}]
\end{gather}
$$

因此，设 $\Psi$ 是 $\Phi$ 在符号计数方法中的对应泛函，对于 $\mathcal{B}^{[h]}$ 的生成函数我们有

$$
\begin{gather}
B^{[h+1]}(z)=\Psi[B^{[h]}(z)]
\end{gather}
$$

下面我们给出几个例子。考虑平面 Catalan 树

$$
\begin{gather}
\mathcal{G}=\mathcal{Z}\times \mathrm{Seq}(\mathcal{G}) \implies G(z)=\dfrac{z}{1-G(z)}
\end{gather}
$$

定义一棵树的**高度**为从根节点到叶子节点的最长路径中边的数量。则高度 $\leq h$ 的 Catalan 树满足递归方程

$$
\begin{gather}
\mathcal{G}^{[0]}=\mathcal{Z} ,\quad \mathcal{G}^{[h+1]}=\mathcal{Z}\times \mathrm{Seq}(\mathcal{G}^{[h]})
\end{gather}
$$

这给出

$$
\begin{gather}
G^{[0]}(z)=z, \quad G^{[h+1]}(z)=\dfrac{z}{1-G^{[h]}(z)}
\end{gather}
$$

展开递推式，我们可得

$$
\begin{gather}
G^{[h]}(z)=\dfrac{z}{1-\dfrac{z}{1-\dfrac{z}{\dfrac{\ddots}{1-z} }}}
\end{gather}
$$

这通常被称为一个“有限连分数”。

对于平面二叉树

$$
\begin{gather}
\mathcal{B}=\mathcal{Z}+\mathcal{B}\times \mathcal{B} \implies B(z)=z+B(z)^{2}
\end{gather}
$$

我们有递归方程

$$
\begin{gather}
B^{[0]}(z)=z, \quad B^{[h+1]}(z)=z+(B^{[h]}(z))^{2}
\end{gather}
$$

在这种情况下，$B^{[h]}(z)$ 具有“连续平方”形式：

$$
\begin{gather}
B^{[h]}(z)=z+(z+(z+(\cdots)^{2})^{2})^{2}
\end{gather}
$$

它与 Mandelbrot 集和 Mandelbrot 分形有紧密的联系。

对于 Cayley 树

$$
\begin{gather}
\mathcal{T}=\mathcal{Z}\otimes  \mathrm{Set}(\mathcal{T}) \implies T(z)=ze^{T(z)}
\end{gather}
$$

其 EGF 满足递归方程

$$
\begin{gather}
T^{[0]}(z)=z, \quad T^{[h+1]}(z)=ze^{ T^{[h]}(z) }
\end{gather}
$$

从而我们有“连续指数”形式

$$
\begin{gather}
T^{[h]}(z)=z\exp(z\exp(z\exp(\cdots z \exp z)))
\end{gather}
$$

这些例子表明，对于递归深度的分析与迭代理论和动力系统的研究是密切相关的。在这些问题中，代数方法通常是不可用的，我们只能诉诸于复分析方法给出的近似解。

## 统计分析

对于极值参数，它们的矩分析遵循一种特定的模式。设 $\mathcal{F}$ 是一个组合类，其生成函数为 $f(z)$，考虑一个参数 $\chi$ 使得 $f^{[h]}(z)$ 枚举了那些 $\chi$ 值至多为 $h$ 的对象，那么那些 $\chi$ 值等于 $h$ 的对象的生成函数为

$$
\begin{gather}
f^{[h]}(z)-f^{[h-1]}(z)
\end{gather}
$$

从而 $\chi$ 的累计值的生成函数由以下函数给出：

$$
\begin{align}
\Xi(z)&= \sum_{h=0}^{\infty} h (f^{[h]}(z)-f^{[h-1]}(z)) \\
&= \sum_{h=0}^{\infty} (f(z)-f^{[h]}(z))
\end{align}
$$

其中第二个等式由分部求和法给出。

对于最大分量，$\Xi$ 包含了截断的 Taylor 级数；对于最大深度，$\Xi$ 包含了递归构造泛函 $\Psi$ 的不动点（函数 $f(z)$）与由迭代得到的对不动点的估计（函数 $f^{[h]}(z)$）之差。这是极值分析中的一种常见情形。