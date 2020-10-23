Jenkinsfile (Declarative Pipeline)
pipeline {
  agent any
    stages {
      stage('Build') {
        steps {
          sh 'wget https://raw.githubusercontent.com/9868-08/jenkins/master/Dockerfile;/
          wget https://raw.githubusercontent.com/9868-08/jenkins/master/helloworld.py;/
          docker build . --tag hello-world;/docker run hello-world' 
        }
      }
    }
}
