# ステップ４:コンテナ状態の確認（docker ps）
「docker ps」コマンドは、実行中のすべてのコンテナ、コンテナの開始に使用されたイメージ、および稼働時間を一覧表示します。このコマンドは、個々のコンテナに関する情報を見つけるために使用できるコンテナID（container-id）とフレンドリ名（friendly-name）も表示します。

$ `docker ps`{{execute}}

*（表示例）*  
*CONTAINER ID &emsp; IMAGE &emsp; COMMAND &emsp; CREATED &emsp; STATUS &emsp; PORTS &emsp; NAMES*  
*<span style="color: red; ">d6ae8a871e8f</span> &emsp; nginx &emsp; "/docker-entrypoint.…" &emsp; 3 minutes ago &emsp; Up 3 minutes &emsp; 80/tcp &emsp; <span style="color: red; ">elegant_thompson</span>*  

*（説明）*  
「*<span style="color: red; ">d6ae8a871e8f</span>*」は *コンテナID（container-id）* です。  
「*<span style="color: red; ">elegant_thompson</span>*」は *フレンドリ名（friendly-name）* です。