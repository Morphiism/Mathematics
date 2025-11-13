本系列的主题是**解析组合学**（Analytic Combinatorics）。**组合学**研究的内容是具体且离散（可数）的结构：整数、排列、图、树等等。而**解析**指代的是分析学，也就是对连续函数的研究，具体来说，我们所用到的理论是复分析与渐近分析。

你可能会有疑问，为什么这两个看似不相关的领域能够结合在一起？但事实上，离散结构与复函数的联系早在十九世纪之前就为数学界所知，其中最为著名的就是 Riemann 猜想：素数的分布性质被精确地编码于特定的复函数（即 Riemann $\zeta$ 函数）的零点中，通过分析函数的零点，我们可以得到比直接分析整数本身更为深刻的结果，这也直接催生了一个新的数学领域，即**解析数论**（Analytic Number Theory）。

在解析组合学中，**生成函数**（generating function）是最为核心的对象，我们以一个典型例子来进行展示。集合 $[n]=\{ 1,2,\dots,n \}$ 的一个排列可以写成 $w_{1}w_{2}\dots w_{n}$，其中 $w_{j}$ 表示移动到第 $j$ 个位置的元素，下面我们考虑这样一种排列，它满足

$$
\begin{gather}
w_{1}<w_{2}>w_{3}<w_{4}>\cdots
\end{gather}
$$

称为**交错排列**。假设 $n$ 是一个奇数（从而 $w_{n-1}>w_{n}$），我们想知道：对于一般的 $n=2m+1$，有多少 $[n]$ 的排列是交错的？

通过枚举，我们可得前几个数字是 $1,2,16,272,7936$，第一眼看过去，似乎并没有什么明显的规律，直到我们毫无理由地给出正切函数 $\tan z$ 并考察它的 Taylor 展开式：

$$
\begin{gather}
\tan z=1 \dfrac{z}{1!}+2 \dfrac{z^{3}}{3!}+16 \dfrac{z^{5}}{5!}+272 \dfrac{z^{7}}{7!}+7936 \dfrac{z^{9}}{9!}+O(z^{11})
\end{gather}
$$

我们注意到问题的答案就放置在 $\tan z$ 的幂级数展开式的系数上，因此，$\tan z$ 就称为该数值序列的（指数）生成函数。解析组合学的理论指出，这种关联并非是一种巧合，利用其中的技术，我们可以补全这一关联中缺失的部分：设所有交错排列构成的类是 $\mathcal{A}$，$A(z)=\sum a_{n}z^{n} / n!$ 是其生成函数，在每个交错排列中，其最高点的左右两部分都同构于一个较小的交错排列，于是我们有

$$
\begin{gather}
\mathcal{A}\cong \{ 1 \} \cup (\mathcal{A},\max,\mathcal{A})
\end{gather}
$$

这一关于类的等式可以直接转换为关于生成函数的函数方程：

$$
\begin{gather}
A(z)=z+\int_{0}^{z} A(w)^{2} \mathrm{d} w
\end{gather}
$$

其中并集对应于加法，二元组对应于平方，而最大值则对应于积分。对上式求导并解这个常规的微分方程即得 $A(z)=\tan z$. 这种集合构造与生成函数的对应是解析组合学的核心。

在本系列的前半部分，我们将展示何种构造是可行的，并给出其对应的生成函数。注意，在这一部分中，我们不考虑幂级数的收敛性问题，而仅仅把生成函数看作是一种代数对象（形式幂级数），并且其加法、乘法、微分和积分都依照其代数定义来进行。

在后半部分，我们将引入拓扑，并考虑生成函数的分析性质。这种转换基于这样一个原理：在幂级数的收敛半径内，形式幂级数的运算与幂级数的相应运算是一致的（事实上，形式幂级数的运算就是根据此定义的）。我们将展示如何通过分析函数在复平面上的极点来给出其幂级数系数的渐近公式。

# Section 1: 组合类与生成函数

在常见的组合问题中，我们通常被给定一类满足特定性质的对象，并且通常我们会按照一个对象中的“部分”的数量为其分类（例如 $[n]$ 上的排列都具有 $n$ 个部分，一个图的部分数就是它的顶点数）。一个自然的问题，就是要找到具有 $n$ 个部分的对象的个数，由此我们给出以下定义。

**定义 1.1.1** 组合类（combinatorial class）

一个**组合类**是二元组 $(\mathcal{A},\lvert \cdot \rvert)$，其中 $\mathcal{A}$ 是一个至多可数的集合，函数 $\lvert \cdot \rvert\colon \mathcal{A}\to \mathbb{N}$ 满足对任意 $n \in \mathbb{N}$，集合 $\{ a \in \mathcal{A} \mid |a|=n \}$ 是有限的。

$|a|$ 通常称为 $a$ 的“大小”，我们将具有同一大小的对象放在一起，记作 $\mathcal{A}_{n}=\{ a \in \mathcal{A} \mid |a|=n \}$，根据定义，该集合的元素个数 $A_{n}$ 是有限的。

**定义 1.1.2** 计数序列（counting sequence）

一个组合类 $\mathcal{A}$ 的**计数序列**就是序列 $(A_{n})_{n=0}^{\infty}$，其中 $A_{n}=|\mathcal{A}_{n}|$ 是大小为 $n$ 的对象的个数。

现在我们给出几个常用的组合类的例子。

**例 1.1.3** 字符串（word）

给定一个**字符表** $\mathcal{A}=\{ 0,1 \}$，所有由 $\mathcal{A}$ 中元素组成的字符串构成的组合类为

$$
\begin{gather}
\mathcal{W}=\{ \varepsilon,0,1,00,01,10,11,000,001,\dots \}
\end{gather}
$$

其中 $w \in \mathcal{W}$ 的大小定义为 $w$ 中字符的数量，$\varepsilon$ 是空字符串。显然其计数序列 $W_{n}=2^{n}$.

**例 1.1.4** 置换（permutation）

一个大小为 $n$ 的**置换** $\sigma$ 是 $[n]$ 到其自身的双射，我们可以用一个矩阵来描述它：

$$
\begin{gather}
\begin{pmatrix}
1 & 2 & \cdots & n \\
\sigma_{1} & \sigma_{2} & \cdots & \sigma_{n}
\end{pmatrix}
\end{gather}
$$

或者我们可以把它简写为一个字符串 $\sigma_{1}\sigma_{2}\dots\sigma_{n}$（此时我们称其为 $[n]$ 的一个**排列**）。所有置换构成的组合类为

$$
\begin{gather}
\mathcal{P}=\{ \varepsilon,1,12,21,123,132,213,231,312,321,1234,\dots \}
\end{gather}
$$

一个众所周知的事实就是置换的计数序列由阶乘给出：

$$
\begin{gather}
P_{n}=n! =n(n-1)\cdots 2 \cdot 1
\end{gather}
$$

**例 1.1.5** 三角划分（triangulation）

将一个多边形划分为互不重叠的三角形的方法称为**三角划分**，如图所示：

![](1-1.png)

所有三角划分构成的组合类记作 $\mathcal{T}$，其中一个三角划分的大小定义为其中三角形的个数，也就是 $n+2$ 边形的划分数。我们定义 $T_{0}=1$，则计数序列的前几项为 $1,1,2,5,14,42$，并且后面我们会证明其通项公式为

$$
\begin{gather}
T_{n}=\dfrac{1}{n+1} \binom{ 2n }{ n } = \dfrac{(2n)!}{(n+1)!n!}
\end{gather}
$$

这一序列在组合学中极为常见，被称为 **Catalan 数**，通常记为 $C_{n}$.

既然我们的目标是确定一个组合类的计数序列，因此如果两个类有同样的计数序列但其元素不同，那么对于我们来说它们是没有区别的，由此我们给出以下定义：

**定义 1.1.6** 同构（isomorphism）

两个组合类 $\mathcal{A}$ 和 $\mathcal{B}$ 称为**同构的**，记作 $\mathcal{A}\cong\mathcal{B}$，如果存在保持大小的双射 $\phi\colon \mathcal{A}\to \mathcal{B}$，该映射称为一个**同构**。等价地，$\mathcal{A}\cong\mathcal{B}$ 当且仅当它们具有相同的计数序列。

例如，字母表 $\{ 0,1 \}$ 和字母表 $\{ a,b \}$ 对应的字符串类是同构的，只要其上的大小函数都给出字符的数量即可。

接下来我们给出本章的最核心的定义。

**定义 1.1.7** 生成函数（ordinary generating function）

一个序列 $(A_{n})_{n=0}^{\infty}$ 的**生成函数**是形式幂级数

$$
\begin{gather}
A(z)=\sum_{n=0}^{\infty} A_{n}z^{n}
\end{gather}
$$

一个组合类的生成函数是其计数序列的生成函数。等价地，组合类 $\mathcal{A}$ 的生成函数定义为

$$
\begin{gather}
A(z)=\sum_{\alpha \in \mathcal{A}} z^{|\alpha|}
\end{gather}
$$

并称变量 $z$ 在生成函数中指示了大小。

---

这里我们简要地说明一下形式幂级数。给定一个域 $K$（通常取为 $\mathbb{Q},\mathbb{R},\mathbb{C}$），以 $K$ 中元素为系数的形式幂级数构成的集合记作 $K[[z]]$，它与 $K^{\mathbb{N}}$，即 $K$ 中的无限序列构成的集合一一对应。给定形式幂级数 $f(z),g(z)$，它们相等当且仅当其所有系数相等，并且我们可以形式地定义加法和乘法：

$$
\begin{gather}
f(z)+g(z)=\sum_{n=0}^{\infty} (f_{n}+g_{n})z^{n} \\
f(z)g(z)=\sum_{n=0}^{\infty} \left( \sum_{k=0}^{n} f_{k}g_{n-k} \right) z^{n}
\end{gather}
$$

以及微分和积分运算：

$$
\begin{gather}
\dfrac{\mathrm{d} }{\mathrm{d} z} f(z)=\sum_{n=0}^{\infty} (n+1)f_{n+1} z^{n} \\
\int_{0}^{z} f(w)\mathrm{d} w=\sum_{n=0}^{\infty} f_{n} \dfrac{z^{n+1}}{n+1}
\end{gather}
$$

从而所有关于形式幂级数的微分方程都可以转换为关于系数的代数方程，这就避免了 $K$ 上的拓扑的引入。不过，在 $K[[z]]$ 上我们可以定义一种新的拓扑，称为**形式拓扑**，其中 $f,g$ 被看作是“接近的”，如果它们有足够多的系数是相同的。

具体来说，定义 $\mathrm{deg}\ f$ 为满足 $f_{n}\neq 0$ 的最小 $n$，并且定义

$$
\begin{gather}
d(f,g)=2^{-\mathrm{deg}(f-g)}
\end{gather}
$$

我们可以证明，$d$ 是 $K[[z]]$ 上的完备度量，于是幂级数列 $(f^{(k)})$ 按形式拓扑收敛于 $f$，当且仅当每个 $(f_{n}^{(k)})_{k=0}^{\infty}$ 最终都是常数 $f_{n}$，记作 $\lim_{ k \to \infty }f^{(k)}=f$. 由此，我们就可以在 $K[[z]]$ 上定义无限和 $\sum f^{(k)}$ 以及无限乘积 $\prod(1+f^{(k)})$，只要 $\mathrm{deg}\ f^{(k)}\to \infty$ 即可。

---

现在我们回到组合类的生成函数上来，下面我们给出一个常用的记号。

**定义 1.1.8** 系数提取（coefficient extraction）

设 $f(z)=\sum_{n=0}^{\infty}f_{n}z^{n}$ 是一个形式幂级数，则定义

$$
\begin{gather}
[z^{n}]f(z)=f_{n}
\end{gather}
$$

为 $f(z)$ 中 $z^{n}$ 项的系数。

与生成函数相关的另一个概念则是“构造”。对于一个组合类，我们通常可以将其拆分为几个较小的组成部分（例如字符串类 $\mathcal{W}$ 可以由字符表 $\mathcal{A}$ 通过构成序列的方式生成），而我们关注的，就是可以直接转换为生成函数之间的关系的构造，这引出了以下定义：

**定义 1.1.9** 可容许的构造（admissible construction）

设 $\Phi$ 是一个 $m$ 元类函数（构造），即，对任意组合类 $\mathcal{B}^{(1)},\dots,\mathcal{B}^{(m)}$，存在唯一的组合类 $\mathcal{A}$ 使得

$$
\begin{gather}
\mathcal{A}=\Phi(\mathcal{B}^{(1)},\dots,\mathcal{B}^{(m)})
\end{gather}
$$

称 $\Phi$ 是**可容许的**，如果 $\mathcal{A}$ 的计数序列 $(A_{n})$ 仅和 $\mathcal{B}^{(1)},\dots,\mathcal{B}^{(m)}$ 的计数序列 $(B_{n}^{(1)}),\dots,(B_{n}^{(m)})$ 有关。

例如，如果 $\mathcal{A}$ 和 $\mathcal{B}$ 是不相交的，那么 $\mathcal{C}=\mathcal{A}\cup \mathcal{B}$ 就是一个可容许的构造，这是因为其计数序列 $C_{n}$，只和 $A_{n},B_{n}$ 有关（$C_{n}=A_{n}+B_{n}$），从而满足定义。反之，当 $\mathcal{A}\cap \mathcal{B}\neq \varnothing$ 时，$\cup$ 就不是可容许的了，因为 $C_{n}=A_{n}+B_{n}-|\mathcal{A}_{n}\cap \mathcal{B}_{n}|$，其中 $C_{n}$ 还与 $\mathcal{A},\mathcal{B}$ 的内部结构有关。

对于一个可容许的构造，存在一个良定的函数 $\Psi$ 将其生成函数联系起来：

$$
\begin{gather}
A(z)=\Psi(B^{(1)}(z),\dots,B^{(m)}(z))
\end{gather}
$$

这种对应关系是被称为“符号计数方法”的基本原理。

# Section 2: 可容许的构造

下面我们来介绍最基本的几种可容许构造，据此，我们可以给出**可构造类**的范围。它们的生成函数也将一并给出。

**定义 1.2.1** 单位类（neutral class），原子类（atomic class）

一个**单位类**是组合类 $\mathcal{E}=\{ \varepsilon \}$，其中 $|\varepsilon|=0$. 一个**原子类**是组合类 $\mathcal{Z}=\{ 1 \}$，其中 $|1|=1$.

显然，所有的单位类以及所有的原子类都是同构的，并且有生成函数

$$
\begin{gather}
E(z)=1, \quad Z(z)=z
\end{gather}
$$

单位类和原子类将作为我们构造其它类的起点。

**定义 1.2.2** 直积（Cartesian product）

两个组合类 $\mathcal{B},\mathcal{C}$ 的**直积**定义为

$$
\begin{gather}
\mathcal{B}\times \mathcal{C}=\{ (\beta,\gamma) \mid \beta \in \mathcal{B},\gamma \in \mathcal{C} \}
\end{gather}
$$

且对于 $\alpha=(\beta,\gamma)\in \mathcal{A}= \mathcal{B}\times \mathcal{C}$ 有

$$
\begin{gather}
|\alpha|_{\mathcal{A}}=|\beta|_{\mathcal{B}}+|\gamma|_{\mathcal{C}}
\end{gather}
$$

根据该定义，我们立即得到

$$
\begin{gather}
\mathcal{A}\cong\mathcal{E}\times \mathcal{A}\cong\mathcal{A}\times \mathcal{E}
\end{gather}
$$

这就是 $\mathcal{E}$ 被称为“单位”的原因：它是类的直积的单位元。此外，我们也可以看出其可容许性：$\mathcal{A}_{n}$ 由大小相加为 $n$ 的元素对组成，因此有

$$
\begin{gather}
A_{n}=\sum_{k=0}^{n} B_{k}C_{n-k}
\end{gather}
$$

从而类的直积转换为了生成函数的乘积：

$$
\begin{gather}
A(z)=\sum_{n=0}^{\infty} \left( \sum_{k=0}^{n} B_{k}C_{n-k} \right)z^{n}=B(z)C(z)
\end{gather}
$$

**定义 1.2.3** 无交并（disjoint union）

两个组合类 $\mathcal{B},\mathcal{C}$ 的**无交并**，记作 $\mathcal{B}+\mathcal{C}$，定义为同构于以下类的任意组合类：

$$
\begin{gather}
\mathcal{A}=(\mathcal{E}_{1}\times \mathcal{B})\cup(\mathcal{E}_{2}\times \mathcal{C})
\end{gather}
$$

其中 $\mathcal{E}_{1}\neq \mathcal{E}_{2}$ 是单位类，且对 $\alpha \in \mathcal{A}$ 有

$$
\begin{gather}
|\alpha|_{\mathcal{A}}=\begin{cases}
|\alpha|_{\mathcal{B}} & ,\alpha \in \mathcal{B} \\
|\alpha|_{\mathcal{C}} & ,\alpha \in \mathcal{C}
\end{cases}
\end{gather}
$$

需要注意的是，尽管上面的定义不是那么良定，但“在同构下唯一”是我们所能得到的最好结果了，任何进一步的限制都会破坏这种结构的自然性（详细的讨论请参考范畴论对此的解释），不过，对于计数问题而言，这个定义已经足够了，我们可以直接写出其对应的关系：

$$
\begin{gather}
A_{n}=B_{n}+C_{n} \implies A(z)=B(z)+C(z)
\end{gather}
$$

无交并和直积，对应于生成函数的加法和乘法，是组合类的基本构造。接下来，我们给出基于加法和乘法的上层构造。

**定义 1.2.4** 序列构造（sequence construction）

设 $\mathcal{B}$ 是一个组合类，则其**序列构造**定义为

$$
\begin{gather}
\mathrm{Seq}(\mathcal{B})=\mathcal{E}+\mathcal{B}+(\mathcal{B}\times \mathcal{B})+(\mathcal{B}\times \mathcal{B}\times \mathcal{B})+\cdots
\end{gather}
$$

其中 $\alpha=(\beta_{1},\dots,\beta_{m})\in \mathrm{Seq}(\mathcal{B})$ 的大小定义为

$$
\begin{gather}
|\alpha|=\sum_{j=1}^{m} |\beta_{j}|
\end{gather}
$$

字符串类 $\mathcal{W}$ 的构造由此而来，即 $\mathcal{W}=\mathrm{Seq}(\mathcal{A})$.

**定义 1.2.5** 循环构造（cycle construction）

设 $\mathcal{B}$ 是一个组合类，则其**循环构造**定义为

$$
\begin{gather}
\mathrm{Cyc}(\mathcal{B})=(\mathrm{Seq}(\mathcal{B})\setminus \mathcal{E}) / \mathbf{S}
\end{gather}
$$

其中等价关系 $\mathbf{S}$ 定义为 $(\beta_{1},\dots,\beta_{m})\mathbf{S}(\beta_{1}',\dots,\beta_{m}')$ 当且仅当存在 $d$ 使得对任意 $j$ 有

$$
\begin{gather}
\beta'_{j}=\beta_{1+(j-1+d) \bmod m}
\end{gather}
$$

换言之，两个元组等价当且仅当其中一个向右轮转几次可以与另一个重合。例如 $\{ 1234,4123,3412,2341 \}$ 就是轮转对称下的一个等价类。$\mathrm{Cyc}(\mathcal{B})$ 就是 $\mathcal{B}$ 的序列中在轮换对称下不同的对象构成的类。

**定义 1.2.6** 多重集构造（multiset construction）

设 $\mathcal{B}$ 是一个组合类，则其**多重集构造**定义为

$$
\begin{gather}
\mathrm{MSet}(\mathcal{B})=\mathrm{Seq}(\mathcal{B}) / \mathbf{\mathbf{R}}
\end{gather}
$$

其中等价关系 $\mathbf{R}$ 定义为 $(\beta_{1},\dots,\beta_{m})\mathbf{R}(\beta_{1}',\dots,\beta_{m}')$ 当且仅当存在 $[m]$ 上的置换 $\sigma$ 使得对任意 $j$ 有

$$
\begin{gather}
\beta_{j}'=\beta_{\sigma(j)}
\end{gather}
$$

在组合学中，多重集是一种常见的对象，它可以被描述为是一种与集合类似的对象，但允许元素在其中多次出现。从序列的角度来看，一个多重集就是一个失去了有序性的元组，从而对其中的元素进行任意的置换都不会改变多重集本身，这一点被等价关系 $\mathbf{R}$ 完整地表述了出来。

**定义 1.2.7** 幂集构造（powerset construction）

设 $\mathcal{B}$ 是一个组合类，则其**幂集构造** $\mathrm{PSet}(\mathcal{B})$ 定义为 $\mathrm{MSet}(\mathcal{B})$ 的一个子集，由所有没有重复元素的多重集组成。

换言之，$\mathrm{PSet}(\mathcal{B})$ 由 $\mathcal{B}$ 所有有限子集构成。

上述四个构造的可容许性与生成函数由以下定理给出：

**定理 1.2.8** 可容许性定理（无编号类）

组合类的无交并、直积、序列、多重集、幂集和循环构造都是可容许的，其对应的生成函数如下：

$$
\begin{align}
\mathcal{A}=\mathcal{B}+\mathcal{C} &\implies A(z)= B(z)+C(z)  \\
\mathcal{A}=\mathcal{B}\times \mathcal{C} &\implies A(z)=B(z)C(z)  \\
\mathcal{A}=\mathrm{Seq}(\mathcal{B}) &\implies A(z)=\dfrac{1}{1-B(z)}  \\
\mathcal{A}=\mathrm{PSet}(\mathcal{B}) &\implies A(z)=\prod_{n=1}^{\infty} (1+z^{n})^{B_{n}}=\exp\left( \sum_{k=1}^{\infty} \dfrac{(-1)^{k-1}}{k}B(z^{k}) \right) \\
\mathcal{A}=\mathrm{MSet}(\mathcal{B}) &\implies A(z)=\prod_{n=1}^{\infty} (1-z^{n})^{-B_{n}}=\exp\left( \sum_{k=1}^{\infty} \dfrac{1}{k}B(z^{k}) \right) \\
\mathcal{A}=\mathrm{Cyc}(\mathcal{B}) &\implies A(z)=\sum_{k=1}^{\infty} \dfrac{\varphi(k)}{k} \ln \dfrac{1}{1-B(z^{k})}
\end{align}
$$

其中对于序列、多重集、幂集、循环构造有 $\mathcal{B}_{0}=\varnothing$，$\varphi(n)$ 是 Euler $\varphi$ 函数，表示小于等于 $n$ 且与 $n$ 互素的正整数的个数。

**证明**

我们已经证明了无交并和直积的可容许性。对于序列构造，我们有

$$
\begin{gather}
A(z)=1+B(z)+B(z)^{2}+B(z)^{3}+\cdots= \dfrac{1}{1-B(z)}
\end{gather}
$$

由于 $B_{0}=0$，故当 $k>n$ 时，$B(z)^{k}$ 中的最小项次数大于 $n$，因此级数在形式拓扑中收敛，即证。

对于幂集构造，我们首先设 $\mathcal{B}$ 是有限的，于是我们就有以下乘积式成立：

$$
\begin{gather}
\mathrm{PSet}(\mathcal{B})\cong \prod_{\beta \in \mathcal{B}} (\{ \varepsilon \}+\{ \beta \})
\end{gather}
$$

其中 $\varepsilon$ 的大小为 $0$，从而就有

$$
\begin{align}
A(z) &= \prod_{\beta \in \mathcal{B}} (1+z^{|\beta|})=\prod_{n=1}^{\infty} (1+z^{n})^{B_{n}} \\
&= \exp \left( \sum_{n=1}^{\infty} B_{n} \ln (1+z^{n}) \right) \\
&= \exp \left( \sum_{n=1}^{\infty} B_{n} \sum_{k=1}^{\infty} (-1)^{k-1} \dfrac{z^{nk}}{k} \right) \\
&= \exp \left( \sum_{k=1}^{\infty} \dfrac{(-1)^{k-1}}{k} B(z^{k}) \right)
\end{align}
$$

下面设 $\mathcal{B}$ 是可数的，我们注意到每个 $\mathcal{A}_{n}$ 都只和满足 $j\leq n$ 的 $\mathcal{B}_{j}$ 有关，从而我们可以应用有限集的结论。具体来说，令 $\mathcal{B}^{(\leq m)}=\sum_{j=1}^{m}\mathcal{B}_{j}$，且 $\mathcal{A}^{(\leq m)}=\mathrm{PSet}(\mathcal{B}^{(\leq m)})$，则我们有

$$
\begin{gather}
A(z)=A^{(\leq m)}(z)+O(z^{m+1}),\quad B(z)=B^{(\leq m)}(z)+O(z^{m+1})
\end{gather}
$$

另一边，由于 $A^{(\leq m)}(z)$ 和 $B^{(\leq m)}(z)$ 由上面的指数关系连接，令 $m\to \infty$，就得到了所要的极限

$$
\begin{gather}
A(z)=\exp\left( \sum_{k=1}^{\infty} \dfrac{(-1)^{k-1}}{k}B(z^{k}) \right)
\end{gather}
$$

接下来我们来看多重集构造。对于一个多重集，我们总可以对其元素进行排列，使得它以若干个 $\beta_{1}$ 开始，接下来是若干个 $\beta_{2}$，以此类推，于是对于有限集 $\mathcal{B}$，我们就有如下乘积式：

$$
\begin{gather}
\mathrm{MSet}(\mathcal{B})\cong \prod_{\beta \in \mathcal{B}} \mathrm{Seq}(\{ \beta \})
\end{gather}
$$

它转化为生成函数的关系

$$
\begin{align}
A(z) &= \prod_{\beta \in \mathcal{B}} (1-z^{|\beta|})^{-1}=\prod_{n=1}^{\infty} (1-z^{n})^{-B_{n}} \\
&= \exp \left( \sum_{n=1}^{\infty} -B_{n} \ln(1-z^{n}) \right) \\
&= \exp \left( \sum_{n=1}^{\infty} B_{n} \sum_{k=1}^{\infty} \dfrac{z^{nk}}{k} \right) \\
&= \exp \left( \sum_{k=1}^{\infty} \dfrac{1}{k}B(z^{k}) \right)
\end{align}
$$

对于可数集，仿照幂集构造进行一个类似的极限论述即可证明。最后，对于循环构造，我们将在后续的章节中进行证明，因为它的证明依赖于我们后续将要讲解的多元生成函数。

为增加上述构造的表达能力，我们还可以在其上增加一些限制。设 $\mathscr{C}$ 是 $\mathrm{Seq},\mathrm{MSet},\mathrm{PSet},\mathrm{Cyc}$ 中的任意一个，$\Omega$ 是 $\mathbb{N}$ 的一个子集，则 $\mathscr{C}_{\Omega}(\mathcal{B})$ 就表示由 $\mathscr{C}$ 构造的组合类，其元素组成部分的数量在 $\Omega$ 中。例如

$$
\begin{gather}
\mathrm{Seq}_{k}(\mathcal{B}) ,\quad \mathrm{Seq}_{>k}(\mathcal{B}), \quad \mathrm{Seq}_{1..k}(\mathcal{B})
\end{gather}
$$

分别表示长度等于 $k$、大于 $k$、在 $[1..k]=[1,k]\cap \mathbb{Z}$ 区间内的序列构成的类。其生成函数分别为

$$
\begin{gather}
A^{(k)}(z)=B(z)^{k}, \quad A^{(>k)}(z)=\sum_{n>k} B(z)^{n}, \quad A^{(1..k)}(z)=\sum_{n=1}^{k} B(z)^{n}
\end{gather}
$$

对于 $\mathrm{MSet}_{k}(\mathcal{B})=\mathrm{Seq}_{k}(\mathcal{B}) / \mathbf{R}$ 以及其它构造，其生成函数更为复杂，我们将在后续章节进行研究。

现在我们就有了一个解决组合问题的框架：对于一个组合问题，我们只需找到一种方法，使得我们感兴趣的组合类可以由单位类、原子类以及可容许构造的复合来进行表示，从而根据可容许性定理，我们可以立即得到我们所要求的计数序列的生成函数，而从幂级数中提取系数是一项非常常规的操作。下面我们以一个例子来说明这一点。

回顾一下例 1.1.3，字符串类 $\mathcal{W}$ 可以通过以下方式构造出来：

$$
\begin{gather}
\mathcal{W}=\mathrm{Seq}(\mathcal{A}), \quad \mathcal{A}=\{ 0,1 \}\cong \mathcal{Z}+\mathcal{Z}
\end{gather}
$$

从而我们立即得到

$$
\begin{gather}
W(z)= \dfrac{1}{1-2z}=\sum_{n=0}^{\infty} 2^{n}z^{n}, \quad W_{n}=2^{n}
\end{gather}
$$

注意，在上述构造中，我们仅使用了单位类、原子类和基本构造的复合来表示一个组合类，这样的构造称为是**迭代的**或**非递归的**，这些构造的生成函数可以被显式地给出。

与之相对的就是**递归的**构造了，这是那些在构造式中包含自身的构造，其中最典型的就是树的结构。在图论中，**树**被定义为连通且无环的无向图，通常其中有一个顶点被指定为它的“根”。计算机科学家通常会研究一种特殊的树，即**平面有根树**，它们可以被嵌入平面上，从而子节点的排列被视为是有序的。一个一般的平面有根树如下所示：

![](1-2.png)

所有平面有根树构成的类记作 $\mathcal{G}$，其中元素的大小定义为其节点的个数。注意，如果我们把树 $\tau$ 的根去除，那么剩下的部分就构成了若干棵树，因此我们有以下的等式成立：

$$
\begin{gather}
\mathcal{G}\cong \mathcal{Z} \times \mathrm{Seq}(\mathcal{G})
\end{gather}
$$

事实上，这就是 $\mathcal{G}$ 的定义，你可能会觉得这个定义有循环定义的风险，但我们可以这样操作：首先令 $\mathcal{G}^{(0)}=\varnothing$，然后递归地定义

$$
\begin{gather}
\mathcal{G}^{(j+1)}=\mathcal{Z}\times \mathcal{G}^{(j)}
\end{gather}
$$

每次迭代，我们得到的树的深度就增加一层，最后完整的类就可以通过取极限的方式得到：$\mathcal{G}=\bigcup_{j}\mathcal{G}^{(j)}$. 每当我们遇到递归等式时，我们都可以采取类似的方法来显式地构造出该类来。

对于生成函数，我们还是同样地进行转化：

$$
\begin{gather}
G(z)= \dfrac{z}{1-G(z)} \implies G(z)=\dfrac{1-\sqrt{ 1-4z }}{2}
\end{gather}
$$

其中二次方程的另一个根由于包含负系数而被舍弃。应用 $(1+x)^{\alpha}$ 的 Taylor 展开，我们得到

$$
\begin{gather}
G_{n}= \dfrac{1}{n} \binom{ 2n-2 }{ n-1 } =C_{n-1}
\end{gather}
$$

因此平面树的数量由 Catalan 数所给出，从而平面有根树通常也被称为“Catalan 树”。

现在我们来总结一下已有的框架。

**定义 1.2.9** 规范（specification）

一个组合类的 $r$ 元组 $\mathcal{A}=(\mathcal{A}^{(1)},\dots,\mathcal{A}^{(r)})$ 的一个**规范**是一个 $r$ 行的方程组

$$
\begin{gather}
\begin{cases}
\mathcal{A}^{(1)}=\Phi_{1}(\mathcal{A}^{(1)},\dots,\mathcal{A}^{(r)}) \\
\mathcal{A}^{(2)}=\Phi_{2}(\mathcal{A}^{(1)},\dots,\mathcal{A}^{(r)}) \\
\dots \\
\mathcal{A}^{(r)}=\Phi_{r}(\mathcal{A}^{(1)},\dots,\mathcal{A}^{(r)})
\end{cases}
\end{gather}
$$

其中 $\Phi_{j}$ 是一个仅包含无交并、直积、序列、多重集、幂集、循环、单位类、原子类以及（如果有的话）$\mathcal{A}^{(1)},\dots,\mathcal{A}^{(r)}$ 的构造。

如果该方程组是严格上三角的，换言之，$\mathcal{A}^{(r)}$ 仅由 $\mathcal{E},\mathcal{Z}$ 构成，$\mathcal{A}^{(r-1)}$ 仅由 $\mathcal{A}^{(r)},\mathcal{E},\mathcal{Z}$ 构成，以此类推，通过 $r$ 次迭代，我们可以将 $\mathcal{A}^{(1)}$ 写成完全由 $\mathcal{E},\mathcal{Z}$ 以及其它构造所表示的形式，因而该规范就是迭代的。反之则是递归的，此时我们可以进行与树类似的过程：令 $\mathcal{A}^{[0]}=\varnothing$，递归地取 $\mathcal{A}^{[j+1]}=\Phi(\mathcal{A}^{[j]})$，最后再取极限即可。

**定义 1.2.10** 可构造的（constructible）

一个组合类称为是**可构造的**，如果它有一个仅包含无交并、直积、序列、多重集、幂集、循环、单位类、原子类的可容许的规范。

下面是本节的主要定理之一。

**定理 1.2.11** 符号计数方法（无编号类）

一个可构造类的生成函数是一个函数方程组中的一项，且方程组中的运算仅由 $1,z,+,\times,Q,\mathrm{Exp},\overline{\mathrm{Exp}},\mathrm{Log}$ 构成，其中

$$
\begin{gather}
Q(f)=\dfrac{1}{1-f},  &  \overline{\mathrm{Exp}}(f)=\exp\left( \sum_{k=1}^{\infty} (-1)^{k-1} \dfrac{f(z^{k})}{k} \right) \\
\mathrm{Exp}(f)=\exp\left( \sum_{k=1}^{\infty} \dfrac{f(z^{k})}{k} \right), & \mathrm{Log}(f)=\sum_{k=1}^{\infty} \dfrac{\varphi(k)}{k}\ln \dfrac{1}{1-f(z^{k})}
\end{gather}
$$

根据前面的讨论，我们知道迭代的规范对应显式的生成函数，而递归的构造具有通过函数方程组隐含地确定的生成函数，这就是符号计数方法的全部内容。我们以一个例子结束本节。

回顾一下例 1.1.5，我们来通过构造一个递归的规范来解决三角划分的问题。我们可以选定一个三角形，则其两边的部分形成了两个（可以是空的）子划分，如图所示：

![](1-3.png)

其中空划分用一个“二边形”来表示，于是我们有如下对 $\mathcal{T}$ 的规范：

$$
\begin{gather}
\mathcal{T}\cong \mathcal{E}+(\mathcal{T}\times \mathcal{Z}\times \mathcal{T})
\end{gather}
$$

从而我们得到了生成函数的方程

$$
\begin{gather}
T(z)=1+zT(z)^{2} \implies T(z)=\dfrac{1-\sqrt{ 1-4z }}{2z}
\end{gather}
$$

再一次地，我们得到了 Catalan 数：

$$
\begin{gather}
T_{n}=\dfrac{1}{n+1} \binom{ 2n }{ n } =C_{n}
\end{gather}
$$

# Section 3: 整数的拆分与组合

本章的剩余部分主要关注于一些常见的组合学主题，包括整数、字符串和树结构，同样也是符号计数方法通用性的一个展示。

**定义 1.3.1** 组合（composition），拆分（partition）

正整数 $n$ 的一个**组合**是一个整数元组 $(x_{1},\dots,x_{k})$ 满足

$$
\begin{gather}
n=x_{1}+\dots+x_{k}, \quad x_{j}\geq 1
\end{gather}
$$

$n$ 的一个**拆分**是一个整数元组 $(x_{1},\dots,x_{k})$ 满足

$$
\begin{gather}
n=x_{1}+\dots+x_{k}, \quad x_{1}\geq\dots\geq x_{k}\geq 1
\end{gather}
$$

所有组合与拆分构成的组合类分别记作 $\mathcal{C}$ 和 $\mathcal{P}$，其中 $(x_{1},\dots,x_{k})$ 的大小定义为 $x_{1}+\dots+x_{k}$.

根据定义我们知道，组合与拆分的唯一区别就在于各 $x_{j}$ 是否能交换位置（因为我们总是能够给一个集合排序使其按降序排列），这就决定了它们的规范中的不同构造：$\mathcal{C}$ 是 $\mathrm{Seq}$，而 $\mathcal{P}$ 是 $\mathrm{MSet}$.

首先，我们来给出正整数的组合表示，如下所示：

$$
\begin{gather}
\mathcal{I}=\{ 1,2,3,\dots \}=\mathrm{Seq}_{\geq 1}(\mathcal{Z}) \implies I(z)= \dfrac{z}{1-z}
\end{gather}
$$

从而我们有

$$
\begin{gather}
\mathcal{C}=\mathrm{Seq}(\mathcal{I}) \implies C(z)= \dfrac{1}{1-I(z)}=\dfrac{1-z}{1-2z}
\end{gather}
$$

即得

$$
\begin{gather}
C_{n}=2^{n}-2^{n-1}=2^{n-1}, \quad n\geq 1
\end{gather}
$$

这表明，正整数 $n$ 的组合的个数为 $2^{n-1}$，这一简单的结果存在一个简单的解释：考虑一排 $n$ 个点构成的图形，我们可以在点之间插入线条以将这一排点分割为两部分，这样的“点线模型”与 $n$ 的组合是一一对应的。例如，以下图形就对应了组合 $(2,5,2,1)$：

$$
\begin{gather}
\cdot\ \cdot \mid \cdot\cdot\cdot\cdot\cdot \mid \cdot\ \cdot \mid \cdot
\end{gather}
$$

在 $n$ 个点之间有 $n-1$ 个位置可以插入线条，这给出了 $2^{n-1}$ 种组合。

另一边，对于拆分我们有

$$
\begin{gather}
\mathcal{P}=\mathrm{MSet}(\mathcal{I}) \implies P(z)=\prod_{n=1}^{\infty} \dfrac{1}{1-z^{n}}
\end{gather}
$$

直接从 $P(z)$ 中提取系数比较困难，但我们可以对其进行求导，从而得到一个递推关系：

$$
\begin{gather}
z \dfrac{P'(z)}{P(z)}=\sum_{n=1}^{\infty} \dfrac{nz^{n}}{1-z^{n}} \implies nP_{n}=\sum_{j=1}^{n} \sigma(j) P_{n-j}
\end{gather}
$$

其中 $\sigma(n)$ 是 $n$ 的正因数之和。由此，我们可以逐步计算出整数拆分的数量。

我们把 $\mathcal{C}$ 和 $\mathcal{P}$ 的迭代式规范完整地写出来：

$$
\begin{gather}
\mathcal{C}=\mathrm{Seq}(\mathrm{Seq}_{\geq 1}(\mathcal{Z})), \quad \mathcal{P}=\mathrm{MSet}(\mathrm{Seq}_{\geq 1}(\mathcal{Z}))
\end{gather}
$$

通过为其中的构造添加限制，我们可以得到更为精细的结果。

**定理 1.3.2**

设 $\mathcal{T}\subset \mathcal{I}$，则加数被限制在 $\mathcal{T}$ 中的组合与拆分构成的类

$$
\begin{gather}
\mathcal{C}^{\mathcal{T}}=\mathrm{Seq}(\mathrm{Seq}_{\mathcal{T}}(\mathcal{Z})), \quad \mathcal{P}^{\mathcal{T}}=\mathrm{MSet}(\mathrm{Seq}_{\mathcal{T}}(\mathcal{Z}))
\end{gather}
$$

具有生成函数

$$
\begin{gather}
C^{\mathcal{T}}(z)= \dfrac{1}{1-\sum_{n \in \mathcal{T}}z^{n}}= \dfrac{1}{1-T(z)}, \quad P^{\mathcal{T}}(z)=\prod_{n \in \mathcal{T}} \dfrac{1}{1-z^{n}}
\end{gather}
$$

这一定理是可容许性定理的直接推论。特别地，当加数被限制为 $\leq r$ 时，我们有

$$
\begin{gather}
C^{[1..r]}(z)= \dfrac{1}{1-z-z^{2}-\dots-z^{r}}= \dfrac{1-z}{1-2z+z^{r+1}}
\end{gather}
$$

其中比较特殊的是 $r=2$ 的情况，此时有 $C^{\{ 1,2 \}}(z)= \dfrac{1}{1-z-z^{2}}$，利用部分分式分解，我们可以提取出其系数：

$$
\begin{gather}
C_{n}^{\{ 1,2 \}}= \dfrac{1}{\sqrt{ 5 }}\left( \left( \dfrac{1+\sqrt{ 5 }}{2} \right)^{n+1}-\left( \dfrac{1-\sqrt{ 5 }}{2} \right)^{n+1} \right)=F_{n+1}
\end{gather}
$$

为 Fibonacci 数列。这一结果提示我们有一种直接的证明方法：考虑 $n$ 的一个组合，其最后一个加数是 $1$ 或 $2$，如果是 $1$，则前面的部分构成了 $n-1$ 的一个组合；如果是 $2$，则前面的部分构成了 $n-2$ 的一个组合，从而我们得到与 Fibonacci 数列相同的递推关系：$C_{n}^{\{ 1,2 \}}=C_{n-1}^{\{ 1,2 \}}+C_{n-2}^{\{ 1,2 \}}$.

另一方面，我们还可以对外层的构造进行限制，这影响的是加数的数量。例如，设 $\mathcal{C}^{(k)}$ 由所有有 $k$ 个部分的组合构成，那么我们有

$$
\begin{gather}
\mathcal{C}^{(k)}=\mathrm{Seq}_{k}(\mathcal{I}) \implies C^{(k)}(z)=I(z)^{k}=\dfrac{z^{k}}{(1-z)^{k}}
\end{gather}
$$

于是 $n$ 的有 $k$ 个部分的组合的数量为

$$
\begin{gather}
C_{n}^{(k)}=\binom{ n-1 }{ k-1 } 
\end{gather}
$$

这一结果也可以从“点线模型”中看出：我们需要在 $n-1$ 个位置中插入 $k-1$ 条线，组合数 $\binom{ n-1 }{ k-1 }$ 给出了插入的方法数。

接下来我们来看拆分。设 $\mathcal{P}^{(\leq k)}$ 由所有有小于等于 $k$ 个部分的拆分组成，那么 $\mathcal{P}^{(\leq k)}=\mathrm{MSet}_{\leq k}(\mathcal{I})$，这种类型的规范的生成函数求解比较困难，但幸运的是我们可以通过拆分的性质对其进行简化。

对于一个拆分，我们可以用 **Ferrers 图**来表示它，例如，以下图形表示了拆分 $(8,6,6,5,4,2)$：

$$
\begin{align}
& \cdot\cdot\cdot\cdot\cdot\cdot\cdot\cdot \\
& \cdot\cdot\cdot\cdot\cdot\cdot \\
& \cdot\cdot\cdot\cdot\cdot\cdot \\
& \cdot\cdot\cdot\cdot\ \cdot \\
& \cdot\cdot\cdot\cdot \\
& \cdot\cdot
\end{align}
$$

在图中，我们把一行看作一个加数，行的数量就是加数的数量。下面是关键的一步：我们可以转换一下视角，把一列看成一个加数，列的数量就是加数的数量，这给出了同一个数的另一个拆分 $(6,6,5,5,4,3,1,1)$，称为原拆分的**共轭**。

对于 $\mathcal{P}^{(\leq k)}$ 中的一个拆分，其共轭具有这样的性质：其中最大的加数不超过 $k$，此外，由于拆分与其共轭是一一对应的关系，我们就有如下等式成立：

$$
\begin{gather}
\mathcal{P}^{(\leq k)}\cong \mathcal{P}^{[1..k]} \implies P^{(\leq k)}(z)=P^{[1..k]}(z)=\prod_{m=1}^{k} \dfrac{1}{1-z^{m}}
\end{gather}
$$

作为上述关系的一个推论，我们可以求出具有 $k$ 个部分的拆分的数量：

$$
\begin{gather}
P^{(k)}(z)=P^{(\leq k)}(z)-P^{(\leq k-1)}(z)= \dfrac{z^{k}}{(1-z)(1-z^{2})\cdots(1-z^{k})}
\end{gather}
$$

最后，我们来研究另一种常见的组合与拆分的变体，它允许加数中有 $0$ 的存在。

**定义 1.3.3** 弱组合（weak composition），弱拆分（weak partition）

正整数 $n$ 的一个**弱组合**是一个整数元组 $(x_{1},\dots,x_{k})$ 满足

$$
\begin{gather}
n=x_{1}+\dots+x_{k}, \quad x_{j}\geq 0
\end{gather}
$$

$n$ 的一个**弱拆分**是一个整数元组 $(x_{1},\dots,x_{k})$ 满足

$$
\begin{gather}
n=x_{1}+\dots+x_{k}, \quad x_{1}\geq\dots\geq x_{k}\geq 0
\end{gather}
$$

如果我们直接写出弱组合的规范，我们会发现它是不可容许的：

$$
\begin{gather}
\mathcal{C}^{w}=\mathrm{Seq}(\mathrm{Seq}(\mathcal{Z}))=\mathrm{Seq}(\{ \varepsilon \}+\mathcal{Z}+\mathcal{Z}^{2}+\cdots)
\end{gather}
$$

因为序列构造只有当 $\mathcal{B}_{0}=\varnothing$ 时才是可容许的。尽管直接的构造没有效果，但我们可以做一些转换。特别地，我们考虑具有 $k$ 个部分的弱组合，它的规范是可容许的：

$$
\begin{gather}
\mathcal{C}^{w,(k)}=\mathrm{Seq}_{k}(\mathrm{Seq}(\mathcal{Z}))=\mathrm{Seq}(\mathcal{Z})^{k} \implies C^{w,(k)}(z)=\dfrac{1}{(1-z)^{k}}
\end{gather}
$$

从而有

$$
\begin{gather}
C_{n}^{w,(k)}=\binom{ n+k-1 }{ k-1 } 
\end{gather}
$$

同样，利用“点线模型”，我们可以给出上述结果的一个简单证明。下面是 $n=10,k=5$ 时的一个弱组合 $(2,4,0,3,1)$ 的一个图形：

$$
\begin{gather}
\cdot\ \cdot \mid \cdot\cdot\cdot\ \cdot \mid \mid \cdot\cdot\cdot \mid \cdot
\end{gather}
$$

我们可以想象有 $n+k-1$ 个空位，其中可以放入点或者线，每当点的位置确定，则线的位置也随之确定，这给出了共 $\binom{ n+k-1 }{ n }=\binom{ n+k-1 }{ k-1 }$ 种放置的方法。

另一种证明方法如下：考虑 $n$ 的一个有 $k$ 个部分的弱组合 $(x_{1},\dots,x_{k})$，那么 $(x_{1}+1,\dots,x_{k}+1)$ 就是 $n+k$ 的一个有 $k$ 个部分的组合，这给出

$$
\begin{gather}
C_{n}^{w,(k)}=C_{n+k}^{(k)}=\binom{ n+k-1 }{ k-1 } 
\end{gather}
$$

同理，我们可得 $n$ 的具有 $k$ 个部分的弱拆分的数量为

$$
\begin{gather}
P_{n}^{w,(k)}=P_{n+k}^{(k)}=[z^{n}] \prod_{m=1}^{k} \dfrac{1}{1-z^{m}}
\end{gather}
$$

注意到 $\mathcal{P}^{w,(k)}$ 的生成函数与 $\mathcal{P}^{(\leq k)}$ 的生成函数是相同的：因为我们可以将取值为 $0$ 的 $x_{j}$ 去除，从而得到一个 $\leq k$ 个部分的拆分，反之我们也可以将不足 $k$ 个部分的拆分在末尾补 $0$，进而得到一个有 $k$ 个部分的弱拆分，这就证明了上述同构关系 $\mathcal{P}^{w,(k)}\cong\mathcal{P}^{(\leq k)}$.

# Section 4: 字符串和正则语言

固定一个有限的字符表 $\mathcal{A}$，其中每个字符都是原子（具有大小 $1$），我们将 $\mathcal{A}$ 的所有有限序列构成的组合类记作 $\mathcal{W}$（或 $\mathcal{A}^{\star}$），称为字符串类。$\mathcal{W}$ 的任意子集 $\mathcal{L}$ 称为是一个（形式）**语言**。根据字符串类的定义，我们立即得到

$$
\begin{gather}
\mathcal{W}=\mathrm{Seq}(\mathcal{A}) \implies W(z)=\dfrac{1}{1-mz}, \quad W_{n}=m^{n}
\end{gather}
$$

其中 $m$ 是 $\mathcal{A}$ 中字符的数量。

在本节中，我们将介绍字符串类的一族特殊子集，即正则语言，以及它的两种不同但等价的表示方法：一种是迭代的（非递归的），另一种是递归的，它们各自有其适用的领域，尽管这两种构造的等价性不是平凡的。

我们从字符表为 $\mathcal{A}=\{ a,b \}$ 的二进制字符串开始。给定这样一个字符串 $aaabaababbaaa$，我们可以发现它有这样一种结构：首先以一个 $a$ 的序列开始（可以是空序列），然后接着是一个 $b$，再接着是一个 $a$ 的序列（可以是空序列），接着又是一个 $b$，以此类推。由此，我们建立了一个基本的同构：

$$
\begin{gather}
\mathcal{W}\cong \mathrm{Seq}(a)\ \mathrm{Seq}(b\ \mathrm{Seq}(a)) \implies W(z)=\dfrac{1}{1-z} \dfrac{1}{1-\frac{z}{1-z}}= \dfrac{1}{1-2z}
\end{gather}
$$

在这一基础上，我们可以添加一些限制条件，比如我们可以要求 $a$ 连续出现的次数 $<k$，这对应了如下的规范：

$$
\begin{gather}
\mathcal{W}^{\langle k \rangle }\cong \mathrm{Seq}_{<k}(a)\ \mathrm{Seq}(b\ \mathrm{Seq}_{<k}(a)) \implies W^{\langle k \rangle }(z)= \dfrac{1-z^{k}}{1-2z+z^{k+1}}
\end{gather}
$$

观察上面两个例子可以发现，它们的规范都是迭代的，且仅使用了无交并、直积以及序列，这引出了以下定义：

**定义 1.4.1** 正则规范（regular specification），$S$-正则（$S$-regular）

一个只含有原子、无交并、直积和序列构造的迭代规范称为是一个**正则规范**。一个语言 $\mathcal{L}$ 称为是 $S$**-正则的**，如果存在一个由正则规范所描述的组合类 $\mathcal{M}$ 使得 $\mathcal{L}\cong\mathcal{M}$.

根据正则规范以及可容许性定理，我们立即得到：

**定理 1.4.2**

一个 $S$-正则语言的生成函数是一个有理函数，它是由将正则规范中的原子替换为 $z$，无交并替换为 $+$，直积替换为 $\times$，序列替换为 $Q$ 构成的。

关于 $S$-正则语言，我们再给出两个例子。

考虑仅出现 $k$ 次字符 $b$ 的二进制字符串构成的语言 $\mathcal{L}$，则其有正则规范

$$
\begin{gather}
\mathcal{L}\cong \mathrm{Seq}(a)\ (b\ \mathrm{Seq}(a))^{k} \implies L(z)= \dfrac{z^{k}}{(1-z)^{k+1}}
\end{gather}
$$

这给出 $L_{n}=\binom{ n }{ k }$. 事实上，对于一个长度为 $n$ 的二进制字符串，一旦我们选定了 $b$ 的位置，那么 $a$ 的位置就完全确定了，这给出 $\binom{ n }{ k }$ 种放置 $b$ 的方法。

接下来，我们要求两个 $b$ 之间的距离小于 $d$，这样的字符串的数量记作 $\binom{ n }{ k }_{<d}$，则我们有

$$
\begin{gather}
\mathcal{L}^{[d]}\cong \mathrm{Seq}(a)\ (b\ \mathrm{Seq}_{<d}(a))^{k-1}\ b\ \mathrm{Seq}(a) \implies \binom{ n }{ k } _{<d} = [z^{n}] \dfrac{z^{k}(1-z^{d})^{k-1}}{(1-z)^{k+1}}
\end{gather}
$$

一个类似的问题是确定两个 $b$ 之间的距离大于等于 $d$ 的字符串数量 $\binom{ n }{ k }_{\geq d}$，利用符号计数方法，无需多加思考便能立即得到该问题的答案。

另一个例子中，我们要求二进制字符串中不能出现连续 $\alpha$ 个 $a$ 和连续 $\beta$ 个 $b$，此时 $\mathrm{Seq}(a)\ \mathrm{Seq}(b\ \mathrm{Seq}(a))$ 的规范就不适用了，因此我们需要将其换成

$$
\begin{gather}
\mathcal{W}\cong \mathrm{Seq}(b)\ \mathrm{Seq}(a\ \mathrm{Seq}(a)\ b\ \mathrm{Seq}(b))\ \mathrm{Seq}(a)
\end{gather}
$$

通过计算两边的生成函数，我们可以证明它们确实是同构的，从而我们有

$$
\begin{gather}
\mathcal{W}^{\langle \alpha,\beta \rangle }\cong \mathrm{Seq}_{\leq\beta}(b)\ \mathrm{Seq}(a\ \mathrm{Seq}_{<\alpha}(a)\ b\ \mathrm{Seq}_{<\beta}(b))\ \mathrm{Seq}_{\leq\alpha}(a)
\end{gather}
$$

得益于符号计数方法，其生成函数 $W^{\langle \alpha,\beta \rangle}(z)$ 可以从上述规范中直接读出。

下面我们来考虑模式匹配的问题。一个“模式”通常指的是一个特定的字符串（比如 $abb$），我们想知道的是含有这种模式的字符串占所有字符串的比例。对于“含有一个模式”的含义，我们有两种定义：

- 子序列式：这样一种模式只需要字符以正确的顺序出现，而不要求连续性，例如 $ccd\ \boxed{a}\ cadc\ \boxed{b}\ dac\ \boxed{b}\ c$.
- 因子式：这样一种模式要求字符以正确的顺序连续地出现，例如 $cdc\ \boxed{abb}\ dbb$.

对于子序列式的模式，我们可以直接写出它的规范。设给定的模式为 $\mathfrak{p}=p_{1}p_{2}\dots p_{k}$，则含有 $\mathfrak{p}$ 的字符串具有以下的结构：首先以一个不包含 $p_{1}$ 的序列开始，紧接着是 $p_{1}$，接下来是一个不包含 $p_{2}$ 的序列，接着一个 $p_{2}$，以此类推，从而我们有

$$
\begin{gather}
\mathcal{L}\cong \mathrm{Seq}(\mathcal{A}\setminus p_{1})\ p_{1}\ \mathrm{Seq}(\mathcal{A}\setminus p_{2})\ p_{2}\dots \mathrm{Seq}(\mathcal{A}\setminus p_{k})\ p_{k}\ \mathrm{Seq}(\mathcal{A})
\end{gather}
$$

从而 $\mathcal{L}$ 的生成函数为

$$
\begin{gather}
L(z)= \dfrac{z^{k}}{(1-(m-1)z)^{k}} \dfrac{1}{1-mz}
\end{gather}
$$

然而，对于因子式的模式匹配，迭代式的规范就不那么适用了：对于简单的模式 $abb$，其规范具有如下所示的复杂结构：

$$
\begin{gather}
\mathcal{L}\cong (b)^{\star}\ a(a)^{\star}b\ (a(a)^{\star}b)^{\star}\ b(a+b)^{\star}, \quad x^{\star}=\mathrm{Seq}(x)
\end{gather}
$$

因此，我们需要另一种递归式的规范方法，下面我们给出定义：

**定义 1.4.3** 有限自动机（finite automaton）

一个**有限自动机**包含一个有向多重图，其边由有限字符表 $\mathcal{A}$ 中的元素编号，其顶点集 $Q$ 称为**状态集**，和一个 $q_{0}\in Q$ 称为**初始状态**，以及子集 $\overline{Q}\subset Q$ 称为**最终状态**。

一个自动机称为是**确定性的**，如果对任意 $(q,\alpha)\in Q\times \mathcal{A}$，最多存在一条边（称为一个**状态转移**）以 $q$ 为起始点，且该边由 $\alpha$ 编号。

一个确定性有限自动机可以用来判断一个字符串是否含有某种模式。给定一个字符串 $w$，我们从初始状态开始，读入 $w$ 的第一个字符，假设是 $a$，此时自动机就进行了一次状态转移：从 $q_{0}$ 移动到边 $a$ 所指向的节点，接下来读入 $w$ 的第二个字符，进行类似的操作，以此类推。如果读完 $w$ 的所有字符后自动机的状态是一个最终状态，我们就称 $w$ 被该状态机**接受**。

我们以模式 $abb$ 对应的自动机来进行说明：

![](1-4.png)

给定字符串 $ababba$，则自动机的状态变化如下：

$$
\begin{gather}
0 \overset{a}{\longrightarrow} 1 \overset{b}{\longrightarrow} 2 \overset{a}{\longrightarrow} 1 \overset{b}{\longrightarrow} 2 \overset{b}{\longrightarrow} 3 \overset{a}{\longrightarrow} 3
\end{gather}
$$

$3$ 是一个最终状态，因此 $ababba$ 被该自动机接受，这表明它含有模式 $abb$.

**定义 1.4.4** $A$-正则（$A$-regular）

一个语言 $\mathcal{L}$ 是 $A$**-正则的**，如果它由被一个确定性有限自动机所接受的字符串构成。一个组合类 $\mathcal{M}$ 是 $A$-正则的，如果存在一个 $A$-正则的语言 $\mathcal{L}$ 使得 $\mathcal{M}\cong\mathcal{L}$.

下面的等价定理将 $S$-正则与 $A$-正则联系了起来，它的证明我们略去。

**定理 1.4.5** Kleene-Rabin-Scott 定理

一个语言是 $S$-正则的当且仅当它是 $A$-正则的。

该定理表明，一个被有限自动机接受的语言必然有正则规范，反之亦然，因此我们建立的两种构造方法是等价的，我们可以根据情况任意选用一种方法，而不必担心存在一致性问题。

下面我们给出由有限自动机所描述的语言的生成函数。

**定理 1.4.6**

设 $G$ 是一个确定性有限自动机，其状态集为 $Q=\{ q_{0},\dots,q_{s} \}$，初始状态为 $q_{0}$，且最终状态为 $\overline{Q}=\{ q_{i_{1}},\dots,q_{i_{f}} \}$，则由被 $G$ 接受的字符串构成的语言 $\mathcal{L}$ 的生成函数是一个有理函数，且由以下表达式给出：

$$
\begin{gather}
L(z)=\mathbf{u} (I-zT)^{-1} \mathbf{v}
\end{gather}
$$

其中转移矩阵 $T$ 定义为

$$
\begin{gather}
T_{j,k}=\lvert \{ \alpha \in \mathcal{A} \mid \text{边 } (q_{j},q_{k}) \text{ 由 } \alpha \text{ 编号} \} \rvert 
\end{gather}
$$

$\mathbf{u}$ 是行向量 $(1,0,\dots,0)$，$\mathbf{v}$ 是列向量 $(v_{0},\dots,v_{s})^{T}$ 使得

$$
\begin{gather}
v_{j}=[q_{j} \in \overline{Q}]=\begin{cases}
1 & , q_{j}\in \overline{Q} \\
0 & , q_{j}\not\in \overline{Q}
\end{cases}
\end{gather}
$$

**证明**

对于 $0\leq j\leq s$，定义语言 $\mathcal{L}_{j}$ 包含所有使得 $G$ 从状态 $q_{j}$ 开始，读入 $w$ 后 $G$ 达到最终状态的字符串 $w$，于是我们有以下等式：

$$
\begin{gather}
\mathcal{L}_{j}\cong \Delta_{j}+ \sum_{\alpha \in \mathcal{A}} \alpha\ \mathcal{L}_{(q_{j}\circ\alpha)}
\end{gather}
$$

其中 $\Delta_{j}$ 在 $q_{j}$ 是最终状态时为单位类，在其它情况下为空集；$q_{j}\circ\alpha$ 表示读入 $\alpha$ 后从 $q_{j}$ 到达的新状态。这一同构关系的证明非常简单：如果 $q_{j}$ 已经是最终状态，那么读入一个空字符就可以达到最终状态；任取 $\alpha \in \mathcal{A}$，如果一个字符串 $w$ 在 $\mathcal{L}_{j}$ 中并且 $w$ 的第一个字符为 $\alpha$，那么去除第一个字符后剩下的字符串必然能够使 $G$ 从状态 $q_{j}\circ\alpha$ 到达最终状态，这给出了因子 $\alpha\ \mathcal{L}_{(q_{j}\circ\alpha)}$.

从上述同构关系我们得到生成函数的线性方程：

$$
\begin{gather}
L_{j}(z)=[q_{j} \in \overline{Q}]+z \sum_{\alpha \in \mathcal{A}} L_{(q_{j}\circ\alpha)}(z)
\end{gather}
$$

于是当 $\mathbf{L}(z)$ 为列向量 $(L_{0}(z),\dots,L_{s}(z))^{T}$ 时有

$$
\begin{gather}
\mathbf{L}(z)=\mathbf{v}+zT \mathbf{L}(z)
\end{gather}
$$

$\mathbf{v}$ 和 $T$ 如定理中所示，从而得到 $\mathcal{L}$ 的生成函数 $L_{0}(z)=\mathbf{u}(1-zT)^{-1}\mathbf{v}$.

我们仍然以 $abb$ 的例子来说明这一过程。根据前面的定义，我们有

$$
\begin{align}
\mathcal{L}_{0} &\cong a\mathcal{L}_{1}+b\mathcal{L}_{0} \\
\mathcal{L}_{1} &\cong a\mathcal{L}_{1}+b\mathcal{L}_{2} \\
\mathcal{L}_{2} &\cong a\mathcal{L}_{1}+b\mathcal{L}_{3} \\
\mathcal{L}_{3} &\cong a\mathcal{L}_{3}+b\mathcal{L}_{3}+\mathcal{E}
\end{align}
$$

这给出了生成函数的一个线性方程组

$$
\begin{align}
L_{0} &= zL_{1}+zL_{0} \\
L_{1} &= zL_{1}+zL_{2} \\
L_{2} &= zL_{1}+zL_{3} \\
L_{3} &= zL_{3}+zL_{3}+1
\end{align}
$$

解这个方程组，我们就得到了含有模式 $abb$ 的字符串构成的类的生成函数：

$$
\begin{gather}
L_{0}(z)= \dfrac{z^{3}}{(1-z)(1-2z)(1-z-z^{2})},\quad L_{0,n}=2^{n}-F_{n+3}+1
\end{gather}
$$

其中 $F_{n}$ 是 Fibonacci 数。特别地，长度为 $n$ 且不包含 $abb$ 的字符串的数量为 $F_{n+3}-1$.

自动机不止可以做因子式的模式匹配，但仅就该问题而言，我们还可以做的更好：我们可以给出最终结果 $L(z)$ 的一个显式表达，如下所示。

对于一个模式 $\mathfrak{p}=p_{1}\dots p_{k}$，我们引入它的**自相关向量** $c=(c_{0},\dots,c_{k-1})$ 如下：

$$
\begin{gather}
c_{i}=[p_{i+1}p_{i+2}\dots p_{k}=p_{1}p_{2}\dots p_{k-i}]
\end{gather}
$$

它检测了 $\mathfrak{p}$ 的开头与末尾重叠的部分：

$$
\begin{align}
\mathfrak{p}=p_{1}\dots p_{i}\ & \boxed{p_{i+1}\dots p_{k}} \\
&\boxed{{p_{1}}\dots\ p_{k-i}}\ p_{k-i+1}\dots p_{k} = \mathfrak{p}
\end{align}
$$

与之对应的**自相关多项式**定义为

$$
\begin{gather}
c(z)=\sum_{j=0}^{k-1} c_{j}z^{j}
\end{gather}
$$

定义 $\mathcal{S}$ 由不包含模式 $\mathfrak{p}$ 的字符串构成，$\mathcal{T}$ 由模式 $\mathfrak{p}$ 仅在末尾出现的字符串构成。首先，在 $\mathcal{S}$ 中的字符串末尾添加一个字符，得到的字符串或者不包含 $\mathfrak{p}$，或者仅在末尾包含 $\mathfrak{p}$，从而有

$$
\begin{gather}
\mathcal{S}+\mathcal{T}\cong \mathcal{E}+\mathcal{S}\times \mathcal{A}
\end{gather}
$$

接下来，将一个 $\mathfrak{p}$ 添加到 $\mathcal{S}$ 中字符串的末尾，则我们有下式成立：

$$
\begin{gather}
\mathcal{S}\times \{ \mathfrak{p} \}\cong \mathcal{T}\times \sum_{c_{i}=1} \{ p_{k-i+1}p_{k-i+2}\dots p_{k} \}
\end{gather}
$$

这一同构关系由下图给出：

![](1-5.png)

于是我们得到了关于生成函数 $S$ 和 $T$ 的方程组

$$
\begin{gather}
S(z)+T(z)=1+mzS(z),\quad z^{k} S(z)=T(z)c(z)
\end{gather}
$$

解得

$$
\begin{gather}
S(z)=\dfrac{c(z)}{z^{k}+(1-mz)c(z)},\quad T(z)=\dfrac{z^{k}}{z^{k}+(1-mz)c(z)}
\end{gather}
$$

从而包含模式 $\mathfrak{p}$ 的字符串构成的类 $\mathcal{L}$ 的生成函数为

$$
\begin{gather}
L(z)=\dfrac{1}{1-mz}-S(z)= \dfrac{z^{k}}{(1-mz)(z^{k}+(1-mz)c(z))}
\end{gather}
$$

最后，我们给出正则语言的一个应用，它显示了字符串编码的用处。集合 $[n]$ 的一个**划分**指的是一族集合 $\{ B_{1},\dots,B_{r} \}$，使得各 $B_{j}\neq \varnothing$ 且互不相交，并且 $\bigcup B_{j}=[n]$. 例如 $\{ \{ 6,4 \},\{ 5,1,2 \},\{ 3,7,8 \} \}$ 就是 $[8]$ 的一个划分。我们记 $\mathcal{S}^{(r)}$ 为所有具有 $r$ 个部分的集合划分构成的类，下面我们就来确定 $S_{n}^{(r)}$ 的数量。

设字符表为 $\mathcal{B}=\{ b_{1},\dots,b_{r} \}$，我们可以找到一种方法来建立 $\mathcal{S}^{(r)}$ 与一种语言之间的同构。具体来说，对于 $[n]$ 的一个划分 $P=\{ B_{1},\dots,B_{r} \}$，选择每个 $B_{j}$ 中最小的元素作为它的代表元，然后为 $P$ 排序使得各代表元升序排列，此时有 $P=\{ B_{1}',\dots,B_{r}' \}$，最后为 $B_{j}'$ 中的元素分配字符 $b_{j}$，构成字符串 $\beta(1)\beta(2)\dots\beta(n)$，其中 $\beta(k)$ 是为 $k$ 分配的字符。

例如，对于划分 $\{ \{ 6,4 \},\{ 5,1,2 \},\{ 3,7,8 \} \}$，我们首先对其排序得到 $\{ \{ \mathbf{1},2,5 \},\{ \mathbf{3},7,8 \},\{ \mathbf{4},6 \} \}$，然后用 $\mathcal{B}$ 为其编码：

$$
\begin{gather}
\begin{pmatrix}
1 & 2 & 3 & 4 & 5 & 6 & 7 & 8 \\
b_{1} & b_{1} & b_{2} & b_{3} & b_{1} & b_{3} & b_{2} & b_{2}
\end{pmatrix}
\end{gather}
$$

这样构成的字符串有以下特点：

1. 所有字符均出现；
2. $b_{j}$ 第一次出现的位置在 $b_{j+1}$ 之前。

由此我们可以写出 $\mathcal{S}^{(r)}$ 的规范：

$$
\begin{gather}
\mathcal{S}^{(r)}\cong b_{1}\ \mathrm{Seq}(b_{1})\ b_{2}\ \mathrm{Seq}(b_{1}+b_{2})\dots b_{r}\ \mathrm{Seq}(b_{1}+\dots+b_{r})
\end{gather}
$$

从而有生成函数

$$
\begin{gather}
S^{(r)}(z)= \dfrac{z^{r}}{(1-z)(1-2z)\cdots(1-rz)}
\end{gather}
$$

根据部分分式分解即得

$$
\begin{gather}
S^{(r)}(z)=\dfrac{1}{r!}\sum_{j=1}^{r} \binom{ r }{ j } \dfrac{(-1)^{r-j}}{1-jz} \implies S_{n}^{(r)}=\dfrac{1}{r!}\sum_{j=1}^{r} (-1)^{r-j}\binom{ r }{ j } j^{n}
\end{gather}
$$

数 $S_{n}^{(r)}$ 被称为**第二类无符号 Stirling 数**，有时记作 $\left\{ \begin{matrix} n \\ r \end{matrix} \right\}$，我们将在后续的章节中再次遇到它。