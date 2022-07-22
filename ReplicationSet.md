## ReplicationSet

-   ReplicaSet is the next-generation ReplicationController that supports the new set-based label selector.
-   It's mainly used by Deployment as a mechanism to orchestrate pod creation, deletion and updates
-   Note that we recommend using Deployments instead of directly using Replica Sets, unless you require custom update orchestration or don't require updates at all
-   A ReplicaSet's purpose is to maintain a stable set of replica Pods running at any given time. 
-   As such, it is often used to guarantee the availability of a specified number of identical Pods.
-   You can configure HorizontalPodAutoscaler for ReplicaSet as well.

### YAML configuration
-   ReplicaSet.yaml
```
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: <rs-name>
  namespace: <namespace>
spec:
  replicas: <replicas>
  selector:
    matchLabels:            ## Diff between RS and RC. (RC doesnot have matchLabels)
      <key>: <value>
  template:
    metadata:
      labels:
        <key>: <value>
    spec:
      containers:
      - name: <container_name>
        image: <image>
        imagePullPolicy: <image_pull_policy>
        ports:
        - containerPort: <container_port>
          protocol: <protocol>
        resources:
          requests:
            memory: <request_memory>
            cpu: <request_cpu>
          limits:
            memory: <limit_memory>
            cpu: <limit_cpu>
```

- ```kubectl get rs```
- ```kubectl get rs <replication_controller>```
- ```kubectl delete rs <replication_controller>```
