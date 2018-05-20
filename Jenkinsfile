pipeline {
  agent none
  stages {
    stage('Maven package') {
      agent {
        docker {
          image 'maven:3.5.0'
        }
      }
      steps {
        sh 'mvn clean package'
      }
    }
    stage('Docker Build') {
      agent any
      steps {
        sh 'docker build -t bhargava1/devops:secound_app .'
      }
    }
    stage('Docker Push') {
      agent any
      steps {
        withCredentials([usernamePassword(credentialsId: 'dockerHub', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
          sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
          sh 'docker push bhargava1/devops:secound_app'
        }
      }
    }
  }
}
