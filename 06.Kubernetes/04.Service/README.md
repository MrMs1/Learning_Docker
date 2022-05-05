# Service

Podの集合に対する経路やサービスディスカバリを提供する。

## ClusterIP Service

デフォルトのService。  
Kubernetesクラスタ上の内部IPアドレスにServiceを公開する。
Pod間の通信を可能にする。  

## NodePort Service

Kubernetesクラスタ外からアクセスできるようにする。  
各ノード上からServiceポートへ接続するためのグローバルなポートを開ける点でClusterIP Serviceと異なる。  

## LoadBalancer Service

ローカルKubernetes環境では利用できないService。  
各クラウドプラットフォームで提供されているロードバランサーと連携するためのもの。  

## ExternalName Service

Kubernetesクラスタ内から外部ホストを解決するためのエイリアスを提供する。  
