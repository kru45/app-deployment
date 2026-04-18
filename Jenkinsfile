pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                // Ensure your GitHub URL is correct here
                git branch: 'main', url: 'https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git'
            }
        }
        stage('Build') {
            steps {
                // Ensure the name here matches exactly what you set in Jenkins Global Tool Configuration
                nodejs('node-latest') {
                    sh 'npm install'
                    sh 'npm run build'
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying to Nginx...'
                // This command copies your production build to the Nginx container
                sh 'docker cp build/. my-web-server:/usr/share/nginx/html'
            }
        }
    }
}
