# ステップ８:コンテナの削除（docker rm）
停止しているコンテナを削除するためには「docker rm \<friendly-name | container-id\>」を使用します。削除したコンテナは、「docker ps -a」コマンドで削除（表示されない）されたことを確認できます。

$ docker rm *<span style="color: red; ">\<friendly-name | container-id\></span>*  
$ `docker ps -a`{{execute}}