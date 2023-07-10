# CKA commands and files

### This repository contains various commands and concepts to work with kubernetes

### Schedulers

- A nodename is assigned to a pod automatically by kubernetes which points which node a pod is created
- Users can explicitly assign nodename to a pod
- NodeName unlike image cannot be modified for a pod
- To change the node of a pod a pod binding request is sent to kubernetes

- Get scheduler and controller status
```sh
kubectl get componentstatus
```
