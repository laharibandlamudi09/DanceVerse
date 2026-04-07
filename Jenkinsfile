pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t dance-app .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker stop dance-container || true'
                sh 'docker rm dance-container || true'
            }
        }

        stage('Run New Container') {
            steps {
                sh 'docker run -d -p 8082:80 --name dance-container dance-app'
            }
        }

    }
}