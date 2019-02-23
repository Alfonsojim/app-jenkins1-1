pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t app:test .'
      }
    }
    stage('Test') {
      steps {
        echo 'Test'
        sh 'docker run --rm --name app -id -p 80:80 app:test'
        sh '/bin/nc -vz localhost 22'
        sh '/bin/nc -vz localhost 80'
      }
      post{
        sh 'docker container stop app'
      }
    }
    stage('Push Registry') {
      steps {
        sh 'docker tag app:test mmiguel80/app:stable'
        sh 'docker push app:test mmiguel80/app:stable'
      }
    }
  }
}