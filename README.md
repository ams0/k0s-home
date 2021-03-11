# k0s-home

Install an home cluster with k0s(ctl)

```bash
k0sctl apply -c cluster.yml

mkdir ~/.kube/ ; k0sctl kubeconfig -c cluster.yml > $HOME/.kube/config
kubectl cluster-info
```

