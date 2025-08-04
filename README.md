# 📊 Kubernetes Monitoring with kube-prometheus-stack

This repository contains selected Kubernetes YAML files exported from a live setup of the [kube-prometheus-stack](https://github.com/prometheus-community/helm-charts/tree/main/charts/kube-prometheus-stack), which includes **Prometheus**, **Grafana**, **Alertmanager**, and related monitoring components.

> 📝 **Disclaimer**:  
> I did **not manually write** these YAML files.  
> Instead, I exported them using `kubectl get ... -o yaml` from a running Kubernetes cluster.  
> This was done to study and demonstrate my understanding of how the Prometheus stack is deployed and structured in a real-world environment.

---

## 🔍 What's in This Repository

The repository includes:

- `grafana-deployment.yaml` – Grafana Deployment configuration
- `grafana-service.yaml` – ClusterIP Service exposing Grafana
- `prometheus-deployment.yaml` – Prometheus StatefulSet
- `prometheus-service.yaml` – Prometheus ClusterIP Service
- `alertmanager.yaml` – Alertmanager StatefulSet
- `servicemonitor.yaml` – Sample ServiceMonitor used by Prometheus to scrape metrics

---

## 🚀 How I Deployed the Stack

This setup was done using **Minikube**, **kubectl**, **Docker**, and **Helm** on Windows.

### 🛠 Prerequisites

- [Minikube](https://minikube.sigs.k8s.io/docs/)
- [kubectl](https://kubernetes.io/docs/tasks/tools/)
- [Helm](https://helm.sh/docs/intro/install/) — installed via [winget](https://learn.microsoft.com/en-us/windows/package-manager/winget/):

```bash
winget install Helm.Helm
```
🧱 Helm Installation of kube-prometheus-stack
bash
Copy
Edit
# Add the Helm repo
```bash
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
helm install prometheus prometheus-community/kube-prometheus-stack
```
📁 Commands Used to Export Files
All files in this repo were collected using the following kubectl commands:

# Grafana deployment and service
```bash
kubectl get deploy prometheus-grafana -o yaml > grafana-deployment.yaml
kubectl get svc  prometheus-grafana -o yaml > grafana-service.yaml
```
# Prometheus statefulset and service
```bash
kubectl get statefulset prometheus-prometheus-kube-prometheus-prometheus -o yaml > prometheus-deployment.yaml
kubectl get svc prometheus-kube-prometheus-prometheus -o yaml > prometheus-service.yaml
```
# Alertmanager statefulset
```bash
kubectl get statefulset alertmanager-prometheus-kube-prometheus-alertmanager -o yaml > alertmanager.yaml
```
# ServiceMonitor
```bash
kubectl get servicemonitor -o yaml > servicemonitor.yaml
```
# Dashboard Images
### Login Page
![Dashboard Images](<Screenshot 2025-08-04 222017.png>) 
### Landing page
![Dashboard Images](<Screenshot 2025-08-04 204510.png>) 
### Minikube performance
![Dashboard Images](<Screenshot 2025-08-04 204957.png>) 
![Dashboard Images](<Screenshot 2025-08-04 205425.png>) 
![Dashboard Images](<Screenshot 2025-08-04 205503.png>) 
### Some additional dashboards
![Dashboard Images](<Screenshot 2025-08-04 205540.png>) 
![Dashboard Images](<Screenshot 2025-08-04 205933.png>) 
![Dashboard Images](<Screenshot 2025-08-04 205959.png>) 
![Dashboard Images](<Screenshot 2025-08-04 221947.png>)

💡 Purpose of This Repo
This repository is intended to:

Showcase my understanding of Kubernetes-native monitoring

Demonstrate Helm-based deployment practices

Help others see what’s actually installed by kube-prometheus-stack

🛠 Tools Used
Windows 11

Minikube with Docker driver

kubectl

Helm

GitHub

Thanks for checking this out!