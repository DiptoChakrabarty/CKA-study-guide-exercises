# CKA commands and files

## This repository contains various commands to work with kubernetes

## Image Security

- Create a secret to hold private registry details
```sh
kubectl create secret docker-registry regcred \
--docker-server=${SERVER URL} \
--docker-username=${REGISTRY USERNAME} \
--docker-password=${REGISTRY PASSWORD} \
--docker-email=${REGISTRY EMAIL}
```