# CKA commands and files



### Static Pods

- In kube-system namespaces pods appended with name of controlplane are static pods

- Static pods file location
```sh
- Check kubelet process : ps -aux | grep kubelet
- Read kubelet conf file
- Parameter called staticPodPath has static pods path : /etc/kuberenetes/manifests
```
- Place static pod manifests in staticPodPath in system

- To delete a static pod from a node remove the static pod definition file from static pod path of that node
