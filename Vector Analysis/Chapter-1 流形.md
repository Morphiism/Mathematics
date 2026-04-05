我们已经熟悉了 Euclid 空间 $\mathbb{R}^{n}$ 上的微分学与积分学，以及其上的 $n$ 维体积（测度）：设 $A\subset \mathbb{R}^{n}$ 是一个可测集，其体积可以写成

$$
\begin{gather}
m(A)=\int_{A} 1
\end{gather}
$$

当 $n=1$ 时，通常称 $m(A)$ 为 $A$ 的长度，而 $n=2$ 时称为 $A$ 的面积。

不过，在应用中，我们也会遇到 $\mathbb{R}^{n}$ 中的低维结构：例如，$\mathbb{R}^{3}$ 中的曲线是 1 维结构，曲面是 2 维结构，对于足够光滑的低维结构，我们希望能够求出它们的长度或面积。在本章中，我们将定义曲线与曲面的 $k$ 维对应物，称为 $\mathbb{R}^{n}$ 中的 $k$-**流形**，并且我们也将定义与之相关的 $k$ 维体积，最后，我们将明确什么是流形上关于 $k$-体积的积分。

# Section 1: 平行六面体

我们以平行六面体开始，它的体积拥有一个显式的公式。

**定义 1.1.1** 平行六面体（parallelopiped）

设 $k\leq n$，称 $\mathcal{P}\subset \mathbb{R}^{n}$ 是一个 $k$-**平行六面体**，如果存在线性无关的向量 $v_{1},\dots,v_{k}\in \mathbb{R}^{n}$ 使得

$$
\begin{gather}
\mathcal{P}=\mathcal{P}(v_{1},\dots,v_{k})=\{ c_{1}v_{1}+\dots+c_{k}v_{k} \mid 0\leq c_{j}\leq 1 \}
\end{gather}
$$

称向量 $v_{1},\dots,v_{k}$ 为 $\mathcal{P}$ 的**边**。

显然，一个 2-平行六面体为平行四边形，而一个 3-平行六面体则是平行六面体它本来的含义。

当 $k=n$ 时，平行六面体 $\mathcal{P}(v_{1},\dots,v_{n})$ 的 $n$ 维体积很容易求出：考虑将标准基 $e_{j}$ 映射为 $v_{j}$ 的线性映射 $T$，则它将单位正方体 $I^{n}=[0,1]^{n}$ 映射到 $\mathcal{P}$，从而有

$$
\begin{gather}
m(\mathcal{P})=|\det T| m(I^{n})=|\det T|
\end{gather}
$$

然而，当 $k<n$ 时，$\mathcal{P}$ 的 $n$ 维体积等于 0，因为其包含在 $\mathbb{R}^{n}$ 的一个体积为 0 的低维子空间中。这就要求我们给出 $k$ 维体积的定义。尽管我们对此还没有思路，但我们知道这种体积所要满足的两条性质：首先，我们知道正交变换保持 $n$ 维体积不变，因此我们可以合理地要求这一性质对 $k$ 维体积也成立；其次，如果 $\mathcal{P}$ 正好位于 $\mathbb{R}^{n}$ 的子空间 $\mathbb{R}^{k}\times 0$ 中，那么 $\mathcal{P}$ 在 $\mathbb{R}^{n}$ 中的 $k$ 维体积应当等于 $\mathcal{P}$ 作为 $\mathbb{R}^{k}$ 中的平行六面体的体积。下面我们将看到，这两个性质唯一地确定了 $\mathbb{R}^{n}$ 上的 $k$-体积。

**引理 1.1.2**

设 $W$ 是 $\mathbb{R}^{n}$ 的一个 $k$ 维子空间，则存在 $\mathbb{R}^{n}$ 的一个规范正交基使得其前 $k$ 个向量构成了 $W$ 的一个规范正交基。

**证明**

取 $W$ 的一个基，将其扩张成 $\mathbb{R}^{n}$ 的一个基，然后对其应用 Gram-Schmidt 过程即可。

**引理 1.1.3**

设 $W$ 是 $\mathbb{R}^{n}$ 的一个 $k$ 维子空间，则存在正交变换 $h\colon \mathbb{R}^{n}\to \mathbb{R}^{n}$ 使得 $W$ 在 $h$ 下的像是子空间 $\mathbb{R}^{k}\times 0$.

**证明**

根据引理 1.1.2，我们可以取规范正交基 $b_{1},\dots,b_{n}$ 使得 $b_{1},\dots,b_{k}$ 是 $W$ 的规范正交基。定义线性映射 $g\colon \mathbb{R}^{n}\to \mathbb{R}^{n}$ 为 $g(e_{j})=b_{j}$，则有 $g(x)=Bx$，其中矩阵 $B$ 的列是 $b_{1},\dots,b_{n}$. 由规范正交性，我们有 $B^{T}B=I$，从而 $g$ 是正交变换。此外，$g$ 将 $\mathbb{R}^{k}\times 0$ 的基 $e_{1},\dots,e_{k}$ 映射到 $b_{1},\dots,b_{k}$，因此 $h=g^{-1}$ 就是所求的正交变换。

现在我们来构造所求的 $k$-体积。

**定理 1.1.4**

设 $k<n$，存在唯一的函数 $V\colon (\mathbb{R}^{n})^{k}\to [0,\infty)$ 满足以下性质：

1. 如果 $h\colon \mathbb{R}^{n}\to \mathbb{R}^{n}$ 是正交变换，则 $V(h(x_{1}),\dots,h(x_{k}))=V(x_{1},\dots,x_{k})$
2. 如果 $y_{1},\dots,y_{k}$ 属于 $\mathbb{R}^{n}$ 的子空间 $\mathbb{R}^{k}\times 0$，使得对任意 $j$ 有 $y_{j}=(z_{j},0,\dots,0)$，那么 $V(y_{1},\dots,y_{k})=|\det(z_{1},\dots,z_{k})|$

函数 $V(x_{1},\dots,x_{k})=0$ 当且仅当 $x_{1},\dots,x_{k}$ 线性相关，并且其满足等式

$$
\begin{gather}
V(x_{1},\dots,x_{k})=\sqrt{ \det (X^{T}X) }
\end{gather}
$$

其中 $X=[x_{1},\dots,x_{k}]$ 是以 $x_{1},\dots,x_{k}$ 为列的矩阵。

**证明**

给定 $X=[x_{1},\dots,x_{k}]$，我们定义

$$
\begin{gather}
F(X)=\det(X^{T}X)
\end{gather}
$$

(1). 如果 $h\colon \mathbb{R}^{n}\to \mathbb{R}^{n}$ 是正交变换，则存在正交矩阵 $Q$ 使得 $h(x)=Qx$，则我们有

$$
\begin{gather}
F(QX)=\det(X^{T}Q^{T}QX)=\det(X^{T}X)=F(X)
\end{gather}
$$

此外，如果 $Z$ 是一个 $k\times k$ 矩阵，$Y$ 是一个 $n\times k$ 矩阵，并且满足

$$
\begin{gather}
Y=\begin{bmatrix}
Z \\
0
\end{bmatrix}
\end{gather}
$$

则

$$
\begin{gather}
F(Y)=\det\left(\begin{bmatrix}
Z^{T} & 0
\end{bmatrix}\begin{bmatrix}
Z \\
0
\end{bmatrix}\right)=\det(Z^{T}Z)=(\det Z)^{2}
\end{gather}
$$

(2). 给定 $x_{1},\dots,x_{k}\in \mathbb{R}^{n}$，取包含它们的一个 $k$ 维子空间 $W$，令 $h(x)=Qx$ 是引理 1.1.3 中的正交变换，则矩阵 $QX$ 具有形式

$$
\begin{gather}
QX=\begin{bmatrix}
Z \\
0
\end{bmatrix}
\end{gather}
$$

从而 $F(X)=F(QX)=(\det Z)^{2}\geq 0$. 此外，$F(X)=0$ 当且仅当 $Z$ 的列是线性相关的，而这当且仅当向量 $x_{1},\dots,x_{k}$ 是线性相关的。

(3). 现在我们定义 $V(X)=\sqrt{ F(X) }$，根据步骤 (1) 我们知道 $V$ 满足性质 1 和 2，同时根据步骤 (2) 我们知道 $V$ 是唯一确定的，这就完成了证明。

**定义 1.1.5** $k$-体积（$k$-volume）

设 $x_{1},\dots,x_{k}\in \mathbb{R}^{n}$ 是线性无关的，我们定义平行六面体 $\mathcal{P}(x_{1},\dots,x_{k})$ 的 $k$-**体积**为 $V(x_{1},\dots,x_{k})$.

下面我们给出一个例子。考虑 $\mathbb{R}^{3}$ 中两个线性无关的向量 $a,b$ 张成的平行四边形，则 $V(a,b)$ 就是以 $a,b$ 为边的平行四边形的面积，可以写成

$$
\begin{gather}
V(a,b)^{2}=\det \begin{bmatrix}
\lVert a \rVert ^{2} & \langle a,b \rangle  \\
\langle b,a \rangle  & \lVert b \rVert ^{2}
\end{bmatrix}=\lVert a \rVert ^{2}\lVert b \rVert ^{2}(1-\cos^{2}\theta)=\lVert a \rVert ^{2}\lVert b \rVert ^{2}\sin^{2}\theta
\end{gather}
$$

其中 $\theta$ 是 $a,b$ 之间的夹角。下图显示了 $V(a,b)$ 被称为面积的原因。

![](Vector%20Analysis/images/1-1.png)

在三维空间中，我们还有另一种方法来计算平行四边形的面积，也就是所谓的**叉积**

$$
\begin{gather}
a\times b=\det \begin{bmatrix}
a_{2} & b_{2} \\
a_{3} & b_{3}
\end{bmatrix}e_{1}-\det \begin{bmatrix}
a_{1} & b_{1} \\
a_{3} & b_{3}
\end{bmatrix}e_{2}+\det \begin{bmatrix}
a_{1} & b_{1} \\
a_{2} & b_{2}
\end{bmatrix}e_{3}
\end{gather}
$$

其长度 $\lVert a\times b \rVert$ 就等于 $\mathcal{P}(a,b)$ 的面积 $V(a,b)$，只需注意到

$$
\begin{gather}
\lVert a\times b \rVert ^{2}=\lVert a \rVert ^{2}\lVert b \rVert ^{2}-\langle a,b \rangle ^{2}
\end{gather}
$$

即可证明。

与三维空间类似，在 $\mathbb{R}^{n}$ 中，同样有两种不同的方法来计算 $k$-平行六面体的体积。一种是定理 1.1.4 中给出的公式，它非常简洁，但计算时非常不便；而另一种则可以看作是三维空间中叉积的推广，是我们在实际应用中使用的方法，下面我们来推导它。

**定义 1.1.6** 升序 $k$-元组（ascending $k$-tuple）

设 $k\leq n$，$x_{1},\dots,x_{k} \in \mathbb{R}^{n}$，令 $X$ 为矩阵 $[x_{1},\dots,x_{k}]$. 我们称 $I=(i_{1},\dots,i_{k})$ 是集合 $[n]=\{ 1,\dots,n \}$ 上的一个**升序** $k$-**元组**，如果整数 $i_{1},\dots,i_{k}$ 满足 $1\leq i_{1}<\dots<i_{k}\leq n$，并且我们用

$$
\begin{gather}
X_{I} \quad \text{或} \quad X(i_{1},\dots,i_{k})
\end{gather}
$$

来表示由 $X$ 的 $i_{1},\dots,i_{k}$ 行构成的 $k\times k$ 子矩阵。

更一般地说，设 $I$ 是 $[n]$ 上的任意 $k$-元组（不一定是升序，且可以重复），我们使用相同的记号 $X_{I}$ 来表示矩阵 $Y$ 使得 $Y$ 的第 $j$ 行是 $X$ 的第 $i_{j}$ 行。在这种情况下，$Y$ 不一定是 $X$ 的子矩阵。

**定理 1.1.7**

设 $k\leq n$，$X$ 是一个 $n\times k$ 矩阵，则有

$$
\begin{gather}
V(X)=\sqrt{ \sum_{[I]} (\det X_{I})^{2} }
\end{gather}
$$

其中 $[I]$ 表示 $I$ 遍历了 $[n]$ 上的所有升序 $k$-元组。

**证明**

设 $X=[x_{1},\dots,x_{k}]$，令

$$
\begin{gather}
F(X)=\det(X^{T}X), \quad G(X)=\sum_{[I]} (\det X_{I})^{2}
\end{gather}
$$

则我们要证 $F(X)=G(X)$ 对任意 $X$ 成立。

(1). 定理对 $k=1$ 或 $k=n$ 成立：如果 $k=1$，那么 $X$ 是列向量 $(\lambda_{1},\dots,\lambda_{n})$，于是有

$$
\begin{gather}
F(X)=\sum_{i=1}^{n} \lambda_{i}^{2}=G(X)
\end{gather}
$$

如果 $k=n$，那么 $G(X)$ 的求和中只有一项，于是有

$$
\begin{gather}
F(X)=(\det X)^{2}=G(X)
\end{gather}
$$

(2). 如果 $X$ 的列相互正交，那么我们有

$$
\begin{gather}
F(X)=\lVert x_{1} \rVert ^{2} \cdots \lVert x_{k} \rVert ^{2}
\end{gather}
$$

因为 $X^{T}X$ 的项具有形式 $x_{i}^{T}x_{j}$，根据正交性，只有对角线上的项不为零。

(3). 考虑以下两种初等列变换，其中 $j\neq\ell$：

- 交换第 $j$ 列和第 $\ell$ 列
- 将第 $\ell$ 列的 $c$ 倍加到第 $j$ 列

我们证明上述两种变换不改变 $F$ 和 $G$ 的值。

根据线性代数的知识，对矩阵进行初等列变换等价于使用初等矩阵 $E$ 右乘 $X$. 特别地，对于上面列出的两种变换，其初等矩阵满足 $\det E=\pm 1$，从而有

$$
\begin{align}
F(XE) &= \det (E^{T} X^{T} XE) \\
&= (\det E^{T}) \det(X^{T}X) (\det E) \\
&= F(X)
\end{align}
$$

对于 $G$，注意到如果我们对 $X$ 先做列变换，然后取出 $i_{1},\dots,i_{k}$ 行，这与先取出 $i_{1},\dots,i_{k}$ 行，再做列变换的结果是一致的，即

$$
\begin{gather}
(XE)_{I}=X_{I}E
\end{gather}
$$

于是我们有

$$
\begin{align}
G(XE) &= \sum_{[I]} (\det(XE)_{I})^{2} \\
&= \sum_{[I]} \det(X_{I}E)^{2} \\
&= \sum_{[I]} (\det X_{I})^{2} (\det E)^{2} \\
&= G(X)
\end{align}
$$

(4). 为了对所有矩阵证明定理，我们首先对一类特殊的矩阵进行证明：其最后一行的项除了最后一列外均为零，并且各列相互正交。

给定 $X$，如果其最后一行有非零元素，那么可以通过第 (3) 步中给出的初等列变换将 $X$ 变换为如下形式：

$$
\begin{gather}
D=\begin{bmatrix}
* \\
0 \quad \cdots \quad 0 \quad \lambda
\end{bmatrix}
\end{gather}
$$

其中 $\lambda\neq 0$. 如果 $X$ 的最后一行为全零行，那么 $X$ 自身就具有这种形式，其中 $\lambda=0$. 接下来我们对 $D$ 的列应用无归一化的 Gram-Schmidt 过程（将第 $j$ 列 $d_{j}$ 替换为 $d_{j}-\dfrac{\langle d_{1},d_{j} \rangle}{\langle d_{1},d_{1} \rangle} d_{1}-\dots-\dfrac{\langle d_{j-1},d_{j} \rangle}{\langle d_{j-1},d_{j-1} \rangle} d_{j-1}$），从而这其中只涉及第 (3) 步给出的初等列变换，并且在这一过程中矩阵最后一行的零元素不变。最终，矩阵的列相互正交，并且仍然具有形式 $D$.

(5). 我们对 $n$ 进行归纳来证明定理。

如果 $n=1$ 或 $n=2$，那么步骤 (1) 表明定理成立。现在假设定理对行数小于 $n$ 的矩阵成立。根据步骤 (1)，我们只需对 $1<k<n$ 进行证明；又根据步骤 (4)，我们可以假设 $X$ 的最后一行除了最后一列的元素外均为零，并且各列相互正交，于是 $X$ 具有形式

$$
\begin{gather}
X=\begin{bmatrix}
b_{1} & b_{2} & \cdots & b_{k} \\
0 & 0 & \cdots & \lambda
\end{bmatrix}
\end{gather}
$$

其中 $b_{i}\in \mathbb{R}^{n-1}$ 是正交向量，记 $B=[b_{1},\dots,b_{k}],C=[b_{1},\dots,b_{k-1}]$，则根据步骤 (2)，我们有

$$
\begin{gather}
F(X)=\lVert b_{1} \rVert ^{2}\cdots \lVert b_{k-1} \rVert ^{2}(\lVert b_{k} \rVert ^{2}+\lambda^{2})=F(B)+\lambda^{2}F(C)
\end{gather}
$$

为了计算 $G(X)$，我们按 $i_{k}$ 的值分成两部分：

$$
\begin{gather}
G(X)=\sum_{[I]; i_{k}<n} (\det X_{I})^{2}+\sum_{[I];i_{k}=n} (\det X_{I})^{2}
\end{gather}
$$

当 $i_{k}<n$ 时，$X_{I}=B_{I}$，因此上式的第一项为 $G(B)$. 另一方面，如果 $i_{k}=n$，则有

$$
\begin{gather}
\det X(i_{1},\dots,i_{k-1},n)=\pm \lambda \det C(i_{1},\dots,i_{k-1})
\end{gather}
$$

因此上式的第二项为 $\lambda^{2}G(C)$，从而

$$
\begin{gather}
G(X)=G(B)+\lambda^{2}G(C)
\end{gather}
$$

根据归纳假设，$F(B)=G(B),F(C)=G(C)$，于是有 $F(X)=G(X)$，这就完成了证明。

# Section 2: 参数化流形

现在我们定义参数化流形的概念，以及它对应的体积。

**定义 1.2.1** 参数化流形（parametrized manifold）

设 $k\leq n$，$A\subset \mathbb{R}^{k}$ 是开集，且 $\alpha\colon A\to \mathbb{R}^{n}$ 是 $C^{r}$ 连续函数（$r\geq 1$），则集合 $Y=\alpha[A]$ 与函数 $\alpha$ 合称为一个 $k$ 维**参数化流形**，记作 $Y_{\alpha}$. 我们定义其 $k$-体积为

$$
\begin{gather}
V(Y_{\alpha})=\int_{A} V(J_{\alpha})
\end{gather}
$$

如果右侧的积分存在，其中 $J_{\alpha}$ 是 $\alpha$ 的 Jacobian 矩阵。

下面我们使用 Riemann 积分的概念来说明上述体积定义的合理性。设 $A$ 是 $\mathbb{R}^{k}$ 中一个长方形 $Q$ 的内部，且 $\alpha\colon A\to \mathbb{R}^{n}$ 在 $Q$ 的邻域中可被扩张为一个 $C^{r}$ 函数，令 $Y=\alpha[A]$.

令 $P$ 是 $Q$ 的一个分割，取其中一个小长方形

$$
\begin{gather}
R=[a_{1},a_{1}+h_{1}]\times\dots \times[a_{k},a_{k}+h_{k}]
\end{gather}
$$

则 $\alpha$ 将 $R$ 映射到 $Y$ 上的一个曲面，而 $R$ 的各边被映射到 $Y$ 上的一条曲线，如图所示：

![](Vector%20Analysis/images/1-2.png)

对于连接 $a$ 与 $a+h_{i}e_{i}$ 的边在 $\alpha$ 下所成的像，从该曲线的起点到终点的向量由以下式子给出：

$$
\begin{gather}
\alpha(a+h_{i}e_{i})-\alpha(a)
\end{gather}
$$

它的一阶近似为向量

$$
\begin{gather}
v_{i}=\alpha'(a) h_{i}e_{i}=\dfrac{ \partial \alpha }{ \partial x_{i} } h_{i}
\end{gather}
$$

于是我们可以将向量 $v_{1},\dots,v_{k}$ 张成的平行六面体的体积作为 $\alpha[R]$ 的一个一阶近似，从而有

$$
\begin{gather}
V(v_{1},\dots,v_{k})=V\left( \dfrac{ \partial \alpha }{ \partial x_{1} },\dots,\dfrac{ \partial \alpha }{ \partial x_{k} } \right)(h_{1}\cdots h_{k})=V(J_{\alpha}) m(R)
\end{gather}
$$

当我们对所有小长方形 $R$ 进行求和时，我们就给出了积分

$$
\begin{gather}
\int_{A} V(J_{\alpha})
\end{gather}
$$

的一个近似。当分割 $P$ 越来越精细时，求和的结果就越接近积分。

下面我们定义在参数化流形上的积分。

**定义 1.2.2**

设 $A\subset \mathbb{R}^{k}$ 是开集，$\alpha\colon A\to \mathbb{R}^{n}$ 是 $C^{r}$ 函数，$Y=\alpha[A]$，$f\colon Y\to \mathbb{R}$ 是连续函数，我们定义 $Y_{\alpha}$ 上 $f$ 关于 $k$-体积的**积分**为

$$
\begin{gather}
\int_{Y_{\alpha}} f\mathrm{d} V=\int_{A} (f\circ\alpha) V(J_{\alpha})
\end{gather}
$$

如果右侧的积分存在。

特别地，我们有

$$
\begin{gather}
V(Y_{\alpha})=\int_{Y_{\alpha}}\mathrm{d} V=\int_{A} V(J_{\alpha})
\end{gather}
$$

现在我们来证明上述定义关于“重参数化”是不变的。

**定义 1.2.3** 微分同胚（diffeomorphism）

设 $A,B\subset \mathbb{R}^{n}$ 是开集，称双射 $g\colon A\to B$ 是一个 $C^{r}$ **微分同胚**，如果 $g$ 和 $g^{-1}$ 都是 $C^{r}$ 连续的。

**定理 1.2.4**

设 $A,B\subset \mathbb{R}^{k}$ 是开集，$g\colon A\to B$ 是一个 $C^{r}$ 微分同胚，令 $\beta\colon B\to \mathbb{R}^{n}$ 是 $C^{r}$ 函数，$Y=\beta[B]$；再令 $\alpha=\beta \circ g$，则 $\alpha\colon A\to \mathbb{R}^{n}$ 且 $Y=\alpha[A]$. 如果 $f\colon Y\to \mathbb{R}$ 是一个连续函数，那么 $f$ 在 $Y_{\beta}$ 上可积当且仅当它在 $Y_{\alpha}$ 上可积，此时有

$$
\begin{gather}
\int_{Y_{\alpha}}f\mathrm{d} V=\int_{Y_{\beta}}f\mathrm{d} V
\end{gather}
$$

特别地，有 $V(Y_{\alpha})=V(Y_{\beta})$.

**证明**

我们要证

$$
\begin{gather}
\int_{B} (f\circ \beta)V(J_{\beta})=\int_{A} (f\circ\alpha) V(J_{\alpha})
\end{gather}
$$

其中一个积分存在当且仅当另一个也存在。根据积分换元公式，我们有

$$
\begin{gather}
\int_{B}(f\circ\beta)V(J_{\beta})=\int_{A}(f\circ\beta \circ g)(V(J_{\beta})\circ g) |\det g'|
\end{gather}
$$

由于 $\beta \circ g=\alpha$，故我们只需证明 $(V(J_{\beta})\circ g)|\det g'|=V(J_{\alpha})$.

任取 $x \in A$，令 $y=g(x)$，根据链式法则有

$$
\begin{gather}
J_{\alpha}(x)=J_{\beta}(y)J_{g}(x)
\end{gather}
$$

从而

$$
\begin{gather}
V(J_{\alpha}(x))^{2}=\det[J_{g}(x)^{T} J_{\beta}(y)^{T}J_{\beta}(y)J_{g}(x)]=(\det J_{g}(x))^{2} V(J_{\beta}(y))^{2}
\end{gather}
$$

这就完成了证明。

下面我们考虑两个例子。

设 $A\subset \mathbb{R}^{1}$ 是一个开区间，$\alpha\colon A\to \mathbb{R}^{n}$ 是 $C^{r}$ 函数，$Y=\alpha[A]$，则我们称 $Y_{\alpha}$ 是 $\mathbb{R}^{n}$ 中的一条**参数曲线**，其 1-体积通常称为其长度，由下式给出：

$$
\begin{gather}
V(Y_{\alpha})=\int_{A} V(J_{\alpha})=\int_{A} \sqrt{ \left( \dfrac{ \partial \alpha_{1} }{ \partial t }  \right)^{2}+\dots+\left( \dfrac{ \partial \alpha_{n} }{ \partial t }  \right)^{2} }
\end{gather}
$$

这是因为 $J_{\alpha}$ 为列向量 $\left( \dfrac{ \partial \alpha_{1} }{ \partial t },\dots,\dfrac{ \partial \alpha_{n} }{ \partial t } \right)$，当 $n=3$ 时，上式就给出了曲线的弧长公式。

再设 $A$ 是 $\mathbb{R}^{2}$ 中的开集，$\alpha\colon A\to \mathbb{R}^{n}$ 是 $C^{r}$ 函数，$Y=\alpha[A]$，则称 $Y_{\alpha}$ 是一个**参数曲面**，其 2-体积通常称为其面积。

我们主要考虑 $\mathbb{R}^{3}$ 中的参数曲面，此时其面积由下式给出：

$$
\begin{gather}
V(Y_{\alpha})=\int_{A} V(J_{\alpha})=\int_{A} \left\lVert  \dfrac{ \partial \alpha }{ \partial x } \times \dfrac{ \partial \alpha }{ \partial y }   \right\rVert 
\end{gather}
$$

特别地，当 $\alpha(x,y)=(x,y,f(x,y))$ 时（即 $Y$ 是 $C^{r}$ 函数 $f$ 的图像时），我们有

$$
\begin{gather}
J_{\alpha}=\begin{bmatrix}
1 & 0 \\
0 & 1 \\
\dfrac{ \partial f }{ \partial x }  & \dfrac{ \partial f }{ \partial y } 
\end{bmatrix}
\end{gather}
$$

从而

$$
\begin{gather}
V(Y_{\alpha})=\int_{A} \sqrt{ 1+\left( \dfrac{ \partial f }{ \partial x }  \right)^{2}+\left( \dfrac{ \partial f }{ \partial y }  \right)^{2} }
\end{gather}
$$

这正是曲面面积的计算公式。

# Section 3: 单位分解

在正式定义流形之前，我们还需要引入一个重要的工具：**单位分解**，它允许我们将局部邻域内的性质光滑地推广至全局结构，这在流形的研究中尤为重要。

我们以几个引理开始。

**引理 1.3.1**

设 $Q$ 是 $\mathbb{R}^{n}$ 中的一个长方形，则存在 $C^{\infty}$ 函数 $\phi\colon \mathbb{R}^{n}\to \mathbb{R}$ 使得当 $x \in \mathrm{Int}(Q)$ 时有 $\phi(x)>0$，在其余部分则有 $\phi(x)=0$.

**证明**

定义函数 $f\colon \mathbb{R}\to \mathbb{R}$ 如下：

$$
\begin{gather}
f(x)=\begin{cases}
e^{ -1/x } & , x>0 \\
0 & ,\mathrm{otherwise}
\end{cases}
\end{gather}
$$

根据一元函数微分学，$f$ 是 $C^{\infty}$ 连续的。定义

$$
\begin{gather}
g(x)=f(x)f(1-x)
\end{gather}
$$

则 $g$ 是 $C^{\infty}$ 函数，且当 $0<x<1$ 时有 $g(x)>0$，而在其余情况下 $g(x)=0$. 最后，如果

$$
\begin{gather}
Q=[a_{1},b_{1}]\times\dots \times[a_{n},b_{n}]
\end{gather}
$$

取

$$
\begin{gather}
\phi(x)=g\left( \dfrac{x-a_{1}}{b_{1}-a_{1}} \right)\cdots g\left( \dfrac{x-a_{n}}{b_{n}-a_{n}} \right)
\end{gather}
$$

即可。

**引理 1.3.2**

设 $\mathcal{A}$ 是 $\mathbb{R}^{n}$ 中的开集族，$A=\bigcup \mathcal{A}$，则存在可数个长方形 $Q_{j}\subset A$ 满足以下条件：

1. 开集族 $\{ \mathrm{Int}(Q_{j}) \}$ 覆盖 $A$
2. 每个 $Q_{j}$ 都包含于 $\mathcal{A}$ 的一个元素中
3. $A$ 中的每个点都存在一个邻域使得它只和有限个 $Q_{j}$ 相交

**证明**

(1). 设 $D_{1},D_{2},\dots$ 是一列紧致集，其并集为 $A$，且满足 $D_{i}\subset \mathrm{Int}(D_{i+1})$，定义

$$
\begin{gather}
B_{i}=D_{i}\setminus \mathrm{Int}(D_{i-1}) \quad (D_{0}=\varnothing)
\end{gather}
$$

由于 $B_{i}\subset D_{i}$，故 $B_{i}$ 是有界的，又因为 $B_{i}$ 是两个闭集 $D_{i}$ 和 $\mathrm{Int}(D_{i-1})^{c}$ 的交集，故 $B_{i}$ 是闭的，从而是紧致的。此外，$B_{i}$ 与 $D_{i-2}$ 不相交，因为 $D_{i-2}\subset \mathrm{Int}(D_{i-1})$. 现在，任取 $x \in B_{i}$，取正方体 $C_{x}$ 使得它包含于 $\mathcal{A}$ 的一个元素中（从而 $C_{x}\subset A$）并且与 $D_{i-2}$ 不相交，如图所示：

![](Vector%20Analysis/images/1-3.png)

所有正方体 $C_{x}$ 的内部覆盖了 $B_{i}$，从中我们取有限个组成集族 $\mathcal{C}_{i}$.

(2). 令

$$
\begin{gather}
\mathcal{C}=\bigcup_{i=1}^{\infty} \mathcal{C}_{i}
\end{gather}
$$

则 $\mathcal{C}$ 是正方体的可数集合，我们来证明 $\mathcal{C}$ 满足所求的三个条件。

根据构造，每个 $\mathcal{C}$ 中的元素均包含于 $\mathcal{A}$ 的元素中，这证明了 2. 任取 $x \in A$，令 $i$ 为满足 $x \in \mathrm{Int}(D_{i})$ 的最小整数，于是有 $x \in B_{i}=D_{i}\setminus \mathrm{Int}(D_{i-1})$，由于 $\mathcal{C}_{i}$ 覆盖了 $B_{i}$，故存在正方体 $Q$ 使得 $x \in \mathrm{Int}(Q)$，这证明了 1.

最后我们来证明 3. 给定 $x \in A$，存在 $i$ 使得 $x \in \mathrm{Int}(D_{i})$，根据构造，集合 $\mathcal{C}_{i+2},\mathcal{C}_{i+3},\dots$ 中的元素与 $D_{i}$ 是不相交的，因此，与开集 $\mathrm{Int}(D_{i})$ 有交集的正方体只有 $\mathcal{C}_{1},\dots,\mathcal{C}_{i+1}$ 中的有限个元素，这就完成了证明。

接下来我们来证明本节的主定理：光滑单位分解的存在性。

**定理 1.3.3**

设 $\mathcal{A}$ 是 $\mathbb{R}^{n}$ 中的开集族，$A=\bigcup \mathcal{A}$，则存在一列连续函数 $\phi_{i}\colon \mathbb{R}^{n}\to \mathbb{R}$ 满足以下条件：

1. 对任意 $x$ 有 $\phi_{i}(x)\geq 0$
2. $\mathrm{supp}(\phi_{i})\subset A$
3. $A$ 中的每个点都存在一个邻域使得它只和有限个 $\mathrm{supp}(\phi_{i})$ 相交
4. 对任意 $x \in A$ 有 $\sum_{i=1}^{\infty}\phi_{i}(x)=1$
5. $\phi_{i}$ 是 $C^{\infty}$ 连续的
6. $\mathrm{supp}(\phi_{i})$ 是紧致集
7. 每个 $\mathrm{supp}(\phi_{i})$ 都包含于 $\mathcal{A}$ 的一个元素中

满足条件 1-4 的函数集合 $\{ \phi_{i} \}$ 称为一个**单位分解**，进一步，满足条件 6 的称为**紧支撑的**，而满足条件 7 的则称为**受**开集族 $\mathcal{A}$ 的**控制**。

**证明**

给定 $\mathcal{A}$ 和 $A$，令 $\{ Q_{j} \}$ 为引理 1.3.2 中所示的长方形集合，再根据引理 1.3.1，取 $C^{\infty}$ 函数 $\psi_{i}\colon \mathbb{R}^{n}\to \mathbb{R}$ 使得它在 $\mathrm{Int}(Q_{i})$ 上为正，在其余部分为零，则对任意 $x$ 有 $\psi_{i}(x)\geq 0$. 此外，$\mathrm{supp}(\psi_{i})=Q_{i}$ 为紧致集，并且其包含于 $\mathcal{A}$ 的一个元素中。最后，$A$ 中的每个点都存在一个邻域使得它只和有限个 $Q_{i}$ 相交，因此 $\{ \psi_{i} \}$ 满足除了条件 4 外的所有条件。

条件 3 表明，对任意 $x \in A$，存在 $x$ 的一个邻域使得在其中只有有限个 $\psi_{1}(x),\psi_{2}(x),\dots$ 不为零，因此级数

$$
\begin{gather}
\psi(x)=\sum_{i=1}^{\infty} \psi_{i}(x)
\end{gather}
$$

收敛。又因为每个 $x \in A$ 都存在一个邻域，在其上 $\psi$ 等于有限个 $C^{\infty}$ 函数的和，故 $\psi$ 也是 $C^{\infty}$ 函数。最后，对任意 $x \in A$，存在长方形 $Q_{i}$ 使得 $x \in \mathrm{Int}(Q_{i})$，从而 $\psi_{i}(x)>0$，因此 $\psi(x)>0$，定义

$$
\begin{gather}
\phi_{i}(x)=\dfrac{\psi_{i}(x)}{\psi(x)}
\end{gather}
$$

即得 $\sum_{i=1}^{\infty}\phi_{i}(x)=1$ 对任意 $x \in A$ 均成立。

下面我们就用单位分解来证明一些基础结论。

**定义 1.3.4** $C^{r}$ 连续

设 $S\subset \mathbb{R}^{k}$，称函数 $f\colon S\to \mathbb{R}^{n}$ 在 $S$ 上是 $C^{r}$ **连续**的，如果 $f$ 可以扩张为 $g\colon U\to \mathbb{R}^{n}$ 使得 $g$ 在包含 $S$ 的开集 $U$ 上 $C^{r}$ 连续。

根据上述定义，两个 $C^{r}$ 函数的复合仍然是 $C^{r}$ 函数：设 $S\subset \mathbb{R}^{k}$，$f_{1}\colon S\to \mathbb{R}^{n}$ 是 $C^{r}$ 函数，再设 $f_{1}[S]\subset T\subset \mathbb{R}^{n}$，$f_{2}\colon T\to \mathbb{R}^{p}$ 是 $C^{r}$ 函数，则我们可以将其扩张为 $C^{r}$ 函数 $g_{1}\colon U\to \mathbb{R}^{n}$ 和 $g_{2}\colon V\to \mathbb{R}^{p}$，于是 $g_{2}\circ g_{1}$ 就是一个定义在开集 $g_{1}^{-1}[V]\supset S$ 上的 $f_{2}\circ f_{1}$ 的 $C^{r}$ 扩张。

下面的引理表明：一个函数是 $C^{r}$ 连续的当且仅当它在局部是 $C^{r}$ 连续的。

**引理 1.3.5**

设 $S\subset \mathbb{R}^{k}$，$f\colon S\to \mathbb{R}^{n}$，如果对任意 $x \in S$，存在 $x$ 的邻域 $U_{x}$ 以及 $C^{r}$ 函数 $g_{x}\colon U_{x}\to \mathbb{R}^{n}$ 使得在 $U_{x}\cap S$ 上有 $f=g_{x}$，那么 $f$ 在 $S$ 上是 $C^{r}$ 函数。

**证明**

开集族 $\{ U_{x} \}$ 覆盖了 $S$，令 $A$ 为它们的并集，那么我们可以取单位分解 $\{ \phi_{i} \}$ 使得它受 $\{ U_{x} \}$ 的控制。对任意 $i$，取开集 $U_{x}$ 使得 $\mathrm{supp}(\phi_{i})\subset U_{x}$，并令 $g_{i}$ 为 $C^{r}$ 函数 $g_{x}\colon U_{x}\to \mathbb{R}^{n}$，则函数 $\phi_{i}g_{i}\colon U_{x}\to \mathbb{R}^{n}$ 在 $U_{x}$ 的一个闭子集之外消失。通过在 $A\setminus U_{x}$ 上取零值，我们可以将其扩张为 $C^{r}$ 函数 $h_{i}\colon A\to \mathbb{R}^{n}$，下面我们定义

$$
\begin{gather}
g(x)=\sum_{i=1}^{\infty} h_{i}(x)
\end{gather}
$$

对任意 $x \in A$，存在 $x$ 的一个邻域使得在其上只有有限个 $h_{i}\neq 0$，因此，$g$ 作为有限个 $C^{r}$ 函数的和也是 $C^{r}$ 连续的。此外，对任意 $x \in S$，有

$$
\begin{gather}
h_{i}(x)=\phi_{i}(x)g_{i}(x)=\phi_{i}(x)f(x)
\end{gather}
$$

对任意满足 $\phi_{i}(x)\neq 0$ 的 $i$ 成立，于是我们有

$$
\begin{gather}
g(x)=\sum_{i=1}^{\infty} \phi_{i}(x)f(x)=f(x)
\end{gather}
$$

这就完成了证明。

从上述定理证明中我们可以看出，单位分解充当了局部结构的“粘合剂”，能够将局部邻域内的性质推广至全局结构。

# Section 4: 流形

现在我们可以定义一般意义上的流形结构。我们记上半空间 $\mathbb{H}^{k}$ 为所有满足 $x_{k}\geq 0$ 的 $x \in \mathbb{R}^{k}$ 构成的集合，上半开空间 $\mathbb{H}_{+}^{k}$ 为满足 $x_{k}>0$ 的 $x \in \mathbb{R}^{k}$ 构成的集合。我们对在 $\mathbb{H}^{k}$ 中开而在 $\mathbb{R}^{k}$ 中不开的集合特别感兴趣，在这种情况下，我们有如下引理：

**引理 1.4.1**

设 $U$ 在 $\mathbb{H}^{k}$ 中是开集而在 $\mathbb{R}^{k}$ 中不是，$\alpha\colon U\to \mathbb{R}^{n}$ 是 $C^{r}$ 函数，令 $\beta\colon U'\to \mathbb{R}^{n}$ 是一个定义在 $\mathbb{R}^{k}$ 中的开集 $U'$ 上的 $\alpha$ 的扩张，则对任意 $x \in U$，导数 $\beta'(x)$ 只和函数 $\alpha$ 有关而与扩张 $\beta$ 无关。

这一引理允许我们定义 $\alpha$ 的导数 $\alpha'(x)=\beta'(x)$.

**证明**

由于引理中涉及的函数均连续可导，故我们有偏导数等于单侧极限

$$
\begin{gather}
\dfrac{ \partial \beta }{ \partial x_{j} }(x) =\lim_{ h \to 0+ } \dfrac{\beta(x+he_{j})-\beta(x)}{h}
\end{gather}
$$

当 $x \in U\subset \mathbb{H}^{k}$ 时，$x+he_{j}$ 也属于 $\mathbb{H}^{k}$，当 $h$ 足够小时，我们就有 $\beta(x+he_{j})-\beta(x)=\alpha(x+he_{j})-\alpha(x)$，从而 $\dfrac{ \partial \beta }{ \partial x_{j} }$ 只和 $\alpha$ 有关，这就完成了证明。

**定义 1.4.2** 流形（manifold）

设 $k>0$，称 $M\subset \mathbb{R}^{n}$ 是一个 $C^{r}$ 连续的 $k$-**流形**，如果其满足：对任意 $p \in M$，存在 $M$ 中包含 $p$ 的开集 $V$，在 $\mathbb{R}^{k}$ 或者 $\mathbb{H}^{k}$ 中开的集合 $U$，以及一个连续双射 $\alpha\colon U\to V$ 使得：

1. $\alpha$ 是 $C^{r}$ 连续的
2. $\alpha^{-1}\colon V\to U$ 是连续函数
3. 对任意 $x \in U$，矩阵 $J_{\alpha}(x)$ 的秩为 $k$

函数 $\alpha$ 称为 $M$ 上关于 $p$ 的**坐标卡**（coordinate patch）。如果 $M$ 上所有坐标卡的定义域均在 $\mathbb{R}^{k}$ 上是开的，则称 $M$ 是一个**无边界** $k$-**流形**。

我们定义 $\mathbb{R}^{n}$ 上的离散点集为一个 $0$-流形。

我们以一个例子来说明上述定义。

考虑情形 $k=2$，矩阵 $J_{\alpha}(x)$ 的秩为 $2$ 的条件表明，它的列 $\dfrac{ \partial \alpha }{ \partial x_{1} }$ 和 $\dfrac{ \partial \alpha }{ \partial x_{2} }$ 是线性无关的。注意到偏导数 $\dfrac{ \partial \alpha }{ \partial x_{j} }$ 是曲线 $f(t)=\alpha(x+te_{j})$ 的速度向量，从而与曲面 $M$ 是相切的，进而我们可知 $\dfrac{ \partial \alpha }{ \partial x_{1} }$ 与 $\dfrac{ \partial \alpha }{ \partial x_{2} }$ 在 $x$ 点处张成了 $M$ 的一个切平面，如图所示：

![](Vector%20Analysis/images/1-4.png)

同时，在图上我们也可以看出，在流形 $M$ 上存在两类点，其中一类有类似于开球的邻域（图中上方），另一类有类似于半开球的邻域（图中下方），后者组成了我们称之为“边界”的集合。关于边界的严格数学表述将在下一节定义。

我们以一个基础结论结束本节。

**引理 1.4.3**

设 $M\subset \mathbb{R}^{n}$ 是一个流形，$\alpha\colon U\to V$ 是 $M$ 上的坐标卡，如果 $U_{0}$ 是 $U$ 中的开集，那么 $\alpha|_{U_{0}}$ 也是 $M$ 上的坐标卡。

**证明**

由于 $U_{0}$ 是开集而 $\alpha^{-1}$ 连续，故 $V_{0}=\alpha[U_{0}]$ 在 $V$ 中是开的，于是 $U_{0}$ 在 $\mathbb{R}^{k}$ 或 $\mathbb{H}^{k}$ 中是开的（取决于 $U$ 在 $\mathbb{R}^{k}$ 还是 $\mathbb{H}^{k}$ 中是开的），且 $V_{0}$ 在 $M$ 中是开的，从而 $\alpha|_{U_{0}}$ 是坐标卡：它是 $U_{0}$ 到 $V_{0}$ 的双射；它是 $C^{r}$ 连续的因为 $\alpha$ 是；它的反函数是连续的，因为它只是 $\alpha^{-1}$ 的限制；并且其导数的秩为 $k$ 因为 $J_{\alpha}$ 也是。

# Section 5: 流形的边界

在本节中，我们将明确一个流形的边界的精确表述，并证明一个用于构造流形的有用定理。首先，我们来证明坐标卡的一个重要性质。

**定理 1.5.1**

设 $M\subset\mathbb{R}^{n}$ 是 $C^{r}$ 连续的 $k$-流形，$\alpha_{0}\colon U_{0}\to V_{0}$ 和 $\alpha_{1}\colon U_{1}\to V_{1}$ 是 $M$ 上的坐标卡，其中 $W=V_{0}\cap V_{1}\neq \varnothing$，令 $W_{i}=\alpha_{i}^{-1}[W]$，则函数

$$
\begin{gather}
\alpha_{1}^{-1}\circ\alpha_{0}\colon W_{0}\to W_{1}
\end{gather}
$$

是 $C^{r}$ 连续的，并且其导数可逆。

我们通常称 $\alpha_{1}^{-1}\circ\alpha_{0}$ 为坐标卡 $\alpha_{0}$ 与 $\alpha_{1}$ 之间的**转移函数**，一些典型例子如图所示。

![](Vector%20Analysis/images/1-5.png)

**证明**

我们需要证明如果 $\alpha\colon U\to V$ 是 $M$ 上的坐标卡，那么 $\alpha^{-1}\colon V\to \mathbb{R}^{k}$ 是一个 $C^{r}$ 函数，从而我们可知，由于 $\alpha_{0}$ 和 $\alpha_{1}^{-1}$ 是 $C^{r}$ 函数，其复合 $\alpha_{1}^{-1}\circ\alpha_{0}$ 也是；同理 $\alpha_{0}^{-1}\circ\alpha_{1}$ 也是 $C^{r}$ 函数，从而链式法则表明这两个转移函数均有可逆的导数。

为证明 $\alpha^{-1}$ 是 $C^{r}$ 函数，根据引理 1.3.5，我们只需证明它是局部 $C^{r}$ 连续的。设 $p_{0}\in V$，$x_{0}=\alpha^{-1}(p_{0})$，我们证明 $\alpha^{-1}$ 在 $p_{0}$ 的邻域内等于一个 $C^{r}$ 函数。

我们首先考虑 $U$ 在 $\mathbb{H}^{k}$ 中开而在 $\mathbb{R}^{k}$ 中不开的情况。根据假设，我们可以将 $\alpha$ 扩张为定义在开集 $U'$ 上的 $C^{r}$ 函数 $\beta$，由于 $J_{\alpha}(x_{0})$ 的秩为 $k$，我们可以不失一般性地假设前 $k$ 行是线性无关的。令 $\pi\colon \mathbb{R}^{n}\to \mathbb{R}^{k}$ 是将 $x \in \mathbb{R}^{n}$ 投影至前 $k$ 个坐标的映射，则函数 $g=\pi \circ\beta\colon U'\to \mathbb{R}^{k}$ 的导数可逆，从而根据反函数定理，$g$ 是一个从 $x_{0}$ 的邻域 $W$ 到 $\mathbb{R}^{k}$ 中的开集的 $C^{r}$ 微分同胚。

![](1-6.png)

我们来证明 $C^{r}$ 函数 $h=g^{-1}\circ \pi$ 就是要求的 $\alpha^{-1}$ 的扩张。由于 $U_{0}=W\cap U$ 在 $U$ 中是开的，故 $V_{0}=\alpha[U_{0}]$ 在 $V$ 中也是开的，这表明存在开集 $A\subset \mathbb{R}^{n}$ 使得 $A\cap V=V_{0}$，通过与 $\pi^{-1}[g[W]]$ 取交集，我们可以选取 $A$ 使得它包含于 $h$ 的定义域中，从而 $h\colon A\to \mathbb{R}^{k}$ 是 $C^{r}$ 连续的。任取 $p \in V_{0}$，令 $x=\alpha^{-1}(p)$，则有

$$
\begin{gather}
h(p)=h(\alpha(x))=g^{-1}(\pi(\alpha(x)))=g^{-1}(g(x))=x=\alpha^{-1}(p)
\end{gather}
$$

即证。

当 $U$ 在 $\mathbb{R}^{k}$ 中开时，我们取 $U'=U$ 和 $\beta=\alpha$ 并重复上面的论证即可。

现在我们来定义流形的边界是什么。

**定义 1.5.2** 边界（boundary）

设 $M$ 是 $\mathbb{R}^{n}$ 中的 $k$-流形，$p \in M$，如果存在 $p$ 处的坐标卡 $\alpha\colon U\to V$ 使得 $U$ 在 $\mathbb{R}^{k}$ 中开，则称 $p$ 是 $M$ 的**内部点**；否则就称 $p$ 是 $M$ 的**边界点**。所有内部点构成的集合记作 $\mathrm{Int}(M)$，称为 $M$ 的**内部**；所有边界点构成的集合记作 $\partial M$，称为 $M$ 的**边界**。

注意，上述定义中的“内部”和“边界”与点集拓扑学中集合的内部与边界是无关的，因此，当看到类似 $\partial M$ 的符号时，需要明确是 $M$ 作为流形的边界还是 $M$ 作为集合的边界，在大多数情况下，这种区分可以从上下文中推导出来。

对于一个流形，我们可以通过以下判别法检测边界点：

**引理 1.5.3**

设 $M$ 是 $\mathbb{R}^{n}$ 中的 $k$-流形，$\alpha\colon U\to V$ 是 $M$ 上点 $p$ 处的坐标卡，那么：

1. 如果 $U$ 在 $\mathbb{R}^{k}$ 中开，则 $p$ 是 $M$ 的内部点
2. 如果 $U$ 在 $\mathbb{H}^{k}$ 中开，且有 $x_{0}\in \mathbb{H}_{+}^{k}$ 使得 $p=\alpha(x_{0})$，则 $p$ 是 $M$ 的内部点
3. 如果 $U$ 在 $\mathbb{H}^{k}$ 中开，且有 $x_{0}\in \mathbb{R}^{k-1}\times 0$ 使得 $p=\alpha(x_{0})$，则 $p$ 是 $M$ 的边界点

**证明**

从定义中可直接得到 1. 对于 2，令 $U_{0}=U\cap \mathbb{H}_{+}^{k}$ 且 $V_{0}=\alpha[U_{0}]$，则 $\alpha|_{U_{0}}\colon U_{0}\to V_{0}$ 是 $p$ 处的坐标卡，且 $U_{0}$ 在 $\mathbb{R}^{k}$ 中是开的。

我们来证明 3. 设 $\alpha_{0}\colon U_{0}\to V_{0}$ 是 $p$ 处的坐标卡，$U_{0}$ 在 $\mathbb{H}^{k}$ 中开，且 $p=\alpha_{0}(x_{0}),x_{0}\in \mathbb{R}^{k-1}\times 0$. 假设有 $p$ 处的坐标卡 $\alpha_{1}\colon U_{1}\to V_{1}$ 使得 $U_{1}$ 在 $\mathbb{R}^{k}$ 中开，我们需要导出一个矛盾。

由于 $V_{0},V_{1}$ 在 $M$ 中是开的，则 $W=V_{0}\cap V_{1}$ 在 $M$ 中也是开的。令 $W_{i}=\alpha_{i}^{-1}[W]$，则 $W_{0}$ 在 $\mathbb{H}^{k}$ 中开并且包含 $x_{0}$，$W_{1}$ 在 $\mathbb{R}^{k}$ 中开。定理 1.5.1 表明转移函数

$$
\begin{gather}
\alpha_{0}^{-1}\circ\alpha_{1}\colon W_{1}\to W_{0}
\end{gather}
$$

是一个 $C^{r}$ 微分同胚，从而其像集 $W_{0}$ 在 $\mathbb{R}^{k}$ 中也是开的。然而，$W_{0}\subset \mathbb{H}^{k}$ 且包含 $x_{0}\in \mathbb{R}^{k-1}\times 0$，因此它在 $\mathbb{R}^{k}$ 中不是开的。这是一个矛盾，因此 $p$ 是 $M$ 的边界点，这就完成了证明。

注意到 $\mathbb{H}^{k}$ 自身是 $\mathbb{R}^{k}$ 中的 $k$-流形，根据上述引理，其边界正是 $\partial \mathbb{H}^{k}=\mathbb{R}^{k-1}\times 0$.

**定理 1.5.4**

设 $M\subset \mathbb{R}^{n}$ 是 $C^{r}$ 连续的 $k$-流形，如果 $\partial M\neq \varnothing$，那么 $\partial M$ 是一个 $C^{r}$ 连续的无边界 $k-1$ 流形。

**证明**

令 $p \in \partial M$，$\alpha\colon U\to V$ 是 $p$ 处的坐标卡，则 $U$ 在 $\mathbb{H}^{k}$ 中开并且有 $x_{0}\in \partial \mathbb{H}^{k}$ 使得 $p=\alpha(x_{0})$. 根据引理 1.5.3，每个 $U\cap \mathbb{H}_{+}^{k}$ 中的点都被 $\alpha$ 映射到 $M$ 的内部，而每个 $U\cap \partial \mathbb{H}^{k}$ 中的点都被 $\alpha$ 映射到 $\partial M$. 因此，$\alpha$ 在 $U\cap \partial \mathbb{H}^{k}$ 上的限制是 $U\cap \partial \mathbb{H}^{k}$ 到 $\partial M$ 中的开集 $V_{0}=V\cap \partial M$ 的双射。

令 $U_{0}$ 是 $\mathbb{R}^{k-1}$ 中的开集使得 $U_{0}\times 0=U\cap \partial \mathbb{H}^{k}$，如果 $x \in U_{0}$，定义 $\alpha_{0}(x)=\alpha(x,0)$，则 $\alpha_{0}\colon U_{0}\to V_{0}$ 是 $\partial M$ 上的坐标卡：它是 $C^{r}$ 连续的因为 $\alpha$ 是；它导数的秩为 $k-1$，因为 $J_{\alpha_{0}}(x)$ 是 $J_{\alpha}(x,0)$ 的前 $k-1$ 列；反函数 $\alpha_{0}^{-1}$ 是连续的，因为它等于 $\alpha^{-1}$ 在 $V_{0}$ 上的限制与向前 $k-1$ 个坐标投影的函数 $\pi$ 的复合。

上述证明中构造的坐标卡 $\alpha_{0}$ 称为 $\alpha$ 在 $\partial M$ 上的**限制**。

最后，我们证明一个常用的构造流形的方法。

**定理 1.5.5**

设 $\mathcal{O}$ 是 $\mathbb{R}^{n}$ 中的开集，$f\colon \mathcal{O}\to \mathbb{R}$ 是 $C^{r}$ 函数，令 $M=\{ x \mid f(x)=0 \}$，$N=\{ x \mid f(x)\geq 0 \}$，假设 $M\neq \varnothing$ 且 $J_{f}(x)$ 在任意 $x \in M$ 处的秩为 $1$，则 $N$ 是 $\mathbb{R}^{n}$ 上的 $n$-流形，并且 $\partial N=M$.

**证明**

首先假设 $p \in N$ 满足 $f(p)>0$，令 $U$ 为包含所有使得 $f(x)>0$ 的 $x$ 构成的开集，令 $\alpha\colon U\to U$ 为恒等映射，则显然 $\alpha$ 是 $N$ 上 $p$ 处的坐标卡，其定义域在 $\mathbb{R}^{n}$ 中开。

现在假设 $f(p)=0$，由于 $J_{f}(p)$ 的秩为 $1$，至少一个偏导数 $\dfrac{ \partial f }{ \partial x_{j} }(p)\neq 0$，不妨设 $\dfrac{ \partial f }{ \partial x_{n} }(p)\neq 0$. 定义 $F\colon \mathcal{O}\to \mathbb{R}^{n}$ 为 $F(x)=(x_{1},\dots,x_{n-1},f(x))$，则

$$
\begin{gather}
J_{F}(p)=\begin{bmatrix}
I_{n-1} & 0 \\
* & \dfrac{ \partial f }{ \partial x_{n} } (p)
\end{bmatrix}
\end{gather}
$$

因此 $J_{F}(p)$ 可逆，这表明 $F$ 是从 $p$ 的邻域 $A$ 到开集 $B\subset \mathbb{R}^{n}$ 的微分同胚。进一步，$F$ 将 $N$ 上的开集 $A\cap N$ 映射到 $\mathbb{H}^{n}$ 上的开集 $B\cap \mathbb{H}^{n}$，并将 $A\cap M$ 映射到 $B\cap \partial \mathbb{H}^{n}$，于是函数 $F^{-1}\colon B\cap \mathbb{H}^{n}\to A\cap N$ 就是所求的坐标卡。

熟悉多元微分学的读者可能已经看出，上述定理正是隐函数定理的流形重述：隐函数定理从局部的坐标进行描述，而上述定理从全局的流形性质进行描述。它们共同表达了一个本质：流形的局部区域可以确定一个隐函数。根据这种对应关系，我们写出相应于扩展版隐函数定理的流形版本。

**定理 1.5.6**

设 $f\colon \mathbb{R}^{n+k}\to \mathbb{R}^{n}$ 是 $C^{r}$ 函数，$M=\{ x \mid f(x)=0 \}$，假设 $M\neq \varnothing$ 并且 $J_{f}(x)$ 在任意 $x \in M$ 处的秩为 $n$，则 $M$ 是 $\mathbb{R}^{n+k}$ 中的无边界 $k$-流形。

**证明**

不失一般性地设 $J_{f}(x)$ 的前 $n$ 列线性无关，从而 $\dfrac{ \partial (f_{1},\dots,f_{n}) }{ \partial (x_{1},\dots,x_{n}) }$ 可逆。记 $v=(x_{1},\dots,x_{n}),u=(x_{n+1},\dots,x_{n+k})$，对 $f(v,u)=0$ 在 $x_{0}=(v_{0},u_{0})$ 处应用隐函数定理，则有包含 $u_{0}$ 的开集 $U\subset \mathbb{R}^{k}$ 和包含 $x_{0}$ 的开集 $V$，以及 $C^{r}$ 函数 $g\colon U\to \mathbb{R}^{n}$ 使得

$$
\begin{gather}
\{ x \in V \mid f(x)=0 \}=\{ (g(u),u) \mid u \in U \}
\end{gather}
$$

令 $\alpha\colon U\to M\cap V$ 为 $\alpha(u)=(g(u),u)$，则 $\alpha$ 就是所求的坐标卡。

我们以一个推论结束本节。我们称由 $\lVert x \rVert\leq a$ 的 $x \in \mathbb{R}^{n}$ 构成的集合 $B^{n}(a)$ 为半径为 $a$ 的 $n$-**球**；称由 $\lVert x \rVert=a$ 的 $x \in \mathbb{R}^{n}$ 构成的集合 $S^{n-1}(a)$ 为半径为 $a$ 的 $n-1$ **球面**。

**推论 1.5.7**

$n$-球 $B^{n}(a)$ 是一个光滑（$C^{\infty}$ 连续）的 $n$-流形，且 $S^{n-1}(a)=\partial B^{n}(a)$.

**证明**

对 $C^{\infty}$ 函数 $f(x)=a^{2}-\lVert x \rVert^{2}$ 应用定理 1.5.5，则

$$
\begin{gather}
J_{f}(x)=[-2x_{1},\dots,-2x_{n}]
\end{gather}
$$

在 $S^{n-1}(a)=\{ x \mid f(x)=0 \}$ 上 $J_{f}(x)$ 的秩为 $1$，这就完成了证明。

# Section 6: 流形上标量场的积分

本节我们来定义什么是流形 $M$ 上的标量函数 $f$ 关于体积 $V$ 的积分。在微积分中，这类积分通常称为“第一类曲线/曲面积分”，与“第二类”积分，即流形上微分形式的积分相对。对于后者我们将在后续的章节进行研究。

首先我们来定义当 $f$ 的支撑集可被单个坐标卡覆盖时的积分。

**定义 1.6.1**

设 $M\subset \mathbb{R}^{n}$ 是一个 $C^{r}$ 连续的紧致 $k$-流形，$f\colon M\to \mathbb{R}$ 是一个连续函数，令 $C=\mathrm{supp}(f)$，则 $C$ 是紧致的。假设 $\alpha\colon U\to V$ 是 $M$ 上的坐标卡使得 $C\subset V$，则 $\alpha^{-1}[C]$ 是紧致的。通过将 $U$ 替换为一个更小的开集，我们可以假设 $U$ 是有界的。定义 $f$ 在 $M$ 上关于 $V$ 的**积分**为

$$
\begin{gather}
\int_{M} f \mathrm{d} V=\int_{\mathrm{Int}(U)} (f\circ\alpha)V(J_{\alpha})
\end{gather}
$$

其中 $\mathrm{Int}(U)=U$ 如果 $U$ 在 $\mathbb{R}^{k}$ 中开；$\mathrm{Int}(U)=U\cap \mathbb{H}_{+}^{k}$ 如果 $U$ 在 $\mathbb{H}^{k}$ 中开而不在 $\mathbb{R}^{k}$ 中开。

容易看出上述定义中的积分存在：函数 $F=(f\circ\alpha)V(J_{\alpha})$ 在 $U$ 上连续，且在紧致集 $\alpha^{-1}[C]$ 外消失，因此 $F$ 是有界的，从而可积。

**引理 1.6.2**

如果 $f$ 的支撑集能被单个坐标卡覆盖，那么积分 $\int_{M}f\mathrm{d}V$ 是良定的，与坐标卡的选取无关。

**证明**

我们首先证明如下结论：设 $\alpha\colon U\to V$ 是一个包含 $\mathrm{supp}(f)$ 的坐标卡，令 $W$ 是 $U$ 中的开集使得 $\alpha[W]$ 也包含 $\mathrm{supp}(f)$，那么有

$$
\begin{gather}
\int_{\mathrm{Int}(W)} (f\circ\alpha)V(J_{\alpha})=\int_{\mathrm{Int}(U)} (f\circ\alpha)V(J_{\alpha})
\end{gather}
$$

事实上，由于 $F=(f\circ\alpha)V(J_{\alpha})$ 在 $W$ 以外消失，故 $F$ 在 $W$ 和 $U$ 上的积分相同，下面只需证明 $F$ 在 $U$ 和 $\mathrm{Int}(U)$ 上的积分相同，$W$ 上的证明同理。当 $U$ 在 $\mathbb{R}^{k}$ 中开时，$\mathrm{Int}(U)=U$，结论是平凡的；当 $U$ 在 $\mathbb{H}^{k}$ 中开而不在 $\mathbb{R}^{k}$ 中开时，有

$$
\begin{gather}
\int_{U} F-\int_{\mathrm{Int}(U)} F=\int_{U\cap \partial \mathbb{H}^{k}} F
\end{gather}
$$

又由于 $\partial \mathbb{H}^{k}$ 在 $\mathbb{R}^{k}$ 中具有测度零，故右侧的积分消失，两个积分相同。

现在设 $\alpha_{i}\colon U_{i}\to V_{i}, i=0,1$ 是 $M$ 上的坐标卡使得 $V_{0},V_{1}$ 均包含 $\mathrm{supp}(f)$. 我们想证明

$$
\begin{gather}
\int_{\mathrm{Int}(U_{0})} (f\circ\alpha_{0})V(J_{\alpha_{0}})=\int_{\mathrm{Int}(U_{1})} (f\circ\alpha_{1})V(J_{\alpha_{1}})
\end{gather}
$$

令 $W=V_{0}\cap V_{1}$，$W_{i}=\alpha_{i}^{-1}[W]$，根据上面的结论，我们只需在 $W_{0},W_{1}$ 上证明等式。由于 $\alpha_{1}^{-1}\circ\alpha_{0}\colon \mathrm{Int}(W_{0})\to \mathrm{Int}(W_{1})$ 是一个微分同胚，故根据定理 1.2.4 即证。

为了定义一般意义上的积分 $\int_{M} f\mathrm{d}V$，我们使用 $M$ 上的单位分解。

**引理 1.6.3**

设 $M\subset \mathbb{R}^{n}$ 是一个 $C^{r}$ 连续的紧致 $k$-流形，给定覆盖 $M$ 的一族坐标卡 $\mathcal{A}$，存在有限个 $C^{\infty}$ 函数 $\phi_{1},\dots,\phi_{\ell}\colon \mathbb{R}^{n}\to \mathbb{R}$ 满足：

1. 对任意 $x$ 有 $\phi_{i}(x)\geq 0$
2. 对任意 $i$，集合 $\mathrm{supp}(\phi_{i})$ 是紧致集，且存在坐标卡 $\alpha_{i}\colon U_{i}\to V_{i}$ 属于给定的 $\mathcal{A}$ 使得 $\mathrm{supp}(\phi_{i})\cap M\subset V_{i}$
3. 对 $x \in M$ 有 $\sum_{i=1}^{\ell}\phi(x)=1$

我们称 $\{ \phi_{1},\dots,\phi_{\ell} \}$ 是 $M$ 上受 $\mathcal{A}$ 控制的单位分解。

**证明**

对任意坐标卡 $\alpha\colon U\to V$ 属于 $\mathcal{A}$，选取开集 $A_{V}$ 使得 $A_{V}\cap M=V$，令 $A$ 为所有 $A_{V}$ 的并集，选取 $A$ 上的单位分解使得其受开覆盖 $\{ A_{V} \}$ 的控制。对任意 $x \in M$，存在它的邻域 $U_{x}$ 使其只和有限个 $\mathrm{supp}(\phi_{i})$ 相交，这些 $U_{x}$ 构成了 $M$ 的一个开覆盖。由紧致性，我们可以选取有限个邻域 $U_{x}$，从而在 $M$ 上仅有有限个 $\phi_{i}$ 不恒等于零，这些 $\phi_{i}$ 就是我们所要求的。

**定义 1.6.4**

设 $M\subset \mathbb{R}^{n}$ 是一个 $C^{r}$ 连续的紧致 $k$-流形，$f\colon M\to \mathbb{R}$ 是一个连续函数，取 $M$ 上的单位分解 $\phi_{1},\dots,\phi_{\ell}$ 使其受 $M$ 上所有坐标卡的控制。定义 $f$ 在 $M$ 上关于 $V$ 的**积分**为

$$
\begin{gather}
\int_{M} f\mathrm{d} V=\sum_{i=1}^{\ell} \int_{M} \phi_{i} f\mathrm{d} V
\end{gather}
$$

并定义 $M$ 的 $k$ 维**体积**为

$$
\begin{gather}
V(M)=\int_{M} 1\mathrm{d} V
\end{gather}
$$

上述定义在 $f$ 的支撑集被单个坐标卡覆盖时与之前的定义是相容的：记 $A=\mathrm{Int}(U)$，则有

$$
\begin{align}
\sum_{i=1}^{\ell} \int_{M} \phi_{i}f\mathrm{d} V &= \sum_{i=1}^{\ell} \int_{A} (\phi_{i}\circ\alpha)(f\circ\alpha)V(J_{\alpha}) \\
&= \int_{A} \sum_{i=1}^{\ell} (\phi_{i}\circ\alpha)(f\circ\alpha) V(J_{\alpha}) \\
&= \int_{A} (f\circ\alpha) V(J_{\alpha}) \\
&= \int_{M} f\mathrm{d} V
\end{align}
$$

我们还可以注意到，上述定义与单位分解的取法是无关的：设 $\psi_{1},\dots \psi_{m}$ 是另一个单位分解，由于 $\psi_{j}f$ 的支撑集被单个坐标卡覆盖，我们可以应用前面的计算以得到

$$
\begin{gather}
\sum_{i=1}^{\ell} \int_{M} \phi_{i}\psi_{j} f\mathrm{d} V=\int_{M} \psi_{j}f\mathrm{d} V
\end{gather}
$$

两边对 $j$ 求和，则有

$$
\begin{gather}
\sum_{j=1}^{m} \sum_{i=1}^{\ell} \int_{M} \phi_{i}\psi_{j}f\mathrm{d} V=\sum_{j=1}^{m} \int_{M}\psi_{j}f\mathrm{d} V
\end{gather}
$$

根据对称性，上式左边的二重求和同样等于

$$
\begin{gather}
\sum_{i=1}^{\ell} \int_{M} \phi_{i} f\mathrm{d} V
\end{gather}
$$

这就完成了证明。

根据前面的定义，这类积分的线性性是显然的，我们把它形式化地写成一个定理：

**定理 1.6.5**

设 $M\subset \mathbb{R}^{n}$ 是一个 $C^{r}$ 连续的紧致 $k$-流形，$f,g\colon M\to \mathbb{R}$ 是连续函数，则对任意标量 $a,b$ 有

$$
\begin{gather}
\int_{M} (af+bg)\mathrm{d} V=a\int_{M} f\mathrm{d} V+b\int_{M} g\mathrm{d} V
\end{gather}
$$

定义 1.6.4 是一个理论化的定义，它并不适用于计算。在实际应用中，我们通常会把流形拆解为若干个小块，对每一块进行参数化，然后进行积分。下面我们就来把这一过程精确化。

**定义 1.6.6** 测度零（measure zero）

设 $M\subset \mathbb{R}^{n}$ 是一个 $C^{r}$ 连续的紧致 $k$-流形，称集合 $D\subset M$ 在 $M$ 中具有**测度零**，如果它可以被可数个坐标卡 $\alpha_{i}\colon U_{i}\to V_{i}$ 覆盖，且对任意 $i$，集合

$$
\begin{gather}
D_{i}=\alpha_{i}^{-1}[D\cap V_{i}]
\end{gather}
$$

在 $\mathbb{R}^{k}$ 中具有测度零。

**定理 1.6.7**

设 $M\subset \mathbb{R}^{n}$ 是一个 $C^{r}$ 连续的紧致 $k$-流形，$f\colon M\to \mathbb{R}$ 是一个连续函数。假设 $\alpha_{i}\colon A_{i}\to M_{i},i=1,\dots,N$ 是 $M$ 上的坐标卡，使得 $A_{i}$ 在 $\mathbb{R}^{k}$ 中开并且 $M$ 是开集 $M_{1},\dots,M_{N}$ 以及一个 $M$ 上的零测集 $K$ 的无交并，那么

$$
\begin{gather}
\int_{M} f\mathrm{d} V=\sum_{i=1}^{N} \int_{A_{i}} (f\circ\alpha_{i}) V(J_{\alpha_{i}})
\end{gather}
$$

这一定理表明 $M$ 上的积分可以通过将 $M$ 分解成若干参数化流形并分别积分进行计算。

**证明**

由于等式两边关于 $f$ 是线性的，我们可以假设 $f$ 的支撑集 $C$ 可被单个坐标卡 $\alpha\colon U\to V$ 覆盖。同时，我们可以假设 $U$ 是有界的，此时

$$
\begin{gather}
\int_{M} f\mathrm{d} V=\int_{\mathrm{Int}(U)} (f\circ\alpha)V(J_{\alpha})
\end{gather}
$$

(1). 令 $W_{i}=\alpha^{-1}[M_{i}\cap V],L=\alpha^{-1}[K\cap V]$，则 $W_{i}$ 在 $\mathbb{R}^{k}$ 中开，$L$ 在 $\mathbb{R}^{k}$ 中具有测度零，并且 $U$ 是 $W_{i}$ 与 $L$ 的无交并。

![](1-7.png)

我们来证明

$$
\begin{gather}
\int_{M} f\mathrm{d} V=\sum_{i=1}^{N} \int_{W_{i}} (f\circ\alpha)V(J_{\alpha})
\end{gather}
$$

设 $F=(f\circ\alpha)V(J_{\alpha})$，由于 $\mathrm{supp}(f)\subset V$，故 $F$ 在除了 $L$ 以外的 $\partial W_{i}$ 上消失，从而有

$$
\begin{align}
\sum_{i=1}^{N} \int_{W_{i}} F &= \int_{\mathrm{Int}(U)\setminus L} F \\
&= \int_{\mathrm{Int}(U)} F \\
&= \int_{M} f\mathrm{d} V
\end{align}
$$

(2). 下面我们证明

$$
\begin{gather}
\int_{W_{i}} F=\int_{A_{i}} F_{i}
\end{gather}
$$

其中 $F_{i}=(f\circ\alpha_{i})V(J_{\alpha_{i}})$.

![](1-8.png)

转移函数 $\alpha_{i}^{-1}\circ\alpha$ 是一个微分同胚，其将 $W_{i}$ 映射到开集

$$
\begin{gather}
B_{i}=\alpha_{i}^{-1}[M_{i}\cap V]
\end{gather}
$$

根据积分换元公式，我们仿照定理 1.2.4 的证明可得

$$
\begin{gather}
\int_{W_{i}} F=\int_{B_{i}} F_{i}
\end{gather}
$$

最后我们只需证明

$$
\begin{gather}
\int_{B_{i}}F_{i}=\int_{A_{i}}F_{i}
\end{gather}
$$

由于 $C=\mathrm{supp}(f)$ 在 $M$ 上闭，故 $\alpha_{i}^{-1}[C]$ 在 $A_{i}$ 中闭，从而其补集

$$
\begin{gather}
D_{i}=A_{i}\setminus \alpha_{i}^{-1}[C]
\end{gather}
$$

在 $A_{i}$ 中开。$F_{i}$ 在 $D_{i}$ 上消失，因此我们有

$$
\begin{gather}
\int_{A_{i}} F_{i}=\int_{B_{i}} F_{i}+\int_{D_{i}}F_{i}-\int_{B_{i}\cap D_{i}}F_{i}=\int_{B_{i}} F_{i}
\end{gather}
$$

这就完成了证明。

下面我们以一个例子结束本章。假设我们要求 $\mathbb{R}^{3}$ 中球面 $S^{2}(a)$ 的面积，我们可以将其分解为上、下半球以及赤道所在的大圆。大圆在 $S^{2}(a)$ 上具有测度零，对于上半开球面，我们可以对其参数化为

$$
\begin{gather}
\alpha(x,y)=(x,y,\sqrt{ a^{2}-x^{2}-y^{2} }), \quad (x,y)\in \{ (x,y) \mid x^{2}+y^{2}<a^{2} \}
\end{gather}
$$

可以验证

$$
\begin{gather}
V(J_{\alpha})=\dfrac{a}{\sqrt{ a^{2}-x^{2}-y^{2} }}
\end{gather}
$$

因此

$$
\begin{gather}
V(Y_{\alpha})=\int_{0}^{2\pi} \int_{0}^{a} \dfrac{ar}{\sqrt{ a^{2}-r^{2} }} \mathrm{d} r \mathrm{d} \theta=2\pi a^{2}
\end{gather}
$$

根据对称性，下半球面的面积同样是 $2\pi a^{2}$，因此球面 $S^{2}(a)$ 的面积为 $4\pi a^{2}$.