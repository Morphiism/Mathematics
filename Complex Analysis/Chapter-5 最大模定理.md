本章我们来深入研究最大模定理及其推论，我们将给出最大模定理的另一个证明，以及它的各种不同版本。剩下的章节我们将探讨这一极大原理的各种推广及其应用。

# Section 1: 极大原理

我们首先利用开映射定理给出最大模定理的另一个证明。设 $\Omega \subset \mathbb{C}$，并设 $\alpha$ 位于 $\Omega$ 的内部，则存在 $\rho>0$ 使得 $B(\alpha,\rho)\subset\Omega$，这表明存在 $\xi \in\Omega$ 使得 $|\alpha|<|\xi|$. 换句话说，如果 $\alpha$ 满足 $|\alpha|\geq |\xi|$ 对任意 $\xi \in\Omega$ 成立，那么一定有 $\alpha \in \partial\Omega$.

**定理 5.1.1** 最大模定理 I

如果 $f$ 在区域 $G$ 上解析，并且存在 $a \in G$ 使得对任意 $z \in G$ 有 $|f(a)|\geq |f(z)|$，那么 $f$ 是一个常值函数。

**证明**

假设 $f$ 非常值，那么开映射定理表明 $f[G]$ 是一个开集。然而，根据上文的讨论，如果 $|f(a)|\geq |f(z)|$ 对任意 $z \in G$ 成立，那么 $f(a)$ 必定属于 $f[G]$ 的边界，矛盾。因此 $f$ 是常值函数。

以上定理的另一种表述为：解析函数模的最大值（如果有的话）必定在边界处取到。

**定理 5.1.2** 最大模定理 II

设 $G\subset \mathbb{C}$ 是一个有界开集，函数 $f$ 在 $\overline{G}$ 上连续，在 $G$ 上解析，则

$$
\begin{gather}
\max \{ |f(z)| \mid z \in \overline{G} \}=\max \{ |f(z)| \mid z \in \partial G \}
\end{gather}
$$

**证明**

由于 $G$ 有界，故 $\overline{G}$ 紧致，从而 $|f|$ 在 $\overline{G}$ 上有最大值点 $a$. 如果 $f$ 是常值函数，那么结论是平凡的；如果 $f$ 非常值，假设 $a \in G$，那么 $a$ 属于 $G$ 的一个连通分量 $C$，由于 $G$ 是开集，故 $C$ 是开的，从而由最大模定理知 $f$ 在 $C$ 上为常值函数。又由于 $f$ 在 $\overline{C}$ 上连续，故 $f$ 的最大值也在 $\partial C\subset \partial G$ 上取到。

以上定理中 $G$ 有界的假设是不能去掉的。我们可以构造范例如下：令 $G=\left\{  x+iy \mid - \dfrac{\pi}{2}<y<\dfrac{\pi}{2}  \right\}$ 并取 $f(z)=\exp(e^{z})$，则 $f$ 在 $\overline{G}$ 上连续且在 $G$ 上解析。如果 $z \in \partial G$，则 $z=x\pm i \dfrac{\pi}{2}$，于是 $|f(z)|=\lvert \exp(\pm ie^{x}) \rvert=1$. 然而，当 $x$ 沿着实轴趋于 $\infty$ 时，$f(x) \to \infty$.

不过，由以上的例子可见，最大模定理不再成立的原因来自函数 $f$ 在无穷远点的行为。因此，我们可以将 $G$ 有界的假设替换为 $|f|$ 在无穷远处的增长上界。首先，我们给出一些定义：

**定义 5.1.3** 上极限（limit superior），下极限（limit inferior）

设 $G\subset \mathbb{C}$，函数 $f\colon G\to \mathbb{R}$，$a \in \overline{G}$ 或 $a=\infty$，则 $f$ 在 $z$ 趋于 $a$ 时的**上极限**定义为

$$
\begin{gather}
\limsup_{ z \to a } f(z)=\lim_{ r \to 0+ } \sup \{ f(z) \mid z \in G\cap B(a,r) \}
\end{gather}
$$

其中当 $a=\infty$ 时 $B(a,r)$ 取 $\mathbb{C}_{\infty}$ 上的度量。类似地，定义 $f$ 在 $z$ 趋于 $a$ 时的**下极限**为

$$
\begin{gather}
\liminf_{ z \to a } f(z)=\lim_{ r \to 0+ } \inf \{ f(z) \mid z \in G\cap B(a,r) \}
\end{gather}
$$

容易证明，$\lim_{ z \to a }f(z)$ 存在且等于 $\alpha$ 当且仅当 $f$ 的上极限与下极限相等且等于 $\alpha$.

设 $G\subset \mathbb{C}$，我们定义 $G$ 的**扩展边界** $\partial_{\infty}G$ 为 $G$ 在 $\mathbb{C}_{\infty}$ 中的边界。换句话说，如果 $G$ 有界，那么 $\partial_{\infty}G=\partial G$；如果无界，那么 $\partial_{\infty}G=\partial G\cup \{ \infty \}$.

**定理 5.1.4** 最大模定理 III

设 $f$ 在区域 $G$ 上解析，假设存在常数 $M$ 使得对任意 $a \in \partial_{\infty}G$ 有 $\limsup_{ z \to a }|f(z)|\leq M$，则对 $z \in G$ 有 $|f(z)|\leq M$.

**证明**

任取 $\delta>0$，令 $H=\{ z \in G \mid |f(z)|>M+\delta \}$，则我们要证 $H=\varnothing$.

由于 $|f|$ 连续，故 $H$ 是一个开集。由于 $\limsup_{ z \to a }|f(z)|\leq M$ 对任意 $a \in \partial_{\infty}G$ 成立，故存在 $B(a,r)$ 使得 $|f(z)|<M+\delta$ 对 $z \in G\cap B(a,r)$ 成立，因此 $\overline{H}\subset G$. 此外，由于以上不等式对 $a=\infty$ 也成立，故 $H$ 必定是有界的，从而 $\overline{H}$ 是紧致集。于是我们可以应用定理 5.1.2. 然而，对于 $z \in \partial H$，我们有 $|f(z)|=M+\delta$，从而对于 $z \in H$ 有 $|f(z)|\leq M+\delta$，这表明 $H=\varnothing$，即证。

尽管以上三个不同版本的最大模定理其表述有很大的区别，但它们的本质是一致的：解析函数在区域内部的模长受其在边界上的模长控制。其中，定理 5.1.2 描述了有界区域的边界，而定理 5.1.4 描述了无穷远边界。

# Section 2: Schwarz 引理

最大模定理的一个重要推论是 Schwarz 引理，它允许我们对单位圆盘 $D=\{ z \mid |z|<1 \}$ 上的共形映射进行分类。

**定理 5.2.1** Schwarz 引理

设 $D=\{ z \mid |z|<1 \}$，$f$ 在 $D$ 上解析，满足

1. $|f(z)|\leq 1$ 对任意 $z \in D$ 成立
2. $f(0)=0$

那么 $|f'(0)|\leq 1$ 且 $|f(z)|\leq|z|$ 对 $z \in D$ 成立。此外，如果 $|f'(0)|=1$ 或者存在 $z\neq 0$ 使得 $|f(z)|=|z|$，那么存在 $|c|=1$ 使得 $f(w)=cw$ 对 $w \in D$ 成立。

**证明**

定义 $g\colon D\to \mathbb{C}$ 为 $g(z)=\dfrac{f(z)}{z},z\neq 0$，且 $g(0)=f'(0)$，则 $g$ 在 $D$ 上解析。根据最大模定理，对 $0<r<1$ 有 $|g(z)|\leq \dfrac{1}{r}$ 对 $|z|\leq r$ 成立，令 $r\to 1$ 得到 $|g(z)|\leq 1$，即 $|f'(0)|\leq 1$ 且 $|f(z)|\leq |z|$. 如果存在 $z\neq 0$ 使得 $|f(z)|=|z|$ 或者 $|f'(0)|=1$，那么 $|g|$ 在 $D$ 内部取到最大值，因此最大模定理表明 $g=c$ 为常数，并且满足 $|c|=1$，这就完成了证明。

对 $|a|<1$，我们定义 Mobius 变换

$$
\begin{gather}
\varphi_{a}(z)=\dfrac{z-a}{1-\overline{a}z}
\end{gather}
$$

注意到，$\varphi_{a}$ 在 $|z|<|a|^{-1}$ 处解析，因此它在一个包含 $\overline{D}$ 的开圆盘上解析。此外，我们可以验证

$$
\begin{gather}
\varphi_{a}(\varphi_{-a}(z))=z=\varphi_{-a}(\varphi_{a}(z))
\end{gather}
$$

对 $|z|<1$ 成立，因此 $\varphi_{a}$ 是 $D$ 上的双射。

令 $\theta \in \mathbb{R}$，则我们还有

$$
\begin{align}
|\varphi_{a}(e^{i\theta})| &= \left\lvert  \dfrac{e^{i\theta}-a}{1-\overline{a}e^{i\theta}}  \right\rvert  \\
&= \left\lvert  \dfrac{e^{i\theta}-a}{\overline{e^{i\theta}}-\overline{a}}  \right\rvert  \\
&= 1
\end{align}
$$

这就是说，$\varphi_{a}[\partial D]=\partial D$.

这些关于 $\varphi_{a}$ 的事实，以及其他相关的结论，都总结在以下的定理中：

**定理 5.2.2**

如果 $|a|<1$，则 $\varphi_{a}$ 是 $D$ 上的双射，它的反函数是 $\varphi_{-a}$. 此外，$\varphi_{a}$ 将 $\partial D$ 满射到 $\partial D$，并且 $\varphi_{a}(a)=0$，$\varphi_{a}'(0)=1-|a|^{2}$，$\varphi_{a}'(a)=(1-|a|^{2})^{-1}$.

现在我们来看 $\varphi_{a}$ 如何被应用于 Schwarz 引理中。假设 $f$ 在 $D$ 上解析，满足 $|f(z)|\leq 1$，并设 $|a|<1$，$f(a)=\alpha$，于是 $|\alpha|<1$ 否则 $f$ 是常值函数。在所有满足这些条件的 $f$ 中，$|f'(a)|$ 的最大值是多少？为了解决这一问题，我们令 $g=\varphi_{\alpha}\circ f\circ\varphi_{-a}$，则 $g$ 将 $D$ 映射到 $D$，且满足

$$
\begin{gather}
g(0)=\varphi_{\alpha}(f(a))=\varphi_{\alpha}(\alpha)=0
\end{gather}
$$

于是 Schwarz 引理给出 $|g'(0)|\leq 1$. 另一方面，通过显式求导，我们得到

$$
\begin{align}
g'(0)=\dfrac{1-|a|^{2}}{1-|\alpha|^{2}} f'(a)
\end{align}
$$

于是

$$
\begin{gather}
|f'(a)|\leq \dfrac{1-|\alpha|^{2}}{1-|a|^{2}}
\end{gather}
$$

等式成立当且仅当 $|g'(0)|=1$，或者，根据 Schwarz 引理，存在 $|c|=1$ 使得

$$
\begin{gather}
f(z)=\varphi_{-\alpha}(c\varphi_{a}(z))
\end{gather}
$$

对 $|z|<1$ 成立。

现在我们可以证明 Schwarz 引理的一个主要推论。注意到，当 $|c|=1$ 且 $|a|<1$ 时，$f=c\varphi_{a}$ 定义了一个 $D$ 上的双射。以下的定理表明，它的逆命题也成立。

**定理 5.2.3**

设 $f\colon D\to D$ 是一个解析双射，并设 $f(a)=0$. 则存在单位复数 $|c|=1$ 使得 $f=c\varphi_{a}$.

**证明**

由于 $f$ 是双射，故有反函数 $g\colon D\to D$. 则对 $f,g$ 应用导数不等式得到

$$
\begin{align}
|f'(a)|\leq \dfrac{1}{1-|a|^{2}} , \quad |g'(0)|\leq 1-|a|^{2}
\end{align}
$$

但由于 $1=g'(0)f'(a)$，故 $|f'(a)|=(1-|a|^{2})^{-1}$，从而有 $f=c\varphi_{a}$ 成立。

# Section 3: Hadamard 三圆定理

在本节中我们研究实数上的凸函数，并指出它们与复解析函数的关联。

**定义 5.3.1** 凸函数（convex function）

函数 $f\colon[a,b]\to \mathbb{R}$ 是一个**凸函数**，如果对任意 $x_{1},x_{2} \in[a,b]$ 和 $0\leq t\leq 1$ 有

$$
\begin{gather}
f((1-t)x_{1}+tx_{2})\leq (1-t)f(x_{1})+tf(x_{2})
\end{gather}
$$

换句话说，一个函数是凸的，如果连接 $(x_{1},f(x_{1}))$ 和 $(x_{2},f(x_{2}))$ 的线段完全位于从 $x_{1}$ 到 $x_{2}$ 的函数图像之上。这也就是说，函数图像以上的部分是一个**凸集**。

**定理 5.3.2**

函数 $f\colon[a,b]\to \mathbb{R}$ 是凸函数当且仅当集合

$$
\begin{gather}
A=\{ (x,y) \mid a\leq x\leq b, y\geq f(x) \}
\end{gather}
$$

是一个凸集。

利用数学归纳法，我们也可以得到以下结果：

**定理 5.3.3**

函数 $f\colon [a,b]\to \mathbb{R}$ 是凸函数当且仅当对任意 $x_{1},\dots,x_{n}\in[a,b]$ 和 $t_{1},\dots,t_{n}\geq 0$ 满足 $\sum_{k=1}^{n}t_{k}=1$，有

$$
\begin{gather}
f\left( \sum_{k=1}^{n} t_{k}x_{k} \right)\leq \sum_{k=1}^{n} t_{k} f(x_{k})
\end{gather}
$$

凸函数和凸集的优点是什么？我们在复积分中已经看到了凸集的作用：凸集（更一般地，星状集）是单连通的。此外，圆盘是凸集这一事实也发挥了极大的作用。而对于凸函数，它们通常被用于构造不等式。特别地，根据凸函数的定义，对任意 $x \in[a,b]$ 有 $f(x)\leq \max \{ f(a),f(b) \}$. 此外，我们还有以下的充要条件：

**定理 5.3.4**

函数 $f\colon[a,b]\to \mathbb{R}$ 是凸函数当且仅当对 $a\leq x<y<z\leq b$ 有

$$
\begin{gather}
\dfrac{f(y)-f(x)}{y-x}\leq \dfrac{f(z)-f(y)}{z-y}
\end{gather}
$$

由该定理可知，一个可微函数 $f$ 是凸的当且仅当 $f'$ 单调递增。进一步，如果 $f$ 二阶可微，那么 $f$ 是凸的当且仅当 $f''(x)\geq 0$.

在实际应用中，我们遇到的函数将不仅是凸的，而且还是**对数凸的**，这就是说，函数 $\log f(x)$ 是凸函数。

**定理 5.3.5**

如果 $f\colon[a,b]\to \mathbb{R}_{>0}$ 是对数凸函数，那么 $f$ 是凸函数。

**证明**

根据定义，对 $x,y \in[a,b],0\leq t\leq 1$ 我们有

$$
\begin{gather}
\log f(tx+(1-t)y)\leq t\log f(x)+(1-t) \log f(y)
\end{gather}
$$

两边取指数得

$$
\begin{gather}
f(tx+(1-t)y)\leq \exp(t \log f(x)+(1-t)\log f(y))
\end{gather}
$$

由于指数函数具有正二阶导数，因此它是凸的，从而

$$
\begin{gather}
\exp(t\log f(x)+(1-t)\log f(y))\leq t f(x)+(1-t) f(y)
\end{gather}
$$

这就完成了证明。

**定理 5.3.6**

令 $a<b$，$G$ 为竖直条带 $\{ x+iy \mid a<x<b \}$，假设 $f$ 在 $\overline{G}$ 上解析，如果我们定义 $M\colon [a,b]\to \mathbb{R}$ 为

$$
\begin{gather}
M(x)=\sup_{y} |f(x+iy)|
\end{gather}
$$

并且设 $|f(z)|<B$ 对任意 $z \in G$ 成立，那么 $M(x)$ 是对数凸函数。

在证明这一定理之前，我们需要注意到，说 $M(x)$ 对数凸，根据定理 5.3.4，意味着对于 $a\leq x<u<y\leq b$ 有

$$
\begin{align}
(y-x) \log M(u)\leq (y-u)\log M(x)+(u-x)\log M(y)
\end{align}
$$

两边取指数即得

$$
\begin{align}
M(u)^{y-x}\leq M(x)^{y-u}M(y)^{u-x}
\end{align}
$$

此外，根据凸函数的性质，由定理 5.3.5 得

$$
\begin{gather}
M(x)\leq \max \{ M(a),M(b) \}
\end{gather}
$$

对任意 $a\leq x\leq b$ 成立。这给出了以下定理：

**定理 5.3.7**

令 $f,G$ 如定理 5.3.6 所示，如果 $f$ 不是常值函数，那么

$$
\begin{gather}
|f(z)|< \sup \{ |f(w)| \mid w \in \partial G \}
\end{gather}
$$

对 $z \in G$ 成立。

为证明定理 5.3.6，我们还需要以下的引理。

**引理 5.3.8**

令 $f,G$ 如定理 5.3.6 所示，并设 $|f(z)|\leq 1$ 对 $z \in \partial G$ 成立，那么 $|f(z)|\leq 1$ 对 $z \in G$ 成立。

**证明**

任取 $\varepsilon>0$，定义 $g_{\varepsilon}(z)=(1+\varepsilon(z-a))^{-1}$，$z \in \overline{G}$，则对 $x+iy \in \overline{G}$ 有

$$
\begin{align}
|g_{\varepsilon}(z)| &\leq |\mathrm{Re}(1+\varepsilon(z-a))|^{-1} \\
&= |1+\varepsilon(x-a)|^{-1} \\
&\leq 1
\end{align}
$$

因此对于 $z \in \partial G$ 有 $|f(z)g_{\varepsilon}(z)|\leq 1$. 此外，由于 $|f|$ 有上界 $B$，故

$$
\begin{align}
|f(z)g_{\varepsilon}(z)| &\leq B|1+\varepsilon(z-a)|^{-1} \\
&\leq \dfrac{B}{\varepsilon|\mathrm{Im}\,z|}
\end{align}
$$

因此，如果 $R=\{ x+iy \mid a\leq x\leq b, |y|\leq B /\varepsilon \}$，那么 $|f(z)g_{\varepsilon}(z)|\leq 1$ 对 $z \in \partial R$ 成立。于是，最大模定理表明 $|f(z)g_{\varepsilon}(z)|\leq 1$ 对 $z \in R$ 成立。而当 $|\mathrm{Im}\,z|>B /\varepsilon$ 时，同样有 $|f(z)g_{\varepsilon}(z)|\leq 1$ 成立，因此对任意 $z \in G$ 我们有

$$
\begin{gather}
|f(z)|\leq |1+\varepsilon(z-a)|
\end{gather}
$$

令 $\varepsilon\to 0+$ 即证。

**证明**（5.3.6）

我们只需证明

$$
\begin{gather}
M(u)^{b-a}\leq M(a)^{b-u}M(b)^{u-a}
\end{gather}
$$

对 $a<u<b$ 成立。为此，注意到对于 $A> 0$，$A^{z}=\exp(z\log A)$ 是一个无零点的整函数，因此定义为

$$
\begin{gather}
g(z)=M(a)^{(b-z) /(b-a)}M(b)^{(z-a) /(b-a)}
\end{gather}
$$

的函数 $g$ 是整函数，永不消失，并且对于 $z=x+iy$ 有

$$
\begin{align}
|g(z)|=M(a)^{(b-x) /(b-a)}M(b)^{(x-a) /(b-a)}
\end{align}
$$

这里我们假设了 $M(a)\neq 0,M(b)\neq 0$，然而，如果这两者之一为零，那么 $f$ 恒等于零。于是，上式右侧的表达式关于 $x \in[a,b]$ 连续，且永不消失，从而 $|g|^{-1}$ 在 $\overline{G}$ 中有界。此外，$|g(a+iy)|=M(a)$，$|g(b+iy)|=M(b)$，故 $|f(z) /g(z)|\leq 1$ 对 $z \in \partial G$ 成立。因此，$f /g$ 满足引理 5.3.8 条件，从而

$$
\begin{gather}
|f(z)|\leq|g(z)|
\end{gather}
$$

对 $z \in G$ 成立。令 $z=u+iy$ 并对 $y$ 取上确界即得

$$
\begin{gather}
M(u)\leq M(a)^{(b-u)/(b-a)} M(b)^{(u-a)/(b-a)}
\end{gather}
$$

这就完成了证明。

下一个定理是定理 5.3.6 在圆环上的类比，它有一个贴切的名字：三圆（Three Circles）定理。考虑 $A=\mathrm{ann}(0,R_{1},R_{2})$，其中 $0<R_{1}<R_{2}$，如果 $G=\{ x+iy \mid \log R_{1}<x<\log R_{2} \}$，那么指数函数 $\exp$ 将 $G$ 满射到 $A$，并将 $\partial G$ 满射到 $\partial A$. 利用这个事实，我们就可以给出三圆定理的证明。

**定理 5.3.9** Hadamard 三圆定理

设 $0<R_{1}<R_{2}<\infty$，$f$ 在 $\mathrm{ann}(0,R_{1},R_{2})$ 上解析。对于 $R_{1}<r<R_{2}$，定义 $M(r)=\max \{ |f(re^{i\theta})| \mid 0\leq\theta\leq 2\pi \}$，则对 $R_{1}<r_{1}\leq r\leq r_{2}<R_{2}$ 有

$$
\begin{align}
\log M(r)\leq \dfrac{\log r_{2}-\log r}{\log r_{2}-\log r_{1}}\log M(r_{1})+\dfrac{\log r-\log r_{1}}{\log r_{2}-\log r_{1}}\log M(r_{2})
\end{align}
$$

换句话说，$\log M(r)$ 是 $\log r$ 的凸函数。

**证明**

令 $G=\{ x+iy \mid \log r_{1}<x<\log r_{2} \}$，则 $g\colon G\to \mathbb{C}$ 定义为 $g=f\circ \exp$ 在 $\overline{G}$ 上解析。又由于 $f$ 在紧致集 $\overline{\mathrm{ann}(0,r_{1},r_{2})}$ 上连续，故有界，从而 $g$ 在 $\overline{G}$ 上有界。此外，我们有

$$
\begin{gather}
M(r)=\sup_{y} |g(\log r+iy)|
\end{gather}
$$

因此对 $g$ 应用定理 5.3.6，即证 $M(r)$ 在 $[r_{1},r_{2}]$ 上是 $\log r$ 的对数凸函数。

对应于三圆定理，我们也通常称定理 5.3.6 为 **Hadamard 三直线定理**。

# Section 4: Phragmen-Lindelof 定理

在最大模定理 II 和 III 中我们看到，要得到 $f$ 有界的结论，我们必须假设 $f$ 在边界上有界（无论是有界边界还是无穷远边界）。而 Phragmen 和 Lindelof 证明了，在一定的条件下，我们可以将这个有界条件放宽，正如以下的扩展 Liouville 定理所示：如果整函数 $f$ 满足 $|f(z)|\leq 1+|z|^{1/2}$，那么 $f$ 是常值函数（将 $f$ 展开为幂级数并在圆 $|z|=R$ 上对系数做估计）。Phragmen-Lindelof 定理为函数 $f$ 在 $z$ 趋于边界点时的增长速率做了类似的限制，不过，其结论与最大模定理相同，即 $f$ 的有界性。

**定理 5.4.1** Phragmen-Lindelof 定理

设 $G$ 是单连通域，$f$ 在 $G$ 上解析。假设解析函数 $\varphi\colon G\to \mathbb{C}$ 恒不为零且有界，如果 $M$ 是一个常数且 $\partial_{\infty}G=A\cup B$ 满足

1. 对任意 $a \in A$，$\limsup_{ z \to a }|f(z)|\leq M$
2. 对任意 $b\in B$ 和 $\eta>0$，$\limsup_{ z \to b }|f(z)||\varphi(z)|^{\eta}\leq M$

那么 $|f(z)|\leq M$ 对 $z \in G$ 成立。

**证明**

设 $|\varphi(z)|\leq\kappa$ 对 $z \in G$ 成立。此外，由于 $G$ 单连通，故在 $G$ 上可以定义 $\log\varphi(z)$ 的一个分支，因此我们可以定义 $\varphi(z)^{\eta}=\exp(\eta \log\varphi(z))$. 令 $F(z)=f(z)\varphi(z)^{\eta}\kappa^{-\eta}$，则 $F$ 在 $G$ 上解析，并且 $|F(z)|\leq|f(z)|$. 于是我们有 $\limsup_{ z \to a }|F(z)|\leq \max \{ M,\kappa^{-\eta}M \}$ 对任意 $a \in \partial_{\infty}G$ 成立，从而最大模定理给出

$$
\begin{gather}
|f(z)|\leq |\varphi(z)|^{-\eta} \max \{ M,\kappa^{-\eta}M \}
\end{gather}
$$

令 $\eta\to 0+$ 即证 $|f(z)|\leq M$.

**定理 5.4.2**

设 $a\geq 1 /2$，$G=\{ z \mid |\mathrm{arg}\,z|<\pi / 2a \}$，假设 $f$ 在 $G$ 上解析，且存在 $M$ 使得对任意 $w \in \partial G$ 有 $\limsup_{ z \to w }|f(z)|\leq M$，则如果有 $P>0$ 和 $b<a$ 使得

$$
\begin{gather}
|f(z)|\leq P \exp(|z|^{b})
\end{gather}
$$

对充分大的 $|z|$ 成立，则 $|f(z)|\leq M$ 对 $z \in G$ 成立。

**证明**

令 $b<c<a$，定义 $\varphi(z)=\exp(-z^{c})$. 如果 $z=re^{i\theta}$，$|\theta|<\pi /2a$，则我们有

$$
\begin{gather}
|\varphi(z)|=\exp(-r^{c}\cos c\theta)
\end{gather}
$$

由于 $c<a$，故 $|c\theta|<\pi c /2a<\pi /2$，从而 $\cos c\theta\geq \rho>0$，这表明 $\varphi$ 在 $G$ 上有界。此外，对于 $\eta>0$ 和充分大的 $r$，有

$$
\begin{align}
|f(z)||\varphi(z)|^{\eta}&\leq P\exp(r^{b}-\eta r^{c}\cos c\theta) \\
&\leq P\exp(r^{b}-\eta r^{c}\rho)
\end{align}
$$

但在 $r\to \infty$ 时有 $r^{b-c}\to 0$，因此 $r^{b}-\eta r^{c}\rho=r^{c}(r^{b-c}-\eta \rho)\to -\infty$，从而

$$
\begin{gather}
\limsup_{ r \to \infty } |f(z)||\varphi(z)|^{\eta}=0
\end{gather}
$$

由 Phragmen-Lindelof 定理即证。

注意，以上定理中扇形 $G$ 的角度大小是唯一相关的参数，与 $G$ 的朝向无关。因此，如果 $G$ 是任意内角为 $\pi /a$ 的扇形，以上定理仍然成立。

**定理 5.4.3**

设 $a\geq 1 /2$，$G=\{ z \mid |\mathrm{arg}\,z|<\pi / 2a \}$，假设 $f$ 在 $G$ 上解析，且存在 $M$ 使得对任意 $w \in \partial G$ 有 $\limsup_{ z \to w }|f(z)|\leq M$. 如果对任意 $\delta>0$，存在 $P>0$ 使得

$$
\begin{gather}
|f(z)|\leq P\exp(\delta |z|^{a})
\end{gather}
$$

对充分大的 $|z|$ 成立，则 $|f(z)|\leq M$ 对 $z \in G$ 成立。

**证明**

定义 $F(z)=f(z)\exp(-\varepsilon z^{a})$，其中 $\varepsilon>0$ 是任意的。如果 $x>0$ 且 $0<\delta<\varepsilon$，那么存在 $P>0$ 使得当 $x$ 充分大时有

$$
\begin{gather}
|F(x)|\leq P\exp((\delta-\varepsilon)x^{a})
\end{gather}
$$

于是当 $x \to \infty$ 时有 $|F(x)| \to 0$，因此 $M_{1}=\sup_{x>0}|F(x)|<\infty$. 定义 $M_{2}=\max \{ M,M_{1} \}$ 以及

$$
\begin{gather}
H_{+}=\left\{  z \in G \mid 0<\mathrm{arg}\,z< \dfrac{\pi}{2a}  \right\} \\
H_{-}=\left\{  z \in G \mid -\dfrac{\pi}{2a}<\mathrm{arg}\,z<0  \right\}
\end{gather}
$$

则 $\limsup_{ z \to w }|f(z)|\leq M_{2}$ 对任意 $z \in \partial H_{+}$ 和 $z \in \partial H_{-}$. 于是，定理 5.4.2 给出 $|F(z)|\leq M_{2}$ 对 $z \in H_{+}$ 和 $z \in H_{-}$ 成立，因此 $|F(z)|\leq M_{2}$ 对 $z \in G$ 成立。

我们断言 $M_{2}=M$. 事实上，如果 $M_{2}=M_{1}>M$，那么 $|F|$ 在 $G$ 的内部取到最大值，因为 $x\to \infty$ 时 $|F(x)| \to 0$ 且 $\limsup_{ x \to 0 }|F(x)|\leq M<M_{1}$. 因此，由最大模定理知 $F$ 是常值函数，与 $\limsup_{ x \to 0 }|F(x)|\leq M$ 矛盾。因此 $M_{1}=M$，进而有 $M_{2}=M$ 且 $|F(z)|\leq M$ 对 $z \in G$ 成立，即

$$
\begin{gather}
|f(z)|\leq M\exp(\varepsilon \mathrm{Re}\, z^{a})
\end{gather}
$$

令 $\varepsilon\to 0+$ 即证。

令 $G=\{ z \mid z\neq 0,|\mathrm{arg}\,z|<\pi /2a \}$，定义 $f(z)=\exp(z^{a})$，则

$$
\begin{gather}
|f(z)|=\exp(|z|^{a} \cos a\theta), \quad \theta=\mathrm{arg}\,z
\end{gather}
$$

因此对于 $z \in \partial G$ 有 $|f(z)|=1$，但 $f$ 在 $G$ 上显然是无界的。这表明定理 5.4.3 中的增长限制是相当精细的，并且无法再改进了。