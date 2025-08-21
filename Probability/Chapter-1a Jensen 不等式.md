在证明 Jensen 不等式前，我们要对凸函数的性质有充分的了解。首先我们给出几个引理：

**引理 1**

函数 $F\colon \mathbb{R}\to \mathbb{R}$ 是凸函数当且仅当对任意满足 $a<b<c$ 的 $a,b,c \in \mathbb{R}$ 有

$$
\dfrac{F(b)-F(a)}{b-a}\leq \dfrac{F(c)-F(b)}{c-b}
$$

**证明**

设 $F$ 是凸函数，$b=\lambda a+(1-\lambda)c,\lambda=\dfrac{c-b}{c-a}\in(0,1)$，则有

$$
F(b)\leq \lambda F(a)+(1-\lambda)F(c)= \dfrac{(c-b)F(a)+(b-a)F(c)}{c-a}
$$

即

$$
(c-b)F(b)+(b-a)F(b)\leq(c-b)F(a)+(b-a)F(c)
$$

即证。反之，任取 $b=\lambda a+(1-\lambda)c,\lambda \in(0,1)$，则有 $a<b<c$，并且满足 $F(b)\leq\lambda F(a)+(1-\lambda)F(c)$，故 $F$ 是凸函数。

**引理 2**

函数 $F\colon \mathbb{R}\to \mathbb{R}$ 是凸函数当且仅当 $F$ 在任意紧致区间 $[a,b]$ 上绝对连续，并且 $F'$ 在其定义域上递增。

**证明**

设 $F$ 是凸函数，$x<y<z$，则根据引理 1 有

$$
\begin{align}
(z-x)F(y)&\leq (z-y)F(x)+(y-x)F(z) \\
&=(z-x)F(x)+(y-x)(F(z)-F(x))
\end{align}
$$

即 $\dfrac{F(y)-F(x)}{y-x}\leq \dfrac{F(z)-F(x)}{z-x}$，同样地，对于 $t<s<x$，我们有 $\dfrac{F(t)-F(x)}{t-x}\leq \dfrac{F(s)-F(x)}{s-x}$，令 $y\to x+,s\to x-$，则 $F$ 在 $x$ 处存在有限的左右导数 $F_{-}'(x)$ 和 $F_{+}'(x)$. 此外，对于 $x<y$ 我们有

$$
F_{-}'(x)\leq F_{+}'(x)\leq F_{-}'(y)\leq F_{+}'(y)
$$

任取 $a<b$，对任意 $x,y \in[a,b]$，我们有

$$
|F(y)-F(x)|=\left\lvert  \dfrac{F(y)-F(x)}{y-x}  \right\rvert |y-x|\leq L|y-x|
$$

其中 $L=\max(|F_{+}'(a)|,|F_{-}'(b)|)$，因此对任意 $\varepsilon>0$，取 $\delta= \dfrac{\varepsilon}{L}$，则对任意不相交的区间 $(a_{1},b_{1}),\dots,(a_{n},b_{n})\subset[a,b]$ 有

$$
\sum_{j=1}^{n} (b_{j}-a_{j})<\delta \implies \sum_{j=1}^{n} |F(b_{j})-F(a_{j})|< L\delta=\varepsilon
$$

因此 $F$ 在 $[a,b]$ 上绝对连续，并且 $F'$ 在有定义的集合上递增。

反之，设 $a<b<c$，则根据微积分基本定理，存在 $f \in L^{1}([a,c],m)$ 使得

$$
F(x)=F(a)+\int_{a}^{x}f(t)\mathrm{d} t, x \in [a,c]
$$

并且 $f=F'$ a.e. 在 $[a,c]$ 上递增，因此

$$
\dfrac{F(b)-F(a)}{b-a}=\dfrac{1}{b-a}\int_{a}^{b}f(t)\mathrm{d} t\leq f(b)\leq \dfrac{1}{c-b}\int_{b}^{c}f(t)\mathrm{d} t= \dfrac{F(c)-F(b)}{c-b}
$$

根据引理 1 知 $F$ 是凸函数。

**引理 3**

如果 $F\colon \mathbb{R}\to \mathbb{R}$ 是凸函数，$t_{0}\in \mathbb{R}$，那么存在 $\beta \in \mathbb{R}$ 使得对任意 $t \in \mathbb{R}$ 有

$$
F(t)-F(t_{0})\geq \beta(t-t_{0})
$$

**证明**

取 $\beta=F_{+}'(t_{0})$，我们来证明上述不等式。设 $t>t_{0}$，由于 $F$ 在 $[t_{0},t]$ 上绝对连续，并且 $F'$ a.e. 存在且递增，故

$$
F(t)-F(t_{0})=\int_{t_{0}}^{t} F'(u)\mathrm{d} u\geq F_{+}'(t_{0})(t-t_{0})
$$

再设 $t<t_{0}$，则同样有

$$
F(t_{0})-F(t)=\int_{t}^{t_{0}} F'(u)\mathrm{d} u\leq F_{-}'(t_{0})(t_{0}-t)\leq F_{+}'(t_{0})(t_{0}-t)
$$

因此 $\beta \in \mathbb{R}$ 满足条件。

现在我们给出 Jensen 不等式的证明。

**定理 4** Jensen 不等式

设 $(X,\mathcal{M},\mu)$ 是一个测度空间，满足 $\mu(X)=1$，且函数 $g\colon X\to \mathbb{R}$ 是可积的，$F\colon \mathbb{R}\to \mathbb{R}$ 是凸函数，那么有

$$
F\left( \int g\mathrm{d} \mu \right)\leq \int F\circ g \mathrm{d} \mu
$$

**证明**

令 $t_{0}=\int g\mathrm{d}\mu,t=g(x)$，则根据引理 3 知存在 $\beta \in \mathbb{R}$ 使得

$$
F(g(x))-F\left( \int g\mathrm{d} \mu \right)\geq\beta\left( g(x)-\int g\mathrm{d} \mu \right)
$$

对 $x$ 关于 $\mu$ 积分，则有

$$
\int F\circ g\mathrm{d} \mu-\mu(X)F\left( \int g\mathrm{d} \mu \right)\geq \beta\left( \int g\mathrm{d} \mu-\mu(X)\int g\mathrm{d} \mu \right)=0
$$

这就完成了证明。

根据上面的证明过程可见，只有当 $\mu(X)=1$，即这是一个概率空间时，Jensen 不等式才成立。