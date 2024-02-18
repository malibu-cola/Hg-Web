[Top](https://malibu-cola.github.io/Hg-Web/)

# QUBO

[tytan_tutoria](https://github.com/tytansdk/tytan_tutorial?tab=readme-ov-file)のおすすめコースを勉強し、量子エンジニア(アニーリング式)認定試験を解けるようになることが目標。
## 設定

最初にtytansdkをインストールする必要がある。

```python
!pip install git+https://github.com/tytansdk/tytan
```

## 各アルゴリズム

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


## まとめ

- n個の量子ビットからm個を1にする
  - 最大カット問題
  - 温度計パズル
  - お絵かきロジック

```python
# 例:3個の量子ビットから2個を1にする
H += (q0 + q1 + q2 -2) ** 2
```

- 2個の量子ビットを降順にする。
  - 温度計パズル

```python
# 例: q0 ≧ q1 にする（[0, 0]、[1, 1]、[1, 0]はセーフ。[0, 1] になったときだけペナルティを与える）
H += (1 - q0) * q1
```

- 全ての量子ビットを降順にする。
  - 温度計パズル

```python
# 例: q0 ≧ q1 ≧ q2 にする（2個の降順を連鎖させる）
H += (1 - q0) * q1 + (1 - q1) * q2
```

- 解が0と1だけの方程式
  - 数字を均等に2組に分ける
  - シフト最適化

```python
# 例:重さ1, 2, 3のボールのどれを取れば合計3の重さになるか。
H += (1*q0 + 2*q2 + 3*q3 - 3)**2
```

- 2個の量子ビットが同時に1になったら報酬
  - お絵描きロジック

```python
# 2この量子ビットが同時に1になったら報酬0.1
H += -0.1 * (q0 * q1)

# 2個の量子ビットが同時に1になったらペナルティ0.1
H += +0.1 * (q0 * q1)
```

- One-Hotエンコーディング
  - バニラ、チョコ、





## その他

[QUBOの条件式](https://vigne-cla.com/21-12/)