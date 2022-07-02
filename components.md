# Kubernetes Components

-   When you deploy K8S you get a cluster
-   Kubernetes uses single responsibility principle, so each component of K8S is responsible only for one responsibility

## Master Node(s) / Control Plain
-   Most important components of master nodes are:
    -   API Server  (**kube-apiserver**)
        -   The API server is a component of the K8S control plain that exposes the K8S API.
        -   The API server is front end for K8S control plain.
    -   Distribute Database (**etcd**)
        -   Consitent and highly available key value store used as K8S backing store for all cluster data.
    -   Scheduler (**kube-scheduler**)
        -   Kube scheduler component that watches for newly created Pods with no assigned node and selects a node for them to run on.
    -   Controller Manager (**kube-controller-manager**)
        -   The control plain components run controller processes
        -   Logically each controller is a separate process, but to reduce complexity, they are all compiled into a single binary and run in a single process.
        -   Some of the controllers are:
            -   Node controller
                -   Responsible for noticing and responding when nodes go down
            -   Job controller
                -   watches for job objects that represent one-off tasks, then creates pods to run those tasks to completion.
            -   Endpoints controller
                -   Polulates the endpoints objects(that is,joins Services and Pods)
            -   Service account and Token controller
                -   Create default accounts and API access tokens for new namespaces
-   The control plain or master node(s) manages the worker nodes and the pods in the cluster.

## Worker Node(s)
-   K8S cluster consists of set of worker machines called nodes, that run the containerized application.
-   Every cluster has atleast one worker node.
-   Most important components of worker nodes are:
    -   Node Agent (**kubelet**)
        -   An agent that runs on each node in the cluster. It make sure that containers are running in a pod.
        -   Kubelet takes a set of PodSpecs that are provided through various mechanisms and ensures that the containers described in those PodSpecs are running and healthy.
        -   Kubelet doesnot manage containers which are not created by K8S
    -   Networking component (**kube-proxy**)
        -   Kube-proxy is a network proxy that runs on each node in your cluster, implementing pasrt of the kubernetes Service concept.
        -   kube-proxy maintains network rules on nodes. these network rules allow network communication to your pods from network sessions inside or outside of your cluster.
    -   Container Runtime (**CRI - docker,rkt ect**)
        -   The container runtime is a software that is responsible for running containers
    -   Pods (**Multiple pods running containers**)
-   The worker node(s) hosts the **pods** that are the components of the application workload.

## Addons
-   Addons uses K8S resources to implement cluster feature,because these are proving cluster level features, namespaced resource for addons belonging within the **kube-system** namespace.
-   DNS
    -   Cluster DNS is a DNS Server, in addition to the other DNS Server(s) in your environment, which serves DNS records for K8S services.
    -   Containers started by K8S automatically include this DNS server in their DNS Searches.

-   Web UI (dashboard)
    -   Dashboard is a general purpose, web-based UI for K8S cluster
    -   It allows users to manage and trobleshoot applications running in the cluster, as well as the cluster itself.

-   Container resource monitoring
    -   container resource monitoring records generic time-series metric about containers in a central database, and provides a UI for browsing that data.

-   Cluster-level logging
    -   A cluster level logging mechanisum is responsible for saving container logs to a central log store with search/browsing interface.
