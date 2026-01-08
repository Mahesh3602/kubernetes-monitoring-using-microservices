# Information
- Repo has code to install monitoring on Kubernetes system.
- There is monitoring namesapce with pods for grafana, prometheus and node exporter
- There are sample application to test the monitoring
- It uses Kustomize approach to create platform

# Prerequisites
- working Kubernetes cluster (Ex- 1 controlplane and 2 worker nodes in ready state)

# Steps
  ## create separate namespaces
cd ./infrastructure/namespaces/
kubectl kustomize .
kubectl apply -k . 

 ## install prometheus, grafana ,node exporter ,kube-stsatemetrics , alertmanager deployments from monitoring folder
cd ./monitoring/prometheus/ 
kubectl kustomize .
kubectl apply -k . 

cd ./monitoring/grafana/
kubectl kustomize .
kubectl apply -k . 

cd ./monitoring/node-exporter/
kubectl kustomize .
kubectl apply -k . 

cd ./monitoring/kube-state-metrics/
kubectl kustomize .
kubectl apply -k . 

cd ./monitoring/alertmanager/
kubectl kustomize .
kubectl apply -k .

# deploy sample application Homepage
cd ./services/homepage/
kubectl kustomize .
kubectl apply -k .

# deploy sample application jelly
cd ./services/jelly/
kubectl kustomize .
kubectl apply -k .

# Allow inbouund traffic on the ports on aws
Prometheus - 30090
Grafana - 30030
alertmanager- 30093
Kube - 
nodeexporter - 
sample homepage application service - 31000
sample jellyfin application service - 30096

# Test grafana & Prometheus
- http://<publicip>:30030
http://54.234.114.137:30030
- http://<publicip>:30090
http://54.234.114.137:30090

# Add prometheus as datasource in grafana

 ## import dashboards
 - ex- 
 - 15661 : for kubernetes
 - 1860 : for node exporter
 - 
        

