在上一章中，我们回顾了一元微分学，与之相对的自然就是积分学了，它是本章我们研究的主要内容。更准确地说，我们要研究的是**定积分**，它与不定积分，也称为原函数相对应。将微分学与积分学联系起来的是微积分基本定理（Newton-Leibniz 公式），我们将在之后对其进行研究。

我们将从区间 $I$ 以及函数 $f\colon I\to \mathbb{R}$ 开始研究积分。我们将为它们赋予一个值 $\int_{I}f$，通常会写成 $\int_{I}f(x)\mathrm{d}x$ 或者 $\int_{a}^{b}f(x)\mathrm{d}x$，如果区间的端点是 $a$ 和 $b$.

事实上，有两种方法可以用来定义定积分：Riemann 积分和 Lebesgue 积分。Riemann 积分比较容易计算，并且它可以满足绝大多数场景的应用，而 Lebesgue 积分可以取代 Riemann 积分并推广至更多类型的函数。在分析学更深入的理论中，我们用的几乎都是 Lebesgue 积分。

我们将采用一种“Lebesgue 式”的方法来定义 Riemann 积分：首先我们考虑一种非常简单的函数，即**分段常值函数**（这对应于 Lebesgue 积分中的**简单函数**），对它们来定义 Riemann 积分是容易的，然后我们可以去处理更一般的函数，用分段常值函数去逼近它们，这样我们就可以得到一般函数的 Riemann 积分理论。

# Section 1: 划分

在引入积分前，我们需要研究如何把一个区间划分为几个小区间，我们首先给出以下定义：

**定义 12.1.1** 连通的（connected）

设 $X\subset \mathbb{R}$，称 $X$ 是**连通的**，如果对任意 $x,y \in X,x<y$ 有 $[x,y]\subset X$.

之后，我们将定义一个更一般的连通性的概念，它可以推广至其它空间。一个有界区间 $(a,b)$ 显然是连通的，并且空集 $\varnothing$ 和单点集 $\{ x \}$ 也是连通的（因为在这两个集合中找不到两个元素使得 $x<y$ ）。

**定理 12.1.2**

设 $X\subset \mathbb{R}$，则以下两个命题等价：

1. $X$ 是有界且连通的
2. $X$ 是一个有界区间

**证明**

显然 $2\implies 1$，现在假设 $X$ 是有界且连通的。如果 $X$ 是空集或者单点集，那么 $X$ 是一个退化的区间。如果 $X$ 不是空集或单点集，那么令 $L=\inf X,M=\sup X$，则 $L<M$，设 $L<x<M$，我们要证 $x \in X$.

根据上下确界的定义，对任意正整数 $n$，总存在 $y,z \in X$ 使得 $M-\dfrac{1}{n}<y\leq M,L\leq z<L+\dfrac{1}{n}$，由 $X$ 的连通性得 $[y,z]\subset X$，由于 $L<x<M$，因此必然存在 $n$ 使得 $L+\dfrac{1}{n}<x<M-\dfrac{1}{n}$，从而 $x \in[y,z]\subset X$，因此 $(L,M)\subset X$，于是 $X$ 必然是 $(L,M),[L,M),(L,M],[L,M]$ 其中之一，这就完成了证明。

我们研究 Riemann 积分时几乎总是在有界区间上。下面我们需要给每个区间定义一个长度。

**定义 12.1.3** 区间的长度（length）

设 $I$ 是一个有界区间，定义 $I$ 的**长度** $|I|$ 如下：如果有实数 $a<b$ 使得 $I$ 是 $(a,b),(a,b],[a,b),[a,b]$ 其中之一，则定义 $|I|=b-a$；如果 $I$ 是空集或单点集，则定义 $|I|=0$.

下面我们来定义区间的划分。

**定义 12.1.4** 区间的划分（partition）

设 $I$ 是一个有界区间，有限集合 $\mathbf{P}\subset \mathscr{P}(I)$ 是 $I$ 的一个**划分**，如果：

1. $\mathbf{P}$ 的元素是有界区间
2. $\bigcup \mathbf{P}=I$
3. 对任意 $J,K \in \mathbf{P}$，如果 $J\neq K$，则 $J\cap K=\varnothing$.

例如，区间 $[0,2]$ 的一个划分为 $\{ \varnothing,\{ 0 \},(0,1),[1,2] \}$，我们可以注意到将空集从 $\mathbf{P}$ 中去除后得到的集合仍然是一个划分。

下面我们给出长度的一个基本性质，通常称为“有限可加性”。

**定理 12.1.5**

设 $I$ 是一个有界区间，$\mathbf{P}$ 是 $I$ 的一个划分，那么

$$
|I|=\sum_{J \in \mathbf{P}} |J|
$$

**证明**

注意到 $\mathbf{P}$ 是有限集，因此我们可以对 $\mathbf{P}$ 的元素个数进行归纳。当 $|\mathbf{P}|=0$ 时，显然此时 $I=\varnothing$，结论成立。当 $|P|=1$ 时，显然有 $\mathbf{P}=\{ I \}$，结论也成立。假设 $|\mathbf{P}|=n$ 时结论成立，现在考虑 $|\mathbf{P}|=n+1$ 的情况。

如果 $I$ 是空集或单点集，那么 $|I|=0$ 并且对所有 $J\in \mathbf{P}$ 有 $|J|=0$，故结论成立。现设 $I$ 是一个非退化的区间，其端点为 $a<b$.

如果 $b \in I$，那么存在 $K\in \mathbf{P}$ 使得 $b \in K$，并且 $K$ 一定是区间 $\{ b \},(c,b],[c,b]$ 之一，从而 $I\setminus K$ 是 $(a,c],[a,c],(a,c),[a,c)$ 之一，无论哪种情况，都有

$$
|I|=|K|+|I\setminus K|
$$

由于 $|\mathbf{P}\setminus \{ K \}|=n$，故由归纳假设有 $|I\setminus K|=\sum_{J \in \mathbf{P}\setminus \{ K \}}|J|$，从而

$$
|I|=\sum_{J \in \mathbf{P}} |J|
$$

$b\not\in I$ 的情况同理，这就完成了证明。

关于区间的划分，我们还需要知道，在什么时候，一个划分比另一个更精细，这种不断加细的过程正是极限发挥作用之处。

**定义 12.1.6** 更细的划分（finer partition）

设 $I$ 是一个有界区间，$\mathbf{P},\mathbf{P}'$ 是 $I$ 的两个划分，称 $\mathbf{P}'$ 比 $\mathbf{P}$ **更细**（或称 $\mathbf{P}$ 比 $\mathbf{P}'$ **更粗糙**），如果对任意 $J \in \mathbf{P}'$ 都存在 $K\in \mathbf{P}$ 使得 $J\subset K$.

定义 $\mathbf{P},\mathbf{P}'$ 的**公共加细**为集合

$$
\{ K\cap J \mid K \in \mathbf{P},J \in \mathbf{P}' \}
$$

显然，$\mathbf{P},\mathbf{P}'$ 的公共加细比 $\mathbf{P}$ 更细，也比 $\mathbf{P}'$ 更细。

我们以一个例子来说明这一点。例如，在区间 $[0,4]$ 的所有划分中，$\{ [0,4] \}$ 是最粗糙的，而 $\{ [0,2],(2,4] \}$ 比 $\{ [0,4] \}$ 更细，并且 $\{ [0,1),[1,2],(2,3],(3,4] \}$ 比 $\{ [0,2],(2,4] \}$ 更细。

# Section 2: 分段常值积分

现在我们描述一类非常简单的函数，对它们积分非常容易。

**定义 12.2.1** 分段常值函数（piecewise constant function）

设 $I$ 是一个有界区间，函数 $f\colon I\to \mathbb{R}$，如果存在 $I$ 的一个划分 $\mathbf{P}$，使得对任意 $J \in \mathbf{P}$，$f$ 在 $J$ 上的限制函数 $f|_{J}$ 是常值函数，则称 $f$ 是 $I$ 上关于 $\mathbf{P}$ 的**分段常值函数**。

显然，如果 $f$ 关于 $\mathbf{P}$ 是分段常值的，并且如果 $\mathbf{P}'$ 比 $\mathbf{P}$ 更细，那么 $f$ 关于 $\mathbf{P}'$ 也是分段常值的。从而我们可以证明以下定理：

**定理 12.2.2**

设 $I$ 是有界区间，函数 $f\colon I\to \mathbb{R},g\colon I\to \mathbb{R}$ 是分段常值函数，则：

1. $f+g$ 是分段常值函数
2. $fg$ 是分段常值函数
3. 如果对任意 $x \in I$ 有 $g(x)\neq 0$，那么 $\dfrac{1}{g}$ 是分段常值函数

**证明**

设 $f$ 关于 $\mathbf{P}_{1}$ 是分段常值的，$g$ 关于 $\mathbf{P}_{2}$ 是分段常值的，取 $\mathbf{P}$ 为 $\mathbf{P}_{1},\mathbf{P}_{2}$ 的公共加细，那么 $f+g,fg$ 关于 $\mathbf{P}$ 是分段常值的。如果 $g(x)\neq 0$，那么 $\dfrac{1}{g}$ 关于 $\mathbf{P}_{2}$ 也是分段常值的。

现在我们来定义分段常值函数的积分。

**定义 12.2.3** 分段常值积分（piecewise constant integral）

设 $I$ 是有界区间，函数 $f\colon I\to \mathbb{R}$ 关于 $I$ 的划分 $\mathbf{P}$ 是分段常值函数，定义 $f$ 关于 $\mathbf{P}$ 的**积分**为

$$
\int_{\mathbf{P}} f=\sum_{J \in \mathbf{P}} c_{J}|J|
$$

其中 $c_{J}$ 是 $f$ 在 $J$ 上的常数值。

上面的定义中需要注意一点：当 $J=\varnothing$ 时，我们可以为 $c_{J}$ 赋予任意实数，然而此时 $|J|=0$，故 $c_{J}$ 的选取不会影响积分的值。

下面我们证明：分段常值函数积分的值与划分 $\mathbf{P}$ 的选取无关。

**定理 12.2.4**

设 $I$ 是有界区间，函数 $f\colon I\to \mathbb{R}$，如果 $\mathbf{P},\mathbf{P}'$ 都是 $I$ 的划分，并且 $f$ 关于 $\mathbf{P}$ 和 $\mathbf{P}'$ 都是分段常值函数，那么

$$
\int_{\mathbf{P}}f=\int_{\mathbf{P}'}f
$$

**证明**

设 $\mathbf{P}''$ 是 $\mathbf{P},\mathbf{P}'$ 的公共加细，那么 $f$ 关于 $\mathbf{P}''$ 也是分段常值的，从而

$$
\int_{\mathbf{P}}f=\sum_{K \in \mathbf{P}}c_{K}|K|=\sum_{K \in \mathbf{P}}c_{K} \sum_{J\subset K;J \in \mathbf{P}''}|J|=\sum_{J \in \mathbf{P}''}c_{J}|J|=\int_{\mathbf{P}''}f
$$

同理也有 $\int_{\mathbf{P}'}f=\int_{\mathbf{P}''}f$，这就完成了证明。

根据上述定理，我们就可以定义：

**定义 12.2.5** 分段常值积分（piecewise constant integral）

设 $I$ 是有界区间，函数 $f\colon I\to \mathbb{R}$ 是分段常值函数，定义 $f$ 的**积分**为

$$
\int_{I}f=\int_{\mathbf{P}}f
$$

其中 $\mathbf{P}$ 是 $I$ 的任意划分，使得 $f$ 关于 $\mathbf{P}$ 是分段常值函数。

例如，设函数 $f\colon [0,3]\to \mathbb{R}$ 定义为

$$
f(x)=\begin{cases}
1 &, 0\leq x<2 \\
2 &, 2\leq x\leq 3
\end{cases}
$$

那么 $f$ 是分段常值的，并且 $\int_{[0,3]}f=\int_{0}^{3}f=1\cdot 2+2\cdot 1=4$.

下面我们给出分段常值函数积分的基本性质，它们最终会被 Riemann 积分的性质所取代。

**定理 12.2.6**

设 $I$ 是有界区间，函数 $f\colon I\to \mathbb{R},g\colon I\to \mathbb{R}$ 是分段常值函数，则有：

1. 线性性：$\int_{I}(af+bg)=a \int_{I}f+b \int_{I}g$
2. 比较准则：如果对任意 $x \in I$ 有 $f(x)\leq g(x)$，那么 $\int_{I}f\leq \int_{I}g$
3. 设 $I\subset J$，函数 $F\colon J\to \mathbb{R}$ 定义为 $$
F(x)=\begin{cases}
f(x) &, x \in I \\
0 &, x \not\in I
\end{cases}
$$ 则 $F$ 是分段常值函数，并且 $\int_{J}F=\int_{I}f$
4. 设 $\{ J,K \}$ 是 $I$ 的划分，那么 $f|_{J}$ 和 $f|_{K}$ 都是分段常值函数，并且 $\int_{I}f=\int_{J}f|_{J}+\int_{K}f|_{K}$

**证明**

取 $I$ 的一个划分 $\mathbf{P}$ 使得 $f,g$ 关于 $\mathbf{P}$ 是分段常值的（这是可行的，参考定理 12.2.2 的证明），从而

$$
\int_{I}(af+bg)=\sum_{J \in \mathbf{P}}(ac_{J}+bd_{J})|J|=a\int_{I}f+b\int_{I}g
$$

设对任意 $x \in I$ 有 $f(x)\leq g(x)$，令 $h=g-f$，那么 $h(x)\geq 0$，从而

$$
\int_{I}h=\sum_{J \in \mathbf{P}}e_{J}|J|\geq 0
$$

即 $\int_{I}f\leq \int_{I}g$.

任取 $J$ 的一个划分 $\mathbf{P}'$，我们取 $\mathbf{P},\mathbf{P}'$ 的公共加细 $\mathbf{P}''$，则 $F$ 关于 $\mathbf{P}''$ 是分段常值的，并且

$$
\int_{J}F=\sum_{K \subset I;K \in \mathbf{P}''}c_{K}|K|+\sum_{K\subset J\setminus I;K \in \mathbf{P}''} 0\cdot |K|=\int_{I}f
$$

最后，令

$$
\mathbf{P}_{1}=\{ J\cap L \mid L \in \mathbf{P} \},\mathbf{P}_{2}=\{ K\cap L \mid L \in \mathbf{P} \}
$$

则 $\mathbf{P}_{1}\cup \mathbf{P}_{2}$ 是 $I$ 的一个比 $\mathbf{P}$ 更细的划分，并且

$$
\int_{I}f=\sum_{J' \in \mathbf{P}_{1}}c_{J'}|J'|+\sum_{K' \in \mathbf{P}_{2}}c_{K'}|K'|=\int_{J}f|_{J}+\int_{K}f|_{K}
$$

这就完成了证明。

# Section 3: 有界函数的积分

设 $f\colon I\to \mathbb{R}$ 是有界函数，我们想要定义 $f$ 的 Riemann 积分，为此，我们首先需要定义 $f$ 的上 Riemann 积分以及下 Riemann 积分，它们所扮演的角色就类似于上下极限之于极限。

**定义 12.3.1** 控制函数（dominant function）

设 $I$ 是有界区间，函数 $f\colon I\to \mathbb{R},g\colon I\to \mathbb{R}$，如果对任意 $x \in I$ 有 $f(x)\leq g(x)$，则称 $g$ 在 $I$ 上**从上方控制** $f$，并称 $f$ 在 $I$ 上**从下方控制** $g$.

所谓“用分段常值函数逼近一般函数”，就是指使用分段常值函数从上方和下方控制 $f$，这就是上下 Riemann 积分的思路。

**定义 12.3.2** 上 Riemann 积分，下 Riemann 积分

设 $I$ 是有界区间，函数 $f\colon I\to \mathbb{R}$ 是有界函数，则定义**上 Riemann 积分**为

$$
\overline{\int_{I}}f=\inf \left\{  \int_{I}g \middle| g \text{是从上方控制} f \text{的分段常值函数}  \right\}
$$

定义**下 Riemann 积分**为

$$
\underline{\int_{I}}f=\sup \left\{  \int_{I}g \middle| g \text{是从下方控制} f \text{的分段常值函数}  \right\}
$$

对于上、下积分，我们有一个常用的估计：

**定理 12.3.3**

设 $I$ 是有界区间，函数 $f\colon I\to \mathbb{R}$ 是有界函数，并且对任意 $x \in I$ 有 $|f(x)|\leq M$，则

$$
-M|I| \leq \underline{\int_{I}}f \leq \overline{\int_{I}}f \leq M|I|
$$

**证明**

定义为 $g(x)=M$ 的函数 $g\colon I\to \mathbb{R}$ 从上方控制 $f$，并且 $\int_{I}g=M|I|$，故由定义得 $\overline{\int_{I}}f\leq M|I|$，同理有 $-M|I|\leq \underline{\int_{I}}f$. 最后我们要证明上积分大于等于下积分。

设 $g$ 从上方控制 $f$，$h$ 从下方控制 $f$，从而对任意 $x \in I$ 有 $h(x)\leq f(x)\leq g(x)$，则有 $\int_{I}h\leq \int_{I}g$，对 $h$ 取上确界，则 $\underline{\int_{I}}f\leq \int_{I}g$，再对 $g$ 取下确界，则 $\underline{\int_{I}}f\leq \overline{\int_{I}}f$，这就完成了证明。

类似于上下极限，我们也定义 $f$ Riemann 可积当且仅当上下积分相等。

**定义 12.3.4** Riemann 积分

设 $I$ 是有界区间，函数 $f\colon I\to \mathbb{R}$ 是有界函数，如果 $\underline{\int_{I}}f=\overline{\int_{I}}f$，则称 $f$ 在 $I$ 上 **Riemann 可积**，并且定义

$$
\int_{I}f=\underline{\int_{I}}f=\overline{\int_{I}}f
$$

我们可以发现：Riemann 积分的符号与分段常值函数积分的符号是一样的，下面我们证明，Riemann 积分可以取代分段常值函数的积分，从而这里不会造成任何歧义。

**定理 12.3.5**

设 $I$ 是有界区间，函数 $f\colon I\to \mathbb{R}$ 是分段常值函数，那么 $f$ 在 $I$ 上 Riemann 可积，并且 $R.\int_{I}f=p.c. \int_{I}f$.

**证明**

任取一个从上方控制 $f$ 的分段常值函数 $g$，则有 $f(x)\leq g(x)$，从而 $p.c.\int_{I}f\leq p.c.\int_{I}g$，然而，$f$ 自身也是从上方控制 $f$ 的分段常值函数，因此我们有 $\overline{\int_{I}}f=p.c.\int_{I}f$. 同理也有 $\underline{\int_{I}}f=p.c.\int_{I}f$，从而有

$$
R.\int_{I}f=\overline{\int_{I}}f=p.c.\int_{I}f
$$

现在，我们就可以丢弃分段常值函数的积分，而始终使用 Riemann 积分（直到它被 Lebesgue 积分所取代）。

下面，我们给出一种计算函数的 Riemann 积分的方法，它与 Riemann 和的概念相关联。你或许在其它的教材中见过 Riemann 和，它给出了另一种定义 Riemann 积分的方法。

**定义 12.3.6** Riemann 和

设 $I$ 是有界区间，函数 $f\colon I\to \mathbb{R}$ 是有界函数，$\mathbf{P}$ 是 $I$ 的一个划分，则定义**上 Riemann 和**为

$$
U(f,\mathbf{P})=\sum_{J \in \mathbf{P}\setminus \{ \varnothing \}} (\sup_{x \in J} f(x))|J|
$$

定义**下 Riemann 和**为

$$
L(f,\mathbf{P})=\sum_{J \in \mathbf{P}\setminus \{ \varnothing \}} (\inf_{x \in J} f(x))|J|
$$

下面我们将 Riemann 和与 Riemann 积分联系起来。

**定理 12.3.7**

设 $I$ 是有界区间，函数 $f\colon I\to \mathbb{R}$ 是有界函数，$\mathbf{P}$ 是 $I$ 的一个划分，$g,h$ 是关于 $\mathbf{P}$ 的分段常值函数，并且 $g$ 从上方控制 $f$，$h$ 从下方控制 $f$，则有

$$
\int_{I}h \leq L(f,\mathbf{P})\leq U(f,\mathbf{P})\leq \int_{I}g
$$

**证明**

定义为 $\overline{f}(x)=\sup_{x \in J}f(x),x \in J$ 的函数 $\overline{f}\colon I\to \mathbb{R}$ 是一个分段常值函数，于是 $U(f,\mathbf{P})=\int_{I}\overline{f}$，又由于 $g$ 从上方控制 $f$，并且 $g$ 是分段常值函数，故对任意 $x \in J$，我们有 $\sup_{x \in J}f(x)\leq g(x)$，从而对任意 $x \in I$ 有 $\overline{f}(x)\leq g(x)$，因此 $U(f,\mathbf{P})\leq \int_{I}g$.

同理我们有 $\int_{I}h\leq L(f,\mathbf{P})$. 由于 $J\neq \varnothing$，故 $\inf_{x \in J}f(x)\leq \sup_{x \in J}f(x)$，从而 $L(f,\mathbf{P})\leq U(f,\mathbf{P})$.

**定理 12.3.8**

设 $I$ 是有界区间，函数 $f\colon I\to \mathbb{R}$ 是有界函数，那么

$$
\overline{\int_{I}}f=\inf_{\mathbf{P}} U(f,\mathbf{P}), \underline{\int_{I}}f=\sup_{\mathbf{P}} L(f,\mathbf{P})
$$

**证明**

我们只证明 $\overline{\int_{I}}f=\inf_{\mathbf{P}}U(f,\mathbf{P})$，另一个等式的证明是类似的。根据定理 12.3.7，我们有 $U(f,\mathbf{P})\leq \int_{I}g$，其中 $g$ 是从上方控制 $f$ 的分段常值函数，取下确界，就有 $\inf_{\mathbf{P}}U(f,\mathbf{P})\leq \overline{\int_{I}}f$. 下面我们要证另一个方向的不等式。

考虑函数 $\overline{f}(x)=\sup_{x \in J}f(x),x \in J$，则 $\overline{f}$ 是从上方控制 $f$ 的分段常值函数，于是根据上 Riemann 积分的定义知 $\overline{\int_{I}}f\leq \int_{I}\overline{f}=U(f,\mathbf{P})$，因此我们有 $\overline{\int_{I}}f\leq \inf_{\mathbf{P}}U(f,\mathbf{P})$，这就完成了证明。

根据上面的定理，我们可以给出一种计算函数 Riemann 积分的方法：设 $I$ 是一个非退化的有界区间，那么我们可以将区间按长度平均分成 $n$ 份，将这一划分记为 $\mathbf{P}_{n}$，那么我们有

$$
L(f,\mathbf{P}_{n})\leq \underline{\int_{I}}f\leq \overline{\int_{I}}f\leq U(f,\mathbf{P}_{n})
$$

要证 $f$ Riemann 可积，我们就只需证明

$$
\lim_{ n \to \infty } (U(f,\mathbf{P}_{n})-L(f,\mathbf{P}_{n}))=\lim_{ n \to \infty } \omega(f,\mathbf{P}_{n})=0
$$

此时就有 $\int_{I}f=\lim_{ n \to \infty }U(f,\mathbf{P}_{n})=\lim_{ n \to \infty }L(f,\mathbf{P}_{n})$，这样就将计算 Riemann 积分的问题还原为了一个序列极限问题。

迄今为止，我们只定义了有界区间上有界函数的 Riemann 积分，现在，我们想要定义无界区间或者无界函数的 Riemann 积分，这些积分我们称为**反常积分**，它们可以通过对正常积分取极限来定义。

**定义 12.3.9** 无界区间上的 Riemann 积分

设 $I$ 是区间 $(a,+\infty)$ 或 $[a,+\infty)$，函数 $f\colon I\to \mathbb{R}$ 是有界函数，并且对任意 $M>a$，函数 $f$ 在 $(a,M)$ 上 Riemann 可积，如果极限

$$
\lim_{ M \to +\infty; M \in I } \int_{a}^{M} f
$$

存在且等于实数 $L$，则称反常积分 $\int_{a}^{+\infty}f$ **收敛于** $L$，记作 $\int_{a}^{+\infty}f=L$. 反之则称反常积分 $\int_{a}^{+\infty}f$ **发散**。

对于反常积分 $\int_{-\infty}^{b}f$ 的收敛性，我们可以类似地定义。对于两侧无限的反常积分 $\int_{-\infty}^{+\infty}f$，我们需要将其划分为两个单侧无限的积分 $\int_{-\infty}^{a}f+\int_{a}^{+\infty}f$ 进行考虑，$\int_{-\infty}^{+\infty}f$ 收敛当且仅当两个单侧无限的反常积分收敛。

**定义 12.3.10** 无界函数的 Riemann 积分

设 $I$ 是区间 $(a,b)$ 或 $[a,b)$，函数 $f\colon I\to \mathbb{R}$ 满足 $\lim_{ x \to b;x \in I }f(x)=\pm \infty$，并且对任意 $a<c<b$，函数 $f$ 在 $(a,c)$ 上 Riemann 可积，如果极限

$$
\lim_{ c \to b; c \in I } \int_{a}^{c} f
$$

存在且等于实数 $L$，则称反常积分 $\int_{a}^{b}f$ **收敛于** $L$，记作 $\int_{a}^{b}f=L$. 反之则称反常积分 $\int_{a}^{b}f$ **发散**。

同样，我们也可以定义无界点 $b$ 右侧的反常积分。注意，我们不把反常积分的收敛定义为 Riemann 可积，也就是说，Riemann 可积函数一定是有界的。

# Section 4: Riemann 可积性

现在，我们可以将定理 12.2.6 推广至一般的 Riemann 可积函数。

**定理 12.4.1**

设 $I$ 是有界区间，函数 $f\colon I\to \mathbb{R},g\colon I\to \mathbb{R}$ 是 Riemann 可积的，则：

1. 线性性：$\int_{I}(af+bg)=a \int_{I}f+b \int_{I}g$
2. 比较准则：如果对任意 $x \in I$ 有 $f(x)\leq g(x)$，那么 $\int_{I}f\leq \int_{I}g$
3. 设 $I\subset J$，函数 $F\colon J\to \mathbb{R}$ 定义为 $$
F(x)=\begin{cases}
f(x) &, x \in I \\
0 &, x \not\in I
\end{cases}
$$ 则 $F$ 是 Riemann 可积的，并且 $\int_{J}F=\int_{I}f$
4. 设 $\{ J,K \}$ 是 $I$ 的划分，那么 $f|_{J}$ 和 $f|_{K}$ 都是 Riemann 可积的，并且 $\int_{I}f=\int_{J}f|_{J}+\int_{K}f|_{K}$

**证明**

对于线性性，我们可以将其分成两个命题来证明：加性和齐次性。首先来看加性，任取 $\varepsilon>0$，有在上方控制 $f,g$ 的分段常值函数 $\overline{f},\overline{g}$ 使得

$$
\overline{\int_{I}}(f+g)\leq \int_{I}\overline{f}+\int_{I}\overline{g}< \int_{I}f+\int_{I}g+2\varepsilon
$$

同理有

$$
\int_{I}f+\int_{I}g-2\varepsilon< \underline{\int_{I}}(f+g)
$$

从而有 $\int_{I}(f+g)=\int_{I}f+\int_{I}g$.

对于齐次性，当 $c=0$ 时，显然有 $\int_{I}cf=\int_{I}0=0=0\cdot \int_{I}f$. 当 $c>0$ 时，有

$$
c\int_{I}f-c\varepsilon<c\int_{I}\underline{f}\leq\underline{\int_{I}}cf\leq\overline{\int_{I}}cf\leq c \int_{I}\overline{f}<c \int_{I}f+c\varepsilon
$$

即 $\int_{I}cf=c \int_{I}f$. 下面只需证明 $c=-1$ 的情况即可，我们有

$$
-\int_{I}f-\varepsilon<-\int_{I}\overline{f}\leq\underline{\int_{I}}-f\leq\overline{\int_{I}}-f\leq -\int_{I}\underline{f}< -\int_{I}f+\varepsilon
$$

即 $\int_{I}-f=-\int_{I}f$. 对于 $c<0$ 的情况，只需将 $c$ 写成 $(-1)(-c)$ 即可。

定义 $h=g-f$，则函数 $\underline{h}(x)=0$ 从下方控制 $h$，故 $\int_{I}h\geq \int_{I}\underline{h}=0$，即 $\int_{I}f\leq \int_{I}g$.

设 $\overline{f}$ 从上方控制 $f$，则函数

$$
\overline{F}(x)=\begin{cases}
\overline{f}(x) &, x \in I \\
0 &, x \not\in I
\end{cases}
$$

从上方控制 $\overline{F}$，从而

$$
\overline{\int_{J}}F\leq \int_{J}\overline{F}=\int_{I}\overline{f}<\int_{I}f+\varepsilon
$$

另一边是类似的，从而有 $\int_{J}F=\int_{I}f$.

最后，设 $\overline{f}$ 从上方控制 $f$，$\underline{f}$ 从下方控制 $f$，则有

$$
\int_{I}f+\varepsilon>\int_{I}\overline{f}=\int_{J}\overline{f}|_{J}+\int_{K}\overline{f}|_{K},\int_{I}\underline{f}=\int_{J}\underline{f}|_{J}+\int_{K}\underline{f}|_{K}>\int_{I}f-\varepsilon
$$

从而

$$
0\leq\left( \int_{J}\overline{f}|_{J}-\int_{J}\underline{f}|_{J} \right)+\left( \int_{K}\overline{f}|_{K}-\int_{K}\underline{f}|_{K} \right)<2\varepsilon
$$

故 $0\leq\int_{J}\overline{f}|_{J}-\int_{J}\underline{f}|_{J}<2\varepsilon$，即 $f|_{J}$ 在 $J$ 上 Riemann 可积，同理 $f|_{K}$ 在 $K$ 上 Riemann 可积。现在定义

$$
F_{J}(x)=\begin{cases}
f(x) &, x \in J \\
0 &, x \in I\setminus J
\end{cases}
$$

那么 $f=F_{J}+F_{K}$，从而根据线性性和性质 3 得

$$
\int_{I}f=\int_{I}F_{J}+\int_{I}F_{K}=\int_{J}f|_{J}+\int_{K}f|_{K}
$$

这就完成了证明。

通常，我们将 $\int_{J}f|_{J}$ 写成 $\int_{J}f$，尽管 $f$ 是定义在更大的区间 $I$ 上的函数。利用性质 4 以及归纳法，我们可以知道

$$
\int_{I}f=\sum_{J \in \mathbf{P}}\int_{J}f
$$

其中 $\mathbf{P}$ 是 $I$ 的一个划分。这一性质通常称为积分的“有限可加性”，它来源于区间长度的有限可加性。

上述定理的性质 1（线性性）表明两个 Riemann 可积的函数之和也是 Riemann 可积的，下面我们给出其它构造 Riemann 可积函数的方法。

**定理 12.4.2**

设 $I$ 是有界区间，函数 $f\colon I\to \mathbb{R},g\colon I\to \mathbb{R}$ 是 Riemann 可积的，那么定义为 $\max(f,g)(x)=\max(f(x),g(x))$ 的函数 $\max(f,g)\colon I\to \mathbb{R}$ 是 Riemann 可积的，类似地，函数 $\min(f,g)$ 也是 Riemann 可积的。

**证明**

我们只证明 $\max(f,g)$ 是 Riemann 可积的，另一个是类似的。任取 $\varepsilon>0$，则存在 $\overline{f},\overline{g}$ 从上方控制 $f,g$，以及 $\underline{f},\underline{g}$ 从下方控制 $f,g$，使得

$$
\int_{I}f-\varepsilon<\int_{I}\underline{f}\leq\int_{I}\overline{f}<\int_{I}f+\varepsilon
$$

对 $g$ 也有类似的结论。定义 $h=\overline{f}-\underline{f}+\overline{g}-\underline{g}$，那么有 $\int_{I}h< 4\varepsilon$.

又由于 $\max(\overline{f},\overline{g})$ 从上方控制 $\max(f,g)$，$\max(\underline{f},\underline{g})$ 从下方控制 $\max(f,g)$，则有

$$
\int_{I}\max(\underline{f},\underline{g})\leq \underline{\int_{I}}\max(f,g)\leq \overline{\int_{I}}\max(f,g)\leq \int_{I}\max(\overline{f},\overline{g})
$$

而

$$
\overline{f}(x)=\underline{f}(x)+(\overline{f}-\underline{f})(x)\leq \underline{f}(x)+h(x)
$$

同理有 $\overline{g}(x)\leq \underline{g}(x)+h(x)$，故

$$
\int_{I}\max(\overline{f},\overline{g})\leq \int_{I}\max(\underline{f},\underline{g})+\int_{I}h<\int_{I}\max(\underline{f},\underline{g})+4\varepsilon
$$

这表明 $\overline{\int_{I}}\max(f,g)-\underline{\int_{I}}\max(f,g)<4\varepsilon$，故 $\max(f,g)$ 在 $I$ 上 Riemann 可积。

利用上面的定理，我们可以知道，如果 $f$ Riemann 可积，那么 $f$ 的**正数部分** $f^{+}=\max(f,0)$ 以及**负数部分** $f^{-}=-\min(f,0)$ 都可积，进而有 $f$ 的绝对值 $|f|=f^{+}+f^{-}$ 可积。我们将用这个结论证明以下的定理。

**定理 12.4.3**

设 $I$ 是有界区间，函数 $f\colon I\to \mathbb{R},g\colon I\to \mathbb{R}$ 是 Riemann 可积的，那么函数 $fg$ 也是 Riemann 可积的。

**证明**

将 $f$ 和 $g$ 写成正数部分和负数部分，则

$$
fg=(f^{+}-f^{-})(g^{+}-g^{-})=f^{+}g^{+}-f^{+}g^{-}-f^{-}g^{+}+f^{-}g^{-}
$$

根据 12.4.2 知 $f^{+},f^{-},g^{+},g^{-}$ 都可积，我们现在证明 $f^{+}g^{+}$ Riemann 可积，剩余三项的证明是类似的。

由于 $f^{+},g^{+}$ 是非负且有界的，故存在实数 $M>0$ 使得

$$
0\leq f^{+}(x)\leq M,0\leq g^{+}(x)\leq M
$$

现取 $\varepsilon>0$，则存在从上方控制 $f^{+}$ 的分段常值函数 $\overline{f^{+}}$ 以及从下方控制 $f^{+}$ 的分段常值函数 $\underline{f^{+}}$ 满足

$$
0\leq \underline{f^{+}}(x)\leq f^{+}(x)\leq \overline{f^{+}}(x)\leq M
$$

并且

$$
\int_{I}f^{+}-\varepsilon<\int_{I}\underline{f^{+}}\leq \int_{I} \overline{f^{+}}<\int_{I}f^{+}+\varepsilon
$$

对 $g$ 也有类似的结论。由于 $\overline{f^{+}}\overline{g^{+}}$ 从上方控制 $f^{+}g^{+}$，$\underline{f^{+}}\underline{g^{+}}$ 从下方控制 $f^{+}g^{+}$，故

$$
0\leq \overline{\int_{I}}f^{+}g^{+}-\underline{\int_{I}}f^{+}g^{+}\leq \int_{I}\overline{f^{+}}\overline{g^{+}}-\int_{I}\underline{f^{+}}\underline{g^{+}}
$$

但

$$
\overline{f^{+}}\overline{g^{+}}(x)-\underline{f^{+}}\underline{g^{+}}(x)=\overline{f^{+}}(\overline{g^{+}}-\underline{g^{+}})(x)+\underline{g^{+}}(\overline{f^{+}}-\underline{f^{+}})(x)
$$

故

$$
\int_{I}\overline{f^{+}}\overline{g^{+}}-\int_{I}\underline{f^{+}}\underline{g^{+}}\leq M(2\varepsilon)+M(2\varepsilon)=4M\varepsilon
$$

即证 $f^{+}g^{+}$ Riemann 可积。

到目前为止，我们已经讨论了许多 Riemann 可积性的内容，但除了分段常值函数，我们从未真正构造出一些 Riemann 可积的函数。现在我们就来证明，有一大类函数都是 Riemann 可积的。首先从一致连续函数开始。

**定理 12.4.4**

设 $I$ 是有界区间，函数 $f\colon I\to \mathbb{R}$ 是一致连续的，那么 $f$ 是 Riemann 可积的。

**证明**

由于一致连续函数将有界集映射到有界集，故 $f$ 是有界函数。如果 $I$ 是空集或者单点集，那么定理自动成立，现在设 $I$ 是非退化的区间，其端点是 $a<b$.

对任意 $\varepsilon>0$，存在 $\delta>0$ 使得对任意 $d(x',x'')<\delta$ 的 $x',x''\in I$ 有 $d(f(x'),f(x''))<\varepsilon$. 取正整数 $N$ 使得 $\dfrac{b-a}{N}<\delta$，将 $I$ 按长度均分为 $N$ 份 $J_{1},\dots,J_{N}$，则在每个 $J_{k}$ 上都有 $d(x',x'')<\delta$，从而有

$$
\overline{\int_{I}}f-\underline{\int_{I}}f\leq \sum_{k=1}^{N}(\sup_{x \in J_{k}}f(x)-\inf_{x \in J_{k}}f(x)) |J_{k}|\leq \sum_{k=1}^{N} \varepsilon \dfrac{b-a}{N}=\varepsilon(b-a)
$$

因此 $f$ 在 $I$ 上 Riemann 可积。

根据上述定理以及定理 10.3.6 可以得到推论：

**定理 12.4.5**

设实数 $a<b$，函数 $f\colon [a,b]\to \mathbb{R}$ 是连续函数，那么 $f$ 是 Riemann 可积的。

如果我们把 $[a,b]$ 换成其它类型的区间，那么上述定理就不成立，因为我们无法保证函数是有界的，然而，如果我们假设一个函数是连续且有界的，那么它就是 Riemann 可积的。

**定理 12.4.6**

设 $I$ 是有界区间，函数 $f\colon I\to \mathbb{R}$ 是连续且有界的，那么 $f$ 是 Riemann 可积的。

**证明**

当 $I$ 是空集或单点集时，定理自动成立。现设实数 $a<b$，$I$ 是 $(a,b),[a,b),(a,b]$ 之一，并设实数 $M>0$ 满足对任意 $x \in I$ 有 $|f(x)|\leq M$.

任取 $0<\varepsilon<\dfrac{b-a}{2}$，则 $f$ 在区间 $[a+\varepsilon,b-\varepsilon]$ 上连续，从而 Riemann 可积，设 $g$ 在 $[a+\varepsilon,b-\varepsilon]$ 上从上方控制 $f$，并且

$$
\int_{a+\varepsilon}^{b-\varepsilon}g<\int_{a+\varepsilon}^{b-\varepsilon}f+\varepsilon
$$

定义

$$
\overline{f}(x)=\begin{cases}
g(x) &, x \in[a+\varepsilon,b-\varepsilon] \\
M &, x \in I\setminus[a+\varepsilon,b-\varepsilon]
\end{cases}
$$

则 $\overline{f}$ 在 $I$ 上从上方控制 $f$，并且

$$
\overline{\int_{I}}f\leq\int_{I}\overline{f}\leq \int_{a+\varepsilon}^{b-\varepsilon}g+2M\varepsilon<\int_{a+\varepsilon}^{b-\varepsilon}f+(2M+1)\varepsilon
$$

另一个方向的不等式是类似的，从而有

$$
\overline{\int_{I}}f-\underline{\int_{I}}f<(4M+2)\varepsilon
$$

这就完成了证明。

这样就给出了一大类 Riemann 可积函数，即有界连续函数。我们还可以进行一点扩充，将**分段连续**函数也包括进来。

**定义 12.4.7** 分段连续函数（piecewise continuous function）

设 $I$ 是有界区间，函数 $f\colon I\to \mathbb{R}$，如果存在 $I$ 的划分 $\mathbf{P}$ 使得对任意 $J\in \mathbf{P}$，$f$ 在 $J$ 上的限制函数 $f|_{J}$ 是连续的，则称 $f$ 是 $I$ 上的**分段连续函数**。

**定理 12.4.8**

设 $I$ 是有界区间，函数 $f\colon I\to \mathbb{R}$ 是分段连续且有界的，那么 $f$ 是 Riemann 可积的。

**证明**

设 $f$ 关于 $I$ 的划分 $\mathbf{P}$ 是分段连续的，设 $J \in \mathbf{P}$，那么 $f$ 在 $J$ 上是 Riemann 可积的，我们将 $f|_{J}$ 延拓为

$$
F_{J}(x)=\begin{cases}
f(x) &, x \in J \\
0 &, x \in I\setminus J
\end{cases}
$$

则每个 $F_{J}$ 都是可积的，从而 $f=\sum_{J \in \mathbf{P}}F_{J}$ 是 Riemann 可积的。

上述定理表明，如果有界函数 $f$ 在 $I$ 上的间断点只有有限个，那么 $f$ 在 $I$ 上 Riemann 可积。之后，我们可以将这个结果优化为可数个间断点。

除了分段连续函数外，还有一大类函数是 Riemann 可积的，即单调函数，我们首先从闭区间上的单调函数开始。

**定理 12.4.9**

设实数 $a<b$，函数 $f\colon [a,b]\to \mathbb{R}$ 是单调函数，那么 $f$ 是 Riemann 可积的。

**证明**

不妨设 $f$ 单调递增，则 $f(a)\leq f(x)\leq f(b)$，从而 $f$ 是有界函数。设 $N$ 是一个正整数，将 $[a,b]$ 划分为 $N$ 个区间 $\left[ a+\dfrac{b-a}{N}k,a+\dfrac{b-a}{N}(k+1) \right)$，其中 $k=0,1,\dots,N-1$，和一个单点集 $\{ b \}$，则有

$$
\overline{\int_{I}}f \leq U(f,\mathbf{P})=\sum_{k=0}^{N-1}f\left( a+\dfrac{b-a}{N}(k+1) \right) \dfrac{b-a}{N}
$$

从而

$$
\overline{\int_{I}}f-\underline{\int_{I}}\leq U(f,\mathbf{P})-L(f,\mathbf{P})=(f(b)-f(a)) \dfrac{b-a}{N}
$$

根据 $N$ 的任意性可知 $f$ Riemann 可积。

现在我们将 12.4.9 推广至一般的有界区间。

**定理 12.4.10**

设 $I$ 是有界区间，函数 $f\colon I\to \mathbb{R}$ 是单调且有界的，那么 $f$ 是 Riemann 可积的。

**证明**

考虑闭区间 $[a+\varepsilon,b-\varepsilon]$，则 $f$ 在 $[a+\varepsilon,b-\varepsilon]$ 上单调，从而 Riemann 可积，下面仿照定理 12.4.6 的证明即证。

最后，我们来给出著名的积分判别法：

**定理 12.4.11** 积分判别法（integral test）

设函数 $f\colon [0,+\infty)$ 单调递减，并且它是非负的，那么级数 $\sum_{k=0}^{\infty}f(k)$ 收敛当且仅当反常积分 $\int_{0}^{+\infty} f$ 收敛。

**证明**

给定正整数 $N$，由于 $f$ 单调递减，则 $f$ 在 $[0,N]$ 上可积，并且有

$$
\sum_{k=1}^{N}f(k) \leq\int_{0}^{N}f=\sum_{k=0}^{N-1} \int_{k}^{k+1}f\leq \sum_{k=0}^{N-1} f(k)
$$

由于 $f$ 是非负的，故函数 $\int_{0}^{x}f$ 单调递增，从而 $\int_{0}^{+\infty}f=\sup_{N>0}\int_{0}^{N}f$.

如果级数 $\sum_{k=0}^{\infty}f(k)$ 收敛，那么 $\sup_{N>0}\int_{0}^{N}f$ 是有限的，从而 $\int_{0}^{+\infty}f$ 收敛。如果反常积分 $\int_{0}^{+\infty}f$ 收敛，那么非负级数 $\sum_{k=1}^{\infty}f(k)$ 有上界，故收敛，进而有 $\sum_{k=0}^{\infty}f(k)$ 收敛。这就完成了证明。