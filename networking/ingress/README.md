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

- Imperative command example
```
You need to configure an Ingress resource to route incoming traffic for a web application named "my-web-app". The application should listen on port 80 and should be accessible using the domain "my-web-app.example.com".
```
<details><summary>show</summary>
<p>

```bash
# Step 1: Create the Ingress resource
kubectl create ingress my-web-app-ingress \
  --rule="my-web-app.example.com/*=my-web-app:80"

```
</p>
</details>

- Example of ingress patch
```
You are managing a Kubernetes cluster with two web applications, "app-a" and "app-b". The applications need to be accessible using the same domain "my-apps.example.com", but they should respond to different paths. The "app-a" service should be reachable at the path "/appA", and the "app-b" service should be reachable at the path "/appB".
```

<details><summary>show</summary>
<p>

```bash
# Step 1: Create the Ingress resource for app-a with the path "/appA"
kubectl create ingress my-apps-ingress \
  --rule="my-apps.example.com/appA=app-a:80"

# Step 2: Add a new rule to the existing Ingress resource for app-b with the path "/appB"
kubectl patch ingress my-apps-ingress \
  --patch='{"spec":{"rules":[{"host":"my-apps.example.com","http":{"paths":[{"path":"/appB","pathType":"Prefix","backend":{"service":{"name":"app-b","port":{"number":80}}}}]}}]}}'

```
</p>
</details>

