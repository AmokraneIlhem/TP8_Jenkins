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
    stage('SonarQube analysis') {
                    steps {
                        withSonarQubeEnv('sonar') {
                            bat "./gradlew sonarqube"
                        }
                    }
         }
         stage("Quality gate") {
                    steps {
                        waitForQualityGate abortPipeline: true
                    }
           post{
             failure {
               mail(subject: 'Failed', body: 'Bonjour,Quality Gate Failed. Cordialement.', to: 'ii_amokrane@esi.dz')
             }
           }
         }

  }
}
