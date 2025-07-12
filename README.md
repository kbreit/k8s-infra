# Kubernetes Manifests

This is a lab environment for me to work with Kubernetes GitOps style deployments. While it was originally using k3s, I've moved it to kubeadm for greater flexibility.

The design assumes a single control plane node with multiple workers. While having all three nodes as control plane is feasible, the modifications to the manifests haven't been done so it isn't supported in this repository.

## Cilium

Cilium is used for the CNI and service mesh. It recently migrated to be installed via `helm`. Its configuration makes it not only the CNI but also the layer 2 load balancer (ARP) and ingress controller. Gateway API should be configured but isn't tested.

## ArgoCD

Installing ArgoCD in this environment is probably a 2 step process. First, install the CRDs, then Argo.

TODO:

- Add applications
- Make the application I have work better
- Add multi-environment selectors for AppSet
- Allow for Argo to enable/disable for an application per cluster
