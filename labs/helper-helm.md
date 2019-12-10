# Helper: Helm CLI Commands

<!-- TOC -->
- [Helper: Helm CLI Commands](#helper-helm-cli-commands)
  - [Delete package (Optional)](#delete-package-optional)
  - [Install remote charts](#install-remote-charts)
- [Upload Helm Chart to ACR](#upload-chart-ACR) ]

## Delete package (Optional)

```sh
# helm del <chartname>
$ helm del vote

release "vote" deleted
```

For Helm 3
```sh
# helm uninstall <chartname>
$ helm uninstall vote

release "vote" uninstalled
```



## Install remote charts

```sh
$ helm install https://myhelmrepo001.blob.core.windows.net/helmrepo/azure-voting-app-0.1.0.tgz -n vote-dev

$ helm install https://myhelmrepo001.blob.core.windows.net/helmrepo/azure-voting-app-0.1.0.tgz -n vote-dev \
    --set azureVoteFront.service.type=ClusterIP,ingress.enabled=true,ingress.host=vote.486f848139314d26aeef.japaneast.aksapp.io,azureVoteFront.deployment.image=yoichika.azurecr.io/azure-voting-app-front,azureVoteFront.deployment.imageTag=latest
```
## Upload chart ACR
Configure the Azure CLI defaults with the name of your Azure Container Registry

```sh
az configure --defaults acr=<acrName>
```

Now add your Azure Container Registry Helm chart repository to your Helm client
```sh
az acr helm repo add
```

- https://docs.microsoft.com/en-us/azure/container-registry/container-registry-helm-repos
- https://helm.sh/docs/topics/charts/

---
[Top](../README.md)
