# CNI（Contena Network Intarface）のインストール
**<span style="color: red; ">【masterノードで実施（Terminal Host 1）】</span>**  

①**CNI（Contena Network Intarface）** のインストールのためのファイルのmanifestダウンロード（yaml）を実施します。(今回はCNIに「weave」を使用します)  

$ `wget https://cloud.weave.works/k8s/v1.18/net.yaml`{{execute HOST1}}  

②CNIをkubernetesのクラスターにインストールします。  

$ `sudo kubectl apply -f ./net.yaml`{{execute HOST1}}