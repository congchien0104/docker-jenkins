pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerhub')
  }
  stages {
    stage('Build') {
      steps {
                echo '=== Building Petclinic Docker Image ==='
                script {
                    app = docker.build("chienphung/petclinic-spinnaker-jenkins")
                }
            }
    }
  }
}
