pipeline {
   agent {label 'Production'}
   environment { 
   NAME = "myapp"
   VERSION = "${env.BUILD_ID}-${env.GIT_COMMIT}"
   IMAGE = "${NAME}:${VERSION}"
    }
   stages {
      stage("Docker build") {
         steps {
            echo "Version : ${VERSION} IMAGE: ${IMAGE}"
            sh "docker build -t amitbaranes/dotnet-demo-sela:latest ."
         }
      }
      stage("Docker push") {
         steps {
           sh "docker push  amitbaranes/dotnet-demo-sela:latest"
         }
      }
      }
   } 
    post {
        always {
            cleanWs deleteDirs: true, notFailBuild: true
        }
    }
}