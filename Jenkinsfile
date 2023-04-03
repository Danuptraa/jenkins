pipeline {
  agent any
  stages {
    stage('Install Dependencies') {
      steps {
        sh 'npm install'
      }
    }
    stage('Build') {
      steps {
        sh 'ng build --prod'
      }
    }
    stage('Test') {
      steps {
        sh 'ng test'
      }
    }
    stage('Deploy') {
      steps {
        sshagent(['danuptraa']) {
          sh 'scp -r dist/ root@178.128.58.84:/home/project/manatra'
          sh 'ssh root@178.128.58.84 "cd /home/project/manatra && pm2 restart manatra"'
        }
      }
    }
  }
}
