# 環境設定とdockerのインストール（workerノード）  
<u>**<span style="color: red; ">※このステップは本レッスンでは必要ありません。</span>**</u>

本レッスンでは必要ありませんが、Kubernetesクラスター環境を動作させる実workerノードでは下記の手順（①~⑨）で**kubeadm**をインストール必要があります。

**<span style="color: red; ">（workerノードで実施（HOST 2））</span>**  

①ホスト名の変更します。<span style="color: red; ">（※”_”,”-”はホスト名に使えない。）</span>  

$ `sudo hostnamectl set-hostname worker1`  

②/etc/hostsファイルの変更します。

$ `sudo vi /etc/hosts`  
```
127.0.0.1   localhost   worker1
```

③rootにユーザを切り替えます。  

\# `sudo -s`  

④dockerをインストールします。（ubuntuのリポジトリのものを使用します。）  

\# `apt install docker.io`  

⑤システム起動時に起動するように設定します。  

\# `systemctl enable docker`  

