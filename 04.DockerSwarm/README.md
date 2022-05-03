# Docker Swarm

複数のDockerホストをクラスタ化するツール。  
コンテナオーケストレーションシステムの一つ。

---

## コンテナオーケストレーションにかかわる名称一覧

|  名称  |  役割  | コマンド  |
| ---- | ---- |---- |
|  Compose  |  複数のコンテナを使うDockerアプリケーションの管理（主にシングルホスト）  | docker-compose  |
|  Swarm  |  クラスタの構築や管理を担う（主にマルチホスト）  | docker swarm  |
|  Service  |  Swarm前提、クラスタ内のService（1つ以上のコンテナのあるまり）を管理する  | docker service  |
|  Stack  |  Swarm前提、複数のServiceをまとめたアプリケーション全体の管理  | docker stack  |

---

## Service

アプリケーションを構成する一部のコンテナを制御するための単位。  
docker service ls で一覧を確認できる。

---

## Stack

複数のServiceをグルーピングした単位。  
アプリケーション全体の構成を定義する。  
Serviceは1つのアプリケーションイメージしか扱えないため、複数のServiceをStackによって扱う。  

### overlayネットワーク

overlayネットワークは、複数のDockerホストにデプロイされているコンテナ群を同じネットワークに配置させる技術。  
StackによりデプロイされるService群は、overlayネットワークに所属する。  
Stackで利用するoverlayネットワークを設定しなければ、Stackの数だけoverlayネットワークが作成され、その中にService群が所属する。  
**他のoverlayネットワークに所属するServiceから別のoverlayネットワークをディスカバリ、通信することはできない。**  
あらかじめoverlayネットワークを作成しておき、Stackから作成されるServiceを所属させるようにすることで対応する。  
overlayネットワークの作成は managerコンテナ内で以下のコマンドを実行して行う。  

```sh
docker container exec -it manager docker network create --driver=overlay --atachable [ネットワーク名]
```

---

## 構築例

[Docker Swarm 構築手順](swarm構築手順.md)  

---
[TOPへ戻る](../README.md)  
