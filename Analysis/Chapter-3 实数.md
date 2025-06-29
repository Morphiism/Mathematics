回顾一下我们已有的结构，我们从自然数 $\mathbb{N}$ 开始构造出了整数 $\mathbb{Z}$，进一步构造出了有理数 $\mathbb{Q}$，每一步我们都把一种新的运算引入到数系上来。对于前者，这个运算是减法，对于后者，这个运算是除法。与之类似，要从有理数构造出实数，我们同样要引入一种新的运算到有理数上：**极限**。与前面不同的是，这一过程是从“离散”到“连续”的过程，因此我们需要做更多的工作。

对于数学中的很多部分来说，有理数已经足够处理了，然而，有理数对于数学的重要分支：几何学来说是不够的。例如，单位正方形的对角线长度 $\sqrt{ 2 }$ 就无法用有理数表示，因此，实数的构造是几何学算术化（公理化）的必要条件。此外，实数比起有理数还具有一些重要性质，我们将在后面做详细说明。

# Section 1: Cauchy 序列

首先我们回顾一下**序列**的概念。有理数的一个（无限）序列就是一个函数 $f\colon \mathbb{N}\to \mathbb{Q}$，令 $a_{n}=f(n)$，则一个序列可以写成

$$
(a_{n})_{n=0}^{\infty}=(a_{0},a_{1},a_{2},\dots)
$$

$a_{n}$ 的下标可以从 $n=m$ 开始取，通常我们取 $m=0$ 或 $m=1$.

下面我们引入**度量**的概念。

**定义 3.1.1** $\mathbb{Q}$ 上的度量（metric）

设 $p,q \in \mathbb{Q}$，定义 $\mathbb{Q}$ 上的**度量函数** $d\colon \mathbb{Q}^2\to \mathbb{Q}$ 为 $d(p,q)= |p-q|$.

根据绝对值的性质 2.3.10，我们可以证明如下定理：

**定理 3.1.2**

设 $p,q,r\in \mathbb{Q}$，则有：

1. 正定性：$d(p,q)>0$ 对于 $p \neq q$；$d(p,p)=0$
2. 对称性：$d(p,q)=d(q,p)$
3. 三角不等式：$d(p,q)\leq d(p,r)+d(r,q)$

我们构造实数的方法基于 **Cauchy 序列**的概念，如果你了解一些分析学的内容，你可能知道一个重要定理：一个序列有极限当且仅当它是一个 Cauchy 序列。我们的构造方法正是基于这种思路：每个实数都是有理数 Cauchy 序列的形式极限，在有了实数后我们就可以定义真正的极限，从而我们可以将有理数同构嵌入实数中。

**定义 3.1.3** Cauchy 序列

一个有理数序列 $(a_{n})_{n=0}^{\infty}$ 是一个 **Cauchy 序列**如果对于任意的有理数 $\varepsilon>0$ 都存在 $N\in \mathbb{N}$，使得对任意 $n,m>N$ 有 $d(a_{n},a_{m})<\varepsilon$.

上述定义表明，如果 $(a_{n})$ 是一个 Cauchy 序列，那么当 $n,m$ 足够大时，$a_{n}$ 和 $a_{m}$ 之间的差距可以变得任意的小，也就是说序列最终的值趋于稳定。上述条件可以利用一阶逻辑写成

$$
\forall \varepsilon>0 \exists N\in \mathbb{N} \forall n,m>N (d(a_{n},a_{m})<\varepsilon)
$$

其中 $\forall$ 称为**全称量词**，可以解释为“对任意...有”，$\exists$ 称为**存在量词**，可以解释为“存在...使得”。

下面我们考虑序列的一种性质：有界性。

**定义 3.1.4** 有界的（bounded）

有理数序列 $(a_{n})_{n=0}^{\infty}$ 是**有界的**如果存在有理数 $M>0$ 使得对于任意 $n\in \mathbb{N}$ 有 $|a_{n}|\leq M$.

利用归纳法我们可以证明，有限序列是有界的，进而我们可以证明以下定理：

**定理 3.1.5**

Cauchy 序列是有界的。

**证明**

设 $(a_{n})_{n=0}^{\infty}$ 是一个 Cauchy 序列，取 $\varepsilon=1$，则存在 $N$ 使得对任意 $n,m>N$ 有 $d(a_{n},a_{m})<\varepsilon$，特别地，取 $m=N+1$，则

$$
|a_{n}|-|a_{N+1}| \leq |a_{n}-a_{N+1}|<1
$$

于是 $|a_{n}|< |a_{N+1}|+1$. 对于前面有限个数，由于有限序列是有界的，从而有 $M_{1}>0$ 满足对于 $n\leq N$ 有 $|a_{n}|\leq M_{1}$. 取 $M=\max(M_{1},|a_{N+1}|+1)$，则对于任意 $n\in \mathbb{N}$ 有 $|a_{n}|\leq M$，即证。

为了构造实数，我们需要明确两个序列什么时候“收敛于同一个极限”，这引出了下面的定义：

**定义 3.1.6** 等价的（equivalent）

两个有理数序列 $(a_{n})_{n=0}^{\infty},(b_{n})_{n=0}^{\infty}$ 是**等价的**如果对任意的有理数 $\varepsilon>0$ 都存在 $N\in \mathbb{N}$ 使得对任意 $n>N$ 有 $d(a_{n},b_{n})<\varepsilon$.

换言之，两个序列等价表明当 $n$ 足够大时，两个序列最终可以任意地接近。

下面我们证明：Cauchy 序列的等价序列也是 Cauchy 序列。

**定理 3.1.7**

给定有理数序列 $(a_{n}),(b_{n})$，其中 $(a_{n})$ 是 Cauchy 序列，$(a_{n})$ 与 $(b_{n})$ 等价，则 $(b_{n})$ 也是 Cauchy 序列。

**证明**

任取 $\varepsilon>0$，根据定义我们有 $N_{1}$ 使得对任意 $n,m>N_{1}$ 有 $d(a_{n},a_{m})<\varepsilon$，并且有 $N_{2}$ 使得对任意 $n>N_{2}$ 有 $d(a_{n},b_{n})<\varepsilon$.

于是取 $N=\max(N_{1},N_{2})$，对于 $n,m>N$，我们有

$$
d(b_{n},b_{m})\leq d(b_{n},a_{n})+d(a_{n},a_{m})+d(a_{m},b_{m})< 3\varepsilon
$$

由于 $\varepsilon$ 是任意的，因此 $d(b_{n},b_{m})<3\varepsilon$ 当且仅当 $d(b_{n},b_{m})<\varepsilon$，这表明 $(b_{n})$ 是 Cauchy 序列。

接下来我们证明，Cauchy 序列的等价性是一个等价关系，自反性和对称性是显然的，因此下面我们证明序列等价具有传递性。

**定理 3.1.8**

设 $(a_{n}),(b_{n}),(c_{n})$ 是 Cauchy 序列，$(a_{n})$ 等价于 $(b_{n})$，$(b_{n})$ 等价于 $(c_{n})$，则 $(a_{n})$ 等价于 $(c_{n})$.

**证明**

任取 $\varepsilon>0$，有 $N$ 满足对任意 $n>N$ 有 $d(a_{n},b_{n})<\varepsilon,d(b_{n},c_{n})<\varepsilon$，于是 $d(a_{n},c_{n})\leq d(a_{n},b_{n})+d(b_{n},c_{n})<2\varepsilon$，即证。

现在我们就可以来定义实数了。

# Section 2: 实数的构造

记有理数的 Cauchy 序列构成的集合为 $S \subset \mathbb{Q}^{\mathbb{N}}$，在 $S$ 上定义等价关系 $\sim$ 使得 $(a_{n}) \sim (b_{n})$ 当且仅当 $(a_{n})$ 与 $(b_{n})$ 等价，**实数**（Real Number）就被定义为 $S$ 关于 $\sim$ 的商集

$$
\mathbb{R}=S / \sim = \{ [(a_{n})] \mid a_{n}\in \mathbb{Q}, (a_{n}) \text{是 Cauchy 序列} \}
$$

## 加法

**定义 3.2.1** $\mathbb{R}$ 上的加法

设 $[(a_{n})],[(b_{n})]\in \mathbb{R}$，定义 $\mathbb{R}$ 上的**加法**为

$$
[(a_{n})]+[(b_{n})]=[(a_{n}+b_{n})]
$$

下面我们验证其良定性。设 $(a_{n})\sim(a_{n}'),(b_{n})\sim(b_{n}')$，则

$$
\forall \varepsilon>0 \exists N \forall n>N (d(a_{n},a_{n}')<\varepsilon,d(b_{n},b_{n}')<\varepsilon)
$$

从而

$$
d(a_{n}+b_{n},a_{n}'+b_{n}')= |a_{n}+b_{n}-a_{n}'-b_{n}'|\leq |a_{n}-a_{n}'| + |b_{n}-b_{n}'|<2\varepsilon
$$

即 $(a_{n}+b_{n})\sim(a_{n}'+b_{n}')$.

显然，实数的加法是交换且结合的，这可以由有理数的加法交换与结合律直接得到。

所有项均为 $0$ 的常数序列 $[(0)]=\overline{0}$ 是 $\mathbb{R}$ 上的加法单位元，对于 $[(a_{n})]\in \mathbb{R}$，序列 $[(-a_{n})]=-[(a_{n})]$ 是其加法逆元。因此 $\mathbb{R}$ 上的加法满足域的加法公理。

有了加法逆元，$\mathbb{R}$ 上的减法的定义就是自然的了。

**定义 3.2.2** $\mathbb{R}$ 上的减法

设 $x,y \in \mathbb{R}$，定义 $\mathbb{R}$ 上的**减法**为

$$
x-y=x+(-y)
$$

## 乘法

**定义 3.2.3** $\mathbb{R}$ 上的乘法

设 $[(a_{n})],[(b_{n})]\in \mathbb{R}$，定义 $\mathbb{R}$ 上的**乘法**为

$$
[(a_{n})]\cdot[(b_{n})]=[(a_{n}b_{n})]
$$

设 $(a_{n})\sim(a_{n}'),(b_{n})\sim(b_{n}')$，则

$$
\forall \varepsilon>0 \exists N \forall n>N (d(a_{n},a_{n}')<\varepsilon,d(b_{n},b_{n}')<\varepsilon)
$$

于是

$$
d(a_{n}b_{n},a_{n}'b_{n}')= |a_{n}b_{n}-a_{n}'b_{n}'|\leq |(a_{n}-a_{n}')b_{n}|+|a_{n}'(b_{n}-b_{n}')|
$$

由于 Cauchy 序列是有界的，从而有 $M_{1},M_{2}$ 满足 $|b_{n}|\leq M_{1},|a_{n}'|\leq M_{2}$，因此 $d(a_{n}b_{n},a_{n}'b_{n}')<(M_{1}+M_{2})\varepsilon$，即 $(a_{n}b_{n})\sim(a_{n}'b_{n}')$.

根据有理数的性质，我们立即有实数乘法的交换律、结合律、分配律成立。

所有项均为 $1$ 的常值序列 $[(1)]=\overline{1}$ 是 $\mathbb{R}$ 上的乘法单位元。

唯一需要我们谨慎处理的是乘法逆元。对于 $[(a_{n})]\neq \overline{0}$，一种可能的想法是取 $[(a_{n}^{-1})]$，然而，这会引发一个问题：$(a_{n})$ 中可能含有 $0$，而对 $0$ 取乘法逆元是不被允许的。因此，我们需要对 $(a_{n})$ 的取法进行修正，这依赖于下面的定理。

**定理 3.2.4**

设 $[(a_{n})]\in \mathbb{R},[(a_{n})]\neq \overline{0}$，则存在 Cauchy 序列 $(b_{n})\sim (a_{n})$ 使得对任意 $n\in \mathbb{N}$ 有 $|b_{n}| \geq \eta>0$.

**证明**

我们有 $(a_{n})$ 不等价于 $\overline{0}$，将定义 3.1.6 中的逻辑关系全部取反，我们有

$$
\exists \varepsilon>0 \forall N \exists n>N (|a_{n}| \geq \varepsilon)
$$

取 $\eta=\varepsilon,N=0$，则有 $n_{0}>N$ 满足 $|a_{n_{0}}| \geq\eta$，令 $b_{0}=a_{n_{0}}$. 下面取 $N=n_{0}$，则有 $n_{1}>N$ 满足 $|a_{n_{1}}|\geq\eta$，令 $b_{1}=a_{n_{1}}$. 以此类推，我们就构造出了序列 $(b_{n})$ 使得 $|b_{n}|\geq\eta>0$.

下面我们证明 $(b_{n})\sim (a_{n})$，我们已知 $(a_{n})$ 是 Cauchy 序列，则

$$
\forall \varepsilon>0 \exists N \forall n,m>N (d(a_{n},a_{m})<\varepsilon)
$$

根据构造过程，我们可以知道 $n_{k}>k$，因此只要 $n>N$ 就一定有 $d(a_{n},b_{n})<\varepsilon$，即 $(a_{n})\sim(b_{n})$.

现在任取 $[(a_{n})]\in \mathbb{R},[(a_{n})]\neq \overline{0}$，则有 $[(a_{n})]=[(b_{n})]$，且 $|b_{n}|\geq \eta>0$，我们需要验证 $(b_{n}^{-1})$ 是一个 Cauchy 序列。事实上，我们有

$$
\left|\dfrac{1}{b_{n}}-\dfrac{1}{b_{m}}\right|=\dfrac{|b_{n}-b_{m}|}{|b_{n}b_{m}|}\leq \dfrac{|b_{n}-b_{m}|}{\eta^2}
$$

因此 $[(b_{n}^{-1})]\in \mathbb{R}$，且 $[(b_{n}^{-1})]=[(b_{n})]^{-1}=[(a_{n})]^{-1}$.

现在我们可以定义除法：

**定义 3.2.5** $\mathbb{R}$ 上的除法

设 $x,y\in \mathbb{R},y\neq \overline{0}$，定义 $\mathbb{R}$ 上的**除法**为

$$
x / y = x\cdot y^{-1}
$$

综合上述讨论，我们有：

**定理 3.2.6**

三元组 $(\mathbb{R},+,\cdot)$ 是一个域。

## 序关系

**定义 3.2.7** $\mathbb{R}$ 上的序

设 $[(a_{n})]\in \mathbb{R}$，定义 $\mathbb{R}$ 上的**序**如下：若存在 $(b_{n})\sim(a_{n})$ 使得 $b_{n}\geq \eta>0$，则定义 $[(a_{n})]>\overline{0}$，称 $[(a_{n})]$ 为**正的**；若 $-[(a_{n})]>\overline{0}$，则定义 $[(a_{n})]<\overline{0}$，称 $[(a_{n})]$ 为**负的**.

设 $x,y\in \mathbb{R}$，则定义 $x<y$ 如果 $x-y<\overline{0}$；定义 $x>y$ 如果 $x-y>\overline{0}$.

上面定义的序有下列性质：

**定理 3.2.8**

设 $x,y\in \mathbb{R}$，则：

1. 三分律：$x<\overline{0},x=\overline{0},x>\overline{0}$ 有且仅有一个成立。
2. 若 $x,y>\overline{0}$，则 $x+y>\overline{0},xy>\overline{0}$.

**证明**

我们先证明 1. 设 $x=[(a_{n})]\neq \overline{0}$，其中 $|a_{n}|\geq \eta>0$，由于 $(a_{n})$ 是 Cauchy 序列，则取 $\varepsilon=\dfrac{\eta}{2}$，存在 $N$ 使得对任意 $n,m>N$ 有 $d(a_{n},a_{m})<\varepsilon$. 于是我们有 $a_{m}-\varepsilon<a_{n}<a_{m}+\varepsilon$.

如果 $a_{N+1}>0$，则对任意 $n>N$ 有 $a_{n}\geq \dfrac{\eta}{2}>0$，从而 $[(a_{n})]>\overline{0}$，反之，如果 $a_{N+1}<0$，则 $[(a_{n})]<\overline{0}$. 根据有理数的三分律，$[(a_{n})]$ 要么 $>\overline{0}$，要么 $<\overline{0}$，即证。

2 可以从有理数的保序性得到：$a_{n}+b_{n}\geq \eta_{1}+\eta_{2}>0$，$a_{n}b_{n}\geq \eta_{1}\eta_{2}>0$.

我们可以证明，从上述性质可以推导出序 $<$ 的三分律、传递性、加法和乘法保序性，从而我们有

**定理 3.2.9**

四元组 $(\mathbb{R},+,\cdot,<)$ 是一个序域。

下面我们给出另一个判断序关系的定理，它表明，非负实数是一个**闭集**。

**定理 3.2.10**

设 $[(a_{n})]\in \mathbb{R}$ 满足 $a_{n}\geq 0$，则 $[(a_{n})]\geq \overline{0}$.

**证明**

我们使用反证法。假设 $[(a_{n})]<0$，于是有 $(b_{n})\sim(a_{n})$ 满足 $b_{n}\leq -\eta<0$，从而 $d(a_{n},b_{n})\geq \eta$，这与 $(b_{n})\sim(a_{n})$ 矛盾。

上述定理有个推论，表明如果 $a_{n}\leq b_{n}$，则 $[(a_{n})]\leq [(b_{n})]$.

## 有理数的同构嵌入

现在我们考虑 $\mathbb{R}$ 的子集

$$
\overline{\mathbb{Q}}=\{ [(q)] \mid q \in \mathbb{Q} \}
$$

包含所有有理数常值序列。令 $\overline{q}=[(q)]$，则我们有：

1. $\overline{p}+\overline{q}=\overline{p+q}$
2. $\overline{p}\cdot\overline{q}=\overline{pq}$
3. $p<q \implies  \overline{p}<\overline{q}$

因此 $\overline{\mathbb{Q}}$ 构成了 $\mathbb{R}$ 的一个封闭子集，令 $f\colon \mathbb{Q}\to \overline{\mathbb{Q}}$ 满足 $f(q)=\overline{q}$，则 $f$ 是一个双射，并且满足：

$$
\begin{gather*}
\begin{cases}
f(0)=\overline{0} \\
f(1)=\overline{1} \\
f(p+q)=f(p)+f(q) \\
f(pq)=f(p)f(q) \\
p<q \implies f(p)<f(q)
\end{cases}
\end{gather*}
$$

因此 $\overline{\mathbb{Q}}$ 同构于 $\mathbb{Q}$，$f$ 将 $\mathbb{Q}$ 同构嵌入 $\mathbb{R}$.

现在我们将 $\overline{q}$ 等同于 $q$，$\overline{\mathbb{Q}}$ 等同于 $\mathbb{Q}$，于是就有了实数结构 $(\mathbb{R},0,1,+,\cdot,<)$，其中实数集 $\mathbb{R}$ 包含有理数集 $\mathbb{Q}$ 作为它的子集。对于一般的实数的表示方法，我们等到下一章定义极限后再做讨论。

## 绝对值与指数

**定义 3.2.11** 绝对值

设 $x \in \mathbb{R}$，定义 $x$ 的**绝对值**为

$$
|x|=\begin{cases}
x &, x\geq 0 \\
-x &, x<0
\end{cases}
$$

$\mathbb{R}$ 上的绝对值与 $\mathbb{Q}$ 上的性质是相同的，这是因为 $\mathbb{R}$ 和 $\mathbb{Q}$ 都是序域。

同样，我们可以定义 $\mathbb{R}$ 上的度量。

**定义 3.2.12** $\mathbb{R}$ 上的度量

设 $x,y\in \mathbb{R}$，定义 $\mathbb{R}$ 上的**度量函数** $d\colon \mathbb{R}^2\to \mathbb{R}$ 为 $d(x,y)=|x-y|$.

当 $n \in \mathbb{Z}$ 时，可以定义 $\mathbb{R}$ 上的乘方，并且对 $\mathbb{Q}$ 成立的性质对 $\mathbb{R}$ 也成立。

**定义 3.2.13** $\mathbb{R}$ 上的乘方

设 $x \in \mathbb{R},n \in \mathbb{N}$，递归地定义 $\mathbb{R}$ 上的**乘方**为

$$
\begin{gather*}
\begin{cases}
x^0=1 \\
x^{n'}=x^n \cdot x
\end{cases}
\end{gather*}
$$

再设 $x \in \mathbb{R} \setminus \{ 0 \},n \in \mathbb{Z}$，定义 $\mathbb{R}$ 上的**乘方**为

$$
x^n=\begin{cases}
x^n &, n\geq 0 \\
(x^{-1})^{-n} &, n<0
\end{cases}
$$

## 有理数的分布

下面我们考虑自然数、整数、有理数在实数中是如何排布的，首先从自然数开始。

**定理 3.2.14** $\mathbb{R}$ 的 Archimedes 性

设 $x \in \mathbb{R}$，则有 $n \in \mathbb{N}$ 使得 $x<n$.

**证明**

设 $x=[(a_{n})]$，则 $(a_{n})$ 是有界的，从而存在有理数 $M>0$ 满足 $a_{n}\leq M$. 利用 $\mathbb{Q}$ 的 Archimedes 性，存在 $n\in \mathbb{N}$ 满足 $M<n$，于是我们有 $x<n$.

仿照 2.3.16 的证明，我们得到：

**定理 3.2.15**

设 $x \in \mathbb{R}$，则存在唯一的整数 $n$ 使得 $n\leq x<n+1$.

我们把这个整数记作 $\lfloor x \rfloor$，称为 $x$ 的**整数部分**。

下面考虑 $\mathbb{Q}$ 在 $\mathbb{R}$ 中的分布情况，我们有如下定理：

**定理 3.2.16** $\mathbb{Q}$ 的稠密性

任取 $x,y \in \mathbb{R},x<y$，存在 $r\in \mathbb{Q}$ 使得 $x<r<y$.

**证明**

对 $y-x>0$ 应用 Archimedes 性质，我们有 $\dfrac{1}{y-x} <n$，即 $0< \dfrac{1}{n}< y-x$，从而 $n(y-x)>1$，即 $nx<nx+1<ny$.

取 $m=\lfloor nx+1 \rfloor$，则有

$$
nx < m=\lfloor nx \rfloor +1 \leq nx+1 <ny
$$

从而 $x< \dfrac{m}{n}<y$，即证。

利用上面的定理，我们可以证明如下性质：

**定理 3.2.17**

设 $x,[(a_{n})] \in \mathbb{R}$，且 $x\leq a_{n}$，则 $x\leq [(a_{n})]$.

**证明**

用反证法，假设 $x>[(a_{n})]$，则存在 $r \in \mathbb{Q}$ 使得 $x>r>[(a_{n})]$，从而存在 $n$ 使得 $a_{n}<r<x$，这与 $x\leq a_{n}$ 矛盾。

现在我们已经完成了实数的构造，但是目前为止我们还没看到实数相对于有理数的任何优点：我们只证明了实数和有理数在基本的序域性质上相同。在下一节，我们将指出实数优于有理数的一个性质，并将乘方的指数扩展到有理数。

# Section 3: 确界性质

首先我们给出**上界**、**下界**的定义。

**定义 3.3.1** 上界（upper bound），下界（lower bound）

设 $E\subset \mathbb{R}$，称 $M\in \mathbb{R}$ 是 $E$ 在 $\mathbb{R}$ 中的一个**上界**，如果对任意 $x \in E$ 有 $x\leq M$. 称 $L\in \mathbb{R}$ 是 $E$ 在 $\mathbb{R}$ 中的一个**下界**，如果对任意 $x \in E$ 有 $L\leq x$.

对于 $E\subset \mathbb{R}$ 的所有上界中，最小的那个（如果能取到的话）是最重要的，因为它精确地描述了 $E$ 的范围，这引出了下面的定义：

**定义 3.3.2** 上确界（supremum），下确界（infimum）

设 $E\subset \mathbb{R}$，称 $\alpha \in \mathbb{R}$ 是 $E$ 在 $\mathbb{R}$ 中的**上确界**，如果 $\alpha$ 是 $E$ 的最小上界，记作 $\alpha=\sup E$. 称 $\beta \in \mathbb{R}$ 是 $E$ 在 $\mathbb{R}$ 中的**下确界**，如果 $\beta$ 是 $E$ 的最大下界，记作 $\beta=\inf E$.

把上述定义详细地写出来，就是说 $\alpha=\sup E$ 当且仅当

1. $\alpha$ 是 $E$ 的上界
2. 对任意 $M$，如果 $M$ 是 $E$ 的上界，则 $\alpha\leq M$

上面的第二条有时也写成对任意 $\gamma<\alpha$，存在 $x \in E$ 使得 $\gamma<x$.

下面的定理是实数最重要的一个性质，正是该性质将实数与有理数区分开来。

**定理 3.3.3** $\mathbb{R}$ 的上确界性质

设 $E\subset \mathbb{R},E\neq \varnothing$，且 $E$ 在 $\mathbb{R}$ 中有上界，那么 $E$ 在 $\mathbb{R}$ 中有唯一上确界。

**证明**

首先我们证明唯一性。设 $\alpha,\beta$ 是 $E$ 的上确界，则由 $\alpha$ 的最小性得 $\alpha\leq\beta$，再由 $\beta$ 的最小性得 $\beta\leq\alpha$，于是 $\alpha=\beta$，即 $E$ 最多只有一个上确界。

下面证明存在性。由于 $E\neq \varnothing$，我们可以取 $x_{0}\in E$. 设 $M$ 是 $E$ 的一个上界，并取 $n\geq 1$ 是一个整数，根据整数的分布，可以找到整数 $K$ 使得 $\dfrac{K}{n}\geq M$，于是 $\dfrac{K}{n}$ 也是 $E$ 的上界。对于 $x_{0}$，我们也可以找到整数 $L$ 使得 $\dfrac{L}{n}<x_{0}$，从而 $\dfrac{L}{n}$ 不是 $E$ 的上界。

现在我们要证存在整数 $L< m\leq K$ 使得 $\dfrac{m}{n}$ 是 $E$ 的上界而 $\dfrac{m-1}{n}$ 不是。事实上，令 $U=\left\{ m \in \mathbb{Z} \mid \forall x \in E \left(\dfrac{m}{n}\geq x\right) \right\}$，显然 $U$ 在 $\mathbb{Z}$ 中有下界，从而根据 $\mathbb{N}$ 的良序性，$U$ 有最小元 $m$，并且 $L<m\leq K$. 我们把这个数记作 $m_{n}$.

于是我们得到了一个有理数序列 $\left(\dfrac{m_{n}}{n}\right)_{n=1}^{\infty}$，我们要证它是 Cauchy 序列。取整数 $N\geq 1$ 以及 $n,n' >N$，由于 $\dfrac{m_{n}}{n}$ 是 $E$ 的上界而 $\dfrac{m_{n'}-1}{n'}$ 不是，我们有 $\dfrac{m_{n'}-1}{n'}< \dfrac{m_{n}}{n}$，即

$$
\dfrac{m_{n'}}{n'}- \dfrac{m_{n}}{n}< \dfrac{1}{n'}< \dfrac{1}{N}
$$

互换 $n$ 和 $n'$ 的位置，同理我们有

$$
\dfrac{m_{n}}{n}- \dfrac{m_{n'}}{n'}< \dfrac{1}{n}< \dfrac{1}{N}
$$

从而 $\left| \dfrac{m_{n}}{n}- \dfrac{m_{n'}}{n'} \right|< \dfrac{1}{N}$，任取 $\varepsilon>0$，由 Archimedes 性我们可以取 $N> \dfrac{1}{\varepsilon}$，对于任意 $n,n'>N$，有 $\left| \dfrac{m_{n}}{n}- \dfrac{m_{n'}}{n'} \right|<\varepsilon$，从而 $\left(\dfrac{m_{n}}{n}\right)_{n=1}^{\infty}$ 是一个 Cauchy 序列。

设 $\alpha=\left[ \left(\dfrac{m_{n}}{n}\right) \right]$，设 $x \in E$，由于 $\dfrac{m_{n}}{n}$ 是 $E$ 的上界，从而 $x\leq \dfrac{m_{n}}{n}$，于是 $x\leq \alpha$，即 $\alpha$ 是 $E$ 的上界。设 $y$ 是 $E$ 的上界，由于 $\dfrac{m_{n}-1}{n}$ 不是 $E$ 的上界，且 $\left( \dfrac{m_{n}}{n} \right)\sim\left( \dfrac{m_{n}-1}{n} \right)$，从而 $y\geq \dfrac{m_{n}-1}{n}$，即 $y\geq \alpha$. 综上，$\alpha$ 是 $E$ 的上确界。

上确界性质是 $\mathbb{Q}$ 所不具备的，例如 $\{ q \in \mathbb{Q} \mid q^2<2 \}$ 在 $\mathbb{Q}$ 中就没有上确界，这表明上确界性质无法由基本的序域公理推导出来，而是 $\mathbb{R}$ 特有的性质。

利用该性质，我们可以将乘方的指数扩展到有理数。

**定义 3.3.4** $n$ 次根

设 $x \in \mathbb{R},x\geq 0,n \in \mathbb{N},n>0$，定义 $x$ 的 $n$ **次根**为

$$
x^{1 / n}=\sup \{ y \in \mathbb{R} \mid y\geq 0, y^n\leq x \}
$$

通常我们将 $x^{1 / 2}$ 记作 $\sqrt{ x }$. 我们暂时不会引入负数的 $n$ 次根，事实上，只有定义了复数后我们才能讨论复数的指数问题。

下面给出一些 $n$ 次根的基本性质。

**定理 3.3.5**

设实数 $x,y\geq 0$，整数 $n,m>0$，则：

1. $y=x^{1 / n}\iff y^n=x$
2. $x^{1 / n}\geq 0$
3. $x>y \implies x^{1 / n}>y^{1 / n}$
4. 如果 $x<1$，则 $x^{1 / n}<x^{1 / (n+1)}$，如果 $x>1$，则 $x^{1 / n}>x^{1 / (n+1)}$，如果 $x=1$，则 $x^{1 / n}=1$
5. $(xy)^{1 / n}=x^{1 / n}y^{1 / n}$
6. $(x^{1 / n})^{1 / m}=x^{1 / nm}$

**证明**

2 是显然的，因为 $0 \in E=\{ z \mid z\geq 0,z^n\leq x \}$.

对于 1，设 $y=x^{1 / n}$，我们将使用反证法，证明 $y^n>x$ 与 $y^n<x$ 都会导出矛盾。首先假设 $y^n<x$，设 $0<\varepsilon<1$，考虑数

$$
(y+\varepsilon)^n=y^n+ny^{n-1}\varepsilon+\dots+\varepsilon^n
$$

取 $E$ 的一个上界 $M$，则 $y\leq M$，并且 $\varepsilon^n<\varepsilon$，从而 $(y+\varepsilon)^n\leq y^n+K\varepsilon$，其中 $K>0$. 由于 $y^n<x$，故存在 $\varepsilon$ 使得 $y^n+K\varepsilon<x$，于是 $(y+\varepsilon)^n<x$. 这与 $y$ 是 $E$ 的上界矛盾。

再假设 $y^n>x$，设 $0<\varepsilon<1$，考虑数

$$
\begin{align*}
(y-\varepsilon)^n &= y^n - ny^{n-1}\varepsilon+\dots+(-1)^n \varepsilon^n \\
&\geq y^n - n y^{n-1} \varepsilon- \binom{n}{3} y^{n-3} \varepsilon^3-\cdots \\
&\geq y^n - K\varepsilon
\end{align*}
$$

由于 $y^n>x$，则有 $\varepsilon$ 使得 $y^n-K\varepsilon>x$，从而 $(y-\varepsilon)^n>x$，这表明对任意 $z \in E$ 有 $y-\varepsilon\geq z$（否则 $(y-\varepsilon)^n<z^n\leq x$），于是 $y-\varepsilon$ 也是 $E$ 的上界，与 $y$ 是最小上界矛盾。因此 $y^n=x$.

反之，设 $y^n=x$，则 $y$ 是 $E$ 的最大值，因而也是 $E$ 的上确界，即 $y=x^{1 / n}$.

对于 3，我们证明其逆否命题。对 $x^{1 / n}\leq y^{1 / n}$ 两边取 $n$ 次幂，由 $(x^{1 / n})^n=x$ 得 $x\leq y$. 

由 3 我们可知 $x=y \iff x^{1 / n}=y^{1 / n}$，从而可以通过取 $n$ 次幂来证明 5 和 6.

对于 4，设 $x=1$，由于 $1^n=1$，故 $1^{1 / n}=1$. 设 $x>1$，则 $x^{1 / k}> 1$，设 $t=x^{1 / n},s=x^{1 / (n+1)}$，则 $t^n=x,s^{n+1}=x$，于是 $s^n<x$，即 $s<t$. 设 $x<1$，则 $x^{1 / k}<1$，则 $s^n>x=t^n$，即 $s>t$.

接下来我们就可以定义有理数指数了。

**定义 3.3.6** $\mathbb{R}$ 上的乘方

设 $x \in \mathbb{R},x> 0,q \in \mathbb{Q}$，记 $q= \dfrac{a}{b},a,b \in \mathbb{Z},b>0$，定义 $\mathbb{R}$ 上的**乘方**为

$$
x^{q}=(x^{1 / b})^a
$$

我们来验证上述定义是良定的。设 $\dfrac{a}{b}=\dfrac{a'}{b'},b,b'>0$，并先设 $a>0$，于是 $a'>0$，令 $y=x^{1 / ab'}=x^{1 / ba'}$，则

$$
(x^{1 / b})^a=y^{a'a}=y^{aa'}=(x^{1 / b'})^{a'}
$$

当 $a=0$ 时，$(x^{1 / b})^a=(x^{1 / b'})^{a'}=1$. 当 $a<0$ 时，考虑 $\dfrac{-a}{b}=\dfrac{-a'}{b'}$，我们有 $(x^{1 / b})^{-a}=(x^{1 / b'})^{-a'}$，两边取倒数即可。

并且我们可以证明，上面的定义和我们之前的定义是一致的。

有理数次幂的乘方同样满足指数的运算律。

**定理 3.3.7**

设 $x,y\in \mathbb{R},x,y>0,p,q\in \mathbb{Q}$，则：

1. $x^q>0$
2. $x^{p+q}=x^p x^q,(xy)^q=x^q y^q,(x^p)^q=x^{pq}$
3. 如果 $q>0$ 则 $x<y \implies x^q<y^q$
4. 若 $x>1$，则 $p<q \implies x^p<x^q$，若 $x<1$，则 $p<q \implies x^p>x^q$

**证明**

上述性质可以直接使用整数次幂和 $n$ 次根的性质证明，以 4 为例，设 $x>1$，由于 $p<q$，则 $q-p= \dfrac{a}{b}>0,a,b>0$，于是 $x^{1 / b}>1$，从而 $(x^{1 / b})^a>1$，即 $x^q>x^p$. 同理可证 $x<1$ 的情况。

我们知道实数系 $\mathbb{R}$ 具有上确界性质，但是对于下确界没有多少提及，然而我们可以证明，上确界性质和下确界性质是等价的。

**定理 3.3.8** $\mathbb{R}$ 的下确界性质

设 $E\subset \mathbb{R},E\neq \varnothing$，且 $E$ 在 $\mathbb{R}$ 中有下界，则 $E$ 在 $\mathbb{R}$ 中有唯一下确界。

**证明**

记 $E$ 的下界构成的集合为 $L$，则 $L\subset \mathbb{R},L\neq \varnothing$，$E$ 中的任意元素都是 $L$ 的上界，因此有 $\alpha=\sup L$，我们要证 $\alpha$ 是 $E$ 的下确界。

设 $\beta<\alpha$，则 $\beta$ 不是 $L$ 的上界，这表明对所有 $x \in E$ 有 $\alpha\leq x$，从而 $\alpha$ 是 $E$ 的下界。设 $\gamma>\alpha$，则 $\gamma \not\in L$，即 $\gamma$ 不是 $E$ 的下界，因此 $\alpha$ 具有最大性。综上，$\alpha$ 是 $E$ 的（唯一）下确界。

于是我们可以将上下确界性质合称为确界性质。上下确界的直接关联由下面的定理给出：

**定理 3.3.9**

设 $E\subset \mathbb{R},E\neq \varnothing$，且 $E$ 在 $\mathbb{R}$ 中有上确界 $\alpha$，令 $-E=\{ -x \mid x \in E \}$，则 $-\alpha=\inf (-E)$.

**证明**

对任意 $x \in E$ 有 $x\leq\alpha$，则 $-\alpha\leq -x$，即 $-\alpha$ 是 $-E$ 的下界。对 $\gamma<\alpha$，存在 $x \in E$ 使得 $\gamma<x$，即对于 $-\alpha< -\gamma$，存在 $-x \in -E$ 使得 $-x< -\gamma$，即 $-\alpha$ 是 $-E$ 的最大下界，即证。

确界性质是实数完备性的一种体现，它表明，实数是连续的，而不像有理数那样存在空洞。我们后面会看到，所有实数完备性定理都从不同的角度描述了实数的连续结构。

本章我们使用了有理数的 Cauchy 序列来构造实数，实际上，还有其它方法来构造实数，例如 Dedekind 分割法、算术超滤法等。我们将在附录中简要说明一下 Dedekind 分割法，在这之后我们将正式引入极限。