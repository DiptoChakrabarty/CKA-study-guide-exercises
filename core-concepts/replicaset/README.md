# CKA commands and files



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