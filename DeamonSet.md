## Kubernetes DeamonSet

-   DeamonSet is a controller in Kubernetes
-   A DeamonSet ensures that all nodes run a copy of a Pod
-   Usecases
    -   Running a logs collection deamon on every node
    -   Running a cluster storage deamon on every node
    -   Running a node monitoring deamon on every node
-   DeamonSet configuration looks like this
```
apiVersion: apps/v1
kind: DeamonSet
metadata:
  name: <deamon-set-name>
spec:
  selector:
    matchLabels:
      <label>: <value>
  template:
    metadata:
      labels:
        <label>: <value>
    spec:
      tolerations:
      - key: node-role.kubernetes.io/master
        effect: NoSchedule
      containers:
      - image: <image-name>
        ports:
        - containerPort: <port-number>  
```
-   By default the DeamonSet runs on worker nodes. incase if we wish to run it along with master node we might need to configure it explicitly. as defined in ```spec.template.spec.tolerations```
-   To know the deamon sets in cluster use the following command ```kubectl get deamonset``` or ```kubectl get ds``` 
-   DeamonSet results on Pods. To know pods running in which node using command. ```kubectl get pods -o wide```