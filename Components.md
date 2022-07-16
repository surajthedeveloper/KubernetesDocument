# Kubernetes Components

## Pod
-   pod is a collection of containers that can run on a host.- pod is an abstraction over container
-   Pod is the smallest deployable unit in K8S
-   Container lives inside a pod
-   Each pod gets a unique IP address
-   containers in a pod share resources
-   with in a pod container can talk to each other using localhost
-   Usually one application per pod

## Service
-   Service is a permanent IP address
-   Lifecycle of Pod and Service is not connected
-   Service is a named abstraction of software service consisting of local port that the proxy listens on, and the selector that determines which pods will answer requests sent through the proxy.
-   Service is also Load Balancer
-   Service Types
    -   Cluster IP
        -   Default type
        -   Internal Service
        -   
    -   NodePort
        -   External traffic has access to fixed port on each worker node
        -   nodeport value ranges from 30000 to 32767
        -   Not secured as the ip is exposed outside 
        -   ClusterIp is created automatically
        -   Nodeport service is an extension of ClusterIP Service 
        -   Not used in production
    -   LoadBalancer
        -   Nodeport and ClusterIp is created automatically
        -   LoadBalancer service is an extension of NodePort Service
    -   Headless
        -   

## Ingress
-   Ingress helps to route traffic into cluster
-   Service is a permanent IP address. 
-   Client expects something like http://my-app.com instead of http://12.10.123.56:8080
-   Ingress helps to achieve this

## ConfigMap
-   ConfigMap holds the external configuration of your application.
-   ConfigMap should be connected to pod in order for pod to get the configuration

## Secrets
-   Secret is similar to ConfigMap but used to store secret data
-   Data is stored in base64 encoded format instead of storing it in plain text format
-   Secret should be connected to pod in order for pod to get the configuration

## Volumes
-   Kubernetes component considered as an External harddrive for the pod
-   Kubernetes doesnot manage data persistance, k8s administrator should be responsible for backing up the data,replicating and managing and making sure that its kept in proper hardware etc

## Deployment
-   blue print for our application pod
-   Deployment is an abstraction of pods
-   Deployment enables declarative updates for Pods and ReplicaSets
-   The strategy the Deployment is using by default is something called rolling update 
-   Deployment for stateless applications

## StatefulSet
-   StatefulSet is used for stateful applications such as database pods
-   StatefulSet for DB is hard to configure so usually DB's are aften hosted outside of k8s cluster
-   Stateful applications are deployed using StatefulSet component
-   Replicating stateful applications is more difficult
-   In StatefulSet replication i.e in scale up, next pod is created if previous pod is up and running.
-   In StatefulSet replication i.e in scale down, deletion is reverse order, starting from last one.
-   Each pod gets the individual DNS name (in case of deployment it's not present)
-   **Stateful applications are not prefect for containerized environments**
-   

## ReplicaSet
-   ReplicaSet ensures that a specified number of pod replica are running at any given times
-   ReplicaSet is used for stateless applications