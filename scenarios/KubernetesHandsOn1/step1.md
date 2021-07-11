# 環境設定とdockerのインストール（masterノード）  
**<span style="color: red; ">（※このステップは本レッスンでは必要ありません。）</span>**

本レッスンでは必要ありませんが、Kubernetesクラスター環境を動作させる実masterノードでは下記の手順（①~⑨）で**kubeadm**をインストール必要があります。  

**<span style="color: red; ">（masterノードで実施（HOST 1））</span>**  

**kubeadm**はKubernetesクラスター環境を高速に作成する方法として**kubeadm init**と**kubeadm join**というコマンドを提供するツールです。Kubernetesのクラスターを立ち上げ、稼働させる上で最低限必要なものを提供します。  
<br>

①ホスト名の変更します。  

$ `sudo hostnamectl set-hostname master`  

②/etc/hostsファイルの変更します。

$ `sudo vi /etc/hosts`  
```
127.0.0.1   localhost   master
```

③rootにユーザを切り替えます。  

\# `sudo -s`  

④dockerをインストールします。（ubuntuのリポジトリのものを使用。）  

\# `apt install docker.io`  

⑤システム起動時に起動するように設定します。  

\# `systemctl enable docker`  
