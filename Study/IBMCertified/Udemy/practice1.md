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