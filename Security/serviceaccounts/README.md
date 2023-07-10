# CKA commands and files

## This repository contains various commands to work with kubernetes

## ServiceAccounts

- Creating a service account
```sh
kubectl create serviceaccount developer
```

- service-account.yaml is a service account, serviceacct-role.yaml is role rules for service account, serviceacct-rolebinding.yaml is rolebinding of role and serviceaccount

- In deployment under spec.spec serviceAccountName field is used to set serviceaccount

- Set service account for deployment
```
kubectl set serviceaccount deploy/{deployment name}
```

- Create token for sa
```
kubectl create token {sa-name}
```

- Create service account imperative command
```
kubectl create serviceaccount pvviewer --dry-run=client -o yaml > svc-act.yaml
```