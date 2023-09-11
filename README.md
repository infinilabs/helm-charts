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

    helm install infini-console infinilabs/console


### Easysearch

#### Quick Start

    cat << EOF | kubectl apply -f -
    apiVersion: cert-manager.io/v1
    kind: Issuer
    metadata:
      name: issuer-ca
    spec:
      selfSigned: {}
    ---
    apiVersion: cert-manager.io/v1
    kind: Certificate
    metadata:
      name: certificate-ca
    spec:
      commonName: certificate-ca
      duration: 87600h0m0s
      isCA: true
      issuerRef:
        kind: Issuer
        name: issuer-ca
      privateKey:
        algorithm: ECDSA
        size: 256
      renewBefore: 2160h0m0s
      secretName: ca-secret

    helm install infini-easysearch infinilabs/easysearch