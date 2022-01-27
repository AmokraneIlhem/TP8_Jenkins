  stages {
    stage('build') {
      steps {
        bat './gradlew build '
        bat './gradlew javadoc'
        archiveArtifacts 'build/libs/*.jar'
        archiveArtifacts 'build/reports/**'
        mail(subject: 'déploiement nouvelle version  ', body: 'Bonjour, je vous informe que une nouvelle version vient d\'être ajoutée . Cordialement.', to: 'ii_amokrane@esi.dz')
      }
    }
