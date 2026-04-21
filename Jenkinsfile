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
                // Navigate into the parent folder, then the react folder
                dir('app-deployment/my-react-app') {
                    sh 'npm install'
                    sh 'npm run build'
                }
            }
        }
        
        stage('Archive') {
            steps {
                // Archive from the deep path
                archiveArtifacts artifacts: 'app-deployment/my-react-app/build/**', fingerprint: true
            }
        }
    }
}
