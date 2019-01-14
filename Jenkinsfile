pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        bat 'gradle build'
        archiveArtifacts 'build/libs/*.jar'
        bat 'gradle javadoc'
      }
    }
    stage('mail notificaton') {
      steps {
        emailext(subject: 'notification TP', body: 'hello from TP', to: 'fa_bouali@esi.dz')
      }
    }
    stage('quality gate') {
      steps {
        tool 'sonarqube'
        withSonarQubeEnv 'SonarQube Scanner 3.2.0'
      }
    }
  }
}