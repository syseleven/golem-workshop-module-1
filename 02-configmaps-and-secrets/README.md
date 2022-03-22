# ConfigMaps and Secrets

* If you haven´t done yet create and set your namespace

```shell
kubectl create ns <MY-NAMESPACE>
kubectl config set-context --current --namespace=<MY-NAMESPACE>
```

* Deploy application

```shell
kubectl apply -f web-application/deployment/
```

* Show ConfigMap and Secret

```shell
kubectl get configmap,secret
kubectl describe configmaps web-application-config
kubectl describe secrets web-application-secret
kubectl get -o json secrets web-application-secret
kubectl get secrets web-application-secret -o jsonpath='{.data.passcode\.txt}' | base64 -d
```
