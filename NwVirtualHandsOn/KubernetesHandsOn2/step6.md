# manifestファイル（yaml）作成

**<span style="color: red; ">【masterノードで実施（Terminal Host 1）】</span>**  

Podを作成するためにmanifestファイル（nginxphp_pod.yaml）を作成し、Podを作成します。

①manifestファイル（nginxphp_pod.yaml）のコンテナイメージ名（二箇所）を編集します。（「xxx.xxx.xxx.xxx」はregistryノードのIPアドレスを指定します。<span style="color: red; ">但し、本レッスンではmasterノードのIPアドレス（控えた「ens3」のIPアドレス）を指定します。</span>）   

$ `cd`{{execute HOST1}}  
$ `vi nginxphp_pod.yaml`{{execute HOST1}}  

```yaml  
apiVersion: v1
kind: Service           #サービスを定義
metadata:
  name: nginx-service   #Serviceリソース名
  labels:
    app: nginx          #対象のアプリケーション名
spec:
  type: NodePort        #ノードのポートでアクセスを受付け
  ports:
  - port: 80            #クラスタ内仮想IPのポート番号
    targetPort: 80      #コンテナのポート番号
    nodePort: 31001     #受付けノードのポート番号
    protocol: TCP       #TCPプロトコル
  selector:
    app: nginx          #割当てポートのアプリケーション名
---
apiVersion: apps/v1
kind: Deployment        #実行方法を定義
metadata:
  name: nginx           #Deploymentリソース名
spec:
  replicas: 2           #生成するPod数
  selector:
    matchLabels:
      app: nginx        #Deploymentリソースで管理するPodのラベル
  template:
    metadata:
      labels:
        app: nginx      #アプリケーション名
    spec:               #Podに用いるコンテナの定義
      containers:
      - name: nginx     #コンテナ名
        image: xxx.xxx.xxx.xxx:5000/mynginx:1.0
        ports:
        - containerPort: 80     #コンテナにアクセスされるポート番号
      - name: phpfpm    #コンテナ名
        image: xxx.xxx.xxx.xxx:5000/myphpfpm:1.0
        ports:
        - containerPort: 9000   #コンテナにアクセスされるポート番号
```  
