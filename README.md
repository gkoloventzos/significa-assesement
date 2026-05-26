# Significa Assesement K8S deployment
Use a machine with minikube installed

Commands to run the deployment. You will also need the significa-assesement-app repository

## Clone the repository
```bash
git clone git@github.com:gkoloventzos/significa-assessment-app.git
```

## Clone this repository
```bash
git clone git@github.com:gkoloventzos/significa-assessment-app.git
```

## Then run the following commands
```bash
eval $(minikube docker-env)
minikube start --driver=docker
minikube addons enable ingress        
minikube addons enable metrics-server
cd significa-assesement-app/SimpleWebApp
docker build -t gkoloven-significa:latest .
cd ~/significa-assesement/
kubectl apply -f k8s_significa/namespase.yaml
kubectl apply -f k8s_significa/configmap.yaml
kubectl apply -f k8s_significa/deployment.yaml
kubectl apply -f k8s_significa/service.yaml
minikube service simplewebapp-service -n simplewebapp
```
