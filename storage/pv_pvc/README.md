# CKA commands and files

## Questions and Solutions
- Solution in dbvol_webapp.yaml

```
You are deploying a web application Pod named 'webapp' in your Kubernetes cluster. The web application requires persistent storage to store log files. You need to provision a Persistent Volume (PV) and a Persistent Volume Claim (PVC) for the application.

1) Create a Persistent Volume named 'dbvol' with the following specifications:

Storage class: manual
Reclaim policy: Retain
Capacity: 1Gi
Access mode: ReadWriteOnce
Host path: "/mnt/data"

2) Create a Persistent Volume Claim named 'dbvol' with the following specifications:

Storage class: manual
Access mode: ReadWriteOnce
Requested storage: 0.5Gi

3)Create the 'webapp' Pod, using the 'busybox' image, with the following configuration:

An environment variable 'LOG_HANDLERS' with the value 'file'.
A volume named 'log-vol' mounted at the path '/log' within the container. This volume should use the 'dbvol' PVC.

```