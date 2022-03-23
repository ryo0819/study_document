| AWS | GCP |
| --- | --- |
| `Storage Gateway` | `VPC Service Control` |
| オンプレミスサーバーにマウントしているディスクをクラウドから読み書き可能 | |
| `ELB` | `Cloud Load Balancing` |
| レイヤー4、レイヤー7の負荷分散を提供 |  |
| `Direct Connect` | `Cloud Interconnect`,<br>`Partner Interconnect` |
| 自社環境とクラウドをセキュアに接続するネットワーク(レイヤー2) |  |
| `VPC` | `VPC` |
| 仮装ネットワーク(レイヤー3) |  |
| `Route 53` | `Cloud DNS` |
| DNSのフルマネージドサービス |  |
| `Cloud Front` | `Cloud CDN` |
| CDN(コンテンツデリバリーネットワーク)のフルマネージドサービス |  |
| `RDS`,<br>`Aurora(RDBMS)`<br>MySQLやPostgresSQLを含む6種 | `Cloud SQL`<br>ストレージ10TBまで(Json形式は使用できない)<br>MySQL,PostgresSQLの2種類<br>BIツール向けのデータセット分析可能 |
| `Dynamo DB`,<br>`Neptune(NoSQL)`<br>低レイテンシーで高スループット | `Cloud Bigtable`(ストレージ数TB/数PB, NoSQLDB),<br>`Cloud Datastore`(csv形式は使用できない,トランザクションに使用できる, NoSQLドキュメントデータベース) |
| `Aurora Serverless(分散型RDBMS)`<br>ストロングコンシステンシーとスケーラビリティを兼備<br>複雑なクエリにも対応できる<br>複数のリージョン間でアクセスされた時に強力なトランザクションの一貫性を保証 | `Cloud Spanner`<br>グローバルに水平方向にスケーラブル可能<br>フルマネージド<br>メタデータの保存に適している(DataCatalog)<br>99.999%の可用性<br>無制限のスケーリング<br>RDBでありながら、NoSQLの特徴も持つ |
| `RedShift`<br>`Athena` | `BigQuery`<br>データウェアハウス |
| `Batch`<br>`Kinesis`<br>`SWF`<br>`Data Pipeline` | `Cloud Dataflow`(バッチ処理&ストリーミング処理)<br>Apache BEAMをベース<br>フルマネージド |
| `Elastic Map Reduce` | `Cloud Dataproc`(Spark,Hadoop)<br>MapReduceをベース<br>フルマネージド |
| `SageMaker` | `Cloud Datalab`<br>`Google Colab`(データ分析)<br>Jupyter Notebookをベース<br>フルマネージド |
|  | `Cloud Composer`<br>Apache Airflowのフルマネージド<br>ワークフローは非循環グラフ(DAG)<br>pythonを使用 |
| `Glue` | `Cloud Dateprep`(ETL/データクレンジングツール)<br>技術者でなくても可能<br>フルマネージド<br>Dataflow上で稼働する<br>コード要らず |
| `SNS`<br>`SMS` | `Cloud Pub/Sub`(非同期メッセージング) |
|  | `Google Genomics`(遺伝子解析) |
| `QuickSight` | `Google Data Studio`(BIツール)<br>GCSやBigQueryなどと連携可<br>チャンネルデータ用にyoutubeも設定できる<br>データソースのデータをキャッシュするが微調整することができる |
| `IoT core`<br>`MQ`<br>`Greengrass`<br>`IoT Analytics`<br>`freeRTOS`<br>`IoT Device Defender` | `IoT Core` |
| `Machine Learning`<br>`深層学習AMI`<br>`Apache MXNet`<br>`TensorFlow` | `Google Cloud Machine Learning`<br>TensorFlowを用いた機械学習サービス |
| `Comprehand` | `Google Cloud Natural Language API`<br>自然言語分析,構文解析や感情分析 |
| `Comprehand`<br>`Polly`<br>`Transcribe` | `Cloud Speech API`<br>音声のテキスト変換サービス<高速なニューラルネットワーク> |
| `Translate` | `Cloud Translation API`<br>テキスト翻訳サービス、動的翻訳 |
| `Rekognition`<br>`DeepLens` | `Cloud Vision API`<br>画像分析サービス<br>不適切検出<br>文字認識(OCR) |
|  | `Cloud Video Intelligence API`<br>動画コンテンツ分析(メタデータの抽出) |
| `Lex` | `Dialogflow`<br>音声/テキスト対応のチャットボット |
| `CloudWatch` | `Stackdriver Monitoring`<br>ロギング、モニタリング、アラート、パフォーマンスなど<br>一部GCPからAWSも監視可能 |
| `CloudFormation` | `Cloud Deployment Manager` |
| `API Gateway` | `Cloud Endpoints`<br>APIの構築/デプロイ/管理 |
|  | `AI Platform`<br>シリアル化されたトレーニングモデルを保存済み<br>モデルとしてサービスに渡し、バージョン管理する<br>オンライン予測は応答メッセージで返却<br>バッチ予測はより複雑なモデルで大量の予測を処理 |
| `AWS CloudTrail` | `Cloud Audit Logs`<br>誰がどこで何をしたか確認できる |
