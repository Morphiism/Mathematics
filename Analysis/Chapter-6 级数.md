我们对序列极限已经有了一个充分的认识，现在我们就拿序列极限来建立无穷级数理论。首先我们回顾一下有限级数或称有限和的基本性质，然后我们将把这些性质推广到无限和。

# Section 1: 有限级数

**定义 6.1.1** 有限级数（finite series）

设 $(a_{n})_{n=0}^{N}$ 是一个有限序列，递归地定义**有限级数**如下：

$$
\begin{cases}
\displaystyle \sum_{i=0}^{0} a_{i}=a_{0} \\
\displaystyle \sum_{i=0}^{n+1} a_{i}=\sum_{i=0}^{n} a_{i}+a_{n+1}
\end{cases}
$$

当 $n<0$ 时，我们定义 $\sum_{i=0}^{n}a_{i}=0$，当 $n>N$ 时，定义 $a_{n}=0$.

通常，我们可以把有限级数写成如下形式：

$$
\sum_{i=0}^{n} a_{i}=a_{0}+a_{1}+\dots+a_{n}
$$

类似地也可以定义起点为 $i=m$ 的有限级数。

我们不加证明地给出以下定理。

**定理 6.1.2**

设 $(a_{n})_{n=0}^{N},(b_{n})_{n=0}^{N}$ 是有限序列，则有：

1. $\displaystyle \sum_{i=0}^{m}a_{i}+\sum_{i=m+1}^{n}a_{i}=\sum_{i=0}^{n}a_{i}$
2. $\displaystyle \sum_{i=0}^{n}a_{i}=\sum_{j=k}^{n+k}a_{j-k}$
3. 线性性：$\displaystyle \sum_{i=0}^{n}(pa_{i}+qb_{i})=p\sum_{i=0}^{n}a_{i}+q\sum_{i=0}^{n}b_{i}$
4. 三角不等式：$\displaystyle \left| \sum_{i=0}^{n}a_{i} \right|\leq \sum_{i=0}^{n}|a_{i}|$
5. 比较准则：若对任意 $k\in \mathbb{N}$ 有 $a_{k}\leq b_{k}$，则 $\displaystyle \sum_{i=0}^{n}a_{i}\leq \sum_{i=0}^{n}b_{i}$

下面我们定义有限集上的求和运算，回顾一下，我们称集合 $X$ 是有限集，如果存在双射 $g\colon n\to X$，其中 $n=\{ 0,1,\dots,n-1 \}$ 是自然数。

**定义 6.1.3** 有限和（finite sum）

设 $X\neq \varnothing$ 是一个有限集，$f\colon X\to \mathbb{R}$，定义**有限和**如下：取双射 $g\colon n\to X$，定义

$$
\sum_{x \in X}f(x)=\sum_{i=0}^{n-1} f(g(i))
$$

如果 $X=\varnothing$，则定义 $\sum_{x \in X}f(x)=0$.

根据实数加法的交换性与结合性，双射 $g$ 的选取是任意的，从而上述定义是良定的。

通常，我们把 $x \in X=\{ y\in Y \mid \varphi(y) \}$ 写成 $\varphi(x)$，比如

$$
\sum_{x \in \{ y\in \mathbb{N} \mid 0\leq y\leq n \}} f(x)=\sum_{0\leq x\leq n} f(x)
$$

利用定理 6.1.2，我们可以证明关于有限和的很多性质，下面我们给出有限和的特有性质。

**定理 6.1.4**

设 $X,Y$ 是有限集，则有：

1. $\displaystyle \sum_{i=0}^{n}a_{i}=\sum_{0\leq i\leq n}a_{i}$
2. 换元法：设 $g\colon Y\to X$ 是一个双射，则 $\displaystyle \sum_{x \in X}f(x)=\sum_{y \in Y}f(g(y))$
3. 设 $X\cap Y=\varnothing$，则 $\displaystyle \sum_{z \in X\cup Y}f(z)=\sum_{x \in X}f(x)+\sum_{y \in Y}f(y)$

下面我们考虑多变量函数的求和，我们有如下定理：

**定理 6.1.5** 有限级数的 Fubini 定理

设 $X,Y$ 是有限集，$f\colon X\times Y\to \mathbb{R}$，则

$$
\sum_{x \in X}\left( \sum_{y \in Y} f(x,y) \right)=\sum_{(x,y)\in X\times Y}f(x,y)=\sum_{(y,x)\in Y\times X}f(x,y)
$$

严格的证明需要使用归纳法，这里我们只给出一个思路。对于第一个等号，需要使用实数的交换性和结合性，将 $x$ 相同的项放在一起，则有

$$
(f(x_{0},y_{0})+f(x_{0},y_{1})+\cdots)+(f(x_{1},y_{0})+f(x_{1},y_{1})+\cdots)+\cdots
$$

对于第二个等号，我们使用换元法，取 $Y\times X\to X\times Y$ 的双射 $h(y,x)=(x,y)$ 即可。

利用 $X\times Y\times Z=(X\times Y)\times Z$ 可以将上述定理推广至 $n$ 个变量。

最后我们考虑极限与求和的关系，我们有如下定理：

**定理 6.1.6**

设 $X$ 是有限集，如果对任意 $x \in X$，都有实数序列 $(a_{n}(x))_{n=0}^{\infty}$ 收敛，则序列 $\left( \sum_{x \in X}a_{n}(x) \right)$ 收敛，且

$$
\lim_{ n \to \infty } \sum_{x \in X} a_{n}(x)=\sum_{x \in X}\lim_{ n \to \infty } a_{n}(x)
$$

由极限的代数性质（4.1.9）以及归纳法立即得到。

我们研究无穷级数的目的就是为了理解，什么情况下，上面关于有限级数的性质可以推广到无穷。

# Section 2: 无穷级数

**定义 6.2.1** 形式无穷级数（formal infinite series）

设 $(a_{n})_{n=0}^{\infty}$ 是一个实数序列，一个**形式无穷级数**是形如

$$
\sum_{i=0}^{\infty} a_{i}=a_{0}+a_{1}+a_{2}+\cdots
$$

的表达式。指标的起点也可以取 $i=m$.

目前，无穷级数只是被形式地定义了，就像极限符号 $\lim_{ n \to \infty }a_{n}$ 一样，如果 $(a_{n})$ 发散，那么极限符号就是一个形式化的、无意义的符号。现在，我们来定义级数的收敛，为形式级数赋予一个值。

**定义 6.2.2** 级数的收敛

设 $\sum_{i=0}^{\infty}a_{i}$ 是一个形式级数，定义其**部分和**序列为 $S_{n}=\sum_{i=0}^{n}a_{i}$，如果序列 $(S_{n})$ 收敛于 $L$，则称级数 $\sum_{i=0}^{\infty}a_{i}$ **收敛于** $L$，记作 $\sum_{i=0}^{\infty}a_{i}=L$. 如果 $(S_{n})$ 发散，则称级数 $\sum_{i=0}^{\infty}a_{i}$ **发散**。

根据定义我们知道，级数的收敛性取决于部分和序列的收敛性，从而我们将级数收敛问题转化为了一个序列收敛问题，从而我们就能够使用序列极限的定理来判断级数的收敛性。一个例子如下：

**定理 6.2.3** Cauchy 准则

级数 $\sum_{i=0}^{\infty}a_{i}$ 收敛当且仅当对任意 $\varepsilon>0$，存在 $N\in \mathbb{N}$ 使得对任意 $n>N$ 和 $p>0$ 有 $|a_{n+1}+\dots+a_{n+p}|<\varepsilon$.

**证明**

对部分和序列 $(S_{n})$ 应用 Cauchy 准则，并注意到 $|S_{n+p}-S_{n}|=|a_{n+1}+\dots+a_{n+p}|$ 即可。

从上述定理我们可以得到一个有用的推论。

**定理 6.2.4**

如果级数 $\sum_{i=0}^{\infty}a_{i}$ 收敛，则 $\lim_{ n \to \infty }a_{n}=0$.

**证明**

在 Cauchy 准则（6.2.3）中取 $p=1$ 即得。

这给了我们一种快速判断一个级数是否发散的方法：如果 $\lim_{ n \to \infty }a_{n}\neq 0$，那么级数发散。

下面我们考虑将定理 6.1.2 推广到无穷级数上，首先我们从前三条开始。

**定理 6.2.5**

设级数 $\sum_{i=0}^{\infty}a_{i}$ 和 $\sum_{i=0}^{\infty}b_{i}$ 收敛，则：

1. $\displaystyle \sum_{i=0}^{\infty}a_{i}=\sum_{i=0}^{k-1}a_{i}+\sum_{i=k}^{\infty}a_{i}$
2. $\displaystyle \sum_{i=0}^{\infty}a_{i}=\sum_{j=k}^{\infty}a_{j-k}$
3. 线性性：$\displaystyle \sum_{i=0}^{\infty}(pa_{i}+qb_{i})=p\sum_{i=0}^{\infty}a_{i}+q\sum_{i=0}^{\infty}b_{i}$

**证明**

(1). 设 $\sum_{i=0}^{\infty}a_{i}$ 的部分和序列 $(S_{n})_{n=0}^{\infty}$ 收敛于 $L$，则 $\sum_{i=k}^{\infty}a_{i}$ 的部分和序列 $(S_{n}-S_{k-1})_{n=k}^{\infty}$ 收敛于 $L-S_{k-1}$，即证。

对于 2，两边的部分和序列相同，从而极限也相同。

(3). 使用 Cauchy 准则，任取 $\varepsilon>0$，存在 $N$ 使得对任意 $n>N$ 和 $t>0$ 有

$$
\left| \sum_{i=1}^{t} p a_{n+i}+q b_{n+i} \right| \leq |p| \left| \sum_{i=1}^{t} a_{n+i} \right| +|q| \left| \sum_{i=1}^{t} b_{n+i} \right| <(|p|+|q|)\varepsilon
$$

这就完成了证明。

下面我们考虑 6.1.2(4) 三角不等式，对于级数 $\sum_{i=0}^{\infty}|a_{i}|$，我们有如下定义：

**定义 6.2.6** 绝对收敛（absolute convergence），条件收敛（conditional convergence）

设 $\sum_{i=0}^{\infty}a_{i}$ 是一个形式级数，如果级数 $\sum_{i=0}^{\infty}|a_{i}|$ 收敛，则称级数**绝对收敛**。如果级数 $\sum_{i=0}^{\infty}a_{i}$ 收敛但不绝对收敛，则称级数**条件收敛**。

下面我们给出绝对收敛判别法：

**定理 6.2.7** 三角不等式（triangle inequality）

设级数 $\sum_{i=0}^{\infty}a_{i}$ 绝对收敛，则级数收敛，且有

$$
\left| \sum_{i=0}^{\infty} a_{i} \right| \leq \sum_{i=0}^{\infty} |a_{i}|
$$

**证明**

我们使用 Cauchy 准则，任取 $\varepsilon>0$，存在 $N$ 使得对任意 $n>N,p>0$ 有 $|a_{n+1}+\dots+a_{n+p}|\leq |a_{n+1}|+\dots+|a_{n+p}|<\varepsilon$，因此级数 $\sum_{i=0}^{\infty}a_{i}$ 收敛。

设 $S_{n}=\sum_{i=0}^{n}a_{i},T_{n}=\sum_{i=0}^{n}|a_{i}|$，则对任意 $n \in \mathbb{N}$，有 $|S_{n}|\leq T_{n}$，由比较准则，我们有

$$
-\sum_{i=0}^{\infty} |a_{i}|\leq \sum_{i=0}^{\infty} a_{i}\leq \sum_{i=0}^{\infty} |a_{i}|
$$

这就完成了证明。

最后，我们再给出一个判别法。

**定理 6.2.8** 交错级数判别法（alternating series test）

设 $(a_{n})_{n=0}^{\infty}$ 是一个非负的递减序列，则级数 $\sum_{i=0}^{\infty}(-1)^{i}a_{i}$ 收敛当且仅当 $\lim_{ n \to \infty }a_{n}=0$.

**证明**

设 $\sum_{i=0}^{\infty}(-1)^{i}a_{i}$ 收敛，则 $\lim_{ n \to \infty }(-1)^{n}a_{n}=0$，即 $\lim_{ n \to \infty }a_{n}=0$，因为 $d((-1)^{n}a_{n},0)=d(a_{n},0)$.

现设 $\lim_{ n \to \infty }a_{n}=0$. 设部分和序列为 $(S_{n})$，则对于 $N\in \mathbb{N}$ 有

$$
S_{N+2}-S_{N}=(-1)^{N+1}(a_{N+1}-a_{N+2})
$$

因此当 $N$ 是奇数时，$S_{N+2}\geq S_{N}$，当 $N$ 是偶数时，$S_{N+2}\leq S_{N}$.

现设 $N$ 是偶数，则对 $k \in \mathbb{N}$ 有 $S_{N+2k}\leq\dots\leq S_{N+2}\leq S_{N}$，且 $S_{N+2k+1}=S_{N+2k}-a_{N+2k+1}\leq S_{N+2k}\leq S_{N}$，于是我们有

$$
S_{N+1}=S_{N}-a_{N+1}\leq S_{N+2k+1}\leq S_{N+2k}\leq S_{N}
$$

则 $S_{N}-a_{N+1}\leq S_{n}\leq S_{N}$ 对 $n>N$ 成立。由于 $\lim_{ n \to \infty }a_{n}=0$，对任意 $\varepsilon>0$，存在 $N$ 使得 $0\leq a_{N+1}<\varepsilon$，对任意 $n>N$ 和 $p>0$，我们有 $|S_{n+p}-S_{n}|<\varepsilon$，从而 $(S_{n})$ 收敛。

我们可以将级数问题看成序列收敛问题，反过来，我们也可以将序列收敛问题看成级数收敛问题。对于序列 $(a_{n})_{n=0}^{\infty}$，我们令 $u_{0}=a_{0}$，当 $n>0$ 时令 $u_{n}=a_{n}-a_{n-1}$，则 $\sum_{i=0}^{\infty}u_{i}$ 的部分和序列就是 $(a_{n})$，这样，我们就将一个序列问题转化为了一个级数问题。总而言之，序列和级数是一体两面的。

# Section 3: 非负级数

现在我们考察一类级数 $\sum_{i=0}^{\infty}a_{i}$，其中 $a_{n}\geq 0$，称为**非负级数**或者**正项级数**。这类级数有一些比较良好的性质，比如部分和序列单调递增，以及如果级数收敛，那么级数绝对收敛等等。因此我们给出下面的定理：

**定理 6.3.1**

设 $\sum_{i=0}^{\infty}a_{i}$ 是一个非负级数，则级数绝对收敛当且仅当存在实数 $M>0$ 使得对任意 $n \in \mathbb{N}$ 有 $\sum_{i=0}^{n}a_{i}\leq M$.

**证明**

对部分和序列 $(S_{n})$ 应用单调收敛定理，并注意到 $|a_{n}|=a_{n}$.

这个定理使得我们能够将 6.1.2(5) 推广到无穷。

**定理 6.3.2** 比较准则

设级数 $\sum_{i=0}^{\infty}a_{i},\sum_{i=0}^{\infty}b_{i}$ 满足对任意 $n \in \mathbb{N}$ 有 $|a_{n}|\leq b_{n}$，那么如果 $\sum_{i=0}^{\infty}b_{i}$ 收敛，则 $\sum_{i=0}^{\infty}a_{i}$ 绝对收敛，且

$$
\left| \sum_{i=0}^{\infty} a_{i} \right| \leq \sum_{i=0}^{\infty} |a_{i}| \leq \sum_{i=0}^{\infty} b_{i}
$$

**证明**

设 $L=\sum_{i=0}^{\infty}b_{i}$，则 $L$ 是 $\sum_{i=0}^{n}|a_{i}|$ 的一个上界，从而 $\sum_{i=0}^{\infty}|a_{i}|$ 收敛。第一个不等式来源于绝对收敛级数的三角不等式，对于第二个不等式，我们有 $\sum_{i=0}^{n}|a_{i}|\leq \sum_{i=0}^{n}b_{i}$，两边取极限即得。

在比较准则中，一个常用的级数是**几何级数**或称**等比级数**

$$
\sum_{i=0}^{\infty} x^{i}=1+x+x^{2}+\cdots
$$

对于其收敛性，我们有：

**命题 6.3.3**

当 $|x|<1$ 时，几何级数绝对收敛于 $\dfrac{1}{1-x}$，当 $|x|\geq 1$ 时，几何级数发散。

**证明**

设 $|x|<1$，我们可以证明级数 $\sum_{i=0}^{\infty}|x|^{i}$ 的部分和为 $\dfrac{1-|x|^{n+1}}{1-|x|}$，当 $n\to \infty$ 时，部分和序列收敛于 $\dfrac{1}{1-|x|}$. 这就完成了 $|x|<1$ 部分的证明。

当 $|x|\geq 1$ 时，序列 $(x^{n})$ 发散，故级数发散。

使用几何级数作为比较对象，我们就得到了著名的根值判别法和比值判别法：

**定理 6.3.4** 根值判别法（root test）

设 $\sum_{i=0}^{\infty}a_{i}$ 是实数序列，$\alpha=\limsup_{ n \to \infty }|a_{n}|^{1/n}$，则：

1. 如果 $\alpha<1$，那么级数绝对收敛。
2. 如果 $\alpha>1$，那么级数发散。

**证明**

设 $\alpha<1$，显然我们有 $\alpha\geq 0$，取 $0<\varepsilon<1-\alpha$，则存在 $N$，使得对任意 $n>N$ 有 $|a_{n}|^{1/n}<\alpha+\varepsilon$，即 $|a_{n}|<(\alpha+\varepsilon)^{n}$. 根据定理 6.2.5(1)，级数前有限项不影响级数的收敛性，且几何级数 $\sum_{i=N+1}^{\infty}(\alpha+\varepsilon)^{i}$ 收敛，根据比较准则，级数 $\sum_{i=0}^{\infty}a_{n}$ 绝对收敛。

设 $\alpha>1$，取 $0<\varepsilon<\alpha-1$，则对任意 $N$ 都有 $n>N$ 使得 $|a_{n}|>(\alpha-\varepsilon)^{n}>1$，于是 $(a_{n})$ 不收敛于 $0$，从而级数发散。

之后我们会看到满足 $\alpha=1$ 的收敛序列与发散序列，从而当 $\alpha=1$ 时我们不能得到任何结论。

有时候，根值判别法使用起来不太方便，于是我们就需要比值判别法。首先，我们先证明一个引理：

**引理 6.3.5**

设 $(c_{n})$ 是一个正数序列，则有以下不等式成立：

$$
\liminf_{ n \to \infty } \dfrac{c_{n+1}}{c_{n}}\leq \liminf_{ n \to \infty } c_{n}^{1/n}\leq \limsup_{ n \to \infty } c_{n}^{1/n}\leq \limsup_{ n \to \infty } \dfrac{c_{n+1}}{c_{n}}
$$

**证明**

第二个不等式根据上下极限的性质得到，我们来证明第三个不等式，第一个可以类似地证明。

设 $L=\limsup_{ n \to \infty }\dfrac{c_{n+1}}{c_{n}}$，如果 $L=+\infty$，那么我们不用证明什么。现设 $L$ 是一个有限实数，并且我们有 $L\geq 0$.

任取 $\varepsilon>0$，存在 $N$ 使得对任意 $n>N$ 有 $c_{n+1}<c_{n}(L+\varepsilon)$，根据归纳法我们有 $c_{n}<c_{N+1}(L+\varepsilon)^{n-N-1}$，设 $M=c_{N+1}(L+\varepsilon)^{-N-1}$，则有 $c_{n}^{1/n}<M^{1/n}(L+\varepsilon)$.

由于 $\lim_{ n \to \infty }M^{1/n}=1$，根据极限的比较准则，我们有 $\limsup_{ n \to \infty }c_{n}^{1/n}\leq L+\varepsilon$ 对任意 $\varepsilon>0$ 成立，于是 $\limsup_{ n \to \infty }c_{n}^{1/n}\leq L$.

从而我们有下面的定理：

**定理 6.3.6** 比值判别法（ratio test）

设 $\sum_{i=0}^{\infty}a_{i}$ 是实数序列，$a_{n}\neq 0$，则：

1. 若 $\limsup_{ n \to \infty }\dfrac{|a_{n+1}|}{|a_{n}|}<1$，则级数绝对收敛。
2. 若 $\liminf_{ n \to \infty }\dfrac{|a_{n+1}|}{|a_{n}|}>1$，则级数发散。

**证明**

对序列 $(|a_{n}|)$ 使用引理 6.3.5 再利用根值判别法即可。

利用引理 6.3.5 我们也可以得到下面的极限：

**命题 6.3.7**

$\lim_{ n \to \infty }n^{1/n}=1$

**证明**

序列 $(n)_{n=1}^{\infty}$ 是一个正数序列，从而有

$$
1=\liminf_{ n \to \infty } \dfrac{n+1}{n}\leq \liminf_{ n \to \infty } n^{1/n}\leq \limsup_{ n \to \infty } n^{1/n}\leq \limsup_{ n \to \infty } \dfrac{n+1}{n}=1
$$

于是 $\lim_{ n \to \infty }n^{1/n}=1$.

从上面的证明中我们看到，如果 $\lim_{ n \to \infty }\dfrac{c_{n+1}}{c_{n}}=L$，那么一定有 $\lim_{ n \to \infty }c_{n}^{1/n}=L$.

现在我们回到非负级数的研究上来，对于一个单调递减的序列 $(a_{n})$，我们有如下定理来判断级数的收敛性：

**定理 6.3.8** Cauchy 判别法

设 $(a_{n})_{n=1}^{\infty}$ 是一个非负递减的实数序列，则级数 $\sum_{i=1}^{\infty}a_{i}$ 收敛当且仅当级数 $\sum_{k=0}^{\infty}2^{k}a_{2^{k}}=a_{1}+2a_{2}+4a_{4}+\cdots$ 收敛。

**证明**

设 $\sum_{i=1}^{\infty}a_{i}$ 的部分和为 $S_{n}$，$\sum_{k=0}^{\infty}2^{k}a_{2^{k}}$ 的部分和为 $T_{n}$，则我们只需证明对任意 $n \in \mathbb{N}$ 有 $S_{2^{n+1}-1}\leq T_{n}\leq 2S_{2^{n}}$，从而 $(S_{n})$ 有界当且仅当 $(T_{n})$ 有界。

我们使用归纳法，当 $n=0$ 时 $S_{1}\leq T_{0}\leq 2S_{1}$ 成立，设不等式对 $n$ 成立，则 $T_{n+1}=T_{n}+2^{n+1}a_{2^{n+1}}$，并且我们有

$$
S_{2^{n+1}}=S_{2^{n}}+\sum_{i=2^{n}+1}^{2^{n+1}} a_{i}\geq S_{2^{n}}+2^{n}a_{2^{n+1}}
$$

从而 $2S_{2^{n+1}}\geq 2S_{2^{n}}+2^{n+1}a_{2^{n+1}}$，于是 $T_{n+1}\leq 2S_{2^{n+1}}$.

另一边，我们有

$$
S_{2^{n+2}-1}=S_{2^{n+1}-1}+\sum_{i=2^{n+1}}^{2^{n+2}-1} a_{i}\leq S_{2^{n+1}-1}+2^{n+1}a_{2^{n+1}}
$$

从而 $S_{2^{n+2}-1}\leq T_{n+1}$，这就完成了证明。

利用 Cauchy 判别法，我们可以证明另一个常用级数的收敛性，通常称为 $p$ 级数或者 Riemann $\zeta$ 函数。

**命题 6.3.9**

设实数 $p>0$，则当 $p>1$ 时级数 $\sum_{n=1}^{\infty}\dfrac{1}{n^{p}}$ 绝对收敛，当 $p\leq 1$ 时级数发散。

**证明**

我们使用 Cauchy 判别法，原级数的收敛性取决于级数

$$
\sum_{k=0}^{\infty} 2^{k} \dfrac{1}{(2^{k})^{p}}=\sum_{k=0}^{\infty} (2^{1-p})^{k}
$$

的收敛性。这是一个几何级数，当 $|2^{1-p}|<1$ 时绝对收敛，$|2^{1-p}|\geq 1$ 时发散，即 $p>1$ 时收敛，$p\leq 1$ 时发散。

特别地，**调和级数** $\sum_{n=1}^{\infty}\dfrac{1}{n}$ 发散（尽管 $\lim_{ n \to \infty }\dfrac{1}{n}=0$ ），而著名的 Basel 问题 $\sum_{n=1}^{\infty}\dfrac{1}{n^{2}}$ 收敛，Euler 发现并证明了这个级数收敛于 $\dfrac{\pi^{2}}{6}$. 我们看到这两个级数都满足 $\lim_{ n \to \infty }\dfrac{|a_{n+1}|}{|a_{n}|}=1$，因此当根值判别法或者比值判别法给出 $1$ 时，我们不能得到任何结论。

# Section 4: 级数的重排

现在我们想把有限和（6.1.3）推广至无限集，然而，这立即引出了两个问题：第一，无穷级数中的项是可数个，从而我们最多只能在可数集上求和（回想一下，一个集合 $X$ 是可数的如果存在双射 $g\colon \mathbb{N}\to X$ ），这一方面的讨论我们放在下一章。

第二，定义 6.1.3 中要求对任意双射 $g$，求和的结果都是相同的，推广到无穷级数上，这就要求级数 $\sum_{i=0}^{\infty}a_{i}$ 在任意双射 $f\colon \mathbb{N}\to \mathbb{N}$ 下的重排级数 $\sum_{i=0}^{\infty}a_{f(i)}$ 与原级数收敛于相同的值，这是一件需要证明的事。

**定理 6.4.1** 非负级数的重排

设 $\sum_{i=0}^{\infty}a_{i}$ 是一个非负收敛级数，$f\colon \mathbb{N}\to \mathbb{N}$ 是双射，则级数 $\sum_{i=0}^{\infty}a_{f(i)}$ 收敛，并且与原级数有相同的和。

**证明**

设 $S_{n}=\sum_{i=0}^{n}a_{i},T_{m}=\sum_{i=0}^{m}a_{f(i)}$，并设 $L=\sup S_{n},L'=\sup T_{m}$，任取 $m \in \mathbb{N}$，令 $Y=\{ i \in \mathbb{N} \mid i\leq m \}$，则

$$
T_{m}=\sum_{i \in Y}a_{f(i)}=\sum_{i \in f[Y]}a_{i}
$$

由于 $f$ 是双射，从而存在 $N$ 使得 $f[Y]\subset \{ i \in \mathbb{N} \mid i\leq N \}$，于是 $T_{m}\leq \sum_{i=0}^{N}a_{i}=S_{N}$，因此 $L'\leq L$.

反之，利用双射 $f^{-1}$，互换 $S_{n}$ 与 $T_{m}$ 的位置，可得 $L\leq L'$，则有 $L=L'$，这就完成了证明。

现在有了非负级数的重排定理，我们可以将其推广到绝对收敛级数上。

**定理 6.4.2** 绝对收敛级数的重排

设 $\sum_{i=0}^{\infty}a_{i}$ 是一个绝对收敛级数，$f\colon \mathbb{N}\to \mathbb{N}$ 是双射，则级数 $\sum_{i=0}^{\infty}a_{f(i)}$ 绝对收敛，且与原级数有相同的和。

**证明**

对级数 $\sum_{i=0}^{\infty}|a_{i}|$ 应用 6.4.1，从而级数 $\sum_{i=0}^{\infty}|a_{f(i)}|$ 收敛且与 $\sum_{i=0}^{\infty}|a_{i}|$ 有相同的和。

设 $L=\sum_{i=0}^{\infty}a_{i}$，我们要证明 $\sum_{i=0}^{\infty}a_{f(i)}=L$，即对任意 $\varepsilon>0$，存在 $M$ 使得对任意 $m>M$ 有 $|\sum_{i=0}^{m}a_{f(i)}-L|<\varepsilon$.

由于 $\sum_{i=0}^{\infty}|a_{i}|$ 收敛，于是存在 $N_{1}$ 使得对任意 $q>p>N_{1}$ 有 $\sum_{i=p}^{q} |a_{i}|<\varepsilon$. 由于 $L=\sum_{i=0}^{\infty}a_{i}$，故存在 $N>N_{1}$ 使得对任意 $n>N$ 有 $|\sum_{i=0}^{n}a_{i}-L|<\varepsilon$.

序列 $(f^{-1}(n))_{n=0}^{N+1}$ 是有限的，从而存在 $M$ 使得对任意 $0\leq n\leq N+1$ 有 $f^{-1}(n)\leq M$，从而 $\{ n \in \mathbb{N} \mid n\leq N+1 \}\subset \{ f(i) \mid i\leq M \}$，于是对任意 $m>M$ 有

$$
\sum_{i=0}^{m} a_{f(i)}=\sum_{i=0}^{N+1} a_{i}+\sum_{i \in X}a_{i}
$$

其中 $X=\{ f(i) \mid i\leq m \}\setminus \{ n \in \mathbb{N} \mid n\leq N+1 \}$. 由于 $X$ 是有限集，于是存在 $q>N+2$ 使得 $X \subset \{ i \in \mathbb{N} \mid N+2\leq i\leq q \}$，从而

$$
\left| \sum_{i=0}^{m} a_{f(i)}-\sum_{i=0}^{N+1} a_{i} \right| =\left| \sum_{i \in X}a_{i} \right| \leq \sum_{i=N+2}^{q} |a_{i}|<\varepsilon
$$

综上，我们有 $|\sum_{i=0}^{m}a_{f(i)}-L|<2\varepsilon$，这就完成了证明。

于是我们证明了：绝对收敛级数的重排不改变它的和。然而，出乎意料地，当一个级数条件收敛时，对它进行重排会发生非常不好的结果。事实上，我们有一个定理指出：对一个条件收敛的级数进行重排，可以使其收敛于**任何**实数，甚至发散。我们之后会证明这一点。

总而言之，对于绝对收敛级数，我们熟知的有限级数的性质可以自然的推广到无穷级数上，然而，对于条件收敛级数，我们就需要小心对待，因为对它重排可能会得到错误的结果。