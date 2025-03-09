# k8s + nextcloud + postgres

## Prerequisites

- [Docker](https://docs.docker.com/get-docker/)
- [Kubernetes](https://kubernetes.io/docs/setup/)
- [Helm](https://helm.sh/docs/intro/install/)


## Installation

```bash
k create ns nextcloud
helm repo add nextcloud https://nextcloud.github.io/helm/
helm install my-release nextcloud/nextcloud -f ./values.yaml -n nextcloud
```

## Access

```bash
kubectl get secret --namespace nextcloud my-release-nextcloud -o jsonpath="{.data.nextcloud-password}" | base64 --decode
```
admin/password


## Uninstall

```bash
helm uninstall my-release -n nextcloud
k delete ns nextcloud
```