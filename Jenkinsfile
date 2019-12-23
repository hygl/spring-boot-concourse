pipeline {
  agent {
    node {
      label 'kubernetes'
    }

  }
  stages {
    stage('Prep') {
      agent {
        node {
          label 'kubernetes'
        }

      }
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