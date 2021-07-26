# Dockerホストの視覚化  
Weave Scopeコンテナが起動すると、ポート4040でUIにアクセスできます。

https://localhost:4040

**KatacodaのWebアクセス方法：**  
①ターミナルペインの「**Terminal Host 1**」のタグの隣の「**＋**」をクリックします。  
②表示されるドロップリストから「**Select port to view on Host 1**」をクリックします。  
③ボックスに「**4040**」を入力し、「**Display Port**」をクリックします。 

**（表示例）**
![Scope farst](./assets/Step13-1.png)   

<br>

新しいコンテナーが起動されると、Scopeはライブアーキテクチャ（リアルタイムな機能仕様）を反映するように自動的に更新されます。

\# `docker run -d --link redis:redis katacoda/redis-node-docker-example`{{execute}}

追加のフロントエンドコンテナを起動して結果を確認してください。  

**（表示例）**  
![Scope container plus](./assets/Step13-2.png)   
