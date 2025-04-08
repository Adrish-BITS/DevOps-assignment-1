pipeline {
    agent any

    environment {
        STAGING_SERVER = 'staging.example.com'
        PROD_SERVER = 'prod.example.com'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
            }
        }

        stage('Test') {
            steps {
                echo 'Running Tests...'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to Staging...'
            }
        }

        stage('Approval') {
            steps {
                input message: 'Approve to deploy to Production?'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to Production...'
            }
        }
    }

    post {
        failure {
            echo 'Something failed. Please check.'
        }
    }
}
