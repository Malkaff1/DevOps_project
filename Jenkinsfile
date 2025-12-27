pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        echo 'Code is already checked out by Jenkins SCM'
      }
    }

    stage('Build Image') {
      steps {
        sh 'docker build -t my-nginx-web ./docker/nginx'
      }
    }

    stage('Run Container') {
      steps {
        sh 'docker rm -f nginx-web || true'
        sh 'docker run -d -p 8080:80 --name nginx-web my-nginx-web'
      }
    }

    stage('Smoke Test') {
      steps {
        sh 'curl -f http://localhost:8080'
      }
    }
  }