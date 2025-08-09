pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'echo "This is a build step"'
            }
        }
        stage('Test') {
            steps {
                sh 'echo "This is a test step"'
            }
        }
    }
    post {
        always {
            echo 'Pipeline completed.'
        }
    }
}
