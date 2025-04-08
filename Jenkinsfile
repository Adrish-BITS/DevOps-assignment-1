pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    try {
                        echo 'Building the project...'
                        bat 'echo Simulating build'
                    } catch (e) {
                        echo "Build failed: ${e}"
                        error("Stopping pipeline due to build failure.")
                    }
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    try {
                        echo 'Running tests...'
                        bat 'echo Simulating test'
                        // Simulate failure (uncomment to test)
                        // bat 'exit 1'
                    } catch (e) {
                        echo "Test failed: ${e}"
                        error("Stopping pipeline due to test failure.")
                    }
                }
            }
        }

        stage('Deploy to Staging') {
            steps {
                script {
                    try {
                        echo 'Deploying to staging...'
                        bat 'copy index.html D:\\staging\\'
                    } catch (e) {
                        echo "Staging deployment failed: ${e}"
                        error("Stopping pipeline due to staging deployment failure.")
                    }
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                input message: 'Approve deployment to Production?'
                script {
                    try {
                        echo 'Deploying to production...'
                        bat 'copy index.html D:\\production\\'
                    } catch (e) {
                        echo "Production deployment failed: ${e}"
                        error("Pipeline stopped: production deployment failed.")
                    }
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Please check logs.'
        }
        always {
            echo 'Pipeline execution finished.'
        }
    }
}
