## Project 1 Continuous Integration 
![image](https://user-images.githubusercontent.com/46215433/219878271-4ab530d7-9cf8-4f6d-b5b9-d988bd85ad25.png)

# Pre-requisite #
* AWS Account
* Visual Studio Code
* GitHub Account
* DockerHub Account
* Application Source code repo: https://github.com/sagarkulkarni1989/mrdevops_nexus_helm_cicd_app.git
				- https://github.com/sagarkulkarni1989/demo-counter-app.git

# Tools
1. AWS - Security Group, EC2
2. Source Code Management:Git
3. CI/CD : Jenkins 
4. Build Tool : Maven
5. Code quality check: SonarQube 
6. Artifact repository : Nexus and DockerHub
7. Containerization : Docker 

# Stages:
- Git Checkout
- Unit Test
- Intgration Test
- Maven Build
- Static Code Analysis 
- Quality Gates 
- Upload file to Nexus 
- Docker image build
- Push image to docker hub

# Infrastructure  Setup 
1. AWS - EC2 Instances : Type: Ubuntu 20.04  t2.medium , security group - inbound rules: all trafic for anywhere.  access key etc
2. jenkins setup: 
      * https://github.com/sagarkulkarni1989/Devops_Projects/blob/main/Project1Continuous_Integration/jenkins.sh
      * https://github.com/sagarkulkarni1989/Devops_Projects/blob/main/Project1Continuous_Integration/docker.sh
      * Install Maven on Jenkins VM
	  
3. SonarQube(you can create dedicated VM or use same Jenkins VM):https://github.com/sagarkulkarni1989/Devops_Projects/blob/main/Project1Continuous_Integration/sonarqube.sh
4. Nexus: https://github.com/sagarkulkarni1989/Devops_Projects/blob/main/Project1Continuous_Integration/Nexus.sh

# Access all through console 
1. Jenkins : http://<public_IP>:8080
2. SonarQube: http://<public_IP>:9000
3. Nexus: http://<Public_IP>:8081

# Configuration #
1. On Jenkins console
    - Manage Jenkins - Manage Plugins
    	- SonarQube Scanner
    	- Sonar Quality Gates
    	- Quality Gates
    	- Sonar Gerrit
	    - SonarQube Generic Coverage
	    - docker and docker-pipeline 
	    - nexus-artifact-uploader
	    - pipeline-utility-steps
    - Manage Jenkins - Manage Credentials
  		 - Sonar-token   	 kind:secret text   	 ID:sonar-token
	         -  for nexus   Kind: Username and password
		 - for dockerhub  kind:secret text   ID: git_creds     (Dockerhub credentials)
2. SonarQube Webhook:
	- Administration - configurations- webhooks
	- name: jenkins-webhook     URL:http://3.108.64.16:8080/sonarqube-webhook/  <jenkins public_IP:8080>/
3. Configure Sonarqube Server:
	- Manage Jenkins - Configure System - sonarqube server
4. Nexus Repository Creation:
	- maven hosted2 = 1] release 2] snapshot   AppName: 1. demoapp-snapshot 2. demoapp-release
5. Generate Sonarqube Token: Administration – Security – Users  (Use this token while creating sonar-token Jenkins credentials)
	
# Reference snapshots:
* Sonarqube Server configuration in Jenkins 
![image](https://user-images.githubusercontent.com/46215433/219933058-7aaac154-5728-48be-87d3-e771971d18a1.png)

* Sonarqube webhook setup 
![image](https://user-images.githubusercontent.com/46215433/219933086-4b277da0-fbcf-4afe-8ac9-461917763b90.png)


* Troubleshooting during implementation 
* Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Get      http://%2Fvar%2Frun%2Fdocker.sock/v1.26/containers/hello-world/json: dial unix /var/run/docker.sock: connect: permission denied.
WA: https://www.edureka.co/community/7764/trying-docker-jenkins-pipeline-facing-jenkins-pipeline-socket

![image](https://user-images.githubusercontent.com/46215433/219878288-ca13f5d8-8b38-47b2-b467-d7836f10e653.png)

