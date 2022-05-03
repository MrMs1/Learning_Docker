# docker-compose

docker-compose.ymlファイルで複数のコンテナ実行を一括で管理できる。  
ファイル内で設定を記載するほかにも、build属性で個別のDockerファイルを指定することも可能。

---

## コマンド

```sh
docker-compose up -d
```

コンテナ群の起動。Dockerイメージのビルド、実行を行う。  
dオプションでバックグラウンド実行。  

```sh
docker-compose down
```

コンテナ群の停止・削除  
docker container stopと異なり、コンテナIDは不要。 

---
## volumes

ホスト・コンテナ間でファイルが共有される設定項目。  
COPY、docker container cpとは異なり、共有されるだけ。  
  
---
[TOPへ戻る](../README.md)  
