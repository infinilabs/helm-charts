# **Infinilabs Helm Charts**

## Usage

[Helm](https://helm.sh) must be installed to use the charts. Please refer to
Helm's [documentation](https://helm.sh/docs) to get started.

Once Helm has been set up correctly, add the repo as follows:

    ~ helm repo add infinilabs https://helm.infinilabs.com

If you had already added this repo earlier, run `helm repo update` to retrieve
the latest versions of the packages. You can then run `helm search repo
infinilabs` to see the charts.

Note: The default storageClass of these charts use is [local-path](https://github.com/rancher/local-path-provisioner). If you want use other StorageClass(installed), you can create `vaules.yaml` file that it contains 'storageClassName: \<storageClassName\>' and use it (eg. helm install -f values.yaml).

### Console

#### Quick Start

    ~ helm install console infinilabs/console -n <namespace>

#### Uninstall
    ~ helm uninstall console -n <namespace>
    ~ kubectl delete pvc console-data-console-0 console-config-console-0 -n <namespace>

### Easysearch

#### Prerequisites

+ [cert-manager](https://cert-manager.io/docs/installation/)

#### Quick Start

    ~ cat << EOF | kubectl apply -n <namespace> -f -
    apiVersion: cert-manager.io/v1
    kind: Issuer
    metadata:
      name: easysearch-ca-issuer
    spec:
      selfSigned: {}
    ---
    apiVersion: cert-manager.io/v1
    kind: Certificate
    metadata:
      name: easysearch-ca-certificate
    spec:
      commonName: easysearch-ca-certificate
      duration: 87600h0m0s
      isCA: true
      issuerRef:
        kind: Issuer
        name: easysearch-ca-issuer
      privateKey:
        algorithm: ECDSA
        size: 256
      renewBefore: 2160h0m0s
      secretName: easysearch-ca-secret
    EOF

    ~ helm install easysearch infinilabs/easysearch -n <namespace>
  
#### Uninstall
    ~ helm uninstall easysearch -n <namespace>
    ~ kubectl delete pvc easysearch-data-easysearch-0 easysearch-config-easysearch-0 -n <namespace>

### Gateway

#### Prerequisites

+ [Easysearch](#Easysearch)

#### Quick Start

    ~ helm install gateway infinilabs/gateway -n <namespace>

#### Uninstall
    ~ helm uninstall gateway -n <namespace>
    ~ kubectl delete pvc gateway-data-gateway-0 -n <namespace>