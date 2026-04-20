pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/kru45/react-app.git'
            }
        }

        stage('Install & Build') {
            steps {
                sh 'npm install'
                sh 'npm run build'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t react-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop react-container || true
                docker rm react-container || true
                docker run -d -p 3000:80 --name react-container react-app
                '''
            }
        }
    }
}
