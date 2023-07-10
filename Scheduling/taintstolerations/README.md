# CKA commands and files



### Taints and Tolerations

- Taint Effects

```sh
    1) NoSchedule : Pod not scheduled on nodes
    2) PreferNoSchedule : try to avoid placing pods
    3) NoExecute : new pods not scheduled and existing pods evicted if do not tolerate taint

Taints and Tolerations only allow node to accept a pod , it does not restrict which node the pod will be scheduled in
```
 - Taint Nodes

 ```sh
    kubectl taint nodes <node name>  key=value: taint-effect

    kubectl taint node node1 app=blue:NoSchedule
```

- Check Taint on master node

```sh
    kubectl describe node kubemaster | grep Taint
```

- Get taints in all nodes

```sh
    kubectl get nodes -o json | jq '.items[].spec.taints'

    kubectl describe nodes node1
```

- Remove taint from master node

```sh
    kubectl taint nodes master node-role.kubernetes.io/master : NoSchedule-

    add - at end to remove taint
```

- Operators

```sh
 Equal : Must match key value pair of labels

 Exists: Check if key present in node label
```