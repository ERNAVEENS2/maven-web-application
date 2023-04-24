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
	deploy adapters: [tomcat9(path: '', url: 'http://13.232.79.69:8080/')], contextPath: '/home/ec2-user/apache-tomcat-9.0.73/webapps', war: '/home/ec2-user/java_application/workspace/maven-web-application/target'  
 /* sshagent(['bfe1b3c1-c29b-4a4d-b97a-c068b7748cd0']) {
   sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@172-31-33-36:/opt/apache-tomcat-9.0.73/webapps/"    
  */
  }
  }
  }
}
