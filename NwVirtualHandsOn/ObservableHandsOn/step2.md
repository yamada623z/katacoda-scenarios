# prometheusのコンフィグ設定#1  
prometheusサーバーには、スクレイプ（観測値を収集すること）するエンドポイントと、メトリック（観測値）にアクセスする頻度を定義する構成ファイルが必要です。  

\# `vi prometheus.yml`{{execute}}
```yaml
global:
  scrape_interval:     15s
  evaluation_interval: 15s

scrape_configs:
  - job_name: 'prometheus'

    static_configs:
      - targets: ['127.0.0.1:9090', '127.0.0.1:9100']
        labels:
          group: 'prometheus'
```

**scrape_interval**：観測値の収集頻度  
**evaluation_interval**：観測値のルールの評価を行う間隔<span style="color: red; ">※1</span>  

- prometheusがデータをスクレイピングするサーバーとポートを定義します。 この例では、異なるポートで実行される2つのターゲットを定義しています。  

- 9090ポートはprometheusそのものです。 prometheusは、内部のメトリックとパフォーマンスに関連する情報を公開し、それ自体を監視できるようにします。  

- 9100ポートは、NodeExporterPrometheusプロセス<span style="color: red; ">※2</span>です。 これにより、ディスクスペース、メモリ、CPU使用率などのノードに関する情報が公開されます。  

<span style="color: red; ">※1</span>：観測値のルール（閾値を超過した場合のアラート通知など）を規定し、その評価を行う間隔を指定します。  

<span style="color: red; ">※2</span>：NodeExporterPrometheusプロセスはノードのシステムメトリックスを収集するプロセスです。  

