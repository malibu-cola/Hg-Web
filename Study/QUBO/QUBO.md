---
layout: default
---

# QUBO

[tytan_tutoria](https://github.com/tytansdk/tytan_tutorial?tab=readme-ov-file)のおすすめコースを勉強し、量子エンジニア(アニーリング式)認定試験を解けるようになることが目標。
量子アニーリングマシンについては[こちら](../QuantumAnnealing/QuantumAnnealing.md)

## 設定

最初にtytansdkをインストールする必要がある。

```python
!pip install git+https://github.com/tytansdk/tytan
```

## 各アルゴリズム

### お勧めコース

- [最大カット問題](./MaxCut.md)
- [温度計パズル](./ThermoPazzle.md)
- [数字を均等に２組に分ける](./DivideNum.md)
- [シフト最適化](./ShiftOptimize.md)
- [お絵かきロジック](./DrawLogic.md)
- [巡回セールスマン問題](./TravelSales.md)
- [クラスタリング](./Clustering.md)
- [連立方程式を解く](./SimulEquation.md)
- [線形回帰](./LSM.md)
- [ナップザック問題](./Knapsack.md)

### チュートリアル

- [00_NetworkXを利用したグラフ問題](./tutorial/tutorial00_networkx.md)
- [01_Simulated Annealing手順](./tutorial/tutorial01_qubo.md)
- [02_MaxCut問題と整数分割問題](./tutorial/tutorial02_maxcut.md)
- [03_二値整数計画問題](./tutorial/tutorial03_bil.md)
- [04_グラフ分割問題とグラフカラーリング問題](./tutorial/tutorial04_graphcoloring.md)
- [05_クリーク判定問題とクリークカバー問題、厳密被覆問題](./tutorial/tutorial05_cliques.md)
- [06_ジョブシーケンス問題](./tutorial/tutorial06_job_sequencing_problem.md)
- []


## まとめ

- n個の量子ビットからm個を1にする

```python
# 例:3個の量子ビットから2個を1にする
H += (q0 + q1 + q2 -2) ** 2
```

- 2個の量子ビットを降順にする。

```python
# 例: q0 ≧ q1 にする（[0, 0]、[1, 1]、[1, 0]はセーフ。[0, 1] になったときだけペナルティを与える）
H += (1 - q0) * q1
```

- 全ての量子ビットを降順にする。

```python
# 例: q0 ≧ q1 ≧ q2 にする（2個の降順を連鎖させる）
H += (1 - q0) * q1 + (1 - q1) * q2
```

- 解が0と1だけの方程式

```python
# 例:重さ1, 2, 3のボールのどれを取れば合計3の重さになるか。
H += (1*q0 + 2*q2 + 3*q3 - 3)**2
```

- 2個の量子ビットが同時に1になったら報酬・ペナルティ


```python
# 2個の量子ビットが同時に1になったら報酬0.1
H += -0.1 * (q0 * q1)

# 2個の量子ビットが同時に1になったらペナルティ0.1
H += +0.1 * (q0 * q1)
```

- One-Hotエンコーディング

```python
# バニラ、チョコ、ストロベリーのどれかにする
# →1~3の数字のどれかにする
# →３個の量子ビットから1個を1にする
# →1になった場所で解釈する
H += (q0 + q1 + q2 - 1) ** 2
``` 

- Nbit表現

```python
# xが0~3の整数であることを前提に「2x = 4」の方程式を解く
x = 2*x0 + 1*x1

H += (2*x - 4)**2

# xを0~255の整数で表す
x = 128*x0 + 64*x1 + 32*x2 + 16*x3 + 8*x4 + 4*x5 + 2*x6 + 1*x7
```

|問題|n個からm個|降順|方程式|同時に1|One-Hot|N-bit|
|--|--|--|--|--|--|--|
|最大カット問題|O||||||
|温度計パズル|O|O|||||
|数字分割|||O|||||
|シフト最適化|||O|||||w
|お絵かきロジック|O|||O|||
|巡回セールスマン||||O|O||
|クラスタリング||||O|O||
|連立方程式|||O|||O|
|線形回帰|||||O||
|ナップザック問題|||||||

## その他

- [QUBOの条件式](https://vigne-cla.com/21-12/)
- [Blueqat club basic認定試験に向けての各種ポイント](https://blueqat.com/yuichiro_minato2/6bc363dd-373e-4354-aad3-a04985e314f2)
- [Blueqat club standard認定試験に向けての各種ポイント](https://blueqat.com/yuichiro_minato2/0fec35c5-efaa-465a-89a8-fa91ce09458f)
- [Blueqat club qubomaster認定試験に向けての各種ポイント](https://blueqat.com/yuichiro_minato2/c31102b3-27fb-4a56-a949-476a2d7bab60)