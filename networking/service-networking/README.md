# CKA commands and files

## This repository contains various commands to work with kubernetes

## Service NetWorking

- Nodes IP Address range : same as eth0 range as host

- Pods IP Address range : check ipalloc in logs of networking runtime pod

- Service IP Address range : kubeapi server yaml cluster ip range
cat /etc/kubernetes/manifests/kube-apiserver.yaml | grep cluster-ip-range

- all binaries : /opt/cni/bin

- Networking solution : /etc/cni/net.d
