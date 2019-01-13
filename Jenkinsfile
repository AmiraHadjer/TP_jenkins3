pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat 'C:\\gradle-4.10.2-all\\gradle-4.10.2\\bin\\gradle'
        archiveArtifacts 'lib/*.jar'
      }
    }
  }
}