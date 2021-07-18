# ＜今回の目標＞
## 【Pod（アプリケーション）作成】  
- kubernetes上に静的WebサービスのPodを作成する。  
- Podの動作確認を実施する。  
- kubernetesの動作確認を実施する。（セルフヒーリング、ロードバランス）   

<span style="color: red; ">※Katacoda利用のハンズオンの場合、必ずブラウザはChromeを使用すること。</span>  
<br>

## 【Pod作成イメージ】  

![Pod Image](./assets/PodImage.png)  

- kubernetesのクラスター上のPodにはnginxとphp-fpmのコンテナと２つで構成されている。  
    - nginx：静的Webサービス（webサーバー）
    - php-fpm：PHP（動的にWebページを生成することができるスクリプト言語）のFastCGI実装のひとつ。FastCGIはWebサーバー上でユーザープログラムを動作させる仕様のひとつです。  
- ユーザーが外部アドレス（xxx.xxx.xxx.xx:31001）にブラウザ等からアクセスするとサービス（nginx-service）を介して、nginxにアクセスします。  
    - ページが「\*.html」の場合はnginxで処理し、応答を返します。  
    - ページが「\*.php」の場合はnginxからphp-fpmに処理を依頼し、その応答をnginxからユーザに返します。  
