# workerノードのクラスターへの接続（kubeadm join）
**<span style="color: red; ">【masterノードで実施（Terminal Host 1）】</span>**  

Kubernetesクラスター環境を構築します。  

①下記のコマンドで表示されたコマンドイメージをworkerノードで実行することにより、masterノードとjoinされます。

$ `kubeadm token create --print-join-command`{{execute HOST1}}  

**<span style="color: red; ">【workerノードで実施（Terminal Host 2）】</span>**  

②masterノードで実行した上記のコマンド（①）の応答を **<span style="color: red; ">コピー＆ペースト</span>** してworkerノードで実行します。

**（例）**  
$ `kubeadm join xxx.xxx.xxx.xxx:6443 --token xxxxxx.xxxxxxxxxxxxx --discovery-token-ca-cert-hash sha256:xxxxxxx`  

