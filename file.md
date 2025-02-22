# Kubernetes ResourceQuota and LimitRange (Imperative Commands)

## 1. Set ResourceQuota for a Namespace
```sh
kubectl create quota dev-quota \
  --hard=cpu=1,memory=1Gi,pods=10,requests.cpu=500m,requests.memory=512Mi,limits.cpu=1,limits.memory=1Gi \
  --namespace=dev --dry-run=client -o yaml > dev-quota.yaml

```

### Explanation:
- **`cpu=2`** → Maximum **1 CPUs**
- **`memory=4Gi`** → Maximum **1GiB Memory**
- **`pods=10`** → Maximum **10 Pods**

### Verify ResourceQuota:
```sh
kubectl get resourcequota dev-quota --namespace=dev
kubectl describe resourcequota dev-quota --namespace=dev
```

---

## 2. Set LimitRange for Pods in a Namespace
```sh
kubectl create limitrange dev-limits --namespace=dev \
  --pod-max=cpu=500m,memory=1Gi \
  --pod-min=cpu=100m,memory=128Mi
```

### Explanation:
- **`pod-max=cpu=500m,memory=1Gi`** → Maximum **500m CPU** and **1GiB Memory** per pod
- **`pod-min=cpu=100m,memory=128Mi`** → Minimum **100m CPU** and **128MiB Memory** per pod

### Verify LimitRange:
```sh
kubectl get limitrange dev-limits --namespace=dev
kubectl describe limitrange dev-limits --namespace=dev
```

---

### 📌 Notes:
- `ResourceQuota` helps in limiting resource usage at the **namespace level**.
- `LimitRange` helps in setting **minimum and maximum resource limits** per pod/container.
- Use these configurations to **prevent over-utilization** of resources in Kubernetes clusters.

---

✅ **Now you can use these commands to manage your Kubernetes resources efficiently!** 🚀
