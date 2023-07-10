# Kubernetes Commands and Files

### This repository contains various commands to work with kubernetes

### ReplicaSet

- Get all replicasets
```sh
kubectl get replicaset
```

- Scale ReplicaSet
```sh
kubectl scale --replicas=3 replicaset nginxrc
```

- Deleting a replicaset
```sh
kubectl delete replicaset nginxrc
```