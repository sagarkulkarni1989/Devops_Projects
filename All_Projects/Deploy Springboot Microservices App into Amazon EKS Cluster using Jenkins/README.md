# Deploy Springboot Microservices App into Amazon EKS Cluster using Jenkins Pipeline and Kubectl CLI Plug-in | Containerize Springboot App and Deploy into EKS Cluster using Jenkins Pipeline #
* We will learn how to automate springboot microservices builds using Jenkins pipeline and Deploy into AWS EKS Cluster with help of Kubernetes CLI plug-in.
* We will use Springboot Microservices based Java application. I have already created a repo with source code + Dockerfile. The repo also have Jenkinsfile for automating the following:

        - Automating builds using Jenkins
        - Automating Docker image creation
        - Automating Docker image upload into AWS ECR
        - Automating Docker Containers Deployments to Kubernetes Cluster        
* What is Amazon EKS: Amazon EKS is a fully managed container orchestration service. 
EKS allows you to quickly deploy a production ready Kubernetes cluster in AWS, deploy and manage containerized applications more easily with a fully managed Kubernetes service.
EKS takes care of master node/control plane. We need to create worker nodes.

* EKS cluster can be created in following ways:
  1. AWS console
  2. AWS CLI
  3. eksctl command
  4. using Terraform

We will create EKS cluster using eksctl command line tool.


### AWS EC2 Instance Setup ###
    - Login to an AWS account using a user with admin privileges and ensure your region is set to us-east-1 N. Virginia.
    - Move to the EC2 console. Click Launch Instance.For name use Main-Server
    - Select AMIs as Ubuntu and select Instance Type as t2.medium. Create new Key Pair and Create a new Security Group with traffic allowed from ssh, http and https.
    - Click on launch Instance and once EC2 Instance started, connect to it with EC2 Instance Connect.
    
#### Tools Setup on EC2 ####
1. Install AWS CLI – Command line tools for working with AWS services, including Amazon EKS.[here](https://sunitabachhav2007.hashnode.dev/prometheus-and-grafana-dashboard-on-eks-cluster-using-helm-chart)  
2. Install eksctl – A command line tool for working with EKS clusters that automates many individual tasks. [here](https://sunitabachhav2007.hashnode.dev/prometheus-and-grafana-dashboard-on-eks-cluster-using-helm-chart)
3. Install kubectl  – A command line tool for working with Kubernetes clusters. [here](https://sunitabachhav2007.hashnode.dev/prometheus-and-grafana-dashboard-on-eks-cluster-using-helm-chart)
4. Java
5. Maven
6. Jenkins
7. Docker

