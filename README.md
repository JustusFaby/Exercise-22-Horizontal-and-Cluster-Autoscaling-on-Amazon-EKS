# Exercise 22: Horizontal and Cluster Autoscaling on Amazon EKS

## 📌 Overview

This project demonstrates the implementation of **Horizontal Pod Autoscaler (HPA)** and **Cluster Autoscaler** on **Amazon Elastic Kubernetes Service (EKS)**. The application automatically scales pods based on CPU utilization and provisions additional worker nodes when the existing nodes are unable to schedule new pods.

---

## 🎯 Objective

Implement automatic scaling in Kubernetes by configuring:

* Horizontal Pod Autoscaler (HPA)
* Cluster Autoscaler
* Metrics Server
* IAM Roles for Service Accounts (IRSA)
* Load testing to trigger autoscaling

---

## 🛠️ Technologies Used

* Amazon EKS
* Kubernetes
* eksctl
* kubectl
* AWS CLI
* Amazon EC2 Auto Scaling Group
* IAM Roles for Service Accounts (IRSA)
* Metrics Server
* Cluster Autoscaler
* NGINX
* BusyBox (Load Generator)

---

## 🏗️ Architecture

```text
                   Load Generator
                 (BusyBox / wget)
                         │
                         ▼
                  NGINX Application
                         │
                         ▼
           Horizontal Pod Autoscaler
                         │
               Scale Pods (2 → 20)
                         │
                         ▼
              Cluster Autoscaler
                         │
              Scale Nodes (2 → 3)
                         │
                         ▼
          Amazon EKS Managed Node Group
```

---

## ✨ Features

* Deploy application on Amazon EKS
* Install and configure Metrics Server
* Configure Horizontal Pod Autoscaler
* Configure Cluster Autoscaler
* Implement IRSA authentication
* Auto-discover AWS Auto Scaling Groups
* Automatic pod scaling
* Automatic node scaling
* CPU utilization monitoring
* Load testing

---

## 📂 Project Structure

```text
exercise-22/
│── deployment.yaml
│── service.yaml
│── hpa.yaml
│── cluster-autoscaler-policy.json
│── cluster-autoscaler-autodiscover.yaml
│── README.md
```

---

## 📋 Prerequisites

* AWS Account
* Amazon EKS Cluster
* kubectl
* eksctl
* AWS CLI
* IAM OIDC Provider
* Metrics Server

---

## 🚀 Implementation Steps

### Step 1 – Create Amazon EKS Cluster

Create a managed EKS cluster using **eksctl**.

### Step 2 – Install Metrics Server

Deploy Metrics Server to collect Kubernetes resource metrics.

### Step 3 – Deploy Application

Deploy the NGINX application and expose it using a Kubernetes Service.

### Step 4 – Configure Horizontal Pod Autoscaler

Create an HPA to automatically scale pods based on CPU utilization.

### Step 5 – Configure IAM Roles for Service Accounts (IRSA)

Grant Cluster Autoscaler the required AWS permissions without using AWS Access Keys.

### Step 6 – Install Cluster Autoscaler

Deploy Cluster Autoscaler and configure Auto Scaling Group auto-discovery.

### Step 7 – Generate Load

Generate application traffic using a BusyBox pod.

### Step 8 – Verify Autoscaling

Verify pod scaling, node scaling, CPU metrics, and Auto Scaling Group capacity.

---

## ✅ Verification Commands

```bash
kubectl get nodes

kubectl get deployment

kubectl get hpa

kubectl get pods

kubectl top pods

kubectl top nodes

aws autoscaling describe-auto-scaling-groups \
--query "AutoScalingGroups[*].[AutoScalingGroupName,DesiredCapacity,MinSize,MaxSize]" \
--output table

kubectl logs -n kube-system deployment/cluster-autoscaler --tail=20
```

---

## 📈 Results

* Successfully deployed application on Amazon EKS
* Metrics Server installed and configured
* Horizontal Pod Autoscaler configured successfully
* Cluster Autoscaler installed successfully
* IRSA configured successfully
* Auto Scaling Group discovered automatically
* Worker nodes scaled automatically
* CPU metrics collected successfully
* Load testing completed successfully

---

## 📚 Learning Outcomes

* Amazon EKS
* Kubernetes Autoscaling
* Horizontal Pod Autoscaler (HPA)
* Cluster Autoscaler
* Metrics Server
* IAM Roles for Service Accounts (IRSA)
* Amazon EC2 Auto Scaling Groups
* Kubernetes Resource Monitoring

---

# 🎥 Demo Video

**Demo Video Link:**

> **Paste your demo video link here**

```text
https://your-demo-video-link
```

---

## 👨‍💻 Author

**Justus Faby Jeyakumar**

GitHub: https://github.com/JustusFaby
