pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                nodejs('node-latest') {
                    sh 'npm install'
                    sh 'npm run build'
                }
            }
        }
        stage('Deploy') {
            steps {
                // This copies the production files into your Nginx container
                sh 'docker cp build/. my-web-server:/usr/share/nginx/html'
            }
        }
    }
}
