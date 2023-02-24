## Project 1 Monitoring Jenkins with Prometheus and Grafana


# Pre-requisite #
* AWS Account
* Visual Studio Code
* GitHub Account

# Tools
1. AWS - Security Group, EC2
2. CI/CD : Jenkins 
3. Monitoring Tool : Prometheus and Grafana
4. Containerization : Docker 

# Infrastructure  Setup 
1. AWS - EC2 Instances : Type: Ubuntu 20.04  t2.medium , security group - inbound rules: all trafic for anywhere.  access key etc
2. jenkins setup: 
      * https://github.com/sagarkulkarni1989/Devops_Projects/blob/main/Project1Continuous_Integration/jenkins.sh
      * https://github.com/sagarkulkarni1989/Devops_Projects/blob/main/Project1Continuous_Integration/docker.sh
 
	  
3. Prometheus and Grafana: 
	 * docker run -d --name prometheus -p 9090:9090 prom/prometheus
	 * docker run -d --name grafana -p 3000:3000 grafana/grafana


# Access all through console 
1. Jenkins : http://<public_IP>:8080
2. Prometheus: http://<public_IP>:9090
3. Grafana: http://<Public_IP>:3000

# Configuration #
1. On Jenkins console
    - Manage Jenkins - Manage Plugins
    	- Prometheus

2. Configure Prometheus
	- docker exec -it <Container_ID> /bin/sh
	- cd /etc/prometheus
	- vi prometheus.yml
			  - job_name: "jenkins"
    		  - metrics_path: /prometheus
    static_configs:
      - targets: ["13.127.25.100:9090"]
5. Grafana setup – Security – 
	



