# ステップ７:コンテナの停止（docker stop）
マンド「docker stop \<friendly-name | container-id\>」は、実行中のコンテナを停止させます。停止したコンテナは、「docker ps -a」コマンドで停止（Exited）していることを確認できます。

$ docker stop *<span style="color: red; ">\<friendly-name | container-id\></span>*  
$ `docker ps -a`{{execute}}