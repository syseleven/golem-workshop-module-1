# Pods

## Preparation

* Before you begin with the actual exercise please make sure to follow these steps to work in your own environment:

  ```shell
  kubectl create ns <YOURNAME>
  kubectl config set-context --current --namespace=<YOURNAME>
  ```

* Clone this repository to your working station and change into the directory for this exercise

---

## Exercise

### Creating pods

* Create a pod via an imperative command

  ```shell
  kubectl run --image=nginx my-nginx
  ```

* Verify the creation of the pod by listing the pods

  ```shell
  kubectl get pods
  ```

* Let's start a pod running the same image the declarative way using the provided `pod.yaml`

  ```shell
  kubectl apply -f pod.yaml
  ```

  <details><summary>Contents of pod.yaml</summary>

  ```yaml
  apiVersion: v1
  kind: Pod
  metadata:
    name: my-declarative-nginx
  spec:
    containers:
    - name: nginx
      image: nginx
  ```

  </details>

* <details><summary>List the pods again to verify creation of the pod</summary>

  ```shell
  kubectl get pods
  ```

  </details>

### Get information on the pods

* Gather more details on the imperatively created pod

  ```shell
  kubectl describe pod my-nginx
  ```

* When working with a resouce created declaratively you can also reference the YAML file instead using the resouce's name

  ```shell
  kubectl describe -f pod.yaml
  ```

* View the logs of one of the pods (substitute `<POD_NAME>` with a real name of a pod currently running)

  ```shell
  kubectl logs <POD_NAME>
  ```

  <details><summary>Hint: You can also use the -f flag to interactively follow the logs of a pod</summary>

  ```shell
  kubectl logs -f <POD_NAME>
  ```

  </details>

* Optional: Get an interactive shell in one of the pods (substitute `<POD_NAME>` with a real name of a pod currently running)

  ```shell
  kubectl exec -ti <POD_NAME> -- bash
  ```
  * Leave the container
  
    ```shell
    root@my-nginx:/# exit
    ```

### Optional: Cleanup and delete the pods

* Delete a pod via an imperative command

  ```shell
  kubectl delete pod my-nginx
  ```

* Delete the pod the declarative way using the provided `pod.yaml`

  ```shell
  kubectl delete -f pod.yaml
  ```

---

## Conclusion

* you are now able to create and delete pods manually and the declarative way
* you can obtain detailed information of the pod's metadata and configuration
* you can view live logs of a pod's container(s)
