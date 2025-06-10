[[Chapter-6 复向量空间上的算子]] [[Chapter-9 内积空间]]

上一章，我们引入了内积空间，并给出了关于内积的一些基本性质。在本章中，我们将研究内积空间上的算子，这一部分的研究成果在内积空间理论中最为深刻。

# Section 1: 伴随映射

**定义 10.1.1** 伴随映射（Adjoint Map）

设 $V,W$ 是内积空间，$T\in\mathcal L(V,W)$，则 $T$ 的**伴随映射**是映射 $T^\dagger\colon W\to V$ 满足：对任意 $v\in V,w\in W$ 有

$$
\langle Tv,w\rangle=\langle v,T^\dagger w\rangle
$$

注意，在第四章行列式（上）中我们定义了**伴随矩阵**为代数余子式构成的矩阵，这与我们定义的**伴随映射**是无关的。

上述定义还可以这样理解：考虑 $V$ 上的线性泛函 $v\mapsto \langle Tv,w\rangle$，根据Riesz表示定理，存在唯一一个向量使得 $v$ 与该向量的内积等于 $\langle Tv,w\rangle$，我们就定义这个向量为 $T^\dagger w$。

下面我们来研究伴随映射的基本性质。

**定理 10.1.2**

设 $S,T\in\mathcal L(V,W),R\in\mathcal L(U,V),\lambda\in\mathbb F$，则

1. $T^\dagger$ 是线性映射
2. $(S+T)^\dagger=S^\dagger + T^\dagger$
3. $(\lambda T)^\dagger=\overline{\lambda} T^\dagger$
4. $(T^\dagger)^\dagger=T$
5. $I^\dagger=I$
6. $(SR)^\dagger=R^\dagger S^\dagger$

**证明**

我们先来证明1。我们有

$$
\begin{align*}
\langle v,T^\dagger (aw_1+bw_2)\rangle &=\langle Tv,aw_1+bw_2\rangle\\
&=\overline a\langle Tv,w_1\rangle+\overline b\langle Tv,w_2\rangle\\
&=\langle v,aT^\dagger w_1+bT^\dagger w_2\rangle
\end{align*}
$$

因此 $T^\dagger(aw_1+bw_2)=aT^\dagger w_1+bT^\dagger w_2$，即 $T^\dagger\in\mathcal L(W,V)$。

同理，我们可以通过“在内积中移动并取伴随”的方法证明2和3。

设 $v\in V,w\in W$，则

$$
\langle (T^\dagger)^\dagger v,w\rangle=\langle v,T^\dagger w\rangle=\langle Tv,w\rangle
$$

于是 $(T^\dagger)^\dagger=T$。

同样，我们有

$$
\langle v,I^\dagger w\rangle=\langle Iv,w\rangle=\langle v,w\rangle=\langle v,Iw\rangle
$$

因此 $I^\dagger =I$。

最后，对于 $u\in U,w\in W$，有

$$
\langle u,(SR)^\dagger w\rangle=\langle SRu,w\rangle=\langle Ru,S^\dagger w\rangle=\langle u,R^\dagger S^\dagger w\rangle
$$

即 $(SR)^\dagger=R^\dagger S^\dagger$。

下面我们考虑伴随映射的核与像，这反映了伴随映射的“对偶性”。

**定理 10.1.3**

设 $T\in\mathcal L(V,W)$，则

1. $\ker T^\dagger=(\mathrm{im}\ T)^\perp$
2. $\mathrm{im}\ T^\dagger=(\ker T)^\perp$
3. $\ker T=(\mathrm{im}\ T^\dagger)^\perp$
4. $\mathrm{im}\ T=(\ker T^\dagger)^\perp$

**证明**

$w\in\ker T^\dagger$ 当且仅当对任意 $v\in V$ 有 $\langle v,T^\dagger w\rangle=\langle Tv,w\rangle=0$ 当且仅当 $w\in(\mathrm{im}\ T)^\perp$。于是1成立。

在1中把 $T$ 替换成 $T^\dagger$ 并使用 $(T^\dagger)^\dagger=T$ 就证明了3。在3中两边取正交补并利用 $(U^\perp)^\perp=U$ 就证明了2。在2中把 $T$ 用 $T^\dagger$ 替换就证明了4。

如果你看过第三章对偶空间，那你可能会发现对偶映射与伴随映射非常相似，这种相似性在下面的定理中有所体现：

**定理 10.1.4**

设 $T\in\mathcal L(V,W), e_1,\dots,e_n$ 是 $V$ 的规范正交基，$f_1,\dots,f_m$ 是 $W$ 的规范正交基，设 $A=\mathcal M(T,(e_1,\dots,e_n),(f_1,\dots,f_m))$，$B=\mathcal M(T^\dagger,(f_1,\dots,f_m),(e_1,\dots,e_n))$，则 $B$ 等于 $A$ 的共轭转置 $A^H=\overline{A}^T$。

**证明**

由规范正交基的性质，我们有

$$
Te_k=\langle Te_k,f_1\rangle f_1+\dots+\langle Te_k,f_m\rangle f_m
$$

于是 $A_{jk}=\langle Te_k,f_j\rangle$。同理，我们还有

$$
T^\dagger f_j=\langle T^\dagger f_j,e_1\rangle e_1+\dots+\langle T^\dagger f_j,e_n\rangle e_n
$$

则 $B_{kj}=\langle T^\dagger f_j,e_k\rangle=\langle f_j,Te_k\rangle=\overline{\langle Te_k,f_j\rangle}=\overline{A}_{jk}$

因此 $B=\overline{A}^T=A^H$。

注意，上述定理只对规范正交基成立，对于非规范正交基，$\mathcal M(T^\dagger)$ 未必等于 $\mathcal M(T)^H$。

在实向量空间上，矩阵的共轭转置就是矩阵的转置，这表明实内积空间 $V$ 上，$T^*$ 与 $T^\dagger$ 具有某种同构性。事实上，如果我们取 $\Phi\colon V\to V^*$ 为

$$
(\Phi u)(v)=\langle v,u\rangle
$$

则 $\Phi$ 是 $V$ 到 $V^*$ 的自然同构。现在令 $\Phi_V,\Phi_W$ 为 $V,W$ 上的 $\Phi$ 映射，则有

$$
\Phi_V\circ T^\dagger=T^*\circ \Phi_W
$$

现在我们将注意力转向内积空间上的算子，首先我们考虑算子的特征值：

**定理 10.1.5**

设 $T\in \mathcal L(V)$，则 $\lambda$ 是 $T$ 的特征值当且仅当 $\overline \lambda$ 是 $T^\dagger$ 的特征值。

**证明**

$\lambda$ 是 $T$ 的特征值当且仅当 $\ker(T-\lambda I)\ne \{0\}$，两边取正交补，当且仅当 $\mathrm{im}(T^\dagger-\overline\lambda I)\ne V$，当且仅当 $T^\dagger-\overline\lambda I$ 不可逆，当且仅当 $\overline\lambda$ 是 $T^\dagger$ 的特征值。

接下来我们介绍两类在内积空间上极为重要的算子：Hermite算子和正规算子。

**定义 10.1.6** Hermite算子（Hermitian Operator）

内积空间 $V$ 上的算子 $T$ 称为一个**Hermite算子**如果 $T=T^\dagger$，即对任意 $v,w\in V$ 有 $\langle Tv,w\rangle=\langle v,Tw\rangle$

我们可以证明，Hermite算子的和也是Hermite算子，实数与Hermite算子的乘积也是Hermite算子。

在复内积空间上，Hermite算子的性质类似于实数在复数域中的性质，而伴随对应于复数的共轭，我们之后能看到更多支持这一类比的性质。

**定理 10.1.7**

Hermite算子的特征值都是实的。

**证明**

设 $T\in\mathcal L(V)$ 是Hermite算子，$\lambda$ 是 $T$ 的特征值，对应的特征向量是 $v$，则

$$
\lambda \|v\|^2=\langle \lambda v,v\rangle=\langle Tv,v\rangle=\langle v,Tv\rangle=\langle v,\lambda v\rangle=\overline \lambda \|v\|^2
$$

于是 $\lambda=\overline \lambda$，即 $\lambda\in\mathbb R$。

下面的定理表明，在复内积空间上，只有0算子才能使 $Tv$ 总正交于 $v$。

**定理 10.1.8**

设 $V$ 是复内积空间，$T\in\mathcal L(V)$，若对任意 $v\in V$ 都有 $\langle Tv,v\rangle=0$，则 $T=0$

**证明**

我们从定理9.1.11证明中的极化恒等式得到启发，对于 $u,w\in V$，$\langle Tu,w\rangle$ 可以表示为

$$
\begin{align*}
\langle Tu,w\rangle &=\dfrac{\langle T(u+w),u+w\rangle-\langle T(u-w),u-w\rangle}{4}\\
&+i\dfrac{\langle T(u+iw),u+iw\rangle-\langle T(u-iw),u-iw\rangle}{4}
\end{align*}
$$

注意右边每一项都是 $\langle Tv,v\rangle$ 的形式，故 $\langle Tu,w\rangle=0$，取 $w=Tu$ 即得 $T=0$。

下面的定理给出了Hermite算子与实数性质相似的另一个例子。

**定理 10.1.9**

设 $V$ 是复内积空间，$T\in\mathcal L(V)$，则 $T$ 是Hermite算子当且仅当对任意 $v\in V$ 有 $\langle Tv,v\rangle\in\mathbb R$

**证明**

设 $v\in V$，则

$$
\langle Tv,v\rangle-\overline{\langle Tv,v\rangle}=\langle Tv,v\rangle-\langle v,Tv\rangle=\langle (T-T^\dagger)v,v\rangle
$$

若 $T$ 是Hermite算子，则 $\langle Tv,v\rangle=\overline{\langle Tv,v\rangle}$，即 $\langle Tv,v\rangle\in\mathbb R$。

若 $\langle Tv,v\rangle\in\mathbb R$，则 $\langle (T-T^\dagger)v,v\rangle=0$，从而 $T=T^\dagger$，即 $T$ 是Hermite算子，即证。

上面两个定理仅对复内积空间成立，和线性代数中的大多数情形一样。在实内积空间中，我们很容易能找到反例：平面上的 $90^\circ$ 旋转 $R$ 满足 $R\ne 0,\langle Rv,v\rangle=0$。然而，对于实内积空间上的Hermite算子，我们可以证明不会有这种情况。

**定理 10.1.10**

设 $T$ 是 $V$ 上的Hermite算子满足对任意 $v\in V$ 有 $\langle Tv,v\rangle=0$，则 $T=0$

**证明**

我们只需证明 $V$ 是实内积空间的情况。对于 $u,w\in V$，有

$$
\langle Tu,w\rangle=\dfrac{\langle T(u+w),u+w\rangle-\langle T(u-w),u-w\rangle}{4}
$$

要证明上面的等式需要用到Hermite算子的性质：

$$
\langle Tu,w\rangle=\langle u,Tw\rangle=\langle Tw,u\rangle
$$

于是我们有 $\langle Tu,w\rangle=0$，取 $w=Tu$ 得 $T=0$。

下面我们介绍正规算子，它的性质比Hermite算子稍弱一些。

**定义 10.1.11** 正规的（Normal）

内积空间 $V$ 上的算子 $T$ 是**正规的**，如果 $TT^\dagger=T^\dagger T$

显然，Hermite算子都是正规的（因为 $T^\dagger=T$），因此对于正规算子成立的结论对Hermite算子也成立。

下面的定理给出了正规算子的一个简单刻画。

**定理 10.1.12**

内积空间 $V$ 上的算子 $T$ 是正规的当且仅当对任意 $v\in V$ 有 $\|Tv\|=\|T^\dagger v\|$

**证明**

设 $v\in V$，则 $T$ 是正规的当且仅当 $TT^\dagger-T^\dagger T=0$，当且仅当 $\langle (TT^\dagger-T^\dagger T)v,v\rangle=0$，当且仅当 $\langle TT^\dagger v,v\rangle=\langle T^\dagger Tv,v\rangle$，当且仅当 $\|T^\dagger v\|^2=\|Tv\|^2$。其中第二个“当且仅当”能够成立是因为 $TT^\dagger-T^\dagger T$ 是Hermite算子。

我们之前讲到，伴随算子的特征值等于算子特征值的复共轭，但没有关于特征向量的讨论。下面我们将证明正规算子关于特征向量的两个重要定理，它们是谱定理的基础。

**定理 10.1.13**

设 $T$ 是 $V$ 上的正规算子，$v$ 是对应于 $\lambda$ 的特征向量，则 $v$ 也是 $T^\dagger$ 的对应于 $\overline\lambda$ 的特征向量。

**证明**

由于 $T$ 与 $T^\dagger$ 和 $\lambda I$ 是交换的，故 $T-\lambda I$ 是正规的。从而

$$
\|(T-\lambda I)v\|=\|(T^\dagger -\overline\lambda I)v\|=0
$$

于是 $(T^\dagger-\overline\lambda I)v=0$，即证。

**定理 10.1.14**

设 $T$ 是 $V$ 上的正规算子，则 $T$ 的对应于不同特征值的特征向量正交。

**证明**

设 $\lambda,\mu$ 是 $T$ 的不同特征值，对应的特征向量为 $v,w$，则

$$
(\lambda-\mu)\langle v,w\rangle=\langle \lambda v,w\rangle-\langle v,\overline\mu w\rangle\\
=\langle Tv,w\rangle-\langle v,T^\dagger w\rangle=0
$$

即 $\langle v,w\rangle=0$。

因此，我们可以讨论使用规范正交基来对角化正规算子与Hermite算子的可行性，这正是下一节：谱定理的主要内容。

# Section 2: 谱定理

谱定理中的“谱”一词最初来源于物理学，用来描述光谱的颜色分布，在量子力学中，原子核外的电子跃迁时发出或吸收的能量是固定的，对应了能量算子的特征值。因此，算子的特征值通常也称为它的“谱”。

和往常一样，复内积空间上的算子性质通常比实算子好，因此我们首先考虑复谱定理，它表明，复内积空间上的正规算子可以对角化。

**定理 10.2.1** 复谱定理（Complex Spectral Theorem）

设 $V$ 是有限维非零复内积空间，$T\in\mathcal L(V)$，则以下条件等价：

1. $T$ 是正规的
2. $V$ 有一个 $T$ 的特征向量构成的规范正交基
3. $T$ 关于 $V$ 的某个规范正交基有对角矩阵

**证明**

先证 $3\to 1$，设 $T$ 关于某个规范正交基有对角矩阵 $A$，则 $T^\dagger$ 在同一个基下的矩阵 $A^H$ 也是对角矩阵，对角矩阵之间是交换的，因此 $T^\dagger T=TT^\dagger$，即 $T$ 是正规的。

现设1成立，由Schur定理（9.2.8），$T$ 关于某个规范正交基 $e_1,\dots,e_n$ 有上三角矩阵

$$
A=\begin{pmatrix}
A_{11} & \dots & A_{1n} \\
    & \ddots & \vdots  \\
0 &   & A_{nn}
\end{pmatrix}
$$

由于 $T$ 是正规的，则 $\|Te_1\|^2=\|T^\dagger e_1\|^2$，即

$$
|A_{11}|^2=|A_{11}|^2+\dots+|A_{1n}|^2
$$

这表明 $A$ 的第一行除 $A_{11}$ 外都为0。现在又有 $\|Te_2\|^2=\|T^\dagger e_2\|^2$，于是

$$
|A_{22}|^2=|A_{22}|^2+\dots+|A_{2n}|^2
$$

这表明 $A$ 的第二行除 $A_{22}$ 外都为0。以此类推，我们可以证明 $A$ 除对角线上的元素都为0，这表明 $e_1,\dots,e_n$ 是 $T$ 的特征向量，从而证明了2。

由定理5.3.7，$2\to 3$ 是显然的。这就完成了证明。

接下来我们考虑实谱定理，我们已经见过实正规算子不可对角化的例子：平面上的旋转，因此，实谱定理的条件应当比复谱定理更加严格：我们要求 $T$ 是Hermite算子。在证明之前，我们先做一些准备工作。

在第八章，我们介绍了处理实向量空间上的算子的常用方法，即将实向量空间扩展为复向量空间，然后利用复算子的性质推导实算子的性质。具体来说，我们将利用复谱定理以及定理10.1.7来证明实谱定理。在此之前，我们需要找到一种将实内积空间扩张的方法。

**定理 10.2.2**

设 $V$ 是实内积空间，$u_1,u_2,v_1,v_2\in V$，则二元映射

$$
\langle u_1+iv_1,u_2+iv_2\rangle=\langle u_1,u_2\rangle+\langle v_1,v_2\rangle+i(\langle v_1,u_2\rangle-\langle u_1,v_2\rangle)
$$

是复化 $V_{\mathbb C}$ 上的复内积。

这个定理我们留给读者进行验证。

下面的定理是证明实谱定理的关键：

**定理 10.2.3**

设 $V$ 是实内积空间，$T\in\mathcal L(V)$ 是Hermite算子，则 $T$ 在复内积空间 $V_{\mathbb C}$（取定理10.2.2中的内积）上的复化 $T_{\mathbb C}$ 也是Hermite算子。

**证明**

设 $u_1,u_2,v_1,v_2\in V$，则

$$
\begin{align*}
\langle T_{\mathbb C}(u_1+iv_1),u_2+iv_2\rangle &=\langle Tu_1+iTv_1,u_2+iv_2\rangle\\
&=\langle Tu_1,u_2\rangle+\langle Tv_1,v_2\rangle+i(\langle Tv_1,u_2\rangle-\langle Tu_1,v_2\rangle)\\
&=\langle u_1,Tu_2\rangle+\langle v_1,Tv_2\rangle+i(\langle v_1,Tu_2\rangle-\langle u_1,Tv_2\rangle)\\
&=\langle u_1+iv_1,Tu_2+iTv_2\rangle\\
&=\langle u_1+iv_1,T_{\mathbb C}(u_2+iv_2)
\end{align*}
$$

因此 $T_{\mathbb C}$ 是Hermite算子。

回顾一下，所有Hermite算子都是正规算子，于是我们立即得到下面的定理：

**定理 10.2.4** 实谱定理（Real Spectral Theorem）

设 $V$ 是实内积空间，$T\in\mathcal L(V)$，则以下条件等价：

1. $T$ 是Hermite算子
2. $V$ 有一个 $T$ 的特征向量构成的规范正交基
3. $T$ 关于 $V$ 的某个规范正交基有对角矩阵

**证明**

首先证 $3\to 1$，设 $T$ 在某个规范正交基下有对角矩阵 $A$，则 $A^T=A$，从而 $T^\dagger=T$，即 $T$ 是Hermite算子。

现在设1成立。则 $T$ 的复化 $T_{\mathbb C}\in\mathcal L(V_{\mathbb C})$ 是Hermite算子，应用复谱定理，则在 $V_{\mathbb C}$ 的规范正交基 $e_1+if_1,\dots,e_n+if_n$ 下 $T_{\mathbb C}$ 有对角矩阵，且矩阵对角线上为 $T_{\mathbb C}$ 的特征值。

由定理10.1.7可知，$T_{\mathbb C}$ 的特征值均为实数，于是有

$$
T_{\mathbb C}(e_j+if_j)=\lambda_j e_j+i\lambda_j f_j
$$

则 $Te_j=\lambda_j e_j$，再由 $V_{\mathbb C}$ 上内积的定义（10.2.2）可知，$\dfrac{e_1}{\|e_1\|},\dots,\dfrac{e_n}{\|e_n\|}$ 是 $V$ 的规范正交基，于是证明了2。

$2\to 3$ 是显然的。这就完成了证明。

复谱定理完全刻画了复内积空间上的正规算子（进而刻画了Hermite算子），而实谱定理完全刻画了实内积空间上的Hermite算子。接下来，我们考虑实内积空间上的正规算子，这一部分极大地依赖于定理8.2.1：非零有限维向量空间上的算子有一维或二维不变子空间。

首先我们考虑二维实内积空间上的正规非Hermite算子。

**定理 10.2.5**

设 $V$ 是二维实内积空间，$T\in\mathcal L(V)$，则以下条件等价：

1. $T$ 是正规算子但不是Hermite算子
2. $T$ 关于 $V$ 的每个规范正交基的矩阵都具有形式

$$
\begin{pmatrix}
a & -b \\
b & a
\end{pmatrix}
$$

其中 $b\ne 0$。

3. $T$ 关于 $V$ 的某个规范正交基的矩阵具有形式

$$
\begin{pmatrix}
a & -b \\
b & a
\end{pmatrix}
$$

其中 $b>0$。

**证明**

先证 $3\to 1$，设 $T$ 关于 $V$ 的某个规范正交基的矩阵 $A$ 具有上述形式，则可以验证

$$
A^T A=AA^T=\mathrm{diag}(a^2+b^2,a^2+b^2)
$$

但 $A^T\ne A$，因此 $T$ 是正规的但不是Hermite算子。

现设1成立。设 $e_1,e_2$ 是 $V$ 的规范正交基，则

$$
\mathcal M(T)=A=\begin{pmatrix}
a & b \\
c & d
\end{pmatrix}
$$

由于 $T$ 是正规的，则有

$$
A^T A=
\begin{pmatrix}
a^2+c^2 & ab+cd\\
ab+cd & b^2+d^2
\end{pmatrix}=\begin{pmatrix}
a^2+b^2 & ac+bd\\
ac+bd & c^2+d^2
\end{pmatrix}
= AA^T
$$

则 $b^2=c^2$，即 $b=c$ 或 $b=-c$，因为 $T$ 不是Hermite算子，所以 $b=-c$，则有 $ab-bd=-ab+bd$，即 $ab=bd$。显然 $b\ne 0$（否则 $A^T=A$），故 $a=d$。于是

$$
A=\begin{pmatrix}
a & b \\
-b & a
\end{pmatrix}
$$

其中 $b\ne 0$，这就证明了2。

下面假设2成立。可以验证，如果 $T$ 在 $e_1,e_2$ 下的矩阵为

$$
\begin{pmatrix}
a & -b \\
b & a
\end{pmatrix}
$$

其中 $b<0$，则 $T$ 在 $e_1,-e_2$ 下的矩阵为

$$
\begin{pmatrix}
a & b \\
-b & a
\end{pmatrix}
$$

且 $-b>0$。于是我们证明了 $2\to 3$。这就完成了证明。

现在我们已完全描述了一维和二维不变子空间上的正规算子，要刻画任意维上的正规算子，我们就需要使用归纳法。以下定理保证了归纳法是可行的。

**定理 10.2.6**

设 $V$ 是有限维内积空间，$T\in\mathcal L(V)$ 是正规算子，$V$ 的子空间 $U$ 在 $T$ 下不变，则

1. $U^\perp$ 在 $T$ 下不变
2. $U$ 在 $T^\dagger$ 下不变
3. $(T|_U)^\dagger=T^\dagger |_U$
4. $T|_U$ 和 $T|_{U^\perp}$ 都是正规算子

**证明**

首先证明1。设 $U$ 的规范正交基为 $e_1,\dots,e_m$，将其扩张为 $V$ 的规范正交基 $e_1,\dots,e_m,f_1,\dots,f_n$。由于 $U$ 在 $T$ 下不变，因此每个 $Te_j\in \mathrm{span}(e_1,\dots,e_m)$，从而 $T$ 在 $e_1,\dots,e_m,f_1,\dots,f_n$ 下有分块矩阵

$$
\begin{pmatrix}
A_{m\times m} & B_{m\times n} \\
0_{n\times m} & C_{n\times n}
\end{pmatrix}
$$

由于 $T$ 是正规的，则 $\|Te_j\|^2=\|T^\dagger e_j\|^2$。我们知道 $\|Te_j\|^2$ 是 $A$ 的第 $j$ 列元素的平方和，因此

$$
\sum_{j=1}^{m} \|Te_j\|^2=A \text{的所有元素的平方和}
$$

同理

$$
\sum_{j=1}^{m} \|T^\dagger e_j\|^2=A \text{与} B \text{的所有元素的平方和}
$$

由 $\sum_{j=1}^{m} \|Te_j\|^2=\sum_{j=1}^{m} \|T^\dagger e_j\|^2$ 可得 $B=0$。因此每个 $Tf_j\in\mathrm{span}(f_1,\dots,f_n)=U^\perp$（由于 $V=U\oplus U^\perp$），从而证明了1。

对于 $T^\dagger$，由上面的讨论可知，其在同一基下的矩阵为

$$
\begin{pmatrix}
A^H & 0 \\
0 & C^H
\end{pmatrix}
$$

因此 $U=\mathrm{span}(e_1,\dots,e_m)$ 在 $T^\dagger$ 下不变。

对于3，设 $u,v\in U$，则

$$
\langle (T|_U)u,v\rangle=\langle Tu,v\rangle=\langle u,T^\dagger v\rangle=\langle u,(T^\dagger |_U)v\rangle
$$

这表明 $(T|_U)^\dagger=T^\dagger |_U$。

由于 $T$ 与其伴随可交换（因为 $T$ 是正规的），则 $T|_U$ 与 $T^\dagger |_U=(T|_U)^\dagger$ 可交换，从而 $T|_U$ 是正规的。由于 $U^\perp$ 也在 $T$ 下不变，从而用 $U^\perp$ 替换 $U$ 即可得 $T|_{U^\perp}$ 是正规的。

上述引理在 $T$ 是Hermite算子时有一个更强的版本，利用那个引理，我们可以使用归纳法（而不是复化）证明实谱定理。

下面我们来刻画实内积空间上的正规算子。

**定理 10.2.7**

设 $V$ 是有限维非零实内积空间，$T\in\mathcal L(V)$，则以下条件等价：

1. $T$ 是正规的
2. $T$ 关于 $V$ 的某个规范正交基有分块对角矩阵，每个块都是 $1\times 1$ 的矩阵 $(\lambda)$ 或者形如

$$
\begin{pmatrix}
a & -b \\
b & a
\end{pmatrix}
$$

的 $2\times 2$ 矩阵，其中 $b>0$。

**证明**

我们先证 $2\to 1$。如果 $T$ 关于某个规范正交基的矩阵有上述形式，则 $A^T A$ 与 $AA^T$ 的结果都是与 $A$ 形式相同的分块对角矩阵，并且每个块都与其对应的转置相乘。显然 $1\times 1$ 矩阵与其转置是交换的，且我们在定理10.2.5中验证了具有上述形式的 $2\times 2$ 矩阵是交换的。因此总的来说，$A$ 与 $A^T$ 是交换的，即 $T$ 是正规的。

设1成立，我们对 $n=\dim V$ 归纳。当 $n=1$ 时，结论显然成立，当 $n=2$ 时，如果 $T$ 是Hermite算子，则应用实谱定理，如果不是Hermite算子，则应用定理10.2.5。

现在假设结论对于维数小于 $n$ 的空间都成立。如果 $V$ 有在 $T$ 下不变的一维子空间，则令 $U$ 等于该子空间，否则令 $U$ 等于 $V$ 的二维不变子空间。

如果 $\dim U=1$，则取 $U$ 中一个范数为1的向量 $u$，则 $u$ 是 $U$ 的规范正交基，则 $T|_U$ 有 $1\times 1$ 矩阵 $(\lambda)$。如果 $\dim U=2$，则 $T|_U$ 是正规的，但不是Hermite算子，因此可以取一个规范正交基使得 $T|_U$ 有具有上述形式的 $2\times 2$ 矩阵。

由于 $V=U\oplus U^\perp$，且 $U^\perp$ 在 $T$ 下不变，$T|_{U^\perp}$ 是 $U^\perp$ 上的正规算子，由归纳假设，存在一个规范正交基使 $T|_{U^\perp}$ 的矩阵具有要求的形式。把这个基与 $U$ 的基放在一起，都得到了 $V$ 的一个规范正交基，且在这个基下 $T$ 的矩阵具有要求的形式。这就证明了 $1\to 2$。

上述定理就是我们对实正规算子所能达到的最好结果了，因为在实内积空间上甚至存在不可上三角化的算子，例如我们经常见到的平面上的旋转算子。

值得注意的是，上述讨论只是在同一个基下讨论可对角化，而如果我们被允许使用两个不同的基，那么我们将会看到，内积空间上的每个算子都可对角化，这就是所谓的**奇异值分解（SVD）**。

# Section 3: 总结

本章我们证明了谱定理，完全描述了内积空间上的Hermite算子和正规算子。下一章，我们将研究一类特殊的正规算子：**等距同构**，以及一类特殊的Hermite算子：**半正定算子**。最后，我们将把它们结合起来，证明**极分解定理**，这是奇异值分解的算子形式。

本期内容就是这样，感谢观看！