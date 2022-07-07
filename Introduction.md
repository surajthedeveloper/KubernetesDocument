
## What is Kubernetes ?
-   Kubernetes is an open source container orchestration engine for automated deployment, scaling and management of containerized application.
-   Kubernetes is a portable, extensible, open source platform for managing containerzed workloads and services, that facilitates both declarative configuration and automation.

## Advantages/Features of Kubernetes
-   Service Discovery and Load balancing
    -   Kubernetes can expose a container using a DNS name or using their own IP address
    -   If traffic to a container is high, kubernetes is able to load balance and distribute the network traffic so that the deployment is stable.
-   Storage orchestration
    -   K8S allows you to automatically mount a storage system of your choice, such as local storage, public cloud provider and more.
-   Automated rollouts and rollbacks 
    -   You can describe the desired state for your deployed containers using K8S, and it can change the actual state to desired state at a controlled rate.
-   Automated bin packing
    -   You provide K8S with a cluster of nodes that it can use to run containerized tasks.
    -   You tell K8S how much memory(RAM) and CPU each container needs.
    -   K8S can fit containers onto your nodes to make the best use of your resources.
-   Self-Healing
    -   K8S restarts containers that fail, replaces containers, kill container that doesn't respond to your user-defined health check and doesn't advise them to clients until they are ready to use.
-   Secret and configuration management
    -   K8S lets you store and manage sensitive information, such as passwords, OAuth tokens and SSH Keys.
    -   You can deploy and update secrets and application configuration without rebuilding your container images, and without exposing secrets in your stack configuration.

## Kubernetes components
-   [Please refer this page for Kubernetes components](components.md)

## Kubernetes Architecture
-   [Please refer this page for Kubernetes Architecture](architecture.md)

## Kubernetes Objects
-   [Please refer this page for Kubernetes Objects](k8s-objects.md)

## Kubernetes API
-   The K8S API let's you query and manipulate the state of the objects in K8S.
-   The core of K8S control plain is the API Server and the HTTP API that it exposes.
-   

### ReplicaSet
-   ReplicaSet ensures that a specified number of pod replica are running at any given times

## Deployment
-   Deployment enables declarative updates for Pods and ReplicaSets
-   The strategy the Deployment is using by default is something called rolling update 

## Service
-   Service is a named abstraction of software service consisting of local port that the proxy listens on, and the selector that determines which pods will answer requests sent through the proxy.

## ConfigMap
-   ConfigMap holds the configuration data for pods to consume.
-   

## Liveness and Readiness probes
-   Kubernetes uses probes to check the health of a microservice
-   If Readiness probe is not sucessful, no traffic is sent
-   If Liveness probe is not successful, pod is restarted
-   Spring boot Actuator (>=2.3) provides inbuilt readiness and liveness probes
    -   /health/readiness
    -   /health/liveness

## References
-   https://kubernetes.io/docs
-   

# Kubernetes 

# Options to use Kubernetes
-   Online Kubernetes Labs
    -   https://www.katacoda.com/courses/kubernetes/playground
    -   https://labs.play-with-k8s.com/
    -   https://training.play-with-kubernetes.com/
    -   https://cloudacademy.com/lab/introduction-kubernetes-playground/
-   Kubernetes installation tools
    -   Minikube
    -   Kubeadm
-   Cloud based Kubernetes Services
    -   GKE -   Google Kubernetes Engine
    -   AKS -   Azure Kubernetes Service
    -   Amazon EKS - Amazon Elastic Kubernetes service
    
# Kubernetes Commands
-   To launch kubernetes cluster
    ```launch.sh```

-   To get the Kubernetes cluster-info (Health status)
    ```kubectl cluster-info```
    
-   To get the complete cluster info
    ```kubectl cluster-info dump```
    
-   To list all the nodes
    ```kubectl get nodes```
    
What is cron Job ?
What is Deamon set ?
How does communication between pods and services take place ?
Storage classes ?
Namespace ?
PersistentVolumes ?



https://console.cloud.google.com/getting-started?project=neon-coast-354711
gcloud config set project neon-coast-354711
