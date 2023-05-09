
pipeline {
    agent any
    environment {
        ECR_REPOSITORY = '819243027190.dkr.ecr.us-east-1.amazonaws.com/routing-009'
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    def appImage = docker.build("app:${env.BUILD_ID}")
                    docker.withRegistry("https://${ECR_REPOSITORY}", "Ecr Neurogpt") {
                        appImage.push()
                    }
                }
            }
        }
    }
}
