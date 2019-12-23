pipeline {
  agent any
  stages {
    stage('Prep') {
      agent any
      steps {
        sh 'mvn clean '
      }
    }

    stage('build') {
      agent {
        node {
          label 'kubernetes'
        }

      }
      steps {
        sh 'mvn compile -DskipTests=true'
        sh 'mvn test'
      }
    }

  }
}