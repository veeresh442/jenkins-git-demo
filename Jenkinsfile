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