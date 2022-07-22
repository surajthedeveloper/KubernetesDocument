# Kubernetes Namespaces

-   Organise resources in namespaces
-   You can consider namespace as a virtual cluster inside a cluster
-   In Kubernetes, namespaces provides a mechanism for isolating groups of resources within a single cluster
-   Names of resources need to be unique within a namespace, but not across namespaces
-   Namespace-based scoping is applicable only for namespaced objects (e.g. Deployments, Services, etc) and not for cluster-wide objects (e.g. StorageClass, Nodes, PersistentVolumes, etc).

-   command to list the namespaces is : 
    -   ```kubectl get namespace```

        ```
            default                Active   7d21h
            kube-node-lease        Active   7d21h
            kube-public            Active   7d21h
            kube-system            Active   7d21h
        ```
-   By default kubernetes cluster creates 4 namespaces
    -   **default**
        -   The default namespace for objects with no other namespace
        -   resources you create are located here
    -   **kube-node-lease**
        -   This namespace holds Lease objects associated with each node. 
        -   Node leases allow the kubelet to send heartbeats so that the control plane can detect node failure
    -   **kube-public**
        -   This namespace is created automatically and is readable by all users (including those not authenticated). 
        -   This namespace is mostly reserved for cluster usage, in case that some resources should be visible and readable publicly throughout the whole cluster. 
        -   The public aspect of this namespace is only a convention, not a requirement.
        -   Publicely accessible data
        -   A configmap which contains cluster information
    -   **kube-system**
        -   The namespace for objects created by the Kubernetes system
        -   Do not create or modify in kube-system

-   By defaults the components are created in default namespace if not specified one.

-   you can specify the namespace in ```metadata``` section of YAML file.

-   If you are creating component using command line then you can use the option ```--namespace=<namespace name>``` to create components within namespace provided.

-   You can retrieve the components created in specific namespace using the option ```-n <namespace name>``` in ```kubectl get ``` command

-   You can create namespace by following command i.e ```kubectl create namespace <namespace_name>```

-   You can get the namespace by following command i.e ```kubectl get namespace <namespace_name>```

-   Namespaces can be used for
    -   Structure your components (Separating the resources based on team, landscape etc)
    -   Avoid conflicts between teams
    -   Share services between different environment
    -   For deploying common resources used by more multiple applications (Ex. ELK stack deployed in one namespace can be used by Staging and Production landscape)
    -   Access and resource limits on namespace level

-   you can't access most resources from another namespaces
    -   ConfigMap created in one namespace can't be used in another namespace
    -   Secret created in one namespace can't be used in another namespace

-   Service of one namespace can be used by components of another service

-   Some of the components in kubernetes are not namespaced. Which lives globally in a cluster. You can't isolate them. ex Volume, Node etc

-   You can list all the resources that are not bound to namespaces by following command ```kubectl api-resources --namespaced=false```

-   You can list all the resources that are bound to namespaces by following command ```kubectl api-resources --namespaced=true```

-   When you create a Service, it creates a corresponding DNS entry. This entry is of the form <service-name>.<namespace-name>.svc.cluster.local, which means that if a container only uses <service-name>


-   you can change the active namepace in kubernetes using an another tool called ```kubens```
    -   Install a tool called ```kubectx```
    -   ```kubens <namespace name>``` will set namespace provided as active one
    -   This helps to avoid passing ```-n <namespace>``` in kubectl command


## commands
- ```kubectl get namespaces```
- ```kubectl create namespace <namespace_name>```
- ```kubectl get namespace <namespace_name>```
- ```kubectl get namespace <namespace_name> -o yaml```
- ```kubectl delete namespace <namespace_name>```

## YAML configuration
-   Create a file named Namespace.yaml and paste the content mentioned below. and provide the right input for ```<namespace_name>```.
```aidl
apiVersion: v1
kind: Namespace
metadata:
  name: <namespace_name>
```
- ```kubectl apply -f Namespace.yaml```
- ```kubectl get namespaces```
- ```kubectl delete -f Namespace.yaml```