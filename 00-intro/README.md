# Namespaces

* Download kubeconfig
* Copy kubeconfig to `~/.kube/config`
* Install kubectl: https://kubernetes.io/docs/tasks/tools/install-kubectl/
* Try connection

* Check versions of local installation and remote server
  
```shell
kubectl version
```

* List Namespaces

```shell
kubectl get namespaces
```

* Create Namespace

```shell
kubectl create namespace <YOURNAME>
kubectl label namespace <YOURNAME> golem-workshop=true
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
