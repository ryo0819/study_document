# ローカル検証手順
1. プロジェクトフォルダ内のmkdocs.ymlファイルと同じディレクトリにいることを確認してから、以下のDockerコマンドを実行
  ```
  docker run --rm -it -p 8000:8000 -v `pwd`:/docs squidfunk/mkdocs-material
  ```
