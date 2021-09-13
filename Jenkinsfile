pipeline {
    agent any
    stages {       
        stage('Checkout') {
            steps {
               git 'https://github.com/Pravdany1406/maven-jenkins-pipeline-project.git'
        }
    }
        stage ('Build') {
            steps {
                sh 'mvn clean install' 
            }            
      }
        stage ('Test') {
            steps {
                sh 'mvn test' 
            }            
      }
    }
}
