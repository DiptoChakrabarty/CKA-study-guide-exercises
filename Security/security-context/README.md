# CKA commands and files

## Questions and Solutions

- Solution in capabilities-context.yaml
```
You are tasked with deploying a Pod named 'user-id' in your Kubernetes cluster. The Pod should run a container named 'sec-ctx-demo-2' using the 'gcr.io/google-samples/node-hello:1.0' image.

Configure the Pod's security context to run the container with the user ID '1000'.

Additionally, update the security context for the container 'sec-ctx-demo-2' to grant additional Linux capabilities. Allow the container to have capabilities for manipulating the system time and performing network administration.

Write the YAML manifest for the 'user-id' Pod with the appropriate security context settings.
```

- Solution in security-id-user.yaml
```
You are deploying a Pod named 'user-id' in your Kubernetes cluster. The Pod contains two containers: 'sec-ctx-demo-2' and 'second-container'. The 'sec-ctx-demo-2' container uses the 'gcr.io/google-samples/node-hello:1.0' image.

Configure the Pod's security context to set the overall Pod's runAsUser to '1000'.

Additionally, update the security context for the 'sec-ctx-demo-2' container to run as user ID '2000' specifically, overriding the Pod's runAsUser setting.

Ensure that the 'sec-ctx-demo-2' container does not allow privilege escalation.
```