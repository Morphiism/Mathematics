现在，我们来研究一类重要的函数级数，即**幂级数**。我们将首先讨论幂级数的收敛性，然后讨论其极限函数的性质，最后，我们将使用幂级数来严格地定义**指数函数**和**三角函数**。

# Section 1: 收敛性

**定义 17.1.1** 形式幂级数（formal power series）

设 $a \in \mathbb{R}$，一个以 $a$ 为中心的**形式幂级数**是形如

$$
\sum_{n=0}^{\infty} c_{n}(x-a)^{n}
$$

的表达式，其中 $(c_{n})_{n=0}^{\infty}$ 是一个与 $x$ 无关的实数序列，并称 $c_{n}$ 为 $(x-a)^{n}$ 项的**系数**。

之所以称这些幂级数是形式的，这是因为我们还未给 $x$ 赋值：我们还不知道级数在哪些点上收敛，下面我们就来研究这一点。

**定义 17.1.2** 收敛半径（radius of convergence）

设 $\sum_{n=0}^{\infty}c_{n}(x-a)^{n}$ 是一个形式幂级数，定义其**收敛半径**为

$$
R=\dfrac{1}{\limsup_{ n \to \infty } |c_{n}|^{1/n}}
$$

仅在此处我们定义 $\dfrac{1}{0}=+\infty,\dfrac{1}{+\infty}=0$.

下面的定理解释了 $R$ 为什么叫做收敛半径。

**定理 17.1.3**

设 $\sum_{n=0}^{\infty}c_{n}(x-a)^{n}$ 是一个形式幂级数，其收敛半径为 $R$，则：

1. 如果 $|x-a|>R$，那么级数 $\sum_{n=0}^{\infty}c_{n}(x-a)^{n}$ 发散。
2. 如果 $|x-a|<R$，那么级数 $\sum_{n=0}^{\infty}c_{n}(x-a)^{n}$ 绝对收敛。

**证明**

设 $a_{n}=|c_{n}||x-a|^{n}$，则

$$
\limsup_{ n \to \infty }a_{n}^{1/n}=\limsup_{ n \to \infty } |c_{n}|^{1/n} |x-a|= \dfrac{|x-a|}{R}
$$

根据根值判别法，当 $|x-a|>R$ 时，级数发散，当 $|x-a|<R$ 时，级数绝对收敛。

现在，我们假定 $R>0$，那么根据 Weierstrass M 判别法，我们可以得到如下结果：

**定理 17.1.4**

设 $\sum_{n=0}^{\infty}c_{n}(x-a)^{n}$ 是一个形式幂级数，其收敛半径为 $R>0$，函数 $f\colon (a-R,a+R)\to \mathbb{R}$ 是级数的逐点极限，则有：

1. 对任意 $0<r<R$，级数在 $[a-r,a+r]$ 上一致收敛于 $f$，从而 $f$ 在 $(a-R,a+R)$ 上连续。
2. $f$ 在 $(a-R,a+R)$ 上可微，并且对任意 $0<r<R$，级数 $\sum_{n=1}^{\infty}nc_{n}(x-a)^{n-1}$ 在 $[a-r,a+r]$ 上一致收敛于 $f'$.
3. 对任意 $a-R<y<z<a+R$，有 $$
\int_{y}^{z}f=\sum_{n=0}^{\infty} c_{n} \dfrac{(z-a)^{n+1}-(y-a)^{n+1}}{n+1}
$$

**证明**

对每个 $n$，我们有 $\lVert c_{n}(x-a)^{n} \rVert_{\infty}=|c_{n}|r^{n}$，其中 $0<r<R$，根据根值判别法，级数 $\sum_{n=0}^{\infty}\lVert c_{n}(x-a)^{n} \rVert_{\infty}$ 收敛，故由 Weierstrass M 判别法知级数 $\sum_{n=0}^{\infty}c_{n}(x-a)^{n}$ 在 $[a-r,a+r]$ 上一致收敛。

由于每个 $c_{n}(x-a)^{n}$ 都连续，故 $f$ 在 $[a-r,a+r]$ 上连续，根据 $r$ 的任意性得 $f$ 在 $(a-R,a+R)$ 上连续。又由于每个 $c_{n}(x-a)^{n}$ 都 Riemann 可积，故

$$
\int_{y}^{z}f=\sum_{n=0}^{\infty} c_{n} \int_{y}^{z} (x-a)^{n}\mathrm{d} x=\sum_{n=0}^{\infty} c_{n}\dfrac{(z-a)^{n+1}-(y-a)^{n+1}}{n+1}
$$

同样，对每个 $n$，我们有 $\lVert nc_{n}(x-a)^{n-1} \rVert_{\infty}=n|c_{n}|r^{n-1}$，由根值判别法知其收敛，从而级数 $\sum_{n=1}^{\infty}nc_{n}(x-a)^{n-1}$ 一致收敛，根据定理 16.5.4 知其在 $[a-r,a+r]$ 上一致收敛于 $f'$，由 $r$ 的任意性得 $f$ 在 $(a-R,a+R)$ 上可微。

由以上定理可见，幂级数的性质是非常良好的，我们自然会想到，是否可以用幂级数来逼近某个函数？我们把可以表示为幂级数的函数起了一个特殊的名字，称为**实解析函数**。

# Section 2: 实解析函数

**定义 17.2.1** 实解析函数（real analytic function）

设 $E\subset \mathbb{R}$，函数 $f\colon E\to \mathbb{R}$，$a \in \mathrm{Int}(E)$，如果存在 $r>0$ 使得某个以 $a$ 为中心的幂级数 $\sum_{n=0}^{\infty}c_{n}(x-a)^{n}$ 在 $(a-r,a+r)\subset E$ 上逐点收敛于 $f$，那么称 $f$ 在 $a$ 处是**实解析的**。如果 $E$ 是开集并且 $f$ 在 $E$ 的每一点处都是实解析的，则称 $f$ 在 $E$ 上是**实解析函数**。

例如，函数 $\dfrac{1}{1-x}$ 在 $x=0$ 处是实解析的，因为幂级数 $\sum_{n=0}^{\infty}x^{n}$ 在 $(-1,1)$ 上逐点收敛于 $\dfrac{1}{1-x}$.

根据定理 17.1.4 我们知道，实解析函数是连续且可微的，事实上，我们还可以更进一步。

**定义 17.2.2** $k$ 次可微

设 $E\subset \mathbb{R}$，称函数 $f\colon E\to \mathbb{R}$ 在 $E$ 上 $1$ **次可微**，如果 $f$ 是可微的；称 $f$ 在 $E$ 上 $k$ **次可微**，如果 $f'$ 在 $E$ 上 $k-1$ 次可微；称 $f$ 在 $E$ 上**光滑**，如果对任意 $k \in \mathbb{N}$，$f$ 在 $E$ 上都是 $k$ 次可微的；我们定义任意函数都是 $0$ 次可微的。

我们定义 $f^{(0)}=f$，并且递归地定义 $f^{(k+1)}=(f^{(k)})'$.

我们可以证明，实解析函数是光滑的。

**定理 17.2.3**

设 $E\subset \mathbb{R}$，$a \in \mathrm{Int}(E)$，$f\colon E\to \mathbb{R}$ 在 $a$ 处实解析，存在 $r>0$ 使得对任意 $x \in(a-r,a+r)$ 有

$$
f(x)=\sum_{n=0}^{\infty} c_{n}(x-a)^{n}
$$

那么对任意 $k \in \mathbb{N}$，$f$ 在 $(a-r,a+r)$ 上 $k$ 次可微，并且对任意 $x \in(a-r,a+r)$ 有

$$
f^{(k)}(x)=\sum_{n=0}^{\infty} c_{n+k} \dfrac{(n+k)!}{n!} (x-a)^{n}
$$

**证明**

我们对 $k$ 使用归纳法。$k=0$ 的情况是平凡的。假设 $f$ 是 $k$ 次可微的，并且有

$$
f^{(k)}(x)=\sum_{n=0}^{\infty} c_{n+k} \dfrac{(n+k)!}{n!} (x-a)^{n},x \in(a-r,a+r)
$$

那么根据定理 17.1.4，级数

$$
\sum_{n=0}^{\infty} c_{n+k+1} \dfrac{(n+k+1)!}{n!} (x-a)^{n}
$$

在 $[a-r',a+r'],0<r'<r$ 上一致收敛于 $f^{(k+1)}$，从而 $f$ 在 $(a-r,a+r)$ 上 $k+1$ 次可微，这就完成了证明。

由上面的定理，我们可以得到推论：

**定理 17.2.4** Taylor 公式

设 $E\subset \mathbb{R}$，$a \in \mathrm{Int}(E)$，$f\colon E\to \mathbb{R}$ 在 $a$ 处实解析，存在 $r>0$ 使得对任意 $x \in(a-r,a+r)$ 有

$$
f(x)=\sum_{n=0}^{\infty} c_{n}(x-a)^{n}
$$

那么对任意 $k \in \mathbb{N}$ 有 $f^{(k)}(a)=k!c_{k}$，从而对任意 $x \in(a-r,a+r)$ 有

$$
f(x)=\sum_{n=0}^{\infty} \dfrac{f^{(n)}(a)}{n!}(x-a)^{n}
$$

级数 $\sum_{n=0}^{\infty} \dfrac{f^{(n)}(a)}{n!}(x-a)^{n}$ 被称为 $f$ 在 $a$ 点的 **Taylor 级数**，因此，定理 17.2.4 表明，如果一个函数是实解析的，那么它就等于它的 Taylor 级数。反之也成立，根据定义即证。

**定理 17.2.5**

设 $E\subset \mathbb{R}$，$a \in \mathrm{Int}(E)$，函数 $f\colon E\to \mathbb{R}$ 在区间 $(a-r,a+r)$ 上光滑，定义余项

$$
R_{n}(x)=f(x)-\sum_{k=0}^{n} \dfrac{f^{(k)}(a)}{k!}(x-a)^{k},x \in(a-r,a+r)
$$

如果 $(R_{n})_{n=0}^{\infty}$ 在 $(a-r,a+r)$ 上逐点收敛于 $0$，那么 $f$ 在 $a$ 处实解析。

换句话说，$f$ 在 $a$ 处实解析当且仅当 $f$ 在 $a$ 附近等于它的 Taylor 级数，从而我们就可以使用 Lagrange 余项定理（11.3.1）来分析 $f$ 的解析性。

Taylor 公式的另一个推论是，一个实解析函数的幂级数展开式是唯一的。

**定理 17.2.6**

设 $E\subset \mathbb{R}$，$a \in \mathrm{Int}(E)$，$f\colon E\to \mathbb{R}$ 在 $a$ 处实解析，如果 $f$ 在 $a$ 处有两个幂级数展开式

$$
f(x)=\sum_{n=0}^{\infty} c_{n}(x-a)^{n}=\sum_{n=0}^{\infty} d_{n}(x-a)^{n}
$$

那么对任意 $n \in \mathbb{N}$ 有 $c_{n}=d_{n}$.

**证明**

根据 Taylor 公式，对任意 $n \in \mathbb{N}$ 有 $f^{(n)}(a)=n!c_{n}=n!d_{n}$，即 $c_{n}=d_{n}$.

一个实解析函数在一点上最多有一个幂级数展开式，但在不同的点上可以有不同的展开式，比如，函数 $\dfrac{1}{1-x}$ 在 $(-1,1)$ 上有展开式 $\sum_{n=0}^{\infty}x^{n}$，但它在 $\dfrac{1}{2}$ 处也有展开式

$$
\dfrac{1}{1-x}=\dfrac{2}{1-2\left( x-\frac{1}{2} \right)}=\sum_{n=0}^{\infty} 2^{n+1}\left( x-\dfrac{1}{2} \right)^{n}
$$

对于这个幂级数的收敛性，我们可以说什么呢？下面的定理给出了答案。

**定理 17.2.7**

设 $E\subset \mathbb{R}$，$a \in \mathrm{Int}(E)$，$f\colon E\to \mathbb{R}$ 在 $a$ 处实解析，存在 $r>0$ 使得对任意 $x \in(a-r,a+r)$ 有

$$
f(x)=\sum_{n=0}^{\infty} c_{n}(x-a)^{n}
$$

那么 $f$ 在 $(a-r,a+r)$ 上实解析。

**证明**

设 $s>0$，区间 $(b-s,b+s)\subset(a-r,a+r)$，从而有 $|a-b|\leq r-s$.

由于幂级数 $\sum_{n=0}^{\infty}c_{n}(x-a)^{n}$ 在 $(a-r,a+r)$ 上收敛，故对任意 $0<\varepsilon<r$ 有 $\limsup_{ n \to \infty }|c_{n}|^{1/n}<\dfrac{1}{r-\varepsilon}$，于是存在 $N$ 使得对任意 $n>N$ 有 $|c_{n}|<(r-\varepsilon)^{-n}$，令

$$
C=\max(|c_{0}|,|c_{1}|(r-\varepsilon),\dots,|c_{N}|(r-\varepsilon)^{N},1)
$$

则对任意 $n$ 有 $|c_{n}|\leq C(r-\varepsilon)^{-n}$.

现在定义

$$
d_{m}=\sum_{n=m}^{\infty} \binom{ n }{ m } (b-a)^{n-m}c_{n}
$$

则根据 $\displaystyle \dfrac{r}{(r-x)^{m+1}}=\sum_{n=m}^{\infty}\binom{ n }{ m }x^{n-m}r^{-n}$（对 $\dfrac{r}{r-x}$ 求导数）得

$$
\begin{align}
\sum_{n=m}^{\infty} \binom{ n }{ m } |b-a|^{n-m}|c_{n}| &\leq C \sum_{n=m}^{\infty} \binom{ n }{ m } (r-s)^{n-m}(r-\varepsilon)^{-n} \\
& =C \dfrac{r-\varepsilon}{(s-\varepsilon)^{m+1}}
\end{align}
$$

根据比较准则，每个 $d_{m}$ 都绝对收敛，并且对任意 $0<\varepsilon<r$ 都存在 $C$ 使得 $|d_{m}|\leq C(s-\varepsilon)^{-m}$，从而对任意 $x \in(b-s,b+s)$ 有

$$
\sum_{m=0}^{\infty} |d_{m}||x-b|^{m}\leq C \sum_{m=0}^{\infty} \left( \dfrac{|x-b|}{s-\varepsilon} \right)^{m}=C\sum_{m=0}^{\infty} \left( \dfrac{s'}{s-\varepsilon} \right)^{m}
$$

其中 $0<s'<s$，取 $\varepsilon$ 使得 $\dfrac{s'}{s-\varepsilon}<1$，则 $\sum_{m=0}^{\infty}d_{m}(x-b)^{m}$ 绝对收敛，从而根据 Fubini 定理有

$$
\begin{align}
\sum_{m=0}^{\infty} d_{m}(x-b)^{m} &= \sum_{m=0}^{\infty} \sum_{n=m}^{\infty} \binom{ n }{ m } (b-a)^{n-m}c_{n}(x-b)^{m} \\
&= \sum_{n=0}^{\infty} \sum_{m=0}^{n} \binom{ n }{ m } (b-a)^{n-m}c_{n}(x-b)^{m} \\
&= \sum_{n=0}^{\infty} c_{n}(x-a)^{n}=f(x)
\end{align}
$$

即 $f$ 在 $b$ 处实解析，从而 $f$ 在 $(a-r,a+r)$ 上实解析。

简单来说，如果 $f$ 在某点 $a$ 处实解析，那么 $f$ 在 $a$ 的一个邻域中实解析，这就是**解析延拓**的基础，我来解释一下这个结论。

假设解析函数 $f$ 只在 $(a-r,a+r)$ 上有定义 $f(x)=\sum_{n=0}^{\infty}c_{n}(x-a)^{n}$，那么 $f$ 在某点 $b \in(a-r,a+r)$ 处有幂级数展开

$$
f(x)=\sum_{m=0}^{\infty} d_{m}(x-b)^{m}
$$

其系数由 17.2.7 的证明中的 $d_{m}$ 给出。然而，级数 $\sum_{m=0}^{\infty} d_{m}(x-b)^{m}$ 可以在 $(a-r,a+r)$ 以外的点处收敛（复分析的定理指出：幂级数的收敛半径等于中心与最近的奇点的距离），那么在这些外部的点处，我们就可以用幂级数的极限值来定义 $f(x)$，这样的定义有一个优点，即 $f$ 在扩大后的定义域内仍然是解析的，这就是“解析延拓”名字的由来。

由此，我们也就知道了为什么要研究**复解析函数**：实解析延拓的性质远远没有复解析延拓的性质好。比如说，函数 $\dfrac{1}{1-x}$ 在 $x=1$ 处有一个奇点，因此，在实数上，我们绝不可能从 $x=0$ 处将 $f$ 延拓到 $x>1$ 的区域。但在复平面上，我们可以沿着 $x=1$ 周围的一条环路，安全地绕过这个奇点，并将函数解析延拓到整个复平面上。

# Section 3: Abel 定理与乘积

前面我们研究了幂级数 $\sum_{n=0}^{\infty}c_{n}(x-a)^{n}$ 在收敛半径内部与外部的行为：当 $|x-a|<R$ 时，级数绝对收敛，当 $|x-a|>R$ 时，级数发散。然而，当 $x=a+R$ 或者 $a-R$ 时，情况就比较复杂了：级数可能收敛，也可能发散。不过，接下来我们要证明的 **Abel 定理**指出：如果级数在边界处收敛，那么它就有很好的性质，特别地，它是连续的。

在证明之前，我们首先需要一个引理：

**定理 17.3.1** 分部求和法（summation by parts）

设实数序列 $(a_{n})_{n=0}^{\infty},(b_{n})_{n=0}^{\infty}$ 分别收敛于 $A,B$，则级数 $\sum_{i=0}^{\infty}(a_{i+1}-a_{i})b_{i}$ 收敛当且仅当级数 $\sum_{i=0}^{\infty}a_{i+1}(b_{i+1}-b_{i})$ 收敛，并且

$$
\sum_{i=0}^{\infty} (a_{i+1}-a_{i})b_{i}=AB-a_{0}b_{0}-\sum_{i=0}^{\infty} a_{i+1}(b_{i+1}-b_{i})
$$

**证明**

我们有

$$
\sum_{i=0}^{\infty} (a_{i+1}b_{i+1}-a_{i}b_{i})=\lim_{ n \to \infty } (a_{n+1}b_{n+1}-a_{0}b_{0})=AB-a_{0}b_{0}
$$

而

$$
\begin{align}
\sum_{i=0}^{n} (a_{i+1}b_{i+1}-a_{i}b_{i})&=\sum_{i=0}^{n} (a_{i+1}(b_{i+1}-b_{i})+(a_{i+1}-a_{i})b_{i}) \\
&= \sum_{i=0}^{n} a_{i+1}(b_{i+1}-b_{i})+\sum_{i=0}^{n} (a_{i+1}-a_{i})b_{i}
\end{align}
$$

故 $\sum_{i=0}^{\infty}(a_{i+1}-a_{i})b_{i}$ 收敛当且仅当 $\sum_{i=0}^{\infty}a_{i+1}(b_{i+1}-b_{i})$ 收敛，并且有

$$
\sum_{i=0}^{\infty} a_{i+1}(b_{i+1}-b_{i})+\sum_{i=0}^{\infty} (a_{i+1}-a_{i})b_{i}=AB-a_{0}b_{0}
$$

读者可以比较一下上述定理和分部积分法（定理 13.2.4），其中 $a_{i+1}-a_{i}$ 就相当于一种“离散导数”，而求和则相当于一种“离散积分”。

**定理 17.3.2** Abel 定理

设幂级数 $f(x)=\sum_{n=0}^{\infty}c_{n}(x-a)^{n}$ 的收敛半径为 $0<R<+\infty$，如果级数在 $a+R$ 处收敛，那么 $f$ 在 $a+R$ 处连续；如果级数在 $a-R$ 处收敛，那么 $f$ 在 $a-R$ 处连续。

**证明**

我们只证 $a+R$ 的部分，另一个是类似的。我们要证

$$
\lim_{ x \to a+R;|x-a|<R }\sum_{n=0}^{\infty} c_{n}(x-a)^{n}=\sum_{n=0}^{\infty} c_{n}R^{n} 
$$

令 $d_{n}=c_{n}R^{n},y=\dfrac{x-a}{R}$，则上述等式变为

$$
\lim_{ y \to 1;|y|<1 } \sum_{n=0}^{\infty}d_{n}y^{n}= \sum_{n=0}^{\infty} d_{n}
$$

记 $D=\sum_{n=0}^{\infty}d_{n}$，定义

$$
S_{n}=\sum_{i=0}^{n-1} d_{i}-D
$$

则 $\sum_{i=0}^{n}d_{i}y^{i}=\sum_{i=0}^{n}(S_{i+1}-S_{i})y^{i}$，根据分部求和公式有

$$
\sum_{n=0}^{\infty} d_{n}y^{n}=-S_{0}-\sum_{n=0}^{\infty} S_{n+1}(y^{n+1}-y^{n})=D+\sum_{n=0}^{\infty} S_{n+1}(y^{n}-y^{n+1})
$$

由于 $\lim_{ n \to \infty }S_{n}=0$，故对任意 $\varepsilon>0$，存在 $N$ 使得对任意 $n>N$ 有 $|S_{n}|<\varepsilon$. 令 $0<y<1$，则有

$$
\begin{align}
\left| \sum_{n=0}^{\infty} S_{n+1}(y^{n}-y^{n+1}) \right| &\leq \sum_{n=0}^{\infty} |S_{n+1}|(y^{n}-y^{n+1}) \\
&= \sum_{n=0}^{N} |S_{n+1}|(y^{n}-y^{n+1})+\sum_{n=N+1}^{\infty} |S_{n+1}|(y^{n}-y^{n+1})  \\
&\leq \sum_{n=0}^{N} |S_{n+1}|(y^{n}-y^{n+1})+\varepsilon y^{N+1}
\end{align}
$$

令 $y\to 1$，则有

$$
\lim_{ y \to 1;y \in(0,1) } \left( \sum_{n=0}^{N} |S_{n+1}|(y^{n}-y^{n+1})+\varepsilon y^{N+1} \right)=\varepsilon
$$

根据 $\varepsilon$ 的任意性得

$$
\lim_{ y \to 1;y \in(0,1) } \sum_{n=0}^{\infty} S_{n+1}(y^{n}-y^{n+1})=0
$$

即证 $\lim_{ y \to 1;y \in(0,1) }\sum_{n=0}^{\infty}d_{n}y^{n}=D$.

下面，我们来考虑两个实解析函数的代数。两个实解析函数的和显然是实解析的，并且有

$$
f(x)+g(x)=\sum_{n=0}^{\infty} (c_{n}+d_{n})(x-a)^{n}
$$

现在，我们考虑两个实解析函数的乘积。

**定理 17.3.3**

设 $f,g$ 都是 $(a-r,a+r)\to \mathbb{R}$ 的实解析函数，其幂级数展开式分别为

$$
f(x)=\sum_{n=0}^{\infty} c_{n}(x-a)^{n}, g(x)=\sum_{n=0}^{\infty} d_{n}(x-a)^{n}
$$

那么 $fg$ 在 $(a-r,a+r)$ 也是实解析的，并且对任意 $x \in(a-r,a+r)$ 有

$$
fg(x)=\sum_{n=0}^{\infty} \sum_{m=0}^{n} c_{m}d_{n-m} (x-a)^{n}
$$

**证明**

设 $x \in(a-r,a+r)$，由于 $f,g$ 在 $x$ 处绝对收敛，故可以定义

$$
C=\sum_{n=0}^{\infty} |c_{n}(x-a)^{n}|,D=\sum_{n=0}^{\infty} |d_{n}(x-a)^{n}|
$$

对于 $N \in \mathbb{N}$，我们有

$$
\sum_{n=0}^{N} \sum_{m=0}^{\infty} |c_{n}(x-a)^{n}||d_{m}(x-a)^{m}| = \sum_{n=0}^{N} |c_{n}(x-a)^{n}|D\leq CD
$$

故级数 $\sum_{n=0}^{\infty} \sum_{m=0}^{\infty} c_{n}(x-a)^{n}d_{m}(x-a)^{m}$ 绝对收敛。现在我们用两种方法来计算这个和，首先有

$$
\sum_{n=0}^{\infty} \sum_{m=0}^{\infty} c_{n}(x-a)^{n}d_{m}(x-a)^{m}=\sum_{n=0}^{\infty} c_{n}(x-a)^{n}g(x)=f(x)g(x)
$$

另一边，我们有

$$
\begin{align}
\sum_{n=0}^{\infty} \sum_{m=0}^{\infty} c_{n}(x-a)^{n}d_{m}(x-a)^{m} &= \sum_{n=0}^{\infty} \sum_{m=0}^{\infty} c_{n}d_{m}(x-a)^{n+m} \\
&= \sum_{n=0}^{\infty} \sum_{k=n}^{\infty} c_{n}d_{k-n}(x-a)^{k}
\end{align}
$$

其中 $k=n+m$，根据 Fubini 定理有

$$
\sum_{n=0}^{\infty} \sum_{k=n}^{\infty} c_{n}d_{k-n}(x-a)^{k} = \sum_{k=0}^{\infty} \sum_{n=0}^{k} c_{n}d_{k-n}(x-a)^{k}
$$

这就完成了证明。

序列 $\left( \sum_{m=0}^{n}c_{m}d_{n-m} \right)_{n=0}^{\infty}$ 称为序列 $(c_{n})_{n=0}^{\infty}$ 和 $(d_{n})_{n=0}^{\infty}$ 的**卷积**，它是连续卷积（定义 16.6.6）的离散对应。

# Section 4: 指数与对数

利用幂级数，我们就可以为我们常用的一些数学函数奠定一个严格的基础。我们首先从指数函数开始。

**定义 17.4.1** 指数函数（exponential function）

对任意 $x \in \mathbb{R}$，定义**指数函数**为

$$
\exp(x)=\sum_{n=0}^{\infty} \dfrac{x^{n}}{n!}
$$

**定理 17.4.2**

对任意 $x,y \in \mathbb{R}$，我们有：

1. $\exp$ 是 $\mathbb{R}$ 上的实解析函数
2. $\exp'(x)=\exp(x)$
3. $\exp(x+y)=\exp(x)\exp(y)$
4. $\exp$ 在 $\mathbb{R}$ 上严格单调递增，其值域为 $(0,+\infty)$

**证明**

根据比值判别法，$\exp$ 的收敛半径为 $+\infty$，故对任意 $x \in \mathbb{R}$，级数 $\sum_{n=0}^{\infty} \dfrac{x^{n}}{n!}$ 绝对收敛，因而是 $\mathbb{R}$ 上的实解析函数，根据逐项求导定理有

$$
\exp'(x)=\sum_{n=1}^{\infty} \dfrac{x^{n-1}}{(n-1)!}=\sum_{n=0}^{\infty} \dfrac{x^{n}}{n!}=\exp(x)
$$

设 $x,y \in \mathbb{R}$，则有

$$
\begin{align}
\exp(x+y)&=\sum_{n=0}^{\infty} \dfrac{(x+y)^{n}}{n!} \\
&= \sum_{n=0}^{\infty} \sum_{m=0}^{n} \binom{ n }{ m } \dfrac{1}{n!} x^{m}y^{n-m} \\
&= \sum_{n=0}^{\infty} \sum_{m=0}^{n} \dfrac{x^{m}}{m!} \dfrac{y^{n-m}}{(n-m)!} \\
&= \sum_{m=0}^{\infty} \sum_{n=m}^{\infty} \dfrac{x^{m}}{m!} \dfrac{y^{n-m}}{(n-m)!} \\
&= \exp(x)\exp(y)
\end{align}
$$

由此，我们知道 $\exp(0)=1$，并且 $\exp(-x)=\dfrac{1}{\exp(x)}$. 当 $x>0$ 时，$\exp'(x)=\exp(x)>1+x>1$，从而 $\exp$ 在 $[0,+\infty)$ 上严格递增。再根据 $\exp(-x)\exp(x)=1$ 知 $\exp$ 在 $(-\infty,0]$ 上严格递增，从而 $\exp$ 是严格递增函数。

最后，由于 $\exp(x)>1+x,x>0$，故 $\lim_{ x \to +\infty }\exp(x)=+\infty$，进而有 $\lim_{ x \to -\infty }\exp(x)=0$，根据介值定理，其值域为 $(0,+\infty)$.

现在，我们将引入重要常数：**自然底数** $e$，它与指数函数有极为密切的关联。

**定义 17.4.3** 自然底数 $e$

定义**自然底数**为

$$
e=\exp(1)=\sum_{n=0}^{\infty} \dfrac{1}{n!}
$$

**定理 17.4.4**

对任意 $x \in \mathbb{R}$，我们有 $e^{x}=\exp(x)$.

**证明**

利用 $\exp(x+y)=\exp(x)\exp(y)$ 和归纳法，我们可知对任意有理数 $q$，有 $e^{q}=\exp(q)$. 设 $x \in \mathbb{R}$，则存在一个有理数序列 $(q_{n})$，其极限为 $x$，根据指数的连续性有

$$
e^{x}=\lim_{ n \to \infty } e^{q_{n}}=\lim_{ n \to \infty } \exp(q_{n})=\exp(x)
$$

你可能以前见过指数函数，并且也求过它的 Taylor 展开式。然而，事实上，指数函数是由幂级数**定义**的，这与我们通常的学习顺序不同。

**定义 17.4.5** 对数函数（logarithmic function）

定义**对数函数** $\ln\colon (0,+\infty)\to \mathbb{R}$ 为 $\exp$ 的反函数。

**定理 17.4.6**

对任意 $x,y \in (0,+\infty)$，我们有：

1. $\ln$ 在 $(0,+\infty)$ 上可微且严格单调递增，$\ln'(x)=\dfrac{1}{x}$
2. $\ln(xy)=\ln(x)+\ln(y)$
3. $\ln(x^{y})=y \ln(x)$
4. 对任意 $x \in(-1,1)$，有 $$
\ln(1-x)=-\sum_{n=1}^{\infty} \dfrac{x^{n}}{n}
$$

**证明**

由于 $\exp$ 在 $\mathbb{R}$ 上可微且严格递增，故 $\ln$ 在 $(0,+\infty)$ 上连续且严格递增，由于 $\exp'(x)>0$，故 $\ln$ 可微，并且有 $\ln'(x)= \dfrac{1}{\exp'(\ln(x))}=\dfrac{1}{x}$.

设 $x=\exp(s),y=\exp(t)$，则

$$
\begin{gather}
\ln(xy)=\ln(\exp(s+t))=s+t=\ln(x)+\ln(y) \\
\ln(x^{y})=\ln(e^{y s})=ys=y \ln(x)
\end{gather}
$$

设 $0<r<1$，则级数 $\sum_{n=0}^{\infty}x^{n}$ 在 $[-r,r]$ 上一致收敛于 $\dfrac{1}{1-x}$，从而有

$$
-\ln(1-r)=\int_{0}^{r} \dfrac{1}{1-x}\mathrm{d} x=\sum_{n=0}^{\infty} \int_{0}^{r} x^{n}\mathrm{d} x=\sum_{n=0}^{\infty} \dfrac{r^{n+1}}{n+1}
$$

由 $r$ 的任意性即证。

在 $\ln(1-x)$ 的幂级数展开式中将中心换成 $x=1$，则有

$$
\ln(x)=\sum_{n=1}^{\infty} \dfrac{(-1)^{n+1}}{n}(x-1)^{n},x \in(0,2)
$$

由交错级数判别法（6.2.8）知，级数 $\sum_{n=1}^{\infty} \dfrac{(-1)^{n+1}}{n}$ 收敛，从而由 Abel 定理知

$$
\ln 2=\sum_{n=1}^{\infty} \dfrac{(-1)^{n+1}}{n}=1-\dfrac{1}{2}+\dfrac{1}{3}-\dfrac{1}{4}+\cdots
$$

最后，我们来证明 $\ln$ 在 $(0,+\infty)$ 上是实解析的。

**定理 17.4.7**

函数 $\ln$ 在 $(0,+\infty)$ 上实解析。

**证明**

设 $a \in(0,+\infty)$，则有

$$
\ln\left( \dfrac{x}{a} \right)=\sum_{n=1}^{\infty} \dfrac{(-1)^{n+1}}{n!}\left( \dfrac{x}{a}-1 \right)^{n},x \in(0,2a)
$$

从而有

$$
\ln(x)=\ln(a)+\sum_{n=1}^{\infty} \dfrac{(-1)^{n+1}}{n!a^{n}}(x-a)^{n},x \in(0,2a)
$$

即 $\ln$ 在 $a$ 处实解析，即证。

# Section 5: 复数与三角函数

为了定义三角函数，我们需要对**复数**有一定的了解，特别地，我们要对**复指数函数**有一定了解。

一般来说，一个复数就是形如 $z=a+bi$ 的表达式，其中 $i^{2}=-1$. 但这并没有告诉我们如何对复数进行运算。为了严格地构造复数，我们首先要将 $a+bi$ 还原为实数的有序对 $(a,b)$，然后再定义其加法和乘法。

**定义 17.5.1** 复数（complex number）

**复数集**定义为 $\mathbb{C}=\mathbb{R}^{2}$，其上的**加法**定义为

$$
(a,b)+(c,d)=(a+c,b+d)
$$

**乘法**定义为

$$
(a,b)(c,d)=(ac-bd,ad+bc)
$$

$\mathbb{C}$ 上的**标准度量** $d(z,w)=d_{l^{2}}(z,w)$，**绝对值**定义为 $|z|=d(z,(0,0))$.

复数 $z=(a,b)$ 的**共轭**定义为 $\overline{z}=(a,-b)$，**实部**定义为 $\mathrm{Re}(z)=a$，**虚部**定义为 $\mathrm{Im}(z)=b$.

通过简单的代数计算，我们就可以得到以下定理：

**定理 17.5.2**

$(\mathbb{C},+,\cdot)$ 是一个域，并且它包含 $(\mathbb{R},+,\cdot)$ 作为它的子域。

事实上，实数集 $\mathbb{R}$ 同构于 $\{ (x,0)\in \mathbb{C}\mid x \in \mathbb{R} \}$，从而我们可以将 $x$ 与 $(x,0)$ 等同起来。现在我们令 $i=(0,1)$，那么有 $i^{2}=(-1,0)=-1$，于是我们可以将 $z=(a,b)$ 写成 $z=a+bi$.

下面我们给出一些关于复数共轭的性质，它们都非常容易证明。

**定理 17.5.3**

对任意 $z,w \in \mathbb{C}$，有

1. $\overline{z+w}=\overline{z}+\overline{w},\overline{zw}=\overline{z}\cdot  \overline{w}$
2. $\overline{\overline{z}}=z$
3. $\overline{z}=\overline{w}\iff z=w$
4. $\overline{z}=z \iff z \in \mathbb{R}$

现在，我们来考虑 $\mathbb{C}$ 的度量空间性质。我们从定义里面看到，$\mathbb{C}$ 与 $\mathbb{R}^{2}$ 的唯一区别就在于 $\mathbb{C}$ 上的复乘法，因此，$\mathbb{R}^{2}$ 上的度量空间性质可以无缝地迁移到 $\mathbb{C}$ 上来。

**定理 17.5.4**

对任意 $z,w \in \mathbb{C}$，有

1. $d(z,w)=|z-w|$
2. $z \overline{z}=|z|^{2}$
3. $|zw|=|z||w|$
4. $|\overline{z}|=|z|$
5. $|z+w|\leq|z|+|w|$

利用定理 14.1.8，我们得到以下定理：

**定理 17.5.5**

设 $(z_{n})_{n=0}^{\infty}$ 是一个复数序列，则在标准度量下 $\lim_{ n \to \infty }z_{n}=z$ 当且仅当 $\lim_{ n \to \infty }\mathrm{Re}(z_{n})=\mathrm{Re}(z)$ 且 $\lim_{ n \to \infty }\mathrm{Im}(z_{n})=\mathrm{Im}(z)$.

此外，我们还有：

**定理 17.5.6**

$(\mathbb{C},d)$ 是一个完备且连通的度量空间。

**证明**

由于

$$
|\mathrm{Re}(z_{n})-\mathrm{Re}(z_{m})|=|\mathrm{Re}(z_{n}-z_{m})|\leq|z_{n}-z_{m}|
$$

同理 $|\mathrm{Im}(z_{n})-\mathrm{Im}(z_{m})|\leq|z_{n}-z_{m}|$，故如果 $(z_{n})$ 是 $\mathbb{C}$ 中的 Cauchy 序列，那么 $(\mathrm{Re}(z_{n})),(\mathrm{Im}(z_{n}))$ 就是 $\mathbb{R}$ 中的 Cauchy 序列。由 $\mathbb{R}$ 的完备性知 $\mathbb{C}$ 是完备的。

给定两点 $z=a+bi,w=c+di$，可以构造连续函数 $\gamma\colon [0,1]\to \mathbb{C}$ 为

$$
\gamma(t)=(a+(c-a)t)+i(b+(d-b)t)
$$

从而根据定理 15.3.15，$\mathbb{C}$ 是连通的。

**定理 17.5.7** Heine-Borel 定理

设 $K\subset \mathbb{C}$，则 $K$ 是紧致的当且仅当 $K$ 是闭且有界的。

根据 $\mathbb{R}^{2}$ 上的 Heine-Borel 定理即证。

利用实数上的极限定律，我们可以直接得到复数的极限定律。

**定理 17.5.8**

设 $(z_{n}),(w_{n})$ 是收敛的复数序列，则有

1. $\lim_{ n \to \infty }(z_{n}+w_{n})=\lim_{ n \to \infty }z_{n}+\lim_{ n \to \infty }w_{n}$
2. $\lim_{ n \to \infty }z_{n}w_{n}=(\lim_{ n \to \infty }z_{n})(\lim_{ n \to \infty }w_{n})$
3. 如果 $w_{n}\neq 0$ 且 $\lim_{ n \to \infty }w_{n}\neq 0$，则 $\lim_{ n \to \infty }w_{n}^{-1}=(\lim_{ n \to \infty }w_{n})^{-1}$
4. $\lim_{ n \to \infty }\overline{z_{n}}=\overline{\lim_{ n \to \infty }z_{n}}$

对于一个复值函数 $f\colon X\to \mathbb{C}$，我们总可以将其写成两个实值函数

$$
f(x)=\mathrm{Re}\ f(x)+i \mathrm{Im}\ f(x)
$$

因此，我们可以将实值函数的绝大多数内容直接迁移到复值函数上，包括一致收敛理论以及本章的幂级数理论。从而我们可以仿照实指数函数来定义**复指数函数**：

**定义 17.5.9** 指数函数（exponential function）

定义**指数函数** $\exp\colon \mathbb{C}\to \mathbb{C}$ 为

$$
\exp(z)=\sum_{n=0}^{\infty} \dfrac{z^{n}}{n!}
$$

我们可以叙述并证明复级数的比值判别法，然后证明 $\exp(z)$ 在任意点 $z$ 处都绝对收敛，并且 $\exp(z+w)=\exp(z)\exp(w)$ 仍然成立。另一个有用的结果是 $\exp(\overline{z})=\overline{\exp(z)}$，可以通过对部分和 $\sum_{k=0}^{n} \dfrac{z^{k}}{k!}$ 取共轭再令 $n\to \infty$ 进行证明。利用指数函数，我们就可以在复数上定义指数：$e^{z}=\exp(z)$.

现在，我们就可以来介绍最重要的特殊函数之一：三角函数。这里，我们将使用一种解析的方式来定义，区别于通常的几何方法，解析定义的优点是，我们可以轻松地得到三角函数的分析学性质。

**定义 17.5.10** 正弦函数（sine function），余弦函数（cosine function）

定义**正弦函数** $\sin\colon \mathbb{C}\to \mathbb{C}$ 和**余弦函数** $\cos\colon \mathbb{C}\to \mathbb{C}$ 为

$$
\sin(z)=\dfrac{e^{iz}-e^{-iz}}{2i},\cos(z)=\dfrac{e^{iz}+e^{-iz}}{2}
$$

上述定义也被称为 **Euler 公式**，通过简单的变形，我们可以得到另一种形式的 Euler 公式：

$$
e^{iz}=\cos(z)+i\sin(z),e^{-iz}=\cos(z)-i\sin(z)
$$

利用 $\exp$ 的幂级数展开式，我们也可以得到

$$
\sin(z)=\sum_{n=0}^{\infty} (-1)^{n} \dfrac{z^{2n+1}}{(2n+1)!},\cos(z)=\sum_{n=0}^{\infty} (-1)^{n} \dfrac{z^{2n}}{(2n)!}
$$

利用比值判别法，我们知道 $\sin$ 和 $\cos$ 在任意点处都绝对收敛，从而在 $\mathbb{C}$ 上解析。不过，我们感兴趣的是实数上的三角函数。下面我们给出一些三角恒等式，它们几乎都可以直接从定义中推出。

**定理 17.5.11**

对任意 $x,y \in \mathbb{R}$，有

1. $\sin^{2}(x)+\cos^{2}(x)=1$，从而 $\sin,\cos$ 在 $\mathbb{R}$ 上的值域是 $[-1,1]$
2. $\sin'(x)=\cos(x),\cos'(x)=-\sin(x)$
3. $\sin(-x)=-\sin(x),\cos(-x)=\cos(x)$
4. $\sin(x+y)=\sin(x)\cos(y)+\cos(x)\sin(y)$
5. $\cos(x+y)=\cos(x)\cos(y)-\sin(x)\sin(y)$
6. $\cos(x)=\mathrm{Re}(e^{ix}),\sin(x)=\mathrm{Im}(e^{ix})$

**证明**

将 $\sin,\cos$ 的定义代入即可验证 1-3，根据幂级数展开式，我们知道对任意 $x \in \mathbb{R}$ 有 $\sin(x)\in \mathbb{R},\cos(x)\in \mathbb{R}$，从而根据 Euler 公式得 6.

对于 4 和 5，我们有

$$
\cos(x+y)+i\sin(x+y)=e^{i(x+y)}=e^{ix}e^{iy}=(\cos x+i \sin x)(\cos y+i\sin y)
$$

利用 6 分别取出实部和虚部即可。

下面我们推导一些三角函数的其它性质。

**引理 17.5.12**

存在实数 $x>0$ 使得 $\sin(x)=0$.

**证明**

假设对任意 $x>0$ 有 $\sin(x)\neq 0$，那么也有 $\cos(x)\neq 0$（否则就有 $\sin(2x)=2\sin(x)\cos(x)=0$ ），由于 $\cos(0)=1$，故对任意 $x>0$ 有 $\cos(x)>0$（否则根据介值定理可知存在一点 $x$ 使得 $\cos(x)=0$ ），根据 $\sin'(x)=\cos(x)$，这表明 $\sin$ 在 $(0,+\infty)$ 上严格递增，由于 $\sin(0)=0$，故对任意 $x>0$ 有 $\sin(x)>0$.

现在考虑函数 $\cot(x)=\dfrac{\cos(x)}{\sin(x)}$，那么 $\cot$ 在 $(0,+\infty)$ 上是正且可微的，其导数为 $\cot'(x)=- \dfrac{1}{\sin^{2}(x)}\leq -1$，从而根据微积分基本定理有

$$
\int_{x}^{x+s}\cot'(t) \mathrm{d} t=\cot(x+s)-\cot(x)\leq -s,s>0
$$

于是，当 $s\to +\infty$ 时，有 $\cot(x+s)\leq \cot(x)-s<0$，这与 $\cot$ 在 $(0,+\infty)$ 上恒正矛盾。

根据这个引理，我们就可以给出以下定义：

**定义 17.5.13** 圆周率 $\pi$

定义**圆周率**为

$$
\pi=\inf \{ x \in(0,+\infty)\mid \sin(x)=0 \}
$$

换言之，$\pi$ 是 $\sin$ 的最小的正零点。根据引理 17.5.12 中关于介值定理的论述，我们知道 $\sin$ 在 $(0,\pi)$ 上恒正，又 $\cos'(x)=-\sin(x)$，故 $\cos$ 在 $(0,\pi)$ 上严格递减，这表明 $\cos(\pi)<1$，再根据 $\sin^{2}(x)+\cos^{2}(x)=1$ 得 $\cos(\pi)=-1$，从而我们就有了著名的 **Euler 恒等式**：

$$
e^{i\pi}=\cos(\pi)+i\sin(\pi)=-1
$$

下面我们再给出一些三角恒等式。

**定理 17.5.14**

对任意 $x \in \mathbb{R}$，有

1. $\sin(x+\pi)=-\sin(x),\cos(x+\pi)=-\cos(x)$，从而 $2\pi$ 是 $\sin$ 和 $\cos$ 的最小正周期
2. $\sin$ 的零点集为 $\{ k\pi \mid k \in \mathbb{Z} \}$
3. $\cos$ 的零点集为 $\left\{  k\pi+ \dfrac{\pi}{2} \middle| k \in \mathbb{Z}  \right\}$
4. $\sin\left( x+\dfrac{\pi}{2} \right)=\cos(x),\cos\left( x+\dfrac{\pi}{2} \right)=-\sin(x)$

**证明**

对于 1，利用 17.5.11 的 4 和 5 以及 $\sin(\pi)=0,\cos(\pi)=-1$ 即得。于是，现在我们只需考察 $[0,2\pi)$ 区间内 $\sin,\cos$ 的行为即可。

我们已经有 $\sin(0)=\sin(\pi)=0$，现在我们要证没有其它零点。前面我们已经证明了 $\sin$ 在 $(0,\pi)$ 上恒正，根据性质 1 得 $\sin$ 在 $(\pi,2\pi)$ 上恒负，从而 $\sin$ 在 $[0,2\pi)$ 上只有 $0,\pi$ 两个零点，即证。

根据 $\sin(\pi)=2\sin\left( \dfrac{\pi}{2} \right)\cos\left( \dfrac{\pi}{2} \right)=0$ 并且 $\sin\left( \dfrac{\pi}{2} \right)>0$ 得 $\cos\left( \dfrac{\pi}{2} \right)=0$，从而有 $\sin\left( \dfrac{\pi}{2} \right)=1$ 以及 $\cos\left( \dfrac{3\pi}{2} \right)=0$. 由于 $\cos'(x)=-\sin(x)$，故 $\cos$ 在 $(0,\pi)$ 严格递减，在 $(\pi,2\pi)$ 严格递增，从而其零点只有 $\dfrac{\pi}{2},\dfrac{3\pi}{2}$，即证。

对于 4，利用加法公式和 $\sin\left( \dfrac{\pi}{2} \right)=1,\cos\left( \dfrac{\pi}{2} \right)=0$ 即证。

对于特殊角 $\dfrac{\pi}{3},\dfrac{\pi}{4},\dfrac{\pi}{6}$ 的三角函数值，我们可以利用二倍角公式和三倍角公式通过解代数方程求出，这里就不赘述了。

利用三角函数，我们还可以得到复数的另一种表达方式，即**极坐标形式**：

$$
z=a+bi=r(\cos \theta+i\sin \theta)=re^{i\theta},r>0,\theta \in(-\pi,\pi]
$$

根据三角函数的周期性，我们得以将 $\theta$ 限制在 $(-\pi,\pi]$ 中，通常称为 $z$ 的**辐角主值**，记作 $\mathrm{arg}(z)$.

当然，我们也可以定义其它的所有三角函数，并推导出我们熟悉的所有三角恒等式，这里我们给出一例。

**定义 17.5.15** 正切函数（tangent function）

**正切函数** $\tan\colon \left( -\dfrac{\pi}{2},\dfrac{\pi}{2} \right)\to \mathbb{R}$ 定义为

$$
\tan(x)=\dfrac{\sin(x)}{\cos(x)}
$$

利用三角函数的周期性，我们有 $\tan(x+\pi)=\tan(x)$，从而可以将 $\tan$ 的定义域周期延拓至 $\mathbb{R}\setminus\left\{  k\pi+\dfrac{\pi}{2}\mid k \in \mathbb{Z}  \right\}$ 上。不过，现在我们还是保留原来的定义域。

我们可以证明，$\tan$ 在 $\left( -\dfrac{\pi}{2},\dfrac{\pi}{2} \right)$ 上可微且严格递增，其导数为 $\tan'(x)=1+\tan^{2}(x)$，并且有 $\lim_{ x \to \pi / 2;x \in(-\pi / 2,\pi / 2) }\tan(x)=+\infty$ 和 $\lim_{ x \to -\pi / 2;x \in(-\pi / 2,\pi / 2) }\tan(x)=-\infty$，从而 $\tan$ 是 $\left( -\dfrac{\pi}{2},\dfrac{\pi}{2} \right)\to \mathbb{R}$ 的双射。

因此我们可以定义**反正切函数** $\arctan\colon \mathbb{R}\to\left( -\dfrac{\pi}{2},\dfrac{\pi}{2} \right)$，根据反函数定理，$\arctan$ 在 $\mathbb{R}$ 上可微且严格递增，其导数为 $\dfrac{1}{1+x^{2}}$，利用几何级数公式和逐项积分定理，我们有

$$
\arctan(x)=\int_{0}^{x} \dfrac{1}{1+t^{2}}\mathrm{d} t=\sum_{n=0}^{\infty} (-1)^{n} \dfrac{x^{2n+1}}{2n+1},x \in(-1,1)
$$

由于 $\sum_{n=0}^{\infty} \dfrac{(-1)^{n}}{2n+1}$ 收敛，故由 Abel 定理得

$$
\arctan(1)= \dfrac{\pi}{4}=\sum_{n=0}^{\infty} \dfrac{(-1)^{n}}{2n+1}
$$

利用这个公式（或者其它的计算式，因为上面的级数收敛得太慢了），我们就可以计算出 $\pi=3.14159\dots$

最后，我们来证明一个在上一章遗留下来的命题。

**命题 17.5.16**

定义为

$$
f(x)=\sum_{n=1}^{\infty} \dfrac{1}{4^{n}}\cos(32^{n}\pi x)
$$

的函数 $f\colon \mathbb{R}\to \mathbb{R}$ 在 $\mathbb{R}$ 上连续，但处处不可微。

**证明**

我们有 $\lVert 4^{-n}\cos(32^{n}\pi x) \rVert_{\infty}=4^{-n}$，根据 Weierstrass M 判别法，级数一致收敛，又由于每个 $4^{-n}\cos(32^{n}\pi x)$ 都连续，从而 $f$ 在 $\mathbb{R}$ 上连续。

对于整数 $j$ 和 $m\geq 1$，我们有

$$
\begin{align}
& \left| f\left( \dfrac{j+1}{32^{m}} \right)-f\left( \dfrac{j}{32^{m}} \right) \right| =\left| \sum_{n=1}^{\infty} \dfrac{\cos(32^{n-m}\pi (j+1))-\cos(32^{n-m}\pi j)}{4^{n}} \right|  \\
&= \left| \sum_{n=1}^{m-1} \dfrac{\cos(32^{n-m}\pi (j+1))-\cos(32^{n-m}\pi j)}{4^{n}}+ \dfrac{2\cos(\pi j)}{4^{m}} \right|  \\
&\geq \left| \dfrac{2\cos(\pi j)}{4^{m}} \right| - \sum_{n=1}^{m-1} \dfrac{|\cos(32^{n-m}\pi (j+1))-\cos(32^{n-m}\pi j)|}{4^{n}} \\
&\geq 2\cdot 4^{-m}-\sum_{n=1}^{m-1} \dfrac{32^{n-m}\pi}{4^{n}} \\
&\geq 2\cdot 4^{-m}-4^{-m}\sum_{n=1}^{m-1} \dfrac{\pi}{8^{m-n}} \\
&\geq 2\cdot 4^{-m}-4^{-m}\sum_{n=1}^{m-1} \dfrac{1}{2^{m-n}} \\
&> 4^{-m}
\end{align}
$$

设 $x_{0}\in \mathbb{R}$，假设 $f$ 在 $x_{0}$ 处可微，导数为 $L$，取 $\varepsilon=1$，那么存在 $\delta>0$ 使得对任意 $x \in(x_{0}-\delta,x_{0}+\delta)$ 有

$$
|f(x)-f(x_{0})-L(x-x_{0})|\leq |x-x_{0}|
$$

从而 $|f(x)-f(x_{0})|\leq(1+|L|)|x-x_{0}|$. 取 $m\geq 1$ 使得 $32^{-m}<\delta$ 并且 $8^{m}>2(1+|L|)$，设 $a=\dfrac{j}{32^{m}}\leq x_{0}<\dfrac{j+1}{32^{m}}=b$，则有

$$
4^{-m}<|f(b)-f(a)| \leq |f(b)-f(x_{0})|+|f(x_{0})-f(a)|\leq 2(1+|L|)32^{-m}
$$

即 $8^{m}<2(1+|L|)$，矛盾。故 $f$ 在 $x_{0}$ 处不可微。

可见，连续函数的行为有时候会变得非常病态。此外，我们观察一下这个 $f$ 的结构：它是由无限个三角函数相加得到的，与幂级数（多项式级数）只能表达实解析函数不同，三角级数可以表示很多函数。这就启发我们研究形如

$$
a_{0}+\sum_{n=1}^{\infty} (a_{n}\cos(n\pi x)+b_{n}\sin(n\pi x))
$$

的函数级数，称为 **Fourier 级数**，这也是我们下一章要介绍的主要内容。