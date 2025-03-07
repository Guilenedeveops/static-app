pipeline{
    agent any
    stages{
        stage('codescan'){
            steps{
                sh 'trivy fs . -o file.txt'
                sh 'cat file.txt'

            }
        }
    
        stage('dockerbuild'){
            
                steps{
                    sh 'docker build -t revision-repo .'
                    sh 'docker build -t newversion .'
                    sh 'docker images'
                }
            

        }
        stage('Dockerlogin'){
            steps{
                sh 'aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 867344455679.dkr.ecr.us-east-1.amazonaws.com'
                
                
            }
        }
         stage('Dockertag'){
            steps{
                sh 'docker tag revision-repo:latest 867344455679.dkr.ecr.us-east-1.amazonaws.com/revision-repo:latest'
                sh 'docker tag revision-repo:latest 867344455679.dkr.ecr.us-east-1.amazonaws.com/revision-repo:v1.$BUILD_NUMBER'
                
            }
        }
        stage('Dockerpush'){
            steps{
                sh 'docker push 867344455679.dkr.ecr.us-east-1.amazonaws.com/revision-repo:latest'
                sh 'docker push 867344455679.dkr.ecr.us-east-1.amazonaws.com/revision-repo:v1.$BUILD_NUMBER'
                
            }
        }
        stage('Dockertest'){
            steps{
                sh 'docker images'
                sh 'docker run -itd --name web1 -p 83:80 revision-repo'
                sh 'docker ps'
                
                
            }
        }

            }
}