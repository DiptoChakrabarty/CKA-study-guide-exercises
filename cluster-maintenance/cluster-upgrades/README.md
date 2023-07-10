# CKA commands and files



### Cluster Upgrade

- Upgrade of cluster requires two steps
    * upgrade of master nodes
    * upgrade of worker nodes

- [Upgrading Kubeadm Clusters](https://kubernetes.io/docs/tasks/administer-cluster/kubeadm/kubeadm-upgrade/)

- Check latest version of kubeadm available and upgrade plan
```sh
kubeadm upgrade plan
```

- Install specific version of kubeadm and kubelet
```sh
update apt beforehand
apt install kubeadm=1.20.15-00
apt install kubelet=1.20.0-00

check if installation possible with upgrade plan command
```

- Worker nodes have same steps just have to updated from ssh into them