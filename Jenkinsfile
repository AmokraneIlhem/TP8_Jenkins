pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat './gradlew build'
<<<<<<< HEAD

        bat './gradlew javadoc'
        archiveArtifacts 'build/libs/*.jar'
        archiveArtifacts 'build/reports/**'

=======
        
        bat './gradlew javadoc'
        archiveArtifacts 'build/libs/*.jar'
        archiveArtifacts 'build/reports/**'
       
>>>>>>> 1a9f319f7a82e299c1eac0a2ca209648e4151e5c
      }
      post {
        always {
         mail(subject: 'Deploiement nouvelle version', body: 'Bonjour, Je vous informe qu\'une nouvelle version est disponible sur le github. Cordialement.', to: 'ii_amokrane@esi.dz')
        }
<<<<<<< HEAD

=======
   
>>>>>>> 1a9f319f7a82e299c1eac0a2ca209648e4151e5c
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
