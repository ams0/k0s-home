# k0s-home

Install an home cluster with k0s(ctl)

```bash
k0sctl apply -c cluster.yml

mkdir ~/.kube/ ; k0sctl kubeconfig -c cluster.yml > $HOME/.kube/config
kubectl cluster-info
```

Install the ArgoCD root app and point it to the Github Repo:

```bash

```

For the time being, create a secret for DD (using an env var for key); the helm chart will point to the secret

```bash
kubectl create secret generic datadog-secret --from-literal api-key=${DATADOG_APIKEY} --namespace="datadog"
```

