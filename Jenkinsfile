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
        script {
          dockerImage = docker.build("-f nginx/Dockerfile", "-t ${registry}:nginxplus", "--build-arg=NGINX_REPO_CERT=${NGINX_REPO_CERT}", "--build-arg=NGINX_REPO_KEY=${NGINX_REPO_KEY}")
        }
      }
    }
    stage('Deploy Image') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
          }
        }
      }
    }
    stage('Remove Unused docker image') {
      steps{
        sh "docker rmi $registry:nginxplus"
      }
    }
  }
}