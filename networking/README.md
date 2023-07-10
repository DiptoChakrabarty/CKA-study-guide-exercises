# CKA commands and files

### NetWorking

- Determine Ip Address
```sh
    ifconfig

    ip addr
```

- Find mac address of another node in network
```sh
    arp node
```

- No of Requests in a port
```sh

    netstat -tnlp | grep < port > | wc -l

```

- Network plugin for kubernetes and directory
```sh
    ps -aux | grep kubernetes

    /etc/cni/net.d
```

- Check gateway and destination
```sh
    route -n
```

- Default CNI binaries location : /opt/cni/bin

- Check CNI plugin used : /etc/cni/net.d/ (location)

- Check ip address range by cni plugin used: ip addr show weave \\example