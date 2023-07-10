# CKA commands and files



### Namespaces

- Find all pods of all namespaces

```sh
    kubectl get pods --all-namespaces
```

- Use pod of another namespace
```sh
    db-service.dev.svc.cluster.local

   - We are trying to access db-service pod of namespace dev from namespace default 
   - cluster local is domain name of cluster
   - svc is subdomain name
```

- Create a namespace

```sh
    kubectl create namespace dev
```

- Get pods of other namespace

```sh
    kubectl get pods --namespace=dev
```

- Switch to another namespace

```sh
    kubectl  config set-context $(kubectl config current-context) --namespace=dev
    
     kubectl  config set-context --current --namespace=dev
```
- Check current Namespace

```sh
 kubectl config view --minify --output 'jsonpath={..namespace}'
```

- Get all contexts

```sh
kubectl config get-contexts
```

- Delete namespace in terminating state

```sh
 kubectl get namespace {namespace} -o json > ns.json
 
 Remove kubernetes from finalizers in json
 
 kubectl replace --raw "/api/v1/namespaces/{namespace}/finalize" -f ./ns.json
```