pipeline {
    agent {label "k8s-node"} //this will copy everydddtaasasAahing from gitj to worddsddkfdsfder node k8s
    environment{
        DOCKERHUB_CREDENTIALS = credentials('docker-hub-ovdi')
    }
     stages {
            stage('1-Release Date') {
                  steps {
                    sh ' date'
                 }
           }
         
          stage('2-Code Build') {
                steps {
                    git 'https://github.com/aristidejou/capstone2.git'
                }
          }
         
        stage('3-Docker Build') {
                   steps {
                         sh ' sudo docker build   /home/ubuntu/jenkins/workspace/pipeline/ -t ovdi/website:latest'
                        sh' sudo chmod 777 /var/run/docker.sock'
                       withCredentials([string(credentialsId: 'dockerhubpwd', variable: 'dockerhubpwd')]) {
                           sh 'docker login -u ovdi -p ${dockerhubpwd}'
                          }
                sh ' docker push ovdi/website'
                sh' sudo docker rm -f $(sudo docker ps -a -q)'
                sh 'sudo docker run -it -p 81:80 -d ovdi/website'
                }
        }
         
      stage('4-Deployment/replicas') {
                steps {
                        script{
                                    try{
                                        sh 'sudo kubectl create -f ovdi-deploy.yaml'
                                        sh 'sudo kubectl create -f ovdi-svc-np.yaml'
                                    }catch (error){
                                        sh 'sudo kubectl apply -f ovdi-deploy.yaml'
                                        sh 'sudo kubectl apply -f ovdi-svc-np.yaml'
                                    }
                            }
                }
          }    
         
         
         
         
    }
}
  //  post {always { sh 'docker logout'            }}}
