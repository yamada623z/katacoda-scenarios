# スケーリング（kubectlコマンド利用）の動作確認  
kubectlコマンドはkubernetesに関する各種操作を行うコマンドです。  
kubectlコマンドを利用してPodのスケーリング（サービスを継続したままでのPod数の増減）の操作確認を実施します。  

**<span style="color: red; ">【masterノードで実施（Terminal Host 1）】</span>**  

①現在のPodの状態を確認する。  
$ `kubectl get pods`{{execute HOST1}}  

②kubectlコマンド利用してPodをスケールします。（数字の部分を変更します）  
$ `kubectl scale --replicas=3 deployment.apps/nginx`{{execute HOST1}}  

- 現在のPod数より増やすとスケールアウト（Pod数が増える。）  
- 現在のPod数より減らすとスケールイン（Podの数が減る。）

③ブラウザをリロードして、サービスが継続していることを確認します。  

④下記のコマンドでPodの状態を確認する。（Pod数が②で指定した数であることを確認します）  
$ `kubectl get pods`{{execute HOST1}}  

