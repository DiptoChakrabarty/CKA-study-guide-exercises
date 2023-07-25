# CKA commands and files

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

## Questions and Solutions

- Solution in cluster-role-binding.yaml
```
You have been tasked with granting the 'cluster-admin' role to a user named 'cluster-admin' in your Kubernetes cluster. This role should provide extensive permissions to manage nodes in the cluster.

Create a ClusterRole named 'cluster-admin' with the following permissions:

API group: [""]
Resource: ["nodes"]
Verbs: ["list", "get", "create", "delete"]
Bind the ClusterRole 'cluster-admin' to the user 'cluster-admin' using a ClusterRoleBinding named 'cluster-admin-role-binding'.
```

- Solution in imperative commands
<details><summary>show</summary>
<p>
    
```bash
# Step 1: Create the 'cluster-admin' ClusterRole
kubectl create clusterrole cluster-admin --verb=list,get,create,delete --resource=nodes

# Step 2: Bind the 'cluster-admin' ClusterRole to the 'cluster-admin' user using ClusterRoleBinding
kubectl create clusterrolebinding cluster-admin-role-binding \
  --clusterrole=cluster-admin \
  --user=cluster-admin

# Step 3: Test the access
kubectl auth can-i list nodes --as cluster-admin
kubectl auth can-i get nodes --as cluster-admin
kubectl auth can-i create nodes --as cluster-admin
kubectl auth can-i delete nodes --as cluster-admin
```

</p>
</details>