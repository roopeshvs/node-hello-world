pipeline {
  agent any
  tools {nodejs "nodejs"}
  environment {
    CI = 'true'
    HOME = '.'
    npm_config_cache = 'npm-cache'
  }
  stages {
    stage('Install Packages') {
      steps {
        sh 'npm install'
      }
    }
    stage('Deployment') {
          steps {
            sh 'aws s3 rm s3://roopesh-jenkins --recursive'
            sh 'aws s3 cp . s3://roopesh-jenkins --recursive --include "*"'
          }
      }
    }
}
