# Persistent Storage

## Preparation

* Before you begin with the actual exercise please make sure to follow these steps to work in your own environment:

  ```shell
  kubectl create ns <YOURNAME>
  kubectl config set-context --current --namespace=<YOURNAME>
  ```

* Clone this repository to your working station and change into the directory for this exercise

---

## Exercise

### Deploy the resources

* Show available storageclasses

  ```sh
  kubectl get storageclass
  ```

* Deploy Persistent Volume Claim

  ```shell
  kubectl apply -f pvc.yaml
  kubectl get -f pvc.yaml
  ```

* *Note that the pvc will be pending until a consumer pod is up*

* Deploy Application and Service

  ```shell
  kubectl apply -f deployment.yaml
  kubectl get -f deployment.yaml
  
  kubectl apply -f service.yaml
  kubectl get -f service.yaml
  ```

* Show Persistent Volume Claim and details of Deployment

  ```shell
  kubectl get pod,pvc,deploy,svc
  kubectl describe pvc first-storage
  kubectl describe deployment webserver-with-storage
  ```

* add Data to Pod and delete Pod

  ```shell
  kubectl exec -it <POD> -- /bin/bash
  ```

  * Inside Container run the following
  
    ```sh
    curl localhost # should response with 403 Forbidden since NGINX is not allowed to list directory and no index.html is available
    
    cat /usr/share/nginx/html/index.html # should be emtpy since we've mounted a clean storage into our container 
    
    echo '
    <!DOCTYPE html>
    <html>
    <head>
    <title>Welcome to the workshop!</title>
    <style>
    html { color-scheme: light dark; }
    body { width: 35em; margin: 0 auto;
    font-family: Tahoma, Verdana, Arial, sans-serif; }
    </style>
    </head>
    <body>
    <h1>Welcome to the workshop!</h1>
    
    <p><em>Thank you!</em></p>
    </body>
    </html>
    ' > /usr/share/nginx/html/index.html
    
    cat /usr/share/nginx/html/index.html
    curl localhost
    
    exit
    ```

* Exit the pod
* Open new Terminal and Port Forward to Service

  ```shell
  kubectl port-forward svc/webserver-with-storage 8080:80
  ```

* Open your Browser and check http://localhost:8080
* Open another terminal and delete pod

  ```shell
  kubectl delete pod <POD>
  ```

* Check if port-forward is still working, if not, reopen new

  ```shell
  kubectl port-forward svc/webserver-with-storage 8080:80
  ```

* Open your Browser again http://localhost:8080
* You should receive the same result since PVC left untouched

### Optional: Cleanup

* To cleanup after this exercise you can optionally run

  ```shell
  kubectl delete -f service.yaml -f deployment.yaml -f pvc.yaml
  ```
