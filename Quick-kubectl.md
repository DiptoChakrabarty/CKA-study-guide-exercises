# Advanced Kubectl commands

## Aliases for the exam
```
export do='--dry-run=client -o yaml'
export now='--force --grace-period 0'
export yl='-o yaml'
export kn='-n kube-system'

```

- Get json values
```
kubectl get nodes -o json
```

- Use json path to get node names
```
kubectl get nodes -o=jsonpath='{.items[*].metadata.name}'
```

- get all users kubeconfig
```
kubectl config view --kubeconfig=/root/my-kube-config -o jsonpath='{.users[*].name}'
```

- sort pv by storage capacity
```
kubectl get pv --sort-by=spec.capacity.storage
```

- getting output with custom columns and names
```
kubectl get pv --sort-by=spec.capacity.storage -o custom-columns=NAME:.metadata.name,CAPACITY:.spec.capacity.storage
```

- find name of context of user aws-user
```
kubectl config view --kubeconfig=my-kube-config -o jsonpath="{.contexts[?(@.context.user=='aws-user')].name}"
```

- create a pod and expose it (make svc automatic)
```
kubectl run httpd --image=httpd:alpine --port=80 --expose
```

- Get deployment name, replicasready and order by deployment name with custom columns
```
kubectl get deploy -o custom-columns=DEPLOYMENT:.metadata.name,CONTAINER:.spec.template.spec.containers[0].image,REPLICAS_READY:.status.readyReplicas --sort-by=.metadata.name
```

- Set selector of svc
```
kubectl set selector --local -f - 'tier=messaging'
```
