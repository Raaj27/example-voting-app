pipeline {
  agent any
  
  stages {
    stage('Build result') {
      steps {
        sh 'docker build -t devenv27/result ./result'
      }
    } 
    stage('Build vote') {
      steps {
        sh 'docker build -t devenv27/vote ./vote'

      }
    }
    stage('Build worker') {
      steps {
        sh 'docker build -t devenv27/worker ./worker'

      }
    }
    stage('Push result image') {
      
      steps {
        withDockerRegistry(credentialsId: 'dockerhub', url:'https://registry.hub.docker.com') {
          sh 'docker push devenv27/result:latest'
        }
      }
    }
    stage('Push vote image') {
      
      steps {
        withDockerRegistry(credentialsId: 'dockerhub', url:'https://registry.hub.docker.com') {
          sh 'docker push devenv27/vote:latest'        }
      }
    }
    stage('Push worker image') {
      
      steps {
        withDockerRegistry(credentialsId: 'dockerhub', url:'https://registry.hub.docker.com') {
          sh 'docker push devenv27/worker:latest'        }
      }
    }
  }
}
