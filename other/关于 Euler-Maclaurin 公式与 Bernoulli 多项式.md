# 从 Basel 问题讲起

1650 年，来自瑞士巴塞尔（Basel）的数学家 Jacob Bernoulli 向全世界寻求以下问题的解：级数

$$
\begin{gather}
1+\dfrac{1}{2^{2}}+\dfrac{1}{3^{2}}+\cdots=\sum_{n=1}^{\infty} \dfrac{1}{n^{2}}
\end{gather}
$$

的精确值是什么？

这一问题在 1735 年由数学家 Leonhard Euler 解决：Euler 发现，上述级数的值为

$$
\begin{gather}
\sum_{n=1}^{\infty} \dfrac{1}{n^{2}}=\dfrac{\pi^{2}}{6}
\end{gather}
$$

Euler 对该问题的求解可以分成两步：首先，他将上述级数的近似值计算到了惊人的 17 位小数：

$$
\begin{gather}
\sum_{n=1}^{\infty} \dfrac{1}{n^{2}} \approx 1.64493406684822644
\end{gather}
$$

从这一近似值，Euler 注意到：它恰好与 $\dfrac{\pi^{2}}{6}$ 的前几位小数相同，这引导 Euler 发现了 Basel 问题的第一个证明。

在本文中，我们将展示 Euler 是如何在没有计算机的年代得到如此精确的近似值的，在这一过程中，我们将逐步建立起一种极为常用且重要的近似方法，即 **Euler-Maclaurin 求和公式**。

# 初步尝试

经过简单的尝试后，我们会注意到一个问题，那就是级数 $\displaystyle \sum_{n=1}^{\infty} \dfrac{1}{n^{2}}$ 的收敛速度太慢了：前 1000 项的近似值为

$$
\begin{gather}
\sum_{n=1}^{1000} \dfrac{1}{n^{2}} \approx 1.6439
\end{gather}
$$

仅有两位精确小数，而这样的计算已经是人力所不可及的了。为此，我们需要使用其它的方法来近似这个和。

首先，我们可以将这个和可视化如下：

![](1.png)

其中蓝色的矩形的面积是我们所要求的，红色的曲线则是 $f(x)=\dfrac{1}{x^{2}}$ 的图像。我们可以把每个矩形分成三个部分：曲线下方、黑色直线上方的三角形以及两者之间的月牙形。第一个部分就是单纯的积分：

$$
\begin{gather}
\int_{1}^{\infty} \dfrac{1}{x^{2}} \mathrm{d} x=1
\end{gather}
$$

而第二个部分则是一个“telescoping-sum”

$$
\begin{gather}
\dfrac{1}{2}\left( 1-\dfrac{1}{2^{2}} \right)+\dfrac{1}{2}\left( \dfrac{1}{2^{2}}-\dfrac{1}{3^{2}} \right)+\dfrac{1}{2}\left( \dfrac{1}{3^{2}}-\dfrac{1}{4^{2}} \right)+\cdots=\dfrac{1}{2}
\end{gather}
$$

于是，剩下的工作就是估计中间月牙形部分的面积，我们将区间 $[i,i+1]$ 上的月牙形区域的面积记作 $A_{i}$，显然 $A_{i}$ 可以表示为梯形的面积减去一个积分：

$$
\begin{gather}
A_{i}=\dfrac{f(i)+f(i+1)}{2}-\int_{i}^{i+1} f(x) \mathrm{d} x
\end{gather}
$$

我们的目标是尽可能精确地估计 $\displaystyle \sum_{i=1}^{\infty}A_{i}$ 的值，同时避免做大量的计算，因此，将第一项 $\dfrac{f(i)+f(i+1)}{2}$ 消去是我们首先要做的，这可以通过对后一项积分进行变换来实现。

具体来说，我们将使用分部积分公式

$$
\begin{gather}
\int_{a}^{b} u \mathrm{d} v= \left. uv \right| _{a}^{b} - \int_{a}^{b} v \mathrm{d} u
\end{gather}
$$

寄希望于边界项 $uv|_{a}^{b}$ 能够消去前一项。此外，为了公式推导的方便，我们将 $f(x)$ 的自变量平移 $i$ 单位，写成

$$
\begin{gather}
A=\dfrac{f(0)+f(1)}{2}-\int_{0}^{1} f(x)\mathrm{d} x
\end{gather}
$$

现在应用分部积分公式，其中 $u=f(x)$ 而 $\mathrm{d}v=\mathrm{d}x$，于是 $v=x+C$，其中 $C$ 是一个待定的常数，得到

$$
\begin{gather}
A=\dfrac{f(0)+f(1)}{2}-((1+C)f(1)-Cf(0))+\int_{0}^{1}(x+C)f'(x)\mathrm{d} x
\end{gather}
$$

当 $C=-\dfrac{1}{2}$ 时我们有

$$
\begin{gather}
A=\int_{0}^{1}\left( x-\dfrac{1}{2} \right)f'(x)\mathrm{d} x
\end{gather}
$$

从而我们成功地消去了第一项。然而，剩下的这一项积分仍然难以计算，因此我们继续分部积分，取 $u=f'(x)$ 而 $\mathrm{d}v=(x-1 / 2)\mathrm{d}x$，得到

$$
\begin{gather}
A=Cf'(1)-Cf'(0)-\int_{0}^{1}\left( \dfrac{x^{2}}{2}-\dfrac{x}{2}+C \right)f''(x)\mathrm{d} x
\end{gather}
$$

这里的积分常数 $C$ 似乎是任意的，但我们有一个隐含条件，那就是最后的积分项应该足够小，从而我们可以通过计算前面的边界项来得到 $A$ 的一个近似值。特别地，上述公式对于一个**多项式**来说应当足够精确：因为它们是所有函数的“基准”，意味着如果我们的近似方法对所有低次多项式都能精确成立，那么对于更一般的光滑函数（可在局部展开为多项式的函数），它也会有良好的精度。

既然这里用到了 $f$ 的二阶导数，那么我们可以使用二次多项式进行测试，此时有

$$
\begin{gather}
\int_{0}^{1}\left( \dfrac{x^{2}}{2}-\dfrac{x}{2}+C \right)f''(x)\mathrm{d} x=a\cdot \int_{0}^{1}\left( \dfrac{x^{2}}{2}-\dfrac{x}{2}+C \right)\mathrm{d} x
\end{gather}
$$

在最好的情况下，我们要求积分项为 0，此时解得 $C=\dfrac{1}{12}$.

回过头来，我们可以验证含有 $f'(x)$ 的积分项满足同样的性质：当 $f$ 是一次多项式（线性函数）时，有

$$
\begin{gather}
\int_{0}^{1} \left( x-\dfrac{1}{2} \right)f'(x)\mathrm{d} x=a\cdot \int_{0}^{1}\left( x-\dfrac{1}{2} \right)\mathrm{d} x=0
\end{gather}
$$

类似地，要得到对于三次多项式的精确公式，我们可以在二次公式

$$
\begin{gather}
A=\dfrac{f'(1)-f'(0)}{12}-\int_{0}^{1}\left( \dfrac{x^{2}}{2}-\dfrac{x}{2}+\dfrac{1}{12} \right)f''(x)\mathrm{d} x
\end{gather}
$$

的基础上再次分部积分，得到

$$
\begin{gather}
A=\dfrac{f'(1)-f'(0)}{12}+\int_{0}^{1}\left( \dfrac{x^{3}}{6}-\dfrac{x^{2}}{4}+\dfrac{x}{12} \right)f'''(x)\mathrm{d} x
\end{gather}
$$

同理我们可以递归地得到四次、五次以及更高次的公式。

# 统一范式

随着我们写出越来越精确的近似公式，一种规律将开始显现：我们有

$$
\begin{gather}
A=Q_{1}+Q_{2}+\dots+Q_{k}+(-1)^{k+1}\int_{0}^{1}\phi_{k+1}(x)f^{(k+1)}(x)\mathrm{d} x
\end{gather}
$$

其中 $Q$ 是边界项，$Q_{1}=\dfrac{f'(1)-f'(0)}{12},Q_{2}=0$ 等等；$\phi_{k+1}$ 是一个 $k+1$ 次的多项式，它是 $\phi_{k}$ 的一个原函数，且满足

$$
\begin{gather}
\int_{0}^{1}\phi_{k+1}(x)\mathrm{d} x=0
\end{gather}
$$

以使得当 $f$ 是 $k+1$ 次多项式时上述近似公式成为精确公式。下面我们将这一递归范式进行形式化，并从头推导出上面的公式。

**定义 1**

设 $\mathcal{P}$ 是 $\mathbb{R}$ 上的一元多项式构成的向量空间，定义线性算子 $\mathscr{A}\colon \mathcal{P}\to \mathcal{P}$ 如下：对任意 $p \in \mathcal{P}$，定义 $\mathscr{A}p$ 为唯一的多项式 $q \in \mathcal{P}$ 使得

- $q'=p$
- $\displaystyle \int_{0}^{1}q=0$

取 $\phi_{0}=1$，我们可以递归地定义 $\phi_{k+1}=\mathscr{A}\phi_{k}$，进而得到一个多项式序列 $(\phi_{k})_{k=0}^{\infty}$，这一序列的构造方式与我们做分部积分的过程是一致的：设 $f$ 是一个 $C^{\infty}$ 光滑的函数，则有递推式

$$
\begin{gather}
\int_{0}^{1} \phi_{k}(x)f^{(k)}(x)\mathrm{d} x=\left. \phi_{k+1}(x)f^{(k)}(x) \right|_{0}^{1} -\int_{0}^{1}\phi_{k+1}(x)f^{(k+1)}(x)\mathrm{d} x
\end{gather}
$$

我们将 $\left. \phi_{k+1}(x)f^{(k)}(x) \right|_{0}^{1}$ 称为“边界项”，因为它只和 $\phi_{k+1}(x)f^{(k)}(x)$ 在区间 $[0,1]$ 的边界上的取值有关。从 $k=0$ 开始，利用上面的递推公式我们就可以得到

$$
\begin{align}
A=&\sum_{i=1}^{k} (-1)^{i+1} (\phi_{i+1}(1)f^{(i)}(1)-\phi_{i+1}(0)f^{(i)}(0)) \\
&+(-1)^{k+1}\int_{0}^{1}\phi_{k+1}(x)f^{(k+1)}(x)\mathrm{d} x
\end{align}
$$

于是，接下来我们的任务就是分析并给出 $\phi_{k}$ 的一个显式表达式。

# Bernoulli 多项式

直接通过算子 $\mathscr{A}$ 的定义，我们可以计算出前几个 $\phi_{k}$：

$$
\begin{gather}
\phi_{0}(x)=1 \\
\phi_{1}(x)=x-\dfrac{1}{2} \\
\phi_{2}(x)=\dfrac{x^{2}}{2}-\dfrac{x}{2}+\dfrac{1}{12} \\
\phi_{3}(x)=\dfrac{x^{4}}{24}-\dfrac{x^{3}}{12}+\dfrac{x^{2}}{24}-\dfrac{1}{720} \\
\phi_{4}(x)=\dfrac{x^{5}}{120}-\dfrac{x^{4}}{48}+\dfrac{x^{3}}{72}-\dfrac{x}{720}
\end{gather}
$$

注意到，每个 $\phi_{k}$ 的最高项的系数总是 $\dfrac{1}{k!}$，这使得计算变得非常复杂且不方便，因此，下面我们引入归一化的多项式，它有一个特殊的名字：

**定义 2** Bernoulli 多项式

第 $n$ 个 **Bernoulli 多项式**定义为

$$
\begin{gather}
B_{n}(x)=n! \phi_{n}(x)
\end{gather}
$$

于是，$\phi_{k}$ 的递归性质就转化为了 $B_{k}$ 的性质：

$$
\begin{gather}
B_{n+1}'(x)=(n+1)! \phi_{n+1}'(x)=(n+1)!\phi_{n}(x)=(n+1)B_{n}(x) \\
\int_{0}^{1}B_{n}(x)\mathrm{d} x=n! \int_{0}^{1}\phi_{n}(x)\mathrm{d} x=0, \quad n\geq 1
\end{gather}
$$

此外，$A$ 的等式也可以使用 Bernoulli 多项式给出：

$$
\begin{align}
A=&\sum_{i=1}^{k} (-1)^{i+1}\left( \dfrac{B_{i+1}(1)}{(i+1)!}f^{(i)}(1)-\dfrac{B_{i+1}(0)}{(i+1)!}f^{(i)}(0) \right) \\
&+\dfrac{(-1)^{k+1}}{(k+1)!} \int_{0}^{1} B_{k+1}(x)f^{(k+1)}(x)\mathrm{d} x
\end{align}
$$

可以看出，边界项的系数是由 Bernoulli 多项式在 0 和 1 处的取值决定的，我们列出前几项：

$$
\begin{align}
\begin{array}{c|cccccccc}
n & 0 & 1 & 2 & 3 & 4 & 5 & 6 & 7 \\
\hline
B_n(0) & 1 & -\dfrac{1}{2} & \dfrac{1}{6} & 0 & -\dfrac{1}{30} & 0 & \dfrac{1}{42} & 0 \\
B_n(1) & 1 & \dfrac{1}{2} & \dfrac{1}{6} & 0 & -\dfrac{1}{30} & 0 & \dfrac{1}{42} & 0 \\
\end{array}
\end{align}
$$

从中我们可以发现一些特征：$B_{n}(1)=B_{n}(0)$ 对 $n\geq 2$ 成立；奇数项 $B_{2k+1}(0)=0$ 对 $k\geq 1$ 成立。第一个特征是 Bernoulli 多项式性质的一个直接推论：我们有

$$
\begin{gather}
\int_{0}^{1}B_{n}(x)\mathrm{d} x=\dfrac{B_{n+1}(1)-B_{n+1}(0)}{n+1}=0, \quad n\geq 1
\end{gather}
$$

第二个性质我们将在后续进行证明。于是，我们可以将 $A$ 的表达式写成

$$
\begin{align}
A=&\sum_{k=1}^{M} \dfrac{B_{2k}(0)}{(2k)!}(f^{(2k-1)}(1)-f^{(2k-1)}(0)) \\
&-\dfrac{1}{(2M)!}\int_{0}^{1} B_{2M}(x)f^{(2M)}(x)\mathrm{d} x
\end{align}
$$

我们将系数 $B_{n}(0)$ 记作 $B_{n}$，称为第 $n$ 个 **Bernoulli 数**。这里我们将 $B_{1}$ 设置为了 $-\dfrac{1}{2}$，在一些文献中，也定义 $B_{1}=\dfrac{1}{2}$（即 $B_{n}=B_{n}(1)$），我们后面将看到，这两种定义并无本质上的区别。

# 生成函数

分析一个序列的常用方法是通过它的**生成函数**，即形式幂级数

$$
\begin{gather}
G(x,t)=\sum_{n=0}^{\infty} B_{n}(x) \dfrac{t^{n}}{n!}
\end{gather}
$$

通过 Bernoulli 多项式的性质，我们可以得到其生成函数的一个微分方程。具体来说，根据导数性质

$$
\begin{gather}
B_{n}'(x)=nB_{n-1}(x)
\end{gather}
$$

两边乘以 $\dfrac{t^{n}}{n!}$ 并求和，得到

$$
\begin{gather}
\partial_{x}G(x,t)=\sum_{n=0}^{\infty} B'_{n}(x) \dfrac{t^{n}}{n!}=\sum_{n=1}^{\infty} B_{n-1}(x) \dfrac{t^{n}}{(n-1)!}=t G(x,t)
\end{gather}
$$

固定 $t$，解得

$$
\begin{gather}
G(x,t)=C(t)e^{ xt }
\end{gather}
$$

其中 $C(t)$ 是一个不依赖于 $x$ 的函数。接下来，根据积分性质

$$
\begin{gather}
\int_{0}^{1}B_{n}(x)\mathrm{d} x=0, \quad n\geq 1
\end{gather}
$$

我们有

$$
\begin{gather}
\int_{0}^{1} G(x,t)\mathrm{d} x=\sum_{n=0}^{\infty} \left( \int_{0}^{1}B_{n}(x)\mathrm{d} x \right) \dfrac{t^{n}}{n!}=1
\end{gather}
$$

另一方面，根据 $G(x,t)=C(t)e^{ xt }$ 得到

$$
\begin{gather}
\int_{0}^{1} G(x,t)\mathrm{d} x=C(t) \int_{0}^{1} e^{ xt }\mathrm{d} x=C(t) \dfrac{e^{t}-1}{t}=1
\end{gather}
$$

从而 $C(t)=\dfrac{t}{e^{t}-1}$，这给出

$$
\begin{gather}
G(x,t)=\sum_{n=0}^{\infty} B_{n}(x) \dfrac{t^{n}}{n!}=\dfrac{te^{ xt }}{e^{ t }-1}
\end{gather}
$$

令 $x=0$，我们就得到了 Bernoulli 数列的指数生成函数

$$
\begin{gather}
\sum_{n=0}^{\infty} B_{n} \dfrac{t^{n}}{n!}=\dfrac{t}{e^{ t }-1}
\end{gather}
$$

几乎所有关于 Bernoulli 数的性质都可以从它的生成函数中提取出来。例如，我们可以得到奇数项的生成函数

$$
\begin{gather}
\sum_{k=0}^{\infty} B_{2k+1} \dfrac{t^{2k+1}}{(2k+1)!}=\dfrac{1}{2}\left( \dfrac{t}{e^{ t }-1}-\dfrac{-t}{e^{ -t }-1} \right)=-\dfrac{t}{2}
\end{gather}
$$

这就是说，除了 $B_{1}=-\dfrac{1}{2}$ 外，所有的奇数项均为 0. 另外，在 $G(x,t)$ 中令 $x=1$，得到

$$
\begin{gather}
\sum_{n=0}^{\infty} B_{n}(1) \dfrac{t^{n}}{n!}=\dfrac{te^{ t }}{e^{ t }-1}=\dfrac{t}{e^{t}-1}+t=t+\sum_{n=0}^{\infty} B_{n} \dfrac{t^{n}}{n!}
\end{gather}
$$

这表明，除了 $B_{1}$ 不同以外，两种 Bernoulli 数的定义是完全相同的。

此外，通过生成函数，我们还可以导出 Bernoulli 数的一个递推公式：

$$
\begin{gather}
G(0,t)(e^{ t }-1)=\left( \sum_{n=0}^{\infty} B_{n} \dfrac{t^{n}}{n!} \right)\left( \sum_{n=1}^{\infty} \dfrac{t^{n}}{n!} \right)=\sum_{n=1}^{\infty} \sum_{k=0}^{n-1} \binom{ n }{ k } B_{k} \dfrac{t^{n}}{n!}=t
\end{gather}
$$

取 $t^{n}$ 项的系数，就有

$$
\begin{gather}
\sum_{k=0}^{n-1} \binom{ n }{ k } B_{k}=0 \quad (n\geq 2), \quad B_{0}=1
\end{gather}
$$

由此，我们可以快速地计算 Bernoulli 数至任意项。

# Euler 的近似公式

让我们回到文章最初的问题：如何计算 $\displaystyle \sum_{n=1}^{\infty} \dfrac{1}{n^{2}}$ 的近似值？根据前面的分析，我们可知

$$
\begin{gather}
\sum_{n=1}^{\infty} \dfrac{1}{n^{2}}=1+\dfrac{1}{2}+\sum_{i=1}^{\infty} A_{i}
\end{gather}
$$

其中 $A_{i}$ 的值由一个平移后的函数 $f$ 给出：

$$
\begin{gather}
A_{i}=\dfrac{f(0)+f(1)}{2}-\int_{0}^{1}f(x)\mathrm{d} x
\end{gather}
$$

现在我们将定义域平移回区间 $[i,i+1]$ 上，从而我们有

$$
\begin{align}
A_{i}=&\sum_{k=1}^{M} \dfrac{B_{2k}}{(2k)!}(f^{(2k-1)}(i+1)-f^{(2k-1)}(i)) \\
&-\dfrac{1}{(2M)!}\int_{i}^{i+1} B_{2M}(x-i)f^{(2M)}(x)\mathrm{d} x
\end{align}
$$

将最后的积分项去除，我们就得到了 $A_{i}$ 的一个近似公式

$$
\begin{gather}
A_{i}\approx \sum_{k=1}^{M} \dfrac{B_{2k}}{(2k)!}(f^{(2k-1)}(i+1)-f^{(2k-1)}(i))
\end{gather}
$$

下面对 $i$ 求和，注意到这里也有一个“telescoping-sum”

$$
\begin{gather}
\sum_{i=1}^{\infty} A_{i} \approx - \sum_{k=1}^{M} \dfrac{B_{2k}}{(2k)!} f^{(2k-1)}(1)=\sum_{k=1}^{M} B_{2k}
\end{gather}
$$

这里我们注意到一个问题：$B_{2k}$ 的值并非很快地收敛到 $0$（事实上，这一级数是发散的），因此随着 $M$ 增大，右边的求和值将会快速地震荡，这是我们不乐于见到的。不过一切都还可以挽回：我们只需对求和式稍作变化

$$
\begin{gather}
\sum_{n=1}^{\infty} \dfrac{1}{n^{2}}=\sum_{n=1}^{9} \dfrac{1}{n^{2}}+\sum_{n=10}^{\infty} \dfrac{1}{n^{2}}
\end{gather}
$$

第一项是可以手动计算的，而对于第二项，我们可以重复前面的论述，得到

$$
\begin{align}
\sum_{n=10}^{\infty} \dfrac{1}{n^{2}}&=\int_{10}^{\infty} \dfrac{1}{x^{2}}\mathrm{d} x+\dfrac{1}{2}\cdot \dfrac{1}{10^{2}}+\sum_{i=10}^{\infty} A_{i} \\
&\approx \dfrac{1}{10}+\dfrac{1}{200}+\sum_{k=1}^{M} \dfrac{B_{2k}}{10^{2k+1}}
\end{align}
$$

这里，分母上的因子 $10^{2k+1}$ 使得最后一个求和中的项衰减地非常快，意味着仅通过计算非常少的项数，我们就可以得到足够的精确位数。例如，仅取 $M=9$ 即可计算出

$$
\begin{gather}
\sum_{n=1}^{\infty} \dfrac{1}{n^{2}}\approx 1.\underline{644934066848226436}947075
\end{gather}
$$

我们可以将其与精确值进行对比：

$$
\begin{gather}
\dfrac{\pi^{2}}{6}\approx 1.\underline{644934066848226436}472415
\end{gather}
$$

可见，通过这种方法，我们可以计算求和式的近似值至极高的精度。

# Euler-Maclaurin 求和公式

本文中我们发展的方法现在被称为 **Euler-Maclaurin 求和公式**，因为 Euler 和数学家 Maclaurin 几乎同时独立发现了它。它的一般形式如下：

$$
\begin{align}
\int_{i}^{i+1} f(x)\mathrm{d} x &=\dfrac{f(i)+f(i+1)}{2}-\sum_{k=1}^{M} \dfrac{B_{2k}}{(2k)!}(f^{(2k-1)}(i+1)-f^{(2k-1)}(i)) \\
&+ \dfrac{1}{(2M)!} \int_{i}^{i+1} B_{2M}(x-i) f^{(2M)}(x)\mathrm{d} x
\end{align}
$$

对 $i=a,a+1,\dots,b-1$ 求和，我们就得到了以下定理：

**定理 3** Euler-Maclaurin 求和公式

设整数 $a<b$，$f\in C^{2M}([a,b])$，则有下式成立：

$$
\begin{align}
\int_{a}^{b} f(x)\mathrm{d} x &=\sum_{n=a}^{b} f(n)- \dfrac{f(a)+f(b)}{2} \\
&-\sum_{k=1}^{M} \dfrac{B_{2k}}{(2k)!}(f^{(2k-1)}(b)-f^{(2k-1)}(a)) \\
&+ \dfrac{1}{(2M)!} \int_{a}^{b} B_{2M}(\{ x \}) f^{(2M)}(x)\mathrm{d} x
\end{align}
$$

其中 $\{ x \}=x-\lfloor x \rfloor$ 是 $x$ 的小数部分。

这一公式建立了离散求和 $\displaystyle \sum_{n=a}^{b}f(n)$ 与连续积分 $\displaystyle \int_{a}^{b}f(x)\mathrm{d}x$ 之间的关系。因此，它通常被用于推导各种和式的渐近公式，下面我们给出两例。

第一个例子是调和数

$$
\begin{gather}
H_{n}=\sum_{k=1}^{n} \dfrac{1}{k}
\end{gather}
$$

设 $f(x)=\dfrac{1}{x}$，将 Euler-Maclaurin 公式展开到第一阶即得

$$
\begin{align}
\sum_{k=1}^{n} \dfrac{1}{k}&\sim \int_{1}^{n} \dfrac{1}{x}\mathrm{d} x+C+\dfrac{1}{2n}-\dfrac{1}{12n^{2}} \\
&= \ln n+C+\dfrac{1}{2n}-\dfrac{1}{12n^{2}}
\end{align}
$$

与调和数的渐近展开 $H_{n}=\ln n+\gamma+\dfrac{1}{2n}-\dfrac{1}{12n^{2}}+O(n^{-3})$ 对比，可见上述公式与渐近展开之间只相差一个常数——这需要将更高阶的项纳入考虑范围。

第二个例子是阶乘函数

$$
\begin{gather}
n! = \exp\left( \sum_{k=1}^{n} \ln k \right)
\end{gather}
$$

我们取 $f(x)=\ln x$，则有

$$
\begin{align}
\sum_{k=1}^{n} \ln k &\sim \int_{1}^{n} \ln x\mathrm{d} x+C_{1}+\dfrac{1}{2}\ln n+\dfrac{1}{12n} \\
&=n\ln n-n+C_{1}+\dfrac{1}{2}\ln n+\dfrac{1}{12n}
\end{align}
$$

将上述公式代入 $n!$ 即得

$$
\begin{gather}
n! \sim C \sqrt{ n } \left( \dfrac{n}{e} \right)^{n}
\end{gather}
$$

同样，要得到经典的 Stirling 近似 $C=\sqrt{ 2\pi }$，我们需要分析更高阶数项的极限行为。

# 渐近级数

值得注意的是，对于 $C^{\infty}$ 函数 $f$，Euler-Maclaurin 公式在形式上能够给出一个无穷级数

$$
\begin{gather}
\sum_{n=a}^{b} f(n)=\int_{a}^{b} f(x)\mathrm{d} x+\dfrac{f(a)+f(b)}{2}+\sum_{k=1}^{\infty} \dfrac{B_{2k}}{(2k)!} (f^{(2k-1)}(b)-f^{(2k-1)}(a))
\end{gather}
$$

但这个级数通常不是收敛的：它是一个**渐近级数**。这意味着，随着截断阶数 $M$ 增大，起初部分和迅速接近精确值，到达一个最低误差点；但一旦到达某个临界点，后续项的绝对值将快速增大，使得部分和开始震荡，最终发散。

这种行为源于 Bernoulli 数的增长行为：$|B_{2k}|\sim \dfrac{2(2k)!}{(2\pi)^{2k}}$，远远高于大多数光滑函数导数的衰减速度。因此，对于给定的 $f$，存在一个最优的截断项数 $M^{*}$，使得误差达到最小。这种现象是渐近分析的固有特征，我们将在解析组合学的复渐近分析部分做进一步展开。