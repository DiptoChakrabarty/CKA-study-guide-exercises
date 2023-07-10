# CKA commands and files

## Network Policies

- Ingress : Rule defined pod allows incoming traffic from api pod and api pod can read the results back from query

- Egress: Rule defined pod is allowed is to do api calls to allowed pods

- Get all network policies
```
kubectl get netpol
```

## Scenarios

- Allow ingress connections from backend pods in backend namespace to frontend pods in frontend namespace - > frontend_backend_8080.yaml

- Restrict all inbound traffic in database pod except from admin pod -> database_admin_pod.yaml

- Allow egress traffic from frontend namespace to ip address range -> egress_frontend_cidr.yaml

- Allow ingress trafic from app namespace to db namespace pods on port 3306 -> app_db_3306.yaml

- Allow ibound and outbound traffic from specific namespace -> allow_all_policy.yam
