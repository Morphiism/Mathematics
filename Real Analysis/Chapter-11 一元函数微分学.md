现在我们正式开始研究微积分，与使用几何直观的切线定义相对，我们将使用极限来定义可微性与导数的概念。使用严格的分析定义的好处是，我们可以通过修改这些定义中的一小部分来把导数的概念推广至高维空间中的多元函数中，在那些地方，通常的几何直观是不起作用的。

# Section 1: 可微性

**定义 11.1.1** 可微（differentiable），导数（derivative）

设 $X\subset \mathbb{R}$，函数 $f\colon X\to \mathbb{R}$，$x_{0}\in X$ 是 $X$ 的极限点，如果极限

$$
\lim_{ x \to x_{0};x \in X } \dfrac{f(x)-f(x_{0})}{x-x_{0}}
$$

存在且等于实数 $L$，则称 $f$ 在 $x_{0}$ 处**可微**，且**导数**为 $L$，记作 $f'(x_{0})=L$. 反之则称 $f$ 在 $x_{0}$ 处不可微。如果对所有极限点 $x_{0}\in X$，$f$ 在 $x_{0}$ 处都可微，则称 $f$ 在 $X$ 上可微。

从定义中可见 $x_{0}$ 是极限点这个条件的必要性，因为当 $x=x_{0}$ 时表达式 $\dfrac{f(x)-f(x_{0})}{x-x_{0}}$ 将自动地无定义。因此，我们不会谈论孤立点上的导数，不过大多数时候 $X$ 都是一个区间，从而根据定理 9.1.9，$X$ 中的每一点都是 $X$ 的极限点，因此我们不必太担心这些问题。

有时候我们会用 $\left.\dfrac{\mathrm{d}f}{\mathrm{d}x}\right|_{x=x_{0}}$ 来表示 $f'(x_{0})$，但是要注意，$\dfrac{\mathrm{d}f}{\mathrm{d}x}$ 只是一个记号，而不能看成是一个分数表达式，尽管 $\mathrm{d}f$ 和 $\mathrm{d}x$ 有其自身独特的意义，但那要等到我们引入微分流形与切向量以后才能讨论。

下面的定理指出：如果 $f$ 在 $x_{0}$ 处可微，那么 $f$ 在 $x_{0}$ 附近是近似线性的。

**定理 11.1.2** Newton 逼近法

设 $X\subset \mathbb{R}$，函数 $f\colon X\to \mathbb{R}$，$x_{0}\in X$ 是 $X$ 的极限点，$L\in \mathbb{R}$，那么以下命题等价：

1. $f$ 在 $x_{0}$ 处可微，导数为 $L$
2. 对任意 $\varepsilon>0$，存在 $\delta>0$ 使得对任意满足 $d(x,x_{0})<\delta$ 的 $x \in X$ 有 $|f(x)-(f(x_{0})+L(x-x_{0}))|\leq\varepsilon |x-x_{0}|$

**证明**

首先设 $1$ 成立，则有 $\lim_{ x \to x_{0};x \in X }\dfrac{f(x)-f(x_{0})}{x-x_{0}}=L$，从而对任意 $\varepsilon>0$，存在 $\delta>0$ 使得对任意 $0<d(x,x_{0})<\delta$ 的 $x \in X$ 有

$$
\left| \dfrac{f(x)-f(x_{0})}{x-x_{0}}-L \right| = \dfrac{|f(x)-(f(x_{0})+L(x-x_{0}))|}{|x-x_{0}|}<\varepsilon
$$

当 $x=x_{0}$ 时，我们有 $|f(x)-(f(x_{0})+L(x-x_{0}))|=\varepsilon|x-x_{0}|=0$，即证 $2$.

反之，将上述证明倒过来写，根据定义我们就有 $1$ 成立。

简单来说，上述定理表明，如果 $f$ 在 $x_{0}$ 处可微，那么有近似式 $f(x)\approx f(x_{0})+f'(x_{0})(x-x_{0})$ 成立，反之亦然。

现在我们来看可微性与连续性的关系，我们可以证明：可微一定连续，但是连续不一定可微。

**定理 11.1.3**

设 $X\subset \mathbb{R}$，函数 $f\colon X\to \mathbb{R}$，$x_{0}\in X$ 是 $X$ 的极限点，如果 $f$ 在 $x_{0}$ 处可微，那么 $f$ 在 $x_{0}$ 处连续。

**证明**

根据 Newton 逼近法，对任意 $\varepsilon>0$，存在 $\delta>0$ 使得对任意 $d(x,x_{0})<\delta$ 的 $x \in X$ 有 $|f(x)-f(x_{0})-f'(x_{0})(x-x_{0})|\leq\varepsilon|x-x_{0}|$，于是

$$
\lim_{ x \to x_{0};x \in X } (f(x)-f(x_{0})-f'(x_{0})(x-x_{0}))=0
$$

由于最后一项的极限为 $0$，故 $\lim_{ x \to x_{0};x \in X }f(x)=f(x_{0})$，即 $f$ 在 $x_{0}$ 处连续。

由上述定理可知，如果函数 $f\colon X\to \mathbb{R}$ 在 $X$ 上可微，那么 $f$ 是 $X$ 上的连续函数。

下面我们给出人们熟知的导数计算法则。

**定理 11.1.4**

设 $X\subset \mathbb{R}$，$x_{0}\in X$ 是 $X$ 的极限点，函数 $f\colon X\to \mathbb{R},g\colon X\to \mathbb{R}$ 在 $x_{0}$ 处可微，则：

1. $(f+g)'(x_{0})=f'(x_{0})+g'(x_{0})$
2. Leibniz 法则：$(fg)'(x_{0})=f'(x_{0})g(x_{0})+f(x_{0})g'(x_{0})$
3. 如果对任意 $x \in X$ 有 $g(x)\neq 0$，则 $\left( \dfrac{1}{g} \right)'(x_{0})=-\dfrac{g'(x_{0})}{g(x_{0})^{2}}$

**证明**

只需使用极限的代数法则即可。对于 $1$，我们有

$$
\dfrac{f(x)+g(x)-(f(x_{0})+g(x_{0}))}{x-x_{0}}=\dfrac{f(x)-f(x_{0})}{x-x_{0}}+\dfrac{g(x)-g(x_{0})}{x-x_{0}}
$$

两边对 $x\to x_{0}$ 取极限即可。对于 $2$，我们有

$$
\dfrac{f(x)g(x)-f(x_{0})g(x_{0})}{x-x_{0}}=\dfrac{f(x)(g(x)-g(x_{0}))+(f(x)-f(x_{0}))g(x_{0})}{x-x_{0}}
$$

由于 $f$ 可微，故 $f$ 连续，从而 $\lim_{ x \to x_{0} }f(x)=f(x_{0})$. 对于 $3$，有

$$
\dfrac{1}{x-x_{0}}\left( \dfrac{1}{g(x)}-\dfrac{1}{g(x_{0})} \right)=-\dfrac{1}{x-x_{0}}\left( \dfrac{g(x)-g(x_{0})}{g(x)g(x_{0})} \right)
$$

这就完成了证明。

我们将法则 2 和 3 结合起来，并把 $\dfrac{f}{g}$ 看成 $f\cdot \dfrac{1}{g}$，就得到了商法则：

$$
\left( \dfrac{f}{g} \right)'(x_{0})=\dfrac{f'(x_{0})g(x_{0})-f(x_{0})g'(x_{0})}{g(x_{0})^{2}}
$$

下面我们考虑复合函数的导数法则，通常被称为链式法则：

**定理 11.1.5** 链式法则（chain rule）

设 $X,Y\subset \mathbb{R}$，$x_{0}\in X$ 是 $X$ 的极限点，$y_{0}\in Y$ 是 $Y$ 的极限点，函数 $f\colon X\to Y$ 在 $x_{0}$ 处可微，$y_{0}=f(x_{0})$，函数 $g\colon Y\to \mathbb{R}$ 在 $y_{0}$ 处可微，则函数 $g\circ f\colon X\to \mathbb{R}$ 在 $x_{0}$ 处可微，并且

$$
(g\circ f)'(x_{0})=g'(y_{0})f'(x_{0})=g'(f(x_{0}))f'(x_{0})
$$

**证明**

记 $f'(x_{0})=L,g'(y_{0})=M$，则对任意 $\varepsilon>0$，存在 $\delta>0$ 使得对任意 $d(y,y_{0})<\delta$ 的 $y \in Y$ 有

$$
|g(y)-g(y_{0})-M(y-y_{0})|\leq\varepsilon|y-y_{0}|
$$

对于这个 $\delta$，存在 $\eta>0$ 使得对任意 $d(x,x_{0})<\eta$ 的 $x \in X$ 有 $d(f(x),f(x_{0}))<\delta$，从而

$$
|g(y)-g(y_{0})-M(f(x)-f(x_{0}))|\leq\varepsilon|f(x)-f(x_{0})|
$$

再由 $f$ 的可微性，存在 $0<\theta<\eta$ 使得对任意 $d(x,x_{0})<\theta$ 的 $x \in X$ 有

$$
|f(x)-f(x_{0})-L(x-x_{0})|\leq\varepsilon|x-x_{0}|
$$

再根据

$$
\begin{align}
& |g(y)-g(y_{0})-M(f(x)-f(x_{0}))| \\
& = |g(y)-g(y_{0})-M(f(x)-f(x_{0})-L(x-x_{0}))-LM(x-x_{0})| \\
& \geq |g(y)-g(y_{0})-LM(x-x_{0})| - |M(f(x)-f(x_{0})-L(x-x_{0}))|
\end{align}
$$

我们就有

$$
\begin{align}
& |g(y)-g(y_{0})-LM(x-x_{0})| \\
& \leq |g(y)-g(y_{0})-M(f(x)-f(x_{0}))|+|M(f(x)-f(x_{0})-L(x-x_{0}))| \\
& \leq \varepsilon|f(x)-f(x_{0})-L(x-x_{0})+L(x-x_{0})|+M\varepsilon |x-x_{0}| \\
& \leq \varepsilon^{2}|x-x_{0}|+ L\varepsilon|x-x_{0}|+M\varepsilon|x-x_{0}|
\end{align}
$$

通过将 $\varepsilon$ 限制在 $(0,1)$ 之间，则有 $\varepsilon^{2}<\varepsilon$，从而根据 $\varepsilon$ 的任意性，由 Newton 逼近法知 $g\circ f$ 在 $x_{0}$ 处可微，且导数为 $LM=g'(y_{0})f'(x_{0})$.

利用 Leibniz 记号，我们可以将链式法则记为

$$
\dfrac{\mathrm{d} g}{\mathrm{d} x}=\dfrac{\mathrm{d} g}{\mathrm{d} f}\dfrac{\mathrm{d} f}{\mathrm{d} x}
$$

同样，我们需要强调：尽管 $\dfrac{\mathrm{d}f}{\mathrm{d}x}$ 有分式的特征，但它实际上不是一个分式。直观上，我们可以认为 $\mathrm{d}x,\mathrm{d}y$ 等是一种“无穷小数”，在标准分析中，无穷小是不存在的，然而的确有一门课程致力于使无穷小严格化，称为非标准分析。

下面，我们来实际计算一些函数的导数。

**命题 11.1.6**

常值函数 $f\colon \mathbb{R}\to \mathbb{R},f(x)=c$ 在 $\mathbb{R}$ 上可微，导数为 $0$. 设 $n$ 是整数，则函数 $f\colon \mathbb{R}\to \mathbb{R},f(x)=x^{n}$ 在 $\mathbb{R}$ 上可微，导数为 $nx^{n-1}$.

**证明**

常值函数满足 $\dfrac{f(x)-f(x_{0})}{x-x_{0}}=0$，从而极限 $f'(x_{0})=0$ 对所有 $x_{0}\in \mathbb{R}$ 成立。

我们使用归纳法证明当 $n$ 是正整数时 $(x^{n})'=nx^{n-1}$. 当 $n=1$ 时，我们有 $\dfrac{f(x)-f(x_{0})}{x-x_{0}}=\dfrac{x-x_{0}}{x-x_{0}}=1$，从而有 $f'(x_{0})=1=1x_{0}^{0}$. 假设对于 $n$ 有 $(x^{n})'=nx^{n-1}$，对于 $n+1$，我们有 $f(x)=x^{n}\cdot x$，则

$$
f'(x)=nx^{n-1}\cdot x+x^{n}=(n+1)x^{n}
$$

这就完成了证明。当 $n=0$ 时，$x^{0}$ 是常值函数，其导数为 $0=0x^{-1}$.

当 $n$ 是负整数时，我们有 $f(x)=\dfrac{1}{x^{-n}}$，根据商法则有

$$
f'(x)=-\dfrac{-nx^{-n-1}}{x^{-2n}}=nx^{n-1}
$$

即证。

当指数为实数时，我们将在学习了反函数导数法则后进行研究。首先我们给出一个引理：

**引理 11.1.7**

设 $X,Y\subset \mathbb{R}$，$x_{0}\in X$ 是 $X$ 的极限点，$y_{0}\in Y$ 是 $Y$ 的极限点，函数 $f\colon X\to Y$ 是双射，$y_{0}=f(x_{0})$，如果 $f$ 在 $x_{0}$ 处可微，并且 $f^{-1}$ 在 $y_{0}$ 处可微，那么

$$
(f^{-1})'(y_{0})=\dfrac{1}{f'(x_{0})}
$$

**证明**

根据链式法则可知

$$
(f^{-1}\circ f)'(x_{0})=(f^{-1})'(y_{0})f'(x_{0})
$$

而 $f^{-1}\circ f$ 是 $X$ 上的恒等函数 $x\mapsto x$，其导数为 $1$，这就完成了证明。

上述引理好像解决了反函数求导的问题，但它有一个重大缺陷：它假定 $f^{-1}$ 是可微的，这导致引理的条件过强而不方便使用。下面的定理弥补了这一缺陷，将引理的条件从可微弱化为连续。

**定理 11.1.8** 反函数定理（inverse function theorem）

设 $X,Y\subset \mathbb{R}$，$x_{0}\in X$ 是 $X$ 的极限点，$y_{0}\in Y$ 是 $Y$ 的极限点，函数 $f\colon X\to Y$ 是双射，$y_{0}=f(x_{0})$，如果 $f$ 在 $x_{0}$ 处可微，$f'(x_{0})\neq 0$，并且 $f^{-1}$ 在 $y_{0}$ 处连续，则 $f^{-1}$ 在 $y_{0}$ 处可微，并且

$$
(f^{-1})'(y_{0})=\dfrac{1}{f'(x_{0})}
$$

**证明**

我们需要证明对任意 $Y\setminus\{ y_{0} \}$ 中元素构成且收敛于 $y_{0}$ 的序列 $(y_{n})$ 有

$$
\lim_{ n \to \infty } \dfrac{f^{-1}(y_{n})-f^{-1}(y_{0})}{y_{n}-y_{0}}=\dfrac{1}{f'(x_{0})}
$$

由于 $f$ 是双射，故对每个 $y_{n}$，定义 $x_{n}=f^{-1}(y_{n})$，根据 $f^{-1}$ 的连续性，序列 $(x_{n})$ 收敛于 $f^{-1}(y_{0})=x_{0}$，再由 $f$ 的可微性知

$$
\lim_{ n \to \infty } \dfrac{f(x_{n})-f(x_{0})}{x_{n}-x_{0}}=f'(x_{0})
$$

由于 $f'(x_{0})\neq 0$，故由极限的代数性质得

$$
\lim_{ n \to \infty } \dfrac{x_{n}-x_{0}}{f(x_{n})-f(x_{0})}=\lim_{ n \to \infty } \dfrac{f^{-1}(y_{n})-f^{-1}(y_{0})}{y_{n}-y_{0}}=\dfrac{1}{f'(x_{0})}
$$

即证。

使用 Leibniz 记号，我们可以把反函数定理写成

$$
\dfrac{\mathrm{d} x}{\mathrm{d} y}=\dfrac{1}{\dfrac{\mathrm{d} y}{\mathrm{d} x}}
$$

现在我们就可以对 $x^{\alpha}$ 求导数了。

**命题 11.1.9**

设 $\alpha \in \mathbb{R}$，则函数 $f\colon (0,+\infty)\to \mathbb{R},f(x)=x^{\alpha}$ 在 $(0,+\infty)$ 上可微，其导数为 $\alpha x^{\alpha-1}$.

**证明**

首先设函数为 $f(x)=x^{1/n},n>0$，它是函数 $x\mapsto x^{n}$ 的反函数，根据定理 10.2.2，$f$ 在 $(0,+\infty)$ 上连续且严格递增，根据反函数定理，我们有

$$
f'(x)=\dfrac{1}{n(x^{1/n})^{n-1}}=\dfrac{1}{n}x^{1/n-1}
$$

设有理数 $q=\dfrac{a}{b},b>0$，则 $f(x)=x^{q}=(x^{1/b})^{a}$ 是一个复合函数，于是

$$
f'(x)=a(x^{1/b})^{a-1}\cdot \dfrac{1}{b} x^{1/b-1}=q x^{q-1}
$$

特别地，我们有 $f'(1)=q=\lim_{ x \to 1;x>0 }\dfrac{x^{q}-1}{x-1}$.

现设 $\alpha$ 是实数，我们有

$$
\lim_{ x \to x_{0};x>0 } \dfrac{x^{\alpha}-x_{0}^{\alpha}}{x-x_{0}}=x_{0}^{\alpha-1} \lim_{ x \to x_{0};x>0 } \dfrac{(x/x_{0})^{\alpha}-1}{x/x_{0}-1}
$$

因此我们需要证明 $\lim_{ x \to 1;x>0 }\dfrac{x^{\alpha}-1}{x-1}=\alpha$. 我们考虑左右极限。

当 $x>1$ 时，取收敛于 $\alpha$ 的有理数序列 $(q_{n})$ 使得 $\alpha\leq q_{n}$，则 $x^{\alpha}\leq x^{q_{n}}$，从而 $\lim_{ x \to 1;x>1 }\dfrac{x^{\alpha}-1}{x-1}\leq q_{n}$，令 $n\to \infty$，则 $\lim_{ x \to 1;x>1 }\dfrac{x^{\alpha}-1}{x-1}\leq \alpha$. 再取收敛于 $\alpha$ 的有理数序列 $(q_{n})$ 使得 $\alpha\geq q_{n}$，则 $x^{\alpha}\geq x^{q_{n}}$，同理有 $\lim_{ x \to 1;x>1 }\dfrac{x^{\alpha}-1}{x-1}\geq \alpha$，进而有 $\lim_{ x \to 1;x>1 }\dfrac{x^{\alpha}-1}{x-1}= \alpha$.

当 $x<1$ 时，同理有 $\lim_{ x \to 1;x \in(0,1) }\dfrac{x^{\alpha}-1}{x-1}= \alpha$，这就完成了证明。

# Section 2: 微分中值定理

导数的一个重要作用是找到函数的最大值和最小值，之前我们已定义了全局的最大值和最小值，现在我们要把这一概念局部化。

**定义 11.2.1** 极大值（local maximum），极小值（local minimum）

设 $X\subset \mathbb{R}$，函数 $f\colon X\to \mathbb{R}$，$x_{0}\in X$，称 $f$ 在 $x_{0}$ 处达到**极大值**，如果存在 $\delta>0$ 使得 $f$ 在 $X\cap(x_{0}-\delta,x_{0}+\delta)$ 上的限制函数 $f|_{X\cap(x_{0}-\delta,x_{0}+\delta)}$ 在 $x_{0}$ 处达到最大值；称 $f$ 在 $x_{0}$ 处达到**极小值**，如果存在 $\delta>0$ 使得 $f$ 在 $X\cap(x_{0}-\delta,x_{0}+\delta)$ 上的限制函数 $f|_{X\cap(x_{0}-\delta,x_{0}+\delta)}$ 在 $x_{0}$ 处达到最小值。

函数的最大值最多只有一个，但函数可以有多个极大值，并且最大值同样也是一个极大值。如果 $x_{0}$ 是 $X$ 的一个孤立点，那么 $f$ 在 $x_{0}$ 处同时达到极大和极小值。

下面的定理给出了寻找函数最大值的一种方法。

**定理 11.2.2** Fermat 引理

设实数 $a<b$，函数 $f\colon (a,b)\to \mathbb{R}$ 在 $x_{0}\in(a,b)$ 处可微，并且 $f$ 在 $x_{0}$ 处达到极大值或极小值，那么 $f'(x_{0})=0$.

**证明**

不妨设 $f$ 在 $x_{0}$ 处达到极大值，极小值的情况是类似的。根据定义，存在 $\delta>0$ 使得对任意 $x \in(x_{0}-\delta,x_{0}+\delta)\subset(a,b)$ 有 $f(x)\leq f(x_{0})$. 考虑定义式

$$
f'(x_{0})=\lim_{ x \to x_{0};x \in(a,b) } \dfrac{f(x)-f(x_{0})}{x-x_{0}}
$$

当 $x \in(x_{0},x_{0}+\delta)$ 时，我们有 $\dfrac{f(x)-f(x_{0})}{x-x_{0}}\leq 0$，故 $f'(x_{0})\leq 0$；当 $x \in(x_{0}-\delta,x_{0})$ 时，我们有 $\dfrac{f(x)-f(x_{0})}{x-x_{0}}\geq 0$，故 $f'(x_{0})\geq 0$，因此 $f'(x_{0})=0$.

注意，上述定理对闭区间 $[a,b]$ 不成立：定义在 $[1,2]$ 上的函数 $x\mapsto 2x$ 在 $x=2$ 处有极大值，但是其导数为 $2\neq 0$. 因此，当我们在求闭区间上的函数的最大值时，除了要检查导数为 $0$ 的点外，还要检查区间的端点。此外，我们还要注意：上述定理的逆定理不成立，例如函数 $x\mapsto x^{3}$ 在 $x=0$ 处导数为 $0$，但 $x=0$ 不是函数的极大或极小值点。

结合 Fermat 引理和最值定理，我们可以得到以下定理：

**定理 11.2.3** Rolle 定理

设实数 $a<b$，函数 $f\colon [a,b]\to \mathbb{R}$ 是连续函数，并且在 $(a,b)$ 上可微，$f(a)=f(b)$，则存在一点 $\xi \in(a,b)$ 使得 $f'(\xi)=0$.

**证明**

根据最值定理，$f$ 在 $[a,b]$ 上有最大值 $M$，最小值 $m$. 如果 $M=m$，那么 $f$ 是常值函数，对任意 $x \in[a,b]$ 都有 $f'(x)=0$.

如果 $m<M$，我们断言 $f$ 必定在 $(a,b)$ 中的一点 $\xi$ 达到最大值或最小值，从而 $f'(\xi)=0$. 如若不然，则 $f$ 在区间的端点处达到最大值和最小值，又根据 $f(a)=f(b)$，故 $M=m$，这与 $m<M$ 矛盾。

利用 Rolle 定理，我们可以证明 Lagrange 中值定理，它是微分学中一个非常重要且基本的定理。

**定理 11.2.4** Lagrange 中值定理

设实数 $a<b$，函数 $f\colon [a,b]\to \mathbb{R}$ 是连续函数，并且在 $(a,b)$ 上可微，则存在一点 $\xi \in(a,b)$ 使得

$$
f'(\xi)=\dfrac{f(b)-f(a)}{b-a}
$$

**证明**

证明思路是将 $f$ 转化，使其满足 Rolle 定理的条件。我们考虑函数 $F\colon [a,b]\to \mathbb{R}$ 满足

$$
F(x)=f(x)-\dfrac{f(b)-f(a)}{b-a}x
$$

$F$ 是连续函数，并且在 $(a,b)$ 上可微，并且 $F(a)=F(b)$，根据 Rolle 定理，存在 $\xi \in(a,b)$ 使得 $F'(\xi)=0$，即 $f'(\xi)=\dfrac{f(b)-f(a)}{b-a}$.

Lagrange 中值定理有一个更常用的推广：Cauchy 中值定理，我们正是使用这种形式的中值定理来分析熟知的 L'Hospital 法则以及 Taylor 公式的 Lagrange 余项定理。

**定理 11.2.5** Cauchy 中值定理

设实数 $a<b$，函数 $f\colon [a,b]\to \mathbb{R},g\colon [a,b]\to \mathbb{R}$ 是连续函数，且都在 $(a,b)$ 上可微，则存在一点 $\xi \in(a,b)$ 使得

$$
(g(b)-g(a))f'(\xi)=(f(b)-f(a))g'(\xi)
$$

**证明**

我们考虑函数 $h\colon [a,b]\to \mathbb{R}$ 满足

$$
h(x)=(g(b)-g(a))f(x)-(f(b)-f(a))g(x)
$$

则 $h$ 是连续函数，且在 $(a,b)$ 上可微，而且 $h(a)=h(b)$，故根据 Rolle 定理，存在 $\xi \in(a,b)$ 使得 $h'(\xi)=(g(b)-g(a))f'(\xi)-(f(b)-f(a))g'(\xi)=0$，即证。

如果 $g(b)\neq g(a)$ 且 $g'(\xi)\neq 0$，那么可以将 Cauchy 中值定理写成

$$
\dfrac{f'(\xi)}{g'(\xi)}=\dfrac{f(b)-f(a)}{g(b)-g(a)}
$$

可见，Lagrange 中值定理是 Cauchy 中值定理在 $g(x)=x$ 时的特例。

下面，我们给出一个大家都熟悉的法则。

**定理 11.2.6** L'Hospital 法则（ $0/0$ 型）

设实数 $a<b$，函数 $f\colon [a,b]\to \mathbb{R},g\colon [a,b]\to \mathbb{R}$ 是连续函数，并且在 $(a,b)$ 上可微，如果 $f(a)=g(a)=0$，且对任意 $x \in(a,b)$ 有 $g'(x)\neq 0$，$L\in \mathbb{R}$，那么

$$
\lim_{ x \to a; x \in(a,b) } \dfrac{f'(x)}{g'(x)}=L \implies \lim_{ x \to a; x \in(a,b) } \dfrac{f(x)}{g(x)}=L
$$

**证明**

首先证明对任意 $x \in(a,b)$ 有 $g(x)\neq 0$. 假设 $g(x_{0})=0$，那么根据 Rolle 定理，存在 $\xi \in(a,x_{0})$ 使得 $g'(\xi)=0$，但这与 $g'(x)\neq 0$ 矛盾。

现设 $x \in(a,b)$，由于 $f(a)=g(a)=0$，因此根据 Cauchy 中值定理有

$$
\dfrac{f(x)}{g(x)}=\dfrac{f(x)-f(a)}{g(x)-g(a)}=\dfrac{f'(\xi)}{g'(\xi)},a<\xi<x
$$

由于 $\lim_{ x \to a ; x \in(a,b) }\dfrac{f'(\xi)}{g'(\xi)}=L$，故 $\lim_{ x \to a; x \in(a,b) } \dfrac{f(x)}{g(x)}=L$，即证。

上面的定理只考虑了 $a$ 右侧的极限，对于 $a$ 左侧以及两侧的极限，我们有类似的命题，我们很容易叙述并证明这些命题。L'Hospital 定理还有另一种形式，通常被称为 $\infty/\infty$ 型，尽管定理只要求分母 $g(x)\to \infty$ 即可。

**定理 11.2.7** L'Hospital 法则（ $\infty/\infty$ 型）

设实数 $a<b$，函数 $f\colon (a,b)\to \mathbb{R},g\colon (a,b)\to \mathbb{R}$ 在 $(a,b)$ 上可微，如果 $\lim_{ x \to a; x \in(a,b) }g(x)=\pm \infty$，$L\in \mathbb{R}$，则

$$
\lim_{ x \to a; x \in(a,b) } \dfrac{f'(x)}{g'(x)}=L \implies \lim_{ x \to a; x \in(a,b) } \dfrac{f(x)}{g(x)}=L
$$

**证明**

由于 $\lim_{ x \to a; x \in(a,b) }g(x)=\pm \infty$，故存在 $\delta_{0}>0$ 使得对任意 $a<x<a+\delta_{0}$ 有 $|g(x)|>0$，即 $g(x)\neq 0$.

根据定义，对任意 $\varepsilon>0$，存在 $0<\delta_{1}<\delta_{0}-a$ 使得对任意 $a<x<a+\delta_{1}$ 有

$$
L-\varepsilon<\dfrac{f'(x)}{g'(x)}<L+\varepsilon
$$

设 $t=a+\delta_{1}$，由于 $f,g$ 在 $[x,t]$ 上连续且可微，故由 Cauchy 中值定理有

$$
L-\varepsilon<\dfrac{f(x)-f(t)}{g(x)-g(t)}<L+\varepsilon
$$

不妨设 $\lim_{ x \to a; x \in(a,b) }g(x)=+\infty$，则存在 $0<\delta_{2}<\delta_{1}-a$ 使得对任意 $a<x<a+\delta_{2}$ 有 $g(x)>g(t)$，从而

$$
(L-\varepsilon)\left( 1-\dfrac{g(t)}{g(x)} \right)+\dfrac{f(t)}{g(x)}<\dfrac{f(x)}{g(x)}<(L+\varepsilon)\left( 1-\dfrac{g(t)}{g(x)} \right)+\dfrac{f(t)}{g(x)}
$$

对 $x\to a$ 取极限，由 $\lim_{ x \to a; x \in(a,b) }\dfrac{1}{g(x)}=0$ 得

$$
L-\varepsilon\leq \lim_{ x \to a; x \in(a,b) } \dfrac{f(x)}{g(x)}\leq L+\varepsilon
$$

由 $\varepsilon$ 的任意性得 $\lim_{ x \to a; x \in(a,b) } \dfrac{f(x)}{g(x)}=L$.

同样，上述定理只考虑了 $a$ 右侧的极限，对于左侧以及两侧的极限，其叙述和证明是类似的。

导数的另一个常用的应用是判断函数的单调性，例如，你可能知道导数为正表明函数单调递增，导数为负表明函数单调递减。下面我们给出这些断言的准确表述。

**定理 11.2.8**

设 $X\subset \mathbb{R}$，$x_{0}\in X$ 是 $X$ 的极限点，函数 $f\colon X\to \mathbb{R}$ 在 $x_{0}$ 处可微，那么如果 $f$ 单调递增，则 $f'(x_{0})\geq 0$；如果 $f$ 单调递减，则 $f'(x_{0})\leq 0$.

**证明**

如果 $f$ 单调递增，那么对任意 $x \in X\setminus\{ x_{0} \}$ 有 $\dfrac{f(x)-f(x_{0})}{x-x_{0}}\geq 0$，从而 $f'(x_{0})\geq 0$，反之亦然。

可能有人认为，如果 $f$ 严格递增，那么导数 $f'(x_{0})>0$，然而，这是错误的：函数 $x\mapsto x^{3}$ 在 $x=0$ 处导数为 $0$，但是函数是严格递增的。不过，我们的确有一个相反的结果，它指出：如果导数 $f'(x)>0$，那么 $f$ 严格递增。

**定理 11.2.9**

设实数 $a<b$，函数 $f\colon [a,b]\to \mathbb{R}$ 是连续函数，在 $(a,b)$ 上可微，并且对任意 $x \in(a,b)$ 有 $f'(x)>0$，那么 $f$ 严格递增；如果对任意 $x \in(a,b)$ 有 $f'(x)<0$，那么 $f$ 严格递减；如果对任意 $x \in(a,b)$ 有 $f'(x)=0$，那么 $f$ 是常值函数。

**证明**

我们使用中值定理进行证明。设 $a\leq x<y\leq b$，由 Lagrange 中值定理得

$$
f(y)-f(x)=f'(\xi)(y-x),x<\xi<y
$$

因此，当 $f'(\xi)>0$ 时，$f$ 严格递增，当 $f'(\xi)<0$ 时，$f$ 严格递减，当 $f'(\xi)=0$ 时，$f$ 是常值函数。

导数 $f'(x)=0$ 的情况有一个推论，它是我们做不定积分的基础：

**定理 11.2.10**

设实数 $a<b$，函数 $f\colon [a,b]\to \mathbb{R},g\colon [a,b]\to \mathbb{R}$ 是连续函数，在 $(a,b)$ 上可微，并且对任意 $x \in(a,b)$ 有 $f'(x)=g'(x)$，则存在 $C\in \mathbb{R}$ 使得对任意 $x \in[a,b]$ 有 $f(x)=g(x)+C$.

**证明**

对函数 $h\colon [a,b]\to \mathbb{R},h(x)=f(x)-g(x)$ 应用定理 11.2.9，则 $h$ 是常值函数，从而存在 $C\in \mathbb{R}$ 使得对任意 $x \in[a,b]$ 有 $h(x)=f(x)-g(x)=C$.

最后，我们来考虑导函数自身的性质，下面的定理指出：如果 $f$ 在闭区间 $[a,b]$ 上可微，那么导函数 $f'$ 自动地满足介值定理。

**定理 11.2.11** Darboux 定理

设实数 $a<b$，函数 $f\colon [a,b]\to \mathbb{R}$ 在 $[a,b]$ 上可微，设 $\alpha \in \mathbb{R}$ 满足 $f'(a)<\alpha<f'(b)$ 或 $f'(b)<\alpha<f'(a)$，则存在 $c \in(a,b)$ 使得 $f'(c)=\alpha$.

**证明**

定义函数 $g\colon [a,b]\to \mathbb{R},g(x)=f(x)-\alpha x$，不妨设 $f'(a)<\alpha<f'(b)$，则有 $g'(a)<0<g'(b)$，我们需要找到 $c \in(a,b)$ 使得 $g'(c)=0$.

由于 $g'(a)<0$，即 $\lim_{ x \to a; x \in[a,b] }\dfrac{g(x)-g(a)}{x-a}<0$，故存在 $0<\delta_{1}<b-a$ 使得对任意 $a<x<a+\delta_{1}$ 有 $g(x)<g(a)$，取 $t_{1} \in(a,a+\delta_{1})$，同理可以取 $t_{2}\in(b-\delta_{2},b)$ 使得 $g(t_{2})>g(b)$，这表明 $g$ 的最大值和最小值都在 $(a,b)$ 中达到，从而存在 $c \in(a,b)$ 使得 $g'(c)=0$，即证。

# Section 3: Taylor 公式

现在我们回顾一下 Newton 逼近法的内涵，它指出：如果函数 $f$ 在 $x_{0}$ 处可微，那么在 $x_{0}$ 附近有近似式 $f(x)\approx f(x_{0})+f'(x_{0})(x-x_{0})$，现在我们要问，这个近似有多好？也就是说，误差项

$$
R(x)=f(x)-(f(x_{0})+f'(x_{0})(x-x_{0}))
$$

有多大？Newton 逼近法指出，$\lim_{ x \to x_{0} }\dfrac{R(x)}{x-x_{0}}=0$，但我们是否可以更进一步，求出 $R(x)$ 的具体表达式？利用中值定理，这是可行的。

我们从头开始，首先假设 $f\colon [a,b]\to \mathbb{R}$ 是连续函数，并且在 $(a,b)$ 上可微，$x_{0}\in(a,b)$，并且 $R_{0}(x)=f(x)-f(x_{0})$，那么

$$
\dfrac{R_{0}(x)}{x-x_{0}}=\dfrac{R_{0}(x)-R_{0}(x_{0})}{x-x_{0}}=R_{0}'(\xi)=f'(\xi)
$$

因此 $R_{0}(x)=f'(\xi)(x-x_{0})$，这就是 Lagrange 中值定理。

现在，如果我们假定 $f'$ 也在 $(a,b)$ 上可微（也就是说 $f$ 在 $(a,b)$ 上二次可微），并且 $R_{1}(x)=f(x)-f(x_{0})-f'(x_{0})(x-x_{0})$，那么就有

$$
\dfrac{R_{1}'(x)}{x-x_{0}}=\dfrac{R_{1}'(x)-R_{1}'(x_{0})}{x-x_{0}}=R_{1}''(\xi)=f''(\xi)
$$

于是我们得到 $R_{1}'(x)=f''(\xi)(x-x_{0})$，则 $R_{1}(x)=\dfrac{f''(\xi)}{2}(x-x_{0})^{2}+C$，因为 $R_{1}(x_{0})=0$ 故 $C=0$. 于是我们就求出了 Newton 近似的 Lagrange 余项。

现在，让我们继续思考：如果 $f$ 在 $(a,b)$ 上三次可导，那么我们是否可以有一个更加精确的近似？如果有，那么余项是什么形式的？

根据已有的近似项，我们可以猜测 $f$ 的近似式为

$$
f(x)\approx f(x_{0})+f'(x_{0})(x-x_{0})+k(x-x_{0})^{2}
$$

现在我们来考虑余项 $R_{2}(x)$，回顾前面的证明，我们发现，我们需要让 $R_{2}''(x_{0})=0$，这样 $R_{2}(x)$ 的形式才能是 $c(x-x_{0})^{3}$，因此我们有

$$
R_{2}''(x_{0})=f''(x_{0})-2k=0 \implies k=\dfrac{f''(x_{0})}{2}
$$

从而

$$
\dfrac{R_{2}''(x)}{x-x_{0}}=\dfrac{R_{2}''(x)-R_{2}''(x_{0})}{x-x_{0}}=R_{2}'''(\xi)=f'''(\xi)
$$

于是 $R_{2}''(x)=f'''(\xi)(x-x_{0})$，由于 $R_{2}(x_{0})=R_{2}'(x_{0})=0$，故 $R_{2}(x)=\dfrac{f'''(\xi)}{2\cdot 3}(x-x_{0})^{3}$，令 $n! = n\cdot (n-1)! = n\cdot(n-1)\cdots 2\cdot 1$ 称为 $n$ 的**阶乘**（factorial），则 $R_{2}(x)=\dfrac{f'''(\xi)}{3!}(x-x_{0})^{3}$.

现在这一规律应该很明显了：我们有

$$
R_{n}(x)=f(x)-\sum_{k=0}^{n} \dfrac{f^{(k)}(x_{0})}{k!}(x-x_{0})^{k}=\dfrac{f^{(n+1)}(\xi)}{(n+1)!}(x-x_{0})^{n+1}
$$

其中 $0! =1$，$f^{(n)}$ 是 $f$ 的 $n$ 阶导数，例如 $f^{(0)}=f,f^{(1)}=f',f^{(2)}=f''$ 等等，$\xi$ 是介于 $x$ 和 $x_{0}$ 之间的实数。以上就是我们熟知的一元函数的 Taylor 公式的主要内容，其中阶乘 $k!$ 的出现是非常自然的：我们需要 $R_{n}^{(k)}(x_{0})=0$，通过待定系数法我们就知道 $(x-x_{0})^{k}$ 的系数就是 $\dfrac{f^{(k)}(x_{0})}{k!}$.

**定理 11.3.1** Taylor 公式（带 Lagrange 余项）

设实数 $a<b$，函数 $f\colon [a,b]\to \mathbb{R}$ 满足 $f^{(n)}$ 在 $[a,b]$ 上连续，并且 $f^{(n)}$ 在 $(a,b)$ 上可微，那么对任意 $x,x_{0}\in[a,b]$，存在 $x\leq\xi\leq x_{0}$ 或者 $x_{0}\leq\xi\leq x$ 使得

$$
R_{n}(x)=f(x)-\sum_{k=0}^{n} \dfrac{f^{(k)}(x_{0})}{k!}(x-x_{0})^{k}=\dfrac{f^{(n+1)}(\xi)}{(n+1)!}(x-x_{0})^{n+1}
$$

**证明**

根据导数的计算法则，我们有 $R_{n}^{(k)}(x_{0})=0,k=0,1,\dots,n$. 设 $G(x)=(x-x_{0})^{n+1}$，则同样有 $G^{(k)}(x_{0})=0,k=0,1,\dots,n$. 由于 $f^{(n)}$ 在 $[a,b]$ 上连续，故 $f^{(k)},k=0,1,\dots,n-1$ 在 $[a,b]$ 上连续且可微。

不妨设 $x_{0}<x$，则由 Cauchy 中值定理有

$$
\dfrac{R_{n}(x)}{G(x)}=\dfrac{R_{n}'(\xi_{1})}{G'(\xi_{1})}=\dots=\dfrac{R_{n}^{(n)}(\xi_{n})}{G^{(n)}(\xi_{n})}=\dfrac{R_{n}^{(n+1)}(\xi)}{G^{(n+1)}(\xi)}=\dfrac{f^{(n+1)}(\xi)}{(n+1)!}
$$

其中 $x_{0}<\xi<\xi_{n}<\dots<\xi_{1}<x$，这就完成了证明。

上述定理是 Lagrange 中值定理的推广，当 $x_{0}=0$ 时，上述定理就称为带 Lagrange 余项的 Maclaurin 公式。

有时候，我们不需要那么精确的余项 $R_{n}(x)$，而只需要一个近似公式，就像 Newton 逼近法一样，那么这时候 Taylor 公式的条件就可以适当地放宽，如下定理所示：

**定理 11.3.2** Taylor 公式（带 Peano 余项）

设实数 $a<b$，函数 $f\colon (a,b)\to \mathbb{R}$ 在 $x_{0}\in(a,b)$ 处有 $n$ 阶导数 $f^{(n)}(x_{0})$，则

$$
\lim_{ x \to x_{0};x \in(a,b) } \dfrac{R_{n}(x)}{(x-x_{0})^{n}}=0
$$

其中 $R_{n}(x)=f(x)-\sum_{k=0}^{n} \dfrac{f^{(k)}(x_{0})}{k!}(x-x_{0})^{k}$.

**证明**

由于 $f$ 在 $x_{0}$ 处有 $n$ 阶导数 $f^{(n)}(x_{0})$，故存在 $\delta_{1}>0$ 使得对任意 $x \in(x_{0}-\delta_{1},x_{0}+\delta_{1})\subset(a,b)$，$f$ 在 $x$ 处有 $n-1$ 阶导数 $f^{(n-1)}(x)$，从而存在 $0<\delta<\delta_{1}$ 使得对任意 $x \in[x_{0}-\delta,x_{0}+\delta]$，$f^{(k)},k=0,1,\dots,n-2$ 在 $x$ 处连续且可微。于是由 L'Hospital 法则得

$$
\lim_{ x \to x_{0} } \dfrac{R_{n}(x)}{(x-x_{0})^{n}}=\lim_{ x \to x_{0} } \dfrac{R_{n}'(x)}{n(x-x_{0})^{n-1}}=\dots=\lim_{ x \to x_{0} } \dfrac{R_{n}^{(n-1)}(x)}{n!(x-x_{0})}
$$

而

$$
\lim_{ x \to x_{0} } \dfrac{R_{n}^{(n-1)}(x)}{x-x_{0}}=\lim_{ x \to x_{0} }\dfrac{f^{(n-1)}(x)-f^{(n-1)}(x_{0})-f^{(n)}(x_{0})(x-x_{0})}{x-x_{0}}=0
$$

这就完成了证明。

上述定理中的余项 $R_{n}(x)$ 称为 Peano 余项，当 $n=1$ 时，上述定理就是 Newton 逼近法。因此，上面的定理指出：如果 $f$ 在 $x_{0}$ 处有 $n$ 阶导数，那么有近似式

$$
f(x)\approx \sum_{k=0}^{n} \dfrac{f^{(k)}(x_{0})}{k!}(x-x_{0})^{k}
$$

后者通常称为 Taylor 多项式。之后，在我们研究函数的幂级数展开时，我们还会提到 Taylor 公式，在那时，我们将令指数 $n$ 趋于无穷，从而构成所谓的 Taylor 级数。那里的很多内容都是建立在带 Lagrange 余项的 Taylor 公式上的。