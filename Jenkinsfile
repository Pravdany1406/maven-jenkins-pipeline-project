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
        stage('s3 ariticaft publishing'){
            steps {
              echo "publishing Build aritifacts to s3"
              withCredentials([[
                 $class: 'AmazonWebServicesCredentialsBinding',
                 credentialsId: "aws-s3",
                 accessKeyVariable: 'AWS_ACCESS_KEY_ID',
                 secretKeyVariable: 'AWS_SECRET_ACCESS_KEY'
              ]]) {              
              sh ''' aws s3 cp  /home/ubuntu/jenkins/workspace/test/target/*.jar   s3://jenkinss3log/Artifacts/${BUILD_NUMBER}_maven.sample-0.0.1-SNAPSHOT.jar '''
         }
       }
     }
  }
}
