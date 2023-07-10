# CKA commands and files



### Authentication

#### Auth Mechanisms

- Static username and passwords
- Username and token
- Service accounts

#### TLS Certificates

This is process of creating client certificates

- Certficate Creation process for certificate authority (openssl here)
```sh
generate the keys 
openssl genrsa -out ca.key 2048

sign the certificates
openssl req -new -key ca.key -subj "/CN=KUBERNETES-CA" -out ca.csr

sign the certificates
openssl x509 -req -in ca.csr -signkey ca.key -out ca.crt
```

- Certificate creation for admin user
```sh
generate the keys 
openssl genrsa -out admin.key 2048

sign the certificates
openssl req -new -key admin.key -subj "/CN=kube-admin" -out admin.csr

sign the certificates
openssl x509 -req -in admin.csr -CA ca.crt -CAkey ca.key -out admin.crt
```

- To find certificates of apiserver kubelet etc
```sh
Check manifests files from /etc/kubernetes/manifests/
```

- Check certificate details using command
```sh
openssl x509 -in {crt path}crt -text -noout

Subject CN is common name of the certificate

Issuer CN is common name of issuer
```

- If kube api server down inspect docker logs for troubleshooting

#### Certificate API

- Convert cert to base64 in one line
```
cat {filepath}.csr | base64  -w 0
```

- Get the certificates
```sh
kubectl get csr
```

- Approve a certificate
```sh
kubectl certificate approve {certificate name}
```

- Check groups certificate applying to
```sh
kubectl get {csr-name} -o yaml
```