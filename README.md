# Significa Assesement K8S deployment

## K8S integration
Use a machine with minikube installed

Commands to run the deployment. You will also need the significa-assesement-app repository

### Clone the repository
```bash
git clone git@github.com:gkoloventzos/significa-assessment-app.git
```

### Clone this repository
```bash
git clone git@github.com:gkoloventzos/significa-assessment-app.git
```

### Then run the following commands
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
I will not add any Azure K8S deployment as I do not want to incur any charges on my Azure account

```bash
kubectl rollout restart deployment/simplewebapp -n simplewebapp
```
This command will rollout any changes on minikube.

## Monitoring

For monitoring, in my work, I have used Grafana and Prometheus with great results.
I will use the same with Loki to get some of the app messages.
I will check the 
- errors (4xx/5xx) for failures
- request latency for slow responses
- request throughput for traffic
- CPU usage
- memory usage
- disk usage
- pod health
- replica availability
- node status

These stats will give an overview of the cluster and application behaviour.
Grafana + AlertManager can send messages directly to a Slack channel for quick and easy acknowledgment of issues.

