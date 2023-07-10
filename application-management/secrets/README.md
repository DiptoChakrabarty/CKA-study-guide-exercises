# Kubernetes Commands and Files

### This repository contains various commands to work with kubernetes

### Secrets

- Create secret from values
```sh
kubectl create secret generic db-secret --from-literal=DB_Host=sql01 --from-literal=DB_User=root --from-literal=DB_Password=password123
```

- Attach full secret directly to pod
```sh
envFrom:
    - secretRef:
        name: db-secret
```

- Get secrets file from imperative command
```sh
kubectl create secret generic db-secret --from-literal=DB_Host=sql01 --dry-run=client -o yaml
```