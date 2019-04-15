pipeline {
  agent {
    docker {
      image 'maven:3.6.0-jdk8'
      args 'man/.m2:root/.m2'
    }

  }
  stages {
    stage('Prep') {
      steps {
        sh 'mvn clean '
      }
    }
  }
}