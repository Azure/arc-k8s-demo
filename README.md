# Official cluster configuration sample for Azure Arc enabled Kubernetes

This repository contains sample Kubernetes manifest files that can be deployed using GitOps to an Azure Arc enabled Kubernetes cluster.

## Contents

| File/folder       | Description                                |
|-------------------|--------------------------------------------|
| `README.md`       | This README file. |
| `cluster-apps`    | Contains an example application that should be deployed to every cluster. |
| `namespaces`    | Contains three namespace resources to provision on an attached cluster. |
| `team-a`    | Contains a ConfigMap resource written into `team-a` namespace, communicates configuration data for the application team. |
| `CODE_OF_CONDUCT.md` | Microsoft code of conduct. |
| `LICENSE`         | The license for the sample. |

## Prerequisites

One or more Kubernetes clusters are [connected to Azure Arc](https://docs.microsoft.com/en-in/azure/azure-arc/kubernetes/connect-cluster) using the `connectedk8s` Azure CLI extension.

## Running the sample

Create a GitOps configuration referencing this sample repo by using the Azure CLI extension `k8sconfiguration` or Azure portal. Complete documentation on the available options can be found [here](https://docs.microsoft.com/en-in/azure/azure-arc/kubernetes/use-gitops-connected-cluster).

After a configuration is created, Azure Arc enabled Kubernetes will instantiate the resources described in this repository. This includes creating namespaces, deploying an example workload, and a config map.

```console
az k8sconfiguration create \
    --name cluster-config \
    --cluster-name ${CLUSTER_NAME} --resource-group ${RESOURCE_GROUP} \
    --operator-instance-name cluster-config --operator-namespace cluster-config \
    --repository-url https://github.com/Azure/arc-k8s-demo \
    --scope cluster --cluster-type connectedClusters
```

## Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.opensource.microsoft.com.

When you submit a pull request, a CLA bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.
