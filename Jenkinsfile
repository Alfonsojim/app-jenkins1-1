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
        sh 'docker run --rm -d -p 80:80 --name app app:test'
        sh '/bin/nc -vz localhost 22'
        sh '/bin/nc -vz localhost 80'
        sh 'docker container stop app'
      }
    }
    stage('Push Registry') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'dockerHubCred', passwordVariable: 'Password', usernameVariable: 'Username')]) {
          echo 'PASSWORD: '"$Password"
          echo 'USERNAME: '"$Username"
          sh 'docker tag app:test mmiguel80/app:stable'
          sh 'docker push mmiguel80/app:stable'
        }
      }
    }
  }
}