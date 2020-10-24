pipeline {
    agent any
    environment {
        REPO = 'dinky98/tmp'
        PRIVATE_REPO = "${PRIVATE_REGISTRY}/${REPO}"
        DOCKER_PRIVATE = credentials('docker-private-registry')
    }
    stages {
        stage ('Docker build Micro-Service') {
            parallel {
                stage ('Hello world application') {
                    agent { label 'docker'}
                    steps {
                        sh "docker build -f https://raw.githubusercontent.com/9868-08/jenkins/master/Dockerfile -t ${REPO}:${COMMIT}"
                    }
                }
            }
        }
        stage ('Run'){
            agent { label 'docker'}
            steps {
                // Create Network
                sh "docker network create jenkins-${BUILD_NUMBER}"
                //Start application micro-services
                sh "docker run -d --name 'jenkins-${BUILD_NUMBER}' --network jenkins-${BUILD_NUMBER} ${REPO}:${COMMIT}"
                sh "docker run -d --name 'slave-${BUILD_NUMBER}'   --network jenkins-${BUILD_NUMBER} ${REPO}:${COMMIT}-slave"
                sh "docker run -d --name 'nginx-${BUILD_NUMBER}'   --network jenkins-${BUILD_NUMBER} --link jenkins-${BUILD_NUMBER}:jenkins ${REPO}:${COMMIT}-nginx"
                // Get container IDs
                script {
                    DOCKER_JENKINS = sh(script: "docker ps -qa -f ancestor=${REPO}:${COMMIT}", returnStdout: true).trim()
                    DOCKER_SLAVE   = sh(script: "docker ps -qa -f ancestor=${REPO}:${COMMIT}-slave", returnStdout: true).trim()
                    DOCKER_NGINX   = sh(script: "docker ps -qa -f ancestor=${REPO}:${COMMIT}-nginx", returnStdout: true).trim()
                }
            }
        }
    }
    post {
        always {
            echo 'Run regardless of the completion status of the Pipeline run.'
        }
        changed {
            echo 'Only run if the current Pipeline run has a different status from the previously completed Pipeline.'
        }
        success {
            echo 'Only run if the current Pipeline has a "success" status, typically denoted in the web UI with a blue or green indication.'

        }
        unstable {
            echo 'Only run if the current Pipeline has an "unstable" status, usually caused by test failures, code violations, etc. Typically denoted in the web UI with a yellow indication.'
        }
        aborted {
            echo 'Only run if the current Pipeline has an "aborted" status, usually due to the Pipeline being manually aborted. Typically denoted in the web UI with a gray indication.'
        }
    }
}