# Deployment

-   A Deployment provides declarative updates for Pods and ReplicaSets.
-   You describe a desired state in a Deployment, and the Deployment Controller changes the actual state to the desired state at a controlled rate
-   You can define Deployments to create new ReplicaSets, or to remove existing Deployments and adopt all their resources with new Deployments.
-   Deployment strategy
    - Recreate 
      -  All existing Pods are killed before new ones are created when
    - RollingUpdate 
      - The Deployment updates Pods in a rolling update fashion
      - You can specify ```maxUnavailable``` and ```maxSurge``` to control the rolling update process
      - ```maxUnavailable``` 
        - specifies maximum number of Pods that can be unavailable during the update process
        - The value can be an absolute number or a percentage of desired Pods.
        - The default value is 25%.
      - ```maxSurge```
        - specifies maximum number of Pods that can be created over the desired number of Pods.
        - The value can be an absolute number or a percentage of desired Pods.
        - The default value is 25%.
- ```minReadySeconds```  specifies the minimum number of seconds for which a newly created Pod should be ready without any of its containers crashing, for it to be considered available. default is 0
- Deployment is used for stateless application deployment

## YAML configuration
-   Deployment.yaml
```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: <deployment_name>
  namespace: <namepace_name>
  labels:
    <key> : <value>
spec:
  replicas: <replicas>
  strategy:
    type: <strategy_type>   ## "Recreate" or "RollingUpdate". "RollingUpdate" is the default
    rollingUpdate:  
      maxSurge: <max_surge_value>                 ## optional default value is 25%
      maxUnavailable: <max_unavailable_value>     ## optional default value is 25%
  selector:
    matchLabels:
      <key> : <value>
  template:
    metadata:
      labels:
        <key> : <value>
    spec:
      containers:
      - name: <container_name>
        image: <image>
        imagePullPolicy: <imagePullPolicy>
        ports:
        - containerPort: <port>
          protocol: <protocol>
        resources:
          requests:
            memory: <requests_memory>
            cpu: <requests_cpu>
          limits:
            memory: <limits_memory>
            cpu: <limits_cpu>
```

-   ```kubectl get deployments```
-   ```kubectl get deployment <deployment_name>```
-   ```kubectl describe deployment <deployment_name>```
-   ```kubectl get pods```
-   ```kubectl get replicaset```
-   ```kubectl delete deployment <deployment_name>```

-   To know the status of rollout for deployment, use the following command ```kubectl rollout status deployment/<deployment_name>```
-   To know the history of rollout for deployment, use the following command ```kubectl rollout history deployment/<deployment_name>```