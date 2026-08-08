# 实对称正定矩阵的 Gauss-Seidel 迭代收敛性证明

## 定理

设

$$
A=\begin{pmatrix}
a_{11}&a_{12}&\cdots&a_{1n}\\
a_{21}&a_{22}&\cdots&a_{2n}\\
\vdots&\vdots&&\vdots\\
a_{n1}&a_{n2}&\cdots&a_{nn}
\end{pmatrix}
$$

为**实对称正定矩阵**。则对于线性方程组 $Ax=b$，Gauss-Seidel 迭代法收敛。

---

## 一、Gauss-Seidel 迭代公式与迭代矩阵

对于线性方程组 $Ax=b$，将系数矩阵分解为

$$
A = L + D + U,
$$

其中 $D$ 为对角矩阵，$L$、$U$ 分别为严格下三角和严格上三角矩阵。

于是

$$
Ax=b \;\Longrightarrow\; (L+D+U)x=b
\;\Longrightarrow\; (L+D)x=-Ux+b
\;\Longrightarrow\; x=-(L+D)^{-1}Ux+(L+D)^{-1}b.
$$

由此得到 **Gauss-Seidel 迭代公式**：

$$
x^{(k+1)}=-(L+D)^{-1}Ux^{(k)}+(L+D)^{-1}b. \tag{1}
$$

其中迭代矩阵为

$$
G=-(L+D)^{-1}U,
$$

常数项为 $c=(L+D)^{-1}b$。

---

## 二、收敛性证明

设 $\lambda$ 为 $G$ 的任一特征值，$v\neq 0$ 为对应的特征向量。

在正式推证之前，先给出几个由 $A$ 的实对称正定性所保证的基本性质。

- 因 $A$ 正定，故对任意 $v\neq 0$，有 $v^HAv>0$，即

$$
v^HDv+v^HLv+v^HUv>0.
$$

- 因 $A$ 正定，其顺序主子式均大于零，特别地对角元 $a_{ii}>0$，故对角矩阵 $D$ 正定，从而对任意 $v\neq 0$，有

$$
v^HDv>0.
$$

- 因 $A$ 为实对称矩阵，故 $U=L^T$。对于复向量 $v$ 与实矩阵 $L$（满足 $\bar{L}=L$），有

$$
v^HUv = v^HL^Tv = (v^HL^Tv)^T = v^TL\bar{v} = v^T\bar{L}\bar{v} = \overline{v^HLv}.
$$

记

$$
\alpha = v^HDv > 0, \qquad \beta = v^HLv,
$$

则上述性质可简洁地表示为

$$
v^HUv = \bar{\beta}, \qquad v^HAv = \alpha+\beta+\bar{\beta} > 0. \tag{2}
$$

---

现在开始正式的推证。

由 $Gv=\lambda v$，得

$$
-(L+D)^{-1}Uv=\lambda v,
$$

等价于

$$
-Uv=\lambda(L+D)v. \tag{3}
$$

在 (3) 式两边左乘 $v^H$，得

$$
-v^HUv=\lambda v^H(L+D)v=\lambda\left(v^HLv+v^HDv\right).
$$

利用记号 $\alpha$、$\beta$ 以及 $v^HUv=\bar{\beta}$，上式化为

$$
-\bar{\beta}=\lambda(\alpha+\beta). \tag{4}
$$

对 (4) 式两边取模并平方，得

$$
|\beta|^2=|\lambda|^2|\alpha+\beta|^2. \tag{5}
$$

另一方面，由 (2) 式中的 $v^HAv=\alpha+\beta+\bar{\beta}>0$，可得

$$
|\alpha+\beta|^2 = (\alpha+\beta)(\bar{\alpha}+\bar{\beta}).
$$

由于 $\alpha$ 为正实数，$\bar{\alpha}=\alpha$，故

$$
|\alpha+\beta|^2 = (\alpha+\beta)(\alpha+\bar{\beta})
= \alpha(\alpha+\beta+\bar{\beta}) + \beta\bar{\beta}.
$$

而 $\alpha>0$ 且 $\alpha+\beta+\bar{\beta}>0$，因此

$$
\alpha(\alpha+\beta+\bar{\beta}) > 0,
$$

从而

$$
|\alpha+\beta|^2 > \beta\bar{\beta} = |\beta|^2. \tag{6}
$$

**说明 $\alpha+\beta\neq 0$：** 若 $\alpha+\beta=0$，则 $\beta=-\alpha$，于是

$$
\alpha+\beta+\bar{\beta} = 0 + \overline{-\alpha} = -\alpha < 0,
$$

这与 $\alpha+\beta+\bar{\beta}>0$ 矛盾。因此 $\alpha+\beta\neq 0$，故 $|\alpha+\beta|^2>0$。

结合 (5) 与 (6)，得

$$
|\lambda|^2|\alpha+\beta|^2 = |\beta|^2 < |\alpha+\beta|^2.
$$

两边同除 $|\alpha+\beta|^2$，得

$$
|\lambda|^2 < 1,
$$

故

$$
|\lambda| < 1.
$$

---

## 三、结论

因为 $\lambda$ 是 $G$ 的任意特征值，故所有特征值的模均小于 $1$，从而谱半径

$$
\rho(G) < 1.
$$

因此，**实对称正定矩阵的 Gauss-Seidel 迭代法必收敛**。