pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Build') {
            steps {
                // This command pulls the node image, maps your current workspace, 
                // installs dependencies, and builds the app.
                sh 'docker run --rm -v "${PWD}:/app" -w /app node:20-alpine sh -c "npm install && npm run build"'
            }
        }
    }
}
