# Overview
Docker環境でfluentdを使ってログを収集する実験用

# 構成
Dockerのコンテナで`cron`によって日付情報`Sun Jul 28 09:49:01 UTC 2019`このようなものが毎分出力されます。  
その出力内容を`fluentd`でtailし、別のfluentdに送信します。  
受け側のfluentdは受けたものをテキストログに出します。

# 実行方法

```shell
cd ./docker
docker-compose up -d
```
