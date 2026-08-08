# 严格对角占优矩阵的 Jacobi 迭代收敛性证明

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

为**严格对角占优矩阵**，即满足

$$
|a_{ii}| > \sum_{j \neq i} |a_{ij}|, \qquad i = 1, 2, \dots, n.
$$

则对于线性方程组 $Ax=b$，Jacobi 迭代法收敛。

---

## 一、Jacobi 迭代公式与迭代矩阵

对于线性方程组 $Ax=b$，将系数矩阵分解为

$$
A = L + D + U,
$$

其中 $D$ 为对角矩阵，$L$ 和 $U$ 分别为严格下三角和严格上三角矩阵。

于是

$$
Ax=b \;\Longrightarrow\; (L+D+U)x=b
\;\Longrightarrow\; Dx=-(L+U)x+b
\;\Longrightarrow\; x=-D^{-1}(L+U)x+D^{-1}b.
$$

由此得到 **Jacobi 迭代公式**：

$$
x^{(k+1)} = -D^{-1}(L+U)x^{(k)} + D^{-1}b. \tag{1}
$$

其中

$$
T_J = -D^{-1}(L+U)
$$

称为 **Jacobi 迭代矩阵**，常数项为 $c = D^{-1}b$。

---

由于 $A$ 严格对角占优，故 $a_{ii} \neq 0$，从而对角矩阵 $D$ 可逆，且

$$
D^{-1} = \begin{pmatrix}
\dfrac{1}{a_{11}} & 0 & \cdots & 0 \\[6pt]
0 & \dfrac{1}{a_{22}} & \cdots & 0 \\[6pt]
\vdots & \vdots & & \vdots \\[6pt]
0 & 0 & \cdots & \dfrac{1}{a_{nn}}
\end{pmatrix}.
$$

因此迭代矩阵可具体表示为

$$
T_J = -D^{-1}(L+U)
= -\begin{pmatrix}
\dfrac{1}{a_{11}} & 0 & \cdots & 0 \\[6pt]
0 & \dfrac{1}{a_{22}} & \cdots & 0 \\[6pt]
\vdots & \vdots & & \vdots \\[6pt]
0 & 0 & \cdots & \dfrac{1}{a_{nn}}
\end{pmatrix}
\begin{pmatrix}
0 & a_{12} & \cdots & a_{1n} \\
a_{21} & 0 & \cdots & a_{2n} \\
\vdots & \vdots & & \vdots \\
a_{n1} & a_{n2} & \cdots & 0
\end{pmatrix},
$$

即

$$
T_J = \begin{pmatrix}
0 & -\dfrac{a_{12}}{a_{11}} & \cdots & -\dfrac{a_{1n}}{a_{11}} \\[8pt]
-\dfrac{a_{21}}{a_{22}} & 0 & \cdots & -\dfrac{a_{2n}}{a_{22}} \\[8pt]
\vdots & \vdots & & \vdots \\[8pt]
-\dfrac{a_{n1}}{a_{nn}} & -\dfrac{a_{n2}}{a_{nn}} & \cdots & 0
\end{pmatrix}. \tag{2}
$$

---

## 二、收敛性证明

下面给出两种证明方法，均表明 $\rho(T_J) < 1$，从而 Jacobi 迭代收敛。

### 方法一：利用无穷范数估计谱半径

计算迭代矩阵 $T_J$ 的无穷范数：

$$
\|T_J\|_\infty
= \max_{1 \le i \le n} \sum_{j=1}^{n} |(T_J)_{ij}|
= \max_{1 \le i \le n} \sum_{j \neq i} \left| -\frac{a_{ij}}{a_{ii}} \right|
= \max_{1 \le i \le n} \frac{1}{|a_{ii}|} \sum_{j \neq i} |a_{ij}|.
$$

由严格对角占优条件，对每个 $i$ 都有

$$
\frac{1}{|a_{ii}|} \sum_{j \neq i} |a_{ij}| < 1,
$$

故

$$
\|T_J\|_\infty < 1.
$$

又因为谱半径不超过任意矩阵范数，即

$$
\rho(T_J) \le \|T_J\|_\infty < 1,
$$

所以 Jacobi 迭代收敛。

---

### 方法二：利用盖尔圆盘定理估计谱半径

**盖尔圆盘定理（Gershgorin Circle Theorem）**：  
设 $C = (c_{ij})$ 为 $n \times n$ 复矩阵。对每一行 $i$，定义盖尔圆盘

$$
D_i = \left\{ z \in \mathbb{C} : |z - c_{ii}| \le R_i \right\}, \qquad R_i = \sum_{j \neq i} |c_{ij}|.
$$

则矩阵 $C$ 的所有特征值均位于 $\bigcup_{i=1}^{n} D_i$ 中。

---

现考察迭代矩阵 $T_J$，其形式如 (2) 所示。对第 $i$ 行，主对角元为 $0$，圆盘半径为

$$
R_i = \sum_{j \neq i} \left| -\frac{a_{ij}}{a_{ii}} \right|
= \frac{1}{|a_{ii}|} \sum_{j \neq i} |a_{ij}|
< \frac{1}{|a_{ii}|} \cdot |a_{ii}|
= 1.
$$

故每个盖尔圆盘

$$
D_i = \left\{ z \in \mathbb{C} : |z| < 1 \right\}
$$

均位于单位圆内部。于是所有盖尔圆盘的并集 $\bigcup_{i=1}^{n} D_i$ 也位于单位圆内。

由盖尔圆盘定理，$T_J$ 的所有特征值均位于单位圆内，因此

$$
\rho(T_J) < 1.
$$

故 Jacobi 迭代收敛。

---

## 三、结论

综上，对于严格对角占优矩阵 $A$，其 Jacobi 迭代矩阵的谱半径满足 $\rho(T_J) < 1$，因而 **Jacobi 迭代一定收敛**。