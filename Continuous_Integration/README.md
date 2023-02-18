## Project 1 Continuous Integration 

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
2. enkins setup: 
3. SonarQube
4. Nexus: 

# Access all through console 
1. Jenkins : http://<public_IP>:8080
2. SonarQube: http://<public_IP>:9000
3. Nexus: http://<Public_IP>:8081

Configuration : 
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
