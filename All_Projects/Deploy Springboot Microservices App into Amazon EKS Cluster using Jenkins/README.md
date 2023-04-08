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

#### PROJECT OUTLINE ####
        - https://www.coachdevops.com/2022/01/deploy-springboot-microservices-app.html
        - One EC2 Instance
        - Tools Installation on EC2: AWS CLI, kubectl,eksctl, maven,jenkins,docker, java
        - Add jenkins user to Docker group : sudo usermod -a -G docker jenkins
        - Required jenkins plugins: Docker, Docker pipeline and Kubernetes Deploy plug-ins are installed in Jenkins
        - EKS cluster setup https://www.coachdevops.com/2022/02/create-amazon-eks-cluster-by-eksctl-how.html
        - Docker jenkins integraiton: 
        - Git repository clone: 
        
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
6. Jenkins [here](https://www.jenkins.io/doc/book/installing/linux/#debianubuntu)
7. Docker  [here](https://www.coachdevops.com/2019/05/install-docker-ubuntu-how-to-install.html)

#### Install Docker on Ubuntu ####
1. sudo apt install docker.io -y
2. Add Ubuntu user to Docker group : sudo usermod -aG docker $USER
3. sudo systemctl start docker
4. sudo systemctl enable docker
5. sudo systemctl status docker

#### EKS Cluster Setup ####
* Switch to Jenkins user: sudo su - jenkins
* Create EKS Cluster with two worker nodes using eksctl

        eksctl create cluster --name demo-eks --region us-east-2 --nodegroup-name my-nodes --node-type t3.small --managed --nodes 2     (Change region as per your account)
* the above command should create a EKS cluster in AWS, it might take 15 to 20 mins. The eksctl tool uses CloudFormation under the hood, creating one stack for the EKS master control plane and another stack for the worker nodes.
        
        eksctl get cluster --name demo-eks --region us-east-2

* kubeconfig file be updated under /var/lib/jenkins/.kube folder.
* you can view the kubeconfig file by entering the below command:
