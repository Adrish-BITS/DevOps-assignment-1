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
                bat 'cp index.html D:/staging'  // Simulated deploy
            }
        }

        stage('Approval') {
            steps {
                input message: 'Approve to deploy to Production?'
            }
        }

        stage('Deploy to Production') {
            steps {
                input message: 'Approve deployment to Production?'
                echo 'Deploying to Production...'
                bat 'cp index.html D:/production'  // Simulated deploy
            }
        }
    }

    post {
        failure {
            echo 'Something failed. Please check.'
        }
    }
}
