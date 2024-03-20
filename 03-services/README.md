# Services

## Preparation

* Before you begin with the actual exercise please make sure to follow these steps to work in your own environment:

  ```shell
  kubectl create ns <YOURNAME>
  kubectl config set-context --current --namespace=<YOURNAME>
  ```

* Clone this repository to your working station and change into the directory for this exercise

---

## Exercise

### Create a web application

* Apply the file `deployment-web.yaml`

  ```shell
  kubectl apply -f deployment-web.yaml
  ```

* <details><summary>Inspect the created deployment and the underlying resources</summary>

  ```shell
  kubectl get -f deployment-web.yaml
  kubectl get pods
  kubectl get rs
  ```

  </details>

### Make the deployment publically available

* Create a service (type Loadbalancer) with the file `service-loadbalancer.yaml`

  ```shell
  kubectl apply -f service-loadbalancer.yaml
  ```

* Get external IP from LoadBalancer Service
  (watch this command until "EXTERNAL-IP" is no longer "pending" and finally gets a fix IP)

  ```shell
  kubectl get service web-application -w
  ```

* Visit the URL `http://<IP_ADDRESS>` or curl the website with `curl http://<IP_ADDRESS>`

### Make the deployment (only) internally available

* Create a service (of type ClusterIP) with the file `service-clusterip.yaml`

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

  * *Note that all services can be reached via DNS cluser internally: serviceName.namespace.svc.cluster.local*

  * Exit the debugging pod

### Make the deployment reachable on your work station for debugging purposes

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
