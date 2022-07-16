# Kubernetes YAML configuration

-   The format of configuration file ```YAML```
-   Each configuration in kubernetes has 5 parts
    -   ```apiVersion```
    -   ```kind```
    -   ```metadata```
    -   specification - ```spec```
    -   ```status```
    ```
        apiVersion: # Holds the version that kubernetes provides for each kind
        kind:       # type of component
        metadata:   # metadata information for the component
        spec:       # attributes specific to kind
        status:     # Maintained by Kubernetes to manage desired state and actual state
    ```
-   **apiVersion**
    -   apiVersion indicates the specification that kubernetes should follow during configuration handling.
-   **kind**
    -   Holds the type of component that is being created
-   **metadata**
    -   one of the metadata is ```name``` of the component
-   **specification**
    -   specification holds the configuration specific to the component
    -   attributes of ```spec``` are specific to the ```kind```
-   **status**
    -   automatically generated and added by kubernetes
    -   K8S always checks the desired state and actual state of a component. If the desired state and actual state do not match, then k8s knows something needs to be fixed so k8s will try to fix it.
    -   This is the base for self healing feature that kubernetes provides
    -   k8s updates the status of an component continuously
    -   ```etcd``` holds the current status of any k8s component.

## Deployment and Service
-   Connecting components Labels, Selectors and Ports
-   The way the connection is established using Labels and Selectors
    -   ```metadata``` part contains ```labels```
    -   ```spec``` contains the ```selector``` 
-   Connecting Deployment to Pod. 
    -   Pod get the label through the template blueprint. This label is matched by the selector
    -   ```spec.selector.matchLabels``` == ```spec.template.metadata.labels```
    ```
      spec:
        selector:
          matchLabels:
            app: my-app         ## used to establish connection between deployment and pod
        template:
          metadata:
            labels:
              app: my-app      ## used to establish connection between deployment and pod
    ```
-   Connecting Service to Deployment
    -   ```deployment.metadata.labels``` == ```deployment.spec.template.metadata.labels``` == ```service.spec.selector```
    -   ```deployment.spec.template.spec.containers.*.ports.*.containerPort``` == ```service.spec.ports.*.targetPort```
    ```
    apiVersion: apps/v1
    kind: Deployment
    metadata:
      labels:
        app: my-app             ## used to establish connection between deployment and service
    spec:
      template:
        metadata:
          labels:
            app: my-app      ## used to establish connection between deployment and service
        spec:
          containers:
          - ports:
            - containerPort: 8080  ## used to establish connection between deployment and service
    ---
    apiVersion: v1
    kind: Service
    metadata:
      name: my-app-service
    spec:
      selector:
        app: my-app             ## used to establish connection between deployment and service
      ports:
        - protocol: TCP
          port: 80              ## Service port that we can connect to
          targetPort: 8080      ## used to establish connection between deployment and service
    ```

## 
-   