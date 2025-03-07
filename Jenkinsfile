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
                    sh 'docker build -t webapp .'
                    sh 'docker images'
                }
            

        }
    }
}