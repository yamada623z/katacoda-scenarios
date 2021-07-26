# 準備  
このステップは、Katacodaでkubernetesのクラスターを構築・利用するための手順です。実ノードでは、kubernetesのクラスターをあらかじめ構築しておく必要があります。  
<br>

**<span style="color: red; ">【masterノードで実施（Terminal Host 1）】</span>**  

①masterノードのIPアドレスを確認します。（「ens3」のIPアドレスを控えておきます。）

$ `ifconfig`{{execute HOST1}}  

②rootにユーザを切り替えます。  

$ `sudo -s`{{execute HOST1}}  

③「/etc/docker/daemon.json」の「"insecure-registries"」の行を編集します。（「xxx.xxx.xxx.xxx」はregistryノードのIPアドレスを指定します。<span style="color: red; ">※但し、本レッスンではmasterノードのIPアドレス（控えた「ens3」のIPアドレス）を指定してください。</span>）  

\# `vi /etc/docker/daemon.json`{{execute HOST1}}  

```json
{
      "insecure-registries": ["xxx.xxx.xxx.xxx:5000","registry.test.training.katacoda.com:4567", "docker-registry-mirror.katacoda.com"]
}
```  

④dockerを再起動します。（「daemon.json」ファイルの反映）  

\# `systemctl restart docker`{{execute HOST1}}  

（一般ユーザに戻します）  

\# `exit`{{execute HOST1}}  
<br>

**<span style="color: red; ">【workerノードで実施（Terminal Host 2）】</span>**  

④rootにユーザを切り替えます。  

$ `sudo -s`{{execute HOST2}}  

⑤「/etc/docker/daemon.json」の「"insecure-registries"」の行を編集します。（「xxx.xxx.xxx.xxx」はregistryノードのIPアドレスを指定します。<span style="color: red; ">※但し、本レッスンではmasterノードのIPアドレス（控えた「ens3」のIPアドレス）を指定してください。</span>）  

\# `vi /etc/docker/daemon.json`{{execute HOST2}}  

```json
{
      "insecure-registries": ["xxx.xxx.xxx.xxx:5000","registry.test.training.katacoda.com:4567", "docker-registry-mirror.katacoda.com"]
}
```  

⑥dockerを再起動します。（「daemon.json」ファイルの反映）  

\# `systemctl restart docker`{{execute HOST2}}  

（一般ユーザに戻します）  

\# `exit`{{execute HOST2}}  
<br>

**<span style="color: red; ">【masterノードで実施（Terminal Host 1）】</span>**  

⑦「launch.sh」を実行してください。  

$ `launch.sh`{{execute HOST1}}  
<br>

⑧ノード状態を確認し、クラスターの正常性を確認します。  

$ `kubectl get nodes`{{execute HOST1}}  

**（表示例）**  
```  
$ kubectl get nodes
NAME           STATUS   ROLES    AGE   VERSION
controlplane   Ready    master   84s   v1.18.0
node01         Ready    <none>   24s   v1.18.0
```

⑨ハンズオンに必要なファイルはカレントのフォルダにあります。確認してください。  

**<span style="color: red; ">【masterノードで実施（Terminal Host 1）】</span>**  

$ `ls -la`{{execute HOST1}}  

**（表示例）**  
```  
-rw-r--r--  1 root root  1135 Apr 27 02:09 default.conf
-rw-r--r--  1 root root    32 Apr 27 02:09 index.php
-rw-r--r--  1 root root   655 Apr 27 02:09 nginxphp_pod.yaml
-rw-r--r--  1 root root    95 Apr 27 02:09 php-fpm.conf
-rw-r--r--  1 root root 72763 Apr 27 02:09 php.ini
-rw-r--r--  1 root root    37 Apr 27 02:09 test.php
-rw-r--r--  1 root root   217 Apr 27 02:09 www.conf
```  
（ファイルの説明）  
default.conf：  
nginxの設定ファイルです。httpの待ち受けポートやphpとのインタフェース、始めに検出するファイルの位置などが設定されています。  

index.php：  
phpファイルです。phpの情報を表示させます。  

nginxphp_pod.yaml：  
nginx＋phpを連携するようにPodを作成するためのmanifestファイルです。（Step6で説明します）  

php-fpm.conf・php.ini・www.conf：  
phpの動作に必要な設定ファイルです。  

test.php：  
phpファイルです。現在、アクセス中のプロセス（Pod）の名前を表示させます。  
