pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        bat './gradlew build '
           post {
        failure {
  mail(subject: 'Erreur  ', body: 'Bonjour, je vous informe que une nouvelle version vient d\'être ajoutée . Cordialement.', to: 'ii_amokrane@esi.dz')}
success {
mail(subject: 'Success  ', body: 'Bonjour, je vous informe que une nouvelle version vient d\'être ajoutée . Cordialement.', to: 'ii_amokrane@esi.dz')}
    }
       }

      steps {
        bat './gradlew javadoc'
        archiveArtifacts 'build/libs/*.jar'
        archiveArtifacts 'build/reports/**'
      }
    }

  }
}
