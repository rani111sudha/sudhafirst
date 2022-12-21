pipeline {
    agent any
        stages {
            stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }

    
    
        stage('Git checkout') {
            steps {
                git branch: 'main', credentialsId: 'Git-cred', url: 'https://github.com/rani111sudha/sudhafirst'
                
                
            }
        }
        
     
            
        stage('Maven build') {
            steps {
               sh "mvn clean package"
               
                }
            }
                                                 stage('Tomcat Deploy') {
                                                  steps {
                                                     sshagent(['Tomcat-creds']) {
                                                        sh "scp -o StrictHostKeyChecking=no target/*.war ec2-user@172.31.17.53:/opt/tomcat9/webapps"
                                                        sh "ssh ec2-user@172.31.17.53 /opt/tomcat9/bin/shutdown.sh"
                                                        sh "ssh ec2-user@172.31.17.53 /opt/tomcat9/bin/startup.sh"
                                                        
                                                     
        }
        
                                                      
                                                  }
                                                     }  
                                                         }
    }
    
