[[Chapter-6 复向量空间上的算子]]

现在我们已经有了特征值和特征向量的工具，我们就可以继续来研究算子的矩阵。在第四章中，我们定义了矩阵的行列式，并令算子的行列式等于它的矩阵的行列式，本章中，我们将给出一个等价的定义。

# Section 1: 行列式

在行列式（上）中，我们讲到，行列式反映了图形在算子的作用下拉伸或收缩的系数，而这个系数与我们的基的选取是无关的。于是，如果我们在复向量空间中取一个特征向量构成的基 $v_1,\dots,v_n$，其张成了一个高维空间中的立方体，而 $T$ 对各 $v_j$ 的作用只是将其拉伸或收缩 $\lambda_j$ 倍，于是 $Tv_1,\dots,Tv_n$ 张成了一个高维长方体，其“体积”为 $\lambda_1 \dots \lambda_n$。受以上讨论启发，我们给出如下定义：

**定义 7.1.1** 行列式（Determinant）

设 $V$ 是复向量空间，$T\in\mathcal L(V),\lambda_1,\dots,\lambda_n$ 是 $T$ 的所有特征值（包含重根），则 $T$ 的**行列式**定义为

$$
\det T=\lambda_1 \dots \lambda_n
$$

关于实向量空间，我们将在以后的章节讨论。

接下来我们需要证明这一定义与我们之前的定义等价。有了前面几章的铺垫，这里的证明就非常简单了。

**定理 7.1.2**

设 $V$ 是复向量空间，$T\in\mathcal L(V)$，则 $\det T=\det \mathcal M(T)$

**证明**

我们已经知道基变换保持矩阵的行列式不变，又知道复向量空间上的算子都可以上三角化（且对角线上是特征值），取一个这样的基，则有 $\det \mathcal M(T)=\lambda_1 \dots \lambda_n =\det T$。

于是我们可以通过矩阵行列式的性质推导出算子行列式的性质。

**定理 7.1.3**

设 $V$ 是复向量空间，$S,T\in\mathcal L(V)$，则 $\det ST=(\det S)(\det T)$

**证明**

任取一个基，则 

$$
\det ST=\det \mathcal M(S)\mathcal M(T)=(\det \mathcal M(S))(\det \mathcal M(T))=(\det S)(\det T)
$$

**定理 7.1.4**

复向量空间上的算子 $T$ 可逆当且仅当 $\det T\ne 0$

**证明**

$T$ 可逆当且仅当 $\ker T = \{0\}$，当且仅当0不是 $T$ 的特征值，当且仅当 $\det T=\lambda_1\dots\lambda_n\ne 0$。

下面我们来研究行列式与特征多项式之间的联系。根据特征多项式的定义，我们可以立即得到：

**定理 7.1.5**

设 $V$ 是 $n$ 维复向量空间，$T\in\mathcal L(V)$，则 $T$ 的特征多项式的常数项为 $(-1)^n \det T$

**证明**

$\Delta_T(z)=(z-\lambda_1)\dots(z-\lambda_n)$，展开并取常数项即证。

一些教材中将下面的结果作为特征多项式的定义，而把我们的定义作为结果：

**定理 7.1.6**

设 $V$ 是有限维复向量空间，$T\in\mathcal L(V)$，则 $\Delta_T(z)=\det(zI-T)$

**证明**

任取一个 $\lambda$，则

$$
-(T-\lambda I)=(zI-T)-(z-\lambda)I
$$

所以 $\lambda$ 是 $T$ 的特征值当且仅当 $z-\lambda$ 是 $zI-T$ 的特征值。设 $T$ 的特征值为 $\lambda_1,\dots,\lambda_n$，则 $zI-T$ 的特征值为 $z-\lambda_1,\dots,z-\lambda_n$，从而

$$
\det(zI-T)=(z-\lambda_1)\dots (z-\lambda_n)=\Delta_T(z)
$$

于是我们得到了一个求算子的特征值的方法：只需取一个基构造矩阵 $A=\mathcal M(T)$，然后解方程 $\det (\lambda I-A)=0$ 即可。

# Section 2: 迹

还有一个与算子的特征值相关的概念是算子的迹，定义如下：

**定义 7.2.1** 迹（Trace）

设 $V$ 是复向量空间，$T\in\mathcal L(V),\lambda_1,\dots,\lambda_n$ 是 $T$ 的所有特征值（包含重根），则 $T$ 的**迹**定义为

$$
\mathrm{Tr}\ T=\lambda_1+\dots+\lambda_n
$$

与行列式相同，我们可以用特征多项式的系数表示迹：

**定理 7.2.2**

设 $V$ 是 $n$ 维复向量空间，$T\in\mathcal L(V)$，则 $T$ 的特征多项式 $z^{n-1}$ 项的系数为 $-\mathrm{Tr}\ T$

**证明**

由 $\Delta_T(z)=(z-\lambda_1)\dots(z-\lambda_n)$ 即证。

将迹与行列式结合，我们可以将 $\Delta_T(z)$ 写为：

$$
\Delta_T(z)=z^n - (\mathrm{Tr}\ T)z^{n-1}+\dots+(-1)^n (\det T)
$$

接下来我们考虑矩阵的迹，它定义为矩阵对角线上元素的和。

**定义 7.2.3** 迹（Trace）

设 $A\in\mathbb F^{n,n}$，则定义 $A$ 的**迹**为

$$
\mathrm{Tr}\ A=A_{11}+A_{22}+\dots+A_{nn}
$$

下面，我们仿照行列式的做法，证明算子的迹等于其矩阵的迹。为此，我们先证明一个引理：

**定理 7.2.4**

设 $A,B\in\mathbb F^{n,n}$，则 $\mathrm{Tr}\ AB=\mathrm{Tr}\ BA$

**证明**

根据定义，我们有 $(AB)_{j,j}=\sum_{k=1}^{n} A_{jk}B_{kj}$，于是

$$
\mathrm{Tr}\ AB=\sum_{j=1}^{n}\sum_{k=1}^{n} A_{jk}B_{kj}
=\sum_{k=1}^{n}\sum_{j=1}^{n} B_{kj}A_{jk}=\mathrm{Tr}\ BA
$$

由上面这个定理，我们可以证明：相似的矩阵有相同的迹。因为

$$
\mathrm{Tr}\ PAP^{-1}=\mathrm{Tr}\ (PA)P^{-1}=\mathrm{Tr}\ P^{-1}(PA)=\mathrm{Tr}\ A
$$

因此 $\mathrm{Tr}\ \mathcal M(T)$ 的值与基的选取无关，于是我们有如下定理：

**定理 7.2.5**

设 $V$ 是复向量空间，$T\in\mathcal L(V)$，则 $\mathrm{Tr}\ T=\mathrm{Tr}\ \mathcal M(T)$

**证明**

我们只需证明上述结论对 $V$ 的某个基成立。由于复向量空间上的算子都可上三角化，取这样的一个基，就能得到我们想要的结果。

由于矩阵的迹计算更简单，因此我们可以通过矩阵的迹来计算算子的迹。

**定理 7.2.6**

设 $V$ 是复向量空间，$S,T\in\mathcal L(V)$，则 $\mathrm{Tr}(S+T)=\mathrm{Tr}\ S+\mathrm{Tr}\ T$

**证明**

任取一个基，则有

$$
\begin{align*}
\mathrm{Tr}(S+T)&=\mathrm{Tr}(\mathcal M(S)+\mathcal M(T))\\
&=\mathrm{Tr}\ \mathcal M(S) + \mathrm{Tr}\ \mathcal M(T)\\
&=\mathrm{Tr}\ S +\mathrm{Tr}\ T
\end{align*}
$$

下面的定理是迹的一个简单应用，但是它能够导出量子物理中的一些重要结果（例如不确定性原理）。

**定理 7.2.7**

不存在算子 $S,T$ 使得 $ST-TS=I$

**证明**

我们有 $\mathrm{Tr}(ST-TS)=\mathrm{Tr}(\mathcal M(S)\mathcal M(T)-\mathcal M(T)\mathcal M(S))=0$，而 $\mathrm{Tr}\ I\ne 0$，即证。

# Section 3: 总结

本章我们介绍了迹与行列式，并给出了它们与特征多项式之间的联系。下一章，我们将研究实向量空间上的算子，并找出哪些定理仍然适用，以及其它定理在实向量空间上失效的原因。

本章内容就是这样，感谢观看！