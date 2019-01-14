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
      parallel {
        stage('quality gate') {
          steps {
            withSonarQubeEnv('sonarqube') {
              bat 'sonar-scanner'
            }

            waitForQualityGate true
          }
        }
        stage('test repporting') {
          steps {
            jacoco()
          }
        }
      }
    }
    stage('') {
      steps {
        bat 'gradle uploadArchives'
      }
    }
  }
}