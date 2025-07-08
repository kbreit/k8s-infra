# Kubernetes Manifests

This is a lab environment for me to work with Kubernetes GitOps style deployments. While it was originally using k3s, I've moved it to kubeadm for greater flexibility.

The design assumes a single control plane node with multiple workers. While having all three nodes as control plane is feasible, the modifications to the manifests haven't been done so it isn't supported in this repository.

## kube-vip

kube-vip is the first application that should be installed as it is responsible for handling VIPs for the control plane nodes. The VIP should be passed to `kubeadm` with `--control-plane-endpoint 192.168.15.95 --upload-certs`. This works even for a single control plane node.

Note: `kube-vip` is a new addition and while installable is not fully configured.

## Cilium

Cilium is used for the CNI and service mesh. The repository assumes it is installed and configured using the `cilium` CLI tool. Eventually the Helm chart will be supported with a script to improve consistency. However, the ConfigMap is stored in this repository.

Note: Cilium is a new addition and while installable and operational it isn't fully configured.

## ArgoCD

Installing ArgoCD in this environment is probably a 2 step process. First, install the CRDs, then Argo.

TODO:

- Add applications
- Make the application I have work better
- Add multi-environment selectors for AppSet
- Allow for Argo to enable/disable for an application per cluster
