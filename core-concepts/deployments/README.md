# Kubernetes Commands and Files

### This repository contains various commands to work with kubernetes

### Deployments

- Check number of deployments present in system

```sh
    kubectl get deployment
```
- Delete Deployment

```sh
    kubectl delete deployment <deployment-name>
```
- Information about the Deployment
```sh
    kubectl describe deployments 
```
- Scale a deployment
```sh
    kubectl scale deployments/<deployment-name>  --replicas=4
```
- Information about deployment
```sh
    kubectl describe deployments/<name>
```
- Update a deployment image
```sh
    kubectl set image deployments/<deployment-name>   <container-name>=<new image name>
```
- Rollout status
```sh
    kubectl rollout status deployments/<deployment-name>   
```
- Rollback deployment
```sh
    kubectl rollout undo deployment/<deployment-name>
```
- Edit Deployment
```sh
    kubectl edit deployment.v1.apps/nginx-deployment
```
- Run deployment with replicas
```sh
    kubectl run <pod-name> --image=<image name> --replicas=<no of replicas>
    
    kubectl create deployment <deployment name> --image=<image name>
```

- Get deployment yaml
```sh
kubectl create deployment nginx --image=nginx --dry-run=client -o yaml > nginx-deploy.yaml
```

- Set label of deployment
```
kubectl create deployment my-dep -o yaml --dry-run=client | kubectl label --local -f - environment=qa -o yaml | kubectl create -f -
```