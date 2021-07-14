# CNI（Contena Network Intarface）のインストール
**<span style="color: red; ">【masterノードで実施（HOST 1）】</span>**  

①**CNI（Contena Network Intarface）** のインストールのためのYAMLファイルのダウン
ロードを実施します。(今回はCNIに「weave」を使用します)  

$ `wget https://cloud.weave.works/k8s/v1.14/net.yaml`{{execute HOST1}}  

②CNIをkubernetes上にインストールします。  

$ `sudo kubectl apply -f ./net.yaml`{{execute HOST1}}