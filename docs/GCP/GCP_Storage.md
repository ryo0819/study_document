# ストレージ系

- 一回限りのデータ転送に使われる　-> `Transfer Appliance`(<span style="color: red; ">直接GCSに転送することはできない</span>)

  - パブリックインターネットを介して転送できるオプションがない場合に利用が推奨される(ISPと場所によっては`Dedicated InterConnectも選択肢としてあり`)

- 繰り返されるデータ転送 -> `Storage Transfer Service`(他クラウド/オンプレからデータを転送できる)

  - ＋α: 10TB以上は転送することはできない

- ローカルから最も効率よくデータ転送する方法 -> gsutil cp <span style="color: red; ">**-m**</span>とすることでマルチスレッドで処理することができる

- `Cloud Storage`: データ量制限なし、TTLの設定、保存できるものはなんでも(動画/音声/画像など)

  - zipファイルに一時的にアクセスしたい場合は<u style="color: red;">有効期限を持つ署名付きURLを作成することができる</u>