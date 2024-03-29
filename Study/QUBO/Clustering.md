# クラスタリング

## 問題

10個の点を３クラスに分類する。点の座標は以下。

```
x = [0.45, 0.80, 0.71, 0.49, 0.79, 0.30, 0.44, 0.14, 0.30, 0.40]
y = [0.14, 0.14, 0.17, 0.25, 0.32, 0.63, 0.68, 0.74, 0.77, 0.84]
```
![Cludtering1](./pic/Clustering1.png)

## ソースコード

```python
from tytan import *
import numpy as np
import matplotlib.pyplot as plt

x = np.array([0.45, 0.80, 0.71, 0.49, 0.79, 0.30, 0.44, 0.14, 0.30, 0.40])
y = np.array([0.14, 0.14, 0.17, 0.25, 0.32, 0.63, 0.68, 0.74, 0.77, 0.84])

# q[i][j] = 点iがクラスjに分類される時1、そうでない時0
q = symbols_list([10, 3])

H = 0
# 分類されるクラスは1つだけ
for i in range(0, 10):
  H += (q[i][0] + q[i][1] + q[i][2] - 1) ** 2

# ２つの点の見て、その距離がペナルティになる。
for i1 in range(0, 10):
  for i2 in range(0, 10):
    dist = ((x[i1] - x[i2]) ** 2 + (y[i1] - y[i2]) ** 2) ** 0.5

    # 同じクラスに入ったら、距離がペナルティ。
    H += 0.1 * dist * (q[i1][0] * q[i2][0])
    H += 0.1 * dist * (q[i1][1] * q[i2][1])
    H += 0.1 * dist * (q[i1][2] * q[i2][2])

qubo, offset = Compile(H).get_qubo()
print('offset', offset)
solver = sampler.SASampler()
result = solver.run(qubo)

for r in result[:3]:
  print(r)

  tmp = np.array(list(r[0].values())).reshape(10, 3)
  ans = np.argmax(tmp, axis = 1)
  print(ans)

  plt.figure(figsize=(3, 3))
  plt.plot(x[ans==0], y[ans==0], 'o', label='0')
  plt.plot(x[ans==1], y[ans==1], 'o', label='1')
  plt.plot(x[ans==2], y[ans==2], 'o', label='2')
  plt.xlabel('x')
  plt.ylabel('y')
  plt.legend()
  plt.show()
```

## 結果

```
offset 10.0
[{'q0_0': 0, 'q0_1': 1, 'q0_2': 0, 'q1_0': 0, 'q1_1': 0, 'q1_2': 1, 'q2_0': 0, 'q2_1': 0, 'q2_2': 1, 'q3_0': 0, 'q3_1': 1, 'q3_2': 0, 'q4_0': 0, 'q4_1': 0, 'q4_2': 1, 'q5_0': 1, 'q5_1': 0, 'q5_2': 0, 'q6_0': 1, 'q6_1': 0, 'q6_2': 0, 'q7_0': 1, 'q7_1': 0, 'q7_2': 0, 'q8_0': 1, 'q8_1': 0, 'q8_2': 0, 'q9_0': 1, 'q9_1': 0, 'q9_2': 0}, -9.504333476237282, 1]
[1 2 2 1 2 0 0 0 0 0]

[{'q0_0': 0, 'q0_1': 1, 'q0_2': 0, 'q1_0': 1, 'q1_1': 0, 'q1_2': 0, 'q2_0': 1, 'q2_1': 0, 'q2_2': 0, 'q3_0': 0, 'q3_1': 1, 'q3_2': 0, 'q4_0': 1, 'q4_1': 0, 'q4_2': 0, 'q5_0': 0, 'q5_1': 0, 'q5_2': 1, 'q6_0': 0, 'q6_1': 0, 'q6_2': 1, 'q7_0': 0, 'q7_1': 0, 'q7_2': 1, 'q8_0': 0, 'q8_1': 0, 'q8_2': 1, 'q9_0': 0, 'q9_1': 0, 'q9_2': 1}, -9.504333476237282, 1]
[1 0 0 1 0 2 2 2 2 2]

[{'q0_0': 0, 'q0_1': 0, 'q0_2': 1, 'q1_0': 0, 'q1_1': 1, 'q1_2': 0, 'q2_0': 0, 'q2_1': 1, 'q2_2': 0, 'q3_0': 0, 'q3_1': 0, 'q3_2': 1, 'q4_0': 0, 'q4_1': 1, 'q4_2': 0, 'q5_0': 1, 'q5_1': 0, 'q5_2': 0, 'q6_0': 1, 'q6_1': 0, 'q6_2': 0, 'q7_0': 1, 'q7_1': 0, 'q7_2': 0, 'q8_0': 1, 'q8_1': 0, 'q8_2': 0, 'q9_0': 1, 'q9_1': 0, 'q9_2': 0}, -9.504333476237282, 2]
[2 1 1 2 1 0 0 0 0 0]
```

![Clustering2](./pic/Clustering2.png)
上位３つが最適解で、クラスを入れ替えたものだったので、画像は１枚のみ掲載。
