* Different between Build periodically and Poll SCM
* Copy Jenkins jobs from one server to another
* Secret text in Jenkins 
* Jenkins Backup 
         - https://www.youtube.com/watch?v=grQ4cAcj81U&list=PLVx1qovxj-akoYTAboxT1AbHlPmrvRYYZ&index=15
* Jenkins dynamic parameterization 
* Jenkins Shared Library | Re-usability of Jenkins pipeline
* How to pass parameters to downstream job
* How to disable username and password authentiction 
* Important plugins
* Jenkins master-slave setup 
        - https://www.youtube.com/watch?v=pzG_ZQNbZug&list=PLVx1qovxj-akoYTAboxT1AbHlPmrvRYYZ&index=25
        - https://www.youtube.com/watch?v=655a1itG3xg&list=PLVx1qovxj-akoYTAboxT1AbHlPmrvRYYZ&index=26
* matrix and Role-based authentication | Fix Jenkins admin password forgot 
         - https://www.youtube.com/watch?v=iPBNEWUocjs&list=PLVx1qovxj-akoYTAboxT1AbHlPmrvRYYZ&index=13
* Jenkins declarative vs scripted pipeline
* Jenkinsfile | Write Jenkinsfile to build docker image from Dockerfile   
         - https://www.youtube.com/watch?v=aAWALhp6wSE&list=PLVx1qovxj-akoYTAboxT1AbHlPmrvRYYZ&index=19
* Jenkins pipeline for maven project| upstream and dwonstream jobs  
         - https://www.youtube.com/watch?v=ctDJryQU7l4&list=PLVx1qovxj-akoYTAboxT1AbHlPmrvRYYZ&index=21
    

#### Installing Jenkins ####
https://www.jenkins.io/doc/book/installing/
1. Using Docker
2. Kuberntes
3. Linux
4. Windows
5. WAR File

#### Pipeline ####
https://www.jenkins.io/doc/book/pipeline/
1. Declarative versus Scripted Pipeline
         - A Jenkinsfile can be written using two types of syntax - Declarative and Scripted.
 ```        
   Jenkinsfile (Declarative Pipeline)
pipeline {
    agent any 
    stages {
        stage('Build') { 
            steps {
                // 
            }
        }
        stage('Test') { 
            steps {
                // 
            }
        }
        stage('Deploy') { 
            steps {
                // 
            }
        }
    }
}
```
2. Scripted Pipeline
```
Jenkinsfile (Scripted Pipeline)
node {  
    stage('Build') { 
        // 
    }
    stage('Test') { 
        // 
    }
    stage('Deploy') { 
        // 
    }
}
```

#### What is Blue Ocean? ####
Blue Ocean as it stands provides easy-to-use Pipeline visualization. It was intended to be a rethink of the Jenkins user experience, designed from the ground up for Jenkins Pipeline. Blue Ocean was intended to reduce clutter and increases clarity for all users.

#### Master slave configuration ####
1] https://www.coachdevops.com/2021/06/jenkins-build-agent-setup-how-to-setup.html
2] 
