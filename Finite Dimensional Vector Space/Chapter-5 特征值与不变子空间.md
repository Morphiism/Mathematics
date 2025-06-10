[[Chapter-1 矩阵是什么]] [[Chapter-2 子空间与方程组的解]] [[Chapter-3 对偶与矩阵的行]] [[Chapter-4 行列式（上）]]

前面几章我们研究了从一个向量空间到另一个向量空间的映射，本章我们将研究从向量空间到它自身的映射（称为**算子**）。对于算子的研究构成了线性代数最重要的一部分。在本章中，我们将介绍**特征值**与**特征向量**，这会成为我们研究算子的重要工具。

# Section 1: 向量空间的直和分解

对于一个向量空间 $V$，我们有时希望能够将其分成几个小的部分分别进行研究，一种常用的方法是通过**直和**。在介绍直和之前，我们先介绍向量空间的**和**。

**定义5.1.1** 和（Sum），直和（Direct Sum）

设 $U_1,\dots,U_m$ 是 $V$ 的子空间，它们的**和**定义为

$$
U_1+\dots+U_m=\{u_1+\dots+u_m\colon u_j\in U_j\}
$$

此外，如果 $u_1+\dots+u_m=0$ 当且仅当 $u_1=\dots=u_m=0$，则称该和是**直和**，记作

$$
U_1\oplus\dots\oplus U_m
$$

读者可能会发现，直和的条件与向量组线性无关的条件有相似之处。实际上，在有限维空间内，任意一组线性无关的向量 $v_1,\dots,v_m$ 都诱导了一个直和：$\mathrm{span}(v_1)\oplus\dots\oplus\mathrm{span}(v_m)$，因此，一个 $n$ 维的向量空间有直和分解：

$$
V=U_1\oplus\dots\oplus U_n
$$

其中每个 $U_j$ 都是一维的。

下面我们给出判断一个和是直和的充要条件：

**定理 5.1.2**

设 $U_1,\dots,U_m$ 是 $V$ 的子空间，则 $U_1+\dots+U_m$ 是直和当且仅当

$$
\dim (U_1+\dots+U_m)=\dim U_1+\dots+\dim U_m
$$

为证明上面的定理，我们引入下面的定义：

**定义 5.1.3** 积（Product）

设 $U_1,\dots,U_m$ 是向量空间，则它们的**积**定义为

$$
U_1\times \dots\times U_m=\{(u_1,\dots,u_m)\colon u_j\in U_j\}
$$

在其上可以定义加法和数乘：

$$
\begin{gather*}
(u_1,\dots,u_m)+(v_1,\dots,v_m)=(u_1+v_1,\dots,u_m+v_m)\\
\lambda(u_1,\dots,u_m)=(\lambda u_1,\dots,\lambda u_m)
\end{gather*}
$$

于是我们可以验证 $U_1\times \dots\times U_m$ 是一个向量空间，并且如果各 $U_j$ 是有限维的，那么有

$$
\dim(U_1\times \dots\times U_m)=\dim U_1+\dots+\dim U_m
$$

现在我们给出5.1.2的证明：

**证明**

定义 $\Gamma\colon U_1\times\dots\times U_m\to U_1+\dots+U_m$ 为

$$
\Gamma(u_1,\dots,u_m)=u_1+\dots+u_m
$$

显然 $\Gamma$ 是满射。则 $U_1+\dots+U_m$ 是直和当且仅当 $\Gamma$ 是单射，当且仅当 $\Gamma$ 是双射，当且仅当 $\dim(U_1\times\dots\times U_m)=\dim(U_1+\dots+U_m)$，当且仅当

$$
\dim (U_1+\dots+U_m)=\dim U_1+\dots+\dim U_m
$$

# Section 2: 一维不变子空间

如果向量空间 $V$ 有直和分解 $V=U_1\oplus\dots\oplus U_m$，那么对于 $V$ 上的算子 $T$ 的研究，我们可以将其限制在各个子空间上进行，即研究 $T|_{U_j}$ 的性质。但是这里有一个问题：$T|_{U_j}$ 的值域不一定是 $U_j$，即 $T|_{U_j}$ 不一定是 $U_j$ 上的算子。因此我们将只研究那些在 $T$ 的作用下不变的子空间，具体来说就是：

**定义 5.2.1** 不变子空间（Invariant Subspace）

设 $U$ 是 $V$ 的子空间，称 $U$ 在 $T$ 下**不变**，如果有 $T(U)\subset U$。

现在我们提出**不变子空间问题**：向量空间 $V$ 上的算子是否一定有不同于 $\{0\}$ 和 $V$ 的不变子空间？对于有限维向量空间，我们在之后会看到，这个问题的回答是肯定的。

接下来，我们从最简单的非平凡不变子空间开始研究：一维不变子空间。

设 $U=\mathrm{span}(v)$，若 $U$ 在 $T$ 下是不变的，则有

$$
Tv=\lambda v
$$

上面的方程启发我们给出如下定义：

**定义 5.2.2** 特征值（Eigenvalue），特征向量（Eigenvector）

设 $T\in \mathcal L(V)$，若存在 $v\in V,v\ne 0$ 使得 $Tv=\lambda v$，则称 $\lambda$ 是 $T$ 的一个**特征值**，$v$ 是对应于 $\lambda$ 的一个**特征向量**。

根据定义以及有限维向量空间上算子的性质（详见第二章），我们立即得到下面的定理：

**定理 5.2.3**

设 $V$ 是有限维的，$T\in \mathcal L(V),\lambda\in\mathbb F$，则有以下命题等价：

1. $\lambda$ 是 $T$ 的特征值
2. $T-\lambda I$ 不是单射
3. $T-\lambda I$ 不是满射
4. $T-\lambda I$ 不可逆

下面我们来证明，对应于不同特征值的特征向量是线性无关的。

**定理 5.2.4**

设 $T\in \mathcal L(V), \lambda_1,\dots,\lambda_m$ 是 $T$ 的各不相同的特征值，$v_1,\dots,v_m$ 是对应的特征向量，则 $v_1,\dots,v_m$ 是线性无关的。

**证明**

我们使用反证法。假设 $v_1,\dots,v_m$ 是线性相关的，设 $j$ 是使得 $v_j$ 是包含在前面各向量的张成空间内的最小整数，则有

$$
a_1v_1+\dots+a_{j-1}v_{j-1}-v_j=0
$$

其中 $a_1,\dots,a_{j-1}$ 不全为零。将 $T$ 作用在等式两边，则有

$$
a_1\lambda_1 v_1+\dots+a_{j-1}\lambda_{j-1}v_{j-1}-\lambda_j v_j=0
$$

将 $v_j$ 代入即得

$$
a_1 (\lambda_1-\lambda_j)v_1+\dots+a_{j-1}(\lambda_{j-1}-\lambda_j)v_{j-1}=0
$$

由 $j$ 的最小性，知 $v_1,\dots,v_{j-1}$ 线性无关，从而所有的 $a$ 均为零，产生矛盾。

之后我们讲到对角化时会看到，如果一个算子有足够多的特征值，那么它就可以对角化，这一结论的证明就依赖于上面的定理。

同时我们也能得到一个推论：

**定理 5.2.5**

设 $V$ 是有限维的，则 $T\in\mathcal L(V)$ 最多有 $\dim V$ 个各不相同的特征值。

算子不同于一般线性映射的原因是算子能够自乘，具体来说，我们定义 $T^m(v)=T(T^{m-1}(v))$，并且我们定义 $T^0=I$ 为恒等算子。此外，如果还有 $T$ 可逆，则定义 $T^{-m}=(T^{-1})^m$，从而我们有

$$
T^m T^n=T^{m+n},(T^m)^n=T^{mn}
$$

于是我们可以定义算子的多项式，多项式在算子的研究中是一个非常重要的工具，关于多项式的知识我们将做简要介绍。

**定义 5.2.6** 算子的多项式

记 $\mathbb F[z]$ 为 $\mathbb F$ 上的多项式构成的集合，设 $p\in \mathbb F[z], p(z)=a_0+a_1z+\dots+a_mz^m,T\in\mathcal L(V)$，则定义 

$$
p(T)=a_0I+a_1 T+\dots+a_m T^m
$$

由多项式的乘积，我们可以证明 $p(T)q(T)=(pq)(T)=q(T)p(T)$，即算子的多项式是交换的。

下面我们给出关于多项式的两个主要定理，它们的证明我们将省略。

**定理 5.2.7** 多项式的带余除法

给定 $p,s\in \mathbb F[z],s\ne 0$，则存在唯一的多项式 $q,r$ 使得

$$
p=sq+r
$$

且 $\deg r < \deg s$。

**定理 5.2.8** 代数基本定理

非常数的复系数多项式在复数域上有零点。

由上面两个定理我们可以证明：每个 $p\in \mathbb C[z],p=a_0+a_1z+\dots+a_mz^m$ 都可以分解为各个零点所对应的一次因式的积：

$$
p(z)=c(z-\lambda_1)\dots(z-\lambda_m)
$$

其中 $c\ne 0,\lambda_1,\dots,\lambda_m$ 是 $p$ 的全部 $m$ 个零点（包含重根）。

下面我们来证明复向量空间上算子的一个中心结果。

**定理 5.2.9**

有限维非零复向量空间上的算子有特征值。

**证明**

设 $\dim V=n>0$，取 $T\in\mathcal L(V),v\in V,v\ne 0$，记次数不超过 $n$ 的多项式构成的集合为 $\mathcal P_n(\mathbb F)$，我们定义映射 $\Phi\colon \mathcal P_n(\mathbb C)\to V$ 为 

$$
\Phi(p)=p(T)(v)
$$

因为 $\dim \mathcal P_n(\mathbb C)=n+1$（因为 $1,z,\dots,z^n$ 构成了 $\mathcal P_n(\mathbb C)$ 的一个基），故 $\Phi$ 不是单射。

从而存在 $p\ne 0, \Phi(p)=p(T)(v)=0$。设 $p=a_0+a_1z+\dots+a_mz^m=c(z-\lambda_1)\dots(z-\lambda_m)$，则有

$$
p(T)(v)=c(T-\lambda_1 I)\dots(T-\lambda_m I)v=0
$$

由于 $v\ne 0$，于是存在一个 $j$，使得 $T-\lambda_j I$ 不是单射，即 $\lambda_j$ 是 $T$ 的特征值。

# Section 3: 上三角化与对角化

下面我们考虑算子关于某个基的矩阵，我们希望该矩阵有足够多的零，从而我们处理起来更加方便，在这一章中，我们主要关注上三角矩阵和对角矩阵。下面的定理建立了上三角矩阵与不变子空间的联系：

**定理 5.3.1**

设 $T\in \mathcal L(V)$，且 $v_1,\dots,v_n$ 是 $V$ 的一个基，则以下命题等价：

1. $\mathcal M(T,(v_1,\dots,v_n))$ 是上三角的
2. 对于每个 $j$，有 $Tv_j\in \mathrm{span}(v_1,\dots,v_{j})$
3. 对于每个 $j$，$\mathrm{span}(v_1,\dots,v_{j})$ 在 $T$ 下不变

**证明**

由矩阵的定义（详见第一章），我们立即得到1和2的等价性。假设2成立，固定 $j$，则对于 $1\le i\le j$，都有 $Tv_i\in \mathrm{span}(v_1,\dots,v_j)$，于是 $\mathrm{span}(v_1,\dots,v_j)$ 在 $T$ 下不变。则有 $2\Longrightarrow 3$。

现假设3成立，则有 $T(\mathrm{span}(v_1,\dots,v_j))\subset \mathrm{span}(v_1,\dots,v_j)$，则有 $Tv_j\in \mathrm{span}(v_1,\dots,v_j)$，于是有 $3\Longrightarrow 2$。

上三角矩阵有很多良好的性质，比如，我们可以直接从矩阵中得出其是否可逆：

**定理 5.3.2**

若 $T\in\mathcal L(V)$ 关于某个基 $v_1,\dots,v_n$ 的矩阵是上三角的，那么 $T$ 可逆当且仅当矩阵的对角线上的元素都不为零。

**证明**

$$
\begin{bmatrix}
\lambda_1  &  &  &  &  *\\
  & \ddots  &   &  & \\
  &  & \lambda_j &  & \\
  &  &  & \ddots  &\\
0  &  &  &  & \lambda_n
\end{bmatrix}
$$

设矩阵对角线上的元素为 $\lambda_1,\dots,\lambda_n$，假设 $T$ 可逆，则 $\lambda_1\ne 0$，因为 $Tv_1=\lambda_1 v_1$，而 $\ker T=\{0\}$。现假设 $\lambda_j=0$，则 

$$
T(\mathrm{span}(v_1,\dots,v_j))\subset \mathrm{span}(v_1,\dots,v_{j-1})
$$

从而 $T$ 限制在 $\mathrm{span}(v_1,\dots,v_j)$ 上的映射不是单射，即存在 $v\ne 0$ 使得 $Tv=0$，这表明 $T$ 不可逆，产生矛盾。

现在我们假设对角线上的元素不为零，于是有 $v_1=T(v_1/\lambda_1)\in T(V)$。现假设 $v_1,\dots,v_{j-1}\in T(V)$，则

$$
T(v_j/\lambda_j)=b_1v_1+\dots+b_{j-1}v_{j-1}+v_j
$$

于是 $v_j\in T(V)$。由数学归纳法，对于所有 $j$，都有 $v_j\in T(V)$。又 $v_1,\dots,v_n$ 是基，这表明 $T(V)=V$，即 $T$ 是满射，于是 $T$ 可逆。

这个定理有一个推论，它告诉我们上三角矩阵的对角线元素就是特征值。

**定理 5.3.3**

若 $T\in\mathcal L(V)$ 关于某个基 $v_1,\dots,v_n$ 的矩阵是上三角的，那么 $T$ 的特征值为矩阵对角线上的元素。

**证明**

设 $\lambda\in \mathbb F$，则 $T-\lambda I$ 的矩阵为

$$
\begin{bmatrix}
\lambda_1-\lambda  &  &  &  &  *\\
  & \ddots  &   &  & \\
  &  & \lambda_j-\lambda &  & \\
  &  &  & \ddots  &\\
0  &  &  &  & \lambda_n-\lambda
\end{bmatrix}
$$

则 $\lambda$ 是 $T$ 的特征值当且仅当 $T-\lambda I$ 不可逆，当且仅当 $\lambda$ 等于某个 $\lambda_j$。

对于一个算子，是否一定存在一个基使它的矩阵是上三角的？对于有限维的复向量空间，我们可以回答“是”。然而，对于实向量空间则不然，因此，复向量空间上的算子在很多性质上都优于实向量空间上的算子。这一差别来源于代数基本定理，而代数基本定理作为一个分析的命题（所有代数基本定理的证明都涉及复分析），也反映了复变函数在很多性质上都优于实变函数。

**定理 5.3.4**

有限维非零复向量空间上的算子可上三角化。

**证明一**

我们使用归纳法。对于 $\dim V=1$，定理显然成立。

假设定理对于维数小于 $n$ 的空间成立，设 $\dim V=n,T\in \mathcal L(V)$，我们的思路是将 $T$ 限制在一个更小的空间上，从而可以使用归纳假设，一种简单的方法是使用商算子：$(T/U)(v+U)=Tv+U$，可以将 $T$ 限制在商空间 $V/U$ 上。

由于 $V$ 有特征值（定理 5.2.9），任取一个特征向量 $v_1$，令 $U=\mathrm{span}(v_1)$，则 $U$ 在 $T$ 下不变，且 $\dim V/U=n-1$（取商映射 $\pi(v)=v+U$ 应用线性映射基本定理即得）。于是 $T/U$ 作为 $\mathcal L(V/U)$ 上的算子可上三角化，设使用的基为 $v_2+U,\dots,v_n+U$，则对任意 $j$ 有

$$
(T/U)(v_j+U)=Tv_j +U\in \mathrm{span}(v_2+U,\dots,v_j+U)
$$

这表明 $Tv_j\in \mathrm{span}(v_1,\dots,v_j)$，于是 $T$ 在基 $v_1,\dots,v_n$ 下的矩阵是上三角的。

**证明二**

另一种方法与证明一的思路相同，都需要将 $T$ 限制在更小的空间上然后使用归纳法。不过在这里，我们将直接使用限制算子：$T|_U(u)=Tu$。读者可以仿照证明一自行完成证明。（注：只需取 $U=\mathrm{im}(T-\lambda I)$ 即可，其中 $\lambda$ 是 $T$ 的特征值）

在下一章，我们将给出一个比上述定理更强的结论（即Jordan形）。

接下来我们考虑比上三角矩阵性质更好的对角矩阵。显然，如果 $T$ 关于某个基 $v_1,\dots,v_n$ 有对角矩阵，那么每个 $v_j$ 都是 $T$ 的特征向量，于是我们提出以下定义：

**定义 5.3.5** 特征空间（Eigenspace）

设 $T\in\mathcal L(V), \lambda$ 是 $T$ 的特征值，则对应于 $\lambda$ 的**特征空间**定义为

$$
E_\lambda(T)=\{v\colon Tv=\lambda v\}
$$

根据定义，我们立即得到 $E_\lambda(T)=\ker(T-\lambda I)$，从而 $\lambda$ 是 $T$ 的特征值当且仅当 $E_\lambda(T)\ne \{0\}$。

接下来我们考虑特征空间的和，我们有以下定理：

**定理 5.3.6**

设 $V$ 是有限维的，$T\in\mathcal L(V),\lambda_1,\dots,\lambda_m$ 是 $T$ 的不同特征值，则

$$
E_{\lambda_1}+\dots+E_{\lambda_m}
$$

是直和，且

$$
\dim E_{\lambda_1}+\dots+\dim E_{\lambda_m}\le \dim V
$$

**证明**

从每个特征空间 $E_{\lambda_j}$ 中取 $u_j$，则 $u_j$ 是 $T$ 的特征向量。设 

$$
u_1+\dots+u_m=0
$$

由于对应于不同特征值的特征向量是线性无关的，因此每个 $u_j$ 都为零，即特征空间的和是直和。于是我们有

$$
\dim E_{\lambda_1}+\dots+\dim E_{\lambda_m}=\dim (E_{\lambda_1}\oplus\dots\oplus E_{\lambda_m})\le \dim V
$$

我们知道，如果 $T$ 可对角化，那么 $\dim E_{\lambda_1}+\dots+\dim E_{\lambda_m}=\dim V$，下面我们证明这个条件是充要的。

**定理 5.3.7**

设 $V$ 是有限维的，$T\in\mathcal L(V),\lambda_1,\dots,\lambda_m$ 是 $T$ 的不同特征值，则下面的命题等价：

1. $T$ 可对角化
2. $V$ 有 $T$ 的特征向量构成的基
3. 存在 $T$ 下不变的一维子空间 $U_1,\dots,U_n$ 使得 $V=U_1\oplus\dots\oplus U_n$
4. $V=E_{\lambda_1}\oplus\dots\oplus E_{\lambda_m}$
5. $\dim V=\dim E_{\lambda_1}+\dots+\dim E_{\lambda_m}$

**证明**

显然1和2等价，要看出2和3的等价性，只需注意到每个 $u_j\in U_j,u_j\ne 0$ 都是 $T$ 的特征向量，于是我们有1, 2, 3等价。显然我们也有4和5等价，于是我们只要证明 $4\Longleftrightarrow 2$。

设 $V$ 有特征向量构成的基，则每个 $v\in V$ 都在 $E_{\lambda_1}+\dots+E_{\lambda_m}$ 中，又特征空间是直和，于是我们证明了4。

现假设我们有 $\dim V=\dim E_{\lambda_1}+\dots+\dim E_{\lambda_m}$，从每个特征空间中取一个基组成 $V$ 的基 $v_1,\dots,v_n$，则每个 $v_j$ 都是特征向量，设

$$
a_1v_1+\dots+a_nv_n=0
$$

将各个 $v_j$ 按特征空间组合，得到 $u_1+\dots+u_m=0,u_j=\sum a_iv_i$，其中各 $v_i\in E_{\lambda_j}$。由于特征空间是直和，故各 $u_j=0$，又各 $v_i$ 是特征空间的基，故各 $a_i=0$，于是 $v_1,\dots,v_n$ 线性无关，则它为 $V$ 的一个基，从而我们证明了2。

由此我们可以得到一个推论，如果一个算子的特征值足够多，那么它就可以对角化。

**定理 5.3.8**

设 $V$ 是有限维的，$T\in\mathcal L(V)$，且 $T$ 有 $\dim V$ 个不同的特征值，则 $T$ 可对角化。

**证明**

考虑特征空间 $E_{\lambda_j},j=1,\dots,\dim V$，从中取出非零向量 $v_1,\dots,v_{\dim V}$，由于对应于不同特征值的特征向量线性无关，故各 $v_j$ 构成了 $V$ 的一个基，从而 $T$ 可对角化。

对于任意一个算子，它是否能够对角化呢？很遗憾，即使是复向量空间的算子也不一定能够对角化，但下一章我们会证明，存在一个基可以使算子的矩阵尽可能的接近对角矩阵，这是复向量空间上算子的一个核心结论。

# Section 4: 基变换

下面我们对算子的矩阵做一些研究。我们想要知道，同一算子 $T$ 在不同基下的矩阵有什么关联？我们从矩阵乘法的定义开始讲起。

设 $T\colon U\to V,S\colon V\to W, T$ 在 $(u_1,\dots,u_m),(v_1,\dots,v_n)$ 下的矩阵为 $A, S$ 在 $(v_1,\dots,v_n),(w_1,\dots,w_p)$ 下的矩阵为 $B$，于是我们定义矩阵乘法 $AB$ 为映射 $ST$ 在 $(u_1,\dots,u_m),(w_1,\dots,w_p)$ 下的矩阵。注意乘法时各个基的变化。

下面我们考虑算子 $T\colon V\to V$，我们想要了解 $A=\mathcal M(T,(v_1,\dots,v_n))$ 与 $B=\mathcal M(T,(w_1,\dots,w_n))$ 的关系（称为**相似矩阵**），我们可以这样做：之前我们构造算子的矩阵时都使用了同一个基，但我们也可以选用不同的基来构造。由于切换基对于算子 $T$ 没有影响（这就是为什么我们选用线性映射而非矩阵来研究线性代数），因此我们需要使用恒等映射 $I$，并构造矩阵如下：

$$
P=\mathcal M(I,(v_1,\dots,v_n),(w_1,\dots,w_n))
$$

于是我们有

$$
P^{-1}=\mathcal M(I,(w_1,\dots,w_n),(v_1,\dots,v_n))
$$

且

$$
B=PAP^{-1}
$$

因此我们证明了：**从一个基到另一个基的过渡矩阵是恒等映射在两个基上的矩阵**。

从而我们也修复了上一章行列式中的一个问题：线性算子在不同基上的矩阵行列式相同（$\det B=(\det P)(\det A)(\det P^{-1})=\det A$），于是我们的定义 $\det T=\det \mathcal M(T)$ 是良定的。

本章我们介绍了特征值和特征向量，我们看到，不是所有算子都可对角化，下一章我们将继续研究复向量空间上的算子，我们将证明：存在一个基使得算子的矩阵尽可能的简单。在这之后，我们将简要考察实向量空间上算子的性质。

本期内容就是这样，感谢观看！