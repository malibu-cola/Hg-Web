# 二値整数計画問題

連立方程式を満たした上で、ある計算を最小化するという、制約付きの最小値問題。
$Sx = b$を満たすベクトル$x$のうち、$cx$を採用にする$x$を探す問題。

## QUBO

この問題は２つの式から成り立つ。
- $H_A$:連立方程式の制約を満たすため

$$
H_A = \sum_{j = 1}^m [b_j - \sum_{i = 1}^N S_{ji}x_i]^2
$$

- $H_B$: 最小コストを求めるため。

$$
H_B = - \sum_{i=1}^N c_i x_i
$$

これらを重みありで繋ぎ合わせると

$$
H = H_A + \lambda H_B = \sum_{j = 1}^m [b_j - \sum_{i = 1}^N S_{ji}x_i]^2- \lambda \times \sum_{i=1}^N c_i x_i
$$

## 例題

連立方程式

$$
\begin{pmatrix}
3 & 2 & 1\\
5 & 2 & 3
\end{pmatrix}
\begin{pmatrix}
x_0 \\ x_1 \\ x_2
\end{pmatrix}
 = 
\begin{pmatrix}
3 \\ 5
\end{pmatrix}
$$

を満たす$\boldsymbol{x}$のうち

$$
\begin{pmatrix}
1 & 2 & 1
\end{pmatrix}
 \begin{pmatrix}
 x_0 \\ x_1 \\ x_2
 \end{pmatrix}
$$

を最小にする$\boldsymbol{x}$を求める。

制約条件を満たすときQUBO式は$0$になる。

## 1. 