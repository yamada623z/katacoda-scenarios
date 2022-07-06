# ダッシュボードの実装とアクセス
**<span style="color: red; ">【masterノード（controlplane）で実施】</span>**  

①下記の手順でダッシュボードへのアクセスの為の証明書を作成します。  

$ `mkdir $HOME/certs`{{execute}}  

$ `cd $HOME/certs`{{execute}}  

$ `openssl genrsa 2048 > dashboard.key`{{execute}}  

$ `openssl req -new -key dashboard.key > dashboard.csr`{{execute}}  
（「Country Name」のみ「JP」を入力し、その後はEnterキーで何も入れません。）

$ `openssl x509 -days 3650 -req -signkey dashboard.key < dashboard.csr > dashboard.crt`{{execute}}  

②作成した証明書からsecretを作ります。  

$ `kubectl create secret generic kubernetes-dashboardcerts --from-file=$HOME/certs -n kube-system`{{execute}}  

**（表示例）**  
```
secret/kubernetes-dashboard-certs created
```  

③ダッシュボードをPodとして、クラスターにインストールします。  
$ `kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.0.3/aio/deploy/recommended.yaml`{{execute}}  
<br>

④クラスターの状況を確認します。  

$ `kubectl cluster-info`{{execute}}  
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

