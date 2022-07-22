

## Kubernetes Objects
-   [Please refer this page for Kubernetes Objects](k8s-objects.md)

## Kubernetes API
-   The K8S API let's you query and manipulate the state of the objects in K8S.
-   The core of K8S control plain is the API Server and the HTTP API that it exposes.
-   



## Liveness and Readiness probes
-   Kubernetes uses probes to check the health of a microservice
-   If Readiness probe is not sucessful, no traffic is sent
-   If Liveness probe is not successful, pod is restarted
-   Spring boot Actuator (>=2.3) provides inbuilt readiness and liveness probes
    -   /health/readiness
    -   /health/liveness

CRDs ?

1. Pod creation
2. Replication Controller creation
3. 


https://console.cloud.google.com/getting-started?project=neon-coast-354711
gcloud config set project neon-coast-354711

https://www.gremlin.com/community/tutorials/how-to-create-a-kubernetes-cluster-on-ubuntu-16-04-with-kubeadm-and-weave-net/

https://github.com/rushtojp/devopsclassfiles
https://github.com/rushtojp/devopsclassfiles/blob/master/Kubernetes/Kubernetes%20Minikube%20Installation.txt
https://github.com/docker/awesome-compose

https://microservices-demo.github.io/deployment/kubernetes-start.html

https://github.com/rushtojp/devopsclassfiles/blob/master/Kubernetes/Setup%20cluster%20using%20minikube.txt

https://github.com/rushtojp/k8s-scripts

https://kubernetes.io/docs/tasks/run-application/

https://labs.play-with-k8s.com/

https://www.katacoda.com/courses/kubernetes/playground