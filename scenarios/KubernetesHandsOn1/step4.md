# CNI（Contena Network Intarface）のインストール
**<span style="color: red; ">（masterノードで実施（HOST 1））</span>**  

**CNI（Contena Network Intarface）** のインストールのためのYAMLファイルのダウン
ロードを実施します。(weaveの場合)  

$ `wget https://cloud.weave.works/k8s/v1.14/net.yaml`{{execute HOST1}}  

CNIをkubernetes上にインストールします。  

$ `sudo kubectl apply -f ./net.yaml`{{execute HOST1}}