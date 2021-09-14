pipeline {
    agent { label 'slave1' }
    environment {
        AWS_ACCESS_KEY_ID     = credentials('aws-s3')
        AWS_SECRET_ACCESS_KEY = credentials('aws-s3')
    }
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
        stage('s3 logging'){
            steps {
              withCredentials(bindings: [ credentialsId: 'aws-s3', defaultRegion: 'us-east-1'])
              echo "job logs to s3"
              cat ''' ${JENKINS_HOME}/jobs/${JOB_NAME}/builds/${BUILD_NUMBER}/log >> ${BUILD_NUMBER}.log '''
              sh ''' aws s3 cp  ${BUILD_NUMBER}.log s3://jenkinss3log/logs/ '''
       }
     }
  }
}
