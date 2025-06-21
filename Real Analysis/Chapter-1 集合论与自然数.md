在分析中，最重要，也是最先学习的概念便是**极限**。然而，我们对极限的定义是不完善的，除非我们完全描述清楚了**实数**是什么。比如，为什么可以取任意小的 $\varepsilon>0$ 而不会遇到所谓的“无穷小”？有理数与实数有什么区别，以至于我们必须在实数上定义极限？如果不了解实数的完备性，这些问题是无法严格回答的。

而要定义实数，我们就必须了解**有理数**，而有理数又可还原到**整数**，整数又可进一步还原到**自然数**。自然数的公理又是使用集合论的语言写成的，因此，我们将从集合开始逐步构建起分析的框架。

# Section 1: 公理集合论

按照朴素的观点，我们可以认为**集合**是一类确定的、可区分的对象构成的一个整体。这就是说，我们认为下面的命题是成立的：

**公理** 概括公理模式（Axiom Schema of Comprehension）

设 $\varphi$ 是一个性质，则 $Y=\{x \mid \varphi(x)\}$ 是一个集合。

然而，Russell 悖论表明，概括公理是不一致的，即使用它会引发矛盾：考虑集合 $S=\{x\mid x \not\in x\}$，则有 $S \in S\iff S \not\in S$，矛盾。

因此我们不得不放弃概括公理，转而使用更弱的**分离公理模式**：

设 $X$ 是一个集合，$\varphi$ 是一个性质，则 $Y=\{x\in X\mid \varphi(x)\}$ 是一个集合。

但是，现在我们有了一个新的问题：通过分离公理得到的集合都不大于已有的集合，这就导致我们无法进行集合论的研究。比如，分离公理无法确定两个集合的并集 $X \cup Y$ 是否存在。于是我们就需要添加更多的公理来保证一些特定的集合构造是可行的。

在数学中，ZFC 公理系统是最常用的一种集合论假设，其中只有一种原始（无定义）对象：集合，以及一种原始二元关系：集合间的属于关系 $\in$，满足以下公理：

**公理 ZF1** 外延公理（Axiom of Extensionality）

如果对任意 $x$ 有 $x \in X \iff x \in Y$，那么 $X=Y$.

**公理 ZF2** 分离公理模式（Axiom Schema of Separation）

设 $\varphi$ 是一个性质（带有参数 $p$ ），那么对任意集合 $X$ 和 $p$ 存在集合 $Y=\{x\in X\mid \varphi(x,p)\}$.

**公理 ZF3** 配对公理（Axiom of Pairing）

对任意集合 $a,b$ 存在集合 $X=\{a,b\}$.

**公理 ZF4** 并集公理（Axiom of Union）

对任意集合 $X$ 存在集合 $Y=\bigcup X=\{y\mid \exists T \in X (y \in T) \}$.

**公理 ZF5** 幂集公理（Axiom of Power Set）

对任意集合 $X$ 存在集合 $Y=\mathscr{P}(X)=\{ T\mid T \subset X \}$.

**公理 ZF6** 无限公理（Axiom of Infinity）

存在集合 $S$，使得 $\varnothing \in S$ 且对于任意 $x \in S$ 都有 $x \cup \{ x \} \in S$.

**公理 ZF7** 替换公理模式（Axiom Schema of Replacement）

设 $F$ 是一个函数，那么对任意集合 $X$ 存在集合 $Y=F[X]=\{ F(x)\mid x \in X \}$.

**公理 ZF8** 正则公理（Axiom of Regularity）

任意集合 $S \ne \varnothing$ 都存在 $x \in S$ 使得 $S \cap x=\varnothing$.

**公理 AC** 选择公理（Axiom of Choice）

任意集合 $S$ 都存在函数 $g$ 使得对任意 $x \in S,x\ne \varnothing$ 有 $g(x) \in x$.

## 外延公理与分离公理

外延公理表明，一个集合完全由它的元素确定，集合自身并不带有任何额外的结构。于是，我们要指明一个集合，只需要明确那个集合中有什么元素。一种方法就是将集合中的元素列举出来，比如 $\{a,b\},\{a,b,c\}$ 等。注意集合中的元素是无序的，并且元素重复对于集合没有影响，即

$$
\{a,b,c\}=\{b,c,a\}=\{b,c,a,a\}
$$

上面的相等可以由外延公理得出。

对于无限集合等无法列举其元素的集合，我们就必须使用分离公理。一个性质 $\varphi$ 是一个与 $x$ 有关的命题，说 $x$ 满足性质 $\varphi$ 就是说命题 $\varphi(x)$ 是真命题。比如所有正实数构成的集合就是 $\{x \in \mathbb{R} \mid x>0\}$（事实上我们还没有定义实数，因此现在这个集合是不存在的），这也是为什么 ZF2 是一个公理模式：每个性质 $\varphi$ 都对应了一条公理，因此 ZFC 实际上包含了无穷条公理。

我们将性质 $x \ne x$ 应用到任意集合 $S$ 上，就得到了空集：不含有任何元素的集合，记作 $\varnothing$，它是我们得到的第一个具体的集合。

将外延公理的条件拆分开来，我们可以定义

**定义 1.1.1** 子集（subset）

如果对任意 $x$ 有 $x \in X \implies x \in Y$，则称 $X$ 是 $Y$ 的**子集**，或 $Y$ **包含** $X$，记作 $X \subset Y$.

于是两个集合相等当且仅当 $X \subset Y$ 且 $Y \subset X$.

显然空集是任意集合的子集。

## 配对公理

配对公理也叫做无序对公理，它表明可以将集合 $a,b$ 组合成无序对 $\{a,b\}$，一个只含有两个元素的集合。然而，很多时候我们需要的是**有序对**，比如点的坐标，向量的分量等。事实上，有序对可以由无序对来构造，我们只需明确有序对的决定性特征：

$$
(a,b)=(c,d) \implies a=c \text{且} b=d
$$

即可。可以验证 $(a,b)=\{\{a\},\{a,b\}\}$ 满足上述条件，因此可以作为有序对的定义。

**定义 1.1.2** $n$-元组（$n$-tuple）

设 $x_{1},\dots,x_{n}$ 是集合，定义**有序对**（2-元组）为 $(x_{1},x_{2})=\{\{x_{1}\},\{x_{1},x_{2}\}\}$，并递归地定义 $n$**-元组**为 $(x_{1},\dots,x_{n})=((x_{1},\dots,x_{n-1}),x_{n})$.

有序组同样也满足与有序对类似的性质。

## 并集公理与幂集公理

并集公理肯定了并集的存在性，从而使得我们能够构造元素个数大于2的集合，比如 $\bigcup \{\{a,b\},\{c\}\}=\{a,b\} \cup \{c\}=\{a,b,c\},\{a,b,c\} \cup \{d\}=\{a,b,c,d\}$ 等。

利用并集，我们可以定义其它的集合构造，如交集和差集。

**定义 1.1.3** 交集（intersection）

设 $X$ 是一个集合，其交集定义为 $\bigcap X=\left\{ y \in \bigcup X \mid \forall T \in X (y \in T) \right\}$.

即，$X$ 的交集包含了所有 $X$ 中元素的公共元素。习惯上，我们可以写 $\bigcap \{A,B\}=A \cap B, \bigcap \{A,B,C\}=A \cap B \cap C$ 等。

**定义 1.1.4** 差集（set difference）

设 $X,Y$ 是集合，$X$ 对 $Y$ 的**差集**定义为 $X \setminus Y=\{x \in X \mid x \not\in Y\}$.

如果 $Y \subset X$，则称 $X \setminus Y$ 为 $Y$ 在 $X$ 中的**补集**（complement），如果 $X$ 是明确的，通常可以写成 $Y^{c}$.

集合的交、并、差满足一系列性质，如交换性、结合性等，其中最重要的性质是 De Morgan 律：

**定理 1.1.5** De Morgan 律

设 $A \subset X,B \subset X$，则

$$
\begin{gather*}
X \setminus (A \cap B)=(X \setminus A) \cup (X \setminus B) \\
X \setminus (A \cup B)=(X \setminus A) \cap (X \setminus B)
\end{gather*}
$$

可以通过证明两个方向上的包含来证明上述定理。

另一方面，幂集可以看成是并集的反方向运算：$\mathscr{P}(X)$ 由 $X$ 的所有子集构成，从而有 $\bigcup \mathscr{P}(X)=X$，因为 $X$ 自身也是 $X$ 的子集。

使用幂集公理，我们可以给出数学中最重要的定义：关系与函数。首先我们来定义有序对组成的集合：直积。

**定义 1.1.6** 直积（Cartesian product）

集合 $X,Y$ 的**直积**定义为 $X \times Y=\{(x,y) \in \mathscr{P}(\mathscr{P}(X \cup Y)) \mid x \in X, y \in Y \}$.

下面我们可以定义**关系**。

**定义 1.1.7** 关系（relation）

一个从 $X$ 到 $Y$ 的关系 $R$ 定义为 $R \subset X \times Y$，$Y$ 称为 $R$ 的**陪域**（codomain），$\mathrm{Dom}(R)=\{ x \in X \mid \exists y \in Y((x,y)\in R) \}$ 称为 $R$ 的**定义域**（domain）。

设 $E \subset X$，则称 $R[E]=\{ y \in Y \mid (x,y) \in R, x \in E \}$ 为 $E$ 在 $R$ 下的**像**（image），称 $\mathrm{Ran}(R) = R[X]$ 为 $R$ 的**值域**（range）。设 $G \subset Y$，则称 $R^{-1}[G]=\{ x \in X \mid (x,y) \in R, y \in G \}$ 为 $G$ 在 $R$ 下的**原像**（preimage）。

通常我们将 $(x,y) \in R$ 记作 $xRy$.

我们以几个例子来说明这一点。首先我们考虑整数上的小于关系，我们有 $0<1, 0<2, 1<2, 2<3, \dots$，即

$$
R_{<} = \{ \dots,(0,1),(0,2),(1,2),(2,3),\dots \}
$$

我们再看整数上的等于关系，有

$$
R_{=}=\{ \dots,(-1,-1),(0,0),(1,1),(2,2),\dots \}
$$

通过将元素之间的关系转换成有序对的属于关系，我们成功地将各种关联纳入了 ZFC 的框架之下。

现在我们考虑一种特殊的关系 $f \subset X \times Y$，其满足对于任意的 $x \in X$ 都有唯一的 $y \in Y$ 使得 $(x,y) \in f$，这就是一个**映射**。

**定义 1.1.8** 映射（map），函数（function）

设 $f \subset X \times Y$ 满足对任意的 $x \in X$ 都有唯一的 $y \in Y$ 使得 $(x,y) \in f$，则称 $f$ 是一个从 $X$ 到 $Y$ 的**映射**（或**函数**），记作 $f\colon X \to Y$。通常将 $(x,y) \in f$ 记作 $y=f(x)$，称 $y$ 为 $f$ 在 $x$ 的**值**。

每个关系都可以单值化为一个映射，具体操作如下：任取 $x \in \mathrm{Dom}(R)$，选择 $y \in R[x]$ 并令 $f(x)=y$，就得到了从 $\mathrm{Dom}(R)$ 到 $Y$ 的一个映射 $f$，选择公理保证了这种选择总是可行的。

下面我们再给出一些与关系相关的概念。

**定义 1.1.9** 逆关系（inverse relation）

关系 $R \subset X \times Y$ 的**逆关系**定义为 $R^{-1}=\{ (y,x) \mid (x,y) \in R \}$.

**定义 1.1.10** 复合（composition）

关系 $R \subset X \times Y$ 与 $S \subset Y \times Z$ 的**复合**定义为 $S \circ R=\{ (x,z) \mid \exists y \in Y((x,y) \in R, (y,z) \in S) \}$.

显然映射的复合仍然是映射，但是映射的逆关系不一定是映射。下面的定义给出了映射的逆关系是映射的条件。

**定义 1.1.11** 单射（injection），满射（surjection），双射（bijection）

设 $f\colon X \to Y$ 是一个映射，

- 若 $\mathrm{Ran}(f)=Y$，则称 $f$ 是一个**满射**。
- 若 $f(x_{1})=f(x_{2}) \implies x_{1}=x_{2}$，则称 $f$ 是一个**单射**。
- 若 $f$ 既是单射又是满射，则称 $f$ 是一个**双射**。

如果 $f$ 是一个双射，则对于任意 $y\in Y$，存在唯一的 $x \in X$ 使得 $(x,y) \in f$，这就表明 $f^{-1}$ 也是一个映射（同时也是双射），且 $f(f^{-1}(x))=f^{-1}(f(x))=x$.

注意，$f$ 的满射性是相对于陪域而言的，如 $f\colon X \to \mathrm{Ran}(f)$ 是满射，但如果 $\mathrm{Ran}(f) \subsetneq Y$，那么 $f\colon X\to Y$ 就不是满射。在一般的数学研究中，这种区别不会造成严重错误，在需要时指明映射的陪域即可。

通常我们使用 $Y^{X}=\{ f \in \mathscr{P}(X \times Y) \mid f\colon X \to Y \}$ 表示 $X \to Y$ 的映射构成的集合。

## 无限公理

我们首先引入集合的后继运算以及归纳集的定义。

**定义 1.1.12** 后继（successor）

集合 $x$ 的**后继**定义为 $x'=x \cup \{ x \}$.

**定义 1.1.13** 归纳集（inductive set）

一个集合 $S$ 是**归纳集**，如果 $\varnothing \in S$ 且对任意 $x \in S$ 有 $x' \in S$.

于是无限公理表明：存在归纳集。现在我们取一个归纳集 $S$ 并分离出以下集合：

$$
\omega=\{ x \in S \mid x \in \text{所有归纳集} \}
$$

这个集合在分析中非常重要，原因将在之后揭晓。

**定理 1.1.14**

$\omega$ 是最小的归纳集。

**证明**

根据定义我们有 $\omega \subset \text{所有归纳集}$，于是我们有了最小性，现在要证 $\omega$ 是归纳集。

任取归纳集 $S$，有 $\varnothing \in S$，因此 $\varnothing \in \omega$.

设 $x \in \omega$，则 $x \in S$，即 $x' \in S$，于是 $x' \in \omega$. 这就完成了证明。

现在我们知道 $\omega$ 中存在元素 $\varnothing,\varnothing',\varnothing'',\dots$，为了进一步研究 $\omega$ 中的元素，我们引入下面的定义：

**定义 1.1.15** 传递集（transitive set）

一个集合 $S$ 是**传递集**，如果对任意 $x \in S$ 有 $x \subset S$.

下面的定理表明，传递集对后继运算封闭。

**定理 1.1.16**

设 $x$ 是传递集，则 $x'$ 也是传递集。

**证明**

设 $y \in t \in x'=x \cup \{ x \}$，要证 $y \in x'$.

若 $t=x$，则显然有 $y \in x'$.

若 $t \in x$，则由传递集的定义有 $t \subset x$，从而 $y \in t \subset x$，即 $y \in x'$. 即证。

空集显然是传递集，从而 $\varnothing,\varnothing',\varnothing'',\dots \in \omega$ 都是传递集，下面我们证明 $\omega$ 中没有其它元素。

**定理 1.1.17**

$\omega$ 的所有元素都是传递集。

**证明**

令 $\alpha=\{ x \in \omega \mid x \text{是传递集} \}$，我们要证 $\alpha$ 是归纳集。

显然 $\varnothing \in \alpha$，再由传递集对后继的封闭性可知 $\alpha$ 是归纳集。由于 $\omega$ 是最小的归纳集，所以有 $\alpha=\omega$.

下面我们证明最后一个关于 $\omega$ 的定理。

**定理 1.1.18**

任取 $x,y \in \omega$，则 $x'=y' \implies x=y$.

首先我们证明一个引理：

**引理**

设 $x$ 是一个集合，则 $x \not\in x$.

**证明**

如果 $x=\varnothing$，则显然有 $x \not\in x$.

如果 $x \ne \varnothing$，假设有 $x \in x$，利用配对公理构造集合 $S=\{ x \}$，则 $S \cap x=x\ne \varnothing$，这与正则公理矛盾。因此 $x \not\in x$.

**证明（1.1.18）**

假设 $x \ne y$，则有 $x \in x'=y'=y \cup \{ y \}$，于是 $x \in y$. 同理 $y\in x$. 由于 $x$ 是传递集，故有 $x \in x$，矛盾。

现在我们总结一下我们所知的 $\omega$ 的性质：

1. $\varnothing \in \omega$.
2. $x \in \omega \implies x' \in \omega$.
3. 对任意 $x \in \omega$ 有 $x' \ne \varnothing$.
4. 对任意 $x,y \in \omega$ 有 $x'=y' \implies x=y$.
5. 设 $\alpha \subset \omega$，$\varnothing \in \alpha$ 且对任意 $x \in \alpha$ 有 $x' \in \alpha$，则 $\alpha=\omega$.

现在我们就可以断言，$\omega$ 就是（准确来说，是同构于）自然数集，这里就是古典分析学的源头，只需简单地定义

$$
0=\varnothing,1=0'=\{ 0 \},2=1'=\{ 0,1 \},3=2'=\{ 0,1,2 \},\dots
$$

从而我们就构造出了自然数的一个模型，见下一节内容。

最后，作为本节的结尾，我们给出**有限**与**无限**的概念。

**定义 1.1.19** 有限集（finite set)，无限集（infinite set），可数集（countable set），基数（cardinality），序列（sequence）

设 $X$ 是一个集合，如果存在双射 $f\colon n \to X$，则称 $X$ 是**有限集**，其**基数**为 $|X|=n$. 不是有限集的集合称为**无限集**。

如果存在双射 $f\colon \omega \to X$，则称 $X$ 是**可数集**，定义其基数为 $|X|=\aleph_{0}$.

映射 $f\colon n \to X$ 称为 $X$ 中元素的**有限序列**，映射 $f\colon \omega \to X$ 称为 $X$ 中元素的**无限序列**。

# Section 2: 自然数

下面的自然数性质称为 Peano 公理，简称为 PA1-PA5.

**定义 1.2.1** 自然数（Natural Number）

三元组 $(\mathbb{N},0,s)$（其中 $s\colon \mathbb{N} \to \mathbb{N}$ ）是一个**自然数系**如果：

1. $0 \in \mathbb{N}$.
2. $n \in \mathbb{N} \implies s(n)\in \mathbb{N}$.
3. 对任意 $n \in \mathbb{N}$ 有 $s(n) \ne 0$.
4. 对任意 $n,m\in \mathbb{N}$ 有 $s(n)=s(m) \implies n=m$.
5. 设 $S \subset \mathbb{N}$，$0\in S$ 且对任意 $n\in S$ 有 $s(n)\in S$，则 $S=\mathbb{N}$.

$\mathbb{N}$ 中的元素称为**自然数**，$s$ 称为**后继函数**，PA5 又称为归纳公理。

Peano 公理精确地描述了自然数系的形象：PA1 和 PA2 给出了自然数的基本元素，即它有一个起点，其元素是按顺序排列的。然而，仅凭这两条公理还无法确定自然数的形状，比如，我们可以有如下所示的环形结构：

$$
0 \to s(0) \to ss(0) \to sss(0) \to ssss(0)=s(0) \to ss(0) \to \dots
$$

又或者是如下的双向无穷长链：

$$
\dots \to a \to s(a) \to ss(a)=0 \to s(0) \to ss(0) \to \dots
$$

于是我们就需要添加 PA3 和 PA4 来否定上述的“错误”结构，但 PA1-PA4 仍不足以限定出我们心中的自然数结构，这是因为我们的自然数中可能会出现如下的冗余结构：

$$
\begin{gather*}
0 \to s(0) \to ss(0) \to \dots \\
x \to s(x) \to ss(x) \to \dots \\
\dots
\end{gather*}
$$

这就是为什么我们还要添加 PA5，它显示了自然数的一种“最小性”，从而我们的自然数模型只能有一条单向无穷长链：

$$
0 \to s(0) \to ss(0) \to sss(0) \to \dots
$$

按习惯记号，我们可以写 $1=s(0),2=ss(0),3=sss(0),\dots$

上一节的讨论表明，ZFC 蕴含了 PA，其中最小归纳集 $\omega$ 就是一个自然数模型。并且我们还可以证明，所有的自然数模型都同构，即在同构的意义下，自然数模型是唯一的。这一命题的证明依赖于下面的定理：

**定理 1.2.2** 递归原理

给定集合 $X$ 与函数 $h\colon X\to X$，以及 $x_{0} \in X$，则存在唯一的函数 $f\colon \omega \to X$ 满足

$$
\begin{gather*}
\begin{cases}
f(0)=x_{0}\\
f(n')=h(f(n))
\end{cases}
\end{gather*}
$$

**证明**

我们先证明唯一性。设有映射 $f,g$ 满足定理条件，令 $\alpha=\{ n \in \omega \mid f(n)=g(n) \}$，我们要证 $\alpha=\omega$.

$f(0)=x_{0}=g(0)$，故 $0 \in \alpha$.

设 $n \in \alpha$，则 $f(n')=h(f(n))=h(g(n))=g(n')$，于是 $n' \in \alpha$.

故 $\alpha$ 是归纳集，由 $\omega$ 的最小性得 $\alpha=\omega$. 从而有 $f=g$.

再来证明存在性。我们在 $\omega \times X$ 上定义一种关系 $R$，称为归纳关系，满足

1. $(0,x_{0}) \in R$
2. $(n,x)\in R \implies (n',h(x))\in R$

显然 $\omega \times X$ 是一个归纳关系，从中分离出 $f=\{ (n,x) \mid (n,x) \in \text{所有归纳关系} \}$，则 $f$ 也是一个归纳关系，并且具有最小性。现在要证 $f$ 是一个映射。

我们使用归纳法，如果有 $(0,x_{0})\in f,(0,z)\in f,x_{0} \neq z$，则 $f \setminus \{ (0,z) \}$ 仍是一个归纳关系，这与 $f$ 的最小性矛盾。

现设存在唯一的 $x \in X$ 使 $(n,x) \in f$，假设有 $(n',h(x)) \in f,(n',t) \in f,t \neq h(x)$，此时可以验证 $f \setminus \{ (n',t) \}$ 也是一个归纳关系，与最小性矛盾。从而 $f$ 是一个映射，满足 $f(0)=x_{0},f(n')=h(f(n))$.

现在我们可以证明自然数系的同构唯一性。

**定理 1.2.3**

设 $(X,x_{0},s)$ 是一个自然数系，则存在双射 $f\colon \omega \to X$ 满足

$$
\begin{gather*}
\begin{cases}
f(0)=x_{0} \\
f(n')=s(f(n))
\end{cases}
\end{gather*}
$$

首先证明一个引理。

**引理**

设 $m \in \omega,m \neq 0$，则存在 $k \in \omega$ 使得 $k'=m$.

**证明**

令 $\alpha=\{ 0 \} \cup \{ m \in \omega \mid \exists k \in \omega (k'=m) \}$，则 $0 \in \alpha$.

假设 $m \in \alpha$，如果 $m=0$，则显然 $m'=0' \in \alpha$.

如果 $m \neq 0$，则有 $m=k'$，从而 $m'=(k')'$，于是 $m' \in \alpha$.

故 $\alpha=\omega$. 又 $k' \neq 0$，即证 $\{ m \in \omega \mid \exists k \in \omega (k'=m) \}=\omega \setminus \{ 0 \}$.

**证明（1.2.3）**

根据递归原理，存在映射 $f$ 满足定理条件，现证 $f$ 是双射。

考虑集合 $f[\omega] \subset X$，显然 $x_{0} \in f[\omega]$，假设 $x \in f[\omega]$，则有 $n \in \omega$ 使得 $x=f(n)$，从而 $s(x)=s(f(n))=f(n') \in f[\omega]$. 因此 $f[\omega]=X$，即 $f$ 是满射。

任取 $m \in \omega$，对 $n$ 归纳证明 $f(n)=f(m) \implies n=m$.

当 $n=0$ 时，有 $f(m)=x_{0}$，则 $m=0$（否则就有 $m=k'$，从而 $f(m)=s(f(k))=x_{0}$ 矛盾）。

假设 $f(n)=f(m) \implies n=m$，设 $f(n')=f(m)$，则 $m \neq 0$，从而有 $f(n')=f(k')$，即 $s(f(n))=s(f(k))$，于是 $f(n)=f(k)$，根据归纳假设有 $n=k$，从而 $n'=k'=m$. 因此 $f$ 是单射，这就完成了证明。

现在我们已经证明所有的自然数模型都是同构的，因此我们没必要再区分不同的自然数系，通常我们使用 $\omega$ 或者 $\mathbb{N}$ 来指代唯一的那个自然数集。

特别地，$(\mathbb{N},0,s)$ 和 $(\mathbb{N},1,s)$ 就 Peano 的五条公理来说，是同构的。因此“自然数是从 0 开始还是从 1 开始”是一个无意义的问题。它们真正能够被区分的地方在于其上定义的运算，即加法和乘法。

## 加法和乘法

$\mathbb{N}$ 上的加法、乘法等运算都是利用递归原理定义的，具体构造如下：

**定义 1.2.4** 加法（addition）

给定 $m \in \mathbb{N}$，递归地定义 $\mathbb{N}$ 上的**加法**如下：

$$
\begin{gather*}
\begin{cases}
0+m=m \\
n' + m = (n+m)'
\end{cases}
\end{gather*}
$$

将 $f(n)=n+m,h(n)=n'$ 代入 1.2.2，可见上述定义是合理的。

**定义 1.2.5** 乘法（multiplication）

给定 $m \in \mathbb{N}$，递归地定义 $\mathbb{N}$ 上的**乘法**如下：

$$
\begin{gather*}
\begin{cases}
0 \cdot m=0 \\
n' \cdot m=(n \cdot m)+m
\end{cases}
\end{gather*}
$$

现在我们就可以验证如上定义的加法和乘法是符合我们的直观的，即它们满足交换律、结合律、分配律等。

**定理 1.2.6**

设 $k,m,n \in \mathbb{N}$，则有：

1. $m+n'=(m+n)',m \cdot n'=(m \cdot n)+m$.
2. 交换律：$m+n=n+m,mn=nm$.
3. 结合律：$(k+m)+n=k+(m+n),(km)n=k(mn)$.
4. 分配律：$k(m+n)=km+kn$.
5. 消去律：$k+m=k+n\implies m=n$. $km=kn,k\neq 0\implies m=n$.
6. 如果 $mn=0$，则 $m=0$ 或 $n=0$.

**证明**

我们对 $m$ 进行归纳来证明 $m+n'=(m+n)'$.

首先从定义得到 $0+n'=n'=(0+n)'$，且有

$$
m'+n'=(m+n')'=(m+n)''=(m'+n)'
$$

其中第二个等号成立是由于归纳假设。

现在我们证明加法交换律，记该命题为 $P(m,n)$，显然 $P(0,0)$ 成立，接下来我们证明 $P(m,0)\implies P(m',0)$，则有

$$
m'+0=(m+0)'=(0+m)'=0+m'
$$

再证对于任意 $m \in \mathbb{N}$ 有 $P(m,n)\implies P(m,n')$，我们有

$$
m+n'=(m+n)'=(n+m)'=n'+m
$$

综合上述讨论，由归纳公理我们有 $P(m,n)$ 对任意 $m,n \in \mathbb{N}$ 成立。

其它的定律也可以使用类似的归纳法进行证明，限于篇幅，我们将单开一个章节进行证明。

特别地，我们有 $n'=n+1=1+n$ 以及 $n=n \cdot 1=1\cdot n$.

最后我们来定义指数，对于它的性质我们等到定义了有理数后再做研究。

**定义 1.2.7** 乘方（exponentiation）

给定 $m \in \mathbb{N} \setminus \{ 0 \}$，递归地定义 $\mathbb{N}$ 上的**乘方**如下：

$$
\begin{gather*}
\begin{cases}
m^{0}=1 \\
m^{n'}=m^{n} \cdot m
\end{cases}
\end{gather*}
$$

## 序关系

在我们直观的自然数系中，除了加法和乘法，还有大小的概念，即**序关系**，定义如下：

**定义 1.2.7** 序（order）

设 $m,n \in \mathbb{N}$，称 $m$ **小于或等于** $n$，如果存在 $k \in \mathbb{N}$ 使得 $m+k=n$，记作 $m \leq n$. 此时也称 $n$ **大于或等于** $m$，记作 $n \geq m$.

称 $m$ **小于** $n$，如果 $m \leq n$ 且 $m \neq n$，记作 $m<n$. 此时也称 $n$ **大于** $m$，记作 $n>m$.

$\mathbb{N}$ 上的序关系有如下性质：

**定理 1.2.8**

设 $k,m,n \in \mathbb{N}$，则有：

1. 若 $m<n$，则 $m'\leq n$.
2. 反自反性：$n \not< n$.
3. 反对称性：$m\leq n,n\leq m \implies m=n$.
4. 传递性：$k<m,m<n \implies k<n$.
5. 完全性：$m\leq n$ 与 $n\leq m$ 至少有一个成立。
6. 三分律：$m<n,m=n,m>n$ 有且仅有一个成立。
7. 保序性：$m<n\implies k+m<k+n$. $m<n,k\neq 0\implies km<kn$.

同样，为减少篇幅，我们将单开一个章节进行证明。

接下来我们证明 $\mathbb{N}$ 最重要的性质之一：良序原理。

**定理 1.2.9** 良序原理（Well-ordering Principle）

设 $L \subset \mathbb{N}$ 且 $L\neq \varnothing$，则 $L$ 有最小元。

**证明**

令 $M=\{ m \in \mathbb{N} \mid \forall n \in L(m\leq n) \}$，我们要证 $M\cap L\neq \varnothing$. 反设 $M \cap L=\varnothing$，我们有：$0\in M$（因为 $0\leq n$ ）。

设 $m \in M$，则 $\forall n \in L(m\leq n)$. 由于 $M\cap L=\varnothing$，故 $\forall n \in L(m< n)$，从而 $\forall n \in L(m'\leq n)$，即 $m' \in M$. 于是有 $M=\mathbb{N}$，矛盾。

由良序原理我们可以导出以下定理：

**定理 1.2.10** 强归纳法（Strong Induction）

设 $S \subset \mathbb{N}$，$0\in S$ 且 $\forall k<n(k \in S)\implies n \in S$，则 $S=\mathbb{N}$.

**证明**

令 $M=\{ m \in \mathbb{N} \mid m \not\in S \}$，假设 $M \neq \varnothing$，则根据良序原理，$M$ 有最小元 $m$. 因为 $0 \in S$，故 $m\neq 0$，再由 $m$ 的最小性得 $\forall k<m(k \in S)$，根据 $S$ 的定义可知 $m \in S$，矛盾。于是有 $M=\varnothing$.

强归纳法在一些定理的证明中有很大作用，特别是依赖于小于 $n$ 的所有自然数的命题。

经过上述讨论，我们得到了一个扩展的自然数结构 $(\mathbb{N},0,s,+,\cdot,<)$，通常我们所知的自然数就是指这个结构，并且我们还能证明，这种结构是同构唯一的（只要其上定义的运算是本质上相同的）。

具体来说，设 $(X,x_{0},s,+,\cdot,<)$ 是一个自然数结构，那么存在双射 $f\colon \mathbb{N}\to X$ 满足：

$$
\begin{gather*}
\begin{cases}
f(0)=x_{0} \\
f(n')=s(f(n)) \\
f(n+m)=f(n) + f(m) \\
f(n \cdot m)=f(n) \cdot f(m) \\
n<m \implies f(n) < f(m)
\end{cases}
\end{gather*}
$$

这种保持结构的双射我们称为**同构**。

让我们总结一下，我们从最底层的 ZFC 公理出发，逐步构造出了映射、归纳集等概念，然后利用最小归纳集构造了自然数，并在其上定义了加法、乘法、序，形成了结构 $(\mathbb{N},0,s,+,\cdot,<)$，而且，其中的每一步都是严格的。这就是说，我们不必担心自然数的运算律会出错：因为我们已从一些不言自明的公理中**证明**了它们。

下一章我们将利用自然数构造**整数**，与自然数相同，我们将在整数上定义加法和乘法，同样我们也需要证明整数上运算的交换律、结合律等，最后，我们将证明 $\mathbb{N}$ 可以自然地嵌入到整数中，从而完成了一次数系的扩展。在这之后，我们将对整数进行同样的操作，将数系扩展到**有理数**。