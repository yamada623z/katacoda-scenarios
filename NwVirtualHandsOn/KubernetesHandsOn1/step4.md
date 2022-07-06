# CNI（Contena Network Intarface）のインストール
**<span style="color: red; ">【masterノード（controlplane）で実施】</span>**  

①**CNI（Contena Network Intarface）** のインストールのため、manifestファイル（yaml）のダウンロードを実施します。(今回はCNIに「weave」を使用します)  

$ `wget https://cloud.weave.works/k8s/v1.18/net.yaml`{{execute}}  

②CNIをkubernetesのクラスターにインストールします。  

$ `sudo kubectl apply -f ./net.yaml`{{execute}}