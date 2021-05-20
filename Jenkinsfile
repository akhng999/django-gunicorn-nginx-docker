pipeline {
  environment {
    registry = "akhng999/nginx"
    registryCredential = 'dockerhub'
    dockerImage = ''
    NGINX_REPO_CERT = credentials("NGINX_REPO_DEV_CERT")
    NGINX_REPO_KEY = credentials("NGINX_REPO_DEV_KEY")
   }
  agent any
  stages {
    stage('Building image') {
      steps{
          sh "cp django.env.example django.env"
          sh 'echo ${NGINX_REPO_CERT} > "etc/ssl/nginx/nginx-repo.crt"'
          sh 'echo ${NGINX_REPO_KEY} > "etc/ssl/nginx/nginx-repo.key"'
          sh 'docker-compose build'
      }
    }
  }
}