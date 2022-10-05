# WISCH Kubernetes Cluster

How to:

```bash
flux bootstrap github --components-extra=image-reflector-controller,image-automation-controller --read-write-key --owner=WISVCH --repository=gke-cluster --branch=main --path=./clusters/release
```

The rest is magic, for now.
