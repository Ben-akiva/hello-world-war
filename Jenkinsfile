pipeline {
  agent any
  stages {
    stage('checkout') {
      steps {
        git(url: 'https://github.com/Ben-akiva/hello-world-war.git', branch: 'master')
      }
    }

    stage('Build') {
      steps {
        sh 'docker build .'
      }
    }

  }
}