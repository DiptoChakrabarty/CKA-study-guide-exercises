# CKA commands and files



### Rolling Updates and Rollouts

- Check status of rollouts of deployment
```sh
kubectl rollout status deployment/myapp
```

- Rollout history
```sh
kubectl rollout history deployment/myapp
```

- Recreate Strategy scales down old deployment to 0 first then scales up with new deployment version

- Undo a Rollout
```sh
kubectl rollout undo deployment/myapp
```

- Record rolling update
```
kubectl set image deploy {deploy name} {container name}={new image} --record
```