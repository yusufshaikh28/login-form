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
                docker stop login-container || exit 0
                docker rm login-container || exit 0
                docker run -d -p 8081:80 --name login-container login-app:latest
                '''
            }
        }
    }
}
