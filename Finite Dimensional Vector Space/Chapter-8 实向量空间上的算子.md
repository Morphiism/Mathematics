[[Chapter-6 复向量空间上的算子]]

前面我们已经了解了复向量空间上算子的结构与性质，本章中我们将关注实向量空间上的算子。数学家Jacques Hadamard曾说过：“**在实数域中，连接两个真理的最短路径是通过复数域。**” 因此，我们将利用复向量空间上算子的结果来推导实算子的性质。

# Section 1: 复化

就如同实数嵌入复数一般，我们马上就会看到，一个实向量空间可以自然地嵌入到一个复向量空间内，从而实算子可以扩张为一个复算子，于是我们就能利用复向量空间的理论发展实向量空间的理论。

我们先来定义向量空间的复化。

**定义 8.1.1** 复化（Complexification）

设 $V$ 是实向量空间，定义 $V$ 的**复化**为

$$
V_{\mathbb C}=\{u+iv\colon u,v\in V\}
$$

定义 $V_{\mathbb C}$ 上的加法和数乘为

$$
\begin{gather*}
(u_1+iv_1)+(u_2+iv_2)=(u_1+u_2)+i(v_1+v_2)\\
(a+bi)(u+iv)=(au-bv)+i(av+bu)
\end{gather*}
$$

其中 $a,b\in\mathbb R,u_i,v_i\in V$。

我们可以验证，在给定的加法和数乘下，$V_{\mathbb C}$ 是一个复向量空间，其中加法单位元是 $0=0+i0$。

下面我们来推导关于复化空间的基本性质。

**定理 8.1.2**

设 $V$ 是实向量空间，$v_1,\dots,v_m\in V$，则有

1. 向量组 $v_1,\dots,v_m$ 在 $V$ 中线性无关当且仅当它在 $V_{\mathbb C}$ 中线性无关
2. 向量组 $v_1,\dots,v_m$ 张成 $V$ 当且仅当它张成 $V_{\mathbb C}$
3. 向量组 $v_1,\dots,v_m$ 是 $V$ 的基当且仅当它是 $V_{\mathbb C}$ 的基

**证明**

设 $v_1,\dots,v_m$ 在 $V$ 中线性无关，则对于 $a_1,\dots,a_m\in\mathbb R$ 有

$$
a_1v_1+\dots+a_mv_m=0\Longrightarrow a_1=\dots=a_m=0
$$

现设 $c_1,\dots,c_m\in\mathbb C$，且 $c_1v_1+\dots+c_mv_m=0$，则

$$
(\mathrm{Re}\ c_1)v_1+\dots+(\mathrm{Re}\ c_m)v_m=0,(\mathrm{Im}\ c_1)v_1+\dots+(\mathrm{Im}\ c_m)v_m=0
$$

这表明各 $c_j$ 的实部和虚部都为0，即 $c_j=0$，即向量组线性无关。另一个方向的蕴含是显然的。这就证明了1。

设 $V=\mathrm{span}(v_1,\dots,v_m)$，则在 $V_{\mathbb C}$ 中 $\mathrm{span}(v_1,\dots,v_m)$ 包含了向量 $v_1,\dots,v_m,iv_1,\dots,iv_m$，因此 $v_1,\dots,v_m$ 张成 $V_{\mathbb C}$。同样，另一个方向的蕴含是显然的。这就证明了2。

由1和2我们立即得到了3。

由上面的定理，我们还能知道，$V$（作为实向量空间）的维数等于 $V_{\mathbb C}$（作为复向量空间）的维数。

下面我们来定义算子的复化。

**定义 8.1.3** 复化（Complexification）

设 $V$ 是实向量空间，$T\in\mathcal L(V)$，则 $T$ 的**复化**定义为复算子 $T_{\mathbb C}\in\mathcal L(V_{\mathbb C})$ 满足

$$
T_{\mathbb C}(u+iv)=Tu+iTv
$$

其中 $u,v\in V$。

读者可以验证 $T_{\mathbb C}$ 的确是 $V_{\mathbb C}$ 上的线性算子。

对于 $v\in V$，我们有 $T_{\mathbb C}v=Tv$，回顾矩阵的定义（第一章），我们有：

**定理 8.1.4**

设 $v_1,\dots,v_n$ 是 $V$ 的基，$T\in\mathcal L(V)$，则在这个基下有 $\mathcal M(T_{\mathbb C})=\mathcal M(T)$

# Section 2: 特征分解

在第五章我们讲到，实算子不一定有特征值，这是因为多项式在实数上不一定有零点，从而实算子没有一维不变子空间。然而，我们可以证明，一维或二维的不变子空间总是存在的。

**定理 8.2.1**

非零有限维向量空间上的算子有一维或二维不变子空间。

**证明**

对于复向量空间，每个算子都有特征值，从而有一维不变子空间。

因此，设 $V$ 是实向量空间，$T\in\mathcal L(V)$，其复化 $T_{\mathbb C}$ 有特征值 $a+bi$，于是有 $u+iv\ne 0$ 使得

$$
T_{\mathbb C}(u+iv)=(a+bi)(u+iv)=(au-bv)+i(av+bu)
$$

则 $Tu=au-bv,Tv=av+bu$。设 $U=\mathrm{span}(u,v)$，则 $U$ 是一维或二维的，且在 $T$ 下不变。

接下来我们考虑算子的特征值，特征向量及其相关的性质。首先我们介绍如何通过复化的特征值求实算子的特征值。

**定理 8.2.2**

设 $V$ 是实向量空间，$T\in\mathcal L(V)$，则 $T_{\mathbb C}$ 的实特征值都是 $T$ 的特征值。

**证明**

设 $\lambda$ 是 $T_{\mathbb C}$ 的实特征值，则有 $u+iv\ne 0$ 使得

$$
T_{\mathbb C}(u+iv)=\lambda(u+iv)=\lambda u+i \lambda v
$$

从而 $Tu=\lambda u,Tv=\lambda v$，因为 $u\ne 0$ 或 $v\ne 0$，故 $\lambda$ 是 $T$ 的特征值。

另一方面，设 $\lambda$ 是 $T$ 的特征值，则有 $Tv=\lambda v$，于是 $T_{\mathbb C}v=\lambda v$，即 $\lambda$ 是 $T_{\mathbb C}$ 的实特征值。这就完成了证明。

我们知道，对于一个实系数多项式 $p(z)=a_0+a_1z+\dots+a_mz^m$，如果它有一个复零点 $\lambda$，则它的共轭复数 $\overline\lambda$ 也是它的零点，表现出一种对称性。同样，我们也会看到，复化的复特征值与其共轭也有这种对称性。

**定理 8.2.3**

设 $V$ 是实向量空间，$T\in\mathcal L(V)$，$\lambda\in\mathbb C,j$ 是非负整数，$u,v\in V$，则

$$
(T_{\mathbb C}-\lambda I)^j (u+iv)=0 \text{当且仅当} (T_{\mathbb C}-\overline\lambda I)^j (u-iv)=0
$$

**证明**

我们对 $j$ 进行归纳。当 $j=0$ 时显然成立。现设结论对 $j-1$ 成立。

设 $(T_{\mathbb C}-\lambda I)^j (u+iv)=0$，则 

$$
(T_{\mathbb C}-\lambda I)^{j-1}(T_{\mathbb C}-\lambda I) (u+iv)=0
$$

设 $\lambda=a+bi,a,b\in\mathbb R$，则

$$
(T_{\mathbb C}-\lambda I) (u+iv)=(Tu-au+bv)+i(Tv-av-bu)
$$

根据归纳假设，我们有

$$
(T_{\mathbb C}-\overline\lambda I)^{j-1} ((Tu-au+bv)-i(Tv-av-bu))
=(T_{\mathbb C}-\overline\lambda I)^j (u-iv)=0
$$

这就证明了一个方面，同理，我们可以证明另一方向的蕴含。于是完成了证明。

由这个定理我们可以得到两个推论：

**定理 8.2.4**

设 $V$ 是实向量空间，$T\in\mathcal L(V)$，$\lambda\in\mathbb C$，则

1. $\lambda$ 是 $T_{\mathbb C}$ 的特征值当且仅当 $\overline\lambda$ 是 $T_{\mathbb C}$ 的特征值
2. $\lambda$ 作为 $T_{\mathbb C}$ 的特征值的重数等于 $\overline\lambda$ 的重数

**证明**

在定理8.2.3中取 $j=1$ 即可证明1。

设 $u_1+iv_1,\dots,u_m+iv_m$ 是 $G_{\lambda}(T_{\mathbb C})$ 的基，则 $u_1-iv_1,\dots,u_m-iv_m$ 就是 $G_{\overline\lambda}(T_{\mathbb C})$ 的基，从而 $\dim G_{\lambda}=\dim G_{\overline\lambda}$，即证。

下面的定理是“奇数次多项式在实数域上有零点”的推论，但我们也可以使用复化来证明它。

**定理 8.2.5**

奇数维实向量空间上的算子有特征值。

**证明**

考虑奇数维实向量空间 $V$ 上的一个算子 $T$，因为 $T_{\mathbb C}$ 的非实特征值是成对出现的，且重数相同，所以非实特征值的重数之和为偶数。然而，$T_{\mathbb C}$ 的所有特征值重数之和为 $\dim V_{\mathbb C}=\dim V$，故 $T_{\mathbb C}$ 一定有实特征值，从而 $T$ 一定有特征值。

我们在复向量空间中证明的一个中心结果是定理6.1.10，我们想要知道，在什么情况下，对于实向量空间上的算子也有该结论成立？下面的定理给出了一个充要条件。

**定理 8.2.6**

设 $V$ 是有限维非零实向量空间，$T\in\mathcal L(V)$，则 $V$ 有 $T$ 的广义特征向量构成的基当且仅当 $T_{\mathbb C}$ 的特征值都是实的。

**证明**

设 $T_{\mathbb C}$ 的特征值都是实的，$n=\dim V$，于是 $T$ 有全部 $n$ 个特征值，设 $\lambda_1,\dots,\lambda_m$ 是不同的特征值。我们要证 $V=G_{\lambda_1}\oplus\dots\oplus G_{\lambda_m}$

接下来我们仿照定理6.1.10的证明，对 $n$ 进行归纳。当 $n=1$ 时结论显然成立。现假设结论对于维数小于 $n$ 的空间都成立，我们可以这样假设是因为 $T$ 的特征值足够多，从而后续我们对子空间 $U$ 应用归纳假设时不会出现 $U$ 没有特征值来继续分解的情况。

下面的证明过程与定理6.1.10完全相同，可以点击下方链接回顾：

最终我们可以证明 $V$ 有直和分解 $V=G_{\lambda_1}\oplus\dots\oplus G_{\lambda_m}$，从每一项中取出一个基放在一起，就得到了 $V$ 的一个基。

另一方面，设 $V$ 有广义特征向量构成的基 $v_1,\dots,v_n$，并设 $T_{\mathbb C}$ 的不同特征值为 $\lambda_1,\dots,\lambda_m$，则有 $(T_{\mathbb C}-\lambda_j I)^n v_k=0$，取其共轭，则有 $(T_{\mathbb C}-\overline\lambda_j I)^n v_k=0$，这表明 $v_k\in G_{\lambda_j}(T_{\mathbb C})\cap G_{\overline\lambda_j}(T_{\mathbb C})$。

然而广义特征空间是直和项，因此 $\lambda_j=\overline\lambda_j$（否则 $v_k$ 将等于0），从而 $\lambda_j\in\mathbb R$，即证。

回顾一下，定理6.2.1在复向量空间和实向量空间上都成立，因此，我们可以证明，如果 $T_{\mathbb C}$ 的特征值都是实的，那么 $T$ 就有Jordan形。

# Section 3: 特征多项式与极小多项式

接下来我们讨论实算子的特征多项式，下面的定理是定义的关键：

**定理 8.3.1**

设 $V$ 是实向量空间，$T\in\mathcal L(V)$，则 $\Delta_{T_{\mathbb C}}$ 的系数都是实数。

**证明**

由于 $T_{\mathbb C}$ 的非实特征值成对出现且重数相同，则其特征多项式中的因式具有以下两种类型：

$$
(z-r_k)^{c_k},(z-\lambda_j)^{d_j}(z-\overline\lambda_j)^{d_j}
$$

其中 $r_k\in\mathbb R,\lambda_j\in\mathbb C\setminus \mathbb R$。而后者为 $(z^2-2(\mathrm{Re}\ \lambda_j)z+|\lambda_j|^2)^{d_j}$，因此所有因子的系数都是实的，从而 $\Delta_{T_{\mathbb C}}$ 的系数都是实的。

既然 $\Delta_{T_{\mathbb C}}$ 是实系数多项式，那么我们就可以定义 $T$ 的特征多项式为其复化的特征多项式。

**定义 8.3.2** 特征多项式（Characteristic Polynomial）

设 $V$ 是实向量空间，$T\in\mathcal L(V)$，则 $T$ 的**特征多项式**定义为 $\Delta_T=\Delta_{T_{\mathbb C}}$

与复向量空间类似，我们可以推导出特征多项式的一些性质。

**定理 8.3.3**

设 $V$ 是有限维实向量空间，$T\in\mathcal L(V)$，则

1. $\deg \Delta_T=\dim V$
2. $\Delta_T$ 的所有实零点都是 $T$ 的特征值

**证明**

由定义立即得到1。同样根据定义，$\Delta_T$ 的所有实零点都是 $T_{\mathbb C}$ 的实特征值，也是 $T$ 的特征值。

**定理 8.3.4** Cayley-Hamilton定理

设 $T\in\mathcal L(V)$，则 $\Delta_T(T)=0$

**证明**

我们已对复向量空间做了证明。设 $V$ 是实向量空间，由定义得到 $\Delta_T(T_{\mathbb C})=0$，对于任意 $v\in V$，我们有 $\Delta_T(T_{\mathbb C})v=\Delta_T(T)v=0$，因此 $\Delta_T(T)=0$。

下面我们讨论极小多项式，我们不必重复定义极小多项式，因为定义6.3.5没有限制在复向量空间上。类比特征多项式，我们可以证明 $T$ 的极小多项式等于其复化的极小多项式。

**定理 8.3.5**

设 $V$ 是实向量空间，$T\in\mathcal L(V)$，则 $m_T=m_{T_{\mathbb C}}$

**证明**

对于任意 $j$，我们有 $(T_{\mathbb C})^j (u+iv)=T^j u+i T^j v$，因此对于多项式 $p$ 有 $p(T_{\mathbb C})=(p(T))_{\mathbb C}$，则 $m_T(T_{\mathbb C})=(m_T(T))_{\mathbb C}=0$。

设首一多项式 $p$ 满足 $p(T_{\mathbb C})=0$，设 $p(z)=c_0+c_1z+\dots+c_{m-1}z^{m-1}+z^m$，令多项式 $r$ 为

$$
r(z)=(\mathrm{Re}\ c_0)+(\mathrm{Re}\ c_1)z+\dots+(\mathrm{Re}\ c_{m-1})z^{m-1}+z^m
$$

于是 $r(T)=0$，则 $\deg p=\deg r\ge \deg m_T$。这表明 $m_T$ 是 $T_{\mathbb C}$ 的极小多项式。

类似地，定理6.3.6没有限制在复向量空间上，因此有如下定理成立：

**定理 8.3.6**

设 $V$ 是有限维的，$T\in\mathcal L(V)$，则

1. $m_T$ 整除 $\Delta_T$
2. $\deg m_T\le \dim V$

**证明**

由Cayley-Hamilton定理立即得到1。由 $\deg\Delta_T=\dim V$ 和整除性得到2。

这一定理给我们对极小多项式次数的估计带来了很大改进（从 $(\dim V)^2$ 到 $\dim V$）。

# Section 4: 迹与行列式

下面我们来定义实算子的迹与行列式。

**定义 8.4.1** 迹（Trace）

设 $V$ 是实向量空间，$T\in\mathcal L(V)$，则 $T$ 的**迹**定义为 $\mathrm{Tr}\ T=\mathrm{Tr}\ T_{\mathbb C}$

**定义 8.4.2** 行列式（Determinant）

设 $V$ 是实向量空间，$T\in\mathcal L(V)$，则 $T$ 的**行列式**定义为 $\det T=\det T_{\mathbb C}$

由于 $T_{\mathbb C}$ 的非实特征值是成对出现的，且重数相等，因此上面的定义是良定的。

于是，根据复算子的性质，我们就可以立即得到实算子的迹与行列式的性质。这也就是说，第七章中的所有定理都对实算子成立（一些证明需要做一点平凡的改动）。

# Section 5: 总结

本章我们借助复向量空间上的算子研究了实向量空间上的算子。下一章，我们将引入**内积**，这是长度、角度等度量性质在向量空间中的抽象，我们还将讨论内积空间上的算子。

本章内容就是这样，感谢观看！