# Init Containers


## Questions and Solutions


- Solution in nginx-init.yaml
```
write a index.html file in init container which will be used by original container

The init container should write hello world into an html file

The nginx pod should use this file for its webpage

Write the YAML file in 'nginx-init.yaml'

```

- Solution in web-app-pod.yaml

```
 A Pod running the application container 'web-app' has been experiencing intermittent issues during startup. You suspect that the problem might be related to the application's dependencies not being fully ready before the main container starts.

To address this, you decide to implement an init container to wait for the required dependencies to be available before launching the 'web-app' container.

Write a YAML manifest to define the Pod with the necessary init container that waits for a PostgreSQL database with the label 'app=db' to become ready. The 'web-app' container uses the 'busybox' image, and the 'init-container' uses the 'postgres' image.

Ensure the 'init-container' waits for the database pod to have a 'Running' status and log the message 'Dependencies are ready' once the readiness condition is met.

Name the YAML file 'web-app-pod.yaml'.

```

- Solution in app-server-pod.yaml

```
You are tasked with deploying a new application called 'app-server' that requires some initial configuration before it can start serving traffic. The configuration files are stored in a ConfigMap named 'app-config'.

Create a Pod named 'app-server-pod' with two containers: 'app-server' and 'config-init'. The 'app-server' container uses the 'app-image' with the latest tag, and the 'config-init' container uses the 'busybox' image.

Ensure the 'config-init' container mounts the 'app-config' ConfigMap as a volume at the path '/config' and copies the configuration files to the '/app-config' directory within the 'app-server' container.

Once the 'config-init' container successfully copies the files, it should log the message 'Configuration files copied successfully.' to the standard output.

Write the YAML manifest to create the 'app-server-pod' with the appropriate containers and volumes. Save the YAML file as 'app-server-pod.yaml'.

```