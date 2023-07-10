# Kubernetes Commands and Files

## This repository contains various commands to work with kubernetes

## Ingress

- Create ingress imperative command
```
kubectl create ingress {ingress name} --rule="{host}/path={service}:{port}"
```

- Ingress of multiple paths same host
```
kubectl create ingress {ingress name} --class=default \
--rule="{host}/={service1}:port" \
--rule="{host}/admin/={service2}:portadmin"
```