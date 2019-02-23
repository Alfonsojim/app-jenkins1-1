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
        echo 'Test'
        sh 'docker run -it app'
        sh '/bin/nc -vz localhost 22'
        sh '/bin/nc -vz localhost 80'
      }
      post{
        sh 'docker stop app'
      }
    }
    stage('Push Registry') {
      steps {
        sh 'docker tag app mmiguel80/app:stable'
        sh 'docker push mmiguel80/app:stable'
      }
    }
  }
}