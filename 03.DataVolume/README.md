# Data Volume

Dockerコンテナ内のディレクトリをディスクに永続化するための仕組み。

## コマンド

```sh
# vオプションで共有するディレクトリを指定
docker container run [option] -v ホスト側ディレクトリ:コンテナ側ディレクトリ リポジトリ名[:タグ] [コマンド] [コマンド引数]

```

---

## Data Volume コンテナ

Data Volumeではホストとコンテナが直接ディレクトリを共有するが、Data Volume コンテナを利用することでコンテナ間でディレクトリを共有する。  
Data Volume コンテナはデータを持つだけのコンテナである。  

---
[TOPへ戻る](../README.md)  
