# コンテナの削除（docker rm）
停止しているコンテナを削除するためには「**docker rm** <span style="color: red; ">friendly-name</span> または <span style="color: red; ">container-id</span>」を使用します。削除したコンテナは、「**docker ps -a**」コマンドで削除（表示されない）されたことを確認できます。

（下記に習って入力してください。）  

$ **docker rm** <span style="color: red; ">friendly-name</span> または <span style="color: red; ">container-id</span>  

$ `docker ps -a`{{execute}}
