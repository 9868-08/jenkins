pipeline { 
    agent any 
    stages { 
        stage('Cloning our Git') { 
            steps { 
                git 'https://github.com/9868-08/jenkins.git' 
            }
        } 
        stage('Building our image') { 
            steps { 
                script { 
                    dockerImage = docker.build registry + ":$BUILD_NUMBER"
                }
            } 
        }
        stage('Run our image') { 
            steps { 
                sh "docker run $registry:$BUILD_NUMBER" 
            }
        } 
        stage('Cleaning up') { 
            steps { 
                sh "docker rmi $registry:$BUILD_NUMBER" 
            }
        } 
    }
}