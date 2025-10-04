$L^{p}$ 空间，作为 $L^{1}$ 空间的推广，构成了现代分析学的重要部分。本章我们对其性质做简要的介绍。

# Section 1: 基础理论

**定义 28.1.1** $L^{p}$ 范数

设 $(X,\mathcal{M},\mu)$ 是测度空间，$f$ 是 $X$ 上的可测函数，$0<p<\infty$，定义 $L^{p}$ **范数**为

$$
\begin{gather}
\lVert f \rVert _{p}=\left( \int |f|^{p} \mathrm{d} \mu \right)^{1/p}
\end{gather}
$$

并且定义

$$
\begin{gather}
L^{p}(X,\mathcal{M},\mu)=\{ f\colon X\to \mathbb{C} \mid f \text{可测且} \lVert f \rVert _{p}<\infty \} / \sim
\end{gather}
$$

其中 $f\sim g$ 当且仅当 $f=g$ a.e.

通常我们可以将 $L^{p}(X,\mathcal{M},\mu)$ 简写为 $L^{p}(X,\mu),L^{p}(\mu)$，或者当 $\mu$ 可从上下文推导出时 $L^{p}$. 当 $\mu$ 为 $(A,\mathscr{P}(A))$ 上的计数测度时，通常记为 $l^{p}(A)$. 当 $A=\mathbb{N}$ 时，我们将 $l^{p}(\mathbb{N})$ 记作 $l^{p}$.

$L^{p}$ 是一个向量空间：如果 $f,g \in L^{p}$，那么有

$$
\begin{gather}
|f+g|^{p}\leq (2 \max(|f|,|g|))^{p}\leq 2^{p} (|f|^{p}+|g|^{p})
\end{gather}
$$

因此 $f+g \in L^{p}$，此外，对于 $c \in \mathbb{C}$ 有 $\lVert cf \rVert_{p}=|c|\lVert f \rVert_{p}$，从而 $cf \in L^{p}$. 进一步，我们对 $\lVert \cdot \rVert_{p}$ 的命名暗示了 $L^{p}$ 是一个赋范空间：显然 $\lVert f \rVert_{p}=0$ 当且仅当 $f=0$ a.e.，但是三角不等式就不那么显然了。事实上，三角不等式仅在 $p\geq 1$ 时成立，这被称为 **Minkowski 不等式**，下面我们就来证明这一点。

**引理 28.1.2**

如果 $a,b\geq 0$ 且 $0<\lambda<1$，则

$$
\begin{gather}
a^{\lambda}b^{1-\lambda}\leq \lambda a+(1-\lambda)b
\end{gather}
$$

等号成立当且仅当 $a=b$.

**证明**

如果 $b=0$，则不等式显然成立。反之，令 $t= a / b$，则不等式等价于

$$
\begin{gather}
t^{\lambda}\leq \lambda t+1-\lambda
\end{gather}
$$

等号成立当且仅当 $t=1$. 利用初等微积分即证。

**定理 28.1.3** Holder 不等式

设 $(X,\mathcal{M},\mu)$ 是测度空间，$1<p<\infty,p^{-1}+q^{-1}=1$，如果 $f,g$ 是 $X$ 上的可测函数，则

$$
\begin{gather}
\lVert fg \rVert _{1}\leq \lVert f \rVert _{p}\lVert g \rVert _{q}
\end{gather}
$$

特别地，当 $f \in L^{p},g \in L^{q}$ 时，有 $fg \in L^{1}$，并且此时等号成立当且仅当存在不全为零的常数 $\alpha,\beta\geq 0$ 使得 $\alpha|f|^{p}=\beta|g|^{q}$ a.e.

**证明**

当 $\lVert f \rVert_{p}=0$ 或 $\lVert g \rVert_{q}=0$，以及 $\lVert f \rVert_{p}=\infty$ 或 $\lVert g \rVert_{q}=\infty$ 时是平凡的。此外，如果不等式对于某个 $f,g$ 成立，那么它对于所有 $af$ 和 $bg$ 都成立，因此我们可以假设 $\lVert f \rVert_{p}=\lVert g \rVert_{q}=1$.

将引理 28.1.2 应用到 $a=|f(x)|^{p},b=|g(x)|^{q},\lambda=p^{-1}$，即得

$$
\begin{gather}
|f(x)g(x)|\leq p^{-1} |f(x)|^{p}+q^{-1} |g(x)|^{q}
\end{gather}
$$

等号成立当且仅当 $|f|^{p}=|g|^{q}$ a.e. 对两边积分，得到

$$
\begin{gather}
\lVert fg \rVert _{1}\leq p^{-1} \int|f|^{p}\mathrm{d} \mu+q^{-1} \int|g|^{q}\mathrm{d} \mu=p^{-1}+q^{-1}=1=\lVert f \rVert _{p}\lVert g \rVert _{q}
\end{gather}
$$

这就完成了证明。

Holder 不等式中的指数 $p,q$ 称为**共轭指数**，它们在 $L^{p}$ 空间的理论中经常出现。

**定理 28.1.4** Minkowski 不等式

设 $(X,\mathcal{M},\mu)$ 是测度空间，如果 $1\leq p<\infty$，$f,g \in L^{p}$，则有

$$
\begin{gather}
\lVert f+g \rVert _{p}\leq \lVert f \rVert _{p}+\lVert g \rVert _{p}
\end{gather}
$$

等号成立当且仅当存在不全为零的常数 $\alpha,\beta\geq 0$ 使得 $\alpha f=\beta g$ a.e.

**证明**

当 $p=1$ 或 $f+g=0$ a.e. 时是平凡的。此外，根据三角不等式有

$$
\begin{gather}
|f+g|^{p}\leq (|f|+|g|)|f+g|^{p-1}
\end{gather}
$$

取 $q= \dfrac{p}{p-1}$ 为 $p$ 的共轭指数，应用 Holder 不等式，得到

$$
\begin{align}
\int |f+g|^{p} \mathrm{d} \mu &\leq \lVert f \rVert _{p} \lVert |f+g|^{p-1} \rVert _{q} +\lVert g \rVert _{p} \lVert |f+g|^{p-1} \rVert _{q} \\
&= (\lVert f \rVert _{p}+\lVert g \rVert _{p}) \left( \int |f+g|^{p}\mathrm{d} \mu \right)^{1/q}
\end{align}
$$

两边除以 $\left( \int |f+g|^{p}\mathrm{d} \mu \right)^{1/q}$，利用 $p^{-1}+q^{-1}=1$ 即证。根据三角不等式和 Holder 不等式的取等条件可知存在 $\alpha,\beta\geq 0$ 使得 $\alpha f=\beta g$ a.e.

这一结果表明当 $p\geq 1$ 时 $L^{p}$ 是一个赋范空间。进一步我们还有：

**定理 28.1.5**

设 $(X,\mathcal{M},\mu)$ 是测度空间，则对任意 $1\leq p<\infty$，$L^{p}$ 是一个 Banach 空间。

**证明**

我们将使用定理 27.1.4. 设 $(f_{k})_{k=1}^{\infty}\subset L^{p}$ 且 $\sum_{k=1}^{\infty}\lVert f_{k} \rVert_{p}=B<\infty$，令 $G_{n}=\sum_{k=1}^{n}|f_{k}|,G=\sum_{k=1}^{\infty}|f_{k}|$，则 $\lVert G_{n} \rVert_{p}\leq \sum_{k=1}^{n}\lVert f_{k} \rVert_{p}\leq B$，因此根据单调收敛定理知

$$
\begin{gather}
\int G^{p} = \lim_{ n \to \infty } \int G_{n}^{p} \leq B^{p}
\end{gather}
$$

于是 $G \in L^{p}$，即 $G(x)<\infty$ a.e.，从而级数 $\sum_{k=1}^{\infty}f_{k}$ 收敛 a.e.，记其极限为 $F$，则有 $|F|\leq G$，故 $F \in L^{p}$. 此外，有 $\left\lvert  F-\sum_{k=1}^{n}f_{k}  \right\rvert^{p}\leq (2G)^{p} \in L^{1}$，故根据控制收敛定理得

$$
\begin{gather}
\left\lVert  F- \sum_{k=1}^{n} f_{k}  \right\rVert _{p}^{p}= \int \left\lvert  F - \sum_{k=1}^{n} f_{k}  \right\rvert ^{p} \to 0 \quad (n\to \infty)
\end{gather}
$$

即证 $\sum_{k=1}^{\infty}f_{k}$ 在 $L^{p}$ 范数下收敛。

**定理 28.1.6**

设 $(X,\mathcal{M},\mu)$ 是测度空间，$1\leq p<\infty$，则简单函数 $f=\sum_{j=1}^{n}a_{j}\chi_{E_{j}}$，其中 $\mu(E_{j})<\infty$ 构成的集合在 $L^{p}$ 中是稠密的。

**证明**

显然简单函数在 $L^{p}$ 中。如果 $f \in L^{p}$，取一列简单函数 $(f_{n})$ 使得 $f_{n}\to f$ a.e. 且 $|f_{n}|\leq|f|$，于是我们有 $f_{n}\in L^{p}$，并且 $|f_{n}-f|^{p}\leq (2|f|)^{p} \in L^{1}$，从而根据控制收敛定理得 $\lVert f_{n}-f \rVert_{p}\to 0$. 此外，如果 $f_{n}=\sum_{j=1}^{n}a_{j}\chi_{E_{j}}$，其中 $E_{j}$ 是互不相交的，那么必然有 $\mu(E_{j})<\infty$，因为

$$
\begin{gather}
\int |f_{n}|^{p}=\sum_{j=1}^{n} |a_{j}|^{p} \mu(E_{j})<\infty
\end{gather}
$$

这就完成了证明。

为了完成 $L^{p}$ 空间理论的完整图景，我们引入对应于极限值 $p=\infty$ 的空间 $L^{\infty}$ 如下：

**定义 28.1.7** 本性上确界（essential supremum），$L^{\infty}$ 范数

设 $(X,\mathcal{M},\mu)$ 是测度空间，$f\colon X\to \mathbb{R}^{*}$ 是可测函数，定义 $f$ 的**本性上确界**为

$$
\begin{gather}
\mathrm{ess}\sup f = \inf \{ a \mid \mu(\{ x \mid f(x)>a \}) = 0 \}
\end{gather}
$$

定义 $f\colon X\to \mathbb{C}$ 的 $L^{\infty}$ **范数**为 $\lVert f \rVert_{\infty}=\mathrm{ess}\sup |f|$，并且定义

$$
\begin{gather}
L^{\infty}(X,\mathcal{M},\mu)=\{ f\colon X\to \mathbb{C} \mid f \text{可测且} \lVert f \rVert _{\infty}<\infty \} / \sim
\end{gather}
$$

其中 $f\sim g$ 当且仅当 $f=g$ a.e.

根据定义我们知道，如果 $f \in L^{\infty}$，那么 $f$ 几乎处处有界：存在有界可测函数 $g$ 使得 $f=g \chi_{E}$，其中 $E=\{ x \mid |f(x)|\leq \lVert f \rVert_{\infty} \}$. 关于 $1\leq p<\infty$ 的结论可以自然地推广至 $p=\infty$，如下所示：

**定理 28.1.8**

设 $(X,\mathcal{M},\mu)$ 是测度空间，则有：

1. 如果 $f,g$ 是 $X$ 上的可测函数，那么 $\lVert fg \rVert_{1}\leq \lVert f \rVert_{1}\lVert g \rVert_{\infty}$. 如果 $f \in L^{1}$，$g \in L^{\infty}$，那么 $\lVert fg \rVert_{1}=\lVert f \rVert_{1}\lVert g \rVert_{\infty}$ 当且仅当 $|g(x)|=\lVert g \rVert_{\infty}$ 对 a.e. $x \in \{ x \mid f(x)\neq 0 \}$ 成立。
2. $\lVert \cdot \rVert_{\infty}$ 是 $L^{\infty}$ 上的一个范数。
3. 设 $f_{n},f \in L^{\infty}$，则 $\lVert f_{n}-f \rVert_{\infty}\to 0$ 当且仅当存在 $E \in \mathcal{M}$ 使得 $\mu(E^{c})=0$ 且 $(f_{n})$ 在 $E$ 上一致收敛于 $f$.
4. $L^{\infty}$ 是一个 Banach 空间。
5. 简单函数在 $L^{\infty}$ 中稠密。

**证明**

(1). 当 $\lVert f \rVert_{1}=0$ 或 $\lVert g \rVert_{\infty}=0$，以及 $\lVert f \rVert_{1}=\infty$ 或 $\lVert g \rVert_{\infty}=\infty$ 时是平凡的。在其它情况下有

$$
\begin{gather}
\lVert fg \rVert _{1}=\int |f||g|\mathrm{d} \mu\leq \int |f| \lVert g \rVert _{\infty} \mathrm{d} \mu =\lVert f \rVert _{1}\lVert g \rVert _{\infty}
\end{gather}
$$

当 $f \in L^{1},g \in L^{\infty}$ 时，把空间限制在 $\{ x \mid f(x)\neq 0 \}$ 上，则如果 $|g(x)|=\lVert g \rVert_{\infty}$ a.e.，那么显然有 $\lVert fg \rVert_{1}=\lVert f \rVert_{1}\lVert g \rVert_{\infty}$. 反之，如果 $\lVert fg \rVert_{1}=\lVert f \rVert_{1}\lVert g \rVert_{\infty}$，则有

$$
\begin{gather}
\int |f|(|g|-\lVert g \rVert _{\infty}) \mathrm{d} \mu=0
\end{gather}
$$

即 $|f|(|g|-\lVert g \rVert_{\infty})=0$ a.e.，从而在 $\{ x \mid f(x)\neq 0 \}$ 上有 $|g|=\lVert g \rVert_{\infty}$ a.e.

(2). 正定性和齐次性是显然的，设 $f,g \in L^{\infty}$，则有

$$
\begin{gather}
|f(x)+g(x)|\leq |f(x)|+|g(x)|\leq \lVert f \rVert _{\infty}+\lVert g \rVert _{\infty} \quad \text{a.e.}
\end{gather}
$$

对左边取本性上确界，即得 $\lVert f+g \rVert_{\infty}\leq \lVert f \rVert_{\infty}+\lVert g \rVert_{\infty}$，即 $\lVert \cdot \rVert_{\infty}$ 是 $L^{\infty}$ 上的范数。

(3). 设 $\lVert f_{n}-f \rVert_{\infty}\to 0$，令 $g_{n}=f_{n}-f$，则 $g_{n} \in L^{\infty}$，$\lVert g_{n} \rVert_{\infty}\to 0$. 设 $E_{n}=\{ x \mid |g_{n}(x)|\leq \lVert g_{n} \rVert_{\infty} \}$，$E=\bigcap_{n=1}^{\infty}E_{n}$，则 $\mu(E_{n}^{c})=0$，从而 $\mu(E^{c})=0$，并且 $(g_{n})$ 在 $E$ 上一致收敛于 $0$，即 $(f_{n})$ 一致收敛于 $f$.

反之，如果 $(f_{n})$ 在 $E$ 上一致收敛于 $f$，且 $\mu(E^{c})=0$，则在 $E$ 上有对任意 $\varepsilon>0$，存在 $N$ 使得对任意 $n>N,x \in E$ 有 $|f_{n}-f|<\varepsilon$，取本性上确界就有 $\lVert f_{n}-f \rVert_{\infty}\leq \varepsilon$，即证 $\lVert f_{n}-f \rVert_{\infty}\to 0$.

(4). 设 $(f_{k})_{k=1}^{\infty}\subset L^{\infty}$ 是 Cauchy 序列，即对任意 $\varepsilon>0$，存在 $N$ 使得对任意 $n,m>N$ 有 $\lVert f_{n}-f_{m} \rVert_{\infty}<\varepsilon$，即

$$
\begin{gather}
|f_{n}(x)-f_{m}(x)|<\varepsilon \quad \text{a.e. } x
\end{gather}
$$

取 $\varepsilon=1 / k$，则存在 $N_{k}$ 和零测集 $E_{k}$ 使得对任意 $n,m>N_{k},x \in X\setminus E_{k}$ 有 $|f_{n}(x)-f_{m}(x)|<1 / k$. 取 $E=\bigcup_{k=1}^{\infty} E_{k}$，则 $\mu(E)=0$，并且在 $X\setminus E$ 上满足对任意 $\varepsilon>0$，存在 $k>1 / \varepsilon$ 使得对任意 $n,m>N_{k}$ 有 $|f_{n}(x)-f_{m}(x)|<1 / k<\varepsilon$，因此 $(f_{n}(x))$ 是 $\mathbb{C}$ 上的 Cauchy 序列，故收敛。令

$$
\begin{gather}
f=\begin{cases}
\lim_{ n \to \infty } f_{n}(x) & ,x \in X\setminus E \\
0 & , x \in E
\end{cases}
\end{gather}
$$

则 $f_{k}\to f$ a.e.

取 $\varepsilon=1$，存在 $N$ 使得对任意 $n,m>N$ 有 $|f_{n}(x)-f_{m}(x)|<1$ a.e.，令 $m\to \infty$，则有 $|f_{n}(x)-f(x)|\leq 1$ a.e.，从而有

$$
\begin{gather}
|f(x)|\leq|f_{n}(x)|+|f_{n}(x)-f(x)|\leq \lVert f_{n} \rVert _{\infty} +1 \quad \text{a.e.}
\end{gather}
$$

又由于 $(f_{n})$ 是 Cauchy 序列，故有界，因此 $\lVert f \rVert_{\infty}<\infty$，即 $f \in L^{\infty}$. 此外，对任意 $\varepsilon>0$，存在 $N$ 使得对任意 $n,m>N$ 有 $|f_{n}(x)-f_{m}(x)|<\varepsilon$，令 $m\to \infty$ 得 $|f_{n}(x)-f(x)|\leq\varepsilon$ 对 a.e. $x$ 成立，从而有

$$
\begin{gather}
\lVert f_{n}-f \rVert _{\infty}\leq\varepsilon
\end{gather}
$$

即 $(f_{k})$ 按 $L^{\infty}$ 范数收敛于 $f$，即证 $L^{\infty}$ 的完备性。

(5). 显然简单函数在 $L^{\infty}$ 中。设 $f \in L^{\infty}$，则对于 a.e. $x$ 有 $|f(x)|\leq M$，分别取实部和虚部，我们可以假设 $f$ 是实值函数。对任意 $\varepsilon>0$，取 $N$ 使得 $M / N<\varepsilon$，令

$$
\begin{gather}
I_{k}=\left[ -M+(k-1) \dfrac{2M}{N}, -M+k \dfrac{2M}{N} \right), \quad k=1,2,\dots,N
\end{gather}
$$

其中 $I_{N}$ 是闭区间以覆盖 $M$，再令

$$
\begin{gather}
E_{k}=f^{-1}[I_{k}], y_{k}=-M+\left( k- \dfrac{1}{2} \right) \dfrac{2M}{N}
\end{gather}
$$

定义 $\phi=\sum_{k=1}^{N}y_{k}\chi_{E_{k}}$，则当 $f(x)\in I_{k}$ 时有 $|f(x)-y_{k}|\leq M / N<\varepsilon$，因此在 $\bigcup_{k=1}^{N}E_{k}$ 上有 $|f(x)-\phi(x)|<\varepsilon$，特别地，对于 a.e. $x$ 有不等式成立，从而 $\lVert f-\phi \rVert_{\infty}\leq\varepsilon$，即证简单函数的稠密性。

根据上述定理的 1，以及形式等式 $1^{-1}+\infty^{-1}=1$，我们可以把 $1,\infty$ 看成一对共轭指数，这样，我们就完成了 $L^{p}$ 空间理论的完整图景：每个 $L^{p}$ 空间都与一个 $L^{q}$ 空间对应，其中 $p^{-1}+q^{-1}=1,1\leq p\leq \infty$.

另外，28.1.8 的 3 也表明，依 $L^{\infty}$ 范数收敛与一致收敛是紧密相关的，这也解释了为何它们使用相同的符号。事实上，如果我们使用的是 Lebesgue 测度，那么当 $f$ 连续时，这两个范数就是相同的：因为 $\{ x \mid |f(x)|>a \}$ 是开集。由此我们可以将有界连续函数空间 $C_{b}$ 看成 $L^{\infty}$ 空间的一个闭子空间。

下面我们来看多个 $L^{p}$ 空间的联系。一般来说，当 $p\neq q$ 时，不一定有 $L^{p}\subset L^{q}$ 或 $L^{q}\subset L^{p}$，我们以一个简单的例子说明原因：设 $f_{a}(x)=x^{-a}$，其中 $a>0$，则初等微积分表明 $f_{a}\chi_{(0,1)}\in L^{p}$ 当且仅当 $p<a^{-1}$，而 $f_{a}\chi_{(1,\infty)}\in L^{p}$ 当且仅当 $p>a^{-1}$，因此如果 $f \not\in L^{p}$，我们可以总结为两个原因：$|f|^{p}$ 在某一点处发散到无穷的速度过快，或者 $|f|^{p}$ 在无穷远处衰减的速度过慢。当 $p$ 增大时，前者的奇异性增强了（发散的更快），后者的奇异性则减弱了，因此如果 $p<q$，那么 $L^{p}$ 中的函数比起 $L^{q}$ 中的在局部更为奇异，但是 $L^{q}$ 中的函数比起 $L^{p}$ 中的分布的范围更广。根据这两种效应，下面我们给出四个结果，它们分别从不同角度精确地描述了这两种效应的影响。

**定理 28.1.9**

设 $(X,\mathcal{M},\mu)$ 是测度空间，如果 $0<p<q<r\leq \infty$，那么 $L^{q}\subset L^{p}+L^{r}$.

**证明**

如果 $f \in L^{q}$，令 $E=\{ x \mid |f(x)|>1 \}$，$g=f\chi_{E},h=f\chi_{E^{c}}$，则 $|g|^{p}=|f|^{p}\chi_{E}\leq|f|^{q}\chi_{E}$，于是 $g \in L^{p}$，并且当 $r<\infty$ 时有 $|h|^{r}=|f|^{r}\chi_{E^{c}}\leq|f|^{q}\chi_{E^{c}}$，于是 $h \in L^{r}$. 当 $r=\infty$ 时，同样有 $|h|\leq 1$，于是 $h \in L^{\infty}$，这就表明 $f \in L^{p}+L^{r}$，即证。

**定理 28.1.10**

设 $(X,\mathcal{M},\mu)$ 是测度空间，如果 $0<p<q<r\leq \infty$，那么 $L^{p}\cap L^{r}\subset L^{q}$，并且 $\lVert f \rVert_{q}\leq \lVert f \rVert_{p}^{\lambda}\lVert f \rVert_{r}^{1-\lambda}$，其中 $\lambda \in(0,1)$ 满足

$$
\begin{gather}
q^{-1}=\lambda p^{-1}+(1-\lambda)r^{-1}, \quad \text{i.e. } \lambda= \dfrac{q^{-1}-r^{-1}}{p^{-1}-r^{-1}}
\end{gather}
$$

**证明**

如果 $r=\infty$，我们有 $|f|^{q}\leq \lVert f \rVert_{\infty}^{q-p}|f|^{p}$，$\lambda=p / q$，从而有

$$
\begin{gather}
\lVert f \rVert _{q}^{q}=\int|f|^{q}\leq \lVert f \rVert _{\infty}^{q-p} \int|f|^{p}=\lVert f \rVert _{\infty}^{q-p} \lVert f \rVert _{p}^{p}
\end{gather}
$$

取 $q$ 次根，即得 $\lVert f \rVert_{q}\leq \lVert f \rVert_{p}^{\lambda}\lVert f \rVert_{\infty}^{1-\lambda}$.

如果 $r<\infty$，应用 Holder 不等式，其中共轭指数取为 $p / \lambda q$ 和 $r / (1-\lambda)q$ 即得

$$
\begin{align}
\int|f|^{q} &= \int |f|^{\lambda q}|f|^{(1-\lambda)q}\leq \lVert |f|^{\lambda q} \rVert _{p / \lambda q} \lVert |f|^{(1-\lambda)q} \rVert _{r / (1-\lambda)q} \\
&= \left( \int |f|^{p} \right)^{\lambda q / p} \left( \int |f|^{r} \right)^{(1-\lambda)q / r}=\lVert f \rVert _{p}^{\lambda q} \lVert f \rVert _{r}^{(1-\lambda)q}
\end{align}
$$

取 $q$ 次根即证。根据不等式即得 $L^{p}\cap L^{r}\subset L^{q}$.

**定理 28.1.11**

设 $A$ 是任意集合，$0<p<q\leq \infty$，则 $l^{p}(A)\subset l^{q}(A)$，且 $\lVert f \rVert_{q}\leq \lVert f \rVert_{p}$.

**证明**

设 $f \in l^{p}(A)$，显然 $\lVert f \rVert_{\infty}^{p}=\sup_{\alpha} |f(\alpha)|^{p}\leq \sum_{\alpha}|f(\alpha)|^{p}$，因此 $\lVert f \rVert_{\infty}\leq \lVert f \rVert_{p}$. 对于 $q<\infty$，根据定理 28.1.10，取 $\lambda=p / q$ 就有

$$
\begin{gather}
\lVert f \rVert _{q}\leq \lVert f \rVert _{p}^{\lambda} \lVert f \rVert _{\infty}^{1-\lambda}\leq \lVert f \rVert _{p}
\end{gather}
$$

这就完成了证明。

**定理 28.1.12**

设 $(X,\mathcal{M},\mu)$ 是测度空间，如果 $\mu(X)<\infty$，$0<p<q\leq \infty$，则有 $L^{q}\subset L^{p}$，且 $\lVert f \rVert_{p}\leq \lVert f \rVert_{q}\mu(X)^{(1 / p)-(1 / q)}$.

**证明**

如果 $q=\infty$，则有

$$
\begin{gather}
\lVert f \rVert _{p}^{p}=\int|f|^{p}\leq \int \lVert f \rVert _{\infty}^{p}= \lVert f \rVert _{\infty}^{p} \mu(X)
\end{gather}
$$

如果 $q<\infty$，应用 Holder 不等式，取共轭指数为 $q / p$ 和 $q / (q-p)$ 则有

$$
\begin{gather}
\lVert f \rVert _{p}^{p} = \int|f|^{p}\leq \lVert |f|^{p} \rVert _{q / p} \lVert 1 \rVert _{q / (q-p)}=\lVert f \rVert _{q}^{p} \mu(X)^{(q-p) / q}
\end{gather}
$$

取 $q$ 次根就完成了证明。

最后我们来总结一下 $L^{p}$ 空间的基本性质。三个最重要的 $L^{p}$ 空间分别为 $L^{1},L^{2},L^{\infty}$，它们各自有各自的重要应用：$L^{1}$ 是我们熟悉的可积函数空间，基本的积分收敛定理在其上成立；$L^{2}$ 的特殊性源于它是 Hilbert 空间；而 $L^{\infty}$ 的特殊性源于其上的范数与一致收敛的联系。然而，在许多情况下 $L^{1}$ 和 $L^{\infty}$ 的性质有些病态，而满足 $1<p<\infty$ 的空间 $L^{p}$ 反而具有更好的性质，这一点非常明显地体现在下面我们要研究的对偶空间上。

# Section 2: 对偶空间

假设 $p,q$ 是一对共轭指数，那么 Holder 不等式表明，每个 $g \in L^{q}$ 都诱导了 $L^{p}$ 上的一个有界线性泛函：

$$
\begin{gather}
\phi_{g}(f)=\int fg
\end{gather}
$$

并且 $\phi_{g}$ 的算子范数最大为 $\lVert g \rVert_{q}$. 事实上，我们可以证明，映射 $g\mapsto \phi_{g}$ 几乎总是一个从 $L^{q}$ 到 $(L^{p})^{*}$ 的等距映射。

**定理 28.2.1**

设 $(X,\mathcal{M},\mu)$ 是测度空间，$p,q$ 是共轭指数且 $1\leq q<\infty$，如果 $g \in L^{q}$，则定义为 $\phi_{g}(f)=\int fg$ 的线性泛函 $\phi_{g}$ 满足

$$
\begin{gather}
\lVert g \rVert _{q}=\lVert \phi_{g} \rVert =\sup \left\{  \left\lvert  \int fg  \right\rvert  \middle| \lVert f \rVert _{p} =1  \right\}
\end{gather}
$$

如果 $\mu$ 是半有限的，那么结论对 $q=\infty$ 也成立。

**证明**

Holder 不等式表明 $\lVert \phi_{g} \rVert\leq \lVert g \rVert_{q}$. 当 $g=0$ a.e. 时是平凡的，当 $g\neq 0$ 且 $1<q<\infty$ 时，令

$$
\begin{gather}
f= \dfrac{|g|^{q-1} \overline{\mathrm{sgn}\ g}}{\lVert g \rVert _{q}^{q-1}}
\end{gather}
$$

取 $p=q / (q-1)$ 是 $q$ 的共轭指数，则有

$$
\begin{gather}
\lVert f \rVert _{p}^{p}= \dfrac{1}{\lVert g \rVert _{q}^{(q-1)p}} \int |g|^{(q-1)p}= \dfrac{\lVert g \rVert _{q}^{q}}{\lVert g \rVert _{q}^{q}}=1
\end{gather}
$$

于是

$$
\begin{gather}
\lVert \phi_{g} \rVert \geq \int fg = \dfrac{1}{\lVert g \rVert _{q}^{q-1}} \int |g|^{q} = \lVert g \rVert _{q}
\end{gather}
$$

即证 $\lVert \phi_{g} \rVert=\lVert g \rVert_{q}$. 当 $q=1$ 时，$f=\overline{\mathrm{sgn}\ g}$，则 $\lVert f \rVert_{\infty}=1$，从而 $\lVert \phi_{g} \rVert\geq \int fg=\lVert g \rVert_{1}$.

设 $\mu$ 是半有限的，$q=\infty$，令 $A=\{ x \mid |g(x)|>\lVert g \rVert_{\infty}-\varepsilon \}$，则 $\mu(A)>0$，于是存在 $B\subset A$ 使得 $0<\mu(B)<\infty$，令

$$
\begin{gather}
f= \dfrac{\overline{\mathrm{sgn}\ g}}{\mu(B)} \chi_{B}
\end{gather}
$$

则 $\lVert f \rVert_{1}=1$，因此

$$
\begin{gather}
\lVert \phi_{g} \rVert \geq \int fg= \dfrac{1}{\mu(B)} \int_{B} |g| \geq \lVert g \rVert _{\infty}-\varepsilon
\end{gather}
$$

根据 $\varepsilon$ 的任意性，故 $\lVert \phi_{g} \rVert=\lVert g \rVert_{\infty}$.

反之，如果 $f\mapsto \int fg$ 是 $L^{p}$ 上的有界线性泛函，那么 $g$ 几乎总是在 $L^{q}$ 中。事实上，我们有以下更强的结论成立：

**定理 28.2.2**

设 $(X,\mathcal{M},\mu)$ 是测度空间，$p,q$ 是共轭指数，$\Sigma$ 由在一个有限测度集外消失的简单函数构成，如果 $g$ 是 $X$ 上的可测函数使得对任意 $f \in\Sigma$ 有 $fg \in L^{1}$，并且设

$$
\begin{gather}
M_{q}(g)=\sup \left\{  \left\lvert  \int fg  \right\rvert     \middle|  f \in\Sigma, \lVert f \rVert _{p}=1  \right\} < \infty
\end{gather}
$$

此外，如果还有 $S_{g}=\{ x \mid g(x)\neq 0 \}$ 是 $\sigma$-有限的或者 $\mu$ 是半有限的，那么有 $g \in L^{q}$ 且 $M_{q}(g)=\lVert g \rVert_{q}$.

**证明**

首先，设 $f$ 是一个在有限测度集 $E$ 外消失的有界可测函数，且 $\lVert f \rVert_{p}=1$，那么 $|\int fg|\leq M_{q}(g)$. 这是因为我们可以取简单函数 $f_{n}\to f$，其中 $f_{n}$ 在 $E$ 外消失，满足 $|f_{n}|\leq|f|$. 由于 $|f_{n}|\leq \lVert f \rVert_{\infty}\chi_{E}$ 且 $g\chi_{E}\in L^{1}$，根据控制收敛定理知 $|\int fg|=\lim_{ n \to \infty }|\int f_{n}g|\leq M_{q}(g)$.

现在设 $q<\infty$，且 $S_{g}$ 是 $\sigma$-有限的。令 $(E_{n})_{n=1}^{\infty}$ 满足 $\mu(E_{n})<\infty$，$S_{g}=\bigcup_{n=1}^{\infty} E_{n}$，且 $E_{1}\subset E_{2}\subset\cdots$，并令 $(\phi_{n})$ 为简单函数满足 $\phi_{n}\to g$ 且 $|\phi_{n}|\leq|g|$，取 $g_{n}=\phi_{n}\chi_{E_{n}}$，则 $g_{n}\to g$，$|g_{n}|\leq|g|$，且 $g_{n}$ 在 $E_{n}$ 以外消失。令

$$
\begin{gather}
f_{n}= \dfrac{|g_{n}|^{q-1} \overline{\mathrm{sgn}\ g}}{\lVert g_{n} \rVert _{q}^{q-1}}
\end{gather}
$$

于是 $\lVert f_{n} \rVert_{p}=1$，从而根据 Fatou 引理有

$$
\begin{align}
\lVert g \rVert _{q} &\leq \liminf_{ n \to \infty } \lVert g_{n} \rVert _{q} = \liminf_{ n \to \infty } \int |f_{n}g_{n}| \\
&\leq \liminf_{ n \to \infty } \int|f_{n}g| = \liminf_{ n \to \infty } \int f_{n}g \leq M_{q}(g)
\end{align}
$$

另一方面，Holder 不等式表明 $M_{q}(g)\leq \lVert g \rVert_{q}$，即证 $g \in L^{q}$ 且 $M_{q}(g)=\lVert g \rVert_{q}$.

现在设 $q=\infty$，令 $A=\{ x \mid |g(x)|\geq M_{\infty}(g)+\varepsilon \}\subset S_{g}$，假设 $\mu(A)>0$，由于 $S_{g}$ 是 $\sigma$-有限的（或者由于 $\mu$ 是半有限的），故存在 $B\subset A$ 使得 $0<\mu(B)<\infty$，令

$$
\begin{gather}
f= \dfrac{\overline{\mathrm{sgn}\ g}}{\mu(B)} \chi_{B}
\end{gather}
$$

则 $\lVert f \rVert_{1}=1$ 且 $\int fg=\mu(B)^{-1} \int_{B} |g|\geq M_{\infty}(g)+\varepsilon$，但这与 $\int fg\leq M_{\infty}(g)$ 矛盾，因此 $\lVert g \rVert_{\infty}\leq M_{\infty}(g)$. 反向的不等式是平凡的，即证。

如果 $\mu$ 是半有限的，$q<\infty$，我们要证 $A_{\varepsilon}=\{ x \mid |g(x)|>\varepsilon \}$ 具有有限测度，从而 $S_{g}$ 是 $\sigma$-有限的。假设 $\mu(A_{\varepsilon})=\infty$，则存在 $A_{\varepsilon}$ 的一列子集 $(E_{n})$，满足 $0<\mu(E_{n})<\infty$ 且 $\mu(E_{n})\to \infty$，令

$$
\begin{gather}
f_{n}= \dfrac{\overline{\mathrm{sgn}\ g}}{\mu(E_{n})^{1/p}} \chi_{E_{n}}
\end{gather}
$$

则 $\lVert f_{n} \rVert_{p}=1$，并且有

$$
\begin{gather}
M_{q}(g)\geq \int fg = \dfrac{1}{\mu(E_{n})^{1/p}} \int_{E_{n}} |g| \geq \varepsilon \mu(E_{n})^{1-1/p}=\varepsilon \mu(E_{n})^{1/q}
\end{gather}
$$

令 $n\to \infty$，则有 $M_{q}(g)=\infty$，矛盾，因此 $\mu(A_{\varepsilon})<\infty$，这就完成了证明。

最后，也是最深刻的关于 $(L^{p})^{*}$ 的结论如下，它表明，在几乎所有情况下，映射 $g\mapsto \phi_{g}$ 都是一个满射。

**定理 28.2.3**

设 $(X,\mathcal{M},\mu)$ 是测度空间，$p,q$ 是共轭指数，如果 $1<p<\infty$，那么对任意 $\phi \in(L^{p})^{*}$，都存在 $g \in L^{q}$ 使得对任意 $f \in L^{p}$ 有 $\phi(f)=\int fg$，从而 $L^{q}$ 等距同构于 $(L^{p})^{*}$. 如果 $\mu$ 是 $\sigma$-有限的，那么结论对 $p=1$ 也成立。

**证明**

首先设 $\mu$ 是有限的，从而简单函数都在 $L^{p}$ 中。如果 $\phi \in(L^{p})^{*}$ 且 $E \in \mathcal{M}$，令 $\nu(E)=\phi(\chi_{E})$. 设 $(E_{n})$ 是一列互不相交的集合，$E=\bigcup_{j=1}^{\infty}E_{j}$，我们有 $\chi_{E}=\sum_{j=1}^{\infty}\chi_{E_{j}}$，其中右边的级数在 $L^{p}$ 范数中收敛：

$$
\begin{gather}
\left\lVert  \chi_{E}-\sum_{j=1}^{n} \chi_{E_{j}}  \right\rVert _{p}=\left\lVert  \sum_{j=n+1}^{\infty} \chi_{E_{j}}  \right\rVert _{p}=\mu\left( \bigcup_{j=n+1}^{\infty} E_{j} \right)^{1/p} \to 0 \quad (n\to \infty)
\end{gather}
$$

（这里使用了 $p<\infty$ 的条件）此外，由于 $\phi$ 是线性且连续的，故有

$$
\begin{gather}
\nu(E)=\sum_{j=1}^{\infty} \phi(\chi_{E_{j}})=\sum_{j=1}^{\infty} \nu(E_{j})
\end{gather}
$$

因此 $\nu$ 是一个复测度。如果 $\mu(E)=0$，则 $\chi_{E}=0$，因此 $\nu(E)=0$，这表明 $\nu\ll \mu$，因此有 Radon-Nikodym 定理知存在 $g \in L^{1}(\mu)$ 使得

$$
\begin{gather}
\nu(E)=\phi(\chi_{E})=\int_{E} g \mathrm{d} \mu
\end{gather}
$$

于是对于简单函数 $f$ 有 $\phi(f)=\int fg\mathrm{d}\mu$. 又由于 $|\int fg|\leq \lVert \phi \rVert\lVert f \rVert_{p}$，因此由定理 28.2.2 得 $g \in L^{q}$，从而根据简单函数的稠密性知对任意 $f \in L^{p}$ 有 $\phi(f)=\int fg$.

现在设 $\mu$ 是 $\sigma$-有限的，取一列递增的集合 $(E_{n})$ 满足 $0<\mu(E_{n})<\infty$ 且 $X=\bigcup_{j=1}^{\infty}E_{j}$，并将 $L^{p}(E_{n})$ 与 $L^{p}(X)$ 的子空间等同，那么上面的论述表明对任意 $n$，存在 $g_{n}\in L^{q}(E_{n})$ 使得对任意 $f \in L^{p}(E_{n})$ 有 $\phi(f)=\int fg_{n}$，并且 $\lVert g_{n} \rVert_{q}=\lVert \phi|_{L^{p}(E_{n})} \rVert\leq \lVert \phi \rVert$.

根据 Radon-Nikodym 定理，函数 $g_{n}$ 是 a.e.-唯一的，因此如果 $n<m$（即 $E_{n}\subset E_{m}$），那么在 $E_{n}$ 上有 $g_{n}=g_{m}$ a.e.，于是我们可以定义 $X$ 上的函数 $g$，使得它在 $E_{n}$ 上有 $g=g_{n}$ a.e. 根据单调收敛定理，有 $\lVert g \rVert_{q}=\lim_{ n \to \infty }\lVert g_{n} \rVert_{q}\leq \lVert \phi \rVert$，因此 $g \in L^{q}$，此外，如果 $f \in L^{p}$，那么根据控制收敛定理和在 $L^{p}$ 范数下 $f\chi_{E_{n}}\to f$ 得

$$
\begin{gather}
\phi(f)=\lim_{ n \to \infty }\phi(f\chi_{E_{n}})=\lim_{ n \to \infty }\int_{E_{n}}fg=\int fg
\end{gather}
$$

最后，设 $\mu$ 是任意测度且 $p>1$，从而 $q<\infty$. 根据上面的论述，对于每个 $\sigma$-有限的集合 $E$，都存在一个 a.e.-唯一的函数 $g_{E}\in L^{q}(E)$ 使得对任意 $f \in L^{p}(E)$ 有 $\phi(f)=\int fg$，且 $\lVert g_{E} \rVert_{q}\leq \lVert \phi \rVert$. 如果 $F\supset E$ 且 $F$ 是 $\sigma$-有限的，那么在 $E$ 上有 $g_{F}=g_{E}$ a.e.，从而 $\lVert g_{F} \rVert_{q}\geq \lVert g_{E} \rVert_{q}$.

设 $M=\sup_{E} \lVert g_{E} \rVert_{q}$，其中 $E$ 是 $\sigma$-有限的集合，则 $M\leq \lVert \phi \rVert$，取一列 $\sigma$-有限的集合 $(E_{n})$ 使得 $\lVert g_{E_{n}} \rVert_{q}\to M$，并令 $F=\bigcup_{j=1}^{\infty}E_{j}$，则 $F$ 是 $\sigma$-有限的，且对任意 $n$ 有 $\lVert g_{F} \rVert_{q}\geq \lVert g_{E_{n}} \rVert_{q}$，从而 $\lVert g_{F} \rVert_{q}=M$. 现在，如果 $A\supset F$ 且 $A$ 是 $\sigma$-有限的，那么我们有

$$
\begin{gather}
\int |g_{F}|^{q}+\int |g_{A\setminus F}|^{q}=\int |g_{A}|^{q}\leq M^{q}=\int |g_{F}|^{q}
\end{gather}
$$

因此 $g_{A\setminus F}=0$ a.e.，从而 $g_{A}=g_{F}$ a.e.（这里使用了 $q<\infty$ 的条件）。但如果 $f \in L^{p}$，那么 $A=F\cup \{ x \mid f(x)\neq 0 \}$ 就是 $\sigma$-有限的，因此 $\phi(f)=\int fg_{A}=\int fg_{F}$，取 $g=g_{F}$ 就完成了证明。

由该定理，我们也可以得到一个推论：

**定理 28.2.4**

如果 $1<p<\infty$，那么 $L^{p}$ 是自反的。

从本节的三个定理我们可以看出，当 $1<p<\infty$ 时，$L^{p}$ 空间具有 $L^{1}$ 和 $L^{\infty}$ 空间所不具有的一些性质，特别是 $L^{p}$ 与 $L^{q}$（$p,q$ 共轭）的对偶性，这使得它们在 Fourier 分析以及偏微分方程（PDE）中有丰富的应用。

# Section 3: 常用不等式

算子的估计以及不等式是 $L^{p}$ 空间的应用的核心，其中最基本的不等式就是 Holder 不等式和 Minkowski 不等式。本节中我们将给出一些其它的重要结果。第一个结论几乎是平凡的，但得益于它的广泛应用，它值得单独列出作为一个定理：

**定理 28.3.1** Chebyshev 不等式

设 $(X,\mathcal{M},\mu)$ 是测度空间，$0<p<\infty$，$f \in L^{p}$，那么对任意 $\alpha>0$ 有

$$
\begin{gather}
\mu(\{ x \mid |f(x)|>\alpha \})\leq \left( \dfrac{\lVert f \rVert _{p}}{\alpha} \right)^{p}
\end{gather}
$$

**证明**

令 $E_{\alpha}=\{ x \mid |f(x)|>\alpha \}$，则

$$
\begin{gather}
\lVert f \rVert _{p}^{p}=\int|f|^{p}\geq \int_{E_{\alpha}}|f|^{p}\geq \int_{E_{\alpha}}\alpha^{p}=\alpha^{p} \mu(E_{\alpha})
\end{gather}
$$

即证。

上述不等式是概率论中的一个基本结论。下一个结果是关于 $L^{p}$ 上的积分算子估计的一个一般定理。

**定理 28.3.2**

设 $(X,\mathcal{M},\mu)$ 和 $(Y,\mathcal{N},\nu)$ 是 $\sigma$-有限的测度空间，$K\colon X\times Y\to \mathbb{C}$ 是 $(\mathcal{M}\otimes \mathcal{N})$-可测函数，并且存在 $C>0$ 使得对 a.e. $y \in Y$ 有 $\int |K(x,y)|\mathrm{d}\mu(x)\leq C$ 且对 a.e. $x \in X$ 有 $\int|K(x,y)|\mathrm{d}\nu(y)\leq C$，而且 $1\leq p\leq \infty$，那么如果 $f \in L^{p}(\nu)$，则对 a.e. $x \in X$，积分

$$
\begin{gather}
Tf(x)=\int K(x,y)f(y)\mathrm{d} \nu(y)
\end{gather}
$$

绝对收敛，并且 $Tf \in L^{p}(\mu)$，$\lVert Tf \rVert_{p}\leq C\lVert f \rVert_{p}$.

**证明**

首先设 $1<p<\infty$，令 $q$ 是 $p$ 的共轭指数，将 Holder 不等式应用在乘积

$$
\begin{gather}
|K(x,y)f(y)|=|K(x,y)|^{1/q} (|K(x,y)|^{1/p}|f(y)|)
\end{gather}
$$

上，则有

$$
\begin{align}
&\int |K(x,y)||f(y)|\mathrm{d} \nu(y)  \\
&\leq \left( \int |K(x,y)| \mathrm{d} \nu(y) \right)^{1/q} \left( \int|K(x,y)||f(y)|^{p} \mathrm{d} \nu(y) \right)^{1/p} \\
&\leq C^{1/q} \left( \int|K(x,y)||f(y)|^{p} \mathrm{d} \nu(y) \right)^{1/p}
\end{align}
$$

从而根据 Fubini-Tonelli 定理，对 a.e. $x \in X$ 有

$$
\begin{align}
\int \left( \int |K(x,y)||f(y)| \mathrm{d} \nu(y) \right)^{p} \mathrm{d} \mu(x) &\leq C^{p/q} \iint |K(x,y)||f(y)|^{p} \mathrm{d} \nu(y) \mathrm{d} \mu(x) \\
&\leq C^{(p/q)+1} \int |f(y)|^{p} \mathrm{d} \nu(y)
\end{align}
$$

由于 $f \in L^{p}(\nu)$，故不等式右边是有限的，从而对 a.e. $x \in X$，函数 $K(x,\cdot)f \in L^{1}(\nu)$，因此 $Tf$ 在 a.e. $x$ 上是良定的，并且

$$
\begin{gather}
\int |Tf(x)|^{p} \mathrm{d} \mu(x)\leq C^{(p/q)+1} \lVert f \rVert _{p}^{p}
\end{gather}
$$

两边取 $p$ 次根，即得 $\lVert Tf \rVert_{p}\leq C\lVert f \rVert_{p}$.

如果 $p=1$，则对 a.e. $x \in X$ 有

$$
\begin{align}
\lVert Tf \rVert _{1} \leq\iint |K(x,y)||f(y)| \mathrm{d} \nu(y)\mathrm{d} \mu(x)\leq C \int |f(y)| \mathrm{d} \nu(y)=C\lVert f \rVert _{1}
\end{align}
$$

如果 $p=\infty$，则对 a.e. $x \in X$ 有

$$
\begin{align}
|Tf(x)| \leq\int |K(x,y)||f(y)| \mathrm{d} \nu(y)\leq \int |K(x,y)| \lVert f \rVert _{\infty} \mathrm{d} \nu(y)\leq C\lVert f \rVert _{\infty}
\end{align}
$$

取本性上确界即得 $\lVert Tf \rVert_{\infty}\leq C\lVert f \rVert_{\infty}$，这就完成了证明。

接下来，我们来看 Minkowski 不等式，它表明一个和的 $L^{p}$ 范数不大于 $L^{p}$ 范数之和，下面我们来将其扩展到积分上。

**定理 28.3.3** Minkowski 不等式

设 $(X,\mathcal{M},\mu)$ 和 $(Y,\mathcal{N},\nu)$ 是 $\sigma$-有限的测度空间，$f\colon X\times Y\to \mathbb{C}$ 是 $(\mathcal{M}\otimes \mathcal{N})$-可测函数，则：

1. 如果 $f\geq 0$ 且 $1\leq p<\infty$，那么

$$
\begin{gather}
\left( \int \left( \int f(x,y)\mathrm{d} \nu(y) \right)^{p} \mathrm{d} \mu(x) \right)^{1/p}\leq \int \left( \int f(x,y)^{p} \mathrm{d} \mu(x) \right)^{1/p} \mathrm{d} \nu(y)
\end{gather}
$$

2. 如果 $1\leq p\leq \infty$，对 a.e. $y$ 有 $f(\cdot,y)\in L^{p}(\mu)$，且 $y\mapsto \lVert f(\cdot,y) \rVert_{p}$ 在 $L^{1}(\nu)$ 中，那么对 a.e. $x$ 有 $f(x,\cdot)\in L^{1}(\nu)$，且 $x\mapsto \int f(x,y)\mathrm{d}\nu(y)$ 在 $L^{p}(\mu)$ 中，并且

$$
\begin{gather}
\left\lVert  \int f(\cdot,y) \mathrm{d} \nu(y)  \right\rVert _{p}\leq \int \lVert f(\cdot,y) \rVert _{p}\mathrm{d} \nu(y)
\end{gather}
$$

**证明**

当 $p=1$ 时 (1) 就退化为 Fubini-Tonelli 定理。设 $1<p<\infty$，令 $q$ 为 $p$ 的共轭指数，取 $g \in L^{q}(\mu)$，则根据 Holder 不等式以及 Fubini-Tonelli 不等式得

$$
\begin{align}
\int \left( \int f(x,y) \mathrm{d} \nu(y) \right) |g(x)| \mathrm{d} \mu(x) &= \iint f(x,y)|g(x)| \mathrm{d} \mu(x)\mathrm{d} \nu(y) \\
&\leq \lVert g \rVert _{q} \int \left( \int f(x,y)^{p} \mathrm{d} \mu(x) \right)^{1/p} \mathrm{d} \nu(y)
\end{align}
$$

如果不等式右边无限，那么结论是平凡的。如果右边有限，令 $h(x)=\int f(x,y)\mathrm{d}\nu(y)$，则 $L^{q}(\mu)$ 上的线性泛函 $g\mapsto \int gh\mathrm{d}\mu$ 是有界的，从而由定理 28.2.2 得

$$
\begin{align}
\left( \int \left( \int f(x,y)\mathrm{d} \nu(y) \right)^{p} \mathrm{d} \mu(x) \right)^{1/p}&=\lVert h \rVert _{p}=\sup_{\lVert g \rVert _{q}=1} \left\lvert \int gh \mathrm{d} \mu  \right\rvert  \\
&\leq \int \left( \int f(x,y)^{p} \mathrm{d} \mu(x) \right)^{1/p} \mathrm{d} \nu(y)
\end{align}
$$

当 $p<\infty$ 时，根据 1 和 Fubini 定理即可证明 2（将 $f$ 替换为 $|f|$ 即可）。当 $p=\infty$ 时，对 a.e. $x,y$ 有 $|f(x,y)|\leq \lVert f(\cdot,y) \rVert_{\infty}$，于是有

$$
\begin{gather}
\left\lvert \int f(x,y) \mathrm{d} \nu(y) \right\rvert \leq \int|f(x,y)|\mathrm{d} \nu(y)\leq \int \lVert f(\cdot,y) \rVert _{\infty} \mathrm{d} \nu(y)
\end{gather}
$$

取本性上确界即证。

当 $\nu$ 是计数测度时，上述定理就退化为原来的 Minkowski 不等式。本节的最后一个结果关于 $(0,\infty)$ 上的 Lebesgue 积分算子。

**定理 28.3.4**

设 $K\colon(0,\infty)^{2}\to \mathbb{C}$ 是 Lebesgue 可测函数，满足对任意 $\lambda>0$ 有 $K(\lambda x,\lambda y)=\lambda^{-1}K(x,y)$，并且 $\int_{0}^{\infty}|K(x,1)|x^{-1/p}\mathrm{d}x=C<\infty$ 对某个 $p \in[1,\infty]$ 成立，令 $q$ 为 $p$ 的共轭指数，对于 $f \in L^{p},g \in L^{q}$，定义

$$
\begin{gather}
Tf(y)=\int_{0}^{\infty} K(x,y)f(x)\mathrm{d} x, \quad Sg(x)=\int_{0}^{\infty} K(x,y)g(y) \mathrm{d} y
\end{gather}
$$

则 $Tf,Sg$ 是 a.e. 良定的，并且 $\lVert Tf \rVert_{p}\leq C\lVert f \rVert_{p},\lVert Sg \rVert_{q}\leq C\lVert g \rVert_{q}$.

**证明**

令 $z=x / y$，则

$$
\begin{gather}
\int_{0}^{\infty}|K(x,y)f(x)|\mathrm{d} x=\int_{0}^{\infty}y |K(zy,y)f(zy)| \mathrm{d} z=\int_{0}^{\infty}|K(z,1)f_{z}(y)|\mathrm{d} z
\end{gather}
$$

其中 $f_{z}(y)=f(zy)$，此外，还有

$$
\begin{gather}
\lVert f_{z} \rVert _{p}=\left( \int_{0}^{\infty}|f(zy)|^{p} \mathrm{d} y \right)^{1/p}=\left( \int_{0}^{\infty}z^{-1} |f(x)|^{p} \mathrm{d} x \right)^{1/p}=z^{-1/p}\lVert f \rVert _{p}
\end{gather}
$$

因此，根据 Minkowski 不等式，$Tf$ 是 a.e. 良定的，并且

$$
\begin{gather}
\lVert Tf \rVert _{p}\leq \int_{0}^{\infty} |K(z,1)|\lVert f_{z} \rVert _{p}\mathrm{d} z=\lVert f \rVert _{p}\int_{0}^{\infty}|K(z,1)|z^{-1/p}\mathrm{d} z=C\lVert f \rVert _{p}
\end{gather}
$$

另一方面，令 $u=y^{-1}$，则有

$$
\begin{align}
\int_{0}^{\infty}|K(1,y)|y^{-1/q}\mathrm{d} y&=\int_{0}^{\infty}|K(y^{-1},1)|y^{-1-1/q} \mathrm{d} y \\
&= \int_{0}^{\infty} |K(u,1)| u^{-1/p} \mathrm{d} u=C
\end{align}
$$

因此同样的证明过程表明 $Sg$ 是 a.e. 良定的，并且 $\lVert Sg \rVert_{q}\leq C\lVert g \rVert_{q}$.

通过选取合适的 $K$，我们有推论如下：

**定理 28.3.5** Hardy 不等式

设 $1<p\leq \infty$，$q$ 是 $p$ 的共轭指数，$f \in L^{p},g \in L^{q}$，定义

$$
\begin{gather}
Tf(y)= y^{-1} \int_{0}^{y} f(x)\mathrm{d} x, \quad Sg(x)=\int_{x}^{\infty} y^{-1} g(y)\mathrm{d} y
\end{gather}
$$

则有

$$
\begin{gather}
\lVert Tf \rVert _{p}\leq \dfrac{p}{p-1} \lVert f \rVert _{p}, \quad \lVert Sg \rVert _{q}\leq q \lVert g \rVert _{q}
\end{gather}
$$

**证明**

在定理 28.3.4 中取 $K(x,y)=y^{-1}\chi_{E}(x,y)$，其中 $E=\{ (x,y) \mid x<y \}$，则有 $\int_{0}^{\infty}|K(x,1)|x^{-1/p}\mathrm{d}x=\int_{0}^{1}x^{-1/p}=p / (p-1)=q$，即证。