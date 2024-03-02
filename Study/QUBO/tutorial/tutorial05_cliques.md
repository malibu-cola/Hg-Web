# クリーク問題とクリークカバー問題

## 【クリーク判定問題】

- クリークとは頂点同士が全て繋がっている頂点群のこと
- クリーク問題はグラフ$G = (V, E)$の部分集合$W \in V$において、大きさ$|W| = K$ のあらゆる2点を繋ぐ$\frac{K(K - 1)}{2}$個の辺があるかどうかを判定する。

### 例

```python 
import networkx as nx
import matplotlib.pyplot as plt
import numpy as np

options = {'node_color': '#efefef', 'node_size': 1200, 'with_labels': 'True'}

n = 7 # 頂点数
K = 4 # 探すクリーク数（グラフGの部分集合Wのサイズのこと）

G = nx.Graph()
G.add_nodes_from(nx.path_graph(n))
G.add_edges_from([(0, 1), (0, 2), (0, 3), (0, 4), (1, 2), (1, 3), (2, 3), (4, 6), (4, 5), (5, 6)])

nx.draw(G, **options)
```
![tutorial05_1](./pic/tutorial05_1.png)