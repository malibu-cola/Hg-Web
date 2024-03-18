# Practice1

## Q1. 古典NOTゲートに当たる量子ゲートは以下のうちどれ。

- (正解)Xゲート
- (不正解)Z, Y, H, Sゲート

## Q2. Sゲートを２回行うのと等しいゲートはどれ

- (正解)Tゲート
- (不正解)S-dagger, Z, Y, Rx($\pi$/4)
- $$ S = P_{\pi/2} = \begin{pmatrix}1&0\\0&i\end{pmatrix}$$
- $$ T = P_{\pi/4} = \begin{pmatrix} 1&0\\0&\frac{1+i}{\sqrt{2}}\end{pmatrix} $$

![q02_1](./pic/q02_1.png)![q02_2](./pic/q02_2.png)![q02_3](./pic/q02_3.png)![q02_4](./pic/q02_4.png)

## Q3. 測定に用いる軸周りに状態ベクトルを回転しないゲートを以下から２つ選べ。

- (正解)Xゲート, Yゲート
- (不正解)Z, T, Sゲート
- XとYゲートはx軸、y軸周りに反時計回りで$\pi$rad回転させる。Z, S, TゲートはZ軸周りに回転する。

## Q4. 次のゲートのうち非自発的(involutary)なゲートはどれ。

- (正解)X, Y, Z, Iゲート
- (不正解)S, Tゲート
- 以下の性質を満たす時ゲートはinvolutary(非自発的?)という。$$A^2 = I$$
- $S^2 = Z, T^2 = S$なのでこれは満たさない。

## Q5. 常にエルミートなゲートはどれ

- (正解)X, Y, Z, H, Iゲート
- (不正解)Rx, Ry, Rz, 
- ゲートがエルミート(共役転置)の時、$$A^* = A$$を満たす

## Q6. 正しくないものを２つ選べ

- (正解)$SS = T, ZZ = T$
- (不正解)$XX = I, IX = XI, TT = S$

## Q7. 関係性が正しいものを２つ選べ

- (正解)
  - Inverse of X is X
  - P($\pi$) = Z
  - TTTT = Z(T^5にタイポしている)
  - $\sqrt{Z}$ = S
- (不正解)
  - None of the above

## Q8. Xが等しいのは

- (正解)HZH
- (不正解)TZT, YHY, ZYZ

## Q9. PゲートがZと等しくなる引数$\phi$の値は？

- $$P(\phi) = \begin{pmatrix} 1&0\\0&e^{i\phi} \end{pmatrix}$$
- (正解)$\phi = \pi$

## 10. Hに等しいのは

- (正解)$Z \sqrt{X}$
- $$\begin{aligned}H &= XY^{1/2}\\H &= Y^{-1/2}X\\H &= ZY^{-1/2}\\H &= Y^{1/2}Z\end{aligned}$$

## 11. HHに等しいのは

- (正解)I
- (不正解)H, X, Y, Z

## 12. 次のゲートのうち、ユニバーサルなのは

- (正解)All of the above
  - Rotational gate+H
  - CX, H and P
  - U gate
- ゲートのユニバーサルセットは
  1. 回転ゲート(Rx, Ry, Rz)とH
  2. CX, HとP
  3. Uゲート
- これらのユニバーサルゲートの組みはブロッホ級表面の任意の点に移動できる状態ベクトルであるため'ユニバーサル'と呼ばれる。

## 13. 次の回路で得られる状態はどれか。

![q13](./pic/q13.png)

- (正解)$\frac{1}{\sqrt{2}}(\ket{00} + \ket{11})$

## 14. 以下のゲートが表しているのは

![q14](./pic/q14.png)

- (正解)CX gate with q0 as control qubit and q1 as target bit

## 15. Yゲートの演算子は

- (正解)$Y = \begin{pmatrix}0&-i\\i&0\end{pmatrix}$

## 16. Zゲートの演算子は

- (正解)$\begin{pmatrix}1&0\\0&-1\end{pmatrix}$

## 17. Xゲートの固有状態のベクトルは

- (正解)$\ket{+}$と$\ket{-}$

## 18. Xゲートの固有値は

- (正解)$+1$と$-1$

## 19. 次の量子回路の測定後の状態ベクトルとその確率はどれか

![q19](./pic/q19.png)

- (正解)$\ket{11}; 100\%$

## 20. 次の回路と等しいのは

![q20](./pic/q20.png)

- (正解)$I$

## 21. $U(\theta, \phi, \lambda)$とHゲートが等しくなるのは

- (正解)$U(\pi/2,  0, 0)$
- $$U(\theta, \phi, \lambda) = \begin{pmatrix}\cos{\frac{\theta}{2}}&-e^{i\lambda}\sin{\frac{\theta}{2}}\\e^{i\phi\sin{\frac{\theta}{2}}}&e^{i(\phi+\lambda)}\cos{\frac{\theta}{2}}\end{pmatrix}$$
- $$U(\pi/2,0, 0) = \frac{1}{\sqrt{2}}\begin{pmatrix}1&1\\1&-1\end{pmatrix}$$

## 22. 以下のうちユニタリーなのは

- (正解)H
- (不正解)2X, H+X, $\frac{1}{2}H$