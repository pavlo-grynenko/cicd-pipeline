pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh './scripts/build.sh'
      }
    }

    stage('Test') {
      steps {
        sh './scripts/test.sh'
      }
    }

    stage('Docker build') {
      steps {
        sh 'docker build -t pavlo-grynenko-image .'
      }
    }

  }
}