pipeline {
    agent {label "k8s-node"} //this will copy everytaasasAahing from git to worddsddkfdsfder node k8s
    environment{
        DOCKERHUB_CREDENTIALS = credentials('docker-hub-ovdi')
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
         
        stage('3-Docker Build') {
           steps {
            sh ' sudo docker build   /home/ubuntu/jenkins/workspace/pipeline/ -t ovdi/website'
          }
       }
         
         stage('login') {
           steps {
              
           }
       }
         
        stage("-Docker Push"){                                     
                       steps{
                      
                       sh' sudo docker rm -f $(sudo docker ps -a -q)'
                       sh 'sudo docker rm -f ovdi/website'
                       sh 'sudo docker rmi -f ovdi/website'
                       sh 'sudo docker run -it -p 81:80 -d ovdi/website'
                       sh ' docker push ovdi/website'

                              
                       }
              }  
    }

    post {
           always {
                    sh 'docker logout'
            }
        }
}
