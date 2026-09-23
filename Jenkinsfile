pipeline {
    agent any

    environment {
        APP_NAME    = 'SampleApp'
        APP_VERSION = '1.0.0'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                bat 'python -m py_compile app.py'
            }
        }

        stage('Deploy') {
            steps {
                input(
                    message: "Approve deployment of ${APP_NAME} version ${APP_VERSION}?",
                    ok: 'Release'
                )

                bat 'python app.py'
            }
        }
    }
}