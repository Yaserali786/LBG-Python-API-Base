pipeline {
    agent any
    environment {
        GCR_CREDENTIALS_ID = 'yaser-week3-secret' // The ID you provided in Jenkins credentials
        IMAGE_NAME = 'yaser-test-build-1'
        GCR_URL = 'gcr.io/lbg-mea-build-c19'
    }
    stages {
        stage('Build and Push to GCR') {
            steps {
                script {
                    // Authenticate with Google Cloud
                // Configure Docker to use gcloud as a credential helper
                sh 'gcloud auth configure-docker --quiet'
                // Build the Docker image
                sh "docker build -t ${GCR_URL}/${IMAGE_NAME}:${BUILD_NUMBER} ."
                // Push the Docker image to GCR
                sh "docker push ${GCR_URL}/${IMAGE_NAME}:${BUILD_NUMBER}"
                }
            }
        }
    }
}