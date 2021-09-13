pipeline {
    agent any
    tools {
        maven 'Maven 3.8.2'
        
    }
    stages {
        stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                '''
            }
        }
        stage('Checkout') {
            steps {
               git 'https://github.com/Pravdany1406/maven-jenkins-pipeline-project.git'
        }
    }
        stage ('Build') {
            steps {
                sh 'mvn install' 
            }
            
                }
    }
}
