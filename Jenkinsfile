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
                sh { docker build . }
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