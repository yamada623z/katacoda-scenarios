# workerノードのクラスターへの接続（kubeadm join）
<u>**<span style="color: red; ">※このステップは本レッスンでは必要ありません。</span>**</u>  

Kubernetesクラスター環境を構築します。  

①下記のコマンドで表示されたコマンドイメージをworkerノードで実行することにより、masterノードとjoinされます。

$ `kubeadm token create --print-join-command`{{execute}}  

**<span style="color: red; ">【workerノード（node01）で実施】</span>**  

②masterノード（controlplane）で実行した上記のコマンド（①）の応答を **<span style="color: red; ">コピー＆ペースト</span>** してworkerノードで実行します。

**（例）**  
$ `kubeadm join xxx.xxx.xxx.xxx:6443 --token xxxxxx.xxxxxxxxxxxxx --discovery-token-ca-cert-hash sha256:xxxxxxx`  

