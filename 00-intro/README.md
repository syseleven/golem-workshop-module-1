# Namespaces

* Download kubeconfig (link will be provided by instructors)
* Copy kubeconfig to `~/.kube/config`
* Install kubectl: https://kubernetes.io/docs/tasks/tools/install-kubectl/

* Check versions of local installation and remote server
  
```shell
kubectl version
```

* Verify kubectl uses your kubeconfig file by default

```shell
kubectl config view
```

* Try to connect

```shell
kubectl get nodes
```

* List Namespaces

```shell
kubectl get namespaces
```

* Create Namespace

```shell
kubectl create namespace <YOURNAME>
```

* Set default namespace to context

```shell
kubectl config set-context --current --namespace=<YOURNAME>
```

* See change in kubeconfig

```shell
cat ~/.kube/config
```

* Verify that [helm is installed](https://helm.sh/docs/intro/install/) (should be 3.x.x)

```shell
helm version
```
