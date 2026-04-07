pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t dance-app .'
            }
        }

        stage('Stop Old Container') {
            steps {
                bat 'docker stop dance-container || exit 0'
                bat 'docker rm dance-container || exit 0'
            }
        }

        stage('Run New Container') {
            steps {
                bat 'docker run -d -p 8082:80 --name dance-container dance-app'
            }
        }

    }
}