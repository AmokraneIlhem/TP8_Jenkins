pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat './gradlew build'
        
        bat './gradlew javadoc'
        archiveArtifacts 'build/libs/*.jar'
        archiveArtifacts 'build/reports/**'
       
      }
      post {
        always {
         mail(subject: 'Deploiement nouvelle version', body: 'Bonjour, Je vous informe qu\'une nouvelle version est disponible sur le github. Cordialement.', to: 'ii_amokrane@esi.dz')
        }
   
      }
    }

  }
}
