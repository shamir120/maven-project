pipeline {
    agent any
stages {
    stage('checkout scm') {
        steps {
         checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'Git-creds', url: 'https://github.com/shamir120/maven-project.git']]])   
            }
        } 
    stage('build') {
        steps {
            sh 'mvn clean install'
            }
        }
    stage('test') {
        steps {
            sh 'mvn test'
            }
        }  
   }
}
