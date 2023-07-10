# CKA commands and files

## This repository contains various commands to work with kubernetes

## KubeConfig

- Kubeconfig file has 3 components
```sh
Clusters: Different clusters user has access to

Users: User account which user has access, these users can have different privileges

Context: Which user account has access to which cluster
```

- View config
```sh
kubectl config view
```

- Switch context
```sh
kubectl config use-context {CONTEXT}
```

- Use kubeconfig flag to use another kube config
```sh
kubectl config view --kubeconfig={FILE PATH}
```

- Mergin two kubeconfigs
```sh
backup existing config
cp ~/.kube/config ~/.kube/config.bak

merge and get new config
KUBECONFIG=~/.kube/config:/path/to/new/config kubectl config view --flatten > /tmp/config

replace old config
mv /tmp/config ~/.kube/config 
```