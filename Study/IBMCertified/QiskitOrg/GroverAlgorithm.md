# グローバーのアルゴリズム

[こちら](https://learning.quantum.ibm.com/tutorial/grovers-algorithm)のページの和訳をしています。

## 背景

- 振幅増幅は汎用の量子アルゴリズム、またはサブルーチンである。
- 古典的なアルゴリズムよりも 2次の高速化を実現する。 
- [Grover のアルゴリズム](https://arxiv.org/abs/quant-ph/9605043)は、非構造化検索の問題における高速化を初めて実証した。 
- グローバー探索問題を定式化するには、オラクル関数と増幅回路が必要。
- ここでは、Grover オラクルを構築し、Qiskit 回路ライブラリの`GroverOperator`を使用して Grover の検索インスタンスを簡単にセットアップする方法を示します。 
- ランタイム `Sampler` プリミティブにより、自動コンパイル、エラー抑制、読み出しエラー軽減技術などの Grover 回路のシームレスな実行が可能になります。


## セットアップ

```python
import math
import warnings
warnings.filterwarnings('ignore')

from qiskit import QuantumCircuit
from qiskit.ircuit.library import GroverOperator, MCMT, ZGate
from qiskit.visualization import plot_distribution
```