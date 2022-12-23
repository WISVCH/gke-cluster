# WISCH Kubernetes Cluster

Welcome to the WISVCH Kubernetes Cluster repo. This repository is a collection of config files that make up the currently running kubernetes cloud deployment of WISVCH. The kubernetes cluster uses:
 - Kubernetes
 - Fluxv2
 - Helm
 - Mozilla sops
 - The CH charts repository: https://github.com/WISVCH/charts
  
It is recommended to read up on Kubernetes, fluxV2 and Helm before contributing. 

## Quick start guide
Adding an application to the release cluster:
 - Make a pull request at https://github.com/WISVCH/charts with a new chart.  
 - Add the secrets to the `./secrets` folder according to the instructions of the README.md in that folder
 - Add the app to the `./apps` folder according to the instructions of the README.md in that folder


## Miscellaneous 

FLux was originally bootstrapped with the command:
```bash
flux bootstrap github --components-extra=image-reflector-controller,image-automation-controller --read-write-key --owner=WISVCH --repository=gke-cluster --branch=main --path=./clusters/release
```

Age is used for secret encryption.
The public key is: `age1ug2fepnvaqsfpn7t5gjjh2l0j8074jwh9h50pnjcjxn08v8pp3xq7ymxn2`.
