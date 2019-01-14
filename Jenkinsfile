pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat 'C:\\gradle-4.10.2-all\\gradle-4.10.2\\bin\\gradle'
        archiveArtifacts 'build/lib/*.jar'
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