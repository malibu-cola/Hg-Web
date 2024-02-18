# 数字を均等に２つに分ける

## 問題

6つの自然数$(15, 25, 33, 41, 64, 82)$を総和が等しくなるように2組に分ける。

## ソースコード

```python
from tytan import *
import numpy as np

v = [15, 25, 33, 41, 64, 82]
q = symbols_list(6)

H = 0
H += (sum(q * v) - sum(v)//2) ** 2

qubo, offset = Compile(H).get_qubo()
solver = sampler.SASampler()
result = solver.run(qubo)

for r in result[:3]:
  print(r)
  print(sum(np.array(list(r[0].values()) * np.array(v))))
```

## 結果

```
[{'q0': 0, 'q1': 1, 'q2': 0, 'q3': 1, 'q4': 1, 'q5': 0}, -16900.0, 27]
130
[{'q0': 1, 'q1': 0, 'q2': 1, 'q3': 0, 'q4': 0, 'q5': 1}, -16900.0, 27]
130
[{'q0': 0, 'q1': 0, 'q2': 0, 'q3': 1, 'q4': 0, 'q5': 1}, -16851.0, 23]
123
```
上二つが最適解。0と１が入れ替わっているだけなので実質、解は一つ。
