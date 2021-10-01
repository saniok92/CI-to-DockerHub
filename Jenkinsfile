pipeline {
  agent any
  tools {
        dockerTool 'Docker'
    }
  environment {
    DOCKERHUB_CREDENTIALS = credentials('saniok92-dockerhub')
  }
  stages {
    stage('Build'){
      steps {
        sh'
        docker.withRegistry('https://index.docker.io/v1/', 'DOCKERHUB_CREDENTIALS') {
          git 'git@github.com:saniok92/CI-to-DockerHub.git'
                               docker.build('example')
                               image.push('latest')'
        }
      }
    }
  }

  post {
    always {
      sh 'docker logout'
    }
  }
}
