pipeline {
   agent {label 'Production'}
   stages {
      stage('Restore')
      {
         steps {
           sh "dotnet restore"
         }
      }
      stage("Publish") {
         steps {
           sh "sudo dotnet publish -c release -o /app --no-restore"
         }
      }
   } 
    post {
        always {
            cleanWs deleteDirs: true, notFailBuild: true
        }
    }
}