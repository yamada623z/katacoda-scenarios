# クラスターのノード状態の確認（kubectl get nodes）
**<span style="color: red; ">【masterノードで実施（HOST 1）】</span>**  

①ノード状態を確認し、クラスターの正常性を確認します。  

\$ `kubectl get nodes`{{execute HOST1}}  

**（表示例）**  
```  
$ kubectl get nodes
NAME           STATUS   ROLES    AGE   VERSION
controlplane   Ready    master   84s   v1.14.0
node01         Ready    <none>   24s   v1.14.0
```  
