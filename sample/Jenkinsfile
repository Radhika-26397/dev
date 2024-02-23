pipeline {
    agent any

    environment {
        DOCKER_HUB_CREDENTIALS = credentials('docker-hub-credentials')
        IMAGE_NAME = 'radhika26/nginx'
        TAG = 'latest'
    }

    stages {
        stage('Build and Push Docker Image') {
            steps {
                script {
                    // Build Docker image
                    sh 'docker build -t $IMAGE_NAME:$TAG .'

                    // Log in to Docker Hub
                    sh "docker login -u ${DOCKER_HUB_CREDENTIALS_USR} -p ${DOCKER_HUB_CREDENTIALS_PSW}"

                    // Push Docker image to Docker Hub
                    sh "docker push $IMAGE_NAME:$TAG"
                }
            }
        }
    }
}

