本章我们补充一些在无编号类的计数中用到的数论函数，特别是 Euler $\varphi$ 函数和 Mobius 函数 $\mu$.

**定义 A.1** Euler $\varphi$ 函数（Euler totient function）

设整数 $n\geq 1$，定义 $\varphi(n)$ 为 $[n]$ 中与 $n$ 互素的元素的个数，并定义 $\varphi(1)=1$.

显然，对于素数 $p \in \mathcal{P}=\{ 2,3,5,7,\dots \}$，小于它的所有数都与它互素，因此 $\varphi(p)=p-1$. 进一步，对于 $p^{k}$，与它不互素的只有包含因子 $p$ 的数，于是我们有

$$
\begin{gather}
\varphi(p^{k})=p^{k}-p^{k-1}=p^{k}(1-p^{-1})
\end{gather}
$$

为了将上述公式推广到一般的 $n$，我们还需要一个性质，即函数 $\varphi$ 是**积性的**：如果 $a,b$ 互素，那么 $\varphi(ab)=\varphi(a)\varphi(b)$. 由此，再根据算术基本定理即可证明以下结论：

**定理 A.2**

设整数 $n\geq 1$，则有 $\varphi(n)=n\prod_{p\ \mid\ n}(1-p^{-1})$

**证明**

我们只需证明 $\varphi$ 的积性，因为算术基本定理指出，任意 $n$ 可以唯一地分解为素数的乘积：$n=p_{1}^{k_{1}}\cdots p_{n}^{k_{n}}$，从而有

$$
\begin{gather}
\varphi(n)=\varphi(p_{1}^{k_{1}})\cdots \varphi(p_{n}^{k_{n}})=n(1-p_{1}^{-1})\cdots (1-p_{n}^{-1})
\end{gather}
$$

设 $a,b$ 是互素的，将 $[ab]$ 中的数排成一个 $a\times b$ 的矩阵：

$$
\begin{gather}
1 & 2 & \dots & b-1 & b \\
b+1 & b+2 & \dots & 2b-1 & 2b \\
\vdots & \vdots & \ddots & \vdots & \vdots \\
(a-1)b+1 & (a-1)b+2 & \dots & ab-1 & ab
\end{gather}
$$

如果 $i$ 与 $b$ 不互素，那么去掉矩阵中的第 $i$ 列，留下 $\varphi(b)$ 列，下面考虑剩下的某一列 $j,j+b, \dots,j+(a-1)b$ 中与 $ab$ 互素的元素个数。由于 $j$ 与 $b$ 互素，故我们只需考虑与 $a$ 互素的元素个数。又由于 $a,b$ 互素，故

$$
\begin{gather}
(j+kb) \bmod a,\quad k=0,1,\dots,a-1
\end{gather}
$$

可以取遍模 $a$ 的所有余数 $\{ 0,1,\dots,a-1 \}$，其中与 $a$ 互素的数共有 $\varphi(a)$ 个，从而我们有 $\varphi(ab)=\varphi(a)\varphi(b)$，这就完成了证明。

**定义 A.3** Mobius 函数

设整数 $n\geq 1$，定义 $\mu(n)=(-1)^{r}$ 如果 $n$ 是 $r$ 个不同的素数之积，在其余情况下定义 $\mu(n)=0$.

许多关于数论函数的性质可以通过生成函数的方法来得到，这正是解析数论中所用到的技术。

**定义 A.4** Dirichlet 生成函数

序列 $(a_{n})_{n\geq 1}$ 的 **Dirichlet 生成函数**（DGF）定义为形式级数

$$
\begin{gather}
\alpha(s)=\sum_{n\geq 1} \dfrac{a_{n}}{n^{s}}
\end{gather}
$$

特别地，常序列 $a_{n}=1$ 对应的 DGF 正是 Riemann $\zeta$ 函数

$$
\begin{gather}
\zeta(s)=\sum_{n=1}^{\infty} \dfrac{1}{n^{s}}
\end{gather}
$$

于是，算术基本定理就给出了如下等式：

$$
\begin{align}
\zeta(s) &= \prod_{p} \left( 1+\dfrac{1}{p^{s}}+\dfrac{1}{p^{2s}}+\cdots \right)=\prod_{p} \dfrac{1}{1-p^{-s}}
\end{align}
$$

其中 $p$ 取遍所有素数。从而对于 Mobius 函数我们有

$$
\begin{gather}
M(s)=\sum_{n=1}^{\infty} \dfrac{\mu(n)}{n^{s}}=\prod_{p}\left( 1-\dfrac{1}{p^{s}} \right)=\dfrac{1}{\zeta(s)}
\end{gather}
$$

最后，设序列 $(a_{n}),(b_{n}),(c_{n})$ 的 DGF 分别为 $\alpha(s),\beta(s),\gamma(s)$，则我们有

$$
\begin{gather}
\alpha(s)=\beta(s)\gamma(s) \iff a_{n}=\sum_{d\ \mid\ n} b_{d}c_{n / d}
\end{gather}
$$

特别地，当 $c_{n}=1$ 即 $\gamma(s)=\zeta(s)$ 时，我们有

$$
\begin{gather}
\alpha(s)=\beta(s)\zeta(s) \iff \beta(s)=M(s)\alpha(s)
\end{gather}
$$

这就给出了 **Mobius 反演**

$$
\begin{gather}
a_{n}=\sum_{d\ \mid\ n} b_{d} \iff b_{n}=\sum_{d\ \mid\ n} \mu(d) a_{n / d}
\end{gather}
$$

这一关系被用于求解包含 $\mathrm{MSet}$ 的隐式构造问题，以及无编号循环构造的计数中。