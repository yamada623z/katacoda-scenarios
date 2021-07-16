# オートヒーリングの動作確認

**<span style="color: red; ">【masterノードで実施（Terminal Host 1）】</span>**  

①現在のPodの状態を確認する。  
$ `kubectl get pods`{{execute HOST1}}  

②Podを削除します。  
$ `kubectl delete pods nginx-xxxxxxxx-xxxx`  

- ①のコマンドで表示されたPod名（nginx-xxxxxxxx-xxxx）を指定する。  

②ブラウザをリロードして、サービスが継続していることを確認します。  

④下記のコマンドでPodの状態を確認する。  
$ `kubectl get pods`{{execute HOST1}}  

- 削除した分のPodが新たに生成されていることを確認する。  

