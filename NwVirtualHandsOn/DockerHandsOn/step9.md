# イメージの削除（docker rmi）
Dockerホストマシンにダウンロードされたイメージは、コマンド「**docker images**」で確認することができます。  

$ `docker images`{{execute}}  

必要のないDockerイメージはDockerホストマシンから削除することができます。  
コマンドは「**docker rmi** <span style="color: red; ">image-name</span> または <span style="color: red; ">image-id</span>」です。  
<span style="color: red; ">image-name</span>はリポジトリ名とタグの組み合わせです。  
<span style="color: red; ">image-id</span>は「**docker images**」で確認することができます。  

$ `docker rmi nginx`{{execute}}  

DockerイメージがDockerホストマシンから削除されたことを確認します。  

$ `docker images`{{execute}}  
