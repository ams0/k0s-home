# k0s-home

Install an home cluster with k0s(ctl)

```bash
k0sctl apply -c cluster.yml

mkdir -p ~/.kube/ && k0sctl kubeconfig -c cluster.yaml > $HOME/.kube/config
kubectl cluster-info ; kubectl get nodes
```

Install the ArgoCD root app and point it to the Github Repo:

```bash
kubectl create ns argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/ams0/argocd-apps/main/install.yaml
kubectl apply -f manifests/root-app.yaml

```

If some nodes don't come, try to hard clean them:

```
sudo systemctl stop containerd
sudo rm -R /etc/kubernetes/
sudo rm -R /var/lib/containerd/
sudo rm -R /var/lib/kubelet/
```

and reapply the configuration.

To reset the cluster:

```bash
k0sctl reset -f -c cluster.yaml
```

For the time being, create a secret for DD (using an env var for key); the helm chart will point to the secret

```bash
kubectl create secret generic datadog-secret --from-literal api-key=${DATADOG_APIKEY} --namespace="datadog"
```

