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
       
    sh "scp /home/ec2-user/java_application/workspace/maven-web-application/target/maven-web-application.war ec2-user@172.31.33.36:/home/ec2-user/apache-tomcat-9.0.73/webapps"
	}
   }
   }
  }
  }
