# サービスアカウントの作成
**<span style="color: red; ">【masterノード（controlplane）で実施】</span>**  

サービスアカウントを作成し、「**admin-user**」権限でログインします。（全ての操作、表示が可能となります。）  

①下記のmanifestファイルを用意する。  
$ `cd`{{execute HOST1}}  
$ `vi service-account.yaml`{{execute}}  
```yaml
apiVersion: v1
kind: ServiceAccount
metadata:
  name: admin-user
  namespace: kube-system
---
apiVersion: rbac.authorization.k8s.io/v1beta1
kind: ClusterRoleBinding
metadata:
  name: admin-user
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: ClusterRole
  name: cluster-admin
subjects:
- kind: ServiceAccount
  name: admin-user
  namespace: kube-system
```
②作成したmanifestファイルをデプロイします。  
$ `kubectl apply -f service-account.yaml`{{execute}}  

③下記のコマンドで、「admin-user-token-xxxxx」の生成を確認します。  
$ `kubectl -n kube-system get secret | grep admin-user-token`{{execute}}  
**（表示例）**
```
admin-user-token-xxxxx kubernetes.io/serviceaccount-
token 3 40m
```  
④「admin-user-token-xxxxx」を指定して、tokenを取得します。  
$ `kubectl -n kube-system describe secret admin-user-token-xxxxx`  
**（表示例）**
```
Name:         admin-user-token-xxxxx
Namespace:    kube-system
Labels:       <none>
Annotations:  kubernetes.io/service-account.name: admin-user
              kubernetes.io/service-account.uid: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx

Type:  kubernetes.io/service-account-token

Data
====
ca.crt:     1025 bytes
namespace:  11 bytes
token: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```  
⑤上記の「**token:**」以降の文字列（xxxxの部分）をマウスで選択し、コピーします。   
⑥現在、ダッシュボードに表示されている「Kubernetes Dashboard」のウインドウ上のラジオボタン「**トークン**」をチェックし、下段の「**トークンを入力**」に⑤でコピーした文字列をペーストして「**サインイン**」ボタンをクリックします。  

**（表示例）**  
![DashBoard Image](./assets/Step13.png)  

