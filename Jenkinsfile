pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script {
                    // Build commands, e.g., compile Java or build Docker image
                    sh 'echo Building...'
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    // Test commands, e.g., run JUnit tests
                    sh 'echo Testing...'
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    // Deploy commands, e.g., deploy to staging using Docker
                    sh 'echo Deploying...'
                }
            }
        }
    }
    post {
        always {
            // Commands to clean up, run regardless of result
            sh 'echo Cleaning up...'
        }
        success {
            // Commands on success
            sh 'echo Success!'
        }
        failure {
            // Commands on failure
            sh 'echo Failed!'
        }
    }
}

