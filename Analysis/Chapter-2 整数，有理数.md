本章我们来定义**整数**和**有理数**。在我们的直观思维中，整数是通过减法引入的：两个自然数相减后得到的数不是自然数，因此我们需要引入负数以保持减法的封闭性。

然而，这种方法是不严谨的，它是一个循环论证：只有在整数上才能定义减法（ $b-a=b+(-a)$ ），但现在我们却要使用减法来定义整数。不过，这不是说我们的直观思维就是错的，相反，我们正是按照减法的思路定义整数的，我们只需要规避这个循环论证，这可以通过使用**形式减法**来完成。

我们把两个自然数 $(m,n)$ 放在一起表示做形式减法，但现在这只是一个有序对，要显示其“减法”的内涵，我们就需要对其进行限定，比如 $(1,0)$，$(2,1)$，$(3,2)$ 等等就减法的角度来说应当是相等的，我们把这种广义的相等性称为**等价关系**。

# Section 1: 等价关系与等价类

**定义 2.1.1** 等价关系（equivalence relation）

集合 $X$ 上的关系 $\sim \subset X\times X$ 是一个**等价关系**如果其满足：

- 自反性：$x\sim x$
- 对称性：$x\sim y\implies y\sim x$
- 传递性：$x\sim y,y\sim z\implies x\sim z$

等价关系是对相等关系 $\Delta=\{ (x,x) \mid x \in X \}$ 的一个自然推广，反之，相等关系是 $X$ 上最小的等价关系。

我们在有限维向量空间 2 中提到，向量空间 $V$ 中在等价关系 $v-w \in U$ 下相互等价的向量构成了仿射子集 $v+U$，所有的仿射子集构成了商空间 $V / U$，这就是一个**等价类**与**商集**的例子。

**定义 2.1.2** 等价类（equivalence class），商集（quotient set）

设 $\sim$ 是 $X$ 上的等价关系，$x \in X$，定义 $x$ 的**等价类**为

$$
[x]=\{ y \in X \mid y\sim x \}
$$

$X$ 关于 $\sim$ 的所有等价类构成的集合记作

$$
X / \sim =\{ [x] \in \mathscr{P}(X) \mid x \in X \}
$$

称为 $X$ 关于 $\sim$ 的**商集**。

下面我们推导一些关于等价关系的基本性质。

**定理 2.1.3**

设 $\sim$ 是 $X$ 上的等价关系，则：

1. $x\sim y \iff [x]=[y]$
2. $[x]\neq [y]\implies [x]\cap [y]=\varnothing$

**证明**

设 $x \sim y$，设 $t \in X$，则 $t \in [x] \iff t\sim x \iff t\sim y \iff t \in [y]$.

反之，设 $[x]=[y]$，则 $x \in [y]$，从而 $x \sim y$.

对于 2，我们证明其逆否命题。设 $[x]\cap [y]\neq \varnothing$，则有 $t \in X$ 使得 $t \sim x$ 且 $t \sim y$，于是 $x \sim y$，因此 $[x]=[y]$.

以上两个性质表明商集 $X / \sim$ 是 $X$ 的一个**分割**，具体来说，就是：

**定义 2.1.4** 分割（partition）

集合 $X$ 的子集族 $P \subset \mathscr{P}(X)$ 是 $X$ 的一个**分割**如果其满足：

1. $\bigcup P=X$
2. $P$ 的元素非空且对于任意 $a,b \in P$ 有 $a \cap b=\varnothing$.

下面的定理表明，$X$ 上的等价关系与 $X$ 的分割是一一对应的。

**定理 2.1.5**

设 $\sim$ 是 $X$ 上的等价关系，则 $X / \sim$ 是 $X$ 的一个分割。反之，$X$ 的每个分割 $P$ 都诱导了 $X$ 上的一个等价关系 $\sim$，使得 $P=X / \sim$.

**证明**

任取 $x \in X$，有 $x \in [x] \in X / \sim$，从而 $x \in \bigcup (X / \sim)$，再由定理 2.1.3 的 2 可知 $X / \sim$ 是 $X$ 的一个分割。

给定分割 $P$，定义 $X$ 上的关系 $\sim$ 如下：

$$
x \sim y \iff \exists T \in P(x,y \in T)
$$

自反性和对称性是显然的，现在考虑传递性。设 $x \sim y,y \sim z$，则有 $T\in P$ 使得 $x,y \in T$，根据分割的定义，$y$ 属于且只属于 $T$，因此 $y \sim z$ 表明 $z \in T$，于是 $x \sim z$. 因此 $\sim$ 是 $X$ 上的等价关系，且 $X / \sim = P$.

利用等价关系，我们就可以来定义整数了。

# Section 2: 整数

之前提到整数应当作为自然数对的形式减法，因此我们在 $\mathbb{N}^2=\mathbb{N}\times \mathbb{N}$ 上定义等价关系 $\sim$ 如下：

$$
(m,n) \sim (p,q) \iff m+q=n+p
$$

> 先验地看，这就是说 $m-n=p-q \iff m+q=n+p$.

整数集 $\mathbb{Z}$（integer）则被定义为 $\mathbb{N}^2$ 关于 $\sim$ 的商集：

$$
\mathbb{Z}=\mathbb{N}^2 / \sim =\{ [(m,n)] \mid m,n \in \mathbb{N} \}
$$

## 加法

按我们的先验直观，两个整数的加法应该按如下方式定义：

$$
[(m,n)] + [(p,q)] = [(m+p,n+q)]
$$

但这引出了一个问题：当 $(m,n) \sim(m_{1},n_{1}),(p,q)\sim (p_{1},q_{1})$ 时，是否总是有 $(m+p,n+q)\sim(m_{1}+p_{1},n_{1}+q_{1})$？换句话说，我们的运算是良定义的（well-defined）吗？这是一个需要证明的问题。

设 $m+n_{1}=n+m_{1},p+q_{1}=q+p_{1}$，相加可得

$$
m+p+n_{1}+q_{1}=n+q+m_{1}+p_{1}
$$

即 $(m+p,n+q)\sim(m_{1}+p_{1},n_{1}+q_{1})$，于是我们可以定义：

**定义 2.2.1** $\mathbb{Z}$ 上的加法

设 $[(m,n)],[(p,q)] \in \mathbb{Z}$，定义 $\mathbb{Z}$ 上的**加法**为

$$
[(m,n)]+[(p,q)]=[(m+p,n+q)]
$$

根据定义，我们知道 $[(p,q)]+[(m,n)]=[(p+m,q+n)]$，再由自然数的加法交换律，我们就立即证明了 $\mathbb{Z}$ 上的加法具有交换律。类似地，由自然数的加法结合律可以得到整数的加法结合律。

下面我们考虑 $\mathbb{Z}$ 中的一个元素

$$
[(0,0)]=\{ (0,0),(1,1),(2,2),\dots \}
$$

它满足对任意 $a \in \mathbb{Z}$ 有 $a+[(0,0)]=a$. 我们称该元素为 $\mathbb{Z}$ 上的**加法单位元**，记作 $\overline{0}=[(0,0)]$. 我们可以证明加法单位元是唯一的，因为

$$
\overline{0}_{1}=\overline{0}_{1}+\overline{0}_{2}=\overline{0}_{2}
$$

接下来我们可以定义**负元**的概念，这也是我们定义整数的最初目的。

设 $[(m,n)] \in \mathbb{Z}$，在 $\mathbb{Z}$ 中有另一个元素 $[(n,m)]$ 满足：

$$
[(m,n)]+[(n,m)]=[(m+n,m+n)]=\overline{0}
$$

我们就称 $[(n,m)]$ 是 $[(m,n)]$ 的**加法逆元**或**负元**，记作 $-[(m,n)]$. 和加法单位元一样，我们可以证明加法逆元是唯一的，因为

$$
(-a)_{1}=(-a)_{1}+\overline{0}=(-a)_{1}+a+(-a)_{2}=\overline{0}+(-a)_{2}=(-a)_{2}
$$

这条性质是 $\mathbb{N}$ 所不具备的。

现在，我们就可以定义 $\mathbb{Z}$ 上的减法了：

**定义 2.2.2** $\mathbb{Z}$ 上的减法

设 $a,b \in \mathbb{Z}$，定义 $\mathbb{Z}$ 上的**减法**为

$$
b-a=b+(-a)
$$

## 乘法

**定义 2.2.3** $\mathbb{Z}$ 上的乘法

设 $[(m,n)],[(p,q)] \in \mathbb{Z}$，定义 $\mathbb{Z}$ 上的**乘法**为

$$
[(m,n)]\cdot [(p,q)]=[(mp+nq,mq+np)]
$$

> 先验地看，此即 $(m-n)(p-q)=(mp+nq)-(mq+np)$.

读者可以自行验证以上定义的乘法是良定义的。

利用自然数上乘法的性质，我们可以证明 $\mathbb{Z}$ 上的乘法是交换的、结合的、并且对加法有分配律。

我们也可以证明 $\mathbb{Z}$ 没有零因子。

**定理 2.2.4**

设 $a,b \in \mathbb{Z},a\cdot b=\overline{0}$，则 $a=\overline{0}$ 或 $b=\overline{0}$.

**证明**

设 $a=[(m,n)],b=[(p,q)]$，则有 $mp+nq=mq+np$. 根据对称性，不妨假设 $m<n,p<q$，则有 $n=m+k,q=p+r,k,r\neq 0$，从而有 $kr=0$，这与 $k,r\neq 0$ 矛盾。

下面我们考虑 $\mathbb{Z}$ 中的元素 $[(1,0)]$，满足 $a \cdot [(1,0)]=a$，该元素称为 $\mathbb{Z}$ 的**乘法单位元**，记作 $\overline{1}=[(1,0)]$. 可以证明乘法单位元是唯一的。

由于 $(0,0)$ 与 $(1,0)$ 不等价，因此有 $\overline{0}\neq \overline{1}$.

综合上述讨论，我们有如下定理：

**定理 2.2.5**

三元组 $(\mathbb{Z},+,\cdot)$ 是一个**交换环**（commutative ring），即对任意 $a,b,c \in \mathbb{Z}$ 有：

- 交换性：$a+b=b+a,ab=ba$
- 结合性：$(a+b)+c=a+(b+c),(ab)c=a(bc)$
- 加法单位：存在 $\overline{0}\in \mathbb{Z}$ 使得 $a+\overline{0}=a$
- 加法逆元：存在 $-a \in \mathbb{Z}$ 使得 $a+(-a)=\overline{0}$
- 乘法单位：存在 $\overline{1}\in \mathbb{Z}$ 使得 $\overline{1} \cdot a=a$
- 分配性：$a(b+c)=ab+ac$

## 序关系

**定义 2.2.6** $\mathbb{Z}$ 上的序

设 $[(m,n)],[(p,q)] \in \mathbb{Z}$，定义 $\mathbb{Z}$ 上的**序**为

$$
[(m,n)]<[(p,q)] \iff m+q<n+p
$$

设 $(m,n)\sim(m_{1},n_{1}),(p,q)\sim(p_{1},q_{1})$，我们要证

$$
m+q<n+p \iff m_{1}+q_{1}<n_{1}+p_{1}
$$

事实上，根据 $m+n_{1}=n+m_{1},p+q_{1}=q+p_{1}$ 立即得到

$$
m+q+n_{1}+p_{1}=n+p+m_{1}+q_{1}
$$

即证序关系的良定性。

$\mathbb{Z}$ 上的序关系有如下性质：

**定理 2.2.7**

对任意 $a,b,c \in \mathbb{Z}$ 有：

1. 反自反性：$a \not< a$
2. 传递性：$a<b,b<c\implies a<c$
3. 三分律：$a<b,a=b,a>b$ 有且仅有一个成立
4. 加法保序性：$a<b\implies a+c<b+c$
5. 乘法保序性：如果 $c>\overline{0}$，则 $a<b\implies ac<bc$

**证明**

1-4 直接继承于自然数的相应性质，下面我们来证明 5.

设 $a=[(m,n)],b=[(p,q)],c=[(s,t)]$，则

$$
ac=[(ms+nt,mt+ns)],bc=[(ps+qt,pt+qs)]
$$

$c>\overline{0}$，故 $s>t$，设 $s=t+u,u\neq 0$. 设 $a<b$，即 $m+q<n+p$，则 $(m+q)u<(n+p)u$，于是（利用加法保序性）

$$
(m+q)s+(n+p)t<(n+p)s+(m+q)t
$$

即 $ms+nt+pt+qs<mt+ns+ps+qt$，即 $ac<bc$.

## 自然数的同构嵌入

现在我们考虑 $\mathbb{Z}$ 的一个子集

$$
\overline{\mathbb{N}}=\{ [(0,0)],[(1,0)],[(2,0)],\dots \}
$$

记 $\overline{n}=[(n,0)]$，则 $\overline{\mathbb{N}}$ 有如下性质：

1. $\overline{m}+\overline{n}=\overline{m+n}$
2. $\overline{m}\cdot \overline{n}=\overline{m\cdot n}$
3. $m<n \implies  \overline{m}<\overline{n}$

因此 $\overline{\mathbb{N}}$ 构成了 $\mathbb{Z}$ 的一个封闭子集。设 $n \in \mathbb{N}$，令 $f(n)=\overline{n}$，则 $f\colon \mathbb{N}\to \overline{\mathbb{N}}$ 是一个双射，且满足：

$$
\begin{gather*}
\begin{cases}
f(0)=\overline{0} \\
f(1)=\overline{1} \\
f(m+n)=f(m)+f(n) \\
f(m\cdot n)=f(m)\cdot f(n) \\
m<n \implies f(m)<f(n)
\end{cases}
\end{gather*}
$$

这就是说 $\mathbb{N}$ 同构于 $\overline{\mathbb{N}}$，并且 $f$ 将 $\mathbb{N}$ 同构嵌入 $\mathbb{Z}$ 中。

现在我们来考虑 $\mathbb{Z}$ 中的一般元素 $[(m,n)]$，我们分两种情况讨论。

如果 $m\geq n$，则 $m=n+k$，从而 $[(m,n)]=[(n+k,n)]=[(k,0)]=\overline{k}$.

如果 $m<n$，则 $n=m+k$，从而 $[(m,n)]=[(m,m+k)]=[(0,k)]=-\overline{k}$.

因此 $\mathbb{Z}$ 中的元素或者是 $\mathbb{N}$ 中的元素，或者是 $\mathbb{N}$ 中元素的负元，于是 $\mathbb{Z}$ 形如

$$
\mathbb{Z}=\{ \dots,-\overline{2},-\overline{1},\overline{0},\overline{1},\overline{2},\dots \}
$$

现在，我们把 $\overline{n}$ 等同于 $n$，并把 $\overline{\mathbb{N}}$ 等同于 $\mathbb{N}$，就得到了整数的算术结构 $(\mathbb{Z},0,1,+,\cdot,<)$，其中整数集 $\mathbb{Z}$ 包含自然数集 $\mathbb{N}$ 作为它的子集，它是我们对自然数上的加法进行扩张的结果。

# Section 3: 有理数

和整数类似，有理数是将除法引入整数的结果，同样，我们也需要使用形式除法来规避循环论证。本节中所有关于整数的运算性质都看作已知，它们可以通过上一节的基本性质推导出来。

在 $\mathbb{Z}\times(\mathbb{Z}\setminus \{ 0 \})$ 上定义等价关系 $\sim$ 如下：

$$
(a,b)\sim (c,d) \iff ad=bc
$$

> 先验地看，这就是说 $\dfrac{a}{b}=\dfrac{c}{d} \iff ad=bc$.

有理数 $\mathbb{Q}$（rational number）被定义为 $\mathbb{Z}\times(\mathbb{Z}\setminus \{ 0 \})$ 关于 $\sim$ 的商集：

$$
\mathbb{Q}=(\mathbb{Z}\times(\mathbb{Z}\setminus \{ 0 \})) / \sim =\{ [(a,b)] \mid a,b \in \mathbb{Z},b\neq 0 \}
$$

## 加法

**定义 2.3.1** $\mathbb{Q}$ 上的加法

设 $[(a,b)],[(c,d)] \in \mathbb{Q}$，定义 $\mathbb{Q}$ 上的**加法**如下：

$$
[(a,b)]+[(c,d)]=[(ad+bc,bd)]
$$

> 先验地看，这就是 $\dfrac{a}{b}+\dfrac{c}{d}=\dfrac{ad+bc}{bd}$.

读者可以验证上述定义是良定的。

给定 $[(a,b)],[(c,d)]\in \mathbb{Q}$，我们有：

$$
[(a,b)]+[(c,d)]=[(ad+bc,bd)]=[(cb+da,db)]=[(c,d)]+[(a,b)]
$$

从而我们从整数的交换律推导出了有理数的加法交换律。同理，我们可以从整数的结合律推导出有理数的加法结合律。

在 $\mathbb{Q}$ 上有一个元素 $[(0,1)]$ 满足 $r+[(0,1)]=r$，则 $\overline{0}=[(0,1)]$ 是 $\mathbb{Q}$ 上的加法单位元。

取 $[(a,b)] \in \mathbb{Q}$，则有 $[(-a,b)]\in \mathbb{Q}$ 满足 $[(a,b)]+[(-a,b)]=\overline{0}$，于是 $[(-a,b)]$ 就是 $[(a,b)]$ 的加法逆元，记作 $-[(a,b)]$.

最后我们来定义 $\mathbb{Q}$ 上的减法。

**定义 2.3.2** $\mathbb{Q}$ 上的减法

设 $r,s \in \mathbb{Q}$，定义 $\mathbb{Q}$ 上的**减法**为：

$$
r-s=r+(-s)
$$

## 乘法

**定义 2.3.3** $\mathbb{Q}$ 上的乘法

设 $[(a,b)],[(c,d)]\in \mathbb{Q}$，定义 $\mathbb{Q}$ 上的**乘法**为：

$$
[(a,b)]\cdot [(c,d)]=[(ac,bd)]
$$

同样，读者可以自行验证上述定义是良定的。

根据整数的乘法交换律和结合律，我们可以推导出有理数的乘法交换律和结合律。有理数的分配律同样可以由整数的分配律得到。

$\mathbb{Q}$ 上有一个元素 $[(1,1)]\neq \overline{0}$ 满足 $r \cdot [(1,1)]=r$，则 $\overline{1}=[(1,1)]$ 是 $\mathbb{Q}$ 上的乘法单位元。

下面的性质是 $\mathbb{Z}$ 所不具备的。

对于 $\overline{0}\neq [(a,b)]\in \mathbb{Q}$，有 $[(b,a)]\in \mathbb{Q}$ 使得 $[(a,b)]\cdot [(b,a)]=\overline{1}$，称 $[(b,a)]$ 为 $[(a,b)]$ 的**乘法逆元**，记作 $[(a,b)]^{-1}$. 可以证明乘法逆元是唯一的。

有了乘法逆元，我们就可以来定义除法。

**定义 2.3.4** $\mathbb{Q}$ 上的除法

设 $r,s \in \mathbb{Q},s\neq \overline{0}$，定义 $\mathbb{Q}$ 上的**除法**为

$$
r / s=r\cdot s^{-1}
$$

综合以上讨论，我们有：

**定理 2.3.5**

三元组 $(\mathbb{Q},+,\cdot)$ 是一个**域**（field），即对任意 $r,s,t \in \mathbb{Q}$ 有：

- 交换性：$r+s=s+r,rs=sr$
- 结合性：$(r+s)+t=r+(s+t),(rs)t=r(st)$
- 加法单位：存在 $\overline{0}\in \mathbb{Q}$ 使得 $r+\overline{0}=r$
- 加法逆元：存在 $-r\in \mathbb{Q}$ 使得 $r+(-r)=\overline{0}$
- 乘法单位：存在 $\overline{1}\in \mathbb{Q}$ 使得 $\overline{1}\cdot r=r$
- 乘法逆元：如果 $r\neq \overline{0}$ 则存在 $r^{-1}\in \mathbb{Q}$ 使得 $r\cdot r^{-1}=\overline{1}$
- 分配性：$r(s+t)=rs+rt$

## 序关系

**定义 2.3.6** $\mathbb{Q}$ 上的序

设 $[(a,b)],[(c,d)]\in \mathbb{Q}$ 且 $b,d>0$（如果 $b<0$ 则取 $(-a,-b)$ ），定义 $\mathbb{Q}$ 上的**序**为

$$
[(a,b)]<[(c,d)] \iff ad<bc
$$

读者可以验证上述定义是良定的。

$\mathbb{Q}$ 上的序具有以下性质：

**定理 2.3.7**

对任意 $r,s,t\in \mathbb{Q}$ 有：

1. 反自反性：$r \not< r$
2. 传递性：$r<s,s<t \implies r<t$
3. 三分律：$r<s,r=s,r>s$ 有且仅有一个成立
4. 加法保序性：$r<s \implies r+t<s+t$
5. 乘法保序性：如果 $t>\overline{0}$，则 $r<s \implies rt<st$

**证明**

1-4 继承自整数的相应性质，现在来证明 5.

设 $r=[(a,b)],s=[(c,d)],t=[(e,f)]$，其中 $b,d,e,f>0,ad<bc$.

根据定义，我们有

$$
rt=[(ae,bf)],st=[(ce,df)]
$$

我们要证 $aedf<bfce$，即 $(ad)(ef)<(bc)(ef)$，根据整数的保序性即证。

根据上述性质，我们有：

**定理 2.3.8**

四元组 $(\mathbb{Q},+,\cdot,<)$ 是一个**序域**（ordered field），即：

1. $(\mathbb{Q},+,\cdot)$ 是一个域
2. $<$ 具有传递性和三分律
3. $<$ 对 $+$ 和 $\cdot$ 具有保序性

如果 $r>\overline{0}$，则称 $r$ 是**正的**（positive），如果 $r<\overline{0}$，则称 $r$ 是**负的**（negative）。

## 整数的同构嵌入

现考虑 $\mathbb{Q}$ 的子集

$$
\overline{\mathbb{Z}}=\{ \dots,[(-2,1)],[(-1,1)],[(0,1)],[(1,1)],[(2,1)],\dots \}
$$

令 $\overline{n}=[(n,1)]$，则有：

1. $\overline{-n}=-\overline{n}$
2. $\overline{m}+\overline{n}=\overline{m+n}$
3. $\overline{m}\cdot  \overline{n}=\overline{m\cdot n}$
4. $m<n \implies  \overline{m}<\overline{n}$

因此 $\overline{\mathbb{Z}}$ 构成了 $\mathbb{Q}$ 的一个封闭子集。设 $n\in \mathbb{Z}$，令 $f(n)=\overline{n}$，则 $f\colon \mathbb{Z}\to \overline{\mathbb{Z}}$ 是一个双射，并且满足：

$$
\begin{gather*}
\begin{cases}
f(0)=\overline{0} \\
f(1)=\overline{1} \\
f(m+n)=f(m)+f(n) \\
f(m\cdot n)=f(m)\cdot f(n) \\
m<n \implies f(m)<f(n)
\end{cases}
\end{gather*}
$$

于是 $\overline{\mathbb{Z}}$ 同构于 $\mathbb{Z}$，且 $f$ 将 $\mathbb{Z}$ 同构嵌入 $\mathbb{Q}$ 中。

现在考虑 $\mathbb{Q}$ 的一般元素 $[(a,b)]$，根据乘法的定义，我们有

$$
[(a,b)]=[(a,1)]\cdot [(1,b)]=[(a,1)]\cdot [(b,1)]^{-1}=[(a,1)] / [(b,1)]
$$

这就是说 $\mathbb{Q}$ 中的元素或者是 $\overline{\mathbb{Z}}$ 中的元素，或者是 $\overline{\mathbb{Z}}$ 中两个元素相除的结果。我们将 $\overline{n}$ 等同于 $n$，将 $\overline{\mathbb{Z}}$ 等同于 $\mathbb{Z}$，并且将除法 $a / b$ 写成分数形式 $\dfrac{a}{b}$，则 $\mathbb{Q}$ 形如

$$
\mathbb{Q}=\left\{ \dfrac{a}{b} \mid a,b\in \mathbb{Z},b\neq 0 \right\}
$$

于是我们就得到了有理数算术结构 $(\mathbb{Q},0,1,+,\cdot,<)$，其中有理数集 $\mathbb{Q}$ 包含整数集 $\mathbb{Z}$ 作为它的子集，它是我们对整数上的乘法进行扩张的结果。

## 绝对值与指数

**定义 2.3.9** 绝对值（absolute value）

设 $q \in \mathbb{Q}$，定义 $q$ 的**绝对值**为

$$
|q|=\begin{cases}
q  & ,  q\geq 0 \\
-q  & ,  q<0
\end{cases}
$$

绝对值有如下性质：

**定理 2.3.10**

设 $p,q \in \mathbb{Q}$，则：

1. $|pq| = |p| |q|$，特别地，$| -q | = |q|$
2. 正定性：$|q| >0,q\neq 0$；$|0|=0$
3. 三角不等式：$|p+q| \leq |p|+|q|$

**证明**

(1). 如果 $p>0,q>0$，则 $|pq|=pq,|p|=p,|q|=q$，于是 $|pq| = |p||q|$.

如果 $p>0,q<0$，则 $|pq|=-pq,|p|=p,|q|=-q$，于是 $|pq| = |p||q|$.

其它情况同理。

根据定义立即得到 2.

(3). 如果 $p>0,q>0$，则 $|p+q|=p+q= |p|+|q|$.

如果 $p>0,q<0,p+q\geq 0$，则 $|p+q|=p+q\leq p = |p|\leq |p|+|q|$.

其它情况同理。

接下来我们考虑乘方。我们已在自然数上定义了指数，现在我们要把定义扩展到有理数上。首先我们定义：

**定义 2.3.11** $\mathbb{Q}$ 上的乘方

设 $q \in \mathbb{Q}$，递归地定义 $\mathbb{Q}$ 上的**乘方**为：

$$
\begin{gather*}
\begin{cases}
q^0=1 \\
q^{n'}=q^{n}\cdot q
\end{cases}
\end{gather*}
$$

乘方有以下性质：

**定理 2.3.12**

设 $p,q \in \mathbb{Q},m,n \in \mathbb{N}$，则有：

1. $q^{m+n}=q^{m}\cdot q^{n},(q^m)^n=q^{mn},(pq)^n=p^n q^n$
2. 设 $n>0$，则 $q^n=0 \iff q=0$
3. 设 $n>0$，则 $0\leq p<q \implies 0\leq p^n<q^n$
4. $|q^n| = |q|^n$

**证明**

(1). 对 $n$ 归纳。$q^{m+0}=q^{m}=q^{m}\cdot q^{0}$，假设 $q^{m+n}=q^{m}\cdot q^{n}$，则

$$
q^{m+n'}=q^{(m+n)'}=q^{m+n}\cdot q=q^{m}\cdot q^{n}\cdot q=q^{m}\cdot q^{n'}
$$

其余的两个等式可以同样地对 $n$ 归纳证明。

(2). $q=0 \implies q^n=0$ 是显然的。现对 $n\geq 1$ 归纳证明 $q^n =0\implies q=0$.

$n=1$ 是显然的。假设 $q^n=0 \implies q=0$，设 $q^{n'}=q^n \cdot q=0$，则 $q^n=0$ 或 $q=0$，无论是 $q^n=0$ 还是 $q=0$ 我们都有 $q=0$，即证。

(3). 对 $n$ 归纳。$n=1$ 是显然的，假设 $0\leq p<q\implies 0\leq p^n<q^n$，当 $p=0$ 时显然成立，因此设 $0< p<q$，则 $0< p^{n'} < q\cdot p^{n} < q^{n'}$，即证。

(4). 对 $n$ 归纳并使用 $|pq| = |p||q|$ 即可。

下面我们要定义 $q^{-n}$，我们希望定理 2.3.12 仍然成立，根据这个原则，我们给出如下定义：

**定义 2.3.13** $\mathbb{Q}$ 上的乘方

设 $q \in \mathbb{Q},q\neq 0,n \in \mathbb{Z}$，定义 $\mathbb{Q}$ 上的乘方为

$$
q^n =\begin{cases}
q^n &, n\geq 0 \\
(q^{-1})^{-n} &, n<0
\end{cases}
$$

我们可以验证上述定义满足下列性质：

**定理 2.3.14**

设 $p,q \in \mathbb{Q},p,q\neq 0,m,n \in \mathbb{Z}$，则：

1. $q^{m+n}=q^{m}\cdot q^{n},(q^m)^n=q^{mn},(pq)^n=p^n q^n$
2. 设 $0<p<q$，如果 $n>0$ 则 $0<p^n<q^n$，如果 $n<0$ 则 $0<q^n<p^n$
3. 设 $p,q>0,n\neq 0$，则 $p^n=q^n \implies p=q$
4. $|q^n| = |q|^n$

**证明**

1 和 4 继承自定理 2.3.12 的 1 和 4. 对于 2，我们只需证明 $0<q^{-1}<p^{-1}$.

设 $p=[(a,b)],q=[(c,d)]$，则 $0<ad<bc$，且 $q^{-1}=[(d,c)],p^{-1}=[(b,a)]$，根据定义就有 $0<q^{-1}<p^{-1}$. 再对 $|n|$ 归纳即可得到 $n<0$ 时 $0<q^n<p^n$.

(3). 对 $n$ 归纳并使用乘法消去律即可得到 $n>0$ 时 $p^n=q^n \implies p=q$.

当 $n<0$ 时，有 $q^n=(q^{-1})^{-n}$，从而有 $p^{-1}=q^{-1}$，即 $p=q$.

## 整数的分布

现在我们考虑整数与有理数相对于序关系 $<$ 是如何排列的，我们有以下定理：

**定理 2.3.15** $\mathbb{Q}$ 的 Archimedes 性

任取 $q\in \mathbb{Q}$，存在 $n \in \mathbb{N}$ 使得 $q<n$.

**证明**

若 $q\leq 0$，取 $n=1$ 即可。若 $q>0$，则 $q$ 可以表示为 $q=\dfrac{a}{b}$，其中 $a,b\in \mathbb{Z},a,b>0$. 取 $n=a+1$，则 $q\leq a<a+1=n$，这就完成了证明。

上面的定理表明：$\mathbb{N}$ 在 $\mathbb{Q}$ 中没有上界。设 $q>0$，则有：对任意 $q$，存在 $n \in \mathbb{N}$ 使得 $0<\dfrac{1}{n}<q$，即没有最小的正有理数。这一定理是我们后续引入 $\varepsilon-N$ 定义的基础。

上述定理有一个推论：

**定理 2.3.16**

任取 $q\in \mathbb{Q}$，存在唯一的整数 $n$ 使得 $n\leq q<n+1$.

**证明**

设 $q\geq 0$，令 $M=\{ n\in \mathbb{N} \mid q<n \}$，由 Archimedes 性可知 $M$ 非空，于是由 $\mathbb{N}$ 的良序性可知 $M$ 有最小元 $m$，其满足 $m-1\leq q<m$. 由 $m$ 的最小性可知 $m$ 是唯一的。

若 $q<0$，则 $p=-q>0$，令 $M=\{ n \in \mathbb{N} \mid p\leq n \}$，由上文同理可得存在唯一的 $m$ 使得 $m-1<p\leq m$，于是 $-m\leq q< 1-m$，即证。

这个唯一的整数 $n$ 称为 $q$ 的**整数部分**（integer part），记作 $n=\lfloor q \rfloor$.

现在我们考虑有理数自身的分布，我们可以证明任意两个有理数 $p,q$ 之间一定有另一个有理数。事实上，取 $r=\dfrac{p+q}{2}$ 即可。

由此，我们可以得到整数与有理数的排列方式：在一条两端无限延长的直线上，每隔一个单位长度都对应了一个整数，在两个整数之间有无限多个有理数。然而，在这条直线上还有一些无限细的空洞没有数来对应，那些位置就是所谓的**无理数**，我们引入实数的目的就是为了填补这些空洞。