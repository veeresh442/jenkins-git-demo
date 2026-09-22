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

    environment {
        APP_NAME = 'JenkinsDemo'
    }

    stages {

        stage('Build') {

            environment {
                BUILD_TYPE = 'release'
            }

            steps {

                echo "Application: ${APP_NAME}"
                echo "Version: ${VERSION}"
                echo "Build type: ${BUILD_TYPE}"

                bat '''
                    echo Starting Windows build process
                    echo Application: %APP_NAME%
                    echo Version: %VERSION%
                    echo Build type: %BUILD_TYPE%
                    echo Files in workspace:
                    dir
                '''
            }
        }

       stage('Test') {
    steps {
        echo "Testing ${ENVIRONMENT} environment"

        script {
            try {
                bat '''
                    echo Running tests...
                    exit /b 1
                '''
            } catch (err) {
                echo "Test failed, but the error was caught."
            }
        }

        echo "Pipeline continued after try/catch."
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
                    echo Application: %APP_NAME%
                    echo Version: %VERSION%
                    echo Environment: %ENVIRONMENT%
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