pipeline {
   agent {label 'Test'}
   stages {
      stage("Docker build") {
         steps {
            sh "docker build -t amitbaranes/dotnet-demo-sela:${env.BUILD_ID} ."
         }
      }
      stage("Login to docker hub") {
         steps {
           sh "docker login --username=${env.DOCKERHUB_USER_NAME} --password=${env.DOCKERHUB_PASSWORD}"
         }
      }
      stage("Docker push") {
         steps {
           sh "docker push  amitbaranes/dotnet-demo-sela:${VERSION}"
         }
      }
   } 
    post {
        always {
            cleanWs deleteDirs: true, notFailBuild: true
        }
    }
}