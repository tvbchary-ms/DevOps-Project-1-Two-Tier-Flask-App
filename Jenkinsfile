pipeline {
    agent any

    stages {
        stage('Clone Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/tvbchary-ms/DevOps-Project-1-Two-Tier-Flask-App'
            }
        }

        stage('Build Docker Image') {
            steps {
                dir('.') {   // change this if files are in subfolder
                    sh '''
                        docker build -t flask-app:latest .
                    '''
                }
            }
        }

        stage('Deploy with Docker Compose') {
            steps {
                sh 'docker compose down || true'
                sh 'docker compose up -d --build'
            }
        }
    }
}

