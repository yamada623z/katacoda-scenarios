# kubeadmのインストール（masterノード（controlplane））  
<u>**<span style="color: red; ">※このステップは本レッスンでは必要ありません。</span>**</u>  

**<span style="color: red; ">【masterノード（controlplane）で実施】</span>**  

⑥apt-transport-httpsのインストールは念のため実施します。  

\# `apt update && apt install -y apt-transport-https`  

⑦kubernetes のキーとリポジトリを登録します。  

\# `curl -s https://packages.cloud.google.com/apt/doc/aptkey.gpg | apt-key add -`  
\# `apt-add-repository “deb http://apt.kubernetes.io/kubernetes-xenial main"`  

⑧スワップをオフにします。  
<span style="color: red; ">※恒久的にswapoffにする必要あります。（/etc/fstabのswap行をコメントアウトします）</span>  

\# `swapoff -a`  

⑨**kubeadm**をインストールします。  

\# `apt update`  
\# `apt install -y kubeadm`