## Project 1 Monitoring servers using Prometheus and Grafana


# Pre-requisite #
* AWS Account
* Visual Studio Code
* GitHub Account

# Tools
1. AWS - Security Group, EC2
2. Monitoring Tool : Prometheus and Grafana


# Infrastructure  Setup 
1. AWS - EC2 Instances : Type: Ubuntu 20.04 and amazon Linux  t2.micro , security group - inbound rules: all trafic for anywhere.  access key etc
2. Prometheus setup on Amazon Linux: 
      * wget https://github.com/prometheus/prometheus/releases/download/v2.37.6/prometheus-2.37.6.linux-amd64.tar.gz
      * tar -xvf prometheus-2.37.6.linux-amd64.tar.gz
      * cd prometheus-2.37.6.linux-amd64
      * nohup ./prometheus &    or ./prometheus
      * Node exporter : Install it on both machines, we need to install it all the machine which needs to monitor
      		* installation: wget https://github.com/prometheus/node_exporter/releases/download/v1.5.0/node_exporter-1.5.0.linux-amd64.tar.gz 
      		* tar -xvf <XXXX.tar.gz>
	  
3. Prometheus and Grafana: 
	 * docker run -d --name prometheus -p 9090:9090 prom/prometheus
	 * docker run -d --name grafana -p 3000:3000 grafana/grafana


# Access all through console 
1. Jenkins : http://<public_IP>:8080
2. Prometheus: http://<public_IP>:9090
3. Grafana: http://<Public_IP>:3000

# Configuration #
1. Configure Prometheus
	- cd /etc/prometheus
	- vi prometheus.yml
	
	```
	  - job_name: "prometheus"
   	    static_configs:
              - targets: ["localhost:9090"]
         - job_name: "node_exporter"
           static_configs:
              - targets: ["3.110.45.128:9100", "43.204.227.151:9100"]

	```
	

      ![image](https://user-images.githubusercontent.com/46215433/221115509-a9b07705-811b-4d19-83cd-b166edb5792f.png)

5. Grafana setup – 
	- Add your first Data Source
	- Select Prometheus
	- URL: Prometheus URL and save and test
	
	![image](https://user-images.githubusercontent.com/46215433/221116310-89c12129-6f7d-4e95-8169-e07454ed6e87.png)
	
	- Create your first dashboard
	- Add new panel
	- Select Query patterns : Jenkins_plugin_active
	- Select Visualizations: stat  and provide dashboard name and save it
	
	![image](https://user-images.githubusercontent.com/46215433/221117162-65eb0ea4-291c-4bb1-a5d6-a70cffb546ec.png)
	![image](https://user-images.githubusercontent.com/46215433/221117227-5dadb4b6-4b47-4eb7-a390-1a7fed7e1565.png)
	![image](https://user-images.githubusercontent.com/46215433/221117426-984689dc-760a-4cce-a01f-07be1fca425f.png)
	
	![image](https://user-images.githubusercontent.com/46215433/221153371-e25c8ea5-490c-40c7-8331-206383d63528.png)

	





	



