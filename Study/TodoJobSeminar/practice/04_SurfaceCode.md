# 表面符号

このノートブックでは、5量子ビットの表面符号を用いて、誤りの検出が可能なことを確認します。
ただし、ここで見せるサンプルでは誤りの検出のみで、誤りの訂正はできません。

## 1. ライブラリのインポート

```python
%pip install qiskit==0.45.2 qiskit-aer==0.12.0
%pip install pylatexenc
```

```python
import numpy as np
from qiskit import QuantumCircuit
from qiskit_aer import AerSimulator
from qiskit.visualization import plot_histogram
from qiskit_aer.noise import pauli_error
```

## 2. 表面符号

ここでは、５量子ビットに状態を符号化して、観測用の量子ビットを４つ用意し、誤りが発生しているかどうかを確認します。
どれか１つの観測用ビットが反転していれば、誤りが発生していることがわかります。

![04_01](./pic/04_01.png)

```python
def surface_code(bit_error_channel: list[int] = [], phase_error_channel: list[int] = []) -> QuantumCircuit:
    # bit_error_channel : ビット反転エラーを起こす量子ビット
    # phase_error_channel : 位相反転エラーを起こす量子ビット

    n_qubits = 5 + 4
    circ = QuantumCircuit(n_qubits, 4)

    # 符号化
    circ.h(7)
    circ.cx(7, 0)
    circ.cx(7, 1)
    circ.cx(7, 4)
    circ.cx(4, 7)


    circ.h(8)
    circ.cx(8, 2)
    circ.cx(8, 3)
    circ.cx(8, 4)
    circ.cx(3, 8)

    circ.barrier()

    # エラーが発生する部分
    for i in bit_error_channel:
        circ.x(i)

    for i in phase_error_channel:
        circ.z(i)

    circ.barrier()

    # エラー検知箇所
    # Z0 Z2 Z4
    circ.cx(0, 5)
    circ.cx(2, 5)
    circ.cx(4, 5)

    # Z1 Z3 Z4
    circ.cx(1, 6)
    circ.cx(3, 6)
    circ.cx(4, 6)

    # X0 X1 X4
    circ.h(7)
    circ.cx(7, 0)
    circ.cx(7, 1)
    circ.cx(7, 4)
    circ.h(7)

    # X2 X3 X4
    circ.h(8)
    circ.cx(8, 2)
    circ.cx(8, 3)
    circ.cx(8, 4)
    circ.h(8)

    circ.barrier()

    circ.measure([5, 6, 7, 8], [0, 1, 2, 3])

    return circ
```

```python
circ = surface_code()
circ.draw("mpl")
```

![04_02](./pic/04_02.png)

```python
backend_sim = AerSimulator()
n_shots = 10000

result = backend_sim.run(circ, shots=n_shots).result()
plot_histogram(result.get_counts(0))
```

![04_03](./pic/04_03.png)


全ての量子ビットが0になっている。

## 2. エラー検出

次に、この回路にノイズを乗せてみる。
ビット反転エラー、位相反転エラーによって、観測ビットの値が変わることを確認します。

```python
circ = surface_code(bit_error_channel=[1])
result = backend_sim.run(circ, shots=n_shots).result()
plot_histogram(result.get_counts(0))
```

![04_04](./pic/04_04.png)

この方法では、以下のように違う量子ビットにノイズを乗せても、同じ結果になってい舞うことがあるので、エラー箇所の特定はできません。

```python
circ = surface_code(bit_error_channel=[3])
result = backend_sim.run(circ, shots=n_shots).result()
plot_histogram(result.get_counts(0))
```

![04_05](./pic/04_05.png)

```python
circ = surface_code(phase_error_channel=[0])
result = backend_sim.run(circ, shots=n_shots).result()
plot_histogram(result.get_counts(0))
```

![04_06](./pic/04_06.png)

また２量子ビットのエラーでは検出できないことがある。

```python
circ = surface_code(bit_error_channel=[0, 2])
result = backend_sim.run(circ, shots=n_shots).result()
plot_histogram(result.get_counts(0))
```

![04_07](./pic/04_07.png)

0000となり、正常な状態と区別ができず、エラーを検出できない。
２量子ビット以上でエラーが発生する全ての場合で検出できないわけではない。

```python
circ = surface_code(bit_error_channel=[0, 1])
result = backend_sim.run(circ, shots=n_shots).result()
plot_histogram(result.get_counts(0))
```

![04_08](./pic/04_08.png)