# Flask on Kubernetes (kind)

Simple Flask app containerized with Docker and deployed to a local Kubernetes cluster using kind.

## Run locally
    docker build -t flask-app:v1 .
    docker run --rm -p 5000:5000 flask-app:v1

## Deploy to kind
    kind create cluster
    kind load docker-image flask-app:v1
    kubectl apply -f deployment.yaml
    kubectl port-forward svc/flask-app 8080:80

## Endpoints
- `/` returns the pod hostname
- `/health` is used by the readinessProbe
