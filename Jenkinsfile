pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t app .'
      }
    }
    stage('Test') {
      steps {
        echo 'TEST 2'
      }
    }
    stage('Deploy') {
      steps {
        echo 'DEPLOY'
      }
    }
  }
}