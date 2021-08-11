# オートヒーリングの動作確認
kubectlコマンドを利用してPodのオートヒーリング（サービスを継続したままでのPodの自動復旧）の操作確認を実施します。  

**<span style="color: red; ">【masterノードで実施（Terminal Host 1）】</span>**  

①現在のPodの状態を確認する。  
$ `kubectl get pods`{{execute HOST1}}  

②Podを削除します。  
$ `kubectl delete pods nginx-xxxxxxxx-xxxx`  

- ①のコマンドで表示されたPod名（nginx-xxxxxxxx-xxxx）を指定する。  

③ブラウザをリロードして、サービスが継続していることを確認します。  

④下記のコマンドでPodの状態を確認する。  
$ `kubectl get pods`{{execute HOST1}}  

- 削除した分のPodが新たに生成されていることを確認する。（削除したPod名の消滅、新たなPod名での生成を確認します）  

