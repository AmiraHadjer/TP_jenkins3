pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat 'C:\\gradle-4.10.2-all\\gradle-4.10.2\\bin\\gradle'
        archiveArtifacts 'lib/*.jar'
      }
    }
    stage('sonar') {
      steps {
        withSonarQubeEnv 'C:\\sonarqube-7.3\\bin\\windows-x86-64\\lib\\wrapper'
      }
    }
  }
}