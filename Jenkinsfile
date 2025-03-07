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
                    sh 'docker built -t webapp .'
                    sh 'docker images'
                }
            }

        }
    }
}