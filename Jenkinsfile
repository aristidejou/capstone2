pipeline {
    agent {label "k8s-node"} //this will copy everything from git to worker node k8s
    environment{
        DOCKERHUB_CREDENTIALS = credentials('docker-key')
    }
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
        
        stage("3-Dockerfile Build"){                                     
                       steps{
                       // sh 'sudo docker rm -f $(sudo docker ps -a -q)'
                       // sh 'sudo docker rmi -f $(sudo docker  -a -q)'
                        sh 'sudo docker build /home/ubuntu/jenkins/workspace/pipeline/ -t ovdi/website'
                        sh 'sudo docker run -it -p 80:80 -d ovdi/website'
                        sh 'sudo docker push ovdi/website'
                       }
              }  
    }
}
