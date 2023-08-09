pipeline {
  agent any
  environment {
        AWS_ACCOUNT_ID="893473272543"
        AWS_DEFAULT_REGION="us-east-1"
        IMAGE_REPO_NAME="practical-devops"
        IMAGE_TAG="v1"
        REPOSITORY_URI = "893473272543.dkr.ecr.us-east-1.amazonaws.com"
  }
  stages {
    stage('Logging into AWS ECR') {
      steps {
        script {
        sh "docker login -u AWS -p $(aws ecr get-login-password --region the-region-you-are-in) 893473272543.dkr.ecr.the-region-you-are-in.amazonaws.com"
        }  
      }
    }
    // Building Docker images
    stage('Building image') {
      steps{
        script {
          dockerImage = docker.build "${IMAGE_REPO_NAME}:${IMAGE_TAG}"
        }
      }
    }
   
    // Uploading Docker images into AWS ECR
    stage('Pushing to ECR') {
     steps{  
         script {
                sh """docker tag ${IMAGE_REPO_NAME}:${IMAGE_TAG} ${REPOSITORY_URI}:$IMAGE_TAG"""
                sh """docker push ${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_DEFAULT_REGION}.amazonaws.com/${IMAGE_REPO_NAME}:${IMAGE_TAG}"""
         }
        }
      }
  }
}
