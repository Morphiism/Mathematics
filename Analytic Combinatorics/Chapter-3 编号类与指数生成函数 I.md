组合学中的许多结构自然地表现为一种带有编号的对象，其中物体的每个原子都带有一个“标记”以使其与其它原子区分开来。这其中最常见的是**图**的结构，它被定义为三元组 $G=(V,E,\phi)$，包含顶点集 $V$，边集 $E$，以及函数 $\phi\colon E\to V^{2}$ 将一条边 $e$ 与一对顶点 $(v_{i},v_{j})$ 对应。通常，一个图的顶点数和边数是有限的，并且我们将每个顶点视为不同的对象，这就给出了一个典型的有编号对象：

![](3-1.png)

其中编号图 $g$ 具有顶点集 $\{ 1,2,3,4 \}$，这也是它的编号构成的集合（特别地，顶点 $i$ 具有编号 $i$），以及边集 $\{ e_{13},e_{14},e_{23},e_{24} \}$，关联函数 $\phi$ 可以从图中读出。

编号类与无编号类最大的区别在于它们之间的乘法。对于编号类，直接取两个元素形成有序对是不够的：它们的编号需要被重新分配以确保各原子的编号均不相同。我们将看到，这使得编号类的乘积类在计数时多了一个因子，正是这一区别导致了它们的生成函数的不同：无编号类是普通生成函数（OGF）$\sum f_{n}z^{n}$，而编号类则是指数生成函数（EGF）$\sum f_{n}z^{n} / n!$.

# Section 1: 编号类

正如我们前面提到的，编号图是所有编号对象的底层结构：几乎所有带编号的组合对象都可以使用图来编码，因此我们给出下面的定义：

**定义 3.1.1** 编号对象（labelled object），编号类（labelled class）

一个大小为 $n$ 的**编号对象**是一个图，其顶点集是正整数的子集，且顶点数为 $n$. 称一个大小为 $n$ 的编号对象是**良编号的**，如果它的顶点集是 $[n]$. 一个**编号类**就是一个由良编号对象构成的组合类。

注意，上述定义中的图可以是无向图，也可以是有向图。通常，我们不会显式地写出一个编号对象的图表示，在大多数情况下，这种对应关系可以简单地从上下文中推导出来。

另外一个注意事项：尽管我们一直将图作为一种编号对象看待，但我们也可以将其作为无编号对象来看待，这样得到的组合类所统计的就是图的“形状”。以前面的图 $g$ 为例，其无编号的对应物就是将其所有顶点去除编号后得到的“影子”：

![](3-2.png)

为了统计编号对象的数量，我们给出下面的定义：

**定义 3.1.2** 指数生成函数（exponential generating function）

序列 $(A_{n})_{n\geq 0}$ 的**指数生成函数**（EGF）定义为形式幂级数

$$
\begin{gather}
A(z)=\sum_{n=0}^{\infty} A_{n} \dfrac{z^{n}}{n!}
\end{gather}
$$

一个编号类的 EGF 是其计数序列的 EGF。等价地，编号类 $\mathcal{A}$ 的 EGF 定义为

$$
\begin{gather}
A(z)=\sum_{\alpha \in \mathcal{A}} \dfrac{z^{|\alpha|}}{|\alpha|!}
\end{gather}
$$

称变量 $z$ 在生成函数中指示了大小。

利用系数提取的记号，我们可知 EGF $f(z)$ 中 $z^{n} / n!$ 项的系数 $f_{n}$ 可以表示为

$$
\begin{gather}
f_{n}=n! [z^{n}] f(z)
\end{gather}
$$

在编号类的计数问题中，有三种结构是最基本的：置换、空图和循环，它们的构造如下：

**例 3.1.3** 置换（permutation）

一个置换 $\sigma=\sigma_{1}\dots\sigma_{n}$ 在编号类 $\mathcal{P}$ 中的表示是一个线性的长链

$$
\begin{gather}
\sigma_{1}-\sigma_{2}-\dots-\sigma_{n}
\end{gather}
$$

从而 $\mathcal{P}$ 可以表示为

$$
\begin{gather}
\mathcal{P}=\{ \varepsilon,1,1-2,2-1,1-2-3,1-3-2,\dots \}
\end{gather}
$$

显然 $P_{n}=n!$，从而其 EGF 为 $P(z)=\sum_{n\geq 0}z^{n}=(1-z)^{-1}$.

**例 3.1.4** 空图（empty graph）

一个大小为 $n$ 的**空图**定义为图 $([n],\varnothing,\varnothing)$，即没有边连接的图。空图构成的编号类 $\mathcal{U}$ 可以表示为

$$
\begin{gather}
\mathcal{U}=\{ \varepsilon,1,1\ 2, 1\ 2\ 3,1\ 2\ 3\ 4,\dots \}
\end{gather}
$$

有时候，将空图替换为按编号递增的线性长链

$$
\begin{gather}
1-2-3-4-5
\end{gather}
$$

也是可行的。显然有 $U_{n}=1$，因此其 EGF 为 $U(z)=\sum_{n\geq 0}z^{n} / n! = e^{z}$.

**例 3.1.5** 循环（cycle）

在编号类 $\mathcal{C}$ 中，一个循环 $(12345)$ 通常表示为带有一个环的有向图：

![](3-3.png)

一个长度为 $n$ 的循环共有 $n$ 种线性表示（选择其中一个数放在开头，共有 $n$ 种选法），而线性表示与置换是一一对应的，因此长度为 $n$ 的循环的数量为 $(n-1)!$，因此其 EGF 为

$$
\begin{gather}
\sum_{n\geq 0} \dfrac{z^{n}}{n}=\ln \dfrac{1}{1-z}
\end{gather}
$$

我们之后将会看到，对数函数是编号对象的循环构造的特征。

# Section 2: 可容许的构造

现在我们给出一系列从原始编号类 $\mathcal{E},\mathcal{Z}$ 构造出其它编号类的方法。编号类的**无交并**与无编号类是相同的，于是其生成函数仍然是 $B(z)+C(z)$. 接下来，我们要定义编号类的乘积，我们不能直接取 $\mathcal{A}=\mathcal{B}\times \mathcal{C}$，因为一对良编号的对象不是良编号的：编号 $1$ 必然会出现两次。因此，在我们给出**编号积**的定义之前，我们先来定义编号的分配方式。

**定义 3.2.1** 重编号（relabeling）

设 $\alpha$ 是一个编号对象，其编号集为 $A$，$f\colon A\to f[A]$ 是一个严格递增函数，则 $\alpha$ 的一个**重编号**是编号对象 $\alpha'$，其具有编号集 $f[A]$.

就我们的需求而言，有两种本质上等价的重编号方法是有用的：

**定义 3.2.2** 约化（reduction），扩张（expansion）

设 $\alpha$ 是一个大小为 $n$ 的编号对象，它的**约化**是 $\alpha$ 的重编号 $\rho(\alpha)$ 使得其编号集是 $[n]$.

设 $\alpha$ 是一个良编号对象，它的一个**扩张**是 $\alpha$ 的重编号 $\beta$，记作 $e(\alpha)$.

上面的定义允许我们定义两个良编号对象的乘积，其思路就是取有序对，并重新分配编号。

**定义 3.2.3** 编号积（labelled product）

两个良编号对象 $\beta,\gamma$ 的**编号积**定义为集合

$$
\begin{gather}
\beta \otimes \gamma=\{ (\beta',\gamma') \mid (\beta',\gamma')\text{是良编号的}, \rho(\beta')=\beta, \rho(\gamma')=\gamma \}
\end{gather}
$$

等价地，$\beta,\gamma$ 的编号积定义为集合

$$
\begin{gather}
\beta \otimes \gamma=\{ (e(\beta),f(\gamma)) \mid \mathrm{im}(e)\cap \mathrm{im}(f)=\varnothing, \mathrm{im}(e)\cup \mathrm{im}(f)=[|\beta|+|\gamma|] \}
\end{gather}
$$

其中 $e,f$ 是重编号函数，$\mathrm{im}(e)$ 定义为 $e(\beta)$ 的编号集。

根据定义我们可以看出，编号积中的元素都是良编号的，并且 $\beta \otimes\gamma$ 中的元素个数为

$$
\begin{gather}
\binom{ |\beta|+|\gamma| }{ |\beta| } =\binom{ |\beta|+|\gamma| }{ |\gamma| } 
\end{gather}
$$

这个二项式系数因子非常重要，原因将在下面给出。

**定义 3.2.4** 编号积（labelled product）

两个编号类 $\mathcal{B},\mathcal{C}$ 的**编号积**定义为

$$
\begin{gather}
\mathcal{B}\otimes \mathcal{C}=\bigcup_{\beta \in \mathcal{B},\gamma \in \mathcal{C}} (\beta \otimes \gamma)
\end{gather}
$$

利用编号积以及无交并，我们可以继续定义序列、循环、集合等构造，同时，我们也将证明其可容许性。

首先我们来看编号积，它的计数序列满足等式

$$
\begin{gather}
A_{n}=\sum_{|\beta|+|\gamma|=n} \binom{ |\beta|+|\gamma| }{ |\beta| } B_{|\beta|}C_{|\gamma|}=\sum_{k=0}^{n} \binom{ n }{ k } B_{k}C_{n-k}
\end{gather}
$$

在等式两边乘以 $z^{n} / n!$ 并求和就得到

$$
\begin{gather}
A(z)=\sum_{n=0}^{\infty} \sum_{k=0}^{n} \dfrac{B_{k}C_{n-k} z^{n}}{k!(n-k)!}=\sum_{k=0}^{\infty} \sum_{n=k}^{\infty} \dfrac{B_{k}z^{k}}{k!} \dfrac{C_{n-k}z^{n-k}}{(n-k)!}=B(z)C(z)
\end{gather}
$$

注意到，二项式系数 $\binom{ n }{ k }$ 正对应了 EGF 的乘积，事实上，这是编号类使用 EGF 进行计数的根本原因。

多个编号类的乘积也是类似的：当 $\mathcal{A}=\mathcal{B}^{(1)}\otimes\dots \otimes \mathcal{B}^{(r)}$ 时有

$$
\begin{gather}
A_{n}=\sum_{n_{1}+\dots+n_{r}=n} \binom{ n }{ n_{1},\dots,n_{r} } B_{n_{1}}^{(1)}\cdots B_{n_{r}}^{(r)} \implies A(z)=B^{(1)}(z)\cdots B^{(r)}(z)
\end{gather}
$$

其中 $\binom{ n }{ n_{1},\dots,n_{r} }$ 是多项式系数，它统计了将 $n$ 个物体中的 $n_{1}$ 个分为第一类，$n_{2}$ 个分为第二类，...，$n_{r}$ 个分为第 $r$ 类的方法数。

**定义 3.2.5** 序列，$k$-序列（sequence）

设 $\mathcal{B}$ 是一个编号类，它的 $k$**-序列**构造定义为

$$
\begin{gather}
\mathrm{Seq}_{k}(\mathcal{B})=\underbrace{ \mathcal{B}\otimes \dots \otimes \mathcal{B} }_{ k }
\end{gather}
$$

当 $\mathcal{B}_{0}=\varnothing$ 时，它的**序列**构造定义为

$$
\begin{gather}
\mathrm{Seq}(\mathcal{B})=\mathcal{E}+\mathcal{B}+(\mathcal{B}\otimes \mathcal{B})+(\mathcal{B}\otimes \mathcal{B}\otimes \mathcal{B})+\cdots=\bigcup_{k\geq 0} \mathrm{Seq}_{k}(\mathcal{B})
\end{gather}
$$

序列构造的生成函数与无编号类是相同的，它给出

$$
\begin{gather}
\mathcal{A}=\mathrm{Seq}_{k}(\mathcal{B}) \implies A(z)=B(z)^{k} \\
\mathcal{A}=\mathrm{Seq}(\mathcal{B}) \implies A(z)=\sum_{k=0}^{\infty}  B(z)^{k}=\dfrac{1}{1-B(z)}
\end{gather}
$$

**定义 3.2.6** 集合，$k$-集合（set）

设 $\mathcal{B}$ 是一个编号类，它的 $k$**-集合**定义为商集

$$
\begin{gather}
\mathrm{Set}_{k}(\mathcal{B})=\mathrm{Seq}_{k}(\mathcal{B}) / \mathbf{R}
\end{gather}
$$

其中 $\mathbf{R}$ 如定义 1.2.6 所示。当 $\mathcal{B}_{0}=\varnothing$ 时，其**集合**构造定义为

$$
\begin{gather}
\mathrm{Set}(\mathcal{B})=\bigcup_{k\geq 0} \mathrm{Set}_{k}(\mathcal{B})
\end{gather}
$$

一个 $k$-集合严格对应了 $k!$ 个 $k$-序列，这可以通过为 $k$-集合重新排序得到：首先选取第一个元素，共有 $k$ 个选项，然后选取第二个元素，共 $k-1$ 个选项，以此类推，最后我们就得到了 $k!$ 种选法。因此我们有

$$
\begin{gather}
\mathcal{A}=\mathrm{Set}_{k}(\mathcal{B}) \implies A(z)= \dfrac{1}{k!} B(z)^{k} \\
\mathcal{A}=\mathrm{Set}(\mathcal{B}) \implies A(z)=\sum_{k=0}^{\infty} \dfrac{B(z)^{k}}{k!} =\exp B(z)
\end{gather}
$$

在编号类中，每个对象都是不同的，因此没有了 $\mathrm{MSet}$ 与 $\mathrm{PSet}$ 的区别。此外，编号类在直接计数的公式上比起无编号类更加简单。

**定义 3.2.7** 循环，$k$-循环（cycle）

设 $\mathcal{B}$ 是一个编号类，它的 $k$**-循环**定义为商集

$$
\begin{gather}
\mathrm{Cyc}_{k}(\mathcal{B})=\mathrm{Seq}_{k}(\mathcal{B}) / \mathbf{S}
\end{gather}
$$

其中 $\mathbf{S}$ 如定义 1.2.5 所示。当 $\mathcal{B}_{0}=\varnothing$ 时，其**循环**构造定义为

$$
\begin{gather}
\mathrm{Cyc}(\mathcal{B})=\bigcup_{k\geq 1} \mathrm{Cyc}_{k}(\mathcal{B})
\end{gather}
$$

一个 $k$-循环严格对应了 $k$ 个 $k$-序列，对应了循环的 $k$ 种线性表示方法，因此我们有

$$
\begin{gather}
\mathcal{A}=\mathrm{Cyc}_{k}(\mathcal{B})\implies A(z)=\dfrac{1}{k}B(z)^{k} \\
\mathcal{A}=\mathrm{Cyc}(\mathcal{B}) \implies A(z)=\sum_{k=1}^{\infty} \dfrac{B(z)^{k}}{k}=\ln \dfrac{1}{1-B(z)}
\end{gather}
$$

总结上述讨论，我们给出编号类的可容许性定理：

**定理 3.2.8** 可容许性定理（编号类）

编号类的无交并、编号积、序列、集合与循环构造都是可容许的，其 EGF 如下：

$$
\begin{align}
\mathcal{A}=\mathcal{B}+\mathcal{C} &\implies A(z)=B(z)+C(z) \\
\mathcal{A}=\mathcal{B}\otimes \mathcal{C} &\implies A(z)=B(z)C(z) \\
\mathcal{A}=\mathrm{Seq}_{k}(\mathcal{B}) &\implies A(z)=B(z)^{k} \\
\mathcal{A}=\mathrm{Seq}(\mathcal{B}) &\implies A(z)=\dfrac{1}{1-B(z)} \\
\mathcal{A}=\mathrm{Set}_{k}(\mathcal{B}) &\implies A(z)= \dfrac{1}{k!} B(z)^{k} \\
\mathcal{A}=\mathrm{Set}(\mathcal{B}) &\implies A(z)=\exp B(z) \\
\mathcal{A}=\mathrm{Cyc}_{k}(\mathcal{B}) &\implies A(z)=\dfrac{1}{k}B(z)^{k} \\
\mathcal{A}=\mathrm{Cyc}(\mathcal{B}) &\implies A(z)=\ln \dfrac{1}{1-B(z)}
\end{align}
$$

其中序列、集合、循环构造中有 $\mathcal{B}_{0}=\varnothing$.

和无编号类一样，在编号类中也可以定义**可构造类**，它就是由单位类 $\mathcal{E}=\{ \varepsilon \}$，原子类 $\mathcal{Z}=\{ 1 \}$，以及定理 3.2.8 中的构造的复合所得到的类。定理 3.2.8 的一个直接推论就是我们可以自动地得到可构造类的生成函数所满足的函数方程：

**定理 3.2.9** 符号计数方法（编号类）

一个可构造类的 EGF 是一个函数方程组中的一项，方程组中的项仅包含 $1,z$ 以及运算

$$
\begin{gather}
+,\times,Q(f)=\dfrac{1}{1-f}, E(f)=\exp f, L(f)=\ln \dfrac{1}{1-f}
\end{gather}
$$

如果我们将具有限制的构造纳入考虑，那么运算 $f^{k},f^{k} / k!,f^{k} / k$ 也将被加入列表。

本章，我们同样将给出一些在组合学中的经典构造，并讨论它们的一些变体，我们将看到，利用符号计数方法，一旦我们得到其原始规范，从中得到变体几乎是毫不费力的。

本节的最后，我们来讨论一下编号类与无编号类的联系。对于一个编号类 $\mathcal{A}$，我们可以定义它的**无编号对应物**为将 $\mathcal{A}$ 中的元素的编号全部去除所得到的组合类 $\widehat{\mathcal{A}}$. 对于 $\widehat{\mathcal{A}}$ 中的一个大小为 $n$ 的元素，每个等价类必然包含了 $\geq 1$ 而 $\leq n!$ 个元素（考虑为其赋予编号的方式），因此我们有：

**定理 3.2.10**

编号类 $\mathcal{A}$ 与其无编号对应物 $\widehat{\mathcal{A}}$ 的计数序列有不等式

$$
\begin{gather}
\widehat{A}_{n}\leq A_{n}\leq n! \widehat{A}_{n}, \quad \text{i.e.},\quad 1\leq \dfrac{A_{n}}{\widehat{A}_{n}}\leq n!
\end{gather}
$$

通过几个例子我们就可以知道，上面的不等式无法再进一步改进。左边的不等式在 $\mathcal{A}=\mathcal{U}=\mathrm{Set}(\mathcal{Z})$ 时得到：其无编号对应物与 $\mathcal{U}$ 相同，因此 $\widehat{U}_{n}=U_{n}=1$. 另一边，当 $\mathcal{A}=\mathcal{P}=\mathrm{Seq}(\mathcal{Z})$ 时，其无编号对应物就是自然数类 $\mathrm{Seq}(\mathcal{Z})$，因此有 $P_{n}=n! \widehat{P}_{n}=n!$.

尽管编号类与其无编号对应物的计数序列没有直接的联系，但至少我们可以从编号类的一个规范得到无编号对应物的规范：具体来说，设

$$
\begin{gather}
\mathcal{A}=\Phi(\mathcal{E},\mathcal{Z},+,\otimes,\mathrm{Seq},\mathrm{Set},\mathrm{Cyc})
\end{gather}
$$

是一个可构造的编号类，那么它的无编号对应物就具有规范

$$
\begin{gather}
\widehat{A}=\Phi(\mathcal{E},\mathcal{Z},+,\times,\mathrm{Seq},\mathrm{MSet},\mathrm{Cyc})
\end{gather}
$$

换句话说，将 $\mathcal{A}$ 的规范中所有涉及的运算全部替换为其对应的无编号运算，就得到了 $\widehat{\mathcal{A}}$ 的一个规范，从而它们的生成函数都是可计算的。

# Section 3: 有限集上的满射与划分

接下来的两节主要关注于所谓的“二级非递归构造”，即通过复合两个构造所得到的非递归结构。特别地，本节我们将研究**满射**与**划分**，它们分别是“集合的序列”与“集合的集合”：

$$
\mathcal{R}=\mathrm{Seq}(\mathrm{Set}_{\geq 1}(\mathcal{Z})),\quad \mathcal{S}=\mathrm{Set}(\mathrm{Set}_{\geq 1}(\mathcal{Z}))
$$

它们分别是无编号类中的整数组合与整数拆分的类比。

## 满射与划分

**定义 3.3.1** 满射（surjection）

一个函数 $f\colon A\to B$ 是**满的**，如果对任意 $b\in B$，存在 $a\in A$ 使得 $f(a)=b$.

定义 $\mathcal{R}_{n}^{(r)}$ 为所有从 $[n]$ 到 $[r]$ 的满射构成的类，其中的元素称为 $r$**-满射**。

根据定义我们知道，对于 $f\in \mathcal{R}_{n}^{(r)}$ 和 $1\leq j\leq r$，原像集 $f^{-1}[\{ j \}]$ 总是非空的，并且每个 $r$-满射都由 $r$-元组 $(f^{-1}[\{ 1 \}],\dots,f^{-1}[\{ r \}])$ 唯一地确定，如图所示：

![](3-4.png)

因此我们有如下构造：

$$
\begin{gather}
\mathcal{R}^{(r)}=\mathrm{Seq}_{r}(\mathrm{Set}_{\geq 1}(\mathcal{Z})) \implies R^{(r)}(z)=(e^{z}-1)^{r}
\end{gather}
$$

一言以蔽之：满射是非空集合的序列。利用二项式定理展开乘积并取 $z^{n}$ 项的系数，我们得到

$$
\begin{gather}
R_{n}^{(r)}=n![z^{n}] \sum_{j=0}^{r} \binom{ r }{ j } (-1)^{j} e^{(r-j)z}=\sum_{j=0}^{r} \binom{ r }{ j } (-1)^{j} (r-j)^{n}
\end{gather}
$$

接下来我们来看集合的划分，根据等价关系与划分的一一对应性，形式上我们有如下定义：

**定义 3.3.2** 划分（partition）

集合 $S$ 的一个**划分**是 $S$ 关于其上的等价关系 $\sim$ 的商集 $S / \sim$，其中的每个等价类称为一个**分块**。

定义 $\mathcal{S}_{n}^{(r)}$ 为所有 $[n]$ 的具有 $r$ 个分块的划分构成的类，其中的元素称为 $r$**-划分**。

集合划分数的计算与满射是紧密相关的。事实上，我们有构造：

$$
\begin{gather}
\mathcal{S}^{(r)}=\mathrm{Set}_{r}(\mathrm{Set}_{\geq 1}(\mathcal{Z})) \implies S^{(r)}(z)= \dfrac{1}{r!} (e^{z}-1)^{r}
\end{gather}
$$

从而满射数与划分数有基本等式

$$
\begin{gather}
S_{n}^{(r)}=\dfrac{1}{r!} R_{n}^{(r)}
\end{gather}
$$

这也可以从它们的结构上直接读出：满射是集合的序列，而划分是集合的集合，因此每个 $r$-划分都严格对应了 $r!$ 个 $r$-满射。

数列 $S_{n}^{(r)}$ 被称为（无符号）第二类 Stirling 数，或 Stirling 划分数。Knuth 引入了下面的符号，以显示其与二项式系数的相似性：

$$
\begin{gather}
S_{n}^{(r)}=\left\{ \begin{matrix} n \\ r \end{matrix} \right\} = \dfrac{1}{r!}\sum_{j=0}^{r} \binom{ r }{ j } (-1)^{j} (r-j)^{n}
\end{gather}
$$

在 Graham, Knuth, Patashnik 合著的《具体数学》（concrete mathematics）中，作者详细地讨论了两类 Stirling 数的关系，以及它们在连接离散与连续数学方面的重要作用。

现在我们考虑无限制的满射与划分类

$$
\begin{gather}
\mathcal{R}=\bigcup_{r\geq 0} \mathcal{R}^{(r)}=\mathrm{Seq}(\mathrm{Set}_{\geq 1}(\mathcal{Z})),\quad \mathcal{S}=\bigcup_{r\geq 0} \mathcal{S}^{(r)}=\mathrm{Set}(\mathrm{Set}_{\geq 1}(\mathcal{Z}))
\end{gather}
$$

它们分别有 EGF

$$
\begin{gather}
R(z)=\dfrac{1}{2-e^{z}}, \quad S(z)=\exp(e^{z}-1)
\end{gather}
$$

数列 $S_{n}=n![z^{n}]S(z)$ 称为 **Bell 数**，尽管其没有简单的显式公式，但根据其生成函数我们可以立即得到它的一个递推公式：

$$
\begin{gather}
\dfrac{\mathrm{d} }{\mathrm{d} z}S(z)=e^{z}S(z) \implies S_{n+1}=\sum_{k=0}^{n} \binom{ n }{ k } S_{k}
\end{gather}
$$

另一方面，如果我们暂时引入分析的方法，那么我们可以得到如下的级数展开式：

$$
\begin{gather}
R(z)=\dfrac{1}{2} \dfrac{1}{1-e^{z} / 2}=\dfrac{1}{2} \sum_{\ell=0}^{\infty} \dfrac{e^{\ell z}}{2^{\ell}} \\
S(z)=\dfrac{1}{e} \exp(e^{z})=\dfrac{1}{e} \sum_{\ell=0}^{\infty} \dfrac{e^{\ell z}}{\ell!}
\end{gather}
$$

取 $z^{n}$ 项的系数，即得

$$
\begin{gather}
R_{n}=\dfrac{1}{2} \sum_{\ell=0}^{\infty} \dfrac{\ell^{n}}{2^{\ell}}, \quad S_{n}=\dfrac{1}{e} \sum_{\ell=0}^{\infty} \dfrac{\ell^{n}}{\ell!}
\end{gather}
$$

使用符号计数方法的一个好处就是我们可以通过基础的规范得到一大类具有限制的构造，特别地，我们有以下定理：

**定理 3.3.3**

满足原像集的基数属于 $A\subset \mathbb{Z}_{\geq 1}$，值域的基数属于 $B\subset \mathbb{N}$ 的满射构成的类 $\mathcal{R}^{(A,B)}$ 具有 EGF

$$
\begin{gather}
R^{(A,B)}(z)=\beta(\alpha(z)),\quad \alpha(z)=\sum_{a\in A} \dfrac{z^{a}}{a!}, \beta(z)=\sum_{b\in B} z^{b}
\end{gather}
$$

满足分块的大小属于 $A\subset \mathbb{Z}_{\geq 1}$，分块的数量属于 $B\subset \mathbb{N}$ 的划分构成的类 $\mathcal{S}^{(A,B)}$ 具有 EGF

$$
\begin{gather}
S^{(A,B)}(z)=\beta(\alpha(z)),\quad \alpha(z)=\sum_{a\in A} \dfrac{z^{a}}{a!}, \beta(z)=\sum_{b\in B} \dfrac{z^{b}}{b!}
\end{gather}
$$

上述定理可以由下面的规范立即得到：

$$
\begin{gather}
\mathcal{R}^{(A,B)}=\mathrm{Seq}_{B}(\mathrm{Set}_{A}(\mathcal{Z})), \quad \mathcal{S}^{(A,B)}=\mathrm{Set}_{B}(\mathrm{Set}_{A}(\mathcal{Z}))
\end{gather}
$$

例如，分块大小 $\leq b$ 与 $>b$ 的集合划分构成的类 $\mathcal{S}^{\langle \leq b \rangle}$ 和 $\mathcal{S}^{\langle >b \rangle}$ 具有 EGF $S^{\langle \leq b \rangle}(z)=\exp(e_{b}(z)-1)$ 和 $S^{\langle >b \rangle}=\exp(e^{z}-e_{b}(z))$，其中 $e_{b}$ 是截断指数函数

$$
\begin{gather}
e_{b}(z)=1+\dfrac{z}{1!}+\dfrac{z^{2}}{2!}+\dots+\dfrac{z^{b}}{b!}
\end{gather}
$$

此外，对于分块数量和大小有奇偶性限制的划分，我们可以使用双曲函数

$$
\begin{gather}
\sinh(z)=z+\dfrac{z^{3}}{3!}+\dfrac{z^{5}}{5!}+\cdots \\
\cosh(z)=1+\dfrac{z^{2}}{2!}+\dfrac{z^{4}}{4!}+\cdots
\end{gather}
$$

以及指数函数 $\exp(z)$ 进行复合使用。

## 字符串与离散概率模型

下面我们来看字符串的编号类表示。固定一个字符表 $\mathcal{X}=\{ a_{1},\dots,a_{r} \}$，令 $\mathcal{W}$ 为由 $\mathcal{X}$ 上的字符串构成的类，则一个长度为 $n$ 的字符串 $w \in \mathcal{W}$ 就可以看成一个从 $[n]$ 到 $[r]$ 的函数（不一定是满射），这就给出

$$
\begin{gather}
\mathcal{W}=\mathrm{Seq}_{r}(\mathrm{Set}(\mathcal{Z})) \implies W(z)=(e^{z})^{r}=e^{rz}
\end{gather}
$$

从而我们按期望得到了 $W_{n}=r^{n}$. 换言之，$r$-字符表上的字符串等价于值域的基数为 $r$ 的函数，并且由一个 $r$ 次的编号积表示。

当字符串中的字符有出现次数限制时，上面的构造立即给出了以下结论：

**定理 3.3.4**

令 $\mathcal{W}^{(A)}$ 表示所有 $r$-字符表上的字符串构成的类，满足每个字符的出现次数属于 $A\subset \mathbb{N}$，则其有 EGF

$$
\begin{gather}
W^{(A)}(z)=\alpha(z)^{r}, \quad \alpha(z)=\sum_{a\in A} \dfrac{z^{a}}{a!}
\end{gather}
$$

特别地，由字符出现数 $\leq b$ 和 $>b$ 的字符串构成的类 $\mathcal{W}^{\langle \leq b \rangle}$ 和 $\mathcal{W}^{\langle >b \rangle}$ 的 EGF 由截断指数函数给出：

$$
\begin{gather}
W^{\langle \leq b \rangle }(z)=e_{b}(z)^{r}, \quad W^{\langle >b \rangle }(z)=(e^{z}-e_{b}(z))^{r}
\end{gather}
$$

在第一个公式中取 $b=1$，则它就给出了 $r$ 个物体的 $n$-排列的数量：

$$
\begin{gather}
n![z^{n}](1+z)^{r}=n! \binom{ r }{ n } =r(r-1)\cdots(r-n+1)
\end{gather}
$$

等价地，这也是从 $[n]$ 到 $[r]$ 的单射的数量。

接下来的两个例子展示了 EGF 在经典的概率论问题中的应用，即“生日悖论”与“优惠券收集问题”，它们显示了符号计数方法可以被用于分析离散概率模型，这是多元生成函数所解决的主要问题。

假设现在有一群人排成了一列，从第一个开始，每个人依次地报出自己的出生日期，那么平均需要多少人才能够找到两个有相同生日的人？这一问题被称为一个“悖论”，是因为它有一个相当反直觉的答案：平均 $n\approx 25$ 人中就有两人有相同的生日！

优惠券收集问题是生日悖论的对偶问题：还是以生日为例，平均需要多少人才能使他们的生日覆盖一年中的每一天？这一次，反直觉的点在于答案是一个相当大的数字 $n'\approx2365$，考虑到一年的天数通常只有 $365$ 天。

下面我们就来分析这两个问题，考虑有 $r$ 个字符的字符表 $\mathcal{X}$，表示一年中的 $r$ 天，那么生日问题和优惠券收集问题所要问的就是，对于一个函数 $f\colon[n]\to \mathcal{X}$，在什么时候 $f$ 不再是一个单射（即存在两个人的生日相同）？以及在什么时候 $f$ 是一个满射（每一天都是某个人的生日）？

设 $B$ 等于第一次出现非单射的 $n$ 值，则 $B$ 是一个值域为 $[2..r+1]$ 的离散随机变量。如果在 $n$ 时没有出现非单射，则 $\beta_{1},\dots,\beta_{n}$ 中的各字符是不同的，利用 $n$-排列的公式，我们就得到了事件 $\{ B>n \}$ 的概率：

$$
\begin{align}
\mathbb{P}(B>n)&=\dfrac{r(r-1)\cdots(r-n+1)}{r^{n}} \\
&=\dfrac{n!}{r^{n}} [z^{n}] (1+z)^{r} \\
&=n! [z^{n}] \left( 1+\dfrac{z}{r} \right)^{r}
\end{align}
$$

根据概率论中的基本公式，我们即得 $B$ 的期望

$$
\begin{gather}
\mathbb{E}(B)=\sum_{n=0}^{\infty} \mathbb{P}(B>n)=1+ \sum_{n=1}^{r} \dfrac{r(r-1)\cdots(r-n+1)}{r^{n}}
\end{gather}
$$

对于 $r=365$，我们计算得到 $\mathbb{E}(B)\approx 24.62$.

另一种计算上述期望的方式是通过其生成函数来得到。我们回顾一下 Gamma 函数的定义：

$$
\begin{gather}
\Gamma(n+1)=n! =\int_{0}^{\infty} t^{n} e^{-t}\mathrm{d} t
\end{gather}
$$

两边乘以 $f_{n}$ 并求和即得

$$
\begin{gather}
\sum_{n=0}^{\infty} f_{n}n! = \int_{0}^{\infty} e^{-t}\left( \sum_{n=0}^{\infty} f_{n}t^{n} \right)\mathrm{d} t=\int_{0}^{\infty} e^{-t}f(t)\mathrm{d} t
\end{gather}
$$

取 $f(z)=(1+z / r)^{r}$ 即得

$$
\begin{gather}
\mathbb{E}(B)=\int_{0}^{\infty} e^{-t} \left( 1+\dfrac{t}{r} \right)^{r} \mathrm{d} t
\end{gather}
$$

此时我们就可以使用渐近方法了，例如，使用 Laplace 方法，我们可得

$$
\begin{gather}
\mathbb{E}(B)=\sqrt{ \dfrac{\pi r}{2} } + \dfrac{2}{3} +O(r^{-1/2})
\end{gather}
$$

使用上式计算 $r=365$ 时的期望值 $24.61$ 可以精确到小数点后的第二位。

使用积分形式的期望表达式的另一个优点是，它的形式是统一的：意味着它可以被用于其它类似的问题上。例如，假设我们要计算“$b$ 个人有相同生日”第一次出现的时间，那么它的期望就是

$$
\begin{gather}
I(r,b)=\int_{0}^{\infty} e^{-t} e_{b-1}\left( \dfrac{t}{r} \right)^{r} \mathrm{d} t
\end{gather}
$$

其中 $e_{b}$ 是截断指数函数，原始的生日问题则对应于 $b=2$ 的情况。利用 Laplace 方法，我们可以类似地提取出 $I(r,b)$ 的一个渐近公式。

现在我们转到优惠券收集问题。设 $C$ 等于第一次出现满射时的 $n$ 值，则事件 $\{ C\leq n \}$ 发生等价于字符串 $\beta_{1},\dots,\beta_{n}$ 所对应的函数是满射，因此根据满射公式有

$$
\begin{align}
\mathbb{P}(C\leq n)&= \dfrac{R_{n}^{(r)}}{r^{n}} \\
&= \dfrac{n!}{r^{n}} [z^{n}] (e^{z}-1)^{r} \\
&= n![z^{n}] (e^{z/r}-1)^{r}
\end{align}
$$

于是事件 $\{ C>n \}$ 的概率就是

$$
\begin{align}
\mathbb{P}(C>n)=1-\mathbb{P}(C\leq n)=n![z^{n}](e^{z}-(e^{z/r}-1)^{r})
\end{align}
$$

再一次应用积分公式就得到

$$
\begin{gather}
\mathbb{E}(C)=\int_{0}^{\infty} (1-(1-e^{-t/r})^{r}) \mathrm{d} t
\end{gather}
$$

做换元 $v=1-e^{-t/r}$ 并积分就得到

$$
\begin{gather}
\mathbb{E}(C)=rH_{r}=r \left( 1+\dfrac{1}{2}+\dots+\dfrac{1}{r} \right)
\end{gather}
$$

其中 $H_{r}$ 称为**调和数**，根据 Euler-Maclaurin 求和可得 $H_{r}$ 的一个渐近公式：

$$
\begin{gather}
H_{r}=\ln r+\gamma+\dfrac{1}{2r}+O(r^{-2})
\end{gather}
$$

其中 $\gamma \approx 0.577216$ 是 Euler-Mascheroni 常数。从而我们有 $\mathbb{E}(C)$ 的渐近公式

$$
\begin{gather}
\mathbb{E}(C)=r\ln r+\gamma r+\dfrac{1}{2}+O(r^{-1})
\end{gather}
$$

这里的非线性项 $r\ln r$ 就解释了它的增长率。

和之前一样，符号计数方法允许我们轻松地推广至其它情形。例如，所有的优惠券（或生日）每个都被获取 $b$ 次所需的期望时间为

$$
\begin{gather}
J(r,b)=\int_{0}^{\infty} \left( 1-\left( 1-e_{b-1}\left( \dfrac{t}{r} \right)e^{-t/r} \right)^{r} \right)\mathrm{d} t
\end{gather}
$$

其中原问题就对应于 $b=1$ 的情况。

# Section 4: 置换与循环

前面我们定义了置换 $\mathcal{P}=\mathrm{Seq}(\mathcal{Z})$，但在本节中，我们将基于置换的另一种表示法，即循环表示，对置换进行研究。

**定理 3.4.1** 置换的循环分解（cycle decompositon of permutations）

任意置换都可以唯一地分解为不相交的循环的乘积。

**证明**

我们将置换 $\sigma$ 看作 $[n]$ 到其自身的双射，在 $[n]$ 上定义关系如下：如果存在 $k$ 使得 $y=\sigma^{k}(x)$，则定义 $x\sim y$. 下面我们来验证 $\sim$ 是一个等价关系。

1. $x=\sigma^{0}(x)$，故 $x\sim x$，即证自反性。
2. 如果 $y=\sigma^{k}(x)$，由于 $\sigma$ 是双射，故 $x=\sigma^{-k}(y)$，即 $y\sim x$，即证对称性。
3. 如果 $y=\sigma^{k}(x),z=\sigma^{l}(y)$，则 $z=\sigma^{k+l}(x)$，即 $x\sim z$，即证传递性。

因此 $\sim$ 是一个等价关系，$[n]$ 关于 $\sim$ 的商集就表示了将 $\sigma$ 分解为不相交的循环的乘积的方法。我们称一个等价类为一个**轨道**。

现在假设 $\sigma$ 有两种循环分解 $c_{1}c_{2}\dots c_{n}=d_{1}d_{2}\dots d_{m}$，考虑 $c_{1}$ 中的一个元素 $x$，由于循环是不相交的，故 $\sigma$ 对 $x$ 的作用完全由 $c_{1}$ 决定，即 $\sigma^{k}(x)=c_{1}^{k}(x)$. 由于 $d_{1}\dots d_{m}$ 也是 $\sigma$ 的循环分解，故必然存在一个 $d$ 使其包含 $x$，通过重新编号，我们可以假设 $x$ 在 $d_{1}$ 中，同理我们也有 $\sigma^{k}(x)=d_{1}^{k}(x)$.

由于 $x$ 在 $c_{1}$ 和 $d_{1}$ 中的轨道相同，因此必然有 $c_{1}=d_{1}$. 下面取 $c_{2}$ 中的元素 $y$ 然后重复上面的论证，我们可以证明 $c_{2}=d_{2}$，依次类推，即证循环分解的唯一性。

对于一个任意的置换，我们可以这样来得到其循环分解：首先从任意元素，比如 1 开始，不断地应用 $\sigma$ 得到 $1$ 的轨道 $1,\sigma(1),\sigma^{2}(1),\dots$，直到我们回到了 1，这就找到了一个包含 1 的循环，下面再选择一个不在循环中的元素应用上述步骤，以此类推，即得 $\sigma$ 的循环分解。这表明，置换可以写成“循环的集合”，即

$$
\begin{gather}
\mathcal{P}=\mathrm{Seq}(\mathcal{Z})\cong \mathrm{Set}(\mathrm{Cyc}(\mathcal{Z}))
\end{gather}
$$

![](3-5.png)

这一关系同样也反映在生成函数的关系上：

$$
\begin{gather}
P(z)=\dfrac{1}{1-z}=\exp\left( \ln \dfrac{1}{1-z} \right)
\end{gather}
$$

指数函数和对数函数相互为逆这一性质，不过是置换能唯一分解为循环这一组合事实的分析学反映！

和之前一样，我们可以对置换的循环加上不同的限制，得到：

**定理 3.4.2**

满足循环长度属于 $A\subset \mathbb{Z}_{\geq 1}$，循环数量属于 $B\subset \mathbb{N}$ 的置换构成的类 $\mathcal{P}^{(A,B)}$ 具有 EGF

$$
\begin{gather}
P^{(A,B)}(z)=\beta(\alpha(z)), \quad \alpha(z)=\sum_{a\in A} \dfrac{z^{a}}{a}, \beta(z)=\sum_{b\in B} \dfrac{z^{b}}{b!}
\end{gather}
$$

特别地，含有 $r$ 个循环的置换构成的类 $\mathcal{P}^{(r)}$ 有构造

$$
\begin{gather}
\mathcal{P}^{(r)}=\mathrm{Set}_{r}(\mathrm{Cyc}(\mathcal{Z})) \implies P^{(r)}(z)=\dfrac{1}{r!} \left( \ln \dfrac{1}{1-z} \right)^{r}
\end{gather}
$$

其系数

$$
\begin{gather}
P_{n}^{(r)}=\dfrac{n!}{r!}[z^{n}] \left( \ln \dfrac{1}{1-z} \right)^{r}
\end{gather}
$$

是组合学中的一个基本数列，它被称为（无符号）**第一类 Stirling 数**，或称为 **Stirling 循环数**，有时记作 $\left[ \begin{matrix} n \\r \end{matrix} \right]$.

上面的公式不太适合计算 $P_{n}^{(r)}$ 的精确值，这里，我们暂时地借用多元生成函数中的思想，引入二元生成函数：

$$
\begin{align}
P(z,u)&=\sum_{r=0}^{\infty} P^{(r)}(z)u^{r} \\
&= \sum_{r=0}^{\infty} \dfrac{u^{r}}{r!} \left( \ln \dfrac{1}{1-z} \right)^{r} \\
&= \exp\left( u \ln \dfrac{1}{1-z} \right) \\
&=(1-z)^{-u}
\end{align}
$$

此时再取 $z^{n}$ 项的系数即得

$$
\begin{gather}
[z^{n}](1-z)^{-u}=(-1)^{n} \binom{ -u }{ n } =u(u+1)\cdots(u+n-1)
\end{gather}
$$

换言之，我们有简单的公式

$$
\begin{gather}
\sum_{k=0}^{n} \left[ \begin{matrix} n \\ k \end{matrix} \right] u^{k} = u(u+1)\cdots(u+n-1)
\end{gather}
$$

编码了所有上指标为 $n$ 的 Stirling 循环数。由此我们可以轻松得到一个随机置换的循环数量（对 $u$ 求导并设其为 1）

$$
\begin{gather}
\mu_{n}= \dfrac{1}{n!} \sum_{k=0}^{n} k \left[ \begin{matrix} n \\ k \end{matrix} \right]=H_{n}\sim \ln n
\end{gather}
$$

其中 $H_{n}$ 是调和数。这表明，置换的平均循环数随着置换大小增大呈现对数增长。

另一方面，我们可以对循环的长度进行限制。我们通常使用两类限制，即不存在长循环（如对合）和不存在短循环（如错排），下面我们分别给出两者的构造。

我们称置换 $\sigma$ 是一个**对合**，如果 $\sigma^{2}=\mathrm{id}$，其中 $\mathrm{id}$ 是恒等置换。显然，一个对合只有长度为 $1$ 和 $2$ 的循环，因此我们有

$$
\begin{gather}
\mathcal{I}=\mathrm{Set}(\mathrm{Cyc}_{1,2}(\mathcal{Z})) \implies I(z)=\exp\left( z+\dfrac{z^{2}}{2} \right)
\end{gather}
$$

其 EGF 足够简单，我们可以从中直接提取出显式的系数：

$$
\begin{gather}
I_{n}=\sum_{k=0}^{\lfloor n / 2 \rfloor } \dfrac{n!}{(n-2k)! 2^{k} k!}
\end{gather}
$$

一个类似的构造是**配对**，它是不包含不动点（长度为 1 的循环）的对合：

$$
\begin{gather}
\mathcal{J}=\mathrm{Set}(\mathrm{Cyc}_{2}(\mathcal{Z})) \implies J(z)=\exp \dfrac{z^{2}}{2}, \quad J_{2n}=1\cdot 3\cdot 5\cdots (2n-1)
\end{gather}
$$

更广义的情况下，对于循环长度 $\leq r$ 的置换，有 EGF

$$
\begin{gather}
B^{(r)}(z)=\exp\left( \sum_{j=0}^{r} \dfrac{z^{j}}{j} \right)
\end{gather}
$$

其系数 $B_{n}^{(r)}$ 满足递归方程

$$
\begin{gather}
(n+1)B_{n+1}^{(r)}=(n+1)B_{n}^{(r)}-B_{n-r}^{(r)}
\end{gather}
$$

我们称一个置换 $\sigma$ 是一个**错排**，如果 $\sigma$ 没有不动点。换言之，错排 $\sigma$ 只有长度 $>1$ 的循环。同样我们可以定义 $r$**-错排**为只有长度 $>r$ 的循环的置换，其构造为

$$
\begin{gather}
\mathcal{D}^{(r)}=\mathrm{Set}(\mathrm{Cyc}_{>r}(\mathcal{Z})) \implies D^{(r)}(z)=\dfrac{1}{1-z}\exp\left( -\sum_{j=1}^{r} \dfrac{z^{j}}{j} \right)
\end{gather}
$$

对于 $r=1$ 的错排，直接计算即可得到

$$
\begin{gather}
\dfrac{D_{n}^{(1)}}{n!}=1- \dfrac{1}{1!}+\dfrac{1}{2!}-\dots+\dfrac{(-1)^{n}}{n!}
\end{gather}
$$

一个 $\dfrac{1}{e}$ 的截断级数。它是以下问题的解：$n$ 个人进入一家剧院，将他们的帽子挂在衣帽间的架子上，每个人离开时随机拿走一顶帽子，那么所有人都拿不到他们自己的帽子的概率就近似地等于 $\dfrac{1}{e}\approx 37\%$. 上述问题的另一种解法是通过容斥原理，我们将在多元生成函数章节详细地讨论这种方法。

我们还可以对循环长度的奇偶性进行限制，其对应的 EGF 分别为

$$
\begin{gather}
E(z)=\exp\left( \dfrac{1}{2}\ln \dfrac{1}{1-z^{2}} \right)=\dfrac{1}{\sqrt{ 1-z^{2} }} \\
O(z)=\exp\left( \dfrac{1}{2}\ln \dfrac{1+z}{1-z} \right)=\sqrt{ \dfrac{1+z}{1-z} }
\end{gather}
$$

分别对应于只包含偶数长度循环的置换（$E(z)$）和只包含奇数长度循环的置换（$O(z)$）。其中偶数与奇数长度的循环构造由对数函数

$$
\begin{gather}
\dfrac{1}{2}\ln \dfrac{1}{1-z^{2}}=\dfrac{1}{2}\left( \ln \dfrac{1}{1-z} + \ln \dfrac{1}{1+z} \right)=\sum_{k=1}^{\infty} \dfrac{z^{2k}}{2k} \\
\dfrac{1}{2}\ln \dfrac{1+z}{1-z}= \dfrac{1}{2}\left( \ln \dfrac{1}{1-z} - \ln \dfrac{1}{1+z} \right)=\sum_{k=0}^{\infty} \dfrac{z^{2k+1}}{2k+1}
\end{gather}
$$

给出。另一方面，利用等式

$$
\begin{gather}
\cosh(z)=\dfrac{e^{z}+e^{-z}}{2}, \quad \sinh(z)=\dfrac{e^{z}-e^{-z}}{2}
\end{gather}
$$

我们就可以得到包含偶数个循环与包含奇数个循环的置换的 EGF.