
# Django Notes App

## Overview

Django Notes App is a full-stack web application for managing personal notes, featuring a RESTful API backend built with Django and a responsive React frontend. The project is containerized with Docker and deployed on Kubernetes using Helm charts with auto-scaling capabilities powered by the Horizontal Pod Autoscaler (HPA).

---

## Features

- Create, read, update, and delete notes via REST API  
- Interactive React frontend with intuitive UI  
- Kubernetes deployment with Helm charts for easy scaling and management  
- Auto-scaling based on CPU utilization with HPA  
- CI/CD pipeline configured using Jenkins for automated builds and deployments

---

## Tech Stack

- **Backend:** Django, Django REST Framework  
- **Frontend:** React.js  
- **Containerization:** Docker  
- **Orchestration:** Kubernetes, Helm  
- **CI/CD:** Jenkins  
- **Monitoring:** Kubernetes Metrics Server (required for HPA)  

---

## Project Structure

```
.
├── api/                  # Django REST API application source code
├── mynotes/              # React frontend application
├── notesapp/             # Django project settings and configurations
├── notesappchart/        # Helm chart templates and values for Kubernetes deployment
├── k8s/                  # Raw Kubernetes manifests (optional/manual use)
├── Dockerfile            # Backend Dockerfile
├── docker-compose.yml    # Local development setup with Docker Compose
├── Jenkinsfile           # CI/CD pipeline configuration
├── requirements.txt      # Python dependencies
└── README.md             # This file
```

---

## Prerequisites

- Kubernetes cluster (local or cloud) with metrics-server installed  
- Helm CLI (v3+)  
- `kubectl` CLI configured to access your cluster  
- Docker (for building container images)  
- Jenkins (optional, for CI/CD automation)

---

## Installation & Deployment

1. **Deploy Helm Chart**

```bash
helm install notesapp notesappchart/ -f notesappchart/values.yaml --namespace nginx --create-namespace
```

2. **Set Kubernetes Namespace Context**

```bash
kubectl config set-context --current --namespace=nginx
```

3. **Verify Deployment**

```bash
kubectl get all
```

---

## Accessing the Application

Forward the service port to your local machine:

```bash
kubectl port-forward svc/notes-app-service 8000:8000
```

Open your browser and visit: [http://localhost:8000](http://localhost:8000)

---

## Auto-scaling with Horizontal Pod Autoscaler (HPA)

The application is configured to auto-scale pods based on CPU utilization (target 80%).

### Load Testing for HPA

Run a load generator pod to simulate traffic:

```bash
kubectl run -i --tty load-generator --rm --image=busybox -n nginx -- /bin/sh
```

Inside the pod shell, run:

```bash
while true; do wget -q -O - http://notes-app-service.nginx.svc.cluster.local:8000; done
```

Watch the HPA status:

```bash
kubectl get hpa
kubectl get pods
```

Press `Ctrl+C` to stop the load generator.

---

## Local Development

1. Build and run the backend and frontend using Docker Compose:

```bash
docker-compose up --build
```

2. Access frontend at [http://localhost:3000](http://localhost:3000)  
3. Backend API runs at [http://localhost:8000](http://localhost:8000)

---

## Testing

Run Django tests with:

```bash
python manage.py test
```

---

## CI/CD Pipeline

A Jenkins pipeline (`Jenkinsfile`) is included to automate:

- Docker image build and push  
- Helm chart deployment to Kubernetes cluster  

Customize the pipeline according to your Jenkins environment.

---

## Notes

- Ensure the Kubernetes Metrics Server is installed and running to enable HPA.  
- Resource requests and limits are configured in Helm values for optimal autoscaling.

---

## Contributing

Contributions are welcome! Please fork the repository and submit pull requests for improvements or bug fixes.

---

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

## Contact

For questions or feedback, please contact the project maintainer.
