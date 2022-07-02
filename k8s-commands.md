Minikube commands
=================
```minikube start```

```minikube dashboard```


Kubernetes Commands
===================

-	Kubectl => Kube controller

```kubectl version``` or ```kubectl version --short```

```kubectl get namespaces``` or  ```kubectl get namespace``` or ```kubectl get ns```

```kubectl get events```

```kubectl get events --sort-by=.metadata.creationTimeStamp```

```kubectl create deployment [Name For deployment] --image=[Image name]:[Version]```
		=> creates a deployment, replicaset and pod

-	Example : kubectl create deployment microservice --image=jannusuraj/microservice:1.0.0

```kubectl get deployment```

```kubectl delete deployment [name of the deployment]```

```kubectl expose deployment [Name of deployment] --type=[Type] --port=[Port]```
		=> creates a service

-	Example : kubectl expose deployment microservice --type=LoadBalancer --port=8080

```kubectl get service``` or ```kubectl get svc```

```kubectl delete service [name of the service]```

```kubectl port-forward service/[service name] [system port]:[service port]```

-	Example : kubectl port-forward service/microservice 7080:8080

```kubectl get pods``` or ```kubectl get po``` or ```kubectl get pod```

```kubectl get pods -o wide``` = To get more details

```kubectl explain pods```

```kubectl describe pods [pod name]```

```kubectl get replicaset``` or ```kubectl get rs``` or ```kubectl get replicasets```

```kubectl get replicaset -o wide``` = To get more details

```kubectl explain replicaset```

```kubectl describe pods [pod name]```

```kubectl delete pods [pod name]```

```kubectl scale deployment [deployment name] --replicas=[number of replicas]```

```kubectl set image deployment [deployment name] [container name]=[new image name]```

```kubectl get componentstatuses```

```kubectl get deployment [deployment name] -o yaml```
		=> to get the deployment details in yaml format

```kubectl get deployment [deployment name] -o yaml >> [filename].yaml```
		=> To move the deployment details into yaml file

```kubectl diff -f [deployment file].yaml```
		=> To know the difference between current depployment and the deployment file

```kubectl apply -f [deployment file].yaml```
		=> To create or update the any kubernetes resource from yaml configuration file

```kubectl delete all -l app=[application label]```
		=> To delete all resources based on label

```kubectl get all```
		=> to get the details of all resources

```kubectl logs [pod name]``` 
		=> to view the pod logs
	
```kubectl logs -f [pod name]``` 
		=> to tail the logs

```kubectl create configmap [configmap name] --from-literal=[key]=[value]```

-	Example : kubectl create configmap microservice-configuration --from-literal=WELCOME_TEXT=Welcome!!!

```kubectl get configmap``` or ```kubectl get cm```

```kubectl get configmap [configmap name]```

```kubectl get configmap [configmap name] -o yaml```
	=> To get the configmap in yaml format

```kubectl rollout history deployment [deployment name]```
	=> To get the rollout history for deployment

```kubectl rollout undo deployment [deployment name] --to-revision=[revision number]```
	=> To rollback the deployment to older revision version obtained from rollout history

```kubectl autoscale deployment [deployment name] --min=[minimum no of pods] --max=[maximum no of pods] --cpu-percent=[threshold of CPU after with new pods should be created]```
	=> Used for autoscaling the deployment called horizontal pod autoscaler (hpa)

```kubectl get hpa```
	=> to get the horizontal pod autoscaler

```kubectl delete hpa [hpa name]```

```kubectl top pod```
	=> to get the cpu and memory usage of a pods

```kubectl top nodes```
	=> to get the cpu and memory usage of a nodes


