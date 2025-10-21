[[Chapter-1 矩阵是什么]]

在这一章中，我们将注意力转向线性映射的表示：矩阵，并补充一些我们之前忽略的内容。

我们已经知道，在给定两个基的情况下，线性映射构成的向量空间 $\mathcal L(V,W)$ 与矩阵构成的向量空间 $\mathbb F^{m,n}$ 有显然的同构 $\mathcal M$。因此，在本章中我们将不对矩阵与线性映射做区分。只不过读者应当明确，当我们在说“线性映射 $A$”时，我们实际指的是线性映射 $T$ 使得 $T$ 的矩阵为 $A$。

# Section 1: Gauss消元法

消元法的思想非常简单，它主要依赖于以下定理：

**定理 12.1.1**

设 $V$ 中的向量组 $v_1,\dots,v_j,\dots,v_k,\dots,v_m$ 线性无关，则以下向量组也线性无关：

1. $v_1,\dots,v_k,\dots,v_j,\dots,v_m$
2. $v_1,\dots,cv_j,\dots,v_k,\dots,v_m$，其中 $c\ne 0$
3. $v_1,\dots,v_j,\dots,v_k+cv_j,\dots,v_m$

上述定理的证明由线性无关的定义即得，并且如果把上述定理中的“无关”都改成“相关”，定理也成立。本质上，消元法就是对矩阵的行反复应用上述定理。对于矩阵的列在行变换中的变化，我们有如下定理：

**定理 12.1.2**

设 $T\in\mathcal L(V,W)$ 是单射，则 $v_1,\dots,v_m$ 线性无关当且仅当 $T(v_1),\dots,T(v_m)$ 线性无关。

**证明**

设 $v_1,\dots,v_m$ 线性无关，$a_1 T(v_1)+\dots+a_m T(v_m)=0$，则

$$
T(a_1v_1+\dots+a_mv_m)=0
$$

由于 $T$ 是单射，从而 $a_1v_1+\dots+a_mv_m=0$，由线性无关性得 $a_1=\dots=a_m=0$，即证。

另一个方向的蕴含同理。

要应用上述定理，我们需要注意到行变换对于矩阵的一列 $v_j$ 来说等同于用某个可逆矩阵 $E$（称为**初等矩阵**）乘以 $v_j$。由于 $E$ 是可逆的，从而 $E$ 是单射，应用定理12.1.2可知，行变换保持列的线性无关性不变。

下面我们给出本节的主要定理：

**定理 12.1.3** Gauss消元法（Gaussian Elimination）

给定矩阵 $A_{m\times n}$，则存在唯一的**简化行阶梯形矩阵（RREF）**$R_{m\times n}$ 和可逆矩阵 $E_{m\times m}$ 使得 $A=ER$

为了方便讨论，我们给出一些概念。设 $R$ 是一个RREF，则称每一行第一个非零元为**主元（Pivot）**，主元所在的列称为**主元列**，所在的行称为**主元行**。如果存在可逆矩阵 $E$ 使得 $A=EB$，则称 $A$ 和 $B$ **行等价**，记作 $A\overset{r}{\sim} B$。现在我们给出上述定理的证明（事实上，Gauss消元法指的是这个定理的存在性证明）。

**证明**

首先来证明存在性。给定矩阵 $A$，如果 $A=0$，则取 $R=0,E=I$ 即可，因此我们可以假设 $A\ne 0$。我们按以下步骤构造与 $A$ 行等价的RREF $R$：

第一步：

令 $k_1$ 为使得 $A$ 的第 $k$ 列非零的最小整数，取 $A_{j_1,k_1}\ne 0$，将 $A$ 的第 $j_1$ 行乘以 $\dfrac{1}{A_{j_1,k_1}}$，然后将变换后的 $j_1$ 行乘以 $-A_{j,k_1}$ 并加到第 $j$ 行，就创造了一个零元，将这一步重复 $m-1$ 次，依次消除 $k_1$ 列的其它非零元，最后交换第 $j_1$ 行与第一行，得到矩阵

$$
A_1=\begin{bmatrix}
0  & \dots &0 & 1 & * & \dots  & * \\
0  &  & 0  & 0 & * & &  *  \\
\vdots &  & \vdots  &  \vdots & \vdots & & \vdots \\
0  & \dots  & 0 & 0 & * &\dots   & *
\end{bmatrix}\overset{r}{\sim} A
$$

第 $l$ 步：

将 $A_{l-1}$ 的前 $l-1$ 行划去，得到矩阵 $A_{l-1}'$。如果 $A_{l-1}'=0$，则取 $R=A_{l-1}$。我们知道，定理12.1.1中的三种行变换都对应了一个初等矩阵 $E$，于是有 $E_s E_{s-1}\dots E_1 A=R$，即 $A=E_1^{-1} \dots E_s^{-1} R=ER$。

如果 $A_{l-1}'\ne 0$，令 $k_l$ 为使得 $A_{l-1}'$ 的第 $k$ 列非零的最小整数，取 $(A_{l-1})_{j_l,k_l}\ne 0(j_l\ge l)$，将 $A_{l-1}$ 的第 $j_l$ 行乘以 $\dfrac{1}{(A_{l-1})_{j_l,k_l}}$，然后将变换后的 $j_l$ 行乘以 $-(A_{l-1})_{j,k_l}$ 并加到第 $j$ 行，将这一步重复 $m-1$ 次，最后交换第 $j_l$ 行与第 $l$ 行，即得矩阵 $A_l\overset{r}{\sim} A_{l-1}\overset{r}{\sim} A$。

上述过程一定会停止，因为 $k_l$ 是严格递增的，而 $k_l\le n$。于是我们证明了与 $A$ 行等价的RREF $R$ 的存在性。

下面我们来证唯一性。设有RREF $R$ 和 $R'$ 行等价于 $A$，首先我们考虑 $R$ 和 $R'$ 的主元列。

对于RREF的一列 $v$，它是一个RREF的主元列当且仅当 $v$ 不是在它前面的列的线性组合，同时我们又知道 $R\overset{r}{\sim}A\overset{r}{\sim} R'$，以及行变换不改变列之间的线性关系，因此 $R$ 与 $R'$ 的主元列位置相同，而且主元列的元素相同（由于RREF的定义），因此 $R$ 与 $R'$ 的主元列相同。

现在考虑非主元列，不妨设为第 $k$ 列，这一列可以表示为主元列的线性组合（因为行秩等于列秩，从而主元列是 $A$ 的列张成的空间的一个基），又有行变换不改变列的线性关系，因此这一线性组合对于 $R$ 和 $R'$ 都相同，从而 $R$ 和 $R'$ 的第 $k$ 列相同。综上所述，$R=R'$，即 $A$ 的RREF是唯一的。

Gauss消元法有多种形式，其中最常用的一种是**前向消元&回代**。

具体来说，给定秩为 $r$ 的一个矩阵 $A$，我们先通过交换两行将 $r$ 个主元移动到前 $r$ 行，然后对主元下方的元素进行消元，最终可以得到一个行阶梯形矩阵 $U$。从 $A$ 到 $U$ 的过程就称为**前向消元**。

而**回代**则关注于线性方程 $Ax=b$，通过消元法可以化成 $Ux=c$，从中可以解出 $x_{j_r}$，然后代回原方程可以解出 $x_{j_{r-1}}$，以此类推，其中 $j_1,\dots,j_r$ 是主元列，最终我们可以得到方程的完整解集。

从定理12.1.3我们还可以导出一个重要的矩阵分解：

**定理 12.1.4** 满秩分解

设矩阵 $A_{m\times n}$ 的秩为 $r$，则有列满秩矩阵 $C_{m\times r}$ 与行满秩矩阵 $R_{r\times n}$ 满足 $A=CR$

**证明**

我们已经知道 $A$ 的主元列是 $A$ 的列张成的空间的一个基，将主元列放在一起构成一个矩阵 $C$，则显然 $C$ 是列满秩的。然后我们把 $A$ 的RREF中的非零行（也就是前 $r$ 行）放在一起构成矩阵 $R$，显然 $R$ 是行满秩的。

现在我们考虑分解 $A=ER_0$，根据矩阵的乘法，我们知道 $E$ 的前 $r$ 列就是 $A$ 的主元列，又知道 $R_0$ 的后 $m-r$ 行全为0，于是就有

$$
ER_0=\begin{bmatrix} C & E_1\end{bmatrix}
\begin{bmatrix}
R \\ 0
\end{bmatrix}=CR
$$

上述的满秩分解也可以写成 $r$ 个秩为1的矩阵之和，具体来说，设 $C$ 的列为 $u_1,\dots,u_r$，$R$ 的行为 $v_1^T,\dots,v_r^T$，则有

$$
A=CR=u_1 v_1^T+\dots+u_r v_r^T
$$

# Section 2: 相似形与矩阵分解

我们在第五章最后简要说明了在不同基下同一线性算子的矩阵有何关联，这里我们做一些回顾。

设 $A=\mathcal M(T,(v_1,\dots,v_n))$，$B=\mathcal M(T,(w_1,\dots,w_n))$，我们令 $P=\mathcal M(I,(w_1,\dots,w_n),(v_1,\dots,v_n))$，则 $P$ 的第 $k$ 列为

$$
Iw_k=w_k=c_{1k}v_1+\dots+c_{nk}v_n
$$

中的系数 $c_{1k},\dots,c_{nk}$。且 $P^{-1}=\mathcal M(I,(v_1,\dots,v_n),(w_1,\dots,w_n))$。

于是我们有

$$
A=PBP^{-1}
$$

本节中定理的证明几乎都是按照以上模板展开的，其中 $v_1,\dots,v_n$ 通常取为标准基，而 $w_1,\dots,w_n$ 则通常取为特征向量，此时就有相似对角化 $A=P\Lambda P^{-1}$。

**定理 12.2.1**

设 $A_{n\times n}$ 可对角化，则存在可逆矩阵 $P$ 和对角矩阵 $\Lambda$ 满足 $A=P\Lambda P^{-1}$

这对应了定理5.3.7。

**定理 12.2.2**

设 $A_{n\times n}$ 是复矩阵，则存在可逆矩阵 $P$ 和Jordan形矩阵 $J$ 使得 $A=PJP^{-1}$，并且Jordan形除了各Jordan块的前后排序外是唯一确定的。

**证明**

存在性的证明对应定理6.2.3，现在我们来证唯一性。

我们有广义特征分解 $V=G_{\lambda_1}\oplus\dots\oplus G_{\lambda_m}$，且算子 $(T-\lambda_j I)|_{G_{\lambda_j}}$ 是幂零的，设为 $N$。

参考定理6.2.1，数

$$
c_k=\dim\ker N^k - \dim\ker N^{k-1}
$$

确定了 $G_{\lambda_j}$ 部分阶数至少为 $k$ 的Jordan块的数量，从而

$$
b_k=c_k-c_{k+1}
$$

确定了 $G_{\lambda_j}$ 部分阶数为 $k$ 的Jordan块的数量。因此Jordan块的结构是由 $N$ 的核空间维数唯一确定的，从而Jordan形除了Jordan块的排序外是唯一确定的。

现在我们将视线转向内积空间，如果不做特殊说明，那么总是取Euclidean内积 $\langle u,v\rangle=u^T \overline{v}=v^H u$。

以下的分解对应了Gram-Schmidt过程。

**定理 12.2.3** $QR$ 分解

设 $A_{m\times n}$ 是列满秩的，则存在各列规范正交的矩阵 $Q_{m\times n}$ 与上三角可逆矩阵 $R_{n\times n}$ 使得 $A=QR$。进一步，如果 $m=n$，则 $Q$ 是一个酉矩阵（或正交矩阵）。

**证明**

设 $A$ 的列为 $v_1,\dots,v_n$，对其应用Gram-Schmidt过程，得到 $e_1=\dfrac{v_1}{\|v_1\|}$，且

$$
e_j=\dfrac{v_j-\langle v_j,e_1\rangle e_1-\dots-\langle v_j,e_{j-1}\rangle e_{j-1}}{\|v_j-\langle v_j,e_1\rangle e_1-\dots-\langle v_j,e_{j-1}\rangle e_{j-1}\|}
$$

于是有 $v_1=\|v_1\|e_1$，和

$$
\begin{align*}
v_j & = \langle v_j,e_1\rangle e_1+\dots+\langle v_j,e_{j-1}\rangle e_{j-1}\\
&+\|v_j-\langle v_j,e_1\rangle e_1-\dots-\langle v_j,e_{j-1}\rangle e_{j-1}\| e_j
\end{align*}
$$

令 $e_1,\dots,e_n$ 构成 $Q$ 的列，则上式中各 $e_k$ 的系数构成了 $R$ 的第 $j$ 列。由于 $v_1,\dots,v_n$ 线性无关，则 $v_j-\langle v_j,e_1\rangle e_1-\dots-\langle v_j,e_{j-1}\rangle e_{j-1}\ne 0$，从而 $R$ 是上三角可逆矩阵。

当 $m=n$ 时，$e_1,\dots,e_n$ 是一个规范正交基，于是有 $Q^H Q=I$，这就完成了证明。

当 $A$ 的列线性相关时，同样可以做 $QR$ 分解，只不过此时 $R$ 是不可逆的行阶梯形矩阵，具体做法如下：

设 $v_1,\dots,v_n$ 是 $A$ 的列，设 $j_1$ 是使 $v_j\ne 0$ 的最小整数，取 $e_{j_1}=\dfrac{v_{j_1}}{\|v_{j_1}\|}$。

现假设已有 $e_{j_1},\dots,e_{j_{k-1}}$，设 $j_k$ 是使 $e_{j_1},\dots,e_{j_{k-1}},v_j(j>j_{k-1})$ 线性无关的最小整数，取

$$
e_{j_k}=\dfrac{v_{j_k}-\langle v_{j_k},e_{j_1}\rangle e_{j_1}-\dots-\langle v_{j_k},e_{j_{k-1}}\rangle e_{j_{k-1}}}{\|v_{j_k}-\langle v_{j_k},e_{j_1}\rangle e_{j_1}-\dots-\langle v_{j_k},e_{j_{k-1}}\rangle e_{j_{k-1}}\|}
$$

于是得到了一个最大规范正交组 $e_{j_1},\dots,e_{j_r}$，在这些列，$R$ 的元素可以直接从上面的公式中得到，就像在定理12.2.3中一样。

而对于其它的列，它们或者是0，或者是前面列的线性组合。在后者的情况中，假设这列是第 $j$ 列，其中 $j_{k}<j<j_{k+1}$，则有

$$
v_j=\langle v_j,e_{j_1}\rangle e_{j_1}+\dots+\langle v_j,e_{j_k}\rangle e_{j_k}
$$

现在我们构造出了行阶梯形矩阵 $R$，对于 $Q$，我们对规范正交组 $e_{j_1},\dots,e_{j_r}$ 进行扩充与重编号，得到 $e_1=e_{j_1},\dots,e_r=e_{j_r},e_{r+1},\dots,e_n$，于是就有了各列规范正交的矩阵 $Q$。

下面的定理对应于Schur定理。

**定理 12.2.4** Schur定理

设 $A_{n\times n}$ 是复矩阵，则有上三角矩阵 $R$ 和酉矩阵 $U$ 满足 $A=URU^H$

接下来的两个定理均来自谱定理。

**定理 12.2.5** 复谱定理

设 $A_{n\times n}$ 是复正规矩阵，则有对角矩阵 $\Lambda$ 和酉矩阵 $U$ 满足 $A=U\Lambda U^H$。进一步，如果 $A$ 是复Hermitian矩阵，则 $\Lambda$ 是实对角矩阵。

**定理 12.2.6** 实谱定理

设 $A_{n\times n}$ 是实对称矩阵，则有实对角矩阵 $\Lambda$ 和正交矩阵 $Q$ 满足 $A=Q\Lambda Q^T$

本节的最后一个定理来自极分解。

**定理 12.2.7** 极分解

给定矩阵 $A_{n\times n}$，则有酉矩阵（或正交矩阵）$Q$ 使得 $A=Q\sqrt{A^H A}$

从上面的定理可以导出 $n\times n$ 矩阵的SVD，而对于一般的 $m\times n$ 矩阵的SVD，我们将在之后研究。

矩阵相似对角化的一个重要应用场景是解线性递推方程，以Fibonacci数列为例，我们有

$$
F_{n+2}=F_{n+1}+F_{n},F_0=0,F_1=1
$$

我们可以做如下构造：

$$
\begin{bmatrix} F_{n+2} \\ F_{n+1} \end{bmatrix}=
\begin{bmatrix} 1 & 1 \\ 1 & 0 \end{bmatrix}
\begin{bmatrix} F_{n+1} \\ F_{n} \end{bmatrix}=
A\begin{bmatrix} F_{n+1} \\ F_{n} \end{bmatrix}
$$

于是我们有

$$
\begin{bmatrix} F_{n+1} \\ F_{n} \end{bmatrix}=A^n 
\begin{bmatrix} F_{1} \\ F_{0} \end{bmatrix}
$$

我们对 $A$ 做相似对角化，则有

$$
A=\begin{bmatrix} \phi_+ & \phi_- \\ 1 & 1 \end{bmatrix}
\begin{bmatrix} \phi_+ & \\ & \phi_- \end{bmatrix}
\begin{bmatrix} \phi_+ & \phi_- \\ 1 & 1 \end{bmatrix}^{-1}=
P\Lambda P^{-1}
$$

其中 $\phi_+=\dfrac{1+\sqrt 5}{2},\phi_-=\dfrac{1-\sqrt 5}{2}$，从而

$$
A^n=(P\Lambda P^{-1})^n=P\Lambda^n P^{-1}
$$

则 $F_n=\dfrac{\phi_+^n-\phi_-^n}{\sqrt 5}$。

一般来说，一个 $k$ 阶的常系数齐次线性递推方程可以转化成一个 $k$ 阶矩阵的对角化问题。

对角化的另一个应用是二次型的标准化。我们以实二次型为例，一个二次型形如

$$
f(x)=\sum_{1\le i,j\le n} A_{ij} x_i x_j=x^T Ax
$$

其中 $A$ 是对称矩阵。我们的目标是通过变量替换除去 $f(x)$ 中的交叉项 $x_i x_j(i\ne j)$，这时候的矩阵 $A$ 就变成了对角矩阵 $\Lambda$。因此，这一标准化过程纯粹就是谱定理的应用，具体过程如下：

由于 $A$ 是对称矩阵，从而存在正交矩阵 $Q$ 使得 $A=Q\Lambda Q^T$，于是有

$$
f(x)=x^T Q\Lambda Q^T x=(Q^T x)^T \Lambda Q^T x
$$

令 $y=Q^T x$，则原二次型化为 $y^T\Lambda y$，并且，由于 $A$ 的特征值是唯一确定的，从而 $\Lambda$ 是唯一确定的，由此我们知道二次型 $f(x)$ 的标准形是唯一确定的（除了平方项前的系数外）。这一定理称为**惯性定理**。

# Section 3: 行列式

在第四章我们已推导了一些关于矩阵行列式的性质，这里补充介绍一个求解变量较少的线性方程组的方法。

**定理 12.3.1** Cramer法则

设 $A_{n\times n}$ 是可逆的，则线性方程组 $Ax=b,x=(x_1,\dots,x_n)$ 的解为

$$
x_j=\dfrac{\det B_j}{\det A}
$$

其中 $B_j$ 是将 $A$ 的第 $j$ 列替换为 $b$ 得到的矩阵。

**证明**

我们已知道 $A^{-1}=\dfrac{1}{\det A}A^*$，则 $x=\dfrac{1}{\det A}A^* b$，从而

$$
x_j=\dfrac{1}{\det A}(b_1 C_{1j}+\dots+b_n C_{nj})=\dfrac{\det B_j}{\det A}
$$

行列式也可以用于判断矩阵的正定性，从而避免了特征值的计算。

**定理 12.3.2** Sylvester准则

设 $A_{n\times n}$ 是复Hermitian矩阵，且所有顺序主子式（从左上角开始的 $k\times k$ 阶子矩阵的行列式）都大于零，则 $A$ 是正定矩阵。反之也成立。

首先我们给出两个引理：

**定理 12.3.3**

设 $v_1,\dots,v_n$ 是 $V$ 的基，$W$ 是 $V$ 的 $k$ 维子空间，如果 $m<k$，那么存在 $w\in W,w\ne 0$ 使得 $w\in\mathrm{span}(v_{m+1},\dots,v_n)$

**证明**

设 $W$ 的基为 $w_1,\dots,w_k$，假设定理不成立，那么 $w_1,\dots,w_k,v_{m+1},\dots,v_n$ 就是 $V$ 的一个基，这与 $\dim V=n$ 矛盾。

**定理 12.3.4**

设 $A_{n\times n}$ 是一个复Hermitian矩阵，$W$ 是一个 $k$ 维子空间使得对任意 $w\in W,w\ne 0$ 有 $w^H Aw>0$，那么 $A$ 至少有 $k$ 个正特征值。

**证明**

根据谱定理，有特征向量构成的规范正交基 $e_1,\dots,e_n$，假设只有前 $m(m<k)$ 个特征值是正的，那么我们有

$$
w=a_{m+1}e_{m+1}+\dots+a_ne_n
$$

从而

$$
\begin{gather*}
w^H Aw =\langle a_{m+1}\lambda_{m+1}e_{m+1}+\dots+a_n\lambda_n e_n,a_{m+1}e_{m+1}+\dots+a_n e_n \rangle\\
=\lambda_{m+1}|a_{m+1}|^2+\dots+\lambda_n |a_n|^2\le 0
\end{gather*}
$$

这与条件矛盾，从而完成了证明。

下面我们给出Sylvester准则的证明。

**证明（定理12.3.2）**

我们将使用归纳法。当 $n=1$ 时结论显然成立。

假设结论对于 $n-1$ 成立，设左上角开始的 $(n-1)\times (n-1)$ 阶子矩阵为 $A_{n-1}$，从而 $A_{n-1}$ 是正定的。

令 $W=\{(w_1,\dots,w_{n-1},0)\colon w_j\in \mathbb C\}$，取 $w\in W,w\ne 0$，则有

$$
w^H Aw=\hat{w}^H A_{n-1} \hat{w}>0
$$

其中 $\hat{w}=(w_1,\dots,w_{n-1})$，于是 $A$ 至少有 $n-1$ 个正特征值。$A$ 的 $n$ 阶子式就是 $\det A=\lambda_1 \dots \lambda_n>0$，从而 $\lambda_n>0$，这就是说 $A$ 是正定的。

现假设 $A$ 是正定的，取 $w=(w_1,\dots,w_k,0,\dots,0)$，则有

$$
w^H Aw=\hat{w}^H A_k \hat{w}>0
$$

从而 $A_k$ 是正定的，于是 $\det A_k>0$，这就完成了证明。

从上述定理也可以导出一个重要的分解：**Cholesky分解**。

**定理 12.3.5** Cholesky分解

设 $A_{n\times n}$ 是正定的，则存在唯一的上三角可逆矩阵 $C$ 使得 $A=C^H C$

**证明**

因为 $A$ 是正定的，所以 $A$ 的顺序主子式都大于零，从而对 $A$ 进行前向消元时不需要交换行，从而有下三角矩阵 $L$ 和上三角矩阵 $U_0$ 满足 $A=LU_0$，其中 $U_0$ 的对角线上是 $A$ 的主元（均大于零）。

将 $A$ 的主元从 $U_0$ 中提取出来，则有对角矩阵 $D$ 使得 $A=LDU$，其中 $L$ 和 $U$ 的对角线上均为1。由于 $A^H=A$，则有 $U=L^H$，于是 $A=LDL^H=L\sqrt{D}\sqrt{D}L^H$。

令 $C^H=L\sqrt{D}$，则有 $A=C^H C$。显然 $C$ 是上三角可逆矩阵，而 $L$ 记录了前向消元的过程，$\sqrt{D}$ 中的元素是 $A$ 的主元的平方根，两者都是由 $A$ 唯一确定的，从而 $C$ 也是唯一确定的。

# Section 4: 奇异值分解

在十一章中，我们已给出了 $n\times n$ 矩阵的SVD，现在我们将给出一般的矩阵的SVD，这一分解主要依赖于下面的广义极分解定理。

**定理 12.4.1** 极分解

设 $T\in\mathcal L(V,W)$，则有：

1. 若 $\dim V\le\dim W$，则存在保范数的映射 $S\in\mathcal L(V,W)$ 使得 $T=S\sqrt{T^\dagger T}$
2. 若 $\dim V\ge\dim W$，则存在保范数的映射 $S\in\mathcal L(W,V)$ 使得 $T=\sqrt{T T^\dagger} S^\dagger$

**证明**

设 $\dim V\le\dim W$，仿照定理11.3.1的证明过程，首先我们可以证明

$$
\|Tv\|=\|\sqrt{T^\dagger T}v\|
$$

从而 $S_1\colon \mathrm{im}\ \sqrt{T^\dagger T}\to \mathrm{im}\ T$ 满足

$$
S_1(\sqrt{T^\dagger T}v)=Tv
$$

是良定的线性映射，且保持范数不变。

接下来我们将对 $S_1$ 进行扩张，我们知道 $\dim (\mathrm{im}\ \sqrt{T^\dagger T})^\perp=\dim V-\dim \mathrm{im}\ \sqrt{T^\dagger T}$，$\dim(\mathrm{im}\ T)^\perp=\dim W-\dim \mathrm{im}\ T$，从而 $\dim (\mathrm{im}\ \sqrt{T^\dagger T})^\perp\le \dim(\mathrm{im}\ T)^\perp$。

分别取规范正交基 $e_1,\dots,e_n$ 和 $f_1,\dots,f_m(n\le m)$，定义 $S_2\colon (\mathrm{im}\ \sqrt{T^\dagger T})^\perp \to (\mathrm{im}\ T)^\perp$ 如下：

$$
S_2(a_1e_1+\dots+a_ne_n)=a_1f_1+\dots+a_nf_n
$$

则 $S_2$ 也是保范数的。将 $S_1$ 和 $S_2$ 合起来就得到了保范数的映射 $S$。

现设 $\dim V\ge \dim W$，由于 $T\in\mathcal L(V,W)$，则 $T^\dagger \in\mathcal L(W,V)$。对 $T^\dagger$ 应用1，则有

$$
T^\dagger =S\sqrt{TT^\dagger}
$$

两边取伴随，则有

$$
T=\sqrt{TT^\dagger} S^\dagger
$$

这就完成了证明。

从以上定理我们可以导出 $m\times n$ 矩阵的SVD。

**定理 12.4.2** 奇异值分解（Singular Value Decomposition）

给定 $A_{m\times n}$，则存在酉矩阵 $U_{m\times m}$ 和 $V_{n\times n}$ 以及矩阵 $\Sigma_{m\times n}$ 满足 $A=U\Sigma V^H$，其中 $\Sigma$ 只有对角线 $\Sigma_{j,j}$ 上有非零元。

**证明**

首先我们假设 $m\ge n$，从而我们可以使用定理12.3.1的1，从而有各列规范正交的矩阵 $Q_{m\times n}$ 满足

$$
A=Q\sqrt{A^H A}
$$

由于 $\sqrt{A^H A}$ 是半正定矩阵，应用谱定理，则存在酉矩阵 $V_{n\times n}$ 和对角矩阵 $\Sigma_1$ 使得

$$
\sqrt{A^H A}=V \Sigma_1 V^H
$$

则 $A=QV\Sigma_1 V^H=U_1 \Sigma_1 V^H$，其中 $U_1$ 是 $m\times n$ 矩阵，且各列规范正交。

现在将 $U_1$ 的各列扩充为一个规范正交基，组成酉矩阵 $U_{m\times m}$，并在 $\Sigma_1$ 下方添加 $n-m$ 个零行，则有

$$
U\Sigma V^H=\begin{bmatrix} U_1 & U_2\end{bmatrix}
\begin{bmatrix} \Sigma_1 \\ 0\end{bmatrix}V^H=
U_1 \Sigma_1 V^H=A
$$

对于 $n\ge m$ 的情况，我们可以用同样的方法得到，不同的是，此时有

$$
U\Sigma V^H=U \begin{bmatrix} \Sigma_1 & 0\end{bmatrix}
\begin{bmatrix} V_1^H \\ V_2^H\end{bmatrix}=U\Sigma_1 V_1^H=A
$$

这就完成了证明。

根据上面的定理，我们可以证明 $A^H A$ 和 $AA^H$ 的非零特征值相同，因为

$$
A^H A=V\Sigma^H \Sigma V^H,AA^H=U\Sigma \Sigma^H U^H
$$

而 $\Sigma^H \Sigma$ 与 $\Sigma \Sigma^H$ 的非零值显然相同，从而我们可以定义 $A$ 的**非零奇异值**为 $\sqrt{A^H A}$ 或 $\sqrt{A A^H}$ 的非零特征值。并且我们称 $U$ 的列为 $A$ 的**左奇异向量**，$V$ 的列为 $A$ 的**右奇异向量**。然而，对于 $m\ne n$ 的矩阵 $A_{m\times n}$，没有一种良好的方法来定义 $A$ 的零奇异值。

下面我们来讨论一般矩阵的**伪逆**，定义如下：

**定义 12.4.3** 伪逆（Pseudo-inverse）

给定矩阵 $A_{m\times n}=U\Sigma V^H$，设

$$
\Sigma=\begin{bmatrix} \Sigma_0 & 0 \\ 0 & 0 \end{bmatrix}
$$

其中 $\Sigma_0$ 是 $r\times r$ 的可逆对角矩阵，定义 $A$ 的**伪逆**为 $A^+=V\Sigma^+ U^H$，其中

$$
\Sigma^+ =\begin{bmatrix} \Sigma_0^{-1} & 0 \\ 0 & 0 \end{bmatrix}
$$

从定义可以看出，$\Sigma_0$ 对角线上的是 $A$ 的非零奇异值。

伪逆有如下性质：

**定理 12.4.4**

给定矩阵 $A_{m\times n}$，其伪逆为 $A^+$，则有：

1. $AA^+ A=A$
2. $A^+ AA^+=A^+$
3. $(AA^+)^H=AA^+$
4. $(A^+ A)^H=A^+ A$

反之，根据上面的性质，伪逆 $A^+$ 的形式是唯一确定的。

**证明**

利用SVD，有

$$
AA^+ A=(U\Sigma V^H)(V\Sigma^+ U^H)(U\Sigma V^H)=U\Sigma\Sigma^+ \Sigma V^H=A
$$

同理也可以验证2、3、4。现假设有 $A_1^+,A_2^+$ 满足上述性质，则有

$$
\begin{gather*}
A_1^+=A_1^+ AA_1^+=A_1^+ AA_2^+ AA_1^+=A_1^+(AA_2^+)^H(AA_1^+)^H\\
=A_1^+(AA_1^+AA_2^+)^H=A_1^+(AA_2^+)^H=A_1^+AA_2^+\\
=A_1^+AA_2^+AA_2^+=(A_1^+A)^H(A_2^+A)^H A_2^+=(A_2^+AA_1^+A)^HA_2^+\\
=(A_2^+A)^H A_2^+=A_2^+AA_2^+=A_2^+
\end{gather*}
$$

即满足性质1-4的矩阵 $A^+$ 是唯一确定的。因此这四条性质也可作为伪逆的公理化定义。

上面的定理从代数的角度研究了伪逆的性质，接下来我们从几何的视角来看待它。

**定理 12.4.5**

给定矩阵 $A_{m\times n}$，其伪逆为 $A^+$，则：

1. $A^+ A$ 是到 $A^H$ 的列张成的空间的正交投影
2. $AA^+$ 是到 $A$ 的列张成的空间的正交投影

**证明**

考虑 $A$ 对应的线性映射 $T\colon V\to W$，则有

$$
Tv=s_1 \langle v,e_1\rangle f_1+\dots+s_r \langle v,e_r\rangle f_r
$$

其中 $s_1,\dots,s_r$ 是 $T$ 的非零奇异值，$e_1,\dots,e_n$ 是 $V$ 的规范正交基，$f_1,\dots,f_m$ 是 $W$ 的规范正交基，$r\le m$ 且 $r\le n$。于是

$$
T^+ Tv=\langle v,e_1\rangle e_1+\dots+\langle v,e_r\rangle e_r
$$

由于 $T e_{r+p}=0$，因此 $\ker T=\mathrm{span}(e_{r+1},\dots,e_{n})$，从而 $\mathrm{span}(e_1,\dots,e_r)=(\ker T)^\perp=\mathrm{im}\ T^\dagger$。因此 $T^+ T$ 是到 $\mathrm{im}\ T^\dagger$ 的正交投影，这就是说1成立。

同样我们也有

$$
T^+ v=\dfrac{\langle v,f_1\rangle e_1}{s_1}+\dots+\dfrac{\langle v,f_r\rangle e_r}{s_r}
$$

于是有

$$
TT^+ v=\langle v,f_1\rangle f_1+\dots+\langle v,f_r\rangle f_r
$$

同理我们可以证明2。

现在我们再来看最小二乘法，我们要解决的问题是求 $w$ 使得

$$
L=\|v-Aw\|^2
$$

最小。显然 $Aw$ 在 $A$ 的列张成的空间中，并且我们知道在这个子空间中距离 $v$ 最近的点就是 $v$ 在这个空间上的投影，于是我们有

$$
Aw=AA^+ v
$$

于是 $w=A^+ v$ 就是最小二乘方程的一个特解，并且它也等于我们上一章得到的 $(A^T A)^+ A^T v$，下面我们给出方程的通解。

根据线性方程解的结构，我们只需构造出 $\ker T=(\mathrm{im}\ T^\dagger)^\perp$ 的向量，向 $(\mathrm{im}\ T^\dagger)^\perp$ 的正交投影 $I-T^+ T$ 就可以解决这个问题。于是我们有

$$
w=A^+ v+(I-A^+ A)u
$$

其中 $u$ 是任意向量。

我们还可以证明 $A^+ v$ 与 $(I-A^+ A)u$ 是正交的，从而我们可以定义 $w^+=A^+ v$ 是最小二乘方程的**最优解**，其满足 $\|w^+\|\le \|w\|$。

最后一个应用来自统计学，称为**主成分分析（Principal Component Analysis/PCA）**，具体来说，我们被给予 $n$ 个数据，每个数据有 $m$ 个特征，即每个数据都是 $\mathbb R^m$ 中的向量。一般来说，这些向量不会均匀的分散在 $\mathbb R^m$ 的各处，而是相对集中在某个低维的子空间上。PCA的目标就是找出这个子空间，从而达到数据降维的效果。

PCA的具体流程如下：

首先我们将所有数据组合成一个 $m\times n$ 的矩阵 $A_0$，分别计算 $A_0$ 的各行的平均值 $\mu_1,\dots,\mu_m$，然后令 $A_0$ 的每行都减去对应行的平均值，得到矩阵 $A$，满足 $A$ 的每行的平均值为零。

现在我们考虑 $C=AA^T/(n-1)$，$C_{ij}$ 等于 $A$ 的第 $i$ 行与 $j$ 行的点乘再除以 $n-1$，也就是特征 $i$ 与 $j$ 的**样本协方差**，特别地，$C$ 的对角线上就是特征 $j$ 的**样本方差** $s_j^2$。

设 $A$ 的奇异值为 $\sigma_1\ge \dots\ge \sigma_r>0$，则 $A$ 有SVD

$$
A=U\Sigma V^T=\sigma_1 u_1v_1^T+\dots+\sigma_r u_rv_r^T
$$

且 $\sigma_j^2$ 是 $AA^T$ 的特征值，对应的特征向量为 $u_j$，从而有**总体方差**

$$
s^2=s_1^2+\dots+s_m^2=\sigma_1^2+\dots+\sigma_r^2
$$

从而数据在 $u_1$ 方向上方差最大（可以理解为占总方差的 $\sigma_1^2/s^2$），下面的 $u_2,u_3,\dots$ 方向上方差依次减小。方差越小，数据分布越密集，因此数据主要分布在前 $k$ 个方向张成的空间 $\mathrm{span}(u_1,\dots,u_k)$ 周围，这里的 $u_j$ 就称为**主成分**。利用PCA，我们就可以对数据进行降维、去噪声等操作，同时保留数据的主要信息。

# Section 5: 总结

本章是对前十一章内容的总结以及应用，也是本专栏的最后一章。最后我想谈一谈学习（线性）代数的一些要点。很多人常常在学习向量空间与线性映射时感到吃力，不知道这些概念在讲什么，其实这是正常的，因为“数学是一门我们不知道自己所说的是什么，也不知道所言之物是否为真的学科”。（Bertrand Russell，*Introduction to Mathematical Philosophy*）

换言之，数学只是一种**形式系统**，在这之中只有一些符合某种结构的**字符串**，其中有一些是给定的，称为**公理**，以及**推理规则**——规定了我们如何改变系统中的字符串，除此之外别无他物。这就是说，形式系统中的字符串没有固有的意义（不知道自己所说的是什么），并且我们只是根据规则进行推导，而不涉及经验的事实（不知道所言之物是否为真）。这就是数学中我们称之为“结构”与“形式”的部分。

而数学中我们称为“意义”的部分，就是对形式系统的一种**解释**。一旦我们人为地对系统中的字符串赋予了意义，我们就划定了我们研究的对象的范围。如果一种对象符合系统中的公理以及推理规则，那么在这种解释下所有公理的推论（称为**定理**）就自动成为了真命题。

我们以一个例子来说明这一点。向量空间的公理（见第一章）明确了一个集合成为向量空间的条件，然而，抛弃一切直观与经验来看，这只不过是一些符号串而已，从中推导出的结果（例如 $0v=0$）也没有任何意义——它们只是符号。而只有明确了具体对象（比如 $v$ 取为 $n$ 维列向量），这些符号才有了意义与真值。

近代数学最重要的特征就是“结构”与“意义”的分离，这样做的好处就是可以将结构相同的对象纳入同一个框架中去考虑，而且如果在数学的一个分支中遇到了另一个分支中的结构，那么我们可以立即迁移到另一个系统上，运用另一个系统内的定理解决问题，于是数学的各部分就可以有机地结合在一起，形成一个整体。一些例子比如群表示论（群论+线性代数）、代数拓扑（群论+拓扑）、解析数论（复分析+数论）等等。

但是有一点我们要明确：那就是“意义”，也就是形式系统的解释，是随时可以抛弃的东西。有时候把向量看成有序组是方便的，但有时把向量看成箭头或者一个点是自然的。“意义”对于我们来说只是一种直观，是用来引导我们进行定理推导的，而对于形式系统的结构没有任何影响。对这种“意义”之间的滑动的不习惯使得很多人在脱离了具体的矩阵、列向量等对象，进入抽象数学后感到吃力和无法理解。而认识到“结构”与“意义”的分离就是理解抽象数学的第一步。

以上就是本章的全部内容了，感谢观看！