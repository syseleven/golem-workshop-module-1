# Simple Web Application

* Install Docker: https://docs.docker.com/install/
* Build docker image

```shell
docker build -t syseleven/k8s-workshop-web-application:1.0.0 web-application/
```

* Run docker image locally

```shell
docker run --rm -p 8080:80 syseleven/k8s-workshop-web-application:1.0.0
```

* Go to http://localhost:8080

* Now deploy the application and a service to kubernetes

```shell
kubectl create ns <YOURNAME>
kubectl config set-context --current --namespace=<YOURNAME>
kubectl apply -f web-application/deployment/
```

* Get external IP from LoadBalancer Service
* repeat this command until "EXTERNAL-IP" is no longer "pending" and finally gets a fix IP

```shell
kubectl get service web-application
```

* Go to http://<IP_ADDRESS>
* Scale it up to two pods

```shell
kubectl scale deployment web-application --replicas 2
```

* See Status of Deployment

```shell
kubectl get deployments
kubectl describe deployment web-application
kubectl get deployment web-application -o yaml
```

* See Status of ReplicaSets

```shell
kubectl get replicasets
kubectl describe replicasets web-application-xxx
```

* See Status of Pods

```shell
kubectl get pods
kubectl describe pods
kubectl logs <WEB_APPLICATION_POD_NAME>
```

* Get shell in pod

```shell
kubectl exec -it <WEB_APPLICATION_POD_NAME> -- /bin/bash
exit
```

* Port Forwarding

```shell
kubectl port-forward service/web-application 8080:80
```

* Go to http://localhost:8080
