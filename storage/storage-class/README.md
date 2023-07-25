# CKA commands and examples

## Questions and Solutions

- Solution in app-data.yaml
```
Your Kubernetes cluster has been set up with a dynamic storage provisioner supporting the 'ReadWriteMany' access mode. You need to deploy a stateful application that requires read-write access from multiple pods simultaneously.

1) Create a Storage Class named 'fast-storage' with the following specifications:

Provisioner: 'your-provisioner'
Access mode: ReadWriteMany
reclaimPolicy: Delete

2) Create a Persistent Volume Claim named 'app-data-pvc' with the following specifications:

Storage Class: 'fast-storage'
Access mode: ReadWriteMany
Requested storage: 5Gi

3) Create a StatefulSet named 'app-data-statefulset' with the following configuration:

Replicas: 3
Template with a single container named 'app-container' running an image 'busybox:latest'.
Environment variable 'DATA_PATH' set to '/data' in the container.
A volume named 'app-data-volume' mounted at the path '/data' within the container. This volume should use the 'app-data-pvc' PVC.
Write the YAML manifest for the Storage Class, PVC, and StatefulSet and save it as 'app-data.yaml'.

```