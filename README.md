# helm-weather-tsg

This repository contains a Helm chart for deploying the WeatherApp application on Kubernetes. The chart provides configuration for deployment, service, ingress, and integration with Vault for secrets management.

## Features

- Deploys the WeatherApp as a scalable Kubernetes Deployment.
- Exposes the app via a Kubernetes Service (ClusterIP, or LoadBalancer).
- Optional Ingress support with customizable paths and annotations.
- Configurable resource requests and limits.
- Supports Docker image pull secrets.
- Integrates with Vault for secret management.
- Easily customizable via `values.yaml`.

## Prerequisites

- Helm - (https://helm.sh/)
- Kubernetes cluster
- Vault - (https://www.vaultproject.io/) for secrets management
- DockerHub credentials (if using a private image)
- Nginx ingress controller or other ingress controller

## Installation

1. **Clone the repository:**
   ```sh
   git clone https://gitlab.com/nitzanmr/helm_weather.git
   cd helm-weather-tsg

2. **Create Vault Secret:**
    export VAULT_TOKEN=your-vault-token
    kubectl create secret generic vault-token --from-literal=token=$VAULT_TOKEN

3. **Create DockerHub Pull Secret:**
    kubectl create secret docker-registry dockerhub \
    --docker-username=<your-username> \
    --docker-password=<your-password> \
    --docker-email=<your-email>
4. **helm install weatherapp**

    for overiding the defaults:
    helm install weatherapp . -f my-values.yaml

## Configuration
    See values.yaml for all configurable options.

    Key options:

    * replicaCount: Number of app replicas.
    * image.repository, image.tag: Docker image settings.
    * service.type: Service type (ClusterIP, LoadBalancer).
    * ingress.enabled: Enable/disable ingress.
    * config.bgColor: Background color for the app UI.
