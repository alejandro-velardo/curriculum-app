pipeline {
  agent any
  stages {
    stage('Checkout Code') {
      steps {
        git(url: 'https://github.com/alejandro-velardo/curriculum-app/', branch: 'dev')
      }
    }

    stage('Log') {
      parallel {
        stage('Log') {
          steps {
            sh 'ls -la'
          }
        }

        stage('Front-End Unit Tests / Shell Script') {
          steps {
            sh '''cd curriculum-front && npm i && npm install --save-dev vue-jest
Â && npm run test:unit'''
          }
        }

      }
    }

    stage('Build') {
      steps {
        sh 'docker build -f curriculum-front/Dockerfile . '
      }
    }

  }
}