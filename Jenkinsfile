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

    stage('Mail') {
      steps {
        mail(subject: 'Nouvelle Version', body: 'Bonjour, une nouvelle version vient d\'etre ajoutée . Cordialement', to: 'ii_amokrane@esi.dz')
      }
    }

  }
}