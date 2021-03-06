# スケーリング（manifestファイル利用）の動作確認
manifestファイルを利用してPodのスケーリング（サービスを継続したままでのPod数の増減）の操作確認を実施します。    

**<span style="color: red; ">【masterノードで実施（Terminal Host 1）】</span>**  

①現在のPodの状態を確認する。  
$ `kubectl get pods`{{execute HOST1}}  

②manifestファイル（nginxphp_pod.yaml）の下記の数字の部分を書き換えます。  
```yaml
  replicas: 2
```  
- 現在のPod数より増やすとスケールアウト（Pod数が増える。）  
- 現在のPod数より減らすとスケールイン（Podの数が減る。）

③下記のコマンドを実行する。  
$ `kubectl apply -f nginxphp_pod.yaml`{{execute HOST1}}  

④ブラウザをリロードして、サービスが継続していることを確認します。  

⑤下記のコマンドでPodの状態を確認する。（Pod数が②で指定した数であることを確認します）  
$ `kubectl get pods`{{execute HOST1}}  

