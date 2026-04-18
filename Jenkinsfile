pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                // This will use whatever 'npm' is found in the Jenkins container's PATH
                sh 'npm install'
                sh 'npm run build'
            }
        }
        stage('Deploy') {
            steps {
                // This copies the static files to your Nginx container
                sh 'docker cp build/. my-web-server:/usr/share/nginx/html'
            }
        }
    }
}
