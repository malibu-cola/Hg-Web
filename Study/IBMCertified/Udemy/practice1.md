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
- (不正解)$2X, H+X$, $\frac{1}{2}H$

## 23. 3量子ビットと2古典ビットを生成するコードはどれ

- (正解)qc = QuantumCircuit(3, 2)

## 24. 最大限のもつれ回路を生成するコードはどれ

- (正解)
```python
qc = QuantumCircuit(2)
qc.h(0)
qc.cx(0, 1)
```

## 25. 以下のコードを実行した時$\ket{0}$の測定確率はいくつか

```python
qc = QuatnumCircuit(1)
qc.rx(3*math.pi/4)
```

- (正解)0.1464
$$
\begin{aligned}
Rx(\theta) \ket{0} &= \begin{pmatrix}
\cos{\frac{\theta}{2}} & -i\sin{\frac{\theta}{2}}\\
-i\sin{\frac{\theta}{2}}&\cos{\frac{\theta}{2}} 
\end{pmatrix} 
\begin{pmatrix}
1\\0
\end{pmatrix}
\\
&=\cos{\frac{\theta}{2}}\ket{0} -i \sin{\frac{\theta}{2}}\ket{1}
\end{aligned}
$$
より、
$$
\begin{aligned}
Pr(\theta = \frac{3\pi}{4}, \ket{0}) = \cos^2{\frac{3\pi}{8}}
\end{aligned}
$$
半角の公式
$$
\begin{aligned}
\cos^2{\frac{\alpha}{2}} = \frac{1 + \cos{\alpha}}{2}
\end{aligned}
$$
であるから、
$$
\begin{aligned}
\cos^2{\frac{3\pi}{8}} &= \frac{1 + \cos{3\pi/4}}{2}\\
&= \frac{2 - \sqrt{2}}{4}\\
&\sim \frac{0.6}{4}\\
&\sim 0.15
\end{aligned}
$$

## 26. 次の状態ベクトルが与えられるコードはどれ

![q26](./pic/q26.png)

- (正解)

```python
from qiskit import QuantumCircuit, assemble, Aer
from math import pi, sqrt
from qiskit.visualization import plot_bloch_multivector, plot_histogram

sim = Aer.get_backnd('aer_sumulator')
qc = QuantumCircuit(2)
qc.h(0)
qc.cx(0, 1)
qc.x(0)
```

- $\ket{01}$と$\ket{10}$のもつれを作り出す

$$
\begin{aligned}
\ket{00}
&\xrightarrow{h(0)} \frac{1}{\sqrt{2}} (\ket{00} + \ket{01})\\
&\xrightarrow{cx(0, 1)} \frac{1}{\sqrt{2}}(\ket{00} + \ket{11})\\
&\xrightarrow{x(0)} \frac{1}{\sqrt{2}}(\ket{01} + \ket{10})
\end{aligned}
$$

## 27. トフォリゲートを含む量子回路はどれか

```python
qc = QuantumCircuit(3)
# enter code here
```

- (正解)暗記する。
  - `qc.mct([0, 2], 1)`
  - `qc.ccx(0, 1, 2)`
  - ```c2x = CXGate.control(); qc.append(c2x, [1, 2, 0])```

## 28. 以下の回路の深さはいくつか

```python
qc = QuantumCircuit(3, 3)
qc.x(0)
qc.h(1)
qc.cx(0, 1)
qc.h(2)
qc.cx(0, 2)
qc.draw()
```

- (正解)3

![q28](./pic/q28.png)

- `qc.depth()`で確かめられる

## 29. 以下の回路の深さはいくつか

![q29-1](./pic/q29-1.png)

- (正解)4

![q29-2](./pic/q29-2.png)

## 30. BasicAerで使用できないシミュレータはどれ

- (正解)quantum_simulator
- (不正解)BasicAerで使用できる。
  - qasm_simulator
  - statevector_simulator
  - unitary_simulator

## 31. BasicAerとはなにか

- (正解)
  - Pythonベースの量子シミュレーターモジュール。シミュレータはBasicAerプロバイダーからアクセスできる
- (不正解)
  - qiskitで利用できる量子コンピューティングランタイムの一種
  - IBMクラウドで利用できる量子コンピュータのシミュレーションフレームワークの一種
  - 量子回路を表現できるpythonのパッケージ

## 32. 以下の条件で実行すべきコードはどれか

【条件】QASMシミュレータを使用し、量子ビット上で[custom_coupling]を用いて、1024回回路を測定する。

- (正解)

```python
from qiskit import QuantumCircuit, execute, BasicAer

simulator = BasicAer.get_backend('qasm_simulator')

qc = QuantumCircuit(3)
qc.measure_all()

custom_coupling = [[0, 1], [1, 2], [2, 0]]

job  = execute(qc, simulator, coupling_map=custom_coupling)
result = job.result()
counts = result.get_counts(qc)
```

- executeの引数(qc, simulator, coupling_map = ***)が大事

## 33. Qiskitの実行の最適化をコントロールするパラメータはどれか

- (正解)`optimization_level`

## 34. 以下のコードのうち、与えられた設定で回路を実行できるのは

【設定】
- 1236回測定する
- Unitary SImulatorを使う
- custom couplingを使用せず、latexフォーマットで出力する。

- (正解)

```python
from qiskit import QuantumCircuit, execute, BasikAer

simulator = BasicAer.get_backend('unitary_simulator')
qc = QuantumCircuit(3)

job = execute(qc, simulator, shots=1236)

result = job.result().get_unitary()
result = array_to_latex(result)
result
```

- 答えが同じのがたくさんあるクソ問

## 35. 次のコードのうち、どの部分でエラーが発生するか

![q35](./pic/q35.png)

- (正解)エラーは発生しない


## 36. Aerで使用できるシミュレーターはどれ

- (正解)
  - pulse_simulator
  - qasm_simulator
  - statevector_simulator
  - unitary_simulator
- (不正解)
  - ibmq_simulator

## 37. 状態ベクトルシミュレータオブジェクトを使用する際にバックエンドに適切に取り込むのはどのコードか

- (正解)`backend = BasicAer.get_backend('statevector_simulator')`

## 38. `qasm_file`を量子回路`qc`に組み込むのにどのコードが適切か

- (正解)`qc = QuantumCircuit.from_qasm_file('qasm_file')`

- qasm stringから読み取る方法もある

```python
from qiskit import QuantumCircuit
circuit = QuantumCircuit.from_qasm_str("""
OPENQASM 2.0;
include "qelib1.inc";
qreg q[2];
cz q[0], q[1];
u(2*pi, 3*pi, -5*pi) q[0];
""")
circuit.draw('mpl')
```

## 39. Xゲートを表しているのはどれ

- (正解)

```python
qc = QuantumCircuit(1)
qc.x(0)
op = Operator(qc)
```