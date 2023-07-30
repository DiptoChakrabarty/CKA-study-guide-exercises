# CKA commands and files

## Deployments

- Check number of deployments present in system

```sh
    kubectl get deployment
```
- Delete Deployment

```sh
    kubectl delete deployment <deployment-name>
```
- Information about the Deployment
```sh
    kubectl describe deployments 
```
- Scale a deployment
```sh
    kubectl scale deployments/<deployment-name>  --replicas=4
```
- Information about deployment
```sh
    kubectl describe deployments/<name>
```
- Update a deployment image
```sh
    kubectl set image deployments/<deployment-name>   <container-name>=<new image name>
```
- Rollout status
```sh
    kubectl rollout status deployments/<deployment-name>   
```
- Rollback deployment
```sh
    kubectl rollout undo deployment/<deployment-name>
```
- Edit Deployment
```sh
    kubectl edit deployment.v1.apps/nginx-deployment
```
- Run deployment with replicas
```sh
    kubectl run <pod-name> --image=<image name> --replicas=<no of replicas>
    
    kubectl create deployment <deployment name> --image=<image name>
```

- Get deployment yaml
```sh
kubectl create deployment nginx --image=nginx --dry-run=client -o yaml > nginx-deploy.yaml
```

- Set label of deployment
```
kubectl create deployment my-dep -o yaml --dry-run=client | kubectl label --local -f - environment=qa -o yaml | kubectl create -f -
```

## Question and Answers

- Solution in nginx-deployment.yaml
```
Deploy an Nginx web application in your Kubernetes cluster. Create a deployment named "nginx-deployment" with three replicas, exposing the application on port 80. Ensure that the deployment is running, and the replicas are successfully created.
```

<details><summary>Iperative Command</summary>
<p>

```bash
# Step 1: Create the Nginx deployment with three replicas
kubectl create deployment nginx-deployment --image=nginx --replicas=3

# Step 2: Expose the deployment as a service on port 80
kubectl expose deployment nginx-deployment --port=80 --type=ClusterIP

# Step 3: Verify the deployment and replicas
kubectl get deployments
kubectl get pods

```
</p>
</details>

- Rolling update solution
```
The "nginx-deployment" is currently running an older version of Nginx (1.19.2). You need to perform a rolling update to the latest version of Nginx (1.21.1). Ensure that the update is performed gradually, with no downtime for the application.
```
<details><summary>Iperative Command</summary>
<p>

```bash
# Perform a rolling update of the deployment with the new Nginx image
kubectl set image deployment/nginx-deployment nginx=nginx:1.21.1
```
</p>
</details>

- Perform maintainence
```
You need to pause the "nginx-deployment" to prevent any further updates from being applied. After performing some maintenance tasks, resume the deployment to continue rolling updates.
```
<details><summary>Iperative Command</summary>
<p>

```bash
# Pause the deployment to prevent further updates
kubectl rollout pause deployment/nginx-deployment

# Perform maintenance tasks on the cluster or the application.

# Resume the deployment to continue rolling updates
kubectl rollout resume deployment/nginx-deployment

```
</p>
</details>