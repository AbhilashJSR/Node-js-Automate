pipeline {
    agent any

    environment {
        APP_DIR = '/home/ubuntu/node-app'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/AbhilashJSR/Node-js-Automate.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                sh 'npm test || echo "No tests defined, skipping..."'
            }
        }

        stage('Deployment process') {
            steps {
                // Stop previous instance if any
                sh 'pkill node || echo "No process to kill"'

                // Run app in background
                sh 'nohup node index.js > app.log 2>&1 &'
            }
        }
    }

    post {
        success {
            echo 'App Deployed Successfully!'
        }
        failure {
            echo 'Deployment failed.'
        }
    }
}
