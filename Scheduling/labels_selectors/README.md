# CKA commands and files

## Labels and Services

- Get labels of Pods

```sh
    kubectl get pods --show-labels
```
- Label a  Pod

```sh
    kubectl run --generator= run-pod/v1  redis-pod --image=redis:alpine  -l tier=db
```
- Get pods with env=dev

```sh
    kubectl get pods --selector env=dev
```

- Get pods with label bu

```sh
    kubectl get pods -l bu
```

- Get everything in env pod

```sh
    kubectl get all --selector env=pod
```

- Multiple Arguments

```sh
    kubectl get pods -l environment=production,tier=frontend

    here value is in bracket and key in left
    kubectl get pods -l 'environment in (production),tier in (frontend)'

```