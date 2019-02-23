pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t app.'
      }
    }
    stage('Test') {
      steps {
        echo 'Test'
        sh 'docker run --rm -d -p 80:80 app'
        sh '/bin/nc -vz localhost 22'
        sh '/bin/nc -vz localhost 80'
        sh 'docker container stop app'
      }
    }
    stage('Push Registry') {
      steps {
        sh 'docker tag app mmiguel80/app:stable'
        sh 'docker push app mmiguel80/app:stable'
      }
    }
  }
}