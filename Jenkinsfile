pipeline {
  agent any
  tools {
        dockerTool 'Docker'
    }
  environment {
    DOCKERHUB_CREDENTIALS = credentials('docker-hub')
  }
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t saniok92/example:1 .'
      }
    }

    stage('Login') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR -p'
      }
    }

    stage('Push') {
      steps {
        sh 'docker push saniok92/example:1'
      }
    }

  }

  post {
    always {
      sh 'docker logout'
    }
  }
}
