# 🚀 **End-to-End DevOps Architecture: Zomato Clone Deployment**

In this comprehensive DevOps project, I engineered and deployed a highly available **Zomato Clone Application**, contrasting traditional Continuous Integration pipelines with modern, declarative GitOps workflows on AWS. 

## 🛠️ Tech Stack & Tools

**Version Control & CI/CD:**
* ![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white) 
* ![Jenkins](https://img.shields.io/badge/Jenkins-D24939?style=flat-square&logo=jenkins&logoColor=white)
* ![ArgoCD](https://img.shields.io/badge/ArgoCD-EF7B4D?style=flat-square&logo=argo&logoColor=white)

**Containerization & Orchestration:**
* ![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
* ![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white)
* ![AWS EKS](https://img.shields.io/badge/AWS_EKS-FF9900?style=flat-square&logo=amazon-aws&logoColor=white)

**Security & Quality Gates:**
* ![SonarQube](https://img.shields.io/badge/SonarQube-4E9BCD?style=flat-square&logo=sonarqube&logoColor=white)
* ![OWASP](https://img.shields.io/badge/OWASP-000000?style=flat-square&logo=owasp&logoColor=white)
* ![Trivy](https://img.shields.io/badge/Trivy-00979D?style=flat-square&logo=trivy&logoColor=white)

**Monitoring & Observability:**
* ![Prometheus](https://img.shields.io/badge/Prometheus-E6522C?style=flat-square&logo=prometheus&logoColor=white)
* ![Grafana](https://img.shields.io/badge/Grafana-F46800?style=flat-square&logo=grafana&logoColor=white)

---

## 🏗️ Project Architecture Phases

### **Phase 1: Traditional CI/CD (Imperative Deployment)**
* Provisioned AWS EC2 instances and configured a complete Jenkins pipeline.
* Integrated strict **SonarQube Quality Gates** to enforce static code analysis.
* Automated the Docker build process, integrating Trivy and OWASP for container vulnerability scanning before pushing images to the registry and deploying to EC2.

### **Phase 2: Modern GitOps (Declarative Deployment)**
* Migrated from standalone EC2s to a fully managed **AWS EKS (Elastic Kubernetes Service)** cluster for high availability.
* Integrated **ArgoCD** to establish a true GitOps workflow. The GitHub repository acts as the single source of truth, automatically syncing declarative YAML manifests directly into the cluster with zero human intervention.
* Provisioned production-grade networking by installing the AWS Load Balancer Controller via Helm, deploying an Ingress resource to automatically generate an **AWS Application Load Balancer (ALB)** for secure, internet-facing traffic routing.

---

## 🛑 Real-World Troubleshooting & Debugging

During the deployment of the networking layer, I encountered and resolved several cloud infrastructure roadblocks:
1. **IAM 403 Access Denied (`DescribeLoadBalancers`):** The Ingress remained in a pending state due to the AWS Load Balancer Controller lacking permissions. I resolved this by utilizing `eksctl` to bind an OIDC provider and attach the correct AWS IAM policy to the Kubernetes ServiceAccount.
2. **VPC Subnet Discovery Failure:** AWS refused to provision the physical load balancer because it could not discover the target subnets. I resolved this by navigating to the AWS VPC console and manually applying the `kubernetes.io/role/elb=1` tags to my public subnets, explicitly authorizing hardware placement.

---

### 📹 Architecture Walkthrough Video:  
[![YouTube](https://img.shields.io/badge/YouTube-FF0000?style=flat-square&logo=youtube&logoColor=white)](YOUR_YOUTUBE_LINK_HERE)

---

## 📬 Let's Connect:  
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/hardik-yadav-54458630a/)