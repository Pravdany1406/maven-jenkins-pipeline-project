pipeline {
    agent { label 'slave1' }
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
              echo "publishing Build logs to s3"
              withCredentials([[
                 $class: 'AmazonWebServicesCredentialsBinding',
                 credentialsId: "aws-s3",
                 accessKeyVariable: 'AWS_ACCESS_KEY_ID',
                 secretKeyVariable: 'AWS_SECRET_ACCESS_KEY'
              ]]) {              
              sh ''' /usr/bin/aws s3 cp  ${JENKINS_HOME}/jobs/${JOB_NAME}/builds/${BUILD_NUMBER}/log s3://jenkinss3log/logs/${BUILD_NUMBER}.log '''
         }
       }
     }
  }
}
