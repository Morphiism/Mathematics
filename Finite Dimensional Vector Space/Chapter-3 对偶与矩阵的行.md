[[Chapter-2 子空间与方程组的解]]

在前两章中，我们主要研究向量空间 $V\to W$ 的线性映射，从而把握了矩阵（进而把握了方程组）的性质，然而这并不是全部：迄今为止我们研究矩阵都是以各列为基础，但对于矩阵的行我们知之甚少。在本章中，我们将研究矩阵的行的性质，进而得到所谓的**对偶空间**，最后我们将证明，矩阵的行秩等于矩阵的列秩。

这一章可以看作第一章的“对偶”：我们从矩阵出发，进而反推向量空间与线性映射的结构，然后再证明我们得到的线性映射符合我们的直观。

# Section 1: 对偶空间

我们从矩阵 $A$ 的一行说起，根据矩阵乘法的定义，我们知道

$$
\begin{bmatrix} c_1 & \dots & c_n \end{bmatrix}
\begin{bmatrix} x_1 \\ \vdots \\ x_n \end{bmatrix}=
c_1x_1+\dots+c_nx_n
$$

我们看到，左乘一个行向量对应于一个 $V\to \mathbb F$ 的线性映射（也称为 $V$ 上的**线性泛函**）：

$$
\varphi (x_1v_1+\dots+x_nv_n)=x_1c_1+\dots+x_nc_n
$$

因此我们提出如下定义：

**定义 3.1.1** 对偶空间（Dual Space）

$V$ 的**对偶空间** $V^*$ 定义为 $V$ 上的线性泛函构成的集合 $\mathcal L(V,\mathbb F)$

显然 $V^*$ 是一个向量空间，如果 $V$ 是有限维的，那么 $\dim V=\dim V^*$，并且 $V^*$ 有一个特殊的基：

**定义 3.1.2** 对偶基（Dual Basis）

设 $V$ 的一个基为 $v_1,\dots,v_n$，则它的**对偶基**定义为 $V^*$ 中的向量 $\varphi_1,\dots,\varphi_n$ 满足

$$
\varphi_j(v_k)=\delta_{jk}=\begin{cases} 1, & j=k \\ 0, & j\ne k \end{cases}
$$

从而 $\varphi_1,\dots,\varphi_n$ 的矩阵就是 $\mathbb F^{1,n}$ 中的行向量 

$$
\begin{bmatrix} 1 & 0 & \dots & 0 \end{bmatrix},\begin{bmatrix} 0 & 1 & \dots & 0 \end{bmatrix},\dots,\begin{bmatrix} 0 & 0 & \dots & 1 \end{bmatrix}
$$

因此读者可以验证对偶基的确是一个基。

熟悉矩阵论的读者会注意到，将 $v_j$ 映为 $\varphi_j$ 的映射可以等价为列向量的**转置**。一般来说，$m\times n$ 的矩阵 $A$ 的**转置** $A^T$ 是 $n\times m$ 的矩阵 $B$ 使得

$$
A_{jk}=B_{kj},1\le j\le m,1\le k\le n
$$

对于线性映射 $T$，其矩阵为 $A$，我们希望其**对偶映射** $T^*$ 的矩阵为 $A^T$，从而我们可以借助 $T^*$ 来研究矩阵的各行。根据这个原则，我们给出如下定义：

**定义 3.1.3** 对偶映射（Dual Map）

设 $T\in \mathcal L(V,W)$，其**对偶映射**定义为 $T^*\in \mathcal L(W^*,V^*)$ 使得对 $\varphi \in W^*$ 有

$$
T^*(\varphi)=\varphi \circ T
$$

我们已经知道，$\mathcal M(\varphi)$ 是行向量，因此 $\mathcal M(T^*(\varphi))$ 就是矩阵 $A$ 的*各行的线性组合*，特别地，$\mathcal M(T^*(\varphi_j))$ 就是矩阵的第 $j$ 行。于是读者可以验证 $T^*$ 的矩阵的确是 $A^T$。

下面我们来证明线性映射的对偶符合矩阵的转置的性质：

**定理 3.1.4** 

对 $S,T\in\mathcal L(V,W),R\in\mathcal L(U,V)$ 和 $\lambda\in \mathbb F$ 有

- $(S+T)^*=S^*+T^*$
- $(\lambda T)^*=\lambda T^*$
- $(SR)^*=R^* S^*$

**证明**

前两条的正确性是显然的，因此我们来证明第三条。取 $\varphi\in W^*$，则

$$
(SR)^*(\varphi)=\varphi \circ (SR)=R^* (\varphi \circ S)=R^*(S^*(\varphi))=(R^* S^*)(\varphi)
$$

因此 $(SR)^*=R^* S^*$，这对应了矩阵转置 $(AB)^T=B^T A^T$ 的性质。

# Section 2: 对偶映射的核与像

对于线性映射 $T$ 与其对偶 $T^*$，我们希望用 $T$ 的核与像去描述 $T^*$ 的核与像。

我们先来看 $\ker T^*$。设 $\psi\in \ker T^*,v\in V$，则

$$
T^*(\psi)(v)=(\psi\circ T)(v)=\psi (Tv)=0
$$

于是对任意 $w\in \mathrm{im}\ T=T(V)$，有 $\psi(w)=0$，从而 

$$
\ker T^* \subset \{\psi\in W^*\colon \psi(w)=0,\forall w\in\mathrm{im}\ T\}
$$

容易看出反向的包含也成立。为此我们定义：

**定义 3.2.1** 零化子（Annihilator）

设 $U$ 是 $V$ 的子空间，则 $U$ 的**零化子**定义为

$$
U^0=\{\varphi\in V^*\colon \varphi(u)=0,\forall u\in U\}
$$

于是有 $\ker T^*=(\mathrm{im}\ T)^0$。根据对偶性，我们猜想 $\mathrm{im}\ T^*=(\ker T)^0$，而事实也的确如此。

**定理 3.2.2**

设 $V,W$ 是有限维的，$T\in \mathcal L(V,W)$，则

- $\ker T^*=(\mathrm{im}\ T)^0$
- $\mathrm{im}\ T^*=(\ker T)^0$

**证明**

第一条已完成证明（注意第一条的证明中不需要用到有限维的条件），现在我们来证第二条。

设 $\varphi\in \mathrm{im}\ T^*$，则存在 $\psi\in W^*$ 使得 $\varphi=T^*(\psi)=\psi\circ T$。于是对于 $v\in \ker T$ 有 $\varphi(v)=\psi(Tv)=0$，则 $\mathrm{im}\ T^*\subset (\ker T)^0$。

现设 $\varphi\in (\ker T)^0$，则 $\varphi(v)=0,v\in \ker T$，即 $\ker T\subset \ker \varphi$。现在我们要证存在 $\psi\in W^*$ 使得 $\varphi=\psi\circ T$，从而有 $\varphi \in \mathrm{im}\ T^*$。

设 $v\in V, Tv=w$，则在 $\mathrm{im}\ T$ 上定义 $\psi(w)=\varphi(v)$，我们需要证明该定义是*良定*的。为此，设 $Tv_1=Tv_2=w$，于是 $T(v_1-v_2)=0,v_1-v_2\in \ker T$，则 $v_1-v_2\in\ker \varphi$，即 $\varphi(v_1-v_2)=0,\varphi(v_1)=\varphi(v_2)$。

接下来我们要把 $\psi$ 的定义扩展到 $W$ 上，为此，设 $\mathrm{im}\ T$ 的基为 $w_1,\dots,w_k$，将其扩展为 $W$ 的基 $w_1,\dots,w_k,\dots,w_n$，定义 $\psi(w_j)=0,j\ge k+1$ 即证。

由此我们可以对 $T^*$ 的单性和满性做出判断：

**定理 3.2.3**

设 $T\in \mathcal L(V,W)$，则

- $T$ 是单的当且仅当 $T^*$ 是满的
- $T$ 是满的当且仅当 $T^*$ 是单的

**证明**

1. $T$ 是单的当且仅当 $\ker T=\{0\}$，当且仅当 $\mathrm{im}\ T^*=(\ker T)^0=V^*$，当且仅当 $T^*$ 是满的。
2. $T$ 是满的当且仅当 $\mathrm{im}\ T=W$，当且仅当 $\ker T^*=(\mathrm{im}\ T)^0=\{0\}$，当且仅当 $T^*$ 是单的。

接下来我们证明零化子 $U^0$ 是 $V^*$ 的子空间，于是我们可以讨论它的维数：

**定理 3.2.4**

设 $V$ 是有限维的，$U$ 是 $V$ 的子空间，则有

$$
\dim V=\dim U+\dim U^0
$$

**第一种证明**

定义 $i$ 为 $U\to V$ 的嵌入映射：$i(u)=u$，取其对偶 $i^*$，则有 $i^*(\varphi)=\varphi\circ i$，从而 $\ker i^*=U^0$，并且 $\mathrm{im}\ i^*=U^*$。由线性映射基本定理得

$$
\dim V^*=\dim \ker i^*+\dim \mathrm{im}\ i^*
$$

于是有 $\dim V=\dim U+\dim U^0$。

**第二种证明（思路）**

取 $U$ 的一个基 $v_1,\dots,v_m$，扩充为 $V$ 的基 $v_1,\dots,v_m,\dots,v_n$，取其对偶基 $\varphi_1,\dots,\varphi_n$，然后证明 $\varphi_{m+1},\dots,\varphi_n$ 是 $U^0$ 的基。

只要对定义清晰，读者不难完成上述证明过程。

根据这个定理，我们可以得到各个子空间的维数：

**定理 3.2.5**

设 $V,W$ 是有限维的，$T\in \mathcal L(V,W)$，则

- $\dim \ker T^*=\dim \ker T+\dim W-\dim V$
- $\dim \mathrm{im}\ T^*=\dim \mathrm{im}\ T$

**证明**

$$
\begin{align*}
\dim \ker T^* &=\dim (\mathrm{im}\ T)^0\\
&=\dim W-\dim \mathrm{im}\ T\\
&=\dim W-(\dim V-\dim \ker T)\\
&=\dim \ker T+\dim W-\dim V
\end{align*}
$$

由上式可得 

$$
\dim W-\dim \ker T^*=\dim W^*-\dim \ker T^*=\dim V-\dim\ker T
$$

即 $\dim \mathrm{im}\ T^*=\dim \mathrm{im}\ T$。

现在我们就能证明矩阵的行秩等于列秩，为此，我们先定义秩的概念。

**定义 3.2.6** 行秩（Row Rank），列秩（Column Rank）

矩阵 $A$ 的**行秩**定义为 $A$ 的各行的张成空间在 $\mathbb F^{1,n}$ 中的维数，**列秩**定义为 $A$ 的各列的张成空间在 $\mathbb F^{m,1}$ 中的维数。

**定理 3.2.7**

矩阵 $A$ 的行秩等于列秩。

**证明**

由矩阵的定义可知 $A$ 的列秩等于 $\dim \mathrm{span}(Tv_1,\dots,Tv_m)=\dim \mathrm{im}\ T$，又由于 $\mathcal M(T^*)=A^T$，故 $A$ 的行秩等于 $A^T$ 的列秩等于 $\dim \mathrm{im}\ T^*$。综上，$A$ 的行秩等于列秩。

既然行秩等于列秩，那么我们可以不区分行与列，而使用统一的术语**秩**。

于是我们可以证明线性方程组和矩阵论中的一个重要定理：

**定理 3.2.8**

设 $V$ 是有限维的，$T\in \mathcal L(V),\mathcal M(T)=A$，则以下命题等价：

1. $T$ 可逆（从而 $A$ 可逆）
2. $A$ 的各列线性无关
3. $A$ 的各列张成 $\mathbb F^{n,1}$
4. $A$ 的各行线性无关
5. $A$ 的各行张成 $\mathbb F^{1,n}$

**证明**

在上一章我们已证明了1，2，3的等价性，现在证明1，4，5的等价性。

$(1\to 4)$ 由1可得2，3，从而 $A$ 的秩为 $n$，因此 $A$ 的各行线性无关。

$(4\to 5)$ $A$ 的各行线性无关，故 $A$ 的各行是 $\mathbb F^{1,n}$ 的一个基，于是证明了5。

$(5\to 1)$ $A$ 的秩为 $n$，从而 $\dim \mathrm{im}\ T=n$，故 $T$ 是满射，于是 $T$ 可逆。

这也是消元法与行变换能够成功的原因。

# Section 3: 二次对偶与同构性

根据矩阵转置的性质，我们自然会猜想，$V^*$ 的对偶同构于 $V$，这对应了 $(A^T)^T=A$ 的性质，接下来我们就将证明这一点。

**定理 3.3.1**

设 $V$ 是有限维的，则 $V^{**}=(V^*)^* \simeq V$

**证明**

定义 $\Phi\colon V\to V^{**}$ 满足对于 $v\in V,\varphi\in V^*$ 有

$$
(\Phi v)(\varphi)=\varphi(v)
$$

显然 $\Phi$ 是线性的。

现设 $\Phi v=0$，即 $(\Phi v)(\varphi)=\varphi(v)=0$，则 $v=0$，即 $\Phi$ 是单射。于是有 $\dim \Phi(V)=\dim V-\dim \ker \Phi=\dim V=\dim V^{**}$，故 $\Phi(V)=V^{**}$，即 $\Phi$ 是满射。从而 $\Phi$ 是一个同构。

这里，$\Phi$ 不依赖于基的选取，因而被称为一个**自然同构**。

读者可以尝试证明以下两个定理。

**定理 3.3.2**

设 $V$ 是有限维的，$U$ 是 $V$ 的子空间，则 $U\to V$ 的嵌入映射 $i(u)=u$ 的对偶映射 $i^*$ 是 $V^*/U^0 \to U^*$ 的自然同构。

**定理 3.3.3**

设 $V$ 是有限维的，$U$ 是 $V$ 的子空间，则 $V\to V/U$ 的商映射 $\pi(v)=v+U$ 的对偶映射 $\pi^*$ 是 $(V/U)^*\to U^0$ 的自然同构。

# Section 4: 总结

本章我们研究了对偶空间与对偶映射，从而建立了矩阵的行与列之间的等价性。下一章我们将研究行列式，不同于通常的以排列的逆序数为出发点的定义，我们将像矩阵一样建立一个自上而下、公理化的定义，并且可以证明这两种定义是等价的。

本期内容就是这样，感谢观看！