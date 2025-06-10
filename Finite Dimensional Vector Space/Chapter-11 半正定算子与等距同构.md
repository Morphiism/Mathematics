[[Chapter-10 Hermite算子与正规算子]]

上一章我们对Hermite算子与正规算子做了一个刻画，本章我们将研究两类特殊的算子：**半正定算子**与**等距同构**。将它们统一起来的是**极分解定理**，它表明每个算子都可分解成一个等距同构与一个半正定算子的乘积。

# Section 1: 半正定算子

**定义 11.1.1** 半正定的（Positive Semi-definite），正定的（Positive Definite）

算子 $T\in\mathcal L(V)$ 称为**半正定的**，如果 $T$ 是Hermite算子且 $\langle Tv,v\rangle\ge 0$。如果进一步，有 $\langle Tv,v\rangle>0$ 对任意 $v\ne 0$，则称 $T$ 是**正定的**。

如果 $V$ 是复内积空间，则 $T$ 是Hermite算子的条件可以去掉（由于定理10.1.9）。

我们可以类似地定义**半负定**和**负定**。如果 $T$ 是（半）负定的，我们可以证明 $-T$ 是（半）正定的，因此在本章中我们将只研究（半）正定算子。

我们之前提到，Hermite算子在复内积空间中相当于复数域中的实数，那么这里的半正定算子就可以对应于非负数，而正定算子就可以对应于正数。我们知道一个复数 $z$ 是非负数当且仅当 $z$ 有非负的平方根，我们想知道对于半正定算子是否有同样的结论。下面的定理给出了答案。

**定义 11.1.2** 平方根（Square Root）

算子 $R$ 称为算子 $T\in\mathcal L(V)$ 的**平方根**，如果 $R^2=T$。

**定理 11.1.3**

设 $T\in\mathcal L(V)$，则以下条件等价：

1. $T$ 是半正定的
2. $T$ 是Hermite算子且所有特征值非负
3. $T$ 有半正定的平方根
4. $T$ 有Hermite平方根
5. 存在 $R\in\mathcal L(V)$ 使得 $T=R^\dagger R$

**证明**

我们将证明 $1\to 2\to 3\to 4\to 5\to 1$。

假设1成立，则 $T$ 是Hermite算子，应用谱定理，则有规范正交基 $e_1,\dots,e_n$ 使 $T$ 的矩阵为对角矩阵。设 $Te_j=\lambda_j e_j$，则 $\langle Te_j,e_j\rangle=\lambda_j\ge 0$，即得2。

假设2成立，应用谱定理，同理有 $Te_j=\lambda_j e_j$，定义 $Re_j=\sqrt{\lambda_j} e_j$。设 $v=a_1 e_1+\dots+a_n e_n$，则

$$
\langle Rv,v\rangle=\sqrt{\lambda_1}|a_1|^2+\dots+\sqrt{\lambda_n}|a_n|^2\ge 0
$$

显然 $R$ 是Hermite算子，$R^2=T$，即得3成立。

$3\to 4$ 是显然的。

假设4成立，则有Hermite算子 $R$ 使 $T=R^2$，因为 $R=R^\dagger$，故 $T=R^\dagger R$。则5成立。

假设5成立，则 $T^\dagger=R^\dagger R=T$，且 $\langle R^\dagger Rv,v\rangle=\langle Rv,Rv\rangle\ge 0$，即1成立。这就完成了证明。

对于正定算子，我们可以从上面的证明中知道，$T$ 是正定的当且仅当 $T$ 是Hermite算子且所有特征值都是正的，从而 $T$ 是可逆的。这给出了正定算子的一个刻画：

**定理 11.1.4**

设 $T\in\mathcal L(V)$，则以下条件等价：

1. $T$ 是正定的
2. $T$ 是Hermite算子且所有特征值都是正的
3. $T$ 是半正定算子且 $T$ 可逆
4. $T$ 有正定的平方根

**证明**

我们将证明 $1\leftrightarrow 2,2\leftrightarrow 3,2\to 4\to 1$。

应用谱定理，则有规范正交基 $e_1,\dots,e_n$ 使得 $Te_j=\lambda_j e_j$，于是

$$
\langle Te_j,e_j\rangle=\lambda_j,\langle Tv,v\rangle=\lambda_1 |a_1|^2+\dots+\lambda_n |a_n|^2
$$

从而我们有 $1\leftrightarrow 2$。

$2\to 3$ 是显然的。假设3成立，根据定理11.1.3，$T$ 是Hermite算子且所有特征值非负，由于 $T$ 可逆，因此0不是 $T$ 的特征值（否则就有 $v\ne 0,Tv=0$）。因此 $T$ 的特征值都是正的。

$2\to 4$ 也是显然的（取 $Re_j=\sqrt{\lambda_j}e_j$ 即可）。假设4成立，则有正定算子 $R$ 使得 $T=R^2$，则 $\langle R^2v,v\rangle=\langle Rv,Rv\rangle$。我们已证明了 $1\to 3$，于是 $R$ 可逆，从而 $Rv\ne 0$ 对于 $v\ne 0$，从而 $T$ 是正定的。这就完成了证明。

下面的定理进一步强化了半正定算子与非负数的这个类比。

**定理 11.1.5**

$V$ 上每个半正定算子都有唯一的半正定平方根。

**证明**

设 $T\in\mathcal L(V)$ 是半正定的，$\lambda$ 是 $T$ 的特征值，$v$ 是对应的特征向量，则 $Tv=\lambda v$。设 $R$ 是 $T$ 的半正定平方根，我们要证明 $Rv=\sqrt{\lambda} v$，从而 $R$ 在 $T$ 的特征向量上是唯一确定的，又 $V=E_{\lambda_1}\oplus\dots\oplus E_{\lambda_m}$，从而 $R$ 在 $V$ 上就是唯一确定的。

根据谱定理，有一个规范正交基 $e_1,\dots,e_n$ 使得 $Te_j=\lambda_j e_j$，则 $Re_j=\sqrt{\lambda_j}e_j$，从而 

$$
Rv=a_1\sqrt{\lambda_1}e_1+\dots+a_n\sqrt{\lambda_n}e_n
$$

由于 $v$ 是特征向量，则有

$$
v=\sum_{\lambda_j=\lambda} a_j e_j
$$

于是

$$
Rv=\sum_{\lambda_j=\lambda} a_j\sqrt{\lambda_j} e_j=\sqrt{\lambda}\sum_{\lambda_j=\lambda} a_j e_j=\sqrt{\lambda} v
$$

即证。

既然半正定平方根是唯一的，我们就可以用 $\sqrt{T}$ 来表示它。

# Section 2: 等距同构

**定义 11.2.1** 等距同构（Isometry），正交算子（Orthogonal Operator），酉算子（Unitary Operator）

算子 $S\in\mathcal L(V)$ 称为**等距同构**，如果对任意 $v\in V$ 有 $\|Sv\|=\|v\|$。

实内积空间上的等距同构称为**正交算子**，复内积空间上的等距同构称为**酉算子**。

换句话说，算子是等距同构当且仅当它保持范数不变。

在给出等距同构的等价条件之前，我们先证明一个引理：

**定理 11.2.2**

设 $S,T\in\mathcal L(V)$，则 $TS=I$ 当且仅当 $ST=I$

**证明**

设 $TS=I$，则对任意 $v\in V$ 有 $T(Sv)=v$，从而 $T$ 是满射，于是 $T$ 可逆，于是 $S=T^{-1}$ 也可逆，且 $S^{-1}=T$，即 $ST=I$。反之同理。

**定理 11.2.3**

设 $S\in\mathcal L(V)$，则以下条件等价：

1. $S$ 是等距同构
2. $\langle Su,Sv\rangle=\langle u,v\rangle$
3. 对 $V$ 中的任意规范正交组 $e_1,\dots,e_m$，$Se_1,\dots,Se_m$ 是规范正交的
4. $V$ 有规范正交基 $e_1,\dots,e_n$ 使 $Se_1,\dots,Se_n$ 是规范正交的
5. $S^\dagger S=SS^\dagger =I$
6. $S$ 可逆且 $S^{-1}=S^\dagger$
7. $S^\dagger$ 是等距同构

**证明**

我们将证明 $1\to 2\to 3\to 4\to 5\to 6\to 7\to 1$。

假设1成立，我们已知用范数来计算内积的方法（极化恒等式），由于 $S$ 保持范数不变，则 $S$ 也保持内积不变，即 $\langle Su,Sv\rangle=\langle u,v\rangle$。

现设2成立，则 $\langle Se_j,Se_k\rangle=\langle e_j,e_k\rangle=\delta_{jk}$，从而 $Se_1,\dots,Se_m$ 是规范正交的。

$3\to 4$ 是显然的。

现设4成立。因为 $e_1,\dots,e_n$ 和 $Se_1,\dots,Se_n$ 都是规范正交基，所以

$$
\langle Se_j,Se_k\rangle=\delta_{jk}=\langle e_j,e_k\rangle
$$

由于每个 $v\in V$ 都可以用 $e_1,\dots,e_n$ 表示，故上面的等式表明

$$
\langle Su,Sv\rangle=\langle u,v\rangle=\langle S^\dagger Su,v\rangle
$$

对任意 $u,v$ 成立，从而 $S^\dagger S=I$。这就证明了5。

$5\to 6$ 也是显然的。

设6成立，则 

$$
\|S^\dagger v\|^2=\langle S^\dagger v,S^\dagger v\rangle=\langle SS^\dagger v,v\rangle=\|v\|^2
$$

即 $S^\dagger$ 是等距同构。

设7成立，我们已经有 $1\to 5$，因此 $SS^\dagger=S^\dagger S=I$，从而 $S^\dagger$ 是正规的，根据定理10.1.12，我们就有 $\|S^\dagger v\|=\|Sv\|=\|v\|$。这就完成了证明。

在上述定理中，1与4的等价性表明，$S$ 是等距同构当且仅当在某个规范正交基下 $S$ 的矩阵的列是规范正交的，再由1和7的等价性表明，上述结论中的“列”可以换成“行”。

此外，上面的定理表明等距同构是正规算子，因此我们可以使用正规算子的刻画方法来描述等距同构。我们将分成复和实两种情况讨论。

**定理 11.2.4**

设 $V$ 是有限维非零复内积空间，$S\in\mathcal L(V)$，则以下条件等价：

1. $S$ 是等距同构
2. $V$ 有一个 $S$ 的特征向量构成的规范正交基，且对应的特征值的绝对值都为1

**证明**

先设1成立，应用复谱定理，则 $V$ 有一个规范正交基 $e_1,\dots,e_n$ 满足 $Se_j=\lambda_j e_j$，则有

$$
|\lambda_j|=\|Se_j\|=\|e_j\|=1
$$

从而有 $1\to 2$。

再设2成立，则有

$$
v=\langle v,e_1\rangle e_1+\dots+\langle v,e_n\rangle e_n
$$

且

$$
\|Sv\|^2=|\lambda_1|^2 |\langle v,e_1\rangle|^2+\dots+|\lambda_n|^2 |\langle v,e_n\rangle|^2=\|v\|^2
$$

从而 $S$ 是等距同构。这就完成了证明。

下面我们要证明实的情形，这里我们将使用定理10.2.7。

**定理 11.2.5**

设 $V$ 是有限维非零实内积空间，$S\in\mathcal L(V)$，则以下条件等价：

1. $S$ 是等距同构
2. $S$ 关于 $V$ 的某个规范正交基有分块对角矩阵，每个块都是 $1\times 1$ 的矩阵 $(\pm 1)$ 或者形如

$$
\begin{pmatrix}
\cos\theta & -\sin\theta \\
\sin\theta & \cos\theta
\end{pmatrix}
$$

的 $2\times 2$ 矩阵，其中 $\theta\in (0,\pi)$。

**证明**

先设1成立，则 $V$ 有规范正交基 $e_1,\dots,e_n$ 使得 $S$ 在这个基下有分块对角矩阵，每个块都是 $1\times 1$ 的矩阵 $(\lambda)$，或者形如

$$
\begin{pmatrix}
a & -b \\
b & a
\end{pmatrix}
$$

的 $2\times 2$ 矩阵，其中 $b>0$。

对于 $1\times 1$ 矩阵 $(\lambda)$，有 $e_k$ 满足 $Se_k=\lambda e_k$，由 $\|Se_k\|=\|e_k\|$ 得 $|\lambda|=1$，即 $\lambda=1$ 或 $\lambda=-1$。

对于 $2\times 2$ 矩阵，有 $e_j,e_{j+1}$ 使得 $Se_j=ae_j+be_{j+1}$，则有

$$
\|Se_j\|^2=a^2+b^2=\|e_j\|^2=1
$$

再由 $b>0$ 得 $a=\cos\theta,b=\sin\theta$ 对于 $\theta\in (0,\pi)$。这就证明了2。

现设2成立，则 $V$ 有直和分解

$$
V=U_1\oplus\dots\oplus U_m
$$

其中每个 $U_j$ 都是 $V$ 的一维或二维不变子空间，根据分块情况而定。进一步，属于不同的 $U_j$ 的向量是正交的，且每个 $S|_{U_j}$ 都是等距同构，从而

$$
\|Sv\|^2=\|Su_1\|^2+\dots+\|Su_m\|^2=\|u_1\|^2+\dots+\|u_m\|^2=\|v\|^2
$$

于是有 $2\to 1$。这就完成了证明。

上面的定理表明，实内积空间上的等距同构（正交算子）由三部分构成：恒等算子（对应于乘1的部分），关于某个超平面的反射（对应于乘-1的部分），二维子空间上的旋转（对应于 $2\times 2$ 的矩阵）。

> 可以验证，$n$ 维内积空间上的等距同构关于映射的复合运算构成了一个**群**，在实内积空间上，这个群就是 $O(n)$，在复内积空间上，这个群是 $U(n)$。在这两个群中满足 $\det S=1$ 的元素可以构成子群，分别记为 $SO(n)$ 和 $SU(n)$（S表示Special），它们在粒子物理中非常重要：$SO(3)$ 描述了三维空间上的纯旋转，而 $SU(3)$ 是描述夸克之间强相互作用的标准模型的一部分。

# Section 3: 极分解与奇异值分解

回想一下，我们把复内积空间上的Hermite算子类比成实数，而半正定算子则类比为非负数。那么等距同构对应什么呢？根据定理11.2.3，我们知道等距同构 $S$ 满足 $S^\dagger S=I$，这对应了复数 $z$ 满足 $\overline{z}z=|z|^2=1$，这表明等距同构对应于单位圆上的点。

每个复数 $z$ 都有极坐标形式：$z=re^{i\theta}$，其中 $r\ge 0,|e^{i\theta}|=1$。根据我们的类比，这暗示了每个算子都可以写成一个等距同构与一个半正定算子的乘积。为进一步确定算子的形式，我们继续研究复数：

$$
z=|z|\cdot \dfrac{z}{|z|}=\dfrac{z}{|z|}\sqrt{\overline{z}z}
$$

这就启发我们给出下面的定理：

**定理 11.3.1** 极分解

设 $T\in\mathcal L(V)$，则存在等距同构 $S\in\mathcal L(V)$ 使得 $T=S\sqrt{T^\dagger T}$

**证明**

设 $v\in V$，由于 $T^\dagger T$ 是半正定算子，则

$$
\|Tv\|^2=\langle Tv,Tv\rangle=\langle T^\dagger Tv,v\rangle=\langle \sqrt{T^\dagger T}^2 v,v\rangle=\|\sqrt{T^\dagger T}v\|^2
$$

从而 $\ker T=\ker \sqrt{T^\dagger T}$，即 $\dim\mathrm{im}\ T=\dim\mathrm{im}\ \sqrt{T^\dagger T}$，定义 $S_1\colon \mathrm{im}\ \sqrt{T^\dagger T}\to \mathrm{im}\ T$ 为

$$
S_1 (\sqrt{T^\dagger T}v)=Tv
$$

我们首先证明 $S_1$ 是良定的。设 $\sqrt{T^\dagger T}v_1=\sqrt{T^\dagger T}v_2$，则

$$
\|Tv_1-Tv_2\|=\|T(v_1-v_2)\|=\|\sqrt{T^\dagger T}(v_1-v_2)\|=0
$$

即 $Tv_1=Tv_2$，故 $S_1$ 是良定的。显然 $S_1$ 是线性映射。

接下来我们要把 $S_1$ 扩展为 $V$ 上的等距同构。

由于 $\dim (\mathrm{im}\ T)^\perp=\dim (\mathrm{im}\ \sqrt{T^\dagger T})^\perp$，分别取两个规范正交基 $e_1,\dots,e_m$ 和 $f_1,\dots,f_m$，定义 $S_2\colon (\mathrm{im}\ \sqrt{T^\dagger T})^\perp\to (\mathrm{im}\ T)^\perp$ 为

$$
S_2 (a_1 e_1+\dots+a_m e_m)=a_1 f_1+\dots+a_m f_m
$$

从而 $\|S_2 w\|=\|w\|$。

现在令 $S$ 分别在 $\mathrm{im}\ \sqrt{T^\dagger T}$ 和 $(\mathrm{im}\ \sqrt{T^\dagger T})^\perp$ 等于 $S_1$ 和 $S_2$，设 $v\in V$，则 $v$ 可以唯一地分解成

$$
v=u+w,u\in \mathrm{im}\ \sqrt{T^\dagger T},w\in (\mathrm{im}\ \sqrt{T^\dagger T})^\perp
$$

从而

$$
\|Sv\|^2=\|S_1 u\|^2+\|S_2 w\|^2=\|u\|^2+\|w\|^2=\|v\|^2
$$

故 $S$ 是等距同构。

在极分解 $T=S\sqrt{T^\dagger T}$ 中，$\sqrt{T^\dagger T}$ 是半正定算子，因此我们可以应用谱定理，取一个规范正交基使其对角化。然而，等距同构 $S$ 在这个基下不一定是对角矩阵，因此，我们实际需要两个，而不是一个规范正交基，来描述算子 $T$。这就是下面定理的主要内容：

**定理 11.3.2** 奇异值分解（Singular Value Decomposition/SVD）

设 $T\in\mathcal L(V)$，则有非负数 $s_1,\dots,s_n$ 和规范正交基 $e_1,\dots,e_n$ 与 $f_1,\dots,f_n$ 使得对任意 $v\in V$ 有

$$
Tv=s_1\langle v,e_1\rangle f_1+\dots+s_n\langle v,e_n\rangle f_n
$$

**证明**

$T$ 有极分解 $T=S\sqrt{T^\dagger T}$，对 $\sqrt{T^\dagger T}$ 应用谱定理，则有规范正交基 $e_1,\dots,e_n$ 使 $\sqrt{T^\dagger T}$ 有对角矩阵，令 $s_1,\dots,s_n$ 为 $\sqrt{T^\dagger T}$ 的特征值，则由定理11.1.3得 $s_j\ge 0$，从而

$$
S\sqrt{T^\dagger T}v=s_1\langle v,e_1\rangle Se_1+\dots+s_n\langle v,e_n\rangle Se_n
$$

由定理11.2.3知，$Se_1,\dots,Se_n$ 是规范正交的，令 $f_j=Se_j$，则 $f_1,\dots,f_n$ 是规范正交基，这就证明了定理。

这里的非负数 $s_1,\dots,s_n$ 就称为 $T$ 的**奇异值**。

**定义 11.3.3** 奇异值（Singular Value）

设 $T\in\mathcal L(V)$，则 $T$ 的**奇异值**就是 $\sqrt{T^\dagger T}$ 的特征值，每个特征值 $\lambda$ 重复 $\dim E_{\lambda}(\sqrt{T^\dagger T})$ 次。

下面的定理给出了一种计算奇异值的方法。

**定理 11.3.4**

设 $T\in\mathcal L(V)$，则 $T$ 的**奇异值**就是 $T^\dagger T$ 的特征值的正平方根，每个特征值 $\lambda$ 重复 $\dim E_{\lambda}(T^\dagger T)$ 次。

**证明**

谱定理表明有规范正交基 $e_1,\dots,e_n$ 使得 $T^\dagger Te_j=\lambda_j e_j$，则 $\sqrt{T^\dagger T}e_j=\sqrt{\lambda_j}e_j$，这就得到了要证的结论。

我们在研究 $V\to W$ 的线性映射时，需要取定 $V$ 和 $W$ 的两个基，而在我们研究算子 $V\to V$ 时，我们通常总是让 $V$ 的同一个基扮演这两个角色。

奇异值分解则给了我们一个机会：对算子的研究使用两个不同的基。奇异值分解表明，只要允许我们使用两个不同的基，那么每个算子都关于 $V$ 的规范正交基有对角矩阵。具体来说，设 $T$ 有定理11.3.2所表示的分解，则

$$
\mathcal M(T,(e_1,\dots,e_n),(f_1,\dots,f_n))=\mathrm{diag}(s_1,\dots,s_n)=\Sigma
$$

设 $v_1,\dots,v_n$ 是 $V$ 的任意规范正交基，$A=\mathcal M(T,(v_1,\dots,v_n))$，$U=\mathcal M(I,(f_1,\dots,f_n),(v_1,\dots,v_n))$，$V=\mathcal M(I,(e_1,\dots,e_n),(v_1,\dots,v_n))$，则

$$
A=U\Sigma V^{-1}=U\Sigma V^H
$$

下面我们给出与 $T$ 相关的一些算子的奇异值分解。

**定理 11.3.5**

设 $T\in\mathcal L(V)$ 有奇异值分解

$$
Tv=s_1\langle v,e_1\rangle f_1+\dots+s_n\langle v,e_n\rangle f_n
$$

则有：

1. $T^\dagger v=s_1\langle v,f_1\rangle e_1+\dots+s_n\langle v,f_n\rangle e_n$
2. $T^\dagger Tv=s_1^2 \langle v,e_1\rangle e_1+\dots+s_n^2 \langle v,e_n\rangle e_n$
3. $TT^\dagger v=s_1^2 \langle v,f_1\rangle f_1+\dots+s_n^2 \langle v,f_n\rangle f_n$
4. 如果 $T$ 可逆，则

$$
T^{-1}v=\dfrac{\langle v,f_1\rangle e_1}{s_1}+\dots+\dfrac{\langle v,f_n\rangle e_n}{s_n}
$$

**证明**

设 $v,w\in V$，则

$$
\begin{gather*}
\langle Tv,w\rangle=s_1\langle v,e_1\rangle\langle f_1,w\rangle+\dots+s_n\langle v,e_n\rangle\langle f_n,w\rangle\\
=\langle v,s_1\langle w,f_1\rangle e_1+\dots+s_n\langle w,f_n\rangle e_n\rangle=\langle v,T^\dagger w\rangle
\end{gather*}
$$

从而 $T^\dagger w=s_1\langle w,f_1\rangle e_1+\dots+s_n\langle w,f_n\rangle e_n$。这就证明了1。

利用 $T$ 和 $T^\dagger$ 的奇异值分解，就可以证明2和3。

假设 $T$ 可逆，则 $\langle T^\dagger Tv,v\rangle=\langle Tv,Tv\rangle>0$ 对于 $v\ne 0$，从而 $T^\dagger T$ 是正定的，故 $T$ 的奇异值都是正数。

设 $Sv=\dfrac{\langle v,f_1\rangle e_1}{s_1}+\dots+\dfrac{\langle v,f_n\rangle e_n}{s_n}$，则 $STv=TSv=v$，从而有 $S=T^{-1}$，于是完成了证明。

以上定理表明，$T$ 和 $T^\dagger$ 有相同的奇异值，并且 $T$ 可逆当且仅当 $T$ 的奇异值非零。

受上面定理的4的启发，我们可以对所有算子定义一种较弱的逆元，称为**伪逆**，定义如下：

**定义 11.3.6** 伪逆（Pseudo-inverse）

设 $T\in\mathcal L(V)$，$T$ 的非零奇异值为 $s_1,\dots,s_m$，则 $T$ 的**伪逆** $T^+$ 定义为

$$
T^+ v=\dfrac{\langle v,f_1\rangle e_1}{s_1}+\dots+\dfrac{\langle v,f_m\rangle e_m}{s_m}
$$

显然，当 $T$ 可逆时，$T^+=T^{-1}$。

对于矩阵 $A$ 来说，其伪逆就等于 $A^+=V\Sigma^+ U^H$，其中 $\Sigma^+=\mathrm{diag}(s_1^{-1},\dots,s_m^{-1},0,\dots,0)$。因此，对于任意最小二乘方程

$$
A^T Aw=A^T v
$$

我们都可以得到一个合理的解 $w=(A^T A)^+ A^T v$。

一个算子 $T$ 不一定有特征值，但是它一定有奇异值，根据下面的定理，这给了我们对向量的范数进行估计的方法。

**定理 11.3.7**

设 $T\in\mathcal L(V)$，$\hat s$ 是 $T$ 的最小奇异值，$s$ 是 $T$ 的最大奇异值，则对任意 $v\in V$ 有 $\hat{s}\|v\|\le \|Tv\|\le s\|v\|$，且两边的等号均可以取到。

**证明**

不妨设 $T$ 的奇异值满足 $\hat s=s_1\le \dots \le s_n=s$，则

$$
Tv=s_1\langle v,e_1\rangle f_1+\dots+s_n\langle v,e_n\rangle f_n
$$

于是

$$
\|Tv\|^2=s_1^2 |\langle v,e_1\rangle|^2+\dots+s_n^2 |\langle v,e_n\rangle|^2
$$

从而 $\hat{s}^2 \|v\|^2\le \|Tv\|^2\le s^2\|v\|^2$。

取 $v=\|v\|e_1$ 即得 $\|Tv\|=\hat s \|v\|$，取 $v=\|v\|e_n$ 即得 $\|Tv\|=s\|v\|$。这就完成了证明。

从上述定理立即得到：如果 $\lambda$ 是 $T$ 的特征值，则 $\hat s\le |\lambda|\le s$。

通过奇异值，我们还可以为 $\mathcal L(V)$ 定义范数如下：

**定义 11.3.8** 范数（Norm）

设 $T\in\mathcal L(V)$，则 $T$ 的**范数**定义为 $T$ 的最大奇异值，即

$$
\|T\|=s=\max_{\|v\|=1}\|Tv\|
$$

下面的定理表明算子范数的确是一个范数。

**定理 11.3.9** 三角不等式

设 $S,T\in\mathcal L(V)$，则 $\|S+T\|\le \|S\|+\|T\|$

**证明**

设 $v\in V,\|v\|=1$，则由向量的三角不等式有

$$
\|(S+T)v\|\le \|Sv\|+\|Tv\|\le \|S\|+\|T\|
$$

从而

$$
\max_{\|v\|=1}\|(S+T)v\|\le \|S\|+\|T\|
$$

即 $\|S+T\|\le \|S\|+\|T\|$。

# Section 4: 分析与行列式

在第四章与第七章介绍行列式时，我们都提到了，行列式反映了图形拉伸或收缩的比例，但这一断言还未得到证明。然而，一个严格的证明不可能被给出，除非我们已完全明确了什么是“长度”，“面积”，“体积”等概念。这也就是说，我们要定义**测度**。

然而，严格定义测度对于理解线性代数没有帮助，而且也超出了笔者的能力范围。因此，我们将只关注直观的“测度”概念，而不给出严格的可测定义。我们只是声明：这一节的所有关于测度的直观命题都可通过适当的调整转化为严格且正确的分析学定理。

我们先证明两个引理：

**定理 11.4.1**

设 $S\in\mathcal L(V)$ 是等距同构，则 $|\det S|=1$

**证明**

对于复向量空间有 $|\det S|=|\lambda_1|\dots|\lambda_n|=1$。

对于实向量空间，我们可以证明 $S$ 的复化 $S_{\mathbb C}$ 也是等距同构，从而 $|\det S|=|\det S_{\mathbb C}|=1$。

**定理 11.4.2**

设 $T\in\mathcal L(V)$，则 $|\det T|=\det \sqrt{T^\dagger T}$

**证明**

根据极分解定理，有 $T=S\sqrt{T^\dagger T}$，则

$$
|\det T|=|\det S|\det \sqrt{T^\dagger T}=\det \sqrt{T^\dagger T}
$$

在实内积空间上，由于 $\det\sqrt{T^\dagger T}\ge 0$，故 $\det T$ 的正负只取决于 $\det S$ 的正负。然而，根据定理11.2.5，$\det S$ 的正负完全取决于分块对角矩阵中有多少个 $1\times 1$ 矩阵 $(-1)$，取决于 $S$ 使整个空间反射了多少次。这就是为什么我们把行列式称为“有向面积/体积”。

下面我们将讨论 $\mathbb R^n$ 上的测度，首先从最显然的子集开始。

**定义 11.4.3** 开盒子（Open Box），体积（Volume）

$\mathbb R^n$ 上的**开盒子**是集合

$$
B=\{(y_1,\dots,y_n)\in\mathbb R^n\colon x_j < y_j < x_j+r_j,r_j>0\}
$$

定义开盒子的**体积**为 $V(B)=r_1\dots r_n$。

接下来我们可以对任意可测集（直观来说就是可以定义合理的测度的集合）定义测度：

**定义 11.4.4** 测度（Measure）

设 $\Omega\subset \mathbb R^n$ 是可测的，则定义其**测度**为

$$
\mu(\Omega)=\inf\left(\sum_{i} V(B_i)\right)
$$

其中 $\Omega\subset \bigcup_{i} B_i$（也称 $\{B_i\}$ **覆盖** $\Omega$）。

下面我们考虑算子对测度的影响。

**定理 11.4.5**

设 $S\in\mathcal L(\mathbb R^n)$ 是等距同构，$\Omega\subset\mathbb R^n$ 是可测的，则 $\mu(S(\Omega))=\mu(\Omega)$

**证明**

正交算子可以分成三部分：恒等，反射，旋转。这三者均不改变开盒子的体积，而测度是由开盒子的体积逼近的，因此等距同构不改变测度。

**定理 11.4.6**

设 $T\in\mathcal L(\mathbb R^n)$ 是半正定算子，$\Omega\subset\mathbb R^n$ 是可测的，则 $\mu(T(\Omega))=(\det T)\mu(\Omega)$

**证明**

根据谱定理，有规范正交基 $e_1,\dots,e_n$ 使得 $Te_j=\lambda_j e_j$。我们先考虑 $e_1,\dots,e_n$ 是标准基的情况，于是有

$$
T(x_1,\dots,x_n)=(\lambda_1 x_1,\dots,\lambda_n x_n)
$$

对于开盒子 $B=(x_1,x_1+r_1)\times \dots \times(x_n,x_n+r_n)$，有

$$
V(T(B))=\lambda_1 r_1 \dots \lambda_n r_n=(\det T)V(B)
$$

从而

$$
\mu(T(\Omega))=(\det T)\mu(\Omega)
$$

如果 $e_1,\dots,e_n$ 不是标准基，那么我们可以利用等距同构 $S$ 来转换基：

$$
T_1=S^\dagger TS
$$

其中 $S$ 将第 $j$ 个标准基映到 $e_j$。由于等距同构不改变测度，于是有

$$
\mu(T(\Omega))=\mu(T_1(\Omega))=(\det T)\mu(\Omega)
$$

这就完成了证明。

结合以上两个定理，我们就可以描述任意算子对测度的作用。

**定理 11.4.7**

设 $T\in\mathcal L(\mathbb R^n)$，$\Omega\subset\mathbb R^n$ 是可测的，则 $\mu(T(\Omega))=|\det T|\mu(\Omega)$

**证明**

根据极分解定理，有 $T=S\sqrt{T^\dagger T}$，则

$$
\mu(T(\Omega))=(\det \sqrt{T^\dagger T})\mu(\Omega)=|\det T|\mu(\Omega)
$$

上面的定理表明，算子将测度改变了 $|\det T|$ 倍，从而证明了我们最初的断言。

行列式的一个非常重要的应用出现在重积分的换元中，这里我们将做简单介绍。首先我们介绍所谓的**简单函数**。

**定义 11.4.8** 简单函数（Simple Function）

设 $\Omega\subset \mathbb R^n$ 是可测的，称 $f\colon \Omega\to \mathbb R$ 是**简单函数**，如果对任意 $x\in\Omega$，有 $f(x)\in\{a_1,\dots,a_n\}$。

简单函数的一个重要性质是它们能够分解成几个不相交的可测集上的常值函数，即

$$
f(x)=\sum_{j=1}^{n} a_j \chi_{E_j}(x)
$$

其中 $\chi_{E_j}(x)=1$ 如果 $x\in E_j$，反之则为0。各 $E_j$ 是可测集且互不相交。

下面我们就可以定义**积分**了，我们将从简单 $\to$ 非负可测 $\to$ 绝对可积的顺序依次定义积分。

**定义 11.4.9** 积分（Integral）

设 $\Omega\subset \mathbb R^n$ 是可测集，$f\colon \Omega\to \mathbb R$，则定义 $f$ 的**积分**如下：

1. 若 $f$ 是非负简单函数，则定义

$$
\int_\Omega f=\sum_{j=1}^{n} a_j \mu(E_j)
$$

2. 若 $f$ 是非负可测的，则定义

$$
\int_\Omega f=\sup\left\{ \int_\Omega s \colon s\text{是非负简单函数且对} x\in\Omega \text{有} f(x)\ge s(x) \right\}
$$

3. 若 $f$ 是绝对可积的，则定义

$$
\int_\Omega f=\int_\Omega f^+ - \int_\Omega f^-
$$

其中 $f^+(x)=\max(f(x),0),f^-(x)=-\min(f(x),0)$。

上面的积分定义通常被称为Lebesgue积分，与Riemann积分相对。直观上看，Lebesgue积分就是将函数的值域进行划分，然后用简单函数来近似它，最后，随着这一划分越来越精细，简单函数的积分就越趋近于函数的积分。

下面我们给出**可微**的定义。

**定义 11.4.10** 可微（Differentiable），导数（Derivative）

设 $\Omega$ 是 $\mathbb R^n$ 的开子集，$\sigma\colon \Omega\to \mathbb R^n$，对于 $x\in\Omega$，称 $\sigma$ 在 $x$ 点**可微**，如果有 $T\in\mathcal L(\mathbb R^n)$ 使得

$$
\sigma(x+h)=\sigma(x)+Th+o(\|h\|)
$$

如果 $\sigma$ 在 $x$ 点可微，则称唯一满足可微条件的算子 $T\in\mathcal L(\mathbb R^n)$ 为 $\sigma$ 在 $x$ 的**导数**，记作 $\sigma'(x)$。

根据可微的定义，我们知道，如果 $\sigma$ 在 $x$ 可微，则在 $x$ 附近的一个小邻域内，$\sigma$ 的行为基本上就是一个线性算子，从而在那个邻域内，测度变换了 $|\det \sigma'(x)|$。

记 $x=(x_1,\dots,x_n),\sigma(x)=(\sigma_1(x),\dots,\sigma_n(x))$，则可以证明 $\sigma'(x)$ 在标准基下的矩阵为

$$
J_\sigma(x)=
\begin{pmatrix}
\dfrac{\partial \sigma_1}{\partial x_1} & \dots & \dfrac{\partial \sigma_1}{\partial x_n} \\
\vdots & & \vdots \\
\dfrac{\partial \sigma_n}{\partial x_1} & \dots & \dfrac{\partial \sigma_n}{\partial x_n}
\end{pmatrix}
$$

这一矩阵也称为Jacobi矩阵。

现在我们可以给出重积分换元公式，其中 $y=\sigma(x)$ 可以看成一个变量替换。

**定理 11.4.11** 积分的变量替换

设 $\Omega$ 是 $\mathbb R^n$ 的开子集，$\sigma\colon \Omega\to \mathbb R^n$ 在 $\Omega$ 上可微，$f\colon \Omega\to \mathbb R$ 是绝对可积的，则

$$
\int_{\sigma(\Omega)} f(y)dy=\int_\Omega f(\sigma(x))|\det \sigma'(x)|dx
$$

我们不给出上述定理的证明，因为它涉及了太多的技术细节。相反，我们将给出在证明过程中所用到的一些直观图景。

根据积分的定义，我们知道 $f$ 可以被简单函数逼近。取一个小区域 $\Gamma$ 使得 $f$ 在 $\sigma(\Gamma)$ 上几乎为常值函数 $f(\sigma(x))$，于是这个区域上的积分近似为

$$
f(\sigma(x))\mu(\sigma(\Gamma))
$$

由于 $\sigma$ 可微，则 $\sigma$ 在 $\Gamma$ 上几乎是一个线性算子 $\sigma'(x)$，于是有

$$
\mu(\sigma(\Gamma))=|\det \sigma'(x)|\mu(\Gamma)
$$

将 $\Gamma$ 取的越来越精细并求和，就得到了想要的结果。我们可以看到，这里行列式的出现是自然的。

# Section 5: 总结

线性代数的基础内容：有限维向量空间到这里就介绍完了。回顾一下，第一章我们介绍了向量空间与线性映射的基本定义，第二章我们主要研究了线性方程 $Tv=w$ 解的存在性与唯一性，第三章我们介绍了对偶空间，使我们能够从另一个视角来看待线性映射，第四章我们引入了矩阵的行列式，并指出了行列式的本质：对图形的拉伸系数。

从第五章开始，我们主要研究向量空间到自身的线性映射，即线性算子，并研究它能够对角化的条件，以及不可对角化时我们能够做到多好。最后，第九章到第十一章我们在向量空间上引入了内积，这给我们带来了更为丰富的理论，和更广的应用范围。

在下一章，我们将对矩阵部分的内容做一点补充，也是对前十一章的内容做一点总结。本期内容就是这样，感谢观看！