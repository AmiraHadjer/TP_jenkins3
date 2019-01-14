pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat 'gradle build'
        archiveArtifacts 'build/libs/*.jar'
      }
    }
    stage('sonar') {
      steps {
        withSonarQubeEnv('C:\\sonar-scanner-3.2.0.1227-windows\\bin\\sonar-scanner') {
          waitForQualityGate true
        }

      }
    }
  }
}