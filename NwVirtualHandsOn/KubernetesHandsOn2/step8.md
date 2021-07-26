# kubernetesクラスターからのpodの削除
Step6で作成したmanifestファイルで、kubernetesクラスターからPodを削除します。  
<span style="color: red; ">※このステップを実施した場合は、Step7を再度、実施してください。</span>  
<br>
**<span style="color: red; ">【masterノードで実施（Terminal Host 1）】</span>**  

①下記のコマンドでkubernetesクラスターからPodを削除します。  

$ `kubectl delete -f nginxphp_pod.yaml`{{execute HOST1}}  

②Podの起動状況を確認します。

$ `kubectl get pods`{{execute HOST1}}  

