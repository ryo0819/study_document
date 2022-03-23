# Cloud Dataproc

# 概要

- `Map Reduce`をベースとしたGCP上で手軽にHadoopやSparkのクラスターを立ち上げ、データの解析を行うフルマネージドサービス

# 詳細

- クラスターを作成するとGCE上にワーカーノードが作成されるため、サーバーレスなサービスでは無い

- <span style="color: red; ">Apache Spark</span>アプリケーションを実行することができる

- また、サポートしているジョブは
  - Pig
  - Hive
  - Spark SQL
  - Spark
  - <span style="color: red; ">MapReduce</span>
  - PySpark

- ORCファイル形式を扱うことで、HDFS(Hadoop File System)の更新機能を使うことができる

- Spark Broadcastを使用すると、ビッグデータと小さなデータを効率的に結合することができる

- <span style="color: red; ">Dataprocクラスタはジョブごとに固有になるようにすると良い</span>(ジョブにつきクラスタ1個)

- HDFSやSSD/HDDを使用するとクラスタの寿命とともにデータが消失してしまう
  - 対策としては<span style="color: red; ">GCSを使用する</span>

- セカンダリワーカーはデータを保存せず、処理ノードとして機能する

- Bigqueryを入力及び出力ソースとするにはクラスターに<span style="color: red; ">Bigqueryコネクター</span>をインストールする

- **--no-address**フラグを使用するとパブリックIPがノードに割り当てられない
  - サブネットが特定のGCPサービスを利用するにはサブネットでプライベートGoogleアクセスを有効にする

- ワークフローテンプレート(API): ジョブを実行する場所に関する情報を含むジョブのグラフ

- pigジョブ: ディスクを大量に消費するオペレーション
  - 対策としては、インメモリ処理アーキテクチャの<span style="color: red; ">Spark</span>に移行する(GCPでは無い)
  - <span style="color: red; ">クラウド移行のスピードを重視する場合はDataproc(GCP)を選択する</span>(既存のオンプレHadoopジョブがあるとか)

- I/Oを多用するジョブは<span style="color: red; ">ディスクサイズを増やす</span>、計算能力が低い時は<span style="color: blue; ">CPUを増やす</span>

## パフォーマンス向上手段

- ディスクをHDDから<span style="color: red; ">SSD</span>に切り替える

- CSV形式よりも<span style="color: red; ">parquet形式</span>のデータを使用する(ファイル形式に注意)

- プリエンプティブノードを使用いている場合は、ディスクサイズを大きくして使用する

## コスト節約

- プリエンプティブノードを使用する
  - 停止する可能性があるノードなので、クリティカルでない要件で使用を検討する
  - プリエンプティブワーカーの数をクラスタ内の総ワーカー数の50%にすると最適な結果が得られる

- 永続データをクラスタ外に保存して、データ処理をしてない時はシャットダウン