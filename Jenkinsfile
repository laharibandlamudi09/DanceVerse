pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t dance-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop dance-container || true
                docker rm dance-container || true
                docker run -d -p 8082:80 --name dance-container dance-app
                '''
            }
        }
    }
}