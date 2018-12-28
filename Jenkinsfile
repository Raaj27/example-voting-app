pipeline {
  agent any
  
  stages {
    stage('Build result') {
      steps {
        sh 'docker build ./result'
      }
    } 
    stage('Build vote') {
      steps {
        sh 'docker build  ./vote'

      }
    }
    stage('Build worker') {
      steps {
        sh 'docker build  ./worker'

      }
    }
    stage('Push result image') {
      
      steps {
        withDockerRegistry(credentialsId: 'dockerhub', url:'https://docker.io') {
          sh 'docker push devenv27/results'
        }
      }
    }
    stage('Push vote image') {
      
      steps {
        withDockerRegistry(credentialsId: 'dockerhub', url:'https://docker.io') {
          sh 'docker push devenv27/votes'        }
      }
    }
    stage('Push worker image') {
      
      steps {
        withDockerRegistry(credentialsId: 'dockerhub', url:'https://docker.io') {
          sh 'docker push devenv27/workers'        }
      }
    }
  }
}
