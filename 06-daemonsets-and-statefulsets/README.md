# DaemonSets and StatefulSets

## Preparation

* Before you begin with the actual exercise please make sure to follow these steps to work in your own environment:

  ```shell
  kubectl create ns <YOURNAME>
  kubectl config set-context --current --namespace=<YOURNAME>
  ```

* Clone this repository to your working station and change into the directory for this exercise

---

## Exercise

### Create a DaemonSet

* Apply the file `daemonset.yaml`

  ```shell
  kubectl apply -f daemonset.yaml
  ```

* Inspect the created DaemonSet and the underlying resources

  ```shell
  kubectl get ds,pods
  ```

### Create a StatefulSet

* Create StatefulSet by applying the file `statefulset.yaml`

  ```shell
  kubectl apply -f statefulset.yaml
  ```

* Inspect the created StatefulSet and the underlying resources

  ```shell
  kubectl get sts,pods
  ```

### Inspect the differences

* Note how both DaemonSets and StatefulSets do not use/create a ReplicaSet like Deployments do

  ```shell
  kubectl get rs
  ```

* Note the different naming schemes for pods from ...
  * Deployments: `appname-<RS_ID>-<POD_ID>`
  * DaemonSets: `appname-<POD_ID>`
  * StatefulSets: `appname-<0 to N-1>`

    ```shell
    kubectl get pods
    ```

* Optionally use `kubectl describe` to investigate the resources further

### Optional: Cleanup

* To cleanup after this exercise you can optionally run

  ```shell
  kubectl delete -f daemonset.yaml -f statefulset.yaml
  ```
