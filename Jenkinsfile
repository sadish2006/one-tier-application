pipeline {
    agent any

    stages {

        stage('Clone GitHub Repo') {
            steps {
                git branch: 'main',
                url: 'https://github.com/sadish2006/one-tier-application.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''
                docker build -t one-tier-app:latest .
                '''
            }
        }

        stage('Run Docker Container') {
            steps {
                sh '''
                docker rm -f one-tier-container || true
                docker run -d -p 5000:5000 --name one-tier-container one-tier-app:latest
                '''
            }
        }
    }
}
