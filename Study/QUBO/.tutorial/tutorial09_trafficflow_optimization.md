# 交通経路最適化問題

渋滞緩和のために、経路を選択し、最適化する。

```python
import networkx as nx
import matplotlib.pyplot as plt

G = nx.Graph()
G.add_nodes_from([i for i in range(9)])
G.add_edges_from([(0, 1), (0, 3), (1, 2), (1, 4), (2, 5), (3, 4), (3, 6), (4, 5), (4, 7), (5, 8), (6, 7), (7, 8)])
options = {'node_size': 1200, 'with_labels': 'True'}
pos = nx.spring_layout(G)
nx.draw(G, pos, **options, node_color='#efefef')

edge_labels = {(0, 1):'s0', (0, 3):'s2', (1, 2):'s1', (1, 4):'s3', \
                           (2, 5):'s4', (3, 4):'s5', (3, 6):'s7', (4, 5):'s6', \
                           (4, 7):'s8', (5, 8):'s9', (6, 7):'s10', (7, 8):'s11'}

nx.draw_networkx_edge_labels(G, pos, edge_labels=edge_labels)
plt.show()
```
![tutorial09_01](./pic/tutorial09_01.png)

