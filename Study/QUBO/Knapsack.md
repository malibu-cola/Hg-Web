# ナップザック問題

## 問題


所持金750円で、美味しい水、サイコソーダ、ミックスオレをかう時、回復量が最も多くなる組み合わせを求めよ。なお、重複購入OK

|飲み物|値段|回復量|
|-|-|-|
|美味しい水|200円|30回復|
|サイコソーダ|300円|50回復|
|ミックスオレ|350円|70回復|


### 750円ぴったりで買う場合。

#### 準備1

最大公約数でそれぞれの変数を割る。重みのバランスの設定が簡単になる。

所持金:15

|飲み物|値段|回復量|
|-|-|-|
|美味しい水|4|3|
|サイコソーダ|6|5|
|ミックスオレ|7|7|

#### 準備2

各飲み物の最大値を見積もり、量子ビットを準備する。
```
美味しい水:最大値3つ→q0, q1, q2
サイコソーダ:最大値2つ→q3, q4
ミックスオレ:最大値2つ→q5, q6
```

#### ソースコード

```python
from tytan import *

q = symbols_list(7)

H = 0
# 値段の制約条件(必ず15円にする)
H += (4*q[0] + 4*q[1] + 4*q[2] + 6*q[3] + 6*q[4] + 7*q[5] + 7*q[6] - 15) ** 2
# 回復量を弱い報酬とする
H += -0.01*(3*q[0] + 3*q[1] + 3*q[2] + 5*q[3] + 5*q[4] + 7*q[5] + 7*q[6])

qubo, offset = Compile(H).get_qubo()
print('offset', offset)
solver = sampler.SASampler()
result = solver.run(qubo)

for r in result:
  print(r)
```

#### 結果

```
offset 225.0
[{'q0': 0, 'q1': 1, 'q2': 1, 'q3': 0, 'q4': 0, 'q5': 0, 'q6': 1}, -225.13, 26]
[{'q0': 0, 'q1': 1, 'q2': 1, 'q3': 0, 'q4': 0, 'q5': 1, 'q6': 0}, -225.13, 7]
[{'q0': 1, 'q1': 0, 'q2': 1, 'q3': 0, 'q4': 0, 'q5': 0, 'q6': 1}, -225.13, 11]
[{'q0': 1, 'q1': 0, 'q2': 1, 'q3': 0, 'q4': 0, 'q5': 1, 'q6': 0}, -225.13, 4]
[{'q0': 1, 'q1': 1, 'q2': 0, 'q3': 0, 'q4': 0, 'q5': 0, 'q6': 1}, -225.13, 25]
[{'q0': 1, 'q1': 1, 'q2': 0, 'q3': 0, 'q4': 0, 'q5': 1, 'q6': 0}, -225.13, 11]
[{'q0': 0, 'q1': 0, 'q2': 1, 'q3': 1, 'q4': 1, 'q5': 0, 'q6': 0}, -224.13000000000002, 3]
[{'q0': 0, 'q1': 1, 'q2': 0, 'q3': 1, 'q4': 1, 'q5': 0, 'q6': 0}, -224.13000000000002, 10]
[{'q0': 1, 'q1': 0, 'q2': 0, 'q3': 1, 'q4': 1, 'q5': 0, 'q6': 0}, -224.13000000000002, 3]
```

#### 750円**以内**で買う場合

750→15となったので0..15の16通りの答えがあるが、補助量子ビットを16個も使用するのは非効率。減らせないかを考える。
合計金額が11円の時、美味しい水を買えば、必ず良い解になる。そのため考えるのは,12, 13, 14, 15の4通り

#### ソースコード

`symbols_list`を使う場合と`symbols()`を使う場合で結果が異なったため両方掲載。後者が正解。
```python
from tytan import *
import numpy as np

# 先と同様に量子ビットを準備
q = symbols_list(7)
# 補助量子ビットを準備(解が4通り)
s = symbols_list(4)

H = 0
H += (s[0] + s[1] + s[2] + s[3] - 1) ** 2
H += (4*q[0] + 4*q[1] + 4*q[2] + 6*q[3] + 6*q[4] + 7*q[5] + 7*q[6] - (12*s[0] + 13*s[1] + 14*s[2] + 15*s[3]))**2
H += -0.01*(3*q[0] + 3*q[1] + 3*q[2] + 5*q[3] + 5*q[4] + 7*q[5] + 7*q[6])

# 変数を降順に
H += (1 - q[0]) * q[1] + (1 - q[1]) * q[2]
H += (1 - q[3]) * q[4]
H += (1 - q[5]) * q[6]

qubo, offset = Compile(H).get_qubo()
print('offset', offset)
solver = sampler.SASampler()
result = solver.run(qubo)

for r in result:
  print(r)
```

```python 
from tytan import *
import numpy as np

#量子ビットを用意する
q0 = symbols('q0')
q1 = symbols('q1')
q2 = symbols('q2')
q3 = symbols('q3')
q4 = symbols('q4')
q5 = symbols('q5')
q6 = symbols('q6')

#補助ビットを用意する
s0 = symbols('s0')
s1 = symbols('s1')
s2 = symbols('s2')
s3 = symbols('s3')

#補助ビットをワンホットにする（強い条件）
#これにより (12*s0 + 13*s1 + 14*s2 + 15*s3) で 「12 or 13 or 14 or 15」 を表現できる
H = 0
H += (s0 + s1 + s2 + s3 - 1)**2

#7個のドリンクをそれぞれ取るか取らないか、値段を係数にして合計が「12 or 13 or 14 or 15」になる（強い条件）
H += (4*q0 + 4*q1 + 4*q2 + 6*q3 + 6*q4 + 7*q5 + 7*q6 - (12*s0 + 13*s1 + 14*s2 + 15*s3))**2

#7個のドリンクをそれぞれ取るか取らないか、回復量を係数にして報酬とする（弱い条件）
H += -0.01 * (3*q0 + 3*q1 + 3*q2 + 5*q3 + 5*q4 + 7*q5 + 7*q6)

#おいしいみずを降順にする
H += (1 - q0) * q1
H += (1 - q1) * q2
#サイコソーダを降順にする
H += (1 - q3) * q4
#ミックスオレを降順にする
H += (1 - q5) * q6


#コンパイル
qubo, offset = Compile(H).get_qubo()
print(f'offset\n{offset}')

#サンプラー選択
solver = sampler.SASampler()

#サンプリング
result = solver.run(qubo)

#結果
for r in result:
    print(r)
```

#### 結果

- 前者

```
offset 1.0
[{'q0': 1, 'q1': 0, 'q2': 0, 'q3': 0, 'q4': 0, 'q5': 1, 'q6': 0}, -0.10000000000000142, 51]
[{'q0': 0, 'q1': 0, 'q2': 1, 'q3': 1, 'q4': 1, 'q5': 1, 'q6': 1}, 1.7300000000000182, 49]
```
- 後者
```
offset
1.0
[{'q0': 0, 'q1': 0, 'q2': 0, 'q3': 0, 'q4': 0, 'q5': 0, 'q6': 0, 's0': 0, 's1': 0, 's2': 0, 's3': 1}, -1.0, 9]
[{'q0': 0, 'q1': 0, 'q2': 0, 'q3': 0, 'q4': 0, 'q5': 0, 'q6': 0, 's0': 0, 's1': 0, 's2': 1, 's3': 0}, -1.0, 22]
[{'q0': 0, 'q1': 0, 'q2': 0, 'q3': 0, 'q4': 0, 'q5': 0, 'q6': 0, 's0': 0, 's1': 1, 's2': 0, 's3': 0}, -1.0, 20]
[{'q0': 0, 'q1': 0, 'q2': 0, 'q3': 0, 'q4': 0, 'q5': 0, 'q6': 0, 's0': 1, 's1': 0, 's2': 0, 's3': 0}, -1.0, 20]
[{'q0': 0, 'q1': 0, 'q2': 1, 'q3': 1, 'q4': 1, 'q5': 1, 'q6': 1, 's0': 0, 's1': 0, 's2': 0, 's3': 1}, 0.7300000000000182, 2]
[{'q0': 0, 'q1': 0, 'q2': 1, 'q3': 1, 'q4': 1, 'q5': 1, 'q6': 1, 's0': 0, 's1': 0, 's2': 1, 's3': 0}, 0.7300000000000182, 6]
[{'q0': 0, 'q1': 0, 'q2': 1, 'q3': 1, 'q4': 1, 'q5': 1, 'q6': 1, 's0': 0, 's1': 1, 's2': 0, 's3': 0}, 0.7300000000000182, 5]
[{'q0': 0, 'q1': 0, 'q2': 1, 'q3': 1, 'q4': 1, 'q5': 1, 'q6': 1, 's0': 1, 's1': 0, 's2': 0, 's3': 0}, 0.7300000000000182, 16]
```