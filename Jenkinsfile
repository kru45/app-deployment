pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                // 'node-latest' must match the name you used in the Global Tool Configuration
                nodejs('node-latest') {
                    sh 'npm install'
                    sh 'npm run build'
                }
            }
        }
        stage('Deploy') {
            steps {
                // This command copies your build to the Nginx container
                // Replace 'my-web-server' with the name of your Nginx container
                sh 'docker cp build/. my-web-server:/usr/share/nginx/html'
            }
        }
    }
}
