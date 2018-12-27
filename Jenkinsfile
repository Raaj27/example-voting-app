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

          sh 'docker push dockersamples/result'
        }
      }
    }
    stage('Push vote image') {
      
      steps {
        withDockerRegistry(credentialsId: 'dockerhub', url:'https://registry.hub.docker.com') {
          sh 'docker push dockersamples/vote'
        }
      }
    }
    stage('Push worker image') {
      
      steps {
        withDockerRegistry(credentialsId: 'dockerhub', url:'https://registry.hub.docker.com') {
          sh 'docker push dockersamples/worker'
        }
      }
    }
  }
}
