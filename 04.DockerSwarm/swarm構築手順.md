# Docker Swarm 構築手順

## 1. Swarmクラスタを構成する [docker-compose.yml](./docker-compose.yml) の作成

## 2. コンテナ群の起動

```sh
docker-compose up -d
```

## 3. クラスタの管理を行う manager の設定

```sh
docker container exec -it manager docker swarm init
```

swarm init を行ったDockerホストは manager としてマークされ、Swarmモードが有効になる。  
swarm init 実行時に`JOINトークン`が発行される。  
他のDockerホストをSwarmクラスタのworkerとして登録するためにこのトークンが必要。

## 4. worker の登録

```sh
docker container exec -it worker01 docker swarm join --token [swarm init 時に発行されたトークン] manager[またはトークン発行時に出力されたIPアドレス]:[トークン発行時に出力されたポート]
```

同様に各workerで上記コマンドを実行する。  
docker swarm join 以降の記述は swarm init 時に出力されるコマンドをコピペすればいい。  

**Swarmの構築はここまでで完了する。**  
以降は、Swarm内にStackをデプロイする手順を記載する。  

## 5. overlayネットワークの作成

SwarmにデプロイするStackの各Serviceを所属させるoverlayネットワークを作成する。

```sh
docker container exec -it manager docker network create --driver=overlay --atachable [ネットワーク名]
```

## 6. Stackのデプロイ

Stackを構成するServiceを記述した[ymlファイル](./stack/ch03-webapi.yml)を作成し、以下のコマンドを実行。  
-c デプロイするStackの定義ファイルを指定する。  
ymlファイルのパスはコンテナ内でのパス、つまりマウントしているディレクトリにymlファイルを配置し、コンテナ内でのパスを指定する。  

```sh
docker container exec -it manager docker stack deploy -c [ymlファイルのパス] [Stack名]
```

デプロイされたStackの確認

```sh
docker container exec -it manager docker stack services [option] [Stack名]
```

デプロイされたコンテナ群の確認  
コンテナがどのように配置されているかを確認できる。

```sh
docker container exec -it manager docker stack ps [Stack名]
```

Docker Hub のdockersamples/visualizerのイメージを使用することで配置されているコンテナの可視化が可能（ブラウザで閲覧できる）。
[visualizerのStack](./stack/visualizer.yml)をデプロイしてServiceへアクセスすることでイメージでコンテナの配置を確認できる。

## 7. プロキシサーバーの設置

Serviceが複数のコンテナが複数のノードに分散して配置されているため、Serviceクラスタ外（ホスト側）からアクセスするのが困難である。  
そのため、Serviceクラスタ外からのトラフィックを目的のServiceへ転送するプロキシサーバーを設置する。  
dockercloud/haproxyを使用する。  
[nginxのyml](./stack/ch03-webapi.yml)にSERVICE_PORTSを追加し、ポートフォワーディングするポートを指定する。  
指定する値は[Swarm](docker-compose.yml)の公開しているポートである80。  
nginxのStackを再デプロイ後、[プロキシサーバーのStack](./stack/ch03-ingress.yml)もデプロイする。

---
[Docker Swarm へ戻る](README.md)  

---
[TOPへ戻る](../README.md)  