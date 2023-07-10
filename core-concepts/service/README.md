# CKA commands and files



### Services

- Types of Services

```sh
 1) NodePort : makes internal port accessible
 2) ClusterIp : creates virtual ip inside cluster
 3) LoadBalancer: provides loadbalancer to app
 ```
 
 - Port Forward
 ```sh
 kubectl port-forward svc/nginx-demo 8000:80
 ```

 - Get a template ready
```sh
kubectl create svc clusterip redis --tcp=8080:9090 --dry-run=client -o yaml > service.yaml
```

- Expose a pod
```sh
kubectl expose pod redis --port=6379 --name=redis-service
```

- Expose pod or deployment as nodeport
```
kubectl expose deploy {deploy name} --name={svc name} --port={port} --type=NodePort --protocol=TCP
```

- Create service and attach selector
```
kubectl create svc clusterip messaging-service --tcp=6379:6379 --dry-run=client -o yaml | kubectl set selector --local -f - 'tier=messaging' -o yaml | kubectl create -f -
```

- Get nslookup command from within cluster of svc
```
kubectl run  test-nslookup --image=busybox:1.28 -it --restart=OnFailure -- nslookup nginx-resolver-service

for pods replace with pod ip

kubectl run  test-nslookup --image=busybox:1.28 -it --restart=OnFailure -- nslookup {pod IP}
```