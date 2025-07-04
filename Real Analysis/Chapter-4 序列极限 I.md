现在我们已经做好了正式引入极限的准备，首先我们将重新描述之前的一些概念，如 Cauchy 序列、有界序列等，其中用实数替代有理数，首先从实数序列开始。

# Section 1: 收敛序列

**定义 4.1.1** Cauchy 序列

实数序列 $(a_{n})_{n=0}^{\infty}$ 是一个 **Cauchy 序列**如果对任意实数 $\varepsilon>0$，存在 $N \in \mathbb{N}$ 使得对任意 $n,m>N$ 有 $d(a_{n},a_{m})<\varepsilon$.

对比定义 3.1.3 和上述定义，我们可以看到两者的最大区别在于 $\varepsilon$ 是有理数还是实数。然而，根据 $\mathbb{Q}$ 的稠密性，对于实数 $\varepsilon>0$，总存在有理数 $0<\varepsilon_{1}<\varepsilon$，因此一个序列是 3.1.3 意义下的 Cauchy 序列当且仅当它是 4.1.1 意义下的 Cauchy 序列，从而我们不必再区分两种定义，而把它们看作一个统一的概念。这一点也适用于下面的有界序列概念。

**定义 4.1.2** 有界的（bounded）

实数序列 $(a_{n})_{n=0}^{\infty}$ 是**有界的**如果存在实数 $M>0$ 使得对任意 $n \in \mathbb{N}$ 有 $|a_{n}|\leq M$.

接下来我们可以讨论序列的极限是什么意思。

**定义 4.1.3** 极限（limit），收敛（converge），发散（diverge）

设 $(a_{n})_{n=0}^{\infty}$ 是一个实数序列，$L \in \mathbb{R}$，如果对任意 $\varepsilon>0$，存在 $N \in \mathbb{N}$ 使得对任意 $n>N$ 有 $d(a_{n},L)<\varepsilon$，则称 $(a_{n})$ **收敛于** $L$，并称 $(a_{n})$ 的**极限**为 $L$，记作 $\lim_{ n \to \infty } a_{n}=L$. 如果对任意 $L \in \mathbb{R}$，$(a_{n})$ 都不收敛，则称 $(a_{n})$ **发散**。

根据极限的定义，我们可以知道更改、添加、删除一个序列的有限项不会改变序列的收敛性以及其极限（如果有的话），我们只需把 $N$ 取的足够大即可。

下面我们证明收敛序列的极限是唯一的，从而 $\lim_{ n \to \infty } a_{n}$ 这个符号是良定的。

**定理 4.1.4**

设序列 $(a_{n})$ 收敛，则其极限是唯一的。

**证明**

假设 $(a_{n})$ 同时收敛于 $L$ 和 $L'$，那么对任意 $\varepsilon>0$，存在 $N$ 使得对任意 $n>N$ 有 $d(a_{n},L)<\varepsilon$ 和 $d(a_{n},L')<\varepsilon$，于是根据三角不等式有

$$
0\leq d(L,L')\leq d(L,a_{n})+d(a_{n},L')<2\varepsilon
$$

于是 $L=L'$（否则可以取 $\varepsilon=d(L,L')/2$，从而得到矛盾），这就完成了证明。

从上面的证明中我们也可以得到一个有用的推论：如果对任意 $\varepsilon>0$ 有 $0\leq x<\varepsilon$，那么 $x=0$.

作为极限的一个例子，我们给出下面的命题：

**命题 4.1.5**

$\lim_{ n \to \infty } \dfrac{1}{n}=0$

**证明**

取整数 $N\geq 1$，对任意 $n>N$ 我们有

$$
d\left( \dfrac{1}{n},0 \right)=\dfrac{1}{n}<\dfrac{1}{N}
$$

于是，如果我们取 $N>\dfrac{1}{\varepsilon}$（由 Archimedes 性可知这是可行的），我们就有 $d\left( \dfrac{1}{n},0 \right)<\dfrac{1}{N}<\varepsilon$，即 $\lim_{ n \to \infty } \dfrac{1}{n}=0$.

现在我们给出一些收敛序列的基本性质。

**定理 4.1.6**

设序列 $(a_{n})$ 收敛，则 $(a_{n})$ 也是一个 Cauchy 序列。

**证明**

设 $\lim_{ n \to \infty }a_{n}=L$，根据定义，任取 $\varepsilon>0$，存在 $N \in \mathbb{N}$ 使得对任意 $n>N$ 有 $d(a_{n},L)<\varepsilon$. 现在设 $m,n>N$，则我们有

$$
d(a_{n},a_{m})\leq d(a_{n},L)+d(L,a_{m})<2\varepsilon
$$

即 $(a_{n})$ 是一个 Cauchy 序列。

我们之前证明了 Cauchy 序列是有界的，因此我们有如下推论：

**定理 4.1.7**

设序列 $(a_{n})$ 收敛，则 $(a_{n})$ 是有界的。

现在我们来完成构造实数的最后一步：用真正的极限替换形式极限，正如分数替换了形式除法，减法替换了形式减法一样。

**定理 4.1.8**

设 $[(a_{n})]\in \mathbb{R}$，则 $\lim_{ n \to \infty }a_{n}=[(a_{n})]$.

**证明**

设 $x=[(a_{n})]$，假设 $(a_{n})$ 不收敛于 $x$，那么存在一个 $\varepsilon>0$，对任意的 $N$ 都有 $n_{0}>N$ 使得 $d(a_{n_{0}},x)\geq \varepsilon$，即 $a_{n_{0}}\geq x+\varepsilon$ 或 $a_{n_{0}}\leq x-\varepsilon$.

再根据 $(a_{n})$ 是 Cauchy 序列的性质，存在一个 $N$ 使得对任意 $m,n>N$ 有 $d(a_{n},a_{m})<\dfrac{\varepsilon}{2}$，特别地，我们有 $d(a_{n_{0}},a_{m})<\dfrac{\varepsilon}{2}$，因此对 $m>N$ 有 $a_{m}>x+\dfrac{\varepsilon}{2}$ 或者 $a_{m}<x-\dfrac{\varepsilon}{2}$，于是 $[(a_{n})]\geq x+\dfrac{\varepsilon}{2}$ 或者 $[(a_{n})]\leq x-\dfrac{\varepsilon}{2}$. 这与 $x=[(a_{n})]$ 矛盾。

至此，我们就完成了实数的构造：每个实数都是某个有理数序列的极限，结构 $(\mathbb{R},0,1,+,\cdot,<)$ 是一个完备的 Archimedes 序域，并包含 $\mathbb{Q}$ 作为它的子域。确界性质是完备性的一个方面，我们之后还会看到其它的完备性定理。

定理 4.1.8 指出：有理数的 Cauchy 序列收敛，我们可能会猜想对实数序列也有同样的结果。事实上，这个猜想是正确的，然而它的证明比想象中的困难：我们不知道极限值，从而就不能使用极限的定义。我们将在拥有足够多的工具后再来证明它。

下面我们给出极限的代数性质。

**定理 4.1.9**

设序列 $(a_{n}),(b_{n})$ 收敛，则有：

1. $\lim_{ n \to \infty }(a_{n}+b_{n})=\lim_{ n \to \infty }a_{n}+\lim_{ n \to \infty }b_{n}$
2. $\lim_{ n \to \infty } a_{n}b_{n}=(\lim_{ n \to \infty }a_{n})(\lim_{ n \to \infty }b_{n})$
3. 设 $b_{n}\neq 0$ 且 $\lim_{ n \to \infty }b_{n}\neq 0$，则 $\lim_{ n \to \infty } b_{n}^{-1}=(\lim_{ n \to \infty }b_{n})^{-1}$

**证明**

设 $x=\lim_{ n \to \infty }a_{n},y=\lim_{ n \to \infty }b_{n}$，为省略篇幅，下面只给出证明过程中的一些关键步骤。

$$
\begin{gather}
|a_{n}+b_{n}-x-y|\leq |a_{n}-x|+|b_{n}-y|<2\varepsilon \\
|a_{n}b_{n}-xy|\leq |(a_{n}-x)b_{n}|+|x(b_{n}-y)|< (M+|x|)\varepsilon \\
\left| \dfrac{1}{b_{n}}- \dfrac{1}{y} \right| = \dfrac{|b_{n}-y|}{|b_{n}y|}< \dfrac{\varepsilon}{\eta |y|}
\end{gather}
$$

读者可以自行补充剩下的内容。

最后，我们可以把有理数序列等价的定义推广到实数。

**定义 4.1.10** 等价的（equivalent）

两个实数序列 $(a_{n}),(b_{n})$ 是**等价的**如果 $\lim_{ n \to \infty }(a_{n}-b_{n})=0$.

我们可以证明上述定义和定义 3.1.6 是一致的。显然，如果 $(a_{n})$ 收敛，$(a_{n}),(b_{n})$ 等价，则它们收敛于同一个极限。

# Section 2: 广义实数系

现在我们把视线转向发散序列。有些序列，比如 $1,2,3,\dots$ 似乎像是要“收敛”到 $+\infty$，而 $-1,-2,-3,\dots$ “收敛”到 $-\infty$，而另一些，比如 $1,-1,1,-1,\dots$ 则不收敛到任何数。为了精确地描述 $\pm\infty$ 的性质，我们引入**广义实数系**：

**定义 4.2.1** 广义实数系（extended real number system）

**广义实数系** $\mathbb{R}^{*}$ 定义为 $\mathbb{R}\cup \{ +\infty,-\infty \}$，其中对所有 $x \in \mathbb{R}$ 有 $-\infty<x<+\infty$，且 $-(+\infty)=-\infty$. 称 $x \in \mathbb{R}^{*}$ 是**有限的**，如果 $x \in \mathbb{R}$，称 $x \in \mathbb{R}^{*}$ 是**无限的**，如果 $x=+\infty$ 或 $x=-\infty$.

对于 $\pm \infty$，我们只定义它们的序关系以及负运算，这是因为一旦我们将代数运算扩展到 $\mathbb{R}^{*}$ 上，实数运算的一些良好性质就会被破坏。例如，按我们的直观，显然应该有 $+\infty=+\infty+1$，但是 $0\neq 1$，因此加法的消去律不再成立。

对于广义实数的序，我们有下列结论成立：

**定理 4.2.2**

设 $x,y,z \in \mathbb{R}^{*}$，则：

1. 三分律：$x<y,x=y,x>y$ 有且仅有一个成立
2. 传递性：$x<y,y<z \implies x<z$
3. 若 $x<y$，则 $-y< -x$

上述定理的证明对于 $x,y,z \in \mathbb{R}$ 时是显然的，因此只需讨论其中至少有一个无限实数的情况即可，这里不再赘述了。

之前我们定义了 $E \subset \mathbb{R}$ 的上确界，现在我们允许上确界为 $+\infty$，具体定义如下：

**定义 4.2.3** 上确界（supremum），下确界（infimum）

设 $E \subset \mathbb{R}^{*},E\neq \varnothing$，定义 $E$ 的**上确界**如下：

1. 如果 $E \subset \mathbb{R}$ 且有上界，则按照定义 3.3.2 确定 $\sup E$
2. 如果 $+\infty \in E$ 或者 $E \subset \mathbb{R}$ 且无上界，则定义 $\sup E=+\infty$
3. 如果 $-\infty \in E,+\infty \not\in E$，则定义 $\sup E=\sup (E\setminus \{ -\infty \})$

定义 $E$ 的**下确界**为 $\inf E=-\sup(-E)$，其中 $-E=\{ -x \mid x \in E \}$.

当 $E=\varnothing$ 时，定义 $\sup E=-\infty,\inf E=+\infty$.

空集要单独拿出来的原因是，事实上，每一个 $x \in \mathbb{R}$ 都是空集的上界和下界（可以使用反证法证明），因此上确界，作为最小上界，最合理的定义就是 $-\infty$，这也是唯一使得 $\sup E<\inf E$ 的情况。

下面我们验证上述定义符合上下确界的性质。

**定理 4.2.4**

设 $E \subset \mathbb{R}^{*},E\neq \varnothing$，则有：

1. 对任意 $x \in E$ 有 $\inf E\leq x\leq \sup E$
2. 设 $M \in \mathbb{R}^{*}$ 是 $E$ 的一个上界，则 $\sup E\leq M$
3. 设 $L \in \mathbb{R}^{*}$ 是 $E$ 的一个下界，则 $L\leq \inf E$

上述定理与 4.2.2 一样，只需讨论含有无限实数的情况。

我们引入广义实数系的目的是使每个集合都有上确界，在我们的研究中通常只会涉及实数序列，以及实数序列的上下确界。

**定义 4.2.5** 序列的上确界和下确界

设 $(a_{n})_{n=0}^{\infty}$ 是一个实数序列，$I \subset \mathbb{N}$，定义

$$
\begin{gather}
\sup_{n \in I} a_{n}=\sup \{ a_{n} \mid n \in I \} \\
\inf_{n \in I} a_{n}=\inf \{ a_{n} \mid n \in I \}
\end{gather}
$$

当 $I=\mathbb{N}$ 时，可以简记为 $\sup a_{n}$ 及 $\inf a_{n}$.

之前我们看到，收敛序列都是有界的，但有界序列不一定收敛。然而，如果一个序列是有界且单调的，那么它一定收敛。首先我们给出单调序列的定义。

**定义 4.2.6** 单调递增的（monotone increasing），单调递减的（monotone decreasing）

设 $(a_{n})_{n=0}^{\infty}$ 是一个实数序列，称 $(a_{n})$ 是**单调递增的**，如果对任意 $n \in \mathbb{N}$ 有 $a_{n}\leq a_{n+1}$，称 $(a_{n})$ 是**单调递减的**，如果对任意 $n \in \mathbb{N}$ 有 $a_{n}\geq a_{n+1}$.

把上述不等号换成 $<$ 或 $>$ 就得到了**严格单调递增/递减**的定义。

下面我们给出关于序列的上下确界的一个应用。

**定理 4.2.7** 单调收敛定理

设实数序列 $(a_{n})$ 在 $\mathbb{R}$ 中有上界，且 $(a_{n})$ 单调递增，则 $(a_{n})$ 收敛，且 $\lim_{ n \to \infty }a_{n}=\sup a_{n}$.

**证明**

由 $\mathbb{R}$ 的确界性质，可以取 $x=\sup a_{n}\in \mathbb{R}$，根据上确界的定义，对任意 $\varepsilon>0$，存在 $N\in \mathbb{N}$ 使得 $x-\varepsilon<a_{N}\leq x$. 由于 $(a_{n})$ 单调递增，因此对任意 $n>N$ 有 $x-\varepsilon<a_{N}\leq a_{n}\leq x$，从而 $d(a_{n},x)<\varepsilon$，即 $\lim_{ n \to \infty }a_{n}=x$.

同理，对于单调递减的序列，我们可以证明与之相对应的单调收敛定理。

单调收敛定理是非常有用的一个定理，因为使用它不要求我们提前知道极限的值。一旦我们知道某个序列收敛，我们就可以使用极限的代数性质快速地求出极限。我们用一个例子来说明这一点。

**命题 4.2.8**

设 $0\leq x<1$，则 $\lim_{ n \to \infty }x^{n}=0$

**证明**

$x=0$ 是显然的，设 $0<x<1$，则序列 $(x^{n})$ 单调递减，且有下界 $0 \in \mathbb{R}$，则 $(x^{n})$ 收敛。由于 $x^{n+1}=x\cdot x^{n}$，两边取极限得 $L=xL$，解得 $L=0$.

最后我们来给出极限为 $\pm \infty$ 的定义。

**定义 4.2.9** 无穷极限

设 $(a_{n})$ 是一个实数序列，如果对任意 $M>0$，存在 $N\in \mathbb{N}$ 使得对任意 $n>N$ 有 $a_{n}>M$，则称 $(a_{n})$ **发散至** $+\infty$，并称 $(a_{n})$ 的**极限**为 $+\infty$，记作 $\lim_{ n \to \infty }a_{n}=+\infty$. 如果 $a_{n}< -M$，则称 $(a_{n})$ 发散至 $-\infty$，并称 $(a_{n})$ 的极限为 $-\infty$，记作 $\lim_{ n \to \infty }a_{n}=-\infty$.

无穷极限在一些方面与有限极限具有相似的性质，读者可以自行推导。

# Section 3: 上极限与下极限

我们考虑序列 $1.1,-1.01,1.001,-1.0001,\dots$，它显然不是收敛序列，但是序列中的一半元素似乎正在“趋近于” $1$，而另一半“趋近于” $-1$. 为了描述这种现象，我们给出下面的定义：

**定义 4.3.1** 序列的附着点（adherent point）

设 $(a_{n})_{n=0}^{\infty}$ 是一个实数序列，$x \in \mathbb{R}$，称 $x$ 是 $(a_{n})$ 的**附着点**，如果对任意 $\varepsilon>0$ 和 $N \in \mathbb{N}$，存在 $n>N$ 使得 $d(a_{n},x)<\varepsilon$. 如果 $\sup a_{n}=+\infty$，则称 $+\infty$ 是 $(a_{n})$ 的一个附着点，如果 $\inf a_{n}=-\infty$，则称 $-\infty$ 是 $(a_{n})$ 的一个附着点。

对于前面的序列来说，$1$ 和 $-1$ 就是它的两个附着点。注意附着点与极限的区别：附着点只需要存在 $n>N$ 使得 $d(a_{n},x)<\varepsilon$，而极限需要对任意 $n>N$ 有 $d(a_{n},x)<\varepsilon$，因此，附着点实际上是一种弱化的极限。

**定理 4.3.2**

设 $x \in \mathbb{R}$，且序列 $(a_{n})$ 收敛于 $x$，则 $x$ 是 $(a_{n})$ 的唯一附着点。

**证明**

显然 $x$ 是 $(a_{n})$ 的附着点，假设 $(a_{n})$ 另有附着点 $y \neq x$，取 $\varepsilon=\dfrac{|y-x|}{2}$，则存在 $N$ 使得对任意 $n>N$ 有 $d(a_{n},x)<\varepsilon$，于是对于这个 $N$，不存在 $n>N$ 使得 $d(a_{n},y)<\varepsilon$，这与 $y$ 是附着点矛盾。

一个序列不一定有极限，但是它一定有附着点，下面我们给出两种特殊的附着点。

**定义 4.3.3** 上极限（limit superior），下极限（limit inferior）

设 $(a_{n})_{n=0}^{\infty}$ 是一个实数序列，定义序列 $(a_{n}^{+}),(a_{n}^{-})$ 为

$$
\begin{gather}
a_{n}^{+}=\sup_{k\geq n} a_{k} \\
a_{n}^{-}=\inf_{k\geq n} a_{k}
\end{gather}
$$

定义 $(a_{n})$ 的**上极限**和**下极限**分别为

$$
\begin{gather}
\limsup_{ n \to \infty } a_{n}=\inf a_{n}^{+} \\
\liminf_{ n \to \infty } a_{n}=\sup a_{n}^{-}
\end{gather}
$$

直观地来看，序列 $(a_{n}^{+})$ 的第一项给出了 $a_{0},a_{1},\dots$ 的上确界，第二项给出了 $a_{1},a_{2},\dots$ 的上确界，下一项是 $a_{2},a_{3},\dots$ 的上确界，等等。显然，$(a_{n}^{+})$ 是单调递减的。注意，$a_{n}^{+}$ 可以是广义实数，比如 $1,2,3,\dots$ 的 $a_{n}^{+}=+\infty$，此时 $\limsup_{ n \to \infty }a_{n}=+\infty$.

下面我们给出上下极限的一些性质。

**定理 4.3.4**

设 $(a_{n})_{n=0}^{\infty}$ 是一个实数序列，$L^{+},L^{-}\in \mathbb{R}$ 是 $(a_{n})$ 的上极限和下极限，则：

1. 对任意 $\varepsilon>0$，存在 $N \in \mathbb{N}$ 使得对任意 $n>N$ 有 $a_{n}<L^{+}+\varepsilon$. 类似地，对任意 $n>N$ 有 $a_{n}>L^{-}-\varepsilon$.
2. 对任意 $\varepsilon>0$ 和 $N \in \mathbb{N}$，存在 $n>N$ 使得 $a_{n}>L^{+}-\varepsilon$. 类似地，存在 $n>N$ 使得 $a_{n}<L^{-}+\varepsilon$.
3. $\inf a_{n}\leq L^{-}\leq L^{+}\leq \sup a_{n}$
4. 设 $x \in \mathbb{R}$ 是 $(a_{n})$ 的附着点，则 $L^{-}\leq x\leq L^{+}$
5. 设 $L\in \mathbb{R}$，则 $(a_{n})$ 收敛于 $L$ 当且仅当 $L^{+}=L^{-}=L$

**证明**

对于 1 我们只证关于上极限的性质，下极限同理。任取 $\varepsilon>0$，有 $L^{+}=\inf a_{n}^{+}<L^{+}+\varepsilon$，则存在 $N$ 使得 $a_{N}^{+}=\sup_{k\geq N}a_{k}<L^{+}+\varepsilon$，即对任意 $n\geq N$，有 $a_{n}<L^{+}+\varepsilon$，即证。

同样，对于 2 我们只证上极限的部分。任取 $\varepsilon>0$，有 $L^{+}-\varepsilon<\inf a_{n}^{+}$，则对任意 $N\in \mathbb{N}$，有 $L^{+}-\varepsilon<a_{N}^{+}=\sup_{k\geq N}a_{k}$，则存在 $n\geq N$ 使得 $L^{+}-\varepsilon<a_{n}$，即证。

1 和 2 表明，$L^{+}$ 和 $L^{-}$ 是 $(a_{n})$ 的附着点。对于 3，第一和第三个不等式是显然的，现在来证 $L^{-}\leq L^{+}$. 假设 $L^{-}>L^{+}$，令 $\varepsilon=\dfrac{L^{-}-L^{+}}{2}$，存在 $N$ 使得对任意 $n>N$ 有 $a_{n}>L^{-}-\varepsilon$，而此时也有 $a_{n}<L^{+}+\varepsilon$，矛盾。

对于 4，不妨假设 $x>L^{+}$，令 $\varepsilon=\dfrac{x-L^{+}}{2}$ 再使用 1 可以导出矛盾，因此 $x\leq L^{+}$，同理也可以证明 $x\geq L^{-}$，因此 $L^{-}\leq x\leq L^{+}$. 4 表明，上极限是最大的附着点，下极限是最小的附着点。由此再根据 4.3.2 可以证明 5 的一个方面。

另一方面，设 $L^{+}=L^{-}=L$，则对任意 $\varepsilon>0$ 存在 $N$ 使得对任意 $n>N$ 有 $L-\varepsilon<a_{n}<L+\varepsilon$，即 $\lim_{ n \to \infty }a_{n}=L$. 这就完成了证明。

上述定理的 3 和 4 可以自然地推广到广义实数上，从而 $L^{+}$ 是最大的附着点，$L^{-}$ 是最小的附着点。

上下极限给了我们一种判断收敛性的方法：计算上下极限，看它们是否相等。

下面我们考虑多个序列的序关系。

**定理 4.3.5** 比较准则

设实数序列 $(a_{n})_{n=0}^{\infty},(b_{n})_{n=0}^{\infty}$ 满足对任意 $n\in \mathbb{N}$ 有 $a_{n}\leq b_{n}$，则：

1. $\sup a_{n}\leq \sup b_{n},\inf a_{n}\leq \inf b_{n}$
2. $\limsup_{ n \to \infty }a_{n}\leq \limsup_{ n \to \infty }b_{n},\liminf_{ n \to \infty }a_{n}\leq \liminf_{ n \to \infty }b_{n}$

**证明**

我们只证明关于上确界的部分，下确界同理。假设 $\sup a_{n}>\sup b_{n}$，根据上确界的定义，存在 $n$ 使得 $b_{n}\leq \sup b_{n}<a_{n}$，矛盾。

再假设 $A^{+}=\limsup_{ n \to \infty }a_{n}>\limsup_{ n \to \infty }b_{n}=B^{+}$，取 $\varepsilon=\dfrac{A^{+}-B^{+}}{2}$，存在 $N$ 使得对任意 $n>N$ 有 $b_{n}<B^{+}+\varepsilon$，而对于 $N$ 存在 $n>N$ 使得 $a_{n}>A^{+}-\varepsilon>b_{n}$，矛盾。

从上述定理我们可以得到下面的常用判别定理：

**定理 4.3.6** 挤压定理（squeeze theorem）

设实数序列 $(a_{n}),(b_{n}),(c_{n})$ 满足对任意 $n \in \mathbb{N}$ 有 $a_{n}\leq b_{n}\leq c_{n}$，且 $(a_{n})$ 和 $(c_{n})$ 收敛于 $L$，则 $(b_{n})$ 也收敛于 $L$.

**证明**

根据 4.3.5，我们有 $L\leq \limsup_{ n \to \infty }b_{n}\leq L$，即 $\limsup_{ n \to \infty }b_{n}=L$，同理 $\liminf_{ n \to \infty }b_{n}=L$，于是 $\lim_{ n \to \infty }b_{n}=L$.

将单调收敛定理和挤压定理结合使用，我们就可以计算出大量的极限。下面我们给出一个应用。

**定理 4.3.7**

设 $(a_{n})$ 是实数序列，则 $\lim_{ n \to \infty }a_{n}=0$ 当且仅当 $\lim_{ n \to \infty }|a_{n}|=0$.

**证明**

设 $\lim_{ n \to \infty }a_{n}=0$，则对任意 $\varepsilon>0$，存在 $N$ 使得对任意 $n>N$ 有 $|a_{n}|<\varepsilon$，由于 $||a_{n}||=|a_{n}|$，故 $\lim_{ n \to \infty }|a_{n}|=0$.

反之，由于 $-|a_{n}|\leq a_{n}\leq |a_{n}|$，而 $(-|a_{n}|),(|a_{n}|)$ 都收敛于 $0$，则 $\lim_{ n \to \infty }a_{n}=0$.

使用上述定理，我们可以证明对任意 $-1<x<1$ 有 $\lim_{ n \to \infty }x^{n}=0$.

最后，我们来证明改良后的定理 4.1.8.

**定理 4.3.8** $\mathbb{R}$ 的完备性，Cauchy 准则

实数序列 $(a_{n})$ 在 $\mathbb{R}$ 中有极限当且仅当 $(a_{n})$ 是 Cauchy 序列。

**证明**

我们已证明了收敛序列是 Cauchy 序列。现设 $(a_{n})$ 是 Cauchy 序列，则 $(a_{n})$ 是有界的，于是 $(a_{n})$ 的附着点都是有限实数，特别地，上下极限 $L^{+},L^{-}\in \mathbb{R}$，现在我们只需证明 $L^{+}=L^{-}$.

任取 $\varepsilon>0$，存在 $N$ 使得对任意 $n,m>N$ 有 $d(a_{n},a_{m})<\varepsilon$，特别地，有 $a_{N+1}-\varepsilon<a_{n}<a_{N+1}+\varepsilon$，从而

$$
a_{N+1}-\varepsilon\leq \inf_{k\geq N+1}a_{k}\leq L^{-}\leq L^{+} \leq \sup_{k\geq N+1}a_{k}\leq a_{N+1}+\varepsilon
$$

即 $0\leq L^{+}-L^{-}\leq 2\varepsilon$，则 $L^{+}=L^{-}$，这就完成了证明。

定理 4.3.8 是实数完备性的一个体现，事实上，它和 $\mathbb{R}$ 的确界性质是等价的。我们之后还会看到其它等价定理。

我们以几个基本极限结束本章的讨论。

**命题 4.3.9**

设有理数 $q>0$，则 $\lim_{ n \to \infty } \dfrac{1}{n^{q}}=0$

**证明**

序列 $\left( \dfrac{1}{n^{q}} \right)_{n=1}^{\infty}$ 单调递减且有下界 $0$，因此它收敛，设极限为 $L$. 首先我们设 $q=\dfrac{1}{b}$，则 $L^{b}=\lim_{ n \to \infty }\dfrac{1}{n}=0$，然后设 $q=\dfrac{a}{b}$，则 $L=\left( \lim_{ n \to \infty } \dfrac{1}{n^{1/b}} \right)^{a}=0$.

**命题 4.3.10**

当 $|x|<1$ 时，$\lim_{ n \to \infty }x^{n}=0$，当 $x=1$ 时，$\lim_{ n \to \infty }x^{n}=1$，当 $x=-1$ 或 $|x|>1$ 时，$(x^{n})$ 发散。

**证明**

$|x|<1$ 的情况我们已证过了，$x=1$ 是显然的。当 $x=-1$ 时，$\limsup_{ n \to \infty }x^{n}=1,\liminf_{ n \to \infty }x^{n}=-1$，因此 $(x^{n})$ 发散。

当 $|x|>1$ 时，假设 $(|x|^{n})$ 收敛，则 $1=(\lim_{ n \to \infty }|x|^{n})(\lim_{ n \to \infty }|x|^{-n})$，但 $\lim_{ n \to \infty } \dfrac{1}{|x|^{n}}=0$，矛盾。因此 $(|x|^{n})$ 发散，从而 $(x^{n})$ 发散（可以证明其逆否命题）。

**命题 4.3.11**

设实数 $x>0$，则 $\lim_{ n \to \infty }x^{1/n}=1$

**证明**

$x=1$ 是显然的。设 $x>1$，序列 $(x^{1/n})$ 单调递减且有下界 $1$，故收敛。下证 $\inf(x^{1/n})=1$. 任取 $\varepsilon>0$，由于 $((1+\varepsilon)^{n})$ 发散至 $+\infty$，故对任意 $M>1$，存在 $n$ 使得 $(1+\varepsilon)^{n}>M$，即 $1<M^{1/n}<1+\varepsilon$，因此 $1+\varepsilon$ 不是下界，从而 $\lim_{ n \to \infty }x^{1/n}=\inf(x^{1/n})=1$.

设 $x<1$，序列 $(x^{1/n})$ 单调递增且有上界 $1$，故收敛。设极限为 $L$，则 $L=L\left( \lim_{ n \to \infty }\left( \dfrac{1}{x^{1/n}} \right) \right)=1$.