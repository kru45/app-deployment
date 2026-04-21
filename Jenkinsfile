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
                // This 'dir' block tells Jenkins to perform 
                // the commands specifically inside 'my-react-app'
                dir('my-react-app') {
                    sh 'npm install'
                    sh 'npm run build'
                }
            }
        }
        
        stage('Archive') {
            steps {
                // Collect the build files from the subfolder
                archiveArtifacts artifacts: 'my-react-app/build/**', fingerprint: true
            }
        }
    }
}
