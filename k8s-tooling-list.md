# k8s Tooling List

## Basics

- `kubectl` -> <https://kubernetes.io/docs/tasks/tools/>
- `kubectx`/`kubens` -> <https://github.com/ahmetb/kubectx>
- `kubectx-foreach` -> <https://github.com/ahmetb/kubectl-foreach>
- `kubectl-convert` ->  <https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/#install-kubectl-convert-plugin>
- `kubectl-neat` -> <https://github.com/itaysk/kubectl-neat>
- `kubectl-node-shell` -> <https://github.com/kvaps/kubectl-node-shell>
- `kubectl-df-pv` -> <https://github.com/yashbhutwala/kubectl-df-pv>
- `kubectl-get-all` -> <https://github.com/corneliusweig/ketall>
- `helm` -> <https://helm.sh/docs/intro/install/>
- `stern`-> <https://github.com/stern/stern>

## Extra

- `k9s` -> <https://github.com/derailed/k9s>
- Lens -> <https://k8slens.dev/>
- Web basierter Generator für K8S YMLs -> <https://k8syaml.com/>

## Docker (Ersatz/lizenztechnisches)

- Lizenzbedenken Docker Desktop Windows -> <https://dev.to/_nicolas_louis_/how-to-run-docker-on-windows-without-docker-desktop-hik>
- Podman als Docker Ersatz - <https://podman.io/>

## Environment

- `zsh-autosuggestions` -> <https://github.com/zsh-users/zsh-autosuggestions>
- `zsh-autocomplete` -> <https://github.com/marlonrichert/zsh-autocomplete>
- `zsh-syntax-highlighting` -> <https://github.com/zsh-users/zsh-syntax-highlighting>
- `oh-my-zsh` -> <https://ohmyz.sh/#install>
- `Powerlevel10k` -> <https://github.com/romkatv/powerlevel10k>

## Config Management

```shell
export KUBECONFIG="$(find ~/.kube/configs -iname 'kubeconfig-*' -exec printf '%s:' '{}' +)${HOME}/.kube/configs/config"

load_kubeconfig () {
  export KUBECONFIG="$(find ~/.kube/configs -iname 'kubeconfig-*' -exec printf '%s:' '{}' +)${HOME}/.kube/configs/config"
}
load_kubeconfig
```

## Prometheus

- Prometheus mit mehreren Clustern -> <https://sysrant.com/posts/prometheus-multi-cluster/>

## k8s testen

- kubeadm (minimum viable Kubernetes cluster) -> <https://kubernetes.io/docs/reference/setup-tools/kubeadm/>
- k3s (Lightweight Kubernetes) -> <https://k3s.io/>
- k3d (k3d is a lightweight wrapper to run k3s) -> <https://k3d.io/>
- KIND (Kubernetes in Docker) -> <https://kind.sigs.k8s.io/>
