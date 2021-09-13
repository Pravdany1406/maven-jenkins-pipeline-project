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
                echo "Maven Compile"
                sh 'mvn clean compile' 
            }            
      }
        stage ('Test') {
            steps {
                echo "Maven Test and Packaging"
                sh 'mvn test install' 
            }
            post {
                success {
                    echo "Hello World"
           }
        }
     }
  }
}
