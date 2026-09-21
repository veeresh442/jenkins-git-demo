pipeline {
    agent any

    parameters {
        choice(
            name: 'ENVIRONMENT',
            choices: ['development', 'testing', 'production'],
            description: 'Select deployment environment'
        )

        string(
            name: 'VERSION',
            choices: ['1.0', '2.0', '3.0'],
            description: 'Application version'
        )
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