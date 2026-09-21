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

                bat '''
                    echo Starting Windows build process
                    echo Application version: %VERSION%
                    echo Current directory:
                    cd
                    echo Files in workspace:
                    dir
                '''
            }
        }

        stage('Test') {
            steps {
                echo "Testing ${ENVIRONMENT} environment"

                bat '''
                    echo Running tests...
                    echo Test completed successfully
                    exit /b 1
                '''
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

                bat '''
                    echo Starting deployment...
                    echo Deploying version %VERSION%
                    echo Deployment completed successfully
                '''
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