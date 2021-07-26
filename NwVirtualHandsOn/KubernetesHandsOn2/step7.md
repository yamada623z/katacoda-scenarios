# kubernetesクラスターへのpodの作成
Step6で作成したmanifestファイルで、kubernetesクラスターへPodを作成します。  
<br>
**<span style="color: red; ">【masterノードで実施（Terminal Host 1）】</span>**  

①下記のコマンドでkubernetesクラスターへPodを作成します。  

$ `kubectl apply -f nginxphp_pod.yaml`{{execute HOST1}}  

②Podの起動状況を確認します。

$ `kubectl get pods`{{execute HOST1}}  

