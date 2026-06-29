本章我们来讨论 Fourier 分析——特别是 Fourier 变换与复分析的联系。为此，我们将首先建立周期函数的 Fourier 级数理论，接着将其推广到一般的具有特定增长条件函数的 Fourier 变换。我们将看到复曲线积分是如何在重要定理（如 Fourier 反演定理，Poisson 求和公式等）的证明中发挥作用的，并且我们还将证明：一个实值函数能否扩张为一个全纯函数，取决于它的 Fourier 变换在无穷远处的衰减速度。

# Section 1: Fourier 级数

在微积分学中我们已经对连续周期函数的 Fourier 级数做了一些研究。特别地，对于周期为 $L$ 的复值函数 $f$，它的 Fourier 系数定义为

$$
\begin{gather}
a_{n}=\dfrac{1}{L} \int_{0}^{L} f(x) e^{-2\pi i nx /L} \mathrm{d} x
\end{gather}
$$

因此为了使以上积分有定义，我们需要对 $f$ 的可积性做一定的假设。为了保持理论的简洁性，在前几节中我们将假设 $f$ 至少是 **Riemann 可积**的。这就是说，对于有界实值函数 $f$，对任意 $\varepsilon>0$，存在 $[0,L]$ 的一个划分 $\mathbf{P}=\{ 0=x_{0}<\dots <x_{N}=L \}$ 使得相应的 Darboux 上和 $U(f,\mathbf{P})$ 与下和 $L(f,\mathbf{P})$ 之差小于 $\varepsilon$. 此外，复值函数 Riemann 可积当且仅当它的实部和虚部均 Riemann 可积。

定义在 $\mathbb{R}$ 上的 $2\pi$-周期函数、定义在长度 $2\pi$ 的区间上的函数，以及定义在单位圆 $S^{1}=\{ z \mid |z|=1 \}$ 上的函数之间有一个自然的联系。下面我们来解释这一关系。

圆 $S^{1}$ 上的点具有形式 $e^{i\theta}$，其中 $\theta \in \mathbb{R}$ 在相差一个 $2\pi$ 的整数倍下是唯一的。设 $F$ 是 $S^{1}$ 上的函数，那么我们可以定义

$$
\begin{gather}
f(\theta)=F(e^{i\theta})
\end{gather}
$$

于是 $f$ 就是定义在 $\mathbb{R}$ 上的 $2\pi$-周期函数，并且 $f$ 与 $F$ 的可积性与连续性是完全相同的。由于 $f$ 是 $2\pi$-周期的，因此我们可以将 $f$ 限制在一个长度 $2\pi$ 的区间上，例如 $[0,2\pi],[-\pi,\pi]$ 等，而仍然与圆上的函数 $F$ 一致。我们注意到 $f$ 在区间两端的取值必定相同，因为它们对应于圆上的同一点。反之，任何满足 $f(0)=f(2\pi)$ 的函数 $f\colon[0,2\pi]\to \mathbb{C}$ 都可以扩张成一个 $\mathbb{R}$ 上的 $2\pi$-周期函数，从而对应于一个 $S^{1}$ 上的函数。特别地，$[0,2\pi]$ 上的连续函数 $f$ 对应于圆上的一个连续函数，当且仅当 $f(0)=f(2\pi)$.

根据上面的讨论，我们将以上三种函数视为同一类数学对象，并不再区分三种术语。

现在，我们给出 Fourier 级数的正式定义。

**定义 7.1.1** Fourier 级数（Fourier Series）

设 $f$ 是定义在长度 $L$ 的区间 $[a,b]$ 上的 Riemann 可积函数，则 $f$ 的第 $n$ 个 **Fourier 系数**定义为

$$
\begin{gather}
\hat{f}(n)=\dfrac{1}{L} \int_{a}^{b} f(x) e^{-2\pi inx /L}\mathrm{d} x
\end{gather}
$$

$f$ 的 **Fourier 级数**定义为形式级数

$$
\begin{gather}
f(x) \sim \sum_{n=-\infty}^{\infty} \hat{f}(n) e^{2\pi inx /L}
\end{gather}
$$

注意，我们在这里并没有分析该级数的收敛性，因此目前该级数完全是形式的，因此我们使用 $\sim$ 而非等号来连接 $f(x)$ 与它的 Fourier 级数。

我们也可以对圆上的函数定义 Fourier 级数。根据前文的讨论，我们可以将其对应为一个 $2\pi$-周期函数 $f$，并在任意一个长度 $2\pi$ 的区间上计算 $f$ 的 Fourier 系数。根据 $f$ 的周期性，定义中积分的值与区间的选取无关，因此圆上函数的 Fourier 级数是良定的。

Fourier 分析中的一个基本问题是：在什么条件下，函数 $f$ 的 Fourier 级数收敛于 $f$？这里我们需要澄清两个设定：其一是级数的部分和，我们定义它为对称和

$$
\begin{gather}
S_{N}(f)(x)=\sum_{n=-N}^{N} \hat{f}(n) e^{2\pi i nx /L}
\end{gather}
$$

其二是级数的收敛，在本章中，我们将看到对这一点的多种解释。这个问题的解可能非常困难，也可能相对容易，这取决于我们期望级数以何种方式收敛，或对函数 $f$ 施加了哪些限制。

现在我们暂时把收敛性放在一边，转而考虑另一个基础问题：如果我们可以把 Fourier 级数视为函数 $f$ 在频率基 $e^{2\pi inx /L}$ 下的表示，那么这一表示是否是忠实的？换句话说，函数的 Fourier 系数是否能够完全确定一个函数？精确地来说，应当是确定函数的等价类——两个函数属于同一类如果仅在“测度零集”上不同——因为 Fourier 系数是由积分定义的。下面的定理肯定了这一点。

**定理 7.1.2**

设 $f$ 是圆上的 Riemann 可积函数，对 $n \in \mathbb{Z}$ 有 $\hat{f}(n)=0$，那么 $f$ 在连续点 $\theta_{0}$ 上有 $f(\theta_{0})=0$.

于是，根据 Riemann 可积函数的 Lebesgue 准则，我们可以判断 $f$ 在几乎所有点上为零。

**证明**

我们首先假设 $f$ 是实值函数，并使用反证法。我们可以不失一般性地假设 $f$ 定义在 $[-\pi,\pi]$ 上，在 $\theta_{0}=0$ 点连续，且 $f(0)>0$. 证明的思路是选取一系列在 $0$ 附近达到最大值的三角多项式 $p_{k}$ 使得 $\int p_{k}(\theta)f(\theta)\mathrm{d}\theta \to \infty$，这就与我们的假设矛盾。

由于 $f$ 在 $0$ 处连续，故存在 $0<\delta\leq \pi /2$ 使得对 $|\theta|<\delta$ 有 $f(\theta)>f(0) /2$. 定义

$$
\begin{gather}
p(\theta)=\varepsilon+\cos\theta
\end{gather}
$$

其中 $\varepsilon>0$ 满足当 $\delta\leq|\theta|\leq \pi$ 时有 $|p(\theta)|<1-\varepsilon /2$. 再取 $0<\eta<\delta$，使得当 $|\theta|<\eta$ 时有 $p(\theta)\geq 1+\varepsilon /2$. 最后，定义

$$
\begin{gather}
p_{k}(\theta)=p(\theta)^{k}
\end{gather}
$$

以及 $B>0$ 满足 $|f(\theta)|\leq B$. 容易看出，每个 $p_{k}$ 都是三角多项式，从而对任意 $k$ 有

$$
\begin{gather}
\int_{-\pi}^{\pi} p_{k}(\theta)f(\theta)\mathrm{d} \theta=0
\end{gather}
$$

然而，我们有如下的估计

$$
\begin{gather}
\left\lvert  \int_{\delta\leq|\theta|\leq \pi} p_{k}(\theta)f(\theta)\mathrm{d} \theta  \right\rvert \leq 2\pi B(1-\varepsilon /2)^{k} \to 0
\end{gather}
$$

此外，$\delta$ 的选取使得在 $|\theta|<\delta$ 时 $p(\theta)\geq 0$ 且 $f(\theta)\geq 0$，因此

$$
\begin{gather}
\int_{\eta\leq|\theta|<\delta} p_{k}(\theta)f(\theta)\mathrm{d} \theta\geq 0
\end{gather}
$$

最后，我们有

$$
\begin{gather}
\int_{|\theta|<\eta} p_{k}(\theta)f(\theta)\mathrm{d} \theta\geq \eta f(0) (1+\varepsilon /2)^{k} \to \infty
\end{gather}
$$

这表明 $\int p_{k}(\theta)f(\theta)\mathrm{d}\theta\to \infty$，与假设矛盾。

如果 $f$ 是复值函数，令 $f=u+iv$，则

$$
\begin{gather}
u=\dfrac{f+\overline{f}}{2}, \quad v=\dfrac{f-\overline{f}}{2i}
\end{gather}
$$

由于 $\hat{\overline{f}}(n)=\overline{\hat{f}(-n)}$，因此 $u,v$ 的 Fourier 系数均为零，根据上面的证明，即证 $f$ 在连续点处等于零。这就完成了证明。

**定理 7.1.3**

设 $f$ 是圆上的连续函数，对 $n \in \mathbb{Z}$ 有 $\hat{f}(n)=0$，那么 $f=0$ 为常数。

下一个推论回答了前面提到的基本收敛问题中最简单的那部分：Fourier 级数的绝对收敛蕴含一致收敛。

**定理 7.1.4**

设 $f$ 是圆上的连续函数且 $f$ 的 Fourier 级数绝对收敛，则 Fourier 级数一致收敛于 $f$. 这就是说

$$
\begin{gather}
\lim_{ N \to \infty } S_{N}(f)(\theta)=f(\theta)
\end{gather}
$$

对 $\theta \in S^{1}$ 一致。

**证明**

根据假设，我们有 $\sum_{n=-\infty}^{\infty}|\hat{f}(n)|<\infty$，这表明级数

$$
\begin{gather}
\sum_{n=-\infty}^{\infty} \hat{f}(n) e^{in\theta}=\lim_{ N \to \infty } \sum_{n=-N}^{N} \hat{f}(n)e^{in\theta}
\end{gather}
$$

绝对且一致收敛于圆上的连续函数 $g$. 此外，根据一致收敛性，$g$ 的 Fourier 系数就是 $\hat{f}(n)$，因为我们可以交换求和与积分的顺序。于是，将定理 7.1.3 应用到函数 $f-g$ 上即得 $f=g$.

现在我们要问，在什么条件下可以使 $f$ 的 Fourier 级数绝对收敛？事实表明，$f$ 的光滑性直接影响到 Fourier 系数的衰减速度，并且 $f$ 越光滑，系数衰减的速度越快。下面我们来定量地描述这一行为。

**定义 7.1.5**

设 $f,g$ 在 $x=a$ 的邻域中有定义，称 $x\to a$ 时 $f(x)=O(g(x))$，如果存在 $C>0$ 以及 $a$ 的一个邻域，在其中有 $|f(x)|\leq C|g(x)|$.

**定理 7.1.6**

设 $f$ 在圆上二次连续可微，则当 $\lvert n \rvert \to \infty$ 时有

$$
\begin{gather}
\hat{f}(n)=O\left( \dfrac{1}{|n|^{2}} \right)
\end{gather}
$$

从而 $f$ 的 Fourier 级数绝对且一致收敛于 $f$.

**证明**

我们对 $n\neq 0$ 时的 Fourier 系数进行二次分部积分，得到

$$
\begin{align}
2\pi \hat{f}(n)&=\int_{0}^{2\pi} f(\theta) e^{-in\theta}\mathrm{d} \theta \\
&=\dfrac{1}{in} \int_{0}^{2\pi} f'(\theta)e^{-in\theta}\mathrm{d} \theta \\
&=\dfrac{-1}{n^{2}} \int_{0}^{2\pi} f''(\theta)e^{-in\theta}\mathrm{d} \theta
\end{align}
$$

由于 $f''$ 在 $[0,2\pi]$ 上连续，从而有界，因此存在 $C>0$ 使得

$$
\begin{gather}
2\pi |\hat{f}(n)|\leq \dfrac{1}{|n|^{2}} \int_{0}^{2\pi} |f''(\theta)|\mathrm{d} \theta\leq \dfrac{C}{|n|^{2}}
\end{gather}
$$

由于级数 $\sum 1 /n^{2}$ 收敛，因此 $f$ 的 Fourier 级数绝对收敛，这就完成了证明。

在以上定理的证明中，我们还可得到一个恒等式

$$
\begin{gather}
\widehat{f'}(n)=in \hat{f}(n)
\end{gather}
$$

当 $n\neq 0$ 时证明如上所示，当 $n=0$ 时有 $\widehat{f'}(0)=0$. 因此如果 $f$ 可微，并且 $f \sim \sum a_{n}e^{in\theta}$，那么 $f' \sim \sum a_{n} in e^{in\theta}$；如果进一步有 $f$ 二次可微，那么 $f'' \sim \sum a_{n}(in)^{2}e^{in\theta}$，以此类推。更强的光滑性蕴含更快的系数衰减速度。

# Section 2: 卷积

两个函数的**卷积**的概念在 Fourier 分析中起着重要作用，其定义如下：

**定义 7.2.1** 卷积（convolution）

设 $f,g$ 是 $2\pi$-周期的 Riemann 可积函数，定义其**卷积**为

$$
\begin{gather}
(f*g)(x)=\dfrac{1}{2\pi}\int_{-\pi}^{\pi} f(y)g(x-y)\mathrm{d} y
\end{gather}
$$

由于两个可积函数的乘积是可积的，因此以上积分是良定的。

下面我们给出卷积的一些基本性质。

**定理 7.2.2**

设 $f,g,h$ 是 $2\pi$-周期的 Riemann 可积函数，则：

1. $f*(g+h)=f*g+f*h$
2. 对 $c \in \mathbb{C}$ 有 $(cf)*g=c(f*g)=f*(cg)$
3. $f*g=g*f$
4. $(f*g)*h=f*(g*h)$
5. $f*g$ 是连续函数
6. $\widehat{f*g}(n)=\hat{f}(n)\hat{g}(n)$

性质 1-4 描述了卷积的代数性质：分配性、交换性、结合性；性质 5 显示了一个重要的原则：卷积 $f*g$ 比 $f$ 和 $g$ 更为光滑；而性质 6 是 Fourier 分析的核心：用术语来说，它表明 Fourier 变换将时域上的卷积转换为频域上的乘积，反之亦然。

**证明**

性质 1 和 2 直接由积分的线性性得到。对于剩下的性质，我们首先对连续函数 $f,g$ 进行证明，在这种情况下，根据 Fubini 定理，我们可以自由地交换积分的顺序。

(3). 设 $F(y)=f(y)g(x-y)$，则 $F$ 连续并且是 $2\pi$-周期的，于是我们做反射 $y\mapsto -y$，并复合一个平移 $y\mapsto y-x$，即得

$$
\begin{gather}
(f*g)(x)= \dfrac{1}{2\pi} \int_{-\pi}^{\pi} F(y)\mathrm{d} y= \dfrac{1}{2\pi} \int_{-\pi}^{\pi} F(x-y)\mathrm{d} y=(g*f)(x)
\end{gather}
$$

(4). 我们有

$$
\begin{align}
((f*g)*h)(x) &= \dfrac{1}{2\pi} \int_{-\pi}^{\pi} \left( \dfrac{1}{2\pi} \int_{-\pi}^{\pi} f(z)g(y-z)\mathrm{d} z \right)h(x-y) \mathrm{d} y \\
&= \dfrac{1}{2\pi} \int_{-\pi}^{\pi} f(z) \left( \dfrac{1}{2\pi} \int_{-\pi}^{\pi}  g(y)h(x-z-y) \mathrm{d} y \right) \mathrm{d} z \\
&= \dfrac{1}{2\pi} \int_{-\pi}^{\pi} f(z) (g*h)(x-z) \mathrm{d} z \\
&=(f*(g*h))(x)
\end{align}
$$

其中第二步我们做了变量替换 $y\mapsto y+z$ 并使用了性质：$2\pi$-周期函数在任意一个长度 $2\pi$ 的区间上的积分都相同。

(5). 设 $x_{1},x_{2} \in \mathbb{R}$，我们有

$$
\begin{gather}
(f*g)(x_{1})-(f*g)(x_{2})=\dfrac{1}{2\pi} \int_{-\pi}^{\pi} f(y)(g(x_{1}-y)-g(x_{2}-y)) \mathrm{d} y
\end{gather}
$$

由于 $g$ 连续，于是它在有界闭区间上一致连续。又因为 $g$ 是周期的，因此它在 $\mathbb{R}$ 上一致连续。于是，给定 $\varepsilon>0$，存在 $\delta>0$ 使得 $|x_{1}-x_{2}|<\delta$ 蕴含 $|g(x_{1})-g(x_{2})|<\varepsilon$，从而有

$$
\begin{align}
\lvert (f*g)(x_{1})-(f*g)(x_{2}) \rvert &\leq \dfrac{1}{2\pi} \int_{-\pi}^{\pi} |f(y)||g(x_{1}-y)-g(x_{2}-y)| \mathrm{d} y \\
&\leq \dfrac{\varepsilon}{2\pi} \int_{-\pi}^{\pi} |f(y)|\mathrm{d} y \\
&\leq B\varepsilon
\end{align}
$$

其中 $|f(x)|\leq B$ 对 $x \in \mathbb{R}$ 成立。

(6). 我们有

$$
\begin{align}
\widehat{f*g}(n) &=\dfrac{1}{2\pi} \int_{-\pi}^{\pi} \left( \dfrac{1}{2\pi} \int_{-\pi}^{\pi} f(y)g(x-y) \mathrm{d} y \right) e^{-inx} \mathrm{d} x \\
&=\dfrac{1}{2\pi} \int_{-\pi}^{\pi} f(y) e^{-iny} \left( \dfrac{1}{2\pi} \int_{-\pi}^{\pi} g(x-y)e^{-in(x-y)} \mathrm{d} x \right) \mathrm{d} y \\
&= \hat{f}(n)\hat{g}(n)
\end{align}
$$

对于一般的情况，我们需要以下的逼近定理：

**定理 7.2.3**

设 $f$ 在圆上 Riemann 可积，其上界为 $B$，则存在一列圆上的连续函数 $(f_{k})$ 使得对任意 $k$ 有

$$
\begin{gather}
\sup_{x \in [-\pi,\pi]} |f_{k}(x)|\leq B
\end{gather}
$$

并且

$$
\begin{gather}
\lim_{ k \to \infty } \int_{-\pi}^{\pi} |f(x)-f_{k}(x)|\mathrm{d} x=0
\end{gather}
$$

这就是说，圆上的有界连续函数构成的集合 $C_{b}$ 按 $L^{1}$ 度量在圆上的 Riemann 可积函数集合 $\mathcal{R}$ 中稠密。

**证明**

给定 $\varepsilon>0$，由于 $f$ Riemann 可积，故存在 $[-\pi,\pi]$ 的一个划分

$$
\begin{gather}
\mathbf{P}=\{ -\pi=x_{0}<x_{1}<\dots<x_{n}=\pi \}
\end{gather}
$$

使得

$$
\begin{gather}
U(f,\mathbf{P})-L(f,\mathbf{P})<\dfrac{\varepsilon}{2}
\end{gather}
$$

我们取

$$
\begin{gather}
f^{*}(x)=\sum_{k=1}^{n} (\inf_{x \in [x_{k-1},x_{k}]} f(x)) \chi_{[x_{k-1},x_{k}]}(x)
\end{gather}
$$

则 $f^{*}$ 是一个分段常值函数，$|f^{*}(x)|\leq B$，并且

$$
\begin{gather}
\int_{-\pi}^{\pi} |f(x)-f^{*}(x)| \mathrm{d} x<\dfrac{\varepsilon}{2}
\end{gather}
$$

现在我们来修改 $f^{*}$ 使其成为一个连续函数 $\tilde{f}$. 令 $\delta>0$ 小于划分 $\mathbf{P}$ 中最小区间的长度，在 $[x_{k}-\delta,x_{k}+\delta]$ 上用斜线段连接 $f^{*}(x_{k}-\delta)$ 和 $f^{*}(x_{k}+\delta)$，如图所示：

![](7-1.png)

由于 $f^{*}$ 与 $\tilde{f}$ 仅在 $n$ 个长度 $2\delta$ 的区间上不同，通过取充分小的 $\delta$，我们可以使

$$
\begin{gather}
\int_{-\pi}^{\pi} |f^{*}(x)-\tilde{f}(x)|\mathrm{d} x<\dfrac{\varepsilon}{2}
\end{gather}
$$

从而

$$
\begin{gather}
\int_{-\pi}^{\pi} |f(x)-\tilde{f}(x)|\mathrm{d} x<\varepsilon
\end{gather}
$$

令 $\varepsilon=1 /k$，取 $f_{k}=\tilde{f}$ 就完成了证明。

**证明**（7.2.2）

利用定理 7.2.3 构造 $L^{1}$ 收敛于 $f,g$ 的连续函数列 $(f_{k})$ 和 $(g_{k})$，则我们有

$$
\begin{gather}
f*g-f_{k}*g_{k}=(f-f_{k})*g+f_{k}*(g-g_{k})
\end{gather}
$$

由于

$$
\begin{align}
\lvert ((f-f_{k})*g)(x) \rvert &\leq \dfrac{1}{2\pi} \int_{-\pi}^{\pi} |f(y)-f_{k}(y)||g(x-y)|\mathrm{d} y \\
&\leq \dfrac{B}{2\pi} \int_{-\pi}^{\pi} |f(y)-f_{k}(y)|\mathrm{d} y \to 0
\end{align}
$$

因此 $(f-f_{k})*g\to 0$ 对 $x$ 一致，同理 $f_{k}*(g-g_{k})\to 0$ 对 $x$ 一致，这表明 $f_{k}*g_{k}\to f*g$ 对 $x$ 一致。这就证明了性质 3, 4, 5.

对于性质 6，由于 $f_{k}*g_{k}$ 一致收敛于 $f*g$，通过交换极限与积分，我们有 $\widehat{f_{k}*g_{k}}(n)\to \widehat{f*g}(n)$. 此外，我们有

$$
\begin{align}
\lvert \hat{f}(n)-\hat{f}_{k}(n) \rvert &\leq \dfrac{1}{2\pi} \int_{-\pi}^{\pi} |f(x)-f_{k}(x)|\mathrm{d} x \to 0
\end{align}
$$

同理 $\hat{g}_{k}(n)\to \hat{g}(n)$，这就完成了证明。

在我们对 Fourier 级数的研究中，卷积自然地出现在级数的部分和中：

$$
\begin{align}
S_{N}(f)(x) &= \sum_{n=-N}^{N} \hat{f}(n) e^{inx} \\
&= \sum_{n=-N}^{N} \left( \dfrac{1}{2\pi} \int_{-\pi}^{\pi} f(y)e^{-iny} \mathrm{d} y \right) e^{inx} \\
&=\dfrac{1}{2\pi} \int_{-\pi}^{\pi} f(y) \sum_{n=-N}^{N} e^{in(x-y)} \mathrm{d} y \\
&=(f*D_{N})(x)
\end{align}
$$

其中

$$
\begin{gather}
D_{N}(x)=\sum_{n=-N}^{N} e^{inx}=\dfrac{\sin((N+1 /2)x)}{\sin(x /2)}
\end{gather}
$$

称为第 $N$ 个 **Dirichlet 核**。因此，我们就将 Fourier 级数收敛的研究转化为了对卷积 $f*D_{N}$ 的研究。为此，我们首先来研究一般的积分核 $K_{n}$.

**定义 7.2.4** 恒等逼近（approximation to the identity）

圆上的一族核函数 $(K_{n})$ 称为是一个**恒等逼近**，如果它满足：

1. 对任意 $n$ 有 $\displaystyle \dfrac{1}{2\pi}\int_{-\pi}^{\pi} K_{n}(x)\mathrm{d}x=1$
2. 存在 $M>0$ 使得对任意 $n$ 有 $\displaystyle \int_{-\pi}^{\pi}|K_{n}(x)|\mathrm{d}x\leq M$
3. 对任意 $\delta>0$ 有 $\displaystyle \lim_{ n \to \infty }\int_{\delta\leq|x|\leq \pi} |K_{n}(x)|\mathrm{d}x=0$

这一定义名字的来源由以下定理给出：

**定理 7.2.5**

设 $(K_{n})$ 是一个恒等逼近，$f$ 是圆上的 Riemann 可积函数，则

$$
\begin{gather}
\lim_{ n \to \infty } (f*K_{n})(x)=f(x)
\end{gather}
$$

对 $f$ 的连续点 $x$ 成立。如果 $f$ 是连续函数，那么上式关于 $x$ 一致。

这就是说，恒等逼近中的恒等元（identity）指的是卷积的恒等元，称为 Dirac delta 函数 $\delta$，尽管它不是通常意义上的函数，而是一个分布。熟悉信号分析的读者了解，$\delta$ 函数的一个核心性质就是它能够“分离”出函数在某点的值：

$$
\begin{gather}
(f*\delta)(x)=\int_{-\infty}^{\infty} f(y)\delta(x-y)\mathrm{d} y=f(x)
\end{gather}
$$

作为对 $\delta$ 函数的一个近似，恒等逼近 $K_{n}$ 也部分地具有这一性质，其第三个性质正反映了这一点。

**证明**

设 $\varepsilon>0$，$f$ 在 $x$ 处连续，则存在 $\delta>0$ 使得 $|y|<\delta$ 蕴含

$$
\begin{gather}
\lvert f(x-y)-f(x) \rvert <\varepsilon
\end{gather}
$$

于是我们有

$$
\begin{align}
\lvert (f*K_{n})(x)-f(x) \rvert &= \dfrac{1}{2\pi} \left\lvert  \int_{-\pi}^{\pi} K_{n}(y)(f(x-y)-f(x))\mathrm{d} y  \right\rvert  \\
&\leq \dfrac{1}{2\pi} \int_{|y|<\delta} |K_{n}(y)||f(x-y)-f(x)|\mathrm{d} y \\
&+ \dfrac{1}{2\pi} \int_{\delta\leq|y|\leq \pi} |K_{n}(y)||f(x-y)-f(x)|\mathrm{d} y \\
&\leq \dfrac{M\varepsilon}{2\pi}+\dfrac{B}{\pi} \int_{\delta\leq|y|<\pi} |K_{n}(y)|\mathrm{d} y
\end{align}
$$

根据恒等逼近的性质 3，当 $n\to \infty$ 时不等式右侧的第二项将消失，于是存在 $C>0$，当 $n$ 充分大时就有

$$
\begin{gather}
\lvert (f*K_{n})(x)-f(x) \rvert <C\varepsilon
\end{gather}
$$

即证 $(f*K_{n})(x)\to f(x)$. 如果 $f$ 是连续函数，那么 $f$ 在圆上一致连续，从而 $\delta$ 可以被选取使得它与 $x$ 无关，这就证明了极限的一致性。

现在一个自然的问题，就是问 Dirichlet 核 $D_{N}$ 是否是一个恒等逼近？如果答案是肯定的，那么定理 7.2.5 就表明 $f$ 的 Fourier 级数在 $f$ 的连续点收敛于 $f$. 不幸的是，这一结论并不成立。事实上，我们有

$$
\begin{gather}
\int_{-\pi}^{\pi} |D_{N}(x)|\mathrm{d} x\geq c\log N
\end{gather}
$$

当 $N$ 充分大时成立。这表明，Fourier 级数的逐点收敛是一个复杂的问题，甚至可能在连续点上失效。Carleson 证明了，对于连续函数（更一般地，$L^{2}$ 函数），我们所能达到的最好结果就是几乎处处收敛。

# Section 3: Fourier 级数的收敛性

既然 Fourier 的逐点收敛可能在某些点上失效，那么我们就希望按不同的方法来定义极限

$$
\begin{gather}
\lim_{ N \to \infty } S_{N}(f)=f
\end{gather}
$$

使得上式成立。在本节中，我们将给出三种不同的诠释，分别是 **Cesaro 和**、**Abel 和**以及 $L^{2}$ 收敛。

## Cesaro 和

Cesaro 求和的最初动机是为了给一些发散级数，例如

$$
\begin{gather}
1-1+1-1+\cdots
\end{gather}
$$

赋予一个合理的“广义和”。对于一个级数 $\sum c_{n}$，通常的极限理论是考虑级数的部分和序列 $s_{n}=\sum_{k=0}^{n}c_{k}$ 的极限。然而，对于上面例子中的级数，它的部分和不断地在 $0$ 和 $1$ 之间摆动，因此，直观上我们可以为其赋值为 $\dfrac{1}{2}$，这一过程正是由 Cesaro 求和实现的。

**定义 7.3.1** Cesaro 和

设 $\sum_{n=0}^{\infty}c_{n}$ 是一个复数级数，$(s_{n})$ 为其部分和序列，定义 $(s_{n})$ 的第 $N$ 个 **Cesaro 平均**，或者 $\sum c_{n}$ 的第 $N$ 个 **Cesaro 部分和**为

$$
\begin{gather}
\sigma_{N}=\dfrac{s_{0}+s_{1}+\dots+s_{N-1}}{N}
\end{gather}
$$

如果 $\sigma_{N}$ 收敛于 $\sigma$，则称级数 $\sum c_{n}$ 的 **Cesaro 和**为 $\sigma$.

容易证明，如果级数收敛于 $s$，那么在 Cesaro 求和意义下级数也收敛于 $s$，因此 Cesaro 求和是对原有极限概念的一个推广。

在 Fourier 级数的收敛性分析中，Cesaro 求和的表现非常良好，这就是说，其相应的积分核是一个恒等逼近，下面我们就来证明这一点。

根据定义，Fourier 级数的 Cesaro 部分和为

$$
\begin{align}
\sigma_{N}(f)(x) &=\dfrac{S_{0}(f)(x)+\dots+S_{N-1}(f)(x)}{N} \\
&=\left( f* \dfrac{D_{0}+\dots+D_{N-1}}{N} \right)(x) \\
&=(f*F_{N})(x)
\end{align}
$$

其中 $F_{N}$ 称为第 $N$ 个 **Fejer 核**。

**引理 7.3.2**

对 $N\geq 1$ 有

$$
\begin{gather}
F_{N}(x)=\dfrac{1}{N} \dfrac{\sin^{2}(Nx /2)}{\sin^{2}(x /2)}
\end{gather}
$$

并且 $(F_{N})$ 是一个恒等逼近。

**证明**

根据定义，我们有

$$
\begin{align}
F_{N}(x) &= \dfrac{1}{N} \sum_{n=0}^{N-1} D_{n}(x) \\
&= \dfrac{1}{N} \sum_{n=0}^{N-1} \sum_{k=-n}^{n} e^{ikx} \\
&= \dfrac{1}{N} \sum_{n=-N}^{N} (N-|n|) e^{inx} \\
&= \dfrac{1}{N} \sum_{n=0}^{N-1} \sum_{m=0}^{N-1} e^{inx}e^{-imx} \\
&= \dfrac{1}{N} \left\lvert  \sum_{n=0}^{N-1} e^{inx}  \right\rvert ^{2} \\
&=\dfrac{1}{N} \dfrac{\sin^{2}(Nx /2)}{\sin^{2}(x /2)}
\end{align}
$$

要证 $F_{N}$ 是恒等逼近，首先注意到恒等逼近的性质 1 中的积分正是 $F_{N}$ 的第 $0$ 个 Fourier 系数，即 $\dfrac{1}{N}(1+\dots+1)=1$. 由于 $F_{N}\geq 0$，因此我们自动得到性质 2（有界性）。最后，当 $\delta\leq |x|\leq \pi$ 时，成立

$$
\begin{gather}
F_{N}(x)\leq \dfrac{1}{N \sin^{2}(\delta /2)}
\end{gather}
$$

从而

$$
\begin{gather}
\lim_{ N \to \infty } \int_{\delta\leq|x|\leq \pi} |F_{N}(x)|\mathrm{d} x=0
\end{gather}
$$

这就完成了证明。

将定理 7.2.5 应用到 Fejer 核上，即得以下的定理：

**定理 7.3.3** Fejer 定理

设 $f$ 是圆上的 Riemann 可积函数，则 $f$ 的 Fourier 级数在其连续点 $x$ 上的 Cesaro 和为 $f(x)$. 此外，如果 $f$ 是连续函数，那么 $f$ 的 Fourier 级数在 Cesaro 和的意义上一致收敛于 $f$.

作为以上定理的推论，我们有以下的结论：

**定理 7.3.4** Weierstrass 逼近定理

设 $f$ 在 $[-\pi,\pi]$ 上连续，$f(-\pi)=f(\pi)$，则对任意 $\varepsilon>0$，存在三角多项式 $P$ 使得对任意 $-\pi\leq x\leq \pi$ 有

$$
\begin{gather}
\lvert f(x)-P(x) \rvert <\varepsilon
\end{gather}
$$

这是因为 $f$ 的 Fourier 级数的部分和是三角多项式，从而其 Cesaro 平均也是三角多项式，后者在 $[-\pi,\pi]$ 上一致收敛于 $f$. 从这一定理，我们也可以得到紧支撑连续函数的 Weierstrass 逼近定理，它的证明思路共分为两步：首先用三角多项式逼近连续函数，然后用 $e^{x}$ 的截断级数（它是一个代数多项式）来逼近三角多项式。

## Abel-Poisson 和

另一种求级数 $\sum c_{n}$ 广义和的方式涉及到幂级数，其动机是，如果级数中的项发散速度不是太快，那么我们引入一个指数衰减项 $r^{n}$（Abel）或者 $e^{-n\delta}$（Poisson），构成一个幂级数

$$
\begin{gather}
A(r)=\sum_{n=0}^{\infty} c_{n} r^{n}
\end{gather}
$$

当极限 $\lim_{ r \to 1- } A(r)$ 存在时，我们就把这个值定义为级数的广义和。对于 Poisson 的形式，我们只需取 $r=e^{-\delta}$，然后令 $\delta\to 0+$ 即可，这两者是等价的。因此，接下来的研究中我们只选用 Abel 的形式。

**定义 7.3.5** Abel 和

设 $\sum_{n=0}^{\infty}c_{n}$ 是一个复数级数，称它的 **Abel 和**为 $s$，如果对任意 $0\leq r<1$，级数的 **Abel 平均**

$$
\begin{gather}
A(r)=\sum_{n=0}^{\infty} c_{n}r^{n}
\end{gather}
$$

收敛，并且

$$
\begin{gather}
\lim_{ r \to 1- } A(r)=s
\end{gather}
$$

我们可以证明，Abel 和是一种比 Cesaro 和更强的求和方法：如果一个级数的 Cesaro 和是 $s$，那么它的 Abel 和也是 $s$. 但反之则不然：级数

$$
\begin{gather}
1-2+3-4+\cdots=\sum_{k=0}^{\infty} (-1)^{k}(k+1)
\end{gather}
$$

的 Abel 和是

$$
\begin{gather}
\lim_{ r \to 1- } \sum_{k=0}^{\infty} (-1)^{k}(k+1)r^{k}=\lim_{ r \to 1- } \dfrac{1}{(1+r)^{2}}=\dfrac{1}{4}
\end{gather}
$$

然而该级数没有 Cesaro 和：其 Cesaro 部分和在正数和 $-\dfrac{1}{2}$ 之间震荡。

对于 Fourier 级数的部分和，我们定义 $f(\theta)\sim \sum a_{n}e^{in\theta}$ 的 Abel 平均为

$$
\begin{gather}
A_{r}(f)(\theta)=\sum_{n=-\infty}^{\infty} a_{n} r^{|n|}e^{in\theta}
\end{gather}
$$

由于 $f$ 可积，因此 $|a_{n}|$ 关于 $n$ 是一致有界的，从而 $A_{r}(f)$ 关于 $0\leq r<1$ 绝对且一致收敛，并且我们有

$$
\begin{align}
A_{r}(f)(\theta) &= \sum_{n=-\infty}^{\infty} r^{|n|} \left( \dfrac{1}{2\pi} \int_{-\pi}^{\pi} f(\varphi)e^{-in\varphi} \mathrm{d} \varphi \right) e^{in\theta} \\
&= \dfrac{1}{2\pi} \int_{-\pi}^{\pi} f(\varphi) \left( \sum_{n=-\infty}^{\infty} r^{|n|} e^{in(\theta-\varphi)} \right) \mathrm{d} \varphi \\
&= (f*P_{r})(\theta)
\end{align}
$$

其中

$$
\begin{gather}
P_{r}(\theta)=\sum_{n=-\infty}^{\infty} r^{|n|}e^{in\theta}=\dfrac{1-r^{2}}{1-2r\cos\theta+r^{2}}
\end{gather}
$$

称为 **Poisson 核**。

**引理 7.3.6**

设 $0\leq r<1$，当 $r\to 1-$ 时 $\{ P_{r} \}$ 是一个恒等逼近。这就是说，$P_{r}$ 均值为 $1$，关于 $r$ 一致有界，并且对任意 $\delta>0$ 有

$$
\begin{gather}
\lim_{ r \to 1- } \int_{\delta\leq|\theta|\leq \pi} |P_{r}(\theta)|\mathrm{d} \theta=0
\end{gather}
$$

**证明**

为证明恒等逼近的性质 1，我们对级数 $\sum_{n=-\infty}^{\infty}r^{|n|}e^{in\theta}$ 做逐项积分（由于级数一致收敛，因此这是可行的），仅有 $n=0$ 这一项为 $2\pi$，其余的项均为零。显然 $P_{r}(\theta)\geq 0$，因此我们自动得到了一致有界性。最后，注意到

$$
\begin{gather}
1-2r\cos\theta+r^{2}=(1-r)^{2}+2r(1-\cos\theta)
\end{gather}
$$

于是当 $1 /2<r<1$ 且 $\delta\leq|\theta|\leq \pi$ 时有

$$
\begin{gather}
1-2r\cos\theta+r^{2}\geq c_{\delta}>0
\end{gather}
$$

从而 $P_{r}(\theta)\leq (1-r^{2}) /c_{\delta}$，这就完成了证明。

结合以上引理以及定理 7.2.5，我们便得到了 Abel 和意义下的 Fourier 级数收敛定理。

**定理 7.3.7**

设 $f$ 是圆上的 Riemann 可积函数，则 $f$ 的 Fourier 级数在其连续点 $\theta$ 上的 Abel 和为 $f(\theta)$. 此外，如果 $f$ 是连续函数，那么 $f$ 的 Fourier 级数在 Abel 和的意义上一致收敛于 $f$.

利用上述定理，我们可以给出圆盘上 **Dirichlet 问题**的解。它说的是，给定函数 $f$，以及单位圆盘

$$
\begin{gather}
D=\{ (r,\theta) \mid 0\leq r<1 \}
\end{gather}
$$

求解 $\overline{D}$ 上带有边界条件 $u(1,\theta)=f(\theta)$ 的稳态热传导方程

$$
\begin{gather}
\Delta u=\dfrac{ \partial ^{2} u }{ \partial x^{2} } +\dfrac{ \partial ^{2} u }{ \partial y^{2} } =0
\end{gather}
$$

其中 $\Delta=\nabla^{2}$ 称为 **Laplace 算子**，满足以上方程的 $u$ 称为**调和函数**。

我们首先给出一种启发式求解方法。应用链式法则，我们将 $\Delta u$ 改写为极坐标形式：

$$
\begin{gather}
\Delta u=\dfrac{ \partial ^{2} u }{ \partial r^{2} } +\dfrac{1}{r} \dfrac{ \partial u }{ \partial r } +\dfrac{1}{r^{2}} \dfrac{ \partial ^{2} u }{ \partial \theta^{2} } 
\end{gather}
$$

根据 $\Delta u=0$ 得到

$$
\begin{gather}
r^{2} \dfrac{ \partial ^{2}u }{ \partial r^{2} } +r \dfrac{ \partial u }{ \partial r } =- \dfrac{ \partial ^{2}u }{ \partial \theta^{2} } 
\end{gather}
$$

做分离变量 $u(r,\theta)=F(r)G(\theta)$，则有

$$
\begin{gather}
\dfrac{r^{2} F''(r)+rF'(r)}{F(r)}=- \dfrac{G''(\theta)}{G(\theta)}
\end{gather}
$$

令上式等于 $\lambda$，我们就得到两个常微分方程

$$
\begin{gather}
G''(\theta)+\lambda G(\theta)=0 \\
r^{2}F''(r)+rF'(r)-\lambda F(r)=0
\end{gather}
$$

由于 $G(\theta)$ 必然是 $2\pi$-周期的，因此 $\lambda\geq 0$，于是有 $\lambda=m^{2}$，并且

$$
\begin{gather}
G(\theta)=Ae^{im\theta}+Be^{-im\theta}
\end{gather}
$$

对于 $\lambda=m^{2}>0$，$F(r)$ 的两个线性无关解分别是 $r^{m}$ 和 $r^{-m}$；当 $m=0$ 时，$F(r)$ 的两个线性无关解是 $1$ 和 $\log r$. 注意到，当 $r\to 0$ 时，$r^{-m}$ 和 $\log r$ 都发散至无穷，这不符合我们的直觉，因此我们将其去除。因此我们便只留下如下的特征函数：

$$
\begin{gather}
u_{m}(r,\theta)=r^{|m|}e^{im\theta} ,\quad m \in \mathbb{Z}
\end{gather}
$$

于是，我们期望 Dirichlet 问题的解具有形式

$$
\begin{gather}
u(r,\theta)=\sum_{m=-\infty}^{\infty} a_{m} r^{|m|} e^{im\theta}
\end{gather}
$$

当 $r=1$ 时，根据边界条件，我们有

$$
\begin{gather}
f(\theta)=\sum_{m=-\infty}^{\infty} a_{m} e^{im\theta}
\end{gather}
$$

这就是说，$a_{m}$ 是 $f$ 的 Fourier 系数，从中我们自然地得到了 Poisson 核：

$$
\begin{gather}
u(r,\theta)=A_{r}(f)(\theta)=(f*P_{r})(\theta)
\end{gather}
$$

下面我们就来严格地证明这一点。

**定理 7.3.8**

设 $f$ 是圆上的 Riemann 可积函数，则定义在 $\overline{D}$ 上的函数

$$
\begin{gather}
u(r,\theta)=(f*P_{r})(\theta)
\end{gather}
$$

满足以下性质：

1. $u$ 在 $D$ 上是调和函数。
2. 如果 $f$ 在 $\theta$ 处连续，那么 $\lim_{ r \to 1- } u(r,\theta)=f(\theta)$. 如果 $f$ 是连续函数，那么以上极限关于 $\theta$ 一致。
3. 如果 $f$ 是连续函数，那么 $u$ 是满足性质 1 和 2 的唯一函数。

**证明**

根据 $u$ 的级数表达式 $\sum_{n=-\infty}^{\infty}a_{n}r^{|n|}e^{in\theta}$，设 $\rho<1$，则在圆盘 $B(0,\rho)$ 内，级数绝对且一致收敛，从而可以逐项求导，这表明 $u$ 在 $D$ 上二次连续可微。再根据 $\Delta u$ 的极坐标形式，通过逐项求导即可证明 $\Delta u=0$.

性质 2 是定理 7.3.7 的一个直接应用。下面我们来证明性质 3. 假设 $v$ 满足性质 1 和 2，那么对 $0<r<1$，$v(r,\theta)$ 有 Fourier 级数

$$
\begin{gather}
v(r,\theta) \sim \sum_{n=-\infty}^{\infty} a_{n}(r) e^{in\theta} ,\quad a_{n}(r)=\dfrac{1}{2\pi}\int_{-\pi}^{\pi} v(r,\theta)e^{-in\theta} \mathrm{d} \theta
\end{gather}
$$

由于

$$
\begin{gather}
\dfrac{ \partial ^{2} v }{ \partial r^{2} } +\dfrac{1}{r} \dfrac{ \partial v }{ \partial r } +\dfrac{1}{r^{2}} \dfrac{ \partial ^{2} v }{ \partial \theta^{2} }=0
\end{gather}
$$

在上式两边乘以 $e^{-in\theta}$ 并对 $\theta$ 积分，就得到

$$
\begin{gather}
a_{n}''(r)+\dfrac{1}{r} a_{n}'(r)-\dfrac{n^{2}}{r^{2}} a_{n}(r)=0
\end{gather}
$$

从而当 $n\neq 0$ 时我们有 $a_{n}(r)=A_{n}r^{n}+B_{n}r^{-n}$. 由于 $v$ 有界，故 $a_{n}(r)$ 是有界的，因此 $B_{n}=0$. 为求解 $A_{n}$，我们令 $r\to 1-$，由于 $v$ 一致收敛于 $f$，我们有

$$
\begin{gather}
A_{n}=\dfrac{1}{2\pi}\int_{-\pi}^{\pi} f(\theta)e^{-in\theta}\mathrm{d} \theta=\hat{f}(n)
\end{gather}
$$

当 $n=0$ 时我们有 $a_{0}(r)=A_{0}+B_{0}\log r$，则同样有 $B_{0}=0$ 且 $A_{0}=\hat{f}(0)$，于是根据 Fourier 级数的唯一性知 $u=v$，这就完成了证明。

## $L^{2}$ 收敛

在所有收敛方式中，适用性最为广泛的一种就是所谓的“按 $L^{2}$ 度量收敛”，这就是以下定理所要说的：

**定理 7.3.9**

设 $f$ 在圆上 Riemann 可积，那么

$$
\begin{gather}
\lim_{ N \to \infty } \dfrac{1}{2\pi} \int_{0}^{2\pi} \lvert f(\theta)-S_{N}(f)(\theta) \rvert ^{2} \mathrm{d} \theta=0
\end{gather}
$$

这一定理的证明的关键是使用向量空间 $\mathcal{R}$ 上的正交性。在 $\mathcal{R}$ 上，我们可以定义内积和范数

$$
\begin{gather}
\langle f,g \rangle =\dfrac{1}{2\pi} \int_{0}^{2\pi} f(\theta) \overline{g(\theta)} \mathrm{d} \theta,\quad \lVert f \rVert =\langle f,f \rangle =\dfrac{1}{2\pi} \int_{0}^{2\pi} |f(\theta)|^{2} \mathrm{d} \theta
\end{gather}
$$

令 $e_{n}(\theta)=e^{in\theta}$，则 $\{ e_{n} \}$ 是一族标准正交向量，即

$$
\begin{gather}
\langle e_{n},e_{m} \rangle = \begin{cases}
1, & n=m \\
0, & n\neq m
\end{cases}
\end{gather}
$$

并且我们注意到计算 $f$ 的 Fourier 系数的过程就等价于将 $f$ 向 $e_{n}$ 做投影：

$$
\begin{gather}
\langle f,e_{n} \rangle =\dfrac{1}{2\pi}\int_{0}^{2\pi} f(\theta)e^{-in\theta}\mathrm{d} \theta=\hat{f}(n)
\end{gather}
$$

设 $a_{n}=\hat{f}(n)$，则 $S_{N}(f)=\sum_{|n|\leq N}a_{n}e_{n}$，根据 $\{ e_{n} \}$ 的正交性，对任意 $|n|\leq N$，我们都有 $f-S_{N}(f)$ 正交于 $e_{n}$，因此我们有

$$
\begin{gather}
\left\langle  f-\sum_{|n|\leq N} a_{n}e_{n},\sum_{|n|\leq N} b_{n}e_{n}  \right\rangle =0
\end{gather}
$$

有两个结论可以从上面的等式中得到。其一是勾股定理：

$$
\begin{align}
\lVert f \rVert ^{2} &= \left\lVert  f-\sum_{|n|\leq N} a_{n}e_{n}  \right\rVert ^{2}+\left\lVert  \sum_{|n|\leq N} a_{n}e_{n}  \right\rVert ^{2} \\
&= \lVert f-S_{N}(f) \rVert ^{2}+\sum_{|n|\leq N} |a_{n}|^{2}
\end{align}
$$

其二是对我们的几何直观的一种确认：$f$ 在 $\{ e_{n} \}_{|n|\leq N}$ 所张成的空间上的正交投影的确是 $S_{N}(f)$.

**引理 7.3.10**

设 $f$ 在圆上 Riemann 可积，其 Fourier 系数为 $a_{n}$，则

$$
\begin{gather}
\lVert f-S_{N}(f) \rVert \leq \left\lVert  f-\sum_{|n|\leq N} c_{n}e_{n}  \right\rVert 
\end{gather}
$$

对任意复数 $c_{n}$ 成立。等式成立当且仅当对任意 $n$ 有 $a_{n}=c_{n}$.

**证明**

对下式应用勾股定理即证：

$$
f-\sum_{|n|\leq N}c_{n}e_{n}=f-S_{N}(f)+\sum_{|n|\leq N} (a_{n}-c_{n})e_{n}
$$

利用引理 7.3.10，我们就可以给出定理 7.3.9 的证明了。其证明分为两步：首先用三角多项式逼近连续函数，然后再用连续函数逼近可积函数。

**证明**（7.3.9）

设 $f$ 在圆上连续，则给定 $\varepsilon>0$，存在三角多项式 $P$ 使得

$$
\begin{gather}
\lvert f(\theta)-P(\theta) \rvert <\varepsilon
\end{gather}
$$

平方并对 $\theta$ 积分即得 $\lVert f-P \rVert<\varepsilon$. 设 $P$ 的次数为 $M$，则根据引理 7.3.10，当 $N>M$ 时我们就有

$$
\begin{gather}
\lVert f-S_{N}(f) \rVert <\varepsilon
\end{gather}
$$

现在设 $f$ 在圆上 Riemann 可积。则我们可以找到有界连续函数 $g$ 使得

$$
\begin{gather}
\int_{0}^{2\pi} |f(\theta)-g(\theta)|\mathrm{d} \theta<\varepsilon^{2}
\end{gather}
$$

于是

$$
\begin{align}
\lVert f-g \rVert ^{2} &= \dfrac{1}{2\pi} \int_{0}^{2\pi} |f(\theta)-g(\theta)|^{2} \mathrm{d} \theta \\
&\leq \dfrac{B}{\pi} \int_{0}^{2\pi} |f(\theta)-g(\theta)|\mathrm{d} \theta \\
&< \dfrac{B}{\pi} \varepsilon^{2}
\end{align}
$$

因此 $\lVert f-g \rVert<C\varepsilon$. 再取三角多项式 $P$ 使得 $\lVert g-P \rVert<\varepsilon$，则我们有

$$
\begin{align}
\lVert f-S_{N}(f) \rVert &\leq \lVert f-g \rVert +\lVert g-S_{n}(f) \rVert  \\
&\leq \lVert f-g \rVert +\lVert g-P \rVert  \\
&\leq (C+1)\varepsilon
\end{align}
$$

这就完成了证明。

此外，利用 $\lVert f-S_{N}(f) \rVert \to 0$ 我们还能得到以下的等式：

**定理 7.3.11** Parseval 恒等式

设 $f$ 是圆上的 Riemann 可积函数，则

$$
\begin{gather}
\sum_{n=-\infty}^{\infty} |\hat{f}(n)|^{2}=\dfrac{1}{2\pi} \int_{0}^{2\pi} |f(\theta)|^{2} \mathrm{d} \theta
\end{gather}
$$

这就是说，Fourier 变换 $f \mapsto \hat{f}$ 是一个从 $\mathcal{R}$ 到 $\ell^{2}(\mathbb{Z})$ 的等距映射。我们说 Riemann 可积函数空间 $\mathcal{R}$ 不是完备的，就是指存在 $(a_{n}) \in\ell^{2}(\mathbb{Z})$，使得 $\sum a_{n}e^{in\theta}$ 不是任何 Riemann 可积函数的 Fourier 级数。这便是促使我们考虑完备空间 $L^{2}([0,2\pi])$ 的根本原因之一。

根据以上定理以及收敛级数的性质，我们立即得到：

**定理 7.3.12** Riemann-Lebesgue 引理

如果 $f$ 在圆上 Riemann 可积，那么当 $|n| \to \infty$ 时有 $\hat{f}(n)\to 0$.

以上定理的一个等价表达是如果 $f$ 在 $[0,2\pi]$ 上可积，则当 $N\to \infty$ 时有

$$
\begin{gather}
\int_{0}^{2\pi} f(\theta)\sin(N\theta) \mathrm{d} \theta \to 0
\end{gather}
$$

且

$$
\begin{gather}
\int_{0}^{2\pi} f(\theta)\cos(N\theta)\mathrm{d} \theta \to 0
\end{gather}
$$

最后，我们再给出 Parseval 恒等式的另一种表达。这实际上是一个更普遍的定理的特例：如果一个映射保持范数不变，那么它也保持内积不变。

**定理 7.3.13** Parseval 恒等式

设 $F,G$ 是圆上的 Riemann 可积函数，其 Fourier 系数分别为 $a_{n}$ 和 $b_{n}$，则

$$
\begin{gather}
\dfrac{1}{2\pi} \int_{0}^{2\pi} F(\theta) \overline{G(\theta)} \mathrm{d} \theta=\sum_{n=-\infty}^{\infty} a_{n} \overline{b_{n}}
\end{gather}
$$

**证明**

根据 Parseval 恒等式以及范数的极化恒等式

$$
\begin{gather}
\langle F,G \rangle =\dfrac{1}{4}(\lVert F+G \rVert ^{2}-\lVert F-G \rVert ^{2}+i \lVert F+iG \rVert ^{2}-i \lVert F-iG \rVert ^{2})
\end{gather}
$$

即证。

## 逐点收敛

之前我们提到，连续函数的 Fourier 级数只能做到几乎处处收敛。不过，如果我们假设函数拥有更强的光滑性，那么 Fourier 级数的逐点收敛是可以达到的，正如以下定理所展示的：

**定理 7.3.14**

设 $f$ 是圆上的 Riemann 可积函数，在 $\theta_{0}$ 处可微，则

$$
\begin{gather}
\lim_{ N \to \infty } S_{N}(f)(\theta_{0})=f(\theta_{0})
\end{gather}
$$

**证明**

定义

$$
\begin{gather}
F(t)=\begin{cases}
\dfrac{f(\theta_{0}-t)-f(\theta_{0})}{t}, & t\neq 0, |t|\leq \pi \\
-f'(\theta_{0}), & t=0
\end{cases}
\end{gather}
$$

由于 $f$ 在 $\theta_{0}$ 可微，故 $F$ 在 $0$ 的邻域内有界。此外，由于 $f$ 可积，因此 $F$ 在 $[-\pi,-\delta]\cup[\delta,\pi]$ 上可积。这表明 $F$ 在 $[-\pi,\pi]$ 上 Riemann 可积。于是我们有

$$
\begin{align}
S_{N}(f)(\theta_{0})-f(\theta_{0}) &= \dfrac{1}{2\pi} \int_{-\pi}^{\pi} (f(\theta_{0}-t)-f(\theta_{0}))D_{N}(t)\mathrm{d} t \\
&= \dfrac{1}{2\pi} \int_{-\pi}^{2\pi} F(t) tD_{N}(t)\mathrm{d} t
\end{align}
$$

由于

$$
\begin{align}
tD_{N}(t) &=\dfrac{t}{\sin(t /2)} \sin((N+1 /2)t) \\
&= \dfrac{t}{\sin(t /2)} (\sin(Nt)\cos(t /2)+\cos(Nt)\sin(t /2))
\end{align}
$$

且 $\dfrac{t}{\sin(t /2)}$ 在 $[-\pi,\pi]$ 上连续，应用 Riemann-Lebesgue 引理即证。

注意到，在以上定理中如果我们将可微换成在 $\theta_{0}$ 处满足 **Lipschitz 条件**，即存在 $M>0$ 使得 $\lvert f(\theta)-f(\theta_{0}) \rvert\leq M\lvert \theta-\theta_{0} \rvert$，结论同样成立。

以上定理的一个重要推论是局部化原则：这就是说，$S_{N}(f)$ 在 $\theta_{0}$ 处的收敛性仅取决于 $f$ 在 $\theta_{0}$ 局部的行为，尽管 Fourier 系数的定义涉及整个区间上的积分。

**定理 7.3.15**

设 $f,g$ 是圆上的 Riemann 可积函数，给定 $\theta_{0}$，如果存在包含 $\theta_{0}$ 的开区间 $I$ 使得对任意 $\theta \in I$ 有 $f(\theta)=g(\theta)$，那么

$$
\begin{gather}
\lim_{ N \to \infty } (S_{N}(f)(\theta_{0})-S_{N}(g)(\theta_{0}))=0
\end{gather}
$$

**证明**

$f-g$ 在 $I$ 上恒等于零，从而在 $\theta_{0}$ 处可微，应用定理 7.3.14 即证。

# Section 4: Fourier 变换

Fourier 变换是 Fourier 级数在非周期函数上的对应物。对于一个支撑在 $[-M,M]$ 上的函数 $f$，我们希望将其展开为一系列旋转因子 $e^{2\pi i \xi x}$ 的和，为此，我们将 $f$ 限制在 $[-L /2,L /2]$ 上，$L /2>M$，来计算 Fourier 系数：

$$
\begin{gather}
a_{n}(L)= \dfrac{1}{L} \int_{-L /2}^{L /2} f(x)e^{-2\pi inx /L} \mathrm{d} x
\end{gather}
$$

在适当的意义下，我们就有

$$
\begin{gather}
f(x)=\sum_{n=-\infty}^{\infty} a_{n}(L) e^{2\pi inx /L}
\end{gather}
$$

我们定义 $f$ 的 Fourier 变换

$$
\begin{gather}
\hat{f}(\xi)=\int_{-\infty}^{\infty} f(x) e^{-2\pi i \xi x}\mathrm{d} x
\end{gather}
$$

则我们有

$$
\begin{gather}
f(x)=\sum_{n=-\infty}^{\infty} \dfrac{1}{L} \hat{f}\left( \dfrac{n}{L} \right)e^{2\pi inx /L}
\end{gather}
$$

当 $L\to \infty$ 时（这就是说，我们将非周期函数视为周期 $\infty$ 的函数），上面的求和看上去就像是一个 Riemann 和，因此我们至少在直观上可以写

$$
\begin{gather}
f(x)=\int_{-\infty}^{\infty} \hat{f}(\xi) e^{2\pi i\xi x}\mathrm{d} \xi
\end{gather}
$$

本节我们将来证明，在合适的假设下，以上的等式事实上严格成立，从而建立了一个函数与其 Fourier 变换之间的一种对称关系。

和 Fourier 级数一样，我们首先来研究 $\mathbb{R}$ 上的函数以及它的积分。给定函数在有界闭区间上积分的定义，一种最为自然的扩展为

$$
\begin{gather}
\int_{-\infty}^{\infty} f(x)\mathrm{d} x=\lim_{ N \to \infty } \int_{-N}^{N} f(x)\mathrm{d} x
\end{gather}
$$

当然，右侧的极限可能不存在。不过，稍微思考一下就能想到，如果我们要求 $f$ 在无穷远邻域上的衰减速度足够快，那么以上广义积分就存在。一种有用的条件如下所示：

**定义 7.4.1** 适度衰减（moderate decrease）

称函数 $f$ 在 $\mathbb{R}$ 上**适度衰减**，如果 $f$ 是连续函数，并且存在 $A>0$ 使得对任意 $x$ 有

$$
\begin{gather}
\lvert f(x) \rvert \leq \dfrac{A}{1+x^{2}}
\end{gather}
$$

$\mathbb{R}$ 上所有适度衰减函数构成的集合记作 $\mathcal{M}(\mathbb{R})$.

上述条件表明 $f$ 是有界的，并且在无穷远邻域上至少与 $1 /x^{2}$ 下降的一样快。令 $I_{N}=\int_{-N}^{N} f$，则当 $N\to \infty$ 时序列 $I_{N}$ 有极限，因为它是一个 Cauchy 序列：设 $M>N$，则

$$
\begin{align}
\lvert I_{M}-I_{N} \rvert &= \left\lvert  \int_{N\leq|x|\leq M} f(x)\mathrm{d} x  \right\rvert  \\
&\leq A \int_{N\leq|x|\leq M} \dfrac{\mathrm{d} x}{x^{2}} \\
&\leq \dfrac{2A}{N} \to 0
\end{align}
$$

同时，我们也证明了尾部积分 $\int_{|x|\geq N}f(x)\mathrm{d}x \to 0$. 此外，我们还指出：我们可以将适度衰减的定义替换为

$$
\begin{gather}
|f(x)|\leq \dfrac{A}{1+|x|^{1+\varepsilon}}, \quad \varepsilon>0
\end{gather}
$$

这不会影响本章节中之后将要给出的定理，我们取 $\varepsilon=1$ 只是为了方便。

**定理 7.4.2**

设 $f,g \in \mathcal{M}(\mathbb{R})$，则有：

1. 线性性：对 $a,b \in \mathbb{C}$ 有 $\displaystyle \int_{-\infty}^{\infty}(af+bg)=a \int_{-\infty}^{\infty}f+b \int_{-\infty}^{\infty}g$
2. 平移不变性：对 $h \in \mathbb{R}$ 有 $\displaystyle \int_{-\infty}^{\infty}f(x-h)\mathrm{d}x=\int_{-\infty}^{\infty}f(x)\mathrm{d}x$
3. 对 $\delta>0$ 有 $\displaystyle \delta \int_{-\infty}^{\infty}f(\delta x)\mathrm{d}x=\int_{-\infty}^{\infty}f(x)\mathrm{d}x$
4. 连续性：$\displaystyle \lim_{ h \to 0 }\int_{-\infty}^{\infty}\lvert f(x-h)-f(x) \rvert\mathrm{d}x=0$

**证明**

线性性直接由积分和极限的线性性得到。对于平移不变性，我们只需证明

$$
\begin{gather}
\int_{-N}^{N}f(x-h)\mathrm{d} x-\int_{-N}^{N}f(x)\mathrm{d} x \to 0
\end{gather}
$$

而第一项为 $\int_{-N}^{N}f(x-h)\mathrm{d}x=\int_{-N-h}^{N-h}f(x)\mathrm{d}x$，因此上式受

$$
\begin{gather}
\left\lvert  \int_{-N-h}^{-N} f  \right\rvert +\left\lvert  \int_{N-h}^{N} f  \right\rvert \leq \dfrac{Ah}{1+N^{2}}+\dfrac{Ah}{1+(N-h)^{2}}
\end{gather}
$$

控制，从而当 $N\to \infty$ 时趋于 $0$. 同理也可证性质 3，只需注意到

$$
\begin{gather}
\delta \int_{-N}^{N} f(\delta x)\mathrm{d} x=\int_{-\delta N}^{\delta N} f(x)\mathrm{d} x
\end{gather}
$$

最后，为证明连续性，我们设 $|h|\leq 1$，对给定的 $\varepsilon>0$，我们首先取足够大的 $N$ 使得

$$
\begin{gather}
\int_{|x|\geq N} f(x)\mathrm{d} x< \dfrac{\varepsilon}{4}, \quad \int_{|x|\geq N} f(x-h)\mathrm{d} x < \dfrac{\varepsilon}{4}
\end{gather}
$$

固定 $N$，由于 $f$ 连续，从而在 $[-N-1,N+1]$ 上一致连续，则当 $h$ 足够小时有

$$
\begin{gather}
\sup_{|x|\leq N} \lvert f(x-h)-f(x) \rvert < \dfrac{\varepsilon}{4N}
\end{gather}
$$

结合上面三个不等式，我们就有

$$
\begin{align}
\int_{-\infty}^{\infty} \lvert f(x-h)-f(x) \rvert \mathrm{d} x &\leq \int_{-N}^{N} \lvert f(x-h)-f(x) \rvert \mathrm{d} x \\
&+\int_{|x|\geq N} \lvert f(x-h) \rvert \mathrm{d} x+\int_{|x|\geq N} \lvert f(x) \rvert \mathrm{d} x \\
&< \varepsilon
\end{align}
$$

这就完成了证明。

对于适度下降的函数，下面的定义是良定的：

**定义 7.4.3** Fourier 变换（Fourier Transform）

设 $f \in \mathcal{M}(\mathbb{R})$，定义它的 **Fourier 变换** $\hat{f}=\mathcal{F}(f)\colon \mathbb{R}\to \mathbb{C}$ 为

$$
\begin{gather}
\hat{f}(\xi)=\int_{-\infty}^{\infty} f(x) e^{-2\pi i\xi x}\mathrm{d} x
\end{gather}
$$

根据适度下降函数的性质，可知 $\hat{f}$ 是有界且连续的。此外，根据平移不变性，我们可得

$$
\begin{gather}
\hat{f}(\xi)=\dfrac{1}{2} \int_{-\infty}^{\infty} (f(x)-f(x-1 /2\xi)) e^{-2\pi i\xi x} \mathrm{d} x
\end{gather}
$$

因此当 $|\xi| \to \infty$ 时有 $\hat{f}(\xi)\to 0$. 然而，以上的定义无法保证 $\hat{f}$ 也是适度衰减的，进而也无法考虑 Fourier 反演 $f(x)=\int_{-\infty}^{\infty} f(\xi)e^{2\pi ix\xi}\mathrm{d}\xi$ 的正确性。为了弥补这一缺陷，我们将考虑一个由更为光滑且正则的函数构成的空间，称为 **Schwarz 空间**。这一空间选取的动机源自 Fourier 级数中的结论：Fourier 系数在 $|n| \to \infty$ 时衰减的速度越快，那么函数 $f$ 就越光滑。根据这一类比，我们给出以下定义：

**定义 7.4.4** Schwarz 空间，快速衰减（rapid decrease）

$\mathbb{R}$ 上的 **Schwarz 空间** $\mathcal{S}(\mathbb{R})$ 定义为所有满足**快速衰减**条件，即

$$
\begin{gather}
\sup_{x} |x|^{k} |f^{(\ell)}(x)| <\infty
\end{gather}
$$

对任意 $k,\ell\geq 0$ 成立的 $C^{\infty}$ 函数构成的集合。

容易验证，$\mathcal{S}(\mathbb{R})$ 在逐点的加法和乘法下构成了一个 $\mathbb{C}$ 上的向量空间，此外，如果 $f \in \mathcal{S}(\mathbb{R})$，那么 $f'$ 和 $x f(x)$ 也属于 $\mathcal{S}(\mathbb{R})$，这表明 $\mathcal{S}(\mathbb{R})$ 在导数算子和乘以多项式下是封闭的。

$\mathcal{S}(\mathbb{R})$ 中的一个简单例子是 **Gaussian 函数**

$$
\begin{gather}
f(x)=e^{-x^{2}}
\end{gather}
$$

其在 Fourier 变换，以及其他的很多领域中有着核心作用。读者可以验证，$f$ 的任意阶导数均具有形式 $P(x)e^{-x^{2}}$，其中 $P$ 是一个多项式，而这立即表明 $f \in \mathcal{S}(\mathbb{R})$. 更一般地说，对任意 $a>0$，函数 $e^{-ax^{2}}$ 都是 $\mathcal{S}(\mathbb{R})$ 中的元素。

我们用

$$
\begin{gather}
f(x) \overset{\mathcal{F}}{\longrightarrow} \hat{f}(\xi)
\end{gather}
$$

来表示 $\hat{f}(\xi)$ 是 $f(x)$ 的 Fourier 变换。利用这个符号，我们列出 $\mathcal{S}(\mathbb{R})$ 上 Fourier 变换的性质如下：

**定理 7.4.5**

设 $f \in \mathcal{S}(\mathbb{R})$，则：

1. 对任意 $h \in \mathbb{R}$ 有 $f(x+h)\overset{\mathcal{F}}{\longrightarrow} \hat{f}(\xi)e^{2\pi ih\xi}$
2. 对任意 $h \in \mathbb{R}$ 有 $f(x)e^{-2\pi ihx}\overset{\mathcal{F}}{\longrightarrow} \hat{f}(\xi+h)$
3. 对任意 $\delta>0$ 有 $f(\delta x)\overset{\mathcal{F}}{\longrightarrow} \delta^{-1}\hat{f}(\delta^{-1}\xi)$
4. $f'(x) \overset{\mathcal{F}}{\longrightarrow} 2\pi i \xi \hat{f}(\xi)$
5. $-2\pi ixf(x)\overset{\mathcal{F}}{\longrightarrow} \dfrac{\mathrm{d}}{\mathrm{d}\xi} \hat{f}(\xi)$

性质 4 和 5 表明，除了一个 $2\pi i$ 的系数，Fourier 变换能够将微分与乘积互换。这正是使得 Fourier 变换（以及它的推广 Laplace 变换）成为微分方程理论中的核心对象的原因。

**证明**

性质 1, 2, 3 的证明相当直接：应用定义以及定理 7.4.2 即可。对于性质 4，根据分部积分法得

$$
\begin{gather}
\int_{-N}^{N} f'(x)e^{-2\pi i\xi x}\mathrm{d} x=\left. f(x)e^{-2\pi i\xi x}\right|_{-N}^{N} +2\pi i\xi \int_{-N}^{N} f(x)e^{-2\pi i\xi x}\mathrm{d} x
\end{gather}
$$

令 $N\to \infty$ 即证。最后，我们来证明 $\hat{f}$ 可导。令 $\varepsilon>0$，考虑

$$
\begin{align}
&\dfrac{\hat{f}(\xi+h)-\hat{f}(\xi)}{h}-\mathcal{F}(-2\pi ixf)(\xi) \\
&=\int_{-\infty}^{\infty} f(x)e^{-2\pi i\xi x}\left( \dfrac{e^{-2\pi ixh}-1}{h}+2\pi ix \right)\mathrm{d} x
\end{align}
$$

由于 $f(x)$ 和 $xf(x)$ 都是快速衰减的，故存在 $N$ 使得它们的尾部积分 $\int_{|x|\geq N}f(x)\mathrm{d}x$ 和 $\int_{|x|\geq N}xf(x)\mathrm{d}x$ 小于 $\varepsilon$，此外，对于 $|x|\leq N$，当 $h$ 足够小时就有

$$
\begin{gather}
\left\lvert  \dfrac{e^{-2\pi ixh}-1}{h}+2\pi ix  \right\rvert < \dfrac{\varepsilon}{N}
\end{gather}
$$

从而

$$
\begin{align}
&\left\lvert  \dfrac{\hat{f}(\xi+h)-\hat{f}(\xi)}{h}-\mathcal{F}(-2\pi ixf)(\xi)  \right\rvert  \\
&\leq \int_{-N}^{N} \left\lvert  f(x)e^{-2\pi i\xi x}\left( \dfrac{e^{-2\pi ixh}-1}{h}+2\pi ix \right)  \right\rvert \mathrm{d} x+C\varepsilon \\
&\leq C'\varepsilon
\end{align}
$$

即证 $\dfrac{\mathrm{d}}{\mathrm{d}\xi}\hat{f}(\xi)=\mathcal{F}(-2\pi ixf)(\xi)$.

**定理 7.4.6**

如果 $f \in \mathcal{S}(\mathbb{R})$，那么 $\hat{f}\in \mathcal{S}(\mathbb{R})$.

**证明**

我们已经证明 $\hat{f}$ 是有界的。此外，对非负整数 $k,\ell$，以下表达式是有界的：

$$
\begin{gather}
\xi^{k} \left( \dfrac{\mathrm{d} }{\mathrm{d} \xi} \right)^{\ell} \hat{f}(\xi)
\end{gather}
$$

因为根据定理 7.4.5，它是下式的 Fourier 变换：

$$
\begin{gather}
\dfrac{1}{(2\pi i)^{k}} \left( \dfrac{\mathrm{d} }{\mathrm{d} x} \right)^{k} ((2\pi ix)^{\ell}f(x))
\end{gather}
$$

这表明 $\hat{f}$ 满足快速衰减条件，因而 $\hat{f} \in \mathcal{S}(\mathbb{R})$.

## Fourier 反演

接下来我们来证明 Fourier 反演公式 $f(x)=\int_{-\infty}^{\infty}\hat{f}(\xi)e^{2\pi i\xi x}\mathrm{d}\xi$，它涉及对 Gaussian 核 $e^{-ax^{2}}$ 的细致研究，以及定理 7.2.5 的一个类比。

根据归一化条件，我们首先从 $a=\pi$ 的情况开始：

$$
\begin{gather}
\int_{-\infty}^{\infty} e^{-\pi x^{2}} \mathrm{d} x=1
\end{gather}
$$

在这种情况下，我们有如下的等式：

**定理 7.4.7**

如果 $f(x)=e^{-\pi x^{2}}$，那么 $\hat{f}(\xi)=f(\xi)$.

**证明**

定义

$$
\begin{gather}
F(\xi)=\hat{f}(\xi)=\int_{-\infty}^{\infty} e^{-\pi x^{2}}e^{-2\pi i\xi x}\mathrm{d} x
\end{gather}
$$

则 $F(0)=1$. 由于 $f'(x)=-2\pi x e^{-\pi x^{2}}$，因此

$$
\begin{align}
F'(\xi)=\int_{-\infty}^{\infty} e^{-\pi x^{2}}(-2\pi ix)e^{-2\pi i\xi x}\mathrm{d} x=i \int_{-\infty}^{\infty} f'(x)e^{-2\pi i\xi x}\mathrm{d} x
\end{align}
$$

再应用定理 7.4.5，就有

$$
\begin{gather}
F'(\xi)=i(2\pi i\xi \hat{f}(\xi))=-2\pi \xi F(\xi)
\end{gather}
$$

令 $G(\xi)=F(\xi)e^{\pi \xi^{2}}$，则根据上式有 $G'(\xi)=0$，即 $G$ 是一个常数。又因为 $G(0)=1$，故 $G=1$，并且 $F(\xi)=e^{-\pi \xi^{2}}$，这就完成了证明。

作为推论，我们应用变量替换公式得到：

**定理 7.4.8**

如果 $\delta>0$ 且 $K_{\delta}(x)=\delta^{-1/2}e^{-\pi x^{2}/\delta}$，则 $\hat{K}_{\delta}(\xi)=e^{-\pi\delta \xi^{2}}$.

我们指出：当 $\delta \to 0+$ 时，$K_{\delta}$ 是一族恒等逼近。这意味着它满足以下三个条件：

1. $\displaystyle \int_{-\infty}^{\infty}K_{\delta}(x)\mathrm{d}x=1$
2. $\displaystyle \int_{-\infty}^{\infty}|K_{\delta}(x)|\mathrm{d}x\leq M$
3. 对任意 $\eta>0$，$\displaystyle \lim_{ \delta \to 0+ }\int_{|x|>\eta}|K_{\delta}(x)|\mathrm{d}x=0$

为证明性质 1，注意到 1 中的积分等于 $\hat{K}_{\delta}(0)=1$. 由于 $K_{\delta}(x)\geq 0$，因此性质 2 直接由 1 得到。最后，我们应用变量替换公式，得到

$$
\begin{gather}
\int_{|x|>\eta} |K_{\delta}(x)|\mathrm{d} x=\int_{|y|>\eta \delta^{-1/2}} e^{-\pi y^{2}} \mathrm{d} y \to 0
\end{gather}
$$

即证以下定理：

**定理 7.4.9**

当 $\delta\to 0+$ 时，$\{ K_{\delta} \}_{\delta>0}$ 是一族恒等逼近。

下面我们给出定理 7.2.5 的一个类比。我们定义 $\mathcal{S}(\mathbb{R})$ 上的卷积为

$$
\begin{gather}
(f*g)(x)=\int_{-\infty}^{\infty} f(x-t)g(t)\mathrm{d} t
\end{gather}
$$

对于固定的 $x$，$f(x-t)g(t)$ 关于 $t$ 是快速衰减的，因此以上积分收敛。

**定理 7.4.10**

设 $f \in \mathcal{S}(\mathbb{R})$，$\{ K_{\delta} \}_{\delta>0}$ 在 $\delta\to 0+$ 时是一族恒等逼近，则

$$
\begin{gather}
\lim_{ \delta \to 0+ } (f*K_{\delta})(x)=f(x)
\end{gather}
$$

关于 $x$ 一致。

**证明**

首先我们断言 $f$ 在 $\mathbb{R}$ 上一致连续。事实上，由快速衰减条件，给定 $\varepsilon>0$，存在 $R$ 使得 $|x|\geq R$ 蕴含 $|f(x)|<\varepsilon /4$. 此外，$f$ 在紧致区间 $[-R,R]$ 上一致连续，结合以上结论，我们可以找到 $\eta>0$ 使得

$$
\begin{gather}
|x-y|\leq \eta \implies |f(x)-f(y)|<\varepsilon
\end{gather}
$$

现在我们按定理 7.2.5 的结构进行论证。我们有

$$
\begin{align}
\lvert (f*K_{\delta})(x)-f(x) \rvert &= \left\lvert  \int_{-\infty}^{\infty} K_{\delta}(t)(f(x-t)-f(x))\mathrm{d} t  \right\rvert  \\
&\leq \int_{|t|> \eta} K_{\delta}(t) \lvert f(x-t)-f(t) \rvert \mathrm{d} t \\
&+ \int_{|t|\leq \eta} K_{\delta}(t)\lvert f(x-t)-f(t) \rvert \mathrm{d} t
\end{align}
$$

当 $\delta\to 0+$ 时，不等式右侧的第一项趋于零，第二项为 $\varepsilon$，这就完成了证明。

下面的等式通常称为乘积公式。

**定理 7.4.11**

设 $f,g \in \mathcal{S}(\mathbb{R})$，则

$$
\begin{gather}
\int_{-\infty}^{\infty} f(x)\hat{g}(x)\mathrm{d} x=\int_{-\infty}^{\infty} \hat{f}(x)g(x)\mathrm{d} x
\end{gather}
$$

**证明**

对 $F(x,y)=f(x)g(y)e^{-2\pi ixy}$ 应用 Fubini 定理即可。

利用乘积公式，以及 Gaussian 核的性质，我们可以给出本节的第一个主定理。

**定理 7.4.12** Fourier 反演（Fourier inversion）

如果 $f \in \mathcal{S}(\mathbb{R})$，则

$$
\begin{gather}
f(x)=\int_{-\infty}^{\infty} \hat{f}(\xi)e^{-2\pi ix\xi}\mathrm{d} \xi
\end{gather}
$$

**证明**

我们首先证明 $x=0$ 的情况。令 $G_{\delta}(x)=e^{-\pi\delta x^{2}}$，则 $\hat{G}_{\delta}(\xi)=K_{\delta}(\xi)$，于是根据乘积公式有

$$
\begin{gather}
\int_{-\infty}^{\infty} f(x)K_{\delta}(x)\mathrm{d} x=\int_{-\infty}^{\infty} \hat{f}(\xi) G_{\delta}(\xi)\mathrm{d} \xi
\end{gather}
$$

当 $\delta\to 0+$ 时，由于 $K_{\delta}$ 是恒等逼近，因此上式左边是 $f(0)$. 同时，$G_{\delta}$ 在 $\delta\to 0+$ 时一致收敛于 $1$，因此上式右边为 $\int_{-\infty}^{\infty}\hat{f}(\xi)\mathrm{d}\xi$，这就是所要证的。对于一般情况，令 $F(y)=f(x+y)$，则我们有

$$
\begin{gather}
f(x)=F(0)=\int_{-\infty}^{\infty} \hat{F}(\xi)\mathrm{d} \xi=\int_{-\infty}^{\infty} \hat{f}(\xi) e^{2\pi ix\xi}\mathrm{d} \xi
\end{gather}
$$

Fourier 反演允许我们取 Fourier 变换的逆变换 $\mathcal{F}^{-1}$，定义为

$$
\begin{gather}
\mathcal{F}^{-1}(f)(x)=\int_{-\infty}^{\infty} f(\xi)e^{2\pi ix\xi}\mathrm{d} \xi
\end{gather}
$$

则定理 7.4.12 表明在 $\mathcal{S}(\mathbb{R})$ 上有 $\mathcal{F}^{-1}\circ \mathcal{F}=I$，其中 $I$ 是恒等算子。此外，由于 $\mathcal{F}$ 和 $\mathcal{F}^{-1}$ 仅在指数上相差一个负号，因此我们有

$$
\begin{gather}
\mathcal{F}(f)(y)=\mathcal{F}^{-1}(f)(-y)
\end{gather}
$$

这给出 $\mathcal{F}\circ \mathcal{F}^{-1}=I$，作为结论，我们有：

**定理 7.4.13**

Fourier 变换是 $\mathcal{S}(\mathbb{R})$ 上的一个双射。

## Plancherel 定理

本节的第二个主定理是 Plancherel 定理。首先我们需要给出卷积的一些性质，特别是 Fourier 变换交换卷积与逐点乘积，正如我们在周期卷积中看到的那样。

**定理 7.4.14**

如果 $f,g \in \mathcal{S}(\mathbb{R})$，则：

1. $f*g \in \mathcal{S}(\mathbb{R})$
2. $f*g=g*f$
3. $\widehat{f*g}(\xi)=\hat{f}(\xi)\hat{g}(\xi)$

**证明**

为证明 $f*g$ 是快速衰减的，我们注意到对任意 $y$ 和 $\ell\geq 0$ 有

$$
\begin{align}
\sup_{x} |x|^{\ell}|g(x-y)|&\leq \sup_{x} (|x-y|+|y|)^{\ell} |g(x-y)| \\
&\leq \sup_{x} 2^{\ell}(|x-y|^{\ell}+|y|^{\ell})|g(x-y)| \\
&\leq A_{\ell}(1+|y|^{\ell})\leq A_{\ell}(1+|y|)^{\ell}
\end{align}
$$

因为 $g$ 是快速衰减的。从以上不等式，我们得到

$$
\begin{gather}
\sup_{x} |x|^{\ell} |(f*g)(x)| \leq A_{\ell} \int_{-\infty}^{\infty} |f(y)|(1+|y|)^{\ell} \mathrm{d} y< \infty
\end{gather}
$$

上述的不等式能够延续到 $f*g$ 的任意导数上，因为

$$
\begin{gather}
\left( \dfrac{\mathrm{d} }{\mathrm{d} x} \right)^{k} (f*g)(x)=\left( f* \dfrac{\mathrm{d} ^{k}}{\mathrm{d} x^{k}} g \right)(x)
\end{gather}
$$

这就证明了 $f*g$ 是快速衰减的，从而属于 $\mathcal{S}(\mathbb{R})$.

对于性质 2，将变量替换公式

$$
\begin{gather}
\int_{-N}^{N} F(x)\mathrm{d} x=\int_{-N}^{N} F(-x)\mathrm{d} x
\end{gather}
$$

以及平移不变性应用于 $F(y)=f(x-y)g(y)$ 即证。

最后，我们对 $F(x,y)=f(y)g(x-y)e^{-2\pi ix \xi}$ 应用 Fubini 定理，对 $y$ 积分得到 $(f*g)(x)e^{-2\pi ix\xi}$，而对 $x$ 积分得到 $f(y)e^{-2\pi iy\xi}\hat{g}(\xi)$，即证。

现在我们来使用卷积的性质来证明 Plancherel 定理，它表明 Fourier 变换在配备了内积

$$
\begin{gather}
\langle f,g \rangle =\int_{-\infty}^{\infty} f(x) \overline{g(x)} \mathrm{d} x
\end{gather}
$$

的空间 $\mathcal{S}(\mathbb{R})$ 上是一个等距同构。同时，它也是 Fourier 级数中的 Parseval 恒等式的对应物。

**定理 7.4.15** Plancherel 定理

如果 $f \in \mathcal{S}(\mathbb{R})$，那么 $\lVert \hat{f} \rVert=\lVert f \rVert$.

**证明**

定义 $f^{\dagger}(x)=\overline{f(-x)}$，则 $\widehat{f^{\dagger}}(\xi)=\overline{\hat{f}(\xi)}$. 令 $h=f*f^{\dagger}$，则我们有

$$
\begin{gather}
\hat{h}(\xi)=|\hat{f}(\xi)|^{2}, \quad h(0)=\int_{-\infty}^{\infty} |f(x)|^{2} \mathrm{d} x
\end{gather}
$$

对 $h$ 应用 Fourier 反演得

$$
\begin{gather}
h(0)=\int_{-\infty}^{\infty} \hat{h}(\xi)\mathrm{d} \xi
\end{gather}
$$

这就是所要证的。

## Poisson 求和公式

本节的最后一个主定理是 Poisson 求和公式，它是连接 Fourier 级数与变换的一个桥梁。回忆一下，我们最初定义 Fourier 变换的动机就是为非周期函数构造一种 Fourier 级数的对应物。我们现在证明，在圆上的函数与其相关的 $\mathbb{R}$ 上的函数之间有一种更深层次的联系。

给定 $f \in \mathcal{S}(\mathbb{R})$，我们可以构造一个圆上的函数如下：

$$
\begin{gather}
F_{1}(x)=\sum_{n=-\infty}^{\infty} f(x+n)
\end{gather}
$$

由于 $f$ 快速衰减，因此级数在紧致集上绝对且一致收敛，从而 $F_{1}$ 是连续函数。此外，注意到 $F_{1}(x+1)=F_{1}(x)$，因为将 $x$ 替换为 $x+1$ 仅仅只是对级数的项做了一次平移。因此 $F_{1}$ 是一个周期函数，称为 $f$ 的**周期化**。

还有另一种方法可以得到 $f$ 的“周期版本”，这一次是通过 Fourier 级数。根据 Fourier 反演公式

$$
\begin{gather}
f(x)=\int_{-\infty}^{\infty} \hat{f}(\xi) e^{2\pi i\xi x}\mathrm{d} \xi
\end{gather}
$$

我们考虑它在整数点上的取值

$$
\begin{gather}
F_{2}(x)=\sum_{n=-\infty}^{\infty} \hat{f}(n)e^{2\pi inx}
\end{gather}
$$

显然 $F_{2}$ 也是 $1$-周期的。一个基本事实是，以上两种周期化函数事实上是同一函数，这就是 Poisson 求和公式的内容。

**定理 7.4.16** Poisson 求和公式（Poisson summation formula）

如果 $f \in \mathcal{S}(\mathbb{R})$，则

$$
\begin{gather}
\sum_{n=-\infty}^{\infty} f(x+n)=\sum_{n=-\infty}^{\infty} \hat{f}(n)e^{2\pi inx}
\end{gather}
$$

特别地，当 $x=0$ 时有

$$
\begin{gather}
\sum_{n=-\infty}^{\infty} f(n)=\sum_{n=-\infty}^{\infty} \hat{f}(n)
\end{gather}
$$

换句话说，$f$ 的周期化函数的 Fourier 系数正是 $f$ 的 Fourier 变换在整数点的取值。

**证明**

根据定理 7.1.2，要证明两个连续函数相等，我们可以证明它们具有相同的 Fourier 系数。显然，$F_{2}$ 的第 $m$ 个 Fourier 系数为 $\hat{f}(m)$，而 $F_{1}$ 的 Fourier 系数为

$$
\begin{align}
\int_{0}^{1} \left( \sum_{n=-\infty}^{\infty} f(x+n) \right)e^{-2\pi imx}\mathrm{d} x &= \sum_{n=-\infty}^{\infty} \int_{0}^{1} f(x+n)e^{-2\pi imx}\mathrm{d} x \\
&=\sum_{n=-\infty}^{\infty} \int_{n}^{n+1} f(y) e^{-2\pi imy} \mathrm{d} y \\
&= \int_{-\infty}^{\infty} f(y)e^{-2\pi imy}\mathrm{d} y \\
&= \hat{f}(m)
\end{align}
$$

其中第一步中的交换积分与求和是允许的，因为级数在紧致集上一致收敛。这就完成了证明。

# Section 5: 围道积分

本节我们将 Fourier 变换的主要定理推广到适度衰减函数，而这正是复分析，特别是 Cauchy 积分-留数定理参与并发挥作用的地方。我们将看到，Fourier 变换与 Poisson 求和公式是如何作为简单的围道积分的推论得到的。

尽管在实域上我们仍然能够得到推广的结论：如果

$$
\begin{gather}
|f(x)|\leq \dfrac{A}{1+x^{2}} \quad \text{且} \quad |\hat{f}(\xi)|\leq \dfrac{A'}{1+\xi^{2}}
\end{gather}
$$

那么定理 7.4.10 与乘积公式的证明仍然成立，从这我们可得 Fourier 反演公式；如果 $g$ 也是适度衰减的，那么 $f*g$ 也是适度衰减的，并且有 $\mathcal{F}(f*g)=\mathcal{F}(f)\mathcal{F}(g)$，这就能得到 Plancherel 定理；最后，在适度衰减条件下 Poisson 求和公式的证明也无需修改。不过，Fourier 变换的某些性质只有在复数域下才会展现，例如，要使 Fourier 变换 $\hat{f}$ 具有有限带宽，换句话说，$\hat{f}$ 支撑在有界区间 $[-M,M]$ 上，函数 $f$ 需要满足什么条件？这一问题的答案，正如 **Paley-Wiener 定理**所指出的，涉及函数 $f$ 在复数域上的全纯性。

## 复数上的 Fourier 积分

本节的上半部分，我们将使用围道积分来推导包括 Fourier 反演以及 Poisson 求和公式在内的若干定理。我们将引入一类函数，其在允许我们自由使用积分公式的前提下，也足够广泛，以包含我们所设想的许多应用。

对 $a>0$，我们记 $\mathfrak{F}_{a}$ 包含所有满足以下两个条件的函数 $f$：

1. $f$ 在水平条带 $S_{a}=\{ z \mid \lvert \mathrm{Im}\,z \rvert<a \}$ 上解析；
2. 存在 $A>0$ 使得对任意 $z=x+iy \in S_{a}$ 有 $$
|f(x+iy)|\leq \dfrac{A}{1+x^{2}}
$$

换句话说，解析函数 $f \in \mathfrak{F}_{a}$ 在每条水平直线 $\mathrm{Im}\,z=y$ 上适度衰减，关于 $-a<y<a$ 一致。我们记 $\mathfrak{F}$ 为所有 $\mathfrak{F}_{a}$ 的并集。

下面我们将展示如何通过简单的围道积分得到 Fourier 变换的各种性质，首先从一个不等式开始：

**定理 7.5.1**

如果 $f \in \mathfrak{F}_{a}$，则 $\lvert \hat{f}(\xi) \rvert\leq Be^{-2\pi b\lvert \xi \rvert}$ 对 $0<b<a$ 成立。

**证明**

$\xi=0$ 的情况仅仅只是说 $\hat{f}$ 是有界的，这可以直接由 $f$ 的适度衰减性得到。下面首先设 $\xi>0$，证明的一个关键步骤就是将积分路径（实数轴）下移 $b$ 个单位，这就是说，考虑如图所示的路径：

![](7-2.png)

取 $g(z)=f(z)e^{-2\pi i\xi z}$，我们断言当 $R\to \infty$ 时 $g$ 在竖直线段上的积分为零。事实上，我们有

$$
\begin{align}
\left\lvert  \int_{-R-ib}^{-R} g(z)\mathrm{d} z  \right\rvert &\leq \int_{0}^{b} \lvert f(-R-it)e^{-2\pi i\xi (-R-it)} \rvert \mathrm{d} t \\
&\leq \int_{0}^{b} \dfrac{A}{1+R^{2}} e^{-2\pi \xi t} \mathrm{d} t = O(1 /R^{2})
\end{align}
$$

另一条线段同理。于是，根据 Cauchy 定理，我们有

$$
\begin{gather}
\hat{f}(\xi)=\int_{-\infty}^{\infty} f(x-ib)e^{-2\pi i\xi(x-ib)} \mathrm{d} x
\end{gather}
$$

这就给出

$$
\begin{gather}
\lvert \hat{f}(\xi) \rvert \leq \int_{-\infty}^{\infty} \dfrac{A}{1+x^{2}} e^{-2\pi \xi b}\mathrm{d} x\leq Be^{-2\pi b\xi}
\end{gather}
$$

当 $\xi<0$ 时，将积分路径上移 $b$ 个单位即证。

以上定理表明，如果 $f \in \mathfrak{F}$，那么 $\hat{f}$ 是快速衰减的（事实上，它至少与指数函数下降的一样快），并且 $f$ 的解析范围越大（$a$ 越大），其衰减速度越快（可以取更大的 $b$）。在本节的下半部分，我们将讨论 $\hat{f}$ 拥有最快的下降速度——也即拥有紧支撑——时，$f$ 所要满足的条件。

由于 $\hat{f}$ 在 $\mathbb{R}$ 上快速衰减，因此 Fourier 反演中的积分有意义，于是我们就可以来证明这一等式。

**定理 7.5.2** Fourier 反演

如果 $f \in \mathfrak{F}$，那么对任意 $x \in \mathbb{R}$ 有

$$
\begin{gather}
f(x)=\int_{-\infty}^{\infty} \hat{f}(\xi) e^{2\pi i\xi x}\mathrm{d} \xi
\end{gather}
$$

**证明**

由于 $\xi$ 的正负会影响路径的选取，因此我们将上述积分写成

$$
\begin{gather}
\int_{-\infty}^{\infty} \hat{f}(\xi)e^{2\pi i\xi x}\mathrm{d} x=\int_{-\infty}^{0} \hat{f}(\xi)e^{2\pi i\xi x}\mathrm{d} \xi+\int_{0}^{\infty} \hat{f}(\xi)e^{2\pi i\xi x}\mathrm{d} \xi
\end{gather}
$$

对于第二个积分项，设 $f \in \mathfrak{F}_{a}$，并取 $0<b<a$，则根据定理 7.5.1 的证明得

$$
\begin{gather}
\hat{f}(\xi)=\int_{-\infty}^{\infty} f(u-ib)e^{-2\pi i\xi(u-ib)} \mathrm{d} u
\end{gather}
$$

于是由 Fubini 定理得

$$
\begin{align}
\int_{0}^{\infty} \hat{f}(\xi)e^{2\pi i\xi x}\mathrm{d} \xi &=\int_{0}^{\infty} \int_{-\infty}^{\infty} f(u-ib) e^{-2\pi i\xi(u-ib)}e^{2\pi i\xi x} \mathrm{d} u \mathrm{d} \xi \\
&= \int_{-\infty}^{\infty} f(u-ib) \int_{0}^{\infty} e^{-2\pi i\xi(u-x-ib)} \mathrm{d} \xi \mathrm{d} u \\
&=\int_{-\infty}^{\infty} f(u-ib) \dfrac{1}{2\pi b+2\pi i(u-x)} \mathrm{d} u \\
&= \dfrac{1}{2\pi i} \int_{-\infty}^{\infty} \dfrac{f(u-ib)}{u-ib-x} \mathrm{d} u \\
&= \dfrac{1}{2\pi i} \int_{L_{1}} \dfrac{f(z)}{z-x}\mathrm{d} z
\end{align}
$$

其中 $L_{1}$ 是指向右侧的直线 $\{ u-ib \mid u \in \mathbb{R} \}$. 对于第一个积分项，同理有

$$
\begin{gather}
\int_{-\infty}^{0} \hat{f}(\xi)e^{2\pi i\xi x}\mathrm{d} \xi = -\dfrac{1}{2\pi i} \int_{L_{2}} \dfrac{f(z)}{z-x}\mathrm{d} z
\end{gather}
$$

其中 $L_{2}$ 是指向右侧的直线 $\{ u+ib \mid u \in \mathbb{R} \}$. 考虑如图所示的路径 $\gamma_{R}$：

![](7-3.png)

由于 $f(z) /(z-x)$ 在 $z=x$ 处有单极点，并且当 $R\to \infty$ 时竖直线段上的积分为零，于是由 Cauchy 积分-留数定理得

$$
\begin{align}
f(x) = \dfrac{1}{2\pi i} \int_{L_{1}} \dfrac{f(z)}{z-x}\mathrm{d} z-\dfrac{1}{2\pi i} \int_{L_{2}} \dfrac{f(z)}{z-x} \mathrm{d} z=\int_{-\infty}^{\infty} \hat{f}(\xi)e^{2\pi i\xi x}\mathrm{d} \xi
\end{align}
$$

这就完成了证明。

我们的最后一个定理是 Poisson 求和公式。

**定理 7.5.3** Poisson 求和公式

如果 $f \in \mathfrak{F}$，则

$$
\begin{gather}
\sum_{n=-\infty}^{\infty} f(n)=\sum_{n=-\infty}^{\infty} \hat{f}(n)
\end{gather}
$$

**证明**

设 $f \in \mathfrak{F}_{a}$，取 $0<b<a$. 我们考虑函数 $\dfrac{f(z)}{e^{2\pi iz}-1}$，它在每个整数点上都有单极点，其留数为 $f(n) / 2\pi i$，于是我们将留数定理应用于路径 $\gamma_{N}$：

![](7-4.png)

这给出

$$
\begin{gather}
\sum_{|n|\leq N} f(n)=\int_{\gamma_{N}} \dfrac{f(z)}{e^{2\pi iz}-1} \mathrm{d} z
\end{gather}
$$

令 $N \to \infty$，由于 $f$ 适度衰减，级数 $\sum_{n=-\infty}^{\infty}f(n)$ 收敛，并且竖直线段上的积分趋于零，从而

$$
\begin{gather}
\sum_{n=-\infty}^{\infty} f(n)=\int_{L_{1}} \dfrac{f(z)}{e^{2\pi iz}-1}\mathrm{d} z-\int_{L_{2}} \dfrac{f(z)}{e^{2\pi iz}-1}\mathrm{d} z
\end{gather}
$$

其中 $L_{1},L_{2}$ 如 7.5.2 中所示。

如果 $z \in L_{1}$，那么 $\lvert e^{2\pi iz} \rvert>1$，于是根据几何级数的展开公式有

$$
\begin{gather}
\dfrac{1}{e^{2\pi iz}-1}=\dfrac{e^{-2\pi iz}}{1-e^{-2\pi iz}}=e^{-2\pi iz} \sum_{n=0}^{\infty} e^{-2\pi inz}
\end{gather}
$$

如果 $z \in L_{2}$，那么 $\lvert e^{2\pi iz} \rvert<1$，从而

$$
\begin{gather}
\dfrac{1}{e^{2\pi iz}-1}=-\sum_{n=0}^{\infty} e^{2\pi inz}
\end{gather}
$$

这就给出

$$
\begin{align}
\sum_{n=-\infty}^{\infty} f(n) &= \int_{L_{1}} f(z) \sum_{n=0}^{\infty} e^{-2\pi i(n+1)z}\mathrm{d} z+\int_{L_{2}} f(z)\sum_{n=0}^{\infty} e^{2\pi inz} \mathrm{d} z \\
&= \sum_{n=0}^{\infty} \int_{-\infty}^{\infty} f(x)e^{-2\pi i(n+1)x}\mathrm{d} x+\sum_{n=0}^{\infty} \int_{-\infty}^{\infty} f(x)e^{2\pi inx}\mathrm{d} x \\
&= \sum_{n=0}^{\infty} \hat{f}(n+1) +\sum_{n=0}^{\infty} \hat{f}(-n)=\sum_{n=-\infty}^{\infty} \hat{f}(n)
\end{align}
$$

其中第二个等式中我们将 $L_{1}$ 和 $L_{2}$ 平移回实轴，根据定理 7.5.1 的证明，这一过程保持积分的值不变。

## Paley-Wiener 定理

接下来，我们将稍微改变一下我们的视角：我们不假设 $f$ 的光滑性，但我们将假设 $f$ 和 $\hat{f}$ 都是适度衰减的，从而 Fourier 反演公式成立。首先，我们考虑定理 7.5.1 的一个部分逆命题。

**定理 7.5.4**

设 $\hat{f}$ 满足衰减条件 $\lvert \hat{f}(\xi) \rvert\leq Ae^{-2\pi a\lvert \xi \rvert}$，$a,A>0$，则 $f(x)$ 可以扩张为一个在水平条带 $S_{b}=\{ z \mid \lvert \mathrm{Im}\, z \rvert<b \}$ 上解析的函数 $f(z)$，对任意 $0<b<a$ 成立。

换句话说，通过 Fourier 变换 $\hat{f}$ 的衰减条件，我们可以自动得到函数 $f$ 的光滑性条件。

**证明**

定义

$$
\begin{gather}
f_{n}(z)=\int_{-n}^{n} \hat{f}(\xi) e^{2\pi i\xi z}\mathrm{d} \xi
\end{gather}
$$

由于 $\hat{f}(\xi)e^{2\pi i\xi z}$ 关于 $z$ 在 $\mathbb{C}$ 上解析，因此 $f_{n}$ 是一个整函数。此外，由于 $0<b<a$，因此

$$
\begin{gather}
f(z)=\int_{-\infty}^{\infty} \hat{f}(\xi)e^{2\pi i\xi z} \mathrm{d} \xi
\end{gather}
$$

在 $S_{b}$ 上有定义，因为积分受

$$
\begin{gather}
A \int_{-\infty}^{\infty} e^{-2\pi a|\xi|} e^{2\pi b|\xi|} \mathrm{d} \xi<\infty
\end{gather}
$$

的控制。此外，对于 $z \in S_{b}$ 有

$$
\begin{gather}
\lvert f(z)-f_{n}(z) \rvert \leq A \int_{|\xi|\geq n} e^{-2\pi a|\xi|}e^{2\pi b|\xi|} \mathrm{d} \xi \to 0
\end{gather}
$$

因此 $(f_{n})$ 在 $S_{b}$ 上一致收敛于 $f$，这表明 $f$ 在 $S_{b}$ 上解析，这就完成了证明。

作为推论，我们有：

**定理 7.5.5**

如果 $\hat{f}(\xi)=O(e^{-2\pi a|\xi|})$，$a>0$，并且 $f$ 在一个非空开区间上消失，则 $f=0$ 为常数。

**证明**

由于 $f$ 可以扩张为 $S_{b}$ 上的解析函数，则根据“非常值解析函数的零点孤立”的结论，$f=0$ 恒成立。

Paley-Wiener 定理在前面定理的基础上更进了一步，描述了那些具有紧支撑 Fourier 变换的函数的光滑性。

**定理 7.5.6** Paley-Wiener 定理

设 $f$ 适度衰减，则 $f$ 可以扩张为一个整函数，满足 $|f(z)|\leq Ae^{2\pi M|z|}$，$A>0$，当且仅当 $\hat{f}$ 的支撑集包含于 $[-M,M]$.

**证明**

一个方向的推导非常简单。假设 $\hat{f}$ 支撑在 $[-M,M]$ 上，则根据适度衰减条件，我们有 Fourier 反演

$$
\begin{gather}
f(x)=\int_{-M}^{M} \hat{f}(\xi) e^{2\pi i\xi x}\mathrm{d} \xi
\end{gather}
$$

将自变量 $x \in \mathbb{R}$ 替换为 $z \in \mathbb{C}$ 即可得到一个整函数

$$
\begin{gather}
g(z)=\int_{-M}^{M} \hat{f}(\xi) e^{2\pi i\xi z}\mathrm{d} \xi
\end{gather}
$$

并且显然 $g(x)=f(x)$ 对 $x \in \mathbb{R}$ 成立。此外，设 $z=x+iy$，则

$$
\begin{align}
\lvert g(z) \rvert &\leq \int_{-M}^{M} \lvert \hat{f}(\xi) \rvert e^{-2\pi \xi y}\mathrm{d} \xi \\
&\leq Ae^{2\pi M|z|}
\end{align}
$$

另一个方向的推导需要更多的工作。首先，我们注意到，如果 $\hat{f}$ 支撑在 $[-M,M]$ 上，那么上面的论证实际上给出了更强的上界 $|f(z)|\leq Ae^{2\pi M|y|}$，而非条件中的 $Ae^{2\pi M|z|}$. 于是，我们的想法就是尝试将其简化到这一更好的情况。然而，这对我们来说还不够，因为我们需要在 $x$ 方向上增加一个适度衰减条件，以使得特定的积分收敛。因此，我们便从具有更强的假设的 $f$ 出发，逐步地减弱 $f$ 的条件，直到与定理中的条件相同。

(1). 我们首先假设 $f$ 是整函数，满足衰减条件

$$
\begin{gather}
\lvert f(x+iy) \rvert \leq A' \dfrac{e^{ 2\pi M|y| }}{1+x^{2}}
\end{gather}
$$

在这一假设下我们证明 $\hat{f}$ 支撑在 $[-M,M]$ 上。首先设 $\xi>M$，则根据本节中我们经常使用的平移实轴论证，得到

$$
\begin{align}
\hat{f}(\xi) &= \int_{-\infty}^{\infty} f(x)e^{-2\pi i\xi x}\mathrm{d} x \\
&= \int_{-\infty}^{\infty} f(x-iy)e^{-2\pi i\xi(x-iy)} \mathrm{d} x
\end{align}
$$

其中 $y>0$，则有

$$
\begin{align}
\lvert \hat{f}(\xi) \rvert &\leq A' \int_{-\infty}^{\infty} \dfrac{e^{ 2\pi My }e^{ -2\pi \xi y }}{1+x^{2}} \mathrm{d} x \\
&\leq Ce^{ -2\pi y(\xi-M) }
\end{align}
$$

由于 $\xi>M$，当 $y\to \infty$ 时，即得 $\hat{f}(\xi)=0$. 同理可得 $\xi<-M$ 时 $\hat{f}(\xi)=0$.

(2). 我们放宽对 $f$ 的限制，假设其只满足

$$
\begin{gather}
\lvert f(x+iy) \rvert \leq Ae^{ 2\pi M|y| }
\end{gather}
$$

设 $\xi>M$，对 $\varepsilon>0$ 我们构造辅助函数

$$
\begin{gather}
f_{\varepsilon}(z)=\dfrac{f(z)}{(1+i\varepsilon z)^{2}}
\end{gather}
$$

我们观察到 $1 /(1+i\varepsilon z)^{2}$ 的绝对值在闭下半平面（包含实轴）上小于等于 $1$，并且当 $\varepsilon\to 0$ 时绝对值趋于 $1$，于是，当 $\varepsilon \to 0$ 时我们有

$$
\begin{align}
\lvert \hat{f}_{\varepsilon}(z)-\hat{f}(z) \rvert \leq \int_{-\infty}^{\infty} |f(x)| \left\lvert  \dfrac{1}{(1+i\varepsilon x)^{2}}-1  \right\rvert \mathrm{d} x \to 0
\end{align}
$$

即 $\hat{f}_{\varepsilon}(z) \to \hat{f}(z)$. 但 $f_{\varepsilon}$ 满足衰减条件

$$
\begin{gather}
\lvert f_{\varepsilon}(x+iy) \rvert \leq A'' \dfrac{e^{ 2\pi M|y| }}{1+x^{2}}
\end{gather}
$$

因此根据 (1) 有 $\hat{f}_{\varepsilon}(\xi)=0$，从而 $\hat{f}(\xi)=0$. 当 $\xi<-M$ 时，我们使用 $f(z) /(1-i\varepsilon z)^{2}$ 在上半平面进行论证，同理可证 $\hat{f}(\xi)=0$.

(3). 最后，我们来证明定理中的条件蕴含步骤 (2) 中的限制。通过对 $f$ 进行适当放缩，我们只需证明 $|f(x)|\leq 1$ 对 $x \in \mathbb{R}$ 成立和 $|f(z)|\leq e^{ 2\pi M|z| }$ 对 $z \in \mathbb{C}$ 成立蕴含 $\lvert f(x+iy) \rvert\leq e^{ 2\pi M|y| }$. 我们将使用 Phragmen-Lindelof 定理的一个推论（5.4.2）进行证明。

考虑由 $0<\mathrm{arg}\,z<\pi /2$ 的点 $z$ 构成的扇形，也就是第一象限 $Q=\{ x+iy \mid x,y>0 \}$，我们定义

$$
\begin{gather}
F(z)=f(z)e^{2\pi iMz}
\end{gather}
$$

则在 $\partial Q$ 上有 $|F(z)|\leq 1$. 此外，在 $Q$ 的内部我们有 $|F(z)|\leq e^{c|z|}$，当 $|z|$ 足够大时有 $|F(z)|\leq \exp(|z|^{3/2})$，从而根据定理 5.4.2 得 $|F(z)|\leq 1$ 在 $Q$ 上成立，即 $|f(z)|\leq e^{ 2\pi M|y| }$. 对其他三个象限做类似的论证就完成了证明。

我们指出：由于 Fourier 变换与其反演仅在指数项上相差一个符号，因此我们可以将以上定理中的 $f$ 与 $\hat{f}$ 的角色互换，此时它所描述的就是在时域上具有紧支撑的函数，其 Fourier 变换可以扩张为整函数，并且具有指数上界。结合两种 Paley-Wiener 定理的表述，我们可以得出一个非常重要的结论：一个函数的时域表达和频域表达不可能同时具有紧支撑，它是现代信号处理领域的基石之一。

本节的最后，我们再给出 Paley-Wiener 定理的另一种形式，它描述的是 Fourier 变换在 $\xi<0$ 时消失的函数。

**定理 7.5.7** Paley-Wiener 定理 II

设 $f,\hat{f}$ 适度衰减，则 $\hat{f}(\xi)=0$ 对 $\xi<0$ 成立当且仅当 $f$ 可以扩张为闭上半平面 $\{ x+iy \mid y\geq 0 \}$ 上的有界连续函数，且在平面内部解析。

**证明**

首先设 $\hat{f}(\xi)=0$ 对 $\xi<0$ 成立，则根据 Fourier 反演定理得

$$
\begin{align}
f(x)=\int_{0}^{\infty} \hat{f}(\xi) e^{2\pi i\xi x}\mathrm{d} \xi
\end{align}
$$

于是我们可以将 $f$ 扩张为

$$
\begin{gather}
f(z)=\int_{0}^{\infty} \hat{f}(\xi) e^{2\pi i\xi z}\mathrm{d} \xi
\end{gather}
$$

根据适度衰减条件，我们有

$$
\begin{gather}
\lvert f(z) \rvert \leq A \int_{0}^{\infty} \dfrac{1}{1+\xi^{2}} \mathrm{d} \xi<\infty
\end{gather}
$$

因此 $f$ 是有界函数。此外，我们还有

$$
\begin{gather}
f_{n}(z)=\int_{0}^{n} \hat{f}(\xi) e^{ 2\pi i\xi z } \mathrm{d} \xi
\end{gather}
$$

在闭上半平面上一致收敛于 $f$，这就证明了连续性与内部的解析性。

对于相反方向的蕴含，我们仿照 7.5.6 的证明，构造辅助函数

$$
\begin{gather}
f_{\varepsilon,\delta}(z)=\dfrac{f(z+i\delta)}{(1-i\varepsilon z)^{2}}
\end{gather}
$$

则 $f_{\varepsilon,\delta}$ 在一个包含闭上半平面的区域内解析，并且 $\hat{f}_{\varepsilon,\delta}(\xi)=0$ 对 $\xi<0$ 成立。接下来令 $\delta \to 0$，再令 $\varepsilon \to 0$ 即证 $\hat{f}(\xi)=0$ 对 $\xi<0$ 成立。这就完成了证明。

同样，在以上定理中，我们可以交换 $f$ 与 $\hat{f}$，从而得到时域函数满足 $f(x)=0$ 对 $x<0$ 成立的一个充要条件。