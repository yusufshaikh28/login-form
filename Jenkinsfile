pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/yusufshaikh28/login-form.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t login-app:latest .'
            }
        }

        stage('Run Container') {
            steps {
                bat '''
                REM Stop container if it exists
                docker stop login-container || exit 0
                docker rm login-container || exit 0
                
                REM Run container on port 8081
                docker run -d -p 8081:80 --name login-container login-app:latest
                '''
            }
        }

        stage('Deployment Link') {
            steps {
                echo 'Application deployed successfully!'
                echo 'Access your Login Page at: http://localhost:8081'
            }
        }
    }
}
