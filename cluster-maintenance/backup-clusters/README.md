# CKA commands and files



### Backup of Clusters

- Keep yaml file of all resource grps
```sh
kubectl get all --all-namespaces -o yaml > all-resources.yaml
```

### Backing up ETCD

- Backup the etcd of the cluster
```sh
ETCDCTL_API=3 etcdctl snapshot save snapshot.db
```

- View backup status
```sh
ETCDCTL_API=3 etcdctl snapshot status snapshot.db
```

- Restore backup
```sh
Stop kubeapiserver service
- service kube-apiserver stop

Restore cluster
ETCDCTL_API=3 etcdctl snapshot restore snapshot.db\
--data-dir /var/lib/etcd-from-backup
This creates new data directory

Reload daemon and restart etcd and kube api server service
systemctl daemon reload

service etcd kube-apiserver restart

For all etcdctl commands specify the folloing
--endpoint=[127.0.0.1:2379] :This is the default as ETCD is running on master node and exposed on localhost 2379.
--cacert : verify certificates of TLS-enabled secure servers using this CA bundle
--cert : identify secure client using this TLS certificate file
--key : identify secure client using this TLS key file
```

- Example of snapshot save
```sh
etcdctl snapshot save /opt/snapshot-pre-boot.db \
> --endpoints=https://[127.0.0.1]:2379 \
> --cacert=/etc/kubernetes/pki/etcd/ca.crt \
> --cert=/etc/kubernetes/pki/etcd/server.crt \
> --key=/etc/kubernetes/pki/etcd/server.key
```

- Example of backup
```sh
ETCDCTL_API=3 etcdctl snapshot restore  /opt/snapshot-pre-boot.db --data-dir=/etc/restore-etcd

Edit etcd config file /etc/kubernetes/manifests/etcd.yaml

Change the mount path of etcd-data volume to take old config

volumes:
  - hostPath:
      path: /etc/restore-etcd
      type: DirectoryOrCreate
    name: etcd-data
```

- To check etcd version
```sh
Check logs of etcd pods

Check etcd process

Check image used by etcd
```

- Listening address to reach etcd : listen-client-url flag