# kubernetesクラスターからのpodの削除

**<span style="color: red; ">【masterノードで実施（Terminal Host 1）】</span>**  

Step6で作成したmanifestファイルで、kubernetesクラスターからPodを削除します。  

①下記のコマンドでkubernetesクラスターからPodを削除します。  

$ `kubectl delete -f nginxphp_pod.yaml`{{execute HOST1}}  

②Podの起動状況を確認します。

$ `kubectl get pods`{{execute HOST1}}  

