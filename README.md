# DevSecOps-2-project
# DevSecOps Pipeline for a Netflix-like Application

This project demonstrates a **DevSecOps pipeline for a Netflix-like application** using AWS and Kubernetes. It covers the following stages:

## Stages

1. **Containerization**  
   The application is packaged in a Docker container and deployed locally on an EC2 instance for testing.

2. **Security**  
   Security scanning and integration are implemented at the build phase to ensure a secure deployment.

3. **CI/CD Automation**  
   Jenkins automates the build, test, and deployment cycle, pushing images to Docker Hub for seamless integration.

4. **Monitoring and Observability**  
   Prometheus and Grafana provide performance insights and help identify bottlenecks.

5. **Kubernetes Deployment**  
   Helm charts are used to deploy and manage the application on a Kubernetes cluster, ensuring scalability.

6. **GitOps Workflow**  
   ArgoCD handles declarative, version-controlled application deployments to Kubernetes.

---

## Key Features
- **Scalability**: Achieved through Kubernetes orchestration.
- **Security**: Integrated into the CI/CD pipeline.
- **Automation**: Continuous integration and deployment using Jenkins.
- **Observability**: Real-time monitoring with Prometheus and Grafana.

---

## Technologies Used
- **Docker**: For containerization of the application.
- **AWS EC2**: To run the application locally during testing.
- **Jenkins**: For CI/CD automation.
- **Prometheus & Grafana**: For monitoring and observability.
- **Kubernetes**: For application orchestration.
- **Helm Charts**: To simplify Kubernetes deployments.
- **ArgoCD**: For GitOps-based workflow automation.
