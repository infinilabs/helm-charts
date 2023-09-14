# **Infinilabs Helm Charts**

## Usage

[Helm](https://helm.sh) must be installed to use the charts. Please refer to
Helm's [documentation](https://helm.sh/docs) to get started.

Once Helm has been set up correctly, add the repo as follows:

    helm repo add infinilabs https://helm.infinilabs.com

If you had already added this repo earlier, run `helm repo update` to retrieve
the latest versions of the packages. You can then run `helm search repo
infinilabs` to see the charts.

### Console

#### Quick Start

    helm install console infinilabs/console -n <namespace>

#### Uninstall
    helm uninstall console -n <namespace>
    kubectl delete pvc console-data-console-0 console-config-console-0 -n <namespace>

### Easysearch

#### Prerequisites

+ [cert-manager](https://cert-manager.io/docs/installation/)
+ [local-path](https://github.com/rancher/local-path-provisioner)

Note: If you want use other StorageClass(installed), you can create `vaules.yaml` file that it contains 'storageClassName: \<storageClassName\>' and use it (eg. helm install -f values.yaml).

#### Quick Start

    helm install easysearch infinilabs/easysearch -n <namespace>
  
#### Uninstall
    helm uninstall easysearch -n <namespace>
    kubectl delete pvc easysearch-data-easysearch-0 easysearch-config-easysearch-0 -n <namespace>
