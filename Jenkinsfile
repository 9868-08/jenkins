pipeline {
  agent {
         docker { image 'node:14-alpine'}
stages {
    stage('Build') { 
      steps {
        sh if [test -f "Dockerfile"]; then
           rm Dockerfileecho
           fi
           if [test -f "helloworld.py"]; then
           rm helloworld.py
           fi
        sh 'wget https://raw.githubusercontent.com/9868-08/jenkins/master/Dockerfile'
        sh 'wget https://raw.githubusercontent.com/9868-08/jenkins/master/helloworld.py'
        sh '/usr/bin/docker build . --tag hello-world;/docker run hello-world
      }
    }
}
}
