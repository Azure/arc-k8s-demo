---
page_type: sample
languages:
- yaml
products:
- azure-arc
description: "Example repository for Azure Arc enabled Kubernetes"
urlFragment: "update-this-to-unique-url-stub"
---

# Official sample for Azure Arc enabled Kubernetes

This repository is an example of a basic GitOps repository that can be used with Azure Arc enabled Kubernetes.

## Contents

Outline the file contents of the repository. It helps users navigate the codebase, build configuration and any related assets.

| File/folder       | Description                                |
|-------------------|--------------------------------------------|
| `README.md`       | This README file. |
| `cluster-apps`    | Contains an example application that should be deployed to every cluster. |
| `namespaces`    | Contains three namespace resources to provision on an attached cluster. |
| `policy`    | Example policy definition for applying GitOps configurations to a cluster. |
| `team-a`    | Contains a ConfigMap resource written into `team-a` namespace, communicates configuration data for the application team. |
| `CODE_OF_CONDUCT.md` | Microsoft code of conuct. |
| `LICENSE`         | The license for the sample. |

## Prerequisites

This repository is attached to one or more Azure Arc enabled Kubernetes clusters.

## Running the sample

Create a GitOps configuration by using the Azure CLI extension `k8sconfiguration` referencing this sample repo.

After a configuration is created Azure Arc enabled Kubernetes will instantiate the resources described in this repository. Which includes creating namespaces, deploying an example container, and updating a config map.

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
