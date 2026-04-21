pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Install and Build') {
            steps {
                // Jenkins will use the Node/npm versions installed on the server
                sh 'npm install'
                sh 'npm run build'
            }
        }
        
        stage('Archive') {
            steps {
                // This keeps the build output accessible in Jenkins
                archiveArtifacts artifacts: 'build/**', fingerprint: true
            }
        }
    }
}
