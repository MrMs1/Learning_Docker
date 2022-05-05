# Kubernetes

Google社主導で開発されたコンテナ運用の自動化のためのコンテナオーケストレーションシステム。  
Swarmよりも機能が充実している。

## kubectl

Kubernetesを操作するためのコマンドラインツール。  
[インストール](https://kubernetes.io/ja/docs/tasks/tools/install-kubectl/)が必要。  

## Dashboard

Kubernetesにデプロイされているコンテナを確認するWebベースの管理ツール。  
[利用方法](https://kubernetes.io/ja/docs/tasks/access-application-cluster/web-ui-dashboard/#%E3%83%80%E3%83%83%E3%82%B7%E3%83%A5%E3%83%9C%E3%83%BC%E3%83%89ui%E3%81%AE%E3%83%87%E3%83%97%E3%83%AD%E3%82%A4)

## 主なリソース

[Kubernetesクラスタ構成図](Kubernetesクラスタの構成.drawio.svg)  

|  リソース名  |  用途  |
| ---- | ---- |
|  [Node](https://kubernetes.io/ja/docs/concepts/architecture/nodes/)  |  Kubernetesクラスタで実行するコンテナを配置するためのサーバ  |
|  [Namespace](https://kubernetes.io/ja/docs/concepts/overview/working-with-objects/namespaces/)  |  Kubernetesクラスタ内で作る仮想的なクラスタ  |
|  [Pod](https://kubernetes.io/ja/docs/concepts/workloads/pods/)  |  コンテナ集合体の単位。コンテナ実行方法を定義する  |
|  [ReplicaSet](https://kubernetes.io/ja/docs/concepts/workloads/controllers/replicaset/)  |  同じ仕様のPodを複数生成・管理する  |
|  [Deployment](https://kubernetes.io/ja/docs/concepts/workloads/controllers/deployment/)  |  ReplicaSetの世代管理をする  |
|  [Service](https://kubernetes.io/ja/docs/concepts/services-networking/service/)  |  Podの集合にアクセスするための経路を定義する  |
|  [Ingress](https://kubernetes.io/ja/docs/concepts/services-networking/ingress/)  |  ServiceをKubernetesクラスタの外に公開する  |
|  [ConfigMap](https://kubernetes.io/ja/docs/concepts/configuration/configmap/)  |  設定情報を定義し、Podに供給する  |
|  [PersistentVolume](https://kubernetes.io/ja/docs/concepts/storage/persistent-volumes/)  |  Podが利用するストレージサイズや種別を定義する  |
|  [PersistentVolumeClaim](https://kubernetes.io/ja/docs/concepts/storage/persistent-volumes/)  |  PersistentVolumeを動的に確保する  |
|  [StorageClass](https://kubernetes.io/docs/concepts/storage/storage-classes/)  |  PersistentVolumeが確保するストレージの種類を定義する  |
|  [StatefulSet](https://kubernetes.io/ja/docs/concepts/workloads/controllers/statefulset/)  |  同じ仕様で一意性のあるPodを複数生成・管理する  |
|  [Job](https://kubernetes.io/docs/concepts/workloads/controllers/job/)  |  常駐目的でない複数のPodを作成し、正常終了することを保証する  |
|  [CronJob](https://kubernetes.io/ja/docs/concepts/workloads/controllers/cron-jobs/)  |  cron記法でスケジューリングして実行されるJob  |
|  [Secret](https://kubernetes.io/ja/docs/concepts/configuration/secret/)  |  認証情報等の機密データを定義する  |
|  [Role](https://kubernetes.io/ja/docs/reference/access-authn-authz/rbac/)  |  Namespace内で操作可能なKubernetesリソースのルールを定義する  |
|  [RoleBinding](https://kubernetes.io/ja/docs/reference/access-authn-authz/rbac/)  |  RoleとKubernetesリソースを利用するユーザーを紐づける  |
|  [ClusterRole](https://kubernetes.io/ja/docs/reference/access-authn-authz/rbac/)  |  Cluster全体で操作可能なKubernetesリソースのルールを定義する  |
|  [ClusterRoleBinding](https://kubernetes.io/ja/docs/reference/access-authn-authz/rbac/)  |  ClusterRoleとKubernetesリソースを利用するユーザーを紐づける  |
|  [ServiceAccount](https://kubernetes.io/docs/tasks/configure-pod-container/configure-service-account/)  |  PodにKubernetesリソースを操作させる際に利用するユーザー  |

## よく使用するコマンド

[kubectlチートシート](https://kubernetes.io/ja/docs/reference/kubectl/cheatsheet/)

## freshpod

Kubernetes上でデプロイされているコンテナイメージの更新を検知し、自動再デプロイを行う。  
containersのimagePullPolocyをIfNotPresetにする必要がある。  

## kube-prompt

macOS/Linux向けの補完ツール。  

## Kubernetes API

Kubernetesのリソース作成・更新・削除はKubernetesクラスタにデプロイされているAPIによって行われる。  
このAPIは複数のAPI群を束ねるように構成されており、apiVersionはリソースの操作に利用するAPIの種別を示している。  

## [Role-Based Access Control(RBAC)](09.Role-Based%20Access%20Control(RBAC)/README.md)

## [Helm](10.Helm/README.md)

---
[TOPへ戻る](../README.md)
