pipeline {
  agent any

  triggers {
    pollSCM('H H 1 * *')
  }

  stages {
    stage('Checkout') {
      steps {
        git branch: 'main', 
        url: 'https://github.com/sibiniiii/source-maven-java-spring-hello-webapp.git'
      }
    }
    stage('Build') {
      steps {
        sh 'cat ./Jenkinsfile'
      }
    }
    stage('Test') {
      steps {
        echo 'Jenkinsfile steping'
      }
    }
    stage('Deploy') {
      steps {
        deploy adapters: [tomcat9(credentialsId: 'admin', url: 'http://43.201.152.200:8080/')], contextPath: null, war: 'path/to/war'
      }
    }
  }
}
