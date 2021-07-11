# クラスターの生成（kubeadm init）
**<span style="color: red; ">（masterノードで実施（HOST 1））</span>**  

kubernetesの構築を行います。
（使用するCNIによって「--pod-network-cidr」の指定が必要です。）  

\# `kubeadm init`{{execute HOST1}}  

**（以下はkubeadm init実行後の表示例）**
```
Your Kubernetes master has initialized successfully!
```
*「Kubernetesマスターが正常に初期化されました！」*  
```
 To start using your cluster, you need to run the following as a regular user:
 ```
 *「クラスターの使用を開始するには、通常のユーザーとして次を実行する必要があります。」*
 ```
    mkdir -p $HOME/.kube
    sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
    sudo chown $(id -u):$(id -g) $HOME/.kube/config
```
<span style="color: red; ">**※1 上記を実際に表示通りに実行します。**</span>  
```
 You should now deploy a pod network to the cluster.↲
 Run "kubectl apply -f [podnetwork].yaml" with one of the options listed
    https://kubernetes.io/docs/concepts/clusteradministration/addons/
```
*「ここで、ポッドネットワークをクラスターにデプロイする必要があります」*   
※2 CNI（Contena Network Intarface）のインストールします（Step4で実施）  
```
You can now join any number of machines by running the following on each node
as root:
```
*「各ノードで次を実行することで、任意の数のマシンに参加できるようになりました。」「ルートで：」*  
※workerノードを追加する際には、下記の**kubeadm join**を実施します。
```
kubeadm join 10.40.x.10:6443 --token
xxxxxx.xxxxxxxxxxxxx --discovery-token-ca-cert-hash sha256:xxxxxxx
```  
<span style="color: red; ">**※1を実行します。**</span>  

$ `mkdir -p $HOME/.kube`{{execute HOST1}}  

$ `sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config`{{execute HOST1}}  

$ `sudo chown $(id -u):$(id -g) $HOME/.kube/config`{{execute HOST1}}  

