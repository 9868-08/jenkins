pipeline {
  agent {
    // Equivalent to "docker build -f Dockerfile.build --build-arg version=1.0.2 ./build/
    dockerfile {
        filename 'https://raw.githubusercontent.com/9868-08/jenkins/master/Dockerfile'
        dir 'build'
        label 'hello world'
        additionalBuildArgs  '--build-arg version=1.0.2'
        args '-v /tmp:/tmp'
    }
  }
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