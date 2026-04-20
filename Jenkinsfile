pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/kru45/app-deployment.git'
            }
        }

        stage('Install & Build') {
            steps {
                dir('my-react-app') {
                    sh 'npm install'
                    sh 'npm run build'
                }
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
