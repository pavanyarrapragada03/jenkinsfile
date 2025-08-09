stage('Deploy') {
    steps {
        echo 'Pushing Docker image to registry...'
        // This is the updated command with your username
        sh "docker tag ${DOCKER_IMAGE} docker.io/pavanyarrapragada03/${DOCKER_IMAGE}"
        sh "docker push docker.io/pavanyarrapragada03/${DOCKER_IMAGE}"
    }
}
