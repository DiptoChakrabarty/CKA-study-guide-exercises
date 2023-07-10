# CKA commands and files



### OS Upgrade

- Pod Eviction Time : Time for a terminated pod to come back up

- Remove all pods from a node
```sh
kubectl drain {node name}
```

- Make a node unschedulable
```sh
kubectl cordon {node name}
```

- Make a node schedulable again
```sh
kubectl uncordon {node name}
```

- Drain a node ignoring daemonsets
```sh
kubectl drain {node name} --ignore-daemonsets
```

- Pods not part of replicaset are lost forever if their nodes are drained