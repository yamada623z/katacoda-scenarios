# ステップ９:イメージの削除（docker rmi）
Dockerホストマシンにダウンロードされたイメージは、コマンド「docker images」で確認することができます。  

$ `docker images`{{execute}}  

必要のないDockerイメージはDockerホストマシンから削除することができます。  
コマンドは「docker rmi \<image-name\> | \<image-id\>」です。  
*<span style="color: red; ">\<image-name\></span>はリポジトリ名とタグの組み合わせです。  
*<span style="color: red; ">\<image-id\></span>は「docker images」で確認することができます。

$ docker rmi *<span style="color: red; ">\<image-name | image-id\></span>*  

DockerイメージがDockerホストマシンから削除されたことを確認します。  

$ `docker images`{{execute}}  