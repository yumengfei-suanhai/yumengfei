# 严格对角占优矩阵的 Gauss-Seidel 迭代收敛性证明

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

是**严格对角占优矩阵**，即满足

$$
|a_{ii}|>\sum_{j\neq i}|a_{ij}|,\qquad i=1,2,\dots,n.
$$

则对于线性方程组 $Ax=b$，Gauss-Seidel 迭代法收敛。

---

## 证明

### 一、迭代格式

将系数矩阵分解为

$$
A=L+D+U,
$$

其中 $D$ 为对角矩阵，$L$、$U$ 分别为严格下三角和严格上三角矩阵。于是

$$
Ax=b\implies (L+D+U)x=b\implies (L+D)x=-Ux+b,
$$

从而得到 Gauss-Seidel 迭代格式

$$
x^{(k+1)}=-(L+D)^{-1}Ux^{(k)}+(L+D)^{-1}b.
$$

记迭代矩阵为

$$
G=-(L+D)^{-1}U,
$$

则收敛性等价于谱半径 $\rho(G)<1$。

---

### 二、特征值估计

设 $\lambda$ 为 $G$ 的任一特征值，$v=(x_1,x_2,\dots,x_n)^T$ 为对应的特征向量。取

$$
\|v\|_\infty=1,
$$

即存在指标 $i$，使得

$$
|x_i|=1,\qquad |x_j|\le 1\quad (j\neq i).
$$

由 $Gv=\lambda v$ 得

$$
-(L+D)^{-1}Uv=\lambda v,
$$

等价于

$$
Uv=-\lambda(L+D)v.
$$

考察上式第 $i$ 个分量：

$$
\sum_{j>i} a_{ij}x_j=-\lambda\left(a_{ii}x_i+\sum_{j<i}a_{ij}x_j\right).
$$

取模得

$$
\left|\sum_{j>i} a_{ij}x_j\right|
=|\lambda|\left|a_{ii}x_i+\sum_{j<i}a_{ij}x_j\right|. \tag{1}
$$

#### 左侧估计

由三角不等式及 $|x_j|\le 1$，有

$$
\left|\sum_{j>i} a_{ij}x_j\right|
\le \sum_{j>i}|a_{ij}||x_j|
\le \sum_{j>i}|a_{ij}|
= \sum_{j\neq i}|a_{ij}|-\sum_{j<i}|a_{ij}|.
$$

利用严格对角占优条件 $\sum_{j\neq i}|a_{ij}|<|a_{ii}|$，得

$$
\left|\sum_{j>i} a_{ij}x_j\right|
< |a_{ii}|-\sum_{j<i}|a_{ij}|. \tag{2}
$$

#### 右侧估计

由反向三角不等式，

$$
\left|a_{ii}x_i+\sum_{j<i}a_{ij}x_j\right|
\ge |a_{ii}||x_i|-\left|\sum_{j<i}a_{ij}x_j\right|.
$$

又 $|x_i|=1$，且 $|x_j|\le 1$，所以

$$
\left|\sum_{j<i}a_{ij}x_j\right|
\le \sum_{j<i}|a_{ij}||x_j|
\le \sum_{j<i}|a_{ij}|.
$$

因此

$$
\left|a_{ii}x_i+\sum_{j<i}a_{ij}x_j\right|
\ge |a_{ii}|-\sum_{j<i}|a_{ij}| >0.
$$

于是由 (1) 式可得

$$
|\lambda|\left(|a_{ii}|-\sum_{j<i}|a_{ij}|\right)
\le |\lambda|\left|a_{ii}x_i+\sum_{j<i}a_{ij}x_j\right|
= \left|\sum_{j>i}a_{ij}x_j\right|. \tag{3}
$$

#### 综合 (2) 与 (3)

由 (2)(3) 得

$$
|\lambda|\left(|a_{ii}|-\sum_{j<i}|a_{ij}|\right)
< |a_{ii}|-\sum_{j<i}|a_{ij}|.
$$

由于严格对角占优保证

$$
|a_{ii}|-\sum_{j<i}|a_{ij}| > 0,
$$

两边同除该正数，得

$$
|\lambda|<1.
$$

---

### 三、结论

因为 $\lambda$ 是 $G$ 的任意特征值，故所有特征值的模均小于 $1$，从而谱半径

$$
\rho(G)<1.
$$

因此，**严格对角占优矩阵的 Gauss-Seidel 迭代法必收敛**。