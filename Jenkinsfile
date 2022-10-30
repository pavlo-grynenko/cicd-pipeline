pipeline {
  agent any
  stages {
    stage('error') {
      parallel {
        stage('error') {
          steps {
            sh './scripts/build.sh'
          }
        }

        stage('Build step') {
          steps {
            sh './scripts/build.sh'
          }
        }

      }
    }

  }
}