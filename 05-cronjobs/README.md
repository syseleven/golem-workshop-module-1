# Cronjobs

## Preparation

* Before you begin with the actual exercise please make sure to follow these steps to work in your own environment:

  ```shell
  kubectl create ns <YOURNAME>
  kubectl config set-context --current --namespace=<YOURNAME>
  ```

* Clone this repository to your working station and change into the directory for this exercise

---

## Exercise

### Create a cronjob

* Create a cronjob with the provided `cronjob.yaml`

  ```shell
  kubectl apply -f cronjob.yaml
  ```

* Verify the creation of the cronjob

  ```shell
  kubectl get cronjobs
  ```

### Watch the execution of the cronjob

* Watch the jobs and pods and look out for a pod starting with `demo-cron-*`

  ```shell
  watch -- kubectl get job,pods
  ```

* Copy the name of the pod and look at its log

  ```shell
  kubectl logs demo-cron-XXXXXXX-xxxxx
  ```

* Also take note of how every cronjob run creates a job which creates a pod
  (be patient it may take two minutes)

  ```shell
  kubectl get jobs,pods
  ```

* Optionally inspect the resources created by this exercise

### Optional: clean up and delete the cronjob

* Delete the cronjob

  ```shell
  kubectl delete -f cronjob.yaml
  ```
