# MaxCut問題と自然数分割問題

## MaxCut問題

一筆書きで切ることができる最大の変の数を求める問題。
辺の両側の点が異なっていれば切れるというルール。

## QUBO式

量子ビット$s_i$が+1と-1のスピンを取る時、QUBO式(イジング式)は
$$
C = \sum_{i, j} s_i s_j
$$
となる。$s_i, s_j$が+1, -1と別の値を取るときにコストが小さくなる。

量子ビット$q_i$が0, 1と書かれる場合は$s_i = 2q_i - 1$として相互に変換できる。
変換後のコスト関数は
$$
C = \sum_{i, j} (- q_i - q_j + 2*q_i *q_j)
$$
となる。


```python 
!pip install --quiet networkx matplotlib
```

```python 
import networkx as nx
import matplotlib.pyplot as plt

options = {'node_size': 1000, 'with_labels': 'True', 'node_color': '#efefef'}

G = nx.Graph()
G.add_nodes_from([0, 1, 2, 3, 4])
G.add_edges_from([(0, 1), (0, 3), (1, 2), (2, 3), (2, 4), (3, 4)])

nx.draw(G, **options)
```

