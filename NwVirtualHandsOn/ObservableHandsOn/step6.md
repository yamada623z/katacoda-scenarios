# メトリクス機能を有効にする
最初の作業は、メトリクス機能を有効にする（新しい）experimentalフラグを有効にし、localhost:9323でリッスンするメトリクスアドレスを定義することです。「/etc/docker/daemon.json」に記述し、dockerをリスタートします。（下記の「{"metrics-addr"～」の行を追加します。※前の行の文末に「,」を追加してください。）  

\# `vi /etc/docker/daemon.json`{{execute}}  
```json
{
    "bip":"172.18.0.1/24",
    "debug": true,
    "storage-driver": "overlay",
    "registry-mirrors": ["http://docker-registry-mirror.katacoda.com"],
    "insecure-registries": ["registry.test.training.katacoda.com:4567", "docker-registry-mirror.katacoda.com"],
    "metrics-addr": "127.0.0.1:9323", "experimental": true}
}
```
\# `systemctl restart docker`{{execute}}  
<br>

dockerが開始すると、メトリックエンドポイントにアクセスできるようになります。下記のコマンドで表示できます。  

\# `curl localhost:9323/metrics`{{execute}}  
