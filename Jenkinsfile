pipeline {
  agent {
    docker {
      image 'node:6-alpine'
      args '-p 3003:3003'
    }

  }
  stages {
    stage('build') {
      steps {
        sh 'npm install'
      }
    }
    stage('Test ') {
      steps {
        sh './jenkins/scripts/test.sh'
      }
    }
  }
  environment {
    CI = 'true'
  }
}