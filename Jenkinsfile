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
      stage('SonarQube Analysis') {
    def mvn = tool 'Default Maven';
    withSonarQubeEnv() {
      sh "${mvn}/bin/mvn clean verify sonar:sonar -Dsonar.projectKey=maven-project"
    }
  }
    stage('test') {
        steps {
            sh 'mvn test'
            }
        }  
   }
}
