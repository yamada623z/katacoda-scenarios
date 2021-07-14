# ロードバランサー機能の実装
<u>**<span style="color: red; ">※このステップは本レッスンでは必要ありません。</span>**</u>

本レッスンでは必要ありませんが、ロードバランサー機能はパブリッククラウドには標準で実装されていますが、オンプレミスでは下記のように機能を追加して実装します。

**<span style="color: red; ">【masterノードで実施（HOST 1）】</span>**  

①rootにユーザを切り替えます。  

\# `sudo -s`  

②ロードバランサー機能（MetalLB）のインストールします。  

\# `kubectl apply -f https://raw.githubusercontent.com/google/metallb/v0.8.3/manifests/metallb.yaml`

③ConfigMapファイル（設定を記述します）の作成します。  

\# `vi metallb_conf.yaml`
```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  namespace: metallb-system
  name: config
data:
  config: |
    address-pools:
    - name: default
      protocol: layer2
      addresses:
      - xxx.xxx.xxx.xxx-xxx.xxx.xxx.xxx
```  
末尾の行は環境に沿った値で設定します。（開始IPアドレス-終了IPアドレス）  

④ConfigMapファイルのインストールします。  

\# `kubectl apply -f metallb_conf.yaml`  

