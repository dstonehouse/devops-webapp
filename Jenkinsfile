pipeline {
  agent any
  stages {
    stage('Clone') {
      steps {
        git(url: 'https://github.com/dstonehouse/devops-webapp/tree/master', branch: 'master')
      }
    }

    stage('Build') {
      steps {
        sh '''whoami
date
echo $PATH
pwd
ls -la
./gradlew build --info'''
      }
    }

    stage('Publish') {
      steps {
        archiveArtifacts(artifacts: 'build/libs/*.war', fingerprint: true, onlyIfSuccessful: true)
      }
    }

  }
}