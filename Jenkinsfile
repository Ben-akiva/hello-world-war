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
        sh 'docker build -t benakiva/hello-word-java:$BUILD_NUMBER .'
      }
    }

    stage('test') {
      steps {
        sh 'docker run -itd --name hello-word -p 80:8080 benakiva/hello-word-java:$BUILD_NUMBER'
        sleep 5
        sh 'curl localhost:8080'
        sh 'docker stop hello-word && docker rm hello-word'
      }
    }

    stage('Push to DockerHub') {
      steps {
        sh 'docker login '
        sh 'docker push benakiva/hello-word-java:${env.BUILD_NUMBER}'
      }
    }

  }
}