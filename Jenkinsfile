pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        bat './gradlew build     '
        bat './gradlew javadoc'
        archiveArtifacts 'build/libs/*.jar'
        archiveArtifacts 'build/reports/**'
        mail(subject: 'd�ploiement nouvelle version  ', body: 'Bonjour, je vous informe que une nouvelle version vient d\'�tre ajout�e . Cordialement.', to: 'ii_amokrane@esi.dz')
      }
    }

  }
}