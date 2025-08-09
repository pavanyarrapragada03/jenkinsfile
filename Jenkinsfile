pipeline {
    agent any

    environment {
        // Defines the Docker image name using the Jenkins build number
        DOCKER_IMAGE = "my-app:${env.BUILD_NUMBER}"
        // Set your Docker registry URL here
        DOCKER_REGISTRY = "your-registry-url.com"
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building the Docker image...'
                sh "docker build -t ${DOCKER_IMAGE} ."
            }
        }
        
        stage('Test') {
            steps {
                echo 'Running tests...'
                // Run tests inside the Docker container
                sh "docker run --rm ${DOCKER_IMAGE} npm test"
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'Pushing Docker image to registry...'
                sh "docker tag ${DOCKER_IMAGE} ${DOCKER_REGISTRY}/${DOCKER_IMAGE}"
                sh "docker push ${DOCKER_REGISTRY}/${DOCKER_IMAGE}"
                
                // You can add your actual deployment commands here,
                // for example, using SSH to update a server.
                echo 'Deployment successful.'
            }
        }
    }
}
