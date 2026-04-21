pipeline {
    agent {
        // This will automatically pull the official Node image
        // and run your build inside it.
        docker { 
            image 'node:20-alpine' 
            args '-u root' // Helps avoid permission issues inside the container
        }
    }
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Build') {
            steps {
                sh 'npm install'
                sh 'npm run build'
            }
        }
        
        stage('Archive Build Artifacts') {
            steps {
                // This saves the 'build' folder so you can download it 
                // directly from the Jenkins dashboard
                archiveArtifacts artifacts: 'build/**', fingerprint: true
            }
        }
    }
}
