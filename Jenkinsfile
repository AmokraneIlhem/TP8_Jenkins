pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat './gradlew build'
        bat './gradlew javadoc'
        archiveArtifacts 'build/libs/*.jar'
        archiveArtifacts 'build/reports/**'
        mail(subject: 'Deploiement nouvelle version', body: 'Bonjour, Je vous informe qu\'une nouvelle version est disponible sur le github. Cordialement.', to: 'ii_amokrane@esi.dz')
      }
    }

  }
}













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
    }
    post {

failure {
echo "Build failed"}
success {
echo "Build succeeded" }
stage('Mail') {

      steps {
        mail(subject: 'Nouvelle Version', body: 'Bonjour, une nouvelle version vient d\'etre ajoutée . Cordialement', to: 'ii_amokrane@esi.dz')
      }
}
    }

  }
}
