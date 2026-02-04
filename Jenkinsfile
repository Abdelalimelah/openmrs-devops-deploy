pipeline {
  agent any

  stages {
    stage('Deploy (Docker Compose from home folder)') {
      steps {
        sh '''
          cd /Users/abdelalime/openmrs-docker
          /usr/local/bin/docker compose up -d
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
