# Deployments

## Preparation

* Before you begin with the actual exercise please make sure to follow these steps to work in your own environment:

  ```shell
  kubectl create ns <YOURNAME>
  kubectl label namespace <YOURNAME> golem-workshop=true
  kubectl config set-context --current --namespace=<YOURNAME>
  ```

* Clone this repository to your working station and change into the directory for this exercise

## Exercise

### Creating deployments

* Create a deployments via an imperative command

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
  * optionally create your own YAML file for the deployment

    ```shell
    kubectl create deployment declarative-deploy --image=nginx --replicas=2 --dry-run=client -o yaml > deployment.yaml
    ```

* Either way - apply the `deployment.yaml`

  ```shell
  kubectl apply -f deployment.yaml
  ```

* List the deployment and the underlying resources again to verify their creation

### Get information on the deployments

* Gather more details one of the deployments

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
  
  # some entrypoints for investigation
  kubectl get deployment
  kubectl get replicaset
  kubectl get pod
  ```

* scale the deployment `declarative-deploy` to 3 by editing the YAML file

  ```shell
  vi deployment.yaml
  
  ...
  spec:
    replicas: 3
  ...
  
  kubectl apply -f deployment.yaml
  ```

* watch the changes again
* update the image of the deployment `declarative-deploy` using `kubectl edit`

  ```shell
  kubectl edit deploy declarative-deploy
  
  ...
  spec:
    template:
      spec:
        containers:
        - name: nginx
          image: "syseleven/metakube-hello:2.0.0"
  ...
  ```

### Optional: clean up and delete the deployments

* Delete the deployments

  ```shell
  kubectl delete deployments nginx-deploy declarative-deploy
  ```
