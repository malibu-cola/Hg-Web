# Practice2

## 1. 制御量子ビットに関係なくpな事項かを表す制御ゲートはどれか

- (正解)CZ

$$
\begin{aligned}
    CZ(0, 1) = CZ(1, 0) = 
    \begin{pmatrix}
    1&0&0&0\\
    0&1&0&0\\
    0&0&1&0\\
    0&0&0&-1\\
    \end{pmatrix}
\end{aligned}
$$

## 2. involutaryなゲートはどれ

- (正解)X, Y, Zゲート
- (不正解)CX, CY, 

involutaryの時
$$
\begin{aligned}
    A^2 &= I\\
    A^{-1} &= A
\end{aligned}
$$
である。パウリゲートはこれを満たす。

## 3. エルミートでないゲートはどれ

- (正解)RX, RY
- 回転ゲートRX, Ry, Rzは常にエルミートではない

## 4. $\frac{1}{\sqrt{2}}(\ket{0} + i\ket{1})$を作る回路はどれか

- (正解)
![q04](./pic2/q04.png)

$$
\begin{aligned}
P(\theta) = \begin{pmatrix}
1&0\\0&e^{i\theta}
\end{pmatrix}
\end{aligned}
$$
より
$$
\begin{aligned}
P(\pi/2) = \begin{pmatrix}
1&0\\0&e^{i\pi/2}
\end{pmatrix}
=\begin{pmatrix}
1&0\\0&i
\end{pmatrix}
\end{aligned}
$$
$$
\begin{aligned}
\ket{0} 
&\xrightarrow{H} \frac{1}{\sqrt{2}}(\ket{0} + \ket{1})\\
&\xrightarrow{P(\pi/2)} \frac{1}{\sqrt{2}}\begin{pmatrix}
1&0\\0&i
\end{pmatrix}
\begin{pmatrix}
1\\1
\end{pmatrix}\\
&= \frac{1}{\sqrt{2}}\begin{pmatrix}
1\\i
\end{pmatrix}\\
&=\frac{1}{\sqrt{2}}(\ket{0} + i\ket{1})
\end{aligned}
$$