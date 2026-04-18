pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                // Ensure you have "GitHub" configured or use your repo URL here
                git branch: 'main', url: 'https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git'
            }
        }
        stage('Build') {
            steps {
                // Use the 'node-latest' tool you configured in Step 2
                nodejs('node-latest') {
                    sh 'npm install'
                    sh 'npm run build'
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying to Nginx...'
                // This copies the static files from the build folder into the nginx container
                sh 'docker cp dist/. my-web-server:/usr/share/nginx/html'
            }
        }
    }
}
