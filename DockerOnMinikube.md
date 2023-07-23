# Docker on Minikube (Apple Silicon)

Instructions for setting up Minikube (as an alternative to Docker Desktop) to run Docker containers on an Apple Silicon (M1 & M2).

The instructions are based on:
1. [How to Setup Minikube on MAC M1/M2](https://devopscube.com/minikube-mac/)
2. [Run Docker without Docker Desktop on macOS](https://dhwaneetbhatt.com/blog/run-docker-without-docker-desktop-on-macos)

which contain additional context and details.

## Commands

### Installation
```
brew install qemu
brew install socket_vmnet
sudo brew services start socket_vmnet
brew install minikube
brew install docker
brew install docker-compose
```

```
brew install minikube
brew install colima
brew install docker
brew install docker-compose
```

### Validation
```
minikube start
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

### Other tips

Start k8s dashboard:
```
minikube addons enable metrics-server
minikube dashboard
```