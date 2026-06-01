# AWS DevOps Capstone Project
🚀 AWS DevOps Capstone — QR Code App on EKS
A production-style DevOps capstone project that provisions an Amazon EKS cluster using Terraform and deploys a full-stack QR Code Generator application using Kubernetes manifests.

🔗 GitHub Repository: aws-devops-capstone


📐 Architecture Overview
                    ┌──────────────────────────────────┐
                    │          AWS Cloud (us-east-1)   │
                    │                                  │
                    │  ┌──────────── VPC ────────────┐ │
                    │  │  10.0.0.0/16                │ │
                    │  │                             │ │
                    │  │  Subnet 1   Subnet 2   Subnet 3  │
                    │  │  us-east-1b us-east-1c us-east-1d │
                    │  │                             │ │
                    │  │  ┌──────── EKS Cluster ──────┐ │ │
                    │  │  │  devops-capstone-project  │ │ │
                    │  │  │  K8s v1.28                │ │ │
                    │  │  │                           │ │ │
                    │  │  │  [Node: t3.medium]        │ │ │
                    │  │  │                           │ │ │
                    │  │  │  ┌─────────┐ ┌─────────┐ │ │ │
                    │  │  │  │Frontend │ │Backend  │ │ │ │
                    │  │  │  │ (x2)    │ │ (x2)   │ │ │ │
                    │  │  │  │Port 3000│ │Port 80  │ │ │ │
                    │  │  │  └─────────┘ └─────────┘ │ │ │
                    │  │  └──────────────────────────┘ │ │
                    │  └─────────────────────────────┘ │
                    └──────────────────────────────────┘

🛠️ Tech Stack
LayerTechnologyInfrastructureTerraform (AWS Provider ~5.0)Container OrchestrationAmazon EKS (Kubernetes 1.28)NetworkingCustom VPC, 3 Public Subnets, IGWComputeManaged Node Group — t3.mediumBackendFastAPI / QR Code API (containerized)FrontendNext.js / React (containerized)Regionus-east-1

📁 Project Structure
aws-devops-capstone/
├── main.tf           # VPC, Subnets, IGW, Route Tables, EKS Cluster
├── provider.tf       # Terraform AWS provider config
├── backend.yaml      # Kubernetes Deployment + ClusterIP Service for API
├── frontend.yaml     # Kubernetes Deployment + LoadBalancer Service for UI
├── .gitignore
└── LICENSE

⚙️ Infrastructure — Terraform
What Gets Provisioned

VPC (10.0.0.0/16) with DNS hostnames enabled
3 Public Subnets across us-east-1b, us-east-1c, us-east-1d
Internet Gateway + Route Table associations for all subnets
EKS Cluster (devops-capstone-project, K8s v1.28) with public endpoint access
Managed Node Group — t3.medium, desired/max size: 1
