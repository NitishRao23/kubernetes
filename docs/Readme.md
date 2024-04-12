# Docker Image and Kubernetes Deployment Guide

This guide provides step-by-step instructions for creating a Docker image, pushing it to Docker Hub, deploying it on Kubernetes, and exposing it to a port for access.

## Create Docker Image

1. Create the Dockerfile with the required configuration.
2. Build the Docker image using the following command:

```bash
docker build -t new-image:v1 .
```


## Push Docker Image to Docker Hub

3. Check the Docker images list:

```docker images```

4. Tag the newly created image:
docker tag new-image:v1 nitishrao/new-image:v1

5. Log in to Docker Hub when prompted:

```docker login```

6. Push the tagged image to Docker Hub:

```docker push nitishrao/new-image:v1```


## Deploy on Kubernetes

7. Create a YAML file (image1.yaml) for the Kubernetes pod configuration.
8. Apply the configuration using the following command:

```kubectl apply -f image1.yaml```


## Check Pods Status

9. Check the status of pods:

kubectl get pods

10. Ensure that the newly created pod is in the running state.

## Expose Pod to a Port

11. Expose the pod to a port using a service:
 ```bash
 kubectl expose pod apache-deployment-645bc4554-hk7tl --type=NodePort --port=81 --target-port=80 --name=apache-service
 ```

## Check Service Status

12. Verify that the service is exposed to the port:
 ```bash
 kubectl get svc apache-service
 ```

## Access the Deployed Image

13. Generate a link to access the image via the specified port using Minikube:
 ```bash
 minikube service apache-service --url
 ```
14. Open the generated link in a new browser tab to access the deployed image.

## Conclusion

By following these steps, you have successfully created a Docker image, pushed it to Docker Hub, deployed it on Kubernetes, exposed it to a port, and accessed it via Minikube.
