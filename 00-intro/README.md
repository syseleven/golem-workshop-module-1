# Namespaces

* Download kubeconfig
* Copy kubeconfig to `~/.kube/config`
* Install kubectl: https://kubernetes.io/docs/tasks/tools/install-kubectl/
* Try connection

```shell
kubectl version
```

* List Namespaces

```shell
kubectl get namespaces
```

* Create Namespace

```shell
kubectl create namespace <YOUR_NAME>
```

* Set default namespace to context

```shell
kubectl config set-context --current --namespace=<YOUR_NAME>
```

* See change in kubeconfig

```shell
cat ~/.kube/config
```

* Verify that helm is installed (should be 3.x.x)

```shell
helm version
```
