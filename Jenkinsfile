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

    stage('Docker Build') {
      steps {
        sh 'docker build -t pavlogrynenko/cicd-pipeline:latest .'
      }
    }

    stage('Docker Push') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'        
        sh 'docker push pavlogrynenko/cicd-pipeline:latest'
      }
    }
  }

  post {
    always {
      sh 'docker logout'
    }
  }
}
