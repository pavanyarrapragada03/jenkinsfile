pipeline {
    // Specifies the agent to run the pipeline on. 'any' means any available agent.
    agent any

    // Defines environment variables that can be used throughout the pipeline.
    environment {
        // Example: Define a Docker image name
        DOCKER_IMAGE = "my-app:${env.BUILD_NUMBER}"
    }

    // A list of stages that make up the pipeline.
    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
                // Build a Docker image from the Dockerfile in the project root.
                sh "docker build -t ${DOCKER_IMAGE} ."
            }
        }
        
        stage('Test') {
            steps {
                echo 'Running tests...'
                // Use the built Docker image to run tests.
                sh "docker run --rm ${DOCKER_IMAGE} npm test"
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
                // Push the Docker image to a registry.
                // Replace "your-registry" with your actual registry URL.
                sh "docker tag ${DOCKER_IMAGE} your-registry/${DOCKER_IMAGE}"
                sh "docker push your-registry/${DOCKER_IMAGE}"
                // Add a command to deploy the new image to your server, e.g., via SSH.
            }
        }
    }
}
