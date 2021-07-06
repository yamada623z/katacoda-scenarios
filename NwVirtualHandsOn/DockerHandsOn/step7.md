# ステップ７:コンテナの停止（docker stop）
コマンド「docker stop friendly-name または container-id」は、実行中のコンテナを停止させます。停止したコンテナは、「docker ps -a」コマンドで停止（Exited）していることを確認できます。

$ docker stop <span style="color: red; ">friendly-name</span> または <span style="color: red; ">container-id</span>  
$ `docker ps -a`{{execute}}