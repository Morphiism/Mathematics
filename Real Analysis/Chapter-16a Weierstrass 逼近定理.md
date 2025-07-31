我们将分成多个步骤来证明 Weierstrass 逼近定理。在证明中，我们一共需要三个重要引理。第一个引理是多项式可以用作恒等逼近。

**引理 1**

对任意 $\varepsilon>0$ 和 $0<\delta<1$，都存在 $[-1,1]$ 上的多项式 $p$，使得它是一个 $(\varepsilon,\delta)$-恒等逼近。

**证明**

定义 $[-1,1]$ 上的多项式 $p\colon [-1,1]\to \mathbb{R}$ 为

$$
p(x)=c(1-x^{2})^{N}
$$

则 $p$ 是连续的，并且支撑在 $[-1,1]$ 上。由于 $(1-x^{2})^{N}\geq 1-Nx^{2}$，故

$$
\int_{-1}^{1}(1-x^{2})^{N}\mathrm{d} x\geq \int_{-\frac{1}{\sqrt{ N }}}^{\frac{1}{\sqrt{ N }}}(1-x^{2})^{N}\mathrm{d} x\geq \int_{-\frac{1}{\sqrt{ N }}}^{\frac{1}{\sqrt{ N }}}(1-Nx^{2})\mathrm{d} x= \dfrac{4}{3\sqrt{ N }}
$$

取 $c=\left( \int_{-1}^{1}(1-x^{2})^{N}\mathrm{d}x \right)^{-1}>0$，则在 $[-1,1]$ 上有 $p(x)\geq 0$ 且 $\int_{-1}^{1}p=1$.

现在，我们要选取 $N$ 使得对任意 $\delta<|x|<1$ 有 $p(x)<\varepsilon$. 我们有

$$
p(x)=\dfrac{(1-x^{2})^{N}}{\int_{-1}^{1}(1-x^{2})^{N}\mathrm{d}x}\leq \sqrt{ N }(1-\delta^{2})^{N}
$$

由于 $\lim_{ N \to \infty }\sqrt{ N }(1-\delta^{2})^{N}=0$，故存在 $N$ 使得 $\sqrt{ N }(1-\delta^{2})^{N}<\varepsilon$，从而我们有 $p(x)<\varepsilon$，即证。

第二个关键引理是，与多项式进行卷积会产生另一个多项式。

**引理 2**

设 $f\colon \mathbb{R}\to \mathbb{R}$ 是支撑在 $[0,1]$ 上的连续函数，$g\colon \mathbb{R}\to \mathbb{R}$ 是支撑在 $[-1,1]$ 上的连续函数，并且是 $[-1,1]$ 上的多项式，那么 $f*g$ 在 $[0,1]$ 上是多项式。

**证明**

由于 $g$ 是 $[-1,1]$ 上的多项式，故有实数 $c_{0},\dots,c_{n}$ 使得

$$
g(x)=\sum_{i=0}^{n} c_{i}x^{i}, x \in[-1,1]
$$

由于 $f$ 支撑在 $[0,1]$ 上，故对任意 $x \in[0,1]$ 有

$$
\begin{align}
f*g(x) &= \int_{0}^{1} f(y)g(x-y)\mathrm{d} y \\
&= \int_{0}^{1} f(y) \sum_{i=0}^{n} c_{i}(x-y)^{i}\mathrm{d} y \\
&= \int_{0}^{1} f(y)\sum_{i=0}^{n} \sum_{j=0}^{i} c_{i} \binom{ i }{ j } x^{j}(-y)^{i-j}\mathrm{d} y \\
&= \int_{0}^{1} f(y) \sum_{j=0}^{n} \sum_{i=j}^{n} c_{i} \binom{ i }{ j } x^{j}(-y)^{i-j}\mathrm{d} y \\
&= \sum_{j=0}^{n} x^{j} \int_{0}^{1}f(y) \sum_{i=j}^{n} c_{i}\binom{ i }{ j } (-y)^{i-j}\mathrm{d} y
\end{align}
$$

令 $C_{j}=\int_{0}^{1}f(y) \sum_{i=j}^{n} c_{i}\binom{ i }{ j } (-y)^{i-j}\mathrm{d} y$，则 $C_{j}$ 与 $x$ 无关，故 $f*g$ 是 $[0,1]$ 上的多项式。

第三个关键引理是，如果一个一致连续的函数与一个恒等逼近做卷积，那么我们得到的函数将接近原来的函数（这实际上就是 $f*\delta=f$ ）。

**引理 3**

设 $f\colon \mathbb{R}\to \mathbb{R}$ 是支撑在 $[0,1]$ 上的连续函数，并且对任意 $x \in \mathbb{R}$ 有 $|f(x)|\leq M$，取 $\varepsilon>0,0<\delta<1$ 使得对任意 $|x-y|<\delta$ 的 $x,y\in \mathbb{R}$ 有 $|f(x)-f(y)|<\varepsilon$，设 $g$ 是一个 $(\varepsilon,\delta)$-恒等逼近，那么对任意 $x \in[0,1]$ 有

$$
|f*g(x)-f(x)|<(4M+1)\varepsilon
$$

**证明**

设 $x \in[0,1]$，则有

$$
\begin{align}
f*g(x) &= \int_{-1}^{1} f(x-y)g(y)\mathrm{d} y \\
&= \int_{-\delta}^{\delta}f(x-y)g(y)\mathrm{d} y+\int_{[-1,-\delta]\cup[\delta,1]}f(x-y)g(y)\mathrm{d} y
\end{align}
$$

根据恒等逼近的性质，当 $\delta<|y|<1$ 时，$g(y)<\varepsilon$，从而

$$
\int_{[-1,-\delta]\cup[\delta,1]}|f(x-y)|g(y)\mathrm{d} y\leq 2(1-\delta)M\varepsilon<2M\varepsilon
$$

根据一致连续性，我们有

$$
\int_{-\delta}^{\delta}(f(x)-\varepsilon)g(y)\mathrm{d} y \leq\int_{-\delta}^{\delta}f(x-y)g(y)\mathrm{d} y\leq \int_{-\delta}^{\delta}(f(x)+\varepsilon)g(y)\mathrm{d} y
$$

由于 $1-2\varepsilon\leq\int_{-\delta}^{\delta}g\leq 1$，因此

$$
\int_{-\delta}^{\delta}(f(x)+\varepsilon)g(y)\mathrm{d} y\leq f(x)+\varepsilon
$$

并且

$$
\begin{align}
\int_{-\delta}^{\delta}(f(x)-\varepsilon)g(y)\mathrm{d} y &\geq (f(x)-\varepsilon)(1-2\varepsilon) \\
& =f(x)-2\varepsilon f(x)-\varepsilon+2\varepsilon^{2} \\
& > f(x)-(2M+1)\varepsilon
\end{align}
$$

从而

$$
-(2M+1)\varepsilon-2M\varepsilon< f*g(x)-f(x)< \varepsilon+2M\varepsilon<(4M+1)\varepsilon
$$

这就完成了证明。

把这三个引理结合起来，我们就可以证明 Weierstrass 逼近定理的一个预备形式。

**引理 4**

设 $f\colon \mathbb{R}\to \mathbb{R}$ 是支撑在 $[0,1]$ 上的连续函数，那么对任意 $\varepsilon>0$，存在函数 $p\colon \mathbb{R}\to \mathbb{R}$，它在 $[0,1]$ 上是多项式，并且对任意 $x \in[0,1]$ 有 $|p(x)-f(x)|<\varepsilon$.

**证明**

由于 $f$ 在 $[0,1]$ 上连续，故一致连续且有界，从而存在 $M$ 使得对任意 $x$ 有 $|f(x)|\leq M$，并且对任意 $\varepsilon>0$，存在 $0<\delta<1$ 使得对任意 $|x-y|<\delta$ 的 $x,y$ 有 $|f(x)-f(y)|<\varepsilon_{1}=\dfrac{\varepsilon}{4M+1}$.

根据引理 1，存在 $[-1,1]$ 上的多项式 $q$ 使其为 $(\varepsilon_{1},\delta)$-恒等逼近，根据引理 2，卷积 $p=f*q$ 是 $[0,1]$ 上的多项式，再根据引理 3，对任意 $x \in[0,1]$ 有

$$
|p(x)-f(x)|=|f*q(x)-f(x)|<(4M+1)\varepsilon_{1}=\varepsilon
$$

这就完成了证明。

现在我们要对上述结果进行改进，使其成为真正的 Weierstrass 逼近定理。

**引理 5**

设 $f\colon [0,1]\to \mathbb{R}$ 是连续函数，$f(0)=f(1)=0$，那么定义为

$$
F(x)=\begin{cases}
f(x) &, x \in[0,1] \\
0 &, x \not\in [0,1]
\end{cases}
$$

的函数 $F\colon \mathbb{R}\to \mathbb{R}$ 在 $\mathbb{R}$ 上连续（ $F$ 称为 $f$ 的**零延拓**）。

**证明**

显然 $F$ 在 $\mathbb{R}\setminus\{ 0,1 \}$ 上连续，现在我们要证

$$
\lim_{ x \to 0;x \in \mathbb{R} } F(x)=F(0)
$$

我们考虑左右极限。当 $x<0$ 时，$F(x)=0$，故极限为 $0=F(0)$. 当 $0<x<1$ 时，$F(x)=f(x)$，由 $f$ 的连续性知极限为 $f(0)=F(0)$，即证。$x=1$ 处的极限同理。

结合引理 4 和 5，我们就有如下结果：

**引理 6**

设 $f\colon [0,1]\to \mathbb{R}$ 是连续函数，并且 $f(0)=f(1)=0$，那么对任意 $\varepsilon>0$，存在多项式 $p\colon [0,1]\to \mathbb{R}$ 使得对任意 $x \in[0,1]$ 有 $|p(x)-f(x)|<\varepsilon$.

下面，我们把条件 $f(0)=f(1)=0$ 去掉，从而可以将其应用于更广的函数类。

**引理 7**

设 $f\colon [0,1]\to \mathbb{R}$ 是连续函数，那么对任意 $\varepsilon>0$，存在多项式 $p\colon [0,1]\to \mathbb{R}$ 使得对任意 $x \in[0,1]$ 有 $|p(x)-f(x)|<\varepsilon$.

**证明**

定义函数 $g\colon [0,1]\to \mathbb{R}$ 为

$$
g(x)=f(x)-f(0)-x(f(1)-f(0))
$$

那么 $g$ 在 $[0,1]$ 上连续，并且 $g(0)=g(1)=0$，从而根据引理 6，有多项式 $q\colon [0,1]\to \mathbb{R}$ 使得对任意 $x \in[0,1]$ 有

$$
|q(x)-g(x)|=|q(x)+f(0)+x(f(1)-f(0))-f(x)|<\varepsilon
$$

令 $p(x)=q(x)+f(0)+x(f(1)-f(0))$，则 $p\colon [0,1]\to \mathbb{R}$ 也是多项式，并且有

$$
|p(x)-f(x)|=|q(x)-g(x)|<\varepsilon
$$

这就完成了证明。

最后，我们把函数的定义域扩张为 $[a,b]$，就得到了完整的 Weierstrass 逼近定理。

**定理 16.6.2** Weierstrass 逼近定理

设实数 $a<b$，函数 $f\colon [a,b]\to \mathbb{R}$ 是连续函数，那么对任意 $\varepsilon>0$ 都存在 $[a,b]$ 上的多项式 $p$ 使得 $d_{\infty}(p,f)<\varepsilon$.

**证明**

定义函数 $g\colon [0,1]\to \mathbb{R}$ 为

$$
g(x)=f(a+(b-a)x)
$$

则 $g$ 是连续函数，根据引理 7，有 $[0,1]$ 上的多项式 $q$ 使得 $d_{\infty}(q,g)<\varepsilon$.

令

$$
p(x)=q\left( \dfrac{x-a}{b-a} \right)
$$

则 $p$ 是 $[a,b]$ 上的多项式，并且 $d_{\infty}(p,f)=d_{\infty}(q,g)<\varepsilon$，这就完成了证明。

注意，Weierstrass 逼近定理只适用于紧致集上的连续函数，我们可以在证明过程中看出原因：紧致集上的连续函数一定是一致连续的，这是引理 3 成立的条件。

上述定理还可以推广到 $\mathbb{R}^{n}$ 上。设 $K\subset \mathbb{R}^{n}$ 是一个紧致集，$f\colon K\to \mathbb{R}$ 是连续函数，那么对任意 $\varepsilon>0$，都存在一个 $n$ 元多项式 $p\colon K\to \mathbb{R}$ 使得 $d_{\infty}(p,f)<\varepsilon$. 这个推广的定理可以通过对上面的论证进行更复杂的变动来证明。