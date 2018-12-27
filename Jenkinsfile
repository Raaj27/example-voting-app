pipeline {
  agent any
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
      when {
        branch 'master'
      }
      steps {
        withDockerRegistry(credentialsId: 'dockerbuildbot-index.docker.io', url:'') {
          sh 'docker push dockersamples/result'
        }
      }
    }
    stage('Push vote image') {
      when {
        branch 'master'
      }
      steps {
        withDockerRegistry(credentialsId: 'dockerbuildbot-index.docker.io', url:'') {
          sh 'docker push dockersamples/vote'
        }
      }
    }
    stage('Push worker image') {
      when {
        branch 'master'
      }
      steps {
        withDockerRegistry(credentialsId: 'dockerbuildbot-index.docker.io', url:'') {
          sh 'docker push dockersamples/worker'
        }
      }
    }
  }


       stage('DeployToProduction') {
            when {
                branch 'master'
            }
            steps {
                input 'Deploy to Production?'
                milestone(1)
                //implement Kubernetes deployment here
                kubernetesDeploy(
                    kubeconfigId: 'kubeconfig',
                    configs: 'kube-deployment.yml',
                    enableConfigSubstitution: true
                )
            }
        }
    }





















