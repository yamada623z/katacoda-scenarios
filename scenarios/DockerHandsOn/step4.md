# コンテナ状態の確認（docker ps）
「**docker ps**」コマンドは、実行中のすべてのコンテナ、コンテナの開始に使用されたイメージ、および稼働時間を一覧表示します。このコマンドは、個々のコンテナに関する情報を見つけるために使用できる<span style="color: red; ">コンテナID（container-id）</span>と<span style="color: red; ">フレンドリ名（friendly-name）</span>も表示します。  

$ `docker ps`{{execute}}  

**（表示例）**  
```
CONTAINER ID	IMAGE	COMMAND			CREATED		STATUS		PORTS	NAMES  
d6ae8a871e8f	nginx	"/docker-entrypoint.…" 3 minutes ago	Up 3 minutes	80/tcp	elegant_thompson
```
**（説明）**  

「<span style="color: red; ">d6ae8a871e8f</span>」は コンテナID（container-id） です。  
「<span style="color: red; ">elegant_thompson</span>」は フレンドリ名（friendly-name） です。  
