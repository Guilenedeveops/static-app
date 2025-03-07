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
                
            }
        }
        stage('Dockerpush'){
            steps{
                sh 'docker push 867344455679.dkr.ecr.us-east-1.amazonaws.com/revision-repo:latest'
                
            }
        }
    }
}