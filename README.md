# Flask RDS Application

## Overview
This project is a Python Flask web application that connects to an Amazon RDS MySQL database. It demonstrates how to deploy a Flask application on a Kubernetes cluster and access the database.

## Features
- User registration with form validation.
- Connection to an Amazon RDS MySQL database.
- Deployed on a Kubernetes cluster using EKS.
- document https://docs.google.com/document/d/10PpxYTwQlyMNxpyneXmhzCe0nzjQtSmYbhFsxXYKrKI/edit?usp=sharing

## Prerequisites
Before you begin, ensure you have the following installed:
- [Docker](https://docs.docker.com/get-docker/)
- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
- [eksctl](https://eksctl.io/introduction/#installation)
- [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)

## Getting Started

### 1. Clone the Repository
```bash
git clone https://github.com/sandeep-kalasgonda/flask-rds.git
cd flask-rds
```

### 2. Build the Docker Image
```bash
docker build -t sandeep3414/flask-rsd .
```

### 3. Push the Image to Docker Hub
```bash
docker push sandeep3414/flask-rsd
```

### 4. Create an RDS MySQL Database
Follow the [AWS RDS documentation](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_Overview.html) to create your database.

### 5. Initialize the EKS Cluster
```bash
eksctl create cluster --name test-cluster1 --version 1.28 --region us-east-1 --nodegroup-name standard-workers --node-type t3.small --nodes 2 --nodes-min 1 --nodes-max 2 --managed
```

### 6. Deploy the Application
```bash
kubectl apply -f deployment.yaml
kubectl apply -f services.yaml
```

### 7. Test the Application
To access the application, use the Load Balancer DNS link provided by Kubernetes.

## Access the Application
Once deployed, you can access the application at:
```
http://<LoadBalancer-DNS-Name>
```

## Check Database Connection
Make sure your application can connect to the RDS database using the environment variables set in your deployment configuration.

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments
- Flask
- Kubernetes
- Amazon RDS
