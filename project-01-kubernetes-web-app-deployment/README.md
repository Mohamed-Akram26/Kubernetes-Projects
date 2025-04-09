# Simple Kubernetes Web App Deployment

This project demonstrates how to deploy a simple web application on Kubernetes using core Kubernetes components like Namespace, ConfigMap, Secret, Deployment, and Ingress. It helps showcase how these YAML files work together in a real-world app deployment scenario.

## Project Structure

### 1. `namespace.yml`
-  Creates a dedicated Kubernetes namespace called `demo-app`.


### 2. `configmap.yml`
- Defines a ConfigMap named `demo-configmap` containing non-sensitive configuration data like `APP_ENV`.


### 3. `secret.yml`
- Creates a Kubernetes Secret named `demo-secret` holding sensitive credentials such as a `DB_PASSWORD`.


### 4. `deployment.yml`
- Deploys a web application (nginx) in the `demo-app` namespace using a Deployment resource named `demo-deployment`.
- **How it works**:
  - Uses values from `demo-configmap` and `demo-secret` via environment variables.
  - Creates 2 replicas of the pod for high availability.
  - Exposes the app on port 80 via a corresponding service.

### 5. `ingress.yml`
-  Defines an Ingress rule that maps external traffic to the internal service on the `/` path using the host `demo.local`.
-  Allows external access to the app with a custom domain name, without exposing the service directly via LoadBalancer or NodePort.


## How it all works together

1. The `demo-app` namespace logically groups all the components.
2. The `ConfigMap` and `Secret` provide configuration and credentials.
3. The `Deployment` pulls these values into pods and runs the app.
4. The `Ingress` routes external traffic to the app service.
5. Port-forwarding and curl tests validate the successful deployment internally.

This project is a foundational example of building and exposing an app securely and efficiently using Kubernetes.

