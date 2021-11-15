# Dive-In Kubernetes: Basic Concepts

## Beschreibungstext

In diesem Dive-In Workshop bekommt ihr einen Überblick über das Basiskonzept von Kubernetes, Grundlagen von Containern und vielen anderen Ressourcen vermittlet. Darüber hinaus sprechen wir über aktuelles Tooling und stellen einige kurz vor.

## Workshop requirements

To participate in our workshops you will require the following items on your notebook:

* Linux, MacOS or Windows idealy with an administrator access
* SSH key pair (public and private key)
* [Create SSH key pair](https://www.ssh.com/ssh/keygen/)
* Docker desktop software
* [Install Docker desktop Windows](https://docs.docker.com/docker-for-windows/install/)
* [Install Docker desktop MacOS](https://docs.docker.com/docker-for-mac/install/)
* kubernetes client software kubectl
* [Install kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
* kubectx context management tool
* [Install kubectx](https://github.com/ahmetb/kubectx/)
* helm client software version 3.x
* [Install helm](https://helm.sh/docs/intro/install)

## Extra

- `k9s` -> https://github.com/derailed/k9s
- Lens -> https://k8slens.dev/
- Ranchder Desktop -> https://rancher.com/blog/2021/rancher-desktop-an-open-source-app-for-desktop-kubernetes-and-container-management
- Web basierter Generator für K8S YMLs -> https://k8syaml.com/

## Docker (Ersatz/lizenztechnisches)

- bei Lizenzbedenken bzgl. Docker Desktop auf Windows -> https://dev.to/_nicolas_louis_/how-to-run-docker-on-windows-without-docker-desktop-hik
- Podman als Docker Ersatz - https://podman.io/

## Environment

- `zsh-autosuggestions` -> https://github.com/zsh-users/zsh-autosuggestions
- `zsh-autocomplete` -> https://github.com/marlonrichert/zsh-autocomplete
- `zsh-syntax-highlighting` -> https://github.com/zsh-users/zsh-syntax-highlighting
- `oh-my-zsh` -> https://ohmyz.sh/#install
- `Powerlevel10k` -> https://github.com/romkatv/powerlevel10k

## Config Management

```
export KUBECONFIG="$(find ~/.kube/configs -iname 'kubeconfig-*' -exec printf '%s:' '{}' +)${HOME}/.kube/configs/config"

load_kubeconfig () {
  export KUBECONFIG="$(find ~/.kube/configs -iname 'kubeconfig-*' -exec printf '%s:' '{}' +)${HOME}/.kube/configs/config"
}
load_kubeconfig
```

## Prometheus

- Prometheus mit mehreren Clustern -> https://sysrant.com/posts/prometheus-multi-cluster/

## k8s testen

- kubeadm (minimum viable Kubernetes cluster) -> https://kubernetes.io/docs/reference/setup-tools/kubeadm/
- k3s (Lightweight Kubernetes) -> https://k3s.io/
- k3d (k3d is a lightweight wrapper to run k3s) -> https://k3d.io/
- KIND (Kubernetes in Docker) -> https://kind.sigs.k8s.io/

## Additional tooling and resources

* https://github.com/aylei/kubectl-debug
* https://github.com/kubernetes-sigs/krew
* https://github.com/corneliusweig/rakkess
* https://github.com/derailed/popeye
* https://github.com/kubernetes-sigs/krew-index/blob/master/plugins/view-secret.yaml
* https://github.com/kubernetes-sigs/krew-index/blob/master/plugins/get-all.yaml
* https://github.com/kubernetes-sigs/krew-index/blob/master/plugins/resource-capacity.yaml
* https://github.com/kubernetes-sigs/krew-index/blob/master/plugins/view-utilization.yaml
* https://github.com/instrumenta/kubeval
* https://github.com/hadolint/hadolint
* https://www.telepresence.io/
* https://github.com/weaveworks/flux
* https://tilt.dev/
* https://argoproj.github.io/argo-cd/
* https://kubernetes.github.io/ingress-nginx/
* https://cert-manager.readthedocs.io/
* https://github.com/presslabs/mysql-operator
* https://github.com/coreos/prometheus-operator
* https://prometheus.io/
* https://grafana.com
* https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.16/
* https://operatorhub.io/
* https://keel.sh/
* https://helm.sh/
* https://ahmet.im/blog/mastering-kubeconfig/
* https://github.com/IBM/kui
* https://github.com/bitnami-labs/sealed-secrets
* https://github.com/eldadru/ksniff
* https://kubernetes.academy/
* https://github.com/jonmosco/kube-ps1
* https://github.com/kubernetes/autoscaler/tree/master/cluster-autoscaler
* https://github.com/herbrandson/k8dash
* https://github.com/kubernetes/dashboard
* https://gitlab.com/bashofmann/angular-test-app-finished
* https://github.com/kelseyhightower/kubernetes-the-hard-way
* https://k8s.af/
* https://github.com/derailed/k9s
* https://github.com/ramitsurana/awesome-kubernetes
* https://github.com/int128/kubelogin
* https://github.com/wagoodman/dive
