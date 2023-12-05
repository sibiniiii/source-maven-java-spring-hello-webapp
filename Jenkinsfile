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
        sh 'mvn clean package'
      }
    }
    stage('Test') {
      steps {
        echo 'mvn test'
      }
    }
    stage('Deploy') {
      steps {
        deploy adapters: [tomcat9(credentialsId: 'tomcat-manager', url: 'http://43.201.152.200:8080/')], contextPath: null, war: 'target/hello-world.war'
      }
    }
  }
}
