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
}