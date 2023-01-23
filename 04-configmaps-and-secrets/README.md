# ConfigMaps and Secrets

## Preparation

* Before you begin with the actual exercise please make sure to follow these steps to work in your own environment:

  ```shell
  kubectl create ns <YOURNAME>
  kubectl label namespace <YOURNAME> golem-workshop=true
  kubectl config set-context --current --namespace=<YOURNAME>
  ```

* Clone this repository to your working station and change into the directory for this exercise

## Exercise

### Deploy the components

* Deploy application with configmap and secret

  ```shell
  kubectl apply -f secret.yaml
  kubectl apply -f configmap.yaml
  kubectl apply -f deployment.yaml
  ```

### Investigate the setup

* Show ConfigMap and Secret

  ```shell
  kubectl get configmap,secret
  ```

* Note the differences in display for configmaps and secrets

  ```shell
  kubectl describe configmaps web-application-config
  kubectl describe secrets web-application-secret
  ```

* Retrieve the "secret" value from the secret
  
  ```shell
  kubectl get -o json secrets web-application-secret
  kubectl get secrets web-application-secret -o jsonpath='{.data.passcode\.txt}' | base64 -d
  ```

* See how the configmap and secret are being used inside the deployment

  ```shell
  kubectl get deployment web-application -o yaml
  ```

### Optional: Cleanup

* To cleanup after this exercise you can optionally run

  ```shell
  kubectl delete cm/web-application-config secret/web-application-secret deploy/web-application
  ```