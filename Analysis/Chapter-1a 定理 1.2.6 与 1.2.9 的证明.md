**定理 1.2.6**

设 $k,m,n \in \mathbb{N}$，则有：

1. $m+n'=(m+n)',m \cdot n'=(m \cdot n)+m$.
2. 交换律：$m+n=n+m,mn=nm$.
3. 结合律：$(k+m)+n=k+(m+n),(km)n=k(mn)$.
4. 分配律：$k(m+n)=km+kn$.
5. 消去律：$k+m=k+n\implies m=n$. $km=kn,k\neq 0\implies m=n$.
6. 如果 $mn=0$，则 $m=0$ 或 $n=0$.

**证明**

首先证明关于加法的性质。

(1). 对 $m$ 归纳。$0+n'=n'=(0+n)'$，设 $m+n'=(m+n)'$，则

$$
m'+n'=(m+n')'=(m+n)''=(m'+n)'
$$

(2). 先证 $m+0=0+m$. 对 $m$ 归纳，$0+0=0+0$，设 $m+0=0+m$，则

$$
m'+0=(m+0)'=(0+m)'=0+m'
$$

再对 $n$ 归纳。$m+0=0+m$，设 $m+n=n+m$，则

$$
m+n'=(m+n)'=(n+m)'=n'+m
$$

(3). 对 $n$ 归纳。$(k+m)+0=k+m=k+(m+0)$，（省略归纳假设）我们有

$$
(k+m)+n'=(k+m+n)'=k+(m+n)'=k+(m+n')
$$

(5). 对 $k$ 归纳。显然 $0+m=0+n \implies m=n$，设 $k'+m=k'+n$，则 $(k+m)'=(k+n)'$，即 $k+m=k+n$，由归纳假设得 $m=n$.

接下来证明关于乘法的性质。

(4). 对 $k$ 归纳。$0(m+n)=0=0\cdot m+0\cdot n$，且

$$
k'(m+n)=(k(m+n))+(m+n)=km+kn+m+n=k'\cdot m+k'\cdot n
$$

(1). 对 $m$ 归纳。$0\cdot n'=0=(0\cdot n)+0$，且

$$
\begin{gather*}
m'\cdot n'=(m\cdot n')+n'=mn+m+n' \\
(m'\cdot n)+m'=mn+n+m'
\end{gather*}
$$

再根据 $m+n'=n+m'=(m+n)'$ 即证。

(2). 先证 $m\cdot 0=0\cdot m$。$0\cdot 0=0\cdot 0$，且 $m' \cdot 0=(m\cdot 0)+0=0=0\cdot m'$.

再对 $n$ 归纳。我们有

$$
m\cdot n'=(m\cdot n)+m=(n\cdot m)+m=n' \cdot m
$$

(3). 对 $n$ 归纳。$(km)\cdot 0=0=k(m\cdot 0)$，且

$$
(km)\cdot n'=kmn+km=k(mn+m)=k(m\cdot n')
$$

(6). 我们证明其逆否命题，即 $m\neq 0 \text{且} n\neq 0\implies mn\neq 0$.

设 $m,n\neq 0$，则有 $k,\ell \in \mathbb{N}$ 使得 $k'=m,\ell'=n$，于是

$$
mn=k'\cdot n=kn+n=kn+\ell'=(kn+\ell)'\neq 0
$$

这一定理表明自然数没有零因子，即不存在 $m,n\neq 0$ 使得 $mn=0$.

(5). 对 $n$ 归纳。设 $km=k\cdot 0=0$，由于 $k\neq 0$，则有 $m=0=n$. 设 $km=kn'$，则 $km=kn+k$，显然 $m\neq 0$，则有 $\ell$ 使得 $\ell'=m$，从而有 $k\ell+k=kn+k$，根据加法消去律有 $k\ell=kn$，从而 $n=\ell$，即 $n'=m$. 这就完成了证明。

**定理 1.2.9**

设 $k,m,n \in \mathbb{N}$，则有：

1. 若 $m<n$，则 $m'\leq n$.
2. 反自反性：$n \not< n$.
3. 反对称性：$m\leq n,n\leq m \implies m=n$.
4. 传递性：$k<m,m<n \implies k<n$.
5. 完全性：$m\leq n$ 与 $n\leq m$ 至少有一个成立。
6. 三分律：$m<n,m=n,m>n$ 有且仅有一个成立。
7. 保序性：$m<n\implies k+m<k+n$. $m<n,k\neq 0\implies km<kn$.

**证明**

(1). 根据定义我们有 $k \in \mathbb{N} \setminus \{ 0 \}$ 使得 $m+k=n$，从而有 $\ell'=k$，于是 $m+\ell'=(m+\ell)'=m'+\ell=n$，即 $m'\leq n$.

(2). 假设 $n<n$，则有 $n\leq n$ 且 $n\neq n$，这与 $n=n$ 矛盾。

(3). 根据定义有 $k,\ell \in \mathbb{N}$ 满足 $m+k=n,n+\ell=m$，则 $n+k+\ell=n$，消去 $n$ 得 $k+\ell=0$，这表明 $k=\ell=0$（否则就有 $0=(k+x)'$ ）。于是有 $m=n$.

(4). 由定义有 $p,q \in \mathbb{N}\setminus \{ 0 \}$ 使得 $m=k+p,n=m+q$，则 $n=k+p+q$，可以验证 $p+q\neq 0$，于是 $k<n$. 用同样的方法也可以证明 $\leq$ 的传递性。

(5). 对 $n$ 归纳。对任意 $m$ 都有 $0\leq m$，假设 $m\leq n$ 与 $n\leq m$ 至少有一成立，考虑 $n'$ 与 $m$ 的序：

如果 $m\leq n$，则 $m+k=n$，于是 $n'=(m+k)'=m+k'$，即 $m\leq n'$.

现设 $n\leq m$，如果 $n=m$，则 $n'=m'=m+0'$，即 $m\leq n'$.

如果 $n\neq m$，则 $n<m$，从而 $n'\leq m$. 于是 $n'\leq m$ 和 $m\leq n'$ 至少有一成立，这就完成了证明。

(6). 如果 $n\leq m$ 且 $m\leq n$，则 $n=m$.

如果 $n\leq m$ 但 $m \not\leq n$，则 $n<m$. 反之，则有 $m<n$. 

在这三种情况中，$n<m,n=m,m<n$ 三者有且仅有一个成立，这就完成了证明。

(7). 首先证明加法保序性。

设 $m<n$，则有 $\ell\neq 0$ 使得 $m+\ell=n$，则有 $k+m+\ell=k+n$，即 $k+m<k+n$.

然后证明乘法保序性。

设 $m<n$，则 $m+\ell=n,\ell\neq 0$，于是 $k(m+\ell)=km+k\ell=kn$，由于 $k\neq 0$，则 $k\ell\neq 0$，这表明 $km<kn$. 这就完成了证明。

最后我们补充一个自然数算术系统的同构唯一性的证明。

**定理**

设 $(X,x_{0},s,+,\cdot,<)$ 是一个自然数算术系统，则存在双射 $f\colon \omega\to X$ 满足：

$$
\begin{cases}
f(0)=x_{0} \\
f(n')=s(f(n)) \\
f(n+m)=f(n)+f(m) \\
f(n\cdot m)=f(n)\cdot f(m) \\
n<m\implies f(n)<f(m)
\end{cases}
$$

**证明**

根据定理 1.2.3，存在双射 $f\colon \omega\to X$ 满足 $f(0)=x_{0},f(n')=s(f(n))$，接下来我们证明 $f$ 满足下面三个条件。

对 $n$ 归纳。$f(0+m)=f(m)=x_{0}+f(m)=f(0)+f(m)$，假设 $f(n+m)=f(n)+f(m)$，则

$$
\begin{align*}
f(n'+m) &= s(f(n+m)) \\
&= s(f(n)+f(m)) \\
&= s(f(n))+f(m) \\
&= f(n')+f(m)
\end{align*}
$$

$f(0\cdot m)=f(0)=x_{0}=f(0)\cdot f(m)$，假设 $f(n\cdot m)=f(n)\cdot f(m)$，则

$$
\begin{align*}
f(n'\cdot m) &= f(n\cdot m+m) \\
&= f(n\cdot m)+f(m) \\
&= f(n)\cdot f(m)+f(m) \\
&= s(f(n))\cdot f(m) \\
&= f(n')\cdot f(m)
\end{align*}
$$

设 $n<m$，则有 $n+k=m,k\neq 0$，于是 $f(n+k)=f(n)+f(k)=f(m)$. 由于 $f$ 是双射，故 $f(k)\neq x_{0}$，于是有 $f(n)<f(m)$.

于是我们证明了由 Peano 公理和定义 1.2.4，1.2.5，1.2.8 所限定的自然数算术系统 $(\mathbb{N},0,s,+,\cdot,<)$ 在同构的意义下是唯一的。