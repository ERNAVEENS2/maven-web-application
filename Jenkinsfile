pipeline{

agent any

stages{

  stage('CheckOutCode'){
    steps{
    git branch: 'development', credentialsId: '957b543e-6f77-4cef-9aec-82e9b0230975', url: 'https://github.com/devopstrainingblr/maven-web-application-1.git'
	
	}
  }
  
  stage('Build'){
  steps{
  sh  "mvn clean package"
  }
  }
  stage('DeployAppIntoTomcat'){
  steps{
	sshagent(['tomcat']) {
       
    sh "ssh -o StrictHostKeyChecking=no /target/maven-web-application.war ip-172-31-33-36.ap-south-1.compute.internal:/home/ec2-user/apache-tomcat-9.0.73/webapps/" 
	}
   }
   }
  }
  }
