pipeline {
    agent any
   
    environment {
        // Define the virtual environment path
        VENV_PATH = "${WORKSPACE}/.venv"
    }
    stages {
        stage('Setup Environment') {
            steps {
                echo 'Setting up the Python virtual environment...'
                sh """
                python3 -m venv $VENV_PATH
                """
            }
        }
        stage('Install Dependencies') {
            steps {
                echo 'Installing project dependencies...'
                sh """
                source $VENV_PATH/bin/activate
                pip install -r requirements.txt
                """
            }
        }
        stage('Lint Code') {
            steps {
                echo 'Linting the code...'
                sh """
                source $VENV_PATH/bin/activate
                flake8 --statistics --output-file lint-report.txt
                """
            }
            post {
                always {
                    archiveArtifacts artifacts: 'lint-report.txt', fingerprint: true
                }
            }
        }
        stage('Unit Tests') {
            steps {
                echo 'Running unit tests...'
                sh """
                source $VENV_PATH/bin/activate
                pytest --junitxml=unit-test-results.xml
                """
            }
            post {
                always {
                    junit 'unit-test-results.xml'
                }
            }
        }
        stage('Integration Tests') {
            steps {
                echo 'Running integration tests...'
                sh """
                source $VENV_PATH/bin/activate
                pytest --junitxml=integration-test-results.xml
                """
            }
            post {
                always {
                    junit 'integration-test-results.xml'
                }
            }
        }
        stage('Build and Package') {
            steps {
                echo 'Building and packaging the application...'
                sh """
                source $VENV_PATH/bin/activate
                python setup.py sdist
                """
            }
            post {
                always {
                    archiveArtifacts artifacts: 'dist/*.tar.gz', fingerprint: true
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying application to the staging environment...'
                sh """
                echo 'Deploying build to staging server...'
                """
                // Example: ssh deploy@staging 'deploy-command'
            }
        }
        stage('Monitor and Performance Tests') {
            steps {
                echo 'Monitoring application and running performance tests...'
                sh """
                source $VENV_PATH/bin/activate
                locust -f locustfile.py --headless --users 100 --spawn-rate 10
                """
            }
        }
    }
    post {
        success {
            echo 'Build and deployment succeeded!'
            // Send notifications or trigger further actions
        }
        failure {
            echo 'Build or deployment failed!'
            // Send failure notifications
        }
        always {
            echo 'Cleaning up after build...'
            cleanWs()
        }
    }
}

