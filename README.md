# WISCH Kubernetes Cluster

How to:

```bash
flux bootstrap github --components-extra=image-reflector-controller,image-automation-controller --read-write-key --owner=WISVCH --repository=gke-cluster --branch=main --path=./clusters/release
```

The rest is magic, for now.

## Age

Age is used for secret encryption.
The public key is: `age1ug2fepnvaqsfpn7t5gjjh2l0j8074jwh9h50pnjcjxn08v8pp3xq7ymxn2`.
