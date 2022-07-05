# Introduction to Kubernetes

-   **Kubernetes** is a **greek** word for **Helmsman** or **Captain of ship**
-   **Kubernetes** is also referred as **K8S** because **Kubernetes** has 8 letters between first and last character

##   What is Kubernetes (in-short) ?
-   Kubernetes is a **Container management/orchestration tool**
-   Developed by Google lab (and later donated to **CNCF - Cloud Native Computing Foundation**)
-   open source
-   Written in **GoLang**

##   What is Container Orchestration Tool/Engine ?
-   Container orchestration tool or engine automates deploying, scaling and managing containerized application on a group of server.
-   Examples for such tools are:
    -   Kubernetes
    -   Docker Swarm
    -   Apache Mesos Marathon

##   What are Containerized applications ?
-   Container allow a developer to package up an application with all the parts it needs, such as libraries and other dependencies and ship it all out as one package.
-   Docker is a tool designed to make it easier to deploy and run applications by using containers

##   Why do we need Kubernetes ?
-   Organization have to use multiple containers for each application(not just one container) to ensure
    -   Availability
    -   Load balancing
    -   Scale Up and Down based on user load
-   when there are so many containers, organization have to take care of 
    -   Deploying
    -   Scheduling
    -   scaling
    -   load balancing
    -   batch execution
    -   rollbacks
    -   monitoring
-   Container Orchestration Tools helps organization to automate these processes
-   One of such most widely used and popular tool is **Kubernetes**
-   We have other tools such as Docker Swarm, Apache Mesos Marathon etc


##   Features of Kubernetes
-   **Automatic Bin packing**
    -   Kubernetes will take care of packaging these jobs(containers) in **bins(servers)** in most effective way.
    -   Kubernetes automatically packages your application and schedules the container based on the requirements and resources available.
    -   When you specify a **Pod** you can optionally specify how much CPU and Memory(RAM) each container needs. When containers have resource requests specified, the scheduler can make better decisions about which **Node**s to place the PodS on. (Pod's and Node's are kubernetes terms, check kubernetes architecture)    
-   **Service discovery and Load balancing**
    -   Every **Pod** contains
        -   Unique IP
        -   container's
        -   Volume(storage)
    -   **Pods** that have the same set of functions are abstracted into sets, called **services**
    -   A kubernetes **Service** is a set of **Pod** that work together
    -   Kubernetes gives **Pods** their own IP addresses, and a single DNS name for a set of **Pods**, and can load balance across them
    -   Kubernetes can expose a container using a DNS name or using their own IP address
    -   If traffic to a container is high, kubernetes is able to load balance and distribute the network traffic so that the deployment is stable.
-   **Storage orchestration**
    -   Containers running inside a Pod may need to store data
    -   Pods can have a storage volumes
    -   Usually a single volume is shared within all containers in a pod
    -   Kubernetes allows to mount the storage system of your choice (Local, Cloud(AWS),Network(NFS))
-   **Self Healing**    
    -   K8S restarts containers that fail, replaces containers, kill container that doesn't respond to your user-defined health check and doesn't advise them to clients until they are ready to use.
    -   If container fails ->   restart container
    -   If node dies    ->  replaces and reschedule containers on other nodes
    -   If container does not respond to user defined health check ->   Kills container
    -   The process which take cares of all this functionality is called **ReplicationController**
-   **Automated rollouts and rollbacks**
    -   Rollout
        -   deploy changes to the application or its configuration
    -   Rollback
        -   Revert the changes and restore to previous state
    -   Kubernetes ensures there is no downtime during this process
    -   You can describe the desired state for your deployed containers using K8S, and it can change the actual state to desired state at a controlled rate.
-   **Secret and certification management**
    -   Secret
        -   Kubernetes sensitive data like passwords,keys, tokens are handled using Secrets
        -   Secret is a Kubernetes object created outside pods & containers
        -   Makes sensitive data portable and easy to manage
        -   Secret is a Kubernetes object that separates sensitive data from pods and containers
    -   Config maps
        -   Kubernetes configurations are handled using Config Maps
        -   Config Map is a Kubernetes object created outside pods & containers
        -   Makes configuration portable and easy to manage
        -   Config Map is a Kubernetes object that separates configuration from pods and containers
    -   Kubernetes manages secrets and configuration details for an application separately from the container image
    -   Deploy and update secrets and application configuration without rebuilding your image and without exposing secrets in your stack configuration.
    -   Secrets and Configurations are stored separately in ETCD -> ETCD is a key-value datastore.
    -   The max size limit for a secret is 1 MB.
-   **Batch execution**
    -   Batch job requires an executable/process to be **run to completion**
    -   In Kubernetes **run to completion** jobs are primarily used for batch processing
    -   Each job creates one or more pods
    -   During job execution if any container or pod fails, **Job controller** will reschedule the container or pod in another node
    -   Can run multiple pods in parallel and can scale up if required
    -   As the job is completed, the pods will move from running state to shut down state.
    -   Kubernetes supports batch execution, long running jobs and replaces failed containers. 
-   **Horizontal scaling**
    -   In kubernetes we can scale up or down the containers, we can do this in following ways
        -   Using commands
        -   from the dashboard(Kubernetes UI)
        -   Automatically based on CPU usage
    -   Replication controller(rc or rcs)
        -   Replication controller is a structure that enables to create multiple pods, then make sure that the number of pods always exist.
        -   If a pod crashes, the replication controller replaces it.
    -   Manifest
        -   Replication controller gets the number of pods to run and make available at any time from the information provided in manifest file.
    -   Horizontal Pod autoscaler
        -   automatically scales the number of pods in a replication controller based on observed CPU Utilization or with custom matrix


## What is Kubernetes ?
-   Kubernetes is an open source container orchestration engine for automated deployment, scaling and management of containerized application.
-   Kubernetes is a portable, extensible, open source platform for managing containerzed workloads and services, that facilitates both declarative configuration and automation.