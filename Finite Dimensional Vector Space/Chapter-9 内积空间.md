[[Chapter-1 矩阵是什么]]

迄今为止，我们只对向量空间的线性结构做了研究。然而，在我们日常的几何空间中，还有长度、角度等概念。因此，本章我们将研究长度、角度在向量空间中的对应：**范数**与**内积**，并研究带有内积的向量空间上向量的关系。

# Section 1: 内积与范数

在日常的几何空间中，一个向量通常表示为从原点指向某点 $(x_1,x_2)$ 的箭头，它的长度通常定义为 $\sqrt{x_1^2+x_2^2}$，而有时也可以取 $|x_1|+|x_2|$ 或 $\max(|x_1|,|x_2|)$。要抽象化长度的概念，我们就要找到不同的"长度"之间的共性，也就是**使长度之为长度的性质**。这些性质都记录在下面的定义中：

**定义 9.1.1** 范数（Norm）

向量空间 $V$ 上的一个映射 $\|\cdot\|\colon V\to \mathbb R$ 是一个**范数**如果对任意 $u,v\in V,\lambda\in \mathbb F$ 有：

1. **正定性**：$\|v\| >0$ 如果 $v\ne 0$；$\|0\|=0$
2. **齐次性**：$\|\lambda v\|=|\lambda|\|v\|$
3. **三角不等式**：$\|u+v\|\le \|u\|+\|v\|$

定义了范数的向量空间称为**赋范空间**。

一些范数的例子包括：

- $L^1$ 范数（Manhattan距离）：$\|(x_1,\dots,x_n)\|_1=|x_1|+\dots+|x_n|$
- $L^2$ 范数（Euclid距离）：$\|(x_1,\dots,x_n)\|=\sqrt{|x_1|^2+\dots+|x_n|^2}$
- $L^{\infty}$ 范数：$\|(x_1,\dots,x_n)\|_{\infty}=\sup(|x_1|,\dots,|x_n|)$

在函数空间上也可类似地定义 $\|f\|=\sqrt{\int_{-\infty}^{\infty} |f(x)|^2 dx}$ 等。

>熟悉分析学的读者可能会发现，范数自然地诱导了 $V$ 上的一个**度量** $d(x,y)=\|x-y\|$，从而我们可以在 $V$ 上定义**极限**，这是做分析学研究的基础。这就是**泛函分析**所研究的主要内容，即：无限维赋范空间上的分析。

现在我们考虑角度。在实几何空间中，两个向量的夹角通常是用点积

$$
(x_1,x_2)\cdot (y_1,y_2)=x_1y_1+x_2y_2=\|x\|\|y\|\cos\theta
$$

定义的，于是我们有 $x\cdot x=\|x\|^2$。

然而在复数域中，按上面点积的定义，不一定有 $z\cdot z=\|z\|^2$。因此，为了保持这个性质，复数域上的点积就应该是 $(z_1,z_2)\cdot (w_1,w_2)=z_1\overline w_1+z_2\overline w_2$。

内积就是对复点积性质的抽象，如下所示：

**定义 9.1.2** 内积（Inner Product）

向量空间上的映射 $\langle \cdot,\cdot \rangle \colon V\times V\to \mathbb F$ 是一个**内积**如果对任意 $u,v,w\in V,\lambda\in\mathbb F$ 有：

1. **正定性**：$\langle v,v\rangle >0$ 如果 $v\ne 0$；$\langle 0,0 \rangle=0$
2. **共轭对称性**：$\langle u,v\rangle = \overline{\langle v,u\rangle}$
3. **第一个位置的加性**：$\langle u+w,v\rangle=\langle u,v\rangle+\langle w,v\rangle$
4. **第一个位置的齐次性**：$\langle \lambda u,v\rangle =\lambda \langle u,v\rangle$

定义了内积的向量空间称为**内积空间**。

一些内积的例子包括：

一般的Euclid内积：

$$
\langle (z_1,\dots,z_m),(w_1,\dots,w_m)\rangle=z_1\overline w_1+\dots+z_m\overline w_m
$$

以及它在函数空间上的对应：

$$
\langle f,g\rangle=\int_{-\infty}^{\infty} f(x)\overline{g(x)} dx
$$

该内积在Fourier级数中起到很大作用，我们在之后会做简要介绍。

下面我们推导一些内积的基本性质。

**定理 9.1.3**

设 $V$ 是内积空间，则对 $u,v,w\in V,\lambda\in\mathbb F$ 有：

1. 映射 $\varphi(v)=\langle v,u\rangle$ 是一个 $V\to \mathbb F$ 的线性映射（a.k.a. 线性泛函）
2. $\langle 0,u\rangle=\langle u,0\rangle=0$
3. $\langle u,v+w\rangle=\langle u,v\rangle+\langle u,w\rangle$
4. $\langle u,\lambda v\rangle=\overline \lambda \langle u,v\rangle$

**证明**

由内积的线性性得到1，再由齐次性，取 $\lambda=0$ 得 $\langle 0,u\rangle=0$，再根据共轭对称性得到 $\langle u,0\rangle=0$，从而证明了2。

下面我们证明3，则有

$$
\langle u,v+w\rangle=\overline{\langle v+w,u\rangle}\\
=\overline{\langle v,u\rangle}+\overline{\langle w,u\rangle}\\
=\langle u,v\rangle+\langle u,w\rangle
$$

同理我们也可以证明4。

对于点积，我们看到 $z\cdot z=\|z\|^2$，我们之后会证明，每个内积都诱导了 $V$ 上的一个范数，现在我们就暂且将下面的等式看成一个记号：

$$
\|u\|=\sqrt{\langle u,u\rangle}
$$

为了使 $\|u\|$ 成为一个范数，我们就需要证明三角不等式。为此，我们需要深入研究内积的性质。

在几何空间中，相互垂直的向量有很大作用，因此我们给出下面的定义：

**定义 9.1.4** 正交的（Orthogonal）

如果 $\langle u,v\rangle=0$，则称 $u,v$ **正交**。

根据定义，我们立即得到以下性质：

**定理 9.1.5**

1. 0与任意向量正交
2. 0是唯一一个与自身正交的向量

**证明**

由 $\langle 0,u\rangle=0$ 以及 $\langle 0,0\rangle=0$ 立即得到。

正交的向量之所以重要，是因为下面的著名定理：

**定理 9.1.6** 勾股定理，Pythagoras定理

若 $u,v$ 正交，则 $\|u+v\|^2=\|u\|^2+\|v\|^2$

**证明**

$$
\begin{align*}
\|u+v\|^2 &=\langle u+v,u+v\rangle\\
&=\langle u,u\rangle+\langle u,v\rangle+\langle v,u\rangle+\langle v,v\rangle\\
&=\|u\|^2+\|v\|^2
\end{align*}
$$

可以证明，在实内积空间中，勾股定理的逆定理成立。（注意在实内积空间中 $\langle u,v\rangle=\langle v,u\rangle$）

有时候，我们想把一个向量 $u$ 写成另一个向量 $v$ 的标量倍加上一个与 $v$ 正交的向量 $w$，这就是所谓的"正交分解"，它在牛顿力学中非常重要。

我们设 $u=cv+(u-cv)$，且 $\langle u-cv,v\rangle=\langle u,v\rangle-c\langle v,v\rangle=0$，这表明 $c$ 应取 $\dfrac{\langle u,v\rangle}{\|v\|^2}$，于是我们证明了如下定理：

**定理 9.1.7** 正交分解

设 $u,v\in V,v\ne 0$，令 $c=\dfrac{\langle u,v\rangle}{\|v\|^2}, w=u-cv$，则 $u=cv+w$ 且 $\langle w,v\rangle=0$。

正交分解被用于证明下面的著名不等式：

**定理 9.1.8** Cauchy-Schwartz不等式

设 $u,v\in V$，则 $|\langle u,v\rangle|\le \|u\|\|v\|$，等号成立当且仅当一个向量是另一个向量的标量倍。

**证明**

若 $v=0$，则结论显然成立，因此假设 $v\ne 0$。

考虑正交分解 $u=\dfrac{\langle u,v\rangle}{\|v\|^2}v+w$，由勾股定理，我们有

$$
\begin{align*}
\|u\|^2 &=\left\|\frac{\langle u,v\rangle}{\|v\|^2}v\right\|^2+\|w\|^2\\
&=\frac{|\langle u,v\rangle|^2}{\|v\|^2}+\|w\|^2\\
& \ge \frac{|\langle u,v\rangle|^2}{\|v\|^2}
\end{align*}
$$

两边乘以 $\|v\|^2$ 再开方就得到了不等式，由证明过程可以看出，等号成立当且仅当 $w=u-cv=0$，即一个向量是另一个向量的标量倍。

由于 $\dfrac{|\langle u,v\rangle|}{\|u\|\|v\|}\le 1$，因此我们可以类比点积，定义两个向量 $u,v$ 的**夹角** $\theta\in[0,\pi]$ 为 $\cos\theta = \dfrac{\langle u,v\rangle}{\|u\|\|v\|}$。

范数的三角不等式就是上面不等式的推论：

**定理 9.1.9** 三角不等式

设 $u,v\in V$，则 $\|u+v\|\le \|u\|+\|v\|$，等号成立当且仅当一个向量是另一个向量的标量倍。

**证明**

$$
\begin{align*}
\|u+v\|^2 &=\langle u,u\rangle+\langle u,v\rangle+\langle v,u\rangle+\langle v,v\rangle\\
&=\|u\|^2+\|v\|^2+2\mathrm{Re}\langle u,v\rangle\\
&\le \|u\|^2+\|v\|^2+2|\langle u,v\rangle|\\
&\le \|u\|^2+\|v\|^2+2\|u\|\|v\|\\
&=(\|u\|+\|v\|)^2
\end{align*}
$$

两边开方即得不等式，且等号成立当且仅当 $|\langle u,v\rangle|=\|u\|\|v\|$，当且仅当一个向量是另一个向量的标量倍。

由此我们证明了，每个内积空间上都有范数。因此，在泛函分析中，通常也会研究内积空间上的收敛性（例如，复Hilbert空间就是一个完备的内积空间，其内积为Euclid内积的积分形式，它也是量子物理的基础）。

利用内积，我们可以证明很多几何恒等式，一个例子如下：

**定理 9.1.10** 平行四边形恒等式

设 $u,v\in V$，则 $\|u+v\|^2+\|u-v\|^2=2(\|u\|^2+\|v\|^2)$

**证明**

$$
\begin{align*}
\|u+v\|^2+\|u-v\|^2&=\langle u+v,u+v\rangle+\langle u-v,u-v\rangle\\
&=\|u\|^2+\|v\|^2+\langle u,v\rangle+\langle v,u\rangle\\
& +\|u\|^2+\|v\|^2-\langle u,v\rangle-\langle v,u\rangle\\
&=2(\|u\|^2+\|v\|^2)
\end{align*}
$$

平行四边形恒等式的重要性在下面的定理中体现：

**定理 9.1.11**

设 $V$ 是赋范空间，如果 $V$ 上的范数满足平行四边形恒等式，则 $V$ 上可定义一个内积，使得 $\|u\|=\sqrt{\langle u,u\rangle}$。

由于上面的定理证明过程过于繁琐，因此我们只给出一个思路。

总体的思路是利用**极化恒等式**来定义内积：

$$
\langle u,v\rangle=\frac{\|u+v\|^2-\|u-v\|^2}{4}
$$

如果 $\mathbb F=\mathbb R$，或者

$$
\langle u,v\rangle=\frac{\|u+v\|^2-\|u-v\|^2+i\|u+iv\|^2-i\|u-iv\|^2}{4}
$$

如果 $\mathbb F=\mathbb C$。接下来就对照内积的定义进行验证即可。注意，在齐次性的证明中，需要使用Cauchy法：即先证明其对自然数成立，然后推广到有理数，然后再由范数的连续性（这是三角不等式的一个推论）推广到实数及复数。

# Section 2: 规范正交

几何空间的标准基 $(1,0,0),(0,1,0),(0,0,1)$ 满足以下性质：任意两个向量都正交，每个向量范数都为1。有这样的性质的基非常重要，因此我们给它一个名字：

**定义 9.2.1** 规范正交的（Orthonormal）

内积空间 $V$ 中的向量组 $e_1,\dots,e_m$ 是**规范正交的**如果其满足

$$
\langle e_j,e_k\rangle =\delta_{jk}=
\begin{cases}
1,& j=k\\
0,& j\ne k
\end{cases}
$$

如果规范正交组 $e_1,\dots,e_m$ 是 $V$ 的基，则称其为 $V$ 的**规范正交基**。

一个向量的范数通常不太容易求出，例如，设 $v=a_1v_1+\dots+a_nv_n$，则

$$
\|v\|^2=\langle v,v\rangle=\sum_{j,k} a_j\overline a_k\langle v_j,v_k\rangle
$$

因此，我们需要知道 $\langle v_j,v_k\rangle$ 这一共 $n^2$ 个内积才能求 $v$ 的范数。然而，对于规范正交基，这一过程就非常容易了。

**定理 9.2.2**

设 $e_1,\dots,e_m$ 是规范正交的，则对任意 $a_1,\dots,a_m\in\mathbb F$ 有

$$
\|a_1e_1+\dots+a_me_m\|^2=|a_1|^2+\dots+|a_m|^2
$$

根据上面的讨论，证明是显然的。

由此我们可以得到一个推论：

**定理 9.2.3**

设 $e_1,\dots,e_m$ 是规范正交的，则 $e_1,\dots,e_m$ 线性无关。

**证明**

设 $a_1e_1+\dots+a_me_m=0$，则 $|a_1|^2+\dots+|a_m|^2=0$，这表明每个 $a_j$ 都为0，即 $e_1,\dots,e_m$ 线性无关。

因此 $V$ 中长度为 $\dim V$ 的规范正交组是规范正交基。

根据下面的定理，我们可以看到，规范正交基上的分解也是很简单的。

**定理 9.2.4**

设 $e_1,\dots,e_n$ 是 $V$ 是规范正交基，$v\in V$，则

$$
v=\langle v,e_1\rangle e_1+\dots+\langle v,e_n\rangle e_n
$$

**证明**

设 $v=a_1e_1+\dots+a_ne_n$，则 $\langle v,e_j\rangle=a_j$，即证。

Fourier级数实际上就是上述定理在函数空间上的应用，其思路是使用规范正交基 $1,e^{it},e^{-it},e^{2it},e^{-2it},\dots$ 来表示 $f(t),t\in[-\pi,\pi]$，即

$$
f(t)=\sum_{k=-\infty}^{\infty} c_k e^{ik\pi t}
$$

其中 $c_k=\langle f(t),e^{ik\pi t}\rangle=\frac{1}{2\pi}\int_{-\pi}^{\pi} f(t)e^{-ikt} dt$。

对于一个内积空间，它一定有规范正交基吗？下面的定理可以给出答案：

**定理 9.2.5** Gram-Schmidt过程

设 $v_1,\dots,v_m$ 是 $V$ 中线性无关的向量组，设 $e_1=v_1/\|v_1\|$，对于 $j\ge 2$，定义

$$
e_j=\frac{v_j-\langle v_j,e_1\rangle e_1-\dots-\langle v_j,e_{j-1}\rangle e_{j-1}}{\|v_j-\langle v_j,e_1\rangle e_1-\dots-\langle v_j,e_{j-1}\rangle e_{j-1}\|}
$$

则 $e_1,\dots,e_m$ 是规范正交的，且对于任意 $j$ 有 

$$
\mathrm{span}(v_1,\dots,v_j)=\mathrm{span}(e_1,\dots,e_j)
$$

**证明**

我们对 $j$ 进行归纳。$j=1$ 时，由 $e_1=v_1/\|v_1\|$ 得 $\mathrm{span}(e_1)=\mathrm{span}(v_1)$。现假设 $\mathrm{span}(v_1,\dots,v_{j-1})=\mathrm{span}(e_1,\dots,e_{j-1})$。

由于 $v_1,\dots,v_j$ 线性无关，则 $v_j\notin \mathrm{span}(e_1,\dots,e_{j-1})$，于是 $e_j$ 定义中的分母不为0，用向量除以它的范数得到的向量范数为1，因此 $\|e_j\|=1$，且对于 $1\le k<j$ 有

$$
\langle e_j,e_k\rangle=\frac{\langle v_j,e_k\rangle-\langle v_j,e_k\rangle}{\|v_j-\langle v_j,e_1\rangle e_1-\dots-\langle v_j,e_{j-1}\rangle e_{j-1}\|}=0
$$

于是 $e_1,\dots,e_j$ 规范正交。

根据 $e_j$ 的定义我们知道 $v_j\in\mathrm{span}(e_1,\dots,e_j)$，因此 

$$
\mathrm{span}(v_1,\dots,v_j)\subset\mathrm{span}(e_1,\dots,e_j)
$$

而上面两个空间的维数都为 $j$，故 $\mathrm{span}(v_1,\dots,v_j)=\mathrm{span}(e_1,\dots,e_j)$。

Gram-Schmidt过程可以这样描述：首先选取 $v_1$ 方向上的一个单位向量 $e_1$，然后令 $v_2$ 减去它在 $v_1$ 方向上的投影，这就形成了一个直角，接下来令 $v_3$ 减去它在 $v_1,v_2$ 两个方向上的投影，于是 $e_3$ 就正交于 $v_1,v_2$ 张成的平面，以此类推，就得到了一个规范正交的向量组。

由此我们得到两个推论：

**定理 9.2.6**

设 $V$ 是有限维内积空间，则

1. $V$ 有一个规范正交基
2. $V$ 中的规范正交组可以扩充为规范正交基

**证明**

对于1，取 $V$ 的一个基应用Gram-Schmidt过程即可。

设 $e_1,\dots,e_m$ 是规范正交的，将其扩充成 $V$ 的基 $e_1,\dots,e_m,v_1,\dots,v_k$ 并应用Gram-Schmidt过程就得到规范正交基 $e_1,\dots,e_m,f_1,\dots,f_k$，其中因为 $e_1,\dots,e_m$ 是规范正交的，所以在Gram-Schmidt过程中不变。

在第五章，我们证明了复向量空间上的算子关于某个基有上三角矩阵，现在，既然我们在讨论内积空间，我们想要知道是否有规范正交基使算子的矩阵为上三角矩阵。下面的定理说明了这一点。

**定理 9.2.7**

设 $T\in\mathcal L(V)$，如果 $T$ 关于 $V$ 的某个基有上三角矩阵，则 $T$ 关于 $V$ 的某个规范正交基有上三角矩阵。

**证明**

设 $T$ 关于 $V$ 的基 $v_1,\dots,v_n$ 有上三角矩阵，则对任意 $j$ 有 $\mathrm{span}(v_1,\dots,v_j)$ 在 $T$ 下不变（详见定理5.3.1）。

对 $v_1,\dots,v_n$ 应用Gram-Schmidt过程，得到 $e_1,\dots,e_n$，则

$$
\mathrm{span}(v_1,\dots,v_j)=\mathrm{span}(e_1,\dots,e_j)
$$

于是 $\mathrm{span}(e_1,\dots,e_j)$ 在 $T$ 下不变，从而 $T$ 关于规范正交基 $e_1,\dots,e_n$ 有上三角矩阵。

由复算子的性质，我们立即得到以下定理：

**定理 9.2.8** Schur定理

设 $V$ 是有限维非零复内积空间，$T\in\mathcal L(V)$，则 $T$ 关于 $V$ 的某个规范正交基有上三角矩阵。

在几何空间中，我们有

$$
x\cdot y=x_1y_1+x_2y_2=x^T y
$$

我们在第三章中提到，$x^T$ 是一个线性泛函。下面的定理告诉我们，这种内积与线性泛函的对偶性不是偶然的。

**定理 9.2.9** Riesz表示定理

设 $V$ 是有限维内积空间，$\varphi$ 是 $V$ 上的线性泛函，则存在唯一的 $u\in V$ 使得对任意 $v\in V$ 有 $\varphi(v)=\langle v,u\rangle$

**证明**

首先证明存在性。设 $e_1,\dots,e_n$ 是 $V$ 的规范正交基，则

$$
\begin{align*}
\varphi(v)&=\varphi(\langle v,e_1\rangle e_1+\dots+\langle v,e_n\rangle e_n)\\
&=\langle v,e_1\rangle \varphi(e_1)+\dots\langle v,e_n\rangle \varphi(e_n)\\
&=\langle v,\overline{\varphi(e_1)}e_1+\dots+\overline{\varphi(e_n)}e_n\rangle
\end{align*}
$$

取 $u=\overline{\varphi(e_1)}e_1+\dots+\overline{\varphi(e_n)}e_n$ 即可。

现在来证唯一性。设有 $u_1,u_2$ 满足 $\varphi(v)=\langle v,u_1\rangle=\langle v,u_2\rangle$，则

$$
\langle v,u_1\rangle-\langle v,u_2\rangle=\langle v,u_1-u_2\rangle=0
$$

取 $v=u_1-u_2$，由正定性，得 $u_1-u_2=0$，即 $u_1=u_2$。

上面的定理给出了一个计算公式 $u=\overline{\varphi(e_1)}e_1+\dots+\overline{\varphi(e_n)}e_n$，并且，根据唯一性，右边的值与选用哪个规范正交基是无关的。

> **注**：在物理学中，向量的内积通常被定义为具有第二个位置的齐次性。这是因为在量子物理中，一个**量子态**是一个Hilbert空间中的向量，通常用Dirac记号表示：$|\psi\rangle$，并且两个向量的内积用 $\langle \varphi | \psi \rangle$ 表示。那么根据Riesz表示定理，存在唯一一个线性泛函使得 $\Phi |\psi\rangle=\langle \varphi | \psi \rangle$，我们就把这个泛函记作 $\langle \varphi |$，从而我们有 $\langle \varphi || \psi \rangle=\langle \varphi | \psi \rangle$。内积的第二个位置的齐次性保证了这种"拆分"是可行的。

# Section 3: 正交补与正交投影

接下来我们考虑与一个集合内所有向量都正交的向量，定义如下：

**定义 9.3.1** 正交补（Orthogonal Complement）

设 $U\subset V$，则 $U$ 的**正交补**定义为

$$
U^{\perp}=\{v\colon \forall u\in U,\langle v,u\rangle=0\}
$$

注意上述定义中的 $U$ 不要求是 $V$ 的子空间。

一些例子有：空间中的直线的正交补是垂直于直线且过原点的平面，平面的正交补是垂直于平面且过原点的直线。

下面我们来推导正交补的基本性质。

**定理 9.3.2**

设 $V$ 是内积空间，$U,W\subset V$，则

1. $U^{\perp}$ 是 $V$ 的子空间
2. $V^\perp =\{0\},\{0\}^\perp =V$
3. $U\cap U^\perp\subset \{0\}$
4. 若 $U\subset W$，则 $W^\perp \subset U^\perp$

**证明**

显然 $0\in U^\perp$，设 $v,w\in U^\perp$，则

$$
\langle av+bw,u\rangle=a\langle v,u\rangle+b\langle w,u\rangle=0
$$

故 $U^{\perp}$ 是 $V$ 的子空间。

由定理9.1.5，我们立即得到2。

设 $v\in U\cap U^\perp$，则 $\langle v,v\rangle=0$，因此 $v=0$，从而证明了3。

设 $v\in W^\perp$，则对任意 $w\in W$ 有 $\langle v,w\rangle=0$。又 $U\subset W$，则对任意 $u\in U$ 有 $\langle v,u\rangle=0$，故 $v\in U^\perp$。从而证明了4。

下面我们来考虑当 $U$ 是 $V$ 的子空间时其正交补有什么性质。根据本节开始时的例子，我们得到下面的定理：

**定理 9.3.3**

设 $U$ 是 $V$ 的有限维子空间，则 $V=U\oplus U^\perp$

**证明**

我们先证明 $V=U+U^\perp$。

设 $e_1,\dots,e_m$ 是 $U$ 的规范正交基，设 $v\in V$，令 

$$
\begin{align*}
u&=\langle v,e_1\rangle e_1+\dots+\langle v,e_m\rangle e_m\\
w&=v-\langle v,e_1\rangle e_1-\dots-\langle v,e_m\rangle e_m
\end{align*}
$$

则 $v=u+w$。对于任意 $j$，我们有 $\langle w,e_j\rangle=\langle v,e_j\rangle-\langle v,e_j\rangle=0$，因此 $w\in U^\perp$，显然有 $u\in U$，于是 $V=U+U^\perp$。

又有 $U\cap U^\perp=\{0\}$，这表明 $U+U^\perp$ 是直和，即证。

于是我们得到了一个维数公式：$\dim U^\perp=\dim V-\dim U$。

我们还能得到一个推论：

**定理 9.3.4**

设 $U$ 是 $V$ 的有限维子空间，则 $U=(U^\perp)^\perp$

**证明**

设 $u\in U$，则对任意 $w\in U^\perp$，有 $\langle u,w\rangle=0$，即 $u\in (U^\perp)^\perp$，则 $U\subset (U^\perp)^\perp$。

设 $v\in (U^\perp)^\perp$，则有 $v=u+w,u\in U,w\in U^\perp$，于是 $v-u=w\in U^\perp$。又 $v\in (U^\perp)^\perp,u\in U\subset (U^\perp)^\perp$，则 $v-u\in (U^\perp)^\perp$。故 $v-u\in U^\perp \cap (U^\perp)^\perp$，从而 $v-u=0,v=u\in U$，于是 $(U^\perp)^\perp\subset U$，即证。

我们在一些问题中经常需要向某个子空间做投影，利用正交补，我们可以按如下方法定义投影：

**定义 9.3.5** 正交投影（Orthogonal Projection）

设 $U$ 是 $V$ 的有限维子空间，定义 $V$ 到 $U$ 的**正交投影**为算子 $P_U\in \mathcal L(V)$ 如下：对于 $v\in V$，将其写成 $v=u+w,u\in U,w\in U^\perp$，则 $P_U v=u$

特别地，对于一维子空间 $U=\mathrm{span}(u)$，有

$$
P_U v=\frac{\langle v,u\rangle}{\|u\|^2}u
$$

下面我们给出正交投影的一些基本性质。

**定理 9.3.6**

设 $U$ 是 $V$ 的有限维子空间，$v\in V$，则

1. 对于 $u\in U$ 有 $P_U u=u$，对于 $w\in U^\perp$ 有 $P_U w=0$
2. $\mathrm{im}\ P_U=U, \ker P_U=U^\perp$
3. $v-P_U v\in U^\perp, P_{U^\perp}=I-P_U$
4. $P_U^2=P_U$
5. $\|P_U v\|\le \|v\|$
6. 对 $U$ 的规范正交基 $e_1,\dots,e_m$ 有 $P_U v=\langle v,e_1\rangle e_1+\dots+\langle v,e_m\rangle e_m$

**证明**

由定义立即得到1。

显然 $\mathrm{im}\ P_U\subset U$，设 $u\in U$，则 $u=P_U u\in\mathrm{im}\ P_U$，则 $\mathrm{im}\ P_U=U$。显然也有 $U^\perp\subset \ker P_U$，对于 $v\in\ker P_U$，在直和分解中则必然有 $v=0+v,0\in U,v\in U^\perp$，因此 $\ker P_U\subset U^\perp$，即证得了2。

对于 $v\in V$，有 $v=u+w,u\in U,w\in U^\perp$，则

$$
v-P_U v=v-u=w\in U^\perp
$$

且 $P_{U^\perp}v=w=(I-P_U)v$，于是有3成立。

$$
P_U^2 v=P_U u=u=P_U v
$$

于是 $P_U^2=P_U$。

$$
\|P_U v\|^2=\|u\|^2\le \|u\|^2+\|w\|^2=\|v\|^2
$$

开根号即得5。

对于6，参考定理9.3.3的证明，则显然有 

$$
P_U v=u=\langle v,e_1\rangle e_1+\dots+\langle v,e_m\rangle e_m
$$

下面我们求解一类在各种领域都非常常见的问题：给定一个子空间 $U$ 和向量 $v$，求 $\|v-u\|,u\in U$ 的最小值。使用正交投影，这一问题的求解非常容易。

**定理 9.3.7**

设 $U$ 是 $V$ 的有限维子空间，$v\in V$，则对任意 $u\in U$ 有

$$
\|v-P_U v\|\le \|v-u\|
$$

等号成立当且仅当 $u=P_U v$

**证明**

$$
\|v-P_U v\|^2\le \|v-P_U v\|^2+\|P_U v-u\|^2=\|v-u\|^2
$$

两边开方即得不等式，等号成立当且仅当 $\|P_U v-u\|^2=0$，当且仅当 $u=P_U v$。

上述定理的一个重要应用就是**线性回归问题**，如下所示：

给定 $n$ 个向量 $(x_i^{(1)},\dots,x_i^{(k)},y_i)\in \mathbb R^{k+1}$，要求参数 $w^{(1)},\dots,w^{(k)},b$ 使得 

$$
L=\sum_{i=1}^{n} \left(y_i-(w^{(1)}x_i^{(1)}+\dots+w^{(k)}x_i^{(k)}+b)\right)^2
$$

最小。

下面我们来求解这个最小二乘问题，我们将把这个问题转换成一个投影问题来解决。

考虑 $n$ 维向量 

$$
(x_1^{(1)},\dots,x_n^{(1)}),\dots,(x_1^{(k)},\dots,x_n^{(k)}),(1,\dots,1)
$$

张成的空间 $U$，令 $v=(y_1,\dots,y_n)$，则问题转化为要求使

$$
L=\|v-u\|^2
$$

最小的 $u$，由定理9.3.7得 $u=P_U v$。下面我们就来求 $u$。

由于 $v-u\in U^\perp$，故有

$$
\langle v-u,x^{(j)}\rangle=(x^{(j)})^T(v-u)=0
$$

（如无特殊说明，所有向量都应理解为列向量）以各 $x^{(j)}$ 为列构造矩阵

$$
A=\begin{bmatrix}x^{(1)} & \dots & x^{(k)} & 1\end{bmatrix}
$$

于是我们有 $A^T v=A^T u=A^TA w$，其中 $w=(w^{(1)},\dots,w^{(k)},b)$。这表明，我们要求的参数是方程

$$
A^T Aw=A^T v
$$

的解（如果有的话）。在之后的章节，我们将介绍 $A^T A$ 不可逆时的处理方法。

# Section 4: 总结

本章我们介绍了内积空间及其基本性质，以及与向量的正交性相关的几个概念。下一章，我们将研究内积空间上的算子，我们的最终目的是证明**谱定理**，它表明，内积空间上的一大类算子都可以对角化。

本期内容就是这样，感谢观看！