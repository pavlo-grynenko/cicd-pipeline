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

    stage('Docker push image') {
	docker.withRegistry('https://registry.hub.docker.com', 'docker-hub') {
		app.push("${env.BUILD_NUMBER}")
		app.push("latest")
	}	
    }
  }
}
