pipeline {
  agent {
    docker {
      args '-p 2000:3000'
      image 'node:10.1'
    }

  }
  stages {
    stage('Build') {
      steps {
        sh '''npm -v  

npm install  '''
      }
    }
    stage('Test') {
      steps {
        sh './jenkins/scripts/test.sh'
      }
    }
    stage('Deliver') {
      steps {
        sh './jenkins/scripts/deliver.sh'
        input 'Finished using the web site? (Click "Proceed" to continue)'
        sh './jenkins/scripts/kill.sh'
      }
    }
  }
  environment {
    CI = 'true'
  }
}