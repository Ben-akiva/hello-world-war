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
        sh 'docker build hello-word-java .'
      }
    }

    stage('test') {
      steps {
        sh 'docker -itd --name hello-word -p 80:8080 hello-word-java'
        sleep 5
        sh 'curl:localhost:8080'
        sh 'docker stop hello-word && docker rm hello-word'
      }
    }

  }
}