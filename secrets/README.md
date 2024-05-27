# Secrets

This folder contains all the secrets that are used by deployments.
The secrets are encrypted using [mozilla sops](https://github.com/mozilla/sops) with the following public key of the cluster:

```
age1ug2fepnvaqsfpn7t5gjjh2l0j8074jwh9h50pnjcjxn08v8pp3xq7ymxn2
```

## Creating a new secret

To create a new secret:

1. Create a template file without any secrets in the `templates` folder and name it `{name}.tpl.yaml`.
2. Copy this file in the `secrets` directory (removing the `tpl` extension part) and fill in the secrets.
3. Use `sops` to encrypt the secrets file.

```bash
sops --age=age1ug2fepnvaqsfpn7t5gjjh2l0j8074jwh9h50pnjcjxn08v8pp3xq7ymxn2 --encrypt --encrypted-regex '^(data|stringData)$' --in-place {name}.yaml
```

The cluster will automatically decrypt the secrets with its private key during runtime.

## Editing existing secrets

To edit an already encrypted file, set the private key in the `SOPS_AGE_KEY` environment variable, and use the `sops` command to edit the file:

```bash
sops {name}.yaml
```

When you exit the editor, the file will be encryped and saved, overwriting the previous file.