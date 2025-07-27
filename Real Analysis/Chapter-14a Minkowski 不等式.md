Minkowski 不等式是分析学中的一个重要不等式，它的证明依赖于 Holder 不等式，而后者的证明又依赖于 Young 不等式，因此我们从 Young 不等式开始证明。

**定理 1** Young 不等式

设实数 $a,b\geq 0,p,q>1$ 满足 $\dfrac{1}{p}+\dfrac{1}{q}=1$，则有

$$
ab\leq \dfrac{a^{p}}{p}+\dfrac{b^{q}}{q}
$$

等号成立当且仅当 $a^{p}=b^{q}$.

**证明**

固定 $b$，构造函数 $f\colon [0,+\infty)\to \mathbb{R}$ 为

$$
f(x)=\dfrac{x^{p}}{p}+\dfrac{b^{q}}{q}-bx
$$

则 $f$ 在 $[0,+\infty)$ 可微，其导数为

$$
f'(x)=x^{p-1}-b
$$

令 $f'(x)=0$，解得 $x=b^{1/(p-1)}$，代入得

$$
f(x)=\dfrac{b^{p/(p-1)}}{p}+\dfrac{b^{q}}{q}-b^{p/(p-1)}=b^{q}\left( \dfrac{1}{p}+\dfrac{1}{q}-1 \right)=0
$$

由于 $p>1$，故在 $x=b^{1/(p-1)}$ 左侧 $f'(x)<0$，右侧 $f'(x)>0$，从而 $f$ 在 $x=b^{1/(p-1)}$ 处达到全局最小值，因此对任意 $x \in[0,+\infty)$ 有 $f(x)\geq 0$.

等号成立当且仅当 $a=b^{1/(p-1)}$，当且仅当 $a^{p}=b^{p/(p-1)}=b^{q}$，这就完成了证明。

**定理 2** Holder 不等式

设实数 $p,q>1$ 满足 $\dfrac{1}{p}+\dfrac{1}{q}=1$，则对任意 $a,b \in \mathbb{R}^{n}$ 有

$$
\sum_{i=1}^{n}|a_{i}b_{i}|\leq \left( \sum_{i=1}^{n}|a_{i}|^{p} \right)^{1/p} \left( \sum_{i=1}^{n}|b_{i}|^{q} \right)^{1/q}
$$

等号成立当且仅当存在不全为零的实数 $c_{1},c_{2}\geq 0$ 使得对任意 $1\leq i\leq n$ 有 $c_{1}|a_{i}|^{p}=c_{2}|b_{i}|^{q}$.

**证明**

令 $A=\left( \sum_{i=1}^{n}|a_{i}|^{p} \right)^{1/p},B=\left( \sum_{i=1}^{n}|b_{i}|^{q} \right)^{1/q}$，如果 $A=0$ 或者 $B=0$，那么 $a=0$ 或者 $b=0$，此时等号成立。

设 $A>0$ 且 $B>0$，定义 $x_{i}=\dfrac{|a_{i}|}{A},y_{i}=\dfrac{|b_{i}|}{B}$，则 $\sum_{i=1}^{n}x_{i}^{p}=\sum_{i=1}^{n}y_{i}^{q}=1$，对每个 $x_{i}y_{i}$ 应用 Young 不等式得

$$
x_{i}y_{i}\leq \dfrac{x_{i}^{p}}{p}+\dfrac{y_{i}^{q}}{q}
$$

对 $i$ 求和，于是有

$$
\sum_{i=1}^{n}x_{i}y_{i}= \sum_{i=1}^{n} \dfrac{|a_{i}b_{i}|}{AB} \leq \dfrac{1}{p}+\dfrac{1}{q}=1
$$

即证。等号成立当且仅当对每个 $i$ 都有 $x_{i}^{p}=y_{i}^{q}$，即 $B^{q} |a_{i}|^{p}=A^{p} |b_{i}|^{q}$，当 $a=0$ 或者 $b=0$ 时上式也满足，这就完成了证明。

**定理 3** Minkowski 不等式

设实数 $p\geq 1$，则对任意 $a,b \in \mathbb{R}^{n}$ 有

$$
\left( \sum_{i=1}^{n} |a_{i}+b_{i}|^{p} \right)^{1/p}\leq \left( \sum_{i=1}^{n} |a_{i}|^{p} \right)^{1/p}+\left( \sum_{i=1}^{n} |b_{i}|^{p} \right)^{1/p}
$$

等号成立当且仅当存在不全为零的实数 $c_{1},c_{2}\geq 0$ 使得对任意 $1\leq i\leq n$ 有 $c_{1}|a_{i}|=c_{2}|b_{i}|$.

**证明**

当 $p=1$ 时，不等式就是绝对值的三角不等式。现设 $p>1$，我们有

$$
S=\sum_{i=1}^{n} |a_{i}+b_{i}|^{p}\leq \sum_{i=1}^{n}|a_{i}+b_{i}|^{p-1}|a_{i}|+\sum_{i=1}^{n}|a_{i}+b_{i}|^{p-1}|b_{i}|
$$

设 $q=\dfrac{p}{p-1}$，则有 $\dfrac{1}{p}+\dfrac{1}{q}=1$，利用 Holder 不等式得

$$
\sum_{i=1}^{n}|a_{i}+b_{i}|^{p-1}|a_{i}|\leq \left( \sum_{i=1}^{n}|a_{i}|^{p} \right)^{1/p} \left( \sum_{i=1}^{n} |a_{i}+b_{i}|^{p} \right)^{1/q}
$$

对另一项也有类似的结论，从而

$$
S\leq S^{1/q}\left( \left( \sum_{i=1}^{n} |a_{i}|^{p} \right)^{1/p}+\left( \sum_{i=1}^{n} |b_{i}|^{p} \right)^{1/p} \right) 
$$

当 $S=0$ 时等号成立，此时有 $a_{i}=-b_{i}$，即 $|a_{i}|=|b_{i}|$. 当 $S>0$ 时，在不等式两边乘以 $S^{-1/q}$ 再根据 $\dfrac{1}{p}+\dfrac{1}{q}=1$ 即证。

等号成立当且仅当存在不全为零的实数 $c_{1},c_{2},c_{3},c_{4}\geq 0$ 使得

$$
c_{1}|a_{i}+b_{i}|^{p}=c_{2}|a_{i}|^{p},c_{3}|a_{i}+b_{i}|^{p}=c_{4}|b_{i}|^{p}
$$

即存在不全为零的实数 $k_{1},k_{2}\geq 0$ 使得 $k_{1}|a_{i}|=k_{2}|b_{i}|$，当 $S=0$ 时上式也满足，这就完成了证明。