pipeline {
  agent any
  environment {
        //be sure to replace "willbla" with your own Docker Hub username
        DOCKER_IMAGE_NAME = "devenv27/dockersamples"
    }
  stages {
    stage('Build result') {
      steps {
        sh 'docker build -t dockersamples/result ./result'
      }
    } 
    stage('Build vote') {
      steps {
        sh 'docker build -t dockersamples/vote ./vote'
      }
    }
    stage('Build worker') {
      steps {
        sh 'docker build -t dockersamples/worker ./worker'
      }
    }
    stage('Push result image') {
      
      steps {
        withDockerRegistry(credentialsId: 'dockerhub', url:'https://registry.hub.docker.com') {
          sh 'docker tag dockersamples/result devenv27/result'
          sh 'docker push devenv27/result'
        }
      }
    }
    stage('Push vote image') {
      
      steps {
        withDockerRegistry(credentialsId: 'dockerhub', url:'https://registry.hub.docker.com') {
sh 'docker tag dockersamples/vote devenv27/vote'
          sh 'docker push devenv27/vote'        }
      }
    }
    stage('Push worker image') {
      
      steps {
        withDockerRegistry(credentialsId: 'dockerhub', url:'https://registry.hub.docker.com') {
sh 'docker tag dockersamples/worker devenv27/worker'
          sh 'docker push devenv27/worker'        }
      }
    }
  }
}
