# プライベートレジストリの構築  
プライベートレジストリ（ノンセキュア※）を構築します。自己で作成したコンテナイメージを格納し、Podをビルドする際に使用します。これを構築しないと、Podをスケールした際に新しいPodがイメージの無いノードでビルドされません。  
※外部公開をしないデバッグ環境での利用の為、セキュリティ無しで構築します。  
<br>

**<span style="color: red; ">【registryノードで実施】※本レッスンではmasterノードで実施します。</span>**  

①rootにユーザを切り替えます。  

$ `sudo -s`{{execute HOST1}}  

②dockerをインストールします。（ubuntuのリポジトリのものを使用します。）<span style="color: red; ">（本レッスンでは不要です。）</span>  

\# `apt install docker.io`  

③システム起動時に起動するように設定します。<span style="color: red; ">（本レッスンでは不要です。）</span>  

\# `systemctl enable docker`  

④docker上で動作させる「registry」の最新のコンテナイメージをpullする。

\# `docker pull registry`{{execute HOST1}}  

⑤「registry」のコンテナイメージをポート5000を指定して起動します。

\# `docker run -dit -p 5000:5000 --name registry -e REGISTRY_STORAGE_DELETE_ENABLED=true registry`{{execute HOST1}}  
<br>

**<span style="color: red; ">【master/workerノードで実施】（Step1で実施しています）</span>**  

⑥「daemon.json」ファイルを生成し、「/etc/docker]
に配置します。（「xxx.xxx.xxx.xxx」はregistryノードのIPアドレスを指定します。）  
```json
{
  "insecure-registries" : [“xxx.xxx.xxx.xxx:5000"]
}
```

⑦dockerを再起動します。（「daemon.json」ファイルの反映）  

\# `systemctl restart docker`  

（一般ユーザに戻します）  

\# `exit`{{execute HOST1}}  
<br>

## 【プライベートレジストリの利用方法】  
※例として、作成するコンテナイメージを「mynginx:1.0」、registryノードのIPアドレスを「xxx.xxx.xxx.xxx」とします。

①コンテナイメージを作成します。  
$ `docker build --no-cache mynginx:1.0 .`  

②コンテナイメージの名前を変更します。  
$ `docker tag mynginx:1.0 xxx.xxx.xxx.xxx:5000/mynginx:1.0`  

③コンテナイメージをレジストリにpushします。  
$ `docker push xxx.xxx.xxx.xxx:5000/mynginx:1.0`  

- docker pushまたはpullコマンドで、イメージ名が指定された形式と一致しない場合はプライベートレジストリからではなく、パブリックレジストリからコンテナイメージをpushまたはpullしようとします。  
- 一度、Dockerイメージをpushすると、同じイメージ名でも上書きができません。（イメージ生成時にリビジョンを変更をするなどが必要。）  
- プライベートレジストリで管理されているコンテナイメージの参照・削除などはWeb-UIを構築することで可能となります。    
（プライベートレジストリのWeb-UIの構築方法はstep3で説明します。）  

