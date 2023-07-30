# CKA commands and files

## Ingress

- Create ingress imperative command
```
kubectl create ingress {ingress name} --rule="{host}/path={service}:{port}"
```

- Ingress of multiple paths same host
```
kubectl create ingress {ingress name} --class=default \
--rule="{host}/={service1}:port" \
--rule="{host}/admin/={service2}:portadmin"
```

## Questions and Solutions

- Solution in my-web-app.yaml
```
deploy a web application named "my-web-app" that listens on port 80. Create an Ingress resource to route incoming traffic to the "my-web-app" service.
```

- Solution in app-ingress.yaml
```
You have been assigned to configure Ingress resources to route traffic for multiple web applications in your Kubernetes cluster. There are two services, "app-a" and "app-b," that need to be accessible using different paths. Additionally, the applications should be reachable using host-based routing for specific domains.

You are required to set up the Ingress resources as follows:

For the "app-a" service, create an Ingress resource that should be accessible at the path "/appA" and should respond to the domain "app-a.example.com".

For the "app-b" service, create an Ingress resource that should be accessible at the path "/appB" and should respond to the domain "app-b.example.com".

Ensure that the services are correctly exposed and the paths and domains are configured accurately.

Write the YAML manifests for the required Ingress resources to fulfill the above requirements. Save the files as "app-a-ingress.yaml" and "app-b-ingress.yaml".
```

- Solution in web-app-rewrite.yaml
```
You have deployed a web application named "my-web-app" in your Kubernetes cluster. Configure the Ingress resource to rewrite the path "/app" to "/new-app" before routing traffic to the "my-web-app" service.

Write the YAML manifest for the required Ingress resource with the path rewriting configuration. Save the file as "my-web-app-ingress.yaml".
```