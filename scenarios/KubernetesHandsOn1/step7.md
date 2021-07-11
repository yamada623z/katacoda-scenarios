# workerノードのクラスターへの接続（kubeadm join）
**<span style="color: red; ">（masterノードで実施（HOST 1））</span>**  

Kubernetesクラスター環境を構築します。  

下記のコマンドで表示されたコマンドイメージをworkerノードで実行することにより、masterノードとjoinされます。

\# `kubeadm token create --print-join-command`{{execute HOST1}}  

**<span style="color: red; ">（workerノードで実施（HOST 2））</span>**  

masterノードで実行した上記のコマンドの応答をコピー＆ペーストしてworkerノードで実行します。

\# `kubeadm join 10.40.x.10:6443 --token xxxxxx.xxxxxxxxxxxxx --discovery-token-ca-cert-hash sha256:xxxxxxx`  

