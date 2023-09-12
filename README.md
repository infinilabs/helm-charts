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

    helm install console infinilabs/console


### Easysearch

#### Quick Start

    helm install easysearch infinilabs/easysearch