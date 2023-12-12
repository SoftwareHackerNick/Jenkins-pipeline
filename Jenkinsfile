pipeline {
 agent any
 environment {
 // Define environment variables if needed
 DOCKER_HUB_CREDENTIALS = '57adbd53-4053-4457-9c5f-e396d996964b'
 DOCKER_IMAGE_NAME = 'nikhilpatil22599/jenkins_pipeline'
 DOCKER_IMAGE_TAG = "${DOCKER_IMAGE_NAME}:${env.BUILD_NUMBER}"
 }
 stages {
 stage('Checkout') {
 steps {
 // Checkout the source code from the Git repository
 checkout scm
 }
 }
 stage('Build and Push Docker Image') {
 steps {
 script {
 // Build the Docker image
 def dockerImage = docker.build("${DOCKER_IMAGE_TAG}")
 // AuthenƟcate with Docker Hub
 docker.withRegistry('hƩps://registry.hub.docker.com', "${DOCKER_HUB_CREDENTIALS}") {
 // Push the Docker image to Docker Hub
 dockerImage.push()
 }
 }
 }
 }
 }
 post {
 success {
 echo "Docker image built and pushed successfully"
 }
 }
}