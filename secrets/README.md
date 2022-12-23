# Secrets
This folder contains all the secrets that are used by deployments. These secrets can be changed by copying the `{name}.tpl.yaml`'s file content into the associated `{name}.yaml` file and filling in the secrets. One can then encrypt the file by using [mozilla sops](https://github.com/mozilla/sops) with the public key of the cluster: `age1ug2fepnvaqsfpn7t5gjjh2l0j8074jwh9h50pnjcjxn08v8pp3xq7ymxn2`. 

The encryption method decrypts the file in place. The commando used to encrypt is: 
```bash
sops --age=age1ug2fepnvaqsfpn7t5gjjh2l0j8074jwh9h50pnjcjxn08v8pp3xq7ymxn2 --encrypt --encrypted-regex '^(data|stringData)$' --in-place .\{name}.yaml
```

The cluster will automatically decrypt the secrets with its private key during runtime.
