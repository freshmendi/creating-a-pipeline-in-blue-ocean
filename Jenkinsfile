pipeline {
  agent {
    docker {
      image 'node:6-alpine'
      args '-p 3003:3000'
    }

  }
  stages {
    stage('build') {
      steps {
        sh 'npm install'
      }
    }
    stage('Test ') {
      parallel {
        stage('Test ') {
          steps {
            sh './jenkins/scripts/test.sh'
          }
        }
        stage('rollback_to_dev') {
          steps {
            sh 'sh  date'
          }
        }
      }
    }
    stage('Deliver ') {
      steps {
        sh './jenkins/scripts/deliver.sh'
        input 'Finished using the web site? (Click "Proceed" to continue)'
        sh './jenkins/scripts/kill.sh'
      }
    }
  }
  environment {
    CI = 'true'
  }
}