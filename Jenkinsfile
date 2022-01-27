pipeline {
  agent any
  stages {
    stage('Build') {
      post {
        always {
          mail(subject: 'Deploiement nouvelle version', body: 'Bonjour, Je vous informe qu\'une nouvelle version est disponible sur le github. Cordialement.', to: 'ii_amokrane@esi.dz')
        }

      }
      steps {
        bat './gradlew build'
        bat './gradlew javadoc'
        archiveArtifacts 'build/libs/*.jar'
        archiveArtifacts 'build/reports/**'
      }
    }

    stage('SonarQube analysis') {
      parallel {
        stage('SonarQube analysis') {
          steps {
            withSonarQubeEnv('sonar') {
              bat './gradlew sonarqube'
            }

          }
        }

        stage('Test Reporting') {
          steps {
            cucumber(fileIncludePattern: 'target/report.json', reportTitle: 'CucumberReport')
          }
        }

      }
    }

    stage('Quality gate') {
      post {
        failure {
          mail(subject: 'Failed', body: 'Bonjour,Quality Gate Failed. Cordialement.', to: 'ii_amokrane@esi.dz')
        }

      }
      steps {
        waitForQualityGate true
      }
    }

  }
}