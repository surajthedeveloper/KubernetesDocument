# Deploying application in Kubernetes using .yaml configuration file

-   Let's develop and deploy our own application. 
-   Let's clone the following repository i.e, [k8s-service-1](https://github.com/surajthedeveloper/k8s-service-1)
-   The project is very simple it exposes an endpoint called ```/config``` which will provide the value of **HOST** environment variable and the service runs on port ```8080```
    -   So the request would be ```http://localhost:8080/config```
-   Let's build and run the code. (prerequisites -> docker,Java,Gradle installed in your machine)
    -   To build the image use the following command   ```.\gradlew clean build docker -x test``` 
    -   Let's verify if the image is build successfully by ```docker images``` command and verify if the image is listed
-   Let's push the image into docker repository (prerequisite is docker account)
    -   Inorder to push images from local system to docker hub you need to sign in from command line first.
    -   use the following command to login ```docker logion```. provide username and password.
    -   Before publishing we need to tag the image by command ```docker tag <image_name>:<version> <accountname>/<image_name>:<version>```
        -   ```docker tag k8s-service-1:1.0.0 jannusuraj/k8s-service-1:1.0.0```
    -   Once tagging is done we can push the image by command ```docker push <accountname>/<image_name>:<version>```
        -   ```docker push jannusuraj/k8s-service-1:1.0.0```
    -   verify if the image upload is successful by visiting https://hub.docker.com/ page
-   Before deploying our image into kubernetes we need to inform kubernetes to read images from our private repository. So we need to create a secret key using following command. ```kubectl create secret docker-registry <Name for the secret> --docker-server=<docker registry> --docker-username=<username> --docker-password=<password>```
-   Verify the secret key generation by command ```kubectl get secret```
-   Let's create a .yaml file for our first deployment named ```k8s-service-1.yaml``` and paste the content

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: k8s-service-1
  labels:
    app: k8s-service-1
spec:
  replicas: 1
  selector:
    matchLabels:
      app: k8s-service-1
  template:
    metadata:
      labels:
        app: k8s-service-1
    spec:
      imagePullSecrets:
        - name: [Name for the secret]
      containers:
        - name: k8s-service-1
          image: [accountname]/k8s-service-1:1.0.0
          imagePullPolicy: IfNotPresent
          ports:
            - containerPort: 8080
          envFrom:
            - configMapRef:
                name: message-configmap
---
apiVersion: v1
kind: Service
metadata:
  name: k8s-service-1
spec:
  selector:
    app: k8s-service-1
  ports:
  - protocol: TCP
    port: 8080
    targetPort: 8080
  type: LoadBalancer
---
apiVersion: v1
kind: ConfigMap
metadata:
  name: message-configmap
data:
  MESSAGE: Welcome
```

-   replace the value for [accountname] and [Name for the secret] in ```k8s-service-1.yaml``` file.

-   Let's deploy our .yaml file into kuberetes using the command ```kubectl apply -f k8s-service-1.yaml```
-   Verify the deployment creation, pod creation, replicaset creation and service creation using following commands
    -   ```kubectl get deployments```
    -   ```kubectl get replicaset```
    -   ```kubectl get pods```
    -   ```kubectl get services```
-   Let's open this URL http://localhost:8080/config in chrome and verify the output. You should receive the pod name in response.
```
{
  "hostname": "k8s-service-1-688fccd646-ngsrx",
  "message": ""
}
```