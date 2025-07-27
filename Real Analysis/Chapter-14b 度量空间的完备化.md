我们将仿照从有理数中构造实数的方法进行度量空间的完备化。

设 $(X,d)$ 是一个度量空间，记 $X$ 上的 Cauchy 序列构成的集合为 $S$，在 $S$ 上定义等价关系 $\sim$ 使得 $(x_{n})\sim(y_{n})$ 当且仅当 $(x_{n})$ 等价于 $(y_{n})$，下面我们定义

$$
\overline{X}=S / \sim
$$

作为完备化的第一步。

第二步，我们定义度量函数 $\overline{d}\colon \overline{X}^{2}\to \mathbb{R}$ 满足

$$
\overline{d}([(x_{n})],[(y_{n})])=\lim_{ n \to \infty } d(x_{n},y_{n})
$$

**定理 1**

$\overline{d}$ 是良定的，并且 $(\overline{X},\overline{d})$ 是一个度量空间。

**证明**

首先我们要证明，极限 $\lim_{ n \to \infty }d(x_{n},y_{n})$ 总是存在，我们来证明实数序列 $(d(x_{n},y_{n}))$ 是一个 Cauchy 序列。

由于 $(x_{n}),(y_{n})$ 是 Cauchy 序列，故对任意 $\varepsilon>0$，存在 $N$ 使得对任意 $n,m>N$ 有 $d(x_{n},x_{m})<\varepsilon,d(y_{n},y_{m})<\varepsilon$，从而当 $d(x_{n},y_{n})>d(x_{m},y_{m})$ 时有

$$
|d(x_{n},y_{n})-d(x_{m},y_{m})|\leq d(x_{n},x_{m})+d(y_{m},y_{n})<2\varepsilon
$$

当 $d(x_{n},y_{n})\leq d(x_{m},y_{m})$ 时也有同样的结论，因此 $(d(x_{n},y_{n}))$ 是 Cauchy 序列，由 $\mathbb{R}$ 的完备性知其收敛。

下面证明 $(x_{n})\sim(x_{n}'),(y_{n})\sim(y_{n}')$ 时 $\lim_{ n \to \infty }d(x_{n},y_{n})=\lim_{ n \to \infty }d(x_{n}',y_{n}')$.

任取 $\varepsilon>0$，存在 $N$ 使得对任意 $n>N$ 有 $d(x_{n},x_{n}')<\varepsilon,d(y_{n},y_{n}')<\varepsilon$，从而当 $d(x_{n},y_{n})>d(x_{n}',y_{n}')$ 时有

$$
|d(x_{n},y_{n})-d(x_{n}',y_{n}')|\leq d(x_{n},x_{n}')+d(y_{n}',y_{n})<2\varepsilon
$$

当 $d(x_{n},y_{n})\leq d(x_{n}',y_{n}')$ 时同理，故 $\lim_{ n \to \infty }|d(x_{n},y_{n})-d(x_{n}',y_{n}')|=0$，即证。因此 $\overline{d}$ 是良定的，下面验证 $\overline{d}$ 是一个度量。

对称性是显然的。并且当 $[(x_{n})]=[(y_{n})]$ 时显然也有 $\overline{d}([(x_{n})],[(y_{n})])=0$，现设 $[(x_{n})] \neq [(y_{n})]$，则 $(x_{n})$ 不等价于 $(y_{n})$，即 $\lim_{ n \to \infty }d(x_{n},y_{n})\neq 0$，由于 $d(x_{n},y_{n})\geq 0$，故其极限 $>0$，这样就证明了正定性。

对于三角不等式，我们有

$$
\overline{d}(x,y)=\lim_{ n \to \infty } d(x_{n},y_{n})\leq \lim_{ n \to \infty } (d(x_{n},z_{n})+d(z_{n},y_{n}))=\overline{d}(x,z)+\overline{d}(z,y)
$$

这就完成了证明。

第三步，我们来证明 $(\overline{X},\overline{d})$ 是完备的，这也是最重要的一步。

**定理 2**

度量空间 $(\overline{X},\overline{d})$ 是完备的。

**证明**

设 $(x^{(k)})$ 是 $\overline{X}$ 上的 Cauchy 序列，我们要证它收敛于某个 $x \in \overline{X}$.

对于每个 $k$，我们知道序列 $x^{(k)}=(x^{(k)}_{n})$ 是一个 Cauchy 序列，从而存在 $N_{k}$ 使得对任意 $n>N_{k}$ 有

$$
d(x_{n}^{(k)},x_{N_{k}}^{(k)})<\dfrac{1}{k}
$$

定义 $X$ 中的序列 $y_{k}=x_{N_{k}}^{(k)}$，我们要证 $(y_{k})$ 是一个 Cauchy 序列。由于 $(x^{(k)})$ 是 Cauchy 序列，故对任意 $\varepsilon>0$ 有 $M_{1}$ 使得对任意 $i,j>M_{1}$ 有

$$
\overline{d}(x^{(i)},x^{(j)})=\lim_{ n \to \infty } d(x_{n}^{(i)},x_{n}^{(j)})<\varepsilon
$$

于是有 $M_{2}$ 使得对任意 $n>M_{2}$ 有 $d(x_{n}^{(i)},x_{n}^{(j)})<\varepsilon$. 现在取 $N>\max(M_{2},N_{i},N_{j})$，则有

$$
d(y_{i},y_{j})\leq d(x_{N_{i}}^{(i)},x_{N}^{(i)})+d(x_{N}^{(i)},x_{N}^{(j)})+d(x_{N}^{(j)},x_{N_{j}}^{(j)})< \varepsilon+\dfrac{1}{i}+\dfrac{1}{j}
$$

当 $M_{1}$ 足够大时，可以使 $\dfrac{1}{i}+\dfrac{1}{j}<\varepsilon$，故 $(y_{k})$ 是一个 Cauchy 序列，于是存在 $x=[(y_{k})] \in \overline{X}$，现在我们要证 $\lim_{ k \to \infty;\overline{d} }x^{(k)}=x$.

取正整数 $K$，当 $k>K$ 时，我们有

$$
d(x_{n}^{(k)},y_{n})\leq d(x_{n}^{(k)},y_{k})+d(y_{k},y_{n})=d(x_{n}^{(k)},x_{N_{k}}^{(k)})+d(y_{k},y_{n})
$$

存在 $K_{1}$ 使得对任意 $k>K_{1}$ 和 $n>N_{k}$ 有 $d(x_{n}^{(k)},x_{N_{k}}^{(k)})<\dfrac{1}{k}<\varepsilon$，并且还存在 $K_{2}$ 使得对任意 $k,n>K_{2}$ 有 $d(y_{k},y_{n})<\varepsilon$. 令 $K=\max(K_{1},K_{2})$，则当 $k>K$ 和 $n>\max(N_{k},K_{2})$ 时有

$$
d(x_{n}^{(k)},y_{n})\leq d(x_{n}^{(k)},x_{N_{k}}^{(k)})+d(y_{k},y_{n})<2\varepsilon
$$

对 $n\to \infty$ 取极限，则有 $\overline{d}(x^{(k)},x)\leq 2\varepsilon$，因此 $(x^{(k)})$ 收敛于 $x$，这就完成了证明。

第四步，我们将 $X$ 同构嵌入 $\overline{X}$，我们将常值序列 $[(x)]$ 等同于 $x \in X$，并且有

$$
\overline{d}([(x)],[(y)])=\lim_{ n \to \infty }d(x,y)=d(x,y)
$$

因此 $(X,d)$ 就可以看作是 $(\overline{X},\overline{d})$ 的子空间。

第五步，我们证明 $X$ 的闭包就是 $\overline{X}$，这解释了选用符号 $\overline{X}$ 的原因。

**定理 3**

$X$ 在 $(\overline{X},\overline{d})$ 中的闭包是 $\overline{X}$.

**证明**

设 $x \in \overline{X}$，我们要证明 $x$ 是 $X$ 的附着点。由于 $x=[(x_{n})]$ 是 Cauchy 序列，故对任意 $\varepsilon>0$，存在 $N$ 使得对任意 $n>N$ 有 $d(x_{n},x_{N})<\varepsilon$，从而

$$
\overline{d}(x,x_{N})=\lim_{ n \to \infty } d(x_{n},x_{N})\leq \varepsilon
$$

其中 $x_{N}\in X$，因此 $x$ 是 $X$ 的附着点，这就完成了证明。

最后，我们可以丢弃繁琐的等价类符号 $[(x_{n})]$，而使用极限来替代它。

**定理 4**

设 $(x_{n})$ 是 $X$ 中的一个 Cauchy 序列，那么 $\lim_{ n \to \infty;\overline{d} }x_{n}=[(x_{n})]$.

**证明**

根据完备性，我们知道 $\lim_{ n \to \infty;\overline{d} }x_{n}\in \overline{X}$，从而有 $X$ 中的 Cauchy 序列 $(y_{n})$ 使得 $[(y_{n})]=\lim_{ n \to \infty;\overline{d} }x_{n}$，故对任意 $\varepsilon>0$ 有 $N_{1}$ 使得对任意 $n>N_{1}$ 有

$$
\overline{d}([(y_{n})],x_{n})=\lim_{ k \to \infty } d(y_{k},x_{n})<\varepsilon
$$

故存在 $K>N_{1}$ 使得对任意 $k>K$ 有 $d(y_{k},x_{n})<\varepsilon$. 由于 $(x_{n})$ 是 Cauchy 序列，故存在 $N_{2}>K$ 使得对任意 $n>N_{2}$ 有 $d(x_{n},x_{N_{2}})<\varepsilon$，于是对任意 $n>N_{2}$ 有

$$
d(x_{n},y_{n})\leq d(x_{n},x_{N_{2}})+d(x_{N_{2}},y_{n})<2\varepsilon
$$

这表明 $(x_{n})\sim(y_{n})$，故

$$
\lim_{ n \to \infty;\overline{d} } x_{n}=[(y_{n})]=[(x_{n})]
$$

即证。

通过上述六个步骤，我们就从度量空间 $(X,d)$ 中构造出了一个完备度量空间 $(\overline{X},\overline{d})$，也就是说，我们证明了以下定理：

**定理 14.3.9** 度量空间的完备化（completion）

设 $(X,d)$ 是度量空间，则存在一个完备度量空间 $(\overline{X},\overline{d})$，其包含 $(X,d)$ 作为它的子空间，并且 $X$ 在 $(\overline{X},\overline{d})$ 中的闭包就是 $\overline{X}$.