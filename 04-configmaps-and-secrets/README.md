# ConfigMaps and Secrets

## Preparation

* Before you begin with the actual exercise please make sure to follow these steps to work in your own environment:

  ```shell
  kubectl create ns <YOURNAME>
  kubectl config set-context --current --namespace=<YOURNAME>
  ```

* Clone this repository to your working station and change into the directory for this exercise

---

## Exercise

### Deploy the components

* Deploy application with configmap and secret

  ```shell
  kubectl apply -f secret.yaml -f configmap.yaml -f deployment.yaml
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

* See how the configmap and secret are being injected inside the deployment

  ```shell
  kubectl get deployment web-application -o yaml
  ```

* Fetch the IP address of your LB service again
  and browse the website `http://<IP_ADDRESS>`
  or curl the website with `curl http://<IP_ADDRESS>`.
  * If you already deleted the LB - create a port forward to the pod before

    ```shell
    kubectl port-forward pods/web-application-<xxxxxxx> 8080:80
    ```
    
    * then visit the URL http://localhost:8080 or `curl http://localhost:8080`

* <details><summary>Optionally connect to the app pod and look at the index.php</summary>

  ```shell
  kubectl get pods
  kubectl exec web-application-xxxx-xx -- cat index.php
  ```

  </details>

### Optional: Cleanup

* To cleanup after this exercise you can optionally run

  ```shell
  kubectl delete cm/web-application-config secret/web-application-secret deploy/web-application
  ```
