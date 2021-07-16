# 準備  
このステップは、Katacodaでkubernetesのクラスターを構築・利用するための手順です。実ノードでは、kubernetesのクラスターをあらかじめ構築しておく必要があります。  
<br>

**<span style="color: red; ">【masterノードで実施（Terminal Host 1）】</span>**  

①rootにユーザを切り替えます。  

$ `sudo -s`{execute HOST1}  

②カレントのフォルダにある「daemon.json」の「"insecure-registries"」の行を編集し、「/etc/docker」に配置します。（「xxx.xxx.xxx.xxx」はregistryノードのIPアドレスを指定します）  

\# `vi daemon.json`{execute HOST1}  

```json
{
  "insecure-registries" : ["xxx.xxx.xxx.xxx:5000"]
}
```

\# `cp daemon.json /etc/docker`{execute HOST1}  

③dockerを再起動します。（「daemon.json」ファイルの反映）  

\# `systemctl restart docker`{execute HOST1}  

（一般ユーザに戻します）  

\# `exit`{execute HOST1}  
<br>

**<span style="color: red; ">【workerノードで実施（Terminal Host 2）】</span>**  

④rootにユーザを切り替えます。  

$ `sudo -s`{execute HOST2}  

②カレントのフォルダにある「daemon.json」の「"insecure-registries"」の行を編集し、「/etc/docker」に配置します。（「xxx.xxx.xxx.xxx」はregistryノードのIPアドレスを指定します）  

\# `vi daemon.json`{execute HOST2}  

```json
{
  "insecure-registries" : ["xxx.xxx.xxx.xxx:5000"]
}
```

\# `cp daemon.json /etc/docker`{execute HOST2}  

⑥dockerを再起動します。（「daemon.json」ファイルの反映）  

\# `systemctl restart docker`{execute HOST2}  

（一般ユーザに戻します）  

\# `exit`{execute HOST2}  
<br>

**<span style="color: red; ">【masterノードで実施（Terminal Host 1）】</span>**  

⑦「launch.sh」を実行してください。  

$ `launch.sh`{execute HOST1}  
<br>

⑧ノード状態を確認し、クラスターの正常性を確認します。  

$ `kubectl get nodes`{execute HOST1}  

**（表示例）**  
```  
$ kubectl get nodes
NAME           STATUS   ROLES    AGE   VERSION
controlplane   Ready    master   84s   v1.18.0
node01         Ready    <none>   24s   v1.18.0
```

⑨ハンズオンに必要なファイルはカレントのフォルダにあります。確認してください。  

**<span style="color: red; ">【masterノードで実施（Terminal Host 1）】</span>**  

$ `ls -la`{execute HOST1}  

**（表示例）**  
```  
-rw-r--r--  1 root root   400 Apr 27 07:03 daemon.json
-rw-r--r--  1 root root  1135 Apr 27 02:09 default.conf
-rw-r--r--  1 root root    46 Apr 27 02:09 Dockerfile_mynginx
-rw-r--r--  1 root root   193 Apr 27 02:09 Dockerfile_myphpfpm
-rw-r--r--  1 root root    32 Apr 27 02:09 index.php
-rw-r--r--  1 root root   655 Apr 27 02:09 nginxphp_pod.yaml
-rw-r--r--  1 root root    95 Apr 27 02:09 php-fpm.conf
-rw-r--r--  1 root root 72763 Apr 27 02:09 php.ini
-rw-r--r--  1 root root    37 Apr 27 02:09 test.php
-rw-r--r--  1 root root   217 Apr 27 02:09 www.conf
```
