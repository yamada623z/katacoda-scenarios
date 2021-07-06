# ステップ17：コンテナの動作確認
コンテナの動作確認として「curl docker」を実行します。ステップ12で作成した「index.html」の内容が表示されます。    

$ `curl docker`{{execute}}  
<br>
（表示例）  
```<h1>Hello World</h1>```

実ノードであれば、「curl localhost:80」で確認することが可能ですが、Katacodaのネットワークの構造上、不可となります。  

KatacodaのWebアクセス方法：  
①ターミナルペインの「Terminal」のタグの隣の「＋」をクリックする。  
②表示されるドロップリストから「View HTTP port 80 on Host 1」をクリックする。