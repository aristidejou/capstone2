pipeline {
    agent {label "k8s-node"} 
    environment{
        DOCKERHUB_CREDENTIALS = credentials('docker-key')
     stages {
        stage('1-Release Date') {
            steps {
                    sh 'date'
            }
        }
         
        stage('2-Code Build') {
            steps {
                    git 'https://github.com/aristidejou/capstone2.git'
            }
        }
        
        
    }
}
