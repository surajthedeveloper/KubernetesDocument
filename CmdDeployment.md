# Deploying application in Kubernetes using commandline

-   ```kubectl``` is the command line tool provided by kubernetes
-   **Deployment** is the component provided by Kuberenetes which is used for application deployment.
-   Deployment enables declarative updates for Pods and ReplicaSets
-   Docker hub repository provides the public images which we can use based on our need
-   Let's use hello-world image provided by docker for our testing 
-   Image details can be found here : https://hub.docker.com/_/hello-world?tab=tags
-   The command to create deployment for an application is ```kubectl create deployment <Deployment_Name> --image=<IMAGE_NAME>:<IMAGE_VERSION>```
    -   ```kubectl create deployment helloworld --image=hello-world:latest```
-   The command to list the deployments is ```kubectl get deployments```
-   Debugging in kubernetes might be tedious job, but kubernetes helps with a feature called **events** with which we can find what's happening inside kubernetes cluster.
-   command to list the events is ```kubectl get events``` 
-   If you want more details about the deployments then we could use the option **-o wide** as ```kubectl get deployments -o wide```
-   For detailed infomation about a perticular deployment we can use **discribe** option i.e, ```kubectl describe deployment <deployment_name```
    -   ```kubectl describe deployment helloworld```
-   As we know that deployment updates pods and replicasets, the creation of deployment should create pods and replicasets too.
-   The commad to list all pods is  ```kubectl get pods``` or ```kubectl get po``` 
-   The command to list all replicaset is ```kubectl get replicaset```  or ```kubectl get rs```
-   Each image is created to perform some task. Let's verify what does the **hello-world** image has performed.
-   As we know that image is deployed in to a container which is a part of POD in worker node.
-   Smallest deployable component in K8S is **pods**
-   So we can check the logs of pods to know what **hello-world** image has performed
-   command for checking logs in ```kubectl logs <pod_name>``` . You must see something like this
```
Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
```

-   command to delete the deployment is ```kubectl delete deployment <deployment_name>``` . This inturn deletes the pods and replicasets as well.
    -   ```kubectl delete deployment helloworld```