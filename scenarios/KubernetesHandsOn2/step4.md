# コンテナイメージの作成  
**<span style="color: red; ">【masterノードで実施（Terminal Host 1）】</span>**  

①Topフォルダ（nginxphp）と作成するコンテナイメージ毎（nginx,php-fpm）にフォルダを作成します。  

$ `mkdir nginxphp`{{execute HOST1}}  
$ `mkdir nginxphp/nginx`{{execute HOST1}}  
$ `mkdir nginxphp/phpfpm`{{execute HOST1}}  

②nginxのコンテナイメージ作成に必要なファイルを移動します。  

$ `mv default.conf nginxphp/nginx`{{execute HOST1}}  

③php-fpmのコンテナイメージに必要なフォルダの作成し、ファイルを移動します。  

$ `mkdir nginxphp/phpfpm/php-fpm.d`{{execute HOST1}}  
$ `mv php.ini nginxphp/phpfpm/`{{execute HOST1}}  
$ `mv php-fpm.conf nginxphp/phpfpm/`{{execute HOST1}}  
$ `mv *.php nginxphp/phpfpm/`{{execute HOST1}}  
$ `mv www.conf nginxphp/phpfpm/php-fpm.d`{{execute HOST1}}  

④nginxのコンテナイメージを作成します。「Dockerfile」を作成して、コンテナイメージ「mynginx:1.0」を作成します。  

$ `cd nginxphp/nginx`{{execute HOST1}}  
$ `vi Dockerfile`{{execute HOST1}}  
```
FROM nginx
ADD default.conf /etc/nginx/conf.d
```{{copy}}
$ `sudo docker build -t mynginx:1.0 .`{{execute HOST1}}  

⑤php-fpmのコンテナイメージを作成します。「Dockerfile」を作成して、コンテナイメージ「myphpfpm:1.0」を作成します。  
  
$ `cd ../phpfpm`{{execute HOST1}}  
$ `vi Dockerfile`{{execute HOST1}}  
```
FROM php:7-fpm
ADD php.ini /usr/local/etc/php/php.ini
ADD php-fpm.conf /usr/local/etc/php-fpm.conf
ADD php-fpm.d /usr/local/etc/php-fpm.d
ADD index.php /var/www/html
ADD test.php /var/www/html
```{{copy}}
$ `sudo docker build -t myphpfpm:1.0 .`{{execute HOST1}}  
