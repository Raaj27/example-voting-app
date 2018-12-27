pipeline {
  agent any
  
  stages {
    stage('Build result') {
      steps {
        sh 'docker build -t dockersamples/result ./result'
        sh 'docker tag dockersamples/result:latest devenv27/result:latest'
      }
    } 
    stage('Build vote') {
      steps {
        sh 'docker build -t dockersamples/vote ./vote'
        sh 'docker tag dockersamples/vote:latest devenv27/vote:latest'

      }
    }
    stage('Build worker') {
      steps {
        sh 'docker build -t dockersamples/worker ./worker'
        sh 'docker tag dockersamples/worker:latest devenv27/worker:latest'

      }
    }
    stage('Push result image') {
      
      steps {
        withDockerRegistry(credentialsId: 'dockerhub', url:'https://registry.hub.docker.com') {
          sh 'docker push devenv27/result'
        }
      }
    }
    stage('Push vote image') {
      
      steps {
        withDockerRegistry(credentialsId: 'dockerhub', url:'https://registry.hub.docker.com') {
          sh 'docker push devenv27/vote'        }
      }
    }
    stage('Push worker image') {
      
      steps {
        withDockerRegistry(credentialsId: 'dockerhub', url:'https://registry.hub.docker.com') {
          sh 'docker push devenv27/worker'        }
      }
    }
  }
}
