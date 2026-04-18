pipeline {
    agent any
    
    stages {
        stage('Build') {
            agent {
                docker { image 'node:20-alpine' }
            }
            steps {
                sh 'npm install'
                sh 'npm run build'
            }
        }
        
        stage('Deploy') {
            steps {
                // This 'sh' runs on your host machine, where the Docker daemon lives
                sh 'docker cp my-react-app/build/. my-web-server:/usr/share/nginx/html'
            }
        }
    }
}
