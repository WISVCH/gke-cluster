# The apps running on the cluster

## Release apps
This folder contains all regular end-user deployments of the cluster that are not considered infrastructure. A deployments folder should be mentioned in the `_clusters/release/kustomization.yaml` to be considered as an deployment that should be run on release.

## App
 An app folder is filled with three files:
  - image.yaml
  - kustomization.yaml
  - release.yaml

Each file has a different purpose:

### image.yaml
This file specifies the imagerepository and the imagepolicy for flux. Flux uses this information to pull and deploy a new image once one is present at the given image location. CH often uses `ghrc.io` which is git's package repository.

### kustomization.yaml
This file specifies which files kubernetes should consider for kubernetes in the specified folder.

### release.yaml
This file specifies the values given to the HelmRelease of the specified app. These values are then passed to the chart that is being used. One can reference secrets and assign them to a certain value if necessary.

example for secret importing:
```yaml
valuesFrom:
    - kind: Secret
      name: {secret_name}
      valuesKey: {key_of_secret}
      targetPath: {targetted_value_path}
```

## Charts
CH uses charts for templating deployments for this repo. The charts of CH can be found in: https://github.com/WISVCH/charts. Charts are a way to update deployment specifics for apps while also providing default values and version support. It is suggested to read up on Helm charts at: https://helm.sh/.
