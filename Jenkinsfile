pipeline {
    agent any

    options {
        timestamps()
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install dependencies') {
            steps {
                dir('portfolio-next') {
                    sh 'node -v && npm -v'
                    sh 'npm ci'
                }
            }
        }

        stage('Build') {
            steps {
                dir('portfolio-next') {
                    sh 'npm run build'
                }
            }
        }
    }

    post {
        success { echo 'Build réussi' }
        failure { echo 'Build échoué' }
    }
}
