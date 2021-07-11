# ダッシュボードの外部ノードからアクセス
**<span style="color: red; ">（masterノードで実施（HOST 1））</span>**  

masterノードのポートを使用して、外部ノードからアクセス出来るようにします。  

Podの状態からダッシュボードのみを表示します。  
\# `kubectl get pods --all-namespaces | grep dashboard`{{execute HOST1}}  

ダッシュボードの定義ファイルを編集します。  
\# `kubectl -n kubernetes-dashboard edit service kubernetes-dashboard`{{execute HOST1}}  

```
(省略）
spec:
(省略）
  ports:
  - port: 443
    protocol: TCP
    targetPort: 8443
    nodePort: 32002 <- nodePortを追加します（任意のポートを指定します。 例：32002）
(省略)
  type: ClusterIP <- この行を削除し、下記の行「type: NodePort」を追加します。
  type: NodePort
(省略)
```  
サービスの状態を取得し、確認します。  

\# `kubectl get svc --all-namespaces`{{execute HOST1}}  

**（表示例）**
```
kube-system kubernetes-dashboard    NodePort    10.111.163.244  <none>      443:32002/TCP   16m
```
ポート：32002で表示を確認します。  

ブラウザからのアクセスは以下の通り。（「10.40.x.10」はmasterノードのIPアドレスです。）  
`https://10.40.x.10:32002`  

**KatacodaのWebアクセス方法：**  
①ターミナルペインの「**Terminal Host 1**」のタグの隣の「**＋**」をクリックする。  
②表示されるドロップリストから「**Select port to view on Host 1**」をクリックする。  
③ボックスに「**32002**」を入力し、「**Display Port**」します。  

