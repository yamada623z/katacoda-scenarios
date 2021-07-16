# dockerイメージのプライベートレジストリへの登録

**<span style="color: red; ">【masterノードで実施（Terminal Host 1）】</span>**  

Podの作成に必要なコンテナイメージをプライベートレジストリにpushします。
<br>

①コンテナイメージの名前を変更します。（「xxx.xxx.xxx.xxx」はregistryノードのIPアドレスを指定します）  

$ `docker tag mynginx:1.0 xxx.xxx.xxx.xxx:5000/mynginx:1.0`  
$ `docker tag myphpfpm:1.0 xxx.xxx.xxx.xxx:5000/myphpfpm:1.0`  

②コンテナイメージをレジストリにpushします。  

$ `docker push xxx.xxx.xxx.xxx:5000/mynginx:1.0`  
$ `docker push xxx.xxx.xxx.xxx:5000/myphpfpm:1.0`  
