pipeline {
    agent any
    
     stages {
        stage('1-Release Date') {
            steps {
                    sh 'date'
            }
        }
         
        stage('1-commit on master') {
            steps {
                    git 'https://github.com/aristidejou/capstone2.git'
            }
        }
        
       
    }
}
