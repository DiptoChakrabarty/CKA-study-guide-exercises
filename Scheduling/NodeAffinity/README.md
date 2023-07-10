# CKA commands and files

## NodeAffinity

- Types of NodeAffinity

```sh
    - requiredDuringSchedulingIgnoredDuringExecution : Place pods with matching labels only

    - preferredDuringSchedulingIgnoredDuringExecution : Prefer to place pod with matching labels else place elsewhere
```

- Label a node
```sh
  kubectl label node node01 <key>=<value>
```

- Check which pods are running on which nodes
```sh
    kubectl get pods -o wide
```

- Get node labels
```sh
 kubectl get nodes --show-labels
```

- Operators

```sh
 Equal : Must match key value pair of labels

 Exists: Check if key present in node label
```