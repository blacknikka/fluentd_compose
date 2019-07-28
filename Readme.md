# Overview
Docker環境でfluentdを使ってログを収集する実験用

# 構成
Dockerのコンテナで`cron`によって日付情報`Sun Jul 28 09:49:01 UTC 2019`このようなものが毎分出力されます。  
その出力内容を`fluentd`でtailし、別のfluentdに送信します。  
受け側のfluentdは受けたものをテキストログに出します。

# 実行方法

`docker-compose`が２つある構成です。  
その２つのネットワークを繋げる為のネットワークを作成することを想定しています。

```shell
docker network create --driver bridge fluent_test

cd ./compose-client
docker-compose up -d
cd ../compose-server
docker-compose up -d
```
