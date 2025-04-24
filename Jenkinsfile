pipeline {
  agent any

  environment {
    IMAGE_NAME = 'arunagiri92/dev'
  }

  stages {
    stage('Checkout') {
      steps {
        git branch: 'dev', url: 'https://github.com/Giri-AA/devops-build.git'
      }
    }

    stage('Build Docker Image') {
      steps {
        script {
          bat "docker build -t %IMAGE_NAME% ."
        }
      }
    }

    stage('Push to Docker Hub') {
      steps {
        script {
          withDockerRegistry([credentialsId: 'docker-hub-creds', url: '']) {
            bat "docker push %IMAGE_NAME%"
          }
        }
      }
    }
  }
}
