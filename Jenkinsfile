pipeline {
  agent { label 'node-agent' }

  stages {
    stage('Checkout') {
      steps {
        git branch: 'main',
            url: 'https://github.com/elashrypublic/digi-jenkins-lab.git'
      }
    }

    stage('Install') {
      steps {
        sh '''
          npm install
        '''
      }
    }

    stage('Test') {
      steps {
        sh '''
          npm test
        '''
      }
    }
  }

  post {
    success { echo '✅ All tests passed on EC2!' }
    failure  { echo '❌ Build failed!' }
    always   { cleanWs() }
  }
}
