pipeline {
    agent any

    parameters {
        choice(
            name: 'ENVIRONMENT',
            choices: ['dev', 'staging', 'prod'],
            description: 'Select deployment environment'
        )
    }

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/sidak-max/labexam.git'
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
                    message: "Approve deployment to ${ENVIRONMENT}?",
                    ok: 'Go'
                )

                bat 'python app.py'
            }
        }
    }
}
