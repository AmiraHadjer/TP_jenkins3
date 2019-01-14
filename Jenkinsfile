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
    stage('test repporting') {
      steps {
        jacoco()
      }
    }
    stage('Upload') {
      steps {
        bat 'gradle uploadArchives'
      }
    }
    stage('slack notification') {
      steps {
        slackSend(token: '41FJUHEG1ckO3MIeu7UUBgkO', baseUrl: 'https://esi-bouali-sil1.slack.com/services/hooks/jenkins-ci/', message: 'message slack')
      }
    }
  }
}