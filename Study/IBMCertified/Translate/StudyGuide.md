# Study Guideの和訳

## Qiskit 開発者認定試験の準備

ここでは、Qiskit 開発者の受験準備に役立つヒントとリソースをいくつか紹介します。
試験には、Qiskit を使用した量子コンピューティングに関する質問が含まれており、以下の分野での能力を確保します。

- Qiskit SDK を使用した量子回路の定義、実行、結果の視覚化
- 単一量子ビット ゲートとブロック球上でのその回転を理解する。
- 量子回路におけるさまざまなマルチ量子ビットゲートとその効果を理解する。
- qiskit.circuit、qiskit.execute、qiskit.providers、qiskit.qasm、qiskit.quantum_info、qiskit.tools、および qiskit.visualization パッケージにある一般的に使用されるクラスと関数を含む、基本的な Qiskit SDK 機能を活用します。

理想的には、試験を受ける前に次のスキルを身につけておく必要があります。

- [IBM Quantum Composer](https://quantum-computing.ibm.com/composer) を使用して、量子回路の結果を作成、実行、視覚化するための実用的な知識
- [IBM Quantum Lab](https://quantum-computing.ibm.com/lab) にあるものなど、Qiskit SDK の機能を強調するサンプルの開発に関する実用的な知識
- 複雑なベクトルと行列を使用した量子状態と進化のモデリングに関する実践的な知識。
- パウリ行列に関する実用的な知識。
- 量子状態測定確率に関する実用的な知識。
- ベル状態を引き起こす一般的な回路に精通していること。

受験準備におすすめのルートはこちら

1. [「Qiskit を使用した量子計算の学習」教科書](https://qiskit.org/textbook)を、「多重量子ビットともつれ」セクションまで学習する
2. 次に、IBM Quantum Lab の以下の領域をカバーするいくつかのチュートリアルを進めると役立ちます。
   1. [量子回路](https://quantum-computing.ibm.com/lab/files/qiskit-tutorials/tutorials/circuits)
   2. [量子シミュレータ](https://quantum-computing.ibm.com/lab/files/qiskit-tutorials/tutorials/simulators)
3. 次に、量子ゲート、測定、リセットの組み合わせである量子回路についてもう少し詳しく見てみましょう。 最初に、以下のトピックを必ずカバーしてください。 回路を理解するには、これらの Web サイトを参照してください。
   1. [defining-quqntum-circuits](https://qiskit.org/textbook/ch-algorithms/defining-quantum-circuits.html)
   2. [representing-qubit-states](https://qiskit.org/textbook/ch-states/representing-qubit-states.html)
   3. [Gate](https://qiskit.org/documentation/stubs/qiskit.circuit.Gate.html)
   4. [Visualize](https://qiskit.org/documentation/tutorials/circuits_advanced/03_advanced_circuit_visualization.html)
      1. [さまざまな単一量子ビットゲートを使用する](https://qiskit.org/textbook/ch-states/single-qubit-gates.html)
      2. [さまざまなマルチ量子ビットゲートを使用する](https://qiskit.org/textbook/ch-gates/multiple-qubits-entangled-states.html)
      3. [バリア操作を使用する](https://qiskit.org/documentation/stubs/qiskit.circuit.library.Barrier.html)
      4. [回路の深さを返す](https://arnaldogunzi.medium.com/how-to-calculate-the-depth-of-a-quantum-circuit-in-qiskit-868505abc104)
      5. [量子回路の拡張](https://qiskit.org/documentation/stubs/qiskit.extensions.Initialize.html)
      6. [qiskit バージョンに関する操作](https://qiskit.org/documentation/install.html)
      7. [演算子](https://qiskit.org/documentation/tutorials/circuits_advanced/02_operators_overview.html)
      8. [fidelity(忠実度)](https://qiskit.org/documentation/stubs/qiskit.quantum_info.state_fidelity.html)
   5. 次に研究するトピックは[量子レジスタ](https://qiskit.org/documentation/getting_started.html)です。 これらのリソースにアクセスすると、この分野についてさらに詳しく知ることができます。
      1. [量子回路の構築](https://qiskit.org/textbook/ch-algorithms/defining-quantum-circuits.html)
      2. [マルチ量子ビットレジスタの構築](https://qiskit.org/textbook/ch-gates/multiple-qubits-entangled-states.html)
      3. [量子回路を古典レジスタに測定する](https://qiskit.org/documentation/stubs/qiskit.circuit.Measure.html)
      4. [古典、量子レジスタ](https://qiskit.org/documentation/stubs/qiskit.circuit.QuantumRegister.html)
      5. [量子回路の実行](https://qiskit.org/documentation/apidoc/execute.html)
   6. 次に考慮すべきトピックは[シミュレーター](https://qiskit.org/documentation/tutorials/simulators/1_aer_provider.html)です。 シミュレータは、実際の量子デバイスを模倣するために使用されます。 これらのトピックを参照するためのリンクを以下に示します。
         1. 実験のヒストグラム データを返す
         2. 実験の状態ベクトルを返す
         3. 実験のユニタリーを返す
         4. 利用可能なシミュレータ
         5. statevector_simulator バックエンドへのアクセス
         6. qasm_simulator バックエンドへのアクセス
         7. unitary_simulator バックエンドへのアクセス
   7. [Open QASM](https://github.com/Qiskit/openqasm) は Open Quantum Assembly Language であり、量子命令の中間言語です([参考](https://medium.com/qiskit/a-new-openqasm-for-a-new-era-of-dynamic-circuits-87f031cac49))。 以下は、Open QASM とそれを使用する方法を理解するためのリソースです。
      1. 回線の OpenQASM 文字列を返す
      2. QASM ファイルの読み取り
   8. Qiskit Backend（[参考](https://medium.com/qiskit/qiskit-backends-what-they-are-and-how-to-work-with-them-fb66b3bd0463)） は、IBM Quantum Experience デバイスで使用される機能を指します。 Qiskit バックエンドがどのように機能するかを理解するには、以下のリソースを参照してください。
      1. ジョブインスタンスのステータスを監視する
      2. Qiskit バックエンドの概要
   9. [視覚化](https://qiskit.org/documentation/tutorials/circuits/2_plotting_data_in_qiskit.html)では、Qiskit でさまざまなデータをプロットします。 これらの概念を理解するためのリソースを以下に示します。
       1. 回路を描く データのヒストグラムをプロットする
       2. ブロッホマルチベクトルのプロット
       3. ブロッホベクトルのプロット
       4. QSphere のプロット
       5. 密度行列のプロット
       6. ゲートマップとエラー率のプロット