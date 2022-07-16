## Minikube setup in local machine

### Options to use Kubernetes
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

### Minikube
-   minikube is local Kubernetes, focusing on making it easy to learn and develop for Kubernetes.
-   All you need is Docker (or similarly compatible) container or a Virtual Machine environment, and Kubernetes is a single command away i.e, ```minikube start```

-   Installation steps and prerequisite for Linux, Windows and Mac can be found [here](https://minikube.sigs.k8s.io/docs/start/)
-   You can manage your cluster using following commands
    -   In order to start the cluster ```minikube start```
    -   In order to pause the cluster ```minikube pause```
    -   In order to unpause the cluster ```minikube unpause```
    -   In order to stop the cluster ```minikube stop```
    -   In order to delete all minikube clusters ```minikube delete --all```
-   Inorder to use the kubernetes dashboard (UI) provided by minikube use the following command ```minikube dashboard```
    -   **Note: Open a new terminal and run the above command**


### Recommended/Prerequisites steps to start using kubectl
-   ```minikube start``` to start the minikube k8s cluster
-   ```kubectl version --short``` to verify the minikube installation
-   ```kubectl dashboard``` for the kubernetes dashboard
-   We might need to do some additional steps and configuration in minikube to get the same same feeling as we get in any cloud providers
    -   ```minikube tunnel``` in a new terminal, which helps in LoadBalancer deployment. (This step we are doing it only in local minikube cluster)
    -   ```kubectl create secret docker-registry <Name_for_the_secret> --docker-server=<docker_registry> --docker-username=<username> --docker-password=<password>``` this will help us to pull the images from our private repository. 

