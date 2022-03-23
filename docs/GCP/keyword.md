# 概要

- GCP勉強に遭遇したキーワードたちをまとめたページ

## 詳細

- `行`や`列`ときたらSQLの概念なので、Cloud SQLやCloud SpannerなどのSQLデータベース

- `エンティティと種類`: Cloud Datastore

- `リアルタイム取り込み`、 `処理`、 `分析`の組み合わせは`Pub/Sub + Dataflow + BigQuery`

- 過学習(オーバーフィッティング)への対策は、`データ拡張を行い既存のデータセットより多く生成する`、 `L2正則化`、 `ドロップアウト`、 `ネットワークサイズ縮小(特徴を小さくする)`

  - +α
    - L1正則化: 特徴選択に使用する
    - L2正則化: 過学習を防ぐ

- 学習不足(アンダーフィッティング)への対策は、`レイヤーの追加`、`語彙やn-gramのサイズを大きくする(モデルを複雑にする)`
  - ニューロン
  - 隠しレイヤー

- 機械学習モデルの種類

  - SVM(サポートベクターマシン)

  - ナイーブベイズ
    - とあるデータがどのカテゴリーに属するか判定

  - 再帰型ニューラルネットワーク(RNN)
    - 過去のデータから新しい事象を処理する
    - 関連
      - バイアス
      - ウエイト

  - 畳み込みニューラルネットワーク(CNN), YOLO(You Only Look Once)
    - 画像認識や動画認識

  - 多層パーセプトロン(MLP)
    - データを入力すると別のデータが出力される関数の1種

  - ロジスティック回帰(線形分類, 二値分類に対する分類モデル)
    - 二値分類を予測する

  - 決定木
    - 目的変数と説明変数より、サービス購入の見込みがある人の予測などを行う

- `次元数を減らす`にはPCA(主成分分析)という手法を使用する。
  - 新しい特徴量を抽出する(非可逆)
  - <u style="color: red;">数値データのみに機能する</u>
  - 以下の場合に検討する
    - 50%を超える欠損値を持つ特徴を削除
    - 2つの共依存関数がある時は1つを削除

- <u style="color: red;">指数バックオフ</u>: リクエスト間の遅延を増加させながら、失敗したリクエストを定期的に再試行するエラー処理
  - エラーが解消されていないのに連続でアクセスすることで処理が集中してしまい、逆にサービス復旧に時間がかからないようにするため

- <u style="color: red;">OLAP(Online Analytical Processing)</u>: DB上に蓄積された大量データに対し、素早く分析を行い抽出するBIツール

- <u style="color: blue;">OLTP(Online Transaction Processing)</u>: 大量に発生する小さいサイズのデータ処理に秀でている

- メタデータをカタログ化するには、`Data Catalog`(データ検出、メタデータ管理サービス)
  - フルマネージド
  - BigQueryやPub/Sub, Cloud Storageとの関連(サポートあり)

- `説明可能性が高い`とは機械学習のモデルが何故そのように判断したかを説明できるかどうか

- セキュリティ要件はIAM・Audit Log、サービスごとのセキュリティ

- `マルチクラウド戦略`に向いているサービスはCloud Composer, Anthos

- `Spark SQL`: SQLまたはPython構文で、分散処理と分析を実行できる大規模データ向けのサービス

- `Dataprep`: GCPコンソールから<u style="color: red;">ノーコード</u>でETLを行えるツール
  - インポートデータの指定、フローの作成、レシピの作成を行いDataflowのジョブ実行より加工済みデータを指定先に出力する
  
  - ノーコードということは非技術者でも扱うことができるツールである

- 分類問題の評価指標:
  - `精度`
  - `検出率`
  - `混同行列`
    - 混同行列の各値によって全ての評価指標を算出することができる
  - `正答率`

- 回帰問題の評価指標:
  - `MSE(Mean Square Error)`: 平均二乗誤差、値が小さいほど誤差の少ないモデル
  - `RMSE(Root Mean Square Error)`: 二乗平均平方根誤差、値が小さいほど誤差が少ないモデル
  - `MAE(Mean Absolute Error)`: 平均絶対誤差、値が小さいほど予測精度が高い

- Tensorflowの出力層の活性化関数は`Softmax(複数出力が合計「1.0」になるようにする)`

- Tensorflowのトレーニング時間の向上はAI PlatformでGPU・TPUを使用する

- `転移学習`: 学習が完了したモデルに新たな学習を追加して対応する、<u style="color: red;">計算量を少なくすることができる</u>

- データ損失への対策は`より多くのデータを収集する`、`新たな特徴を作成`、`モデルを複雑にする`

- 機械学習モデルのトレーニング
  - ローカルで行う場合
    - 迅速に調整ができる、コストが節約ができる

  - クラウドで行う場合
    - 拡張トレーニングを行う場合に有効

- `活性化関数`: 総入力を入力として、出力が切り替わる関数
  - パーセプトロン: ステップ関数
  - ニューラルネットワーク: シグモイド、ReLU

- `損失関数`: 活性化関数の結果を利用して出た結果を元に重みを増減させる関数

- データ処理の種類
  - 上から順に大規模なデータ処理が必要かつ処理時間が多い
    - `ETL`: Extract → Transform → Load
    - `ELT`: Extract → Load → Transform
    - `EL`: Extract → Load

- `Avro`: コンパクトなデータ形式で読み込みが速い、「シリアル化されたデータ」

- Googleのベストプラクティスとしてはでいるだけ`マネージドサービス`を選ぶようにする

- `A/Bテスト`: Aパターン・Bパターンを作成して、成果を比較してより高い効果を得る

- Hadoop/Sparkの移行の選択肢
  - すでにHadoop/Sparkの資産がある場合は`Dataproc`
  - 資産がない場合は`Dataflow`

- トランザクションを考慮した分析
  - 行う場合: `Cloud SQL`
  - 行わない場合: `BigQuery`

- HA(High Availability, 高可用性)構成は`クラスター`とも呼ばれ、プライマリゾーンとセカンダリゾーンにインスタンスを配置する
  - プライマリインスタンスが落ちた時に、スタンバイインスタンスが新しいプライマリインスタンスになる(=`フェイルオーバー`)
  - +α: リードレプリカは高可用性を目的とした構成ではない(参照専用のDBを増やし、負荷分散を目的)

- プリミティブロール(基本の役割)
  - PJ内の全リソースに対する権限の設定
    - Viewer: リソースの表示◯、変更×
    - Editor: リソースの変更◯、変更○
    - Owner:  リソースの変更◯、変更○、リソースに対する役割・権限◯、課金の設定◯

- GPUを使うタイミング
    - ソースが存在しない
    - 変更が煩雑なモデル
    - TPUで利用できないTensorflow演算を使用するモデル
    - バッチサイズが中〜大規模なモデル

- TPUを使うタイミング
    - 行列演算が多いモデル
    - トレーニングに数週間・数ヶ月かかるモデル
    - メインのトレーニンググループ内にカスタムTensorflow演算がない
    - バッチサイズが非常に大規模

- 集約されたログシンクを使用すると各PJに対して単一のシンクを作成できる = 1つのPJに権限を上げるだけで対象ログが全て見える
    - エクスポート先
        - GCS
        - pub/sub
        - BigQuery
        - Cloud loggingバケット
    - また、ログをエクスポートすることにより以下が可能になる
        - <u style="color: red;">長期間ログを保存できる(30日以上)</u>
        - <u style="color: red;">ログを解析に回すことができる</u>
        - <u style="color: red;">リアルタイムデータを処理することができる</u>

- `AutoMLを使用する理由`: MLAPIsではさまざまなものを検出・翻訳できる(例えばCloud Vision APIでは画像内に何があるかを検出できる)が、特定のものを検出・判別したいとなった際(画像内からウォーリーだけを見つけたいとか)にはトレーニングが必要となる。AutoMLを使用すると、この時に画像内に何があるか見つけるというトレーニングを省くことができるというメリットがある

- Datastore(現在はFirestoreというサービス)に採用されている`ドキュメント型DB`とは自由な形式のデータ(JsonやXML)を保存することができる
  - 最適な用途としては
    - ACIDプロパティに基づくトランザクション
    - 小売店向けにリアルタイム在庫と商品の詳細を提供するカタログ

- サービスアカウントの利用は`ツールやAPI、アプリケーションからのアクセスを許可する場合`に有効