本章我们来定义复函数 $f$ 沿着平面上的路径 $\gamma$ 的积分

$$
\begin{gather}
\int_{\gamma} f(z)\mathrm{d} z
\end{gather}
$$

它构成了复分析的一个基础组成部分，并且这里所阐述的定理是数学的重要支柱之一，在其他领域也有着广泛的应用。

# Section 1: Riemann-Stieltjes 积分

我们从 Riemann-Stieltjes 积分的定义开始，以此作为定义函数在 $\mathbb{C}$ 路径上的积分的基础。

**定义 2.1.1** 有界变差（bounded variation）

一个函数 $\gamma\colon[a,b]\to \mathbb{C}$ 是**有界变差的**，如果存在 $M>0$ 使得对任意 $[a,b]$ 的划分 $P=\{ a=t_{0}<t_{1}<\dots<t_{n}=b \}$ 有

$$
\begin{gather}
v(\gamma,P)=\sum_{k=1}^{n} |\gamma(t_{k})-\gamma(t_{k-1})|\leq M
\end{gather}
$$

定义 $\gamma$ 的**总变差**为

$$
\begin{gather}
V(\gamma)=\sup \{ v(\gamma,P) \mid P \text{是} [a,b] \text{的划分} \}
\end{gather}
$$

显然，如果 $\gamma$ 是有界变差函数，那么 $V(\gamma)\leq M<\infty$. 并且容易证明，$\gamma$ 是有界变差的当且仅当 $\mathrm{Re}\,\gamma$ 和 $\mathrm{Im}\,\gamma$ 都是有界变差的。此外，如果 $\gamma$ 是实函数并且是单调递增的，那么 $V(\gamma )=\gamma(b)-\gamma(a)$，从而是有界变差的。

**定理 2.1.2**

设 $\gamma,\sigma\colon[a,b]\to \mathbb{C}$ 是有界变差函数，则：

1. 如果 $P,Q$ 是 $[a,b]$ 的划分，$P\subset Q$，那么 $v(\gamma,P)\leq v(\gamma,Q)$
2. 设 $\alpha,\beta \in \mathbb{C}$，则 $\alpha\gamma+\beta\sigma$ 是有界变差的，并且 $$
V(\alpha\gamma+\beta\sigma)\leq|\alpha|V(\gamma)+|\beta|V(\sigma)
$$

**证明**

(1). 设 $P=\{ a=t_{0}<t_{1}<\dots<t_{n}=b \}$，我们只需证明 $Q=P\cup \{ t' \}$ 的情况。假设 $t_{k-1}<t'<t_{k}$，则根据三角不等式

$$
\begin{gather}
|\gamma(t_{k})-\gamma(t_{k-1})|\leq |\gamma(t_{k})-\gamma(t')|+|\gamma(t')-\gamma(t_{k-1})|
\end{gather}
$$

即得 $v(\gamma,P)\leq v(\gamma,Q)$.

(2). 取划分 $P$，同样由三角不等式得

$$
\begin{align}
&|(\alpha\gamma+\beta\sigma)(t_{k})-(\alpha\gamma+\beta\sigma)(t_{k-1})| \\
&\leq |\alpha||\gamma(t_{k})-\gamma(t_{k-1})|+|\beta||\sigma(t_{k})-\sigma(t_{k-1})|
\end{align}
$$

两边求和得 $v(\alpha\gamma+\beta\sigma,P)\leq|\alpha|v(\gamma,P)+|\beta|v(\sigma,P)\leq|\alpha|V(\gamma)+|\beta|V(\sigma)$，再取上确界即证。

下一个定理给出了大量有界变差函数的例子，这些函数是我们主要研究的对象。

**定理 2.1.3**

如果 $\gamma\colon[a,b]\to \mathbb{C}$ 是分段光滑的，则 $\gamma$ 是有界变差的，并且

$$
\begin{gather}
V(\gamma)=\int_{a}^{b} |\gamma'(t)|\mathrm{d} t
\end{gather}
$$

**证明**

我们只需证明 $\gamma$ 光滑的情况，从而，对于分段光滑路径，我们可以将其分成有限个区间上的光滑路径，在每个区间上应用光滑的结论即证。

令 $P=\{ a=t_{0}<t_{1}<\dots<t_{n}=b \}$，则我们有

$$
\begin{align}
v(\gamma,P) &= \sum_{k=1}^{n} |\gamma(t_{k})-\gamma(t_{k-1})| \\
&= \sum_{k=1}^{n} \left\lvert  \int_{t_{k-1}}^{t_{k}} \gamma'(t)\mathrm{d} t  \right\rvert  \\
&\leq \sum_{k=1}^{n} \int_{t_{k-1}}^{t_{k}} |\gamma'(t)|\mathrm{d} t \\
&= \int_{a}^{b} |\gamma'(t)|\mathrm{d} t
\end{align}
$$

于是 $V(\gamma)\leq \int_{a}^{b}|\gamma'|$，从而 $\gamma$ 是有界变差的。

由于 $\gamma'$ 在紧致集 $[a,b]$ 上连续，故一致连续，于是对 $\varepsilon>0$，存在 $\delta_{1}>0$ 使得 $|s-t|<\delta_{1}$ 蕴含 $|\gamma(s)-\gamma(t)|<\varepsilon$. 另外，我们还可以取 $\delta_{2}>0$ 使得如果划分 $P=\{ a=t_{0}<\dots<t_{m}=b \}$ 满足 $\lVert P \rVert=\max_{k}(t_{k}-t_{k-1})<\delta_{2}$，那么

$$
\begin{gather}
\left\lvert  \int_{a}^{b} |\gamma'(t)|\mathrm{d} t-\sum_{k=1}^{m} |\gamma'(\tau_{k})|(t_{k}-t_{k-1})  \right\rvert <\varepsilon
\end{gather}
$$

对任意 $\tau_{k}\in[t_{k-1},t_{k}]$ 成立。因此

$$
\begin{align}
\int_{a}^{b} |\gamma'(t)|\mathrm{d} t &< \varepsilon+ \sum_{k=1}^{m} |\gamma'(\tau_{k})|(t_{k}-t_{k-1}) \\
&=\varepsilon +\sum_{k=1}^{m} \left\lvert  \int_{t_{k-1}}^{t_{k}} \gamma'(\tau_{k}) \mathrm{d} t  \right\rvert  \\
&\leq \varepsilon+\sum_{k=1}^{m} \left\lvert  \int_{t_{k-1}}^{t_{k}} (\gamma'(\tau_{k})-\gamma'(t)) \mathrm{d} t  \right\rvert +\sum_{k=1}^{m} \left\lvert  \int_{t_{k-1}}^{t_{k}} \gamma'(t)\mathrm{d} t  \right\rvert 
\end{align}
$$

当 $\lVert P \rVert<\delta=\min(\delta_{1},\delta_{2})$ 时，有 $|\gamma'(\tau_{k})-\gamma'(t)|<\varepsilon$ 对 $t\in[t_{k-1},t_{k}]$ 成立，于是

$$
\begin{align}
\int_{a}^{b}|\gamma'(t)|\mathrm{d} t &\leq \varepsilon+\varepsilon(b-a)+\sum_{k=1}^{m} |\gamma(t_{k})-\gamma(t_{k-1})| \\
&\leq \varepsilon(1+b-a)+V(\gamma)
\end{align}
$$

从而有 $\int_{a}^{b}|\gamma'|\leq V(\gamma)$，这就完成了证明。

下面我们给出本节的主要存在性定理。

**定理 2.1.4**

设 $\gamma\colon[a,b]\to \mathbb{C}$ 是有界变差函数，$f\colon[a,b]\to \mathbb{C}$ 是连续函数，则存在唯一的复数 $I$ 使得对任意 $\varepsilon>0$，存在 $\delta>0$，使得当划分 $P=\{ t_{0}<\dots<t_{n} \}$ 满足 $\lVert P \rVert=\max_{k}(t_{k}-t_{k-1})<\delta$ 时有

$$
\begin{gather}
\left\lvert  I-\sum_{k=1}^{n} f(\tau_{k})(\gamma(t_{k})-\gamma(t_{k-1}))  \right\rvert <\varepsilon
\end{gather}
$$

对任意选取的 $\tau_{k}\in[t_{k-1},t_{k}]$ 成立。

复数 $I$ 称为 $f$ 在 $[a,b]$ 上关于 $\gamma$ 的 **Riemann-Stieltjes 积分**，记作

$$
\begin{gather}
I=\int_{a}^{b} f\mathrm{d} \gamma=\int_{a}^{b}f(t)\mathrm{d} \gamma(t)
\end{gather}
$$

**证明**

$f$ 在 $[a,b]$ 上一致连续，因此我们可以取 $\delta_{1}>\delta_{2}>\cdots$ 使得 $|s-t|<\delta_{m}$ 蕴含 $|f(s)-f(t)|< \dfrac{1}{m}$. 对每个 $m\geq 1$，令 $\mathcal{P}_{m}$ 表示所有满足 $\lVert P \rVert<\delta_{m}$ 的划分 $P$，于是 $\mathcal{P}_{1}\supset \mathcal{P}_{2}\supset\cdots$. 最后，定义 $F_{m}$ 为以下集合的闭包：

$$
\begin{gather}
\left\{  \sum_{k=1}^{n} f(\tau_{k})(\gamma(t_{k})-\gamma(t_{k-1})) \middle| P \in \mathcal{P}_{m}, \tau_{k}\in[t_{k-1},t_{k}]  \right\}
\end{gather}
$$

我们断言以下结论成立：

$$
\begin{gather}
\begin{cases}
F_{1}\supset F_{2}\supset\cdots \\
\mathrm{diam}\,F_{m}\leq \dfrac{2}{m}V(\gamma)
\end{cases}
\end{gather}
$$

于是，根据 Cantor 定理，存在唯一的 $I \in F_{m}$ 对任意 $m$ 成立。任取 $\varepsilon>0$，令 $m>(2 /\varepsilon)V(\gamma)$，则 $\mathrm{diam}\,F_{m}<\varepsilon$，从而 $F_{m}\subset B(I,\varepsilon)$，即证。

下面我们来验证以上断言。$F_{1}\supset F_{2}\supset\cdots$ 可由 $\mathcal{P}_{1}\supset \mathcal{P}_{2}\supset\cdots$ 直接得到。对于另一个断言，我们记 $S(P)$ 为具有形式 $\sum f(\tau_{k})(\gamma(t_{k})-\gamma(t_{k-1}))$ 的 Riemann 和，其中 $\tau_{k}\in[t_{k-1},t_{k}]$. 对于 $m\geq 1$ 和 $P \in \mathcal{P}_{m}$，我们来证明当 $P\subset Q$ 时有 $|S(P)-S(Q)|\leq \dfrac{1}{m}V(\gamma)$.

我们只需证明 $Q=P\cup \{ t' \}$ 的情况，此时设 $t_{p-1}<t'<t_{p}$，$\sigma \in[t_{p-1},t']$，$\sigma'\in[t',t_{p}]$，则我们有

$$
\begin{align}
S(Q)&=\sum_{k\neq p}f(\sigma_{k})(\gamma(t_{k})-\gamma(t_{k-1}))+f(\sigma)(\gamma(t')-\gamma(t_{p-1})) \\
&+f(\sigma')(\gamma(t_{p})-\gamma(t'))
\end{align}
$$

于是，利用 $|s-t|<\delta_{m}$ 蕴含 $|f(s)-f(t)|<\dfrac{1}{m}$ 的结论，得到

$$
\begin{align}
|S(P)-S(Q)| &\leq \left\lvert  \sum_{k\neq p} (f(\tau_{k})-f(\sigma_{k}))(\gamma(t_{k})-\gamma(t_{k-1}))  \right\rvert  \\
&+\lvert f(\tau_{p})-f(\sigma) \rvert \lvert \gamma(t')-\gamma(t_{p-1}) \rvert  \\
&+\lvert f(\tau_{p})-f(\sigma') \rvert \lvert \gamma(t_{p})-\gamma(t') \rvert  \\
&\leq \dfrac{1}{m} \sum_{k\neq p}|\gamma(t_{k})-\gamma(t_{k-1})|+ \dfrac{1}{m} \lvert \gamma(t')-\gamma(t_{p-1}) \rvert  \\
&+ \dfrac{1}{m} \lvert \gamma(t_{p})-\gamma(t') \rvert \\
&\leq \dfrac{1}{m}V(\gamma)
\end{align}
$$

进一步，令 $P,R$ 为 $\mathcal{P}_{m}$ 中的两个划分，取 $P,R$ 的公共加细 $Q$，则根据上面的结论，我们有

$$
\begin{gather}
|S(P)-S(R)|\leq|S(P)-S(Q)|+|S(Q)-S(R)|\leq \dfrac{2}{m}V(\gamma)
\end{gather}
$$

取上确界即得 $\mathrm{diam}\,F_{m}\leq \dfrac{2}{m}V(\gamma)$，这就完成了证明。

下面几个结论可以通过常规的 $\varepsilon-\delta$ 论证得到，其证明我们略去。

**定理 2.1.5**

设 $\gamma,\sigma\colon[a,b]\to \mathbb{C}$ 是有界变差函数，$f,g\colon[a,b]\to \mathbb{C}$ 是连续函数，则对任意 $\alpha,\beta \in \mathbb{C}$ 有

1. $\displaystyle \int_{a}^{b}(\alpha f+\beta g)\mathrm{d}\gamma=\alpha \int_{a}^{b}f\mathrm{d}\gamma+\beta \int_{a}^{b}g\mathrm{d}\gamma$
2. $\displaystyle \int_{a}^{b}f\mathrm{d}(\alpha\gamma+\beta\sigma)=\alpha \int_{a}^{b}f\mathrm{d}\gamma+\beta \int_{a}^{b}f\mathrm{d}\sigma$

**定理 2.1.6**

设 $\gamma\colon[a,b]\to \mathbb{C}$ 是有界变差函数，$f\colon[a,b]\to \mathbb{C}$ 是连续函数，那么如果 $a=t_{0}<t_{1}<\dots<t_{n}=b$，则有

$$
\begin{gather}
\int_{a}^{b}f\mathrm{d} \gamma=\sum_{k=1}^{n} \int_{t_{k-1}}^{t_{k}} f\mathrm{d} \gamma
\end{gather}
$$

前面我们提到，我们主要研究的是分段光滑路径。下面的定理指出，在这种情况下，我们可以将 Riemann-Stieltjes 积分 $\int f\mathrm{d}\gamma$ 转化为一般的 Riemann 积分。

**定理 2.1.7**

如果 $\gamma\colon[a,b]\to \mathbb{C}$ 是分段光滑路径，$f\colon[a,b]\to \mathbb{C}$ 是连续函数，则

$$
\begin{gather}
\int_{a}^{b} f\mathrm{d} \gamma=\int_{a}^{b} f(t)\gamma'(t)\mathrm{d} t
\end{gather}
$$

**证明**

我们只需考虑 $\gamma$ 光滑的情况。此外，通过分别考虑 $\gamma$ 的实部和虚部，我们可以假设 $\gamma$ 是一个实函数。令 $\varepsilon>0$，则存在 $\delta>0$ 使得当 $\lVert P \rVert<\delta$ 时有

$$
\begin{gather}
\left\lvert  \int_{a}^{b}f\mathrm{d} \gamma-\sum_{k=1}^{n} f(\tau_{k})(\gamma(t_{k})-\gamma(t_{k-1}))  \right\rvert <\dfrac{\varepsilon}{2}
\end{gather}
$$

且

$$
\begin{gather}
\left\lvert  \int_{a}^{b} f(t)\gamma'(t)\mathrm{d} t-\sum_{k=1}^{n} f(\tau_{k})\gamma'(\tau_{k})(t_{k}-t_{k-1})  \right\rvert <\dfrac{\varepsilon}{2}
\end{gather}
$$

对任意 $\tau_{k}\in[t_{k-1},t_{k}]$ 成立。应用中值定理我们可知，存在 $\tau_{k}\in(t_{k-1},t_{k})$ 使得 $\gamma'(\tau_{k})(t_{k}-t_{k-1})=\gamma(t_{k})-\gamma(t_{k-1})$，取这个 $\tau_{k}$，我们就有

$$
\begin{gather}
\sum_{k=1}^{n} f(\tau_{k})(\gamma(t_{k})-\gamma(t_{k-1}))=\sum_{k=1}^{n} f(\tau_{k})\gamma'(\tau_{k})(t_{k}-t_{k-1})
\end{gather}
$$

再应用三角不等式即得 $\left\lvert  \int_{a}^{b}f\mathrm{d}\gamma-\int_{a}^{b}f\gamma'  \right\rvert<\varepsilon$，这就完成了证明。

做完了准备工作，下面我们可以正式定义复积分了。

**定义 2.1.8** 轨迹（trace），可求长的（rectifiable）

设 $\gamma\colon[a,b]\to \mathbb{C}$ 是一条路径，我们称 $\gamma[a,b]=\{ \gamma(t) \mid t \in[a,b] \}$ 为 $\gamma$ 的**轨迹**，记作 $\{ \gamma \}$. 如果 $\gamma$ 是有界变差的，则称 $\gamma$ 是一条**可求长的路径**。

注意，$\gamma$ 的轨迹总是一个紧致集。此外，如果 $P$ 是 $[a,b]$ 的一个划分，则 $v(\gamma,P)$ 正是连接 $\{ \gamma \}$ 上点的折线的长度。因此，说 $\gamma$ 是可求长的就等价于说 $\gamma$ 具有有限长度，其长度为 $V(\gamma)$. 特别地，如果 $\gamma$ 是分段光滑的，那么 $\gamma$ 是可求长的，并且其长度为 $\int_{a}^{b}|\gamma'|$.

**定义 2.1.9**

设 $\gamma\colon[a,b]\to \mathbb{C}$ 是可求长路径，$f$ 在 $\{ \gamma \}$ 上连续，则 $f$ 沿着路径 $\gamma$ 的积分定义为

$$
\begin{gather}
\int_{\gamma} f=\int_{\gamma} f(z)\mathrm{d} z=\int_{a}^{b} f(\gamma(t)) \mathrm{d} \gamma(t)
\end{gather}
$$

下面我们给出几个例子。设 $\gamma\colon[0,2\pi]\to \mathbb{C}$ 为 $\gamma(t)=e^{it}$，定义 $f(z)=\dfrac{1}{z}$，则我们有

$$
\begin{gather}
\int_{\gamma}f=\int_{0}^{2\pi}e^{-it}(ie^{it})\mathrm{d}t=2\pi i
\end{gather}
$$

再设 $m\geq 0$ 为整数，$f(z)=z^{m}$，则在相同的 $\gamma$ 下有

$$
\begin{gather}
\int_{\gamma}f=\int_{0}^{2\pi}ie^{i(m+1)t}\mathrm{d}t=\left.\dfrac{e^{i(m+1)t}}{m+1}\right|_{0}^{2\pi}=0
\end{gather}
$$

设 $\gamma\colon[a,b]\to \mathbb{C}$ 是一个可求长路径，$\varphi\colon[c,d]\to[a,b]$ 是一个连续单调递增函数，满足 $\varphi(c)=a,\varphi(d)=b$，则路径 $\gamma \circ\varphi\colon [c,d]\to \mathbb{C}$ 与 $\gamma$ 拥有相同的轨迹。此外，$\gamma \circ\varphi$ 是可求长的，因为如果 $c=s_{0}<\dots<s_{n}=d$ 是 $[c,d]$ 的划分，那么 $a=\varphi(s_{0})\leq\dots\leq\varphi(s_{n})=b$ 就是 $[a,b]$ 的划分，因此

$$
\begin{gather}
\sum_{k=1}^{n} |\gamma(\varphi(s_{k}))-\gamma(\varphi(s_{k-1}))|\leq V(\gamma)<\infty
\end{gather}
$$

又由于我们定义 $f$ 在 $\{ \gamma \}=\{ \gamma \circ\varphi \}$ 上连续，因此积分 $\int_{\gamma \circ\varphi}f$ 是良定的。

**定理 2.1.10**

设 $\gamma\colon[a,b]\to \mathbb{C}$ 是可求长路径，$\varphi\colon[c,d]\to[a,b]$ 是连续单调递增函数，满足 $\varphi(c)=a,\varphi(d)=b$，则对任意在 $\{ \gamma \}$ 上连续的函数 $f$，有

$$
\begin{gather}
\int_{\gamma}f=\int_{\gamma \circ\varphi} f
\end{gather}
$$

**证明**

任取 $\varepsilon>0$，则存在 $\delta_{1}>0$ 使得当 $[c,d]$ 的划分 $\{ s_{0}<\dots<s_{n} \}$ 满足 $s_{k}-s_{k-1}<\delta_{1}$，且 $s_{k-1}\leq\sigma_{k}\leq s_{k}$ 时有

$$
\begin{gather}
\left\lvert  \int_{\gamma \circ\varphi} f-\sum_{k=1}^{n} f(\gamma \circ\varphi(\sigma_{k}))(\gamma \circ\varphi(s_{k})-\gamma \circ\varphi(s_{k-1}))  \right\rvert < \dfrac{\varepsilon}{2}
\end{gather}
$$

同样，存在 $\delta_{2}>0$ 使得 $[a,b]$ 的划分 $\{ t_{0}<\dots<t_{n} \}$ 满足 $t_{k}-t_{k-1}<\delta_{2}$，且 $t_{k-1}\leq \tau_{k}\leq t_{k}$ 时有

$$
\begin{gather}
\left\lvert  \int_{\gamma}f-\sum_{k=1}^{n} f(\gamma(\tau_{k}))(\gamma(t_{k})-\gamma(t_{k-1}))  \right\rvert < \dfrac{\varepsilon}{2}
\end{gather}
$$

由于 $\varphi$ 在 $[c,d]$ 上一致连续，因此存在 $0<\delta<\delta_{1}$ 使得 $|s-s'|<\delta$ 蕴含 $|\varphi(s)-\varphi(s')|<\delta_{2}$. 于是，当 $\{ s_{0}<\dots<s_{n} \}$ 满足 $s_{k}-s_{k-1}<\delta$ 时，取 $t_{k}=\varphi(s_{k})$，则有 $t_{k}-t_{k-1}=\varphi(s_{k})-\varphi(s_{k-1})<\delta_{2}$. 再取 $\sigma_{k}\in[s_{k-1},s_{k}]$，$\tau_{k}=\varphi(\sigma_{k})$，则此时上述两个不等式同时成立，并且其中的求和式相等。这给出

$$
\begin{gather}
\left\lvert  \int_{\gamma}f-\int_{\gamma \circ\varphi}  \right\rvert <\varepsilon
\end{gather}
$$

这就完成了证明。

上面的定理引导我们在可求长路径的集合上定义这样一个等价关系，使得一个等价类中的元素具有相同的轨迹，并且连续函数在轨迹上的积分都相同。根据上述定理，似乎我们应该定义 $\gamma$ 等价于 $\sigma$ 当且仅当存在 $\varphi$ 使得 $\sigma=\gamma \circ\varphi$. 然而，对于单调递增函数 $\varphi$，它不一定是可逆的，因此这不是一个等价关系。（不满足对称性）

于是，我们只能加强 $\varphi$ 的限制，令它是**严格**单调递增的。这就给出了平面上“曲线”的定义。

**定义 2.1.11** 曲线（curve）

设 $\sigma\colon[c,d]\to \mathbb{C}$ 和 $\gamma\colon[a,b]\to \mathbb{C}$ 是可求长路径，定义 $\sigma$ **等价于** $\gamma$，如果存在连续且严格单调递增的函数 $\varphi\colon[c,d]\to[a,b]$ 满足 $\varphi(c)=a,\varphi(d)=b$，使得 $\sigma=\gamma \circ\varphi$. 我们称 $\varphi$ 是一个**重参数化**。

一条**曲线**是路径的一个等价类。曲线的轨迹定义为等价类中任意路径的轨迹，并且连续函数 $f$ 沿着曲线的积分定义为 $f$ 沿着等价类中任意路径的积分。一条曲线是（分段）光滑的当且仅当等价类中存在（分段）光滑的路径。

由于定理 2.1.10，我们可以将曲线与等价类中的路径等同，这种符号的滥用不会对我们的积分理论产生任何严重的错误。

设 $\gamma\colon[a,b]\to \mathbb{C}$ 是一条可求长路径，对于 $t\in[a,b]$，我们定义它的**总变差函数**为

$$
\begin{align}
|\gamma|(t) &= V(\gamma,[a,t]) \\
&= \sup \left\{  \sum_{k=1}^{n} |\gamma(t_{k})-\gamma(t_{k-1})| \middle| a=t_{0}<t_{1}<\dots<t_{n}=t, n\geq 1  \right\}
\end{align}
$$

显然 $|\gamma|(t)$ 是单调递增的，从而具有有界变差。如果 $f$ 在 $\{ \gamma \}$ 上连续，那么我们定义

$$
\begin{gather}
\int_{\gamma} f(z)|\mathrm{d} z|=\int_{a}^{b} f(\gamma(t)) \mathrm{d} |\gamma|(t)
\end{gather}
$$

此外，对于可求长曲线 $\gamma$，我们定义 $-\gamma$ 为曲线 $(-\gamma)(t)=\gamma(-t)$，其中 $t \in[-b,-a]$. 再设 $c \in \mathbb{C}$，我们定义 $\gamma+c$ 为曲线 $(\gamma+c)(t)=\gamma(t)+c$.

**定理 2.1.12**

设 $\gamma$ 是可求长曲线，$f$ 在 $\{ \gamma \}$ 上连续，则：

1. $\displaystyle \int_{-\gamma}f=-\int_{\gamma}f$
2. $\displaystyle \left\lvert  \int_{\gamma} f  \right\rvert\leq \int_{\gamma} |f(z)||\mathrm{d}z|\leq V(\gamma) \sup_{z\in \{ \gamma \}}|f(z)|$
3. 如果 $c \in \mathbb{C}$，则 $\displaystyle \int_{\gamma}f(z)\mathrm{d}z=\int_{\gamma+c}f(z-c)\mathrm{d}z$

**证明**

(1). 设 $\gamma\colon[a,b]\to \mathbb{C}$，则对任意 $\varepsilon>0$，存在 $\delta>0$ 使得当 $[a,b]$ 的划分 $\{ t_{0}<\dots<t_{n} \}$ 满足 $t_{k}-t_{k-1}<\delta$，且 $t_{k-1}\leq \tau_{k}\leq t_{k}$ 时有

$$
\begin{gather}
\left\lvert  \int_{\gamma} f-\sum_{k=1}^{n} f(\gamma(\tau_{k})) (\gamma(t_{k})-\gamma(t_{k-1}))  \right\rvert < \dfrac{\varepsilon}{2}
\end{gather}
$$

同样，当 $[-b,-a]$ 的划分 $\{ s_{0}<\dots<s_{n} \}$ 满足 $s_{k}-s_{k-1}<\delta$，且 $s_{k-1}\leq\sigma_{k}\leq s_{k}$ 时有

$$
\begin{gather}
\left\lvert  \int_{-\gamma} f-\sum_{k=1}^{n} f(\gamma(-\sigma_{k}))(\gamma(-s_{k})-\gamma(-s_{k-1}))  \right\rvert <\dfrac{\varepsilon}{2}
\end{gather}
$$

令 $s_{k}=-t_{n-k}$，$\sigma_{k}=-\tau_{n-k+1}$，则有

$$
\begin{gather}
\left\lvert  \int_{-\gamma}f+\sum_{k=1}^{n} f(\gamma(\tau_{n-k+1}))(\gamma(t_{n-k+1})-\gamma(t_{n-k}))  \right\rvert < \dfrac{\varepsilon}{2}
\end{gather}
$$

从而根据三角不等式有

$$
\begin{gather}
\left\lvert  \int_{-\gamma}f+\int_{\gamma}f  \right\rvert <\varepsilon
\end{gather}
$$

(2). 第二个不等式是显然的：

$$
\begin{align}
\int_{\gamma} |f(z)||\mathrm{d} z|\leq \sup_{z\in \{ \gamma \}} |f(z)| \int_{a}^{b} \mathrm{d} |\gamma|(t)=V(\gamma) \sup_{z\in \{ \gamma \}} |f(z)|
\end{align}
$$

对于第一个不等式，由于

$$
\begin{gather}
|\gamma|(t_{k})-|\gamma|(t_{k-1})=V(\gamma,[t_{k-1},t_{k}])\geq|\gamma(t_{k})-\gamma(t_{k-1})|
\end{gather}
$$

因此利用 (1) 中的不等式，我们有

$$
\begin{align}
\left\lvert  \int_{\gamma} f  \right\rvert &\leq \dfrac{\varepsilon}{2}+\left\lvert  \sum_{k=1}^{n} f(\gamma(\tau_{k}))(\gamma(t_{k})-\gamma(t_{k-1}))  \right\rvert  \\
&\leq \dfrac{\varepsilon}{2}+\sum_{k=1}^{n} |f(\gamma(\tau_{k}))||\gamma(t_{k})-\gamma(t_{k-1})| \\
&\leq \dfrac{\varepsilon}{2}+\sum_{k=1}^{n} |f(\gamma(\tau_{k}))|(|\gamma|(t_{k})-|\gamma|(t_{k-1}))
\end{align}
$$

再根据常规的 $\varepsilon-\delta$ 论证得

$$
\begin{gather}
\left\lvert  \int_{\gamma}|f(z)||\mathrm{d} z|-\sum_{k=1}^{n} |f(\gamma(\tau_{k}))|(|\gamma|(t_{k})-|\gamma|(t_{k-1}))  \right\rvert < \dfrac{\varepsilon}{2}
\end{gather}
$$

这给出

$$
\begin{gather}
\left\lvert  \int_{\gamma} f  \right\rvert\leq\varepsilon+\int_{\gamma}|f(z)||\mathrm{d} z|
\end{gather}
$$

根据 $\varepsilon$ 的任意性即证。

(3). 由于

$$
\begin{gather}
f((\gamma+c)(\tau_{k})-c)((\gamma+c)(t_{k})-(\gamma+c)(t_{k-1}))=f(\gamma(\tau_{k}))(\gamma(t_{k})-\gamma(t_{k-1}))
\end{gather}
$$

因此同样根据 $\varepsilon-\delta$ 论证，我们有

$$
\begin{gather}
\left\lvert  \int_{\gamma+c}f(z-c)\mathrm{d} z-\sum_{k=1}^{n} f(\gamma(\tau_{k}))(\gamma(t_{k})-\gamma(t_{k-1}))  \right\rvert <\dfrac{\varepsilon}{2}
\end{gather}
$$

利用 (1) 中的不等式，即证

$$
\begin{gather}
\left\lvert  \int_{\gamma+c}f(z-c)\mathrm{d} z-\int_{\gamma}f(z)\mathrm{d} z  \right\rvert <\varepsilon
\end{gather}
$$

这就完成了证明。

下一个定理是实数上的微积分基本定理的对应物。

**定理 2.1.13**

设 $G\subset \mathbb{C}$ 是开集，$\gamma$ 是 $G$ 上的可求长曲线，具有起点 $\alpha$ 和终点 $\beta$，如果 $f\colon G\to \mathbb{C}$ 是一个连续函数，并且有原函数 $F\colon G\to \mathbb{C}$，则

$$
\begin{gather}
\int_{\gamma} f=F(\beta)-F(\alpha)
\end{gather}
$$

为证这一定理，我们需要下面的引理：

**引理 2.1.14**

如果 $G\subset \mathbb{C}$ 是开集，$\gamma\colon[a,b]\to \mathbb{C}$ 是可求长曲线，且 $f\colon G\to \mathbb{C}$ 是连续函数，那么对任意 $\varepsilon>0$，存在折线 $\Gamma \subset G$ 使得 $\Gamma(a)=\gamma(a),\Gamma(b)=\gamma(b)$，并且

$$
\begin{gather}
\left\lvert  \int_{\gamma}f-\int_{\Gamma}f  \right\rvert <\varepsilon
\end{gather}
$$

**证明**

情形一：设 $G$ 是一个开圆盘。由于 $\{ \gamma \}$ 紧致，因此 $d=d(\{ \gamma \},\partial G)>0$，从而如果 $G=B(c,r)$，则 $\{ \gamma \}\subset B(c,\rho)$，其中 $\rho=r-d /2$. 于是 $f$ 在紧致集 $\overline{B(c,\rho)}$ 上一致连续。不失一般性，我们可以假设 $f$ 在 $G$ 上一致连续。选取 $\delta>0$ 使得 $|z-w|<\delta$ 蕴含 $|f(z)-f(w)|<\varepsilon$，由于 $\gamma$ 一致连续，因此存在划分 $\{ t_{0}<\dots<t_{n} \}$ 使得

$$
\begin{gather}
|\gamma(s)-\gamma(t)|<\delta
\end{gather}
$$

对任意 $t_{k-1}\leq s,t\leq t_{k}$ 成立。取 $t_{k-1}\leq \tau_{k}\leq t_{k}$ 我们有

$$
\begin{gather}
\left\lvert  \int_{\gamma}f-\sum_{k=1}^{n} f(\gamma(\tau_{k}))(\gamma(t_{k})-\gamma(t_{k-1}))  \right\rvert <\varepsilon
\end{gather}
$$

定义 $\Gamma\colon[a,b]\to \mathbb{C}$ 为连接 $\gamma(t_{k-1})$ 和 $\gamma(t_{k})$ 的折线，即

$$
\begin{gather}
\Gamma(t)=\dfrac{1}{t_{k}-t_{k-1}}((t_{k}-t)\gamma(t_{k-1})+(t-t_{k-1})\gamma(t_{k})),\quad t_{k-1}\leq t\leq t_{k}
\end{gather}
$$

从而

$$
\begin{gather}
|\Gamma(t)-\gamma(\tau_{k})|<\delta
\end{gather}
$$

对 $t_{k-1}\leq t\leq t_{k}$ 成立。由于 $\int_{\Gamma}f=\int_{a}^{b}f(\Gamma(t))\Gamma'(t)\mathrm{d}t$，因此

$$
\begin{gather}
\int_{\Gamma}f=\sum_{k=1}^{n} \dfrac{\gamma(t_{k})-\gamma(t_{k-1})}{t_{k}-t_{k-1}} \int_{t_{k-1}}^{t_{k}} f(\Gamma(t))\mathrm{d} t
\end{gather}
$$

从而我们有

$$
\begin{align}
&\left\lvert  \int_{\gamma}f-\int_{\Gamma}f  \right\rvert < \varepsilon+\left\lvert  \sum_{k=1}^{n} f(\gamma(\tau_{k}))(\gamma(t_{k})-\gamma(t_{k-1}))-\int_{\Gamma}f  \right\rvert  \\
&\leq\varepsilon+\sum_{k=1}^{n} |\gamma(t_{k})-\gamma(t_{k-1})| \dfrac{1}{t_{k}-t_{k-1}} \int_{t_{k-1}}^{t_{k}} |f(\Gamma(t))-f(\gamma(\tau_{k}))|\mathrm{d} t \\
&\leq \varepsilon+\varepsilon \sum_{k=1}^{n} |\gamma(t_{k})-\gamma(t_{k-1})|\leq \varepsilon(1+V(\gamma))
\end{align}
$$

这就完成了情形一的证明。

情形二：$G$ 是任意开集。由于 $\{ \gamma \}$ 紧致，故有 $r>0$ 使得 $r<d(\{ \gamma \},\partial G)$. 选取 $\delta>0$ 使得 $|s-t|<\delta$ 蕴含 $|\gamma(s)-\gamma(t)|<r$. 设 $P=\{ t_{0}<\dots<t_{n} \}$ 是 $[a,b]$ 的划分，当 $\lVert P \rVert<\delta$ 时，对 $t\in[t_{k-1},t_{k}]$ 有 $|\gamma(t)-\gamma(t_{k-1})|<r$，因此 $\gamma$ 在 $[t_{k-1},t_{k}]$ 上的限制 $\gamma_{k}$ 满足 $\{ \gamma_{k} \}\subset B(\gamma(t_{k-1}),r)$. 根据情形一，存在折线 $\Gamma_{k}\colon[t_{k-1},t_{k}]\to \mathbb{C}$ 使得 $\Gamma_{k}(t_{k-1})=\gamma(t_{k-1}),\Gamma_{k}(t_{k})=\gamma(t_{k})$，并且 $\left\lvert  \int_{\gamma_{k}}f-\int_{\Gamma_{k}}f  \right\rvert<\varepsilon /n$. 我们定义 $\Gamma\colon[a,b]\to \mathbb{C}$ 在 $[t_{k-1},t_{k}]$ 上等于 $\Gamma_{k}$，则 $\Gamma$ 就是所求的折线。

**证明**（2.1.13）

情形一：$\gamma\colon[a,b]\to \mathbb{C}$ 是分段光滑曲线。则根据微积分基本定理有

$$
\begin{gather}
\int_{\gamma}f=\int_{a}^{b} f(\gamma(t))\gamma'(t)\mathrm{d} t=\int_{a}^{b}(F\circ\gamma)'(t)\mathrm{d} t=F(\beta)-F(\alpha)
\end{gather}
$$

情形二：$\gamma$ 是任意可求长曲线。利用引理 2.1.14，存在折线 $\Gamma$ 使得 $\left\lvert  \int_{\gamma}f-\int_{\Gamma}f  \right\rvert<\varepsilon$，而折线 $\Gamma$ 是分段光滑的，于是根据情形一有

$$
\begin{gather}
\left\lvert  \int_{\gamma}f-(F(\beta)-F(\alpha))  \right\rvert <\varepsilon
\end{gather}
$$

由 $\varepsilon$ 的任意性即证。

可见，利用引理 2.1.14，我们可以将关于可求长曲线的论证转化为关于分段光滑曲线的论证。这样的技巧将在后续的章节中多次使用。

一条曲线 $\gamma\colon[a,b]\to \mathbb{C}$ 是**闭的**，如果 $\gamma(a)=\gamma(b)$. 于是，在定理 2.1.13 的条件下，我们有推论：

**定理 2.1.15**

设 $G\subset \mathbb{C}$ 是开集，$\gamma$ 是 $G$ 上的可求长闭曲线，如果 $f\colon G\to \mathbb{C}$ 是一个连续函数，并且有原函数 $F\colon G\to \mathbb{C}$，则

$$
\begin{gather}
\int_{\gamma} f=0
\end{gather}
$$

尽管定理 2.1.13 是实数上的微积分基本定理的对应，但它是一个更弱的结论：微积分基本定理表明连续函数必然有原函数，从而有 Newton-Leibnitz 公式成立。这对复函数不成立，例如 $f(z)=|z|^{2}$. 假设 $F$ 是 $f$ 的原函数，那么 $F$ 是解析的，从而满足 Cauchy-Riemann 方程：

$$
\begin{gather}
\dfrac{ \partial U }{ \partial x }=\dfrac{ \partial V }{ \partial y } =x^{2}+y^{2}, \quad \dfrac{ \partial U }{ \partial y } =\dfrac{ \partial V }{ \partial x } =0 
\end{gather}
$$

但 $\dfrac{ \partial U }{ \partial y }=0$ 表明 $U(x,y)=u(x)$，于是 $\dfrac{ \partial U }{ \partial x }=u'(x)=x^{2}+y^{2}$，构成矛盾。因此，$f(z)=|z|^{2}$ 没有原函数。

> 在定义路径积分 $\int_{\gamma}f(z)\mathrm{d}z$ 时，我们使用的底层结构是 Riemann-Stieltjes 积分。不过，事实上我们完全可以以 Lebesgue 积分为基础来定义路径积分：给定可求长曲线 $\gamma$，其诱导了 $[a,b]$ 上的复测度 $\mu_{\gamma}$，从而对于连续函数 $f$，Lebesgue-Stieltjes 积分 $\int_{[a,b]} (f\circ\gamma)\mathrm{d}\mu_{\gamma}$ 良定，并且等于 Riemann-Stieltjes 积分 $\int_{a}^{b}f(\gamma(t))\mathrm{d}\gamma(t)$.
> 
> 然而，使用 Riemann-Stieltjes 积分作为路径积分的定义有其内在的合理性：在复分析中，我们所研究的函数 $f$ 通常至少是连续的，这便使得测度论工具的引入成为一种不必要的抽象化。其次，在 Riemann-Stieltjes 积分观点下，路径积分在重参数化下保持不变（定理 2.1.10）这一结论是内蕴的，反而在 Lebesgue-Stieltjes 积分观点下需要额外处理测度的变化，丢失了其几何直观性。

# Section 2: 解析函数的幂级数展开

在本节中，我们将第一次见识到解析函数的刚性，即开集上的解析函数有幂级数展开。特别地，开集上的解析函数是无穷次可微的。

首先，我们证明一个引理：

**引理 2.2.1**

设 $|z|<1$，则

$$
\begin{gather}
\int_{0}^{2\pi} \dfrac{e^{is}}{e^{is}-z}\mathrm{d} s=2\pi
\end{gather}
$$

**证明**

令 $\varphi(s,t)=\dfrac{e^{is}}{e^{is}-tz}$，其中 $s \in[0,2\pi],t \in[0,1]$. 由于 $\varphi$ 连续可微，因此 $g(t)=\int_{0}^{2\pi}\varphi(s,t)\mathrm{d}s$ 是连续可微的。此外，$g(0)=2\pi$，因此如果我们可以证明 $g$ 是常值函数，那么就有所要的结论 $g(1)=2\pi$.

根据 Leibnitz 法则，我们有

$$
\begin{gather}
g'(t)=\int_{0}^{2\pi} \dfrac{ze^{is}}{(e^{is}-tz)^{2}} \mathrm{d} s=\left. \dfrac{iz}{e^{is}-tz} \right|_{s=0}^{s=2\pi}=0
\end{gather}
$$

因此 $g$ 是一个常值函数，这就完成了证明。

下一个结论尽管重要，却是一个暂时的引理：我们将见到一个更为普遍的公式——Cauchy 积分公式，它是复分析的核心定理之一。

**定理 2.2.2**

设 $f\colon G\to \mathbb{C}$ 是解析函数，并且 $\overline{B(a,r)}\subset G$. 如果 $\gamma(t)=a+re^{it}$，其中 $0\leq t\leq 2\pi$，则

$$
\begin{gather}
f(z)=\dfrac{1}{2\pi i} \int_{\gamma} \dfrac{f(w)}{w-z}\mathrm{d} w
\end{gather}
$$

对任意 $|z-a|<r$ 成立。

**证明**

通过设 $G_{1}=\{ (z-a) /r \mid z \in G \}$ 并取 $g(z)=f(a+rz),z \in G_{1}$，我们可以不失一般性地假设 $a=0,r=1$. 即，我们可以假设 $\overline{B(0,1)}\subset G$.

取 $|z|<1$，我们要证

$$
\begin{align}
f(z)=\dfrac{1}{2\pi i}\int_{\gamma} \dfrac{f(w)}{w-z}\mathrm{d} w=\dfrac{1}{2\pi} \int_{0}^{2\pi} \dfrac{f(e^{is})e^{is}}{e^{is}-z} \mathrm{d} s
\end{align}
$$

这就是说，我们要证

$$
\begin{align}
0 &= \int_{0}^{2\pi} \dfrac{f(e^{is})e^{is}}{e^{is}-z}\mathrm{d} s-2\pi f(z) \\
&= \int_{0}^{2\pi} \left( \dfrac{f(e^{is})e^{is}}{e^{is}-z}-f(z) \right) \mathrm{d} s
\end{align}
$$

设 $\varphi(s,t)=\dfrac{f((1-t)z+te^{is})e^{is}}{e^{is}-z}-f(z)$，其中 $t \in [0,1],s \in[0,2\pi]$，由于当 $0<t<1$ 时 $|(1-t)z+te^{is}|<1$，因此 $\varphi$ 良定并且连续可微，从而 $g(t)=\int_{0}^{2\pi}\varphi(s,t)\mathrm{d}s$ 是连续可微的。

我们需要证明 $g(1)=0$，这可以通过证明 $g(0)=0$ 且 $g$ 是常值函数得到。根据引理 2.2.1，我们有

$$
\begin{align}
g(0) = f(z) \int_{0}^{2\pi} \dfrac{e^{is}}{e^{is}-z}\mathrm{d} s-2\pi f(z)=0
\end{align}
$$

此外，根据 Leibnitz 法则，我们有 $g'(t)=\int_{0}^{2\pi}\varphi_{2}(s,t)\mathrm{d}s$，其中

$$
\begin{gather}
\varphi_{2}(s,t)=e^{is} f'((1-t)z+te^{is})
\end{gather}
$$

而当 $0<t\leq 1$ 时 $\varphi_{2}$ 有原函数 $\Phi(s)=\dfrac{f((1-t)z+te^{is})}{it}$，因此 $g'(t)=\Phi(2\pi)-\Phi(0)=0$，从而 $g=0$ 为常值函数，这就完成了证明。

上述结论如何帮助我们得到解析函数的幂级数展开呢？答案是我们使用几何级数：设 $|z-a|<r$ 且 $w$ 在圆 $|z-a|=r$ 上，则

$$
\begin{gather}
\dfrac{1}{w-z}=\dfrac{1}{w-a}\cdot \dfrac{1}{1-\frac{z-a}{w-a}}=\dfrac{1}{w-a} \sum_{n=0}^{\infty} \left( \dfrac{z-a}{w-a} \right)^{n}
\end{gather}
$$

由于 $|z-a|<|w-a|=r$，故右侧的级数绝对且一致收敛。于是我们在等式两边乘以 $f(z) /2\pi i$ 并沿着圆周 $\gamma\colon|w-a|=r$ 积分，则等式左边就变成了 $f(z)$，而右边通过对级数逐项积分，就给出了 $f(z)$ 幂级数展开式中的系数，这便是下一个定理的主要内容。不过，首先我们需要验证逐项积分的可行性。

**引理 2.2.3**

设 $\gamma$ 是可求长曲线，$F_{n},F$ 在 $\{ \gamma \}$ 上连续，如果 $F_{n}$ 一致收敛于 $F$，那么

$$
\begin{gather}
\int_{\gamma} F=\lim_{ n \to \infty } \int_{\gamma} F_{n}
\end{gather}
$$

**证明**

任取 $\varepsilon>0$，则存在 $N$ 使得对任意 $n>N$ 有 $|F_{n}(w)-F(w)|<\varepsilon /V(\gamma)$ 对任意 $w \in \{ \gamma \}$ 成立，从而有

$$
\begin{align}
\left\lvert  \int_{\gamma} F_{n}-\int_{\gamma} F  \right\rvert &= \left\lvert  \int_{\gamma} (F_{n}-F)  \right\rvert  \\
&\leq \int_{\gamma} |F_{n}(w)-F(w)||\mathrm{d} w| \\
&< \varepsilon
\end{align}
$$

对任意 $n>N$ 成立。

**定理 2.2.4**

设 $f$ 在 $B(a,R)$ 上解析，则 $f(z)=\sum_{n=0}^{\infty}a_{n}(z-a)^{n}$ 对任意 $|z-a|<R$ 成立，其中 $a_{n}=\dfrac{1}{n!}f^{(n)}(a)$，并且级数的收敛半径 $\geq R$.

**证明**

令 $0<r<R$，从而 $\overline{B(a,r)}\subset B(a,R)$. 如果 $\gamma(t)=a+re^{it}$，$0\leq t\leq 2\pi$，则根据定理 2.2.2 有

$$
\begin{gather}
f(z)= \dfrac{1}{2\pi i} \int_{\gamma} \dfrac{f(w)}{w-z} \mathrm{d} w
\end{gather}
$$

对 $|z-a|<r$ 成立。又因为 $w$ 在圆 $|z-a|=r$ 上，故

$$
\begin{gather}
\dfrac{|f(w)||z-a|^{n}}{|w-a|^{n+1}}\leq \dfrac{M}{r} \left( \dfrac{|z-a|}{r} \right)^{n}
\end{gather}
$$

其中 $M=\max_{w \in \{ \gamma \}}|f(w)|$. 由于 $|z-a| /r<1$，因此 Weierstrass M 判别法表明级数 $\sum_{n=0}^{\infty}f(w)(z-a)^{n} /(w-a)^{n+1}$ 一致收敛，从而由逐项积分法得

$$
\begin{gather}
f(z)=\sum_{n=0}^{\infty} \left( \dfrac{1}{2\pi i} \int_{\gamma} \dfrac{f(w)}{(w-a)^{n+1}} \mathrm{d} w \right) (z-a)^{n}
\end{gather}
$$

如果我们取

$$
\begin{gather}
a_{n}=\dfrac{1}{2\pi i} \int_{\gamma} \dfrac{f(w)}{(w-a)^{n+1}} \mathrm{d} w
\end{gather}
$$

那么 $a_{n}$ 与 $z$ 无关，从而级数 $\sum_{n=0}^{\infty}a_{n}(z-a)^{n}$ 在 $|z-a|<r$ 时收敛于 $f(z)$. 此外，根据幂级数的逐项微分定理，我们有 $a_{n}=\dfrac{1}{n!}f^{(n)}(a)$，从而 $a_{n}$ 也与 $\gamma$ 无关，换句话说，$a_{n}$ 与 $r$ 无关。由于 $r<R$ 是任意的，我们可知 $f(z)=\sum_{n=0}^{\infty}a_{n}(z-a)^{n}$ 对任意 $|z-a|<R$ 成立，这表明级数的收敛半径至少为 $R$，这就完成了证明。

由以上定理，我们得到推论：

**定理 2.2.5**

如果 $f\colon G\to \mathbb{C}$ 是解析函数，$a \in G$，则 $f(z)=\sum_{n=0}^{\infty}a_{n}(z-a)^{n}$ 对任意 $|z-a|<R=d(a,\partial G)$ 成立。

**定理 2.2.6**

如果 $f\colon G\to \mathbb{C}$ 是解析的，那么 $f$ 是无穷次可微的。

**定理 2.2.7**

如果 $f\colon G\to \mathbb{C}$ 是解析函数，并且 $\overline{B(a,r)}\subset G$，则

$$
\begin{gather}
f^{(n)}(a)=\dfrac{n!}{2\pi i} \int_{\gamma} \dfrac{f(w)}{(w-a)^{n+1}} \mathrm{d} w
\end{gather}
$$

其中 $\gamma(t)=a+re^{it},0\leq t\leq 2\pi$.

**定理 2.2.8** Cauchy 估计公式（Cauchy's Estimate）

设 $f$ 在 $B(a,R)$ 上解析，且 $|f(z)|\leq M$ 对任意 $z \in B(a,R)$ 成立，则

$$
\begin{gather}
|f^{(n)}(a)|\leq \dfrac{n!M}{R^{n}}
\end{gather}
$$

**证明**

取 $0<r<R$，利用定理 2.2.7，我们有

$$
\begin{align}
|f^{(n)}(a)|\leq \dfrac{n!}{2\pi} \cdot \dfrac{M}{r^{n+1}} \cdot 2\pi r=\dfrac{n!M}{r^{n}}
\end{align}
$$

由于 $r<R$ 是任意的，令 $r\to R-$ 即证。

我们以下面的命题结束本节，它是一个更普遍的定理（Cauchy 定理）的特例，而后者将在后续的章节进行阐述。

**定理 2.2.9** Cauchy 定理（特例）

设 $f$ 在 $B(a,R)$ 上解析，$\gamma$ 是 $B(a,R)$ 中的可求长闭曲线，则

$$
\begin{gather}
\int_{\gamma} f=0
\end{gather}
$$

**证明**

根据定理 2.1.15，我们只需证明 $f$ 有原函数。根据 $f$ 的幂级数展开，我们令

$$
\begin{gather}
F(z)=\sum_{n=0}^{\infty} \dfrac{a_{n}}{n+1}(z-a)^{n+1}
\end{gather}
$$

由于 $\lim_{ n \to \infty }(n+1)^{1/n}=1$，因此上述级数的收敛半径与 $\sum a_{n}(z-a)^{n}$ 相同，从而 $F$ 在 $B(a,R)$ 上良定，并且根据逐项微分定理有 $F'(z)=f(z)$ 对任意 $|z-a|<R$ 成立。这就完成了证明。

# Section 3: 解析函数的零点

如果 $p(z),s(z)$ 是两个多项式，那么一个广为人知的事实是，存在唯一的多项式 $q(z),r(z)$ 使得 $p(z)=s(z)q(z)+r(z)$，其中 $\mathrm{deg}\,r<\mathrm{deg}\,q$. 特别地，当 $p(a)=0$ 时，取 $s(z)=z-a$，则有 $r(z)=0,p(z)=(z-a)q(z)$. 如果进一步还有 $q(a)=0$，那么我们可以对 $q(z)$ 做进一步的分解，得到 $p(z)=(z-a)^{m}t(z)$，其中 $t(a)\neq 0$，且 $\mathrm{deg}\,t=\mathrm{deg}\,p-m$.

**定义 2.3.1** 重数（multiplicity）

设 $f\colon G\to \mathbb{C}$ 是解析函数，$a \in G$ 满足 $f(a)=0$，则称 $a$ 是 $f$ 的一个具有**重数** $m\geq 1$ 的零点，如果存在解析函数 $g\colon G\to \mathbb{C}$ 使得 $g(a)\neq 0$ 且 $f(z)=(z-a)^{m}g(z)$.

回到我们对多项式零点的讨论。显然，一个多项式零点的重数一定小于等于多项式的次数。如果 $n=\mathrm{deg}\,p$，且 $a_{1},\dots,a_{k}$ 是 $p$ 的不同零点，那么根据前面的讨论可知 $p(z)=(z-a_{1})^{m_{1}}\cdots(z-a_{k})^{m_{k}}s(z)$，其中 $s(z)$ 是一个没有零点的多项式。现在，根据代数基本定理，一个没有零点的多项式是常值函数。于是，如果我们能够证明代数基本定理，那么我们就完成了多项式的因子分解。这正是本节我们要做的工作。

**定义 2.3.2** 整函数（entire function）

函数 $f\colon \mathbb{C}\to \mathbb{C}$ 是一个**整函数**，如果 $f$ 在 $\mathbb{C}$ 上解析。

**定理 2.3.3**

如果 $f$ 是一个整函数，那么 $f$ 的幂级数展开式

$$
\begin{gather}
f(z)=\sum_{n=0}^{\infty} a_{n}z^{n}
\end{gather}
$$

具有无穷大的收敛半径。

**证明**

对任意 $R>0$，$f$ 在 $B(0,R)$ 上解析，则级数 $f(z)=\sum a_{n}z^{n}$ 对 $|z|<R$ 成立，这就完成了证明。

根据以上定理，我们可以将整函数视为一种“无穷次”的多项式。这就引出了问题：多项式的性质是否能够推广到整函数上？例如，整函数是否能够分解为因子的乘积？这便是 **Weierstrass 分解定理**，它将在后续的章节中得到证明。另一个多项式的性质是没有有界的非常值多项式：事实上，如果 $p(z)=z^{n}+a_{n-1}z^{n-1}+\dots+a_{0}$，则

$$
\begin{gather}
\lim_{ z \to \infty } p(z)=\lim_{ z \to \infty } z^{n}(1+a_{n-1}z^{-1}+\dots+a_{0}z^{-n})=\infty
\end{gather}
$$

下面的定理表明，这一性质对于整函数也成立。

**定理 2.3.4** Liouville 定理

如果 $f$ 是有界整函数，那么 $f$ 是常值函数。

**证明**

假设 $|f(z)|\leq M$ 对任意 $z \in \mathbb{C}$ 成立。根据 Cauchy 估计公式，由于 $f$ 在 $B(z,R)$ 上解析，故 $|f'(z)|\leq M /R$ 对任意 $R>0$ 成立，从而 $f'(z)=0$. 又因为 $\mathbb{C}$ 是连通集，故 $f$ 是常值函数。

尽管上述定理的证明简短，但它却是一个极为重要的定理：根据这一定理，我们可以给出代数基本定理的一个分析证明。

**定理 2.3.5** 代数基本定理（Fundamental Theorem of Algebra）

如果 $p(z)$ 是一个非常值多项式，那么存在 $a \in \mathbb{C}$ 使得 $p(a)=0$.

**证明**

假设 $p(z)\neq 0$ 对任意 $z \in \mathbb{C}$ 成立。则 $f(z)=p(z)^{-1}$ 是一个整函数。由于 $p(z)$ 非常值，故 $\lim_{ z \to \infty }p(z)=\infty$，从而 $\lim_{ z \to \infty }f(z)=0$. 即存在 $R>0$ 使得 $|z|>R$ 蕴含 $|f(z)|<1$. 又由于 $\overline{B(0,R)}$ 是紧致集，故 $f$ 在 $|z|\leq R$ 也是有界的，从而根据 Liouville 定理知 $f$ 是常值函数，矛盾。

**定理 2.3.6**

如果 $p(z)$ 是一个多项式，并且 $a_{1},\dots,a_{k}$ 是 $p$ 的所有不同零点，其中 $a_{\ell}$ 的重数为 $m_{\ell}$，则存在 $c \in \mathbb{C}$ 使得

$$
\begin{gather}
p(z)=c(z-a_{1})^{m_{1}}\cdots (z-a_{k})^{m_{k}}
\end{gather}
$$

并且 $m_{1}+\dots+m_{k}=\mathrm{deg}\,p$.

再回到整函数与多项式的类比上。需注意的是，这一类比并不能完全将多项式的性质移植到整函数上。例如，一个非常值多项式能够取到 $\mathbb{C}$ 上的任意值：对多项式 $p(z)-a$ 应用代数基本定理即可。但整函数 $e^{z}$ 没有这一性质，因为不存在 $z \in \mathbb{C}$ 使得 $e^{z}=0$. 然而，我们可以证明这就是最糟糕的情况了，即，整函数的值域是整个 $\mathbb{C}$，最多只有一个例外。这一结论称为 **Picard 小定理**。此外，我们也不应将 $G$ 上的解析函数与 $\mathbb{C}$ 上的多项式做类比，在这种情况下，我们只能将其类比为 $G$ 上的多项式。

设 $|z|<1$，令

$$
\begin{gather}
f(z)=\cos \dfrac{1+z}{1-z}
\end{gather}
$$

注意到 $\dfrac{1+z}{1-z}$ 将圆盘 $D=\{ z \mid |z|<1 \}$ 映射到 $G=\{ z \mid \mathrm{Re}\,z>0 \}$. $f$ 的零点集为 $\left\{  \dfrac{n\pi-2}{n\pi+2} \middle| n=2k+1  \right\}$，因此 $f$ 有无穷多个零点。当 $n\to \infty$ 时，$\dfrac{n\pi-2}{n\pi+2}\to 1$，后者不在 $f$ 的解析域 $D$ 中。这是最一般情况下的故事。然而，一旦零点的极限落在 $D$ 中，如下定理所示，函数 $f$ 就会立刻退化为平凡的情况：

**定理 2.3.7**

设 $G\subset \mathbb{C}$ 是连通开集，$f\colon G\to \mathbb{C}$ 是解析函数，则以下命题等价：

1. $f=0$ 是常值函数
2. 存在 $a \in G$ 使得对任意 $n\geq 0$ 有 $f^{(n)}(a)=0$
3. $\{ z \in G \mid f(z)=0 \}$ 在 $G$ 中有一个极限点

**证明**

显然 1 蕴含 2 和 3. 假设 3 成立，令 $a \in G$ 为 $Z=\{ z \in G \mid f(z)=0 \}$ 的极限点，并令 $R>0$ 满足 $B(a,R)\subset G$. 由于 $f$ 是连续的，故 $f(a)=0$. 假设存在 $n>0$ 使得 $f(a)=f'(a)=\dots=f^{(n-1)}(a)=0$，但 $f^{(n)}(a)\neq 0$，对 $f$ 做幂级数展开得

$$
\begin{gather}
f(z)=\sum_{k=n}^{\infty} a_{k}(z-a)^{k} 
\end{gather}
$$

其在 $|z-a|<R$ 时收敛。定义

$$
\begin{gather}
g(z)=\sum_{k=n}^{\infty} a_{k}(z-a)^{k-n}
\end{gather}
$$

则 $g$ 在 $B(a,R)$ 上解析，$f(z)=(z-a)^{n}g(z)$，且 $g(a)=a_{n}\neq 0$. 由于 $g$ 在 $B(a,R)$ 上连续，故存在 $0<r<R$ 使得当 $|z-a|<r$ 时 $g(z)\neq 0$. 但由于 $a$ 是 $Z$ 的极限点，故存在 $b$ 使得 $f(b)=0$ 且 $|b-a|<r$，于是 $(b-a)^{n}g(b)=0$，即 $g(b)=0$，矛盾。这就证明了 2.

下设命题 2 成立。令 $A=\{ z \in G \mid f^{(n)}(a)=0,n\geq 0 \}$，根据 2 可知 $A\neq \varnothing$，我们来证明 $A$ 是既开又闭的，从而由连通性知 $A=G$. 为证 $A$ 是闭集，设 $z \in \overline{A}$，并令序列 $(z_{k})\subset A$ 收敛于 $z$. 由于每个 $f^{(n)}$ 均连续，故 $f^{(n)}(z)=\lim_{ k \to \infty }f^{(n)}(z_{k})=0$，因此 $z \in A$，于是 $A$ 是闭集。

为证 $A$ 是开集，设 $a \in A$ 且 $B(a,R)\subset G$. 则在 $|z-a|<R$ 上有幂级数展开 $f(z)=\sum_{n=0}^{\infty}a_{n}(z-a)^{n}$，且 $a_{n}=\dfrac{1}{n!}f^{(n)}(a)=0$，从而 $f(z)=0$ 对所有 $z \in B(a,R)$ 成立，因此 $B(a,R)\subset A$，即证 $A$ 是开集。这就完成了证明。

将上述定理应用到 $f-g$ 上，我们立即得到：

**定理 2.3.8**

如果 $f,g$ 在区域 $G$ 上解析，则 $f=g$ 当且仅当 $\{ z \in G \mid f(z)=g(z) \}$ 在 $G$ 中有一个极限点。

**定理 2.3.9**

如果 $f$ 在区域 $G$ 上解析且 $f$ 不恒等于零，则对任意 $a \in G$ 满足 $f(a)=0$，存在整数 $n\geq 1$ 和解析函数 $g\colon G\to \mathbb{C}$ 使得 $g(a)\neq 0$ 且对任意 $z \in G$ 有 $f(z)=(z-a)^{n}g(z)$. 即，$f$ 的每个零点均具有有限重数。

**证明**

令 $n$ 为使得 $f^{(n-1)}(a)=0$ 的最大整数，并定义 $g(z)=(z-a)^{-n}f(z)$，$z\neq a$，且 $g(a)=\dfrac{1}{n!}f^{(n)}(a)$. 则 $g$ 在 $G\setminus\{ a \}$ 上解析，为证 $g$ 在 $G$ 上解析，我们只需证明 $g$ 在 $a$ 的一个邻域内解析。应用定理 2.3.7 证明中 $3\implies 2$ 的方法即证。

**定理 2.3.10**

如果 $f\colon G\to \mathbb{C}$ 是解析函数且不恒等于零，$a \in G$ 满足 $f(a)=0$，那么存在 $R>0$ 使得 $B(a,R)\subset G$ 且 $f(z)\neq 0$ 对 $0<|z-a|<R$ 成立。

**证明**

根据定理 2.3.7，$f$ 的零点必然是孤立点，否则 $f$ 就恒等于零。

最后，我们给出一种情况，在其中多项式与解析函数的类比是相反的。这就是说，有一种性质只有当我们在解析函数的框架——而非多项式——下才变得明显。

**引理 2.3.11**

设 $G$ 是一个区域，$f\colon G\to \mathbb{C}$ 是解析函数，且 $f[G]$ 是一个圆的子集，那么 $f$ 是常值函数。

**证明**

设 $f[G]$ 是圆 $|z-a|=r$ 的子集，通过取 $g(z)=(f(z)-a) /r$，我们可以不失一般性地假设 $f[G]$ 是圆 $|z|=1$ 的子集。我们证明的思路是通过 Mobius 变换将圆映射到实轴，然后使用“实值解析函数为常值函数”的结论进行证明。

考虑 Mobius 变换

$$
\begin{gather}
T(z)=i \dfrac{1-z}{1+z}
\end{gather}
$$

其在 $\mathbb{C}\setminus \{ -1 \}$ 上解析，并且将单位圆周 $S^{1}\setminus\{ -1 \}$ 映射到实轴 $\mathbb{R}$. 定义 $h(z)=T(f(z))$，如果 $-1 \not\in f[G]$，那么 $h$ 在 $G$ 上解析，从而 $h=u+i 0$ 是实值解析函数。根据 Cauchy-Riemann 方程即证 $h=u$ 为常值函数。由于 $T$ 是双射，故 $f$ 也是常值函数。

如果 $-1 \in f[G]$，那么根据定理 2.3.8，或者 $f=-1$ 为常值函数，或者 $\{ z \in G \mid f(z)=-1 \}$ 均为孤立点。对于后一种情况，将 $f(z)=-1$ 的点去除得到的集合 $G'$ 仍然是连通开集。在 $G'$ 上定义 $h(z)=T(f(z))$，则根据前文，$h$ 是常值函数，从而 $f$ 在 $G'$ 上是常值函数。根据 $f$ 的连续性，必然有 $f(z)=-1$ 对任意 $z \in G$ 成立，这就完成了证明。

**定理 2.3.12** 最大模定理（Maximum Modulus Theorem）

设 $G$ 是一个区域，$f\colon G\to \mathbb{C}$ 是解析函数，满足存在 $a \in G$ 使得对任意 $z \in G$ 有 $|f(z)|\leq |f(a)|$，则 $f$ 是常值函数。

**证明**

令 $\overline{B(a,r)}\subset G$，$\gamma(t)=a+re^{it},0\leq t\leq 2\pi$. 根据定理 2.2.2，我们有

$$
\begin{align}
f(a)= \dfrac{1}{2\pi i}\int_{\gamma} \dfrac{f(w)}{w-a} \mathrm{d} w=\dfrac{1}{2\pi} \int_{0}^{2\pi} f(a+re^{it}) \mathrm{d} t
\end{align}
$$

于是

$$
\begin{align}
|f(a)|\leq \dfrac{1}{2\pi} \int_{0}^{2\pi} |f(a+re^{it})| \mathrm{d} t\leq |f(a)|
\end{align}
$$

这表明

$$
\begin{gather}
\int_{0}^{2\pi} (|f(a)|-|f(a+re^{it})|) \mathrm{d} t=0
\end{gather}
$$

又由于 $|f(a)|-|f(a+re^{it})|\geq 0$，故对任意 $t$ 有 $|f(a)|=|f(a+re^{it})|$. 此外，根据 $r$ 的任意性，可知 $f$ 将任意圆盘 $B(a,R)$ 映射到圆 $|z|=|f(a)|$ 上。根据引理 2.3.11，这表明 $f$ 在 $B(a,R)$ 上是常值函数，再根据定理 2.3.8 知 $f(z)=f(a)$ 在 $G$ 上成立，这就完成了证明。

根据最大模定理，区域上的非常值解析函数不可能达到它的最大模长。这一结论即使对于多项式来说也并非显而易见。同时，这一定理的推论也影响深远，我们将在后续的章节进行讨论。