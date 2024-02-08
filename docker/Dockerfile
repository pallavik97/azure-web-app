# Dockerfile for building Docker image with Azure AKS infrastructure and application

# Use an official Azure CLI image as the base image
FROM mcr.microsoft.com/azure-cli

# Install kubectl
RUN az aks install-cli

# Set the working directory
WORKDIR /app

# Copy the application files
COPY ../app/ ./

# Copy the Kubernetes manifest file
COPY ../kubernetes/deployment.yaml /app/deployment.yaml

# Copy the Terraform files
COPY ../terraform/ /app/terraform/

# Your additional setup steps here (if needed)
