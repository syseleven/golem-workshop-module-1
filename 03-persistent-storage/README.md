# Persistent Storage

* Deploy Persistent Volume Claim

```shell
kubectl -n "YOUR-NAMESPACE" apply -f pvc.yaml
kubectl -n "YOUR-NAMESPACE" get -f pvc.yaml
```

* Deploy Application and Service

```shell
kubectl -n "YOUR-NAMESPACE" apply -f deployment.yaml
kubectl -n "YOUR-NAMESPACE" get -f deployment.yaml

kubectl -n "YOUR-NAMESPACE" apply -f service.yaml
kubectl -n "YOUR-NAMESPACE" get -f service.yaml
```

* Show Persistent Volume Claim and details of Deployment

```shell
kubectl -n "YOUR-NAMESPACE" get pod,pvc,deploy,svc
kubectl -n "YOUR-NAMESPACE" describe pvc first-storage
kubectl -n "YOUR-NAMESPACE" describe deployment webserver-with-storage
```

* add Data to Pod and delete Pod

```shell
kubectl -n "YOUR-NAMESPACE" exec -it "POD" -- /bin/bash
```

#Inside Container

```
curl localhost
cat /usr/share/nginx/html/index.html

echo '
<!DOCTYPE html>
<html>
<head>
<title>Welcome to the Golem Dive-in Kubernetes workshop!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to the Golem Dive-in Kubernetes workshop!</h1>

<p><em>Thank you!</em></p>
</body>
</html>
' > /usr/share/nginx/html/index.html

cat /usr/share/nginx/html/index.html
curl localhost

exit
```

# Outside Container

* Open new Terminal and Port Forward to Service

```shell
kubectl -n "YOUR-NAMESPACE" port-forward svc/webserver-with-storage 8080:80
```

* Open your Browser and check http://localhost:8080

* Open another terminal and delete pod

```shell
kubectl -n "YOUR-NAMESPACE" delete "pod"
```

* Check if port-forward is still working, if not, reopen new

```shell
kubectl -n "YOUR-NAMESPACE" port-forward svc/webserver-with-storage 8080:80
```

* Open your Browser again http://localhost:8080
* You should receive the same result
