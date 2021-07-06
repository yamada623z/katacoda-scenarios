# コンテナの起動（ポート割付）
「docker run」コマンドは、DockerイメージからDockerコンテナを作成・実行します。  

**（書式）**  
docker run <span style="color: red; ">[オプション] ｛イメージ名｝[:｛タグ名｝]</span>  

<span style="color: red; ">「-d</span>」は、バックグラウンドでコンテナを実行するオプションです。  
<span style="color: red; ">「-p ｛ホストのポート番号｝:｛コンテナーのポート番号｝」</span>のオプション指定で、Dockerホストマシンとポートマッピングを構成します。  
「nginx」は80番ポートを常時Listenするコンテナです。Dockerホストマシンとポートマッピングすることにより、Dockerホストマシンの80番ポートで入力を受け付けます。  

<span style="color: red; ">｛イメージ名｝[:｛タグ名｝]</span>には、Step14で作成したコンテナイメージを指定します。

$ `docker run -d -p 80:80 webserver-image:v1`{{execute}}  

**（表示例）**  
###### 67bcb99e625ac1b2f7193a27901b2ae61481ee9470bdea0a9c957d6ca8a39e08  
