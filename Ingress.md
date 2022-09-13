## Ingress

-   An API object that manages external access to the services in a cluster, typically HTTP
-   Ingress exposes HTTP and HTTPS routes from outside the cluster to services within the cluster
-   Traffic routing is controlled by rules defined on the Ingress resource.
-   Pre-requisites
    -   You must have an Ingress controller to satisfy an Ingress.
    -   Only creating an Ingress resource has no effect.
-   Implementation for ingress is called Ingress-Controller. 
-   These are the set of pods that runs in the cluster which evaluates and processes ingress rules.
-   The function of Ingress Controller is to
    -   Evaluate all rules
    -   Manage all re-directions
    -   This is the entrypoint for all requests in our cluster
-   k8s Nginx Ingress controller is the Ingress Controller implementation provided by Kubernetes
-   There are many third party Ingree Controller Implementation available
-   Minikube has Minikube Ingress controller, which is easy to manage
    -   ```minikube addons enable ingress```
-   With Ingress you can configure one domain with multiple services based on different path
-   With Ingress you can configure sub-domains for each service
-   We can configure TLS certificate in Ingress with the help of secrets of type tls


## YAML configuration
-   Ingress.yaml
```
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: <ingress_name>   ## must be a valid DNS sub-domain name
spec:
  ingressClassName: <ingress-class-name>
  rules:
  - host: <host>
    http:
      paths:
      - path: <path>
        pathType: <path_type>
        backend:
          service:
            name: <service_name>
            port:
              number: <port>
```




