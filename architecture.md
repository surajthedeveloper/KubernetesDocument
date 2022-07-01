# Kubernetes Architecture

## Master Node(s)
-   Most important components of master nodes are:
    -   API Server  (**kube-apiserver**)
    -   Distribute Database (**etcd**)
    -   Scheduler (**kube-scheduler**)
    -   Controller Manager (**kube-controller-manager**)


## Worker Node(s)
-   Most important components of worker nodes are:
    -   Node Agent (**kubelet**)
    -   Networking component (**kube-proxy**)
    -   Container Runtime (**CRI - docker,rkt ect**)
    -   Pods (**Multiple pods running containers**)


## Questions
-   What happens if the master node goes down ? will the entire application is down ?
    -   Ans : No. The applications can continue run working even with master node down. Because while we access the application url the master node doesnot get involved at all.

 