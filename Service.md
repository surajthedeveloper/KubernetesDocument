# Service

-   An abstract way to expose an application running on a set of Pods as a network service.
-   The set of Pods targeted by a Service is usually determined by a selector.
-   Service is a permanent IP address
-   Lifecycle of Pod and Service is not connected
-   Service is a named abstraction of software service consisting of local port that the proxy listens on, and the selector that determines which pods will answer requests sent through the proxy.
-   Service is also Load Balancer
-   A Service can map any incoming port to a targetPort. By default and for convenience, the targetPort is set to the same value as the port field.
-   Service Types
    -   Cluster IP
        -   Exposes the Service on a cluster-internal IP. 
        -   Choosing this value makes the Service only reachable from within the cluster
        -   This is the default ServiceType.
    -   NodePort
        -   Exposes the Service on each Node's IP at a static port (the NodePort)
        -   A ClusterIP Service, to which the NodePort Service routes, is automatically created
        -   You'll be able to contact the NodePort Service, from outside the cluster, by requesting <NodeIP>:<NodePort>.
        -   nodeport value ranges from 30000 to 32767
        -   Not secured as the ip is exposed outside 
        -   Not used in production
    -   LoadBalancer
        -   Exposes the Service externally using a cloud provider's load balancer
        -   NodePort and ClusterIP Services, to which the external load balancer routes, are automatically created.
    -   ExternalName
        -   Maps the Service to the contents of the externalName field (e.g. foo.bar.example.com), by returning a CNAME record with its value
        -   No proxying of any kind is set up.
        

## Yaml configuration
-   Service.yaml
```
apiVersion: v1
kind: Service
metadata:
  name: <service_name>
  namespace: <namespace>
  labels:
    <key>: <value>
spec:
  selector:
    <key>: <value>
  type: <service_type>
  ports:
  - port: <service_port>
    protocol: <protocol>
    targetPort: <target_port>
    nodePort: <node_port>
```

- ```kubectl get services```
- ```kubectl get services <service_name>```
- ```kubectl delete services <service_name>```