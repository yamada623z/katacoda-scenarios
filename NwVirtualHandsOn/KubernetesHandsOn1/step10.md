# ダッシュボードの実装とアクセス
**<span style="color: red; ">【masterノードで実施（HOST 1）】</span>**  

①下記の手順でダッシュボードへのアクセスの為の証明書を作成します。  

$ `mkdir $HOME/certs`{{execute HOST1}}  

$ `cd $HOME/certs`{{execute HOST1}}  

$ `openssl genrsa 2048 > dashboard.key`{{execute HOST1}}  

$ `openssl req -new -key dashboard.key > dashboard.csr`{{execute HOST1}}  
（「Country Name」のみ「JP」を入力し、その後はEnterキーで何も入れません。）

$ `openssl x509 -days 3650 -req -signkey dashboard.key < dashboard.csr > dashboard.crt`{{execute HOST1}}  

②作成した証明書からsecretを作ります。  

$ `kubectl create secret generic kubernetes-dashboardcerts --from-file=$HOME/certs -n kube-system`{{execute HOST1}}  

**（表示例）**  
```
secret/kubernetes-dashboard-certs created
```  

③ダッシュボードをPodとして、クラスターに実装します。  
$ `kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.0.0-beta8/aio/deploy/recommended.yaml`{{execute HOST1}}  
<br>

④クラスターの状況を確認します。  

$ `kubectl cluster-info`{{execute HOST1}}  
**（表示）**  
```
Kubernetes master is running at https://xxx.xxx.xxx.xxx:6443
KubeDNS is running at
https://xxx.xxx.xxx.xxx:6443/api/v1/namespaces/kubesystem/services/kube-dns:dns/proxy
```  

<u>**<span style="color: red; ">※下記のコマンドは本レッスンでは必要ありません。</span>**</u>

本レッスンでは必要ありませんが、実ノードでは「**kubectl proxy**」を起動し、ブラウザでアクセスすることができます。  

$ `kubectl proxy`  
**（表示例）**  
```
Starting to serve on 127.0.0.1:8001
```
ブラウザでは下記のURLを指定します。  

`http://localhost:8001/api/v1/namespaces/kubesystem/
services/https:kubernetes-dashboard:/proxy/`  

