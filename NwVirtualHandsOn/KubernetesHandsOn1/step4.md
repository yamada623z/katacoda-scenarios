# CNI（Contena Network Intarface）のインストール（masterノード）
<u>**<span style="color: red; ">※このステップは本レッスンでは必要ありません。</span>**</u>  

①**CNI（Contena Network Intarface）** のインストールのため、manifestファイル（yaml）のダウンロードを実施します。(今回はCNIに「weave」を使用します)  

$ `wget https://cloud.weave.works/k8s/v1.18/net.yaml`  

②CNIをkubernetesのクラスターにインストールします。  

$ `sudo kubectl apply -f ./net.yaml`