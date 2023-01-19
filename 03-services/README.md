# Services

## Preparation

* Before you begin with the actual exercise please make sure to follow these steps to work in your own environment:

  ```shell
  kubectl create ns <YOURNAME>
  kubectl label namespace <YOURNAME> golem-workshop=true
  kubectl config set-context --current --namespace=<YOURNAME>
  ```

* Clone this repository to your working station and change into the directory for this exercise

## Exercise

### Create a web application

* Apply the file `deployment-web.yaml`

  ```shell
  kubectl apply -f deployment-web.yaml
  ```

* Inspect the created deployment and the underlying resources

### Make the deployment publically available

* Create a service (type Loadbalancer) with the file `service-loadbalancer.yaml`

  ```shell
  kubectl apply -f service-loadbalancer.yaml
  ```

* Get external IP from LoadBalancer Service
  (repeat this command until "EXTERNAL-IP" is no longer "pending" and finally gets a fix IP)

  ```shell
  kubectl get service web-application
  ```

* Go to `http://<IP_ADDRESS>`

### Make the deployment internally available

* Create a service (type ClusterIp) with the file `service-clusterip.yaml`

  ```shell
  kubectl apply -f service-clusterip.yaml
  ```

* Get a shell in a debugging pod to test the application/service in the cluster

  ```shell
  kubectl run tmp-shell --rm -ti --image nicolaka/netshoot -- /bin/bash
  ```

  * Inside the pod try to reach the internal service

    ```shell
    curl http://web-application-int
    ```

  * *Note that the services can be reached via DNS cluser internally: serviceName.namespace.svc.cluster.local*

### Make the deployment reachable on work station for debugging

* Port Forwarding

```shell
kubectl port-forward service/web-application-int 8080:80
```

* Go to [http://localhost:8080](http://localhost:8080)

### Optional: Cleanup

* To cleanup after this exercise you can optionally run

  ```shell
  kubectl delete svc/web-application-int svc/web-application deploy/web-application
  ```
