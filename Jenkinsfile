pipeline {
  agent {
    node {
      label 'docker'
    }

  }
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

    stage('test') {
      steps {
        sh 'mvn clean package'
      }
    }

  }
}