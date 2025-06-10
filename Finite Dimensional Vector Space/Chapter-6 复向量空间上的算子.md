[[Chapter-5 特征值与不变子空间]]

上一章我们介绍了特征值与特征向量，我们证明了，在复向量空间上，每个算子都有一个基使得其矩阵是上三角的。然而，并不是每个算子都可以对角化，大多数算子因为缺乏足够的特征向量而没有一个很好的描述。因此，本章的目标之一就是寻找一个良好的基，不断地改进我们的上三角矩阵，直到不能再化简为止（即所谓的**Jordan形**）。此外，本章还会介绍与每个算子紧密关联的两个多项式：**特征多项式**与**极小多项式**，然后给出另一个可对角化的等价条件。

# Section 1: 广义特征向量与幂零算子

首先我们做一些准备工作。在上一章我们定义了算子的幂 $T^m$，现在我们来研究它的核空间与像空间。

设 $v\in\ker T^m$，那么 $T^m v=0$，从而 $T^{m+1}v=T(T^m v)=0,v\in\ker T^{m+1}$，因此 $\ker T^m\subset \ker T^{m+1}$。也就是说，随着算子自乘为幂，它的核空间在不断扩大，那么这一过程会停止吗？下面的定理给出了答案：

**定理 6.1.1**

设 $T\in\mathcal L(V)$，若存在 $m$ 使得 $\ker T^m=\ker T^{m+1}$，则对于任意正整数 $k$，有

$$
\ker T^{m+k}=\ker T^m
$$

**证明**

给定正整数 $k$，只需证明 $\ker T^{m+k}=\ker T^{m+k+1}$。因为核空间是扩大的，所以我们已经有了一个方向的包含。现设 $v\in\ker T^{m+k+1}$，则

$$
T^{m+k+1} v=T^{m+1}(T^k v)=0
$$

由于 $\ker T^m=\ker T^{m+1}$，故 

$$
T^m(T^k v)=T^{m+k} v=0
$$

从而 $v\in \ker T^{m+k}$，即证。

这个定理表明，如果在某一时刻核空间不再扩大，那么之后的所有核都相同。

**定理 6.1.2**

设 $V$ 是有限维的，$T\in\mathcal L(V)$，则 $\ker T^{\dim V}=\ker T^{\dim V+1}$

**证明**

设 $n=\dim V$，假设 $\ker T^n\ne \ker T^{n+1}$，则有

$$
\{0\}\subsetneq\ker T\subsetneq\dots\subsetneq \ker T^n\subsetneq \ker T^{n+1}
$$

上述序列中每一个的维数都至少增加1，因此 $\dim\ker T^{n+1}\ge n+1$，产生矛盾。

以上两个定理表明，在有限维空间上，$T^m$ 的核最多扩大到 $\ker T^{\dim V}$。

对于 $T^m$ 的像，我们可以类似地证明：随着 $T$ 的自乘，其像空间不断缩小，且在有限维空间上，像最多缩小到 $\mathrm{im}\ T^{\dim V}$。下面的讨论中用不到 $T^m$ 的像空间，因此上面的结论留给读者自证。

根据线性映射基本定理，我们有 $\dim V=\dim\ker T+\dim\mathrm{im}\ T$，但并不总是有 $V=\ker T\oplus \mathrm{im}\ T$。幸运的是，我们有下面的定理作为替代。

**定理 6.1.3**

设 $V$ 是有限维的，$T\in\mathcal L(V)$，则有 $V=\ker T^{\dim V}\oplus\mathrm{im}\ T^{\dim V}$

**证明**

设 $n=\dim V, v\in \ker T^n \cap \mathrm{im}\ T^n$，则 $T^n v=0$，且存在 $u$ 使 $v=T^n u$。将 $T^n$ 应用于等式两边，则有 $T^{2n}u=0$。由于 $\ker T^n=\ker T^{2n}$，于是 $v=T^n u=0$，即 $\ker T^n \cap \mathrm{im}\ T^n=\{0\}$。

这表明 $\ker T^n+\mathrm{im}\ T^n$ 是直和，从而

$$
\dim(\ker T^n\oplus\mathrm{im}\ T^n)=\dim \ker T^n+\dim \mathrm{im}\ T^n=\dim V
$$

即证。

在上一章，我们定义了特征空间 $E_\lambda(T)=\ker (T-\lambda I)$，事实证明，这个定义不能完全满足我们的要求，我们需要更多的特征向量。又由于算子自乘时核空间扩大，因此我们有如下定义：

**定义 6.1.4** 广义特征向量（Generalized Eigenvector），广义特征空间（Generalized Eigenspace）

设 $T\in\mathcal L(V),\lambda$ 是 $T$ 的一个特征值，则 $v\in V,v\ne 0$ 是对应于 $\lambda$ 的**广义特征向量**如果存在 $j$ 使得

$$
(T-\lambda I)^j v=0
$$

对应于 $\lambda$ 的所有广义特征向量连同零向量构成的集合称为对应于 $\lambda$ 的**广义特征空间**，记作 $G_\lambda(T)$。

在有限维空间上，我们有：

**定理 6.1.5**

设 $V$ 是有限维的，$T\in\mathcal L(V)$，则 $G_\lambda(T)=\ker(T-\lambda I)^{\dim V}$

**证明**

设 $n=\dim V$，显然有 $\ker(T-\lambda I)^n\subset G_\lambda(T)$，现设 $v\in G_\lambda(T)$，则有

$$
(T-\lambda I)^j v=(T-\lambda I)^n v=0
$$

故 $v\in\ker (T-\lambda I)^n$，即证。

我们在上一章证明了对应于不同特征值的特征向量是线性无关的，现在我们来证明这一结果对广义特征向量也成立。

**定理 6.1.6**

设 $T\in\mathcal L(V), \lambda_1,\dots,\lambda_m$ 是 $T$ 的不同特征值，对应的广义特征向量为 $v_1,\dots,v_m$，则 $v_1,\dots,v_m$ 线性无关。

**证明**

取定 $j$，设 $k$ 是使得 $(T-\lambda_j I)^k v_j\ne 0$ 的最大整数，设 

$$
w=(T-\lambda_j I)^k v_j
$$

则 $(T-\lambda_j I)w=0$，即 $Tw=\lambda_j w$。

则对任意 $\lambda\in\mathbb F$，有 $(T-\lambda I)w=(\lambda_j-\lambda)w$，于是 $(T-\lambda I)^n w=(\lambda_j-\lambda)^n w, n=\dim V$。

设 $a_1v_1+\dots+a_j v_j+\dots+a_mv_m=0$，将算子

$$
(T-\lambda_1 I)^n \dots (T-\lambda_j I)^k \dots (T-\lambda_m I)^n
$$

应用在上式两边，则有 $a_j (\lambda_j-\lambda_1)^n\dots(\lambda_j-\lambda_m)^n w=0$，从而 $a_j=0$。由 $j$ 的任意性，则有 $a_1=\dots=a_m=0$，从而 $v_1,\dots,v_m$ 线性无关。

接下来我们考虑有限维算子 $T-\lambda I$ 在广义特征空间上的限制 $(T-\lambda I)|_{G_\lambda}$。由定义我们可以知道，存在 $n$ 使得对任意 $v\in G_\lambda$ 都有 $(T-\lambda I)^n v=0$，于是 $(T-\lambda I)^n |_{G_\lambda}=0$。这种在连续自乘后最终变成0的算子非常重要，因此我们给出如下定义：

**定义 6.1.7** 幂零的（Nilpotent）

算子 $T\in\mathcal L(V)$ 称为**幂零的**，如果存在 $m$ 使得 $T^m=0$

下面的定理表明，存在一个基，使得幂零算子有一个相对简单的矩阵。

**定理 6.1.8**

设 $V$ 是有限维的，$N\in\mathcal L(V)$ 是幂零的，则 $V$ 有一个基使得 $\mathcal M(N)$ 是上三角的，且对角线上元素均为0。

**证明**

我们先证 $N^{\dim V}=0$。由于 $V=G_0(N)$，故 $\ker N^{\dim V}=G_0(N)=V$。

下面我们先取 $\ker N$ 的一个基，然后扩充成 $\ker N^2$ 的基，然后扩充成 $\ker N^3$ 的基，如此下去，一直到 $\ker N^{\dim V}$ 的基。

现在我们考虑在这个基下的矩阵。最前面的几列全为0，因为它们对应的基向量在 $\ker N$ 中。下面一组列对应 $\ker N^2$ 中的基向量，对于 $v\in\ker N^2$，有 $Nv\in\ker N$，故这些基向量在 $N$ 的作用后是前面基向量的线性组合，从而在这些列中非零元素一定在对角线上方。再下面一组列对应 $\ker N^3$ 中的基向量，同理可知它们经 $N$ 作用后是前面向量的线性组合，因此非零元素在对角线上方。如此下去，我们就证明了在该基下，$N$ 的矩阵形如

$$
\begin{pmatrix}
0 &  & * \\
  & \ddots & \\
0 &  & 0
\end{pmatrix}
$$

现在有了广义特征向量，我们就可以对复向量空间上的算子进行很好的刻画。首先我们证明一个引理：

**定理 6.1.9**

设 $S,T\in\mathcal L(V), ST=TS$，则 $\ker S$ 与 $\mathrm{im}\ S$ 在 $T$ 下不变。

**证明**

设 $v\in\ker S$，则 $S(Tv)=T(Sv)=0$，即 $Tv\in\ker S$，则 $\ker S$ 在 $T$ 下不变。

设 $v\in\mathrm{im}\ S$，则 $v=Su$，于是 $Tv=T(Su)=S(Tu)\in\mathrm{im}\ S$，则 $\mathrm{im}\ S$ 在 $T$ 下不变。

**定理 6.1.10**

设 $V$ 是有限维非零复向量空间，$T\in\mathcal L(V), \lambda_1,\dots,\lambda_m$ 是 $T$ 的不同特征值，则

1. 每个 $(T-\lambda_j I)|_{G_{\lambda_j}}$ 是幂零的
2. 每个 $G_{\lambda_j}$ 在 $T$ 下不变
3. $V=G_{\lambda_1}\oplus\dots\oplus G_{\lambda_m}$
4. $V$ 有一个基使得 $T$ 有分块对角矩阵

$$
\begin{pmatrix}
A_1 & & 0 \\
& \ddots & \\
0 & & A_m
\end{pmatrix}
$$

其中每个 $A_j$ 都是上三角的，且对角线上元素均为 $\lambda_j$ 

**证明**

由定义我们立即得到1。设 $n=\dim V$，我们知道 $G_{\lambda_j}=\ker (T-\lambda_j I)^n$，又算子的多项式 $p(T)$ 与 $T$ 是交换的，于是 $G_{\lambda_j}$ 在 $T$ 下不变，于是证明了2。

下面我们使用数学归纳法来证明3。当 $n=1$ 时，结论显然成立。现在假设结论对于维数小于 $n$ 的空间都成立。

由于 $T$ 有特征值，设为 $\lambda_1$，因此我们有

$$
V=G_{\lambda_1}(T) \oplus \mathrm{im}(T-\lambda_1 I)^n
$$

设 $U=\mathrm{im}(T-\lambda_1 I)^n$，则 $U$ 在 $T$ 下不变，且 $\dim U<n$。于是我们可以对 $T|_U$ 应用归纳假设，则

$$
U=G_{\lambda_2}(T|_U)\oplus\dots\oplus G_{\lambda_m}(T|_U)
$$

现在我们只需证明对于每个 $j\ge 2$ 都有 $G_{\lambda_j}(T)=G_{\lambda_j}(T|_U)$。

$G_{\lambda_j}(T|_U)\subset G_{\lambda_j}(T)$ 是显然的。设 $v\in G_{\lambda_j}(T)$，则有唯一分解 $v=v_1+u,v_1\in G_{\lambda_1}(T),u\in U$，且 $u=v_2+\dots+v_m,v_j\in G_{\lambda_j}(T)$，于是

$$
v=v_1+\dots+v_j+\dots+v_m
$$

由于对应于不同特征值的广义特征向量线性无关，因此除了 $v_j$ 外其他的 $v_i$ 均为0，特别地，$v_1=0$，于是 $v=u\in U$，所以 $v\in G_{\lambda_j}(T|_U)$，即证。

接下来我们考虑 $T$ 在 $G_{\lambda_j}$ 上的限制，由于 $(T-\lambda_j I)|_{G_{\lambda_j}}$ 是幂零的，于是我们可以取 $G_{\lambda_j}$ 的基使得其矩阵为上三角的，且对角线上元素为0。又因为

$$
T|_{G_{\lambda_j}}=\lambda_j I|_{G_{\lambda_j}} + (T-\lambda_j I)|_{G_{\lambda_j}}
$$

故 $T|_{G_{\lambda_j}}$ 的矩阵形如

$$
A_j=
\begin{pmatrix}
\lambda_j & & *\\
& \ddots & \\
0 & & \lambda_j
\end{pmatrix}
$$

将所有这样的 $G_{\lambda_j}$ 的基放在一起就得到了 $V$ 的一个基，在这个基下 $T$ 的矩阵就是我们想要的形式。

读者可以对比定理5.3.4与上面的定理，我们可以发现，利用广义特征向量，我们得以优化定理5.3.4的结果。

在直和分解 $V=G_{\lambda_1}\oplus\dots\oplus G_{\lambda_m}$ 中，每一部分的维数非常重要，因此我们给它一个定义：

**定义 6.1.11** 代数重数（Algebraic Multiplicity），几何重数（Geometric Multiplicity）

设 $T\in\mathcal L(V),\lambda$ 是 $T$ 的一个特征值，则 $\lambda$ 的**代数重数**（简称**重数**）定义为 $\dim G_{\lambda}(T)$，**几何重数**定义为 $\dim E_{\lambda}(T)$。

显然 $E_{\lambda}(T)\subset G_{\lambda}(T)$，于是我们有 $\lambda$ 的几何重数 $\le$ 代数重数。并且我们可以证明，$T$ 可对角化当且仅当对任意 $\lambda$ 都有代数重数 $=$ 几何重数。

根据定理6.1.10，我们还能知道特征值 $\lambda_j$ 在定理中所描述的矩阵的对角线上出现的次数就是 $\lambda_j$ 的重数。

> **注**：有些教材上将广义特征空间称为“根子空间”，这是因为 $(z-\lambda_j)^{d_j}$（其中 $d_j$ 是特征值 $\lambda_j$ 的重数）是 $T$ 的特征多项式的一个因子。关于特征多项式的内容我们将在之后介绍。

# Section 2: Jordan基与Jordan形

在定理6.1.10中，我们得到了一个有足够多0的上三角矩阵，然而事实上我们可以做的更好：我们将证明，存在一个基使得算子的矩阵中只有对角线与在对角线上方的副对角线有非零元素，构成我们所说的**Jordan形**，下面我们就来完成这一目标。

回顾定理6.1.10的证明过程，我们可以发现，在分块 $A_j$ 中，对角线上是特征值，而对 $A_j$ 的元素起决定作用的则是幂零算子 $(T-\lambda_j I)|_{G_{\lambda_j}}$ 以及定理6.1.8。因此，深入考察幂零算子的矩阵是有必要的。

下面我们先来看一个例子。设 $N\in\mathcal L(\mathbb C^6)$ 为

$$
N(z_1,z_2,z_3,z_4,z_5,z_6)=(0,z_1,z_2,0,z_4,0)
$$

经过观察，我们发现，如果取 $e_j$ 为第 $j$ 个位置为1，其余位置为0的向量，则向量组

$$
N^2 e_1,Ne_1,e_1,Ne_4,e_4,e_6
$$

是一个基，并且在这个基下，$N$ 的矩阵形如

$$
\begin{pmatrix}
0 & 1 & 0 & & &0\\
0 & 0 & 1 & & &\\
0 & 0 & 0 & & &\\
& & & 0 & 1 & \\
& & & 0 & 0 & \\
0& & & & & 0 
\end{pmatrix}
$$

注意每个分块中只有副对角线上有非零元素。受上面的例子启发，我们将证明：每个幂零算子都可以化成上面这样的结构。

**定理 6.2.1**

设 $V$ 是有限维的，$N\in\mathcal L(V)$ 是幂零的，则有向量 $v_1,\dots,v_n$ 和非负整数 $m_1,\dots,m_n$ 使得

1. 对每个 $j$ 有 $N^{m_j+1}v_j=0$
2. $N^{m_1}v_1,\dots,Nv_1,v_1,\dots,N^{m_n}v_n,\dots,Nv_n,v_n$ 是 $V$ 的一个基，且在该基下 $N$ 有分块对角矩阵

$$
\begin{pmatrix}
N_1 & & 0\\
& \ddots & \\
0 & & N_p
\end{pmatrix}
$$

每个 $N_j$ 都形如

$$
\begin{pmatrix}
0 & 1 & & 0\\
& \ddots & \ddots & \\
& & \ddots & 1 \\
0 & & & 0
\end{pmatrix}
$$

**证明**

我们使用数学归纳法。当 $n=\dim V=1$ 时，仅有的幂零算子是0算子，则取 $v_1\ne 0,m_1=0$ 即可。现假设结论对于维数小于 $n$ 的空间都成立。

$N$ 是幂零的，故 $N$ 不是单射，于是 $N$ 不是满射，因此 $\dim \mathrm{im}\ N<n$。如果 $\mathrm{im}\ N=\{0\}$，则 $N$ 是0算子，则结论显然成立，因此我们可以假设 $\mathrm{im}\ N\ne \{0\}$。

对限制算子 $N|_{\mathrm{im}\ N}\in\mathcal L(\mathrm{im}\ N)$ 应用归纳假设，则有 $v_1,\dots,v_k$ 和 $m_1,\dots,m_k$ 使得

$$
N^{m_1}v_1,\dots,Nv_1,v_1,\dots,N^{m_k}v_k,\dots,Nv_k,v_k
$$

是 $\mathrm{im}\ N$ 的基，且 $N^{m_j+1}v_j=0$。

因为 $v_j\in\mathrm{im}\ N$，所以有 $v_j=Nu_j$，现在我们断言

$$
N^{m_1+1}u_1,\dots,Nu_1,u_1,\dots,N^{m_k+1}u_k,\dots,Nu_k,u_k
$$

是线性无关的。为证明这个断言，设各 $N^i u_j$ 的线性组合等于0，将 $N$ 应用于等式两边，就得到了一个 $N^i v_j$ 的线性组合，因此，除了

$$
N^{m_1+1}u_1,\dots,N^{m_k+1}u_k
$$

的系数外，其他系数都为0。而上面这组向量为

$$
N^{m_1}v_1,\dots,N^{m_k}v_k
$$

因此这些向量系数也为0。这就完成了线性无关性的证明。

现在将这些向量扩充为 $V$ 的基

$$
N^{m_1+1}u_1,\dots,Nu_1,u_1,\dots,N^{m_k+1}u_k,\dots,Nu_k,u_k,w_1,\dots,w_p
$$

由于 $Nw_j\in\mathrm{im}\ N$，故 $Nw_j$ 可以表示为 $N^i v_j$ 的线性组合，而每个 $N^i v_j$ 都等于 $N$ 在某个 $N^i u_j$ 上的作用，从而存在 $x_j=\sum N^i u_j$ 使得 $Nw_j=Nx_j$。

现在令 $u_{k+j}=w_j-x_j$，则 $Nu_{k+j}=0$，并且

$$
N^{m_1+1}u_1,\dots,Nu_1,u_1,\dots,N^{m_k+1}u_k,\dots,Nu_k,u_k,u_{k+1},\dots,u_{k+p}
$$

是 $V$ 的基，且这个基具有我们所要求的形式。类比一开始的例子，我们可以知道在这个基下，$N$ 的矩阵也有我们要求的形式。注意对应于 $u_{k+j}$ 的分块是 $1\times 1$ 的零矩阵。

现在我们就可以将这个定理应用于一般的复向量空间上的算子了。注意，在下面的定义中，每个 $\lambda_j$ 不一定是不同的，$J_k$ 也有可能是 $1\times 1$ 的矩阵 $(\lambda_j)$。

**定义 6.2.2** Jordan基（Jordan Basis），Jordan形（Jordan Form）

设 $T\in \mathcal L(V), V$ 的一个基称为 $T$ 的**Jordan基**如果在这个基下，$T$ 有分块对角矩阵

$$
\begin{pmatrix}
J_1 & & 0 \\
& \ddots & \\
0 & & J_p
\end{pmatrix}
$$

每个 $J_k$ 形如

$$
\begin{pmatrix}
\lambda_j & 1 & & 0 \\
& \ddots & \ddots & \\
& & \ddots & 1 \\
0 & & & \lambda_j
\end{pmatrix}
$$

这个矩阵就称为 $T$ 的**Jordan形**。

**定理 6.2.3**

设 $V$ 是有限维非零复向量空间，$T\in\mathcal L(V)$，则 $V$ 有一个基是 $T$ 的Jordan基。

**证明**

我们已经证明了结论对幂零算子成立（定理6.2.1），现在设 $T$ 的不同特征值为 $\lambda_1,\dots,\lambda_m$，则有广义特征分解

$$
V=G_{\lambda_1}\oplus\dots\oplus G_{\lambda_m}
$$

每个 $(T-\lambda_j I)|_{G_{\lambda_j}}$ 都是幂零的，于是可以取 $G_{\lambda_j}$ 的一个基使其为 $(T-\lambda_j I)|_{G_{\lambda_j}}$ 的Jordan基。将所有这些基组合起来就得到了 $V$ 的一个基，且是 $T$ 的Jordan基。

> **注**：我们在定义Jordan形时令每个Jordan分块在对角线和对角线上方的副对角线上有非零元素，这主要是为了与前面上三角化的讨论保持一致。实际上我们也可以令每个Jordan分块在对角线和对角线下方的副对角线上有非零元素，这样的矩阵也可称为Jordan形，证明时只需把定理6.2.1中的基按 $N$ 的次数升序排列即可（如 $v_1,Nv_1,\dots,N^{m_1}v_1,\dots$）。

我们可以从Jordan形中直接读出算子 $T$ 的一些结构。例如，在Jordan块中，对角线上元素为 $\lambda_j$ 的分块的个数就是 $\lambda_j$ 的几何重数，这给出了可对角化等价于代数重数 $=$ 几何重数的一个简单证明。

# Section 3: 特征多项式与极小多项式

每个复向量空间上的算子都有两个多项式与之关联：特征多项式与极小多项式，它们反映了算子与其特征值的一些关联。我们先来介绍特征多项式。

**定义 6.3.1** 特征多项式（Characteristic Polynomial）

设 $V$ 是复向量空间，$T\in\mathcal L(V),\lambda_1,\dots,\lambda_m$ 是 $T$ 的不同特征值，重数分别为 $d_1,\dots,d_m$，则多项式

$$
\Delta_T(z)=(z-\lambda_1)^{d_1}\dots(z-\lambda_m)^{d_m}
$$

称为 $T$ 的**特征多项式**。

在下一章，我们将介绍特征多项式的一个等价定义（行列式），但是比起行列式的定义，我们的定义在使用时更为方便。

根据定义，我们立即得到：

**定理 6.3.2**

设 $V$ 是有限维复向量空间，$T\in\mathcal L(V)$，则

1. $\deg \Delta_T =\dim V$
2. $\Delta_T$ 的所有零点都是 $T$ 的特征值

下面的定理是复向量空间上算子的中心结果之一，然而使用我们的定义，我们得到了一个简单证明。

**定理 6.3.3** Cayley-Hamilton定理

设 $V$ 是有限维复向量空间，$T\in\mathcal L(V)$，则 $\Delta_T(T)=0$

**证明**

设 $\lambda_1,\dots,\lambda_m$ 是 $T$ 的不同特征值，重数分别为 $d_1,\dots,d_m$，于是在 $G_{\lambda_j}$ 上，有 $(T-\lambda_j I)^{d_j}|_{G_{\lambda_j}}=0$（因为 $N^{\dim V}=0$）。

由于广义特征分解是直和，因此我们只需证明对任意 $j$ 都有 $\Delta_T(T)|_{G_{\lambda_j}}=0$。我们有

$$
\Delta_T(T)=(T-\lambda_1 I)^{d_1}\dots (T-\lambda_m I)^{d_m}
$$

由于算子的多项式是交换的，将 $(T-\lambda_j I)^{d_j}$ 换到 $\Delta_T(T)$ 的最右端，则对任意 $v\in G_{\lambda_j}$ 有 $\Delta_T(T)|_{G_{\lambda_j}}(v)=0$，从而 $\Delta_T(T)|_{G_{\lambda_j}}=0$，即证。

下面我们来看极小多项式，首先我们来证明它的存在唯一性。

**定理 6.3.4**

设 $V$ 是有限维的，$T\in\mathcal L(V)$，则存在唯一一个次数最小的首一多项式 $p$ 使得 $p(T)=0$

**证明**

设 $n=\dim V$，则 $\mathcal L(V)$ 中长度为 $n^2+1$ 的向量组

$$
I,T,T^2,\dots,T^{n^2}
$$

线性相关。设 $m$ 是使得 $T^m\in \mathrm{span}(I,T,\dots,T^{m-1})$ 的最小整数，于是

$$
a_0 I+a_1T+\dots+a_{m-1}T^{m-1}+T^m=0
$$

令 $p(z)=a_0+a_1z+\dots+a_{m-1}z^{m-1}+z^m$，由 $m$ 的最小性，则有 $p$ 的次数最小，且 $p(T)=0$。

假设有 $q(T)=0$ 且 $\deg q=m$，则 $(p-q)(T)=0,\deg(p-q)<m$，与 $m$ 的最小性矛盾，因此 $p$ 是唯一的。

于是我们可以对每个算子定义极小多项式。由上面的证明可以知道，极小多项式的次数最高为 $(\dim V)^2$。

**定义 6.3.5** 极小多项式（Minimal Polynomial）

设 $T\in\mathcal L(V)$，则 $T$ 的**极小多项式** $m_T$ 定义为唯一一个使得 $m_T(T)=0$ 的次数最小的首一多项式。

下面的定理揭示了特征多项式与极小多项式之间的关系。

**定理 6.3.6**

设 $T\in\mathcal L(V),p\in \mathbb F[z]$，则 $p(T)=0$ 当且仅当 $m_T$ 整除 $p$

**证明**

假设 $m_T$ 整除 $p$，则有多项式 $q$ 使得 $p=qm_T$，于是 $p(T)=q(T)m_T(T)=0$。

现假设 $p(T)=0$，根据多项式的带余除法，有

$$
p=qm_T+r
$$

且 $\deg r<\deg m_T$。故 $p(T)=r(T)=0$，这表明 $r=0$（若不然，令 $r$ 除以其最高次项系数，就得到一个次数小于极小多项式的零化多项式）。从而 $m_T$ 整除 $p$。

从上面定理立即得到：$m_T$ 整除 $\Delta_T$。

下面的定理进一步确定了极小多项式的结构。

**定理 6.3.7**

设 $T\in\mathcal L(V)$，则 $T$ 的特征值都是 $m_T$ 的零点。

**证明**

设 $\lambda\in \mathbb F$ 是 $m_T$ 的零点，则有分解

$$
m_T(z)=(z-\lambda)p(z)
$$

由于 $\deg p<\deg m_T$，故存在 $v\ne 0$ 使得 $p(T)v\ne 0$，于是

$$
m_T(T)=(T-\lambda I)p(T)v=0
$$

表明 $(T-\lambda I)v=0$，即 $\lambda$ 是 $T$ 的特征值。

现设 $\lambda$ 是 $T$ 的特征值，则有 $Tv=\lambda v$，将 $T$ 应用于等式两边则有 $T^j v=\lambda^j v$，于是

$$
\begin{align*}
m_T(T)v&=(a_0I+a_1T+\dots+a_{m-1}T^{m-1}+T^m)v\\
&=(a_0+a_1\lambda+\dots+a_{m-1}\lambda^{m-1}+\lambda^m)v\\
&=m_T(\lambda)v=0
\end{align*}
$$

这表明 $m_T(\lambda)=0$。

因此，对于复向量空间上的算子，我们有

$$
m_T(z)=(z-\lambda_1)^{k_1}\dots(z-\lambda_m)^{k_m}
$$

其中 $1\le k_j\le d_j, d_j$ 是 $\lambda_j$ 的重数。而各 $k_j$ 我们可以从 $T$ 的Jordan形中确定。

设 $T$ 的Jordan形为

$$
\begin{pmatrix}
J_1 & & 0 \\
& \ddots & \\
0 & & J_p
\end{pmatrix}
$$

我们着重关注对角线上为 $\lambda_j$ 的Jordan块，我们知道这些分块来源于 $G_{\lambda_j}$ 上的一个Jordan基：

$$
N^{m_1}v_1,\dots,Nv_1,v_1,\dots,N^{m_n}v_n,\dots,Nv_n,v_n
$$

其中 $N=(T-\lambda_j I)|_{G_{\lambda_j}}$。

令 $k_j=1+\max(m_1,\dots,m_n)$，则对任意 $k$，我们有 $N^{k_j}v_k=0$，因此 $(T-\lambda_j I)^{k_j}|_{G_{\lambda_j}}=0$，于是 $(z-\lambda_j)^{k_j}$ 是 $m_T$ 的一个因子。由多项式的交换性，我们就有

$$
m_T(z)=(z-\lambda_1)^{k_1}\dots(z-\lambda_m)^{k_m}
$$

换句话说，$m_T$ 中 $z-\lambda_j$ 的次数是对应于 $\lambda_j$ 的最大的Jordan块的阶数。

由上面的讨论，我们立即得到下面的等价定理：

**定理 6.3.8**

设 $V$ 是有限维复向量空间，$T\in\mathcal L(V)$，则 $T$ 可对角化当且仅当 $m_T$ 没有重根。

# Section 4: 总结

本章我们深入研究了复向量空间上的算子，介绍了算子的分解，Jordan形，以及两个特殊的多项式。然而，我们所证明的都是“存在性定理”，它们无法告诉我们如何求得算子的特征值。下一章，我们将引入算子的**迹**与**行列式**（第二次），并给出一个计算算子特征值的方法。

本期内容就是这样，感谢观看！