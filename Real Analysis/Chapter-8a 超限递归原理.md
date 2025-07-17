首先我们证明两个引理：

**引理 1** 唯一性引理

设 $\varphi$ 是一个类函数，$f,g$ 分别是定义在序数 $\delta,\gamma$ 上的函数，$\delta\leq\gamma$，如果对任意 $\alpha<\delta$ 有 $f(\alpha)=\varphi(f|_{\alpha}),g(\alpha)=\varphi(g|_{\alpha})$，则 $f=g|_{\delta}$，即对任意 $\alpha<\delta$ 有 $f(\alpha)=g(\alpha)$.

**证明**

在良序集 $\delta$ 上使用超限归纳法。当 $\alpha=0$ 时，有

$$
f(0)=\varphi(f|_{0})=\varphi(0)=\varphi(g|_{0})=g(0)
$$

假设对任意 $\beta<\alpha$ 有 $f(\beta)=g(\beta)$，则 $f|_{\alpha}=g|_{\alpha}$，于是

$$
f(\alpha)=\varphi(f|_{\alpha})=\varphi(g|_{\alpha})=g(\alpha)
$$

这就完成了证明。

**引理 2** 序数上的递归原理

设 $\varphi$ 是一个类函数，则唯一存在序数 $\delta$ 上的函数 $\psi_{\delta}$ 使得对任意 $\alpha<\delta$ 有

$$
\psi_{\delta}(\alpha)=\varphi(\psi_{\delta}|_{\alpha})
$$

**证明**

唯一性由引理 1 即得。下面来证存在性，我们将使用 $\mathbf{On}$ 上的超限归纳法。

当 $\delta=0$ 时，可取 $\psi_{0}=0$.

假设对所有 $\gamma<\delta$ 存在函数 $\psi_{\gamma}$ 满足对任意 $\alpha<\gamma$ 有

$$
\psi_{\gamma}(\alpha)=\varphi(\psi_{\gamma}|_{\alpha})
$$

如果 $\delta$ 是后继序数，设 $\delta=\gamma'$，则利用已有的函数 $\psi_{\gamma}$ 定义 $\psi_{\delta}$ 如下：

$$
\psi_{\delta}(\alpha)=\varphi(\psi_{\gamma}|_{\alpha}), \alpha<\delta
$$

下证 $\psi_{\gamma}|_{\alpha}=\psi_{\delta}|_{\alpha}$，由于 $\delta=\gamma'$，故当 $\beta<\alpha<\delta$ 时总有 $\beta<\gamma<\delta$，因此

$$
\psi_{\gamma}(\beta)=\varphi(\psi_{\gamma}|_{\beta})=\psi_{\delta}(\beta)
$$

这就是所要证的。

如果 $\delta$ 是极限序数，对任意 $\alpha<\delta$ 有 $\alpha'<\delta$，利用已有的 $\psi_{\alpha'}$ 定义

$$
\psi_{\delta}(\alpha)=\psi_{\alpha'}(\alpha)
$$

当 $\beta<\alpha$ 时，我们有 $\beta'<\alpha'$，从而

$$
\psi_{\delta}(\beta)=\psi_{\beta'}(\beta)=\psi_{\alpha'}(\beta)
$$

后一个等式利用了引理 1，于是我们有 $\psi_{\delta}|_{\alpha}=\psi_{\alpha'}|_{\alpha}$，从而

$$
\psi_{\delta}(\alpha)=\psi_{\alpha'}(\alpha)=\varphi(\psi_{\alpha'}|_{\alpha})=\varphi(\psi_{\delta}|_{\alpha})
$$

这就完成了证明。

下面我们给出超限归纳原理的证明。

**定理 8.2.17** 超限归纳原理

设 $\varphi$ 是一个类函数，则存在唯一的类函数 $\psi$ 满足对任意序数 $\alpha$ 有

$$
\psi(\alpha)=\varphi(\psi|_{\alpha})
$$

**证明**

$\psi$ 的唯一性根据 $\mathbf{On}$ 上的超限归纳法易证。下证存在性。

根据引理 2，对任意序数 $\alpha$，存在唯一的函数 $\psi_{\alpha'}$ 满足

$$
\psi_{\alpha'}(\beta)=\varphi(\psi_{\alpha'}|_{\beta}),\beta<\alpha'
$$

定义序数函数 $\psi$ 如下：

$$
\psi(\alpha)=\psi_{\alpha'}(\alpha)
$$

此时有

$$
\psi(\alpha)=\varphi(\psi_{\alpha'}|_{\alpha})=\varphi(\psi|_{\alpha})
$$

后一个等式成立是因为对于 $\beta<\alpha$ 有

$$
\psi(\beta)=\psi_{\beta'}(\beta)=\psi_{\alpha'}(\beta)
$$

这就完成了证明。