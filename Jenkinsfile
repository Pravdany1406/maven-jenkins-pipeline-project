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
                    java -jar /var/lib/jenkins/.m2/repository/org/dany/maven.sample/0.0.1-SNAPSHOT/maven.sample-0.0.1-SNAPSHOT.jar
                }
      }
    }
}
