# Kubernetes Helm

-   Kubernetes Helm is a package manager for Kubernetes (You can consider it as HomeBrew, Apt or Yum)
-   It makes it possible to organize Kubernetes objects in a packaged application that anyone can download and install in one click
-   In Helm, these packages are called charts

-   Let's consider we have more than 100 applications that we need to deploy in K8S cluster. For deploying these 100 applications we need 100 .yaml configuration files. But in organizations the deployment pattern for each of these 100 application would be same. I mean to say there could be duplicate configurations exist each of these 100 .yaml configuration file. 
-   Helm solves this same problem. you will create a Blue print for your deployment called Chart in "Chart.yaml". But some of the parameters called image name, version would be different for each of these 100 microservices. Helm provides a way to pass these custom values in a "Values.yaml" file. So the template can use it from external source called "Values.yaml" file.
-   These Helm charts can be stored in a public/Private Helm repositories
-   Deploying application using helm is lot easier. It downloads the chart from helm repository and installs in K8S cluster.
```helm install --values=my-custom-values.yaml <chartname>```
