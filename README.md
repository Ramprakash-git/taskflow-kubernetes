# TaskFlow Kubernetes

This repository contains Kubernetes manifests for deploying the TaskFlow backend application on Amazon EKS.

## Components

- **Namespace:** Provides isolation for TaskFlow resources.
- **ConfigMap:** Stores application configuration.
- **ServiceAccount:** Provides AWS IAM access to backend Pods through IRSA.
- **Deployment:** Manages backend application Pods and container configuration.
- **Service:** Provides internal networking for backend Pods.
- **Ingress:** Configures external access through AWS Application Load Balancer.

## Architecture

The AWS Load Balancer Controller manages the ALB, which routes incoming traffic directly to backend Pods using IP target mode.

The backend connects to Amazon RDS PostgreSQL and retrieves database credentials from AWS Secrets Manager using IRSA.

## Deployment

Application deployment is automated through GitHub Actions.

The backend CD workflow retrieves the manifests from this repository, updates the container image with the latest ECR image, and deploys the application to Amazon EKS.