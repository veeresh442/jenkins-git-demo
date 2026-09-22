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
                echo "Building ${APP_NAME}"
                echo "Version: ${VERSION}"
                echo "Build type: ${BUILD_TYPE}"

                bat '''
                    echo Starting Windows build process
                    echo Application: %APP_NAME%
                    echo Version: %VERSION%
                    echo Build type: %BUILD_TYPE%
                    echo Build completed successfully
                '''
            }
        }

        stage('Test') {
            steps {
                echo "Testing ${ENVIRONMENT} environment"

                bat '''
                    echo Running tests...
                    echo Application: %APP_NAME%
                    echo Version: %VERSION%
                    echo Tests completed successfully
                    exit /b 0
                '''
            }
        }
        
        stage('Credential Test') {
    steps {
        withCredentials([
            string(
                credentialsId: 'demo-secret',
                variable: 'MY_SECRET'
            )
        ]) {
            bat '''
                echo Checking Jenkins credential injection...

                if "%MY_SECRET%"=="" (
                    echo Secret was NOT injected
                    exit /b 1
                ) else (
                    echo Secret was successfully injected
                )
            '''
        }
    }
}

        stage('Deploy') {
            when {
                expression {
                    params.ENVIRONMENT == 'production'
                }
            }

            steps {
                echo "Deploying ${APP_NAME} version ${VERSION} to ${ENVIRONMENT}"

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
            echo 'Pipeline completed successfully!'
        }

        failure {
            echo 'Pipeline failed!'
        }
    }
}