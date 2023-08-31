# **Infinilabs Charts**

## 准备工作
下载 Infinilabs Charts 包
```
git clone https://git.infini.ltd:64443/infini/helm-charts.git
```

在 Kubernetes 上创建一个 namespace：
```
kubectl create ns infini
```

## Console

### 快速部署
```
cd chart/infini-console
#部署 Console Chart, 版本名称为 infini-console
helm install infini-console . -n infini
```

## Easysearch

### 快速部署
```
cd chart/infini-easysearch
#自签 CA 证书
kubectl apply -f ca-secret.yaml -n infini
#部署 Easysearch Chart, 版本名称为 infini-easysearch
helm install infini-easysearch . -n infini
```

### 配置文件
```
cat chart/infini-easysearch/values.yaml
...
#集群名称
clusterName: infinilabs
replicaCount: 3             
#主节点列表（默认版本名称是 infini-easysearch，如有变动需调整下面 masterHosts、discoverySeedHosts 值 ）
masterHosts: '"infini-easysearch-0","infini-easysearch-1","infini-easysearch-2"'
discoverySeedHosts: '"infini-easysearch-0.infini-easysearch-svc-headless","infini-easysearch-1.infini-easysearch-svc-headless","infini-easysearch-2.infini-easysearch-svc-headless"'
#节点角色（可按需调整）
nodeRoles: '"master","data","ingest","remote_cluster_client"'
...
storageClassName: local-path
dataVolumeStorage: 100Gi
```
