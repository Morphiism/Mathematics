现在我们转到另一个主题，即多元函数的微分学。更准确地说，是对两个 Euclidean 空间 $\mathbb{R}^{n},\mathbb{R}^{m}$ 之间的向量函数的微分学，并试着去理解这个函数的导数是什么。

在此之前，我们需要对 $\mathbb{R}^{n}$ 上的向量空间结构有一定了解，对这方面的研究可以参考任意一本线性代数教材，这里我们只介绍一些之后将会用到的符号和概念。

# Section 1: 线性映射

对于一个 $x \in \mathbb{R}^{n}$，我们通常把它写成

$$
x=(x_{1},\dots,x_{n}),x_{j}\in \mathbb{R}
$$

称为 $n$ 维**行向量**，这就是说，当我们用矩阵 $A$ 去乘 $x$ 时，要将 $x$ 转置为**列向量** $x^{T}$.

在不加特殊说明的情况下，$\mathbb{R}^{n}$ 的基总是取为标准基：

$$
(x_{1},\dots,x_{n})=x_{1}e_{1}+\dots+x_{n}e_{n}
$$

一个 $\mathbb{R}^{n}\to \mathbb{R}^{m}$ 的线性映射通常是由矩阵 $A$ 给出的，这时候我们就可以定义线性映射 $L_{A}\colon \mathbb{R}^{n}\to \mathbb{R}^{m}$ 为

$$
(L_{A}x)^{T}=Ax^{T}
$$

同样，一个线性映射也唯一地给出了一个矩阵表示（在取定某个基后）。

$\mathbb{R}^{n}$ 上的内积通常取为 Euclidean 内积：

$$
\langle x,y \rangle = x\cdot y =x_{1}y_{1}+\dots+x_{n}y_{n}
$$

其范数定义为

$$
\lVert x \rVert = \sqrt{ \langle x,x \rangle  } =(x_{1}^{2}+\dots+x_{n}^{2})^{1/2}
$$

从而有 $d_{l^{2}}(x,y)=\lVert x-y \rVert$.

最后，我们给出一个定理：

**定理 19.1.1**

设 $L\colon \mathbb{R}^{n}\to \mathbb{R}^{m}$ 是线性映射，则 $L$ 在 $\mathbb{R}^{n}$ 上连续。

**证明**

取矩阵 $A$ 作为 $L$ 的表示，设 $M$ 为 $A$ 的所有元素的绝对值之和，则根据 Cauchy-Schwarz 不等式有

$$
\begin{align}
\lVert Lx \rVert &= \left( \sum_{i=1}^{m} \left( \sum_{j=1}^{n} A_{ij}x_{j} \right)^{2} \right)^{1/2} \\
&= \left( \sum_{i=1}^{m} \langle A_{i, .}, x \rangle^{2}  \right)^{1/2} \\
&\leq \left( \sum_{i=1}^{m}  \lVert A_{i, .} \rVert^{2} \lVert x \rVert ^{2} \right)^{1/2} \\
&= \lVert x \rVert \left( \sum_{i=1}^{m} \sum_{j=1}^{n} A_{ij}^{2}  \right)^{1/2} \\
&\leq M \lVert x \rVert 
\end{align}
$$

设 $x_{0}\in \mathbb{R}^{n}$，则对任意 $\varepsilon>0$，取 $0<\delta< \dfrac{\varepsilon}{M}$，则对任意 $x \in B(x_{0},\delta)$ 有

$$
\lVert Lx-Lx_{0} \rVert \leq M \lVert x-x_{0} \rVert < M\cdot \dfrac{\varepsilon}{M}=\varepsilon
$$

这就完成了证明。

# Section 2: 全导数与方向导数

在一元微分学中，导数被定义为

$$
f'(x_{0})=\lim_{ x \to x_{0};x \in X } \dfrac{f(x)-f(x_{0})}{x-x_{0}}
$$

然而，到多元微分学，情况就不同了：$f(x)-f(x_{0})$ 是 $\mathbb{R}^{m}$ 中的向量，而 $x-x_{0}$ 是 $\mathbb{R}^{n}$ 中的向量，它们的除法是无定义的。幸运的是，我们有一种方法可以改写这个定义，即 Newton 近似：

$$
|f(x)-(f(x_{0})+L(x-x_{0}))|\leq \varepsilon |x-x_{0}|, x \in(x_{0}-\delta,x_{0}+\delta)
$$

或者说

$$
\lim_{ x \to x_{0};x \in X } \dfrac{|f(x)-(f(x_{0})+L(x-x_{0}))|}{|x-x_{0}|}=0
$$

把其中的绝对值替换为范数，就可以避免向量的除法，但此时 $L$ 也不再是一个实数（标量），而是一个 $\mathbb{R}^{n}\to \mathbb{R}^{m}$ 的函数。根据导数的“近似线性”性质，我们期望 $L$ 是一个线性映射，从而我们有近似式

$$
f(x)\approx f(x_{0})+L(x-x_{0})
$$

由此，我们给出以下定义：

**定义 19.2.1** 可微（differentiable）

设 $E\subset \mathbb{R}^{n}$，函数 $f\colon E\to \mathbb{R}^{m}$，$x_{0}\in E$ 是极限点，并且 $L\colon \mathbb{R}^{n}\to \mathbb{R}^{m}$ 是一个线性映射，如果

$$
\lim_{ x \to x_{0};x \in E } \dfrac{\lVert f(x)-(f(x_{0})+L(x-x_{0})) \rVert }{\lVert x-x_{0} \rVert }=0
$$

则称 $f$ 在 $x_{0}$ 处**可微**，其**导数**为 $L$.

现在，我们来证明导数是唯一的，从而我们可以定义符号 $f'(x_{0})$.

**定理 19.2.2**

设 $E\subset \mathbb{R}^{n}$，函数 $f\colon E\to \mathbb{R}^{m}$，$x_{0}\in \mathrm{Int}(E)$ 是极限点，如果 $f$ 在 $x_{0}$ 处可微，并且导数为 $L_{1},L_{2}$，那么 $L_{1}=L_{2}$.

**证明**

假设 $L_{1}\neq L_{2}$，那么存在 $v \in \mathbb{R}^{n},v\neq 0$ 使得 $L_{1}v\neq L_{2}v$，设 $t \in \mathbb{R}$，由于 $x_{0}$ 是内点，故当 $t\to 0$ 时有 $x_{0}+tv \in E$，从而

$$
\lim_{ t \to 0 } \dfrac{\lVert f(x_{0}+tv)-f(x_{0})-L_{1}(tv) \rVert }{\lVert tv \rVert }=0
$$

于是对任意 $\varepsilon>0$，存在 $\delta>0$ 使得对任意 $0<|t|<\delta$ 有

$$
\dfrac{\lVert f(x_{0}+tv)-f(x_{0})-L_{1}(tv) \rVert }{\lVert tv \rVert }<\varepsilon
$$

对 $L_{2}$ 同理，从而有

$$
\begin{align}
& \dfrac{\lVert L_{1}(tv)-L_{2}(tv) \rVert }{\lVert tv \rVert } \\
&\leq \dfrac{\lVert f(x_{0}+tv)-f(x_{0})-L_{1}(tv) \rVert }{\lVert tv \rVert }+\dfrac{\lVert f(x_{0}+tv)-f(x_{0})-L_{2}(tv) \rVert }{\lVert tv \rVert } \\
&< 2\varepsilon
\end{align}
$$

取 $\varepsilon= \dfrac{\lVert L_{1}v-L_{2}v \rVert}{2\lVert v \rVert}>0$，则产生矛盾，故 $L_{1}=L_{2}$.

根据这个定理，我们可以得到推论：线性映射 $L$ 在任意一点的导数为 $L$ 自身。

现在，我们就可以为 $E$ 的内点处的导数定义一个符号，记作 $f'$ 或 $Df$，为了与后续的**偏导数**做区分，这里的导数通常被称为**全导数**。这里我们不考虑边界点上的导数，而只在定义域的内部计算导数。

下面，我们将介绍方向导数的概念，并把它和可微性联系起来。

**定义 19.2.3** 方向导数（directional derivative）

设 $E\subset \mathbb{R}^{n}$，函数 $f\colon E\to \mathbb{R}^{m}$，$x_{0}\in E$ 是极限点，$v \in \mathbb{R}^{n},v\neq 0$，如果极限

$$
\lim_{ t \to 0;t>0,x_{0}+tv \in E } \dfrac{f(x_{0}+tv)-f(x_{0})}{t}
$$

存在，则称 $f$ 在 $x_{0}$ 处**沿方向** $v$ **可微**，并把上述极限记作 $D_{v}f(x_{0})$.

在实数上，我们一共有两个本质上不同的方向：$+1$ 和 $-1$，并且我们有 $D_{+1}f(x_{0})$ 是 $f$ 在 $x_{0}$ 处的**右导数**，$D_{-1}f(x_{0})$ 是 $f$ 在 $x_{0}$ 处的**左导数**。因此，方向导数是左右导数的推广。

当 $x_{0}$ 是 $E$ 的边界点时，对于某些方向 $v$，有 $x_{0}+tv \not\in E$，这时候极限是无定义的，我们也称 $f$ 在 $x_{0}$ 处沿着方向 $v$ 不可微。

方向导数和全导数有如下关系：

**定理 19.2.4**

设 $E\subset \mathbb{R}^{n}$，函数 $f\colon E\to \mathbb{R}^{m}$，$x_{0}\in \mathrm{Int}(E)$ 是极限点，并且 $v \in \mathbb{R}^{n},v\neq 0$，如果 $f$ 在 $x_{0}$ 处可微，那么 $f$ 在 $x_{0}$ 处沿着方向 $v$ 也可微，并且

$$
D_{v}f(x_{0})=f'(x_{0})v
$$

**证明**

由于 $x \in \mathrm{Int}(E)$，故当 $t\to 0$ 时有 $x_{0}+tv \in E$，从而

$$
\lim_{ t \to 0;t>0 } \dfrac{\lVert f(x_{0}+tv)-f(x_{0})-f'(x_{0})(tv) \rVert }{\lVert tv \rVert }=0
$$

即

$$
\lim_{ t \to 0;t>0 } \left\lVert  \dfrac{f(x_{0}+tv)-f(x_{0})}{t}-f'(x_{0})v  \right\rVert =0
$$

从而有 $D_{v}f(x_{0})=f'(x_{0})v$.

由上述定理我们知道，可微性蕴含了方向可微性，但反之不成立。

与方向导数密切相关的是**偏导数**的概念，实际上就是沿着标准基方向的方向导数。

**定义 19.2.5** 偏导数（partial derivative）

设 $E\subset \mathbb{R}^{n}$，函数 $f\colon E\to \mathbb{R}^{m}$，$x_{0}\in E$ 是极限点，整数 $1\leq j\leq n$，如果极限

$$
\lim_{ t \to 0; x_{0}+te_{j}\in E } \dfrac{f(x_{0}+te_{j})-f(x_{0})}{t}
$$

存在，则称 $f$ 在 $x_{0}$ 处关于变量 $x_{j}$ 的**偏导数**存在，记作 $\dfrac{ \partial f }{ \partial x_{j} }(x_{0})$.

注意，偏导数和方向导数有细微的差别：偏导数要求 $t>0$ 和 $t<0$ 的极限都存在，但方向导数只要求 $t>0$ 的极限存在即可。

简单来说，要求一个函数的偏导数，我们只需要将除了 $x_{j}$ 以外的变量看成常数，然后求单变量函数 $f(x_{j})$ 的导数即可。如果 $f$ 的陪域是 $\mathbb{R}^{m}$，我们可以把它写成 $f=(f_{1},\dots,f_{m})$，那么我们有

$$
\dfrac{ \partial f }{ \partial x_{j} } (x_{0})=\left( \dfrac{ \partial f_{1} }{ \partial x_{j} } (x_{0}),\dots,\dfrac{ \partial f_{m} }{ \partial x_{j} } (x_{0}) \right)
$$

当然，其中的每个偏导数都要存在。也就是说，要对一个向量值函数求偏导数，只需分别对每个分量求偏导数即可。

根据定理 19.2.4，如果 $f$ 在 $x_{0}$ 处可微，那么有

$$
\dfrac{ \partial f }{ \partial x_{j} } (x_{0})=D_{e_{j}}f(x_{0})=f'(x_{0})e_{j}
$$

对于任意 $v \in \mathbb{R}^{n},v\neq 0$，我们可以将其分解为 $v=v_{1}e_{1}+\dots+v_{n}e_{n}$，从而

$$
D_{v}f(x_{0})=f'(x_{0})v=\sum_{j=1}^{n} v_{j} f'(x_{0})e_{j}=\sum_{j=1}^{n} v_{j} \dfrac{ \partial f }{ \partial x_{j} } (x_{0})
$$

即可以用偏导数表示方向导数。

前面我们提到，可微性蕴含了方向可微性（也蕴含了偏导数存在性），但反之不然。然而，我们可以证明，如果偏导数不仅存在，而且连续，那么函数在 $x_{0}$ 处就是可微的。

**定理 19.2.6**

设 $E\subset \mathbb{R}^{n}$，函数 $f\colon E\to \mathbb{R}^{m}$，$F\subset E$，$x_{0}\in \mathrm{Int}(F)$ 是 $F$ 的极限点，如果 $f$ 在 $F$ 上的所有偏导数都存在，并且在 $x_{0}$ 处连续，那么 $f$ 在 $x_{0}$ 处可微，而且有

$$
f'(x_{0})(v_{1},\dots,v_{n})=\sum_{j=1}^{n} v_{j}\dfrac{ \partial f }{ \partial x_{j} } (x_{0})
$$

**证明**

定义线性映射 $L\colon \mathbb{R}^{n}\to \mathbb{R}^{m}$ 为

$$
L(v_{1},\dots,v_{n})=\sum_{j=1}^{n} v_{j}\dfrac{ \partial f }{ \partial x_{j} } (x_{0})
$$

我们要证对任意 $\varepsilon>0$，存在 $\delta$ 使得对任意 $x \in B(x_{0},\delta)$ 有

$$
\lVert f(x)-f(x_{0})-L(x-x_{0}) \rVert \leq\varepsilon \lVert x-x_{0} \rVert 
$$

由于 $x_{0}\in \mathrm{Int}(F)$，故存在 $r>0$ 使得 $B(x_{0},r)\subset F$. 由于 $\dfrac{ \partial f }{ \partial x_{j} }$ 在 $x_{0}$ 处连续，故存在 $0<\delta_{j}<r$ 使得对任意 $x \in B(x_{0},\delta_{j})$ 有

$$
\left\lVert  \dfrac{ \partial f }{ \partial x_{j} } (x)-\dfrac{ \partial f }{ \partial x_{j} } (x_{0})  \right\rVert <\varepsilon
$$

令 $\delta=\min_{1\leq j\leq n} \delta_{j}$，将 $f$ 和 $x$ 写成 $x=x_{0}+v_{1}e_{1}+\dots+v_{n}e_{n}\in B(x_{0},\delta)$ 和 $f=(f_{1},\dots,f_{m})$，对变量 $x_{1}$ 应用中值定理有

$$
f_{i}(x_{0}+v_{1}e_{1})-f_{i}(x_{0})=v_{1} \dfrac{ \partial f_{i} }{ \partial x_{1} } (x_{0}+t_{i}e_{1})
$$

而我们有

$$
\left\lvert  \dfrac{ \partial f_{i} }{ \partial x_{1} } (x_{0}+t_{i}e_{1})-\dfrac{ \partial f_{i} }{ \partial x_{1} } (x_{0})  \right\rvert \leq \left\lVert  \dfrac{ \partial f }{ \partial x_{1} } (x_{0}+t_{i}e_{1})-\dfrac{ \partial f }{ \partial x_{1} } (x_{0})  \right\rVert <\varepsilon
$$

对 $1\leq i\leq m$ 求和，根据三角不等式就有

$$
\left\lVert  f(x_{0}+v_{1}e_{1})-f(x_{0})-v_{1}\dfrac{ \partial f }{ \partial x_{1} } (x_{0})  \right\rVert \leq |v_{1}|m\varepsilon\leq m\varepsilon \lVert x-x_{0} \rVert 
$$

同理，我们有

$$
\left\lVert  f(x_{0}+v_{1}e_{1}+v_{2}e_{2})-f(x_{0}+v_{1}e_{1})-v_{2}\dfrac{ \partial f }{ \partial x_{2} } (x_{0})  \right\rVert \leq m\varepsilon \lVert x-x_{0} \rVert 
$$

以此类推，最后我们有

$$
\begin{align}
&\left\lVert  f(x_{0}+v_{1}e_{1}+\dots+v_{n}e_{n})-f(x_{0}+v_{1}e_{1}+\dots+v_{n-1}e_{n-1})-v_{n}\dfrac{ \partial f }{ \partial x_{n} } (x_{0})  \right\rVert  \\
&\leq m\varepsilon \lVert x-x_{0} \rVert 
\end{align}
$$

将这 $n$ 个不等式相加，根据三角不等式有

$$
\left\lVert  f(x_{0}+v_{1}e_{1}+\dots+v_{n}e_{n})-f(x_{0})-\sum_{j=1}^{n} v_{j}\dfrac{ \partial f }{ \partial x_{j} } (x_{0})  \right\rVert \leq mn\varepsilon \lVert x-x_{0} \rVert 
$$

这就完成了证明。

可见，如果 $f\colon E\to \mathbb{R}^{m}$ 在 $F\subset E$ 的内点上存在连续偏导数，那么 $f$ 在 $F$ 上可微，并且有公式

$$
D_{v}f(x_{0})=f'(x_{0})v=\sum_{j=1}^{n} v_{j}\dfrac{ \partial f }{ \partial x_{j} } (x_{0})
$$

特别地，如果 $f\colon E\to \mathbb{R}$ 是一个实值函数，其在 $x_{0}$ 处的**梯度**定义为

$$
\nabla f(x_{0})=\left( \dfrac{ \partial f }{ \partial x_{1} } (x_{0}),\dots,\dfrac{ \partial f }{ \partial x_{n} } (x_{0}) \right)
$$

那么我们就有熟知的公式

$$
D_{v}f(x_{0})=v\cdot \nabla f(x_{0})
$$

更一般地，设 $f=(f_{1},\dots,f_{m})$，那么我们有

$$
f'(x_{0})(v_{1},\dots,v_{n})=\left( \sum_{j=1}^{n} v_{j}\dfrac{ \partial f_{i} }{ \partial x_{j} } (x_{0}) \right)_{1\leq i\leq m}
$$

于是我们可以写出 $f'(x_{0})$ 的矩阵表示

$$
J_{f}(x_{0})=\left( \dfrac{ \partial f_{i} }{ \partial x_{j} } (x_{0}) \right)_{1\leq i\leq m,1\leq j\leq n}
$$

称为 $f$ 在 $x_{0}$ 处的 **Jacobian 矩阵**，有时记作 $\dfrac{\partial(f_{1},\dots,f_{m})}{\partial(x_{1},\dots,x_{n})}$，它可以写成

$$
J_{f}(x_{0})=\left( \dfrac{ \partial f }{ \partial x_{1} } (x_{0})^{T},\dots,\dfrac{ \partial f }{ \partial x_{n} } (x_{0})^{T} \right)=\begin{pmatrix}
\nabla f_{1}(x_{0}) \\
\vdots \\
\nabla f_{m}(x_{0})
\end{pmatrix}
$$

因此，实值函数的 Jacobian 矩阵就是 $\nabla f(x_{0})$.

下面，我们给出一个应用。

**定理 19.2.7**

设 $f\colon \mathbb{R}^{n}\to \mathbb{R}^{m}$ 是可微的，并且对任意 $x \in \mathbb{R}^{n}$ 有 $f'(x)=0$，那么 $f$ 是一个常值函数。

**证明**

设 $x_{0}\in \mathbb{R}^{n}$，对任意 $v_{j}\in \mathbb{R}$，根据中值定理有

$$
f_{i}(x_{0}+v_{j}e_{j})-f_{i}(x_{0})=v_{j} \dfrac{ \partial f_{i} }{ \partial x_{j} } (x_{0}+t_{j}e_{j})=0
$$

从而对任意 $x \in \mathbb{R}^{n}$ 有 $f_{i}(x+v_{j}e_{j})=f_{i}(x)$.

设 $x,y \in \mathbb{R}^{n}$，则有 $y=x+v_{1}e_{1}+\dots+v_{n}e_{n}$，于是

$$
f_{i}(y)=f_{i}(x+v_{1}e_{1}+\dots+v_{n-1}e_{n-1})=\dots=f_{i}(x+v_{1}e_{1})=f_{i}(x)
$$

从而 $f(y)=f(x)$，这表明 $f$ 是一个常值函数。

# Section 3: 链式法则

现在我们叙述多元微积分的链式法则，它的证明过程与一元微积分的链式法则非常相似。

**定理 19.3.1** 链式法则（chain rule）

设 $E\subset \mathbb{R}^{n},F\subset \mathbb{R}^{m}$，函数 $f\colon E\to F,g\colon F\to \mathbb{R}^{p}$，设 $f$ 在 $x_{0}\in \mathrm{Int}(E)$ 处可微，$g$ 在 $f(x_{0})\in \mathrm{Int}(F)$ 处可微，那么 $g\circ f$ 在 $x_{0}$ 处可微，并且

$$
(g\circ f)'(x_{0})=g'(f(x_{0}))f'(x_{0})
$$

**证明**

记 $f'(x_{0})=L_{1},g'(f(x_{0}))=L_{2}$，根据定理 19.1.1 的证明，存在 $M>0$ 使得对任意 $x$ 有

$$
\lVert L_{1}x \rVert \leq M\lVert x \rVert ,\lVert L_{2}x \rVert \leq M\lVert x \rVert 
$$

任取 $\varepsilon>0$，存在 $\delta>0$ 使得对任意 $y \in B(f(x_{0}),\delta)$ 有

$$
\lVert g(y)-g(f(x_{0}))-L_{2}(y-f(x_{0})) \rVert \leq\varepsilon \lVert y-f(x_{0}) \rVert 
$$

对于这个 $\delta$，存在 $\eta>0$ 使得对任意 $x \in B(x_{0},\eta)$ 有

$$
\lVert f(x)-f(x_{0})-L_{1}(x-x_{0}) \rVert \leq\varepsilon \lVert x-x_{0} \rVert , \lVert f(x)-f(x_{0}) \rVert <\delta
$$

并且

$$
\begin{align}
& \lVert g(y)-g(f(x_{0}))-L_{2}L_{1}(x-x_{0}) \rVert  \\
&= \lVert g(y)-g(f(x_{0}))-L_{2}(y-f(x_{0}))+L_{2}(y-f(x_{0})-L_{1}(x-x_{0})) \rVert  \\
&\leq \lVert g(y)-g(f(x_{0}))-L_{2}(y-f(x_{0})) \rVert +\lVert L_{2}(y-f(x_{0})-L_{1}(x-x_{0})) \rVert 
\end{align}
$$

从而

$$
\begin{align}
& \lVert g(f(x))-g(f(x_{0}))-L_{2}L_{1}(x-x_{0}) \rVert  \\
&\leq \varepsilon \lVert f(x)-f(x_{0}) \rVert + M \lVert f(x)-f(x_{0})-L_{1}(x-x_{0}) \rVert  \\
&\leq \varepsilon(M+\varepsilon)\lVert x-x_{0} \rVert +M\varepsilon \lVert x-x_{0} \rVert  \\
&= (\varepsilon^{2}+2M\varepsilon)\lVert x-x_{0} \rVert 
\end{align}
$$

令 $\varepsilon<1$，则 $\varepsilon^{2}<\varepsilon$，从而有 $(g\circ f)'(x_{0})=L_{2}L_{1}$，这就完成了证明。

作为链式法则的应用，我们给出下面的例子。

设 $f\colon \mathbb{R}^{n}\to \mathbb{R},g\colon \mathbb{R}^{n}\to \mathbb{R}$ 在 $x_{0}$ 处可微，令 $k\colon \mathbb{R}^{2}\to \mathbb{R}$ 表示乘法函数：$k(a,b)=ab$，我们知道，函数 $fg$ 是 $f,g$ 的直和 $f \oplus g$ 与 $k$ 的复合，因此，我们有

$$
\begin{align}
J_{fg}(x_{0}) &= J_{k}(f(x_{0}),g(x_{0}))J_{f\oplus g}(x_{0}) \\
&= (g(x_{0}),f(x_{0})) \begin{pmatrix}
\nabla f(x_{0}) \\
\nabla g(x_{0})
\end{pmatrix} \\
&= g\nabla f(x_{0})+f\nabla g(x_{0})
\end{align}
$$

于是我们就得到了乘积法则：$\nabla(fg)=g\nabla f+f\nabla g$，类似地，还有加法法则 $\nabla(f+g)=\nabla f+\nabla g$，以及商法则

$$
\nabla\left( \dfrac{f}{g} \right)=\dfrac{g\nabla f-f\nabla g}{g^{2}}
$$

再设 $L\colon \mathbb{R}^{n}\to \mathbb{R}^{m}$ 是线性映射，我们知道，$L$ 的全导数是其自身，即 $L'(x)=L$，因此对于可微函数 $f\colon E\to \mathbb{R}^{n}$ 有

$$
(Lf)'(x_{0})=Lf'(x_{0})
$$

这是一元微积分中 $(cf)'=cf'$ 的推广。

最后，我们再给出一种非常有用的特殊情形：设 $f\colon \mathbb{R}^{n}\to \mathbb{R}^{m}$ 是可微的，并且对于整数 $1\leq j\leq n$，函数 $x_{j}\colon \mathbb{R}\to \mathbb{R}$ 是可微的，那么有

$$
\dfrac{\mathrm{d} }{\mathrm{d} t}f(x_{1}(t),\dots,x_{n}(t))=\sum_{j=1}^{n} x_{j}'(t) \dfrac{ \partial f }{ \partial x_{j} } (x_{1}(t),\dots,x_{n}(t))
$$

为了看出这一点，我们注意到函数 $f(x_{1}(t),\dots,x_{n}(t))$ 是函数 $f$ 和函数 $x_{1}\oplus \dots \oplus x_{n}$ 的复合，那么有

$$
\begin{align}
\dfrac{\mathrm{d} }{\mathrm{d} t}f(x_{1}(t),\dots,x_{n}(t))^{T} &= J_{f}(x_{1}(t),\dots,x_{n}(t)) J_{x_{1}\oplus \dots \oplus x_{n}}(t) \\
&= \left( \dfrac{ \partial f }{ \partial x_{1} } (x)^{T},\dots,\dfrac{ \partial f }{ \partial x_{n} }(x)^{T}  \right)\begin{pmatrix}
x_{1}'(t) \\
\vdots \\
x_{n}'(t)
\end{pmatrix} \\
&= \sum_{j=1}^{n} x_{j}'(t) \dfrac{ \partial f }{ \partial x_{j} } (x_{1}(t),\dots,x_{n}(t))^{T}
\end{align}
$$

可见，利用 Jacobian 矩阵，我们可以快速的计算出一个函数在某处的全导数。

我们再给出链式法则的一个应用，它推广了一元函数上的中值定理。

**定理 19.3.2** 中值定理（mean value theorem）

设 $E\subset \mathbb{R}^{n}$ 是开集，函数 $f\colon E\to \mathbb{R}$ 是可微的，设 $x_{0}\in E,v \in \mathbb{R}^{n},v\neq 0$，如果 $\{ x_{0}+tv \mid 0\leq t\leq 1 \}\subset E$，那么存在 $0<t_{0}<1$ 使得

$$
f(x_{0}+v)-f(x_{0})=f'(x_{0}+t_{0}v) v
$$

**证明**

定义 $\phi\colon [0,1]\to \mathbb{R}$ 为

$$
\phi(t)=f(x_{0}+tv)-f(x_{0})
$$

则 $\phi$ 在 $[0,1]$ 上可微，从而由一元函数中值定理得

$$
f(x_{0}+v)-f(x_{0})=\phi(1)-\phi(0)=\phi'(t_{0})=f'(x_{0}+t_{0}v) v
$$

这就完成了证明。

注意，上述定理与连续使用 $f_{i}$ 上的中值定理不同：前者的中值点 $x_{0}+t_{0}v$ 是相同的，而后者每个分量上的中值点 $x_{0}+t_{i}v$ 可能不同。

# Section 4: Clairaut 定理

现在我们考虑对一个函数进行多次微分会发生什么。

**定义 19.4.1** 连续可微（continuously differentiable）

设 $E\subset \mathbb{R}^{n}$ 是开集，函数 $f\colon E\to \mathbb{R}^{m}$，如果每个偏导数 $\dfrac{ \partial f }{ \partial x_{j} }$ 在 $E$ 上存在且连续，则称 $f$ 是**连续可微的**。如果进一步有偏导数自身也是连续可微的，则称 $f$ 是**二次连续可微的**。

我们把连续函数称为 $C^{0}$ 函数，连续可微函数称为 $C^{1}$ 函数，二次连续可微函数称为 $C^{2}$ 函数，类似地可以定义 $C^{3},C^{4},\dots$ 函数。光滑函数称为 $C^{\infty}$ 函数。

在 $C$ 类之外，我们还有 $D$ 类：我们把 $k$ 次可微的函数称为 $D^{k}$ 函数，光滑函数也称为 $D^{\infty}$ 函数。由于可微性蕴含连续性，故条件 $D^{k}$ 弱于 $C^{k}$，但强于 $C^{k-1}$，从而我们有蕴含链：

$$
C^{0}\impliedby D^{1}\impliedby C^{1} \impliedby D^{2} \impliedby C^{2}\impliedby \cdots \impliedby D^{\infty} \iff C^{\infty}
$$

当我们对一个函数求多次偏导数时，有时会遇到一个问题：求导的顺序。以函数 $(x,y)\mapsto \dfrac{xy^{3}}{x^{2}+y^{2}}$ 为例，如果我们先对 $x$ 求导，就有

$$
\dfrac{ \partial f }{ \partial x } (x,y)= \dfrac{y^{3}(y^{2}-x^{2})}{(x^{2}+y^{2})^{2}}
$$

于是 $\dfrac{ \partial f }{ \partial x }(0,y)=y$，故 $\dfrac{ \partial  }{ \partial y }\dfrac{ \partial f }{ \partial x }(0,0)=1$. 然而，如果我们先对 $y$ 求导，就有

$$
\dfrac{ \partial f }{ \partial y } (x,y)= \dfrac{x(3x^{2}y^{2}+y^{4})}{(x^{2}+y^{2})^{2}}
$$

于是 $\dfrac{ \partial f }{ \partial y }(x,0)=0$，从而 $\dfrac{ \partial  }{ \partial x }\dfrac{ \partial f }{ \partial y }(0,0)=0$，因此求导的顺序会影响最终的结果。

因此对于一个函数 $f$，我们没有理由相信偏导数 $\dfrac{ \partial  }{ \partial y } \dfrac{ \partial f }{ \partial x }$ 和 $\dfrac{ \partial  }{ \partial x }\dfrac{ \partial f }{ \partial y }$ 是相等的。然而，我们可以证明，如果 $f$ 是 $C^{2}$ 连续的，那么求导的顺序就是可以交换的。

**定理 19.4.2** Clairaut 定理

设 $E\subset \mathbb{R}^{n}$ 是开集，函数 $f\colon E\to \mathbb{R}^{m}$ 是 $C^{2}$ 函数，那么对任意 $x_{0}\in E$ 和整数 $1\leq i,j\leq n$ 有 $\dfrac{ \partial  }{ \partial x_{j} }\dfrac{ \partial f }{ \partial x_{i} }(x_{0})=\dfrac{ \partial  }{ \partial x_{i} }\dfrac{ \partial f }{ \partial x_{j} }(x_{0})$.

**证明**

由于偏导数分别作用于 $f$ 的每个分量，因此我们可以只研究其中一个分量，这样就可以假设 $m=1$. 当 $i=j$ 时，结论是平凡的，因此我们设 $i\neq j$. 最后，我们可以令 $F(x)=f(x+x_{0})$，从而我们只需证明 $F$ 在 $0$ 处可交换求导顺序。

设 $a=\dfrac{ \partial  }{ \partial x_{j} }\dfrac{ \partial F }{ \partial x_{i} }(0),b=\dfrac{ \partial  }{ \partial x_{i} }\dfrac{ \partial F }{ \partial x_{j} }(0)$，我们要证 $a=b$.

任取 $\varepsilon>0$，由于 $f$ 是 $C^{2}$ 函数，故存在 $\delta>0$ 使得对任意 $\lVert x \rVert< 2\delta$ 有

$$
\left\lvert  \dfrac{ \partial  }{ \partial x_{j} } \dfrac{ \partial F }{ \partial x_{i} } (x)-a  \right\rvert <\varepsilon,\left\lvert  \dfrac{ \partial  }{ \partial x_{i} } \dfrac{ \partial F }{ \partial x_{j} } (x)-b  \right\rvert <\varepsilon
$$

现在令 $X=F(\delta e_{i}+\delta e_{j})-F(\delta e_{i})-F(\delta e_{j})+F(0)$，根据微积分基本定理，我们有

$$
\begin{gather}
F(\delta e_{i}+\delta e_{j})-F(\delta e_{j})=\int_{0}^{\delta} \dfrac{ \partial F }{ \partial x_{i} } (x_{i}e_{i}+\delta e_{j})\mathrm{d} x_{i} \\
F(\delta e_{i})-F(0)=\int_{0}^{\delta}\dfrac{ \partial F }{ \partial x_{i} } (x_{i}e_{i})\mathrm{d} x_{i}
\end{gather}
$$

并且根据中值定理可知存在 $0<x_{j}<\delta$ 使得

$$
\dfrac{ \partial F }{ \partial x_{i} } (x_{i}e_{i}+\delta e_{j})-\dfrac{ \partial F }{ \partial x_{i} } (x_{i}e_{i})=\delta \dfrac{ \partial  }{ \partial x_{j} } \dfrac{ \partial F }{ \partial x_{i} } (x_{i}e_{i}+x_{j}e_{j})
$$

由于 $\lVert x_{i}e_{i}+x_{j}e_{j} \rVert\leq \sqrt{ 2 }\delta <2\delta$，故

$$
-\varepsilon \delta< \dfrac{ \partial F }{ \partial x_{i} } (x_{i}e_{i}+\delta e_{j})-\dfrac{ \partial F }{ \partial x_{i} } (x_{i}e_{i})-\delta a<\varepsilon \delta
$$

对 $x_{i}$ 在 $[0,\delta]$ 上积分得

$$
-\varepsilon\delta^{2}< X-\delta^{2}a<\varepsilon\delta^{2}
$$

同理，互换 $i,j$ 的位置，我们有 $-\varepsilon\delta^{2}<X-\delta^{2}b<\varepsilon\delta^{2}$，从而有

$$
\lvert \delta^{2}a-\delta^{2}b \rvert <2\varepsilon\delta^{2}
$$

即 $|a-b|<2\varepsilon$，根据 $\varepsilon$ 的任意性得 $a=b$.

上述定理表明，如果函数 $f$ 是 $C^{2}$ 函数，那么其导数就可以交换顺序，从而我们就可以把交叉导数写成 $\dfrac{ \partial^{2} f }{ \partial x \partial y }$，并且我们还可以将其扩展至 $C^{n}$ 函数。以 $C^{3}$ 函数为例，我们有

$$
\dfrac{ \partial  }{ \partial x } \dfrac{ \partial  }{ \partial y } \dfrac{ \partial f }{ \partial z } =\dfrac{ \partial  }{ \partial x } \dfrac{ \partial  }{ \partial z } \dfrac{ \partial f }{ \partial y } =\dfrac{ \partial  }{ \partial y } \dfrac{ \partial  }{ \partial x } \dfrac{ \partial f }{ \partial z } 
$$

这三者相等的原因不同：1 和 2 相等是因为 $C^{3}$ 函数同时也是 $C^{2}$ 函数，根据 Clairaut 定理，有 $\dfrac{ \partial  }{ \partial y }\dfrac{ \partial f }{ \partial z }=\dfrac{ \partial  }{ \partial z }\dfrac{ \partial f }{ \partial y }$，于是对 $x$ 的偏导数也相等；1 和 3 相等是因为根据定义，$\dfrac{ \partial f }{ \partial z }$ 是 $C^{2}$ 函数，从而根据 Clairaut 定理，有 $\dfrac{ \partial  }{ \partial x } \dfrac{ \partial  }{ \partial y } \dfrac{ \partial f }{ \partial z }=\dfrac{ \partial  }{ \partial y } \dfrac{ \partial  }{ \partial x } \dfrac{ \partial f }{ \partial z }$.

简而言之，我们可以对 $C^{n}$ 函数的 $n$ 重导数任意换序，从而像 $\dfrac{ \partial^{4} f }{ \partial x^{2} \partial y^{2} }$ 这样的符号不会引起歧义。不仅如此，我们还可以把偏导数看成一种**算子**，从而我们可以有如下公式：

$$
\left( \dfrac{ \partial  }{ \partial x } +\dfrac{ \partial  }{ \partial y }  \right)^{2} f=\left( \dfrac{ \partial^{2} }{ \partial x^{2} } +\dfrac{ \partial^{2} }{ \partial x \partial y } +\dfrac{ \partial^{2}  }{ \partial y^{2} }  \right)f=\dfrac{ \partial^{2} f }{ \partial x^{2} }+\dfrac{ \partial^{2} f }{ \partial x \partial y }+\dfrac{ \partial^{2} f  }{ \partial y^{2} }
$$

利用算子形式的偏导数，我们可以给出以下定理：

**定理 19.4.3** Taylor 公式（带 Lagrange 余项）

设 $E\subset \mathbb{R}^{n}$ 是开集，函数 $f\colon E\to \mathbb{R}$ 是 $C^{m+1}$ 函数，那么对任意 $x_{0}\in E$ 和 $v\in \mathbb{R}^{n},v\neq 0$，并且 $\{ x_{0}+tv \mid 0\leq t\leq 1 \}\subset E$，定义余项为

$$
R_{m}(x_{0}+v)=f(x_{0}+v)-\sum_{k=0}^{m} \dfrac{1}{k!} \left( v_{1}\dfrac{ \partial  }{ \partial x_{1} } +\dots+v_{n}\dfrac{ \partial  }{ \partial x_{n} }  \right)^{k} f(x_{0})
$$

那么存在 $0<t_{0}<1$ 使得

$$
R_{m}(x_{0}+v)= \dfrac{1}{(m+1)!}\left( v_{1}\dfrac{ \partial  }{ \partial x_{1} } +\dots+v_{n}\dfrac{ \partial  }{ \partial x_{n} }  \right)^{m+1}f(x_{0}+t_{0}v)
$$

**证明**

定义 $\phi\colon [0,1]\to \mathbb{R}$ 为

$$
\phi(t)=R_{m}(x_{0}+tv)=f(x_{0}+tv)-\sum_{k=0}^{m} \dfrac{t^{k}}{k!} \left( v_{1}\dfrac{ \partial  }{ \partial x_{1} } +\dots+v_{n}\dfrac{ \partial  }{ \partial x_{n} }  \right)^{k} f(x_{0})
$$

首先我们来证明

$$
\dfrac{\mathrm{d}^{k} }{\mathrm{d} t^{k}} f(x_{0}+tv)=\left( v_{1}\dfrac{ \partial  }{ \partial x_{1} } +\dots+v_{n}\dfrac{ \partial  }{ \partial x_{n} }  \right)^{k}f(x_{0}+tv),0\leq k\leq m+1
$$

我们使用归纳法，$k=0$ 的情况是平凡的，当 $k=1$ 时，有

$$
\dfrac{\mathrm{d} }{\mathrm{d} t}f(x_{0}+tv) =f'(x_{0}+tv)v=\left( \sum_{j=1}^{n} v_{j}\dfrac{ \partial  }{ \partial x_{j} }  \right)f(x_{0}+tv)
$$

假设结论对 $k-1$ 成立，则

$$
\begin{align}
& \dfrac{\mathrm{d}^{k} }{\mathrm{d} t^{k}} f(x_{0}+tv) = \dfrac{\mathrm{d} }{\mathrm{d} t}\left( v_{1}\dfrac{ \partial  }{ \partial x_{1} } +\dots+v_{n}\dfrac{ \partial  }{ \partial x_{n} }  \right)^{k-1}f(x_{0}+tv) \\
&= \dfrac{\mathrm{d} }{\mathrm{d} t}\left( \sum_{j_{1}+\dots+j_{n}=k-1} \binom{ k-1 }{ j_{1},\dots,j_{n} }  v_{1}^{j_{1}}\cdots v_{n}^{j_{n}}\dfrac{ \partial^{k-1} f(x_{0}+tv) }{ \partial x_{1}^{j_{1}}\cdots \partial x_{n}^{j_{n}} }  \right)
\end{align}
$$

其中 $\displaystyle \binom{ k }{ j_{1},\dots,j_{n} }= \dfrac{k!}{j_{1}! \cdots j_{n}!}$ 是多项式系数，其满足

$$
\binom{ k }{ j_{1},\dots,j_{n} } = \binom{ k-1 }{ j_{1}-1,j_{2},\dots,j_{n} } +\dots+\binom{ k-1 }{ j_{1},\dots,j_{n-1},j_{n}-1 } ,j_{r}>0
$$

展开成阶乘形式然后利用 $j_{1}+\dots+j_{n}=k$ 的条件即证。我们定义当某个 $j_{r}< 0$ 时多项式系数为 $0$，从而上述递推公式对任意 $j_{r}$ 都成立。

由于 $\dfrac{\mathrm{d}^{k} }{\mathrm{d} t^{k}} f(x_{0}+tv)$ 展开式中的项形如 $\displaystyle \binom{ k-1 }{ i_{1},\dots,i_{n} } v^{i_{1}}\cdots v^{i_{r}+1} \cdots v^{i_{n}}$，因此展开式中 $v^{j_{1}}\cdots v^{j_{n}}$ 项的系数来源于 $\dfrac{\mathrm{d}^{k-1} }{\mathrm{d} t^{k-1}} f(x_{0}+tv)$ 中的 $v^{j_{1}-1}\cdots v^{j_{n}}$ 等项，从而其系数为

$$
\binom{ k-1 }{ j_{1}-1,j_{2},\dots,j_{n} }+\dots+\binom{ k-1 }{ j_{1},\dots,j_{n-1},j_{n}-1 } = \binom{ k }{ j_{1},\dots,j_{n} } 
$$

因此我们有

$$
\begin{align}
\dfrac{\mathrm{d}^{k} }{\mathrm{d} t^{k}} f(x_{0}+tv) &= \left( \sum_{j_{1}+\dots+j_{n}=k} \binom{ k }{ j_{1},\dots,j_{n} } v_{1}^{j_{1}}\cdots v_{n}^{j_{n}} \dfrac{ \partial^{k} f(x_{0}+tv) }{ \partial x_{1}^{j_{1}} \cdots \partial x_{n}^{j_{n}} }  \right) \\
&= \left( \sum_{j=1}^{n} v_{j}\dfrac{ \partial  }{ \partial x_{j} }  \right)^{k} f(x_{0}+tv)
\end{align}
$$

由于 $\phi$ 在 $[0,1]$ 上 $m+1$ 次可微，由一元函数 Taylor 公式知存在 $0<t_{0}<1$ 使得

$$
R_{m}(x_{0}+v)=\phi(1)=\sum_{k=0}^{m} \dfrac{\phi^{(k)}(0)}{k!}+ \dfrac{\phi^{(m+1)}(t_{0})}{(m+1)!}
$$

根据上面的讨论就得到了我们要证明的。

上述定理是对一元函数的 Taylor 公式的扩展，也是对多元函数中值定理（19.3.2）的扩展，因此，我们可以看出这两个定理的证明是类似的。

现在我们来看看 Taylor 展开式的前三项，第一项就是平凡的 $f(x_{0})$，第二项是 $\displaystyle \sum_{j=1}^{n}v_{j} \dfrac{ \partial f }{ \partial x_{j} }(x_{0})$，即 $v\cdot \nabla f(x_{0})$，第三项则是

$$
\dfrac{1}{2} \left( v_{1}\dfrac{ \partial  }{ \partial x_{1} } +\dots+v_{n}\dfrac{ \partial  }{ \partial x_{n} }  \right)^{2} f(x_{0})=\dfrac{1}{2} v^{T} H_{f}(x_{0}) v
$$

其中

$$
H_{f}(x_{0})=\left( \dfrac{ \partial^{2} f }{ \partial x_{i} \partial x_{j} } (x_{0}) \right)_{1\leq i,j\leq n}
$$

称为 $f$ 的 **Hessian 矩阵**。根据 Clairaut 定理，如果 $f$ 至少是 $C^{2}$ 连续的，那么 $H_{f}(x)$ 就是一个实对称矩阵，根据线性代数的理论，二次型 $v^{T}H_{f}(x)v$ 的正负值取决于 $H_{f}(x)$ 是正定的还是负定的，这就给了我们一种判断极值的方法。不过首先，我们要把 Fermat 引理推广至多元函数。

**定理 19.4.4** Fermat 引理

设 $E\subset \mathbb{R}^{n}$，函数 $f\colon E\to \mathbb{R}$ 在 $x_{0}\in \mathrm{Int}(E)$ 处达到极大值或极小值，如果 $f$ 在 $x_{0}$ 处可微，那么有 $\nabla f(x_{0})=0$.

**证明**

不妨设 $f$ 在 $x_{0}$ 处达到极大值，那么对任意 $1\leq j\leq n$，存在 $\delta>0$ 使得对任意 $|t|<\delta$ 有 $f(x_{0}+te_{j})\geq f(x_{0})$，考虑偏导数定义式

$$
\lim_{ t \to 0;|t|<\delta } \dfrac{f(x_{0}+te_{j})-f(x_{0})}{t}
$$

的左极限和右极限，由于 $f$ 在 $x_{0}$ 处可微，故偏导数 $\dfrac{ \partial f }{ \partial x_{j} }(x_{0})=0$，从而 $\nabla f(x_{0})=\left( \dfrac{ \partial f }{ \partial x_{1} },\dots,\dfrac{ \partial f }{ \partial x_{n} } \right)=0$.

**定理 19.4.5**

设开集 $E\subset \mathbb{R}^{n},x_{0}\in E$，函数 $f\colon E\to \mathbb{R}$ 是 $C^{2}$ 函数，且 $\nabla f(x_{0})=0$，那么对任意 $x \in E$，

1. 如果 $H_{f}(x)$ 是正定矩阵，那么 $f$ 在 $x_{0}$ 处达到严格极小值。
2. 如果 $H_{f}(x)$ 是负定矩阵，那么 $f$ 在 $x_{0}$ 处达到严格极大值。

**证明**

由于 $E$ 是开集，故存在 $\delta>0$ 使得 $B(x_{0},\delta)\subset E$，设 $v \in \mathbb{R}^{n},v\neq 0$ 满足 $x_{0}+v \in B(x_{0},\delta)$，则根据 Taylor 公式有

$$
f(x_{0}+v)-f(x_{0})= \dfrac{1}{2} v^{T} H_{f}(x_{0}+t_{0}v) v
$$

如果 $H_{f}(x)$ 是正定的，那么 $f(x_{0}+v)-f(x_{0})>0$，即 $f$ 在 $x_{0}$ 处达到严格极小值；反之，则 $f$ 在 $x_{0}$ 处达到严格极大值。

这个定理也可以限制在一维上，这时 Hessian 矩阵就退化为 $f''(x)$，从而我们有 $f''(x)>0\implies f$ 在 $x_{0}$ 处达到严格极小值，反之亦然。

# Section 5: 反函数定理

在引入下一个主要定理：反函数定理之前，我们先来利用完备度量空间的理论来建立一个重要引理，即**压缩映射定理**。

**定义 19.5.1** 压缩映射（contraction map）

设 $(X,d)$ 是度量空间，映射 $f\colon X\to X$，如果对任意 $x,y \in X$ 有 $d(f(x),f(y))\leq d(x,y)$，则称 $f$ 是一个**压缩映射**。如果存在实数 $0<c<1$ 使得对任意 $x,y \in X$ 有 $d(f(x),f(y))\leq c d(x,y)$，则称 $f$ 是一个**严格压缩映射**，称 $c$ 为 $f$ 的**压缩系数**。

**定义 19.5.2** 不动点（fixed point）

设 $f\colon X\to X$ 是一个映射，$x \in X$，如果 $f(x)=x$，则称 $x$ 是 $f$ 的一个**不动点**。

我们可以证明，严格压缩映射一定有不动点，至少对于完备度量空间是如此。

**定理 19.5.3** 压缩映射定理（contraction mapping theorem）

设 $(X,d)$ 是度量空间，$f\colon X\to X$ 是一个严格压缩映射，那么 $f$ 最多有一个不动点。如果进一步有 $X$ 是非空且完备的，那么 $f$ 恰有一个不动点。

**证明**

假设 $f$ 有两个不动点 $x,y$，则 $d(f(x),f(y))=d(x,y)$，这与 $f$ 是严格压缩映射矛盾。

现设 $X$ 是非空且完备的，取 $x_{0}\in X$，并递归地定义 $x_{n+1}=f(x_{n})$，得到序列 $(x_{n})_{n=0}^{\infty}$，其满足

$$
d(x_{n+1},x_{n})=d(f(x_{n}),f(x_{n-1}))\leq cd(x_{n},x_{n-1})\leq \dots\leq c^{n}d(x_{1},x_{0})
$$

当 $n>m\geq 0$ 时，我们有

$$
d(x_{n},x_{m})\leq d(x_{n},x_{n-1})+\dots+d(x_{m+1},x_{m})\leq \dfrac{c^{m}}{1-c}d(x_{1},x_{0})
$$

任取 $\varepsilon>0$，取 $N$ 使得 $\dfrac{c^{N}}{1-c}d(x_{1},x_{0}) <\varepsilon$，则对任意 $n>m>N$ 有 $d(x_{n},x_{m})\leq \dfrac{c^{N}}{1-c}d(x_{1},x_{0})<\varepsilon$，故 $(x_{n})$ 是一个 Cauchy 序列，由 $X$ 的完备性知其收敛于 $x \in X$，下面我们要证 $f(x)=x$.

取 $\varepsilon>0$，存在 $N$ 使得对任意 $n>N$ 有 $d(x_{n},x)<\varepsilon$，则有

$$
d(x,f(x))\leq d(x,x_{n+1})+d(f(x_{n}),f(x))<\varepsilon+cd(x_{n},x)<(1+c)\varepsilon
$$

即 $f(x)=x$，这就完成了证明。

下面我们给出压缩映射定理的一个推论，它在反函数定理的证明中起到了重要的作用。

**引理 19.5.4**

设实数 $r>0$，$B(0,r)\subset \mathbb{R}^{n}$，函数 $g\colon B(0,r)\to \mathbb{R}^{n}$ 满足 $g(0)=0$，并且对任意 $x,y \in B(0,r)$ 有

$$
\lVert g(x)-g(y) \rVert \leq \dfrac{1}{2}\lVert x-y \rVert 
$$

那么定义为 $f(x)=x+g(x)$ 的函数 $f\colon B(0,r)\to \mathbb{R}^{n}$ 是单射，并且 $B\left( 0, \dfrac{r}{2} \right)\subset f[B(0,r)]$.

**证明**

假设 $f$ 不是单射，即存在 $x\neq y$ 使得 $f(x)=f(y)$，即 $x+g(x)=x+g(y)$，从而 $\lVert g(x)-g(y) \rVert=\lVert x-y \rVert$，这与 $g$ 的定义矛盾。因此 $f$ 是单射。

现设 $y \in B\left( 0,\dfrac{r}{2} \right)$，我们要证存在 $x \in B(0,r)$ 使得 $f(x)=x+g(x)=y$. 定义 $F(x)=y-g(x)$，我们有

$$
\lVert F(x) \rVert \leq \lVert y \rVert +\lVert g(x) \rVert \leq \lVert y \rVert + \dfrac{1}{2}\lVert x \rVert <r
$$

从而 $F$ 将 $B(0,r)$ 映射到自身，并且也是 $B(0,r)$ 上的严格压缩映射。

取 $0<\varepsilon<r-2\lVert y \rVert$，将 $F$ 限制在闭球 $\overline{B(0,r-\varepsilon)}$ 上，则

$$
\lVert F(x) \rVert \leq \lVert y \rVert +\dfrac{1}{2}\lVert x \rVert \leq \lVert y \rVert +\dfrac{r-\varepsilon}{2}\leq r-\varepsilon
$$

从而 $F$ 是完备度量空间 $\overline{B(0,r-\varepsilon)}$ 上的严格压缩映射，从而有不动点 $x$，即 $F(x)=y-g(x)=x$，这就完成了证明。

使用这个引理，我们可以证明多元微积分中最重要的定理之一，即反函数定理。

**定理 19.5.5** 反函数定理（inverse function theorem）

设 $E\subset \mathbb{R}^{n}$ 是开集，函数 $f\colon E\to \mathbb{R}^{n}$ 是 $C^{1}$ 函数，$x_{0}\in E$，如果线性映射 $f'(x_{0})\colon \mathbb{R}^{n}\to \mathbb{R}^{n}$ 可逆，那么存在包含 $x_{0}$ 的开集 $U\subset E$ 和包含 $f(x_{0})$ 的开集 $V\subset \mathbb{R}^{n}$ 使得 $f$ 是 $U$ 到 $V$ 的双射，并且逆映射 $f^{-1}\colon V\to U$ 在 $f(x_{0})$ 处可微，且

$$
(f^{-1})'(f(x_{0}))=f'(x_{0})^{-1}
$$

**证明**

首先我们注意到，如果 $f^{-1}$ 在 $f(x_{0})$ 处可微，定义恒等映射 $Ix=x$，则有

$$
I=I'(x_{0})=(f^{-1}\circ f)'(x_{0})=(f^{-1})'(f(x_{0}))f'(x_{0})
$$

即 $(f^{-1})'(f(x_{0}))=f'(x_{0})^{-1}$. 下面注意到只需证明 $f(x_{0})=0$ 的情况，因为我们可以定义 $F(x)=f(x)-f(x_{0})$，此时有 $f^{-1}(y)=F^{-1}(y-f(x_{0}))$，因此我们可以设 $f(x_{0})=0$.

类似地，我们也可以假设 $x_{0}=0$，因为我们可以定义 $G(x)=f(x+x_{0})$，从而 $f^{-1}(y)=G^{-1}(y)+x_{0}$，从而我们设 $x_{0}=0$.

最后，我们可以假设 $f'(0)=I$，因为我们可以定义 $H(x)=f'(0)^{-1}f(x)$，一旦我们对 $H$ 证明了反函数定理，即存在包含 $0$ 的开集 $U',V'$ 使得 $H$ 是 $U'\to V'$ 的双射，并且 $H^{-1}$ 在 $0$ 处可微，且 $(H^{-1})'(0)=I$，由于 $f'(0)^{-1}$ 是连续的，故 $f'(0)[V']$ 是包含 $0$ 的开集，根据 $f(x)=f'(0)H(x)$ 我们有 $f^{-1}(y)=H^{-1}(f'(0)^{-1} y)$，从而 $f^{-1}$ 在 $0$ 处可微，并且

$$
(f^{-1})'(0)=(H^{-1})'(0) f'(0)^{-1}=f'(0)^{-1}
$$

因此，我们要证明 $x_{0}=0,f(x_{0})=0,f'(x_{0})=I$ 时的反函数定理。

设 $g\colon E\to \mathbb{R}^{n}$ 定义为 $g(x)=f(x)-x$，则 $g(0)=g'(0)=0$，从而对任意整数 $1\leq j\leq n$ 有 $\dfrac{ \partial g }{ \partial x_{j} }(0)=0$，又因为 $g$ 是 $C^{1}$ 函数，故存在 $r>0$ 使得对任意 $x \in B(0,r)$ 有

$$
\left\lVert  \dfrac{ \partial g }{ \partial x_{j} } (x)  \right\rVert \leq \dfrac{1}{2n^{2}}
$$

从而对任意 $v \in \mathbb{R}^{n}$ 有

$$
\lVert D_{v}g(x) \rVert =\left\lVert  \sum_{j=1}^{n} v_{j}\dfrac{ \partial g }{ \partial x_{j} } (x)  \right\rVert \leq \sum_{j=1}^{n} |v_{j}| \dfrac{1}{2n^{2}}\leq \dfrac{1}{2n}\lVert v \rVert 
$$

根据微积分基本定理，对任意 $x,y \in B(0,r)$ 有

$$
g(y)-g(x)=\int_{0}^{1} \dfrac{\mathrm{d} }{\mathrm{d} t}g(x+t(y-x))\mathrm{d} t=\int_{0}^{1} D_{y-x}g(x+t(y-x))\mathrm{d} t
$$

由于 $\lVert D_{y-x}g(x+t(y-x)) \rVert\leq \dfrac{1}{2n}\lVert y-x \rVert$，故该向量每个分量的大小都小于等于 $\dfrac{1}{2n}\lVert y-x \rVert$，于是 $\lVert g(y)-g(x) \rVert\leq \dfrac{1}{2}\lVert y-x \rVert$.

根据引理 19.5.4，定义为 $f(x)=x+g(x)$ 的函数 $f$ 在 $B(0,r)$ 上是单射，并且 $B\left( 0,\dfrac{r}{2} \right)\subset f[B(0,r)]$，从而有逆映射 $f^{-1}\colon B\left( 0,\dfrac{r}{2} \right)\to B(0,r)$.

设 $V=B\left( 0,\dfrac{r}{2} \right),U=f^{-1}[V]$，则 $f$ 是从 $U$ 到 $V$ 的连续双射，故 $U,V$ 都是包含 $0$ 的开集，下面我们要证

$$
\lim_{ y \to 0;y \in V } \dfrac{\lVert f^{-1}(y)-f^{-1}(0)-I(y) \rVert }{\lVert y \rVert }=\lim_{ y \to 0;y \in V } \dfrac{\lVert f^{-1}(y)-y \rVert }{\lVert y \rVert }=0
$$

由于 $\lVert g(x) \rVert=\lVert f(x)+x \rVert\leq \dfrac{1}{2}\lVert x \rVert$，故 $\dfrac{1}{2}\lVert x \rVert\leq \lVert f(x) \rVert\leq \dfrac{3}{2}\lVert x \rVert$，取 $V\setminus\{ 0 \}$ 中收敛于 $0$ 的序列 $(y_{n})$，定义 $x_{n}=f^{-1}(y_{n})$，则

$$
\dfrac{1}{2}\lVert x_{n} \rVert \leq \lVert y_{n} \rVert \leq \dfrac{3}{2}\lVert x_{n} \rVert 
$$

从而序列 $(x_{n})$ 收敛于 $0$，由于 $f$ 在 $0$ 处可微，故

$$
\lim_{ n \to \infty } \dfrac{\lVert f(x_{n})-f(0)-I(x_{n}) \rVert }{\lVert x_{n} \rVert }=\lim_{ n \to \infty } \dfrac{\lVert y_{n}-f^{-1}(y_{n}) \rVert }{\lVert y_{n} \rVert }=0
$$

这就完成了证明。

反函数定理指出，一个函数在 $x_{0}$ 的某个邻域内是局部可逆的，如果它在此处的导数 $f'(x_{0})$ 是可逆的，此时我们还可以计算逆映射的导数 $f'(x_{0})^{-1}$.

当 $f'(x_{0})$ 存在但不可逆时，我们可以从证明过程中看出，$f^{-1}$ 在 $f(x_{0})$ 处不可能可微，此时反函数定理就失效了。然而，$f$ 仍然可以有逆映射，例如函数 $x\mapsto x^{3}$ 在 $0$ 处导数为 $0$，但是它仍然可逆。

下面，我们给出反函数定理的一个应用。

**定理 19.5.6**

设 $f\colon \mathbb{R}^{n}\to \mathbb{R}^{n}$ 是一个 $C^{1}$ 函数，并且对任意 $x \in \mathbb{R}^{n}$，线性映射 $f'(x)$ 都是可逆的，那么只要 $V\subset \mathbb{R}^{n}$ 是开集，$f[V]$ 就是开集。

**证明**

设 $y_{0}\in f[V]$，则存在 $x_{0}\in V$ 使得 $f(x_{0})=y_{0}$. 由于 $f'(x_{0})$ 可逆，故存在包含 $x_{0}$ 的开集 $U\subset V$ 和包含 $y_{0}$ 的开集 $W\subset \mathbb{R}^{n}$ 使得 $f$ 是 $U\to W$ 的双射。

取 $w \in W$，则 $f'(f^{-1}(w))$ 是可逆的，从而 $f^{-1}$ 在 $f(f^{-1}(w))=w$ 处可微，故 $f^{-1}$ 在 $W$ 上连续。

现设 $U'=B(x,r)\cap U$ 是开集，$W'=f[U']\subset W$，则 $f$ 是 $U'\to W'$ 的双射，从而有 $f[U']=W'$，故 $W'\subset f[V]$ 是开集，并且它包含 $f(x_{0})=y_{0}$，这表明 $f[V]$ 是开集。

# Section 6: 隐函数定理

有时候，一个函数关系不是直接由 $y=f(x)$ 给出，而是由一个方程 $F(x,y)=0$ 隐含地给出的。例如，单位圆方程 $x^{2}+y^{2}=1$ 限制在上半圆可以唯一地确定一个函数 $y=\sqrt{ 1-x^{2} }$，但是在 $x=1$ 附近无法确定任何以 $x$ 为自变量的函数。然而，在此处可以确定以 $y$ 为自变量的函数 $x=\sqrt{ 1-y^{2} }$. 因此，虽然单位圆方程不能直接给出函数关系，但是它在局部可以确定一个函数。

现在，我们自然要问，什么样的函数 $F$ 可以使我们能够从方程 $F(x)=0$ 的局部确定一个函数，进一步，这个函数有什么性质呢？**隐函数定理**给出了一种判断方法。

**定理 19.6.1** 隐函数定理（implicit function theorem）

设 $E\subset \mathbb{R}^{n}$ 是开集，函数 $f\colon E\to \mathbb{R}$ 是 $C^{1}$ 函数，$y=(y_{1},\dots,y_{n})\in E$ 满足 $f(y)=0,\dfrac{ \partial f }{ \partial x_{n} }(y)\neq 0$，那么存在包含 $(y_{1},\dots,y_{n-1})$ 的开集 $U\subset \mathbb{R}^{n-1}$ 和包含 $y$ 的开集 $V\subset E$ 以及函数 $g\colon U\to \mathbb{R}$ 使得 $g(y_{1},\dots,y_{n-1})=y_{n}$ 并且

$$
\begin{align}
& \{ x\in V \mid f(x)=0 \} \\
&=\{ (x_{1},\dots,x_{n-1},g(x_{1},\dots,x_{n-1})) \mid (x_{1},\dots,x_{n-1})\in U \}
\end{align}
$$

此外，$g$ 在 $(y_{1},\dots,y_{n-1})$ 处可微，并且对任意整数 $1\leq j\leq n-1$ 有

$$
\dfrac{ \partial g }{ \partial x_{j} } (y_{1},\dots,y_{n-1})=- \dfrac{ \partial f }{ \partial x_{j} } (y) / \dfrac{ \partial f }{ \partial x_{n} } (y)
$$

**证明**

我们将使用反函数定理来证明它。设函数 $F\colon E\to \mathbb{R}^{n}$ 定义为

$$
F(x_{1},\dots,x_{n})=(x_{1},\dots,x_{n-1},f(x_{1},\dots,x_{n}))
$$

则 $F$ 是 $C^{1}$ 函数，并且 $F(y)=(y_{1},\dots,y_{n-1},0)$，还有

$$
J_{F}(y)=\begin{pmatrix}
1 & 0 & \cdots & 0 & 0 \\
0 & 1 & \cdots & 0 & 0 \\
\vdots & \vdots & \ddots & \vdots & \vdots \\
0 & 0 & \cdots & 1 & 0 \\
\dfrac{ \partial f }{ \partial x_{1} } (y) & \dfrac{ \partial f }{ \partial x_{2} } (y) & \cdots & \dfrac{ \partial f }{ \partial x_{n-1} } (y) & \dfrac{ \partial f }{ \partial x_{n} } (y)
\end{pmatrix}
$$

由于 $\dfrac{ \partial f }{ \partial x_{n} }(y)\neq 0$，故 $J_{F}(y)$ 可逆，从而有包含 $y$ 的开集 $V\subset E$ 和包含 $F(y)$ 的开集 $W\subset \mathbb{R}^{n}$ 使得 $F$ 是 $V$ 到 $W$ 的双射，并且 $F^{-1}$ 在 $F(y)$ 处可微。

设 $F^{-1}(x)=(h_{1}(x),\dots,h_{n}(x))$，由于 $F(F^{-1}(x))=x$，故对任意整数 $1\leq j\leq n-1$ 有 $h_{j}(x)=x_{j}$，并且

$$
f(x_{1},\dots,x_{n-1},h_{n}(x_{1},\dots,x_{n}))=x_{n}
$$

令 $U=\{ (x_{1},\dots,x_{n-1}) \in \mathbb{R}^{n-1} \mid (x_{1},\dots,x_{n-1},0)\in W \}$，则 $U$ 是包含 $(y_{1},\dots,y_{n-1})$ 的开集，定义 $g\colon U\to \mathbb{R}$ 为

$$
g(x_{1},\dots,x_{n-1})=h_{n}(x_{1},\dots,x_{n-1},0)
$$

我们来证明

$$
\begin{align}
& \{ x\in V \mid f(x)=0 \} \\
&=\{ (x_{1},\dots,x_{n-1},g(x_{1},\dots,x_{n-1})) \mid (x_{1},\dots,x_{n-1})\in U \}
\end{align}
$$

设 $x \in V,f(x_{1},\dots,x_{n})=0$，于是 $F(x)=(x_{1},\dots,x_{n-1},0)\in W$，那么 $(x_{1},\dots,x_{n-1})\in U$，并且 $x=F^{-1}(x_{1},\dots,x_{n-1},0)$，从而有

$$
x_{n}=h_{n}(x_{1},\dots,x_{n-1},0)=g(x_{1},\dots,x_{n-1})
$$

这就证明了一个方向的包含。反之，设 $(x_{1},\dots,x_{n-1})\in U$，且 $x_{n}=h_{n}(x_{1},\dots,x_{n-1},0)$，则 $F(x_{1},\dots,x_{n})=(x_{1},\dots,x_{n-1},0)$，即 $f(x_{1},\dots,x_{n})=0$，并且 $x=F^{-1}(x_{1},\dots,x_{n-1},0)\in V$，即证。

由于 $F^{-1}$ 在 $(y_{1},\dots,y_{n-1},0)$ 处可微，故 $g$ 也在该点可微，又由于 $f$ 在 $y=(y_{1},\dots,y_{n-1},g(y_{1},\dots,y_{n-1}))$ 处可微，对

$$
f(x_{1},\dots,x_{n-1},g(x_{1},\dots,x_{n-1}))=0,(x_{1},\dots,x_{n-1})\in U
$$

应用链式法则得

$$
\dfrac{ \partial f }{ \partial x_{j} } (y)+\dfrac{ \partial f }{ \partial x_{n} }(y) \dfrac{ \partial g }{ \partial x_{j} } (y_{1},\dots,y_{n-1})=0
$$

这就完成了证明。

注意，上述定理中我们假设 $\dfrac{ \partial f }{ \partial x_{n} }(y)\neq 0$，我们完全可以把这个假设换成任意一个 $\dfrac{ \partial f }{ \partial x_{j} }(y)\neq 0$，此时确定的隐函数 $g$ 就会把 $x_{j}$ 以外的变量作为自变量。因此，只要梯度 $\nabla f(y)\neq 0$，那么集合 $\{ x \in \mathbb{R}^{n} \mid f(x)=0 \}$ 就可以确定某个变量 $x_{j}$ 关于另外 $n-1$ 个变量的隐函数。

如果一个集合的每一点处都可以确定某个连续的隐函数，那么这个集合就称为**流形**，它是现代几何学的基本概念之一。

作为隐函数定理的一个推论，我们有一种可以在约束条件下求函数极值的方法（条件极值），称为 **Lagrange 乘数法**。

**定理 19.6.2** Lagrange 乘数法

设 $E\subset \mathbb{R}^{n}$ 是开集，函数 $f\colon E\to \mathbb{R},g\colon E\to \mathbb{R}$ 都是 $C^{1}$ 函数，如果 $x^{*}\in E$ 是 $f$ 在约束 $g(x)=0$ 下的极值点，并且 $\nabla g(x^{*})\neq 0$，那么存在 $\lambda$ 使得

$$
\nabla f(x^{*})=\lambda \nabla g(x^{*})
$$

**证明**

由于 $\nabla g(x^{*})\neq 0$，不妨设 $\dfrac{ \partial g }{ \partial x_{n} }(x^{*})\neq 0$，根据隐函数定理，存在开集 $U\subset \mathbb{R}^{n-1}$ 和函数 $\phi\colon U\to \mathbb{R}$ 使得

$$
g(x_{1},\dots,x_{n-1},\phi(x_{1},\dots,x_{n-1}))=0,(x_{1},\dots,x_{n-1})\in U
$$

定义函数 $F\colon U\to \mathbb{R}$ 为

$$
F(x_{1},\dots,x_{n-1})=f(x_{1},\dots,x_{n-1},\phi(x_{1},\dots,x_{n-1}))
$$

由于 $x^{*}=(x_{1}^{*},\dots,x_{n}^{*})$ 是 $f$ 在约束 $g(x)=0$ 下的极值点，故 $(x_{1}^{*},\dots,x_{n-1}^{*})$ 是 $F$ 在无约束条件下的极值点，从而对任意 $1\leq j\leq n-1$ 有

$$
\begin{align}
\dfrac{ \partial F }{ \partial x_{j} } (x_{1}^{*},\dots,x_{n-1}^{*}) &= \dfrac{ \partial f }{ \partial x_{j} }+\dfrac{ \partial f }{ \partial x_{n} } \dfrac{ \partial \phi }{ \partial x_{j} }  \\
&= \dfrac{ \partial f }{ \partial x_{j} }- \dfrac{ \partial f }{ \partial x_{n} } \left(  \dfrac{ \partial g }{ \partial x_{j} }  / \dfrac{ \partial g }{ \partial x_{n} } \right) \\
&= 0
\end{align}
$$

即 $\dfrac{ \partial f }{ \partial x_{j} } / \dfrac{ \partial g }{ \partial x_{j} }=\dfrac{ \partial f }{ \partial x_{n} } / \dfrac{ \partial g }{ \partial x_{n} }=\lambda$，从而有 $\nabla f(x^{*})=\lambda \nabla g(x^{*})$，这就完成了证明。

上述定理的一个等价形式是，定义 Lagrange 函数

$$
L(x,\lambda)=f(x)-\lambda g(x)
$$

如果 $x^{*}$ 是 $f$ 在约束 $g(x)=0$ 下的极值点，那么就有

$$
\nabla L(x^{*},\lambda)=\nabla f(x^{*})-\lambda \nabla g(x^{*})=0
$$

计算时，我们需要解方程组 $\dfrac{ \partial L }{ \partial x_{j} }=0,\dfrac{ \partial L }{ \partial \lambda }=-g(x)=0$，得到的 $x^{*}$ 值就是可能的极值点之一（因为这是必要条件）。

如果我们有 $k$ 个约束 $g_{1}(x)=0,\dots,g_{k}(x)=0$，我们根据上面的证明过程可以看出一些推广的方法。本质上来说，Lagrange 乘数法就是利用隐函数定理，将一个单约束 $n$ 个变量的问题转化为了一个无约束 $n-1$ 个变量的问题。那么推广的方法就很明显了：我们需要一种高维的隐函数定理，其能够将 $k$ 个约束 $n$ 个变量的问题转化为无约束 $n-k$ 个变量的问题。这两个定理我们将在附录中叙述。