pipeline {
    agent any

    stages {
        stage('Setup') {
            steps {
                echo 'Setting up the environment...'
		}
	}

        stage('Lint') {
            steps {
                echo 'Linting the code...'
                sh 'npx eslint src/*.js' // Adjust this command based on your project structure
            }
        }

        stage('Build') {
            steps {
                echo 'Building...'
                sh 'echo "No build required for static HTML/JS projects"'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing...'
                sh 'echo "Running tests"'
                // Add a command to run tests, like running a headless browser test
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying...'
                // Mock deployment command
                sh 'echo "Deploying to staging server"'
                // Use tools like rsync or scp to deploy to a server
            }
        }
    }
}
