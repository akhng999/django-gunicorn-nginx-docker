pipeline {
  environment {
    registry = "akhng999/nginx"
    registryCredential = 'dockerhub'
    dockerImage = ''
    NGINX_REPO_CERT = credentials("NGINX_REPO_EVAL_CERT")
    NGINX_REPO_KEY = credentials("NGINX_REPO_EVAL_KEY")
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