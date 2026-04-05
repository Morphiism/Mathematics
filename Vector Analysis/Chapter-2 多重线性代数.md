在上一章中，我们定义了流形上的“第一类”积分，即流形上标量场的积分。在微积分中，我们还遇到过“第二类”积分，也就是接下来的几章所要定义的**微分形式**的积分。对于形式的研究中，我们会发现现有的分析与线性代数理论不足以描述这种结构，而必须诉诸于一种更高阶的理论：多重线性代数。因此，本章我们将对这一理论进行简单的介绍。

# Section 1: 张量

**定义 2.1.1** 张量（tensor）

设 $V$ 是一个向量空间，函数 $f\colon V^{k}\to \mathbb{R}$ 称为**在第** $i$ **个变量上线性**，如果给定向量 $v_{j},j\neq i$，定义为

$$
\begin{gather}
T(v)=f(v_{1},\dots,v_{i-1},v,v_{i+1},\dots,v_{k})
\end{gather}
$$

的函数 $T\colon V\to \mathbb{R}$ 是线性的。函数 $f$ 称为是**多重线性的**，如果它在任意 $i$ 个变量上是线性的。这样的函数 $f$ 也称为一个 $k$-**张量**。$V$ 上所有 $k$-张量构成的集合记作 $T^{k}(V)$.

当 $k=1$ 时，$T^{1}(V)$ 就是 $V$ 上所有线性泛函 $f\colon V\to \mathbb{R}$ 构成的集合，通常记作 $V^{*}$，称为 $V$ 的**对偶空间**。

**定理 2.1.2**

向量空间 $V$ 上 $k$-张量的集合 $T^{k}(V)$ 是一个向量空间，如果我们定义

$$
\begin{gather}
(f+g)(v_{1},\dots,v_{k})=f(v_{1},\dots,v_{k})+g(v_{1},\dots,v_{k}) \\
(cf)(v_{1},\dots,v_{k})=cf(v_{1},\dots,v_{k})
\end{gather}
$$

**证明**

根据 $\mathbb{R}$ 的域结构，加法和数乘的交换性、结合性以及分配性是显然的。零张量为将所有 $(v_{1},\dots,v_{k})$ 映到零的函数，$f$ 的加法逆元 $-f$ 定义为

$$
\begin{gather}
(-f)(v_{1},\dots,v_{k})=-f(v_{1},\dots,v_{k})
\end{gather}
$$

这就完成了证明。

和线性映射一样，一个多重线性映射完全由它在基向量上的值决定，下面我们就来证明这一点。

**引理 2.1.3**

设 $u_{1},\dots,u_{n}$ 是向量空间 $V$ 的基，如果 $f,g\colon V^{k}\to \mathbb{R}$ 是 $V$ 上的 $k$-张量，并且

$$
\begin{gather}
f(u_{i_{1}},\dots,u_{i_{k}})=g(u_{i_{1}},\dots,u_{i_{k}})
\end{gather}
$$

对任意 $[n]$ 上的 $k$-元组 $I=(i_{1},\dots,i_{k})$ 成立，那么 $f=g$.

**证明**

任取 $V$ 上的 $k$-元组 $(v_{1},\dots,v_{k})$，我们可以将其表示为基向量的线性组合：

$$
\begin{gather}
v_{i}=\sum_{j=1}^{n} c_{ij}u_{j}
\end{gather}
$$

从而我们有

$$
\begin{align}
f(v_{1},\dots,v_{k}) &= \sum_{j_{1}=1}^{n} c_{1j_{1}} f(u_{j_{1}},v_{2},\dots,v_{k}) \\
&= \sum_{j_{1}=1}^{n} \sum_{j_{2}=1}^{n} c_{1j_{1}} c_{2j_{2}} f(u_{j_{1}},u_{j_{2}},v_{3},\dots,v_{k}) \\
&= \cdots \\
&= \sum_{1\leq j_{1},\dots,j_{k}\leq n} c_{1j_{1}}\cdots c_{kj_{k}} f(u_{j_{1}},\dots,u_{j_{k}}) \\
&= \sum_{1\leq j_{1},\dots,j_{k}\leq n} c_{1j_{1}}\cdots c_{kj_{k}} g(u_{j_{1}},\dots,u_{j_{k}}) \\
&= g(v_{1},\dots,v_{k})
\end{align}
$$

即证。

**定理 2.1.4**

设 $u_{1},\dots,u_{n}$ 是向量空间 $V$ 的基，$I=(i_{1},\dots,i_{k})$ 是 $[n]$ 上的 $k$-元组，则存在唯一的 $k$-张量 $\phi_{I}$ 使得对任意 $k$-元组 $J=(j_{1},\dots,j_{k})$，有

$$
\begin{gather}
\phi_{I}(u_{j_{1}},\dots,u_{j_{k}})=\begin{cases}
1 & , I=J \\
0 & , I\neq J
\end{cases}
\end{gather}
$$

成立。所有 $\phi_{I}$ 构成了 $T^{k}(V)$ 上的一个基。

张量 $\phi_{I}$ 称为对应于 $u_{1},\dots,u_{n}$ 的**基本** $k$-**张量**。由于它们构成了 $T^{k}(V)$ 的一个基，并且 $[n]$ 上的 $k$-元组 $I$ 共有 $n^{k}$ 个，因此 $T^{k}(V)$ 的维度为 $n^{k}$. 当 $k=1$ 时，$V^{*}$ 的基 $\phi_{1},\dots,\phi_{n}$ 称为 $u_{1},\dots,u_{n}$ 的**对偶基**。

**证明**

唯一性部分由引理 2.1.3 给出，我们来证明存在性。当 $k=1$ 时，我们定义线性映射 $\phi_{i}\colon V\to \mathbb{R}$ 为

$$
\begin{gather}
\phi_{i}(u_{j})=\begin{cases}
1 & , i=j \\
0 & , i\neq j
\end{cases}
\end{gather}
$$

则 $\phi_{1},\dots,\phi_{n}$ 为所求的 $1$-张量。对于 $k>1$，给定 $k$-元组 $I$，我们定义

$$
\begin{gather}
\phi_{I}(v_{1},\dots,v_{k})=\phi_{i_{1}}(v_{1})\cdots \phi_{i_{k}}(v_{k})
\end{gather}
$$

根据 $\phi_{i}$ 的线性性，$\phi_{I}$ 是多重线性的，并且仅在 $I=J$ 时 $\phi_{I}=1$.

下面我们来证明 $\phi_{I}$ 构成 $T^{k}(V)$ 的一个基。给定 $V$ 上的 $k$-张量 $f$，我们证明它可以唯一地写成 $\phi_{I}$ 的线性组合。对任意 $k$-元组 $I$，我们定义

$$
\begin{gather}
d_{I}=f(u_{i_{1}},\dots,u_{i_{k}})
\end{gather}
$$

然后令

$$
\begin{gather}
g=\sum_{J} d_{J} \phi_{J}
\end{gather}
$$

其中 $J$ 遍历 $[n]$ 上的所有 $k$-元组。于是根据定义，$f$ 和 $g$ 在 $(u_{i_{1}},\dots,u_{i_{k}})$ 上的值相等，从而根据引理，$f=g$. 下面证唯一性，假设另有

$$
\begin{gather}
g=\sum_{J} d_{J}'\phi_{J}
\end{gather}
$$

则

$$
\begin{gather}
\sum_{J} (d_{J}-d_{J}') \phi_{J}=0
\end{gather}
$$

任取 $J$，在上式两边求关于 $(u_{j_{1}},\dots,u_{j_{k}})$ 的值，则有 $d_{J}=d_{J}'$ 对任意 $J$ 成立，这就完成了证明。

上述定理表明，存在唯一的 $k$-张量 $f$ 使得 $f(u_{i_{1}},\dots,u_{i_{k}})=d_{I}$ 对任意 $k$-元组 $I$ 成立。因此一个 $k$-张量可以通过它在基向量的 $k$-元组上的值确定。

我们来看一个例子。考虑 $V=\mathbb{R}^{n}$，设 $e_{1},\dots,e_{n}$ 为 $\mathbb{R}^{n}$ 上的标准基，令 $\phi_{1},\dots,\phi_{n}$ 为 $T^{1}(\mathbb{R}^{n})$ 上的对偶基，则我们有

$$
\begin{gather}
\phi_{i}(x)=\phi_{i}(x_{1}e_{1}+\dots+x_{n}e_{n})=x_{i}
\end{gather}
$$

因此，$\phi_{i}$ 是向第 $i$ 个坐标的投影函数。

更一般地，给定 $k$-元组 $I=(i_{1},\dots,i_{k})$，基本张量 $\phi_{I}$ 可以表示为

$$
\begin{gather}
\phi_{I}(x_{1},\dots,x_{k})=\phi_{i_{1}}(x_{1})\cdots \phi_{i_{k}}(x_{k})
\end{gather}
$$

设 $x_{j}$ 具有分量 $x_{1j},\dots,x_{nj}$，则我们有

$$
\begin{gather}
\phi_{I}(x_{1},\dots,x_{k})=x_{i_{1}1}\cdots x_{i_{k}k}
\end{gather}
$$

因此 $\phi_{I}$ 仅仅是 $x_{1},\dots,x_{k}$ 分量的一个单项式，并且 $\mathbb{R}^{n}$ 上的一般张量是这样的单项式的线性组合。这就是说，$\mathbb{R}^{n}$ 上的 $k$-张量具有形式

$$
\begin{gather}
f(x_{1},\dots,x_{k})=\sum_{1\leq i_{1},\dots,i_{k}\leq n} d_{i_{1}\cdots i_{k}} x_{i_{1}1}\cdots x_{i_{k}k}
\end{gather}
$$

现在我们定义所谓的**张量积**，它将一个 $k$-张量和一个 $\ell$-张量组合为一个 $k+\ell$ 张量。

**定义 2.1.5** 张量积（tensor product）

设 $f$ 是 $V$ 上的 $k$-张量，$g$ 是 $V$ 上的 $\ell$-张量，定义 $V$ 上的 $k+\ell$ 张量 $f\otimes g$ 如下：

$$
\begin{gather}
(f\otimes g)(v_{1},\dots,v_{k+\ell})=f(v_{1},\dots,v_{k})g(v_{k+1},\dots,v_{k+\ell})
\end{gather}
$$

容易证明 $f\otimes g$ 是多重线性的，它称为 $f$ 与 $g$ 的**张量积**。

下面我们列出张量积的一些性质。

**定理 2.1.6**

设 $f,g,h$ 是 $V$ 上的张量，则有以下性质成立：

1. 结合性：$f\otimes(g\otimes h)=(f\otimes g)\otimes h$
2. 齐次性：$(cf)\otimes g=c(f\otimes g)=f\otimes(cg)$
3. 分配性：设 $f$ 和 $g$ 是同阶张量，则有 $$
\begin{gather}
(f+g)\otimes h=f\otimes h+g\otimes h \\
h\otimes (f+g)=h\otimes f+h\otimes g
\end{gather}
$$
4. 给定 $V$ 的基 $u_{1},\dots,u_{n}$ 以及 $k$-元组 $I=(i_{1},\dots,i_{k})$，基本张量 $\phi_{I}$ 满足方程 $$
\begin{gather}
\phi_{I}=\phi_{i_{1}}\otimes \cdots \otimes \phi_{i_{k}}
\end{gather}
$$

**证明**

根据张量积的定义，上述定理的证明是显然的。我们以 1 和 4 为例，假设 $f,g,h$ 的阶数分别为 $k,\ell,m$，则有

$$
\begin{align}
&(f\otimes (g\otimes h))(v_{1},\dots,v_{k+\ell+m})  \\
&=f(v_{1},\dots,v_{k}) g(v_{k+1},\dots,v_{k+\ell}) h(v_{k+\ell+1},\dots,v_{k+\ell+m}) \\
&=((f\otimes g)\otimes h)(v_{1},\dots,v_{k+\ell+m})
\end{align}
$$

对于 4，任取 $J=(j_{1},\dots,j_{k})$，我们有

$$
\begin{gather}
\phi_{i_{1}}\otimes \dots \otimes \phi_{i_{k}}(u_{j_{1}},\dots,u_{j_{k}})=\phi_{i_{1}}(u_{j_{1}})\cdots \phi_{i_{k}}(u_{j_{k}})=\begin{cases}
1 & , I=J \\
0 & , I\neq J
\end{cases}
\end{gather}
$$

根据定理 2.1.4 即证。

最后，我们来研究张量如何与线性映射进行相互作用。

**定义 2.1.7** 对偶映射（dual map）

设 $T\colon V\to W$ 是线性映射，我们定义其**对偶映射**

$$
\begin{gather}
T^{*}\colon T^{k}(W)\to T^{k}(V)
\end{gather}
$$

如下：如果 $f\in T^{k}(W)$ 且 $v_{1},\dots,v_{k}\in V$，那么

$$
\begin{gather}
(T^{*}f) (v_{1},\dots,v_{k})=f(T(v_{1}),\dots,T(v_{k}))
\end{gather}
$$

换言之，映射 $T^{*}f$ 是线性映射 $T\times\dots \times T\colon V^{k}\to W^{k}$ 与张量 $f$ 的复合，如下面的交换图所示：

![](2-1.png)

容易证明 $T^{*}f$ 是多重线性的，此外，映射 $T^{*}$ 自身作为张量上的函数也是线性的，下面我们给出证明。

**定理 2.1.8**

设 $T\colon V\to W$ 是线性映射，令

$$
\begin{gather}
T^{*}\colon T^{k}(W)\to T^{k}(V)
\end{gather}
$$

为其对偶映射，则其满足以下性质：

1. $T^{*}$ 是线性的
2. $T^{*}(f\otimes g)=T^{*}f \otimes T^{*}g$
3. 如果 $S\colon W\to X$ 是线性映射，则 $(ST)^{*}f=T^{*}(S^{*}f)$

**证明**

根据定义验证即可。我们以 3 为例，对任意 $k$-元组 $(v_{1},\dots,v_{k})$，有

$$
\begin{align}
(ST)^{*}f(v_{1},\dots,v_{k}) &= f(ST(v_{1}),\dots,ST(v_{k})) \\
&= S^{*} f(T(v_{1}),\dots,T(v_{k})) \\
&= T^{*}(S^{*}f)(v_{1},\dots,v_{k})
\end{align}
$$

其余两个性质同理。

下面的交换图是性质 3 的一个描述：

![](2-2.png)

# Section 2: 交错张量

本节我们将引入一类特殊的张量：**交错张量**，并推导其性质。为此，我们首先需要补充一些关于置换群的知识。

**定义 2.2.1** 置换（permutation）

设 $n\geq 1$，集合 $[n]$ 上的一个**置换** $\sigma$ 定义为一个从 $[n]$ 到其自身的双射。$[n]$ 上所有置换构成的集合记作 $S_{n}$. $S_{n}$ 与其上的复合运算一同构成了一个群，称为 $n$ **阶对称群**，该群的阶数为 $n!$.

**定义 2.2.2** 基本置换（elementary permutation）

设 $1\leq i<k$，定义 $e_{i}\in S_{k}$ 如下：对任意 $j\neq i,i+1$ 有 $e_{i}(j)=j$，且

$$
\begin{gather}
e_{i}(i)=i+1, \quad e_{i}(i+1)=i
\end{gather}
$$

我们称 $e_{i}$ 是一个**基本置换**。

注意到 $e_{i}\circ e_{i}$ 等于恒等置换 $\mathrm{id}$，因此 $e_{i}$ 的逆就是它本身。

**引理 2.2.3**

如果 $\sigma \in S_{k}\ (k\geq 2)$，那么 $\sigma$ 等于一系列基本置换的复合。

**证明**

我们来证明如果 $\sigma$ 保持前 $i-1\ (0<i\leq k)$ 个整数不变，那么它可以写成 $\sigma=\pi \circ\sigma'$，其中 $\pi$ 是基本置换的复合，$\sigma'$ 保持前 $i$ 个整数不变。接下来，我们不断对 $\sigma'$ 再次应用上述结论，直到新的 $\sigma'$ 保持前 $k$ 个整数不变，即 $\sigma'$ 为恒等置换。又由于恒等置换是基本置换的复合，这就完成了证明。

设 $\sigma$ 保持 $1,\dots,i-1$ 不变，因为 $\sigma$ 是双射，故 $\sigma(i)\neq 1,\dots,i-1$. 如果 $\sigma(i)=i$，那么我们设 $\pi=\mathrm{id},\sigma'=\sigma$ 即可。如果 $\sigma(i)=\ell>i$，那么我们令

$$
\begin{gather}
\sigma'=e_{i}\circ e_{i+1}\circ\dots \circ e_{\ell-1}\circ\sigma
\end{gather}
$$

则 $\sigma'$ 保持 $1,\dots,i-1$ 不变，并且

$$
\begin{gather}
\sigma'(i)=e_{i}\circ\dots \circ e_{\ell-1}(\ell)=i
\end{gather}
$$

取 $\pi=e_{\ell-1}\circ\dots \circ e_{i}$ 即证。

**定义 2.2.4** 逆序（inversion）

设 $\sigma \in S_{k}$，我们称满足 $i<j$ 且 $\sigma(i)>\sigma(j)$ 的整数对 $(i,j)$ 为 $\sigma$ 的一个**逆序**。定义 $\sigma$ 的**符号** $\mathrm{sgn}(\sigma)=(-1)^{\tau}$，其中 $\tau$ 为 $\sigma$ 的逆序的个数。如果 $\mathrm{sgn}(\sigma)=1$，则称 $\sigma$ 是一个**偶置换**；如果 $\mathrm{sgn}(\sigma)=-1$，则称 $\sigma$ 是一个**奇置换**。

**引理 2.2.5**

设 $\sigma,\tau \in S_{k}$，则其满足以下性质：

1. 如果 $\sigma$ 等于 $m$ 个基本置换的复合，则有 $\mathrm{sgn}(\sigma)=(-1)^{m}$
2. $\mathrm{sgn}(\sigma \circ \tau)=\mathrm{sgn}(\sigma)\mathrm{sgn}(\tau)$
3. $\mathrm{sgn}(\sigma^{-1})=\mathrm{sgn}(\sigma)$
4. 如果 $p\neq q$，且 $\tau$ 是只交换 $p$ 和 $q$ 而保持其他整数不变的置换，则 $\mathrm{sgn}(\tau)=-1$

**证明**

(1). 我们来证明对任意置换 $\sigma$ 有

$$
\begin{gather}
\mathrm{sgn}(\sigma \circ e_{\ell})=-\mathrm{sgn}(\sigma)
\end{gather}
$$

给定 $\sigma$，我们将其表示为如下形式：

$$
\begin{gather}
(\sigma(1),\dots,\sigma(\ell),\sigma(\ell+1),\dots,\sigma(k))
\end{gather}
$$

令 $\tau=\sigma \circ e_{\ell}$，则有

$$
\begin{align}
& (\tau(1),\dots,\tau(\ell),\tau(\ell+1),\dots,\tau(k)) \\
&=(\sigma(1),\dots,\sigma(\ell+1),\sigma(\ell),\dots,\sigma(k))
\end{align}
$$

我们来分别计算 $\sigma$ 和 $\tau$ 的逆序数。设 $p\neq q$，我们比较 $\sigma(p)$ 和 $\sigma(q)$ 在两个序列中的相对位置。如果 $p,q$ 都不等于 $\ell$ 或 $\ell+1$，那么 $\sigma(p),\sigma(q)$ 的位置相同；如果 $p,q$ 中的一个（不妨设为 $p$）等于 $\ell$ 或 $\ell+1$，而另一个不等于，那么在两个序列中 $\sigma(p)$ 的位置有所变化，但是 $\sigma(p)$ 与 $\sigma(q)$ 的相对位置不变：如果 $(p,q)$ 在第一个序列中是逆序，那么其在第二个序列中也是，反之亦然。

现在我们来关注 $p=\ell,q=\ell+1$ 的情况：如果 $\sigma(\ell)$ 和 $\sigma(\ell+1)$ 在第一个序列中形成逆序，那么在第二个序列中就不形成逆序，反之亦然。因此，第二个序列的逆序数或者比第一个序列多一个，或者少一个，这就完成了证明。

(2). 接下来我们来证明定理。恒等置换的符号为 $1$，将其与 $m$ 个基本置换进行复合后，其符号改变了 $m$ 次，即证性质 1. 对于 2，我们将 $\sigma$ 表示成 $m$ 个基本置换的复合，$\tau$ 表示为 $n$ 个基本置换的复合，根据 $(-1)^{m+n}=(-1)^{m}(-1)^{n}$ 即证 2. 对于 3，根据 $\sigma^{-1}\circ\sigma=\mathrm{id}$，应用性质 2 即得

$$
\begin{gather}
\mathrm{sgn}(\sigma^{-1})=\mathrm{sgn}(\sigma)^{-1}=\mathrm{sgn}(\sigma)
\end{gather}
$$

最后，假设 $p<q$，我们可以将 $\tau$ 表示为如下基本置换的复合：

$$
\begin{gather}
\tau=e_{q-1}\circ\dots\circ e_{p+1} \circ e_{p}\circ e_{p+1} \circ\dots\circ e_{q-1}
\end{gather}
$$

上式中有奇数个基本置换，故根据性质 1 有 $\mathrm{sgn}(\tau)=-1$.

现在我们来定义交错张量。

**定义 2.2.6** 对称张量（symmetric tensor），交错张量（alternating tensor）

设 $f$ 是 $V$ 上的 $k$-张量，如果 $\sigma$ 是 $[k]$ 上的置换，我们定义张量 $f^{\sigma}$ 为

$$
\begin{gather}
f^{\sigma}(v_{1},\dots,v_{k})=f(v_{\sigma(1)},\dots,v_{\sigma(k)})
\end{gather}
$$

称 $f$ 是一个**对称张量**，如果 $f^{e}=f$ 对任意基本置换 $e$ 成立；称 $f$ 是一个**交错张量**，如果 $f^{e}=-f$ 对任意基本置换 $e$ 成立。

换句话说，张量 $f$ 是对称的，如果对任意 $i$ 有

$$
\begin{gather}
f(v_{1},\dots,v_{i},v_{i+1},\dots,v_{k})=f(v_{1},\dots,v_{i+1},v_{i},\dots,v_{k})
\end{gather}
$$

张量 $f$ 是交错的，如果对任意 $i$ 有

$$
\begin{gather}
f(v_{1},\dots,v_{i},v_{i+1},\dots,v_{k})=-f(v_{1},\dots,v_{i+1},v_{i},\dots,v_{k})
\end{gather}
$$

在本系列中，我们主要对交错张量感兴趣。

向量空间 $V$ 上的 $k$ 阶交错张量构成的集合用 $\mathcal{A}^{k}(V)$ 表示。容易证明两个交错张量的线性组合仍然是交错的，因此 $\mathcal{A}^{k}(V)$ 在张量的加法和数乘下构成了 $T^{k}(V)$ 的子空间。当 $k=1$ 时，我们定义 $\mathcal{A}^{1}(V)=T^{1}(V)$.

下面我们给出一些交错张量的例子。

当 $k>1$ 时，基本张量 $\phi_{I}$ 自身是不交错的，不过，它们的特定线性组合是交错的，比如

$$
\begin{gather}
f=\phi_{ij}-\phi_{ji}
\end{gather}
$$

如果我们设 $V=\mathbb{R}^{n}$，并取其上的标准基以及与其对应的对偶基 $\phi_{i}$，那么 $f$ 可以表示为

$$
\begin{gather}
f(x,y)=x_{i}y_{j}-x_{j}y_{i}=\det \begin{bmatrix}
x_{i} & y_{i} \\
x_{j} & y_{j}
\end{bmatrix}
\end{gather}
$$

显然我们有 $f(x,y)=-f(y,x)$. 类似地，下面的张量 $g$ 也是交错的：

$$
\begin{gather}
g(x,y,z)=\det \begin{bmatrix}
x_{i} & y_{i} & z_{i} \\
x_{j} & y_{j} & z_{j} \\
x_{k} & y_{k} & z_{k}
\end{bmatrix}
\end{gather}
$$

它可以表示为基本张量的线性组合：

$$
\begin{gather}
g=\phi_{ijk}+\phi_{jki}+\phi_{kij}-\phi_{jik}-\phi_{ikj}-\phi_{kji}
\end{gather}
$$

上面的例子表明，交错张量与行列式是紧密相关的，之后我们将会谈到这一点。

现在我们来研究向量空间 $\mathcal{A}^{k}(V)$，具体来说，我们将为其找到一个基。

**引理 2.2.7**

设 $f$ 是 $V$ 上的 $k$-张量，$\sigma,\tau \in S_{k}$，则有：

1. 映射 $f\mapsto f^{\sigma}$ 是 $T^{k}(V)$ 上的线性算子，并且其满足 $(f^{\sigma})^{\tau}=f^{\tau \circ\sigma}$
2. $f$ 是交错的当且仅当对任意置换 $\sigma$ 有 $f^{\sigma}=\mathrm{sgn}(\sigma)f$；如果 $f$ 是交错的且 $v_{p}=v_{q}\ (p\neq q)$，那么 $f(v_{1},\dots,v_{k})=0$

**证明**

线性性只不过是 $(af+bg)^{\sigma}=af^{\sigma}+bg^{\sigma}$ 的重述。为证明 1，我们有

$$
\begin{align}
(f^{\sigma})^{\tau}(v_{1},\dots,v_{k})&= f^{\sigma}(v_{\tau(1)},\dots,v_{\tau(k)}) \\
&= f^{\sigma}(w_{1},\dots,w_{k}) \quad (w_{i}=v_{\tau(i)}) \\
&= f(w_{\sigma(1)},\dots,w_{\sigma(k)}) \\
&= f(v_{\tau(\sigma(1))},\dots,v_{\tau(\sigma(k))}) \\
&= f^{\tau \circ\sigma}(v_{1},\dots,v_{k})
\end{align}
$$

对于 2，设 $\sigma$ 可以表示为基本置换的复合 $e_{1}\circ \dots \circ e_{m}$，则根据性质 1 有

$$
\begin{align}
f^{\sigma}&= ((\cdots (f^{e_{m}})\cdots)^{e_{2}})^{e_{1}} \\
&= (-1)^{m}f \\
&= \mathrm{sgn}(\sigma)f
\end{align}
$$

最后，设 $\tau$ 为仅交换 $p$ 和 $q$ 的置换，由于 $v_{p}=v_{q}$，故我们有

$$
\begin{gather}
f^{\tau}(v_{1},\dots,v_{k})=f(v_{1},\dots,v_{k})
\end{gather}
$$

另一方面，由于 $\mathrm{sgn}(\tau)=-1$，故

$$
\begin{gather}
f^{\tau}(v_{1},\dots,v_{k})=-f(v_{1},\dots,v_{k})
\end{gather}
$$

这表明 $f(v_{1},\dots,v_{k})=0$.

现在我们来构造 $\mathcal{A}^{k}(V)$ 的基。当 $k=1$ 时，$\mathcal{A}^{1}(V)=T^{1}(V)$，因此我们没什么可做的。当 $k>n=\mathrm{dim}\ V$ 时，$\mathcal{A}^{k}(V)$ 是平凡的：这是因为张量 $f$ 完全由其在基向量的 $k$-元组上的值决定，而当 $k>n$ 时，必然存在一个基向量使得其在 $k$-元组中出现两次以上，根据交错性，$\mathcal{A}^{k}(V)$ 中就只有零张量。

最后，我们考虑 $1<k\leq n$ 的情况。我们首先证明 $f$ 完全由其在升序 $k$-元组上的值确定，然后我们再证明这些值可以任意地选取。

**引理 2.2.8**

设 $u_{1},\dots,u_{n}$ 是向量空间 $V$ 的基，如果 $f,g$ 是 $V$ 上的交错 $k$-张量，并且

$$
\begin{gather}
f(u_{i_{1}},\dots,u_{i_{k}})=g(u_{i_{1}},\dots,u_{i_{k}})
\end{gather}
$$

对任意 $[n]$ 上的升序 $k$-元组 $I=(i_{1},\dots,i_{k})$ 成立，那么 $f=g$.

**证明**

根据引理 2.1.3，我们只需证明 $f$ 和 $g$ 在基向量的任意 $k$-元组上的取值相同。设 $J=(j_{1},\dots,j_{k})$，如果存在 $p\neq q$ 使得 $j_{p}=j_{q}$，那么根据交错性，$f,g$ 在 $(u_{j_{1}},\dots,u_{j_{k}})$ 上的取值均为零。如果所有指标都不相同，我们取置换 $\sigma \in S_{k}$ 使得 $I=(j_{\sigma(1)},\dots,j_{\sigma(k)})$ 按升序排列，那么我们有

$$
\begin{align}
f(u_{i_{1}},\dots,u_{i_{k}})= f^{\sigma}(u_{j_{1}},\dots,u_{j_{k}})= \mathrm{sgn}(\sigma)f(u_{j_{1}},\dots,u_{j_{k}})
\end{align}
$$

类似的等式对 $g$ 也成立。由于 $f,g$ 在 $(u_{i_{1}},\dots,u_{i_{k}})$ 上相等，其在 $(u_{j_{1}},\dots,u_{j_{k}})$ 上也相等，即证。

**定理 2.2.9**

设 $u_{1},\dots,u_{n}$ 是向量空间 $V$ 的基，$I=(i_{1},\dots,i_{k})$ 是 $[n]$ 上的升序 $k$-元组，则 $V$ 上存在唯一的交错 $k$-张量 $\psi_{I}$ 使得对任意 $[n]$ 上的升序 $k$-元组 $J=(j_{1},\dots,j_{k})$ 有

$$
\begin{gather}
\psi_{I}(u_{j_{1}},\dots,u_{j_{k}})=\begin{cases}
1 & , I=J \\
0 & , I\neq J
\end{cases}
\end{gather}
$$

所有张量 $\psi_{I}$ 构成了 $\mathcal{A}^{k}(V)$ 的一个基。此外，其满足

$$
\begin{gather}
\psi_{I}=\sum_{\sigma \in S_{k}} \mathrm{sgn}(\sigma) (\phi_{I})^{\sigma}
\end{gather}
$$

张量 $\psi_{I}$ 称为 $V$ 上对应于 $u_{1},\dots,u_{n}$ 的**基本交错** $k$-**张量**。

**证明**

唯一性由引理 2.2.8 给出，为证明存在性，我们使用定理中的公式定义张量 $\psi_{I}$，并证明它满足上面的条件。

首先，我们证明 $\psi_{I}$ 是交错的。任取 $\tau \in S_{k}$，我们有

$$
\begin{align}
(\psi_{I})^{\tau}&= \sum_{\sigma} \mathrm{sgn}(\sigma)((\phi_{I})^{\sigma})^{\tau} \\
&=\sum_{\sigma} \mathrm{sgn}(\sigma)(\phi_{I})^{\tau \circ\sigma} \\
&=\mathrm{sgn}(\tau) \sum_{\sigma} \mathrm{sgn}(\tau \circ\sigma) (\phi_{I})^{\tau \circ\sigma} \\
&=\mathrm{sgn}(\tau) \psi_{I}
\end{align}
$$

因此 $\psi_{I}$ 是交错的。

下面我们证明 $\psi_{I}$ 的值与定理中所声明的一致。给定 $J$，我们有

$$
\begin{gather}
\psi_{I}(u_{j_{1}},\dots,u_{j_{k}})=\sum_{\sigma} \mathrm{sgn}(\sigma) \phi_{I}(u_{j_{\sigma(1)}},\dots,u_{j_{\sigma(k)}})
\end{gather}
$$

上式右侧的求和中最多只有一项不为零，即满足 $I=(j_{\sigma(1)},\dots,j_{\sigma(k)})$ 的一项。然而，由于 $I,J$ 都是升序的，故唯一的可能就是 $I=J$ 并且 $\sigma=\mathrm{id}$，此时 $\psi_{I}=1$，其余情况下 $\psi_{I}=0$.

现在我们证明 $\psi_{I}$ 构成 $\mathcal{A}^{k}(V)$ 的基。设 $f$ 是一个交错 $k$-张量，我们证明 $f$ 可以唯一地写成 $\psi_{I}$ 的线性组合。

任取升序 $k$-元组 $I$，定义

$$
\begin{gather}
d_{I}=f(u_{i_{1}},\dots,u_{i_{k}})
\end{gather}
$$

并取

$$
\begin{gather}
g=\sum_{[J]} d_{J} \psi_{J}
\end{gather}
$$

其中 $[J]$ 表示 $J$ 遍历所有 $[n]$ 上的升序 $k$-元组。如果 $I$ 是一个升序 $k$-元组，那么 $g$ 在 $(u_{i_{1}},\dots,u_{i_{k}})$ 上的值为 $d_{I}=f(u_{i_{1}},\dots,u_{i_{k}})$，从而根据引理有 $f=g$. 唯一性部分的证明与 2.1.4 相同，这样就完成了证明。

上述定理表明，只要取定了 $V$ 上的基 $u_{1},\dots,u_{n}$，那么任意一个交错 $k$-张量 $f$ 都可以写成

$$
\begin{gather}
f=\sum_{[J]} d_{J} \psi_{J}
\end{gather}
$$

的形式，即 $f$ 完全由其在基向量升序 $k$-元组上的取值决定。

向量空间 $\mathcal{A}^{k}(V)$ 的维数是多少？如果 $k=1$，那么 $\mathcal{A}^{1}(V)=T^{1}(V)$ 的维数是 $n$，这是已知的结论。一般来说，给定 $k>1$ 以及 $[n]$ 的有 $k$ 个元素的子集 $\{ i_{1},\dots,i_{k} \}$，有且仅有一个对应的升序 $k$-元组，从而仅有一个相应的基本交错张量。因此，$\mathcal{A}^{k}(V)$ 的维数就等于 $[n]$ 的 $k$ 元素子集的数量，这一数字我们称之为**二项式系数**

$$
\begin{gather}
\binom{ n }{ k } =\dfrac{n!}{k!(n-k)!}
\end{gather}
$$

下面，我们来考虑交错张量与线性映射之间的相互作用，我们有如下定理：

**定理 2.2.10**

设 $T\colon V\to W$ 是线性映射，如果 $f$ 是 $W$ 上的交错 $k$-张量，那么 $T^{*}f$ 就是 $V$ 上的交错张量。

**证明**

根据定义验证即可。任取 $1\leq i<k$，我们有

$$
\begin{align}
T^{*}f(v_{1},\dots,v_{i},v_{i+1},\dots,v_{k})&= f(Tv_{1},\dots,Tv_{i},Tv_{i+1},\dots,Tv_{k}) \\
&= -f(Tv_{1},\dots,Tv_{i+1},Tv_{i},\dots,Tv_{k}) \\
&= -T^{*}f(v_{1},\dots,v_{i+1},v_{i},\dots,v_{k})
\end{align}
$$

即证。

最后，我们来讨论交错张量与行列式之间的联系。一言以蔽之：行列式就是一个基本 $n$ 阶交错张量。

**定义 2.2.11** 行列式（determinant）

设 $e_{1},\dots,e_{n}$ 是 $\mathbb{R}^{n}$ 上的标准基，$\phi_{1},\dots,\phi_{n}$ 为对应的 $T^{1}(\mathbb{R}^{n})$ 上的对偶基。向量空间 $\mathcal{A}^{n}(\mathbb{R}^{n})$ 的维数为 $1$，从而 $\psi_{1,\dots,n}$ 为其上唯一的基本交错张量。如果 $X=[x_{1},\dots,x_{n}]$ 是一个 $n\times n$ 矩阵，我们定义 $X$ 的**行列式**为

$$
\begin{gather}
\det X=\psi_{1,\dots,n}(x_{1},\dots,x_{n})
\end{gather}
$$

我们来证明上述定义满足行列式的公理：多重线性和交错性根据定义即得，此外，设 $I_{n}$ 为 $n$ 阶单位矩阵，则有

$$
\begin{gather}
\det I_{n}=\psi_{1,\dots,n}(e_{1},\dots,e_{n})=\sum_{\sigma} \mathrm{sgn}(\sigma) (\phi_{1,\dots,n})^{\sigma}(e_{1},\dots,e_{n})
\end{gather}
$$

右侧的求和中，仅有 $\sigma=\mathrm{id}$ 这一项不为零，因此我们有 $\det I_{n}=1$，这样就满足了归一性。因此，$\psi_{1,\dots,n}$ 满足了行列式的公理，就如我们所声明的那样。

从上述定义中，我们也可以立即得到行列式的一个计算公式：

$$
\begin{align}
\det X &= \sum_{\sigma} \mathrm{sgn}(\sigma) \phi_{I}(x_{\sigma(1)},\dots,x_{\sigma(n)}) \\
&=\sum_{\sigma} \mathrm{sgn}(\sigma) x_{1,\sigma(1)}\cdots x_{n,\sigma(n)}
\end{align}
$$

上述公式有时也直接作为行列式的定义。

对于 $k<n$ 时的交错张量 $\psi_{I}$，它们也有一个用行列式表达的计算公式，如下所示：

**定理 2.2.12**

任取升序 $k$-元组 $I$，设 $\psi_{I}$ 是 $\mathbb{R}^{n}$ 上对应于标准基的基本交错张量。给定 $x_{1},\dots,x_{k}\in \mathbb{R}^{n}$，令矩阵 $X=[x_{1},\dots,x_{k}]$，则有

$$
\begin{gather}
\psi_{I}(x_{1},\dots,x_{k})=\det X_{I}
\end{gather}
$$

其中 $X_{I}$ 表示 $X$ 的 $i_{1},\dots,i_{k}$ 行构成的子矩阵。

**证明**

我们有

$$
\begin{align}
\psi_{I}(x_{1},\dots,x_{k})&= \sum_{\sigma} \mathrm{sgn}(\sigma) \phi_{I}(x_{\sigma(1)},\dots,x_{\sigma(k)}) \\
&= \sum_{\sigma}\mathrm{sgn}(\sigma) x_{i_{1},\sigma(1)}\cdots x_{i_{k},\sigma(k)}
\end{align}
$$

这正是 $\det X_{I}$ 的计算公式。

# Section 3: 楔积

与一般的张量相同，对于两个交错张量，我们想要为其定义一种乘积运算。然而，即使 $f,g$ 是交错的，$f\otimes g$ 几乎从不交错，因此我们需要一种别的运算。这种运算的实际定义并不是很重要，真正重要的是它满足的性质，就像我们对行列式的公理化定义一样。

**定理 2.3.1**

设 $V$ 是向量空间，存在一个运算 $\land$，其将每个 $f\in \mathcal{A}^{k}(V)$ 与 $g\in \mathcal{A}^{\ell}(V)$ 映射到 $f\land g\in \mathcal{A}^{k+\ell}(V)$，并且满足以下性质：

1. 结合性：$f\land(g\land h)=(f\land g)\land h$
2. 齐次性：$(cf)\land g=c(f\land g)=f\land(cg)$
3. 分配性：如果 $f,g$ 的阶数相同，则有 $$
\begin{gather}
(f+g)\land h=f\land h+g\land h \\
h\land (f+g)=h\land f+h\land g
\end{gather}
$$
4. 反对称性：如果 $f,g$ 的阶数分别为 $k,\ell$，则 $$
g\land f=(-1)^{k\ell} f\land g
$$
5. 给定 $V$ 的基 $u_{1},\dots,u_{n}$，令 $\phi_{i}$ 表示 $V^{*}$ 上的对偶基，$\psi_{I}$ 为其对应的基本交错张量。如果 $I=(i_{1},\dots,i_{k})$ 是 $[n]$ 上的升序 $k$-元组，那么 $$
\psi_{I}=\phi_{i_{1}}\land \dots \land \phi_{i_{k}}
$$

在有限维空间 $V$ 上，上述五个性质唯一地确定了 $\land$. 此外，它还有以下性质：

6. 如果 $T\colon V\to W$ 是线性映射，$f,g$ 是 $W$ 上的交错张量，那么 $$
T^{*}(f\land g)=T^{*}f\land T^{*}g
$$

张量 $f\land g$ 称为张量 $f$ 和 $g$ 的**楔积**（wedge product）。注意到，根据性质 4，一个奇数阶的交错张量满足 $f\land f=0$.

**证明**

(1). 设 $F$ 是 $V$ 上的 $k$-张量，我们定义映射 $A\colon T^{k}(V)\to T^{k}(V)$ 如下：

$$
\begin{gather}
AF=\sum_{\sigma \in S_{k}} \mathrm{sgn}(\sigma) F^{\sigma}
\end{gather}
$$

于是我们有 $\psi_{I}=A\phi_{I}$. 此外，映射 $A$ 还满足以下性质：

i. $A$ 是线性的；
ii. $AF$ 是一个交错张量；
iii. 如果 $F$ 是交错张量，那么 $AF=k! F$

我们来验证这些性质。由于映射 $F\mapsto F^{\sigma}$ 是线性的，因此 $A$ 是线性的。$AF$ 的交错性由如下计算给出：

$$
\begin{align}
(AF)^{\tau} &= \sum_{\sigma} \mathrm{sgn}(\sigma)(F^{\sigma})^{\tau} \\
&= \sum_{\sigma} \mathrm{sgn}(\sigma) F^{\tau \circ\sigma} \\
&= \mathrm{sgn}(\tau) \sum_{\sigma} \mathrm{sgn}(\tau \circ\sigma) F^{\tau \circ\sigma} \\
&= \mathrm{sgn}(\tau) AF
\end{align}
$$

最后，假设 $F$ 是交错的，那么 $F^{\sigma}=\mathrm{sgn}(\sigma)F$，于是有

$$
\begin{gather}
AF=\sum_{\sigma} \mathrm{sgn}(\sigma)^{2} F=k! F
\end{gather}
$$

(2). 给定 $f\in \mathcal{A}^{k}(V)$ 和 $g\in \mathcal{A}^{\ell}(V)$，我们定义

$$
\begin{gather}
f\land g=\dfrac{1}{k!\ell!} A(f\otimes g)
\end{gather}
$$

则 $f\land g$ 是一个 $k+\ell$ 阶的交错张量。

(3). 下面我们来验证 $\land$ 的性质。结合性是最为困难的，我们把它留到最后。对于齐次性，我们有

$$
\begin{align}
(cf)\land g &= \dfrac{1}{k!\ell!} A((cf)\otimes g) \\
&= \dfrac{1}{k!\ell!} A(c(f\otimes g)) \\
&= \dfrac{1}{k!\ell!} c A(f\otimes g) \\
&= c (f\land g)
\end{align}
$$

对 $f\land(cg)$ 也有类似的结果。根据 $\otimes$ 的分配性与 $A$ 的线性同样可证分配性。

(4). 我们验证反对称性。我们来证明，如果 $F,G$ 分别是 $k$ 阶和 $\ell$ 阶的张量，那么

$$
\begin{gather}
A(F\otimes G)=(-1)^{k\ell} A(G\otimes F)
\end{gather}
$$

设 $\pi$ 为 $[k+\ell]$ 上的置换，使得

$$
\begin{gather}
(\pi(1),\dots,\pi(k+\ell))=(k+1,\dots,k+\ell,1,\dots,k)
\end{gather}
$$

则 $\mathrm{sgn}(\pi)=(-1)^{k\ell}$. 又由于

$$
\begin{align}
(G\otimes F)^{\pi}(v_{1},\dots,v_{k+\ell}) &= G(v_{k+1},\dots,v_{k+\ell}) F(v_{1},\dots,v_{k}) \\
&= (F\otimes G)(v_{1},\dots,v_{k+\ell})
\end{align}
$$

因此有

$$
\begin{align}
A(F\otimes G) &= \sum_{\sigma} \mathrm{sgn}(\sigma) (F\otimes G)^{\sigma} \\
&= \sum_{\sigma} \mathrm{sgn}(\sigma) (G\otimes F)^{\sigma \circ \pi} \\
&= \mathrm{sgn}(\pi) \sum_{\sigma} \mathrm{sgn}(\sigma \circ \pi) (G\otimes F)^{\sigma \circ \pi} \\
&= (-1)^{k\ell} A(G\otimes F)
\end{align}
$$

(5). 现在我们来验证结合性，这需要几个步骤。首先我们证明：如果 $F$ 和 $G$ 分别是 $k$ 阶与 $\ell$ 阶的张量，且 $AF=0$，那么 $A(F\otimes G)=0$.

考虑 $A(F\otimes G)$ 中的一项

$$
\begin{gather}
\mathrm{sgn}(\sigma) F(v_{\sigma(1)},\dots,v_{\sigma(k)}) G(v_{\sigma(k+1)},\dots,v_{\sigma(k+\ell)})
\end{gather}
$$

我们将含有因子 $G(v_{\sigma(k+1)},\dots,v_{\sigma(k+\ell)})$ 的项合并在一起，得到

$$
\begin{gather}
\mathrm{sgn}(\sigma) \left[ \sum_{\tau} \mathrm{sgn}(\tau) F(v_{\sigma(\tau(1))},\dots,v_{\sigma(\tau(k))}) \right] G(v_{\sigma(k+1)},\dots,v_{\sigma(k+\ell)})
\end{gather}
$$

而括号内的项正是 $AF(v_{\sigma(1)},\dots,v_{\sigma(k)})=0$，因此这些项合并后得到零。同理，含有其他 $G$ 因子的项合并后也得到零，因此 $A(F\otimes G)=0$.

(6). 设 $F$ 是任意张量，$h$ 是交错 $m$-张量，我们证明

$$
\begin{gather}
(AF)\land h=\dfrac{1}{m!} A(F\otimes h)
\end{gather}
$$

设 $F$ 的阶数为 $k$，则我们要证的等式可以写成

$$
\begin{gather}
\dfrac{1}{k!m!} A((AF)\otimes h)=\dfrac{1}{m!} A(F\otimes h)
\end{gather}
$$

$A$ 的线性与 $\otimes$ 的分配性表明上式可以写成

$$
\begin{gather}
A((AF)\otimes h-k!F\otimes h)=A((AF-k!F)\otimes h)=0
\end{gather}
$$

根据步骤 (5)，我们只需证明 $A(AF-k!F)=0$，这可以根据 $A$ 的性质 iii 立即得到，因为 $AF$ 是一个交错 $k$-张量。

(7). 设 $f,g,h$ 分别是 $k,\ell,m$ 阶张量，我们证明

$$
\begin{gather}
(f\land g)\land h=\dfrac{1}{k!\ell!m!} A((f\otimes g)\otimes h)
\end{gather}
$$

令 $F=f\otimes g$，我们有

$$
\begin{align}
(f\land g)\land h &= \dfrac{1}{k!\ell!} (AF) \land h \\
&= \dfrac{1}{k!\ell!m!} A(F\otimes h) \\
&= \dfrac{1}{k!\ell!m!} A((f\otimes g)\otimes h)
\end{align}
$$

(8). 现在，我们可以来验证结合性了。设 $f,g,h$ 与步骤 (7) 中相同，则有

$$
\begin{align}
k!\ell!m! (f\land g)\land h &= A((f\otimes g)\otimes h) \\
&= A(f\otimes (g\otimes h)) \\
&= (-1)^{k(\ell+m)} A((g\otimes h)\otimes f) \\
&= (-1)^{k(\ell+m)} k!\ell!m! (g\land h)\land f \\
&= k!\ell!m! f\land (g\land h)
\end{align}
$$

(9). 我们验证性质 5. 我们来证明：对任意 $1$-张量 $f_{1},\dots,f_{k}$，成立

$$
\begin{gather}
A(f_{1}\otimes \dots \otimes f_{k})=f_{1}\land\dots \land f_{k}
\end{gather}
$$

当 $k=1$ 时，上式是平凡的。假设上式对 $k-1$ 成立，令 $F=f_{1}\otimes\dots \otimes f_{k-1}$，则有

$$
\begin{align}
A(F\otimes f_{k}) &= 1! (AF)\land f_{k} \\
&= (f_{1}\land\dots \land f_{k-1}) \land f_{k}
\end{align}
$$

根据归纳法即证。现在性质 5 就是上式的一个推论：对任意 $I$ 有

$$
\begin{gather}
\psi_{I}=A\phi_{I}=A(\phi_{i_{1}}\otimes \dots \otimes \phi_{i_{k}})=\phi_{i_{1}}\land\dots \land \phi_{i_{k}}
\end{gather}
$$

(10). 我们来验证唯一性。在有限维空间 $V$ 上，我们通过只应用性质 1-5 得到 $\land$ 的一个计算公式以证明这一点。

令 $\phi_{I}$ 和 $\psi_{I}$ 如性质 5 中所示。给定交错张量 $f,g$，我们将其唯一地写成基本交错张量的线性组合：

$$
\begin{gather}
f=\sum_{[I]} b_{I} \psi_{I} ,\quad g=\sum_{[J]} c_{J} \psi_{J}
\end{gather}
$$

其中 $I$ 是升序 $k$-元组，$J$ 是升序 $\ell$-元组。根据分配性和齐次性我们有

$$
\begin{gather}
f\land g=\sum_{[I]} \sum_{[J]} b_{I} c_{J} \psi_{I}\land \psi_{J}
\end{gather}
$$

因此，要计算 $f\land g$，我们只需计算基本交错张量的楔积

$$
\begin{gather}
\psi_{I}\land \psi_{J}=(\phi_{i_{1}}\land\dots \land \phi_{i_{k}})\land (\phi_{j_{1}}\land\dots \land \phi_{j_{\ell}})
\end{gather}
$$

为此，我们使用结合性以及反对称性

$$
\begin{gather}
\phi_{i}\land \phi_{j}=-\phi_{j}\land \phi_{i}, \quad \phi_{i}\land \phi_{i}=0
\end{gather}
$$

这表明，$\psi_{I}\land \psi_{J}=0$ 如果有两个指标相同；否则它就等于 $\mathrm{sgn}(\pi)$ 乘以基本交错 $k+\ell$ 张量 $\psi_{K}$，使得 $K$ 为通过将 $k+\ell$ 元组 $(I,J)$ 排列为升序得到的升序 $k+\ell$ 元组，且 $\pi$ 就是完成这一排列的置换。

(11). 最后，我们来验证性质 6. 设 $T\colon V\to W$ 是线性映射，$F$ 是 $W$ 上的 $k$-张量，则我们有

$$
\begin{align}
T^{*}(F^{\sigma})(v_{1},\dots,v_{k}) &= F^{\sigma}(Tv_{1},\dots,Tv_{k}) \\
&= F(Tv_{\sigma(1)},\dots,Tv_{\sigma(k)}) \\
&= (T^{*} F)^{\sigma} (v_{1},\dots,v_{k})
\end{align}
$$

又由于 $A$ 是线性的，故 $T^{*}(AF)=A(T^{*}F)$，从而

$$
\begin{align}
T^{*}(f\land g) &= \dfrac{1}{k!\ell!} T^{*}(A(f\otimes g)) \\
&= \dfrac{1}{k!\ell!} A(T^{*}(f\otimes g)) \\
&= \dfrac{1}{k!\ell!} A(T^{*}f\otimes T^{*}g) \\
&= T^{*}f \land T^{*}g
\end{align}
$$

这就完成了证明。

有了这个定理，我们就完成了全部所需的多重线性代数知识。事实上，在后续的章节中，我们只会用到交错张量与楔积相关的知识。