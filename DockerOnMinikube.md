# Docker on Minikube (Apple Silicon)

Instructions for setting up Minikube (as an alternative to Docker Desktop) to run Docker containers on an Apple Silicon (M1 & M2).

Based on:

[How to run Minikube on an Apple M1 chip without Docker Desktop](
    https://everythingdevops.dev/how-to-run-minikube-on-apple-m1-chip-without-docker-desktop/
)

## Installation

```
brew install minikube
brew install colima
brew install docker
brew install docker-compose
```

## Launch
```
colima start
minikube start
```
Optionally but recommended, start k8s dashboard:
```
minikube addons enable metrics-server
minikube dashboard
```

## Validation
General:
```
colima status
docker ps
kubectl get all
```
Validate docker engine function:
```
docker run hello-world
```
Validate k8s function:
```
kubectl create deployment kubernetes-bootcamp --image=gcr.io/google-samples/kubernetes-bootcamp:v1
kubectl expose deployment/kubernetes-bootcamp --type="NodePort" --port 8080
minikube service kubernetes-bootcamp
```

## Getting Started

### [Minikube LoadBalancer access](https://minikube.sigs.k8s.io/docs/handbook/accessing/#loadbalancer-access)

Start minikube tunnel in one terminal:
```
minikube tunnel
```

In another terminal:
```
kubectl create deployment hello-minikube1 --image=kicbase/echo-server:1.0
kubectl expose deployment hello-minikube1 --type=LoadBalancer --port=8080
```
If 8080 is in use, use a different port:
```
kubectl expose deployment hello-minikube1 --type=LoadBalancer --port=8081 \
    --target-port=8080
```
