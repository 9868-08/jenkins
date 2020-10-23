pipeline {
  agent {
    label 'docker' 
  }
  stages {
      stage('Build') {
        steps {
          sh 'wget https://raw.githubusercontent.com/9868-08/jenkins/master/Dockerfile'
          sh 'wget https://raw.githubusercontent.com/9868-08/jenkins/master/helloworld.py'
          sh '/usr/bin/docker build . --tag hello-world;/docker run hello-worldi'
        }
      }
    }
}
