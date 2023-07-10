# CKA commands and files



### Monitoring and Logging

- kubectl top node : Command to check node memory and cpu usage

- kubectl top node --sort-by='memory' --no-headers | head -1 : node with higest memory usage

- kubectl top pod --sort-by='memory' : pod with highest memory usage

- add head -1 or tail -1 to get topmost or lowest

- kubectl logs -f {pod name} - check logs of a pod

- kubectl logs -f {pod name} {container name} -  when pod has multiple containers