pipeline {
  
  agent any
  
  environment {
    DOCKERHUB_CREDENTIALS=credentials('docker-hub')
  }

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

    stage('Docker Login') {
      steps {
	sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }

    stage('Docker Push') {
      steps {
        sh 'docker push pavlogrynenko/pavlo-grynenko-image:latest'
      }
    }
  }

  post {
    always {
      sh 'docker logout'
    }
  }
}
