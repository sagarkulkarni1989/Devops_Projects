## DevOps Tools ##
Add Image here

# SDLC #
Software Development Process is a long journey. Multiple components of software need to be developed simultaneously within short deadline.
* Methods of SDLC
1. Waterfall
2. Spiral
3. Agile
4. Scrum
5. Lean
# DevOps ? #
DevOps is more of a development culture that focuses on producing quality product as efficiently as possible.
Its helps automate the whole software development process and hence increase efficiency and decrease costs.
1. Improves deployment frequency 
2. Achieves faster time to market
3. Improves mean time to recovery
4. Lowers the failure rate of new releases

# Agile # 
Its a software development methodology which promotes shorter development life-cycles and where there is a feedback loop that priorities the customers fedback and changes that need to be made according to it.
1. Transparency
2. Predictable Costs and Schedule 
3. Allows for change
4. Improve Quality

![image](https://user-images.githubusercontent.com/46215433/227969872-36c3fc4a-9e2d-4132-801d-4ee09af1bc0c.png)

* Devops and agile
1. Communication
	* Agile : Dev+ test+ BA
	* DevOps: Dev+ test+ BA + Ops
2. Automation and Quick feedback 
	* Agile : Interations, Extreme programming and CI/CD 
	* DevOps : Agile + IaaC + Observability

# DevSecOps #
DevSecOps is the practice of integrating security into a continuous integration, continuous delivery, and continuous deployment pipeline. By incorporating DevOps values into software security, security verification becomes an active, integrated part of the development process.
Much like DevOps, DevSecOps is an organizational and technical methodology that combines project management workflows with automated IT tools. DevSecOps integrates active security audits and security testing into agile development and DevOps workflows.

To implement DevSecOps, teams should: 

* Introduce security throughout the software development lifecycle in order to minimize vulnerabilities in software code.
* Ensure the entire DevOps team, including developers and operations teams, share responsibility for following security best practices.
* Enable automated security checks at each stage of software delivery by integrating security controls, tools, and processes into the DevOps workflow.
* With DevSecOps, security should be applied to each phase of the typical DevOps pipeline: plan, build, test, deploy, operate, and observe.

![image](https://user-images.githubusercontent.com/46215433/228709156-f34d8e9d-1a92-4ba4-bd5b-359f95f24631.png)

1. Plan:The plan phase is the least automated phase of DevSecOps, involving collaboration, discussion, review, and strategy of security analysis.
	A popular planning tool for DevSecOps is IriusRisk,Jira Software etc
2. Build: The build phase begins once developers commit code to the source repository. DevSecOps build tools focus on automated security analysis against the build output artifact. Important security practices include software component analysis, static application software testing (SAST), and unit tests. Tools can be plugged into an existing CI/CD pipeline to automate these tests.Some well-known tools to execute build phase analysis include: OWASP Dependency-Check, SonarQube, SourceClear, Retire.js, Checkmarx, and Snyk.Some of the more popular security code tools include Gerrit, Phabricator, SpotBugs, PMD, CheckStyle,
3.Test: The test phase is triggered after a build artifact is created and successfully deployed to staging or testing environments. A comprehensive test suite takes a considerable amount of time to execute.The test phase uses dynamic application security testing (DAST) tools to detect live application flows like user authentication, authorization, SQL injection, and API-related endpoints.including BDD Automated Security Tests, JBroFuzz, Boofuzz, OWASP ZAP, Arachi, IBM AppScan
4.Deploy:If the previous phases pass successfully, it's time to deploy the build artifact to production. The security areas of concern to address during the deploy phase are those that only happen against the live production system. For example, any differences in configuration between the production environment and the previous staging and development environments should be thoroughly reviewed. Production TLS and DRM certificates should be validated and reviewed for upcoming renewal. Configuration management tools are a key ingredient for security in the release phase, since they provide visibility into the static configuration of a dynamic infrastructure.Some popular configuration management tools include Ansible, Puppet, HashiCorp Terraform, Chef, and Docker. 



## DevOps Knowledge ##
1. Project1: Devops project with Ansible(GIT-Jenkins-Ansible-Webserver(httpd))  Done, document pending
2. Project2: Devops Project with Docker  Yet to start
3. Project3: Devops project with Kubernetes Yet to start
1. Project4 : Continuous Integration 
2. Project5 : Continuous Delivery on AWS(Java Application)
3. Project6 : Kubernetes Monitoring Using Prometheus and Grafana
4. Project7 : Setting up Promethues and Grafana for monitoring servers



# Technical Stack #
* Source code management: GIT
* Build Tool: Maven, Gradle
* CI/CD: Jenkins https://github.com/sagarkulkarni1989/Devops_Projects/blob/main/Technical_stack/Jenkins/README.md

# Relational vs. Non-Relational Database #
* https://www.guru99.com/nosql-tutorial.html

* A relational database is structured, meaning the data is organized in tables. Many times, the data within these tables have relationships with one another, or dependencies. 
* SQL Databases (Relational) SQL is short for Structured Query Language, basically meaning a very firm way of sorting through data in the form of tables, columns, and rows.
* popular SQL database systems include: Oracle, Microsoft SQL Server, PostgreSQL, MySQL, MariaDB
* NoSQL Databases (Non-Relational)In contrast to a relational database, a NoSQL database is one that is less structured/confined in format, and thus, allows for more flexibility and adaptability.
* popular NoSQL databases include: MongoDB, Google Cloud Firestore, Cassandra,Redis, Amazon DynamoDB
1. Type of NoSQL Databse
      - Document-based databases : MongoDB, Riak, 
      - Key-value stores : Redis
      - Column-oriented databases: Cassandra
      - Graph-based databases: Neo4J, FlockDB 



