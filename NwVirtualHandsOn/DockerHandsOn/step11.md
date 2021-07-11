# コンテナ上でのシェル実行（docker run -it）
「<span style="color: red; ">-i</span>」フラグはコンテナ内で標準出力を介してインタラクティブに操作することを許すオプションです。「<span style="color: red; ">-t</span>」フラグはコンテナ内で擬似ターミナルまたはターミナルを割り当てるオプションです。  
このコマンドの書式ではコンテナ内の「/bin/bash」を実行するように指定しています。この結果Bashシェルがコンテナ内で立ち上がります。  (コンテナ内のシェルから復帰する場合は「**exit**」を入力します。)

$ `docker run -it ubuntu /bin/bash`{{execute}}  

**（表示例）**  
```
root@5bde6b629564:/#
root@5bde6b629564:/# exit
exit
$
```