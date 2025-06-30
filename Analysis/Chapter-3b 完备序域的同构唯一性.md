本章我们将证明完备序域在同构下是唯一的，具体来说，就是：

**定理**

设 $(\overline{\mathbb{R}},\overline{0},\overline{1},+,\cdot,<)$ 是一个 Archimedes 序域，且具有确界性质，则存在双射 $\varphi\colon \mathbb{R}\to \overline{\mathbb{R}}$ 满足：

$$
\begin{cases}
\varphi(0)=\overline{0} \\
\varphi(1)=\overline{1} \\
\varphi(x+y)=\varphi(x)+\varphi(y) \\
\varphi(xy)=\varphi(x)\varphi(y) \\
x<y \implies \varphi(x)<\varphi(y)
\end{cases}
$$

我们将以 $\mathbb{N}-\mathbb{Z}-\mathbb{Q}-\mathbb{R}$ 的顺序逐步构造上述同构。

# 自然数

首先令 $\varphi(0)=\overline{0},\varphi(1)=\overline{1}$，则我们有

**定理 1**

$\overline{0}<\overline{1}$

**证明**

域公理保证了 $\overline{0}\neq \overline{1}$. 假设 $\overline{0}>\overline{1}$，则 $\overline{0}+(-\overline{1})>\overline{1}+(-\overline{1})$，即 $-\overline{1}>\overline{0}$，于是 $\overline{0}\cdot (-\overline{1})>\overline{1}\cdot(-\overline{1})$，即 $\overline{0}> -\overline{1}$，矛盾。

下面将 $\mathbb{N}$ 与 $\overline{\mathbb{N}}$ 对应，设 $n \in \mathbb{N}$，令 $\varphi(n)=\overline{n}$，其中 $\overline{n}=\overline{1}+\dots+\overline{1}$（ $n$ 个 $\overline{1}$ ）。

我们可以证明 $\mathbb{N}$ 同构于 $\overline{\mathbb{N}}$，即：

**定理 2**

设 $m,n \in \mathbb{N}$，则：

1. $\overline{m+n}=\overline{m}+\overline{n}$
2. $\overline{m\cdot n}=\overline{m}\cdot  \overline{n}$
3. $m<n \implies  \overline{m}<\overline{n}$

**证明**

(1). 用归纳法。$\overline{m+0}=\overline{m}=\overline{m}+\overline{0}$，设 $\overline{m+n}=\overline{m}+\overline{n}$，则

$$
\overline{m+n+1}=\overline{m+n}+\overline{1}=\overline{m}+\overline{n}+\overline{1}=\overline{m}+\overline{n+1}
$$

2 同理。对于 3，首先用归纳法证明 $n>0 \implies  \overline{n}>\overline{0}$（ $\overline{n}+\overline{1}\geq \overline{1}>\overline{0}$ ），设 $m<n$，则 $n-m>0$，于是 $\overline{n}=\overline{m}+\overline{n-m}>\overline{m}$.

# 整数和有理数

对于非负整数（自然数），我们已经定义了 $\varphi$ 的值，对于 $-n \in \mathbb{Z},n> 0$，令 $\varphi(-n)=-\overline{n}$，我们可以验证 $\mathbb{Z}$ 同构于 $\overline{\mathbb{Z}}$.

在这之后我们将 $\mathbb{Q}$ 与 $\overline{\mathbb{Q}}$ 对应。设 $\dfrac{m}{n} \in \mathbb{Q}$，令 $\varphi \left( \dfrac{m}{n} \right)=\dfrac{\overline{m}}{\overline{n}}$，我们可以证明：

**定理 3**

设 $\dfrac{m}{n}, \dfrac{p}{q} \in \mathbb{Q}$，则：

1. $\varphi \left( \dfrac{m}{n}+\dfrac{p}{q} \right)=\varphi \left( \dfrac{m}{n} \right)+\varphi \left( \dfrac{p}{q} \right)$
2. $\varphi \left( \dfrac{m}{n}\cdot \dfrac{p}{q} \right)=\varphi \left( \dfrac{m}{n} \right)\cdot\varphi \left( \dfrac{p}{q} \right)$
3. $\dfrac{m}{n}< \dfrac{p}{q} \implies \varphi \left( \dfrac{m}{n} \right)<\varphi \left( \dfrac{p}{q} \right)$

**证明**

1 和 2 是显然的，通分并使用 $\mathbb{Z}$ 和 $\overline{\mathbb{Z}}$ 的同构性质即可。对于 3，设 $n,q>0$，我们有 $mq<np \implies  \overline{mq}<\overline{np}$，即证。

# 实数

设 $x \in \mathbb{R}\setminus \mathbb{Q}$，我们可以找到以 $x$ 为上确界的有理数递增序列

$$
r_{0}<r_{1}<\dots<r_{n}<\cdots
$$

根据 $\overline{\mathbb{R}}$ 的确界性质，序列 $(\overline{r_{n}})$ 在 $\overline{\mathbb{R}}$ 中有上确界 $\overline{x}$，令 $\varphi(x)=\overline{x}$.

我们需要验证该定义的良定性。当 $x \in \mathbb{R}\setminus \mathbb{Q}$ 时，设递增序列 $(r_{n}),(s_{n})$ 的上确界都为 $x$，$\overline{y}=\sup(\overline{r_{n}}),\overline{z}=\sup(\overline{s_{n}})$，我们要证 $\overline{y}=\overline{z}$.

反设 $\overline{y}<\overline{z}$，则存在 $\overline{s_{i}}$ 使得 $\overline{y}<\overline{s_{i}}$，由于 $s_{i}<x$，故存在 $r_{k}$ 满足 $s_{i}<r_{k}$，从而 $\overline{s_{i}}<\overline{r_{k}}<\overline{y}$，矛盾。反之同理，因此 $\overline{y}=\overline{z}$.

下面我们就可以验证：

**定理 4**

1. $\varphi$ 是满射
2. $\varphi(x+y)=\varphi(x)+\varphi(y)$
3. $\varphi(xy)=\varphi(x)\varphi(y)$
4. $x<y \implies\varphi(x)<\varphi(y)$

**证明**

(1). 任取 $\overline{x} \in \overline{\mathbb{R}}$，我们可以找到以 $\overline{x}$ 为上确界的递增序列 $(\overline{r_{n}})$，设 $\mathbb{R}$ 中的序列 $(r_{n})$ 的上确界为 $x$，则 $\varphi(x)=\overline{x}$.

2 和 3 可以根据有理数的同构性得到（ $\overline{r_{n}+s_{n}}=\overline{r_{n}}+\overline{s_{n}}$ ）。

(4). 设 $x=\sup(r_{n}),y=\sup(s_{n})$，则有 $s_{k}$ 使得对所有 $r_{i}$ 有 $r_{i}\leq x < s_{k}$，从而 $\overline{r_{i}}<\overline{s_{k}}$，于是 $\overline{x}\leq \overline{s_{k}}<\overline{y}$.

$\varphi$ 的保序性蕴含了单射性，因此 $\varphi$ 是一个双射，并且保持加法、乘法和序不变，这就完成了证明。

在下一章我们用真正的极限替换形式极限后，我们就不用再考虑实数的内部结构了。