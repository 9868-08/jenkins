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

         stage('Docker Up') {
            steps {
                echo '> Building the docker containers ...'
                sh 'docker build . -t dinky98/jekins'
            }
        }
        stage('Run our image') { 
            steps { 
                sh "docker run dinky98/jekins" 
            }
        } 
        stage('Cleaning up') { 
            steps { 
                sh "docker rmi dinky98/jekins" 
            }
        } 
    }
}