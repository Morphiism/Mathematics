本章我们来给出无编号循环构造的可容许性证明，以及它的生成函数。首先我们需要一个概念：

**定义 B.1** 原始序列（primitive sequence）

一个有限序列 $\sigma=\sigma_{1}\dots\sigma_{n}$ 是**原始的**或**非周期的**，如果不存在 $\tau=\tau_{1}\dots \tau_{m}(m<n)$ 使得 $\sigma=\tau^{k}=\underbrace{ \tau\dots \tau }_{ k }$.

例如，序列 $abbaa$ 是原始的，而 $abab=(ab)^{2}$ 则不是。

设 $\mathcal{B}$ 是一个组合类，$\mathcal{S}=\mathrm{Seq}_{\geq 1}(\mathcal{B})$ 是其序列构成的类，$\mathcal{PS}\subset \mathcal{S}$ 是由原始序列构成的类，则它们的生成函数有以下关联：

$$
\begin{gather}
S(z,u)=\dfrac{uB(z)}{1-uB(z)}=\sum_{k\geq 1} PS(z^{k},u^{k})
\end{gather}
$$

这是因为每个序列或者是原始的，或者是某个原始序列的 $k$ 次方，于是 Mobius 反演就给出

$$
\begin{gather}
PS(z,u)=\sum_{k\geq 1}\mu(k) S(z^{k},u^{k})=\sum_{k=1}^{\infty} \mu(k) \dfrac{u^{k}B(z^{k})}{1-u^{k}B(z^{k})}
\end{gather}
$$

为建立它与循环的联系，我们给出下面的定义：

**定义 B.2** 原始循环（primitive cycle）

一个循环是**原始的**，如果它的任意线性表示都是原始序列。

每个长度为 $\ell$ 的原始循环都对应了 $\ell$ 个原始序列，因此原始循环构成的类 $\mathcal{PC}$ 的生成函数 $PC(z,u)$ 就是将 $PS(z,u)$ 中的 $u^{\ell}$ 换成 $\dfrac{1}{\ell}u^{\ell}$ 得到的，即

$$
\begin{gather}
PC(z,u)=\int_{0}^{u} PS(z,v) \dfrac{\mathrm{d} v}{v}=\sum_{k=1}^{\infty} \dfrac{\mu(k)}{k}\ln \dfrac{1}{1-u^{k}B(z^{k})}
\end{gather}
$$

又因为每个循环或者是原始循环，或者是原始循环的 $k$ 次方，故对于循环类 $\mathcal{C}=\mathrm{Cyc}(\mathcal{B})$ 有

$$
\begin{gather}
C(z,u)=\sum_{k\geq 1} PC(z^{k},u^{k})=\sum_{k=1}^{\infty} \left( \sum_{d\ \mid\ k} \dfrac{\mu(d)}{d} \right) \ln \dfrac{1}{1-u^{k}B(z^{k})}
\end{gather}
$$

**引理 B.3**

设整数 $k\geq 1$，则 $\sum_{d\ \mid\ k}\mu(d) / d=\varphi(k) / k$.

**证明**

我们首先验证 $k=p^{m}$ 的情况，其中 $p$ 是素数，则有

$$
\begin{gather}
\sum_{d\ \mid\ k} \dfrac{\mu(d)}{d}=\dfrac{\mu(1)}{1}+\dfrac{\mu(p)}{p}+\dots +\dfrac{\mu(p^{m})}{p^{m}}=1-\dfrac{1}{p}=\dfrac{\varphi(p^{m})}{p^{m}}
\end{gather}
$$

下面我们来通过函数的积性将结论推广至一般的 $k$. 根据附录 A 中的结论，函数 $\varphi$ 是积性的，而如果 $k_{1},k_{2}$ 互素，则整除 $k_{1}k_{2}$ 的因子 $d$ 可以分解为 $d=d_{1}d_{2}$，其中 $d_{1}\mid k_{1},d_{2}\mid k_{2}$，又由于 $\mu$ 也是积性的（这可以直接从它的定义中看出），故有

$$
\begin{gather}
\sum_{d\ \mid\ k} \dfrac{\mu(d)}{d}=\sum_{d_{1}\mid k_{1},d_{2}\mid k_{2}} \dfrac{\mu(d_{1})\mu(d_{2})}{d_{1}d_{2}}=\left( \sum_{d_{1}\ \mid\ k_{1}} \dfrac{\mu(d_{1})}{d_{1}} \right)\left( \sum_{d_{2}\ \mid\ k_{2}} \dfrac{\mu(d_{2})}{d_{2}} \right)
\end{gather}
$$

从而左边的函数 $f(k)=\sum_{d\ \mid\ k}\mu(d) / d$ 是积性的，这就完成了证明。

因此，带有成分限制的无编号循环构造的生成函数由以下表达式给出：

$$
\begin{gather}
C(z,u)=\sum_{k=1}^{\infty} \dfrac{\varphi(k)}{k} \ln \dfrac{1}{1-u^{k}B(z^{k})}
\end{gather}
$$

令 $u=1$ 就得到了无限制的循环构造的生成函数

$$
\begin{gather}
C(z)=\sum_{k=1}^{\infty} \dfrac{\varphi(k)}{k} \ln \dfrac{1}{1-B(z^{k})}
\end{gather}
$$

在多元生成函数章节中，循环构造也是以同样的方法进行处理的。