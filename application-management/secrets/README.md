# CKA commands and files

## Secrets Commands

- Create secret from values
```sh
kubectl create secret generic db-secret --from-literal=DB_Host=sql01 --from-literal=DB_User=root --from-literal=DB_Password=password123
```

- Attach full secret directly to pod
```sh
envFrom:
    - secretRef:
        name: db-secret
```

- Get secrets file from imperative command
```sh
kubectl create secret generic db-secret --from-literal=DB_Host=sql01 --dry-run=client -o yaml
```

## Questions and Solutions

- Soltuon in mysql-secret.yaml
```
You are deploying a mysql deployment in your Kubernetes cluster. It requires access to a mysql username and password.

Create a kubernetes secret named configsecret storing an username and password

Add the credentials to a mysql deployment which is running 2 replicas write it to a file mysql-secret.yaml
```

- Solution in web-app.yaml
```
You are deploying a multi-tier application in your Kubernetes cluster, and it requires access to sensitive information, such as API keys and passwords. To ensure the security of the application, you decide to use Kubernetes Secrets to manage the confidential data.

Create a Kubernetes Secret named 'app-secrets' to store the API key and password required by the application.

Create a Pod named 'app-pod' with two containers: 'web-app' and 'secrets-init'. The 'web-app' container runs your application, and the 'secrets-init' container uses the 'busybox' image.

Mount the 'app-secrets' Secret as volumes inside the 'secrets-init' container at the paths '/api-key' and '/password'.

Configure the 'secrets-init' container to copy the content of the mounted Secret volumes to the '/secrets' directory.

The 'web-app' container should use the environment variables 'API_KEY' and 'PASSWORD' to access the API key and password values.

Write the YAML manifest to create the 'app-secrets' Secret and the 'app-pod' with the appropriate containers and volumes.
```

- Solution in kubectl commands
```
You have an existing Kubernetes Secret named 'database-creds' that stores the username and password required to access the database. Due to security reasons, you need to update the password in the Secret.

Update the existing 'database-creds' Secret with the new password.

Ensure that the changes are propagated to the running Pods using the Secret without redeploying the Pods.

Write the imperative command or YAML manifest to update the 'database-creds' Secret and apply the changes to the running Pods.
```

<details><summary>show</summary>
<p>
    
```bash

# Create a new Secret
kubectl create secret generic database-creds --from-literal=username=dbuser --from-literal=password=newpassword --dry-run=client -o yaml > updated-secret.yaml

# Apply the changes to the existing Secret
kubectl apply -f updated-secret.yaml

# The changes will automatically propagate to the running Pods using the Secret

```

</p>
</details>
