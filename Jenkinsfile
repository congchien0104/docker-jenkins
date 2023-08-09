pipeline {
    agent { docker { image 'node:18.17.0-alpine3.18' } }
    stages {
        stage('Build docker image'){
            steps{
                script{
                    sh 'docker build -t javatechie/devops-integration .'
                }
            }
        }
    }
}
