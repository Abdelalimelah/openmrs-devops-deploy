pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps { checkout scm }
    }

    stage('Deploy (Docker Compose)') {
      steps {
        sh '''
          docker compose up -d
        '''
      }
    }

    stage('Smoke Test') {
      steps {
        sh '''
          curl -f --retry 20 --retry-delay 10 http://localhost:9901/ > /dev/null
        '''
      }
    }
  }
}
