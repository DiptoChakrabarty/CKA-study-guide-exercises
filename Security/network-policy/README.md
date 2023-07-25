# CKA commands and files

## Network Policies

- Ingress : Rule defined pod allows incoming traffic from api pod and api pod can read the results back from query

- Egress: Rule defined pod is allowed is to do api calls to allowed pods

- Get all network policies
```
kubectl get netpol
```

## Questions and Solutions

- Allow ingress connections from backend pods in backend namespace to frontend pods in frontend namespace - > frontend_backend_8080.yaml
```
You have a Kubernetes cluster with multiple namespaces. The "frontend" namespace contains frontend pods, and the "backend" namespace contains backend pods. You want to allow ingress traffic from the frontend pods to the backend pods on port 8080. Write the YAML file for the network policy.
```

- Restrict all inbound traffic in database pod except from admin pod -> database_admin_pod.yaml
```
: You have a Kubernetes cluster with a namespace named "data". There are sensitive database pods running in this namespace, and you want to restrict all inbound traffic except for a specific pod named "admin". Write the YAML file for the network policy.
```

- Allow egress traffic from frontend namespace to ip address range -> egress_frontend_cidr.yaml
```
You have a Kubernetes cluster with multiple namespaces. You want to allow egress traffic from a specific namespace named "frontend" to a specific IP address range 10.20.30.0/24. Write the YAML file for the network policy.
```

- Allow ingress trafic from app namespace to db namespace pods on port 3306 -> app_db_3306.yaml
```
You have a Kubernetes cluster with multiple namespaces. The "app" namespace contains frontend pods, and the "db" namespace contains database pods. You want to allow ingress traffic from the frontend pods to the database pods, but only on port 3306. Write the YAML file for the network policy.
```

- Allow ibound and outbound traffic from specific namespace -> allow_all_policy.yaml
```
You have a Kubernetes cluster with multiple namespaces. You want to create a network policy that allows all inbound and outbound traffic within a specific namespace named "internal". Write the YAML file for the network policy.
```