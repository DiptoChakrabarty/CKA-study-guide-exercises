# CKA commands and files

## This repository contains various commands to work with kubernetes

## ServiceAccounts

- Creating a service account
```sh
kubectl create serviceaccount developer
```

- service-account.yaml is a service account, serviceacct-role.yaml is role rules for service account, serviceacct-rolebinding.yaml is rolebinding of role and serviceaccount

- In deployment under spec.spec serviceAccountName field is used to set serviceaccount

- Set service account for deployment
```
kubectl set serviceaccount deploy/{deployment name}
```

- Create token for sa
```
kubectl create token {sa-name}
```

- Create service account imperative command
```
kubectl create serviceaccount pvviewer --dry-run=client -o yaml > svc-act.yaml
```

## Questions and Solutions

- Solution in service-account-sam.yaml
```
You are tasked with implementing Role-Based Access Control (RBAC) in your Kubernetes cluster to restrict the permissions of a specific ServiceAccount named 'sam-acct'. The ServiceAccount should have limited access to resources within the 'default' namespace.

Update the existing Role 'sam-role' to grant read (get) access to the 'pods' resource in addition to the existing permissions.

Create a new Role named 'secret-reader-role' that allows the ServiceAccount 'sam-acct' to only read (get) Secrets within the 'default' namespace.

Create a RoleBinding named 'secret-reader-binding' to bind the 'secret-reader-role' to the 'sam-acct' ServiceAccount within the 'default' namespace.
```

- Solution using imperative commands

<details><summary>show</summary>
<p>
    
```bash
kubectl create serviceaccount sam-acct
# create the service account

kubectl create role sam-role --verb=create,delete,list --resource=pods,deployments,secrets,configmaps --namespace=default
# create the role

kubectl create rolebinding sam-rolebinding --role=sam-role --serviceaccount=default:sam-acct
# create the role binding

# test it
kubectl auth can-i create pods --as=system:serviceaccount:default:sam-acct
kubectl auth can-i get pods --as=system:serviceaccount:default:sam-acct
kubectl auth can-i get secrets --as=system:serviceaccount:default:sam-acct
```

</p>
</details>