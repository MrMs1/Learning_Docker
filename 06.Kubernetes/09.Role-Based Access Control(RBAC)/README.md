# Role-Based Access Control(RBAC)

Kubernetesリソースへのアクセスをロールによって制御するための機能・概念。  
`Kubernetes APIのどの操作が可能であるかを定義したロール`  
と  
`認証ユーザー・グループ・ServiceAccountとロールの紐づけ`  
の2つの要素で成立する。

## RBACのKubernetesリソース

|  リソース名  |  内容  |
| ---- | ---- |
|  Role  |  Kubernetes APIへの操作許可のルールを定義し、指定のnamespace内でのみ有効  |
|  RoleBinding  |  認証ユーザー・グループ・ServiceAccount と Role の紐づけを定義する  |
|  ClusterRole  |  Kubernetes APIへの操作許可のルールを定義し、クラスタ全体で有効  |
|  ClusterRoleBinding  |  認証ユーザー・グループ・ServiceAccount と ClusterRole の紐づけを定義する  |

## Kubernetesのユーザー

|  名称  |  内容  |
| ---- | ---- |
|  認証ユーザー  |  クラスタ外からKubernetesを操作するためのユーザー  |
|  ServiceAccount  |  Kubernetes内部で管理され、Pod自身がKubernetes APIを操作するためのユーザー  |

### 認証ユーザー

kubectl等でKubernetesを操作するために提供される。  
グループという認証ユーザーをグルーピングする概念もある。 
以下の認証方法がある。  

- ServiceAccountトークン方式
- 静的トークンファイル方式
- パスワードファイル方式
- X509でのクライアント証明書方式
- OpenID Connect方式

### ServiceAccount

Kubernetesのリソースとして提供される。  
ServiceAccountと紐づけられたPodは与えられた権限の範囲内でKubernetesリソースの操作が可能。  
アプリケーション経由でKubernetes操作を制御できる。  

---
[Kubernetesへ戻る](../README.md)

---
[TOPへ戻る](../../README.md)