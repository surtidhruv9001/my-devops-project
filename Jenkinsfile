pipeline {
    agent any

    environment {
        // Set PATH to include Node.js installation path for access to node, npm, and npx commands
        PATH = "/opt/homebrew/bin:${env.PATH}"
    }

    stages {
        stage('Setup') {
            steps {
                echo 'Setting up the environment...'
                script {
                    // Display Node.js and NPX versions to verify correct setup
                    sh 'node --version'
                    sh 'npx --version'
                }
            }
        }

        stage('Lint') {
            steps {
                echo 'Linting JavaScript files...'
                // Assuming your JavaScript files are in a 'src' directory. Adjust if needed.
                sh 'npx eslint "src/*.js"'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the project...'
                // Since HTML/JS projects typically don't require compilation, echo a placeholder message
                sh 'echo "No build process required for static sites, but build process simulated."'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                // Placeholder for running tests. Actual commands will depend on your test setup.
                sh 'echo "Tests would run here if configured."'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying the project...'
                // Placeholder for deployment. Adjust with actual deployment commands as necessary.
                sh 'echo "Deploying to static site hosting provider or server."'
            }
        }
    }

    // Example of a post block for cleaning up and handling post-build actions
    post {
        always {
            echo 'Cleaning up...'
            // Clean up actions or post-build notifications can be added here
            sh 'echo "Cleanup tasks would run here."'
        }

        success {
            echo 'Build succeeded!'
            // Actions to take on successful build, e.g., notifications or further deployments
        }

        failure {
            echo 'Build failed!'
            // Actions to take on build failure, e.g., notifications to Slack, emails, etc.
        }
    }
}
