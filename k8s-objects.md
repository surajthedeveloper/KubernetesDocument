## Kubernetes Objects
-   Kubernetes objects are persistent entities in the K8S system.
-   To work with K8S objects, whether to create,modify or delete them you will need to use the Kubernetes API.
-   When you create an object in Kubernetes, you must provide the object ```spec``` that describes its desired state, as well as some basic information about the object (such as a name)

### Required fields in yaml file
-   **apiVersion**
    -   Which version of the Kubernetes API you're using to create this object
-   **kind**
    -   What kind of object you want to create
-   **metadata**
    -   Data that helps uniquely identify the object, including a name string, UID, and optional namespace
-   **spec**
    -   What state you desire for the object

### Object Names and IDs
-   Each object in your cluster has a Name that is unique for that type of resource. 
-   Every Kubernetes object also has a UID that is unique across your whole cluster.
-   Names
    -   A client-provided string that refers to an object in a resource URL, such as /api/v1/pods/some-name.
-   UID
    -   A Kubernetes systems-generated string to uniquely identify objects.
    
### Namespace
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

-   K8S starts with 4 initial namespaces
    -   **default**
        -   The default namespace for objects with no other namespace
    -   **kube-node-lease**
        -   This namespace holds Lease objects associated with each node. Node leases allow the kubelet to send heartbeats so that the control plane can detect node failure
    -   **kube-public**
        -   This namespace is created automatically and is readable by all users (including those not authenticated). This namespace is mostly reserved for cluster usage, in case that some resources should be visible and readable publicly throughout the whole cluster. The public aspect of this namespace is only a convention, not a requirement.
    -   **kube-system**
        -   The namespace for objects created by the Kubernetes system

-   When you create a Service, it creates a corresponding DNS entry. This entry is of the form <service-name>.<namespace-name>.svc.cluster.local, which means that if a container only uses <service-name>

### Labels and Selectors
-   Labels are key/value pairs that are attached to objects, such as pods.
-   Labels can be attached to objects at creation time and subsequently added and modified at any time. 
-   Each object can have a set of key/value labels defined. 
-   Each Key must be unique for a given object.
-   Unlike names and UIDs, labels do not provide uniqueness. In general, we expect many objects to carry the same label(s).
-   Via a label selector, the client/user can identify a set of objects. The label selector is the core grouping primitive in Kubernetes.

### Annotations
-   You can use Kubernetes annotations to attach arbitrary non-identifying metadata to objects
-   You can use either labels or annotations to attach metadata to Kubernetes objects
-   The keys and the values in the map must be strings

### Field Selectors
-   Field selectors let you select Kubernetes resources based on the value of one or more resource fields

```kubectl get pods --field-selector status.phase=Running```

-   Field selectors are essentially resource filters
