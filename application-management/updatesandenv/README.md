# CKA commands and files




### Rolling Updates and Rollbacks
- Update a  deployment

```sh

    kubectl  apply -f deploy-def.yml

    kubectl set image deployment/myapp nginx=nginx.1.9.1

```

- Rollout Status

```sh

    kubectl rollout status deployment/myapp

    kubectl rollout history deployment/myaoo

```

- RollBack

```sh
    kubectl rollout undo deployment/myapp

```

### Env files

Env variables can be defined using configmap

- Create configMap

```sh
    kubectl create configmap <configmap name>
```

- Create configmap declarative way

```sh
    kubectl create configmap <configmap-name> --from-literal=<key>=<value>
```
