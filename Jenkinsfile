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
            defaultValue: '1.0',
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
            when {
                expression {
                    params.ENVIRONMENT == 'production'
                }
            }

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