### Technologies and tools
The frontend is a python Flask web application running on port 5153 (app). The app is deployed as a k8s service.
The app connects to a PostgreSQL database (DB) on port 5432. The DB runs as a k8s service.
A GitHub repository stores the source code.
An AWS ECR repository stores the images of the app.
An AWS Codebuild pipeline builds images of the app and pushes them to the ECR repository.
The app and DB services run on nodes in a nodegroup of an AWS EKS cluster.
AWS Cloudwatch monitors and collects data from the AWS EKS cluster.

### Setup
1. Create a repository for the coworking project
2. Create an AWS EKS cluster with a nodegroup to run the DB and app services
3. Create the DB
4. Create an Amazon ECR repository
5. Create a AWS CodeBuild pipeline that automatically builds the app when changes get pushed to the repository
6. Configure AWS CloudWatch for the cluster

### How to deploy changes
Simply push code changes to the repository. This will trigger an automatic rebuild of the image defined at analytics/Dockerfile.