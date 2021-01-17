
pipeline {
  agent {
    any
  }
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
    stage('Test and Build') {
      parallel {
        stage('Run Tests') {
          steps {
            sh 'npm run test'
          }
        }
        stage('Create Build Artifacts') {
          steps {
            sh 'npm run build'
          }
        }
      }
    }
    stage('Deployment') {
          steps {
            withAWS(region:'us-east-1',credentials:'aws-credentials') {
              s3Delete(bucket: 'roopesh-jenkins', path:'**/*')
              s3Upload(bucket: 'roopesh-jenkins', workingDir:'build', includePathPattern:'**/*');
            }
          }
      }
    }
  }
view rawJenkinsfile hosted with ❤ by GitHub
