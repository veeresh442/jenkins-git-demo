pipeline {
    agent any

    environment {
        ENVIRONMENT = 'development'
        VERSION = '1.0'
    }

    stages {

        stage('Build') {
            steps {
                echo "Building version ${VERSION}"
            }
        }

        stage('Test') {
            steps {
                echo "Testing ${ENVIRONMENT} environment"
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying version ${VERSION} to ${ENVIRONMENT}"
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution completed.'
        }

        success {
            echo 'Pipeline was successful!'
        }

        failure {
            echo 'Pipeline failed!'
        }
    }
}