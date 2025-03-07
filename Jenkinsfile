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
            stage{
                steps{
                    sh 'docker build -t webapp .'
                    sh 'docker images'
                }
            }

        }
    }
}