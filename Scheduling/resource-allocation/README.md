# CKA commands and files



### Resource Limits and Requests

- ResourceWuota: Restrict CPU and memory usage in a namespae

- LimitRange : applies to individual containers

- Sort pods by cpu usage
```
kubectl top pods --sort-by=cpu
```