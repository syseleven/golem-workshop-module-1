# Deployments

## Preparation

* Before you begin with the actual exercise please make sure to follow these steps to work in your own environment:

  ```shell
  kubectl create ns <YOURNAME>
  kubectl config set-context --current --namespace=<YOURNAME>
  ```

* Clone this repository to your working station and change into the directory for this exercise

---

## Exercise

### Creating deployments

* Create a deployment via an imperative command

  ```shell
  kubectl create deployment --image=nginx --replicas=2 nginx-deploy
  ```

* Verify the creation of the deployment and the underlying resources

  ```shell
  kubectl get deployment
  kubectl get replicaset
  kubectl get pod
  ```

* Let's create a deployment running the same image the declarative way
  * <details><summary>Optionally create your own YAML file for the deployment</summary>

    ```shell
    kubectl create deployment declarative-deploy --image=nginx --replicas=2 --dry-run=client -o yaml > deployment.yaml
    ```

    </details>

* Either way - apply the `deployment.yaml`

  ```shell
  kubectl apply -f deployment.yaml
  ```

* <details><summary>List the deployment and the underlying resources again to verify their creation</summary>

  ```shell
  kubectl get deployment
  kubectl get replicaset
  kubectl get pod
  ```
* Alternatively you can output all objects at once by using a comma sparated list
  
  ```shell
  kubectl get deploy,rs,pod
  ```

  </details>

### Get information on the deployments

* Gather more details on of the deployments

  ```shell
  # any of these commands can be used
  kubectl describe deploy nginx-deploy
  kubectl describe deploy declarative-deploy
  kubectl describe -f deployment.yaml
  ```

### Modifying deployments

There are numerous ways to modify an existing deployment.
The next steps show you some of the methods available.
Which one you use comes down to the circumstances and personal preference.

* Scale the deployment `nginx-deploy` to 4 pods and investigate the changes

  ```shell
  kubectl scale deployment nginx-deploy --replicas 4
  ```

  <details><summary>Some entrypoints for investigation</summary>

  ```shell
  kubectl get deployment
  kubectl get replicaset
  kubectl get pod
  kubectl describe deploy nginx-deploy
  ```

  </details>

* scale the deployment `declarative-deploy` to 3 by editing the YAML file

  ```shell
  # open the YAML file for editing
  vi deployment.yaml
  
  # find spec.replicas and change it to "3"
  ...
  spec:
    replicas: 3
  ...
  
  # apply the change
  kubectl apply -f deployment.yaml
  ```

* <details><summary>Watch the changes again</summary>

  ```shell
  kubectl get deployment
  kubectl get replicaset
  kubectl get pod
  kubectl describe deploy nginx-deploy
  kubectl describe deploy declarative-deploy
  ```

  </details>

* update the image of the deployment `declarative-deploy` using `kubectl edit`

  ```shell
  # run edit command
  kubectl edit deploy declarative-deploy
  
  # find spec.template.spec.containers[].image and change it to "syseleven/metakube-hello:2.0.0"
  ...
  spec:
    template:
      spec:
        containers:
        - name: nginx
          image: "syseleven/metakube-hello:2.0.0"
  ...
  ```

* <details><summary>Verify that the image has changed</summary>

  ```shell
  kubectl describe deploy declarative-deploy
  ```

  </details>

### Optional: clean up and delete the deployments

* Delete the deployments

  ```shell
  kubectl delete deployments nginx-deploy declarative-deploy
  ```

---

## Conclusion

* you are now able to create pods which are controlled by a replicaset and a deployment
* your understand how scaling of pod replicas works
* you can now edit and change specific elements of a deployment such as the image
* deployments are very often used and are a very common resource to create and control workloads
