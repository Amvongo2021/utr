pipeline {
    agent any
    triggers{
        pollSCM '* * * * * '
    }
    tools {
       maven 'M2_HOME' 
    }
    stages {
       stage ('build'){
          steps {
          sh 'mvn clean'
          sh 'mvn install'
          sh 'mvn package'
          sh 'mvn test'
          sh 'mvn compile'
         
          } 
       } 
       stage ('deploy to tomcat') {
          steps {
              deploy adapters: [tomcat8(credentialsId: 'DockerHUB', path: '', url: 'http://192.168.1.34:8080/')], contextPath: null, war: '**/*.war'
          } 
       }
    }
} 