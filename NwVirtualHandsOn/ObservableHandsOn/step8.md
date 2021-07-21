# prometheusのスタート#2  
prometheusは、ポート9090で使用可能なUIを備えたdockerコンテナとして実行されます。prometheusは設定を使用してターゲットをスクレイプし、メトリクスを収集して保存した後、ダッシュボード、グラフ化、アラートを可能にするAPIを介して利用できるようにします。  

コマンドは、prometheus構成でコンテナを起動します。 prometheusによって作成されたデータはすべて、ホストのディレクトリ/prometheus/dataに保存されます。そのため、コンテナを更新しても、データは保持されます。  

\# `docker rm prometheus-server`{{execute}}  

\# `docker restart prometheus`{{execute}}

\# `docker run -d --net=host -v /root/prometheus.yml:/etc/prometheus/prometheus.yml --name prometheus-server prom/prometheus`{{execute}}  