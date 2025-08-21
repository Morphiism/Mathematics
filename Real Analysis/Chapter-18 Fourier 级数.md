上一章中，我们研究了如何把一类函数（实解析函数）写成一个无限次多项式，即幂级数。幂级数在处理指数函数、三角函数等特殊函数时有很大用处，但是在某些场合下，我们需要处理一些非实解析的函数，这些函数无法展开成幂级数，这时候幂级数就无法发挥作用了。

幸运的是，我们还有另一种级数，即 Fourier 级数，或称三角级数。这类级数处理的并非实解析函数，而是**周期函数**。粗略地说，Fourier 的理论表明，几乎每个周期函数都可以分解为正弦函数和余弦函数的无限和。

Fourier 级数和幂级数理论虽然有相似之处，但它们有一些重要的区别：比如，Fourier 级数的收敛通常不是一致的（按 $L^{\infty}$ 度量收敛），而是按一种不同的度量（ $L^{2}$ 度量）收敛。这一区别使得 Fourier 级数的理论比幂级数的理论更加的“几何化”，换言之，我们将使用内积空间的理论。此外，我们还将大量地使用复数，而幂级数只是稍微涉及了一点复数。

对 Fourier 级数的研究构成了一个独立的分支：Fourier 分析，本章中，我们将只介绍一些基本理论，而不会涉及它的广泛应用。

# Section 1: 周期函数与内积

**定义 18.1.1** 周期函数（periodic function）

设实数 $L>0$，函数 $f\colon \mathbb{R}\to \mathbb{C}$，如果对任意 $x \in \mathbb{R}$ 有 $f(x+L)=f(x)$，则称 $f$ 是 $L$ **周期**的。

例如，三角函数 $\sin,\cos$ 就是 $2\pi$ 周期的。如果函数 $f$ 是 $L$ 周期的，那么对任意整数 $k$，都有 $f(x+kL)=f(x)$，因此，$L$ 周期的函数也是 $kL$ 周期的。由此，我们通常也把 $L$ 周期的函数写成 $L\mathbb{Z}$ 周期的。

对于一个 $L\mathbb{Z}$ 周期的函数 $f$，定义为 $F(x)=f(Lx)$ 的函数 $F$ 是 $\mathbb{Z}$ 周期的，因此，只要我们了解了 $\mathbb{Z}$ 周期的函数，我们也就了解了所有周期的函数。对于一个 $\mathbb{Z}$ 周期的函数，我们只需了解它在 $[0,1)$ 上的行为，然后周期延拓至 $\mathbb{R}$ 上即可。

我们把连续的 $\mathbb{Z}$ 周期复值函数构成的集合记作 $C(\mathbb{R} / \mathbb{Z},\mathbb{C})$，我们可以证明，如果 $f,g \in C(\mathbb{R} / \mathbb{Z},\mathbb{C}),c \in \mathbb{C}$，那么函数 $f+g,cf \in C(\mathbb{R} / \mathbb{Z},\mathbb{C})$，根据 $\mathbb{C}$ 的代数性质，$C(\mathbb{R} / \mathbb{Z},\mathbb{C})$ 是一个向量空间。此外，我们还有如下结果：

**定理 18.1.2**

在 $L^{\infty}$ 度量下，$C(\mathbb{R} / \mathbb{Z},\mathbb{C})$ 是 $C_{b}(\mathbb{R},\mathbb{C})$ 的完备子空间。

**证明**

设 $f \in C(\mathbb{R} / \mathbb{Z},\mathbb{C})$，则 $f$ 在 $[0,1]$ 上连续，故在 $[0,1]$ 上有界。由周期性可知 $f$ 在 $\mathbb{R}$ 上有界。

现设 $C(\mathbb{R} / \mathbb{Z},\mathbb{C})$ 中的序列 $(f_{n})$ 按度量 $d_{\infty}$ 收敛于 $f$，根据一致收敛理论，$f$ 在 $\mathbb{R}$ 上连续，并且有

$$
f(x+1)=\lim_{ n \to \infty } f_{n}(x+1)=\lim_{ n \to \infty } f_{n}(x)=f(x)
$$

即 $f \in C(\mathbb{R} / \mathbb{Z},\mathbb{C})$，因此 $C(\mathbb{R} / \mathbb{Z},\mathbb{C})$ 是闭集。

由于 $C(\mathbb{R} / \mathbb{Z},\mathbb{C})$ 是 $C_{b}(\mathbb{R},\mathbb{C})$ 的子空间，而后者是完备的，故 $C(\mathbb{R} / \mathbb{Z},\mathbb{C})$ 是完备的，这就完成了证明。

在 $C(\mathbb{R} / \mathbb{Z},\mathbb{C})$ 上，不仅有向量空间结构，还可以定义内积：

**定义 18.1.3** 内积（inner product）

定义 $C(\mathbb{R} / \mathbb{Z},\mathbb{C})$ 上的**内积**为

$$
\langle f,g \rangle =\int_{0}^{1}f(x)\overline{g(x)}\mathrm{d} x
$$

其中复值函数 $f(x)=r(x)+i s(x)$ 的积分定义为

$$
\int_{a}^{b}f=\int_{a}^{b}r+i \int_{a}^{b}s
$$

根据 Riemann 积分的线性性，我们有 $\langle af+bg,h \rangle=a\langle f,h \rangle+b\langle g,h \rangle$，并且有 $\langle f,g \rangle=\overline{\langle g,f \rangle}$，还满足正定性：$\langle f,f \rangle>0,f\neq 0;\langle 0,0 \rangle=0$. 因此，$C(\mathbb{R} / \mathbb{Z},\mathbb{C})$ 是一个内积空间。

根据内积空间的理论，我们可以定义：

**定义 18.1.4** $L^{2}$ 范数，$L^{2}$ 度量

定义 $C(\mathbb{R} / \mathbb{Z},\mathbb{C})$ 上的 $L^{2}$ **范数**为

$$
\lVert f \rVert _{2}=\sqrt{ \langle f,f \rangle  }=\left( \int_{0}^{1}|f(x)|^{2}\mathrm{d} x \right)^{1/2}
$$

由 $L^{2}$ 范数诱导的 $L^{2}$ **度量**定义为

$$
d_{L^{2}}(f,g)=\lVert f-g \rVert _{2}=\left( \int_{0}^{1}|f(x)-g(x)|^{2}\mathrm{d} x \right)^{1/2}
$$

则 $(C(\mathbb{R} / \mathbb{Z},\mathbb{C}),d_{L^{2}})$ 构成了一个度量空间。$L^{2}$ 度量与 $\mathbb{R}^{n}$ 上的 $l^{2}$ 度量非常相似，这解释了它们符号的相似性。

利用 $L^{2}$ 度量，我们就有了一种不同于逐点收敛与一致收敛（按 $L^{\infty}$ 度量收敛）的收敛方式：$L^{2}$ 收敛。$L^{2}$ 度量的行为并不如 $L^{\infty}$ 度量的好，比如 $C(\mathbb{R} / \mathbb{Z},\mathbb{C})$ 在 $L^{2}$ 度量下不是完备的，而在 $L^{\infty}$ 度量下是完备的（定理 18.1.2），但这也使得它能够应用于更广泛的函数类。

# Section 2: 三角多项式

既然 $C(\mathbb{R} / \mathbb{Z},\mathbb{C})$ 是一个内积空间，那么它一定有一个基，我们还希望它是规范正交的，这样我们就可以使用公式

$$
c_{n}=\langle f,e_{n} \rangle 
$$

直接计算出系数。这样的规范正交基是否存在呢？下面我们给出答案。

**定义 18.2.1** 特征（characteristic）

对任意整数 $n$，令 $e_{n}\in C(\mathbb{R} / \mathbb{Z},\mathbb{C})$ 表示函数

$$
e_{n}(x)=e^{2\pi i n x}
$$

称为频率为 $n$ 的**特征**。

**定理 18.2.2**

对任意整数 $n,m$，有 $\langle e_{n},e_{m} \rangle=\delta_{nm}$.

**证明**

当 $n=m$ 时，我们有

$$
\langle e_{n},e_{m} \rangle =\int_{0}^{1}1 \mathrm{d} x=1
$$

当 $n\neq m$ 时，有

$$
\langle e_{n},e_{m} \rangle =\int_{0}^{1}e^{2\pi i(n-m)x}\mathrm{d} x=\left. \dfrac{e^{2\pi i (n-m)x}}{2\pi i(n-m)} \right|_{0}^{1}=0 
$$

即证。

上述定理表明，$\{ e_{n} \}_{n \in \mathbb{Z}}$ 是规范正交的（从而是线性无关的），但我们还不知道它是否是一个基。为了研究这一点，我们首先考虑它的有限张成：

**定义 18.2.3** 三角多项式（trigonometric polynomial）

设 $f \in C(\mathbb{R} / \mathbb{Z},\mathbb{C})$，如果存在整数 $N\geq 0$ 和复数序列 $(c_{n})_{n=-N}^{N}$ 使得

$$
f=\sum_{n=-N}^{N} c_{n}e_{n}
$$

则称 $f$ 是一个**三角多项式**。

三角函数 $\cos(2\pi n x)=\dfrac{1}{2}(e^{2\pi inx}+e^{-2\pi i nx})=\dfrac{1}{2}e_{-n}+\dfrac{1}{2}e_{n}$ 是一个三角多项式，类似地，$\sin(2\pi n x)$ 也是一个三角多项式。并且有限个三角多项式的和与积也是三角多项式。

对于一个三角多项式 $f=\sum_{n=-N}^{N}c_{n}e_{n}$，显然我们有 $c_{n}=\langle f,e_{n} \rangle$，并且有

$$
\lVert f \rVert _{2}^{2}=\sum_{n=-N}^{N} |c_{n}|^{2}
$$

我们用一种不同的方式改写一下这个推论。

**定义 18.2.4** Fourier 变换

设 $f \in C(\mathbb{R} / \mathbb{Z},\mathbb{C})$，对任意整数 $n$，定义第 $n$ 个 **Fourier 系数**为

$$
\hat{f}(n)=\langle f,e_{n} \rangle =\int_{0}^{1}f(x)e^{-2\pi inx}\mathrm{d} x
$$

函数 $\hat{f}\colon \mathbb{Z}\to \mathbb{C}$ 称为 $f$ 的 **Fourier 变换**，记作 $\mathcal{F}[f]$.

根据推论我们可以知道，对于三角多项式，我们有 **Fourier 反演公式**

$$
f(x)=\sum_{n=-N}^{N} \hat{f}(n)e_{n}=\sum_{n=-\infty}^{\infty} \hat{f}(n)e^{2\pi inx}
$$

以及 **Plancherel 公式**

$$
\lVert f \rVert _{2}^{2}=\sum_{n=-N}^{N} |\hat{f}(n)|^{2}=\sum_{n=-\infty}^{\infty} |\hat{f}(n)|^{2}
$$

因为对于整数 $|n|>N$，$\hat{f}(n)=0$. 下面，我们要把这两个公式推广到任意 $f \in C(\mathbb{R} / \mathbb{Z},\mathbb{C})$ 上，而不仅仅是三角多项式上。为此，我们将使用周期函数的 Weierstrass 逼近定理，即我们不是用多项式逼近连续函数，而是使用三角多项式来逼近连续周期函数。与多项式的 Weierstrass 逼近定理一样，我们也需要在周期函数上定义**卷积**的概念。

# Section 3: Fourier 定理

**定义 18.3.1** 周期卷积（periodic convolution）

设 $f,g \in C(\mathbb{R} / \mathbb{Z},\mathbb{C})$，定义其**周期卷积** $f*g\colon \mathbb{R}\to \mathbb{C}$ 为

$$
f*g(x)=\int_{0}^{1}f(y)g(x-y)\mathrm{d} y
$$

这里我们为周期卷积和紧支撑函数的卷积赋予了同一个符号，但这不会造成混淆：因为一个函数不可能既是周期的又是紧支撑的。

下面我们给出周期卷积的一些性质。

**定理 18.3.2**

设 $f,g,h \in C(\mathbb{R} / \mathbb{Z},\mathbb{C})$，则有

1. $f*g \in C(\mathbb{R} / \mathbb{Z},\mathbb{C})$
2. 交换性：$f*g=g*f$
3. 线性性：$f*(g+h)=f*g+f*h,f*(cg)=c(f*g)$
4. $f*e_{n}=\hat{f}(n)e_{n}$

**证明**

设 $x \in \mathbb{R}$，则有

$$
f*g(x+1)=\int_{0}^{1}f(y)g(x+1-y)\mathrm{d} y=\int_{0}^{1}f(y)g(x-y)\mathrm{d} y=f*g(x)
$$

因此 $f*g$ 是 $\mathbb{Z}$ 周期的。根据定义，$f,g$ 在任意有界区间 $[a,b]$ 上都是连续的，参考定理 16.6.7 的证明，我们可知 $f*g$ 在 $\mathbb{R}$ 上连续。

同样，根据 Riemann 积分的性质，我们可以证明卷积的交换性和线性性。

最后，我们有

$$
\begin{align}
f*e_{n} &= \int_{0}^{1}f(y)e^{2\pi in(x-y)}\mathrm{d} y \\
&= e^{2\pi inx} \int_{0}^{1}f(y)e^{-2\pi iny}\mathrm{d} y \\
&= \langle f,e_{n} \rangle e_{n}=\hat{f}(n)e_{n}
\end{align}
$$

即证。

利用性质 4，我们知道对任意三角多项式 $p$，有

$$
f*p=\sum_{n=-N}^{N} c_{n}(f*e_{n})=\sum_{n=-N}^{N} c_{n}\hat{f}(n)e_{n}
$$

即和三角多项式做卷积仍然得到三角多项式，这对应了 Weierstrass 逼近定理的第二个引理。

下面，我们引入周期恒等逼近的概念。

**定义 18.3.3** 周期恒等逼近（periodic approximation to the identity）

设 $\varepsilon>0,0<\delta<\dfrac{1}{2}$，称函数 $f\in C(\mathbb{R} / \mathbb{Z},\mathbb{C})$ 是一个**周期** $(\varepsilon,\delta)$ **恒等逼近**，如果满足：

1. 对任意 $x \in \mathbb{R}$ 有 $f(x)\geq 0$，并且 $\int_{0}^{1}f=1$
2. 对任意 $\delta<|x|<1-\delta$，有 $f(x)<\varepsilon$

现在我们给出引理一的一个类比，即三角多项式可以作为恒等逼近。

**引理 18.3.4**

对任意 $\varepsilon>0,0<\delta<\dfrac{1}{2}$，都存在三角多项式 $p$，使其为一个周期 $(\varepsilon,\delta)$ 恒等逼近。

**证明**

给定整数 $N\geq 1$，定义 **Fejer 核**为函数

$$
F_{N}=\sum_{n=-N}^{N} \left( 1-\dfrac{|n|}{N} \right)e_{n}
$$

显然，$F_{N}$ 是一个三角多项式，并且有

$$
\begin{align}
F_{N} &= \dfrac{1}{N} \sum_{n=-N}^{N} (N-|n|)e_{n} \\
&= \dfrac{1}{N} \sum_{n=0}^{N-1} \sum_{m=0}^{N-1} e_{n}\overline{e_{m}} \\
&= \dfrac{1}{N} \left| \sum_{n=0}^{N-1} e_{n} \right|^{2}
\end{align}
$$

当 $x$ 是整数时，$F_{N}(x)=N$，当 $x$ 不是整数时，根据几何级数公式得

$$
\begin{align}
F_{N}(x) &= \dfrac{1}{N} \left| \dfrac{e^{2\pi i Nx}-1}{e^{2\pi ix}-1} \right| ^{2} \\
&= \dfrac{1}{N} \left| \dfrac{e^{\pi iNx}}{e^{\pi ix}} \dfrac{e^{\pi iNx}-e^{-\pi iNx}}{e^{\pi ix}-e^{-\pi ix}} \right| ^{2} \\
&= \dfrac{1}{N} \dfrac{\sin^{2}(\pi Nx)}{\sin^{2}(\pi x)}
\end{align}
$$

从而对任意 $x \in \mathbb{R}$ 有 $F_{N}(x)\geq 0$，并且

$$
\int_{0}^{1}F_{N}=\sum_{n=-N}^{N} \left( 1-\dfrac{|n|}{N} \right)\int_{0}^{1}e_{n}=\left( 1-\dfrac{0}{N} \right)1=1
$$

最后，对任意 $\delta<|x|<1-\delta$ 有

$$
F_{N}(x)\leq \dfrac{1}{N \sin^{2}(\pi x)}< \dfrac{1}{N\sin^{2}(\pi \delta)}
$$

当 $N$ 足够大时，可以使 $F_{N}(x)<\varepsilon$，这就完成了证明。

现在我们就来证明周期函数的 Weierstrass 逼近定理。

**定理 18.3.5** Weierstrass 逼近定理

设 $f\in C(\mathbb{R} / \mathbb{Z},\mathbb{C})$，则对任意 $\varepsilon>0$，存在三角多项式 $p$，使得 $\lVert f-p \rVert_{\infty}<\varepsilon$.

**证明**

设 $f\in C(\mathbb{R} / \mathbb{Z},\mathbb{C})$，则 $f$ 一致连续且有界，从而存在 $M>0$ 使得对任意 $x \in \mathbb{R}$ 有 $|f(x)|\leq M$，并且对任意 $\varepsilon>0$，存在 $0<\delta< \dfrac{1}{2}$ 使得对任意满足 $|x'-x''|<\delta$ 的 $x',x''\in \mathbb{R}$ 有 $|f(x')-f(x'')|<\varepsilon$.

根据引理 18.3.4，我们可以找到一个三角多项式 $p$ 使其为周期 $(\varepsilon,\delta)$ 恒等逼近，那么 $f*p$ 也是一个三角多项式，现在我们来计算 $\lVert f-f*p \rVert_{\infty}$.

设 $x \in \mathbb{R}$，则有

$$
\begin{align}
|f(x)-f*p(x)| &= \left| f(x)-\int_{0}^{1}f(x-y)p(y)\mathrm{d} y \right|  \\
&= \left| \int_{0}^{1}f(x)p(y)\mathrm{d} y-\int_{0}^{1}f(x-y)p(y) \right|  \\
&\leq \int_{0}^{1}|f(x)-f(x-y)| p(y)\mathrm{d} y
\end{align}
$$

上式右端可以分解成

$$
\int_{\delta}^{1-\delta}|f(x)-f(x-y)|p(y)\mathrm{d} y+\int_{[0,\delta]\cup[1-\delta,1]}|f(x)-f(x-y)|p(y)\mathrm{d} y
$$

当 $\delta<|y|<1-\delta$ 时，有 $p(y)<\varepsilon$，故

$$
\int_{\delta}^{1-\delta}|f(x)-f(x-y)|p(y)\mathrm{d} y\leq 2M\varepsilon(1-2\delta)<2M\varepsilon
$$

当 $y \in[0,\delta]$ 时，有 $|x-(x-y)|<\delta$，当 $y \in[1-\delta,1]$ 时，我们有 $|f(x)-f(x-y)|=|f(x-1)-f(x-y)|$，从而 $|x-1-(x-y)|<\delta$，故

$$
\int_{[0,\delta]\cup[1-\delta,1]}|f(x)-f(x-y)|p(y)\mathrm{d} y\leq \varepsilon\int_{[0,\delta]\cup[1-\delta,1]}p<\varepsilon
$$

于是 $|f(x)-f*p(x)|<(2M+1)\varepsilon$，这就完成了证明。

利用 Weierstrass 逼近定理，我们就可以将 Fourier 反演公式和 Plancherel 公式推广到任意连续周期函数上。

**定理 18.3.6** Fourier 定理

对任意 $f \in C(\mathbb{R} / \mathbb{Z},\mathbb{C})$，**Fourier 级数** $\sum_{n=-\infty}^{\infty}\hat{f}(n)e_{n}$ 按 $L^{2}$ 度量收敛于 $f$，即

$$
\lim_{ N \to \infty } \left\lVert  f-\sum_{n=-N}^{N} \hat{f}(n)e_{n}  \right\rVert _{2}=0
$$

**证明**

任取 $0<\varepsilon<1$，存在三角多项式 $p=\sum_{n=-N_{0}}^{N_{0}}c_{n}e_{n}$ 使得 $\lVert f-p \rVert_{\infty}<\varepsilon$，从而有 $\lVert f-p \rVert_{2}\leq \lVert f-p \rVert_{\infty}<\varepsilon$.

现在设 $N>N_{0}$，令 $p_{N}=\sum_{n=-N}^{N}\hat{f}(n)e_{n}$，则对任意 $|m|\leq N$ 有

$$
\langle f-p_{N},e_{m} \rangle =\langle f,e_{m} \rangle -\sum_{n=-N}^{N} \hat{f}(n)\langle e_{n},e_{m} \rangle =\hat{f}(m)-\hat{f}(m)=0
$$

又由于 $p_{N}-p$ 可以写成 $e_{m},|m|\leq N$ 的线性组合，从而有 $\langle f-p_{N},p_{N}-p \rangle=0$，由勾股定理得

$$
\lVert f-p_{N} \rVert _{2}^{2}\leq\lVert f-p_{N} \rVert _{2}^{2}+\lVert p_{N}-p \rVert _{2}^{2}=\lVert f-p \rVert _{2}^{2}<\varepsilon
$$

这就完成了证明。

注意，我们只能得到 Fourier 级数按 $L^{2}$ 度量收敛于 $f$，而从这个结论无法推出级数逐点收敛或者一致收敛。相反，一致收敛却能够推出 $L^{2}$ 收敛以及逐点收敛，这表明一致收敛比 $L^{2}$ 收敛更强。因此，我们需要知道，什么时候 $L^{2}$ 收敛可以被加强为一致收敛，下面的定理给出了一个充分条件。

**定理 18.3.7**

对任意 $f \in C(\mathbb{R} / \mathbb{Z},\mathbb{C})$，如果级数 $\sum_{n=-\infty}^{\infty}|\hat{f}(n)|$ 收敛，那么 Fourier 级数 $\sum_{n=-\infty}^{\infty}\hat{f}(n)e_{n}$ 一致收敛于 $f$，即

$$
\lim_{ N \to \infty } \left\lVert  f-\sum_{n=-N}^{N} \hat{f}(n)e_{n}  \right\rVert _{\infty}=0
$$

**证明**

根据 Weierstrass M 判别法，级数 $\sum_{n=-\infty}^{\infty}\hat{f}(n)e_{n}$ 一致收敛于某个函数 $F$，于是

$$
\lim_{ N \to \infty } \left\lVert  F-\sum_{n=-N}^{N} \hat{f}(n)e_{n}  \right\rVert _{\infty}=0
$$

由于 $\lVert f \rVert_{2}\leq \lVert f \rVert_{\infty}$，故

$$
\lim_{ N \to \infty } \left\lVert  F-\sum_{n=-N}^{N} \hat{f}(n)e_{n}  \right\rVert _{2}=0
$$

这表明 $\sum_{n=-\infty}^{\infty}\hat{f}(n)e_{n}$ 按 $L^{2}$ 度量收敛于 $F$，但根据 Fourier 定理，该级数按 $L^{2}$ 度量收敛于 $f$，根据极限的唯一性，我们有 $F=f$，即证。

作为 Fourier 定理的一个推论，我们还有如下结果：

**定理 18.3.8** Plancherel 定理

对任意 $f \in C(\mathbb{R} / \mathbb{Z},\mathbb{C})$，级数 $\sum_{n=-\infty}^{\infty}|\hat{f}(n)|^{2}$ 收敛，并且

$$
\lVert f \rVert _{2}^{2}=\sum_{n=-\infty}^{\infty} |\hat{f}(n)|^{2}
$$

**证明**

设 $\varepsilon>0$，则存在 $N_{0}$ 使得对任意 $N>N_{0}$ 有

$$
\left\lVert  f-\sum_{n=-N}^{N} \hat{f}(n)e_{n}  \right\rVert _{2}<\varepsilon
$$

根据三角不等式，我们有

$$
(\lVert f \rVert _{2}-\varepsilon)^{2}< \left\lVert  \sum_{n=-N}^{N} \hat{f}(n)e_{n}  \right\rVert_{2}^{2} =\sum_{n=-N}^{N} |\hat{f}(n)|^{2}<(\lVert f \rVert _{2}+\varepsilon)^{2}
$$

从而

$$
(\lVert f \rVert _{2}-\varepsilon)^{2}<\liminf_{ N \to \infty } \sum_{n=-N}^{N} |\hat{f}(n)|^{2}\leq \limsup_{ N \to \infty } \sum_{n=-N}^{N} |\hat{f}(n)|^{2}<(\lVert f \rVert _{2}+\varepsilon)^{2}
$$

根据 $\varepsilon$ 的任意性即证。

我们知道，一个内积可以分解成范数的线性组合：

$$
\langle u,v\rangle=\frac{\|u+v\|^2-\|u-v\|^2+i\|u+iv\|^2-i\|u-iv\|^2}{4}
$$

因此，我们有推论：

**定理 18.3.9** Parseval 恒等式

对任意 $f,g \in C(\mathbb{R} / \mathbb{Z},\mathbb{C})$，级数 $\sum_{n=-\infty}^{\infty}\hat{f}(n)\overline{\hat{g}(n)}$ 收敛，并且

$$
\langle f,g \rangle =\int_{0}^{1}f(x)\overline{g(x)}\mathrm{d} x=\sum_{n=-\infty}^{\infty} \hat{f}(n)\overline{\hat{g}(n)}
$$

**证明**

我们有 $f+g,f-g,f+ig,f-ig \in C(\mathbb{R} / \mathbb{Z},\mathbb{C})$，对其应用 Plancherel 定理，则有

$$
\begin{align}
4\langle f,g \rangle &=\lVert f+g \rVert _{2}^{2}-\lVert f-g \rVert _{2}^{2}+i\lVert f+ig \rVert _{2}^{2}-i\lVert f-ig \rVert _{2}^{2} \\
&= \sum_{n=-\infty}^{\infty} (|\hat{f}(n)+\hat{g}(n)|^{2}-|\hat{f}(n)-\hat{g}(n)|^{2}) \\
&+ \sum_{n=-\infty}^{\infty} i(|\hat{f}(n)+i\hat{g}(n)|^{2}-|\hat{f}(n)-i\hat{g}(n)|^{2}) \\
&= \sum_{n=-\infty}^{\infty} 4 \hat{f}(n)\overline{\hat{g}(n)}
\end{align}
$$

即证。

下面，我们再给出一些与 Fourier 级数相关的定理。

**定理 18.3.10**

设 $f \in C(\mathbb{R} / \mathbb{Z},\mathbb{C})$ 是可微的，其导函数 $f'$ 连续，那么 $f'\in C(\mathbb{R} / \mathbb{Z},\mathbb{C})$，并且 $\mathcal{F}[f'](n)=2\pi i n \hat{f}(n)$.

**证明**

设 $x \in \mathbb{R}$，则

$$
f'(x+1)=\lim_{ y \to x+1 } \dfrac{f(y)-f(x+1)}{y-(x+1)}=\lim_{ y \to x } \dfrac{f(y+1)-f(x+1)}{y-x}=f'(x)
$$

故 $f' \in C(\mathbb{R} / \mathbb{Z},\mathbb{C})$，并且有

$$
\begin{align}
\mathcal{F}[f'](n) &= \int_{0}^{1}f'(x)e^{-2\pi inx}\mathrm{d} x \\
&= f(1)e^{-2\pi in}-f(0)+2\pi in \int_{0}^{1}f(x)e^{-2\pi inx}\mathrm{d} x \\
&= 2\pi in \hat{f}(n)
\end{align}
$$

即证。

**定理 18.3.11**

设 $f,g \in C(\mathbb{R} / \mathbb{Z},\mathbb{C})$，则对任意整数 $n$ 有

$$
\mathcal{F}[f*g](n)=\hat{f}(n)\hat{g}(n)
$$

**证明**

首先我们证明对于三角多项式 $p$ 有 $\mathcal{F}[f*p](n)=\hat{f}(n)\hat{p}(n)$. 设 $p=\sum_{n=-N}^{N}c_{n}e_{n}$，那么 $f*p = \sum_{n=-N}^{N} c_{n} \hat{f}(n)e_{n}$，从而

$$
\mathcal{F}[f*p](n) = \sum_{m=-\infty}^{\infty} c_{m}\hat{f}(m)\langle e_{m},e_{n} \rangle = c_{n}\hat{f}(n)=\hat{f}(n)\hat{p}(n)
$$

任取 $\varepsilon>0$，设三角多项式 $p$ 满足 $\lVert g-p \rVert_{\infty}<\varepsilon$，则 $\lVert g-p \rVert_{2}<\varepsilon$. 根据 Plancherel 定理，$|\hat{f}(n)|^{2}$ 是有界的，从而 $|\hat{f}(n)|$ 也是有界的，此外，$f$ 也是有界的，因此取 $M>0$ 使得 $|\hat{f}(n)|\leq M,|f(x)|\leq M$. 现在有

$$
|\mathcal{F}[f*g](n)-\mathcal{F}[f*p](n)|=|\langle f*(g-p),e_{n} \rangle |\leq \lVert f*(g-p) \rVert _{2}
$$

并且

$$
|f*g(x)-f*p(x)|\leq \int_{0}^{1}|f(x-y)||g(y)-p(y)|\mathrm{d} y \leq M\varepsilon
$$

还有

$$
|\hat{g}(n)-\hat{p}(n)| = |\langle g-p,e_{n} \rangle |\leq \lVert g-p \rVert _{2}<\varepsilon
$$

从而

$$
\begin{align}
& |\mathcal{F}[f*g]-\hat{f}(n)\hat{g}(n)|  \\
& \leq |\mathcal{F}[f*g](n)-\mathcal{F}[f*p](n)|+|\mathcal{F}[f*p](n)-\hat{f}(n)\hat{g}(n)| \\
& \leq \lVert f*(g-p) \rVert _{\infty}+ |\hat{f}(n)||\hat{p}(n)-\hat{g}(n)| \\
& \leq 2M\varepsilon
\end{align}
$$

根据 $\varepsilon$ 的任意性即证。

上述定理的一个形象的表达是，Fourier 变换把卷积与乘积“缠绕”在一起。

最后，我们来考虑一下实值函数的 Fourier 变换，利用 Euler 公式 $e^{ix}=\cos x+i\sin x$，我们很容易得到以下定理：

**定理 18.3.12**

设 $f \in C(\mathbb{R} / \mathbb{Z},\mathbb{C})$，定义**三角 Fourier 系数**为

$$
a_{n}=2 \int_{0}^{1}f(x)\cos(2\pi nx)\mathrm{d} x,b_{n}=2 \int_{0}^{1}f(x)\sin(2\pi nx)\mathrm{d} x
$$

则 Fourier 级数

$$
\dfrac{a_{0}}{2}+\sum_{n=1}^{\infty} (a_{n}\cos(2\pi nx)+b_{n}\sin(2\pi nx))
$$

按度量 $L^{2}$ 收敛于 $f$. 如果进一步有级数 $\sum_{n=1}^{\infty}a_{n},\sum_{n=1}^{\infty}b_{n}$ 绝对收敛，那么 Fourier 级数一致收敛于 $f$.

**证明**

根据 Fourier 定理，我们有

$$
\lim_{ N \to \infty } \left\lVert  f-\sum_{n=-N}^{N} \hat{f}(n)e_{n}  \right\rVert _{2}=0
$$

设 $1\leq |n|\leq N$，则有

$$
\begin{align}
\hat{f}(-n)e_{-n}+\hat{f}(n)e_{n} &= \int_{0}^{1}f(x)e^{2\pi inx}\mathrm{d} x (\cos(2\pi nx)-i \sin(2\pi nx)) \\
&+ \int_{0}^{1}f(x)e^{-2\pi inx}\mathrm{d} x(\cos(2\pi nx)+i \sin(2\pi nx)) \\
&= 2 \int_{0}^{1}f(x)\cos(2\pi nx)\mathrm{d} x (\cos(2\pi nx)) \\
&+ 2 \int_{0}^{1}f(x)\sin(2\pi nx)\mathrm{d} x (\sin(2\pi nx)) \\
&= a_{n}\cos(2\pi nx)+b_{n}\sin(2\pi nx)
\end{align}
$$

当 $n=0$ 时，$\hat{f}(0)=\int_{0}^{1}f(x)\mathrm{d}x=\dfrac{a_{0}}{2}$，因此我们有

$$
\lim_{ N \to \infty } \left\lVert  f-\dfrac{a_{0}}{2}-\sum_{n=1}^{N} (a_{n}\cos(2\pi nx)+b_{n}\sin(2\pi nx))  \right\rVert _{2}=0
$$

即证。如果级数 $\sum_{n=1}^{\infty}a_{n},\sum_{n=1}^{\infty}b_{n}$ 绝对收敛，那么级数

$$
\sum_{n=1}^{\infty} |\hat{f}(n)|=\sum_{n=1}^{\infty} \left| \dfrac{a_{n}-ib_{n}}{2} \right| \leq \dfrac{1}{2}\sum_{n=1}^{\infty} (|a_{n}|+|b_{n}|)
$$

以及级数

$$
\sum_{n=1}^{\infty} |\hat{f}(-n)|=\sum_{n=1}^{\infty} \left| \dfrac{a_{n}+ib_{n}}{2} \right| \leq \dfrac{1}{2}\sum_{n=1}^{\infty} (|a_{n}|+|b_{n}|)
$$

绝对收敛，从而 Fourier 级数一致收敛于 $f$，这就完成了证明。

# Section 4: 任意周期的 Fourier 级数

最后，我们将对 $L\mathbb{Z}$ 周期的函数建立 Fourier 级数理论。设 $L>0$，定义 $C(\mathbb{R} / L\mathbb{Z},\mathbb{C})$ 为所有 $L\mathbb{Z}$ 周期的连续复值函数构成的空间，在其上可以定义内积：

**定义 18.4.1** 内积

定义 $C(\mathbb{R} / L\mathbb{Z},\mathbb{C})$ 上的**内积**为

$$
\langle f,g \rangle =\dfrac{1}{L} \int_{0}^{L}f(x)\overline{g(x)}\mathrm{d} x
$$

下面我们定义特征：$C(\mathbb{R} / L\mathbb{Z},\mathbb{C})$ 上的规范正交基。

**定义 18.4.2** 特征

对任意整数 $n$，令 $e_{n}\in C(\mathbb{R} / L\mathbb{Z},\mathbb{C})$ 表示函数

$$
e_{n}(x)=e^{2\pi i n x / L}
$$

称为频率为 $n$ 的**特征**。

**定义 18.4.3** Fourier 变换

设 $f \in C(\mathbb{R} / L\mathbb{Z},\mathbb{C})$，对任意整数 $n$，定义第 $n$ 个 **Fourier 系数**为

$$
\hat{f}(n)=\langle f,e_{n} \rangle
$$

函数 $\hat{f}\colon \mathbb{Z}\to \mathbb{C}$ 称为 $f$ 的 **Fourier 变换**，记作 $\mathcal{F}[f]$.

接下来，我们给出本章的两个主要定理（Fourier 定理和 Plancherel 定理）在 $C(\mathbb{R} / L\mathbb{Z},\mathbb{C})$ 上的对应。

**定理 18.4.4** Fourier 定理

对任意 $f \in C(\mathbb{R} / L\mathbb{Z},\mathbb{C})$，**Fourier 级数** $\sum_{n=-\infty}^{\infty}\hat{f}(n)e_{n}$ 按 $L^{2}$ 度量收敛于 $f$，即

$$
\lim_{ N \to \infty } \left\lVert  f-\sum_{n=-N}^{N} \hat{f}(n)e_{n}  \right\rVert _{2}=0
$$

如果进一步有级数 $\sum_{n=-\infty}^{\infty}|\hat{f}(n)|$ 收敛，那么 Fourier 级数一致收敛于 $f$.

**证明**

对函数 $f(Lt)$ 应用 Fourier 定理，则有级数

$$
\sum_{n=-\infty}^{\infty} e^{2\pi in t} \int_{0}^{1}f(Lt)e^{-2\pi in t}\mathrm{d} t
$$

按 $L^{2}$ 度量收敛于函数 $f(Lt)$，令 $x=Lt$，则有

$$
\int_{0}^{L}f(x)e^{-2\pi inx / L}\mathrm{d} x=L\int_{0}^{1}f(Lt)e^{-2\pi in t}\mathrm{d} t
$$

于是级数

$$
\sum_{n=-\infty}^{\infty} e^{2\pi inx / L} \dfrac{1}{L}\int_{0}^{1}f(x)e^{-2\pi inx / L}\mathrm{d} x
$$

按 $L^{2}$ 度量收敛于 $f$. 当级数 $\sum_{n=-\infty}^{\infty}|\hat{f}(n)|$ 收敛时，逐字逐句重复定理 18.3.7 的证明，即可证明 Fourier 级数一致收敛于 $f$.

**定理 18.4.5** Plancherel 定理

对任意 $f \in C(\mathbb{R} / L\mathbb{Z},\mathbb{C})$，级数 $\sum_{n=-\infty}^{\infty}|\hat{f}(n)|^{2}$ 收敛，并且

$$
\lVert f \rVert _{2}^{2}=\sum_{n=-\infty}^{\infty} |\hat{f}(n)|^{2}
$$

**证明**

对函数 $f(Lt)$ 应用 Plancherel 定理，则有

$$
\int_{0}^{1}|f(Lt)|^{2}\mathrm{d} t=\sum_{n=-\infty}^{\infty} \left| \int_{0}^{1}f(Lt)e^{-2\pi in t}\mathrm{d} t \right|^{2}
$$

令 $x=Lt$，则有

$$
\dfrac{1}{L} \int_{0}^{L} |f(x)|^{2}\mathrm{d} x=\sum_{n=-\infty}^{\infty} \left| \dfrac{1}{L} \int_{0}^{1}f(x)e^{-2\pi inx / L}\mathrm{d} x \right|^{2}
$$

这就完成了证明。