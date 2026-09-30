pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t flask-mlops-app:latest .'
            }
        }
        stage('Clean Up Old Container') {
            steps {
                sh 'docker stop flask-app || true'
                sh 'docker rm flask-app || true'
            }
        }
        stage('Deploy Container') {
            steps {
                sh 'docker run -d -p 5000:5000 --name flask-app flask-mlops-app:latest'
            }
        }
    }
}
