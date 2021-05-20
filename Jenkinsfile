pipeline {
  environment {
    registry = "akhng999/nginx"
    registryCredential = 'dockerhub'
    dockerImage = ''
    NGINX_REPO_CERT = credentials("NGINX_REPO_DEV_CERT_FILE")
    NGINX_REPO_KEY = credentials("NGINX_REPO_DEV_KEY_FILE")
   }
  agent any
  stages {
    stage('Building image') {
      steps{
          sh "cp django.env.example django.env"
          sh 'cat ${NGINX_REPO_CERT} > "nginx/nginx-repo.crt"'
          sh 'cat ${NGINX_REPO_KEY} > "nginx/nginx-repo.key"'
          sh 'docker-compose build'
      }
    }
  }
}