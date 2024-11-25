# DevSecOps-2-project
This project demonstrates a DevSecOps pipeline for a Netflix-like application using AWS and Kubernetes. It covers the following stages:
	1.	Containerization: The application is packaged in a Docker container and deployed locally on an EC2 instance for testing.
	2.	Security: Security scanning and integration are implemented at the build phase to ensure a secure deployment.
	3.	CI/CD Automation: Jenkins automates the build, test, and deployment cycle, pushing images to Docker Hub for seamless integration.
	4.	Monitoring and Observability: Prometheus and Grafana provide performance insights and help identify bottlenecks.
	5.	Kubernetes Deployment: Helm charts are used to deploy and manage the application on a Kubernetes cluster, ensuring scalability.
	6.	GitOps Workflow: ArgoCD handles declarative, version-controlled application deployments to Kubernetes.
