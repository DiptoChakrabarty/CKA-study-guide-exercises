# Kubernetes Commands and Files

## This repository contains various commands to work with kubernetes

## Cluster Role and Cluster Role Binding

- Get api Groups for different resources
```sh
kubectl api-resources | grep {resource name}
```

-  Make clusterrolebinding imperative
```
kubectl create clusterrolebinding pvviewer-role-binding --serviceaccount=pvviewer --clusterrole=pvviewer-role --dry-run=client -o yaml > clb.yaml
```

- Make clusterrole
```
kubectl create clusterrole pvviewer-role --verb=list --resource=persistentvolume --dry-run=client -o yaml > cl-rol.yaml
```