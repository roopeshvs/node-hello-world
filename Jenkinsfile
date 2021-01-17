pipeline {
  agent {
    docker {
      image 'node:10-alpine'
      args '-p 20001-20100:3000'
    }

  }
  stages {
    stage('Install Packages') {
      steps {
        sh 'npm install'
      }
    }

    stage('Create Build') {
      steps {
        sh 'npm run build'
      }
    }

  }
  environment {
    CI = 'true'
    HOME = '.'
    npm_config_cache = 'npm-cache'
  }
}