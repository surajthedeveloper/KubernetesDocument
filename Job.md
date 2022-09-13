# Job

-   Job is a controller in k8s, which supervises pods for carrying out certain tasks
-   There are mainly 3 types of k8s jobs
    -   Non-Parallel jobs (Job)
        -   Usually a single pod jobs
        -   The restart policy should be either OnFailure or Never. It cannot be always
        -   
    -   Parallel jobs with fixed completion count
    -   Parallel jobs with a task queue
-   Pods are not deleted after completion
-   Jobs are of 2 types
    -   Run to completion (Job)
    -   Scheduled (CronJob)
-   Job controller restarts or rescheduled if a pod or node fails during the execution.
-   Usecases
    -   One time initialization of resources such as database
    -   Multiple workers to process messages in queue


## Commands
- ```kubectl get jobs```
- ```kubectl get jobs <job_name>```
- ```kubectl delete jobs <job_name>```


## Yaml configuration
-   Job.yaml
```
apiVersion: batch/v1
kind: Job
metadata:
  name: <job_name>
spec:
  template:
    spec:
      containers:
      - name: <container_name>
        image: <image_name>
      restartPolicy: <restart_policy>
  backoffLimit: <backoff_limit>       ## default is 6, exponential backoff
```