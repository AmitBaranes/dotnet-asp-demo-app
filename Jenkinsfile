pipeline {
   agent {label 'Slave'}
   stages {
      stage('Restore')
      {
         steps {
           sh "sudo dotnet restore"
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